---
title: 응시
description: 응시는 첫 번째 입력 형태 이며 혼합 현실에서 대상이 지정 되는 기본 형식입니다.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 혼합 현실, 응시, 상호 작용, 디자인
ms.openlocfilehash: 7e65d26d3e9edabbd01d35a887ffc8622a3c6337
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414376"
---
# <a name="gaze"></a><span data-ttu-id="4926c-104">응시</span><span class="sxs-lookup"><span data-stu-id="4926c-104">Gaze</span></span>

<span data-ttu-id="4926c-105">**응시** 는 첫 번째 입력 형태 이며 혼합 현실에서 대상이 지정 되는 기본 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="4926c-105">**Gaze** is the first form of input and is a primary form of targeting within mixed reality.</span></span> <span data-ttu-id="4926c-106">응시를 통해 사용자가 전 세계 어디에서 찾고 있는지를 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4926c-106">Gaze tells you where the user is looking in the world and lets you determine their intent.</span></span> <span data-ttu-id="4926c-107">실제 세계에서는 일반적으로 상호 작용 하려는 개체를 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="4926c-107">In the real world, you'll typically look at an object that you intend to interact with.</span></span> <span data-ttu-id="4926c-108">이는 응시와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="4926c-108">This is the same with gaze.</span></span>

<span data-ttu-id="4926c-109">혼합 현실 헤드셋은 사용자 헤드의 위치와 방향을 사용 하 여 헤드 응시 벡터를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4926c-109">Mixed reality headsets use the position and orientation of your user's head to determine their head gaze vector.</span></span> <span data-ttu-id="4926c-110">이 벡터를 사용자의 눈 사이에서 바로 미리 레이저 포인터로 생각할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4926c-110">You can think of this vector as a laser pointer straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="4926c-111">사용자가 대화방을 볼 때 응용 프로그램은 자체 holograms 및 [공간 매핑](spatial-mapping.md) 메시를 사용 하 여 사용자가 볼 수 있는 가상 또는 실제 개체를 결정 하기 위해이 광선을 교차할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4926c-111">As the user looks around the room, your application can intersect this ray, both with its own holograms and with the [spatial mapping](spatial-mapping.md) mesh to determine what virtual or real-world object your user may be looking at.</span></span>

