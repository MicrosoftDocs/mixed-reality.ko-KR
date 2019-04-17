---
title: 찾을 수 있는 카메라
description: HoloLens 프런트 연결 카메라에 대 한 일반 정보입니다.
author: wguyman
ms.author: wguyman
ms.date: 02/24/2019
ms.topic: article
keywords: 카메라, hololens, 색 카메라 프런트 연결
ms.openlocfilehash: ffcd6faf15dd8556db393237d468a3cdf60e4bdb
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603622"
---
# <a name="locatable-camera"></a><span data-ttu-id="f2959-104">찾을 수 있는 카메라</span><span class="sxs-lookup"><span data-stu-id="f2959-104">Locatable camera</span></span>

<span data-ttu-id="f2959-105">HoloLens 앞면의 사용자에 게 확인 하려면 앱을 사용 하도록 설정 하는 장치는 탑재 된 세계 지향 카메라를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-105">HoloLens includes a world-facing camera mounted on the front of the device which enables apps to see what the user sees.</span></span> <span data-ttu-id="f2959-106">스마트폰, 노트북 또는 데스크톱에서 색 카메라에 대 한 것 처럼 개발자가에 대 한 액세스 및 카메라 컨트롤입니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-106">Developers have access to and control of the camera just as they would for color cameras on smartphones, portables, or desktops.</span></span> <span data-ttu-id="f2959-107">동일한 유니버설 windows [미디어 캡처](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx) windows media foundation HoloLens 작업할 모바일 및 데스크톱에서 작동 하는 Api입니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-107">The same universal windows [media capture](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx) and windows media foundation APIs that work on mobile and desktop work on HoloLens.</span></span> <span data-ttu-id="f2959-108">Unity [이러한 windows Api도 래핑](locatable-camera-in-unity.md) 일반 사진 및 비디오 (홀로그램 없이 또는)에서 카메라의 위치 및 큐브 뷰를 찾기 등의 작업에 대 한 HoloLens에서 카메라의 단순한 사용을 추상화 하는 장면입니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-108">Unity [has also wrapped these windows APIs](locatable-camera-in-unity.md) to abstract simple usage of the camera on HoloLens for tasks such as taking regular photos and videos (with or without holograms) and locating the camera's position in and perspective on the scene.</span></span>

## <a name="device-camera-information"></a><span data-ttu-id="f2959-109">장치 카메라 정보</span><span class="sxs-lookup"><span data-stu-id="f2959-109">Device camera information</span></span>

### <a name="hololens-first-generation"></a><span data-ttu-id="f2959-110">HoloLens (초기)</span><span class="sxs-lookup"><span data-stu-id="f2959-110">HoloLens (first-generation)</span></span>

* <span data-ttu-id="f2959-111">흰색 자동 분산, 자동 노출 및 전체 이미지 처리 파이프를 사용 하 여 고정된 포커스 (PV) 사진/비디오 카메라</span><span class="sxs-lookup"><span data-stu-id="f2959-111">Fixed focus photo/video (PV) camera, with auto white balance, auto exposure, and full image processing pipe</span></span>
* <span data-ttu-id="f2959-112">카메라 활성화 될 때마다 전 세계 연결 흰색 개인 LED 켜 집니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-112">White Privacy LED facing the world will illuminate whenever the camera is active</span></span>
* <span data-ttu-id="f2959-113">카메라 30, 24, 20, 15 및 5 fps (모든 모드 16 9 가로 세로 비율을은) 다음과 같은 모드를 지원 합니다.:</span><span class="sxs-lookup"><span data-stu-id="f2959-113">The camera supports the following modes (all modes are 16:9 aspect ratio) at 30, 24, 20, 15, and 5 fps:</span></span>

  |  <span data-ttu-id="f2959-114">비디오</span><span class="sxs-lookup"><span data-stu-id="f2959-114">Video</span></span>  |  <span data-ttu-id="f2959-115">미리 보기</span><span class="sxs-lookup"><span data-stu-id="f2959-115">Preview</span></span>  |  <span data-ttu-id="f2959-116">여전히</span><span class="sxs-lookup"><span data-stu-id="f2959-116">Still</span></span>  |  <span data-ttu-id="f2959-117">가로 뷰 필드 (H-FOV)</span><span class="sxs-lookup"><span data-stu-id="f2959-117">Horizontal Field of View (H-FOV)</span></span> |  <span data-ttu-id="f2959-118">제안 된 사용</span><span class="sxs-lookup"><span data-stu-id="f2959-118">Suggested usage</span></span> | 
  |----------|----------|----------|----------|----------|
  |  <span data-ttu-id="f2959-119">1280x720</span><span class="sxs-lookup"><span data-stu-id="f2959-119">1280x720</span></span> |  <span data-ttu-id="f2959-120">1280x720</span><span class="sxs-lookup"><span data-stu-id="f2959-120">1280x720</span></span> |  <span data-ttu-id="f2959-121">1280x720</span><span class="sxs-lookup"><span data-stu-id="f2959-121">1280x720</span></span> |  <span data-ttu-id="f2959-122">45deg</span><span class="sxs-lookup"><span data-stu-id="f2959-122">45deg</span></span>  |  <span data-ttu-id="f2959-123">(비디오 안정화를 통해 기본 모드)</span><span class="sxs-lookup"><span data-stu-id="f2959-123">(default mode with video stabilization)</span></span> | 
  |  <span data-ttu-id="f2959-124">해당 사항 없음</span><span class="sxs-lookup"><span data-stu-id="f2959-124">N/A</span></span> |  <span data-ttu-id="f2959-125">해당 사항 없음</span><span class="sxs-lookup"><span data-stu-id="f2959-125">N/A</span></span> |  <span data-ttu-id="f2959-126">2048x1152</span><span class="sxs-lookup"><span data-stu-id="f2959-126">2048x1152</span></span> |  <span data-ttu-id="f2959-127">67deg</span><span class="sxs-lookup"><span data-stu-id="f2959-127">67deg</span></span> |  <span data-ttu-id="f2959-128">가장 높은 해상도 여전히 이미지</span><span class="sxs-lookup"><span data-stu-id="f2959-128">Highest resolution still image</span></span> | 
  |  <span data-ttu-id="f2959-129">1408x792</span><span class="sxs-lookup"><span data-stu-id="f2959-129">1408x792</span></span> |  <span data-ttu-id="f2959-130">1408x792</span><span class="sxs-lookup"><span data-stu-id="f2959-130">1408x792</span></span> |  <span data-ttu-id="f2959-131">1408x792</span><span class="sxs-lookup"><span data-stu-id="f2959-131">1408x792</span></span> |  <span data-ttu-id="f2959-132">48deg</span><span class="sxs-lookup"><span data-stu-id="f2959-132">48deg</span></span> |  <span data-ttu-id="f2959-133">비디오 안정화 전에 오버 스캔 (패딩) 확인</span><span class="sxs-lookup"><span data-stu-id="f2959-133">Overscan (padding) resolution before video stabilization</span></span> | 
  |  <span data-ttu-id="f2959-134">1344x756</span><span class="sxs-lookup"><span data-stu-id="f2959-134">1344x756</span></span> |  <span data-ttu-id="f2959-135">1344x756</span><span class="sxs-lookup"><span data-stu-id="f2959-135">1344x756</span></span> |  <span data-ttu-id="f2959-136">1344x756</span><span class="sxs-lookup"><span data-stu-id="f2959-136">1344x756</span></span> |  <span data-ttu-id="f2959-137">67deg</span><span class="sxs-lookup"><span data-stu-id="f2959-137">67deg</span></span> |  <span data-ttu-id="f2959-138">오버 스캔을 사용 하 여 큰 FOV 비디오 모드</span><span class="sxs-lookup"><span data-stu-id="f2959-138">Large FOV video mode with overscan</span></span> | 
  |  <span data-ttu-id="f2959-139">896x504</span><span class="sxs-lookup"><span data-stu-id="f2959-139">896x504</span></span> |  <span data-ttu-id="f2959-140">896x504</span><span class="sxs-lookup"><span data-stu-id="f2959-140">896x504</span></span> |  <span data-ttu-id="f2959-141">896x504</span><span class="sxs-lookup"><span data-stu-id="f2959-141">896x504</span></span> |  <span data-ttu-id="f2959-142">48deg</span><span class="sxs-lookup"><span data-stu-id="f2959-142">48deg</span></span> |  <span data-ttu-id="f2959-143">전원 부족 이미지에 대 한 낮은 해상도 모드 처리 작업</span><span class="sxs-lookup"><span data-stu-id="f2959-143">Low power / Low resolution mode for image processing tasks</span></span> | 

