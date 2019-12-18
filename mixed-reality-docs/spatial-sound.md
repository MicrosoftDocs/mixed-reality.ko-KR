---
title: 혼합 현실에서 오디오
description: 혼합 현실에서 오디오는 UI 상호 작용의 사용자 신뢰도를 높이고 경험을 컨퍼런스 수 있습니다.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: 공간 음향, 서라운드 사운드, 3d 오디오, 3d 소리, 공간 오디오
ms.openlocfilehash: b939433daf80a95a11bc0e1ac2ffd75dfe0cf299
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181983"
---
# <a name="audio-in-mixed-reality"></a><span data-ttu-id="f1a28-104">혼합 현실에서 오디오</span><span class="sxs-lookup"><span data-stu-id="f1a28-104">Audio in mixed reality</span></span>
<span data-ttu-id="f1a28-105">오디오는 혼합 현실에서 디자인 및 생산성의 필수적인 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-105">Audio is an essential part of design and productivity in mixed reality.</span></span> <span data-ttu-id="f1a28-106">사운드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-106">Sound can:</span></span>
* <span data-ttu-id="f1a28-107">제스처 및 음성 조작에서 사용자 신뢰도를 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-107">Increase user confidence in gesture and voice interactions.</span></span>
* <span data-ttu-id="f1a28-108">사용자에 게 다음 단계를 안내 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-108">Guide users to next steps.</span></span>
* <span data-ttu-id="f1a28-109">가상 개체를 실제 세계와 효과적으로 결합 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-109">Effectively combine virtual objects with the real world.</span></span>

<span data-ttu-id="f1a28-110">HoloLens를 비롯 한 혼합 현실 헤드셋의 짧은 대기 시간 헤드 추적은 고품질 HRTF 기반 spatialization을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-110">The low-latency head tracking of mixed reality headsets, including HoloLens, supports high-quality HRTF-based spatialization.</span></span> <span data-ttu-id="f1a28-111">응용 프로그램에서 오디오를 spatialize 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-111">You can spatialize audio in your application to:</span></span>
* <span data-ttu-id="f1a28-112">시각적 요소에 주의를 기울여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-112">Call attention to visual elements.</span></span>
* <span data-ttu-id="f1a28-113">사용자가 실제 환경에 대 한 인식을 유지 하도록 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-113">Help users maintain awareness of their real-world surroundings.</span></span>

<span data-ttu-id="f1a28-114">Acoustics는 혼합 현실 세계에 holograms을 더욱 깊이 있게 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-114">Acoustics more deeply connect holograms to the mixed-reality world.</span></span> <span data-ttu-id="f1a28-115">환경 및 개체 상태에 대 한 신호를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-115">It provides cues about the environment and object state.</span></span>

<span data-ttu-id="f1a28-116">[오디오를 사용 하는 디자인의 자세한 예를](spatial-sound-design.md)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f1a28-116">See detailed [examples of design that uses audio](spatial-sound-design.md).</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/PTPvx7mDon4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="device-support"></a><span data-ttu-id="f1a28-117">장치 지원</span><span class="sxs-lookup"><span data-stu-id="f1a28-117">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="f1a28-118"><strong>기능</strong></span><span class="sxs-lookup"><span data-stu-id="f1a28-118"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="f1a28-119"><a href="hololens-hardware-details.md"><strong>HoloLens (첫 번째 gen)</strong></a></span><span class="sxs-lookup"><span data-stu-id="f1a28-119"><a href="hololens-hardware-details.md"><strong>HoloLens (first gen)</strong></a></span></span></td>
        <td><span data-ttu-id="f1a28-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="f1a28-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="f1a28-121"><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="f1a28-121"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="f1a28-122">Spatialization</span><span class="sxs-lookup"><span data-stu-id="f1a28-122">Spatialization</span></span></td>
        <td><span data-ttu-id="f1a28-123">✔️</span><span class="sxs-lookup"><span data-stu-id="f1a28-123">✔️</span></span></td>
        <td><span data-ttu-id="f1a28-124">✔️</span><span class="sxs-lookup"><span data-stu-id="f1a28-124">✔️</span></span></td>
        <td><span data-ttu-id="f1a28-125">✔️</span><span class="sxs-lookup"><span data-stu-id="f1a28-125">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="f1a28-126">Spatialization 하드웨어 가속</span><span class="sxs-lookup"><span data-stu-id="f1a28-126">Spatialization hardware acceleration</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="f1a28-127">✔️</span><span class="sxs-lookup"><span data-stu-id="f1a28-127">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="use-of-sounds-in-mixed-reality"></a><span data-ttu-id="f1a28-128">혼합 현실에서 소리 사용</span><span class="sxs-lookup"><span data-stu-id="f1a28-128">Use of sounds in mixed reality</span></span>
