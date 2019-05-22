---
title: 앱 품질 기준
description: 이 문서에는 혼합된 현실 앱의 품질에 영향을 주는 상위 요소를 설명 합니다.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: 앱 품질 기준에 혼합 현실을, 혼합 현실 앱
ms.openlocfilehash: 756bc148f290aa3406c9ac8bb7003d463c62772c
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974746"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="36849-104">앱 품질 기준</span><span class="sxs-lookup"><span data-stu-id="36849-104">App quality criteria</span></span>

<span data-ttu-id="36849-105">이 문서에는 혼합된 현실 앱의 품질에 영향을 주는 상위 요소를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="36849-106">각 요소에 대 한 다음 정보가 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36849-106">For each factor the following information is provided</span></span>
* <span data-ttu-id="36849-107">개요-품질 요소 및 중요 한 이유는 간략 한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="36849-107">Overview – a brief description of the quality factor and why it is important.</span></span>
* <span data-ttu-id="36849-108">장치 영향-어떤 유형의 창 혼합 현실 장치 영향을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-108">Device impact - which type of Window Mixed Reality device is impacted.</span></span>
* <span data-ttu-id="36849-109">품질 기준 – 품질 요소를 평가 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="36849-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="36849-110">– 문제를 측정 (또는 환경) 메서드를 측정 하는 방법.</span><span class="sxs-lookup"><span data-stu-id="36849-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="36849-111">권장 사항-더 나은 사용자 환경을 제공 하는 방법을 요약 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="36849-112">리소스-관련 개발자 및 더 나은 앱 환경을 만드는 것이 유용할 수 있는 디자인 리소스입니다.</span><span class="sxs-lookup"><span data-stu-id="36849-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="36849-113">프레임 속도</span><span class="sxs-lookup"><span data-stu-id="36849-113">Frame rate</span></span>

<span data-ttu-id="36849-114">프레임 속도 홀로그램 안정성 및 사용자와 쾌적의 첫 번째 기본 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="36849-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="36849-115">아래 권장 되는 대상 프레임 속도 홀로그램 흔들림 환경의 believability에 부정적인 영향을 고 눈 피로 잠재적으로 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="36849-116">Windows Mixed Reality 몰입 형 헤드셋에서 환경에 대 한 대상 프레임 속도 60hz 또는 지원 하려는 Windows Mixed Reality 호환 Pc에 따라 90이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36849-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets will be either 60Hz or 90Hz depending on which Windows Mixed Reality Compatible PCs you wish to support.</span></span> <span data-ttu-id="36849-117">HoloLens에 대 한 대상 프레임 속도 60hz 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-117">For HoloLens the target frame rate is 60Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="36849-118">장치 영향</span><span class="sxs-lookup"><span data-stu-id="36849-118">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="36849-119"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="36849-119"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="36849-120"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="36849-120"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="36849-121">✔️</span><span class="sxs-lookup"><span data-stu-id="36849-121">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="36849-122">✔️</span><span class="sxs-lookup"><span data-stu-id="36849-122">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="36849-123">품질 기준</span><span class="sxs-lookup"><span data-stu-id="36849-123">Quality criteria</span></span>

|  <span data-ttu-id="36849-124">가장</span><span class="sxs-lookup"><span data-stu-id="36849-124">Best</span></span>  |  <span data-ttu-id="36849-125">충족</span><span class="sxs-lookup"><span data-stu-id="36849-125">Meets</span></span> |  <span data-ttu-id="36849-126">실패</span><span class="sxs-lookup"><span data-stu-id="36849-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="36849-127">앱 당 대상 장치에 대 한 두 번째 (FPS) 목표 프레임을 일관 되 게 충족합니다. HoloLens;에서 60 fps Ultra pc; 90 fps 및 일반 Pc에서 60 fps 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-127">The app consistently meets frames per second (FPS) goal for target device: 60fps on HoloLens; 90fps on Ultra PCs; and 60fps on mainstream PCs.</span></span> | <span data-ttu-id="36849-128">앱에 방해가 되지 core 환경을; 일시적인 프레임 삭제 또는 FPS 원하는 목표 보다 일관 되 게 낮은 하지만 앱 환경을 방해 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-128">The app has intermittent frame drops not impeding the core experience; or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="36849-129">앱에서 프레임 속도 평균 10 초 마다 이하로 떨어지는 발생 했습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-129">The app is experiencing a drop in frame rate on average every ten seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="36849-130">측정 방법</span><span class="sxs-lookup"><span data-stu-id="36849-130">How to measure</span></span>

