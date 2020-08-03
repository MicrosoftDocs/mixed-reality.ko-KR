---
title: HoloLens 연구 모드
description: 응용 프로그램은 HoloLens의 연구 모드를 사용 하 여 키 장치 센서 스트림 (깊이, 환경 추적 및 IR 반사)에 액세스할 수 있습니다.
author: hferrone
ms.author: v-haferr
ms.date: 07/31/2020
ms.topic: article
keywords: 연구 모드, cv, rs4, 컴퓨터 비전, 연구, HoloLens, HoloLens 2
ms.openlocfilehash: dd49186d1218b6a6a6c9a8d5943159daad3bcefb
ms.sourcegitcommit: 36316e2658d3dfa804d798b9f4fb2f9186052144
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/01/2020
ms.locfileid: "87507697"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="99576-104">HoloLens 연구 모드</span><span class="sxs-lookup"><span data-stu-id="99576-104">HoloLens Research Mode</span></span>

<span data-ttu-id="99576-105">연구 모드는 장치에서 키 센서에 대 한 액세스 권한을 제공 하기 위해 첫 번째 세대 HoloLens에서 도입 되었습니다. 특히 배포에 적합 하지 않은 연구 응용 프로그램에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="99576-105">Research Mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span>  <span data-ttu-id="99576-106">HoloLens 2의 연구 모드는 HoloLens 1의 기능을 유지 하며 추가 스트림에 대 한 액세스를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="99576-106">Research Mode for HoloLens 2 retains the capabilities of HoloLens 1, adding access to additional streams:</span></span>

* <span data-ttu-id="99576-107">**표시 되는 밝은 환경 추적 카메라** -헤드 추적 및 맵 작성을 위해 시스템에서 사용 하는 회색 크기의 카메라입니다.</span><span class="sxs-lookup"><span data-stu-id="99576-107">**Visible Light Environment Tracking Cameras** - Gray-scale cameras used by the system for head tracking and map building.</span></span>
* <span data-ttu-id="99576-108">**깊이 카메라** – 다음과 같은 두 가지 모드로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="99576-108">**Depth Camera** – Operates in two modes:</span></span>  
    + <span data-ttu-id="99576-109">직접 추적에 사용 되는 AHAT, 높은 빈도 (45 FPS) 심층 감지</span><span class="sxs-lookup"><span data-stu-id="99576-109">AHAT, high-frequency (45 FPS) near-depth sensing used for hand tracking.</span></span> <span data-ttu-id="99576-110">첫 번째 버전의 단기 throw 모드와는 달리 AHAT는 1 측정기 이상으로 단계를 래핑하는 의사 깊이를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="99576-110">Differently from the 1st version short-throw mode, AHAT gives pseudo-depth with phase wrap beyond 1 meter.</span></span> 
    + <span data-ttu-id="99576-111">[공간 매핑에서](spatial-mapping.md) 사용 되는 긴-발생 빈도가 낮은 빈도 (1-5 FPS)</span><span class="sxs-lookup"><span data-stu-id="99576-111">Long-throw, low-frequency (1-5 FPS) far-depth sensing used by [Spatial Mapping](spatial-mapping.md)</span></span>

* <span data-ttu-id="99576-112">HoloLens에서 깊이를 계산 하는 데 사용 하는 **두 가지 버전의 IR (반사 stream** )</span><span class="sxs-lookup"><span data-stu-id="99576-112">**Two versions of the IR-reflectivity stream** - Used by the HoloLens to compute depth.</span></span> <span data-ttu-id="99576-113">이러한 이미지는 적외선으로 표시 되며 주변에 표시 되는 빛의 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="99576-113">These images are illuminated by infrared and unaffected by ambient visible light.</span></span>

<span data-ttu-id="99576-114">HoloLens 2를 사용 하는 경우 아래 추가 입력에 액세스할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99576-114">If you're using a HoloLens 2 you also have access to the additional inputs below:</span></span>

