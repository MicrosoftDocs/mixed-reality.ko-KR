---
title: MR 및 Azure 307-Machine learning
description: 이 과정을 완료 하 여 혼합 현실 응용 프로그램 내에서 Azure Machine Learning Studio을 구현 하는 방법을 알아보세요.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, 아카데미, unity, 자습서, api, 기계 학습, ml, 기계 학습 스튜디오, hololens, 몰입 형, vr
ms.openlocfilehash: c86c592573dd39d926869d8cce6025fa264cc90f
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437928"
---
>[!NOTE]
><span data-ttu-id="f1c7c-104">혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="f1c7c-105">따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="f1c7c-106">이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="f1c7c-107">지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="f1c7c-108">향후에는 HoloLens 2를 개발 하는 방법을 보여 주는 새 자습서 시리즈를 게시할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="f1c7c-109">이 알림은 게시 될 때 해당 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-307-machine-learning"></a><span data-ttu-id="f1c7c-110">MR 및 Azure 307: Machine learning</span><span class="sxs-lookup"><span data-stu-id="f1c7c-110">MR and Azure 307: Machine learning</span></span>

![최종 제품-시작](images/AzureLabs-Lab7-0.png)

<span data-ttu-id="f1c7c-112">이 과정에서는 Azure Machine Learning Studio를 사용 하 여 혼합 현실 응용 프로그램에 Machine Learning (ML) 기능을 추가 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-112">In this course, you will learn how to add Machine Learning (ML) capabilities to a mixed reality application using Azure Machine Learning Studio.</span></span>

