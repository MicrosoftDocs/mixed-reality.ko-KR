---
title: MR, Azure 308부터-장치 간 알림
description: 혼합된 현실 응용 프로그램에서 Azure Notification Hubs, Azure Functions 및 Azure Storage 및 테이블을 구현 하는 방법을 알아보려면이 과정을 완료 합니다.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 혼합 현실, academy, unity, 자습서, api, 알림, 함수, 테이블, notification hubs를 몰입 형, hololens, vr
ms.openlocfilehash: 3b6e930acd81c7d6e3addc107ec0da605d38cad1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694609"
---
>[!NOTE]
><span data-ttu-id="10ad9-104">혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="10ad9-105">따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="10ad9-106">이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="10ad9-107">지원 되는 장치에서 작업을 계속 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="10ad9-108">새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="10ad9-109">게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-308-cross-device-notifications"></a><span data-ttu-id="10ad9-110">MR 및 Azure 308: 장치 간 알림</span><span class="sxs-lookup"><span data-stu-id="10ad9-110">MR and Azure 308: Cross-device notifications</span></span>

![최종 제품-시작](images/AzureLabs-Lab8-00.png)

<span data-ttu-id="10ad9-112">이 과정에서는 Azure Notification Hubs, Azure Tables 및 Azure Functions를 사용 하 여 혼합된 현실 응용 프로그램에 Notification Hubs 기능을 추가 하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-112">In this course, you will learn how to add Notification Hubs capabilities to a mixed reality application using Azure Notification Hubs, Azure Tables, and Azure Functions.</span></span>

<span data-ttu-id="10ad9-113">**Azure Notification Hubs** 는 개발자가 모든 플랫폼에서 클라우드 내에서 모든 전원이 대상 및 개인 설정 된 푸시 알림을 보낼 수 있는 Microsoft 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-113">**Azure Notification Hubs** is a Microsoft service, which allows developers to send targeted and personalized push notifications to any platform, all powered within the cloud.</span></span> <span data-ttu-id="10ad9-114">효과적으로 최종 사용자와 통신 하는 개발자를 허용 또는 시나리오에 따라 다양 한 응용 프로그램 간의 통신도 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-114">This can effectively allow developers to communicate with end users, or even communicate between various applications, depending on the scenario.</span></span> <span data-ttu-id="10ad9-115">자세한 내용은 참조는 **Azure Notification Hubs** [페이지](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview)합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-115">For more information, visit the **Azure Notification Hubs** [page](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview).</span></span>

<span data-ttu-id="10ad9-116">**Azure Functions** 작은 코드를 실행 하기 위해 개발자를 허용 하는 Microsoft 서비스에 '', Azure에서 functions 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-116">**Azure Functions** is a Microsoft service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="10ad9-117">다양 한 이점을 가질 수 있는 로컬 응용 프로그램 보다는 클라우드의 작업을 위임 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-117">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="10ad9-118">**Azure Functions** C를 비롯 한 여러 개발 언어를 지 원하는\#, F\#, Node.js, Java 및 PHP 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-118">**Azure Functions** supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="10ad9-119">자세한 내용은 참조는 **Azure Functions** [페이지](https://docs.microsoft.com/azure/azure-functions/functions-overview)합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-119">For more information, visit the **Azure Functions** [page](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="10ad9-120">**Azure 테이블** 는 클라우드에 구조화 된 비 SQL 데이터를 저장 하는 개발자를 허용 하는 Microsoft 클라우드 서비스를 쉽게 액세스할 수 있도록 어디서 나 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-120">**Azure Tables** is a Microsoft cloud service, which allows developers to store structured non-SQL data in the cloud, making it easily accessible anywhere.</span></span> <span data-ttu-id="10ad9-121">서비스 소재 필요에 따라 테이블의 발전에 대 한 허용, 스키마 없이 디자인 되어 있으므로 매우 유연 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-121">The service boasts a schemaless design, allowing for the evolution of tables as needed, and thus is very flexible.</span></span> <span data-ttu-id="10ad9-122">자세한 내용은 참조는 **Azure Tables** [페이지](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span><span class="sxs-lookup"><span data-stu-id="10ad9-122">For more information, visit the **Azure Tables** [page](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span></span>

<span data-ttu-id="10ad9-123">이 과정을 완료 해야 혼합된 현실 헤드셋 몰입 형 응용 프로그램 및 데스크톱 PC는 응용 프로그램을, 다음을 수행할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-123">Having completed this course, you will have a mixed reality immersive headset application, and a Desktop PC application, which will be able to do the following:</span></span>

1. <span data-ttu-id="10ad9-124">데스크톱 PC 앱에서는 사용자 (X, Y)으로 2D 공간에서 개체를 이동 하려면 마우스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-124">The Desktop PC app will allow the user to move an object in 2D space (X and Y), using the mouse.</span></span>

2. <span data-ttu-id="10ad9-125">PC 앱 내에서 개체의 이동 문자열의 형태로 될 JSON을 사용 하 여, 형식, 개체 ID를 포함 하는 클라우드로 전송 되 고 정보 (X 및 Y 좌표)을 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-125">The movement of objects within the PC app will be sent to the cloud using JSON, which will be in the form of a string, containing an object ID, type, and transform information (X and Y coordinates).</span></span> 

3. <span data-ttu-id="10ad9-126">혼합된 현실 앱, 데스크톱 앱에는 동일한 장면에 Notification Hubs 서비스 (업데이트 된 데스크톱 PC 앱에서)에서 개체 이동에 대 한 알림을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-126">The mixed reality app, which has an identical scene to the desktop app, will receive notifications regarding object movement, from the Notification Hubs service (which has just been updated by the Desktop PC app).</span></span> 

4. <span data-ttu-id="10ad9-127">개체 ID, 형식 및 변환 정보를 포함 될, 알림을 받으면 혼합된 현실 앱 자체 장면에 받은 정보를 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-127">Upon receiving a notification, which will contain the object ID, type, and transform information, the mixed reality app will apply the received information to its own scene.</span></span>

<span data-ttu-id="10ad9-128">응용 프로그램에서는 사용자의 몫 디자인을 사용 하 여 결과에서는 통합 하는 방법에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-128">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="10ad9-129">이 과정은 Unity 프로젝트를 사용 하 여 Azure 서비스를 통합 하는 방법을 알려 주기 위해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-129">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="10ad9-130">혼합된 현실 응용 프로그램을 강화 하기 위해이 과정에서 얻는 지식을 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-130">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span> <span data-ttu-id="10ad9-131">이 과정은 다른 혼합 현실 Labs를 직접 포함 하지 않는 자체 포함 된 자습서입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-131">This course is a self-contained tutorial, which does not directly involve any other Mixed Reality Labs.</span></span>

## <a name="device-support"></a><span data-ttu-id="10ad9-132">장치 지원</span><span class="sxs-lookup"><span data-stu-id="10ad9-132">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="10ad9-133">과정</span><span class="sxs-lookup"><span data-stu-id="10ad9-133">Course</span></span></th><th style="width:150px"> <span data-ttu-id="10ad9-134"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="10ad9-134"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="10ad9-135"><a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="10ad9-135"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="10ad9-136">MR 및 Azure 308: 장치 간 알림</span><span class="sxs-lookup"><span data-stu-id="10ad9-136">MR and Azure 308: Cross-device notifications</span></span></td><td style="text-align: center;"> <span data-ttu-id="10ad9-137">✔️</span><span class="sxs-lookup"><span data-stu-id="10ad9-137">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="10ad9-138">✔️</span><span class="sxs-lookup"><span data-stu-id="10ad9-138">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="10ad9-139">이 코스는 주로 Windows Mixed Reality 몰입 형 (VR) 헤드셋 주력, Microsoft HoloLens이 과정에서 배운 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-139">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="10ad9-140">과정을 따라가려면 정보 HoloLens를 지원 하기 위해 사용 해야 합니다. 변경 내용에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-140">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="10ad9-141">HoloLens를 사용 하는 경우 음성 캡처하는 동안 일부 echo를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-141">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="10ad9-142">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="10ad9-142">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="10ad9-143">이 자습서는 Unity 사용 하 여 기본 경험이 있는 개발자 용으로 설계 하 고 C#입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-143">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="10ad9-144">또한 주의 필수 구성 요소 및이 문서에서 작성 된 지침을 나타내는 새로운 테스트 되었으며 (2018 년 5 월) 작성 시점에 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-144">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="10ad9-145">내에서 나열 된 사용 가능한 최신 소프트웨어를 사용 하는 합니다 [도구를 설치](install-the-tools.md) 없습니다 가정이 과정에서 정보를 아래에 나열 된 보다 최신 소프트웨어에서 찾을 수 있는 항목을 일치 완벽 하 게 됩니다 있지만 문서 .</span><span class="sxs-lookup"><span data-stu-id="10ad9-145">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="10ad9-146">다음 하드웨어 및 소프트웨어가이 과정에 대 한 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-146">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="10ad9-147">개발 PC A [Windows Mixed Reality 호환](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 몰입 형 (VR) 헤드셋 개발용</span><span class="sxs-lookup"><span data-stu-id="10ad9-147">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="10ad9-148">Windows 10 Fall Creators Update (또는 이상) 사용 하도록 설정 하는 개발자 모드를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="10ad9-148">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="10ad9-149">최신 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="10ad9-149">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="10ad9-150">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="10ad9-150">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="10ad9-151">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="10ad9-151">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="10ad9-152">A [Windows Mixed Reality 몰입 형 (VR) 헤드셋](immersive-headset-hardware-details.md) 하거나 [Microsoft HoloLens](hololens-hardware-details.md) 개발자 모드를 설정 하 여</span><span class="sxs-lookup"><span data-stu-id="10ad9-152">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="10ad9-153">Azure 설정에 대 한 알림 허브에 액세스 하려면 인터넷 액세스</span><span class="sxs-lookup"><span data-stu-id="10ad9-153">Internet access for Azure setup and to access Notification Hubs</span></span>

## <a name="before-you-start"></a><span data-ttu-id="10ad9-154">시작하기 전 주의 사항</span><span class="sxs-lookup"><span data-stu-id="10ad9-154">Before you start</span></span>

