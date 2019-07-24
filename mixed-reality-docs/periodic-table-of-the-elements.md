---
title: 원소의 주기율표
description: 요소의 정기 테이블은 Microsoft의 혼합 현실 디자인 랩에서 오픈 소스 샘플 앱으로, 개체 컬렉션을 사용 하 여 다양 한 표면 유형을 포함 하는 3D 공간에서 개체의 배열을 레이아웃 하는 방법을 배울 수 있습니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 디자인, 샘플 앱, 컨트롤
ms.openlocfilehash: ad95d2bcfd1b70d805adcceb36be0c6c29b838f0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63525330"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="be323-104">원소의 주기율표</span><span class="sxs-lookup"><span data-stu-id="be323-104">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="be323-105">이 문서에서는 혼합 현실 앱 개발에 대 한 학습 정보 및 제안을 공유 하는 위치를 [혼합 현실 디자인 랩에서](https://github.com/Microsoft/MRDesignLabs_Unity)만든 예비 샘플에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="be323-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="be323-106">디자인 관련 문서와 코드는 새로운 검색을 수행할 때 개선 됩니다.</span><span class="sxs-lookup"><span data-stu-id="be323-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="be323-107">[요소의 정기 테이블](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) 은 Microsoft의 혼합 현실 디자인 랩에서 오픈 소스 샘플 앱입니다.</span><span class="sxs-lookup"><span data-stu-id="be323-107">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is a open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="be323-108">이 프로젝트를 사용 하 여 **[개체 컬렉션](object-collection.md)** 을 사용 하는 다양 한 표면 형식으로 3d 공간에서 개체의 배열을 레이아웃 하는 방법을 배울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be323-108">With this project, you can learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](object-collection.md)**.</span></span> <span data-ttu-id="be323-109">또한 HoloLens에서 표준 입력에 응답 하는 interactable 개체를 만드는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="be323-109">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="be323-110">이 프로젝트의 구성 요소를 사용 하 여 혼합 현실 앱 환경을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be323-110">You can use this project's components to create your own mixed reality app experience.</span></span>

![요소 앱의 기간 테이블](images/640px-periodictable-hero.jpg)

## <a name="about-the-app"></a><span data-ttu-id="be323-112">앱 정보</span><span class="sxs-lookup"><span data-stu-id="be323-112">About the app</span></span>

<span data-ttu-id="be323-113">요소의 주기적 테이블은 시각화 요소와 각 속성을 3D 공간에 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="be323-113">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="be323-114">이 도구는 응시 및 air 탭과 같은 HoloLens의 기본 상호 작용을 통합 합니다.</span><span class="sxs-lookup"><span data-stu-id="be323-114">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="be323-115">사용자는 애니메이션 3D 모델을 사용 하 여 요소에 대해 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be323-115">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="be323-116">이러한 사용자는 protons 및 neutrons로 구성 된 요소의 전자 핵심 이기를 시각적으로 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be323-116">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="be323-117">배경</span><span class="sxs-lookup"><span data-stu-id="be323-117">Background</span></span>

<span data-ttu-id="be323-118">HoloLens를 처음 경험 하 고 나면, 정기적 테이블 앱은 혼합 현실에서 시험해 보고 싶을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="be323-118">After I first experienced HoloLens, a periodic table app was an idea I knew that I wanted to experiment with in mixed reality.</span></span> <span data-ttu-id="be323-119">각 요소에는 텍스트와 함께 표시 되는 데이터 요소가 많기 때문에 3D 공간에서 입력 컴퍼지션을 탐색 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="be323-119">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="be323-120">요소의 전자 모델을 시각화할 수 있는 것은이 프로젝트의 또 다른 흥미로운 부분 이었습니다.</span><span class="sxs-lookup"><span data-stu-id="be323-120">Being able to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="be323-121">디자인</span><span class="sxs-lookup"><span data-stu-id="be323-121">Design</span></span>

