---
title: 앱 품질 기준
description: 이 문서에는 혼합된 현실 앱의 품질에 영향을 주는 상위 요소를 설명 합니다.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: 앱 품질 기준에 혼합 현실을, 혼합 현실 앱
ms.openlocfilehash: 8070a434be462a636b314527c59f299ca77fb6d4
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602380"
---
# <a name="app-quality-criteria"></a>앱 품질 기준

이 문서에는 혼합된 현실 앱의 품질에 영향을 주는 상위 요소를 설명 합니다. 각 요소에 대 한 다음 정보가 제공 됩니다.
* 개요-품질 요소 및 중요 한 이유는 간략 한 설명입니다.
* 장치 영향-어떤 유형의 창 혼합 현실 장치 영향을 받습니다.
* 품질 기준 – 품질 요소를 평가 하는 방법입니다.
* – 문제를 측정 (또는 환경) 메서드를 측정 하는 방법.
* 권장 사항-더 나은 사용자 환경을 제공 하는 방법을 요약 합니다.
* 리소스-관련 개발자 및 더 나은 앱 환경을 만드는 것이 유용할 수 있는 디자인 리소스입니다.

## <a name="frame-rate"></a>프레임 속도

프레임 속도 홀로그램 안정성 및 사용자와 쾌적의 첫 번째 기본 요소입니다. 아래 권장 되는 대상 프레임 속도 홀로그램 흔들림 환경의 believability에 부정적인 영향을 고 눈 피로 잠재적으로 표시 될 수 있습니다. Windows Mixed Reality 몰입 형 헤드셋에서 환경에 대 한 대상 프레임 속도 60hz 또는 지원 하려는 Windows Mixed Reality 호환 Pc에 따라 90이 됩니다. HoloLens에 대 한 대상 프레임 속도 60hz 합니다.

### <a name="device-impact"></a>장치 영향

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>품질 기준

|  가장  |  충족 |  실패 |
--- | --- | ---
| 앱 당 대상 장치에 대 한 두 번째 (FPS) 목표 프레임을 일관 되 게 충족합니다. HoloLens;에서 60 fps Ultra pc; 90 fps 및 일반 Pc에서 60 fps 합니다. | 앱에 방해가 되지 core 환경을; 일시적인 프레임 삭제 또는 FPS 원하는 목표 보다 일관 되 게 낮은 하지만 앱 환경을 방해 하지 않습니다. | 앱에서 프레임 속도 평균 10 초 마다 이하로 떨어지는 발생 했습니다. |

### <a name="how-to-measure"></a>측정 방법

