---
title: 렌더링
description: Holographic 렌더링을 사용 하면 응용 프로그램이 실제 세계에 정확 하 게 배치 되었는지 아니면 사용자가 만든 가상 영역 내에서 정확 하 게 배치 되었는지 여부에 관계 없이 사용자를 대상으로 하는 위치에서 홀로그램을 그릴 수 있습니다.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 렌더링, 홀로그램
ms.openlocfilehash: 45713fd7a30fc55a799da7e89ef52aff8f7eec46
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415407"
---
# <a name="rendering"></a>렌더링

Holographic 렌더링을 사용 하면 응용 프로그램이 실제 세계에 정확 하 게 배치 되었는지 아니면 사용자가 만든 가상 영역 내에서 정확 하 게 배치 되었는지 여부에 관계 없이 사용자를 대상으로 하는 위치에서 홀로그램을 그릴 수 있습니다. [Holograms](hologram.md) 는 소리 및 조명의 개체입니다. 렌더링을 사용 하면 지 수를 사용 하 여 빛을 추가할 수 있습니다.

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
        <td><a href="hololens-hardware-details.md"><strong>HoloLens(1세대)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
    </tr>
     <tr>
        <td>렌더링</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="holographic-rendering"></a>Holographic 렌더링

Holographic 렌더링의 핵심은 사용자에 게 실제 세계와 holograms를 함께 볼 수 있도록 하는 HoloLens와 같은 표시 간 표시로 렌더링 하는지, 아니면 차단 되는 Windows Mixed Reality 몰입 형 헤드셋과 같은 불투명 표시로 렌더링 하는지 여부를 알고 있습니다. 전 세계입니다.

**보기 표시**를 사용 하는 장치 (예: [HoloLens](hololens-hardware-details.md))는 전 세계에 조명을 추가 합니다. 검은색 픽셀은 완전히 투명 하지만 밝은 픽셀은 점차 불투명 합니다. 디스플레이의 조명이 실제 세계의 조명에 추가 되기 때문에 흰색 픽셀은 약간 반투명 합니다.

Stereoscopic 렌더링은 holograms에 대 한 깊이 있는 한 가지 큐를 제공 하는 반면, [접지 효과](interaction-fundamentals.md) 를 추가 하면 홀로그램이 가까이 있는 표면을 더 쉽게 볼 수 있습니다. 한 가지 접지 기술은 근처 표면에서 홀로그램 주위에 광선을 추가한 다음이 광선에 대해 그림자를 렌더링 하는 것입니다. 이러한 방식으로 섀도는 환경에서 광원을 빼는 것 처럼 보입니다. [공간 사운드](spatial-sound.md) 는 다른 매우 중요 한 깊이 큐로, 사용자가 홀로그램의 거리와 상대 위치에 대 한 이유를 알려 줍니다.

[Windows Mixed Reality 몰입 형 헤드셋](immersive-headset-hardware-details.md)과 같이 **불투명 디스플레이**를 사용 하는 장치는 전 세계를 차단 합니다. 검정 픽셀은 검정 픽셀이 고 다른 색은 사용자에 게 해당 색으로 표시 됩니다. 응용 프로그램은 사용자에 게 표시 되는 모든 항목을 렌더링 해야 합니다. 이렇게 하면 사용자가 편안 하 게 사용할 수 있도록 일정 한 새로 고침 빈도를 유지 관리 하는 것이 훨씬 더 중요 합니다.

## <a name="predicted-rendering-parameters"></a>예측 된 렌더링 매개 변수

혼합 현실 헤드셋 (HoloLens 및 몰입 형 헤드셋)은 주변에 상대적인 사용자 헤드의 위치와 방향을 지속적으로 추적 합니다. 응용 프로그램에서 다음 프레임의 준비를 시작 하면 시스템은 사용자의 헤드가 화면에 표시 되는 순간에 사용자의 헤드가 나중에 표시 되는 위치를 예측 합니다. 이 예측을 기반으로 시스템은 해당 프레임에 사용할 뷰 및 프로젝션 변환을 계산 합니다. 응용 프로그램에서 **이러한 변환을 사용 하 여 올바른 결과를 생성 해야 합니다**. 시스템에서 제공 하는 변환을 사용 하지 않는 경우 결과 이미지가 실제 세계와 일치 하지 않아 사용자 discomfort이 발생 합니다.

