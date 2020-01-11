---
title: 셰이더가
description: MRTK 표준 셰이더는 holograms와 함께 사용할 수 있는 다양 한 유형의 시각적 효과를 제공 합니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: 혼합 현실, 컨트롤, 상호 작용, ui, ux
ms.openlocfilehash: 8d0e01bb26347d95a80703884c4e9408653e03ed
ms.sourcegitcommit: 2bfe9b1af4ee2cc0d668caeccb8ebc3137cbc20b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901451"
---
# <a name="shader"></a><span data-ttu-id="6e016-104">셰이더가</span><span class="sxs-lookup"><span data-stu-id="6e016-104">Shader</span></span>

![셰이더가](images/UX/UX_Hero_StandardShader.jpg)

<span data-ttu-id="6e016-106">Holographic 개체는 실제 환경에서 물리적 개체와 혼합 되므로 사용자에 게 시각적 신호를 제공 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e016-106">Since holographic objects are mixed with physical ones in the real environment, it's important to provide visual cues to the user.</span></span> <span data-ttu-id="6e016-107">MRTK 표준 셰이더는 holograms와 함께 사용할 수 있는 다양 한 유형의 시각적 효과를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e016-107">The MRTK Standard shader provides various types of visual effects that can be used with holograms.</span></span> <span data-ttu-id="6e016-108">MRTK 표준 음영 시스템은 Unity의 표준 셰이더와 유사한 시각적 개체를 사용할 수 있는 유연한 단일 셰이더를 활용 하 고, [흐름 설계 시스템 원칙](https://www.microsoft.com/design/fluent/#/)을 구현 하며, 혼합 현실 장치에 대 한 성능을 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e016-108">The MRTK Standard shading system utilizes a single, flexible shader that can achieve visuals similar to Unity's Standard Shader, implements [Fluent Design System principles](https://www.microsoft.com/design/fluent/#/), and remains performant on mixed reality devices.</span></span>
<br>

## <a name="examples-of-visual-effects-using-mrtk-standard-shader"></a><span data-ttu-id="6e016-109">MRTK 표준 셰이더를 사용 하는 시각적 효과의 예</span><span class="sxs-lookup"><span data-stu-id="6e016-109">Examples of visual effects using MRTK Standard shader</span></span> 
:::row:::
    :::column:::
       <span data-ttu-id="6e016-110">![이동](images/UX/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="6e016-110">![Move](images/UX/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="6e016-111">**근접 조명**</span><span class="sxs-lookup"><span data-stu-id="6e016-111">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="6e016-112">![회전](images/UX/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="6e016-112">![Rotate](images/UX/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="6e016-113">**테두리 라이트**</span><span class="sxs-lookup"><span data-stu-id="6e016-113">**Border light**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="mrtk-standard-shader-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="6e016-114">MRTK의 MRTK 표준 셰이더 (혼합 현실 도구 키트) 및 Unity</span><span class="sxs-lookup"><span data-stu-id="6e016-114">MRTK Standard shader in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="6e016-115">MRTK-표준 셰이더</span><span class="sxs-lookup"><span data-stu-id="6e016-115">MRTK - Standard shader</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)


<br>

---

## <a name="see-also"></a><span data-ttu-id="6e016-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6e016-116">See also</span></span>

* [<span data-ttu-id="6e016-117">커서</span><span class="sxs-lookup"><span data-stu-id="6e016-117">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="6e016-118">손 광선</span><span class="sxs-lookup"><span data-stu-id="6e016-118">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="6e016-119">Button</span><span class="sxs-lookup"><span data-stu-id="6e016-119">Button</span></span>](button.md)
* [<span data-ttu-id="6e016-120">상호 작용 가능한 개체</span><span class="sxs-lookup"><span data-stu-id="6e016-120">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="6e016-121">경계 상자 및 앱 바</span><span class="sxs-lookup"><span data-stu-id="6e016-121">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="6e016-122">조작</span><span class="sxs-lookup"><span data-stu-id="6e016-122">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="6e016-123">손 메뉴</span><span class="sxs-lookup"><span data-stu-id="6e016-123">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="6e016-124">Near 메뉴</span><span class="sxs-lookup"><span data-stu-id="6e016-124">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="6e016-125">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="6e016-125">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="6e016-126">음성 명령</span><span class="sxs-lookup"><span data-stu-id="6e016-126">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="6e016-127">키보드</span><span class="sxs-lookup"><span data-stu-id="6e016-127">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="6e016-128">Tooltip</span><span class="sxs-lookup"><span data-stu-id="6e016-128">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="6e016-129">슬레이트</span><span class="sxs-lookup"><span data-stu-id="6e016-129">Slate</span></span>](slate.md)
* [<span data-ttu-id="6e016-130">슬라이더</span><span class="sxs-lookup"><span data-stu-id="6e016-130">Slider</span></span>](slider.md)
* [<span data-ttu-id="6e016-131">빌보딩 및 태그얼롱</span><span class="sxs-lookup"><span data-stu-id="6e016-131">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="6e016-132">진행률 표시</span><span class="sxs-lookup"><span data-stu-id="6e016-132">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="6e016-133">표면 자성</span><span class="sxs-lookup"><span data-stu-id="6e016-133">Surface magnetism</span></span>](surface-magnetism.md)
