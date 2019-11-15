---
title: 개체 컬렉션
description: 개체 컬렉션은 미리 정의 된 3 차원 도형에서 개체의 배열을 레이아웃 하는 데 도움이 되는 레이아웃 컨트롤입니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 컨트롤, 디자인
ms.openlocfilehash: 98fec76558502658511faf3f18d623bfa5a49dc2
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/15/2019
ms.locfileid: "74106006"
---
# <a name="object-collection"></a><span data-ttu-id="b39ed-104">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="b39ed-104">Object collection</span></span>

![Elements app의 주기 테이블에 사용 되는 개체 컬렉션입니다.](images/UX/UX_Hero_ObjectCollection.jpg)<br>


<span data-ttu-id="b39ed-106">개체 컬렉션은 미리 정의 된 3 차원 도형에서 개체의 배열을 레이아웃 하는 데 도움이 되는 레이아웃 컨트롤입니다.</span><span class="sxs-lookup"><span data-stu-id="b39ed-106">Object collection is a layout control which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="b39ed-107">이 도구는 다양 한 표면 스타일, 즉 **평면, 원통, 구** 및 **방사형**을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="b39ed-107">It supports various surface styles - **plane, cylinder, sphere** and **radial**.</span></span> <span data-ttu-id="b39ed-108">개체의 반지름과 크기와 개체 사이의 간격을 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b39ed-108">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="b39ed-109">개체 컬렉션은 Unity의 모든 개체 (2D 및 3D)를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="b39ed-109">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="b39ed-110">**[혼합 현실 도구 키트](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)** 에서 개체 컬렉션을 만드는 데 도움이 되는 Unity 스크립트와 예제를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="b39ed-110">In the **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)**, we have created Unity script and examples that will help you create an object collection.</span></span>


## <a name="object-collection-examples"></a><span data-ttu-id="b39ed-111">개체 컬렉션 예제</span><span class="sxs-lookup"><span data-stu-id="b39ed-111">Object collection examples</span></span>

<span data-ttu-id="b39ed-112">[요소의 정기 테이블](periodic-table-of-the-elements.md) 은 개체 컬렉션의 작동 방식을 보여 주는 샘플 앱입니다.</span><span class="sxs-lookup"><span data-stu-id="b39ed-112">[Periodic Table of the Elements](periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="b39ed-113">개체 컬렉션을 사용 하 여 여러 도형의 3D 화학 요소 상자에 레이아웃을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b39ed-113">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="b39ed-114">요소 앱의 주기 테이블에 표시 되는 개체 컬렉션 예 ![](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="b39ed-114">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="b39ed-115">*요소 샘플 앱의 주기 테이블에 표시 되는 개체 컬렉션 예*</span><span class="sxs-lookup"><span data-stu-id="b39ed-115">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="b39ed-116">3D 개체</span><span class="sxs-lookup"><span data-stu-id="b39ed-116">3D objects</span></span>

<span data-ttu-id="b39ed-117">개체 컬렉션을 사용 하 여 가져온 3D 개체의 레이아웃을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b39ed-117">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="b39ed-118">아래 예제에서는 일부 3D의 개체 개체에 대 한 평면과 실린더 레이아웃을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b39ed-118">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="b39ed-119">3D 개체의 평면 및 원통형 레이아웃 예제를 ![](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="b39ed-119">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="b39ed-120">*3D 개체의 평면 및 원통형 레이아웃 예*</span><span class="sxs-lookup"><span data-stu-id="b39ed-120">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="b39ed-121">2D 개체</span><span class="sxs-lookup"><span data-stu-id="b39ed-121">2D objects</span></span>

<span data-ttu-id="b39ed-122">또한 개체 컬렉션에서 2D 이미지를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b39ed-122">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="b39ed-123">아래 예제에서는 2D 이미지를 모눈에 표시 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b39ed-123">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![개체 컬렉션을 사용 하는 2D 이미지의 예](images/940px-layout-3dobjects-3.jpg)

<span data-ttu-id="b39ed-125">개체 컬렉션을 사용 하 여 2D 이미지의 예제를 ![](images/940px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="b39ed-125">![An example of 2D images with Object collection](images/940px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="b39ed-126">*2D 이미지를 사용 하 여 개체 컬렉션을 사용 하는 예제*</span><span class="sxs-lookup"><span data-stu-id="b39ed-126">*Examples of using object collection with 2D images*</span></span>

<br>

---

## <a name="object-collection-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="b39ed-127">Unity 용 MRTK (Mixed Reality Toolkit)의 개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="b39ed-127">Object collection in MRTK(Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="b39ed-128">MRTK-개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="b39ed-128">MRTK - Object collection</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)


<br>

---


## <a name="see-also"></a><span data-ttu-id="b39ed-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b39ed-129">See also</span></span>

* [<span data-ttu-id="b39ed-130">커서</span><span class="sxs-lookup"><span data-stu-id="b39ed-130">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="b39ed-131">손 모양</span><span class="sxs-lookup"><span data-stu-id="b39ed-131">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="b39ed-132">Button</span><span class="sxs-lookup"><span data-stu-id="b39ed-132">Button</span></span>](button.md)
* [<span data-ttu-id="b39ed-133">상호 작용 가능한 개체</span><span class="sxs-lookup"><span data-stu-id="b39ed-133">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="b39ed-134">경계 상자 및 앱 바</span><span class="sxs-lookup"><span data-stu-id="b39ed-134">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="b39ed-135">조작은</span><span class="sxs-lookup"><span data-stu-id="b39ed-135">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="b39ed-136">손 메뉴</span><span class="sxs-lookup"><span data-stu-id="b39ed-136">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="b39ed-137">메뉴 근처</span><span class="sxs-lookup"><span data-stu-id="b39ed-137">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="b39ed-138">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="b39ed-138">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="b39ed-139">음성 명령</span><span class="sxs-lookup"><span data-stu-id="b39ed-139">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="b39ed-140">키보드</span><span class="sxs-lookup"><span data-stu-id="b39ed-140">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="b39ed-141">놓으면</span><span class="sxs-lookup"><span data-stu-id="b39ed-141">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="b39ed-142">찬</span><span class="sxs-lookup"><span data-stu-id="b39ed-142">Slate</span></span>](slate.md)
* [<span data-ttu-id="b39ed-143">슬라이더</span><span class="sxs-lookup"><span data-stu-id="b39ed-143">Slider</span></span>](slider.md)
* [<span data-ttu-id="b39ed-144">빌보딩 및 태그얼롱</span><span class="sxs-lookup"><span data-stu-id="b39ed-144">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="b39ed-145">진행률 표시</span><span class="sxs-lookup"><span data-stu-id="b39ed-145">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="b39ed-146">표면 자기</span><span class="sxs-lookup"><span data-stu-id="b39ed-146">Surface magnetism</span></span>](surface-magnetism.md)
