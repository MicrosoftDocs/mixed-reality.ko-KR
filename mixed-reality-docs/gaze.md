---
title: 응시
description: 응시 입력의 첫 번째 형태 이며 혼합된 현실 내에서 대상으로 하는 데 필요한 기본 형태의.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 혼합된 현실 게이즈, 상호 작용 디자인
ms.openlocfilehash: 738ba9063a5d00f3bbedce989d93076d56ad1a44
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629104"
---
# <a name="gaze"></a><span data-ttu-id="3f6f5-104">응시</span><span class="sxs-lookup"><span data-stu-id="3f6f5-104">Gaze</span></span>

<span data-ttu-id="3f6f5-105">**Gaze** 입력의 첫 번째 형태 이며 기본 형식의 혼합된 현실 내에서 대상으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f6f5-105">**Gaze** is the first form of input and is a primary form of targeting within mixed reality.</span></span> <span data-ttu-id="3f6f5-106">응시 여기서 사용자는 전 세계를 찾고 의도 확인할 수 있습니다이 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3f6f5-106">Gaze tells you where the user is looking in the world and lets you determine their intent.</span></span> <span data-ttu-id="3f6f5-107">실제 환경에서 일반적으로 상호 작용 하려는 개체 찾아 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6f5-107">In the real world, you'll typically look at an object that you intend to interact with.</span></span> <span data-ttu-id="3f6f5-108">응시와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f6f5-108">This is the same with gaze.</span></span>

<span data-ttu-id="3f6f5-109">혼합된 현실 헤드셋 위치 및 사용자의 헤드의 방향을 사용 하 여 해당 헤드 게이즈 벡터를 결정.</span><span class="sxs-lookup"><span data-stu-id="3f6f5-109">Mixed reality headsets use the position and orientation of your user's head to determine their head gaze vector.</span></span> <span data-ttu-id="3f6f5-110">사용자의 눈 간에 직접에서 직선 레이저 포인터로이 벡터의 생각할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6f5-110">You can think of this vector as a laser pointer straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="3f6f5-111">응용 프로그램 모두 자체 홀로그램와이 광선과 교차할 수 전시실 사용자가에 따라 합니다 [공간 매핑](spatial-mapping.md) 메시 사용자 일 수 있습니다 하는 가상 또는 실제 개체를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6f5-111">As the user looks around the room, your application can intersect this ray, both with its own holograms and with the [spatial mapping](spatial-mapping.md) mesh to determine what virtual or real-world object your user may be looking at.</span></span>

