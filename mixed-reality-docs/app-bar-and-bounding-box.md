---
title: 앱 바 및 경계 상자
description: 앱 바에 일련의 단추를 홀로그램 경계 아래쪽 가장자리에 표시 하는 포함 된 개체 수준 메뉴입니다.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 경계 상자 막대는 앱
ms.openlocfilehash: ab472e1c988e6bdfb0a69d90e90280082b3db759
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813871"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="30eb5-104">경계 상자과 앱 표시줄</span><span class="sxs-lookup"><span data-stu-id="30eb5-104">Bounding box and App bar</span></span>
![경계는 혼합 현실에서 개체를 조작 하기 위한 표준 인터페이스입니다.](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="30eb5-106">경계 상자는 무엇입니까?</span><span class="sxs-lookup"><span data-stu-id="30eb5-106">What is the Bounding box?</span></span>

<span data-ttu-id="30eb5-107">경계는 혼합 현실에서 개체를 조작 하기 위한 표준 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="30eb5-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="30eb5-108">개체가 현재 조정할 수는 유도성 사용자를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="30eb5-108">It provides the user an affordance that the object is currently adjustable.</span></span> <span data-ttu-id="30eb5-109">모퉁이 개체 또한 확장할 수는 사용자에 게 알림.</span><span class="sxs-lookup"><span data-stu-id="30eb5-109">The corners tell the user that the object can also scale.</span></span> <span data-ttu-id="30eb5-110">이 visual 유도성 조정 모드를 외부에서 표시 되지 않은 경우에 사용자에 게-개체의 전체 영역을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="30eb5-110">This visual affordance shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="30eb5-111">없었다면 있습니다, 다른 개체 또는 화면에 맞춰 지 개체 있습니다 되지 않아야 하는 주위 공간 것 처럼 동작 처럼 보이기 때문에 특히 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="30eb5-111">This is especially important because if it weren’t there, an object snapped to another object or surface may appear to behave as if there was space around it that shouldn’t be there.</span></span> <span data-ttu-id="30eb5-112">HoloLens 2의 경계 상자 직접 직접 조작 작동 하며 사용자의 손가락의 근접성에 응답 합니다.</span><span class="sxs-lookup"><span data-stu-id="30eb5-112">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="30eb5-113">시각적 피드백을 사용자가 개체의 거리를 인식할 수 있도록 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="30eb5-113">It shows visual feedback to help the user perceive the distance from the object.</span></span> 

<span data-ttu-id="30eb5-114">![HoloLens-의-관점 경계 상자를 통해 개체를 확장 합니다.](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="30eb5-114">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
<span data-ttu-id="30eb5-115">*경계 상자를 통해 개체 크기 조정*</span><span class="sxs-lookup"><span data-stu-id="30eb5-115">*Scaling an object via bounding box*</span></span>

<span data-ttu-id="30eb5-116">경계 상자 모퉁이 핸들 크기 조정에 대 한 광범위 하 게 인식된 패턴을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="30eb5-116">The handles in the corners of the bounding box follow a widely understood pattern for adjusting scale.</span></span> 

<span data-ttu-id="30eb5-117">![HoloLens-의-관점 경계 상자를 통해 개체를 회전](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="30eb5-117">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
<span data-ttu-id="30eb5-118">*경계 상자를 통해 개체를 회전*</span><span class="sxs-lookup"><span data-stu-id="30eb5-118">*Rotating an object via bounding box*</span></span>


<span data-ttu-id="30eb5-119">![직접 근접에 대 한 시각적 피드백](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="30eb5-119">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
<span data-ttu-id="30eb5-120">*근접도에 따라 시각적 피드백*</span><span class="sxs-lookup"><span data-stu-id="30eb5-120">*Visual feedback based on the proximity*</span></span>

<span data-ttu-id="30eb5-121">경계 상자의 가장자리의 세로 사각형 affordances 회전 표시기 됩니다.</span><span class="sxs-lookup"><span data-stu-id="30eb5-121">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="30eb5-122">이렇게 하면 사용자 더 세밀 하 게 조정 해당 배치 홀로그램 위에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="30eb5-122">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="30eb5-123">뿐만 아니라 수 조정 및 확장 있지만 이제도 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="30eb5-123">Not only can they adjust and scale, but now rotate as well.</span></span>

* <span data-ttu-id="30eb5-124">Unity 앱 개발을 위한 참조 [경계 상자 혼합 현실 도구 키트-Unity에서](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)</span><span class="sxs-lookup"><span data-stu-id="30eb5-124">For Unity app development, see [Bounding box on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)</span></span>



## <a name="what-is-the-app-bar"></a><span data-ttu-id="30eb5-125">앱 바는 무엇입니까?</span><span class="sxs-lookup"><span data-stu-id="30eb5-125">What is the App bar?</span></span>

<span data-ttu-id="30eb5-126">앱 바에 일련의 단추를 홀로그램 경계 아래쪽 가장자리에 표시 하는 포함 된 개체 수준 메뉴입니다.</span><span class="sxs-lookup"><span data-stu-id="30eb5-126">The App bar is a object-level menu containing a series of buttons that displays on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="30eb5-127">이 패턴은 일반적으로 사용자를 제거 하 고 홀로그램 조정할 수 있도록 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="30eb5-127">This pattern is commonly used to give users the ability to remove and adjust holograms.</span></span>

<span data-ttu-id="30eb5-128">사용자 개체를 이동 하는 대로 세계를 잠글 수 있는 개체를 사용 하 여이 패턴은 사용 되므로 앱 바 사용자에 게 가장 가까운 개체 측에 항상 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="30eb5-128">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="30eb5-129">이 빌보드 없습니다, 하는 동안 효과적으로 달성을 위해 동일한 결과가 됩니다. 사용자의 채워집니다 위치 또는 될 수 있는 사용 가능한 환경에서 다른 위치에서 블록 기능을 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="30eb5-129">While this isn't billboarding, it effectively achieves the same result; preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span>

<span data-ttu-id="30eb5-130">![홀로그램을 따라 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="30eb5-130">![Walking around a hologram.</span></span> <span data-ttu-id="30eb5-131">앱 바는 다음과 같습니다.](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="30eb5-131">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
<span data-ttu-id="30eb5-132">*앱 바가 따릅니다를 홀로그램을 따라 이동 합니다.*</span><span class="sxs-lookup"><span data-stu-id="30eb5-132">*Walking around a hologram, the App bar follows*</span></span>

<span data-ttu-id="30eb5-133">앱 바는 주로 사용자의 환경에서 가져온된 개체를 관리 하는 방법으로 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="30eb5-133">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="30eb5-134">혼합된 현실에서 개체 지향은 위치와 방법을 완전히 제어할을 사용자가 경계 상자를 사용 하 여 결합 합니다.</span><span class="sxs-lookup"><span data-stu-id="30eb5-134">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

* <span data-ttu-id="30eb5-135">Unity 앱 개발을 위한 참조 [앱 바 혼합 현실 도구 키트-Unity에서](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)</span><span class="sxs-lookup"><span data-stu-id="30eb5-135">For Unity app development, see [App bar on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)</span></span>

## <a name="see-also"></a><span data-ttu-id="30eb5-136">참조</span><span class="sxs-lookup"><span data-stu-id="30eb5-136">See also</span></span>
* [<span data-ttu-id="30eb5-137">상호 작용 가능한 개체</span><span class="sxs-lookup"><span data-stu-id="30eb5-137">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="30eb5-138">Unity의 텍스트</span><span class="sxs-lookup"><span data-stu-id="30eb5-138">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="30eb5-139">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="30eb5-139">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="30eb5-140">진행률 표시</span><span class="sxs-lookup"><span data-stu-id="30eb5-140">Displaying progress</span></span>](progress.md)
