---
title: 혼합 현실에서 오디오
description: 혼합 현실에서 오디오는 UI 상호 작용의 사용자 신뢰도를 높이고 경험을 컨퍼런스 수 있습니다.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: 공간 음향, 서라운드 사운드, 3d 오디오, 3d 소리, 공간 오디오
ms.openlocfilehash: b939433daf80a95a11bc0e1ac2ffd75dfe0cf299
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181983"
---
# <a name="audio-in-mixed-reality"></a>혼합 현실에서 오디오
오디오는 혼합 현실에서 디자인 및 생산성의 필수적인 부분입니다. 사운드는 다음과 같습니다.
* 제스처 및 음성 조작에서 사용자 신뢰도를 늘립니다.
* 사용자에 게 다음 단계를 안내 합니다.
* 가상 개체를 실제 세계와 효과적으로 결합 합니다.

HoloLens를 비롯 한 혼합 현실 헤드셋의 짧은 대기 시간 헤드 추적은 고품질 HRTF 기반 spatialization을 지원 합니다. 응용 프로그램에서 오디오를 spatialize 수 있습니다.
* 시각적 요소에 주의를 기울여야 합니다.
* 사용자가 실제 환경에 대 한 인식을 유지 하도록 지원 합니다.

Acoustics는 혼합 현실 세계에 holograms을 더욱 깊이 있게 연결 합니다. 환경 및 개체 상태에 대 한 신호를 제공 합니다.

[오디오를 사용 하는 디자인의 자세한 예를](spatial-sound-design.md)참조 하세요.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/PTPvx7mDon4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="device-support"></a>장치 지원

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>기능</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (첫 번째 gen)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
    </tr>
     <tr>
        <td>Spatialization</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
     <tr>
        <td>Spatialization 하드웨어 가속</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="use-of-sounds-in-mixed-reality"></a>혼합 현실에서 소리 사용
[혼합 현실에서 소리를 사용](spatial-sound-design.md) 하려면 터치 및 키보드 및 마우스 응용 프로그램에서와 다른 방법이 필요 합니다. 핵심 설계 결정에는 spatialize 소리와 sonify에 대 한 상호 작용이 포함 됩니다. 이러한 결정은 사용자 신뢰도, 생산성 및 학습 곡선에 크게 영향을 주지 않습니다.

### <a name="case-studies"></a>사례 연구
HoloTour는 전 세계의 tourist 및 과거 사이트로 사용자를 이동 합니다. HoloTour 사례 연구는 [사운드 디자인](case-study-spatial-sound-design-for-holotour.md) 을 참조 하세요. 특수 마이크와 렌더링 설치 프로그램을 사용 하 여 주체 공간을 캡처 했습니다.

RoboRaid는 HoloLens의 에너지 슈팅입니다. RoboRaid 사례 연구를 [위한 사운드 디자인](case-study-using-spatial-sound-in-roboraid.md) 은 공간 오디오를 매우 극적으로 사용할 수 있도록 하기 위해 수행 된 디자인 선택 사항을 설명 합니다.

## <a name="spatialization"></a>Spatialization
Spatialization는 공간 오디오의 방향 구성 요소입니다. 7\.1 home 극장 설정의 경우 spatialization는 loudspeakers 간에 이동 하는 것 만큼 간단 합니다. 그러나 혼합 현실 헤드폰의 경우 정확도와 편안 하 게 HRTF 기반 기술을 사용 하는 것이 필수적입니다. Windows에서는 HRTF 기반 spatialization를 제공 하며이 지원은 HoloLens 2에서 하드웨어 가속 됩니다.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a>Spatialize?
Spatialization는 혼합 현실 응용 프로그램에서 많은 소리를 개선할 수 있습니다. Spatialization는 수신기의 헤드에서 소리를 가져와 세계에 배치 합니다. 응용 프로그램에서 spatialization를 효과적으로 사용 하는 방법에 대 한 제안은 [공간 음향 디자인](spatial-sound-design.md)을 참조 하세요.

### <a name="spatializer-personalization"></a>Spatializer 개인 설정
HRTFs는 frequency 스펙트럼 간의 수준 및 단계 차이를 조작 합니다. 실제 모델 및 사용자 헤드, 몸통 및 귀 셰이프 (pinnae)의 측정을 기반으로 합니다. 우리의 brains는 이러한 차이에 대응 하 여 소리로 인 한 방향을 제공 합니다.

모든 개인에는 고유한 귀 모양, 헤드 크기 및 귀 위치가 있습니다. 따라서 최상의 HRTFs가 사용자를 준수 합니다. Spatialization 정확도를 높이기 위해 HoloLens는 헤드셋 디스플레이에서 pupilary 거리 (IPD)를 사용 하 여 헤드 크기에 대 한 HRTFs를 조정 합니다.

### <a name="spatializer-platform-support"></a>Spatializer 플랫폼 지원
Windows에서는 [ISPATIALAUDIOCLIENT API](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound)를 통해 hrtfs를 비롯 한 spatialization을 제공 합니다. 이 API는 HoloLens 2 HRTF 하드웨어 가속을 응용 프로그램에 노출 합니다.

### <a name="spatializer-middleware-support"></a>Spatializer 미들웨어 지원
Windows ' HRTFs에 대 한 지원은 다음 타사 오디오 엔진에서 사용할 수 있습니다.
* [Unity 오디오 엔진 플러그 인](spatial-sound-in-unity.md)
* [Wtoaudio 엔진 플러그 인](https://www.audiokinetic.com/products/plug-ins/msspatial/)

## <a name="acoustics"></a>Acoustics
공간 오디오는 방향에 대 한 정보입니다. 다른 차원에는 폐색, 장애물, 반향, portalling 및 원본 모델링이 포함 됩니다. 이러한 차원을 통틀어 *acoustics*라고 합니다. Acoustics 없이 spatialized 소리는 인식 거리가 부족 합니다.

Acoustics 처리가의 범위는 단순에서 매우 복잡 합니다. 모든 오디오 엔진에서 지원 되는 간단한 반향을 사용 하 여 수신기 환경에 spatialized 소리를 푸시할 수 있습니다. [Project Acoustics](https://aka.ms/acoustics) 와 같은 Acoustics 시스템은 보다 풍부 하 고 뛰어난 Acoustics 처리를 제공 합니다. 프로젝트 Acoustics 벽, 도어 및 기타 장면 기 하 도형의 효과를 소리로 모델링할 수 있습니다. 이는 관련 장면 기 하 도형을 개발 시에 알려진 경우에 효과적으로 사용할 수 있는 옵션입니다.

## <a name="next-steps"></a>다음 단계
- [Unity의 공간 음향](spatial-sound-in-unity.md)
- [혼합 현실 응용 프로그램에서 소리를 사용 하는 방법](spatial-sound-design.md)
