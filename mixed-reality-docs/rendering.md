---
title: 렌더링
description: Holographic 렌더링 실제에서 또는 가상 사용자가 만든 영역 내에서 정확 하 게 배치할지 여부를 앱이를 홀로그램 사용자 주변에 정확한 위치에 그릴 수 있도록 합니다.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 렌더링, 홀로그램
ms.openlocfilehash: 9d87af1b445bc6f730dd02bd7bd7f3aefe7f53db
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604822"
---
# <a name="rendering"></a>렌더링

Holographic 렌더링 실제에서 또는 가상 사용자가 만든 영역 내에서 정확 하 게 배치할지 여부를 앱이를 홀로그램 사용자 주변에 정확한 위치에 그릴 수 있도록 합니다. [홀로그램](hologram.md) 소리 및 조명 개체 수행 되 고 렌더링에는 앱이 빛을 추가할 수 있도록 합니다.

## <a name="device-support"></a>장치 지원

<table>
<tr>
<th>기능</th><th style="width:150px"><a href="hololens-hardware-details.md">HoloLens (첫 번째 범용)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></th>
</tr><tr>
<td>문서 이름</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr>
</table>

## <a name="holographic-rendering"></a>Holographic 렌더링

Holographic 렌더링을 아는 것이 중요 사용자가 실제 세계와 여 홀로그램 함께-볼 수 있는 HoloLens와 같은 투명 한 표시 또는 Windows Mixed Reality 몰입 형 헤드셋 블록 등 불투명 디스플레이 렌더링 하는 여부를 세계입니다.

사용 하 여 장치 **투명 한 표시**처럼 [HoloLens](hololens-hardware-details.md), 전 세계에 빛을 추가 합니다. 검정 픽셀이 원색 픽셀 점점 불투명 한 것은 완전히 투명 하 게 됩니다. 디스플레이에서 조명 조명이 실제 환경에서 추가 되 면 때문에 흰색 픽셀은 다소 반투명 합니다.

Stereoscopic 렌더링에서는 프로그램 홀로그램 하나 깊이 암시 하는 동안 추가 [효과 토대가](interaction-fundamentals.md) 을 보러 오세요 쉽게 어떤 화면을 홀로그램 거의 사용자 제공할 수 있습니다. 접지 기술 중 하나 주변 화면에서를 홀로그램 주위에 빛을 추가한 다음이 광선에 대해 그림자를 렌더링 하는 것입니다. 이러한 방식으로 환경에서 빛을 뺄에 그림자가 나타납니다. [공간 소리](spatial-sound.md) 거리와를 홀로그램의 상대 위치에 대 한 사용자가 이유를 수 있도록 다른 매우 중요 깊이 암시 될 수 있습니다.

사용 하 여 장치 **불투명 표시**처럼 [Windows Mixed Reality 몰입 형 헤드셋](immersive-headset-hardware-details.md), 세계 차단 합니다. 검정 픽셀이 검은색, 되며 다른 색이 사용자에 게 해당 색으로 표시 됩니다. 앱 이므로 사용자가 편리 하 게 환경을 상수 새로 고침 빈도 유지 하기 위해 더욱 중요 한 모든 사용자에 게 표시를 렌더링 하는 경우

## <a name="predicted-rendering-parameters"></a>렌더링 매개 변수를 예측 합니다.

혼합 현실 헤드셋 (HoloLens 및 몰입 형 헤드셋) 위치 및 해당 환경 기준으로 사용자의 헤드의 방향을 지속적으로 추적 합니다. 다음 프레임을 준비 하 고 시작 하는 앱, 시스템 사용자의 헤드 될 위치 나중에 프레임을 디스플레이에 표시 되는 정확한 시점을 예측 합니다. 이 예측에 따라 시스템 뷰 및 프로젝션 변환을 해당 프레임에 대 한 사용을 계산 합니다. 응용 프로그램 **올바른 결과 생성 하려면 이러한 변환을 사용 해야**시스템 제공 변환 사용 되지 않는 경우 결과 이미지는 실제로 사용자 뜨거움을 올바르게 정렬 되지 됩니다.

