---
title: MR 및 Azure Machine learning 307-
description: 혼합된 현실 응용 프로그램에서 Azure Machine Learning Studio를 구현 하는 방법을 알아보려면이 과정을 완료 합니다.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 혼합 현실, academy, unity, 자습서, api, 기계 학습, 기계 학습, 기계 학습 스튜디오, 몰입 형 hololens, vr
ms.openlocfilehash: 93263817df0fd809a09b32c1b34a636eab7026a1
ms.sourcegitcommit: 9b6949d7cd2e67e6bde9b32aebeaeea325baa6c4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66516035"
---
>[!NOTE]
><span data-ttu-id="06816-104">혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="06816-105">따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="06816-106">이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06816-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="06816-107">지원 되는 장치에서 작업을 계속 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06816-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="06816-108">새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06816-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="06816-109">게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06816-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-307-machine-learning"></a><span data-ttu-id="06816-110">MR 및 Azure 307: 기계 학습</span><span class="sxs-lookup"><span data-stu-id="06816-110">MR and Azure 307: Machine learning</span></span>

![최종 제품-시작](images/AzureLabs-Lab7-0.png)

<span data-ttu-id="06816-112">이 과정에서는 Azure Machine Learning Studio를 사용 하 여 혼합된 현실 응용 프로그램에 Machine Learning (ML) 기능을 추가 하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="06816-112">In this course, you will learn how to add Machine Learning (ML) capabilities to a mixed reality application using Azure Machine Learning Studio.</span></span>

