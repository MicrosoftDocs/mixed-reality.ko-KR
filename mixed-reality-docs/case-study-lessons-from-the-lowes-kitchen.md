---
title: 사례 연구-Lowe의 주방 교훈
description: HoloLens 팀 Lowe의 HoloLens 프로젝트에서 파생 된 모범 사례 중 일부를 공유 하려고 합니다.
author: BrandonBray
ms.author: kevincol
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality Lowe의, HoloLens, 주방, 사례 연구
ms.openlocfilehash: 24759f90b8b84ec19e644fb8dff44f64c3ab81d2
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599845"
---
# <a name="case-study---lessons-from-the-lowes-kitchen"></a><span data-ttu-id="3e29c-104">사례 연구-Lowe의 주방 교훈</span><span class="sxs-lookup"><span data-stu-id="3e29c-104">Case study - Lessons from the Lowe's kitchen</span></span>

<span data-ttu-id="3e29c-105">HoloLens 팀 Lowe의 HoloLens 프로젝트에서 파생 된 모범 사례 중 일부를 공유 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e29c-105">The HoloLens team wants to share some of the best practices that were derived from the Lowe's HoloLens project.</span></span> <span data-ttu-id="3e29c-106">프로젝션 Lowe의 HoloLens의 비디오 Satya의 2016 Ignite 키 노트에서 아래 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e29c-106">Below is a video of the Lowe's HoloLens projected demonstrated at Satya's 2016 Ignite keynote.</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/gC_4JxF0e_k]

## <a name="lowes-hololens-best-practices"></a><span data-ttu-id="3e29c-107">Lowe의 HoloLens 모범 사례</span><span class="sxs-lookup"><span data-stu-id="3e29c-107">Lowe's HoloLens Best Practices</span></span>

<span data-ttu-id="3e29c-108">두 개의 비디오는 2016 년 4 월 이후 두 Lowe 저장소에 있었던 Lowe의 HoloLens 파일럿에서 파생 된 모범 사례를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e29c-108">The two videos cover best practices that were derived from the Lowe's HoloLens Pilot that has been in two Lowe's stores since April 2016.</span></span> <span data-ttu-id="3e29c-109">주요 항목은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3e29c-109">The key topics are:</span></span>
* <span data-ttu-id="3e29c-110">모바일 장치에 대 한 성능 최대화</span><span class="sxs-lookup"><span data-stu-id="3e29c-110">Maximize performance for a mobile device</span></span>
* <span data-ttu-id="3e29c-111">모든 holographic 프레임을 사용 하 여 UX 메서드 만들기 (두 번째 talk)</span><span class="sxs-lookup"><span data-stu-id="3e29c-111">Create UX methods with a full holographic frame (2nd talk)</span></span>
* <span data-ttu-id="3e29c-112">전체 자릿수 맞춤 (두 번째 talk)</span><span class="sxs-lookup"><span data-stu-id="3e29c-112">Precision alignment (2nd talk)</span></span>
* <span data-ttu-id="3e29c-113">Holographic 경험을 공유 (두 번째 talk)</span><span class="sxs-lookup"><span data-stu-id="3e29c-113">Shared holographic experiences (2nd talk)</span></span>
* <span data-ttu-id="3e29c-114">고객 상호 작용 (두 번째 talk)</span><span class="sxs-lookup"><span data-stu-id="3e29c-114">Interacting with customers (2nd talk)</span></span>

## <a name="video-1"></a><span data-ttu-id="3e29c-115">비디오 1</span><span class="sxs-lookup"><span data-stu-id="3e29c-115">Video 1</span></span>

<span data-ttu-id="3e29c-116">**모바일 장치에 대 한 성능을 최대화** HoloLens는 장치에서 수행 하는 모든 처리를 사용 하 여 제한 되지 않는 장치입니다.</span><span class="sxs-lookup"><span data-stu-id="3e29c-116">**Maximize performance for a mobile device** HoloLens is an untethered device with all the processing taking place in the device.</span></span> <span data-ttu-id="3e29c-117">이 모바일 플랫폼 필요 하며 하나의 사고방식을 모바일 응용 프로그램을 만드는 것과 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e29c-117">This requires a mobile platform and requires a mindset similar to creating mobile applications.</span></span> <span data-ttu-id="3e29c-118">HoloLens 응용 프로그램 환경을 제공 하기 위해 맛 있는 사용자를 위해 60 FPS 유지 관리 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3e29c-118">Microsoft recommends that your HoloLens application maintain 60FPS to provide a delicious experience for your users.</span></span> <span data-ttu-id="3e29c-119">낮은 FPS 있는 불안정 한 상태가 제공 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e29c-119">Having low FPS can result in unstable holograms.</span></span>