<span data-ttu-id="f1c7c-113">*Azure Machine Learning Studio* 는 개발자에 게 데이터 입력, 출력, 준비 및 시각화에 도움이 될 수 있는 많은 수의 기계 학습 알고리즘을 제공 하는 Microsoft 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-113">*Azure Machine Learning Studio* is a Microsoft service, which provides developers with a large number of machine learning algorithms, which can help with data input, output, preparation, and visualization.</span></span> <span data-ttu-id="f1c7c-114">이러한 구성 요소를 통해 예측 분석 실험을 개발 하 고,이를 반복 하 고, 모델을 학습 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-114">From these components, it is then possible to develop a predictive analytics experiment, iterate on it, and use it to train your model.</span></span> <span data-ttu-id="f1c7c-115">다음 교육을 통해 Azure 클라우드에서 모델을 작동 하도록 설정 하 여 새 데이터의 점수를 매길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-115">Following training, you can make your model operational within the Azure cloud, so that it can then score new data.</span></span> <span data-ttu-id="f1c7c-116">자세한 내용은 [Azure Machine Learning Studio 페이지](https://azure.microsoft.com/services/machine-learning-studio/)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-116">For more information, visit the [Azure Machine Learning Studio page](https://azure.microsoft.com/services/machine-learning-studio/).</span></span>

<span data-ttu-id="f1c7c-117">이 과정을 완료 하면 혼합 현실의 헤드셋 응용 프로그램을 사용할 수 있으며 다음 작업을 수행 하는 방법이 학습 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-117">Having completed this course, you will have a mixed reality immersive headset application, and will have learned how do the following:</span></span>

1.  <span data-ttu-id="f1c7c-118">*Azure Machine Learning Studio* 포털에 판매 데이터 표를 제공 하 고 인기 있는 항목의 향후 판매를 예측 하는 알고리즘을 디자인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-118">Provide a table of sales data to the *Azure Machine Learning Studio* portal, and        design an algorithm to predict future sales of popular items.</span></span>
2.  <span data-ttu-id="f1c7c-119">ML 서비스에서 예측 데이터를 수신 하 고 해석할 수 있는 **Unity 프로젝트**를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-119">Create a **Unity Project**, which can receive and interpret prediction data from the ML service.</span></span>
3.  <span data-ttu-id="f1c7c-120">선반에서 가장 인기 있는 판매 항목을 제공 하 여 **Unity 프로젝트**내에서 폐색 데이터를 시각적으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-120">Display the predication data visually within the **Unity Project**, through providing the most popular sales items, on a shelf.</span></span>

<span data-ttu-id="f1c7c-121">응용 프로그램에서 결과를 디자인과 통합 하는 방법을 사용자가 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-121">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="f1c7c-122">이 과정은 Azure 서비스를 Unity 프로젝트와 통합 하는 방법을 배울 수 있도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-122">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="f1c7c-123">이 과정에서 얻은 지식을 사용 하 여 혼합 현실 응용 프로그램을 개선 하는 것은 사용자의 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-123">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="f1c7c-124">이 과정은 다른 혼합 현실 랩을 직접 포함 하지 않는 자체 포함 된 자습서입니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-124">This course is a self-contained tutorial, which does not directly involve any other Mixed Reality Labs.</span></span>

## <a name="device-support"></a><span data-ttu-id="f1c7c-125">장치 지원</span><span class="sxs-lookup"><span data-stu-id="f1c7c-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="f1c7c-126">과정</span><span class="sxs-lookup"><span data-stu-id="f1c7c-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="f1c7c-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="f1c7c-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="f1c7c-128"><a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="f1c7c-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="f1c7c-129">MR 및 Azure 307: Machine learning</span><span class="sxs-lookup"><span data-stu-id="f1c7c-129">MR and Azure 307: Machine learning</span></span></td><td style="text-align: center;"> <span data-ttu-id="f1c7c-130">✔️</span><span class="sxs-lookup"><span data-stu-id="f1c7c-130">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="f1c7c-131">✔️</span><span class="sxs-lookup"><span data-stu-id="f1c7c-131">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="f1c7c-132">이 과정에서 주로 Windows Mixed Reality (VR) 헤드셋에 초점을 맞춘 반면,이 과정에서 학습 하는 내용을 Microsoft HoloLens에도 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-132">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="f1c7c-133">과정을 진행할 때 HoloLens를 지원 하기 위해 사용 해야 하는 모든 변경 내용에 대 한 메모를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-133">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="f1c7c-134">HoloLens를 사용 하는 경우 음성 캡처 중에 몇 가지 echo를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-134">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f1c7c-135">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="f1c7c-135">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="f1c7c-136">이 자습서는 Unity 및 C#에 대 한 기본 경험이 있는 개발자를 위해 작성 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-136">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="f1c7c-137">또한이 문서에서 사전 요구 사항 및 작성 된 지침은 작성 시 테스트 되 고 확인 된 내용 (2018 일 수 있음)을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-137">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="f1c7c-138">[도구 설치 문서](install-the-tools.md)에 나와 있는 것 처럼 최신 소프트웨어를 무료로 사용할 수 있지만,이 과정의 정보가 아래 나열 된 것 보다 최신 소프트웨어에서 찾을 수 있는 것으로 간주 하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-138">You are free to use the latest software, as listed within the [install the tools article](install-the-tools.md), though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="f1c7c-139">이 과정에는 다음 하드웨어 및 소프트웨어를 권장 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-139">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="f1c7c-140">모던 (VR) 헤드셋 개발을 위한 [Windows Mixed Reality와 호환 되](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 는 개발 PC</span><span class="sxs-lookup"><span data-stu-id="f1c7c-140">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="f1c7c-141">개발자 모드를 사용 하는 Windows 10이 하 버전의 작성자 업데이트 (또는 이상)</span><span class="sxs-lookup"><span data-stu-id="f1c7c-141">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="f1c7c-142">최신 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="f1c7c-142">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="f1c7c-143">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="f1c7c-143">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="f1c7c-144">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="f1c7c-144">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="f1c7c-145">개발자 모드가 사용 하도록 설정 된 [Windows Mixed Reality 모던 (VR) 헤드셋](immersive-headset-hardware-details.md) 또는 [Microsoft HoloLens](hololens-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="f1c7c-145">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="f1c7c-146">Azure 설정 및 ML 데이터 검색에 대 한 인터넷 액세스</span><span class="sxs-lookup"><span data-stu-id="f1c7c-146">Internet access for Azure setup and ML data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="f1c7c-147">시작하기 전 확인 사항</span><span class="sxs-lookup"><span data-stu-id="f1c7c-147">Before you start</span></span>

<span data-ttu-id="f1c7c-148">이 프로젝트를 빌드하는 데 문제가 발생 하지 않도록 하려면 루트 또는 루트 폴더에이 자습서에서 언급 한 프로젝트를 만드는 것이 좋습니다. (긴 폴더 경로는 빌드 시에 문제를 일으킬 수 있습니다.)</span><span class="sxs-lookup"><span data-stu-id="f1c7c-148">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 

## <a name="chapter-1---azure-storage-account-setup"></a><span data-ttu-id="f1c7c-149">1 장-계정 설정 Azure Storage</span><span class="sxs-lookup"><span data-stu-id="f1c7c-149">Chapter 1 - Azure Storage Account setup</span></span>

<span data-ttu-id="f1c7c-150">Azure Translator API를 사용 하려면 응용 프로그램에서 사용할 수 있도록 서비스 인스턴스를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-150">To use the Azure Translator API, you will need to configure an instance of the service to be made available to your application.</span></span>
1.  <span data-ttu-id="f1c7c-151">[Azure Portal](https://portal.azure.com)에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-151">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="f1c7c-152">아직 Azure 계정이 없는 경우 새로 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-152">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="f1c7c-153">교실 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 proctors 중 하나에 문의 하 여 새 계정을 설정 하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-153">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="f1c7c-154">로그인 되 면 왼쪽 메뉴에서 **저장소 계정** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-154">Once you are logged in, click on **Storage Accounts** in the left menu.</span></span>

    ![계정 설정 Azure Storage](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > <span data-ttu-id="f1c7c-156">새 단어는 **새** 포털에서 **리소스 만들기**로 대체 되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-156">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="f1c7c-157">**저장소 계정** 탭에서 **추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-157">On the **Storage Accounts** tab, click on **Add**.</span></span>

    ![계정 설정 Azure Storage](images/AzureLabs-Lab7-2.png)

4.  <span data-ttu-id="f1c7c-159">**저장소 계정 만들기** 패널에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-159">In the **Create Storage Account** panel:</span></span>

    1.  <span data-ttu-id="f1c7c-160">계정에 대 한 **이름을** 삽입 합니다 .이 필드에는 숫자 및 소문자만 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-160">Insert a **Name** for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>
    2.  <span data-ttu-id="f1c7c-161">**배포 모델에서** **Resource manager**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-161">For **Deployment model,** select **Resource manager**.</span></span>
    3.  <span data-ttu-id="f1c7c-162">**계정 종류**에 대해 **저장소 (범용 v1)** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-162">For **Account kind**, select **Storage (general purpose v1)**.</span></span>
    4.  <span data-ttu-id="f1c7c-163">**성능**으로 **표준**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-163">For **Performance**, select **Standard**.</span></span>
    5.  <span data-ttu-id="f1c7c-164">**복제** 의 경우 **읽기 액세스-지역 중복 저장소 (RA-GRS)** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-164">For **Replication** select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>
    6.  <span data-ttu-id="f1c7c-165">**보안 전송을** **사용 하지 않도록 설정**해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-165">Leave **Secure transfer required** as **Disabled**.</span></span>
    7.  <span data-ttu-id="f1c7c-166">**구독**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-166">Select a **Subscription**.</span></span>
    4. <span data-ttu-id="f1c7c-167">리소스 그룹을 선택 하거나 새 **리소스 그룹** 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-167">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="f1c7c-168">리소스 그룹은 Azure 자산의 컬렉션에 대 한 청구를 모니터링 하 고, 액세스를 제어 하 고, 프로 비전 하 고, 관리 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-168">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="f1c7c-169">단일 프로젝트와 연결 된 모든 Azure 서비스 (예: 이러한 랩)를 공용 리소스 그룹에 유지 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-169">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="f1c7c-170">Azure 리소스 그룹에 대 한 자세한 내용을 보려면 [리소스 그룹 문서를 참조](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)하세요.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-170">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>
    
    5.  <span data-ttu-id="f1c7c-171">새 리소스 그룹을 만드는 경우 리소스 그룹의 **위치** 를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-171">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="f1c7c-172">위치는 응용 프로그램이 실행 되는 영역에 있는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-172">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="f1c7c-173">일부 Azure 자산은 특정 지역 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-173">Some Azure assets are only available in certain regions.</span></span>

5.  <span data-ttu-id="f1c7c-174">또한이 서비스에 적용 된 사용 약관을 이해 했는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-174">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    ![계정 설정 Azure Storage](images/AzureLabs-Lab7-3.png)

6.  <span data-ttu-id="f1c7c-176">**만들기**를 클릭 한 후에는 서비스를 만들 때까지 기다려야 합니다 .이 작업이 몇 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-176">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="f1c7c-177">서비스 인스턴스를 만든 후 알림이 포털에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-177">A notification will appear in the portal once the Service instance is created.</span></span>

    ![계정 설정 Azure Storage](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio"></a><span data-ttu-id="f1c7c-179">2 장-Azure Machine Learning Studio</span><span class="sxs-lookup"><span data-stu-id="f1c7c-179">Chapter 2 - The Azure Machine Learning Studio</span></span>

<span data-ttu-id="f1c7c-180">*Azure Machine Learning*을 사용 하려면 응용 프로그램에서 사용할 수 있도록 Machine Learning 서비스의 인스턴스를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-180">To use the *Azure Machine Learning*, you will need to configure an instance of the Machine Learning service to be made available to your application.</span></span>

1.  <span data-ttu-id="f1c7c-181">Azure Portal의 왼쪽 위 모서리에서 **새로 만들기** 를 클릭 하 고 **Machine Learning Studio 작업 영역**을 검색 하 고 **enter**키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-181">In the Azure Portal, click on **New** in the top left corner, and search for **Machine Learning Studio Workspace**, press **Enter**.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-5.png)

2.  <span data-ttu-id="f1c7c-183">새 페이지에 **Machine Learning Studio 작업 영역** 서비스에 대 한 설명이 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-183">The new page will provide a description of the **Machine Learning Studio Workspace**  service.</span></span> <span data-ttu-id="f1c7c-184">이 프롬프트의 왼쪽 아래에서 **만들기** 단추를 클릭 하 여이 서비스와의 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-184">At the bottom left of this prompt, click the **Create** button, to create an association with this service.</span></span>

3.  <span data-ttu-id="f1c7c-185">**만들기**를 클릭 하면 새 **Machine Learning Studio 서비스**에 대 한 몇 가지 세부 정보를 제공 해야 하는 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-185">Once you have clicked on **Create**, a panel will appear where you need to provide some details about your new **Machine Learning Studio service**:</span></span>

    1.  <span data-ttu-id="f1c7c-186">이 서비스 인스턴스의 원하는 **작업 영역 이름을** 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-186">Insert your desired **Workspace name** for this service instance.</span></span>

    2.  <span data-ttu-id="f1c7c-187">**구독**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-187">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="f1c7c-188">리소스 그룹을 선택 하거나 새 **리소스 그룹** 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-188">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="f1c7c-189">리소스 그룹은 Azure 자산의 컬렉션에 대 한 청구를 모니터링 하 고, 액세스를 제어 하 고, 프로 비전 하 고, 관리 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-189">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="f1c7c-190">단일 프로젝트와 연결 된 모든 Azure 서비스 (예: 이러한 랩)를 공용 리소스 그룹에 유지 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-190">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="f1c7c-191">Azure 리소스 그룹에 대 한 자세한 내용을 보려면 [리소스 그룹 문서를 참조](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)하세요.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-191">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="f1c7c-192">새 리소스 그룹을 만드는 경우 리소스 그룹의 **위치** 를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-192">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="f1c7c-193">위치는 응용 프로그램이 실행 되는 영역에 있는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-193">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="f1c7c-194">일부 Azure 자산은 특정 지역 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-194">Some Azure assets are only available in certain regions.</span></span> <span data-ttu-id="f1c7c-195">이전 장에서 Azure Storage를 만드는 데 사용한 것과 동일한 리소스 그룹을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-195">You should use the same resource group that you used for creating the Azure Storage in the previous Chapter.</span></span>

    5.  <span data-ttu-id="f1c7c-196">**저장소 계정** 섹션에서 **기존 항목 사용**을 클릭 한 다음 드롭다운 메뉴를 클릭 하 고 여기에서 마지막 챕터에서 만든 **저장소 계정을** 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-196">For the **Storage account** section, click **Use existing**, then click the dropdown menu, and from there, click the **Storage Account** you created in the last Chapter.</span></span>

    6.  <span data-ttu-id="f1c7c-197">드롭다운 메뉴에서 적절 한 **작업 영역 가격 책정 계층** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-197">Select the appropriate **Workspace pricing tier** for you, from the dropdown menu.</span></span>

    7.  <span data-ttu-id="f1c7c-198">**웹 서비스 계획** 섹션에서 새로 **만들기** **를** 클릭 한 다음 텍스트 필드에 이름을 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-198">Within the **Web service plan** section, click **Create** **new,** then insert a name for it in the text field.</span></span>

    8.  <span data-ttu-id="f1c7c-199">**웹 서비스 계획 가격 책정 계층** 섹션에서 원하는 가격 책정 계층을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-199">From the **Web service plan pricing tier** section, select the price tier of your choice.</span></span> <span data-ttu-id="f1c7c-200">**DEVTEST Standard** 라는 개발 테스트 계층은 무료로 제공 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-200">A development testing tier called **DEVTEST Standard** should be available to you at no charge.</span></span>

    9.  <span data-ttu-id="f1c7c-201">또한이 서비스에 적용 된 사용 약관을 이해 했는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-201">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    10. <span data-ttu-id="f1c7c-202">**만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-202">Click **Create**.</span></span>

        ![Azure Machine Learning Studio](images/AzureLabs-Lab7-6.png)

4.  <span data-ttu-id="f1c7c-204">**만들기**를 클릭 한 후에는 서비스를 만들 때까지 기다려야 합니다 .이 작업이 몇 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-204">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

5.  <span data-ttu-id="f1c7c-205">서비스 인스턴스를 만든 후 알림이 포털에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-205">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-7.png)

6.  <span data-ttu-id="f1c7c-207">알림을 클릭 하 여 새 서비스 인스턴스를 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-207">Click on the notification to explore your new Service instance.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-8.png)

7.  <span data-ttu-id="f1c7c-209">알림에서 **리소스로 이동** 단추를 클릭 하 여 새 서비스 인스턴스를 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-209">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span>

8.  <span data-ttu-id="f1c7c-210">표시 되는 페이지의 **추가 링크** 섹션에서 **시작 Machine Learning Studio**를 클릭 합니다. 그러면 브라우저를 **Machine Learning Studio** 포털로 안내 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-210">In the page displayed, under the **Additional Links** section, click **Launch Machine Learning Studio**, which will direct your browser to the **Machine Learning Studio** portal.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-9.png)

9.  <span data-ttu-id="f1c7c-212">오른쪽 위 또는 가운데에 있는 **로그인** 단추를 사용 하 여 Machine Learning Studio에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-212">Use the **Sign In** button, at the top right or in the center, to log into your Machine Learning Studio.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-dataset-setup"></a><span data-ttu-id="f1c7c-214">3 장-Machine Learning Studio: 데이터 집합 설치</span><span class="sxs-lookup"><span data-stu-id="f1c7c-214">Chapter 3 - The Machine Learning Studio: Dataset setup</span></span>

<span data-ttu-id="f1c7c-215">Machine Learning 알고리즘의 작동 방법 중 하나는 기존 데이터를 분석 한 다음 기존 데이터 집합을 기반으로 향후 결과를 예측 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-215">One of the ways Machine Learning algorithms work is by analyzing existing data and then attempting to predict future results based on the existing data set.</span></span> <span data-ttu-id="f1c7c-216">이는 일반적으로 기존 데이터를 더 많이 사용 하는 것을 의미 하므로 이후 결과를 예측 하는 알고리즘이 더 좋아집니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-216">This generally means that the more existing data you have, the better the algorithm will be at predicting future results.</span></span>

<span data-ttu-id="f1c7c-217">이 과정에서 ProductsTableCSV 이라는 샘플 테이블이 제공 [되며 여기에서 다운로드할 수 있습니다](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).</span><span class="sxs-lookup"><span data-stu-id="f1c7c-217">A sample table is provided to you, for this course, called [ProductsTableCSV and can be downloaded here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f1c7c-218">위의 .zip 파일에는 **ProductsTableCSV** 와 **unitypackage**가 모두 포함 되어 있습니다 .이 파일은 [6 장에서](#chapter-6---importing-the-mlproducts-unity-package)필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-218">The above .zip file contains both the **ProductsTableCSV** and the **.unitypackage**, which you will need in [Chapter 6](#chapter-6---importing-the-mlproducts-unity-package).</span></span> <span data-ttu-id="f1c7c-219">이 패키지는 csv 파일에 별도로 제공 되지만 해당 챕터에도 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-219">This package is also provided within that Chapter, though separate to the csv file.</span></span>

<span data-ttu-id="f1c7c-220">이 샘플 데이터 집합에는 2017 년의 각 날짜의 매시간 가장 인기 있는 개체 레코드가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-220">This sample data set contains a record of the best-selling objects at every hour of each day of the year 2017.</span></span>
        
![Machine Learning Studio: 데이터 집합 설치](images/AzureLabs-Lab7-11.png)

<span data-ttu-id="f1c7c-222">예를 들어 오후 1 시 (시간 13)에서 2017의 1 일에 가장 잘 팔리는 항목은 솔트 및 고추입니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-222">For example, on day 1 of 2017, at 1pm (hour 13), the best-selling item was salt and pepper.</span></span>

<span data-ttu-id="f1c7c-223">이 샘플 테이블에는 9998 개의 항목이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-223">This sample table contains 9998 entries.</span></span>

1.  <span data-ttu-id="f1c7c-224">**Machine Learning Studio** 포털로 다시 이동 하 여이 테이블을 ML에 대 한 **데이터 집합** 으로 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-224">Head back to the **Machine Learning Studio** portal, and add this table as a **Dataset** for your ML.</span></span> <span data-ttu-id="f1c7c-225">화면의 왼쪽 아래에 있는 **+ 새로 만들기** 단추를 클릭 하 여이 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-225">Do this by clicking the **+ New** button in the bottom left corner of the screen.</span></span>

    ![Machine Learning Studio: 데이터 집합 설치](images/AzureLabs-Lab7-12.png)

2.  <span data-ttu-id="f1c7c-227">섹션은 아래쪽에서 위쪽으로 제공 되며 왼쪽에는 탐색 패널이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-227">A section will come up from the bottom, and within that there is navigation panel on the left.</span></span> <span data-ttu-id="f1c7c-228">**로컬 파일에서**데이터 집합을 클릭 한 다음 오른쪽에 있는 **데이터 집합**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-228">Click **Dataset**, then to the right of that, **From Local File**.</span></span>

    ![Machine Learning Studio: 데이터 집합 설치](images/AzureLabs-Lab7-13.png)

3.  <span data-ttu-id="f1c7c-230">다음 단계를 수행 하 여 새 **데이터 집합** 을 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-230">Upload the new **Dataset** by following these steps:</span></span>

    1. <span data-ttu-id="f1c7c-231">하드 드라이브에서 새 데이터 집합을 **찾아볼** 수 있는 업로드 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-231">The upload window will appear, where you can **Browse** your hard drive for the new dataset.</span></span>

        ![Machine Learning Studio: 데이터 집합 설치](images/AzureLabs-Lab7-14.png)

    2.  <span data-ttu-id="f1c7c-233">을 선택 하 고 다시 업로드 창에서 읽으려고 확인란을 선택 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-233">Once selected, and back in the upload window, leave the checkbox unticked.</span></span>

    3.  <span data-ttu-id="f1c7c-234">아래 텍스트 필드에서 데이터 집합 이름으로 **ProductsTableCSV** 를 입력 합니다 (자동으로 추가 해야 함).</span><span class="sxs-lookup"><span data-stu-id="f1c7c-234">In the text field below, enter **ProductsTableCSV.csv** as the name for the dataset (though should automatically be added).</span></span>

    4.  <span data-ttu-id="f1c7c-235">**형식**에 대 한 드롭다운 메뉴를 사용 하 여 **헤더 (.csv)가 포함 된 일반 CSV 파일**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-235">Using the dropdown menu for **Type**, select **Generic CSV File with a header (.csv)**.</span></span>

    5.  <span data-ttu-id="f1c7c-236">업로드 창의 오른쪽 아래에 있는 틱을 누르면 **데이터 집합이** 업로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-236">Press the tick in the bottom right of the upload window, and your **Dataset** will be uploaded.</span></span>

## <a name="chapter-4---the-machine-learning-studio-the-experiment"></a><span data-ttu-id="f1c7c-237">4 장-Machine Learning Studio: 실험</span><span class="sxs-lookup"><span data-stu-id="f1c7c-237">Chapter 4 - The Machine Learning Studio: The Experiment</span></span>

<span data-ttu-id="f1c7c-238">기계 학습 시스템을 구축 하려면 먼저 데이터에 대 한 이론적 유효성을 검사 하기 위해 실험을 빌드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-238">Before you can build your machine learning system, you will need to build an experiment, to validate your theory about your data.</span></span> <span data-ttu-id="f1c7c-239">결과를 사용 하 여 더 많은 데이터가 필요한 지 또는 데이터와 가능한 결과 간의 상관 관계가 없는지를 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-239">With the results, you will know whether you need more data, or if there is no correlation between the data and a possible outcome.</span></span>

<span data-ttu-id="f1c7c-240">실험 만들기를 시작 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-240">To start creating an experiment:</span></span>

1.  <span data-ttu-id="f1c7c-241">페이지 왼쪽 아래에 있는 **+ 새로 만들기** 단추를 다시 클릭 한 다음 **실험** > **빈 실험**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-241">Click again on the **+ New** button on the bottom left of the page, then click on **Experiment** > **Blank Experiment**.</span></span>

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-15.png)

2.  <span data-ttu-id="f1c7c-243">새 페이지가 빈 실험으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-243">A new page will be displayed with a blank Experiment:</span></span>

3.  <span data-ttu-id="f1c7c-244">왼쪽 패널에서 **내 데이터** 집합 > **저장 된 데이터 집합** 을 확장 하 고 **ProductsTableCSV** 를 **실험 캔버스로**끌어다 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-244">From the panel on the left expand **Saved Datasets** > **My Datasets** and drag the  **ProductsTableCSV** on to the **Experiment Canvas**.</span></span>

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-16.png)

4.  <span data-ttu-id="f1c7c-246">왼쪽 패널에서 **데이터 변환** > **샘플 및 분할**을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-246">In the panel on the left, expand **Data Transformation** > **Sample and Split**.</span></span> <span data-ttu-id="f1c7c-247">그런 다음 **데이터 분할** 항목을 **실험 캔버스로**끌어다 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-247">Then drag the **Split Data** item in to the **Experiment Canvas**.</span></span> <span data-ttu-id="f1c7c-248">데이터 분할 항목은 데이터 집합을 두 부분으로 분할 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-248">The Split Data item will split the data set into two parts.</span></span> <span data-ttu-id="f1c7c-249">기계 학습 알고리즘을 학습 하는 데 사용 하는 한 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-249">One part you will use for training the machine learning algorithm.</span></span> <span data-ttu-id="f1c7c-250">두 번째 부분은 생성 된 알고리즘의 정확도를 평가 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-250">The second part will be used to evaluate the accuracy of the algorithm generated.</span></span>

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-17.png)

5.  <span data-ttu-id="f1c7c-252">캔버스의 데이터 분할 항목이 선택 된 상태에서 오른쪽 패널의 **첫 번째 출력 데이터 집합에 있는 행의 비율** 을 **0.7**로 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-252">In the right panel (while the Split Data item on the canvas is selected), edit the **Fraction of rows in the first output dataset** to **0.7**.</span></span> <span data-ttu-id="f1c7c-253">이렇게 하면 데이터는 두 부분으로 분할 되 고 첫 번째 부분은 데이터의 70% 이며 두 번째 부분은 나머지 30%가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-253">This will split the data into two parts, the first part will be 70% of the data, and the second part will be the remaining 30%.</span></span> <span data-ttu-id="f1c7c-254">데이터가 무작위로 분할 되도록 하려면 **임의 분할** 확인란이 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-254">To ensure that the data is split randomly, make sure the **Randomized split** checkbox remains checked.</span></span>

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-18.png)

6.  <span data-ttu-id="f1c7c-256">캔버스의 **ProductsTableCSV** 항목 밑에서 분할 된 데이터 항목의 위쪽으로 연결을 끕니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-256">Drag a connection from the base of the **ProductsTableCSV** item on the canvas to the top of the Split Data item.</span></span> <span data-ttu-id="f1c7c-257">이렇게 하면 항목을 연결 하 고 **ProductsTableCSV** 데이터 집합 출력 (데이터)을 분할 데이터 입력으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-257">This will connect the items and send the **ProductsTableCSV** dataset output (the data) to the Split Data input.</span></span>  

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-19.png)

7.  <span data-ttu-id="f1c7c-259">왼쪽의 **실험** 패널에서 **Machine Learning** > **학습**을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-259">In the **Experiments** panel on the left side, expand **Machine Learning** > **Train**.</span></span> <span data-ttu-id="f1c7c-260">**모델 학습** 항목을 실험 캔버스로 끌어다 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-260">Drag the **Train Model** item out in to the Experiment canvas.</span></span> <span data-ttu-id="f1c7c-261">캔버스는 아래와 동일 하 게 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-261">Your canvas should look the same as the below.</span></span>

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-20.png)

