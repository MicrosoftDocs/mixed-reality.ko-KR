---
title: 시스템 제스처
description: 시작 메뉴를 호출 하는 시스템 제스처입니다.
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: 혼합 현실, 제스처, 상호 작용, 디자인
ms.openlocfilehash: 417811fff9d98e459dc0047d46ea065acfced4ef
ms.sourcegitcommit: f2b7c6381006fab6d0472fcaa680ff7fb79954d6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74064236"
---
# <a name="system-gesture"></a><span data-ttu-id="429f7-104">시스템 제스처</span><span class="sxs-lookup"><span data-stu-id="429f7-104">System gesture</span></span>

<span data-ttu-id="429f7-105">시스템 제스처는 시작 메뉴를 호출 하는 데 사용 되는 손 제스처입니다.</span><span class="sxs-lookup"><span data-stu-id="429f7-105">The system gesture is a hand gesture used to invoke the Start Menu.</span></span> <span data-ttu-id="429f7-106">이는 키보드에서 Windows 키를 누르거나 Xbox 컨트롤러의 Xbox 단추를 누르거나 몰입 형 헤드셋 동작 컨트롤러의 Windows 단추를 누르는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="429f7-106">It is the equivalent of pressing the Windows key on the keyboard, the Xbox button on an Xbox controller, or the Windows button on the immersive headset motion controller.</span></span> <span data-ttu-id="429f7-107">상호 작용을 디자인할 때 충돌을 방지 하기 위해 각 혼합 현실 장치에서 시스템용으로 예약 된 제스처를 이해 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="429f7-107">It's important to understand which gestures are reserved for the system on each Mixed Reality device to prevent conflicts when designing your interactions.</span></span>

## <a name="device-support"></a><span data-ttu-id="429f7-108">장치 지원</span><span class="sxs-lookup"><span data-stu-id="429f7-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="429f7-109"><strong>기능과</strong></span><span class="sxs-lookup"><span data-stu-id="429f7-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="429f7-110"><a href="hololens-hardware-details.md"><strong>HoloLens(1세대)</strong></a></span><span class="sxs-lookup"><span data-stu-id="429f7-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="429f7-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="429f7-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="429f7-112"><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="429f7-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="429f7-113">블 룸</span><span class="sxs-lookup"><span data-stu-id="429f7-113">Bloom</span></span></td>
        <td><span data-ttu-id="429f7-114">✔️</span><span class="sxs-lookup"><span data-stu-id="429f7-114">✔️</span></span></td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="429f7-115">손목 단추</span><span class="sxs-lookup"><span data-stu-id="429f7-115">Wrist button</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="429f7-116">✔️</span><span class="sxs-lookup"><span data-stu-id="429f7-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="429f7-117">아이 응시 및 야자수</span><span class="sxs-lookup"><span data-stu-id="429f7-117">Eye gaze and palm up pinch</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="429f7-118">✔️</span><span class="sxs-lookup"><span data-stu-id="429f7-118">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a><span data-ttu-id="429f7-119">블 룸</span><span class="sxs-lookup"><span data-stu-id="429f7-119">Bloom</span></span>
<span data-ttu-id="429f7-120">HoloLens (첫 번째 gen)에서 시작 메뉴를 표시 하기 위해 꽃 벚꽃를 모방 기호화 된 제스처로 "블 룸"를 디자인 했습니다.</span><span class="sxs-lookup"><span data-stu-id="429f7-120">To bring up the start menu in HoloLens (1st gen), we designed “Bloom”, which is a symbolic gesture mimicking the flower blossom.</span></span> <span data-ttu-id="429f7-121">상호 작용 하 고, 쉽게 수행 하 고, 신속 하 게 회수할 수 있는 특수 한 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="429f7-121">It's distinctive for surefooted interaction, easy to perform, and quick to recall.</span></span> <span data-ttu-id="429f7-122">HoloLens (첫 번째 gen)에서 블 룸 제스처를 수행 하려면 야자나무를 함께 사용 하 여 손을 놓고 손가락을 확산 시켜 손을 여세요.</span><span class="sxs-lookup"><span data-stu-id="429f7-122">To do the bloom gesture on HoloLens (1st gen), hold out your hand with your palm up and fingertips together, then open your hand by spreading your fingers.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="429f7-123">![블 룸 close](images/bloom-close.png)</span><span class="sxs-lookup"><span data-stu-id="429f7-123">![Bloom close](images/bloom-close.png)</span></span><br>
        <span data-ttu-id="429f7-124">**1 단계: 쉽게 함께 팜 강화**</span><span class="sxs-lookup"><span data-stu-id="429f7-124">**Step 1: Palm up with fingertips together**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="429f7-125">![블 룸 open](images/bloom-open.png)</span><span class="sxs-lookup"><span data-stu-id="429f7-125">![Bloom open](images/bloom-open.png)</span></span><br>
        <span data-ttu-id="429f7-126">**2 단계: 간편 하 게 확산 된 팜**</span><span class="sxs-lookup"><span data-stu-id="429f7-126">**Step 2: Palm up with fingertips spread**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="wrist-button"></a><span data-ttu-id="429f7-127">손목 단추</span><span class="sxs-lookup"><span data-stu-id="429f7-127">Wrist button</span></span>