<span data-ttu-id="f1a28-129">[혼합 현실에서 소리를 사용](spatial-sound-design.md) 하려면 터치 및 키보드 및 마우스 응용 프로그램에서와 다른 방법이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-129">[Use of sounds in mixed reality](spatial-sound-design.md) requires a different approach than in touch and keyboard-and-mouse applications.</span></span> <span data-ttu-id="f1a28-130">핵심 설계 결정에는 spatialize 소리와 sonify에 대 한 상호 작용이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-130">Key sound design decisions include which sounds to spatialize and which interactions to sonify.</span></span> <span data-ttu-id="f1a28-131">이러한 결정은 사용자 신뢰도, 생산성 및 학습 곡선에 크게 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-131">These decisions strongly effect user confidence, productivity, and learning curve.</span></span>

### <a name="case-studies"></a><span data-ttu-id="f1a28-132">사례 연구</span><span class="sxs-lookup"><span data-stu-id="f1a28-132">Case studies</span></span>
<span data-ttu-id="f1a28-133">HoloTour는 전 세계의 tourist 및 과거 사이트로 사용자를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-133">HoloTour virtually takes users to tourist and historical sites around the world.</span></span> <span data-ttu-id="f1a28-134">HoloTour 사례 연구는 [사운드 디자인](case-study-spatial-sound-design-for-holotour.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f1a28-134">See the [Sound design for HoloTour](case-study-spatial-sound-design-for-holotour.md) case study.</span></span> <span data-ttu-id="f1a28-135">특수 마이크와 렌더링 설치 프로그램을 사용 하 여 주체 공간을 캡처 했습니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-135">A special microphone and rendering setup were used to capture the subject spaces.</span></span>

<span data-ttu-id="f1a28-136">RoboRaid는 HoloLens의 에너지 슈팅입니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-136">RoboRaid is a high-energy shooter for HoloLens.</span></span> <span data-ttu-id="f1a28-137">RoboRaid 사례 연구를 [위한 사운드 디자인](case-study-using-spatial-sound-in-roboraid.md) 은 공간 오디오를 매우 극적으로 사용할 수 있도록 하기 위해 수행 된 디자인 선택 사항을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-137">The [Sound design for RoboRaid](case-study-using-spatial-sound-in-roboraid.md) case study describes the design choices that were made to ensure spatial audio was used to the fullest dramatic effect.</span></span>

