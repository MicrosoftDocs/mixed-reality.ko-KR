---
title: 혼합 현실 응용 프로그램에서 소리 사용
description: 공간 사운드는 혼합 현실 응용 프로그램에서 집중 교육, 접근성 및 UX 디자인을 위한 강력한 도구입니다.
author: kegodin
ms.author: kegodin
ms.date: 11/02/2019
ms.topic: article
keywords: Windows Mixed Reality, 공간 소리, 디자인, 스타일
ms.openlocfilehash: c069095808eaa9d31b1ffa41dbaa29c9f635837b
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641059"
---
# <a name="using-sound-in-mixed-reality-applications"></a>혼합 현실 응용 프로그램에서 소리 사용

소리를 사용 하 여 사용자의 응용 프로그램 상태 모델을 멘 탈 합니다. 적절 한 경우 spatialization를 사용 하 여 혼합 된 세계에 소리를 놓습니다. 이러한 방식으로 청각 및 시각적 개체를 연결 하면 많은 상호 작용의 직관적인 특성을 deepens 사용자 자신감을 높일 수 있습니다.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="when-should-i-add-sounds"></a>소리를 추가 해야 하는 경우
혼합 현실 응용 프로그램은 실제 인터페이스의 부족으로 인해 2D 화면에서 응용 프로그램 보다 사운드가 더 많이 필요 합니다. 소리는 사용자에 게 알리거나 상호 작용을 강화할 때 추가 해야 합니다.

### <a name="inform-and-reinforce"></a>알림 및 보강
* 알림과 같이 사용자가 시작 하지 않은 이벤트의 경우 사용자에 게 변경이 발생 했음을 알리는 소리를 추가 하는 것이 좋습니다.
* 상호 작용에는 여러 단계가 있을 수 있습니다. 소리 전환을 강화 하려면 소리를 사용 하는 것이 좋습니다.

상호 작용, 이벤트 및 제안 된 사운드 특성의 예는 아래를 참조 하세요.

### <a name="exercise-restraint"></a>운동 지지대
사용자는 오디오 정보에 대해 무제한 용량을 갖지 않습니다.
* 각 사운드는 특정 한 중요 한 정보를 전달 해야 합니다.
* 사용자에 게 알리는 소리를 재생할 때 다른 소리의 볼륨을 일시적으로 줄입니다.
* 단추 가리키기 소리 (아래 참조)에서 소리를 과도 하 게 트리거하지 않도록 시간 지연을 추가 합니다.

### <a name="dont-rely-solely-on-sounds"></a>소리만 사용 하지 않음
사용 되는 소리는 사용자가이를 듣지 못할 경우 유용 하지만, 소리를 끄면 응용 프로그램을 사용할 수 있습니다.
* 사용자가 청각 장애가 있을 수 있습니다.
* 응용 프로그램을 큰 환경에서 사용할 수 있습니다.
* 사용자에 게 장치 오디오를 사용 하지 않도록 설정 하는 개인 정보나 기타 이유가 있을 수 있습니다.

## <a name="how-should-i-sonify-interactions"></a>상호 작용을 어떻게 sonify 하나요?
혼합 현실의 상호 작용 형식에는 제스처, 직접 조작 및 음성이 포함 됩니다. 이러한 상호 작용의 소리를 선택 하거나 디자인 하려면 다음의 제안 된 특성을 사용 합니다.

