---
title: 진행률 표시
description: 진행률 컨트롤은 긴 작업을 진행 중인 사용자에게 피드백을 제공합니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, ux, ui, 컨트롤, 디자인
ms.openlocfilehash: d62d86c690233f351b6c156c66eba33cb2687ea6
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813739"
---
# <a name="displaying-progress"></a><span data-ttu-id="cc167-104">진행률 표시</span><span class="sxs-lookup"><span data-stu-id="cc167-104">Displaying progress</span></span>

<span data-ttu-id="cc167-105">진행률 컨트롤은 긴 작업을 진행 중인 사용자에게 피드백을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="cc167-105">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="cc167-106">이는 진행률 표시기가 표시될 때 사용자가 앱을 조작할 수 없다는 의미이며 사용되는 표시기에 따라 대기 시간을 예측할 수도 있다는 의미입니다.</span><span class="sxs-lookup"><span data-stu-id="cc167-106">It can mean that the user cannot interact with the app when the progress indicator is visible, and can also indicate how long the wait time might be, depending on the indicator used.</span></span>

<span data-ttu-id="cc167-107">![HoloLens에 진행률 링 예제](images/HoloLens2_Loader.gif)</span><span class="sxs-lookup"><span data-stu-id="cc167-107">![Progress ring example in HoloLens](images/HoloLens2_Loader.gif)</span></span><br>
<span data-ttu-id="cc167-108">*HoloLens에 진행률 링 예제*</span><span class="sxs-lookup"><span data-stu-id="cc167-108">*Progress ring example in HoloLens*</span></span>

## <a name="types-of-progress"></a><span data-ttu-id="cc167-109">진행률 유형</span><span class="sxs-lookup"><span data-stu-id="cc167-109">Types of progress</span></span>

<span data-ttu-id="cc167-110">상황에 대 한 사용자 정보를 제공 하는 것이 반드시 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc167-110">It is important to provide the user information about what is happening.</span></span> <span data-ttu-id="cc167-111">혼합된 현실에서 사용자 수 수 쉽게 사항 물리적 환경 또는 개체 앱은 하지 제공 좋은 시각적 피드백 경우.</span><span class="sxs-lookup"><span data-stu-id="cc167-111">In mixed reality users can be easily distracted by physical environment or objects if your app does not gives good visual feedback.</span></span> <span data-ttu-id="cc167-112">몇 초를 사용 하는 경우에 대 한 데이터를 로드 하는 경우와 같이 또는 장면에서 업데이트 하는, 시각적 표시기를 표시 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="cc167-112">For situations that take a few seconds, such when data is loading or a scene is updating, it is good idea to show a visual indicator.</span></span> <span data-ttu-id="cc167-113">작업 진행 중-임을 사용자에 게 표시할 두 가지는 **진행률 표시줄이** 또는 **진행률 링**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc167-113">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

### <a name="progress-bar"></a><span data-ttu-id="cc167-114">진행률 표시줄</span><span class="sxs-lookup"><span data-stu-id="cc167-114">Progress bar</span></span>

![HoloLens에 진행률 표시줄 예제](images/640px-progressbar.jpg)

<span data-ttu-id="cc167-116">진행률 표시줄을 작업의 완료 백분율을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cc167-116">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="cc167-117">작업 시간 (비활성화 상태) 라고 하는 동안 사용 해야 하지만 진행률의 앱을 사용 하 여 사용자의 상호 작용을 차단 하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc167-117">It should be used during an operation whose duration is known (determinate), but it's progress should not block the user's interaction with the app.</span></span>

### <a name="progress-ring"></a><span data-ttu-id="cc167-118">진행률 링</span><span class="sxs-lookup"><span data-stu-id="cc167-118">Progress ring</span></span>

![HoloLens에 진행률 링 예제](images/640px-progressring.jpg)

<span data-ttu-id="cc167-120">진행률 링만 결정 되지 않은 상태 여 서 있으며 추가 사용자 상호 작용은 작업이 완료 될 때까지 차단 되는 경우 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc167-120">A Progress ring only has an indeterminate state, and should be used when any further user interaction is blocked until the operation has completed.</span></span>

### <a name="progress-with-a-custom-object"></a><span data-ttu-id="cc167-121">사용자 지정 개체를 사용 하 여 진행률</span><span class="sxs-lookup"><span data-stu-id="cc167-121">Progress with a custom object</span></span>

![HoloLens에 사용자 지정 메시 예제를 사용 하 여 진행률](images/640px-progresscustom.jpg)

<span data-ttu-id="cc167-123">사용자 고유의 사용자 지정 2D/3D 개체를 사용 하 여 진행률 컨트롤을 사용자 지정 하 여 앱의 개성과 브랜드 id에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc167-123">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span>

## <a name="best-practices"></a><span data-ttu-id="cc167-124">모범 사례</span><span class="sxs-lookup"><span data-stu-id="cc167-124">Best practices</span></span>
* <span data-ttu-id="cc167-125">긴밀 하 게 결합 [빌보드 또는 tag-along](billboarding-and-tag-along.md) 쉽게 해당 헤드 빈 공간으로 이동 하 고 상황에 맞는 손실 수 사용자 이므로 진행률 표시.</span><span class="sxs-lookup"><span data-stu-id="cc167-125">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="cc167-126">앱이에서 반복적인 충돌이 발생 하면 아무 것도 볼 수 없는 경우 처럼 보일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc167-126">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="cc167-127">Billboarding 및 tag-along 진행률 prefab에 빌드됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc167-127">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="cc167-128">항상 사용자에 게 상황에 대 한 상태 정보를 제공 하는 것이 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc167-128">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="cc167-129">진행률 prefab 상태를 제공 하는 데 Windows 표준 링 형식 진행 상황 비롯 한 다양 한 시각적 스타일을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc167-129">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="cc167-130">또한 앱의 브랜드에 맞게 진행 상황의 스타일을 원하는 경우 애니메이션을 사용 하 여 메시를 사용자 지정을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc167-130">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc167-131">참조</span><span class="sxs-lookup"><span data-stu-id="cc167-131">See also</span></span>
* [<span data-ttu-id="cc167-132">진행률 스크립트 및 혼합 현실 도구 키트에서 prefabs</span><span class="sxs-lookup"><span data-stu-id="cc167-132">Progress scripts and prefabs on Mixed Reality Toolkit</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Loader)
* [<span data-ttu-id="cc167-133">경계 상자</span><span class="sxs-lookup"><span data-stu-id="cc167-133">Bounding Box</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="cc167-134">상호 작용 가능한 개체</span><span class="sxs-lookup"><span data-stu-id="cc167-134">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="cc167-135">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="cc167-135">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="cc167-136">빌보딩 및 태그얼롱</span><span class="sxs-lookup"><span data-stu-id="cc167-136">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
