---
title: 공간 음향
description: 혼합 현실 응용 프로그램에서 공간 소리를 사용 하면 3D 공간에 소리를 convincingly 수 있습니다.
author: hak0n
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: 공간 음향, 서라운드 사운드, 3d 오디오, 3d 소리, 공간 오디오
ms.openlocfilehash: a30a484c4e47593556fbd1786158262551e11d22
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829919"
---
# <a name="spatial-sound"></a><span data-ttu-id="c6257-104">공간 음향</span><span class="sxs-lookup"><span data-stu-id="c6257-104">Spatial sound</span></span>

<span data-ttu-id="c6257-105">개체를 볼 수 없는 경우에는 소리를 통해 무엇을 하 고 있는지 확인할 수 있는 방법 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="c6257-105">When objects are out of our line of sight, one of the ways that we can perceive what's going on around us is through sound.</span></span> <span data-ttu-id="c6257-106">Windows Mixed Reality에서 오디오 엔진은 방향, 거리 및 환경 시뮬레이션을 사용 하 여 3D 소리를 시뮬레이션 하 여 혼합 현실 환경의 aural 구성 요소를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6257-106">In Windows Mixed Reality, the audio engine provides the aural component of the mixed-reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="c6257-107">개발자는 응용 프로그램에서 공간 소리를 사용 하 여 모든 사용자에 게 3 차원 공간 (구)의 소리를 convincingly 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6257-107">Using spatial sound in an application allows developers to convincingly place sounds in a 3 dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="c6257-108">이러한 소리는 실제 물리적 개체 또는 사용자 환경에서 혼합 현실 holograms에서 가져온 것 처럼 보입니다.</span><span class="sxs-lookup"><span data-stu-id="c6257-108">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="c6257-109">[Holograms](hologram.md) 는 빛이 고 때로는 소리가 나도록 하는 개체 이기 때문에, 소리 구성 요소를 사용 하 여 더 많은 이익은를 만들고 더 몰입 형 환경을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6257-109">Given that [holograms](hologram.md) are objects made of light and sometimes sound, the sound component helps ground holograms making them more believable and creating a more immersive experience.</span></span>

<span data-ttu-id="c6257-110">Holograms는 사용자의 응시가 가리키는 경우에만 시각적으로 나타날 수 있지만 앱의 소리는 모든 방향에서 제공 될 수 있습니다. 위, 아래, 옆, 등 이 기능을 사용 하 여 현재 사용자의 보기에 있지 않을 수 있는 개체에 주의를 기울일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6257-110">Although holograms can only appear visually where the user's gaze is pointing, your app's sound can come from all directions; above, below, behind, to the side, etc. You can use this feature to draw attention to an object that might not currently be in the user's view.</span></span> <span data-ttu-id="c6257-111">사용자는 혼합 현실 세계의 원본에서 소리를 emanating 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6257-111">A user can perceive sounds to be emanating from a source in the mixed-reality world.</span></span> <span data-ttu-id="c6257-112">예를 들어, 사용자가 개체에 가까이 있거나 개체가 가까이 있을 때 볼륨이 늘어납니다.</span><span class="sxs-lookup"><span data-stu-id="c6257-112">For example, as the user gets closer to an object or the object gets closer to them, the volume increases.</span></span> <span data-ttu-id="c6257-113">마찬가지로 개체가 사용자를 중심으로 이동 하거나 그 반대의 경우에도 공간 소리는 소리를 개체에서 직접 가져오는 것에 대 한 효과를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6257-113">Similarly, as objects move around a user, or vice versa, spatial sounds give the illusion that sounds are coming directly from the object.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/PTPvx7mDon4]

## <a name="device-support"></a><span data-ttu-id="c6257-114">장치 지원</span><span class="sxs-lookup"><span data-stu-id="c6257-114">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c6257-115"><strong>기능</strong></span><span class="sxs-lookup"><span data-stu-id="c6257-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="c6257-116"><a href="hololens-hardware-details.md"><strong>HoloLens(1세대)</strong></a></span><span class="sxs-lookup"><span data-stu-id="c6257-116"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="c6257-117"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="c6257-117"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="c6257-118"><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="c6257-118"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c6257-119">공간 음향</span><span class="sxs-lookup"><span data-stu-id="c6257-119">Spatial sound</span></span></td>
        <td><span data-ttu-id="c6257-120">✔️</span><span class="sxs-lookup"><span data-stu-id="c6257-120">✔️</span></span></td>
        <td><span data-ttu-id="c6257-121">✔️</span><span class="sxs-lookup"><span data-stu-id="c6257-121">✔️</span></span></td>
        <td><span data-ttu-id="c6257-122">✔️ (헤드폰 사용)</span><span class="sxs-lookup"><span data-stu-id="c6257-122">✔️ (with headphones)</span></span></td>
    </tr>
