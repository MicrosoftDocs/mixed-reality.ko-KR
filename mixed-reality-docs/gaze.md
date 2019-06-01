---
title: 응시
description: 응시 입력의 첫 번째 형태 이며 혼합된 현실 내에서 대상으로 하는 데 필요한 기본 형태의.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 실제로, 게이즈 상호 작용 mixed, 디자인
ms.openlocfilehash: 9e50067f9dfeacf3dce5ea9a928990d1b142e4d0
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453714"
---
# <a name="gaze"></a><span data-ttu-id="d75f4-104">응시</span><span class="sxs-lookup"><span data-stu-id="d75f4-104">Gaze</span></span>

<span data-ttu-id="d75f4-105">**Gaze** 입력의 첫 번째 형태 이며 기본 형식의 혼합된 현실 내에서 대상으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="d75f4-105">**Gaze** is the first form of input and is a primary form of targeting within mixed reality.</span></span> <span data-ttu-id="d75f4-106">응시 여기서 사용자는 전 세계를 찾고 의도 확인할 수 있습니다이 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d75f4-106">Gaze tells you where the user is looking in the world and lets you determine their intent.</span></span> <span data-ttu-id="d75f4-107">실제 환경에서 일반적으로 상호 작용 하려는 개체 찾아 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="d75f4-107">In the real world, you'll typically look at an object that you intend to interact with.</span></span> <span data-ttu-id="d75f4-108">응시와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="d75f4-108">This is the same with gaze.</span></span>

<span data-ttu-id="d75f4-109">혼합된 현실 헤드셋 위치 및 사용자의 헤드의 방향을 사용 하 여 해당 헤드 게이즈 벡터를 결정.</span><span class="sxs-lookup"><span data-stu-id="d75f4-109">Mixed reality headsets use the position and orientation of your user's head to determine their head gaze vector.</span></span> <span data-ttu-id="d75f4-110">사용자의 눈 간에 직접에서 직선 레이저 포인터로이 벡터의 생각할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75f4-110">You can think of this vector as a laser pointer straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="d75f4-111">응용 프로그램 모두 자체 홀로그램와이 광선과 교차할 수 전시실 사용자가에 따라 합니다 [공간 매핑](spatial-mapping.md) 메시 사용자 일 수 있습니다 하는 가상 또는 실제 개체를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75f4-111">As the user looks around the room, your application can intersect this ray, both with its own holograms and with the [spatial mapping](spatial-mapping.md) mesh to determine what virtual or real-world object your user may be looking at.</span></span>

<span data-ttu-id="d75f4-112">HoloLens 2에서 상호 작용 통해 근처 또는 훨씬 상호 작용을 제공할 사용자의 헤드 게이즈를 응시 대상이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75f4-112">On HoloLens 2, interactions can be targeted by either the user's head gaze, eye gaze or through near or far hand interactions.</span></span>
<span data-ttu-id="d75f4-113">HoloLens에 (첫 번째 gen) 해당 사용자의 헤드 게이즈를에서 타기 팅 하기 보다는 동안 렌더링 또는 손 모양 아이콘이 위치에 직접 작용 상호 작용 파생 일반적으로 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d75f4-113">On HoloLens (1st gen), interactions should generally derive their targeting from the user's head gaze, rather than trying to render or interact at the hand's location directly.</span></span> <span data-ttu-id="d75f4-114">손 모양 아이콘이의 상대적 동작 상호 작용을 시작 되 면 컨트롤에 사용할 수 있습니다 합니다 [제스처](gestures.md)와 마찬가지로 합니다 [조작 또는 탐색](gestures.md#composite-gestures) 제스처입니다.</span><span class="sxs-lookup"><span data-stu-id="d75f4-114">Once an interaction has started, relative motions of the hand may be used to control the [gesture](gestures.md), as with the [manipulation or navigation](gestures.md#composite-gestures) gesture.</span></span> <span data-ttu-id="d75f4-115">몰입 형 헤드셋을 사용 하 여 대상을 지정할 수 있습니다 하거나 헤드 게이즈를 사용 하 여 또는 가리키고 가능한 [컨트롤러 동작](motion-controllers.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="d75f4-115">With immersive headsets, you can target using either head gaze or pointing-capable [motion controllers](motion-controllers.md).</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/zCPiZlWdVws]

