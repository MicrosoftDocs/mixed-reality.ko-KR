---
title: MR 및 Azure 310-개체 검색
description: 기계 학습 모델을 학습 하는 방법을 알아보려면이 과정을 완료 하 고 유사한 개체와 혼합된 현실 응용 프로그램 내에서 실제 위치를 인식 하도록 학습된 된 모델을 사용 합니다.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure에서 사용자 지정 시각 검색, 혼합 현실, academy, unity, 자습서, api, hololens 개체
ms.openlocfilehash: 89ee79943a88de8a34c679ae33621db5770908b0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597650"
---
>[!NOTE]
><span data-ttu-id="c8868-104">혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="c8868-105">따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="c8868-106">이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="c8868-107">지원 되는 장치에서 작업을 계속 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="c8868-108">새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="c8868-109">게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-310-object-detection"></a><span data-ttu-id="c8868-110">Mr 및 Azure 310: 개체 검색</span><span class="sxs-lookup"><span data-stu-id="c8868-110">Mr and Azure 310: Object detection</span></span>

<span data-ttu-id="c8868-111">이 과정에서는 배웁니다 사용자 지정 시각적 콘텐츠 및 제공 된 이미지 내의 공간 위치를 인식 하는 방법을 Azure Custom Vision을 사용 하 여 혼합된 현실 응용 프로그램에서 "개체 검색" 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-111">In this course, you will learn how to recognize custom visual content and its spatial position within a provided image, using Azure Custom Vision "Object Detection" capabilities in a mixed reality application.</span></span>

<span data-ttu-id="c8868-112">이 서비스를 사용 하면 개체 이미지를 사용 하 여 기계 학습 모델을 학습할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-112">This service will allow you to train a machine learning model using object images.</span></span> <span data-ttu-id="c8868-113">그런 다음 학습 된 모델은 유사한 개체를 인식 하 고 실제 환경에서의 위치를 Microsoft HoloLens 카메라 캡처에 의해 제공 또는 사용 카메라 몰입 형 (VR) 헤드셋에 대 한 PC에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-113">You will then use the trained model to recognize similar objects and approximate their location in the real world, as provided by the camera capture of Microsoft HoloLens or a camera connect to a PC for immersive (VR) headsets.</span></span>

![과정 결과](images/AzureLabs-Lab310-00.png)

<span data-ttu-id="c8868-115">**Azure Custom Vision, 개체 감지** 개발자는 사용자 지정 이미지 분류자를 만들 수 있는 Microsoft 서비스 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-115">**Azure Custom Vision, Object Detection** is a Microsoft Service which allows developers to build custom image classifiers.</span></span> <span data-ttu-id="c8868-116">이러한 분류자 사용할 수 있습니다 새 이미지를 사용 하 여 제공 하 여 해당 새 이미지 내의 개체를 검색할 **경계 상자** 이미지 자체 내에서.</span><span class="sxs-lookup"><span data-stu-id="c8868-116">These classifiers can then be used with new images to detect objects within that new image, by providing **Box Boundaries** within the image itself.</span></span> <span data-ttu-id="c8868-117">서비스는이 프로세스를 간소화 하는 간단 하 고, 사용 하기 쉬운 온라인 포털을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-117">The Service provides a simple, easy to use, online portal to streamline this process.</span></span> <span data-ttu-id="c8868-118">자세한 내용은 다음 링크를 방문 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-118">For more information, visit the following links:</span></span>

* [<span data-ttu-id="c8868-119">Azure Custom Vision 페이지</span><span class="sxs-lookup"><span data-stu-id="c8868-119">Azure Custom Vision page</span></span>](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)
* [<span data-ttu-id="c8868-120">제한 및 할당량</span><span class="sxs-lookup"><span data-stu-id="c8868-120">Limits and Quotas</span></span>](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/limits-and-quotas)

<span data-ttu-id="c8868-121">이 과정을 완료 하면 다음을 수행 하는 일을 할 수 있는 혼합된 현실 응용 프로그램을 갖게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-121">Upon completion of this course, you will have a mixed reality application which will be able to do the following:</span></span>

1. <span data-ttu-id="c8868-122">사용자 수 *gaze* Azure Custom Vision Service, 개체 감지를 사용 하 여 학습 하는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-122">The user will be able to *gaze* at an object, which they have trained using the Azure Custom Vision Service, Object Detection.</span></span> 
2. <span data-ttu-id="c8868-123">사용자가 사용할 합니다 *탭* 제스처에서 찾고 있는 항목의 이미지를 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-123">The user will use the *Tap* gesture to capture an image of what they are looking at.</span></span>
3. <span data-ttu-id="c8868-124">앱에서 Azure Custom Vision Service에 이미지를 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-124">The app will send the image to the Azure Custom Vision Service.</span></span>
4. <span data-ttu-id="c8868-125">세계 좌표 공간 텍스트로 인식 결과 표시 하는 서비스에서 회신이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-125">There will be a reply from the Service which will display the result of the recognition as world-space text.</span></span> <span data-ttu-id="c8868-126">Microsoft HoloLens ' 공간 추적을 인식할 수 있는 개체의 세계 좌표 위치를 이해 하 고 사용 하는 방법으로 활용 하 여을 통해이 작업을 수행할 수는 합니다 *태그* 어떤에서 발견 되는 이미지를 사용 하 여 연결 레이블 텍스트를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-126">This will be accomplished through utilizing the Microsoft HoloLens' Spatial Tracking, as a way of understanding the world position of the recognized object, and then using the *Tag* associated with what is detected in the image, to provide the label text.</span></span>

<span data-ttu-id="c8868-127">과정에 대해서도 다루는 수동으로 업로드 이미지에 태그를 만들기 및 학습 다른 인식 하는 서비스 개체 (제공 된 예제는 cup), 여 설정 합니다 *경계 상자의* 제출한 이미지 내에서.</span><span class="sxs-lookup"><span data-stu-id="c8868-127">The course will also cover manually uploading images, creating tags, and training the Service, to recognize different objects (in the provided example, a cup), by setting the *Boundary Box* within the image you submit.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="c8868-128">생성 및 사용 하 여 앱의 다음 개발자는 Azure Custom Vision Service를 다시 탐색 식별 서비스에 대 한 예측 하 고 있었는지 여부를 결정할는 올바른 여부 (아무 것도 서비스 태그를 통해 누락 및 조정 된 *경계 상자*).</span><span class="sxs-lookup"><span data-stu-id="c8868-128">Following the creation and use of the app, the developer should navigate back to the Azure Custom Vision Service, and identify the predictions made by the Service, and determine whether they were correct or not (through tagging anything the Service missed, and adjusting the *Bounding Boxes*).</span></span> <span data-ttu-id="c8868-129">서비스 수 다음 다시 학습 해야, 실제 개체 인식 가능성 늘어납니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-129">The Service can then be re-trained, which will increase the likelihood of it recognizing real world objects.</span></span>

<span data-ttu-id="c8868-130">이 과정을 샘플 Unity 기반 응용 프로그램에 Azure Custom Vision Service, 개체 검색에서에서 결과 가져오는 방법을 배우게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-130">This course will teach you how to get the results from the Azure Custom Vision Service, Object Detection, into a Unity-based sample application.</span></span> <span data-ttu-id="c8868-131">사용자 지정 응용 프로그램을 작성 하려는 경우에 이러한 개념을 적용 하는 것이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-131">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="c8868-132">장치 지원</span><span class="sxs-lookup"><span data-stu-id="c8868-132">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="c8868-133">과정</span><span class="sxs-lookup"><span data-stu-id="c8868-133">Course</span></span></th><th style="width:150px"> <span data-ttu-id="c8868-134"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="c8868-134"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="c8868-135"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="c8868-135"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="c8868-136">MR 및 Azure 310: 개체 검색</span><span class="sxs-lookup"><span data-stu-id="c8868-136">MR and Azure 310: Object detection</span></span></td><td style="text-align: center;"> <span data-ttu-id="c8868-137">✔️</span><span class="sxs-lookup"><span data-stu-id="c8868-137">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="c8868-138">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="c8868-138">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="c8868-139">이 자습서는 Unity 사용 하 여 기본 경험이 있는 개발자 용으로 설계 하 고 C#입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-139">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="c8868-140">또한 주의 필수 구성 요소 및이 문서에서 작성 된 지침을 나타내는 새로운 테스트 되었으며 (2018 년 7 월) 작성 시점에 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-140">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="c8868-141">내에서 나열 된 사용 가능한 최신 소프트웨어를 사용 하는 합니다 [도구를 설치](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) 없습니다 가정이 과정에서 정보를 나열 된 것 보다 최신 소프트웨어에 맞게 보면 일치 완벽 하 게 됩니다 있지만 문서 아래.</span><span class="sxs-lookup"><span data-stu-id="c8868-141">You are free to use the latest software, as listed within the [install the tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="c8868-142">다음 하드웨어 및 소프트웨어가이 과정에 대 한 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-142">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="c8868-143">PC 개발</span><span class="sxs-lookup"><span data-stu-id="c8868-143">A development PC</span></span>
- [<span data-ttu-id="c8868-144">Windows 10 Fall Creators Update (또는 이상) 사용 하도록 설정 하는 개발자 모드를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="c8868-144">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="c8868-145">최신 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="c8868-145">The latest Windows 10 SDK</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="c8868-146">Unity 2017.4 LTS</span><span class="sxs-lookup"><span data-stu-id="c8868-146">Unity 2017.4 LTS</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="c8868-147">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="c8868-147">Visual Studio 2017</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- <span data-ttu-id="c8868-148">A [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) 개발자 모드를 설정 하 여</span><span class="sxs-lookup"><span data-stu-id="c8868-148">A [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) with Developer mode enabled</span></span>
- <span data-ttu-id="c8868-149">Azure 설정 및 Custom Vision Service 검색에 대 한 인터넷 액세스</span><span class="sxs-lookup"><span data-stu-id="c8868-149">Internet access for Azure setup and Custom Vision Service retrieval</span></span>
-  <span data-ttu-id="c8868-150">일련의 적어도 15 개의 이미지는 필요한)를 인식 하는 사용자 지정 비전 원하는 각 개체에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-150">A series of at least fifteen (15) images are required) for each object that you would like the Custom Vision to recognize.</span></span> <span data-ttu-id="c8868-151">원하는,이 과정을 통해 이미 제공 되는 이미지를 사용할 수 있습니다 [cup 일련](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span><span class="sxs-lookup"><span data-stu-id="c8868-151">If you wish, you can use the images already provided with this course, [a series of cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="c8868-152">시작하기 전 주의 사항</span><span class="sxs-lookup"><span data-stu-id="c8868-152">Before you start</span></span>

