---
title: 상호 작용할 수 없는 개체
description: 2D 추상 전 세계에서 이벤트를 트리거하는 데 사용 하는 비유를 오랫동안 단추입니다. 3 차원 혼합된 현실 세계에서 추상화를 더 이상이 환경으로 제한 될 필요가 없습니다.
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: 혼합된 현실 "," 컨트롤 "," 상호 작용 "," ui "," ux
ms.openlocfilehash: eea7eff6c591a9319b920936ce2be511cecb7496
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813828"
---
# <a name="interactable-object"></a>상호 작용할 수 없는 개체

2D 추상 전 세계에서 이벤트를 트리거하는 데 사용 하는 비유를 오랫동안 단추입니다. 3 차원 혼합된 현실 세계에서 추상화를 더 이상이 환경으로 제한 될 필요가 없습니다. 항목 수를 **상호 작용할 수 없는 개체** 이벤트를 트리거하는 합니다. 상호 작용할 수 없는 개체로 나타낼 수 있습니다 것과 테이블에는 커피 cup에서 공중에서 부동 풍선으로. 여전히 확인 수행 대화 상자 UI와 같이 이러한 특정 상황에서 기존 단추를 사용 합니다. 단추의 시각적 표시는 컨텍스트에 따라 달라 집니다.

![Interactible 개체](images/640px-interactibleobject-hero-640px.jpg)


## <a name="important-properties-of-the-interactable-object"></a>상호 작용할 수 없는 개체의 중요 한 속성

### <a name="visual-cue"></a>시각 신호

시각 신호는 토대로 신호 light의 형태로 눈으로 수신 하 고 시각적 인식 하는 동안 visual 시스템에서 처리 합니다. 시각적 시스템에서 여러 종류, 특히 사용자 기준 이므로 시각 신호 것은 대규모 전 세계를 인식 하는 방법에 대 한 정보입니다.

혼합된 현실에서 실제 환경과 holographic 개체 혼합 되어 있으므로 수 있습니다 상호 작용할 수 없는 개체는 이해 하기가 어렵습니다. 환경에서 상호 작용할 수 없는 개체에 대 한 상태 각 입력에 대해 차별화 된 시각을 제공 하는 것이 반드시 합니다. 이렇게 하면 사용자 이해 사용자 경험의 어느 부분이 상호 작용할 수 없는 이며 일관성 있는 상호 작용 메서드를 사용 하 여 사용자를 확신할 수 있습니다.

#### <a name="far-interactions"></a>먼 상호 작용

모든 개체에 대 한 해당 사용자와 상호 작용할 수 게이즈를 직접 광선 동작 컨트롤러의 광선 것이 좋습니다 이러한 세 가지 입력된 상태에 대 한 다양 한 시각적 표시를 할:
* **기본 (관찰)** : 개체의 기본 유휴 상태입니다.
* **대상된 (가리키기)** : 개체를 응시 커서를 사용 하 여 대상으로 하는 경우에 근접 또는 동영상 컨트롤러의 포인터 손가락으로 합니다.
* **누른**: 어 탭 제스처, 손가락 누르거나 동작 컨트롤러의 선택 단추를 사용 하 여 개체를 누를 때 표시 됩니다.

사용자의 입력된 상태에 시각 신호 제공 강조 표시 하거나 확장 하는 기법을 사용할 수 있습니다. Windows Mixed Reality 시작 메뉴 및 앱 바 단추 입력된 상태를 다른 시각화의 예제를 찾을 수 있습니다. 

![관찰 상태 시각화의 예제에서는 상태를 대상으로 하 고 누른 상태](images/640px-interactibleobject-states.png)<br>
*관찰 상태 시각화의 예제에서는 상태를 대상으로 하 고 누른 상태*

![관찰 상태 대상 상태 및 상태 holographic 단추 누름](images/MRTK_InteractableState.png)<br>
*관찰 상태 대상 상태 및 상태 holographic 단추 누름*

#### <a name="neardirect-interactions"></a>Near(direct) 상호 작용

HoloLens 2 명확 하 고 직접 입력 개체와 상호 작용할 수 있는 추적을 지원 합니다. 햅 틱 피드백 및 경우에 따라에서 완벽 한 깊이 인식 하지 않고 개체에서 직접은 얼마나 떨어져 하거나 터치 하는 여부를 확인 하기 어려운 수 있습니다. 에 제공 하는 관계에서는 손이의 특정 개체의 상태를 전달 하려면 충분 한 시각 신호를 제공 하는 것이 반드시 합니다.