8.  <span data-ttu-id="f1c7c-263">**데이터 분할** 항목의 ***왼쪽 아래*** 에서 **모델 학습** 항목의 **오른쪽 위에** 연결을 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-263">From the ***bottom left*** of the **Split Data** item drag a connection to the **top right** of the **Train Model** item.</span></span> <span data-ttu-id="f1c7c-264">데이터 집합에서 처음 70%의 분할은 학습 모델에서 알고리즘을 학습 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-264">The first 70% split from the dataset will be used by the Train Model to train the algorithm.</span></span>

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-21.png)

9.  <span data-ttu-id="f1c7c-266">캔버스에서 **모델 학습** 항목을 선택 하 고 브라우저 창의 오른쪽에 있는 **속성** 패널에서 **열 선택기 시작** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-266">Select the **Train Model** item on the canvas, and in the **Properties** panel (on the right-hand side of your browser window) click the **Launch column selector** button.</span></span>

10. <span data-ttu-id="f1c7c-267">텍스트 상자에 **product** 를 입력 하 고 **enter**키를 누릅니다. *제품* 은 예측 학습을 위한 열로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-267">In the text box type **product** and then press **Enter**, *product* will be set as a column to train predictions.</span></span> <span data-ttu-id="f1c7c-268">이를 수행 하 고 오른쪽 아래 모서리에 있는 **틱** 을 클릭 하 여 선택 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-268">Following this, click on the **tick** in the bottom-right corner to close the selection dialog.</span></span>

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-22.png)

