---
title: 3D 앱 시작 관리자 디자인 지침
description: 3D 앱 시작 관리자는 응용 프로그램 실행을 선택할 수 있는 사용자의 혼합된 현실 집에서 "실제" 개체입니다.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality를 디자인, 3D 앱 시작 관리자, 몰입 형 헤드셋, 라이브 큐브
ms.openlocfilehash: 47db5bffa121c0cc11d246dc749c464e5f187270
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598550"
---
# <a name="3d-app-launcher-design-guidance"></a><span data-ttu-id="33e00-104">3D 앱 시작 관리자 디자인 지침</span><span class="sxs-lookup"><span data-stu-id="33e00-104">3D app launcher design guidance</span></span>

<span data-ttu-id="33e00-105">Windows Mixed Reality 몰입 형 (VR) 헤드셋을 놓을 때 입력할 집 Windows Mixed Reality 산 및 물으로 둘러싸인 절벽에서 집으로 시각화 (수행할 수 있지만 [다른 환경을 선택 하 고 자체를 만들 수도](add-custom-home-environments.md)).</span><span class="sxs-lookup"><span data-stu-id="33e00-105">When you put on a Windows Mixed Reality immersive (VR) headset, you enter the Windows Mixed Reality home, visualized as a house on a cliff surrounded by mountains and water (though you can [choose other environments and even create your own](add-custom-home-environments.md)).</span></span> <span data-ttu-id="33e00-106">홈이 공간 내에서 사용자가 정렬 하 고 3D 개체는 원하는 방식으로 처리 되는 앱을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-106">Within the space of this home, a user is free to arrange and organize the 3D objects and apps that they care about any way they want.</span></span> <span data-ttu-id="33e00-107">A **3D 앱 시작 관리자** 사용자에서는 "실제" 개체의 응용 프로그램 실행을 선택할 수 있는 현실 집을 혼합 됩니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-107">A **3D app launcher** is a “physical” object in the user’s mixed reality house that they can select to launch an app.</span></span>

