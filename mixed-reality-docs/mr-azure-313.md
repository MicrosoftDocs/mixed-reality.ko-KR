---
title: MR 및 Azure 313-IoT Hub 서비스
description: 이 과정을 완료 하 여 Ubuntu 16.4를 실행 하는 가상 머신에서 Azure IoT Hub 서비스를 구현한 다음 Microsoft HoloLens 또는 모던 (VR) 헤드셋을 사용 하 여 메시지 데이터를 시각화 하는 방법을 알아보세요.
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: azure, mixed reality, 아카데미, edge, iot edge, 자습서, api, 알림, 기능, 테이블, hololens, 몰입 형, vr, iot, virtual machine, ubuntu, python
ms.openlocfilehash: 93f7dc64426360d2e02b0ee0a9b1796fc8f2b469
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694595"
---
>[!NOTE]
><span data-ttu-id="04558-104">혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="04558-105">따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="04558-106">이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="04558-107">지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="04558-108">향후에는 HoloLens 2를 개발 하는 방법을 보여 주는 새 자습서 시리즈를 게시할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="04558-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="04558-109">이 알림은 게시 될 때 해당 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-313-iot-hub-service"></a><span data-ttu-id="04558-110">MR 및 Azure 313: IoT Hub 서비스</span><span class="sxs-lookup"><span data-stu-id="04558-110">MR and Azure 313: IoT Hub Service</span></span>

![과정 결과](images/AzureLabs-Lab313-00.png)

<span data-ttu-id="04558-112">이 과정에서는 Ubuntu 16.4 운영 체제를 실행 하는 가상 머신에서 **Azure IoT Hub 서비스** 를 구현 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-112">In this course, you will learn how to implement an **Azure IoT Hub Service** on a virtual machine running the Ubuntu 16.4 operating system.</span></span> <span data-ttu-id="04558-113">그런 다음 **azure 함수 앱** 는 Ubuntu VM에서 메시지를 수신 하 고 **azure Table Service**내에 결과를 저장 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-113">An **Azure Function App** will then be used to receive messages from your Ubuntu VM, and store the result within an **Azure Table Service**.</span></span> <span data-ttu-id="04558-114">그러면 Microsoft HoloLens 또는 모던 (VR) 헤드셋의 **Power BI** 를 사용 하 여이 데이터를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-114">You will then be able to view this data using **Power BI** on Microsoft HoloLens or immersive (VR) headset.</span></span>

<span data-ttu-id="04558-115">이 과정의 내용은 IoT Edge 장치에 *적용* 될 수 있지만,이 과정에서는 가상 컴퓨터 환경에 집중 하는 것이 좋습니다. 따라서 실제에 지 장치에 대 한 액세스가 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-115">The content of this course *is applicable* to IoT Edge devices, though for the purpose of this course, the focus will be on a virtual machine environment, so that access to a physical Edge device is not necessary.</span></span>

<span data-ttu-id="04558-116">이 과정을 완료 하면 다음을 배울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-116">By completing this course, you will learn to:</span></span>

- <span data-ttu-id="04558-117">IoT 장치를 표시 하는 가상 컴퓨터 (Ubuntu 16 OS)에 **IoT Edge 모듈** 을 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-117">Deploy an **IoT Edge module** to a Virtual Machine (Ubuntu 16 OS), which will represent your IoT device.</span></span>
- <span data-ttu-id="04558-118">컨테이너에 저장 된 이미지를 분석 하는 코드를 사용 하 여 **Azure Custom Vision Tensorflow 모델** 을 Edge 모듈에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-118">Add an **Azure Custom Vision Tensorflow Model** to the Edge module, with code that will analyze images stored in the container.</span></span>
- <span data-ttu-id="04558-119">분석 결과 메시지를 **IoT Hub 서비스로**다시 보내도록 모듈을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-119">Set up the module to send the analysis result message back to your **IoT Hub Service**.</span></span>
- <span data-ttu-id="04558-120">Azure **함수 앱** 을 사용 하 여 **azure 테이블**내에 메시지를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-120">Use an **Azure Function App** to store the message within an **Azure Table**.</span></span>
- <span data-ttu-id="04558-121">**Power BI** 설정 하 여 저장 된 메시지를 수집 하 고 보고서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="04558-121">Set up **Power BI** to collect the stored message and create a report.</span></span>
- <span data-ttu-id="04558-122">**Power BI**내에서 IoT 메시지 데이터를 시각화 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-122">Visualize your IoT message data within **Power BI**.</span></span>

<span data-ttu-id="04558-123">사용할 서비스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-123">The Services you will use include:</span></span>

