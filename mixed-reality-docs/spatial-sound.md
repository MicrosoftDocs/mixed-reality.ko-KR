---
title: 혼합 현실에서 오디오
description: 혼합 현실에서 오디오는 UI 상호 작용의 사용자 신뢰도를 높이고 경험을 컨퍼런스 수 있습니다.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: 공간 음향, 서라운드 사운드, 3d 오디오, 3d 소리, 공간 오디오
ms.openlocfilehash: 1930017903439aee3ac53b6c4be344fdc44c356f
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641111"
---
# <a name="audio-in-mixed-reality"></a><span data-ttu-id="dc2ab-104">혼합 현실에서 오디오</span><span class="sxs-lookup"><span data-stu-id="dc2ab-104">Audio in Mixed Reality</span></span>
<span data-ttu-id="dc2ab-105">오디오는 혼합 현실에서 디자인 및 생산성의 필수적인 부분으로, 다음과 같은 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc2ab-105">Audio is an essential part of design and productivity in mixed reality, and can:</span></span>
* <span data-ttu-id="dc2ab-106">제스처 및 음성 기반 상호 작용의 사용자 신뢰도 향상</span><span class="sxs-lookup"><span data-stu-id="dc2ab-106">Increase user confidence in gesture- and voice-based interactions</span></span>
* <span data-ttu-id="dc2ab-107">사용자에 게 다음 단계로 안내</span><span class="sxs-lookup"><span data-stu-id="dc2ab-107">Guide users to next steps</span></span>
* <span data-ttu-id="dc2ab-108">가상 개체를 실제 세계와 효과적으로 결합</span><span class="sxs-lookup"><span data-stu-id="dc2ab-108">Effectively combine virtual objects with the real world</span></span>

<span data-ttu-id="dc2ab-109">HoloLens를 비롯 하 여 혼합 현실 헤드셋의 짧은 대기 시간 헤드 추적으로 고품질 HRTF 기반 spatialization을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc2ab-109">The low-latency head tracking of mixed reality headsets, including HoloLens, enables the use of high quality HRTF-based spatialization.</span></span> <span data-ttu-id="dc2ab-110">응용 프로그램의 Spatializing 오디오는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dc2ab-110">Spatializing audio in your application can:</span></span>
* <span data-ttu-id="dc2ab-111">시각적 요소에 주의를 기울여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc2ab-111">Call attention to visual elements</span></span>
* <span data-ttu-id="dc2ab-112">사용자가 실제 환경에 대 한 인식을 유지 하도록 지원</span><span class="sxs-lookup"><span data-stu-id="dc2ab-112">Help users maintain awareness of their real-world surroundings</span></span>

<span data-ttu-id="dc2ab-113">Acoustics를 더 깊게 추가 하면 holograms가 혼합 된 환경에 연결 되 고 환경 및 개체 상태에 대 한 큐를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc2ab-113">Adding acoustics more deeply connects holograms to the mixed world, and can provide cues about the environment and object state.</span></span>

