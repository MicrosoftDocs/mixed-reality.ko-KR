---
title: HoloLens 연구 모드
description: HoloLens에서 연구 모드를 사용 하 여 응용 프로그램 주요 장치 센서 스트림 (깊이, 추적, 환경 및 IR 반사) 액세스할 수 있습니다.
author: davidgedye
ms.author: dgedye
ms.date: 05/03/2018
ms.topic: article
keywords: 모드, cv, rs4, 컴퓨터 비전, HoloLens 연구 조사
ms.openlocfilehash: 5feda021bd6a1a90fd98c751b1cea768eed980af
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597510"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="e9b9b-104">HoloLens 연구 모드</span><span class="sxs-lookup"><span data-stu-id="e9b9b-104">HoloLens Research mode</span></span>

> [!NOTE]
> <span data-ttu-id="e9b9b-105">일부로이 기능이 추가 되었습니다 합니다 [Windows 10 2018 년 4 월 업데이트](release-notes-april-2018.md) HoloLens에 대 한는 이전 버전에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e9b9b-105">This feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md) for HoloLens, and is not available on earlier releases.</span></span>

<span data-ttu-id="e9b9b-106">Research 모드는 HoloLens 장치에서 키 센서에 대 한 응용 프로그램 액세스를 제공 하는의 새로운 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="e9b9b-106">Research mode is a new capability of HoloLens that provides application access to the key sensors on the device.</span></span> <span data-ttu-id="e9b9b-107">이러한 개체는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e9b9b-107">These include:</span></span>
- <span data-ttu-id="e9b9b-108">네 가지 환경 맵 빌드 및 헤드 추적에 대 한 시스템에서 사용 하는 카메라를 추적 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b9b-108">The four environment tracking cameras used by the system for map building and head tracking.</span></span>
- <span data-ttu-id="e9b9b-109">두 버전에 대 한 높은 빈도 (30 FPS) 깊이 거의 감지 일반적으로 사용 되는 추적에 직접 및 낮은 빈도 (1 FPS) 먼 깊이 감지에 대 한 다른의 깊이 카메라 데이터의 현재 공간 매핑 사용</span><span class="sxs-lookup"><span data-stu-id="e9b9b-109">Two versions of the depth camera data – one for high-frequency (30 FPS) near-depth sensing, commonly used in hand tracking, and the other for lower-frequency (1 FPS) far-depth sensing, currently used by Spatial Mapping,</span></span>
- <span data-ttu-id="e9b9b-110">이러한 이미지는 HoloLens에서 표시등이 되며 합리적으로 영향을 받지 한 앰비언트 조명으로 깊이 있지만 그 자체로 유용을 계산 하는 HoloLens에서 사용 하는 IR 반사 스트림의 두 가지 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="e9b9b-110">Two versions of an IR-reflectivity stream, used by the HoloLens to compute depth, but valuable in its own right as these images are illuminated from the HoloLens and reasonably unaffected by ambient light.</span></span>

