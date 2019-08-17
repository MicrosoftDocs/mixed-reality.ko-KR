---
title: 새 공간에서 HoloLens 사용
description: HoloLens는 시간이 지남에 따라 공백이 표시 되는 모양을 학습 합니다. 사용자는 공간을 통해 특정 방법으로 HoloLens를 이동 하 여이 프로세스를 쉽게 수행할 수 있습니다.
author: dorreneb
ms.author: dobrown
ms.date: 08/16/2019
ms.topic: article
keywords: Windows Mixed Reality, 디자인, 공간 매핑, HoloLens, 표면 재구성, 메시, 헤드 추적, 매핑
ms.openlocfilehash: a6a83dfc2c883723e4cd79c0dc46a9cd78f1f604
ms.sourcegitcommit: 60f73ca23023c17c1da833c83d2a02f4dcc4d17b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566022"
---
# <a name="use-hololens-in-new-spaces"></a>새 공간에서 HoloLens 사용

사용자가 공간을 이동할 때 HoloLens *맵*또는 해당 환경에 대 한 정보를 학습 합니다. 시간이 지남에 따라 HoloLens는 관찰 된 환경의 모든 부분에 대 한 *공간 맵을* 작성 합니다. HoloLens는 환경의 변경 내용이 관찰 될 때 지도를 업데이트 합니다. 이 검색은 앱 시작 사이에 자동으로 유지 됩니다.

장치를 켜 있고 사용자가 로그인 한 경우 HoloLens가 맵을 만들고 업데이트 합니다. 장치를 보유 하거나 장치를 사용 하는 경우 장치는 해당 영역을 매핑하려고 시도 합니다. HoloLens는 시간 경과에 따라 공간을 자연스럽 게 알 수 있지만 공간을 더 빠르고 효율적으로 매핑하는 데 사용할 수 있는 팁과 트릭을 제공 합니다. 

HoloLens가 공간을 매핑할 수 없거나 보정을 벗어난 경우 제한 된 모드로 전환 될 수 있습니다. 제한 된 모드에서는 holograms를 주변에 놓을 수 없습니다.

## <a name="tips-and-tricks-for-mapping-spaces"></a>공간 매핑을 위한 팁과 요령

### <a name="make-sure-the-space-is-set-up-for-mixed-reality"></a>혼합 현실에 대해 공간이 설정 되었는지 확인 합니다.

환경의 기능을 사용 하면 HoloLens가 공간을 해석 하기 어려울 수 있습니다. 조명 수준, 공간의 재질, 개체 레이아웃 등은 모두 HoloLens에서 영역을 매핑하는 방법에 영향을 줍니다.

Hololens의 공간을 설정 하기 위한 팁과 기타 혼합 현실 장치는 [hololens의 환경 고려 사항](environment-considerations-for-hololens.md)에서 찾을 수 있습니다.

### <a name="understand-the-scenarios-for-the-area"></a>영역에 대 한 시나리오 이해

가장 많은 시간을 할애 하 여 가장 많은 시간을 할애 하 여 지도가 적절 하 고 완전 하 게 사용할 수 있도록 하는 것이 중요 합니다. 

예를 들어, HoloLens의 사용자 시나리오에서 점 A에서 Point B로 이동 하는 경우, 이동 하는 동안 모든 방향에서 두 번까지 경로를 2-3 번 살펴봅니다. 

### <a name="walk-slowly-around-the-space"></a>공간을 느리게 탐색

영역 주위를 너무 빨리 탐색 하는 경우 HoloLens가 영역 매핑을 누락 하 게 될 가능성이 높습니다. 공간을 천천히 탐색 하 고, 5-8 피트 마다 중지 하 여 주변에서 살펴볼 수 있습니다.

부드러운 이동은 HoloLens가 더 effeciently를 지도 하는 데도 도움이 됩니다.

### <a name="look-in-all-directions"></a>모든 방향 살펴보기

공간을 매핑하는 경우에는 데이터가 서로 상대적으로 이동 하는 지점에 대 한 데이터를 더 많이 볼 수 있습니다. 

예를 들어, 검색 하지 않는 경우 HoloLens에서 실내의 상한 위치를 모를 수 있습니다. 

공간을 매핑하면 바닥에서 살펴보세요.

### <a name="cover-key-areas-multiple-times"></a>주요 영역을 여러 번 커버

영역을 여러 번 이동 하면 첫 번째 연습에서 누락 했을 수 있는 기능을 선택 하는 데 도움이 됩니다. 2 ~ 3 배의 영역을 탐색 하 여 이상적인 맵을 작성 해 보세요.

가능 하면 이러한 이동을 반복 하는 동안 한 방향으로 영역을 이동 하는 데 소요 되는 시간을 이동한 다음, 원래 상태로 전환 하 고 다시 연습 합니다.

### <a name="take-your-time-mapping-the-area"></a>영역 매핑

HoloLens가 전체 지도 하 고 해당 환경에 맞게 조정 되는 데 15 ~ 20 분 정도 걸릴 수 있습니다. HoloLens를 자주 사용 하려는 공간이 있는 경우 해당 시간을 앞으로 이동 하 여 공간을 매핑하면 나중에 문제를 방지할 수 있습니다. 

## <a name="possible-errors-in-the-spatial-map"></a>공간 맵에서 발생할 수 있는 오류

공간 매핑 데이터의 오류는 다음 세 가지 범주 중 하나에 속합니다.

* *구멍*: 실제 서피스가 공간 매핑 데이터에 없습니다.
* *Hallucinations*: 실제 세계에 존재 하지 않는 공간 매핑 데이터에 서피스가 있습니다.
* *Wormholes*: 이는 실제로는 맵의 다른 부분에 있는 것으로 간주 하 여 공간 맵의 일부를 ' 손실 ' 합니다.
* *편차*: 공간 매핑 데이터의 표면은 실제 화면에 완전히 맞추고, 푸시 또는 끌어올 수 있습니다.

[Holograms를 삭제](environment-considerations-for-hololens.md) 하 고 공간을 다시 매핑하여 이러한 오류 중 상당수를 완화할 수 있습니다.