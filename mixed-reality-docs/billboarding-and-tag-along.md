---
title: 빌보드 및 tag-along
description: 빌보드 사용 하 여 개체를 항상 사용자에 직면 하 게 방향을 지정 합니다.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality를 빌보드를 tag-along
ms.openlocfilehash: e33ab0121398742b2e48553c9cbf2c1debdc6abf
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974783"
---
# <a name="billboarding-and-tag-along"></a>빌보드 및 tag-along

빌보드는 혼합된 현실에서 개체에 적용할 수 있는 동작 개념입니다. 빌보드 사용 하 여 개체를 항상 사용자에 직면 하 게 방향을 지정 합니다. 텍스트를 사용 하 여 특히 유용 있으며 메뉴 시스템 (전 세계 잠김) 사용자의 환경에서 정적 개체의 위치이 고, 그렇지 지거나 이동할 사용자가 읽을 수 없습니다.

![HoloLens 측면 항상 사용자에 직면 하는 메뉴 시스템](images/billboarding-fragments.gif)<br>
*HoloLens 측면 항상 사용자에 직면 하는 메뉴 시스템*

빌보드 사용할 수 있는 개체는 사용자의 환경에서 자유롭게 회전할 수 있습니다. 디자인 고려 사항에 따라 단일 축으로 제약할 수도 있습니다. 유의 하십시오 billboarded 개체 클립 하거나 너무 배치 될 경우 자체 채워집니다 수 다른 개체에 가까운 또는 HoloLens에 너무 가까이 화면 검색 합니다. 이 방지 하려면 생각해 총 공간 개체 빌보드 사용 하도록 설정 하는 축에서 회전할 때 발생할 수 있습니다.

## <a name="what-is-a-tag-along"></a>tag-along 란?

Tag-along는 동작 개념 billboarded 개체를 포함 하 여 홀로그램을 추가할 수 있습니다. 이 상호 작용을 더 자연스럽 고 친숙 한 방식으로 콘텐츠 헤드 잠긴의 효과 달성 하는 경우 Tag-along 개체를 사용자의 보기에 유지 하려고 합니다. 이렇게 하면 자유롭게 것도 여전히 직접 해당 보기의 외부 홀로그램을 표시 하는 동안 이러한 맨 앞으로 상호 작용할 수 있습니다.

![HoloLens pin 패널 tag-along 동작 하는 방법의 좋은 예입니다.](images/tagalong-1000px.jpg)<br>
*HoloLens 시작 메뉴는 tag-along 동작의 좋은 예*

Tag-along 개체 처럼 동작 하는 방법을 미세 조정할 수 있는 매개 변수를 가집니다. 사용자가 자신의 환경에 이동 하는 동안 콘텐츠 또는 사용자의 시야가 필요에 따라 해제 수 있습니다. 사용자가 콘텐츠 뷰의 모서리 쪽으로 이동 하 여 사용자의 주변 내로 유지 하려고 합니다.에 따라 사용자가 이동 하는 방법을 신속 하 게 유지 될 수 있습니다 보기에서 일시적으로 콘텐츠입니다. 사용자 gazes 향해 tag-along 개체, 경우 있어 자세히 보기로 합니다. 콘텐츠 항상 사용자가 해당 콘텐츠는 방향을 잊어버릴 하므로 "한눈 떨어진" 되 고 생각할 수 있습니다.

추가 매개 변수는 고무 밴드에서 사용자의 머리글에 연결 된 것으로 생각 될 tag-along 개체를 만들 수 있습니다. 가속 또는 감속 빨라져 더 주변에 없는 것으로 생각 될 수 있도록 개체에 대 한 가중치를 제공 합니다. 이 spring 동작은 유도성 tag-along의 작동 방식을 정확 하 게 멘 탈 모델을 빌드할 수 있도록 합니다. 오디오는 없는 경우 사용자 개체 tag-along 모드로 대 한 추가 affordances를 제공 합니다. 오디오 효과 이동;의 속도 더욱 높일 빠른 헤드 순서 대로 자연 스러운 속도로 walking 최소 있는 경우 오디오 효과 전혀 가질 해야 하는 동안 더 눈에 띄는 음향 효과 제공 해야 합니다.

콘텐츠 헤드 잠금이 설정 처럼 tag-along 개체 엄청난 또는 크게 이동 하거나 사용자의 보기에 너무 많은 스프링 nauseating 입증할 수 있습니다. 사용자 찾습니다 하 고 다음 신속 하 게 중지 빠른으로 중지 했습니다. 해당 head이 중지 되었음을 설정 뿐만 아니라 해당 비전 표시 하면 세계 중지 해당 분산이 알립니다. 그러나 tag-along 사용자 중지 되 면 이동에 유지 하는 경우이 빠른을 혼동 될 수 있습니다.

## <a name="see-also"></a>참조
* [커서](cursors.md)
* [Instinctual 상호 작용](interaction-fundamentals.md)
* [편안함](comfort.md)