## <a name="spatialization"></a><span data-ttu-id="f1a28-138">Spatialization</span><span class="sxs-lookup"><span data-stu-id="f1a28-138">Spatialization</span></span>
<span data-ttu-id="f1a28-139">Spatialization는 공간 오디오의 방향 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-139">Spatialization is the directional component of spatial audio.</span></span> <span data-ttu-id="f1a28-140">7\.1 home 극장 설정의 경우 spatialization는 loudspeakers 간에 이동 하는 것 만큼 간단 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-140">For a 7.1 home theater setup, spatialization is as simple as panning between loudspeakers.</span></span> <span data-ttu-id="f1a28-141">그러나 혼합 현실 헤드폰의 경우 정확도와 편안 하 게 HRTF 기반 기술을 사용 하는 것이 필수적입니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-141">But for headphones in mixed reality, it's essential to use an HRTF-based technology for accuracy and comfort.</span></span> <span data-ttu-id="f1a28-142">Windows에서는 HRTF 기반 spatialization를 제공 하며이 지원은 HoloLens 2에서 하드웨어 가속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-142">Windows offers HRTF-based spatialization, and this support is hardware-accelerated on HoloLens 2.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a><span data-ttu-id="f1a28-143">Spatialize?</span><span class="sxs-lookup"><span data-stu-id="f1a28-143">Should I spatialize?</span></span>
<span data-ttu-id="f1a28-144">Spatialization는 혼합 현실 응용 프로그램에서 많은 소리를 개선할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-144">Spatialization can improve many sounds in mixed-reality applications.</span></span> <span data-ttu-id="f1a28-145">Spatialization는 수신기의 헤드에서 소리를 가져와 세계에 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-145">Spatialization takes a sound out of the listener's head and places it in the world.</span></span> <span data-ttu-id="f1a28-146">응용 프로그램에서 spatialization를 효과적으로 사용 하는 방법에 대 한 제안은 [공간 음향 디자인](spatial-sound-design.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f1a28-146">For suggestions on effective use of spatialization in your application, see [Spatial sound design](spatial-sound-design.md).</span></span>

### <a name="spatializer-personalization"></a><span data-ttu-id="f1a28-147">Spatializer 개인 설정</span><span class="sxs-lookup"><span data-stu-id="f1a28-147">Spatializer personalization</span></span>
<span data-ttu-id="f1a28-148">HRTFs는 frequency 스펙트럼 간의 수준 및 단계 차이를 조작 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-148">HRTFs manipulate the level and phase differences between ears across the frequency spectrum.</span></span> <span data-ttu-id="f1a28-149">실제 모델 및 사용자 헤드, 몸통 및 귀 셰이프 (pinnae)의 측정을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-149">They're based on physical models and measurements of human head, torso, and ear shapes (pinnae).</span></span> <span data-ttu-id="f1a28-150">우리의 brains는 이러한 차이에 대응 하 여 소리로 인 한 방향을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-150">Our brains respond to these differences to provide perceived direction in sound.</span></span>

<span data-ttu-id="f1a28-151">모든 개인에는 고유한 귀 모양, 헤드 크기 및 귀 위치가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-151">Every individual has a unique ear shape, head size, and ear position.</span></span> <span data-ttu-id="f1a28-152">따라서 최상의 HRTFs가 사용자를 준수 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-152">So the best HRTFs conform to you.</span></span> <span data-ttu-id="f1a28-153">Spatialization 정확도를 높이기 위해 HoloLens는 헤드셋 디스플레이에서 pupilary 거리 (IPD)를 사용 하 여 헤드 크기에 대 한 HRTFs를 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-153">To increase spatialization accuracy, HoloLens uses your inter-pupilary distance (IPD) from the headset displays to adjust the HRTFs for your head size.</span></span>

### <a name="spatializer-platform-support"></a><span data-ttu-id="f1a28-154">Spatializer 플랫폼 지원</span><span class="sxs-lookup"><span data-stu-id="f1a28-154">Spatializer platform support</span></span>
<span data-ttu-id="f1a28-155">Windows에서는 [ISPATIALAUDIOCLIENT API](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound)를 통해 hrtfs를 비롯 한 spatialization을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-155">Windows offers spatialization, including HRTFs, via the [ISpatialAudioClient API](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound).</span></span> <span data-ttu-id="f1a28-156">이 API는 HoloLens 2 HRTF 하드웨어 가속을 응용 프로그램에 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-156">This API exposes the HoloLens 2 HRTF hardware acceleration to applications.</span></span>