### <a name="hololens-2"></a><span data-ttu-id="f2959-144">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="f2959-144">HoloLens 2</span></span>

* <span data-ttu-id="f2959-145">흰색 자동 분산, 자동 노출 및 전체 이미지 처리 파이프를 사용 하 여 자동 포커스 (PV) 사진/비디오 카메라</span><span class="sxs-lookup"><span data-stu-id="f2959-145">Auto-focus photo/video (PV) camera, with auto white balance, auto exposure, and full image processing pipe</span></span>
* <span data-ttu-id="f2959-146">카메라 활성화 될 때마다 전 세계 연결 흰색 개인 LED 켜 집니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-146">White Privacy LED facing the world will illuminate whenever the camera is active</span></span>
* <span data-ttu-id="f2959-147">카메라 (모든 비디오 모드 16 9 가로 세로 비율을은)는 다음과 같은 모드를 지원 합니다.:</span><span class="sxs-lookup"><span data-stu-id="f2959-147">The camera supports the following modes (all video modes are 16:9 aspect ratio):</span></span>

  >[!NOTE]
  ><span data-ttu-id="f2959-148">이러한 모드는 HoloLens 2 일반 공급 전에 변경 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-148">These modes are subject to change prior to HoloLens 2 general availability.</span></span>

  |  <span data-ttu-id="f2959-149">비디오</span><span class="sxs-lookup"><span data-stu-id="f2959-149">Video</span></span>  |  <span data-ttu-id="f2959-150">미리 보기</span><span class="sxs-lookup"><span data-stu-id="f2959-150">Preview</span></span>  |  <span data-ttu-id="f2959-151">여전히</span><span class="sxs-lookup"><span data-stu-id="f2959-151">Still</span></span>  |  <span data-ttu-id="f2959-152">프레임 속도</span><span class="sxs-lookup"><span data-stu-id="f2959-152">Frame rates</span></span>  |  <span data-ttu-id="f2959-153">가로 뷰 필드 (H-FOV)</span><span class="sxs-lookup"><span data-stu-id="f2959-153">Horizontal Field of View (H-FOV)</span></span> |  <span data-ttu-id="f2959-154">제안 된 사용</span><span class="sxs-lookup"><span data-stu-id="f2959-154">Suggested usage</span></span> | 
  |----------|----------|----------|----------|----------|----------|
  |  <span data-ttu-id="f2959-155">1920x1080</span><span class="sxs-lookup"><span data-stu-id="f2959-155">1920x1080</span></span> |  <span data-ttu-id="f2959-156">1920x1080</span><span class="sxs-lookup"><span data-stu-id="f2959-156">1920x1080</span></span> |  <span data-ttu-id="f2959-157">해당 사항 없음</span><span class="sxs-lookup"><span data-stu-id="f2959-157">N/A</span></span> |  <span data-ttu-id="f2959-158">30, 15 fps</span><span class="sxs-lookup"><span data-stu-id="f2959-158">30, 15 fps</span></span>  |  <span data-ttu-id="f2959-159">54deg</span><span class="sxs-lookup"><span data-stu-id="f2959-159">54deg</span></span>  |  <span data-ttu-id="f2959-160">(비디오 안정화를 통해 기본 모드)</span><span class="sxs-lookup"><span data-stu-id="f2959-160">(default mode with video stabilization)</span></span> | 
  |  <span data-ttu-id="f2959-161">해당 사항 없음</span><span class="sxs-lookup"><span data-stu-id="f2959-161">N/A</span></span> |  <span data-ttu-id="f2959-162">해당 사항 없음</span><span class="sxs-lookup"><span data-stu-id="f2959-162">N/A</span></span> |  <span data-ttu-id="f2959-163">3904X2196</span><span class="sxs-lookup"><span data-stu-id="f2959-163">3904X2196</span></span> |  <span data-ttu-id="f2959-164">해당 사항 없음</span><span class="sxs-lookup"><span data-stu-id="f2959-164">N/A</span></span>  |  <span data-ttu-id="f2959-165">64deg</span><span class="sxs-lookup"><span data-stu-id="f2959-165">64deg</span></span> |  <span data-ttu-id="f2959-166">가장 높은 해상도 여전히 이미지</span><span class="sxs-lookup"><span data-stu-id="f2959-166">Highest resolution still image</span></span> | 
  |  <span data-ttu-id="f2959-167">2272x1278</span><span class="sxs-lookup"><span data-stu-id="f2959-167">2272x1278</span></span> |  <span data-ttu-id="f2959-168">2272x1278</span><span class="sxs-lookup"><span data-stu-id="f2959-168">2272x1278</span></span> |  <span data-ttu-id="f2959-169">해당 사항 없음</span><span class="sxs-lookup"><span data-stu-id="f2959-169">N/A</span></span> |  <span data-ttu-id="f2959-170">30, 15 fps</span><span class="sxs-lookup"><span data-stu-id="f2959-170">30, 15 fps</span></span>  |  <span data-ttu-id="f2959-171">64deg</span><span class="sxs-lookup"><span data-stu-id="f2959-171">64deg</span></span> |  <span data-ttu-id="f2959-172">비디오 안정화 전에 오버 스캔 (패딩) 확인</span><span class="sxs-lookup"><span data-stu-id="f2959-172">Overscan (padding) resolution before video stabilization</span></span> | 
  |  <span data-ttu-id="f2959-173">1952x1100</span><span class="sxs-lookup"><span data-stu-id="f2959-173">1952x1100</span></span> |  <span data-ttu-id="f2959-174">1952x1100</span><span class="sxs-lookup"><span data-stu-id="f2959-174">1952x1100</span></span> |  <span data-ttu-id="f2959-175">1952x1100</span><span class="sxs-lookup"><span data-stu-id="f2959-175">1952x1100</span></span>  |  <span data-ttu-id="f2959-176">30, 15 fps</span><span class="sxs-lookup"><span data-stu-id="f2959-176">30, 15 fps</span></span>  |  <span data-ttu-id="f2959-177">64deg</span><span class="sxs-lookup"><span data-stu-id="f2959-177">64deg</span></span> |  <span data-ttu-id="f2959-178">고품질 스트리밍</span><span class="sxs-lookup"><span data-stu-id="f2959-178">High-quality streaming</span></span> | 
  |  <span data-ttu-id="f2959-179">1280x720</span><span class="sxs-lookup"><span data-stu-id="f2959-179">1280x720</span></span> |  <span data-ttu-id="f2959-180">1280x720</span><span class="sxs-lookup"><span data-stu-id="f2959-180">1280x720</span></span> |  <span data-ttu-id="f2959-181">해당 사항 없음</span><span class="sxs-lookup"><span data-stu-id="f2959-181">N/A</span></span> |  <span data-ttu-id="f2959-182">30, 15, 5 fps</span><span class="sxs-lookup"><span data-stu-id="f2959-182">30, 15, 5 fps</span></span>  |  <span data-ttu-id="f2959-183">64deg</span><span class="sxs-lookup"><span data-stu-id="f2959-183">64deg</span></span> |  <span data-ttu-id="f2959-184">스트리밍 및 이미지 처리 작업에 대 한 저해상도 전원 모드</span><span class="sxs-lookup"><span data-stu-id="f2959-184">Low power/resolution mode for streaming and image processing tasks</span></span> | 