<span data-ttu-id="4926c-112">HoloLens 2에서 상호 작용은 사용자의 헤드 응시, 눈동자 응시 또는 근거리 또는 원거리 상호 작용을 통해 대상으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4926c-112">On HoloLens 2, interactions can be targeted by either the user's head gaze, eye gaze or through near or far hand interactions.</span></span>
<span data-ttu-id="4926c-113">HoloLens (첫 번째 gen)에서 상호 작용은 일반적으로 직접 위치에서 렌더링 하거나 상호 작용 하는 대신 사용자의 헤드 응시에서 대상으로 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4926c-113">On HoloLens (1st gen), interactions should generally derive their targeting from the user's head gaze, rather than trying to render or interact at the hand's location directly.</span></span> <span data-ttu-id="4926c-114">상호 작용이 시작 된 후 [조작 또는 탐색](gestures.md#composite-gestures) 제스처와 같이 손의 상대 동작을 사용 하 여 [제스처](gestures.md)를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4926c-114">Once an interaction has started, relative motions of the hand may be used to control the [gesture](gestures.md), as with the [manipulation or navigation](gestures.md#composite-gestures) gesture.</span></span> <span data-ttu-id="4926c-115">모던 헤드셋을 사용 하면 헤드 응시 또는 포인팅 가능 [동작 컨트롤러](motion-controllers.md)를 사용 하 여 대상으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4926c-115">With immersive headsets, you can target using either head gaze or pointing-capable [motion controllers](motion-controllers.md).</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/zCPiZlWdVws]

## <a name="device-support"></a><span data-ttu-id="4926c-116">장치 지원</span><span class="sxs-lookup"><span data-stu-id="4926c-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4926c-117"><strong>기능</strong></span><span class="sxs-lookup"><span data-stu-id="4926c-117"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="4926c-118"><a href="hololens-hardware-details.md"><strong>HoloLens(1세대)</strong></a></span><span class="sxs-lookup"><span data-stu-id="4926c-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="4926c-119"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="4926c-119"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="4926c-120"><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="4926c-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4926c-121">헤드 응시</span><span class="sxs-lookup"><span data-stu-id="4926c-121">Head gaze</span></span></td>
        <td><span data-ttu-id="4926c-122">✔️</span><span class="sxs-lookup"><span data-stu-id="4926c-122">✔️</span></span></td>
        <td><span data-ttu-id="4926c-123">✔️</span><span class="sxs-lookup"><span data-stu-id="4926c-123">✔️</span></span></td>
        <td><span data-ttu-id="4926c-124">✔️</span><span class="sxs-lookup"><span data-stu-id="4926c-124">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4926c-125">아이 응시</span><span class="sxs-lookup"><span data-stu-id="4926c-125">Eye gaze</span></span></td>
        <td><span data-ttu-id="4926c-126">❌</span><span class="sxs-lookup"><span data-stu-id="4926c-126">❌</span></span></td>
        <td><span data-ttu-id="4926c-127">✔️</span><span class="sxs-lookup"><span data-stu-id="4926c-127">✔️</span></span></td>
        <td><span data-ttu-id="4926c-128">❌</span><span class="sxs-lookup"><span data-stu-id="4926c-128">❌</span></span></td>
    </tr>
</table>

> [!NOTE]
> <span data-ttu-id="4926c-129">HoloLens 2에 대 한 추가 지침은 [곧](index.md#news-and-notes)제공 될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="4926c-129">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>


## <a name="uses-of-gaze"></a><span data-ttu-id="4926c-130">응시 사용</span><span class="sxs-lookup"><span data-stu-id="4926c-130">Uses of gaze</span></span>

<span data-ttu-id="4926c-131">혼합 현실 개발자는 head 또는 눈동자 응시를 사용 하 여 많은 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4926c-131">As a mixed reality developer, you can do a lot with head or eye gaze:</span></span>
* <span data-ttu-id="4926c-132">앱은 사용자의 주의가 있는 위치를 확인 하기 위해 장면의 holograms와 교차할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4926c-132">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is.</span></span>
* <span data-ttu-id="4926c-133">앱은 사용자의 응시에 따라 제스처 및 컨트롤러 누름을 대상으로 지정할 수 있으므로 사용자가 선택, 활성화, 잡기, 스크롤 또는 holograms와 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4926c-133">Your app can target gestures and controller presses based on the user's gaze, letting the user select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="4926c-134">앱을 사용 하면 사용자가 holograms 표면에 해당 응시 광선과 공간 매핑 메시를 교차 시켜 서 실제 표면에 놓을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4926c-134">Your app can let the user place holograms on real-world surfaces, by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="4926c-135">앱은 사용자가 중요 한 개체의 방향을 확인 *하지 않는* 경우를 알 수 있습니다. 그러면 응용 프로그램에서 시각적 개체와 오디오 신호를 제공 하 여 해당 개체를 가리킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4926c-135">Your app can know when the user is *not* looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

## <a name="cursor"></a><span data-ttu-id="4926c-136">Cursor</span><span class="sxs-lookup"><span data-stu-id="4926c-136">Cursor</span></span>

<span data-ttu-id="4926c-137">헤드 응시의 경우 대부분의 앱은 [커서](cursors.md) (또는 기타 청각/시각적 표시)를 사용 하 여 사용자가 상호 작용 하려는 항목을 사용자에 게 확실 하 게 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4926c-137">For head gaze, most apps should use a [cursor](cursors.md) (or other auditory/visual indication) to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="4926c-138">일반적으로 헤드 응시 광선이 먼저 개체와 교차 하는 위치에이 커서를 배치 합니다 .이는 홀로그램 또는 실제 표면이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4926c-138">You typically position this cursor in the world where their head gaze ray first intersects an object, which may be a hologram or a real-world surface.</span></span>

<span data-ttu-id="4926c-139">![응시를 표시 하는 예제 시각적 커서](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="4926c-139">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
<span data-ttu-id="4926c-140">*응시를 표시 하는 예제 시각적 커서*</span><span class="sxs-lookup"><span data-stu-id="4926c-140">*An example visual cursor to show gaze*</span></span>

<span data-ttu-id="4926c-141">아이 응시의 경우 일반적으로 사용자에 게 혼란을 줄 수 있으므로 커서를 표시 *하지 않는* 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4926c-141">For eye gaze, we generally recommend *not* to show a cursor, as this can quickly become distracting and annoying for the user.</span></span> <span data-ttu-id="4926c-142">대신 시각적 대상을 미세 하 게 강조 표시 하거나 매우 희미 한 눈 커서를 사용 하 여 사용자가 상호 작용할 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="4926c-142">Instead subtly highlight visual targets or use a very faint eye cursor to provide confidence about what the user is about to interact with.</span></span> <span data-ttu-id="4926c-143">자세한 내용은 HoloLens 2의 [눈동자 기반 입력에 대 한 디자인 지침](eye-tracking.md) 을 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="4926c-143">For more information, please check out our [design guidance for eye-based input](eye-tracking.md) on HoloLens 2.</span></span>

## <a name="giving-action-to-the-users-gaze"></a><span data-ttu-id="4926c-144">사용자의 응시에 작업 제공</span><span class="sxs-lookup"><span data-stu-id="4926c-144">Giving action to the user's gaze</span></span>

<span data-ttu-id="4926c-145">사용자가 응시를 사용 하 여 홀로그램 또는 실제 개체를 대상으로 지정 하 고 나면 다음 단계는 해당 개체에 대해 작업을 수행 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4926c-145">Once the user has targeted a hologram or real-world object using their gaze, their next step is to take action on that object.</span></span> <span data-ttu-id="4926c-146">사용자가 작업을 수행 하는 기본 방법은 [제스처](gestures.md), [동작 컨트롤러](motion-controllers.md) 및 [음성을](voice-input.md)사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4926c-146">The primary ways for a user to take action are through [gestures](gestures.md), [motion controllers](motion-controllers.md) and [voice](voice-input.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4926c-147">참조</span><span class="sxs-lookup"><span data-stu-id="4926c-147">See also</span></span>
* [<span data-ttu-id="4926c-148">MR 입력 210: 헤드 응시</span><span class="sxs-lookup"><span data-stu-id="4926c-148">MR Input 210: Head gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="4926c-149">DirectX의 헤드 및 눈 응시</span><span class="sxs-lookup"><span data-stu-id="4926c-149">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="4926c-150">Unity의 헤드 응시</span><span class="sxs-lookup"><span data-stu-id="4926c-150">Head gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="4926c-151">눈동자-HoloLens에서 응시 2</span><span class="sxs-lookup"><span data-stu-id="4926c-151">Eye-gaze on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="4926c-152">Mixed Reality Toolkit를 사용 하 여 Unity의 눈동자 응시</span><span class="sxs-lookup"><span data-stu-id="4926c-152">Eye gaze in Unity using Mixed Reality Toolkit</span></span>](https://aka.ms/mrtk-eyes)
