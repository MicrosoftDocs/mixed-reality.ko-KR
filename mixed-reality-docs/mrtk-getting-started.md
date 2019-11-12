---
title: MRTK 버전 2 시작
description: MRTK를 활용 하려는 새로운 개발자
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
keywords: Windows Mixed Reality, 테스트, 혼합 현실 도구 키트, MRTK 버전 2, MRTK, 도구, SDK, HoloLens, HoloLens 2
ms.openlocfilehash: bb958543aa68586dd689a2048665b233d6be7064
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913131"
---
# <a name="getting-started-with-mrtk-v2"></a><span data-ttu-id="c13d5-104">MRTK v2 시작</span><span class="sxs-lookup"><span data-stu-id="c13d5-104">Getting started with MRTK v2</span></span>

## <a name="mrtk-getting-started-guide"></a><span data-ttu-id="c13d5-105">MRTK 시작 가이드</span><span class="sxs-lookup"><span data-stu-id="c13d5-105">MRTK Getting Started Guide</span></span>
<span data-ttu-id="c13d5-106">MRTK v 2를 시작 하는 방법에 대 한 자세한 내용은 [mrtk 시작 가이드](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c13d5-106">See the [MRTK getting started guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) for detailed information on getting started with MRTK V2.</span></span>

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="c13d5-107">혼합 현실 도구 키트 (MRTK) 란?</span><span class="sxs-lookup"><span data-stu-id="c13d5-107">What is Mixed Reality Toolkit (MRTK)?</span></span>
<span data-ttu-id="c13d5-108">MRTK는 HoloLens가 처음 출시 된 후에 발생 하는 놀라운 오픈 소스 도구 키트 이며, 오늘날 개발자 커뮤니티의 하드 작업 없이는 오늘날 어디에서 나 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c13d5-108">The MRTK is an amazing open source toolkit that has been around since the HoloLens was first released, and would not be where it is today without the hard work of our developer community who have contributed to it.</span></span> <span data-ttu-id="c13d5-109">지난 3 년간 개발자 커뮤니티의 피드백을 수신 하 고 MRTK v 2를 구축 하 여 가장 중요 한 문제를 고려 했습니다.</span><span class="sxs-lookup"><span data-stu-id="c13d5-109">Over the past 3 years, we have listened to the feedback of our developer community, and built MRTK v2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="c13d5-110">Unity가 포함된 MRTK v2는 혼합 현실 애플리케이션용 오픈 소스 플랫폼 간 개발 키트입니다.</span><span class="sxs-lookup"><span data-stu-id="c13d5-110">The MRTK v2 with Unity is an open source cross-platform development kit for mixed reality applications.</span></span>  <span data-ttu-id="c13d5-111">MRTK 버전 2는 Microsoft HoloLens, Windows Mixed Reality 몰입형(VR) 헤드셋 및 OpenVR 플랫폼을 대상으로 하는 애플리케이션의 개발을 가속화하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c13d5-111">MRTK version 2 is intended to accelerate development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets and OpenVR platform.</span></span> <span data-ttu-id="c13d5-112">이 프로젝트는 항목에 대 한 장벽을 줄이고, 혼합 현실 응용 프로그램을 만들고, 모든 성장에 따라 커뮤니티에 다시 기여 하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c13d5-112">The project is aimed at reducing barriers to entry, to create mixed reality applications and contribute back to the community as we all grow.</span></span> 

<span data-ttu-id="c13d5-113">자세히 알아보려면 [Mrtk 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c13d5-113">See the [MRTK documentation portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) to learn more.</span></span>

## <a name="new-with-mrtk-v2"></a><span data-ttu-id="c13d5-114">MRTK v2에서 새로 만들기</span><span class="sxs-lookup"><span data-stu-id="c13d5-114">New with MRTK v2</span></span>
<span data-ttu-id="c13d5-115">이러한 플랫폼 도구에 대 한 약속을 스트레스 하고자 합니다.</span><span class="sxs-lookup"><span data-stu-id="c13d5-115">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="c13d5-116">실제로는 MRTK 버전 2를 활용 하 여 설치 환경 (OOBE) 및 혼합 현실 학습 응용 프로그램 등의 수신함 환경을 개발 했습니다.</span><span class="sxs-lookup"><span data-stu-id="c13d5-116">In fact, we leveraged MRTK version 2 to develop our inbox experiences, such as the setup experience (OOBE) and our Mixed Reality Learning application.</span></span>  <span data-ttu-id="c13d5-117">플랫폼에서 개발 하는 것이 가장 좋은 방법 이라고 생각 하기 때문에 MRTK를 통해 처음에 제공 되는 새로운 HoloLens 2 기능이 표시 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c13d5-117">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="c13d5-118">방식</span><span class="sxs-lookup"><span data-stu-id="c13d5-118">Modular</span></span>
<span data-ttu-id="c13d5-119">모듈식 방식으로 빌드 되었으므로 도구 키트의 모든 비트를 프로젝트에 적용할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c13d5-119">We have built it in a modular way, so there's no need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="c13d5-120">실제로 몇 가지 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c13d5-120">There are actually a few benefits to this.</span></span>  <span data-ttu-id="c13d5-121">이를 통해 프로젝트 크기를 더 작게 유지 하 고 쉽게 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c13d5-121">It keeps your project size smaller, and makes it easier to manage.</span></span>  <span data-ttu-id="c13d5-122">또한 스크립트 가능한 개체를 사용 하 여 빌드 되었으며 인터페이스를 기반으로 하기 때문에 사용자 고유의 구성 요소를 대체 하 여 다른 서비스, 시스템 및 플랫폼을 지원할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c13d5-122">Additionally, because it’s built with scriptable objects and is interface-driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>

### <a name="cross-platform"></a><span data-ttu-id="c13d5-123">플랫폼 간</span><span class="sxs-lookup"><span data-stu-id="c13d5-123">Cross-platform</span></span>
<span data-ttu-id="c13d5-124">다른 플랫폼의 경우 플랫폼 간 지원이 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c13d5-124">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="c13d5-125">이는 모든 단일 플랫폼이 기본적으로 지원 되는 것을 의미 하지는 않지만 빌드 대상을 다른 플랫폼으로 전환 하면 도구 키트 코드가 중단 되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="c13d5-125">And while this doesn’t mean every single platform is supported out of the box, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="c13d5-126">모듈식 디자인을 사용한 견고성과 확장성은 ARCore, Arcore 및 OpenVR와 같은 여러 플랫폼을 지원할 수 있는 좋은 경로를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c13d5-126">The robustness and extensibility with the modular design sets you up on a good path to be able to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>

### <a name="performant"></a><span data-ttu-id="c13d5-127">성능과</span><span class="sxs-lookup"><span data-stu-id="c13d5-127">Performant</span></span>
<span data-ttu-id="c13d5-128">모바일 플랫폼을 사용 하 여 작업 하는 경우 성능을 염두에 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c13d5-128">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="c13d5-129">이는 매우 중요 하며, 도구가 사용자에 대해 작동 하지 않도록 하는 데 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="c13d5-129">This is super important, and we wanted to ensure that the tools are not going to work against you.</span></span>

## <a name="see-also"></a><span data-ttu-id="c13d5-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c13d5-130">See also</span></span>
* [<span data-ttu-id="c13d5-131">MRTK 시작 가이드</span><span class="sxs-lookup"><span data-stu-id="c13d5-131">MRTK getting started guide</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="c13d5-132">MRTK 설명서 홈</span><span class="sxs-lookup"><span data-stu-id="c13d5-132">MRTK documentation home</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="c13d5-133">도구 설치</span><span class="sxs-lookup"><span data-stu-id="c13d5-133">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="c13d5-134">HTK/MRTK에서 MRTK 버전 2로 포팅</span><span class="sxs-lookup"><span data-stu-id="c13d5-134">Porting from HTK/MRTK to MRTK version 2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