</table>

## <a name="simulating-the-perceived-location-and-distance-of-sounds"></a><span data-ttu-id="c6257-123">인식 되는 위치 및 소리 거리 시뮬레이션</span><span class="sxs-lookup"><span data-stu-id="c6257-123">Simulating the perceived location and distance of sounds</span></span>

<span data-ttu-id="c6257-124">사운드가 귀에 도달 하는 방식을 분석 하 여이를 통해 소리를 내보내는 개체의 거리와 방향을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6257-124">By analyzing how sound reaches both our ears, our brain determines the distance and direction of the object emitting the sound.</span></span> <span data-ttu-id="c6257-125">HRTF (또는 Head 관련 전송 함수)는 귀가 특정 시점에서 소리를 받는 방법에 대 한 spectral 응답을 모델링 하 여이 상호 작용을 시뮬레이션 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6257-125">An HRTF (or Head Related Transfer Function) simulates this interaction by modeling the spectral response that characterizes how an ear receives sound from a point in space.</span></span> <span data-ttu-id="c6257-126">공간 오디오 엔진은 개인 설정 된 HRTFs를 사용 하 여 혼합 현실 경험을 확장 하 고 다양 한 방향 및 거리에서 발생 하는 소리를 시뮬레이션 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6257-126">The spatial audio engine uses personalized HRTFs to expand the mixed reality experience, and simulate sounds that are coming from various directions and distances.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/aB3TDjYklmo]

<span data-ttu-id="c6257-127">Azimuth (왼쪽 또는 오른쪽 오디오) 큐는 각 귀에서 소리가 도착할 때의 차이에서 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6257-127">Left or right audio (azimuth) cues originate from differences in the time sound arrives at each ear.</span></span> <span data-ttu-id="c6257-128">위쪽 및 아래쪽 큐는 외부 귀 모양 (pinnae)에서 생성 된 spectral 변경 내용에서 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6257-128">Up and down cues originate from spectral changes produced by the outer ear shape (pinnae).</span></span> <span data-ttu-id="c6257-129">오디오가 어디에서 오는지를 지정 하 여 시스템은 서로 다른 시간에 도착 하는 소리의 경험을 시뮬레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6257-129">By designating where audio is coming from, the system can simulate the experience of sound arriving at different times to our ears.</span></span> <span data-ttu-id="c6257-130">HoloLens에서 azimuth spatialization는 개인 설정 되어 있지만 권한 상승 시뮬레이션은 평균 anthropometrics 집합을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6257-130">Note that on HoloLens, while azimuth spatialization is personalized, the simulation of elevation is based on an average set of anthropometrics.</span></span> <span data-ttu-id="c6257-131">따라서 상승 정확성은 azimuth 정확도 보다 정확도가 떨어질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6257-131">Thus, elevation accuracy may be less accurate than azimuth accuracy.</span></span>

<span data-ttu-id="c6257-132">또한 소리의 특징은 존재 하는 환경에 따라 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c6257-132">The characteristics of sounds also change based on the environment in which they exist.</span></span> <span data-ttu-id="c6257-133">예를 들어, 동굴의 shouting는 음성이 벽, 층 및 최대값이에 바운스 하 여 에코 효과를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6257-133">For instance, shouting in a cave will cause your voice to bounce off the walls, floors, and ceilings, creating an echo effect.</span></span> <span data-ttu-id="c6257-134">공간 사운드의 방 모델 설정은 이러한 반사를 재현 특정 오디오 환경에 소리를 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="c6257-134">The room model setting of spatial sound reproduces these reflections to place sounds in a particular audio environment.</span></span> <span data-ttu-id="c6257-135">이 설정을 사용 하 여 더 몰입 형 오디오 환경을 만들기 위해 해당 공간에서 소리를 시뮬레이션 하는 사용자의 실제 위치를 일치 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6257-135">You can use this setting to match the user's actual location for simulation of sounds in that space to create a more immersive audio experience.</span></span>

## <a name="integrating-spatial-sound"></a><span data-ttu-id="c6257-136">공간 사운드 통합</span><span class="sxs-lookup"><span data-stu-id="c6257-136">Integrating spatial sound</span></span>

