---
title: 혼합 현실 응용 프로그램에서 공간 소리 사용
description: 공간 사운드는 혼합 현실 응용 프로그램에서 집중 교육, 접근성 및 UX 디자인을 위한 강력한 도구입니다.
author: kegodin
ms.author: kegodin
ms.date: 11/02/2019
ms.topic: article
keywords: Windows Mixed Reality, 공간 소리, 디자인, 스타일
ms.openlocfilehash: 08844f6d837407d52ad2ab84b78440ce856151fc
ms.sourcegitcommit: b1ca4194eff452804ce5852208cce9815c6a4500
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80677988"
---
# <a name="how-to-use-sound-in-mixed-reality-applications"></a>혼합 현실 응용 프로그램에서 소리를 사용 하는 방법

소리를 사용 하 여 사용자의 응용 프로그램 상태 모델을 알리고 멘 탈 수 있습니다. 적절 한 경우 spatialization를 사용 하 여 혼합 현실 환경에 소리를 넣습니다. 이러한 방식으로 청각 및 시각적 개체를 연결 하면 활용의 직관적인 특성을 사용 하 여 사용자 신뢰도를 높일 수 있습니다.
<br><br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="when-to-add-sounds"></a>소리를 추가 하는 경우
혼합 현실 응용 프로그램은 종종 tactile 인터페이스가 없기 때문에 2D 앱 보다 사운드가 더 많이 필요 합니다. 사용자에 게 알리거나 상호 작용을 강화할 때 소리를 추가 합니다.

### <a name="inform-and-reinforce"></a>알림 및 보강
* 알림과 같이 사용자가 시작 하지 않은 이벤트의 경우에는 소리를 사용 하 여 사용자에 게 변경이 발생 했음을 알립니다.
* 상호 작용에는 여러 단계가 있을 수 있습니다. 소리를 사용 하 여 단계 전환을 보강 합니다.

상호 작용, 이벤트 및 제안 된 소리 특성의 다음 예를 참조 하세요.

### <a name="exercise-restraint"></a>운동 지지대
사용자는 오디오 정보에 무제한의 용량을가지고 있지 않습니다.
* 각 사운드는 특정 한 중요 한 정보를 전달 해야 합니다.
* 앱이 사용자에 게 알리는 소리를 재생 하는 경우 다른 소리의 볼륨을 일시적으로 줄입니다.
* 단추 가리키기 소리 (다음 정보 참조)의 경우 과도 한 소리 트리거를 방지 하는 시간 지연을 추가 합니다.

### <a name="dont-rely-solely-on-sounds"></a>소리만 사용 하지 않음
사용 되는 소리는 사용자에 게 유용 합니다. 그러나 소리가 꺼진 상태 에서도 응용 프로그램을 사용할 수 있는지 확인 합니다.
* 사용자가 청각 장애가 있을 수 있습니다.
* 응용 프로그램은 큰 환경에서 사용할 수 있습니다.
* 사용자에 게 장치 오디오를 사용 하지 않도록 설정 하는 개인 정보 문제나 기타 이유가 있을 수 있습니다.

## <a name="how-to-sonify-interactions"></a>Sonify 상호 작용 방법
혼합 현실의 상호 작용 형식에는 제스처, 직접 조작 및 음성이 포함 됩니다. 이러한 상호 작용의 소리를 선택 하거나 디자인 하려면 다음의 제안 된 특성을 사용 합니다.