<span data-ttu-id="06816-113">*Azure Machine Learning Studio* 는 많은 수의 데이터 입력, 출력, 준비 및 시각화를 사용 하 여 도움이 될 수 있는 기계 학습 알고리즘을 사용 하 여 개발자가 제공 하는 Microsoft 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="06816-113">*Azure Machine Learning Studio* is a Microsoft service, which provides developers with a large number of machine learning algorithms, which can help with data input, output, preparation, and visualization.</span></span> <span data-ttu-id="06816-114">이러한 구성 요소에서 예측 분석 실험을 개발, 반복 및 모델 학습에 사용 가능한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06816-114">From these components, it is then possible to develop a predictive analytics experiment, iterate on it, and use it to train your model.</span></span> <span data-ttu-id="06816-115">다음 학습 가능 모델 운영 Azure 클라우드 내에서 새 데이터 점수 매기기 다음 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-115">Following training, you can make your model operational within the Azure cloud, so that it can then score new data.</span></span> <span data-ttu-id="06816-116">자세한 내용은 참조는 [Azure Machine Learning Studio 페이지](https://azure.microsoft.com/en-au/services/machine-learning-studio/)합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-116">For more information, visit the [Azure Machine Learning Studio page](https://azure.microsoft.com/en-au/services/machine-learning-studio/).</span></span>

<span data-ttu-id="06816-117">이 과정을 완료 혼합된 현실 헤드셋 몰입 형 응용 프로그램을 갖습니다 하 고 다음을 수행 하는 방법을 배웠습니다 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06816-117">Having completed this course, you will have a mixed reality immersive headset application, and will have learned how do the following:</span></span>

1.  <span data-ttu-id="06816-118">테이블의 판매 데이터를 제공 합니다 *Azure Machine Learning Studio* 포털 및 인기 있는 항목의 향후 판매를 예측 하는 알고리즘 설계 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-118">Provide a table of sales data to the *Azure Machine Learning Studio* portal, and        design an algorithm to predict future sales of popular items.</span></span>
2.  <span data-ttu-id="06816-119">만들기는 **Unity 프로젝트**를 받을 수 있으며 ML 서비스에서 예측 데이터를 해석 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-119">Create a **Unity Project**, which can receive and interpret prediction data from the ML service.</span></span>
3.  <span data-ttu-id="06816-120">예측 데이터를 내 시각적으로 표시 합니다 **Unity 프로젝트**을 통해 선반에 있는 가장 인기 있는 판매 항목을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-120">Display the predication data visually within the **Unity Project**, through providing the most popular sales items, on a shelf.</span></span>

<span data-ttu-id="06816-121">응용 프로그램에서는 사용자의 몫 디자인을 사용 하 여 결과에서는 통합 하는 방법에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-121">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="06816-122">이 과정은 Unity 프로젝트를 사용 하 여 Azure 서비스를 통합 하는 방법을 알려 주기 위해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="06816-122">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="06816-123">혼합된 현실 응용 프로그램을 강화 하기 위해이 과정에서 얻는 지식을 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="06816-123">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="06816-124">이 과정은 다른 혼합 현실 Labs를 직접 포함 하지 않는 자체 포함 된 자습서입니다.</span><span class="sxs-lookup"><span data-stu-id="06816-124">This course is a self-contained tutorial, which does not directly involve any other Mixed Reality Labs.</span></span>

## <a name="device-support"></a><span data-ttu-id="06816-125">장치 지원</span><span class="sxs-lookup"><span data-stu-id="06816-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="06816-126">과정</span><span class="sxs-lookup"><span data-stu-id="06816-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="06816-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="06816-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="06816-128"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="06816-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="06816-129">MR 및 Azure 307: 기계 학습</span><span class="sxs-lookup"><span data-stu-id="06816-129">MR and Azure 307: Machine learning</span></span></td><td style="text-align: center;"> <span data-ttu-id="06816-130">✔️</span><span class="sxs-lookup"><span data-stu-id="06816-130">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="06816-131">✔️</span><span class="sxs-lookup"><span data-stu-id="06816-131">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="06816-132">이 코스는 주로 Windows Mixed Reality 몰입 형 (VR) 헤드셋 주력, Microsoft HoloLens이 과정에서 배운 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06816-132">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="06816-133">과정을 따라가려면 정보 HoloLens를 지원 하기 위해 사용 해야 합니다. 변경 내용에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="06816-133">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="06816-134">HoloLens를 사용 하는 경우 음성 캡처하는 동안 일부 echo를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06816-134">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="06816-135">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="06816-135">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="06816-136">이 자습서는 Unity 사용 하 여 기본 경험이 있는 개발자 용으로 설계 하 고 C#입니다.</span><span class="sxs-lookup"><span data-stu-id="06816-136">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="06816-137">또한 주의 필수 구성 요소 및이 문서에서 작성 된 지침을 나타내는 새로운 테스트 되었으며 (2018 년 5 월) 작성 시점에 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-137">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="06816-138">내에서 나열 된 사용 가능한 최신 소프트웨어를 사용 하는 합니다 [도구 문서 설치](install-the-tools.md)되지만 하지 가정이 과정에서 정보를 아래에 나열 된 보다 최신 소프트웨어에서 찾을 수 있는 항목을 일치 완벽 하 게 합니다 .</span><span class="sxs-lookup"><span data-stu-id="06816-138">You are free to use the latest software, as listed within the [install the tools article](install-the-tools.md), though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="06816-139">다음 하드웨어 및 소프트웨어가이 과정에 대 한 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="06816-139">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="06816-140">개발 PC A [Windows Mixed Reality 호환](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 몰입 형 (VR) 헤드셋 개발용</span><span class="sxs-lookup"><span data-stu-id="06816-140">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="06816-141">Windows 10 Fall Creators Update (또는 이상) 사용 하도록 설정 하는 개발자 모드를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="06816-141">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="06816-142">최신 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="06816-142">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="06816-143">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="06816-143">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="06816-144">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="06816-144">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="06816-145">A [Windows Mixed Reality 몰입 형 (VR) 헤드셋](immersive-headset-hardware-details.md) 하거나 [Microsoft HoloLens](hololens-hardware-details.md) 개발자 모드를 설정 하 여</span><span class="sxs-lookup"><span data-stu-id="06816-145">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="06816-146">Azure 설정 및 ML 데이터 검색에 대 한 인터넷 액세스</span><span class="sxs-lookup"><span data-stu-id="06816-146">Internet access for Azure setup and ML data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="06816-147">시작하기 전 주의 사항</span><span class="sxs-lookup"><span data-stu-id="06816-147">Before you start</span></span>

<span data-ttu-id="06816-148">이 프로젝트를 구축 하는 문제 발생을 방지 하려면 것이 좋습니다 루트 또는 루트 거의 폴더에이 자습서에 언급 된 프로젝트를 만든 (오래 폴더 경로 빌드 시에는 문제가 발생할 수 있습니다).</span><span class="sxs-lookup"><span data-stu-id="06816-148">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 

## <a name="chapter-1---azure-storage-account-setup"></a><span data-ttu-id="06816-149">1 장-Azure Storage 계정 설정</span><span class="sxs-lookup"><span data-stu-id="06816-149">Chapter 1 - Azure Storage Account setup</span></span>

<span data-ttu-id="06816-150">Azure의 Translator API를 사용 하려면 응용 프로그램에 사용할 수 있도록 서비스의 인스턴스를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-150">To use the Azure Translator API, you will need to configure an instance of the service to be made available to your application.</span></span>
1.  <span data-ttu-id="06816-151">에 로그인 합니다 [Azure Portal](https://portal.azure.com)합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-151">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="06816-152">Azure 계정이 아직 없는 경우 새로 만들려면 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-152">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="06816-153">클래스 룸 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 새 계정 설정 도움말에 대 한 여력 중 하나를 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-153">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="06816-154">일단 로그인 하면 클릭할 **저장소 계정** 왼쪽된 메뉴에서.</span><span class="sxs-lookup"><span data-stu-id="06816-154">Once you are logged in, click on **Storage Accounts** in the left menu.</span></span>

    ![Azure Storage 계정 설정](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > <span data-ttu-id="06816-156">단어 **새로 만들기** 로 대체 되었습니다 **리소스 만들기**, 최신 포털에서입니다.</span><span class="sxs-lookup"><span data-stu-id="06816-156">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="06816-157">에 **Storage 계정** 탭을 클릭 **추가**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-157">On the **Storage Accounts** tab, click on **Add**.</span></span>

    ![Azure Storage 계정 설정](images/AzureLabs-Lab7-2.png)

4.  <span data-ttu-id="06816-159">에 **Storage 계정 만들기** 패널:</span><span class="sxs-lookup"><span data-stu-id="06816-159">In the **Create Storage Account** panel:</span></span>

    1.  <span data-ttu-id="06816-160">삽입을 **이름을** 계정의 주의 숫자 및 소문자만이 필드를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-160">Insert a **Name** for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>
    2.  <span data-ttu-id="06816-161">에 대 한 **배포 모델** 선택 **Resource manager**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-161">For **Deployment model,** select **Resource manager**.</span></span>
    3.  <span data-ttu-id="06816-162">에 대 한 **계정 종류**를 선택 **저장소 (범용 v1)** 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-162">For **Account kind**, select **Storage (general purpose v1)**.</span></span>
    4.  <span data-ttu-id="06816-163">에 대 한 **성능**를 선택 **표준**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-163">For **Performance**, select **Standard**.</span></span>
    5.  <span data-ttu-id="06816-164">에 대 한 **복제** 선택 **읽기-액세스-지역 중복 저장소 (RA-GRS)** 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-164">For **Replication** select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>
    6.  <span data-ttu-id="06816-165">둡니다 **보안 전송 필요** 으로 **비활성**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-165">Leave **Secure transfer required** as **Disabled**.</span></span>
    7.  <span data-ttu-id="06816-166">선택 된 **구독**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-166">Select a **Subscription**.</span></span>
    4. <span data-ttu-id="06816-167">선택 된 **리소스 그룹** 하거나 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="06816-167">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="06816-168">리소스 그룹에는 모니터링, 프로 비전, 액세스 제어 및 Azure 자산 모음에 대 한 청구를 관리 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-168">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="06816-169">것이 좋습니다 (예: 이러한 labs)와 같은 일반적인 리소스 그룹에서 단일 프로젝트와 연결 된 모든 Azure 서비스를 유지).</span><span class="sxs-lookup"><span data-stu-id="06816-169">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="06816-170">추가 하려는 경우 Azure 리소스 그룹에 대 한 하세요 [리소스 그룹 방문해](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-170">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>
    
    5.  <span data-ttu-id="06816-171">확인 합니다 **위치** (새 리소스 그룹을 만들면) 하는 경우 리소스 그룹에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-171">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="06816-172">위치는 응용 프로그램은 실행할 지역의 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="06816-172">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="06816-173">일부 Azure 자산은 특정 지역 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06816-173">Some Azure assets are only available in certain regions.</span></span>

5.  <span data-ttu-id="06816-174">이 서비스에 적용 되는 조건에 이해는 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-174">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    ![Azure Storage 계정 설정](images/AzureLabs-Lab7-3.png)

6.  <span data-ttu-id="06816-176">클릭 한 후 **만들기**만들려는 서비스에 대 한 대기 해야, 1 분이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06816-176">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="06816-177">서비스 인스턴스가 생성 되 면 포털에서 알림이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06816-177">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure Storage 계정 설정](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio"></a><span data-ttu-id="06816-179">2 장-Azure Machine Learning Studio</span><span class="sxs-lookup"><span data-stu-id="06816-179">Chapter 2 - The Azure Machine Learning Studio</span></span>

<span data-ttu-id="06816-180">사용 하 여 *Azure Machine Learning*, 응용 프로그램에 사용할 수 있도록 Machine Learning 서비스의 인스턴스를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-180">To use the *Azure Machine Learning*, you will need to configure an instance of the Machine Learning service to be made available to your application.</span></span>

1.  <span data-ttu-id="06816-181">Azure 포털에서 클릭 **새로 만들기** 왼쪽 위에서 모서리 및 검색 **Machine Learning Studio 작업 영역**, 키를 눌러 **Enter**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-181">In the Azure Portal, click on **New** in the top left corner, and search for **Machine Learning Studio Workspace**, press **Enter**.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-5.png)

2.  <span data-ttu-id="06816-183">새 페이지에 대 한 설명을 제공 합니다는 **Machine Learning Studio 작업 영역** 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="06816-183">The new page will provide a description of the **Machine Learning Studio Workspace**  service.</span></span> <span data-ttu-id="06816-184">이 프롬프트의 왼쪽 아래에 있는 클릭 합니다 **만들기** 이 서비스를 사용 하 여 연결을 만들려면 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="06816-184">At the bottom left of this prompt, click the **Create** button, to create an association with this service.</span></span>

3.  <span data-ttu-id="06816-185">클릭 한 후 **Create**, 새 항목에 대 한 일부 세부 정보를 제공 해야 하는 패널이 나타납니다 **Machine Learning Studio 서비스**:</span><span class="sxs-lookup"><span data-stu-id="06816-185">Once you have clicked on **Create**, a panel will appear where you need to provide some details about your new **Machine Learning Studio service**:</span></span>

    1.  <span data-ttu-id="06816-186">원하는 삽입 **작업 영역 이름** 이 서비스 인스턴스에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-186">Insert your desired **Workspace name** for this service instance.</span></span>

    2.  <span data-ttu-id="06816-187">선택 된 **구독**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-187">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="06816-188">선택 된 **리소스 그룹** 하거나 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="06816-188">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="06816-189">리소스 그룹에는 모니터링, 프로 비전, 액세스 제어 및 Azure 자산 모음에 대 한 청구를 관리 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-189">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="06816-190">것이 좋습니다 (예: 이러한 labs)와 같은 일반적인 리소스 그룹에서 단일 프로젝트와 연결 된 모든 Azure 서비스를 유지).</span><span class="sxs-lookup"><span data-stu-id="06816-190">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="06816-191">추가 하려는 경우 Azure 리소스 그룹에 대 한 하세요 [리소스 그룹 방문해](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-191">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="06816-192">확인 합니다 **위치** (새 리소스 그룹을 만들면) 하는 경우 리소스 그룹에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-192">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="06816-193">위치는 응용 프로그램은 실행할 지역의 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="06816-193">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="06816-194">일부 Azure 자산은 특정 지역 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06816-194">Some Azure assets are only available in certain regions.</span></span> <span data-ttu-id="06816-195">이전 장에서 Azure Storage를 만드는 데는 동일한 리소스 그룹을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-195">You should use the same resource group that you used for creating the Azure Storage in the previous Chapter.</span></span>

    5.  <span data-ttu-id="06816-196">에 대 한는 **저장소 계정** 섹션에서 **기존 항목 사용**, 한 다음 드롭다운 메뉴를 클릭 하 고를 클릭 합니다 **저장소 계정** 마지막 단원에서 만든 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-196">For the **Storage account** section, click **Use existing**, then click the dropdown menu, and from there, click the **Storage Account** you created in the last Chapter.</span></span>

    6.  <span data-ttu-id="06816-197">적절 한 선택 **작업 영역 가격 책정 계층** 드롭다운 메뉴에서 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06816-197">Select the appropriate **Workspace pricing tier** for you, from the dropdown menu.</span></span>

    7.  <span data-ttu-id="06816-198">내 합니다 **웹 서비스 계획** 섹션에서 **만들기** **새** 다음 텍스트 필드에서 이름을 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-198">Within the **Web service plan** section, click **Create** **new,** then insert a name for it in the text field.</span></span>

    8.  <span data-ttu-id="06816-199">**웹 서비스 계획 가격 책정 계층** 섹션에서 사용자가 선택한 가격 계층을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-199">From the **Web service plan pricing tier** section, select the price tier of your choice.</span></span> <span data-ttu-id="06816-200">호출 계층 테스트 개발 **DEVTEST 표준** 무료로 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-200">A development testing tier called **DEVTEST Standard** should be available to you at no charge.</span></span>

    9.  <span data-ttu-id="06816-201">이 서비스에 적용 되는 조건에 이해는 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-201">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    10. <span data-ttu-id="06816-202">**만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-202">Click **Create**.</span></span>

        ![Azure Machine Learning Studio](images/AzureLabs-Lab7-6.png)

4.  <span data-ttu-id="06816-204">클릭 한 후 **만들기**만들려는 서비스에 대 한 대기 해야, 1 분이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06816-204">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

5.  <span data-ttu-id="06816-205">서비스 인스턴스가 생성 되 면 포털에서 알림이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06816-205">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-7.png)

6.  <span data-ttu-id="06816-207">새 서비스 인스턴스를 탐색 하려면 알림을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-207">Click on the notification to explore your new Service instance.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-8.png)

7.  <span data-ttu-id="06816-209">클릭 합니다 **리소스로 이동** 알림에서 새 서비스 인스턴스를 탐색 하는 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="06816-209">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span>

8.  <span data-ttu-id="06816-210">아래 표시 된 페이지에는 **추가 링크** 섹션에서 **Machine Learning Studio 시작**, 브라우저를 안내 하는 합니다 **Machine Learning Studio** 포털입니다.</span><span class="sxs-lookup"><span data-stu-id="06816-210">In the page displayed, under the **Additional Links** section, click **Launch Machine Learning Studio**, which will direct your browser to the **Machine Learning Studio** portal.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-9.png)

9.  <span data-ttu-id="06816-212">사용 된 **로그인** Machine Learning Studio에 로그인 할 가운데 또는 오른쪽 맨 위에 있는 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="06816-212">Use the **Sign In** button, at the top right or in the center, to log into your Machine Learning Studio.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-dataset-setup"></a><span data-ttu-id="06816-214">3 장-Machine Learning Studio: 데이터 집합 설정</span><span class="sxs-lookup"><span data-stu-id="06816-214">Chapter 3 - The Machine Learning Studio: Dataset setup</span></span>

<span data-ttu-id="06816-215">기계 학습 알고리즘 작동 방법 중 하나는 기존 데이터를 분석 하 고 미래의 결과 예측 하려고 기반으로 기존 데이터 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="06816-215">One of the ways Machine Learning algorithms work is by analyzing existing data and then attempting to predict future results based on the existing data set.</span></span> <span data-ttu-id="06816-216">일반적으로 즉 더 기존 데이터는 더 나은 알고리즘 될 미래의 결과 예측 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-216">This generally means that the more existing data you have, the better the algorithm will be at predicting future results.</span></span>

<span data-ttu-id="06816-217">샘플 테이블은 지정 된이 과정에 대 한 호출 [ProductsTableCSV에서 다운로드할 수 있습니다 및](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip)합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-217">A sample table is provided to you, for this course, called [ProductsTableCSV and can be downloaded here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="06816-218">위의.zip 파일은 모두 포함 된 **ProductsTableCSV** 및 **.unitypackage**에서 해야 하는 [6 장](#chapter-6---importing-the-mlproducts-unity-package)합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-218">The above .zip file contains both the **ProductsTableCSV** and the **.unitypackage**, which you will need in [Chapter 6](#chapter-6---importing-the-mlproducts-unity-package).</span></span> <span data-ttu-id="06816-219">별도 csv 파일에 있지만 해당 장 내에서이 패키지도 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06816-219">This package is also provided within that Chapter, though separate to the csv file.</span></span>

<span data-ttu-id="06816-220">이 샘플 데이터 집합의 2017 년의 매일 매시간 베스트 셀러 개체의 레코드를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-220">This sample data set contains a record of the best-selling objects at every hour of each day of the year 2017.</span></span>
        
![Machine Learning Studio: 데이터 집합 설정](images/AzureLabs-Lab7-11.png)

<span data-ttu-id="06816-222">예를 들어, 2017의 첫째 날 (13 시간), 오후 1 시의 베스트 셀러 항목이 솔트 및 고추를 각각 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="06816-222">For example, on day 1 of 2017, at 1pm (hour 13), the best-selling item was salt and pepper.</span></span>

<span data-ttu-id="06816-223">이 샘플 테이블 9998 항목을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-223">This sample table contains 9998 entries.</span></span>

1.  <span data-ttu-id="06816-224">다시 이동 합니다 **Machine Learning Studio** 포털이이 테이블을 추가 하 고는 **데이터 집합** 에 기계 학습에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-224">Head back to the **Machine Learning Studio** portal, and add this table as a **Dataset** for your ML.</span></span> <span data-ttu-id="06816-225">클릭 하 여이 작업을 수행 합니다 **+ 새로 만들기** 화면의 왼쪽된 아래 모퉁이의 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="06816-225">Do this by clicking the **+ New** button in the bottom left corner of the screen.</span></span>

    ![Machine Learning Studio: 데이터 집합 설정](images/AzureLabs-Lab7-12.png)

2.  <span data-ttu-id="06816-227">섹션은 표시 맨 아래에서 내에서 왼쪽 탐색 패널 인지.</span><span class="sxs-lookup"><span data-stu-id="06816-227">A section will come up from the bottom, and within that there is navigation panel on the left.</span></span> <span data-ttu-id="06816-228">클릭 **데이터 집합**, 다음, 오른쪽 **로컬 파일에서**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-228">Click **Dataset**, then to the right of that, **From Local File**.</span></span>

    ![Machine Learning Studio: 데이터 집합 설정](images/AzureLabs-Lab7-13.png)

3.  <span data-ttu-id="06816-230">새 업로드 **데이터 집합** 이러한 단계에 따라:</span><span class="sxs-lookup"><span data-stu-id="06816-230">Upload the new **Dataset** by following these steps:</span></span>

    1. <span data-ttu-id="06816-231">수행할 수 있는 업로드 창이 표시 됩니다 **찾아보기** 새 데이터 집합에 대 한 하드 드라이브입니다.</span><span class="sxs-lookup"><span data-stu-id="06816-231">The upload window will appear, where you can **Browse** your hard drive for the new dataset.</span></span>

        ![Machine Learning Studio: 데이터 집합 설정](images/AzureLabs-Lab7-14.png)

    2.  <span data-ttu-id="06816-233">옵션을 선택 하 고 다시 업로드 창의 확인란을 선택 취소 상태로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="06816-233">Once selected, and back in the upload window, leave the checkbox unticked.</span></span>

    3.  <span data-ttu-id="06816-234">아래 텍스트 필드에 입력 **ProductsTableCSV.csv** 데이터 집합의 이름으로 (경우에 자동으로 추가).</span><span class="sxs-lookup"><span data-stu-id="06816-234">In the text field below, enter **ProductsTableCSV.csv** as the name for the dataset (though should automatically be added).</span></span>

    4.  <span data-ttu-id="06816-235">드롭다운 메뉴를 사용 하 여 **형식**를 선택 **일반 CSV 파일 (.csv) 헤더를 사용 하 여**입니다.</span><span class="sxs-lookup"><span data-stu-id="06816-235">Using the dropdown menu for **Type**, select **Generic CSV File with a header (.csv)**.</span></span>

    5.  <span data-ttu-id="06816-236">업로드 창의 오른쪽 아래에 있는 눈금을 눌러 및 **데이터 집합** 업로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06816-236">Press the tick in the bottom right of the upload window, and your **Dataset** will be uploaded.</span></span>

## <a name="chapter-4---the-machine-learning-studio-the-experiment"></a><span data-ttu-id="06816-237">4 장-Machine Learning Studio: 실험</span><span class="sxs-lookup"><span data-stu-id="06816-237">Chapter 4 - The Machine Learning Studio: The Experiment</span></span>

<span data-ttu-id="06816-238">기계 학습 시스템을 작성 하기 전에 데이터에 대 한 이론에 유효성을 검사 하는 실험 구축 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-238">Before you can build your machine learning system, you will need to build an experiment, to validate your theory about your data.</span></span> <span data-ttu-id="06816-239">결과 함께 더 많은 데이터를 해야 하는지 또는 가능한 결과 데이터 간에 상관 관계가 있는 경우를 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06816-239">With the results, you will know whether you need more data, or if there is no correlation between the data and a possible outcome.</span></span>

<span data-ttu-id="06816-240">실험 만들기 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-240">To start creating an experiment:</span></span>

1.  <span data-ttu-id="06816-241">다시 클릭 합니다 **+ 새로 만들기** 페이지의 맨 아래 왼쪽 단추 클릭 **실험** > **빈 실험**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-241">Click again on the **+ New** button on the bottom left of the page, then click on **Experiment** > **Blank Experiment**.</span></span>

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-15.png)

2.  <span data-ttu-id="06816-243">빈 실험을 사용 하 여 새 페이지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06816-243">A new page will be displayed with a blank Experiment:</span></span>

3.  <span data-ttu-id="06816-244">왼쪽 패널에서 확장 **저장 된 데이터 집합* > *내 데이터 집합** 끌어서 합니다 **ProductsTableCSV** 에 **실험 캔버스**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-244">From the panel on the left expand **Saved Datasets* > *My Datasets** and drag the  **ProductsTableCSV** on to the **Experiment Canvas**.</span></span>

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-16.png)

4.  <span data-ttu-id="06816-246">왼쪽 패널에서 확장 **데이터 변환** > **샘플 및 분할**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-246">In the panel on the left, expand **Data Transformation** > **Sample and Split**.</span></span> <span data-ttu-id="06816-247">놓습니다 합니다 **데이터 분할** 항목에 **실험 캔버스**.</span><span class="sxs-lookup"><span data-stu-id="06816-247">Then drag the **Split Data** item in to the **Experiment Canvas**.</span></span> <span data-ttu-id="06816-248">분할 데이터 항목에는 두 부분으로 데이터 집합 분할 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06816-248">The Split Data item will split the data set into two parts.</span></span> <span data-ttu-id="06816-249">일부 기계 학습 알고리즘을 학습에 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-249">One part you will use for training the machine learning algorithm.</span></span> <span data-ttu-id="06816-250">두 번째 파트를 생성 하는 알고리즘의 정확도를 평가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06816-250">The second part will be used to evaluate the accuracy of the algorithm generated.</span></span>

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-17.png)