11. <span data-ttu-id="f1c7c-270">**다중 클래스 로지스틱 회귀** 알고리즘을 학습 하 여 시간 및 날짜를 기준으로 가장 많이 판매 되는 **제품** 을 예측 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-270">You are going to train a **Multiclass Logistic Regression** algorithm to predict the most sold **product** based on the hour of the day and the date.</span></span> <span data-ttu-id="f1c7c-271">Azure Machine Learning studio에서 제공 하는 다양 한 알고리즘에 대 한 세부 정보를 설명 하기 위해이 문서에서는 다루지 않지만 [Machine Learning Algorithm 참고 자료 시트](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet) 에서 더 많은 정보를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-271">It is beyond the scope of this document to explain the details of the different algorithms provided by the Azure Machine Learning studio, though, you can find out more from the [Machine Learning Algorithm Cheat Sheet](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)</span></span>

12. <span data-ttu-id="f1c7c-272">왼쪽의 실험 항목 패널에서 **Machine Learning** 를 확장 하 > **모델** > **분류**를 초기화 하 고 **다중 클래스 로지스틱 회귀** 항목을 실험 캔버스로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-272">From the experiment items panel on the left, expand **Machine Learning** > **Initialize Model** > **Classification**, and drag the **Multiclass Logistic Regression** item on to the experiment canvas.</span></span>

13. <span data-ttu-id="f1c7c-273">**다중 클래스 로지스틱 회귀**의 아래쪽에 있는 출력을 **모델 학습** 항목의 왼쪽 위 입력에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-273">Connect the output, from the bottom of the **Multiclass Logistic Regression**, to the top-left input of the **Train Model** item.</span></span>

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-23.png)

14. <span data-ttu-id="f1c7c-275">왼쪽 패널의 실험 항목 목록에서 **Machine Learning** > **점수**를 확장 하 고 **모델 점수 매기기** 항목을 캔버스로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-275">In list of experiment items in the panel on the left, expand **Machine Learning** > **Score**, and drag the **Score Model** item on to the canvas.</span></span>

15. <span data-ttu-id="f1c7c-276">**학습 모델**의 아래쪽에서 **점수 모델**의 왼쪽 위 입력에 출력을 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-276">Connect the output, from the bottom of the **Train Model**, to the top-left input of the **Score Model**.</span></span>

16. <span data-ttu-id="f1c7c-277">**데이터 분할**에서 오른쪽 아래 출력을 **모델 점수 매기기** 항목의 오른쪽 위 입력에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-277">Connect the bottom-right output from **Split Data**, to the top-right input of the **Score Model** item.</span></span>

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-24.png)

17. <span data-ttu-id="f1c7c-279">왼쪽 패널의 **실험** 항목 목록에서 **Machine Learning** > **평가**를 확장 하 고 **모델 평가** 항목을 캔버스로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-279">In the list of **Experiment** items in the panel on the left, expand **Machine Learning** > **Evaluate**, and drag the **Evaluate Model** item onto the canvas.</span></span>

18. <span data-ttu-id="f1c7c-280">**점수 모델** 의 출력을 **평가 모델**의 왼쪽 위 입력에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-280">Connect the output from the **Score Model** to the top-left input of the **Evaluate Model**.</span></span>

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-25.png)

19. <span data-ttu-id="f1c7c-282">첫 번째 Machine Learning 실험을 빌드 했습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-282">You have built your first Machine Learning Experiment.</span></span> <span data-ttu-id="f1c7c-283">이제 실험을 저장 하 고 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-283">You can now save and run the experiment.</span></span> <span data-ttu-id="f1c7c-284">페이지 아래쪽의 메뉴에서 **저장** 단추를 클릭 하 여 실험을 저장 한 다음 **실행** 을 클릭 하 여 실험을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-284">In the menu at the bottom of the page, click on the **Save** button to save your experiment and then click **Run** to the start the experiment.</span></span>

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-26.png)

20. <span data-ttu-id="f1c7c-286">캔버스의 오른쪽 위에서 실험의 **상태** 를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-286">You can see the **status** of the experiment in the top-right of the canvas.</span></span> <span data-ttu-id="f1c7c-287">몇 분 정도 기다린 후 실험을 완료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-287">Wait a few moments for the experiment to finish.</span></span>

    > <span data-ttu-id="f1c7c-288">실제 데이터 집합이 큰 경우 실험을 실행 하는 데 몇 시간이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-288">If you have a big (real world) dataset it is likely that the experiment could take hours to run.</span></span>

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-27.png)

21. <span data-ttu-id="f1c7c-290">캔버스에서 **모델 평가** 항목을 마우스 오른쪽 단추로 클릭 하 고 상황에 맞는 메뉴에서 마우스를 클릭 하 여 **평가 결과**를 가리킨 다음 **시각화**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-290">Right click on the **Evaluate Model** item in the canvas and from the context menu hover the mouse over **Evaluation Results**, then select **Visualize**.</span></span>

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-28.png)

22. <span data-ttu-id="f1c7c-292">평가 결과는 예상 결과와 실제 결과를 표시 하는 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-292">The evaluation results will be displayed showing the predicted outcomes versus the actual outcomes.</span></span> <span data-ttu-id="f1c7c-293">이는 이전에 분할 된 원래 데이터 집합의 30%를 사용 하 여 모델을 평가 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-293">This uses the 30% of the original dataset, that was split earlier, for evaluating the model.</span></span> <span data-ttu-id="f1c7c-294">결과가 적절 하지 않은 것을 볼 수 있습니다. 이상적으로는 각 행에 있는 가장 큰 숫자를 열에서 강조 표시 된 항목으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-294">You can see the results are not great, ideally you would have the highest number in each row be the highlighted item in the columns.</span></span>

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-29.png)

23. <span data-ttu-id="f1c7c-296">**결과**를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-296">Close the **Results**.</span></span>