- <span data-ttu-id="10ad9-155">이 프로젝트를 구축 하는 문제 발생을 방지 하려면 것이 좋습니다 루트 또는 루트 거의 폴더에이 자습서에 언급 된 프로젝트를 만든 (오래 폴더 경로 빌드 시에는 문제가 발생할 수 있습니다).</span><span class="sxs-lookup"><span data-stu-id="10ad9-155">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
- <span data-ttu-id="10ad9-156">Microsoft 개발자 포털 및 응용 프로그램 등록 포털의 소유자 여야 합니다, 그렇지 않으면 있습니다 응용 프로그램에 액세스할 수 있는 권한이 [Chapter 2](#chapter-2---retrieve-your-new-apps-credentials)합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-156">You must be the owner of your Microsoft Developer Portal and your Application Registration Portal, otherwise you will not have permission to access the app in [Chapter 2](#chapter-2---retrieve-your-new-apps-credentials).</span></span>

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a><span data-ttu-id="10ad9-157">장 1-Microsoft 개발자 포털에서 응용 프로그램 만들기</span><span class="sxs-lookup"><span data-stu-id="10ad9-157">Chapter 1 - Create an application on the Microsoft Developer Portal</span></span>

<span data-ttu-id="10ad9-158">사용 하 여 **Azure Notification Hubs** 서비스 해야 Microsoft 개발자 포털에서 응용 프로그램을 만들려면 응용 프로그램을 보내고 알림을 받을 수 있도록 등록 해야 하는 대로 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-158">To use the **Azure Notification Hubs** Service, you will need to create an Application on the Microsoft Developer Portal, as your application will need to be registered, so that it can send and receive notifications.</span></span>

1.  <span data-ttu-id="10ad9-159">에 로그인 합니다 [Microsoft 개발자 포털](https://developer.microsoft.com/dashboard)합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-159">Log in to the [Microsoft Developer Portal](https://developer.microsoft.com/dashboard).</span></span>

    > <span data-ttu-id="10ad9-160">Microsoft 계정에 로그인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-160">You will need to log in to your Microsoft Account.</span></span>

2.  <span data-ttu-id="10ad9-161">대시보드에서 클릭 **새 앱 만들기**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-161">From the Dashboard, click **Create a new app**.</span></span>

    ![앱 만들기](images/AzureLabs-Lab8-01.png)

3.  <span data-ttu-id="10ad9-163">새 앱 이름 예약 해야 하는 여기서 팝업 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-163">A popup will appear, wherein you need to reserve a name for your new app.</span></span> <span data-ttu-id="10ad9-164">텍스트 상자에 적절 한 이름을; 삽입 선택한 이름 사용 가능한 경우 입력란의 오른쪽에는 눈금 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-164">In the textbox, insert an appropriate name; if the chosen name is available, a tick will appear to the right of the textbox.</span></span> <span data-ttu-id="10ad9-165">삽입 하는 사용 가능한 이름을 만든 후 클릭 합니다 **제품 이름 예약** 팝업의 왼쪽 아래에는 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-165">Once you have an available name inserted, click the **Reserve product name** button to the bottom left of the popup.</span></span>

    ![역방향 이름](images/AzureLabs-Lab8-02.png)

4.  <span data-ttu-id="10ad9-167">이제 만든 앱을 다음 장에서 이동할 준비가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-167">With the app now created, you are ready to move to the next Chapter.</span></span>

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a><span data-ttu-id="10ad9-168">새 앱 자격 증명을 검색 하는-2 장</span><span class="sxs-lookup"><span data-stu-id="10ad9-168">Chapter 2 - Retrieve your new apps credentials</span></span>

<span data-ttu-id="10ad9-169">여기서 새 앱 나열 됩니다 하 고 설치 프로그램에 사용 되는 자격 증명을 검색할 응용 프로그램 등록 포털에 로그인 합니다 **Notification Hubs 서비스** 내 합니다 **Azure Portal**.</span><span class="sxs-lookup"><span data-stu-id="10ad9-169">Log into the Application Registration Portal, where your new app will be listed, and retrieve the credentials which will be used to setup the **Notification Hubs Service** within the **Azure Portal**.</span></span>

1.  <span data-ttu-id="10ad9-170">로 이동 합니다 [응용 프로그램 등록 포털](http://apps.dev.microsoft.com)합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-170">Navigate to the [Application Registration Portal](http://apps.dev.microsoft.com).</span></span>

    ![응용 프로그램 등록 포털](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > <span data-ttu-id="10ad9-172">로그인 하려면 Microsoft 계정을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-172">You will need to use your Microsoft Account to Login.</span></span>  
    > <span data-ttu-id="10ad9-173">이 **해야 합니다** 이전에 사용한 Microsoft 계정 [장](#chapter-1---create-an-application-on-the-microsoft-developer-portal), Windows 스토어 개발자 포털을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-173">This **must** be the Microsoft Account which you used in the previous [Chapter](#chapter-1---create-an-application-on-the-microsoft-developer-portal), with the Windows Store Developer portal.</span></span>

2.  <span data-ttu-id="10ad9-174">응용 프로그램을 보면 합니다 **내 응용 프로그램** 섹션입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-174">You will find your app under the **My applications** section.</span></span> <span data-ttu-id="10ad9-175">을 찾은 후 클릭 하 고 앱이 있는 새 페이지로 이동 됩니다 이름 더하기 **등록**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-175">Once you have found it, click on it and you will be taken to a new page which has the app name plus **Registration**.</span></span>

    ![새로 등록 된 앱](images/AzureLabs-Lab8-04.png)

3.  <span data-ttu-id="10ad9-177">검색할 등록 페이지를 아래로 스크롤하여 사용자 **응용 프로그램 비밀** 섹션 및 **패키지 SID** 앱에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-177">Scroll down the registration page to find your **Application Secrets** section and the **Package SID** for your app.</span></span> <span data-ttu-id="10ad9-178">설정 사용에 대 한 모두 복사 합니다 **Azure Notification Hubs 서비스** 다음 장에서 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-178">Copy both for use with setting up the **Azure Notification Hubs Service** in the next Chapter.</span></span>

    ![응용 프로그램 비밀](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a><span data-ttu-id="10ad9-180">Azure Portal 설치-3 장: Notification Hubs 서비스 만들기</span><span class="sxs-lookup"><span data-stu-id="10ad9-180">Chapter 3 - Setup Azure Portal: create Notification Hubs Service</span></span>

<span data-ttu-id="10ad9-181">앱 자격 증명을 사용 하 여 검색 해야 Azure Notification Hubs 서비스를 만들려는 Azure Portal로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-181">With your apps credentials retrieved, you will need to go to the Azure Portal, where you will create an Azure Notification Hubs Service.</span></span>

1.  <span data-ttu-id="10ad9-182">에 로그인 합니다 [Azure Portal](https://portal.azure.com)합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-182">Log into the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE] 
    > <span data-ttu-id="10ad9-183">Azure 계정이 아직 없는 경우 새로 만들려면 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-183">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="10ad9-184">클래스 룸 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 새 계정 설정 도움말에 대 한 여력 중 하나를 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-184">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="10ad9-185">일단 로그인 하면 클릭할 **새로 만들기** 왼쪽 위에서 모서리 및 검색 **알림 허브**를 클릭 하 고 ***Enter***합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-185">Once you are logged in, click on **New** in the top left corner, and search for **Notification Hub**, and click ***Enter***.</span></span>

    ![알림 허브에 대 한 검색](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > <span data-ttu-id="10ad9-187">단어 ***새로 만들기*** 로 대체 되었습니다 **리소스 만들기**, 최신 포털에서입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-187">The word ***New*** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="10ad9-188">새 페이지에 대 한 설명을 제공 합니다는 *Notification Hubs* 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-188">The new page will provide a description of the *Notification Hubs* service.</span></span> <span data-ttu-id="10ad9-189">선택이 프롬프트의 왼쪽 아래에 있는 합니다 **만들기** 이 서비스를 사용 하 여 연결을 만들려면 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-189">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![notification hubs 인스턴스 만들기](images/AzureLabs-Lab8-07.png)

4.  <span data-ttu-id="10ad9-191">클릭 한 후 ***만들기***:</span><span class="sxs-lookup"><span data-stu-id="10ad9-191">Once you have clicked on ***Create***:</span></span>

    1.  <span data-ttu-id="10ad9-192">이 서비스 인스턴스에 대해 원하는 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-192">Insert your desired name for this service instance.</span></span>

    2.  <span data-ttu-id="10ad9-193">제공 된 **네임 스페이스** 이 앱과 연결할 수는 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-193">Provide a **namespace** which you will be able to associate with this app.</span></span>

    3.  <span data-ttu-id="10ad9-194">선택 된 **위치 합니다.**</span><span class="sxs-lookup"><span data-stu-id="10ad9-194">Select a **Location.**</span></span>

    4.  <span data-ttu-id="10ad9-195">선택 된 **리소스 그룹** 하거나 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-195">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="10ad9-196">리소스 그룹에는 모니터링, 프로 비전, 액세스 제어 및 Azure 자산 모음에 대 한 청구를 관리 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-196">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="10ad9-197">것이 좋습니다 (예: 이러한 labs)와 같은 일반적인 리소스 그룹에서 단일 프로젝트와 연결 된 모든 Azure 서비스를 유지).</span><span class="sxs-lookup"><span data-stu-id="10ad9-197">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="10ad9-198">추가 하려는 경우 Azure 리소스 그룹에 대 한 따르세요이 [리소스 그룹을 관리 하는 방법에 대 한 링크](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-198">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span> 

    5.  <span data-ttu-id="10ad9-199">적절 한 선택 **구독**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-199">Select an appropriate **Subscription**.</span></span>

    6.  <span data-ttu-id="10ad9-200">이 서비스에 적용 되는 조건에 이해는 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-200">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7. <span data-ttu-id="10ad9-201">**만들기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-201">Select **Create**.</span></span>

        ![서비스 세부 정보 입력](images/AzureLabs-Lab8-08.png)

5.  <span data-ttu-id="10ad9-203">클릭 한 후 **만들기**만들려는 서비스에 대 한 대기 해야, 1 분이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-203">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="10ad9-204">서비스 인스턴스가 생성 되 면 포털에서 알림이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-204">A notification will appear in the portal once the Service instance is created.</span></span>

    ![알림(notification)](images/AzureLabs-Lab8-09.png)

7.  <span data-ttu-id="10ad9-206">클릭 합니다 **리소스로 이동** 알림에서 새 서비스 인스턴스를 탐색 하는 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-206">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="10ad9-207">이동에서 새 **알림 허브** 서비스 인스턴스.</span><span class="sxs-lookup"><span data-stu-id="10ad9-207">You will be taken to your new **Notification Hub** service instance.</span></span>

    ![리소스로 이동](images/AzureLabs-Lab8-10.png)
    
8.  <span data-ttu-id="10ad9-209">페이지 아래쪽의 중간 개요 페이지에서 클릭 **Windows (WNS).**</span><span class="sxs-lookup"><span data-stu-id="10ad9-209">From the overview page, halfway down the page, click **Windows (WNS).**</span></span> <span data-ttu-id="10ad9-210">오른쪽 패널을 필요로 하는 텍스트 필드를 두 표시로 변경 됩니다 하 **패키지 SID** 하 고 **보안 키**, 이전에 설정한 앱에서.</span><span class="sxs-lookup"><span data-stu-id="10ad9-210">The panel on the right will change to show two text fields, which require your **Package SID** and **Security Key**, from the app you set up previously.</span></span>

    ![새로 만든 허브 서비스](images/AzureLabs-Lab8-11.png)

9. <span data-ttu-id="10ad9-212">올바른 필드에 세부 정보를 복사한 후 클릭 **저장할**, 알림 허브 업데이트 되었을 때 알림을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-212">Once you have copied the details into the correct fields, click **Save**, and you will receive a notification when the Notification Hub has been successfully updated.</span></span>

    ![보안 세부 정보 복사](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a><span data-ttu-id="10ad9-214">Azure Portal 설치-4 장: Table Service 만들기</span><span class="sxs-lookup"><span data-stu-id="10ad9-214">Chapter 4 - Setup Azure Portal: create Table Service</span></span>

<span data-ttu-id="10ad9-215">Notification Hubs 서비스 인스턴스를 만든 후 Azure Portal에서 저장소 리소스를 만들어 Azure 테이블 서비스를 만들로 다시 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-215">After creating your Notification Hubs Service instance, navigate back to your Azure Portal, where you will create an Azure Tables Service by creating a Storage Resource.</span></span>

1.  <span data-ttu-id="10ad9-216">아직 로그인 하지 않은, 경우에 로그인 합니다 [Azure Portal](https://portal.azure.com)합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-216">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2.  <span data-ttu-id="10ad9-217">로그인 되 면 클릭 **새로 만들기** 왼쪽 위에서 모서리 및 검색 **저장소 계정**를 클릭 하 고 **Enter**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-217">Once logged in, click on **New** in the top left corner, and search for **Storage account**, and click **Enter**.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="10ad9-218">단어 ***새로 만들기*** 로 대체 되었습니다 **리소스 만들기**, 최신 포털에서입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-218">The word ***New*** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="10ad9-219">선택 **저장소 계정-blob, 파일, 테이블, 큐** 목록에서.</span><span class="sxs-lookup"><span data-stu-id="10ad9-219">Select **Storage account - blob, file, table, queue** from the list.</span></span>

    ![저장소 계정에 대 한 검색](images/AzureLabs-Lab8-13.png)

4.  <span data-ttu-id="10ad9-221">새 페이지에 대 한 설명을 제공 합니다는 **저장소 계정** 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-221">The new page will provide a description of the **Storage account** service.</span></span> <span data-ttu-id="10ad9-222">선택이 프롬프트의 왼쪽 아래에 있는 합니다 **만들기** 단추,이 서비스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-222">At the bottom left of this prompt, select the **Create** button, to create an instance of this service.</span></span>

    ![저장소 인스턴스 만들기](images/AzureLabs-Lab8-14.png)

5.  <span data-ttu-id="10ad9-224">클릭 한 후 **만들기**를 패널에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-224">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="10ad9-225">원하는 삽입 **이름을** (모두 소문자 여야 함)이 서비스 인스턴스에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-225">Insert your desired **Name** for this service instance (must be all lowercase).</span></span>

    2. <span data-ttu-id="10ad9-226">에 대 한 **배포 모델**, 클릭 **Resource manager**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-226">For **Deployment model**, click **Resource manager**.</span></span>

    3.  <span data-ttu-id="10ad9-227">에 대 한 **계정 종류**, 선택 드롭다운 메뉴를 사용 하 여 **저장소 (범용 v1)** 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-227">For **Account kind**, using the dropdown menu, select **Storage (general purpose v1)**.</span></span>

    4. <span data-ttu-id="10ad9-228">적절 한 선택 **위치**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-228">Select an appropriate **Location**.</span></span>
    
    5.  <span data-ttu-id="10ad9-229">에 대 한 합니다 **복제** 드롭다운 메뉴에서 **읽기-액세스-지역 중복 저장소 (RA-GRS)** 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-229">For the **Replication** dropdown menu, select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6.  <span data-ttu-id="10ad9-230">에 대 한 **성능**, 클릭 **표준**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-230">For **Performance**, click **Standard**.</span></span>

    7.  <span data-ttu-id="10ad9-231">내 합니다 **보안 전송 필요** 섹션에서 **비활성화**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-231">Within the **Secure transfer required** section, select **Disabled**.</span></span>

    8.  <span data-ttu-id="10ad9-232">**구독** 드롭다운 메뉴에서 적절 한 구독을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-232">From the **Subscription** dropdown menu, select an appropriate subscription.</span></span>

    9.  <span data-ttu-id="10ad9-233">선택 된 **리소스 그룹** 하거나 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-233">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="10ad9-234">리소스 그룹에는 모니터링, 프로 비전, 액세스 제어 및 Azure 자산 모음에 대 한 청구를 관리 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-234">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="10ad9-235">것이 좋습니다 (예: 이러한 labs)와 같은 일반적인 리소스 그룹에서 단일 프로젝트와 연결 된 모든 Azure 서비스를 유지).</span><span class="sxs-lookup"><span data-stu-id="10ad9-235">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="10ad9-236">추가 하려는 경우 Azure 리소스 그룹에 대 한 따르세요이 [리소스 그룹을 관리 하는 방법에 대 한 링크](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-236">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="10ad9-237">둡니다 **가상 네트워크** 으로 **비활성** 선택할 경우.</span><span class="sxs-lookup"><span data-stu-id="10ad9-237">Leave **Virtual networks** as **Disabled** if this is an option for you.</span></span>

    11. <span data-ttu-id="10ad9-238">**만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-238">Click **Create**.</span></span>

        ![저장소 세부 정보 입력](images/AzureLabs-Lab8-15.png)

6.  <span data-ttu-id="10ad9-240">클릭 한 후 **만들기**만들려는 서비스에 대 한 대기 해야, 1 분이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-240">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="10ad9-241">서비스 인스턴스가 생성 되 면 포털에서 알림이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-241">A notification will appear in the portal once the Service instance is created.</span></span> <span data-ttu-id="10ad9-242">새 서비스 인스턴스를 탐색 하려면 알림을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-242">Click on the notifications to explore your new Service instance.</span></span>

    ![새 저장소 알림](images/AzureLabs-Lab8-16.png)

8.  <span data-ttu-id="10ad9-244">클릭 합니다 **리소스로 이동** 알림에서 새 서비스 인스턴스를 탐색 하는 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-244">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="10ad9-245">새 저장소 서비스 인스턴스 개요 페이지로 이동 수는 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-245">You will be taken to your new Storage Service instance overview page.</span></span>

    ![리소스로 이동](images/AzureLabs-Lab8-17.PNG)

9. <span data-ttu-id="10ad9-247">개요 페이지를 오른쪽에서 클릭 **테이블**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-247">From the overview page, to the right-hand side, click **Tables**.</span></span>
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. <span data-ttu-id="10ad9-248">오른쪽 패널을 표시 하도록 변경 됩니다 합니다 **테이블 서비스** 정보, 여기서 새 테이블을 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-248">The panel on the right will change to show the **Table service** information, wherein you need to add a new table.</span></span> <span data-ttu-id="10ad9-249">클릭 하 여이 작업을 수행 합니다 **+** **테이블** 왼쪽 위 모퉁이에 있는 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-249">Do this by clicking the **+** **Table** button to the top-left corner.</span></span>

    ![테이블 열기](images/AzureLabs-Lab8-19.png)

11. <span data-ttu-id="10ad9-251">새 페이지가 표시 될 입력 해야 하는 여기서는 **테이블 이름**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-251">A new page will be shown, wherein you need to enter a **Table name**.</span></span> <span data-ttu-id="10ad9-252">뒷부분에서 응용 프로그램에서 데이터를 참조 하는 데 사용할 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-252">This is the name you will use to refer to the data in your application in later Chapters.</span></span> <span data-ttu-id="10ad9-253">적절 한 이름을 삽입 하 고 클릭 **확인**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-253">Insert an appropriate name and click **OK**.</span></span>

    ![새 테이블 만들기](images/AzureLabs-Lab8-20.png)    

12. <span data-ttu-id="10ad9-255">새 테이블을 만든 후에 내에서 볼 수는 합니다 **테이블 서비스** 페이지 (아래쪽).</span><span class="sxs-lookup"><span data-stu-id="10ad9-255">Once the new table has been created, you will be able to see it within the **Table service** page (at the bottom).</span></span>

    ![만든 새 테이블](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a><span data-ttu-id="10ad9-257">5 장-Visual Studio에서 Azure 테이블을 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-257">Chapter 5 - Completing the Azure Table in Visual Studio</span></span>

<span data-ttu-id="10ad9-258">이제 프로그램 **테이블 서비스** 저장소 계정에 설치 되어, 정보 저장 및 검색에 사용 되는 데이터를 추가할 차례입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-258">Now that your **Table service** storage account has been setup, it is time to add data to it, which will be used to store and retrieve information.</span></span> <span data-ttu-id="10ad9-259">테이블에 대 한 편집을 통해 수행할 수 있습니다 **Visual Studio**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-259">The editing of your Tables can be done through **Visual Studio**.</span></span>

1.  <span data-ttu-id="10ad9-260">오픈 **Visual Studio**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-260">Open **Visual Studio**.</span></span>

2.  <span data-ttu-id="10ad9-261">메뉴에서 클릭 **뷰** > **클라우드 탐색기**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-261">From the menu, click **View** > **Cloud Explorer**.</span></span>

    ![클라우드 탐색기를 열으십시오](images/AzureLabs-Lab8-22.png)

3.  <span data-ttu-id="10ad9-263">합니다 **클라우드 탐색기** 열립니다 도킹 된 항목으로 일 환자, 대로 로드 시간이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-263">The **Cloud Explorer** will open as a docked item (be patient, as loading may take time).</span></span>

    > [!NOTE] 
    > <span data-ttu-id="10ad9-264">만드는 데 사용한 구독 하는 경우에 *저장소 계정* 표시 되지 않으면 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-264">If the Subscription you used to create your *Storage Accounts* is not visible, ensure that you have:</span></span> 
    > - <span data-ttu-id="10ad9-265">Azure Portal에 사용한 것과 동일한 계정에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-265">Logged in to the same account as the one you used for the Azure Portal.</span></span>
    > - <span data-ttu-id="10ad9-266">(계정 설정에서 필터를 적용 해야 할) 계정 관리 페이지에서 구독을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-266">Selected your Subscription from the Account Management Page (you may need to apply a filter from your account settings):</span></span>  
    >
    >   ![구독을 찾을](images/AzureLabs-Lab8-22-5.png)

4.  <span data-ttu-id="10ad9-268">Azure 클라우드 서비스에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-268">Your Azure cloud services will be shown.</span></span> <span data-ttu-id="10ad9-269">찾을 **저장소 계정** 계정을 확장 하는 왼쪽에 있는 화살표를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-269">Find **Storage Accounts** and click the arrow to the left of that to expand your accounts.</span></span>

    ![열려 있는 저장소 계정](images/AzureLabs-Lab8-23.png)

5.  <span data-ttu-id="10ad9-271">새로 만든 확장 되 면 **저장소 계정** 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-271">Once expanded, your newly created **Storage account** should be available.</span></span> <span data-ttu-id="10ad9-272">저장소, 왼쪽에 있는 화살표를 클릭 하 고 확장 되 면 찾습니다 **테이블** 표시 하려면 옆에 있는 화살표를 클릭 합니다 **테이블** 마지막 단원에서 만든 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-272">Click the arrow to the left of your storage, and then once that is expanded, find **Tables** and click the arrow next to that, to reveal the **Table** you created in the last Chapter.</span></span> <span data-ttu-id="10ad9-273">두 번 클릭 하 여 **테이블**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-273">Double click your **Table**.</span></span>

    ![장면 개체 테이블 열기](images/AzureLabs-Lab8-24.png)

6.  <span data-ttu-id="10ad9-275">테이블에는 Visual Studio 창의 가운데에 열립니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-275">Your table will be opened in the center of your Visual Studio window.</span></span> <span data-ttu-id="10ad9-276">가 있는 테이블 아이콘을 클릭 합니다 **+** (및)에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-276">Click the table icon with the **+** (plus) on it.</span></span>

    ![새 테이블 추가](images/AzureLabs-Lab8-25.png)

7.  <span data-ttu-id="10ad9-278">수는 창이 나타나면 묻는 *엔터티 추가*합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-278">A window will appear prompting for you to *Add Entity*.</span></span> <span data-ttu-id="10ad9-279">여러 속성을 사용 하 여 각 총에서 세 개의 엔터티가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-279">You will create three entities in total, each with several properties.</span></span> <span data-ttu-id="10ad9-280">점을 확인할 수 있습니다 *PartitionKey* 하 고 *RowKey* 기본적으로 제공의 데이터를 테이블에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-280">You will notice that *PartitionKey* and *RowKey* are already provided, as these are used by the table to find your data.</span></span> 

    ![파티션 및 행 키](images/AzureLabs-Lab8-26.png)

8. <span data-ttu-id="10ad9-282">업데이트를 *값* 의 **PartitionKey** 및 **RowKey** 같이 (에 추가한 각 행 속성에 대해이 작업을 수행 해야 하지만 RowKey을 증가 될 때마다):</span><span class="sxs-lookup"><span data-stu-id="10ad9-282">Update the *Value* of the **PartitionKey** and **RowKey** as follows (remember to do this for each row property you add, though increment the RowKey each time):</span></span>

    ![올바른 값 추가](images/AzureLabs-Lab8-26-5.png)

9.  <span data-ttu-id="10ad9-284">클릭 **속성 추가** 데이터의 추가 행을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-284">Click **Add property** to add extra rows of data.</span></span> <span data-ttu-id="10ad9-285">일치 하 여 첫 번째 빈 테이블은 아래 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-285">Make your first empty table match the below table.</span></span>

10. <span data-ttu-id="10ad9-286">클릭 **확인** 완료 되 면 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-286">Click **OK** when you are finished.</span></span>

    ![완료 확인 클릭](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > <span data-ttu-id="10ad9-288">변경 했는지 확인 합니다 **형식** 의 **X**를 **Y**, 및 **Z**, 항목을 **Double**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-288">Ensure that you have changed the **Type** of the **X**, **Y**, and **Z**, entries to **Double**.</span></span> 

11. <span data-ttu-id="10ad9-289">이제 데이터 행이 있는 테이블을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-289">You will notice your table now has a row of data.</span></span> <span data-ttu-id="10ad9-290">클릭 합니다 **+** (다른 엔터티를 추가 하려면 다시 아이콘 더하기).</span><span class="sxs-lookup"><span data-stu-id="10ad9-290">Click the **+** (plus) icon again to add another entity.</span></span>

    ![첫 번째 행](images/AzureLabs-Lab8-27-5.png)

12. <span data-ttu-id="10ad9-292">추가 속성을 만들고 아래 표시 된 것과 일치 하도록 새 엔터티의 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-292">Create an additional property, and then set the values of the new entity to match those shown below.</span></span>

    ![큐브를 추가 합니다.](images/AzureLabs-Lab8-28.png)

13. <span data-ttu-id="10ad9-294">다른 엔터티를 추가 하기 위한 마지막 단계를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-294">Repeat the last step to add another entity.</span></span> <span data-ttu-id="10ad9-295">아래 표시 된 것이 엔터티에 대 한 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-295">Set the values for this entity to those shown below.</span></span>

    ![원기둥 추가](images/AzureLabs-Lab8-29.png)

14. <span data-ttu-id="10ad9-297">이제 테이블 아래 처럼 보여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-297">Your table should now look like the one below.</span></span>

    ![전체 테이블](images/AzureLabs-Lab8-30.png)

15. <span data-ttu-id="10ad9-299">이 챕터를 완료 했습니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-299">You have completed this Chapter.</span></span> <span data-ttu-id="10ad9-300">저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-300">Make sure to save.</span></span>

## <a name="chapter-6---create-an-azure-function-app"></a><span data-ttu-id="10ad9-301">-6 장 Azure 함수 앱 만들기</span><span class="sxs-lookup"><span data-stu-id="10ad9-301">Chapter 6 - Create an Azure Function App</span></span>

<span data-ttu-id="10ad9-302">업데이트를 데스크톱 응용 프로그램에서 호출할 Azure 함수 앱을 만듭니다는 **테이블** 서비스를 통해 알림을 보내고 합니다 **알림 허브**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-302">Create an Azure Function App, which will be called by the Desktop application to update the **Table** service and send a notification through the **Notification Hub**.</span></span>

<span data-ttu-id="10ad9-303">먼저 필요한 라이브러리를 로드 하 여 Azure Function을 사용 하면 파일을 만드는 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-303">First, you need to create a file that will allow your Azure Function to load the libraries you need.</span></span>

1.  <span data-ttu-id="10ad9-304">오픈 **메모장** (키 Windows 키와 notepad).</span><span class="sxs-lookup"><span data-stu-id="10ad9-304">Open **Notepad** (press Windows Key and type notepad).</span></span>

    ![메모장을 열려면](images/AzureLabs-Lab8-31.png)

2.  <span data-ttu-id="10ad9-306">열기 메모장을 사용 하 여 아래 JSON 구조를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-306">With Notepad open, insert the JSON structure below into it.</span></span> <span data-ttu-id="10ad9-307">작업을 수행한 후으로 바탕 화면에 저장 **project.json**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-307">Once you have done that, save it on your desktop as **project.json**.</span></span> <span data-ttu-id="10ad9-308">명명이 올바른 것: 확인 수행 **.txt 없는** 파일 확장명입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-308">It is important that the naming is correct: ensure it does **NOT have a .txt** file extension.</span></span> <span data-ttu-id="10ad9-309">익숙할 것 NuGet을 사용한 경우이 파일에서 함수를 사용 하는 라이브러리를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-309">This file defines the libraries your function will use, if you have used NuGet it will look familiar.</span></span>

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "7.0.0",
            "Microsoft.Azure.NotificationHubs" : "1.0.9",
            "Microsoft.Azure.WebJobs.Extensions.NotificationHubs" :"1.1.0"
        }
        }
    }
    }
    ```

3.  <span data-ttu-id="10ad9-310">에 로그인 합니다 [Azure Portal](https://portal.azure.com)합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-310">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

4.  <span data-ttu-id="10ad9-311">일단 로그인 하면 클릭할 **새로 만들기** 왼쪽 위에서 모서리 및 검색 **함수 앱**, 키를 눌러 **Enter**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-311">Once you are logged in, click on **New** in the top left corner, and search for **Function App**, press **Enter**.</span></span>

    ![함수 앱에 대 한 검색](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > <span data-ttu-id="10ad9-313">단어 **새로 만들기** 로 대체 되었습니다 **리소스 만들기**, 최신 포털에서입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-313">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

5.  <span data-ttu-id="10ad9-314">새 페이지에 대 한 설명을 제공 합니다는 **함수 앱** 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-314">The new page will provide a description of the **Function App** service.</span></span> <span data-ttu-id="10ad9-315">선택이 프롬프트의 왼쪽 아래에 있는 합니다 **만들기** 이 서비스를 사용 하 여 연결을 만들려면 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-315">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![함수 앱 인스턴스](images/AzureLabs-Lab8-33.png)

6.  <span data-ttu-id="10ad9-317">클릭 한 후 **만들기**, 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-317">Once you have clicked on **Create**, fill in the following:</span></span>

    1. <span data-ttu-id="10ad9-318">에 대 한 **앱 이름**,이 서비스 인스턴스에 대해 원하는 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-318">For **App name**, insert your desired name for this service instance.</span></span>

    2. <span data-ttu-id="10ad9-319">선택 된 **구독**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-319">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="10ad9-320">첫 번째 경우, 적합 한 가격 책정 계층 선택 만들기 시간을 **함수 앱 서비스**, 무료 계층을 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-320">Select the pricing tier appropriate for you, if this is the first time creating a **Function App Service**, a free tier should be available to you.</span></span>

    4. <span data-ttu-id="10ad9-321">선택 된 **리소스 그룹** 하거나 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-321">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="10ad9-322">리소스 그룹에는 모니터링, 프로 비전, 액세스 제어 및 Azure 자산 모음에 대 한 청구를 관리 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-322">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="10ad9-323">것이 좋습니다 (예: 이러한 labs)와 같은 일반적인 리소스 그룹에서 단일 프로젝트와 연결 된 모든 Azure 서비스를 유지).</span><span class="sxs-lookup"><span data-stu-id="10ad9-323">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="10ad9-324">추가 하려는 경우 Azure 리소스 그룹에 대 한 따르세요이 [리소스 그룹을 관리 하는 방법에 대 한 링크](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-324">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="10ad9-325">에 대 한 **OS**를 원하는 플랫폼으로 Windows를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-325">For **OS**, click Windows, as that is the intended platform.</span></span>

    6. <span data-ttu-id="10ad9-326">선택 된 **호스팅 계획** (이 자습서를 사용 하는 **소비 계획**.</span><span class="sxs-lookup"><span data-stu-id="10ad9-326">Select a **Hosting Plan** (this tutorial is using a **Consumption Plan**.</span></span>

    7. <span data-ttu-id="10ad9-327">선택 된 **위치** **(이전 단계에서 만든 저장소와 동일한 위치를 선택)**</span><span class="sxs-lookup"><span data-stu-id="10ad9-327">Select a **Location** **(choose the same location as the storage you have built in the previous step)**</span></span>

    8. <span data-ttu-id="10ad9-328">에 대 한 합니다 **저장소** 섹션인 **이전 단계에서 만든 저장소 서비스를 선택 해야 합니다**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-328">For the **Storage** section, **you must select the Storage Service you created in the previous step**.</span></span>

    9. <span data-ttu-id="10ad9-329">필요 하지 것입니다 *Application Insights* 이 앱에서 에게도 그대로 **해제**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-329">You will not need *Application Insights* in this app, so feel free to leave it **Off**.</span></span>

    10. <span data-ttu-id="10ad9-330">**만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-330">Click **Create**.</span></span>

        ![새 인스턴스 만들기](images/AzureLabs-Lab8-34.png)

7.  <span data-ttu-id="10ad9-332">클릭 한 후 **만들기** 만들려는 서비스에 대 한 대기 해야, 1 분이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-332">Once you have clicked on **Create** you will have to wait for the service to be created, this might take a minute.</span></span>

8.  <span data-ttu-id="10ad9-333">서비스 인스턴스가 생성 되 면 포털에서 알림이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-333">A notification will appear in the portal once the Service instance is created.</span></span>

    ![새 알림](images/AzureLabs-Lab8-35.png)

9.  <span data-ttu-id="10ad9-335">새 서비스 인스턴스를 탐색 하려면 알림을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-335">Click on the notifications to explore your new Service instance.</span></span>

10. <span data-ttu-id="10ad9-336">클릭 합니다 **리소스로 이동** 알림에서 새 서비스 인스턴스를 탐색 하는 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-336">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> 

    ![리소스로 이동](images/AzureLabs-Lab8-36.png)

11. <span data-ttu-id="10ad9-338">클릭 합니다 **+** (더하기) 옆에 아이콘 *함수*를 *새로 만들기*합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-338">Click the **+** (plus) icon next to *Functions*, to *Create new*.</span></span>

    ![새 함수를 추가 합니다.](images/AzureLabs-Lab8-37.png)

12. <span data-ttu-id="10ad9-340">중앙 패널에는 **함수** 만들기 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-340">Within the central panel, the **Function** creation window will appear.</span></span> <span data-ttu-id="10ad9-341">패널의 위쪽 절반에서 정보를 무시 하 고 클릭 **사용자 지정 함수**합니다 (아래와 같이 파란색 영역)의 맨 아래 근처에 있는 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-341">Ignore the information in the upper half of the panel, and click **Custom function**, which is located near the bottom (in the blue area, as below).</span></span>

    ![사용자 지정 함수](images/AzureLabs-Lab8-38.png)

13. <span data-ttu-id="10ad9-343">창 내에서 새 페이지에는 다양 한 함수 형식 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-343">The new page within the window will show various function types.</span></span> <span data-ttu-id="10ad9-344">자주색 형식을 보려면 아래로 스크롤하여 **HTTP PUT** 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-344">Scroll down to view the purple types, and click **HTTP PUT** element.</span></span>

    ![http put 링크](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > <span data-ttu-id="10ad9-346">그러나 다운 추가로 스크롤해야 할 수도 페이지 (및이 이미지 같지 않을 수 있습니다 정확 하 게 동일 하며 Azure Portal 업데이트 수행 하는 경우) 라는 이름의 요소에 대 한 원하는 *HTTP PUT*합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-346">You may have to scroll further the down the page (and this image may not look exactly the same, if Azure Portal updates have taken place), however, you are looking for an element called *HTTP PUT*.</span></span>

14. <span data-ttu-id="10ad9-347">합니다 **HTTP PUT** 함수 (아래 이미지 참조)를 구성 해야 하는 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-347">The **HTTP PUT** window will appear, where you need to configure the function (see below for image).</span></span>

    1.  <span data-ttu-id="10ad9-348">에 대 한 **언어로** C를 선택 하 고 드롭다운 메뉴를 사용 하 여\#입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-348">For **Language,** using the dropdown menu, select C\#.</span></span>

    2.  <span data-ttu-id="10ad9-349">에 대 한 **이름을** 적절 한 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-349">For **Name,** input an appropriate name.</span></span>

    3.  <span data-ttu-id="10ad9-350">에 **인증 수준을** 드롭다운 메뉴에서 **함수**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-350">In the **Authentication level** dropdown menu, select **Function**.</span></span>

    4.  <span data-ttu-id="10ad9-351">에 대 한 합니다 **테이블 이름** 정확한 이름을 만드는 데 사용 해야 하는 섹션에 **테이블** 이전 (포함 된 동일한 대/소문자) 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-351">For the **Table name** section, you need to use the exact name you used to create your **Table** service previously (including the same letter case).</span></span>

    5.  <span data-ttu-id="10ad9-352">내 합니다 **Storage 계정 연결** 섹션 드롭다운 메뉴를 사용 하 고 여기에서 저장소 계정을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-352">Within the **Storage account connection** section, use the dropdown menu, and select your storage account from there.</span></span> <span data-ttu-id="10ad9-353">클릭 하지는 **새로 만들기** 저장소 계정의 나타나야 하는 다른 패널에 표시할 섹션 제목 함께 하이퍼링크입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-353">If it is not there, click the **New** hyperlink alongside the section title, to show another panel, where your storage account should be listed.</span></span>

        ![새 저장소](images/AzureLabs-Lab8-40.png)

15. <span data-ttu-id="10ad9-355">클릭 **만들기** 및 설정을 성공적으로 업데이트 된 알림을 받게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-355">Click **Create** and you will receive a notification that your settings have been updated successfully.</span></span>

    ![함수 만들기](images/AzureLabs-Lab8-41.png)

16. <span data-ttu-id="10ad9-357">클릭 한 후 **만들기**, 함수 편집기로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-357">After clicking **Create**, you will be redirected to the function editor.</span></span>

    ![함수 코드 업데이트](images/AzureLabs-Lab8-42.png)

17. <span data-ttu-id="10ad9-359">(함수에서 코드를 대체) 하는 함수 편집기에 다음 코드를 삽입:</span><span class="sxs-lookup"><span data-stu-id="10ad9-359">Insert the following code into the function editor (replacing the code in the function):</span></span>

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Microsoft.Azure.NotificationHubs;
    using Newtonsoft.Json;

    public static async Task Run(UnityGameObject gameObj, CloudTable table, IAsyncCollector<Notification> notification, TraceWriter log)
    {
        //RowKey of the table object to be changed
        string rowKey = gameObj.RowKey;

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<UnityGameObject>("UnityPartitionKey", rowKey); 

        TableResult result = table.Execute(operation);

        //Create a UnityGameObject so to set its parameters
        UnityGameObject existingGameObj = (UnityGameObject)result.Result; 

        existingGameObj.RowKey = rowKey;
        existingGameObj.X = gameObj.X;
        existingGameObj.Y = gameObj.Y;
        existingGameObj.Z = gameObj.Z;

        //Replace the table appropriate table Entity with the value of the UnityGameObject
        operation = TableOperation.Replace(existingGameObj); 

        table.Execute(operation);

        log.Verbose($"Updated object position");

        //Serialize the UnityGameObject
        string wnsNotificationPayload = JsonConvert.SerializeObject(existingGameObj);
        
        log.Info($"{wnsNotificationPayload}");

        var headers = new Dictionary<string, string>();

        headers["X-WNS-Type"] = @"wns/raw";

        //Send the raw notification to subscribed devices
        await notification.AddAsync(new WindowsNotification(wnsNotificationPayload, headers)); 

        log.Verbose($"Sent notification");
    }

    // This UnityGameObject represent a Table Entity
    public class UnityGameObject : TableEntity
    {
        public string Type { get; set; }
        public double X { get; set; }
        public double Y { get; set; }
        public double Z { get; set; }
        public string RowKey { get; set; }
    }
    ```

    > [!NOTE]
    > <span data-ttu-id="10ad9-360">포함 된 라이브러리를 사용 하는 수신 이동 된 개체의 위치와 이름을 Unity 장면에서 (로 C# 이라는 개체 **UnityGameObject**).</span><span class="sxs-lookup"><span data-stu-id="10ad9-360">Using the included libraries, the function receives the name and location of the object which was moved in the Unity scene (as a C# object, called **UnityGameObject**).</span></span> <span data-ttu-id="10ad9-361">이 개체는 만들어진된 테이블 내에서 개체 매개 변수를 업데이트 한 다음 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-361">This object is then used to update the object parameters within the created table.</span></span> <span data-ttu-id="10ad9-362">함수는 다음에 모든 구독된 응용 프로그램에 알립니다는 만든 알림 허브 서비스에 대 한 호출을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-362">Following this, the function makes a call to your created Notification Hub service, which notifies all subscribed applications.</span></span>

18. <span data-ttu-id="10ad9-363">코드, 클릭 **저장할**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-363">With the code in place, click **Save**.</span></span>

19. <span data-ttu-id="10ad9-364">다음을 클릭 합니다 **\<** 페이지의 오른쪽에 (화살표) 아이콘을 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-364">Next, click the **\<** (arrow) icon, on the right-hand side of the page.</span></span>

    ![열기 업로드 패널](images/AzureLabs-Lab8-43.png)

20. <span data-ttu-id="10ad9-366">패널은 오른쪽에서에서 슬라이드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-366">A panel will slide in from the right.</span></span> <span data-ttu-id="10ad9-367">해당 창에서 클릭 **업로드**, 파일 탐색기에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-367">In that panel, click **Upload**, and a File Browser will appear.</span></span>

21. <span data-ttu-id="10ad9-368">찾아 클릭 합니다는 **project.json** 파일에서 만든 **메모장** 이전에 클릭 하 고는 **열기** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-368">Navigate to, and click, the **project.json** file, which you created in **Notepad** previously, and then click the **Open** button.</span></span> <span data-ttu-id="10ad9-369">이 파일은 라이브러리 함수를 사용할지를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-369">This file defines the libraries that your function will use.</span></span>

    ![json 업로드](images/AzureLabs-Lab8-44.png)

22. <span data-ttu-id="10ad9-371">파일 업로드에 오른쪽 패널에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-371">When the file has uploaded, it will appear in the panel on the right.</span></span> <span data-ttu-id="10ad9-372">내에서 열기를 클릭 하 여 **함수** 편집기입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-372">Clicking it will open it within the **Function** editor.</span></span> <span data-ttu-id="10ad9-373">찾아야 **정확 하 게** (아래 23 단계) 다음 이미지와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-373">It must look **exactly** the same as the next image (below step 23).</span></span>

23. <span data-ttu-id="10ad9-374">그런 다음, 왼쪽 패널에서 아래 **함수**를 클릭 합니다 **통합** 링크 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-374">Then, in the panel on the left, beneath **Functions**, click the **Integrate** link.</span></span>

    ![함수를 통합 합니다.](images/AzureLabs-Lab8-45.png)

24. <span data-ttu-id="10ad9-376">다음 페이지 상단 오른쪽 모서리에서 클릭 **고급 편집기** (아래와 같이).</span><span class="sxs-lookup"><span data-stu-id="10ad9-376">On the next page, in the top right corner, click **Advanced editor** (as below).</span></span>

    ![고급 편집기 열기](images/AzureLabs-Lab8-46.png)

25. <span data-ttu-id="10ad9-378">A **function.json** 파일이 다음 코드 조각을 사용 하 여 교체 해야 하는 가운데 창에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-378">A **function.json** file will be opened in the center panel, which needs to be replaced with the following code snippet.</span></span> <span data-ttu-id="10ad9-379">작성 하는 함수 및 매개 변수를 정의 하는이 함수에 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-379">This defines the function you are building and the parameters passed into the function.</span></span>

    ```json
    {
    "bindings": [
        {
        "authLevel": "function",
        "type": "httpTrigger",
        "methods": [
            "get",
            "post"
        ],
        "name": "gameObj",
        "direction": "in"
        },
        {
        "type": "table",
        "name": "table",
        "tableName": "SceneObjectsTable",
        "connection": "mrnothubstorage_STORAGE",
        "direction": "in"
        },
        {
        "type": "notificationHub",
        "direction": "out",
        "name": "notification",
        "hubName": "MR_NotHub_ServiceInstance",
        "connection": "MRNotHubNS_DefaultFullSharedAccessSignature_NH",
        "platform": "wns"
        }
    ]
    }
    ```

26. <span data-ttu-id="10ad9-380">이제 편집기 아래 이미지 처럼 보여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-380">Your editor should now look like the image below:</span></span>

    ![표준 편집기 돌아가기](images/AzureLabs-Lab8-47.png)

27. <span data-ttu-id="10ad9-382">방금 삽입 한 입력된 매개 변수 테이블 및 저장소 세부 정보를 일치 하지 않을 수 및 사용자 정보로 업데이트 해야 합니다를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-382">You may notice the input parameters that you have just inserted might not match your table and storage details and therefore will need to be updated with your information.</span></span> <span data-ttu-id="10ad9-383">**이렇게 하지 않으면 여기**처럼 다음 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-383">**Do not do this here**, as it is covered next.</span></span> <span data-ttu-id="10ad9-384">클릭할 합니다 **표준 편집기** 뒤로 돌아가서 페이지의 오른쪽 위 모서리에 있는 링크를 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-384">Simply click the **Standard editor** link, in the top-right corner of the page, to go back.</span></span>

28. <span data-ttu-id="10ad9-385">다시 합니다 **표준 편집기**, 클릭 **Azure Table Storage (테이블)** 아래에 있는 **입력**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-385">Back in the **Standard editor**, click **Azure Table Storage (table)**, under **Inputs**.</span></span> 
    
    ![입력 테이블](images/AzureLabs-Lab8-47-5.png)

29. <span data-ttu-id="10ad9-387">다음 일치 항목을 확인 **여** 정보를 다른 것으로 (다음 단계를 아래 이미지는):</span><span class="sxs-lookup"><span data-stu-id="10ad9-387">Ensure the following match to **your** information, as they may be different (there is an image below the following steps):</span></span>

    1.  <span data-ttu-id="10ad9-388">**테이블 이름**: Azure Storage, 테이블 서비스 내에서 만든 테이블의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-388">**Table name**: the name of the table you created within your Azure Storage, Tables service.</span></span>

    2.  <span data-ttu-id="10ad9-389">**저장소 계정 연결:** 클릭 **새**드롭다운 메뉴와 함께 표시 되 고 창의 오른쪽에 패널이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-389">**Storage account connection:** click **new**, which appears alongside the dropdown menu, and a panel will appear to the right of the window.</span></span>

        ![새 저장소](images/AzureLabs-Lab8-48.png)

        1.  <span data-ttu-id="10ad9-391">선택 하 **저장소 계정**, 호스트에 이전에 만든 된 **함수 앱.**</span><span class="sxs-lookup"><span data-stu-id="10ad9-391">Select your **Storage Account**, which you created previously to host the **Function Apps.**</span></span>

        2. <span data-ttu-id="10ad9-392">합니다 **저장소 계정** 연결 값이 생성 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-392">You will notice that the **Storage Account** connection value has been created.</span></span>

        3. <span data-ttu-id="10ad9-393">키를 눌러 해야 **저장할** 완료 되 면 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-393">Make sure to press **Save** once you are done.</span></span>

    3.  <span data-ttu-id="10ad9-394">**입력** 페이지과 일치 해야는 아래에서 보여 주는 **프로그램** 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-394">The **Inputs** page should now match the below, showing **your** information.</span></span>

        ![입력 완료](images/AzureLabs-Lab8-49.png)

30. <span data-ttu-id="10ad9-396">다음으로, 클릭 **Azure 알림 허브 (알림)** -아래 **출력**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-396">Next, click **Azure Notification Hub (notification)** - under **Outputs**.</span></span> <span data-ttu-id="10ad9-397">다음과 일치 하도록 보장 **여** 정보를 다른 것으로 (다음 단계를 아래 이미지는):</span><span class="sxs-lookup"><span data-stu-id="10ad9-397">Ensure the following are matched to **your** information, as they may be different (there is an image below the following steps):</span></span>

    1.  <span data-ttu-id="10ad9-398">**알림 허브 이름**:의 이름입니다 하 **알림 허브** 이전에 만든 서비스 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-398">**Notification Hub Name**: this is the name of your **Notification Hub** service instance, which you created previously.</span></span>

    2.  <span data-ttu-id="10ad9-399">**Notification Hubs 네임 스페이스 연결**: 클릭 **새**, 드롭다운 메뉴와 함께 표시 되는 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-399">**Notification Hubs namespace connection**: click **new**, which appears alongside the dropdown menu.</span></span>

        ![출력 확인](images/AzureLabs-Lab8-50.png)

    3. <span data-ttu-id="10ad9-401">**연결** 팝업이 표시 됩니다 (아래 이미지 참조)를 선택 해야 합니다 **Namespace** 의 **알림 허브**, 이전에 설정 하는 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-401">The **Connection** popup will appear (see image below), where you need to select the **Namespace** of the **Notification Hub**, which you set up previously.</span></span>

    4. <span data-ttu-id="10ad9-402">선택 하면 **알림 허브** 중간 드롭다운 메뉴에서 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-402">Select your **Notification Hub** name from the middle dropdown menu.</span></span>

    5.  <span data-ttu-id="10ad9-403">설정 된 **정책** 드롭다운 메뉴를 **DefaultFullSharedAccessSignature**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-403">Set the **Policy** dropdown menu to **DefaultFullSharedAccessSignature**.</span></span>

    6. <span data-ttu-id="10ad9-404">클릭 합니다 **선택** 다시 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-404">Click the **Select** button to go back.</span></span>

        ![출력 업데이트](images/AzureLabs-Lab8-51.png)

31.  <span data-ttu-id="10ad9-406">**출력** 페이지과 일치 해야 합니다 아래 같지만 **에** 정보 대신 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-406">The **Outputs** page should now match the below, but with **your** information instead.</span></span> <span data-ttu-id="10ad9-407">키를 눌러 해야 **저장할**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-407">Make sure to press **Save**.</span></span>

> [!WARNING]
> <span data-ttu-id="10ad9-408">*알림 허브 이름의 직접 편집 하지 마십시오* (이 모든 작업은 사용 하는 **고급 편집기**경우 이전 단계를 올바르게 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-408">*Do not edit the Notification Hub name directly* (this should all be done using the **Advanced Editor**, provided you followed the previous steps correctly.</span></span>

![전체 출력](images/AzureLabs-Lab8-50.png)

32. <span data-ttu-id="10ad9-410">이 시점에서 작동 하도록 함수를 테스트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-410">At this point, you should test the function, to ensure it is working.</span></span> <span data-ttu-id="10ad9-411">가상 하드 디스크 파일에 대한 중요 정보를 제공하려면</span><span class="sxs-lookup"><span data-stu-id="10ad9-411">To do this:</span></span> 

    1. <span data-ttu-id="10ad9-412">한 번 더 함수 페이지로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-412">Navigate to the function page once more:</span></span>

        ![전체 출력](images/AzureLabs-Lab8-50-1.png)

    2. <span data-ttu-id="10ad9-414">함수 페이지 다시 클릭 합니다 **테스트** 열리는 페이지의 맨 오른쪽 탭의 *테스트* 블레이드에서:</span><span class="sxs-lookup"><span data-stu-id="10ad9-414">Back on the function page, click the **Test** tab on the far right side of the page, to open the *Test* blade:</span></span>

        ![전체 출력](images/AzureLabs-Lab8-50-2.png)

    3. <span data-ttu-id="10ad9-416">내 합니다 **요청 본문** 붙여넣기 블레이드의 텍스트 상자는 아래 코드:</span><span class="sxs-lookup"><span data-stu-id="10ad9-416">Within the **Request body** textbox of the blade, paste the below code:</span></span>

        ```
        {  
            "Type":null,
            "X":3,
            "Y":0,
            "Z":1,
            "PartitionKey":null,
            "RowKey":"Obj2",
            "Timestamp":"0001-01-01T00:00:00+00:00",
            "ETag":null
        }
        ```

    4. <span data-ttu-id="10ad9-417">테스트 코드를 클릭 합니다 **실행** 단추 오른쪽 맨 아래에 있고 테스트 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-417">With the test code in place, click the **Run** button at the bottom right, and the test will be run.</span></span> <span data-ttu-id="10ad9-418">테스트의 출력 로그를 콘솔 영역에 함수 코드에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-418">The output logs of the test will appear in the console area, below your function code.</span></span>

        ![전체 출력](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > <span data-ttu-id="10ad9-420">위의 테스트에 실패 하면 해야 위의 단계를 정확 하 게 수행 하는 두 번 확인 내의 설정을 특히 합니다 **패널을 통합**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-420">If the above test fails, you will need to double check that you have followed the above steps exactly, particularly the settings within the **integrate panel**.</span></span> 

## <a name="chapter-7---set-up-desktop-unity-project"></a><span data-ttu-id="10ad9-421">7 장-데스크톱 Unity 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="10ad9-421">Chapter 7 - Set up Desktop Unity Project</span></span>

> [!IMPORTANT]
> <span data-ttu-id="10ad9-422">이제 만들려는 데스크톱 응용 프로그램 **것입니다** Unity 편집기에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-422">The Desktop application which you are now creating, **will not** work in the Unity Editor.</span></span> <span data-ttu-id="10ad9-423">Visual Studio를 사용 하 여 응용 프로그램 (또는 배포 된 응용 프로그램)를 작성 하는 다음 편집기 외부에서 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-423">It needs to be run outside of the Editor, following the Building of the application, using Visual Studio (or the deployed application).</span></span> 

<span data-ttu-id="10ad9-424">다음은 일반적인 등록 Unity를 사용 하 여 개발 및 혼합된 현실에 대 한와 따라서 다른 프로젝트에 대 한 좋은 템플릿입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-424">The following is a typical set up for developing with Unity and mixed reality, and as such, is a good template for other projects.</span></span>

<span data-ttu-id="10ad9-425">설정 하 고 혼합된 현실 몰입 형 헤드셋을 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-425">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE] 
> <span data-ttu-id="10ad9-426">해야 **되지** 이 과정에 대 한 동작 컨트롤러 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-426">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="10ad9-427">몰입 형 헤드셋 설정만 지원에 필요한 경우 따르세요 이렇게 [Windows Mixed Reality를 설정 하는 방법에 대 한 링크](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-427">If you need support setting up the immersive headset, please follow this [link on how to set up Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="10ad9-428">오픈 **Unity** 누릅니다 **새로 만들기**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-428">Open **Unity** and click **New**.</span></span>

    ![새 unity 프로젝트](images/AzureLabs-Lab8-52.png)

2.  <span data-ttu-id="10ad9-430">Unity 프로젝트 이름을 삽입 해야 **UnityDesktopNotifHub**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-430">You need to provide a Unity Project name, insert **UnityDesktopNotifHub**.</span></span> <span data-ttu-id="10ad9-431">프로젝트 형식 설정 되어 있는지 확인 **3D**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-431">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="10ad9-432">설정 된 **위치** 적절 한 위치로 (기억에 루트 디렉터리에 가까울수록이 더 좋습니다).</span><span class="sxs-lookup"><span data-stu-id="10ad9-432">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="10ad9-433">그런 다음 클릭 **프로젝트 만들기**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-433">Then, click **Create project**.</span></span>

    ![프로젝트 만들기](images/AzureLabs-Lab8-53.png)

3.  <span data-ttu-id="10ad9-435">Unity 열기를 사용 하 여 기본 검사 가치가 **스크립트 편집기** 로 설정 된 **Visual Studio**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-435">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="10ad9-436">로 이동 **편집할** > **기본 설정** 로 이동한 다음 새 창에서 **외부 도구**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-436">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="10ad9-437">변경 **외부 스크립트 편집기** 하 **Visual Studio 2017**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-437">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="10ad9-438">닫기 합니다 **기본 설정** 창입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-438">Close the **Preferences** window.</span></span>

    ![집합 외부 VS 도구](images/AzureLabs-Lab8-54.png)

4.  <span data-ttu-id="10ad9-440">이동한 다음 **파일** > **빌드 설정** 선택한 **유니버설 Windows 플랫폼**를 클릭 합니다 **플랫폼 전환**단추를 선택 항목을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-440">Next, go to **File** > **Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![플랫폼 전환](images/AzureLabs-Lab8-55.png)

5.  <span data-ttu-id="10ad9-442">있는 동안 **파일** > **빌드 설정**, 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-442">While still in **File** > **Build Settings**, make sure that:</span></span>

    1.  <span data-ttu-id="10ad9-443">**장치를 대상** 로 설정 된 **모든 장치**</span><span class="sxs-lookup"><span data-stu-id="10ad9-443">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="10ad9-444">이 응용 프로그램 수는 데스크톱 이므로 이어야 합니다 **모든 장치**</span><span class="sxs-lookup"><span data-stu-id="10ad9-444">This Application will be for your desktop, so must be **Any Device**</span></span>

    2.  <span data-ttu-id="10ad9-445">**빌드 형식** 로 설정 된 **D3D**</span><span class="sxs-lookup"><span data-stu-id="10ad9-445">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="10ad9-446">**SDK** 로 설정 된 **가장 최근에 설치 된**</span><span class="sxs-lookup"><span data-stu-id="10ad9-446">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="10ad9-447">**Visual Studio 버전** 로 설정 된 **가장 최근에 설치 된**</span><span class="sxs-lookup"><span data-stu-id="10ad9-447">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="10ad9-448">**빌드 및 실행** 로 설정 된 **로컬 컴퓨터**</span><span class="sxs-lookup"><span data-stu-id="10ad9-448">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="10ad9-449">여기 하는 동안 가치가 장면 저장 하 고 빌드에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-449">While here, it is worth saving the scene, and adding it to the build.</span></span>

        1. <span data-ttu-id="10ad9-450">선택 하 여이 작업을 수행할 **열고 장면 추가**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-450">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="10ad9-451">창 저장 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-451">A save window will appear.</span></span>

            ![열기 장면 추가](images/AzureLabs-Lab8-56.png)

        2. <span data-ttu-id="10ad9-453">새 폴더를 만들려면이 고 모든의 미래, 장면에 대 한 다음 선택 합니다 **새 폴더** 새 폴더를 만들려면 단추 이름을 **장면**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-453">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![새 백그라운드에서 폴더](images/AzureLabs-Lab8-57.png)

        3. <span data-ttu-id="10ad9-455">새로 만든 열 **장면** 폴더를 선택한 다음는 **파일 이름:** 텍스트 필드에 입력 **NH\_데스크톱\_장면**, 누릅니다 **저장할**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-455">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **NH\_Desktop\_Scene**, then press **Save**.</span></span>

            ![new NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  <span data-ttu-id="10ad9-457">설정에 남아 **빌드 설정**, 지금은 기본값으로 유지 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-457">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6.  <span data-ttu-id="10ad9-458">같은 창에서 클릭 하는 **플레이어 설정** 단추를 공간에 관련 된 패널이 열립니다이 위치는 **검사기** 위치한.</span><span class="sxs-lookup"><span data-stu-id="10ad9-458">In the same window click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

7.  <span data-ttu-id="10ad9-459">이 패널에서 몇 가지 설정을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-459">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="10ad9-460">에 **기타 설정** 탭:</span><span class="sxs-lookup"><span data-stu-id="10ad9-460">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="10ad9-461">**스크립팅 런타임 버전** 있어야 **실험적 (.NET 4.6 동등)**</span><span class="sxs-lookup"><span data-stu-id="10ad9-461">**Scripting Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**</span></span>

        2. <span data-ttu-id="10ad9-462">**백 엔드를 스크립팅** 있어야 **.NET**</span><span class="sxs-lookup"><span data-stu-id="10ad9-462">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="10ad9-463">**API 호환성 수준** 있어야 **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="10ad9-463">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![net 버전 4.6](images/AzureLabs-Lab8-59.png)

    2.  <span data-ttu-id="10ad9-465">내 합니다 **게시 설정** 탭의 **기능**, 확인:</span><span class="sxs-lookup"><span data-stu-id="10ad9-465">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="10ad9-466">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="10ad9-466">**InternetClient**</span></span>

            ![눈금 인터넷 클라이언트](images/AzureLabs-Lab8-60.png)

8.  <span data-ttu-id="10ad9-468">년대 **빌드 설정** *Unity C\# 프로젝트* 가 더 이상 회색;이 옆의 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-468">Back in **Build Settings** *Unity C\# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="10ad9-469">닫기 합니다 **빌드 설정** 창입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-469">Close the **Build Settings** window.</span></span>

10. <span data-ttu-id="10ad9-470">장면 및 프로젝트 저장할 **파일** > **장면 저장 파일** > **프로젝트를 저장할**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-470">Save your Scene and Project **File** > **Save Scene / File** > **Save Project**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="10ad9-471">건너뛸 하려는 경우는 *Unity 설정* (데스크톱 앱)이이 프로젝트에 대 한 구성 요소 코드에 바로 계속를 자유롭게 [이.unitypackage 다운로드](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage),으로 프로젝트로 가져올를 [ **사용자 지정 패키지**](https://docs.unity3d.com/Manual/AssetPackages.html)를 계속 진행 한 다음 [9 장에서](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-471">If you wish to skip the *Unity Set up* component for this project (Desktop App), and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span>  <span data-ttu-id="10ad9-472">스크립트 구성 요소를 추가 해야 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-472">You will still need to add the script components.</span></span>

## <a name="chapter-8---importing-the-dlls-in-unity"></a><span data-ttu-id="10ad9-473">8 장-Unity에서 Dll 가져오기</span><span class="sxs-lookup"><span data-stu-id="10ad9-473">Chapter 8 - Importing the DLLs in Unity</span></span>

<span data-ttu-id="10ad9-474">Azure Storage for Unity 사용 (자체는.Net 용 Azure SDK를 활용 함).</span><span class="sxs-lookup"><span data-stu-id="10ad9-474">You will be using Azure Storage for Unity (which itself leverages the .Net SDK for Azure).</span></span> <span data-ttu-id="10ad9-475">자세한 내용은이 작업 수행 [Unity에 대 한 Azure Storage에 대 한 링크](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-475">For more information follow this [link about Azure Storage for Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>

<span data-ttu-id="10ad9-476">플러그 인 가져오기 후 다시 구성 해야 하는 Unity의 알려진된 문제는 현재 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-476">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="10ad9-477">이러한 단계 (4-7이 단원의) 버그가 해결 된 후 필요한 더 이상.</span><span class="sxs-lookup"><span data-stu-id="10ad9-477">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="10ad9-478">사용자 고유의 프로젝트에 SDK를 가져오려면 최신 다운로드 했는지 확인 [ **.unitypackage** ](https://aka.ms/azstorage-unitysdk) GitHub에서.</span><span class="sxs-lookup"><span data-stu-id="10ad9-478">To import the SDK into your own project, make sure you have downloaded the latest [**.unitypackage**](https://aka.ms/azstorage-unitysdk) from GitHub.</span></span> <span data-ttu-id="10ad9-479">그런 다음 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-479">Then, do the following:</span></span>

1.  <span data-ttu-id="10ad9-480">추가 합니다 **.unitypackage** 사용 하 여 Unity에는 **자산 \> 패키지 가져오기 \> 사용자 지정 패키지** 메뉴 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-480">Add the **.unitypackage** to Unity by using the **Assets \> Import Package \> Custom Package** menu option.</span></span>

2.  <span data-ttu-id="10ad9-481">에 **Unity 패키지 가져오기** 팝업에서 선택할 수 있는 아래에 있는 모든 상자 \* \**플러그 인* \> \* 저장소 \* \* \* 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-481">In the **Import Unity Package** box that pops up, you can select everything under \*\**Plugin* \> \*Storage\*\*\*.</span></span>  <span data-ttu-id="10ad9-482">이 과정에 대 한 필요 하지 않을 때 나머지 작업은 모두 선택 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-482">Uncheck everything else, as it is not needed for this course.</span></span>

    ![패키지 가져오기](images/AzureLabs-Lab8-61.png)

3.  <span data-ttu-id="10ad9-484">클릭 합니다 ***가져오기*** 프로젝트에 항목을 추가 하려면 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-484">Click the ***Import*** button to add the items to your project.</span></span>

4.  <span data-ttu-id="10ad9-485">로 이동 합니다 **저장소** 아래에 폴더 **플러그 인** 프로젝트에서 표시 하 고 다음 플러그 인 선택 *만*:</span><span class="sxs-lookup"><span data-stu-id="10ad9-485">Go to the **Storage** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="10ad9-486">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="10ad9-486">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="10ad9-487">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="10ad9-487">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="10ad9-488">Microsoft.WindowsAzure.Storage</span><span class="sxs-lookup"><span data-stu-id="10ad9-488">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="10ad9-489">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="10ad9-489">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="10ad9-490">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="10ad9-490">System.Spatial</span></span>

![모든 플랫폼을 선택 취소](images/AzureLabs-Lab8-62.png)

5.  <span data-ttu-id="10ad9-492">사용 하 여 *이러한 특정 플러그 인* 선택 하면 **의 선택을 취소** **Any 플랫폼** 고 **의 선택을 취소** **WSAPlayer** 누른 **적용**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-492">With *these specific plugins* selected, **uncheck** **Any Platform** and **uncheck** **WSAPlayer** then click **Apply**.</span></span>

    ![플랫폼 dll를 적용 합니다.](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > <span data-ttu-id="10ad9-494">이러한 특정 플러그 인 Unity 편집기에서 사용할 수만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-494">We are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="10ad9-495">Unity에서 프로젝트를 내보낸 후 사용할 WSA 폴더에 같은 플러그 인의 다양 한 버전 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-495">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="10ad9-496">에 **저장소** 플러그 인 폴더에만 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-496">In the **Storage** plugin folder, select only:</span></span>

    -   <span data-ttu-id="10ad9-497">Microsoft.Data.Services.Client</span><span class="sxs-lookup"><span data-stu-id="10ad9-497">Microsoft.Data.Services.Client</span></span>

        ![집합에 dll에 대 한 처리](images/AzureLabs-Lab8-64.png)

7.  <span data-ttu-id="10ad9-499">확인 합니다 **없는 프로세스** 상자에 **플랫폼 설정** 클릭 ***적용***합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-499">Check the **Don't Process** box under **Platform Settings** and click ***Apply***.</span></span>

    ![없는 처리 적용](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > <span data-ttu-id="10ad9-501">표시 됩니다이 플러그 인 "처리"를 Unity 어셈블리 패 처가이 플러그 인을 처리 하는 데 문제가 있어.</span><span class="sxs-lookup"><span data-stu-id="10ad9-501">We are marking this plugin "Don't process", because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="10ad9-502">플러그 인 처리 되지 않았습니다. 경우에 계속 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-502">The plugin will still work even though it is not processed.</span></span>

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a><span data-ttu-id="10ad9-503">9-장 데스크톱 Unity 프로젝트에서 TableToScene 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="10ad9-503">Chapter 9 - Create the TableToScene class in the Desktop Unity project</span></span>

<span data-ttu-id="10ad9-504">이제이 응용 프로그램을 실행 하는 코드를 포함 하는 스크립트를 작성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-504">You now need to create the scripts containing the code to run this application.</span></span>

<span data-ttu-id="10ad9-505">생성 해야 하는 첫 번째 스크립트 **TableToScene**를 담당 하는:</span><span class="sxs-lookup"><span data-stu-id="10ad9-505">The first script you need to create is **TableToScene**, which is responsible for:</span></span>

-   <span data-ttu-id="10ad9-506">Azure 테이블 내 엔터티를 읽는 중입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-506">Reading entities within the Azure Table.</span></span>
-   <span data-ttu-id="10ad9-507">테이블 데이터를 사용 하 여 생성, 개체를 결정에 위치 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-507">Using the Table data, determine which objects to spawn, and in which position.</span></span>

<span data-ttu-id="10ad9-508">생성 해야 하는 두 번째 스크립트 **CloudScene**를 담당 하는:</span><span class="sxs-lookup"><span data-stu-id="10ad9-508">The second script you need to create is **CloudScene**, which is responsible for:</span></span>

-   <span data-ttu-id="10ad9-509">장면 관련 개체를 끌어서 놓을 수 있도록 마우스 왼쪽 단추 클릭 이벤트를 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-509">Registering the left-click event, to allow the user to drag objects around the scene.</span></span>
-   <span data-ttu-id="10ad9-510">이 Unity 장면에서 개체 데이터를 직렬화 하 고 Azure 함수 앱으로 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-510">Serializing the object data from this Unity scene, and sending it to the Azure Function App.</span></span>

<span data-ttu-id="10ad9-511">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="10ad9-511">To create this class:</span></span>

1.  <span data-ttu-id="10ad9-512">마우스 오른쪽 단추로 클릭 합니다 **Asset** 폴더는 프로젝트 패널 **만들기** > **폴더**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-512">Right-click in the **Asset** Folder located in the Project Panel, **Create** > **Folder**.</span></span> <span data-ttu-id="10ad9-513">폴더의 이름을 **스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-513">Name the folder **Scripts**.</span></span>

    ![스크립트 폴더 만들기](images/AzureLabs-Lab8-66.png)

    ![2 스크립트 폴더 만들기](images/AzureLabs-Lab8-67.png)

2.  <span data-ttu-id="10ad9-516">열려는 방금 만든 폴더를 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-516">Double click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="10ad9-517">마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **Create** >  **C# 스크립트**.</span><span class="sxs-lookup"><span data-stu-id="10ad9-517">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="10ad9-518">스크립트 이름을 **TableToScene**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-518">Name the script **TableToScene**.</span></span>

    <span data-ttu-id="10ad9-519">![새 c# 스크립트](images/AzureLabs-Lab8-68.png)
    ![TableToScene 이름 바꾸기](images/AzureLabs-Lab8-69.png)</span><span class="sxs-lookup"><span data-stu-id="10ad9-519">![new c# script](images/AzureLabs-Lab8-68.png)
![TableToScene rename](images/AzureLabs-Lab8-69.png)</span></span>

4.  <span data-ttu-id="10ad9-520">Visual Studio 2017에서 열려는 스크립트를 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-520">Double-click on the script to open it in Visual Studio 2017.</span></span>

5.  <span data-ttu-id="10ad9-521">다음 네임 스페이스를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-521">Add the following namespaces:</span></span>

    ```csharp
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Auth;
    using Microsoft.WindowsAzure.Storage.Table;
    using UnityEngine;
    ```

6.  <span data-ttu-id="10ad9-522">클래스 내에서 다음 변수를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-522">Within the class, insert the following variables:</span></span>

    ```csharp
        /// <summary>    
        /// allows this class to behave like a singleton
        /// </summary>    
        public static TableToScene instance;

        /// <summary>    
        /// Insert here you Azure Storage name     
        /// </summary>    
        private string accountName = " -- Insert your Azure Storage name -- ";

        /// <summary>    
        /// Insert here you Azure Storage key    
        /// </summary>    
        private string accountKey = " -- Insert your Azure Storage key -- ";
    ```
    
    > [!NOTE] 
    > <span data-ttu-id="10ad9-523">대체는 **accountName** Azure Storage 서비스 이름 값 및 **accountKey** (참조 아래 이미지) Azure Portal에서 Azure Storage 서비스에 있는 키 값을 갖는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-523">Substitute the **accountName** value with your Azure Storage Service name and **accountKey** value with the key value found in the Azure Storage Service, in the Azure Portal (See Image below).</span></span> 
    >
    > ![계정 키 가져오기](images/AzureLabs-Lab8-70.png)

7.  <span data-ttu-id="10ad9-525">이제 추가 합니다 **start ()** 하 고 **Awake()** 클래스를 초기화 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-525">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {  
            // Call method to populate the scene with new objects as 
            // pecified in the Azure Table
            PopulateSceneFromTableAsync();
        }
    ```

8.  <span data-ttu-id="10ad9-526">내 합니다 **TableToScene** 클래스, Azure 테이블에서 값을 검색 하 고 사용 하 여 장면에서 적절 한 기본 형식을 생성 하는 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-526">Within the **TableToScene** class, add the method that will retrieve the values from the Azure Table and use them to spawn the appropriate primitives in the scene.</span></span>

    ```csharp
        /// <summary>    
        /// Populate the scene with new objects as specified in the Azure Table    
        /// </summary>    
        private async void PopulateSceneFromTableAsync()
        {
            // Obtain credentials for the Azure Storage
            StorageCredentials creds = new StorageCredentials(accountName, accountKey);

            // Storage account
            CloudStorageAccount account = new CloudStorageAccount(creds, useHttps: true);
            
            // Storage client
            CloudTableClient client = account.CreateCloudTableClient(); 
            
            // Table reference
            CloudTable table = client.GetTableReference("SceneObjectsTable");

            TableContinuationToken token = null;

            // Query the table for every existing Entity
            do
            {
                // Queries the whole table by breaking it into segments
                // (would happen only if the table had huge number of Entities)
                TableQuerySegment<AzureTableEntity> queryResult = await table.ExecuteQuerySegmentedAsync(new TableQuery<AzureTableEntity>(), token); 

                foreach (AzureTableEntity entity in queryResult.Results)
                {
                    GameObject newSceneGameObject = null;
                    Color newColor;

                    // check for the Entity Type and spawn in the scene the appropriate Primitive
                    switch (entity.Type)
                    {
                        case "Cube":
                            // Create a Cube in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                            newColor = Color.blue;
                            break;

                        case "Sphere":
                            // Create a Sphere in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                            newColor = Color.red;
                            break;

                        case "Cylinder":
                            // Create a Cylinder in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                            newColor = Color.yellow;
                            break;
                        default:
                            newColor = Color.white;
                            break;
                    }

                    newSceneGameObject.name = entity.RowKey;

                    newSceneGameObject.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
                    {
                        color = newColor
                    };

                    //check for the Entity X,Y,Z and move the Primitive at those coordinates
                    newSceneGameObject.transform.position = new Vector3((float)entity.X, (float)entity.Y, (float)entity.Z);
                }

                // if the token is null, it means there are no more segments left to query
                token = queryResult.ContinuationToken;
            }

            while (token != null);
        }
    ```

9.  <span data-ttu-id="10ad9-527">외부 합니다 **TableToScene** serialize 및 deserialize 하는 응용 프로그램에서 사용 되는 클래스를 정의 해야 하는 클래스는 **테이블 엔터티**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-527">Outside the **TableToScene** class, you need to define the class used by the application to serialize and deserialize the **Table Entities**.</span></span>

    ```csharp
        /// <summary>
        /// This objects is used to serialize and deserialize the Azure Table Entity
        /// </summary>
        [System.Serializable]
        public class AzureTableEntity : TableEntity
        {
            public AzureTableEntity(string partitionKey, string rowKey)
                : base(partitionKey, rowKey) { }

            public AzureTableEntity() { }
            public string Type { get; set; }
            public double X { get; set; }
            public double Y { get; set; }
            public double Z { get; set; }
        }
    ```

10. <span data-ttu-id="10ad9-528">했는지 **저장할** Unity 편집기로 다시 이동 하기 전에 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-528">Make sure you **Save** before going back to the Unity Editor.</span></span>

11. <span data-ttu-id="10ad9-529">클릭 합니다 **주 카메라** 에서 **계층** 패널에서 해당 속성에 표시 되도록 합니다 **검사기**.</span><span class="sxs-lookup"><span data-stu-id="10ad9-529">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span>

12. <span data-ttu-id="10ad9-530">사용 하 여 합니다 **스크립트** 폴더를 열고 스크립트를 선택 **TableToScene 파일** 끕니다 합니다 **주 카메라**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-530">With the **Scripts** folder open, select the script **TableToScene file** and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="10ad9-531">결과 다음과 같이 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-531">The result should be as below:</span></span>

    ![주 카메라에 스크립트 추가](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a><span data-ttu-id="10ad9-533">10-장 데스크톱 Unity 프로젝트에서 CloudScene 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="10ad9-533">Chapter 10 - Create the CloudScene class in the Desktop Unity Project</span></span>

<span data-ttu-id="10ad9-534">생성 해야 하는 두 번째 스크립트 **CloudScene**를 담당 하는:</span><span class="sxs-lookup"><span data-stu-id="10ad9-534">The second script you need to create is **CloudScene**, which is responsible for:</span></span>

-   <span data-ttu-id="10ad9-535">장면 관련 개체를 끌어서 놓을 수 있도록 마우스 왼쪽 단추 클릭 이벤트를 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-535">Registering the left-click event, to allow the user to drag objects around the scene.</span></span>

-   <span data-ttu-id="10ad9-536">이 Unity 장면에서 개체 데이터를 직렬화 하 고 Azure 함수 앱으로 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-536">Serializing the object data from this Unity scene, and sending it to the Azure Function App.</span></span>

<span data-ttu-id="10ad9-537">두 번째 스크립트를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="10ad9-537">To create the second script:</span></span>

1.  <span data-ttu-id="10ad9-538">마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **만들기**에 **C\# 스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-538">Right-click inside the **Scripts** folder, click **Create**, **C\# Script**.</span></span> <span data-ttu-id="10ad9-539">스크립트 이름을 **CloudScene**</span><span class="sxs-lookup"><span data-stu-id="10ad9-539">Name the script **CloudScene**</span></span>
    
    <span data-ttu-id="10ad9-540">![새 c# 스크립트](images/AzureLabs-Lab8-72.png)
    ![CloudScene 이름 바꾸기](images/AzureLabs-Lab8-73.png)</span><span class="sxs-lookup"><span data-stu-id="10ad9-540">![new c# script](images/AzureLabs-Lab8-72.png)
![rename CloudScene](images/AzureLabs-Lab8-73.png)</span></span>

2.  <span data-ttu-id="10ad9-541">다음 네임 스페이스를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-541">Add the following namespaces:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using System.Threading.Tasks;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

3.  <span data-ttu-id="10ad9-542">다음 변수를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-542">Insert the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CloudScene instance;

        /// <summary>
        /// Insert here you Azure Function Url
        /// </summary>
        private string azureFunctionEndpoint = "--Insert here you Azure Function Endpoint--";

        /// <summary>
        /// Flag for object being moved
        /// </summary>
        private bool gameObjHasMoved;

        /// <summary>
        /// Transform of the object being dragged by the mouse
        /// </summary>
        private Transform gameObjHeld;

        /// <summary>
        /// Class hosted in the TableToScene script
        /// </summary>
        private AzureTableEntity azureTableEntity;
    ```

4.  <span data-ttu-id="10ad9-543">대체는 **azureFunctionEndpoint** 아래 이미지에 표시 된 대로 Azure Portal에서 Azure 함수 앱 서비스에 Azure 함수 앱 URL을 사용 하 여 값:</span><span class="sxs-lookup"><span data-stu-id="10ad9-543">Substitute the **azureFunctionEndpoint** value with your Azure Function App URL found in the Azure Function App Service, in the Azure Portal, as shown in the image below:</span></span>

    ![함수 URL 가져오기](images/AzureLabs-Lab8-74.png)

5.  <span data-ttu-id="10ad9-545">이제 추가 합니다 **start ()** 하 고 **Awake()** 클래스를 초기화 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-545">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // initialise an AzureTableEntity
            azureTableEntity = new AzureTableEntity();
        }
    ```

6.  <span data-ttu-id="10ad9-546">내 합니다 **update ()** 메서드 검색 마우스 입력 및 끌어서 장면에서 Gameobject 이동에 다음 코드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-546">Within the **Update()** method, add the following code that will detect the mouse input and drag, which will in turn move GameObjects in the scene.</span></span> <span data-ttu-id="10ad9-547">사용자가 끌어 하 고 개체를 삭제 하는 경우이 이름 및 개체의 좌표를 메서드에 전달할 **UpdateCloudScene()** 에 서비스 호출 하 여 Azure 함수 앱, Azure 테이블 및 트리거를 업데이트 하면는 알림입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-547">If the user has dragged and dropped an object, it will pass the name and coordinates of the object to the method **UpdateCloudScene()**, which will call the Azure Function App service, which will update the Azure table and trigger the notification.</span></span>

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            //Enable Drag if button is held down
            if (Input.GetMouseButton(0))
            {
                // Get the mouse position
                Vector3 mousePosition = new Vector3(Input.mousePosition.x, Input.mousePosition.y, 10);

                Vector3 objPos = Camera.main.ScreenToWorldPoint(mousePosition);

                Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);

                RaycastHit hit;

                // Raycast from the current mouse position to the object overlapped by the mouse
                if (Physics.Raycast(ray, out hit))
                {
                    // update the position of the object "hit" by the mouse
                    hit.transform.position = objPos;

                    gameObjHasMoved = true;

                    gameObjHeld = hit.transform;
                }
            }

            // check if the left button mouse is released while holding an object
            if (Input.GetMouseButtonUp(0) && gameObjHasMoved)
            {
                gameObjHasMoved = false;

                // Call the Azure Function that will update the appropriate Entity in the Azure Table
                // and send a Notification to all subscribed Apps
                Debug.Log("Calling Azure Function");

                StartCoroutine(UpdateCloudScene(gameObjHeld.name, gameObjHeld.position.x, gameObjHeld.position.y, gameObjHeld.position.z));
            }
        }
    ```

7.  <span data-ttu-id="10ad9-548">이제 추가 합니다 **UpdateCloudScene()** 아래와 같이 메서드:</span><span class="sxs-lookup"><span data-stu-id="10ad9-548">Now add the **UpdateCloudScene()** method, as below:</span></span>

    ```csharp
        private IEnumerator UpdateCloudScene(string objName, double xPos, double yPos, double zPos)
        {
            WWWForm form = new WWWForm();

            // set the properties of the AzureTableEntity
            azureTableEntity.RowKey = objName;

            azureTableEntity.X = xPos;

            azureTableEntity.Y = yPos;

            azureTableEntity.Z = zPos;

            // Serialize the AzureTableEntity object to be sent to Azure
            string jsonObject = JsonConvert.SerializeObject(azureTableEntity);

            using (UnityWebRequest www = UnityWebRequest.Post(azureFunctionEndpoint, jsonObject))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(jsonObject);

                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.uploadHandler.contentType = "application/json";

                www.downloadHandler = new DownloadHandlerBuffer();

                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                string response = www.responseCode.ToString();
            }
        }
    ```

8.  <span data-ttu-id="10ad9-549">코드를 저장 하 고 Unity에 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-549">Save the code and return to Unity</span></span>

9.  <span data-ttu-id="10ad9-550">끌기 합니다 **CloudScene** 에 스크립트를 **주 카메라**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-550">Drag the **CloudScene** script onto the **Main Camera**.</span></span> 

    1. <span data-ttu-id="10ad9-551">클릭 합니다 **주 카메라** 에서 **계층** 패널에서 해당 속성에 표시 되도록 합니다 **검사기**.</span><span class="sxs-lookup"><span data-stu-id="10ad9-551">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span> 

    2. <span data-ttu-id="10ad9-552">사용 하 여는 **스크립트** 폴더 열기를 선택 합니다 **CloudScene** 스크립팅하고 끕니다를 **주 카메라**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-552">With the **Scripts** folder open, select the **CloudScene** script and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="10ad9-553">결과 다음과 같이 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-553">The result should be as below:</span></span>

        > ![주 카메라 클라우드 스크립트 끌어](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a><span data-ttu-id="10ad9-555">11 장-uwp 데스크톱 프로젝트 빌드</span><span class="sxs-lookup"><span data-stu-id="10ad9-555">Chapter 11 - Build the Desktop Project to UWP</span></span>

<span data-ttu-id="10ad9-556">이 프로젝트의 Unity 섹션에 필요한 모든 항목이 이제 완료 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-556">Everything needed for the Unity section of this project has now been completed.</span></span>

1.  <span data-ttu-id="10ad9-557">이동할 **빌드 설정** (**파일** > **빌드 설정**).</span><span class="sxs-lookup"><span data-stu-id="10ad9-557">Navigate to **Build Settings** (**File** > **Build Settings**).</span></span>

2.  <span data-ttu-id="10ad9-558">**빌드 설정** 창에서 클릭 **빌드**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-558">From the **Build Settings** window, click **Build**.</span></span>

    ![프로젝트 빌드](images/AzureLabs-Lab8-76.png)

3.  <span data-ttu-id="10ad9-560">A **파일 탐색기** 창은 팝업에서 위치를 빌드에 대 한 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-560">A **File Explorer** window will popup, prompting you for a location to Build.</span></span> <span data-ttu-id="10ad9-561">새 폴더를 만듭니다 (클릭 하 여 **새 폴더** 왼쪽 위 모서리에), 이름을 **빌드**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-561">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![빌드에 대 한 새 폴더](images/AzureLabs-Lab8-77.png)

    1.  <span data-ttu-id="10ad9-563">새로운 **빌드** 폴더를 다른 폴더를 만들고 (사용 하 여 **새 폴더** 번), 하 고 이름을 **NH\_데스크톱\_앱**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-563">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **NH\_Desktop\_App**.</span></span>

        ![폴더 이름을 NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  <span data-ttu-id="10ad9-565">사용 하 여 합니다 **NH\_Desktop\_앱** 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-565">With the **NH\_Desktop\_App** selected.</span></span> <span data-ttu-id="10ad9-566">클릭 **폴더 선택**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-566">click **Select Folder**.</span></span> <span data-ttu-id="10ad9-567">프로젝트 빌드를 1 분 정도 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-567">The project will take a minute or so to build.</span></span>

4.  <span data-ttu-id="10ad9-568">다음 빌드에서 **파일 탐색기** 새 프로젝트의 위치를 표시 하는 데 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-568">Following build, **File Explorer** will appear showing you the location of your new project.</span></span> <span data-ttu-id="10ad9-569">그러나 다른을 만들어야 하는 대로 Unity 프로젝트 먼저 다음의 몇 장을 열 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-569">No need to open it, though, as you need to create the other Unity project first, in the next few Chapters.</span></span>


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a><span data-ttu-id="10ad9-570">12 장-혼합 현실 Unity 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="10ad9-570">Chapter 12 - Set up Mixed Reality Unity Project</span></span>

<span data-ttu-id="10ad9-571">다음은 일반적인 등록 혼합된 현실 등을 사용 하 여 개발 하는 것에 대 한와 따라서 다른 프로젝트에 대 한 좋은 템플릿입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-571">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="10ad9-572">오픈 **Unity** 누릅니다 **새로 만들기**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-572">Open **Unity** and click **New**.</span></span>

    ![새 unity 프로젝트](images/AzureLabs-Lab8-79.png)

2.  <span data-ttu-id="10ad9-574">Unity 프로젝트 이름을 제공 해야 이제 삽입 **UnityMRNotifHub**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-574">You will now need to provide a Unity Project name, insert **UnityMRNotifHub**.</span></span> <span data-ttu-id="10ad9-575">프로젝트 형식 설정 되어 있는지 확인 **3D**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-575">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="10ad9-576">설정 된 **위치** 적절 한 위치로 (기억에 루트 디렉터리에 가까울수록이 더 좋습니다).</span><span class="sxs-lookup"><span data-stu-id="10ad9-576">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="10ad9-577">그런 다음 클릭 **프로젝트 만들기**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-577">Then, click **Create project**.</span></span>

    ![name UnityMRNotifHub](images/AzureLabs-Lab8-80.png)

3.  <span data-ttu-id="10ad9-579">Unity 열기를 사용 하 여 기본 검사 가치가 **스크립트 편집기** 로 설정 된 **Visual Studio**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-579">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="10ad9-580">로 이동 **편집할** > **기본 설정** 로 이동한 다음 새 창에서 **외부 도구**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-580">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="10ad9-581">변경 **외부 스크립트 편집기** 하 **Visual Studio 2017**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-581">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="10ad9-582">닫기 합니다 **기본 설정** 창입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-582">Close the **Preferences** window.</span></span>

    ![vs 외부 편집기 설정](images/AzureLabs-Lab8-81.png)

4.  <span data-ttu-id="10ad9-584">이동한 다음 **파일** > **빌드 설정** 플랫폼에서 전환 **유니버설 Windows 플랫폼**를 클릭 하 여는 **플랫폼 전환**  단추입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-584">Next, go to **File** > **Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![UWP 플랫폼 전환](images/AzureLabs-Lab8-82.png)

5.  <span data-ttu-id="10ad9-586">로 이동 **파일** > **빌드 설정** 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-586">Go to **File** > **Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="10ad9-587">**장치를 대상** 로 설정 된 **모든 장치**</span><span class="sxs-lookup"><span data-stu-id="10ad9-587">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="10ad9-588">Microsoft HoloLens 설정 **대상 장치** 하 *HoloLens*합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-588">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="10ad9-589">**빌드 형식** 로 설정 된 **D3D**</span><span class="sxs-lookup"><span data-stu-id="10ad9-589">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="10ad9-590">**SDK** 로 설정 된 **가장 최근에 설치 된**</span><span class="sxs-lookup"><span data-stu-id="10ad9-590">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="10ad9-591">**Visual Studio 버전** 로 설정 된 **가장 최근에 설치 된**</span><span class="sxs-lookup"><span data-stu-id="10ad9-591">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="10ad9-592">**빌드 및 실행** 로 설정 된 **로컬 컴퓨터**</span><span class="sxs-lookup"><span data-stu-id="10ad9-592">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="10ad9-593">여기 하는 동안 가치가 장면 저장 하 고 빌드에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-593">While here, it is worth saving the scene, and adding it to the build.</span></span>

        1. <span data-ttu-id="10ad9-594">선택 하 여이 작업을 수행할 **열고 장면 추가**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-594">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="10ad9-595">창 저장 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-595">A save window will appear.</span></span>

            ![열기 장면 추가](images/AzureLabs-Lab8-83.png)

        2. <span data-ttu-id="10ad9-597">새 폴더를 만들려면이 고 모든의 미래, 장면에 대 한 다음 선택 합니다 **새 폴더** 새 폴더를 만들려면 단추 이름을 **장면**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-597">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![새 백그라운드에서 폴더](images/AzureLabs-Lab8-84.png)

        3. <span data-ttu-id="10ad9-599">새로 만든 열 **장면** 폴더를 선택한 다음는 **파일 이름:** 텍스트 필드에 입력 **NH\_MR\_장면**, 누릅니다  **저장**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-599">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **NH\_MR\_Scene**, then press **Save**.</span></span>

            ![new scene - NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  <span data-ttu-id="10ad9-601">설정에 남아 **빌드 설정**, 지금은 기본값으로 유지 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-601">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6.  <span data-ttu-id="10ad9-602">같은 창에서 클릭 하는 **플레이어 설정** 단추를 공간에 관련 된 패널이 열립니다이 위치는 **검사기** 위치한.</span><span class="sxs-lookup"><span data-stu-id="10ad9-602">In the same window click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>    

    ![플레이어 설정 열기](images/AzureLabs-Lab8-86.png)

7.  <span data-ttu-id="10ad9-604">이 패널에서 몇 가지 설정을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-604">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="10ad9-605">에 **기타 설정** 탭:</span><span class="sxs-lookup"><span data-stu-id="10ad9-605">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="10ad9-606">**스크립팅 런타임 버전** 있어야 **실험적** (.NET 4.6 동등)</span><span class="sxs-lookup"><span data-stu-id="10ad9-606">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent)</span></span>
        2.  <span data-ttu-id="10ad9-607">**백 엔드를 스크립팅** 있어야 ***.NET***</span><span class="sxs-lookup"><span data-stu-id="10ad9-607">**Scripting Backend** should be ***.NET***</span></span>
        3.  <span data-ttu-id="10ad9-608">**API 호환성 수준** 있어야 **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="10ad9-608">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![api 호환성](images/AzureLabs-Lab8-87.png)

    2.  <span data-ttu-id="10ad9-610">패널을 아래쪽의 **xr 하이 설정을** (아래에서 확인할 **게시 설정**), 눈금 **가상 현실 지원**, 있는지는 **Windows Mixed Reality SDK**  추가</span><span class="sxs-lookup"><span data-stu-id="10ad9-610">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added</span></span>

        ![xr 하이 설정 업데이트](images/AzureLabs-Lab8-88.png)        

    3.  <span data-ttu-id="10ad9-612">내 합니다 **게시 설정** 탭의 **기능**, 도대체:</span><span class="sxs-lookup"><span data-stu-id="10ad9-612">Within the **Publishing Settings** tab, under **Capabilities**, heck:</span></span>

        - <span data-ttu-id="10ad9-613">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="10ad9-613">**InternetClient**</span></span>           

            ![눈금 인터넷 클라이언트](images/AzureLabs-Lab8-89.png)

8.  <span data-ttu-id="10ad9-615">년대 **빌드 설정**를 **Unity C# 프로젝트** 를 더 이상 사용할 수 없습니다:이 옆의 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-615">Back in **Build Settings**, **Unity C# Projects** is no longer greyed out: tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="10ad9-616">이러한 변경과 수행할 빌드 설정 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-616">With these changes done, close the Build Settings window.</span></span>

10. <span data-ttu-id="10ad9-617">장면 및 프로젝트 저장할 **파일** > **장면 저장 파일** > **프로젝트를 저장할**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-617">Save your Scene and Project **File** > **Save Scene / File** > **Save Project**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="10ad9-618">건너뛸 하려는 경우는 *Unity 설정* (혼합 현실 앱)이이 프로젝트에 대 한 구성 요소 코드에 바로 계속를 자유롭게 [이.unitypackage 다운로드](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage),으로 프로젝트로가져올[ **사용자 지정 패키지**](https://docs.unity3d.com/Manual/AssetPackages.html)를 선택한 다음에서 계속 [14 장](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project)합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-618">If you wish to skip the *Unity Set up* component for this project (mixed reality App), and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project).</span></span> <span data-ttu-id="10ad9-619">스크립트 구성 요소를 추가 해야 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-619">You will still need to add the script components.</span></span>

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a><span data-ttu-id="10ad9-620">13 장-혼합된 현실 Unity 프로젝트에서 Dll 가져오기</span><span class="sxs-lookup"><span data-stu-id="10ad9-620">Chapter 13 - Importing the DLLs in the Mixed Reality Unity Project</span></span>

<span data-ttu-id="10ad9-621">Unity 라이브러리 (.NET SDK를 사용 하 여 Azure에 대 한)에 대 한 Azure Storage 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-621">You will be using Azure Storage for Unity library (which uses the .Net SDK for Azure).</span></span> <span data-ttu-id="10ad9-622">이 수행 하십시오 [Unity를 사용 하 여 Azure Storage를 사용 하는 방법에 대 한 링크](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-622">Please follow this [link on how to use Azure Storage with Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>
<span data-ttu-id="10ad9-623">플러그 인 가져오기 후 다시 구성 해야 하는 Unity의 알려진된 문제는 현재 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-623">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="10ad9-624">이러한 단계 (4-7이 단원의) 버그가 해결 된 후 필요한 더 이상.</span><span class="sxs-lookup"><span data-stu-id="10ad9-624">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="10ad9-625">사용자 고유의 프로젝트에 SDK를 가져오려면 최신 다운로드 했는지 확인 [.unitypackage](https://aka.ms/azstorage-unitysdk)합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-625">To import the SDK into your own project, make sure you have downloaded the latest [.unitypackage](https://aka.ms/azstorage-unitysdk).</span></span> <span data-ttu-id="10ad9-626">그런 다음 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-626">Then, do the following:</span></span>

1.  <span data-ttu-id="10ad9-627">Unity를 사용 하 여 위에서 다운로드 한.unitypackage를 추가 합니다 **자산** > **패키지 가져오기** > **Custom Package** 메뉴 옵션 .</span><span class="sxs-lookup"><span data-stu-id="10ad9-627">Add the .unitypackage you downloaded from the above, to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

2.  <span data-ttu-id="10ad9-628">에 **Unity 패키지 가져오기** 팝업에서 선택할 수 있는 아래에 있는 모든 상자 **플러그 인** > **저장소**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-628">In the **Import Unity Package** box that pops up, you can select everything under **Plugin** > **Storage**.</span></span>

    ![패키지 가져오기](images/AzureLabs-Lab8-90.png)

3.  <span data-ttu-id="10ad9-630">클릭 합니다 **가져오기** 프로젝트에 항목을 추가 하려면 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-630">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="10ad9-631">로 이동 합니다 **저장소** 아래에 폴더 **플러그 인** 프로젝트에서 표시 하 고 다음 플러그 인 선택 *만*:</span><span class="sxs-lookup"><span data-stu-id="10ad9-631">Go to the **Storage** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="10ad9-632">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="10ad9-632">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="10ad9-633">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="10ad9-633">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="10ad9-634">Microsoft.WindowsAzure.Storage</span><span class="sxs-lookup"><span data-stu-id="10ad9-634">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="10ad9-635">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="10ad9-635">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="10ad9-636">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="10ad9-636">System.Spatial</span></span>

    ![플러그 인 선택](images/AzureLabs-Lab8-91.png)

5.  <span data-ttu-id="10ad9-638">사용 하 여 *이러한 특정 플러그 인* 선택 하면 **의 선택을 취소** **Any 플랫폼** 고 **의 선택을 취소** **WSAPlayer** 누른 **적용**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-638">With *these specific plugins* selected, **uncheck** **Any Platform** and **uncheck** **WSAPlayer** then click **Apply**.</span></span>

    ![플랫폼 변경 내용 적용](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > <span data-ttu-id="10ad9-640">이러한 특정 플러그 인만 Unity 편집기에서 사용 하도록 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-640">You are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="10ad9-641">Unity에서 프로젝트를 내보낸 후 사용할 WSA 폴더에 같은 플러그 인의 다양 한 버전 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-641">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="10ad9-642">에 **저장소** 플러그 인 폴더에만 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-642">In the **Storage** plugin folder, select only:</span></span>

    -   <span data-ttu-id="10ad9-643">Microsoft.Data.Services.Client</span><span class="sxs-lookup"><span data-stu-id="10ad9-643">Microsoft.Data.Services.Client</span></span>

        ![data services 클라이언트를 선택 합니다.](images/AzureLabs-Lab8-93.png)

7.  <span data-ttu-id="10ad9-645">확인 합니다 **없는 프로세스** 상자에 **플랫폼 설정** 클릭 **적용**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-645">Check the **Don't Process** box under **Platform Settings** and click **Apply**.</span></span>

    ![처리 하지 않음](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > <span data-ttu-id="10ad9-647">표시 하는이 플러그 인 "처리 하지 않음" Unity 어셈블리 패 처가이 플러그 인을 처리 하는 데 문제가 있어.</span><span class="sxs-lookup"><span data-stu-id="10ad9-647">You are marking this plugin "Don't process" because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="10ad9-648">플러그 인 처리 되지 않습니다 하는 경우에 계속 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-648">The plugin will still work even though it isn't processed.</span></span>

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a><span data-ttu-id="10ad9-649">14 장-혼합된 현실 Unity 프로젝트에서 TableToScene 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="10ad9-649">Chapter 14 - Creating the TableToScene class in the mixed reality Unity project</span></span>

<span data-ttu-id="10ad9-650">합니다 **TableToScene** 클래스에 설명 된 것 같습니다 [9 장에서](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-650">The **TableToScene** class is identical to the one explained in [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span> <span data-ttu-id="10ad9-651">동일한 절차를 수행 하는 Unity 프로젝트에 설명 된 혼합된 현실에서 동일한 클래스를 만듭니다 [9 장에서](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-651">Create the same class in the mixed reality Unity Project following the same procedure explained in [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span>

<span data-ttu-id="10ad9-652">이 장의 모두 완료 한 후에 **Unity 프로젝트** 이 클래스는 주 카메라에서 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-652">Once you have completed this Chapter, both of your **Unity Projects** will have this class set up on the Main Camera.</span></span>

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a><span data-ttu-id="10ad9-653">15 장-혼합 현실 Unity 프로젝트에서 NotificationReceiver 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="10ad9-653">Chapter 15 - Creating the NotificationReceiver class in the Mixed Reality Unity Project</span></span>

<span data-ttu-id="10ad9-654">생성 해야 하는 두 번째 스크립트 **NotificationReceiver**를 담당 하는:</span><span class="sxs-lookup"><span data-stu-id="10ad9-654">The second script you need to create is **NotificationReceiver**, which is responsible for:</span></span>

-   <span data-ttu-id="10ad9-655">초기화 시 알림 허브를 사용 하 여 앱을 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-655">Registering the app with the Notification Hub at initialization.</span></span>
-   <span data-ttu-id="10ad9-656">알림 허브에서 보내는 알림을 수신 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-656">Listening to notifications coming from the Notification Hub.</span></span>
-   <span data-ttu-id="10ad9-657">받은 알림에서 개체 데이터를 역직렬화 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-657">Deserializing the object data from received notifications.</span></span>
-   <span data-ttu-id="10ad9-658">Deserialize 된 데이터를 기반으로 하는 장면에서의 Gameobject를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-658">Move the GameObjects in the scene, based on the deserialized data.</span></span>

<span data-ttu-id="10ad9-659">만들려는 합니다 **NotificationReceiver** 스크립트:</span><span class="sxs-lookup"><span data-stu-id="10ad9-659">To create the **NotificationReceiver** script:</span></span>

1.  <span data-ttu-id="10ad9-660">마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **만들기**에 **C\# 스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-660">Right-click inside the **Scripts** folder, click **Create**, **C\# Script**.</span></span> <span data-ttu-id="10ad9-661">스크립트 이름을 **NotificationReceiver**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-661">Name the script **NotificationReceiver**.</span></span>

    <span data-ttu-id="10ad9-662">![새 c# 스크립트를 만듭니다](images/AzureLabs-Lab8-95.png)
    ![NotificationReceiver 이름을](images/AzureLabs-Lab8-96.png)</span><span class="sxs-lookup"><span data-stu-id="10ad9-662">![create new c# script](images/AzureLabs-Lab8-95.png)
![name it NotificationReceiver](images/AzureLabs-Lab8-96.png)</span></span>

2.  <span data-ttu-id="10ad9-663">열려는 스크립트를 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-663">Double click on the script to open it.</span></span>

3.  <span data-ttu-id="10ad9-664">다음 네임 스페이스를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-664">Add the following namespaces:</span></span>

    ```csharp
    //using Microsoft.WindowsAzure.Messaging;
    using Newtonsoft.Json;
    using System;
    using System.Collections;
    using UnityEngine;

    #if UNITY_WSA_10_0 && !UNITY_EDITOR
    using Windows.Networking.PushNotifications;
    #endif
    ```

4.  <span data-ttu-id="10ad9-665">다음 변수를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-665">Insert the following variables:</span></span>

    ```csharp
        /// <summary>
        /// allows this class to behave like a singleton
        /// </summary>
        public static NotificationReceiver instance;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        Vector3 newObjPosition;

        /// <summary>
        /// Value set by the notification, object name
        /// </summary>
        string gameObjectName;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        bool notifReceived;

        /// <summary>
        /// Insert here your Notification Hub Service name 
        /// </summary>
        private string hubName = " -- Insert the name of your service -- ";

        /// <summary>
        /// Insert here your Notification Hub Service "Listen endpoint"
        /// </summary>
        private string hubListenEndpoint = "-Insert your Notification Hub Service Listen endpoint-";
    ```

5.  <span data-ttu-id="10ad9-666">대체는 **hubName** 알림 허브 서비스 이름, 값 및 **hubListenEndpoint** Azure 알림 허브 서비스, 액세스 정책 탭에 있는 끝점 값을 사용 하 여 값을 Azure Portal (아래 이미지 참조).</span><span class="sxs-lookup"><span data-stu-id="10ad9-666">Substitute the **hubName** value with your Notification Hub Service name, and **hubListenEndpoint** value with the endpoint value found in the Access Policies tab, Azure Notification Hub Service, in the Azure Portal (see image below).</span></span>

    ![notification hubs 정책 끝점 삽입](images/AzureLabs-Lab8-97.png)

6.  <span data-ttu-id="10ad9-668">이제 추가 합니다 **start ()** 하 고 **Awake()** 클래스를 초기화 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-668">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Register the App at launch
            InitNotificationsAsync();

            // Begin listening for notifications
            StartCoroutine(WaitForNotification());
        }
    ```

7.  <span data-ttu-id="10ad9-669">추가 된 **WaitForNotification** 주 스레드를 사용 하 여 충돌 없이 Notification Hub 라이브러리에서 알림을 받도록 앱을 허용 하는 방법.</span><span class="sxs-lookup"><span data-stu-id="10ad9-669">Add the **WaitForNotification** method to allow the app to receive notifications from the Notification Hub Library without clashing with the Main Thread:</span></span>

    ```csharp
        /// <summary>
        /// This notification listener is necessary to avoid clashes 
        /// between the notification hub and the main thread   
        /// </summary>
        private IEnumerator WaitForNotification()
        {
            while (true)
            {
                // Checks for notifications each second
                yield return new WaitForSeconds(1f);

                if (notifReceived)
                {
                    // If a notification is arrived, moved the appropriate object to the new position
                    GameObject.Find(gameObjectName).transform.position = newObjPosition;

                    // Reset the flag
                    notifReceived = false;
                }
            }
        }
    ```

8.  <span data-ttu-id="10ad9-670">다음 메서드를 **InitNotificationAsync()** , 초기화 시 알림 허브 서비스를 사용 하 여 응용 프로그램을 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-670">The following method, **InitNotificationAsync()**, will register the application with the notification Hub Service at initialization.</span></span> <span data-ttu-id="10ad9-671">코드 주석 처리 되어 Unity 프로젝트를 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-671">The code is commented out as Unity will not be able to Build the project.</span></span> <span data-ttu-id="10ad9-672">Visual Studio에서 Azure 메시징 Nuget 패키지를 가져올 때 주석을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-672">You will remove the comments when you import the Azure Messaging Nuget package in Visual Studio.</span></span>

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            // PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            // NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            // Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            // if (result.RegistrationId != null)
            // {
            //     Debug.Log($"Registration Successful: {result.RegistrationId}");
            //     channel.PushNotificationReceived += Channel_PushNotificationReceived;
            // }
        }
    ```

9.  <span data-ttu-id="10ad9-673">다음 처리기 **채널\_PushNotificationReceived()** , 알림의 받을 때마다 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-673">The following handler, **Channel\_PushNotificationReceived()**, will be triggered every time a notification is received.</span></span> <span data-ttu-id="10ad9-674">데스크톱 응용 프로그램을 이동 된 Azure 테이블 엔터티로 이동한 다음 해당 GameObject MR 장면에서 같은 위치에 있는 알림을 역직렬화 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-674">It will deserialize the notification, which will be the Azure Table Entity that has been moved on the Desktop Application, and then move the corresponding GameObject in the MR scene to the same position.</span></span> 
    
    > [!IMPORTANT]
    > <span data-ttu-id="10ad9-675">코드를 Visual Studio 내에서 Nuget 패키지 관리자를 사용 하 여 Unity 프로젝트를 빌드한 후 추가 하는 Azure 메시징 라이브러리에 참조 하기 때문에 코드는 주석입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-675">The code is commented out because the code references the Azure Messaging library, which you will add after building the Unity project using the Nuget Package Manager, within Visual Studio.</span></span> <span data-ttu-id="10ad9-676">따라서 Unity 프로젝트 주석으로 처리 하지 않는 한 없습니다를 빌드할 수 됩니다. 수는 해야 프로젝트를 빌드 및 Unity에 반환 하려면 해야 **주석 다시** 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-676">As such, the Unity project will not be able to build, unless it is commented out. Be aware, that should you build your project, and then wish to return to Unity, you will need to **re-comment** that code.</span></span>

    ```csharp
        ///// <summary>
        ///// Handler called when a Push Notification is received
        ///// </summary>
        //private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)    
        //{
        //    Debug.Log("New Push Notification Received");
        //
        //    if (args.NotificationType == PushNotificationType.Raw)
        //    {
        //        //  Raw content of the Notification
        //        string jsonContent = args.RawNotification.Content;
        //
        //        // Deserialise the Raw content into an AzureTableEntity object
        //        AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);
        //
        //        // The name of the Game Object to be moved
        //        gameObjectName = ate.RowKey;          
        //
        //        // The position where the Game Object has to be moved
        //        newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);
        //
        //        // Flag thats a notification has been received
        //        notifReceived = true;
        //    }
        //}
    ```

10. <span data-ttu-id="10ad9-677">Unity 편집기로 다시 이동 하기 전에 변경 내용을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-677">Remember to save your changes before going back to the Unity Editor.</span></span>

11. <span data-ttu-id="10ad9-678">클릭 합니다 **주 카메라** 에서 **계층** 패널에서 해당 속성에 표시 되도록 합니다 **검사기**.</span><span class="sxs-lookup"><span data-stu-id="10ad9-678">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span>

12. <span data-ttu-id="10ad9-679">사용 하 여는 **스크립트** 폴더 열기를 선택 합니다 **NotificationReceiver** 스크립팅하고 끕니다를 **주 카메라**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-679">With the **Scripts** folder open, select the **NotificationReceiver** script and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="10ad9-680">결과 다음과 같이 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-680">The result should be as below:</span></span>

    ![카메라에 알림 수신기 스크립트를 끌어 옵니다.](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > <span data-ttu-id="10ad9-682">를 개발 하는이 Microsoft HoloLens 대 한 업데이트 해야 합니다는 **주 카메라**의 *카메라* 구성 요소 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-682">If you are developing this for the Microsoft HoloLens, you will need to update the **Main Camera**'s *Camera* component, so that:</span></span>
    > - <span data-ttu-id="10ad9-683">플래그를 지웁니다. 단색</span><span class="sxs-lookup"><span data-stu-id="10ad9-683">Clear Flags: Solid Color</span></span>
    > - <span data-ttu-id="10ad9-684">Background: 검정</span><span class="sxs-lookup"><span data-stu-id="10ad9-684">Background: Black</span></span>

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a><span data-ttu-id="10ad9-685">16 장-uwp 혼합된 현실 프로젝트 빌드</span><span class="sxs-lookup"><span data-stu-id="10ad9-685">Chapter 16 - Build the Mixed Reality Project to UWP</span></span>

<span data-ttu-id="10ad9-686">이 장에서 빌드 프로세스는 이전 프로젝트에 대 한 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-686">This Chapter is identical to build process for the previous project.</span></span> <span data-ttu-id="10ad9-687">이 프로젝트의 Unity 섹션에 필요한 모든 항목이 이제 완료 되 면 Unity에서 작성 하는 시간 이므로 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-687">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="10ad9-688">이동할 **빌드 설정** ( **파일** > **빌드 설정** ).</span><span class="sxs-lookup"><span data-stu-id="10ad9-688">Navigate to **Build Settings** ( **File** > **Build Settings** ).</span></span>

2.  <span data-ttu-id="10ad9-689">**빌드 설정** 메뉴에서 확인 **Unity C# 프로젝트**\* 선택 됩니다 (수 있는이 프로젝트의 스크립트는 빌드 후 편집 하려면).</span><span class="sxs-lookup"><span data-stu-id="10ad9-689">From the **Build Settings** menu, ensure **Unity C# Projects**\* is ticked (which will allow you to edit the scripts in this project, after build).</span></span>

3.  <span data-ttu-id="10ad9-690">이 완료 되 면 클릭 **빌드**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-690">After this is done, click **Build**.</span></span>

    ![프로젝트 빌드](images/AzureLabs-Lab8-99.png)

4.  <span data-ttu-id="10ad9-692">A **파일 탐색기** 창은 팝업에서 위치를 빌드에 대 한 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-692">A **File Explorer** window will popup, prompting you for a location to Build.</span></span> <span data-ttu-id="10ad9-693">새 폴더를 만듭니다 (클릭 하 여 **새 폴더** 왼쪽 위 모서리에), 이름을 **빌드**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-693">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![빌드 폴더 만들기](images/AzureLabs-Lab8-100.png)

    1.  <span data-ttu-id="10ad9-695">새로운 **빌드** 폴더를 다른 폴더를 만들고 (사용 하 여 **새 폴더** 번), 하 고 이름을 **NH\_MR\_앱**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-695">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **NH\_MR\_App**.</span></span>

        ![NH_MR_Apps 폴더 만들기](images/AzureLabs-Lab8-101.png)

    2.  <span data-ttu-id="10ad9-697">사용 하 여 합니다 **NH\_MR\_앱** 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-697">With the **NH\_MR\_App** selected.</span></span> <span data-ttu-id="10ad9-698">클릭 **폴더 선택**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-698">click **Select Folder**.</span></span> <span data-ttu-id="10ad9-699">프로젝트 빌드를 1 분 정도 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-699">The project will take a minute or so to build.</span></span>

5.  <span data-ttu-id="10ad9-700">다음 빌드에는 **파일 탐색기** 새 프로젝트의 위치에서 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-700">Following the build, a **File Explorer** window will open at the location of your new project.</span></span>



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a><span data-ttu-id="10ad9-701">17 장-UnityMRNotifHub 솔루션에 NuGet 패키지 추가</span><span class="sxs-lookup"><span data-stu-id="10ad9-701">Chapter 17 - Add NuGet packages to the UnityMRNotifHub Solution</span></span>

> [!WARNING] 
> <span data-ttu-id="10ad9-702">해제해 서는 다음 NuGet 패키지를 추가 하면 (다음에서 코드를 주석 처리 제거 [장](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)), 코드를 Unity 프로젝트 내에서 다시 열 때 오류가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-702">Please remember that, once you add the following NuGet Packages (and uncomment the code in the next [Chapter](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)), the Code, when reopened within the Unity Project, will present errors.</span></span> <span data-ttu-id="10ad9-703">뒤로 돌아가서 Unity 편집기의 편집을 계속 하려는 경우 해당 errosome 코드를 주석으로 한 Visual Studio에서 다시 되 면 나중에 다시 주석 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-703">If you wish to go back and continue editing in the Unity Editor, you will need comment that errosome code, and then uncomment again later, once you are back in Visual Studio.</span></span> 

<span data-ttu-id="10ad9-704">혼합된 현실 빌드가 완료 되 면 혼합된 현실 프로젝트를 빌드한로 이동 및 Visual Studio 2017을 사용 하 여 솔루션을 열려면 해당 폴더 내의 솔루션 (.sln) 파일을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-704">Once the mixed reality build has been completed, navigate to the mixed reality project, which you built, and double click on the solution (.sln) file within that folder, to open your solution with Visual Studio 2017.</span></span>
<span data-ttu-id="10ad9-705">이제 추가 해야 합니다 **WindowsAzure.Messaging.managed** NuGet 패키지를 알림 허브에서 알림을 수신 하는 데 사용 되는 라이브러리입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-705">You will now need to add the **WindowsAzure.Messaging.managed** NuGet package; this is a library that is used to receive Notifications from the Notification Hub.</span></span>

<span data-ttu-id="10ad9-706">NuGet 패키지를 가져오려면:</span><span class="sxs-lookup"><span data-stu-id="10ad9-706">To import the NuGet package:</span></span>

1.  <span data-ttu-id="10ad9-707">에 **솔루션 탐색기**, 솔루션을 마우스 오른쪽 단추로 클릭</span><span class="sxs-lookup"><span data-stu-id="10ad9-707">In the **Solution Explorer**, right click on your Solution</span></span>

2.  <span data-ttu-id="10ad9-708">클릭할 **NuGet 패키지 관리**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-708">Click on **Manage NuGet Packages**.</span></span>

    ![nuget 관리자를 열려면](images/AzureLabs-Lab8-102.png)

3.  <span data-ttu-id="10ad9-710">선택 된 ***찾아보기*** 탭 및 검색할 **WindowsAzure.Messaging.managed**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-710">Select the ***Browse*** tab and search for **WindowsAzure.Messaging.managed**.</span></span>

    ![windows azure 메시징 패키지 찾기](images/AzureLabs-Lab8-103.png)

4.  <span data-ttu-id="10ad9-712">결과 (아래와 같이)를 선택 하 고 오른쪽 창에서의 확인란을 선택 옆 **프로젝트**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-712">Select the result (as shown below), and in the window to the right, select the checkbox next to **Project**.</span></span> <span data-ttu-id="10ad9-713">이 틱의에서 배치 확인란 옆에 **프로젝트**, 옆에 있는 확인란이 함께 합니다 **어셈블리 CSharp** 하 고 **UnityMRNotifHub** 프로젝트.</span><span class="sxs-lookup"><span data-stu-id="10ad9-713">This will place a tick in the checkbox next to **Project**, along with the checkbox next to the **Assembly-CSharp** and **UnityMRNotifHub** project.</span></span>

    ![모든 프로젝트를 선택 합니다.](images/AzureLabs-Lab8-104.png)

5.  <span data-ttu-id="10ad9-715">처음에 제공 된 버전이 **아닐** 이 프로젝트와 호환 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-715">The version initially provided **may not** be compatible with this project.</span></span> <span data-ttu-id="10ad9-716">따라서 옆에 드롭다운 메뉴에서 클릭 **버전**, 클릭 **버전 0.1.7.9**, 클릭 **설치**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-716">Therefore, click on the dropdown menu next to **Version**, and click **Version 0.1.7.9**, then click **Install**.</span></span>

6.  <span data-ttu-id="10ad9-717">이제 NuGet 패키지 설치를 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-717">You have now finished installing the NuGet package.</span></span> <span data-ttu-id="10ad9-718">에 입력 한 설명이 포함 된 코드를 **NotificationReceiver** 클래스 및 주석을 제거...</span><span class="sxs-lookup"><span data-stu-id="10ad9-718">Find the commented code you entered in the **NotificationReceiver** class and remove the comments..</span></span>



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a><span data-ttu-id="10ad9-719">18 장-편집 UnityMRNotifHub 응용 프로그램, NotificationReceiver 클래스</span><span class="sxs-lookup"><span data-stu-id="10ad9-719">Chapter 18 - Edit UnityMRNotifHub application, NotificationReceiver class</span></span>

<span data-ttu-id="10ad9-720">추가한 경우 다음 합니다 **NuGet 패키지**, 해야 *주석 처리를 제거* 내에서 코드의 일부를 **NotificationReceiver** 클래스.</span><span class="sxs-lookup"><span data-stu-id="10ad9-720">Following having added the **NuGet Packages**, you will need to *uncomment* some of the code within the **NotificationReceiver** class.</span></span>

<span data-ttu-id="10ad9-721">다음을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-721">This includes:</span></span>

1. <span data-ttu-id="10ad9-722">맨 위에 있는 네임 스페이스:</span><span class="sxs-lookup"><span data-stu-id="10ad9-722">The namespace at the top:</span></span>

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. <span data-ttu-id="10ad9-723">내의 모든 코드를 **InitNotificationsAsync()** 메서드:</span><span class="sxs-lookup"><span data-stu-id="10ad9-723">All the code within the **InitNotificationsAsync()** method:</span></span>

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            if (result.RegistrationId != null)
            {
                Debug.Log($"Registration Successful: {result.RegistrationId}");
                channel.PushNotificationReceived += Channel_PushNotificationReceived;
            }
        }
    ```

> [!WARNING]
> <span data-ttu-id="10ad9-724">위의 코드에 주석을: 했는지 실수로 *주석 처리가 제거 된* (코드는 컴파일되지 않습니다 경우!)으로 주석입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-724">The code above has a comment in it: ensure that you have not accidentally *uncommented* that comment (as the code will not compile if you have!).</span></span>

3. <span data-ttu-id="10ad9-725">마지막으로, 합니다 **Channel_PushNotificationReceived** 이벤트:</span><span class="sxs-lookup"><span data-stu-id="10ad9-725">And, lastly, the **Channel_PushNotificationReceived** event:</span></span>

    ```csharp
        /// <summary>
        /// Handler called when a Push Notification is received
        /// </summary>
        private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)
        {
            Debug.Log("New Push Notification Received");

            if (args.NotificationType == PushNotificationType.Raw)
            {
                //  Raw content of the Notification
                string jsonContent = args.RawNotification.Content;

                // Deserialize the Raw content into an AzureTableEntity object
                AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);

                // The name of the Game Object to be moved
                gameObjectName = ate.RowKey;

                // The position where the Game Object has to be moved
                newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);

                // Flag thats a notification has been received
                notifReceived = true;
            }
        }
    ```

<span data-ttu-id="10ad9-726">이러한 주석 처리가 제거 된를 사용 하 여 저장 하 고 다음 장에서를 계속 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-726">With these uncommented, ensure that you save, and then proceed to the next Chapter.</span></span>

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a><span data-ttu-id="10ad9-727">19 장-스토어 앱에 혼합된 현실 프로젝트 연결</span><span class="sxs-lookup"><span data-stu-id="10ad9-727">Chapter 19 - Associate the mixed reality project to the Store app</span></span>

<span data-ttu-id="10ad9-728">연결 해야 합니다 **혼합 현실을** 스토어 앱 랩의 시작에서 만든 프로젝트입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-728">You now need to associate the **mixed reality** project to the Store App you created in at the start of the lab.</span></span>

1.  <span data-ttu-id="10ad9-729">솔루션을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-729">Open the solution.</span></span>

2.  <span data-ttu-id="10ad9-730">이동 하려면 솔루션 탐색기 창에서 UWP 앱 프로젝트를 마우스 오른쪽 단추로 클릭 **스토어**, 및 **스토어와 앱을 연결 하는 중...** .</span><span class="sxs-lookup"><span data-stu-id="10ad9-730">Right click on the UWP app Project in the Solution Explorer panel, the go to **Store**, and **Associate App with the Store...**.</span></span>

    ![저장소 연결을 열기](images/AzureLabs-Lab8-105.png)

3.  <span data-ttu-id="10ad9-732">새 창을 호출 나타납니다 **Windows 스토어와 앱 연결**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-732">A new window will appear called **Associate Your App with the Windows Store**.</span></span> <span data-ttu-id="10ad9-733">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-733">Click **Next**.</span></span>

    ![다음 화면으로 이동](images/AzureLabs-Lab8-106.png)

4.  <span data-ttu-id="10ad9-735">로그인 하는 계정에 연결 된 모든 응용 프로그램을 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-735">It will load up all the Applications associated with the Account which you have logged in.</span></span> <span data-ttu-id="10ad9-736">계정에 로그인 하지 않은 경우 **로그인** 페이지입니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-736">If you are not logged in to your account, you can **Log In** on this page.</span></span>

5.  <span data-ttu-id="10ad9-737">찾을 합니다 **스토어 앱 이름을** 이 자습서의 시작 부분에 만들고 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-737">Find the **Store App name** that you created at the start of this tutorial and select it.</span></span> <span data-ttu-id="10ad9-738">그리고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-738">Then click **Next**.</span></span>

    ![찾기 및 저장소 이름을 선택합니다](images/AzureLabs-Lab8-107.png)

6.  <span data-ttu-id="10ad9-740">클릭 **연결**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-740">Click **Associate**.</span></span>

    ![앱 연결](images/AzureLabs-Lab8-108.png)

7.  <span data-ttu-id="10ad9-742">앱이 이제 **관련 된** 스토어 앱을 사용 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-742">Your App is now **Associated** with the Store App.</span></span> <span data-ttu-id="10ad9-743">이 알림을 사용 하도록 설정 하는 데 필요한 경우</span><span class="sxs-lookup"><span data-stu-id="10ad9-743">This is necessary for enabling Notifications.</span></span>

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a><span data-ttu-id="10ad9-744">20 장-UnityMRNotifHub 및 UnityDesktopNotifHub 응용 프로그램 배포</span><span class="sxs-lookup"><span data-stu-id="10ad9-744">Chapter 20 - Deploy UnityMRNotifHub and UnityDesktopNotifHub applications</span></span>

<span data-ttu-id="10ad9-745">이 장에서 실행 되는 앱, 데스크톱 컴퓨터에서 실행 중인 컴퓨터를 한와 몰입 형 헤드셋 내에서 다른 결과가 포함 됩니다 두 사람이 사용 하 여 더 쉬울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-745">This Chapter may be easier with two people, as the result will include both apps running, one running on your computer Desktop, and the other within your immersive headset.</span></span>

<span data-ttu-id="10ad9-746">몰입 형 헤드셋 앱 장면 (로컬 Gameobject의 위치 변경)에 변경 내용을 수신 대기 중인 및 데스크톱 앱은 변경할 수 MR 앱에 공유 되는 해당 로컬 장면 (위치 변경).</span><span class="sxs-lookup"><span data-stu-id="10ad9-746">The immersive headset app is waiting to receive changes to the scene (position changes of the local GameObjects), and the Desktop app will be making changes to their local scene (position changes), which will be shared to the MR app.</span></span> <span data-ttu-id="10ad9-747">데스크톱 앱은 뒤에 수신기에서 수신 대기를 시작할 수 있도록 MR 앱을 먼저 배포 하는 것이 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-747">It makes sense to deploy the MR app first, followed by the Desktop app, so that the receiver can begin listening.</span></span>

<span data-ttu-id="10ad9-748">배포 하는 **UnityMRNotifHub** 로컬 컴퓨터에 앱:</span><span class="sxs-lookup"><span data-stu-id="10ad9-748">To deploy the **UnityMRNotifHub** app on your Local Machine:</span></span>

1.  <span data-ttu-id="10ad9-749">솔루션 파일을 열고 프로그램 **UnityMRNotifHub** 에서 앱 **Visual Studio 2017**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-749">Open the solution file of your **UnityMRNotifHub** app in **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="10ad9-750">에 **솔루션 플랫폼**를 선택 **x86, 로컬 컴퓨터**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-750">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="10ad9-751">에 **솔루션 구성** 선택 **디버그**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-751">In the **Solution Configuration** select **Debug**.</span></span>

    ![프로젝트 구성 설정](images/AzureLabs-Lab8-109.png)

4.  <span data-ttu-id="10ad9-753">로 이동 **빌드 메뉴** 을 클릭할 **솔루션 배포** 을 컴퓨터에 응용 프로그램을 사이드 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-753">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="10ad9-754">이제 앱 시작할 준비가 되었습니다. 설치 된 앱 목록에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-754">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

<span data-ttu-id="10ad9-755">배포 하는 **UnityDesktopNotifHub** 로컬 컴퓨터에서 앱:</span><span class="sxs-lookup"><span data-stu-id="10ad9-755">To deploy the **UnityDesktopNotifHub** app on Local Machine:</span></span>

1.  <span data-ttu-id="10ad9-756">솔루션 파일을 열고 프로그램 **UnityDesktopNotifHub** 에서 앱 **Visual Studio 2017**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-756">Open the solution file of your **UnityDesktopNotifHub** app in **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="10ad9-757">에 **솔루션 플랫폼**를 선택 **x86, 로컬 컴퓨터**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-757">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="10ad9-758">에 **솔루션 구성** 선택 **디버그**합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-758">In the **Solution Configuration** select **Debug**.</span></span>

    ![프로젝트 구성 설정](images/AzureLabs-Lab8-110.png)

4.  <span data-ttu-id="10ad9-760">로 이동 **빌드 메뉴** 을 클릭할 **솔루션 배포** 을 컴퓨터에 응용 프로그램을 사이드 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-760">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="10ad9-761">이제 앱 시작할 준비가 되었습니다. 설치 된 앱 목록에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-761">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

6.  <span data-ttu-id="10ad9-762">뒤에 데스크톱 응용 프로그램 혼합된 현실 응용 프로그램을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-762">Launch the mixed reality application, followed by the Desktop application.</span></span>

<span data-ttu-id="10ad9-763">실행 중인 두 응용 프로그램을 사용 하 여 (왼쪽 마우스 단추를 사용 하 여) 데스크톱 장면에 개체를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-763">With both applications running, move an object in the desktop scene (using the Left Mouse Button).</span></span> <span data-ttu-id="10ad9-764">이러한 위치 변경 내용은 로컬로 만든, serialize 되며 함수 앱 서비스로 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-764">These positional changes will be made locally, serialized, and sent to the Function App service.</span></span> <span data-ttu-id="10ad9-765">함수 앱 서비스에서 알림 허브와 함께 테이블을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-765">The Function App service will then update the Table along with the Notification Hub.</span></span> <span data-ttu-id="10ad9-766">업데이트를 수신, 알림 허브는 보내기 업데이트 된 데이터를 직접 모든 등록 된 응용 프로그램 (이 경우 몰입 형 헤드셋 앱), 그러면 들어오는 데이터를 deserialize 하 고 로컬 개체에 새 위치 데이터를 적용 합니다. 장면에서 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-766">Having received an update, the Notification Hub will send the updated data directly to all the registered applications (in this case the immersive headset app), which will then deserialize the incoming data, and apply the new positional data to the local objects, moving them in scene.</span></span>


## <a name="your-finished-your-azure-notification-hubs-application"></a><span data-ttu-id="10ad9-767">사용자 Azure Notification Hubs 응용 프로그램을 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-767">Your finished your Azure Notification Hubs application</span></span>
 
<span data-ttu-id="10ad9-768">축, Azure Notification Hubs 서비스를 활용 하 고 앱 간의 통신을 허용 하는 혼합된 현실 앱을 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="10ad9-768">Congratulations, you built a mixed reality app that leverages the Azure Notification Hubs Service and allow communication between apps.</span></span>
 
![최종 제품-종료](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a><span data-ttu-id="10ad9-770">보너스 연습</span><span class="sxs-lookup"><span data-stu-id="10ad9-770">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="10ad9-771">연습 1</span><span class="sxs-lookup"><span data-stu-id="10ad9-771">Exercise 1</span></span>

<span data-ttu-id="10ad9-772">장면을 보는 다른 앱으로 해당 알림을 보내고는 Gameobject의 색을 변경 하는 방법을 사용할 수 있습니다?</span><span class="sxs-lookup"><span data-stu-id="10ad9-772">Can you work out how to change the color of the GameObjects and send that notification to other apps viewing the scene?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="10ad9-773">연습 2</span><span class="sxs-lookup"><span data-stu-id="10ad9-773">Exercise 2</span></span>

<span data-ttu-id="10ad9-774">수는 Gameobject 이동을 MR 앱에 추가 하 고 데스크톱 앱에서 업데이트 된 장면을 참조 하세요?</span><span class="sxs-lookup"><span data-stu-id="10ad9-774">Can you add movement of the GameObjects to your MR app and see the updated scene in your desktop app?</span></span>
