---
title: 공간 음향
description: 혼합된 현실 응용 프로그램에서 소리 공간을 사용 하 여 convincingly 3D 공간에서 소리를 배치할 수 있습니다.
author: hak0n
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: 공간 소리, 서라운드 사운드, 오디오 3d, 3d 공간, 사운드 오디오
ms.openlocfilehash: a30a484c4e47593556fbd1786158262551e11d22
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829919"
---
# <a name="spatial-sound"></a><span data-ttu-id="d8c01-104">공간 음향</span><span class="sxs-lookup"><span data-stu-id="d8c01-104">Spatial sound</span></span>

<span data-ttu-id="d8c01-105">개체는 시야를 벗어나는 경우 소리를 통해 우리 주변 진행 상황을 인식할 수 있습니다 우리가 하는 방법 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="d8c01-105">When objects are out of our line of sight, one of the ways that we can perceive what's going on around us is through sound.</span></span> <span data-ttu-id="d8c01-106">Windows Mixed Reality 오디오 엔진 방향, 거리 및 환경 시뮬레이션을 사용 하 여 3D 소리를 시뮬레이션 하 여 혼합 현실 환경 청각적 구성 요소를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c01-106">In Windows Mixed Reality, the audio engine provides the aural component of the mixed-reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="d8c01-107">공간 소리를 사용 하 여 응용 프로그램에서 convincingly 3 차원 공간의 (구)에 소리를 배치 하는 개발자를 사용자 대 모든 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8c01-107">Using spatial sound in an application allows developers to convincingly place sounds in a 3 dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="d8c01-108">그런 다음 실제 개체 또는 사용자의 환경에서 혼합된 현실 홀로그램에서 온 것 처럼 이러한 소리 친숙할 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c01-108">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="d8c01-109">가정 [홀로그램](hologram.md) 개체의 변경 되며 때로는 사운드 사운드 구성 요소를 통해 이익은 더 쉽게 만들고 더 몰입 형 환경을 새롭게 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c01-109">Given that [holograms](hologram.md) are objects made of light and sometimes sound, the sound component helps ground holograms making them more believable and creating a more immersive experience.</span></span>

<span data-ttu-id="d8c01-110">앱의 소리 모든 방향으로;에서 가져올 수 있습니다 홀로그램만에 표시 되는 시각적으로 사용자의 응시가 가리키고 있는 있지만 위에서 아래 뒤 쪽으로 등입니다. 현재 사용자의 보기에 없을 수도 있는 개체에 주목 하도록이 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8c01-110">Although holograms can only appear visually where the user's gaze is pointing, your app's sound can come from all directions; above, below, behind, to the side, etc. You can use this feature to draw attention to an object that might not currently be in the user's view.</span></span> <span data-ttu-id="d8c01-111">사용자는 소리 혼합 현실 세계에 있는 원본에서 페이지 수를 인식할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8c01-111">A user can perceive sounds to be emanating from a source in the mixed-reality world.</span></span> <span data-ttu-id="d8c01-112">예를 들어 사용자가 개체에 더 가깝게 또는 개체에 가까워질수록 볼륨 증가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c01-112">For example, as the user gets closer to an object or the object gets closer to them, the volume increases.</span></span> <span data-ttu-id="d8c01-113">마찬가지로 개체도 사용자 중심 또는 그 반대로 이동 하는 대로 공간 소리 소리 개체에서 직접 생성 되는 효과 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c01-113">Similarly, as objects move around a user, or vice versa, spatial sounds give the illusion that sounds are coming directly from the object.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/PTPvx7mDon4]

## <a name="device-support"></a><span data-ttu-id="d8c01-114">장치 지원</span><span class="sxs-lookup"><span data-stu-id="d8c01-114">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d8c01-115"><strong>기능</strong></span><span class="sxs-lookup"><span data-stu-id="d8c01-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="d8c01-116"><a href="hololens-hardware-details.md"><strong>HoloLens (첫 번째 범용)</strong></a></span><span class="sxs-lookup"><span data-stu-id="d8c01-116"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="d8c01-117"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="d8c01-117"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="d8c01-118"><a href="immersive-headset-hardware-details.md"><strong>몰입 형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="d8c01-118"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d8c01-119">공간 음향</span><span class="sxs-lookup"><span data-stu-id="d8c01-119">Spatial sound</span></span></td>
        <td><span data-ttu-id="d8c01-120">✔️</span><span class="sxs-lookup"><span data-stu-id="d8c01-120">✔️</span></span></td>
        <td><span data-ttu-id="d8c01-121">✔️</span><span class="sxs-lookup"><span data-stu-id="d8c01-121">✔️</span></span></td>
        <td><span data-ttu-id="d8c01-122">(사용 하 여 헤드폰) ✔️</span><span class="sxs-lookup"><span data-stu-id="d8c01-122">✔️ (with headphones)</span></span></td>
    </tr>