5.  <span data-ttu-id="06816-252">(캔버스에서 항목이 선택 되는 데이터 분할) 하는 동안 오른쪽 창에서 편집 합니다 **첫 번째 출력 데이터 집합의 행 분수** 하 **0.7**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-252">In the right panel (while the Split Data item on the canvas is selected), edit the **Fraction of rows in the first output dataset** to **0.7**.</span></span> <span data-ttu-id="06816-253">이 두 부분으로 데이터 분할 첫 번째 부분은 데이터의 70% 되며 두 번째 부분은 나머지 30% 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06816-253">This will split the data into two parts, the first part will be 70% of the data, and the second part will be the remaining 30%.</span></span> <span data-ttu-id="06816-254">을 보장 하기 위해 데이터를 임의로 분할 됩니다 있는지를 확인 합니다 **무작위 분할** 확인란이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06816-254">To ensure that the data is split randomly, make sure the **Randomized split** checkbox remains checked.</span></span>

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-18.png)

6.  <span data-ttu-id="06816-256">하단에서 연결을 끌어 합니다 **ProductsTableCSV** 분할 데이터 항목의 맨 위에 캔버스의 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="06816-256">Drag a connection from the base of the **ProductsTableCSV** item on the canvas to the top of the Split Data item.</span></span> <span data-ttu-id="06816-257">이 항목을 연결 하 고 전송 됩니다 합니다 **ProductsTableCSV** 분할 데이터 입력 데이터 집합 출력 (데이터).</span><span class="sxs-lookup"><span data-stu-id="06816-257">This will connect the items and send the **ProductsTableCSV** dataset output (the data) to the Split Data input.</span></span>  

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-19.png)

7.  <span data-ttu-id="06816-259">에 **실험** 왼쪽 패널에서 확장 하 고 \**Machine Learning* > \* 학습 \* \* 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-259">In the **Experiments** panel on the left side, expand \**Machine Learning* > \*Train\*\*.</span></span> <span data-ttu-id="06816-260">끌기 합니다 **모델 학습** 을 실험 캔버스의 항목 축소 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-260">Drag the **Train Model** item out in to the Experiment canvas.</span></span> <span data-ttu-id="06816-261">캔버스와 동일 하 게 같아야 합니다 아래.</span><span class="sxs-lookup"><span data-stu-id="06816-261">Your canvas should look the same as the below.</span></span>

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-20.png)

8.  <span data-ttu-id="06816-263">***왼쪽 아래*** 의 **데이터 분할** 항목에 대 한 연결을 끌어 합니다 **오른쪽 위** 의 **모델 학습** 항목.</span><span class="sxs-lookup"><span data-stu-id="06816-263">From the ***bottom left*** of the **Split Data** item drag a connection to the **top right** of the **Train Model** item.</span></span> <span data-ttu-id="06816-264">데이터 집합에서 첫 번째 70% 분할 알고리즘을 학습에 학습 모델에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06816-264">The first 70% split from the dataset will be used by the Train Model to train the algorithm.</span></span>

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-21.png)

9.  <span data-ttu-id="06816-266">선택는 **모델 학습** 캔버스 및 항목은 **속성** 패널 (브라우저 창의 오른쪽) 클릭 합니다 **열 선택기 시작** 단추.</span><span class="sxs-lookup"><span data-stu-id="06816-266">Select the **Train Model** item on the canvas, and in the **Properties** panel (on the right-hand side of your browser window) click the **Launch column selector** button.</span></span>