## <a name="locating-the-device-camera-in-the-world"></a><span data-ttu-id="f2959-185">전 세계에서 장치 카메라를 찾기</span><span class="sxs-lookup"><span data-stu-id="f2959-185">Locating the Device Camera in the World</span></span>

<span data-ttu-id="f2959-186">HoloLens 사진 및 비디오를 사용 하는 경우 캡처된 프레임을 원근 투영 카메라를 비롯 하 여 전 세계에 카메라의 위치를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-186">When HoloLens takes photos and videos, the captured frames include the location of the camera in the world, as well as the perspective projection of the camera.</span></span> <span data-ttu-id="f2959-187">이 보강 된 이미징 시나리오에 대 한 실제 환경에서 카메라의 위치에 대 한 이유를 응용 프로그램 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-187">This allows applications to reason about the position of the camera in the real world for augmented imaging scenarios.</span></span> <span data-ttu-id="f2959-188">개발자가 즐겨 찾는 이미지 처리 또는 사용자 지정 컴퓨터 비전 라이브러리를 사용 하 여 고유한 시나리오를 롤백하지 창의적으로 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-188">Developers can creatively roll their own scenarios using their favorite image processing or custom computer vision libraries.</span></span>

<span data-ttu-id="f2959-189">HoloLens 설명서의 다른 위치에서 "카메라"는 "가상 게임 카메라" (으로 렌더링 하면 프러스텀 앱)를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-189">"Camera" elsewhere in HoloLens documentation may refer to the "virtual game camera" (the frustum the app renders to).</span></span> <span data-ttu-id="f2959-190">그렇지 않으면 표시 된 경우가 아니면이 페이지에서 "카메라"은 실제 RGB 색 카메라를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-190">Unless denoted otherwise, "camera" on this page refers to the real-world RGB color camera.</span></span>