</table>

## <a name="simulating-the-perceived-location-and-distance-of-sounds"></a><span data-ttu-id="d8c01-123">인식 된 위치와 소리의 거리를 시뮬레이션합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c01-123">Simulating the perceived location and distance of sounds</span></span>

<span data-ttu-id="d8c01-124">분석 방법 사운드에 도달 하 여 모두 우리의 돌릴 뇌 결정 거리와 소리를 내보내는 개체의 방향입니다.</span><span class="sxs-lookup"><span data-stu-id="d8c01-124">By analyzing how sound reaches both our ears, our brain determines the distance and direction of the object emitting the sound.</span></span> <span data-ttu-id="d8c01-125">HRTF (또는 Head 관련 전송 함수)는 귀 소리 공간에서 지점에서 수신 하는 방법을 지정 하는 스펙트럼 응답을 모델링 하 여이 상호 작용을 시뮬레이션 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c01-125">An HRTF (or Head Related Transfer Function) simulates this interaction by modeling the spectral response that characterizes how an ear receives sound from a point in space.</span></span> <span data-ttu-id="d8c01-126">공간 오디오 엔진 개인 설정 된 HRTFs를 사용 하 여 혼합된 현실 환경을 확장 하 고 다양 한 방향 및 거리에서 생성 되는 소리를 시뮬레이트합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c01-126">The spatial audio engine uses personalized HRTFs to expand the mixed reality experience, and simulate sounds that are coming from various directions and distances.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/aB3TDjYklmo]

<span data-ttu-id="d8c01-127">왼쪽 또는 오른쪽 (방위) 오디오 신호 소리 각 귀 도착 시간 차이에서 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c01-127">Left or right audio (azimuth) cues originate from differences in the time sound arrives at each ear.</span></span> <span data-ttu-id="d8c01-128">신호 위/아래로 외부 귀 모양 (pinnae)으로 생성 된 스펙트럼 변경에서 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c01-128">Up and down cues originate from spectral changes produced by the outer ear shape (pinnae).</span></span> <span data-ttu-id="d8c01-129">지정 하 여 오디오에서 제공 되는 경우 시스템 경험을 시뮬레이션할 수 소리는 귀에 서로 다른 시간에 도착 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c01-129">By designating where audio is coming from, the system can simulate the experience of sound arriving at different times to our ears.</span></span> <span data-ttu-id="d8c01-130">HoloLens, 방위 공간화 개인화 된 동안 상승 시뮬레이션 기반 anthropometrics의 평균 집합에 대해 참고 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c01-130">Note that on HoloLens, while azimuth spatialization is personalized, the simulation of elevation is based on an average set of anthropometrics.</span></span> <span data-ttu-id="d8c01-131">따라서 권한 상승 정확도 방위 정확도 보다 낮을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8c01-131">Thus, elevation accuracy may be less accurate than azimuth accuracy.</span></span>

<span data-ttu-id="d8c01-132">소리의 특징 존재 하는 환경에 따라 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8c01-132">The characteristics of sounds also change based on the environment in which they exist.</span></span> <span data-ttu-id="d8c01-133">예를 들어 있는 동굴에 shouting echo 효과 만드는 벽, 작업장 및 최대값이, 총알이 음성을 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c01-133">For instance, shouting in a cave will cause your voice to bounce off the walls, floors, and ceilings, creating an echo effect.</span></span> <span data-ttu-id="d8c01-134">공간 소리 공간 모델 설정이 특정 오디오 환경에서 소리를 배치에 이러한 반사를 재현 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c01-134">The room model setting of spatial sound reproduces these reflections to place sounds in a particular audio environment.</span></span> <span data-ttu-id="d8c01-135">오디오 더 몰입 형 환경을 만들 수는 공간에서 소리의 시뮬레이션을 위해 사용자의 실제 위치와 일치 하도록이 설정을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8c01-135">You can use this setting to match the user's actual location for simulation of sounds in that space to create a more immersive audio experience.</span></span>

## <a name="integrating-spatial-sound"></a><span data-ttu-id="d8c01-136">공간 소리를 통합합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c01-136">Integrating spatial sound</span></span>

