---
title: 공간 음향 디자인
description: 공간 사운드는 혼합 현실 응용 프로그램에서 집중 교육, 접근성 및 UX 디자인을 위한 강력한 도구입니다.
author: joekellyms
ms.author: joekelly
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 공간 소리, 디자인, 스타일
ms.openlocfilehash: c758037300392d9365c16933677fb0f026976c2a
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750309"
---
# <a name="spatial-sound-design"></a><span data-ttu-id="45ae5-104">공간 음향 디자인</span><span class="sxs-lookup"><span data-stu-id="45ae5-104">Spatial sound design</span></span>

<span data-ttu-id="45ae5-105">공간 사운드는 혼합 현실 응용 프로그램에서 집중 교육, 접근성 및 UX 디자인을 위한 강력한 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-105">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

<span data-ttu-id="45ae5-106">[Marco](https://en.wikipedia.org/wiki/Marco_Polo_(game))를 재생 한 적이 있거나 전화를 사용 하 여 찾을 수 있는 경우에는 공간 소리의 중요성에 대해 잘 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-106">If you've ever played [Marco Polo](https://en.wikipedia.org/wiki/Marco_Polo_(game)), or had someone call your phone to help you locate it, you are already familiar with the importance of spatial sound.</span></span> <span data-ttu-id="45ae5-107">일상 생활의 소리 큐를 사용 하 여 개체를 찾거나, 사용자의 주의가 필요 하거나, 환경을 보다 잘 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-107">We use sound cues in our daily lives to locate objects, get someone's attention, or get a better understanding of our environment.</span></span> <span data-ttu-id="45ae5-108">응용 프로그램의 사운드가 실제 세계에서와 같이 작동 하는 것 처럼 동작 하기 때문에 가상 세계를 더 많이 설득 하 고 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-108">The more closely your app's sound behaves like it does in the real world, the more convincing and engaging your virtual world will be.</span></span>

<br>

> [!VIDEO https://www.youtube.com/embed/aB3TDjYklmo]

## <a name="device-support"></a><span data-ttu-id="45ae5-109">장치 지원</span><span class="sxs-lookup"><span data-stu-id="45ae5-109">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="45ae5-110"><strong>기능</strong></span><span class="sxs-lookup"><span data-stu-id="45ae5-110"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="45ae5-111"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="45ae5-111"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="45ae5-112"><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="45ae5-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="45ae5-113">공간 음향 디자인</span><span class="sxs-lookup"><span data-stu-id="45ae5-113">Spatial sound design</span></span></td>
        <td><span data-ttu-id="45ae5-114">✔️</span><span class="sxs-lookup"><span data-stu-id="45ae5-114">✔️</span></span></td>
        <td><span data-ttu-id="45ae5-115">✔️</span><span class="sxs-lookup"><span data-stu-id="45ae5-115">✔️</span></span></td>
    </tr>
</table>


## <a name="four-key-things-spatial-sound-does-for-mixed-reality-development"></a><span data-ttu-id="45ae5-116">혼합 현실 개발을 위한 4 가지 주요 작업 공간 소리</span><span class="sxs-lookup"><span data-stu-id="45ae5-116">Four key things spatial sound does for mixed reality development</span></span>

<span data-ttu-id="45ae5-117">기본적으로 소리는 스테레오로 재생 됩니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-117">By default, sounds are played back in stereo.</span></span> <span data-ttu-id="45ae5-118">이는 소리가 공간 위치 없이 재생 됨을 의미 하므로 사용자는 소리의 출처를 알 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-118">This means the sound will play with no spatial position, so the user does not know where the sound came from.</span></span> <span data-ttu-id="45ae5-119">공간 사운드는 혼합 현실 개발을 위한 4 가지 주요 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-119">Spatial sound does four key things for mixed reality development:</span></span>

<span data-ttu-id="45ae5-120">**접지가**</span><span class="sxs-lookup"><span data-stu-id="45ae5-120">**Grounding**</span></span>

<span data-ttu-id="45ae5-121">소리를 사용 하지 않으면 가상 개체를 사용 하는 것이 효과적으로 중단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-121">Without sound, virtual objects effectively cease to exist when we turn our head away from them.</span></span> <span data-ttu-id="45ae5-122">실제 개체와 마찬가지로 이러한 개체를 볼 수 없는 경우에도이 개체를 듣고 어디서 나 찾을 수 있게 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-122">Just like real objects, you want to be able to hear these objects even when you can't see them, and you want to be able to locate them anywhere around you.</span></span> <span data-ttu-id="45ae5-123">가상 개체를 실제 세계와 혼합 하기 위해 시각적으로 접지 해야 하는 것과 마찬가지로 접지 된 통화 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-123">Just as virtual objects need to be grounded visually to blend with your real world, they also need to be grounded audibly.</span></span> <span data-ttu-id="45ae5-124">공간 사운드는 진정한 세계 오디오 환경과 디지털 오디오 환경을 원활 하 게 혼합 합니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-124">Spatial sound seamlessly blends your real world audio environment with the digital audio environment.</span></span>

<span data-ttu-id="45ae5-125">**사용자 주의**</span><span class="sxs-lookup"><span data-stu-id="45ae5-125">**User attention**</span></span>

<span data-ttu-id="45ae5-126">혼합 현실 환경에서는 사용자가 원하는 위치를 가정 하 고 시각적 개체를 시각적으로 표시 하는 것을 예측할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-126">In mixed reality experiences, you can't assume where your user is looking and expect them to see something you place in the world visually.</span></span> <span data-ttu-id="45ae5-127">그러나 소리를 재생 하는 개체가 뒤에 있는 경우에도 사용자가 소리 재생을 항상 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-127">But users can always hear a sound play even when the object playing the sound is behind them.</span></span> <span data-ttu-id="45ae5-128">사람들은 소리로 인 한 주의가 필요 하다 고 생각 하는 데 사용 됩니다. 우리는 우리가 instinctually 개체를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-128">People are used to having their attention drawn by sound - we instinctually look toward an object that we hear around us.</span></span> <span data-ttu-id="45ae5-129">사용자의 응시를 시각적으로 가리키기 위해 화살표를 사용 하는 대신 특정 위치에 전달 하려는 경우 해당 위치에 소리를 배치 하는 것이 매우 자연스럽 고 빠른 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-129">When you want to direct your user's gaze to a particular place, rather than using an arrow to point them visually, placing a sound in that location is a very natural and fast way to guide them.</span></span>

<span data-ttu-id="45ae5-130">**집중 교육**</span><span class="sxs-lookup"><span data-stu-id="45ae5-130">**Immersion**</span></span>

<span data-ttu-id="45ae5-131">개체를 이동 하거나 충돌 하는 경우 일반적으로 자료 간의 상호 작용을 듣습니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-131">When objects move or collide, we usually hear those interactions between materials.</span></span> <span data-ttu-id="45ae5-132">따라서 개체가 실제 세계에서 동일 하 게 작동 하지 않는 경우 볼륨을 사용 하 여 다른 방식으로 동영상을 시청 하는 것과 같은 집중 교육 수준이 손실 됩니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-132">So when your objects don't make the same sound they would in the real world, a level of immersion is lost - like watching a scary movie with the volume all the way down.</span></span> <span data-ttu-id="45ae5-133">실제 세계의 모든 소리는 특정 시점에서 제공 됩니다. 헤드를 켜면 이러한 소리가 들리는 위치에서 변화를 듣고 이러한 방식으로 모든 소리의 위치를 추적할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-133">All sounds in the real world come from a particular point in space - when we turn our heads, we hear the change in where those sounds are coming from relative to our ears, and we can track the location of any sound this way.</span></span> <span data-ttu-id="45ae5-134">Spatialized 소리는 볼 수 있는 것 이상의 "느낌"을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-134">Spatialized sounds make up the "feel" of a place beyond what we can see.</span></span>

<span data-ttu-id="45ae5-135">**상호 작용 디자인**</span><span class="sxs-lookup"><span data-stu-id="45ae5-135">**Interaction design**</span></span>

<span data-ttu-id="45ae5-136">대부분의 일반적인 대화형 환경에서 UI 사운드 효과와 같은 상호 작용 사운드는 표준 mono 또는 스테레오로 재생 됩니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-136">In most traditional interactive experiences, interaction sounds like UI sound effects are played in standard mono or stereo.</span></span> <span data-ttu-id="45ae5-137">그러나 UI를 포함 하 여 혼합 현실의 모든 항목이 3D 공간에 존재 하기 때문에 이러한 개체는 spatialized 소리를 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-137">But because everything in mixed reality exists in 3D space - including the UI - these objects benefit from spatialized sounds.</span></span> <span data-ttu-id="45ae5-138">실제 세계의 단추를 누르면 소리는 해당 단추에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-138">When we press a button in the real world, the sound we hear comes from that button.</span></span> <span data-ttu-id="45ae5-139">상호 작용 사운드를 spatializing 하 여 보다 자연스럽 고 실제적인 사용자 환경을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-139">By spatializing interaction sounds, we again provide a more natural and realistic user experience.</span></span>

## <a name="best-practices-when-using-spatial-sound"></a><span data-ttu-id="45ae5-140">공간 사운드 사용에 대 한 모범 사례</span><span class="sxs-lookup"><span data-stu-id="45ae5-140">Best practices when using spatial sound</span></span>

<span data-ttu-id="45ae5-141">**합성 또는 자연스럽 게 소리나는 소리 보다 실제 소리는 잘 작동 합니다.**</span><span class="sxs-lookup"><span data-stu-id="45ae5-141">**Real sounds work better than synthesized or unnatural sounds**</span></span>

<span data-ttu-id="45ae5-142">사용자에 게 더 친숙 한 것은 소리를 사용 하는 것입니다 .이를 통해 더 많은 실제 느낌을 얻을 수 있으며, 사용자가 환경에서 쉽게 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-142">The more familiar your user is with a type of sound, the more real it will feel, and the more easily they will be able to locate it in their environment.</span></span> <span data-ttu-id="45ae5-143">예를 들어, 인간 음성은 매우 일반적인 유형의 소리 이며, 사용자는 실내에서 실제 사용자 만큼 빠르게 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-143">A human voice, for example, is a very common type of sound, and your users will locate it just as quickly as a real person in the room talking to them.</span></span>

<span data-ttu-id="45ae5-144">**기대가 시뮬레이션**</span><span class="sxs-lookup"><span data-stu-id="45ae5-144">**Expectation trumps simulation**</span></span>

<span data-ttu-id="45ae5-145">특정 방향에서 나오는 소리를 사용 하는 경우에는 공간 큐에 관계 없이 해당 방향에 주의를 기울여야 합니다. 예를 들어 대부분의 경우에는 미국 위에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-145">If you are used to a sound coming from a particular direction, your attention will be guided in that direction regardless of spatial cues. For example, most of the time that we hear birds, they are above us.</span></span> <span data-ttu-id="45ae5-146">Bird의 소리를 재생 하면 그 아래에 소리를 둔 경우에도 사용자가 조회 될 가능성이 큽니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-146">Playing the sound of a bird will most likely cause your user to look up, even if you place the sound below them.</span></span> <span data-ttu-id="45ae5-147">이는 일반적으로 혼란 스 러 울 수 있으며, 보다 자연 스러운 경험을 위해 이러한 기대와 같은 기대로 작업 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-147">This is usually confusing, and it is recommended that you work with expectations like these rather than going against them for a more natural experience.</span></span>

<span data-ttu-id="45ae5-148">**대부분의 소리는 spatialized 여야 합니다.**</span><span class="sxs-lookup"><span data-stu-id="45ae5-148">**Most sounds should be spatialized**</span></span>

<span data-ttu-id="45ae5-149">위에서 언급 한 바와 같이 혼합 현실의 모든 항목은 3D 공간에 존재 합니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-149">As mentioned above, everything in Mixed Reality exists in 3D space - your sounds should as well.</span></span> <span data-ttu-id="45ae5-150">특히 메뉴 또는 다른 UI에 연결 된 경우에도 음악이 spatialization 이점을 누릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-150">Even music can sometimes benefit from spatialization, particularly when it's tied to a menu or some other UI.</span></span>

<span data-ttu-id="45ae5-151">**보이지 않는 송신기 방지**</span><span class="sxs-lookup"><span data-stu-id="45ae5-151">**Avoid invisible emitters**</span></span>

<span data-ttu-id="45ae5-152">우리는 조건 화 된 소리를 확인 하는 데 도움이 되었기 때문에 시각적으로 존재 하지 않는 소리를 찾는 것은 자연스럽 고 unnerving 경험이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-152">Because we've been conditioned to look at sounds that we hear around us, it can be an unnatural and even unnerving experience to locate a sound that has no visual presence.</span></span> <span data-ttu-id="45ae5-153">실제 세계의 소리는 빈 공간에서 제공 되지 않으므로 사용자의 즉각적인 환경 내에 오디오 덤프가 배치 될 수도 있음을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-153">Sounds in the real world don't come from empty space, so be sure that if an audio emitter is placed within the user's immediate environment that it can also be seen.</span></span>

<span data-ttu-id="45ae5-154">**공간 마스킹 방지**</span><span class="sxs-lookup"><span data-stu-id="45ae5-154">**Avoid spatial masking**</span></span>

<span data-ttu-id="45ae5-155">공간 사운드는 다른 사운드에서 과도 하 게 사용할 수 있는 매우 미묘한 음향 신호에 의존 합니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-155">Spatial sound relies on very subtle acoustic cues that can be overpowered by other sounds.</span></span> <span data-ttu-id="45ae5-156">스테레오 음악이 나 주변 소리를 사용 하는 경우 사용자가 쉽게 찾을 수 있도록 하는 spatialized 소리의 세부 정보를 위한 공간을 확보 하 고 실제 및 자연 스러운 소리를 유지 하기 위해 혼합에서 충분 한 공간을 확보 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-156">If you do have stereo music or ambient sounds, make sure they are low enough in the mix to give room for the details of your spatialized sounds that will allow your users to locate them easily, and keep them sounding realistic and natural.</span></span>

## <a name="general-concepts-to-keep-in-mind-when-using-spatial-sound"></a><span data-ttu-id="45ae5-157">공간 사운드를 사용할 때 유의 해야 하는 일반적인 개념</span><span class="sxs-lookup"><span data-stu-id="45ae5-157">General concepts to keep in mind when using spatial sound</span></span>

<span data-ttu-id="45ae5-158">**공간 사운드는 시뮬레이션입니다.**</span><span class="sxs-lookup"><span data-stu-id="45ae5-158">**Spatial sound is a simulation**</span></span>

<span data-ttu-id="45ae5-159">공간 사운드가 가장 자주 사용 되는 것은 세계의 실제 또는 가상 개체에서 emanating 것 처럼 보입니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-159">The most frequent use of spatial sound is making a sound seem as though it is emanating from a real or virtual object in the world.</span></span> <span data-ttu-id="45ae5-160">따라서 spatialized 소리는 이러한 개체에서 가장 적합 한 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-160">Thus, spatialized sounds may make the most sense coming from such objects.</span></span>

<span data-ttu-id="45ae5-161">공간 사운드의 인식 정확도는 개체의 크기와 사용자의 거리에 따라 차이가 눈에 띄게 될 수 있다는 것을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-161">Note that the perceived accuracy of spatial sound means that a sound shouldn't necessarily emit from the center of an object, as the difference will be noticeable depending on the size of the object and distance from the user.</span></span> <span data-ttu-id="45ae5-162">작은 개체의 경우 개체의 중심점은 일반적으로 충분 합니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-162">With small objects, the center point of the object is usually sufficient.</span></span> <span data-ttu-id="45ae5-163">큰 개체의 경우 소리를 생성 해야 하는 개체 내의 특정 위치에서 소리 송신기 또는 여러 송신기를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-163">For larger objects, you may want a sound emitter or multiple emitters at the specific location within the object that is supposed to be producing the sound.</span></span>

<span data-ttu-id="45ae5-164">**모든 소리 정규화**</span><span class="sxs-lookup"><span data-stu-id="45ae5-164">**Normalize all sounds**</span></span>

<span data-ttu-id="45ae5-165">거리 감쇠는 실제 세계에서와 같이 사용자의 첫 번째 미터 내에서 신속 하 게 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-165">Distance attenuation happens quickly within the first meter from the user, as it does in the real world.</span></span> <span data-ttu-id="45ae5-166">모든 오디오 파일은 물리적으로 정확한 거리 감쇠를 보장 하기 위해 정규화 해야 하며, 몇 미터 떨어진 경우 (해당 하는 경우) 소리가 들릴 수 있는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-166">All audio files should be normalized to ensure physically accurate distance attenuation, and ensure that a sound can be heard when several meters away (when applicable).</span></span> <span data-ttu-id="45ae5-167">공간 오디오 엔진은 특정 거리 (감쇠와 "거리 신호"의 조합 포함)에 있는 것 처럼 소리를 "느낌" 하는 데 필요한 감쇠를 처리 하 고 그 위에 감쇠를 적용 하 여 효과를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-167">The spatial audio engine will handle the attenuation necessary for a sound to "feel" like it's at a certain distance (with a combination of attenuation and "distance cues"), and applying any attenuation on top of that could reduce the effect.</span></span> <span data-ttu-id="45ae5-168">실제 개체를 시뮬레이션 하는 것 외에도 *공간 사운드* 소리의 초기 거리는 오디오의 적절 한 조합에 충분 합니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-168">Outside of simulating a real object, the initial distance decay of *spatial sound* sounds will likely be more than enough for a proper mix of your audio.</span></span>

<span data-ttu-id="45ae5-169">**개체 검색 및 사용자 인터페이스**</span><span class="sxs-lookup"><span data-stu-id="45ae5-169">**Object discovery and user interfaces**</span></span>

<span data-ttu-id="45ae5-170">오디오 신호를 사용 하 여 사용자가 현재 보기를 벗어나 사용자의 관심을 받을 때 소리는 모든 스테레오 사운드와 방향 오디오 큐에서 방해 수 있는 다른 spatialized 사운드를 비롯 하 여 집중 하 고 강조 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-170">When using audio cues to direct the user's attention beyond their current view, the sound should be audible and prominent in the mix, well above any stereo sounds, and any other spatialized sounds which might distract from the directional audio cue.</span></span> <span data-ttu-id="45ae5-171">사용자 인터페이스의 요소 (예: 메뉴)와 연결 된 소리 및 음악의 경우 해당 개체에 소리 송신기를 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-171">For sounds and music that are associated with an element of the user interface (e.g. a menu), the sound emitter should be attached to that object.</span></span> <span data-ttu-id="45ae5-172">스테레오 및 기타 비 위치 오디오 재생을 사용 하면 사용자가 spatialized 요소를 찾기 어려울 수 있습니다 (위 참조). 공간 마스킹을 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="45ae5-172">Stereo and other non-positional audio playing can make spatialized elements difficult for users to locate (See above: Avoid spatial masking).</span></span>

<span data-ttu-id="45ae5-173">**가능한 한 표준 3D 사운드에 대해 공간 소리 사용**</span><span class="sxs-lookup"><span data-stu-id="45ae5-173">**Use spatial sound over standard 3D sound as much as possible**</span></span>

<span data-ttu-id="45ae5-174">혼합 현실에서는 최상의 사용자 환경을 위해 레거시 3D 오디오 기술이 아닌 공간 사운드를 사용 하 여 3D 오디오를 달성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-174">In mixed reality, for the best user experience, 3D audio should be achieved using spatial sound rather than legacy 3D audio technologies.</span></span> <span data-ttu-id="45ae5-175">일반적으로 개선 된 spatialization 표준 3D 사운드 보다 작은 CPU 비용이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-175">In general, the improved spatialization is worth the small CPU cost over standard 3D sound.</span></span> <span data-ttu-id="45ae5-176">표준 3D 오디오는 우선 순위가 낮은 소리에 사용할 수 있지만, spatialized는 실제 또는 가상 개체와 반드시 연결 되는 것은 아니며, 사용자가 앱과 상호 작용 하는 데 필요 하지 않은 개체를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45ae5-176">Standard 3D audio can be used for low-priority sounds, sounds that are spatialized but not necessarily tied to a physical or virtual object, and objects that the user never need locate to interact with the app.</span></span>

## <a name="see-also"></a><span data-ttu-id="45ae5-177">참조</span><span class="sxs-lookup"><span data-stu-id="45ae5-177">See also</span></span>
* [<span data-ttu-id="45ae5-178">공간 음향</span><span class="sxs-lookup"><span data-stu-id="45ae5-178">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="45ae5-179">공간 매핑</span><span class="sxs-lookup"><span data-stu-id="45ae5-179">Spatial mapping</span></span>](spatial-mapping.md)
