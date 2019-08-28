---
title: MR 및 Azure 304-얼굴 인식
description: 이 과정을 완료하면 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 이해할 수 있습니다.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, 아카데미, unity, 자습서, api, 얼굴 인식, hololens, 몰입 형, vr
ms.openlocfilehash: 7cd2a6683c80279129934c619a9b9cb857badf67
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047179"
---
>[!NOTE]
><span data-ttu-id="596e0-104">혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="596e0-105">따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="596e0-106">이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="596e0-107">지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="596e0-108">향후에는 HoloLens 2를 개발 하는 방법을 보여 주는 새 자습서 시리즈를 게시할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="596e0-109">이 알림은 게시 될 때 해당 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-304-face-recognition"></a><span data-ttu-id="596e0-110">MR 및 Azure 304: 얼굴 인식</span><span class="sxs-lookup"><span data-stu-id="596e0-110">MR and Azure 304: Face recognition</span></span>

![이 과정을 완료 한 결과](images/AzureLabs-Lab4-00.png)

<span data-ttu-id="596e0-112">이 과정에서는 Microsoft Face API와 함께 Azure Cognitive Services를 사용 하 여 혼합 현실 응용 프로그램에 얼굴 인식 기능을 추가 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-112">In this course you will learn how to add face recognition capabilities to a mixed reality application, using Azure Cognitive Services, with the Microsoft Face API.</span></span>

<span data-ttu-id="596e0-113">*Azure Face API* 는 개발자에 게 클라우드에서 가장 높은 고급 얼굴 알고리즘을 제공 하는 Microsoft 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-113">*Azure Face API* is a Microsoft service, which provides developers with the most advanced face algorithms, all in the cloud.</span></span> <span data-ttu-id="596e0-114">*Face API* 에는 특성을 사용한 얼굴 감지 및 얼굴 인식 이라는 두 가지 주요 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-114">The *Face API* has two main functions: face detection with attributes, and face recognition.</span></span> <span data-ttu-id="596e0-115">이를 통해 개발자는 단지 얼굴에 대 한 그룹 집합을 설정 하 고 나중에 쿼리 이미지를 서비스로 보내 얼굴을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-115">This allows developers to simply set a set of groups for faces, and then, send query images to the service later, to determine to whom a face belongs.</span></span> <span data-ttu-id="596e0-116">자세한 내용은 [Azure 얼굴 인식 페이지](https://azure.microsoft.com/services/cognitive-services/face/)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="596e0-116">For more information, visit the [Azure Face Recognition page](https://azure.microsoft.com/services/cognitive-services/face/).</span></span>

<span data-ttu-id="596e0-117">이 과정을 완료 하면 다음과 같은 작업을 수행할 수 있는 혼합 현실 HoloLens 응용 프로그램이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-117">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1. <span data-ttu-id="596e0-118">**탭 제스처** 를 사용 하 여 온보드 HoloLens 카메라를 사용 하 여 이미지 캡처를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-118">Use a **Tap Gesture** to initiate the capture of an image using the on-board HoloLens camera.</span></span> 
2. <span data-ttu-id="596e0-119">캡처된 이미지를 *Azure Face API* 서비스로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-119">Send the captured image to the *Azure Face API* service.</span></span>
3. <span data-ttu-id="596e0-120">*Face API* 알고리즘의 결과를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-120">Receive the results of the *Face API* algorithm.</span></span>
4. <span data-ttu-id="596e0-121">단순한 사용자 인터페이스를 사용 하 여 일치 하는 사용자의 이름을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-121">Use a simple User Interface, to display the name of matched people.</span></span>

<span data-ttu-id="596e0-122">이렇게 하면 Face API 서비스에서 Unity 기반 혼합 현실 응용 프로그램으로 결과를 가져오는 방법을 배울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-122">This will teach you how to get the results from the Face API Service into your Unity-based mixed reality application.</span></span>

