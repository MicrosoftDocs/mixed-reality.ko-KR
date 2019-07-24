---
title: 경계 상자 및 앱 바
description: 앱 바는 홀로그램 범위의 아래쪽 가장자리에 표시 되는 일련의 단추를 포함 하는 개체 수준 메뉴입니다.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, 앱 바, 경계 상자
ms.openlocfilehash: d289be31129324c6ff419b69dbce52bd8f62eb64
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829677"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="50987-104">경계 상자 및 앱 바</span><span class="sxs-lookup"><span data-stu-id="50987-104">Bounding box and App bar</span></span>
![경계는 혼합 현실에서 개체 조작을 위한 표준 인터페이스입니다.](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="50987-106">경계 상자는 무엇 인가요?</span><span class="sxs-lookup"><span data-stu-id="50987-106">What is the Bounding box?</span></span>

<span data-ttu-id="50987-107">경계는 혼합 현실에서 개체 조작을 위한 표준 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="50987-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="50987-108">사용자에 게 개체를 현재 조정할 수 있는 affordance 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="50987-108">It provides the user an affordance that the object is currently adjustable.</span></span> <span data-ttu-id="50987-109">모퉁이는 개체의 크기를 조정할 수도 있음을 사용자에 게 알려줍니다.</span><span class="sxs-lookup"><span data-stu-id="50987-109">The corners tell the user that the object can also scale.</span></span> <span data-ttu-id="50987-110">이 시각적 개체는 조정 모드 외부에 표시 되지 않는 경우에도 사용자에 게 개체의 전체 영역을 affordance 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="50987-110">This visual affordance shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="50987-111">이는 해당 개체가 없는 경우 다른 개체 또는 표면에 맞춰진 개체가 거기에 있어서는 안 되는 것 처럼 동작 하는 것 처럼 보일 수 있으므로 특히 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="50987-111">This is especially important because if it weren’t there, an object snapped to another object or surface may appear to behave as if there was space around it that shouldn’t be there.</span></span> <span data-ttu-id="50987-112">HoloLens 2에서 경계 상자는 직접 조작을 사용 하 여 작동 하며 사용자의 finger's 근접에 응답 합니다.</span><span class="sxs-lookup"><span data-stu-id="50987-112">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="50987-113">사용자가 개체의 거리를 파악 하는 데 도움이 되는 시각적 피드백을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="50987-113">It shows visual feedback to help the user perceive the distance from the object.</span></span> 

<span data-ttu-id="50987-114">![경계 상자를 통해 개체 크기를 조정 하는 HoloLens 관점](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="50987-114">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
<span data-ttu-id="50987-115">*경계 상자를 통해 개체 크기 조정*</span><span class="sxs-lookup"><span data-stu-id="50987-115">*Scaling an object via bounding box*</span></span>

<span data-ttu-id="50987-116">경계 상자 모퉁이의 핸들은 크기 조정을 조정 하기 위해 널리 이해 되는 패턴을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="50987-116">The handles in the corners of the bounding box follow a widely understood pattern for adjusting scale.</span></span> 

<span data-ttu-id="50987-117">![경계 상자를 통해 개체를 회전 하는 HoloLens 관점](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="50987-117">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
<span data-ttu-id="50987-118">*경계 상자를 통해 개체 회전*</span><span class="sxs-lookup"><span data-stu-id="50987-118">*Rotating an object via bounding box*</span></span>


<span data-ttu-id="50987-119">![근접 한 시각적 피드백](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="50987-119">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
<span data-ttu-id="50987-120">*근접을 기준으로 시각적 피드백*</span><span class="sxs-lookup"><span data-stu-id="50987-120">*Visual feedback based on the proximity*</span></span>

<span data-ttu-id="50987-121">경계 상자 가장자리의 세로 사각형 affordances 회전 표시기입니다.</span><span class="sxs-lookup"><span data-stu-id="50987-121">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="50987-122">이렇게 하면 사용자가 배치 된 holograms을 보다 세부적으로 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50987-122">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="50987-123">조정 하 고 크기를 조정할 수 있을 뿐만 아니라 이제 회전도 가능 합니다.</span><span class="sxs-lookup"><span data-stu-id="50987-123">Not only can they adjust and scale, but now rotate as well.</span></span>

* <span data-ttu-id="50987-124">Unity 앱 개발의 경우 [혼합 현실 도구 키트의 경계 상자-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="50987-124">For Unity app development, see [Bounding box on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)</span></span>



## <a name="what-is-the-app-bar"></a><span data-ttu-id="50987-125">앱 바 란?</span><span class="sxs-lookup"><span data-stu-id="50987-125">What is the App bar?</span></span>

<span data-ttu-id="50987-126">앱 바는 홀로그램 범위의 아래쪽 가장자리에 표시 되는 일련의 단추를 포함 하는 개체 수준 메뉴입니다.</span><span class="sxs-lookup"><span data-stu-id="50987-126">The App bar is a object-level menu containing a series of buttons that displays on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="50987-127">이 패턴은 사용자에 게 holograms를 제거 하 고 조정 하는 기능을 제공 하는 데 일반적으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50987-127">This pattern is commonly used to give users the ability to remove and adjust holograms.</span></span>

<span data-ttu-id="50987-128">이 패턴은 세계에서 잠긴 개체와 함께 사용 되므로 사용자가 개체를 이동할 때 앱 바는 항상 사용자에 게 가장 가까운 개체 쪽에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50987-128">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="50987-129">이는 billboarding 되지 않지만 실제로 동일한 결과를 얻는 것입니다. 사용자의 위치를 려 하거나 환경의 다른 위치에서 사용할 수 있는 기능을 차단 합니다.</span><span class="sxs-lookup"><span data-stu-id="50987-129">While this isn't billboarding, it effectively achieves the same result; preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span>

<span data-ttu-id="50987-130">![홀로그램을 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="50987-130">![Walking around a hologram.</span></span> <span data-ttu-id="50987-131">앱 바는 다음과 같습니다.](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="50987-131">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
<span data-ttu-id="50987-132">*홀로그램을 탐색 하는 동안 앱 바는 다음과 같습니다.*</span><span class="sxs-lookup"><span data-stu-id="50987-132">*Walking around a hologram, the App bar follows*</span></span>

<span data-ttu-id="50987-133">앱 바는 주로 사용자 환경에서 배치 된 개체를 관리 하는 방법으로 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="50987-133">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="50987-134">경계 상자와 함께 사용 하는 경우 사용자는 혼합 현실에서 개체의 방향 및 위치를 완전히 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50987-134">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

* <span data-ttu-id="50987-135">Unity 앱 개발의 경우 [혼합 현실 도구 키트의 앱 바-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="50987-135">For Unity app development, see [App bar on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)</span></span>

## <a name="see-also"></a><span data-ttu-id="50987-136">참조</span><span class="sxs-lookup"><span data-stu-id="50987-136">See also</span></span>
* [<span data-ttu-id="50987-137">상호 작용 가능한 개체</span><span class="sxs-lookup"><span data-stu-id="50987-137">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="50987-138">Unity의 텍스트</span><span class="sxs-lookup"><span data-stu-id="50987-138">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="50987-139">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="50987-139">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="50987-140">진행률 표시</span><span class="sxs-lookup"><span data-stu-id="50987-140">Displaying progress</span></span>](progress.md)
