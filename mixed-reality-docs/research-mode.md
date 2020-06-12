---
title: HoloLens 연구 모드
description: 응용 프로그램은 HoloLens의 연구 모드를 사용 하 여 키 장치 센서 스트림 (깊이, 환경 추적 및 IR 반사)에 액세스할 수 있습니다.
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
keywords: 연구 모드, cv, rs4, 컴퓨터 비전, 연구, HoloLens, HoloLens 2
ms.openlocfilehash: 62b82e3a36452d4b104bf04999e556ec19d2a5e3
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720399"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="1353c-104">HoloLens 연구 모드</span><span class="sxs-lookup"><span data-stu-id="1353c-104">HoloLens Research mode</span></span>

## <a name="overview"></a><span data-ttu-id="1353c-105">개요</span><span class="sxs-lookup"><span data-stu-id="1353c-105">Overview</span></span>

<span data-ttu-id="1353c-106">연구 모드는 장치에서 키 센서에 대 한 액세스 권한을 제공 하기 위해 첫 번째 세대 HoloLens에서 도입 되었습니다. 특히 배포에 적합 하지 않은 연구 응용 프로그램에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1353c-106">Research mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span> <span data-ttu-id="1353c-107">이제 다음 입력에서 데이터를 수집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1353c-107">You can now gather data from the following inputs:</span></span>

* <span data-ttu-id="1353c-108">**표시 되는 밝은 환경 추적 카메라** -헤드 추적 및 맵 작성을 위해 시스템에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1353c-108">**Visible Light Environment Tracking Cameras** - Used by the system for head tracking and map building.</span></span>
* <span data-ttu-id="1353c-109">**깊이 카메라** – 다음과 같은 두 가지 모드로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="1353c-109">**Depth Camera** – Operates in two modes:</span></span>  
    + <span data-ttu-id="1353c-110">[손으로 추적](interaction-fundamentals.md) 하는 데 사용 되는 짧은 throw, 높은 빈도 (30fps) 근거리 감지</span><span class="sxs-lookup"><span data-stu-id="1353c-110">Short-throw, high-frequency (30 FPS) near-depth sensing used for [Hand Tracking](interaction-fundamentals.md)</span></span>
    + <span data-ttu-id="1353c-111">[공간 매핑에서](spatial-mapping.md) 사용 되는 긴-발생 빈도가 낮은 빈도 (1-5 FPS)</span><span class="sxs-lookup"><span data-stu-id="1353c-111">Long-throw, low-frequency (1-5 FPS) far-depth sensing used by [Spatial Mapping](spatial-mapping.md)</span></span>
* <span data-ttu-id="1353c-112">HoloLens에서 깊이를 계산 하는 데 사용 하는 **두 가지 버전의 IR (반사 stream** )</span><span class="sxs-lookup"><span data-stu-id="1353c-112">**Two versions of the IR-reflectivity stream** - Used by the HoloLens to compute depth.</span></span> <span data-ttu-id="1353c-113">이러한 이미지는 적외선으로 표시 되며 주변에 표시 되는 빛의 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1353c-113">These images are illuminated by infrared and unaffected by ambient visible light.</span></span>

<span data-ttu-id="1353c-114">HoloLens 2를 사용 하는 경우 다음 입력에도 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1353c-114">If you're using a HoloLens 2 you will also be able to access the following inputs:</span></span>

* <span data-ttu-id="1353c-115">**가 속도계** – 시스템에서 X, Y 및 Z 축과 무게를 따라 선형 가속을 결정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1353c-115">**Accelerometer** – Used by the system to determine linear acceleration along the X, Y and Z axes and gravity.</span></span>
* <span data-ttu-id="1353c-116">**Gyro** – 시스템에서 회전을 결정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1353c-116">**Gyro** – Used by the system to determine rotations.</span></span>
* <span data-ttu-id="1353c-117">**지자기 센터** – 시스템에서 절대 방향을 예측 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1353c-117">**Magnetometer** – Used by the system to estimate absolute orientation.</span></span>

