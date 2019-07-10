---
title: MR 및 Azure 313-IoT Hub 서비스
description: Ubuntu 16.4를 실행 하는 가상 컴퓨터에서 Azure IoT Hub 서비스를 구현 하는 방법을 알아보려면이 과정을 완료 한 다음 Microsoft HoloLens 또는 몰입 형 (VR) 헤드셋을 사용 하 여 메시지 데이터를 시각화 합니다.
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: azure, 혼합 현실, academy, edge, iot edge, 자습서, api, 알림, 함수, 테이블, 몰입 형 hololens, vr, iot, 가상 머신, ubuntu, python
ms.openlocfilehash: 93f7dc64426360d2e02b0ee0a9b1796fc8f2b469
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694595"
---
>[!NOTE]
><span data-ttu-id="274fe-104">혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="274fe-105">따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="274fe-106">이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="274fe-107">지원 되는 장치에서 작업을 계속 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="274fe-108">새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="274fe-109">게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-313-iot-hub-service"></a><span data-ttu-id="274fe-110">MR 및 Azure 313: IoT Hub Service</span><span class="sxs-lookup"><span data-stu-id="274fe-110">MR and Azure 313: IoT Hub Service</span></span>

![과정 결과](images/AzureLabs-Lab313-00.png)

<span data-ttu-id="274fe-112">이 과정에서는 구현 하는 방법을 배우게 됩니다는 **Azure IoT Hub 서비스** 가상 머신에서 Ubuntu 16.4 운영 체제를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-112">In this course, you will learn how to implement an **Azure IoT Hub Service** on a virtual machine running the Ubuntu 16.4 operating system.</span></span> <span data-ttu-id="274fe-113">**Azure 함수 앱** Ubuntu VM에서 메시지를 수신 하려면 다음을 사용 하 고 내에서 결과 저장 한 **Azure Table Service**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-113">An **Azure Function App** will then be used to receive messages from your Ubuntu VM, and store the result within an **Azure Table Service**.</span></span> <span data-ttu-id="274fe-114">그런 다음 사용 하 여이 데이터를 볼 수 있습니다 **Power BI** Microsoft HoloLens 또는 몰입 형 (VR) 헤드셋 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-114">You will then be able to view this data using **Power BI** on Microsoft HoloLens or immersive (VR) headset.</span></span>

<span data-ttu-id="274fe-115">이 과정의 내용을 *적용 됩니다* IoT Edge 장치에이 과정에서는 목적으로 있지만 포커스는 되도록 가상 컴퓨터 환경에서 실제 Edge 장치에 액세스할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-115">The content of this course *is applicable* to IoT Edge devices, though for the purpose of this course, the focus will be on a virtual machine environment, so that access to a physical Edge device is not necessary.</span></span>

<span data-ttu-id="274fe-116">이 과정을 완료 하는 것이 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-116">By completing this course, you will learn to:</span></span>

- <span data-ttu-id="274fe-117">배포를 **IoT Edge 모듈** IoT 장치를 나타내는 가상 컴퓨터 (Ubuntu 16 OS).</span><span class="sxs-lookup"><span data-stu-id="274fe-117">Deploy an **IoT Edge module** to a Virtual Machine (Ubuntu 16 OS), which will represent your IoT device.</span></span>
- <span data-ttu-id="274fe-118">추가 된 **Azure 사용자 지정 비전 Tensorflow 모델** Edge 모듈은 컨테이너에 저장 된 이미지를 분석 하는 코드를 사용 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-118">Add an **Azure Custom Vision Tensorflow Model** to the Edge module, with code that will analyze images stored in the container.</span></span>
- <span data-ttu-id="274fe-119">분석 결과 메시지를 보내려면 모듈 설정 다시 하 **IoT Hub 서비스**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-119">Set up the module to send the analysis result message back to your **IoT Hub Service**.</span></span>
- <span data-ttu-id="274fe-120">사용 하 여는 **Azure 함수 앱** 내에서 메시지를 저장 하는 **Azure Table**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-120">Use an **Azure Function App** to store the message within an **Azure Table**.</span></span>
- <span data-ttu-id="274fe-121">설정할 **Power BI** 보고서를 만들고 저장된 된 메시지를 수집 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-121">Set up **Power BI** to collect the stored message and create a report.</span></span>
- <span data-ttu-id="274fe-122">내 IoT 메시지 데이터 시각화 **Power BI**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-122">Visualize your IoT message data within **Power BI**.</span></span>

<span data-ttu-id="274fe-123">사용 하 여 서비스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-123">The Services you will use include:</span></span>