정확 하 게 새 프레임을 표시 하는 도달 하는 경우 예측할 시스템 측정 되는 지속적으로 앱의 렌더링 파이프라인의 효과적인 종단 간 대기 시간을 참고 합니다. 시스템은 렌더링 파이프라인의 길이 조정 하는 동안 파이프라인 최대한 짧게 유지 하 여 홀로그램 안정성을 추가로 개선할 수 있습니다.

고급 기술을 사용 하 여 시스템 예측을 보강 하는 응용 프로그램에는 시스템 뷰 및 프로젝션 변환을 재정의할 수 있습니다. 이러한 앱 해야 해야 여전히 변환을 사용 하 여 시스템 제공 해당 사용자 지정 변환에 대 한 기준으로 의미 있는 결과 생성 하기 위해.

## <a name="other-rendering-parameters"></a>다른 렌더링 매개 변수

프레임을 렌더링 하는 경우 시스템 응용 프로그램 그려야 백 버퍼 뷰포트를 지정 합니다. 이 뷰포트는 종종 프레임 버퍼의 전체 크기 보다 작아야 합니다. 뷰포트 크기에 관계 없이 프레임 응용 프로그램에서 렌더링 된 후 시스템은 고급 이미지를 표시 하는 전체를 입력 합니다.

하는 응용 프로그램 자체에 필요한 새로 고침 빈도 렌더링할 수 없습니다에 대 한 [시스템 렌더링 매개 변수를 구성할 수 있습니다](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) 메모리 압력 및/또는 향상 된 픽셀 별칭을 지정 하는 대신 렌더링 비용을 줄일 수 있습니다. 백 버퍼 형식을 변경할 수도 있습니다, 일부 앱에 대해 메모리 대역폭 및 픽셀 처리량을 향상 시킬 수 있습니다.

렌더링 꼭지점이 절 두 체, 확인 및 framerate는 앱을 렌더링 하 라는 메시지가 표시 프레임 간에 변경 될 수 있습니다 하 고 왼쪽 및 오른쪽 눈 간에 다를 수 있습니다. 예를 들어, [혼합 현실 캡처](mixed-reality-capture.md) (MRC) 활성 상태 인지와 [사진/비디오 카메라 구성 보기](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) 옵트인-에 없는 나와 눈을 더 큰 FOV 또는 확인을 사용 하 여 렌더링 될 수 있습니다.

