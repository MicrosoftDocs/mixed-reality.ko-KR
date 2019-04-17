---
title: MRTK 버전 2 사용 하 여 시작
description: 새 MRTK 활용 하려는 개발자를 위한
author: grbury
ms.author: grbury
ms.date: 02/22/19
ms.topic: article
keywords: Windows Mixed Reality, 테스트, MRTK 버전 2, MRTK, 도구, SDK, HoloLens, HoloLens 2
ms.openlocfilehash: 44e5fe0fd4384af68922eda4bcb0594d39a1c1b7
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600030"
---
# <a name="getting-started-with-mrtk-version-2"></a><span data-ttu-id="51d6e-104">MRTK 버전 2 사용 하 여 시작</span><span class="sxs-lookup"><span data-stu-id="51d6e-104">Getting started with MRTK version 2</span></span>

<span data-ttu-id="51d6e-105">MRTK가 처음 출시 되는 HoloLens 이므로 없습니다 경우 현재 해당 하는 개발자 커뮤니티의 어려운 작업 없이 관련 된 멋진 오픈 소스 도구 키트입니다.</span><span class="sxs-lookup"><span data-stu-id="51d6e-105">The MRTK is an amazing open source toolkit that has been around since the HoloLens was first released, and would not be where it is today without the hard work of our developer community who have contributed to it.</span></span> <span data-ttu-id="51d6e-106">지난 3 년 동안 개발자 커뮤니티의 피드백을 수신 하 고 작성 MRTK 버전 2는 가장 큰 문제를 고려해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51d6e-106">Over the past 3 years, we have listened to the feedback of our developer community, and built MRTK version 2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="51d6e-107">Unity 사용 하 여 버전 2 MRTK 혼합된 현실 응용 프로그램에는 오픈 소스 플랫폼 간 개발 키트입니다.</span><span class="sxs-lookup"><span data-stu-id="51d6e-107">The MRTK version 2 with Unity is an open source cross-platform development kit for mixed reality applications.</span></span>  <span data-ttu-id="51d6e-108">Microsoft HoloLens, (VR) 헤드셋을 몰입 형 Windows Mixed Reality 및 OpenVR 플랫폼을 대상으로 하는 응용 프로그램의 개발을 가속화 MRTK 버전 2 것입니다.</span><span class="sxs-lookup"><span data-stu-id="51d6e-108">MRTK version 2 is intended to accelerate development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets and OpenVR platform.</span></span> <span data-ttu-id="51d6e-109">프로젝트는 장벽이 혼합된 현실 응용 프로그램을 만들고 우리가 증가 함에 따라 커뮤니티에 다시 기여에 항목을 줄이는 목표로 합니다.</span><span class="sxs-lookup"><span data-stu-id="51d6e-109">The project is aimed at reducing barriers to entry to create mixed reality applications and contribute back to the community as we all grow.</span></span> 


<span data-ttu-id="51d6e-110">참조 된 <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/wiki/Getting-Started-with-MRTK-v2" target="_blank">MRTK 버전 2 wiki</a> 를 시작 하 고 자세한 정보.</span><span class="sxs-lookup"><span data-stu-id="51d6e-110">See the <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/wiki/Getting-Started-with-MRTK-v2" target="_blank">MRTK version 2 wiki</a> to get started and learn more.</span></span>

## <a name="new-with-mrtk-version-2"></a><span data-ttu-id="51d6e-111">MRTK 버전 2 사용 하 여 새</span><span class="sxs-lookup"><span data-stu-id="51d6e-111">New with MRTK version 2</span></span>
<span data-ttu-id="51d6e-112">노력의 일환으로 이러한 플랫폼 도구 스트레스 하고자 합니다.</span><span class="sxs-lookup"><span data-stu-id="51d6e-112">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="51d6e-113">사실, 받은 편지함 경험 설치 환경 (OOBE) 등이 혼합 현실 학습 응용 프로그램을 개발 하려면 MRTK 버전 2 활용 했습니다.</span><span class="sxs-lookup"><span data-stu-id="51d6e-113">In fact, we leveraged MRTK version 2 to develop our inbox experiences, such as the setup experience (OOBE) and our Mixed Reality Learning application.</span></span>  <span data-ttu-id="51d6e-114">플랫폼에서 개발 하는 가장 좋은 방법은 것 때문에 먼저 MRTK를 통해서도 새 HoloLens 2 기능을 확인 하려면 예상할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51d6e-114">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="51d6e-115">모듈식</span><span class="sxs-lookup"><span data-stu-id="51d6e-115">Modular</span></span>
<span data-ttu-id="51d6e-116">빌드 했습니다이 모듈식 방식으로 프로젝트에 도구 키트의 모든 비트를 수행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="51d6e-116">We have built it in a modular way, so that you do not need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="51d6e-117">이 실제로 몇 가지 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51d6e-117">There are actually a few benefits to this.</span></span>  <span data-ttu-id="51d6e-118">또한 프로젝트 크기를 작게 유지 뿐만 관리 하기가 쉬워집니다.</span><span class="sxs-lookup"><span data-stu-id="51d6e-118">It keeps your project size smaller, as well as makes it easier to manage.</span></span>  <span data-ttu-id="51d6e-119">위쪽에, 있기 때문에 스크립트 가능한 개체를 사용 하 여 빌드되어 인터페이스 제어 되 고도 포함 되어 있는 다른 서비스, 시스템 및 플랫폼을 지원 하기 위해 고유한 구성 요소를 대체할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51d6e-119">On top of that, because it’s built with scriptable objects and is interface driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>


### <a name="cross-platform"></a><span data-ttu-id="51d6e-120">플랫폼 간</span><span class="sxs-lookup"><span data-stu-id="51d6e-120">Cross-platform</span></span>
<span data-ttu-id="51d6e-121">다른 플랫폼의 설명 하자면이 플랫폼 간 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="51d6e-121">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="51d6e-122">및 다른 플랫폼 빌드 대상 전환할 때 중단 toolkit 코드 없음 확인 했 동안 모든 단일 플랫폼은 기본적으로 지원 되는 뜻입니다.</span><span class="sxs-lookup"><span data-stu-id="51d6e-122">And while this doesn’t mean every single platform is supported out of the box, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="51d6e-123">견고성 및 모듈식 디자인을 사용 하 여 확장성을 설정 합니다 ARCore, ARKit 및 OpenVR 같은 여러 플랫폼을 지원할 수에 대 한 적절 한 경로에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51d6e-123">The robustness and extensibility with the modular design sets you up on a good path to be able to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>


### <a name="performant"></a><span data-ttu-id="51d6e-124">고성능</span><span class="sxs-lookup"><span data-stu-id="51d6e-124">Performant</span></span>
<span data-ttu-id="51d6e-125">모바일 플랫폼을 사용 했습니다 생성 성능을 염두에서를 사용 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="51d6e-125">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="51d6e-126">이 매우 중요 하 고 도구는 수에 대해 작동 하도록 하지 확인 하려고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="51d6e-126">This is super important, and we wanted to ensure that the tools are not going to work against you.</span></span>


## <a name="see-also"></a><span data-ttu-id="51d6e-127">참조</span><span class="sxs-lookup"><span data-stu-id="51d6e-127">See also</span></span>
* [<span data-ttu-id="51d6e-128">도구 설치</span><span class="sxs-lookup"><span data-stu-id="51d6e-128">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="51d6e-129">HTK/MRTK에서 MRTK 버전 2로 이식</span><span class="sxs-lookup"><span data-stu-id="51d6e-129">Porting from HTK/MRTK to MRTK version 2</span></span>](mrtk-porting-guide.md)