<span data-ttu-id="596e0-123">응용 프로그램에서 결과를 디자인과 통합 하는 방법을 사용자가 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-123">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="596e0-124">이 과정은 Azure 서비스를 Unity 프로젝트와 통합 하는 방법을 배울 수 있도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-124">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="596e0-125">이 과정에서 얻은 지식을 사용 하 여 혼합 현실 응용 프로그램을 개선 하는 것은 사용자의 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-125">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="596e0-126">장치 지원</span><span class="sxs-lookup"><span data-stu-id="596e0-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="596e0-127">과정</span><span class="sxs-lookup"><span data-stu-id="596e0-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="596e0-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="596e0-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="596e0-129"><a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="596e0-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="596e0-130">MR 및 Azure 304: 얼굴 인식</span><span class="sxs-lookup"><span data-stu-id="596e0-130">MR and Azure 304: Face recognition</span></span></td><td style="text-align: center;"> <span data-ttu-id="596e0-131">✔️</span><span class="sxs-lookup"><span data-stu-id="596e0-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="596e0-132">✔️</span><span class="sxs-lookup"><span data-stu-id="596e0-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="596e0-133">이 과정에서 주로 HoloLens에 초점을 맞춘 반면,이 과정에서 배운 내용을 Windows Mixed Reality 모던 (VR) 헤드셋에도 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="596e0-134">모던 (VR) 헤드셋은 액세스할 수 있는 카메라를 포함 하지 않으므로 PC에 연결 된 외부 카메라가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="596e0-135">이 과정을 진행 하면서 모던 (VR) 헤드셋을 지원 하기 위해 사용 해야 하는 변경 내용에 대 한 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="596e0-136">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="596e0-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="596e0-137">이 자습서는 Unity 및 C#에 대 한 기본 경험이 있는 개발자를 위해 작성 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="596e0-138">또한이 문서에서 사전 요구 사항 및 작성 된 지침은 작성 시 테스트 되 고 확인 된 내용 (2018 일 수 있음)을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="596e0-139">[도구 설치](install-the-tools.md) 문서에 나와 있는 것 처럼 최신 소프트웨어를 무료로 사용할 수 있지만,이 과정의 정보가 아래 나열 된 것 보다 최신 소프트웨어에서 찾을 수 있는 것으로 간주 하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="596e0-140">이 과정에는 다음 하드웨어 및 소프트웨어를 권장 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="596e0-141">모던 (VR) 헤드셋 개발을 위한 [Windows Mixed Reality와 호환 되](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 는 개발 PC</span><span class="sxs-lookup"><span data-stu-id="596e0-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="596e0-142">개발자 모드를 사용 하는 Windows 10이 하 버전의 작성자 업데이트 (또는 이상)</span><span class="sxs-lookup"><span data-stu-id="596e0-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md)
- [<span data-ttu-id="596e0-143">최신 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="596e0-143">The latest Windows 10 SDK</span></span>](install-the-tools.md)
- [<span data-ttu-id="596e0-144">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="596e0-144">Unity 2017.4</span></span>](install-the-tools.md)
- [<span data-ttu-id="596e0-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="596e0-145">Visual Studio 2017</span></span>](install-the-tools.md)
- <span data-ttu-id="596e0-146">개발자 모드가 사용 하도록 설정 된 [Windows Mixed Reality 모던 (VR) 헤드셋](immersive-headset-hardware-details.md) 또는 [Microsoft HoloLens](hololens-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="596e0-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="596e0-147">PC에 연결 된 카메라 (몰입 형 헤드셋 개발용)</span><span class="sxs-lookup"><span data-stu-id="596e0-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="596e0-148">Azure 설정 및 Face API 검색을 위한 인터넷 액세스</span><span class="sxs-lookup"><span data-stu-id="596e0-148">Internet access for Azure setup and Face API retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="596e0-149">시작하기 전 주의 사항</span><span class="sxs-lookup"><span data-stu-id="596e0-149">Before you start</span></span>

1.  <span data-ttu-id="596e0-150">이 프로젝트를 빌드하는 데 문제가 발생 하지 않도록 하려면 루트 또는 루트 폴더에이 자습서에서 언급 한 프로젝트를 만드는 것이 좋습니다. (긴 폴더 경로는 빌드 시에 문제를 일으킬 수 있습니다.)</span><span class="sxs-lookup"><span data-stu-id="596e0-150">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="596e0-151">HoloLens를 설정 하 고 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-151">Set up and test your HoloLens.</span></span> <span data-ttu-id="596e0-152">HoloLens를 설정 하는 데 지원이 필요한 경우 [hololens 설정 문서를 방문](https://docs.microsoft.com/hololens/hololens-setup)해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-152">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="596e0-153">새 HoloLens 앱 개발을 시작할 때 보정 및 센서 조정을 수행 하는 것이 좋습니다 (경우에 따라 각 사용자에 대해 해당 작업을 수행 하는 데 도움이 될 수 있음).</span><span class="sxs-lookup"><span data-stu-id="596e0-153">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="596e0-154">보정에 대 한 도움말을 보려면 [HoloLens 보정 문서에](calibration.md#hololens-2)대 한 다음 링크를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="596e0-154">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens-2).</span></span>

<span data-ttu-id="596e0-155">센서 조정에 대 한 도움말을 보려면 [HoloLens 센서 조정 문서에 대 한 링크를](sensor-tuning.md)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="596e0-155">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="596e0-156">1 장-Azure Portal</span><span class="sxs-lookup"><span data-stu-id="596e0-156">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="596e0-157">Azure에서 *Face API* 서비스를 사용 하려면 응용 프로그램에서 사용할 수 있도록 서비스 인스턴스를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-157">To use the *Face API* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="596e0-158">먼저 [Azure Portal](https://portal.azure.com)에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-158">First, log in to the [Azure Portal](https://portal.azure.com).</span></span> 

    > [!NOTE]
    > <span data-ttu-id="596e0-159">아직 Azure 계정이 없는 경우 새로 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-159">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="596e0-160">교실 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 proctors 중 하나에 문의 하 여 새 계정을 설정 하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-160">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="596e0-161">로그인 되 면 왼쪽 위 모서리에서 **새로 만들기** 를 클릭 하 고 *Face API*를 검색 한 후 **enter**키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-161">Once you are logged in, click on **New** in the top left corner, and search for *Face API*, press **Enter**.</span></span>

    ![face api 검색](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > <span data-ttu-id="596e0-163">새 단어는 **새** 포털에서 **리소스 만들기**로 대체 되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-163">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="596e0-164">새 페이지에 *Face API* 서비스에 대 한 설명이 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-164">The new page will provide a description of the *Face API* service.</span></span> <span data-ttu-id="596e0-165">이 프롬프트의 왼쪽 아래에서 **만들기** 단추를 선택 하 여이 서비스와의 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-165">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![face api 정보](images/AzureLabs-Lab4-02.png)

4.  <span data-ttu-id="596e0-167">**만들기**를 클릭 하면 다음을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-167">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="596e0-168">이 서비스 인스턴스의 원하는 이름을 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-168">Insert your desired name for this service instance.</span></span>

    2. <span data-ttu-id="596e0-169">구독을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-169">Select a subscription.</span></span>

    3. <span data-ttu-id="596e0-170">적절 한 가격 책정 계층을 선택 합니다. *Face API 서비스*를 처음 만드는 경우 무료 계층 (명명 된 F0)을 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-170">Select the pricing tier appropriate for you, if this is the first time creating a *Face API Service*, a free tier (named F0) should be available to you.</span></span>

    4. <span data-ttu-id="596e0-171">리소스 그룹을 선택 하거나 새 **리소스 그룹** 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-171">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="596e0-172">리소스 그룹은 Azure 자산의 컬렉션에 대 한 청구를 모니터링 하 고, 액세스를 제어 하 고, 프로 비전 하 고, 관리 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-172">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="596e0-173">단일 프로젝트와 연결 된 모든 Azure 서비스 (예: 이러한 랩)를 공용 리소스 그룹에 유지 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-173">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="596e0-174">Azure 리소스 그룹에 대 한 자세한 내용을 보려면 [리소스 그룹 문서를 참조](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)하세요.</span><span class="sxs-lookup"><span data-stu-id="596e0-174">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="596e0-175">나중에 사용 하는 UWP 앱 인 **Person 작성자**는 위치에 ' 미국 서 부 '를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-175">The UWP app, **Person Maker**, which you use later, requires the use of 'West US' for location.</span></span>

    6. <span data-ttu-id="596e0-176">또한이 서비스에 적용 된 사용 약관을 이해 했는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-176">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7. <span data-ttu-id="596e0-177">선택 **만들기\*합니다.**</span><span class="sxs-lookup"><span data-stu-id="596e0-177">Select **Create\*.**</span></span>

        ![face api 서비스 만들기](images/AzureLabs-Lab4-03.png)

5.  <span data-ttu-id="596e0-179">클릭 한 후 **만들기**\* 만들려는 서비스에 대 한 대기 해야, 1 분이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-179">Once you have clicked on **Create\*,** you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="596e0-180">서비스 인스턴스를 만든 후 알림이 포털에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-180">A notification will appear in the portal once the Service instance is created.</span></span>

    ![서비스 만들기 알림](images/AzureLabs-Lab4-04.png)

7.  <span data-ttu-id="596e0-182">알림을 클릭 하 여 새 서비스 인스턴스를 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-182">Click on the notifications to explore your new Service instance.</span></span>

    ![리소스 알림으로 이동](images/AzureLabs-Lab4-05.png)

8.  <span data-ttu-id="596e0-184">준비가 되 면 알림에서 리소스로 **이동** 단추를 클릭 하 여 새 서비스 인스턴스를 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-184">When you are ready, click **Go to resource** button in the notification to explore your new Service instance.</span></span>

    ![액세스 얼굴 api 키](images/AzureLabs-Lab4-06.png)

9.  <span data-ttu-id="596e0-186">이 자습서에서 응용 프로그램은 서비스에 대 한 호출을 수행 해야 합니다 .이 작업은 서비스의 ' 키 ' 구독을 사용 하 여 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-186">Within this tutorial, your application will need to make calls to your service, which is done through using your service's subscription 'key'.</span></span> <span data-ttu-id="596e0-187">*Face API* 서비스의 *빠른 시작* 페이지에서 첫 번째 지점은 번호 1 이며 *키를 가져옵니다.*</span><span class="sxs-lookup"><span data-stu-id="596e0-187">From the *Quick start* page, of your *Face API* service, the first point is number 1, to *Grab your keys.*</span></span>

10. <span data-ttu-id="596e0-188">*서비스* 페이지에서 파란색 **키** 하이퍼링크 (빠른 시작 페이지의 경우) 또는 서비스 탐색 메뉴 (왼쪽에서 ' 키 ' 아이콘으로 표시 됨)의 **키** 링크를 선택 하 여 키를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-188">On the *Service* page select either the blue **Keys** hyperlink (if on the Quick start page), or the **Keys** link in the services navigation menu (to the left, denoted by the 'key' icon), to reveal your keys.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="596e0-189">나중에 필요 하므로 키 중 하나를 기록 하 고 보호 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-189">Take note of either one of the keys and safeguard it, as you will need it later.</span></span>

## <a name="chapter-2---using-the-person-maker-uwp-application"></a><span data-ttu-id="596e0-190">2 장-' Person Maker ' UWP 응용 프로그램 사용</span><span class="sxs-lookup"><span data-stu-id="596e0-190">Chapter 2 - Using the 'Person Maker' UWP application</span></span>

<span data-ttu-id="596e0-191">[Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip)라는 미리 작성 된 UWP 응용 프로그램을 다운로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-191">Make sure to download the prebuilt UWP Application called [Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip).</span></span> <span data-ttu-id="596e0-192">이 앱은이 과정의 최종 제품이 아니므로 이후 프로젝트에서 사용 하는 Azure 항목을 만드는 데 도움이 되는 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-192">This app is not the end product for this course, just a tool to help you create your Azure entries, which the later project will rely upon.</span></span>

<span data-ttu-id="596e0-193">**Person Maker** 를 사용 하면 사용자와 연결 된 Azure 항목 및 사용자 그룹을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-193">**Person Maker** allows you to create Azure entries, which are associated with people, and groups of people.</span></span> <span data-ttu-id="596e0-194">응용 프로그램은 추가 된 사용자의 얼굴을 인식 하기 위해 나중에 FaceAPI에서 사용할 수 있는 형식으로 필요한 모든 정보를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-194">The application will place all the needed information in a format which can then later be used by the FaceAPI, in order to recognize the faces of people whom you have added.</span></span> 

> <span data-ttu-id="596e0-195">중요 한 **사용자 작성자** 는 몇 가지 기본 제한을 사용 하 여 **무료 구독 계층**에 대 한 분당 서비스 호출 수를 초과 하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-195">[IMPORTANT] **Person Maker** uses some basic throttling, to help ensure that you do not exceed the number of service calls per minute for the **free subscription tier**.</span></span> <span data-ttu-id="596e0-196">제한이 발생 하면 위쪽의 녹색 텍스트가 빨강으로 변경 되 고 ' 활성 '으로 업데이트 됩니다. 이 경우 응용 프로그램을 대기 합니다. 다음에는 계속 해 서 face 서비스에 액세스할 수 있을 때까지 기다린 후 다시 사용할 수 있는 경우 ' 활성 '으로 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-196">The green text at the top will change to red and update as 'ACTIVE' when throttling is happening; if this is the case, simply wait for the application (it will wait until it can next continue accessing the face service, updating as 'IN-ACTIVE' when you can use it again).</span></span>

<span data-ttu-id="596e0-197">이 응용 프로그램은 Face API를 모두 사용할 수 있도록 하는 *ProjectOxford* 라이브러리를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-197">This application uses the *Microsoft.ProjectOxford.Face* libraries, which will allow you to make full use of the Face API.</span></span> <span data-ttu-id="596e0-198">이 라이브러리는 NuGet 패키지로 무료로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-198">This library is available for free as a NuGet Package.</span></span> <span data-ttu-id="596e0-199">이와 유사한 Api에 대 한 자세한 내용은 [api 참조 문서를 참조](https://docs.microsoft.com/azure/cognitive-services/face/apireference)하세요.</span><span class="sxs-lookup"><span data-stu-id="596e0-199">For more information about this, and similar, APIs [make sure to visit the API reference article](https://docs.microsoft.com/azure/cognitive-services/face/apireference).</span></span>

> [!NOTE] 
> <span data-ttu-id="596e0-200">이러한 작업을 수행 하는 방법에 대 한 지침은 필요한 단계에 불과합니다. 이러한 작업을 수행 하는 방법은 문서에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-200">These are just the steps required, instructions for how to do these things is further down the document.</span></span> <span data-ttu-id="596e0-201">**Person 작성자** 앱은 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-201">The **Person Maker** app will allow you to:</span></span>
>
> - <span data-ttu-id="596e0-202">연결 하려는 여러 사용자로 구성 된 그룹인 *개인 그룹*을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-202">Create a *Person Group*, which is a group composed of several people which you want to associate with it.</span></span> <span data-ttu-id="596e0-203">Azure 계정을 사용 하 여 여러 사용자 그룹을 호스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-203">With your Azure account you can host multiple Person Groups.</span></span>
>
> - <span data-ttu-id="596e0-204">Person 그룹의 멤버인 *개인*을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-204">Create a *Person*, which is a member of a Person Group.</span></span> <span data-ttu-id="596e0-205">각 사용자에 게는 연결 된 여러 *얼굴* 이미지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-205">Each person has a number of *Face* images associated with it.</span></span>
>
> -  <span data-ttu-id="596e0-206">*사용자*에 게 *얼굴 이미지* 를 할당 하 여 Azure Face API 서비스가 해당 *얼굴*을 통해 *사람* 을 인식할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-206">Assign *face images* to a *Person*, to allow your Azure Face API Service to recognize a *Person* by the corresponding *face*.</span></span>
>
> -  <span data-ttu-id="596e0-207">*Azure Face API 서비스*를 *학습* 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-207">*Train* your *Azure Face API Service*.</span></span>

<span data-ttu-id="596e0-208">사용자를 인식할 수 있도록이 앱을 학습 하려면 사용자 그룹에 추가 하려는 각 사용자에 대 한 10 개 이상의 사진이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-208">Be aware, so to train this app to recognize people, you will need ten (10) close-up photos of each person which you would like to add to your Person Group.</span></span> <span data-ttu-id="596e0-209">Windows 10 Cam 앱을 사용 하면 이러한 정보를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-209">The Windows 10 Cam App can help you to take these.</span></span> <span data-ttu-id="596e0-210">각 사진이 명확 하 게 표시 되지 않도록 (이 경우에는 제목에서 흐리게, 흐리게 또는 너무 멀리가 안 됨), 이미지 파일 크기는 **4mb**이 고 **1kb**미만이 아닌 jpg 또는 png 파일 형식의 사진을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-210">You must ensure that each photo is clear (avoid blurring, obscuring, or being too far, from the subject), have the photo in jpg or png file format, with the image file size being no larger **4 MB**, and no less than **1 KB**.</span></span>

> [!NOTE]
> <span data-ttu-id="596e0-211">이 자습서를 수행 하는 경우 HoloLens를 사용 하는 경우와 마찬가지로 교육을 위해 자신의 얼굴을 사용 하지 마세요. 사용자가 직접 볼 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-211">If you are following this tutorial, do not use your own face for training, as when you put the HoloLens on, you cannot look at yourself.</span></span> <span data-ttu-id="596e0-212">동료 또는 동료 학생의 얼굴을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-212">Use the face of a colleague or fellow student.</span></span>

<span data-ttu-id="596e0-213">실행 중인 **Person 작성자**:</span><span class="sxs-lookup"><span data-stu-id="596e0-213">Running **Person Maker**:</span></span>

1.  <span data-ttu-id="596e0-214">**PersonMaker** 폴더를 열고 *PersonMaker 솔루션* 을 두 번 클릭 하 여 *Visual Studio*에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-214">Open the **PersonMaker** folder and double click on the *PersonMaker solution* to open it with *Visual Studio*.</span></span>

2.  <span data-ttu-id="596e0-215">*PersonMaker 솔루션이* 열리면 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-215">Once the *PersonMaker solution* is open, make sure that:</span></span>

    1. <span data-ttu-id="596e0-216">*솔루션 구성이* **디버그**로 설정 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-216">The *Solution Configuration* is set to **Debug**.</span></span>

    2. <span data-ttu-id="596e0-217">*솔루션 플랫폼이* **x 86** 으로 설정 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-217">The *Solution Platform* is set to **x86**</span></span>

    3. <span data-ttu-id="596e0-218">*대상 플랫폼이* **로컬 컴퓨터**입니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-218">The *Target Platform* is **Local Machine**.</span></span>

    4.  <span data-ttu-id="596e0-219">*Nuget 패키지를 복원* 해야 할 수도 있습니다. *솔루션* 을 마우스 오른쪽 단추로 클릭 하 고 **nuget 패키지 복원**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-219">You also may need to *Restore NuGet Packages* (right-click the *Solution* and select **Restore NuGet Packages**).</span></span>

3.  <span data-ttu-id="596e0-220">*로컬 컴퓨터* 를 클릭 하면 응용 프로그램이 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-220">Click *Local Machine* and the application will start.</span></span> <span data-ttu-id="596e0-221">더 작은 화면에서 모든 콘텐츠가 표시 되지 않을 수도 있지만,이 경우에는 자세히 스크롤하여 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-221">Be aware, on smaller screens, all content may not be visible, though you can scroll further down to view it.</span></span>

    ![person 작성자 사용자 인터페이스](images/AzureLabs-Lab4-07.png)

4.  <span data-ttu-id="596e0-223">Azure 내의 *Face API* 서비스에서 **azure 인증 키**를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-223">Insert your **Azure Authentication Key**, which you should have, from your *Face API* service within Azure.</span></span>

5.  <span data-ttu-id="596e0-224">넣거나</span><span class="sxs-lookup"><span data-stu-id="596e0-224">Insert:</span></span>

    1. <span data-ttu-id="596e0-225">*사용자 그룹*에 할당 하려는 *ID* 입니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-225">The *ID* you want to assign to the *Person Group*.</span></span> <span data-ttu-id="596e0-226">ID는 소문자 여야 하며 공백 없이 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-226">The ID must be lowercase, with no spaces.</span></span> <span data-ttu-id="596e0-227">Unity 프로젝트에서 나중에 필요 하므로이 ID를 기록해 둡니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-227">Make note of this ID, as it will be required later in your Unity project.</span></span>
    2. <span data-ttu-id="596e0-228">*사용자 그룹* 에 할당 하려는 *이름* 입니다 (공백이 있을 수 있음).</span><span class="sxs-lookup"><span data-stu-id="596e0-228">The *Name* you want to assign to the *Person Group* (can have spaces).</span></span>


6.  <span data-ttu-id="596e0-229">**사용자 그룹 만들기** 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-229">Press **Create Person Group** button.</span></span> <span data-ttu-id="596e0-230">단추 아래에 확인 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-230">A confirmation message should appear underneath the button.</span></span>

> [!NOTE]
> <span data-ttu-id="596e0-231">' 액세스 거부 ' 오류가 발생 한 경우 Azure 서비스에 대해 설정한 위치를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-231">If you have an 'Access Denied' error, check the location you set for your Azure service.</span></span> <span data-ttu-id="596e0-232">위에서 설명한 것 처럼이 앱은 ' 미국 서 부 ' 용으로 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-232">As stated above, this app is designed for 'West US'.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="596e0-233">**알려진 그룹 페치** 단추를 클릭할 수도 있습니다 .이는 이미 person 그룹을 만든 경우 새 항목을 만드는 대신 해당 그룹을 사용 하려는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-233">You will notice that you can also click the **Fetch a Known Group** button: this is for if you have already created a person group, and wish to use that, rather than create a new one.</span></span> <span data-ttu-id="596e0-234">알려진 그룹을 사용 하 여 *사용자 그룹 만들기* 를 클릭 하면 그룹도 인출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-234">Be aware, if you click *Create a Person Group* with a known group, this will also fetch a group.</span></span>

7.  <span data-ttu-id="596e0-235">만들려는 *사용자* 의 *이름을* 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-235">Insert the *Name* of the *Person* you want to create.</span></span>

    1. <span data-ttu-id="596e0-236">**사용자 만들기** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-236">Click the **Create Person** button.</span></span>

    2. <span data-ttu-id="596e0-237">단추 아래에 확인 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-237">A confirmation message should appear underneath the button.</span></span>

    3. <span data-ttu-id="596e0-238">이전에 만든 사용자를 삭제 하려면 텍스트 상자에 이름을 쓰고 **Person delete** 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-238">If you wish to delete a person you have previously created, you can write the name into the textbox and press **Delete Person**</span></span>

8.  <span data-ttu-id="596e0-239">그룹에 추가할 사용자의 10 개 사진 위치를 알고 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-239">Make sure you know the location of ten (10) photos of the person you would like to add to your group.</span></span>

9.  <span data-ttu-id="596e0-240">**만들기 및 폴더 열기** 를 눌러 Windows 탐색기를 사용자와 연결 된 폴더에 엽니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-240">Press **Create and Open Folder** to open Windows Explorer to the folder associated to the person.</span></span> <span data-ttu-id="596e0-241">폴더에 10 개의 이미지를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-241">Add the ten (10) images in the folder.</span></span> <span data-ttu-id="596e0-242">*JPG* 또는 *PNG* 파일 형식 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-242">These must be of *JPG* or *PNG* file format.</span></span>

10. <span data-ttu-id="596e0-243">**Azure에 제출을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-243">Click on **Submit To Azure**.</span></span> <span data-ttu-id="596e0-244">카운터는 제출 상태를 표시 한 다음 완료 되 면 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-244">A counter will show you the state of the submission, followed by a message when it has completed.</span></span>

11. <span data-ttu-id="596e0-245">카운터가 완료 되 고 확인 메시지가 표시 되 면 **학습** 을 클릭 하 여 서비스를 학습 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-245">Once the counter has finished and a confirmation message has been displayed click on **Train** to train your Service.</span></span>

<span data-ttu-id="596e0-246">프로세스가 완료 되 면 Unity로 이동할 준비가 된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-246">Once the process has completed, you are ready to move into Unity.</span></span>

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="596e0-247">3 장-Unity 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="596e0-247">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="596e0-248">다음은 혼합 현실를 사용 하 여 개발 하기 위한 일반적인 설정으로, 다른 프로젝트에 적합 한 템플릿입니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-248">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="596e0-249">*Unity* 를 열고 **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-249">Open *Unity* and click **New**.</span></span> 

    ![새 Unity 프로젝트를 시작 합니다.](images/AzureLabs-Lab4-08.png)

2.  <span data-ttu-id="596e0-251">이제 Unity 프로젝트 이름을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-251">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="596e0-252">**MR_FaceRecognition**을 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-252">Insert **MR_FaceRecognition**.</span></span> <span data-ttu-id="596e0-253">프로젝트 형식이 **3d**로 설정 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-253">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="596e0-254">위치를 적절 한 **위치** 에 적절 하 게 설정 합니다. 루트 디렉터리에 가까울수록 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-254">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="596e0-255">그런 다음 **프로젝트 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-255">Then, click **Create project**.</span></span>

    ![새 Unity 프로젝트에 대 한 세부 정보를 제공 합니다.](images/AzureLabs-Lab4-09.png)

3.  <span data-ttu-id="596e0-257">Unity를 연 상태에서 기본 **스크립트 편집기** 가 **Visual Studio**로 설정 되어 있는지 확인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-257">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="596e0-258">**> 기본 설정 편집** 으로 이동한 다음 새 창에서 **외부 도구**로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-258">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="596e0-259">**외부 스크립트 편집기** 를 **Visual Studio 2017**로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-259">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="596e0-260">**기본 설정** 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-260">Close the **Preferences** window.</span></span>

    ![스크립트 편집기 기본 설정을 업데이트 합니다.](images/AzureLabs-Lab4-10.png)

4.  <span data-ttu-id="596e0-262">그런 다음 **파일 > 빌드 설정** 으로 이동 하 고 플랫폼 **전환** 단추를 클릭 하 여 플랫폼을 **유니버설 Windows 플랫폼**로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-262">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![빌드 설정 창에서 플랫폼을 UWP로 전환 합니다.](images/AzureLabs-Lab4-11.png)

5.  <span data-ttu-id="596e0-264">**파일 > 빌드 설정** 으로 이동 하 고 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-264">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="596e0-265">**대상 장치가** **HoloLens** 로 설정 됨</span><span class="sxs-lookup"><span data-stu-id="596e0-265">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="596e0-266">모던 헤드셋의 경우 **대상 장치** 를 *모든 장치로*설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-266">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2. <span data-ttu-id="596e0-267">**빌드 형식이** **D3D** 로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-267">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="596e0-268">**SDK** 가 **최신 설치** 로 설정 됨</span><span class="sxs-lookup"><span data-stu-id="596e0-268">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="596e0-269">**Visual Studio 버전이** **최신 설치** 로 설정 됨</span><span class="sxs-lookup"><span data-stu-id="596e0-269">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="596e0-270">**빌드 및 실행** 이 **로컬 컴퓨터로** 설정 됨</span><span class="sxs-lookup"><span data-stu-id="596e0-270">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="596e0-271">장면을 저장 하 고 빌드에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-271">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="596e0-272">이렇게 하려면 열려 있는 **장면 추가**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-272">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="596e0-273">저장 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-273">A save window will appear.</span></span>

            ![열린 장면 추가 단추를 클릭 합니다.](images/AzureLabs-Lab4-12.png)

        2. <span data-ttu-id="596e0-275">새 **폴더** 단추를 선택 하 여 새 폴더를 만들고 이름을 **장면**으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-275">Select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![새 스크립트 폴더 만들기](images/AzureLabs-Lab4-13.png)

        3. <span data-ttu-id="596e0-277">새로 만든 **장면** 폴더를 연 다음 **파일 이름**: 텍스트 필드에 **FaceRecScene**를 입력 하 고 **저장**을 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-277">Open your newly created **Scenes** folder, and then in the **File name**: text field, type **FaceRecScene**, then press **Save**.</span></span>

            ![새 장면에 이름을 지정 합니다.](images/AzureLabs-Lab4-14.png)

    7. <span data-ttu-id="596e0-279">*빌드 설정*의 나머지 설정은 지금은 기본값으로 남겨 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-279">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="596e0-280">*빌드 설정* 창에서 **플레이어 설정** 단추를 클릭 하면 *검사기* 가 있는 공간에서 관련 패널이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-280">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![플레이어 설정을 엽니다.](images/AzureLabs-Lab4-15.png)

7. <span data-ttu-id="596e0-282">이 패널에서 몇 가지 설정을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-282">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="596e0-283">**기타 설정** 탭에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-283">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="596e0-284">**스크립팅** **런타임 버전** 은 **실험적** (.net 4.6에 해당) 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-284">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent).</span></span> <span data-ttu-id="596e0-285">이렇게 변경 하면 편집기를 다시 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-285">Changing this will trigger a need to restart the Editor.</span></span>
        2. <span data-ttu-id="596e0-286">**Scripting 백엔드** 는 **.net** 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-286">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="596e0-287">**API 호환성 수준은** **.net 4.6** 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-287">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![다른 설정을 업데이트 합니다.](images/AzureLabs-Lab4-16.png)
      
    2. <span data-ttu-id="596e0-289">**게시 설정** 탭의 **기능**아래에서 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-289">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="596e0-290">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="596e0-290">**InternetClient**</span></span>
        - <span data-ttu-id="596e0-291">**웹캠**</span><span class="sxs-lookup"><span data-stu-id="596e0-291">**Webcam**</span></span>

            ![게시 설정을 업데이트 하는 중입니다.](images/AzureLabs-Lab4-17.png)

    3. <span data-ttu-id="596e0-293">패널의 아래쪽에서 **XR 설정** ( **게시 설정**아래에 있음), **지원 되는 틱 가상 현실**, **Windows Mixed reality SDK** 가 추가 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-293">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![X R 설정을 업데이트 합니다.](images/AzureLabs-Lab4-18.png)

8.  <span data-ttu-id="596e0-295">*빌드 설정*으로 돌아가서 **Unity C# 프로젝트가** 더 이상 회색으로 표시 되지 않습니다. 이 옆의 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-295">Back in *Build Settings*, **Unity C# Projects** is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="596e0-296">빌드 설정 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-296">Close the Build Settings window.</span></span>
10. <span data-ttu-id="596e0-297">장면 및 프로젝트를 저장 합니다 (**파일 > 장면/파일 저장 > 프로젝트 저장**).</span><span class="sxs-lookup"><span data-stu-id="596e0-297">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4---main-camera-setup"></a><span data-ttu-id="596e0-298">4 장-기본 카메라 설정</span><span class="sxs-lookup"><span data-stu-id="596e0-298">Chapter 4 - Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="596e0-299">이 과정의 *Unity 설정* 구성 요소를 건너뛰고 바로 코드를 계속 진행 하려는 경우 [unitypackage를 다운로드](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage)하 여 [사용자 지정 패키지로](https://docs.unity3d.com/Manual/AssetPackages.html)프로젝트에 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-299">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage), and import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="596e0-300">이 패키지에는 [5 장에서](#chapter-5--import-the-newtonsoftjson-library)다룬 *newtonsoft.json DLL*의 가져오기도 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-300">Be aware that this package also includes the import of the *Newtonsoft DLL*, covered in [Chapter 5](#chapter-5--import-the-newtonsoftjson-library).</span></span> <span data-ttu-id="596e0-301">이를 가져온 후에는 [6 장](#chapter-6---create-the-faceanalysis-class)에서 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-301">With this imported, you can continue from [Chapter 6](#chapter-6---create-the-faceanalysis-class).</span></span>

1.  <span data-ttu-id="596e0-302">*계층* 패널에서 **기본 카메라**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-302">In the *Hierarchy* Panel, select the **Main Camera**.</span></span>

2.  <span data-ttu-id="596e0-303">선택한 후에는 *검사기 패널*에서 **주 카메라** 의 모든 구성 요소를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-303">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="596e0-304">**카메라 개체** 의 이름을 **주 카메라로** 지정 해야 합니다 (철자 확인).</span><span class="sxs-lookup"><span data-stu-id="596e0-304">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>

    2. <span data-ttu-id="596e0-305">기본 카메라 **태그** 는 **maincamera** 로 설정 되어야 합니다 (철자 확인).</span><span class="sxs-lookup"><span data-stu-id="596e0-305">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3. <span data-ttu-id="596e0-306">**변환 위치가** **0, 0, 0** 으로 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-306">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4. <span data-ttu-id="596e0-307">**Clear 플래그** 를 **Solid 색** 으로 설정</span><span class="sxs-lookup"><span data-stu-id="596e0-307">Set **Clear Flags** to **Solid Color**</span></span>

    5. <span data-ttu-id="596e0-308">카메라 구성 요소의 **배경색** 을 **검은색, 알파 0 (16 진수 코드: #00000000)** 으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-308">Set the **Background** Color of the Camera Component to **Black, Alpha 0 (Hex Code: #00000000)**</span></span>

        ![카메라 구성 요소 설정](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a><span data-ttu-id="596e0-310">5 장-Newtonsoft.json 라이브러리 가져오기</span><span class="sxs-lookup"><span data-stu-id="596e0-310">Chapter 5 – Import the Newtonsoft.Json library</span></span>

> [!IMPORTANT]
> <span data-ttu-id="596e0-311">[마지막 챕터](#chapter-4---main-camera-setup)에서 '. unitypackage '를 가져온 경우이 챕터를 건너뛸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-311">If you imported the '.unitypackage' in the [last Chapter](#chapter-4---main-camera-setup), you can skip this Chapter.</span></span>

<span data-ttu-id="596e0-312">받아서 봇 서비스로 전송 되는 개체를 deserialize 하 고 serialize 할 수 있도록 *newtonsoft.json* 라이브러리를 다운로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-312">To help you deserialize and serialize objects received and sent to the Bot Service you need to download the *Newtonsoft.Json* library.</span></span> <span data-ttu-id="596e0-313">이 [unity 패키지 파일](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage)에서 올바른 unity 폴더 구조를 사용 하 여 이미 구성 된 호환 버전을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-313">You will find a compatible version already organized with the correct Unity folder structure in this [Unity package file](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage).</span></span> 

<span data-ttu-id="596e0-314">라이브러리를 가져오려면:</span><span class="sxs-lookup"><span data-stu-id="596e0-314">To import the library:</span></span>

1.  <span data-ttu-id="596e0-315">Unity 패키지를 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-315">Download the Unity Package.</span></span>
2.  <span data-ttu-id="596e0-316">**자산**, **패키지 가져오기**, **사용자 지정 패키지**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-316">Click on **Assets**, **Import Package**, **Custom Package**.</span></span>

    ![Newtonsoft.json 라이브러리 가져오기](images/AzureLabs-Lab4-20.png)

3.  <span data-ttu-id="596e0-318">다운로드 한 Unity 패키지를 찾고 열기를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-318">Look for the Unity Package you have downloaded, and click Open.</span></span>
4.  <span data-ttu-id="596e0-319">패키지의 모든 구성 요소가 선택 인지 확인 하 고 **가져오기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-319">Make sure all the components of the package are ticked and click **Import**.</span></span>

    ![Newtonsoft.json 라이브러리 가져오기](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a><span data-ttu-id="596e0-321">6 장-FaceAnalysis 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="596e0-321">Chapter 6 - Create the FaceAnalysis class</span></span>

<span data-ttu-id="596e0-322">FaceAnalysis 클래스의 목적은 Azure 얼굴 인식 서비스와 통신 하는 데 필요한 메서드를 호스트 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-322">The purpose of the FaceAnalysis class is to host the methods necessary to communicate with your Azure Face Recognition Service.</span></span> 

- <span data-ttu-id="596e0-323">서비스를 캡처한 후 캡처 이미지는 분석 하 고 내 얼굴을 식별 하며 알려진 사람에 게 속해 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-323">After sending the service a capture image, it will analyse it and identify the faces within, and determine if any belong to a known person.</span></span> 
- <span data-ttu-id="596e0-324">알려진 사용자가 있는 경우이 클래스는 해당 이름을 장면에 UI 텍스트로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-324">If a known person is found, this class will display its name as UI text in the scene.</span></span>

<span data-ttu-id="596e0-325">*FaceAnalysis* 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="596e0-325">To create the *FaceAnalysis* class:</span></span>

 1. <span data-ttu-id="596e0-326">프로젝트 패널에 있는 *자산 폴더* 를 마우스 오른쪽 단추로 클릭 한 다음**폴더** **만들기** > 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-326">Right-click in the *Assets Folder* located in the Project Panel, then click on **Create** > **Folder**.</span></span> <span data-ttu-id="596e0-327">폴더 **스크립트**를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-327">Call the folder **Scripts**.</span></span> 

    ![FaceAnalysis 클래스를 만듭니다.](images/AzureLabs-Lab4-22.png)

2.  <span data-ttu-id="596e0-329">위에서 만든 폴더를 두 번 클릭 하 여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-329">Double click on the folder just created, to open it.</span></span> 
3.  <span data-ttu-id="596e0-330">폴더 내부를 마우스 오른쪽 단추로 클릭 한 다음 **C# 스크립트** **만들기**  >  를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-330">Right-click inside the folder, then click on **Create** > **C# Script**.</span></span> <span data-ttu-id="596e0-331">*FaceAnalysis*스크립트를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-331">Call the script *FaceAnalysis*.</span></span> 
4.  <span data-ttu-id="596e0-332">새 *FaceAnalysis* 스크립트를 두 번 클릭 하 여 Visual Studio 2017을 사용 하 여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-332">Double click on the new *FaceAnalysis* script to open it with Visual Studio 2017.</span></span>
5.  <span data-ttu-id="596e0-333">*FaceAnalysis* 클래스 위에 다음 네임 스페이스를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-333">Enter the following namespaces above the *FaceAnalysis* class:</span></span>

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  <span data-ttu-id="596e0-334">이제 deserialising에 사용 되는 모든 개체를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-334">You now need to add all of the objects which are used for deserialising.</span></span> <span data-ttu-id="596e0-335">이러한 개체는 *FaceAnalysis* 스크립트 (아래쪽 중괄호 아래) **외부** 에 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-335">These objects need to be added **outside** of the *FaceAnalysis* script (beneath the bottom curly bracket).</span></span> 

    ```csharp
        /// <summary>
        /// The Person Group object
        /// </summary>
        public class Group_RootObject
        {
            public string personGroupId { get; set; }
            public string name { get; set; }
            public object userData { get; set; }
        }

        /// <summary>
        /// The Person Face object
        /// </summary>
        public class Face_RootObject
        {
            public string faceId { get; set; }
        }

        /// <summary>
        /// Collection of faces that needs to be identified
        /// </summary>
        public class FacesToIdentify_RootObject
        {
            public string personGroupId { get; set; }
            public List<string> faceIds { get; set; }
            public int maxNumOfCandidatesReturned { get; set; }
            public double confidenceThreshold { get; set; }
        }

        /// <summary>
        /// Collection of Candidates for the face
        /// </summary>
        public class Candidate_RootObject
        {
            public string faceId { get; set; }
            public List<Candidate> candidates { get; set; }
        }

        public class Candidate
        {
            public string personId { get; set; }
            public double confidence { get; set; }
        }

        /// <summary>
        /// Name and Id of the identified Person
        /// </summary>
        public class IdentifiedPerson_RootObject
        {
            public string personId { get; set; }
            public string name { get; set; }
        }
    ```
7. <span data-ttu-id="596e0-336">*Start ()* 및 *Update ()* 메서드는 사용 되지 않으므로 지금 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-336">The *Start()* and *Update()* methods will not be used, so delete them now.</span></span> 

8.  <span data-ttu-id="596e0-337">*FaceAnalysis* 클래스 내에서 다음 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-337">Inside the *FaceAnalysis* class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static FaceAnalysis Instance;

        /// <summary>
        /// The analysis result text
        /// </summary>
        private TextMesh labelText;

        /// <summary>
        /// Bytes of the image captured with camera
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// Path of the image captured with camera
        /// </summary>
        internal string imagePath;

        /// <summary>
        /// Base endpoint of Face Recognition Service
        /// </summary>
        const string baseEndpoint = "https://westus.api.cognitive.microsoft.com/face/v1.0/";

        /// <summary>
        /// Auth key of Face Recognition Service
        /// </summary>
        private const string key = "- Insert your key here -";

        /// <summary>
        /// Id (name) of the created person group 
        /// </summary>
        private const string personGroupId = "- Insert your group Id here -";
    ```

    > [!NOTE]
    > <span data-ttu-id="596e0-338">**키** 와 **personGroupId** 을 이전에 만든 그룹의 서비스 키와 Id로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-338">Replace the **key** and the **personGroupId** with your Service Key and the Id of the group that you created previously.</span></span>

9.  <span data-ttu-id="596e0-339">Initialises *()* 메서드를 추가 합니다 .이 메서드는 클래스를 기본 카메라에 *ImageCapture* 클래스를 추가 하 고 레이블 생성 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-339">Add the *Awake()* method, which initialises the class, adding the *ImageCapture* class to the Main Camera and calls the Label creation method:</span></span>

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;

            // Add the ImageCapture Class to this Game Object
            gameObject.AddComponent<ImageCapture>();

            // Create the text label in the scene
            CreateLabel();
        }
    ```

10. <span data-ttu-id="596e0-340">*CreateLabel ()* 메서드를 추가 합니다 .이 메서드는 분석 결과를 표시 하는 *레이블* 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-340">Add the *CreateLabel()* method, which creates the *Label* object to display the analysis result:</span></span>

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private void CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Attach the label to the Main Camera
            newLabel.transform.parent = gameObject.transform;
            
            // Resize and position the new cursor
            newLabel.transform.localScale = new Vector3(0.4f, 0.4f, 0.4f);
            newLabel.transform.position = new Vector3(0f, 3f, 60f);

            // Creating the text of the Label
            labelText = newLabel.AddComponent<TextMesh>();
            labelText.anchor = TextAnchor.MiddleCenter;
            labelText.alignment = TextAlignment.Center;
            labelText.tabSize = 4;
            labelText.fontSize = 50;
            labelText.text = ".";       
        }
    ```

11. <span data-ttu-id="596e0-341">*DetectFacesFromImage ()* 및 *GetImageAsByteArray ()* 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-341">Add the *DetectFacesFromImage()* and *GetImageAsByteArray()* method.</span></span> <span data-ttu-id="596e0-342">이전에는 얼굴 인식 서비스를 요청 하 여 제출 된 이미지에서 가능한 얼굴을 검색 하 고, 후자는 캡처된 이미지를 바이트 배열로 변환 하는 데 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-342">The former will request the Face Recognition Service to detect any possible face in the submitted image, while the latter is necessary to convert the captured image into a bytes array:</span></span>

    ```csharp
        /// <summary>
        /// Detect faces from a submitted image
        /// </summary>
        internal IEnumerator DetectFacesFromImage()
        {
            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}detect";

            // Change the image into a bytes array
            imageBytes = GetImageAsByteArray(imagePath);

            using (UnityWebRequest www = 
                UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/octet-stream");
                www.uploadHandler.contentType = "application/octet-stream";
                www.uploadHandler = new UploadHandlerRaw(imageBytes);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Face_RootObject[] face_RootObject = 
                    JsonConvert.DeserializeObject<Face_RootObject[]>(jsonResponse);

                List<string> facesIdList = new List<string>();
                // Create a list with the face Ids of faces detected in image
                foreach (Face_RootObject faceRO in face_RootObject)
                {
                    facesIdList.Add(faceRO.faceId);
                    Debug.Log($"Detected face - Id: {faceRO.faceId}");
                }
                
                StartCoroutine(IdentifyFaces(facesIdList));
            }
        }

        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

12. <span data-ttu-id="596e0-343">*IdentifyFaces ()* 메서드를 추가 합니다 .이 메서드는 전송 된 이미지에서 이전에 검색 된 알려진 얼굴을 식별 하도록 *얼굴 인식 서비스* 에 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-343">Add the *IdentifyFaces()* method, which requests the *Face Recognition Service* to identify any known face previously detected in the submitted image.</span></span> <span data-ttu-id="596e0-344">요청은 이름이 아니라 식별 된 사람의 id를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-344">The request will return an id of the identified person but not the name:</span></span>

    ```csharp
        /// <summary>
        /// Identify the faces found in the image within the person group
        /// </summary>
        internal IEnumerator IdentifyFaces(List<string> listOfFacesIdToIdentify)
        {
            // Create the object hosting the faces to identify
            FacesToIdentify_RootObject facesToIdentify = new FacesToIdentify_RootObject();
            facesToIdentify.faceIds = new List<string>();
            facesToIdentify.personGroupId = personGroupId;
            foreach (string facesId in listOfFacesIdToIdentify)
            {
                facesToIdentify.faceIds.Add(facesId);
            }
            facesToIdentify.maxNumOfCandidatesReturned = 1;
            facesToIdentify.confidenceThreshold = 0.5;

            // Serialise to Json format
            string facesToIdentifyJson = JsonConvert.SerializeObject(facesToIdentify);
            // Change the object into a bytes array
            byte[] facesData = Encoding.UTF8.GetBytes(facesToIdentifyJson);

            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}identify";

            using (UnityWebRequest www = UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/json");
                www.uploadHandler.contentType = "application/json";
                www.uploadHandler = new UploadHandlerRaw(facesData);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                Candidate_RootObject [] candidate_RootObject = JsonConvert.DeserializeObject<Candidate_RootObject[]>(jsonResponse);

                // For each face to identify that ahs been submitted, display its candidate
                foreach (Candidate_RootObject candidateRO in candidate_RootObject)
                {
                    StartCoroutine(GetPerson(candidateRO.candidates[0].personId));
                    
                    // Delay the next "GetPerson" call, so all faces candidate are displayed properly
                    yield return new WaitForSeconds(3);
                }           
            }
        }
    ```

13. <span data-ttu-id="596e0-345">*Getperson ()* 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-345">Add the *GetPerson()* method.</span></span> <span data-ttu-id="596e0-346">이 메서드는 개인 id를 제공 하 여 식별 된 사람의 이름을 반환 하도록 *얼굴 인식 서비스* 에 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-346">By providing the person id, this method then requests for the *Face Recognition Service* to return the name of the identified person:</span></span>

    ```csharp
        /// <summary>
        /// Provided a personId, retrieve the person name associated with it
        /// </summary>
        internal IEnumerator GetPerson(string personId)
        {
            string getGroupEndpoint = $"{baseEndpoint}persongroups/{personGroupId}/persons/{personId}?";
            WWWForm webForm = new WWWForm();

            using (UnityWebRequest www = UnityWebRequest.Get(getGroupEndpoint))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                IdentifiedPerson_RootObject identifiedPerson_RootObject = JsonConvert.DeserializeObject<IdentifiedPerson_RootObject>(jsonResponse);

                // Display the name of the person in the UI
                labelText.text = identifiedPerson_RootObject.name;
            }
        }
    ```

14.  <span data-ttu-id="596e0-347">Unity 편집기로 다시 이동 하기 전에 변경 내용을 **저장** 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-347">Remember to **Save** the changes before going back to the Unity Editor.</span></span>
15.  <span data-ttu-id="596e0-348">Unity 편집기에서 프로젝트 패널의 Scripts 폴더에 있는 FaceAnalysis 스크립트를 *계층 패널*의 기본 카메라 개체로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-348">In the Unity Editor, drag the FaceAnalysis script from the Scripts folder in Project panel to the Main Camera object in the *Hierarchy panel*.</span></span> <span data-ttu-id="596e0-349">새 스크립트 구성 요소가 기본 카메라에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-349">The new script component will be so added to the Main Camera.</span></span> 

![기본 카메라에 FaceAnalysis 두기](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a><span data-ttu-id="596e0-351">7 장-ImageCapture 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="596e0-351">Chapter 7 - Create the ImageCapture class</span></span>

<span data-ttu-id="596e0-352">*ImageCapture* 클래스의 목적은 *Azure 얼굴 인식 서비스* 와 통신 하는 데 필요한 메서드를 호스트 하 여 캡처할 이미지를 분석 하 고, 얼굴을 식별 하 고, 알려진 사람에 게 속하는지 확인 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-352">The purpose of the *ImageCapture* class is to host the methods necessary to communicate with your *Azure Face Recognition Service* to analyse the image you will capture, identifying faces in it and determining if it belongs to a known person.</span></span> <span data-ttu-id="596e0-353">알려진 사용자가 있는 경우이 클래스는 해당 이름을 장면에 UI 텍스트로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-353">If a known person is found, this class will display its name as UI text in the scene.</span></span>

<span data-ttu-id="596e0-354">*ImageCapture* 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="596e0-354">To create the *ImageCapture* class:</span></span>
 
1.  <span data-ttu-id="596e0-355">이전에 만든 **Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 한 다음 **만들기**,  **C# 스크립트**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-355">Right-click inside the **Scripts** folder you have created previously, then click on **Create**, **C# Script**.</span></span> <span data-ttu-id="596e0-356">*ImageCapture*스크립트를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-356">Call the script *ImageCapture*.</span></span> 
2.  <span data-ttu-id="596e0-357">새 *ImageCapture* 스크립트를 두 번 클릭 하 여 Visual Studio 2017을 사용 하 여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-357">Double click on the new *ImageCapture* script to open it with Visual Studio 2017.</span></span>
3.  <span data-ttu-id="596e0-358">ImageCapture 클래스 위에 다음 네임 스페이스를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-358">Enter the following namespaces above the ImageCapture class:</span></span>

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  <span data-ttu-id="596e0-359">*ImageCapture* 클래스 내에서 다음 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-359">Inside the *ImageCapture* class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture instance;

        /// <summary>
        /// Keeps track of tapCounts to name the captured images 
        /// </summary>
        private int tapsCount;

        /// <summary>
        /// PhotoCapture object used to capture images on HoloLens 
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// HoloLens class to capture user gestures
        /// </summary>
        private GestureRecognizer recognizer;
    ```

5.  <span data-ttu-id="596e0-360">클래스를 초기화 하는 데 필요한 *()* 및 *Start ()* 메서드를 추가 하 고 HoloLens에서 사용자의 제스처를 캡처할 수 있도록 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-360">Add the *Awake()* and *Start()* methods necessary to initialise the class and allow the HoloLens to capture the user's gestures:</span></span>

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Called right after Awake
        /// </summary>
        void Start()
        {
            // Initialises user gestures capture 
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

6.  <span data-ttu-id="596e0-361">사용자가 *탭* 제스처를 수행할 때 호출 되는 *TapHandler ()* 를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-361">Add the *TapHandler()* which is called when the user performs a *Tap* gesture:</span></span>

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            tapsCount++;
            ExecuteImageCaptureAndAnalysis();
        }
    ```

7.  <span data-ttu-id="596e0-362">*ExecuteImageCaptureAndAnalysis ()* 메서드를 추가 합니다 .이 메서드는 이미지 캡처 프로세스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-362">Add the *ExecuteImageCaptureAndAnalysis()* method, which will begin the process of Image Capturing:</span></span>

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Computer Vision service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters c = new CameraParameters();
                c.hologramOpacity = 0.0f;
                c.cameraResolutionWidth = targetTexture.width;
                c.cameraResolutionHeight = targetTexture.height;
                c.pixelFormat = CapturePixelFormat.BGRA32;

                captureObject.StartPhotoModeAsync(c, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    // Set the image path on the FaceAnalysis class
                    FaceAnalysis.Instance.imagePath = filePath;

                    photoCaptureObject.TakePhotoAsync
                    (filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
                });
            });
        }
    ```

8.  <span data-ttu-id="596e0-363">사진 캡처 프로세스가 완료 되 면 호출 되는 처리기를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-363">Add the handlers that are called when the photo capture process has been completed:</span></span>

    ```csharp
        /// <summary>
        /// Called right after the photo capture process has concluded
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        /// <summary>
        /// Register the full execution of the Photo Capture. If successfull, it will begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Request image caputer analysis
            StartCoroutine(FaceAnalysis.Instance.DetectFacesFromImage());
        }
    ```

9. <span data-ttu-id="596e0-364">Unity 편집기로 다시 이동 하기 전에 변경 내용을 **저장** 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-364">Remember to **Save** the changes before going back to the Unity Editor.</span></span>

## <a name="chapter-8---building-the-solution"></a><span data-ttu-id="596e0-365">8 장-솔루션 빌드</span><span class="sxs-lookup"><span data-stu-id="596e0-365">Chapter 8 - Building the solution</span></span>

<span data-ttu-id="596e0-366">응용 프로그램에 대 한 철저 한 테스트를 수행 하려면 HoloLens에 테스트용으로 로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-366">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>

<span data-ttu-id="596e0-367">이렇게 하려면 먼저 다음을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-367">Before you do, ensure that:</span></span>

-   <span data-ttu-id="596e0-368">3 장에서 설명한 모든 설정이 올바르게 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-368">All the settings mentioned in the Chapter 3 are set correctly.</span></span> 
-   <span data-ttu-id="596e0-369">*FaceAnalysis* 스크립트는 주 카메라 개체에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-369">The script *FaceAnalysis* is attached to the Main Camera object.</span></span> 
-   <span data-ttu-id="596e0-370">*FaceAnalysis* 스크립트 내에서 **인증 키** 와 **그룹 Id** 가 모두 설정 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-370">Both the **Auth Key** and **Group Id** have been set within the *FaceAnalysis* script.</span></span>

<span data-ttu-id="596e0-371">이 시점에서 솔루션을 빌드할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-371">A this point you are ready to build the Solution.</span></span> <span data-ttu-id="596e0-372">솔루션이 구축 되 면 응용 프로그램을 배포할 준비가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-372">Once the Solution has been built, you will be ready to deploy your application.</span></span>

<span data-ttu-id="596e0-373">빌드 프로세스를 시작 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-373">To begin the Build process:</span></span>

1.  <span data-ttu-id="596e0-374">파일, 저장을 차례로 클릭 하 여 현재 장면을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-374">Save the current scene by clicking on File, Save.</span></span>
2.  <span data-ttu-id="596e0-375">파일, 빌드 설정으로 이동 하 여 열려 있는 장면 추가를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-375">Go to File, Build Settings, click on Add Open Scenes.</span></span>
3.  <span data-ttu-id="596e0-376">Tick Unity C# 프로젝트를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-376">Make sure to tick Unity C# Projects.</span></span>

    ![Visual Studio에서 솔루션을 배포 합니다.](images/AzureLabs-Lab4-24.png)

4.  <span data-ttu-id="596e0-378">빌드를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-378">Press Build.</span></span> <span data-ttu-id="596e0-379">이 작업을 수행 하면 Unity는 파일 탐색기 창을 시작 합니다. 여기에서 앱을 빌드할 폴더를 만들고 선택 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-379">Upon doing so, Unity will launch a File Explorer window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="596e0-380">이제 Unity 프로젝트 내에서 해당 폴더를 만들고 it 앱을 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-380">Create that folder now, within the Unity project, and call it App.</span></span> <span data-ttu-id="596e0-381">그런 다음 앱 폴더를 선택 하 고 폴더 선택을 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-381">Then with the App folder selected, press Select Folder.</span></span> 
5.  <span data-ttu-id="596e0-382">Unity는 응용 프로그램 폴더에서 프로젝트 빌드를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-382">Unity will begin building your project, out to the App folder.</span></span> 
6.  <span data-ttu-id="596e0-383">Unity가 빌드를 완료 하면 (시간이 걸릴 수 있음) 빌드 위치에서 파일 탐색기 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-383">Once Unity has finished building (it might take some time), it will open a File Explorer window at the location of your build.</span></span>

    ![Visual Studio에서 솔루션을 배포 합니다.](images/AzureLabs-Lab4-25.png)

7.  <span data-ttu-id="596e0-385">앱 폴더를 연 다음, 위에 표시 된 대로 새 프로젝트 솔루션을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-385">Open your App folder, and then open the new Project Solution (as seen above, MR_FaceRecognition.sln).</span></span>


## <a name="chapter-9---deploying-your-application"></a><span data-ttu-id="596e0-386">9 장-응용 프로그램 배포</span><span class="sxs-lookup"><span data-stu-id="596e0-386">Chapter 9 - Deploying your application</span></span>

<span data-ttu-id="596e0-387">HoloLens에 배포 하려면:</span><span class="sxs-lookup"><span data-stu-id="596e0-387">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="596e0-388">HoloLens의 IP 주소 (원격 배포의 경우)가 필요 하 고 HoloLens가 **개발자 모드**에 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-388">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="596e0-389">가상 하드 디스크 파일에 대한 중요 정보를 제공하려면</span><span class="sxs-lookup"><span data-stu-id="596e0-389">To do this:</span></span>

    1. <span data-ttu-id="596e0-390">HoloLens를 입고 하는 동안 **설정을**엽니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-390">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="596e0-391">**네트워크 & 인터넷 > wi-fi > 고급 옵션** 으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-391">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="596e0-392">**IPv4** 주소를 적어둡니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-392">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="596e0-393">그런 다음 **설정**으로 다시 이동한 다음 **개발자를 위한 & 보안 >를 업데이트** 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-393">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="596e0-394">에서 개발자 모드를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-394">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="596e0-395">새 Unity 빌드 ( *앱* 폴더)로 이동 하 여 *Visual Studio*에서 솔루션 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-395">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
3.  <span data-ttu-id="596e0-396">솔루션 구성에서 **디버그**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-396">In the Solution Configuration select **Debug**.</span></span>
4.  <span data-ttu-id="596e0-397">솔루션 플랫폼에서 **x86**, **원격 컴퓨터**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-397">In the Solution Platform, select **x86**, **Remote Machine**.</span></span> 

    ![Visual Studio에서 솔루션을 배포 합니다.](images/AzureLabs-Lab4-26.png)
 
5.  <span data-ttu-id="596e0-399">**빌드 메뉴로** 이동 하 여 **솔루션 배포**를 클릭 하 여 응용 프로그램을 HoloLens로 테스트용으로 로드.</span><span class="sxs-lookup"><span data-stu-id="596e0-399">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="596e0-400">이제 앱이 HoloLens에 설치 된 앱 목록에 표시 되어 시작할 준비가 되었습니다!</span><span class="sxs-lookup"><span data-stu-id="596e0-400">Your App should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="596e0-401">모던 헤드셋에 배포 하려면 **솔루션 플랫폼** 을 *로컬 컴퓨터*로 설정 하 고 **구성을** *디버그*로 설정 하 고 *x 86* 을 **플랫폼**으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-401">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="596e0-402">그런 다음 **빌드 메뉴**를 사용 하 여 *솔루션 배포*를 선택 하 여 로컬 컴퓨터에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-402">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 


## <a name="chapter-10---using-the-application"></a><span data-ttu-id="596e0-403">10 장-응용 프로그램 사용</span><span class="sxs-lookup"><span data-stu-id="596e0-403">Chapter 10 - Using the application</span></span>

1.  <span data-ttu-id="596e0-404">HoloLens를 입고 앱을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-404">Wearing the HoloLens, launch the app.</span></span>
2.  <span data-ttu-id="596e0-405">*Face API*등록 한 사용자를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-405">Look at the person that you have registered with the *Face API*.</span></span> <span data-ttu-id="596e0-406">다음 사항을 확인합니다</span><span class="sxs-lookup"><span data-stu-id="596e0-406">Make sure that:</span></span>

    -  <span data-ttu-id="596e0-407">개인의 얼굴이 너무 멀리 떨어져 있으며 명확 하 게 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-407">The person's face is not too distant and clearly visible</span></span>
    -  <span data-ttu-id="596e0-408">환경 조명이 너무 어두움</span><span class="sxs-lookup"><span data-stu-id="596e0-408">The environment lighting is not too dark</span></span>

3.  <span data-ttu-id="596e0-409">탭 제스처를 사용 하 여 사용자의 사진을 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-409">Use the tap gesture to capture the person's picture.</span></span>
4.  <span data-ttu-id="596e0-410">앱이 분석 요청을 보내고 응답을 받을 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-410">Wait for the App to send the analysis request and receive a response.</span></span>
5.  <span data-ttu-id="596e0-411">사용자가 성공적으로 인식 되 면 사용자 이름이 UI 텍스트로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-411">If the person has been successfully recognized, the person's name will appear as UI text.</span></span>
6.  <span data-ttu-id="596e0-412">몇 초 마다 탭 제스처를 사용 하 여 캡처 프로세스를 반복할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-412">You can repeat the capture process using the tap gesture every few seconds.</span></span>

## <a name="your-finished-azure-face-api-application"></a><span data-ttu-id="596e0-413">완성 된 Azure Face API 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="596e0-413">Your finished Azure Face API Application</span></span>

<span data-ttu-id="596e0-414">축 하 합니다. Azure 얼굴 인식 서비스를 활용 하 여 이미지 내 얼굴을 감지 하 고 알려진 얼굴을 식별 하는 혼합 현실 앱을 빌드 했습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-414">Congratulations, you built a mixed reality app that leverages the Azure Face Recognition service to detect faces within an image, and identify any known faces.</span></span>

![이 과정을 완료 한 결과](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="596e0-416">보너스 연습</span><span class="sxs-lookup"><span data-stu-id="596e0-416">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="596e0-417">연습 1</span><span class="sxs-lookup"><span data-stu-id="596e0-417">Exercise 1</span></span>

<span data-ttu-id="596e0-418">**Azure Face API** 는 단일 이미지에서 최대 64 얼굴을 검색할 수 있을 만큼 강력 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-418">The **Azure Face API** is powerful enough to detect up to 64 faces in a single image.</span></span> <span data-ttu-id="596e0-419">응용 프로그램을 확장 하 여 두 개 또는 세 개의 얼굴을 인식할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-419">Extend the application, so that it could recognize two or three faces, amongst many other people.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="596e0-420">연습 2</span><span class="sxs-lookup"><span data-stu-id="596e0-420">Exercise 2</span></span>

<span data-ttu-id="596e0-421">또한 **Azure Face API** 는 모든 종류의 특성 정보를 다시 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-421">The **Azure Face API** is also able to provide back all kinds of attribute information.</span></span> <span data-ttu-id="596e0-422">응용 프로그램에이를 통합 합니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-422">Integrate this into the application.</span></span> <span data-ttu-id="596e0-423">이는 [Emotion API](https://azure.microsoft.com/en-au/services/cognitive-services/emotion/)와 결합 될 때 훨씬 더 흥미롭습니다.</span><span class="sxs-lookup"><span data-stu-id="596e0-423">This could be even more interesting, when combined with the [Emotion API](https://azure.microsoft.com/en-au/services/cognitive-services/emotion/).</span></span>
