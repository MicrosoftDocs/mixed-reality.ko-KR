---
title: 요소의 정기적 테이블
description: 요소의 정기적 테이블에는 Microsoft의 혼합 현실 디자인 실습 개체 컬렉션을 사용 하 여 다양 한 화면 형식을 사용 하 여 3D 공간에서 개체의 배열에 배치 하는 방법을 알아보십시오 오픈 소스 샘플 앱입니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality를 디자인, 샘플 앱, 컨트롤
ms.openlocfilehash: ad95d2bcfd1b70d805adcceb36be0c6c29b838f0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604113"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="58044-104">요소의 정기적 테이블</span><span class="sxs-lookup"><span data-stu-id="58044-104">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="58044-105">이 문서에서 설명 하는 예비 샘플에 설명 합니다 [혼합 현실 디자인 Labs](https://github.com/Microsoft/MRDesignLabs_Unity)에 대 한 학습 공유 하는 위치 및 제안에 대 한 혼합 현실 앱 개발.</span><span class="sxs-lookup"><span data-stu-id="58044-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="58044-106">이 디자인 관련 문서 및 코드에는 새 검색 우리가 발전할 합니다.</span><span class="sxs-lookup"><span data-stu-id="58044-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="58044-107">[요소의 정기적 테이블](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) 은 Microsoft의 혼합 현실 디자인 실습에서 오픈 소스 샘플 앱입니다.</span><span class="sxs-lookup"><span data-stu-id="58044-107">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is a open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="58044-108">이 프로젝트와 함께 3D 공간에서 개체의 배열을 사용 하 여 다양 한 화면 형식에 배치 하는 방법을 알아볼 수 있습니다는  **[개체 컬렉션](object-collection.md)** 합니다.</span><span class="sxs-lookup"><span data-stu-id="58044-108">With this project, you can learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](object-collection.md)**.</span></span> <span data-ttu-id="58044-109">또한 HoloLens에서 표준 입력에 응답 하는 상호 작용할 수 없는 개체를 만드는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="58044-109">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="58044-110">혼합 현실 앱 환경을 직접 만들어야이 프로젝트의 구성이 요소를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58044-110">You can use this project's components to create your own mixed reality app experience.</span></span>

![요소 앱의 기간 테이블](images/640px-periodictable-hero.jpg)

## <a name="about-the-app"></a><span data-ttu-id="58044-112">앱에 대 한</span><span class="sxs-lookup"><span data-stu-id="58044-112">About the app</span></span>

<span data-ttu-id="58044-113">요소의 정기적 테이블 화학 물 요소 및 각 3D 공간에서 해당 속성을 시각화합니다.</span><span class="sxs-lookup"><span data-stu-id="58044-113">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="58044-114">응시 및 air 탭 같은 HoloLens의 기본 상호 작용을 통합 합니다.</span><span class="sxs-lookup"><span data-stu-id="58044-114">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="58044-115">애니메이션이 적용 된 3D 모델을 사용 하 여 요소에 대 한 사용자 수에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="58044-115">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="58044-116">요소의 전자 셸 및 양성자 및 neutrons로 구성 된 해당 이기-시각적으로 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58044-116">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="58044-117">배경</span><span class="sxs-lookup"><span data-stu-id="58044-117">Background</span></span>

<span data-ttu-id="58044-118">HoloLens, 먼저 양상이 주기적 table 앱 혼합된 현실에서 실험 하려고 하는 것이 필자의 아이디어가 했습니다.</span><span class="sxs-lookup"><span data-stu-id="58044-118">After I first experienced HoloLens, a periodic table app was an idea I knew that I wanted to experiment with in mixed reality.</span></span> <span data-ttu-id="58044-119">각 요소에 텍스트를 사용 하 여 표시 되는 많은 데이터 요소, 3D 공간에서 인쇄 컴퍼지션을 탐색 하는 데 유용한 주제 것 생각 했습니다.</span><span class="sxs-lookup"><span data-stu-id="58044-119">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="58044-120">이 프로젝트의 다른 흥미로운 부분은 된 시각화 요소의 전자 모델 수입니다.</span><span class="sxs-lookup"><span data-stu-id="58044-120">Being able to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="58044-121">디자인</span><span class="sxs-lookup"><span data-stu-id="58044-121">Design</span></span>

<span data-ttu-id="58044-122">주기적 테이블의 기본 보기의 경우 내를 포함 하는 각 요소의 전자 모델 3 차원 상자 생각 합니다.</span><span class="sxs-lookup"><span data-stu-id="58044-122">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="58044-123">사용자 요소의 볼륨의 대략적인 아이디어를 얻을 수 있도록 각 상자의 화면 반투명 것입니다.</span><span class="sxs-lookup"><span data-stu-id="58044-123">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="58044-124">응시 및 air 탭을 사용 하 여 사용자의 각 요소에 대해 자세히 예기치 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58044-124">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="58044-125">테이블 뷰 및 세부 정보 보기 간 전환을 원활 하 고 자연 스러운가 하도록 만들었습니다 실생활에서 열기 상자 물리적 상호 작용 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="58044-125">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="58044-126">![디자인 스케치](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="58044-126">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="58044-127">*디자인 스케치*</span><span class="sxs-lookup"><span data-stu-id="58044-127">*Design sketches*</span></span>

