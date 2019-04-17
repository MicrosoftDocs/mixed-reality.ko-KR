---
title: 상호 작용할 수 없는 개체
description: 2D 추상 전 세계에서 이벤트를 트리거하는 데 사용 하는 비유를 오랫동안 단추입니다. 3 차원 혼합된 현실 세계에서 추상화를 더 이상이 환경으로 제한 될 필요가 없습니다.
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: 혼합된 현실 "," 컨트롤 "," 상호 작용 "," ui "," ux
ms.openlocfilehash: f349d21707375690e00b0f7e465634c62be1537e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59601180"
---
# <a name="interactable-object"></a>상호 작용할 수 없는 개체

2D 추상 전 세계에서 이벤트를 트리거하는 데 사용 하는 비유를 오랫동안 단추입니다. 3 차원 혼합된 현실 세계에서 추상화를 더 이상이 환경으로 제한 될 필요가 없습니다. 항목 수를 **상호 작용할 수 없는 개체** 이벤트를 트리거하는 합니다. 상호 작용할 수 없는 개체로 나타낼 수 있습니다 것과 테이블에는 커피 cup에서 공중에서 부동 풍선으로. 여전히 확인 수행 대화 상자 UI와 같이 이러한 특정 상황에서 기존 단추를 사용 합니다. 단추의 시각적 표시는 컨텍스트에 따라 달라 집니다.

![영웅 이미지 interactible 개체](images/640px-interactibleobject-hero-640px.jpg)


에  **[혼합 현실 Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, 일련의 Unity 스크립트를 만들어 놓은 및 prefabs 도움이 되는 상호 작용할 수 없는 개체를 만듭니다. 이러한 표준 상호 작용 상태를 사용 하 여 사용자를 상호 작용할 수 있는 개체의 모든 형식을 만드는 데 사용할 수 있습니다: 관찰을 대상으로 하 고 누르면 됩니다. 자신의 자산을 사용 하 여 시각적 디자인을 쉽게 지정할 수 있습니다. 자세한 애니메이션 만들기 및 할당 Unity의 애니메이션 컨트롤러의 상호 작용 상태에 대 한 해당 애니메이션 클립 또는 offset 및 배율을 사용 하 여 사용자 지정할 수 있습니다. 


## <a name="visual-feedback-for-the-different-input-interaction-states"></a>다른 입력된 상호 작용 상태에 대 한 시각적 피드백

혼합된 현실에서 실제 환경과 holographic 개체 혼합 되어 있으므로 수 있습니다 상호 작용할 수 없는 개체는 이해 하기가 어렵습니다. 환경에서 상호 작용할 수 없는 개체에 대 한 상태 각 입력에 대해 차별화 된 시각적 피드백을 제공 하는 것이 반드시 합니다. 이렇게 하면 사용자 이해 사용자 경험의 어느 부분이 상호 작용할 수 없는 이며 일관성 있는 상호 작용 메서드를 사용 하 여 사용자를 확신할 수 있습니다.

모든 개체에 대 한 해당 사용자와 상호 작용할 수, 것이 좋습니다 이러한 세 개의 입력 상태에 대 한 다양 한 시각적 피드백을 할:
* **관찰**: 개체의 기본 유휴 상태입니다.
* **대상**: 개체를 응시 커서를 사용 하 여 대상으로 하는 경우에 근접 또는 동영상 컨트롤러의 포인터 손가락으로 합니다.
* **누른**: 어 탭 제스처, 손가락 누르거나 동작 컨트롤러의 선택 단추를 사용 하 여 개체를 누를 때 표시 됩니다.

![Holographic 단추](images/640px-interactibleobject-holographicbutton-650px.jpg)<br>
*상태 대상 상태 및 상태를 누르면 관찰*

Windows Mixed Reality 시작 메뉴 및 앱 바 단추 입력된 상태를 다른 시각화의 예제를 찾을 수 있습니다. 사용자의 입력된 상태에 대 한 시각적 피드백을 제공할 강조 표시 하거나 확장 하는 기법을 사용할 수 있습니다.

입력을 추적 하는 완전히 표시 된 직접 지원 하기 때문 HoloLens 2에서는 바늘 근접도에 따라 추가 affordances를 제공할 수 있습니다 했습니다. 합니다 [HoloLens 2 단추](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) 이 예제를 보여 줍니다.

![Pressable 단추](images/640px-interactibleobject-pressablebutton-650px.jpg)<br>




## <a name="interactable-object-samples"></a>상호 작용할 수 없는 개체 샘플

### <a name="mesh-button"></a>메시 단추

![메시 단추](images/640px-interactibleobject-meshbutton.jpg)

이들은 상호 작용할 수 없는 개체로 기본 형식 및 가져온된 3D 메시를 사용 하는 예제입니다. 각 입력된 상호 작용 상태를 응답에 서로 다른 규모, 오프셋 및 색 값을 쉽게 할당할 수 있습니다.

### <a name="toolbar"></a>도구 모음

![도구 모음](images/640px-interactibleobject-toolbar.jpg)

도구 모음에는 혼합된 현실 환경에서 널리 사용 되는 패턴입니다. 와 같은 추가 동작을 사용 하 여 단추의 간단한 모음입니다 [Billboarding 및 tag-along](billboarding-and-tag-along.md)합니다. 이 예제는 MixedRealityToolkit에서 Billboarding 및 tag-along 스크립트를 사용합니다. 속도 및 임계값 값 이동 거리를 포함 하 여 자세한 동작 제어할 수 있습니다.

### <a name="traditional-button"></a>전통적인 단추

![전통적인 단추](images/640px-interactibleobject-traditionalbutton.jpg)

이 예제에서는 일반적인 2D 스타일 단추를 보여 줍니다. 각 입력된 상태는 약간 다른 깊이 애니메이션 속성에 있습니다.

### <a name="other-examples"></a>다른 예제

![푸시 단추](images/640px-interactibleobject-pushbutton.jpg)<br>
*푸시 단추*
<br>
![실제 수명 개체](images/640px-interactibleobject-reallifeobject.jpg)<br>
*실제 개체*

HoloLens를 사용 하 여 물리적 공간을 활용할 수 있습니다. 실제 벽 holographic 누름 단추를 가정해 보겠습니다. 또는 실제 테이블에서 coffee cup 어떤가요? 소프트웨어 모델링에서 가져온 3D 모델을 사용 하 여 실제 개체와 유사 하는 상호 작용할 수 없는 개체를 만들 수 있습니다. 디지털 개체 이므로 마법 상호 작용을 추가할 수 있습니다.

## <a name="interactable-object-in-mixed-reality-toolkit"></a>혼합 현실 도구 키트의 상호 작용할 수 없는 개체
찾을 수 있습니다는 [Interactable의 예는 혼합 현실 도구 키트의 개체](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)


## <a name="see-also"></a>참조
* [혼합된 현실 도구 키트-Unity pressable 단추](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [개체 컬렉션](object-collection.md)
* [빌보드 및 tag-along](billboarding-and-tag-along.md)
