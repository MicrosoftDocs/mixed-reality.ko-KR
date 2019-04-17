---
title: MR 및 Azure 302b-Custom vision
description: 기계 학습 모델을 학습 하는 방법을 알아보려면이 과정을 완료 하 고 혼합된 현실 응용 프로그램에서 유사한 개체를 인식 하도록 학습된 된 모델을 사용 합니다.
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: azure, 혼합 현실, academy, unity, 자습서, api, 사용자 지정 비전, hololens, 몰입 형, vr
ms.openlocfilehash: e6e9782a8d559af660dc4765556f1e926c5360b1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600000"
---
>[!NOTE]
><span data-ttu-id="b6062-104">혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="b6062-105">따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="b6062-106">이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="b6062-107">지원 되는 장치에서 작업을 계속 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="b6062-108">새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="b6062-109">게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-302b-custom-vision"></a><span data-ttu-id="b6062-110">MR 및 Azure 302b: 사용자 지정 비전</span><span class="sxs-lookup"><span data-stu-id="b6062-110">MR and Azure 302b: Custom vision</span></span>

<span data-ttu-id="b6062-111">이 과정에서는 배웁니다는 제공 된 이미지 내에서 사용자 지정 시각적 콘텐츠를 인식 하는 방법이 혼합된 현실 응용 프로그램에서 Azure 사용자 지정 비전 기능을 사용 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-111">In this course, you will learn how to recognize custom visual content within a provided image, using Azure Custom Vision capabilities in a mixed reality application.</span></span>

<span data-ttu-id="b6062-112">이 서비스를 사용 하면 개체 이미지를 사용 하 여 기계 학습 모델을 학습할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-112">This service will allow you to train a machine learning model using object images.</span></span> <span data-ttu-id="b6062-113">그런 다음 Microsoft HoloLens 또는 몰입 형 (VR) 헤드셋에 대 한 사용자 PC에 연결 된 카메라의 카메라 캡처에 의해 제공 된 유사한 개체를 인식 하도록 학습된 된 모델을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-113">You will then use the trained model to recognize similar objects, as provided by the camera capture of Microsoft HoloLens or a camera connected to your PC for immersive (VR) headsets.</span></span>

![과정 결과](images/AzureLabs-Lab302b-00.png)

<span data-ttu-id="b6062-115">Azure Custom Vision는 Microsoft Cognitive 서비스 개발자는 사용자 지정 이미지 분류자를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-115">Azure Custom Vision is a Microsoft Cognitive Service which allows developers to build custom image classifiers.</span></span> <span data-ttu-id="b6062-116">이러한 분류자 인식 하도록 새 이미지를 사용 하 여 사용할 수 있습니다 하거나 분류 하 고 새 이미지 내의 개체 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-116">These classifiers can then be used with new images to recognize, or classify, objects within that new image.</span></span> <span data-ttu-id="b6062-117">서비스는 프로세스를 간소화 하는 간단 하 고, 사용 하기 쉬운 온라인 포털을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-117">The Service provides a simple, easy to use, online portal to streamline the process.</span></span> <span data-ttu-id="b6062-118">자세한 내용은 참조는 [Azure Custom Vision Service 페이지](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-118">For more information, visit the [Azure Custom Vision Service page](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).</span></span>

<span data-ttu-id="b6062-119">이 과정을 완료 하면 두 가지 모드로 작동할 수 있는 혼합된 현실 응용 프로그램을 갖게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-119">Upon completion of this course, you will have a mixed reality application which will be able to work in two modes:</span></span>

-   <span data-ttu-id="b6062-120">**분석 모드**: Custom Vision Service 수동으로 설정 이미지를 업로드, 태그를 만들고, 서비스를 학습 하 여 다른 개체 (이 경우 마우스 및 키보드)를 인식 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-120">**Analysis Mode**: setting up the Custom Vision Service manually by uploading images, creating tags, and training the Service to recognize different objects (in this case mouse and keyboard).</span></span> <span data-ttu-id="b6062-121">그런 다음 카메라를 사용 하 여 이미지를 캡처하고 실제 환경에서 이러한 개체를 인식 하는 HoloLens 앱을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-121">You will then create a HoloLens app that will capture images using the camera, and try to recognize those objects in the real world.</span></span>

-   <span data-ttu-id="b6062-122">**학습 모드**: 앱에서 "학습 모드" 수 있게 해 주는 코드를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-122">**Training Mode**: you will implement code that will enable a "Training Mode" in your app.</span></span> <span data-ttu-id="b6062-123">학습 모드를 사용 하면 HoloLens' 카메라를 사용 하 여 이미지를 캡처, 서비스에 캡처된 이미지를 업로드 및 사용자 지정 비전 모델을 학습 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-123">The training mode will allow you to capture images using the HoloLens' camera, upload the captured images to the Service, and train the custom vision model.</span></span>

