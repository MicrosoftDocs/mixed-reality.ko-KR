---
title: 실습 및 동작 컨트롤러
description: 실습 및 동작 컨트롤러 상호 작용에 대 한 개요
author: shengkait
ms.author: shengkait
ms.date: 04/26/2019
ms.topic: article
keywords: 혼합 현실을, 실습, 동작 controlles, 상호 작용 디자인
ms.openlocfilehash: b13efadd111ca970abe625221fb8045644822c37
ms.sourcegitcommit: b5bad4eeb5cdd0c2a7b639442656c306e8b5853b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65813977"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="ed99f-104">실습 및 동작 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="ed99f-104">Hands and motion controllers</span></span>
## <a name="scenarios"></a><span data-ttu-id="ed99f-105">시나리오</span><span class="sxs-lookup"><span data-stu-id="ed99f-105">Scenarios</span></span>
<span data-ttu-id="ed99f-106">이 상호 작용 모델을 읽은 후 채택 하려는 경우는 [디자인 지침](interaction-fundamentals.md), 두 손을 holographic 세계와 상호 작용 하는 데 사용자가 응용 프로그램을 개발 하는 경우를 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed99f-106">If you choose to adopt this interaction model after reading the [design guidelines](interaction-fundamentals.md), it means that you are developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="ed99f-107">응용 프로그램은 가상 및 실제 간의 경계를 제거 하는 목표를 달성 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed99f-107">Your application is going to achieve the goal of removing the boundry between virtual and physical.</span></span>

<span data-ttu-id="ed99f-108">일부 특정 시나리오는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ed99f-108">Some specific scenarios might be:</span></span>
* <span data-ttu-id="ed99f-109">정보 근로자 2D 가상 화면 및 표시 하 고 콘텐츠를 제어 하는 Ui를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed99f-109">Providing information workers 2D vitual screens and UIs to display and control contents</span></span>
* <span data-ttu-id="ed99f-110">첫 번째 줄 작업자 자습서 및 가이드 공장 어셈블리 라인에 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ed99f-110">Providing first line workers tutorials and guides in factory assembly lines</span></span>
* <span data-ttu-id="ed99f-111">지원 및 의료 전문가 교육에 대 한 전문적인 도구를 개발 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed99f-111">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="ed99f-112">가상 3D 개체를 사용 하 여 실제 데코 레이트 하 하거나 두 번째 권역 만들기</span><span class="sxs-lookup"><span data-stu-id="ed99f-112">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="ed99f-113">위치 기반 서비스 및 배경으로 실제 세계를 사용 하 여 게임</span><span class="sxs-lookup"><span data-stu-id="ed99f-113">Creating location based services and games using the real world as background</span></span>

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="ed99f-114">실습 및 동작 컨트롤러 형식</span><span class="sxs-lookup"><span data-stu-id="ed99f-114">Hands and motion controllers modalities</span></span>
### <a name="direct-manipulation-with-handsdirect-manipulationmd"></a>[<span data-ttu-id="ed99f-115">수동으로 직접 조작</span><span class="sxs-lookup"><span data-stu-id="ed99f-115">Direct manipulation with hands</span></span>](direct-manipulation.md)
<span data-ttu-id="ed99f-116">손으로, 사용자와 접촉 하 고는 홀로그램을 직접 조작 수 있는 기능을 활용 하는 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="ed99f-116">This is a modality leveraging the power of hands, with which users are capable of touching and manipulating the holograms directly.</span></span> <span data-ttu-id="ed99f-117">Leaveraging 이니셔티브를 일상 생활 환경을 적절 한 시각적 affordances 제공, 사용자 가상 애니메이션과 상호 작용을 실제 개체를 조작 하는 동일한 방식으로 사용할 수 있습니다. 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed99f-117">By leaveraging daily life experiences and providing proper visual affordances, users are able to use the same way of manipulating real world objects to interact with virtual ones.</span></span>   

### <a name="point-and-commit-with-handspoint-and-commitmd"></a>[<span data-ttu-id="ed99f-118">수동으로 가리키고 커밋</span><span class="sxs-lookup"><span data-stu-id="ed99f-118">Point and commit with hands</span></span>](point-and-commit.md)
<span data-ttu-id="ed99f-119">이 형식을 사용 하면 거리에서 홀로그램 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed99f-119">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="ed99f-120">사용자가 환경 최대한 활용할 수 있도록 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed99f-120">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="ed99f-121">사용자 제공을 원하는 위치에 배치할 수 및 모든 거리에서 여전히 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed99f-121">Users can place holograms anywhere and can still access them from any distances.</span></span> <span data-ttu-id="ed99f-122">멘 탈 모델 및 제어 하 고 조작 2D 및 3D 홀로그램 제스처를 항상 동기화 되었는지와 직접 조작 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed99f-122">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>

### <a name="motion-controllersmotion-controllersmd"></a>[<span data-ttu-id="ed99f-123">모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="ed99f-123">Motion controllers</span></span>](motion-controllers.md)
<span data-ttu-id="ed99f-124">동작 컨트롤러는 하나 또는 둘 다 실습을 사용 하는 동안 다양 한 거리에서 정확 하 게 상호 작용을 제공 하 여 사용자의 실제 용량을 확장 하는 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="ed99f-124">Motion controllers are tools that extend the users' physical capabilities by providing precise interactions across a large range of distances while using one or both hands.</span></span> <span data-ttu-id="ed99f-125">이러한 하드웨어 accessories 많은 일반적으로 사용 되는 상호 작용 및 제공 빠른, tactile 피드백에 대해 다양 한 작업에 대 한 바로 가기 키를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ed99f-125">These hardware accessories provide shortcuts to many commonly-used interactions and gives surefooted, tactile feedback for a variety of actions.</span></span> <span data-ttu-id="ed99f-126">현재 동작 컨트롤러는 WMR 시나리오에 사용할 수만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed99f-126">Currently, motion controllers are only available for WMR scenarios.</span></span> 

![](images/Hands-and-controllers-720px.jpg)<br>

## <a name="see-also"></a><span data-ttu-id="ed99f-127">참조</span><span class="sxs-lookup"><span data-stu-id="ed99f-127">See also</span></span>
* [<span data-ttu-id="ed99f-128">헤드 게이즈 및 커밋</span><span class="sxs-lookup"><span data-stu-id="ed99f-128">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="ed99f-129">(근처 직접 상호 작용)을 직접 조작</span><span class="sxs-lookup"><span data-stu-id="ed99f-129">Direct manipulation (Near hand interaction)</span></span>](direct-manipulation.md)
* [<span data-ttu-id="ed99f-130">지점 및 커밋 (극동 직접 상호 작용)</span><span class="sxs-lookup"><span data-stu-id="ed99f-130">Point and commit (Far hand interaction)</span></span>](point-and-commit.md)
* [<span data-ttu-id="ed99f-131">핸즈프리</span><span class="sxs-lookup"><span data-stu-id="ed99f-131">Hands-free</span></span>](hands-free.md)
* [<span data-ttu-id="ed99f-132">응시 및 유지</span><span class="sxs-lookup"><span data-stu-id="ed99f-132">Gaze and dwell</span></span>](gaze-targeting.md)
