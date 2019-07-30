---
title: MR 및 Azure 308-장치 간 알림
description: 이 과정을 완료 하 여 혼합 현실 응용 프로그램 내에서 Azure Notification Hubs, Azure Functions 및 Azure Storage와 테이블을 구현 하는 방법을 알아보세요.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, 아카데미, unity, 자습서, api, 알림, 기능, 테이블, notification hubs, hololens, 몰입 형, vr
ms.openlocfilehash: 3b6e930acd81c7d6e3addc107ec0da605d38cad1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694609"
---
>[!NOTE]
><span data-ttu-id="ef024-104">혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="ef024-105">따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="ef024-106">이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="ef024-107">지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="ef024-108">향후에는 HoloLens 2를 개발 하는 방법을 보여 주는 새 자습서 시리즈를 게시할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="ef024-109">이 알림은 게시 될 때 해당 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-308-cross-device-notifications"></a><span data-ttu-id="ef024-110">MR 및 Azure 308: 장치 간 알림</span><span class="sxs-lookup"><span data-stu-id="ef024-110">MR and Azure 308: Cross-device notifications</span></span>

![최종 제품-시작](images/AzureLabs-Lab8-00.png)

<span data-ttu-id="ef024-112">이 과정에서는 Azure Notification Hubs, Azure 테이블 및 Azure Functions를 사용 하 여 혼합 현실 응용 프로그램에 Notification Hubs 기능을 추가 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-112">In this course, you will learn how to add Notification Hubs capabilities to a mixed reality application using Azure Notification Hubs, Azure Tables, and Azure Functions.</span></span>

