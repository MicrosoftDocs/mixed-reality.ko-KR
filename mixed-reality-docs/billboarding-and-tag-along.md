---
title: Billboarding 및 태그 동반
description: Billboarding를 사용 하는 개체는 항상 사용자를 대상으로 합니다.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, billboarding, 태그 동반
ms.openlocfilehash: 032e665d94a73b94b59f693e452874af0b45f021
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436992"
---
# <a name="billboarding-and-tag-along"></a>Billboarding 및 태그 동반

<br>

<img src="images/billboarding-fragments.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">

Billboarding는 혼합 현실에서 개체에 적용할 수 있는 동작 개념입니다. Billboarding를 사용 하는 개체는 항상 사용자를 대상으로 합니다. 이는 사용자의 환경에 배치 된 정적 개체 (세계에서 잠김)를 이동 해야 하는 경우에는 사용자의 환경에 배치 된 정적 개체를 숨기 거 나 읽을 수 없게 하는 텍스트 및 menuing 시스템에 특히 유용 합니다.

Billboarding를 사용 하는 개체는 사용자 환경에서 자유롭게 회전할 수 있습니다. 디자인 고려 사항에 따라 단일 축으로 제한 될 수도 있습니다. Billboarded 개체는 다른 개체에 너무 가까이 배치 되거나 HoloLens에 스캔 된 표면이 너무 가까이 배치 된 경우에는 클리핑 또는 려 수 있습니다. 이를 방지 하려면 billboarding에 대해 사용 하도록 설정 된 축에서 회전할 때 개체가 생성할 수 있는 총 공간을 고려해 야 합니다.

## <a name="what-is-a-tag-along"></a>태그의 정의

태그 동반은 billboarded 개체를 포함 하 여 holograms에 추가할 수 있는 동작 개념입니다. 이 상호 작용은 보다 자연스럽 고 친숙 한 방법으로, 헤드 잠긴 콘텐츠의 효과를 달성할 수 있습니다. 태그 동반 개체는 사용자의 뷰를 떠나지 않습니다. 이를 통해 사용자는 직접 보기 외부에서 holograms 표시 하는 동시에 해당 사용자의 앞에 있는 것과 자유롭게 상호 작용할 수 있습니다.

HoloLens 핀 패널 ![태그 동반 동작의 좋은 예](images/tagalong-1000px.jpg)<br>
*HoloLens 시작 메뉴는 태그 동반 동작의 좋은 예입니다.*

태그를 포함 하는 개체에는 동작 방식을 세밀 하 게 조정할 수 있는 매개 변수가 있습니다. 사용자가 환경 주위에서 이동할 때 원하는 대로 사용자의 시야에 콘텐츠를 배치 하거나 축소할 수 있습니다. 사용자가 이동 하면 콘텐츠는 사용자가 이동 하는 속도에 따라 사용자의 주변 내에 유지 됩니다. 사용자가 이동 하면 콘텐츠가 일시적으로 표시 되지 않을 수 있습니다. 사용자가 태그를 따라 개체를 gazes 하는 경우에는 더 자세히 볼 수 있습니다. 콘텐츠를 항상 "한 눈에 파악" 하는 것은 사용자에 게 콘텐츠가 있는 방향을 잊지 않도록 하는 것입니다.

추가 매개 변수를 사용 하면 사용자의 헤드에 대 한 태그 동반 개체 느낌을 고무 띠로 만들 수 있습니다. 완충 가속 또는 감속은 개체에 대 한 가중치를 제공 하 여 더 물리적으로 표시 되도록 합니다. 이 스프링 동작은 사용자가 태그를 사용 하는 방법에 대 한 정확한 멘 탈 모델을 빌드하는 데 도움이 되는 affordance입니다. 오디오는 사용자가 태그 동반 모드에서 개체를 사용할 때 추가 affordances을 제공 하는 데 도움이 됩니다. 오디오는 이동 속도를 보강 해야 합니다. 고속 헤드 턴은 모든 효과가 있는 경우 자연 속도로 이동 하는 것이 최소 오디오를 포함 하는 동안 보다 눈에 띄는 음향 효과를 제공 해야 합니다.

진정한 헤드 잠금 콘텐츠와 마찬가지로 태그를 사용 하는 개체는 사용자의 뷰에서 무분별 또는 스프링을 너무 많이 이동 하는 경우 과도 하 게 또는 nauseating을 입증할 수 있습니다. 사용자가이를 확인 하 고 신속 하 게 중지 하면 해당 사용자가 중지 된 것을 알 수 있습니다. 이러한 잔액은 세계를 중지 하는 것을 알 수 있는 것을 알 수 있습니다. 그러나 사용자가 중지 되었을 때 태그를 따라 이동 하는 경우에는 해당 사용자의 감지를 혼동할 수 있습니다.

## <a name="see-also"></a>참고 항목
* [커서](cursors.md)
* [Instinctual 상호 작용](interaction-fundamentals.md)
* [편안함](comfort.md)
