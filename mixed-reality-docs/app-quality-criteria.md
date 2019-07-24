---
title: 앱 품질 기준
description: 이 문서에서는 혼합 현실 앱의 품질에 영향을 주는 주요 요소에 대해 설명 합니다.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: 앱 품질 기준, 혼합 현실, 혼합 현실 앱
ms.openlocfilehash: 8e635585c0981d81bf71fb5577232af28f2a0fdd
ms.sourcegitcommit: 150d258a23130026c8792da383a3993657841fb4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67024488"
---
# <a name="app-quality-criteria"></a>앱 품질 기준

이 문서에서는 혼합 현실 앱의 품질에 영향을 주는 주요 요소에 대해 설명 합니다. 각 요소에 대해 다음 정보가 제공 됩니다.
* 개요 – 품질 요소에 대 한 간단한 설명 및 중요 한 이유입니다.
* 장치 영향-영향을 받는 창 혼합 현실 장치의 유형입니다.
* 품질 기준 – 품질 요소를 평가 하는 방법입니다.
* 방법 측정 – 문제를 측정 (또는 경험) 하는 방법
* 권장 사항 – 더 나은 사용자 환경을 제공 하는 방법에 대 한 요약입니다.
* 리소스-더 나은 앱 환경을 만드는 데 유용한 개발자 및 디자인 리소스입니다.

## <a name="frame-rate"></a>프레임 속도

프레임 요금은 홀로그램 안정성 및 사용자 편안의 첫 번째 기둥입니다. 권장 되는 목표 보다 낮은 프레임 속도로 holograms 표시 되 고 경험 believability에 부정적인 영향을 미치고 잠재적으로 눈 피로를 일으킬 수 있습니다. Windows Mixed Reality 몰입 형 헤드셋의 사용자 환경에 대 한 대상 프레임 요금은 지원 하려는 Windows 혼합 현실 호환 Pc에 따라 60Hz 또는 90Hz가 됩니다. HoloLens의 경우 대상 프레임 률은 60Hz입니다.

### <a name="device-impact"></a>장치 영향

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>품질 기준

|  최상위  |  평가 |  통과 |
--- | --- | ---
| 앱은 대상 장치의 FPS (초당 프레임 수) 목표를 만족 합니다. HoloLens의 60fps; 울트라 Pc의 90fps 및 기본 Pc의 60fps | 앱은 코어 환경을 방해할 하지 않는 간헐적 프레임 삭제를 포함 합니다. 또는 FPS는 원하는 목표 보다 지속적으로 낮지만 앱 환경을 방해 하지 않습니다. | 앱이 10 초 이내에 평균적으로 프레임 속도로 놓기가 발생 합니다. |

### <a name="how-to-measure"></a>측정 방법

