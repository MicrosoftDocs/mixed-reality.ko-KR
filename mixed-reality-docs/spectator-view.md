---
title: Spectator 뷰
description: 외부 디스플레이 또는 혼합 현실 환경의 비디오 녹화에서 혼합 현실 환경을 보여 주는 수단으로 외부 장치에서 holograms을 시각화 합니다.
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
keywords: Spectator View, iPhone, iOS, iPad, OpenCV, 카메라, ARKit, HoloLens, Mixed Reality, MixedRealityToolkit, 데모, 레코드
ms.openlocfilehash: 708ed694af3769f16d5dce0595e026f9a348d754
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047170"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a><span data-ttu-id="a8045-104">HoloLens 및 HoloLens Spectator 보기 2</span><span class="sxs-lookup"><span data-stu-id="a8045-104">Spectator View for HoloLens and HoloLens 2</span></span>

![표식](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a><span data-ttu-id="a8045-106">개요</span><span class="sxs-lookup"><span data-stu-id="a8045-106">Overview</span></span>

<span data-ttu-id="a8045-107">HoloLens를 제공 하는 경우에는 자주 제공 하지 않는 사용자가 불가사의를 경험 하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8045-107">When wearing a HoloLens, we often forget that a person who does not have it on is unable to experience the wonders that we can.</span></span> <span data-ttu-id="a8045-108">Spectator 보기를 사용 하면 다른 사용자가 해당 지역에서 HoloLens 사용자에 게 표시 되는 2D 화면을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8045-108">Spectator View allows others to see on a 2D screen what a HoloLens user sees in their world.</span></span>
<span data-ttu-id="a8045-109">Spectator View는 모바일 장치를 사용 하 여 HD에 holograms을 기록 하는 빠르고 경제적인 접근 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8045-109">Spectator View offers a fast and affordable approach to recording holograms in HD with mobile devices.</span></span> <span data-ttu-id="a8045-110">또한 비디오 카메라를 사용 하 여 holograms에 대 한 전문적인 품질 기록을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8045-110">It also offers a professional quality recording of holograms with video cameras.</span></span>

## <a name="key-resources"></a><span data-ttu-id="a8045-111">주요 리소스</span><span class="sxs-lookup"><span data-stu-id="a8045-111">Key Resources</span></span>

* [<span data-ttu-id="a8045-112">**GitHub의 Spectator 보기**</span><span class="sxs-lookup"><span data-stu-id="a8045-112">**Spectator View on GitHub**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView)
* [<span data-ttu-id="a8045-113">**Spectator View 설명서**</span><span class="sxs-lookup"><span data-stu-id="a8045-113">**Spectator View Documentation**</span></span>](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [<span data-ttu-id="a8045-114">**Spectator 뷰 샘플**</span><span class="sxs-lookup"><span data-stu-id="a8045-114">**Spectator View Samples**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a><span data-ttu-id="a8045-115">사용 사례</span><span class="sxs-lookup"><span data-stu-id="a8045-115">Use Cases</span></span>
* <span data-ttu-id="a8045-116">IPhone 또는 Android 장치를 사용 하 여 혼합 현실 환경을 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8045-116">You can record a mixed reality experience using an iPhone or Android device.</span></span> <span data-ttu-id="a8045-117">전체 HD를 기록 하 고 holograms 및 그림자에 앤티앨리어싱을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8045-117">Record in full HD and apply anti-aliasing to holograms and even shadows.</span></span> <span data-ttu-id="a8045-118">Holograms 비디오를 빠르게 캡처하는 비용 효율적이 고 빠른 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="a8045-118">It is a cost-effective and quick way to capture video of holograms.</span></span>
* <span data-ttu-id="a8045-119">IPhone 또는 iPad에서 바로 Apple TV로 라이브 혼합 현실 경험을 스트리밍할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8045-119">Stream live mixed reality experiences to an Apple TV directly from your iPhone or iPad, lag-free!</span></span>
* <span data-ttu-id="a8045-120">게스트와 경험을 공유 합니다. HoloLens가 아닌 사용자가 휴대폰 또는 태블릿에서 직접 holograms 경험 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8045-120">Share the experience with guests: Let non-HoloLens users experience holograms directly from their phones or tablets.</span></span>

## <a name="current-features"></a><span data-ttu-id="a8045-121">현재 기능</span><span class="sxs-lookup"><span data-stu-id="a8045-121">Current Features</span></span>

* <span data-ttu-id="a8045-122">Holograms의 공간 동기화는 모든 사용자가 정확히 동일한 장소에서 Holograms을 볼 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a8045-122">Spatial synchronization of Holograms, so everyone sees holograms in the exact same place.</span></span>
* <span data-ttu-id="a8045-123">iOS (ARKit 사용 장치) 및 Android (Arkit 사용 장치) 지원.</span><span class="sxs-lookup"><span data-stu-id="a8045-123">iOS (ARKit-enabled devices) and Android (ARCore-enabled devices) support.</span></span>
<span data-ttu-id="a8045-124">여러 iOS 게스트.</span><span class="sxs-lookup"><span data-stu-id="a8045-124">Multiple iOS guests.</span></span>
<span data-ttu-id="a8045-125">비디오 + holograms + 주변 소리 + 홀로그램 소리의 기록입니다.</span><span class="sxs-lookup"><span data-stu-id="a8045-125">Recording of video + holograms + ambient sound + hologram sound.</span></span>
<span data-ttu-id="a8045-126">다른 지원 앱과 함께 비디오를 저장 하거나, 전자 메일을 보내거나, 공유할 수 있도록 시트를 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8045-126">Share sheet so you can save video, email it, or share with other supporting apps.</span></span>

<span data-ttu-id="a8045-127">![표식](images/SpecViewPhoneDemo.jpg)
표식표식![](images/hololensspectatorview-500px.jpg) ![](images/spectatorview-300px.png)</span><span class="sxs-lookup"><span data-stu-id="a8045-127">![Marker](images/SpecViewPhoneDemo.jpg)
![Marker](images/hololensspectatorview-500px.jpg) ![Marker](images/spectatorview-300px.png)</span></span>

<span data-ttu-id="a8045-128">다음 표에서는 다양 한 Spectator 뷰 기능 및 해당 기능을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a8045-128">The following table shows different Spectator View functionality and their capabilities.</span></span> <span data-ttu-id="a8045-129">비디오 녹음 요구에 가장 적합 한 옵션을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8045-129">Choose the option that best fits your video recording needs:</span></span>

|                                      | <span data-ttu-id="a8045-130">휴대폰</span><span class="sxs-lookup"><span data-stu-id="a8045-130">Mobile</span></span>                  |                    <span data-ttu-id="a8045-131">비디오 카메라</span><span class="sxs-lookup"><span data-stu-id="a8045-131">Video Camera</span></span>              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| <span data-ttu-id="a8045-132">HD 품질</span><span class="sxs-lookup"><span data-stu-id="a8045-132">HD quality</span></span>                           |         <span data-ttu-id="a8045-133">전체 HD</span><span class="sxs-lookup"><span data-stu-id="a8045-133">Full HD</span></span>         |        <span data-ttu-id="a8045-134">전문 품질 filming (비디오 카메라에 의해 결정 됨)</span><span class="sxs-lookup"><span data-stu-id="a8045-134">Professional quality filming (as determined by video camera)</span></span>      |
| <span data-ttu-id="a8045-135">간편한 카메라 이동</span><span class="sxs-lookup"><span data-stu-id="a8045-135">Easy camera movement</span></span>                 |            <span data-ttu-id="a8045-136">✔</span><span class="sxs-lookup"><span data-stu-id="a8045-136">✔</span></span>            |                      <span data-ttu-id="a8045-137">✔</span><span class="sxs-lookup"><span data-stu-id="a8045-137">✔</span></span>                      |
| <span data-ttu-id="a8045-138">세 번째 사용자 뷰</span><span class="sxs-lookup"><span data-stu-id="a8045-138">Third-person view</span></span>                    |            <span data-ttu-id="a8045-139">✔</span><span class="sxs-lookup"><span data-stu-id="a8045-139">✔</span></span>            |                      <span data-ttu-id="a8045-140">✔</span><span class="sxs-lookup"><span data-stu-id="a8045-140">✔</span></span>                      |
| <span data-ttu-id="a8045-141">화면에 스트리밍할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8045-141">Can be streamed to screens</span></span>           |            <span data-ttu-id="a8045-142">✔</span><span class="sxs-lookup"><span data-stu-id="a8045-142">✔</span></span>            |                      <span data-ttu-id="a8045-143">✔</span><span class="sxs-lookup"><span data-stu-id="a8045-143">✔</span></span>                      |
| <span data-ttu-id="a8045-144">이식 가능</span><span class="sxs-lookup"><span data-stu-id="a8045-144">Portable</span></span>                             |            <span data-ttu-id="a8045-145">✔</span><span class="sxs-lookup"><span data-stu-id="a8045-145">✔</span></span>            |                                             |
| <span data-ttu-id="a8045-146">무선</span><span class="sxs-lookup"><span data-stu-id="a8045-146">Wireless</span></span>                             |            <span data-ttu-id="a8045-147">✔</span><span class="sxs-lookup"><span data-stu-id="a8045-147">✔</span></span>            |                                             |
| <span data-ttu-id="a8045-148">추가 필수 하드웨어</span><span class="sxs-lookup"><span data-stu-id="a8045-148">Additional required hardware</span></span>         |     <span data-ttu-id="a8045-149">Android 휴대폰, iPhone</span><span class="sxs-lookup"><span data-stu-id="a8045-149">Android phone, iPhone</span></span>    | <span data-ttu-id="a8045-150">HoloLens + Rig + Tripod + 비디오 카메라 + PC + Unity</span><span class="sxs-lookup"><span data-stu-id="a8045-150">HoloLens + Rig + Tripod + Video Camera + PC + Unity</span></span> |
| <span data-ttu-id="a8045-151">하드웨어 투자</span><span class="sxs-lookup"><span data-stu-id="a8045-151">Hardware investment</span></span>                  |           <span data-ttu-id="a8045-152">낮음</span><span class="sxs-lookup"><span data-stu-id="a8045-152">Low</span></span>            |                     <span data-ttu-id="a8045-153">높음</span><span class="sxs-lookup"><span data-stu-id="a8045-153">High</span></span>                    |
| <span data-ttu-id="a8045-154">플랫폼 간</span><span class="sxs-lookup"><span data-stu-id="a8045-154">Cross-platform</span></span>                       |           <span data-ttu-id="a8045-155">Android, iOS</span><span class="sxs-lookup"><span data-stu-id="a8045-155">Android, iOS</span></span>   |                                             |
| <span data-ttu-id="a8045-156">동기화 된 콘텐츠</span><span class="sxs-lookup"><span data-stu-id="a8045-156">Synchronized content</span></span>                 |            <span data-ttu-id="a8045-157">✔</span><span class="sxs-lookup"><span data-stu-id="a8045-157">✔</span></span>            |                      <span data-ttu-id="a8045-158">✔</span><span class="sxs-lookup"><span data-stu-id="a8045-158">✔</span></span>                      |
| <span data-ttu-id="a8045-159">런타임 설치 기간</span><span class="sxs-lookup"><span data-stu-id="a8045-159">Runtime setup duration</span></span>               |         <span data-ttu-id="a8045-160">대화</span><span class="sxs-lookup"><span data-stu-id="a8045-160">Instant</span></span>          |                     <span data-ttu-id="a8045-161">느림</span><span class="sxs-lookup"><span data-stu-id="a8045-161">Slow</span></span>                    |
## <a name="see-also"></a><span data-ttu-id="a8045-162">참조</span><span class="sxs-lookup"><span data-stu-id="a8045-162">See also</span></span>

* [<span data-ttu-id="a8045-163">혼합 현실 캡처</span><span class="sxs-lookup"><span data-stu-id="a8045-163">Mixed reality capture</span></span>](mixed-reality-capture.md) 
* [<span data-ttu-id="a8045-164">개발자를 위한 혼합 현실 캡처</span><span class="sxs-lookup"><span data-stu-id="a8045-164">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="a8045-165">혼합 현실의 공유 환경</span><span class="sxs-lookup"><span data-stu-id="a8045-165">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