- <span data-ttu-id="04558-124">**Azure IoT Hub** 는 개발자가 IoT 자산을 연결, 모니터링 및 관리 하는 데 사용할 수 있는 Microsoft Azure 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="04558-124">**Azure IoT Hub** is a Microsoft Azure Service which allows developers to connect, monitor, and manage, IoT assets.</span></span> <span data-ttu-id="04558-125">자세한 내용은 [ **Azure IoT Hub 서비스** 페이지](https://azure.microsoft.com/en-au/services/iot-hub/)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="04558-125">For more information, visit the [**Azure IoT Hub Service** page](https://azure.microsoft.com/en-au/services/iot-hub/).</span></span>

- <span data-ttu-id="04558-126">**Azure Container Registry** 는 개발자가 다양 한 유형의 컨테이너에 대해 컨테이너 이미지를 저장할 수 있도록 하는 Microsoft Azure 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="04558-126">**Azure Container Registry** is a Microsoft Azure Service which allows developers to store container images, for various types of containers.</span></span> <span data-ttu-id="04558-127">자세한 내용은 [ **Azure Container Registry 서비스** 페이지](https://azure.microsoft.com/en-au/services/container-registry/)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="04558-127">For more information, visit the [**Azure Container Registry Service** page](https://azure.microsoft.com/en-au/services/container-registry/).</span></span>

- <span data-ttu-id="04558-128">**Azure 함수 앱** 는 개발자가 azure에서 작은 코드, ' 함수 '를 실행할 수 있도록 하는 Microsoft Azure 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="04558-128">**Azure Function App** is a Microsoft Azure Service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="04558-129">이렇게 하면 다양 한 이점을 얻을 수 있는 로컬 응용 프로그램이 아닌 클라우드로 작업을 위임할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-129">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="04558-130">**Azure Functions** 는 C\#, F\#, node.js, Java 및 PHP를 비롯 한 몇 가지 개발 언어를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-130">**Azure Functions** supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="04558-131">자세한 내용은 [ **Azure Functions** 페이지](https://docs.microsoft.com/azure/azure-functions/functions-overview)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="04558-131">For more information, visit the [**Azure Functions** page](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

- <span data-ttu-id="04558-132">**Azure Storage: 테이블** 은 개발자가 구조화 된 비 SQL 데이터를 클라우드에 저장 하 여 어디서 나 쉽게 액세스할 수 있도록 하는 Microsoft Azure 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="04558-132">**Azure Storage: Tables** is a Microsoft Azure Service, which allows developers to store structured, non-SQL, data in the cloud, making it easily accessible anywhere.</span></span> <span data-ttu-id="04558-133">이 서비스는 스키마 없는 디자인을 boasts, 필요에 따라 테이블의 진화를 허용 하므로 매우 유연 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-133">The Service boasts a schema-less design, allowing for the evolution of tables as needed, and thus is very flexible.</span></span> <span data-ttu-id="04558-134">자세한 내용은 [ **Azure Tables** 페이지를 참조 하세요.](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span><span class="sxs-lookup"><span data-stu-id="04558-134">For more information, visit the [**Azure Tables** page](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span></span>

<span data-ttu-id="04558-135">이 과정에서는 IoT Hub 서비스를 설정 하 고 사용 하는 방법을 설명 하 고 장치에서 제공 하는 응답을 시각화 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-135">This course will teach you how to setup and use the IoT Hub Service, and then visualize a response provided by a device.</span></span> <span data-ttu-id="04558-136">사용자가 빌드할 수 있는 사용자 지정 IoT Hub 서비스 설정에 이러한 개념을 적용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-136">It will be up to you to apply these concepts to a custom IoT Hub Service setup, which you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="04558-137">장치 지원</span><span class="sxs-lookup"><span data-stu-id="04558-137">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="04558-138">과정</span><span class="sxs-lookup"><span data-stu-id="04558-138">Course</span></span></th><th style="width:150px"> <span data-ttu-id="04558-139"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="04558-139"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="04558-140"><a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="04558-140"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="04558-141">MR 및 Azure 313: IoT Hub 서비스</span><span class="sxs-lookup"><span data-stu-id="04558-141">MR and Azure 313: IoT Hub Service</span></span></td><td style="text-align: center;"> <span data-ttu-id="04558-142">✔️</span><span class="sxs-lookup"><span data-stu-id="04558-142">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="04558-143">✔️</span><span class="sxs-lookup"><span data-stu-id="04558-143">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="04558-144">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="04558-144">Prerequisites</span></span>

<span data-ttu-id="04558-145">Microsoft HoloLens를 비롯 하 여 혼합 현실에서 개발 하기 위한 최신 필수 구성 요소는 [도구 설치](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) 문서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="04558-145">For the most up-to-date prerequisites for developing with mixed reality, including with the Microsoft HoloLens, visit the [Install the tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) article.</span></span>

> [!NOTE]
> <span data-ttu-id="04558-146">이 자습서는 Python을 사용 하는 기본 경험이 있는 개발자를 위해 작성 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-146">This tutorial is designed for developers who have basic experience with Python.</span></span> <span data-ttu-id="04558-147">또한이 문서에서 사전 요구 사항 및 작성 된 지침은 작성 시 테스트 되 고 확인 된 내용 (7 월 2018)을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="04558-147">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="04558-148">[도구 설치](install-the-tools.md) 문서에 나와 있는 것 처럼 최신 소프트웨어를 무료로 사용할 수 있지만,이 과정의 정보가 아래에 나열 된 것과 같은 최신 소프트웨어에서 찾을 수 있는 것으로 가정 하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-148">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than that listed below.</span></span>

<span data-ttu-id="04558-149">다음 하드웨어 및 소프트웨어가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-149">The following hardware and software is required:</span></span>

- <span data-ttu-id="04558-150">Windows 10의 작성자 업데이트 (또는 그 이상), **개발자 모드 사용**</span><span class="sxs-lookup"><span data-stu-id="04558-150">Windows 10 Fall Creators Update (or later), **Developer Mode enabled**</span></span>

    > [!WARNING]
    > <span data-ttu-id="04558-151">Windows 10 Home Edition에서 Hyper-v를 사용 하 여 가상 컴퓨터를 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-151">You cannot run a Virtual Machine using Hyper-V on Windows 10 Home Edition.</span></span>

- <span data-ttu-id="04558-152">Windows 10 SDK (최신 버전)</span><span class="sxs-lookup"><span data-stu-id="04558-152">Windows 10 SDK (latest version)</span></span>
- <span data-ttu-id="04558-153">HoloLens, **개발자 모드 사용**</span><span class="sxs-lookup"><span data-stu-id="04558-153">A HoloLens, **Developer Mode enabled**</span></span>
- <span data-ttu-id="04558-154">Visual Studio 2017.15.4 (Azure 클라우드 탐색기 액세스 하는 데만 사용 됨)</span><span class="sxs-lookup"><span data-stu-id="04558-154">Visual Studio 2017.15.4 (Only used to access the Azure Cloud Explorer)</span></span>
- <span data-ttu-id="04558-155">Azure 및 IoT Hub 서비스에 대 한 인터넷 액세스.</span><span class="sxs-lookup"><span data-stu-id="04558-155">Internet Access for Azure, and for IoT Hub Service.</span></span> <span data-ttu-id="04558-156">자세한 내용은 [IoT Hub 서비스 페이지에 대 한 링크를](https://azure.microsoft.com/en-au/services/iot-hub/) 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="04558-156">For more information, please follow this [link to IoT Hub Service page](https://azure.microsoft.com/en-au/services/iot-hub/)</span></span>
- <span data-ttu-id="04558-157">기계 학습 모델입니다.</span><span class="sxs-lookup"><span data-stu-id="04558-157">A machine learning model.</span></span> <span data-ttu-id="04558-158">모델을 사용할 준비가 되지 않은 경우 [이 과정에서 제공 되는 모델을 사용할 수](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip)있습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-158">If you do not have your own ready to use model, [you can use the model provided with this course](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).</span></span>
- <span data-ttu-id="04558-159">Windows 10 개발 컴퓨터에서 **hyper-v** 소프트웨어를 사용 하도록 설정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-159">**Hyper-V** software enabled on your Windows 10 development machine.</span></span>
- <span data-ttu-id="04558-160">개발 컴퓨터에서 실행 되는 Ubuntu (16.4 또는 18.4)를 실행 하는 가상 머신 또는 Linux를 실행 하는 별도의 컴퓨터 (Ubuntu 16.4 또는 18.4)를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-160">A Virtual Machine running Ubuntu (16.4 or 18.4), running on your development machine or alternatively you can use a separate computer running Linux (Ubuntu 16.4 or 18.4).</span></span> <span data-ttu-id="04558-161">Windows에서 Hyper-v를 사용 하 여 VM을 만드는 방법에 대 한 자세한 내용은 ["시작 하기 전에" 챕터](#before-you-start)에서 확인할 수 있습니다. (https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).</span><span class="sxs-lookup"><span data-stu-id="04558-161">You can find more information on how to create a VM on Windows using Hyper-V in the ["Before you Start" chapter](#before-you-start).(https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).</span></span>  



### <a name="before-you-start"></a><span data-ttu-id="04558-162">시작하기 전 주의 사항</span><span class="sxs-lookup"><span data-stu-id="04558-162">Before you start</span></span>

1. <span data-ttu-id="04558-163">HoloLens를 설정 하 고 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-163">Set up and test your HoloLens.</span></span> <span data-ttu-id="04558-164">HoloLens를 설정 하는 데 지원이 필요한 경우 [hololens 설정 문서를 방문](https://docs.microsoft.com/hololens/hololens-setup)해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-164">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span>
2. <span data-ttu-id="04558-165">새 HoloLens 앱 개발을 시작할 때 **보정** 및 **센서 조정을** 수행 하는 것이 좋습니다 (경우에 따라 각 사용자에 대해 해당 작업을 수행 하는 데 도움이 될 수 있음).</span><span class="sxs-lookup"><span data-stu-id="04558-165">It is a good idea to perform **Calibration** and **Sensor Tuning** when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span>

<span data-ttu-id="04558-166">보정에 대 한 도움말을 보려면 [HoloLens 보정 문서에](calibration.md#hololens)대 한 다음 링크를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="04558-166">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="04558-167">센서 조정에 대 한 도움말을 보려면 [HoloLens 센서 조정 문서에 대 한 링크를](sensor-tuning.md)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="04558-167">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

3. <span data-ttu-id="04558-168">**Hyper-v**를 사용 하 여 **Ubuntu 가상 머신을** 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-168">Set up your **Ubuntu Virtual Machine** using **Hyper-V**.</span></span> <span data-ttu-id="04558-169">프로세스에 도움이 되는 리소스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-169">The following resources will help you with the process.</span></span>
    1.  <span data-ttu-id="04558-170">먼저이 링크에 따라 [Ubuntu 16.04.4 LTS (Xenial Xerus) ISO를 다운로드](http://au.releases.ubuntu.com/16.04/)합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-170">First, follow this link to [download the Ubuntu 16.04.4 LTS (Xenial Xerus) ISO](http://au.releases.ubuntu.com/16.04/).</span></span> <span data-ttu-id="04558-171">**AMD64 (64 비트 PC) 데스크톱 이미지**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-171">Select the **64-bit PC (AMD64) desktop image**.</span></span>
    2.  <span data-ttu-id="04558-172">Windows 10 컴퓨터에서 **hyper-v** 를 사용 하도록 설정 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-172">Make sure **Hyper-V** is enabled on your Windows 10 machine.</span></span> <span data-ttu-id="04558-173">[Windows 10에서 hyper-v를 설치 하 고 사용 하도록 설정](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)하는 방법에 대 한 지침은이 링크를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="04558-173">You can follow this link for guidance on [installing and enabling Hyper-V on Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).</span></span>
    3.  <span data-ttu-id="04558-174">Hyper-v를 시작 하 고 새 Ubuntu VM을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="04558-174">Start Hyper-V and create a new Ubuntu VM.</span></span> <span data-ttu-id="04558-175">[Hyper-v를 사용 하 여 VM을 만드는 방법에](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine)대 한 단계별 가이드는 다음 링크를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="04558-175">You can follow this link for a [step by step guide on how to create a VM with Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine).</span></span> <span data-ttu-id="04558-176">**"부팅 가능한 이미지 파일에서 운영 체제 설치"** 를 요청 하는 경우 이전에 다운로드 한 **Ubuntu ISO** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-176">When requested to **"Install an operating system from a bootable image file"**, select the **Ubuntu ISO** you have download earlier.</span></span>

    > [!NOTE]
    > <span data-ttu-id="04558-177">**Hyper-v 빠른 생성** 을 사용 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-177">Using **Hyper-V Quick Create** is not suggested.</span></span>  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a><span data-ttu-id="04558-178">1 장-Custom Vision 모델 검색</span><span class="sxs-lookup"><span data-stu-id="04558-178">Chapter 1 - Retrieve the Custom Vision model</span></span>

<span data-ttu-id="04558-179">이 과정에서는 이미지에서 키보드와 마우스를 검색 하는 [미리 작성 된 Custom Vision 모델](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) 에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-179">With this course you will have access to a [pre-built Custom Vision model](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) that detects keyboards and mice from images.</span></span> <span data-ttu-id="04558-180">이를 사용 하는 경우 [2 장으로](#chapter-2---the-container-registry-service)이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-180">If you use this, proceed to [Chapter 2](#chapter-2---the-container-registry-service).</span></span>

<span data-ttu-id="04558-181">그러나 사용자 고유의 Custom Vision 모델을 사용 하려는 경우 다음 단계를 따를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-181">However, you can follow these steps if you wish to use your own Custom Vision model:</span></span>

1. <span data-ttu-id="04558-182">**Custom Vision 프로젝트** 에서 **성능** 탭으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-182">In your **Custom Vision Project** go to the **Performance** tab.</span></span>

    > [!WARNING]
    > <span data-ttu-id="04558-183">모델을 내보내려면 *compact* 도메인을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-183">Your model must use a *compact* domain, to export the model.</span></span> <span data-ttu-id="04558-184">프로젝트에 대 한 설정에서 모델 도메인을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-184">You can change your models domain in the settings for your project.</span></span>

    ![성능 탭](images/AzureLabs-Lab313-01.png)

2. <span data-ttu-id="04558-186">내보내려는 **반복** 을 선택 하 고 **내보내기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-186">Select the **Iteration** you want to export and click on **Export**.</span></span> <span data-ttu-id="04558-187">블레이드가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-187">A blade will appear.</span></span>

    ![블레이드 내보내기](images/AzureLabs-Lab313-02.png)

3. <span data-ttu-id="04558-189">블레이드에서 **Docker 파일**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-189">In the blade click **Docker File**.</span></span>

    ![docker 선택](images/AzureLabs-Lab313-03.png)

4. <span data-ttu-id="04558-191">드롭다운 메뉴에서 **Linux** 를 클릭 한 다음 **다운로드**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-191">Click **Linux** in the drop-down menu and then click on **Download**.</span></span>

    ![다운로드 클릭](images/AzureLabs-Lab313-04.png)

5. <span data-ttu-id="04558-193">콘텐츠 압축을 풉니다.</span><span class="sxs-lookup"><span data-stu-id="04558-193">Unzip the content.</span></span> <span data-ttu-id="04558-194">이 과정의 뒷부분에서이를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-194">You will use it later in this course.</span></span>

## <a name="chapter-2---the-container-registry-service"></a><span data-ttu-id="04558-195">2 장-Container Registry 서비스</span><span class="sxs-lookup"><span data-stu-id="04558-195">Chapter 2 - The Container Registry Service</span></span>

<span data-ttu-id="04558-196">**Container Registry 서비스** 는 컨테이너를 호스트 하는 데 사용 되는 리포지토리입니다.</span><span class="sxs-lookup"><span data-stu-id="04558-196">The **Container Registry Service** is the repository used to host your containers.</span></span>

<span data-ttu-id="04558-197">이 과정에서 빌드하고 사용할 **IoT Hub 서비스** 는에 지 장치에 배포할 컨테이너를 얻기 위한 **Container Registry 서비스** 를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="04558-197">The **IoT Hub Service** that you will build and use in this course, refers to **Container Registry Service** to obtain the containers to deploy in your Edge Device.</span></span>

1. <span data-ttu-id="04558-198">먼저 [Azure Portal에 대](https://portal.azure.com/)한이 링크를 따르고 자격 증명으로 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-198">First, follow this [link to the Azure Portal](https://portal.azure.com/), and login with your credentials.</span></span>

2. <span data-ttu-id="04558-199">**리소스 만들기** 로 이동 하 여 **Container Registry**찾습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-199">Go to **Create a resource** and look for **Container Registry**.</span></span>

    ![컨테이너 레지스트리](images/AzureLabs-Lab313-05.png)

3. <span data-ttu-id="04558-201">**만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-201">Click on **Create**.</span></span>

    ![](images/AzureLabs-Lab313-06.png)

4. <span data-ttu-id="04558-202">서비스 설정 매개 변수를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-202">Set the Service setup parameters:</span></span>

    1. <span data-ttu-id="04558-203">프로젝트의 이름을 삽입 합니다 .이 예제에서는 **IoTCRegistry**라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-203">Insert a name for your project, In this example its called **IoTCRegistry**.</span></span>

    2. <span data-ttu-id="04558-204">리소스 그룹을 선택 하거나 새 **리소스 그룹** 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="04558-204">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="04558-205">리소스 그룹은 Azure 자산 컬렉션에 대 한 모니터링, 제어 액세스, 프로 비전 및 관리를 위한 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-205">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="04558-206">단일 프로젝트와 연결 된 모든 Azure 서비스 (예: 이러한 과정)를 공용 리소스 그룹에 유지 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-206">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

    3. <span data-ttu-id="04558-207">서비스의 위치를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-207">Set the location of the Service.</span></span>

    4. <span data-ttu-id="04558-208">**관리 사용자** 를 **사용**으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-208">Set **Admin user** to **Enable**.</span></span>

    5. <span data-ttu-id="04558-209">**SKU** 를 **기본**으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-209">Set **SKU** to **Basic**.</span></span> 

    ![](images/AzureLabs-Lab313-07.png)

5. <span data-ttu-id="04558-210">**만들기** 를 클릭 하 고 서비스를 만들 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="04558-210">Click **Create** and wait for the Services to be created.</span></span> 

6. <span data-ttu-id="04558-211">*Container Registry*성공적으로 생성 되었음을 알리는 알림이 표시 되 면 서비스로 **이동** 을 클릭 하 여 서비스 페이지로 리디렉션됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-211">Once the notification pops up informing you of the successful creation of the *Container Registry*, click on **Go to resource** to be redirected to your Service page.</span></span>

    ![](images/AzureLabs-Lab313-08.png)

7. <span data-ttu-id="04558-212">*Container Registry* 서비스 페이지에서 **액세스 키**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-212">In the *Container Registry* Service page, click on **Access keys**.</span></span>

8. <span data-ttu-id="04558-213">다음 매개 변수를 기록해 둡니다 (메모장을 사용할 수 있음).</span><span class="sxs-lookup"><span data-stu-id="04558-213">Take note (you could use your Notepad) of the following parameters:</span></span>
    1. <span data-ttu-id="04558-214">**로그인 서버**</span><span class="sxs-lookup"><span data-stu-id="04558-214">**Login Server**</span></span>
    2. <span data-ttu-id="04558-215">**이름**</span><span class="sxs-lookup"><span data-stu-id="04558-215">**Username**</span></span>
    3. <span data-ttu-id="04558-216">**암호**</span><span class="sxs-lookup"><span data-stu-id="04558-216">**Password**</span></span>

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a><span data-ttu-id="04558-217">3 장-IoT Hub 서비스</span><span class="sxs-lookup"><span data-stu-id="04558-217">Chapter 3 - The IoT Hub Service</span></span>

<span data-ttu-id="04558-218">이제 **IoT Hub 서비스**를 만들고 설정 하는 과정을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-218">Now you will begin the creation and setup of your **IoT Hub Service**.</span></span>

1. <span data-ttu-id="04558-219">아직 로그인 하지 않은 경우 [Azure Portal](https://portal.azure.com)에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-219">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2.  <span data-ttu-id="04558-220">로그인 되 면 왼쪽 위 모서리에서 **리소스 만들기** 를 클릭 하 고 **IoT Hub**를 검색 한 다음 **Enter 키**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="04558-220">Once logged in, click on **Create a resource** in the top left corner, and search for **IoT Hub**, and click **Enter**.</span></span>

 ![저장소 계정 검색](images/AzureLabs-Lab313-10.png)

3.  <span data-ttu-id="04558-222">새 페이지에 **저장소 계정** 서비스에 대 한 설명이 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-222">The new page will provide a description of the **Storage account** Service.</span></span> <span data-ttu-id="04558-223">이 프롬프트의 왼쪽 아래에서 **만들기** 단추를 클릭 하 여이 서비스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="04558-223">At the bottom left of this prompt, click the **Create** button, to create an instance of this Service.</span></span>

    ![저장소 인스턴스 만들기](images/AzureLabs-Lab313-11.png)

4.  <span data-ttu-id="04558-225">**만들기**를 클릭 하면 패널이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-225">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="04558-226">리소스 그룹을 선택 하거나 새 **리소스 그룹** 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="04558-226">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="04558-227">리소스 그룹은 Azure 자산의 컬렉션에 대 한 청구를 모니터링 하 고, 액세스를 제어 하 고, 프로 비전 하 고, 관리 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-227">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="04558-228">단일 프로젝트와 연결 된 모든 Azure 서비스 (예: 이러한 과정)를 공용 리소스 그룹에 유지 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-228">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="04558-229">Azure 리소스 그룹에 대 한 자세한 내용을 보려면 [리소스 그룹을 관리 하는 방법에 대](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)한 다음 링크를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="04558-229">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>


    2. <span data-ttu-id="04558-230">적절 한 **위치** 를 선택 합니다 .이 과정에서 만드는 모든 서비스에서 동일한 위치를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-230">Select an appropriate **Location** (Use the same location across all the Services you create in this course).</span></span>

    3. <span data-ttu-id="04558-231">이 서비스 인스턴스의 원하는 **이름을** 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-231">Insert your desired **Name** for this Service instance.</span></span>    

5.  <span data-ttu-id="04558-232">페이지 아래쪽에서 다음을 **클릭 합니다. 크기 및 크기**조정.</span><span class="sxs-lookup"><span data-stu-id="04558-232">On the bottom of the page click on **Next: Size and scale**.</span></span>

    ![저장소 인스턴스 만들기](images/AzureLabs-Lab313-12.png)

6.  <span data-ttu-id="04558-234">이 페이지에서 **가격 책정 및 크기 조정 계층** 을 선택 합니다 (첫 IoT Hub 서비스 인스턴스인 경우 무료 계층을 사용할 수 있어야 함).</span><span class="sxs-lookup"><span data-stu-id="04558-234">In this page, select your **Pricing and scale tier** (if this is your first IoT Hub Service instance, a free tier should be available to you).</span></span>  

7.  <span data-ttu-id="04558-235">**검토 + 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-235">Click on **Review + Create**.</span></span>

    ![저장소 인스턴스 만들기](images/AzureLabs-Lab313-13.png)

8.  <span data-ttu-id="04558-237">설정을 검토 하 고 **만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-237">Review your settings and click on **Create**.</span></span>

    ![저장소 인스턴스 만들기](images/AzureLabs-Lab313-14.png)

9. <span data-ttu-id="04558-239">*IoT Hub* 서비스가 성공적으로 생성 되었음을 알리는 알림이 표시 되 면 서비스로 이동 하 여 서비스로 리디렉션할 수 있습니다. 페이지로 **이동** 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-239">Once the notification pops up informing you of the successful creation of the *IoT Hub* Service, click on **Go to resource** to be redirected to your Service page.</span></span>

    ![저장소 인스턴스 만들기](images/AzureLabs-Lab313-15.png)

10. <span data-ttu-id="04558-241">*자동 장치 관리*가 표시 될 때까지 왼쪽 패널을 스크롤하여 **IoT Edge**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-241">Scroll the side panel on the left until you see *Automatic Device Management*, the click on **IoT Edge**.</span></span>

    ![저장소 인스턴스 만들기](images/AzureLabs-Lab313-16.png)

11. <span data-ttu-id="04558-243">오른쪽에 표시 되는 창에서 **IoT Edge 장치 추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-243">In the window that appears to the right, click on **Add IoT Edge Device**.</span></span> <span data-ttu-id="04558-244">블레이드가 오른쪽에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-244">A blade will appear to the right.</span></span>

12. <span data-ttu-id="04558-245">블레이드에서 새 장치에 **장치 ID** (선택한 이름)를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-245">In the blade, provide your new device a **Device ID** (a name of your choice).</span></span> <span data-ttu-id="04558-246">그런 다음 **저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-246">Then, click **Save**.</span></span> <span data-ttu-id="04558-247">선택 **자동 생성** 된 경우 *기본* 및 *보조 키* 가 자동으로 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-247">The *Primary* and *Secondary Keys* will auto generate, if you have **Auto Generate** ticked.</span></span>

    ![저장소 인스턴스 만들기](images/AzureLabs-Lab313-17.png)

13. <span data-ttu-id="04558-249">새 장치가 나열 되는 *IoT Edge 장치* 섹션으로 다시 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-249">You will navigate back to the *IoT Edge Devices* section, where your new device will be listed.</span></span> <span data-ttu-id="04558-250">새 장치를 클릭 합니다 (아래 이미지에서 빨간색으로 표시).</span><span class="sxs-lookup"><span data-stu-id="04558-250">Click on your new device (outlined in red in the below image).</span></span> 

    ![저장소 인스턴스 만들기](images/AzureLabs-Lab313-18.png)

14. <span data-ttu-id="04558-252">표시 되는 *장치 세부 정보* 페이지에서 **연결 문자열** (기본 키)의 복사본을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="04558-252">On the *Device Details* page that appears, take a copy of the **Connection String** (primary key).</span></span>

    ![저장소 인스턴스 만들기](images/AzureLabs-Lab313-19.png)

15. <span data-ttu-id="04558-254">왼쪽 패널로 돌아가 *공유 액세스 정책*을 클릭 하 여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="04558-254">Go back to the panel on the left, and click *Shared access policies*, to open it.</span></span> 

16. <span data-ttu-id="04558-255">표시 되는 페이지에서 **iothubowner**를 클릭 하면 화면 오른쪽에 블레이드가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-255">On the page that appears, click **iothubowner**, and a blade will appear to the right of the screen.</span></span> 

17. <span data-ttu-id="04558-256">연결 **문자열 (기본** 키)의 연결 문자열 (기본 키)을 기록해 둡니다. 나중에 장치에 대 한 *연결 문자열* 을 설정할 때 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-256">Take note (on your Notepad) of the **Connection string** (primary key), for later use when setting the *Connection String* to your device.</span></span>

    ![저장소 인스턴스 만들기](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a><span data-ttu-id="04558-258">4 장-개발 환경 설정</span><span class="sxs-lookup"><span data-stu-id="04558-258">Chapter 4 - Setting up the development environment</span></span>

<span data-ttu-id="04558-259">*IoT Hub Edge*에 대 한 모듈을 만들고 배포 하려면 Windows 10을 실행 하는 개발 컴퓨터에 다음 구성 요소가 설치 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-259">In order to create and deploy modules for *IoT Hub Edge*, you will require the following components installed on your development machine running Windows 10:</span></span>

1.  <span data-ttu-id="04558-260">[Windows용 Docker](https://store.docker.com/editions/community/docker-ce-desktop-windows)다운로드할 수 있는 계정을 만들도록 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-260">[Docker for Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows), it will ask you to create an account to be able to download.</span></span> 

    <span data-ttu-id="04558-261">[![windows 용 docker 다운로드](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)</span><span class="sxs-lookup"><span data-stu-id="04558-261">[![download docker for windows](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="04558-262">Docker를 실행 하려면 *windows 10 PRO*, *Enterprise 14393*또는 *windows Server 2016 RTM*이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-262">Docker requires *Windows 10 PRO*, *Enterprise 14393*, or *Windows Server 2016 RTM*, to run.</span></span> <span data-ttu-id="04558-263">다른 버전의 Windows 10을 실행 하는 경우 [Docker 도구 상자](https://docs.docker.com/toolbox/toolbox_install_windows/)를 사용 하 여 docker를 설치 해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-263">If you are running other versions of Windows 10, you can try installing Docker using the [Docker Toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/).</span></span>

2.  <span data-ttu-id="04558-264">[Python 3.6](https://www.python.org/downloads/).</span><span class="sxs-lookup"><span data-stu-id="04558-264">[Python 3.6](https://www.python.org/downloads/).</span></span>

    <span data-ttu-id="04558-265">[![python 3.6 다운로드](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)</span><span class="sxs-lookup"><span data-stu-id="04558-265">[![download python 3.6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)</span></span>

3.  <span data-ttu-id="04558-266">[Visual Studio Code (VS Code 라고도 함)](https://code.visualstudio.com/download).</span><span class="sxs-lookup"><span data-stu-id="04558-266">[Visual Studio Code (also known as VS Code)](https://code.visualstudio.com/download).</span></span>

    <span data-ttu-id="04558-267">[![다운로드 VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)</span><span class="sxs-lookup"><span data-stu-id="04558-267">[![download VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)</span></span>

<span data-ttu-id="04558-268">위에서 언급 한 소프트웨어를 설치한 후에는 컴퓨터를 다시 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-268">After installing the software mentioned above, you will need to restart your machine.</span></span>

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a><span data-ttu-id="04558-269">5 장-Ubuntu 환경 설정</span><span class="sxs-lookup"><span data-stu-id="04558-269">Chapter 5 - Setting up the Ubuntu environment</span></span>

<span data-ttu-id="04558-270">이제 **UBUNTU OS를 실행**하는 장치 설정으로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-270">Now you can move on to setting up your device **running Ubuntu OS**.</span></span> <span data-ttu-id="04558-271">아래 단계에 따라 필요한 소프트웨어를 설치 하 고 보드에 컨테이너를 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-271">Follow the steps below, to install the necessary software, to deploy your containers on your board:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="04558-272">관리 사용자로 실행 하려면 항상 **sudo** 를 사용 하 여 터미널 명령 앞에와 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-272">You should always precede the terminal commands with **sudo** to run as admin user.</span></span> <span data-ttu-id="04558-273">핵</span><span class="sxs-lookup"><span data-stu-id="04558-273">i.e:</span></span>
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  <span data-ttu-id="04558-274">**Ubuntu 터미널**을 열고 다음 명령을 사용 하 여 **pip**를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-274">Open the **Ubuntu Terminal**, and use the following command to install **pip**:</span></span>

    > [! 힌트]<span data-ttu-id="04558-275"> 바로 가기 키를 사용 하 여 *터미널* 을 매우 쉽게 열 수 있습니다. **Ctrl + Alt + T**</span><span class="sxs-lookup"><span data-stu-id="04558-275"> You can open *Terminal* very easily through using the keyboard shortcut: **Ctrl + Alt + T**.</span></span>

    ```bash
        sudo apt-get install python-pip
    ```

2.  <span data-ttu-id="04558-276">이 장에서는 *터미널*에서 장치 저장소를 사용할 수 있는 권한을 묻는 메시지가 표시 될 수 있으며 **y/n** (예 또는 아니요)을 입력 하 고 **enter** 키를 눌러 수락 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-276">Throughout this Chapter, you may be prompted, by *Terminal*, for permission to use your device storage, and for you to input **y/n** (yes or no), type **'y'**, and then press the **Enter** key, to accept.</span></span>

3.  <span data-ttu-id="04558-277">명령이 완료 되 면 다음 명령을 사용 하 여 **말아 넘기기**를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-277">Once that command has completed, use the following command to install **curl**:</span></span>

    ```bash
        sudo apt install curl
    ```

4.  <span data-ttu-id="04558-278">**Pip** 및 **말아** 가 설치 되 면 다음 명령을 사용 하 여 **IoT Edge 런타임을**설치 합니다 .이는 보드의 모듈을 배포 하 고 제어 하는 데 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-278">Once **pip** and **curl** are installed, use the following command to install the **IoT Edge runtime**, this is necessary to deploy and control the modules on your board:</span></span>

    ```bash
        curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > ./microsoft-prod.list

        sudo cp ./microsoft-prod.list /etc/apt/sources.list.d/

        curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg

        sudo cp ./microsoft.gpg /etc/apt/trusted.gpg.d/

        sudo apt-get update

        sudo apt-get install moby-engine

        sudo apt-get install moby-cli

        sudo apt-get update

        sudo apt-get install iotedge
    ```

5. <span data-ttu-id="04558-279">이 시점에서 *런타임 구성 파일*을 열고, (메모장에서) **IoT Hub 서비스** 를 만들 때 ([13 장의 3 단계](#chapter-3---the-iot-hub-service))에 적어 둔 **장치 연결 문자열**을 삽입 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-279">At this point you will be prompted to open up the *runtime config file*, to insert the **Device Connection String**, that you noted down (in your Notepad), when creating the **IoT Hub Service** ([at step 14, of Chapter 3](#chapter-3---the-iot-hub-service)).</span></span> <span data-ttu-id="04558-280">터미널에서 다음 줄을 실행 하 여 해당 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="04558-280">Run the following line on the terminal to open that file:</span></span>

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. <span data-ttu-id="04558-281">다음과 같이 편집할 준비가 된 **config.xml** 파일이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-281">The **config.yaml** file will be displayed, ready for you to edit:</span></span>

    > [!WARNING]
    > <span data-ttu-id="04558-282">이 파일이 열리면 약간 혼란 스 러 울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-282">When this file opens, it may be somewhat confusing.</span></span> <span data-ttu-id="04558-283">*터미널* 자체 내에서이 파일을 편집 하는 텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="04558-283">You will be text editing this file, within the *Terminal* itself.</span></span> 

    1.  <span data-ttu-id="04558-284">키보드의 화살표 키를 사용 하 여 아래로 스크롤합니다 (약간 아래로 스크롤해야 하는 경우).</span><span class="sxs-lookup"><span data-stu-id="04558-284">Use the arrow keys on your keyboard to scroll down (you will need to scroll down a little way), to reach the line containing":</span></span>

        <span data-ttu-id="04558-285">**"\<여기 > 장치 연결 문자열을 추가**합니다."</span><span class="sxs-lookup"><span data-stu-id="04558-285">"**\<ADD DEVICE CONNECTION STRING HERE>**".</span></span>

    2. <span data-ttu-id="04558-286">**괄호를 포함**한 줄을 앞에서 설명한 **장치 연결 문자열로** 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-286">Substitute line, **including the brackets**, with the **Device Connection String** you have noted earlier.</span></span>

7. <span data-ttu-id="04558-287">연결 문자열을 입력 하 고 키보드에서 **Ctrl + X** 키를 눌러 파일을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-287">With your Connection String in place, on your keyboard, press the **Ctrl-X** keys to save the file.</span></span> <span data-ttu-id="04558-288">**Y**를 입력 하 여 확인 하 라는 메시지를 표시 합니다. 그런 다음 **enter** 키를 눌러 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-288">It will ask you to confirm by typing **Y**. Then, press the **Enter** key, to confirm.</span></span> <span data-ttu-id="04558-289">그러면 일반 *터미널*로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="04558-289">You will go back to the regular *Terminal*.</span></span> 

8. <span data-ttu-id="04558-290">이러한 명령이 모두 성공적으로 실행 되 면 **IoT Edge 런타임을**설치 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-290">Once these commands have all run successfully, you will have installed the **IoT Edge Runtime**.</span></span> <span data-ttu-id="04558-291">초기화 된 후에는 장치가 전원이 공급 될 때마다 런타임이 자체에서 시작 되 고, 백그라운드에서 제공 되어 **IoT Hub 서비스**에서 모듈이 배포 될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="04558-291">Once initialized, the runtime will start on its own every time the device is powered up, and will sit in the background, waiting for modules to be deployed from the **IoT Hub Service**.</span></span>

9.  <span data-ttu-id="04558-292">다음 명령줄을 실행 하 여 *IoT Edge 런타임을*초기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-292">Run the following command line to initialize the *IoT Edge Runtime*:</span></span>

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="04558-293">.Yaml 파일 또는 위의 설정을 변경 하는 경우에는 *터미널*내에서 위의 다시 시작 줄을 다시 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-293">If you make changes to your .yaml file, or the above setup, you will need to run the above restart line again, within *Terminal*.</span></span>

10. <span data-ttu-id="04558-294">다음 명령줄을 실행 하 여 *IoT Edge 런타임* 상태를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-294">Check the *IoT Edge Runtime* status by running the following command line.</span></span> <span data-ttu-id="04558-295">런타임이 녹색 텍스트로 **활성 (실행 중)** 상태로 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-295">The runtime should appear with the status **active (running)** in green text.</span></span>

    ```bash
        sudo systemctl status iotedge
    ```

11. <span data-ttu-id="04558-296">Ctrl + **C** 키를 눌러 상태 페이지를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-296">Press the **Ctrl-C** keys, to exit the status page.</span></span> <span data-ttu-id="04558-297">다음 명령을 입력 하 여 *IoT Edge 런타임이* 컨테이너를 올바르게 풀링 하 고 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-297">You can verify that the *IoT Edge Runtime* is pulling the containers correctly by typing the following command:</span></span>

    ```bash
        sudo docker ps
    ```

12. <span data-ttu-id="04558-298">두 개의 (2) 컨테이너가 있는 목록이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-298">A list with two (2) containers should appear.</span></span> <span data-ttu-id="04558-299">이러한 모듈은 IoT Hub 서비스 (edgeAgent 및 edgeHub)에 의해 자동으로 생성 되는 기본 모듈입니다.</span><span class="sxs-lookup"><span data-stu-id="04558-299">These are the default modules that are automatically created by the IoT Hub Service (edgeAgent and edgeHub).</span></span> <span data-ttu-id="04558-300">사용자 고유의 모듈을 만들고 배포 하면이 목록에서 기본 모듈 아래에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-300">Once you create and deploy your own modules, they will appear in this list, underneath the default ones.</span></span>

## <a name="chapter-6---install-the-extensions"></a><span data-ttu-id="04558-301">6 장-확장 설치</span><span class="sxs-lookup"><span data-stu-id="04558-301">Chapter 6 - Install the extensions</span></span>

> [!IMPORTANT]
> <span data-ttu-id="04558-302">다음 몇 장 (6-9)은 Windows 10 컴퓨터에서 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-302">The next few Chapters (6-9) are to be performed on your Windows 10 machine.</span></span>

1. <span data-ttu-id="04558-303">**VS Code**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="04558-303">Open **VS Code**.</span></span>

2. <span data-ttu-id="04558-304">VS Code 왼쪽 막대에서 **확장** (정사각형) 단추를 클릭 하 여 **확장 패널**을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="04558-304">Click on the **Extensions** (square) button on the left bar of VS Code, to open the **Extensions panel**.</span></span>

3. <span data-ttu-id="04558-305">아래 이미지에 표시 된 것 처럼 다음 확장을 검색 하 고 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-305">Search for, and install, the following extensions (as shown in the image below):</span></span>

    1. <span data-ttu-id="04558-306">Azure IoT Edge</span><span class="sxs-lookup"><span data-stu-id="04558-306">Azure IoT Edge</span></span>
    2. <span data-ttu-id="04558-307">Azure IoT 도구 키트</span><span class="sxs-lookup"><span data-stu-id="04558-307">Azure IoT Toolkit</span></span>
    3. <span data-ttu-id="04558-308">Docker</span><span class="sxs-lookup"><span data-stu-id="04558-308">Docker</span></span>   

    ![컨테이너 만들기](images/AzureLabs-Lab313-24.png)

4. <span data-ttu-id="04558-310">확장이 설치 되 면 VS Code를 닫았다가 다시 엽니다.</span><span class="sxs-lookup"><span data-stu-id="04558-310">Once the extensions are installed, close and re-open VS Code.</span></span>

5. <span data-ttu-id="04558-311">VS Code를 한 번 더 열면**통합 터미널** **보기** > 로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-311">With VS Code open once more, navigate to **View** > **Integrated terminal**.</span></span>

6. <span data-ttu-id="04558-312">이제 **Cookiecutter**를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-312">You will now install **Cookiecutter**.</span></span> <span data-ttu-id="04558-313">터미널에서 다음 bash 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-313">In the terminal run the following bash command:</span></span>

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > [! 힌트]<span data-ttu-id="04558-314"> 명령을 사용 하는 데 문제가 있는 경우:</span><span class="sxs-lookup"><span data-stu-id="04558-314"> If you have trouble with this command:</span></span> 
    >1. <span data-ttu-id="04558-315">VS Code 및/또는 컴퓨터를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-315">Restart VS Code, and/ or your computer.</span></span>
    >2. <span data-ttu-id="04558-316">Python을 설치 하는 데 사용 하는 것으로 **VS Code 터미널** 을 전환 해야 할 수도 **있습니다. 즉** , 특히 python 환경이 컴퓨터에 이미 설치 되어 있는 경우에 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-316">It might be necessary to switch the **VS Code Terminal** to the one you have been using to install Python, i.e. **Powershell** (especially in case the Python environment was already installed on your machine).</span></span> <span data-ttu-id="04558-317">터미널이 열리면 터미널의 오른쪽에 있는 드롭다운 메뉴를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-317">With the Terminal open, you will find the drop down menu on the right side of the Terminal.</span></span>
     <span data-ttu-id="04558-318">![컨테이너 만들기](images/AzureLabs-Lab313-24b.png)</span><span class="sxs-lookup"><span data-stu-id="04558-318">![Create your container](images/AzureLabs-Lab313-24b.png)</span></span> 
    >3. <span data-ttu-id="04558-319">**Python** 설치 경로가 컴퓨터에 **환경 변수로** 추가 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-319">Make sure the **Python** installation path is added as **Environment Variable** on your machine.</span></span> <span data-ttu-id="04558-320">Cookiecutter는 동일한 위치 경로의 일부 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-320">Cookiecutter should be part of the same location path.</span></span> <span data-ttu-id="04558-321">[환경 변수에 대 한 자세한 내용은 다음 링크](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="04558-321">Please follow this [link for more information on Environment Variables](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx),</span></span> 

7. <span data-ttu-id="04558-322">**Cookiecutter** 설치가 완료 되 면 시스템 환경 내에서 **Cookiecutter** 가 명령으로 인식 되도록 컴퓨터를 다시 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-322">Once **Cookiecutter** has finished installing, you should restart your machine, so that **Cookiecutter** is recognized as a command, within your System's environment.</span></span>

## <a name="chapter-7---create-your-container-solution"></a><span data-ttu-id="04558-323">7 장-컨테이너 솔루션 만들기</span><span class="sxs-lookup"><span data-stu-id="04558-323">Chapter 7 - Create your container solution</span></span>

<span data-ttu-id="04558-324">이 시점에서 모듈을 사용 하 여 *Container Registry*에 푸시할 컨테이너를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-324">At this point, you need to create the container, with the module, to be pushed into the *Container Registry*.</span></span> <span data-ttu-id="04558-325">컨테이너를 푸시한 후에는 *IoT Hub Edge* 서비스를 사용 하 여 *IoT Edge 런타임을*실행 하는 장치에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-325">Once you have pushed your container, you will use the *IoT Hub Edge* Service to deploy it to your device, which is running the *IoT Edge runtime*.</span></span>

1. <span data-ttu-id="04558-326">VS Code에서 **보기** > **명령 팔레트**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-326">From VS Code, click **View** > **Command palette**.</span></span>

2. <span data-ttu-id="04558-327">색상표에서 Azure IoT Edge 검색 하 고 실행 **합니다. 새 Iot Edge 솔루션**.</span><span class="sxs-lookup"><span data-stu-id="04558-327">In the palette, search and run **Azure IoT Edge: New Iot Edge Solution**.</span></span>

3. <span data-ttu-id="04558-328">솔루션을 만들려는 위치로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-328">Browse into a location where you want to create your solution.</span></span> <span data-ttu-id="04558-329">**Enter** 키를 눌러 위치를 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-329">Press the **Enter** key, to accept the location.</span></span>

4. <span data-ttu-id="04558-330">솔루션에 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-330">Give a name to your solution.</span></span> <span data-ttu-id="04558-331">**Enter** 키를 눌러 제공 된 이름을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-331">Press the **Enter** key, to confirm your provided name.</span></span>

5. <span data-ttu-id="04558-332">이제 솔루션에 대 한 템플릿 프레임 워크를 선택 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-332">Now you will be prompted to choose the template framework for your solution.</span></span> <span data-ttu-id="04558-333">**Python 모듈**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-333">Click **Python Module**.</span></span> <span data-ttu-id="04558-334">**Enter** 키를 눌러이 선택을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-334">Press the **Enter** key, to confirm this choice.</span></span>

6. <span data-ttu-id="04558-335">모듈에 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-335">Give a name to your module.</span></span> <span data-ttu-id="04558-336">**Enter** 키를 눌러 모듈의 이름을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-336">Press the **Enter** key, to confirm the name of your module.</span></span> <span data-ttu-id="04558-337">나중에 사용 되므로 모듈 이름에 대해 메모장을 사용 하 여 메모를 작성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-337">Make sure to take a note (with your Notepad) of the module name, as it is used later.</span></span>

7. <span data-ttu-id="04558-338">미리 빌드된 *Docker 이미지 리포지토리* 주소가 색상표에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-338">You will notice a pre-built *Docker Image Repository* address will appear on the palette.</span></span> <span data-ttu-id="04558-339">다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-339">It will look like:</span></span>

    <span data-ttu-id="04558-340">**localhost: 5000/-모듈의 이름-** .</span><span class="sxs-lookup"><span data-stu-id="04558-340">**localhost:5000/-THE NAME OF YOUR MODULE-**.</span></span> 

8. <span data-ttu-id="04558-341">**Localhost: 5000**을 삭제 하 고 해당 위치에서 **Container Registry 서비스** 를 만들 때 기록한 *Container Registry* **로그인 서버** 주소 ([2 장의 8 단계](#chapter-2---the-container-registry-service))를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-341">Delete **localhost:5000**, and in its place insert the *Container Registry* **Login Server** address, which you noted when creating the **Container Registry Service** ([in step 8, of Chapter 2](#chapter-2---the-container-registry-service)).</span></span> <span data-ttu-id="04558-342">**Enter** 키를 눌러 주소를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-342">Press the **Enter** key, to confirm the address.</span></span>

9. <span data-ttu-id="04558-343">이 시점에서 Python 모듈에 대 한 템플릿이 포함 된 솔루션이 만들어지고 해당 구조가 화면 왼쪽에 있는 VS Code의 **탐색 탭**에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-343">At this point, the solution containing the template for your Python module will be created and its structure will be displayed in the **Explore Tab**, of VS Code, on the left side of the screen.</span></span> <span data-ttu-id="04558-344">**탐색 탭** 이 열려 있지 않으면 왼쪽 표시줄에서 맨 위에 있는 단추를 클릭 하 여 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-344">If the **Explore Tab** is not open, you can open it by clicking the top-most button, in the bar on the left.</span></span>

    ![컨테이너 만들기](images/AzureLabs-Lab313-25.png)

10. <span data-ttu-id="04558-346">이 챕터의 마지막 단계에서는 **탐색 탭**내에서 **env 파일**을 클릭 하 여 열고 *Container Registry* **사용자 이름** 및 **암호**를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-346">The last step for this Chapter, is to click and open the **.env file**, from within the **Explore Tab**, and add your *Container Registry* **username** and **password**.</span></span> <span data-ttu-id="04558-347">이 파일은 git에서 무시 되지만 컨테이너를 빌드하는 동안 **Container Registry 서비스**에 액세스 하기 위한 자격 증명을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-347">This file is ignored by git, but on building the container, will set the credentials to access the **Container Registry Service**.</span></span>

    ![컨테이너 만들기](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a><span data-ttu-id="04558-349">8 장-컨테이너 솔루션 편집</span><span class="sxs-lookup"><span data-stu-id="04558-349">Chapter 8 - Editing your container solution</span></span>

<span data-ttu-id="04558-350">이제 다음 파일을 업데이트 하 여 컨테이너 솔루션을 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-350">You will now complete the container solution, by updating the following files:</span></span>

- <span data-ttu-id="04558-351">py python 스크립트입니다. *<span></span>*</span><span class="sxs-lookup"><span data-stu-id="04558-351">*main<span></span>.py* python script.</span></span>
- <span data-ttu-id="04558-352">*요구 사항 .txt*.</span><span class="sxs-lookup"><span data-stu-id="04558-352">*requirements.txt*.</span></span>
- <span data-ttu-id="04558-353">*배포. 템플릿. json*.</span><span class="sxs-lookup"><span data-stu-id="04558-353">*deployment.template.json*.</span></span>
- <span data-ttu-id="04558-354">*Dockerfile. amd64*</span><span class="sxs-lookup"><span data-stu-id="04558-354">*Dockerfile.amd64*</span></span>

<span data-ttu-id="04558-355">그런 다음 python 스크립트에서 *Custom Vision 모델*에 대해 일치 시킬 이미지를 확인 하는 데 사용 하는 *images* 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="04558-355">You will then create the *images* folder, used by the python script to check for images to match against your *Custom Vision model*.</span></span> <span data-ttu-id="04558-356">마지막으로, 모델을 읽는 데 도움이 되는 *레이블과* 사용자 모델인 *모델인 파일을* 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-356">Lastly, you will add the *labels.txt* file, to help read your model, and the *model.pb* file, which is your model.</span></span>

1. <span data-ttu-id="04558-357">VS Code 열린 상태에서 모듈 폴더로 이동 하 고 **py<span></span>** 라는 스크립트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-357">With VS Code open, navigate to your module folder, and look for the script called **main<span></span>.py**.</span></span> <span data-ttu-id="04558-358">두 번 클릭 하 여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="04558-358">Double-click to open it.</span></span>

2. <span data-ttu-id="04558-359">파일의 내용을 삭제 하 고 다음 코드를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-359">Delete the content of the file and insert the following code:</span></span>

    ```python
    # Copyright (c) Microsoft. All rights reserved.
    # Licensed under the MIT license. See LICENSE file in the project root for
    # full license information.

    import random
    import sched, time
    import sys
    import iothub_client
    from iothub_client import IoTHubModuleClient, IoTHubClientError, IoTHubTransportProvider
    from iothub_client import IoTHubMessage, IoTHubMessageDispositionResult, IoTHubError
    import json
    import os
    import tensorflow as tf
    import os
    from PIL import Image
    import numpy as np
    import cv2

    # messageTimeout - the maximum time in milliseconds until a message times out.
    # The timeout period starts at IoTHubModuleClient.send_event_async.
    # By default, messages do not expire.
    MESSAGE_TIMEOUT = 10000

    # global counters
    RECEIVE_CALLBACKS = 0
    SEND_CALLBACKS = 0

    TEMPERATURE_THRESHOLD = 25
    TWIN_CALLBACKS = 0

    # Choose HTTP, AMQP or MQTT as transport protocol.  Currently only MQTT is supported.
    PROTOCOL = IoTHubTransportProvider.MQTT


    # Callback received when the message that we're forwarding is processed.
    def send_confirmation_callback(message, result, user_context):
        global SEND_CALLBACKS
        print ( "Confirmation[%d] received for message with result = %s" % (user_context, result) )
        map_properties = message.properties()
        key_value_pair = map_properties.get_internals()
        print ( "    Properties: %s" % key_value_pair )
        SEND_CALLBACKS += 1
        print ( "    Total calls confirmed: %d" % SEND_CALLBACKS )


    def convert_to_opencv(image):
        # RGB -> BGR conversion is performed as well.
        r,g,b = np.array(image).T
        opencv_image = np.array([b,g,r]).transpose()
        return opencv_image

    def crop_center(img,cropx,cropy):
        h, w = img.shape[:2]
        startx = w//2-(cropx//2)
        starty = h//2-(cropy//2)
        return img[starty:starty+cropy, startx:startx+cropx]

    def resize_down_to_1600_max_dim(image):
        h, w = image.shape[:2]
        if (h < 1600 and w < 1600):
            return image

        new_size = (1600 * w // h, 1600) if (h > w) else (1600, 1600 * h // w)
        return cv2.resize(image, new_size, interpolation = cv2.INTER_LINEAR)

    def resize_to_256_square(image):
        h, w = image.shape[:2]
        return cv2.resize(image, (256, 256), interpolation = cv2.INTER_LINEAR)

    def update_orientation(image):
        exif_orientation_tag = 0x0112
        if hasattr(image, '_getexif'):
            exif = image._getexif()
            if (exif != None and exif_orientation_tag in exif):
                orientation = exif.get(exif_orientation_tag, 1)
                # orientation is 1 based, shift to zero based and flip/transpose based on 0-based values
                orientation -= 1
                if orientation >= 4:
                    image = image.transpose(Image.TRANSPOSE)
                if orientation == 2 or orientation == 3 or orientation == 6 or orientation == 7:
                    image = image.transpose(Image.FLIP_TOP_BOTTOM)
                if orientation == 1 or orientation == 2 or orientation == 5 or orientation == 6:
                    image = image.transpose(Image.FLIP_LEFT_RIGHT)
        return image


    def analyse(hubManager):

        messages_sent = 0;

        while True:
            #def send_message():
            print ("Load the model into the project")
            # These names are part of the model and cannot be changed.
            output_layer = 'loss:0'
            input_node = 'Placeholder:0'

            graph_def = tf.GraphDef()
            labels = []

            labels_filename = "labels.txt"
            filename = "model.pb"

            # Import the TF graph
            with tf.gfile.FastGFile(filename, 'rb') as f:
                graph_def.ParseFromString(f.read())
                tf.import_graph_def(graph_def, name='')

            # Create a list of labels
            with open(labels_filename, 'rt') as lf:
                for l in lf:
                    labels.append(l.strip())
            print ("Model loaded into the project")

            results_dic = dict()

            # create the JSON to be sent as a message
            json_message = ''

            # Iterate through images 
            print ("List of images to analyse:")
            for file in os.listdir('images'):
                print(file)

                image = Image.open("images/" + file)

                # Update orientation based on EXIF tags, if the file has orientation info.
                image = update_orientation(image)

                # Convert to OpenCV format
                image = convert_to_opencv(image)

                # If the image has either w or h greater than 1600 we resize it down respecting
                # aspect ratio such that the largest dimension is 1600
                image = resize_down_to_1600_max_dim(image)

                # We next get the largest center square
                h, w = image.shape[:2]
                min_dim = min(w,h)
                max_square_image = crop_center(image, min_dim, min_dim)

                # Resize that square down to 256x256
                augmented_image = resize_to_256_square(max_square_image)

                # The compact models have a network size of 227x227, the model requires this size.
                network_input_size = 227

                # Crop the center for the specified network_input_Size
                augmented_image = crop_center(augmented_image, network_input_size, network_input_size)

                try:
                    with tf.Session() as sess:     
                        prob_tensor = sess.graph.get_tensor_by_name(output_layer)
                        predictions, = sess.run(prob_tensor, {input_node: [augmented_image] })
                except Exception as identifier:
                    print ("Identifier error: ", identifier)

                print ("Print the highest probability label")
                highest_probability_index = np.argmax(predictions)
                print('FINAL RESULT! Classified as: ' + labels[highest_probability_index])

                l = labels[highest_probability_index]

                results_dic[file] = l

                # Or you can print out all of the results mapping labels to probabilities.
                label_index = 0
                for p in predictions:
                    truncated_probablity = np.float64(round(p,8))
                    print (labels[label_index], truncated_probablity)
                    label_index += 1

            print("Results dictionary")
            print(results_dic)

            json_message = json.dumps(results_dic)
            print("Json result")
            print(json_message)

            # Initialize a new message
            message = IoTHubMessage(bytearray(json_message, 'utf8'))
        
            hubManager.send_event_to_output("output1", message, 0)

            messages_sent += 1
            print("Message sent! - Total: " + str(messages_sent))      
            print('----------------------------')
            
            # This is the wait time before repeating the analysis
            # Currently set to 10 seconds
            time.sleep(10)


    class HubManager(object):
        
        def __init__(
                self,
                protocol=IoTHubTransportProvider.MQTT):
            self.client_protocol = protocol
            self.client = IoTHubModuleClient()
            self.client.create_from_environment(protocol)

            # set the time until a message times out
            self.client.set_option("messageTimeout", MESSAGE_TIMEOUT)

        # Forwards the message received onto the next stage in the process.
        def forward_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(
                outputQueueName, event, send_confirmation_callback, send_context)

        def send_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(outputQueueName, event, send_confirmation_callback, send_context)

    def main(protocol):
        try:
            hub_manager = HubManager(protocol)
            analyse(hub_manager)
            while True:
                time.sleep(1)

        except IoTHubError as iothub_error:
            print ( "Unexpected error %s from IoTHub" % iothub_error )
            return
        except KeyboardInterrupt:
            print ( "IoTHubModuleClient sample stopped" )

    if __name__ == '__main__':
        main(PROTOCOL)
    ```

3.  <span data-ttu-id="04558-360">**요구 사항 .txt**라는 파일을 열고 해당 콘텐츠를 다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="04558-360">Open the file called **requirements.txt**, and substitute its content with the following:</span></span>

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  <span data-ttu-id="04558-361">다음 지침에 따라 **deployment. template. json**파일을 열고 해당 콘텐츠를 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-361">Open the file called **deployment.template.json**, and substitute its content following the below guideline:</span></span>

    1. <span data-ttu-id="04558-362">고유 하 고 고유한 JSON 구조가 있으므로 예제를 복사 하는 대신 직접 편집 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-362">Because you will have your own, unique, JSON structure, you will need to edit it by hand (rather than copying an example).</span></span> <span data-ttu-id="04558-363">이 작업을 쉽게 하려면 아래 이미지를 가이드로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-363">To make this easy, use the below image as a guide.</span></span>
    2. <span data-ttu-id="04558-364">사용자와 다르게 보이지만 **변경 하지 않아야**하는 영역이 노란색으로 강조 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-364">Areas which will look different to yours, but which you **should NOT change are highlighted yellow**.</span></span>
    3. <span data-ttu-id="04558-365">**삭제 해야 하는 섹션은 빨간색으로 강조 표시 됩니다.**</span><span class="sxs-lookup"><span data-stu-id="04558-365">**Sections which you need to delete, are a highlighted red.**</span></span>
    4. <span data-ttu-id="04558-366">올바른 대괄호를 삭제 하 고 쉼표도 제거 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-366">Be careful to delete the correct brackets, and also remove the commas.</span></span>

        ![컨테이너 만들기](images/AzureLabs-Lab313-27.png)

    5. <span data-ttu-id="04558-368">완성 된 JSON은 다음 이미지와 같이 표시 되어야 합니다. 단, *사용자 이름/암호/모듈 이름/모듈 참조*와 같은 고유한 차이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-368">The completed JSON should look like the following image (though, with your unique differences: *username/password/module name/module references*):</span></span>

        ![컨테이너 만들기](images/AzureLabs-Lab313-28.png)

5.  <span data-ttu-id="04558-370">**Dockerfile. amd64**라는 파일을 열고 콘텐츠를 다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="04558-370">Open the file called **Dockerfile.amd64**, and substitute its content with the following:</span></span>

    ```
    FROM ubuntu:xenial

    WORKDIR /app

    RUN apt-get update && \
        apt-get install -y --no-install-recommends libcurl4-openssl-dev python-pip libboost-python-dev && \
        rm -rf /var/lib/apt/lists/* 
    RUN pip install --upgrade pip
    RUN pip install setuptools

    COPY requirements.txt ./
    RUN pip install -r requirements.txt

    RUN pip install pillow
    RUN pip install numpy

    RUN apt-get update && apt-get install -y \ 
        pkg-config \
        python-dev \ 
        python-opencv \ 
        libopencv-dev \ 
        libav-tools  \ 
        libjpeg-dev \ 
        libpng-dev \ 
        libtiff-dev \ 
        libjasper-dev \ 
        python-numpy \ 
        python-pycurl \ 
        python-opencv


    RUN pip install opencv-python
    RUN pip install tensorflow
    RUN pip install --upgrade tensorflow

    COPY . .

    RUN useradd -ms /bin/bash moduleuser
    USER moduleuser

    CMD [ "python", "-u", "./main.py" ]

    ```

6.  <span data-ttu-id="04558-371">**모듈** 아래에 있는 폴더를 마우스 오른쪽 단추로 클릭 하 고 (이전에 입력 한 이름을 포함 합니다. 아래 예제에서는 *pythonmodule*라고 함) **새 폴더**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-371">Right-click on the folder beneath **modules** (it will have the name you provided previously; in the example further down, it is called *pythonmodule*), and click on **New Folder**.</span></span> <span data-ttu-id="04558-372">폴더 이름을 **images**로 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-372">Name the folder **images**.</span></span>

7.  <span data-ttu-id="04558-373">폴더 안에 마우스나 키보드를 포함 하는 일부 이미지를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-373">Inside the folder, add some images containing mouse or keyboard.</span></span> <span data-ttu-id="04558-374">이러한 이미지는 Tensorflow 모델에서 분석할 이미지가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-374">Those will be the images that will be analyzed by the Tensorflow model.</span></span>

    > [!WARNING]
    > <span data-ttu-id="04558-375">사용자 고유의 모델을 사용 하는 경우 고유한 모델 데이터를 반영 하도록이를 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-375">If you are using your own model, you will need to change this to reflect your own models data.</span></span>

8.  <span data-ttu-id="04558-376">이제 [1 장](#chapter-1---retrieve-the-custom-vision-model)에서 이전에 다운로드 했거나 사용자 고유의 **Custom Vision Service**에서 만든 model 폴더에서 **레이블도** 및 **모델인** 파일을 검색 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-376">You will now need to retrieve the **labels.txt** and **model.pb** files from the model folder, which you previous downloaded (or created from your own **Custom Vision Service**), in [Chapter 1](#chapter-1---retrieve-the-custom-vision-model).</span></span> <span data-ttu-id="04558-377">파일이 있으면 다른 파일과 함께 솔루션 내에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-377">Once you have the files, place them within your solution, alongside the other files.</span></span> <span data-ttu-id="04558-378">최종 결과는 아래 이미지와 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-378">The final result should look like the image below:</span></span>

    ![컨테이너 만들기](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a><span data-ttu-id="04558-380">9 장-솔루션을 컨테이너로 패키지</span><span class="sxs-lookup"><span data-stu-id="04558-380">Chapter 9 - Package the solution as a container</span></span>

1.  <span data-ttu-id="04558-381">이제 파일을 컨테이너로 "패키지" 하 고 **Azure Container Registry**에 푸시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-381">You are now ready to "package" your files as a container and push it to your **Azure Container Registry**.</span></span> <span data-ttu-id="04558-382">VS Code 내에서 *통합 터미널* (**View** >  **\`** **integrated terminal** 또는 **Ctrl**+)을 열고 다음 줄을 사용 하 여 **Docker** 에 로그인 합니다 (다음의 값으로 대체 합니다. Azure Container Registry 자격 증명을 사용 하는 명령 **(ACR)** :</span><span class="sxs-lookup"><span data-stu-id="04558-382">Within VS Code, open the *Integrated Terminal* (**View** > **Integrated Terminal** or **Ctrl**+**\`**), and use the following line to login to **Docker** (substitute the values of the command with the credentials of your **Azure Container Registry (ACR)**):</span></span>

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. <span data-ttu-id="04558-383">파일 **배포. 템플릿**을 마우스 오른쪽 단추로 클릭 하 고 **IoT Edge 솔루션 빌드**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-383">Right-click on the file **deployment.template.json**, and click **Build IoT Edge Solution**.</span></span> <span data-ttu-id="04558-384">이 빌드 프로세스는 장치에 따라 상당한 시간이 걸리므로 대기할 준비가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-384">This build process takes quite some time (depending on your device), so be prepared to wait.</span></span> <span data-ttu-id="04558-385">빌드 프로세스가 완료 된 후에는 **deployment. json** 파일이 **config**라는 새 폴더 내에 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-385">After the build process finishes, a **deployment.json** file will have been created inside a new folder called **config**.</span></span>

    ![배포 만들기](images/AzureLabs-Lab313-30.png)

3. <span data-ttu-id="04558-387">**명령 팔레트** 를 다시 열고 Azure를 **검색 합니다.** 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-387">Open the **Command Palette** again, and search for **Azure: Sign In**.</span></span> <span data-ttu-id="04558-388">Azure 계정 자격 증명을 사용 하 여 프롬프트를 따릅니다. VS Code은 복사 하 여 *열*수 있는 옵션을 제공 합니다 .이 옵션을 사용 하면 곧 필요한 장치 코드를 복사 하 여 기본 웹 브라우저를 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-388">Follow the prompts using your Azure Account credentials; VS Code will provide you with an option to *Copy and Open*, which will copy the device code you will soon need, and open your default web browser.</span></span> <span data-ttu-id="04558-389">메시지가 표시 되 면 장치 코드를 붙여넣어 컴퓨터를 인증 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-389">When asked, paste the device code, to authenticate your machine.</span></span>

    ![복사 및 열기](images/AzureLabs-Lab313-31.png)

4. <span data-ttu-id="04558-391">일단 로그인 하면 *탐색* 패널의 아래쪽에 **Azure IoT Hub 장치**라는 새 섹션이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-391">Once signed in you will notice, on the bottom side of the *Explore* panel, a new section called **Azure IoT Hub Devices**.</span></span> <span data-ttu-id="04558-392">이 섹션을 클릭 하 여 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-392">Click this section to expand it.</span></span>

    ![edge 장치](images/AzureLabs-Lab313-32.png)

5. <span data-ttu-id="04558-394">장치를 사용할 수 없는 경우 *Azure IoT Hub 장치*를 마우스 오른쪽 단추로 클릭 한 다음 **IoT Hub 연결 문자열 설정**을 클릭 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-394">If your device is not here, you will need to right-click *Azure IoT Hub Devices*, and then click **Set IoT Hub Connection String**.</span></span> <span data-ttu-id="04558-395">그러면 **명령 팔레트** (VS Code 위쪽)에 *연결 문자열*을 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-395">You will then see that the **Command Palette** (at the top of VS Code), will prompt you to input your *Connection String*.</span></span> <span data-ttu-id="04558-396">[3 장](#chapter-3---the-iot-hub-service)끝에 적어 둔 *연결 문자열* 입니다.</span><span class="sxs-lookup"><span data-stu-id="04558-396">This is the *Connection String* you noted down at the end of [Chapter 3](#chapter-3---the-iot-hub-service).</span></span> <span data-ttu-id="04558-397">에서 문자열을 복사한 후 **enter** 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="04558-397">Press the **Enter** key, once you have copied the string in.</span></span>    

6. <span data-ttu-id="04558-398">장치가 로드 되 고 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-398">Your device should load, and appear.</span></span> <span data-ttu-id="04558-399">장치 이름을 마우스 오른쪽 단추로 클릭 한 다음 **단일 장치에 대 한 배포 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-399">Right-click on the device name, and then click, **Create Deployment for Single Device**.</span></span>

    ![배포 만들기](images/AzureLabs-Lab313-33b.png)

7. <span data-ttu-id="04558-401">**구성** 폴더로 이동한 다음, **배포. json** 파일을 선택 하 여 *파일 탐색기* 프롬프트가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-401">You will get a *File Explorer* prompt, where you can navigate to the **config** folder, and then select the **deployment.json** file.</span></span> <span data-ttu-id="04558-402">해당 파일을 선택한 상태에서 **Edge 배포 매니페스트 선택** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-402">With that file selected, click the **Select Edge Deployment Manifest** button.</span></span>

    ![배포 만들기](images/AzureLabs-Lab313-34.png)

8. <span data-ttu-id="04558-404">이제 **Azure Container Registry**에서 컨테이너를 모듈로 배포 하 여 장치에 효과적으로 배포 하는 데 필요한 매니페스트와 함께 **IoT Hub 서비스** 를 제공 했습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-404">At this point you have provided your **IoT Hub Service** with the manifest for it to deploy your container, as a module, from your **Azure Container Registry**, effectively deploying it to your device.</span></span>

9. <span data-ttu-id="04558-405">장치에서 IoT Hub 전송 된 메시지를 보려면 **탐색기** 패널의 **Azure IoT Hub** 장치 섹션에서 장치 이름을 다시 마우스 오른쪽 단추로 클릭 하 고 **D2C 메시지 모니터링 시작**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-405">To view the messages sent from your device to the IoT Hub, right-click again on your device name in the **Azure IoT Hub Devices** section, in the **Explorer** panel, and click on **Start Monitoring D2C Message**.</span></span> <span data-ttu-id="04558-406">장치에서 전송 된 메시지는 VS 터미널에 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-406">The messages sent from your device should appear in the VS Terminal.</span></span> <span data-ttu-id="04558-407">다소 시간이 걸릴 수 있으므로 잠시 기다려 주십시오.</span><span class="sxs-lookup"><span data-stu-id="04558-407">Be patient, as this may take some time.</span></span> <span data-ttu-id="04558-408">다음 챕터에서 디버깅을 참조 하 고 배포에 성공 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-408">See the next Chapter for debugging, and checking if deployment was successful.</span></span>

<span data-ttu-id="04558-409">이 모듈은 이제 각 반복에서 **이미지** 폴더의 이미지를 반복 하 고 분석 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-409">This module will now iterate between the images in the **images** folder and analyze them, with each iteration.</span></span> <span data-ttu-id="04558-410">이는 IoT Edge 장치 환경에서 기본적인 기계 학습 모델을 사용 하는 방법을 보여 주는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="04558-410">This is obviously just a demonstration of how to get the basic machine learning model to work in an IoT Edge device environment.</span></span> 

<span data-ttu-id="04558-411">이 예제의 기능을 확장 하기 위해 여러 가지 방법으로 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-411">To expand the functionality of this example, you could proceed in several ways.</span></span> <span data-ttu-id="04558-412">한 가지 방법은 컨테이너에 일부 코드를 포함 하 여 장치에 연결 된 웹캠에서 사진을 캡처하고 이미지 폴더에 이미지를 저장 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="04558-412">One way could be including some code in the container, that captures photos from a webcam that is connected to the device, and saves the images in the images folder.</span></span> 

<span data-ttu-id="04558-413">또 다른 방법은 IoT 장치에서 컨테이너로 이미지를 복사 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="04558-413">Another way could be copying the images from the IoT device into the container.</span></span> <span data-ttu-id="04558-414">이 작업을 수행 하는 실용적인 방법은 IoT 장치 터미널에서 다음 명령을 실행 하는 것입니다. 프로세스를 자동화 하려는 경우 작은 앱이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-414">A practical way to do that is to run the following command in the IoT device Terminal (perhaps a small app could do the job, if you wished to automate the process).</span></span> <span data-ttu-id="04558-415">파일이 저장 되는 폴더 위치에서 수동으로 실행 하 여이 명령을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-415">You can test this command by running it manually from the folder location where your files are stored:</span></span>

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a><span data-ttu-id="04558-416">10 장-IoT Edge 런타임 디버깅</span><span class="sxs-lookup"><span data-stu-id="04558-416">Chapter 10 - Debugging the IoT Edge Runtime</span></span>

<span data-ttu-id="04558-417">다음은 **Ubuntu 장치**에서 *IoT Edge 런타임의*메시징 활동을 모니터링 하 고 디버깅 하는 데 도움이 되는 명령줄 목록과 팁입니다.</span><span class="sxs-lookup"><span data-stu-id="04558-417">The following are a list of command lines, and tips, to help you monitor and debug the messaging activity of the *IoT Edge Runtime*, from your **Ubuntu device**.</span></span> 

- <span data-ttu-id="04558-418">다음 명령줄을 실행 하 여 *IoT Edge 런타임* 상태를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-418">Check the *IoT Edge Runtime* status by running the following command line:</span></span>

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > <span data-ttu-id="04558-419">상태 보기를 마치려면 **ctrl + C**를 눌러야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-419">Remember to press **Ctrl + C**, to finish viewing the status.</span></span>

- <span data-ttu-id="04558-420">현재 배포 된 컨테이너를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-420">List the containers that are currently deployed.</span></span> <span data-ttu-id="04558-421">*IoT Hub 서비스가* 성공적으로 컨테이너를 배포 하면 다음 명령줄을 실행 하 여 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-421">If the *IoT Hub Service* has deployed the containers successfully, they will be displayed by running the following command line:</span></span>

    ```bash
        sudo iotedge list
    ```

    <span data-ttu-id="04558-422">또는</span><span class="sxs-lookup"><span data-stu-id="04558-422">Or</span></span>

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > <span data-ttu-id="04558-423">위의 내용은 목록에 표시 되는 대로 모듈이 성공적으로 배포 되었는지 여부를 확인 하는 좋은 방법입니다. 그렇지 않으면 *edgeHub* 및 *edgeAgent* **만** 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-423">The above is a good way to check whether your module has been deployed successfully, as it will appear in the list; you will otherwise **only** see the *edgeHub* and *edgeAgent*.</span></span>

- <span data-ttu-id="04558-424">컨테이너의 코드 로그를 표시 하려면 다음 명령줄을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-424">To display the code logs of a container, run the following command line:</span></span>

    ```bash
        journalctl -u iotedge
    ```

<span data-ttu-id="04558-425">**IoT Edge 런타임을 관리 하는 데 유용한 명령:**</span><span class="sxs-lookup"><span data-stu-id="04558-425">**Useful commands to manage the IoT Edge Runtime:**</span></span>

-  <span data-ttu-id="04558-426">호스트의 모든 컨테이너를 삭제 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-426">To delete all containers in the host:</span></span>

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  <span data-ttu-id="04558-427">*IoT Edge 런타임을*중지 하려면:</span><span class="sxs-lookup"><span data-stu-id="04558-427">To stop the *IoT Edge Runtime*:</span></span>

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a><span data-ttu-id="04558-428">11 장-테이블 서비스 만들기</span><span class="sxs-lookup"><span data-stu-id="04558-428">Chapter 11 - Create Table Service</span></span> 

<span data-ttu-id="04558-429">저장소 리소스를 만들어 azure Tables 서비스를 만들 Azure Portal로 다시 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-429">Navigate back to your Azure Portal, where you will create an Azure Tables Service, by creating a Storage resource.</span></span>

1. <span data-ttu-id="04558-430">아직 로그인 하지 않은 경우 [Azure Portal](https://portal.azure.com)에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-430">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="04558-431">로그인 되 면 왼쪽 위 모서리에서 **리소스 만들기**를 클릭 하 고 **저장소 계정**을 검색 한 다음 **enter** 키를 눌러 검색을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-431">Once logged in, click on **Create a resource**, in the top left corner, and search for **Storage account**, and press the **Enter** key, to start the search.</span></span>

3. <span data-ttu-id="04558-432">표시 되 면 목록에서 **저장소 계정-blob, 파일, 테이블, 큐** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-432">Once it has appeared, click **Storage account - blob, file, table, queue** from the list.</span></span>

    ![저장소 계정 검색](images/AzureLabs-Lab313-35.png)

4. <span data-ttu-id="04558-434">새 페이지에 **저장소 계정** 서비스에 대 한 설명이 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-434">The new page will provide a description of the **Storage account** Service.</span></span> <span data-ttu-id="04558-435">이 프롬프트의 왼쪽 아래에서 **만들기** 단추를 클릭 하 여이 서비스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="04558-435">At the bottom left of this prompt, click the **Create** button, to create an instance of this Service.</span></span>

    ![저장소 인스턴스 만들기](images/AzureLabs-Lab313-36.png)

5. <span data-ttu-id="04558-437">**만들기**를 클릭 하면 패널이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-437">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="04558-438">이 서비스 인스턴스의 원하는 **이름을** 삽입 합니다 (*모두 소문자 여야 함*).</span><span class="sxs-lookup"><span data-stu-id="04558-438">Insert your desired **Name** for this Service instance (*must be all lowercase*).</span></span>

    2. <span data-ttu-id="04558-439">**배포 모델**에서 **리소스 관리자**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-439">For **Deployment model**, click **Resource manager**.</span></span>

    3. <span data-ttu-id="04558-440">**계정 종류**의 경우 드롭다운 메뉴에서 **저장소 (범용 v1)** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-440">For **Account kind**, using the dropdown menu, click **Storage (general purpose v1)**.</span></span>

    4. <span data-ttu-id="04558-441">적절 한 **위치**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-441">Click an appropriate **Location**.</span></span>
    
    5. <span data-ttu-id="04558-442">**복제** 드롭다운 메뉴에서 **읽기 액세스-지역 중복 저장소 (RA-GRS)** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-442">For the **Replication** dropdown menu, click **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6. <span data-ttu-id="04558-443">**성능**으로 **표준**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-443">For **Performance**, click **Standard**.</span></span>

    7. <span data-ttu-id="04558-444">**보안 전송 필요** 섹션에서 **사용 안 함**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-444">Within the **Secure transfer required** section, click **Disabled**.</span></span>

    8. <span data-ttu-id="04558-445">**구독** 드롭다운 메뉴에서 적절 한 구독을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-445">From the **Subscription** dropdown menu, click an appropriate subscription.</span></span>

    9. <span data-ttu-id="04558-446">리소스 그룹을 선택 하거나 새 **리소스 그룹** 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="04558-446">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="04558-447">리소스 그룹은 Azure 자산 컬렉션에 대 한 모니터링, 제어 액세스, 프로 비전 및 관리를 위한 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-447">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="04558-448">단일 프로젝트와 연결 된 모든 Azure 서비스 (예: 이러한 과정)를 공용 리소스 그룹에 유지 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-448">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="04558-449">Azure 리소스 그룹에 대 한 자세한 내용을 보려면 [리소스 그룹을 관리 하는 방법에 대](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)한 다음 링크를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="04558-449">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="04558-450">이 옵션을 선택 하는 경우 **가상 네트워크** 를 **사용 안 함**으로 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-450">Leave **Virtual networks** as **Disabled**, if this is an option for you.</span></span>

    11. <span data-ttu-id="04558-451">**만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-451">Click **Create**.</span></span>

        ![저장소 정보 입력](images/AzureLabs-Lab313-37.png)

6. <span data-ttu-id="04558-453">**만들기**를 클릭 한 후에는 서비스를 만들 때까지 기다려야 합니다 .이 작업이 몇 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-453">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

7. <span data-ttu-id="04558-454">서비스 인스턴스를 만든 후 알림이 포털에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-454">A notification will appear in the Portal once the Service instance is created.</span></span> <span data-ttu-id="04558-455">알림을 클릭 하 여 새 서비스 인스턴스를 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-455">Click on the notifications to explore your new Service instance.</span></span>

    ![새 저장소 알림](images/AzureLabs-Lab313-38.png)

8. <span data-ttu-id="04558-457">알림에서 **리소스로 이동** 단추를 클릭 하면 새 저장소 서비스 인스턴스 개요 페이지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-457">Click the **Go to resource** button in the notification, and you will be taken to your new Storage Service instance overview page.</span></span>

    ![리소스로 이동](images/AzureLabs-Lab313-39.png)

9. <span data-ttu-id="04558-459">개요 페이지에서 오른쪽에 있는 **테이블**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-459">From the overview page, to the right-hand side, click **Tables**.</span></span>
    
    ![표의](images/AzureLabs-Lab313-40.png)

10. <span data-ttu-id="04558-461">오른쪽 패널은 새 테이블을 추가 해야 하는 **테이블 서비스** 정보를 표시 하도록 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-461">The panel on the right will change to show the **Table Service** information, wherein you need to add a new table.</span></span> <span data-ttu-id="04558-462">왼쪽 위 모서리에서 **+ 테이블** 단추를 클릭 하 여이 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-462">Do this by clicking the **+ Table** button to the top-left corner.</span></span>

    ![테이블 열기](images/AzureLabs-Lab313-41.png)

11. <span data-ttu-id="04558-464">**테이블 이름을**입력 해야 하는 새 페이지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-464">A new page will be shown, wherein you need to enter a **Table name**.</span></span> <span data-ttu-id="04558-465">이 이름은 이후 챕터의 응용 프로그램에서 데이터를 참조 하는 데 사용 됩니다 (함수 앱 만들기 및 Power BI).</span><span class="sxs-lookup"><span data-stu-id="04558-465">This is the name you will use to refer to the data in your application in later Chapters (creating Function App, and Power BI).</span></span> <span data-ttu-id="04558-466">이름으로 **Iotmessages** 를 삽입 하 고이 문서의 뒷부분에서 사용 되는 경우에만 기억할 수 있으며 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-466">Insert **IoTMessages** as the name (you can choose your own, just remember it when used later in this document) and click **OK**.</span></span> 

12. <span data-ttu-id="04558-467">새 테이블을 만든 후에는 **테이블 서비스** 페이지 (아래쪽)에서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-467">Once the new table has been created, you will be able to see it within the **Table Service** page (at the bottom).</span></span>

    ![새 테이블을 만들었습니다.](images/AzureLabs-Lab313-42.png)  

13. <span data-ttu-id="04558-469">이제 **액세스 키** 를 클릭 하 고 **저장소 계정 이름** 및 **키** 의 복사본을 가져옵니다 (메모장 사용) .이 과정의 뒷부분에서 **Azure 함수 앱**를 만들 때 이러한 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-469">Now click on **Access keys** and take a copy of the **Storage account name** and **Key** (using your Notepad), you will use these values later in this course, when creating the **Azure Function App**.</span></span>

    ![새 테이블을 만들었습니다.](images/AzureLabs-Lab313-43.png) 

14. <span data-ttu-id="04558-471">왼쪽의 패널을 다시 사용 하 여 *테이블 서비스* 섹션으로 스크롤하고 테이블 (또는 새 포털에서 **테이블 찾아보기**) **을 클릭 하** 고 **테이블 URL** (메모장 사용)의 복사본을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="04558-471">Using the panel on the left again, scroll to the *Table Service* section, and click **Tables** (or **Browse Tables**, in newer Portals) and take a copy of the **Table URL** (using your Notepad).</span></span> <span data-ttu-id="04558-472">이 과정에서 나중에 테이블을 **Power BI** 응용 프로그램에 연결할 때이 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-472">You will use this value later in this course, when linking your table to your **Power BI** application.</span></span>

    ![새 테이블을 만들었습니다.](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a><span data-ttu-id="04558-474">12 장-Azure 테이블 완료</span><span class="sxs-lookup"><span data-stu-id="04558-474">Chapter 12 - Completing the Azure Table</span></span>

<span data-ttu-id="04558-475">이제 **Table Service** storage 계정이 설정 되었으므로 데이터를 추가 하 여 정보를 저장 하 고 검색 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-475">Now that your **Table Service** storage account has been setup, it is time to add data to it, which will be used to store and retrieve information.</span></span> <span data-ttu-id="04558-476">테이블 편집은 **Visual Studio**를 통해 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-476">The editing of your Tables can be done through **Visual Studio**.</span></span>

1. <span data-ttu-id="04558-477">**Visual Studio** 를 엽니다 (Visual Studio Code**하지 않음** ).</span><span class="sxs-lookup"><span data-stu-id="04558-477">Open **Visual Studio** (**not** Visual Studio Code).</span></span>

2. <span data-ttu-id="04558-478">메뉴에서**클라우드 탐색기** **보기** > 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-478">From the menu, click **View** > **Cloud Explorer**.</span></span>

    ![클라우드 탐색기 열기](images/AzureLabs-Lab313-45.png)

3. <span data-ttu-id="04558-480">**클라우드 탐색기** 은 도킹 된 항목으로 열립니다. 로드 시 시간이 걸릴 수 있으므로 잠시 기다려 주십시오.</span><span class="sxs-lookup"><span data-stu-id="04558-480">The **Cloud Explorer** will open as a docked item (be patient, as loading may take time).</span></span>

    > [!WARNING] 
    > <span data-ttu-id="04558-481">*저장소 계정을* 만드는 데 사용한 구독이 표시 되지 않는 경우 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-481">If the subscription you used to create your *Storage Accounts* is not visible, ensure that you have:</span></span> 
    > - <span data-ttu-id="04558-482">Azure Portal에 사용한 것과 동일한 계정에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-482">Logged in to the same account as the one you used for the Azure Portal.</span></span>
    > - <span data-ttu-id="04558-483">계정 관리 페이지에서 구독을 선택 했습니다 (계정 설정에서 필터를 적용 해야 할 수 있음).</span><span class="sxs-lookup"><span data-stu-id="04558-483">Selected your subscription from the Account Management page (you may need to apply a filter from your account settings):</span></span>  
    >
    >   ![구독 찾기](images/AzureLabs-Lab313-46.png)

4. <span data-ttu-id="04558-485">Azure cloud Services가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-485">Your Azure cloud Services will be shown.</span></span> <span data-ttu-id="04558-486">**저장소 계정을** 찾고 왼쪽에 있는 화살표를 클릭 하 여 계정을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-486">Find **Storage Accounts** and click the arrow to the left of that to expand your accounts.</span></span>

    ![저장소 계정 열기](images/AzureLabs-Lab313-47.png)

5. <span data-ttu-id="04558-488">확장 되 면 새로 만든 **저장소 계정을** 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-488">Once expanded, your newly created **Storage account** should be available.</span></span> <span data-ttu-id="04558-489">저장소 왼쪽에 있는 화살표를 클릭 한 다음 확장 되 면 **테이블** 을 찾아 해당 옆의 화살표를 클릭 하 여 마지막 챕터에서 만든 **테이블** 을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-489">Click the arrow to the left of your storage, and then once that is expanded, find **Tables** and click the arrow next to that, to reveal the **Table** you created in the last Chapter.</span></span> <span data-ttu-id="04558-490">**테이블**을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-490">Double-click your **Table**.</span></span>

6. <span data-ttu-id="04558-491">Visual Studio 창의 중앙에서 테이블이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="04558-491">Your table will be opened in the center of your Visual Studio window.</span></span> <span data-ttu-id="04558-492">**+** (더하기)가 있는 테이블 아이콘을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-492">Click the table icon with the **+** (plus) on it.</span></span>

    ![새 테이블 추가](images/AzureLabs-Lab313-48.png)

7. <span data-ttu-id="04558-494">*엔터티를 추가*하 라는 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-494">A window will appear prompting for you to *Add Entity*.</span></span> <span data-ttu-id="04558-495">3 개의 속성을 포함 하지만 엔터티는 하나만 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="04558-495">You will create only one entity, though it will have three properties.</span></span> <span data-ttu-id="04558-496">*PartitionKey* 및 *rowkey* 는 테이블에서 데이터를 찾기 위해 사용 되므로 이미 제공 된 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-496">You will notice that *PartitionKey* and *RowKey* are already provided, as these are used by the table to find your data.</span></span> 

    ![파티션 및 행 키](images/AzureLabs-Lab313-49.png)

8. <span data-ttu-id="04558-498">다음 값을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-498">Update the following values:</span></span>

    - <span data-ttu-id="04558-499">이름: **PartitionKey**, 값: **PK_IoTMessages**</span><span class="sxs-lookup"><span data-stu-id="04558-499">Name: **PartitionKey**, Value: **PK_IoTMessages**</span></span> 

    - <span data-ttu-id="04558-500">이름: **Rowkey**, 값: **RK_1_IoTMessages**</span><span class="sxs-lookup"><span data-stu-id="04558-500">Name: **RowKey**, Value: **RK_1_IoTMessages**</span></span> 

9. <span data-ttu-id="04558-501">그런 다음 *엔터티 추가* 창의 왼쪽 아래에 있는 **속성 추가** 를 클릭 하 고 다음 속성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-501">Then, click **Add property** (to the lower left of the *Add Entity* window) and add the following property:</span></span>

    - <span data-ttu-id="04558-502">**MessageContent**, *문자열*, 값을 비워 둡니다.</span><span class="sxs-lookup"><span data-stu-id="04558-502">**MessageContent**, as a *string*, leave the Value empty.</span></span>

10. <span data-ttu-id="04558-503">테이블은 아래 이미지에 있는 것과 일치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-503">Your table should match the one in the image below:</span></span>

    ![올바른 값 추가](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > <span data-ttu-id="04558-505">엔터티가 행 키에 숫자 1을 갖는 이유는이 과정을 통해 더 많은 메시지를 추가 하려고 할 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="04558-505">The reason why the entity has the number 1 in the row key, is because you might want to add more messages, should you desire to experiment further with this course.</span></span>

11. <span data-ttu-id="04558-506">작업이 완료 되 면 **확인을** 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-506">Click **OK** when you are finished.</span></span> <span data-ttu-id="04558-507">이제 테이블을 사용할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-507">Your table is now ready to be used.</span></span>

## <a name="chapter-13---create-an-azure-function-app"></a><span data-ttu-id="04558-508">13 장-Azure 함수 앱 만들기</span><span class="sxs-lookup"><span data-stu-id="04558-508">Chapter 13 - Create an Azure Function App</span></span> 

<span data-ttu-id="04558-509">이제 이전 장에서 만든 **Table** service에 *IoT Edge* 장치 메시지를 저장 하기 위해 *IoT Hub 서비스* 에 의해 호출 되는 *Azure 함수 앱*를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-509">It is now time to create an *Azure Function App*, which will be called by the *IoT Hub Service* to store the *IoT Edge* device messages in the **Table** Service, which you created in the previous Chapter.</span></span>

<span data-ttu-id="04558-510">먼저 Azure 함수에서 필요한 라이브러리를 로드 하도록 허용 하는 파일을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-510">First, you need to create a file that will allow your Azure Function to load the libraries you need.</span></span>

1.  <span data-ttu-id="04558-511">**메모장** 을 엽니다 ( *Windows 키*를 누른 다음 *notepad*를 입력).</span><span class="sxs-lookup"><span data-stu-id="04558-511">Open **Notepad** (press the *Windows Key*, and type *notepad*).</span></span>

    ![메모장 열기](images/AzureLabs-Lab313-51.png)

2.  <span data-ttu-id="04558-513">메모장을 열고 아래에 JSON 구조를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-513">With Notepad open, insert the JSON structure below into it.</span></span> <span data-ttu-id="04558-514">이 작업을 완료 한 후에는 데스크톱에 프로젝트를 **json**으로 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-514">Once you have done that, save it on your desktop as **project.json**.</span></span> <span data-ttu-id="04558-515">이 파일은 함수에서 사용할 라이브러리를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-515">This file defines the libraries your function will use.</span></span> <span data-ttu-id="04558-516">NuGet을 사용한 경우 익숙할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="04558-516">If you have used NuGet, it will look familiar.</span></span>
    
    > [!WARNING]
    > <span data-ttu-id="04558-517">이름을 올바르게 지정 해야 합니다. **.txt** 파일 확장명이 없는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-517">It is important that the naming is correct; ensure it does **NOT have a .txt** file extension.</span></span> <span data-ttu-id="04558-518">참조는 아래를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="04558-518">See below for reference:</span></span>
    >
    > ![JSON 저장](images/AzureLabs-Lab313-52.png)

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "9.2.0"
        }
        }
    }
    }
    ```

3.  <span data-ttu-id="04558-520">[Azure Portal](https://portal.azure.com)에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-520">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

4.  <span data-ttu-id="04558-521">로그인 되 면 왼쪽 위 모서리에서 **리소스 만들기** 를 클릭 하 고 **함수 앱**를 검색 한 다음 **enter** 키를 눌러 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-521">Once you are logged in, click on **Create a resource** in the top left corner, and search for **Function App**, and press the **Enter** key, to search.</span></span> <span data-ttu-id="04558-522">결과에서 *함수 앱* 를 클릭 하 여 새 패널을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="04558-522">Click *Function App* from the results, to open a new panel.</span></span>

    ![함수 앱 검색](images/AzureLabs-Lab313-53.png)

5.  <span data-ttu-id="04558-524">새 패널은 **함수 앱** 서비스에 대 한 설명을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-524">The new panel will provide a description of the **Function App** Service.</span></span> <span data-ttu-id="04558-525">이 패널의 왼쪽 아래에서 **만들기** 단추를 클릭 하 여이 서비스와의 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="04558-525">At the bottom left of this panel, click the **Create** button, to create an association with this Service.</span></span>

    ![함수 앱 인스턴스](images/AzureLabs-Lab313-54.png)

6.  <span data-ttu-id="04558-527">**만들기**를 클릭 한 후에는 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-527">Once you have clicked on **Create**, fill in the following:</span></span>

    1. <span data-ttu-id="04558-528">**앱 이름**에 대해 원하는 이름을이 서비스 인스턴스에 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-528">For **App name**, insert your desired name for this Service instance.</span></span>

    2. <span data-ttu-id="04558-529">**구독**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-529">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="04558-530">적절 한 가격 책정 계층을 선택 합니다. **함수 앱 서비스**를 처음 만드는 경우 무료 계층을 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-530">Select the pricing tier appropriate for you, if this is the first time creating a **Function App Service**, a free tier should be available to you.</span></span>

    4. <span data-ttu-id="04558-531">리소스 그룹을 선택 하거나 새 **리소스 그룹** 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="04558-531">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="04558-532">리소스 그룹은 Azure 자산 컬렉션에 대 한 모니터링, 제어 액세스, 프로 비전 및 관리를 위한 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-532">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="04558-533">단일 프로젝트와 연결 된 모든 Azure 서비스 (예: 이러한 과정)를 공용 리소스 그룹에 유지 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-533">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="04558-534">Azure 리소스 그룹에 대 한 자세한 내용을 보려면 [리소스 그룹을 관리 하는 방법에 대](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)한 다음 링크를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="04558-534">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="04558-535">**OS**의 경우 원하는 플랫폼인 Windows를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-535">For **OS**, click Windows, as that is the intended platform.</span></span>

    6. <span data-ttu-id="04558-536">**호스팅 계획** 을 선택 합니다 .이 자습서는 **소비 계획**을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-536">Select a **Hosting Plan** (this tutorial is using a **Consumption Plan**.</span></span>

    7. <span data-ttu-id="04558-537">**위치** 선택 (이전 단계에서 빌드한 저장소와 동일한 위치 선택)</span><span class="sxs-lookup"><span data-stu-id="04558-537">Select a **Location** (choose the same location as the storage you have built in the previous step)</span></span>

    8. <span data-ttu-id="04558-538">**저장소** 섹션의 경우 **이전 단계에서 만든 저장소 서비스를 선택 해야**합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-538">For the **Storage** section, **you must select the Storage Service you created in the previous step**.</span></span>

    9. <span data-ttu-id="04558-539">이 앱에 *Application Insights* 필요 하지 않으므로 자유롭게 그대로 **둡니다.**</span><span class="sxs-lookup"><span data-stu-id="04558-539">You will not need *Application Insights* in this app, so feel free to leave it **Off**.</span></span>

    10. <span data-ttu-id="04558-540">**만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-540">Click **Create**.</span></span>

        ![새 인스턴스 만들기](images/AzureLabs-Lab313-55.png)

7.  <span data-ttu-id="04558-542">**만들기**를 클릭 한 후에는 서비스를 만들 때까지 기다려야 합니다 .이 작업이 몇 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-542">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

8.  <span data-ttu-id="04558-543">서비스 인스턴스를 만든 후 알림이 포털에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-543">A notification will appear in the Portal once the Service instance is created.</span></span>

    ![새 알림](images/AzureLabs-Lab313-56.png)

9.  <span data-ttu-id="04558-545">배포가 성공적으로 완료 되 면 알림을 클릭 합니다 (완료 됨).</span><span class="sxs-lookup"><span data-stu-id="04558-545">Click on the notification, once deployment is successful (has finished).</span></span>

10. <span data-ttu-id="04558-546">알림에서 **리소스로 이동** 단추를 클릭 하 여 새 서비스 인스턴스를 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-546">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> 

    ![리소스로 이동](images/AzureLabs-Lab313-57.png)

11. <span data-ttu-id="04558-548">새 패널의 왼쪽에서 **+** *함수*옆에 있는 더하기 () 아이콘을 클릭 하 여 새 함수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="04558-548">In the left side of the new panel, click the **+** (plus) icon next to *Functions*, to create a new function.</span></span>

    ![새 함수 추가](images/AzureLabs-Lab313-58.png)

12. <span data-ttu-id="04558-550">중앙 패널 내에서 **함수** 만들기 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-550">Within the central panel, the **Function** creation window will appear.</span></span> <span data-ttu-id="04558-551">아래로 스크롤하여 **사용자 지정 함수**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-551">Scroll down further, and click on **Custom function**.</span></span>

    ![사용자 지정 함수](images/AzureLabs-Lab313-59.png)

13. <span data-ttu-id="04558-553">**IoT Hub (이벤트 허브)** 를 찾을 때까지 다음 페이지 아래로 스크롤한 다음 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-553">Scroll down the next page, until you find **IoT Hub (Event Hub)**, then click on it.</span></span>

    ![사용자 지정 함수](images/AzureLabs-Lab313-60.png)

14. <span data-ttu-id="04558-555">**IoT Hub (이벤트 허브)** 블레이드에서 **언어** 를로 **C#** 설정 하 고 **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-555">In the **IoT Hub (Event Hub)** blade, set the **Language** to **C#** and then click on **new**.</span></span>

    ![사용자 지정 함수](images/AzureLabs-Lab313-61.png)

15. <span data-ttu-id="04558-557">표시 되는 창에서 **IoT Hub** 가 선택 되어 있는지 확인 하 고 *IoT Hub* 필드 이름이 이전에 만든 *IoT Hub 서비스* 의 이름 ([3 장의 8 단계](#chapter-3---the-iot-hub-service))과 일치 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-557">In the window that will appear, make sure that **IoT Hub** is selected and the name of the *IoT Hub* field corresponds with the name of your *IoT Hub Service* that you have created previously ([in step 8, of Chapter 3](#chapter-3---the-iot-hub-service)).</span></span> <span data-ttu-id="04558-558">그런 다음 **선택** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-558">Then click the **Select** button.</span></span>

    ![사용자 지정 함수](images/AzureLabs-Lab313-62.png)

16. <span data-ttu-id="04558-560">**IoT Hub (이벤트 허브)** 블레이드로 돌아가서 **만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-560">Back on the **IoT Hub (Event Hub)** blade, click on **Create**.</span></span>

    ![사용자 지정 함수](images/AzureLabs-Lab313-63.png)

17. <span data-ttu-id="04558-562">그러면 함수 편집기로 리디렉션됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-562">You will be redirected to the function editor.</span></span>

    ![사용자 지정 함수](images/AzureLabs-Lab313-64.png)

18. <span data-ttu-id="04558-564">모든 코드를 삭제 하 고 다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="04558-564">Delete all the code in it and replace it with the following:</span></span>

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"
    #r "NewtonSoft.Json"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Newtonsoft.Json;
    using System.Threading.Tasks;

    public static async Task Run(string myIoTHubMessage, TraceWriter log)
    {
        log.Info($"C# IoT Hub trigger function processed a message: {myIoTHubMessage}");
        
        //RowKey of the table object to be changed
        string tableName = "IoTMessages";
        string tableURL = "https://iothubmrstorage.table.core.windows.net/IoTMessages";

        // If you did not name your Storage Service as suggested in the course, change the name here with the one you chose.
        string storageAccountName = "iotedgestor"; 

        string storageAccountKey = "<Insert your Storage Key here>";   

        string partitionKey = "PK_IoTMessages";
        string rowKey = "RK_1_IoTMessages";

        Microsoft.WindowsAzure.Storage.Auth.StorageCredentials storageCredentials =
            new Microsoft.WindowsAzure.Storage.Auth.StorageCredentials(storageAccountName, storageAccountKey);

        CloudStorageAccount storageAccount = new CloudStorageAccount(storageCredentials, true);

        // Create the table client.
        CloudTableClient tableClient = storageAccount.CreateCloudTableClient();

        // Get a reference to a table named "IoTMessages"
        CloudTable messageTable = tableClient.GetTableReference(tableName);

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<MessageEntity>(partitionKey, rowKey);
        TableResult result = await messageTable.ExecuteAsync(operation);

        //Create a MessageEntity so to set its parameters
        MessageEntity messageEntity = (MessageEntity)result.Result;

        messageEntity.MessageContent = myIoTHubMessage;
        messageEntity.PartitionKey = partitionKey;
        messageEntity.RowKey = rowKey;

        //Replace the table appropriate table Entity with the value of the MessageEntity Ccass structure.
        operation = TableOperation.Replace(messageEntity);

        // Execute the insert operation.
        await messageTable.ExecuteAsync(operation);
    }

    // This MessageEntity structure which will represent a Table Entity
    public class MessageEntity : TableEntity
    {
        public string Type { get; set; }
        public string MessageContent { get; set; }   
    }
    ```

19. <span data-ttu-id="04558-565">다음 변수를 변경 하 여 **저장소 계정**에서 찾을 수 있는 적절 한**값** (  [11 장에서 각각 11 장, 13 단계](#chapter-11---create-table-service))에 해당 하는 값에 해당 하는 변수를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-565">Change the following variables, so that they correspond to the appropriate values (**Table** and **Storage** values, from [step 11 and 13, respectively, of Chapter 11](#chapter-11---create-table-service)), that you will find in your **Storage Account**:</span></span>

    - <span data-ttu-id="04558-566">**tableName**- **저장소 계정**에 있는 **테이블** 의 이름을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-566">**tableName**, with the name of your **Table** located in your **Storage Account**.</span></span>
    - <span data-ttu-id="04558-567">**Tableurl**- **저장소 계정**에 있는 **테이블** 의 url을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-567">**tableURL**, with the URL of your **Table** located in your **Storage Account**.</span></span>
    - <span data-ttu-id="04558-568">**Storageaccountname**, **저장소 계정** 이름 이름에 해당 하는 값의 이름을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-568">**storageAccountName**, with the name of the value corresponding with the name of your **Storage Account** name.</span></span>
    - <span data-ttu-id="04558-569">이전에 만든 저장소 서비스에서 가져온 키를 사용 하 여 **storageAccountKey**.</span><span class="sxs-lookup"><span data-stu-id="04558-569">**storageAccountKey**, with the Key you have obtained in the Storage Service you have created previously.</span></span>

    ![사용자 지정 함수](images/AzureLabs-Lab313-65.png)

20. <span data-ttu-id="04558-571">코드가 준비 되 면 **저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-571">With the code in place, click **Save**.</span></span>

21. <span data-ttu-id="04558-572">그런 다음 페이지의 **\<** 오른쪽에 있는 (화살표) 아이콘을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-572">Next, click the **\<** (arrow) icon, on the right-hand side of the page.</span></span>

    ![사용자 지정 함수](images/AzureLabs-Lab313-66.png)

22. <span data-ttu-id="04558-574">패널은 오른쪽에서 오른쪽으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-574">A panel will slide in from the right.</span></span> <span data-ttu-id="04558-575">해당 패널에서 **업로드**를 클릭 하면 *파일 브라우저가* 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="04558-575">In that panel, click **Upload**, and a *File Browser* will appear.</span></span>

23. <span data-ttu-id="04558-576">로 이동 하 여 이전에 **메모장** 에서 만든 **프로젝트. json** 파일을 클릭 한 다음 **열기** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-576">Navigate to, and click, the **project.json** file, which you created in **Notepad** previously, and then click the **Open** button.</span></span> <span data-ttu-id="04558-577">이 파일은 함수에서 사용할 라이브러리를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-577">This file defines the libraries that your function will use.</span></span>

    ![사용자 지정 함수](images/AzureLabs-Lab313-67.png)

24. <span data-ttu-id="04558-579">파일이 업로드 되 면 오른쪽의 패널에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-579">When the file has uploaded, it will appear in the panel on the right.</span></span> <span data-ttu-id="04558-580">이 단추를 클릭 하면 **함수** 편집기 내에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="04558-580">Clicking it will open it within the **Function** editor.</span></span> <span data-ttu-id="04558-581">이 이미지는 다음 이미지와 정확히 동일 하 **게** 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-581">It must look **exactly** the same as the next image.</span></span>

    ![사용자 지정 함수](images/AzureLabs-Lab313-68.png)

25. <span data-ttu-id="04558-583">이 시점에서 함수 기능을 테스트 하 여 *테이블*에 메시지를 저장 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-583">At this point it would be good to test the capability of your Function to store the message on your *Table*.</span></span> <span data-ttu-id="04558-584">창의 오른쪽 위에서 **테스트**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-584">On the top right side of the window, click on **Test**.</span></span>

    ![사용자 지정 함수](images/AzureLabs-Lab313-69.png)

26. <span data-ttu-id="04558-586">위의 이미지에 표시 된 것 처럼 **요청 본문**에 메시지를 삽입 하 고 **실행**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-586">Insert a message on the **Request body**, as shown in the image above, and click on **Run**.</span></span> 

27. <span data-ttu-id="04558-587">함수를 실행 하 여 결과 상태를 표시 합니다. *출력* 창 위에 녹색 **상태 202이 수락**되었음을 알 수 있습니다 .이는 성공적인 호출 임을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-587">The function will run, displaying the result status (you will notice the green **Status 202 Accepted**, above the *Output* window, which means it was a successful call):</span></span>

    ![출력 결과](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a><span data-ttu-id="04558-589">14 장-활성 메시지 보기</span><span class="sxs-lookup"><span data-stu-id="04558-589">Chapter 14 - View active messages</span></span>

<span data-ttu-id="04558-590">이제 Visual Studio를 열 때 (Visual Studio Code**하지 않음** ) *MessageContent* 문자열 영역에 저장 되므로 테스트 메시지 결과를 시각화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-590">If you now open Visual Studio (**not** Visual Studio Code), you can visualize your test message result, as it will be stored in the *MessageContent* string area.</span></span>

![사용자 지정 함수](images/AzureLabs-Lab313-71.png)

<span data-ttu-id="04558-592">Table Service와 함수 앱를 사용 하 여 Ubuntu 장치 메시지가 *I이상 메시지* 테이블에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-592">With the Table Service and Function App in place, your Ubuntu device messages will appear in your *IoTMessages* Table.</span></span> <span data-ttu-id="04558-593">아직 실행 중이 아닌 경우 장치를 다시 시작 하면 Visual Studio *클라우드 탐색기*를 사용 하 여 장치 및 모듈의 결과 메시지를 테이블 내에서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-593">If not already running, start your device again, and you will be able to see the result messages from your device, and module, within your Table, through using Visual Studio *Cloud Explorer*.</span></span>

![데이터 시각화](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a><span data-ttu-id="04558-595">15 장-Power BI 설치</span><span class="sxs-lookup"><span data-stu-id="04558-595">Chapter 15 - Power BI Setup</span></span>

<span data-ttu-id="04558-596">IOT 장치에서 데이터를 시각화 하려면 **Power BI** (데스크톱 버전)을 설치 하 여 방금 만든 *테이블* 서비스에서 데이터를 수집 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-596">To visualize the data from your IOT device you will setup **Power BI** (desktop version), to collect the data from the *Table* Service, which you just created.</span></span> <span data-ttu-id="04558-597">Power BI의 *HoloLens* 버전은 해당 데이터를 사용 하 여 결과를 시각화 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-597">The *HoloLens* version of Power BI will then use that data to visualize the result.</span></span>

1.  <span data-ttu-id="04558-598">Windows 10에서 Microsoft Store를 열고 **Power BI Desktop**를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-598">Open the Microsoft Store on Windows 10 and search for **Power BI Desktop**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  <span data-ttu-id="04558-600">응용 프로그램을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-600">Download the application.</span></span> <span data-ttu-id="04558-601">다운로드가 완료 되 면 엽니다.</span><span class="sxs-lookup"><span data-stu-id="04558-601">Once it has finished downloading, open it.</span></span>

3.  <span data-ttu-id="04558-602">**Microsoft 365 계정**으로 *Power BI* 에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-602">Log into *Power BI* with your **Microsoft 365 account**.</span></span> <span data-ttu-id="04558-603">등록 하려면 브라우저로 리디렉션될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-603">You may be redirected to a browser, to sign up.</span></span> <span data-ttu-id="04558-604">등록 하면 Power BI 앱으로 돌아가서 다시 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-604">Once you are signed up, go back to the Power BI app, and sign in again.</span></span>

4.  <span data-ttu-id="04558-605">**데이터 가져오기** 를 클릭 하 고 **자세히**...를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-605">Click on **Get Data** and then click on **More...**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  <span data-ttu-id="04558-607">**Azure**, **azure Table Storage**를 클릭 한 다음 **연결**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-607">Click **Azure**, **Azure Table Storage**, then click on **Connect**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  <span data-ttu-id="04558-609">테이블 서비스를 만드는 동안 이전에 수집한 **테이블 URL** ([11 장의 13 단계](#chapter-11---create-table-service))을 삽입 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-609">You will be prompted to insert the **Table URL** that you collected earlier ([in step 13 of Chapter 11](#chapter-11---create-table-service)), while creating your Table Service.</span></span> <span data-ttu-id="04558-610">URL을 삽입 한 후에 "하위 폴더" 테이블을 참조 하는 경로 부분을 삭제 합니다 (이 과정에서는 I이상 메시지).</span><span class="sxs-lookup"><span data-stu-id="04558-610">After inserting the URL, delete the portion of the path referring to the Table "sub-folder" (which was IoTMessages, in this course).</span></span> <span data-ttu-id="04558-611">최종 결과는 아래 이미지에 표시 된 것과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-611">The final result should be as displayed in the image below.</span></span> <span data-ttu-id="04558-612">그런 다음 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-612">Then click on **OK**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  <span data-ttu-id="04558-614">Table Storage를 만드는 동안 앞에서 설명한 **저장소 키** ([11 장 11 단계](#chapter-11---create-table-service))를 삽입 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-614">You will be prompted to insert the **Storage Key** that you noted ([in step 11 of Chapter 11](#chapter-11---create-table-service)) earlier while creating your Table Storage.</span></span> <span data-ttu-id="04558-615">그런 다음 **연결**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-615">Then click on **Connect**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. <span data-ttu-id="04558-617">**탐색기 패널이** 표시 되 면 테이블 옆의 상자에 상자를 표시 하 고 **로드**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-617">A **Navigator Panel** will be displayed, tick the box next to your Table and click on **Load**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. <span data-ttu-id="04558-619">이제 테이블이 Power BI에 로드 되었지만 쿼리를 사용 하 여 값을 표시 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-619">Your table has now been loaded on Power BI, but it requires a query to display the values in it.</span></span> <span data-ttu-id="04558-620">이렇게 하려면 화면 오른쪽에 있는 **필드 패널** 에 있는 테이블 이름을 마우스 오른쪽 단추로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-620">To do so, right-click on the table name located in the **FIELDS panel** at the right side of the screen.</span></span> <span data-ttu-id="04558-621">그런 다음 **쿼리 편집**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-621">Then click on **Edit Query**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. <span data-ttu-id="04558-623">**파워 쿼리 편집기** 가 새 창으로 열리고 테이블이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-623">A **Power Query Editor**  will open up as a new window, displaying your table.</span></span> <span data-ttu-id="04558-624">테이블의 *내용* 열에서 **레코드** 를 클릭 하 여 저장 된 콘텐츠를 시각화 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-624">Click on the word **Record** within the *Content* column of the table, to visualize your stored content.</span></span>

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. <span data-ttu-id="04558-626">창의 왼쪽 위에서 **표**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-626">Click on **Into Table**, at the top-left of the window.</span></span> 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. <span data-ttu-id="04558-628">**닫기 & 적용**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-628">Click on **Close & Apply**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. <span data-ttu-id="04558-630">쿼리 로드를 완료 한 후에는 **필드 패널**내에서 화면 오른쪽에 있는 **MessageContent** 열 내용을 시각화 하기 위해 매개 변수 **이름** 및 **값**에 해당 하는 상자를 tick.</span><span class="sxs-lookup"><span data-stu-id="04558-630">Once it has finished loading the query, within the **FIELDS panel**, on the right side of the screen, tick the boxes corresponding to the parameters **Name** and **Value**, to visualize the **MessageContent** column content.</span></span>

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. <span data-ttu-id="04558-632">창의 왼쪽 위에서 **파란색 디스크 아이콘** 을 클릭 하 여 선택한 폴더에 작업을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-632">Click on the **blue disk icon** at the top left of the window to save your work in a folder of your choice.</span></span>

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. <span data-ttu-id="04558-634">이제 게시 단추를 클릭 하 여 작업 영역에 테이블을 업로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-634">You can now click on the Publish button to upload your table to your Workspace.</span></span> <span data-ttu-id="04558-635">메시지가 표시 되 면 **내 작업 영역** 을 클릭 하 고 *선택*을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-635">When prompted, click **My workspace** and click *Select*.</span></span> <span data-ttu-id="04558-636">전송의 성공적인 결과가 표시 될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="04558-636">Wait for it to display the successful result of the submission.</span></span>

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> <span data-ttu-id="04558-639">다음 장은 HoloLens 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="04558-639">The following Chapter is HoloLens specific.</span></span> <span data-ttu-id="04558-640">Power BI 현재 모던 응용 프로그램으로 사용할 수 데스크톱 앱을 통해 Windows Mixed Reality 포털 (즉, 절벽 하우스)에서 데스크톱 버전을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-640">Power BI is not currently availble as an immersive application, however you can run the desktop version in the Windows Mixed Reality Portal (aka Cliff House), through the Desktop app.</span></span>

## <a name="chapter-16---display-power-bi-data-on-hololens"></a><span data-ttu-id="04558-641">16 장-HoloLens에 Power BI 데이터 표시</span><span class="sxs-lookup"><span data-stu-id="04558-641">Chapter 16 - Display Power BI data on HoloLens</span></span>

1. <span data-ttu-id="04558-642">HoloLens의 응용 프로그램 목록에서 아이콘을 탭 하 여 **Microsoft Store**에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-642">On your HoloLens, log in to the **Microsoft Store**, by tapping on its icon in the applications list.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-87.png)

2. <span data-ttu-id="04558-644">**Power BI** 응용 프로그램을 검색 한 후 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-644">Search and then download the **Power BI** application.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-88.png)

3. <span data-ttu-id="04558-646">응용 프로그램 목록에서 **Power BI** 을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-646">Start **Power BI** from your applications list.</span></span> 

4. <span data-ttu-id="04558-647">**Power BI** 에서 **Microsoft 365 계정**에 로그인 하 라는 메시지가 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-647">**Power BI** might ask you to login to your **Microsoft 365 account**.</span></span>

5. <span data-ttu-id="04558-648">앱 내에서 작업 영역은 아래 이미지와 같이 기본적으로 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-648">Once inside the app, the workspace should display by default as shown in the image below.</span></span> <span data-ttu-id="04558-649">이 문제가 발생 하지 않으면 창의 왼쪽에 있는 작업 영역 아이콘을 클릭 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04558-649">If that does not happen, simply click on the workspace icon on the left side of the window.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a><span data-ttu-id="04558-651">IoT Hub 응용 프로그램을 완료 했습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-651">Your finished your IoT Hub application</span></span>

<span data-ttu-id="04558-652">축 하 합니다. 시뮬레이트된 가상 머신에 지 장치를 사용 하 여 IoT Hub 서비스를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-652">Congratulations, you have successfully created an IoT Hub Service, with a simulated Virtual Machine Edge device.</span></span> <span data-ttu-id="04558-653">장치는 azure 함수 앱에서 활용 하 여 기계 학습 모델의 결과를 Azure 테이블 서비스에 전달할 수 있으며,이를 통해 Power BI으로 읽어 Microsoft HoloLens 내에서 시각화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-653">Your device can  communicate the results of a machine learning model to an Azure Table Service, facilitated by an Azure Function App, which is read into Power BI, and visualized within a Microsoft HoloLens.</span></span>
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="04558-655">보너스 연습</span><span class="sxs-lookup"><span data-stu-id="04558-655">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="04558-656">연습 1</span><span class="sxs-lookup"><span data-stu-id="04558-656">Exercise 1</span></span>

<span data-ttu-id="04558-657">테이블에 저장 된 메시징 구조를 확장 하 고 그래프로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="04558-657">Expand the messaging structure stored in the table and display it as a graph.</span></span> <span data-ttu-id="04558-658">나중에 표시 하기 위해 더 많은 데이터를 수집 하 여 동일한 테이블에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04558-658">You might want to collect more data and store it in the same table, to be later displayed.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="04558-659">연습 2</span><span class="sxs-lookup"><span data-stu-id="04558-659">Exercise 2</span></span>

<span data-ttu-id="04558-660">분석할 카메라를 통해 이미지를 캡처할 수 있도록 IoT 보드에 배포할 추가 "카메라 캡처" 모듈을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="04558-660">Create an additional "camera capture" module to be deployed on the IoT board, so that it can capture images through the camera to be analyzed.</span></span>
