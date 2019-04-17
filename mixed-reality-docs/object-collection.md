---
title: 개체 컬렉션
description: 개체 컬렉션에는 미리 정의 된 3 차원 도형에 있는 개체의 배열을 레이아웃할 수 있는 레이아웃 컨트롤입니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality를 컨트롤 디자인
ms.openlocfilehash: 88ab0359d5083d43d5d6312ef1185f67ca0caa7d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605012"
---
# <a name="object-collection"></a><span data-ttu-id="553f3-104">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="553f3-104">Object collection</span></span>

<span data-ttu-id="553f3-105">개체 컬렉션에는 미리 정의 된 3 차원 도형에 있는 개체의 배열을 레이아웃할 수 있는 레이아웃 컨트롤입니다.</span><span class="sxs-lookup"><span data-stu-id="553f3-105">Object collection is a layout control which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="553f3-106">네 가지 다른 화면 스타일-지원 **평면, 원기둥 구체** 하 고 **분산형**합니다.</span><span class="sxs-lookup"><span data-stu-id="553f3-106">It supports four different surface styles - **plane, cylinder, sphere** and **scatter**.</span></span> <span data-ttu-id="553f3-107">Radius 및 개체 및 이들 간의 공간 크기를 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="553f3-107">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="553f3-108">개체 컬렉션의 Unity-2D 및 3D 개체를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="553f3-108">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="553f3-109">에  **[혼합 현실 Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_ObjectCollection.md)**, Unity 스크립트를 만들었습니다 및 [예제 장면](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Scenes/ObjectCollectionExample.unity) 개체 컬렉션을 만들 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="553f3-109">In the **[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_ObjectCollection.md)**, we have created Unity script and [example scene](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Scenes/ObjectCollectionExample.unity) that will help you create an object collection.</span></span>

<span data-ttu-id="553f3-110">![요소 앱의 정기적 표에 사용 되는 개체 컬렉션](images/640px-objectcollection-hero-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="553f3-110">![Object collection used in the Periodic Table of the Elements app](images/640px-objectcollection-hero-640px.jpg)</span></span><br>
<span data-ttu-id="553f3-111">*요소 샘플 앱의 정기적 표에 사용 되는 개체 컬렉션*</span><span class="sxs-lookup"><span data-stu-id="553f3-111">*Object collection used in the Periodic Table of the Elements sample app*</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="553f3-112">개체 컬렉션 예제</span><span class="sxs-lookup"><span data-stu-id="553f3-112">Object collection examples</span></span>

<span data-ttu-id="553f3-113">[요소의 정기적 테이블](periodic-table-of-the-elements.md) 은 개체 컬렉션의 작동 원리를 보여 주는 샘플 앱입니다.</span><span class="sxs-lookup"><span data-stu-id="553f3-113">[Periodic Table of the Elements](periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="553f3-114">다른 셰이프에서 3D 화학 물 요소 상자 레이아웃 개체 컬렉션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="553f3-114">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="553f3-115">![요소 앱의 정기적 표에 표시 된 개체 컬렉션 예제](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="553f3-115">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="553f3-116">*요소 샘플 앱의 정기적 표에 표시 된 개체 컬렉션 예제*</span><span class="sxs-lookup"><span data-stu-id="553f3-116">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="553f3-117">3D 개체</span><span class="sxs-lookup"><span data-stu-id="553f3-117">3D objects</span></span>

<span data-ttu-id="553f3-118">가져온된 3D 개체의 레이아웃에 개체 컬렉션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="553f3-118">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="553f3-119">아래 예제에서는 일부 chair 3D 개체의 원기둥 레이아웃과 평면을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="553f3-119">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="553f3-120">![평면 및 3D 개체의 원통형 레이아웃의 예](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="553f3-120">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="553f3-121">*평면 및 3D 개체의 원통형 레이아웃의 예*</span><span class="sxs-lookup"><span data-stu-id="553f3-121">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="553f3-122">2D 개체</span><span class="sxs-lookup"><span data-stu-id="553f3-122">2D objects</span></span>

<span data-ttu-id="553f3-123">또한 개체 컬렉션을 사용 하 여 2D 이미지를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="553f3-123">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="553f3-124">아래 예제에서는 어떻게 2D 이미지를 보여 줍니다. 표에 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="553f3-124">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![개체 컬렉션을 사용 하 여 2D 이미지의 예](images/640px-layout-3dobjects-3.jpg)

<span data-ttu-id="553f3-126">![개체 컬렉션을 사용 하 여 2D 이미지의 예](images/640px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="553f3-126">![An example of 2D images with Object collection](images/640px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="553f3-127">*개체 컬렉션을 사용 하 여 2D 이미지의 예*</span><span class="sxs-lookup"><span data-stu-id="553f3-127">*Examples of 2D images with object collection*</span></span>

## <a name="see-also"></a><span data-ttu-id="553f3-128">참조</span><span class="sxs-lookup"><span data-stu-id="553f3-128">See also</span></span>
* [<span data-ttu-id="553f3-129">스크립트 및 GitHub의 혼합 현실 도구 키트의 개체 컬렉션에 대 한 prefabs</span><span class="sxs-lookup"><span data-stu-id="553f3-129">Scripts and prefabs for Object collection in the Mixed Reality Toolkit on GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)
* [<span data-ttu-id="553f3-130">상호 작용할 수 없는 개체</span><span class="sxs-lookup"><span data-stu-id="553f3-130">Interactable object</span></span>](interactable-object.md)