다음 전달할 시각적 피드백을 사용 합니다.
* **기본 (관찰)** : 개체의 기본 유휴 상태입니다.
* **가리킨**: 홀로그램, 변경 시각적 개체는 직접 통신 거의 직접 경우 홀로그램 대상으로 합니다. 
* **거리와 상호 작용 지점의**: 직접 홀로그램 다가오면 디자인 손가락은 개체 멀리 방법과 예상된 지점의 상호 작용도 통신 하는 피드백
* **문의 시작**: 변경 시각적 개체 (광원, 색)는 터치 전달할 발생
* **잡았습니다**: 시각적 개체 (광원, 색)을 변경할 개체는 잡았습니다 하는 경우.
* **문의 끝**: 시각적 개체 (광원, 색)을 변경할 경우 터치를 마쳤습니다.

![시각화 상호 작용 상태 근처의 예](images/640px-interactibleobject-states-near.jpg)<br>
*시각화 상호 작용 상태 근처의 예*

합니다 [HoloLens 2 단추](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) 다른 입력된 상호 작용 상태 시각화의 예를 보여 줍니다.

![HoloLens 2에서 pressable 단추 예제](images/640px-interactibleobject-pressablebutton-650px2.jpg)<br>
*HoloLens 2에서 pressable 단추 예제*

HoloLens 2에서는 깊이 perception에서 사용자의 신뢰도 개선 하는 시각적 표시를 추가로 있습니다. 링의 손끝에서 표시 하 고 끝 가까워질수록 개체 처럼 확장 합니다. 키를 눌러 상태에 점에 링 결국 수렴 합니다. 이 visual 유도성을 지 원하는 개체에서의 거리를 이해 합니다.

![손끝 링 시각화](images/640px-interactibleobject-pressablebutton-650px3.jpg)<br>
*HoloLens 2의 손끝 링 시각화*

![직접 근접에 대 한 시각적 피드백](images/HoloLens2_Proximity.gif)<br>
*-경계 상자 근접도에 따라 시각적 피드백의 예*


### <a name="audio-cue"></a>오디오 신호
직접 직접 상호 작용에 대 한 적절 한 오디오 피드백 사용자 환경을 크게 향상할 수 있습니다. 다음 전달할 오디오 피드백을 사용 합니다.
* **문의 시작**: 터치가 시작 될 때 소리 재생
* **연락처 최종**: 터치 끝에서 소리 재생
* **잡기 시작**: 잡기 시작 될 때 소리 재생
* **끝을 잡고**: 잡기 끝에서 소리 재생

### <a name="voice-command"></a>음성 명령
모든 상호 작용할 수 없는 개체에 대 한 대체 상호 작용 옵션을 지원 하도록 반드시 합니다. 기본, 것이 좋습니다 상호 작용할 수 없는 모든 개체에 대 한 음성 명령을 지원 합니다. 검색 기능 향상을 위해 가리키기 상태에서 도구 설명을 제공할 수 있습니다.

<img src="images/640px-interactibleobject-voicecommand.jpg" alt="Tooltip for the voice command" title="음성 명령에 대 한 도구 설명" width="350"><br/>*음성 명령에 대 한 도구 설명*

## <a name="creating-interactable-object-with-mixed-reality-toolkit-mrtk"></a>혼합 현실 도구 키트 (MRTK)을 사용 하 여 상호 작용할 수 없는 개체 만들기

에  **[혼합 현실 Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)** , 일련의 Unity 스크립트를 찾을 수 있습니다 및 prefabs 도움이 되는 상호 작용할 수 없는 개체를 만듭니다. 다양 한 유형의 입력된 상호 작용 상태에 응답 하는 개체를 사용할 수 있습니다.

* **[Interactable](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)**
* **[Button](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)**
* **[직접 상호 작용 예제 장면](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)**

MixedRealityToolkit의 표준 셰이더와 같은 다양 한 옵션을 제공 **근접 light** 를 시각적 및 오디오 큐를 만들 수 있습니다.
* **[MRTK 표준 셰이더](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)**


## <a name="see-also"></a>참조

* **[경계 상자](app-bar-and-bounding-box.md)**
* **[개체 컬렉션](object-collection.md)**
* **[빌보드 및 tag-along](billboarding-and-tag-along.md)**