### <a name="spatializer-middleware-support"></a><span data-ttu-id="f1a28-157">Spatializer 미들웨어 지원</span><span class="sxs-lookup"><span data-stu-id="f1a28-157">Spatializer middleware support</span></span>
<span data-ttu-id="f1a28-158">Windows ' HRTFs에 대 한 지원은 다음 타사 오디오 엔진에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-158">Support for Windows' HRTFs is available for the following third-party audio engines.</span></span>
* <span data-ttu-id="f1a28-159">[Unity 오디오 엔진 플러그 인](spatial-sound-in-unity.md)</span><span class="sxs-lookup"><span data-stu-id="f1a28-159">A [Unity audio engine plugin](spatial-sound-in-unity.md)</span></span>
* <span data-ttu-id="f1a28-160">[Wtoaudio 엔진 플러그 인](https://www.audiokinetic.com/products/plug-ins/msspatial/)</span><span class="sxs-lookup"><span data-stu-id="f1a28-160">A [Wwise audio engine plugin](https://www.audiokinetic.com/products/plug-ins/msspatial/)</span></span>

## <a name="acoustics"></a><span data-ttu-id="f1a28-161">Acoustics</span><span class="sxs-lookup"><span data-stu-id="f1a28-161">Acoustics</span></span>
<span data-ttu-id="f1a28-162">공간 오디오는 방향에 대 한 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-162">Spatial audio is about more than direction.</span></span> <span data-ttu-id="f1a28-163">다른 차원에는 폐색, 장애물, 반향, portalling 및 원본 모델링이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-163">Other dimensions include occlusion, obstruction, reverb, portalling, and source modeling.</span></span> <span data-ttu-id="f1a28-164">이러한 차원을 통틀어 *acoustics*라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-164">Collectively these dimensions are referred to as *acoustics*.</span></span> <span data-ttu-id="f1a28-165">Acoustics 없이 spatialized 소리는 인식 거리가 부족 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-165">Without acoustics, spatialized sounds lack perceived distance.</span></span>

<span data-ttu-id="f1a28-166">Acoustics 처리가의 범위는 단순에서 매우 복잡 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-166">Acoustics treatments range from simple to very complex.</span></span> <span data-ttu-id="f1a28-167">모든 오디오 엔진에서 지원 되는 간단한 반향을 사용 하 여 수신기 환경에 spatialized 소리를 푸시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-167">You can use a simple reverb that's supported by any audio engine to push spatialized sounds into the environment of the listener.</span></span> <span data-ttu-id="f1a28-168">[Project Acoustics](https://aka.ms/acoustics) 와 같은 Acoustics 시스템은 보다 풍부 하 고 뛰어난 Acoustics 처리를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-168">Acoustics systems such as [Project Acoustics](https://aka.ms/acoustics)  provide richer and more compelling acoustics treatment.</span></span> <span data-ttu-id="f1a28-169">프로젝트 Acoustics 벽, 도어 및 기타 장면 기 하 도형의 효과를 소리로 모델링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-169">Project Acoustics can model the effect of walls, doors, and other scene geometry on a sound.</span></span> <span data-ttu-id="f1a28-170">이는 관련 장면 기 하 도형을 개발 시에 알려진 경우에 효과적으로 사용할 수 있는 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="f1a28-170">It's an effective option for cases where the relevant scene geometry is known at development time.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f1a28-171">다음 단계</span><span class="sxs-lookup"><span data-stu-id="f1a28-171">Next steps</span></span>
- [<span data-ttu-id="f1a28-172">Unity의 공간 음향</span><span class="sxs-lookup"><span data-stu-id="f1a28-172">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
- [<span data-ttu-id="f1a28-173">혼합 현실 응용 프로그램에서 소리를 사용 하는 방법</span><span class="sxs-lookup"><span data-stu-id="f1a28-173">How to use sound in mixed-reality applications</span></span>](spatial-sound-design.md)