<span data-ttu-id="429f7-128">HoloLens 2에서 블 룸 제스처는 추가 교육을 필요로 하지 않는 더 많은 instinctual 상호 작용을 허용 하는 가상 손목 단추로 대체 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="429f7-128">In HoloLens 2, we replaced the Bloom gesture with a virtual wrist button that allows for more instinctual interactions that require no additional teaching.</span></span> <span data-ttu-id="429f7-129">사용자가 손목 단추를 표시 하 여 쉽게 접근 하 고 다른 손으로 누를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="429f7-129">By showing users the button on the wrist, they can intuitively reach out and press it with their other hand.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="429f7-130">![손목 단추 준비](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="429f7-130">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="429f7-131">**1 단계: 손목 단추를 표시 합니다.**</span><span class="sxs-lookup"><span data-stu-id="429f7-131">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="429f7-132">![손목 단추 누르기](images/wrist-button-press.png)</span><span class="sxs-lookup"><span data-stu-id="429f7-132">![Wrist button press](images/wrist-button-press.png)</span></span><br>
        <span data-ttu-id="429f7-133">**2 단계: 손목 단추 누르기**</span><span class="sxs-lookup"><span data-stu-id="429f7-133">**Step 2: Press the wrist button**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="eye-gaze-and-palm-up-pinch"></a><span data-ttu-id="429f7-134">눈에 응시 하 고 야자수</span><span class="sxs-lookup"><span data-stu-id="429f7-134">Eye-gaze and palm up pinch</span></span>
<span data-ttu-id="429f7-135">또한 HoloLens 2에서 편리 하 게 액세스할 수 있는 단일 솔루션을 설계 했습니다.</span><span class="sxs-lookup"><span data-stu-id="429f7-135">We have also designed a one-handed solution for ease of access in HoloLens 2.</span></span> <span data-ttu-id="429f7-136">이 제스처를 사용 하려면 사용자가 손목 단추를 클릭 한 다음 동일한 손을 사용 하 여 엄지 단추를 사용 하 여 손가락을 위로 이동할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="429f7-136">This gesture requires users to eye gaze at the wrist button, then use the same hand to perform a palm up pinch using their thumb and index finger.</span></span><br>
:::row:::
    :::column:::
        <span data-ttu-id="429f7-137">![손목 단추 준비](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="429f7-137">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="429f7-138">**1 단계: 손목 단추를 표시 합니다.**</span><span class="sxs-lookup"><span data-stu-id="429f7-138">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="429f7-139">![손목 단추를 손가락으로](images/wrist-button-pinch.png)</span><span class="sxs-lookup"><span data-stu-id="429f7-139">![Wrist button pinch](images/wrist-button-pinch.png)</span></span><br>
        <span data-ttu-id="429f7-140">**2 단계: 단추를 누른 후 손가락으로 이동**</span><span class="sxs-lookup"><span data-stu-id="429f7-140">**Step 2: Eye gaze at the button then pinch**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="429f7-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="429f7-141">See also</span></span>

* [<span data-ttu-id="429f7-142">Instinctual 상호 작용</span><span class="sxs-lookup"><span data-stu-id="429f7-142">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="429f7-143">눈 응시</span><span class="sxs-lookup"><span data-stu-id="429f7-143">Eye-gaze</span></span>](eye-tracking.md)
* [<span data-ttu-id="429f7-144">음성 입력 </span><span class="sxs-lookup"><span data-stu-id="429f7-144">Voice input</span></span>](voice-input.md)