* 실시간 프레임 속도 그래프는 [Windows 장치 포털](using-the-windows-device-portal.md#system-performance) 의 "시스템 성능"에서 제공 됩니다.
* 개발 디버깅을 위해 앱에 프레임 주기 진단 카운터를 추가 합니다. 샘플 카운터에 대 한 리소스를 참조 하세요.
* 앱이 실행 되는 동안 한 쪽에서 쪽으로 이동 하 여 프레임 속도로 떨어질 수 있습니다. 홀로그램에 예기치 않은 떨림 이동이 표시 되 면 프레임 속도가 낮거나 안정성 평면이 원인일 가능성이 높습니다.

### <a name="recommendations"></a>권장 사항

* 개발 작업을 시작할 때 프레임 속도 카운터를 추가 합니다.
* 프레임 속도로 놓기가 발생 하는 변경 내용을 평가 하 고 성능 버그로 적절 하 게 해결 해야 합니다.

### <a name="resources"></a>리소스

#### <a name="documentation"></a>설명서

* [혼합 현실 성능 이해](understanding-performance-for-mixed-reality.md)
* [홀로그램 안정성 및 프레임 속도](hologram-stability.md#frame-rate)
* [Asset performance 예산](asset-creation-process.md)
* [Unity의 권장 성능](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a>도구 및 자습서

* [MRToolkit, FPS 카운터 표시](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [MRToolkit, 셰이더](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a>외부 참조

* [Unity, 모바일 응용 프로그램 최적화](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a>홀로그램 안정성

안정적인 holograms는 앱의 유용성 및 believability을 높이고 사용자에 게 더 편안한 보기 환경을 만듭니다. 홀로그램 안정성의 품질은 좋은 앱 개발과 장치에서 환경을 이해 (추적) 하는 기능으로 인해 발생 합니다. 프레임 요금은 안정성의 첫 번째 기둥 이지만 다음을 비롯 한 다른 요인이 안정성에 영향을 줄 수 있습니다.

* 안정화 평면 사용
* 공간 앵커에 대 한 거리
* 추적

### <a name="device-impact"></a>장치 영향

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>품질 기준

|  최상위  |  평가 |  통과 |
--- | --- | ---
|  Holograms 지속적으로 안정적으로 표시 됩니다. | 보조 콘텐츠가 예기치 않은 움직임을 보여 주는 경우 또는 예기치 않은 이동으로 전체 앱 환경을 방해 하지 않습니다. | 프레임의 기본 콘텐츠는 예기치 않은 움직임을 보여 주는 것입니다. |

### <a name="how-to-measure"></a>측정 방법

장치를 입고 하 고 환경을 확인 하는 동안 다음을 수행 합니다.

* Holograms가 예기치 않은 움직임을 표시 하는 경우, 낮은 프레임 속도가 나 초점면에 대 한 안정성 평면의 부적절 한 맞춤이 원인일 경우 면에서 쪽으로 이동 합니다.
* Holograms 및 환경을 중심으로 이동 하 여 스윔 및 jumpiness와 같은 동작을 찾습니다. 이 유형의 동작은 장치에서 환경을 추적 하지 않거나 공간 앵커에 대 한 거리를 발생 시킬 수 있습니다.
* 프레임에 큰 holograms 여러 개 있는 경우 다양 한 수준에서 홀로그램 동작을 관찰 하 여 헤드 위치를 측면에서 쪽으로 이동 합니다. shakiness가 표시 되 면 안정화 평면으로 인해 발생할 수 있습니다.

### <a name="recomendations"></a>권장 사항

* 개발 작업을 시작할 때 프레임 속도 카운터를 추가 합니다.
* 안정화 평면을 사용 합니다.
* 항상 앵커의 3 미터 내에 고정 된 holograms을 렌더링 합니다.
* 적절 한 추적을 위해 환경이 설정 되어 있는지 확인 합니다.
* 프레임 내에서 다양 한 초점면 수준에서 holograms을 방지 하기 위해 환경을 디자인 합니다.

### <a name="resources"></a>리소스

#### <a name="documentation"></a>설명서

* [홀로그램 안정성 및 프레임 속도](hologram-stability.md#frame-rate)
* [사례 연구, 안정화 평면 사용](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [혼합 현실 성능 이해](understanding-performance-for-mixed-reality.md)
* [Unity의 권장 성능](performance-recommendations-for-unity.md)
* [공간 앵커](spatial-anchors.md)
* [추적 오류 처리](coordinate-systems.md#handling-tracking-errors)
* [고정 참조 프레임](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a>도구 및 자습서

* [MR 부록 키트, Kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a>실제 표면의 Holograms 위치

물리적 개체가 있는 holograms의 잘못 된 맞춤 (서로 관련 된 경우)은 holograms와 실제 세계의 비 합집합을 명확 하 게 나타냅니다. 배치의 정확도는 시나리오의 요구 사항에 상대적 이어야 합니다. 예를 들어 일반 표면 배치에서는 공간 맵을 사용할 수 있지만 더 정확한 배치에서는 표식 및 보정을 사용 해야 합니다.

### <a name="device-impact"></a>장치 영향

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>품질 기준

|  최상위  |  평가 |  통과 |
--- | --- | ---
| Holograms는 일반적으로 센티미터에서 인치 범위의 표면에 맞춥니다. 더 많은 정확도가 필요한 경우 앱은 원하는 앱 사양 내에서 공동 작업을 위한 효율적인 수단을 제공 해야 합니다. | NA | Holograms 화면 평면을 분리 하거나 화면에서 부동 상태로 표시 하 여 실제 대상 개체와 정렬 되지 않은 상태로 표시 됩니다. 정확도가 필요한 경우 Holograms는 시나리오의 근접 사양을 충족 해야 합니다. | 

### <a name="how-to-measure"></a>측정 방법

* 공간 맵에 배치 된 Holograms는 화면 위 또는 아래에 크게 부동 상태로 표시 되어서는 안 됩니다.
* 정확한 배치가 필요한 Holograms에는 시나리오 요구 사항에 맞는 일종의 표식 및 보정 시스템이 있어야 합니다.

### <a name="recommendations"></a>권장 사항

* 공간 맵은 전체 자릿수가 필요 하지 않은 경우 화면에 개체를 배치 하는 데 유용 합니다.
* 최상의 정밀도를 위해 마커 또는 포스터를 사용 하 여 최종 보정에 대 한 holograms 및 Xbox 컨트롤러 (또는 일부 수동 맞춤 메커니즘)를 설정 합니다.
* 매우 큰 holograms을 논리적 부분으로 분리 하 고 각 부분을 표면에 정렬 하는 것이 좋습니다.
* IPD (interpupilary distance)를 잘못 설정 하면 홀로그램 맞춤에도 영향을 미칠 수 있습니다. 항상 사용자의 IPD으로 HoloLens를 구성 합니다.

### <a name="resources"></a>리소스

#### <a name="documentation"></a>설명서

* [공간 매핑 배치](spatial-mapping.md#placement)
* [대화방 스캔 프로세스](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [공간 앵커 모범 사례](spatial-anchors.md#best-practices)
* [추적 오류 처리](coordinate-systems.md#handling-tracking-errors)
* [Unity의 공간 매핑](spatial-mapping-in-unity.md)
* [Vuforia 개발 개요](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a>도구 및 자습서

* [MR 공간 230: 공간 매핑](holograms-230.md)
* [MR 도구 키트, 공간 매핑 라이브러리](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [MR 부록 키트, 포스터 보정 샘플](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [MR 부록 키트, Kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a>외부 참조

* [Lowes 사례 연구, 전체 자릿수 맞춤](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a>편안 하 게 영역 보기

앱 개발자는 다양 한 깊이에서 콘텐츠 및 holograms를 배치 하 여 사용자의 눈이 수렴 하는 위치를 제어 합니다. Hololens를 사용 하는 사용자는 사용자 로부터 거의 2.0 m 거리 만큼 떨어진 곳에서 화면을 고정 하 여 깨끗 한 이미지를 유지 관리 하기 위해 항상 2.0 m을 수용 합니다. 콘텐츠 깊이가 잘못 되 면 visual discomfort 또는 피로이 발생할 수 있습니다.

### <a name="device-impact"></a>장치 영향

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>품질 기준

<table>
<tr>
<td> 최상위 </td><td><ul>
<li>2m에 콘텐츠를 저장 합니다.</li><li>2m에 holograms을 배치할 수 없고 수렴 및 범위 간 충돌을 방지할 수 없는 경우 가장 적합 한 영역 배치는 1.25 m과 5m 사이입니다.</li><li>모든 경우에서 디자이너는 콘텐츠 크기 및 기본 배치 매개 변수를 조정 하는 것과 같이 사용자가 1 + m 자리를 상호 작용할 수 있도록 콘텐츠를 구조화 해야 합니다.</li><li>시나리오에서 특별히 요구 하지 않는 한 클리핑 평면은 1m부터 fadeout을 사용 하 여 구현 해야 합니다.</li><li>더 작은 홀로그램을 더 자세히 관찰 해야 하는 경우에는 콘텐츠가 50cm 보다 가까이 있지 않아야 합니다.</li>
</ul></td>
</tr><tr>
<td> 평가</td><td> 콘텐츠는 보기 및 동작 지침 내에 있지만 클리핑 평면을 부적절 하 게 사용 하거나 사용 하지 않습니다.</td>
</tr><tr>
<td> 통과 </td><td> 콘텐츠가 너무 가까이 표시 됩니다 (일반적 &lt;으로 1.25 m 또는 &lt;holograms를 더 자세히 관찰 해야 하는 고정 된의 경우 50cm).</td>
</tr>
</table>

### <a name="how-to-measure"></a>측정 방법

* 콘텐츠는 일반적으로 2m 이상 이지만 1.25 보다 작거나 5m 보다 커야 합니다.
* 몇 가지 예외를 제외 하 고, HoloLens 클리핑 렌더링 거리는 1m에서 시작 하는 콘텐츠가 있는 85CM으로 설정 되어야 합니다. 내용에 접근 하 고 클리핑 평면 효과를 확인 합니다.
* 고정 콘텐츠는 50cm 떨어진 곳에 가까울수록 안됩니다.

### <a name="recommendations"></a>권장 사항

* 2m의 최적의 보기 거리에 대 한 디자인 콘텐츠입니다.
* 1m에서 시작 하 여 fadeout 콘텐츠를 사용 하 여 클리핑 렌더링 거리를 85cm로 설정 합니다.
* 자세히 보기를 필요로 하는 고정 된 holograms의 경우에는 클립 평면이 30cm 보다 가까이 있지 않아야 하 고, fadeout이 클리핑 평면에서 10cm 이상 시작 되어야 합니다.

### <a name="resources"></a>리소스

* [렌더링 거리](hologram-stability.md#hologram-render-distances)
* [Unity의 포커스 포인트](focus-point-in-unity.md)
* [규모 실험](scale.md#experimenting-with-scale)
* [텍스트, 권장 글꼴 크기](typography.md#recommended-font-size)

## <a name="depth-switching"></a>깊이 전환

편안 하 게 발생 하는 문제 영역을 확인 하는 것에 관계 없이 사용자가 근거리 및 far 초점면 (holograms 및 실제 콘텐츠 포함) 사이에서 자주 또는 빠르게 전환 하는 요구는 oculomotor 피로 및 일반 discomfort으로 이어질 수 있습니다.

### <a name="device-impact"></a>장치 영향

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>품질 기준

|  최상위  |  평가 |  통과 |
--- | --- | ---
|  사용자가 자연스럽 게 refocus 하지 않는 제한 된 또는 자연 스러운 수준 전환. | 갑작스러운 깊이 전환이는 핵심 이며 앱 환경 또는 예기치 않은 실제 콘텐츠로 인 한 급격 한 깊이 전환으로 설계 되었습니다. | 일관 된 깊이 전환 또는 앱 환경에 대 한 필수 또는 핵심이 아닌 급격 한 깊이 전환. | 

### <a name="how-to-measure"></a>측정 방법

* 앱에서 사용자가 일관 되 게, 또는 갑자기 깊이 포커스를 변경 해야 하는 경우 깊이 전환 문제가 있습니다.

### <a name="recommendations"></a>권장 사항

* 일관 된 초점 평면에서 기본 콘텐츠를 유지 하 고 안정화 평면이 초점면와 일치 하는지 확인 합니다. 그러면 oculomotor 피로 및 예기치 않은 홀로그램 이동이 완화 됩니다.

### <a name="resources"></a>리소스

* [렌더링 거리](hologram-stability.md#hologram-render-distances)
* [Unity의 포커스 포인트](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a>공간 음향 사용

Windows Mixed Reality에서 오디오 엔진은 방향, 거리 및 환경 시뮬레이션을 사용 하 여 3D 소리를 시뮬레이션 하 여 혼합 현실 환경의 aural 구성 요소를 제공 합니다. 개발자는 응용 프로그램에서 공간 소리를 사용 하 여 모든 사용자에 게 3 차원 공간 (구)의 소리를 convincingly 수 있습니다. 이러한 소리는 실제 물리적 개체 또는 사용자 환경에서 혼합 현실 holograms에서 가져온 것 처럼 보입니다. 공간 사운드는 혼합 현실 응용 프로그램에서 집중 교육, 접근성 및 UX 디자인을 위한 강력한 도구입니다.

### <a name="device-impact"></a>장치 영향

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>품질 기준

|  최상위  |  평가 |  통과 |
--- | --- | ---
|  소리는 논리적으로 spatialized UX는 소리를 적절 하 게 사용 하 여 개체 검색 및 사용자 피드백을 지원 합니다. 소리는 자연스럽 고 개체와 관련이 있으며 시나리오 전체에서 정규화 됩니다. | 공간 오디오는 believability에 적합 하 게 사용 되지만 사용자 의견 및 검색 기능을 지원 하기 위한 수단으로는 없습니다. | 소리는 예상 대로 spatialized 되지 않으며 UX 내에서 사용자를 지원 하기 위해 소리가 부족할 수 있습니다. 또는 공간 오디오는 시나리오 디자인에서 고려 되지 않았거나 사용 되지 않았습니다. | 

### <a name="how-to-measure"></a>측정 방법

* 일반적으로 관련 소리는 대상 holograms에서 내보내야 합니다 (예: holographic dog에서 오는 짖 소리).
* 사용자에 게 holographic 프레임 외부의 작업을 인식 하거나 피드백을 제공할 수 있도록 UX 전체에서 사운드 신호를 사용 해야 합니다.

### <a name="recommendations"></a>권장 사항

* 공간 오디오를 사용 하 여 개체 검색 및 사용자 인터페이스를 지원 합니다.
* 실제 소리는 합성 또는 비 자연 음향 보다 효과적입니다.
* 대부분의 소리는 spatialized 이어야 합니다.
* 보이지 않는 송신기를 사용 하지 마십시오.
* 공간 마스킹을 사용 하지 않습니다.
* 모든 소리를 표준화 합니다.

### <a name="resources"></a>리소스

#### <a name="documentation"></a>설명서

* [공간 음향](spatial-sound.md)
* [공간 음향 디자인](spatial-sound-design.md)
* [Unity의 공간 음향](spatial-sound-in-unity.md)
* [사례 연구, HoloTour에 대 한 공간 음향](case-study-spatial-sound-design-for-holotour.md)
* [사례 연구, RoboRaid에서 공간 소리 사용](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a>도구 및 자습서

* [MR 공간 220: 공간 음향](holograms-220.md)
* [MRToolkit, 공간 오디오](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a>FOV (holographic frame) 경계에 집중

잘 디자인 된 사용자 환경은 사용자를 중심으로 확장 되는 가상 환경의 유용한 컨텍스트를 만들고 유지 관리할 수 있습니다. FOV 경계의 효과를 완화 하는 것은 콘텐츠 크기 조정 및 컨텍스트, 공간 오디오, 지침 시스템 및 사용자 위치의 사용에 대 한 자세한 디자인을 포함 합니다. 이 작업을 수행 하는 경우 사용자는 편안 하 게 앱 환경을 사용 하는 동안 FOV 경계에 의해 손상 된 것을 느낄 수 있습니다.

### <a name="device-impact"></a>장치 영향

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>품질 기준

|  최상위  |  평가 |  통과 |
--- | --- | ---
|  사용자는 컨텍스트를 손실 하지 않으며 보기는 편안 합니다. 대량 개체에 대 한 컨텍스트 지원이 제공 됩니다. 프레임 외부 개체에 대 한 검색 가능성 및 보기 지침이 제공 됩니다. 일반적으로 holograms의 동작 디자인과 크기는 편안 하 게 볼 수 있는 환경에 적합 합니다. | 사용자는 컨텍스트를 손실 하지 않지만 제한 된 상황에서는 추가 목 모션이 필요할 수 있습니다. 제한 된 상황에서 크기 조정으로 인해 holograms는 수직 또는 수평 프레임을 중단 하 여 holograms를 볼 수 있습니다. | Holograms를 보려면 컨텍스트를 손실 하 고/또는 일관성 있는 목 모션이 필요 합니다. 큰 holographic 개체에 대 한 컨텍스트 지침이 없습니다. 검색 지침이 없는 프레임 외부에서 개체를 이동 하는 것이 불가능 하거나, 긴 holograms를 보려면 일반적인 목 모션이 필요 합니다. | 

### <a name="how-to-measure"></a>측정 방법

* (규모가 큼) 홀로그램의 컨텍스트가 손실 되거나 경계에서 잘릴 수 있으므로 인식 되지 않습니다.
* Holograms의 위치는 holographic 프레임에서 빠르게 이동 하는 관심 있는 감독 또는 콘텐츠가 부족 하기 때문에 찾기가 어렵습니다.
* 시나리오를 수행 하려면 일반적인 및 반복적인 위쪽 및 아래쪽 헤드 동작을 수행 하 여 홀로그램을 피로 합니다.

### <a name="recommendations"></a>권장 사항

* FOV에 맞는 작은 개체를 사용 하 여 환경을 시작한 다음 시각적 신호를 사용 하 여 더 큰 버전으로 전환 합니다.
* 공간 오디오 및 주의 감독을 사용 하면 사용자가 FOV 외부에 있는 콘텐츠를 찾을 수 있습니다.
* 가능 하면 FOV를 수직으로 자르는 holograms을 피합니다.
* 최상의 보기 위치를 위해 사용자에 게 앱 내 지침을 제공 합니다.

### <a name="resources"></a>리소스

#### <a name="documentation"></a>설명서

* [홀로그램 프레임](holographic-frame.md)
* [사례 연구, HoloStudio UI 및 상호 작용 디자인 학습](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [개체 및 환경의 크기 조정](scale.md)
* [커서, 시각적 신호](cursors.md#visual-cues)

#### <a name="external-references"></a>외부 참조

* [FOV에 대 한 많은 ado](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a>사용자 위치에 반응 하는 콘텐츠

Holograms은 "실제" 개체와 거의 동일한 방식으로 사용자의 위치에 대응 해야 합니다. 주목할 만한 디자인 고려 사항은 사용자의 위치를 고정 하 고 사용자의 동작에 맞게 조정할 수 있는 UI 요소입니다. 사용자 위치에 맞게 올바르게 조정 되는 앱을 디자인 하면 더 이익은 환경을 만들고 더 쉽게 사용할 수 있습니다.

### <a name="device-impact"></a>장치 영향

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>품질 기준

<table>
<tr>
<td> 최상위 </td><td> 사용자가 필요한 사용자 이동 범위 내에서 사용자가 자연스럽 게 콘텐츠와 상호 작용할 수 있도록 콘텐츠와 UI가 사용자 위치에 맞게 조정 됩니다.</td>
</tr><tr>
<td> 평가 </td><td> UI는 사용자 위치에 맞게 조정 되지만 사용자의 위치를 조정 해야 하는 주요 콘텐츠 보기를 방해할 수 있습니다.</td>
</tr><tr>
<td> 통과 </td><td><ol>
<li>UI 요소는 이동 하는 동안 손실 되거나 잠기므로 사용자가 컨트롤로 반환 (또는 찾기) 하지 않습니다.</li><li>UI 요소는 기본 콘텐츠 보기를 제한 합니다.</li><li>UI 이동은 특히 <a href="billboarding-and-tag-along.md">태그 동반</a> ui 요소를 사용 하 여 거리 및 모멘텀를 볼 수 있도록 최적화 되어 있지 않습니다.</li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a>측정 방법

* 모든 측정값은 시나리오의 적절 한 범위 내에서 수행 해야 합니다. 사용자 이동이 다를 수 있지만 응용 프로그램을 실행 하는 데는 극단적인 사용자 이동이 필요 하지 않습니다.
* UI 요소의 경우 사용자 이동에 관계 없이 관련 컨트롤을 사용할 수 있습니다. 예를 들어 사용자가 확대/축소를 사용 하 여 3D 맵을 보고 탐색 하는 경우 위치에 관계 없이 사용자가 확대/축소 컨트롤을 쉽게 사용할 수 있습니다.

### <a name="recommendations"></a>권장 사항

* 사용자가 카메라 이며 이동을 제어 합니다. 드라이브를 사용 하도록 합니다.
* 다른 방법으로는 사용자가 이동 하는 경우에는 전 세계에 잠그거나 가려져 없는 텍스트 및 menuing 시스템에 대해 billboarding을 고려 합니다.
* 사용자가 앞에 있는 내용을 볼 수 있도록 허용 하면서 사용자를 따라야 하는 콘텐츠에 태그를 함께 사용 합니다.

### <a name="resources"></a>리소스

#### <a name="documentation"></a>설명서

* [상호 작용 디자인](hologram.md)
* [색, 광원 및 재질](color,-light-and-materials.md)
* [빌보딩 및 태그얼롱](billboarding-and-tag-along.md)
* [Instinctual 상호 작용](interaction-fundamentals.md)
* [자체 동작 및 사용자 locomotion](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a>도구 및 자습서

* [MR 입력 210: 응시](holograms-210.md)

## <a name="input-interaction-clarity"></a>입력 상호 작용 명확성

입력 상호 작용의 명확성은 앱의 유용성에 매우 중요 하며, 입력 일관성, approachability, 상호 작용 메서드의 검색 기능을 포함 합니다. 사용자는 재설정 없이 플랫폼 전체의 공통 상호 작용을 사용할 수 있어야 합니다. 앱에 사용자 지정 입력이 있는 경우 명확 하 게 통신 하 고 설명 해야 합니다.

### <a name="device-impact"></a>장치 영향

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>품질 기준

|  최상위  |  평가 |  통과 |
--- | --- | ---
|  입력 상호 작용 방법은 Windows Mixed Reality 제공 [지침](interaction-fundamentals.md)과 일치 합니다. 모든 사용자 지정 입력은 표준 상호 작용을 사용 하는 대신 표준 입력으로 중복 되어서는 안 되며, 사용자에 게 명확 하 게 전달 하 고 표시 해야 합니다. | 가장 좋지만 사용자 지정 입력은 표준 입력 방법으로 중복 됩니다. 사용자는 여전히 앱 환경을 통해 목표와 진행 상황을 달성할 수 있습니다. | 입력 방법 또는 단추 매핑을 이해 하기 어렵습니다. 입력은 과도 하 게 사용자 지정 되므로 표준 입력을 지원 하지 않거나 지침이 없거나 피로 및 편안 하 게 문제가 발생할 수 있습니다. | 

### <a name="how-to-measure"></a>측정 방법

* 앱은 일관 된 [표준 입력 메서드를 사용 합니다.](interaction-fundamentals.md)
* 앱에 customer 입력이 있는 경우 다음을 통해 명확 하 게 전달 됩니다.
* 첫 실행 환경
* 소개 화면
* 도구 설명
* 손 coach
* 도움말 섹션
* 음성 전달

### <a name="recommendations"></a>권장 사항

* 가능 하면 표준 입력 메서드를 사용 합니다.
* 비표준 입력 방법에 대 한 데모, 자습서 및 도구 설명을 제공 합니다.
* 응용 프로그램 전체에서 일관 된 상호 작용 모델을 사용 합니다.

### <a name="resources"></a>리소스

#### <a name="documentation"></a>설명서

* [Instinctual 상호 작용](interaction-fundamentals.md)
* [Interactable 개체](interactable-object.md)
* [헤드 게이즈 및 유지](gaze-and-dwell.md)
* [커서](cursors.md)
* [편안 함 및 응시](comfort.md#gaze-direction)
* [제스처](gestures.md)
* [음성 입력 ](voice-input.md)
* [음성 명령](voice-design.md)
* [모션 컨트롤러](motion-controllers.md)
* [Unity 입력 포팅 가이드](input-porting-guide-for-unity.md)
* [Unity의 키보드 입력](keyboard-input-in-unity.md)
* [Unity의 응시](gaze-in-unity.md)
* [Unity의 제스처 및 모션 컨트롤러](gestures-and-motion-controllers-in-unity.md)
* [Unity의 음성 입력](voice-input-in-unity.md)
* [DirectX의 키보드, 마우스 및 컨트롤러 입력](keyboard,-mouse,-and-controller-input-in-directx.md)
* [DirectX의 헤드 및 눈 응시](gaze-in-directx.md)
* [DirectX의 헤드 및 모션 컨트롤러](hands-and-motion-controllers-in-directx.md)
* [DirectX의 음성 입력](voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a>도구 및 자습서

* [사례 연구: 더 많은 개인 컴퓨팅 담당](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [캐스트 조사: HoloStudio UI 및 상호 작용 디자인 학습](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [샘플 앱: 요소의 주기적 테이블](periodic-table-of-the-elements.md)
* [샘플 앱: 음력 모듈](lunar-module.md)
* [MR 입력 210: 응시](holograms-210.md)
* [MR 입력 211: 제스처](holograms-211.md)
* [MR 입력 212: 음성](holograms-212.md)

## <a name="interactable-objects"></a>Interactable 개체

단추는 긴 2D 추상 세계에서 이벤트를 트리거하는 데 사용 되는 비유입니다. 3 차원 혼합 현실 세계에서는 이러한 추상화의 목표로 더 이상 국한 되지 않습니다. 모든 항목은 이벤트를 트리거하는 Interactable 개체 일 수 있습니다. Interactable 개체는 테이블의 커피에서 공기의 풍선 부동으로 표시할 수 있습니다. Interactable 개체는 폼에 관계 없이 시각적 및 오디오 큐를 통해 사용자가 명확 하 게 인식할 수 있어야 합니다.

### <a name="device-impact"></a>장치 영향

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>품질 기준

|  최상위  |  평가 |  통과 |
--- | --- | ---
|  폼에 관계 없이 interactable 개체는 유휴 상태, 대상 지정 및 선택 됨의 세 가지 상태에서 시각적 및 오디오 큐를 통해 인식할 수 있습니다. "이 항목을 참조 하세요." 라는 것은 전체 환경에서 명확 하 고 일관 되 게 사용 됩니다. 개체를 확장 하 고 배포 하 여 오류를 자유롭게 대상으로 지정할 수 있습니다. | 사용자는 오디오 또는 시각적 피드백을 통해 interactable로 개체를 인식할 수 있으며 개체를 대상으로 하 고 활성화할 수 있습니다. | 시각적 개체 또는 오디오 신호를 제공 하지 않으면 사용자가 interactable 개체를 인식할 수 없습니다. 개체 확장 또는 개체 간 거리 때문에 오류가 발생 하기 쉽습니다. | 

### <a name="how-to-measure"></a>측정 방법

* Interactable 개체는 ' Interactable '로 인식할 수 있습니다. 단추, 메뉴 및 앱 관련 콘텐츠를 포함 합니다. 이에 대 한 규칙은 interactable 개체를 대상으로 지정할 때 시각 및 오디오 큐가 있어야 합니다.

### <a name="recommendations"></a>권장 사항

* 시각적 개체와 오디오 피드백을 사용 하 여 상호 작용 합니다.
* 각 입력 상태 (유휴 상태, 대상 지정, 선택 됨)에 대해 시각적 피드백을 구분 해야 합니다.
* Interactable 개체의 크기를 조정 하 고 오류를 자유롭게 대상으로 지정 해야 합니다.
* 그룹화 된 interactable 개체 (예: 메뉴 모음 또는 목록)에는 대상 지정을 위한 적절 한 간격이 있어야 합니다.
* 음성 명령을 지 원하는 단추 및 메뉴는 명령 키워드 ("참조)에 대 한 텍스트 레이블을 제공 해야 합니다.

### <a name="resources"></a>리소스

#### <a name="documentation"></a>설명서

* [상호 작용 가능한 개체](interactable-object.md)
* [Unity의 텍스트](text-in-unity.md)
* [경계 상자 및 앱 바](app-bar-and-bounding-box.md)
* [음성 명령](voice-design.md)

#### <a name="tools-and-tutorials"></a>도구 및 자습서

* [Mixed Reality Toolkit-UX](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a>대화방 스캔

공간 매핑 데이터를 필요로 하는 앱은 사용자가 장치를 활성화 하 여 환경을 탐색 하는 동안 시간 및 세션 간에이 데이터를 자동으로 수집 하는 장치에 의존 합니다. 이 데이터의 완성도와 품질은 사용자가 수행한 탐색 크기, 탐색 이후 경과 된 시간, 장치에서 영역을 스캔 한 후 가구 및 문과 같은 개체가 이동 했는지 여부를 포함 하는 다양 한 요인에 따라 달라 집니다. 많은 앱은 사용자가 공간 맵의 완전성 및 품질을 개선 하기 위해 추가 단계를 수행 해야 하는지 여부를 판단 하기 위해 경험을 시작할 때 공간 매핑 데이터를 분석 합니다. 사용자가 환경을 검색 해야 하는 경우 검사 하는 동안 지침이 제공 되어야 합니다.

### <a name="device-impact"></a>장치 영향

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>품질 기준

|  최상위  |  평가 |  통과 |
--- | --- | ---
|  사용자 검사가 진행 중 이라고 알려주는 공간 메시의 시각화입니다. 사용자가 수행할 작업과 검사가 시작 및 중지 되는 시기를 명확 하 게 알 수 있습니다. | 공간 메시의 시각화가 제공 되지만 사용자가 수행할 작업을 명확 하 게 알지 못할 수 있으며 진행 정보는 제공 되지 않습니다. | 메시의 시각화가 없습니다. 찾을 위치와 관련 하 여 사용자에 게 제공 되는 지침 정보가 없습니다. 검색을 시작/중지할 수 있습니다. |

### <a name="how-to-measure"></a>측정 방법

* 필요한 방 스캔 중에는 찾을 위치와 검사를 시작 및 중지 하는 시기를 나타내는 시각적 개체와 오디오 지침이 제공 됩니다.

### <a name="recommendations"></a>권장 사항

* 사용자가 환경에 포함 해야 하는 총 볼륨의 크기를 표시 합니다.
* 검사가 시작 되 면 통신 하 고 진행률 표시기와 같은 작업을 중지 합니다.
* 검색 중에 메시의 시각화를 사용 합니다.
* 사용자가 대화방을 보고 이동할 수 있도록 시각적 및 오디오 신호를 제공 합니다.
* 데이터를 개선 하기 위해 이동할 위치를 사용자에 게 알립니다. 필요한 검색 품질을 얻기 위해 수행 해야 하는 작업을 사용자에 게 알리는 것이 가장 좋을 수 있습니다. 예를 들어 천장, 가구를 찾는 등의 작업을 수행 하는 것이 좋습니다.

### <a name="resources"></a>리소스

#### <a name="documentation"></a>설명서

* [실내 스캔 시각화](room-scan-visualization.md)
* [사례 연구: HoloLens의 공간 매핑 기능 확장](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [사례 연구: HoloTour에 대 한 공간 음향 디자인](case-study-spatial-sound-design-for-holotour.md)
* [사례 연구: 조각에서 몰입 형 환경 만들기](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a>도구 및 자습서

* [Mixed Reality Toolkit-UX](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a>방향 표시기

혼합 현실 앱에서 콘텐츠는 실제 개체에서 뷰 또는 폐색의 필드 밖에 있을 수 있습니다. 잘 디자인 된 앱을 사용 하면 사용자가 보이지 않는 콘텐츠를 더 쉽게 찾을 수 있습니다. 방향성 표시기는 사용자에 게 중요 한 콘텐츠를 경고 하 고 사용자의 위치를 기준으로 콘텐츠에 대 한 지침을 제공 합니다. 보이지 않는 콘텐츠에 대 한 지침은 소리 송신기, 방향 화살표 또는 직접 시각적 표시의 형태로 사용할 수 있습니다.

### <a name="device-impact"></a>장치 영향

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>품질 기준

|  최상위  |  평가 |  통과 |
--- | --- | ---
|  시각적 개체와 오디오 큐는 사용자에 게 보기 필드 외부의 관련 콘텐츠를 직접 안내 합니다. | 콘텐츠의 일반적인 방향을 사용자에 게 가리키는 화살표 또는 표시기입니다. | 관련 콘텐츠가 보기 필드의 외부에 있으며 사용자에 게 잘못 된 위치나 위치 지침이 없습니다. | 

### <a name="how-to-measure"></a>측정 방법

* 보기의 사용자 필드 외부에 있는 관련 콘텐츠는 시각적 개체 및/또는 오디오 신호를 통해 검색할 수 있습니다.

### <a name="recommendations"></a>권장 사항

* 관련 콘텐츠가 사용자의 보기 필드 외부에 있는 경우 방향 표시기와 오디오 신호를 사용 하 여 사용자에 게 콘텐츠를 안내 합니다. 대부분의 경우에는 방향 화살표 보다 직접 시각적 개체 가이드가 선호 됩니다.
* 방향 표시기는 커서에 내장 되어서는 안 됩니다.

### <a name="resources"></a>리소스

* [홀로그램 프레임](holographic-frame.md)

## <a name="data-loading"></a>데이터 로드

진행률 컨트롤은 긴 작업을 진행 중인 사용자에게 피드백을 제공합니다. 진행률 표시기가 표시 될 때 사용자가 앱과 상호 작용할 수 없으며 대기 시간이 얼마나 길어질 수도 있음을 의미할 수 있습니다.

### <a name="device-impact"></a>장치 영향

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>품질 기준

|  최상위  |  평가 |  통과 |
--- | --- | ---
|  데이터를 로드 또는 처리 하는 동안 진행률이 표시 되는 진행률 표시줄 또는 링 형식의 애니메이션 시각적 표시기입니다. 시각적 표시기는 대기 시간에 대 한 지침을 제공 합니다. | 사용자에 게 데이터 로드가 진행 중 이라는 알림이 표시 되지만 대기 시간을 나타내는 것은 표시 되지 않습니다. | 5 초 보다 오래 걸리는 태스크에 대 한 데이터 로드 또는 프로세스 표시기가 없습니다. |

### <a name="how-to-measure"></a>측정 방법

* 데이터를 로드 하는 동안 5 초 넘게 비어 있는 상태가 없는지 확인 합니다.

### <a name="recommendations"></a>권장 사항

* 사용자가이 앱을 중단 또는 충돌 하도록 할 수 있는 경우 진행 상황을 보여 주는 데이터 로드 애니메이터를 제공 합니다. 적절 한 엄지 단추는 5 초 넘게 걸릴 수 있는 ' 로드 ' 작업입니다.

### <a name="resources"></a>리소스

* [진행률 표시](progress.md)