<span data-ttu-id="3f6f5-112">HoloLens 2에서 상호 작용 통해 근처 또는 훨씬 상호 작용을 제공할 사용자의 헤드 게이즈 대상이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6f5-112">On HoloLens 2, interactions can be targeted by either the user's head gaze or through near or far hand interactions.</span></span>  <span data-ttu-id="3f6f5-113">HoloLens에 (첫 번째 gen) 해당 사용자의 헤드 게이즈를에서 타기 팅 하기 보다는 동안 렌더링 또는 손 모양 아이콘이 위치에 직접 작용 상호 작용 파생 일반적으로 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f6f5-113">On HoloLens (1st gen), interactions should generally derive their targeting from the user's head gaze, rather than trying to render or interact at the hand's location directly.</span></span> <span data-ttu-id="3f6f5-114">손 모양 아이콘이의 상대적 동작 상호 작용을 시작 되 면 컨트롤에 사용할 수 있습니다 합니다 [제스처](gestures.md)와 마찬가지로 합니다 [조작 또는 탐색](gestures.md#composite-gestures) 제스처입니다.</span><span class="sxs-lookup"><span data-stu-id="3f6f5-114">Once an interaction has started, relative motions of the hand may be used to control the [gesture](gestures.md), as with the [manipulation or navigation](gestures.md#composite-gestures) gesture.</span></span> <span data-ttu-id="3f6f5-115">몰입 형 헤드셋을 사용 하 여 대상을 지정할 수 있습니다 하거나 게이즈를 사용 하 여 또는 가리키고 가능한 [컨트롤러 동작](motion-controllers.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="3f6f5-115">With immersive headsets, you can target using either gaze or pointing-capable [motion controllers](motion-controllers.md).</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/zCPiZlWdVws]

## <a name="device-support"></a><span data-ttu-id="3f6f5-116">장치 지원</span><span class="sxs-lookup"><span data-stu-id="3f6f5-116">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="3f6f5-117">기능</span><span class="sxs-lookup"><span data-stu-id="3f6f5-117">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="3f6f5-118"><a href="hololens-hardware-details.md">HoloLens (첫 번째 범용)</a></span><span class="sxs-lookup"><span data-stu-id="3f6f5-118"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="3f6f5-119">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="3f6f5-119">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="3f6f5-120"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="3f6f5-120"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="3f6f5-121">헤드 응시</span><span class="sxs-lookup"><span data-stu-id="3f6f5-121">Head gaze</span></span></td><td style="text-align: center;"> <span data-ttu-id="3f6f5-122">✔️</span><span class="sxs-lookup"><span data-stu-id="3f6f5-122">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="3f6f5-123">✔️</span><span class="sxs-lookup"><span data-stu-id="3f6f5-123">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="3f6f5-124">✔️</span><span class="sxs-lookup"><span data-stu-id="3f6f5-124">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="3f6f5-125">응시</span><span class="sxs-lookup"><span data-stu-id="3f6f5-125">Eye gaze</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="3f6f5-126">✔️</span><span class="sxs-lookup"><span data-stu-id="3f6f5-126">✔️</span></span></td><td></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="3f6f5-127">HoloLens 2 관련 된 자세한 지침 [예정](index.md#news-and-notes)합니다.</span><span class="sxs-lookup"><span data-stu-id="3f6f5-127">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>


## <a name="uses-of-gaze"></a><span data-ttu-id="3f6f5-128">응시 사용</span><span class="sxs-lookup"><span data-stu-id="3f6f5-128">Uses of gaze</span></span>

<span data-ttu-id="3f6f5-129">혼합된 현실 개발자가 할 수 있는 많은 게이즈를 사용 하 여:</span><span class="sxs-lookup"><span data-stu-id="3f6f5-129">As a mixed reality developer, you can do a lot with gaze:</span></span>
* <span data-ttu-id="3f6f5-130">앱은 사용자의 이목을 위치를 확인 하려면 장면에서 홀로그램으로 응시를 교차 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6f5-130">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is.</span></span>
* <span data-ttu-id="3f6f5-131">제스처와 사용자의 게이즈를 사용자가 선택, 활성화, 가져오기, 스크롤 또는 그렇지 않은 경우 해당 홀로그램 상호 작용에 따라 컨트롤러 누름 앱 대상으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6f5-131">Your app can target gestures and controller presses based on the user's gaze, letting the user select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="3f6f5-132">앱 사용자 공간 매핑 메시를 사용 하 여 해당 게이즈 광선과 교차 하 여 홀로그램 실제 화면에 배치 하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6f5-132">Your app can let the user place holograms on real-world surfaces, by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="3f6f5-133">앱은 사용자가 알 수 *되지* visual 및 오디오 신호 개체 방향으로 변환할 수 있도록 앱을 야기할 수 있는 중요 한 개체의 방향을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f6f5-133">Your app can know when the user is *not* looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

## <a name="cursor"></a><span data-ttu-id="3f6f5-134">Cursor</span><span class="sxs-lookup"><span data-stu-id="3f6f5-134">Cursor</span></span>

<span data-ttu-id="3f6f5-135">대부분의 앱을 사용할지는 [커서](cursors.md) (또는 다른 시각적 개체/청각 표시)에 사용자의 신뢰를 부여 하려면 아마도 상호 작용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f6f5-135">Most apps should use a [cursor](cursors.md) (or other auditory/visual indication) to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="3f6f5-136">일반적으로 전 세계를 홀로그램 또는 실제 화면 일 수 있는 개체에 해당 게이즈 광선 먼저 작용이 커서를 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="3f6f5-136">You typically position this cursor in the world where their gaze ray first interacts an object, which may be a hologram or a real-world surface.</span></span>

<span data-ttu-id="3f6f5-137">![게이즈를 표시 하는 예제 visual 커서](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="3f6f5-137">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
<span data-ttu-id="3f6f5-138">*게이즈를 표시 하는 예제 visual 커서*</span><span class="sxs-lookup"><span data-stu-id="3f6f5-138">*An example visual cursor to show gaze*</span></span>

## <a name="giving-action-to-the-users-gaze"></a><span data-ttu-id="3f6f5-139">사용자의 게이즈를 작업을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3f6f5-139">Giving action to the user's gaze</span></span>

<span data-ttu-id="3f6f5-140">사용자가 홀로그램 또는 해당 게이즈를 사용 하 여 실제 개체를 대상으로 지정 되 면 해당 개체에 대해 작업을 수행 하는 다음 단계가입니다.</span><span class="sxs-lookup"><span data-stu-id="3f6f5-140">Once the user has targeted a hologram or real-world object using their gaze, their next step is to take action on that object.</span></span> <span data-ttu-id="3f6f5-141">사용자 작업을 수행 하는 주요 수단을 통해 됩니다 [제스처](gestures.md)를 [컨트롤러 동작](motion-controllers.md) 하 고 [음성](voice-input.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="3f6f5-141">The primary ways for a user to take action are through [gestures](gestures.md), [motion controllers](motion-controllers.md) and [voice](voice-input.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3f6f5-142">참조</span><span class="sxs-lookup"><span data-stu-id="3f6f5-142">See also</span></span>
* [<span data-ttu-id="3f6f5-143">MR 입력 210: 응시</span><span class="sxs-lookup"><span data-stu-id="3f6f5-143">MR Input 210: Gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="3f6f5-144">DirectX의 헤드 및 눈 응시</span><span class="sxs-lookup"><span data-stu-id="3f6f5-144">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="3f6f5-145">Unity의 응시</span><span class="sxs-lookup"><span data-stu-id="3f6f5-145">Gaze in Unity</span></span>](gaze-in-unity.md)