* 실시간 프레임 속도 그래프를 통해 제공 됩니다는 [Windows Device Portal](using-the-windows-device-portal.md#system-performance) "시스템 성능"입니다.
* 개발 디버깅을 위해 앱에 진단 프레임 속도 카운터를 추가 합니다. 샘플 카운터에 대 한 리소스를 참조 하세요.
* 프레임 속도 삭제 머리를 좌우 이동 하 여 앱이 실행 되는 동안 장치에서 발생할 수 있습니다. 홀로그램 예기치 않은 흔들림 이동에 표시 하는 경우 다음 낮은 프레임 속도 또는 안정성 평면 원인이 될 수 있습니다.

### <a name="recommendations"></a>권장 사항

* 개발 작업의 시작 부분에 프레임 속도 카운터를 추가 합니다.
* 프레임 속도가 떨어지는 발생 하는 변경 내용은 평가 하 고 성능 버그로 적절 하 게 확인 해야 합니다.

### <a name="resources"></a>리소스

#### <a name="documentation"></a>설명서

* [혼합된 현실에 대 한 성능 이해](understanding-performance-for-mixed-reality.md)
* [홀로그램 안정성 및 프레임 속도](hologram-stability.md#frame-rate)
* [자산 성능 예산이](asset-creation-process.md)
* [Unity에 대 한 성능 권장 사항](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a>도구 및 자습서

* [MRToolkit, FPS 카운터 표시](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [MRToolkit, 셰이더](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a>외부 참조

* [Unity에서 모바일 응용 프로그램 최적화](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a>홀로그램 안정성

안정적인 홀로그램 유용성 및 앱의 believability 증가 더 편리 하 게 보기 환경을 사용자에 대 한 합니다. 홀로그램 안정성 품질이 좋은 앱 개발 및 (추적)를 이해 하는 장치의 기능 결과 해당 환경입니다. 프레임 속도 안정성의 첫 번째 pillar 상태인 다른 요인 안정성 포함 하 여 영향을 줄 수 있습니다.:

* 안정화 평면 사용
* 공간 앵커 거리입니다.
* 추적

### <a name="device-impact"></a>장치 영향

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a>품질 기준

|  가장  |  충족 |  실패 |
--- | --- | ---
|  홀로그램은 일관 되 게 안정적인를 표시 합니다. | 보조 콘텐츠 보여 예기치 않은 이동 합니다. 또는 예기치 않은 이동 전체 앱 환경을 방해 하지 않습니다. | 주 콘텐츠 프레임에 예기치 않은 이동을 보여 줍니다. |

### <a name="how-to-measure"></a>측정 방법

장치를 착용 하 고 환경을 보는 동안:

* 측면에서 머리를 이동 하 여 홀로그램 예기치 않은 이동을 표시 하는 경우 다음 낮은 프레임 속도 하거나 부적절 한 초점 평면에 안정성 평면의 맞춤이 발생할 수 있습니다.
* 홀로그램 및 환경 이동, 스윔 jumpiness 등 동작에 대 한 확인 합니다. 이 유형의 동작 추적 하지 환경 또는 거리를 공간 앵커 장치 원인일 가능성이 큽니다.
* 많은 경우 또는 여러 홀로그램 프레임에 안정화 평면 원인일 가능성이 있으면 흔들리는 헤드 현황을 측면에서 이동 하는 동안 다양 한 깊이 있는 홀로그램 동작을 관찰 합니다.

### <a name="recomendations"></a>Recomendations

* 개발 작업의 시작 부분에는 프레임 속도 카운터를 추가 합니다.
* 안정화 평면을 사용 합니다.
* 항상 해당 앵커 3 미터 내에서 고정된 홀로그램을 렌더링 합니다.
* 사용자 환경이 적절 한 추적을 위한 설치 되었는지 확인 합니다.
* 프레임 내에서 다양 한 초점 깊이 수준에는 제공 하지 않으려면 환경을 설계 합니다.

### <a name="resources"></a>리소스

#### <a name="documentation"></a>설명서

* [홀로그램 안정성 및 프레임 속도](hologram-stability.md#frame-rate)
* [안정화 평면을 사용 하 여 사례 연구](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [혼합된 현실에 대 한 성능 이해](understanding-performance-for-mixed-reality.md)
* [Unity에 대 한 성능 권장 사항](performance-recommendations-for-unity.md)
* [공간 앵커](spatial-anchors.md)
* [추적 오류 처리](coordinate-systems.md#handling-tracking-errors)
* [고정 참조 프레임](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a>도구 및 자습서

* [Kinect IPD MR 도우미 키트](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a>실제 화면에서 홀로그램 위치

실제 개체 (지정한 경우 서로 기준으로 배치)를 사용 하 여 홀로그램의 misalignments는 비-공용 구조체 홀로그램 및 실세계의 명백한 증거입니다. 배치의 정확도; 시나리오의 요구를 기준으로 해야 합니다. 예를 들어 일반 화면 배치 공간 맵을 사용할 수 있지만 보다 정확 하 게 배치 표식 및 보정 일부 사용 해야 합니다.

### <a name="device-impact"></a>장치 영향

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a>품질 기준

|  가장  |  충족 |  실패 |
--- | --- | ---
| 홀로그램 인치 범위를 센티미터 단위로 일반적으로 화면에 맞춥니다. 자세한 정확도 필요한 경우 앱 원하는 앱 사양 내에서 공동 작업 하는 효율적인 방법을 제공 해야 합니다. | NA | 홀로그램 화면의 평면을 중단 하거나 화면에서 float로 표시 하 여 실제 대상 개체를 사용 하 여 정렬 되지 않은 나타납니다. 정확도 필요한 경우 홀로그램 시나리오의 근접 사양을 충족 해야 합니다. | 

### <a name="how-to-measure"></a>측정 방법

* 홀로그램 공간 지도에 배치 되는 크게 위나 아래 화면에 고정 해제 하지 나타납니다.
* 홀로그램 정확 하 게 배치 해야 하는 시나리오의 요구 사항을 정확 하 게 된 표식 및 보정 시스템 형태의 있어야 합니다.

### <a name="recommendations"></a>권장 사항

* 공간 맵 정밀도 필요 없는 경우 화면에서 개체를 배치 하는 데 유용 합니다.
* 최상의 전체 자릿수를 사용 하 여 표식이 나 포스터를 홀로그램 및 Xbox 컨트롤러를 (또는 일부 수동 맞춤 메커니즘)를 설정 합니다. 최종 보정에 대 한 합니다.
* 초대형 홀로그램 논리적 부분으로 분할 하 고 각 부분을 화면에 맞게 조정 하는 것이 좋습니다.
* 부적절 하 게 집합 interpupilary 거리 IPD 영향을 홀로그램 맞춤을 줄 수도 있습니다. 항상 사용자의 IPD에 HoloLens를 구성 합니다.

### <a name="resources"></a>리소스

#### <a name="documentation"></a>설명서

* [공간 매핑 배치](spatial-mapping.md#placement)
* [검색 프로세스 공간](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [공간 앵커에 대 한 유용한 정보](spatial-anchors.md#best-practices)
* [추적 오류 처리](coordinate-systems.md#handling-tracking-errors)
* [Unity에서 공간 매핑](spatial-mapping-in-unity.md)
* [Vuforia 개발 개요](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a>도구 및 자습서

* [MR 공간 230: 공간 매핑](holograms-230.md)
* [MR 도구 키트, 공간 매핑 라이브러리](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [MR 도우미 키트 포스터 보정 샘플](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [Kinect IPD MR 도우미 키트](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a>외부 참조

* [전체 자릿수 맞춤 Lowes 사례 연구](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a>쾌적의 보기 영역

앱 개발자가 컨트롤을 다양 한 깊이 있는 내용 및 홀로그램을 배치 하 여 사용자의 눈을 수렴 하는 위치입니다. HoloLens 착용 하는 사용자가 항상 광학 거리 2.0 m 약 사용자 반대쪽에 고정 HoloLens 표시 되기 때문에 명확한 이미지를 유지 하기 위해 2.0 m 수용 합니다. 부적절 한 콘텐츠 깊이 visual 뜨거움 또는 피로 발생할 수 있습니다.

### <a name="device-impact"></a>장치 영향

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a>품질 기준

<table>
<tr>
<td> 가장 </td><td><ul>
<li>2 분에 콘텐츠를 배치 합니다.</li><li>홀로그램 2 분에 배치할 수 없습니다 하 고 수렴 숙박 사이의 충돌을 피할 수 없는 경우 홀로그램 배치에 대 한 최적의 영역 1.25 m에서 5 분 사이입니다.</li><li>디자이너에 항상 1 + 상호 작용 하도록 장려 하는 콘텐츠를 구성 해야 m 번 (예: 콘텐츠 크기를 조정 및 기본 배치 매개 변수).</li><li>시나리오에 필요한 하지 않는 한 클리핑 평면 1m부터 fadeout 사용 하 여 구현 해야 합니다.</li><li>여기서 작동 없음 홀로그램 좀 더 자세히 관찰 하는 것은 필요한 경우에는 콘텐츠 50 cm 보다 좀 더 자세히 되지 않습니다.</li>
</ul></td>
</tr><tr>
<td> 충족</td><td> 콘텐츠 보기 및 동작 지침 있지만 부적절 한 사용 또는 사용 되지 않지만 클리핑 평면 이내입니다.</td>
</tr><tr>
<td> 실패 </td><td> 콘텐츠 너무 가깝게 표시 됩니다 (일반적으로 &lt;1.25 m 또는 &lt;좀 더 자세히 관찰을 요구 하는 고정 제공에 대 한 50 cm.)</td>
</tr>
</table>

### <a name="how-to-measure"></a>측정 방법

* 콘텐츠 일반적으로 있어야 2m 았 있지만 1.25 또는 5 분 보다 더 보다 더 자세히 합니다.
* 몇 가지 예외를 제외 하 고, fadeout 1m에서 시작 하는 콘텐츠를 사용 하 여 HoloLens 클리핑 렌더링 거리.85CM을 설정 해야 합니다. 콘텐츠 있으며 클리핑 평면 효과 유의 하십시오.
* 고정 콘텐츠 50 cm 지금 보다 좀 더 자세히 되지 않아야 합니다.

### <a name="recommendations"></a>권장 사항

* 2 분의 최적의 상태로 보기 거리에 대 한 콘텐츠를 디자인 합니다.
* Fadeout 1m에서 시작 하는 콘텐츠를 사용 하 여 85 cm을 클리핑 렌더링 거리를 설정 합니다.
* 가까운 보고 해야 하는 고정 홀로그램 클리핑 평면 30 cm 보다 더 자세히 해야 하며 fadeout 적어도 10 cm 클리핑 평면에서 시작 해야 합니다.

### <a name="resources"></a>리소스

* [거리를 렌더링 합니다.](hologram-stability.md#hologram-render-distances)
* [Unity의 포커스 지점](focus-point-in-unity.md)
* [확장을 사용 하 여 실험](scale.md#experimenting-with-scale)
* [텍스트, 권장 글꼴 크기](typography.md#recommended-font-size)

## <a name="depth-switching"></a>깊이 전환

편안 하 게 문제의 보기 영역에 관계 없이 사용자 간에 자주 또는 신속 하 게 전환할 수에 대 한 요청이 근처 및 홀로그램 및 실제 콘텐츠 등 훨씬 초점 개체 oculomotor 피로 일반 뜨거움 발생할 수 있습니다.

### <a name="device-impact"></a>장치 영향

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>품질 기준

|  가장  |  충족 |  실패 |
--- | --- | ---
|  전환 하는 제한 된 또는 자연 스러운 깊이 비정상적 쉬운데 사용자를 나타나지는 않습니다. | 갑작스러운 깊이 스위치 핵심 이며 앱 환경으로 설계 된 또는 예기치 않은 실제 내용으로 인해 갑작스러운 깊이 스위치. | 일관 된 깊이 스위치 또는 갑작스러운 깊이 전환 하는 필요 하지 않은 또는 앱 환경에는 핵심입니다. | 

### <a name="how-to-measure"></a>측정 방법

* 응용 프로그램에 일관 되 게 및/또는 갑자기 깊이 포커스를 변경 하려면 사용자가 필요한 경우 문제를 전환 하는 깊이 합니다.

### <a name="recommendations"></a>권장 사항

* 일관 된 초점 평면에서 기본 콘텐츠를 유지 하 고 안정화 평면 초점 평면 일치 하는지 확인 합니다. 이 oculomotor 피로 예기치 않은 홀로그램 이동 완화 됩니다.

### <a name="resources"></a>리소스

* [거리를 렌더링 합니다.](hologram-stability.md#hologram-render-distances)
* [Unity의 포커스 지점](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a>소리 공간 사용

Windows Mixed Reality 오디오 엔진 3D 방향, 거리 및 환경 시뮬레이션을 사용 하 여 사운드를 시뮬레이션 하 여 혼합된 현실 환경 청각적 구성 요소를 제공 합니다. 공간 소리를 사용 하 여 응용 프로그램에서 convincingly 3 차원 공간의 (구)에 소리를 배치 하는 개발자를 사용자 대 모든 수 있습니다. 그런 다음 실제 개체 또는 사용자의 환경에서 혼합된 현실 홀로그램에서 온 것 처럼 이러한 소리 친숙할 합니다. 공간 소리는 집중 교육, 내게 필요한 옵션 및 혼합된 현실 응용 프로그램의 UX 디자인에 대 한 강력한 도구입니다.

### <a name="device-impact"></a>장치 영향

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>품질 기준

|  가장  |  충족 |  실패 |
--- | --- | ---
|  소리 spatialized 논리적으로, 및 UX 개체 검색 및 사용자 의견을 지원 하기 위해 적절히 소리를 사용 합니다. 소리가는 시나리오에서 자연 스러운 및 개체와 관련 된 정규화 된입니다. | 공간 오디오가 believability에 적절 하 게 사용 되는 사용자에 게 피드백 및 검색 기능에 도움이 되는 수단으로 없습니다. | 예상 대로 소리 spatialized 하지는 및/또는 사운드를 사용자 환경 내에서 사용자를 지원 하기 위해 부족 또는 공간 오디오 것으로 간주 하지 되었거나 시나리오의 디자인에 사용 합니다. | 

### <a name="how-to-measure"></a>측정 방법

* 대상 홀로그램에서 관련 소리 내보내야 일반적으로 (예:., holographic dog에서 나오는 bark 소리.)
* 사운드 신호 의견이 나 holographic 프레임 외부 작업에 대 한 인식을 사용 하 여 사용자를 지원 하기 위해 UX 전체에서 사용할 해야 합니다.

### <a name="recommendations"></a>권장 사항

* 개체 검색 및 사용자 인터페이스를 사용 하 여 지원 하기 위해 공간 오디오를 사용 합니다.
* 실제 소리 synthesize 또는 비 자연 사운드 보다 더 잘 작동 합니다.
* 대부분의 소리를 spatialized 해야 합니다.
* 보이지 않는 미터를 방지 합니다.
* 공간 마스킹 하지 마세요.
* 모든 소리를 정규화 합니다.

### <a name="resources"></a>리소스

#### <a name="documentation"></a>설명서

* [소리 공간](spatial-sound.md)
* [공간 적절 하 게 디자인](spatial-sound-design.md)
* [Unity에서 공간 소리](spatial-sound-in-unity.md)
* [사례 연구, HoloTour에 대 한 소리 공간](case-study-spatial-sound-design-for-holotour.md)
* [RoboRaid에서 공간 소리를 사용 하 여 사례 연구](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a>도구 및 자습서

* [MR 공간 220: 소리 공간](holograms-220.md)
* [MRToolkit, 공간 오디오](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a>Holographic 프레임 (FOV) 경계에 집중

잘 설계 된 사용자 환경을 만들고 사용자 중심을 확장 하는 가상 환경의 유용한 컨텍스트를 유지 합니다. 콘텐츠 크기 조정 및 상황에 맞는 신중 하 게 설계에서는 FOV 경계의 영향을 완화, 공간 오디오, 지침 시스템 및 사용자의 위치를 사용 합니다. 을 제대로 수행 하는 경우 사용자가 편리 하 게 앱 경험 하는 동안 FOV 경계에 의해 손상 작은 생각 합니다.

### <a name="device-impact"></a>장치 영향

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a>품질 기준

|  가장  |  충족 |  실패 |
--- | --- | ---
|  사용자 컨텍스트를 손실 하지 않습니다 하 고 보기 편리 하 게 됩니다. 큰 개체에 대 한 상황에 맞는 지원이 제공 됩니다. 검색 기능 및 지침 보기 프레임 외부 개체에 대 한 제공 됩니다. 일반적으로 동작 설계 및 소수 자릿수를 홀로그램은 편안한 화면에 적합 합니다. | 사용자 컨텍스트를 손실 되지 않지만 추가 목 동작 제한 된 상황에서 해야 할 수 있습니다. 제한 된 상황 에서만 확장 홀로그램 홀로그램 보기에 일부 목 동작을 유발 하는 세로 또는 가로 프레임 중 하나를 중단 하면 됩니다. | 사용자 컨텍스트 및/또는 일관 된 목 동작 손실 될 위험이 홀로그램 보기 해야 합니다. 개체 검색 기능 지침 또는 긴 홀로그램 없이 프레임 외부 손실 쉽게 이동 하는 큰 holographic 개체에 대 한 상황에 맞는 지침이 없습니다 보려는 일반 목 동작에 필요 합니다. | 

### <a name="how-to-measure"></a>측정 방법

* (큼) 홀로그램에 대 한 컨텍스트를 분실 하거나 경계에서 잘리지 인해 인식할 수 없습니다.
* 홀로그램의 위치는 주의 이사회 또는 신속 하 게 holographic 프레임 내부 및 외부로 이동 하는 콘텐츠 부족으로 인해 찾을 하기가 어렵습니다.
* 시나리오에는 일반 및 헤드 동작 완전히를 홀로그램 목 피로에서 결과 보려면 위/아래로 반복 해야 합니다.

### <a name="recommendations"></a>권장 사항

* FOV, 적합 한 다음 더 큰 버전에 시각 신호를 사용 하 여 전환 하는 작은 개체를 사용 하 여 환경을 시작 합니다.
* 사용자를 FOV 외부에 있는 콘텐츠를 찾기 위해 공간 오디오 및 주의 이사를 사용 합니다.
* 가능한 만큼 세로로 FOV 클립는 제공을 하지 않습니다.
* 최고의 위치 보기에 대 한 앱에서 지침을 사용 하 여 사용자를 제공 합니다.

### <a name="resources"></a>리소스

#### <a name="documentation"></a>설명서

* [Holographic 프레임](holographic-frame.md)
* [사례 연구, HoloStudio UI와 상호 작용 디자인 학습](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [개체 및 환경의 확장](scale.md)
* [커서를 시각 신호](cursors.md#visual-cues)

#### <a name="external-references"></a>외부 참조

* [법석 FOV에 대 한](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a>사용자 위치에 반응 하는 콘텐츠

홀로그램 거의 동일한 방식으로 "실제" 개체는 사용자가 위치 대응 해야 합니다. 중요 한 디자인 고려 사항 중 이며 반드시 사용자의 위치 수 없으므로 UI 요소에 고정 되어 사용자의 동작에 맞게 조정 사용자 위치를 올바르게 조정 되는 앱 디자인 더 이익은 환경을 만들를 쉽게 사용할 수 있도록 합니다.

### <a name="device-impact"></a>장치 영향

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>품질 기준

<table>
<tr>
<td> 가장 </td><td> 콘텐츠 및 UI 콘텐츠로 이동 예상 되는 사용자의 범위 내에서 자연스럽 게 상호 작용 하는 사용자를 허용 하는 사용자 위치에 맞게 조정 합니다.</td>
</tr><tr>
<td> 충족 </td><td> UI는 사용자 위치에 맞게 조정 하지만 사용자의 위치를 조정 하도록 요구 하는 키 콘텐츠 보기를 방해할 수 있습니다.</td>
</tr><tr>
<td> 실패 </td><td><ol>
<li>UI 요소는 분실 하거나 비정상적 돌아갑니다 (또는 찾기) 컨트롤 이동 되어 사용자 중에 잠깁니다.</li><li>UI 요소는 기본 콘텐츠 보기를 제한합니다.</li><li>UI 이동 거리 및 특히 모멘텀 보기 최적화 되지 <a href="billboarding-and-tag-along.md">tag-along</a> UI 요소입니다.</li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a>측정 방법

* 모든 측정 시나리오의 적절 한 범위 내에서 수행 되어야 합니다. 사용자 이동 달라 지지만 앱 극단적인 사용자 이동 하지 마세요.
* UI 요소에 대 한 관련 컨트롤 사용자 이동에 관계 없이 사용할 수 있어야 합니다. 예를 들어 사용자가 보기를 확대/축소를 사용 하 여 3D 맵 주위로 탐색을 하는 경우 확대/축소 컨트롤 위치에 관계 없이 사용자를 쉽게 사용할 수 여야 합니다.

### <a name="recommendations"></a>권장 사항

* 사용자가 카메라와 움직임을 제어 합니다. 이러한 드라이브 수 있습니다.
* 텍스트 빌보드 고려 하 고 그렇지 않으면 world 잠긴 나 사용자가 려 지 수 메뉴 시스템 이동할 이었습니다.
* 여전히 사용자가 앞에 내용을 볼 수 있도록 하는 동안 사용자를 수행 해야 하는 콘텐츠에 대 한 tag-along를 사용 합니다.

### <a name="resources"></a>리소스

#### <a name="documentation"></a>설명서

* [상호 작용 디자인](hologram.md)
* [색, 광원 및 재질](color,-light-and-materials.md)
* [빌보드 및 tag-along](billboarding-and-tag-along.md)
* [상호 작용 기본 사항](interaction-fundamentals.md)
* [동작 자체 및 사용자 locomotion](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a>도구 및 자습서

* [MR 입력 210: 응시](holograms-210.md)

## <a name="input-interaction-clarity"></a>입력된 상호 작용 명확성

입력된 상호 작용 쉽게 구별할 수 있도록 앱의 유용성 중요 하며 입력된 일관성 approachability, 상호 작용 방법의 검색 기능을 포함 합니다. 사용자는 relearning 없이 플랫폼 전체의 일반적인 상호 작용을 사용할 수 있어야 합니다. 앱 사용자 지정 입력 있으면 수 명확 하 게 전달 하 고 설명 합니다.

### <a name="device-impact"></a>장치 영향

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>품질 기준

|  가장  |  충족 |  실패 |
--- | --- | ---
|  입력된 상호 작용 방법을 제공 하는 Windows Mixed Reality를 사용 하 여 일관성이 [지침](interaction-fundamentals.md)합니다. 사용자 지정 입력 표준 입력 (대신 사용 하 여 표준 상호 작용)를 사용 하 여 중복 되지 않아야 하 고 명확 하 게 전달와 사용자에 게 설명 합니다. | 비슷하게 가장 좋지만 사용자 지정 입력 표준 입력된 메서드를 사용 하 여 중복 됩니다. 사용자 목표 및 앱 환경을 통해 진행률을 달성할 수 있습니다. | 입력된 메서드 또는 단추 매핑 이해 하기가 어렵습니다. 입력은 고도로 사용자 지정, 지침이 없습니다 표준 입력을 지원 하지 않습니다 또는 피로 편안 하 게 문제를 발생할 수 있습니다. | 

### <a name="how-to-measure"></a>측정 방법

* 앱에서 일관 된 [표준 메서드를 입력 합니다.](interaction-fundamentals.md)
* 앱 사용자 지정 입력 있으면 통해 명확 하 게 전달 됩니다.
* 첫 실행 경험
* 소개 화면
* 도구 설명
* 직접 coach
* 도움말 섹션
* 음성 전달

### <a name="recommendations"></a>권장 사항

* 가능 하면 표준 입력된 메서드를 사용 합니다.
* 비표준 입력된 메서드에 대 한 데모, 자습서 및 도구 설명을 제공 합니다.
* 앱 전체에서 일관 된 상호 작용 모델을 사용 합니다.

### <a name="resources"></a>리소스

#### <a name="documentation"></a>설명서

* [Windows MR 상호 작용 기본 사항](interaction-fundamentals.md)
* [상호 작용할 수 없는 개체](interactable-object.md)
* [대상으로 응시](gaze-targeting.md)
* [커서](cursors.md)
* [편안 함과 응시](comfort.md#gaze-direction)
* [제스처](gestures.md)
* [음성 입력](voice-input.md)
* [음성 디자인](voice-design.md)
* [컨트롤러 동작](motion-controllers.md)
* [포팅 가이드 Unity에 대 한 입력](input-porting-guide-for-unity.md)
* [Unity의 키보드 입력](keyboard-input-in-unity.md)
* [Unity에서 gaze](gaze-in-unity.md)
* [제스처와 Unity의 동작 컨트롤러](gestures-and-motion-controllers-in-unity.md)
* [Unity에서 음성 입력](voice-input-in-unity.md)
* [키보드, 마우스 및 DirectX에서 컨트롤러 입력](keyboard,-mouse,-and-controller-input-in-directx.md)
* [응시, 제스처 및 DirectX에서 컨트롤러 동작](gaze,-gestures,-and-motion-controllers-in-directx.md)
* [DirectX의 음성 입력](voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a>도구 및 자습서

* [사례 연구: 위해 더 많은 개인 컴퓨팅](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [연구를 캐스팅 합니다. HoloStudio UI와 상호 작용 디자인 학습](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [샘플 앱: 요소의 정기적 테이블](periodic-table-of-the-elements.md)
* [샘플 앱: 음력 모듈](lunar-module.md)
* [MR 입력 210: 응시](holograms-210.md)
* [MR 입력 211: 제스처](holograms-211.md)
* [MR 입력 212: 음성](holograms-212.md)

## <a name="interactable-objects"></a>상호 작용할 수 없는 개체

2D 추상 전 세계에서 이벤트를 트리거하는 데 사용 하는 비유를 오랫동안 단추입니다. 3 차원 혼합된 현실 세계에서 추상화를 더 이상이 환경으로 제한 될 필요가 없습니다. 아무 것도 이벤트를 트리거하는 상호 작용할 수 없는 개체 수 있습니다. 상호 작용할 수 없는 개체로 나타낼 수 있습니다 것과 테이블에는 커피 cup에서 공중에서 부동 풍선으로. 폼에 관계 없이 상호 작용할 수 없는 개체는 시각적 및 오디오 신호를 통해 사용자가 명확 하 게 인식할 수 있어야 합니다.

### <a name="device-impact"></a>장치 영향

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>품질 기준

|  가장  |  충족 |  실패 |
--- | --- | ---
|  폼에 관계 없이 상호 작용할 수 없는 개체는 시각적 및 오디오 신호를 통해 인식할 수 있는 세 가지 상태 간에: 유휴 상태, 선택한 대상으로 지정 합니다. "참조 말 것"을 선택 취소 하 고 일관 되 게 사용 환경 전체에서. 개체 크기를 조정 되며 대상으로 사용 가능한 오류에 대 한 허용 하도록 배포 됩니다. | 사용자 수으로 오디오 또는 시각적 피드백을 통해 상호 작용할 수 없는 개체를 인식할 수 있습니다 하 고 개체를 활성화 합니다. | 사용자 없는 visual 또는 오디오 신호 들어 상호 작용할 수 없는 개체를 인식할 수 없습니다. 상호 작용은 오류가 개체 간의 거리 또는 개체 크기 조정으로 인해 발생 하기 쉽습니다. | 

### <a name="how-to-measure"></a>측정 방법

* 상호 작용할 수 없는 개체는 '상호 작용할 수 없는';으로 인식할 수 단추, 메뉴 및 앱 특정 콘텐츠를 포함합니다. 일반적으로 없어야 visual 및 오디오 큐를 상호 작용할 수 없는 개체를 대상으로 합니다.

### <a name="recommendations"></a>권장 사항

* 상호 작용에 대 한 시각적 및 오디오 피드백을 사용 합니다.
* 각 입력 (유휴 상태, 대상, 선택 된) 상태에 대 한 시각적 피드백을 구분할 수 해야
* 상호 작용할 수 없는 개체를 확장 하 고 대상으로 사용 가능한 오류에 대 한 배치 해야 합니다.
* 그룹화 된 상호 작용할 수 없는 개체 (예: 메뉴 모음 또는 목록)을 대상으로 하는 것에 대 한 적절 한 간격이 있어야 합니다.
* 단추와 음성 명령을 지 원하는 메뉴 명령 키워드에 대 한 텍스트 레이블을 제공 해야 ("표시, 말")

### <a name="resources"></a>리소스

#### <a name="documentation"></a>설명서

* [상호 작용할 수 없는 개체](interactable-object.md)
* [Unity에서 텍스트](text-in-unity.md)
* [앱 바 및 경계 상자](app-bar-and-bounding-box.md)
* [음성 디자인](voice-design.md)

#### <a name="tools-and-tutorials"></a>도구 및 자습서

* [혼합된 현실 도구 키트-UX](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a>공간 검색

공간 매핑 데이터를 필요한 응용 프로그램을 자동으로 시간이 지남에 따라이 데이터를 수집 하려면 장치에 의존 하 고 사용자로 세션 전반에 걸쳐 활성 장치를 사용 하 여 해당 환경을 살펴봅니다. 완성도이 데이터의 품질을 다양 한 사용자가 수행 하는 탐색, 탐색 이후 경과 된 시간은 어떻게 양과 장치 영역을 검색 하므로 가구 등 문 개체가 이동 하는지 여부를 비롯 한 요인에 따라 달라 집니다. 대부분의 앱에서는 사용자 완결성과 공간 map의 품질을 개선 하기 위해 추가 단계를 수행 해야 하는지 여부를 판단 하려면 환경의 시작 공간 매핑 데이터를 분석 하 고 있습니다. 사용자가 검색 환경, 검색 환경 지침을 제공 해야의 선택을 취소 해야 합니다.

### <a name="device-impact"></a>장치 영향

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a>품질 기준

|  가장  |  충족 |  실패 |
--- | --- | ---
|  공간 메시의 시각화 알 검색 하는 사용자가 진행 중입니다. 사용자는 명확 하 게 할 일 및 검색의 시작 및 중지 시기를 알고 있습니다. | 공간 메시의 시각화를 제공 하지만 사용자 명확 하 게 알 수행할 작업 및 진행률 정보를 제공 하지. | 메시의 시각화가 없습니다. 지침 정보가을 where 절 또는 경우 검색을 시작/중지에 대 한 사용자에 게 제공 되지 않습니다. |

### <a name="how-to-measure"></a>측정 방법

* 필요한 공간을 검색 하는 동안 visual 및 오디오 지침을 확인할 수 있는 위치 및 시작 하는 시기 및 중지 검색을 나타내는 제공 됩니다.

### <a name="recommendations"></a>권장 사항

* 환경의 일부가 되도록 해야 사용자가 주변에 총 볼륨의 양을 나타냅니다.
* 검색을 시작 / 중지 진행률 표시기와 같은 경우 통신 합니다.
* 검색 하는 동안 메시의 시각화를 사용 합니다.
* 사용자가 찾고 전시실 이동에 시각 및 오디오 신호를 제공 합니다.
* 데이터를 개선 하기 위해 이동할 위치를 사용자에 게 알립니다. 대부분의 경우에 것이 사용자에 게 알리고 필요한지 않습니다 (예: 살펴보고 한계 조회 가구 뒤)를 가장 필요한 검사 품질을 얻기 위해.

### <a name="resources"></a>리소스

#### <a name="documentation"></a>설명서

* [대화방 검색 시각화](room-scan-visualization.md)
* [사례 연구: HoloLens의 공간 매핑 기능을 확장](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [사례 연구: HoloTour 공간 적절 하 게 디자인](case-study-spatial-sound-design-for-holotour.md)
* [사례 연구: 조각에는 몰입 형 환경을 만들기](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a>도구 및 자습서

* [혼합된 현실 도구 키트-UX](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a>방향 표시기

혼합된 현실 앱에서 콘텐츠 보기의 필드를 벗어난 것 같습니다 또는 실제 개체에 의해 폐색 합니다. 잘 설계 된 앱을 더 쉬워집니다 사용자가 표시 되지 않는 콘텐츠를 찾을 수 있습니다. 방향 표시기 경고 중요 한 콘텐츠를 사용자 및 사용자의 위치를 기준으로 내용에 대 한 지침을 제공 합니다. 지침 표시 되지 않는 콘텐츠 형식의 사운드 미터, 방향 화살표 또는 직접 시각적 걸릴 수 있습니다.

### <a name="device-impact"></a>장치 영향

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>품질 기준

|  가장  |  충족 |  실패 |
--- | --- | ---
|  직접 visual 및 오디오 신호는 관련 콘텐츠 보기의 필드 외부 사용자를 안내합니다. | 화살표 또는 콘텐츠의 일반적으로 사용자를 가리키는 일부 표시기입니다. | 관련 콘텐츠 보기의 필드를 외부 및 저하 되었거나 위치 지침이 없는 사용자에 게 제공 됩니다. | 

### <a name="how-to-measure"></a>측정 방법

* 외부 사용자 필드의 보기에서 관련 콘텐츠는 visual 및/또는 오디오 신호를 통해 검색할 수 있습니다.

### <a name="recommendations"></a>권장 사항

* 관련 콘텐츠는 사용자의 뷰 필드를 벗어날 때 방향 표시기 및 오디오 신호 콘텐츠에 사용자 가이드를 사용 합니다. 대부분의 경우에서 직접 시각적으로 알려줍니다 스타일러스가 기본 방향 화살표입니다.
* 커서로 방향 지표를 구축 되어야 합니다.

### <a name="resources"></a>리소스

* [Holographic 프레임](holographic-frame.md)

## <a name="data-loading"></a>데이터 로드

진행률 컨트롤은 긴 작업을 진행 중인 사용자에게 피드백을 제공합니다. 진행률 표시기가 표시 되 고 대기 시간 기간 수 있습니다 하는 것을 나타낼 수도 있습니다 하는 경우 사용자 앱 상호 작용할 수 없습니다는 의미할 수 있습니다.

### <a name="device-impact"></a>장치 영향

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>품질 기준

|  가장  |  충족 |  실패 |
--- | --- | ---
|  진행률 표시줄 또는 모든 데이터를 로드 하거나 처리 하는 동안 진행률을 보여 주는 링의 형태로 시각적 표시기를 애니메이션 합니다. 시각적 표시기 기간 대기 수 지침을 제공 합니다. | 사용자는 데이터 로드 진행에서 되는 기간 대기 수의 표시가 알림을 받습니다. | 데이터 로드 또는 5 초 보다 오래 된 작업에 대 한 프로세스 표시기는 없습니다. |

### <a name="how-to-measure"></a>측정 방법

* 데이터를 로드 하는 동안 5 초 넘게 빈 상태가 없는 확인 합니다.

### <a name="recommendations"></a>권장 사항

* 사용자는이 앱을 중단 했거나 충돌을 인식할 수 있습니다 때 모든 상황에서 진행률을 표시 하는 데이터 로드 애니메이터를 제공 합니다. 적절 한 규칙의 thumb은 5 초 넘게 걸리는 모든 '로드' 활동입니다.

### <a name="resources"></a>리소스

* [진행률 표시](progress.md)
