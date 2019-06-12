---
title: 홀로그램이란?
description: HoloLens 살펴보고 3 차원 홀로그램 상호 작용할 수 있습니다, 개체의 이루어지고 있습니다 주변에 나타나는 사운드.
author: beaufolsom
ms.author: befolsom
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, 홀로그램, 디자인, 상호 작용
ms.openlocfilehash: 714b08db23aa641252291aebe89fa3059c209a6f
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829785"
---
# <a name="what-is-a-hologram"></a><span data-ttu-id="c5bab-104">홀로그램이란?</span><span class="sxs-lookup"><span data-stu-id="c5bab-104">What is a hologram?</span></span>

<span data-ttu-id="c5bab-105">HoloLens 만들 수 있습니다 **홀로그램**조명의 개체 한 사운드 나타나는, 주변에 실제 개체인 것 처럼 합니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-105">HoloLens lets you create **holograms**, objects made of light and sound that appear in the world around you, just as if they were real objects.</span></span> <span data-ttu-id="c5bab-106">홀로그램 응답할 하 [gaze](gaze.md), [제스처](gestures.md) 하 고 [음성 명령](voice-input.md)와 상호 작용할 수 있습니다 [실제 화면](spatial-mapping.md) 와 관련해 서.</span><span class="sxs-lookup"><span data-stu-id="c5bab-106">Holograms respond to your [gaze](gaze.md), [gestures](gestures.md) and [voice commands](voice-input.md), and can interact with [real-world surfaces](spatial-mapping.md) around you.</span></span> <span data-ttu-id="c5bab-107">홀로그램을 사용 하 여 전 세계의 일부인 디지털 개체를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-107">With holograms, you can create digital objects that are part of your world.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/MVXH5V8MVQo]

## <a name="device-support"></a><span data-ttu-id="c5bab-108">장치 지원</span><span class="sxs-lookup"><span data-stu-id="c5bab-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c5bab-109"><strong>기능</strong></span><span class="sxs-lookup"><span data-stu-id="c5bab-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="c5bab-110"><a href="hololens-hardware-details.md"><strong>HoloLens (첫 번째 범용)</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5bab-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="c5bab-111"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="c5bab-111"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="c5bab-112"><a href="immersive-headset-hardware-details.md"><strong>몰입 형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5bab-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c5bab-113">홀로그램</span><span class="sxs-lookup"><span data-stu-id="c5bab-113">Holograms</span></span></td>
        <td><span data-ttu-id="c5bab-114">✔️</span><span class="sxs-lookup"><span data-stu-id="c5bab-114">✔️</span></span></td>
        <td><span data-ttu-id="c5bab-115">✔️</span><span class="sxs-lookup"><span data-stu-id="c5bab-115">✔️</span></span></td>
        <td><span data-ttu-id="c5bab-116">❌</span><span class="sxs-lookup"><span data-stu-id="c5bab-116">❌</span></span></td>
    </tr>
</table>

## <a name="a-hologram-is-made-of-light-and-sound"></a><span data-ttu-id="c5bab-117">빛과 소리를 홀로그램이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-117">A hologram is made of light and sound</span></span>

<span data-ttu-id="c5bab-118">홀로그램은 HoloLens [렌더링](rendering.md) 사용자의 눈 앞에 직접 holographic 프레임에 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-118">The holograms that HoloLens [renders](rendering.md) appear in the holographic frame directly in front of the user's eyes.</span></span> <span data-ttu-id="c5bab-119">홀로그램 표시에서 밝은 테마와 밝은 환경에서 모두 참조 하는 것을 의미 하는 고객의 세계에 빛을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-119">Holograms add light to your world, which means that you see both the light from the display and the light from your surroundings.</span></span> <span data-ttu-id="c5bab-120">HoloLens는 홀로그램 색을 사용 하 여 black 렌더링 없습니다 있도록 light 자신만에서 제거 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-120">HoloLens doesn't remove light from your eyes, so holograms can't be rendered with the color black.</span></span> <span data-ttu-id="c5bab-121">대신, black 콘텐츠 투명 하 게 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-121">Instead, black content appears as transparent.</span></span>

<span data-ttu-id="c5bab-122">홀로그램 많은 다른 모양 및 동작에 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-122">Holograms can have many different appearances and behaviors.</span></span> <span data-ttu-id="c5bab-123">일부는 현실적이 고 실선, 있고 cartoonish 및 마법의 합니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-123">Some are realistic and solid, and others are cartoonish and ethereal.</span></span> <span data-ttu-id="c5bab-124">홀로그램 환경의 기능을 강조 표시할 수 있습니다 하 고 앱의 사용자 인터페이스의 요소 수입니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-124">Holograms can highlight features in your surroundings, and they can be elements in your app's user interface.</span></span>

