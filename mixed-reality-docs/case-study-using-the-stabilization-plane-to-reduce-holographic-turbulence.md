---
title: 사례 연구-안정화 평면을 사용 하 여 holographic turbulence 줄이기
description: 안정화 평면을 사용 하 여 holographic turbulence 줄이기
author: bstrukus
ms.author: bestruku
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, holograms, 안정화, 사례 연구
ms.openlocfilehash: d31f3128ba10d6fc7bd57f3068db3dd16b23f901
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436438"
---
# <a name="case-study---using-the-stabilization-plane-to-reduce-holographic-turbulence"></a>사례 연구-안정화 평면을 사용 하 여 holographic turbulence 줄이기

Holograms를 사용 하는 것은 복잡할 수 있습니다. 공간을 이동 하 고 다른 모든 각도에서 holograms을 볼 수 있다는 사실은 일반적인 컴퓨터 화면으로 가져올 수 없는 집중 교육 수준을 제공 합니다. 이러한 holograms을 준비 하 고 현실적인 느낌은 Microsoft HoloLens 하드웨어와 holographic apps의 지능형 디자인 모두에서 수행 하는 기술 측면입니다.

## <a name="the-tech"></a>기술

실제로 공간을 공유 하는 것 처럼 holograms 표시 되도록 하려면 색 구분 없이 제대로 렌더링 해야 합니다. 이는 주로 [안정화 평면](hologram-stability.md#reprojection)을 호출 하는 항목에 holograms 고정 되도록 HoloLens 하드웨어에 기본 제공 되는 기술에 의해 이루어집니다.

평면은 point와 normal에서 정의 하지만 항상 평면에서 카메라를 가리키도록 하려고 하기 때문에 평면을 설정 하는 것이 중요 합니다. 모든 항목을 고정 하 고 안정적으로 유지 하기 위해 처리에 초점을 맞출 수 있도록 HoloLens를 지시할 수 있습니다. 그러나이 포커스 포인트를 설정 하는 방법은 앱에 따라 달라 지 며 콘텐츠에 따라 앱을 만들거나 중단할 수 있습니다.

간단히 말해서, 안정화 평면이 제대로 적용 되는 경우에는 holograms 가장 효과적 이지만 실제로는 생성 하는 응용 프로그램의 유형에 따라 달라 집니다. 현재 HoloLens에 사용할 수 있는 앱 중 일부를이 문제를 해결 하는 방법을 살펴보겠습니다.

## <a name="behind-the-scenes"></a>백그라운드 작업

다음 앱을 개발할 때 비행기를 사용 하지 않는 경우 개체가 sway로 이동 하면 개체가 sway가 되 고 빠른 헤드 또는 홀로그램 이동에 대 한 색 분리가 표시 되는 것을 알 수 있습니다. 개발 기간 동안, 안정화 평면을 가장 잘 활용 하는 방법과 해결할 수 없는 문제를 해결 하는 방법에 대 한 자세한 내용은 평가판 및 오류를 통해 배웠습니다.

### <a name="galaxy-explorer-stationary-content-3d-interactivity"></a>Galaxy 탐색기: 고정 콘텐츠, 3D 대화형

[Galaxy 탐색기](galaxy-explorer.md) 의 장면에는 두 가지 주요 요소가 있습니다. 즉, 두 가지 주요 요소가 있습니다. 안정화 논리의 경우 각 프레임에서 현재 응시 벡터가 교차 하는 것을 확인 하 여 지정 된 충돌 계층에서 어떤 것도 적중 되는지 확인 합니다. 이 경우 관심이 있는 계층은 행성 이므로, 응시가 전 세계에 있는 경우 안정화 평면이 배치 됩니다. 대상 충돌 계층의 어떤 개체도 적중 되지 않으면 앱은 보조 "plan B" 계층을 사용 합니다. 에서 gazed 되는 항목이 없는 경우 안정화 평면은 콘텐츠에서 gazing 때와 동일한 거리에 유지 됩니다. UI 도구는 전체 장면의 안정성을 가깝게 이동 하는 것을 발견 했으므로 평면 대상으로 남아 있습니다.

Galaxy 탐색기의 디자인은 작업을 안정적으로 유지 하 고 색 분리의 효과를 줄이는 데 적합 합니다. 사용자는 한 쪽에서 다른 쪽으로 이동 하는 대신 콘텐츠를 탐색 하 고 궤도로 전환 하는 것이 좋습니다 .이 경우 행성은 색 구분이 눈에 띄지 않을 만큼 orbiting. 또한 일정 한 60 FPS가 유지 되며이는 색 분리가 발생 하지 않도록 하는 긴 방법으로 진행 됩니다.

이를 직접 확인 하려면 [GitHub의 Galaxy 탐색기 코드](https://github.com/Microsoft/GalaxyExplorer/tree/master/Assets/Scripts/Utilities)에서 LSRPlaneModifier.cs 라는 파일을 찾습니다.

### <a name="holostudio-stationary-content-with-a-ui-focus"></a>HoloStudio: UI 포커스가 있는 고정 콘텐츠

HoloStudio에서 작업 하는 동일한 모델을 찾는 데 대부분의 시간을 사용 합니다. 새 도구를 선택 하거나 UI를 탐색 하려는 경우를 제외 하 고는 상당한 금액을 이동 하지 않습니다. 따라서 평면 설정 논리를 단순하게 유지할 수 있습니다. UI를 확인 하는 경우에는이 평면이 스냅 하는 모든 UI 요소에 평면을 설정 합니다. 모델을 볼 때 평면은 사용자와 모델 간의 기본 거리에 해당 하는 설정 거리 만큼 떨어져 있습니다.

![홈 단추의 사용자 gazes로 HoloStudio에서 시각화 된 안정화 평면](images/holostudio-stabilization-plane-500px.png)

### <a name="holotour-and-3d-viewer-stationary-content-with-animation-and-movies"></a>HoloTour 및 3D 뷰어: 애니메이션 및 동영상이 있는 고정 콘텐츠

HoloTour 및 3D 뷰어에서는 3D 효과가 있는 독립 애니메이션 개체 또는 동영상이 위에 추가 된 것을 볼 수 있습니다. 이러한 앱의 안정화는 현재 보고 있는 모든 사용자로 설정 됩니다.

또한 HoloTour는 고정 된 위치를 유지 하는 대신 이동 하 여 가상 세계의 straying를 방지할 수 있습니다. 이렇게 하면 안정성 문제가 발생 하기 위해 다른 holograms에서 멀리 떨어져 있을 수 있습니다.

![HoloTour의이 예제에서는 안정화 평면을 Hadrian의이 동영상으로 설정 합니다.](images/holotour-stabilization-plane-500px.jpg)

### <a name="roboraid-dynamic-content-and-environmental-interactions"></a>RoboRaid: 동적 콘텐츠 및 환경 상호 작용

RoboRaid에서 안정화 평면을 설정 하는 것은 가장 갑작스러운 이동이 필요한 앱 이지만 매우 간단 합니다. 평면은 벽 또는 주변 개체에 대 한 효과를 달성 하는 데 적합 하며, 멀리 떨어져 있을 때 그 앞의 고정 거리에 고정 됩니다.

RoboRaid는 안정화 평면을 염두에 두면 설계 되었습니다. Reticle를 가장 많이 이동 하는 것으로, 색 bleeding를 최소화 하는 빨강 및 파랑만 사용 하 여이를 우회 합니다. 또한 조각 사이에 약간의 깊이를 포함 하 여, 이미 예상 되는 시차 효과를 마스킹 하 여 발생 하는 색 도련을 최소화 합니다. 로봇은 신속 하 게 이동 하지 않고 정기적으로 짧은 거리 간격으로 이동 하지 않습니다. 기본적으로 안정화가 설정 되는 사용자의 앞에 2 미터를 유지 하는 경향이 있습니다.

### <a name="fragments-and-young-conker-dynamic-content-with-environmental-interaction"></a>조각 및 젊은 Conker: 환경 상호 작용을 포함 하는 동적 콘텐츠

Asobo Studio에서 작성 된 C++, 조각 및 젊은 Conker는 안정화 평면을 설정 하는 다른 방법을 사용 합니다. POI (관심 지점)는 코드에 정의 되 고 우선 순위를 기준으로 정렬 됩니다. Poi는 Conker 모델 (예: 젊은 Conker, 메뉴, 조 준 reticle 및 로고)입니다. Poi 사용자의 응시와 교차 하 고 평면이 가장 높은 개체의 중심으로 설정 됩니다. 교차가 발생 하지 않으면 평면이 기본 거리로 설정 됩니다.

조각 및 젊은 Conker 이전에 재생 공간으로 검색 된 항목을 벗어나 이동 하는 경우 앱을 일시 중지 하 여 holograms에서 너무 멀리 straying 합니다. 따라서 가장 안정적인 환경을 제공 하기 위해 찾은 경계 내에 유지 됩니다.

## <a name="do-it-yourself"></a>직접

HoloLens가 있는 경우 설명 된 개념을 사용 하 여 재생 하려는 경우 테스트 장면을 다운로드 하 고 아래 연습을 수행해 볼 수 있습니다. Unity의 기본 제공 gizmo API를 사용 하며 평면이 설정 되는 위치를 시각화 하는 데 도움이 됩니다. 이 코드는이 사례 연구에서 스크린샷 캡처에도 사용 되었습니다.
1. 최신 버전의 [MixedRealityToolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)를 동기화 합니다.
2. [HoloToolkit-Examples/유틸리티/장면/StabilizationPlaneSetting](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Utilities/Scenes/StabilizationPlaneSetting.unity) 장면을 엽니다.
3. 생성 된 프로젝트를 빌드하고 구성 합니다.
4. 장치에서를 실행 합니다.

### <a name="exercise-1"></a>연습 1

서로 다른 방향으로 여러 흰색 점이 표시 됩니다. 그 앞에는 서로 다른 깊이에 세 점이 표시 됩니다. 비행기를 탭 하 여 평면이 설정 된 점을 변경 합니다. 이 연습에서 다른 두 개의 경우에는 점에서 gazing 하는 동안 공간 주위의 이동 합니다. 왼쪽, 오른쪽, 위쪽 및 아래쪽으로 설정 합니다. 점에서 및 아버지 가까이로 이동 합니다. 안정화 평면이 다른 대상으로 설정 된 경우 어떻게 반응 하는지 확인 합니다.

### <a name="exercise-2"></a>연습 2

이제 두 개의 이동 점이 표시 될 때까지 오른쪽으로 이동 합니다. 하나는 수평 패스에서, 하나는 수직 패스에서 하나는 진동입니다. 다시 한 번 탭 하 여 평면이 설정 된 점을 변경 합니다. 평면에 연결 된 점에 색 분리가 어떻게 있으므로 안전성이 떨어질 표시 되는지 확인 합니다. 평면 설정 함수에서 도트의 속도를 사용 하려면 다시 탭 합니다. 이 매개 변수는 개체의 의도 된 동작에 대해 HoloLens에 대 한 힌트를 제공 합니다. 이를 사용 하는 시기를 알고 있어야 합니다. 즉, 한 점에서 속도가 사용 되는 경우 다른 이동 점으로는 더 큰 색 구분이 표시 됩니다. 응용 프로그램을 디자인할 때이 점을 염두에 두어야 합니다. 개체의 동작에 대해 긴밀 한 흐름을 유지 하면 아티팩트가 나타나지 않도록 방지할 수 있습니다.

### <a name="exercise-3"></a>연습 3

새 점 구성이 표시 될 때까지 한 번 더 사용 하세요. 이 경우 거리에 점이 있고 그 앞에 점 하나 spiraling 있습니다. 비행기를 탭 하 여 평면이 설정 된 점을 변경 하 고, 뒤쪽의 점과 동작의 점 사이를 교대로 이동 합니다. 평면 위치와 속도를 spiraling 도트의 수로 설정 하면 아티팩트가 어디에 나 표시 될 수 있습니다.

**팁**
* 평면 설정 논리를 간단 하 게 유지 합니다. 살펴본 바와 같이 복잡 한 평면 설정 알고리즘이 필요 하지 않습니다. 안정화 평면은 퍼즐의 한 부분입니다.
* 가능 하면 항상 대상 간 평면을 원활 하 게 이동 합니다. 멀리 떨어져 있는 대상을 즉시 전환 하면 장면이 시각적으로 중단 될 수 있습니다.
* 특정 대상에 잠금을 설정 하려면 평면 설정 논리에 옵션을 지정 하는 것이 좋습니다. 이렇게 하면 필요한 경우 로고 또는 제목 화면과 같은 개체에 평면을 잠글 수 있습니다.

## <a name="about-the-author"></a>작성자 정보

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Ben Strukus" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>이혜준 Strukus</b><br>소프트웨어 엔지니어 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>참고 항목
* [MR 기본 사항 100: Unity 시작](holograms-100.md)
* [Unity의 포커스 포인트](focus-point-in-unity.md)
* [홀로그램 안정성](hologram-stability.md)