새 프레임이 디스플레이에 도달 하는 시기를 정확 하 게 예측 하기 위해 시스템은 응용 프로그램의 렌더링 파이프라인에 대 한 효과적인 종단 간 대기 시간을 지속적으로 측정 합니다. 시스템이 렌더링 파이프라인의 길이로 조정 되는 동안 해당 파이프라인을 가능한 한 짧게 유지 하 여 홀로그램의 안정성을 향상 시킬 수 있습니다.

고급 기술을 사용 하 여 시스템 예측을 보강 하는 응용 프로그램은 시스템 뷰 및 프로젝션 변환을 재정의할 수 있습니다. 이러한 응용 프로그램은 의미 있는 결과를 생성 하기 위해 사용자 지정 변환의 기반으로 시스템 제공 변환을 계속 사용 해야 합니다.

## <a name="other-rendering-parameters"></a>기타 렌더링 매개 변수

프레임을 렌더링할 때 시스템은 응용 프로그램에서 그려야 하는 백 버퍼 뷰포트를 지정 합니다. 이 viewport는 프레임 버퍼의 전체 크기 보다 작은 경우가 많습니다. 응용 프로그램에서 프레임을 렌더링 한 후에는 뷰포트 크기에 관계 없이 이미지를 확장 하 여 전체 화면을 채웁니다.

자동으로 필요한 새로 고침 속도로 렌더링할 수 없는 응용 프로그램의 경우 메모리 압력을 줄이고 픽셀 앨리어싱을 늘리기 위해 [시스템 렌더링 매개 변수를 구성할 수 있습니다](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) . 백 버퍼 형식을 변경할 수도 있습니다 .이 경우 일부 앱에서 메모리 대역폭과 픽셀 처리량을 향상 시키는 데 도움이 될 수 있습니다.

앱이 렌더링 되는 것으로 확인 되는 렌더링의 대/소문자, 해상도 및 프레임 속도가 프레임에서 프레임으로 변경 될 수도 있으며, 왼쪽 및 오른쪽 눈에 걸쳐 달라질 수도 있습니다. 예를 들어 [혼합 현실 캡처](mixed-reality-capture.md) (mrc)가 활성 상태이 고 [photo/video 카메라 보기 구성을](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) 옵트인 (opt in) 할 수 없는 경우에는 한 눈이 더 큰 FOV 또는 해상도로 렌더링 될 수 있습니다.

