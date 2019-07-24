---
title: 사례 연구-혼합 현실에서 사람 표시
description: 환상적인 요소만 만들 수는 없지만 혼합 현실 환경, 개체 및 사람들의 가장 현실적인 캡처를 활용 하는 경우에는 어떤 종류의 기회가 있나요?
author: mavitazk
ms.author: mavitazk
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 사람, 아바타, 혼합 현실 캡처, 대규모 비디오
ms.openlocfilehash: 35dced220d4e76cfc92ec17c0b88c1576eced403
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63527151"
---
# <a name="case-study---representing-humans-in-mixed-reality"></a>사례 연구-혼합 현실에서 사람 표시

빛이 있는 James Turrell 디자인. 작업을 한 단계씩 코드 실행 하는 것은 깊이와 포커스의 의미를 흐리게 하는 것입니다. 벽은 가까이와 무한 한 것 처럼 보이지만 밝기는 그림자에 대 한 방법을 제공 합니다. 밝은 색 및 확산을 신중 하 게 분산 하 여 설계 된 익숙하지 않은 인식 Turrell는 현실에 대 한 이해를 확장 하는 방법인 [이러한 sensations](http://www.sculpture.org/documents/scmag02/nov02/turrell/turrell.shtml) 를 *' 눈*에 '로 설명 합니다. Turrell imagines와 같은 뛰어난 기능을 활용 하는 것은 오늘날 혼합 현실의 몰입 형 환경과는 달리, microsoft의 감지를 활용 하는 강력한 도구입니다.

![Wide Turrell (1998)](images/wide-out-james-turrell.jpg)

## <a name="how-do-you-represent-complex-real-world-environments-in-mixed-reality"></a>혼합 현실에서 복잡 한 실제 환경을 어떻게 표시 하나요?

몰입 형 환경에서 Turrell의 작업을 나타내는 것은 훌륭한 과제를 위해 수행 됩니다. 조명, 크기 조정 및 공간 오디오는 자신의 작업을 나타낼 수 있는 기회를 제공 합니다. 우리에 게는 상대적으로 간단한 3D 모델링이 필요 하지만,이는 삽화에 대 한 빛의 영향을 받습니다.

Turrell의 stark, surreal minimalism는 작업의 경험 이지만 혼합 현실에서 더 복잡 한 자료를 포함 하는 우리를 표시 하려는 경우 어떻게 되나요?

![느낌표-Ai Weiwei (2013)](images/bang-ai-weiwie.jpg)

2013에서 음악가 Ai Weiwei 발표 a tangling는 Stools Venice에서 886 살구색 Biennale [을 사용](http://www.designboom.com/art/ai-weiwei-bang-installation-at-venice-art-biennale-2013/) 하 고 있습니다. 각 나무 stool는 craftsmanship이 매우 중요 한 연대에서 제공 되며 이러한 stools는 세대 간에 전달 됩니다. Stools 자체 (목재는 복잡 하지 않음, 조각의 전체 자릿수, 신중한 배치)는 최신 문화권에 대 한 Ai의 해설에 매우 중요 합니다.

살구색 stools는 자신의 신뢰성을 통해 음악가의 메시지를 배달 합니다. 실제 표현은 환경에 중요 하며 기술적인 문제를 생성 하는 것이 중요 합니다. Sculpting stools 각각 886의 있으므로 매우은 포괄적이 고 비용이 많이 듭니다. 모델 및 배치에 소요 되는 시간 자료의 신뢰성을 어떻게 유지 하나요? 이러한 개체를 처음부터 다시 만드는 것은 아트 워크 자체의 해석을 하는 경우가 많습니다. 음악가의 의도를 유지 하려면 어떻게 해야 하나요?

## <a name="methods-of-capturing-mixed-reality-assets"></a>혼합 현실 자산을 캡처하는 방법

처음부터 새로 만드는 대신 실제 내용을 캡처하는 것이 좋습니다. 진행 중인 캡처 방법 집합을 통해 혼합 현실 (환경, 개체 및 사람)에서 발견 되는 각 핵심 자산 유형의 인증 된 표현을 개발할 수 있습니다.

광범위 한 범주는 잘 구성 된 2D 비디오부터 최신 형태의 대규모 비디오까지 다양 합니다. Ai Weiwei의 경우 우리를 만드는 동안 검색 (종종 기본 기술 photogrammetry)을 사용 하 여 각 stools 자체를 검색할 수 있습니다. 360 ° photo 및 비디오 캡처는 우리 전체에 배치 된 고품질의 첨단 카메라를 활용 하 여 환경을 가상화 하는 또 다른 방법입니다. 이러한 기술을 사용 하는 경우 각 부분의 craftsmanship을 볼 수 있는 충분 한 세부 정보와 함께 규모의 의미를 이해 하기 시작 합니다. 이러한 모든 것은 현실에서 가능 하지 않은 새로운 vistas 및 큐브 뷰를 허용 하는 디지털 형식으로 되어 있습니다.

![2D에서 대규모 비디오](images/2d-to-volumetric-video.png)

환상적인 요소만 만들 수는 없지만 혼합 현실 환경, 개체 및 사람들의 가장 현실적인 캡처를 활용 하는 경우에는 어떤 종류의 기회가 있나요? 이러한 메서드 간에 겹치는 부분을 살펴보면 미디어의 위치를 쉽게 파악할 수 있습니다.

환경 및 개체의 경우 photogrammetry의 요소를 포함 하기 위해 360 ° 이미징 소프트웨어가 진화 하 고 있습니다. 깊이 정보를 장면에서 격리 하면 고급 360 ° 비디오를 통해 가상 장면을 살펴볼 때 헤드를 fishbowl 수 있는 느낌을 줄일 수 있습니다.

사용자를 위해 동작 캡처 및 검색을 결합 하 고 확장 하는 새로운 방법이 새로 등장 합니다. 동작 캡처는 시각적 효과 및 시네마 문자에 대 한 자세한 인간 움직임을 위한 것 이며, 스캔은 얼굴, 얼굴 등의 자세한 인간 시각적 개체를 캡처하기 위해 고급입니다. 향상 된 렌더링 기술을 통해 대규모 video 라는 새로운 메서드는 시각적 개체와 깊이 정보를 결합 하 여 이러한 기술을 활용 하 여 차세대 3D 인간 캡처를 만듭니다.

## <a name="volumetric-video-and-the-pursuit-of-authentic-human-capture"></a>대규모 비디오와 인증 된 인간 캡처의 담당

사람들은 스토리텔링의 핵심이 됩니다. 대부분의 리터럴 의미는 사람이 말하는 것, 수행 하는 또는 스토리의 주제입니다. 오늘날의 빠른 몰입 형 환경에서 가장 몰입이 고 눈에 잘 잘 되는 몇 가지 순간은 소셜입니다. 거실에서 혼합 현실 경험을 공유 하 여 unbelievable 새 환경에서 친구 들이 볼 수 있습니다. 인간 요소는 가장 훌륭한 현실 현실를 만듭니다.

![VR의 Mindshow](images/mindshow-in-vr-640px.jpg)

몰입 형 환경의 아바타는 스토리텔링에서 새로운 종류의 전형을 사용 하도록 설정 합니다. 최신 앱은 가상 본문 소유권의 개념을 재고 하 고, 세대를 설정 하 여 사용자 간의 거리를 제거 합니다. [Mindshow](http://mindshow.com/) 같은 기업은 아바타를 활용 하 여 사용자가 완전히 새로운 가상 사용자와 문자를 사용할 수 있도록 지 원하는 독창적인 도구를 개발 하 고 있습니다. 다른 사람들은 [꾸밈 식의 메서드](https://en.wikipedia.org/wiki/Uncanny_valley)를 탐색 하는 것으로 서, 사용자와 유사한 특성의 특성을 탐색 하는 것이 잠재적으로 독창적인 기회입니다. 현재 현실감이 없으면 일상적인 개발자를 위한 기술 문제 호스트와 함께 [휴먼 likeness의 uncanny 계곡](https://en.wikipedia.org/wiki/Uncanny_valley) 을 방지 하는 데 도움이 됩니다. 이러한 이유로 (및 그 이상), 현실적인 아바타은 예측 가능한 미래에 대 한 기본값이 될 가능성이 높습니다. 그러나 현실감는 혼합 현실에 상당한 과제가 발생 하지만 *3d 공간에서 사람을 인증 해야 하는 주요 시나리오가 있습니다*.

Microsoft Research에서 Microsoft Research를 활용 하는 소규모 팀은 대규모 비디오의 형태를 통해 사람을 캡처하기 위한 방법을 개발 하는 몇 년간 지난 몇 년간 노력 했습니다. 현재 프로세스는 비디오 프로덕션과 비슷합니다. sculpted 자산에 움직임을 적용 하는 것이 아니라 전체 3D 기록입니다. 성능과 이미지는 실시간으로 캡처됩니다 .이는 음악가의 작업이 아니라 인증 된 표현입니다. 기술이 상용 응용 프로그램으로 확장 되기 시작 하는 동안에는 대규모 비디오의 의미는 [Microsoft의 더 많은 개인 컴퓨팅 비전](https://www.youtube.com/watch?v=tcyj-_IEWt8)에 매우 중요 합니다.

![대규모 video SIGGRAPH 2015](images/volumetric-video-siggraph-2015.gif)

인증 된 인간 캡처는 혼합 현실에서 새로운 고유한 경험 범주를 잠금 해제 합니다. 유명인, 동료 또는 좋아했던 인지 여부에 관계 없이 사용자가 인식할 수 있는 사용자를 확인 하는 것은 디지털 미디어에서 가능 하지 않은 분위기 깊이를 만듭니다. 그에 해당 하는 nuance의 얼굴입니다. 3D 공간에서 이러한 인간 품질을 캡처할 수 있는 경우의 기회는 어떻게 되나요?

현재 팀은 엔터테인먼트 및 교육 등의 섹터를 중심으로 대규모 비디오의 경계를 푸시합니다. [Actiongram](https://www.microsoft.com/p/actiongram/9nblggh5ftmt) 은 독창적인 문자 및 [유명인](https://www.youtube.com/watch?v=BwWueXlsOrA) 을 제공 하 여 혼합 현실 사례를 만듭니다. [대상: ](https://www.jpl.nasa.gov/news/news.php?feature=6220)현재 NASA의 Kennedy Space Center에 있는 Mars는 전설의 astronaut의 전설의 대규모 비디오를 제공 합니다. 경험을 통해 방문자는 Mars에서 인간 colonization의 작업을 소개 하는 것 처럼, Mars의 화면을 살펴볼 수 있습니다.

## <a name="humans-are-fundamental-to-mixed-reality"></a>일부는 혼합 현실의 기본입니다.

이러한 비디오를 자연스럽 게 만드는 방법을 디자인 하는 것은 어려운 일 이지만 팀에서 상당한 잠재력을 보이는 것입니다. 이러한 기회는 기술이 더 쉽게 액세스할 수 있게 되 면 확장 되 고 기록에서 실시간 캡처로 이동 합니다.

[Holoportation](https://www.microsoft.com/en-us/research/project/holoportation-3/) 는 동일한 기본 기술을 기반으로 하 고, 시각적 개체와 깊이 정보를 캡처하고, 결과를 실시간으로 렌더링 하는 연구 노력입니다. 팀은 실제 인간 표현의 강력한 기능을 활용 하 여 대화 및 공유 환경의 미래를 파악할 수 있습니다. 전 세계 어디에서 든 3 차원 캡처를 사용자 환경에 추가할 수 있는 경우 어떻게 되나요?

![대화의 미래](images/girl-with-dress.jpg)

새 수준의 집중 교육를 Skype와 같은 일상적인 앱으로 계층화 하 여 디지털 회의 및 비즈니스 여행 개념을 크게 변경 합니다. 대규모 video는 고유의 시나리오를 엽니다. 전문가에 게는 couches에 있는 멀리 떨어져 있는 대륙 또는 디지털 친구에 게 의사 하 고 있습니다. 혼합 현실 환경에 인증 된 인간 표현을 추가 하면 디지털 회의 및 비즈니스 여행 개념이 크게 변경 됩니다.

James Turrell의 추상적 아트와 Ai Weiwei의 중요 한 현실감는 고유한 기술적 문제를 제공 하는 것 처럼, 사용자를 creative 아바타 및 현실적인 캡처로 표현 하는 방법을 제공 합니다. 다른 항목은 무시 하 고 각각의 잠재력을 탐색 하면이 새로운 공간의 인간 상호 작용을 이해 하는 데 도움이 됩니다.

## <a name="about-the-author"></a>작성자 정보

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Mark Vitazko" width="60" height="60" src="images/mark-vitazko.jpg"></td>
<td style="border-style: none"><b>표시 Vitazko</b><br>UX 디자이너@Microsoft</td>
</tr>
</table>
