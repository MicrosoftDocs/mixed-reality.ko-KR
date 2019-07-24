---
title: 사례 연구-Lowe의 부엌 단원
description: HoloLens 팀은 Lowe의 HoloLens 프로젝트에서 파생 된 몇 가지 모범 사례를 공유 하려고 합니다.
author: BrandonBray
ms.author: kevincol
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Lowe의, HoloLens, 주방, 사례 연구
ms.openlocfilehash: 24759f90b8b84ec19e644fb8dff44f64c3ab81d2
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522349"
---
# <a name="case-study---lessons-from-the-lowes-kitchen"></a><span data-ttu-id="bb651-104">사례 연구-Lowe의 부엌 단원</span><span class="sxs-lookup"><span data-stu-id="bb651-104">Case study - Lessons from the Lowe's kitchen</span></span>

<span data-ttu-id="bb651-105">HoloLens 팀은 Lowe의 HoloLens 프로젝트에서 파생 된 몇 가지 모범 사례를 공유 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb651-105">The HoloLens team wants to share some of the best practices that were derived from the Lowe's HoloLens project.</span></span> <span data-ttu-id="bb651-106">다음은 Satya의 2016 Ignite 키 노트에서 보여 주는 Lowe의 HoloLens에 대 한 비디오입니다.</span><span class="sxs-lookup"><span data-stu-id="bb651-106">Below is a video of the Lowe's HoloLens projected demonstrated at Satya's 2016 Ignite keynote.</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/gC_4JxF0e_k]

## <a name="lowes-hololens-best-practices"></a><span data-ttu-id="bb651-107">Lowe의 HoloLens 모범 사례</span><span class="sxs-lookup"><span data-stu-id="bb651-107">Lowe's HoloLens Best Practices</span></span>

<span data-ttu-id="bb651-108">두 개의 비디오에서는 4 월 2016 이후 두 Lowe의 상점에 있었던 Lowe의 HoloLens 파일럿에서 파생 된 모범 사례를 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="bb651-108">The two videos cover best practices that were derived from the Lowe's HoloLens Pilot that has been in two Lowe's stores since April 2016.</span></span> <span data-ttu-id="bb651-109">주요 항목은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bb651-109">The key topics are:</span></span>
* <span data-ttu-id="bb651-110">모바일 장치에 대 한 성능 최대화</span><span class="sxs-lookup"><span data-stu-id="bb651-110">Maximize performance for a mobile device</span></span>
* <span data-ttu-id="bb651-111">Full holographic 프레임을 사용 하 여 UX 메서드 만들기 (2 차 통신)</span><span class="sxs-lookup"><span data-stu-id="bb651-111">Create UX methods with a full holographic frame (2nd talk)</span></span>
* <span data-ttu-id="bb651-112">전체 자릿수 맞춤 (두 번째 대화)</span><span class="sxs-lookup"><span data-stu-id="bb651-112">Precision alignment (2nd talk)</span></span>
* <span data-ttu-id="bb651-113">공유 holographic 환경 (두 번째 대화)</span><span class="sxs-lookup"><span data-stu-id="bb651-113">Shared holographic experiences (2nd talk)</span></span>
* <span data-ttu-id="bb651-114">고객과 상호 작용 (두 번째 대화)</span><span class="sxs-lookup"><span data-stu-id="bb651-114">Interacting with customers (2nd talk)</span></span>

## <a name="video-1"></a><span data-ttu-id="bb651-115">비디오 1</span><span class="sxs-lookup"><span data-stu-id="bb651-115">Video 1</span></span>

<span data-ttu-id="bb651-116">**모바일 장치에 대 한 성능 최대화** HoloLens는 장치에서 모든 처리가 발생 하는 작업할 장치입니다.</span><span class="sxs-lookup"><span data-stu-id="bb651-116">**Maximize performance for a mobile device** HoloLens is an untethered device with all the processing taking place in the device.</span></span> <span data-ttu-id="bb651-117">모바일 플랫폼이 필요 하며 모바일 응용 프로그램을 만드는 것과 비슷한 마음가짐이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb651-117">This requires a mobile platform and requires a mindset similar to creating mobile applications.</span></span> <span data-ttu-id="bb651-118">사용자에 게 맛 있는 환경을 제공 하기 위해 HoloLens 응용 프로그램에서 60FPS를 유지 관리 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="bb651-118">Microsoft recommends that your HoloLens application maintain 60FPS to provide a delicious experience for your users.</span></span> <span data-ttu-id="bb651-119">FPS가 낮으면 holograms가 불안정 해질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb651-119">Having low FPS can result in unstable holograms.</span></span>