<span data-ttu-id="dc2ab-114">오디오를 사용 하는 디자인에 대 한 자세한 예제는 [소리 디자인](spatial-sound-design.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dc2ab-114">For more detailed examples of design using audio, see [sound design](spatial-sound-design.md).</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/PTPvx7mDon4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="device-support"></a><span data-ttu-id="dc2ab-115">장치 지원</span><span class="sxs-lookup"><span data-stu-id="dc2ab-115">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dc2ab-116"><strong>기능과</strong></span><span class="sxs-lookup"><span data-stu-id="dc2ab-116"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="dc2ab-117"><a href="hololens-hardware-details.md"><strong>HoloLens(1세대)</strong></a></span><span class="sxs-lookup"><span data-stu-id="dc2ab-117"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="dc2ab-118"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="dc2ab-118"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="dc2ab-119"><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="dc2ab-119"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="dc2ab-120">Spatialization</span><span class="sxs-lookup"><span data-stu-id="dc2ab-120">Spatialization</span></span></td>
        <td><span data-ttu-id="dc2ab-121">✔️</span><span class="sxs-lookup"><span data-stu-id="dc2ab-121">✔️</span></span></td>
        <td><span data-ttu-id="dc2ab-122">✔️</span><span class="sxs-lookup"><span data-stu-id="dc2ab-122">✔️</span></span></td>
        <td><span data-ttu-id="dc2ab-123">✔️</span><span class="sxs-lookup"><span data-stu-id="dc2ab-123">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="dc2ab-124">Spatialization 하드웨어 가속</span><span class="sxs-lookup"><span data-stu-id="dc2ab-124">Spatialization hardware acceleration</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="dc2ab-125">✔️</span><span class="sxs-lookup"><span data-stu-id="dc2ab-125">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="using-sounds-in-mixed-reality"></a><span data-ttu-id="dc2ab-126">혼합 현실에서 소리 사용</span><span class="sxs-lookup"><span data-stu-id="dc2ab-126">Using sounds in mixed reality</span></span>
<span data-ttu-id="dc2ab-127">[혼합 현실에서 소리를 사용 하](spatial-sound-design.md) 는 경우 터치 및 키보드와 마우스 응용 프로그램에서와 다른 방법이 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc2ab-127">[Using sounds in mixed reality](spatial-sound-design.md) can require a different approach than in touch and keyboard-and-mouse applications.</span></span> <span data-ttu-id="dc2ab-128">핵심 설계 결정에는 spatialize 소리와 sonify에 대 한 상호 작용이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc2ab-128">Key sound design decisions include which sounds to spatialize and which interactions to sonify.</span></span> <span data-ttu-id="dc2ab-129">이러한 결정은 사용자 신뢰도, 생산성 및 학습 곡선에 크게 영향을 미칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc2ab-129">These decisions can have a strong effect on user confidence, productivity, and learning curve.</span></span>

### <a name="case-studies"></a><span data-ttu-id="dc2ab-130">사례 연구</span><span class="sxs-lookup"><span data-stu-id="dc2ab-130">Case studies</span></span>
<span data-ttu-id="dc2ab-131">HoloTour는 전 세계의 tourist 및 과거 사이트로 사용자를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc2ab-131">HoloTour virtually takes users to tourist and historical sites around the world.</span></span> <span data-ttu-id="dc2ab-132">다음 사례 연구에서는 HoloTour의 사운드 디자인에 대해 설명 합니다. [HoloTour에 대 한 소리 설계](case-study-spatial-sound-design-for-holotour.md).</span><span class="sxs-lookup"><span data-stu-id="dc2ab-132">The following case study describes the sound design for HoloTour: [Sound design for HoloTour](case-study-spatial-sound-design-for-holotour.md).</span></span> <span data-ttu-id="dc2ab-133">특수 마이크와 렌더링 설치 프로그램을 사용 하 여 주체 공간을 캡처 했습니다.</span><span class="sxs-lookup"><span data-stu-id="dc2ab-133">A special microphone and rendering setup were used to capture the subject spaces.</span></span>

<span data-ttu-id="dc2ab-134">RoboRaid는 HoloLens의 에너지 슈팅입니다.</span><span class="sxs-lookup"><span data-stu-id="dc2ab-134">RoboRaid is a high-energy shooter for HoloLens.</span></span> <span data-ttu-id="dc2ab-135">다음 사례 연구에서는 공간 오디오를 사용 하 여 [RoboRaid에 대 한 사운드 디자인](case-study-using-spatial-sound-in-roboraid.md)을 최대한 활용할 수 있도록 하기 위한 디자인 선택에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc2ab-135">The following case study describes the design choices made to ensure spatial audio was used to fullest dramatic effect: [Sound design for RoboRaid](case-study-using-spatial-sound-in-roboraid.md).</span></span>

## <a name="spatialization"></a><span data-ttu-id="dc2ab-136">Spatialization</span><span class="sxs-lookup"><span data-stu-id="dc2ab-136">Spatialization</span></span>
<span data-ttu-id="dc2ab-137">Spatialization는 공간 오디오의 방향 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="dc2ab-137">Spatialization is the directional component of spatial audio.</span></span> <span data-ttu-id="dc2ab-138">7\.1 home 극장 설치를 사용 하는 경우 spatialization는 큰 스피커 간을 이동 하는 것 처럼 간단 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc2ab-138">When using a 7.1 home theater setup, spatialization is as simple as panning between loud speakers.</span></span> <span data-ttu-id="dc2ab-139">그러나 혼합 현실에서 헤드폰이 있으면 정확도 및 편안 하 게 HRTF 기반 기술을 사용 하는 것이 필수적입니다.</span><span class="sxs-lookup"><span data-stu-id="dc2ab-139">But with headphones in mixed reality it's essential to use an HRTF-based technology for accuracy and comfort.</span></span> <span data-ttu-id="dc2ab-140">Windows에서는 HRTF 기반 spatialization를 제공 하며이 지원은 HoloLens 2에서 하드웨어 가속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc2ab-140">Windows offers HRTF-based spatialization, and this support is hardware-accelerated on HoloLens 2.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a><span data-ttu-id="dc2ab-141">Spatialize?</span><span class="sxs-lookup"><span data-stu-id="dc2ab-141">Should I spatialize?</span></span>
<span data-ttu-id="dc2ab-142">혼합 현실 응용 프로그램의 많은 소리는 수신기의 헤드에서 소리를 spatialization 하 고 전 세계에 배치 하는에서 혜택을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="dc2ab-142">Many sounds in mixed reality applications benefit from spatialization, which takes a sound out of the listener's head and places it in the world.</span></span> <span data-ttu-id="dc2ab-143">응용 프로그램에서 spatialization를 가장 효과적으로 사용 하는 방법에 대 한 제안은 [공간 음향 디자인](spatial-sound-design.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dc2ab-143">Refer to [Spatial Sound Design](spatial-sound-design.md) for suggestions on the most effective uses of spatialization in your application.</span></span>

### <a name="spatializer-personalization"></a><span data-ttu-id="dc2ab-144">Spatializer 개인 설정</span><span class="sxs-lookup"><span data-stu-id="dc2ab-144">Spatializer personalization</span></span>
<span data-ttu-id="dc2ab-145">HRTFs는 frequency 스펙트럼 간의 수준 및 단계 차이를 조작 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc2ab-145">HRTFs manipulate the level and phase differences between ears across the frequency spectrum.</span></span> <span data-ttu-id="dc2ab-146">실제 모델 및 사용자 헤드, 몸통 및 귀 셰이프 (pinnae)의 측정을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc2ab-146">They're based on physical models and measurements of human head, torso, and ear shapes (pinnae).</span></span> <span data-ttu-id="dc2ab-147">우리의 brains는 이러한 차이에 대응 하 여 소리 방향에 대 한 인식의 증가를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc2ab-147">Our brains respond to these differences to give rise to a perception of direction in sound.</span></span> 

<span data-ttu-id="dc2ab-148">모든 개인에 게는 고유한 귀 모양, 헤드 크기 및 귀 위치가 있으므로 가장 적합 한 HRTFs는 사용자에 게 맞는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="dc2ab-148">Every individual has a unique ear shape, head size, and ear position, so the best HRTFs are those that conform to you.</span></span> <span data-ttu-id="dc2ab-149">HoloLens는 헤드셋에서 IPD (pupilary distance)를 사용 하 여 spatialization 정확도를 높여 헤드 크기에 대 한 HRTFs를 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc2ab-149">HoloLens increases spatialization accuracy by using your inter-pupilary distance (IPD) from the headset displays to adjust the HRTFs for your head size.</span></span>

### <a name="spatializer-platform-support"></a><span data-ttu-id="dc2ab-150">Spatializer 플랫폼 지원</span><span class="sxs-lookup"><span data-stu-id="dc2ab-150">Spatializer platform support</span></span>
<span data-ttu-id="dc2ab-151">Windows에서는 [ISPATIALAUDIOCLIENT API](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound)를 통해 hrtfs를 비롯 한 spatialization을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc2ab-151">Windows offers spatialization, including HRTFs, via the [ISpatialAudioClient API](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound).</span></span> <span data-ttu-id="dc2ab-152">이 API는 HoloLens 2 HRTF 하드웨어 가속을 응용 프로그램에 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc2ab-152">This API exposes the HoloLens 2 HRTF hardware acceleration to applications.</span></span>

### <a name="spatializer-middleware-support"></a><span data-ttu-id="dc2ab-153">Spatializer 미들웨어 지원</span><span class="sxs-lookup"><span data-stu-id="dc2ab-153">Spatializer middleware support</span></span>
<span data-ttu-id="dc2ab-154">Windows ' HRTFs에 대 한 지원은 일부 타사 오디오 엔진에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc2ab-154">Support for Windows' HRTFs is available for some 3rd-party audio engines:</span></span>
* <span data-ttu-id="dc2ab-155">[Unity 오디오 엔진](spatial-sound-in-unity.md) 플러그 인은 HRTF xapo를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc2ab-155">A [Unity audio engine](spatial-sound-in-unity.md) plugin calls the HRTF XAPO</span></span>
* <span data-ttu-id="dc2ab-156">[Wtoaudio 엔진 플러그 인](https://www.audiokinetic.com/products/plug-ins/msspatial/) 은 ISpatialAudioClient API를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc2ab-156">A [Wwise audio engine plugin](https://www.audiokinetic.com/products/plug-ins/msspatial/) calls the ISpatialAudioClient API</span></span>

## <a name="acoustics"></a><span data-ttu-id="dc2ab-157">Acoustics</span><span class="sxs-lookup"><span data-stu-id="dc2ab-157">Acoustics</span></span>
<span data-ttu-id="dc2ab-158">공간 오디오는 방향 보다 약 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc2ab-158">Spatial audio can be about more than direction.</span></span> <span data-ttu-id="dc2ab-159">폐색, 장애물, 반향, portalling 및 원본 모델링를 포함 한 다른 차원을 통칭 하 여 ' acoustics ' 이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc2ab-159">Other dimensions, including occlusion, obstruction, reverb, portalling, and source modelling, are collectively referred to as 'acoustics'.</span></span> <span data-ttu-id="dc2ab-160">Acoustics를 사용 하지 않으면 spatialized 소리에는 인식 거리가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dc2ab-160">Without acoustics, spatialized sounds lack a perceived distance.</span></span>

<span data-ttu-id="dc2ab-161">Acoustics 처리의 범위는 단순에서 매우 복잡 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc2ab-161">Acoustics treatment can range from simple to very complex.</span></span> <span data-ttu-id="dc2ab-162">오디오 엔진에서 지원 되는 것과 같은 간단한 반향를 사용 하 여 수신기 주변 환경에 spatialized 소리를 푸시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc2ab-162">By using a simple reverb, such as that supported by any audio engine, you can push spatialized sounds out into the environment surrounding the listener.</span></span> <span data-ttu-id="dc2ab-163">[Project acoustics](https://aka.ms/acoustics)와 같은 acoustics 시스템에서 더 풍부 하 고 뛰어난 acoustics 처리를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc2ab-163">Richer and more compelling acoustics treatment is available from acoustics systems such as [Project Acoustics](https://aka.ms/acoustics).</span></span> <span data-ttu-id="dc2ab-164">Project Acoustics는 벽, 도어 및 기타 장면 기 하 도형의 효과를 소리로 모델링할 수 있으며, 관련 장면 기 하 도형을 개발 시에 알려진 경우에는 효과적인 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="dc2ab-164">Project Acoustics can model the effect of walls, doors, and other scene geometry on a sound, and is an effective option for cases where the relevant scene geometry is known at development time.</span></span>

