---
title: 관람자 보기
description: 외부 디스플레이에서 혼합 현실 환경을 보여 주거나 혼합 현실 환경의 비디오를 녹화하는 수단으로 외부 디바이스에서 홀로그램을 시각화합니다.
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: 관람자 보기, iPhone, iOS, iPad, OpenCV, 카메라, ARKit, HoloLens, Mixed Reality, Mixed Reality Toolkit, 데모, 레코드
ms.openlocfilehash: 9bc1c2809c7d780d439d9efb58f464b41de3dccd
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/29/2020
ms.locfileid: "74491166"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a><span data-ttu-id="d8107-104">HoloLens 및 HoloLens 2의 관람자 보기</span><span class="sxs-lookup"><span data-stu-id="d8107-104">Spectator View for HoloLens and HoloLens 2</span></span>

![표식](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a><span data-ttu-id="d8107-106">개요</span><span class="sxs-lookup"><span data-stu-id="d8107-106">Overview</span></span>

<span data-ttu-id="d8107-107">HoloLens를 착용할 때 이를 착용하지 않은 사람이 놀라운 것을 경험하지 못할 수 있다는 것을 잊는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="d8107-107">When wearing a HoloLens, we often forget that a person who does not have it on is unable to experience the wonders that we can.</span></span> <span data-ttu-id="d8107-108">관람자 보기를 사용하면 다른 사용자가 2D 화면에서 HoloLens 사용자가 자신의 세계에서 보는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8107-108">Spectator View allows others to see on a 2D screen what a HoloLens user sees in their world.</span></span>
<span data-ttu-id="d8107-109">관람자 보기는 모바일 디바이스를 사용하여 홀로그램을 HD로 녹화하는 빠르고 경제적인 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d8107-109">Spectator View offers a fast and affordable approach to recording holograms in HD with mobile devices.</span></span> <span data-ttu-id="d8107-110">또한 비디오 카메라를 사용하여 홀로그램을 전문적인 품질로 녹화하는 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d8107-110">It also offers a professional quality recording of holograms with video cameras.</span></span>

## <a name="key-resources"></a><span data-ttu-id="d8107-111">주요 리소스</span><span class="sxs-lookup"><span data-stu-id="d8107-111">Key Resources</span></span>

* [<span data-ttu-id="d8107-112">**GitHub의 관람자 보기**</span><span class="sxs-lookup"><span data-stu-id="d8107-112">**Spectator View on GitHub**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView)
* [<span data-ttu-id="d8107-113">**관람자 보기 설명서**</span><span class="sxs-lookup"><span data-stu-id="d8107-113">**Spectator View Documentation**</span></span>](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [<span data-ttu-id="d8107-114">**관람자 보기 샘플**</span><span class="sxs-lookup"><span data-stu-id="d8107-114">**Spectator View Samples**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a><span data-ttu-id="d8107-115">사용 사례</span><span class="sxs-lookup"><span data-stu-id="d8107-115">Use Cases</span></span>
* <span data-ttu-id="d8107-116">iPhone 또는 Android 디바이스를 사용하여 혼합 현실 환경을 녹화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8107-116">You can record a mixed reality experience using an iPhone or Android device.</span></span> <span data-ttu-id="d8107-117">Full HD로 녹화하고, 안티앨리어싱을 홀로그램과 그림자에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="d8107-117">Record in full HD and apply anti-aliasing to holograms and even shadows.</span></span> <span data-ttu-id="d8107-118">이는 홀로그램의 비디오를 캡처하는 비용 효율적이고 빠른 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="d8107-118">It is a cost-effective and quick way to capture video of holograms.</span></span>
* <span data-ttu-id="d8107-119">라이브 혼합 현실 환경을 지연 없이 iPhone 또는 iPad에서 Apple TV로 직접 스트림합니다!</span><span class="sxs-lookup"><span data-stu-id="d8107-119">Stream live mixed reality experiences to an Apple TV directly from your iPhone or iPad, lag-free!</span></span>
* <span data-ttu-id="d8107-120">게스트와 경험을 공유합니다. 비 HoloLens 사용자가 휴대폰 또는 태블릿에서 홀로그램을 직접 경험할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8107-120">Share the experience with guests: Let non-HoloLens users experience holograms directly from their phones or tablets.</span></span>

## <a name="current-features"></a><span data-ttu-id="d8107-121">현재 기능</span><span class="sxs-lookup"><span data-stu-id="d8107-121">Current Features</span></span>

* <span data-ttu-id="d8107-122">홀로그램의 공간 동기화를 통해 모든 사용자가 똑같은 장소에서 홀로그램을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8107-122">Spatial synchronization of Holograms, so everyone sees holograms in the exact same place.</span></span>
* <span data-ttu-id="d8107-123">iOS(ARKit 사용 디바이스) 및 Android(ARCore 사용 디바이스)를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="d8107-123">iOS (ARKit-enabled devices) and Android (ARCore-enabled devices) support.</span></span>
<span data-ttu-id="d8107-124">여러 iOS 게스트가 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8107-124">Multiple iOS guests.</span></span>
<span data-ttu-id="d8107-125">비디오 + 홀로그램 + 주변 소리 + 홀로그램 소리를 녹화합니다.</span><span class="sxs-lookup"><span data-stu-id="d8107-125">Recording of video + holograms + ambient sound + hologram sound.</span></span>
<span data-ttu-id="d8107-126">비디오를 저장하거나, 이메일로 보내거나, 다른 지원 앱과 공유할 수 있도록 시트를 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="d8107-126">Share sheet so you can save video, email it, or share with other supporting apps.</span></span>

<span data-ttu-id="d8107-127">![표식](images/SpecViewPhoneDemo.jpg)
![표식](images/hololensspectatorview-500px.jpg) ![표식](images/spectatorview-300px.png)</span><span class="sxs-lookup"><span data-stu-id="d8107-127">![Marker](images/SpecViewPhoneDemo.jpg)
![Marker](images/hololensspectatorview-500px.jpg) ![Marker](images/spectatorview-300px.png)</span></span>

<span data-ttu-id="d8107-128">다음 표에는 다양한 관람자 보기 기능 및 해당 특성이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8107-128">The following table shows different Spectator View functionality and their capabilities.</span></span> <span data-ttu-id="d8107-129">비디오 녹화 요구 사항에 가장 적합한 옵션을 선택하세요.</span><span class="sxs-lookup"><span data-stu-id="d8107-129">Choose the option that best fits your video recording needs:</span></span>

|                                      | <span data-ttu-id="d8107-130">모바일</span><span class="sxs-lookup"><span data-stu-id="d8107-130">Mobile</span></span>                  |                    <span data-ttu-id="d8107-131">비디오 카메라</span><span class="sxs-lookup"><span data-stu-id="d8107-131">Video Camera</span></span>              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| <span data-ttu-id="d8107-132">HD 품질</span><span class="sxs-lookup"><span data-stu-id="d8107-132">HD quality</span></span>                           |         <span data-ttu-id="d8107-133">Full HD</span><span class="sxs-lookup"><span data-stu-id="d8107-133">Full HD</span></span>         |        <span data-ttu-id="d8107-134">전문 품질 촬영(비디오 카메라)</span><span class="sxs-lookup"><span data-stu-id="d8107-134">Professional quality filming (as determined by video camera)</span></span>      |
| <span data-ttu-id="d8107-135">간편한 카메라 이동</span><span class="sxs-lookup"><span data-stu-id="d8107-135">Easy camera movement</span></span>                 |            <span data-ttu-id="d8107-136">✔</span><span class="sxs-lookup"><span data-stu-id="d8107-136">✔</span></span>            |                      <span data-ttu-id="d8107-137">✔</span><span class="sxs-lookup"><span data-stu-id="d8107-137">✔</span></span>                      |
| <span data-ttu-id="d8107-138">3인칭 보기</span><span class="sxs-lookup"><span data-stu-id="d8107-138">Third-person view</span></span>                    |            <span data-ttu-id="d8107-139">✔</span><span class="sxs-lookup"><span data-stu-id="d8107-139">✔</span></span>            |                      <span data-ttu-id="d8107-140">✔</span><span class="sxs-lookup"><span data-stu-id="d8107-140">✔</span></span>                      |
| <span data-ttu-id="d8107-141">화면으로 스트리밍 가능</span><span class="sxs-lookup"><span data-stu-id="d8107-141">Can be streamed to screens</span></span>           |            <span data-ttu-id="d8107-142">✔</span><span class="sxs-lookup"><span data-stu-id="d8107-142">✔</span></span>            |                      <span data-ttu-id="d8107-143">✔</span><span class="sxs-lookup"><span data-stu-id="d8107-143">✔</span></span>                      |
| <span data-ttu-id="d8107-144">이식 가능</span><span class="sxs-lookup"><span data-stu-id="d8107-144">Portable</span></span>                             |            <span data-ttu-id="d8107-145">✔</span><span class="sxs-lookup"><span data-stu-id="d8107-145">✔</span></span>            |                                             |
| <span data-ttu-id="d8107-146">무선</span><span class="sxs-lookup"><span data-stu-id="d8107-146">Wireless</span></span>                             |            <span data-ttu-id="d8107-147">✔</span><span class="sxs-lookup"><span data-stu-id="d8107-147">✔</span></span>            |                                             |
| <span data-ttu-id="d8107-148">추가 필수 하드웨어</span><span class="sxs-lookup"><span data-stu-id="d8107-148">Additional required hardware</span></span>         |     <span data-ttu-id="d8107-149">Android 휴대폰, iPhone</span><span class="sxs-lookup"><span data-stu-id="d8107-149">Android phone, iPhone</span></span>    | <span data-ttu-id="d8107-150">HoloLens + 의장품 + 삼각대 + 비디오 카메라 + PC + Unity</span><span class="sxs-lookup"><span data-stu-id="d8107-150">HoloLens + Rig + Tripod + Video Camera + PC + Unity</span></span> |
| <span data-ttu-id="d8107-151">하드웨어 투자</span><span class="sxs-lookup"><span data-stu-id="d8107-151">Hardware investment</span></span>                  |           <span data-ttu-id="d8107-152">낮음</span><span class="sxs-lookup"><span data-stu-id="d8107-152">Low</span></span>            |                     <span data-ttu-id="d8107-153">높음</span><span class="sxs-lookup"><span data-stu-id="d8107-153">High</span></span>                    |
| <span data-ttu-id="d8107-154">플랫폼 간</span><span class="sxs-lookup"><span data-stu-id="d8107-154">Cross-platform</span></span>                       |           <span data-ttu-id="d8107-155">Android, iOS</span><span class="sxs-lookup"><span data-stu-id="d8107-155">Android, iOS</span></span>   |                                             |
| <span data-ttu-id="d8107-156">동기화된 콘텐츠</span><span class="sxs-lookup"><span data-stu-id="d8107-156">Synchronized content</span></span>                 |            <span data-ttu-id="d8107-157">✔</span><span class="sxs-lookup"><span data-stu-id="d8107-157">✔</span></span>            |                      <span data-ttu-id="d8107-158">✔</span><span class="sxs-lookup"><span data-stu-id="d8107-158">✔</span></span>                      |
| <span data-ttu-id="d8107-159">런타임 설치 기간</span><span class="sxs-lookup"><span data-stu-id="d8107-159">Runtime setup duration</span></span>               |         <span data-ttu-id="d8107-160">즉시</span><span class="sxs-lookup"><span data-stu-id="d8107-160">Instant</span></span>          |                     <span data-ttu-id="d8107-161">느림</span><span class="sxs-lookup"><span data-stu-id="d8107-161">Slow</span></span>                    |
## <a name="see-also"></a><span data-ttu-id="d8107-162">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d8107-162">See also</span></span>

* [<span data-ttu-id="d8107-163">혼합 현실 캡처</span><span class="sxs-lookup"><span data-stu-id="d8107-163">Mixed reality capture</span></span>](mixed-reality-capture.md) 
* [<span data-ttu-id="d8107-164">개발자를 위한 혼합 현실 캡처</span><span class="sxs-lookup"><span data-stu-id="d8107-164">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="d8107-165">혼합 현실의 공유 환경</span><span class="sxs-lookup"><span data-stu-id="d8107-165">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