### <a name="gesture-interactions"></a>제스처 상호 작용
혼합 현실에서 사용자는 커서를 사용 하 여 단추와 상호 작용할 수 있습니다. 단추 동작은 사용자가 상호 작용을 취소할 수 있도록 단추를 눌렀다 놓은 경우를 제외 하 고 사용자가 단추를 눌렀다 놓으면 일반적으로 수행 됩니다. 이러한 단계를 보강 하려면 소리를 사용 합니다. 또한 사용자가 먼 단추를 대상으로 하는 것을 지원 하려면 커서 가리키기 소리를 사용 하는 것이 좋습니다.
* 단추 누르기 소리를 tactile 클릭 해야 합니다. 예: [MRTK_ButtonPress .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* 단추를 누르지 않는 소리는 비슷한 tactile 느낌을 가져야 합니다. 볼록 피치와 누르기 사운드가 있으면 완료 강화. 예: [MRTK_ButtonUnpress .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonUnpress.wav)
* 가리키기 소리의 경우 낮은 빈도 thud 또는 범프와 같이 약한 및 비 위협 사운드를 사용 하는 것이 좋습니다.


### <a name="direct-manipulation"></a>직접 조작
HoloLens 2에서는 두 개의 부분으로 된 손 모양 추적을 통해 사용자 인터페이스 요소를 직접 조작할 수 있습니다. 소리는 물리적 피드백이 없다는 중요 한 대체 항목입니다.

사용자가 키 이동의 아래쪽에 도달 했을 때 물리적으로 표시 되지 않기 때문에 직접 조작에서 **단추 누르기** 소리가 중요 합니다. 주요 여행에 대 한 시각적 표시기는 작은, 미묘한 및 폐색 수 있습니다. 제스처 상호 작용의 경우와 마찬가지로 단추 누름은 클릭과 같은 짧은 tactile 소리를 가져야 하 고, unpresses는 볼록 피치를 사용 하 여 비슷한 클릭을 가져야 합니다.
* 예: [MRTK_ButtonPress .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* 예: [MRTK_ButtonUnpress .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonUnpress)

직접 조작에서 **잡기** 나 **릴리스** 를 확인 하는 것은 시각적으로 통신 하기 어렵습니다. 사용자의 손을 시각적 효과를 발휘 하는 경우가 많으며, 하드 없는 개체는 실제 시각적으로 "잡기"를 하지 않습니다. 반면에 소리는 성공적인 잡기와 릴리스 상호 작용을 효과적으로 전달할 수 있습니다.
* 잡기 작업에는 개체 주위에 손가락을 muffled 하는 것을 evokes 하는 짧고 약간의 tactile 사운드가 있어야 합니다. 경우에 따라 소리를 이동 하는 경우 소리의 영향을 whoosh 하는 "" 사운드가 수반 됩니다. 예: [MRTK_Move_Start .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_Move_Start.wav)
* 릴리스 작업에는 유사 하 고 tactile 소리가 있어야 하 고, 일반적으로 광고에서 중단 되 고, 그 다음에는 영향을 주고 개체 정착를 전달 하는 "whoosh"가 발생 합니다. 예: [MRTK_Move_End .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_Move_End.wav)

**그리기** 상호 작용은 사용자 손을 이동 하 여 볼륨을 제어 하는 반복, 영구 사운드를 사용 해야 하며, 사용자 손을 계속 사용 하는 경우, 사용자 손을 빠르게 이동할 때의 최대 볼륨에 해당 볼륨을 완전히 자동으로 유지 합니다.



### <a name="voice-interactions"></a>음성 상호 작용
음성 상호 작용에는 종종 미묘한 시각적 요소가 있습니다. 소리를 사용 하 여 상호 작용 단계를 보강 합니다. 제스처와 직접 조작 소리를 구분 하기 위해 더 많은 톤 소리를 선택 하는 것이 좋습니다.

* 음성 **명령 확인**에는 양수의 톤을 사용 합니다. 이 경우에는 톤 및 주요 음악 간격이 적용 됩니다.
* 음성 명령 **실패**에 대해 더 짧고 긍정적으로 떨어지는 톤을 사용 합니다. 음수 소리 방지 대신 더 percussive 중립적인 소리를 사용 하 여 응용 프로그램이 상호 작용에서 이동 하는 것을 통신 합니다.
* 응용 프로그램에서 절전 모드 해제 단어를 사용 하는 경우, 장치에서 **수신 대기를 시작**하 고 응용 프로그램이 수신 대기 하는 동안 미묘한 반복 소리가 발생 하면 짧은 gentle 톤을 사용 합니다. 

### <a name="notifications"></a>알림
알림은 응용 프로그램 상태 변경 내용 및 사용자가 시작 하지 않은 기타 이벤트 (예: 프로세스 완료, 메시지 및 호출)를 전달 합니다.

혼합 현실에서 이동 하는 개체는 사용자의 뷰 필드 밖으로 이동할 수 있습니다. 개체 및 동작 속도에 따라 달라 지는 spatialized 소리를 사용 하 여 **애니메이션 개체** 를 함께 제공 합니다.
* 또한 애니메이션의 끝에서 spatialized 소리를 재생 하 여 사용자에 게 새 위치를 알려 줍니다.
* 점진적 이동의 경우 이동 중에 "whoosh" 소리를 사용 하면 사용자가 개체를 추적 하는 데 도움이 됩니다.

**메시지 알림은** 종종 여러 번 들릴 수 있으며, 경우에 따라 빠르게 연속 해 서 발생할 수 있습니다. 이는 작동 하지 않는 것이 중요 합니다. 중간 범위의 긍정 색조 사운드는 여기에 적용 됩니다.

* 호출은 휴대폰 벨 소리와 비슷한 품질을 가져야 합니다. 이는 일반적으로 사용자가 호출에 대답할 때까지 재생 하는 반복 음악 문구입니다.
* 음성 통신 연결 및 연결 끊기에는 짧은 톤 소리가 있어야 합니다. 연결 소리에는 성공적인 연결을 나타내는 긍정 톤이 있어야 하 고, 연결 끊김 소리는 호출 완료를 나타내는 중립 소리 여야 합니다.

## <a name="spatialization"></a>Spatialization
Spatialization는 스테레오 헤드폰 또는 스피커를 사용 하 여 혼합 된 세계에 소리를 놓습니다.

### <a name="which-sounds-should-i-spatialize"></a>어떤 소리를 spatialize?
공간 위치가 있는 이벤트와 연결 된 경우에는 소리를 spatialized 해야 합니다. 여기에는 UI, 합의서 등 AI 음성 및 시각적 표시기가 포함 됩니다.

Spatializing **사용자 인터페이스** 요소를 사용 하면 잠긴 스테레오 사운드 수를 제한 하 여 사용자의 sonic "공간"을 혼잡 수 있습니다. 특히 직접 조작 상호 작용에서 오디오 피드백이 spatialized 때 터치, 잡기 및 해제가 더 자연스럽 게 됩니다. 그러나 이러한 요소의 거리 감쇠와 관련 하 여 아래를 참조 하십시오.

Spatializing **시각적 표시기** 와  **_합의서 등_ AI 음성** 은 사용자가 보기의 필드 외부에 있는 경우 사용자에 게 알려 줍니다.
    
이와 대조적으로 잘 정의 된 공간 위치가 없는  **_faceless_ AI 음성**및 기타 요소에 대 한 spatialization 방지 합니다. 관련 시각적 요소가 없는 Spatialization는 사용자가 찾을 수 없는 시각적 요소가 있다는 것을 방해 수 있습니다.

Spatialization를 추가 하면 몇 가지 CPU 비용이 발생 합니다. 대부분의 응용 프로그램은 동시에 두 개의 소리를 재생 합니다. 이 경우 spatialization 비용은 무시할 수 있습니다. MRTK 프레임 요금 모니터를 사용 하 여 spatialization를 추가할 때의 영향을 판단할 수 있습니다. 

### <a name="when-and-how-should-i-apply-distance-based-attenuation"></a>거리 기반 감쇠를 적용 하는 시기 및 방법
실제 세계에서 멀리 떨어져 있는 소리는 더 조용한 것입니다. 오디오 엔진은 원본 거리를 기준으로이 감쇠를 모델링할 수 있습니다. 관련 정보를 통신할 때 거리 기반 감쇠를 사용 합니다.

**시각적 표시기**, **애니메이션 holograms**및 기타 정보 사운드에 대 한 거리가 일반적으로 사용자와 관련이 있습니다. 거리 기반 감쇠를 사용 하 여 이러한 큐를 직관적으로 제공 합니다.
* 혼합 된 세계 공간의 크기에 맞게 각 원본에 대 한 감쇠 곡선을 조정 합니다. 오디오 엔진의 기본 곡선은 종종 매우 큰 (kilometer) 공간을 차지 합니다.

단추 및 기타 상호 작용 **의 점진적 단계** 를 강화 하는 소리는 감쇠를 적용 하지 않아야 합니다. 이러한 소리의 강화 효과는 일반적으로 단추에 대 한 거리를 전달 하는 것 보다 더 중요 합니다. 많은 단추 클릭이 연속적으로 들릴 때 특히 키보드를 사용 하면 변형이 혼란을 수 있습니다.

### <a name="which-spatialization-technology-should-i-use"></a>어떤 spatialization 기술을 사용 해야 하나요?
헤드폰 또는 HoloLens 스피커를 사용 하는 경우 HRTF (head 관련 전송 함수) 기반 spatialization 기술을 사용 합니다. 실제 세계의 헤드를 중심으로 하는 소리 전파를 모델링 합니다. 사운드 소스가 헤드의 한쪽 면에서 멀리 떨어져 있는 경우에도 약간의 감쇠 및 지연이 있는 거리가 먼 귀에 전파 됩니다. 이와 대조적으로 스피커 패닝은 감쇠만 사용 하 고 소리가 오른쪽에 있는 경우 왼쪽 귀에 전체 감쇠를 적용 하 고 그 반대의 경우도 마찬가지입니다. 이는 정상적인 청력 수신기에 불편 하 게 사용할 수 있으며 한 가지 귀에서 청각 장애가 있는 수신기에 액세스할 수 없습니다.

## <a name="next-steps"></a>다음 단계
* [Unity에서 공간 소리 사용](spatial-sound-in-unity.md)
* [Roboraid의 사례 연구](case-study-using-spatial-sound-in-roboraid.md)
* [HoloTour의 사례 연구](case-study-spatial-sound-design-for-holotour.md)

