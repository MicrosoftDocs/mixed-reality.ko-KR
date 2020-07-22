---
title: Unreal을 사용하기 위한 권장 성능
description: Unreal의 혼합 현실 앱에 대한 최적의 성능을 위한 권장 사항
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 혼합 현실, 성능, 최적화, 설정, 설명서
ms.openlocfilehash: a7972962eeb2b1480a7da38210b5ee77104f508b
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303641"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="a9458-104">Unreal을 사용하기 위한 권장 성능</span><span class="sxs-lookup"><span data-stu-id="a9458-104">Performance recommendations for Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="a9458-105">개요</span><span class="sxs-lookup"><span data-stu-id="a9458-105">Overview</span></span>

<span data-ttu-id="a9458-106">이 문서에서는 [혼합 현실에 대한 성능 추천 사항](understanding-performance-for-mixed-reality.md)에 요약된 설명을 기반으로 하지만, Unreal Engine 특정 기능에 초점을 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="a9458-106">This article builds on the discussion outlined in [performance recommendations for mixed reality](understanding-performance-for-mixed-reality.md), but focuses on features specific to Unreal Engine.</span></span> <span data-ttu-id="a9458-107">계속하기 전에 애플리케이션 병목, 혼합 현실 앱 분석 및 프로파일링, 일반 성능 수정 사항을 확인해 보는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a9458-107">You're encouraged to read up on application bottlenecks, analyzing and profiling mixed reality apps, and general performance fixes before continuing.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="a9458-108">권장 Unreal 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="a9458-108">Recommended Unreal project settings</span></span>
<span data-ttu-id="a9458-109">**편집 > 프로젝트 설정**에서 다음의 각 설정을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9458-109">You can find each of the following settings in **Edit > Project Settings**.</span></span>

1. <span data-ttu-id="a9458-110">모바일 VR 렌더러 사용:</span><span class="sxs-lookup"><span data-stu-id="a9458-110">Using the mobile VR renderer:</span></span>
    * <span data-ttu-id="a9458-111">**프로젝트** 섹션으로 스크롤하고 **대상 하드웨어**를 선택한 다음, 대상 플랫폼을 **모바일/태블릿**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a9458-111">Scroll to the **Project** section, select **Target Hardware**, and set the target platform to **Mobile/Tablet**</span></span>

![모바일 대상 설정](images/unreal/performance-recommendations-img-01.png)

2. <span data-ttu-id="a9458-113">폐색 고르기 사용 안 함:</span><span class="sxs-lookup"><span data-stu-id="a9458-113">Disabling occlusion culling:</span></span>
    * <span data-ttu-id="a9458-114">**엔진** 섹션으로 스크롤하고 **렌더링**을 선택한 다음, **고르기** 섹션을 확장하고 **폐색 고르기**를 선택 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="a9458-114">Scroll to the **Engine** section, select **Rendering**, expand the **Culling** section, and uncheck **Occlusion Culling**.</span></span>
        + <span data-ttu-id="a9458-115">렌더링되는 자세한 장면에 폐색 고르기가 필요한 경우 **엔진 > 렌더링**에서 **소프트웨어 폐색 고르기 지원**을 사용하도록 설정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a9458-115">If you need occlusion culling for a detailed scene being rendered, it's recommended that you enable **Support Software Occlusion Culling** in **Engine > Rendering**.</span></span> <span data-ttu-id="a9458-116">이렇게 하면 Unreal이 CPU에서 작동하며, HoloLens 2에서 성능이 좋지 않은 GPU 폐색 쿼리를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9458-116">This lets Unreal to do the work on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>

![폐색 고르기 사용 안 함](images/unreal/performance-recommendations-img-02.png)

3. <span data-ttu-id="a9458-118">모바일 다중 보기 사용:</span><span class="sxs-lookup"><span data-stu-id="a9458-118">Using mobile multi-view:</span></span>
    * <span data-ttu-id="a9458-119">**엔진** 섹션으로 스크롤하고 **렌더링**을 선택한 다음, **VR** 섹션을 확장하고 **인스턴스 스테레오**와 **모바일 다중 뷰**를 모두 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a9458-119">Scroll to the **Engine** section, select **Rendering**, expand the **VR** section, and enable both **Instanced Stereo** and **Mobile Multi-View**.</span></span> <span data-ttu-id="a9458-120">모바일 HDR를 선택 취소해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9458-120">Mobile HDR should be unchecked.</span></span>

![VR 렌더링 설정](images/unreal/performance-recommendations-img-03.png)

4. <span data-ttu-id="a9458-122">**렌더링할 CSM 계단식 최대 수**를 **1**로 설정하고 **최대 이동 가능한 스포트라이트/점 광원**을 **0**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a9458-122">Setting the **Maximum number of CSM cascades to render** to **1** and **Max Movable Spotlights / Point Lights** to **0**.</span></span> 