<span data-ttu-id="b6062-124">이 코스 샘플 Unity 기반 응용 프로그램에 Custom Vision Service에서 결과 가져오는 방법을 배우게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-124">This course will teach you how to get the results from the Custom Vision Service into a Unity-based sample application.</span></span> <span data-ttu-id="b6062-125">사용자 지정 응용 프로그램을 작성 하려는 경우에 이러한 개념을 적용 하는 것이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-125">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="b6062-126">장치 지원</span><span class="sxs-lookup"><span data-stu-id="b6062-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="b6062-127">과정</span><span class="sxs-lookup"><span data-stu-id="b6062-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="b6062-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="b6062-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="b6062-129"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="b6062-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="b6062-130">MR 및 Azure 302b: 사용자 지정 비전</span><span class="sxs-lookup"><span data-stu-id="b6062-130">MR and Azure 302b: Custom vision</span></span></td><td style="text-align: center;"> <span data-ttu-id="b6062-131">✔️</span><span class="sxs-lookup"><span data-stu-id="b6062-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="b6062-132">✔️</span><span class="sxs-lookup"><span data-stu-id="b6062-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="b6062-133">이 과정 HoloLens에 주로 중점을 두고, 하는 동안 Windows Mixed Reality 몰입 형 (VR) 헤드셋을이 과정에서 배운 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="b6062-134">몰입 형 (VR) 헤드셋에 액세스할 수 있는 카메라 없기 때문에 PC에 연결 하는 외부 카메라를 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="b6062-135">과정을 따라가려면 정보 몰입 형 (VR) 헤드셋을 지원 하기 위해 사용 해야 합니다. 변경 내용에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b6062-136">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="b6062-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="b6062-137">이 자습서는 Unity 사용 하 여 기본 경험이 있는 개발자 용으로 설계 하 고 C#입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="b6062-138">또한 주의 필수 구성 요소 및이 문서에서 작성 된 지침을 나타내는 새로운 테스트 되었으며 (2018 년 7 월) 작성 시점에 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="b6062-139">내에서 나열 된 사용 가능한 최신 소프트웨어를 사용 하는 합니다 [도구를 설치](install-the-tools.md) 없습니다 가정이 과정에서 정보를 나열 된 것 보다 최신 소프트웨어에 맞게 보면 일치 완벽 하 게 됩니다 있지만 문서 아래.</span><span class="sxs-lookup"><span data-stu-id="b6062-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="b6062-140">다음 하드웨어 및 소프트웨어가이 과정에 대 한 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="b6062-141">개발 PC A [Windows Mixed Reality 호환](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 몰입 형 (VR) 헤드셋 개발용</span><span class="sxs-lookup"><span data-stu-id="b6062-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="b6062-142">Windows 10 Fall Creators Update (또는 이상) 사용 하도록 설정 하는 개발자 모드를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="b6062-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="b6062-143">최신 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="b6062-143">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="b6062-144">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="b6062-144">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="b6062-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="b6062-145">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="b6062-146">A [Windows Mixed Reality 몰입 형 (VR) 헤드셋](immersive-headset-hardware-details.md) 하거나 [Microsoft HoloLens](hololens-hardware-details.md) 개발자 모드를 설정 하 여</span><span class="sxs-lookup"><span data-stu-id="b6062-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="b6062-147">카메라 (몰입 형 헤드셋 개발용) PC에 연결</span><span class="sxs-lookup"><span data-stu-id="b6062-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="b6062-148">Azure 설정 및 사용자 지정 Vision API 검색에 대 한 인터넷 액세스</span><span class="sxs-lookup"><span data-stu-id="b6062-148">Internet access for Azure setup and Custom Vision API retrieval</span></span>
- <span data-ttu-id="b6062-149">일련의 최소 5 (5) 이미지 (10 개로 권장)를 인식 하도록 Custom Vision Service 원하는 각 개체에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-149">A series of at least five (5) images (ten (10) recommended) for each object that you would like the Custom Vision Service to recognize.</span></span> <span data-ttu-id="b6062-150">원하는 경우 사용할 수 있습니다 [(컴퓨터 마우스 및 키보드)이이 과정을 통해 이미 제공 되는 이미지 ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip)합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-150">If you wish, you can use [the images already provided with this course (a computer mouse and a keyboard) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="b6062-151">시작하기 전 주의 사항</span><span class="sxs-lookup"><span data-stu-id="b6062-151">Before you start</span></span>

1.  <span data-ttu-id="b6062-152">이 프로젝트를 구축 하는 문제 발생을 방지 하려면 것이 좋습니다 루트 또는 루트 거의 폴더에이 자습서에 언급 된 프로젝트를 만든 (오래 폴더 경로 빌드 시에는 문제가 발생할 수 있습니다).</span><span class="sxs-lookup"><span data-stu-id="b6062-152">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="b6062-153">설정 하 고 여 HoloLens를 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-153">Set up and test your HoloLens.</span></span> <span data-ttu-id="b6062-154">에 HoloLens 등록 설정을 지원 해야 하는 경우 [HoloLens 설치 문서를 참조 하도록](https://docs.microsoft.com/hololens/hololens-setup)합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-154">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="b6062-155">(때로는 도움이 각 사용자에 대 한 이러한 작업을 수행) 새 HoloLens 앱 개발을 시작할 때 보정 및 센서 튜닝을 수행 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-155">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="b6062-156">보정에 대 한 도움말을 따라이 [HoloLens 보정 문서 링크](calibration.md#hololens)합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-156">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="b6062-157">센서 조정에 대 한 도움말을 따라이 [HoloLens 센서 튜닝 문서 링크](sensor-tuning.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-157">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-custom-vision-service-portal"></a><span data-ttu-id="b6062-158">1 장-Custom Vision Service 포털</span><span class="sxs-lookup"><span data-stu-id="b6062-158">Chapter 1 - The Custom Vision Service Portal</span></span>

<span data-ttu-id="b6062-159">사용 하 여 *Custom Vision Service* Azure에서 응용 프로그램에 사용할 수 있도록 서비스의 인스턴스를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-159">To use the *Custom Vision Service* in Azure, you will need to configure an instance of the Service to be made available to your application.</span></span>

1.  <span data-ttu-id="b6062-160">먼저 [로 이동 합니다 *Custom Vision Service* 기본 페이지](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-160">First, [navigate to the *Custom Vision Service* main page](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span></span>

2.  <span data-ttu-id="b6062-161">클릭 합니다 **시작** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-161">Click on the **Get Started** button.</span></span>

    ![](images/AzureLabs-Lab302b-01.png)

3.  <span data-ttu-id="b6062-162">에 로그인 합니다 *Custom Vision Service* 포털입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-162">Sign in to the *Custom Vision Service* Portal.</span></span>

    ![](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > <span data-ttu-id="b6062-163">Azure 계정이 아직 없는 경우 새로 만들려면 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-163">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="b6062-164">클래스 룸 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 새 계정 설정 도움말에 대 한 여력 중 하나를 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-164">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

4.  <span data-ttu-id="b6062-165">처음으로 로그인 한 후 메시지가 표시 됩니다와 합니다 *서비스 약관* 패널입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-165">Once you are logged in for the first time, you will be prompted with the *Terms of Service* panel.</span></span> <span data-ttu-id="b6062-166">약관에 동의 하는 확인란을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-166">Click on the checkbox to agree to the terms.</span></span> <span data-ttu-id="b6062-167">클릭 **동의 함**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-167">Then click on **I agree**.</span></span>

    ![](images/AzureLabs-Lab302b-03.png)

5.  <span data-ttu-id="b6062-168">조건에 동의 하지, 있습니다를 탐색 합니다 *프로젝트* 포털의 섹션입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-168">Having agreed to the Terms, you will be navigated to the *Projects* section of the Portal.</span></span> <span data-ttu-id="b6062-169">클릭할 **새 프로젝트**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-169">Click on **New Project**.</span></span>

    ![](images/AzureLabs-Lab302b-04.png)

6.  <span data-ttu-id="b6062-170">탭은 프로젝트의 일부 필드를 지정 하 라는 메시지가 표시 됩니다는 오른쪽에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-170">A tab will appear on the right-hand side, which will prompt you to specify some fields for the project.</span></span>

    1.  <span data-ttu-id="b6062-171">삽입 된 *이름을* 프로젝트에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-171">Insert a *Name* for your project.</span></span>

    2.  <span data-ttu-id="b6062-172">삽입 된 *설명을* 프로젝트에 대 한 (*선택적*).</span><span class="sxs-lookup"><span data-stu-id="b6062-172">Insert a *Description* for your project (*optional*).</span></span>

    3.  <span data-ttu-id="b6062-173">선택 된 *리소스 그룹* 하거나 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-173">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="b6062-174">리소스 그룹에는 모니터링, 프로 비전, 액세스 제어 및 Azure 자산 모음에 대 한 청구를 관리 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="b6062-175">좋습니다 일반적인 리소스 그룹에서 (예: 이러한 교육 과정) 예: 단일 프로젝트와 연결 된 Azure 서비스를 모두 유지).</span><span class="sxs-lookup"><span data-stu-id="b6062-175">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

    4. <span data-ttu-id="b6062-176">설정 된 *프로젝트 형식* 에 **분류**</span><span class="sxs-lookup"><span data-stu-id="b6062-176">Set the *Project Types* to **Classification**</span></span>
    
    5. <span data-ttu-id="b6062-177">설정 된 *도메인* 으로 **일반**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-177">Set the *Domains* as **General**.</span></span>

        ![](images/AzureLabs-Lab302b-05.png)

        > <span data-ttu-id="b6062-178">추가 하려는 경우 Azure 리소스 그룹에 대 한 하세요 [리소스 그룹 방문해](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-178">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

7.  <span data-ttu-id="b6062-179">완료 되 면 클릭할 **프로젝트 만들기**, Custom Vision Service 프로젝트 페이지를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-179">Once you are finished, click on **Create project**, you will be redirected to the Custom Vision Service, project page.</span></span>

## <a name="chapter-2---training-your-custom-vision-project"></a><span data-ttu-id="b6062-180">2 장-프로젝트에 사용자 지정 비전 교육</span><span class="sxs-lookup"><span data-stu-id="b6062-180">Chapter 2 - Training your Custom Vision project</span></span>

<span data-ttu-id="b6062-181">한 번 Custom Vision 포털에 기본 목표가 이미지에서 특정 개체를 인식 하도록 프로젝트를 학습 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-181">Once in the Custom Vision portal, your primary objective is to train your project to recognize specific objects in images.</span></span> <span data-ttu-id="b6062-182">최소 5 개의 이미지 해야 하지만 10 (10)를 인식 하도록 응용 프로그램 원하는 각 개체에 대 한 기본 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-182">You need at least five (5) images, though ten (10) is preferred, for each object that you would like your application to recognize.</span></span> <span data-ttu-id="b6062-183">[(컴퓨터 마우스 및 키보드)이이 과정을 통해 제공 되는 이미지를 사용할 수 있습니다](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip)합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-183">[You can use the images provided with this course (a computer mouse and a keyboard)](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span></span> 

<span data-ttu-id="b6062-184">Custom Vision Service 프로젝트를 학습 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-184">To train your Custom Vision Service project:</span></span>

1.  <span data-ttu-id="b6062-185">클릭 합니다 **+** 단추 옆에 **태그입니다.**</span><span class="sxs-lookup"><span data-stu-id="b6062-185">Click on the **+** button next to **Tags.**</span></span>

    ![](images/AzureLabs-Lab302b-06.png)

2.  <span data-ttu-id="b6062-186">추가 된 **이름을** 인식 하려는 개체의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-186">Add the **name** of the object you would like to recognize.</span></span> <span data-ttu-id="b6062-187">클릭할 **저장할**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-187">Click on **Save**.</span></span>

    ![](images/AzureLabs-Lab302b-07.png)

3.  <span data-ttu-id="b6062-188">알 수 있습니다 하 **태그** 추가 되었습니다 (표시에 대 한 페이지를 다시 로드 해야 할).</span><span class="sxs-lookup"><span data-stu-id="b6062-188">You will notice your **Tag** has been added (you may need to reload your page for it to appear).</span></span> <span data-ttu-id="b6062-189">아직 선택 하지 않은 경우에 새 태그와 함께 확인란을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-189">Click the checkbox alongside your new tag, if it is not already checked.</span></span>

    ![](images/AzureLabs-Lab302b-08.png)

4.  <span data-ttu-id="b6062-190">클릭할 **이미지 추가** 페이지의 가운데에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-190">Click on **Add Images** in the center of the page.</span></span>

    ![](images/AzureLabs-Lab302b-09.png)

5.  <span data-ttu-id="b6062-191">클릭할 **로컬 파일 찾아보기**를 검색 하 고 최소 되 고 업로드 하려는 이미지를 선택 5 (5).</span><span class="sxs-lookup"><span data-stu-id="b6062-191">Click on **Browse local files**, and search, then select, the images you would like to upload, with the minimum being five (5).</span></span> <span data-ttu-id="b6062-192">이러한 이미지의 모든 교육 하는 개체를 포함 해야 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-192">Remember all of these images should contain the object which you are training.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="b6062-193">업로드 한 번에 여러 이미지를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-193">You can select several images at a time, to upload.</span></span>

6.  <span data-ttu-id="b6062-194">탭의 이미지를 보시 면에서 적절 한 태그를 선택 합니다 **태그 내** 상자입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-194">Once you can see the images in the tab, select the appropriate tag in the **My Tags** box.</span></span>

    ![](images/AzureLabs-Lab302b-10.png)

7.  <span data-ttu-id="b6062-195">클릭할 **파일 업로드**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-195">Click on **Upload files**.</span></span> <span data-ttu-id="b6062-196">파일 업로드를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-196">The files will begin uploading.</span></span> <span data-ttu-id="b6062-197">업로드 확인 했으면 클릭 **수행**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-197">Once you have confirmation of the upload, click **Done**.</span></span>

    ![](images/AzureLabs-Lab302b-11.png)

8.  <span data-ttu-id="b6062-198">새 동일한 프로세스를 반복 **태그** 라는 **키보드** 에 대 한 적절 한 사진 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-198">Repeat the same process to create a new **Tag** named **Keyboard** and upload the appropriate photos for it.</span></span> <span data-ttu-id="b6062-199">해야 **선택 취소** *마우스* 표시 하도록 새 태그를 만든 후는 *이미지를 추가할* 창.</span><span class="sxs-lookup"><span data-stu-id="b6062-199">Make sure to **uncheck** *Mouse* once you have created the new tags, so to show the *Add images* window.</span></span>

9.  <span data-ttu-id="b6062-200">태그가 설정 모두를 만든 후 클릭 **학습**, 첫 번째 학습 반복은 개발을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-200">Once you have both Tags set up, click on **Train**, and the first training iteration will start building.</span></span>

    ![](images/AzureLabs-Lab302b-12.png)

10. <span data-ttu-id="b6062-201">을 작성 하는 라는 두 개의 단추를 볼 수는 **기본값으로** 하 고 **예측 URL**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-201">Once it is built, you will be able to see two buttons called **Make default** and **Prediction URL**.</span></span> <span data-ttu-id="b6062-202">클릭할 **기본값으로** 첫째, 클릭 **예측 URL**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-202">Click on **Make default** first, then click on **Prediction URL**.</span></span>

    ![](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > <span data-ttu-id="b6062-203">끝점 URL이 제공 되는 중에 설정 되어 *반복* 기본으로 표시 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-203">The endpoint URL which is provided from this, is set to whichever *Iteration* has been marked as default.</span></span> <span data-ttu-id="b6062-204">따라서 새를 나중에 확인 하는 경우 *반복* 기본값으로 업데이트, 코드를 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-204">As such, if you later make a new *Iteration* and update it as default, you will not need to change your code.</span></span>

11. <span data-ttu-id="b6062-205">클릭 한 후 *예측 URL*오픈 *메모장*, 복사 및 붙여넣기 합니다 **URL** 및 **예측 키**수 있도록, 코드에서 나중에 필요할 때 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-205">Once you have clicked on *Prediction URL*, open *Notepad*, and copy and paste the **URL** and the **Prediction-Key**, so that you can retrieve it when you need it later in the code.</span></span>

    ![](images/AzureLabs-Lab302b-14.png)

12. <span data-ttu-id="b6062-206">클릭 합니다 **코그** 맨 위에 있는 화면의 오른쪽입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-206">Click on the **Cog** at the top right of the screen.</span></span>

    ![](images/AzureLabs-Lab302b-15.png)

13. <span data-ttu-id="b6062-207">복사를 **교육 키** 에 붙여 넣습니다를 *메모장*, 나중에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-207">Copy the **Training Key** and paste it into a *Notepad*, for later use.</span></span>

    ![](images/AzureLabs-Lab302b-16.png)

14. <span data-ttu-id="b6062-208">복사할 수도 하 **프로젝트 Id**에 붙여넣습니다 하 *메모장* 나중에 사용할 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-208">Also copy your **Project Id**, and also paste it into your *Notepad* file, for later use.</span></span>

    ![](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="b6062-209">3 장-Unity 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="b6062-209">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="b6062-210">다음은 일반적인 등록 혼합된 현실 등을 사용 하 여 개발 하는 것에 대 한와 따라서 다른 프로젝트에 대 한 좋은 템플릿입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-210">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="b6062-211">오픈 *Unity* 누릅니다 **새로 만들기**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-211">Open *Unity* and click **New**.</span></span>

    ![](images/AzureLabs-Lab302b-17.png)

2.  <span data-ttu-id="b6062-212">이제 Unity 프로젝트 이름을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-212">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="b6062-213">Insert **AzureCustomVision.**</span><span class="sxs-lookup"><span data-stu-id="b6062-213">Insert **AzureCustomVision.**</span></span> <span data-ttu-id="b6062-214">프로젝트 템플릿은 설정 되어 있는지 확인 **3D**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-214">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="b6062-215">설정 된 **위치** 적절 한 위치로 (기억에 루트 디렉터리에 가까울수록이 더 좋습니다).</span><span class="sxs-lookup"><span data-stu-id="b6062-215">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="b6062-216">그런 다음 클릭 **프로젝트 만들기**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-216">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab302b-18.png)

3.  <span data-ttu-id="b6062-217">Unity 열기를 사용 하 여 기본 검사 가치가 **스크립트 편집기** 로 설정 된 **Visual Studio**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-217">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="b6062-218">로 이동 **편집할* > *기본 설정** 로 이동한 다음 새 창에서 **외부 도구**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-218">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="b6062-219">변경 **외부 스크립트 편집기** 하 **Visual Studio 2017**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-219">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="b6062-220">닫기 합니다 **기본 설정** 창입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-220">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab302b-19.png)

4.  <span data-ttu-id="b6062-221">이동한 다음 **파일 > 빌드 설정** 선택한 **유니버설 Windows 플랫폼**를 클릭 합니다 **플랫폼 전환** 선택 항목을 적용 하려면 단추.</span><span class="sxs-lookup"><span data-stu-id="b6062-221">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![](images/AzureLabs-Lab302b-20.png)

5.  <span data-ttu-id="b6062-222">여전히 **파일 > 빌드 설정** 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-222">While still in **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="b6062-223">**장치를 대상** 로 설정 된 **Hololens**</span><span class="sxs-lookup"><span data-stu-id="b6062-223">**Target Device** is set to **Hololens**</span></span>

        > <span data-ttu-id="b6062-224">몰입 형 헤드셋, 설정 **대상 장치** 하 *모든 장치*합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-224">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>
        
    2.  <span data-ttu-id="b6062-225">**빌드 형식** 로 설정 된 **D3D**</span><span class="sxs-lookup"><span data-stu-id="b6062-225">**Build Type** is set to **D3D**</span></span>
    3.  <span data-ttu-id="b6062-226">**SDK** 로 설정 된 **가장 최근에 설치 된**</span><span class="sxs-lookup"><span data-stu-id="b6062-226">**SDK** is set to **Latest installed**</span></span>
    4.  <span data-ttu-id="b6062-227">**Visual Studio 버전** 로 설정 된 **가장 최근에 설치 된**</span><span class="sxs-lookup"><span data-stu-id="b6062-227">**Visual Studio Version** is set to **Latest installed**</span></span>
    5.  <span data-ttu-id="b6062-228">**빌드 및 실행** 로 설정 된 **로컬 컴퓨터**</span><span class="sxs-lookup"><span data-stu-id="b6062-228">**Build and Run** is set to **Local Machine**</span></span>
    6.  <span data-ttu-id="b6062-229">장면 저장 하 고 빌드에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-229">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="b6062-230">선택 하 여이 작업을 수행할 **열고 장면 추가**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-230">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="b6062-231">창 저장 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-231">A save window will appear.</span></span>

            ![](images/AzureLabs-Lab302b-21.png)

        2. <span data-ttu-id="b6062-232">새 폴더를 만들려면이 고 모든의 미래, 장면에 대 한 다음 선택 합니다 **새 폴더** 새 폴더를 만들려면 단추 이름을 **장면**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-232">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![](images/AzureLabs-Lab302b-22.png)

        3. <span data-ttu-id="b6062-233">새로 만든 열 **장면** 폴더를 선택한 다음는 *파일 이름:* 텍스트 필드에 입력 **CustomVisionScene**, 클릭 **저장**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-233">Open your newly created **Scenes** folder, and then in the *File name:* text field, type **CustomVisionScene**, then click on **Save**.</span></span>

            ![](images/AzureLabs-Lab302b-23.png)

            > <span data-ttu-id="b6062-234">주의 내에서 Unity 장면에 저장 해야 합니다 *자산* 폴더를 Unity 프로젝트와 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-234">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity project.</span></span> <span data-ttu-id="b6062-235">백그라운드에서 폴더 (및 다른 유사한 폴더)를 만들기 Unity 프로젝트를 구성 하는 일반적인 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-235">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>
            
    7.  <span data-ttu-id="b6062-236">설정에 남아 *빌드 설정*, 지금은 기본값으로 유지 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-236">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

        ![](images/AzureLabs-Lab302b-24.png)

6.  <span data-ttu-id="b6062-237">에 *빌드 설정* 창을 **플레이어 설정** 단추를 공간에 관련 된 패널이 열립니다이 위치를 *검사기* 위치한.</span><span class="sxs-lookup"><span data-stu-id="b6062-237">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span>

7. <span data-ttu-id="b6062-238">이 패널에서 몇 가지 설정을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-238">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="b6062-239">에 **기타 설정** 탭:</span><span class="sxs-lookup"><span data-stu-id="b6062-239">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="b6062-240">**스크립팅 런타임 버전** 해야 **실험적 (.NET 4.6 동등)**, 편집기를 다시 시작 해야 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-240">**Scripting Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**, which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="b6062-241">**백 엔드를 스크립팅** 있어야 **.NET**</span><span class="sxs-lookup"><span data-stu-id="b6062-241">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="b6062-242">**API 호환성 수준** 있어야 **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="b6062-242">**API Compatibility Level** should be **.NET 4.6**</span></span>

        ![](images/AzureLabs-Lab302b-25.png)

    2.  <span data-ttu-id="b6062-243">내 합니다 **게시 설정** 탭의 **기능**, 확인:</span><span class="sxs-lookup"><span data-stu-id="b6062-243">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="b6062-244">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="b6062-244">**InternetClient**</span></span>

        2.  <span data-ttu-id="b6062-245">**웹캠**</span><span class="sxs-lookup"><span data-stu-id="b6062-245">**Webcam**</span></span>

        3. <span data-ttu-id="b6062-246">**Microphone**</span><span class="sxs-lookup"><span data-stu-id="b6062-246">**Microphone**</span></span>

        ![](images/AzureLabs-Lab302b-26.png)

    3.  <span data-ttu-id="b6062-247">패널을 아래쪽의 **xr 하이 설정을** (아래에서 확인할 **게시 설정**), 눈금 **가상 현실 지원**, 있는지는 **Windows Mixed Reality SDK**  추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-247">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

    ![](images/AzureLabs-Lab302b-27.png)

8.  <span data-ttu-id="b6062-248">년대 *빌드 설정* *Unity C\# 프로젝트* 가 더 이상 회색;이 옆의 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-248">Back in *Build Settings* *Unity C\# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="b6062-249">빌드 설정 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-249">Close the Build Settings window.</span></span>

10.  <span data-ttu-id="b6062-250">장면 및 프로젝트 저장 (**파일 > 저장 장면 파일 > 프로젝트 저장**).</span><span class="sxs-lookup"><span data-stu-id="b6062-250">Save your Scene and project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a><span data-ttu-id="b6062-251">4 장-Unity에서 Newtonsoft DLL 가져오기</span><span class="sxs-lookup"><span data-stu-id="b6062-251">Chapter 4 - Importing the Newtonsoft DLL in Unity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b6062-252">건너뛸 하려는 경우는 *Unity 설정* 이 구성 요소, 과정 및 코드로 바로 계속, 다운로드 자유롭게 [302b.unitypackage-MR-Azure](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage),으로 프로젝트로 가져올를 [ **사용자 지정 패키지**](https://docs.unity3d.com/Manual/AssetPackages.html)를 계속 진행 한 다음 [6 장](#chapter-6---create-the-customvisionanalyser-class)합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-252">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-302b.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 6](#chapter-6---create-the-customvisionanalyser-class).</span></span>

<span data-ttu-id="b6062-253">이 과정을 사용 해야 합니다 **Newtonsoft** 라이브러리 자산에는 DLL로 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-253">This course requires the use of the **Newtonsoft** library, which you can add as a DLL to your assets.</span></span> <span data-ttu-id="b6062-254">포함 하는 패키지 [이 링크에서이 라이브러리를 다운로드할 수 있습니다](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage)합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-254">The package containing [this library can be downloaded from this Link](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).</span></span>
<span data-ttu-id="b6062-255">Newtonsoft 라이브러리를 프로젝트로 가져오는이 과정을 통해 제공 된 Unity 패키지를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-255">To import the Newtonsoft library into your project, use the Unity Package which came with this course.</span></span>

1.  <span data-ttu-id="b6062-256">추가 된 *.unitypackage* 사용 하 여 Unity에는 **자산* > *가져오기* *패키지*  >  *사용자 지정* *패키지** 메뉴 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-256">Add the *.unitypackage* to Unity by using the **Assets* > *Import* *Package* > *Custom* *Package** menu option.</span></span>

2.  <span data-ttu-id="b6062-257">에 **Unity 패키지 가져오기** 표시 되는 상자에서 아래에 있는 포함 하 여 모든 것을 확인 **플러그 인** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-257">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![](images/AzureLabs-Lab302b-28.png)

3.  <span data-ttu-id="b6062-258">클릭 합니다 **가져오기** 프로젝트에 항목을 추가 하려면 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-258">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="b6062-259">로 이동 합니다 **Newtonsoft** 아래에 폴더 **플러그 인** 프로젝트 보기를 선택 합니다 *Newtonsoft.Json 플러그 인*.</span><span class="sxs-lookup"><span data-stu-id="b6062-259">Go to the **Newtonsoft** folder under **Plugins** in the project view and select the *Newtonsoft.Json plugin*.</span></span>

    ![](images/AzureLabs-Lab302b-29.png)

5.  <span data-ttu-id="b6062-260">사용 하 여는 *Newtonsoft.Json 플러그 인* 되도록 선택 하면 **Any 플랫폼** 는 **unchecked**, 한지 확인 합니다 **WSAPlayer** 이기도 **unchecked**, 클릭 **적용**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-260">With the *Newtonsoft.Json plugin* selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="b6062-261">이 파일이 올바르게 구성 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-261">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > <span data-ttu-id="b6062-262">이러한 플러그 인을 표시만 Unity 편집기에서 사용 되도록 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-262">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="b6062-263">Unity에서 프로젝트를 내보낸 후 사용 되는 WSA 폴더에서 다른 집합을 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-263">There are a different set of them in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="b6062-264">열어야 할 때 다음에 **WSA** 폴더 내에서 합니다 **Newtonsoft** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-264">Next, you need to open the **WSA** folder, within the **Newtonsoft** folder.</span></span> <span data-ttu-id="b6062-265">방금 구성한 동일한 파일의 복사본을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-265">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="b6062-266">파일을 선택 하 고 [관리자]에서 확인 하는</span><span class="sxs-lookup"><span data-stu-id="b6062-266">Select the file, and then in the inspector, ensure that</span></span>
    -   <span data-ttu-id="b6062-267">**모든 플랫폼** 는 **선택 취소 되어 있음**</span><span class="sxs-lookup"><span data-stu-id="b6062-267">**Any Platform** is **unchecked**</span></span> 
    -   <span data-ttu-id="b6062-268">**만** **WSAPlayer** 는 **확인**</span><span class="sxs-lookup"><span data-stu-id="b6062-268">**only** **WSAPlayer** is **checked**</span></span>
    -   <span data-ttu-id="b6062-269">**처리 하지 않음** 는 **확인**</span><span class="sxs-lookup"><span data-stu-id="b6062-269">**Dont process** is **checked**</span></span>

    ![](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a><span data-ttu-id="b6062-270">5 장-카메라 설정</span><span class="sxs-lookup"><span data-stu-id="b6062-270">Chapter 5 - Camera setup</span></span>

1.  <span data-ttu-id="b6062-271">계층 구조 창에서 선택 합니다 *주 카메라*합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-271">In the Hierarchy Panel, select the *Main Camera*.</span></span>

2.  <span data-ttu-id="b6062-272">선택한 후에의 모든 구성 요소를 볼 수는 합니다 *주 카메라* 에 *검사기 패널*합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-272">Once selected, you will be able to see all the components of the *Main Camera* in the *Inspector Panel*.</span></span>

    1.  <span data-ttu-id="b6062-273">합니다 *카메라* 개체의 이름은 **주 카메라** (맞춤법 참고!)</span><span class="sxs-lookup"><span data-stu-id="b6062-273">The *camera* object must be named **Main Camera** (note the spelling!)</span></span>

    2.  <span data-ttu-id="b6062-274">주 카메라 **태그** 으로 설정 되어 있어야 **MainCamera** (맞춤법 참고!)</span><span class="sxs-lookup"><span data-stu-id="b6062-274">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3.  <span data-ttu-id="b6062-275">있는지 확인 합니다 **변환 위치** 로 설정 된 **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="b6062-275">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4.  <span data-ttu-id="b6062-276">설정할 **플래그 지우기** 하 **단색** (이 대 한 무시 몰입 형 헤드셋).</span><span class="sxs-lookup"><span data-stu-id="b6062-276">Set **Clear Flags** to **Solid Color** (ignore this for immersive headset).</span></span>

    5.  <span data-ttu-id="b6062-277">설정 된 **백그라운드** 카메라의 색 구성 요소를 **검정, 알파 0 (16 진수 코드: #00000000)** (이 대 한 무시 몰입 형 헤드셋).</span><span class="sxs-lookup"><span data-stu-id="b6062-277">Set the **Background** Color of the camera Component to **Black, Alpha 0 (Hex Code: #00000000)** (ignore this for immersive headset).</span></span>

    ![](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a><span data-ttu-id="b6062-278">-6 장 CustomVisionAnalyser 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-278">Chapter 6 - Create the CustomVisionAnalyser class.</span></span>

<span data-ttu-id="b6062-279">이 시점에서 일부 코드를 작성할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-279">At this point you are ready to write some code.</span></span>

<span data-ttu-id="b6062-280">사용 하 여 시작 합니다 *CustomVisionAnalyser* 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-280">You will begin with the *CustomVisionAnalyser* class.</span></span>

> [!NOTE]
> <span data-ttu-id="b6062-281">에 대 한 호출을 **Custom Vision Service** 표시 된 코드에서 다음 사용 하 여 이루어집니다를 **사용자 지정 비전 REST API**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-281">The calls to the **Custom Vision Service** made in the code shown below are made using the **Custom Vision REST API**.</span></span> <span data-ttu-id="b6062-282">이 사용 하 여을 통해 구현 (비슷한을 직접 구현 하는 방법을 이해 하는 데 유용함)이이 API를 사용 하는 방법을 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-282">Through using this, you will see how to implement and make use of this API (useful for understanding how to implement something similar on your own).</span></span> <span data-ttu-id="b6062-283">인식 하며 Microsoft 제공 하는 수를 **Custom Vision Service SDK** 서비스를 호출 하기 위해 사용할 수도 있는 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-283">Be aware, that Microsoft offers a **Custom Vision Service SDK** that can also be used to make calls to the Service.</span></span> <span data-ttu-id="b6062-284">자세한 내용은 참조는 [Custom Vision Service SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) 문서.</span><span class="sxs-lookup"><span data-stu-id="b6062-284">For more information visit the [Custom Vision Service SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) article.</span></span>

<span data-ttu-id="b6062-285">이 클래스는 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-285">This class is responsible for:</span></span>

-   <span data-ttu-id="b6062-286">캡처된 바이트의 배열로 최신 이미지를 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-286">Loading the latest image captured as an array of bytes.</span></span>

-   <span data-ttu-id="b6062-287">Azure는 바이트 배열 보내기 *Custom Vision Service* 분석에 대 한 인스턴스.</span><span class="sxs-lookup"><span data-stu-id="b6062-287">Sending the byte array to your Azure *Custom Vision Service* instance for analysis.</span></span>

-   <span data-ttu-id="b6062-288">JSON 문자열로 응답을 수신 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-288">Receiving the response as a JSON string.</span></span>

-   <span data-ttu-id="b6062-289">응답을 역직렬화 하 고 결과 전달 *예측* 에 *SceneOrganiser* 응답을 표시 하는 방법을 처리 하는 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-289">Deserializing the response and passing the resulting *Prediction* to the *SceneOrganiser* class, which will take care of how the response should be displayed.</span></span>

<span data-ttu-id="b6062-290">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="b6062-290">To create this class:</span></span>

1.  <span data-ttu-id="b6062-291">마우스 오른쪽 단추로 클릭 합니다 *자산 폴더* 에 *프로젝트 패널*, 클릭 **만들기 > 폴더**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-291">Right-click in the *Asset Folder* located in the *Project Panel*, then click **Create > Folder**.</span></span> <span data-ttu-id="b6062-292">폴더를 호출 **스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-292">Call the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab302b-33.png)

2.  <span data-ttu-id="b6062-293">열려는 방금 만든 폴더를 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-293">Double-click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="b6062-294">폴더를 마우스 오른쪽 단추로 클릭 **Create** > **C\# 스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-294">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="b6062-295">스크립트 이름을 *CustomVisionAnalyser*합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-295">Name the script *CustomVisionAnalyser*.</span></span>

4.  <span data-ttu-id="b6062-296">새 두 번 클릭 *CustomVisionAnalyser* 스크립트를 사용 하 여 열고 **Visual Studio**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-296">Double-click on the new *CustomVisionAnalyser* script to open it with **Visual Studio**.</span></span>

5.  <span data-ttu-id="b6062-297">다음과 일치 하도록 파일의 맨 위에 있는 네임 스페이스를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-297">Update the namespaces at the top of your file to match the following:</span></span>

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  <span data-ttu-id="b6062-298">에 *CustomVisionAnalyser* 클래스를 다음 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-298">In the *CustomVisionAnalyser* class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your Prediction Key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > <span data-ttu-id="b6062-299">삽입 해야 하 **예측 키** 에 **predictionKey** 변수 및 **예측 끝점** 에 **predictionEndpoint** 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-299">Make sure you insert your **Prediction Key** into the **predictionKey** variable and your **Prediction Endpoint** into the **predictionEndpoint** variable.</span></span> <span data-ttu-id="b6062-300">에 복사해 둔 *메모장* 과정의 앞부분에 나오는.</span><span class="sxs-lookup"><span data-stu-id="b6062-300">You copied these to *Notepad* earlier in the course.</span></span>

7.  <span data-ttu-id="b6062-301">에 대 한 코드 **Awake()** 이제 인스턴스 변수를 초기화 하려면 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-301">Code for **Awake()** now needs to be added to initialize the Instance variable:</span></span>

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  <span data-ttu-id="b6062-302">메서드 삭제 **start ()** 하 고 **update ()** 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-302">Delete the methods **Start()** and **Update()**.</span></span>

9.  <span data-ttu-id="b6062-303">다음으로 코 루틴을 추가 (정적을 사용 하 여 **GetImageAsByteArray()** 아래 메서드)에서 캡처된 이미지의 분석 결과 얻을 합니다 *ImageCapture* 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-303">Next, add the coroutine (with the static **GetImageAsByteArray()** method below it), which will obtain the results of the analysis of the image captured by the *ImageCapture* class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b6062-304">에 **AnalyseImageCapture** 코 루틴을 호출 하는 *SceneOrganiser* 만들려면 아직 수 있는 클래스.</span><span class="sxs-lookup"><span data-stu-id="b6062-304">In the **AnalyseImageCapture** coroutine, there is a call to the *SceneOrganiser* class that you are yet to create.</span></span> <span data-ttu-id="b6062-305">따라서 **이러한 지금은 줄 주석**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-305">Therefore, **leave those lines commented for now**.</span></span>

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
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

                // The response will be in JSON format, therefore it needs to be deserialized    
    
                // The following lines refers to a class that you will build in later Chapters
                // Wait until then to uncomment these lines

                //AnalysisObject analysisObject = new AnalysisObject();
                //analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
                //SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
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

10.  <span data-ttu-id="b6062-306">변경 내용을 저장 해야 **Visual Studio** 를 반환 하기 전에 **Unity**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-306">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

## <a name="chapter-7---create-the-customvisionobjects-class"></a><span data-ttu-id="b6062-307">7-장 CustomVisionObjects 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="b6062-307">Chapter 7 - Create the CustomVisionObjects class</span></span>

<span data-ttu-id="b6062-308">만든 클래스에서 이제는 합니다 *CustomVisionObjects* 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-308">The class you will create now is the *CustomVisionObjects* class.</span></span>

<span data-ttu-id="b6062-309">이 스크립트는 다른 클래스를 직렬화 및 역직렬화에 대 한 호출에 사용 되는 개체의 수를 포함 합니다 *Custom Vision Service*합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-309">This script contains a number of objects used by other classes to serialize and deserialize the calls made to the *Custom Vision Service*.</span></span>

> [!WARNING]
> <span data-ttu-id="b6062-310">Custom Vision Service,으로 제공 하는 끝점 확인을 수행 하는 것은 다음 JSON 구조 설정한 작업할 [ *사용자 지정 비전 예측 v2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290)합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-310">It is important that you take note of the endpoint that the Custom Vision Service provides you, as the below JSON structure has been set up to work with [*Custom Vision Prediction v2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290).</span></span> <span data-ttu-id="b6062-311">업데이트 해야 다른 버전이 있는 경우는 아래 구조입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-311">If you have a different version, you may need to update the below structure.</span></span>

<span data-ttu-id="b6062-312">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="b6062-312">To create this class:</span></span>

1.  <span data-ttu-id="b6062-313">마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 한 다음 **만들기** > **C\# 스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-313">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="b6062-314">스크립트를 호출할 *CustomVisionObjects*합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-314">Call the script *CustomVisionObjects*.</span></span>

2.  <span data-ttu-id="b6062-315">새 두 번 클릭 **CustomVisionObjects** 스크립트를 사용 하 여 열고 **Visual Studio**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-315">Double-click on the new **CustomVisionObjects** script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="b6062-316">파일의 맨 위에 다음 네임 스페이스를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-316">Add the following namespaces to the top of the file:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="b6062-317">삭제를 **start ()** 및 **update ()** 내부 메서드를 *CustomVisionObjects* 클래스이 클래스는 이제 비워둘 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-317">Delete the **Start()** and **Update()** methods inside the *CustomVisionObjects* class; this class should now be empty.</span></span>

5.  <span data-ttu-id="b6062-318">다음 클래스를 추가 **외부** 는 *CustomVisionObjects* 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-318">Add the following classes **outside** the *CustomVisionObjects* class.</span></span> <span data-ttu-id="b6062-319">사용 되는 이러한 개체는 *Newtonsoft* 응답 데이터 serialize 및 deserialize 하는 라이브러리:</span><span class="sxs-lookup"><span data-stu-id="b6062-319">These objects are used by the *Newtonsoft* library to serialize and deserialize the response data:</span></span>

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
    /// JSON of Images submitted
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
    /// Predictions received by the Service after submitting an image for analysis
    /// </summary> 
    [Serializable]
    public class AnalysisObject
    {
        public List<Prediction> Predictions { get; set; }
    }

    [Serializable]
    public class Prediction
    {
        public string TagName { get; set; }
        public double Probability { get; set; }
    }
    ```

## <a name="chapter-8---create-the-voicerecognizer-class"></a><span data-ttu-id="b6062-320">8-장 VoiceRecognizer 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="b6062-320">Chapter 8 - Create the VoiceRecognizer class</span></span>

<span data-ttu-id="b6062-321">이 클래스는 사용자의 음성 입력을 인식 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-321">This class will recognize the voice input from the user.</span></span>

<span data-ttu-id="b6062-322">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="b6062-322">To create this class:</span></span>

1.  <span data-ttu-id="b6062-323">마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 한 다음 **만들기** > **C\# 스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-323">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="b6062-324">스크립트를 호출할 *VoiceRecognizer*합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-324">Call the script *VoiceRecognizer*.</span></span>

2.  <span data-ttu-id="b6062-325">새 두 번 클릭 **VoiceRecognizer** 스크립트를 사용 하 여 열고 **Visual Studio**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-325">Double-click on the new **VoiceRecognizer** script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="b6062-326">위의 다음 네임 스페이스를 추가 합니다 *VoiceRecognizer* 클래스:</span><span class="sxs-lookup"><span data-stu-id="b6062-326">Add the following namespaces above the *VoiceRecognizer* class:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  <span data-ttu-id="b6062-327">다음 내에서 다음 변수를 추가 합니다 *VoiceRecognizer* 위의 클래스는 *start ()* 메서드:</span><span class="sxs-lookup"><span data-stu-id="b6062-327">Then add the following variables inside the *VoiceRecognizer* class, above the *Start()* method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static VoiceRecognizer Instance;

        /// <summary>
        /// Recognizer class for voice recognition
        /// </summary>
        internal KeywordRecognizer keywordRecognizer;

        /// <summary>
        /// List of Keywords registered
        /// </summary>
        private Dictionary<string, Action> _keywords = new Dictionary<string, Action>();
    ```

5.  <span data-ttu-id="b6062-328">추가 된 **Awake()** 및 **start ()** 메서드는 사용자를 설정 합니다 *키워드* 이미지에 태그를 연결 될 때 인식 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-328">Add the **Awake()** and **Start()** methods, the latter of which will set up the user *keywords* to be recognized when associating a tag to an image:</span></span>

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
        void Start ()
        {

            Array tagsArray = Enum.GetValues(typeof(CustomVisionTrainer.Tags));

            foreach (object tagWord in tagsArray)
            {
                _keywords.Add(tagWord.ToString(), () =>
                {
                    // When a word is recognized, the following line will be called
                    CustomVisionTrainer.Instance.VerifyTag(tagWord.ToString());
                });
            }

            _keywords.Add("Discard", () =>
            {
                // When a word is recognized, the following line will be called
                // The user does not want to submit the image
                // therefore ignore and discard the process
                ImageCapture.Instance.ResetImageCapture();
                keywordRecognizer.Stop();
            });

            //Create the keyword recognizer 
            keywordRecognizer = new KeywordRecognizer(_keywords.Keys.ToArray());

            // Register for the OnPhraseRecognized event 
            keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        }
    ```

6.  <span data-ttu-id="b6062-329">삭제 된 **update ()** 메서드.</span><span class="sxs-lookup"><span data-stu-id="b6062-329">Delete the **Update()** method.</span></span>

7.  <span data-ttu-id="b6062-330">음성 입력이 인식 될 때마다 호출 되는 다음 처리기를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-330">Add the following handler, which is called whenever voice input is recognized:</span></span>

    ```csharp    
        /// <summary>
        /// Handler called when a word is recognized
        /// </summary>
        private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
        {
            Action keywordAction;
            // if the keyword recognized is in our dictionary, call that Action.
            if (_keywords.TryGetValue(args.text, out keywordAction))
            {
                keywordAction.Invoke();
            }
        }
    ```

8.  <span data-ttu-id="b6062-331">변경 내용을 저장 해야 **Visual Studio** 를 반환 하기 전에 **Unity**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-331">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

> [!NOTE]
> <span data-ttu-id="b6062-332">제공 하는 경우는 추가 클래스는 곧 해결 됩니다에서 오류가 나타날 수 있습니다 하는 코드에 대 한 걱정 마십시오.</span><span class="sxs-lookup"><span data-stu-id="b6062-332">Do not worry about code which might appear to have an error, as you will provide further classes soon, which will fix these.</span></span>

## <a name="chapter-9---create-the-customvisiontrainer-class"></a><span data-ttu-id="b6062-333">9-장 CustomVisionTrainer 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="b6062-333">Chapter 9 - Create the CustomVisionTrainer class</span></span>

<span data-ttu-id="b6062-334">이 클래스는 일련의 학습에 웹 호출을 연결 합니다 *Custom Vision Service*합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-334">This class will chain a series of web calls to train the *Custom Vision Service*.</span></span> <span data-ttu-id="b6062-335">각 호출 코드를 바로 위에 자세히 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-335">Each call will be explained in detail right above the code.</span></span>

<span data-ttu-id="b6062-336">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="b6062-336">To create this class:</span></span>

1.  <span data-ttu-id="b6062-337">마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 한 다음 **만들기** > **C\# 스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-337">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="b6062-338">스크립트를 호출할 *CustomVisionTrainer*합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-338">Call the script *CustomVisionTrainer*.</span></span>

2.  <span data-ttu-id="b6062-339">새 두 번 클릭 *CustomVisionTrainer* 스크립트를 사용 하 여 열고 **Visual Studio**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-339">Double-click on the new *CustomVisionTrainer* script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="b6062-340">위의 다음 네임 스페이스를 추가 합니다 *CustomVisionTrainer* 클래스:</span><span class="sxs-lookup"><span data-stu-id="b6062-340">Add the following namespaces above the *CustomVisionTrainer* class:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="b6062-341">다음 내에서 다음 변수를 추가 합니다 *CustomVisionTrainer* 위의 클래스는 **start ()** 메서드.</span><span class="sxs-lookup"><span data-stu-id="b6062-341">Then add the following variables inside the *CustomVisionTrainer* class, above the **Start()** method.</span></span> 

    > [!NOTE]
    > <span data-ttu-id="b6062-342">여기에 학습 URL 내에서 제공 됩니다는 *사용자 지정 비전 교육 1.2* 설명서의 구조 및: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/</span><span class="sxs-lookup"><span data-stu-id="b6062-342">The training URL used here is provided within the *Custom Vision Training 1.2* documentation, and has a structure of: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/</span></span>  
    > <span data-ttu-id="b6062-343">자세한 내용은 참조는 [ *v1.2 참조 사용자 지정 비전 교육 API*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f)합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-343">For more information, visit the [*Custom Vision Training v1.2 reference API*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span></span>

    > [!WARNING]
    > <span data-ttu-id="b6062-344">Custom Vision Service 사용 된 JSON 구조를 학습 모드를 제공 하는 끝점의 참고를 수행 하는 것 (내 합니다 **CustomVisionObjects** 클래스)를 사용 하려면 설정한 [  *사용자 지정 비전 교육 v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f)합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-344">It is important that you take note of the endpoint that the Custom Vision Service provides you for the training mode, as the JSON structure used (within the **CustomVisionObjects** class) has been set up to work with [*Custom Vision Training v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span></span> <span data-ttu-id="b6062-345">업데이트 해야 다른 버전이 있는 경우는 *개체* 구조입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-345">If you have a different version, you may need to update the *Objects* structure.</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CustomVisionTrainer Instance;

        /// <summary>
        /// Custom Vision Service URL root
        /// </summary>
        private string url = "https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/";

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string trainingKey = "- Insert your key here -";

        /// <summary>
        /// Insert your Project Id here
        /// </summary>
        private string projectId = "- Insert your Project Id here -";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// The Tags accepted
        /// </summary>
        internal enum Tags {Mouse, Keyboard}

        /// <summary>
        /// The UI displaying the training Chapters
        /// </summary>
        private TextMesh trainingUI_TextMesh;
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="b6062-346">추가 해야 하 **서비스 키** (학습 키) 값 및 **프로젝트 Id** 값을 적어둔 이전;이 값은 있습니다 [과정 (이전 포털에서 수집 2 장 이상 10 단계)](#chapter-2---training-your-custom-vision-oroject)합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-346">Ensure that you add your **Service Key** (Training Key) value and **Project Id** value, which you noted down previous; these are the values you [collected from the portal earlier in the course (Chapter 2, step 10 onwards)](#chapter-2---training-your-custom-vision-oroject).</span></span>

5.  <span data-ttu-id="b6062-347">다음을 추가 합니다 **start ()** 하 고 **Awake()** 메서드.</span><span class="sxs-lookup"><span data-stu-id="b6062-347">Add the following **Start()** and **Awake()** methods.</span></span> <span data-ttu-id="b6062-348">이러한 메서드 초기화에서 라고 하며 UI 설정에 대 한 호출을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-348">Those methods are called on initialization and contain the call to set up the UI:</span></span>

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
        private void Start()
        { 
            trainingUI_TextMesh = SceneOrganiser.Instance.CreateTrainingUI("TrainingUI", 0.04f, 0, 4, false);
        }
    ```

6.  <span data-ttu-id="b6062-349">삭제 된 **update ()** 메서드.</span><span class="sxs-lookup"><span data-stu-id="b6062-349">Delete the **Update()** method.</span></span> <span data-ttu-id="b6062-350">이 클래스에이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-350">This class will not need it.</span></span>

7.  <span data-ttu-id="b6062-351">추가 된 **RequestTagSelection()** 메서드.</span><span class="sxs-lookup"><span data-stu-id="b6062-351">Add the **RequestTagSelection()** method.</span></span> <span data-ttu-id="b6062-352">이 메서드는 이미지 캡처 되었으며 장치에 저장 될 때 호출 되는 첫 번째 전송할 준비가 되었습니다 및 합니다 *Custom Vision Service*, 학습 하 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-352">This method is the first to be called when an image has been captured and stored in the device and is now ready to be submitted to the *Custom Vision Service*, to train it.</span></span> <span data-ttu-id="b6062-353">이 메서드는 사용자는 캡처된 이미지에 태그 지정 하는 데 사용할 수 있습니다 키워드 집합을 학습 UI에에서 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-353">This method displays, in the training UI, a set of keywords the user can use to tag the image that has been captured.</span></span> <span data-ttu-id="b6062-354">에 알림을 제공 합니다 *VoiceRecognizer* 클래스 음성 입력에 대 한 사용자에 게 수신 대기를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-354">It also alerts the *VoiceRecognizer* class to begin listening to the user for voice input.</span></span>

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  <span data-ttu-id="b6062-355">추가 된 **VerifyTag()** 메서드.</span><span class="sxs-lookup"><span data-stu-id="b6062-355">Add the **VerifyTag()** method.</span></span> <span data-ttu-id="b6062-356">이 메서드는 인식 음성 입력 받을 합니다 **VoiceRecognizer** 클래스를 사용 하 여 유효성을 확인 하 고 다음 학습 프로세스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-356">This method will receive the voice input recognized by the **VoiceRecognizer** class and verify its validity, and then begin the training process.</span></span>

    ```csharp
        /// <summary>
        /// Verify voice input against stored tags.
        /// If positive, it will begin the Service training process.
        /// </summary>
        internal void VerifyTag(string spokenTag)
        {
            if (spokenTag == Tags.Mouse.ToString() || spokenTag == Tags.Keyboard.ToString())
            {
                trainingUI_TextMesh.text = $"Tag chosen: {spokenTag}";
                VoiceRecognizer.Instance.keywordRecognizer.Stop();
                StartCoroutine(SubmitImageForTraining(ImageCapture.Instance.filePath, spokenTag));
            }
        }
    ```

9.  <span data-ttu-id="b6062-357">추가 된 **SubmitImageForTraining()** 메서드.</span><span class="sxs-lookup"><span data-stu-id="b6062-357">Add the **SubmitImageForTraining()** method.</span></span> <span data-ttu-id="b6062-358">이 메서드는 Custom Vision Service 학습 프로세스를 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-358">This method will begin the Custom Vision Service training process.</span></span> <span data-ttu-id="b6062-359">첫 번째 단계를 검색 하는 것은 **태그 Id** 사용자의 유효성이 검사 된 음성 입력와 연결 된 서비스에서.</span><span class="sxs-lookup"><span data-stu-id="b6062-359">The first step is to retrieve the **Tag Id** from the Service which is associated with the validated speech input from the user.</span></span> <span data-ttu-id="b6062-360">합니다 **태그 Id** 은 다음 이미지와 함께 업로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-360">The **Tag Id** will then be uploaded along with the image.</span></span>

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to submit the image.
        /// </summary>
        public IEnumerator SubmitImageForTraining(string imagePath, string tag)
        {
            yield return new WaitForSeconds(2);
            trainingUI_TextMesh.text = $"Submitting Image \nwith tag: {tag} \nto Custom Vision Service";
            string imageId = string.Empty;
            string tagId = string.Empty;

            // Retrieving the Tag Id relative to the voice input
            string getTagIdEndpoint = string.Format("{0}{1}/tags", url, projectId);
            using (UnityWebRequest www = UnityWebRequest.Get(getTagIdEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Tags_RootObject tagRootObject = JsonConvert.DeserializeObject<Tags_RootObject>(jsonResponse);

                foreach (TagOfProject tOP in tagRootObject.Tags)
                {
                    if (tOP.Name == tag)
                    {
                        tagId = tOP.Id;
                    }             
                }
            }

            // Creating the image object to send for training
            List<IMultipartFormSection> multipartList = new List<IMultipartFormSection>();
            MultipartObject multipartObject = new MultipartObject();
            multipartObject.contentType = "application/octet-stream";
            multipartObject.fileName = "";
            multipartObject.sectionData = GetImageAsByteArray(imagePath);
            multipartList.Add(multipartObject);

            string createImageFromDataEndpoint = string.Format("{0}{1}/images?tagIds={2}", url, projectId, tagId);

            using (UnityWebRequest www = UnityWebRequest.Post(createImageFromDataEndpoint, multipartList))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);           

                //unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                www.SetRequestHeader("Training-Key", trainingKey);

                // The upload handler will help uploading the byte array with the request
                www.uploadHandler = new UploadHandlerRaw(imageBytes);

                // The download handler will help receiving the analysis from Azure
                www.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                ImageRootObject m = JsonConvert.DeserializeObject<ImageRootObject>(jsonResponse);
                imageId = m.Images[0].Image.Id;
            }
            trainingUI_TextMesh.text = "Image uploaded";
            StartCoroutine(TrainCustomVisionProject());
        }
    ```

10. <span data-ttu-id="b6062-361">추가 된 **TrainCustomVisionProject()** 메서드.</span><span class="sxs-lookup"><span data-stu-id="b6062-361">Add the **TrainCustomVisionProject()** method.</span></span> <span data-ttu-id="b6062-362">이미지 제출 되었으며 태그가 지정 되 면이 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-362">Once the image has been submitted and tagged, this method will be called.</span></span> <span data-ttu-id="b6062-363">서비스 및 이미지에 제출 된 모든 이전 이미지를 사용 하 여 학습을 수행할 수 있는 새로운 반복을 만들어집니다 방금 업로드 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-363">It will create a new Iteration that will be trained with all the previous images submitted to the Service plus the image just uploaded.</span></span> <span data-ttu-id="b6062-364">이 메서드가 새로 만든 설정할 메서드를 호출 하 고 학습 완료 되 면 **반복** 으로 **기본**분석을 위해 사용 하는 끝점은 최신 학습된 반복 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-364">Once the training has been completed, this method will call a method to set the newly created **Iteration** as **Default**, so that the endpoint you are using for analysis is the latest trained iteration.</span></span>

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to train the Service.
        /// It will generate a new Iteration in the Service
        /// </summary>
        public IEnumerator TrainCustomVisionProject()
        {
            yield return new WaitForSeconds(2);

            trainingUI_TextMesh.text = "Training Custom Vision Service";

            WWWForm webForm = new WWWForm();

            string trainProjectEndpoint = string.Format("{0}{1}/train", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Post(trainProjectEndpoint, webForm))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Training - JSON Response: {jsonResponse}");

                // A new iteration that has just been created and trained
                Iteration iteration = new Iteration();
                iteration = JsonConvert.DeserializeObject<Iteration>(jsonResponse);

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Custom Vision Trained";

                    // Since the Service has a limited number of iterations available,
                    // we need to set the last trained iteration as default
                    // and delete all the iterations you dont need anymore
                    StartCoroutine(SetDefaultIteration(iteration)); 
                }
            }
        }
    ```

11. <span data-ttu-id="b6062-365">추가 된 **SetDefaultIteration()** 메서드.</span><span class="sxs-lookup"><span data-stu-id="b6062-365">Add the **SetDefaultIteration()** method.</span></span> <span data-ttu-id="b6062-366">이 메서드는 이전에 생성 되 고 학습 된 반복으로 설정 됩니다 *기본*입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-366">This method will set the previously created and trained iteration as *Default*.</span></span> <span data-ttu-id="b6062-367">완료 되 면이 메서드는 서비스에서 기존 이전 반복을 삭제 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-367">Once completed, this method will have to delete the previous iteration existing in the Service.</span></span> <span data-ttu-id="b6062-368">이 과정을 작성 하는 동시에 최대 10 번 반복 서비스에서 동시에 존재할 수 제한이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-368">At the time of writing this course, there is a limit of a maximum ten (10) iterations allowed to exist at the same time in the Service.</span></span>

    ```csharp
        /// <summary>
        /// Set the newly created iteration as Default
        /// </summary>
        private IEnumerator SetDefaultIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);
            trainingUI_TextMesh.text = "Setting default iteration";

            // Set the last trained iteration to default
            iteration.IsDefault = true;

            // Convert the iteration object as JSON
            string iterationAsJson = JsonConvert.SerializeObject(iteration);
            byte[] bytes = Encoding.UTF8.GetBytes(iterationAsJson);

            string setDefaultIterationEndpoint = string.Format("{0}{1}/iterations/{2}", 
                                                            url, projectId, iteration.Id);

            using (UnityWebRequest www = UnityWebRequest.Put(setDefaultIterationEndpoint, bytes))
            {
                www.method = "PATCH";
                www.SetRequestHeader("Training-Key", trainingKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Default iteration is set \nDeleting Unused Iteration";
                    StartCoroutine(DeletePreviousIteration(iteration));
                }
            }
        }
    ```

12. <span data-ttu-id="b6062-369">추가 된 **DeletePreviousIteration()** 메서드.</span><span class="sxs-lookup"><span data-stu-id="b6062-369">Add the **DeletePreviousIteration()** method.</span></span> <span data-ttu-id="b6062-370">이 메서드를 찾아 이전 기본이 아닌 반복 삭제:</span><span class="sxs-lookup"><span data-stu-id="b6062-370">This method will find and delete the previous non-default iteration:</span></span>

    ```csharp
        /// <summary>
        /// Delete the previous non-default iteration.
        /// </summary>
        public IEnumerator DeletePreviousIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);

            trainingUI_TextMesh.text = "Deleting Unused \nIteration";

            string iterationToDeleteId = string.Empty;

            string findAllIterationsEndpoint = string.Format("{0}{1}/iterations", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Get(findAllIterationsEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                // The iteration that has just been trained
                List<Iteration> iterationsList = new List<Iteration>();
                iterationsList = JsonConvert.DeserializeObject<List<Iteration>>(jsonResponse);

                foreach (Iteration i in iterationsList)
                {
                    if (i.IsDefault != true)
                    {
                        Debug.Log($"Cleaning - Deleting iteration: {i.Name}, {i.Id}");
                        iterationToDeleteId = i.Id;
                        break;
                    }
                }
            }

            string deleteEndpoint = string.Format("{0}{1}/iterations/{2}", url, projectId, iterationToDeleteId);

            using (UnityWebRequest www2 = UnityWebRequest.Delete(deleteEndpoint))
            {
                www2.SetRequestHeader("Training-Key", trainingKey);
                www2.downloadHandler = new DownloadHandlerBuffer();
                yield return www2.SendWebRequest();
                string jsonResponse = www2.downloadHandler.text;

                trainingUI_TextMesh.text = "Iteration Deleted";
                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "Ready for next \ncapture";

                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "";
                ImageCapture.Instance.ResetImageCapture();
            }
        }
    ```

13. <span data-ttu-id="b6062-371">마지막으로 하는 방법으로이 클래스에 추가 합니다 **GetImageAsByteArray()** 메서드 웹 호출에서 사용 하 여 바이트 배열로 캡처된 이미지를 변환할 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-371">The last method to add in this class is the **GetImageAsByteArray()** method, used on the web calls to convert the image captured into a byte array.</span></span>

    ```csharp
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

14. <span data-ttu-id="b6062-372">변경 내용을 저장 해야 **Visual Studio** 를 반환 하기 전에 **Unity**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-372">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

## <a name="chapter-10---create-the-sceneorganiser-class"></a><span data-ttu-id="b6062-373">10-장 SceneOrganiser 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="b6062-373">Chapter 10 - Create the SceneOrganiser class</span></span>

<span data-ttu-id="b6062-374">이 클래스는:</span><span class="sxs-lookup"><span data-stu-id="b6062-374">This class will:</span></span>

-   <span data-ttu-id="b6062-375">만들기는 **커서** 주 카메라에 연결 하는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-375">Create a **Cursor** object to attach to the Main Camera.</span></span>

-   <span data-ttu-id="b6062-376">만들기는 **레이블** 서비스는 실제 개체를 인식 하는 경우 표시 되는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-376">Create a **Label** object that will appear when the Service recognizes the real-world objects.</span></span>

-   <span data-ttu-id="b6062-377">적절 한 구성 요소를 연결 하 여 주 카메라를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-377">Set up the Main Camera by attaching the appropriate components to it.</span></span>

-   <span data-ttu-id="b6062-378">에 있는 경우 **분석 모드**, 주 카메라의 위치를 기준으로 적절 한 세계 좌표 공간에서 런타임 시 레이블을 생성 및 Custom Vision Service에서 받은 데이터를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-378">When in **Analysis Mode**, spawn the Labels at runtime, in the appropriate world space relative to the position of the Main Camera, and display the data received from the Custom Vision Service.</span></span>

-   <span data-ttu-id="b6062-379">에 있는 경우 **학습 모드**, 학습 프로세스의 여러 단계를 표시 하는 UI를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-379">When in **Training Mode**, spawn the UI that will display the different stages of the training process.</span></span>

<span data-ttu-id="b6062-380">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="b6062-380">To create this class:</span></span>

1.  <span data-ttu-id="b6062-381">마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 한 다음 **만들기** > **C\# 스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-381">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="b6062-382">스크립트 이름을 *SceneOrganiser*합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-382">Name the script *SceneOrganiser*.</span></span>

2.  <span data-ttu-id="b6062-383">새 두 번 클릭 *SceneOrganiser* 스크립트를 사용 하 여 열고 **Visual Studio**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-383">Double-click on the new *SceneOrganiser* script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="b6062-384">하나의 네임 스페이스만 해야 위의 다른를 제거 합니다 *SceneOrganiser* 클래스:</span><span class="sxs-lookup"><span data-stu-id="b6062-384">You will only need one namespace, remove the others from above the *SceneOrganiser* class:</span></span>

    ```csharp
    using UnityEngine;
    ```

4.  <span data-ttu-id="b6062-385">다음 내에서 다음 변수를 추가 합니다 *SceneOrganiser* 위의 클래스는 **start ()** 메서드:</span><span class="sxs-lookup"><span data-stu-id="b6062-385">Then add the following variables inside the *SceneOrganiser* class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        internal GameObject label;

        /// <summary>
        /// Object providing the current status of the camera.
        /// </summary>
        internal TextMesh cameraStatusIndicator;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.5f;
    ```

5.  <span data-ttu-id="b6062-386">삭제 된 **start ()** 하 고 **update ()** 메서드.</span><span class="sxs-lookup"><span data-stu-id="b6062-386">Delete the **Start()** and **Update()** methods.</span></span>

6.  <span data-ttu-id="b6062-387">변수를 바로 아래 추가 합니다 **Awake()** 메서드 클래스를 초기화 하 고 장면 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-387">Right underneath the variables, add the **Awake()** method, which will initialize the class and set up the scene.</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this GameObject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this GameObject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionTrainer class to this GameObject
            gameObject.AddComponent<CustomVisionTrainer>();

            // Add the VoiceRecogniser class to this GameObject
            gameObject.AddComponent<VoiceRecognizer>();

            // Add the CustomVisionObjects class to this GameObject
            gameObject.AddComponent<CustomVisionObjects>();

            // Create the camera Cursor
            cursor = CreateCameraCursor();

            // Load the label prefab as reference
            label = CreateLabel();

            // Create the camera status indicator label, and place it above where predictions
            // and training UI will appear.
            cameraStatusIndicator = CreateTrainingUI("Status Indicator", 0.02f, 0.2f, 3, true);

            // Set camera status indicator to loading.
            SetCameraStatus("Loading");
        }
    ```

7.  <span data-ttu-id="b6062-388">이제 추가 합니다 **CreateCameraCursor()** 만들고 주 카메라 커서를 배치 하는 메서드 및 **CreateLabel()** 메서드를 **Analysis 레이블** 개체 .</span><span class="sxs-lookup"><span data-stu-id="b6062-388">Now add the **CreateCameraCursor()** method that creates and positions the Main Camera cursor, and the **CreateLabel()** method, which creates the **Analysis Label** object.</span></span>

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private GameObject CreateCameraCursor()
        {
            // Create a sphere as new cursor
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Attach it to the camera
            newCursor.transform.parent = gameObject.transform;

            // Resize the new cursor
            newCursor.transform.localScale = new Vector3(0.02f, 0.02f, 0.02f);

            // Move it to the correct position
            newCursor.transform.localPosition = new Vector3(0, 0, 4);

            // Set the cursor color to red
            newCursor.GetComponent<Renderer>().material = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<Renderer>().material.color = Color.green;

            return newCursor;
        }

        /// <summary>
        /// Create the analysis label object
        /// </summary>
        private GameObject CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Resize the new cursor
            newLabel.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);

            // Creating the text of the label
            TextMesh t = newLabel.AddComponent<TextMesh>();
            t.anchor = TextAnchor.MiddleCenter;
            t.alignment = TextAlignment.Center;
            t.fontSize = 50;
            t.text = "";

            return newLabel;
        }
    ```

8. <span data-ttu-id="b6062-389">추가 된 **SetCameraStatus()** 텍스트 메시 카메라의 상태를 제공 하는 메시지를 처리 하는 메서드.</span><span class="sxs-lookup"><span data-stu-id="b6062-389">Add the **SetCameraStatus()** method, which will handle messages intended for the text mesh providing the status of the camera.</span></span>

    ```csharp
        /// <summary>
        /// Set the camera status to a provided string. Will be coloured if it matches a keyword.
        /// </summary>
        /// <param name="statusText">Input string</param>
        public void SetCameraStatus(string statusText)
        {
            if (string.IsNullOrEmpty(statusText) == false)
            {
                string message = "white";

                switch (statusText.ToLower())
                {
                    case "loading":
                        message = "yellow";
                        break;

                    case "ready":
                        message = "green";
                        break;

                    case "uploading image":
                        message = "red";
                        break;

                    case "looping capture":
                        message = "yellow";
                        break;

                    case "analysis":
                        message = "red";
                        break;
                }

                cameraStatusIndicator.GetComponent<TextMesh>().text = $"Camera Status:\n<color={message}>{statusText}..</color>";
            }
        }
    ```

9. <span data-ttu-id="b6062-390">추가 합니다 **PlaceAnalysisLabel()** 하 고 **SetTagsToLastLabel()** 생성 되며 장면에 Custom Vision Service의 데이터를 표시 하는 메서드.</span><span class="sxs-lookup"><span data-stu-id="b6062-390">Add the **PlaceAnalysisLabel()** and **SetTagsToLastLabel()** methods, which will spawn and display the data from the Custom Vision Service into the scene.</span></span>

    ```csharp
        /// <summary>
        /// Instantiate a label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
        }

        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void SetTagsToLastLabel(AnalysisObject analysisObject)
        {
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

            if (analysisObject.Predictions != null)
            {
                foreach (Prediction p in analysisObject.Predictions)
                {
                    if (p.Probability > 0.02)
                    {
                        lastLabelPlacedText.text += $"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}";
                        Debug.Log($"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}");
                    }
                }
            }
        }
    ```

10. <span data-ttu-id="b6062-391">마지막으로 추가 합니다 **CreateTrainingUI()** 메서드를 응용 프로그램 학습 모드 상태인 경우 학습 프로세스의 여러 단계를 표시 하는 UI를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-391">Lastly, add the **CreateTrainingUI()** method, which will spawn the UI displaying the multiple stages of the training process when the application is in Training Mode.</span></span> <span data-ttu-id="b6062-392">이 메서드는 카메라 상태 개체를 만드는 성능을 활용도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-392">This method will also be harnessed to create the camera status object.</span></span>

    ```csharp
        /// <summary>
        /// Create a 3D Text Mesh in scene, with various parameters.
        /// </summary>
        /// <param name="name">name of object</param>
        /// <param name="scale">scale of object (i.e. 0.04f)</param>
        /// <param name="yPos">height above the cursor (i.e. 0.3f</param>
        /// <param name="zPos">distance from the camera</param>
        /// <param name="setActive">whether the text mesh should be visible when it has been created</param>
        /// <returns>Returns a 3D text mesh within the scene</returns>
        internal TextMesh CreateTrainingUI(string name, float scale, float yPos, float zPos, bool setActive)
        {
            GameObject display = new GameObject(name, typeof(TextMesh));
            display.transform.parent = Camera.main.transform;
            display.transform.localPosition = new Vector3(0, yPos, zPos);
            display.SetActive(setActive);
            display.transform.localScale = new Vector3(scale, scale, scale);
            display.transform.rotation = new Quaternion();
            TextMesh textMesh = display.GetComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            return textMesh;
        }
    ```

11. <span data-ttu-id="b6062-393">변경 내용을 저장 해야 **Visual Studio** 를 반환 하기 전에 **Unity**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-393">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b6062-394">계속 하기 전에 엽니다는 **CustomVisionAnalyser** 클래스 및 내 합니다 **AnalyseLastImageCaptured()** 메서드를 *주석 처리를 제거* 다음 줄:</span><span class="sxs-lookup"><span data-stu-id="b6062-394">Before you continue, open the **CustomVisionAnalyser** class, and within the **AnalyseLastImageCaptured()** method, *uncomment* the following lines:</span></span>
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a><span data-ttu-id="b6062-395">11-장 ImageCapture 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="b6062-395">Chapter 11 - Create the ImageCapture class</span></span>

<span data-ttu-id="b6062-396">다음 클래스를 만드는 것은 *ImageCapture* 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-396">The next class you are going to create is the *ImageCapture* class.</span></span>

<span data-ttu-id="b6062-397">이 클래스는 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-397">This class is responsible for:</span></span>

-   <span data-ttu-id="b6062-398">HoloLens 카메라를 사용 하 고 저장 하는 이미지를 캡처하는 *앱* 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-398">Capturing an image using the HoloLens camera and storing it in the *App* Folder.</span></span>

-   <span data-ttu-id="b6062-399">사용자에서 탭 제스처를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-399">Handling Tap gestures from the user.</span></span>

-   <span data-ttu-id="b6062-400">유지 관리 합니다 *Enum* 응용 프로그램에서 실행을 결정 하는 값 *분석* 모드 또는 *학습* 모드.</span><span class="sxs-lookup"><span data-stu-id="b6062-400">Maintaining the *Enum* value that determines if the application will run in *Analysis* mode or *Training* Mode.</span></span>

<span data-ttu-id="b6062-401">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="b6062-401">To create this class:</span></span>

1.  <span data-ttu-id="b6062-402">로 이동 합니다 **스크립트** 이전에 만든 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-402">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="b6062-403">폴더를 마우스 오른쪽 단추로 클릭 **만들기 > C\# 스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-403">Right-click inside the folder, then click **Create > C\# Script**.</span></span> <span data-ttu-id="b6062-404">스크립트 이름을 *ImageCapture*합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-404">Name the script *ImageCapture*.</span></span>

3.  <span data-ttu-id="b6062-405">새 두 번 클릭 **ImageCapture** 스크립트를 사용 하 여 열고 **Visual Studio**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-405">Double-click on the new **ImageCapture** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="b6062-406">파일의 맨 위에 있는 네임 스페이스를 다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-406">Replace the namespaces at the top of the file with the following:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="b6062-407">다음 내에서 다음 변수를 추가 합니다 *ImageCapture* 위의 클래스는 **start ()** 메서드:</span><span class="sxs-lookup"><span data-stu-id="b6062-407">Then add the following variables inside the *ImageCapture* class, above the **Start()** method:</span></span>

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
        /// Loop timer
        /// </summary>
        private float secondsBetweenCaptures = 10f;

        /// <summary>
        /// Application main functionalities switch
        /// </summary>
        internal enum AppModes {Analysis, Training }
        
        /// <summary>
        /// Local variable for current AppMode
        /// </summary>
        internal AppModes AppMode { get; private set; }

        /// <summary>
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  <span data-ttu-id="b6062-408">에 대 한 코드 **Awake()** 하 고 **start ()** 메서드는 이제 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-408">Code for **Awake()** and **Start()** methods now needs to be added:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;

            // Change this flag to switch between Analysis Mode and Training Mode 
            AppMode = AppModes.Training;
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

            // Subscribing to the Hololens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();

            SceneOrganiser.Instance.SetCameraStatus("Ready");
        }
    ```

7.  <span data-ttu-id="b6062-409">탭 제스처 발생할 때 호출 되는 처리기를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-409">Implement a handler that will be called when a Tap gesture occurs.</span></span>

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            switch (AppMode)
            {
                case AppModes.Analysis:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;
                        
                        // Update camera status to looping capture.
                        SceneOrganiser.Instance.SetCameraStatus("Looping Capture");

                        // Begin the capture loop
                        InvokeRepeating("ExecuteImageCaptureAndAnalysis", 0, secondsBetweenCaptures);
                    }
                    else
                    {
                        // The user tapped while the app was analyzing 
                        // therefore stop the analysis process
                        ResetImageCapture();
                    }
                    break;

                case AppModes.Training:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Call the image capture
                        ExecuteImageCaptureAndAnalysis();

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                        // Update camera status to uploading image.
                        SceneOrganiser.Instance.SetCameraStatus("Uploading Image");
                    }              
                    break;
            }     
        }
    ```

    > [!NOTE] 
    > <span data-ttu-id="b6062-410">*분석* 모드는 **TapHandler** 메서드 역할을 시작 하거나 사진 캡처 루프를 중지 하는 스위치입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-410">In *Analysis* mode, the **TapHandler** method acts as a switch to start or stop the photo capture loop.</span></span>
    >
    > <span data-ttu-id="b6062-411">*교육* 모드 카메라에서 이미지를 캡처하지 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-411">In *Training* mode, it will capture an image from the camera.</span></span>
    >
    > <span data-ttu-id="b6062-412">커서 녹색 이면 카메라는 이미지를 사용할 수를 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-412">When the cursor is green, it means the camera is available to take the image.</span></span>
    >
    > <span data-ttu-id="b6062-413">커서 빨간색 이면 카메라 사용량이 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-413">When the cursor is red, it means the camera is busy.</span></span>

8.  <span data-ttu-id="b6062-414">응용 프로그램 이미지 캡처 프로세스를 시작 하 고 이미지를 저장 하는 데 사용 하는 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-414">Add the method that the application uses to start the image capture process and store the image.</span></span>

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Update camera status to analysis.
            SceneOrganiser.Instance.SetCameraStatus("Analysis");

            // Create a label in world space using the SceneOrganiser class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 0.0f,
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

9.  <span data-ttu-id="b6062-415">사진을 캡처한 시간과 분석할 준비가 되었을 때 호출 되는 처리기를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-415">Add the handlers that will be called when the photo has been captured and for when it is ready to be analyzed.</span></span> <span data-ttu-id="b6062-416">결과가 전달 되는 *CustomVisionAnalyser* 또는 *CustomVisionTrainer* 모드에 따라 코드에서 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-416">The result is then passed to the *CustomVisionAnalyser* or the *CustomVisionTrainer* depending on which mode the code is set on.</span></span>

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }


        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            switch (AppMode)
            {
                case AppModes.Analysis:
                    // Call the image analysis
                    StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath));
                    break;

                case AppModes.Training:
                    // Call training using captured image
                    CustomVisionTrainer.Instance.RequestTagSelection();
                    break;
            }
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Update camera status to ready.
            SceneOrganiser.Instance.SetCameraStatus("Ready");

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. <span data-ttu-id="b6062-417">변경 내용을 저장 해야 **Visual Studio** 를 반환 하기 전에 **Unity**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-417">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

11. <span data-ttu-id="b6062-418">모든 스크립트를 완료 했으므로 Unity 편집기에서 돌아가서 누른 채 끌어서 합니다 **SceneOrganiser** 에서 클래스를 **스크립트** 폴더를 **주 카메라** 개체는 *계층 패널*합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-418">Now that all the scripts have been completed, go back in the Unity Editor, then click and drag the **SceneOrganiser** class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

## <a name="chapter-12---before-building"></a><span data-ttu-id="b6062-419">빌드하기 전에 12 장</span><span class="sxs-lookup"><span data-stu-id="b6062-419">Chapter 12 - Before building</span></span>

<span data-ttu-id="b6062-420">응용 프로그램의 철저 한 테스트를 수행 하려면 해야 테스트용으로 로드 하 여 HoloLens에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-420">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>

<span data-ttu-id="b6062-421">를 수행 하기 전에 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-421">Before you do, ensure that:</span></span>

- <span data-ttu-id="b6062-422">에 언급 된 모든 설정을 합니다 [Chapter 2](#chapter-2---training-your-custom-vision-project) 올바르게 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-422">All the settings mentioned in the [Chapter 2](#chapter-2---training-your-custom-vision-project) are set correctly.</span></span>

- <span data-ttu-id="b6062-423">모든 필드를 **주 카메라**, 검사기 패널 올바르게 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-423">All the fields in the **Main Camera**, Inspector Panel, are assigned properly.</span></span>

- <span data-ttu-id="b6062-424">스크립트 **SceneOrganiser** 에 연결할 때 합니다 **주 카메라** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-424">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span>

- <span data-ttu-id="b6062-425">삽입 해야 하 **예측 키** 에 **predictionKey** 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-425">Make sure you insert your **Prediction Key** into the **predictionKey** variable.</span></span>

- <span data-ttu-id="b6062-426">삽입 한 사용자 **예측 끝점** 에 **predictionEndpoint** 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-426">You have inserted your **Prediction Endpoint** into the **predictionEndpoint** variable.</span></span>

- <span data-ttu-id="b6062-427">삽입 한 사용자 **교육 키** 에 **trainingKey** 의 변수를 *CustomVisionTrainer* 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-427">You have inserted your **Training Key** into the **trainingKey** variable, of the *CustomVisionTrainer* class.</span></span>

- <span data-ttu-id="b6062-428">삽입 한 사용자 **프로젝트 ID** 에 **projectId** 의 변수는 *CustomVisionTrainer* 클래스.</span><span class="sxs-lookup"><span data-stu-id="b6062-428">You have inserted your **Project ID** into the **projectId** variable, of the *CustomVisionTrainer* class.</span></span>

## <a name="chapter-13---build-and-sideload-your-application"></a><span data-ttu-id="b6062-429">13 장-빌드 및 테스트용으로 로드 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="b6062-429">Chapter 13 - Build and sideload your application</span></span>

<span data-ttu-id="b6062-430">시작 하는 *빌드* 프로세스:</span><span class="sxs-lookup"><span data-stu-id="b6062-430">To begin the *Build* process:</span></span>

1.  <span data-ttu-id="b6062-431">로 이동 **파일 > 빌드 설정**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-431">Go to **File > Build Settings**.</span></span>

2.  <span data-ttu-id="b6062-432">눈금 **Unity C\# 프로젝트**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-432">Tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="b6062-433">**빌드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-433">Click **Build**.</span></span> <span data-ttu-id="b6062-434">Unity가 시작 됩니다는 **파일 탐색기** 창을 만들고 다음에 앱을 빌드하는 폴더를 선택 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-434">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="b6062-435">해당 폴더를 이제 만들고 이름을 **앱**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-435">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="b6062-436">사용 하 여 다음 합니다 **앱** 폴더를 선택, 클릭 **폴더 선택**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-436">Then with the **App** folder selected, click on **Select Folder**.</span></span>

4.  <span data-ttu-id="b6062-437">Unity 프로젝트를 빌드할 예정 된 **앱** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-437">Unity will begin building your project to the **App** folder.</span></span>

5.  <span data-ttu-id="b6062-438">한 번 Unity (약간의 시간이 걸릴 수 있습니다) 빌드 완료, 열립니다는 **파일 탐색기** 빌드 위치에 있는 창 (작업 표시줄에서 항상 windows에서 위에 나타나지 않을 수 있습니다 있지만 새 추가 대 한 알림을 확인 창)입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-438">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

<span data-ttu-id="b6062-439">HoloLens에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-439">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="b6062-440">(배포에 대 한 원격), 여 HoloLens의 IP 주소를 사용 해야 하 고 중인에 HoloLens 되도록 **개발자 모드**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-440">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="b6062-441">가상 하드 디스크 파일에 대한 중요 정보를 제공하려면</span><span class="sxs-lookup"><span data-stu-id="b6062-441">To do this:</span></span>

    1.  <span data-ttu-id="b6062-442">에 HoloLens, 착용 하는 동안 엽니다는 **설정을**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-442">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="b6062-443">로 이동 **네트워크 및 인터넷** > **Wi-fi** > **고급 옵션**</span><span class="sxs-lookup"><span data-stu-id="b6062-443">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="b6062-444">참고 합니다 **IPv4** 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-444">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="b6062-445">다음으로 다시 이동할 **설정을**, 한 다음 **업데이트 및 보안** > **개발자를 위한**</span><span class="sxs-lookup"><span data-stu-id="b6062-445">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="b6062-446">설정할 **에서 개발자 모드가**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-446">Set **Developer Mode On**.</span></span>

2.  <span data-ttu-id="b6062-447">새 Unity 빌드에 이동 (합니다 **앱** 폴더) 사용 하 여 솔루션 파일을 엽니다 **Visual Studio**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-447">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

3.  <span data-ttu-id="b6062-448">에 *솔루션 구성* 선택 **디버그**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-448">In the *Solution Configuration* select **Debug**.</span></span>

4.  <span data-ttu-id="b6062-449">에 *솔루션 플랫폼*를 선택 **x86, 원격 컴퓨터**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-449">In the *Solution Platform*, select **x86, Remote Machine**.</span></span> <span data-ttu-id="b6062-450">삽입 하 라는 메시지가 표시 됩니다는 **IP 주소** 원격 장치 (여 HoloLens,이 경우 둔).</span><span class="sxs-lookup"><span data-stu-id="b6062-450">You will be prompted to insert the **IP address** of a remote device (the HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab302b-34.png)

5. <span data-ttu-id="b6062-451">로 이동 **빌드할** 메뉴를 클릭 **솔루션 배포** 을 사이드 로드에 HoloLens에 응용 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-451">Go to **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

6. <span data-ttu-id="b6062-452">앱에 HoloLens 시작할 준비가에 설치 된 앱 목록에 나타나야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-452">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="b6062-453">몰입 형 헤드셋을 배포 하려면 설정 합니다 **솔루션 플랫폼** 를 *로컬 컴퓨터*, 설정 및를 **구성** 에 *디버그*, 를사용하여*x86* 으로 **플랫폼**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-453">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="b6062-454">로컬 배포 후 컴퓨터를 사용 하 여는 **빌드** 메뉴 항목을 선택 하 *솔루션 배포*합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-454">Then deploy to the local machine, using the **Build** menu item, selecting *Deploy Solution*.</span></span> 

## <a name="to-use-the-application"></a><span data-ttu-id="b6062-455">응용 프로그램을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-455">To use the application:</span></span>

<span data-ttu-id="b6062-456">앱 기능 사이 전환할 *교육* 모드 및 *예측* 모드를 업데이트 해야 합니다 **AppMode** 이며 변수는 **Awake()** 내에 있는 메서드를 *ImageCapture* 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-456">To switch the app functionality between *Training* mode and *Prediction* mode you need to update the **AppMode** variable, located in the **Awake()** method located within the *ImageCapture* class.</span></span>

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
<span data-ttu-id="b6062-457">로 구분하거나 여러</span><span class="sxs-lookup"><span data-stu-id="b6062-457">or</span></span>
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

<span data-ttu-id="b6062-458">*교육* 모드:</span><span class="sxs-lookup"><span data-stu-id="b6062-458">In *Training* mode:</span></span>

- <span data-ttu-id="b6062-459">살펴봅니다 **마우스** 또는 **키보드** 사용 하는 **탭 하기 제스처**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-459">Look at **Mouse** or **Keyboard** and use the **Tap gesture**.</span></span>

- <span data-ttu-id="b6062-460">다음으로, 텍스트 태그를 제공 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-460">Next, text will appear asking you to provide a tag.</span></span>

- <span data-ttu-id="b6062-461">예를 들어 하나 **마우스** 하거나 **키보드**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-461">Say either **Mouse** or **Keyboard**.</span></span>


<span data-ttu-id="b6062-462">*예측* 모드:</span><span class="sxs-lookup"><span data-stu-id="b6062-462">In *Prediction* mode:</span></span>

- <span data-ttu-id="b6062-463">개체를 살펴보고 사용 합니다 **탭 하기 제스처**합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-463">Look at an object and use the **Tap gesture**.</span></span>

- <span data-ttu-id="b6062-464">확률이 가장 높은 (이 정규화 된)를 사용 하 여 검색 된 개체를 제공 하 텍스트가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-464">Text will appear providing the object detected, with the highest probability (this is normalized).</span></span>

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a><span data-ttu-id="b6062-465">14-장 평가 하 고 사용자 지정 비전 모델을 향상 시키기</span><span class="sxs-lookup"><span data-stu-id="b6062-465">Chapter 14 - Evaluate and improve your Custom Vision model</span></span>

<span data-ttu-id="b6062-466">서비스를 보다 정확 하 게 확인을 계속 하려면 예측에 사용 된 모델을 학습 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-466">To make your Service more accurate, you will need to continue to train the model used for prediction.</span></span> <span data-ttu-id="b6062-467">둘 다를 사용 하 여 새 응용 프로그램을 사용 하 여 이렇게 합니다 *교육* 하 고 *예측* 모드를 사용 하 여이 장에서 다루는 내용는 포털을 방문 하 여 두 번째 요구 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-467">This is accomplished through using your new application, with both the *training* and *prediction* modes, with the latter requiring you to visit the portal, which is what is covered in this Chapter.</span></span> <span data-ttu-id="b6062-468">포털에 여러 번 다시 방문, 모델을 지속적으로 향상 시킬 준비 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-468">Be prepared to revisit your portal many times, to continually improve your model.</span></span>

1. <span data-ttu-id="b6062-469">마찬가지로 Azure 사용자 지정 비전 포털로 이동 하 고 프로젝트가 있는 경우 선택 합니다 *예측* 탭 (에서 페이지의 위쪽 가운데):</span><span class="sxs-lookup"><span data-stu-id="b6062-469">Head to your Azure Custom Vision Portal again, and once you are in your project, select the *Predictions* tab (from the top center of the page):</span></span>

    ![](images/AzureLabs-Lab302b-35.png)

2. <span data-ttu-id="b6062-470">응용 프로그램을 실행 하는 동안 서비스에 전송 된 모든 이미지 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-470">You will see all the images which were sent to your Service whilst your application was running.</span></span> <span data-ttu-id="b6062-471">이미지를 가리키면 해당 이미지에 대해 수행 된 예측을 사용 하 여 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-471">If you hover over the images, they will provide you with the predictions that were made for that image:</span></span>

    ![](images/AzureLabs-Lab302b-36.png)

3. <span data-ttu-id="b6062-472">열려는 이미지 중 하나를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-472">Select one of your images to open it.</span></span> <span data-ttu-id="b6062-473">열기 되 면 오른쪽에 해당 이미지에 대 한 예측이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-473">Once open, you will see the predictions made for that image to the right.</span></span> <span data-ttu-id="b6062-474">수 예측 잘못 되었으며 서비스의 학습 모델에이 이미지를 추가, 클릭 하려는 경우는 *태그 내* 상자 입력과 연결할 태그를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-474">If you the predictions were correct, and you wish to add this image to your Service's training model, click the *My Tags* input box, and select the tag you wish to associate.</span></span> <span data-ttu-id="b6062-475">완료 되 면 클릭 합니다 *저장 후 닫기* 맨 오른쪽 단추를 다음 이미지는 진행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-475">When you are finished, click the *Save and close* button to the bottom right, and continue on to the next image.</span></span>

    ![](images/AzureLabs-Lab302b-37.png)

4. <span data-ttu-id="b6062-476">이미지의 그리드로 다시 했으면 하는 태그를 추가 (저장), 이미지를 확인할 수 있습니다 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-476">Once you are back to the grid of images, you will notice the images which you have added tags to (and saved), will be removed.</span></span> <span data-ttu-id="b6062-477">태그가 지정 된 항목 내에 있지 않은 것이 생각 하는 모든 이미지를 찾을 경우 삭제할 수 있습니다 합니다 (이렇게 하려면 여러 이미지에 대 한) 해당 이미지에 눈금을 클릭 하 고 클릭 한 다음 *삭제* 그리드 페이지의 오른쪽 위 모서리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-477">If you find any images which you think do not have your tagged item within them, you can delete them, by clicking the tick on that image (can do this for several images) and then clicking *Delete* in the upper right corner of the grid page.</span></span> <span data-ttu-id="b6062-478">뒤에 오는 팝업에서 클릭할 수 중 하나 *예, 삭제* 또는 *No*하 여 삭제를 확인 하거나 각각을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-478">On the popup that follows, you can click either *Yes, delete* or *No*, to confirm the deletion or cancel it, respectively.</span></span> 

    ![](images/AzureLabs-Lab302b-38.png)

5. <span data-ttu-id="b6062-479">계속 하려면 준비가 되었을 때 클릭 녹색 *학습* 오른쪽 위에 있는 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-479">When you are ready to proceed, click the green *Train* button in the top right.</span></span> <span data-ttu-id="b6062-480">모든 이미지는 이제 제공한 (수 있는 보다 정확 하 게)를 사용 하 여 서비스 모델 학습 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-480">Your Service model will be trained with all the images which you have now provided (which will make it more accurate).</span></span> <span data-ttu-id="b6062-481">학습 완료 되 면 클릭 해야 합니다 *기본값으로* 단추 한 번 더 있도록에 *예측 URL* 계속 가장 최신의 반복입니다. 서비스를 사용 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-481">Once the training is complete, make sure to click the *Make default* button once more, so that your *Prediction URL* continues to use the most up-to-date iteration of your Service.</span></span>

    <span data-ttu-id="b6062-482">![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)</span><span class="sxs-lookup"><span data-stu-id="b6062-482">![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)</span></span>

## <a name="your-finished-custom-vision-api-application"></a><span data-ttu-id="b6062-483">완성 된 Custom Vision API 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="b6062-483">Your finished Custom Vision API application</span></span>

<span data-ttu-id="b6062-484">축, 실제 개체를 인식 하 고, 서비스 모델을 학습, 표시 된 것의 신뢰도 표시 하려면 Azure Custom Vision API를 활용 하는 혼합된 현실 앱을 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-484">Congratulations, you built a mixed reality app that leverages the Azure Custom Vision API to recognize real world objects, train the Service model, and display confidence of what has been seen.</span></span>

![](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="b6062-485">보너스 연습</span><span class="sxs-lookup"><span data-stu-id="b6062-485">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="b6062-486">연습 1</span><span class="sxs-lookup"><span data-stu-id="b6062-486">Exercise 1</span></span>

<span data-ttu-id="b6062-487">학습 하 **Custom Vision Service** 자세한 개체를 인식 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-487">Train your **Custom Vision Service** to recognize more objects.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="b6062-488">연습 2</span><span class="sxs-lookup"><span data-stu-id="b6062-488">Exercise 2</span></span>

<span data-ttu-id="b6062-489">학습 한 내용으로 확장 하는 방법,으로 다음 연습을 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-489">As a way to expand on what you have learned, complete the following exercises:</span></span>

<span data-ttu-id="b6062-490">개체 인식 되 면 소리를 재생 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6062-490">Play a sound when an object is recognized.</span></span>

### <a name="exercise-3"></a><span data-ttu-id="b6062-491">연습 3</span><span class="sxs-lookup"><span data-stu-id="b6062-491">Exercise 3</span></span>

<span data-ttu-id="b6062-492">앱을 분석 하는 동일한 이미지를 사용 하 여 서비스를 다시 학습에 따라서 서비스를 보다 정확 하 게 확인 API를 사용 하 여 (예측 및 교육을 동시에 수행 됨).</span><span class="sxs-lookup"><span data-stu-id="b6062-492">Use the API to re-train your Service with the same images your app is analyzing, so to make the Service more accurate (do both prediction and training simultaneously).</span></span>