* <span data-ttu-id="36849-131">실시간 프레임 속도 그래프를 통해 제공 됩니다는 [Windows Device Portal](using-the-windows-device-portal.md#system-performance) "시스템 성능"입니다.</span><span class="sxs-lookup"><span data-stu-id="36849-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="36849-132">개발 디버깅을 위해 앱에 진단 프레임 속도 카운터를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="36849-133">샘플 카운터에 대 한 리소스를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="36849-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="36849-134">프레임 속도 삭제 머리를 좌우 이동 하 여 앱이 실행 되는 동안 장치에서 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="36849-135">홀로그램 예기치 않은 흔들림 이동에 표시 하는 경우 다음 낮은 프레임 속도 또는 안정성 평면 원인이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="36849-136">권장 사항</span><span class="sxs-lookup"><span data-stu-id="36849-136">Recommendations</span></span>

* <span data-ttu-id="36849-137">개발 작업의 시작 부분에 프레임 속도 카운터를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="36849-138">프레임 속도가 떨어지는 발생 하는 변경 내용은 평가 하 고 성능 버그로 적절 하 게 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="36849-139">리소스</span><span class="sxs-lookup"><span data-stu-id="36849-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="36849-140">설명서</span><span class="sxs-lookup"><span data-stu-id="36849-140">Documentation</span></span>

* [<span data-ttu-id="36849-141">혼합된 현실에 대 한 성능 이해</span><span class="sxs-lookup"><span data-stu-id="36849-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="36849-142">홀로그램 안정성 및 프레임 속도</span><span class="sxs-lookup"><span data-stu-id="36849-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="36849-143">자산 성능 예산이</span><span class="sxs-lookup"><span data-stu-id="36849-143">Asset performance budget</span></span>](asset-creation-process.md)
* [<span data-ttu-id="36849-144">Unity의 권장 성능</span><span class="sxs-lookup"><span data-stu-id="36849-144">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="36849-145">도구 및 자습서</span><span class="sxs-lookup"><span data-stu-id="36849-145">Tools and tutorials</span></span>

* [<span data-ttu-id="36849-146">MRToolkit, FPS 카운터 표시</span><span class="sxs-lookup"><span data-stu-id="36849-146">MRToolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="36849-147">MRToolkit, 셰이더</span><span class="sxs-lookup"><span data-stu-id="36849-147">MRToolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="36849-148">외부 참조</span><span class="sxs-lookup"><span data-stu-id="36849-148">External references</span></span>

* [<span data-ttu-id="36849-149">Unity에서 모바일 응용 프로그램 최적화</span><span class="sxs-lookup"><span data-stu-id="36849-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="36849-150">홀로그램 안정성</span><span class="sxs-lookup"><span data-stu-id="36849-150">Hologram stability</span></span>

<span data-ttu-id="36849-151">안정적인 홀로그램 유용성 및 앱의 believability 증가 더 편리 하 게 보기 환경을 사용자에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="36849-152">홀로그램 안정성 품질이 좋은 앱 개발 및 (추적)를 이해 하는 장치의 기능 결과 해당 환경입니다.</span><span class="sxs-lookup"><span data-stu-id="36849-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="36849-153">프레임 속도 안정성의 첫 번째 pillar 상태인 다른 요인 안정성 포함 하 여 영향을 줄 수 있습니다.:</span><span class="sxs-lookup"><span data-stu-id="36849-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="36849-154">안정화 평면 사용</span><span class="sxs-lookup"><span data-stu-id="36849-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="36849-155">공간 앵커 거리입니다.</span><span class="sxs-lookup"><span data-stu-id="36849-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="36849-156">추적</span><span class="sxs-lookup"><span data-stu-id="36849-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="36849-157">장치 영향</span><span class="sxs-lookup"><span data-stu-id="36849-157">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="36849-158"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="36849-158"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="36849-159"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="36849-159"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="36849-160">✔️</span><span class="sxs-lookup"><span data-stu-id="36849-160">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="36849-161">품질 기준</span><span class="sxs-lookup"><span data-stu-id="36849-161">Quality criteria</span></span>

|  <span data-ttu-id="36849-162">가장</span><span class="sxs-lookup"><span data-stu-id="36849-162">Best</span></span>  |  <span data-ttu-id="36849-163">충족</span><span class="sxs-lookup"><span data-stu-id="36849-163">Meets</span></span> |  <span data-ttu-id="36849-164">실패</span><span class="sxs-lookup"><span data-stu-id="36849-164">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="36849-165">홀로그램은 일관 되 게 안정적인를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-165">Holograms consistently appear stable.</span></span> | <span data-ttu-id="36849-166">보조 콘텐츠 보여 예기치 않은 이동 합니다. 또는 예기치 않은 이동 전체 앱 환경을 방해 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-166">Secondary content exhibits unexpected movement; or unexpected movement does not impede overall app experience.</span></span> | <span data-ttu-id="36849-167">주 콘텐츠 프레임에 예기치 않은 이동을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="36849-167">Primary content in frame exhibits unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="36849-168">측정 방법</span><span class="sxs-lookup"><span data-stu-id="36849-168">How to measure</span></span>

<span data-ttu-id="36849-169">장치를 착용 하 고 환경을 보는 동안:</span><span class="sxs-lookup"><span data-stu-id="36849-169">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="36849-170">측면에서 머리를 이동 하 여 홀로그램 예기치 않은 이동을 표시 하는 경우 다음 낮은 프레임 속도 하거나 부적절 한 초점 평면에 안정성 평면의 맞춤이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-170">Move your head from side to side, if the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="36849-171">홀로그램 및 환경 이동, 스윔 jumpiness 등 동작에 대 한 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-171">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="36849-172">이 유형의 동작 추적 하지 환경 또는 거리를 공간 앵커 장치 원인일 가능성이 큽니다.</span><span class="sxs-lookup"><span data-stu-id="36849-172">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="36849-173">많은 경우 또는 여러 홀로그램 프레임에 안정화 평면 원인일 가능성이 있으면 흔들리는 헤드 현황을 측면에서 이동 하는 동안 다양 한 깊이 있는 홀로그램 동작을 관찰 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-173">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recomendations"></a><span data-ttu-id="36849-174">Recomendations</span><span class="sxs-lookup"><span data-stu-id="36849-174">Recomendations</span></span>

* <span data-ttu-id="36849-175">개발 작업의 시작 부분에는 프레임 속도 카운터를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-175">Add an frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="36849-176">안정화 평면을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-176">Use the stabilization plane.</span></span>
* <span data-ttu-id="36849-177">항상 해당 앵커 3 미터 내에서 고정된 홀로그램을 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-177">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="36849-178">사용자 환경이 적절 한 추적을 위한 설치 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-178">Make sure your environment is setup for proper tracking.</span></span>
* <span data-ttu-id="36849-179">프레임 내에서 다양 한 초점 깊이 수준에는 제공 하지 않으려면 환경을 설계 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-179">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="36849-180">리소스</span><span class="sxs-lookup"><span data-stu-id="36849-180">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="36849-181">설명서</span><span class="sxs-lookup"><span data-stu-id="36849-181">Documentation</span></span>

* [<span data-ttu-id="36849-182">홀로그램 안정성 및 프레임 속도</span><span class="sxs-lookup"><span data-stu-id="36849-182">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="36849-183">안정화 평면을 사용 하 여 사례 연구</span><span class="sxs-lookup"><span data-stu-id="36849-183">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="36849-184">혼합된 현실에 대 한 성능 이해</span><span class="sxs-lookup"><span data-stu-id="36849-184">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="36849-185">Unity의 권장 성능</span><span class="sxs-lookup"><span data-stu-id="36849-185">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md)
* [<span data-ttu-id="36849-186">공간 앵커</span><span class="sxs-lookup"><span data-stu-id="36849-186">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="36849-187">추적 오류 처리</span><span class="sxs-lookup"><span data-stu-id="36849-187">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="36849-188">고정 참조 프레임</span><span class="sxs-lookup"><span data-stu-id="36849-188">Stationary frame of reference</span></span>](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="36849-189">도구 및 자습서</span><span class="sxs-lookup"><span data-stu-id="36849-189">Tools and tutorials</span></span>

* [<span data-ttu-id="36849-190">Kinect IPD MR 도우미 키트</span><span class="sxs-lookup"><span data-stu-id="36849-190">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="36849-191">실제 화면에서 홀로그램 위치</span><span class="sxs-lookup"><span data-stu-id="36849-191">Holograms position on real surfaces</span></span>

<span data-ttu-id="36849-192">실제 개체 (지정한 경우 서로 기준으로 배치)를 사용 하 여 홀로그램의 misalignments는 비-공용 구조체 홀로그램 및 실세계의 명백한 증거입니다.</span><span class="sxs-lookup"><span data-stu-id="36849-192">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) is a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="36849-193">배치의 정확도; 시나리오의 요구를 기준으로 해야 합니다. 예를 들어 일반 화면 배치 공간 맵을 사용할 수 있지만 보다 정확 하 게 배치 표식 및 보정 일부 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-193">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="36849-194">장치 영향</span><span class="sxs-lookup"><span data-stu-id="36849-194">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="36849-195"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="36849-195"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="36849-196"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="36849-196"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="36849-197">✔️</span><span class="sxs-lookup"><span data-stu-id="36849-197">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="36849-198">품질 기준</span><span class="sxs-lookup"><span data-stu-id="36849-198">Quality criteria</span></span>

|  <span data-ttu-id="36849-199">가장</span><span class="sxs-lookup"><span data-stu-id="36849-199">Best</span></span>  |  <span data-ttu-id="36849-200">충족</span><span class="sxs-lookup"><span data-stu-id="36849-200">Meets</span></span> |  <span data-ttu-id="36849-201">실패</span><span class="sxs-lookup"><span data-stu-id="36849-201">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="36849-202">홀로그램 인치 범위를 센티미터 단위로 일반적으로 화면에 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="36849-202">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="36849-203">자세한 정확도 필요한 경우 앱 원하는 앱 사양 내에서 공동 작업 하는 효율적인 방법을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-203">If more accuracy is required, the app should provide an efficient means for collaboration within the desired app spec.</span></span> | <span data-ttu-id="36849-204">NA</span><span class="sxs-lookup"><span data-stu-id="36849-204">NA</span></span> | <span data-ttu-id="36849-205">홀로그램 화면의 평면을 중단 하거나 화면에서 float로 표시 하 여 실제 대상 개체를 사용 하 여 정렬 되지 않은 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="36849-205">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="36849-206">정확도 필요한 경우 홀로그램 시나리오의 근접 사양을 충족 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-206">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="36849-207">측정 방법</span><span class="sxs-lookup"><span data-stu-id="36849-207">How to measure</span></span>

* <span data-ttu-id="36849-208">홀로그램 공간 지도에 배치 되는 크게 위나 아래 화면에 고정 해제 하지 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="36849-208">Holograms that are placed on spatial map should not appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="36849-209">홀로그램 정확 하 게 배치 해야 하는 시나리오의 요구 사항을 정확 하 게 된 표식 및 보정 시스템 형태의 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-209">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="36849-210">권장 사항</span><span class="sxs-lookup"><span data-stu-id="36849-210">Recommendations</span></span>

* <span data-ttu-id="36849-211">공간 맵 정밀도 필요 없는 경우 화면에서 개체를 배치 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-211">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="36849-212">최상의 전체 자릿수를 사용 하 여 표식이 나 포스터를 홀로그램 및 Xbox 컨트롤러를 (또는 일부 수동 맞춤 메커니즘)를 설정 합니다. 최종 보정에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-212">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="36849-213">초대형 홀로그램 논리적 부분으로 분할 하 고 각 부분을 화면에 맞게 조정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-213">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="36849-214">부적절 하 게 집합 interpupilary 거리 IPD 영향을 홀로그램 맞춤을 줄 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-214">Improperly set interpupilary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="36849-215">항상 사용자의 IPD에 HoloLens를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-215">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="36849-216">리소스</span><span class="sxs-lookup"><span data-stu-id="36849-216">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="36849-217">설명서</span><span class="sxs-lookup"><span data-stu-id="36849-217">Documentation</span></span>

* [<span data-ttu-id="36849-218">공간 매핑 배치</span><span class="sxs-lookup"><span data-stu-id="36849-218">Spatial mapping placement</span></span>](spatial-mapping.md#placement)
* [<span data-ttu-id="36849-219">검색 프로세스 공간</span><span class="sxs-lookup"><span data-stu-id="36849-219">Room scanning process</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="36849-220">공간 앵커에 대 한 유용한 정보</span><span class="sxs-lookup"><span data-stu-id="36849-220">Spatial anchors best practices</span></span>](spatial-anchors.md#best-practices)
* [<span data-ttu-id="36849-221">추적 오류 처리</span><span class="sxs-lookup"><span data-stu-id="36849-221">Handling tracking errors</span></span>](coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="36849-222">Unity의 공간 매핑</span><span class="sxs-lookup"><span data-stu-id="36849-222">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="36849-223">Vuforia 개발 개요</span><span class="sxs-lookup"><span data-stu-id="36849-223">Vuforia development overview</span></span>](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="36849-224">도구 및 자습서</span><span class="sxs-lookup"><span data-stu-id="36849-224">Tools and tutorials</span></span>

* [<span data-ttu-id="36849-225">MR 공간 230: 공간 매핑</span><span class="sxs-lookup"><span data-stu-id="36849-225">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="36849-226">MR 도구 키트, 공간 매핑 라이브러리</span><span class="sxs-lookup"><span data-stu-id="36849-226">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="36849-227">MR 도우미 키트 포스터 보정 샘플</span><span class="sxs-lookup"><span data-stu-id="36849-227">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="36849-228">Kinect IPD MR 도우미 키트</span><span class="sxs-lookup"><span data-stu-id="36849-228">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="36849-229">외부 참조</span><span class="sxs-lookup"><span data-stu-id="36849-229">External references</span></span>

* [<span data-ttu-id="36849-230">전체 자릿수 맞춤 Lowes 사례 연구</span><span class="sxs-lookup"><span data-stu-id="36849-230">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="36849-231">쾌적의 보기 영역</span><span class="sxs-lookup"><span data-stu-id="36849-231">Viewing zone of comfort</span></span>

<span data-ttu-id="36849-232">앱 개발자가 컨트롤을 다양 한 깊이 있는 내용 및 홀로그램을 배치 하 여 사용자의 눈을 수렴 하는 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="36849-232">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="36849-233">HoloLens 착용 하는 사용자가 항상 광학 거리 2.0 m 약 사용자 반대쪽에 고정 HoloLens 표시 되기 때문에 명확한 이미지를 유지 하기 위해 2.0 m 수용 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-233">Users wearing HoloLens will always accommodate to 2.0m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0m away from the user.</span></span> <span data-ttu-id="36849-234">부적절 한 콘텐츠 깊이 visual 뜨거움 또는 피로 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-234">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="36849-235">장치 영향</span><span class="sxs-lookup"><span data-stu-id="36849-235">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="36849-236"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="36849-236"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="36849-237"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="36849-237"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="36849-238">✔️</span><span class="sxs-lookup"><span data-stu-id="36849-238">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="36849-239">품질 기준</span><span class="sxs-lookup"><span data-stu-id="36849-239">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="36849-240">가장</span><span class="sxs-lookup"><span data-stu-id="36849-240">Best</span></span> </td><td><ul>
<li><span data-ttu-id="36849-241">2 분에 콘텐츠를 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-241">Place content at 2m.</span></span></li><li><span data-ttu-id="36849-242">홀로그램 2 분에 배치할 수 없습니다 하 고 수렴 숙박 사이의 충돌을 피할 수 없는 경우 홀로그램 배치에 대 한 최적의 영역 1.25 m에서 5 분 사이입니다.</span><span class="sxs-lookup"><span data-stu-id="36849-242">When holograms cannot be placed at 2m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25m and 5m.</span></span></li><li><span data-ttu-id="36849-243">디자이너에 항상 1 + 상호 작용 하도록 장려 하는 콘텐츠를 구성 해야 m 번 (예: 콘텐츠 크기를 조정 및 기본 배치 매개 변수).</span><span class="sxs-lookup"><span data-stu-id="36849-243">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="36849-244">시나리오에 필요한 하지 않는 한 클리핑 평면 1m부터 fadeout 사용 하 여 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-244">Unless specifically not required by the scenario, a clipping plane should be implement with fadeout starting at 1m.</span></span></li><li><span data-ttu-id="36849-245">여기서 작동 없음 홀로그램 좀 더 자세히 관찰 하는 것은 필요한 경우에는 콘텐츠 50 cm 보다 좀 더 자세히 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-245">In cases where closer observation of a motionless hologram is required, the content should not be closer than 50cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="36849-246">충족</span><span class="sxs-lookup"><span data-stu-id="36849-246">Meets</span></span></td><td> <span data-ttu-id="36849-247">콘텐츠 보기 및 동작 지침 있지만 부적절 한 사용 또는 사용 되지 않지만 클리핑 평면 이내입니다.</span><span class="sxs-lookup"><span data-stu-id="36849-247">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="36849-248">실패</span><span class="sxs-lookup"><span data-stu-id="36849-248">Fail</span></span> </td><td> <span data-ttu-id="36849-249">콘텐츠 너무 가깝게 표시 됩니다 (일반적으로 &lt;1.25 m 또는 &lt;좀 더 자세히 관찰을 요구 하는 고정 제공에 대 한 50 cm.)</span><span class="sxs-lookup"><span data-stu-id="36849-249">Content is presented too close (typically &lt;1.25m, or &lt;50cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="36849-250">측정 방법</span><span class="sxs-lookup"><span data-stu-id="36849-250">How to measure</span></span>

* <span data-ttu-id="36849-251">콘텐츠 일반적으로 있어야 2m 았 있지만 1.25 또는 5 분 보다 더 보다 더 자세히 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-251">Content should typically be 2m away, but no closer than 1.25 or further than 5m.</span></span>
* <span data-ttu-id="36849-252">몇 가지 예외를 제외 하 고, fadeout 1m에서 시작 하는 콘텐츠를 사용 하 여 HoloLens 클리핑 렌더링 거리.85CM을 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-252">With few exceptions, the HoloLens clipping render distance should be set to .85CM with fadeout of content starting at 1m.</span></span> <span data-ttu-id="36849-253">콘텐츠 있으며 클리핑 평면 효과 유의 하십시오.</span><span class="sxs-lookup"><span data-stu-id="36849-253">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="36849-254">고정 콘텐츠 50 cm 지금 보다 좀 더 자세히 되지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-254">Stationary content should not be closer than 50cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="36849-255">권장 사항</span><span class="sxs-lookup"><span data-stu-id="36849-255">Recommendations</span></span>

* <span data-ttu-id="36849-256">2 분의 최적의 상태로 보기 거리에 대 한 콘텐츠를 디자인 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-256">Design content for the optimal viewing distance of 2m.</span></span>
* <span data-ttu-id="36849-257">Fadeout 1m에서 시작 하는 콘텐츠를 사용 하 여 85 cm을 클리핑 렌더링 거리를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-257">Set the clipping render distance to 85cm with fadeout of content starting at 1m.</span></span>
* <span data-ttu-id="36849-258">가까운 보고 해야 하는 고정 홀로그램 클리핑 평면 30 cm 보다 더 자세히 해야 하며 fadeout 적어도 10 cm 클리핑 평면에서 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-258">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30cm and fadeout should start at least 10cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="36849-259">리소스</span><span class="sxs-lookup"><span data-stu-id="36849-259">Resources</span></span>

* [<span data-ttu-id="36849-260">거리를 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-260">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="36849-261">Unity의 포커스 포인트</span><span class="sxs-lookup"><span data-stu-id="36849-261">Focus point in Unity</span></span>](focus-point-in-unity.md)
* [<span data-ttu-id="36849-262">확장을 사용 하 여 실험</span><span class="sxs-lookup"><span data-stu-id="36849-262">Experimenting with scale</span></span>](scale.md#experimenting-with-scale)
* [<span data-ttu-id="36849-263">텍스트, 권장 글꼴 크기</span><span class="sxs-lookup"><span data-stu-id="36849-263">Text, Recommended font size</span></span>](typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="36849-264">깊이 전환</span><span class="sxs-lookup"><span data-stu-id="36849-264">Depth switching</span></span>

<span data-ttu-id="36849-265">편안 하 게 문제의 보기 영역에 관계 없이 사용자 간에 자주 또는 신속 하 게 전환할 수에 대 한 요청이 근처 및 홀로그램 및 실제 콘텐츠 등 훨씬 초점 개체 oculomotor 피로 일반 뜨거움 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-265">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="36849-266">장치 영향</span><span class="sxs-lookup"><span data-stu-id="36849-266">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="36849-267"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="36849-267"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="36849-268"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="36849-268"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="36849-269">✔️</span><span class="sxs-lookup"><span data-stu-id="36849-269">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="36849-270">✔️</span><span class="sxs-lookup"><span data-stu-id="36849-270">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="36849-271">품질 기준</span><span class="sxs-lookup"><span data-stu-id="36849-271">Quality criteria</span></span>

|  <span data-ttu-id="36849-272">가장</span><span class="sxs-lookup"><span data-stu-id="36849-272">Best</span></span>  |  <span data-ttu-id="36849-273">충족</span><span class="sxs-lookup"><span data-stu-id="36849-273">Meets</span></span> |  <span data-ttu-id="36849-274">실패</span><span class="sxs-lookup"><span data-stu-id="36849-274">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="36849-275">전환 하는 제한 된 또는 자연 스러운 깊이 비정상적 쉬운데 사용자를 나타나지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-275">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="36849-276">갑작스러운 깊이 스위치 핵심 이며 앱 환경으로 설계 된 또는 예기치 않은 실제 내용으로 인해 갑작스러운 깊이 스위치.</span><span class="sxs-lookup"><span data-stu-id="36849-276">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="36849-277">일관 된 깊이 스위치 또는 갑작스러운 깊이 전환 하는 필요 하지 않은 또는 앱 환경에는 핵심입니다.</span><span class="sxs-lookup"><span data-stu-id="36849-277">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="36849-278">측정 방법</span><span class="sxs-lookup"><span data-stu-id="36849-278">How to measure</span></span>

* <span data-ttu-id="36849-279">응용 프로그램에 일관 되 게 및/또는 갑자기 깊이 포커스를 변경 하려면 사용자가 필요한 경우 문제를 전환 하는 깊이 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-279">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="36849-280">권장 사항</span><span class="sxs-lookup"><span data-stu-id="36849-280">Recommendations</span></span>

* <span data-ttu-id="36849-281">일관 된 초점 평면에서 기본 콘텐츠를 유지 하 고 안정화 평면 초점 평면 일치 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-281">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="36849-282">이 oculomotor 피로 예기치 않은 홀로그램 이동 완화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36849-282">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="36849-283">리소스</span><span class="sxs-lookup"><span data-stu-id="36849-283">Resources</span></span>

* [<span data-ttu-id="36849-284">거리를 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-284">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="36849-285">Unity의 포커스 포인트</span><span class="sxs-lookup"><span data-stu-id="36849-285">Focus point in Unity</span></span>](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="36849-286">소리 공간 사용</span><span class="sxs-lookup"><span data-stu-id="36849-286">Use of spatial sound</span></span>

<span data-ttu-id="36849-287">Windows Mixed Reality 오디오 엔진 3D 방향, 거리 및 환경 시뮬레이션을 사용 하 여 사운드를 시뮬레이션 하 여 혼합된 현실 환경 청각적 구성 요소를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-287">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="36849-288">공간 소리를 사용 하 여 응용 프로그램에서 convincingly 3 차원 공간의 (구)에 소리를 배치 하는 개발자를 사용자 대 모든 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-288">Using spatial sound in an application allows developers to convincingly place sounds in a 3 dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="36849-289">그런 다음 실제 개체 또는 사용자의 환경에서 혼합된 현실 홀로그램에서 온 것 처럼 이러한 소리 친숙할 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-289">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="36849-290">공간 소리는 집중 교육, 내게 필요한 옵션 및 혼합된 현실 응용 프로그램의 UX 디자인에 대 한 강력한 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="36849-290">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="36849-291">장치 영향</span><span class="sxs-lookup"><span data-stu-id="36849-291">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="36849-292"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="36849-292"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="36849-293"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="36849-293"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="36849-294">✔️</span><span class="sxs-lookup"><span data-stu-id="36849-294">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="36849-295">✔️</span><span class="sxs-lookup"><span data-stu-id="36849-295">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="36849-296">품질 기준</span><span class="sxs-lookup"><span data-stu-id="36849-296">Quality criteria</span></span>

|  <span data-ttu-id="36849-297">가장</span><span class="sxs-lookup"><span data-stu-id="36849-297">Best</span></span>  |  <span data-ttu-id="36849-298">충족</span><span class="sxs-lookup"><span data-stu-id="36849-298">Meets</span></span> |  <span data-ttu-id="36849-299">실패</span><span class="sxs-lookup"><span data-stu-id="36849-299">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="36849-300">소리 spatialized 논리적으로, 및 UX 개체 검색 및 사용자 의견을 지원 하기 위해 적절히 소리를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-300">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="36849-301">소리가는 시나리오에서 자연 스러운 및 개체와 관련 된 정규화 된입니다.</span><span class="sxs-lookup"><span data-stu-id="36849-301">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="36849-302">공간 오디오가 believability에 적절 하 게 사용 되는 사용자에 게 피드백 및 검색 기능에 도움이 되는 수단으로 없습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-302">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="36849-303">예상 대로 소리 spatialized 하지는 및/또는 사운드를 사용자 환경 내에서 사용자를 지원 하기 위해 부족</span><span class="sxs-lookup"><span data-stu-id="36849-303">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="36849-304">또는 공간 오디오 것으로 간주 하지 되었거나 시나리오의 디자인에 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-304">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="36849-305">측정 방법</span><span class="sxs-lookup"><span data-stu-id="36849-305">How to measure</span></span>

* <span data-ttu-id="36849-306">대상 홀로그램에서 관련 소리 내보내야 일반적으로 (예:., holographic dog에서 나오는 bark 소리.)</span><span class="sxs-lookup"><span data-stu-id="36849-306">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="36849-307">사운드 신호 의견이 나 holographic 프레임 외부 작업에 대 한 인식을 사용 하 여 사용자를 지원 하기 위해 UX 전체에서 사용할 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-307">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="36849-308">권장 사항</span><span class="sxs-lookup"><span data-stu-id="36849-308">Recommendations</span></span>

* <span data-ttu-id="36849-309">개체 검색 및 사용자 인터페이스를 사용 하 여 지원 하기 위해 공간 오디오를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-309">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="36849-310">실제 소리 synthesize 또는 비 자연 사운드 보다 더 잘 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-310">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="36849-311">대부분의 소리를 spatialized 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-311">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="36849-312">보이지 않는 미터를 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-312">Avoid invisible emitters.</span></span>
* <span data-ttu-id="36849-313">공간 마스킹 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="36849-313">Avoid spatial masking.</span></span>
* <span data-ttu-id="36849-314">모든 소리를 정규화 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-314">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="36849-315">리소스</span><span class="sxs-lookup"><span data-stu-id="36849-315">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="36849-316">설명서</span><span class="sxs-lookup"><span data-stu-id="36849-316">Documentation</span></span>

* [<span data-ttu-id="36849-317">공간 음향</span><span class="sxs-lookup"><span data-stu-id="36849-317">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="36849-318">공간 음향 디자인</span><span class="sxs-lookup"><span data-stu-id="36849-318">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="36849-319">Unity의 공간 음향</span><span class="sxs-lookup"><span data-stu-id="36849-319">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="36849-320">사례 연구, HoloTour에 대 한 소리 공간</span><span class="sxs-lookup"><span data-stu-id="36849-320">Case study, Spatial sound for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="36849-321">RoboRaid에서 공간 소리를 사용 하 여 사례 연구</span><span class="sxs-lookup"><span data-stu-id="36849-321">Case study, Using spatial sound in RoboRaid</span></span>](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="36849-322">도구 및 자습서</span><span class="sxs-lookup"><span data-stu-id="36849-322">Tools and tutorials</span></span>

* [<span data-ttu-id="36849-323">MR 공간 220: 공간 음향</span><span class="sxs-lookup"><span data-stu-id="36849-323">MR Spatial 220: Spatial sound</span></span>](holograms-220.md)
* [<span data-ttu-id="36849-324">MRToolkit, 공간 오디오</span><span class="sxs-lookup"><span data-stu-id="36849-324">MRToolkit, Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="36849-325">Holographic 프레임 (FOV) 경계에 집중</span><span class="sxs-lookup"><span data-stu-id="36849-325">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="36849-326">잘 설계 된 사용자 환경을 만들고 사용자 중심을 확장 하는 가상 환경의 유용한 컨텍스트를 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-326">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="36849-327">콘텐츠 크기 조정 및 상황에 맞는 신중 하 게 설계에서는 FOV 경계의 영향을 완화, 공간 오디오, 지침 시스템 및 사용자의 위치를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-327">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="36849-328">을 제대로 수행 하는 경우 사용자가 편리 하 게 앱 경험 하는 동안 FOV 경계에 의해 손상 작은 생각 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-328">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="36849-329">장치 영향</span><span class="sxs-lookup"><span data-stu-id="36849-329">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="36849-330"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="36849-330"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="36849-331"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="36849-331"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="36849-332">✔️</span><span class="sxs-lookup"><span data-stu-id="36849-332">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="36849-333">품질 기준</span><span class="sxs-lookup"><span data-stu-id="36849-333">Quality criteria</span></span>

|  <span data-ttu-id="36849-334">가장</span><span class="sxs-lookup"><span data-stu-id="36849-334">Best</span></span>  |  <span data-ttu-id="36849-335">충족</span><span class="sxs-lookup"><span data-stu-id="36849-335">Meets</span></span> |  <span data-ttu-id="36849-336">실패</span><span class="sxs-lookup"><span data-stu-id="36849-336">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="36849-337">사용자 컨텍스트를 손실 하지 않습니다 하 고 보기 편리 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36849-337">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="36849-338">큰 개체에 대 한 상황에 맞는 지원이 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36849-338">Context assistance is provided for large objects.</span></span> <span data-ttu-id="36849-339">검색 기능 및 지침 보기 프레임 외부 개체에 대 한 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36849-339">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="36849-340">일반적으로 동작 설계 및 소수 자릿수를 홀로그램은 편안한 화면에 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-340">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="36849-341">사용자 컨텍스트를 손실 되지 않지만 추가 목 동작 제한 된 상황에서 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-341">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="36849-342">제한 된 상황 에서만 확장 홀로그램 홀로그램 보기에 일부 목 동작을 유발 하는 세로 또는 가로 프레임 중 하나를 중단 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36849-342">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="36849-343">사용자 컨텍스트 및/또는 일관 된 목 동작 손실 될 위험이 홀로그램 보기 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-343">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="36849-344">개체 검색 기능 지침 또는 긴 홀로그램 없이 프레임 외부 손실 쉽게 이동 하는 큰 holographic 개체에 대 한 상황에 맞는 지침이 없습니다 보려는 일반 목 동작에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-344">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="36849-345">측정 방법</span><span class="sxs-lookup"><span data-stu-id="36849-345">How to measure</span></span>

* <span data-ttu-id="36849-346">(큼) 홀로그램에 대 한 컨텍스트를 분실 하거나 경계에서 잘리지 인해 인식할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-346">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="36849-347">홀로그램의 위치는 주의 이사회 또는 신속 하 게 holographic 프레임 내부 및 외부로 이동 하는 콘텐츠 부족으로 인해 찾을 하기가 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-347">Location of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="36849-348">시나리오에는 일반 및 헤드 동작 완전히를 홀로그램 목 피로에서 결과 보려면 위/아래로 반복 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-348">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="36849-349">권장 사항</span><span class="sxs-lookup"><span data-stu-id="36849-349">Recommendations</span></span>

* <span data-ttu-id="36849-350">FOV, 적합 한 다음 더 큰 버전에 시각 신호를 사용 하 여 전환 하는 작은 개체를 사용 하 여 환경을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-350">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="36849-351">사용자를 FOV 외부에 있는 콘텐츠를 찾기 위해 공간 오디오 및 주의 이사를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-351">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="36849-352">가능한 만큼 세로로 FOV 클립는 제공을 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-352">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="36849-353">최고의 위치 보기에 대 한 앱에서 지침을 사용 하 여 사용자를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-353">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="36849-354">리소스</span><span class="sxs-lookup"><span data-stu-id="36849-354">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="36849-355">설명서</span><span class="sxs-lookup"><span data-stu-id="36849-355">Documentation</span></span>

* [<span data-ttu-id="36849-356">홀로그램 프레임</span><span class="sxs-lookup"><span data-stu-id="36849-356">Holographic frame</span></span>](holographic-frame.md)
* [<span data-ttu-id="36849-357">사례 연구, HoloStudio UI와 상호 작용 디자인 학습</span><span class="sxs-lookup"><span data-stu-id="36849-357">Case Study, HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="36849-358">개체 및 환경의 확장</span><span class="sxs-lookup"><span data-stu-id="36849-358">Scale of objects and environments</span></span>](scale.md)
* [<span data-ttu-id="36849-359">커서를 시각 신호</span><span class="sxs-lookup"><span data-stu-id="36849-359">Cursors, Visual cues</span></span>](cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="36849-360">외부 참조</span><span class="sxs-lookup"><span data-stu-id="36849-360">External references</span></span>

* [<span data-ttu-id="36849-361">법석 FOV에 대 한</span><span class="sxs-lookup"><span data-stu-id="36849-361">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="36849-362">사용자 위치에 반응 하는 콘텐츠</span><span class="sxs-lookup"><span data-stu-id="36849-362">Content reacts to user position</span></span>

<span data-ttu-id="36849-363">홀로그램 거의 동일한 방식으로 "실제" 개체는 사용자가 위치 대응 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-363">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="36849-364">중요 한 디자인 고려 사항 중 이며 반드시 사용자의 위치 수 없으므로 UI 요소에 고정 되어 사용자의 동작에 맞게 조정</span><span class="sxs-lookup"><span data-stu-id="36849-364">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="36849-365">사용자 위치를 올바르게 조정 되는 앱 디자인 더 이익은 환경을 만들를 쉽게 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-365">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="36849-366">장치 영향</span><span class="sxs-lookup"><span data-stu-id="36849-366">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="36849-367"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="36849-367"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="36849-368"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="36849-368"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="36849-369">✔️</span><span class="sxs-lookup"><span data-stu-id="36849-369">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="36849-370">✔️</span><span class="sxs-lookup"><span data-stu-id="36849-370">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="36849-371">품질 기준</span><span class="sxs-lookup"><span data-stu-id="36849-371">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="36849-372">가장</span><span class="sxs-lookup"><span data-stu-id="36849-372">Best</span></span> </td><td> <span data-ttu-id="36849-373">콘텐츠 및 UI 콘텐츠로 이동 예상 되는 사용자의 범위 내에서 자연스럽 게 상호 작용 하는 사용자를 허용 하는 사용자 위치에 맞게 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-373">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="36849-374">충족</span><span class="sxs-lookup"><span data-stu-id="36849-374">Meets</span></span> </td><td> <span data-ttu-id="36849-375">UI는 사용자 위치에 맞게 조정 하지만 사용자의 위치를 조정 하도록 요구 하는 키 콘텐츠 보기를 방해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-375">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="36849-376">실패</span><span class="sxs-lookup"><span data-stu-id="36849-376">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="36849-377">UI 요소는 분실 하거나 비정상적 돌아갑니다 (또는 찾기) 컨트롤 이동 되어 사용자 중에 잠깁니다.</span><span class="sxs-lookup"><span data-stu-id="36849-377">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="36849-378">UI 요소는 기본 콘텐츠 보기를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-378">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="36849-379">UI 이동 거리 및 특히 모멘텀 보기 최적화 되지 <a href="billboarding-and-tag-along.md">tag-along</a> UI 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="36849-379">UI movement is not optimized for viewing distance and momentum particularly with <a href="billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="36849-380">측정 방법</span><span class="sxs-lookup"><span data-stu-id="36849-380">How to measure</span></span>

* <span data-ttu-id="36849-381">모든 측정 시나리오의 적절 한 범위 내에서 수행 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-381">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="36849-382">사용자 이동 달라 지지만 앱 극단적인 사용자 이동 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="36849-382">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="36849-383">UI 요소에 대 한 관련 컨트롤 사용자 이동에 관계 없이 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-383">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="36849-384">예를 들어 사용자가 보기를 확대/축소를 사용 하 여 3D 맵 주위로 탐색을 하는 경우 확대/축소 컨트롤 위치에 관계 없이 사용자를 쉽게 사용할 수 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-384">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="36849-385">권장 사항</span><span class="sxs-lookup"><span data-stu-id="36849-385">Recommendations</span></span>

* <span data-ttu-id="36849-386">사용자가 카메라와 움직임을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-386">The user is the camera and they control the movement.</span></span> <span data-ttu-id="36849-387">이러한 드라이브 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-387">Let them drive.</span></span>
* <span data-ttu-id="36849-388">텍스트 빌보드 고려 하 고 그렇지 않으면 world 잠긴 나 사용자가 려 지 수 메뉴 시스템 이동할 이었습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-388">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="36849-389">여전히 사용자가 앞에 내용을 볼 수 있도록 하는 동안 사용자를 수행 해야 하는 콘텐츠에 대 한 tag-along를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-389">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="36849-390">리소스</span><span class="sxs-lookup"><span data-stu-id="36849-390">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="36849-391">설명서</span><span class="sxs-lookup"><span data-stu-id="36849-391">Documentation</span></span>

* [<span data-ttu-id="36849-392">상호 작용 디자인</span><span class="sxs-lookup"><span data-stu-id="36849-392">Interaction design</span></span>](hologram.md)
* [<span data-ttu-id="36849-393">색, 광원 및 재질</span><span class="sxs-lookup"><span data-stu-id="36849-393">Color, light, and material</span></span>](color,-light-and-materials.md)
* [<span data-ttu-id="36849-394">빌보딩 및 태그얼롱</span><span class="sxs-lookup"><span data-stu-id="36849-394">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="36849-395">Instinctual 상호 작용</span><span class="sxs-lookup"><span data-stu-id="36849-395">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="36849-396">동작 자체 및 사용자 locomotion</span><span class="sxs-lookup"><span data-stu-id="36849-396">Self-motion and user locomotion</span></span>](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="36849-397">도구 및 자습서</span><span class="sxs-lookup"><span data-stu-id="36849-397">Tools and tutorials</span></span>

* [<span data-ttu-id="36849-398">MR 입력 210: 응시</span><span class="sxs-lookup"><span data-stu-id="36849-398">MR Input 210: Gaze</span></span>](holograms-210.md)

## <a name="input-interaction-clarity"></a><span data-ttu-id="36849-399">입력된 상호 작용 명확성</span><span class="sxs-lookup"><span data-stu-id="36849-399">Input interaction clarity</span></span>

<span data-ttu-id="36849-400">입력된 상호 작용 쉽게 구별할 수 있도록 앱의 유용성 중요 하며 입력된 일관성 approachability, 상호 작용 방법의 검색 기능을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-400">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="36849-401">사용자는 relearning 없이 플랫폼 전체의 일반적인 상호 작용을 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-401">User should be able to use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="36849-402">앱 사용자 지정 입력 있으면 수 명확 하 게 전달 하 고 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-402">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="36849-403">장치 영향</span><span class="sxs-lookup"><span data-stu-id="36849-403">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="36849-404"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="36849-404"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="36849-405"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="36849-405"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="36849-406">✔️</span><span class="sxs-lookup"><span data-stu-id="36849-406">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="36849-407">✔️</span><span class="sxs-lookup"><span data-stu-id="36849-407">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="36849-408">품질 기준</span><span class="sxs-lookup"><span data-stu-id="36849-408">Quality criteria</span></span>

|  <span data-ttu-id="36849-409">가장</span><span class="sxs-lookup"><span data-stu-id="36849-409">Best</span></span>  |  <span data-ttu-id="36849-410">충족</span><span class="sxs-lookup"><span data-stu-id="36849-410">Meets</span></span> |  <span data-ttu-id="36849-411">실패</span><span class="sxs-lookup"><span data-stu-id="36849-411">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="36849-412">입력된 상호 작용 방법을 제공 하는 Windows Mixed Reality를 사용 하 여 일관성이 [지침](interaction-fundamentals.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-412">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](interaction-fundamentals.md).</span></span> <span data-ttu-id="36849-413">사용자 지정 입력 표준 입력 (대신 사용 하 여 표준 상호 작용)를 사용 하 여 중복 되지 않아야 하 고 명확 하 게 전달와 사용자에 게 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-413">Any custom input should not be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="36849-414">비슷하게 가장 좋지만 사용자 지정 입력 표준 입력된 메서드를 사용 하 여 중복 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36849-414">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="36849-415">사용자 목표 및 앱 환경을 통해 진행률을 달성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-415">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="36849-416">입력된 메서드 또는 단추 매핑 이해 하기가 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-416">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="36849-417">입력은 고도로 사용자 지정, 지침이 없습니다 표준 입력을 지원 하지 않습니다 또는 피로 편안 하 게 문제를 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-417">Input is heavily customized, does not support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="36849-418">측정 방법</span><span class="sxs-lookup"><span data-stu-id="36849-418">How to measure</span></span>

* <span data-ttu-id="36849-419">앱에서 일관 된 [표준 메서드를 입력 합니다.](interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="36849-419">The app uses consistent [standard input methods.](interaction-fundamentals.md)</span></span>
* <span data-ttu-id="36849-420">앱 사용자 지정 입력 있으면 통해 명확 하 게 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36849-420">If the app has custome input, it is clearly communicated through:</span></span>
* <span data-ttu-id="36849-421">첫 실행 경험</span><span class="sxs-lookup"><span data-stu-id="36849-421">First-run experience</span></span>
* <span data-ttu-id="36849-422">소개 화면</span><span class="sxs-lookup"><span data-stu-id="36849-422">Introductory screens</span></span>
* <span data-ttu-id="36849-423">도구 설명</span><span class="sxs-lookup"><span data-stu-id="36849-423">Tooltips</span></span>
* <span data-ttu-id="36849-424">직접 coach</span><span class="sxs-lookup"><span data-stu-id="36849-424">Hand coach</span></span>
* <span data-ttu-id="36849-425">도움말 섹션</span><span class="sxs-lookup"><span data-stu-id="36849-425">Help section</span></span>
* <span data-ttu-id="36849-426">음성 전달</span><span class="sxs-lookup"><span data-stu-id="36849-426">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="36849-427">권장 사항</span><span class="sxs-lookup"><span data-stu-id="36849-427">Recommendations</span></span>

* <span data-ttu-id="36849-428">가능 하면 표준 입력된 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-428">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="36849-429">비표준 입력된 메서드에 대 한 데모, 자습서 및 도구 설명을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-429">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="36849-430">앱 전체에서 일관 된 상호 작용 모델을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-430">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="36849-431">리소스</span><span class="sxs-lookup"><span data-stu-id="36849-431">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="36849-432">설명서</span><span class="sxs-lookup"><span data-stu-id="36849-432">Documentation</span></span>

* [<span data-ttu-id="36849-433">Instinctual 상호 작용</span><span class="sxs-lookup"><span data-stu-id="36849-433">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="36849-434">상호 작용할 수 없는 개체</span><span class="sxs-lookup"><span data-stu-id="36849-434">Interactable objects</span></span>](interactable-object.md)
* [<span data-ttu-id="36849-435">헤드 게이즈 및 유지</span><span class="sxs-lookup"><span data-stu-id="36849-435">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="36849-436">커서</span><span class="sxs-lookup"><span data-stu-id="36849-436">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="36849-437">편안 함과 응시</span><span class="sxs-lookup"><span data-stu-id="36849-437">Comfort and gaze</span></span>](comfort.md#gaze-direction)
* [<span data-ttu-id="36849-438">제스처</span><span class="sxs-lookup"><span data-stu-id="36849-438">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="36849-439">음성 입력 </span><span class="sxs-lookup"><span data-stu-id="36849-439">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="36849-440">음성 명령</span><span class="sxs-lookup"><span data-stu-id="36849-440">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="36849-441">모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="36849-441">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="36849-442">Unity 입력 포팅 가이드</span><span class="sxs-lookup"><span data-stu-id="36849-442">Input porting guide for Unity</span></span>](input-porting-guide-for-unity.md)
* [<span data-ttu-id="36849-443">Unity의 키보드 입력</span><span class="sxs-lookup"><span data-stu-id="36849-443">Keyboard input in Unity</span></span>](keyboard-input-in-unity.md)
* [<span data-ttu-id="36849-444">Unity의 응시</span><span class="sxs-lookup"><span data-stu-id="36849-444">Gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="36849-445">Unity의 제스처 및 모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="36849-445">Gestures and motion controllers in Unity</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="36849-446">Unity의 음성 입력</span><span class="sxs-lookup"><span data-stu-id="36849-446">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="36849-447">DirectX의 키보드, 마우스 및 컨트롤러 입력</span><span class="sxs-lookup"><span data-stu-id="36849-447">Keyboard, mouse, and controller input in DirectX</span></span>](keyboard,-mouse,-and-controller-input-in-directx.md)
* [<span data-ttu-id="36849-448">DirectX의 헤드 및 눈 응시</span><span class="sxs-lookup"><span data-stu-id="36849-448">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="36849-449">DirectX의 헤드 및 모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="36849-449">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="36849-450">DirectX의 음성 입력</span><span class="sxs-lookup"><span data-stu-id="36849-450">Voice input in DirectX</span></span>](voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="36849-451">도구 및 자습서</span><span class="sxs-lookup"><span data-stu-id="36849-451">Tools and tutorials</span></span>

* [<span data-ttu-id="36849-452">사례 연구: 위해 더 많은 개인 컴퓨팅</span><span class="sxs-lookup"><span data-stu-id="36849-452">Case study: The pursuit of more personal computing</span></span>](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="36849-453">연구를 캐스팅 합니다. HoloStudio UI와 상호 작용 디자인 학습</span><span class="sxs-lookup"><span data-stu-id="36849-453">Cast study: HoloStudio UI and interaction design learnings</span></span>](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="36849-454">샘플 앱: 요소의 정기적 테이블</span><span class="sxs-lookup"><span data-stu-id="36849-454">Sample app: Periodic table of the elements</span></span>](periodic-table-of-the-elements.md)
* [<span data-ttu-id="36849-455">샘플 앱: 음력 모듈</span><span class="sxs-lookup"><span data-stu-id="36849-455">Sample app: Lunar module</span></span>](lunar-module.md)
* [<span data-ttu-id="36849-456">MR 입력 210: 응시</span><span class="sxs-lookup"><span data-stu-id="36849-456">MR Input 210: Gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="36849-457">MR 입력 211: 제스처</span><span class="sxs-lookup"><span data-stu-id="36849-457">MR Input 211: Gestures</span></span>](holograms-211.md)
* [<span data-ttu-id="36849-458">MR 입력 212: 음성</span><span class="sxs-lookup"><span data-stu-id="36849-458">MR Input 212: Voice</span></span>](holograms-212.md)

## <a name="interactable-objects"></a><span data-ttu-id="36849-459">상호 작용할 수 없는 개체</span><span class="sxs-lookup"><span data-stu-id="36849-459">Interactable objects</span></span>

<span data-ttu-id="36849-460">2D 추상 전 세계에서 이벤트를 트리거하는 데 사용 하는 비유를 오랫동안 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="36849-460">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="36849-461">3 차원 혼합된 현실 세계에서 추상화를 더 이상이 환경으로 제한 될 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-461">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="36849-462">아무 것도 이벤트를 트리거하는 상호 작용할 수 없는 개체 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-462">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="36849-463">상호 작용할 수 없는 개체로 나타낼 수 있습니다 것과 테이블에는 커피 cup에서 공중에서 부동 풍선으로.</span><span class="sxs-lookup"><span data-stu-id="36849-463">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="36849-464">폼에 관계 없이 상호 작용할 수 없는 개체는 시각적 및 오디오 신호를 통해 사용자가 명확 하 게 인식할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-464">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="36849-465">장치 영향</span><span class="sxs-lookup"><span data-stu-id="36849-465">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="36849-466"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="36849-466"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="36849-467"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="36849-467"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="36849-468">✔️</span><span class="sxs-lookup"><span data-stu-id="36849-468">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="36849-469">✔️</span><span class="sxs-lookup"><span data-stu-id="36849-469">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="36849-470">품질 기준</span><span class="sxs-lookup"><span data-stu-id="36849-470">Quality criteria</span></span>

|  <span data-ttu-id="36849-471">가장</span><span class="sxs-lookup"><span data-stu-id="36849-471">Best</span></span>  |  <span data-ttu-id="36849-472">충족</span><span class="sxs-lookup"><span data-stu-id="36849-472">Meets</span></span> |  <span data-ttu-id="36849-473">실패</span><span class="sxs-lookup"><span data-stu-id="36849-473">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="36849-474">폼에 관계 없이 상호 작용할 수 없는 개체는 시각적 및 오디오 신호를 통해 인식할 수 있는 세 가지 상태 간에: 유휴 상태, 선택한 대상으로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-474">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="36849-475">"참조 말 것"을 선택 취소 하 고 일관 되 게 사용 환경 전체에서.</span><span class="sxs-lookup"><span data-stu-id="36849-475">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="36849-476">개체 크기를 조정 되며 대상으로 사용 가능한 오류에 대 한 허용 하도록 배포 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36849-476">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="36849-477">사용자 수으로 오디오 또는 시각적 피드백을 통해 상호 작용할 수 없는 개체를 인식할 수 있습니다 하 고 개체를 활성화 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-477">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="36849-478">사용자 없는 visual 또는 오디오 신호 들어 상호 작용할 수 없는 개체를 인식할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-478">Given no visual or audio cues, user cannot recognize an interactable object.</span></span> <span data-ttu-id="36849-479">상호 작용은 오류가 개체 간의 거리 또는 개체 크기 조정으로 인해 발생 하기 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-479">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="36849-480">측정 방법</span><span class="sxs-lookup"><span data-stu-id="36849-480">How to measure</span></span>

* <span data-ttu-id="36849-481">상호 작용할 수 없는 개체는 '상호 작용할 수 없는';으로 인식할 수 단추, 메뉴 및 앱 특정 콘텐츠를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-481">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app specific content.</span></span> <span data-ttu-id="36849-482">일반적으로 없어야 visual 및 오디오 큐를 상호 작용할 수 없는 개체를 대상으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-482">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="36849-483">권장 사항</span><span class="sxs-lookup"><span data-stu-id="36849-483">Recommendations</span></span>

* <span data-ttu-id="36849-484">상호 작용에 대 한 시각적 및 오디오 피드백을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-484">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="36849-485">각 입력 (유휴 상태, 대상, 선택 된) 상태에 대 한 시각적 피드백을 구분할 수 해야</span><span class="sxs-lookup"><span data-stu-id="36849-485">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="36849-486">상호 작용할 수 없는 개체를 확장 하 고 대상으로 사용 가능한 오류에 대 한 배치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-486">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="36849-487">그룹화 된 상호 작용할 수 없는 개체 (예: 메뉴 모음 또는 목록)을 대상으로 하는 것에 대 한 적절 한 간격이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-487">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="36849-488">단추와 음성 명령을 지 원하는 메뉴 명령 키워드에 대 한 텍스트 레이블을 제공 해야 ("표시, 말")</span><span class="sxs-lookup"><span data-stu-id="36849-488">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="36849-489">리소스</span><span class="sxs-lookup"><span data-stu-id="36849-489">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="36849-490">설명서</span><span class="sxs-lookup"><span data-stu-id="36849-490">Documentation</span></span>

* [<span data-ttu-id="36849-491">상호 작용 가능한 개체</span><span class="sxs-lookup"><span data-stu-id="36849-491">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="36849-492">Unity의 텍스트</span><span class="sxs-lookup"><span data-stu-id="36849-492">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="36849-493">앱 바 및 경계 상자</span><span class="sxs-lookup"><span data-stu-id="36849-493">App bar and bounding box</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="36849-494">음성 명령</span><span class="sxs-lookup"><span data-stu-id="36849-494">Voice commanding</span></span>](voice-design.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="36849-495">도구 및 자습서</span><span class="sxs-lookup"><span data-stu-id="36849-495">Tools and tutorials</span></span>

* [<span data-ttu-id="36849-496">혼합된 현실 도구 키트-UX</span><span class="sxs-lookup"><span data-stu-id="36849-496">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="36849-497">공간 검색</span><span class="sxs-lookup"><span data-stu-id="36849-497">Room scanning</span></span>

<span data-ttu-id="36849-498">공간 매핑 데이터를 필요한 응용 프로그램을 자동으로 시간이 지남에 따라이 데이터를 수집 하려면 장치에 의존 하 고 사용자로 세션 전반에 걸쳐 활성 장치를 사용 하 여 해당 환경을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="36849-498">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="36849-499">완성도이 데이터의 품질을 다양 한 사용자가 수행 하는 탐색, 탐색 이후 경과 된 시간은 어떻게 양과 장치 영역을 검색 하므로 가구 등 문 개체가 이동 하는지 여부를 비롯 한 요인에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="36849-499">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="36849-500">대부분의 앱에서는 사용자 완결성과 공간 map의 품질을 개선 하기 위해 추가 단계를 수행 해야 하는지 여부를 판단 하려면 환경의 시작 공간 매핑 데이터를 분석 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-500">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="36849-501">사용자가 검색 환경, 검색 환경 지침을 제공 해야의 선택을 취소 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-501">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="36849-502">장치 영향</span><span class="sxs-lookup"><span data-stu-id="36849-502">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="36849-503"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="36849-503"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="36849-504"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="36849-504"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="36849-505">✔️</span><span class="sxs-lookup"><span data-stu-id="36849-505">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="36849-506">품질 기준</span><span class="sxs-lookup"><span data-stu-id="36849-506">Quality criteria</span></span>

|  <span data-ttu-id="36849-507">가장</span><span class="sxs-lookup"><span data-stu-id="36849-507">Best</span></span>  |  <span data-ttu-id="36849-508">충족</span><span class="sxs-lookup"><span data-stu-id="36849-508">Meets</span></span> |  <span data-ttu-id="36849-509">실패</span><span class="sxs-lookup"><span data-stu-id="36849-509">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="36849-510">공간 메시의 시각화 알 검색 하는 사용자가 진행 중입니다.</span><span class="sxs-lookup"><span data-stu-id="36849-510">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="36849-511">사용자는 명확 하 게 할 일 및 검색의 시작 및 중지 시기를 알고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-511">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="36849-512">공간 메시의 시각화를 제공 하지만 사용자 명확 하 게 알 수행할 작업 및 진행률 정보를 제공 하지.</span><span class="sxs-lookup"><span data-stu-id="36849-512">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="36849-513">메시의 시각화가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-513">No visualization of mesh.</span></span> <span data-ttu-id="36849-514">지침 정보가을 where 절 또는 경우 검색을 시작/중지에 대 한 사용자에 게 제공 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-514">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="36849-515">측정 방법</span><span class="sxs-lookup"><span data-stu-id="36849-515">How to measure</span></span>

* <span data-ttu-id="36849-516">필요한 공간을 검색 하는 동안 visual 및 오디오 지침을 확인할 수 있는 위치 및 시작 하는 시기 및 중지 검색을 나타내는 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36849-516">During a required room scan, visual and audio guidance is provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="36849-517">권장 사항</span><span class="sxs-lookup"><span data-stu-id="36849-517">Recommendations</span></span>

* <span data-ttu-id="36849-518">환경의 일부가 되도록 해야 사용자가 주변에 총 볼륨의 양을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="36849-518">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="36849-519">검색을 시작 / 중지 진행률 표시기와 같은 경우 통신 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-519">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="36849-520">검색 하는 동안 메시의 시각화를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-520">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="36849-521">사용자가 찾고 전시실 이동에 시각 및 오디오 신호를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-521">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="36849-522">데이터를 개선 하기 위해 이동할 위치를 사용자에 게 알립니다.</span><span class="sxs-lookup"><span data-stu-id="36849-522">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="36849-523">대부분의 경우에 것이 사용자에 게 알리고 필요한지 않습니다 (예: 살펴보고 한계 조회 가구 뒤)를 가장 필요한 검사 품질을 얻기 위해.</span><span class="sxs-lookup"><span data-stu-id="36849-523">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="36849-524">리소스</span><span class="sxs-lookup"><span data-stu-id="36849-524">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="36849-525">설명서</span><span class="sxs-lookup"><span data-stu-id="36849-525">Documentation</span></span>

* [<span data-ttu-id="36849-526">실내 스캔 시각화</span><span class="sxs-lookup"><span data-stu-id="36849-526">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="36849-527">사례 연구: HoloLens의 공간 매핑 기능을 확장</span><span class="sxs-lookup"><span data-stu-id="36849-527">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="36849-528">사례 연구: HoloTour 공간 적절 하 게 디자인</span><span class="sxs-lookup"><span data-stu-id="36849-528">Case study: Spatial sound design for HoloTour</span></span>](case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="36849-529">사례 연구: 조각에는 몰입 형 환경을 만들기</span><span class="sxs-lookup"><span data-stu-id="36849-529">Case study: Creating an immersive experience in Fragments</span></span>](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="36849-530">도구 및 자습서</span><span class="sxs-lookup"><span data-stu-id="36849-530">Tools and tutorials</span></span>

* [<span data-ttu-id="36849-531">혼합된 현실 도구 키트-UX</span><span class="sxs-lookup"><span data-stu-id="36849-531">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="36849-532">방향 표시기</span><span class="sxs-lookup"><span data-stu-id="36849-532">Directional indicators</span></span>

<span data-ttu-id="36849-533">혼합된 현실 앱에서 콘텐츠 보기의 필드를 벗어난 것 같습니다 또는 실제 개체에 의해 폐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-533">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="36849-534">잘 설계 된 앱을 더 쉬워집니다 사용자가 표시 되지 않는 콘텐츠를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-534">A well designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="36849-535">방향 표시기 경고 중요 한 콘텐츠를 사용자 및 사용자의 위치를 기준으로 내용에 대 한 지침을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-535">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="36849-536">지침 표시 되지 않는 콘텐츠 형식의 사운드 미터, 방향 화살표 또는 직접 시각적 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-536">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="36849-537">장치 영향</span><span class="sxs-lookup"><span data-stu-id="36849-537">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="36849-538"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="36849-538"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="36849-539"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="36849-539"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="36849-540">✔️</span><span class="sxs-lookup"><span data-stu-id="36849-540">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="36849-541">✔️</span><span class="sxs-lookup"><span data-stu-id="36849-541">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="36849-542">품질 기준</span><span class="sxs-lookup"><span data-stu-id="36849-542">Quality criteria</span></span>

|  <span data-ttu-id="36849-543">가장</span><span class="sxs-lookup"><span data-stu-id="36849-543">Best</span></span>  |  <span data-ttu-id="36849-544">충족</span><span class="sxs-lookup"><span data-stu-id="36849-544">Meets</span></span> |  <span data-ttu-id="36849-545">실패</span><span class="sxs-lookup"><span data-stu-id="36849-545">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="36849-546">직접 visual 및 오디오 신호는 관련 콘텐츠 보기의 필드 외부 사용자를 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-546">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="36849-547">화살표 또는 콘텐츠의 일반적으로 사용자를 가리키는 일부 표시기입니다.</span><span class="sxs-lookup"><span data-stu-id="36849-547">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="36849-548">관련 콘텐츠 보기의 필드를 외부 및 저하 되었거나 위치 지침이 없는 사용자에 게 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36849-548">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="36849-549">측정 방법</span><span class="sxs-lookup"><span data-stu-id="36849-549">How to measure</span></span>

* <span data-ttu-id="36849-550">외부 사용자 필드의 보기에서 관련 콘텐츠는 visual 및/또는 오디오 신호를 통해 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-550">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="36849-551">권장 사항</span><span class="sxs-lookup"><span data-stu-id="36849-551">Recommendations</span></span>

* <span data-ttu-id="36849-552">관련 콘텐츠는 사용자의 뷰 필드를 벗어날 때 방향 표시기 및 오디오 신호 콘텐츠에 사용자 가이드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-552">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="36849-553">대부분의 경우에서 직접 시각적으로 알려줍니다 스타일러스가 기본 방향 화살표입니다.</span><span class="sxs-lookup"><span data-stu-id="36849-553">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="36849-554">커서로 방향 지표를 구축 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-554">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="36849-555">리소스</span><span class="sxs-lookup"><span data-stu-id="36849-555">Resources</span></span>

* [<span data-ttu-id="36849-556">홀로그램 프레임</span><span class="sxs-lookup"><span data-stu-id="36849-556">Holographic frame</span></span>](holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="36849-557">데이터 로드</span><span class="sxs-lookup"><span data-stu-id="36849-557">Data loading</span></span>

<span data-ttu-id="36849-558">진행률 컨트롤은 긴 작업을 진행 중인 사용자에게 피드백을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-558">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="36849-559">진행률 표시기가 표시 되 고 대기 시간 기간 수 있습니다 하는 것을 나타낼 수도 있습니다 하는 경우 사용자 앱 상호 작용할 수 없습니다는 의미할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-559">It can mean that the user cannot interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="36849-560">장치 영향</span><span class="sxs-lookup"><span data-stu-id="36849-560">Device impact</span></span>

<table>
<tr>
<th style="width:150px"> <span data-ttu-id="36849-561"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="36849-561"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="36849-562"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="36849-562"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td style="text-align: center;"> <span data-ttu-id="36849-563">✔️</span><span class="sxs-lookup"><span data-stu-id="36849-563">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="36849-564">✔️</span><span class="sxs-lookup"><span data-stu-id="36849-564">✔️</span></span></td>
</tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="36849-565">품질 기준</span><span class="sxs-lookup"><span data-stu-id="36849-565">Quality criteria</span></span>

|  <span data-ttu-id="36849-566">가장</span><span class="sxs-lookup"><span data-stu-id="36849-566">Best</span></span>  |  <span data-ttu-id="36849-567">충족</span><span class="sxs-lookup"><span data-stu-id="36849-567">Meets</span></span> |  <span data-ttu-id="36849-568">실패</span><span class="sxs-lookup"><span data-stu-id="36849-568">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="36849-569">진행률 표시줄 또는 모든 데이터를 로드 하거나 처리 하는 동안 진행률을 보여 주는 링의 형태로 시각적 표시기를 애니메이션 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-569">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="36849-570">시각적 표시기 기간 대기 수 지침을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-570">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="36849-571">사용자는 데이터 로드 진행에서 되는 기간 대기 수의 표시가 알림을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-571">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="36849-572">데이터 로드 또는 5 초 보다 오래 된 작업에 대 한 프로세스 표시기는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="36849-572">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="36849-573">측정 방법</span><span class="sxs-lookup"><span data-stu-id="36849-573">How to measure</span></span>

* <span data-ttu-id="36849-574">데이터를 로드 하는 동안 5 초 넘게 빈 상태가 없는 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-574">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="36849-575">권장 사항</span><span class="sxs-lookup"><span data-stu-id="36849-575">Recommendations</span></span>

* <span data-ttu-id="36849-576">사용자는이 앱을 중단 했거나 충돌을 인식할 수 있습니다 때 모든 상황에서 진행률을 표시 하는 데이터 로드 애니메이터를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="36849-576">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="36849-577">적절 한 규칙의 thumb은 5 초 넘게 걸리는 모든 '로드' 활동입니다.</span><span class="sxs-lookup"><span data-stu-id="36849-577">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="36849-578">리소스</span><span class="sxs-lookup"><span data-stu-id="36849-578">Resources</span></span>

* [<span data-ttu-id="36849-579">진행률 표시</span><span class="sxs-lookup"><span data-stu-id="36849-579">Displaying progress</span></span>](progress.md)