<span data-ttu-id="1353c-118">![연구 모드 앱 스크린샷](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="1353c-118">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="1353c-119">*연구 모드에서 사용할 수 있는 8 개의 센서 스트림을 표시 하는 테스트 응용 프로그램의 혼합 현실 캡처*</span><span class="sxs-lookup"><span data-stu-id="1353c-119">*A mixed reality capture of a test application that displays the eight sensor streams available in Research mode*</span></span>

> [!NOTE]
> <span data-ttu-id="1353c-120">[Windows 10 4 월 2018 업데이트](release-notes-april-2018.md) 의 일부로 Research 모드 기능이 추가 되었으며 이전 릴리스에서는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1353c-120">The Research Mode feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md) for HoloLens, and is not available on earlier releases.</span></span>

## <a name="usage"></a><span data-ttu-id="1353c-121">사용</span><span class="sxs-lookup"><span data-stu-id="1353c-121">Usage</span></span>

<span data-ttu-id="1353c-122">연구 모드는 Computer Vision 및 로봇 공학의 필드에서 새로운 아이디어를 탐색 하는 교육 및 산업 연구원을 위해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1353c-122">Research mode is designed for academic and industrial researchers exploring new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="1353c-123">엔터프라이즈 환경에 배포 되었거나 Microsoft Store 또는 다른 배포 채널을 통해 사용할 수 있는 응용 프로그램에는 적합 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1353c-123">It's not intended for applications deployed in enterprise environments or available through the Microsoft Store or other distribution channels.</span></span>

<span data-ttu-id="1353c-124">또한 Microsoft는 연구 모드 또는 동등한 기능을 향후 하드웨어 또는 OS 업데이트에서 지원 하도록 보장 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1353c-124">Additionally, Microsoft doesn't provide assurances that research mode or equivalent functionality is going to be supported in future hardware or OS updates.</span></span> <span data-ttu-id="1353c-125">그러나이를 사용 하 여 새 아이디어를 개발 하 고 테스트 하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1353c-125">However, this shouldn't stop you from using it to develop and test new ideas!</span></span>

## <a name="security-and-performance"></a><span data-ttu-id="1353c-126">보안 및 성능</span><span class="sxs-lookup"><span data-stu-id="1353c-126">Security and performance</span></span>

<span data-ttu-id="1353c-127">연구 모드를 사용 하도록 설정 하면 일반적인 조건에서 HoloLens 2를 사용 하는 것 보다 더 많은 배터리 전력이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1353c-127">Be aware that enabling research mode uses more battery power than using the HoloLens 2 under normal conditions.</span></span> <span data-ttu-id="1353c-128">이는 연구 모드 기능을 사용 하는 응용 프로그램이 실행 되 고 있지 않은 경우에도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="1353c-128">This is true even if the application using the research mode features is not running.</span></span>  <span data-ttu-id="1353c-129">응용 프로그램에서 센서 데이터를 오용 하는 경우이 모드를 사용 하도록 설정 하면 장치의 전반적인 보안이 낮아질 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1353c-129">Enabling this mode can also lower the overall security of your device because applications may misuse sensor data.</span></span>  <span data-ttu-id="1353c-130">장치 보안에 대 한 자세한 내용은 [HoloLens 보안 FAQ](https://docs.microsoft.com/hololens/hololens-faq-security)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1353c-130">You can find more information on device security in the [HoloLens security FAQ](https://docs.microsoft.com/hololens/hololens-faq-security).</span></span>  


## <a name="device-support"></a><span data-ttu-id="1353c-131">디바이스 지원</span><span class="sxs-lookup"><span data-stu-id="1353c-131">Device support</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    <!-- <col width="33%" /> -->
    </colgroup>
    <tr>
        <td><span data-ttu-id="1353c-132"><strong>기능</strong></span><span class="sxs-lookup"><span data-stu-id="1353c-132"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="1353c-133"><a href="hololens-hardware-details.md"><strong>HoloLens 1 Gen</strong></a></span><span class="sxs-lookup"><span data-stu-id="1353c-133"><a href="hololens-hardware-details.md"><strong>HoloLens 1st Gen</strong></a></span></span></td>
        <!-- <td><a href="hololens2-hardware.md"><strong>HoloLens 2</strong></a></td> -->
    </tr>
     <tr>
        <td><span data-ttu-id="1353c-134">헤드 추적 카메라</span><span class="sxs-lookup"><span data-stu-id="1353c-134">Head Tracking Cameras</span></span></td>
        <td><span data-ttu-id="1353c-135">✔️</span><span class="sxs-lookup"><span data-stu-id="1353c-135">✔️</span></span></td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td><span data-ttu-id="1353c-136">& IR 카메라 깊이</span><span class="sxs-lookup"><span data-stu-id="1353c-136">Depth & IR Camera</span></span></td>
        <td><span data-ttu-id="1353c-137">✔️</span><span class="sxs-lookup"><span data-stu-id="1353c-137">✔️</span></span></td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td><span data-ttu-id="1353c-138">가속도계</span><span class="sxs-lookup"><span data-stu-id="1353c-138">Accelerometer</span></span></td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td><span data-ttu-id="1353c-139">자이로스코프</span><span class="sxs-lookup"><span data-stu-id="1353c-139">Gyroscope</span></span></td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td><span data-ttu-id="1353c-140">지자기 센터</span><span class="sxs-lookup"><span data-stu-id="1353c-140">Magnetometer</span></span></td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
</table>

> [!IMPORTANT]
> <span data-ttu-id="1353c-141">HoloLens 2에 대 한 연구 모드 지원은 7 월 2020에 공개 미리 보기로 제공 될 예정 이며 위에 나열 된 모든 기능을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="1353c-141">Research Mode support for HoloLens 2 is expected to be available in public preview in July 2020 and will include all the features listed above.</span></span> <span data-ttu-id="1353c-142">자세한 내용은 다시 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="1353c-142">Please check back for more information.</span></span> 

## <a name="enabling-research-mode"></a><span data-ttu-id="1353c-143">연구 모드 사용</span><span class="sxs-lookup"><span data-stu-id="1353c-143">Enabling Research mode</span></span>

<span data-ttu-id="1353c-144">연구 모드는 개발자 모드의 확장입니다.</span><span class="sxs-lookup"><span data-stu-id="1353c-144">Research mode is an extension of Developer Mode.</span></span> <span data-ttu-id="1353c-145">시작 하기 전에 연구 모드 설정에 액세스 하려면 장치의 개발자 기능을 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1353c-145">Before starting, the developer features of the device need to be enabled to access the research mode settings:</span></span> 

* <span data-ttu-id="1353c-146">**시작 메뉴를 열고 설정 >** 한 다음 **업데이트**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1353c-146">Open **Start Menu > Settings** and select **Updates**.</span></span>
* <span data-ttu-id="1353c-147">**개발자를 위해** 를 선택 하 고 **개발자 모드**를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1353c-147">Select **For Developers** and enable **Developer Mode**.</span></span>
* <span data-ttu-id="1353c-148">아래로 스크롤하여 **장치 포털**을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1353c-148">Scroll down and enable **Device Portal**.</span></span>

<span data-ttu-id="1353c-149">개발자 기능을 사용 하도록 설정한 후에는 [장치 포털에 연결](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) 하 여 연구 모드 기능을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1353c-149">After the developer features  are enabled, [connect to the device portal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) to enable the research mode features.</span></span>

<span data-ttu-id="1353c-150">*HoloLens 1 Gen*:</span><span class="sxs-lookup"><span data-stu-id="1353c-150">On *HoloLens 1st Gen*:</span></span>

* <span data-ttu-id="1353c-151">**장치 포털**에서 **시스템 > 연구 모드로** 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="1353c-151">Go to **System > Research mode** in the **Device Portal**.</span></span>
* <span data-ttu-id="1353c-152">**센서 스트림에 대 한 액세스 허용을**선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1353c-152">Select **Allow access to sensor stream**.</span></span>
* <span data-ttu-id="1353c-153">페이지 맨 위에 있는 **전원** 메뉴 항목에서 장치를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="1353c-153">Restart the device from the **Power** menu item at the top of the page.</span></span>

<span data-ttu-id="1353c-154">장치를 다시 시작한 후에는 **장치 포털** 을 통해 로드 된 응용 프로그램이 연구 모드 스트림에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1353c-154">Once you've restarted the device, the applications loaded through the **Device Portal** can access Research mode streams.</span></span>

<span data-ttu-id="1353c-155">![HoloLens 장치 포털의 연구 모드 탭](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="1353c-155">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="1353c-156">*HoloLens 장치 포털의 연구 모드 창*</span><span class="sxs-lookup"><span data-stu-id="1353c-156">*Research mode window in the HoloLens Device Portal*</span></span>

## <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="1353c-157">앱에서 센서 데이터 사용</span><span class="sxs-lookup"><span data-stu-id="1353c-157">Using sensor data in your apps</span></span>

<span data-ttu-id="1353c-158">*HoloLens 1 Gen*</span><span class="sxs-lookup"><span data-stu-id="1353c-158">*HoloLens 1st Gen*</span></span>

<span data-ttu-id="1353c-159">응용 프로그램은 [미디어 파운데이션](https://msdn.microsoft.com/library/windows/desktop/ms694197)를 통해 사진 및 비디오 카메라 스트림에 액세스 하는 것과 동일한 방식으로 센서 스트림 데이터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1353c-159">Applications can access the sensor stream data in the same way that photo and video camera streams are accessed through [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span></span> 

<span data-ttu-id="1353c-160">HoloLens 개발에 대해 작동 하는 모든 Api는 연구 모드 에서도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1353c-160">All APIs that work for HoloLens development are also available in Research mode.</span></span> <span data-ttu-id="1353c-161">특히 응용 프로그램은 각 센서 프레임 캡처 시간에서 6DoF 공간에 HoloLens가 있는 위치를 정확 하 게 알고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1353c-161">In particular, the application  knows precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="1353c-162">다양 한 연구 모드 스트림에 액세스 하는 방법, [내장 함수 및 extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)를 사용 하는 방법 및 [HoloLensForCV GitHub 리포지토리](https://github.com/Microsoft/HoloLensForCV) 리포지토리에서 스트림을 기록 하는 방법에 대 한 샘플 응용 프로그램을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1353c-162">You can find sample applications on how to access the various Research mode streams, how to use the [intrinsics and extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world), and how to record streams in the [HoloLensForCV GitHub repo](https://github.com/Microsoft/HoloLensForCV) repo.</span></span>

 > [!NOTE]
 > <span data-ttu-id="1353c-163">이번에는 HoloLensForCV 샘플이 HoloLens 2에서 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1353c-163">At this time, the HoloLensForCV sample doesn't work on HoloLens 2.</span></span>

## <a name="known-issues"></a><span data-ttu-id="1353c-164">알려진 문제</span><span class="sxs-lookup"><span data-stu-id="1353c-164">Known issues</span></span>

<span data-ttu-id="1353c-165">HoloLensForCV 리포지토리에서 [문제 추적기](https://github.com/Microsoft/HololensForCV/issues) 를 사용 하 여 알려진 문제를 따를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1353c-165">You can use the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository to follow known issues.</span></span>

## <a name="see-also"></a><span data-ttu-id="1353c-166">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1353c-166">See also</span></span>

* [<span data-ttu-id="1353c-167">Microsoft 미디어 파운데이션</span><span class="sxs-lookup"><span data-stu-id="1353c-167">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="1353c-168">HoloLensForCV GitHub 리포지토리</span><span class="sxs-lookup"><span data-stu-id="1353c-168">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="1353c-169">Windows 디바이스 포털 사용</span><span class="sxs-lookup"><span data-stu-id="1353c-169">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