1.  <span data-ttu-id="c8868-153">이 프로젝트를 구축 하는 문제 발생을 방지 하려면 것이 좋습니다 루트 또는 루트 거의 폴더에이 자습서에 언급 된 프로젝트를 만든 (오래 폴더 경로 빌드 시에는 문제가 발생할 수 있습니다).</span><span class="sxs-lookup"><span data-stu-id="c8868-153">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="c8868-154">설정 하 고 여 HoloLens를 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-154">Set up and test your HoloLens.</span></span> <span data-ttu-id="c8868-155">에 HoloLens 등록 설정을 지원 해야 하는 경우 [HoloLens 설치 문서를 참조 하도록](https://docs.microsoft.com/hololens/hololens-setup)합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-155">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="c8868-156">(때로는 도움이 각 사용자에 대 한 이러한 작업을 수행) 새 HoloLens 앱 개발을 시작할 때 보정 및 센서 튜닝을 수행 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-156">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="c8868-157">보정에 대 한 도움말을 따라이 [HoloLens 보정 문서 링크](calibration.md#hololens)합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-157">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="c8868-158">센서 조정에 대 한 도움말을 따라이 [HoloLens 센서 튜닝 문서 링크](sensor-tuning.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-158">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-custom-vision-portal"></a><span data-ttu-id="c8868-159">1 장-사용자 지정 비전 포털</span><span class="sxs-lookup"><span data-stu-id="c8868-159">Chapter 1 - The Custom Vision Portal</span></span>

<span data-ttu-id="c8868-160">사용 하 여 **Azure Custom Vision Service**, 응용 프로그램에 사용할 수 있도록 해당 인스턴스를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-160">To use the **Azure Custom Vision Service**, you will need to configure an instance of it to be made available to your application.</span></span>

1.  <span data-ttu-id="c8868-161">탐색할 [에 **Custom Vision Service** 기본 페이지](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-161">Navigate [to the **Custom Vision Service** main page](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span></span>

2.  <span data-ttu-id="c8868-162">클릭할 **Getting Started**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-162">Click on **Getting Started**.</span></span>

    ![](images/AzureLabs-Lab310-01.png)

3.  <span data-ttu-id="c8868-163">사용자 지정 비전 포털에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-163">Sign in to the Custom Vision Portal.</span></span>

    ![](images/AzureLabs-Lab310-02.png)

4.  <span data-ttu-id="c8868-164">Azure 계정이 아직 없는 경우 새로 만들려면 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-164">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="c8868-165">클래스 룸 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 새 계정 설정 도움말에 대 한 여력 중 하나를 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-165">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

5.  <span data-ttu-id="c8868-166">처음으로 로그인 한 후 메시지가 표시 됩니다와 합니다 *서비스 약관* 패널입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-166">Once you are logged in for the first time, you will be prompted with the *Terms of Service* panel.</span></span> <span data-ttu-id="c8868-167">확인란을 클릭 *약관에 동의*합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-167">Click the checkbox to *agree to the terms*.</span></span> <span data-ttu-id="c8868-168">누른 **동의 함**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-168">Then click **I agree**.</span></span>

    ![](images/AzureLabs-Lab310-03.png)

6.  <span data-ttu-id="c8868-169">조건에 동의 하지, 현재 위치는 합니다 *내 프로젝트* 섹션입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-169">Having agreed to the terms, you are now in the *My Projects* section.</span></span> <span data-ttu-id="c8868-170">클릭할 **새 프로젝트**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-170">Click on **New Project**.</span></span>

    ![](images/AzureLabs-Lab310-04.png)

7.  <span data-ttu-id="c8868-171">탭은 프로젝트의 일부 필드를 지정 하 라는 메시지가 표시 됩니다는 오른쪽에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-171">A tab will appear on the right-hand side, which will prompt you to specify some fields for the project.</span></span>

    1.  <span data-ttu-id="c8868-172">프로젝트 이름을 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-172">Insert a name for your project</span></span>

    2.  <span data-ttu-id="c8868-173">프로젝트에 대 한 설명을 삽입 (**선택 사항**)</span><span class="sxs-lookup"><span data-stu-id="c8868-173">Insert a description for your project (**Optional**)</span></span>

    3.  <span data-ttu-id="c8868-174">선택 된 **리소스 그룹** 하거나 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-174">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="c8868-175">리소스 그룹에는 모니터링, 프로 비전, 액세스 제어 및 Azure 자산 모음에 대 한 청구를 관리 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-175">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="c8868-176">것이 좋습니다 (예: 이러한 교육 과정)와 같은 일반적인 리소스 그룹에서 단일 프로젝트와 연결 된 모든 Azure 서비스를 유지).</span><span class="sxs-lookup"><span data-stu-id="c8868-176">It is recommended to keep all the Azure services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > <span data-ttu-id="c8868-177">하려는 경우 [자세한 Azure 리소스 그룹에 대 한 연결된 Docs로 이동](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span><span class="sxs-lookup"><span data-stu-id="c8868-177">If you wish to [read more about Azure Resource Groups, navigate to the associated Docs](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span></span>

    4.  <span data-ttu-id="c8868-178">설정 된 **프로젝트 형식** 으로 **개체 감지 (미리 보기)** 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-178">Set the **Project Types** as **Object Detection (preview)**.</span></span>

8.  <span data-ttu-id="c8868-179">완료 되 면 클릭할 **프로젝트 만들기**, 및 Custom Vision Service 프로젝트 페이지로 리디렉션됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-179">Once you are finished, click on **Create project**, and you will be redirected to the Custom Vision Service project page.</span></span>


## <a name="chapter-2---training-your-custom-vision-project"></a><span data-ttu-id="c8868-180">2 장-프로젝트에 사용자 지정 비전 교육</span><span class="sxs-lookup"><span data-stu-id="c8868-180">Chapter 2 - Training your Custom Vision project</span></span>

<span data-ttu-id="c8868-181">한 번 사용자 지정 비전 포털의 기본 목표가 방법은 학습 이미지에서 특정 개체를 인식 하 여 프로젝트입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-181">Once in the Custom Vision Portal, your primary objective is to train your project to recognize specific objects in images.</span></span>

<span data-ttu-id="c8868-182">원하는 응용 프로그램을 인식 하는 각 개체에 대해 적어도 15 개의 이미지를 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-182">You need at least fifteen (15) images for each object that you would like your application to recognize.</span></span> <span data-ttu-id="c8868-183">이 과정을 통해 제공 되는 이미지를 사용할 수 있습니다 ([cup 일련](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span><span class="sxs-lookup"><span data-stu-id="c8868-183">You can use the images provided with this course ([a series of cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span></span>

<span data-ttu-id="c8868-184">Custom Vision 프로젝트를 학습 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-184">To train your Custom Vision project:</span></span>

1.  <span data-ttu-id="c8868-185">클릭 합니다 **+** 옆에 단추 **태그**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-185">Click on the **+** button next to **Tags**.</span></span>

    ![](images/AzureLabs-Lab310-06.png)

2.  <span data-ttu-id="c8868-186">추가 된 **이름을** 사용 하 여 이미지를 연결 하는 데 사용할 수 있는 태그입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-186">Add a **name** for the tag that will be used to associate your images with.</span></span> <span data-ttu-id="c8868-187">Cup 이미지 인식,이 대 한 태그는 명명 된 하므로 사용 하는 것이 예제의 **Cup**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-187">In this example we are using images of cups for recognition, so have named the tag for this, **Cup**.</span></span> <span data-ttu-id="c8868-188">클릭 **저장할** 한 번 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-188">Click **Save** once finished.</span></span>

    ![](images/AzureLabs-Lab310-07.png)

3.  <span data-ttu-id="c8868-189">알 수 있습니다 하 **태그** 추가 되었습니다 (표시에 대 한 페이지를 다시 로드 해야 할).</span><span class="sxs-lookup"><span data-stu-id="c8868-189">You will notice your **Tag** has been added (you may need to reload your page for it to appear).</span></span> 

    ![](images/AzureLabs-Lab310-08.png)

4.  <span data-ttu-id="c8868-190">클릭할 **이미지 추가** 페이지의 가운데에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-190">Click on **Add images** in the center of the page.</span></span>

    ![](images/AzureLabs-Lab310-09.png)

5.  <span data-ttu-id="c8868-191">클릭할 **로컬 파일 찾아보기**, 하나의 개체에 대 한 15 최소 되 고 사용 하 여 (15) 업로드 하려는 이미지를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-191">Click on **Browse local files**, and browse to the images you would like to upload for one object, with the minimum being fifteen (15).</span></span>

    > [!TIP]
    >  <span data-ttu-id="c8868-192">업로드 한 번에 여러 이미지를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-192">You can select several images at a time, to upload.</span></span>

    ![](images/AzureLabs-Lab310-10.png)

6.  <span data-ttu-id="c8868-193">키를 눌러 **파일 업로드** 사용 하 여 프로젝트를 학습 하려는 모든 이미지를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-193">Press **Upload files** once you have selected all the images you would like to train the project with.</span></span> <span data-ttu-id="c8868-194">파일 업로드를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-194">The files will begin uploading.</span></span> <span data-ttu-id="c8868-195">업로드 확인 했으면 클릭 **수행**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-195">Once you have confirmation of the upload, click **Done**.</span></span>

    ![](images/AzureLabs-Lab310-11.png)

7.  <span data-ttu-id="c8868-196">이 시점에서 이미지 업로드 되지만 태그가 지정 되지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-196">At this point your images are uploaded, but not tagged.</span></span>

    ![](images/AzureLabs-Lab310-12.png)

8.  <span data-ttu-id="c8868-197">이미지에 태그를 추가 하 여 마우스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-197">To tag your images, use your mouse.</span></span> <span data-ttu-id="c8868-198">이미지를 가리키면 강조 표시 선택 영역이 때문에 개체 주위에 선택 영역을 자동으로 그려 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-198">As you hover over your image, a selection highlight will aid you by automatically drawing a selection around your object.</span></span> <span data-ttu-id="c8868-199">정확 하지 않으면 고유한 그릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-199">If it is not accurate, you can draw your own.</span></span> <span data-ttu-id="c8868-200">이렇게 하려면 개체를 포함 하도록 선택 영역을 끌어서 마우스 왼쪽 단추 클릭 마우스의 보유 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-200">This is accomplished by holding left-click on the mouse, and dragging the selection region to encompass your object.</span></span> 

    ![](images/AzureLabs-Lab310-13.png) 

9. <span data-ttu-id="c8868-201">선택 된 이미지 내의 개체의 다음 작은 프롬프트 수 묻습니다 *Region 태그 추가*합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-201">Following the selection of your object within the image, a small prompt will ask for you to *Add Region Tag*.</span></span> <span data-ttu-id="c8868-202">이전에 만든된 태그 ('Cup'를 위 예제의)를 선택 하거나 더 많은 태그를 추가 하는 경우에 입력 하 고 클릭 합니다 **+ (더하기)** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-202">Select your previously created tag ('Cup', in the above example), or if you are adding more tags, type that in and click the **+ (plus)** button.</span></span>

    ![](images/AzureLabs-Lab310-14.png) 

10. <span data-ttu-id="c8868-203">다음 이미지에 태그를 추가 하는 블레이드의 오른쪽 화살표를 클릭 하거나 태그 블레이드를 닫을 수 있습니다 (클릭 하 여 합니다 **X** 블레이드의 오른쪽 위 모서리에서) 다음 이미지를 클릭 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-203">To tag the next image, you can click the arrow to the right of the blade, or close the tag blade (by clicking the **X** in the top-right corner of the blade) and then click the next image.</span></span> <span data-ttu-id="c8868-204">준비 된 다음 이미지를 만든 후에 동일한 절차를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-204">Once you have the next image ready, repeat the same procedure.</span></span> <span data-ttu-id="c8868-205">모든 이미지를 업로드 하면 모든 태그가 지정 됩니다 될 때까지이 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-205">Do this for all the images you have uploaded, until they are all tagged.</span></span> 

    > [!NOTE]
    >  <span data-ttu-id="c8868-206">아래 이미지와 같이 동일한 이미지에서 여러 개체를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-206">You can select several objects in the same image, like the image below:</span></span> 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. <span data-ttu-id="c8868-207">모든 태그가 지정를 클릭 합니다 **태그가 지정 된** 태그가 지정 된 이미지를 표시 하려면 화면 왼쪽의 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-207">Once you have tagged them all, click on the **tagged** button, on the left of the screen, to reveal the tagged images.</span></span> 

    ![](images/AzureLabs-Lab310-16.png)

12. <span data-ttu-id="c8868-208">이제 서비스를 학습 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-208">You are now ready to train your Service.</span></span> <span data-ttu-id="c8868-209">클릭 합니다 **학습** 단추 및 첫 번째 학습 반복이 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-209">Click the **Train** button, and the first training iteration will begin.</span></span>

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. <span data-ttu-id="c8868-210">을 작성 하는 라는 두 개의 단추를 볼 수는 **기본값으로** 하 고 **예측 URL**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-210">Once it is built, you will be able to see two buttons called **Make default** and **Prediction URL**.</span></span> <span data-ttu-id="c8868-211">클릭할 **기본값으로** 첫째, 클릭 **예측 URL**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-211">Click on **Make default** first, then click on **Prediction URL**.</span></span>

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > <span data-ttu-id="c8868-212">이 제공 되는 끝점 중로 설정 되어 *반복* 기본으로 표시 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-212">The endpoint which is provided from this, is set to whichever *Iteration* has been marked as default.</span></span> <span data-ttu-id="c8868-213">따라서 새를 나중에 확인 하는 경우 *반복* 기본값으로 업데이트, 코드를 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-213">As such, if you later make a new *Iteration* and update it as default, you will not need to change your code.</span></span>

14. <span data-ttu-id="c8868-214">클릭 한 후 **예측 URL**오픈 *메모장*, 복사 및 붙여넣기를 **URL** (라고도 하 **예측 끝점**) 하며 **서비스 예측 키**코드에서 나중에 필요할 때 검색할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-214">Once you have clicked on **Prediction URL**, open *Notepad*, and copy and paste the **URL** (also called your **Prediction-Endpoint**) and the **Service Prediction-Key**, so that you can retrieve it when you need it later in the code.</span></span>

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="c8868-215">3 장-Unity 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="c8868-215">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="c8868-216">다음은 일반적인 등록 혼합된 현실 등을 사용 하 여 개발 하는 것에 대 한와 따라서 다른 프로젝트에 대 한 좋은 템플릿입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-216">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="c8868-217">오픈 **Unity** 누릅니다 **새로 만들기**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-217">Open **Unity** and click **New**.</span></span>

    ![](images/AzureLabs-Lab310-21.png)

2.  <span data-ttu-id="c8868-218">이제 Unity 프로젝트 이름을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-218">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="c8868-219">삽입 **CustomVisionObjDetection**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-219">Insert **CustomVisionObjDetection**.</span></span> <span data-ttu-id="c8868-220">프로젝트 형식 설정 되어 있는지 확인 **3D**를 설정 합니다 **위치** 적절 한 위치로 (기억에 루트 디렉터리에 가까울수록 더).</span><span class="sxs-lookup"><span data-stu-id="c8868-220">Make sure the project type is set to **3D**, and set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="c8868-221">그런 다음 클릭 **프로젝트 만들기**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-221">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab310-22.png)

3.  <span data-ttu-id="c8868-222">Unity 열기를 사용 하 여 기본 검사 가치가 **스크립트 편집기** 로 설정 된 **Visual Studio**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-222">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="c8868-223">로 이동 **편집할* > *기본 설정** 로 이동한 다음 새 창에서 **외부 도구**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-223">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="c8868-224">변경 **외부 스크립트 편집기** 하 **Visual Studio**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-224">Change **External Script Editor** to **Visual Studio**.</span></span> <span data-ttu-id="c8868-225">닫기 합니다 **기본 설정** 창입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-225">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab310-23.png)

4.  <span data-ttu-id="c8868-226">이동한 다음 **파일 > 빌드 설정** 전환 합니다 **플랫폼** 에 *유니버설 Windows 플랫폼*, 클릭는 **플랫폼 전환** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-226">Next, go to **File > Build Settings** and switch the **Platform** to *Universal Windows Platform*, and then clicking on the **Switch Platform** button.</span></span>

    ![](images/AzureLabs-Lab310-24.png)

5.  <span data-ttu-id="c8868-227">동일한 **빌드 설정** 창에서 다음 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-227">In the same **Build Settings** window, ensure the following are set:</span></span>

    1.  <span data-ttu-id="c8868-228">**장치를 대상** 로 설정 된 **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="c8868-228">**Target Device** is set to **HoloLens**</span></span>        
    2.  <span data-ttu-id="c8868-229">**빌드 형식** 로 설정 된 **D3D**</span><span class="sxs-lookup"><span data-stu-id="c8868-229">**Build Type** is set to **D3D**</span></span>
    3.  <span data-ttu-id="c8868-230">**SDK** 로 설정 된 **가장 최근에 설치 된**</span><span class="sxs-lookup"><span data-stu-id="c8868-230">**SDK** is set to **Latest installed**</span></span>
    4.  <span data-ttu-id="c8868-231">**Visual Studio 버전** 로 설정 된 **가장 최근에 설치 된**</span><span class="sxs-lookup"><span data-stu-id="c8868-231">**Visual Studio Version** is set to **Latest installed**</span></span>
    5.  <span data-ttu-id="c8868-232">**빌드 및 실행** 로 설정 된 **로컬 컴퓨터**</span><span class="sxs-lookup"><span data-stu-id="c8868-232">**Build and Run** is set to **Local Machine**</span></span>            
    6.  <span data-ttu-id="c8868-233">설정에 남아 **빌드 설정**, 지금은 기본값으로 유지 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-233">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

        ![](images/AzureLabs-Lab310-25.png)

6.  <span data-ttu-id="c8868-234">동일한 **빌드 설정** 창을 합니다 **플레이어 설정** 단추를 공간에 관련 된 패널이 열립니다이 위치를 **검사기** 위치한.</span><span class="sxs-lookup"><span data-stu-id="c8868-234">In the same **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

7. <span data-ttu-id="c8868-235">이 패널에서 몇 가지 설정을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-235">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="c8868-236">에 **기타 설정** 탭:</span><span class="sxs-lookup"><span data-stu-id="c8868-236">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="c8868-237">**스크립팅 런타임 버전** 있어야 **실험적** (.NET 4.6 동등), 편집기를 다시 시작 해야를 트리거하는 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-237">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="c8868-238">**백 엔드를 스크립팅** 있어야 **.NET**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-238">**Scripting Backend** should be **.NET**.</span></span>

        3. <span data-ttu-id="c8868-239">**API 호환성 수준** 있어야 **.NET 4.6**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-239">**API Compatibility Level** should be **.NET 4.6**.</span></span>

            ![](images/AzureLabs-Lab310-26.png)

    2.  <span data-ttu-id="c8868-240">내 합니다 **게시 설정** 탭의 **기능**, 확인:</span><span class="sxs-lookup"><span data-stu-id="c8868-240">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="c8868-241">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="c8868-241">**InternetClient**</span></span>

        2.  <span data-ttu-id="c8868-242">**웹캠**</span><span class="sxs-lookup"><span data-stu-id="c8868-242">**Webcam**</span></span>

        3. <span data-ttu-id="c8868-243">**SpatialPerception**</span><span class="sxs-lookup"><span data-stu-id="c8868-243">**SpatialPerception**</span></span>

            <span data-ttu-id="c8868-244">![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)</span><span class="sxs-lookup"><span data-stu-id="c8868-244">![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)</span></span>

    3.  <span data-ttu-id="c8868-245">패널을 아래쪽의 **xr 하이 설정을** (아래에서 확인할 **게시 설정**), 눈금 **지원 되는 가상 현실**, 있는지 확인 합니다는 **Windows 혼합 실제로 SDK** 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, then make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![](images/AzureLabs-Lab310-29.png)

8.  <span data-ttu-id="c8868-246">년대 **빌드 설정**를 *Unity C\# 프로젝트* 를 더 이상 사용할 수 없습니다:이 옆의 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-246">Back in **Build Settings**, *Unity C\# Projects* is no longer greyed out: tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="c8868-247">닫기 합니다 **빌드 설정** 창입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-247">Close the **Build Settings** window.</span></span>

10. <span data-ttu-id="c8868-248">에 **편집기**, 클릭 **편집** > **프로젝트 설정** > **그래픽**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-248">In the **Editor**, click on **Edit** > **Project Settings** > **Graphics**.</span></span>

    ![](images/AzureLabs-Lab310-30.png)

11. <span data-ttu-id="c8868-249">에 **검사기 패널** 는 *그래픽 설정* 열립니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-249">In the **Inspector Panel** the *Graphics Settings* will be open.</span></span> <span data-ttu-id="c8868-250">라는 배열을 표시 될 때까지 아래로 스크롤하여 **셰이더를 항상 포함**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-250">Scroll down until you see an array called **Always Include Shaders**.</span></span> <span data-ttu-id="c8868-251">늘려 슬롯을 추가 합니다 **크기** 씩 변수 (이 예제에서는 8 인 았 어 있으므로 9).</span><span class="sxs-lookup"><span data-stu-id="c8868-251">Add a slot by increasing the **Size** variable by one (in this example, it was 8 so we made it 9).</span></span> <span data-ttu-id="c8868-252">새 슬롯이 나타납니다 배열의 마지막 위치에 아래와 같이:</span><span class="sxs-lookup"><span data-stu-id="c8868-252">A new slot will appear, in the last position of the array, as shown below:</span></span>

    ![](images/AzureLabs-Lab310-31.png)

12. <span data-ttu-id="c8868-253">슬롯에서 슬롯 셰이더 목록을 열려면 옆의 작은 대상 원을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-253">In the slot, click on the small target circle next to the slot to open a list of shaders.</span></span> <span data-ttu-id="c8868-254">검색할 합니다 **레거시 셰이더/Transparent/확산** 셰이더 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-254">Look for the **Legacy Shaders/Transparent/Diffuse** shader and double-click it.</span></span> 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a><span data-ttu-id="c8868-255">4 장-CustomVisionObjDetection Unity 패키지 가져오기</span><span class="sxs-lookup"><span data-stu-id="c8868-255">Chapter 4 - Importing the CustomVisionObjDetection Unity package</span></span>

<span data-ttu-id="c8868-256">Unity 자산 패키지와 함께 제공 되는이 과정 이라는 **Azure-MR-310.unitypackage**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-256">For this course you are provided with a Unity Asset Package called **Azure-MR-310.unitypackage**.</span></span> 

> <span data-ttu-id="c8868-257">[팁] 전체 작업을 포함 하 여 Unity에서 지 원하는 모든 개체에 패키징할 수 있습니다는 **.unitypackage** 파일 및 내보낸 / 다른 프로젝트에서 가져온입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-257">[TIP] Any objects supported by Unity, including entire scenes, can be packaged into a **.unitypackage** file, and exported / imported in other projects.</span></span> <span data-ttu-id="c8868-258">서로 다른 자산을 이동할, 가장 안전 하 고 가장 효율적인 방법입니다 **Unity 프로젝트**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-258">It is the safest, and most efficient, way to move assets between different **Unity projects**.</span></span>

<span data-ttu-id="c8868-259">찾을 수 있습니다 합니다 [여기에서 다운로드 해야 하는 Azure-MR-310 패키지](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage)합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-259">You can find the [Azure-MR-310 package that you need to download here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage).</span></span>

1.  <span data-ttu-id="c8868-260">사용자 앞에 Unity 대시보드를 클릭 **자산** 화면의 맨 위에 있는 메뉴에서 클릭 **가져오기 패키지 > 사용자 지정 패키지**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-260">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package > Custom Package**.</span></span>

    ![](images/AzureLabs-Lab310-33.png)

2.  <span data-ttu-id="c8868-261">파일 선택기를 사용 하 여 선택 하는 **Azure-MR-310.unitypackage** 패키징하고 클릭 **열기**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-261">Use the file picker to select the **Azure-MR-310.unitypackage** package and click **Open**.</span></span> <span data-ttu-id="c8868-262">이 자산에 대 한 구성 요소 목록에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-262">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="c8868-263">가져오기를 클릭 하 여 확인 합니다 **가져올** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-263">Confirm the import by clicking the **Import** button.</span></span>

    ![](images/AzureLabs-Lab310-34.png)

3.  <span data-ttu-id="c8868-264">가져오기 완료 되 고, 패키지에서 폴더를 추가 이제가 확인할 수 있습니다 하 **자산** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-264">Once it has finished importing, you will notice that folders from the package have now been added to your **Assets** folder.</span></span> <span data-ttu-id="c8868-265">이 종류의 폴더 구조는 Unity 프로젝트에 대 한 일반적인입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-265">This kind of folder structure is typical for a Unity project.</span></span>

    ![](images/AzureLabs-Lab310-35.png)

    1.  <span data-ttu-id="c8868-266">합니다 **자료** 폴더에서 사용 하는 자료를 포함 합니다 **Gaze 커서**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-266">The **Materials** folder contains the material used by the **Gaze Cursor**.</span></span> 

    2.  <span data-ttu-id="c8868-267">합니다 **플러그 인** 폴더 코드에서 서비스 웹 응답을 deserialize 하는 데 사용 되는 Newtonsoft DLL이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-267">The **Plugins** folder contains the Newtonsoft DLL used by the code to deserialize the Service web response.</span></span> <span data-ttu-id="c8868-268">폴더 및 하위 폴더에 포함 된 2 개의 서로 다른 버전은 사용 되 고 Unity 편집기와 UWP 빌드에서 빌드된 라이브러리를 허용 하는 데 필요한입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-268">The two (2) different versions contained in the folder, and sub-folder, are necessary to allow the library to be used and built by both the Unity Editor and the UWP build.</span></span> 

    3.  <span data-ttu-id="c8868-269">합니다 **Prefabs** 장면에 포함 된 prefabs 폴더에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-269">The **Prefabs** folder contains the prefabs contained in the scene.</span></span> <span data-ttu-id="c8868-270">다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-270">Those are:</span></span>

        1.  <span data-ttu-id="c8868-271">합니다 **GazeCursor**, 응용 프로그램에 사용 되는 커서입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-271">The **GazeCursor**, the cursor used in the application.</span></span> <span data-ttu-id="c8868-272">실제 개체 위에 장면에 배치할 수 있게 되기를 SpatialMapping prefab 함께 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-272">Will work together with the SpatialMapping prefab to be able to be placed in the scene on top of physical objects.</span></span>
        2.  <span data-ttu-id="c8868-273">합니다 **레이블**, 개체인 UI 필요한 경우 장면에서 object 태그를 표시 하는 데 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-273">The **Label**, which is the UI object used to display the object tag in the scene when required.</span></span>
        3.  <span data-ttu-id="c8868-274">합니다 **SpatialMapping**를 사용 하도록 응용 프로그램을 활성화 하는 개체 공간 Microsoft HoloLens 추적을 사용 하 여 가상 맵을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-274">The **SpatialMapping**, which is the object that enables the application to use create a virtual map, using the Microsoft HoloLens' spatial tracking.</span></span>

    4.  <span data-ttu-id="c8868-275">합니다 **장면** 현재이 과정에 대 한 미리 작성된 된 장면을 포함 하는 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-275">The **Scenes** folder which currently contains the pre-built scene for this course.</span></span>

4.  <span data-ttu-id="c8868-276">열기를 **장면** 폴더에서는 **프로젝트 패널**, 두 번 클릭 하 고는 **ObjDetectionScene**,이 과정에 대해 사용할 장면을 로드 하 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-276">Open the **Scenes** folder, in the **Project Panel**, and double-click on the **ObjDetectionScene**, to load the scene that you will use for this course.</span></span>

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  <span data-ttu-id="c8868-277">**포함 된 코드가 없습니다**,이 과정을 수행 하 여 코드를 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-277">**No code is included**, you will write the code by following this course.</span></span>

## <a name="chapter-5---create-the-customvisionanalyser-class"></a><span data-ttu-id="c8868-278">-5 장 CustomVisionAnalyser 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-278">Chapter 5 - Create the CustomVisionAnalyser class.</span></span>

<span data-ttu-id="c8868-279">이 시점에서 일부 코드를 작성할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-279">At this point you are ready to write some code.</span></span> <span data-ttu-id="c8868-280">사용 하 여 시작 합니다 **CustomVisionAnalyser** 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-280">You will begin with the **CustomVisionAnalyser** class.</span></span>

> [!NOTE]
> <span data-ttu-id="c8868-281">에 대 한 호출을 **Custom Vision Service**아래에 표시 된 코드에서,를 사용 하 여는 **사용자 지정 비전 REST API**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-281">The calls to the **Custom Vision Service**, made in the code shown below, are made using the **Custom Vision REST API**.</span></span> <span data-ttu-id="c8868-282">이 사용 하 여을 통해 구현 (비슷한을 직접 구현 하는 방법을 이해 하는 데 유용함)이이 API를 사용 하는 방법을 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-282">Through using this, you will see how to implement and make use of this API (useful for understanding how to implement something similar on your own).</span></span> <span data-ttu-id="c8868-283">인식 하며 Microsoft 제공 하는 수를 **Custom Vision SDK** 서비스를 호출 하기 위해 사용할 수도 있는 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-283">Be aware, that Microsoft offers a **Custom Vision SDK** that can also be used to make calls to the Service.</span></span> <span data-ttu-id="c8868-284">자세한 내용은 참조는 [Custom Vision SDK 문서](https://github.com/Microsoft/Cognitive-CustomVision-Windows/)합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-284">For more information visit the [Custom Vision SDK article](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).</span></span>

<span data-ttu-id="c8868-285">이 클래스는 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-285">This class is responsible for:</span></span>

- <span data-ttu-id="c8868-286">캡처된 바이트의 배열로 최신 이미지를 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-286">Loading the latest image captured as an array of bytes.</span></span>

- <span data-ttu-id="c8868-287">Azure는 바이트 배열 보내기 **Custom Vision Service** 분석에 대 한 인스턴스.</span><span class="sxs-lookup"><span data-stu-id="c8868-287">Sending the byte array to your Azure **Custom Vision Service** instance for analysis.</span></span>

- <span data-ttu-id="c8868-288">JSON 문자열로 응답을 수신 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-288">Receiving the response as a JSON string.</span></span>

- <span data-ttu-id="c8868-289">응답을 역직렬화 하 고 결과 전달 **예측** 에 **SceneOrganiser** 응답을 표시 하는 방법을 처리 하는 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-289">Deserializing the response and passing the resulting **Prediction** to the **SceneOrganiser** class, which will take care of how the response should be displayed.</span></span>

<span data-ttu-id="c8868-290">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="c8868-290">To create this class:</span></span>

1.  <span data-ttu-id="c8868-291">마우스 오른쪽 단추로 클릭 합니다 **자산 폴더**에 있는 합니다 **프로젝트 패널**, 클릭 **만들기** > **폴더**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-291">Right-click in the **Asset Folder**, located in the **Project Panel**, then click **Create** > **Folder**.</span></span> <span data-ttu-id="c8868-292">폴더를 호출 **스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-292">Call the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab310-37.png)

2.  <span data-ttu-id="c8868-293">새로 만든된 폴더를 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-293">Double-click on the newly created folder, to open it.</span></span>

3.  <span data-ttu-id="c8868-294">폴더를 마우스 오른쪽 단추로 클릭 **Create** > **C\# 스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-294">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="c8868-295">스크립트 이름을 **CustomVisionAnalyser 합니다.**</span><span class="sxs-lookup"><span data-stu-id="c8868-295">Name the script **CustomVisionAnalyser.**</span></span>

4.  <span data-ttu-id="c8868-296">새 두 번 클릭 **CustomVisionAnalyser** 스크립트를 사용 하 여 열고 **Visual Studio입니다.**</span><span class="sxs-lookup"><span data-stu-id="c8868-296">Double-click on the new **CustomVisionAnalyser** script to open it with **Visual Studio.**</span></span>

5.  <span data-ttu-id="c8868-297">파일의 맨 위에서 참조 하는 다음 네임 스페이스가 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-297">Make sure you have the following namespaces referenced at the top of the file:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  <span data-ttu-id="c8868-298">에 **CustomVisionAnalyser** 클래스를 다음 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-298">In the **CustomVisionAnalyser** class, add the following variables:</span></span>

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
    > <span data-ttu-id="c8868-299">삽입 해야 하 **서비스 예측 키** 에 **predictionKey** 변수 및 **예측 끝점** 에 **predictionEndpoint**  변수입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-299">Make sure you insert your **Service Prediction-Key** into the **predictionKey** variable and your **Prediction-Endpoint** into the **predictionEndpoint** variable.</span></span> <span data-ttu-id="c8868-300">에 복사해 둔 [메모장 이전, Chapter 2 단계에서 14](#chapter-2---training-your-custom-vision-project)합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-300">You copied these to [Notepad earlier, in Chapter 2, Step 14](#chapter-2---training-your-custom-vision-project).</span></span>

7.  <span data-ttu-id="c8868-301">에 대 한 코드 **Awake()** 이제 인스턴스 변수를 초기화 하려면 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-301">Code for **Awake()** now needs to be added to initialize the Instance variable:</span></span>

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

8.  <span data-ttu-id="c8868-302">추가 코 루틴 (정적을 사용 하 여 **GetImageAsByteArray()** 아래 메서드)에서 캡처된 이미지의 분석 결과 얻을 합니다 **ImageCapture** 클래스.</span><span class="sxs-lookup"><span data-stu-id="c8868-302">Add the coroutine (with the static **GetImageAsByteArray()** method below it), which will obtain the results of the analysis of the image, captured by the **ImageCapture** class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c8868-303">에 **AnalyseImageCapture** 코 루틴을 호출 하는 **SceneOrganiser** 만들려면 아직 수 있는 클래스.</span><span class="sxs-lookup"><span data-stu-id="c8868-303">In the **AnalyseImageCapture** coroutine, there is a call to the **SceneOrganiser** class that you are yet to create.</span></span> <span data-ttu-id="c8868-304">따라서 **이러한 지금은 줄 주석**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-304">Therefore, **leave those lines commented for now**.</span></span>

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

9. <span data-ttu-id="c8868-305">삭제를 **start ()** 하 고 **update ()** 메서드를 사용 되지 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-305">Delete the **Start()** and **Update()** methods, as they will not be used.</span></span> 

10.  <span data-ttu-id="c8868-306">변경 내용을 저장 해야 **Visual Studio**를 반환 하기 전에 **Unity**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-306">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c8868-307">앞에서 설명한 대로 수행 걱정할 필요 없이 코드를 제공 하는 경우는 더욱 클래스는 곧 해결 됩니다에서 오류가 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-307">As mentioned earlier, do not worry about code which might appear to have an error, as you will provide further classes soon, which will fix these.</span></span>

## <a name="chapter-6---create-the-customvisionobjects-class"></a><span data-ttu-id="c8868-308">-6 장 CustomVisionObjects 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="c8868-308">Chapter 6 - Create the CustomVisionObjects class</span></span>

<span data-ttu-id="c8868-309">만든 클래스에서 이제는 합니다 **CustomVisionObjects** 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-309">The class you will create now is the **CustomVisionObjects** class.</span></span>

<span data-ttu-id="c8868-310">이 스크립트는 다른 클래스를 직렬화 및 역직렬화 Custom Vision Service에 대 한 호출에 사용 되는 개체의 수를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-310">This script contains a number of objects used by other classes to serialize and deserialize the calls made to the Custom Vision Service.</span></span>

<span data-ttu-id="c8868-311">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="c8868-311">To create this class:</span></span>

1.  <span data-ttu-id="c8868-312">마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 한 다음 **만들기** > **C\# 스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-312">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="c8868-313">스크립트를 호출 합니다 **CustomVisionObjects 합니다.**</span><span class="sxs-lookup"><span data-stu-id="c8868-313">Call the script **CustomVisionObjects.**</span></span>

2.  <span data-ttu-id="c8868-314">새 두 번 클릭 **CustomVisionObjects** 스크립트를 사용 하 여 열고 **Visual Studio입니다.**</span><span class="sxs-lookup"><span data-stu-id="c8868-314">Double-click on the new **CustomVisionObjects** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="c8868-315">파일의 맨 위에서 참조 하는 다음 네임 스페이스가 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-315">Make sure you have the following namespaces referenced at the top of the file:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="c8868-316">삭제를 **start ()** 및 **update ()** 내부 메서드를 **CustomVisionObjects** 클래스,이 클래스는 이제 비워둘 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-316">Delete the **Start()** and **Update()** methods inside the **CustomVisionObjects** class, this class should now be empty.</span></span>

    > [!WARNING]
    > <span data-ttu-id="c8868-317">신중 하 게 다음 지침을 따르는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-317">It is important you follow the next instruction carefully.</span></span> <span data-ttu-id="c8868-318">새 클래스 선언 안에 넣으면 합니다 **CustomVisionObjects** 클래스 컴파일 오류가 발생 합니다 [10 장](#chapter-10---create-the-imagecapture-class)않는다는, 하는 **AnalysisRootObject** 및  **BoundingBox** 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-318">If you put the new class declarations inside the **CustomVisionObjects** class, you will get compile errors in [chapter 10](#chapter-10---create-the-imagecapture-class), stating that **AnalysisRootObject** and **BoundingBox** are not found.</span></span>

5.  <span data-ttu-id="c8868-319">다음 클래스를 추가 *외부* 는 **CustomVisionObjects** 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-319">Add the following classes *outside* the **CustomVisionObjects** class.</span></span> <span data-ttu-id="c8868-320">사용 되는 이러한 개체는 **Newtonsoft** 응답 데이터 serialize 및 deserialize 하는 라이브러리:</span><span class="sxs-lookup"><span data-stu-id="c8868-320">These objects are used by the **Newtonsoft** library to serialize and deserialize the response data:</span></span>

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

6.  <span data-ttu-id="c8868-321">변경 내용을 저장 해야 **Visual Studio**를 반환 하기 전에 **Unity**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-321">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-7---create-the-spatialmapping-class"></a><span data-ttu-id="c8868-322">7-장 SpatialMapping 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="c8868-322">Chapter 7 - Create the SpatialMapping class</span></span>

<span data-ttu-id="c8868-323">이 클래스는 설정 된 **공간 매핑 Collider** 가상 개체와 실제 개체 간의 충돌을 감지할 수 있으므로 장면에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-323">This class will set the **Spatial Mapping Collider** in the scene so to be able to detect collisions between virtual objects and real objects.</span></span>

<span data-ttu-id="c8868-324">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="c8868-324">To create this class:</span></span>

1.  <span data-ttu-id="c8868-325">마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 한 다음 **만들기** > **C\# 스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-325">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="c8868-326">스크립트를 호출 합니다 **SpatialMapping 합니다.**</span><span class="sxs-lookup"><span data-stu-id="c8868-326">Call the script **SpatialMapping.**</span></span>

2.  <span data-ttu-id="c8868-327">새 두 번 클릭 **SpatialMapping** 스크립트를 사용 하 여 열고 **Visual Studio입니다.**</span><span class="sxs-lookup"><span data-stu-id="c8868-327">Double-click on the new **SpatialMapping** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="c8868-328">위에서 참조 된 다음 네임 스페이스가 있는지 확인 합니다 **SpatialMapping** 클래스:</span><span class="sxs-lookup"><span data-stu-id="c8868-328">Make sure you have the following namespaces referenced above the **SpatialMapping** class:</span></span>

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  <span data-ttu-id="c8868-329">그런 다음 내에서 다음 변수를 추가 합니다 **SpatialMapping** 위의 클래스는 **start ()** 메서드:</span><span class="sxs-lookup"><span data-stu-id="c8868-329">Then, add the following variables inside the **SpatialMapping** class, above the **Start()** method:</span></span>

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

5.  <span data-ttu-id="c8868-330">추가 된 **Awake()** 하 고 **start ()**:</span><span class="sxs-lookup"><span data-stu-id="c8868-330">Add the **Awake()** and **Start()**:</span></span>

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

6.  <span data-ttu-id="c8868-331">삭제 된 **update ()** 메서드.</span><span class="sxs-lookup"><span data-stu-id="c8868-331">Delete the **Update()** method.</span></span>

7.  <span data-ttu-id="c8868-332">변경 내용을 저장 해야 **Visual Studio**를 반환 하기 전에 **Unity**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-332">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>


## <a name="chapter-8---create-the-gazecursor-class"></a><span data-ttu-id="c8868-333">8-장 GazeCursor 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="c8868-333">Chapter 8 - Create the GazeCursor class</span></span>

<span data-ttu-id="c8868-334">이 클래스는 실제 공간에서 올바른 위치에 커서를 설정 하는 일을 담당 만들어 사용 합니다 **SpatialMappingCollider**이전 장에서 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-334">This class is responsible for setting up the cursor in the correct location in real space, by making use of the **SpatialMappingCollider**, created in the previous chapter.</span></span>

<span data-ttu-id="c8868-335">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="c8868-335">To create this class:</span></span>

1.  <span data-ttu-id="c8868-336">마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 한 다음 **만들기** > **C\# 스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-336">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="c8868-337">스크립트를 호출 합니다 **GazeCursor**</span><span class="sxs-lookup"><span data-stu-id="c8868-337">Call the script **GazeCursor**</span></span>

2.  <span data-ttu-id="c8868-338">새 두 번 클릭 **GazeCursor** 스크립트를 사용 하 여 열고 **Visual Studio입니다.**</span><span class="sxs-lookup"><span data-stu-id="c8868-338">Double-click on the new **GazeCursor** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="c8868-339">위에서 참조 된 네임 스페이스 했는지 확인 합니다 **GazeCursor** 클래스:</span><span class="sxs-lookup"><span data-stu-id="c8868-339">Make sure you have the following namespace referenced above the **GazeCursor** class:</span></span>

    ```csharp
    using UnityEngine;
    ```

4.  <span data-ttu-id="c8868-340">다음 내에서 다음 변수를 추가 합니다 **GazeCursor** 위의 클래스는 **start ()** 메서드.</span><span class="sxs-lookup"><span data-stu-id="c8868-340">Then add the following variable inside the **GazeCursor** class, above the **Start()** method.</span></span> 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  <span data-ttu-id="c8868-341">업데이트를 **start ()** 메서드를 다음 코드로:</span><span class="sxs-lookup"><span data-stu-id="c8868-341">Update the **Start()** method with the following code:</span></span>

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

6.  <span data-ttu-id="c8868-342">업데이트를 **update ()** 메서드를 다음 코드로:</span><span class="sxs-lookup"><span data-stu-id="c8868-342">Update the **Update()** method with the following code:</span></span>

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
    > <span data-ttu-id="c8868-343">에 대 한 오류에 대 한 걱정 하지 마십시오 합니다 **SceneOrganiser** 되 찾을 수 없으면 다음 장에서 만들려는 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-343">Do not worry about the error for the **SceneOrganiser** class not being found, you will create it in the next chapter.</span></span>

7. <span data-ttu-id="c8868-344">변경 내용을 저장 해야 **Visual Studio**를 반환 하기 전에 **Unity**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-344">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-9---create-the-sceneorganiser-class"></a><span data-ttu-id="c8868-345">9-장 SceneOrganiser 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="c8868-345">Chapter 9 - Create the SceneOrganiser class</span></span>

<span data-ttu-id="c8868-346">이 클래스는:</span><span class="sxs-lookup"><span data-stu-id="c8868-346">This class will:</span></span>

-   <span data-ttu-id="c8868-347">설정 된 *주 카메라* 적절 한 구성 요소를 연결 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-347">Set up the *Main Camera* by attaching the appropriate components to it.</span></span>

-   <span data-ttu-id="c8868-348">실제 및 위치에 해당 위치를 계산 하는 일을 담당 될 때 개체 감지 되 면을 **태그 레이블** 적절 한 근처 **태그 이름**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-348">When an object is detected, it will be responsible for calculating its position in the real world and place a **Tag Label** near it with the appropriate **Tag Name**.</span></span>    

<span data-ttu-id="c8868-349">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="c8868-349">To create this class:</span></span>

1.  <span data-ttu-id="c8868-350">마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 한 다음 **만들기** > **C\# 스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-350">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="c8868-351">스크립트 이름을 **SceneOrganiser**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-351">Name the script **SceneOrganiser**.</span></span>

2.  <span data-ttu-id="c8868-352">새 두 번 클릭 **SceneOrganiser** 스크립트를 사용 하 여 열고 **Visual Studio입니다.**</span><span class="sxs-lookup"><span data-stu-id="c8868-352">Double-click on the new **SceneOrganiser** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="c8868-353">위에서 참조 된 다음 네임 스페이스가 있는지 확인 합니다 **SceneOrganiser** 클래스:</span><span class="sxs-lookup"><span data-stu-id="c8868-353">Make sure you have the following namespaces referenced above the **SceneOrganiser** class:</span></span>

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  <span data-ttu-id="c8868-354">다음 내에서 다음 변수를 추가 합니다 **SceneOrganiser** 위의 클래스는 **start ()** 메서드:</span><span class="sxs-lookup"><span data-stu-id="c8868-354">Then add the following variables inside the **SceneOrganiser** class, above the **Start()** method:</span></span>

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

5.  <span data-ttu-id="c8868-355">삭제 된 **start ()** 하 고 **update ()** 메서드.</span><span class="sxs-lookup"><span data-stu-id="c8868-355">Delete the **Start()** and **Update()** methods.</span></span>

6.  <span data-ttu-id="c8868-356">변수를 아래에 추가 합니다 **Awake()** 메서드 클래스를 초기화 하 고 장면 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-356">Underneath the variables, add the **Awake()** method, which will initialize the class and set up the scene.</span></span>

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

7.  <span data-ttu-id="c8868-357">추가 된 **PlaceAnalysisLabel()** 메서드를 *인스턴스화* (이 시점에서 표시 되지 않는 사용자에 게) 장면 레이블.</span><span class="sxs-lookup"><span data-stu-id="c8868-357">Add the **PlaceAnalysisLabel()** method, which will *Instantiate* the label in the scene (which at this point is invisible to the user).</span></span> <span data-ttu-id="c8868-358">또한는 쿼드 (또한 보이지 않음) 여기서 이미지 배치 되 면 하 고 실제와 겹치는 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-358">It also places the quad (also invisible) where the image is placed, and overlaps with the real world.</span></span> <span data-ttu-id="c8868-359">이 분석으로 실제 환경에서 개체의 대략적인 위치를 결정이 쿼드 다시 추적할지 후 서비스에서 검색 상자 좌표 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-359">This is important because the box coordinates retrieved from the Service after analysis are traced back into this quad to determined the approximate location of the object in the real world.</span></span> 

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

8.  <span data-ttu-id="c8868-360">추가 된 **FinaliseLabel()** 메서드.</span><span class="sxs-lookup"><span data-stu-id="c8868-360">Add the **FinaliseLabel()** method.</span></span> <span data-ttu-id="c8868-361">이 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-361">It is responsible for:</span></span>

    *   <span data-ttu-id="c8868-362">설정 합니다 *레이블* 텍스트를 *태그* 가장 안정적으로 예측 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-362">Setting the *Label* text with the *Tag* of the Prediction with the highest confidence.</span></span>
    *   <span data-ttu-id="c8868-363">계산을 호출 합니다 *경계 상자* 에 이전에 있는 4 개의 개체, 장면에 레이블을 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-363">Calling the calculation of the *Bounding Box* on the quad object, positioned previously, and placing the label in the scene.</span></span>
    *   <span data-ttu-id="c8868-364">방향으로 Raycast를 사용 하 여 레이블 크기를 조정 합니다 *경계 상자*는 실제에서 개체에 대해 충돌 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-364">Adjusting the label depth by using a Raycast towards the *Bounding Box*, which should collide against the object in the real world.</span></span>
    * <span data-ttu-id="c8868-365">다른 이미지를 캡처할 수 있도록 하는 캡처 프로세스를 다시 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-365">Resetting the capture process to allow the user to capture another image.</span></span>

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

9.  <span data-ttu-id="c8868-366">추가 합니다 **CalculateBoundingBoxPosition()** 숫자로 변환 하는 데 필요한 계산을 호스트 하는 메서드는 *경계 상자* 좌표 서비스에서 검색 하 고 다시 쿼드에서 비례적으로.</span><span class="sxs-lookup"><span data-stu-id="c8868-366">Add the **CalculateBoundingBoxPosition()** method, which hosts a number of calculations necessary to translate the *Bounding Box* coordinates retrieved from the Service and recreate them proportionally on the quad.</span></span>

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

10. <span data-ttu-id="c8868-367">변경 내용을 저장 해야 **Visual Studio**를 반환 하기 전에 **Unity**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-367">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="c8868-368">계속 하기 전에 엽니다는 **CustomVisionAnalyser** 클래스 및 내 합니다 **AnalyseLastImageCaptured()** 메서드를 *주석 처리를 제거* 다음 줄:</span><span class="sxs-lookup"><span data-stu-id="c8868-368">Before you continue, open the **CustomVisionAnalyser** class, and within the **AnalyseLastImageCaptured()** method, *uncomment* the following lines:</span></span>
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
> <span data-ttu-id="c8868-369">걱정 하지 마십시오는 **ImageCapture** '을 찾을 수 없습니다' 메시지 클래스를 다음 장에서 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-369">Do not worry about the **ImageCapture** class 'could not be found' message, you will create it in the next chapter.</span></span>


## <a name="chapter-10---create-the-imagecapture-class"></a><span data-ttu-id="c8868-370">10-장 ImageCapture 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="c8868-370">Chapter 10 - Create the ImageCapture class</span></span>

<span data-ttu-id="c8868-371">다음 클래스를 만드는 것은 **ImageCapture** 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-371">The next class you are going to create is the **ImageCapture** class.</span></span>

<span data-ttu-id="c8868-372">이 클래스는 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-372">This class is responsible for:</span></span>

*   <span data-ttu-id="c8868-373">HoloLens 카메라를 사용 하 고 저장 하는 이미지를 캡처하는 *앱* 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-373">Capturing an image using the HoloLens camera and storing it in the *App* folder.</span></span>
*   <span data-ttu-id="c8868-374">처리 *누릅니다* 사용자에서 제스처입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-374">Handling *Tap* gestures from the user.</span></span>

<span data-ttu-id="c8868-375">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="c8868-375">To create this class:</span></span>

1.  <span data-ttu-id="c8868-376">로 이동 합니다 **스크립트** 이전에 만든 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-376">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="c8868-377">폴더를 마우스 오른쪽 단추로 클릭 **Create** > **C\# 스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-377">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="c8868-378">스크립트 이름을 **ImageCapture**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-378">Name the script **ImageCapture**.</span></span>

3.  <span data-ttu-id="c8868-379">새 두 번 클릭 **ImageCapture** 스크립트를 사용 하 여 열고 **Visual Studio입니다.**</span><span class="sxs-lookup"><span data-stu-id="c8868-379">Double-click on the new **ImageCapture** script to open it with **Visual Studio.**</span></span>

4.  <span data-ttu-id="c8868-380">파일의 맨 위에 있는 네임 스페이스를 다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-380">Replace the namespaces at the top of the file with the following:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="c8868-381">다음 내에서 다음 변수를 추가 합니다 **ImageCapture** 위의 클래스는 **start ()** 메서드:</span><span class="sxs-lookup"><span data-stu-id="c8868-381">Then add the following variables inside the **ImageCapture** class, above the **Start()** method:</span></span>

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

6.  <span data-ttu-id="c8868-382">에 대 한 코드 **Awake()** 하 고 **start ()** 메서드는 이제 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-382">Code for **Awake()** and **Start()** methods now needs to be added:</span></span>

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

7.  <span data-ttu-id="c8868-383">탭 제스처 발생할 때 호출 되는 처리기를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-383">Implement a handler that will be called when a Tap gesture occurs:</span></span>

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
    > <span data-ttu-id="c8868-384">커서를 놓으면 **녹색**, 즉, 카메라는 이미지를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-384">When the cursor is **green**, it means the camera is available to take the image.</span></span> <span data-ttu-id="c8868-385">커서를 놓으면 **빨간색**, 즉, 카메라 사용 중입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-385">When the cursor is **red**, it means the camera is busy.</span></span>

8.  <span data-ttu-id="c8868-386">응용 프로그램 이미지 캡처 프로세스를 시작 하 고 이미지를 저장 하는 데 사용 하는 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-386">Add the method that the application uses to start the image capture process and store the image:</span></span>

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

9.  <span data-ttu-id="c8868-387">사진을 캡처한 시간과 분석할 준비가 되었을 때 호출 되는 처리기를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-387">Add the handlers that will be called when the photo has been captured and for when it is ready to be analyzed.</span></span> <span data-ttu-id="c8868-388">결과 전달 되어는 **CustomVisionAnalyser** 분석 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-388">The result is then passed to the **CustomVisionAnalyser** for analysis.</span></span>

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

10. <span data-ttu-id="c8868-389">변경 내용을 저장 해야 **Visual Studio**를 반환 하기 전에 **Unity**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-389">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a><span data-ttu-id="c8868-390">11 장-장면에 있는 스크립트 설정</span><span class="sxs-lookup"><span data-stu-id="c8868-390">Chapter 11 - Setting up the scripts in the scene</span></span>

<span data-ttu-id="c8868-391">이 프로젝트에 필요한 코드를 모두 작성 했으므로 시간이 올바르게 작동 하기 위해를 prefabs 장면에 스크립트를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-391">Now that you have written all of the code necessary for this project, is time to set up the scripts in the scene, and on the prefabs, for them to behave correctly.</span></span>

1.  <span data-ttu-id="c8868-392">내에서 **Unity 편집기**의 **계층 패널**를 선택 합니다 **주 카메라**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-392">Within the **Unity Editor**, in the **Hierarchy Panel**, select the **Main Camera**.</span></span>
2.  <span data-ttu-id="c8868-393">에 **검사기 패널**를 사용 하 여는 **주 카메라** 클릭을 선택 **구성 요소 추가**, 검색 한 다음 **SceneOrganiser** 스크립트 및 두 번 클릭을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-393">In the **Inspector Panel**, with the **Main Camera** selected, click on **Add Component**, then search for **SceneOrganiser** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-38.png)

3.  <span data-ttu-id="c8868-394">에 **프로젝트 패널**를 엽니다는 **Prefabs 폴더**, 끌어를 **레이블** 으로 prefab를 *레이블* 빈 참조 대상의 영역을 입력는 **SceneOrganiser** 스크립트에 방금 추가한 합니다 *주 카메라*아래 이미지에서 보여준 것 처럼:</span><span class="sxs-lookup"><span data-stu-id="c8868-394">In the **Project Panel**, open the **Prefabs folder**, drag the **Label** prefab into the *Label* empty reference target input area, in the **SceneOrganiser** script that you have just added to the *Main Camera*, as shown in the image below:</span></span>

    ![](images/AzureLabs-Lab310-39.png)

4.  <span data-ttu-id="c8868-395">**계층 패널**를 선택 합니다 **GazeCursor** 자식의 **주 카메라**.</span><span class="sxs-lookup"><span data-stu-id="c8868-395">In the **Hierarchy Panel**, select the **GazeCursor** child of the **Main Camera**.</span></span>
5.  <span data-ttu-id="c8868-396">에 **검사기 패널**를 사용 하 여는 **GazeCursor** 클릭을 선택 **구성 요소 추가**, 검색 한 다음 **GazeCursor** 스크립트 및 두 번 클릭을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-396">In the **Inspector Panel**, with the **GazeCursor** selected, click on **Add Component**, then search for **GazeCursor** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-40.png)

6.  <span data-ttu-id="c8868-397">를 다시는 **계층 패널**를 선택 합니다 **SpatialMapping** 자식의 **주 카메라**.</span><span class="sxs-lookup"><span data-stu-id="c8868-397">Again, in the **Hierarchy Panel**, select the **SpatialMapping** child of the **Main Camera**.</span></span>
7.  <span data-ttu-id="c8868-398">에 **검사기 패널**를 사용 하 여는 **SpatialMapping** 클릭을 선택 **구성 요소 추가**, 검색 한 다음 **SpatialMapping** 스크립트 및 추가를 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-398">In the **Inspector Panel**, with the **SpatialMapping** selected, click on **Add Component**, then search for **SpatialMapping** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-41.png)

<span data-ttu-id="c8868-399">나머지 스크립트의 수를 하지 않은 일련의 코드에 의해 추가 됩니다는 **SceneOrganiser** 런타임에 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-399">The remaining scripts thats you have not set will be added by the code in the **SceneOrganiser** script, during runtime.</span></span>

## <a name="chapter-12---before-building"></a><span data-ttu-id="c8868-400">빌드하기 전에 12 장</span><span class="sxs-lookup"><span data-stu-id="c8868-400">Chapter 12 - Before building</span></span>

<span data-ttu-id="c8868-401">응용 프로그램의 철저 한 테스트를 수행 하려면 해야 테스트용으로 로드 하 여 Microsoft HoloLens 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-401">To perform a thorough test of your application you will need to sideload it onto your Microsoft HoloLens.</span></span>

<span data-ttu-id="c8868-402">를 수행 하기 전에 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-402">Before you do, ensure that:</span></span>

-  <span data-ttu-id="c8868-403">에 언급 된 모든 설정 합니다 [3 장](#chapter-3---set-up-the-unity-project) 올바르게 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-403">All the settings mentioned in the [Chapter 3](#chapter-3---set-up-the-unity-project) are set correctly.</span></span>
- <span data-ttu-id="c8868-404">스크립트 **SceneOrganiser** 에 연결할 때 합니다 **주 카메라** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-404">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span>
- <span data-ttu-id="c8868-405">스크립트 **GazeCursor** 에 연결할 때 합니다 **GazeCursor** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-405">The script **GazeCursor** is attached to the **GazeCursor** object.</span></span>
- <span data-ttu-id="c8868-406">스크립트 **SpatialMapping** 에 연결할 때 합니다 **SpatialMapping** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-406">The script **SpatialMapping** is attached to the **SpatialMapping** object.</span></span>
- <span data-ttu-id="c8868-407">[5 장](#chapter-5---create-the-customvisionanalyser-class), 6 단계:</span><span class="sxs-lookup"><span data-stu-id="c8868-407">In [Chapter 5](#chapter-5---create-the-customvisionanalyser-class), Step 6:</span></span>

    - <span data-ttu-id="c8868-408">삽입 해야 하 **서비스 예측 키** 에 **predictionKey** 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-408">Make sure you insert your **Service Prediction Key** into the **predictionKey** variable.</span></span>
    - <span data-ttu-id="c8868-409">삽입 한 사용자 **예측 끝점** 에 **predictionEndpoint** 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-409">You have inserted your **Prediction Endpoint** into the **predictionEndpoint** class.</span></span>

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a><span data-ttu-id="c8868-410">13-장 UWP 솔루션 및 테스트용으로 로드 응용 프로그램 만들기</span><span class="sxs-lookup"><span data-stu-id="c8868-410">Chapter 13 - Build the UWP solution and sideload your application</span></span>

<span data-ttu-id="c8868-411">Microsoft HoloLens 배포할 수 있게 될 UWP 솔루션으로 응용 프로그램을 빌드할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-411">You are now ready to build you application as a UWP Solution that you will be able to deploy on to the Microsoft HoloLens.</span></span> <span data-ttu-id="c8868-412">빌드 프로세스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-412">To begin the build process:</span></span>

1.  <span data-ttu-id="c8868-413">로 이동 **파일 > 빌드 설정**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-413">Go to **File > Build Settings**.</span></span>

2.  <span data-ttu-id="c8868-414">눈금 **Unity C\# 프로젝트**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-414">Tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="c8868-415">클릭할 **열고 장면 추가**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-415">Click on **Add Open Scenes**.</span></span> <span data-ttu-id="c8868-416">이렇게 하면 현재 열려 장면 빌드에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-416">This will add the currently open scene to the build.</span></span>

    ![](images/AzureLabs-Lab310-42.png)

4.  <span data-ttu-id="c8868-417">**빌드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-417">Click **Build**.</span></span> <span data-ttu-id="c8868-418">Unity가 시작 됩니다는 *파일 탐색기* 창을 만들고 다음에 앱을 빌드하는 폴더를 선택 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-418">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="c8868-419">해당 폴더를 이제 만들고 이름을 **앱**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-419">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="c8868-420">사용 하 여 다음 합니다 **앱** 폴더를 선택, 클릭 **폴더 선택**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-420">Then with the **App** folder selected, click **Select Folder**.</span></span>

5.  <span data-ttu-id="c8868-421">Unity 프로젝트를 빌드할 예정 된 **앱** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-421">Unity will begin building your project to the **App** folder.</span></span>

6.  <span data-ttu-id="c8868-422">한 번 Unity (약간의 시간이 걸릴 수 있습니다) 빌드 완료, 열립니다는 **파일 탐색기** 빌드 위치에 있는 창 (작업 표시줄에서 항상 windows에서 위에 나타나지 않을 수 있습니다 있지만 새 추가 대 한 알림을 확인 창)입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-422">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

7.  <span data-ttu-id="c8868-423">Microsoft HoloLens를 배포 하려면 해야 해당 장치의 IP 주소 (배포에 대 한 원격), 및도 하는지 확인 해야 했습니다 **개발자 모드** 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-423">To deploy on to Microsoft HoloLens, you will need the IP Address of that device (for Remote Deploy), and to ensure that it also has **Developer Mode** set.</span></span> <span data-ttu-id="c8868-424">가상 하드 디스크 파일에 대한 중요 정보를 제공하려면</span><span class="sxs-lookup"><span data-stu-id="c8868-424">To do this:</span></span>

    1.  <span data-ttu-id="c8868-425">에 HoloLens, 착용 하는 동안 엽니다는 **설정을**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-425">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="c8868-426">로 이동 **네트워크 및 인터넷** > **Wi-fi** > **고급 옵션**</span><span class="sxs-lookup"><span data-stu-id="c8868-426">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="c8868-427">참고 합니다 **IPv4** 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-427">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="c8868-428">다음으로 다시 이동할 **설정을**, 한 다음 **업데이트 및 보안** > **개발자를 위한**</span><span class="sxs-lookup"><span data-stu-id="c8868-428">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="c8868-429">설정할 **개발자 모드** *에서*합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-429">Set **Developer Mode** *On*.</span></span>

8.  <span data-ttu-id="c8868-430">새 Unity 빌드에 이동 (합니다 **앱** 폴더) 사용 하 여 솔루션 파일을 엽니다 **Visual Studio**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-430">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

9.  <span data-ttu-id="c8868-431">솔루션 구성 선택에서 **디버그**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-431">In the Solution Configuration select **Debug**.</span></span>

10. <span data-ttu-id="c8868-432">솔루션 플랫폼에서 선택 **x86, 원격 컴퓨터**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-432">In the Solution Platform, select **x86, Remote Machine**.</span></span> <span data-ttu-id="c8868-433">삽입 하 라는 메시지가 표시 됩니다는 **IP 주소** 원격 장치 (의 Microsoft HoloLens,이 경우 둔).</span><span class="sxs-lookup"><span data-stu-id="c8868-433">You will be prompted to insert the **IP address** of a remote device (the Microsoft HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab310-43.png)

11. <span data-ttu-id="c8868-434">로 이동 합니다 **빌드** 메뉴를 클릭 **솔루션 배포** 을 사이드 로드에 HoloLens에 응용 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-434">Go to the **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

12. <span data-ttu-id="c8868-435">앱 시작 준비가 Microsoft HoloLens 설치 된 앱 목록에 나타나야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-435">Your app should now appear in the list of installed apps on your Microsoft HoloLens, ready to be launched!</span></span>

### <a name="to-use-the-application"></a><span data-ttu-id="c8868-436">응용 프로그램을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-436">To use the application:</span></span>

* <span data-ttu-id="c8868-437">사용 하 여 학습 하는 개체를 확인 하 **Azure Custom Vision Service, 개체 감지**를 사용 하 여를 **탭 하기 제스처**합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-437">Look at an object, which you have trained with your **Azure Custom Vision Service, Object Detection**, and use the **Tap gesture**.</span></span>
* <span data-ttu-id="c8868-438">개체가 성공적으로 검색 되 면 세계 좌표 *레이블 텍스트* 태그 이름으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-438">If the object is successfully detected, a world-space *Label Text* will appear with the tag name.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c8868-439">사진을 캡처하고 서비스에 보낼 때마다에 서비스 페이지로 다시 이동 하 고 새로 캡처한 이미지를 사용 하 여 서비스를 다시 학습 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-439">Every time you capture a photo and send it to the Service, you can go back to the Service page and retrain the Service with the newly captured images.</span></span> <span data-ttu-id="c8868-440">를 시작할 때 것도 수정 해야 합니다 *경계 상자* 더 정확 하 게 서비스를 다시 학습 하 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-440">At the beginning, you will probably also have to correct the *Bounding Boxes* to be more accurate and retrain the Service.</span></span>

> [!NOTE]
> <span data-ttu-id="c8868-441">Microsoft HoloLens 센서 및/또는 Unity의 SpatialTrackingComponent 실제 개체를 기준으로 하는 적절 한 colliders, 배치에 실패 한 경우 배치 된 레이블 텍스트 개체 거의 나타나지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-441">The Label Text placed might not appear near the object when the Microsoft HoloLens sensors and/or the SpatialTrackingComponent in Unity fails to place the appropriate colliders, relative to the real world objects.</span></span> <span data-ttu-id="c8868-442">이 경우 다른 화면에서 응용 프로그램을 사용 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-442">Try to use the application on a different surface if that is the case.</span></span>

## <a name="your-custom-vision-object-detection-application"></a><span data-ttu-id="c8868-443">사용자 지정 비전, 개체 감지 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="c8868-443">Your Custom Vision, Object Detection application</span></span>

<span data-ttu-id="c8868-444">축 하 Azure Custom Vision, 이미지에서 개체를 인식 하 고 3D 공간에서 해당 개체에 대 한 대략적인 위치를 제공할 수 있는 개체 검색 API를 활용 하는 혼합된 현실 앱을 빌드 했습니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-444">Congratulations, you built a mixed reality app that leverages the Azure Custom Vision, Object Detection API, which can recognize an object from an image, and then provide an approximate position for that object in 3D space.</span></span>

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="c8868-445">보너스 연습</span><span class="sxs-lookup"><span data-stu-id="c8868-445">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="c8868-446">연습 1</span><span class="sxs-lookup"><span data-stu-id="c8868-446">Exercise 1</span></span>

<span data-ttu-id="c8868-447">3d에서 실제 개체를 래핑할 반투명 하 게 큐브는 사용할 텍스트 레이블 추가 *경계 상자*합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-447">Adding to the Text Label, use a semi-transparent cube to wrap the real object in a 3D *Bounding Box*.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="c8868-448">연습 2</span><span class="sxs-lookup"><span data-stu-id="c8868-448">Exercise 2</span></span>

<span data-ttu-id="c8868-449">더 많은 개체를 인식 하 여 Custom Vision Service를 학습 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-449">Train your Custom Vision Service to recognize more objects.</span></span>

### <a name="exercise-3"></a><span data-ttu-id="c8868-450">연습 3</span><span class="sxs-lookup"><span data-stu-id="c8868-450">Exercise 3</span></span>

<span data-ttu-id="c8868-451">개체 인식 되 면 소리를 재생 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8868-451">Play a sound when an object is recognized.</span></span>

### <a name="exercise-4"></a><span data-ttu-id="c8868-452">실습 4</span><span class="sxs-lookup"><span data-stu-id="c8868-452">Exercise 4</span></span>

<span data-ttu-id="c8868-453">앱을 분석 하는 동일한 이미지를 사용 하 여 서비스를 다시 학습에 따라서 서비스를 보다 정확 하 게 확인 API를 사용 하 여 (예측 및 교육을 동시에 수행 됨).</span><span class="sxs-lookup"><span data-stu-id="c8868-453">Use the API to re-train your Service with the same images your app is analyzing, so to make the Service more accurate (do both prediction and training simultaneously).</span></span>