<span data-ttu-id="bb651-120">HoloLens에서 개발할 때 고려할 가장 중요 한 사항은 사용자 지정 셰이더 ( [Hololens Toolkit](https://github.com/Microsoft/HoloToolkit-Unity)에서 무료로 제공)를 사용 하 여 자산 최적화/decimation입니다.</span><span class="sxs-lookup"><span data-stu-id="bb651-120">Some of the most important things to look at when developing on HoloLens is asset optimization/decimation, using custom shaders (available for free in the [HoloLens Toolkit](https://github.com/Microsoft/HoloToolkit-Unity)).</span></span> <span data-ttu-id="bb651-121">또 다른 중요 한 고려 사항은 프로젝트의 시작 부분에서 프레임 속도로 측정 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="bb651-121">Another important consideration is to measure the frame rate from the very beginning of your project.</span></span> <span data-ttu-id="bb651-122">프로젝트에 따라 자산을 표시 하는 순서가 큰 참가자로 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb651-122">Depending on the project, the order of displaying your assets can also be a big contributor</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/o0QIPwgiP9A]

## <a name="video-2"></a><span data-ttu-id="bb651-123">비디오 2</span><span class="sxs-lookup"><span data-stu-id="bb651-123">Video 2</span></span>

<span data-ttu-id="bb651-124">**전체 holographic 프레임으로 UX 메서드 만들기** 실제 세계의 holograms 배치를 이해 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb651-124">**Create UX methods with a full holographic frame** It's important to understand the placement of holograms in a physical world.</span></span> <span data-ttu-id="bb651-125">Lowe는 holograms의 더 큰 환경을 볼 때 사용자가 holograms 경험 하는 데 도움이 되는 다양 한 UX 방법에 대해 이야기 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb651-125">With Lowe's we talk about different UX methods that help users experience holograms up close while still seeing the larger environment of holograms.</span></span>

<span data-ttu-id="bb651-126">**전체 자릿수 맞춤** Lowe의 시나리오에서 실제 부엌에 대 한 holograms의 전체 자릿수 맞춤을 구현 하는 것이 가장 중요 했습니다.</span><span class="sxs-lookup"><span data-stu-id="bb651-126">**Precision alignment** For the Lowe's scenario, it was paramount to the experience to have precision alignment of the holograms to the physical kitchen.</span></span> <span data-ttu-id="bb651-127">Microsoft는 사용자가 물리적 환경에서 변경한 유도 환경을 보장 하는 데 도움이 되는 기술에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb651-127">We discuss techniques helps ensure an experience that convinces users that their physical environment has changed.</span></span>

<span data-ttu-id="bb651-128">**공유 holographic 환경** 결합는 Lowe의 경험을 사용 하는 기본 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="bb651-128">**Shared holographic experiences** Couples are the primary way that the Lowe's experience is consumed.</span></span> <span data-ttu-id="bb651-129">한 사람이 상판를 변경 하 고 다른 사용자가 변경 내용을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb651-129">One person can change the countertop and the other person will see the changes.</span></span> <span data-ttu-id="bb651-130">이 "공유 환경" 이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb651-130">We called this "shared experiences".</span></span>

<span data-ttu-id="bb651-131">**고객과 상호 작용** Lowe의 디자이너는 HoloLens를 사용 하지 않지만 고객이 볼 수 있는 항목을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb651-131">**Interacting with customers** Lowe's designers are not using a HoloLens, but they need to see what the customers are seeing.</span></span> <span data-ttu-id="bb651-132">Microsoft는 UWP 응용 프로그램에서 고객이 볼 수 있는 사항을 캡처하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bb651-132">We show how to capture what the customer is seeing on a UWP application.</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/LceMdyKZ4PI]
