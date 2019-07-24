---
title: 홀로그램이란?
description: HoloLens를 사용 하면 전 세계에 표시 되는 조명 및 소리로 이루어진 3 차원 holograms을 보고 상호 작용할 수 있습니다.
author: beaufolsom
ms.author: befolsom
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, holograms, 디자인, 상호 작용
ms.openlocfilehash: 714b08db23aa641252291aebe89fa3059c209a6f
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829785"
---
# <a name="what-is-a-hologram"></a><span data-ttu-id="11eb9-104">홀로그램이란?</span><span class="sxs-lookup"><span data-stu-id="11eb9-104">What is a hologram?</span></span>

<span data-ttu-id="11eb9-105">HoloLens를 사용 하면 실제 개체인 것 처럼 전 세계에 표시 되는 광원 및 소리로 구성 된 **holograms**개체를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-105">HoloLens lets you create **holograms**, objects made of light and sound that appear in the world around you, just as if they were real objects.</span></span> <span data-ttu-id="11eb9-106">Holograms는 [응시](gaze.md), [제스처](gestures.md) 및 [음성 명령](voice-input.md)에 응답 하 고 [실제 서피스와](spatial-mapping.md) 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-106">Holograms respond to your [gaze](gaze.md), [gestures](gestures.md) and [voice commands](voice-input.md), and can interact with [real-world surfaces](spatial-mapping.md) around you.</span></span> <span data-ttu-id="11eb9-107">Holograms를 사용 하면 전 세계의 일부인 디지털 개체를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-107">With holograms, you can create digital objects that are part of your world.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/MVXH5V8MVQo]

## <a name="device-support"></a><span data-ttu-id="11eb9-108">장치 지원</span><span class="sxs-lookup"><span data-stu-id="11eb9-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="11eb9-109"><strong>기능</strong></span><span class="sxs-lookup"><span data-stu-id="11eb9-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="11eb9-110"><a href="hololens-hardware-details.md"><strong>HoloLens(1세대)</strong></a></span><span class="sxs-lookup"><span data-stu-id="11eb9-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="11eb9-111"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="11eb9-111"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="11eb9-112"><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="11eb9-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="11eb9-113">Holograms</span><span class="sxs-lookup"><span data-stu-id="11eb9-113">Holograms</span></span></td>
        <td><span data-ttu-id="11eb9-114">✔️</span><span class="sxs-lookup"><span data-stu-id="11eb9-114">✔️</span></span></td>
        <td><span data-ttu-id="11eb9-115">✔️</span><span class="sxs-lookup"><span data-stu-id="11eb9-115">✔️</span></span></td>
        <td><span data-ttu-id="11eb9-116">❌</span><span class="sxs-lookup"><span data-stu-id="11eb9-116">❌</span></span></td>
    </tr>
</table>

## <a name="a-hologram-is-made-of-light-and-sound"></a><span data-ttu-id="11eb9-117">홀로그램은 가볍고 소리로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-117">A hologram is made of light and sound</span></span>

<span data-ttu-id="11eb9-118">HoloLens [렌더링](rendering.md) 되는 holograms는 사용자의 눈 앞에 있는 holographic 프레임에 직접 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-118">The holograms that HoloLens [renders](rendering.md) appear in the holographic frame directly in front of the user's eyes.</span></span> <span data-ttu-id="11eb9-119">Holograms를 전 세계에 추가 합니다. 즉, 디스플레이의 빛과 주변 광원을 모두 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-119">Holograms add light to your world, which means that you see both the light from the display and the light from your surroundings.</span></span> <span data-ttu-id="11eb9-120">HoloLens는 눈동자에서 조명을 제거 하지 않으므로 holograms 색으로 렌더링 될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-120">HoloLens doesn't remove light from your eyes, so holograms can't be rendered with the color black.</span></span> <span data-ttu-id="11eb9-121">대신 검정색 콘텐츠가 투명 하 게 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-121">Instead, black content appears as transparent.</span></span>

<span data-ttu-id="11eb9-122">Holograms에는 다양 한 모양과 동작이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-122">Holograms can have many different appearances and behaviors.</span></span> <span data-ttu-id="11eb9-123">일부는 현실적인 및 반도체 이며, 다른 일부는 cartoonish 및 ethereal입니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-123">Some are realistic and solid, and others are cartoonish and ethereal.</span></span> <span data-ttu-id="11eb9-124">Holograms는 사용자의 환경에서 기능을 강조 표시할 수 있으며 앱의 사용자 인터페이스에 요소가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-124">Holograms can highlight features in your surroundings, and they can be elements in your app's user interface.</span></span>

