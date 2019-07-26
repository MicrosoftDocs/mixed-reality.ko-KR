---
title: 직접 및 동작 컨트롤러
description: 직접 및 동작 컨트롤러 상호 작용 개요
author: shengkait
ms.author: shengkait
ms.date: 04/26/2019
ms.topic: article
keywords: 혼합 현실, 손, 동작 제어, 상호 작용, 디자인
ms.openlocfilehash: b6efb0a9651cad8eee9b80bb130aa1a85b9a9941
ms.sourcegitcommit: 76a7aa6e64e114b63ace058dd6d6d662b3c9f09e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68507864"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="b93be-104">직접 및 동작 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="b93be-104">Hands and motion controllers</span></span>
## <a name="scenarios"></a><span data-ttu-id="b93be-105">시나리오</span><span class="sxs-lookup"><span data-stu-id="b93be-105">Scenarios</span></span>
<span data-ttu-id="b93be-106">[디자인 지침](interaction-fundamentals.md)을 읽은 후이 상호 작용 모델을 채택 하도록 선택 하는 경우 사용자가 holographic와 상호 작용 하는 데 두 개의 손을 사용 하도록 요구 하는 응용 프로그램을 개발 하 고 있음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="b93be-106">If you choose to adopt this interaction model after reading the [design guidelines](interaction-fundamentals.md), it means that you are developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="b93be-107">응용 프로그램은 가상과 물리적 간의 boundry을 제거 하는 목표를 달성 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b93be-107">Your application is going to achieve the goal of removing the boundry between virtual and physical.</span></span>

<span data-ttu-id="b93be-108">몇 가지 특정 시나리오는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b93be-108">Some specific scenarios might be:</span></span>
* <span data-ttu-id="b93be-109">정보 근로자 2D 가상 화면 및 Ui를 제공 하 여 콘텐츠 표시 및 제어</span><span class="sxs-lookup"><span data-stu-id="b93be-109">Providing information workers 2D vitual screens and UIs to display and control contents</span></span>
* <span data-ttu-id="b93be-110">공장 어셈블리 줄에 첫 번째 줄 작업자 자습서 및 가이드 제공</span><span class="sxs-lookup"><span data-stu-id="b93be-110">Providing first line workers tutorials and guides in factory assembly lines</span></span>
* <span data-ttu-id="b93be-111">의료 전문가 지원 및 교육을 위한 전문 도구 개발</span><span class="sxs-lookup"><span data-stu-id="b93be-111">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="b93be-112">3D 가상 개체를 사용 하 여 실제 세계를 장식 하거나 두 번째 세계를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b93be-112">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="b93be-113">실제 세계를 배경으로 사용 하 여 위치 기반 서비스 및 게임 만들기</span><span class="sxs-lookup"><span data-stu-id="b93be-113">Creating location based services and games using the real world as background</span></span>

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="b93be-114">손 및 동작 컨트롤러 소프트웨어나</span><span class="sxs-lookup"><span data-stu-id="b93be-114">Hands and motion controllers modalities</span></span>
### <a name="direct-manipulation-with-handsdirect-manipulationmd"></a>[<span data-ttu-id="b93be-115">수동으로 직접 조작</span><span class="sxs-lookup"><span data-stu-id="b93be-115">Direct manipulation with hands</span></span>](direct-manipulation.md)
<span data-ttu-id="b93be-116">이는 사용자가 직접 holograms를 터치 하 고 조작할 수 있는 손을 활용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b93be-116">This is a modality leveraging the power of hands, with which users are capable of touching and manipulating the holograms directly.</span></span> <span data-ttu-id="b93be-117">일상의 경험을 leaveraging 하 고 적절 한 시각적 affordances 제공 하 여 사용자는 실제 개체를 조작 하는 것과 동일한 방식으로 가상 시스템과 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b93be-117">By leaveraging daily life experiences and providing proper visual affordances, users are able to use the same way of manipulating real world objects to interact with virtual ones.</span></span>   

### <a name="point-and-commit-with-handspoint-and-commitmd"></a>[<span data-ttu-id="b93be-118">수동으로 가리키고 커밋</span><span class="sxs-lookup"><span data-stu-id="b93be-118">Point and commit with hands</span></span>](point-and-commit.md)
<span data-ttu-id="b93be-119">이를 통해 사용자는 거리가 holograms 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b93be-119">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="b93be-120">사용자가 주변 환경을 최대한 활용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="b93be-120">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="b93be-121">사용자는 어디 든 지 holograms를 배치할 수 있으며 모든 거리에서 계속 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b93be-121">Users can place holograms anywhere and can still access them from any distances.</span></span> <span data-ttu-id="b93be-122">2D 및 3D holograms을 제어 하 고 조작 하기 위한 멘 탈 모델 및 제스처는 직접 조작의 경우와 매우 동기화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b93be-122">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>

### <a name="motion-controllersmotion-controllersmd"></a>[<span data-ttu-id="b93be-123">모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="b93be-123">Motion controllers</span></span>](motion-controllers.md)
<span data-ttu-id="b93be-124">동작 컨트롤러는 하나 또는 두 손을 모두 사용 하는 동시에 다 수의 거리에서 정확한 상호 작용을 제공 하 여 사용자의 물리적 기능을 확장 하는 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="b93be-124">Motion controllers are tools that extend the user's physical capabilities by providing precise interactions across a large range of distances while using one or both hands.</span></span> <span data-ttu-id="b93be-125">이러한 하드웨어 액세서리는 널리 사용 되는 다양 한 상호 작용에 대 한 바로 가기를 제공 하 고 다양 한 작업에 대 한 tactile 피드백을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b93be-125">These hardware accessories provide shortcuts to many commonly-used interactions and provide surefooted, tactile feedback for a variety of actions.</span></span> <span data-ttu-id="b93be-126">현재 동작 컨트롤러는 WMR (Windows Mixed Reality) 시나리오 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b93be-126">Currently, motion controllers are only available for Windows Mixed Reality (WMR) scenarios.</span></span> 

![손 및 동작 컨트롤러의 비교 소프트웨어나](images/Hands-and-controllers-720px.jpg)<br>

<span data-ttu-id="b93be-128">*손 및 동작 컨트롤러의 비교 소프트웨어나*</span><span class="sxs-lookup"><span data-stu-id="b93be-128">*Comparison of hands and motion controllers modalities*</span></span>

## <a name="see-also"></a><span data-ttu-id="b93be-129">참조</span><span class="sxs-lookup"><span data-stu-id="b93be-129">See also</span></span>
* [<span data-ttu-id="b93be-130">헤드 게이즈 및 커밋</span><span class="sxs-lookup"><span data-stu-id="b93be-130">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="b93be-131">헤드 게이즈 및 유지</span><span class="sxs-lookup"><span data-stu-id="b93be-131">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="b93be-132">수동으로 직접 조작</span><span class="sxs-lookup"><span data-stu-id="b93be-132">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="b93be-133">수동으로 가리키고 커밋</span><span class="sxs-lookup"><span data-stu-id="b93be-133">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="b93be-134">핸즈프리</span><span class="sxs-lookup"><span data-stu-id="b93be-134">Hands-free</span></span>](hands-free.md)