<span data-ttu-id="58044-128">자세히 보기 상태의 3D 공간에서 멋지게 렌더링 된 텍스트를 사용 하 여 각 요소의 정보를 시각화 하고자 했습니다.</span><span class="sxs-lookup"><span data-stu-id="58044-128">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="58044-129">애니메이션이 적용 된 3D 전자 모델 가운데 영역에서 표시 되 고 다른 관점에서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58044-129">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![조작](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="58044-131">![프로토타입](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="58044-131">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="58044-132">*상호 작용 프로토타입*</span><span class="sxs-lookup"><span data-stu-id="58044-132">*Interaction prototypes*</span></span>

<span data-ttu-id="58044-133">사용자 테이블의 아래쪽에 있는 단추 탭으로 화면 형식을 변경할 수-평면, 원통형, 구 및 분산형 간에 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58044-133">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="58044-134">공용 컨트롤 및이 앱에서 사용 되는 패턴</span><span class="sxs-lookup"><span data-stu-id="58044-134">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="58044-135">상호 작용할 수 없는 개체 (단추)</span><span class="sxs-lookup"><span data-stu-id="58044-135">Interactable object (button)</span></span>

<span data-ttu-id="58044-136">[상호 작용할 수 없는 개체](interactable-object.md) 는 기본 HoloLens 입력에 응답할 수 있는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="58044-136">[Interactable object](interactable-object.md) is an object which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="58044-137">모든 개체에 쉽게 적용할 수 있는 prefab 스크립트로 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="58044-137">It is provided as a prefab/script which you can easily apply to any object.</span></span> <span data-ttu-id="58044-138">예를 들어, 커피 cup 장면에서 상호 작용할 수 없는 응시, 어 탭 제스처를 탐색 및 조작 등의 입력에 응답 합니다.</span><span class="sxs-lookup"><span data-stu-id="58044-138">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation and manipulation gestures.</span></span> [<span data-ttu-id="58044-139">자세히 알아보기</span><span class="sxs-lookup"><span data-stu-id="58044-139">Learn more</span></span>](interactable-object.md)