10. <span data-ttu-id="06816-267">텍스트 상자에 입력 **제품** 누릅니다 **Enter**하십시오 *제품* 예측을 학습 하는 열으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06816-267">In the text box type **product** and then press **Enter**, *product* will be set as a column to train predictions.</span></span> <span data-ttu-id="06816-268">다음에 클릭 합니다 **눈금** 선택 대화 상자를 닫으려면 오른쪽 아래 모퉁이에서.</span><span class="sxs-lookup"><span data-stu-id="06816-268">Following this, click on the **tick** in the bottom-right corner to close the selection dialog.</span></span>

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-22.png)

11. <span data-ttu-id="06816-270">학습 하는 것을 **다중 클래스 로지스틱 회귀** 대부분의 판매를 예측 하는 알고리즘 **제품** 요일과 날짜의 시간에 따라 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-270">You are going to train a **Multiclass Logistic Regression** algorithm to predict the most sold **product** based on the hour of the day and the date.</span></span> <span data-ttu-id="06816-271">하지만 Azure Machine Learning studio에서 제공 되는 다양 한 알고리즘의 세부 정보를 설명 하기 위해이 문서의 범위를 벗어납니다 확인할 수 있습니다에서 더 많은 정보를 [Machine Learning 알고리즘 치트 시트](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)</span><span class="sxs-lookup"><span data-stu-id="06816-271">It is beyond the scope of this document to explain the details of the different algorithms provided by the Azure Machine Learning studio, though, you can find out more from the [Machine Learning Algorithm Cheat Sheet](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)</span></span>

12. <span data-ttu-id="06816-272">확장 왼쪽의 실험 항목 패널에서 \* \**Machine Learning* > *초기화 모델* > \* 분류 \* 및 끌어서는 **다중 클래스 로지스틱 회귀**  항목 실험 캔버스에 로그온 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-272">From the experiment items panel on the left, expand \*\**Machine Learning* > *Initialize Model* > \*Classification\*\*\*, and drag the **Multiclass Logistic Regression** item on to the experiment canvas.</span></span>

13. <span data-ttu-id="06816-273">아래쪽에서 출력을 연결 합니다 **다중 클래스 로지스틱 회귀**의 왼쪽 위 입력는 **모델 학습** 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="06816-273">Connect the output, from the bottom of the **Multiclass Logistic Regression**, to the top-left input of the **Train Model** item.</span></span>

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-23.png)

14. <span data-ttu-id="06816-275">왼쪽 패널에서 실험 항목의 목록에서 \**Machine Learning* > \* 점수 \* \*, 끌어서 합니다 **모델 점수 매기기** 캔버스에는 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="06816-275">In list of experiment items in the panel on the left, expand \**Machine Learning* > \*Score\*\*, and drag the **Score Model** item on to the canvas.</span></span>

15. <span data-ttu-id="06816-276">아래쪽에서 출력을 연결 합니다 **모델 학습**의 왼쪽 위 입력 합니다 **모델 점수 매기기**.</span><span class="sxs-lookup"><span data-stu-id="06816-276">Connect the output, from the bottom of the **Train Model**, to the top-left input of the **Score Model**.</span></span>

16. <span data-ttu-id="06816-277">오른쪽 아래 출력에 연결 **데이터 분할**의 오른쪽 입력 합니다  **모델 점수 매기기* 항목*합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-277">Connect the bottom-right output from **Split Data**, to the top-right input of the **Score Model* item*.</span></span>

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-24.png)

17. <span data-ttu-id="06816-279">목록의 **실험** 왼쪽 패널에서 항목을 확장할 \* \**Machine Learning* > \* 평가 \* 및 끌어서 합니다 **모델 평가** 캔버스로 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="06816-279">In the list of **Experiment** items in the panel on the left, expand \*\**Machine Learning* > \*Evaluate\*\*\*, and drag the **Evaluate Model** item onto the canvas.</span></span>

18. <span data-ttu-id="06816-280">출력을 연결 합니다 **모델 점수 매기기** 의 왼쪽 위 입력 합니다 **모델 평가**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-280">Connect the output from the **Score Model** to the top-left input of the **Evaluate Model**.</span></span>

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-25.png)

19. <span data-ttu-id="06816-282">첫 번째 Machine Learning 실험 구축 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06816-282">You have built your first Machine Learning Experiment.</span></span> <span data-ttu-id="06816-283">이제 저장 하 고 실험을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06816-283">You can now save and run the experiment.</span></span> <span data-ttu-id="06816-284">페이지의 맨 아래에 있는 메뉴를 클릭 합니다 **저장** 실험을 저장 한 다음 클릭 하려면 단추 **실행** 시작 실험으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-284">In the menu at the bottom of the page, click on the **Save** button to save your experiment and then click **Run** to the start the experiment.</span></span>

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-26.png)

20. <span data-ttu-id="06816-286">볼 수 있습니다 합니다 **상태** 실험 캔버스의 오른쪽 상단에에서 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06816-286">You can see the **status** of the experiment in the top-right of the canvas.</span></span> <span data-ttu-id="06816-287">완료 하는 실험에 대 일 분 정도 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="06816-287">Wait a few moments for the experiment to finish.</span></span>

    > <span data-ttu-id="06816-288">큰 (실제) 데이터 집합을 사용 하는 경우 가능성이 실험을 실행 하는 데 시간이 걸릴 수 있습니다는.</span><span class="sxs-lookup"><span data-stu-id="06816-288">If you have a big (real world) dataset it is likely that the experiment could take hours to run.</span></span>

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-27.png)

21. <span data-ttu-id="06816-290">마우스 오른쪽 단추로 클릭 합니다 **모델 평가** 캔버스 및 상황에 맞는 메뉴 가리키기를 통해 마우스 항목 **평가 결과**을 선택한 후 **시각화**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-290">Right click on the **Evaluate Model** item in the canvas and from the context menu hover the mouse over **Evaluation Results**, then select **Visualize**.</span></span>

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-28.png)

22. <span data-ttu-id="06816-292">실제 결과와 예측 된 결과 보여 주는 평가 결과 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06816-292">The evaluation results will be displayed showing the predicted outcomes versus the actual outcomes.</span></span> <span data-ttu-id="06816-293">이 모델을 평가 하는 것에 대 한 이전에 분할 된 원래 데이터 집합의 30%를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-293">This uses the 30% of the original dataset, that was split earlier, for evaluating the model.</span></span> <span data-ttu-id="06816-294">결과가 좋은 것이 가장 좋습니다 있습니다 번호가 가장 높은 각 행의 열에 강조 표시 된 항목 수를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06816-294">You can see the results are not great, ideally you would have the highest number in each row be the highlighted item in the columns.</span></span>

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-29.png)

23. <span data-ttu-id="06816-296">닫기 합니다 **결과**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-296">Close the **Results**.</span></span>

24. <span data-ttu-id="06816-297">로 노출 해야 새로 학습 된 기계 학습 모델을 사용 하는 **웹 서비스**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-297">To use your newly trained Machine Learning model you need to expose it as a **Web Service**.</span></span> <span data-ttu-id="06816-298">이 작업을 수행 하려면 클릭 합니다 **웹 서비스 설정** 메뉴 페이지의 맨 위에 있는 메뉴에서 항목을 클릭할 **예측 웹 서비스**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-298">To do this, click on the **Set Up Web Service** menu item in the menu at the bottom of the page, and click on **Predictive Web Service**.</span></span>

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-30.png)

25. <span data-ttu-id="06816-300">새 탭에서 만들어지고 학습 모델을 병합 된 새 웹 서비스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="06816-300">A new tab will be created, and the train model merged to create the new web service.</span></span> 

26. <span data-ttu-id="06816-301">페이지의 맨 위에 있는 메뉴에서 클릭 **저장할**, 클릭 **실행**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-301">In the menu at the bottom of the page click **Save**, then click **Run**.</span></span> <span data-ttu-id="06816-302">실험 캔버스의 오른쪽 위 모서리에서 업데이트 상태가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06816-302">You will see the status updated in the top-right corner of the experiment canvas.</span></span>

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-31.png)

27. <span data-ttu-id="06816-304">실행을 마친 후에 **웹 서비스 배포** 단추 페이지의 맨 아래에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06816-304">Once it has finished running, a **Deploy Web Service** button will appear at the bottom of the page.</span></span> <span data-ttu-id="06816-305">웹 서비스를 배포할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="06816-305">You are ready to deploy the web service.</span></span> <span data-ttu-id="06816-306">클릭 **웹 서비스 배포** 페이지의 맨 위에 있는 메뉴에서 (클래식).</span><span class="sxs-lookup"><span data-stu-id="06816-306">Click **Deploy Web Service** (Classic) in the menu at the bottom of the page.</span></span>

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-32.png)

    > <span data-ttu-id="06816-308">수행 해야 하는 팝업을 허용 하도록 브라우저 묻는 메시지가 나타납니다 **허용**되지만 키를 눌러야 **웹 서비스 배포** 다시 배포 페이지는 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="06816-308">Your browser may prompt to allow a pop-up, which you should **allow**, though you may need to press **Deploy Web Service** again, if the deploy page does not show.</span></span> 

28. <span data-ttu-id="06816-309">실험을 만든 후 리디렉션됩니다 하는 **대시보드** 가 있는 페이지에 **API 키** 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-309">Once the Experiment has been created you will be redirected to a **Dashboard** page where you will have your **API Key** displayed.</span></span> <span data-ttu-id="06816-310">잠시를 메모장에 복사해, 해야 코드에서 가능한 한 빨리 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-310">Copy it into a notepad for the moment, you will need it in your code very soon.</span></span> <span data-ttu-id="06816-311">API 키를 기록한 후 클릭 합니다 **요청/응답** 단추를 **기본 끝점** 키 아래의 섹션입니다.</span><span class="sxs-lookup"><span data-stu-id="06816-311">Once you have noted your API Key, click on the **REQUEST/RESPONSE** button in the **Default Endpoint** section underneath the Key.</span></span>

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > <span data-ttu-id="06816-313">이 페이지에서 테스트를 클릭 하면 입력된 데이터를 입력 하 고 출력을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06816-313">If you click Test in this page, you will be able to enter input data and view the output.</span></span> <span data-ttu-id="06816-314">입력 합니다 **하루** 하 고 **시간**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-314">Enter the **day** and **hour**.</span></span> <span data-ttu-id="06816-315">유지 된 **제품** 빈 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="06816-315">Leave the **product** entry blank.</span></span> <span data-ttu-id="06816-316">다음을 클릭 합니다 **확인** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="06816-316">Then click the **Confirm** button.</span></span> <span data-ttu-id="06816-317">페이지 아래쪽에서 출력 선택 되 고 각 제품의 가능성을 나타내는 JSON 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06816-317">The output on the bottom of the page will show the JSON representing the likelihood of each product being the choice.</span></span>