- <span data-ttu-id="274fe-124">**Azure IoT Hub** 는 연결, 모니터링, IoT 자산을 관리 하는 개발자가 Microsoft Azure 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-124">**Azure IoT Hub** is a Microsoft Azure Service which allows developers to connect, monitor, and manage, IoT assets.</span></span> <span data-ttu-id="274fe-125">자세한 내용은 참조는 [ **Azure IoT Hub 서비스** 페이지](https://azure.microsoft.com/en-au/services/iot-hub/)합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-125">For more information, visit the [**Azure IoT Hub Service** page](https://azure.microsoft.com/en-au/services/iot-hub/).</span></span>

- <span data-ttu-id="274fe-126">**Azure Container Registry** 는 Microsoft Azure 서비스는 개발자가 다양 한 유형의 컨테이너에 대 한 컨테이너 이미지를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-126">**Azure Container Registry** is a Microsoft Azure Service which allows developers to store container images, for various types of containers.</span></span> <span data-ttu-id="274fe-127">자세한 내용은 합니다 [ **Azure 컨테이너 레지스트리 서비스로** 페이지](https://azure.microsoft.com/en-au/services/container-registry/)합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-127">For more information, visit the [**Azure Container Registry Service** page](https://azure.microsoft.com/en-au/services/container-registry/).</span></span>

- <span data-ttu-id="274fe-128">**Azure 함수 앱** 작은 코드를 실행 하기 위해 개발자를 허용 하는 Microsoft Azure 서비스, '', Azure에서 functions 됩니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-128">**Azure Function App** is a Microsoft Azure Service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="274fe-129">다양 한 이점을 가질 수 있는 로컬 응용 프로그램 보다는 클라우드의 작업을 위임 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-129">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="274fe-130">**Azure Functions** C를 비롯 한 여러 개발 언어를 지 원하는\#, F\#, Node.js, Java 및 PHP 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-130">**Azure Functions** supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="274fe-131">자세한 내용은 참조는 [ **Azure Functions** 페이지](https://docs.microsoft.com/azure/azure-functions/functions-overview)합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-131">For more information, visit the [**Azure Functions** page](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

- <span data-ttu-id="274fe-132">**Azure Storage: 테이블** 는 Microsoft Azure 서비스 수 있게 저장할 구조화, 비 SQL, 클라우드에서 데이터 아무 곳 이나 쉽게 액세스할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-132">**Azure Storage: Tables** is a Microsoft Azure Service, which allows developers to store structured, non-SQL, data in the cloud, making it easily accessible anywhere.</span></span> <span data-ttu-id="274fe-133">서비스는 스키마 없이 디자인을 소재 필요에 따라 테이블의 발전에 대 한 허용 되어 있으므로 매우 유연 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-133">The Service boasts a schema-less design, allowing for the evolution of tables as needed, and thus is very flexible.</span></span> <span data-ttu-id="274fe-134">자세한 내용은 참조는 [ **Azure Tables** 페이지](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span><span class="sxs-lookup"><span data-stu-id="274fe-134">For more information, visit the [**Azure Tables** page](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span></span>

<span data-ttu-id="274fe-135">이 과정 설정 하 고 IoT Hub 서비스를 사용 하 여 다음 장치에서 제공 하는 데 응답을 시각화 하는 방법을 배우게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-135">This course will teach you how to setup and use the IoT Hub Service, and then visualize a response provided by a device.</span></span> <span data-ttu-id="274fe-136">이러한 개념을 사용자 지정 IoT Hub 서비스를 설치 하는 작성 하려는 경우에 적용 하는 것이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-136">It will be up to you to apply these concepts to a custom IoT Hub Service setup, which you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="274fe-137">장치 지원</span><span class="sxs-lookup"><span data-stu-id="274fe-137">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="274fe-138">과정</span><span class="sxs-lookup"><span data-stu-id="274fe-138">Course</span></span></th><th style="width:150px"> <span data-ttu-id="274fe-139"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="274fe-139"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="274fe-140"><a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="274fe-140"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="274fe-141">MR 및 Azure 313: IoT Hub Service</span><span class="sxs-lookup"><span data-stu-id="274fe-141">MR and Azure 313: IoT Hub Service</span></span></td><td style="text-align: center;"> <span data-ttu-id="274fe-142">✔️</span><span class="sxs-lookup"><span data-stu-id="274fe-142">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="274fe-143">✔️</span><span class="sxs-lookup"><span data-stu-id="274fe-143">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="274fe-144">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="274fe-144">Prerequisites</span></span>

<span data-ttu-id="274fe-145">Microsoft HoloLens 비롯 한 혼합된 현실 등을 사용 하 여 개발 하는 것에 대 한 최신 필수 구성 요소 참조를 [도구를 설치](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) 문서.</span><span class="sxs-lookup"><span data-stu-id="274fe-145">For the most up-to-date prerequisites for developing with mixed reality, including with the Microsoft HoloLens, visit the [Install the tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) article.</span></span>

> [!NOTE]
> <span data-ttu-id="274fe-146">이 자습서는 Python 사용 하 여 기본 경험이 있는 개발자를 위한 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-146">This tutorial is designed for developers who have basic experience with Python.</span></span> <span data-ttu-id="274fe-147">또한 주의 필수 구성 요소 및이 문서에서 작성 된 지침을 나타내는 새로운 테스트 되었으며 (2018 년 7 월) 작성 시점에 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-147">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="274fe-148">내에서 나열 된 사용 가능한 최신 소프트웨어를 사용 하는 합니다 [도구를 설치](install-the-tools.md) 없습니다 가정는이 과정에서 정보를 완벽 하 게 일치 항목에서 찾을 수 아래에 나열 된 것 보다 최신 소프트웨어 하지만 문서입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-148">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than that listed below.</span></span>

<span data-ttu-id="274fe-149">다음 하드웨어 및 소프트웨어가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-149">The following hardware and software is required:</span></span>

- <span data-ttu-id="274fe-150">Windows 10 Fall Creators Update (또는 이상), **개발자 모드가 사용 하도록 설정**</span><span class="sxs-lookup"><span data-stu-id="274fe-150">Windows 10 Fall Creators Update (or later), **Developer Mode enabled**</span></span>

    > [!WARNING]
    > <span data-ttu-id="274fe-151">Windows 10 Home Edition에서 Hyper-v를 사용 하 여 가상 컴퓨터를 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-151">You cannot run a Virtual Machine using Hyper-V on Windows 10 Home Edition.</span></span>

- <span data-ttu-id="274fe-152">Windows 10 SDK (최신 버전)</span><span class="sxs-lookup"><span data-stu-id="274fe-152">Windows 10 SDK (latest version)</span></span>
- <span data-ttu-id="274fe-153">HoloLens, A **개발자 모드가 사용 하도록 설정**</span><span class="sxs-lookup"><span data-stu-id="274fe-153">A HoloLens, **Developer Mode enabled**</span></span>
- <span data-ttu-id="274fe-154">Visual Studio 2017.15.4 (Azure 클라우드 탐색기를 액세스 하는 데만)</span><span class="sxs-lookup"><span data-stu-id="274fe-154">Visual Studio 2017.15.4 (Only used to access the Azure Cloud Explorer)</span></span>
- <span data-ttu-id="274fe-155">Azure 및 IoT Hub 서비스를 인터넷 액세스</span><span class="sxs-lookup"><span data-stu-id="274fe-155">Internet Access for Azure, and for IoT Hub Service.</span></span> <span data-ttu-id="274fe-156">자세한 내용은 따르세요이 [IoT Hub 서비스 페이지에 링크](https://azure.microsoft.com/en-au/services/iot-hub/)</span><span class="sxs-lookup"><span data-stu-id="274fe-156">For more information, please follow this [link to IoT Hub Service page](https://azure.microsoft.com/en-au/services/iot-hub/)</span></span>
- <span data-ttu-id="274fe-157">기계 학습 모델입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-157">A machine learning model.</span></span> <span data-ttu-id="274fe-158">모델을 사용 하도록 사용자 고유의 준비 되지 않은 경우 [이 과정을 통해 제공 되는 모델을 사용할 수 있습니다](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip)합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-158">If you do not have your own ready to use model, [you can use the model provided with this course](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).</span></span>
- <span data-ttu-id="274fe-159">**Hyper-v** 소프트웨어가 Windows 10 개발 컴퓨터에서 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-159">**Hyper-V** software enabled on your Windows 10 development machine.</span></span>
- <span data-ttu-id="274fe-160">개발 컴퓨터 또는 또는 Ubuntu 16.4, 18.4를 실행 중인 가상 머신에 Linux (Ubuntu 16.4 또는 18.4)를 실행 하는 별도 컴퓨터를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-160">A Virtual Machine running Ubuntu (16.4 or 18.4), running on your development machine or alternatively you can use a separate computer running Linux (Ubuntu 16.4 or 18.4).</span></span> <span data-ttu-id="274fe-161">Hyper-v를 사용 하 여 Windows에서 VM을 만드는 방법에 대 한 자세한 내용은 찾을 수 있습니다 합니다 [장 "시작 하기 전에"](#before-you-start). ( https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).</span><span class="sxs-lookup"><span data-stu-id="274fe-161">You can find more information on how to create a VM on Windows using Hyper-V in the ["Before you Start" chapter](#before-you-start).(https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).</span></span>  



### <a name="before-you-start"></a><span data-ttu-id="274fe-162">시작하기 전 주의 사항</span><span class="sxs-lookup"><span data-stu-id="274fe-162">Before you start</span></span>

1. <span data-ttu-id="274fe-163">설정 하 고 여 HoloLens를 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-163">Set up and test your HoloLens.</span></span> <span data-ttu-id="274fe-164">에 HoloLens 등록 설정을 지원 해야 하는 경우 [HoloLens 설치 문서를 참조 하도록](https://docs.microsoft.com/hololens/hololens-setup)합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-164">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span>
2. <span data-ttu-id="274fe-165">수행 하는 것이 좋습니다 **보정** 하 고 **센서 튜닝** (때로는 도움이 각 사용자에 대 한 이러한 작업을 수행) 새 HoloLens 앱 개발을 시작할 때입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-165">It is a good idea to perform **Calibration** and **Sensor Tuning** when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span>

<span data-ttu-id="274fe-166">보정에 대 한 도움말을 따라이 [HoloLens 보정 문서 링크](calibration.md#hololens)합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-166">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="274fe-167">센서 조정에 대 한 도움말을 따라이 [HoloLens 센서 튜닝 문서 링크](sensor-tuning.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-167">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

3. <span data-ttu-id="274fe-168">설정에 **Ubuntu 가상 머신을** 사용 하 여 **Hyper-v**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-168">Set up your **Ubuntu Virtual Machine** using **Hyper-V**.</span></span> <span data-ttu-id="274fe-169">다음 리소스는 프로세스를 도와 됩니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-169">The following resources will help you with the process.</span></span>
    1.  <span data-ttu-id="274fe-170">먼저이 링크를 따라 [16.04.4 Ubuntu LTS (Xenial Xerus) ISO 다운로드](http://au.releases.ubuntu.com/16.04/)합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-170">First, follow this link to [download the Ubuntu 16.04.4 LTS (Xenial Xerus) ISO](http://au.releases.ubuntu.com/16.04/).</span></span> <span data-ttu-id="274fe-171">선택 된 **64 비트 (AMD64) PC 데스크톱 이미지**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-171">Select the **64-bit PC (AMD64) desktop image**.</span></span>
    2.  <span data-ttu-id="274fe-172">했는지 **Hyper-v** Windows 10 컴퓨터에서 사용 하도록 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-172">Make sure **Hyper-V** is enabled on your Windows 10 machine.</span></span> <span data-ttu-id="274fe-173">지침에 대 한이 링크를 따를 수 있습니다 [를 설치 하 고 Windows 10에서 Hyper-v를 사용 하도록 설정 하면](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-173">You can follow this link for guidance on [installing and enabling Hyper-V on Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).</span></span>
    3.  <span data-ttu-id="274fe-174">Hyper-v를 시작 하 고 새 Ubuntu VM을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-174">Start Hyper-V and create a new Ubuntu VM.</span></span> <span data-ttu-id="274fe-175">이 링크를 따를 수를 [하이퍼-V를 사용 하 여 VM을 만드는 방법에 대 한 단계별 가이드](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine)합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-175">You can follow this link for a [step by step guide on how to create a VM with Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine).</span></span> <span data-ttu-id="274fe-176">요청이 있을 때 **"부팅 이미지 파일에서 운영 체제 설치"** 를 선택 합니다 **Ubuntu ISO** 이전 다운로드를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-176">When requested to **"Install an operating system from a bootable image file"**, select the **Ubuntu ISO** you have download earlier.</span></span>

    > [!NOTE]
    > <span data-ttu-id="274fe-177">사용 하 여 **Hyper-v 빠른 생성** 제안 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-177">Using **Hyper-V Quick Create** is not suggested.</span></span>  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a><span data-ttu-id="274fe-178">1 장-Custom Vision 모델 검색</span><span class="sxs-lookup"><span data-stu-id="274fe-178">Chapter 1 - Retrieve the Custom Vision model</span></span>

<span data-ttu-id="274fe-179">이 과정에 대 한 액세스 해야 합니다는 [미리 빌드된 사용자 지정 비전 모델](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) 키보드 및 마우스에서 이미지를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-179">With this course you will have access to a [pre-built Custom Vision model](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) that detects keyboards and mice from images.</span></span> <span data-ttu-id="274fe-180">이 사용 하는 경우 진행 [Chapter 2](#chapter-2---the-container-registry-service)합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-180">If you use this, proceed to [Chapter 2](#chapter-2---the-container-registry-service).</span></span>

<span data-ttu-id="274fe-181">그러나 사용자 고유의 사용자 지정 비전 모델을 사용 하려는 경우 다음이 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-181">However, you can follow these steps if you wish to use your own Custom Vision model:</span></span>

1. <span data-ttu-id="274fe-182">사용자 **사용자 지정 비전 프로젝트** 로 이동 합니다 **성능** 탭 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-182">In your **Custom Vision Project** go to the **Performance** tab.</span></span>

    > [!WARNING]
    > <span data-ttu-id="274fe-183">모델 사용 해야 합니다는 *compact* 도메인 모델 내보내기에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-183">Your model must use a *compact* domain, to export the model.</span></span> <span data-ttu-id="274fe-184">프로젝트에 대 한 설정에서 도메인 모델을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-184">You can change your models domain in the settings for your project.</span></span>

    ![성능 탭](images/AzureLabs-Lab313-01.png)

2. <span data-ttu-id="274fe-186">선택 된 **반복** 내보내고 클릭 하려는 **내보내기**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-186">Select the **Iteration** you want to export and click on **Export**.</span></span> <span data-ttu-id="274fe-187">블레이드가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-187">A blade will appear.</span></span>

    ![내보내기 블레이드](images/AzureLabs-Lab313-02.png)

3. <span data-ttu-id="274fe-189">블레이드 **Docker 파일**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-189">In the blade click **Docker File**.</span></span>

    ![docker를 선택 합니다.](images/AzureLabs-Lab313-03.png)

4. <span data-ttu-id="274fe-191">클릭 **Linux** 드롭 다운 메뉴를 클릭 **다운로드**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-191">Click **Linux** in the drop-down menu and then click on **Download**.</span></span>

    ![다운로드를 클릭 합니다.](images/AzureLabs-Lab313-04.png)

5. <span data-ttu-id="274fe-193">콘텐츠를 압축을 풉니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-193">Unzip the content.</span></span> <span data-ttu-id="274fe-194">이 과정의 뒷부분에 나오는 것을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-194">You will use it later in this course.</span></span>

## <a name="chapter-2---the-container-registry-service"></a><span data-ttu-id="274fe-195">2 장-컨테이너 레지스트리 서비스</span><span class="sxs-lookup"><span data-stu-id="274fe-195">Chapter 2 - The Container Registry Service</span></span>

<span data-ttu-id="274fe-196">합니다 **컨테이너 레지스트리 서비스** 저장소 컨테이너를 호스트 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-196">The **Container Registry Service** is the repository used to host your containers.</span></span>

<span data-ttu-id="274fe-197">**IoT Hub 서비스** 는 빌드를 사용 하는이 과정에서는 가리킵니다 **컨테이너 레지스트리 서비스** Edge 장치에 배포 하는 데 컨테이너를 가져오려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-197">The **IoT Hub Service** that you will build and use in this course, refers to **Container Registry Service** to obtain the containers to deploy in your Edge Device.</span></span>

1. <span data-ttu-id="274fe-198">먼저이 따라 [Azure 포털 링크가](https://portal.azure.com/), 자격 증명을 사용 하 여 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-198">First, follow this [link to the Azure Portal](https://portal.azure.com/), and login with your credentials.</span></span>

2. <span data-ttu-id="274fe-199">로 이동 **리소스 만들기** 를 찾아서 **Container Registry**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-199">Go to **Create a resource** and look for **Container Registry**.</span></span>

    ![컨테이너 레지스트리](images/AzureLabs-Lab313-05.png)

3. <span data-ttu-id="274fe-201">클릭할 **만들**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-201">Click on **Create**.</span></span>

    ![](images/AzureLabs-Lab313-06.png)

4. <span data-ttu-id="274fe-202">서비스 설치 매개 변수를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-202">Set the Service setup parameters:</span></span>

    1. <span data-ttu-id="274fe-203">이 예제 프로젝트의 이름을 삽입 해당 호출 **IoTCRegistry**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-203">Insert a name for your project, In this example its called **IoTCRegistry**.</span></span>

    2. <span data-ttu-id="274fe-204">선택 된 **리소스 그룹** 하거나 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-204">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="274fe-205">리소스 그룹에는 모니터링, 프로 비전, 액세스 제어 및 Azure 자산 모음에 대 한 청구를 관리 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-205">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="274fe-206">좋습니다 일반적인 리소스 그룹에서 (예: 이러한 교육 과정) 예: 단일 프로젝트와 연결 된 Azure 서비스를 모두 유지).</span><span class="sxs-lookup"><span data-stu-id="274fe-206">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

    3. <span data-ttu-id="274fe-207">서비스의 위치를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-207">Set the location of the Service.</span></span>

    4. <span data-ttu-id="274fe-208">설정 **관리자** 하 **사용**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-208">Set **Admin user** to **Enable**.</span></span>

    5. <span data-ttu-id="274fe-209">설정할 **SKU** 하 **기본**입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-209">Set **SKU** to **Basic**.</span></span> 

    ![](images/AzureLabs-Lab313-07.png)

5. <span data-ttu-id="274fe-210">클릭 **만들기** 서비스를 만들어야 할 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-210">Click **Create** and wait for the Services to be created.</span></span> 

6. <span data-ttu-id="274fe-211">알림을 만드는 데 성공 알리는 팝업 되 면 합니다 *Container Registry*, 클릭 **리소스로 이동** 서비스 페이지로 리디렉션되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-211">Once the notification pops up informing you of the successful creation of the *Container Registry*, click on **Go to resource** to be redirected to your Service page.</span></span>

    ![](images/AzureLabs-Lab313-08.png)

7. <span data-ttu-id="274fe-212">에 *Container Registry* 서비스 페이지를 클릭 **선택키가**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-212">In the *Container Registry* Service page, click on **Access keys**.</span></span>

8. <span data-ttu-id="274fe-213">다음 매개 변수를 기록 (에 메모장을 사용할 수 없습니다)를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-213">Take note (you could use your Notepad) of the following parameters:</span></span>
    1. <span data-ttu-id="274fe-214">**Login Server**</span><span class="sxs-lookup"><span data-stu-id="274fe-214">**Login Server**</span></span>
    2. <span data-ttu-id="274fe-215">**사용자 이름**</span><span class="sxs-lookup"><span data-stu-id="274fe-215">**Username**</span></span>
    3. <span data-ttu-id="274fe-216">**암호**</span><span class="sxs-lookup"><span data-stu-id="274fe-216">**Password**</span></span>

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a><span data-ttu-id="274fe-217">3 장-IoT Hub 서비스</span><span class="sxs-lookup"><span data-stu-id="274fe-217">Chapter 3 - The IoT Hub Service</span></span>

<span data-ttu-id="274fe-218">이제 설치 하 고 만들기를 시작 하 **IoT Hub 서비스**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-218">Now you will begin the creation and setup of your **IoT Hub Service**.</span></span>

1. <span data-ttu-id="274fe-219">아직 로그인 하지 않은, 경우에 로그인 합니다 [Azure Portal](https://portal.azure.com)합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-219">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2.  <span data-ttu-id="274fe-220">일단 로그인 하면 클릭할 **리소스 만들기** 왼쪽 위에서 모서리 및 검색 **IoT Hub**, 클릭 **Enter**.</span><span class="sxs-lookup"><span data-stu-id="274fe-220">Once logged in, click on **Create a resource** in the top left corner, and search for **IoT Hub**, and click **Enter**.</span></span>

 ![저장소 계정에 대 한 검색](images/AzureLabs-Lab313-10.png)

3.  <span data-ttu-id="274fe-222">새 페이지에 대 한 설명을 제공 합니다는 **저장소 계정** 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-222">The new page will provide a description of the **Storage account** Service.</span></span> <span data-ttu-id="274fe-223">이 프롬프트의 왼쪽 아래에 있는 클릭 합니다 **만들기** 단추를 서비스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-223">At the bottom left of this prompt, click the **Create** button, to create an instance of this Service.</span></span>

    ![저장소 인스턴스 만들기](images/AzureLabs-Lab313-11.png)

4.  <span data-ttu-id="274fe-225">클릭 한 후 **만들기**를 패널에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-225">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="274fe-226">선택 된 **리소스 그룹** 하거나 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-226">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="274fe-227">리소스 그룹에는 모니터링, 프로 비전, 액세스 제어 및 Azure 자산 모음에 대 한 청구를 관리 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-227">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="274fe-228">좋습니다 일반적인 리소스 그룹에서 (예: 이러한 교육 과정) 예: 단일 프로젝트와 연결 된 Azure 서비스를 모두 유지).</span><span class="sxs-lookup"><span data-stu-id="274fe-228">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="274fe-229">추가 하려는 경우 Azure 리소스 그룹에 대 한 따르세요이 [리소스 그룹을 관리 하는 방법에 대 한 링크](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-229">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>


    2. <span data-ttu-id="274fe-230">적절 한 선택 **위치** (이 과정에서 만든 모든 서비스에서 동일한 위치를 사용).</span><span class="sxs-lookup"><span data-stu-id="274fe-230">Select an appropriate **Location** (Use the same location across all the Services you create in this course).</span></span>

    3. <span data-ttu-id="274fe-231">원하는 삽입 **이름을** 이 서비스 인스턴스에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-231">Insert your desired **Name** for this Service instance.</span></span>    

5.  <span data-ttu-id="274fe-232">페이지의 맨 아래에서 클릭 **다음: 크기 조정 및 규모**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-232">On the bottom of the page click on **Next: Size and scale**.</span></span>

    ![저장소 인스턴스 만들기](images/AzureLabs-Lab313-12.png)

6.  <span data-ttu-id="274fe-234">이 페이지에서 선택 하 여 **가격 책정 및 크기 계층** (첫 번째 IoT Hub 서비스 인스턴스에 인 경우 무료 계층 사용 가능 해야 할).</span><span class="sxs-lookup"><span data-stu-id="274fe-234">In this page, select your **Pricing and scale tier** (if this is your first IoT Hub Service instance, a free tier should be available to you).</span></span>  

7.  <span data-ttu-id="274fe-235">클릭할 **검토 + 만들기**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-235">Click on **Review + Create**.</span></span>

    ![저장소 인스턴스 만들기](images/AzureLabs-Lab313-13.png)

8.  <span data-ttu-id="274fe-237">설정을 검토 하 고 클릭 **만들기**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-237">Review your settings and click on **Create**.</span></span>

    ![저장소 인스턴스 만들기](images/AzureLabs-Lab313-14.png)

9. <span data-ttu-id="274fe-239">알림이 성공적으로 만들어졌다고 알리는 팝업 되 면 합니다 *IoT Hub* 서비스를 클릭 **리소스로 이동** 서비스 페이지로 리디렉션되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-239">Once the notification pops up informing you of the successful creation of the *IoT Hub* Service, click on **Go to resource** to be redirected to your Service page.</span></span>

    ![저장소 인스턴스 만들기](images/AzureLabs-Lab313-15.png)

10. <span data-ttu-id="274fe-241">표시 될 때까지 왼쪽 사이드 패널을 스크롤하고 *자동 장치 관리*, 클릭 **IoT Edge**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-241">Scroll the side panel on the left until you see *Automatic Device Management*, the click on **IoT Edge**.</span></span>

    ![저장소 인스턴스 만들기](images/AzureLabs-Lab313-16.png)

11. <span data-ttu-id="274fe-243">오른쪽에 표시 되는 창에서 클릭 **IoT Edge 장치 추가**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-243">In the window that appears to the right, click on **Add IoT Edge Device**.</span></span> <span data-ttu-id="274fe-244">블레이드는 오른쪽에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-244">A blade will appear to the right.</span></span>

12. <span data-ttu-id="274fe-245">블레이드에서 새 장치에 제공 된 **장치 ID** (선택한 이름).</span><span class="sxs-lookup"><span data-stu-id="274fe-245">In the blade, provide your new device a **Device ID** (a name of your choice).</span></span> <span data-ttu-id="274fe-246">그런 다음 클릭 **저장할**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-246">Then, click **Save**.</span></span> <span data-ttu-id="274fe-247">합니다 *주* 하 고 *보조 키* 자동을 생성 해야 하는 경우 **자동 생성** 선택 됩니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-247">The *Primary* and *Secondary Keys* will auto generate, if you have **Auto Generate** ticked.</span></span>

    ![저장소 인스턴스 만들기](images/AzureLabs-Lab313-17.png)

13. <span data-ttu-id="274fe-249">다시 이동 합니다는 *IoT Edge 장치* 섹션에서는 새 장치는 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-249">You will navigate back to the *IoT Edge Devices* section, where your new device will be listed.</span></span> <span data-ttu-id="274fe-250">새 장치의 클릭 (빨간색 윤곽선이 있는 아래 이미지).</span><span class="sxs-lookup"><span data-stu-id="274fe-250">Click on your new device (outlined in red in the below image).</span></span> 

    ![저장소 인스턴스 만들기](images/AzureLabs-Lab313-18.png)

14. <span data-ttu-id="274fe-252">에 *장치 세부 정보* 나타나는 페이지 복사본을 만듭니다는 **연결 문자열** (기본 키).</span><span class="sxs-lookup"><span data-stu-id="274fe-252">On the *Device Details* page that appears, take a copy of the **Connection String** (primary key).</span></span>

    ![저장소 인스턴스 만들기](images/AzureLabs-Lab313-19.png)

15. <span data-ttu-id="274fe-254">왼쪽 패널에 돌아가서 누릅니다 *공유 액세스 정책*를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-254">Go back to the panel on the left, and click *Shared access policies*, to open it.</span></span> 

16. <span data-ttu-id="274fe-255">표시 되는 페이지에서 클릭 **iothubowner**, 블레이드 화면의 오른쪽에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-255">On the page that appears, click **iothubowner**, and a blade will appear to the right of the screen.</span></span> 

17. <span data-ttu-id="274fe-256">적어둡니다 (에: 메모장)에 **연결 문자열** (기본 키)를 설정 하는 경우 나중에 사용할 합니다 *연결 문자열* 장치에.</span><span class="sxs-lookup"><span data-stu-id="274fe-256">Take note (on your Notepad) of the **Connection string** (primary key), for later use when setting the *Connection String* to your device.</span></span>

    ![저장소 인스턴스 만들기](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a><span data-ttu-id="274fe-258">4 장-개발 환경 설정</span><span class="sxs-lookup"><span data-stu-id="274fe-258">Chapter 4 - Setting up the development environment</span></span>

<span data-ttu-id="274fe-259">만들고 모듈에 대 한 배포 하기 위해 *IoT Hub Edge*, Windows 10을 실행 하 여 개발 컴퓨터에 설치한 다음 구성 요소 필요:</span><span class="sxs-lookup"><span data-stu-id="274fe-259">In order to create and deploy modules for *IoT Hub Edge*, you will require the following components installed on your development machine running Windows 10:</span></span>

1.  <span data-ttu-id="274fe-260">[Windows 용 docker](https://store.docker.com/editions/community/docker-ce-desktop-windows), 요청을 다운로드 할 수는 계정을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-260">[Docker for Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows), it will ask you to create an account to be able to download.</span></span> 

    <span data-ttu-id="274fe-261">[![windows 용 docker 다운로드](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)</span><span class="sxs-lookup"><span data-stu-id="274fe-261">[![download docker for windows](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="274fe-262">Docker 필요 *Windows 10 PRO*를 *Enterprise 14393*, 또는 *Windows Server 2016 RTM*를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-262">Docker requires *Windows 10 PRO*, *Enterprise 14393*, or *Windows Server 2016 RTM*, to run.</span></span> <span data-ttu-id="274fe-263">다른 버전의 Windows 10을 실행 하는 경우 Docker를 사용 하 여 설치를 시도할 수 있습니다 합니다 [Docker 도구 상자](https://docs.docker.com/toolbox/toolbox_install_windows/)합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-263">If you are running other versions of Windows 10, you can try installing Docker using the [Docker Toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/).</span></span>

2.  <span data-ttu-id="274fe-264">[Python 3.6](https://www.python.org/downloads/).</span><span class="sxs-lookup"><span data-stu-id="274fe-264">[Python 3.6](https://www.python.org/downloads/).</span></span>

    <span data-ttu-id="274fe-265">[![python 3.6 다운로드](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)</span><span class="sxs-lookup"><span data-stu-id="274fe-265">[![download python 3.6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)</span></span>

3.  <span data-ttu-id="274fe-266">[Visual Studio Code (VS Code 라고도 함)](https://code.visualstudio.com/download)합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-266">[Visual Studio Code (also known as VS Code)](https://code.visualstudio.com/download).</span></span>

    <span data-ttu-id="274fe-267">[![VS Code를 다운로드 합니다.](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)</span><span class="sxs-lookup"><span data-stu-id="274fe-267">[![download VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)</span></span>

<span data-ttu-id="274fe-268">위에서 언급 한 소프트웨어를 설치한 후 컴퓨터를 다시 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-268">After installing the software mentioned above, you will need to restart your machine.</span></span>

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a><span data-ttu-id="274fe-269">5 장-Ubuntu 환경 설정</span><span class="sxs-lookup"><span data-stu-id="274fe-269">Chapter 5 - Setting up the Ubuntu environment</span></span>

<span data-ttu-id="274fe-270">이제 장치를 설정 하 이동할 수 있습니다 **Ubuntu 운영 체제를 실행 중인**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-270">Now you can move on to setting up your device **running Ubuntu OS**.</span></span> <span data-ttu-id="274fe-271">보드에 컨테이너를 배포 하는 데 필요한 소프트웨어를 설치 하려면 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-271">Follow the steps below, to install the necessary software, to deploy your containers on your board:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="274fe-272">터미널 명령을 항상 앞에 야 **sudo** 관리자 사용자로 실행 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-272">You should always precede the terminal commands with **sudo** to run as admin user.</span></span> <span data-ttu-id="274fe-273">i.e:</span><span class="sxs-lookup"><span data-stu-id="274fe-273">i.e:</span></span>
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  <span data-ttu-id="274fe-274">엽니다는 **Ubuntu 터미널**, 다음 명령을 사용 하 여 설치 하 고 **pip**:</span><span class="sxs-lookup"><span data-stu-id="274fe-274">Open the **Ubuntu Terminal**, and use the following command to install **pip**:</span></span>

    > [! 힌트]<span data-ttu-id="274fe-275"> 열 수 있습니다 *터미널* 바로 가기 키를 사용 하 여을 통해 매우 쉽게: **Ctrl + Alt + T**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-275"> You can open *Terminal* very easily through using the keyboard shortcut: **Ctrl + Alt + T**.</span></span>

    ```bash
        sudo apt-get install python-pip
    ```

2.  <span data-ttu-id="274fe-276">이 장에서 메시지가 나타날 수 있습니다에 의해 *터미널*, 장치 저장소를 사용할 수 있는 권한 및 사용자를 입력할 **y/n** (예 또는 아니요), 형식 **'y'** , 누릅니다는 **Enter** 적용할 키입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-276">Throughout this Chapter, you may be prompted, by *Terminal*, for permission to use your device storage, and for you to input **y/n** (yes or no), type **'y'**, and then press the **Enter** key, to accept.</span></span>

3.  <span data-ttu-id="274fe-277">명령이 완료 되 면 명령을 사용 하 여 다음 설치 **curl**:</span><span class="sxs-lookup"><span data-stu-id="274fe-277">Once that command has completed, use the following command to install **curl**:</span></span>

    ```bash
        sudo apt install curl
    ```

4.  <span data-ttu-id="274fe-278">한 번 **pip** 하 고 **curl** 는 설치 명령을 사용 하 여 다음 설치를 **IoT Edge 런타임**,이 배포 하 고 보드에서 모듈을 제어 하는 데 필요한:</span><span class="sxs-lookup"><span data-stu-id="274fe-278">Once **pip** and **curl** are installed, use the following command to install the **IoT Edge runtime**, this is necessary to deploy and control the modules on your board:</span></span>

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

5. <span data-ttu-id="274fe-279">이 시점에서 메시지가 표시 됩니다 열어야를 *런타임 구성 파일*삽입 하는 **장치 연결 문자열**에 메모장을 기록해 둔 만들 때를 **IoT Hub 서비스**  ([3 장의 14 단계에서](#chapter-3---the-iot-hub-service)).</span><span class="sxs-lookup"><span data-stu-id="274fe-279">At this point you will be prompted to open up the *runtime config file*, to insert the **Device Connection String**, that you noted down (in your Notepad), when creating the **IoT Hub Service** ([at step 14, of Chapter 3](#chapter-3---the-iot-hub-service)).</span></span> <span data-ttu-id="274fe-280">해당 파일을 열고 터미널에서 다음 줄을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-280">Run the following line on the terminal to open that file:</span></span>

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. <span data-ttu-id="274fe-281">합니다 **config.yaml** 파일 표시, 편집 준비가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-281">The **config.yaml** file will be displayed, ready for you to edit:</span></span>

    > [!WARNING]
    > <span data-ttu-id="274fe-282">이 파일을 열면 것은 다소 복잡할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-282">When this file opens, it may be somewhat confusing.</span></span> <span data-ttu-id="274fe-283">텍스트 내에서이 파일을 편집 해야 합니다 *터미널* 자체입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-283">You will be text editing this file, within the *Terminal* itself.</span></span> 

    1.  <span data-ttu-id="274fe-284">키보드의 화살표 키를 사용 하 여 스크롤합니다 아래로 (해야 간단한 방식으로 아래로 스크롤하여)를 포함 하는 줄에 연결할 ":</span><span class="sxs-lookup"><span data-stu-id="274fe-284">Use the arrow keys on your keyboard to scroll down (you will need to scroll down a little way), to reach the line containing":</span></span>

        <span data-ttu-id="274fe-285">" **\<여기에 장치 연결 문자열 추가 >** "입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-285">"**\<ADD DEVICE CONNECTION STRING HERE>**".</span></span>

    2. <span data-ttu-id="274fe-286">대체 줄 **대괄호를 포함 하 여**를 사용 하 여 합니다 **장치 연결 문자열** 이전에 기록한 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-286">Substitute line, **including the brackets**, with the **Device Connection String** you have noted earlier.</span></span>

7. <span data-ttu-id="274fe-287">키를 눌러 키보드에서 현재 위치에서 연결 문자열을 사용 하 여 합니다 **Ctrl-x** 키 파일을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-287">With your Connection String in place, on your keyboard, press the **Ctrl-X** keys to save the file.</span></span> <span data-ttu-id="274fe-288">입력 하 여 것인지 묻습니다 **Y**합니다. 누릅니다 합니다 **Enter** 키를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-288">It will ask you to confirm by typing **Y**. Then, press the **Enter** key, to confirm.</span></span> <span data-ttu-id="274fe-289">일반 다시 이동 *터미널*합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-289">You will go back to the regular *Terminal*.</span></span> 

8. <span data-ttu-id="274fe-290">이러한 명령은 모든 성공적으로 실행, 되 면 설치 됩니다 합니다 **IoT Edge 런타임은**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-290">Once these commands have all run successfully, you will have installed the **IoT Edge Runtime**.</span></span> <span data-ttu-id="274fe-291">초기화 되 면 장치 전원이 자체 모든 시간에 시작 하는 런타임과 모듈에서 배포에 대 한 대기 중인 백그라운드에서 위치를 **IoT Hub 서비스**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-291">Once initialized, the runtime will start on its own every time the device is powered up, and will sit in the background, waiting for modules to be deployed from the **IoT Hub Service**.</span></span>

9.  <span data-ttu-id="274fe-292">초기화 하려면 다음 명령줄을 실행 합니다 *IoT Edge 런타임은*:</span><span class="sxs-lookup"><span data-stu-id="274fe-292">Run the following command line to initialize the *IoT Edge Runtime*:</span></span>

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="274fe-293">위의 다시 시작 줄을 다시 실행 해야.yaml 파일을 하거나 위의 설정을 변경한 경우 내 *터미널*합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-293">If you make changes to your .yaml file, or the above setup, you will need to run the above restart line again, within *Terminal*.</span></span>

10. <span data-ttu-id="274fe-294">확인 합니다 *IoT Edge 런타임은* 다음 명령줄을 실행 하 여 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-294">Check the *IoT Edge Runtime* status by running the following command line.</span></span> <span data-ttu-id="274fe-295">런타임 상태를 사용 하 여 나타나야 **활성 (실행)** 녹색 텍스트에서입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-295">The runtime should appear with the status **active (running)** in green text.</span></span>

    ```bash
        sudo systemctl status iotedge
    ```

11. <span data-ttu-id="274fe-296">키를 눌러 합니다 **Ctrl + C** 키, 상태 페이지를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-296">Press the **Ctrl-C** keys, to exit the status page.</span></span> <span data-ttu-id="274fe-297">중인지 확인할 수 있습니다 합니다 *IoT Edge 런타임은* 다음 명령을 입력 하 여 컨테이너를 올바르게 끌어오기는:</span><span class="sxs-lookup"><span data-stu-id="274fe-297">You can verify that the *IoT Edge Runtime* is pulling the containers correctly by typing the following command:</span></span>

    ```bash
        sudo docker ps
    ```

12. <span data-ttu-id="274fe-298">2 개의 컨테이너 목록이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-298">A list with two (2) containers should appear.</span></span> <span data-ttu-id="274fe-299">이들은 (edgeAgent 및 edgehub 라는) IoT Hub 서비스에서 자동으로 만들어지는 기본 모듈입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-299">These are the default modules that are automatically created by the IoT Hub Service (edgeAgent and edgeHub).</span></span> <span data-ttu-id="274fe-300">을 만들고 사용자 고유의 모듈을 배포 함으로써 기본 아래이 목록에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-300">Once you create and deploy your own modules, they will appear in this list, underneath the default ones.</span></span>

## <a name="chapter-6---install-the-extensions"></a><span data-ttu-id="274fe-301">확장을 설치-6 장</span><span class="sxs-lookup"><span data-stu-id="274fe-301">Chapter 6 - Install the extensions</span></span>

> [!IMPORTANT]
> <span data-ttu-id="274fe-302">다음 몇 장을 (6-9)는 Windows 10 컴퓨터에서 수행 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-302">The next few Chapters (6-9) are to be performed on your Windows 10 machine.</span></span>

1. <span data-ttu-id="274fe-303">오픈 **VS Code**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-303">Open **VS Code**.</span></span>

2. <span data-ttu-id="274fe-304">클릭 합니다 **확장** (사각형) 단추에서 왼쪽된 표시줄의 VS Code에서 열려는 합니다 **확장 패널**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-304">Click on the **Extensions** (square) button on the left bar of VS Code, to open the **Extensions panel**.</span></span>

3. <span data-ttu-id="274fe-305">검색 한 대로 하 고 설치, 다음 확장 (아래 이미지에 표시 됨):</span><span class="sxs-lookup"><span data-stu-id="274fe-305">Search for, and install, the following extensions (as shown in the image below):</span></span>

    1. <span data-ttu-id="274fe-306">Azure IoT Edge</span><span class="sxs-lookup"><span data-stu-id="274fe-306">Azure IoT Edge</span></span>
    2. <span data-ttu-id="274fe-307">Azure IoT 도구 키트</span><span class="sxs-lookup"><span data-stu-id="274fe-307">Azure IoT Toolkit</span></span>
    3. <span data-ttu-id="274fe-308">Docker</span><span class="sxs-lookup"><span data-stu-id="274fe-308">Docker</span></span>   

    ![컨테이너 만들기](images/AzureLabs-Lab313-24.png)

4. <span data-ttu-id="274fe-310">확장이 설치 되 면 닫았다가 다시 VS Code를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-310">Once the extensions are installed, close and re-open VS Code.</span></span>

5. <span data-ttu-id="274fe-311">VS Code를 사용 하 여 한 번 더를 열고 이동할 **뷰** > **통합된 터미널**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-311">With VS Code open once more, navigate to **View** > **Integrated terminal**.</span></span>

6. <span data-ttu-id="274fe-312">이제 설치할 **Cookiecutter**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-312">You will now install **Cookiecutter**.</span></span> <span data-ttu-id="274fe-313">터미널에서 다음 bash 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-313">In the terminal run the following bash command:</span></span>

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > [! 힌트]<span data-ttu-id="274fe-314">이이 명령 사용 하 여 문제가 있는 경우:</span><span class="sxs-lookup"><span data-stu-id="274fe-314"> If you have trouble with this command:</span></span> 
    >1. <span data-ttu-id="274fe-315">VS Code 및/또는 컴퓨터를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-315">Restart VS Code, and/ or your computer.</span></span>
    >2. <span data-ttu-id="274fe-316">전환 해야 할 수도 있습니다는 **VS Code 터미널** 예: Python을 설치 하는 데 사용할 위치로 **Powershell** (특히 경우 Python 환경을 이미 컴퓨터에 설치 된).</span><span class="sxs-lookup"><span data-stu-id="274fe-316">It might be necessary to switch the **VS Code Terminal** to the one you have been using to install Python, i.e. **Powershell** (especially in case the Python environment was already installed on your machine).</span></span> <span data-ttu-id="274fe-317">터미널을 열고 터미널의 오른쪽에 있는 메뉴 드롭다운을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-317">With the Terminal open, you will find the drop down menu on the right side of the Terminal.</span></span>
     <span data-ttu-id="274fe-318">![컨테이너 만들기](images/AzureLabs-Lab313-24b.png)</span><span class="sxs-lookup"><span data-stu-id="274fe-318">![Create your container](images/AzureLabs-Lab313-24b.png)</span></span> 
    >3. <span data-ttu-id="274fe-319">있는지 확인 합니다 **Python** 설치 경로으로 추가 됩니다 **환경 변수** 컴퓨터에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-319">Make sure the **Python** installation path is added as **Environment Variable** on your machine.</span></span> <span data-ttu-id="274fe-320">Cookiecutter에는 같은 위치 패스의 일부 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-320">Cookiecutter should be part of the same location path.</span></span> <span data-ttu-id="274fe-321">이 수행 하십시오 [환경 변수에 대 한 자세한 내용은 링크](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx),</span><span class="sxs-lookup"><span data-stu-id="274fe-321">Please follow this [link for more information on Environment Variables](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx),</span></span> 

7. <span data-ttu-id="274fe-322">한 번 **Cookiecutter** 설치를 완료 하 여 컴퓨터를 다시 시작 해야 되도록 **Cookiecutter** 시스템 환경 내에서 명령으로 인식 됩니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-322">Once **Cookiecutter** has finished installing, you should restart your machine, so that **Cookiecutter** is recognized as a command, within your System's environment.</span></span>

## <a name="chapter-7---create-your-container-solution"></a><span data-ttu-id="274fe-323">7-장 컨테이너 솔루션 만들기</span><span class="sxs-lookup"><span data-stu-id="274fe-323">Chapter 7 - Create your container solution</span></span>

<span data-ttu-id="274fe-324">모듈에 푸시를 사용 하 여 컨테이너를 생성 해야 하는 시점에서 *Container Registry*합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-324">At this point, you need to create the container, with the module, to be pushed into the *Container Registry*.</span></span> <span data-ttu-id="274fe-325">컨테이너 밀어 넣었으면를 사용 하 여는 *IoT Hub Edge* 실행 되는 장치에 배포할 서비스를 *IoT Edge 런타임*합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-325">Once you have pushed your container, you will use the *IoT Hub Edge* Service to deploy it to your device, which is running the *IoT Edge runtime*.</span></span>

1. <span data-ttu-id="274fe-326">VS Code에서 클릭 **뷰** > **명령 팔레트**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-326">From VS Code, click **View** > **Command palette**.</span></span>

2. <span data-ttu-id="274fe-327">팔레트에서 검색 하 고 실행 **Azure IoT Edge: 새 Iot Edge 솔루션**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-327">In the palette, search and run **Azure IoT Edge: New Iot Edge Solution**.</span></span>

3. <span data-ttu-id="274fe-328">솔루션을 만들려면 원하는 위치로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-328">Browse into a location where you want to create your solution.</span></span> <span data-ttu-id="274fe-329">키를 눌러 합니다 **Enter** 키 위치를 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-329">Press the **Enter** key, to accept the location.</span></span>

4. <span data-ttu-id="274fe-330">솔루션에는 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-330">Give a name to your solution.</span></span> <span data-ttu-id="274fe-331">키를 누릅니다 합니다 **Enter** 키에 제공 된 이름을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-331">Press the **Enter** key, to confirm your provided name.</span></span>

5. <span data-ttu-id="274fe-332">이제 솔루션에 대 한 템플릿 프레임 워크를 선택 하 라는 메시지가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-332">Now you will be prompted to choose the template framework for your solution.</span></span> <span data-ttu-id="274fe-333">클릭 **Python 모듈**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-333">Click **Python Module**.</span></span> <span data-ttu-id="274fe-334">키를 눌러 합니다 **Enter** 키를이 선택을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-334">Press the **Enter** key, to confirm this choice.</span></span>

6. <span data-ttu-id="274fe-335">모듈 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-335">Give a name to your module.</span></span> <span data-ttu-id="274fe-336">키를 눌러 합니다 **Enter** 모듈의 이름을 확인 하려면 키입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-336">Press the **Enter** key, to confirm the name of your module.</span></span> <span data-ttu-id="274fe-337">나중에 사용 되므로 기록해 둡니다 (에: 메모장)와 모듈 이름을 했는지를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-337">Make sure to take a note (with your Notepad) of the module name, as it is used later.</span></span>

7. <span data-ttu-id="274fe-338">미리 작성 된 알 수 있습니다 *Docker 이미지 리포지토리도* 주소 팔레트에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-338">You will notice a pre-built *Docker Image Repository* address will appear on the palette.</span></span> <span data-ttu-id="274fe-339">이 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-339">It will look like:</span></span>

    <span data-ttu-id="274fe-340">**localhost:5000 /-NAME 모듈-** 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-340">**localhost:5000/-THE NAME OF YOUR MODULE-**.</span></span> 

8. <span data-ttu-id="274fe-341">삭제 **localhost:5000**, 및 해당 위치 삽입 된 *Container Registry* **로그인 서버** 주소를 만들 때 적어 둔는 **컨테이너 레지스트리 서비스** ([Chapter 2의 8 단계에서](#chapter-2---the-container-registry-service)).</span><span class="sxs-lookup"><span data-stu-id="274fe-341">Delete **localhost:5000**, and in its place insert the *Container Registry* **Login Server** address, which you noted when creating the **Container Registry Service** ([in step 8, of Chapter 2](#chapter-2---the-container-registry-service)).</span></span> <span data-ttu-id="274fe-342">키를 눌러 합니다 **Enter** 주소 확인 하려면 키입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-342">Press the **Enter** key, to confirm the address.</span></span>

9. <span data-ttu-id="274fe-343">이 시점에서 Python 모듈에 대 한 템플릿이 포함 된 솔루션이 만들어지고 해당 구조에 표시 됩니다는 **탐색 탭**, VS Code 화면 왼쪽에서의 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-343">At this point, the solution containing the template for your Python module will be created and its structure will be displayed in the **Explore Tab**, of VS Code, on the left side of the screen.</span></span> <span data-ttu-id="274fe-344">경우는 **탐색 탭** 가 열려 있지 않은 열 수 있습니다 왼쪽 모음에서 맨 단추를 클릭 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-344">If the **Explore Tab** is not open, you can open it by clicking the top-most button, in the bar on the left.</span></span>

    ![컨테이너 만들기](images/AzureLabs-Lab313-25.png)

10. <span data-ttu-id="274fe-346">이 장에서 마지막 단계는 클릭 하 고 엽니다는 **.env 파일**, 내에서 **탐색 탭**, 추가 *Container Registry* **username** 하 고 **암호**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-346">The last step for this Chapter, is to click and open the **.env file**, from within the **Explore Tab**, and add your *Container Registry* **username** and **password**.</span></span> <span data-ttu-id="274fe-347">Git에서이 파일은 무시 됩니다. 하지만 컨테이너는 액세스 자격 증명을 설정 하는 데 빌드에는 **컨테이너 레지스트리 서비스**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-347">This file is ignored by git, but on building the container, will set the credentials to access the **Container Registry Service**.</span></span>

    ![컨테이너 만들기](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a><span data-ttu-id="274fe-349">8 장-컨테이너 솔루션이 편집</span><span class="sxs-lookup"><span data-stu-id="274fe-349">Chapter 8 - Editing your container solution</span></span>

<span data-ttu-id="274fe-350">이제 다음 파일을 업데이트 하 여 컨테이너 솔루션을 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-350">You will now complete the container solution, by updating the following files:</span></span>

- <span data-ttu-id="274fe-351">*주요<span></span>.py* python 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-351">*main<span></span>.py* python script.</span></span>
- <span data-ttu-id="274fe-352">*requirements.txt*.</span><span class="sxs-lookup"><span data-stu-id="274fe-352">*requirements.txt*.</span></span>
- <span data-ttu-id="274fe-353">*deployment.template.json*.</span><span class="sxs-lookup"><span data-stu-id="274fe-353">*deployment.template.json*.</span></span>
- <span data-ttu-id="274fe-354">*Dockerfile.amd64*</span><span class="sxs-lookup"><span data-stu-id="274fe-354">*Dockerfile.amd64*</span></span>

<span data-ttu-id="274fe-355">만들어 합니다 *이미지* 이미지에 대해 일치를 확인 하려면 python 스크립트에서 사용 하는 폴더에 *사용자 지정 비전 모델*합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-355">You will then create the *images* folder, used by the python script to check for images to match against your *Custom Vision model*.</span></span> <span data-ttu-id="274fe-356">마지막으로 추가 합니다는 *labels.txt* 모델을 읽을 수 있도록 파일 및 *model.pb* 모델 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-356">Lastly, you will add the *labels.txt* file, to help read your model, and the *model.pb* file, which is your model.</span></span>

1. <span data-ttu-id="274fe-357">VS Code를 사용 하 여 열고 모듈 폴더로 이동한 라는 스크립트를 검색할 **주<span></span>.py**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-357">With VS Code open, navigate to your module folder, and look for the script called **main<span></span>.py**.</span></span> <span data-ttu-id="274fe-358">열을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-358">Double-click to open it.</span></span>

2. <span data-ttu-id="274fe-359">파일의 콘텐츠를 삭제 하 고 다음 코드를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-359">Delete the content of the file and insert the following code:</span></span>

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

3.  <span data-ttu-id="274fe-360">라는 파일을 열면 **requirements.txt**, 다음을 사용 하 여 해당 콘텐츠를 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-360">Open the file called **requirements.txt**, and substitute its content with the following:</span></span>

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  <span data-ttu-id="274fe-361">라는 파일을 열면 **deployment.template.json**, 해당 콘텐츠 다음 대체 된 아래 지침:</span><span class="sxs-lookup"><span data-stu-id="274fe-361">Open the file called **deployment.template.json**, and substitute its content following the below guideline:</span></span>

    1. <span data-ttu-id="274fe-362">사용자 고유 JSON 구조를 해야 하므로 (예를 복사) 대신 직접 편집 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-362">Because you will have your own, unique, JSON structure, you will need to edit it by hand (rather than copying an example).</span></span> <span data-ttu-id="274fe-363">손쉽게이 사용 하 여는 아래 이미지를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-363">To make this easy, use the below image as a guide.</span></span>
    2. <span data-ttu-id="274fe-364">사용자 자신의를 다르게 영역 수는 있지만 **변경 하지 않아야 노란색으로 강조 표시 된**.</span><span class="sxs-lookup"><span data-stu-id="274fe-364">Areas which will look different to yours, but which you **should NOT change are highlighted yellow**.</span></span>
    3. <span data-ttu-id="274fe-365">**를 삭제 해야 하는 섹션에는 강조 표시 된 빨간색은입니다.**</span><span class="sxs-lookup"><span data-stu-id="274fe-365">**Sections which you need to delete, are a highlighted red.**</span></span>
    4. <span data-ttu-id="274fe-366">반드시 올바른 괄호를 삭제 하 고 또한 쉼표를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-366">Be careful to delete the correct brackets, and also remove the commas.</span></span>

        ![컨테이너 만들기](images/AzureLabs-Lab313-27.png)

    5. <span data-ttu-id="274fe-368">완료 된 JSON을 다음 이미지와 같습니다 (그러나에 고유한 차이점을 사용 하 여: *사용자 이름/암호/이름/모듈 참조*):</span><span class="sxs-lookup"><span data-stu-id="274fe-368">The completed JSON should look like the following image (though, with your unique differences: *username/password/module name/module references*):</span></span>

        ![컨테이너 만들기](images/AzureLabs-Lab313-28.png)

5.  <span data-ttu-id="274fe-370">라는 파일을 열면 **Dockerfile.amd64**, 다음을 사용 하 여 해당 콘텐츠를 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-370">Open the file called **Dockerfile.amd64**, and substitute its content with the following:</span></span>

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

6.  <span data-ttu-id="274fe-371">아래에 폴더를 마우스 오른쪽 단추로 클릭 **모듈** (; 이전에 제공한 이름을 더 또한 다음 예제에서는 다운 라고 *pythonmodule*)를 클릭 하 고 **새 폴더**.</span><span class="sxs-lookup"><span data-stu-id="274fe-371">Right-click on the folder beneath **modules** (it will have the name you provided previously; in the example further down, it is called *pythonmodule*), and click on **New Folder**.</span></span> <span data-ttu-id="274fe-372">폴더의 이름을 **이미지**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-372">Name the folder **images**.</span></span>

7.  <span data-ttu-id="274fe-373">폴더 안에 마우스나 키보드를 포함 하는 일부 이미지를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-373">Inside the folder, add some images containing mouse or keyboard.</span></span> <span data-ttu-id="274fe-374">이러한 이미지를 Tensorflow 모델에서 분석할 됩니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-374">Those will be the images that will be analyzed by the Tensorflow model.</span></span>

    > [!WARNING]
    > <span data-ttu-id="274fe-375">사용자 고유의 모델을 사용 하는 경우 사용자 고유의 모델 데이터를 반영 하도록 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-375">If you are using your own model, you will need to change this to reflect your own models data.</span></span>

8.  <span data-ttu-id="274fe-376">검색할 해야 합니다 **labels.txt** 및 **model.pb** 이전 다운로드 한 모델 폴더에서 파일 (사용자 고유의에서 만들어지거나 **Custom Vision Service** )를에서 [1 장](#chapter-1---retrieve-the-custom-vision-model)합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-376">You will now need to retrieve the **labels.txt** and **model.pb** files from the model folder, which you previous downloaded (or created from your own **Custom Vision Service**), in [Chapter 1](#chapter-1---retrieve-the-custom-vision-model).</span></span> <span data-ttu-id="274fe-377">파일을 만든 후 다른 파일과 함께 솔루션 내에서 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-377">Once you have the files, place them within your solution, alongside the other files.</span></span> <span data-ttu-id="274fe-378">최종 결과 아래 이미지와 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-378">The final result should look like the image below:</span></span>

    ![컨테이너 만들기](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a><span data-ttu-id="274fe-380">9 장-패키지의 컨테이너 솔루션</span><span class="sxs-lookup"><span data-stu-id="274fe-380">Chapter 9 - Package the solution as a container</span></span>

1.  <span data-ttu-id="274fe-381">준비가 이제 "" 파일을 컨테이너로 패키징하고 푸시 되도록 하 **Azure Container Registry**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-381">You are now ready to "package" your files as a container and push it to your **Azure Container Registry**.</span></span> <span data-ttu-id="274fe-382">VS Code 내에서 엽니다는 *통합 터미널* (**뷰** > **통합 터미널** 하거나 **Ctrl** + **\`** )를 다음 줄에 로그인을 사용 하 여 **Docker** (의 자격 증명을 사용 하 여 명령의 값으로 대체 하 **Azure 컨테이너 레지스트리 (ACR)** ):</span><span class="sxs-lookup"><span data-stu-id="274fe-382">Within VS Code, open the *Integrated Terminal* (**View** > **Integrated Terminal** or **Ctrl**+**\`**), and use the following line to login to **Docker** (substitute the values of the command with the credentials of your **Azure Container Registry (ACR)**):</span></span>

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. <span data-ttu-id="274fe-383">파일을 마우스 오른쪽 단추로 클릭 **deployment.template.json**, 클릭 **IoT Edge 솔루션 빌드**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-383">Right-click on the file **deployment.template.json**, and click **Build IoT Edge Solution**.</span></span> <span data-ttu-id="274fe-384">이 빌드 프로세스 (장치)에 따라 다소 시간이, 따라서 대기 준비가 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-384">This build process takes quite some time (depending on your device), so be prepared to wait.</span></span> <span data-ttu-id="274fe-385">빌드 프로세스가 완료 되 면을 **deployment.json** 파일이 라는 새 폴더 내에서 생성 됩니다 **config**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-385">After the build process finishes, a **deployment.json** file will have been created inside a new folder called **config**.</span></span>

    ![배포 만들기](images/AzureLabs-Lab313-30.png)

3. <span data-ttu-id="274fe-387">엽니다는 **명령 팔레트** 다시 검색 **Azure: 로그인**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-387">Open the **Command Palette** again, and search for **Azure: Sign In**.</span></span> <span data-ttu-id="274fe-388">Azure 계정 자격 증명;를 사용 하 여 프롬프트에 따라 VS Code에 있는 옵션이 제공 됩니다 *복사 하 고 엽니다*, 곧 필요한을 기본 웹 브라우저를 열고 장치 코드를 복사 하는 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-388">Follow the prompts using your Azure Account credentials; VS Code will provide you with an option to *Copy and Open*, which will copy the device code you will soon need, and open your default web browser.</span></span> <span data-ttu-id="274fe-389">을 묻는 메시지가 나타나면 컴퓨터를 인증 하는 장치 코드를 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-389">When asked, paste the device code, to authenticate your machine.</span></span>

    ![복사 및 열기](images/AzureLabs-Lab313-31.png)

4. <span data-ttu-id="274fe-391">한 번 서명에서 알 수 있습니다, 아래쪽 변의 합니다 *탐색* 패널 이라는 새로운 섹션이 **Azure IoT Hub 장치**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-391">Once signed in you will notice, on the bottom side of the *Explore* panel, a new section called **Azure IoT Hub Devices**.</span></span> <span data-ttu-id="274fe-392">이 섹션 확장을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-392">Click this section to expand it.</span></span>

    ![edge 장치](images/AzureLabs-Lab313-32.png)

5. <span data-ttu-id="274fe-394">장치가 없는 경우 여기를 마우스 오른쪽 단추로 클릭 해야 합니다 *Azure IoT Hub 장치*를 클릭 하 고 **IoT Hub 연결 문자열 설정**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-394">If your device is not here, you will need to right-click *Azure IoT Hub Devices*, and then click **Set IoT Hub Connection String**.</span></span> <span data-ttu-id="274fe-395">다음 확인할 수 있습니다 합니다 **명령 팔레트** (맨 위에 있는 VS Code)를 묻는을 입력 하 *연결 문자열*합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-395">You will then see that the **Command Palette** (at the top of VS Code), will prompt you to input your *Connection String*.</span></span> <span data-ttu-id="274fe-396">이 *연결 문자열* 끝날 때 적어둔 [3 장](#chapter-3---the-iot-hub-service)합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-396">This is the *Connection String* you noted down at the end of [Chapter 3](#chapter-3---the-iot-hub-service).</span></span> <span data-ttu-id="274fe-397">키를 눌러 합니다 **Enter** 키의 문자열을 복사한 후 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-397">Press the **Enter** key, once you have copied the string in.</span></span>    

6. <span data-ttu-id="274fe-398">장치를 로드 하 고 표시 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-398">Your device should load, and appear.</span></span> <span data-ttu-id="274fe-399">장치 이름을 마우스 오른쪽 단추로 클릭 하 고 클릭 **단일 장치에 대 한 배포 만들기**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-399">Right-click on the device name, and then click, **Create Deployment for Single Device**.</span></span>

    ![배포 만들기](images/AzureLabs-Lab313-33b.png)

7. <span data-ttu-id="274fe-401">받을 수는 *파일 탐색기* 로 이동할 수 있는 프롬프트를 **구성** 폴더를 선택한 후는 **deployment.json** 파일.</span><span class="sxs-lookup"><span data-stu-id="274fe-401">You will get a *File Explorer* prompt, where you can navigate to the **config** folder, and then select the **deployment.json** file.</span></span> <span data-ttu-id="274fe-402">선택한 해당 파일을 클릭 합니다 **Edge 배포 매니페스트 선택** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-402">With that file selected, click the **Select Edge Deployment Manifest** button.</span></span>

    ![배포 만들기](images/AzureLabs-Lab313-34.png)

8. <span data-ttu-id="274fe-404">이 시점에서 제공한 하 **IoT Hub 서비스** 에서 컨테이너를 모듈로 배포에 대 한 매니페스트를 사용 하 여 프로그램 **Azure Container Registry**, 효과적으로 장치에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-404">At this point you have provided your **IoT Hub Service** with the manifest for it to deploy your container, as a module, from your **Azure Container Registry**, effectively deploying it to your device.</span></span>

9. <span data-ttu-id="274fe-405">IoT Hub에 장치에서 전송 된 메시지를 보려면 마우스 오른쪽 단추로 클릭 다시 장치 이름에는 **Azure IoT Hub 장치** 섹션을 **탐색기** 패널을 클릭할 **모니터링 시작 D2C 메시지**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-405">To view the messages sent from your device to the IoT Hub, right-click again on your device name in the **Azure IoT Hub Devices** section, in the **Explorer** panel, and click on **Start Monitoring D2C Message**.</span></span> <span data-ttu-id="274fe-406">장치에서 전송 된 메시지는 VS 터미널에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-406">The messages sent from your device should appear in the VS Terminal.</span></span> <span data-ttu-id="274fe-407">Patient로 수 약간의 시간이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-407">Be patient, as this may take some time.</span></span> <span data-ttu-id="274fe-408">디버깅 및 배포에 성공 했는지 여부를 확인 한 다음 장에서 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="274fe-408">See the next Chapter for debugging, and checking if deployment was successful.</span></span>

<span data-ttu-id="274fe-409">이 모듈은 이미지 간의 반복 이제는 **이미지** 폴더 하 고, 각 반복을 사용 하 여 분석 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-409">This module will now iterate between the images in the **images** folder and analyze them, with each iteration.</span></span> <span data-ttu-id="274fe-410">IoT Edge 장치 환경에서 작동 하도록 기본 machine learning 모델을 가져오는 방법의 데모 럽입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-410">This is obviously just a demonstration of how to get the basic machine learning model to work in an IoT Edge device environment.</span></span> 

<span data-ttu-id="274fe-411">이 예제의 기능을 확장 하려면 여러 가지 방법으로 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-411">To expand the functionality of this example, you could proceed in several ways.</span></span> <span data-ttu-id="274fe-412">장치에 연결 되 고 이미지 폴더에 이미지를 저장 웹캠에서 사진을 캡처하는 컨테이너의 방법 중 하나는 코드가 포함 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-412">One way could be including some code in the container, that captures photos from a webcam that is connected to the device, and saves the images in the images folder.</span></span> 

<span data-ttu-id="274fe-413">또 다른 방법은 없습니다 복사 하는 이미지 IoT 장치에서 컨테이너에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-413">Another way could be copying the images from the IoT device into the container.</span></span> <span data-ttu-id="274fe-414">IoT 장치 (아마도 작은 앱을 수행할 수는 작업 프로세스를 자동화 하려는 경우)는 터미널에서에서 다음 명령을 실행 방법은 하는 작업을 수행 하는 실용적인 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-414">A practical way to do that is to run the following command in the IoT device Terminal (perhaps a small app could do the job, if you wished to automate the process).</span></span> <span data-ttu-id="274fe-415">이 명령은 파일에 저장 된 폴더 위치에서 수동으로 실행 하 여 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-415">You can test this command by running it manually from the folder location where your files are stored:</span></span>

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a><span data-ttu-id="274fe-416">10 장-IoT Edge 런타임 디버깅</span><span class="sxs-lookup"><span data-stu-id="274fe-416">Chapter 10 - Debugging the IoT Edge Runtime</span></span>

<span data-ttu-id="274fe-417">다음은 명령줄와 팁을 모니터링 하 고 메시징 활동을 디버깅할 수 있도록 목록을 합니다 *IoT Edge 런타임은*에서 프로그램 **Ubuntu 장치**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-417">The following are a list of command lines, and tips, to help you monitor and debug the messaging activity of the *IoT Edge Runtime*, from your **Ubuntu device**.</span></span> 

- <span data-ttu-id="274fe-418">확인 합니다 *IoT Edge 런타임은* 다음 명령줄을 실행 하 여 상태:</span><span class="sxs-lookup"><span data-stu-id="274fe-418">Check the *IoT Edge Runtime* status by running the following command line:</span></span>

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > <span data-ttu-id="274fe-419">키를 눌러야 **Ctrl + C**, 완료 상태를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-419">Remember to press **Ctrl + C**, to finish viewing the status.</span></span>

- <span data-ttu-id="274fe-420">현재 배포 되어 있는 컨테이너를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-420">List the containers that are currently deployed.</span></span> <span data-ttu-id="274fe-421">경우는 *IoT Hub 서비스* 컨테이너를 성공적으로 배포한 다음 명령줄을 실행 하 여 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-421">If the *IoT Hub Service* has deployed the containers successfully, they will be displayed by running the following command line:</span></span>

    ```bash
        sudo iotedge list
    ```

    <span data-ttu-id="274fe-422">또는</span><span class="sxs-lookup"><span data-stu-id="274fe-422">Or</span></span>

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > <span data-ttu-id="274fe-423">위 내용은 여부를 모듈에 성공적으로 배포 되었는지, 목록에 나타나는 대로 확인 하는 좋은 방법 그렇지 않은 경우에 **만** 참조를 *edge 허브* 하 고 *edge 에이전트*합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-423">The above is a good way to check whether your module has been deployed successfully, as it will appear in the list; you will otherwise **only** see the *edgeHub* and *edgeAgent*.</span></span>

- <span data-ttu-id="274fe-424">컨테이너의 코드 로그를 표시 하려면 다음 명령줄을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-424">To display the code logs of a container, run the following command line:</span></span>

    ```bash
        journalctl -u iotedge
    ```

<span data-ttu-id="274fe-425">**IoT Edge 런타임은 관리 하는 유용한 명령:**</span><span class="sxs-lookup"><span data-stu-id="274fe-425">**Useful commands to manage the IoT Edge Runtime:**</span></span>

-  <span data-ttu-id="274fe-426">에 호스트의 모든 컨테이너를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-426">To delete all containers in the host:</span></span>

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  <span data-ttu-id="274fe-427">중지 하는 *IoT Edge 런타임은*:</span><span class="sxs-lookup"><span data-stu-id="274fe-427">To stop the *IoT Edge Runtime*:</span></span>

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a><span data-ttu-id="274fe-428">11-장 테이블 서비스 만들기</span><span class="sxs-lookup"><span data-stu-id="274fe-428">Chapter 11 - Create Table Service</span></span> 

<span data-ttu-id="274fe-429">저장소 리소스를 만들어 Azure 테이블 서비스를 만들 Azure 포털을 다시 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-429">Navigate back to your Azure Portal, where you will create an Azure Tables Service, by creating a Storage resource.</span></span>

1. <span data-ttu-id="274fe-430">아직 로그인 하지 않은, 경우에 로그인 합니다 [Azure Portal](https://portal.azure.com)합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-430">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="274fe-431">에 로그인 되 면 클릭 **리소스 만들기**, 왼쪽 상단 모서리에 검색할 **저장소 계정**, 키를 누릅니다를 **Enter** 키 검색을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-431">Once logged in, click on **Create a resource**, in the top left corner, and search for **Storage account**, and press the **Enter** key, to start the search.</span></span>

3. <span data-ttu-id="274fe-432">나타났습니다, 클릭 **저장소 계정-blob, 파일, 테이블, 큐** 목록에서.</span><span class="sxs-lookup"><span data-stu-id="274fe-432">Once it has appeared, click **Storage account - blob, file, table, queue** from the list.</span></span>

    ![저장소 계정에 대 한 검색](images/AzureLabs-Lab313-35.png)

4. <span data-ttu-id="274fe-434">새 페이지에 대 한 설명을 제공 합니다는 **저장소 계정** 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-434">The new page will provide a description of the **Storage account** Service.</span></span> <span data-ttu-id="274fe-435">이 프롬프트의 왼쪽 아래에 있는 클릭 합니다 **만들기** 단추를 서비스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-435">At the bottom left of this prompt, click the **Create** button, to create an instance of this Service.</span></span>

    ![저장소 인스턴스 만들기](images/AzureLabs-Lab313-36.png)

5. <span data-ttu-id="274fe-437">클릭 한 후 **만들기**를 패널에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-437">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="274fe-438">원하는 삽입 **이름을** 이 서비스 인스턴스에 대 한 (*모두 소문자 여야*).</span><span class="sxs-lookup"><span data-stu-id="274fe-438">Insert your desired **Name** for this Service instance (*must be all lowercase*).</span></span>

    2. <span data-ttu-id="274fe-439">에 대 한 **배포 모델**, 클릭 **Resource manager**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-439">For **Deployment model**, click **Resource manager**.</span></span>

    3. <span data-ttu-id="274fe-440">에 대 한 **계정 종류**, 드롭다운 메뉴를 사용 하 여 클릭 **저장소 (범용 v1)** 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-440">For **Account kind**, using the dropdown menu, click **Storage (general purpose v1)**.</span></span>

    4. <span data-ttu-id="274fe-441">적절 한 클릭 **위치**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-441">Click an appropriate **Location**.</span></span>
    
    5. <span data-ttu-id="274fe-442">에 대 한 합니다 **복제** 드롭다운 메뉴를 클릭 **읽기-액세스-지역 중복 저장소 (RA-GRS)** 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-442">For the **Replication** dropdown menu, click **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6. <span data-ttu-id="274fe-443">에 대 한 **성능**, 클릭 **표준**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-443">For **Performance**, click **Standard**.</span></span>

    7. <span data-ttu-id="274fe-444">내 합니다 **보안 전송 필요** 섹션에서 **비활성화 된**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-444">Within the **Secure transfer required** section, click **Disabled**.</span></span>

    8. <span data-ttu-id="274fe-445">**구독** 드롭다운 메뉴에서 적절 한 구독을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-445">From the **Subscription** dropdown menu, click an appropriate subscription.</span></span>

    9. <span data-ttu-id="274fe-446">선택 된 **리소스 그룹** 하거나 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-446">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="274fe-447">리소스 그룹에는 모니터링, 프로 비전, 액세스 제어 및 Azure 자산 모음에 대 한 청구를 관리 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-447">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="274fe-448">좋습니다 일반적인 리소스 그룹에서 (예: 이러한 교육 과정) 예: 단일 프로젝트와 연결 된 Azure 서비스를 모두 유지).</span><span class="sxs-lookup"><span data-stu-id="274fe-448">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="274fe-449">추가 하려는 경우 Azure 리소스 그룹에 대 한 따르세요이 [리소스 그룹을 관리 하는 방법에 대 한 링크](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-449">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="274fe-450">둡니다 **가상 네트워크** 으로 **비활성**선택할 경우, 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-450">Leave **Virtual networks** as **Disabled**, if this is an option for you.</span></span>

    11. <span data-ttu-id="274fe-451">**만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-451">Click **Create**.</span></span>

        ![저장소 세부 정보 입력](images/AzureLabs-Lab313-37.png)

6. <span data-ttu-id="274fe-453">클릭 한 후 **만들기**만들려는 서비스에 대 한 대기 해야, 1 분이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-453">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

7. <span data-ttu-id="274fe-454">서비스 인스턴스가 생성 되 면 포털에서 알림이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-454">A notification will appear in the Portal once the Service instance is created.</span></span> <span data-ttu-id="274fe-455">새 서비스 인스턴스를 탐색 하려면 알림을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-455">Click on the notifications to explore your new Service instance.</span></span>

    ![새 저장소 알림](images/AzureLabs-Lab313-38.png)

8. <span data-ttu-id="274fe-457">클릭 합니다 **리소스로 이동** 알림을에서 단추 새 저장소 서비스 인스턴스 개요 페이지에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-457">Click the **Go to resource** button in the notification, and you will be taken to your new Storage Service instance overview page.</span></span>

    ![리소스로 이동](images/AzureLabs-Lab313-39.png)

9. <span data-ttu-id="274fe-459">개요 페이지를 오른쪽에서 클릭 **테이블**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-459">From the overview page, to the right-hand side, click **Tables**.</span></span>
    
    ![테이블](images/AzureLabs-Lab313-40.png)

10. <span data-ttu-id="274fe-461">오른쪽 패널을 표시 하도록 변경 됩니다 합니다 **Table Service** 정보, 여기서 새 테이블을 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-461">The panel on the right will change to show the **Table Service** information, wherein you need to add a new table.</span></span> <span data-ttu-id="274fe-462">클릭 하 여이 작업을 수행 합니다 **+ 테이블** 왼쪽 위 모퉁이에 있는 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-462">Do this by clicking the **+ Table** button to the top-left corner.</span></span>

    ![테이블 열기](images/AzureLabs-Lab313-41.png)

11. <span data-ttu-id="274fe-464">새 페이지가 표시 될 입력 해야 하는 여기서는 **테이블 이름**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-464">A new page will be shown, wherein you need to enter a **Table name**.</span></span> <span data-ttu-id="274fe-465">뒷부분 (만들고 함수 앱에 Power BI)에서 응용 프로그램에서 데이터를 참조 하는 데 사용할 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-465">This is the name you will use to refer to the data in your application in later Chapters (creating Function App, and Power BI).</span></span> <span data-ttu-id="274fe-466">삽입 **IoTMessages** 이름으로 (직접 선택할 수 있습니다 단이 문서의 뒷부분에서 사용 되는 경우)를 클릭 하 고 **확인**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-466">Insert **IoTMessages** as the name (you can choose your own, just remember it when used later in this document) and click **OK**.</span></span> 

12. <span data-ttu-id="274fe-467">새 테이블을 만든 후에 내에서 볼 수는 합니다 **Table Service** 페이지 (아래쪽).</span><span class="sxs-lookup"><span data-stu-id="274fe-467">Once the new table has been created, you will be able to see it within the **Table Service** page (at the bottom).</span></span>

    ![만든 새 테이블](images/AzureLabs-Lab313-42.png)  

13. <span data-ttu-id="274fe-469">이제 클릭할 **액세스 키** 의 복사 합니다 **저장소 계정 이름** 및 **키** (에 메모장 사용) 하면 이러한 값이이 과정의 뒷부분에서 만들 때 사용 됩니다는 **Azure 함수 앱**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-469">Now click on **Access keys** and take a copy of the **Storage account name** and **Key** (using your Notepad), you will use these values later in this course, when creating the **Azure Function App**.</span></span>

    ![만든 새 테이블](images/AzureLabs-Lab313-43.png) 

14. <span data-ttu-id="274fe-471">스크롤하여 마찬가지로 왼쪽 패널을 사용 하는 *Table Service* 섹션을 클릭 **테이블** (또는 **테이블 찾아보기**, 최신 포털에서)의 복사를  **URL 테이블** (에 메모장을 사용 하 여).</span><span class="sxs-lookup"><span data-stu-id="274fe-471">Using the panel on the left again, scroll to the *Table Service* section, and click **Tables** (or **Browse Tables**, in newer Portals) and take a copy of the **Table URL** (using your Notepad).</span></span> <span data-ttu-id="274fe-472">테이블을 연결 하는 경우이 값이이 과정의 뒷부분에서 사용 됩니다 하 **Power BI** 응용 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-472">You will use this value later in this course, when linking your table to your **Power BI** application.</span></span>

    ![만든 새 테이블](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a><span data-ttu-id="274fe-474">12 장-Azure 테이블을 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-474">Chapter 12 - Completing the Azure Table</span></span>

<span data-ttu-id="274fe-475">이제 프로그램 **Table Service** 저장소 계정에 설치 되어, 정보 저장 및 검색에 사용 되는 데이터를 추가할 차례입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-475">Now that your **Table Service** storage account has been setup, it is time to add data to it, which will be used to store and retrieve information.</span></span> <span data-ttu-id="274fe-476">테이블에 대 한 편집을 통해 수행할 수 있습니다 **Visual Studio**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-476">The editing of your Tables can be done through **Visual Studio**.</span></span>

1. <span data-ttu-id="274fe-477">오픈 **Visual Studio** (**하지** Visual Studio Code).</span><span class="sxs-lookup"><span data-stu-id="274fe-477">Open **Visual Studio** (**not** Visual Studio Code).</span></span>

2. <span data-ttu-id="274fe-478">메뉴에서 클릭 **뷰** > **클라우드 탐색기**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-478">From the menu, click **View** > **Cloud Explorer**.</span></span>

    ![클라우드 탐색기를 열으십시오](images/AzureLabs-Lab313-45.png)

3. <span data-ttu-id="274fe-480">합니다 **클라우드 탐색기** 열립니다 도킹 된 항목으로 일 환자, 대로 로드 시간이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-480">The **Cloud Explorer** will open as a docked item (be patient, as loading may take time).</span></span>

    > [!WARNING] 
    > <span data-ttu-id="274fe-481">만드는 데 사용한 구독 하는 경우에 *저장소 계정* 표시 되지 않으면 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-481">If the subscription you used to create your *Storage Accounts* is not visible, ensure that you have:</span></span> 
    > - <span data-ttu-id="274fe-482">Azure Portal에 사용한 것과 동일한 계정에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-482">Logged in to the same account as the one you used for the Azure Portal.</span></span>
    > - <span data-ttu-id="274fe-483">(계정 설정에서 필터를 적용 해야 할) 계정 관리 페이지에서 구독을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-483">Selected your subscription from the Account Management page (you may need to apply a filter from your account settings):</span></span>  
    >
    >   ![구독을 찾을](images/AzureLabs-Lab313-46.png)

4. <span data-ttu-id="274fe-485">Azure 클라우드 서비스에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-485">Your Azure cloud Services will be shown.</span></span> <span data-ttu-id="274fe-486">찾을 **저장소 계정** 계정을 확장 하는 왼쪽에 있는 화살표를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-486">Find **Storage Accounts** and click the arrow to the left of that to expand your accounts.</span></span>

    ![열려 있는 저장소 계정](images/AzureLabs-Lab313-47.png)

5. <span data-ttu-id="274fe-488">새로 만든 확장 되 면 **저장소 계정** 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-488">Once expanded, your newly created **Storage account** should be available.</span></span> <span data-ttu-id="274fe-489">저장소, 왼쪽에 있는 화살표를 클릭 하 고 확장 되 면 찾습니다 **테이블** 표시 하려면 옆에 있는 화살표를 클릭 합니다 **테이블** 마지막 단원에서 만든 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-489">Click the arrow to the left of your storage, and then once that is expanded, find **Tables** and click the arrow next to that, to reveal the **Table** you created in the last Chapter.</span></span> <span data-ttu-id="274fe-490">두 번 클릭 하 여 **테이블**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-490">Double-click your **Table**.</span></span>

6. <span data-ttu-id="274fe-491">테이블에는 Visual Studio 창의 가운데에 열립니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-491">Your table will be opened in the center of your Visual Studio window.</span></span> <span data-ttu-id="274fe-492">가 있는 테이블 아이콘을 클릭 합니다 **+** (및)에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-492">Click the table icon with the **+** (plus) on it.</span></span>

    ![새 테이블 추가](images/AzureLabs-Lab313-48.png)

7. <span data-ttu-id="274fe-494">수는 창이 나타나면 묻는 *엔터티 추가*합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-494">A window will appear prompting for you to *Add Entity*.</span></span> <span data-ttu-id="274fe-495">세 가지 속성을 갖게 되 고 있지만 하나의 엔터티를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-495">You will create only one entity, though it will have three properties.</span></span> <span data-ttu-id="274fe-496">점을 확인할 수 있습니다 *PartitionKey* 하 고 *RowKey* 기본적으로 제공의 데이터를 테이블에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-496">You will notice that *PartitionKey* and *RowKey* are already provided, as these are used by the table to find your data.</span></span> 

    ![파티션 및 행 키](images/AzureLabs-Lab313-49.png)

8. <span data-ttu-id="274fe-498">다음 값을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-498">Update the following values:</span></span>

    - <span data-ttu-id="274fe-499">이름: **PartitionKey**, Value: **PK_IoTMessages**</span><span class="sxs-lookup"><span data-stu-id="274fe-499">Name: **PartitionKey**, Value: **PK_IoTMessages**</span></span> 

    - <span data-ttu-id="274fe-500">이름: **RowKey**, Value: **RK_1_IoTMessages**</span><span class="sxs-lookup"><span data-stu-id="274fe-500">Name: **RowKey**, Value: **RK_1_IoTMessages**</span></span> 

9. <span data-ttu-id="274fe-501">클릭 **속성 추가** (왼쪽 아래에 *엔터티 추가* 창) 다음 속성을 추가 하 고:</span><span class="sxs-lookup"><span data-stu-id="274fe-501">Then, click **Add property** (to the lower left of the *Add Entity* window) and add the following property:</span></span>

    - <span data-ttu-id="274fe-502">**Messagecontent가**,으로 *문자열*, 값을 비워 둡니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-502">**MessageContent**, as a *string*, leave the Value empty.</span></span>

10. <span data-ttu-id="274fe-503">테이블에는 아래 이미지를 일치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-503">Your table should match the one in the image below:</span></span>

    ![올바른 값 추가](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > <span data-ttu-id="274fe-505">수도 있으므로 더 많은 메시지를 추가 하려면 실험 하려는 엔터티의 행 키에 번호가 1 인 하는 이유는 이유는이 과정을 통해 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-505">The reason why the entity has the number 1 in the row key, is because you might want to add more messages, should you desire to experiment further with this course.</span></span>

11. <span data-ttu-id="274fe-506">클릭 **확인** 완료 되 면 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-506">Click **OK** when you are finished.</span></span> <span data-ttu-id="274fe-507">테이블에 사용할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-507">Your table is now ready to be used.</span></span>

## <a name="chapter-13---create-an-azure-function-app"></a><span data-ttu-id="274fe-508">13-장에서 Azure 함수 앱 만들기</span><span class="sxs-lookup"><span data-stu-id="274fe-508">Chapter 13 - Create an Azure Function App</span></span> 

<span data-ttu-id="274fe-509">만들려면 이제 차례입니다는 *Azure 함수 앱*, 의해 호출 됩니다는 *IoT Hub 서비스* 저장 하는 *IoT Edge* 장치에서 메시지를 **테이블** 이전 장에서 만든 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-509">It is now time to create an *Azure Function App*, which will be called by the *IoT Hub Service* to store the *IoT Edge* device messages in the **Table** Service, which you created in the previous Chapter.</span></span>

<span data-ttu-id="274fe-510">먼저 필요한 라이브러리를 로드 하 여 Azure Function을 사용 하면 파일을 만드는 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-510">First, you need to create a file that will allow your Azure Function to load the libraries you need.</span></span>

1.  <span data-ttu-id="274fe-511">열기 **메모장** (키를 누릅니다를 *Windows 키*에서 형식과 *메모장*).</span><span class="sxs-lookup"><span data-stu-id="274fe-511">Open **Notepad** (press the *Windows Key*, and type *notepad*).</span></span>

    ![메모장을 열려면](images/AzureLabs-Lab313-51.png)

2.  <span data-ttu-id="274fe-513">열기 메모장을 사용 하 여 아래 JSON 구조를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-513">With Notepad open, insert the JSON structure below into it.</span></span> <span data-ttu-id="274fe-514">작업을 수행한 후으로 바탕 화면에 저장 **project.json**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-514">Once you have done that, save it on your desktop as **project.json**.</span></span> <span data-ttu-id="274fe-515">이 파일은 함수를 사용 하 여 라이브러리를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-515">This file defines the libraries your function will use.</span></span> <span data-ttu-id="274fe-516">NuGet을 사용한 경우 친숙 한 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-516">If you have used NuGet, it will look familiar.</span></span>
    
    > [!WARNING]
    > <span data-ttu-id="274fe-517">명명이 올바른; 반드시 확인 수행 **.txt 없는** 파일 확장명입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-517">It is important that the naming is correct; ensure it does **NOT have a .txt** file extension.</span></span> <span data-ttu-id="274fe-518">참조에 대 한 아래를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="274fe-518">See below for reference:</span></span>
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

3.  <span data-ttu-id="274fe-520">에 로그인 합니다 [Azure Portal](https://portal.azure.com)합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-520">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

4.  <span data-ttu-id="274fe-521">일단 로그인 하면 클릭할 **리소스 만들기** 왼쪽 위에서 모서리 및 검색 **함수 앱**, 키를 누릅니다를 **Enter** 를 검색할 키입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-521">Once you are logged in, click on **Create a resource** in the top left corner, and search for **Function App**, and press the **Enter** key, to search.</span></span> <span data-ttu-id="274fe-522">클릭 *함수 앱* 에서 결과 새 패널이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-522">Click *Function App* from the results, to open a new panel.</span></span>

    ![함수 앱에 대 한 검색](images/AzureLabs-Lab313-53.png)

5.  <span data-ttu-id="274fe-524">새 패널에 대 한 설명을 제공 합니다는 **함수 앱** 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-524">The new panel will provide a description of the **Function App** Service.</span></span> <span data-ttu-id="274fe-525">이 패널의 왼쪽 아래에 있는 클릭 합니다 **만들기** 이 연결 서비스를 만들려면 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-525">At the bottom left of this panel, click the **Create** button, to create an association with this Service.</span></span>

    ![함수 앱 인스턴스](images/AzureLabs-Lab313-54.png)

6.  <span data-ttu-id="274fe-527">클릭 한 후 **만들기**, 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-527">Once you have clicked on **Create**, fill in the following:</span></span>

    1. <span data-ttu-id="274fe-528">에 대 한 **앱 이름**,이 서비스 인스턴스에 대해 원하는 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-528">For **App name**, insert your desired name for this Service instance.</span></span>

    2. <span data-ttu-id="274fe-529">선택 된 **구독**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-529">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="274fe-530">첫 번째 경우, 적합 한 가격 책정 계층 선택 만들기 시간을 **함수 앱 서비스**, 무료 계층을 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-530">Select the pricing tier appropriate for you, if this is the first time creating a **Function App Service**, a free tier should be available to you.</span></span>

    4. <span data-ttu-id="274fe-531">선택 된 **리소스 그룹** 하거나 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-531">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="274fe-532">리소스 그룹에는 모니터링, 프로 비전, 액세스 제어 및 Azure 자산 모음에 대 한 청구를 관리 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-532">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="274fe-533">좋습니다 일반적인 리소스 그룹에서 (예: 이러한 교육 과정) 예: 단일 프로젝트와 연결 된 Azure 서비스를 모두 유지).</span><span class="sxs-lookup"><span data-stu-id="274fe-533">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="274fe-534">추가 하려는 경우 Azure 리소스 그룹에 대 한 따르세요이 [리소스 그룹을 관리 하는 방법에 대 한 링크](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-534">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="274fe-535">에 대 한 **OS**를 원하는 플랫폼으로 Windows를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-535">For **OS**, click Windows, as that is the intended platform.</span></span>

    6. <span data-ttu-id="274fe-536">선택 된 **호스팅 계획** (이 자습서를 사용 하는 **소비 계획**.</span><span class="sxs-lookup"><span data-stu-id="274fe-536">Select a **Hosting Plan** (this tutorial is using a **Consumption Plan**.</span></span>

    7. <span data-ttu-id="274fe-537">선택 된 **위치** (이전 단계에서 만든 저장소와 동일한 위치를 선택)</span><span class="sxs-lookup"><span data-stu-id="274fe-537">Select a **Location** (choose the same location as the storage you have built in the previous step)</span></span>

    8. <span data-ttu-id="274fe-538">에 대 한 합니다 **저장소** 섹션인 **이전 단계에서 만든 저장소 서비스를 선택 해야 합니다**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-538">For the **Storage** section, **you must select the Storage Service you created in the previous step**.</span></span>

    9. <span data-ttu-id="274fe-539">필요 하지 것입니다 *Application Insights* 이 앱에서 에게도 그대로 **해제**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-539">You will not need *Application Insights* in this app, so feel free to leave it **Off**.</span></span>

    10. <span data-ttu-id="274fe-540">**만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-540">Click **Create**.</span></span>

        ![새 인스턴스 만들기](images/AzureLabs-Lab313-55.png)

7.  <span data-ttu-id="274fe-542">클릭 한 후 **만들기**만들려는 서비스에 대 한 대기 해야, 1 분이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-542">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

8.  <span data-ttu-id="274fe-543">서비스 인스턴스가 생성 되 면 포털에서 알림이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-543">A notification will appear in the Portal once the Service instance is created.</span></span>

    ![새 알림](images/AzureLabs-Lab313-56.png)

9.  <span data-ttu-id="274fe-545">성공적으로 배포 되 면 알림을 클릭 (완료).</span><span class="sxs-lookup"><span data-stu-id="274fe-545">Click on the notification, once deployment is successful (has finished).</span></span>

10. <span data-ttu-id="274fe-546">클릭 합니다 **리소스로 이동** 알림에서 새 서비스 인스턴스를 탐색 하는 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-546">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> 

    ![리소스로 이동](images/AzureLabs-Lab313-57.png)

11. <span data-ttu-id="274fe-548">새 패널의 왼쪽에 있는 클릭 합니다 **+** (더하기) 옆에 아이콘 *함수*, 새 함수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-548">In the left side of the new panel, click the **+** (plus) icon next to *Functions*, to create a new function.</span></span>

    ![새 함수를 추가 합니다.](images/AzureLabs-Lab313-58.png)

12. <span data-ttu-id="274fe-550">중앙 패널에는 **함수** 만들기 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-550">Within the central panel, the **Function** creation window will appear.</span></span> <span data-ttu-id="274fe-551">또한 아래로 스크롤을 클릭할 **사용자 지정 함수**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-551">Scroll down further, and click on **Custom function**.</span></span>

    ![사용자 지정 함수](images/AzureLabs-Lab313-59.png)

13. <span data-ttu-id="274fe-553">다음 페이지를 찾을 때까지 아래로 스크롤하여 **IoT Hub (이벤트 허브)** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-553">Scroll down the next page, until you find **IoT Hub (Event Hub)**, then click on it.</span></span>

    ![사용자 지정 함수](images/AzureLabs-Lab313-60.png)

14. <span data-ttu-id="274fe-555">에 **IoT Hub (이벤트 허브)** 블레이드에서 설정 합니다 **언어** 를 **C#** 를 클릭 하 고 **새**.</span><span class="sxs-lookup"><span data-stu-id="274fe-555">In the **IoT Hub (Event Hub)** blade, set the **Language** to **C#** and then click on **new**.</span></span>

    ![사용자 지정 함수](images/AzureLabs-Lab313-61.png)

15. <span data-ttu-id="274fe-557">표시 되는 창에서 확인 **IoT Hub** 선택 이름과 합니다 *IoT Hub* 필드의 이름으로 해당 프로그램 *IoT Hub 서비스* 해야 하는 이전에 만든 ([3 장의 8 단계에서](#chapter-3---the-iot-hub-service)).</span><span class="sxs-lookup"><span data-stu-id="274fe-557">In the window that will appear, make sure that **IoT Hub** is selected and the name of the *IoT Hub* field corresponds with the name of your *IoT Hub Service* that you have created previously ([in step 8, of Chapter 3](#chapter-3---the-iot-hub-service)).</span></span> <span data-ttu-id="274fe-558">다음을 클릭 합니다 **선택** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-558">Then click the **Select** button.</span></span>

    ![사용자 지정 함수](images/AzureLabs-Lab313-62.png)

16. <span data-ttu-id="274fe-560">다시 합니다 **IoT Hub (이벤트 허브)** 블레이드에서 클릭 **만들기**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-560">Back on the **IoT Hub (Event Hub)** blade, click on **Create**.</span></span>

    ![사용자 지정 함수](images/AzureLabs-Lab313-63.png)

17. <span data-ttu-id="274fe-562">함수 편집기로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-562">You will be redirected to the function editor.</span></span>

    ![사용자 지정 함수](images/AzureLabs-Lab313-64.png)

18. <span data-ttu-id="274fe-564">에 모든 코드를 삭제 하 고 다음 코드로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-564">Delete all the code in it and replace it with the following:</span></span>

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

19. <span data-ttu-id="274fe-565">적절 한 값에 해당 되도록 다음 변수를 변경 (**테이블** 하 고 **저장소** 값에서 [장 11 11, 13, 각각 단계](#chapter-11---create-table-service)), 찾을 수 있는 사용자 **저장소 계정**:</span><span class="sxs-lookup"><span data-stu-id="274fe-565">Change the following variables, so that they correspond to the appropriate values (**Table** and **Storage** values, from [step 11 and 13, respectively, of Chapter 11](#chapter-11---create-table-service)), that you will find in your **Storage Account**:</span></span>

    - <span data-ttu-id="274fe-566">**tableName**, 이름의 하 **테이블** 에 있는 프로그램 **저장소 계정**.</span><span class="sxs-lookup"><span data-stu-id="274fe-566">**tableName**, with the name of your **Table** located in your **Storage Account**.</span></span>
    - <span data-ttu-id="274fe-567">**tableURL**의 URL을 사용 하 여 프로그램 **테이블** 에 있는 프로그램 **저장소 계정**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-567">**tableURL**, with the URL of your **Table** located in your **Storage Account**.</span></span>
    - <span data-ttu-id="274fe-568">**storageAccountName**를 이름으로 해당 값의 이름에 **저장소 계정** 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-568">**storageAccountName**, with the name of the value corresponding with the name of your **Storage Account** name.</span></span>
    - <span data-ttu-id="274fe-569">**storageAccountKey**, 이전에 만든 저장소 서비스에서 얻은 키를 사용 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-569">**storageAccountKey**, with the Key you have obtained in the Storage Service you have created previously.</span></span>

    ![사용자 지정 함수](images/AzureLabs-Lab313-65.png)

20. <span data-ttu-id="274fe-571">코드, 클릭 **저장할**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-571">With the code in place, click **Save**.</span></span>

21. <span data-ttu-id="274fe-572">다음을 클릭 합니다 **\<** 페이지의 오른쪽에 (화살표) 아이콘을 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-572">Next, click the **\<** (arrow) icon, on the right-hand side of the page.</span></span>

    ![사용자 지정 함수](images/AzureLabs-Lab313-66.png)

22. <span data-ttu-id="274fe-574">패널은 오른쪽에서에서 슬라이드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-574">A panel will slide in from the right.</span></span> <span data-ttu-id="274fe-575">해당 창에서 클릭 **업로드할**, 및 *파일 브라우저* 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-575">In that panel, click **Upload**, and a *File Browser* will appear.</span></span>

23. <span data-ttu-id="274fe-576">찾아 클릭 합니다는 **project.json** 파일에서 만든 **메모장** 이전에 클릭 하 고는 **열기** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-576">Navigate to, and click, the **project.json** file, which you created in **Notepad** previously, and then click the **Open** button.</span></span> <span data-ttu-id="274fe-577">이 파일은 라이브러리 함수를 사용할지를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-577">This file defines the libraries that your function will use.</span></span>

    ![사용자 지정 함수](images/AzureLabs-Lab313-67.png)

24. <span data-ttu-id="274fe-579">파일 업로드에 오른쪽 패널에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-579">When the file has uploaded, it will appear in the panel on the right.</span></span> <span data-ttu-id="274fe-580">내에서 열기를 클릭 하 여 **함수** 편집기입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-580">Clicking it will open it within the **Function** editor.</span></span> <span data-ttu-id="274fe-581">찾아야 **정확 하 게** 다음 이미지와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-581">It must look **exactly** the same as the next image.</span></span>

    ![사용자 지정 함수](images/AzureLabs-Lab313-68.png)

25. <span data-ttu-id="274fe-583">이 시점에서 것이 좋습니다에 메시지를 저장 하는 함수의 기능을 테스트 하 여 *테이블*합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-583">At this point it would be good to test the capability of your Function to store the message on your *Table*.</span></span> <span data-ttu-id="274fe-584">창의 맨 위 오른쪽에서 클릭 **테스트**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-584">On the top right side of the window, click on **Test**.</span></span>

    ![사용자 지정 함수](images/AzureLabs-Lab313-69.png)

26. <span data-ttu-id="274fe-586">메시지를 삽입 합니다 **요청 본문**에 고 위의 이미지에서 보여준 것 처럼 **실행**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-586">Insert a message on the **Request body**, as shown in the image above, and click on **Run**.</span></span> 

27. <span data-ttu-id="274fe-587">함수 실행 결과 상태를 표시 (녹색으로 바뀝니다 **상태 202 수락**위의 합니다 *출력* 호출에 성공한 것을 의미 하는 창의):</span><span class="sxs-lookup"><span data-stu-id="274fe-587">The function will run, displaying the result status (you will notice the green **Status 202 Accepted**, above the *Output* window, which means it was a successful call):</span></span>

    ![출력 결과](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a><span data-ttu-id="274fe-589">14 장-active 메시지 보기</span><span class="sxs-lookup"><span data-stu-id="274fe-589">Chapter 14 - View active messages</span></span>

<span data-ttu-id="274fe-590">이제 Visual Studio를 열면 (**되지** Visual Studio Code)에 저장 된 대로 테스트 메시지 결과 시각화할 수 있습니다 합니다 *messagecontent가* 영역 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-590">If you now open Visual Studio (**not** Visual Studio Code), you can visualize your test message result, as it will be stored in the *MessageContent* string area.</span></span>

![사용자 지정 함수](images/AzureLabs-Lab313-71.png)

<span data-ttu-id="274fe-592">Table Service 및 위치에서 함수 앱을 사용 하 여 Ubuntu 장치 메시지에 표시 됩니다 하 *IoTMessages* 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-592">With the Table Service and Function App in place, your Ubuntu device messages will appear in your *IoTMessages* Table.</span></span> <span data-ttu-id="274fe-593">아직 실행 하는 경우 장치를 다시 시작 하 고 Visual Studio를 사용 하 여을 통해 장치 및 모듈, 테이블 내에서 결과 메시지를 볼 수 있습니다 *클라우드 탐색기*합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-593">If not already running, start your device again, and you will be able to see the result messages from your device, and module, within your Table, through using Visual Studio *Cloud Explorer*.</span></span>

![데이터 시각화](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a><span data-ttu-id="274fe-595">15 장-Power BI 설치</span><span class="sxs-lookup"><span data-stu-id="274fe-595">Chapter 15 - Power BI Setup</span></span>

<span data-ttu-id="274fe-596">설치 하는 IOT 장치에서 데이터를 시각화할 **Power BI** (데스크톱 버전)에서 데이터를 수집 하는 *테이블* 방금 만든 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-596">To visualize the data from your IOT device you will setup **Power BI** (desktop version), to collect the data from the *Table* Service, which you just created.</span></span> <span data-ttu-id="274fe-597">합니다 *HoloLens* Power BI 버전을 사용 하 여 해당 데이터 결과 시각화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-597">The *HoloLens* version of Power BI will then use that data to visualize the result.</span></span>

1.  <span data-ttu-id="274fe-598">Microsoft Store on Windows 10 열고 검색할 **Power BI Desktop**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-598">Open the Microsoft Store on Windows 10 and search for **Power BI Desktop**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  <span data-ttu-id="274fe-600">응용 프로그램을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-600">Download the application.</span></span> <span data-ttu-id="274fe-601">다운로드 완료를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-601">Once it has finished downloading, open it.</span></span>

3.  <span data-ttu-id="274fe-602">에 로그인 *Power BI* 사용 하 여 프로그램 **Microsoft 365 계정**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-602">Log into *Power BI* with your **Microsoft 365 account**.</span></span> <span data-ttu-id="274fe-603">등록 하는 브라우저에 리디렉션될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-603">You may be redirected to a browser, to sign up.</span></span> <span data-ttu-id="274fe-604">등록 하면 Power BI 앱으로 돌아가서 후 다시 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-604">Once you are signed up, go back to the Power BI app, and sign in again.</span></span>

4.  <span data-ttu-id="274fe-605">클릭할 **데이터 가져오기** 를 클릭 하 고 **더...** .</span><span class="sxs-lookup"><span data-stu-id="274fe-605">Click on **Get Data** and then click on **More...**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  <span data-ttu-id="274fe-607">클릭 **Azure**를 **Azure Table Storage**, 클릭 **Connect**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-607">Click **Azure**, **Azure Table Storage**, then click on **Connect**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  <span data-ttu-id="274fe-609">삽입 하 라는 메시지가 표시 됩니다는 **테이블 URL** 이전에 수집 ([11 장 중 13 단계에서](#chapter-11---create-table-service)), Table Service를 만드는 동안.</span><span class="sxs-lookup"><span data-stu-id="274fe-609">You will be prompted to insert the **Table URL** that you collected earlier ([in step 13 of Chapter 11](#chapter-11---create-table-service)), while creating your Table Service.</span></span> <span data-ttu-id="274fe-610">URL을 삽입 한 후 (이었던 IoTMessages,이 과정에서) "하위 폴더" 테이블을 참조 하는 경로 부분을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-610">After inserting the URL, delete the portion of the path referring to the Table "sub-folder" (which was IoTMessages, in this course).</span></span> <span data-ttu-id="274fe-611">최종 결과 아래 이미지에 표시 된 대로 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-611">The final result should be as displayed in the image below.</span></span> <span data-ttu-id="274fe-612">클릭 **확인**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-612">Then click on **OK**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  <span data-ttu-id="274fe-614">삽입 하 라는 메시지가 표시 됩니다는 **저장소 키** 둔 ([11 장의 11 단계에서](#chapter-11---create-table-service)) Table Storage를 만드는 동안 이전 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-614">You will be prompted to insert the **Storage Key** that you noted ([in step 11 of Chapter 11](#chapter-11---create-table-service)) earlier while creating your Table Storage.</span></span> <span data-ttu-id="274fe-615">클릭 **Connect**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-615">Then click on **Connect**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. <span data-ttu-id="274fe-617">A **탐색 창 패널** 표시할 테이블 옆의 확인란을 선택 하 고 클릭 **부하**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-617">A **Navigator Panel** will be displayed, tick the box next to your Table and click on **Load**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. <span data-ttu-id="274fe-619">Power bi에서 테이블 로드 이제 되었지만 그 안에 값을 표시 하려면 쿼리 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-619">Your table has now been loaded on Power BI, but it requires a query to display the values in it.</span></span> <span data-ttu-id="274fe-620">이렇게 하려면 마우스 오른쪽 단추로 클릭에 있는 테이블 이름에는 **필드 패널** 화면의 오른쪽에 있는 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-620">To do so, right-click on the table name located in the **FIELDS panel** at the right side of the screen.</span></span> <span data-ttu-id="274fe-621">클릭 **쿼리 편집**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-621">Then click on **Edit Query**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. <span data-ttu-id="274fe-623">A **파워 쿼리 편집기** 테이블 표시 새 창으로 열립니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-623">A **Power Query Editor**  will open up as a new window, displaying your table.</span></span> <span data-ttu-id="274fe-624">이라는 단어를 클릭 **레코드** 내 합니다 *콘텐츠* 저장 된 콘텐츠를 시각화 하려면 테이블의 열입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-624">Click on the word **Record** within the *Content* column of the table, to visualize your stored content.</span></span>

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. <span data-ttu-id="274fe-626">클릭할 **Into 테이블**, 창의 왼쪽 위에 있는 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-626">Click on **Into Table**, at the top-left of the window.</span></span> 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. <span data-ttu-id="274fe-628">클릭할 **닫기 및 적용**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-628">Click on **Close & Apply**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. <span data-ttu-id="274fe-630">내 쿼리 로드 완료 되는 **필드 패널**, 화면 오른쪽에 해당 하는 매개 변수 상자 눈금 **이름** 및 **값**를 시각화를 **messagecontent가** 열 내용입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-630">Once it has finished loading the query, within the **FIELDS panel**, on the right side of the screen, tick the boxes corresponding to the parameters **Name** and **Value**, to visualize the **MessageContent** column content.</span></span>

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. <span data-ttu-id="274fe-632">클릭 합니다 **파란색 디스크 아이콘** 에서 원하는 폴더에서 작업 내용 저장 창의 왼쪽 위에서 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-632">Click on the **blue disk icon** at the top left of the window to save your work in a folder of your choice.</span></span>

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. <span data-ttu-id="274fe-634">이제 작업 영역에 테이블을 업로드 하려면 게시 단추를 클릭할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-634">You can now click on the Publish button to upload your table to your Workspace.</span></span> <span data-ttu-id="274fe-635">메시지가 표시 되 면 **내 작업 영역** 누릅니다 *선택*합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-635">When prompted, click **My workspace** and click *Select*.</span></span> <span data-ttu-id="274fe-636">기대 하시라 제출의 성공 결과를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-636">Wait for it to display the successful result of the submission.</span></span>

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> <span data-ttu-id="274fe-639">다음 장에서 특정 HoloLens입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-639">The following Chapter is HoloLens specific.</span></span> <span data-ttu-id="274fe-640">Power BI 아니며 현재 사용할 수는 몰입 형 응용 프로그램으로 Windows 혼합 현실 포털 (즉, Cliff 하우스)의 데스크톱 버전을 실행할 수 있지만 데스크톱 앱을 통해</span><span class="sxs-lookup"><span data-stu-id="274fe-640">Power BI is not currently availble as an immersive application, however you can run the desktop version in the Windows Mixed Reality Portal (aka Cliff House), through the Desktop app.</span></span>

## <a name="chapter-16---display-power-bi-data-on-hololens"></a><span data-ttu-id="274fe-641">16 장-HoloLens에서 표시 Power BI 데이터</span><span class="sxs-lookup"><span data-stu-id="274fe-641">Chapter 16 - Display Power BI data on HoloLens</span></span>

1. <span data-ttu-id="274fe-642">에 HoloLens에 로그인 합니다 **Microsoft Store**, 응용 프로그램 목록에서 해당 아이콘을 탭 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-642">On your HoloLens, log in to the **Microsoft Store**, by tapping on its icon in the applications list.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-87.png)

2. <span data-ttu-id="274fe-644">검색 한 후 다운로드 합니다 **Power BI** 응용 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-644">Search and then download the **Power BI** application.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-88.png)

3. <span data-ttu-id="274fe-646">시작 **Power BI** 응용 프로그램 목록에서.</span><span class="sxs-lookup"><span data-stu-id="274fe-646">Start **Power BI** from your applications list.</span></span> 

4. <span data-ttu-id="274fe-647">**Power BI** 에 로그인 하 라는 메시지 하 **Microsoft 365 계정**합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-647">**Power BI** might ask you to login to your **Microsoft 365 account**.</span></span>

5. <span data-ttu-id="274fe-648">한 번, 앱 내에서 작업 영역 표시 됩니다 기본적으로 아래 이미지에 표시 된 대로.</span><span class="sxs-lookup"><span data-stu-id="274fe-648">Once inside the app, the workspace should display by default as shown in the image below.</span></span> <span data-ttu-id="274fe-649">발생 하지 않는 경우 창의 왼쪽에 작업 영역 아이콘을 클릭 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-649">If that does not happen, simply click on the workspace icon on the left side of the window.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a><span data-ttu-id="274fe-651">에 IoT Hub 응용 프로그램을 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-651">Your finished your IoT Hub application</span></span>

<span data-ttu-id="274fe-652">축 하는 시뮬레이션 된 가상 머신 Edge 장치를 사용 하 여 IoT Hub 서비스를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-652">Congratulations, you have successfully created an IoT Hub Service, with a simulated Virtual Machine Edge device.</span></span> <span data-ttu-id="274fe-653">장치는 기계 학습 모델을 Power BI로 읽고 Microsoft HoloLens 내에서 시각화 하는 Azure 함수 앱에서 쉽게 처리 하는 Azure Table Service에 결과 통신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-653">Your device can  communicate the results of a machine learning model to an Azure Table Service, facilitated by an Azure Function App, which is read into Power BI, and visualized within a Microsoft HoloLens.</span></span>
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="274fe-655">보너스 연습</span><span class="sxs-lookup"><span data-stu-id="274fe-655">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="274fe-656">연습 1</span><span class="sxs-lookup"><span data-stu-id="274fe-656">Exercise 1</span></span>

<span data-ttu-id="274fe-657">테이블에 저장 된 메시징 구조를 확장 하 고 그래프로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-657">Expand the messaging structure stored in the table and display it as a graph.</span></span> <span data-ttu-id="274fe-658">더 많은 데이터를 수집 하 고 표시할 나중에 동일한 테이블에 저장 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-658">You might want to collect more data and store it in the same table, to be later displayed.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="274fe-659">연습 2</span><span class="sxs-lookup"><span data-stu-id="274fe-659">Exercise 2</span></span>

<span data-ttu-id="274fe-660">추가 만들기 "카메라 캡처" 모듈 분석할 카메라를 통해 이미지를 캡처할 수 있습니다 있도록 IoT 보드에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="274fe-660">Create an additional "camera capture" module to be deployed on the IoT board, so that it can capture images through the camera to be analyzed.</span></span>