## <a name="device-support"></a><span data-ttu-id="d75f4-116">장치 지원</span><span class="sxs-lookup"><span data-stu-id="d75f4-116">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="d75f4-117">기능</span><span class="sxs-lookup"><span data-stu-id="d75f4-117">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="d75f4-118"><a href="hololens-hardware-details.md">HoloLens (첫 번째 범용)</a></span><span class="sxs-lookup"><span data-stu-id="d75f4-118"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="d75f4-119">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d75f4-119">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="d75f4-120"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="d75f4-120"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="d75f4-121">헤드 응시</span><span class="sxs-lookup"><span data-stu-id="d75f4-121">Head gaze</span></span></td><td style="text-align: center;"> <span data-ttu-id="d75f4-122">✔️</span><span class="sxs-lookup"><span data-stu-id="d75f4-122">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="d75f4-123">✔️</span><span class="sxs-lookup"><span data-stu-id="d75f4-123">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="d75f4-124">✔️</span><span class="sxs-lookup"><span data-stu-id="d75f4-124">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="d75f4-125">응시</span><span class="sxs-lookup"><span data-stu-id="d75f4-125">Eye gaze</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="d75f4-126">✔️</span><span class="sxs-lookup"><span data-stu-id="d75f4-126">✔️</span></span></td><td></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="d75f4-127">HoloLens 2 관련 된 자세한 지침 [예정](index.md#news-and-notes)합니다.</span><span class="sxs-lookup"><span data-stu-id="d75f4-127">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>


## <a name="uses-of-gaze"></a><span data-ttu-id="d75f4-128">응시 사용</span><span class="sxs-lookup"><span data-stu-id="d75f4-128">Uses of gaze</span></span>

<span data-ttu-id="d75f4-129">혼합된 현실 개발자가 할 수 있는 많은 헤드 또는 눈 게이즈를 사용 하 여:</span><span class="sxs-lookup"><span data-stu-id="d75f4-129">As a mixed reality developer, you can do a lot with head or eye gaze:</span></span>
* <span data-ttu-id="d75f4-130">앱은 사용자의 이목을 위치를 확인 하려면 장면에서 홀로그램으로 응시를 교차 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75f4-130">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is.</span></span>
* <span data-ttu-id="d75f4-131">제스처와 사용자의 게이즈를 사용자가 선택, 활성화, 가져오기, 스크롤 또는 그렇지 않은 경우 해당 홀로그램 상호 작용에 따라 컨트롤러 누름 앱 대상으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75f4-131">Your app can target gestures and controller presses based on the user's gaze, letting the user select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="d75f4-132">앱 사용자 공간 매핑 메시를 사용 하 여 해당 게이즈 광선과 교차 하 여 홀로그램 실제 화면에 배치 하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75f4-132">Your app can let the user place holograms on real-world surfaces, by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="d75f4-133">앱은 사용자가 알 수 *되지* visual 및 오디오 신호 개체 방향으로 변환할 수 있도록 앱을 야기할 수 있는 중요 한 개체의 방향을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d75f4-133">Your app can know when the user is *not* looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

## <a name="cursor"></a><span data-ttu-id="d75f4-134">Cursor</span><span class="sxs-lookup"><span data-stu-id="d75f4-134">Cursor</span></span>