<span data-ttu-id="c6257-137">혼합 현실의 일반적인 원칙은 사용자의 물리적 환경 또는 가상 환경에서 [holograms](hologram.md) 하는 것입니다. holograms에서 발생 하는 대부분의 소리는 spatialized 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6257-137">Because the general principle of mixed reality is to ground [holograms](hologram.md) in the user's physical world or virtual environment, most sounds from holograms should be spatialized.</span></span> <span data-ttu-id="c6257-138">HoloLens에는 자연스럽 게 CPU 및 메모리 예산 고려 사항이 있지만 CPU의 12% 미만 (4 코어 중 하나를 ~ 70% 미만)을 사용 하는 동안 10-12 공간 사운드 음성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6257-138">On HoloLens, there are naturally CPU and memory budget considerations, but you can use 10-12 spatial sound voices there while using less than ~12% of the CPU (~70% of one of the four cores).</span></span> <span data-ttu-id="c6257-139">공간 음향 음성에 권장 되는 용도는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c6257-139">Recommended use for spatial sound voices include:</span></span>
* <span data-ttu-id="c6257-140">(개체 강조 표시, 특히 뷰를 벗어난 경우)를 응시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6257-140">Gaze Mixing (highlighting objects, particularly when out of view).</span></span> <span data-ttu-id="c6257-141">홀로그램에 사용자의 주의가 필요한 경우 해당 홀로그램에서 소리를 재생 합니다 (예: 가상 dog 짖).</span><span class="sxs-lookup"><span data-stu-id="c6257-141">When a hologram needs a user's attention, play a sound on that hologram (e.g. have a virtual dog bark).</span></span> <span data-ttu-id="c6257-142">이렇게 하면 사용자가 홀로그램을 볼 수 없을 때 해당 홀로그램을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6257-142">This helps the user to find the hologram when it is not in view.</span></span>
* <span data-ttu-id="c6257-143">Audio Haptics (touchless 상호 작용을 위한 반응 오디오).</span><span class="sxs-lookup"><span data-stu-id="c6257-143">Audio Haptics (reactive audio for touchless interactions).</span></span> <span data-ttu-id="c6257-144">예를 들어 사용자의 손 또는 이동 컨트롤러가 제스처 프레임을 들어가거나 종료할 때 소리를 재생 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6257-144">For example, play a sound when the user's hand or motion controller enters and exits the gesture frame.</span></span> <span data-ttu-id="c6257-145">또는 사용자가 홀로그램을 선택할 때 소리를 재생 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6257-145">Or play a sound when the user selects a hologram.</span></span>
* <span data-ttu-id="c6257-146">집중 교육 (사용자 주변 주변 소리).</span><span class="sxs-lookup"><span data-stu-id="c6257-146">Immersion (ambient sounds surrounding the user).</span></span>

<span data-ttu-id="c6257-147">또한 공간 사운드를 사용 하 여 표준 스테레오 소리를 혼합 하는 것이 실제적인 환경을 만드는 데 효과적일 수 있는 반면, 반사 ()와 같이 공간 소리의 미묘한 측면을 위해 공간을 확보 하려면 스테레오 사운드를 distance)를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c6257-147">It is also important to note that while blending standard stereo sounds with spatial sound can be effective in creating realistic environments, the stereo sounds should be relatively quiet to leave room for the subtle aspects of spatial sound, such as reflections (distance cues) that can be difficult to hear in a noisy environment.</span></span>

<span data-ttu-id="c6257-148">Windows의 공간 사운드 엔진은 재생에 대해 48k 샘플 비율도 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="c6257-148">Windows' spatial sound engine only supports a 48k sample rate for playback.</span></span> <span data-ttu-id="c6257-149">Unity와 같은 대부분의 미들웨어는 소리 파일을 지원 되는 형식으로 자동으로 변환 하지만 Windows 오디오 Api를 직접 사용 하는 경우 콘텐츠 형식을 효과에서 지 원하는 형식과 일치 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="c6257-149">Most middleware, such as Unity, will automatically convert sound files into the supported format, but when using Windows Audio APIs directly please match the format of the content to the format supported by the effect.</span></span>

## <a name="see-also"></a><span data-ttu-id="c6257-150">참조</span><span class="sxs-lookup"><span data-stu-id="c6257-150">See also</span></span>
* [<span data-ttu-id="c6257-151">MR 공간 220</span><span class="sxs-lookup"><span data-stu-id="c6257-151">MR Spatial 220</span></span>](holograms-220.md)
* [<span data-ttu-id="c6257-152">Unity의 공간 음향</span><span class="sxs-lookup"><span data-stu-id="c6257-152">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
* [<span data-ttu-id="c6257-153">DirectX의 공간 음향</span><span class="sxs-lookup"><span data-stu-id="c6257-153">Spatial sound in DirectX</span></span>](spatial-sound-in-directx.md)
* [<span data-ttu-id="c6257-154">공간 음향 디자인</span><span class="sxs-lookup"><span data-stu-id="c6257-154">Spatial sound design</span></span>](spatial-sound-design.md)
