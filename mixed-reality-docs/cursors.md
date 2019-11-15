---
title: 커서
description: 대상 벡터의 커서 또는 표시기는 사용자에 대 한 지속적인 피드백을 제공 하 여 HoloLens의 용도에 대 한 정보를 파악할 수 있습니다.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (첫 번째 gen), HoloLens 2, 혼합 현실, 커서, 대상 지정, 응시, 제스처
ms.openlocfilehash: 719e7a573e8c8bc682ec0f960d9f3c8f8c8e5a4a
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/15/2019
ms.locfileid: "74105738"
---
# <a name="cursors"></a><span data-ttu-id="7bd62-104">커서</span><span class="sxs-lookup"><span data-stu-id="7bd62-104">Cursors</span></span>

![커서](images/UX/UX_Hero_Cursor.jpg)

<span data-ttu-id="7bd62-106">현재 대상 벡터의 커서 또는 표시기는 헤드셋에서 현재 포커스가 있는 위치를 파악할 수 있도록 사용자에 게 지속적인 피드백을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-106">A cursor, or indicator of your current targeting vector, provides continuous feedback for the user to understand where the headset believes their current focus is at that time.</span></span> <span data-ttu-id="7bd62-107">사용자는 커서를 사용 하 여 현재 대상 지정 지점을 이해 하 고 사용자가 입력에 응답 하는 영역, 홀로그램 또는 점을 나타내는 피드백 역할을 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-107">The cursor allows the user to understand their current targeting point and acts as feedback to indicate what area, hologram, or point will respond to input.</span></span> <span data-ttu-id="7bd62-108">장치에서 사용자의 주의가 인식 되는 위치를 디지털로 표현한 것입니다. 단,이는 의도에 대 한 모든 사항을 결정 하는 것과 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-108">It is the digital representation of where the device understands the user's attention to be (though that may not be the same as determining anything about their intentions).</span></span>

<span data-ttu-id="7bd62-109">커서에서 제공 하는 피드백은 사용자가 시스템에 응답 하는 방법을 예상할 수 있는 기능을 제공 하 고, 해당 신호를 피드백으로 사용 하 여 장치에 대 한 의도를 더 잘 전달 하 고, 궁극적으로 상호 작용 하는 것이 더 확실</span><span class="sxs-lookup"><span data-stu-id="7bd62-109">The feedback provided by the cursor offers users the ability to anticipate how the system will respond, use that signal as feedback to better communicate their intention to the device, and ultimately be more confident about their interactions.</span></span>

<span data-ttu-id="7bd62-110">**손가락, 광선**및 **헤드-응시**의 세 가지 종류의 커서가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-110">There are 3 kinds of cursors: **finger, ray**, and **head-gaze**.</span></span> <span data-ttu-id="7bd62-111">이러한 포인팅 커서는 HoloLens, HoloLens 2 및 모던 헤드셋에서 다른 입력 소프트웨어나 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-111">These pointing cursors work with different input modalities on HoloLens, HoloLens 2, and immersive headsets.</span></span> <span data-ttu-id="7bd62-112">다음은 각 유형의 헤드셋 및 상호 작용 모델에 사용할 커서 유형에 대 한 지침입니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-112">Below is guidance on which type of cursor to use for each type of headset and interaction model.</span></span> <span data-ttu-id="7bd62-113">Mixed Reality Toolkit (MRTK)에서 끌어서 놓기 커서 모듈을 만들어 올바른 포인팅 환경을 구축할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-113">In the Mixed Reality Toolkit (MRTK), we've created drag-and-drop cursors modules to help you build the right pointing experience.</span></span>