<span data-ttu-id="d75f4-135">헤드 게이즈 대부분의 앱을 사용 해야는 [커서](cursors.md) (또는 다른 시각적 개체/청각 표시)에 사용자의 신뢰를 부여 하려면 아마도 상호 작용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d75f4-135">For head gaze, most apps should use a [cursor](cursors.md) (or other auditory/visual indication) to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="d75f4-136">일반적으로 전 세계를 홀로그램 또는 실제 화면 일 수 있는 개체에 해당 헤드 게이즈 광선 먼저 교차이 커서를 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="d75f4-136">You typically position this cursor in the world where their head gaze ray first intersects an object, which may be a hologram or a real-world surface.</span></span>

<span data-ttu-id="d75f4-137">![게이즈를 표시 하는 예제 visual 커서](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="d75f4-137">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
<span data-ttu-id="d75f4-138">*게이즈를 표시 하는 예제 visual 커서*</span><span class="sxs-lookup"><span data-stu-id="d75f4-138">*An example visual cursor to show gaze*</span></span>

<span data-ttu-id="d75f4-139">응시, 일반적으로 좋습니다 *되지* 에 표시할 커서를 방해 하 고 사용자에 대 한 성가신 신속 하 게 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d75f4-139">For eye gaze, we generally recommend *not* to show a cursor, as this can quickly become distracting and annoying for the user.</span></span> <span data-ttu-id="d75f4-140">대신 약간 visual 대상 강조 표시 하거나 매우 희미 한 눈 모양 커서를 사용 하 여 상호 작용할 수에 대 한 사용자가 하는 방법에 대 한 신뢰도 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d75f4-140">Instead subtly highlight visual targets or use a very faint eye cursor to provide confidence about what the user is about to interact with.</span></span> <span data-ttu-id="d75f4-141">자세한 정보를 확인 하세요 우리의 [눈 기반 입력에 대 한 지침을 디자인](eye-tracking.md) HoloLens 2입니다.</span><span class="sxs-lookup"><span data-stu-id="d75f4-141">For more information, please check out our [design guidance for eye-based input](eye-tracking.md) on HoloLens 2.</span></span>

## <a name="giving-action-to-the-users-gaze"></a><span data-ttu-id="d75f4-142">사용자의 게이즈를 작업을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d75f4-142">Giving action to the user's gaze</span></span>

<span data-ttu-id="d75f4-143">사용자가 홀로그램 또는 해당 게이즈를 사용 하 여 실제 개체를 대상으로 지정 되 면 해당 개체에 대해 작업을 수행 하는 다음 단계가입니다.</span><span class="sxs-lookup"><span data-stu-id="d75f4-143">Once the user has targeted a hologram or real-world object using their gaze, their next step is to take action on that object.</span></span> <span data-ttu-id="d75f4-144">사용자 작업을 수행 하는 주요 수단을 통해 됩니다 [제스처](gestures.md)를 [컨트롤러 동작](motion-controllers.md) 하 고 [음성](voice-input.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="d75f4-144">The primary ways for a user to take action are through [gestures](gestures.md), [motion controllers](motion-controllers.md) and [voice](voice-input.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d75f4-145">참조</span><span class="sxs-lookup"><span data-stu-id="d75f4-145">See also</span></span>
* [<span data-ttu-id="d75f4-146">MR 입력 210: 헤드 응시</span><span class="sxs-lookup"><span data-stu-id="d75f4-146">MR Input 210: Head gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="d75f4-147">DirectX의 헤드 및 눈 응시</span><span class="sxs-lookup"><span data-stu-id="d75f4-147">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="d75f4-148">Unity에서 Head 응시</span><span class="sxs-lookup"><span data-stu-id="d75f4-148">Head gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="d75f4-149">시선 추적 HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d75f4-149">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="d75f4-150">혼합 현실 도구 키트를 사용 하 여 Unity의 응시</span><span class="sxs-lookup"><span data-stu-id="d75f4-150">Eye gaze in Unity using Mixed Reality Toolkit</span></span>](https://aka.ms/mrtk-eyes)