지정 된 모든 프레임을 앱에 대 한 *해야* 보기 변환, 프로젝션 변환 및 시스템에서 제공 하는 뷰포트 확인을 사용 하 여 렌더링 합니다. 또한 응용 프로그램은 모든 렌더링/view 매개 변수-프레임에서 고정 된 상태로 유지 됩니다을 가정 하지 해야 합니다. 시스템의 상태와 사용자의 실제 이동을 항상 제한이 적용 되도록 엔진 Unity와 같은 이러한 모든 변환을를 자신의 카메라 개체에서 처리 합니다. 추가 앱 (예:를 통해 전 세계 스틱을 gamepad에서)를 통해 사용자의 가상 움직임을 허용 하는 경우 사용자의 가상 및 실제 동작을 반영 하기 위해 카메라를 일으키는 부모 "장치" 개체 이동, 카메라 위에 추가할 수 있습니다. 적절 한 호출 하 여 시스템을 알려줍니다 해야 앱 보기 변환, 프로젝션 변환 또는 시스템에서 제공 하는 뷰포트 차원과 수정 [API를 재정의](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicCameraPose#Windows_Graphics_Holographic_HolographicCameraPose)합니다.

Holographic 렌더링 프로그램의 안정성을 강화 하려면 앱 제공 해야 Windows 각 프레임 렌더링에 사용 되는 깊이 버퍼입니다. 앱에서 깊이 버퍼를 제공 하는 경우를 미터 단위로 표현 하는 깊이 사용 하 여 일관 된 깊이 값 있어야 합니다. 이 인해 사용자의 헤드 최종적으로 예측 된 위치에서 약간 오프셋 하는 경우 콘텐츠를 더 잘 안정화 픽셀당 깊이 데이터를 사용 하도록 시스템입니다. 깊이 버퍼를 제공할 수 없는 경우 대신 제공 해야 포커스 지점 및 표준, 대부분의 내용을 통해 있는 평면을 정의 합니다. 깊이 버퍼 및 포커스 평면을 모두 제공 하는 경우 시스템 둘 다 사용할 수 있습니다. 특히 깊이 버퍼와 앱 동작에 있는 홀로그램 표시 되 면 속도 벡터를 포함 하는 포커스 지점을 제공 유용할 수 있습니다.

하위 수준 세부 정보 여기, 체크 아웃 합니다 [DirectX 렌더링](rendering-in-directx.md) 문서.

## <a name="holographic-cameras"></a>Holographic 카메라

Windows Mixed Reality의 개념을 도입 된 **holographic 카메라**합니다. Holographic 카메라 3D 그래픽 텍스트에 있는 기존 카메라에 비슷합니다.: 외부의 정의 (위치 및 방향) 및 내장 카메라 속성 (예: 뷰 필드) 가상 3D 장면을 보는 데 사용 합니다. 기존 3D 카메라, 달리 응용 프로그램 위치, 방향 및 카메라의 기본 속성을 제어 되지 않습니다. 대신, 위치 및 holographic 카메라의 방향 암시적으로 사용자의 이동 하 여 제어 됩니다. 사용자의 이동 보기 변환을 통해 프레임별으로 별로 응용 프로그램을 통해 릴레이 됩니다. 마찬가지로, 카메라의 기본 속성 보정된 광학 장치에서 정의 되 고 릴레이 프레임별 프로젝션 변환을 통해.

일반적 단일 스테레오 카메라에 대 한 앱을 렌더링 수 됩니다. 그러나 강력한 렌더링 루프가 여러 카메라를 지원 해야 및 mono와 스테레오 카메라를 지원 해야 합니다. 시스템 앱 사용자와 같은 기능을 활성화 하는 경우 대체 관점에서 렌더링을 요청할 수 있습니다 예를 들어 [혼합 현실 캡처](mixed-reality-capture.md) (MRC) 해당 헤드셋의 형태에 따라 합니다. 여러 카메라를 지원할 수 있는 앱 하 여 가져올 [에서 옵트인](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) 에 [종류](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) 지원할 수 있는 카메라의 합니다.

## <a name="volume-rendering"></a>볼륨 렌더링

의료 렌더링할 때 MRI 또는 3d에서 볼륨을 엔지니어링 [볼륨 렌더링](volume-rendering.md) 기술을 자주 사용 됩니다. 사용자가 헤드를 이동 하면 키 각도에서 이러한 볼륨 보기 자연스럽 게 수 이러한 기술은 혼합된 현실에서 특히 흥미로운 될 수 있습니다.

## <a name="supported-resolutions-on-hololens-1st-gen"></a>HoloLens에 지원 되는 해상도 (첫 번째 범용)
> [!NOTE]
> 나중에이 문서에 제공 하는 자세한 업데이트 됩니다. [업데이트 목록을 보려면](release-notes-april-2018.md)

* 지원 되는 현재 및 최대 해상도의 속성을 [구성 보기](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration)합니다. HoloLens는 720p (1268 x 720)가 최대 해상도를 기본적으로 설정 됩니다.
* 가장 낮은 지원 되는 뷰포트 크기는 50 %720p 360p (634 x 360)는입니다. HoloLens의 0.5 ViewportScaleFactor입니다.
* 540 p 보다 낮은 아무것도 **좋지** visual 저하로 인해 bottle necks 픽셀 채우기 비율에서을 식별 하는 데 사용할 수 있습니다.

## <a name="supported-resolutions-on-hololens-2"></a>HoloLens 2에서 지원 되는 해상도

> [!NOTE]
> HoloLens 2 관련 된 자세한 지침 [예정](index.md#news-and-notes)합니다.


## <a name="see-also"></a>참조
* [홀로그램 안정성](hologram-stability.md)
* [DirectX의 렌더링](rendering-in-directx.md)