<span data-ttu-id="ef024-113">**Azure Notification Hubs** 는 개발자가 대상 및 개인 설정 된 푸시 알림을 모든 플랫폼에 보낼 수 있도록 하는 Microsoft 서비스입니다. 모두 클라우드 내에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-113">**Azure Notification Hubs** is a Microsoft service, which allows developers to send targeted and personalized push notifications to any platform, all powered within the cloud.</span></span> <span data-ttu-id="ef024-114">이를 통해 개발자는 시나리오에 따라 최종 사용자와 통신 하거나 다양 한 응용 프로그램 간에 통신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-114">This can effectively allow developers to communicate with end users, or even communicate between various applications, depending on the scenario.</span></span> <span data-ttu-id="ef024-115">자세한 내용은 **Azure Notification Hubs** [페이지](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ef024-115">For more information, visit the **Azure Notification Hubs** [page](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview).</span></span>

<span data-ttu-id="ef024-116">**Azure Functions** 는 개발자가 Azure에서 작은 코드, ' 함수 '를 실행할 수 있도록 해 주는 Microsoft 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-116">**Azure Functions** is a Microsoft service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="ef024-117">이렇게 하면 다양 한 이점을 얻을 수 있는 로컬 응용 프로그램이 아닌 클라우드로 작업을 위임할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-117">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="ef024-118">**Azure Functions** 는 C\#, F\#, node.js, Java 및 PHP를 비롯 한 몇 가지 개발 언어를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-118">**Azure Functions** supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="ef024-119">자세한 내용은 **Azure Functions** [페이지](https://docs.microsoft.com/azure/azure-functions/functions-overview)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ef024-119">For more information, visit the **Azure Functions** [page](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="ef024-120">**Azure Tables** 는 개발자가 구조화 되지 않은 SQL 데이터를 클라우드에 저장 하 여 어디서 나 쉽게 액세스할 수 있도록 하는 Microsoft 클라우드 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-120">**Azure Tables** is a Microsoft cloud service, which allows developers to store structured non-SQL data in the cloud, making it easily accessible anywhere.</span></span> <span data-ttu-id="ef024-121">이 서비스는 스키마 boasts 디자인 하 여 필요에 따라 테이블의 진화를 허용 하므로 매우 유연 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-121">The service boasts a schemaless design, allowing for the evolution of tables as needed, and thus is very flexible.</span></span> <span data-ttu-id="ef024-122">자세한 내용은 **Azure Tables** [페이지](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ef024-122">For more information, visit the **Azure Tables** [page](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span></span>

<span data-ttu-id="ef024-123">이 과정을 완료 한 후에는 다음과 같은 작업을 수행할 수 있는 혼합 현실 모던 헤드셋 응용 프로그램 및 데스크톱 PC 응용 프로그램이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-123">Having completed this course, you will have a mixed reality immersive headset application, and a Desktop PC application, which will be able to do the following:</span></span>

1. <span data-ttu-id="ef024-124">데스크톱 PC 앱을 사용 하면 사용자가 마우스를 사용 하 여 2D 공간 (X 및 Y)으로 개체를 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-124">The Desktop PC app will allow the user to move an object in 2D space (X and Y), using the mouse.</span></span>

2. <span data-ttu-id="ef024-125">PC 앱 내의 개체 이동은 JSON을 사용 하 여 클라우드로 전송 됩니다. JSON은 개체 ID, 유형 및 변환 정보 (X 및 Y 좌표)를 포함 하는 문자열 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-125">The movement of objects within the PC app will be sent to the cloud using JSON, which will be in the form of a string, containing an object ID, type, and transform information (X and Y coordinates).</span></span> 

3. <span data-ttu-id="ef024-126">데스크톱 앱과 동일한 장면을 포함 하는 혼합 현실 앱은 데스크톱 PC 앱에 의해 업데이트 된 Notification Hubs 서비스에서 개체 이동에 대 한 알림을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-126">The mixed reality app, which has an identical scene to the desktop app, will receive notifications regarding object movement, from the Notification Hubs service (which has just been updated by the Desktop PC app).</span></span> 

4. <span data-ttu-id="ef024-127">개체 ID, 유형 및 변환 정보를 포함 하는 알림이 수신 되 면 혼합 현실 앱은 수신 된 정보를 자신의 장면에 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-127">Upon receiving a notification, which will contain the object ID, type, and transform information, the mixed reality app will apply the received information to its own scene.</span></span>

<span data-ttu-id="ef024-128">응용 프로그램에서 결과를 디자인과 통합 하는 방법을 사용자가 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-128">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="ef024-129">이 과정은 Azure 서비스를 Unity 프로젝트와 통합 하는 방법을 배울 수 있도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-129">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="ef024-130">이 과정에서 얻은 지식을 사용 하 여 혼합 현실 응용 프로그램을 개선 하는 것은 사용자의 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-130">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span> <span data-ttu-id="ef024-131">이 과정은 다른 혼합 현실 랩을 직접 포함 하지 않는 자체 포함 된 자습서입니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-131">This course is a self-contained tutorial, which does not directly involve any other Mixed Reality Labs.</span></span>

## <a name="device-support"></a><span data-ttu-id="ef024-132">장치 지원</span><span class="sxs-lookup"><span data-stu-id="ef024-132">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="ef024-133">과정</span><span class="sxs-lookup"><span data-stu-id="ef024-133">Course</span></span></th><th style="width:150px"> <span data-ttu-id="ef024-134"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="ef024-134"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="ef024-135"><a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="ef024-135"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="ef024-136">MR 및 Azure 308: 장치 간 알림</span><span class="sxs-lookup"><span data-stu-id="ef024-136">MR and Azure 308: Cross-device notifications</span></span></td><td style="text-align: center;"> <span data-ttu-id="ef024-137">✔️</span><span class="sxs-lookup"><span data-stu-id="ef024-137">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="ef024-138">✔️</span><span class="sxs-lookup"><span data-stu-id="ef024-138">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="ef024-139">이 과정에서 주로 Windows Mixed Reality (VR) 헤드셋에 초점을 맞춘 반면,이 과정에서 학습 하는 내용을 Microsoft HoloLens에도 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-139">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="ef024-140">과정을 진행할 때 HoloLens를 지원 하기 위해 사용 해야 하는 모든 변경 내용에 대 한 메모를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-140">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="ef024-141">HoloLens를 사용 하는 경우 음성 캡처 중에 몇 가지 echo를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-141">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ef024-142">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="ef024-142">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="ef024-143">이 자습서는 Unity 및 C#에 대 한 기본 경험이 있는 개발자를 위해 작성 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-143">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="ef024-144">또한이 문서에서 사전 요구 사항 및 작성 된 지침은 작성 시 테스트 되 고 확인 된 내용 (2018 일 수 있음)을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-144">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="ef024-145">[도구 설치](install-the-tools.md) 문서에 나와 있는 것 처럼 최신 소프트웨어를 무료로 사용할 수 있지만,이 과정의 정보가 아래 나열 된 것 보다 최신 소프트웨어에서 찾을 수 있는 것으로 간주 하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-145">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="ef024-146">이 과정에는 다음 하드웨어 및 소프트웨어를 권장 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-146">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="ef024-147">모던 (VR) 헤드셋 개발을 위한 [Windows Mixed Reality와 호환 되](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 는 개발 PC</span><span class="sxs-lookup"><span data-stu-id="ef024-147">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="ef024-148">개발자 모드를 사용 하는 Windows 10이 하 버전의 작성자 업데이트 (또는 이상)</span><span class="sxs-lookup"><span data-stu-id="ef024-148">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ef024-149">최신 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="ef024-149">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ef024-150">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="ef024-150">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ef024-151">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="ef024-151">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="ef024-152">개발자 모드가 사용 하도록 설정 된 [Windows Mixed Reality 모던 (VR) 헤드셋](immersive-headset-hardware-details.md) 또는 [Microsoft HoloLens](hololens-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="ef024-152">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="ef024-153">Azure 설치 및 Notification Hubs 액세스를 위한 인터넷 액세스</span><span class="sxs-lookup"><span data-stu-id="ef024-153">Internet access for Azure setup and to access Notification Hubs</span></span>

## <a name="before-you-start"></a><span data-ttu-id="ef024-154">시작하기 전 주의 사항</span><span class="sxs-lookup"><span data-stu-id="ef024-154">Before you start</span></span>

- <span data-ttu-id="ef024-155">이 프로젝트를 빌드하는 데 문제가 발생 하지 않도록 하려면 루트 또는 루트 폴더에이 자습서에서 언급 한 프로젝트를 만드는 것이 좋습니다. (긴 폴더 경로는 빌드 시에 문제를 일으킬 수 있습니다.)</span><span class="sxs-lookup"><span data-stu-id="ef024-155">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
- <span data-ttu-id="ef024-156">Microsoft 개발자 포털 및 응용 프로그램 등록 포털의 소유자 여야 합니다. 그렇지 않으면 [2 장의](#chapter-2---retrieve-your-new-apps-credentials)앱에 액세스할 수 있는 권한이 없는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-156">You must be the owner of your Microsoft Developer Portal and your Application Registration Portal, otherwise you will not have permission to access the app in [Chapter 2](#chapter-2---retrieve-your-new-apps-credentials).</span></span>

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a><span data-ttu-id="ef024-157">1 장-Microsoft 개발자 포털에서 응용 프로그램 만들기</span><span class="sxs-lookup"><span data-stu-id="ef024-157">Chapter 1 - Create an application on the Microsoft Developer Portal</span></span>

<span data-ttu-id="ef024-158">**Azure Notification Hubs** 서비스를 사용 하려면 응용 프로그램을 등록 해야 하므로 알림을 보내고 받을 수 있도록 Microsoft 개발자 포털에서 응용 프로그램을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-158">To use the **Azure Notification Hubs** Service, you will need to create an Application on the Microsoft Developer Portal, as your application will need to be registered, so that it can send and receive notifications.</span></span>

1.  <span data-ttu-id="ef024-159">[Microsoft 개발자 포털](https://developer.microsoft.com/dashboard)에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-159">Log in to the [Microsoft Developer Portal](https://developer.microsoft.com/dashboard).</span></span>

    > <span data-ttu-id="ef024-160">Microsoft 계정에 로그인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-160">You will need to log in to your Microsoft Account.</span></span>

2.  <span data-ttu-id="ef024-161">대시보드에서 **새 앱 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-161">From the Dashboard, click **Create a new app**.</span></span>

    ![앱 만들기](images/AzureLabs-Lab8-01.png)

3.  <span data-ttu-id="ef024-163">새 앱의 이름을 예약 해야 하는 팝업이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-163">A popup will appear, wherein you need to reserve a name for your new app.</span></span> <span data-ttu-id="ef024-164">텍스트 상자에 적절 한 이름을 삽입 합니다. 선택한 이름을 사용할 수 있으면 텍스트 상자의 오른쪽에 눈금이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-164">In the textbox, insert an appropriate name; if the chosen name is available, a tick will appear to the right of the textbox.</span></span> <span data-ttu-id="ef024-165">사용 가능한 이름을 삽입 한 후에는 팝업의 왼쪽 아래에 있는 **제품 이름 예약** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-165">Once you have an available name inserted, click the **Reserve product name** button to the bottom left of the popup.</span></span>

    ![이름 바꾸기](images/AzureLabs-Lab8-02.png)

4.  <span data-ttu-id="ef024-167">이제 앱을 만들었으므로 다음 장으로 이동할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-167">With the app now created, you are ready to move to the next Chapter.</span></span>

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a><span data-ttu-id="ef024-168">2 장-새 앱 자격 증명 검색</span><span class="sxs-lookup"><span data-stu-id="ef024-168">Chapter 2 - Retrieve your new apps credentials</span></span>

<span data-ttu-id="ef024-169">새 앱이 나열 되는 응용 프로그램 등록 포털에 로그인 하 고 **Azure Portal**내에서 **Notification Hubs 서비스** 를 설정 하는 데 사용 되는 자격 증명을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-169">Log into the Application Registration Portal, where your new app will be listed, and retrieve the credentials which will be used to setup the **Notification Hubs Service** within the **Azure Portal**.</span></span>

1.  <span data-ttu-id="ef024-170">[응용 프로그램 등록 포털](http://apps.dev.microsoft.com)로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-170">Navigate to the [Application Registration Portal](http://apps.dev.microsoft.com).</span></span>

    ![응용 프로그램 등록 포털](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > <span data-ttu-id="ef024-172">로그인 하려면 Microsoft 계정을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-172">You will need to use your Microsoft Account to Login.</span></span>  
    > <span data-ttu-id="ef024-173">Windows 스토어 개발자 포털을 사용 하 여 이전 [챕터](#chapter-1---create-an-application-on-the-microsoft-developer-portal)에서 사용한 Microsoft 계정 **이어야 합니다** .</span><span class="sxs-lookup"><span data-stu-id="ef024-173">This **must** be the Microsoft Account which you used in the previous [Chapter](#chapter-1---create-an-application-on-the-microsoft-developer-portal), with the Windows Store Developer portal.</span></span>

2.  <span data-ttu-id="ef024-174">**내 응용 프로그램** 섹션에서 앱을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-174">You will find your app under the **My applications** section.</span></span> <span data-ttu-id="ef024-175">해당 파일을 찾으면 앱 이름 및 **등록**을 포함 하는 새 페이지로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-175">Once you have found it, click on it and you will be taken to a new page which has the app name plus **Registration**.</span></span>

    ![새로 등록 된 앱](images/AzureLabs-Lab8-04.png)

3.  <span data-ttu-id="ef024-177">등록 페이지 아래로 스크롤하여 **응용 프로그램 암호** 섹션과 앱에 대 한 **패키지 SID** 를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-177">Scroll down the registration page to find your **Application Secrets** section and the **Package SID** for your app.</span></span> <span data-ttu-id="ef024-178">다음 장에서 **Azure Notification Hubs 서비스** 를 설정 하는 데 사용할 두 가지를 모두 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-178">Copy both for use with setting up the **Azure Notification Hubs Service** in the next Chapter.</span></span>

    ![응용 프로그램 암호](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a><span data-ttu-id="ef024-180">3 장-Azure Portal 설정: Notification Hubs 서비스 만들기</span><span class="sxs-lookup"><span data-stu-id="ef024-180">Chapter 3 - Setup Azure Portal: create Notification Hubs Service</span></span>

<span data-ttu-id="ef024-181">앱 자격 증명이 검색 되 면 azure Notification Hubs 서비스를 만들 Azure Portal로 이동 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-181">With your apps credentials retrieved, you will need to go to the Azure Portal, where you will create an Azure Notification Hubs Service.</span></span>

1.  <span data-ttu-id="ef024-182">[Azure Portal](https://portal.azure.com)에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-182">Log into the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE] 
    > <span data-ttu-id="ef024-183">아직 Azure 계정이 없는 경우 새로 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-183">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="ef024-184">교실 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 proctors 중 하나에 문의 하 여 새 계정을 설정 하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-184">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="ef024-185">로그인 되 면 왼쪽 위 모서리에서 **새로 만들기** 를 클릭 하 고 **알림 허브**를 검색 한 다음 ***Enter 키***를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-185">Once you are logged in, click on **New** in the top left corner, and search for **Notification Hub**, and click ***Enter***.</span></span>

    ![알림 허브 검색](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > <span data-ttu-id="ef024-187">새 단어는 ***새*** 포털에서 **리소스 만들기**로 대체 되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-187">The word ***New*** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="ef024-188">새 페이지에 *Notification Hubs* 서비스에 대 한 설명이 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-188">The new page will provide a description of the *Notification Hubs* service.</span></span> <span data-ttu-id="ef024-189">이 프롬프트의 왼쪽 아래에서 **만들기** 단추를 선택 하 여이 서비스와의 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-189">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![notification hubs 인스턴스 만들기](images/AzureLabs-Lab8-07.png)

4.  <span data-ttu-id="ef024-191">***만들기***를 클릭 하면 다음을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-191">Once you have clicked on ***Create***:</span></span>

    1.  <span data-ttu-id="ef024-192">이 서비스 인스턴스의 원하는 이름을 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-192">Insert your desired name for this service instance.</span></span>

    2.  <span data-ttu-id="ef024-193">이 앱에 연결할 수 있는 **네임 스페이스** 를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-193">Provide a **namespace** which you will be able to associate with this app.</span></span>

    3.  <span data-ttu-id="ef024-194">위치를 선택 **합니다.**</span><span class="sxs-lookup"><span data-stu-id="ef024-194">Select a **Location.**</span></span>

    4.  <span data-ttu-id="ef024-195">리소스 그룹을 선택 하거나 새 **리소스 그룹** 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-195">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="ef024-196">리소스 그룹은 Azure 자산의 컬렉션에 대 한 청구를 모니터링 하 고, 액세스를 제어 하 고, 프로 비전 하 고, 관리 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-196">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="ef024-197">단일 프로젝트와 연결 된 모든 Azure 서비스 (예: 이러한 랩)를 공용 리소스 그룹에 유지 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-197">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="ef024-198">Azure 리소스 그룹에 대 한 자세한 내용을 보려면 [리소스 그룹을 관리 하는 방법에 대](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)한 다음 링크를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ef024-198">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span> 

    5.  <span data-ttu-id="ef024-199">적절 한 **구독**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-199">Select an appropriate **Subscription**.</span></span>

    6.  <span data-ttu-id="ef024-200">또한이 서비스에 적용 된 사용 약관을 이해 했는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-200">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7. <span data-ttu-id="ef024-201">**만들기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-201">Select **Create**.</span></span>

        ![서비스 정보 입력](images/AzureLabs-Lab8-08.png)

5.  <span data-ttu-id="ef024-203">**만들기**를 클릭 한 후에는 서비스를 만들 때까지 기다려야 합니다 .이 작업이 몇 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-203">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="ef024-204">서비스 인스턴스를 만든 후 알림이 포털에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-204">A notification will appear in the portal once the Service instance is created.</span></span>

    ![알림(notification)](images/AzureLabs-Lab8-09.png)

7.  <span data-ttu-id="ef024-206">알림에서 **리소스로 이동** 단추를 클릭 하 여 새 서비스 인스턴스를 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-206">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="ef024-207">새 **알림 허브** 서비스 인스턴스로 이동 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-207">You will be taken to your new **Notification Hub** service instance.</span></span>

    ![리소스로 이동](images/AzureLabs-Lab8-10.png)
    
8.  <span data-ttu-id="ef024-209">개요 페이지의 페이지 아래쪽에서 **Windows (WNS)를 클릭 합니다.**</span><span class="sxs-lookup"><span data-stu-id="ef024-209">From the overview page, halfway down the page, click **Windows (WNS).**</span></span> <span data-ttu-id="ef024-210">오른쪽의 패널은 이전에 설정한 앱에서 **패키지 SID** 및 **보안 키**를 필요로 하는 두 개의 텍스트 필드를 표시 하도록 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-210">The panel on the right will change to show two text fields, which require your **Package SID** and **Security Key**, from the app you set up previously.</span></span>

    ![새로 만든 허브 서비스](images/AzureLabs-Lab8-11.png)

9. <span data-ttu-id="ef024-212">세부 정보를 올바른 필드에 복사한 후에는 **저장**을 클릭 합니다. 그러면 알림 허브가 성공적으로 업데이트 되 면 알림이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-212">Once you have copied the details into the correct fields, click **Save**, and you will receive a notification when the Notification Hub has been successfully updated.</span></span>

    ![보안 세부 정보 복사](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a><span data-ttu-id="ef024-214">4 장-Azure Portal 설정: 테이블 서비스 만들기</span><span class="sxs-lookup"><span data-stu-id="ef024-214">Chapter 4 - Setup Azure Portal: create Table Service</span></span>

<span data-ttu-id="ef024-215">Notification Hubs 서비스 인스턴스를 만든 후에는 Azure Portal로 다시 이동 합니다. 여기서 저장소 리소스를 만들어 Azure Tables 서비스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-215">After creating your Notification Hubs Service instance, navigate back to your Azure Portal, where you will create an Azure Tables Service by creating a Storage Resource.</span></span>

1.  <span data-ttu-id="ef024-216">아직 로그인 하지 않은 경우 [Azure Portal](https://portal.azure.com)에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-216">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2.  <span data-ttu-id="ef024-217">로그인 되 면 왼쪽 위 모서리에서 **새로 만들기** 를 클릭 하 고 **저장소 계정**을 검색 한 다음 **Enter 키**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-217">Once logged in, click on **New** in the top left corner, and search for **Storage account**, and click **Enter**.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="ef024-218">새 단어는 ***새*** 포털에서 **리소스 만들기**로 대체 되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-218">The word ***New*** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="ef024-219">목록에서 **저장소 계정-blob, 파일, 테이블, 큐** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-219">Select **Storage account - blob, file, table, queue** from the list.</span></span>

    ![저장소 계정 검색](images/AzureLabs-Lab8-13.png)

4.  <span data-ttu-id="ef024-221">새 페이지에 **저장소 계정** 서비스에 대 한 설명이 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-221">The new page will provide a description of the **Storage account** service.</span></span> <span data-ttu-id="ef024-222">이 프롬프트의 왼쪽 아래에서 **만들기** 단추를 선택 하 여이 서비스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-222">At the bottom left of this prompt, select the **Create** button, to create an instance of this service.</span></span>

    ![저장소 인스턴스 만들기](images/AzureLabs-Lab8-14.png)

5.  <span data-ttu-id="ef024-224">**만들기**를 클릭 하면 패널이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-224">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="ef024-225">이 서비스 인스턴스의 원하는 **이름을** 삽입 합니다 (모두 소문자 여야 함).</span><span class="sxs-lookup"><span data-stu-id="ef024-225">Insert your desired **Name** for this service instance (must be all lowercase).</span></span>

    2. <span data-ttu-id="ef024-226">**배포 모델**에서 **리소스 관리자**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-226">For **Deployment model**, click **Resource manager**.</span></span>

    3.  <span data-ttu-id="ef024-227">**계정 종류**의 경우 드롭다운 메뉴에서 **저장소 (범용 v1)** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-227">For **Account kind**, using the dropdown menu, select **Storage (general purpose v1)**.</span></span>

    4. <span data-ttu-id="ef024-228">적절 한 **위치**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-228">Select an appropriate **Location**.</span></span>
    
    5.  <span data-ttu-id="ef024-229">**복제** 드롭다운 메뉴에서 **읽기 액세스-지역 중복 저장소 (RA-GRS)** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-229">For the **Replication** dropdown menu, select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6.  <span data-ttu-id="ef024-230">**성능**으로 **표준**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-230">For **Performance**, click **Standard**.</span></span>

    7.  <span data-ttu-id="ef024-231">**보안 전송 필요** 섹션에서 **사용 안 함**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-231">Within the **Secure transfer required** section, select **Disabled**.</span></span>

    8.  <span data-ttu-id="ef024-232">**구독** 드롭다운 메뉴에서 적절 한 구독을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-232">From the **Subscription** dropdown menu, select an appropriate subscription.</span></span>

    9.  <span data-ttu-id="ef024-233">리소스 그룹을 선택 하거나 새 **리소스 그룹** 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-233">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="ef024-234">리소스 그룹은 Azure 자산의 컬렉션에 대 한 청구를 모니터링 하 고, 액세스를 제어 하 고, 프로 비전 하 고, 관리 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-234">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="ef024-235">단일 프로젝트와 연결 된 모든 Azure 서비스 (예: 이러한 랩)를 공용 리소스 그룹에 유지 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-235">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="ef024-236">Azure 리소스 그룹에 대 한 자세한 내용을 보려면 [리소스 그룹을 관리 하는 방법에 대](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)한 다음 링크를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ef024-236">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="ef024-237">이 옵션을 선택 하는 경우 **가상 네트워크** 를 **사용 하지 않도록 설정** 된 상태로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-237">Leave **Virtual networks** as **Disabled** if this is an option for you.</span></span>

    11. <span data-ttu-id="ef024-238">**만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-238">Click **Create**.</span></span>

        ![저장소 정보 입력](images/AzureLabs-Lab8-15.png)

6.  <span data-ttu-id="ef024-240">**만들기**를 클릭 한 후에는 서비스를 만들 때까지 기다려야 합니다 .이 작업이 몇 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-240">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="ef024-241">서비스 인스턴스를 만든 후 알림이 포털에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-241">A notification will appear in the portal once the Service instance is created.</span></span> <span data-ttu-id="ef024-242">알림을 클릭 하 여 새 서비스 인스턴스를 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-242">Click on the notifications to explore your new Service instance.</span></span>

    ![새 저장소 알림](images/AzureLabs-Lab8-16.png)

8.  <span data-ttu-id="ef024-244">알림에서 **리소스로 이동** 단추를 클릭 하 여 새 서비스 인스턴스를 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-244">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="ef024-245">새 저장소 서비스 인스턴스 개요 페이지로 이동 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-245">You will be taken to your new Storage Service instance overview page.</span></span>

    ![리소스로 이동](images/AzureLabs-Lab8-17.PNG)

9. <span data-ttu-id="ef024-247">개요 페이지에서 오른쪽에 있는 **테이블**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-247">From the overview page, to the right-hand side, click **Tables**.</span></span>
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. <span data-ttu-id="ef024-248">오른쪽의 패널은 새 테이블을 추가 해야 하는 **Table service** 정보를 표시 하도록 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-248">The panel on the right will change to show the **Table service** information, wherein you need to add a new table.</span></span> <span data-ttu-id="ef024-249">왼쪽 위 모서리에 있는 **+** **테이블** 단추를 클릭 하 여이 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-249">Do this by clicking the **+** **Table** button to the top-left corner.</span></span>

    ![테이블 열기](images/AzureLabs-Lab8-19.png)

11. <span data-ttu-id="ef024-251">**테이블 이름을**입력 해야 하는 새 페이지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-251">A new page will be shown, wherein you need to enter a **Table name**.</span></span> <span data-ttu-id="ef024-252">이 이름은 이후 장에서 응용 프로그램의 데이터를 참조 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-252">This is the name you will use to refer to the data in your application in later Chapters.</span></span> <span data-ttu-id="ef024-253">적절 한 이름을 삽입 하 고 **확인을**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-253">Insert an appropriate name and click **OK**.</span></span>

    ![새 테이블 만들기](images/AzureLabs-Lab8-20.png)    

12. <span data-ttu-id="ef024-255">새 테이블을 만든 후에는 **Table service** 페이지 (아래쪽)에서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-255">Once the new table has been created, you will be able to see it within the **Table service** page (at the bottom).</span></span>

    ![새 테이블을 만들었습니다.](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a><span data-ttu-id="ef024-257">5 장-Visual Studio에서 Azure 테이블 완료</span><span class="sxs-lookup"><span data-stu-id="ef024-257">Chapter 5 - Completing the Azure Table in Visual Studio</span></span>

<span data-ttu-id="ef024-258">이제 **Table service** storage 계정이 설정 되었으므로 데이터를 추가 하 여 정보를 저장 하 고 검색 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-258">Now that your **Table service** storage account has been setup, it is time to add data to it, which will be used to store and retrieve information.</span></span> <span data-ttu-id="ef024-259">테이블 편집은 **Visual Studio**를 통해 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-259">The editing of your Tables can be done through **Visual Studio**.</span></span>

1.  <span data-ttu-id="ef024-260">**Visual Studio**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-260">Open **Visual Studio**.</span></span>

2.  <span data-ttu-id="ef024-261">메뉴에서**클라우드 탐색기** **보기** > 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-261">From the menu, click **View** > **Cloud Explorer**.</span></span>

    ![클라우드 탐색기 열기](images/AzureLabs-Lab8-22.png)

3.  <span data-ttu-id="ef024-263">**클라우드 탐색기** 은 도킹 된 항목으로 열립니다. 로드 시 시간이 걸릴 수 있으므로 잠시 기다려 주십시오.</span><span class="sxs-lookup"><span data-stu-id="ef024-263">The **Cloud Explorer** will open as a docked item (be patient, as loading may take time).</span></span>

    > [!NOTE] 
    > <span data-ttu-id="ef024-264">*저장소 계정을* 만드는 데 사용한 구독이 표시 되지 않는 경우 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-264">If the Subscription you used to create your *Storage Accounts* is not visible, ensure that you have:</span></span> 
    > - <span data-ttu-id="ef024-265">Azure Portal에 사용한 것과 동일한 계정에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-265">Logged in to the same account as the one you used for the Azure Portal.</span></span>
    > - <span data-ttu-id="ef024-266">계정 관리 페이지에서 구독을 선택 했습니다 (계정 설정에서 필터를 적용 해야 할 수 있음).</span><span class="sxs-lookup"><span data-stu-id="ef024-266">Selected your Subscription from the Account Management Page (you may need to apply a filter from your account settings):</span></span>  
    >
    >   ![구독 찾기](images/AzureLabs-Lab8-22-5.png)

4.  <span data-ttu-id="ef024-268">Azure cloud services가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-268">Your Azure cloud services will be shown.</span></span> <span data-ttu-id="ef024-269">**저장소 계정을** 찾고 왼쪽에 있는 화살표를 클릭 하 여 계정을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-269">Find **Storage Accounts** and click the arrow to the left of that to expand your accounts.</span></span>

    ![저장소 계정 열기](images/AzureLabs-Lab8-23.png)

5.  <span data-ttu-id="ef024-271">확장 되 면 새로 만든 **저장소 계정을** 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-271">Once expanded, your newly created **Storage account** should be available.</span></span> <span data-ttu-id="ef024-272">저장소 왼쪽에 있는 화살표를 클릭 한 다음 확장 되 면 **테이블** 을 찾아 해당 옆의 화살표를 클릭 하 여 마지막 챕터에서 만든 **테이블** 을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-272">Click the arrow to the left of your storage, and then once that is expanded, find **Tables** and click the arrow next to that, to reveal the **Table** you created in the last Chapter.</span></span> <span data-ttu-id="ef024-273">**테이블**을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-273">Double click your **Table**.</span></span>

    ![장면 개체 테이블 열기](images/AzureLabs-Lab8-24.png)

6.  <span data-ttu-id="ef024-275">Visual Studio 창의 중앙에서 테이블이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-275">Your table will be opened in the center of your Visual Studio window.</span></span> <span data-ttu-id="ef024-276">**+** (더하기)가 있는 테이블 아이콘을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-276">Click the table icon with the **+** (plus) on it.</span></span>

    ![새 테이블 추가](images/AzureLabs-Lab8-25.png)

7.  <span data-ttu-id="ef024-278">*엔터티를 추가*하 라는 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-278">A window will appear prompting for you to *Add Entity*.</span></span> <span data-ttu-id="ef024-279">각각 몇 가지 속성을 포함 하는 세 개의 엔터티를 전체로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-279">You will create three entities in total, each with several properties.</span></span> <span data-ttu-id="ef024-280">*PartitionKey* 및 *rowkey* 는 테이블에서 데이터를 찾기 위해 사용 되므로 이미 제공 된 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-280">You will notice that *PartitionKey* and *RowKey* are already provided, as these are used by the table to find your data.</span></span> 

    ![파티션 및 행 키](images/AzureLabs-Lab8-26.png)

8. <span data-ttu-id="ef024-282">다음과 같이 **PartitionKey** 및 **rowkey** *값* 을 업데이트 합니다. 즉, 사용자가 추가 하는 각 행 속성에 대해이 작업을 수행 해야 하지만 매번 rowkey를 증가 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-282">Update the *Value* of the **PartitionKey** and **RowKey** as follows (remember to do this for each row property you add, though increment the RowKey each time):</span></span>

    ![올바른 값 추가](images/AzureLabs-Lab8-26-5.png)

9.  <span data-ttu-id="ef024-284">데이터 행을 더 추가 하려면 **속성 추가** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-284">Click **Add property** to add extra rows of data.</span></span> <span data-ttu-id="ef024-285">첫 번째 빈 테이블이 아래 표와 일치 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-285">Make your first empty table match the below table.</span></span>

10. <span data-ttu-id="ef024-286">작업이 완료 되 면 **확인을** 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-286">Click **OK** when you are finished.</span></span>

    ![완료 되 면 확인을 클릭 합니다.](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > <span data-ttu-id="ef024-288">**X**, **Y**, **Z**항목의 **형식을** **Double**로 변경 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-288">Ensure that you have changed the **Type** of the **X**, **Y**, and **Z**, entries to **Double**.</span></span> 

11. <span data-ttu-id="ef024-289">이제 테이블에 데이터 행이 있다는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-289">You will notice your table now has a row of data.</span></span> <span data-ttu-id="ef024-290">**+** (더하기) 아이콘을 다시 클릭 하 여 다른 엔터티를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-290">Click the **+** (plus) icon again to add another entity.</span></span>

    ![첫 번째 행](images/AzureLabs-Lab8-27-5.png)

12. <span data-ttu-id="ef024-292">추가 속성을 만든 다음 아래 표시 된 것과 일치 하도록 새 엔터티의 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-292">Create an additional property, and then set the values of the new entity to match those shown below.</span></span>

    ![큐브 추가](images/AzureLabs-Lab8-28.png)

13. <span data-ttu-id="ef024-294">마지막 단계를 반복 하 여 다른 엔터티를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-294">Repeat the last step to add another entity.</span></span> <span data-ttu-id="ef024-295">이 엔터티의 값을 아래에 표시 된 값으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-295">Set the values for this entity to those shown below.</span></span>

    ![원통 추가](images/AzureLabs-Lab8-29.png)

14. <span data-ttu-id="ef024-297">이제 테이블이 아래와 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-297">Your table should now look like the one below.</span></span>

    ![테이블 완료](images/AzureLabs-Lab8-30.png)

15. <span data-ttu-id="ef024-299">이 챕터를 완료 했습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-299">You have completed this Chapter.</span></span> <span data-ttu-id="ef024-300">저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-300">Make sure to save.</span></span>

## <a name="chapter-6---create-an-azure-function-app"></a><span data-ttu-id="ef024-301">6 장-Azure 함수 앱 만들기</span><span class="sxs-lookup"><span data-stu-id="ef024-301">Chapter 6 - Create an Azure Function App</span></span>

<span data-ttu-id="ef024-302">데스크톱 응용 프로그램에서 **테이블** 서비스를 업데이트 하 고 알림 **허브**를 통해 알림을 보내기 위해 호출 하는 Azure 함수 앱를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-302">Create an Azure Function App, which will be called by the Desktop application to update the **Table** service and send a notification through the **Notification Hub**.</span></span>

<span data-ttu-id="ef024-303">먼저 Azure 함수에서 필요한 라이브러리를 로드 하도록 허용 하는 파일을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-303">First, you need to create a file that will allow your Azure Function to load the libraries you need.</span></span>

1.  <span data-ttu-id="ef024-304">**메모장** 을 엽니다 (Windows 키를 누르고 메모장을 입력).</span><span class="sxs-lookup"><span data-stu-id="ef024-304">Open **Notepad** (press Windows Key and type notepad).</span></span>

    ![메모장 열기](images/AzureLabs-Lab8-31.png)

2.  <span data-ttu-id="ef024-306">메모장을 열고 아래에 JSON 구조를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-306">With Notepad open, insert the JSON structure below into it.</span></span> <span data-ttu-id="ef024-307">이 작업을 완료 한 후에는 데스크톱에 프로젝트를 **json**으로 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-307">Once you have done that, save it on your desktop as **project.json**.</span></span> <span data-ttu-id="ef024-308">이름 지정이 올바른지 확인 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-308">It is important that the naming is correct: ensure it does **NOT have a .txt** file extension.</span></span> <span data-ttu-id="ef024-309">이 파일은 함수가 사용 하는 라이브러리를 정의 합니다. NuGet을 사용 하는 경우 익숙할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-309">This file defines the libraries your function will use, if you have used NuGet it will look familiar.</span></span>

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

3.  <span data-ttu-id="ef024-310">[Azure Portal](https://portal.azure.com)에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-310">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

4.  <span data-ttu-id="ef024-311">로그인 되 면 왼쪽 위 모서리에서 **새로 만들기** 를 클릭 하 고 **함수 앱**를 검색 한 후 **enter**키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-311">Once you are logged in, click on **New** in the top left corner, and search for **Function App**, press **Enter**.</span></span>

    ![함수 앱 검색](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > <span data-ttu-id="ef024-313">새 단어는 **새** 포털에서 **리소스 만들기**로 대체 되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-313">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

5.  <span data-ttu-id="ef024-314">새 페이지에 **함수 앱** 서비스에 대 한 설명이 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-314">The new page will provide a description of the **Function App** service.</span></span> <span data-ttu-id="ef024-315">이 프롬프트의 왼쪽 아래에서 **만들기** 단추를 선택 하 여이 서비스와의 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-315">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![함수 앱 인스턴스](images/AzureLabs-Lab8-33.png)

6.  <span data-ttu-id="ef024-317">**만들기**를 클릭 한 후에는 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-317">Once you have clicked on **Create**, fill in the following:</span></span>

    1. <span data-ttu-id="ef024-318">**앱 이름**에 대해 원하는 이름을이 서비스 인스턴스에 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-318">For **App name**, insert your desired name for this service instance.</span></span>

    2. <span data-ttu-id="ef024-319">**구독**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-319">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="ef024-320">적절 한 가격 책정 계층을 선택 합니다. **함수 앱 서비스**를 처음 만드는 경우 무료 계층을 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-320">Select the pricing tier appropriate for you, if this is the first time creating a **Function App Service**, a free tier should be available to you.</span></span>

    4. <span data-ttu-id="ef024-321">리소스 그룹을 선택 하거나 새 **리소스 그룹** 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-321">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="ef024-322">리소스 그룹은 Azure 자산의 컬렉션에 대 한 청구를 모니터링 하 고, 액세스를 제어 하 고, 프로 비전 하 고, 관리 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-322">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="ef024-323">단일 프로젝트와 연결 된 모든 Azure 서비스 (예: 이러한 랩)를 공용 리소스 그룹에 유지 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-323">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="ef024-324">Azure 리소스 그룹에 대 한 자세한 내용을 보려면 [리소스 그룹을 관리 하는 방법에 대](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)한 다음 링크를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ef024-324">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="ef024-325">**OS**의 경우 원하는 플랫폼인 Windows를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-325">For **OS**, click Windows, as that is the intended platform.</span></span>

    6. <span data-ttu-id="ef024-326">**호스팅 계획** 을 선택 합니다 .이 자습서는 **소비 계획**을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-326">Select a **Hosting Plan** (this tutorial is using a **Consumption Plan**.</span></span>

    7. <span data-ttu-id="ef024-327">위치 선택 **(이전 단계에서 빌드한 저장소와 동일한 위치 선택)**</span><span class="sxs-lookup"><span data-stu-id="ef024-327">Select a **Location** **(choose the same location as the storage you have built in the previous step)**</span></span>

    8. <span data-ttu-id="ef024-328">**저장소** 섹션의 경우 **이전 단계에서 만든 저장소 서비스를 선택 해야**합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-328">For the **Storage** section, **you must select the Storage Service you created in the previous step**.</span></span>

    9. <span data-ttu-id="ef024-329">이 앱에 *Application Insights* 필요 하지 않으므로 자유롭게 그대로 **둡니다.**</span><span class="sxs-lookup"><span data-stu-id="ef024-329">You will not need *Application Insights* in this app, so feel free to leave it **Off**.</span></span>

    10. <span data-ttu-id="ef024-330">**만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-330">Click **Create**.</span></span>

        ![새 인스턴스 만들기](images/AzureLabs-Lab8-34.png)

7.  <span data-ttu-id="ef024-332">**만들기** 를 클릭 하면 서비스를 만들 때까지 기다려야 합니다 .이 경우에는 1 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-332">Once you have clicked on **Create** you will have to wait for the service to be created, this might take a minute.</span></span>

8.  <span data-ttu-id="ef024-333">서비스 인스턴스를 만든 후 알림이 포털에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-333">A notification will appear in the portal once the Service instance is created.</span></span>

    ![새 알림](images/AzureLabs-Lab8-35.png)

9.  <span data-ttu-id="ef024-335">알림을 클릭 하 여 새 서비스 인스턴스를 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-335">Click on the notifications to explore your new Service instance.</span></span>

10. <span data-ttu-id="ef024-336">알림에서 **리소스로 이동** 단추를 클릭 하 여 새 서비스 인스턴스를 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-336">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> 

    ![리소스로 이동](images/AzureLabs-Lab8-36.png)

11. <span data-ttu-id="ef024-338">함수 옆 **+** 에 있는 더하기 () 아이콘을 클릭 하 여 *새를 만듭니다*.</span><span class="sxs-lookup"><span data-stu-id="ef024-338">Click the **+** (plus) icon next to *Functions*, to *Create new*.</span></span>

    ![새 함수 추가](images/AzureLabs-Lab8-37.png)

12. <span data-ttu-id="ef024-340">중앙 패널 내에서 **함수** 만들기 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-340">Within the central panel, the **Function** creation window will appear.</span></span> <span data-ttu-id="ef024-341">패널의 위쪽 절반에 있는 정보를 무시 하 고 사용자 지정 함수를 클릭 합니다 .이 함수는 아래와 같이 파란색 영역에서 아래쪽에 있는 **사용자 지정 함수**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-341">Ignore the information in the upper half of the panel, and click **Custom function**, which is located near the bottom (in the blue area, as below).</span></span>

    ![사용자 지정 함수](images/AzureLabs-Lab8-38.png)

13. <span data-ttu-id="ef024-343">창 내의 새 페이지에 다양 한 함수 형식이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-343">The new page within the window will show various function types.</span></span> <span data-ttu-id="ef024-344">아래로 스크롤하여 자주색 형식을 확인 하 고 **HTTP PUT** 요소를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-344">Scroll down to view the purple types, and click **HTTP PUT** element.</span></span>

    ![http put 링크](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > <span data-ttu-id="ef024-346">페이지 아래로 스크롤해야 할 수도 있습니다 (Azure Portal 업데이트를 수행 하는 경우이 이미지는 정확히 동일 하지 않을 수 있음). 그러나 *HTTP PUT*이라는 요소를 찾고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-346">You may have to scroll further the down the page (and this image may not look exactly the same, if Azure Portal updates have taken place), however, you are looking for an element called *HTTP PUT*.</span></span>

14. <span data-ttu-id="ef024-347">**HTTP PUT** 창이 표시 됩니다. 여기에서 함수를 구성 해야 합니다 (이미지는 아래 참조).</span><span class="sxs-lookup"><span data-stu-id="ef024-347">The **HTTP PUT** window will appear, where you need to configure the function (see below for image).</span></span>

    1.  <span data-ttu-id="ef024-348">**언어** 의 경우 드롭다운 메뉴를 사용 하 여 C\#를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-348">For **Language,** using the dropdown menu, select C\#.</span></span>

    2.  <span data-ttu-id="ef024-349">**이름** 에 대해 적절 한 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-349">For **Name,** input an appropriate name.</span></span>

    3.  <span data-ttu-id="ef024-350">**인증 수준** 드롭다운 메뉴에서 **함수**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-350">In the **Authentication level** dropdown menu, select **Function**.</span></span>

    4.  <span data-ttu-id="ef024-351">**테이블 이름** 섹션의 경우 이전에 **테이블** 서비스를 만드는 데 사용한 정확한 이름을 사용 해야 합니다 (같은 문자를 포함).</span><span class="sxs-lookup"><span data-stu-id="ef024-351">For the **Table name** section, you need to use the exact name you used to create your **Table** service previously (including the same letter case).</span></span>

    5.  <span data-ttu-id="ef024-352">**저장소 계정 연결** 섹션에서 드롭다운 메뉴를 사용 하 고 여기에서 저장소 계정을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-352">Within the **Storage account connection** section, use the dropdown menu, and select your storage account from there.</span></span> <span data-ttu-id="ef024-353">표시 되지 않는 경우 섹션 제목과 함께 **새** 하이퍼링크를 클릭 하 여 저장소 계정이 나열 될 다른 패널을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-353">If it is not there, click the **New** hyperlink alongside the section title, to show another panel, where your storage account should be listed.</span></span>

        ![새 저장소](images/AzureLabs-Lab8-40.png)

15. <span data-ttu-id="ef024-355">**만들기** 를 클릭 하면 설정이 성공적으로 업데이트 되었다는 알림이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-355">Click **Create** and you will receive a notification that your settings have been updated successfully.</span></span>

    ![create 함수](images/AzureLabs-Lab8-41.png)

16. <span data-ttu-id="ef024-357">**만들기**를 클릭 한 후에는 함수 편집기로 리디렉션됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-357">After clicking **Create**, you will be redirected to the function editor.</span></span>

    ![함수 코드 업데이트](images/AzureLabs-Lab8-42.png)

17. <span data-ttu-id="ef024-359">함수 편집기에 다음 코드를 삽입 합니다 (함수의 코드 대체).</span><span class="sxs-lookup"><span data-stu-id="ef024-359">Insert the following code into the function editor (replacing the code in the function):</span></span>

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
    > <span data-ttu-id="ef024-360">함수는 포함 된 라이브러리를 사용 하 여 Unity 장면에서 이동 된 개체의 이름과 위치를 C# **UnityGameObject**라는 개체로 받습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-360">Using the included libraries, the function receives the name and location of the object which was moved in the Unity scene (as a C# object, called **UnityGameObject**).</span></span> <span data-ttu-id="ef024-361">그런 다음이 개체를 사용 하 여 생성 된 테이블 내에서 개체 매개 변수를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-361">This object is then used to update the object parameters within the created table.</span></span> <span data-ttu-id="ef024-362">이를 통해 함수는 생성 된 알림 허브 서비스를 호출 하 여 모든 구독 응용 프로그램에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-362">Following this, the function makes a call to your created Notification Hub service, which notifies all subscribed applications.</span></span>

18. <span data-ttu-id="ef024-363">코드가 준비 되 면 **저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-363">With the code in place, click **Save**.</span></span>

19. <span data-ttu-id="ef024-364">그런 다음 페이지의 **\<** 오른쪽에 있는 (화살표) 아이콘을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-364">Next, click the **\<** (arrow) icon, on the right-hand side of the page.</span></span>

    ![업로드 패널 열기](images/AzureLabs-Lab8-43.png)

20. <span data-ttu-id="ef024-366">패널은 오른쪽에서 오른쪽으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-366">A panel will slide in from the right.</span></span> <span data-ttu-id="ef024-367">해당 패널에서 **업로드**를 클릭 하면 파일 브라우저가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-367">In that panel, click **Upload**, and a File Browser will appear.</span></span>

21. <span data-ttu-id="ef024-368">로 이동 하 여 이전에 **메모장** 에서 만든 **프로젝트. json** 파일을 클릭 한 다음 **열기** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-368">Navigate to, and click, the **project.json** file, which you created in **Notepad** previously, and then click the **Open** button.</span></span> <span data-ttu-id="ef024-369">이 파일은 함수에서 사용할 라이브러리를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-369">This file defines the libraries that your function will use.</span></span>

    ![json 업로드](images/AzureLabs-Lab8-44.png)

22. <span data-ttu-id="ef024-371">파일이 업로드 되 면 오른쪽의 패널에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-371">When the file has uploaded, it will appear in the panel on the right.</span></span> <span data-ttu-id="ef024-372">이 단추를 클릭 하면 **함수** 편집기 내에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-372">Clicking it will open it within the **Function** editor.</span></span> <span data-ttu-id="ef024-373">다음 이미지와 **정확히** 동일 하 게 표시 되어야 합니다 (23 단계 아래).</span><span class="sxs-lookup"><span data-stu-id="ef024-373">It must look **exactly** the same as the next image (below step 23).</span></span>

23. <span data-ttu-id="ef024-374">그런 다음 왼쪽 패널의 **함수**아래에서 **통합** 링크를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-374">Then, in the panel on the left, beneath **Functions**, click the **Integrate** link.</span></span>

    ![기능 통합](images/AzureLabs-Lab8-45.png)

24. <span data-ttu-id="ef024-376">다음 페이지의 오른쪽 위 모서리에서 **고급 편집기** (아래 참조)를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-376">On the next page, in the top right corner, click **Advanced editor** (as below).</span></span>

    ![고급 편집기 열기](images/AzureLabs-Lab8-46.png)

25. <span data-ttu-id="ef024-378">다음 코드 조각으로 바꾸어야 하는 중간 패널에서 **함수 json** 파일이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-378">A **function.json** file will be opened in the center panel, which needs to be replaced with the following code snippet.</span></span> <span data-ttu-id="ef024-379">이 함수는 빌드하는 함수와 함수에 전달 되는 매개 변수를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-379">This defines the function you are building and the parameters passed into the function.</span></span>

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

26. <span data-ttu-id="ef024-380">이제 편집기는 아래 이미지와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-380">Your editor should now look like the image below:</span></span>

    ![표준 편집기로 돌아가기](images/AzureLabs-Lab8-47.png)

27. <span data-ttu-id="ef024-382">방금 삽입 한 입력 매개 변수가 테이블 및 저장소 세부 정보와 일치 하지 않을 수 있으므로 사용자 정보로 업데이트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-382">You may notice the input parameters that you have just inserted might not match your table and storage details and therefore will need to be updated with your information.</span></span> <span data-ttu-id="ef024-383">다음에 설명 된 대로 **이 작업을 수행 하지 마십시오**.</span><span class="sxs-lookup"><span data-stu-id="ef024-383">**Do not do this here**, as it is covered next.</span></span> <span data-ttu-id="ef024-384">페이지의 오른쪽 위 모퉁이에 있는 **표준 편집기** 링크를 클릭 하면 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-384">Simply click the **Standard editor** link, in the top-right corner of the page, to go back.</span></span>

28. <span data-ttu-id="ef024-385">**표준 편집기**로 돌아가서 **입력**아래의 **Azure Table Storage (테이블)** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-385">Back in the **Standard editor**, click **Azure Table Storage (table)**, under **Inputs**.</span></span> 
    
    ![테이블 입력](images/AzureLabs-Lab8-47-5.png)

29. <span data-ttu-id="ef024-387">다음과 같이 다를 수 있으므로 **사용자** 의 정보와 일치 하는지 확인 합니다 (다음 단계 아래에 이미지가 있음).</span><span class="sxs-lookup"><span data-stu-id="ef024-387">Ensure the following match to **your** information, as they may be different (there is an image below the following steps):</span></span>

    1.  <span data-ttu-id="ef024-388">**테이블 이름**: Azure Storage 테이블 서비스 내에서 만든 테이블의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-388">**Table name**: the name of the table you created within your Azure Storage, Tables service.</span></span>

    2.  <span data-ttu-id="ef024-389">**Storage 계정 연결:** 드롭다운 메뉴와 함께 표시 되는 **새로 만들기**를 클릭 하면 창 오른쪽에 패널이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-389">**Storage account connection:** click **new**, which appears alongside the dropdown menu, and a panel will appear to the right of the window.</span></span>

        ![새 저장소](images/AzureLabs-Lab8-48.png)

        1.  <span data-ttu-id="ef024-391">함수 앱을 호스트 하기 위해 이전에 만든 **저장소 계정을**선택 **합니다.**</span><span class="sxs-lookup"><span data-stu-id="ef024-391">Select your **Storage Account**, which you created previously to host the **Function Apps.**</span></span>

        2. <span data-ttu-id="ef024-392">**저장소 계정** 연결 값이 생성 된 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-392">You will notice that the **Storage Account** connection value has been created.</span></span>

        3. <span data-ttu-id="ef024-393">작업을 완료 한 후에는 **저장** 을 눌러야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-393">Make sure to press **Save** once you are done.</span></span>

    3.  <span data-ttu-id="ef024-394">**입력** 페이지는 이제 **사용자** 정보를 표시 하는 아래와 일치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-394">The **Inputs** page should now match the below, showing **your** information.</span></span>

        ![입력 완료](images/AzureLabs-Lab8-49.png)

30. <span data-ttu-id="ef024-396">그런 다음, **출력**아래에서 **Azure notification hubs (알림)** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-396">Next, click **Azure Notification Hub (notification)** - under **Outputs**.</span></span> <span data-ttu-id="ef024-397">다음 단계는 다를 수 있으므로 **사용자** 의 정보와 일치 하는지 확인 합니다 (다음 단계 아래에 이미지가 있음).</span><span class="sxs-lookup"><span data-stu-id="ef024-397">Ensure the following are matched to **your** information, as they may be different (there is an image below the following steps):</span></span>

    1.  <span data-ttu-id="ef024-398">**알림 허브 이름**: 이전에 만든 **알림 허브** 서비스 인스턴스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-398">**Notification Hub Name**: this is the name of your **Notification Hub** service instance, which you created previously.</span></span>

    2.  <span data-ttu-id="ef024-399">**네임 스페이스 연결 Notification Hubs**: 드롭다운 메뉴와 함께 표시 되는 **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-399">**Notification Hubs namespace connection**: click **new**, which appears alongside the dropdown menu.</span></span>

        ![출력 검사](images/AzureLabs-Lab8-50.png)

    3. <span data-ttu-id="ef024-401">이전에 설정한 **알림 허브**의 **네임 스페이스** 를 선택 해야 하는 **연결** 팝업이 표시 됩니다 (아래 이미지 참조).</span><span class="sxs-lookup"><span data-stu-id="ef024-401">The **Connection** popup will appear (see image below), where you need to select the **Namespace** of the **Notification Hub**, which you set up previously.</span></span>

    4. <span data-ttu-id="ef024-402">중간 드롭다운 메뉴에서 **알림 허브** 이름을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-402">Select your **Notification Hub** name from the middle dropdown menu.</span></span>

    5.  <span data-ttu-id="ef024-403">**정책** 드롭다운 메뉴를 **Defaultfullsharedaccesssignature**로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-403">Set the **Policy** dropdown menu to **DefaultFullSharedAccessSignature**.</span></span>

    6. <span data-ttu-id="ef024-404">뒤로 이동 하려면 **선택** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-404">Click the **Select** button to go back.</span></span>

        ![출력 업데이트](images/AzureLabs-Lab8-51.png)

31.  <span data-ttu-id="ef024-406">이제 **출력** 페이지가 아래와 일치 하지만 **사용자** 의 정보를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-406">The **Outputs** page should now match the below, but with **your** information instead.</span></span> <span data-ttu-id="ef024-407">**저장**을 눌러야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-407">Make sure to press **Save**.</span></span>

> [!WARNING]
> <span data-ttu-id="ef024-408">*알림 허브 이름을 직접 편집 하지 마십시오* . (이전 단계를 올바르게 수행한 경우 **고급 편집기**를 사용 하 여 모두 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-408">*Do not edit the Notification Hub name directly* (this should all be done using the **Advanced Editor**, provided you followed the previous steps correctly.</span></span>

![출력 완료](images/AzureLabs-Lab8-50.png)

32. <span data-ttu-id="ef024-410">이 시점에서 함수를 테스트 하 여 작동 하는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-410">At this point, you should test the function, to ensure it is working.</span></span> <span data-ttu-id="ef024-411">가상 하드 디스크 파일에 대한 중요 정보를 제공하려면</span><span class="sxs-lookup"><span data-stu-id="ef024-411">To do this:</span></span> 

    1. <span data-ttu-id="ef024-412">함수 페이지로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-412">Navigate to the function page once more:</span></span>

        ![출력 완료](images/AzureLabs-Lab8-50-1.png)

    2. <span data-ttu-id="ef024-414">함수 페이지로 돌아가서 페이지 맨 오른쪽의 **테스트** 탭을 클릭 하 여 *테스트* 블레이드를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-414">Back on the function page, click the **Test** tab on the far right side of the page, to open the *Test* blade:</span></span>

        ![출력 완료](images/AzureLabs-Lab8-50-2.png)

    3. <span data-ttu-id="ef024-416">블레이드의 **요청 본문** 텍스트 상자 내에 아래 코드를 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-416">Within the **Request body** textbox of the blade, paste the below code:</span></span>

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

    4. <span data-ttu-id="ef024-417">테스트 코드가 준비 되 면 오른쪽 아래에 있는 **실행** 단추를 클릭 하면 테스트가 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-417">With the test code in place, click the **Run** button at the bottom right, and the test will be run.</span></span> <span data-ttu-id="ef024-418">테스트의 출력 로그는 콘솔 영역에서 함수 코드 아래에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-418">The output logs of the test will appear in the console area, below your function code.</span></span>

        ![출력 완료](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > <span data-ttu-id="ef024-420">위의 테스트가 실패 하는 경우 위의 단계를 정확히, 특히 **통합 패널**내에서 설정 했는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-420">If the above test fails, you will need to double check that you have followed the above steps exactly, particularly the settings within the **integrate panel**.</span></span> 

## <a name="chapter-7---set-up-desktop-unity-project"></a><span data-ttu-id="ef024-421">7 장-데스크톱 Unity 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="ef024-421">Chapter 7 - Set up Desktop Unity Project</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ef024-422">지금 만들고 있는 데스크톱 응용 프로그램은 Unity 편집기에서 작동 **하지** 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-422">The Desktop application which you are now creating, **will not** work in the Unity Editor.</span></span> <span data-ttu-id="ef024-423">Visual Studio (또는 배포 된 응용 프로그램)를 사용 하 여 응용 프로그램을 빌드한 후 편집기 외부에서 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-423">It needs to be run outside of the Editor, following the Building of the application, using Visual Studio (or the deployed application).</span></span> 

<span data-ttu-id="ef024-424">다음은 Unity 및 mixed reality를 사용 하 여 개발 하기 위한 일반적인 설정으로, 다른 프로젝트에 적합 한 템플릿입니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-424">The following is a typical set up for developing with Unity and mixed reality, and as such, is a good template for other projects.</span></span>

<span data-ttu-id="ef024-425">혼합 현실 모던 헤드셋을 설정 하 고 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-425">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE] 
> <span data-ttu-id="ef024-426">이 과정에서는 동작 컨트롤러가 필요 **하지** 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-426">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="ef024-427">모던 헤드셋을 설정 하는 데 지원이 필요한 경우 [Windows Mixed Reality를 설정 하는 방법에 대 한 링크](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ef024-427">If you need support setting up the immersive headset, please follow this [link on how to set up Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="ef024-428">**Unity** 를 열고 **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-428">Open **Unity** and click **New**.</span></span>

    ![새 unity 프로젝트](images/AzureLabs-Lab8-52.png)

2.  <span data-ttu-id="ef024-430">Unity 프로젝트 이름, insert **UnityDesktopNotifHub**을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-430">You need to provide a Unity Project name, insert **UnityDesktopNotifHub**.</span></span> <span data-ttu-id="ef024-431">프로젝트 형식이 **3d**로 설정 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-431">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="ef024-432">위치를 적절 한 **위치** 에 적절 하 게 설정 합니다. 루트 디렉터리에 가까울수록 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-432">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="ef024-433">그런 다음 **프로젝트 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-433">Then, click **Create project**.</span></span>

    ![프로젝트 만들기](images/AzureLabs-Lab8-53.png)

3.  <span data-ttu-id="ef024-435">Unity를 연 상태에서 기본 **스크립트 편집기** 가 **Visual Studio**로 설정 되어 있는지 확인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-435">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="ef024-436">**기본 설정** **편집** > 으로 이동한 다음 새 창에서 **외부 도구**로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-436">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="ef024-437">**외부 스크립트 편집기** 를 **Visual Studio 2017**로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-437">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="ef024-438">**기본 설정** 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-438">Close the **Preferences** window.</span></span>

    ![외부 VS 도구 설정](images/AzureLabs-Lab8-54.png)

4.  <span data-ttu-id="ef024-440">그런 다음 **파일** > **빌드 설정** 으로 이동 하 고 **유니버설 Windows 플랫폼**를 선택한 후 **플랫폼 전환** 단추를 클릭 하 여 선택 항목을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-440">Next, go to **File** > **Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![플랫폼 전환](images/AzureLabs-Lab8-55.png)

5.  <span data-ttu-id="ef024-442">**파일** > **빌드 설정**에서 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-442">While still in **File** > **Build Settings**, make sure that:</span></span>

    1.  <span data-ttu-id="ef024-443">**대상 장치가** **모든 장치로** 설정 됨</span><span class="sxs-lookup"><span data-stu-id="ef024-443">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="ef024-444">이 응용 프로그램은 데스크톱을 위한 것 이므로 **모든 장치** 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-444">This Application will be for your desktop, so must be **Any Device**</span></span>

    2.  <span data-ttu-id="ef024-445">**빌드 형식이** **D3D** 로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-445">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="ef024-446">**SDK** 가 **최신 설치** 로 설정 됨</span><span class="sxs-lookup"><span data-stu-id="ef024-446">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="ef024-447">**Visual Studio 버전이** **최신 설치** 로 설정 됨</span><span class="sxs-lookup"><span data-stu-id="ef024-447">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="ef024-448">**빌드 및 실행** 이 **로컬 컴퓨터로** 설정 됨</span><span class="sxs-lookup"><span data-stu-id="ef024-448">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="ef024-449">여기서는 장면을 저장 하 고 빌드에 추가 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-449">While here, it is worth saving the scene, and adding it to the build.</span></span>

        1. <span data-ttu-id="ef024-450">이렇게 하려면 열려 있는 **장면 추가**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-450">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="ef024-451">저장 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-451">A save window will appear.</span></span>

            ![열려 있는 장면 추가](images/AzureLabs-Lab8-56.png)

        2. <span data-ttu-id="ef024-453">이에 대 한 새 폴더를 만들고 나중에 장면을 만든 다음 **새 폴더** 단추를 선택 하 여 새 폴더를 만들고 이름을 **장면을**로 지정한 다음</span><span class="sxs-lookup"><span data-stu-id="ef024-453">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![새 장면 폴더](images/AzureLabs-Lab8-57.png)

        3. <span data-ttu-id="ef024-455">새로 만든 **장면** 폴더를 연 다음 **파일 이름:** 텍스트 필드에 **\_nh Desktop\_장면을**입력 하 고 **저장**을 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-455">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **NH\_Desktop\_Scene**, then press **Save**.</span></span>

            ![새 NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  <span data-ttu-id="ef024-457">**빌드 설정**의 나머지 설정은 지금은 기본값으로 남겨 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-457">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6.  <span data-ttu-id="ef024-458">동일한 창에서 **플레이어 설정** 단추를 클릭 하면 **검사기** 가 있는 공간에서 관련 패널이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-458">In the same window click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

7.  <span data-ttu-id="ef024-459">이 패널에서 몇 가지 설정을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-459">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="ef024-460">**기타 설정** 탭에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-460">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="ef024-461">**스크립팅 런타임 버전이** 실험적 이어야 함 **(.net 4.6 해당)**</span><span class="sxs-lookup"><span data-stu-id="ef024-461">**Scripting Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**</span></span>

        2. <span data-ttu-id="ef024-462">**Scripting 백엔드** 는 **.net** 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-462">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="ef024-463">**API 호환성 수준은** **.net 4.6** 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-463">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![4.6 네트워크 버전](images/AzureLabs-Lab8-59.png)

    2.  <span data-ttu-id="ef024-465">**게시 설정** 탭의 **기능**아래에서 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-465">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="ef024-466">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="ef024-466">**InternetClient**</span></span>

            ![tick 인터넷 클라이언트](images/AzureLabs-Lab8-60.png)

8.  <span data-ttu-id="ef024-468">**빌드 설정** 으로 돌아가기 *Unity C\# 프로젝트가* 더 이상 회색으로 표시 되지 않습니다 .이 옆의 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-468">Back in **Build Settings** *Unity C\# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="ef024-469">**빌드 설정** 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-469">Close the **Build Settings** window.</span></span>

10. <span data-ttu-id="ef024-470">장면 및 프로젝트 **파일** > 저장**장면/파일** > **저장 프로젝트**를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-470">Save your Scene and Project **File** > **Save Scene / File** > **Save Project**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="ef024-471">이 프로젝트에 대 한 *Unity 설정* 구성 요소 (데스크톱 앱)를 건너뛰고 코드를 바로 계속 하려면 unitypackage를 다운로드 하 여 프로젝트에 [**사용자 지정 패키지로**](https://docs.unity3d.com/Manual/AssetPackages.html)가져온 후 챕터에서 계속 [합니다.](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage) [ 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span><span class="sxs-lookup"><span data-stu-id="ef024-471">If you wish to skip the *Unity Set up* component for this project (Desktop App), and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span>  <span data-ttu-id="ef024-472">스크립트 구성 요소를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-472">You will still need to add the script components.</span></span>

## <a name="chapter-8---importing-the-dlls-in-unity"></a><span data-ttu-id="ef024-473">8 장-Unity에서 Dll 가져오기</span><span class="sxs-lookup"><span data-stu-id="ef024-473">Chapter 8 - Importing the DLLs in Unity</span></span>

<span data-ttu-id="ef024-474">Unity에 Azure Storage를 사용 하 게 됩니다 (자체는 Azure 용 .Net SDK를 활용).</span><span class="sxs-lookup"><span data-stu-id="ef024-474">You will be using Azure Storage for Unity (which itself leverages the .Net SDK for Azure).</span></span> <span data-ttu-id="ef024-475">자세한 내용은 [Unity Azure Storage에 대](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)한이 링크를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ef024-475">For more information follow this [link about Azure Storage for Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>

<span data-ttu-id="ef024-476">현재 Unity에는 가져온 후 플러그 인을 다시 구성 해야 하는 알려진 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-476">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="ef024-477">이러한 단계 (이 섹션에서는 4-7)는 버그가 해결 된 후 더 이상 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-477">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="ef024-478">SDK를 고유한 프로젝트로 가져오려면 GitHub에서 최신 [**unitypackage**](https://aka.ms/azstorage-unitysdk) 를 다운로드 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-478">To import the SDK into your own project, make sure you have downloaded the latest [**.unitypackage**](https://aka.ms/azstorage-unitysdk) from GitHub.</span></span> <span data-ttu-id="ef024-479">그런 후에 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-479">Then, do the following:</span></span>

1.  <span data-ttu-id="ef024-480">**자산 가져오기\> 패키지\> 사용자 지정 패키지** 메뉴 옵션을 사용 하 여 unitypackage을 Unity에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-480">Add the **.unitypackage** to Unity by using the **Assets \> Import Package \> Custom Package** menu option.</span></span>

2.  <span data-ttu-id="ef024-481">팝업 되는 **Unity 패키지 가져오기** 상자에서 \* \**플러그 인* \> \* 저장소 \* \* \* 아래의 모든 항목을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-481">In the **Import Unity Package** box that pops up, you can select everything under \*\**Plugin* \> \*Storage\*\*\*.</span></span>  <span data-ttu-id="ef024-482">이 과정에서 필요 하지 않으므로 다른 모든 항목을 선택 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-482">Uncheck everything else, as it is not needed for this course.</span></span>

    ![패키지로 가져오기](images/AzureLabs-Lab8-61.png)

3.  <span data-ttu-id="ef024-484">***가져오기*** 단추를 클릭 하 여 프로젝트에 항목을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-484">Click the ***Import*** button to add the items to your project.</span></span>

4.  <span data-ttu-id="ef024-485">프로젝트 뷰에서 **플러그 인** 의 **저장소** 폴더로 이동 하 고 다음 플러그 인 *만*선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-485">Go to the **Storage** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="ef024-486">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="ef024-486">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="ef024-487">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="ef024-487">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="ef024-488">Windowsazure.servicebus</span><span class="sxs-lookup"><span data-stu-id="ef024-488">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="ef024-489">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="ef024-489">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="ef024-490">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="ef024-490">System.Spatial</span></span>

![모든 플랫폼 선택 취소](images/AzureLabs-Lab8-62.png)

5.  <span data-ttu-id="ef024-492">*이러한 특정 플러그* 인을 선택 하 고 **플랫폼** 을 선택 **취소** 하 고 **WSAPlayer** **선택을 취소** 한 후 **적용**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-492">With *these specific plugins* selected, **uncheck** **Any Platform** and **uncheck** **WSAPlayer** then click **Apply**.</span></span>

    ![플랫폼 dll 적용](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > <span data-ttu-id="ef024-494">이러한 특정 플러그인을 Unity 편집기 에서만 사용 하도록 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-494">We are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="ef024-495">이는 프로젝트를 Unity에서 내보낸 후에 사용 되는 WSA 폴더에 동일한 플러그 인의 버전이 서로 다르기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-495">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="ef024-496">**저장소** 플러그 인 폴더에서 다음만을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-496">In the **Storage** plugin folder, select only:</span></span>

    -   <span data-ttu-id="ef024-497">Microsoft. Data. Service. 클라이언트</span><span class="sxs-lookup"><span data-stu-id="ef024-497">Microsoft.Data.Services.Client</span></span>

        ![dll에 대해 처리 안 함 설정](images/AzureLabs-Lab8-64.png)

7.  <span data-ttu-id="ef024-499">**플랫폼 설정** 에서 **처리 안 함** 상자를 선택 하 고 ***적용***을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-499">Check the **Don't Process** box under **Platform Settings** and click ***Apply***.</span></span>

    ![처리 안 함 적용](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > <span data-ttu-id="ef024-501">Unity 어셈블리 patcher이 플러그 인을 처리 하는 데 어려움을 겪고 있으므로이 플러그 인을 "처리 안 함"으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-501">We are marking this plugin "Don't process", because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="ef024-502">플러그 인은 처리 되지 않은 경우에도 계속 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-502">The plugin will still work even though it is not processed.</span></span>

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a><span data-ttu-id="ef024-503">9 장-데스크톱 Unity 프로젝트에서 TableToScene 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="ef024-503">Chapter 9 - Create the TableToScene class in the Desktop Unity project</span></span>

<span data-ttu-id="ef024-504">이제이 응용 프로그램을 실행 하는 코드가 포함 된 스크립트를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-504">You now need to create the scripts containing the code to run this application.</span></span>

<span data-ttu-id="ef024-505">만들어야 하는 첫 번째 스크립트는 다음을 담당 하는 **TableToScene**입니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-505">The first script you need to create is **TableToScene**, which is responsible for:</span></span>

-   <span data-ttu-id="ef024-506">Azure 테이블 내에서 엔터티를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-506">Reading entities within the Azure Table.</span></span>
-   <span data-ttu-id="ef024-507">테이블 데이터를 사용 하 여 생성할 개체와 위치를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-507">Using the Table data, determine which objects to spawn, and in which position.</span></span>

<span data-ttu-id="ef024-508">만들어야 하는 두 번째 스크립트는 다음을 담당 하는 **Cloudscene**됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-508">The second script you need to create is **CloudScene**, which is responsible for:</span></span>

-   <span data-ttu-id="ef024-509">왼쪽 클릭 이벤트를 등록 하 여 사용자가 장면 주위로 개체를 끌어올 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-509">Registering the left-click event, to allow the user to drag objects around the scene.</span></span>
-   <span data-ttu-id="ef024-510">이 Unity 장면에서 개체 데이터를 직렬화 하 고 Azure 함수 앱로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-510">Serializing the object data from this Unity scene, and sending it to the Azure Function App.</span></span>

<span data-ttu-id="ef024-511">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="ef024-511">To create this class:</span></span>

1.  <span data-ttu-id="ef024-512">프로젝트 패널에 있는 **자산** 폴더를 마우스 오른쪽 단추로 클릭 하 고**폴더**를 **만듭니다** > .</span><span class="sxs-lookup"><span data-stu-id="ef024-512">Right-click in the **Asset** Folder located in the Project Panel, **Create** > **Folder**.</span></span> <span data-ttu-id="ef024-513">폴더 이름을 **스크립트**로 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-513">Name the folder **Scripts**.</span></span>

    ![스크립트 폴더 만들기](images/AzureLabs-Lab8-66.png)

    ![스크립트 폴더 만들기 2](images/AzureLabs-Lab8-67.png)

2.  <span data-ttu-id="ef024-516">위에서 만든 폴더를 두 번 클릭 하 여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-516">Double click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="ef024-517">마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **Create** >  **C# 스크립트**.</span><span class="sxs-lookup"><span data-stu-id="ef024-517">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="ef024-518">스크립트 이름을 **TableToScene**로 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-518">Name the script **TableToScene**.</span></span>

    <span data-ttu-id="ef024-519">![새 c #](images/AzureLabs-Lab8-68.png)
    스크립트![TableToScene 이름 바꾸기](images/AzureLabs-Lab8-69.png)</span><span class="sxs-lookup"><span data-stu-id="ef024-519">![new c# script](images/AzureLabs-Lab8-68.png)
![TableToScene rename](images/AzureLabs-Lab8-69.png)</span></span>

4.  <span data-ttu-id="ef024-520">스크립트를 두 번 클릭 하 여 Visual Studio 2017에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-520">Double-click on the script to open it in Visual Studio 2017.</span></span>

5.  <span data-ttu-id="ef024-521">다음 네임 스페이스를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-521">Add the following namespaces:</span></span>

    ```csharp
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Auth;
    using Microsoft.WindowsAzure.Storage.Table;
    using UnityEngine;
    ```

6.  <span data-ttu-id="ef024-522">클래스 내에서 다음 변수를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-522">Within the class, insert the following variables:</span></span>

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
    > <span data-ttu-id="ef024-523">**AccountName** 값을 Azure Storage 서비스 이름 및 **accountKey** 값으로 대체 하 고 Azure Portal에서 Azure Storage 서비스의 키 값으로 대체 합니다 (아래 이미지 참조).</span><span class="sxs-lookup"><span data-stu-id="ef024-523">Substitute the **accountName** value with your Azure Storage Service name and **accountKey** value with the key value found in the Azure Storage Service, in the Azure Portal (See Image below).</span></span> 
    >
    > ![계정 키 페치](images/AzureLabs-Lab8-70.png)

7.  <span data-ttu-id="ef024-525">이제 **Start ()** 및 **활성 ()** 메서드를 추가 하 여 클래스를 초기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-525">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

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

8.  <span data-ttu-id="ef024-526">**TableToScene** 클래스 내에서 Azure 테이블의 값을 검색 하는 메서드를 추가 하 고이를 사용 하 여 장면에서 적절 한 기본 형식을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-526">Within the **TableToScene** class, add the method that will retrieve the values from the Azure Table and use them to spawn the appropriate primitives in the scene.</span></span>

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

9.  <span data-ttu-id="ef024-527">**TableToScene** 클래스 외부에서는 응용 프로그램에서 **테이블 엔터티**를 serialize 및 deserialize 하는 데 사용 하는 클래스를 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-527">Outside the **TableToScene** class, you need to define the class used by the application to serialize and deserialize the **Table Entities**.</span></span>

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

10. <span data-ttu-id="ef024-528">Unity 편집기로 다시 이동 하기 전에를 **저장** 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-528">Make sure you **Save** before going back to the Unity Editor.</span></span>

11. <span data-ttu-id="ef024-529">**계층** 패널에서 **주 카메라** 를 클릭 하 여 해당 속성이 **검사기**에 표시 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-529">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span>

12. <span data-ttu-id="ef024-530">**Scripts** 폴더가 열리면 스크립트 **TableToScene 파일** 을 선택 하 여 **기본 카메라로**끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-530">With the **Scripts** folder open, select the script **TableToScene file** and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="ef024-531">결과는 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-531">The result should be as below:</span></span>

    ![주 카메라에 스크립트 추가](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a><span data-ttu-id="ef024-533">10 장-데스크톱 Unity 프로젝트에서 CloudScene 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="ef024-533">Chapter 10 - Create the CloudScene class in the Desktop Unity Project</span></span>

<span data-ttu-id="ef024-534">만들어야 하는 두 번째 스크립트는 다음을 담당 하는 **Cloudscene**됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-534">The second script you need to create is **CloudScene**, which is responsible for:</span></span>

-   <span data-ttu-id="ef024-535">왼쪽 클릭 이벤트를 등록 하 여 사용자가 장면 주위로 개체를 끌어올 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-535">Registering the left-click event, to allow the user to drag objects around the scene.</span></span>

-   <span data-ttu-id="ef024-536">이 Unity 장면에서 개체 데이터를 직렬화 하 고 Azure 함수 앱로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-536">Serializing the object data from this Unity scene, and sending it to the Azure Function App.</span></span>

<span data-ttu-id="ef024-537">두 번째 스크립트를 만들려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-537">To create the second script:</span></span>

1.  <span data-ttu-id="ef024-538">**Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 하 고 **만들기**, **C\# 스크립트**를 차례로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-538">Right-click inside the **Scripts** folder, click **Create**, **C\# Script**.</span></span> <span data-ttu-id="ef024-539">스크립트 **Cloudscene** 이름</span><span class="sxs-lookup"><span data-stu-id="ef024-539">Name the script **CloudScene**</span></span>
    
    <span data-ttu-id="ef024-540">![새 c #](images/AzureLabs-Lab8-72.png)
    스크립트![cloudscene 이름 바꾸기](images/AzureLabs-Lab8-73.png)</span><span class="sxs-lookup"><span data-stu-id="ef024-540">![new c# script](images/AzureLabs-Lab8-72.png)
![rename CloudScene](images/AzureLabs-Lab8-73.png)</span></span>

2.  <span data-ttu-id="ef024-541">다음 네임 스페이스를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-541">Add the following namespaces:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using System.Threading.Tasks;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

3.  <span data-ttu-id="ef024-542">다음 변수를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-542">Insert the following variables:</span></span>

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

4.  <span data-ttu-id="ef024-543">아래 이미지에 나와 있는 것 처럼 azure Portal에서 azure 함수 앱 서비스의 azure 함수 앱 URL을 사용 하 여 **azureFunctionEndpoint** 값을 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-543">Substitute the **azureFunctionEndpoint** value with your Azure Function App URL found in the Azure Function App Service, in the Azure Portal, as shown in the image below:</span></span>

    ![함수 URL 가져오기](images/AzureLabs-Lab8-74.png)

5.  <span data-ttu-id="ef024-545">이제 **Start ()** 및 **활성 ()** 메서드를 추가 하 여 클래스를 초기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-545">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

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

6.  <span data-ttu-id="ef024-546">**Update ()** 메서드 내에서 마우스 입력을 감지 하 고 끌 수 있는 다음 코드를 추가 합니다. 이렇게 하면 장면의 gameobject 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-546">Within the **Update()** method, add the following code that will detect the mouse input and drag, which will in turn move GameObjects in the scene.</span></span> <span data-ttu-id="ef024-547">사용자가 개체를 끌어서 놓으면 개체의 이름과 좌표가 **UpdateCloudScene ()** 메서드에 전달 됩니다 .이 서비스는 azure 테이블을 업데이트 하 고 알림을 트리거하는 azure 함수 앱 서비스를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-547">If the user has dragged and dropped an object, it will pass the name and coordinates of the object to the method **UpdateCloudScene()**, which will call the Azure Function App service, which will update the Azure table and trigger the notification.</span></span>

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

7.  <span data-ttu-id="ef024-548">이제 다음과 같이 **UpdateCloudScene ()** 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-548">Now add the **UpdateCloudScene()** method, as below:</span></span>

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

8.  <span data-ttu-id="ef024-549">코드를 저장 하 고 Unity로 돌아가기</span><span class="sxs-lookup"><span data-stu-id="ef024-549">Save the code and return to Unity</span></span>

9.  <span data-ttu-id="ef024-550">**Cloudscene** 스크립트를 **기본 카메라로**끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-550">Drag the **CloudScene** script onto the **Main Camera**.</span></span> 

    1. <span data-ttu-id="ef024-551">**계층** 패널에서 **주 카메라** 를 클릭 하 여 해당 속성이 **검사기**에 표시 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-551">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span> 

    2. <span data-ttu-id="ef024-552">**Scripts** 폴더가 열리면 **cloudscene** 스크립트를 선택 하 고 **기본 카메라로**끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-552">With the **Scripts** folder open, select the **CloudScene** script and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="ef024-553">결과는 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-553">The result should be as below:</span></span>

        > ![클라우드 스크립트를 기본 카메라로 끌어 옵니다.](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a><span data-ttu-id="ef024-555">11 장-UWP에 데스크톱 프로젝트 빌드</span><span class="sxs-lookup"><span data-stu-id="ef024-555">Chapter 11 - Build the Desktop Project to UWP</span></span>

<span data-ttu-id="ef024-556">이제이 프로젝트의 Unity 섹션에 필요한 모든 항목이 완료 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-556">Everything needed for the Unity section of this project has now been completed.</span></span>

1.  <span data-ttu-id="ef024-557">**빌드 설정** (**파일** > **빌드 설정**)으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-557">Navigate to **Build Settings** (**File** > **Build Settings**).</span></span>

2.  <span data-ttu-id="ef024-558">**빌드 설정** 창에서 **빌드**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-558">From the **Build Settings** window, click **Build**.</span></span>

    ![프로젝트 빌드](images/AzureLabs-Lab8-76.png)

3.  <span data-ttu-id="ef024-560">빌드할 위치를 묻는 메시지를 표시 하는 **파일 탐색기** 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-560">A **File Explorer** window will popup, prompting you for a location to Build.</span></span> <span data-ttu-id="ef024-561">왼쪽 위 모서리에서 **새 폴더** 를 클릭 하 여 새 폴더를 만들고 이름을 **작성**합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-561">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![빌드용 새 폴더](images/AzureLabs-Lab8-77.png)

    1.  <span data-ttu-id="ef024-563">새 **빌드** 폴더를 열고 **새** 폴더를 한 번 더 사용 하 여 다른 폴더를 만든 다음 이름으로 **nh\_데스크톱\_앱**을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-563">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **NH\_Desktop\_App**.</span></span>

        ![폴더 이름 NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  <span data-ttu-id="ef024-565">**Nh\_데스크톱\_앱** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-565">With the **NH\_Desktop\_App** selected.</span></span> <span data-ttu-id="ef024-566">**폴더 선택**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-566">click **Select Folder**.</span></span> <span data-ttu-id="ef024-567">프로젝트를 빌드하는 데 1 분 정도 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-567">The project will take a minute or so to build.</span></span>

4.  <span data-ttu-id="ef024-568">빌드 다음에는 새 프로젝트의 위치를 보여 주는 **파일 탐색기** 가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-568">Following build, **File Explorer** will appear showing you the location of your new project.</span></span> <span data-ttu-id="ef024-569">그러나 다음 몇 장에서는 먼저 다른 Unity 프로젝트를 만들어야 하므로 열 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-569">No need to open it, though, as you need to create the other Unity project first, in the next few Chapters.</span></span>


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a><span data-ttu-id="ef024-570">12 장-혼합 현실 Unity 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="ef024-570">Chapter 12 - Set up Mixed Reality Unity Project</span></span>

<span data-ttu-id="ef024-571">다음은 혼합 현실를 사용 하 여 개발 하기 위한 일반적인 설정으로, 다른 프로젝트에 적합 한 템플릿입니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-571">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="ef024-572">**Unity** 를 열고 **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-572">Open **Unity** and click **New**.</span></span>

    ![새 unity 프로젝트](images/AzureLabs-Lab8-79.png)

2.  <span data-ttu-id="ef024-574">이제 Unity 프로젝트 이름, insert **UnityMRNotifHub**을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-574">You will now need to provide a Unity Project name, insert **UnityMRNotifHub**.</span></span> <span data-ttu-id="ef024-575">프로젝트 형식이 **3d**로 설정 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-575">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="ef024-576">위치를 적절 한 **위치** 에 적절 하 게 설정 합니다. 루트 디렉터리에 가까울수록 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-576">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="ef024-577">그런 다음 **프로젝트 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-577">Then, click **Create project**.</span></span>

    ![이름 UnityMRNotifHub](images/AzureLabs-Lab8-80.png)

3.  <span data-ttu-id="ef024-579">Unity를 연 상태에서 기본 **스크립트 편집기** 가 **Visual Studio**로 설정 되어 있는지 확인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-579">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="ef024-580">**기본 설정** **편집** > 으로 이동한 다음 새 창에서 **외부 도구**로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-580">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="ef024-581">**외부 스크립트 편집기** 를 **Visual Studio 2017**로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-581">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="ef024-582">**기본 설정** 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-582">Close the **Preferences** window.</span></span>

    ![외부 편집기를 VS로 설정](images/AzureLabs-Lab8-81.png)

4.  <span data-ttu-id="ef024-584">그런 다음 **파일** > **빌드 설정** 으로 이동 하 고 플랫폼 **전환** 단추를 클릭 하 여 플랫폼을 **유니버설 Windows 플랫폼**로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-584">Next, go to **File** > **Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![플랫폼을 UWP로 전환](images/AzureLabs-Lab8-82.png)

5.  <span data-ttu-id="ef024-586">**파일** > **빌드 설정** 으로 이동 하 여 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-586">Go to **File** > **Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="ef024-587">**대상 장치가** **모든 장치로** 설정 됨</span><span class="sxs-lookup"><span data-stu-id="ef024-587">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="ef024-588">Microsoft HoloLens의 경우 **대상 장치** 를 *HoloLens*로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-588">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="ef024-589">**빌드 형식이** **D3D** 로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-589">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="ef024-590">**SDK** 가 **최신 설치** 로 설정 됨</span><span class="sxs-lookup"><span data-stu-id="ef024-590">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="ef024-591">**Visual Studio 버전이** **최신 설치** 로 설정 됨</span><span class="sxs-lookup"><span data-stu-id="ef024-591">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="ef024-592">**빌드 및 실행** 이 **로컬 컴퓨터로** 설정 됨</span><span class="sxs-lookup"><span data-stu-id="ef024-592">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="ef024-593">여기서는 장면을 저장 하 고 빌드에 추가 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-593">While here, it is worth saving the scene, and adding it to the build.</span></span>

        1. <span data-ttu-id="ef024-594">이렇게 하려면 열려 있는 **장면 추가**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-594">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="ef024-595">저장 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-595">A save window will appear.</span></span>

            ![열려 있는 장면 추가](images/AzureLabs-Lab8-83.png)

        2. <span data-ttu-id="ef024-597">이에 대 한 새 폴더를 만들고 나중에 장면을 만든 다음 **새 폴더** 단추를 선택 하 여 새 폴더를 만들고 이름을 **장면을**로 지정한 다음</span><span class="sxs-lookup"><span data-stu-id="ef024-597">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![새 장면 폴더](images/AzureLabs-Lab8-84.png)

        3. <span data-ttu-id="ef024-599">새로 만든 **장면** 폴더를 연 다음 **파일 이름:** 텍스트 필드에 **\_nh MR\_장면**을 입력 하 고 **저장**을 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-599">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **NH\_MR\_Scene**, then press **Save**.</span></span>

            ![새 장면-NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  <span data-ttu-id="ef024-601">**빌드 설정**의 나머지 설정은 지금은 기본값으로 남겨 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-601">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6.  <span data-ttu-id="ef024-602">동일한 창에서 **플레이어 설정** 단추를 클릭 하면 **검사기** 가 있는 공간에서 관련 패널이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-602">In the same window click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>    

    ![플레이어 설정 열기](images/AzureLabs-Lab8-86.png)

7.  <span data-ttu-id="ef024-604">이 패널에서 몇 가지 설정을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-604">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="ef024-605">**기타 설정** 탭에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-605">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="ef024-606">**스크립팅 런타임 버전이** **실험적** 이어야 함 (.net 4.6 해당)</span><span class="sxs-lookup"><span data-stu-id="ef024-606">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent)</span></span>
        2.  <span data-ttu-id="ef024-607">**Scripting 백엔드** 는 ***.net*** 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-607">**Scripting Backend** should be ***.NET***</span></span>
        3.  <span data-ttu-id="ef024-608">**API 호환성 수준은** **.net 4.6** 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-608">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![api 호환성](images/AzureLabs-Lab8-87.png)

    2.  <span data-ttu-id="ef024-610">패널의 아래쪽에서 **XR 설정** ( **게시 설정**아래에 있음), **지원 되는 틱 가상 현실**, **Windows Mixed reality SDK** 가 추가 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-610">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added</span></span>

        ![xr 설정 업데이트](images/AzureLabs-Lab8-88.png)        

    3.  <span data-ttu-id="ef024-612">**게시 설정** 탭의 **기능**아래에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-612">Within the **Publishing Settings** tab, under **Capabilities**, heck:</span></span>

        - <span data-ttu-id="ef024-613">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="ef024-613">**InternetClient**</span></span>           

            ![tick 인터넷 클라이언트](images/AzureLabs-Lab8-89.png)

8.  <span data-ttu-id="ef024-615">**빌드 설정**으로 돌아가서 **Unity C# 프로젝트가** 더 이상 회색으로 표시 되지 않습니다 .이 옆의 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-615">Back in **Build Settings**, **Unity C# Projects** is no longer greyed out: tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="ef024-616">이러한 변경 작업을 수행한 후 빌드 설정 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-616">With these changes done, close the Build Settings window.</span></span>

10. <span data-ttu-id="ef024-617">장면 및 프로젝트 **파일** > 저장**장면/파일** > **저장 프로젝트**를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-617">Save your Scene and Project **File** > **Save Scene / File** > **Save Project**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="ef024-618">이 프로젝트에 대 한 *Unity 설정* 구성 요소 (혼합 현실 앱)를 건너뛰고 바로 코드를 계속 사용 하려면 [unitypackage를 다운로드](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage)하 고 프로젝트에 [**사용자 지정 패키지로**](https://docs.unity3d.com/Manual/AssetPackages.html)가져온 후 [ 14 장](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project).</span><span class="sxs-lookup"><span data-stu-id="ef024-618">If you wish to skip the *Unity Set up* component for this project (mixed reality App), and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project).</span></span> <span data-ttu-id="ef024-619">스크립트 구성 요소를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-619">You will still need to add the script components.</span></span>

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a><span data-ttu-id="ef024-620">13 장-Mixed Reality Unity 프로젝트에서 Dll 가져오기</span><span class="sxs-lookup"><span data-stu-id="ef024-620">Chapter 13 - Importing the DLLs in the Mixed Reality Unity Project</span></span>

<span data-ttu-id="ef024-621">Unity 라이브러리 (Azure 용 .Net SDK 사용)에 대 한 Azure Storage를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-621">You will be using Azure Storage for Unity library (which uses the .Net SDK for Azure).</span></span> <span data-ttu-id="ef024-622">Unity를 사용 하 여 [Azure Storage를 사용 하는 방법에 대 한 링크를](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ef024-622">Please follow this [link on how to use Azure Storage with Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>
<span data-ttu-id="ef024-623">현재 Unity에는 가져온 후 플러그 인을 다시 구성 해야 하는 알려진 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-623">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="ef024-624">이러한 단계 (이 섹션에서는 4-7)는 버그가 해결 된 후 더 이상 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-624">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="ef024-625">SDK를 고유한 프로젝트로 가져오려면 최신 [unitypackage](https://aka.ms/azstorage-unitysdk)를 다운로드 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-625">To import the SDK into your own project, make sure you have downloaded the latest [.unitypackage](https://aka.ms/azstorage-unitysdk).</span></span> <span data-ttu-id="ef024-626">그런 후에 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-626">Then, do the following:</span></span>

1.  <span data-ttu-id="ef024-627">**자산** > **가져오기**패키지사용자 > **지정 패키지** 메뉴 옵션을 사용 하 여 위에서 다운로드 한 unitypackage을 Unity에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-627">Add the .unitypackage you downloaded from the above, to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

2.  <span data-ttu-id="ef024-628">표시 되는 **Unity 패키지 가져오기** 상자에서 **플러그 인** > **저장소**아래의 모든 항목을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-628">In the **Import Unity Package** box that pops up, you can select everything under **Plugin** > **Storage**.</span></span>

    ![패키지 가져오기](images/AzureLabs-Lab8-90.png)

3.  <span data-ttu-id="ef024-630">**가져오기** 단추를 클릭 하 여 프로젝트에 항목을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-630">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="ef024-631">프로젝트 뷰에서 **플러그 인** 의 **저장소** 폴더로 이동 하 고 다음 플러그 인 *만*선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-631">Go to the **Storage** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="ef024-632">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="ef024-632">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="ef024-633">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="ef024-633">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="ef024-634">Windowsazure.servicebus</span><span class="sxs-lookup"><span data-stu-id="ef024-634">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="ef024-635">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="ef024-635">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="ef024-636">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="ef024-636">System.Spatial</span></span>

    ![플러그 인 선택](images/AzureLabs-Lab8-91.png)

5.  <span data-ttu-id="ef024-638">*이러한 특정 플러그* 인을 선택 하 고 **플랫폼** 을 선택 **취소** 하 고 **WSAPlayer** **선택을 취소** 한 후 **적용**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-638">With *these specific plugins* selected, **uncheck** **Any Platform** and **uncheck** **WSAPlayer** then click **Apply**.</span></span>

    ![플랫폼 변경 내용 적용](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > <span data-ttu-id="ef024-640">이러한 특정 플러그인을 Unity 편집기 에서만 사용 하도록 표시 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-640">You are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="ef024-641">이는 프로젝트를 Unity에서 내보낸 후에 사용 되는 WSA 폴더에 동일한 플러그 인의 버전이 서로 다르기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-641">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="ef024-642">**저장소** 플러그 인 폴더에서 다음만을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-642">In the **Storage** plugin folder, select only:</span></span>

    -   <span data-ttu-id="ef024-643">Microsoft. Data. Service. 클라이언트</span><span class="sxs-lookup"><span data-stu-id="ef024-643">Microsoft.Data.Services.Client</span></span>

        ![data services 클라이언트 선택](images/AzureLabs-Lab8-93.png)

7.  <span data-ttu-id="ef024-645">**플랫폼 설정** 에서 **처리 안 함** 상자를 선택 하 고 **적용**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-645">Check the **Don't Process** box under **Platform Settings** and click **Apply**.</span></span>

    ![처리 안 함](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > <span data-ttu-id="ef024-647">Unity 어셈블리 patcher이 플러그 인을 처리 하는 데 어려움이 있으므로이 플러그 인을 "처리 안 함"으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-647">You are marking this plugin "Don't process" because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="ef024-648">플러그 인은 처리 되지 않은 경우에도 계속 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-648">The plugin will still work even though it isn't processed.</span></span>

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a><span data-ttu-id="ef024-649">14 장-mixed reality Unity 프로젝트에서 TableToScene 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="ef024-649">Chapter 14 - Creating the TableToScene class in the mixed reality Unity project</span></span>

<span data-ttu-id="ef024-650">**TableToScene** 클래스는 [9 장](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)에서 설명한 것과 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-650">The **TableToScene** class is identical to the one explained in [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span> <span data-ttu-id="ef024-651">[9 장](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)에서 설명한 것과 동일한 절차에 따라 혼합 현실 Unity 프로젝트에서 동일한 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-651">Create the same class in the mixed reality Unity Project following the same procedure explained in [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span>

<span data-ttu-id="ef024-652">이 챕터를 완료 한 후에는 두 **Unity 프로젝트** 에서이 클래스를 기본 카메라에 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-652">Once you have completed this Chapter, both of your **Unity Projects** will have this class set up on the Main Camera.</span></span>

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a><span data-ttu-id="ef024-653">15 장-Mixed Reality Unity 프로젝트에서 NotificationReceiver 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="ef024-653">Chapter 15 - Creating the NotificationReceiver class in the Mixed Reality Unity Project</span></span>

<span data-ttu-id="ef024-654">생성 해야 하는 두 번째 스크립트는 다음과 같은 작업을 담당 하는 **Notificationreceiver**입니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-654">The second script you need to create is **NotificationReceiver**, which is responsible for:</span></span>

-   <span data-ttu-id="ef024-655">초기화할 때 알림 허브에 앱을 등록 하는 중입니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-655">Registering the app with the Notification Hub at initialization.</span></span>
-   <span data-ttu-id="ef024-656">알림 허브에서 들어오는 알림을 수신 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-656">Listening to notifications coming from the Notification Hub.</span></span>
-   <span data-ttu-id="ef024-657">수신 된 알림에서 개체 데이터를 deserialize 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-657">Deserializing the object data from received notifications.</span></span>
-   <span data-ttu-id="ef024-658">Deserialize 된 데이터를 기반으로 장면에서 Gameobject를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-658">Move the GameObjects in the scene, based on the deserialized data.</span></span>

<span data-ttu-id="ef024-659">**Notificationreceiver** 스크립트를 만들려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-659">To create the **NotificationReceiver** script:</span></span>

1.  <span data-ttu-id="ef024-660">**Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 하 고 **만들기**, **C\# 스크립트**를 차례로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-660">Right-click inside the **Scripts** folder, click **Create**, **C\# Script**.</span></span> <span data-ttu-id="ef024-661">스크립트의 이름을 **Notificationreceiver**로 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-661">Name the script **NotificationReceiver**.</span></span>

    <span data-ttu-id="ef024-662">![새 c # 스크립트](images/AzureLabs-Lab8-95.png)
    ![이름 notificationreceiver 만들기](images/AzureLabs-Lab8-96.png)</span><span class="sxs-lookup"><span data-stu-id="ef024-662">![create new c# script](images/AzureLabs-Lab8-95.png)
![name it NotificationReceiver](images/AzureLabs-Lab8-96.png)</span></span>

2.  <span data-ttu-id="ef024-663">스크립트를 두 번 클릭 하 여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-663">Double click on the script to open it.</span></span>

3.  <span data-ttu-id="ef024-664">다음 네임 스페이스를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-664">Add the following namespaces:</span></span>

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

4.  <span data-ttu-id="ef024-665">다음 변수를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-665">Insert the following variables:</span></span>

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

5.  <span data-ttu-id="ef024-666">**HubName** 값을 알림 허브 서비스 이름으로 대체 하 고, **HubListenEndpoint** 값을 Azure Portal의 액세스 정책 탭, azure Notification Hub Service에 있는 끝점 값으로 대체 합니다 (아래 이미지 참조).</span><span class="sxs-lookup"><span data-stu-id="ef024-666">Substitute the **hubName** value with your Notification Hub Service name, and **hubListenEndpoint** value with the endpoint value found in the Access Policies tab, Azure Notification Hub Service, in the Azure Portal (see image below).</span></span>

    ![notification hubs 정책 끝점 삽입](images/AzureLabs-Lab8-97.png)

6.  <span data-ttu-id="ef024-668">이제 **Start ()** 및 **활성 ()** 메서드를 추가 하 여 클래스를 초기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-668">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

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

7.  <span data-ttu-id="ef024-669">**Waitfornotification** 메서드를 추가 하 여 앱이 주 스레드를 사용 하 여 충돌 방지 없이 알림 허브 라이브러리에서 알림을 받을 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-669">Add the **WaitForNotification** method to allow the app to receive notifications from the Notification Hub Library without clashing with the Main Thread:</span></span>

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

8.  <span data-ttu-id="ef024-670">다음 메서드인 **Initnotificationasync ()** 는 초기화 시 Notification hubs 서비스에 응용 프로그램을 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-670">The following method, **InitNotificationAsync()**, will register the application with the notification Hub Service at initialization.</span></span> <span data-ttu-id="ef024-671">Unity는 프로젝트를 빌드할 수 없으므로 코드는 주석 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-671">The code is commented out as Unity will not be able to Build the project.</span></span> <span data-ttu-id="ef024-672">Visual Studio에서 Azure Messaging Nuget 패키지를 가져올 때 주석이 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-672">You will remove the comments when you import the Azure Messaging Nuget package in Visual Studio.</span></span>

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

9.  <span data-ttu-id="ef024-673">다음 처리기, **채널\_pushnotificationreceived ()** 는 알림이 수신 될 때마다 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-673">The following handler, **Channel\_PushNotificationReceived()**, will be triggered every time a notification is received.</span></span> <span data-ttu-id="ef024-674">이 알림은 데스크톱 응용 프로그램에서 이동 된 Azure 테이블 엔터티가 되는 알림을 deserialize 하 고 MR 장면에서 해당 하는 GameObject를 같은 위치로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-674">It will deserialize the notification, which will be the Azure Table Entity that has been moved on the Desktop Application, and then move the corresponding GameObject in the MR scene to the same position.</span></span> 
    
    > [!IMPORTANT]
    > <span data-ttu-id="ef024-675">코드는 Visual Studio 내에서 Nuget 패키지 관리자를 사용 하 여 Unity 프로젝트를 빌드한 후 추가 될 Azure 메시징 라이브러리를 참조 하므로 주석 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-675">The code is commented out because the code references the Azure Messaging library, which you will add after building the Unity project using the Nuget Package Manager, within Visual Studio.</span></span> <span data-ttu-id="ef024-676">따라서 Unity 프로젝트는 주석 처리 되지 않은 경우에는 빌드할 수 없습니다. 프로젝트를 빌드한 다음 Unity로 돌아가려면 해당 코드를 **다시 주석** 으로 처리 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-676">As such, the Unity project will not be able to build, unless it is commented out. Be aware, that should you build your project, and then wish to return to Unity, you will need to **re-comment** that code.</span></span>

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

10. <span data-ttu-id="ef024-677">Unity 편집기로 다시 이동 하기 전에 변경 내용을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-677">Remember to save your changes before going back to the Unity Editor.</span></span>

11. <span data-ttu-id="ef024-678">**계층** 패널에서 **주 카메라** 를 클릭 하 여 해당 속성이 **검사기**에 표시 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-678">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span>

12. <span data-ttu-id="ef024-679">**Scripts** 폴더를 연 상태에서 **notificationreceiver** 스크립트를 선택 하 고 **기본 카메라로**끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-679">With the **Scripts** folder open, select the **NotificationReceiver** script and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="ef024-680">결과는 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-680">The result should be as below:</span></span>

    ![알림 수신기 스크립트를 카메라로 끌어 옵니다.](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > <span data-ttu-id="ef024-682">Microsoft HoloLens에 대해이를 개발 하는 경우 다음과 같이 **기본 카메라**의 *카메라* 구성 요소를 업데이트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-682">If you are developing this for the Microsoft HoloLens, you will need to update the **Main Camera**'s *Camera* component, so that:</span></span>
    > - <span data-ttu-id="ef024-683">플래그 지우기: 단색</span><span class="sxs-lookup"><span data-stu-id="ef024-683">Clear Flags: Solid Color</span></span>
    > - <span data-ttu-id="ef024-684">Background: 검정</span><span class="sxs-lookup"><span data-stu-id="ef024-684">Background: Black</span></span>

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a><span data-ttu-id="ef024-685">16 장-UWP에 혼합 현실 프로젝트 빌드</span><span class="sxs-lookup"><span data-stu-id="ef024-685">Chapter 16 - Build the Mixed Reality Project to UWP</span></span>

<span data-ttu-id="ef024-686">이 장은 이전 프로젝트에 대 한 빌드 프로세스와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-686">This Chapter is identical to build process for the previous project.</span></span> <span data-ttu-id="ef024-687">이제이 프로젝트의 Unity 섹션에 필요한 모든 항목이 완료 되었으므로 Unity에서 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-687">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="ef024-688">**빌드 설정** ( **파일** > **빌드 설정** )으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-688">Navigate to **Build Settings** ( **File** > **Build Settings** ).</span></span>

2.  <span data-ttu-id="ef024-689">**빌드 설정** 메뉴에서 \*\*Unity C# 프로젝트\*\*\*가 선택 (빌드 후이 프로젝트의 스크립트를 편집할 수 있음)를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-689">From the **Build Settings** menu, ensure **Unity C# Projects**\* is ticked (which will allow you to edit the scripts in this project, after build).</span></span>

3.  <span data-ttu-id="ef024-690">이 작업을 완료 한 후 **빌드**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-690">After this is done, click **Build**.</span></span>

    ![프로젝트 빌드](images/AzureLabs-Lab8-99.png)

4.  <span data-ttu-id="ef024-692">빌드할 위치를 묻는 메시지를 표시 하는 **파일 탐색기** 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-692">A **File Explorer** window will popup, prompting you for a location to Build.</span></span> <span data-ttu-id="ef024-693">왼쪽 위 모서리에서 **새 폴더** 를 클릭 하 여 새 폴더를 만들고 이름을 **작성**합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-693">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![빌드 폴더 만들기](images/AzureLabs-Lab8-100.png)

    1.  <span data-ttu-id="ef024-695">새 **빌드** 폴더를 열고 **새 폴더** 를 한 번 더 사용 하 여 다른 폴더를 만든 다음 이름으로 **nh\_MR\_앱**을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-695">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **NH\_MR\_App**.</span></span>

        ![NH_MR_Apps 폴더 만들기](images/AzureLabs-Lab8-101.png)

    2.  <span data-ttu-id="ef024-697">**Nh\_MR\_앱** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-697">With the **NH\_MR\_App** selected.</span></span> <span data-ttu-id="ef024-698">**폴더 선택**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-698">click **Select Folder**.</span></span> <span data-ttu-id="ef024-699">프로젝트를 빌드하는 데 1 분 정도 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-699">The project will take a minute or so to build.</span></span>

5.  <span data-ttu-id="ef024-700">빌드를 수행 하면 새 프로젝트의 위치에서 **파일 탐색기** 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-700">Following the build, a **File Explorer** window will open at the location of your new project.</span></span>



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a><span data-ttu-id="ef024-701">17 장-UnityMRNotifHub 솔루션에 NuGet 패키지 추가</span><span class="sxs-lookup"><span data-stu-id="ef024-701">Chapter 17 - Add NuGet packages to the UnityMRNotifHub Solution</span></span>

> [!WARNING] 
> <span data-ttu-id="ef024-702">다음 NuGet 패키지를 추가 하 고 다음 [챕터](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)에서 코드의 주석 처리를 제거 하면 Unity 프로젝트에서 다시 열 때 코드가 오류를 표시 한다는 점에 주의 하세요.</span><span class="sxs-lookup"><span data-stu-id="ef024-702">Please remember that, once you add the following NuGet Packages (and uncomment the code in the next [Chapter](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)), the Code, when reopened within the Unity Project, will present errors.</span></span> <span data-ttu-id="ef024-703">이전 단계로 돌아가서 Unity 편집기에서 계속 편집 하려는 경우에는 일부 코드에 대 한 설명이 필요 합니다. 그런 다음 Visual Studio로 돌아가서 다시 주석 처리를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-703">If you wish to go back and continue editing in the Unity Editor, you will need comment that errosome code, and then uncomment again later, once you are back in Visual Studio.</span></span> 

<span data-ttu-id="ef024-704">혼합 현실 빌드가 완료 되 면 빌드한 mixed reality 프로젝트로 이동 하 고 해당 폴더 내에서 솔루션 파일 (.sln)을 두 번 클릭 하 여 Visual Studio 2017에서 솔루션을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-704">Once the mixed reality build has been completed, navigate to the mixed reality project, which you built, and double click on the solution (.sln) file within that folder, to open your solution with Visual Studio 2017.</span></span>
<span data-ttu-id="ef024-705">이제 **Windowsazure.servicebus** NuGet 패키지를 추가 해야 합니다. 알림 허브에서 알림을 수신 하는 데 사용 되는 라이브러리입니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-705">You will now need to add the **WindowsAzure.Messaging.managed** NuGet package; this is a library that is used to receive Notifications from the Notification Hub.</span></span>

<span data-ttu-id="ef024-706">NuGet 패키지를 가져오려면:</span><span class="sxs-lookup"><span data-stu-id="ef024-706">To import the NuGet package:</span></span>

1.  <span data-ttu-id="ef024-707">**솔루션 탐색기**에서 솔루션을 마우스 오른쪽 단추로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-707">In the **Solution Explorer**, right click on your Solution</span></span>

2.  <span data-ttu-id="ef024-708">**NuGet 패키지 관리**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-708">Click on **Manage NuGet Packages**.</span></span>

    ![nuget 관리자 열기](images/AzureLabs-Lab8-102.png)

3.  <span data-ttu-id="ef024-710">***찾아보기*** 탭을 선택 하 고 **windowsazure.servicebus**를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-710">Select the ***Browse*** tab and search for **WindowsAzure.Messaging.managed**.</span></span>

    ![windows azure 메시징 패키지 찾기](images/AzureLabs-Lab8-103.png)

4.  <span data-ttu-id="ef024-712">아래와 같이 결과를 선택 하 고 오른쪽 창에서 **프로젝트**옆에 있는 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-712">Select the result (as shown below), and in the window to the right, select the checkbox next to **Project**.</span></span> <span data-ttu-id="ef024-713">그러면 **프로젝트**옆에 있는 확인란에 틱이 포함 되 고, **어셈블리-CSharp** 및 **UnityMRNotifHub** 프로젝트 옆에 있는 확인란과 함께 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-713">This will place a tick in the checkbox next to **Project**, along with the checkbox next to the **Assembly-CSharp** and **UnityMRNotifHub** project.</span></span>

    ![모든 프로젝트의 tick](images/AzureLabs-Lab8-104.png)

5.  <span data-ttu-id="ef024-715">처음에 제공 되는 버전은이 프로젝트와 호환 **되지 않을 수 있습니다** .</span><span class="sxs-lookup"><span data-stu-id="ef024-715">The version initially provided **may not** be compatible with this project.</span></span> <span data-ttu-id="ef024-716">따라서 **버전**옆에 있는 드롭다운 메뉴를 클릭 하 고 **버전 0.1.7.9**를 클릭 한 다음 **설치**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-716">Therefore, click on the dropdown menu next to **Version**, and click **Version 0.1.7.9**, then click **Install**.</span></span>

6.  <span data-ttu-id="ef024-717">이제 NuGet 패키지를 설치 했습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-717">You have now finished installing the NuGet package.</span></span> <span data-ttu-id="ef024-718">**Notificationreceiver** 클래스에서 입력 한 주석 처리 된 코드를 찾고 주석을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-718">Find the commented code you entered in the **NotificationReceiver** class and remove the comments..</span></span>



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a><span data-ttu-id="ef024-719">18 장-UnityMRNotifHub 응용 프로그램 편집, NotificationReceiver 클래스</span><span class="sxs-lookup"><span data-stu-id="ef024-719">Chapter 18 - Edit UnityMRNotifHub application, NotificationReceiver class</span></span>

<span data-ttu-id="ef024-720">**NuGet 패키지**를 추가한 후에는 **notificationreceiver** 클래스 내에서 일부 코드의 *주석 처리를 제거* 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-720">Following having added the **NuGet Packages**, you will need to *uncomment* some of the code within the **NotificationReceiver** class.</span></span>

<span data-ttu-id="ef024-721">다음을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-721">This includes:</span></span>

1. <span data-ttu-id="ef024-722">위쪽의 네임 스페이스:</span><span class="sxs-lookup"><span data-stu-id="ef024-722">The namespace at the top:</span></span>

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. <span data-ttu-id="ef024-723">**InitNotificationsAsync ()** 메서드 내의 모든 코드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-723">All the code within the **InitNotificationsAsync()** method:</span></span>

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
> <span data-ttu-id="ef024-724">위의 코드에 주석이 포함 되어 있습니다. 해당 주석을 실수로 *주석 처리가 제거* 하지 않았는지 확인 합니다 (!가 있는 경우 코드가 컴파일되지 않음).</span><span class="sxs-lookup"><span data-stu-id="ef024-724">The code above has a comment in it: ensure that you have not accidentally *uncommented* that comment (as the code will not compile if you have!).</span></span>

3. <span data-ttu-id="ef024-725">그리고 마지막으로 **Channel_PushNotificationReceived** 이벤트는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-725">And, lastly, the **Channel_PushNotificationReceived** event:</span></span>

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

<span data-ttu-id="ef024-726">이러한 주석 처리가 제거을 사용 하 여 저장 한 후 다음 챕터로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-726">With these uncommented, ensure that you save, and then proceed to the next Chapter.</span></span>

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a><span data-ttu-id="ef024-727">19 장-혼합 현실 프로젝트를 스토어 앱에 연결</span><span class="sxs-lookup"><span data-stu-id="ef024-727">Chapter 19 - Associate the mixed reality project to the Store app</span></span>

<span data-ttu-id="ef024-728">이제 랩 시작 시에서 만든 스토어 앱에 **혼합 현실** 프로젝트를 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-728">You now need to associate the **mixed reality** project to the Store App you created in at the start of the lab.</span></span>

1.  <span data-ttu-id="ef024-729">솔루션을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-729">Open the solution.</span></span>

2.  <span data-ttu-id="ef024-730">솔루션 탐색기 패널에서 UWP 앱 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **스토어**로 이동 및 **스토어에 앱 연결**...을 마우스 오른쪽 단추로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-730">Right click on the UWP app Project in the Solution Explorer panel, the go to **Store**, and **Associate App with the Store...**.</span></span>

    ![저장소 연결 열기](images/AzureLabs-Lab8-105.png)

3.  <span data-ttu-id="ef024-732">**응용 프로그램을 Windows 스토어에 연결**이라는 새 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-732">A new window will appear called **Associate Your App with the Windows Store**.</span></span> <span data-ttu-id="ef024-733">**다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-733">Click **Next**.</span></span>

    ![다음 화면으로 이동](images/AzureLabs-Lab8-106.png)

4.  <span data-ttu-id="ef024-735">로그인 한 계정과 연결 된 모든 응용 프로그램을 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-735">It will load up all the Applications associated with the Account which you have logged in.</span></span> <span data-ttu-id="ef024-736">계정에 로그인 하지 않은 경우이 페이지에 로그인 **할 수 있습니다** .</span><span class="sxs-lookup"><span data-stu-id="ef024-736">If you are not logged in to your account, you can **Log In** on this page.</span></span>

5.  <span data-ttu-id="ef024-737">이 자습서의 시작 부분에서 만든 **스토어 앱 이름을** 찾아 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-737">Find the **Store App name** that you created at the start of this tutorial and select it.</span></span> <span data-ttu-id="ef024-738">그리고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-738">Then click **Next**.</span></span>

    ![상점 이름 찾기 및 선택](images/AzureLabs-Lab8-107.png)

6.  <span data-ttu-id="ef024-740">**연결**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-740">Click **Associate**.</span></span>

    ![앱 연결](images/AzureLabs-Lab8-108.png)

7.  <span data-ttu-id="ef024-742">이제 앱이 스토어 앱에 **연결** 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-742">Your App is now **Associated** with the Store App.</span></span> <span data-ttu-id="ef024-743">알림을 사용 하도록 설정 하는 데 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-743">This is necessary for enabling Notifications.</span></span>

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a><span data-ttu-id="ef024-744">20 장-UnityMRNotifHub 및 UnityDesktopNotifHub 응용 프로그램 배포</span><span class="sxs-lookup"><span data-stu-id="ef024-744">Chapter 20 - Deploy UnityMRNotifHub and UnityDesktopNotifHub applications</span></span>

<span data-ttu-id="ef024-745">이 장은 두 명의 사용자에 게 더 쉬울 수 있습니다. 즉, 실행 중인 앱을 모두 포함 하 고 컴퓨터 데스크톱에서 실행 하는 앱과 몰입 형 헤드셋 내에서 다른 항목을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-745">This Chapter may be easier with two people, as the result will include both apps running, one running on your computer Desktop, and the other within your immersive headset.</span></span>

<span data-ttu-id="ef024-746">모던 헤드셋 앱은 장면 (로컬 Gameobject의 위치 변경)에 대 한 변경 내용을 받기 위해 대기 중 이며, 데스크톱 앱은 MR 앱에 공유 되는 로컬 장면 (위치 변경)을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-746">The immersive headset app is waiting to receive changes to the scene (position changes of the local GameObjects), and the Desktop app will be making changes to their local scene (position changes), which will be shared to the MR app.</span></span> <span data-ttu-id="ef024-747">수신자가 수신을 시작할 수 있도록 먼저 MR 앱을 배포한 다음 데스크톱 앱을 배포 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-747">It makes sense to deploy the MR app first, followed by the Desktop app, so that the receiver can begin listening.</span></span>

<span data-ttu-id="ef024-748">로컬 컴퓨터에 **UnityMRNotifHub** 앱을 배포 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-748">To deploy the **UnityMRNotifHub** app on your Local Machine:</span></span>

1.  <span data-ttu-id="ef024-749">**Visual Studio 2017**에서 **UnityMRNotifHub** 앱의 솔루션 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-749">Open the solution file of your **UnityMRNotifHub** app in **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="ef024-750">**솔루션 플랫폼**에서 **X86, 로컬 컴퓨터**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-750">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="ef024-751">**솔루션 구성** 에서 **디버그**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-751">In the **Solution Configuration** select **Debug**.</span></span>

    ![프로젝트 구성 설정](images/AzureLabs-Lab8-109.png)

4.  <span data-ttu-id="ef024-753">**빌드 메뉴로** 이동 하 여 **솔루션 배포** 를 클릭 하 여 응용 프로그램을 컴퓨터에 테스트용으로 로드.</span><span class="sxs-lookup"><span data-stu-id="ef024-753">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="ef024-754">이제 앱이 설치 된 앱 목록에 표시 되어 시작 될 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-754">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

<span data-ttu-id="ef024-755">로컬 컴퓨터에 **UnityDesktopNotifHub** 앱을 배포 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-755">To deploy the **UnityDesktopNotifHub** app on Local Machine:</span></span>

1.  <span data-ttu-id="ef024-756">**Visual Studio 2017**에서 **UnityDesktopNotifHub** 앱의 솔루션 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-756">Open the solution file of your **UnityDesktopNotifHub** app in **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="ef024-757">**솔루션 플랫폼**에서 **X86, 로컬 컴퓨터**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-757">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="ef024-758">**솔루션 구성** 에서 **디버그**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-758">In the **Solution Configuration** select **Debug**.</span></span>

    ![프로젝트 구성 설정](images/AzureLabs-Lab8-110.png)

4.  <span data-ttu-id="ef024-760">**빌드 메뉴로** 이동 하 여 **솔루션 배포** 를 클릭 하 여 응용 프로그램을 컴퓨터에 테스트용으로 로드.</span><span class="sxs-lookup"><span data-stu-id="ef024-760">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="ef024-761">이제 앱이 설치 된 앱 목록에 표시 되어 시작 될 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-761">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

6.  <span data-ttu-id="ef024-762">혼합 현실 응용 프로그램을 시작한 다음 데스크톱 응용 프로그램을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-762">Launch the mixed reality application, followed by the Desktop application.</span></span>

<span data-ttu-id="ef024-763">두 응용 프로그램을 모두 실행 하는 경우 마우스 왼쪽 단추를 사용 하 여 바탕 화면 장면에서 개체를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-763">With both applications running, move an object in the desktop scene (using the Left Mouse Button).</span></span> <span data-ttu-id="ef024-764">이러한 위치 변경은 로컬로 수행 되 고 serialize 되며 함수 앱 서비스로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-764">These positional changes will be made locally, serialized, and sent to the Function App service.</span></span> <span data-ttu-id="ef024-765">그러면 함수 앱 서비스에서 알림 허브와 함께 테이블을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-765">The Function App service will then update the Table along with the Notification Hub.</span></span> <span data-ttu-id="ef024-766">업데이트를 받으면 알림 허브는 등록 된 모든 응용 프로그램 (이 경우에는 몰입 형 헤드셋 앱)에 업데이트 된 데이터를 직접 전송 합니다. 그러면 들어오는 데이터를 deserialize 하 고 새 위치 데이터를 로컬 개체에 적용 합니다. 장면에서 이동</span><span class="sxs-lookup"><span data-stu-id="ef024-766">Having received an update, the Notification Hub will send the updated data directly to all the registered applications (in this case the immersive headset app), which will then deserialize the incoming data, and apply the new positional data to the local objects, moving them in scene.</span></span>


## <a name="your-finished-your-azure-notification-hubs-application"></a><span data-ttu-id="ef024-767">Azure Notification Hubs 응용 프로그램 완성</span><span class="sxs-lookup"><span data-stu-id="ef024-767">Your finished your Azure Notification Hubs application</span></span>
 
<span data-ttu-id="ef024-768">축 하 합니다. Azure Notification Hubs 서비스를 활용 하 고 앱 간의 통신을 허용 하는 혼합 현실 앱을 빌드 했습니다.</span><span class="sxs-lookup"><span data-stu-id="ef024-768">Congratulations, you built a mixed reality app that leverages the Azure Notification Hubs Service and allow communication between apps.</span></span>
 
![최종 제품 종료](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a><span data-ttu-id="ef024-770">보너스 연습</span><span class="sxs-lookup"><span data-stu-id="ef024-770">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="ef024-771">연습 1</span><span class="sxs-lookup"><span data-stu-id="ef024-771">Exercise 1</span></span>

<span data-ttu-id="ef024-772">Gameobject 색을 변경 하는 방법을 설명 하 고 장면을 표시 하는 다른 앱으로 알림을 보낼 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="ef024-772">Can you work out how to change the color of the GameObjects and send that notification to other apps viewing the scene?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="ef024-773">연습 2</span><span class="sxs-lookup"><span data-stu-id="ef024-773">Exercise 2</span></span>

<span data-ttu-id="ef024-774">Gameobject의 이동을 MR 앱에 추가 하 고 데스크톱 앱에서 업데이트 된 장면을 볼 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="ef024-774">Can you add movement of the GameObjects to your MR app and see the updated scene in your desktop app?</span></span>