24. <span data-ttu-id="f1c7c-297">새로 학습 된 Machine Learning 모델을 사용 하려면 **웹 서비스로**노출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-297">To use your newly trained Machine Learning model you need to expose it as a **Web Service**.</span></span> <span data-ttu-id="f1c7c-298">이렇게 하려면 페이지 아래쪽의 메뉴에서 **웹 서비스 설정** 메뉴 항목을 클릭 하 고 **예측 웹 서비스**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-298">To do this, click on the **Set Up Web Service** menu item in the menu at the bottom of the page, and click on **Predictive Web Service**.</span></span>

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-30.png)

25. <span data-ttu-id="f1c7c-300">새 탭이 만들어지고 학습 모델을 병합 하 여 새 웹 서비스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-300">A new tab will be created, and the train model merged to create the new web service.</span></span> 

26. <span data-ttu-id="f1c7c-301">페이지 아래쪽의 메뉴에서 **저장**을 클릭 한 다음 **실행**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-301">In the menu at the bottom of the page click **Save**, then click **Run**.</span></span> <span data-ttu-id="f1c7c-302">실험 캔버스의 오른쪽 위 모서리에 상태가 업데이트 된 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-302">You will see the status updated in the top-right corner of the experiment canvas.</span></span>

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-31.png)

27. <span data-ttu-id="f1c7c-304">실행이 완료 되 면 **웹 서비스 배포** 단추가 페이지 아래쪽에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-304">Once it has finished running, a **Deploy Web Service** button will appear at the bottom of the page.</span></span> <span data-ttu-id="f1c7c-305">웹 서비스를 배포할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-305">You are ready to deploy the web service.</span></span> <span data-ttu-id="f1c7c-306">페이지 아래쪽의 메뉴에서 **웹 서비스 배포** (클래식)를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-306">Click **Deploy Web Service** (Classic) in the menu at the bottom of the page.</span></span>

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-32.png)

    > <span data-ttu-id="f1c7c-308">브라우저에서 **허용**해야 하는 팝업을 허용할지 여부를 묻는 메시지가 표시 될 수 있습니다. 단, 배포 페이지가 표시 되지 않는 경우에는 **웹 서비스 배포** 를 다시 눌러야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-308">Your browser may prompt to allow a pop-up, which you should **allow**, though you may need to press **Deploy Web Service** again, if the deploy page does not show.</span></span> 

28. <span data-ttu-id="f1c7c-309">실험을 만든 후에는 **API 키** 를 표시 하는 **대시보드** 페이지로 리디렉션됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-309">Once the Experiment has been created you will be redirected to a **Dashboard** page where you will have your **API Key** displayed.</span></span> <span data-ttu-id="f1c7c-310">잠시 동안 메모장에 복사 하 여 코드에서 곧 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-310">Copy it into a notepad for the moment, you will need it in your code very soon.</span></span> <span data-ttu-id="f1c7c-311">API 키를 적어둔 후에는 키 아래의 **기본 끝점** 섹션에서 **요청/응답** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-311">Once you have noted your API Key, click on the **REQUEST/RESPONSE** button in the **Default Endpoint** section underneath the Key.</span></span>

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > <span data-ttu-id="f1c7c-313">이 페이지에서 테스트를 클릭 하는 경우 입력 데이터를 입력 하 고 출력을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-313">If you click Test in this page, you will be able to enter input data and view the output.</span></span> <span data-ttu-id="f1c7c-314">**날짜** 와 **시간**을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-314">Enter the **day** and **hour**.</span></span> <span data-ttu-id="f1c7c-315">**제품** 항목을 비워 둡니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-315">Leave the **product** entry blank.</span></span> <span data-ttu-id="f1c7c-316">그런 다음 **확인** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-316">Then click the **Confirm** button.</span></span> <span data-ttu-id="f1c7c-317">페이지 아래쪽의 출력에는 각 제품의 선택 가능성을 나타내는 JSON이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-317">The output on the bottom of the page will show the JSON representing the likelihood of each product being the choice.</span></span>

29. <span data-ttu-id="f1c7c-318">Machine Learning Studio에 필요한 요청 구조에 대 한 지침 및 몇 가지 예제가 표시 되는 새 웹 페이지가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-318">A new web page will open up, displaying the instructions and some examples about the Request structure required by the Machine Learning Studio.</span></span> <span data-ttu-id="f1c7c-319">이 페이지에 표시 된 **요청 URI** 를 메모장에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-319">Copy the **Request URI** displayed in this page, into your notepad.</span></span>

    ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-34.png)

<span data-ttu-id="f1c7c-321">이제 연간 시간 및 요일과 상관 관계가 지정 된 구매 데이터를 기반으로 판매 될 가능성이 가장 높은 제품을 제공 하는 기계 학습 시스템을 빌드 했습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-321">You have now built a machine learning system that provides the most likely product to be sold based on historical purchasing data, correlated with the time of the day and day of the year.</span></span>

<span data-ttu-id="f1c7c-322">웹 서비스를 호출 하려면 서비스 끝점에 대 한 URL과 서비스에 대 한 API 키가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-322">To call the web service, you will need the URL for the service endpoint and an API Key for the service.</span></span> <span data-ttu-id="f1c7c-323">상단 메뉴에서 **사용** 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-323">Click on the **Consume** tab, from the top menu.</span></span>

<span data-ttu-id="f1c7c-324">**소비** 정보 페이지에는 코드에서 웹 서비스를 호출 하는 데 필요한 정보가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-324">The **Consumption** Info page will display the information you will need to call the web service from your code.</span></span> <span data-ttu-id="f1c7c-325">**기본 키** 와 **요청-응답** URL의 복사본을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-325">Take a copy of the **Primary Key** and the **Request-Response** URL.</span></span> <span data-ttu-id="f1c7c-326">다음 장에서 이러한 내용이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-326">You will need these in the next Chapter.</span></span>

## <a name="chapter-5---setting-up-the-unity-project"></a><span data-ttu-id="f1c7c-327">5 장-Unity 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="f1c7c-327">Chapter 5 - Setting up the Unity Project</span></span>

<span data-ttu-id="f1c7c-328">혼합 현실 모던 헤드셋을 설정 하 고 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-328">Set up and test your Mixed Reality Immersive Headset.</span></span>

> [!NOTE]
>  <span data-ttu-id="f1c7c-329">이 과정에서는 동작 컨트롤러가 필요 **하지** 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-329">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="f1c7c-330">모던 헤드셋을 설정 하는 데 지원이 필요한 경우 [여기](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)를 클릭 하세요.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-330">If you need support setting up the Immersive Headset, please click [HERE](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="f1c7c-331">**Unity** 를 열고 **MR\_MachineLearning** 이라는 새 unity 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-331">Open **Unity** and create a new Unity Project called **MR\_MachineLearning.**</span></span> <span data-ttu-id="f1c7c-332">프로젝트 형식이 **3d**로 설정 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-332">Make sure the project type is set to **3D**.</span></span>

2.  <span data-ttu-id="f1c7c-333">Unity를 연 상태에서 기본 **스크립트 편집기** 가 **Visual Studio**로 설정 되어 있는지 확인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-333">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="f1c7c-334"> > **기본 설정** **편집** 으로 이동한 다음 새 창에서 **외부 도구**로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-334">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="f1c7c-335">**외부 스크립트 편집기** 를 **Visual Studio 2017**로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-335">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="f1c7c-336">**기본 설정** 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-336">Close the **Preferences** window.</span></span>

3.  <span data-ttu-id="f1c7c-337">그런 다음 **파일** > **빌드 설정** 으로 이동 하 고 플랫폼 ***전환*** 단추를 클릭 하 여 플랫폼을 **유니버설 Windows 플랫폼**로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-337">Next, go to **File** > **Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the ***Switch Platform*** button.</span></span>

4.  <span data-ttu-id="f1c7c-338">또한 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-338">Also make sure that:</span></span>

    1.  <span data-ttu-id="f1c7c-339">**대상 장치** 는 **임의의 장치로**설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-339">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="f1c7c-340">Microsoft HoloLens의 경우 **대상 장치** 를 *HoloLens*로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-340">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="f1c7c-341">**빌드 형식이** **D3D**로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-341">**Build Type** is set to **D3D**.</span></span>

    3.  <span data-ttu-id="f1c7c-342">**SDK** 가 **최신 설치**로 설정 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-342">**SDK** is set to **Latest installed**.</span></span>

    4.  <span data-ttu-id="f1c7c-343">**Visual Studio 버전이** **최신 설치**로 설정 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-343">**Visual Studio Version** is set to **Latest installed**.</span></span>

    5.  <span data-ttu-id="f1c7c-344">**빌드 및 실행** 이 **로컬 컴퓨터**로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-344">**Build and Run** is set to **Local Machine**.</span></span>

    6.  <span data-ttu-id="f1c7c-345">나중에 제공 되므로 지금은 **장면을** 설정 하는 것에 대해 걱정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-345">Do not worry about setting up **Scenes** right now, as these are provided later.</span></span>

    7.  <span data-ttu-id="f1c7c-346">지금은 나머지 설정이 기본값으로 유지 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-346">The remaining settings should be left as default for now.</span></span>

        ![Unity 프로젝트 설정](images/AzureLabs-Lab7-35.png)

5.  <span data-ttu-id="f1c7c-348">**빌드 설정** 창에서 **플레이어 설정** 단추를 클릭 하면 **검사기** 가 있는 공간에서 관련 패널이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-348">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span> 

6. <span data-ttu-id="f1c7c-349">이 패널에서 몇 가지 설정을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-349">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="f1c7c-350">**기타 설정** 탭에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-350">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="f1c7c-351">**스크립팅** **런타임 버전이** **실험적** 이어야 함 (.net 4.6 해당)</span><span class="sxs-lookup"><span data-stu-id="f1c7c-351">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent)</span></span>

        2. <span data-ttu-id="f1c7c-352">**Scripting 백엔드** 는 ***.net*** 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-352">**Scripting Backend** should be ***.NET***</span></span>

        3. <span data-ttu-id="f1c7c-353">**API 호환성 수준은** **.net 4.6** 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-353">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Unity 프로젝트 설정](images/AzureLabs-Lab7-36.png)

    2.  <span data-ttu-id="f1c7c-355">**게시 설정** 탭의 **기능**아래에서 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-355">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="f1c7c-356">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="f1c7c-356">**InternetClient**</span></span>

            ![Unity 프로젝트 설정](images/AzureLabs-Lab7-37.png)

    3.  <span data-ttu-id="f1c7c-358">패널의 아래쪽에서 **XR 설정** ( **게시 설정**아래에 있음), **지원 되는 틱 가상 현실**, **Windows Mixed reality SDK** 가 추가 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-358">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added</span></span>

        ![Unity 프로젝트 설정](images/AzureLabs-Lab7-38.png)

    