<span data-ttu-id="e9b9b-111">![Research 모드 앱 스크린 샷](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="e9b9b-111">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="e9b9b-112">*연구 모드에서 사용할 수 있는 8 개 센서 스트림을 표시 하는 테스트 응용 프로그램의 혼합된 현실 캡처*</span><span class="sxs-lookup"><span data-stu-id="e9b9b-112">*A mixed reality capture of a test application that displays the eight sensor streams available in Research mode*</span></span>

## <a name="device-support"></a><span data-ttu-id="e9b9b-113">장치 지원</span><span class="sxs-lookup"><span data-stu-id="e9b9b-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="e9b9b-114">기능</span><span class="sxs-lookup"><span data-stu-id="e9b9b-114">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="e9b9b-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="e9b9b-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="e9b9b-116"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="e9b9b-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="e9b9b-117">연구 모드</span><span class="sxs-lookup"><span data-stu-id="e9b9b-117">Research mode</span></span></td><td style="text-align: center;"> <span data-ttu-id="e9b9b-118">✔️</span><span class="sxs-lookup"><span data-stu-id="e9b9b-118">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

## <a name="before-using-research-mode"></a><span data-ttu-id="e9b9b-119">연구 모드를 사용 하기 전에</span><span class="sxs-lookup"><span data-stu-id="e9b9b-119">Before using Research mode</span></span>

<span data-ttu-id="e9b9b-120">연구 모드 라는 잘: Computer Vision 및 로봇 공학의 필드에 새로운 아이디어를 사용해 교육 및 산업 연구원이 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e9b9b-120">Research mode is well named: it is intended for academic and industrial researchers trying out new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="e9b9b-121">엔터프라이즈 배포 하거나 Microsoft Store 사용할 수 있는 응용 프로그램에 대 한 연구 모드를 사용 하는 것이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e9b9b-121">Research mode is not intended for applications that will be deployed across an enterprise or made available in the Microsoft Store.</span></span> <span data-ttu-id="e9b9b-122">이 대 한 이유는 연구 모드 장치의 보안을 줄이고 하 고 일반적인 작업 보다 훨씬 더 많은 배터리 전원 소모입니다.</span><span class="sxs-lookup"><span data-stu-id="e9b9b-122">The reason for this is that Research mode lowers the security of your device and consumes significantly more battery power than normal operation.</span></span> <span data-ttu-id="e9b9b-123">이후 모든 장치에서이 모드를 지원 하기 위해 Microsoft 커밋하지 않는 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b9b-123">Microsoft is not committing to supporting this mode on any future devices.</span></span> <span data-ttu-id="e9b9b-124">따라서 좋습니다 개발 하 고 새로운 아이디어; 테스트 사용 그러나 광범위 하 게 연구 모드를 사용 하거나 계속 이후 하드웨어에서 작동 하는 모든 보증 하는 응용 프로그램을 배포할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e9b9b-124">Thus, we recommend you use it to develop and test new ideas; however, you will not be able to widely deploy applications that use Research mode or have any assurance that it will continue to work on future hardware.</span></span>

## <a name="enabling-research-mode"></a><span data-ttu-id="e9b9b-125">연구 모드를 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="e9b9b-125">Enabling Research mode</span></span>

<span data-ttu-id="e9b9b-126">Research 모드는 개발자 모드의 하위 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="e9b9b-126">Research mode is a sub-mode of developer mode.</span></span> <span data-ttu-id="e9b9b-127">설정 앱의 개발자 모드를 사용 하도록 설정 하려면 먼저 (**설정 > 업데이트 및 보안 > 개발자를 위한**):</span><span class="sxs-lookup"><span data-stu-id="e9b9b-127">You first need to enable developer mode in the Settings app (**Settings > Update & Security > For developers**):</span></span>

1. <span data-ttu-id="e9b9b-128">"개발자 기능을 사용 합니다."로 **에서**</span><span class="sxs-lookup"><span data-stu-id="e9b9b-128">Set "Use developer features" to **On**</span></span>
2. <span data-ttu-id="e9b9b-129">"장치 포털을 사용 합니다."로 **에서**</span><span class="sxs-lookup"><span data-stu-id="e9b9b-129">Set "Enable Device Portal" to **On**</span></span>

<span data-ttu-id="e9b9b-130">에 HoloLens의 IP 주소로 이동 후에 HoloLens와 같은 Wi-fi 네트워크에 연결 된 웹 브라우저를 사용 하 여 (수집한 **설정 > 네트워크 및 인터넷 > Wi-fi > 하드웨어 속성**).</span><span class="sxs-lookup"><span data-stu-id="e9b9b-130">Then using a web browser that is connected to the same Wi-Fi network as your HoloLens, navigate to the IP address of your HoloLens (obtained through **Settings > Network & Internet > Wi-Fi > Hardware properties**).</span></span> <span data-ttu-id="e9b9b-131">이 [장치 포털](using-the-windows-device-portal.md), 포털의 "System" 섹션에서 "연구 모드" 페이지를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9b9b-131">This is the [Device Portal](using-the-windows-device-portal.md), and you will find a "Research mode" page in the "System" section of the portal:</span></span>

<span data-ttu-id="e9b9b-132">![HoloLens 장치 포털의 연구 Mode 탭](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="e9b9b-132">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="e9b9b-133">*HoloLens 장치 포털에서 연구 모드*</span><span class="sxs-lookup"><span data-stu-id="e9b9b-133">*Research mode in the HoloLens Device Portal*</span></span>

<span data-ttu-id="e9b9b-134">선택한 후 **센서 스트림에 대 한 액세스 허용**, HoloLens 다시 부팅 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b9b-134">After selecting **Allow access to sensor streams**, you will need to reboot HoloLens.</span></span> <span data-ttu-id="e9b9b-135">장치 포털 페이지의 맨 위에 있는 "Power" 메뉴 항목에서에서이 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9b9b-135">You can do this from the Device Portal, under the "Power" menu item at the top of the page.</span></span>

<span data-ttu-id="e9b9b-136">장치 다시 부팅 된 후 장치 포털을 통해 로드 된 응용 프로그램 연구 모드 스트림에 액세스할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b9b-136">Once your device has rebooted, applications that have been loaded through Device Portal should be able to access Research mode streams.</span></span>

## <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="e9b9b-137">앱에서 센서 데이터를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="e9b9b-137">Using sensor data in your apps</span></span>

<span data-ttu-id="e9b9b-138">응용 프로그램 열어 센서 스트림 데이터를 액세스할 수 있습니다 [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) 사진/비디오 카메라 스트림에 액세스 하는 동일한 방식으로 스트림 합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b9b-138">Applications can access sensor stream data by opening [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) streams in exactly the same way they access the photo/video camera stream.</span></span> 

<span data-ttu-id="e9b9b-139">HoloLens 개발을 위한 작동 하는 모든 Api 연구 모드에 있을 때 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9b9b-139">All APIs that work for HoloLens development are also available when in Research mode.</span></span> <span data-ttu-id="e9b9b-140">특히 응용 프로그램은 정확 하 게 HoloLens 인 6DoF 공간에서 각 센서 프레임 캡처 시간의 파악할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9b9b-140">In particular, the application can know precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="e9b9b-141">다양 한 연구 모드 스트림에 액세스 하는 방법, extrinsics, 고 내장 함수를 사용 하는 방법 및 스트림을 기록 하는 방법을 보여 주는 샘플 응용 프로그램에서 사용할 수는 [HoloLensForCV GitHub 리포지토리](https://github.com/Microsoft/HoloLensForCV)합니다.</span><span class="sxs-lookup"><span data-stu-id="e9b9b-141">Sample applications showing how you access the various Research mode streams, how to use the intrinsics and extrinsics, and how to record streams are available in the [HoloLensForCV GitHub repo](https://github.com/Microsoft/HoloLensForCV).</span></span>

## <a name="known-issues"></a><span data-ttu-id="e9b9b-142">알려진 문제</span><span class="sxs-lookup"><span data-stu-id="e9b9b-142">Known issues</span></span>

<span data-ttu-id="e9b9b-143">참조를 [문제 추적기](https://github.com/Microsoft/HololensForCV/issues) HoloLensForCV 리포지토리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9b9b-143">See the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository.</span></span>

## <a name="see-also"></a><span data-ttu-id="e9b9b-144">참조</span><span class="sxs-lookup"><span data-stu-id="e9b9b-144">See also</span></span>

* [<span data-ttu-id="e9b9b-145">Microsoft Media Foundation</span><span class="sxs-lookup"><span data-stu-id="e9b9b-145">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="e9b9b-146">HoloLensForCV GitHub 리포지토리</span><span class="sxs-lookup"><span data-stu-id="e9b9b-146">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="e9b9b-147">Windows Device Portal 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="e9b9b-147">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