## <a name="device-support"></a><span data-ttu-id="7bd62-114">장치 지원</span><span class="sxs-lookup"><span data-stu-id="7bd62-114">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="7bd62-115"><strong>기능과</strong></span><span class="sxs-lookup"><span data-stu-id="7bd62-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="7bd62-116"><a href="hololens-hardware-details.md"><strong>HoloLens(1세대)</strong></a></span><span class="sxs-lookup"><span data-stu-id="7bd62-116"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="7bd62-117"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="7bd62-117"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="7bd62-118"><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="7bd62-118"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="7bd62-119">손가락 커서</span><span class="sxs-lookup"><span data-stu-id="7bd62-119">Finger cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="7bd62-120">✔️</span><span class="sxs-lookup"><span data-stu-id="7bd62-120">✔️</span></span></td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="7bd62-121">레이 커서</span><span class="sxs-lookup"><span data-stu-id="7bd62-121">Ray cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="7bd62-122">✔️</span><span class="sxs-lookup"><span data-stu-id="7bd62-122">✔️</span></span></td>
        <td><span data-ttu-id="7bd62-123">✔️</span><span class="sxs-lookup"><span data-stu-id="7bd62-123">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="7bd62-124">헤드-응시 커서</span><span class="sxs-lookup"><span data-stu-id="7bd62-124">Head-gaze cursor</span></span></td>
        <td><span data-ttu-id="7bd62-125">✔️</span><span class="sxs-lookup"><span data-stu-id="7bd62-125">✔️</span></span></td>
        <td><span data-ttu-id="7bd62-126">✔️</span><span class="sxs-lookup"><span data-stu-id="7bd62-126">✔️</span></span></td>
        <td><span data-ttu-id="7bd62-127">✔️</span><span class="sxs-lookup"><span data-stu-id="7bd62-127">✔️</span></span></td>
    </tr>
</table>

## <a name="finger-cursor"></a><span data-ttu-id="7bd62-128">손가락 커서</span><span class="sxs-lookup"><span data-stu-id="7bd62-128">Finger cursor</span></span>
<span data-ttu-id="7bd62-129">핑거 커서는 "[손으로 직접 조작](direct-manipulation.md)" 상호 작용 모드를 향상 시키기 위해 HoloLens 2 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-129">The finger cursor is available only on the HoloLens 2 to enhance the "[direct manipulation with hands](direct-manipulation.md)" interaction mode.</span></span> <span data-ttu-id="7bd62-130">손가락이 가리키는 위치를 더 잘 이해 하기 위해 두 인덱스 손가락의 팁에 링을 연결 했습니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-130">To better understand where the finger is pointing, we have attached rings to the tips of both index fingers.</span></span> <span data-ttu-id="7bd62-131">링 크기는 손가락의 근접성 (손가락 가까이, 링의 작은 쪽)을 기반으로 하며, 손가락이 UI와 접촉 하면 점 모양으로 축소 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-131">The ring size is based on the proximity of the finger to the UI surface (the closer the finger, the smaller the ring) and will shrink to a dot shape when the finger makes contact with the UI.</span></span> <br>

<span data-ttu-id="7bd62-132">![손가락 커서](images/finger-cursor.png)</span><span class="sxs-lookup"><span data-stu-id="7bd62-132">![finger cursor](images/finger-cursor.png)</span></span><br>
<span data-ttu-id="7bd62-133">**손가락 커서 1의 시각적 피드백 상태** : 링이 점으로 축소 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-133">**Visual feedback states of finger cursor** 1: The ring shrinks to a dot.</span></span> <span data-ttu-id="7bd62-134">2: 링이 표면과 맞춰집니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-134">2: The ring aligns with surface.</span></span> <span data-ttu-id="7bd62-135">3: 링이 손가락 벡터에 수직 합니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-135">3: The ring is perpendicular to finger vector.</span></span> <span data-ttu-id="7bd62-136">4: 링 없음</span><span class="sxs-lookup"><span data-stu-id="7bd62-136">4: No ring.</span></span>

