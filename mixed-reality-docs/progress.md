---
title: 진행률 표시
description: 진행률 컨트롤은 긴 작업을 진행 중인 사용자에게 피드백을 제공합니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 디자인, 컨트롤, ui, ux
ms.openlocfilehash: 43b4802e7c821c98c847509ace950f381da12f95
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437534"
---
# <a name="displaying-progress"></a><span data-ttu-id="59956-104">진행률 표시</span><span class="sxs-lookup"><span data-stu-id="59956-104">Displaying progress</span></span>

<br>

<img src="images/HoloLens2_Loader.gif" alt="Progress ring example in HoloLens" width="940px">

<span data-ttu-id="59956-105">진행률 컨트롤은 긴 작업을 진행 중인 사용자에게 피드백을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="59956-105">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="59956-106">이는 진행률 표시기가 표시될 때 사용자가 앱을 조작할 수 없다는 의미이며 사용되는 표시기에 따라 대기 시간을 예측할 수도 있다는 의미입니다.</span><span class="sxs-lookup"><span data-stu-id="59956-106">It can mean that the user cannot interact with the app when the progress indicator is visible, and can also indicate how long the wait time might be, depending on the indicator used.</span></span>

<br>

---

## <a name="types-of-progress"></a><span data-ttu-id="59956-107">진행률 유형</span><span class="sxs-lookup"><span data-stu-id="59956-107">Types of progress</span></span>

<span data-ttu-id="59956-108">발생 한 상황에 대 한 사용자 정보를 제공 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="59956-108">It is important to provide the user information about what is happening.</span></span> <span data-ttu-id="59956-109">혼합 현실에서는 앱이 좋은 시각적 피드백을 제공 하지 않는 경우 실제 환경 또는 개체에 의해 사용자가 쉽게 무시 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59956-109">In mixed reality users can be easily distracted by physical environment or objects if your app does not gives good visual feedback.</span></span> <span data-ttu-id="59956-110">데이터를 로드 하거나 장면을 업데이트 하는 경우와 같이 몇 초 정도 걸리는 상황에서는 시각적 표시기를 표시 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="59956-110">For situations that take a few seconds, such when data is loading or a scene is updating, it is good idea to show a visual indicator.</span></span> <span data-ttu-id="59956-111">작업이 진행 중인 사용자를 표시 하는 두 가지 옵션은 **진행률 표시줄이** 나 **진행 링**입니다.</span><span class="sxs-lookup"><span data-stu-id="59956-111">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a><span data-ttu-id="59956-112">진행률 표시줄</span><span class="sxs-lookup"><span data-stu-id="59956-112">Progress bar</span></span><br>
        <span data-ttu-id="59956-113">진행률 표시줄에는 태스크의 완료율이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="59956-113">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="59956-114">기간이 알려진 작업 (활성화 상태의) 중에 사용 해야 하지만, 진행률은 사용자가 앱과의 상호 작용을 차단 하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="59956-114">It should be used during an operation whose duration is known (determinate), but it's progress should not block the user's interaction with the app.</span></span><br>
        <br>
        <span data-ttu-id="59956-115">*이미지: HoloLens의 진행률 표시줄 예*</span><span class="sxs-lookup"><span data-stu-id="59956-115">*Image: Progress bar example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="59956-116">![공간](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="59956-116">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="59956-117">HoloLens의 ![진행률 표시줄 예제](images/640px-progressbar.jpg)</span><span class="sxs-lookup"><span data-stu-id="59956-117">![Progress bar example in HoloLens](images/640px-progressbar.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a><span data-ttu-id="59956-118">진행률 링</span><span class="sxs-lookup"><span data-stu-id="59956-118">Progress ring</span></span><br>
        <span data-ttu-id="59956-119">진행률 링은 확정 되지 않은 상태 이며 작업이 완료 될 때까지 추가 사용자 조작이 차단 되는 경우에만 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="59956-119">A Progress ring only has an indeterminate state, and should be used when any further user interaction is blocked until the operation has completed.</span></span><br>
        <br>
        <span data-ttu-id="59956-120">*이미지: HoloLens의 진행 링 예*</span><span class="sxs-lookup"><span data-stu-id="59956-120">*Image: Progress ring example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="59956-121">![공간](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="59956-121">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="59956-122">HoloLens의 ![진행률 링 예제](images/640px-progressring.jpg)</span><span class="sxs-lookup"><span data-stu-id="59956-122">![Progress ring example in HoloLens](images/640px-progressring.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a><span data-ttu-id="59956-123">사용자 지정 개체의 진행률</span><span class="sxs-lookup"><span data-stu-id="59956-123">Progress with a custom object</span></span><br>
        <span data-ttu-id="59956-124">사용자 지정 2D/3D 개체를 사용 하 여 진행률 컨트롤을 사용자 지정 하 여 앱의 개성 및 브랜드 id에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59956-124">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span><br>
        <br>
        <span data-ttu-id="59956-125">*이미지: HoloLens의 사용자 지정 메시 예제를 사용 하 여 진행*</span><span class="sxs-lookup"><span data-stu-id="59956-125">*Image: Progress with custom mesh example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="59956-126">![공간](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="59956-126">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="59956-127">HoloLens의 사용자 지정 메시 예제를 사용 하 여 진행 ![](images/640px-progresscustom.jpg)</span><span class="sxs-lookup"><span data-stu-id="59956-127">![Progress with custom mesh example in HoloLens](images/640px-progresscustom.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a><span data-ttu-id="59956-128">모범 사례</span><span class="sxs-lookup"><span data-stu-id="59956-128">Best practices</span></span>
* <span data-ttu-id="59956-129">사용자가 자신의 헤드를 빈 공간으로 쉽게 이동 하 고 컨텍스트를 손실할 수 있으므로 [billboarding 또는 태그](billboarding-and-tag-along.md) 를 진행률 표시와 긴밀 하 게 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="59956-129">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="59956-130">사용자가 아무것도 확인할 수 없는 경우 앱이 손상 된 것 처럼 보일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59956-130">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="59956-131">Billboarding 및 태그 동반은 Progress prefab에 기본 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="59956-131">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="59956-132">항상 사용자에 게 발생 하는 상황에 대 한 상태 정보를 제공 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="59956-132">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="59956-133">진행률 prefab 상태를 제공 하기 위한 Windows 표준 링 유형 진행률을 비롯 한 다양 한 비주얼 스타일을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="59956-133">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="59956-134">응용 프로그램의 브랜드에 맞게 진행률 스타일을 조정 하려는 경우 애니메이션으로 사용자 지정 메시를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59956-134">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="59956-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="59956-135">See also</span></span>
* [<span data-ttu-id="59956-136">Mixed Reality Toolkit의 Progress scripts and prefabs</span><span class="sxs-lookup"><span data-stu-id="59956-136">Progress scripts and prefabs on Mixed Reality Toolkit</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Loader)
* [<span data-ttu-id="59956-137">경계 상자</span><span class="sxs-lookup"><span data-stu-id="59956-137">Bounding box</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="59956-138">상호 작용 가능한 개체</span><span class="sxs-lookup"><span data-stu-id="59956-138">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="59956-139">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="59956-139">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="59956-140">빌보딩 및 태그얼롱</span><span class="sxs-lookup"><span data-stu-id="59956-140">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
