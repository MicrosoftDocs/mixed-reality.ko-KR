---
title: 사례 연구-holographic 분야의 난 기류를 줄이기 위해 안정화 평면 사용
description: 안정화 평면 holographic 분야의 난 기류 줄이기 위해 사용 하 여
author: bstrukus
ms.author: bestruku
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality를 홀로그램, 안정화, 사례 연구
ms.openlocfilehash: a084ede5f9bf3d5f058cc81ec75840e2c2e75af2
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597530"
---
# <a name="case-study---using-the-stabilization-plane-to-reduce-holographic-turbulence"></a>사례 연구-holographic 분야의 난 기류를 줄이기 위해 안정화 평면 사용

제공 된 작업은 까다로울 수 있습니다. 공간에 이동 하 고 모든 다른 각도에서 프로그램 홀로그램 참조 수 한다는 사실 두 가지 수준의 일반 컴퓨터 화면으로 가져올 수 없습니다. 집중 교육을 제공 합니다. 이러한 홀로그램 위치에 유지 하 고 현실적인 찾고는 Microsoft HoloLens 하드웨어와 holographic 앱의 지능형 디자인 하면 기술 어쨌든 뛰어난 기술입니다.

## <a name="the-tech"></a>기술 지원 담당자

홀로그램와 실제로 공간을 공유 하는 것 처럼 표시 되도록 해야 렌더링 제대로 색 구분이 없는 합니다. 이렇게, 부분적으로 기술 홀로그램 부르는에 고정을 유지 하는 HoloLens 하드웨어에 기본 제공 되는 [안정화 평면](hologram-stability.md#stabilization-plane)합니다.

평면 지점과 정상적인 정의한 없지만 카메라 면 평면 항상 것 이므로 실제로 고려해 평면의 지점 설정. 처리 모든 고정 유지에 집중 하는 HoloLens 지시 하 고 안정적이 고 수 있지만이 포커스 지점을 설정 하는 방법을 앱 별 및 수 확인 나 내용에 따라 앱이 중단 합니다.

홀로그램 최상의 경우에 작동 하는 간단히 말해 안정화 평면 제대로 적용 되지만 의미 만들 응용 프로그램의 유형에 따라 달라 지는 실제로 어떤 합니다. 이 문제를 해결할 HoloLens에 대 한 현재 사용할 수 있는 앱 중 일부는 방법에 대해 살펴보겠습니다.

## <a name="behind-the-scenes"></a>백그라운드 작업

다음 앱을 개발할 때는 평면 사용 하지 않은 경우 개체는 sway 이동이 고 빠른 head 또는 홀로그램 이동을 사용 하 여 색 구분 보면 있음을 확인 했습니다. 개발 기간에 걸쳐 알게 시행 착오를 통해 가장 안정화 평면을 사용 하는 방법 및이 문제를 해결할 수 없는 앱을 디자인 하는 방법입니다.

### <a name="galaxy-explorer-stationary-content-3d-interactivity"></a>Galaxy 탐색기: 고정 콘텐츠를 3D 대화형 작업

[Galaxy 탐색기](galaxy-explorer.md) 장면에 두 개의 주요 요소가 있습니다. 천체 콘텐츠 및 작은 UI 도구 모음에 응시 뒤에 오는 기본 뷰. 안정화 논리에 대 한 지정 된 충돌 계층에서 아무 것도 도달할 경우를 확인 하려면 각 프레임에 현재 게이즈 벡터에 새로운 교차 살펴봅니다. 이 경우에 관심이 계층은 행성, 하므로 프로그램 게이즈를 전 세계에서 떨어지면 안정화 평면에 표시 됩니다. 충돌 대상 계층에서 개체를 적중 하는 경우 앱 보조 "B"계획 계층을 사용 합니다. Nothing에서 gazed 되는, 하는 경우 안정화 평면 내용을 gazing 때와 같은 거리에 유지 됩니다. UI 도구 남아 평면 대상으로 거의 간의 점프를 찾을 것와 전체 장면의 안정성을 훨씬 감소 합니다.

Galaxy 탐색기의 디자인 작업을 안정적으로 유지 하 고 색 구분에 영향을 줄이기에 적합 합니다. 경비원 및 콘텐츠 궤도 보다는 측면에서 그를 따라 이동이 하 고는 색 구분 없습니다 눈에 띄는 행성 있을 정도로 느리게 행성 합니다. 또한 상수 60FPS는 유지 하는 작업이 매우에서 색 구분을 방지 합니다.

이 직접 확인 하려면에서 LSRPlaneModifier.cs 이라는 파일을 찾습니다 합니다 [GitHub의 Galaxy 탐색기 코드](https://github.com/Microsoft/GalaxyExplorer/tree/master/Assets/Scripts/Utilities)합니다.

### <a name="holostudio-stationary-content-with-a-ui-focus"></a>HoloStudio: UI 포커스를 사용 하 여 고정 콘텐츠

HoloStudio에서 대부분의 작업 중인 동일한 모델을 살펴보면 시간 투자 합니다. 새 도구를 선택 하거나 평면 설정 논리 간단한 수 유지 하므로 UI를 탐색할 때에 응시 제외 하 고는 상당한 양의 이동 하지 않습니다. UI를 볼 때 평면에 응시 스냅 모든 UI 요소에 설정 됩니다. 모델을 살펴보면 평면 때 설정 된 거리 만큼 떨어진, 및 모델 사이의 기본 거리를 사용 하 여 해당 합니다.

![안정화 평면에서 시각화는 사용자와 HoloStudio gazes 홈 단추](images/holostudio-stabilization-plane-500px.png)

### <a name="holotour-and-3d-viewer-stationary-content-with-animation-and-movies"></a>HoloTour 및 3D 뷰어: 애니메이션 및 동영상을 사용 하 여 고정 콘텐츠

HoloTour 및 3D 뷰어 살펴보려면 독립 애니메이션이 적용 된 개체 또는 동영상에서 그 위에 추가 하는 3D 효과 사용 하 여 합니다. 이러한 앱에 안정화 무엇이 든 현재 보고 있는로 설정 됩니다.

HoloTour도 방지 고정된 위치에 머무르지 않고를 이동 하 여 가상 사용자가 속한 환경에서 너무 멀리 떨어져 straying에서. 이렇게 하면 멀리 떨어져 서서히 생겨날 안정성 문제에 대 한 다른 홀로그램 얻을 수 없습니다.

![이 예에서 HoloTour에서 안정화 평면 하드리아누스의 Pantheon의이 동영상에 설정 됩니다.](images/holotour-stabilization-plane-500px.jpg)

### <a name="roboraid-dynamic-content-and-environmental-interactions"></a>RoboRaid: 동적 콘텐츠 및 환경 상호 작용

안정화 평면 RoboRaid에서 설정 하는 것은 가장 갑작스러운 움직임에 필요한 앱 불구 하 고 매우 간단 합니다. 평면 벽을 집중적으로 맞춰 조정 됩니다 또는 주변 개체에서 멀리 떨어져 하는 경우는 사용자 앞에 고정된 된 거리 만큼 떨어진 float 됩니다.

RoboRaid는 안정화 평면 염두에서에 두고 설계 되었습니다. 헤드 잠긴 이므로 가장을 이동, 십자선, 빨강 및 파랑 색 bleeding 모든을 최소화 하는 사용 하 여이 우회 합니다. 또한 소규모의 깊이 조각에는 이미 필요한 시차 효과 사용 하 여 가장 하 여 발생 하는 모든 색 화상 물림 재단 최소화 사이의 비트를 포함 합니다. 로봇은 매우 신속 하 게 이동 하 고만 정기적으로 짧은 거리를 이동 하지 않습니다. 안정화는 기본적으로 설정 되어 있는 사용자 앞에 약 2 미터 유지 경향이 있습니다.

### <a name="fragments-and-young-conker-dynamic-content-with-environmental-interaction"></a>조각 및 젊은 Conker: 환경 상호 작용을 통해 동적 콘텐츠

Asobo Studio 저술한 C++, 조각 및 Young Conker 안정화 평면 설정과 다른 방법을 사용 합니다. 지점 (POI) 관심 코드에 정의 되 고 우선 순위를 기준으로 정렬 합니다. Poi로 향하는 Young Conker, 메뉴, 조 십자선 및 로고 Conker 모델과 같은 게임의 콘텐츠입니다. poi로 향하는 교차 되는 사용자의 게이즈 및 평면 가장 높은 우선 순위를 사용 하 여 개체의 가운데에 설정 됩니다. 겹치는 경우 평면 거리를 기본 설정 됩니다.

조각 및 Young Conker와 관련해 서는 홀로그램에서 외부 항목은 이전에 검색, play 공간으로 이동 하는 경우 앱을 일시 중지 하 여 너무 멀어서 straying 디자인할 수도 있습니다. 이와 같이 유지 하면 가장 안정적인 환경을 제공 하기 위해 발견 되는 경계 내에서.

## <a name="do-it-yourself"></a>사용자가 직접 수행

HoloLens 있고 지금까지 설명한 개념을 이리저리 조정 하려는 경우 테스트 장면을 다운로드 하 고 아래 연습을 사용해 수 있습니다. Unity의 기본 제공 gizmo API 사용 하며에 평면을 설정할 시각화 하는 데 도움이 됩니다. 이 코드는이 사례 연구에서 스크린 샷 캡처를 에서도 사용 되었습니다.
1. 최신 버전의 동기화 [MixedRealityToolkit Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)합니다.
2. 엽니다는 [HoloToolkit-Examples/Utilities/Scenes/StabilizationPlaneSetting.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Utilities/Scenes/StabilizationPlaneSetting.unity) 장면입니다.
3. 빌드 및 생성된 된 프로젝트를 구성 합니다.
4. 장치에서 실행 합니다.

### <a name="exercise-1"></a>연습 1

다른 방향에서와 관련해 서 여러 흰색 점을 볼 수 있습니다. 사용자 앞에 다른 깊이에 있는 세 점을 볼 수 있습니다. 평면을 점 하는 변경에 어 탭으로 설정 됩니다. 이 연습에서는 다른 두 개의 점이 있는 gazing 하는 동안 주위 공간에 이동 합니다. Up 및 down 헤드에 왼쪽된에서 오른쪽으로 설정 합니다. 에 가까울수록 서로 father 라고 점에서 이동 합니다. 안정화 평면 다양 한 대상으로 설정 된 경우 대응 방법을 참조 하세요.

### <a name="exercise-2"></a>연습 2

이제 경로 가로 및 세로 경로 진동 하나 두 개의 이동 점 표시 될 때까지 오른쪽에 설정 합니다. 이번에 어 탭 하 평면으로 설정 되어 있는 점 변경 합니다. 평면에 연결 된 점에 색 구분은 떨어질 어떻게 알림이 나타납니다. 평면 설정 함수에서 점의 속도 사용 하려면 다시 탭 합니다. 이 매개 변수 개체의 의도 한 동작에 대 한 HoloLens에 힌트를 제공합니다. 반드시 알아야이 사용 하는 경우 속도 한 점을 사용 하는 경우 만들어진 다른 이동 점이 큰 색 구분 표시 됩니다. 앱을 디자인할 때이 점을 명심-개체의 동작에 통합 된 흐름이 있는 방지할 수 있습니다 아티팩트를 표시 합니다.

### <a name="exercise-3"></a>연습 3

설정에 오른쪽에 한 번 더 점의 새 구성을 표시 될 때까지 합니다. 이 경우 거리의 점과 앞에 입출력 스파이럴 한 점이 됩니다. 어 탭을 교대로 반복 되는 동작에서 점 뒤에 점 사이의 평면으로 설정 되어 있는 점을 변경 합니다. Spiraling 점를 평면 위치 및 속도 설정 하 모든 범위를 표시 하는 아티팩트를 사용 하는 방법 확인 합니다.

**팁**
* 평면 설정 논리를 단순하게 유지 합니다. 지금까지 살펴본 대로 몰입 형 환경을 확인 하는 복합 평면의 설정을 알고리즘 필요가 없습니다. 안정화 평면은 하나의 조각 퍼즐입니다.
* 시 모든 가능한 경우 항상 평면을 이동 대상 간에 원활 하 게 합니다. 즉시 먼 대상 전환 장면 시각적으로 중단 될 수 있습니다.
* 매우 구체적인 목표가 고정 하기 위한 평면 설정 논리에 옵션을 포함 하는 것이 좋습니다. 이런 방식으로 필요한 경우 평면 로고 또는 제목 화면 등의 개체에 잠겨 있을 수 있습니다.

## <a name="about-the-author"></a>저자 소개

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Ben Strukus" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Ben Strukus</b><br>소프트웨어 엔지니어 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>참조
* [MR Basics 100: Unity를 사용 하 여 시작](holograms-100.md)
* [Unity의 포커스 지점](focus-point-in-unity.md)
* [홀로그램 안정성](hologram-stability.md)