## <a name="ray-cursor"></a><span data-ttu-id="7bd62-137">레이 커서</span><span class="sxs-lookup"><span data-stu-id="7bd62-137">Ray cursor</span></span>
<span data-ttu-id="7bd62-138">광선 커서는 먼 곳의 끝에 연결 하 여 손을 벗어난 개체를 조작할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-138">Ray cursors attach to the end of far pointing rays to allow manipulation of objects that are out of hands-reach.</span></span> <span data-ttu-id="7bd62-139">몰입 형 헤드셋에서 광선은 동작 컨트롤러에서 시작 하 여 점 커서에서 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-139">In immersive headsets, the rays shoot out from motion controllers and end in dot cursors.</span></span> <span data-ttu-id="7bd62-140">HoloLens 2에서는 이러한 동작 컨트롤러 광선의 멘 탈 모델을 활용 하 고 직접 조작에 사용 되는 손가락 커서와 일치 하는 고리 모양의 커서에서 시작 하 여 palms에서 시작 하는 핸드 광선을 설계 했습니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-140">In HoloLens 2, we leverage the mental model of these motion controller rays and designed hand rays that originate from the palms and end in ring-shaped cursors that are consistent with finger cursors used in direct manipulation.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="7bd62-141">![레이 커서 컨트롤러](images/ray-cursor-controller.png)</span><span class="sxs-lookup"><span data-stu-id="7bd62-141">![Ray cursor controller](images/ray-cursor-controller.png)</span></span><br>
        <span data-ttu-id="7bd62-142">**동작 컨트롤러의 레이 커서**</span><span class="sxs-lookup"><span data-stu-id="7bd62-142">**Ray cursors of motion controllers**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="7bd62-143">![레이 커서 손](images/ray-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="7bd62-143">![Ray cursor hand](images/ray-cursor-hand.png)</span></span><br>
        <span data-ttu-id="7bd62-144">**바늘의 레이 커서**</span><span class="sxs-lookup"><span data-stu-id="7bd62-144">**Ray cursors of hands**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="head-gaze-cursor"></a><span data-ttu-id="7bd62-145">헤드-응시 커서</span><span class="sxs-lookup"><span data-stu-id="7bd62-145">Head-gaze cursor</span></span>
<span data-ttu-id="7bd62-146">헤드-응시 커서는 헤드의 위치와 회전을 사용 하는 보이지 않는 헤드 응시 벡터의 끝에 연결 되는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-146">The head-gaze cursor is a dot that attaches to the end of an invisible head-gaze vector that uses the position and rotation of the head to point.</span></span> <span data-ttu-id="7bd62-147">작업을 실행 하기 위해이 포인팅 커서는 공중 탭, 음성 명령, 지속 및 단추 누름과 같은 다양 한 커밋 입력과 쌍을 이룹니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-147">To execute actions, this pointing cursor is paired with various commit inputs such as air tap, voice commands, dwell, and button press.</span></span> <span data-ttu-id="7bd62-148">HoloLens 2에서 헤드-응시는 공기 탭과 far 광선 간의 상호 작용 충돌을 발생 시킬 수 있기 때문에 공중 탭이 아닌 커밋 입력에 가장 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-148">In HoloLens 2, head-gaze is best paired with any commit input that is not air tap, as there will be interaction conflict between air tap and far hand rays.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="7bd62-149">![헤드 응시 커서 손](images/head-gaze-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="7bd62-149">![Head gaze cursor hand](images/head-gaze-cursor-hand.png)</span></span><br>
        <span data-ttu-id="7bd62-150">**헤드-손 모양 제스처를 사용 하 여 커서 이동**</span><span class="sxs-lookup"><span data-stu-id="7bd62-150">**Head-gaze cursor with hand gesture**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="7bd62-151">![헤드 응시 커서 음성](images/head-gaze-cursor-voice.png)</span><span class="sxs-lookup"><span data-stu-id="7bd62-151">![Head gaze cursor voice](images/head-gaze-cursor-voice.png)</span></span><br>
        <span data-ttu-id="7bd62-152">**헤드-음성 명령으로 커서를 응시 합니다.**</span><span class="sxs-lookup"><span data-stu-id="7bd62-152">**Head-gaze cursor with voice command**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="cursor-customization-recommendations"></a><span data-ttu-id="7bd62-153">커서 사용자 지정 권장 사항</span><span class="sxs-lookup"><span data-stu-id="7bd62-153">Cursor customization recommendations</span></span>
<span data-ttu-id="7bd62-154">커서 피드백 동작 및 모양을 사용자 지정 하려는 경우 다음 몇 가지 디자인 권장 사항을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7bd62-154">If you would like to customize the cursor feedback behaviors and appearances, here are some design recommendations:</span></span>

### <a name="cursor-scale"></a><span data-ttu-id="7bd62-155">커서 배율</span><span class="sxs-lookup"><span data-stu-id="7bd62-155">Cursor scale</span></span>
* <span data-ttu-id="7bd62-156">사용자가 쉽게 콘텐츠를 조작 하 고 볼 수 있도록 커서는 사용 가능한 대상 보다 크지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-156">The cursor should be no larger than the available targets, allowing users to easily interact with and view the content.</span></span>
* <span data-ttu-id="7bd62-157">사용자가 만드는 환경에 따라 사용자가 볼 때 커서의 크기를 조정 하는 것도 중요 한 고려 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-157">Depending on the experience you create, scaling the cursor as the user looks around is also an important consideration.</span></span> <span data-ttu-id="7bd62-158">예를 들어 사용자가 더 이상 사용자의 경험을 볼 수 없게 되 면 커서는 너무 작아서 손실 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-158">For example, as the user looks further away in your experience, the cursor should not become too small such that it's lost.</span></span>
* <span data-ttu-id="7bd62-159">커서의 크기를 조정 하는 경우 유기적 느낌을 제공 하기 위해 크기가 조정 될 때 소프트 애니메이션을 적용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-159">When scaling the cursor, consider applying a soft animation to it as it scales to give it an organic feeling.</span></span>
* <span data-ttu-id="7bd62-160">방해 하지 않는지 콘텐츠를 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-160">Avoid obstructing content.</span></span> <span data-ttu-id="7bd62-161">Holograms는 환경을 기억 하 고 커서를 사용 하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-161">Holograms are what make the experience memorable and the cursor should not be taking away from them.</span></span>

### <a name="directionless-cursor-shape"></a><span data-ttu-id="7bd62-162">Directionless cursor 셰이프</span><span class="sxs-lookup"><span data-stu-id="7bd62-162">Directionless cursor shape</span></span>
* <span data-ttu-id="7bd62-163">하나의 오른쪽 커서 셰이프도 있지만 torus와 같은 directionless 셰이프를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-163">Although there is no one right cursor shape, we recommend that you use a directionless shape like a torus.</span></span> <span data-ttu-id="7bd62-164">특정 방향 (예: 기존 화살표 커서)을 가리키는 커서는 사용자에 게 항상 표시 되는 것으로 혼동 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-164">A cursor that points in some direction (For example, a traditional arrow cursor) might confuse the user to always look that way.</span></span>
* <span data-ttu-id="7bd62-165">이에 대 한 예외는 커서를 사용 하 여 사용자에 게 상호 작용 명령을 전달 하는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-165">An exception to this is when using the cursor to communicate interaction instruction to the user.</span></span> <span data-ttu-id="7bd62-166">예를 들어 혼합 현실 OS에서 holograms 크기를 조정 하는 경우 커서는 손을 이동 하 여 홀로그램 크기를 조정 하는 방법을 사용자에 게 지시 하는 화살표를 일시적으로 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-166">For example, when scaling holograms in the Mixed Reality OS, the cursor temporarily includes arrows that instructs the user on how to move their hand to scale the hologram.</span></span>

### <a name="look-and-feel"></a><span data-ttu-id="7bd62-167">모양 및 느낌</span><span class="sxs-lookup"><span data-stu-id="7bd62-167">Look and feel</span></span>
* <span data-ttu-id="7bd62-168">도넛형 또는 torus 모양의 커서는 많은 응용 프로그램에 대해 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-168">A donut or torus shaped cursor works for a lot of applications.</span></span>
* <span data-ttu-id="7bd62-169">사용자가 만드는 환경을 가장 잘 나타내는 색과 모양을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-169">Pick a color and shape that best represents the experience you are creating.</span></span>
* <span data-ttu-id="7bd62-170">커서는 특히 [색 구분](hologram-stability.md#color-separation)이 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-170">Cursors are especially prone to [color separation](hologram-stability.md#color-separation).</span></span>
* <span data-ttu-id="7bd62-171">분산 된 불투명도가 있는 작은 커서는 시각적 계층 구조를 dominating 않고 정보를 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-171">A small cursor with balanced opacity keeps it informative without dominating the visual hierarchy.</span></span>
* <span data-ttu-id="7bd62-172">콘텐츠를 액세스가 방해 하 고 작업에서 방해 수 있으므로 커서 뒤에 그림자 또는 하이라이트를 사용 하는 것이 cognizant 합니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-172">Be cognizant of using shadows or highlights behind your cursor as they might obstruct content and distract from the task at hand.</span></span>
* <span data-ttu-id="7bd62-173">커서는 앱의 표면에 맞추고 hug 합니다. 이렇게 하면 시스템에서 원하는 위치를 볼 수 있을 뿐만 아니라 시스템에서 주변을 인식 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-173">Cursors should align to and hug the surfaces in your app, this will give the user a feeling that the system can see where they are looking, but also that the system is aware of their surroundings.</span></span> <span data-ttu-id="7bd62-174">예를 들어 혼합 현실 OS에서는 사용자가 홀로그램에서 직접 확인 하지 않는 경우에도 커서를 사용자 세계의 표면에 맞추고 전 세계의 인식 느낌을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-174">For example, in the Mixed Reality OS, the cursor aligns to the surfaces of the user's world, creating a feeling of awareness of the world even when the user isn't looking directly at a hologram.</span></span>
* <span data-ttu-id="7bd62-175">자기적으로가 근접 한 영역 내에 있을 때 대화형 요소로 커서를 잠그면 사용자가 선택 작업을 수행할 때 해당 요소와 상호 작용 하는 확신을 향상 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-175">Magnetically locking the cursor to an interactive element when it is within close proximity can help improve confidence that user will interact with that element when they perform a selection action.</span></span>

### <a name="visual-cues"></a><span data-ttu-id="7bd62-176">시각적 신호</span><span class="sxs-lookup"><span data-stu-id="7bd62-176">Visual cues</span></span>
* <span data-ttu-id="7bd62-177">환경을 단일 홀로그램에 집중 하는 경우 해당 홀로그램에서 볼 때 커서는 홀로그램 및 변경 셰이프만 정렬 하 고 hug 합니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-177">If your experience is focused on a single hologram, your cursor should align and hug only that hologram and change shape when you look away from that hologram.</span></span> <span data-ttu-id="7bd62-178">이는 사용자에 게 홀로그램 작업을 수행할 수 있고 사용자가이를 조작할 수 있음을 알릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-178">This can convey to the user that the hologram is actionable and they can interact with it.</span></span>
* <span data-ttu-id="7bd62-179">응용 프로그램에서 공간 매핑을 사용 하는 경우 커서가 표시 하는 모든 표면에 커서를 맞추고 hug 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-179">If your application uses spatial mapping, then your cursor could align and hug every surface it sees.</span></span> <span data-ttu-id="7bd62-180">그러면 HoloLens를 사용 하는 사용자에 게 피드백을 제공 하 고 응용 프로그램에서 해당 공간을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-180">This gives feedback to the users that HoloLens and your application can see their space.</span></span> <span data-ttu-id="7bd62-181">이를 통해 강화는 진정한 세계 이며 실제 및 가상 간의 차이를 쉽게 파악할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-181">This reinforces the fact that holograms are real and in our world and helps bridge the gap between real and virtual.</span></span>
* <span data-ttu-id="7bd62-182">보기에 holograms 또는 표면이 없을 때 커서에서 수행 해야 하는 작업을 파악 합니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-182">Have an idea of what the cursor should do when there are no holograms or surfaces in view.</span></span> <span data-ttu-id="7bd62-183">사용자 앞의 미리 정해진 거리에 배치 하는 것은 한 가지 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-183">Placing it at a predetermined distance in front of the user is one option.</span></span>

### <a name="possible-actions"></a><span data-ttu-id="7bd62-184">가능한 작업</span><span class="sxs-lookup"><span data-stu-id="7bd62-184">Possible actions</span></span>
* <span data-ttu-id="7bd62-185">커서는 여러 아이콘으로 표시 되어 홀로그램에서 크기 조정 또는 회전과 같이 수행할 수 있는 작업을 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-185">The cursor can be represented by different icons to convey possible actions a hologram can perform, such as scaling or rotation.</span></span>
* <span data-ttu-id="7bd62-186">사용자에 게 무언가가 있음을 의미 하는 경우에만 커서에 추가 정보를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-186">Only add extra information on the cursor if it means something to the user.</span></span> <span data-ttu-id="7bd62-187">그렇지 않으면 사용자가 상태를 변경 하거나 커서를 혼동 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-187">Otherwise, users might either not notice the state changes or get confused by the cursor.</span></span>

### <a name="input-state"></a><span data-ttu-id="7bd62-188">입력 상태</span><span class="sxs-lookup"><span data-stu-id="7bd62-188">Input state</span></span>
* <span data-ttu-id="7bd62-189">커서를 사용 하 여 사용자의 입력 상태나 의도를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-189">We could use the cursor to display the user's input state or intent.</span></span> <span data-ttu-id="7bd62-190">예를 들어 사용자에 게 시스템 상태를 확인 하 고 응용 프로그램에서 사용자에 게 조치를 취할 준비가 되었음을 알리는 아이콘을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-190">For example, we could display an icon telling the user the system sees their hand state and that the application knows they are ready to take action.</span></span>
* <span data-ttu-id="7bd62-191">또한 일시적 색을 통해 시스템에서 음성 명령을 파일과 사용자를 표시 하는 데 커서를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-191">We could also use the cursor to show users that voice commands have been heard by the system via a momentary color chang</span></span>

* <span data-ttu-id="7bd62-192">다음 커서 상태를 다양 한 방법으로 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-192">The following cursor states can be implemented in different ways.</span></span> <span data-ttu-id="7bd62-193">상태 시스템 처럼 커서를 모델링 하 여 이러한 다양 한 상태를 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-193">You might implement these different states by modeling the cursor like a state machine.</span></span> <span data-ttu-id="7bd62-194">예를 들어 다음과 같은 가치를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-194">For example:</span></span>
    * <span data-ttu-id="7bd62-195">유휴 상태는 기본 커서를 표시 하는 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-195">Idle state is where you show the default cursor.</span></span>
    * <span data-ttu-id="7bd62-196">준비 상태는 준비 위치에서 사용자의 손을 검색 한 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-196">Ready state is when you have detected the user's hand in the ready position.</span></span>
    * <span data-ttu-id="7bd62-197">상호 작용 상태는 사용자가 특정 상호 작용을 수행 하는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-197">Interaction state is when the user is performing a particular interaction.</span></span>
    * <span data-ttu-id="7bd62-198">가능한 작업 상태 또는 가리키기 상태는 홀로그램에서 수행할 수 있는 가능한 작업을 전달 하는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-198">Possible Actions state or hover state is when you convey possible actions that can be performed on a hologram.</span></span>

<span data-ttu-id="7bd62-199">다양 한 상태가 검색 되 면 다양 한 아트 자산을 표시할 수 있도록 이러한 상태를 스킨 가능 방식으로 구현할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-199">You could also implement these states in a skin-able manner such that you can display different art assets when different states are detected.</span></span>

<br>

---


## <a name="going-cursor-free"></a><span data-ttu-id="7bd62-200">"커서를 사용 하지 않음"으로 이동</span><span class="sxs-lookup"><span data-stu-id="7bd62-200">Going "cursor-free"</span></span>
<span data-ttu-id="7bd62-201">집중 교육의 의미는 환경의 주요 구성 요소이 고 (응시 및 제스처를 통해)에는 상당한 정밀도가 필요 하지 않은 경우 커서를 사용 하지 않고 디자인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-201">Designing without a cursor is recommended when the sense of immersion is a key component of an experience and when pointing interactions (through gaze and gesture) do not require great precision.</span></span> <span data-ttu-id="7bd62-202">시스템은 시스템에 대 한 지속적인 피드백을 사용자에 게 제공 하 고 사용자가 자신의 의도를 시스템에 안전 하 게 전달할 수 있도록 하 여 커서가 일반적으로 충족 하는 요구 사항을 충족 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-202">The system must still meet the needs that are normally met by a cursor by providing users with continuous feedback on the system's understanding of their pointing and helping them to confidently communicate their intentions to the system.</span></span> <span data-ttu-id="7bd62-203">이는 다른 눈에 띄는 상태를 변경 하 여 달성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-203">This may be achievable through other noticeable state changes.</span></span>

<br>

---

## <a name="cursor-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="7bd62-204">Unity 용 MRTK (Mixed Reality Toolkit)의 커서</span><span class="sxs-lookup"><span data-stu-id="7bd62-204">Cursor in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="7bd62-205">기본적으로 **[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 는 셸 시스템 커서와 동일한 시각적 상태를 가진 커서 Prefab ([defaultcursor. prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors))를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-205">By default, **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides a cursor prefab([DefaultCursor.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) which has the same visual state as the shell's system cursor.</span></span> <span data-ttu-id="7bd62-206">이는 MRTK의 입력 프로필에 있는 포인터 아래에 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-206">It is assigned in MRTK's Input profile, under Pointers.</span></span> <span data-ttu-id="7bd62-207">사용자 환경에 맞게이 커서를 바꾸거나 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-207">You can replace/customize this cursor for your experience.</span></span> <span data-ttu-id="7bd62-208">아이 추적 입력 환경에서 MRTK는 혼란을 최소화 하기 위해 미묘한 시각적 개체를 포함 하는 EyeGazeCursor 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="7bd62-208">For the experience with eye-tracking input, MRTK also provides EyeGazeCursor which has subtle visual to minimize the distraction.</span></span>

* [<span data-ttu-id="7bd62-209">MRTK-포인터 프로필</span><span class="sxs-lookup"><span data-stu-id="7bd62-209">MRTK - Pointer profile</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html#pointer-configuration)
* [<span data-ttu-id="7bd62-210">MRTK-입력 시스템</span><span class="sxs-lookup"><span data-stu-id="7bd62-210">MRTK - Input system</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)
* [<span data-ttu-id="7bd62-211">MRTK-포인터</span><span class="sxs-lookup"><span data-stu-id="7bd62-211">MRTK - Pointers</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html)


---

## <a name="see-also"></a><span data-ttu-id="7bd62-212">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7bd62-212">See also</span></span>
* [<span data-ttu-id="7bd62-213">제스처</span><span class="sxs-lookup"><span data-stu-id="7bd62-213">Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="7bd62-214">헤드 게이즈 및 커밋</span><span class="sxs-lookup"><span data-stu-id="7bd62-214">Head-gaze and commit</span></span>](gaze-and-commit.md)
