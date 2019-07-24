---
title: Interactable 개체
description: 단추는 긴 2D 추상 세계에서 이벤트를 트리거하는 데 사용 되는 비유입니다. 3 차원 혼합 현실 세계에서는 이러한 추상화의 목표로 더 이상 국한 되지 않습니다.
author: cre8ivepark
ms.author: jennyk
ms.date: 06/06/2019
ms.topic: article
keywords: 혼합 현실, 컨트롤, 상호 작용, ui, ux
ms.openlocfilehash: 57299cbb758a69603fc68ad5d43af8f2216e5104
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415367"
---
# <a name="interactable-object"></a>Interactable 개체

단추는 긴 2D 추상 세계에서 이벤트를 트리거하는 데 사용 되는 비유입니다. 3 차원 혼합 현실 세계에서는 이러한 추상화의 목표로 더 이상 국한 되지 않습니다. 모든 항목은 이벤트를 트리거하는 **interactable 개체** 일 수 있습니다. Interactable 개체는 테이블의 커피에서 공기의 풍선 부동으로 표시할 수 있습니다. 대화 상자 UI에서와 같은 특정 상황에서는 여전히 기존 단추를 사용 합니다. 단추의 시각적 표시는 컨텍스트에 따라 달라 집니다.

![Interactible 개체](images/640px-interactibleobject-hero-640px.jpg)


## <a name="important-properties-of-the-interactable-object"></a>Interactable 개체의 중요 한 속성

### <a name="visual-cue"></a>시각적 표시

시각적 신호는 시각적 개체를 시각적으로 인식 하면서 시각적 시스템에서 처리 하 고 밝은 형태로 받은 토대로 된 큐입니다. 시각적 시스템은 다양 한 정보, 특히 사람에 게 중요 한 것 이므로 시각적 신호는 전 세계의 정보에 대 한 많은 정보를 표시 합니다.

혼합 현실에서는 holographic 개체가 실제 환경과 혼합 되어 있으므로 interactable 개체를 이해 하기 어려울 수 있습니다. 사용자 환경에서 interactable 개체의 경우 각 입력 상태에 대해 차별화 된 시각적 표시를 제공 하는 것이 중요 합니다. 이렇게 하면 사용자가 interactable 하는 환경 부분을 이해 하 고 사용자에 게 일관 된 상호 작용 방법을 확신할 수 있습니다.

#### <a name="far-interactions"></a>먼 상호 작용

사용자가 응시, 손 모양 및 모션 컨트롤러의 광선과 상호 작용할 수 있는 개체의 경우 다음과 같은 세 가지 입력 상태에 대해 서로 다른 시각적 표시를 사용 하는 것이 좋습니다.
* **기본 (관찰)** : 개체의 기본 유휴 상태입니다.
* **대상 지정 (가리키기)** : 개체가 응시 커서, 손가락 근접 또는 동작 컨트롤러의 포인터를 대상으로 하는 경우
* **누름**: 공기 탭 제스처를 사용 하 여 개체를 누르면 손가락을 누르거나 동작 컨트롤러의 선택 단추를 누릅니다.

강조 표시 또는 크기 조정과 같은 기술을 사용 하 여 사용자의 입력 상태에 시각적 신호를 제공할 수 있습니다. Windows Mixed Reality에서는 시작 메뉴와 앱 바 단추에서 다양 한 입력 상태를 시각화 하는 예제를 찾을 수 있습니다. 

![관찰 상태, 대상 상태 및 누름 상태 시각화의 예](images/640px-interactibleobject-states.png)<br>
*관찰 상태, 대상 상태 및 누름 상태 시각화의 예*

![Holographic 단추의 관찰 상태, 대상 상태 및 누름 상태](images/MRTK_InteractableState.png)<br>
*Holographic 단추의 관찰 상태, 대상 상태 및 누름 상태*

#### <a name="neardirect-interactions"></a>근거리 (직접) 상호 작용

HoloLens 2는 개체와 상호 작용할 수 있도록 하는 트레일러 추적 입력을 지원 합니다. 햅 피드백 및 완벽 한 수준 인식 없이 개체에서 손 거리를 확인 하는 것이 어려울 수 있습니다. 또는 접촉 하 고 있는지 여부를 확인 하는 것은 어려울 수 있습니다. 개체의 상태를 전달 하는 데 충분 한 시각적 신호를 제공 하는 것은 holograms와 관련 된 개체의 상태를 전달 하는 것이 중요 합니다.

시각적 피드백을 사용 하 여 다음을 전달 합니다.
* **기본 (관찰)** : 개체의 기본 유휴 상태입니다.
* **가리키기**: 손이 가장 가까이 있는 경우에는 시각적 개체를 대상으로 하 여 홀로그램을 대상으로 하는 통신으로 변경 합니다. 
* **상호 작용의 거리 및 지점**: 홀로그램 방법으로, 프로젝션 된 상호 작용 지점 뿐만 아니라 개체에서 손가락으로 떨어져 있는 정도를 전달 하도록 피드백을 디자인 합니다.
* **연락처 시작**: 시각적 개체 (광원, 색)를 변경 하 여 터치가 발생 했음을 알립니다.
* **Grasped**: 개체가 grasped 경우 시각적 개체 (광원, 색)를 변경 합니다.
* **연락처 끝**: 터치가 종료 되 면 시각적 개체 (밝은 색)를 변경 합니다.

![거의 상호 작용 상태 시각화의 예제](images/640px-interactibleobject-states-near.jpg)<br>
*거의 상호 작용 상태 시각화의 예제*