<span data-ttu-id="f2959-191">하지만이 페이지 처리에 대 한 세부 정보 [Media Foundation 특성](https://msdn.microsoft.com/library/windows/desktop/mt740395(v=vs.85).aspx), 카메라 내장 함수를 사용 하 여 가져오려고 Api도 있습니다 [WinRT Api](https://msdn.microsoft.com/library/windows/apps/windows.media.devices.core.cameraintrinsics)합니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-191">The details on this page cover [Media Foundation Attributes](https://msdn.microsoft.com/library/windows/desktop/mt740395(v=vs.85).aspx), however there are also APIs to pull camera intrinsics using [WinRT APIs](https://msdn.microsoft.com/library/windows/apps/windows.media.devices.core.cameraintrinsics).</span></span>  

### <a name="images-with-coordinate-systems"></a><span data-ttu-id="f2959-192">좌표계를 사용 하 여 이미지</span><span class="sxs-lookup"><span data-stu-id="f2959-192">Images with Coordinate Systems</span></span>

<span data-ttu-id="f2959-193">각 이미지 프레임 (여부를 사진 또는 비디오) 좌표계 뿐만 아니라 두 가지 중요 한 변환을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-193">Each image frame (whether photo or video) includes a coordinate system, as well as two important transforms.</span></span> <span data-ttu-id="f2959-194">"View" 카메라에 제공 된 좌표계에서 지도 및 이미지의 픽셀을 "프로젝션" 지도 카메라를 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-194">The "view" transform maps from the provided coordinate system to the camera, and the "projection" maps from the camera to pixels in the image.</span></span> <span data-ttu-id="f2959-195">함께 이러한 변환을 정의할 각 픽셀에 대 한 광선을 그린 photons 픽셀 생성 되는 경로 나타내는 3D 공간에서.</span><span class="sxs-lookup"><span data-stu-id="f2959-195">Together, these transforms define for each pixel a ray in 3D space representing the path taken by the photons that produced the pixel.</span></span> <span data-ttu-id="f2959-196">이러한 표면이 다른 좌표 시스템을 프레임의 좌표계에서 변환의 확보 하 여 앱의 다른 콘텐츠에 관련 될 수 있습니다 (예:는 [고정 참조 프레임](coordinate-systems.md#stationary-frame-of-reference)).</span><span class="sxs-lookup"><span data-stu-id="f2959-196">These rays can be related to other content in the app by obtaining the transform from the frame's coordinate system to some other coordinate system (e.g. from a [stationary frame of reference](coordinate-systems.md#stationary-frame-of-reference)).</span></span> <span data-ttu-id="f2959-197">요약 하면, 각 이미지 프레임 다음을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-197">To summarize, each image frame provides the following:</span></span>
* <span data-ttu-id="f2959-198">픽셀 (형식의 데이터를 RGB/NV12/JPEG/등)</span><span class="sxs-lookup"><span data-stu-id="f2959-198">Pixel Data (in RGB/NV12/JPEG/etc. format)</span></span>
* <span data-ttu-id="f2959-199">3 가지 메타 데이터 (으로 저장 [IMFAttributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx)) 각 프레임 확인 하는 "찾을 수 있는":</span><span class="sxs-lookup"><span data-stu-id="f2959-199">3 pieces of metadata (stored as [IMFAttributes](https://msdn.microsoft.com/library/windows/desktop/ms704598(v=vs.85).aspx)) that make each frame "locatable":</span></span>

|  <span data-ttu-id="f2959-200">특성 이름</span><span class="sxs-lookup"><span data-stu-id="f2959-200">Attribute name</span></span>  |  <span data-ttu-id="f2959-201">형식</span><span class="sxs-lookup"><span data-stu-id="f2959-201">Type</span></span>  |  <span data-ttu-id="f2959-202">GUID</span><span class="sxs-lookup"><span data-stu-id="f2959-202">GUID</span></span>  |  <span data-ttu-id="f2959-203">설명</span><span class="sxs-lookup"><span data-stu-id="f2959-203">Description</span></span> | 
|----------|----------|----------|----------|
|  <span data-ttu-id="f2959-204">MFSampleExtension_Spatial_CameraCoordinateSystem</span><span class="sxs-lookup"><span data-stu-id="f2959-204">MFSampleExtension_Spatial_CameraCoordinateSystem</span></span>  |  <span data-ttu-id="f2959-205">IUnknown ([SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx))</span><span class="sxs-lookup"><span data-stu-id="f2959-205">IUnknown ([SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx))</span></span>  |  <span data-ttu-id="f2959-206">{9D13C82F-2199-4E67-91CD-D1A4181F2534}</span><span class="sxs-lookup"><span data-stu-id="f2959-206">{9D13C82F-2199-4E67-91CD-D1A4181F2534}</span></span>  |  <span data-ttu-id="f2959-207">저장 된 [좌표계](coordinate-systems-in-directx.md) 캡처된 프레임의</span><span class="sxs-lookup"><span data-stu-id="f2959-207">Stores the [coordinate system](coordinate-systems-in-directx.md) of the captured frame</span></span> | 
|  <span data-ttu-id="f2959-208">MFSampleExtension_Spatial_CameraViewTransform</span><span class="sxs-lookup"><span data-stu-id="f2959-208">MFSampleExtension_Spatial_CameraViewTransform</span></span>  |  <span data-ttu-id="f2959-209">Blob ([Matrix4x4](https://msdn.microsoft.com/library/windows/apps/windows.foundation.numerics.matrix4x4.aspx))</span><span class="sxs-lookup"><span data-stu-id="f2959-209">Blob ([Matrix4x4](https://msdn.microsoft.com/library/windows/apps/windows.foundation.numerics.matrix4x4.aspx))</span></span>  |  <span data-ttu-id="f2959-210">{4E251FA4-830F-4770-859A-4B8D99AA809B}</span><span class="sxs-lookup"><span data-stu-id="f2959-210">{4E251FA4-830F-4770-859A-4B8D99AA809B}</span></span>  |  <span data-ttu-id="f2959-211">카메라의 외장 변환 좌표 시스템에 저장</span><span class="sxs-lookup"><span data-stu-id="f2959-211">Stores the camera's extrinsic transform in the coordinate system</span></span> | 
|  <span data-ttu-id="f2959-212">MFSampleExtension_Spatial_CameraProjectionTransform</span><span class="sxs-lookup"><span data-stu-id="f2959-212">MFSampleExtension_Spatial_CameraProjectionTransform</span></span>  |  <span data-ttu-id="f2959-213">Blob ([Matrix4x4](https://msdn.microsoft.com/library/windows/apps/windows.foundation.numerics.matrix4x4.aspx))</span><span class="sxs-lookup"><span data-stu-id="f2959-213">Blob ([Matrix4x4](https://msdn.microsoft.com/library/windows/apps/windows.foundation.numerics.matrix4x4.aspx))</span></span>  |  <span data-ttu-id="f2959-214">{47F9FCB5-2A02-4F26-A477-792FDF95886A}</span><span class="sxs-lookup"><span data-stu-id="f2959-214">{47F9FCB5-2A02-4F26-A477-792FDF95886A}</span></span>  |  <span data-ttu-id="f2959-215">카메라의 프로젝션 변환을 저장합니다</span><span class="sxs-lookup"><span data-stu-id="f2959-215">Stores the camera's projection transform</span></span> | 

<span data-ttu-id="f2959-216">프로젝션 변환을를 + 1 X 및 Y 축에-1에서 확장 되는 이미지 평면 매핑된 렌즈의 내장 함수 속성을 (도법의 중심 초점 기울이기)을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-216">The projection transform represents the intrinsic properties (focal length, center of projection, skew) of the lens mapped onto an image plane that extends from -1 to +1 in both the X and Y axis.</span></span>

```
Matrix4x4 format          Terms
   m11 m12 m13 m14      fx    0   0   0
   m21 m22 m23 m24     skew  fy   0   0
   m31 m32 m33 m34      cx   cy   A  -1
   m41 m42 m43 m44       0    0   B   0
```

<span data-ttu-id="f2959-217">다른 응용 프로그램에는 다른 좌표 시스템 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-217">Different applications will have different coordinate systems.</span></span> <span data-ttu-id="f2959-218">단일 응용 프로그램에 대 한 카메라 픽셀을 찾으려고 흐름의 개요는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-218">Here's an overview of the flow to locate a camera pixel for a single application:</span></span>

![카메라 좌표계에 적용할 변환](images/pvcameratransform5-500px.png)

### <a name="camera-to-application-specified-coordinate-system"></a><span data-ttu-id="f2959-220">응용 프로그램에서 지정한 좌표계에 카메라</span><span class="sxs-lookup"><span data-stu-id="f2959-220">Camera to Application-specified Coordinate System</span></span>

<span data-ttu-id="f2959-221">'CameraView' 및 'CameraCoordinateSystem'에서 응용 프로그램/세계 좌표 시스템을 이동 하려면 다음이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-221">To go from the 'CameraView' and 'CameraCoordinateSystem' to your application/world coordinate system, you'll need the following:</span></span>

<span data-ttu-id="f2959-222">[Unity에서 찾을 수 있는 카메라](locatable-camera-in-unity.md): (따라서 CameraCoordinateSystem 변환에 걱정할 필요가 없습니다)에 자동으로 CameraToWorldMatrix PhotoCaptureFrame 클래스에 의해 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-222">[Locatable camera in Unity](locatable-camera-in-unity.md): CameraToWorldMatrix is automatically provided by PhotoCaptureFrame class(so you don't need to worry about the CameraCoordinateSystem transforms).</span></span>

<span data-ttu-id="f2959-223">[DirectX에서 찾을 수 있는 카메라](locatable-camera-in-directx.md): 카메라의 좌표계 및 사용자 고유의 응용 프로그램 coordinate system(s) 간의 변환에 대 한 쿼리를 매우 간단한 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-223">[Locatable camera in DirectX](locatable-camera-in-directx.md): Shows the fairly straightforward way to query for the transform between the camera's coordinate system and your own application coordinate system(s).</span></span>

### <a name="application-specified-coordinate-system-to-pixel-coordinates"></a><span data-ttu-id="f2959-224">응용 프로그램에서 지정한 좌표계를 픽셀 좌표</span><span class="sxs-lookup"><span data-stu-id="f2959-224">Application-specified Coordinate System to Pixel Coordinates</span></span>

<span data-ttu-id="f2959-225">찾거나 카메라 이미지에 특정 된 3d 위치에 그리기 하려고 한다고 가정해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-225">Let's say you wanted to find or draw at a specific 3d location on a camera image:</span></span>

<span data-ttu-id="f2959-226">뷰 및 프로젝션 변환을 모두 4x4 행렬을 하는 동안 약간 다르게 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-226">The view and projection transforms, while both 4x4 matrices, need to be utilized slightly differently.</span></span> <span data-ttu-id="f2959-227">투영을 수행한 후 즉 하나는 'w로 정규화 '할 프로젝션에이 추가 단계가 시뮬레이션 하는 방법을 여러 다른 3d 위치 (즉, 특정 광선을 따라 모든 항목에 표시 됩니다 같은 픽셀) 화면에서 동일한 2d 위치로 중단 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-227">Namely after performing the Projection, one would 'normalize by w', this extra step in the projection simulates how multiple different 3d locations can end up as the same 2d location on a screen (i.e. anything along a certain ray will show up on the same pixel).</span></span> <span data-ttu-id="f2959-228">셰이더 코드에서 따라서 핵심 사항:</span><span class="sxs-lookup"><span data-stu-id="f2959-228">So key points (in shader code):</span></span>

```
// Usual 3d math:
 float4x4 WorldToCamera = inverse( CameraToWorld );
 float4 CameraSpacePos = mul( WorldToCamera, float4( WorldSpacePos.xyz, 1 ) ); // use 1 as the W component
 // Projection math:
 float4 ImagePosUnnormalized = mul( CameraProjection, float4( CameraSpacePos.xyz, 1 ) ); // use 1 as the W component
 float2 ImagePosProjected = ImagePosUnnormalized.xy / ImagePosUnnormalized.w; // normalize by W, gives -1 to 1 space
 float2 ImagePosZeroToOne = ( ImagePosProjected * 0.5 ) + float2( 0.5, 0.5 ); // good for GPU textures
 int2 PixelPos = int2( ImagePosZeroToOne.x * ImageWidth, ( 1 - ImagePosZeroToOne.y ) * ImageHeight ); // good for CPU textures
```

### <a name="pixel-to-application-specified-coordinate-system"></a><span data-ttu-id="f2959-229">응용 프로그램에서 지정한 좌표계를 픽셀</span><span class="sxs-lookup"><span data-stu-id="f2959-229">Pixel to Application-specified Coordinate System</span></span>

<span data-ttu-id="f2959-230">픽셀에서 세계 좌표 이동은 조금 더 까다롭습니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-230">Going from pixel to world coordinates is a little trickier:</span></span>

```
float2 ImagePosZeroToOne = float2( PixelPos.x / ImageWidth, 1.0 - (PixelPos.y / ImageHeight ) );
 float2 ImagePosProjected = ( ( ImagePosZeroToOne * 2.0 ) - float2(1,1) ); // -1 to 1 space
 float3 CameraSpacePos = UnProjectVector( Projection, float3( ImagePosProjected, 1) );
 float3 WorldSpaceRayPoint1 = mul( CameraToWorld, float4(0,0,0,1) ); // camera location in world space
 float3 WorldSpaceRayPoint2 = mul( CameraToWorld, CameraSpacePos ); // ray point in world space
```

<span data-ttu-id="f2959-231">여기서 UnProject으로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-231">Where we define UnProject as:</span></span>

```
public static Vector3 UnProjectVector(Matrix4x4 proj, Vector3 to)
 {
   Vector3 from = new Vector3(0, 0, 0);
   var axsX = proj.GetRow(0);
   var axsY = proj.GetRow(1);
   var axsZ = proj.GetRow(2);
   from.z = to.z / axsZ.z;
   from.y = (to.y - (from.z * axsY.z)) / axsY.y;
   from.x = (to.x - (from.z * axsX.z)) / axsX.x;
   return from;
 }
```

<span data-ttu-id="f2959-232">지점의 실제 세계 위치를 찾으려면 다음이 필요 합니다: 두 세계 표면이 및 교차점을 찾거나 요소의 크기는 잘 알려져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-232">To find the actual world location of a point, you'll need either: two world rays and find their intersection, or a known size of the points.</span></span>

### <a name="distortion-error"></a><span data-ttu-id="f2959-233">왜곡 오류</span><span class="sxs-lookup"><span data-stu-id="f2959-233">Distortion Error</span></span>

<span data-ttu-id="f2959-234">HoloLens에서 비디오 및 여전히 이미지 스트림을 시스템의 이미지 처리 파이프라인의 왜곡 전에 아닌 프레임 (미리 보기 스트림은 원래 왜곡 된 프레임을 포함 하는 데 사용) 응용 프로그램에 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-234">On HoloLens, the video and still image streams are undistorted in the system's image processing pipeline before the frames are made available to the application (the preview stream contains the original distorted frames).</span></span> <span data-ttu-id="f2959-235">투영 행렬만 사용할 수 있으므로 응용 프로그램 이미지 프레임 나타내는 완벽 한 pinhole 카메라 가정해 야으로 가득 하겠지만는 undistortion 이미지 프로세서에서 작동 하는 단 수 여전히 오류가 최대 10 개의 픽셀 투영 행렬을 사용 하는 경우 프레임 메타 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-235">Because only the projection matrix is made available, applications must assume image frames represent a perfect pinhole camera, however the undistortion function in the image processor may still leave an error of up to 10 pixels when using the projection matrix in the frame metadata.</span></span> <span data-ttu-id="f2959-236">여러 사용 사례, 예를 들어, 실제 포스터/표식, 홀로그램 맞추려는 및 표시 하는 경우이 오류는 중요 하지는 < 10px 오프셋 (약 홀로그램 2 미터 떨어진 위치에 대 한 11 mm)이이 왜곡 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-236">In many use cases, this error will not matter, but if you are aligning holograms to real world posters/markers, for example, and you notice a <10px offset (roughly 11mm for holograms positioned 2 meters away) this distortion error could be the cause.</span></span>

## <a name="locatable-camera-usage-scenarios"></a><span data-ttu-id="f2959-237">찾을 수 있는 카메라 사용 시나리오</span><span class="sxs-lookup"><span data-stu-id="f2959-237">Locatable Camera Usage Scenarios</span></span>

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a><span data-ttu-id="f2959-238">캡처된 전 세계에서 사진 또는 비디오 표시</span><span class="sxs-lookup"><span data-stu-id="f2959-238">Show a photo or video in the world where it was captured</span></span>

<span data-ttu-id="f2959-239">장치 카메라 프레임 이미지를 만든 경우 장치가 정확 하 게 위치를 표시할 수 있는 "카메라를 World" transform을 함께 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-239">The Device Camera frames come with a "Camera To World" transform, that can be used to show exactly where the device was when the image was taken.</span></span> <span data-ttu-id="f2959-240">예를 들어 작은 holographic 아이콘 (CameraToWorld.MultiplyPoint(Vector3.zero)) 및도 그리기는 카메라 직면 하 고 있던 (CameraToWorld.MultiplyVector(Vector3.forward)) 방향의 작은 화살표는이 위치에 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-240">For example you could position a small holographic icon at this location (CameraToWorld.MultiplyPoint(Vector3.zero)) and even draw a little arrow in the direction that the camera was facing (CameraToWorld.MultiplyVector(Vector3.forward)).</span></span>

### <a name="painting-the-world-using-a-camera-shader"></a><span data-ttu-id="f2959-241">카메라 셰이더를 사용 하 여 전 세계 그리기</span><span class="sxs-lookup"><span data-stu-id="f2959-241">Painting the world using a camera shader</span></span>

<span data-ttu-id="f2959-242">이 섹션에서는 만듭니다 재질 '셰이더' 전 세계 장치 카메라의 보기에서 나타난 해당 위치에 따라 해당 색입니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-242">In this section we'll create a material 'shader' that colors the world based on where it showed up in a device camera's view.</span></span> <span data-ttu-id="f2959-243">모든 꼭 짓 점에 카메라에 상대적인 위치를 파악 하 고 다음 픽셀 마다 '프로젝션 매트릭스' 그림에 활용 됩니다 효과적으로 수행할 아웃 텍셀 연관 된 이미지입니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-243">Effectively what we'll do is that every vertex will figure out its location relative to the camera, and then every pixel will utilize the 'projection matrix' to figure out which image texel it is associated with.</span></span> <span data-ttu-id="f2959-244">마지막으로, 및 필요에 따라에서는에서는 페이드 아웃 보일 dream 형태의 메모리도 이미지의 모퉁이.</span><span class="sxs-lookup"><span data-stu-id="f2959-244">Lastly, and optionally, we'll fade out the corners of the image to make it appear more as a dream-like memory:</span></span>

```
// In the vertex shader:
 float4 worldSpace = mul( ObjectToWorld, float4( vertexPos.xyz, 1));
 float4 cameraSpace = mul( CameraWorldToLocal, float4(worldSpace.xyz, 1));

 // In the pixel shader:
 float4 unprojectedTex = mul( CameraProjection, float4( cameraSpace .xyz, 1));
 float2 projectedTex = (unprojectedTex.xy / unprojectedTex.w);
 float2 unitTexcoord = ((projectedTex * 0.5) + float4(0.5, 0.5, 0, 0));
 float4 cameraTextureColor = tex2D(_CameraTex, unitTexcoord);
 // Fade out edges for better look:
 float pctInView = saturate((1.0 - length(projectedTex.xy)) * 3.0);
 float4 finalColor = float4( cameraTextureColor.rgb, pctInView );
```

### <a name="tag--pattern--poster--object-tracking"></a><span data-ttu-id="f2959-245">태그 / 패턴 / 포스터 / 추적 개체</span><span class="sxs-lookup"><span data-stu-id="f2959-245">Tag / Pattern / Poster / Object Tracking</span></span>

<span data-ttu-id="f2959-246">많은 혼합된 현실 응용 프로그램 공간에서 추적 지점을 만들려면 인식할 수 있는 이미지 또는 시각적 패턴을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-246">Many mixed reality applications use a recognizable image or visual pattern to create a trackable point in space.</span></span> <span data-ttu-id="f2959-247">기준으로 개체를 가리키거나 알려진된 위치를 만들 다음 렌더링에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-247">This is then used to render objects relative to that point or create a known location.</span></span> <span data-ttu-id="f2959-248">HoloLens 사용 fiducials (예: QR 코드를 사용 하 여 TV 모니터)를 사용 하 여 태그가 지정 된 실제 개체를 찾기, 홀로그램 fiducials를 위에 놓으면 및 태블릿을 통해 HoloLens와 통신 하는 설치 된 같은 비 HoloLens 장치를 사용 하 여 시각적으로 페어링 포함 됩니다. -Fi 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-248">Some uses for HoloLens include finding a real world object tagged with fiducials (e.g. a TV monitor with a QR code), placing holograms over fiducials, and visually pairing with non-HoloLens devices like tablets that have been setup to communicate with HoloLens via Wi-Fi.</span></span>

<span data-ttu-id="f2959-249">시각적 패턴을 인식 하 고 그런 다음 응용 프로그램 세계 좌표 공간에서 해당 개체를 배치, 하는 몇 가지 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-249">To recognize a visual pattern, and then place that object in the applications world space, you'll need a few things:</span></span>
1. <span data-ttu-id="f2959-250">이미지 패턴 인식 도구 키트, QR 코드, AR 태그, 얼굴 찾기, 원 추적기, OCR 등입니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-250">An image pattern recognition toolkit, such as QR code, AR tags, face finder, circle trackers, OCR etc.</span></span>
2. <span data-ttu-id="f2959-251">런타임 시 이미지 프레임을 수집 하 고 인식 계층에 전달</span><span class="sxs-lookup"><span data-stu-id="f2959-251">Collect image frames at runtime, and pass them to the recognition layer</span></span>
3. <span data-ttu-id="f2959-252">환경 위치 또는 가능성이 world 광선에 다시 이미지 위치로 unproject 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-252">Unproject their image locations back into world positions, or likely world rays.</span></span> <span data-ttu-id="f2959-253">참조 항목</span><span class="sxs-lookup"><span data-stu-id="f2959-253">See</span></span>
4. <span data-ttu-id="f2959-254">이러한 환경 위치 가상 모델 위치</span><span class="sxs-lookup"><span data-stu-id="f2959-254">Position your virtual models over these world locations</span></span>

<span data-ttu-id="f2959-255">몇 가지 중요 한 이미지 처리 링크:</span><span class="sxs-lookup"><span data-stu-id="f2959-255">Some important image processing links:</span></span>
* [<span data-ttu-id="f2959-256">OpenCV</span><span class="sxs-lookup"><span data-stu-id="f2959-256">OpenCV</span></span>](http://opencv.org/)
* [<span data-ttu-id="f2959-257">QR 태그</span><span class="sxs-lookup"><span data-stu-id="f2959-257">QR Tags</span></span>](https://en.wikipedia.org/wiki/QR_code)
* [<span data-ttu-id="f2959-258">FaceSDK</span><span class="sxs-lookup"><span data-stu-id="f2959-258">FaceSDK</span></span>](http://research.microsoft.com/projects/facesdk/)
* [<span data-ttu-id="f2959-259">Microsoft Translator</span><span class="sxs-lookup"><span data-stu-id="f2959-259">Microsoft Translator</span></span>](https://www.microsoft.com/translator/business)

<span data-ttu-id="f2959-260">장기 실행 이미지 인식 알고리즘을 사용 하 여 처리 하는 경우에 특히 대화형 응용 프로그램 프레임 속도 유지 하는 것은 중요 하며, 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-260">Keeping an interactive application frame-rate is critical, especially when dealing with long-running image recognition algorithms.</span></span> <span data-ttu-id="f2959-261">이러한 이유로 다음 패턴을 흔히 사용:</span><span class="sxs-lookup"><span data-stu-id="f2959-261">For this reason we commonly use the following pattern:</span></span>
1. <span data-ttu-id="f2959-262">카메라 개체를 관리 하는 주 스레드:</span><span class="sxs-lookup"><span data-stu-id="f2959-262">Main Thread: manages the camera object</span></span>
2. <span data-ttu-id="f2959-263">주 스레드: 요청 새 프레임 (비동기)</span><span class="sxs-lookup"><span data-stu-id="f2959-263">Main Thread: requests new frames (async)</span></span>
3. <span data-ttu-id="f2959-264">새 프레임 스레드 추적 전달할 주 스레드:</span><span class="sxs-lookup"><span data-stu-id="f2959-264">Main Thread: pass new frames to tracking thread</span></span>
4. <span data-ttu-id="f2959-265">추적 스레드: 처리 요점을 수집 하는 이미지</span><span class="sxs-lookup"><span data-stu-id="f2959-265">Tracking Thread: processes image to collect key points</span></span>
5. <span data-ttu-id="f2959-266">주 스레드: 이동 가상 모델에 맞게 찾을 요점</span><span class="sxs-lookup"><span data-stu-id="f2959-266">Main Thread: moves virtual model to match found key points</span></span>
6. <span data-ttu-id="f2959-267">2 단계에서 주 스레드: 반복</span><span class="sxs-lookup"><span data-stu-id="f2959-267">Main Thread: repeat from step 2</span></span>

<span data-ttu-id="f2959-268">일부 이미지 표식 시스템만 단일 픽셀 위치를 제공 (다른 모든 변환을 제공이 섹션에서는 필요 하지 않을 경우), 가능한 위치는 빛 동등 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-268">Some image marker systems only provide a single pixel location (others provide the full transform in which case this section will not be needed), which equates to a ray of possible locations.</span></span> <span data-ttu-id="f2959-269">단일 3d 위치에 연결할 수 있습니다 다음 여러 광선을 활용 하 고 대략적인 교차점에서 최종 결과 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-269">To get to a single 3d location we can then leverage multiple rays and find the final result by their approximate intersection.</span></span> <span data-ttu-id="f2959-270">이렇게 하려면를 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-270">To do this you'll need to:</span></span>
1. <span data-ttu-id="f2959-271">카메라 이미지가 여러 개 수집 이동 하는 루프를 가져오기</span><span class="sxs-lookup"><span data-stu-id="f2959-271">Get a loop going collecting multiple camera images</span></span>
2. <span data-ttu-id="f2959-272">찾을 합니다 [관련 된 기능 지점](#pixel-to-application-specified-coordinate-system), 및가 전 세계 광선</span><span class="sxs-lookup"><span data-stu-id="f2959-272">Find the [associated feature points](#pixel-to-application-specified-coordinate-system), and their world rays</span></span>
3. <span data-ttu-id="f2959-273">여러 world 광선을 사용 하 여 각 기능을 사전에 있는 경우 해당 광선의 교집합에 대 한 해결 하기 위해 다음 코드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-273">When you have a dictionary of features, each with multiple world rays, you can use the following code to solve for the intersection of those rays:</span></span>

```
public static Vector3 ClosestPointBetweenRays(
   Vector3 point1, Vector3 normalizedDirection1,
   Vector3 point2, Vector3 normalizedDirection2) {
   float directionProjection = Vector3.Dot(normalizedDirection1, normalizedDirection2);
   if (directionProjection == 1) {
     return point1; // parallel lines
   }
   float projection1 = Vector3.Dot(point2 - point1, normalizedDirection1);
   float projection2 = Vector3.Dot(point2 - point1, normalizedDirection2);
   float distanceAlongLine1 = (projection1 - directionProjection * projection2) / (1 - directionProjection * directionProjection);
   float distanceAlongLine2 = (projection2 - directionProjection * projection1) / (directionProjection * directionProjection - 1);
   Vector3 pointOnLine1 = point1 + distanceAlongLine1 * normalizedDirection1;
   Vector3 pointOnLine2 = point2 + distanceAlongLine2 * normalizedDirection2;
   return Vector3.Lerp(pointOnLine2, pointOnLine1, 0.5f);
 }
```

<span data-ttu-id="f2959-274">두 개 이상에 해당 하는 추적 된 태그의 위치를 지정 하는 사용자가 현재 시나리오에 맞게 modelled 장면을 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-274">Given two or more tracked tag locations, you can position a modelled scene to fit the users current scenario.</span></span> <span data-ttu-id="f2959-275">무게를 가정할 수 없습니다, 하는 경우 다음 해야 세 태그가 위치 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-275">If you can't assume gravity, then you'll need three tag locations.</span></span> <span data-ttu-id="f2959-276">사용 하 여 대부분의 경우 여기서 흰색 구 실시간은 단순한 색 구성표를 추적 태그 위치 및 파란색 구 모델링할 태그 위치를 나타내며이 시각적으로 맞춤 품질을 평가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-276">In many cases we use a simple color scheme where white spheres represent real-time tracked tag locations, and blue spheres represent modelled tag locations, this allows the user to visually gauge the alignment quality.</span></span> <span data-ttu-id="f2959-277">모든 응용 프로그램에서 다음 설정을 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-277">We assume the following setup in all our applications:</span></span>
* <span data-ttu-id="f2959-278">두 개 이상에 해당 하는 모델링할 태그의 위치</span><span class="sxs-lookup"><span data-stu-id="f2959-278">Two or more modelled tag locations</span></span>
* <span data-ttu-id="f2959-279">하나는 장면에서 태그의 부모인 ' 보정 공간'</span><span class="sxs-lookup"><span data-stu-id="f2959-279">One 'calibration space' which in the scene is the parent of the tags</span></span>
* <span data-ttu-id="f2959-280">카메라 기능 식별자</span><span class="sxs-lookup"><span data-stu-id="f2959-280">Camera feature identifier</span></span>
* <span data-ttu-id="f2959-281">(것은 부모 공간을 자체 modelled 표식이 없습니다 이동할 신중 하 게 다른 연결을 기준으로 하는 위치 이므로) 실시간 태그를 사용 하 여 modelled 태그에 맞게 보정 공간을 이동 하는 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-281">Behavior which moves the calibration space to align the modelled tags with the real-time tags (we are careful to move the parent space, not the modelled markers themselves, because other connect is positions relative to them).</span></span>

```
// In the two tags case:
 Vector3 idealDelta = (realTags[1].EstimatedWorldPos - realTags[0].EstimatedWorldPos);
 Vector3 curDelta = (modelledTags[1].transform.position - modelledTags[0].transform.position);
 if (IsAssumeGravity) {
   idealDelta.y = 0;
   curDelta.y = 0;
 }
 Quaternion deltaRot = Quaternion.FromToRotation(curDelta, idealDelta);
 trans.rotation = Quaternion.LookRotation(deltaRot * trans.forward, trans.up);
 trans.position += realTags[0].EstimatedWorldPos - modelledTags[0].transform.position;
```

### <a name="render-holograms-from-the-cameras-position"></a><span data-ttu-id="f2959-282">카메라의 위치에서 홀로그램 렌더링</span><span class="sxs-lookup"><span data-stu-id="f2959-282">Render holograms from the Camera's position</span></span>

<span data-ttu-id="f2959-283">참고: 나만의 사이트 생성 하려는 경우 [현실 캡처 (MRC) 혼합](mixed-reality-capture.md)카메라 스트림 사용 하 여 홀로그램을 혼합 하는, 사용할 수는 [MRC 효과](mixed-reality-capture-for-developers.md) showHolograms 속성을 사용 하도록 설정 하거나 [ Unity에서 찾을 수 있는 카메라](locatable-camera-in-unity.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-283">Note: If you are trying to create your own [Mixed reality capture (MRC)](mixed-reality-capture.md), which blends holograms with the Camera stream, you can use the [MRC effects](mixed-reality-capture-for-developers.md) or enable the showHolograms property in [Locatable camera in Unity](locatable-camera-in-unity.md).</span></span>

<span data-ttu-id="f2959-284">RGB 카메라 stream에서 직접 특수 렌더링을 수행 하려는 경우에 사용자 지정 홀로그램 기록/라이브 미리 보기를 제공 하기 위해 공간에서 카메라의 위치에서 홀로그램 비디오 피드를 사용 하 여 동기화을 렌더링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-284">If you'd like to do a special render directly on the RGB Camera stream, it's possible to render holograms in space from the Camera's position in sync with a video feed in order to provide a custom hologram recording/live preview.</span></span>

<span data-ttu-id="f2959-285">Skype,이 작업을 수행 하 HoloLens 사용자가 표시 되는 원격 클라이언트를 표시 하 고 동일한 홀로그램 상호 작용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-285">In Skype, we do this to show the remote client what the HoloLens user is seeing and allow them to interact with the same holograms.</span></span> <span data-ttu-id="f2959-286">Skype 서비스를 통해 각 비디오 프레임을 전송 하기 전에 각 프레임의 해당 하는 카메라 데이터를 가져오는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-286">Before sending over each video frame through the Skype service, we grab each frame's corresponding camera data.</span></span> <span data-ttu-id="f2959-287">다음 비디오 프레임을 사용 하 여 카메라의 외부 및 내부 메타 데이터를 패키지 하 고 Skype 서비스에 보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-287">We then package the camera's extrinsic and intrinsic metadata with the video frame and then send it over the Skype service.</span></span>

<span data-ttu-id="f2959-288">수신 측에서 Unity를 사용 하 여에서는 했습니다 이미 동기화 모두 동일한 좌표계를 사용 하 여 HoloLens 사용자 공간에서 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-288">On the receiving side, using Unity, we've already synced all of the holograms in the HoloLens user's space using the same coordinate system.</span></span> <span data-ttu-id="f2959-289">이렇게 하면 카메라의 외부 메타 데이터를 사용 하 여 Unity 카메라 HoloLens 사용자는 비디오 프레임을 캡처한 경우 준비 된 하 여 홀로그램 나머지) (기준 전 세계의 정확한 위치에 배치 하 고 카메라 내장 함수 정보를 사용 하 여 동일한 뷰를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-289">This allows us to use the camera's extrinsic metadata to place the Unity camera in the exact place in the world (relative to the rest of the holograms) that the HoloLens user was standing when that video frame was captured, and use the camera intrinsic information to ensure the view is the same.</span></span>

<span data-ttu-id="f2959-290">적절 하 게 설정 하는 카메라, 있으면 Skype, HoloLens 표시 Graphics.Blit를 사용 하 여의 혼합된 현실 뷰 만들기에서 접수 프레임으로 카메라 게 어떤 홀로그램 결합 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-290">Once we have the camera set up properly, we combine what holograms the camera sees onto the frame we received from Skype, creating a mixed reality view of what the HoloLens user sees using Graphics.Blit.</span></span>

```cs
private void OnFrameReceived(Texture frameTexture, Vector3 cameraPosition, Quaternion cameraRotation, Matrix4x4 cameraProjectionMatrix)
{
    //set material that will be blitted onto the RenderTexture
    this.compositeMaterial.SetTexture(CompositeRenderer.CameraTextureMaterialProperty, frameTexture);
    //set the camera to be that of the HoloLens's device camera
    this.Camera.transform.position = cameraPosition;
    this.Camera.transform.rotation = cameraRotation;
    this.Camera.projectionMatrix = cameraProjectionMatrix;
    //trigger the Graphics's Blit now that the frame and camera are set up
    this.TextureReady = false;
}
private void OnRenderImage(RenderTexture source, RenderTexture destination)
{
    if (!this.TextureReady)
    {
        Graphics.Blit(source, destination, this.compositeMaterial);
        this.TextureReady = true;
    }
}
```

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a><span data-ttu-id="f2959-291">추적 또는 식별 태그가 지정 된 고정 또는 이동 실제 개체/얼굴 Led 또는 다른 인식기 라이브러리를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="f2959-291">Track or Identify Tagged Stationary or Moving real-world objects/faces using LEDs or other recognizer libraries</span></span>

<span data-ttu-id="f2959-292">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-292">Examples:</span></span>
* <span data-ttu-id="f2959-293">Led 사용 하 여 산업 로봇 (또는 느린 이동에 대 한 QR 코드 개체)</span><span class="sxs-lookup"><span data-stu-id="f2959-293">Industrial robots with LEDs (or QR codes for slower moving objects)</span></span>
* <span data-ttu-id="f2959-294">식별 및 단체 실에 개체를 인식 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-294">Identify and recognize objects in the room</span></span>
* <span data-ttu-id="f2959-295">식별 하 고 (예: 위치 holographic 대화 상대 카드 얼굴을 통해) 대화방 참가자를 인식 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2959-295">Identify and recognize people in the room (e.g. place holographic contact cards over faces)</span></span>

## <a name="see-also"></a><span data-ttu-id="f2959-296">참조</span><span class="sxs-lookup"><span data-stu-id="f2959-296">See also</span></span>
* [<span data-ttu-id="f2959-297">DirectX에서 찾을 수 있는 카메라</span><span class="sxs-lookup"><span data-stu-id="f2959-297">Locatable camera in DirectX</span></span>](locatable-camera-in-directx.md)
* [<span data-ttu-id="f2959-298">Unity에서 찾을 수 있는 카메라</span><span class="sxs-lookup"><span data-stu-id="f2959-298">Locatable camera in Unity</span></span>](locatable-camera-in-unity.md)
* [<span data-ttu-id="f2959-299">혼합된 현실 캡처</span><span class="sxs-lookup"><span data-stu-id="f2959-299">Mixed reality capture</span></span>](mixed-reality-capture.md)
* [<span data-ttu-id="f2959-300">개발자를 위한 실제로 캡처 혼합</span><span class="sxs-lookup"><span data-stu-id="f2959-300">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="f2959-301">미디어 캡처 소개</span><span class="sxs-lookup"><span data-stu-id="f2959-301">Media capture introduction</span></span>](https://msdn.microsoft.com/library/windows/apps/mt243896.aspx)
