---
title: 홀로그램이란?
description: HoloLens를 사용 하면 전 세계에 표시 되는 조명 및 소리로 이루어진 3 차원 holograms을 보고 상호 작용할 수 있습니다.
author: beaufolsom
ms.author: befolsom
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, holograms, 디자인, 상호 작용
ms.openlocfilehash: 714b08db23aa641252291aebe89fa3059c209a6f
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829785"
---
# <a name="what-is-a-hologram"></a>홀로그램이란?

HoloLens를 사용 하면 실제 개체인 것 처럼 전 세계에 표시 되는 광원 및 소리로 구성 된 **holograms**개체를 만들 수 있습니다. Holograms는 [응시](gaze.md), [제스처](gestures.md) 및 [음성 명령](voice-input.md)에 응답 하 고 [실제 서피스와](spatial-mapping.md) 상호 작용할 수 있습니다. Holograms를 사용 하면 전 세계의 일부인 디지털 개체를 만들 수 있습니다.

<br>

>[!VIDEO https://www.youtube.com/embed/MVXH5V8MVQo]

## <a name="device-support"></a>장치 지원

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>기능</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens(1세대)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
    </tr>
     <tr>
        <td>Holograms</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="a-hologram-is-made-of-light-and-sound"></a>홀로그램은 가볍고 소리로 구성 됩니다.

HoloLens [렌더링](rendering.md) 되는 holograms는 사용자의 눈 앞에 있는 holographic 프레임에 직접 나타납니다. Holograms를 전 세계에 추가 합니다. 즉, 디스플레이의 빛과 주변 광원을 모두 볼 수 있습니다. HoloLens는 눈동자에서 조명을 제거 하지 않으므로 holograms 색으로 렌더링 될 수 없습니다. 대신 검정색 콘텐츠가 투명 하 게 표시 됩니다.

Holograms에는 다양 한 모양과 동작이 있을 수 있습니다. 일부는 현실적인 및 반도체 이며, 다른 일부는 cartoonish 및 ethereal입니다. Holograms는 사용자의 환경에서 기능을 강조 표시할 수 있으며 앱의 사용자 인터페이스에 요소가 있을 수 있습니다.

![바닥에서 Holographic 강아지](images/fang3-640px.jpg)

Holograms는 주변의 특정 장소에서 제공 되는 [소리](spatial-sound.md)를 만들 수도 있습니다. HoloLens에서 소리는 소리를 포함 하지 않고 귀 바로 위에 있는 두 개의 스피커에서 제공 됩니다. 화면에 표시 되는 것과 마찬가지로, 사용자 환경의 소리를 차단 하지 않고 새 소리를 도입 하 여 스피커가 추가 됩니다.

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a>홀로그램을 사용자와 함께 전 세계 또는 태그에 배치할 수 있습니다.

홀로그램을 원하는 특정 위치가 있으면 전 세계에 정확 하 게 [배치할](coordinate-systems.md) 수 있습니다. 이 홀로그램을 연습 하면서 전 세계에 비해 안정적으로 표시 됩니다. [공간 앵커](coordinate-systems.md#spatial-anchors) 를 사용 하 여 해당 개체를 전 세계에 고정 하는 경우 시스템은 나중에 다시 돌아올 때 위치를 기억할 수도 있습니다.

![Holographic 빌딩 maquette on a table](images/image5-640px.png)

대신 일부 holograms 사용자를 따릅니다. 이러한 태그를 함께 사용 하면 사용자가 진행 하는 위치에 관계 없이 사용자를 기준으로 holograms을 배치 합니다. 한 번의 사용자와 함께 홀로그램을 가져와서 다른 방에 들어온 후 벽에 놓을 수도 있습니다.

**모범 사례**
* 일부 시나리오에서는 holograms가 쉽게 검색 가능 하거나 환경 전체에서 볼 수 있도록 요구할 수 있습니다. 이러한 종류의 위치에는 두 가지 상위 수준 방법이 있습니다. **"표시-잠김"** 및 **"본문 잠금"** 이라고 하겠습니다.
   * 디스플레이 잠김 콘텐츠는 장치 디스플레이에 "메서드에 액세스할" 됩니다. 이는 많은 사용자 들이 "사용 하지 않도록 설정" 하려는 경우를 비롯 하 여 다양 한 이유 때문에 복잡 합니다. 일반적으로 대부분의 디자이너는 표시 잠금 콘텐츠를 방지 하는 것이 더 좋습니다.
   * 본문에서 잠긴 접근 방식은 훨씬 더 forgivable. 본문 잠금은 홀로그램이 사용자의 body 또는 응시 vector로 테더 링 된 사용자를 중심으로 3d 공간에 배치 되는 경우입니다. 대부분의 환경에서는 사용자가 응시를 "팔 로우" 하 여 사용자가 자신의 본문을 회전 하 고 홀로그램을 잃지 않고 공간 간을 이동할 수 있는 본문 잠금 동작을 채택 했습니다. 지연 시간을 통합 하면 홀로그램 이동이 보다 자연스럽 게 느껴질 수 있습니다. 예를 들어, Windows Holographic OS의 일부 핵심 UI는 사용자가 헤드를 끄는 동안 gentle, 탄력적 같은 지연 시간을 사용 하 여 사용자의 응시를 따르는 본문 잠금 변형을 사용 합니다.
* 일반적으로 헤드에서 약 1-2 미터 떨어진 편안 하 게 볼 때 홀로그램을 준비 합니다.
* Holographic 프레임에서 지속적으로 사용 해야 하는 요소에 대 한 드리프트를 제공 하거나 사용자가 관점을 변경할 때 디스플레이의 한 면에 콘텐츠에 애니메이션 효과를 주는 것이 좋습니다.

**최적 영역에 holograms 두기-1.25 m과 5m 사이**

두 미터는 가장 최적 이며, 1 미터에서 더 가까운 수준으로 이동 하는 것이 저하 됩니다. 한 미터 보다 가까운 거리에서 holograms 정기적으로 이동 하는 것은 고정 holograms 보다 문제가 될 가능성이 높습니다. 사용자를 예기치 않은 환경으로 확장 하지 않도록 콘텐츠가 너무 가까이 있을 경우 적절 하 게 클리핑 하거나 페이드 아웃 하는 것이 좋습니다.

![사용자의 holograms를 배치 하는 데 가장 적합 한 거리입니다.](images/distanceguiderendering-640px.png)

## <a name="a-hologram-interacts-with-you-and-your-world"></a>홀로그램은 사용자 및 전 세계와 상호 작용 합니다.

Holograms는 빛과 소리를 위한 것이 아닙니다. 또한 전 세계의 활성 부분입니다. 홀로그램 및 제스처를 응시 하 고 홀로그램에서 팔 로우를 시작할 수 있습니다. 홀로그램에 음성 명령을 제공 하 고 회신할 수 있습니다.

![Holographic motorcycle 디자인이 실제 motorcycle 본문에 맞게 조정 되었습니다.](images/image8-640px.png)

Holograms 다른 곳에서 가능 하지 않은 개인 상호 작용을 사용 하도록 설정 합니다. HoloLens에서 세계의 위치를 알 수 있기 때문에 holographic 문자는 대화방을 탐색할 때 눈에 직접 볼 수 있습니다.

홀로그램도 주변과 상호 작용할 수 있습니다. 예를 들어 테이블 위에 holographic 바운스 구슬을 삽입할 수 있습니다. 그런 다음 [공중 탭](gestures.md#air-tap)을 사용 하 여 구슬 바운스를 시청 하 고 테이블에 도달할 때 소리를 만듭니다.

Holograms는 실제 개체에 의해 폐색 수도 있습니다. 예를 들어, holographic 문자는 외부의 도어를 살펴보고 벽 뒤에 있을 수 있습니다.

**Holograms와 실제 세계를 통합 하기 위한 팁**
* Gravitational 규칙에 맞춰 holograms 더 쉽게 이익은 수 있습니다. 제외 Holographic & dog를 공간에 부동으로 두지 않고 테이블의 vase에 배치 합니다.
* 대부분의 디자이너에서는 홀로그램이 앉아 있는 표면에 "네거티브 그림자"를 만들어 holograms를 더욱 believably 통합할 수 있음을 발견 했습니다. 홀로그램 주위에서 부드러운 광선을 만든 다음 광선에서 "그림자"를 빼서이를 수행 합니다. 소프트 광선은 실제 세계의 조명 및 환경에서 홀로그램 grounds 그림자를 통합 합니다.

## <a name="a-hologram-is-whatever-you-dream-up"></a>홀로그램은 어떤 것이 든 관계 없이

Holographic 개발자는 2D 화면 및 전 세계의 창의적인 기능을 활용할 수 있습니다. 빌드 *를* 선택 하세요.

![거실에서 Holographic 허수](images/designoverview.jpg)

## <a name="see-also"></a>참조
* [공간 음향](spatial-sound.md)
* [색, 광원 및 재질](color,-light-and-materials.md)