![Holographic dog 현장에서 탐색](images/fang3-640px.jpg)

<span data-ttu-id="c5bab-126">홀로그램으로 만들 수도 [소리](spatial-sound.md), 환경에서 특정 위치에서 온 것으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-126">Holograms can also make [sounds](spatial-sound.md), which will appear to come from a specific place in your surroundings.</span></span> <span data-ttu-id="c5bab-127">HoloLens에서 사운드을 가리지 않고에 귀 바로 위에 있는 두 스피커에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-127">On HoloLens, sound comes from two speakers that are located directly above your ears, without covering them.</span></span> <span data-ttu-id="c5bab-128">표시와 마찬가지로, 스피커는 덧셈, 환경에서 소리를 차단 하지 않고 새 소리를 소개 합니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-128">Similar to the displays, the speakers are additive, introducing new sounds without blocking the sounds from your environment.</span></span>

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a><span data-ttu-id="c5bab-129">홀로그램 환경 또는 늘어나면 태그에 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-129">A hologram can be placed in the world or tag along with you</span></span>

<span data-ttu-id="c5bab-130">수를 홀로그램 하려는 특정 위치에 있는 경우 [배치](coordinate-systems.md) 전 세계에서 해당 정확 하 게 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-130">When you have a particular location where you want a hologram, you can [place](coordinate-systems.md) it precisely there in the world.</span></span> <span data-ttu-id="c5bab-131">해당 홀로그램 주위를 탐색할 때와 관련해 서 전 세계를 기준으로 안정적인 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-131">As you walk around that hologram, it will appear stable relative to the world around you.</span></span> <span data-ttu-id="c5bab-132">사용 하는 경우는 [공간 앵커](coordinate-systems.md#spatial-anchors) 세계 견고 하 게 해당 개체를 고정 하려면 시스템도 기억할 수 있는 생략 하면 나중에 다시 방문 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="c5bab-132">If you use a [spatial anchor](coordinate-systems.md#spatial-anchors) to pin that object firmly to the world, the system can even remember where you left it when you come back later.</span></span>

![테이블에 앉아 holographic 빌드 maquette](images/image5-640px.png)

<span data-ttu-id="c5bab-134">일부 홀로그램 사용자를 대신 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-134">Some holograms follow the user instead.</span></span> <span data-ttu-id="c5bab-135">이러한 tag-along 홀로그램 워크 위치에 관계 없이 사용자를 기준으로 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-135">These tag-along holograms position themselves relative to the user, no matter where they walk.</span></span> <span data-ttu-id="c5bab-136">잠시 있습니다를 사용 하 여 홀로그램을 가져오고 다른 대화방에 표시 되 면 벽에 배치도 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-136">You may even choose to bring a hologram with you for a while and then place it on the wall once you get to another room.</span></span>

<span data-ttu-id="c5bab-137">**모범 사례**</span><span class="sxs-lookup"><span data-stu-id="c5bab-137">**Best practices**</span></span>
* <span data-ttu-id="c5bab-138">일부 시나리오 홀로그램 유지 쉽게 검색할 수 또는 환경 전체에서 표시 되도록 요구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-138">Some scenarios may demand that holograms remain easily discoverable or visible throughout the experience.</span></span> <span data-ttu-id="c5bab-139">두 가지 고급 이런 종류의 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-139">There are two high-level approaches to this kind of positioning.</span></span> <span data-ttu-id="c5bab-140">보겠습니다 **"표시 잠긴"** 하 고 **"본문 잠긴"** 합니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-140">Let's call them **"display-locked"** and **"body-locked"**.</span></span>
   * <span data-ttu-id="c5bab-141">콘텐츠 표시 잠긴 되려면 "잠겨 있음"이라는 장치 화면.</span><span class="sxs-lookup"><span data-stu-id="c5bab-141">Display-locked content is positionally "locked" to the device display.</span></span> <span data-ttu-id="c5bab-142">이 여러 가지 이유로는 비 자연 느낌 "clingyness"는 많은 사용자가 불편을 포함 하 고 "흔들 었 합니다." 하려는 대 한 까다로운</span><span class="sxs-lookup"><span data-stu-id="c5bab-142">This is tricky for a number of reasons, including an unnatural feeling of "clingyness" that makes many users frustrated and wanting to "shake it off."</span></span> <span data-ttu-id="c5bab-143">일반적으로 많은 디자이너 발견 콘텐츠 표시 잠기지 않도록 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-143">In general, many designers have found it better to avoid display-locking content.</span></span>
   * <span data-ttu-id="c5bab-144">본문 잠긴 방법은 훨씬 forgivable입니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-144">The body-locked approach is far more forgivable.</span></span> <span data-ttu-id="c5bab-145">본문-잠금은 홀로그램 사용자의 본문 또는 게이즈 벡터 테더 링 된은 사용자 중심 3d 공간에 배치 하는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-145">Body-locking is when a hologram is tethered to the user's body or gaze vector, but is positioned in 3d space around the user.</span></span> <span data-ttu-id="c5bab-146">다양 한 환경을 위치를 홀로그램 "따르는"를 해당 본문 회전 하 고 공간을 홀로그램 손실 없이 이동할 수 있는 사용자 게이즈를 본문 잠금 동작을 채택 했습니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-146">Many experiences have adopted a body-locking behavior where the hologram "follows" the users gaze, which allows the user to rotate their body and move through space without losing the hologram.</span></span> <span data-ttu-id="c5bab-147">지연 통합 홀로그램 이동을 자연스럽 게 느낄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-147">Incorporating a delay helps the hologram movement feel more natural.</span></span> <span data-ttu-id="c5bab-148">예를 들어, 일부 핵심 Windows Holographic 운영 체제의 UI는 사용자가 헤드를 설정 하는 동안 사용자의 게이즈 살짝, 탄력적 같은 지연 시간을 다음에 나오는 본문-잠금에서 변형을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-148">For example, some core UI of the Windows Holographic OS uses a variation on body-locking that follows the user's gaze with a gentle, elastic-like delay while the user turns their head.</span></span>
* <span data-ttu-id="c5bab-149">배치는 홀로그램 편안한 보기 거리에 일반적으로 헤드에서 약 1 ~ 2 미터입니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-149">Place the hologram at a comfortable viewing distance typically about 1-2 meters away from the head.</span></span>
* <span data-ttu-id="c5bab-150">사용자 자신의 관점을 변경할 때 콘텐츠를 표시 한 쪽에 애니메이션을 적용 하는 것이 좋습니다. 하거나 holographic 프레임에서 계속 되어야 하는 요소에 대 한 드리프트의 용량을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-150">Provide an amount of drift for elements that must be continually in the holographic frame, or consider animating your content to one side of the display when the user changes their point of view.</span></span>

<span data-ttu-id="c5bab-151">**홀로그램 최적의 영역-1.25 m 5 분 사이 배치**</span><span class="sxs-lookup"><span data-stu-id="c5bab-151">**Place holograms in the optimal zone - between 1.25m and 5m**</span></span>

<span data-ttu-id="c5bab-152">두 가지 단위가 가장 최적의 이며 1 미터에서 가져올 더 가깝게 환경이 저하 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-152">Two meters is the most optimal, and the experience will degrade the closer you get from one meter.</span></span> <span data-ttu-id="c5bab-153">더 가까이 있을 수록 보다 1 미터 거리 에서도 홀로그램 방어에서 정기적으로 이동 하는 고정 홀로그램 보다 문제가 될 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-153">At distances nearer than one meter, holograms that regularly move in depth are more likely to be problematic than stationary holograms.</span></span> <span data-ttu-id="c5bab-154">정상적으로 클리핑 또는 너무 가깝게를 하지 못하도록 예기치 않은 환경으로 사용자를 jar 가져오면 내용을 페이드아웃 고려 합니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-154">Consider gracefully clipping or fading out your content when it gets too close so as not to jar the user into an unexpected experience.</span></span>

![사용자 로부터 홀로그램 배치에 대 한 최적의 거리입니다.](images/distanceguiderendering-640px.png)

## <a name="a-hologram-interacts-with-you-and-your-world"></a><span data-ttu-id="c5bab-156">하 여 세계와 상호 작용을 홀로그램</span><span class="sxs-lookup"><span data-stu-id="c5bab-156">A hologram interacts with you and your world</span></span>

<span data-ttu-id="c5bab-157">빛 소리;에 대 한 제공 되지 않습니다. 전 세계의 활성 부분 또한 하기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-157">Holograms aren't only about light and sound; they're also an active part of your world.</span></span> <span data-ttu-id="c5bab-158">홀로그램 및 제스처를 손으로 게이즈를 홀로그램을 따르도록 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-158">Gaze at a hologram and gesture with your hand, and a hologram can start to follow you.</span></span> <span data-ttu-id="c5bab-159">홀로그램에 음성 명령을 지정 하 고 응답할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-159">Give a voice command to a hologram, and it can reply.</span></span>

![실제 motorcycle 본문에 맞추는 holographic motorcycle 디자인](images/image8-640px.png)

<span data-ttu-id="c5bab-161">홀로그램 다른 곳에서 가능 하지 않은 개인 상호 작용을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-161">Holograms enable personal interactions that aren't possible elsewhere.</span></span> <span data-ttu-id="c5bab-162">HoloLens 알기 전 세계의 경우, 때문에 holographic 문자를 확인할 수 있습니다 시각에서 직접 전시실 안내 합니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-162">Because the HoloLens knows where it is in the world, a holographic character can look you directly in the eyes as you walk around the room.</span></span>

<span data-ttu-id="c5bab-163">홀로그램 환경 상호 작용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-163">A hologram can also interact with your surroundings.</span></span> <span data-ttu-id="c5bab-164">예를 들어 테이블 위에 holographic 바운스 공을 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-164">For example, you can place a holographic bouncing ball above a table.</span></span> <span data-ttu-id="c5bab-165">그런 다음 프로그램 [어 탭](gestures.md#air-tap), 공 띄우기 고 사운드 테이블에 도달할 때를 시청 하세요.</span><span class="sxs-lookup"><span data-stu-id="c5bab-165">Then, with an [air tap](gestures.md#air-tap), watch the ball bounce and make sound when it hits the table.</span></span>

<span data-ttu-id="c5bab-166">실제 개체에 의해 홀로그램을 폐색 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-166">Holograms can also be occluded by real-world objects.</span></span> <span data-ttu-id="c5bab-167">예를 들어, holographic 문자 수 및 프로그램 sight 부족 벽을 뒤 문을 통해 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-167">For example, a holographic character might walk through a door and behind a wall, out of your sight.</span></span>

<span data-ttu-id="c5bab-168">**홀로그램 및 실제 세계를 통합 하기 위한 팁**</span><span class="sxs-lookup"><span data-stu-id="c5bab-168">**Tips for integrating holograms and the real world**</span></span>
* <span data-ttu-id="c5bab-169">Gravitational 규칙에 맞추어 관련이 하기 쉽고 더 이익은 홀로그램 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-169">Aligning to gravitational rules makes holograms easier to relate to and more believable.</span></span> <span data-ttu-id="c5bab-170">eg: 처음부터 및 테이블에 꽃병 holographic dog 배치할 것 보다는 공간에서 부동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-170">eg: Place a holographic dog on the ground & a vase on the table rather than have them floating in space.</span></span>
* <span data-ttu-id="c5bab-171">대부분의 디자이너 홀로그램을 홀로그램 하나 더 있는데요는 화면에 "음수 그림자"를 만들어 훨씬 더 believably 통합 수를 발견 했습니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-171">Many designers have found that they can even more believably integrate holograms by creating a "negative shadow" on the surface that the hologram is sitting on.</span></span> <span data-ttu-id="c5bab-172">기초는 홀로그램 주위에 소프트 광선을 만들고 다음 광선이에서 "그림자"를 빼서 여이 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-172">They do this by creating a soft glow on the ground around the hologram and then subtracting the "shadow" from the glow.</span></span> <span data-ttu-id="c5bab-173">그림자 환경의 홀로그램 grounds와 소프트 광선 조명이 실제 환경에서 사용 하 여 통합.</span><span class="sxs-lookup"><span data-stu-id="c5bab-173">The soft glow integrates with the light from the real world and the shadow grounds the hologram in the environment.</span></span>

## <a name="a-hologram-is-whatever-you-dream-up"></a><span data-ttu-id="c5bab-174">홀로그램은 가능한 항목</span><span class="sxs-lookup"><span data-stu-id="c5bab-174">A hologram is whatever you dream up</span></span>

<span data-ttu-id="c5bab-175">Holographic 개발자와 관련해 서 전 세계 및 2D 화면에서 창의력을 중단을 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c5bab-175">As a holographic developer, you have the power to break your creativity out of 2D screens and into the world around you.</span></span> <span data-ttu-id="c5bab-176">항목은 *있습니다* 빌드?</span><span class="sxs-lookup"><span data-stu-id="c5bab-176">What will *you* build?</span></span>

![거실 holographic 허수 world](images/designoverview.jpg)

## <a name="see-also"></a><span data-ttu-id="c5bab-178">참조</span><span class="sxs-lookup"><span data-stu-id="c5bab-178">See also</span></span>
* [<span data-ttu-id="c5bab-179">공간 음향</span><span class="sxs-lookup"><span data-stu-id="c5bab-179">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="c5bab-180">색, 광원 및 재질</span><span class="sxs-lookup"><span data-stu-id="c5bab-180">Color, light and materials</span></span>](color,-light-and-materials.md)
