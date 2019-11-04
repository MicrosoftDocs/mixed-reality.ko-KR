---
title: 개체 컬렉션
description: 개체 컬렉션은 미리 정의 된 3 차원 도형에서 개체의 배열을 레이아웃 하는 데 도움이 되는 레이아웃 컨트롤입니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 컨트롤, 디자인
ms.openlocfilehash: 8f3629c6d9465383efc901ed784a3719cd6fdfb2
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438183"
---
# <a name="object-collection"></a><span data-ttu-id="1efe4-104">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="1efe4-104">Object collection</span></span>

![Elements app의 주기 테이블에 사용 되는 개체 컬렉션입니다.](images/640px-objectcollection-hero-640px.jpg)<br>


<span data-ttu-id="1efe4-106">개체 컬렉션은 미리 정의 된 3 차원 도형에서 개체의 배열을 레이아웃 하는 데 도움이 되는 레이아웃 컨트롤입니다.</span><span class="sxs-lookup"><span data-stu-id="1efe4-106">Object collection is a layout control which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="1efe4-107">이 도구는 다양 한 표면 스타일, 즉 **평면, 원통, 구** 및 **방사형**을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="1efe4-107">It supports various surface styles - **plane, cylinder, sphere** and **radial**.</span></span> <span data-ttu-id="1efe4-108">개체의 반지름과 크기와 개체 사이의 간격을 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1efe4-108">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="1efe4-109">개체 컬렉션은 Unity의 모든 개체 (2D 및 3D)를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="1efe4-109">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="1efe4-110">**[혼합 현실 도구 키트](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)** 에서 개체 컬렉션을 만드는 데 도움이 되는 Unity 스크립트와 예제를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="1efe4-110">In the **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)**, we have created Unity script and examples that will help you create an object collection.</span></span>


## <a name="object-collection-examples"></a><span data-ttu-id="1efe4-111">개체 컬렉션 예제</span><span class="sxs-lookup"><span data-stu-id="1efe4-111">Object collection examples</span></span>

<span data-ttu-id="1efe4-112">[요소의 정기 테이블](periodic-table-of-the-elements.md) 은 개체 컬렉션의 작동 방식을 보여 주는 샘플 앱입니다.</span><span class="sxs-lookup"><span data-stu-id="1efe4-112">[Periodic Table of the Elements](periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="1efe4-113">개체 컬렉션을 사용 하 여 여러 도형의 3D 화학 요소 상자에 레이아웃을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1efe4-113">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="1efe4-114">요소 앱의 주기 테이블에 표시 되는 개체 컬렉션 예 ![](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="1efe4-114">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="1efe4-115">*요소 샘플 앱의 주기 테이블에 표시 되는 개체 컬렉션 예*</span><span class="sxs-lookup"><span data-stu-id="1efe4-115">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="1efe4-116">3D 개체</span><span class="sxs-lookup"><span data-stu-id="1efe4-116">3D objects</span></span>

<span data-ttu-id="1efe4-117">개체 컬렉션을 사용 하 여 가져온 3D 개체의 레이아웃을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1efe4-117">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="1efe4-118">아래 예제에서는 일부 3D의 개체 개체에 대 한 평면과 실린더 레이아웃을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1efe4-118">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="1efe4-119">3D 개체의 평면 및 원통형 레이아웃 예제를 ![](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="1efe4-119">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="1efe4-120">*3D 개체의 평면 및 원통형 레이아웃 예*</span><span class="sxs-lookup"><span data-stu-id="1efe4-120">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="1efe4-121">2D 개체</span><span class="sxs-lookup"><span data-stu-id="1efe4-121">2D objects</span></span>

<span data-ttu-id="1efe4-122">또한 개체 컬렉션에서 2D 이미지를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1efe4-122">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="1efe4-123">아래 예제에서는 2D 이미지를 모눈에 표시 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1efe4-123">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![개체 컬렉션을 사용 하는 2D 이미지의 예](images/940px-layout-3dobjects-3.jpg)

<span data-ttu-id="1efe4-125">개체 컬렉션을 사용 하 여 2D 이미지의 예제를 ![](images/940px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="1efe4-125">![An example of 2D images with Object collection](images/940px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="1efe4-126">*2D 이미지를 사용 하 여 개체 컬렉션을 사용 하는 예제*</span><span class="sxs-lookup"><span data-stu-id="1efe4-126">*Examples of using object collection with 2D images*</span></span>

## <a name="see-also"></a><span data-ttu-id="1efe4-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1efe4-127">See also</span></span>
* [<span data-ttu-id="1efe4-128">GitHub의 Mixed Reality 도구 키트에 있는 개체 컬렉션에 대 한 스크립트 및 prefabs</span><span class="sxs-lookup"><span data-stu-id="1efe4-128">Scripts and prefabs for Object collection in the Mixed Reality Toolkit on GitHub</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_ObjectCollection.md)
* [<span data-ttu-id="1efe4-129">상호 작용 가능한 개체</span><span class="sxs-lookup"><span data-stu-id="1efe4-129">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="1efe4-130">경계 상자</span><span class="sxs-lookup"><span data-stu-id="1efe4-130">Bounding Box</span></span>](app-bar-and-bounding-box.md)