### <a name="gesture-interactions"></a>제스처 상호 작용
혼합 현실에서 사용자는 마우스를 사용 하 여 단추와 상호 작용할 수 있습니다. 단추 동작은 일반적으로 사용자가 상호 작용을 취소할 수 있도록 단추를 누르는 대신를 해제할 때 발생 합니다. 이러한 단계를 보강 하려면 소리를 사용 합니다. 멀리 떨어져 있는 단추를 대상으로 하는 사용자를 지원 하기 위해 포인터 가리키기 소리를 사용 하는 것도 고려 합니다.
* 단추 누르기 소리는 짧게 tactile "클릭" 해야 합니다.<br/>예: [MRTK_ButtonPress .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* 단추-"unpress" 소리는 유사한 tactile 느낌을 가져야 합니다. 누르기 소리 보다 더 높은 피치는 완료 강화 의미입니다.<br/>예: [MRTK_ButtonUnpress .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonUnpress.wav)
* 가리키기 소리의 경우 낮은 빈도 thud 또는 범프와 같이 약한 및 비 위협 사운드를 사용 하는 것이 좋습니다.

### <a name="direct-manipulation"></a>직접 조작
HoloLens 2에서는 두 부분으로 된 사용자 인터페이스 요소에 대 한 직접 조작을 지원 합니다. 다른 물리적 피드백이 없으면 소리가 중요 합니다.

사용자가 키 스트로크의 아래쪽에 도달할 때 다른 표시를 받지 않기 때문에 직접 조작에서 *단추 누르기* 소리가 중요 합니다. 주요 여행에 대 한 소리 표시기는 작은, 미묘한 및 폐색 수 있습니다. 제스처 상호 작용을 사용 하는 것 처럼 단추 누름은 클릭 처럼 짧은 tactile 소리를 표시 합니다. 누름은 비슷한 클릭 소리를 포함 하지만 볼록 피치를 사용 해야 합니다.
* 예: [MRTK_ButtonPress .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* 예: [MRTK_ButtonUnpress .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonUnpress.wav)

잡기 또는 릴리스 작업을 시각적으로 확인 하는 것은 어렵습니다. 사용자 손을 시각적 효과를 사용 하는 경우가 많으며, 하드 수준 있는 개체는 실제 시각적으로 "점령"를 사용 하지 않습니다. 소리는 성공적인 잡기와 릴리스 상호 작용을 효과적으로 전달할 수 있습니다.
* 잡기 작업에는 개체 주위에 손가락을 muffled 하는 것을 evokes 하는 짧고 약간의 tactile 사운드가 있어야 합니다. 경우에 따라 손으로 이동 하는 소리를 전달 하는 "whoosh" 사운드도 있습니다.<br/>예: [MRTK_Move_Start .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_Move_Start.wav)
* 릴리스 작업은 비슷하게 짧고 tactile 소리를 가져와야 합니다. 일반적으로는 영향을 받는 것이 고, 그 다음에는 개체의 정착를 전달 하는 "whoosh"를 사용 하 여 광고 소리와 역순으로 낮은 고주파음입니다.<br/>예: [MRTK_Move_End .wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_Move_End.wav)

*그리기* 상호 작용은 사용자 손을 이동 하 여 볼륨을 결정 하는 지속적인 반복 소리를 가져와야 합니다. 사용자의 손을 loudest 하 고 손을 빠르게 이동 하는 경우에는 자동으로 진행 해야 합니다.

### <a name="voice-interactions"></a>음성 상호 작용
음성 상호 작용에는 종종 미묘한 시각적 요소가 있습니다. 소리를 사용 하 여 상호 작용 단계를 보강 합니다. 더 많은 톤 소리를 사용 하 여 제스처와 직접 조작 소리를 구분할 수 있습니다.

* 음성 *명령 확인*에는 양수의 톤을 사용 합니다. 증가 하는 톤 및 주요 음악 간격은 효과적입니다.
* 음성 명령 *실패*에 대해 더 짧고 작은 음이 음을 사용 합니다. 음이 음을 방지 합니다. 대신 더 percussive 중립적인 소리를 사용 하 여 응용 프로그램이 상호 작용에서 이동 하 고 있음을 통신 합니다.
* 응용 프로그램에 절전 모드 해제 단어가 있는 경우 장치가 *수신 대기를 시작할*때 짧은 gentle 톤을 사용 합니다. 응용 프로그램이 수신 대기 *하는 동안* 미묘한 루핑 소리를 사용 합니다.

### <a name="notifications"></a>알림
알림은 응용 프로그램 상태 변경 내용 및 사용자가 시작 하지 않은 기타 이벤트 (예: 프로세스 완료, 메시지, 전화 통화)를 전달 합니다.

혼합 현실에서 개체는 사용자의 뷰 필드에서 이동 하기도 합니다. 개체 유형과 동작 속도에 따라 달라 지는 *애니메이션 개체* 를 spatialized 소리와 함께 이동 합니다.
* 애니메이션의 끝에서 spatialized 소리를 재생 하 여 개체의 새 위치를 사용자에 게 알리는 데 도움이 됩니다.
* 점진적 이동의 경우 이동 중에 "whoosh" 소리가 있으면 사용자가 개체를 추적할 수 있습니다.

*메시지 알림* 경고음은 반복적으로 빠르게 들릴 수 있습니다. 이러한 기능을 작동 하지 않는 것이 중요 합니다. 중간 범위의 포지티브 톤 소리가 적용 됩니다.

* 들어오는 통화 사운드는 휴대폰 벨 소리와 비슷한 품질을 가져야 합니다. 일반적으로 사용자가 호출에 응답할 때까지 재생 하는 루핑 음악 문구입니다.
* 음성 통신 연결 및 연결 끊기에는 짧은 톤 소리가 있어야 합니다. 연결 소리는 성공적인 연결을 나타내는 양수입니다. 연결 끊기 소리는 호출 완료를 나타내는 중립 소리 여야 합니다.

## <a name="handle-spatialization"></a>Spatialization 처리
Spatialization는 스테레오 헤드폰이 나 스피커를 사용 하 여 혼합 현실 환경에 소리를 놓습니다.

### <a name="which-sounds-to-spatialize"></a>Spatialize에 대 한 소리
공간 위치가 있는 이벤트와 연결 된 경우에는 소리를 spatialized 해야 합니다. 여기에는 UI, 합의서 등 AI 음성 및 시각적 표시기가 포함 됩니다.

Spatialize *사용자 인터페이스* 요소를 사용 하 여 사용자의 sonic의 수를 제한 함으로써 사용자의 sonic "공간"을 혼잡 수 있습니다. 오디오 피드백이 spatialized 면 터치, 잡기 및 해제와 같은 조작 상호 작용을 보다 자연스럽 게 느낄 수 있습니다. 이러한 요소의 거리 감쇠에 대 한 다음 정보를 고려 하십시오.

*시각적 표시기* 와 *합의서 등 AI 음성을* Spatialize 사용자에 게 보기의 필드 외부에 있는 경우 사용자에 게 알려 줍니다.
    
반면, *FACELESS AI 음성* 및 잘 정의 된 공간 위치가 없는 기타 요소에 대 한 spatialization을 방지 합니다. 관련 시각적 요소가 없는 Spatialization는 사용자가 찾을 수 없는 시각적 요소가 있다는 것을 방해 수 있습니다.

Spatialization에는 몇 가지 CPU 비용이 포함 됩니다. 많은 응용 프로그램에서 동시에 두 개의 사운드가 재생 됩니다. 이 경우 spatialization 비용은 무시할 수 있습니다. MRTK 프레임 요금 모니터를 사용 하 여 spatialization를 추가할 때의 영향을 판단할 수 있습니다.

### <a name="when-and-how-to-apply-distance-based-attenuation"></a>거리 기반 감쇠 적용 시기 및 방법
실제 세계에서 멀리 떨어져 있는 소리는 더 조용한 것입니다. 오디오 엔진은 원본 거리를 기준으로이 감쇠를 모델링할 수 있습니다. 관련 정보를 통신할 때 거리 기반 감쇠를 사용 합니다.

*시각적 표시기*, *애니메이션 holograms*및 기타 정보 사운드에 대 한 거리가 일반적으로 사용자와 관련이 있습니다. 거리 기반 감쇠를 사용 하 여 큐를 직관적으로 제공 합니다.

각 원본에 대 한 감쇠 곡선을 혼합 현실 세계 공간의 크기에 맞게 조정 합니다. 오디오 엔진의 기본 곡선은 종종 매우 큰 (kilometer) 공간을 차지 합니다.

단추 작업 및 기타 상호 작용 *의 점진적 단계* 를 보강 하는 소리는 감쇠를 적용 하지 않아야 합니다. 이러한 소리의 강화 효과는 일반적으로 단추에 대 한 거리를 전달 하는 것 보다 더 중요 합니다. 많은 단추 클릭을 연속 해 서 사용할 수 있는 경우 특히 키보드를 사용 하면 변형이 혼란을 수 있습니다.

### <a name="which-spatialization-technology-to-use"></a>사용할 spatialization 기술
헤드폰 또는 HoloLens 스피커를 사용 하는 경우 HRTF (head 관련 전송 함수) 기반 spatialization 기술을 사용 합니다. 이러한 기술은 실제 세계의 헤드를 중심으로 하는 소리 전파를 모델링 합니다. 사운드 소스가 한 헤드의 먼 쪽에 있는 경우에도 소리는 감쇠 및 지연이 발생 하 여 먼 귀에 전파 됩니다. 이와 반대로 스피커 패닝은 감쇠만 사용 하 고 소리가 오른쪽에 있는 경우 왼쪽 귀에 전체 감쇠를 적용 합니다 (그 반대의 경우). 이 기술은 "정상적인 청각" 수신기가 될 수 있으며 한 가지 귀에서 청각 장애가 있는 수신기에 액세스할 수 없게 됩니다.

## <a name="next-steps"></a>다음 단계
* [Unity에서 공간 소리 사용](spatial-sound-in-unity.md)
* [Roboraid의 사례 연구](case-study-using-spatial-sound-in-roboraid.md)
* [HoloTour의 사례 연구](case-study-spatial-sound-design-for-holotour.md)