지정 된 프레임의 경우 응용 프로그램은 시스템에서 제공 하는 뷰 변환, 프로젝션 변환 및 뷰포트 해상도를 사용 하 여 렌더링 *해야 합니다* . 또한 응용 프로그램은 렌더링 또는 뷰 매개 변수가 프레임-프레임에서 고정 된 상태로 유지 되는 것으로 가정해 서는 안 됩니다. Unity와 같은 엔진은 사용자의 실제 이동과 시스템 상태가 항상 적용 되도록 이러한 모든 변환을 자체 카메라 개체에서 처리 합니다. 응용 프로그램에서 전 세계 사용자의 가상 이동을 허용 하는 경우 (예: 게임 패드에서 엄지 스틱 사용), 부모 rig 개체를 이동 하는 카메라 위에 부모 rig 개체를 추가할 수 있습니다. 이렇게 하면 카메라는 사용자의 가상 및 실제 움직임을 반영 합니다. 응용 프로그램이 시스템에서 제공 하는 뷰 변환, 프로젝션 변환 또는 뷰포트 차원을 수정 하는 경우 적절 한 [재정의 API](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicCameraPose#Windows_Graphics_Holographic_HolographicCameraPose)를 호출 하 여 시스템에 알려야 합니다.

Holographic 렌더링의 안정성을 향상 시키기 위해 앱은 렌더링에 사용 되는 깊이 버퍼를 각 프레임에 제공 해야 합니다. 앱에서 깊이 버퍼를 제공 하는 경우에는 카메라에서 미터 단위로 표시 된 깊이 있는 깊이 값이 있어야 합니다. 이를 통해 사용자의 헤드가 예측 위치에서 약간의 오프셋을 종료 하는 경우 시스템에서 픽셀 당 깊이 데이터를 사용 하 여 안정화 된 콘텐츠를 더 효율적으로 사용할 수 있습니다. 깊이 버퍼를 제공할 수 없는 경우에는 대부분의 콘텐츠를 잘라내는 평면을 정의 하는 포커스 지점과 법선을 제공할 수 있습니다. 깊이 버퍼와 포커스 평면이 모두 제공 되는 경우 시스템은 두 가지 모두를 사용할 수 있습니다. 특히 응용 프로그램에서 동작 중인 holograms 표시 하는 경우 속도 벡터를 포함 하는 집중 지점과 깊이 버퍼를 모두 제공 하는 것이 유용 합니다.

항목에 대 한 하위 수준 세부 정보는 [DirectX의 렌더링](rendering-in-directx.md) 문서를 참조 하세요.

## <a name="holographic-cameras"></a>Holographic 카메라

Windows Mixed Reality에서는 **holographic 카메라**의 개념을 소개 합니다. Holographic 카메라는 3D 그래픽 텍스트에 있는 전통적인 카메라와 유사 합니다. 외부 (위치 및 방향)와 내장 카메라 속성을 모두 정의 합니다. (예: 뷰 필드는 가상 3D 장면을 보는 데 사용 됩니다.) 기존의 3D 카메라와 달리 응용 프로그램은 카메라의 위치, 방향 및 기본 속성을 제어 하지 않습니다. 대신 holographic 카메라의 위치와 방향은 사용자의 움직임에 의해 암시적으로 제어 됩니다. 사용자의 이동은 뷰 변환을 통해 프레임 단위로 응용 프로그램에 릴레이 됩니다. 마찬가지로 카메라의 내장 속성은 장치의 보정 된 광학에서 정의 되며 프로젝션 변환을 통해 프레임별로 릴레이 됩니다.

일반적으로 응용 프로그램은 단일 스테레오 카메라에 대해 렌더링 됩니다. 그러나 강력한 렌더링 루프는 여러 카메라를 지원 하며 mono 및 스테레오 카메라를 모두 지원 합니다. 예를 들어, 사용자가 해당 하는 헤드셋의 셰이프에 따라 mrc ( [mixed reality capture](mixed-reality-capture.md) )와 같은 기능을 활성화 하는 경우 시스템은 대체 큐브 뷰에서 렌더링 하도록 응용 프로그램을 요청할 수 있습니다. 여러 카메라를 지원할 수 있는 응용 프로그램에서는 지원할 수 있는 카메라 [종류](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) 에 [옵트인](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) 하 여 해당 응용 프로그램을 가져옵니다.

## <a name="volume-rendering"></a>볼륨 렌더링

3D에서 의료 MRIs 또는 엔지니어링 볼륨을 렌더링 하는 경우 [볼륨 렌더링](volume-rendering.md) 기술이 종종 사용 됩니다. 이러한 기술은 혼합 현실에서 특히 유용할 수 있습니다. 사용자는 단순히 헤드를 이동 하 여 키 각도에서 이러한 볼륨을 자연스럽 게 볼 수 있습니다.

## <a name="supported-resolutions-on-hololens-1st-gen"></a>HoloLens에서 지원 되는 해상도 (첫 번째 gen)
> [!NOTE]
> 더 많은 업데이트가 곧 출시 될 예정입니다. [업데이트 목록 보기](release-notes-april-2018.md)

* 현재 및 지원 되는 최대 해상도는 [뷰 구성](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration)의 속성입니다. HoloLens는 기본적으로 최대 해상도 인 720p (1268x720)로 설정 됩니다.
* 지원 되는 가장 낮은 뷰포트 크기는 360p (634x360) 인 720p의 50%입니다. HoloLens에서 0.5의 ViewportScaleFactor입니다.
* 540p 보다 낮은 항목은 시각적 저하로 인해 **권장 되지** 않지만, necks를 픽셀 채우기 속도로 식별 하는 데 사용할 수 있습니다.

## <a name="supported-resolutions-on-hololens-2"></a>HoloLens 2에서 지원 되는 해상도

> [!NOTE]
> HoloLens 2에 대 한 추가 지침은 [곧](index.md#news-and-notes)제공 될 예정입니다.


## <a name="see-also"></a>참조
* [홀로그램 안정성](hologram-stability.md)
* [DirectX의 렌더링](rendering-in-directx.md)
