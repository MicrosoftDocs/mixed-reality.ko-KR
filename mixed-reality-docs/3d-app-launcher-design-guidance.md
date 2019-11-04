---
title: 3D 앱 시작 관리자 디자인 지침
description: 3D 앱 시작 관리자는 응용 프로그램을 시작 하도록 선택할 수 있는 사용자의 혼합 현실 집에 있는 "물리적" 개체입니다.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 디자인, 3D 앱 시작 관리자, 모던 헤드셋, 라이브 큐브
ms.openlocfilehash: ce9d242e26d67c8fe5af7ac32f4e910a15715d25
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437226"
---
# <a name="3d-app-launcher-design-guidance"></a><span data-ttu-id="e3e69-104">3D 앱 시작 관리자 디자인 지침</span><span class="sxs-lookup"><span data-stu-id="e3e69-104">3D app launcher design guidance</span></span>

<span data-ttu-id="e3e69-105">Windows Mixed Reality 몰입 (VR) 헤드셋에 배치 하는 경우에는 산 및 물로 둘러싸인 절벽에 집으로 시각화 된 Windows Mixed Reality 홈을 입력 합니다 ( [다른 환경을 선택 하 고 직접 만들](add-custom-home-environments.md)수도 있음).</span><span class="sxs-lookup"><span data-stu-id="e3e69-105">When you put on a Windows Mixed Reality immersive (VR) headset, you enter the Windows Mixed Reality home, visualized as a house on a cliff surrounded by mountains and water (though you can [choose other environments and even create your own](add-custom-home-environments.md)).</span></span> <span data-ttu-id="e3e69-106">이 홈의 공간 내에서 사용자가 원하는 방식으로 관심 있는 3D 개체와 앱을 자유롭게 정렬 하 고 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-106">Within the space of this home, a user is free to arrange and organize the 3D objects and apps that they care about any way they want.</span></span> <span data-ttu-id="e3e69-107">**3d 앱 시작 관리자** 는 응용 프로그램을 시작 하도록 선택할 수 있는 사용자의 혼합 현실 집에 있는 "물리적" 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-107">A **3D app launcher** is a “physical” object in the user’s mixed reality house that they can select to launch an app.</span></span>