![바닥에서 Holographic 강아지](images/fang3-640px.jpg)

<span data-ttu-id="11eb9-126">Holograms는 주변의 특정 장소에서 제공 되는 [소리](spatial-sound.md)를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-126">Holograms can also make [sounds](spatial-sound.md), which will appear to come from a specific place in your surroundings.</span></span> <span data-ttu-id="11eb9-127">HoloLens에서 소리는 소리를 포함 하지 않고 귀 바로 위에 있는 두 개의 스피커에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-127">On HoloLens, sound comes from two speakers that are located directly above your ears, without covering them.</span></span> <span data-ttu-id="11eb9-128">화면에 표시 되는 것과 마찬가지로, 사용자 환경의 소리를 차단 하지 않고 새 소리를 도입 하 여 스피커가 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-128">Similar to the displays, the speakers are additive, introducing new sounds without blocking the sounds from your environment.</span></span>

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a><span data-ttu-id="11eb9-129">홀로그램을 사용자와 함께 전 세계 또는 태그에 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-129">A hologram can be placed in the world or tag along with you</span></span>

<span data-ttu-id="11eb9-130">홀로그램을 원하는 특정 위치가 있으면 전 세계에 정확 하 게 [배치할](coordinate-systems.md) 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-130">When you have a particular location where you want a hologram, you can [place](coordinate-systems.md) it precisely there in the world.</span></span> <span data-ttu-id="11eb9-131">이 홀로그램을 연습 하면서 전 세계에 비해 안정적으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-131">As you walk around that hologram, it will appear stable relative to the world around you.</span></span> <span data-ttu-id="11eb9-132">[공간 앵커](coordinate-systems.md#spatial-anchors) 를 사용 하 여 해당 개체를 전 세계에 고정 하는 경우 시스템은 나중에 다시 돌아올 때 위치를 기억할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-132">If you use a [spatial anchor](coordinate-systems.md#spatial-anchors) to pin that object firmly to the world, the system can even remember where you left it when you come back later.</span></span>

![Holographic 빌딩 maquette on a table](images/image5-640px.png)

<span data-ttu-id="11eb9-134">대신 일부 holograms 사용자를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-134">Some holograms follow the user instead.</span></span> <span data-ttu-id="11eb9-135">이러한 태그를 함께 사용 하면 사용자가 진행 하는 위치에 관계 없이 사용자를 기준으로 holograms을 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-135">These tag-along holograms position themselves relative to the user, no matter where they walk.</span></span> <span data-ttu-id="11eb9-136">한 번의 사용자와 함께 홀로그램을 가져와서 다른 방에 들어온 후 벽에 놓을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-136">You may even choose to bring a hologram with you for a while and then place it on the wall once you get to another room.</span></span>

<span data-ttu-id="11eb9-137">**모범 사례**</span><span class="sxs-lookup"><span data-stu-id="11eb9-137">**Best practices**</span></span>
* <span data-ttu-id="11eb9-138">일부 시나리오에서는 holograms가 쉽게 검색 가능 하거나 환경 전체에서 볼 수 있도록 요구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-138">Some scenarios may demand that holograms remain easily discoverable or visible throughout the experience.</span></span> <span data-ttu-id="11eb9-139">이러한 종류의 위치에는 두 가지 상위 수준 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-139">There are two high-level approaches to this kind of positioning.</span></span> <span data-ttu-id="11eb9-140">**"표시-잠김"** 및 **"본문 잠금"** 이라고 하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-140">Let's call them **"display-locked"** and **"body-locked"**.</span></span>
   * <span data-ttu-id="11eb9-141">디스플레이 잠김 콘텐츠는 장치 디스플레이에 "메서드에 액세스할" 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-141">Display-locked content is positionally "locked" to the device display.</span></span> <span data-ttu-id="11eb9-142">이는 많은 사용자 들이 "사용 하지 않도록 설정" 하려는 경우를 비롯 하 여 다양 한 이유 때문에 복잡 합니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-142">This is tricky for a number of reasons, including an unnatural feeling of "clingyness" that makes many users frustrated and wanting to "shake it off."</span></span> <span data-ttu-id="11eb9-143">일반적으로 대부분의 디자이너는 표시 잠금 콘텐츠를 방지 하는 것이 더 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-143">In general, many designers have found it better to avoid display-locking content.</span></span>
   * <span data-ttu-id="11eb9-144">본문에서 잠긴 접근 방식은 훨씬 더 forgivable.</span><span class="sxs-lookup"><span data-stu-id="11eb9-144">The body-locked approach is far more forgivable.</span></span> <span data-ttu-id="11eb9-145">본문 잠금은 홀로그램이 사용자의 body 또는 응시 vector로 테더 링 된 사용자를 중심으로 3d 공간에 배치 되는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-145">Body-locking is when a hologram is tethered to the user's body or gaze vector, but is positioned in 3d space around the user.</span></span> <span data-ttu-id="11eb9-146">대부분의 환경에서는 사용자가 응시를 "팔 로우" 하 여 사용자가 자신의 본문을 회전 하 고 홀로그램을 잃지 않고 공간 간을 이동할 수 있는 본문 잠금 동작을 채택 했습니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-146">Many experiences have adopted a body-locking behavior where the hologram "follows" the users gaze, which allows the user to rotate their body and move through space without losing the hologram.</span></span> <span data-ttu-id="11eb9-147">지연 시간을 통합 하면 홀로그램 이동이 보다 자연스럽 게 느껴질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-147">Incorporating a delay helps the hologram movement feel more natural.</span></span> <span data-ttu-id="11eb9-148">예를 들어, Windows Holographic OS의 일부 핵심 UI는 사용자가 헤드를 끄는 동안 gentle, 탄력적 같은 지연 시간을 사용 하 여 사용자의 응시를 따르는 본문 잠금 변형을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-148">For example, some core UI of the Windows Holographic OS uses a variation on body-locking that follows the user's gaze with a gentle, elastic-like delay while the user turns their head.</span></span>
* <span data-ttu-id="11eb9-149">일반적으로 헤드에서 약 1-2 미터 떨어진 편안 하 게 볼 때 홀로그램을 준비 합니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-149">Place the hologram at a comfortable viewing distance typically about 1-2 meters away from the head.</span></span>
* <span data-ttu-id="11eb9-150">Holographic 프레임에서 지속적으로 사용 해야 하는 요소에 대 한 드리프트를 제공 하거나 사용자가 관점을 변경할 때 디스플레이의 한 면에 콘텐츠에 애니메이션 효과를 주는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-150">Provide an amount of drift for elements that must be continually in the holographic frame, or consider animating your content to one side of the display when the user changes their point of view.</span></span>

<span data-ttu-id="11eb9-151">**최적 영역에 holograms 두기-1.25 m과 5m 사이**</span><span class="sxs-lookup"><span data-stu-id="11eb9-151">**Place holograms in the optimal zone - between 1.25m and 5m**</span></span>

<span data-ttu-id="11eb9-152">두 미터는 가장 최적 이며, 1 미터에서 더 가까운 수준으로 이동 하는 것이 저하 됩니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-152">Two meters is the most optimal, and the experience will degrade the closer you get from one meter.</span></span> <span data-ttu-id="11eb9-153">한 미터 보다 가까운 거리에서 holograms 정기적으로 이동 하는 것은 고정 holograms 보다 문제가 될 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-153">At distances nearer than one meter, holograms that regularly move in depth are more likely to be problematic than stationary holograms.</span></span> <span data-ttu-id="11eb9-154">사용자를 예기치 않은 환경으로 확장 하지 않도록 콘텐츠가 너무 가까이 있을 경우 적절 하 게 클리핑 하거나 페이드 아웃 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-154">Consider gracefully clipping or fading out your content when it gets too close so as not to jar the user into an unexpected experience.</span></span>

![사용자의 holograms를 배치 하는 데 가장 적합 한 거리입니다.](images/distanceguiderendering-640px.png)

## <a name="a-hologram-interacts-with-you-and-your-world"></a><span data-ttu-id="11eb9-156">홀로그램은 사용자 및 전 세계와 상호 작용 합니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-156">A hologram interacts with you and your world</span></span>

<span data-ttu-id="11eb9-157">Holograms는 빛과 소리를 위한 것이 아닙니다. 또한 전 세계의 활성 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-157">Holograms aren't only about light and sound; they're also an active part of your world.</span></span> <span data-ttu-id="11eb9-158">홀로그램 및 제스처를 응시 하 고 홀로그램에서 팔 로우를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-158">Gaze at a hologram and gesture with your hand, and a hologram can start to follow you.</span></span> <span data-ttu-id="11eb9-159">홀로그램에 음성 명령을 제공 하 고 회신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-159">Give a voice command to a hologram, and it can reply.</span></span>

![Holographic motorcycle 디자인이 실제 motorcycle 본문에 맞게 조정 되었습니다.](images/image8-640px.png)

<span data-ttu-id="11eb9-161">Holograms 다른 곳에서 가능 하지 않은 개인 상호 작용을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-161">Holograms enable personal interactions that aren't possible elsewhere.</span></span> <span data-ttu-id="11eb9-162">HoloLens에서 세계의 위치를 알 수 있기 때문에 holographic 문자는 대화방을 탐색할 때 눈에 직접 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-162">Because the HoloLens knows where it is in the world, a holographic character can look you directly in the eyes as you walk around the room.</span></span>

<span data-ttu-id="11eb9-163">홀로그램도 주변과 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-163">A hologram can also interact with your surroundings.</span></span> <span data-ttu-id="11eb9-164">예를 들어 테이블 위에 holographic 바운스 구슬을 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-164">For example, you can place a holographic bouncing ball above a table.</span></span> <span data-ttu-id="11eb9-165">그런 다음 [공중 탭](gestures.md#air-tap)을 사용 하 여 구슬 바운스를 시청 하 고 테이블에 도달할 때 소리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-165">Then, with an [air tap](gestures.md#air-tap), watch the ball bounce and make sound when it hits the table.</span></span>

<span data-ttu-id="11eb9-166">Holograms는 실제 개체에 의해 폐색 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-166">Holograms can also be occluded by real-world objects.</span></span> <span data-ttu-id="11eb9-167">예를 들어, holographic 문자는 외부의 도어를 살펴보고 벽 뒤에 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-167">For example, a holographic character might walk through a door and behind a wall, out of your sight.</span></span>

<span data-ttu-id="11eb9-168">**Holograms와 실제 세계를 통합 하기 위한 팁**</span><span class="sxs-lookup"><span data-stu-id="11eb9-168">**Tips for integrating holograms and the real world**</span></span>
* <span data-ttu-id="11eb9-169">Gravitational 규칙에 맞춰 holograms 더 쉽게 이익은 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-169">Aligning to gravitational rules makes holograms easier to relate to and more believable.</span></span> <span data-ttu-id="11eb9-170">제외 Holographic & dog를 공간에 부동으로 두지 않고 테이블의 vase에 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-170">eg: Place a holographic dog on the ground & a vase on the table rather than have them floating in space.</span></span>
* <span data-ttu-id="11eb9-171">대부분의 디자이너에서는 홀로그램이 앉아 있는 표면에 "네거티브 그림자"를 만들어 holograms를 더욱 believably 통합할 수 있음을 발견 했습니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-171">Many designers have found that they can even more believably integrate holograms by creating a "negative shadow" on the surface that the hologram is sitting on.</span></span> <span data-ttu-id="11eb9-172">홀로그램 주위에서 부드러운 광선을 만든 다음 광선에서 "그림자"를 빼서이를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-172">They do this by creating a soft glow on the ground around the hologram and then subtracting the "shadow" from the glow.</span></span> <span data-ttu-id="11eb9-173">소프트 광선은 실제 세계의 조명 및 환경에서 홀로그램 grounds 그림자를 통합 합니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-173">The soft glow integrates with the light from the real world and the shadow grounds the hologram in the environment.</span></span>

## <a name="a-hologram-is-whatever-you-dream-up"></a><span data-ttu-id="11eb9-174">홀로그램은 어떤 것이 든 관계 없이</span><span class="sxs-lookup"><span data-stu-id="11eb9-174">A hologram is whatever you dream up</span></span>

<span data-ttu-id="11eb9-175">Holographic 개발자는 2D 화면 및 전 세계의 창의적인 기능을 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11eb9-175">As a holographic developer, you have the power to break your creativity out of 2D screens and into the world around you.</span></span> <span data-ttu-id="11eb9-176">빌드 *를* 선택 하세요.</span><span class="sxs-lookup"><span data-stu-id="11eb9-176">What will *you* build?</span></span>

![거실에서 Holographic 허수](images/designoverview.jpg)

## <a name="see-also"></a><span data-ttu-id="11eb9-178">참조</span><span class="sxs-lookup"><span data-stu-id="11eb9-178">See also</span></span>
* [<span data-ttu-id="11eb9-179">공간 음향</span><span class="sxs-lookup"><span data-stu-id="11eb9-179">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="11eb9-180">색, 광원 및 재질</span><span class="sxs-lookup"><span data-stu-id="11eb9-180">Color, light and materials</span></span>](color,-light-and-materials.md)
