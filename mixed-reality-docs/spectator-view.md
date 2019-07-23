---
title: Spectator 뷰
description: 외부 디스플레이 또는 혼합 현실 환경의 비디오 녹화에서 혼합 현실 환경을 보여 주는 수단으로 외부 장치에서 holograms을 시각화 합니다.
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
keywords: Spectator View, iPhone, iOS, iPad, OpenCV, 카메라, ARKit, HoloLens, Mixed Reality, MixedRealityToolkit, 데모, 레코드
ms.openlocfilehash: 135a566456f1000669d2033edcf0d0b4649ccdf3
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387672"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a><span data-ttu-id="b30a9-104">HoloLens 및 HoloLens Spectator 보기 2</span><span class="sxs-lookup"><span data-stu-id="b30a9-104">Spectator View for HoloLens and HoloLens 2</span></span>

![표식](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a><span data-ttu-id="b30a9-106">개요</span><span class="sxs-lookup"><span data-stu-id="b30a9-106">Overview</span></span>

<span data-ttu-id="b30a9-107">HoloLens를 제공 하는 경우에는 자주 제공 하지 않는 사용자가 불가사의를 경험 하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30a9-107">When wearing a HoloLens, we often forget that a person who does not have it on is unable to experience the wonders that we can.</span></span> <span data-ttu-id="b30a9-108">Spectator 보기를 사용 하면 다른 사용자가 해당 지역에서 HoloLens 사용자에 게 표시 되는 2D 화면을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30a9-108">Spectator View allows others to see on a 2D screen what a HoloLens user sees in their world.</span></span>
<span data-ttu-id="b30a9-109">Spectator View는 모바일 장치를 사용 하 여 HD에 holograms을 기록 하는 빠르고 경제적인 접근 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b30a9-109">Spectator View offers a fast and affordable approach to recording holograms in HD with mobile devices.</span></span> <span data-ttu-id="b30a9-110">또한 비디오 카메라를 사용 하 여 holograms에 대 한 전문적인 품질 기록을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b30a9-110">It also offers a professional quality recording of holograms with video cameras.</span></span>

## <a name="key-resources"></a><span data-ttu-id="b30a9-111">주요 리소스</span><span class="sxs-lookup"><span data-stu-id="b30a9-111">Key Resources</span></span>

* [<span data-ttu-id="b30a9-112">**GitHub의 Spectator 보기**</span><span class="sxs-lookup"><span data-stu-id="b30a9-112">**Spectator View on GitHub**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView)
* [<span data-ttu-id="b30a9-113">**마이크로아키텍처**</span><span class="sxs-lookup"><span data-stu-id="b30a9-113">**Architecture**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/blob/master/doc/SpectatorView.Architecture.md)
* [<span data-ttu-id="b30a9-114">**표본의**</span><span class="sxs-lookup"><span data-stu-id="b30a9-114">**Samples**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)
* [<span data-ttu-id="b30a9-115">**모바일 설정 지침**</span><span class="sxs-lookup"><span data-stu-id="b30a9-115">**Mobile Setup Instructions**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/blob/master/doc/SpectatorView.Setup.md)
* [<span data-ttu-id="b30a9-116">**비디오 카메라 설치 지침**</span><span class="sxs-lookup"><span data-stu-id="b30a9-116">**Video Camera Setup Instructions**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/blob/master/doc/SpectatorView.Setup.VideoCamera.md)

## <a name="use-cases"></a><span data-ttu-id="b30a9-117">사용 사례</span><span class="sxs-lookup"><span data-stu-id="b30a9-117">Use Cases</span></span>
* <span data-ttu-id="b30a9-118">IPhone 또는 Android 장치를 사용 하 여 혼합 현실 환경을 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30a9-118">You can record a mixed reality experience using an iPhone or Android device.</span></span> <span data-ttu-id="b30a9-119">전체 HD를 기록 하 고 holograms 및 그림자에 앤티앨리어싱을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b30a9-119">Record in full HD and apply anti-aliasing to holograms and even shadows.</span></span> <span data-ttu-id="b30a9-120">Holograms 비디오를 빠르게 캡처하는 비용 효율적이 고 빠른 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="b30a9-120">It is a cost-effective and quick way to capture video of holograms.</span></span>
* <span data-ttu-id="b30a9-121">IPhone 또는 iPad에서 바로 Apple TV로 라이브 혼합 현실 경험을 스트리밍할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30a9-121">Stream live mixed reality experiences to an Apple TV directly from your iPhone or iPad, lag-free!</span></span>
* <span data-ttu-id="b30a9-122">게스트와 경험을 공유 합니다. HoloLens가 아닌 사용자가 휴대폰 또는 태블릿에서 직접 holograms 경험 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="b30a9-122">Share the experience with guests: Let non-HoloLens users experience holograms directly from their phones or tablets.</span></span>

## <a name="current-features"></a><span data-ttu-id="b30a9-123">현재 기능</span><span class="sxs-lookup"><span data-stu-id="b30a9-123">Current Features</span></span>

* <span data-ttu-id="b30a9-124">Holograms의 공간 동기화는 모든 사용자가 정확히 동일한 장소에서 Holograms을 볼 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b30a9-124">Spatial synchronization of Holograms, so everyone sees holograms in the exact same place.</span></span>
* <span data-ttu-id="b30a9-125">iOS (ARKit 사용 장치) 및 Android (Arkit 사용 장치) 지원.</span><span class="sxs-lookup"><span data-stu-id="b30a9-125">iOS (ARKit-enabled devices) and Android (ARCore-enabled devices) support.</span></span>
<span data-ttu-id="b30a9-126">여러 iOS 게스트.</span><span class="sxs-lookup"><span data-stu-id="b30a9-126">Multiple iOS guests.</span></span>
<span data-ttu-id="b30a9-127">비디오 + holograms + 주변 소리 + 홀로그램 소리의 기록입니다.</span><span class="sxs-lookup"><span data-stu-id="b30a9-127">Recording of video + holograms + ambient sound + hologram sound.</span></span>
<span data-ttu-id="b30a9-128">다른 지원 앱과 함께 비디오를 저장 하거나, 전자 메일을 보내거나, 공유할 수 있도록 시트를 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="b30a9-128">Share sheet so you can save video, email it, or share with other supporting apps.</span></span>

<span data-ttu-id="b30a9-129">![표식](images/SpecViewPhoneDemo.jpg)
표식표식![](images/hololensspectatorview-500px.jpg) ![](images/spectatorview-300px.png)</span><span class="sxs-lookup"><span data-stu-id="b30a9-129">![Marker](images/SpecViewPhoneDemo.jpg)
![Marker](images/hololensspectatorview-500px.jpg) ![Marker](images/spectatorview-300px.png)</span></span>

<span data-ttu-id="b30a9-130">다음 표에서는 다양 한 Spectator 뷰 기능 및 해당 기능을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b30a9-130">The following table shows different Spectator View functionality and their capabilities.</span></span> <span data-ttu-id="b30a9-131">비디오 녹음 요구에 가장 적합 한 옵션을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b30a9-131">Choose the option that best fits your video recording needs:</span></span>

|                                      | <span data-ttu-id="b30a9-132">휴대폰</span><span class="sxs-lookup"><span data-stu-id="b30a9-132">Mobile</span></span>                  |                    <span data-ttu-id="b30a9-133">비디오 카메라</span><span class="sxs-lookup"><span data-stu-id="b30a9-133">Video Camera</span></span>              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| <span data-ttu-id="b30a9-134">HD 품질</span><span class="sxs-lookup"><span data-stu-id="b30a9-134">HD quality</span></span>                           |         <span data-ttu-id="b30a9-135">전체 HD</span><span class="sxs-lookup"><span data-stu-id="b30a9-135">Full HD</span></span>         |        <span data-ttu-id="b30a9-136">전문 품질 filming (비디오 카메라에 의해 결정 됨)</span><span class="sxs-lookup"><span data-stu-id="b30a9-136">Professional quality filming (as determined by video camera)</span></span>      |
| <span data-ttu-id="b30a9-137">간편한 카메라 이동</span><span class="sxs-lookup"><span data-stu-id="b30a9-137">Easy camera movement</span></span>                 |            <span data-ttu-id="b30a9-138">✔</span><span class="sxs-lookup"><span data-stu-id="b30a9-138">✔</span></span>            |                      <span data-ttu-id="b30a9-139">✔</span><span class="sxs-lookup"><span data-stu-id="b30a9-139">✔</span></span>                      |
| <span data-ttu-id="b30a9-140">세 번째 사용자 뷰</span><span class="sxs-lookup"><span data-stu-id="b30a9-140">Third-person view</span></span>                    |            <span data-ttu-id="b30a9-141">✔</span><span class="sxs-lookup"><span data-stu-id="b30a9-141">✔</span></span>            |                      <span data-ttu-id="b30a9-142">✔</span><span class="sxs-lookup"><span data-stu-id="b30a9-142">✔</span></span>                      |
| <span data-ttu-id="b30a9-143">화면에 스트리밍할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b30a9-143">Can be streamed to screens</span></span>           |            <span data-ttu-id="b30a9-144">✔</span><span class="sxs-lookup"><span data-stu-id="b30a9-144">✔</span></span>            |                      <span data-ttu-id="b30a9-145">✔</span><span class="sxs-lookup"><span data-stu-id="b30a9-145">✔</span></span>                      |
| <span data-ttu-id="b30a9-146">이식 가능</span><span class="sxs-lookup"><span data-stu-id="b30a9-146">Portable</span></span>                             |            <span data-ttu-id="b30a9-147">✔</span><span class="sxs-lookup"><span data-stu-id="b30a9-147">✔</span></span>            |                                             |
| <span data-ttu-id="b30a9-148">무선</span><span class="sxs-lookup"><span data-stu-id="b30a9-148">Wireless</span></span>                             |            <span data-ttu-id="b30a9-149">✔</span><span class="sxs-lookup"><span data-stu-id="b30a9-149">✔</span></span>            |                                             |
| <span data-ttu-id="b30a9-150">추가 필수 하드웨어</span><span class="sxs-lookup"><span data-stu-id="b30a9-150">Additional required hardware</span></span>         |     <span data-ttu-id="b30a9-151">Android 휴대폰, iPhone</span><span class="sxs-lookup"><span data-stu-id="b30a9-151">Android phone, iPhone</span></span>    | <span data-ttu-id="b30a9-152">HoloLens + Rig + Tripod + 비디오 카메라 + PC + Unity</span><span class="sxs-lookup"><span data-stu-id="b30a9-152">HoloLens + Rig + Tripod + Video Camera + PC + Unity</span></span> |
| <span data-ttu-id="b30a9-153">하드웨어 투자</span><span class="sxs-lookup"><span data-stu-id="b30a9-153">Hardware investment</span></span>                  |           <span data-ttu-id="b30a9-154">낮음</span><span class="sxs-lookup"><span data-stu-id="b30a9-154">Low</span></span>            |                     <span data-ttu-id="b30a9-155">높음</span><span class="sxs-lookup"><span data-stu-id="b30a9-155">High</span></span>                    |
| <span data-ttu-id="b30a9-156">플랫폼 간</span><span class="sxs-lookup"><span data-stu-id="b30a9-156">Cross-platform</span></span>                       |           <span data-ttu-id="b30a9-157">Android, iOS</span><span class="sxs-lookup"><span data-stu-id="b30a9-157">Android, iOS</span></span>   |                                             |
| <span data-ttu-id="b30a9-158">동기화 된 콘텐츠</span><span class="sxs-lookup"><span data-stu-id="b30a9-158">Synchronized content</span></span>                 |            <span data-ttu-id="b30a9-159">✔</span><span class="sxs-lookup"><span data-stu-id="b30a9-159">✔</span></span>            |                      <span data-ttu-id="b30a9-160">✔</span><span class="sxs-lookup"><span data-stu-id="b30a9-160">✔</span></span>                      |
| <span data-ttu-id="b30a9-161">런타임 설치 기간</span><span class="sxs-lookup"><span data-stu-id="b30a9-161">Runtime setup duration</span></span>               |         <span data-ttu-id="b30a9-162">대화</span><span class="sxs-lookup"><span data-stu-id="b30a9-162">Instant</span></span>          |                     <span data-ttu-id="b30a9-163">느림</span><span class="sxs-lookup"><span data-stu-id="b30a9-163">Slow</span></span>                    |
## <a name="see-also"></a><span data-ttu-id="b30a9-164">참조</span><span class="sxs-lookup"><span data-stu-id="b30a9-164">See also</span></span>

* [<span data-ttu-id="b30a9-165">혼합 현실 캡처</span><span class="sxs-lookup"><span data-stu-id="b30a9-165">Mixed reality capture</span></span>](mixed-reality-capture.md) 
* [<span data-ttu-id="b30a9-166">개발자를 위한 혼합 현실 캡처</span><span class="sxs-lookup"><span data-stu-id="b30a9-166">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="b30a9-167">혼합 현실의 공유 환경</span><span class="sxs-lookup"><span data-stu-id="b30a9-167">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