<span data-ttu-id="e3e69-108">![예: Floaty Bird 3D 앱 시작 관리자](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e3e69-108">![Example: Floaty Bird 3D app launcher](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="e3e69-109">*Floaty Bird 3D 앱 시작 관리자 예제 (가상 앱)*</span><span class="sxs-lookup"><span data-stu-id="e3e69-109">*Floaty Bird 3D app launcher example (fictional app)*</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="e3e69-110">3D 앱 시작 관리자 만들기 프로세스</span><span class="sxs-lookup"><span data-stu-id="e3e69-110">3D app launcher creation process</span></span>

<span data-ttu-id="e3e69-111">3D 앱 시작 관리자를 만드는 단계는 세 가지입니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-111">There are 3 steps to creating a 3D app launcher:</span></span>
1. <span data-ttu-id="e3e69-112">디자인 및 concepting (이 문서)</span><span class="sxs-lookup"><span data-stu-id="e3e69-112">Designing and concepting (this article)</span></span>
2. [<span data-ttu-id="e3e69-113">모델링 및 내보내기</span><span class="sxs-lookup"><span data-stu-id="e3e69-113">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="e3e69-114">응용 프로그램에 통합:</span><span class="sxs-lookup"><span data-stu-id="e3e69-114">Integrating it into your application:</span></span>
    * [<span data-ttu-id="e3e69-115">UWP 앱</span><span class="sxs-lookup"><span data-stu-id="e3e69-115">UWP apps</span></span>](implementing-3d-app-launchers.md)
    * [<span data-ttu-id="e3e69-116">Win32 앱</span><span class="sxs-lookup"><span data-stu-id="e3e69-116">Win32 apps</span></span>](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a><span data-ttu-id="e3e69-117">디자인 개념</span><span class="sxs-lookup"><span data-stu-id="e3e69-117">Design concepts</span></span>

### <a name="fantastic-yet-familiar"></a><span data-ttu-id="e3e69-118">잘 알고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-118">Fantastic yet familiar</span></span>

<span data-ttu-id="e3e69-119">앱 시작 관리자가 거주 하는 Windows Mixed Reality 환경은 fantastical/좋아하는 파트에 대해 잘 알고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-119">The Windows Mixed Reality environment your app launcher lives in is part familiar, part fantastical/sci-fi.</span></span> <span data-ttu-id="e3e69-120">최상의 실행 기가이 세계의 규칙을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-120">The best launchers follow the rules of this world.</span></span> <span data-ttu-id="e3e69-121">앱에서 친숙 한 대표 개체를 사용할 수 있는 방법을 생각해 볼 수 있지만 실제 현실에 대 한 일부 규칙은 벤드 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-121">Think of how you can take a familiar, representative object from your app, but bend some of the rules of actual reality.</span></span> <span data-ttu-id="e3e69-122">마법이 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-122">Magic will result.</span></span>

### <a name="intuitive"></a><span data-ttu-id="e3e69-123">간단</span><span class="sxs-lookup"><span data-stu-id="e3e69-123">Intuitive</span></span>

<span data-ttu-id="e3e69-124">앱 시작 관리자를 살펴보면 앱을 시작 하는 용도는 명확 하 고 혼동이 발생 해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-124">When you look at your app launcher, its purpose - to launch your app - should be obvious and shouldn’t cause any confusion.</span></span> <span data-ttu-id="e3e69-125">예를 들어, 관리자가 절벽 집에서 décor 부분에 대해 혼란 스 럽 지 않을 수 있는 명확 하 고 충분 한 앱 대표 인지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-125">For example, be sure your launcher is an obvious-enough representative of your app that it won’t be confused for a piece of decor in the Cliff House.</span></span> <span data-ttu-id="e3e69-126">앱 시작 관리자는 사용자에 게 연락 하 여 사용자를 초대 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-126">Your app launcher should invite people to touch/select it.</span></span>

<span data-ttu-id="e3e69-127">![예제: 최신 메모 3D 앱 시작 관리자](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e3e69-127">![Example: Fresh Note 3D app launcher](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="e3e69-128">*최신 참고 3D 앱 시작 관리자 예제 (가상 앱)*</span><span class="sxs-lookup"><span data-stu-id="e3e69-128">*Fresh Note 3D app launcher example (fictional app)*</span></span>

### <a name="home-scale"></a><span data-ttu-id="e3e69-129">홈 크기 조정</span><span class="sxs-lookup"><span data-stu-id="e3e69-129">Home scale</span></span>

<span data-ttu-id="e3e69-130">3D 앱 시작은 절벽 집에서 라이브 되며 기본 크기는 공간의 다른 "물리적" 개체에 적합 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-130">3D app launchers live in the Cliff House and their default size should make sense with the other “physical” objects in the space.</span></span> <span data-ttu-id="e3e69-131">집 식물 또는 일부 가구 옆에 시작 관리자를 배치 하면 집, 크기를 중심으로 느낌을 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-131">If you place your launcher beside, say, a house plant or some furniture, it should feel at home, size-wise.</span></span> <span data-ttu-id="e3e69-132">시작 하는 것은 30 평방 센티미터를 확인 하는 것 이지만 사용자가 원하는 경우 규모를 확장 하거나 축소할 수 있다는 점을 명심 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-132">A good starting point is to see how it looks at 30 cubic centimeters, but remember that users can scale it up or down if they like.</span></span>

### <a name="own-able"></a><span data-ttu-id="e3e69-133">소유 가능</span><span class="sxs-lookup"><span data-stu-id="e3e69-133">Own-able</span></span>

<span data-ttu-id="e3e69-134">앱 시작 관리자는 사람들의 공간에 있을 것으로 기대 하는 개체와 같은 느낌을 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-134">The app launcher should feel like an object a person would be excited to have in their space.</span></span> <span data-ttu-id="e3e69-135">이러한 작업은 실질적으로 이러한 작업을 수행 하기 때문에 사용자가 자유롭게 검색 하 고 가까이 유지할 수 있었던 것 처럼 보입니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-135">They’ll be virtually surrounding themselves with these things, so the launcher should feel like something the user thought was desirable enough to seek out and keep nearby.</span></span>

<span data-ttu-id="e3e69-136">![예: Astro 구부리기 3D 앱 시작 관리자](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e3e69-136">![Example: Astro Warp 3D app launcher](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="e3e69-137">*Astro 구부리기 3D 앱 시작 관리자 예제 (가상 앱)*</span><span class="sxs-lookup"><span data-stu-id="e3e69-137">*Astro Warp 3D app launcher example (fictional app)*</span></span>

### <a name="recognizable"></a><span data-ttu-id="e3e69-138">읽을</span><span class="sxs-lookup"><span data-stu-id="e3e69-138">Recognizable</span></span>

<span data-ttu-id="e3e69-139">3D 앱 시작 관리자는 "자신의 앱의 브랜드"를 표시 하는 사용자에 게 즉시 표현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-139">Your 3D app launcher should instantly express “your app’s brand” to people who see it.</span></span> <span data-ttu-id="e3e69-140">앱에 별표 (\*) 또는 특별히 식별 가능한 개체가 있는 경우 디자인의 큰 부분으로 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-140">If you have a star character or an especially identifiable object in your app, we recommend using that as a big part of your design.</span></span> <span data-ttu-id="e3e69-141">혼합 현실 세계에서 개체는 단지 로고만이 아닌 사용자에 게 더 많은 관심을 그리도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-141">In a mixed reality world, an object will draw more interest from users than just a logo alone.</span></span> <span data-ttu-id="e3e69-142">인식 가능한 개체는 신속 하 고 명확 하 게 브랜드를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-142">Recognizable objects communicate brand quickly and clearly.</span></span>

### <a name="volumetric"></a><span data-ttu-id="e3e69-143">대규모</span><span class="sxs-lookup"><span data-stu-id="e3e69-143">Volumetric</span></span>

<span data-ttu-id="e3e69-144">앱은 기본 평면에 로고를 배치 하 고 하루에 호출 하는 것 보다 더 많은 것이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-144">Your app deserves more than just putting your logo on a flat plane and calling it a day.</span></span> <span data-ttu-id="e3e69-145">시작 관리자는 사용자의 공간에서 흥미로운 3D의 실제 개체와 같은 느낌을 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-145">Your launcher should feel like an exciting, 3D, physical object in the user’s space.</span></span> <span data-ttu-id="e3e69-146">좋은 방법은 앱이 Macy의 추수 퍼레이드에서 풍선을 사용 한다고 가정 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-146">A good approach is to imagine your app was going to have a balloon in the Macy’s Thanksgiving Day Parade.</span></span> <span data-ttu-id="e3e69-147">사용자에 게 질문을 하 고 나 서 몇 분 동안에는 어떻게 해야 하나요?</span><span class="sxs-lookup"><span data-stu-id="e3e69-147">Ask yourself, what would really wow people as it came down the street?</span></span> <span data-ttu-id="e3e69-148">모든 보기 각도에서 크게 보이는 것은 무엇 인가요?</span><span class="sxs-lookup"><span data-stu-id="e3e69-148">What would look great from all viewing angles?</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="e3e69-149">*로고 전용](images/20171016-140436-mixedreality-640px.jpg) ![* 로고</span><span class="sxs-lookup"><span data-stu-id="e3e69-149">![Logo only](images/20171016-140436-mixedreality-640px.jpg) *Logo only*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e3e69-150">문자를 사용 하 여 더 쉽게 인식할 ![문자](images/20171016-140557-mixedreality-640px.jpg) *인식*</span><span class="sxs-lookup"><span data-stu-id="e3e69-150">![More recognizable with a character](images/20171016-140557-mixedreality-640px.jpg) *More recognizable with a character*</span></span>
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
        <span data-ttu-id="e3e69-151">![플랫 접근 방법, 즉, 느낌이 좋은 플랫](images/20171016-155101-mixedreality-640px.jpg) *플랫 접근 방식이* 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-151">![Flat approach, not surprisingly, feels flat](images/20171016-155101-mixedreality-640px.jpg) *Flat approach, not surprisingly, feels flat*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e3e69-152">![대규모 접근 방식을 사용 하면 앱을 보다 잘 파악할](images/20171016-161407-mixedreality-640px.jpg) *대규모 접근 방법을* 더 잘 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-152">![Volumetric approach better showcases your app](images/20171016-161407-mixedreality-640px.jpg) *Volumetric approach better showcases your app*</span></span>
    :::column-end:::
:::row-end:::


## <a name="tips-for-good-3d-models"></a><span data-ttu-id="e3e69-153">좋은 3D 모델에 대 한 팁</span><span class="sxs-lookup"><span data-stu-id="e3e69-153">Tips for good 3D models</span></span>

### <a name="best-practices"></a><span data-ttu-id="e3e69-154">모범 사례</span><span class="sxs-lookup"><span data-stu-id="e3e69-154">Best practices</span></span>
* <span data-ttu-id="e3e69-155">앱 시작 관리자에 대 한 차원을 계획할 때 약 30cm 큐브를 촬영 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-155">When planning dimensions for your app launcher, shoot for roughly a 30cm cube.</span></span> <span data-ttu-id="e3e69-156">따라서 1:1:1 크기 비율입니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-156">So, a 1:1:1 size ratio.</span></span>
* <span data-ttu-id="e3e69-157">모델은 1만 polygon 미만 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-157">Models must be under 10,000 polygons.</span></span> [<span data-ttu-id="e3e69-158">삼각형 개수 및 세부 정보 수준에 대 한 자세한 정보 (LODs)</span><span class="sxs-lookup"><span data-stu-id="e3e69-158">Learn more about triangle counts and levels of details (LODs)</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* <span data-ttu-id="e3e69-159">가능 하면 몰입 형 헤드셋에서 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-159">Test on an immersive headset when possible.</span></span>
* <span data-ttu-id="e3e69-160">가능 하면 모델의 기 하 도형에 세부 정보를 빌드 하세요. 자세한 내용은 질감을 사용 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="e3e69-160">Build details into your model’s geometry where possible – don’t rely on textures for detail.</span></span>
* <span data-ttu-id="e3e69-161">"물 근접" 폐쇄형 기 하 도형을 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-161">Build “water tight” closed geometry.</span></span> <span data-ttu-id="e3e69-162">에서 모델링 되지 않은 구멍이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-162">No holes that are not modeled in.</span></span>
* <span data-ttu-id="e3e69-163">개체의 기본 자료를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-163">Use natural materials in your object.</span></span> <span data-ttu-id="e3e69-164">실제 세계에서 크 래 프 트를 만들어 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-164">Imagine crafting it in the real world.</span></span>
* <span data-ttu-id="e3e69-165">모델이 다른 거리와 크기에서 잘 읽도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-165">Make sure your model reads well at different distances and sizes.</span></span>
* <span data-ttu-id="e3e69-166">모델을 이동할 준비가 되 면 [자산 내보내기 지침](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e3e69-166">When your model is ready to go, read the [exporting assets guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).</span></span>

<span data-ttu-id="e3e69-167">질감에서 미묘한 세부 정보를 포함 하는 ![모델](images/20171013-143334-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e3e69-167">![Model with subtle details in the texture](images/20171013-143334-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="e3e69-168">*질감에서 미묘한 세부 정보를 포함 하는 모델*</span><span class="sxs-lookup"><span data-stu-id="e3e69-168">*Model with subtle details in the texture*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="e3e69-169">피해 야 할 사항</span><span class="sxs-lookup"><span data-stu-id="e3e69-169">What to avoid</span></span>
* <span data-ttu-id="e3e69-170">고대비 세부 정보 또는 작은 사용 중 패턴과 텍스처를 사용 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="e3e69-170">Don't use high-contrast details or small, busy patterns and textures.</span></span>
* <span data-ttu-id="e3e69-171">씬 geometry를 사용 하지 마세요. 거리가 적절 하 게 작동 하지 않고 별칭이 잘못 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-171">Don't use thin geometry – it doesn’t work well at a distance and will alias badly.</span></span>
* <span data-ttu-id="e3e69-172">모델의 일부가 1:1:1 크기 비율을 초과 하 여 너무 많이 확장 되는 것을 허용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-172">Don't let parts of your model extend too much beyond the 1:1:1 size ratio.</span></span> <span data-ttu-id="e3e69-173">크기 조정 문제를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-173">It will create scaling problems.</span></span>

<span data-ttu-id="e3e69-174">고대비, 사용량이 적은 패턴을 방지 ![](images/20171013-143603-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e3e69-174">![Avoid high-contrast, small busy patterns](images/20171013-143603-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="e3e69-175">*고대비, 작은 사용 중 패턴 방지*</span><span class="sxs-lookup"><span data-stu-id="e3e69-175">*Avoid high-contrast, small, busy patterns*</span></span>

## <a name="how-to-handle-type"></a><span data-ttu-id="e3e69-176">형식을 처리 하는 방법</span><span class="sxs-lookup"><span data-stu-id="e3e69-176">How to handle type</span></span>

### <a name="best-practices"></a><span data-ttu-id="e3e69-177">모범 사례</span><span class="sxs-lookup"><span data-stu-id="e3e69-177">Best practices</span></span>
* <span data-ttu-id="e3e69-178">앱 시작 관리자 (또는 그 이상)의 1/3에 대 한 형식을 구성 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-178">We recommend your type comprises about 1/3 of your app launcher (or more).</span></span> <span data-ttu-id="e3e69-179">사용자는 시작 관리자가 실제로 시작 관리자 임을 알 수 있도록 하는 주요 사항은 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-179">Type is the main thing that gives people an idea that your launcher is, in fact, a launcher so it’s nice if it’s pretty substantial.</span></span>
* <span data-ttu-id="e3e69-180">Super wide를 사용 하지 마십시오. 앱 시작 전 코어 차원의 범위 내에 유지 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-180">Avoid making type super wide – try to keep it within the confines of the app launchers core dimensions (more or less).</span></span>
* <span data-ttu-id="e3e69-181">플랫 형식이 작동할 수 있지만 특정 환경 및 특정 환경에서 보는 것은 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-181">Flat type can work, but be aware that it can be hard to view from certain angles and in certain environments.</span></span> <span data-ttu-id="e3e69-182">이를 지원 하기 위해이를 solid 개체 또는 배경으로 배치 하는 것을 고려할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-182">You might consider putting it a solid object or backdrop behind it to help with this.</span></span>
* <span data-ttu-id="e3e69-183">3D에서 형식에 차원을 추가 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-183">Adding dimension to your type feels nice in 3D.</span></span> <span data-ttu-id="e3e69-184">형식의 면을 다른 색으로 음영을 사용 하면 가독성을 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-184">Shading the sides of the type a different, darker color can help with readability.</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="e3e69-185">배경 없이 ![플랫 유형을 사용 하면 특정 각도에서 볼 수 있을 수 있으며 특정 환경에서 *배경이 없는 플랫 유형을](images/flattype-640px.png) 특정 각도 및 특정 환경에서 표시 하기가 어려울 수 있습니다\* .</span><span class="sxs-lookup"><span data-stu-id="e3e69-185">![Flat type without a backdrop can be hard to view from certain angles and in certain environments](images/flattype-640px.png) *Flat type without a backdrop can be hard to view from certain angles and in certain environments*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e3e69-186">기본 제공 배경이 있는 ![형식은 *기본 제공 되는 배경이 있는 형식*](images/flattypeandbkg-640px.png) 제대로 작동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-186">![Type with a built-in backdrop can work well](images/flattypeandbkg-640px.png) *Type with a built-in backdrop can work well*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="e3e69-187">![돌출 형식은 가장자리를 음영 처리 하는 경우에도 *입체 형식*](images/20171016-160221-mixedreality-640px.jpg) 회색으로 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-187">![Extruded type can work well if you shade the sides](images/20171016-160221-mixedreality-640px.jpg) *Extruded type can work well if you shade the sides*</span></span>
    :::column-end:::
:::row-end:::


<span data-ttu-id="e3e69-188">**작동 하는 색을 입력 합니다.**</span><span class="sxs-lookup"><span data-stu-id="e3e69-188">**Type colors that work**</span></span>
* <span data-ttu-id="e3e69-189">하얀</span><span class="sxs-lookup"><span data-stu-id="e3e69-189">White</span></span>
* <span data-ttu-id="e3e69-190">명암</span><span class="sxs-lookup"><span data-stu-id="e3e69-190">Black</span></span>
* <span data-ttu-id="e3e69-191">밝은 반 채도 색</span><span class="sxs-lookup"><span data-stu-id="e3e69-191">Bright semi-saturated color</span></span>

<span data-ttu-id="e3e69-192">![형식 색입니다.](images/20171016-112111-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e3e69-192">![Type colors that work.](images/20171016-112111-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="e3e69-193">*작동 하는 색을 입력 합니다.*</span><span class="sxs-lookup"><span data-stu-id="e3e69-193">*Type colors that work*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="e3e69-194">피해 야 할 사항</span><span class="sxs-lookup"><span data-stu-id="e3e69-194">What to avoid</span></span>

<span data-ttu-id="e3e69-195">**문제를 일으키는 색을 입력 합니다.**</span><span class="sxs-lookup"><span data-stu-id="e3e69-195">**Type colors that cause trouble**</span></span>
* <span data-ttu-id="e3e69-196">중간 색조</span><span class="sxs-lookup"><span data-stu-id="e3e69-196">Mid-tones</span></span>
* <span data-ttu-id="e3e69-197">으로</span><span class="sxs-lookup"><span data-stu-id="e3e69-197">Gray</span></span>
* <span data-ttu-id="e3e69-198">채도가 높은 색 또는 낮춘 색</span><span class="sxs-lookup"><span data-stu-id="e3e69-198">Over-saturated colors or desaturated colors</span></span>

<span data-ttu-id="e3e69-199">문제가 발생 하는 색 ![형식입니다.](images/20171016-112246-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e3e69-199">![Type colors that cause trouble.](images/20171016-112246-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="e3e69-200">*문제를 일으키는 색을 입력 합니다.*</span><span class="sxs-lookup"><span data-stu-id="e3e69-200">*Type colors that cause trouble*</span></span>

## <a name="lighting"></a><span data-ttu-id="e3e69-201">조명</span><span class="sxs-lookup"><span data-stu-id="e3e69-201">Lighting</span></span>

<span data-ttu-id="e3e69-202">앱 시작 관리자의 조명은 절벽 집 환경에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-202">The lighting for your app launcher comes from the Cliff House environment.</span></span> <span data-ttu-id="e3e69-203">이 경우에는 집 전체의 여러 위치에서 시작 관리자를 테스트 하 여 밝은 및 그림자 모두에 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-203">Be sure to test your launcher in several places throughout the house so it looks good in both light and shadows.</span></span> <span data-ttu-id="e3e69-204">좋은 소식은이 문서에 있는 다른 디자인 지침을 수행한 경우에는 관리자가 절벽 집에서 대부분의 조명에 매우 좋은 셰이프 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-204">The good news is, if you’ve followed the other design guidance in this document, your launcher should be in pretty good shape for most lighting in the Cliff House.</span></span>

<span data-ttu-id="e3e69-205">시작 관리자가 환경에서 다양 한 조명의 화면에 표시 되는 모습을 테스트 하는 좋은 위치는 스튜디오, 미디어 객실 (Patio의 구체적인 영역)입니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-205">Good places to test how your launcher looks in the various lights in the environment are the Studio, the Media Room, anywhere outside and on the Back Patio (the concrete area with the lawn).</span></span> <span data-ttu-id="e3e69-206">또 다른 좋은 테스트는 반쪽 및 1/2 그림자에 배치 하 고 모양을 확인 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-206">Another good test is to put it in half light and half shadow and see what it looks like.</span></span>

<span data-ttu-id="e3e69-207">사용 중인 시작 관리자가 밝은 및 그림자 모두에 적합 한지 확인 ![합니다.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e3e69-207">![Make sure your launcher looks good in both light and shadows.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="e3e69-208">*시작 관리자가 밝은 및 그림자 둘 다에서 제대로 보이는지 확인 합니다.*</span><span class="sxs-lookup"><span data-stu-id="e3e69-208">*Make sure your launcher looks good in both light and shadows*</span></span>

## <a name="texturing"></a><span data-ttu-id="e3e69-209">질감</span><span class="sxs-lookup"><span data-stu-id="e3e69-209">Texturing</span></span>

### <a name="authoring-your-textures"></a><span data-ttu-id="e3e69-210">질감 제작</span><span class="sxs-lookup"><span data-stu-id="e3e69-210">Authoring your textures</span></span>

<span data-ttu-id="e3e69-211">3D 앱 시작 관리자의 끝 형식은 .PBR (물리적으로 기반 렌더링) 파이프라인을 사용 하 여 만든.</span><span class="sxs-lookup"><span data-stu-id="e3e69-211">The end format of your 3D app launcher will be a .glb file, which is made using the PBR (Physically Based Rendering) pipeline.</span></span> <span data-ttu-id="e3e69-212">이는 복잡 한 프로세스 일 수 있습니다. 현재는 기술 음악가를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-212">This can be a tricky process - now is a good time to employ a technical artist if you haven't already.</span></span> <span data-ttu-id="e3e69-213">용감한 DIY 인 경우, 시작 하기 전에 내부적으로 수행 해야 하는 작업을 [연구 하 고 배우](https://wiki.polycount.com/wiki/PBR) 는 데 걸리는 시간은 일반적인 실수를 피하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-213">If you’re a brave DIY-er, taking the time to [research and learn PBR terminology](https://wiki.polycount.com/wiki/PBR) and what’s happening under the hood before you begin will help you avoid common mistakes.</span></span> 

<span data-ttu-id="e3e69-214">![예제: 최신 메모 앱](images/pbr-freshnote1-640px-500px.png)</span><span class="sxs-lookup"><span data-stu-id="e3e69-214">![Example: Fresh Note app](images/pbr-freshnote1-640px-500px.png)</span></span><br>
<span data-ttu-id="e3e69-215">*최신 참고 3D 앱 시작 관리자 예제 (가상 앱)*</span><span class="sxs-lookup"><span data-stu-id="e3e69-215">*Fresh Note 3D app launcher example (fictional app)*</span></span>

<span data-ttu-id="e3e69-216">**권장 authoring tool**</span><span class="sxs-lookup"><span data-stu-id="e3e69-216">**Recommended authoring tool**</span></span>

<span data-ttu-id="e3e69-217">Allegorithmic [를 사용 하 여 최종](https://www.allegorithmic.com/products/substance-painter) 파일을 작성 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-217">We recommend using [Substance Painter](https://www.allegorithmic.com/products/substance-painter) by Allegorithmic to author your final file.</span></span> <span data-ttu-id="e3e69-218">학습 기능 복사에서 .PBR 셰이더를 작성 하는 방법을 잘 모르는 경우 다음 [자습서](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e3e69-218">If you’re not familiar with authoring PBR shaders in Substance Painter, here’s a [tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span></span>

<span data-ttu-id="e3e69-219">이러한 기능 중 하나를 잘 알고 있는 경우에는 (교대로 [3D 옷걸이](https://3dcoat.com/home/), [Quixel Suite 2 또는](https://quixel.se/suite2/) [moset 도구 모음이](https://www.marmoset.co/toolbag/) 작동 합니다.)</span><span class="sxs-lookup"><span data-stu-id="e3e69-219">(Alternately [3D-Coat](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/), or [Marmoset Toolbag](https://www.marmoset.co/toolbag/) would also work if you’re more familiar with one of these.)</span></span>

### <a name="best-practices"></a><span data-ttu-id="e3e69-220">모범 사례</span><span class="sxs-lookup"><span data-stu-id="e3e69-220">Best practices</span></span>

* <span data-ttu-id="e3e69-221">앱 시작 관리자 개체가 .PBR 용으로 작성 된 경우에는 절벽 집 환경으로 변환 하는 것이 매우 간단 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-221">If your app launcher object was authored for PBR, it should be pretty straightforward to convert it for the Cliff House environment.</span></span>
* <span data-ttu-id="e3e69-222">셰이더에는 금속/황삭 작업 흐름이 필요 합니다. Unreal .PBR 셰이더는 닫는 팩스입니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-222">Our shader is expecting a Metal/Roughness work flow – The Unreal PBR shader is a close facsimile.</span></span>
* <span data-ttu-id="e3e69-223">질감을 내보내는 경우 [권장 되는 질감 크기](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) 를 염두에 두십시오.</span><span class="sxs-lookup"><span data-stu-id="e3e69-223">When exporting your textures keep the [recommended texture sizes](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) in mind.</span></span>
* <span data-ttu-id="e3e69-224">실시간 조명에 대 한 개체를 빌드해야 합니다. 즉, 다음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="e3e69-224">Make sure to build your objects for real-time lighting — this means:</span></span>
    * <span data-ttu-id="e3e69-225">그림자를 구운 안 함</span><span class="sxs-lookup"><span data-stu-id="e3e69-225">Avoid baked shadows – or painted shadows</span></span>
    * <span data-ttu-id="e3e69-226">질감에서 조명 구운 방지</span><span class="sxs-lookup"><span data-stu-id="e3e69-226">Avoid baked lighting in the textures</span></span>
    * <span data-ttu-id="e3e69-227">.PBR 재질 제작 패키지 중 하나를 사용 하 여 셰이더에 대해 생성 된 올바른 맵 가져오기</span><span class="sxs-lookup"><span data-stu-id="e3e69-227">Use one of the PBR material authoring packages to get the right maps generated for our shader</span></span>

## <a name="see-also"></a><span data-ttu-id="e3e69-228">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e3e69-228">See also</span></span>

* [<span data-ttu-id="e3e69-229">혼합 현실 홈에서 사용할 3D 모델 만들기</span><span class="sxs-lookup"><span data-stu-id="e3e69-229">Create 3D models for use in the mixed reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="e3e69-230">3D 앱 시작 관리자(UWP 앱) 구현</span><span class="sxs-lookup"><span data-stu-id="e3e69-230">Implement 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="e3e69-231">3D 앱 시작 관리자(Win32 앱) 구현</span><span class="sxs-lookup"><span data-stu-id="e3e69-231">Implement 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
