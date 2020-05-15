---
title: Unreal을 사용하기 위한 권장 성능
description: Unreal의 혼합 현실 앱에 대한 최적의 성능을 위한 권장 사항
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 혼합 현실, 성능, 최적화, 설정, 설명서
ms.openlocfilehash: 1fab2f714628f61a518d89795cf644e90130200a
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840202"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="17218-104">Unreal을 사용하기 위한 권장 성능</span><span class="sxs-lookup"><span data-stu-id="17218-104">Performance recommendations for Unreal</span></span>

<span data-ttu-id="17218-105">이 문서에서는 [혼합 현실에 대한 성능 추천 사항](understanding-performance-for-mixed-reality.md)에 요약된 설명을 기반으로 하지만, Unreal 엔진 환경과 관련된 학습에 집중하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17218-105">This article builds on the discussion outlined in [performance recommendations for mixed reality](understanding-performance-for-mixed-reality.md) but focuses on learnings specific to the Unreal Engine environment.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="17218-106">권장 Unreal 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="17218-106">Recommended Unreal project settings</span></span>

- <span data-ttu-id="17218-107">모바일 VR 렌더러 사용 - 프로젝트 설정에서 대상 플랫폼이 "프로젝트 – 대상 하드웨어"에서 "모바일/태블릿"으로 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="17218-107">Use the mobile VR renderer- in your project settings, ensure your target platform is set to "Mobile/Tablet" under "Project – Target Hardware"</span></span>
- <span data-ttu-id="17218-108">폐색 선별 사용 안 함 - "선별" 섹션의 "엔진 – 렌더링"에서 "폐색 선별" 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="17218-108">Disable occlusion culling- under "Engine – Rendering" in the "Culling" section, uncheck "Occlusion Culling"</span></span>
    + <span data-ttu-id="17218-109">매우 자세한 장면을 렌더링해야 하기 때문에 폐색 선별이 필요한 경우 "엔진 – 렌더링"에서 "지원 소프트웨어 폐색 선별"를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="17218-109">If occlusion culling is required because a very detailed scene needs to be rendered, it is recommended that "Support Software Occlusion Culling" is enabled Under "Engine – Rendering".</span></span> <span data-ttu-id="17218-110">이렇게 하면 Unreal이 CPU에서 폐색 선별을 수행하고 HoloLens 2에서 성능이 좋지 않은 GPU 폐색 쿼리를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17218-110">This allows Unreal to do occlusion culling on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>
- <span data-ttu-id="17218-111">"VR" 범주의 "엔진 – 렌더링"에서 "인스턴스 스테레오"와 "모바일 다중 뷰"를 모두 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="17218-111">Enable both "Instanced Stereo" and "Mobile Multi-View" under "Engine – Rendering" in the "VR" category.</span></span> <span data-ttu-id="17218-112">"모바일 다중 뷰"를 확인할 수 있도록 "모바일 후처리"를 선택 취소해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17218-112">You may need to uncheck "Mobile Post-Processing" in order to be able to check "Mobile Multi-View"</span></span>