<span data-ttu-id="d8c01-137">일반적인 원칙 혼합된 현실에 포함 되므로 [홀로그램](hologram.md) 사용자의 실제 또는 가상 환경에서 홀로그램에서 대부분의 소리 spatialized 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c01-137">Because the general principle of mixed reality is to ground [holograms](hologram.md) in the user's physical world or virtual environment, most sounds from holograms should be spatialized.</span></span> <span data-ttu-id="d8c01-138">HoloLens에서 자연스럽 게 CPU 및 메모리 예산 고려 사항, 있지만 10-12 공간 사운드 음성 있습니다 ~ 12% 미만의 CPU (4 개 코어 중 하나의 ~ 70%)를 사용 하는 동안 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8c01-138">On HoloLens, there are naturally CPU and memory budget considerations, but you can use 10-12 spatial sound voices there while using less than ~12% of the CPU (~70% of one of the four cores).</span></span> <span data-ttu-id="d8c01-139">공간 사운드 음성에 대 한 권장된 사용은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d8c01-139">Recommended use for spatial sound voices include:</span></span>
* <span data-ttu-id="d8c01-140">Gaze 혼합 (특히 범위를 벗어난 경우 뷰 개체를 강조 표시).</span><span class="sxs-lookup"><span data-stu-id="d8c01-140">Gaze Mixing (highlighting objects, particularly when out of view).</span></span> <span data-ttu-id="d8c01-141">홀로그램에서 사용자의 주의 필요한 경우 해당 홀로그램에서 소리 재생 (예: 가상 dog bark 해야 함).</span><span class="sxs-lookup"><span data-stu-id="d8c01-141">When a hologram needs a user's attention, play a sound on that hologram (e.g. have a virtual dog bark).</span></span> <span data-ttu-id="d8c01-142">그러면 사용자는 홀로그램 보기에 없는 경우 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8c01-142">This helps the user to find the hologram when it is not in view.</span></span>
* <span data-ttu-id="d8c01-143">오디오 Haptics (touchless 상호 작용에 반응 오디오).</span><span class="sxs-lookup"><span data-stu-id="d8c01-143">Audio Haptics (reactive audio for touchless interactions).</span></span> <span data-ttu-id="d8c01-144">예를 들어, 사용자의 직접 또는 동작 컨트롤러 입력 및 제스처 프레임 종료 될 때 소리를 재생 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c01-144">For example, play a sound when the user's hand or motion controller enters and exits the gesture frame.</span></span> <span data-ttu-id="d8c01-145">또는 홀로그램을 선택할 때 소리를 재생 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c01-145">Or play a sound when the user selects a hologram.</span></span>
* <span data-ttu-id="d8c01-146">집중 교육 (앰비언트 소리 사용자 관련)입니다.</span><span class="sxs-lookup"><span data-stu-id="d8c01-146">Immersion (ambient sounds surrounding the user).</span></span>

<span data-ttu-id="d8c01-147">공간 소리를 사용 하 여 표준 스테레오 소리를 혼합 하는 것은 현실적인 환경 만들기에 적용 될 수 있지만, 스테레오 소리 공간에서 반사 (예: 공간 소리 미묘한 측면을 남겨 비교적 자동 수 있어야 한다는 것을 알아야 이기도 신호 거리)는 의견을 듣고 시끄러운 환경에서 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d8c01-147">It is also important to note that while blending standard stereo sounds with spatial sound can be effective in creating realistic environments, the stereo sounds should be relatively quiet to leave room for the subtle aspects of spatial sound, such as reflections (distance cues) that can be difficult to hear in a noisy environment.</span></span>

<span data-ttu-id="d8c01-148">Windows의 공간 사운드 엔진 48 k 샘플링 주기 재생만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="d8c01-148">Windows' spatial sound engine only supports a 48k sample rate for playback.</span></span> <span data-ttu-id="d8c01-149">Unity와 같은 대부분의 미들웨어를 자동으로 사운드 파일을 지원 되는 형식으로 변환 되지만 Windows 오디오 Api를 직접 사용 하는 경우의 효과 의해 지원 되는 형식에 콘텐츠를 형식에 맞게 하세요 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d8c01-149">Most middleware, such as Unity, will automatically convert sound files into the supported format, but when using Windows Audio APIs directly please match the format of the content to the format supported by the effect.</span></span>

## <a name="see-also"></a><span data-ttu-id="d8c01-150">참조</span><span class="sxs-lookup"><span data-stu-id="d8c01-150">See also</span></span>
* [<span data-ttu-id="d8c01-151">MR Spatial 220</span><span class="sxs-lookup"><span data-stu-id="d8c01-151">MR Spatial 220</span></span>](holograms-220.md)
* [<span data-ttu-id="d8c01-152">Unity의 공간 음향</span><span class="sxs-lookup"><span data-stu-id="d8c01-152">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="d8c01-153">DirectX의 공간 음향</span><span class="sxs-lookup"><span data-stu-id="d8c01-153">Spatial sound in DirectX</span></span>](spatial-sound-in-directx.md)
* [<span data-ttu-id="d8c01-154">공간 음향 디자인</span><span class="sxs-lookup"><span data-stu-id="d8c01-154">Spatial sound design</span></span>](spatial-sound-design.md)