<span data-ttu-id="33e00-108">![예: 부동 Bird 3D 앱 시작 관리자](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="33e00-108">![Example: Floaty Bird 3D app launcher](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="33e00-109">*부동 Bird 3D 앱 시작 관리자 예제 (가상 앱)*</span><span class="sxs-lookup"><span data-stu-id="33e00-109">*Floaty Bird 3D app launcher example (fictional app)*</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="33e00-110">3D 앱 시작 관리자 만들기 프로세스</span><span class="sxs-lookup"><span data-stu-id="33e00-110">3D app launcher creation process</span></span>

<span data-ttu-id="33e00-111">3D 앱 시작 관리자를 작성 하는 방법은 3 단계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-111">There are 3 steps to creating a 3D app launcher:</span></span>
1. <span data-ttu-id="33e00-112">디자인 및 concepting (이 문서)</span><span class="sxs-lookup"><span data-stu-id="33e00-112">Designing and concepting (this article)</span></span>
2. [<span data-ttu-id="33e00-113">모델링 및 내보내기</span><span class="sxs-lookup"><span data-stu-id="33e00-113">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="33e00-114">응용 프로그램에 통합 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-114">Integrating it into your application:</span></span>
    * [<span data-ttu-id="33e00-115">UWP 앱</span><span class="sxs-lookup"><span data-stu-id="33e00-115">UWP apps</span></span>](implementing-3d-app-launchers.md)
    * [<span data-ttu-id="33e00-116">Win32 앱</span><span class="sxs-lookup"><span data-stu-id="33e00-116">Win32 apps</span></span>](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a><span data-ttu-id="33e00-117">디자인 개념</span><span class="sxs-lookup"><span data-stu-id="33e00-117">Design concepts</span></span>

### <a name="fantastic-yet-familiar"></a><span data-ttu-id="33e00-118">친숙 한 아직 놀라운 기능</span><span class="sxs-lookup"><span data-stu-id="33e00-118">Fantastic yet familiar</span></span>

<span data-ttu-id="33e00-119">사용자 앱 시작 관리자에 거주 하 고 Windows Mixed Reality 환경은 부분에 친숙 한 파트 정보화/sci-fi입니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-119">The Windows Mixed Reality environment your app launcher lives in is part familiar, part fantastical/sci-fi.</span></span> <span data-ttu-id="33e00-120">가장 좋은 시작 관리자는이 세상 규칙을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-120">The best launchers follow the rules of this world.</span></span> <span data-ttu-id="33e00-121">어떻게 친숙 하 고 대표적인 개체를 앱에서 수행할 수 있지만 실제 실제로의 규칙 중 일부를 변형할 생각할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-121">Think of how you can take a familiar, representative object from your app, but bend some of the rules of actual reality.</span></span> <span data-ttu-id="33e00-122">매직 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-122">Magic will result.</span></span>

### <a name="intuitive"></a><span data-ttu-id="33e00-123">직관적인</span><span class="sxs-lookup"><span data-stu-id="33e00-123">Intuitive</span></span>

<span data-ttu-id="33e00-124">사용자 앱 시작 관리자를 보면 용도-앱을 시작 하려면 명백 하 고 모든 혼동 해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-124">When you look at your app launcher, its purpose - to launch your app - should be obvious and shouldn’t cause any confusion.</span></span> <span data-ttu-id="33e00-125">예를 들어 프로그램 시작 관리자는 장식 Cliff 집안의 부분에 대 한 혼동 하지는 앱의 만큼 충분히 확실 한 대표 하는 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-125">For example, be sure your launcher is an obvious-enough representative of your app that it won’t be confused for a piece of decor in the Cliff House.</span></span> <span data-ttu-id="33e00-126">에 앱 시작 관리자에는 터치/선택할 것 피플을 초대 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-126">Your app launcher should invite people to touch/select it.</span></span>

<span data-ttu-id="33e00-127">![예: 새 참고 3D 앱 시작 관리자](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="33e00-127">![Example: Fresh Note 3D app launcher](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="33e00-128">*새 참고 3D 앱 시작 관리자 예제 (가상 앱)*</span><span class="sxs-lookup"><span data-stu-id="33e00-128">*Fresh Note 3D app launcher example (fictional app)*</span></span>

### <a name="home-scale"></a><span data-ttu-id="33e00-129">홈 확장</span><span class="sxs-lookup"><span data-stu-id="33e00-129">Home scale</span></span>

<span data-ttu-id="33e00-130">Cliff 집에 살고 있는 3D 앱 시작 관리자 및 기본 크기로 공간에서 다른 "실제" 개체를 사용 하 여 의미를 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-130">3D app launchers live in the Cliff House and their default size should make sense with the other “physical” objects in the space.</span></span> <span data-ttu-id="33e00-131">에 배치 하면 프로그램 시작 관리자에서 옆에 있는 예를 들어 집 공장 또는 일부 가구 것 느껴질 size-wise, 집 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-131">If you place your launcher beside, say, a house plant or some furniture, it should feel at home, size-wise.</span></span> <span data-ttu-id="33e00-132">좋은 시작 지점이 30 입방 형 3 센티미터에 어떻게 표시 하는 사용자가 크기를 조정할 수를 위아래로 원하는 경우 기억 됩니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-132">A good starting point is to see how it looks at 30 cubic centimeters, but remember that users can scale it up or down if they like.</span></span>

### <a name="own-able"></a><span data-ttu-id="33e00-133">소유 수</span><span class="sxs-lookup"><span data-stu-id="33e00-133">Own-able</span></span>

<span data-ttu-id="33e00-134">앱 시작 관리자는 담당할 해당 공간에 기대 개체 처럼 느껴질 것입니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-134">The app launcher should feel like an object a person would be excited to have in their space.</span></span> <span data-ttu-id="33e00-135">이러한 됩니다 수 거의 주변 자체이를 사용 하 여 시작 관리자 느껴질 것 같은 사용자 생각 바람직 만큼 자동으로 검색 하 고 주변 유지 하므로.</span><span class="sxs-lookup"><span data-stu-id="33e00-135">They’ll be virtually surrounding themselves with these things, so the launcher should feel like something the user thought was desirable enough to seek out and keep nearby.</span></span>

<span data-ttu-id="33e00-136">![예: 우주 Warp 3D 앱 시작 관리자](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="33e00-136">![Example: Astro Warp 3D app launcher](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="33e00-137">*우주 Warp 3D 앱 시작 관리자 예제 (가상 앱)*</span><span class="sxs-lookup"><span data-stu-id="33e00-137">*Astro Warp 3D app launcher example (fictional app)*</span></span>

### <a name="recognizable"></a><span data-ttu-id="33e00-138">인식할 수 있는</span><span class="sxs-lookup"><span data-stu-id="33e00-138">Recognizable</span></span>

<span data-ttu-id="33e00-139">즉시 3D 앱 시작 관리자에 표시 하는 사람에 게 "앱의 브랜드"를 표현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-139">Your 3D app launcher should instantly express “your app’s brand” to people who see it.</span></span> <span data-ttu-id="33e00-140">앱 별 문자나 특히 식별이 가능한 개체를 해야 하는 경우에 디자인의 주요 부분으로 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-140">If you have a star character or an especially identifiable object in your app, we recommend using that as a big part of your design.</span></span> <span data-ttu-id="33e00-141">혼합된 현실 세계에서 개체를만 로고만 보다 사용자의 관심사를 그립니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-141">In a mixed reality world, an object will draw more interest from users than just a logo alone.</span></span> <span data-ttu-id="33e00-142">인식할 수 있는 빠르고 명확 하 게 브랜드를 통신합니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-142">Recognizable objects communicate brand quickly and clearly.</span></span>

### <a name="volumetric"></a><span data-ttu-id="33e00-143">대규모</span><span class="sxs-lookup"><span data-stu-id="33e00-143">Volumetric</span></span>

<span data-ttu-id="33e00-144">앱은 이상의 평면에 로고를 배치 하 고 호출 시간부터 개발 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-144">Your app deserves more than just putting your logo on a flat plane and calling it a day.</span></span> <span data-ttu-id="33e00-145">프로그램 시작 관리자 사용자의 공간에서 흥미로운, 3D, 물리적 개체 처럼 느껴질 것입니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-145">Your launcher should feel like an exciting, 3D, physical object in the user’s space.</span></span> <span data-ttu-id="33e00-146">앱 Macy의 추수 감사절 일 섰고 풍선에 하려는 imagine 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-146">A good approach is to imagine your app was going to have a balloon in the Macy’s Thanksgiving Day Parade.</span></span> <span data-ttu-id="33e00-147">질문 어떤는 감명을 사람들이 그 길가의 왔는지에 따라?</span><span class="sxs-lookup"><span data-stu-id="33e00-147">Ask yourself, what would really wow people as it came down the street?</span></span> <span data-ttu-id="33e00-148">유용한 모든 보기 각도에서 표시 됩니다 무엇입니까?</span><span class="sxs-lookup"><span data-stu-id="33e00-148">What would look great from all viewing angles?</span></span>


:::row:::
    :::column:::
        ![Logo only](images/20171016-140436-mixedreality-640px.jpg)
        *Logo only*
    :::column-end:::
    :::column:::
        ![More recognizable with a character](images/20171016-140557-mixedreality-640px.jpg)
        *More recognizable with a character*
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
        ![Flat approach, not surprisingly, feels flat](images/20171016-155101-mixedreality-640px.jpg)
        *Flat approach, not surprisingly, feels flat*
    :::column-end:::
    :::column:::
        ![Volumetric approach better showcases your app](images/20171016-161407-mixedreality-640px.jpg)
        *Volumetric approach better showcases your app*
    :::column-end:::
:::row-end:::


## <a name="tips-for-good-3d-models"></a><span data-ttu-id="33e00-149">적합 한 3D 모델에 대 한 팁</span><span class="sxs-lookup"><span data-stu-id="33e00-149">Tips for good 3D models</span></span>

### <a name="best-practices"></a><span data-ttu-id="33e00-150">모범 사례</span><span class="sxs-lookup"><span data-stu-id="33e00-150">Best practices</span></span>
* <span data-ttu-id="33e00-151">사용자 앱 시작 관리자에 대 한 차원을 계획할 때 약 30 cm 큐브에 대 한 문제를 해결 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-151">When planning dimensions for your app launcher, shoot for roughly a 30cm cube.</span></span> <span data-ttu-id="33e00-152">따라서 1: 1:1 크기 비율입니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-152">So, a 1:1:1 size ratio.</span></span>
* <span data-ttu-id="33e00-153">모델에는 10,000 개 미만이 다각형 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-153">Models must be under 10,000 polygons.</span></span> [<span data-ttu-id="33e00-154">삼각형 개수 및 세부 (단계 Lod) 수준에 자세히 알아보기</span><span class="sxs-lookup"><span data-stu-id="33e00-154">Learn more about triangle counts and levels of details (LODs)</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* <span data-ttu-id="33e00-155">가능한 경우에 몰입 형 헤드셋에서 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-155">Test on an immersive headset when possible.</span></span>
* <span data-ttu-id="33e00-156">가능한 경우 모델의 기 하 도형에 빌드 세부 정보 – 자세한 질감을 의존 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="33e00-156">Build details into your model’s geometry where possible – don’t rely on textures for detail.</span></span>
* <span data-ttu-id="33e00-157">"Water 긴밀 하 게" 닫힌 geometry를 빌드하십시오.</span><span class="sxs-lookup"><span data-stu-id="33e00-157">Build “water tight” closed geometry.</span></span> <span data-ttu-id="33e00-158">모델링 되지는 빈 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-158">No holes that are not modeled in.</span></span>
* <span data-ttu-id="33e00-159">개체에 자연 스러운 자료를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-159">Use natural materials in your object.</span></span> <span data-ttu-id="33e00-160">실제 환경에서 작성 한다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-160">Imagine crafting it in the real world.</span></span>
* <span data-ttu-id="33e00-161">모델에 다른 거리 및 크기에서 잘 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-161">Make sure your model reads well at different distances and sizes.</span></span>
* <span data-ttu-id="33e00-162">모델 준비가 되 면 읽기를 [자산 지침 내보내기](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview)합니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-162">When your model is ready to go, read the [exporting assets guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).</span></span>

<span data-ttu-id="33e00-163">![질감의 미묘한 세부 정보를 사용 하 여 모델](images/20171013-143334-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="33e00-163">![Model with subtle details in the texture](images/20171013-143334-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="33e00-164">*질감의 미묘한 세부 정보를 사용 하 여 모델*</span><span class="sxs-lookup"><span data-stu-id="33e00-164">*Model with subtle details in the texture*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="33e00-165">피해 야 할 사항</span><span class="sxs-lookup"><span data-stu-id="33e00-165">What to avoid</span></span>
* <span data-ttu-id="33e00-166">고대비 세부 정보 또는 사용 중인 작은 패턴 및 질감을 사용 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="33e00-166">Don't use high-contrast details or small, busy patterns and textures.</span></span>
* <span data-ttu-id="33e00-167">씬 geometry를 사용 하지 않는 – 거리에서 잘 작동 하지 않습니다 고 별칭 잘못 됩니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-167">Don't use thin geometry – it doesn’t work well at a distance and will alias badly.</span></span>
* <span data-ttu-id="33e00-168">확장 모델의 파트를 허용 하지 않습니다 1 이상의 너무 많은: 1:1 크기 비율입니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-168">Don't let parts of your model extend too much beyond the 1:1:1 size ratio.</span></span> <span data-ttu-id="33e00-169">크기 조정 문제가 생기게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-169">It will create scaling problems.</span></span>

<span data-ttu-id="33e00-170">![고대비 작은 사용 중인 패턴 방지](images/20171013-143603-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="33e00-170">![Avoid high-contrast, small busy patterns](images/20171013-143603-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="33e00-171">*고대비, small, 사용 중인 패턴 방지*</span><span class="sxs-lookup"><span data-stu-id="33e00-171">*Avoid high-contrast, small, busy patterns*</span></span>

## <a name="how-to-handle-type"></a><span data-ttu-id="33e00-172">형식을 처리 하는 방법</span><span class="sxs-lookup"><span data-stu-id="33e00-172">How to handle type</span></span>

### <a name="best-practices"></a><span data-ttu-id="33e00-173">모범 사례</span><span class="sxs-lookup"><span data-stu-id="33e00-173">Best practices</span></span>
* <span data-ttu-id="33e00-174">형식에 앱 시작 관리자 (또는 그 이상)의 약 1/3을 구성 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-174">We recommend your type comprises about 1/3 of your app launcher (or more).</span></span> <span data-ttu-id="33e00-175">형식은 사용자 프로그램 시작 관리자는 실제로 상당히 많은 경우 유용 하도록 시작 관리자 개념을 제공 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-175">Type is the main thing that gives people an idea that your launcher is, in fact, a launcher so it’s nice if it’s pretty substantial.</span></span>
* <span data-ttu-id="33e00-176">형식이 매우 피하십시오 – 유지 앱 시작 관리자의 범위 내에서 핵심 차원 (더 많거나 적은) 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-176">Avoid making type super wide – try to keep it within the confines of the app launchers core dimensions (more or less).</span></span>
* <span data-ttu-id="33e00-177">플랫 형식이 작동 수 있지만 특정 환경에서는 특정 각도 보려는 하드 사용할 수 있다는 주의 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-177">Flat type can work, but be aware that it can be hard to view from certain angles and in certain environments.</span></span> <span data-ttu-id="33e00-178">Solid 개체 또는이 도움이 되도록 배경 배치 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-178">You might consider putting it a solid object or backdrop behind it to help with this.</span></span>
* <span data-ttu-id="33e00-179">형식에 추가 차원 느낌 멋진 3d에서 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-179">Adding dimension to your type feels nice in 3D.</span></span> <span data-ttu-id="33e00-180">형식의 양쪽 음영 다른, 어두운 색 가독성을 사용 하 여 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-180">Shading the sides of the type a different, darker color can help with readability.</span></span>


:::row:::
    :::column:::
        ![Flat type without a backdrop can be hard to view from certain angles and in certain environments](images/flattype-640px.png)
        *Flat type without a backdrop can be hard to view from certain angles and in certain environments*
    :::column-end:::
    :::column:::
        ![Type with a built-in backdrop can work well](images/flattypeandbkg-640px.png)
        *Type with a built-in backdrop can work well*
    :::column-end:::
    :::column:::
        ![Extruded type can work well if you shade the sides](images/20171016-160221-mixedreality-640px.jpg)
        *Extruded type can work well if you shade the sides*
    :::column-end:::
:::row-end:::


<span data-ttu-id="33e00-181">**작동 하는 형식 색**</span><span class="sxs-lookup"><span data-stu-id="33e00-181">**Type colors that work**</span></span>
* <span data-ttu-id="33e00-182">하얀</span><span class="sxs-lookup"><span data-stu-id="33e00-182">White</span></span>
* <span data-ttu-id="33e00-183">검정</span><span class="sxs-lookup"><span data-stu-id="33e00-183">Black</span></span>
* <span data-ttu-id="33e00-184">밝은 반 채도가 높은 색</span><span class="sxs-lookup"><span data-stu-id="33e00-184">Bright semi-saturated color</span></span>

<span data-ttu-id="33e00-185">![작동 하는 색을 입력 합니다.](images/20171016-112111-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="33e00-185">![Type colors that work.](images/20171016-112111-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="33e00-186">*작동 하는 형식 색*</span><span class="sxs-lookup"><span data-stu-id="33e00-186">*Type colors that work*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="33e00-187">피해 야 할 사항</span><span class="sxs-lookup"><span data-stu-id="33e00-187">What to avoid</span></span>

<span data-ttu-id="33e00-188">**문제를 일으키는 형식 색**</span><span class="sxs-lookup"><span data-stu-id="33e00-188">**Type colors that cause trouble**</span></span>
* <span data-ttu-id="33e00-189">중간 톤</span><span class="sxs-lookup"><span data-stu-id="33e00-189">Mid-tones</span></span>
* <span data-ttu-id="33e00-190">회색</span><span class="sxs-lookup"><span data-stu-id="33e00-190">Gray</span></span>
* <span data-ttu-id="33e00-191">과도 하 게 포화 색 또는 낮춘된 색</span><span class="sxs-lookup"><span data-stu-id="33e00-191">Over-saturated colors or desaturated colors</span></span>

<span data-ttu-id="33e00-192">![문제를 일으키는 색을 입력 합니다.](images/20171016-112246-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="33e00-192">![Type colors that cause trouble.](images/20171016-112246-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="33e00-193">*문제를 일으키는 형식 색*</span><span class="sxs-lookup"><span data-stu-id="33e00-193">*Type colors that cause trouble*</span></span>

## <a name="lighting"></a><span data-ttu-id="33e00-194">조명</span><span class="sxs-lookup"><span data-stu-id="33e00-194">Lighting</span></span>

<span data-ttu-id="33e00-195">사용자 앱 시작 관리자에 대 한 조명 Cliff 집 환경에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-195">The lighting for your app launcher comes from the Cliff House environment.</span></span> <span data-ttu-id="33e00-196">프로그램 시작 관리자에서 조명 및 그림자 모두 좋아 보입니다. 집 전체의 여러 위치에서 테스트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-196">Be sure to test your launcher in several places throughout the house so it looks good in both light and shadows.</span></span> <span data-ttu-id="33e00-197">프로그램 시작 관리자는 Cliff 집에서 대부분의 조명에 대해 잘 셰이프에서 수 있어야이 문서의 다른 디자인 지침을 수행한 경우 좋은 소식이입니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-197">The good news is, if you’ve followed the other design guidance in this document, your launcher should be in pretty good shape for most lighting in the Cliff House.</span></span>

<span data-ttu-id="33e00-198">프로그램 시작 관리자 환경에서 다양 한 광원에서 모양을 테스트 하려면 적절 한 위치는 Studio 미디어 대화방에 다시 테라스 (구체적인 영역과 앞 마당) 및 외부 아무 곳 이나를 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-198">Good places to test how your launcher looks in the various lights in the environment are the Studio, the Media Room, anywhere outside and on the Back Patio (the concrete area with the lawn).</span></span> <span data-ttu-id="33e00-199">또 다른 좋은 테스트 절반 조명 및 그림자 절반에 배치 하 모양을 참조입니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-199">Another good test is to put it in half light and half shadow and see what it looks like.</span></span>

<span data-ttu-id="33e00-200">![프로그램 시작 관리자에서 조명 및 그림자를 모두 정상적으로 진행 해야 합니다.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="33e00-200">![Make sure your launcher looks good in both light and shadows.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="33e00-201">*프로그램 시작 관리자에서 조명 및 그림자를 모두 정상적으로 진행 되는지 확인*</span><span class="sxs-lookup"><span data-stu-id="33e00-201">*Make sure your launcher looks good in both light and shadows*</span></span>

## <a name="texturing"></a><span data-ttu-id="33e00-202">질감</span><span class="sxs-lookup"><span data-stu-id="33e00-202">Texturing</span></span>

### <a name="authoring-your-textures"></a><span data-ttu-id="33e00-203">질감 제작</span><span class="sxs-lookup"><span data-stu-id="33e00-203">Authoring your textures</span></span>

<span data-ttu-id="33e00-204">프로그램 3D 앱 시작 관리자의 최종 형식을 (물리적으로 기반 렌더링) PBR 파이프라인을 사용 하 여.glb 파일을 됩니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-204">The end format of your 3D app launcher will be a .glb file, which is made using the PBR (Physically Based Rendering) pipeline.</span></span> <span data-ttu-id="33e00-205">까다로운 프로세스-수 이제 아직 없는 경우 기술 artist를 사용할 수 있는 좋은 기회입니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-205">This can be a tricky process - now is a good time to employ a technical artist if you haven't already.</span></span> <span data-ttu-id="33e00-206">인 경우 한 때 DIY-er 시간을 내어 [PBR 용어를 알아보고 조사](http://wiki.polycount.com/wiki/PBR) 도와 시작 하기 전에 내부에서 일어나는 일반적인 실수를 피하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-206">If you’re a brave DIY-er, taking the time to [research and learn PBR terminology](http://wiki.polycount.com/wiki/PBR) and what’s happening under the hood before you begin will help you avoid common mistakes.</span></span> 

<span data-ttu-id="33e00-207">![예: 새 Note 앱](images/pbr-freshnote1-640px-500px.png)</span><span class="sxs-lookup"><span data-stu-id="33e00-207">![Example: Fresh Note app](images/pbr-freshnote1-640px-500px.png)</span></span><br>
<span data-ttu-id="33e00-208">*새 참고 3D 앱 시작 관리자 예제 (가상 앱)*</span><span class="sxs-lookup"><span data-stu-id="33e00-208">*Fresh Note 3D app launcher example (fictional app)*</span></span>

<span data-ttu-id="33e00-209">**권장 되는 제작 도구**</span><span class="sxs-lookup"><span data-stu-id="33e00-209">**Recommended authoring tool**</span></span>

<span data-ttu-id="33e00-210">사용 하는 것이 좋습니다 [물질 복사](https://www.allegorithmic.com/products/substance-painter) Allegorithmic 최종 파일을 작성 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-210">We recommend using [Substance Painter](https://www.allegorithmic.com/products/substance-painter) by Allegorithmic to author your final file.</span></span> <span data-ttu-id="33e00-211">친숙 하지 않은 물질 페인, 여기에서 PBR 셰이더를 작성 하는 경우는 [자습서](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials)합니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-211">If you’re not familiar with authoring PBR shaders in Substance Painter, here’s a [tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span></span>

<span data-ttu-id="33e00-212">(또는 [3D Coat](https://3dcoat.com/home/)를 [Quixel 제품군 2](https://quixel.se/suite2/), 또는 [Marmoset Toolbag](https://www.marmoset.co/toolbag/) 다음 중 하나를 사용 하 여 더욱 친숙 하는 경우에 작동 됩니다.)</span><span class="sxs-lookup"><span data-stu-id="33e00-212">(Alternately [3D-Coat](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/), or [Marmoset Toolbag](https://www.marmoset.co/toolbag/) would also work if you’re more familiar with one of these.)</span></span>

### <a name="best-practices"></a><span data-ttu-id="33e00-213">모범 사례</span><span class="sxs-lookup"><span data-stu-id="33e00-213">Best practices</span></span>

* <span data-ttu-id="33e00-214">앱 시작 관리자 개체 PBR에 대해 작성 된, 하는 경우에 Cliff 집 환경에 대 한 변환 하는 것이 간단 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-214">If your app launcher object was authored for PBR, it should be pretty straightforward to convert it for the Cliff House environment.</span></span>
* <span data-ttu-id="33e00-215">이 셰이더는 금속/거친 작업 흐름 필요 – The Unreal PBR 셰이더가 닫기 사본을 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-215">Our shader is expecting a Metal/Roughness work flow – The Unreal PBR shader is a close facsimile.</span></span>
* <span data-ttu-id="33e00-216">질감을 내보내는 유지 하는 경우는 [권장 되는 질감 크기](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) 유의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-216">When exporting your textures keep the [recommended texture sizes](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) in mind.</span></span>
* <span data-ttu-id="33e00-217">실시간 조명에 대해 개체를 작성 해야 합니다.-즉:</span><span class="sxs-lookup"><span data-stu-id="33e00-217">Make sure to build your objects for real-time lighting — this means:</span></span>
    * <span data-ttu-id="33e00-218">구운된 그림자 – 또는 그려지는 그림자를 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-218">Avoid baked shadows – or painted shadows</span></span>
    * <span data-ttu-id="33e00-219">질감에서 구운된 조명 방지</span><span class="sxs-lookup"><span data-stu-id="33e00-219">Avoid baked lighting in the textures</span></span>
    * <span data-ttu-id="33e00-220">패키지 제작 PBR 자료 중 하나를 사용 하 여이 셰이더에 대해 생성 된 올바른 지도 받기</span><span class="sxs-lookup"><span data-stu-id="33e00-220">Use one of the PBR material authoring packages to get the right maps generated for our shader</span></span>

## <a name="see-also"></a><span data-ttu-id="33e00-221">참조</span><span class="sxs-lookup"><span data-stu-id="33e00-221">See also</span></span>

* [<span data-ttu-id="33e00-222">홈 혼합된 현실에서 사용 하 여에 대 한 3D 모델 만들기</span><span class="sxs-lookup"><span data-stu-id="33e00-222">Create 3D models for use in the mixed reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="33e00-223">3D 앱 시작 관리자 (UWP 앱)를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-223">Implement 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="33e00-224">3D 앱 시작 관리자 (Win32 앱)를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e00-224">Implement 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