6.  <span data-ttu-id="f1c7c-360">**빌드 설정** 으로 돌아가서 *Unity C#*  프로젝트가 더 이상 회색으로 표시 되지 않습니다. 이 옆의 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-360">Back in **Build Settings** *Unity C#* Projects is no longer greyed out; tick the checkbox next to this.</span></span> 

7.  <span data-ttu-id="f1c7c-361">빌드 설정 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-361">Close the Build Settings window.</span></span>

8.  <span data-ttu-id="f1c7c-362">프로젝트를 저장 합니다 (**파일 > 프로젝트 저장**).</span><span class="sxs-lookup"><span data-stu-id="f1c7c-362">Save your Project (**FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a><span data-ttu-id="f1c7c-363">6 장-MLProducts Unity 패키지 가져오기</span><span class="sxs-lookup"><span data-stu-id="f1c7c-363">Chapter 6 - Importing the MLProducts Unity Package</span></span>

<span data-ttu-id="f1c7c-364">이 과정에서는 [**unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage)라고 하는 Unity 자산 패키지를 다운로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-364">For this course, you will need to download a Unity Asset Package called [**Azure-MR-307.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage).</span></span> <span data-ttu-id="f1c7c-365">이 패키지는 미리 작성 된 모든 개체를 포함 하는 장면으로 완료 되며 모든 개체를 작동 하는 데 집중할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-365">This package comes complete with a scene, with all objects in that prebuilt, so you can focus on getting it all working.</span></span> <span data-ttu-id="f1c7c-366">**ShelfKeeper** 스크립트는 제공 되지만 장면 설정 구조를 위해 공용 변수만 보유 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-366">The **ShelfKeeper** script is provided, though only holds the public variables, for the purpose of scene setup structure.</span></span> <span data-ttu-id="f1c7c-367">다른 모든 섹션을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-367">You will need to do all other sections.</span></span> 

<span data-ttu-id="f1c7c-368">이 패키지를 가져오려면:</span><span class="sxs-lookup"><span data-stu-id="f1c7c-368">To import this package:</span></span>

1.  <span data-ttu-id="f1c7c-369">앞의 Unity 대시보드를 사용 하 여 화면 위쪽의 메뉴에서 **자산** 을 클릭 한 다음 **패키지 가져오기, 사용자 지정 패키지를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-369">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package, Custom Package**.</span></span>

    ![MLProducts Unity 패키지 가져오기](images/AzureLabs-Lab7-39.png)

2.  <span data-ttu-id="f1c7c-371">파일 선택기를 사용 하 여 **unitypackage** 패키지를 선택 하 고 **열기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-371">Use the file picker to select the **Azure-MR-307.unitypackage** package and click **Open**.</span></span>

3.  <span data-ttu-id="f1c7c-372">이 자산의 구성 요소 목록이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-372">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="f1c7c-373">**가져오기를 클릭 하**여 가져오기를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-373">Confirm the import by clicking **Import**.</span></span>

    ![MLProducts Unity 패키지 가져오기](images/AzureLabs-Lab7-40.png)

4.  <span data-ttu-id="f1c7c-375">가져오기가 완료 되 면 Unity **프로젝트 패널**에 몇 가지 새 폴더가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-375">Once it has finished importing, you will notice that some new folders have appeared in your Unity **Project Panel**.</span></span> <span data-ttu-id="f1c7c-376">이러한 모델은 작업을 수행 하는 미리 작성 된 장면의 일부인 3D 모델 및 해당 재질입니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-376">Those are the 3D models and the respective materials that are part of the pre-made scene you will work on.</span></span> <span data-ttu-id="f1c7c-377">이 과정에서 대부분의 코드를 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-377">You will write the majority of the code in this course.</span></span>

    ![MLProducts Unity 패키지 가져오기](images/AzureLabs-Lab7-41.png)

5.  <span data-ttu-id="f1c7c-379">**프로젝트 패널** 폴더 내에서 **장면** 폴더를 클릭 하 고 내부 장면 ( **MR_MachineLearningScene**이라고 함)을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-379">Within the **Project Panel** folder, click on the **Scenes** folder and double click on the scene inside (called **MR_MachineLearningScene**).</span></span> <span data-ttu-id="f1c7c-380">장면이 열립니다 (아래 이미지 참조).</span><span class="sxs-lookup"><span data-stu-id="f1c7c-380">The scene will open (see image below).</span></span> <span data-ttu-id="f1c7c-381">빨간색 다이아몬드가 없는 경우 **게임 패널**의 오른쪽 위에 있는 **gizmo 그리려면** 단추를 클릭 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-381">If the red diamonds are missing, simply click the **Gizmos** button, at the top right of the **Game Panel**.</span></span>

    ![MLProducts Unity 패키지 가져오기](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a><span data-ttu-id="f1c7c-383">7 장-Unity에서 Dll 검사</span><span class="sxs-lookup"><span data-stu-id="f1c7c-383">Chapter 7 - Checking the DLLs in Unity</span></span>

<span data-ttu-id="f1c7c-384">직렬화 및 역직렬화에 사용 되는 JSON 라이브러리의 사용을 활용 하기 위해 Newtonsoft.json DLL은에서 가져온 패키지를 사용 하 여 구현 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-384">To leverage the use of JSON libraries (used for serializing and deserializing), a Newtonsoft DLL has been implemented with the package you brought in.</span></span> <span data-ttu-id="f1c7c-385">라이브러리에 올바른 구성이 있어야 합니다 (특히 코드가 작동 하지 않는 문제가 있는 경우).</span><span class="sxs-lookup"><span data-stu-id="f1c7c-385">The library should have the correct configuration, though it is worth checking (particularly if you are having issues with code not working).</span></span> 

<span data-ttu-id="f1c7c-386">이렇게 하려면</span><span class="sxs-lookup"><span data-stu-id="f1c7c-386">To do so:</span></span>

-  <span data-ttu-id="f1c7c-387">플러그 인 폴더 안의 Newtonsoft.json 파일을 마우스 왼쪽 단추를 클릭 하 고 **검사기 패널**을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-387">Left-click on the Newtonsoft file inside the Plugins folder and look at the **Inspector panel**.</span></span> <span data-ttu-id="f1c7c-388">**모든 플랫폼이** 선택 인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-388">Make sure **Any Platform** is ticked.</span></span> <span data-ttu-id="f1c7c-389">**UWP 탭** 으로 이동 하 여 **처리 안 함** 이 선택 인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-389">Go to the **UWP tab** and also ensure **Don't process** is ticked.</span></span>

    ![Unity에서 Dll 가져오기](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a><span data-ttu-id="f1c7c-391">8 장-ShelfKeeper 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="f1c7c-391">Chapter 8 - Create the ShelfKeeper class</span></span>

<span data-ttu-id="f1c7c-392">**ShelfKeeper** 클래스는 장면에서 생성 된 UI 및 제품을 제어 하는 메서드를 호스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-392">The **ShelfKeeper** class hosts methods that control the UI and products spawned in the scene.</span></span>

<span data-ttu-id="f1c7c-393">가져온 패키지의 일부로이 클래스는 완료 되지 않았지만 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-393">As part of the imported package, you will have been given this class, though it is incomplete.</span></span> <span data-ttu-id="f1c7c-394">이제 해당 클래스를 완료 하는 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-394">It is now time to complete that class:</span></span>

1.  <span data-ttu-id="f1c7c-395">**Scripts** 폴더에서 **ShelfKeeper** 스크립트를 두 번 클릭 하 여 **Visual Studio 2017**을 사용 하 여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-395">Double click on the **ShelfKeeper** script, within the **Scripts** folder, to open it with **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="f1c7c-396">스크립트에 있는 모든 코드를 다음 코드로 바꿉니다 .이 코드는 시간 및 날짜를 설정 하 고 메서드를 사용 하 여 제품을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-396">Replace all the code existing in the script with the following code, which sets the time and date and has a method to show a product.</span></span>

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

3.  <span data-ttu-id="f1c7c-397">**Unity**로 반환 하기 전에 **Visual Studio** 에서 변경 내용을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-397">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

4.  <span data-ttu-id="f1c7c-398">Unity 편집기로 돌아가서 **ShelfKeeper** 클래스가 아래와 동일한 지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-398">Back in the Unity Editor, check that the **ShelfKeeper** class looks like the below:</span></span>

    ![ShelfKeeper 클래스 만들기](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > <span data-ttu-id="f1c7c-400">스크립트에 참조 대상이 없으면 (예: *날짜 (텍스트 메시)* ) **계층 패널**에서 대상 필드로 해당 개체를 끌어 놓기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-400">If your script does not have the reference targets (i.e. *Date (Text Mesh)*), simply drag the corresponding objects from the **Hierarchy Panel**, into the target fields.</span></span> <span data-ttu-id="f1c7c-401">필요한 경우 아래에서 설명을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-401">See below for explanation, if needed:</span></span>
    > 
    > 1.  <span data-ttu-id="f1c7c-402">**ShelfKeeper** 구성 요소 스크립트를 마우스 왼쪽 단추를 클릭 하 여 **생성 지점** 배열을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-402">Open the **Spawn Point** array within the **ShelfKeeper** component script by left-clicking it.</span></span> <span data-ttu-id="f1c7c-403">하위 섹션은 배열 크기를 나타내는 **size**라는 것으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-403">A sub-section will appear called **Size**, which indicates the size of the array.</span></span> <span data-ttu-id="f1c7c-404">**크기** 옆의 텍스트 상자에 **3** 을 입력 하 고 **enter**키를 누릅니다. 그러면 아래에 세 개의 슬롯이 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-404">Type **3** into the textbox next to **Size** and press **Enter**, and three slots will be created beneath.</span></span>
    > 2. <span data-ttu-id="f1c7c-405">**계층 구조** 내에서 해당 개체 옆에 있는 화살표를 마우스 왼쪽 단추를 클릭 하 여 **시간 표시** 개체를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-405">Within the **Hierarchy** expand the **Time Display** object (by left-clicking the arrow beside it).</span></span> <span data-ttu-id="f1c7c-406">다음으로, **검사기** 가 해당 정보를 표시 하도록 **계층 구조**내에서 ***주 카메라*** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-406">Next click the ***Main Camera*** from within the **Hierarchy**, so that the **Inspector** shows its information.</span></span>
    > 3. <span data-ttu-id="f1c7c-407">**계층 패널**에서 **주 카메라** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-407">Select the **Main Camera** in the **Hierarchy Panel**.</span></span> <span data-ttu-id="f1c7c-408">**계층 패널** 의 **날짜** 및 **시간** 개체를 **ShelfKeeper** 구성 요소에 있는 **주 카메라** 의 **검사기** 내에서 **날짜 텍스트** 및 **시간 텍스트** 슬롯으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-408">Drag the **Date** and **Time** objects from the **Hierarchy Panel** to the **Date Text** and **Time Text** slots within the **Inspector** of the **Main Camera** in the **ShelfKeeper** component.</span></span>
    > 4. <span data-ttu-id="f1c7c-409">이미지에 표시 된 것 처럼 **계층 패널** ( *선반* 개체 아래)의 **생성** 지점을 **3 개의** **요소** 참조 대상으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-409">Drag the **Spawn Points** from the **Hierarchy Panel** (beneath the *Shelf* object) to the **3** **Element** reference targets beneath the **Spawn Point** array, as shown in the image.</span></span>
    > 
    >     ![ShelfKeeper 클래스 만들기](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a><span data-ttu-id="f1c7c-411">9 장-제품 예측 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="f1c7c-411">Chapter 9 - Create the ProductPrediction class</span></span>

<span data-ttu-id="f1c7c-412">만들려는 다음 클래스는 **제품 예측** 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-412">The next class you are going to create is the **ProductPrediction** class.</span></span>

<span data-ttu-id="f1c7c-413">이 클래스는 다음을 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-413">This class is responsible for:</span></span>

-   <span data-ttu-id="f1c7c-414">현재 날짜 및 시간을 제공 하 여 **Machine Learning 서비스** 인스턴스를 쿼리 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-414">Querying the **Machine Learning Service** instance, providing the current date and time.</span></span>

-   <span data-ttu-id="f1c7c-415">JSON 응답을 사용 가능한 데이터로 deserialize 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-415">Deserializing the JSON response into usable data.</span></span>

-   <span data-ttu-id="f1c7c-416">데이터 해석, 3 개의 권장 제품 검색</span><span class="sxs-lookup"><span data-stu-id="f1c7c-416">Interpreting the data, retrieving the 3 recommended products.</span></span>

-   <span data-ttu-id="f1c7c-417">**ShelfKeeper** 클래스 메서드를 호출 하 여 장면의 데이터를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-417">Calling the **ShelfKeeper** class methods to display the data in the Scene.</span></span>

<span data-ttu-id="f1c7c-418">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="f1c7c-418">To create this class:</span></span>

1.  <span data-ttu-id="f1c7c-419">**프로젝트 패널**의 **스크립트** 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-419">Go to the **Scripts** folder, in the **Project Panel**.</span></span>

2.  <span data-ttu-id="f1c7c-420">폴더 내부를 마우스 오른쪽 단추로 클릭 하 >  **C# 스크립트**를 **만듭니다** .</span><span class="sxs-lookup"><span data-stu-id="f1c7c-420">Right-click inside the folder, **Create** > **C# Script**.</span></span> <span data-ttu-id="f1c7c-421">스크립트 **제품 예측**을 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-421">Call the script **ProductPrediction**.</span></span>

3.  <span data-ttu-id="f1c7c-422">새 **제품 예측** 스크립트를 두 번 클릭 하 여 **Visual Studio 2017**에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-422">Double click on the new **ProductPrediction** script to open it with **Visual Studio 2017**.</span></span>

4.  <span data-ttu-id="f1c7c-423">**파일 수정이 검색 되었습니다** . 대화 상자가 나타나면 \***솔루션 다시 로드**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-423">If the **File Modification Detected** dialog pops up, click \***Reload Solution**.</span></span>

5.  <span data-ttu-id="f1c7c-424">제품 예측 클래스의 맨 위에 다음 네임 스페이스를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-424">Add the following namespaces to the top of the ProductPrediction class:</span></span>

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

6.  <span data-ttu-id="f1c7c-425">**제품 예측** 클래스 내에서 여러 중첩 클래스로 구성 된 다음 두 개체를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-425">Inside the **ProductPrediction** class insert the following two objects which are composed of a number of nested classes.</span></span> <span data-ttu-id="f1c7c-426">이러한 클래스는 Machine Learning 서비스에 대 한 JSON을 serialize 및 deserialize 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-426">These classes are used to serialize and deserialize the JSON for the Machine Learning Service.</span></span>

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

7.  <span data-ttu-id="f1c7c-427">그런 다음 앞의 코드 위에 다음 변수를 추가 합니다. JSON 관련 코드는 스크립트의 맨 아래, 다른 모든 코드 아래, 그 밖의 코드 아래에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-427">Then add the following variables above the previous code (so that the JSON related code is at the bottom of the script, below all other code, and out of the way):</span></span>

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
    > <span data-ttu-id="f1c7c-428">Machine Learning 포털에서 여기에 있는 **기본 키** 와 **요청-응답 끝점**을 변수에 삽입 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-428">Make sure to insert the **primary key** and **request-response endpoint**, from the Machine Learning Portal, into the variables here.</span></span> <span data-ttu-id="f1c7c-429">아래 이미지는에서 키와 끝점을 가져온 위치를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-429">The below images show where you would have taken the key and endpoint from.</span></span> 
    >  
    > ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-53-1.png)
    >
    > ![Machine Learning Studio: 실험](images/AzureLabs-Lab7-53-2.png)

8.  <span data-ttu-id="f1c7c-432">**Start ()** 메서드 내에이 코드를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-432">Insert this code within the **Start()** method.</span></span> <span data-ttu-id="f1c7c-433">**Start ()** 메서드는 클래스가 초기화 될 때 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-433">The **Start()** method is called when the class initializes:</span></span>

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

9.  <span data-ttu-id="f1c7c-434">다음은 Windows에서 날짜 및 시간을 수집 하 고이를 Machine Learning 실험에서 테이블에 저장 된 데이터와 비교 하는 데 사용할 수 있는 형식으로 변환 하는 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-434">The following is the method that collects the date and time from Windows and converts it into a format that our Machine Learning Experiment can use to compare with the data stored in the table.</span></span>

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

10. <span data-ttu-id="f1c7c-435">이 클래스는 사용 하지 않으므로 **Update ()** 메서드를 **삭제할** 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-435">You can **delete** the **Update()** method since this class will not use it.</span></span>

11. <span data-ttu-id="f1c7c-436">현재 날짜와 시간을 Machine Learning 끝점에 전달 하 고 JSON 형식으로 응답을 수신 하는 다음 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-436">Add the following method which will communicate the current date and time to the Machine Learning endpoint and receive a response in JSON format.</span></span>

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

12. <span data-ttu-id="f1c7c-437">JSON 응답을 deserialize 하 고 deserialization 결과를 **ShelfKeeper** 클래스에 전달 하는 다음 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-437">Add the following method, which is responsible for deserializing the JSON response, and communicating the result of the deserialization to the **ShelfKeeper** class.</span></span> <span data-ttu-id="f1c7c-438">이 결과는 현재 날짜 및 시간에 가장을 판매 하기 위해 예측 된 세 항목의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-438">This result will be the names of the three items predicted to sell the most at current date and time.</span></span> <span data-ttu-id="f1c7c-439">이전 메서드 아래의 **제품 예측** 클래스에 아래 코드를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-439">Insert the code below into the **ProductPrediction** class, below the previous method.</span></span>

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

13. <span data-ttu-id="f1c7c-440">**Visual Studio** 를 저장 하 고 **Unity**에 다시 헤드를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-440">Save **Visual Studio** and head back to **Unity**.</span></span>

14. <span data-ttu-id="f1c7c-441">**스크립트** 폴더의 **제품 예측** 클래스 스크립트를 **기본 카메라** 개체로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-441">Drag the **ProductPrediction** class script from the **Script** folder, onto the **Main Camera** object.</span></span>

15. <span data-ttu-id="f1c7c-442">장면 및 프로젝트 **파일** 을 저장 하 > **장면/파일** > 저장 **프로젝트**를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-442">Save your scene and project **File** > **Save Scene/File** > **Save Project**.</span></span>

## <a name="chapter-10---build-the-uwp-solution"></a><span data-ttu-id="f1c7c-443">10 장-UWP 솔루션 빌드</span><span class="sxs-lookup"><span data-stu-id="f1c7c-443">Chapter 10 - Build the UWP Solution</span></span>

<span data-ttu-id="f1c7c-444">이제 프로젝트가 독립 실행형 응용 프로그램으로 실행 될 수 있도록 프로젝트를 UWP 솔루션으로 빌드할 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-444">It is now time to build your project as a UWP solution, so that it can run as a standalone application.</span></span>

<span data-ttu-id="f1c7c-445">빌드:</span><span class="sxs-lookup"><span data-stu-id="f1c7c-445">To Build:</span></span>

1.  <span data-ttu-id="f1c7c-446">**파일** > **장면 저장**을 클릭 하 여 현재 장면을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-446">Save the current scene by clicking on **File** > **Save Scenes**.</span></span>

2.  <span data-ttu-id="f1c7c-447">**파일** > **빌드 설정** 으로 이동</span><span class="sxs-lookup"><span data-stu-id="f1c7c-447">Go to **File** > **Build Settings**</span></span>

3.  <span data-ttu-id="f1c7c-448">**Unity C# 프로젝트** 라는 상자를 선택 합니다 .이는 빌드 완료 후 클래스를 편집할 수 있도록 하기 때문에 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-448">Check the box called **Unity C# Projects** (this is important because it will allow you to edit the classes after build is completed).</span></span>

4.  <span data-ttu-id="f1c7c-449">열려 있는 **장면 추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-449">Click on **Add Open Scenes**,</span></span>

5.  <span data-ttu-id="f1c7c-450">**빌드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-450">Click **Build**.</span></span>

    ![UWP 솔루션 빌드](images/AzureLabs-Lab7-54.png)

6.  <span data-ttu-id="f1c7c-452">솔루션을 빌드하는 데 사용할 폴더를 선택 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-452">You will be prompted to select the folder where you want to build the Solution.</span></span>

7.  <span data-ttu-id="f1c7c-453">**빌드** 폴더를 만들고 해당 폴더 내에서 원하는 적절 한 이름을 사용 하 여 다른 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-453">Create a **BUILDS** folder and within that folder create another folder with an appropriate name of your choice.</span></span>

8.  <span data-ttu-id="f1c7c-454">새 폴더를 클릭 한 다음 **폴더 선택**을 클릭 하 여 해당 위치에서 빌드를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-454">Click your new folder and then click **Select Folder**, to begin the build at that location.</span></span>

    ![UWP 솔루션 빌드](images/AzureLabs-Lab7-55.png)

    ![UWP 솔루션 빌드](images/AzureLabs-Lab7-56.png)

9.  <span data-ttu-id="f1c7c-457">Unity가 빌드를 완료 하면 (시간이 걸릴 수 있음) 빌드 위치에서 **파일 탐색기** 창이 열립니다. (작업 표시줄은 항상 창 위에 표시 되는 것은 아니지만 새 창 추가를 알려 줍니다.)</span><span class="sxs-lookup"><span data-stu-id="f1c7c-457">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-11---deploy-your-application"></a><span data-ttu-id="f1c7c-458">11 장-응용 프로그램 배포</span><span class="sxs-lookup"><span data-stu-id="f1c7c-458">Chapter 11 - Deploy your Application</span></span>

<span data-ttu-id="f1c7c-459">응용 프로그램을 배포 하려면:</span><span class="sxs-lookup"><span data-stu-id="f1c7c-459">To deploy your application:</span></span>

1.  <span data-ttu-id="f1c7c-460">새 Unity 빌드 ( **앱** 폴더)로 이동 하 여 **Visual Studio**에서 솔루션 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-460">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

2.  <span data-ttu-id="f1c7c-461">Visual Studio를 연 상태에서 MachineLearningLab_Build 솔루션을 마우스 오른쪽 단추로 클릭 하 고 (Visual Studio의 오른쪽에 있음) 솔루션 탐색기에서 NuGet 패키지 복원을 클릭 하 여 수행할 수 있는 NuGet 패키지를 복원 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-461">With Visual Studio open, you need to Restore NuGet Packages, which can be done through right-clicking your MachineLearningLab_Build solution, from the Solution Explorer (found to the right of Visual Studio), and then clicking Restore NuGet Packages:</span></span>

    ![NuGet 패키지 추가](images/AzureLabs-Lab7-57.png)

3.  <span data-ttu-id="f1c7c-463">솔루션 구성에서 **디버그**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-463">In the Solution Configuration select **Debug**.</span></span>

4.  <span data-ttu-id="f1c7c-464">솔루션 플랫폼에서 **x86**, **로컬 컴퓨터**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-464">In the Solution Platform, select **x86**, **Local Machine**.</span></span> 

    > <span data-ttu-id="f1c7c-465">Microsoft HoloLens의 경우 컴퓨터에 테더 링 된 하지 않도록 *원격 컴퓨터*를 설정 하는 것이 더 쉬울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-465">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="f1c7c-466">그러나 다음을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-466">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="f1c7c-467">HoloLens의 **IP 주소** 를 알고 있습니다. *설정 > 네트워크 & 인터넷 > Wi-fi > 고급 옵션*에서 찾을 수 있습니다. IPv4는 사용 해야 하는 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-467">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="f1c7c-468">**개발자 모드가** **설정**되어 있는지 확인 합니다. *개발자를 위한 업데이트 & 보안 > > 설정*에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-468">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![NuGet 패키지 추가](images/AzureLabs-Lab7-58.png)

5.  <span data-ttu-id="f1c7c-470">**빌드 메뉴로** 이동 하 여 **솔루션 배포** 를 클릭 하 여 응용 프로그램을 PC에 테스트용으로 로드.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-470">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your PC.</span></span>

6.  <span data-ttu-id="f1c7c-471">이제 앱이 설치 된 앱 목록에 표시 되어 시작 될 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-471">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

<span data-ttu-id="f1c7c-472">Mixed Reality 응용 프로그램을 실행 하는 경우 Unity 장면에 설정 된 도구를 볼 수 있으며, 초기화에서 Azure 내에 설정 된 데이터가 인출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-472">When you run the Mixed Reality application, you will see the bench that was set up in your Unity scene, and from initialization, the data you set up within Azure will be fetched.</span></span> <span data-ttu-id="f1c7c-473">데이터는 응용 프로그램 내에서 deserialize 되며, 현재 날짜 및 시간에 대 한 세 가지 상위 결과가 시각적으로 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-473">The data will be deserialized within your application, and the three top results for your current date and time will be provided visually, as three models on the bench.</span></span>


## <a name="your-finished-machine-learning-application"></a><span data-ttu-id="f1c7c-474">완성 된 Machine Learning 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="f1c7c-474">Your finished Machine Learning application</span></span>
 
<span data-ttu-id="f1c7c-475">축 하 합니다. Azure Machine Learning를 활용 하 여 데이터 예측을 만들고 장면에 표시 하는 혼합 현실 앱을 빌드 했습니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-475">Congratulations, you built a mixed reality app that leverages the Azure Machine Learning to make data predictions and display it on your scene.</span></span>

![NuGet 패키지 추가](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a><span data-ttu-id="f1c7c-477">조사할</span><span class="sxs-lookup"><span data-stu-id="f1c7c-477">Exercise</span></span>

<span data-ttu-id="f1c7c-478">**연습 1**</span><span class="sxs-lookup"><span data-stu-id="f1c7c-478">**Exercise 1**</span></span>

<span data-ttu-id="f1c7c-479">응용 프로그램의 정렬 순서를 실험 하 고이 데이터가 유용할 수 있으므로 세 개의 하위 예측이 선반에 표시 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-479">Experiment with the sort order of your application and have the three bottom predictions appear on the shelf, as this data would potentially be useful also.</span></span>

<span data-ttu-id="f1c7c-480">**연습 2**</span><span class="sxs-lookup"><span data-stu-id="f1c7c-480">**Exercise 2**</span></span>

<span data-ttu-id="f1c7c-481">**Azure 테이블** 을 사용 하 여 새 테이블에 날씨 정보를 채우고 데이터를 사용 하 여 새 실험을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f1c7c-481">Using **Azure Tables** populate a new table with weather information and create a new experiment using the data.</span></span>
