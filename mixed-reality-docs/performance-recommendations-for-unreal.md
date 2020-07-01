---
title: Unreal을 사용하기 위한 권장 성능
description: Unreal의 혼합 현실 앱에 대한 최적의 성능을 위한 권장 사항
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 혼합 현실, 성능, 최적화, 설정, 설명서
ms.openlocfilehash: 9f128a3ef09f29fc745c21b09b7ec97f5db33605
ms.sourcegitcommit: 7f50210b71a65631fd1bc3fdb215064e0db34333
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84533125"
---
# <a name="performance-recommendations-for-unreal"></a>Unreal을 사용하기 위한 권장 성능

## <a name="overview"></a>개요

이 문서에서는 [혼합 현실에 대한 성능 추천 사항](understanding-performance-for-mixed-reality.md)에 요약된 설명을 기반으로 하지만, Unreal Engine 특정 기능에 초점을 맞춥니다. 계속하기 전에 애플리케이션 병목, 혼합 현실 앱 분석 및 프로파일링, 일반 성능 수정 사항을 확인해 보는 것이 좋습니다.

## <a name="recommended-unreal-project-settings"></a>권장 Unreal 프로젝트 설정
**편집 > 프로젝트 설정**에서 다음의 각 설정을 찾을 수 있습니다.

1. 모바일 VR 렌더러 사용:
    * **프로젝트** 섹션으로 스크롤하고 **대상 하드웨어**를 선택한 다음, 대상 플랫폼을 **모바일/태블릿**으로 설정합니다.

![모바일 대상 설정](images/unreal/performance-recommendations-img-01.png)

2. 폐색 고르기 사용 안 함:
    * **엔진** 섹션으로 스크롤하고 **렌더링**을 선택한 다음, **고르기** 섹션을 확장하고 **폐색 고르기**를 선택 취소합니다.
        + 렌더링되는 자세한 장면에 폐색 고르기가 필요한 경우 **엔진 > 렌더링**에서 **소프트웨어 폐색 고르기 지원**을 사용하도록 설정하는 것이 좋습니다. 이렇게 하면 Unreal이 CPU에서 작동하며, HoloLens 2에서 성능이 좋지 않은 GPU 폐색 쿼리를 방지할 수 있습니다.

![모바일 대상 설정](images/unreal/performance-recommendations-img-02.png)

3. VR 렌더링 업데이트:
    * **엔진** 섹션으로 스크롤하고 **렌더링**을 선택한 다음, **VR** 섹션을 확장하고 **인스턴스 스테레오**와 **모바일 다중 뷰**를 모두 사용하도록 설정합니다.
        + **모바일 다중 뷰**를 선택하려면 **모바일 후처리**를 선택 취소해야 할 수도 있습니다.

![모바일 대상 설정](images/unreal/performance-recommendations-img-03.png)