![nteractable 개체](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="58044-141">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="58044-141">Object collection</span></span>

<span data-ttu-id="58044-142">[개체 컬렉션](object-collection.md) 개체인 다양 한 모양의 여러 개체를 레이아웃 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="58044-142">[Object collection](object-collection.md) is an object which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="58044-143">평면, 원통형, 구 및 분산형 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="58044-143">It supports plane, cylinder, sphere and scatter.</span></span> <span data-ttu-id="58044-144">Radius, 행 및 간격 수가 같은 추가 속성을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58044-144">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="58044-145">자세히 알아보기</span><span class="sxs-lookup"><span data-stu-id="58044-145">Learn more</span></span>](object-collection.md)

![개체 컬렉션](images/640px-periodictable-collections.jpg)

### <a name="fitbox"></a><span data-ttu-id="58044-147">Fitbox</span><span class="sxs-lookup"><span data-stu-id="58044-147">Fitbox</span></span>

<span data-ttu-id="58044-148">사용자는 gazing 있는 위치에 배치 됩니다 홀로그램 기본적으로 현재 응용 프로그램이 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="58044-148">By default, holograms will be placed in the location where the user is gazing at the moment the application is launched.</span></span> <span data-ttu-id="58044-149">이 경우에 따라 홀로그램 벽 뒤 또는 테이블을 가운데에 배치 되 고 같은 원치 않는 결과로 이어집니다.</span><span class="sxs-lookup"><span data-stu-id="58044-149">This sometimes leads to unwanted result such as holograms being placed behind a wall or in the middle of a table.</span></span> <span data-ttu-id="58044-150">fitbox 게이즈를 홀로그램을 배치할 위치를 결정 하는 데 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58044-150">A fitbox allows a user to use gaze to determine the location where the hologram will be placed.</span></span> <span data-ttu-id="58044-151">사용자 고유의 이미지 또는 3D 개체를 사용 하 여 손쉽게 사용자 지정할 수 있는 간단한 PNG 이미지 질감으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="58044-151">It is made with a simple PNG image texture which can be easily customized with your own images or 3D objects.</span></span>

![Fitbox](images/450px-periodictable-fitbox.jpg)

## <a name="technical-details"></a><span data-ttu-id="58044-153">기술 세부 정보</span><span class="sxs-lookup"><span data-stu-id="58044-153">Technical details</span></span>

<span data-ttu-id="58044-154">스크립트 및 있습니다 prefabs 요소 앱의 정기적 테이블에 [혼합 현실 디자인 Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)합니다.</span><span class="sxs-lookup"><span data-stu-id="58044-154">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="application-examples"></a><span data-ttu-id="58044-155">응용 프로그램 예제</span><span class="sxs-lookup"><span data-stu-id="58044-155">Application examples</span></span>

<span data-ttu-id="58044-156">이 프로젝트의 구성 요소를 활용 하 여 만들 수에 대 한 몇 가지 아이디어는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="58044-156">Here are some ideas for what you could create by leveraging the components in this project.</span></span>

### <a name="stock-data-visualization-app"></a><span data-ttu-id="58044-157">주식 데이터 시각화 앱</span><span class="sxs-lookup"><span data-stu-id="58044-157">Stock data visualization app</span></span>

<span data-ttu-id="58044-158">동일한 컨트롤과 상호 작용 모델을 사용 하 여 요소 샘플 주기적 테이블로, 주식 시장 데이터를 시각화 하는 앱을 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58044-158">Using the same controls and interaction model as the Periodic Table of the Elements sample, you could build an app which visualizes stock market data.</span></span> <span data-ttu-id="58044-159">이 예제에서는 구면 셰이프에서 주식 데이터를 레이아웃할 수 개체 컬렉션 컨트롤을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="58044-159">This example uses the Object collection control to lay out stock data in a spherical shape.</span></span> <span data-ttu-id="58044-160">흥미로운 방식으로 각 주식에 대 한 추가 정보를 표시할 수 있는 세부 정보 보기를 상상할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58044-160">You can imagine a detail view where additional information about each stock could be displayed in an interesting way.</span></span>

![응용 프로그램 예제: 재무 (1 / 3)](images/640px-periodictable-applicationexamples-finance1.jpg)

![응용 프로그램 예제: 재무 (2 / 3)](images/640px-periodictable-applicationexamples-finance2.jpg)

<span data-ttu-id="58044-163">![응용 프로그램 예제: 재무 (3 / 3)](images/640px-periodictable-applicationexamples-finance3.jpg)</span><span class="sxs-lookup"><span data-stu-id="58044-163">![Application example: Finance (3 of 3)](images/640px-periodictable-applicationexamples-finance3.jpg)</span></span><br>
<span data-ttu-id="58044-164">*요소 샘플 앱의 정기적 테이블에 사용 되는 개체 컬렉션 재무 응용 프로그램에서 어떻게 사용할 수 있습니다의 예*</span><span class="sxs-lookup"><span data-stu-id="58044-164">*An example of how the Object collection used in the Periodic Table of the Elements sample app could be used in a finance app*</span></span>

### <a name="sports-app"></a><span data-ttu-id="58044-165">스포츠 앱</span><span class="sxs-lookup"><span data-stu-id="58044-165">Sports app</span></span>

<span data-ttu-id="58044-166">이것이 스포츠 데이터 개체 컬렉션 및 기타 구성 요소 샘플 앱의 정기적 테이블에서 요소를 사용 하 여 시각화의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="58044-166">This is an example of visualizing sports data using Object collection and other components from the Periodic Table of the Elements sample app.</span></span>

![응용 프로그램 예제: 스포츠 (1 / 3)](images/640px-periodictable-applicationexamples-sports0.jpg)

![응용 프로그램 예제: 스포츠 (2 / 3)](images/640px-periodictable-applicationexamples-sports1.jpg)

<span data-ttu-id="58044-169">![응용 프로그램 예제: 스포츠 (3 / 3)](images/640px-periodictable-applicationexamples-sports3.jpg)</span><span class="sxs-lookup"><span data-stu-id="58044-169">![Application example: Sports (3 of 3)](images/640px-periodictable-applicationexamples-sports3.jpg)</span></span><br>
<span data-ttu-id="58044-170">*요소 샘플 appcould의 주기적 테이블에 있는 개체 컬렉션을 사용 하는 방법의 예로 스포츠 앱에서 사용할 수*</span><span class="sxs-lookup"><span data-stu-id="58044-170">*An example of how the Object collection used in the Periodic Table of the Elements sample appcould be used in a sports app*</span></span>

## <a name="about-the-author"></a><span data-ttu-id="58044-171">저자 소개</span><span class="sxs-lookup"><span data-stu-id="58044-171">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="58044-172"><b>했어요 Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="58044-172"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="58044-173">UX 디자이너 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="58044-173">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="58044-174">참조</span><span class="sxs-lookup"><span data-stu-id="58044-174">See also</span></span>

* [<span data-ttu-id="58044-175">상호 작용할 수 없는 개체</span><span class="sxs-lookup"><span data-stu-id="58044-175">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="58044-176">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="58044-176">Object collection</span></span>](object-collection.md)