<span data-ttu-id="be323-122">정기적 테이블의 기본 보기에서는 각 요소의 전자 모델을 포함 하는 3 차원 상자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be323-122">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="be323-123">사용자가 요소의 볼륨에 대 한 대략적인 아이디어를 얻을 수 있도록 각 상자의 표면이 반투명 하 게 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="be323-123">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="be323-124">사용자는 응시 및 air 탭을 사용 하 여 각 요소의 자세히 보기를 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be323-124">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="be323-125">테이블 뷰와 자세히 보기를 자연스럽 고 자연스럽 게 전환 하기 위해 실시간으로 열리는 상자의 물리적 상호 작용과 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="be323-125">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="be323-126">![스케치 디자인](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="be323-126">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="be323-127">*디자인 스케치*</span><span class="sxs-lookup"><span data-stu-id="be323-127">*Design sketches*</span></span>

<span data-ttu-id="be323-128">자세히 보기에서는 원활 렌더링 된 텍스트를 사용 하 여 각 요소의 정보를 3D 공간에 시각화 하고자 했습니다.</span><span class="sxs-lookup"><span data-stu-id="be323-128">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="be323-129">애니메이션 3D 전자 모델은 가운데 영역에 표시 되며 다른 각도에서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be323-129">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![조작](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="be323-131">![모델링할](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="be323-131">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="be323-132">*상호 작용 프로토타입*</span><span class="sxs-lookup"><span data-stu-id="be323-132">*Interaction prototypes*</span></span>

<span data-ttu-id="be323-133">사용자는 테이블 아래쪽의 단추를 눌러 표면 유형을 변경할 수 있습니다. 평면, 원통, 구 및 산 사이를 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be323-133">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="be323-134">이 응용 프로그램에서 사용 되는 공용 컨트롤 및 패턴</span><span class="sxs-lookup"><span data-stu-id="be323-134">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="be323-135">Interactable 개체 (button)</span><span class="sxs-lookup"><span data-stu-id="be323-135">Interactable object (button)</span></span>

<span data-ttu-id="be323-136">[Interactable 개체](interactable-object.md) 는 기본 HoloLens 입력에 응답할 수 있는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="be323-136">[Interactable object](interactable-object.md) is an object which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="be323-137">모든 개체에 쉽게 적용할 수 있는 prefab/스크립트로 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="be323-137">It is provided as a prefab/script which you can easily apply to any object.</span></span> <span data-ttu-id="be323-138">예를 들어 장면 interactable에서 커피 컵을 만들고 응시, 공중 탭, 탐색 및 조작 제스처와 같은 입력에 응답할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be323-138">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation and manipulation gestures.</span></span> [<span data-ttu-id="be323-139">자세히 알아보기</span><span class="sxs-lookup"><span data-stu-id="be323-139">Learn more</span></span>](interactable-object.md)

![nteractable 개체](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="be323-141">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="be323-141">Object collection</span></span>

<span data-ttu-id="be323-142">[개체 컬렉션](object-collection.md) 은 다양 한 셰이프에서 여러 개체의 레이아웃을 설정 하는 데 도움이 되는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="be323-142">[Object collection](object-collection.md) is an object which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="be323-143">평면, 원통, 구 및 산을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="be323-143">It supports plane, cylinder, sphere and scatter.</span></span> <span data-ttu-id="be323-144">Radius, 행 수 및 간격과 같은 추가 속성을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be323-144">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="be323-145">자세히 알아보기</span><span class="sxs-lookup"><span data-stu-id="be323-145">Learn more</span></span>](object-collection.md)

![개체 컬렉션](images/640px-periodictable-collections.jpg)

### <a name="fitbox"></a><span data-ttu-id="be323-147">Fitbox</span><span class="sxs-lookup"><span data-stu-id="be323-147">Fitbox</span></span>

<span data-ttu-id="be323-148">기본적으로 holograms는 사용자가 응용 프로그램을 시작 하는 순간 gazing 위치에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="be323-148">By default, holograms will be placed in the location where the user is gazing at the moment the application is launched.</span></span> <span data-ttu-id="be323-149">이로 인해 holograms는 벽 뒤 나 테이블의 중간에 배치 되는 것과 같은 원치 않는 결과가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be323-149">This sometimes leads to unwanted result such as holograms being placed behind a wall or in the middle of a table.</span></span> <span data-ttu-id="be323-150">Fitbox를 사용 하면 사용자는 응시를 사용 하 여 홀로그램이 배치 될 위치를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be323-150">A fitbox allows a user to use gaze to determine the location where the hologram will be placed.</span></span> <span data-ttu-id="be323-151">이 이미지는 고유한 이미지 또는 3D 개체를 사용 하 여 쉽게 사용자 지정할 수 있는 간단한 PNG 이미지 질감으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="be323-151">It is made with a simple PNG image texture which can be easily customized with your own images or 3D objects.</span></span>

![Fitbox](images/450px-periodictable-fitbox.jpg)

## <a name="technical-details"></a><span data-ttu-id="be323-153">기술 세부 정보</span><span class="sxs-lookup"><span data-stu-id="be323-153">Technical details</span></span>

<span data-ttu-id="be323-154">[혼합 현실 디자인 실험 GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)에서 Elements 앱의 주기 테이블에 대 한 스크립트 및 prefabs를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be323-154">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="application-examples"></a><span data-ttu-id="be323-155">응용 프로그램 예제</span><span class="sxs-lookup"><span data-stu-id="be323-155">Application examples</span></span>

<span data-ttu-id="be323-156">이 프로젝트의 구성 요소를 활용 하 여 만들 수 있는 작업에 대 한 몇 가지 아이디어는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="be323-156">Here are some ideas for what you could create by leveraging the components in this project.</span></span>

### <a name="stock-data-visualization-app"></a><span data-ttu-id="be323-157">재고 데이터 시각화 앱</span><span class="sxs-lookup"><span data-stu-id="be323-157">Stock data visualization app</span></span>

<span data-ttu-id="be323-158">요소 샘플의 주기 테이블과 동일한 컨트롤 및 상호 작용 모델을 사용 하 여 주식 시장 데이터를 시각화 하는 앱을 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be323-158">Using the same controls and interaction model as the Periodic Table of the Elements sample, you could build an app which visualizes stock market data.</span></span> <span data-ttu-id="be323-159">이 예제에서는 개체 컬렉션 컨트롤을 사용 하 여 구면 셰이프의 재고 데이터를 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="be323-159">This example uses the Object collection control to lay out stock data in a spherical shape.</span></span> <span data-ttu-id="be323-160">각 주식에 대 한 추가 정보가 흥미로운 방식으로 표시 되는 세부 정보 보기를 생각해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be323-160">You can imagine a detail view where additional information about each stock could be displayed in an interesting way.</span></span>

![응용 프로그램 예: 재무 (1/3)](images/640px-periodictable-applicationexamples-finance1.jpg)

![응용 프로그램 예: 재무 (2/3)](images/640px-periodictable-applicationexamples-finance2.jpg)

<span data-ttu-id="be323-163">![응용 프로그램 예: 재무 (3/3)](images/640px-periodictable-applicationexamples-finance3.jpg)</span><span class="sxs-lookup"><span data-stu-id="be323-163">![Application example: Finance (3 of 3)](images/640px-periodictable-applicationexamples-finance3.jpg)</span></span><br>
<span data-ttu-id="be323-164">*요소 샘플 앱의 주기 테이블에 사용 되는 개체 컬렉션을 재무 앱에서 사용 하는 방법의 예*</span><span class="sxs-lookup"><span data-stu-id="be323-164">*An example of how the Object collection used in the Periodic Table of the Elements sample app could be used in a finance app*</span></span>

### <a name="sports-app"></a><span data-ttu-id="be323-165">스포츠 앱</span><span class="sxs-lookup"><span data-stu-id="be323-165">Sports app</span></span>

<span data-ttu-id="be323-166">다음은 요소 샘플 앱의 주기 테이블에서 개체 컬렉션 및 기타 구성 요소를 사용 하 여 스포츠 데이터를 시각화 하는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="be323-166">This is an example of visualizing sports data using Object collection and other components from the Periodic Table of the Elements sample app.</span></span>

![응용 프로그램 예: 스포츠 (1/3)](images/640px-periodictable-applicationexamples-sports0.jpg)

![응용 프로그램 예: 스포츠 (2/3)](images/640px-periodictable-applicationexamples-sports1.jpg)

<span data-ttu-id="be323-169">![응용 프로그램 예: 스포츠 (3/3)](images/640px-periodictable-applicationexamples-sports3.jpg)</span><span class="sxs-lookup"><span data-stu-id="be323-169">![Application example: Sports (3 of 3)](images/640px-periodictable-applicationexamples-sports3.jpg)</span></span><br>
<span data-ttu-id="be323-170">*샘플 appcould의 주기 테이블에 사용 되는 개체 컬렉션을 스포츠 앱에서 사용 하는 방법의 예*</span><span class="sxs-lookup"><span data-stu-id="be323-170">*An example of how the Object collection used in the Periodic Table of the Elements sample appcould be used in a sports app*</span></span>

## <a name="about-the-author"></a><span data-ttu-id="be323-171">작성자 정보</span><span class="sxs-lookup"><span data-stu-id="be323-171">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="be323-172"><b>동 Yoon 공원</b></span><span class="sxs-lookup"><span data-stu-id="be323-172"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="be323-173">UX 디자이너@Microsoft</span><span class="sxs-lookup"><span data-stu-id="be323-173">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="be323-174">참조</span><span class="sxs-lookup"><span data-stu-id="be323-174">See also</span></span>

* [<span data-ttu-id="be323-175">상호 작용 가능한 개체</span><span class="sxs-lookup"><span data-stu-id="be323-175">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="be323-176">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="be323-176">Object collection</span></span>](object-collection.md)