29. <span data-ttu-id="06816-318">새 웹 페이지를 열립니다, 지침 및 Machine Learning Studio에 필요한 요청 구조에 대 한 몇 가지 예제를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-318">A new web page will open up, displaying the instructions and some examples about the Request structure required by the Machine Learning Studio.</span></span> <span data-ttu-id="06816-319">복사 합니다 **요청 URI** 에 메모장에이 페이지에 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-319">Copy the **Request URI** displayed in this page, into your notepad.</span></span>

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-34.png)

<span data-ttu-id="06816-321">이제 빌드한 기계 학습 일 및 연도의 날의 시간을 사용 하 여 상관 관계가 지정 된 구매 기록 데이터를 기반으로 판매 될 가능성이 가장 높은 제품을 제공 하는 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="06816-321">You have now built a machine learning system that provides the most likely product to be sold based on historical purchasing data, correlated with the time of the day and day of the year.</span></span>

<span data-ttu-id="06816-322">웹 서비스를 호출 하려면 서비스 끝점 및 서비스에 대 한 API 키에 대 한 URL을 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-322">To call the web service, you will need the URL for the service endpoint and an API Key for the service.</span></span> <span data-ttu-id="06816-323">클릭 합니다 **사용** 위쪽 메뉴에서 탭 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-323">Click on the **Consume** tab, from the top menu.</span></span>

<span data-ttu-id="06816-324">합니다 **소비** 정보 페이지 코드에서 웹 서비스를 호출 해야 하는 정보에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06816-324">The **Consumption** Info page will display the information you will need to call the web service from your code.</span></span> <span data-ttu-id="06816-325">복사본을 만듭니다는 **기본 키** 하며 **요청-응답** URL입니다.</span><span class="sxs-lookup"><span data-stu-id="06816-325">Take a copy of the **Primary Key** and the **Request-Response** URL.</span></span> <span data-ttu-id="06816-326">다음 장에서 이러한 보고 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-326">You will need these in the next Chapter.</span></span>

## <a name="chapter-5---setting-up-the-unity-project"></a><span data-ttu-id="06816-327">5 장-Unity 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="06816-327">Chapter 5 - Setting up the Unity Project</span></span>

<span data-ttu-id="06816-328">설정 하 고 혼합 현실 몰입 형 헤드셋을 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-328">Set up and test your Mixed Reality Immersive Headset.</span></span>

> [!NOTE]
>  <span data-ttu-id="06816-329">해야 **되지** 이 과정에 대 한 동작 컨트롤러 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-329">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="06816-330">몰입 형 헤드셋 설정만 지원에 필요한 경우 클릭 하십시오 [여기](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-330">If you need support setting up the Immersive Headset, please click [HERE](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="06816-331">오픈 **Unity** 라는 새 Unity 프로젝트를 만들고 **MR\_MachineLearning 합니다.**</span><span class="sxs-lookup"><span data-stu-id="06816-331">Open **Unity** and create a new Unity Project called **MR\_MachineLearning.**</span></span> <span data-ttu-id="06816-332">프로젝트 형식 설정 되어 있는지 확인 **3D**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-332">Make sure the project type is set to **3D**.</span></span>

2.  <span data-ttu-id="06816-333">Unity 열기를 사용 하 여 기본 검사 가치가 **스크립트 편집기** 로 설정 된 **Visual Studio**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-333">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="06816-334">로 이동 ***편집할* > *기본 설정*** 로 이동한 다음 새 창에서 **외부 도구**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-334">Go to ***Edit* > *Preferences*** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="06816-335">변경 **외부 스크립트 편집기** 하 **Visual Studio 2017**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-335">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="06816-336">닫기 합니다 **기본 설정** 창입니다.</span><span class="sxs-lookup"><span data-stu-id="06816-336">Close the **Preferences** window.</span></span>

3.  <span data-ttu-id="06816-337">다음으로 이동 ***파일* > *빌드 설정*** 플랫폼 전환 **유니버설 Windows 플랫폼**를 클릭 하 여 합니다 ***플랫폼 전환*** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="06816-337">Next, go to ***File* > *Build Settings*** and switch the platform to **Universal Windows Platform**, by clicking on the ***Switch Platform*** button.</span></span>

4.  <span data-ttu-id="06816-338">또한 다음 사항을 확인 합니다</span><span class="sxs-lookup"><span data-stu-id="06816-338">Also make sure that:</span></span>

    1.  <span data-ttu-id="06816-339">**장치를 대상** 로 설정 된 **모든 장치**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-339">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="06816-340">Microsoft HoloLens 설정 **대상 장치** 하 *HoloLens*합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-340">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="06816-341">**빌드 형식** 로 설정 된 **D3D**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-341">**Build Type** is set to **D3D**.</span></span>

    3.  <span data-ttu-id="06816-342">**SDK** 로 설정 된 **가장 최근에 설치 된**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-342">**SDK** is set to **Latest installed**.</span></span>

    4.  <span data-ttu-id="06816-343">**Visual Studio 버전** 로 설정 된 **가장 최근에 설치 된**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-343">**Visual Studio Version** is set to **Latest installed**.</span></span>

    5.  <span data-ttu-id="06816-344">**빌드 및 실행** 로 설정 된 **로컬 컴퓨터**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-344">**Build and Run** is set to **Local Machine**.</span></span>

    6.  <span data-ttu-id="06816-345">설정에 대 한 걱정 하지 마십시오 **장면** 지금은 이러한 나중에 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06816-345">Do not worry about setting up **Scenes** right now, as these are provided later.</span></span>

    7.  <span data-ttu-id="06816-346">이제 나머지 설정은 기본값으로 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06816-346">The remaining settings should be left as default for now.</span></span>

        ![Unity 프로젝트 설정](images/AzureLabs-Lab7-35.png)

5.  <span data-ttu-id="06816-348">에 **빌드 설정** 창을 **플레이어 설정** 단추를 공간에 관련 된 패널이 열립니다이 위치를 **검사기** 위치한.</span><span class="sxs-lookup"><span data-stu-id="06816-348">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span> 

6. <span data-ttu-id="06816-349">이 패널에서 몇 가지 설정을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-349">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="06816-350">에 **기타 설정** 탭:</span><span class="sxs-lookup"><span data-stu-id="06816-350">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="06816-351">**스크립팅** **런타임 버전이** 있어야 **실험적** (.NET 4.6 동등)</span><span class="sxs-lookup"><span data-stu-id="06816-351">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent)</span></span>

        2. <span data-ttu-id="06816-352">**백 엔드를 스크립팅** 있어야 ***.NET***</span><span class="sxs-lookup"><span data-stu-id="06816-352">**Scripting Backend** should be ***.NET***</span></span>

        3. <span data-ttu-id="06816-353">**API 호환성 수준** 있어야 **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="06816-353">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Unity 프로젝트 설정](images/AzureLabs-Lab7-36.png)

    2.  <span data-ttu-id="06816-355">내 합니다 **게시 설정** 탭의 **기능**, 확인:</span><span class="sxs-lookup"><span data-stu-id="06816-355">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="06816-356">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="06816-356">**InternetClient**</span></span>

            ![Unity 프로젝트 설정](images/AzureLabs-Lab7-37.png)

    3.  <span data-ttu-id="06816-358">패널을 아래쪽의 **xr 하이 설정을** (아래에서 확인할 **게시 설정**), 눈금 **가상 현실 지원**, 있는지는 **Windows Mixed Reality SDK**  추가</span><span class="sxs-lookup"><span data-stu-id="06816-358">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added</span></span>

        ![Unity 프로젝트 설정](images/AzureLabs-Lab7-38.png)

    

6.  <span data-ttu-id="06816-360">년대 **빌드 설정** *Unity C#*  프로젝트는 더 이상 회색으로;이 옆의 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-360">Back in **Build Settings** *Unity C#* Projects is no longer greyed out; tick the checkbox next to this.</span></span> 

7.  <span data-ttu-id="06816-361">빌드 설정 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="06816-361">Close the Build Settings window.</span></span>

