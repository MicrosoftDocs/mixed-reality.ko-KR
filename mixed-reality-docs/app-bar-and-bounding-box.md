---
title: 앱 바 및 경계 상자
description: 앱 바에 일련의 단추를 홀로그램 경계 아래쪽 가장자리에 표시 하는 포함 된 개체 수준 메뉴입니다.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 경계 상자 막대는 앱
ms.openlocfilehash: ab472e1c988e6bdfb0a69d90e90280082b3db759
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813871"
---
# <a name="bounding-box-and-app-bar"></a>경계 상자과 앱 표시줄
![경계는 혼합 현실에서 개체를 조작 하기 위한 표준 인터페이스입니다.](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a>경계 상자는 무엇입니까?

경계는 혼합 현실에서 개체를 조작 하기 위한 표준 인터페이스입니다. 개체가 현재 조정할 수는 유도성 사용자를 제공 합니다. 모퉁이 개체 또한 확장할 수는 사용자에 게 알림. 이 visual 유도성 조정 모드를 외부에서 표시 되지 않은 경우에 사용자에 게-개체의 전체 영역을 표시 합니다. 없었다면 있습니다, 다른 개체 또는 화면에 맞춰 지 개체 있습니다 되지 않아야 하는 주위 공간 것 처럼 동작 처럼 보이기 때문에 특히 유용 합니다. HoloLens 2의 경계 상자 직접 직접 조작 작동 하며 사용자의 손가락의 근접성에 응답 합니다. 시각적 피드백을 사용자가 개체의 거리를 인식할 수 있도록 표시 됩니다. 

![HoloLens-의-관점 경계 상자를 통해 개체를 확장 합니다.](images/HoloLens2_BoundingBox.gif)<br>
*경계 상자를 통해 개체 크기 조정*

경계 상자 모퉁이 핸들 크기 조정에 대 한 광범위 하 게 인식된 패턴을 따릅니다. 

![HoloLens-의-관점 경계 상자를 통해 개체를 회전](images/HoloLens2_BoundingBox_Rotate.gif)<br>
*경계 상자를 통해 개체를 회전*


![직접 근접에 대 한 시각적 피드백](images/HoloLens2_Proximity.gif)<br>
*근접도에 따라 시각적 피드백*

경계 상자의 가장자리의 세로 사각형 affordances 회전 표시기 됩니다. 이렇게 하면 사용자 더 세밀 하 게 조정 해당 배치 홀로그램 위에 있습니다. 뿐만 아니라 수 조정 및 확장 있지만 이제도 회전 합니다.

* Unity 앱 개발을 위한 참조 [경계 상자 혼합 현실 도구 키트-Unity에서](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)



## <a name="what-is-the-app-bar"></a>앱 바는 무엇입니까?

앱 바에 일련의 단추를 홀로그램 경계 아래쪽 가장자리에 표시 하는 포함 된 개체 수준 메뉴입니다. 이 패턴은 일반적으로 사용자를 제거 하 고 홀로그램 조정할 수 있도록 사용 됩니다.

사용자 개체를 이동 하는 대로 세계를 잠글 수 있는 개체를 사용 하 여이 패턴은 사용 되므로 앱 바 사용자에 게 가장 가까운 개체 측에 항상 표시 됩니다. 이 빌보드 없습니다, 하는 동안 효과적으로 달성을 위해 동일한 결과가 됩니다. 사용자의 채워집니다 위치 또는 될 수 있는 사용 가능한 환경에서 다른 위치에서 블록 기능을 방지 합니다.

![홀로그램을 따라 이동 합니다. 앱 바는 다음과 같습니다.](images/HoloLens2_AppBarFollowing.gif)<br>
*앱 바가 따릅니다를 홀로그램을 따라 이동 합니다.*

앱 바는 주로 사용자의 환경에서 가져온된 개체를 관리 하는 방법으로 설계 되었습니다. 혼합된 현실에서 개체 지향은 위치와 방법을 완전히 제어할을 사용자가 경계 상자를 사용 하 여 결합 합니다.

* Unity 앱 개발을 위한 참조 [앱 바 혼합 현실 도구 키트-Unity에서](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)

## <a name="see-also"></a>참조
* [상호 작용 가능한 개체](interactable-object.md)
* [Unity의 텍스트](text-in-unity.md)
* [개체 컬렉션](object-collection.md)
* [진행률 표시](progress.md)
