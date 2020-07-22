---
title: MRTK 버전 2 시작
description: MRTK를 활용하는 데 관심이 있는 새 개발자를 대상으로 합니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, 테스트, Mixed Reality Toolkit, MRTK 버전 2, MRTK, 도구, SDK, HoloLens, HoloLens 2
ms.openlocfilehash: a7fdd7b199530b38fb0921baa57d9783fa45672a
ms.sourcegitcommit: 8daefb763d1f23fe02b95b766b00b373f04c5c2d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/17/2020
ms.locfileid: "86447896"
---
# <a name="getting-started-with-mrtk-for-unity"></a><span data-ttu-id="a5096-104">Unity용 MRTK 시작</span><span class="sxs-lookup"><span data-stu-id="a5096-104">Getting started with MRTK for Unity</span></span>
![MRTK](images/UX/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="a5096-106">MRTK(Mixed Reality Toolkit)란?</span><span class="sxs-lookup"><span data-stu-id="a5096-106">What is Mixed Reality Toolkit (MRTK)?</span></span>
<span data-ttu-id="a5096-107">HoloLens가 처음 출시된 이후로 활성화된 MRTK는 놀라운 오픈 소스 도구 키트이며, 이에 기여한 개발자 커뮤니티의 노력이 없었으면 지금의 위치에 있지 못했을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a5096-107">The MRTK is an amazing open source toolkit that has been around since the HoloLens was first released, and would not be where it is today without the hard work of our developer community who have contributed to it.</span></span> <span data-ttu-id="a5096-108">가장 중요한 문제를 고려하기 위해 지난 3년간 개발자 커뮤니티의 피드백을 주의 깊게 살피면서 MRTK v2를 구축했습니다.</span><span class="sxs-lookup"><span data-stu-id="a5096-108">Over the past 3 years, we have listened to the feedback of our developer community, and built MRTK v2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="a5096-109">Unity용 MRTK는 혼합 현실 애플리케이션을 위한 오픈 소스 플랫폼 간 개발 키트입니다.</span><span class="sxs-lookup"><span data-stu-id="a5096-109">MRTK for Unity is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="a5096-110">MRTK는 플랫폼 간 입력 시스템, 기본 구성 요소 및 공간 상호 작용을 위한 공통 빌딩 블록을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a5096-110">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="a5096-111">MRTK 버전 2는 Microsoft HoloLens, Windows Mixed Reality 몰입형(VR) 헤드셋 및 OpenVR 플랫폼을 대상으로 하는 애플리케이션의 개발을 가속화하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a5096-111">MRTK version 2 is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets and OpenVR platform.</span></span> <span data-ttu-id="a5096-112">이 프로젝트는 진입 장벽을 낮추고 혼합 현실 애플리케이션을 만들며 커뮤니티에 다시 기여하는 것을 목표로 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5096-112">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

<span data-ttu-id="a5096-113">자세한 내용은 [GitHub에 대한 MRTK 설명서](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a5096-113">See the [MRTK's documentation on GitHub](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) to explore more.</span></span>

## <a name="new-with-mrtk-v2"></a><span data-ttu-id="a5096-114">MRTK v2의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="a5096-114">New with MRTK v2</span></span>
<span data-ttu-id="a5096-115">여기서는 이러한 플랫폼 도구에 대한 약속을 강조하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5096-115">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="a5096-116">실제로 MRTK 버전 2를 활용하여 설정 환경(OOBE) 및 Mixed Reality 학습 애플리케이션과 같은 받은 편지함 환경을 개발했습니다.</span><span class="sxs-lookup"><span data-stu-id="a5096-116">In fact, we leveraged MRTK version 2 to develop our inbox experiences, such as the setup experience (OOBE) and our Mixed Reality Learning application.</span></span>  <span data-ttu-id="a5096-117">또한 플랫폼에서 개발하는 것이 가장 좋은 방법이라고 생각하므로 새로운 HoloLens 2 기능이 MRTK를 통해 처음 공개될 것으로 예상할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5096-117">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="a5096-118">모듈식</span><span class="sxs-lookup"><span data-stu-id="a5096-118">Modular</span></span>
<span data-ttu-id="a5096-119">모듈식으로 빌드했으므로 도구 키트의 모든 비트를 프로젝트에 적용할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a5096-119">We have built it in a modular way, so there's no need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="a5096-120">실제로 몇 가지 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5096-120">There are actually a few benefits to this.</span></span>  <span data-ttu-id="a5096-121">이를 통해 프로젝트 크기를 더 작게 유지하고 관리하기가 더 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="a5096-121">It keeps your project size smaller, and makes it easier to manage.</span></span>  <span data-ttu-id="a5096-122">또한 스크립트 가능한 개체를 사용하여 빌드되고 인터페이스를 기반으로 하므로 포함된 구성 요소를 사용자 고유의 구성 요소로 바꿔 다른 서비스, 시스템 및 플랫폼을 지원할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5096-122">Additionally, because it’s built with scriptable objects and is interface-driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>

### <a name="cross-platform"></a><span data-ttu-id="a5096-123">플랫폼 간</span><span class="sxs-lookup"><span data-stu-id="a5096-123">Cross-platform</span></span>
<span data-ttu-id="a5096-124">다른 플랫폼과 관련하여 플랫폼 간 지원이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5096-124">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="a5096-125">이는 모든 단일 플랫폼이 기본적으로 지원된다는 것을 의미하지는 않지만, 빌드 대상을 다른 플랫폼으로 전환할 때 도구 키트 코드가 중단되지 않도록 했습니다.</span><span class="sxs-lookup"><span data-stu-id="a5096-125">And while this doesn’t mean every single platform is supported out of the box, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="a5096-126">모듈식 설계를 통한 견고성과 확장성은 ARCore, ARKit 및 OpenVR과 같은 여러 플랫폼을 지원할 수 있는 좋은 경로를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a5096-126">The robustness and extensibility with the modular design sets you up on a good path to be able to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>

### <a name="performant"></a><span data-ttu-id="a5096-127">성능 기준에 적합</span><span class="sxs-lookup"><span data-stu-id="a5096-127">Performant</span></span>
<span data-ttu-id="a5096-128">모바일 플랫폼을 사용하는 경우 성능을 고려하여 구축했습니다.</span><span class="sxs-lookup"><span data-stu-id="a5096-128">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="a5096-129">이는 매우 중요하며, 도구가 사용자에게 불리하게 작동하지 않도록 보장하려고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="a5096-129">This is super important, and we wanted to ensure that the tools are not going to work against you.</span></span>

## <a name="see-also"></a><span data-ttu-id="a5096-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a5096-130">See also</span></span>
* [<span data-ttu-id="a5096-131">MRTK 시작 가이드</span><span class="sxs-lookup"><span data-stu-id="a5096-131">MRTK getting started guide</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="a5096-132">MRTK 설명서 홈</span><span class="sxs-lookup"><span data-stu-id="a5096-132">MRTK documentation home</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="a5096-133">도구 설치</span><span class="sxs-lookup"><span data-stu-id="a5096-133">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="a5096-134">HTK/MRTK에서 MRTK 버전 2로 포팅</span><span class="sxs-lookup"><span data-stu-id="a5096-134">Porting from HTK/MRTK to MRTK version 2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