* <span data-ttu-id="99576-115">**가 속도계** – 시스템에서 X, Y 및 Z 축과 무게를 따라 선형 가속을 결정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="99576-115">**Accelerometer** – Used by the system to determine linear acceleration along the X, Y and Z axes and gravity.</span></span>
* <span data-ttu-id="99576-116">**Gyro** – 시스템에서 회전을 결정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="99576-116">**Gyro** – Used by the system to determine rotations.</span></span>
* <span data-ttu-id="99576-117">**지자기 센터** – 시스템에서 절대 방향을 예측 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="99576-117">**Magnetometer** – Used by the system to estimate absolute orientation.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="99576-118">연구 모드는 현재 공개 미리 보기로 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="99576-118">Research Mode is currently in Public Preview.</span></span> <span data-ttu-id="99576-119">HoloLens 2 샘플, 자습서 및 전체 API 설명서는 연구 모드 Git 리포지토리에서 [Eccv 2020](https://eccv2020.eu/
 ) 에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99576-119">HoloLens 2 samples, tutorials, and full API documentation will be available at [ECCV 2020](https://eccv2020.eu/
 ) in the Research Mode Git repository.</span></span>

<span data-ttu-id="99576-120">![연구 모드 앱 스크린샷](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="99576-120">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="99576-121">*연구 모드에서 사용할 수 있는 8 개의 센서 스트림을 표시 하는 테스트 응용 프로그램의 혼합 현실 캡처*</span><span class="sxs-lookup"><span data-stu-id="99576-121">*A mixed reality capture of a test application that displays the eight sensor streams available in Research Mode*</span></span>

## <a name="usage"></a><span data-ttu-id="99576-122">사용량</span><span class="sxs-lookup"><span data-stu-id="99576-122">Usage</span></span>

<span data-ttu-id="99576-123">연구 모드는 Computer Vision 및 로봇 공학의 필드에서 새로운 아이디어를 탐색 하는 교육 및 산업 연구원을 위해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="99576-123">Research Mode is designed for academic and industrial researchers exploring new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="99576-124">엔터프라이즈 환경에 배포 되었거나 Microsoft Store 또는 다른 배포 채널을 통해 사용할 수 있는 응용 프로그램에는 적합 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="99576-124">It's not intended for applications deployed in enterprise environments or available through the Microsoft Store or other distribution channels.</span></span>

<span data-ttu-id="99576-125">또한 Microsoft는 연구 모드 또는 동등한 기능을 향후 하드웨어 또는 OS 업데이트에서 지원 하도록 보장 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="99576-125">Additionally, Microsoft doesn't provide assurances that Research Mode or equivalent functionality is going to be supported in future hardware or OS updates.</span></span> <span data-ttu-id="99576-126">그러나이를 사용 하 여 새 아이디어를 개발 하 고 테스트 하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="99576-126">However, this shouldn't stop you from using it to develop and test new ideas!</span></span>

## <a name="security-and-performance"></a><span data-ttu-id="99576-127">보안 및 성능</span><span class="sxs-lookup"><span data-stu-id="99576-127">Security and performance</span></span>

<span data-ttu-id="99576-128">연구 모드를 사용 하도록 설정 하면 일반적인 조건에서 HoloLens 2를 사용 하는 것 보다 더 많은 배터리 전력이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="99576-128">Be aware that enabling Research Mode uses more battery power than using the HoloLens 2 under normal conditions.</span></span> <span data-ttu-id="99576-129">이는 연구 모드 기능을 사용 하는 응용 프로그램이 실행 되 고 있지 않은 경우에도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="99576-129">This is true even if the application using the Research Mode features is not running.</span></span>  <span data-ttu-id="99576-130">응용 프로그램에서 센서 데이터를 오용 하는 경우이 모드를 사용 하도록 설정 하면 장치의 전반적인 보안이 낮아질 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99576-130">Enabling this mode can also lower the overall security of your device because applications may misuse sensor data.</span></span>  <span data-ttu-id="99576-131">장치 보안에 대 한 자세한 내용은 [HoloLens 보안 FAQ](https://docs.microsoft.com/hololens/hololens-faq-security)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99576-131">You can find more information on device security in the [HoloLens security FAQ](https://docs.microsoft.com/hololens/hololens-faq-security).</span></span>  

## <a name="device-support"></a><span data-ttu-id="99576-132">디바이스 지원</span><span class="sxs-lookup"><span data-stu-id="99576-132">Device support</span></span>
<table><span data-ttu-id="99576-133">
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    </span><span class="sxs-lookup"><span data-stu-id="99576-133">
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    </span></span><tr>
        <td><span data-ttu-id="99576-134"><strong>기능</strong></span><span class="sxs-lookup"><span data-stu-id="99576-134"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="99576-135"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1세대</strong></a></span><span class="sxs-lookup"><span data-stu-id="99576-135"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1st Gen</strong></a></span></span></td>
        <td><span data-ttu-id="99576-136"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="99576-136"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="99576-137">헤드 추적 카메라</span><span class="sxs-lookup"><span data-stu-id="99576-137">Head Tracking Cameras</span></span></td>
        <td><span data-ttu-id="99576-138">✔️</span><span class="sxs-lookup"><span data-stu-id="99576-138">✔️</span></span></td>
        <td><span data-ttu-id="99576-139">✔️</span><span class="sxs-lookup"><span data-stu-id="99576-139">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="99576-140">& IR 카메라 깊이</span><span class="sxs-lookup"><span data-stu-id="99576-140">Depth & IR Camera</span></span></td>
        <td><span data-ttu-id="99576-141">✔️</span><span class="sxs-lookup"><span data-stu-id="99576-141">✔️</span></span></td>
        <td><span data-ttu-id="99576-142">✔️</span><span class="sxs-lookup"><span data-stu-id="99576-142">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="99576-143">가속도계</span><span class="sxs-lookup"><span data-stu-id="99576-143">Accelerometer</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="99576-144">✔️</span><span class="sxs-lookup"><span data-stu-id="99576-144">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="99576-145">자이로스코프</span><span class="sxs-lookup"><span data-stu-id="99576-145">Gyroscope</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="99576-146">✔️</span><span class="sxs-lookup"><span data-stu-id="99576-146">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="99576-147">지자기 센터</span><span class="sxs-lookup"><span data-stu-id="99576-147">Magnetometer</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="99576-148">✔️</span><span class="sxs-lookup"><span data-stu-id="99576-148">✔️</span></span></td>
    </tr>
</table>

## <a name="enabling-research-mode-hololens-1st-gen-and-hololens-2"></a><span data-ttu-id="99576-149">연구 모드 사용 (HoloLens 1 Gen 및 HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="99576-149">Enabling Research Mode (HoloLens 1st Gen and HoloLens 2)</span></span>

<span data-ttu-id="99576-150">연구 모드는 개발자 모드의 확장입니다.</span><span class="sxs-lookup"><span data-stu-id="99576-150">Research Mode is an extension of Developer Mode.</span></span> <span data-ttu-id="99576-151">시작 하기 전에 연구 모드 설정에 액세스 하려면 장치의 개발자 기능을 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="99576-151">Before starting, the developer features of the device need to be enabled to access the Research Mode settings:</span></span> 

* <span data-ttu-id="99576-152">**시작 메뉴를 열고 설정 >** 한 다음 **업데이트**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="99576-152">Open **Start Menu > Settings** and select **Updates**.</span></span>
* <span data-ttu-id="99576-153">**개발자를 위해** 를 선택 하 고 **개발자 모드**를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="99576-153">Select **For Developers** and enable **Developer Mode**.</span></span>
* <span data-ttu-id="99576-154">아래로 스크롤하여 **장치 포털**을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="99576-154">Scroll down and enable **Device Portal**.</span></span>

<span data-ttu-id="99576-155">개발자 기능을 사용 하도록 설정한 후에는 [장치 포털에 연결](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) 하 여 연구 모드 기능을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="99576-155">After the developer features  are enabled, [connect to the device portal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) to enable the Research Mode features:</span></span>

* <span data-ttu-id="99576-156">**장치 포털**에서 **시스템 > 연구 모드로** 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="99576-156">Go to **System > Research Mode** in the **Device Portal**.</span></span>
* <span data-ttu-id="99576-157">**센서 스트림에 대 한 액세스 허용을**선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="99576-157">Select **Allow access to sensor stream**.</span></span>
* <span data-ttu-id="99576-158">페이지 맨 위에 있는 **전원** 메뉴 항목에서 장치를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="99576-158">Restart the device from the **Power** menu item at the top of the page.</span></span>

<span data-ttu-id="99576-159">장치를 다시 시작한 후에는 **장치 포털** 을 통해 로드 된 응용 프로그램이 연구 모드 스트림에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99576-159">Once you've restarted the device, the applications loaded through the **Device Portal** can access Research Mode streams.</span></span>

<span data-ttu-id="99576-160">![HoloLens 장치 포털의 연구 모드 탭](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="99576-160">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="99576-161">*HoloLens 장치 포털의 연구 모드 창*</span><span class="sxs-lookup"><span data-stu-id="99576-161">*Research Mode window in the HoloLens Device Portal*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="99576-162">HoloLens 2의 연구 모드는 빌드 19041.1356부터 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99576-162">Research Mode for HoloLens 2 is available beginning with build 19041.1356.</span></span> <span data-ttu-id="99576-163">이전 빌드에서 액세스 해야 하는 경우 [Insider preview](https://docs.microsoft.com/hololens/hololens-insider) 프로그램에 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="99576-163">If you need access in an earlier build, sign up for our [Insider Preview](https://docs.microsoft.com/hololens/hololens-insider) program.</span></span>

### <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="99576-164">앱에서 센서 데이터 사용</span><span class="sxs-lookup"><span data-stu-id="99576-164">Using sensor data in your apps</span></span>

<span data-ttu-id="99576-165">응용 프로그램은 [미디어 파운데이션](https://msdn.microsoft.com/library/windows/desktop/ms694197)를 통해 사진 및 비디오 카메라 스트림에 액세스 하는 것과 동일한 방식으로 센서 스트림 데이터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99576-165">Applications can access the sensor stream data in the same way that photo and video camera streams are accessed through [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span></span> 

<span data-ttu-id="99576-166">HoloLens 개발에 대해 작동 하는 모든 Api는 연구 모드 에서도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99576-166">All APIs that work for HoloLens development are also available in Research Mode.</span></span> <span data-ttu-id="99576-167">특히 응용 프로그램은 각 센서 프레임 캡처 시간에서 6DoF 공간에 HoloLens가 있는 위치를 정확 하 게 알고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99576-167">In particular, the application  knows precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="99576-168">다양 한 연구 모드 스트림에 액세스 하는 방법, [내장 함수 및 extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)를 사용 하는 방법 및 [HoloLensForCV GitHub 리포지토리](https://github.com/Microsoft/HoloLensForCV) 리포지토리에서 스트림을 기록 하는 방법에 대 한 샘플 응용 프로그램을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99576-168">You can find sample applications on how to access the various Research Mode streams, how to use the [intrinsics and extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world), and how to record streams in the [HoloLensForCV GitHub repo](https://github.com/Microsoft/HoloLensForCV) repo.</span></span>

 > [!NOTE]
 > <span data-ttu-id="99576-169">이번에는 HoloLensForCV 샘플이 HoloLens 2에서 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="99576-169">At this time, the HoloLensForCV sample doesn't work on HoloLens 2.</span></span>

## <a name="support"></a><span data-ttu-id="99576-170">지원</span><span class="sxs-lookup"><span data-stu-id="99576-170">Support</span></span>

<span data-ttu-id="99576-171">HoloLensForCV 리포지토리에서 [문제 추적기](https://github.com/Microsoft/HololensForCV/issues) 를 사용 하 여 피드백을 게시 하 고 알려진 문제를 추적 하세요.</span><span class="sxs-lookup"><span data-stu-id="99576-171">Please use the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository to post feedback and track known issues.</span></span>

## <a name="see-also"></a><span data-ttu-id="99576-172">참고 항목</span><span class="sxs-lookup"><span data-stu-id="99576-172">See also</span></span>

* [<span data-ttu-id="99576-173">Microsoft 미디어 파운데이션</span><span class="sxs-lookup"><span data-stu-id="99576-173">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="99576-174">HoloLensForCV GitHub 리포지토리</span><span class="sxs-lookup"><span data-stu-id="99576-174">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="99576-175">Windows 디바이스 포털 사용</span><span class="sxs-lookup"><span data-stu-id="99576-175">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
