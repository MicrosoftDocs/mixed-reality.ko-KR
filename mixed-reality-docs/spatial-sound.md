---
title: 공간 음향
description: 혼합된 현실 응용 프로그램에서 소리 공간을 사용 하 여 convincingly 3D 공간에서 소리를 배치할 수 있습니다.
author: hak0n
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: 공간 소리, 서라운드 사운드, 오디오 3d, 3d 공간, 사운드 오디오
ms.openlocfilehash: a30a484c4e47593556fbd1786158262551e11d22
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829919"
---
# <a name="spatial-sound"></a>공간 음향

개체는 시야를 벗어나는 경우 소리를 통해 우리 주변 진행 상황을 인식할 수 있습니다 우리가 하는 방법 중 하나입니다. Windows Mixed Reality 오디오 엔진 방향, 거리 및 환경 시뮬레이션을 사용 하 여 3D 소리를 시뮬레이션 하 여 혼합 현실 환경 청각적 구성 요소를 제공 합니다. 공간 소리를 사용 하 여 응용 프로그램에서 convincingly 3 차원 공간의 (구)에 소리를 배치 하는 개발자를 사용자 대 모든 수 있습니다. 그런 다음 실제 개체 또는 사용자의 환경에서 혼합된 현실 홀로그램에서 온 것 처럼 이러한 소리 친숙할 합니다. 가정 [홀로그램](hologram.md) 개체의 변경 되며 때로는 사운드 사운드 구성 요소를 통해 이익은 더 쉽게 만들고 더 몰입 형 환경을 새롭게 제공 합니다.

앱의 소리 모든 방향으로;에서 가져올 수 있습니다 홀로그램만에 표시 되는 시각적으로 사용자의 응시가 가리키고 있는 있지만 위에서 아래 뒤 쪽으로 등입니다. 현재 사용자의 보기에 없을 수도 있는 개체에 주목 하도록이 기능을 사용할 수 있습니다. 사용자는 소리 혼합 현실 세계에 있는 원본에서 페이지 수를 인식할 수 있습니다. 예를 들어 사용자가 개체에 더 가깝게 또는 개체에 가까워질수록 볼륨 증가 합니다. 마찬가지로 개체도 사용자 중심 또는 그 반대로 이동 하는 대로 공간 소리 소리 개체에서 직접 생성 되는 효과 제공 합니다.

<br>

>[!VIDEO https://www.youtube.com/embed/PTPvx7mDon4]

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
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (첫 번째 범용)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>몰입 형 헤드셋</strong></a></td>
    </tr>
     <tr>
        <td>공간 음향</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>(사용 하 여 헤드폰) ✔️</td>
    </tr>
</table>

## <a name="simulating-the-perceived-location-and-distance-of-sounds"></a>인식 된 위치와 소리의 거리를 시뮬레이션합니다.

분석 방법 사운드에 도달 하 여 모두 우리의 돌릴 뇌 결정 거리와 소리를 내보내는 개체의 방향입니다. HRTF (또는 Head 관련 전송 함수)는 귀 소리 공간에서 지점에서 수신 하는 방법을 지정 하는 스펙트럼 응답을 모델링 하 여이 상호 작용을 시뮬레이션 합니다. 공간 오디오 엔진 개인 설정 된 HRTFs를 사용 하 여 혼합된 현실 환경을 확장 하 고 다양 한 방향 및 거리에서 생성 되는 소리를 시뮬레이트합니다.

<br>

>[!VIDEO https://www.youtube.com/embed/aB3TDjYklmo]

왼쪽 또는 오른쪽 (방위) 오디오 신호 소리 각 귀 도착 시간 차이에서 발생 합니다. 신호 위/아래로 외부 귀 모양 (pinnae)으로 생성 된 스펙트럼 변경에서 발생 합니다. 지정 하 여 오디오에서 제공 되는 경우 시스템 경험을 시뮬레이션할 수 소리는 귀에 서로 다른 시간에 도착 합니다. HoloLens, 방위 공간화 개인화 된 동안 상승 시뮬레이션 기반 anthropometrics의 평균 집합에 대해 참고 합니다. 따라서 권한 상승 정확도 방위 정확도 보다 낮을 수 있습니다.

소리의 특징 존재 하는 환경에 따라 변경할 수도 있습니다. 예를 들어 있는 동굴에 shouting echo 효과 만드는 벽, 작업장 및 최대값이, 총알이 음성을 발생 합니다. 공간 소리 공간 모델 설정이 특정 오디오 환경에서 소리를 배치에 이러한 반사를 재현 합니다. 오디오 더 몰입 형 환경을 만들 수는 공간에서 소리의 시뮬레이션을 위해 사용자의 실제 위치와 일치 하도록이 설정을 사용할 수 있습니다.

## <a name="integrating-spatial-sound"></a>공간 소리를 통합합니다.

일반적인 원칙 혼합된 현실에 포함 되므로 [홀로그램](hologram.md) 사용자의 실제 또는 가상 환경에서 홀로그램에서 대부분의 소리 spatialized 해야 합니다. HoloLens에서 자연스럽 게 CPU 및 메모리 예산 고려 사항, 있지만 10-12 공간 사운드 음성 있습니다 ~ 12% 미만의 CPU (4 개 코어 중 하나의 ~ 70%)를 사용 하는 동안 사용할 수 있습니다. 공간 사운드 음성에 대 한 권장된 사용은 다음과 같습니다.
* Gaze 혼합 (특히 범위를 벗어난 경우 뷰 개체를 강조 표시). 홀로그램에서 사용자의 주의 필요한 경우 해당 홀로그램에서 소리 재생 (예: 가상 dog bark 해야 함). 그러면 사용자는 홀로그램 보기에 없는 경우 찾을 수 있습니다.
* 오디오 Haptics (touchless 상호 작용에 반응 오디오). 예를 들어, 사용자의 직접 또는 동작 컨트롤러 입력 및 제스처 프레임 종료 될 때 소리를 재생 합니다. 또는 홀로그램을 선택할 때 소리를 재생 합니다.
* 집중 교육 (앰비언트 소리 사용자 관련)입니다.

공간 소리를 사용 하 여 표준 스테레오 소리를 혼합 하는 것은 현실적인 환경 만들기에 적용 될 수 있지만, 스테레오 소리 공간에서 반사 (예: 공간 소리 미묘한 측면을 남겨 비교적 자동 수 있어야 한다는 것을 알아야 이기도 신호 거리)는 의견을 듣고 시끄러운 환경에서 어려울 수 있습니다.

Windows의 공간 사운드 엔진 48 k 샘플링 주기 재생만 지원합니다. Unity와 같은 대부분의 미들웨어를 자동으로 사운드 파일을 지원 되는 형식으로 변환 되지만 Windows 오디오 Api를 직접 사용 하는 경우의 효과 의해 지원 되는 형식에 콘텐츠를 형식에 맞게 하세요 것입니다.

## <a name="see-also"></a>참조
* [MR Spatial 220](holograms-220.md)
* [Unity의 공간 음향](spatial-sound-in-unity.md)
* [DirectX의 공간 음향](spatial-sound-in-directx.md)
* [공간 음향 디자인](spatial-sound-design.md)
