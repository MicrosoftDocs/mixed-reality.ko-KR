---
title: 셰이더가
description: ''
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: 혼합 현실, 컨트롤, 상호 작용, ui, ux
ms.openlocfilehash: 23371ae5d70e5e792415fd25c0d58def0a7cefbb
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143273"
---
# <a name="shader"></a><span data-ttu-id="7c5f8-103">셰이더가</span><span class="sxs-lookup"><span data-stu-id="7c5f8-103">Shader</span></span>

![셰이더가](images/UX/UX_Hero_StandardShader.jpg)

<span data-ttu-id="7c5f8-105">Holographic 개체는 환경의 물리적 항목과 혼합 되므로 혼합 현실에서는 시각적 신호를 제공 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c5f8-105">Since holographic objects are mixed with the physical ones in the environment, providing visual cue is important in mixed reality.</span></span> <span data-ttu-id="7c5f8-106">MRTK 표준 셰이더는 holograms와 함께 사용할 수 있는 다양 한 유형의 시각적 효과를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c5f8-106">MRTK Standard shader provides various types of visual effects that can be used with holograms.</span></span> <span data-ttu-id="7c5f8-107">MRTK 표준 음영 시스템은 Unity의 표준 셰이더와 유사한 시각적 개체를 구현 하 고, 흐름 설계 시스템 원칙을 구현 하 고, 혼합 현실 장치에 대 한 성능 상태를 유지할 수 있는 유연한 단일 셰이더를 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7c5f8-107">MRTK Standard shading system utilizes a single, flexible shader that can achieve visuals similar to Unity's Standard Shader, implement Fluent Design System principles, and remain performant on mixed reality devices.</span></span>
<br>

## <a name="examples-of-visual-effects-using-mrtk-standard-shader"></a><span data-ttu-id="7c5f8-108">MRTK 표준 셰이더를 사용 하는 시각적 효과의 예</span><span class="sxs-lookup"><span data-stu-id="7c5f8-108">Examples of visual effects using MRTK Standard shader</span></span> 
:::row:::
    :::column:::
       <span data-ttu-id="7c5f8-109">![이동](images/UX/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="7c5f8-109">![Move](images/UX/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="7c5f8-110">**근접 조명**</span><span class="sxs-lookup"><span data-stu-id="7c5f8-110">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="7c5f8-111">![회전](images/UX/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="7c5f8-111">![Rotate](images/UX/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="7c5f8-112">**테두리 라이트**</span><span class="sxs-lookup"><span data-stu-id="7c5f8-112">**Border light**</span></span><br>
    :::column-end:::
:::row-end:::

---

## <a name="mrtk-standard-shader-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="7c5f8-113">MRTK의 MRTK 표준 셰이더 (혼합 현실 도구 키트) 및 Unity</span><span class="sxs-lookup"><span data-stu-id="7c5f8-113">MRTK Standard shader in MRTK(Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="7c5f8-114">MRTK-표준 셰이더</span><span class="sxs-lookup"><span data-stu-id="7c5f8-114">MRTK - Standard shader</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)


<br>

---

## <a name="see-also"></a><span data-ttu-id="7c5f8-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7c5f8-115">See also</span></span>

* [<span data-ttu-id="7c5f8-116">커서</span><span class="sxs-lookup"><span data-stu-id="7c5f8-116">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="7c5f8-117">손 광선</span><span class="sxs-lookup"><span data-stu-id="7c5f8-117">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="7c5f8-118">Button</span><span class="sxs-lookup"><span data-stu-id="7c5f8-118">Button</span></span>](button.md)
* [<span data-ttu-id="7c5f8-119">상호 작용 가능한 개체</span><span class="sxs-lookup"><span data-stu-id="7c5f8-119">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="7c5f8-120">경계 상자 및 앱 바</span><span class="sxs-lookup"><span data-stu-id="7c5f8-120">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="7c5f8-121">조작</span><span class="sxs-lookup"><span data-stu-id="7c5f8-121">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="7c5f8-122">손 메뉴</span><span class="sxs-lookup"><span data-stu-id="7c5f8-122">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="7c5f8-123">Near 메뉴</span><span class="sxs-lookup"><span data-stu-id="7c5f8-123">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="7c5f8-124">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="7c5f8-124">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="7c5f8-125">음성 명령</span><span class="sxs-lookup"><span data-stu-id="7c5f8-125">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="7c5f8-126">키보드</span><span class="sxs-lookup"><span data-stu-id="7c5f8-126">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="7c5f8-127">Tooltip</span><span class="sxs-lookup"><span data-stu-id="7c5f8-127">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="7c5f8-128">슬레이트</span><span class="sxs-lookup"><span data-stu-id="7c5f8-128">Slate</span></span>](slate.md)
* [<span data-ttu-id="7c5f8-129">슬라이더</span><span class="sxs-lookup"><span data-stu-id="7c5f8-129">Slider</span></span>](slider.md)
* [<span data-ttu-id="7c5f8-130">빌보딩 및 태그얼롱</span><span class="sxs-lookup"><span data-stu-id="7c5f8-130">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="7c5f8-131">진행률 표시</span><span class="sxs-lookup"><span data-stu-id="7c5f8-131">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="7c5f8-132">표면 자성</span><span class="sxs-lookup"><span data-stu-id="7c5f8-132">Surface magnetism</span></span>](surface-magnetism.md)