<span data-ttu-id="3e29c-120">HoloLens에서 개발 하는 것은 자산 최적화/부분 제거, 사용자 지정 셰이더를 사용 하 여 때 살펴봐야 할 가장 중요 한 사항 중 일부 (에 무료로 제공 합니다 [HoloLens 도구 키트](https://github.com/Microsoft/HoloToolkit-Unity)).</span><span class="sxs-lookup"><span data-stu-id="3e29c-120">Some of the most important things to look at when developing on HoloLens is asset optimization/decimation, using custom shaders (available for free in the [HoloLens Toolkit](https://github.com/Microsoft/HoloToolkit-Unity)).</span></span> <span data-ttu-id="3e29c-121">또 다른 중요 한 고려 사항은 프로젝트의 처음부터 프레임 속도 측정 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3e29c-121">Another important consideration is to measure the frame rate from the very beginning of your project.</span></span> <span data-ttu-id="3e29c-122">프로젝트에 따라 자산을 표시 하는 순서는 큰 참가자 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e29c-122">Depending on the project, the order of displaying your assets can also be a big contributor</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/o0QIPwgiP9A]

## <a name="video-2"></a><span data-ttu-id="3e29c-123">비디오 2</span><span class="sxs-lookup"><span data-stu-id="3e29c-123">Video 2</span></span>

<span data-ttu-id="3e29c-124">**모든 holographic 프레임을 사용 하 여 UX 메서드 만들기** 홀로그램 실제 환경에서의 위치를 이해 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e29c-124">**Create UX methods with a full holographic frame** It's important to understand the placement of holograms in a physical world.</span></span> <span data-ttu-id="3e29c-125">Lowe의를 사용 하 여 홀로그램의 더 큰 환경을 표시 하는 동안 닫습니다 등록 환경을 제공 하는 데 도움이 되는 다른 UX 방법을 알아보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="3e29c-125">With Lowe's we talk about different UX methods that help users experience holograms up close while still seeing the larger environment of holograms.</span></span>

<span data-ttu-id="3e29c-126">**전체 자릿수 맞춤** 된 실제 주방 정밀도 맞춤을 제공 해야 할 환경에 가장 중요 한 the Lowe의 경우.</span><span class="sxs-lookup"><span data-stu-id="3e29c-126">**Precision alignment** For the Lowe's scenario, it was paramount to the experience to have precision alignment of the holograms to the physical kitchen.</span></span> <span data-ttu-id="3e29c-127">실제 환경에서 변경 된 사용자를 유도 하는 환경을 보장 하는 기술을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e29c-127">We discuss techniques helps ensure an experience that convinces users that their physical environment has changed.</span></span>

<span data-ttu-id="3e29c-128">**Holographic 환경 공유할** 은 연결 된 Lowe의 환경을 사용 되는 기본 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="3e29c-128">**Shared holographic experiences** Couples are the primary way that the Lowe's experience is consumed.</span></span> <span data-ttu-id="3e29c-129">명 탁상을 변경 하 고 다른 사람이 변경 내용을 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e29c-129">One person can change the countertop and the other person will see the changes.</span></span> <span data-ttu-id="3e29c-130">이 공유"환경"을 호출 했습니다.</span><span class="sxs-lookup"><span data-stu-id="3e29c-130">We called this "shared experiences".</span></span>

<span data-ttu-id="3e29c-131">**고객 상호 작용** Lowe의 디자이너는 HoloLens, 사용 하지 않지만 고객이 표시 되는 항목을 참조 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e29c-131">**Interacting with customers** Lowe's designers are not using a HoloLens, but they need to see what the customers are seeing.</span></span> <span data-ttu-id="3e29c-132">UWP 응용 프로그램에서 표시 하는 고객은 캡처하는 방법을 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="3e29c-132">We show how to capture what the customer is seeing on a UWP application.</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/LceMdyKZ4PI]
