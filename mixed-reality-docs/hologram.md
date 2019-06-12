---
title: 홀로그램이란?
description: HoloLens 살펴보고 3 차원 홀로그램 상호 작용할 수 있습니다, 개체의 이루어지고 있습니다 주변에 나타나는 사운드.
author: beaufolsom
ms.author: befolsom
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, 홀로그램, 디자인, 상호 작용
ms.openlocfilehash: 714b08db23aa641252291aebe89fa3059c209a6f
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829785"
---
# <a name="what-is-a-hologram"></a>홀로그램이란?

HoloLens 만들 수 있습니다 **홀로그램**조명의 개체 한 사운드 나타나는, 주변에 실제 개체인 것 처럼 합니다. 홀로그램 응답할 하 [gaze](gaze.md), [제스처](gestures.md) 하 고 [음성 명령](voice-input.md)와 상호 작용할 수 있습니다 [실제 화면](spatial-mapping.md) 와 관련해 서. 홀로그램을 사용 하 여 전 세계의 일부인 디지털 개체를 만들 수 있습니다.

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
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (첫 번째 범용)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>몰입 형 헤드셋</strong></a></td>
    </tr>
     <tr>
        <td>홀로그램</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="a-hologram-is-made-of-light-and-sound"></a>빛과 소리를 홀로그램이 됩니다.

홀로그램은 HoloLens [렌더링](rendering.md) 사용자의 눈 앞에 직접 holographic 프레임에 표시 합니다. 홀로그램 표시에서 밝은 테마와 밝은 환경에서 모두 참조 하는 것을 의미 하는 고객의 세계에 빛을 추가 합니다. HoloLens는 홀로그램 색을 사용 하 여 black 렌더링 없습니다 있도록 light 자신만에서 제거 되지 않습니다. 대신, black 콘텐츠 투명 하 게 나타납니다.

홀로그램 많은 다른 모양 및 동작에 있을 수 있습니다. 일부는 현실적이 고 실선, 있고 cartoonish 및 마법의 합니다. 홀로그램 환경의 기능을 강조 표시할 수 있습니다 하 고 앱의 사용자 인터페이스의 요소 수입니다.

![Holographic dog 현장에서 탐색](images/fang3-640px.jpg)

홀로그램으로 만들 수도 [소리](spatial-sound.md), 환경에서 특정 위치에서 온 것으로 표시 됩니다. HoloLens에서 사운드을 가리지 않고에 귀 바로 위에 있는 두 스피커에서 제공 됩니다. 표시와 마찬가지로, 스피커는 덧셈, 환경에서 소리를 차단 하지 않고 새 소리를 소개 합니다.

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a>홀로그램 환경 또는 늘어나면 태그에 배치할 수 있습니다.