8.  <span data-ttu-id="06816-362">프로젝트를 저장 합니다 (**파일 > 프로젝트 저장**).</span><span class="sxs-lookup"><span data-stu-id="06816-362">Save your Project (**FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a><span data-ttu-id="06816-363">6 장-MLProducts Unity 패키지 가져오기</span><span class="sxs-lookup"><span data-stu-id="06816-363">Chapter 6 - Importing the MLProducts Unity Package</span></span>

<span data-ttu-id="06816-364">이 과정에 대 한 호출 Unity 자산 패키지를 다운로드 해야 합니다 [ **Azure-MR-307.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage)합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-364">For this course, you will need to download a Unity Asset Package called [**Azure-MR-307.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage).</span></span> <span data-ttu-id="06816-365">이 패키지의 모든 개체를 사용 하 여 장면으로 전체 제공 되는 미리 작성 된, 따라서 가져오는 모든 작업에 집중할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06816-365">This package comes complete with a scene, with all objects in that prebuilt, so you can focus on getting it all working.</span></span> <span data-ttu-id="06816-366">합니다 **ShelfKeeper** 스크립트를 제공 하지만 장면 설치 구조 목적으로 공용 변수를 요소만 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-366">The **ShelfKeeper** script is provided, though only holds the public variables, for the purpose of scene setup structure.</span></span> <span data-ttu-id="06816-367">다른 모든 섹션을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-367">You will need to do all other sections.</span></span> 

<span data-ttu-id="06816-368">이 패키지를 가져오려면:</span><span class="sxs-lookup"><span data-stu-id="06816-368">To import this package:</span></span>

1.  <span data-ttu-id="06816-369">사용자 앞에 Unity 대시보드를 클릭 **자산** 화면의 맨 위에 있는 메뉴에서 클릭 **패키지 가져오기, 사용자 지정 패키지**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-369">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package, Custom Package**.</span></span>

    ![MLProducts Unity 패키지 가져오기](images/AzureLabs-Lab7-39.png)

2.  <span data-ttu-id="06816-371">파일 선택기를 사용 하 여 선택 하는 **Azure-MR-307.unitypackage** 패키징하고 클릭 **열기**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-371">Use the file picker to select the **Azure-MR-307.unitypackage** package and click **Open**.</span></span>

3.  <span data-ttu-id="06816-372">이 자산에 대 한 구성 요소 목록에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="06816-372">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="06816-373">가져오기를 클릭 하 여 확인 **가져올**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-373">Confirm the import by clicking **Import**.</span></span>

    ![MLProducts Unity 패키지 가져오기](images/AzureLabs-Lab7-40.png)

4.  <span data-ttu-id="06816-375">이 가져오기 완료 되 면 Unity에서 새 폴더를 몇가 나타나는 알 수 있습니다 **프로젝트 패널**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-375">Once it has finished importing, you will notice that some new folders have appeared in your Unity **Project Panel**.</span></span> <span data-ttu-id="06816-376">이러한은 3D 모델 및 해당 하는 작업을 미리 만든 장면에 포함 된 자료입니다.</span><span class="sxs-lookup"><span data-stu-id="06816-376">Those are the 3D models and the respective materials that are part of the pre-made scene you will work on.</span></span> <span data-ttu-id="06816-377">이 과정에서 대부분의 코드를 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-377">You will write the majority of the code in this course.</span></span>

    ![MLProducts Unity 패키지 가져오기](images/AzureLabs-Lab7-41.png)

5.  <span data-ttu-id="06816-379">내에서 **프로젝트 패널** 폴더를 클릭 합니다 **장면** 내부 장면에 폴더를 두 번 클릭 (호출 **MR_MachineLearningScene**).</span><span class="sxs-lookup"><span data-stu-id="06816-379">Within the **Project Panel** folder, click on the **Scenes** folder and double click on the scene inside (called **MR_MachineLearningScene**).</span></span> <span data-ttu-id="06816-380">장면이 열립니다 (아래 이미지 참조).</span><span class="sxs-lookup"><span data-stu-id="06816-380">The scene will open (see image below).</span></span> <span data-ttu-id="06816-381">빨간색 다이아몬드 누락 된 경우 클릭할를 **Gizmo** 맨 위에 있는 단추를 오른쪽에 **게임 패널**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-381">If the red diamonds are missing, simply click the **Gizmos** button, at the top right of the **Game Panel**.</span></span>

    ![MLProducts Unity 패키지 가져오기](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a><span data-ttu-id="06816-383">7 장-Unity에서 Dll을 검사</span><span class="sxs-lookup"><span data-stu-id="06816-383">Chapter 7 - Checking the DLLs in Unity</span></span>

<span data-ttu-id="06816-384">(직렬화 및 역직렬화에 대 한 사용) 하는 JSON 라이브러리의 사용을 활용 하려면 Newtonsoft DLL에서 가져온 패키지를 사용 하 여 구현 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="06816-384">To leverage the use of JSON libraries (used for serializing and deserializing), a Newtonsoft DLL has been implemented with the package you brought in.</span></span> <span data-ttu-id="06816-385">라이브러리는 것이 좋습니다 (특히 경우 작동 하지 않는 코드를 사용 하 여 문제가 있는)를 확인 하지만 올바른 구성이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-385">The library should have the correct configuration, though it is worth checking (particularly if you are having issues with code not working).</span></span> 

<span data-ttu-id="06816-386">이를 수행하려면:</span><span class="sxs-lookup"><span data-stu-id="06816-386">To do so:</span></span>

-  <span data-ttu-id="06816-387">플러그 인 폴더 안에 Newtonsoft 파일에서 마우스 왼쪽 단추로 클릭 하 고 확인 합니다 **검사기 패널**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-387">Left-click on the Newtonsoft file inside the Plugins folder and look at the **Inspector panel**.</span></span> <span data-ttu-id="06816-388">했는지 **Any 플랫폼** 선택 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06816-388">Make sure **Any Platform** is ticked.</span></span> <span data-ttu-id="06816-389">로 이동 합니다 **UWP 탭** 하 고 **처리 하지** 선택 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06816-389">Go to the **UWP tab** and also ensure **Don't process** is ticked.</span></span>

    ![Unity에서 Dll 가져오기](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a><span data-ttu-id="06816-391">8-장 ShelfKeeper 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="06816-391">Chapter 8 - Create the ShelfKeeper class</span></span>

<span data-ttu-id="06816-392">합니다 **ShelfKeeper** UI 및 장면에서 생성 되는 제품을 제어 하는 메서드를 호스트 하는 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="06816-392">The **ShelfKeeper** class hosts methods that control the UI and products spawned in the scene.</span></span>

<span data-ttu-id="06816-393">가져온된 패키지의 일부로, 됩니다 받은이 클래스 있지만 완전 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="06816-393">As part of the imported package, you will have been given this class, though it is incomplete.</span></span> <span data-ttu-id="06816-394">해당 클래스를 완료 하려면 시간이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06816-394">It is now time to complete that class:</span></span>

1.  <span data-ttu-id="06816-395">두 번 클릭 합니다 **ShelfKeeper** 스크립트 내 합니다 **스크립트** 폴더를 사용 하 여 열고 **Visual Studio 2017**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-395">Double click on the **ShelfKeeper** script, within the **Scripts** folder, to open it with **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="06816-396">날짜 및 시간을 설정 하 고 제품을 표시 하는 메서드를 다음 코드를 사용 하 여 스크립트에 모든 코드를 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-396">Replace all the code existing in the script with the following code, which sets the time and date and has a method to show a product.</span></span>

    ```csharp
    using UnityEngine;

    public class ShelfKeeper : MonoBehaviour
    {
        /// <summary>
        /// Provides this class Singleton-like behavior
        /// </summary>
        public static ShelfKeeper instance;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for data
        /// </summary>
        public TextMesh dateText;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for time
        /// </summary>
        public TextMesh timeText;

        /// <summary>
        /// Provides references to the spawn locations for the products prefabs
        /// </summary>
        public Transform[] spawnPoint;

        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Set the text of the date in the scene
        /// </summary>
        public void SetDate(string day, string month)
        {
            dateText.text = day + " " + month;
        }

        /// <summary>
        /// Set the text of the time in the scene
        /// </summary>
        public void SetTime(string hour)
        {
            timeText.text = hour + ":00";
        }

        /// <summary>
        /// Spawn a product on the shelf by providing the name and selling grade
        /// </summary>
        /// <param name="name"></param>
        /// <param name="sellingGrade">0 being the best seller</param>
        public void SpawnProduct(string name, int sellingGrade)
        {
            Instantiate(Resources.Load(name),
                spawnPoint[sellingGrade].transform.position, spawnPoint[sellingGrade].transform.rotation);
        }
    }
    ```

3.  <span data-ttu-id="06816-397">변경 내용을 저장 해야 **Visual Studio** 를 반환 하기 전에 **Unity**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-397">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

4.  <span data-ttu-id="06816-398">다시 Unity 편집기에서 있는지 여부를 확인 합니다 **ShelfKeeper** 같습니다 클래스는 아래:</span><span class="sxs-lookup"><span data-stu-id="06816-398">Back in the Unity Editor, check that the **ShelfKeeper** class looks like the below:</span></span>

    ![ShelfKeeper 클래스 만들기](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > <span data-ttu-id="06816-400">스크립트 참조 대상이 없으면 (즉, *(텍스트 메시) 날짜*), 해당 개체를 끌어다 놓기만 하면 됩니다 합니다 **계층 패널**, 대상 필드에 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-400">If your script does not have the reference targets (i.e. *Date (Text Mesh)*), simply drag the corresponding objects from the **Hierarchy Panel**, into the target fields.</span></span> <span data-ttu-id="06816-401">필요한 경우 아래에 대 한 설명을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-401">See below for explanation, if needed:</span></span>
    > 
    > 1.  <span data-ttu-id="06816-402">열기는 **Spawn 지점** 내에서 배열 합니다 **ShelfKeeper** 왼쪽 스크립트 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="06816-402">Open the **Spawn Point** array within the **ShelfKeeper** component script by left-clicking it.</span></span> <span data-ttu-id="06816-403">하위 섹션이 호출 나타납니다 **크기**, 배열의 크기를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="06816-403">A sub-section will appear called **Size**, which indicates the size of the array.</span></span> <span data-ttu-id="06816-404">형식 **3** 옆에 텍스트 상자에 **크기** 누릅니다 **Enter**, 3 개의 슬롯 아래에 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06816-404">Type **3** into the textbox next to **Size** and press **Enter**, and three slots will be created beneath.</span></span>
    > 2. <span data-ttu-id="06816-405">내 합니다 **계층** 확장을 **시간 표시** 개체 (그 옆에 있는 화살표 왼쪽 단추 클릭).</span><span class="sxs-lookup"><span data-stu-id="06816-405">Within the **Hierarchy** expand the **Time Display** object (by left-clicking the arrow beside it).</span></span> <span data-ttu-id="06816-406">클릭 합니다 ***주 카메라*** 내에서 **계층**되도록를 **검사기** 해당 정보를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="06816-406">Next click the ***Main Camera*** from within the **Hierarchy**, so that the **Inspector** shows its information.</span></span>
    > 3. <span data-ttu-id="06816-407">선택 된 **주 카메라** 에 **계층 패널**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-407">Select the **Main Camera** in the **Hierarchy Panel**.</span></span> <span data-ttu-id="06816-408">끌기 합니다 **날짜** 및 **시간** 에서 개체를 **계층 패널** 에 **날짜 텍스트** 및 **시간 텍스트** 내 슬롯 합니다 **검사기** 의 **주 카메라** 에 **ShelfKeeper** 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="06816-408">Drag the **Date** and **Time** objects from the **Hierarchy Panel** to the **Date Text** and **Time Text** slots within the **Inspector** of the **Main Camera** in the **ShelfKeeper** component.</span></span>
    > 4. <span data-ttu-id="06816-409">끌어서를 **생성 포인트** 에서 **계층 패널** (아래에 *선반* 개체)에 **3** **요소**아래에 있는 대상 참조를 **Spawn 지점** 이미지와 같이 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="06816-409">Drag the **Spawn Points** from the **Hierarchy Panel** (beneath the *Shelf* object) to the **3** **Element** reference targets beneath the **Spawn Point** array, as shown in the image.</span></span>
    > 
    >     ![ShelfKeeper 클래스 만들기](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a><span data-ttu-id="06816-411">9-장 ProductPrediction 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="06816-411">Chapter 9 - Create the ProductPrediction class</span></span>

<span data-ttu-id="06816-412">다음 클래스를 만드는 것은 **ProductPrediction** 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="06816-412">The next class you are going to create is the **ProductPrediction** class.</span></span>

<span data-ttu-id="06816-413">이 클래스는 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-413">This class is responsible for:</span></span>

-   <span data-ttu-id="06816-414">쿼리는 **Machine Learning 서비스** 인스턴스를 현재 날짜 및 시간을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-414">Querying the **Machine Learning Service** instance, providing the current date and time.</span></span>

-   <span data-ttu-id="06816-415">사용 가능한 데이터를 JSON 응답을 역직렬화 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-415">Deserializing the JSON response into usable data.</span></span>

-   <span data-ttu-id="06816-416">3 개의 권장 되는 제품을 검색 하 고 데이터를 해석 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-416">Interpreting the data, retrieving the 3 recommended products.</span></span>

-   <span data-ttu-id="06816-417">호출 된 **ShelfKeeper** 장면에서 데이터를 표시 하는 메서드를 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="06816-417">Calling the **ShelfKeeper** class methods to display the data in the Scene.</span></span>

<span data-ttu-id="06816-418">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="06816-418">To create this class:</span></span>

1.  <span data-ttu-id="06816-419">로 이동 합니다 **스크립트** 폴더에서 합니다 **프로젝트 패널**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-419">Go to the **Scripts** folder, in the **Project Panel**.</span></span>

2.  <span data-ttu-id="06816-420">폴더를 마우스 오른쪽 단추로 클릭 **Create** > **C\# 스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-420">Right-click inside the folder, **Create** > **C\# Script**.</span></span> <span data-ttu-id="06816-421">스크립트를 호출할 **ProductPrediction**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-421">Call the script **ProductPrediction**.</span></span>

3.  <span data-ttu-id="06816-422">두 번 클릭 하 여 새 **ProductPrediction** 스크립트를 사용 하 여 열고 **Visual Studio 2017**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-422">Double click on the new **ProductPrediction** script to open it with **Visual Studio 2017**.</span></span>

4.  <span data-ttu-id="06816-423">경우는 **파일 수정 감지** 대화 상자를 팝업에 클릭 \***솔루션 다시 로드**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-423">If the **File Modification Detected** dialog pops up, click \***Reload Solution**.</span></span>

5.  <span data-ttu-id="06816-424">ProductPrediction 클래스의 맨 위에 다음 네임 스페이스를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-424">Add the following namespaces to the top of the ProductPrediction class:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using System.Linq;
    using Newtonsoft.Json;
    using UnityEngine.Networking;
    using System.Runtime.Serialization;
    using System.Collections;
    ```

6.  <span data-ttu-id="06816-425">내 합니다 **ProductPrediction** 클래스 중첩된 클래스의 여러 서비스로 구성 되는 다음 두 항목을 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-425">Inside the **ProductPrediction** class insert the following two objects which are composed of a number of nested classes.</span></span> <span data-ttu-id="06816-426">이러한 클래스는 serialize 및 Machine Learning 서비스에 대 한 JSON을 deserialize 할 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06816-426">These classes are used to serialize and deserialize the JSON for the Machine Learning Service.</span></span>

    ```csharp
        /// <summary>
        /// This object represents the Prediction request
        /// It host the day of the year and hour of the day
        /// The product must be left blank when serialising
        /// </summary>
        public class RootObject
        {
            public Inputs Inputs { get; set; }
        }

        public class Inputs
        {
            public Input1 input1 { get; set; }
        }

        public class Input1
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

    ```csharp
        /// <summary>
        /// This object containing the deserialised Prediction result
        /// It host the list of the products
        /// and the likelihood of them being sold at current date and time
        /// </summary>
        public class Prediction
        {
            public Results Results { get; set; }
        }

        public class Results
        {
            public Output1 output1;
        }

        public class Output1
        {
            public string type;
            public Value value;
        }

        public class Value
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

7.  <span data-ttu-id="06816-427">다음 (있도록 JSON으로 보내고 다른 모든 코드를 아래 스크립트의 맨 아래에서 코드는 관련) 앞의 코드 위에 다음 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-427">Then add the following variables above the previous code (so that the JSON related code is at the bottom of the script, below all other code, and out of the way):</span></span>

    ```csharp
        /// <summary>
        /// The 'Primary Key' from your Machine Learning Portal
        /// </summary>
        private string authKey = "-- Insert your service authentication key here --";

        /// <summary>
        /// The 'Request-Response' Service Endpoint from your Machine Learning Portal
        /// </summary>
        private string serviceEndpoint = "-- Insert your service endpoint here --";

        /// <summary>
        /// The Hour as set in Windows
        /// </summary>
        private string thisHour;

        /// <summary>
        /// The Day, as set in Windows
        /// </summary>
        private string thisDay;

        /// <summary>
        /// The Month, as set in Windows
        /// </summary>
        private string thisMonth;

        /// <summary>
        /// The Numeric Day from current Date Conversion
        /// </summary>
        private string dayOfTheYear;

        /// <summary>
        /// Dictionary for holding the first (or default) provided prediction 
        /// from the Machine Learning Experiment
        /// </summary>    
        private Dictionary<string, string> predictionDictionary;

        /// <summary>
        /// List for holding product prediction with name and scores
        /// </summary>
        private List<KeyValuePair<string, double>> keyValueList;
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="06816-428">삽입 해야 합니다 **기본 키** 하 고 **요청-응답 끝점**, Machine Learning 포털 변수에 여기에서.</span><span class="sxs-lookup"><span data-stu-id="06816-428">Make sure to insert the **primary key** and **request-response endpoint**, from the Machine Learning Portal, into the variables here.</span></span> <span data-ttu-id="06816-429">아래 이미지는 수행 여기서 키 및 끝점을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-429">The below images show where you would have taken the key and endpoint from.</span></span> 
    >  
    > ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-53-1.png)
    >
    > ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-53-2.png)

8.  <span data-ttu-id="06816-432">내에서이 코드를 삽입 합니다 **start ()** 메서드.</span><span class="sxs-lookup"><span data-stu-id="06816-432">Insert this code within the **Start()** method.</span></span> <span data-ttu-id="06816-433">합니다 **start ()** 메서드는 클래스를 초기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-433">The **Start()** method is called when the class initializes:</span></span>

    ```csharp
        void Start()
        {
            // Call to get the current date and time as set in Windows
            GetTodayDateAndTime();

            // Call to set the HOUR in the UI
            ShelfKeeper.instance.SetTime(thisHour);

            // Call to set the DATE in the UI
            ShelfKeeper.instance.SetDate(thisDay, thisMonth);

            // Run the method to Get Predication from Azure Machine Learning
            StartCoroutine(GetPrediction(thisHour, dayOfTheYear));
        }
    ```

9.  <span data-ttu-id="06816-434">다음은 Windows에서 날짜 및 시간을 수집 하 고 Machine Learning 실험 사용 하 여 테이블에 저장 된 데이터를 사용 하 여 비교할 수 있는 형식으로 변환 하는 메서드.</span><span class="sxs-lookup"><span data-stu-id="06816-434">The following is the method that collects the date and time from Windows and converts it into a format that our Machine Learning Experiment can use to compare with the data stored in the table.</span></span>

    ```csharp
        /// <summary>
        /// Get current date and hour
        /// </summary>
        private void GetTodayDateAndTime()
        {
            // Get today date and time
            DateTime todayDate = DateTime.Now;

            // Extrapolate the HOUR
            thisHour = todayDate.Hour.ToString();

            // Extrapolate the DATE
            thisDay = todayDate.Day.ToString();
            thisMonth = todayDate.ToString("MMM");

            // Extrapolate the day of the year
            dayOfTheYear = todayDate.DayOfYear.ToString();
        }
    ```

10. <span data-ttu-id="06816-435">할 수 있습니다 **삭제할** 는 **update ()** 이 클래스는 사용 하지 않으므로 메서드.</span><span class="sxs-lookup"><span data-stu-id="06816-435">You can **delete** the **Update()** method since this class will not use it.</span></span>

11. <span data-ttu-id="06816-436">JSON 형식의 응답을 수신 하 고 현재 날짜 및 시간 Machine Learning 끝점을 통신에 다음 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-436">Add the following method which will communicate the current date and time to the Machine Learning endpoint and receive a response in JSON format.</span></span>

    ```csharp
        private IEnumerator GetPrediction(string timeOfDay, string dayOfYear)
        {
            // Populate the request object 
            // Using current day of the year and hour of the day
            RootObject ro = new RootObject
            {
                Inputs = new Inputs
                {
                    input1 = new Input1
                    {
                        ColumnNames = new List<string>
                        {
                            "day",
                            "hour",
                        "product"
                        },
                        Values = new List<List<string>>()
                    }
                }
            };

            List<string> l = new List<string>
            {
                dayOfYear,
                timeOfDay,
                ""
            };

            ro.Inputs.input1.Values.Add(l);

            Debug.LogFormat("Score request built");

            // Serialise the request
            string json = JsonConvert.SerializeObject(ro);

            using (UnityWebRequest www = UnityWebRequest.Post(serviceEndpoint, "POST"))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(json);
                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + authKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.SetRequestHeader("Accept", "application/json");

                yield return www.SendWebRequest();
                string response = www.downloadHandler.text;

                // Deserialize the response
                DataContractSerializer serializer;
                serializer = new DataContractSerializer(typeof(string));
                DeserialiseJsonResponse(response);
            }
        }
    ```

12. <span data-ttu-id="06816-437">JSON 응답을 역직렬화 하 고 역직렬화 하의 결과 통신을 담당 하는 다음 메서드를 추가 합니다 **ShelfKeeper** 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="06816-437">Add the following method, which is responsible for deserializing the JSON response, and communicating the result of the deserialization to the **ShelfKeeper** class.</span></span> <span data-ttu-id="06816-438">이 결과 현재 날짜 및 시간에 가장 많이 판매를 예측 하는 세 가지 항목의 이름이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06816-438">This result will be the names of the three items predicted to sell the most at current date and time.</span></span> <span data-ttu-id="06816-439">아래 코드를 삽입 합니다 **ProductPrediction** 이전 메서드 아래 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="06816-439">Insert the code below into the **ProductPrediction** class, below the previous method.</span></span>

    ```csharp
        /// <summary>
        /// Deserialize the response received from the Machine Learning portal
        /// </summary>
        public void DeserialiseJsonResponse(string jsonResponse)
        {
            // Deserialize JSON
            Prediction prediction = JsonConvert.DeserializeObject<Prediction>(jsonResponse);
            predictionDictionary = new Dictionary<string, string>();

            for (int i = 0; i < prediction.Results.output1.value.ColumnNames.Count; i++)
            {
                if (prediction.Results.output1.value.Values[0][i] != null)
                {
                    predictionDictionary.Add(prediction.Results.output1.value.ColumnNames[i], prediction.Results.output1.value.Values[0][i]);
                }
            }

            keyValueList = new List<KeyValuePair<string, double>>();

            // Strip all non-results, by adding only items of interest to the scoreList
            for (int i = 0; i < predictionDictionary.Count; i++)
            {
                KeyValuePair<string, string> pair = predictionDictionary.ElementAt(i);
                if (pair.Key.StartsWith("Scored Probabilities"))
                {
                    // Parse string as double then simplify the string key so to only have the item name
                    double scorefloat = 0f;
                    double.TryParse(pair.Value, out scorefloat);
                    string simplifiedName =
                        pair.Key.Replace("\"", "").Replace("Scored Probabilities for Class", "").Trim();
                    keyValueList.Add(new KeyValuePair<string, double>(simplifiedName, scorefloat));
                }
            }

            // Sort Predictions (results will be lowest to highest)
            keyValueList.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Spawn the top three items, from the keyValueList, which we have sorted
            for (int i = 0; i < 3; i++)
            {
                ShelfKeeper.instance.SpawnProduct(keyValueList[i].Key, i);
            }

            // Clear lists in case of reuse
            keyValueList.Clear();
            predictionDictionary.Clear();
        }
    ```

13. <span data-ttu-id="06816-440">저장할 **Visual Studio** 다시 이동 하 고 **Unity**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-440">Save **Visual Studio** and head back to **Unity**.</span></span>

14. <span data-ttu-id="06816-441">끌어서 합니다 **ProductPrediction** 클래스에서 스크립트를 **스크립트** 폴더에는 **주 카메라** 개체.</span><span class="sxs-lookup"><span data-stu-id="06816-441">Drag the **ProductPrediction** class script from the **Script** folder, onto the **Main Camera** object.</span></span>

15. <span data-ttu-id="06816-442">장면 및 프로젝트 저장할 **파일** >  ***장면 저장* / *파일***   >  **프로젝트를 저장할**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-442">Save your scene and project **File** > ***Save Scene* / *File*** > **Save Project**.</span></span>

## <a name="chapter-10---build-the-uwp-solution"></a><span data-ttu-id="06816-443">10 장-UWP 솔루션 빌드</span><span class="sxs-lookup"><span data-stu-id="06816-443">Chapter 10 - Build the UWP Solution</span></span>

<span data-ttu-id="06816-444">독립 실행형 응용 프로그램으로 실행할 수 있도록로 UWP 솔루션으로 프로젝트를 빌드할 때 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="06816-444">It is now time to build your project as a UWP solution, so that it can run as a standalone application.</span></span>

<span data-ttu-id="06816-445">빌드:</span><span class="sxs-lookup"><span data-stu-id="06816-445">To Build:</span></span>

1.  <span data-ttu-id="06816-446">클릭 하 여 현재 장면 저장 **파일** **장면 저장**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-446">Save the current scene by clicking on **File** **Save Scenes**.</span></span>

2.  <span data-ttu-id="06816-447">로 이동 **파일** **빌드 설정**</span><span class="sxs-lookup"><span data-stu-id="06816-447">Go to **File** **Build Settings**</span></span>

3.  <span data-ttu-id="06816-448">호출 확인란 **Unity C\# 프로젝트** (이 중요 한 빌드가 완료 된 후 클래스를 편집할 수)입니다.</span><span class="sxs-lookup"><span data-stu-id="06816-448">Check the box called **Unity C\# Projects** (this is important because it will allow you to edit the classes after build is completed).</span></span>

4.  <span data-ttu-id="06816-449">클릭할 **열고 장면 추가**,</span><span class="sxs-lookup"><span data-stu-id="06816-449">Click on **Add Open Scenes**,</span></span>

5.  <span data-ttu-id="06816-450">**빌드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-450">Click **Build**.</span></span>

    ![UWP 솔루션 빌드](images/AzureLabs-Lab7-54.png)

6.  <span data-ttu-id="06816-452">솔루션을 빌드 하려는 폴더를 선택 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06816-452">You will be prompted to select the folder where you want to build the Solution.</span></span>

7.  <span data-ttu-id="06816-453">만들기는 **빌드** 폴더 및 해당 폴더 내에서 원하는 적절 한 이름을 다른 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="06816-453">Create a **BUILDS** folder and within that folder create another folder with an appropriate name of your choice.</span></span>

8.  <span data-ttu-id="06816-454">새 폴더를 클릭 한 다음 클릭 **폴더 선택**해당 위치에서 빌드를 시작 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-454">Click your new folder and then click **Select Folder**, to begin the build at that location.</span></span>

    ![UWP 솔루션 빌드](images/AzureLabs-Lab7-55.png)

    ![UWP 솔루션 빌드](images/AzureLabs-Lab7-56.png)

9.  <span data-ttu-id="06816-457">한 번 Unity (약간의 시간이 걸릴 수 있습니다) 빌드 완료, 열립니다는 **파일 탐색기** 빌드 위치에 있는 창 (작업 표시줄에서 항상 windows에서 위에 나타나지 않을 수 있습니다 있지만 새 추가 대 한 알림을 확인 창)입니다.</span><span class="sxs-lookup"><span data-stu-id="06816-457">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-11---deploy-your-application"></a><span data-ttu-id="06816-458">응용 프로그램을 배포 하는 장-11</span><span class="sxs-lookup"><span data-stu-id="06816-458">Chapter 11 - Deploy your Application</span></span>

<span data-ttu-id="06816-459">응용 프로그램을 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-459">To deploy your application:</span></span>

1.  <span data-ttu-id="06816-460">새 Unity 빌드에 이동 (합니다 **앱** 폴더) 사용 하 여 솔루션 파일을 엽니다 **Visual Studio**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-460">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

2.  <span data-ttu-id="06816-461">Open Visual Studio를 사용 하 여 NuGet 패키지 복원, MachineLearningLab_Build 솔루션 (Visual Studio의 오른쪽에 있음) 솔루션 탐색기에서 마우스 오른쪽 단추로 클릭 하 고 NuGet 패키지 복원 클릭을 통해 수행할 수 있는를 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-461">With Visual Studio open, you need to Restore NuGet Packages, which can be done through right-clicking your MachineLearningLab_Build solution, from the Solution Explorer (found to the right of Visual Studio), and then clicking Restore NuGet Packages:</span></span>

    ![NuGet 패키지 추가](images/AzureLabs-Lab7-57.png)

3.  <span data-ttu-id="06816-463">솔루션 구성 선택에서 **디버그**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-463">In the Solution Configuration select **Debug**.</span></span>

4.  <span data-ttu-id="06816-464">솔루션 플랫폼에서 선택 **x86**하십시오 **로컬 컴퓨터**합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-464">In the Solution Platform, select **x86**, **Local Machine**.</span></span> 

    > <span data-ttu-id="06816-465">Microsoft HoloLens 알 수 있습니다 것이 더 쉽게 *원격 컴퓨터*컴퓨터로 테더 링 없습니다 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-465">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="06816-466">그러나 또한 다음을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-466">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="06816-467">알고는 **IP 주소** 내에서 찾을 수 있는 여 HoloLens의는 *설정 > 네트워크 및 인터넷 > Wi-fi > 고급 옵션*; IPv4는 주소를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-467">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="06816-468">확인 **개발자 모드** 됩니다 **에**에; *설정 > 업데이트 및 보안 > 개발자를 위한*합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-468">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![NuGet 패키지 추가](images/AzureLabs-Lab7-58.png)

5.  <span data-ttu-id="06816-470">로 이동 **빌드 메뉴** 를 클릭 **솔루션 배포** 사용자 PC에 응용 프로그램을 테스트용으로 로드 하려면.</span><span class="sxs-lookup"><span data-stu-id="06816-470">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your PC.</span></span>

6.  <span data-ttu-id="06816-471">이제 앱 시작할 준비가 되었습니다. 설치 된 앱 목록에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="06816-471">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

<span data-ttu-id="06816-472">혼합 현실 응용 프로그램을 실행 하는 경우 Unity 장면에 설정 된 도구를 표시 되 고 초기화에서 Azure 내에서 설정한 데이터를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06816-472">When you run the Mixed Reality application, you will see the bench that was set up in your Unity scene, and from initialization, the data you set up within Azure will be fetched.</span></span> <span data-ttu-id="06816-473">응용 프로그램 내에서 데이터를 역직렬화 하 고 현재 날짜 및 시간에 대 한 세 가지 상위 결과 시각적으로 세 가지 모델은 도구에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06816-473">The data will be deserialized within your application, and the three top results for your current date and time will be provided visually, as three models on the bench.</span></span>


## <a name="your-finished-machine-learning-application"></a><span data-ttu-id="06816-474">완성 된 Machine Learning 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="06816-474">Your finished Machine Learning application</span></span>
 
<span data-ttu-id="06816-475">축, 데이터 예측을 수행 하 여 장면에서 표시 하는 Azure Machine Learning을 활용 하는 혼합된 현실 앱을 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-475">Congratulations, you built a mixed reality app that leverages the Azure Machine Learning to make data predictions and display it on your scene.</span></span>

![NuGet 패키지 추가](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a><span data-ttu-id="06816-477">연습</span><span class="sxs-lookup"><span data-stu-id="06816-477">Exercise</span></span>

<span data-ttu-id="06816-478">**연습 1**</span><span class="sxs-lookup"><span data-stu-id="06816-478">**Exercise 1**</span></span>

<span data-ttu-id="06816-479">응용 프로그램의 정렬 순서를 사용 하 여 실험 하 및이 데이터는 잠재적으로 유용할 수 없는 선반에 나타나나요 아래 세 가지 예측을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="06816-479">Experiment with the sort order of your application and have the three bottom predictions appear on the shelf, as this data would potentially be useful also.</span></span>

<span data-ttu-id="06816-480">**연습 2**</span><span class="sxs-lookup"><span data-stu-id="06816-480">**Exercise 2**</span></span>

<span data-ttu-id="06816-481">사용 하 여 **Azure 테이블** 날씨 정보를 사용 하 여 새 테이블을 채우고 데이터를 사용 하 여 새 실험을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="06816-481">Using **Azure Tables** populate a new table with weather information and create a new experiment using the data.</span></span>
