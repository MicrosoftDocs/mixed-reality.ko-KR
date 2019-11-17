---
title: Billboarding 및 태그 동반
description: Billboarding를 사용 하는 개체는 항상 사용자를 대상으로 합니다.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, billboarding, 태그 동반
ms.openlocfilehash: ff2b1ce20174b1b9aecbb90b1d1dc3e8896b3761
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143134"
---
# <a name="billboarding-and-tag-along"></a>Billboarding 및 태그 동반

<br>

<img src="images/UX/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a>Billboarding 란?

Billboarding는 혼합 현실에서 개체에 적용할 수 있는 동작 개념입니다. Billboarding를 사용 하는 개체는 항상 사용자를 대상으로 합니다. 이는 사용자의 환경에 배치 된 정적 개체 (세계에서 잠김)를 이동 해야 하는 경우에는 사용자의 환경에 배치 된 정적 개체를 숨기 거 나 읽을 수 없게 하는 텍스트 및 menuing 시스템에 특히 유용 합니다.

Billboarding를 사용 하는 개체는 사용자 환경에서 자유롭게 회전할 수 있습니다. 디자인 고려 사항에 따라 단일 축으로 제한 될 수도 있습니다. Billboarded 개체는 다른 개체에 너무 가까이 배치 되거나 HoloLens에 스캔 된 표면이 너무 가까이 배치 된 경우에는 클리핑 또는 려 수 있습니다. 이를 방지 하려면 billboarding에 대해 사용 하도록 설정 된 축에서 회전할 때 개체가 생성할 수 있는 총 공간을 고려해 야 합니다.

<br>

---
## <a name="what-is-a-tag-along"></a>태그의 정의

태그 동반은 holograms에 추가할 수 있는 동작 개념입니다. 태그 동반 개체는 사용자가 편안 하 게 상호 작용할 수 있도록 범위를 유지 하려고 합니다.

HoloLens 핀 패널 ![태그 동반 동작의 좋은 예](images/tagalong-1000px.jpg)<br>
*HoloLens 시작 메뉴는 태그 동반 동작의 좋은 예입니다.*

태그를 포함 하는 개체에는 동작 방식을 세밀 하 게 조정할 수 있는 매개 변수가 있습니다. 사용자가 환경 주위에서 이동할 때 원하는 대로 사용자의 시야에 콘텐츠를 배치 하거나 축소할 수 있습니다. 사용자가 이동 하면 콘텐츠는 사용자가 이동 하는 속도에 따라 사용자의 주변 내에 유지 됩니다. 사용자가 이동 하면 콘텐츠가 일시적으로 표시 되지 않을 수 있습니다. 사용자가 태그를 따라 개체를 gazes 하는 경우에는 더 자세히 볼 수 있습니다. 콘텐츠를 항상 "한 눈에 파악" 하는 것은 사용자에 게 콘텐츠가 있는 방향을 잊지 않도록 하는 것입니다.

추가 매개 변수를 사용 하면 사용자의 헤드에 대 한 태그 동반 개체 느낌을 고무 띠로 만들 수 있습니다. 완충 가속 또는 감속은 개체에 대 한 가중치를 제공 하 여 더 물리적으로 표시 되도록 합니다. 이 스프링 동작은 사용자가 태그를 사용 하는 방법에 대 한 정확한 멘 탈 모델을 빌드하는 데 도움이 되는 affordance입니다. 오디오는 사용자가 태그 동반 모드에서 개체를 사용할 때 추가 affordances을 제공 하는 데 도움이 됩니다. 오디오는 이동 속도를 보강 해야 합니다. 고속 헤드 턴은 모든 효과가 있는 경우 자연 속도로 이동 하는 것이 최소 오디오를 포함 하는 동안 보다 눈에 띄는 음향 효과를 제공 해야 합니다.

진정한 헤드 잠금 콘텐츠와 마찬가지로 태그를 사용 하는 개체는 사용자의 뷰에서 무분별 또는 스프링을 너무 많이 이동 하는 경우 과도 하 게 또는 nauseating을 입증할 수 있습니다. 사용자가이를 확인 하 고 신속 하 게 중지 하면 해당 사용자가 중지 된 것을 알 수 있습니다. 이러한 잔액은 세계를 중지 하는 것을 알 수 있는 것을 알 수 있습니다. 그러나 사용자가 중지 되었을 때 태그를 따라 이동 하는 경우에는 해당 사용자의 감지를 혼동할 수 있습니다.

<br>

---

## <a name="billboarding-and-tag-along-in-mrtkmixed-reality-toolkit-for-unity"></a>Billboarding 및 태그-Unity 용 MRTK (혼합 현실 도구 키트)
**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 는 Billboarding 및 태그 동반 동작에 대 한 스크립트를 제공 합니다. Billboard.cs 스크립트를 모든 개체에 할당 하 여 billboarding 동작을 추가 하 고 개체를 항상 사용자에 게 표시 합니다. 태그 동반 동작을 추가 하려면 RadialView.cs 스크립트를 사용 합니다. Lerping 시간, 거리, 학위 등의 다양 한 옵션을 조정할 수 있습니다.

* [MRTK-방사형 보기 해 찾기](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html#radialview)
* [MRTK-빌보드 스크립트](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


<br>

---

## <a name="see-also"></a>참고 항목

* [커서](cursors.md)
* [손 광선](point-and-commit.md)
* [Button](button.md)
* [상호 작용 가능한 개체](interactable-object.md)
* [경계 상자 및 앱 바](app-bar-and-bounding-box.md)
* [조작](direct-manipulation.md)
* [손 메뉴](hand-menu.md)
* [Near 메뉴](near-menu.md)
* [개체 컬렉션](object-collection.md)
* [음성 명령](voice-input.md)
* [키보드](keyboard.md)
* [Tooltip](tooltip.md)
* [슬레이트](slate.md)
* [슬라이더](slider.md)
* [셰이더가](shader.md)
* [빌보딩 및 태그얼롱](billboarding-and-tag-along.md)
* [진행률 표시](progress.md)
* [표면 자성](surface-magnetism.md)