수를 홀로그램 하려는 특정 위치에 있는 경우 [배치](coordinate-systems.md) 전 세계에서 해당 정확 하 게 있습니다. 해당 홀로그램 주위를 탐색할 때와 관련해 서 전 세계를 기준으로 안정적인 표시 됩니다. 사용 하는 경우는 [공간 앵커](coordinate-systems.md#spatial-anchors) 세계 견고 하 게 해당 개체를 고정 하려면 시스템도 기억할 수 있는 생략 하면 나중에 다시 방문 하는 경우.

![테이블에 앉아 holographic 빌드 maquette](images/image5-640px.png)

일부 홀로그램 사용자를 대신 수행합니다. 이러한 tag-along 홀로그램 워크 위치에 관계 없이 사용자를 기준으로 배치 합니다. 잠시 있습니다를 사용 하 여 홀로그램을 가져오고 다른 대화방에 표시 되 면 벽에 배치도 선택할 수 있습니다.

**모범 사례**
* 일부 시나리오 홀로그램 유지 쉽게 검색할 수 또는 환경 전체에서 표시 되도록 요구할 수 있습니다. 두 가지 고급 이런 종류의 위치를 지정 합니다. 보겠습니다 **"표시 잠긴"** 하 고 **"본문 잠긴"** 합니다.
   * 콘텐츠 표시 잠긴 되려면 "잠겨 있음"이라는 장치 화면. 이 여러 가지 이유로는 비 자연 느낌 "clingyness"는 많은 사용자가 불편을 포함 하 고 "흔들 었 합니다." 하려는 대 한 까다로운 일반적으로 많은 디자이너 발견 콘텐츠 표시 잠기지 않도록 것이 좋습니다.
   * 본문 잠긴 방법은 훨씬 forgivable입니다. 본문-잠금은 홀로그램 사용자의 본문 또는 게이즈 벡터 테더 링 된은 사용자 중심 3d 공간에 배치 하는 경우입니다. 다양 한 환경을 위치를 홀로그램 "따르는"를 해당 본문 회전 하 고 공간을 홀로그램 손실 없이 이동할 수 있는 사용자 게이즈를 본문 잠금 동작을 채택 했습니다. 지연 통합 홀로그램 이동을 자연스럽 게 느낄 수 있습니다. 예를 들어, 일부 핵심 Windows Holographic 운영 체제의 UI는 사용자가 헤드를 설정 하는 동안 사용자의 게이즈 살짝, 탄력적 같은 지연 시간을 다음에 나오는 본문-잠금에서 변형을 사용 합니다.
* 배치는 홀로그램 편안한 보기 거리에 일반적으로 헤드에서 약 1 ~ 2 미터입니다.
* 사용자 자신의 관점을 변경할 때 콘텐츠를 표시 한 쪽에 애니메이션을 적용 하는 것이 좋습니다. 하거나 holographic 프레임에서 계속 되어야 하는 요소에 대 한 드리프트의 용량을 제공 합니다.

**홀로그램 최적의 영역-1.25 m 5 분 사이 배치**

두 가지 단위가 가장 최적의 이며 1 미터에서 가져올 더 가깝게 환경이 저하 됩니다. 더 가까이 있을 수록 보다 1 미터 거리 에서도 홀로그램 방어에서 정기적으로 이동 하는 고정 홀로그램 보다 문제가 될 가능성이 높습니다. 정상적으로 클리핑 또는 너무 가깝게를 하지 못하도록 예기치 않은 환경으로 사용자를 jar 가져오면 내용을 페이드아웃 고려 합니다.

![사용자 로부터 홀로그램 배치에 대 한 최적의 거리입니다.](images/distanceguiderendering-640px.png)

## <a name="a-hologram-interacts-with-you-and-your-world"></a>하 여 세계와 상호 작용을 홀로그램

빛 소리;에 대 한 제공 되지 않습니다. 전 세계의 활성 부분 또한 하기도 합니다. 홀로그램 및 제스처를 손으로 게이즈를 홀로그램을 따르도록 시작할 수 있습니다. 홀로그램에 음성 명령을 지정 하 고 응답할 수 있습니다.

![실제 motorcycle 본문에 맞추는 holographic motorcycle 디자인](images/image8-640px.png)

홀로그램 다른 곳에서 가능 하지 않은 개인 상호 작용을 사용 하도록 설정 합니다. HoloLens 알기 전 세계의 경우, 때문에 holographic 문자를 확인할 수 있습니다 시각에서 직접 전시실 안내 합니다.

홀로그램 환경 상호 작용할 수도 있습니다. 예를 들어 테이블 위에 holographic 바운스 공을 배치할 수 있습니다. 그런 다음 프로그램 [어 탭](gestures.md#air-tap), 공 띄우기 고 사운드 테이블에 도달할 때를 시청 하세요.

실제 개체에 의해 홀로그램을 폐색 수도 있습니다. 예를 들어, holographic 문자 수 및 프로그램 sight 부족 벽을 뒤 문을 통해 방법을 설명 합니다.

**홀로그램 및 실제 세계를 통합 하기 위한 팁**
* Gravitational 규칙에 맞추어 관련이 하기 쉽고 더 이익은 홀로그램 수 있습니다. eg: 처음부터 및 테이블에 꽃병 holographic dog 배치할 것 보다는 공간에서 부동 합니다.
* 대부분의 디자이너 홀로그램을 홀로그램 하나 더 있는데요는 화면에 "음수 그림자"를 만들어 훨씬 더 believably 통합 수를 발견 했습니다. 기초는 홀로그램 주위에 소프트 광선을 만들고 다음 광선이에서 "그림자"를 빼서 여이 수행 합니다. 그림자 환경의 홀로그램 grounds와 소프트 광선 조명이 실제 환경에서 사용 하 여 통합.

## <a name="a-hologram-is-whatever-you-dream-up"></a>홀로그램은 가능한 항목

Holographic 개발자와 관련해 서 전 세계 및 2D 화면에서 창의력을 중단을 해야 합니다. 항목은 *있습니다* 빌드?

![거실 holographic 허수 world](images/designoverview.jpg)

## <a name="see-also"></a>참조
* [공간 음향](spatial-sound.md)
* [색, 광원 및 재질](color,-light-and-materials.md)
