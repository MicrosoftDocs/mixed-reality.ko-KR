---
title: 공간 적절 하 게 디자인
description: 공간 소리는 집중 교육, 내게 필요한 옵션 및 혼합된 현실 응용 프로그램의 UX 디자인에 대 한 강력한 도구입니다.
author: joekellyms
ms.author: joekelly
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality를 공간 소리, 디자인, 스타일
ms.openlocfilehash: c758037300392d9365c16933677fb0f026976c2a
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750309"
---
# <a name="spatial-sound-design"></a><span data-ttu-id="5f20e-104">공간 적절 하 게 디자인</span><span class="sxs-lookup"><span data-stu-id="5f20e-104">Spatial sound design</span></span>

<span data-ttu-id="5f20e-105">공간 소리는 집중 교육, 내게 필요한 옵션 및 혼합된 현실 응용 프로그램의 UX 디자인에 대 한 강력한 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-105">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

<span data-ttu-id="5f20e-106">재생 어느 한 경우 [Marco Polo](https://en.wikipedia.org/wiki/Marco_Polo_(game)), 또는 회원님의 전화로 하는 데 사용자가 찾을, 공간 소리의 중요도 사용 하 여 이미 익숙한 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-106">If you've ever played [Marco Polo](https://en.wikipedia.org/wiki/Marco_Polo_(game)), or had someone call your phone to help you locate it, you are already familiar with the importance of spatial sound.</span></span> <span data-ttu-id="5f20e-107">개체를 찾으려면, 다른 사람의 주목을, 또는 환경을 더 잘 이해할 소리 신호 우리의 일상 생활에서 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-107">We use sound cues in our daily lives to locate objects, get someone's attention, or get a better understanding of our environment.</span></span> <span data-ttu-id="5f20e-108">더 밀접 하 게 앱의 소리 실제, 자세한 유도 및 참여에 가상 세계 됩니다 것 처럼 동작 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-108">The more closely your app's sound behaves like it does in the real world, the more convincing and engaging your virtual world will be.</span></span>

<br>

> [!VIDEO https://www.youtube.com/embed/aB3TDjYklmo]

## <a name="device-support"></a><span data-ttu-id="5f20e-109">장치 지원</span><span class="sxs-lookup"><span data-stu-id="5f20e-109">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="5f20e-110"><strong>기능</strong></span><span class="sxs-lookup"><span data-stu-id="5f20e-110"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="5f20e-111"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="5f20e-111"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="5f20e-112"><a href="immersive-headset-hardware-details.md"><strong>몰입 형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="5f20e-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="5f20e-113">공간 적절 하 게 디자인</span><span class="sxs-lookup"><span data-stu-id="5f20e-113">Spatial sound design</span></span></td>
        <td><span data-ttu-id="5f20e-114">✔️</span><span class="sxs-lookup"><span data-stu-id="5f20e-114">✔️</span></span></td>
        <td><span data-ttu-id="5f20e-115">✔️</span><span class="sxs-lookup"><span data-stu-id="5f20e-115">✔️</span></span></td>
    </tr>
</table>


## <a name="four-key-things-spatial-sound-does-for-mixed-reality-development"></a><span data-ttu-id="5f20e-116">혼합된 현실 개발을 위한 4 가지 공간 소리가 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-116">Four key things spatial sound does for mixed reality development</span></span>

<span data-ttu-id="5f20e-117">기본적으로 소리 스테레오에서 다시 재생 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-117">By default, sounds are played back in stereo.</span></span> <span data-ttu-id="5f20e-118">즉, 소리에서 발생 한 위치를 알지 못합니다 있도록 없는 공간 위치와 소리가 재생 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-118">This means the sound will play with no spatial position, so the user does not know where the sound came from.</span></span> <span data-ttu-id="5f20e-119">소리 공간 혼합된 현실 개발을 위한 네 가지를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-119">Spatial sound does four key things for mixed reality development:</span></span>

<span data-ttu-id="5f20e-120">**토대가**</span><span class="sxs-lookup"><span data-stu-id="5f20e-120">**Grounding**</span></span>

<span data-ttu-id="5f20e-121">소리를 하지 않고 가상 개체 효과적으로 없으면 소멸 하에서 우리의 헤드를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-121">Without sound, virtual objects effectively cease to exist when we turn our head away from them.</span></span> <span data-ttu-id="5f20e-122">실제 개체와 마찬가지로, 볼 수 없는 하 고 아무 곳 이나와 관련해 서 찾을 수 있게 되기를 원하는 경우에 이러한 개체 들을 수 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-122">Just like real objects, you want to be able to hear these objects even when you can't see them, and you want to be able to locate them anywhere around you.</span></span> <span data-ttu-id="5f20e-123">가상 개체를 실제 사용자를 사용 하 여 blend를 시각적으로 적응할 수 해야 하는 것 처럼 또한 음성으로 적응할 수 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-123">Just as virtual objects need to be grounded visually to blend with your real world, they also need to be grounded audibly.</span></span> <span data-ttu-id="5f20e-124">소리 공간을 원활 하 게 디지털 오디오 환경 사용 하 여 실제 오디오 환경을 혼합합니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-124">Spatial sound seamlessly blends your real world audio environment with the digital audio environment.</span></span>

<span data-ttu-id="5f20e-125">**사용자 주의**</span><span class="sxs-lookup"><span data-stu-id="5f20e-125">**User attention**</span></span>

<span data-ttu-id="5f20e-126">혼합된 현실 환경에서 사용자가 검색 하는 것으로 가정 없으며 예상 대로 표시 시각적으로 전 세계에 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-126">In mixed reality experiences, you can't assume where your user is looking and expect them to see something you place in the world visually.</span></span> <span data-ttu-id="5f20e-127">하지만 사용자 소리 재생 된 경우에 뒤 재생할 소리를 듣고 항상 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-127">But users can always hear a sound play even when the object playing the sound is behind them.</span></span> <span data-ttu-id="5f20e-128">사용자 지정 하 되는 소리-그린 주의가 instinctually 살펴봅니다 우리 주변 제기 하는 개체를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-128">People are used to having their attention drawn by sound - we instinctually look toward an object that we hear around us.</span></span> <span data-ttu-id="5f20e-129">위치는 매우 자연스럽 고 빠른 방법 안내는 소리를 배치 화살표를 사용 하 여 시각적으로 가리키도록 하는 것이 아니라 특정 위치에 사용자의 게이즈를 직접 하려는 경우.</span><span class="sxs-lookup"><span data-stu-id="5f20e-129">When you want to direct your user's gaze to a particular place, rather than using an arrow to point them visually, placing a sound in that location is a very natural and fast way to guide them.</span></span>

<span data-ttu-id="5f20e-130">**Immersion**</span><span class="sxs-lookup"><span data-stu-id="5f20e-130">**Immersion**</span></span>

<span data-ttu-id="5f20e-131">개체를 이동 하거나 충돌 하는 경우 했습니다 듣는 자료 간의 이러한 상호 작용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-131">When objects move or collide, we usually hear those interactions between materials.</span></span> <span data-ttu-id="5f20e-132">따라서 개체는 실제 환경에서 것 같은 소리를 지정 하지 않는, 집중 교육 수준의-아래쪽으로 볼륨을 사용 하 여 scary 동영상을 시청와 같은 손실 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-132">So when your objects don't make the same sound they would in the real world, a level of immersion is lost - like watching a scary movie with the volume all the way down.</span></span> <span data-ttu-id="5f20e-133">실제 환경에서 모든 소리 머리 설정, 우리의 귀를 기준으로 해당 소리에서 들어온 위치 변경 들이 및 소리 위치의 이러한 방식으로 추적할 수 있습니다 때 공간-특정 지점에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-133">All sounds in the real world come from a particular point in space - when we turn our heads, we hear the change in where those sounds are coming from relative to our ears, and we can track the location of any sound this way.</span></span> <span data-ttu-id="5f20e-134">Spatialized 소리 보면 어떤 외의 "느낌"을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-134">Spatialized sounds make up the "feel" of a place beyond what we can see.</span></span>

<span data-ttu-id="5f20e-135">**상호 작용 디자인**</span><span class="sxs-lookup"><span data-stu-id="5f20e-135">**Interaction design**</span></span>

<span data-ttu-id="5f20e-136">대부분의 기존 대화형 환경에서 표준 mono 또는 스테레오 UI 소리 효과 같은 상호 작용 소리가 재생 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-136">In most traditional interactive experiences, interaction sounds like UI sound effects are played in standard mono or stereo.</span></span> <span data-ttu-id="5f20e-137">하지만 이러한 개체 spatialized 소리 활용할 혼합된 현실에서 모든 UI--를 포함 하 여 3D 공간에 존재 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-137">But because everything in mixed reality exists in 3D space - including the UI - these objects benefit from spatialized sounds.</span></span> <span data-ttu-id="5f20e-138">에서는 실제 단추를 누르면 듣는 사운드 단추에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-138">When we press a button in the real world, the sound we hear comes from that button.</span></span> <span data-ttu-id="5f20e-139">상호 작용 소리 spatializing에 의해 다시 더 자연스럽 고 현실적인 사용자 경험을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-139">By spatializing interaction sounds, we again provide a more natural and realistic user experience.</span></span>

## <a name="best-practices-when-using-spatial-sound"></a><span data-ttu-id="5f20e-140">공간 소리를 사용 하는 경우 모범 사례</span><span class="sxs-lookup"><span data-stu-id="5f20e-140">Best practices when using spatial sound</span></span>

<span data-ttu-id="5f20e-141">**합성 된 또는 비 자연 소리 보다 우수 실제 소리 작업**</span><span class="sxs-lookup"><span data-stu-id="5f20e-141">**Real sounds work better than synthesized or unnatural sounds**</span></span>

<span data-ttu-id="5f20e-142">소리를 경험할 더 많은 실제 형식과 더 친숙 한 사용자는를 더 쉽게 더 수 해당 환경에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-142">The more familiar your user is with a type of sound, the more real it will feel, and the more easily they will be able to locate it in their environment.</span></span> <span data-ttu-id="5f20e-143">예를 들어는 인간의 음성 소리의 매우 일반적인 형식이 며와 연락 대화방에 사용자가 해당 실제 사용자를 빠르게 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-143">A human voice, for example, is a very common type of sound, and your users will locate it just as quickly as a real person in the room talking to them.</span></span>

<span data-ttu-id="5f20e-144">**예상이 보다 시뮬레이션을**</span><span class="sxs-lookup"><span data-stu-id="5f20e-144">**Expectation trumps simulation**</span></span>

<span data-ttu-id="5f20e-145">특정 방향에서 들어오는 소리를 사용 하는 경우 공간 신호에 관계 없이 해당 방향에 주의가 안내 합니다. 예를 들어 대부분의 경우 새 이야기할 우리 위에 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-145">If you are used to a sound coming from a particular direction, your attention will be guided in that direction regardless of spatial cues. For example, most of the time that we hear birds, they are above us.</span></span> <span data-ttu-id="5f20e-146">Bird의 소리 재생 중단 될 가능성이 조회할 사용자 아래에 소리를 배치 하는 경우에 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-146">Playing the sound of a bird will most likely cause your user to look up, even if you place the sound below them.</span></span> <span data-ttu-id="5f20e-147">이 일반적으로 혼동 하 고 작업에 대해 좀 더 자연 스러운 환경을 이동 하지 않고 이러한 같은 기대 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-147">This is usually confusing, and it is recommended that you work with expectations like these rather than going against them for a more natural experience.</span></span>

<span data-ttu-id="5f20e-148">**대부분의 소리를 spatialized 해야**</span><span class="sxs-lookup"><span data-stu-id="5f20e-148">**Most sounds should be spatialized**</span></span>

<span data-ttu-id="5f20e-149">위에서 설명 했 듯이 3D 공간에 존재 하는 혼합 현실에서 모든-소리도 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-149">As mentioned above, everything in Mixed Reality exists in 3D space - your sounds should as well.</span></span> <span data-ttu-id="5f20e-150">메뉴 또는 일부 다른 UI에 연결 됩니다 하는 경우에 특히 공간화에서 음악과 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-150">Even music can sometimes benefit from spatialization, particularly when it's tied to a menu or some other UI.</span></span>

<span data-ttu-id="5f20e-151">**보이지 않는 미터를 방지 합니다.**</span><span class="sxs-lookup"><span data-stu-id="5f20e-151">**Avoid invisible emitters**</span></span>

<span data-ttu-id="5f20e-152">우리 주변 받는 소리를 살펴볼 조건 되었습니다 했습니다, 때문에 시각적 표시 되지 않습니다는 사운드를 찾으려고 하는 비 자연도 unnerving 환경을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-152">Because we've been conditioned to look at sounds that we hear around us, it can be an unnatural and even unnerving experience to locate a sound that has no visual presence.</span></span> <span data-ttu-id="5f20e-153">실제 세계의 빈 공간에서 제공 되지, 따라서 해야 하는 경우 오디오 송신기도 볼 수 있습니다 하는 즉시 사용자 환경 내에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-153">Sounds in the real world don't come from empty space, so be sure that if an audio emitter is placed within the user's immediate environment that it can also be seen.</span></span>

<span data-ttu-id="5f20e-154">**공간 마스킹 방지**</span><span class="sxs-lookup"><span data-stu-id="5f20e-154">**Avoid spatial masking**</span></span>

<span data-ttu-id="5f20e-155">소리 공간 다른 소리가 overpowered 수는 매우 미묘 음향 신호에 의존 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-155">Spatial sound relies on very subtle acoustic cues that can be overpowered by other sounds.</span></span> <span data-ttu-id="5f20e-156">있는 경우 스테레오 음악 또는 앰비언트 소리를 쉽게 찾을 수 있도록 하 고 유지 깜박거리는 현실적이 고 자연 스러운 spatialized 소리의 세부 정보에 대 한 공간이 있도록 조합에 만큼 충분히 낮은 지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-156">If you do have stereo music or ambient sounds, make sure they are low enough in the mix to give room for the details of your spatialized sounds that will allow your users to locate them easily, and keep them sounding realistic and natural.</span></span>

## <a name="general-concepts-to-keep-in-mind-when-using-spatial-sound"></a><span data-ttu-id="5f20e-157">공간 소리를 사용할 때 염두에 일반 개념</span><span class="sxs-lookup"><span data-stu-id="5f20e-157">General concepts to keep in mind when using spatial sound</span></span>

<span data-ttu-id="5f20e-158">**소리 공간을 시뮬레이션 하는**</span><span class="sxs-lookup"><span data-stu-id="5f20e-158">**Spatial sound is a simulation**</span></span>

<span data-ttu-id="5f20e-159">소리 공간 가장 자주 사용 하는 소리 전 세계의 실제 또는 가상 개체에서 페이지는 처럼 보일 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-159">The most frequent use of spatial sound is making a sound seem as though it is emanating from a real or virtual object in the world.</span></span> <span data-ttu-id="5f20e-160">따라서 spatialized 소리에 가장 적합 한 이러한 개체에서 오는 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-160">Thus, spatialized sounds may make the most sense coming from such objects.</span></span>

<span data-ttu-id="5f20e-161">참고 소리와 차이 개체의 가운데에서 내보내는 반드시 않아야 공간 사운드 의미의 인식된 정확도 개체 및 사용자 로부터의 거리의 크기에 따라 눈에 띄는 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-161">Note that the perceived accuracy of spatial sound means that a sound shouldn't necessarily emit from the center of an object, as the difference will be noticeable depending on the size of the object and distance from the user.</span></span> <span data-ttu-id="5f20e-162">작은 개체를 사용 하 여 개체의 중심점으로 충분 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-162">With small objects, the center point of the object is usually sufficient.</span></span> <span data-ttu-id="5f20e-163">큰 개체에 대 한 사운드 내보내기 또는 소리 생성 되어야 하는 개체 내에서 특정 위치에서 여러 송신기 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-163">For larger objects, you may want a sound emitter or multiple emitters at the specific location within the object that is supposed to be producing the sound.</span></span>

<span data-ttu-id="5f20e-164">**모든 소리를 정규화 합니다.**</span><span class="sxs-lookup"><span data-stu-id="5f20e-164">**Normalize all sounds**</span></span>

<span data-ttu-id="5f20e-165">거리 감쇠 실제 환경에서와 마찬가지로 사용자의 첫 번째 미터 내에서 신속 하 게 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-165">Distance attenuation happens quickly within the first meter from the user, as it does in the real world.</span></span> <span data-ttu-id="5f20e-166">물리적으로 정확 하 게 거리 감쇠를 확인 하 고 소리를 낼 수 있는지 확인 하려면 모든 오디오 파일을 정규화 해야 경우 여러 미터 떨어진 (있는 경우).</span><span class="sxs-lookup"><span data-stu-id="5f20e-166">All audio files should be normalized to ensure physically accurate distance attenuation, and ensure that a sound can be heard when several meters away (when applicable).</span></span> <span data-ttu-id="5f20e-167">공간 오디오 엔진 소리 "생각" (의 조합으로 감쇠 및 "거리 신호"), 특정 거리 이며 그 위에 효과 줄일 수 있는 감쇠를 적용 하는 데 필요한 감쇠를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-167">The spatial audio engine will handle the attenuation necessary for a sound to "feel" like it's at a certain distance (with a combination of attenuation and "distance cues"), and applying any attenuation on top of that could reduce the effect.</span></span> <span data-ttu-id="5f20e-168">실제 개체를 시뮬레이션 하는 외부에서 초기 거리의 decay *공간 소리* 사운드 오디오의 적절 한에 대 한 충분 한 보다 자세한 조합 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-168">Outside of simulating a real object, the initial distance decay of *spatial sound* sounds will likely be more than enough for a proper mix of your audio.</span></span>

<span data-ttu-id="5f20e-169">**개체 검색 및 사용자 인터페이스**</span><span class="sxs-lookup"><span data-stu-id="5f20e-169">**Object discovery and user interfaces**</span></span>

<span data-ttu-id="5f20e-170">오디오 큐를 사용 하 여 현재 보기를 초과 하 여 사용자의 주의가 직접를 청각적 및 모든 스테레오 소리 및 방향 오디오 신호에서 방해가 될 수 있습니다 하는 다른 spatialized 소리 정점이 조합에 주요 소리 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-170">When using audio cues to direct the user's attention beyond their current view, the sound should be audible and prominent in the mix, well above any stereo sounds, and any other spatialized sounds which might distract from the directional audio cue.</span></span> <span data-ttu-id="5f20e-171">사용자 인터페이스 (예: 메뉴)의 요소와 연관 된 음악와 소리에 대 한 사운드 내보내기 개체에 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-171">For sounds and music that are associated with an element of the user interface (e.g. a menu), the sound emitter should be attached to that object.</span></span> <span data-ttu-id="5f20e-172">스테레오 및 비 위치 다른 오디오 재생 어려울 수 있습니다 spatialized 요소를 찾는 (위의 내용 참조: 방지 공간 마스킹) 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-172">Stereo and other non-positional audio playing can make spatialized elements difficult for users to locate (See above: Avoid spatial masking).</span></span>

<span data-ttu-id="5f20e-173">**공간 소리를 사용 하 여 가능한 한 표준 3D 소리를 통해**</span><span class="sxs-lookup"><span data-stu-id="5f20e-173">**Use spatial sound over standard 3D sound as much as possible**</span></span>

<span data-ttu-id="5f20e-174">혼합된 현실 등 최상의 사용자 환경을 위해 3D 오디오 레거시 3D 오디오 기술 보다는 공간 소리를 사용 하 여 수행할 수 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-174">In mixed reality, for the best user experience, 3D audio should be achieved using spatial sound rather than legacy 3D audio technologies.</span></span> <span data-ttu-id="5f20e-175">일반적으로 향상 된 공간화 가치가 작은 CPU 비용 사운드 표준 3D 위에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-175">In general, the improved spatialization is worth the small CPU cost over standard 3D sound.</span></span> <span data-ttu-id="5f20e-176">표준 3D 오디오 우선 순위가 낮은 소리, spatialized 있지만 실제 또는 가상 개체에 연결 하지 않을 소리 및 사용자 되지 필요를 찾는 앱과 상호 작용 하는 개체에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f20e-176">Standard 3D audio can be used for low-priority sounds, sounds that are spatialized but not necessarily tied to a physical or virtual object, and objects that the user never need locate to interact with the app.</span></span>

## <a name="see-also"></a><span data-ttu-id="5f20e-177">참조</span><span class="sxs-lookup"><span data-stu-id="5f20e-177">See also</span></span>
* [<span data-ttu-id="5f20e-178">공간 음향</span><span class="sxs-lookup"><span data-stu-id="5f20e-178">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="5f20e-179">공간 매핑</span><span class="sxs-lookup"><span data-stu-id="5f20e-179">Spatial mapping</span></span>](spatial-mapping.md)