[HoloLens 2의 단추](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) 는 다양 한 입력 상호 작용 상태를 시각화 하는 예제를 보여 줍니다.

![HoloLens 2의 pressable 단추 예제](images/640px-interactibleobject-pressablebutton-650px2.jpg)<br>
*HoloLens 2의 pressable 단추 예제*

HoloLens 2에는 깊이 인식에 대 한 사용자의 신뢰도를 개선 하는 추가적인 시각적 표시 큐가 있습니다. Fingertip가 개체에 가까울수록 fingertip의 링이 표시 되 고 축소 됩니다. 링은 결국 누름 상태에서 점으로 수렴. 이 시각적 affordance는 사용자가 개체 로부터의 거리를 이해 하는 데 도움이 됩니다.

![Fingertip 링 시각화](images/640px-interactibleobject-pressablebutton-650px3.jpg)<br>
*HoloLens의 Fingertip 링 시각화 2*

![근접 한 시각적 피드백](images/HoloLens2_Proximity.gif)<br>
*근접 경계 상자를 기준으로 하는 시각적 피드백의 예*


### <a name="audio-cue"></a>오디오 큐
직접 상호 작용을 위해 적절 한 오디오 피드백을 통해 사용자 환경을 크게 향상 시킬 수 있습니다. 오디오 피드백을 사용 하 여 다음을 전달 합니다.
* **연락처 시작**: 터치 시작 시 소리 재생
* **연락처 끝**: 터치 엔드에서 소리 재생
* **시작 하기**: 잡기 시작 시 소리 재생
* **종료**: 잡기 쪽에서 소리 재생

### <a name="voice-command"></a>음성 명령
Interactable 개체의 경우 대체 상호 작용 옵션을 지 원하는 것이 중요 합니다. 기본적으로 interactable 되는 모든 개체에 대해 음성 명령을 지 원하는 것이 좋습니다. 검색 가능성을 향상 시키기 위해 가리키기 상태에 도구 설명을 제공할 수 있습니다.

<img src="images/640px-interactibleobject-voicecommand.jpg" alt="Tooltip for the voice command" title="음성 명령에 대 한 도구 설명" width="350"><br/>*음성 명령에 대 한 도구 설명*

## <a name="sizing"></a>크기 조정
사용자가 모든 interactable 개체를 쉽게 사용할 수 있도록 하려면 사용자의 거리를 기준으로 interactable이 최소 크기 (시각적 원호의 각도로 측정 되는 시각적 각도)를 충족 하는지 확인 하는 것이 좋습니다. 시각적 각도는 사용자의 눈동자와 개체 간의 거리를 기준으로 하며 일정 하 게 유지 되 고, 대상의 실제 크기는 사용자의 거리가 변경 될 때 변경 될 수 있습니다. 사용자의 거리를 기준으로 개체의 필요한 실제 크기를 확인 하려면 다음과 같은 시각적 각도 계산기를 사용해 [보세요.](http://elvers.us/perception/visualAngle/)

다음은 interactable 콘텐츠의 최소 크기에 대 한 권장 사항입니다.

### <a name="target-size-for-direct-hand-interaction"></a>직접 상호 작용의 대상 크기
| 거리 | 시야각 | Size |
|---------|---------|---------|
| 45cm  | 2 ° 미만 | 1.6 x 1.6 cm |

![직접 상호 작용의 대상 크기](images/TargetSizingNear.jpg)<br>
*직접 상호 작용의 대상 크기*

직접 상호 작용에 대 한 단추를 만들 때 아이콘 및 잠재적으로 일부 텍스트를 포함할 수 있는 충분 한 공간이 있는지 확인 하려면 최소 크기인 3.2 x 3.2 cm을 권장 합니다. * *

| 거리 | 최소 크기 |
|---------|---------|
| 45cm  | 3.2 x 3.2 cm |

![단추의 대상 크기](images/TargetSizingButtons.png)<br>
*단추의 대상 크기*


### <a name="target-size-for-hand-ray-or-gaze-interaction"></a>핸드 레이 또는 응시 상호 작용의 대상 크기
| 거리 | 시야각 | Size |
|---------|---------|---------|
| 2m  | 1 ° 보다 작음 | 3.5 x 3.5 cm |

![핸드 레이 또는 응시 상호 작용의 대상 크기](images/TargetSizingFar.jpg)<br>
*핸드 레이 또는 응시 상호 작용의 대상 크기*

## <a name="creating-interactable-object-with-mixed-reality-toolkit-mrtk"></a>혼합 현실 도구 키트를 사용 하 여 interactable 개체 만들기 (MRTK)

**[혼합 현실 도구 키트](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 에서 interactable 개체를 만드는 데 도움이 되는 일련의 Unity 스크립트 및 prefabs를 찾을 수 있습니다. 이러한 개체를 사용 하 여 다양 한 유형의 입력 상호 작용 상태에 대해 개체에 응답할 수 있습니다.

* [Interactable](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [Button](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [직접 상호 작용 예제 장면](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

MixedRealityToolkit의 표준 셰이더는 시각적 및 오디오 큐를 만드는 데 도움이 되는 **근접 조명** 과 같은 다양 한 옵션을 제공 합니다.
* [MRTK 표준 셰이더](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


## <a name="see-also"></a>참조

* [경계 상자](app-bar-and-bounding-box.md)
* [개체 컬렉션](object-collection.md)
* [빌보딩 및 태그얼롱](billboarding-and-tag-along.md)