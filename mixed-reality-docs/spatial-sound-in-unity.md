---
title: Unity의 공간 소리
description: Unity 장면 내의 특정 3D 점에서 공간 소리를 재생 합니다.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, 공간 음향, HRTF, 방 크기
ms.openlocfilehash: af3f1486c3e931ad93d7b8960d822653ec740c12
ms.sourcegitcommit: ee8c7e821cb337cbccd8af64b13ee5f50109a776
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80082037"
---
# <a name="spatial-sound-in-unity"></a>Unity의 공간 소리

이 페이지는 Unity의 공간 소리에 대 한 리소스에 연결 됩니다.

## <a name="spatializer-options"></a>Spatializer 옵션
혼합 현실 응용 프로그램에 대 한 Spatializer 옵션은 다음과 같습니다.
* *MS HRTF Spatializer*입니다. Unity는 *Windows Mixed Reality* 선택적 패키지의 일부로이를 제공 합니다.
  * 이는 높은 비용의 단일 소스 아키텍처에서 CPU에 실행 됩니다.
  * 이는 이전에 원본 HoloLens 응용 프로그램과의 호환성을 위해 제공 됩니다.
* *Microsoft Spatializer*입니다. [Microsoft Spatializer GitHub 리포지토리에서](https://github.com/microsoft/spatialaudio-unity)사용할 수 있습니다.
  * 이는 저렴 한 ' 다중 원본 ' 아키텍처를 사용 합니다.
  * HoloLens 2에서이는 하드웨어 가속기로 오프 로드 됩니다.

새 응용 프로그램의 경우 *Microsoft Spatializer*를 권장 합니다.

## <a name="enable-spatialization"></a>Spatialization 사용

[Unity 용 NuGet](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) 을 사용 하 여 _SpatialAudio. Spatializer_ 을 설치 하 고 프로젝트의 오디오 설정에서 **microsoft Spatializer** 를 선택 합니다. 그리고 나서 다음을 수행합니다.
* 계층의 개체에 **오디오 소스** 연결
* **Spatialization 사용** 확인란을 선택 합니다.
* **공간 Blend** 슬라이더를 ' 1 '로 이동
* 개발자 워크스테이션에서 공간 오디오를 사용 하도록 설정 했는지 확인 합니다. 작업 표시줄에서 볼륨 아이콘을 마우스 오른쪽 단추로 클릭 하 고 공간 사운드가 "꺼짐" 이외의 항목으로 설정 되었는지 확인 하 여 사용 하도록 설정 합니다. HoloLens 2에 대 한 최고의 정보를 얻으려면 **헤드폰 용 Windows Sonic**을 선택 합니다.

>[!NOTE]
>종속성 중 하나가 누락 되어 SpatialAudio에서 플러그 인 Spatializer를 로드 하지 못하는 경우 Unity에 오류가 발생 하는 경우 최신 버전의 [Microsoft Visual C++ 재배포 가능 패키지가](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) PC에 설치 되어 있는지 확인 합니다.

자세한 내용은 다음 항목을 참조하세요.
* [Microsoft spatializer GitHub 리포지토리](https://github.com/microsoft/spatialaudio-unity)
* [Microsoft의 spatializer 자습서](unity-spatial-audio-ch1.md)
* [Unity의 오디오 소스 설명서](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [Unity의 spatializer 설명서](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a>거리 기반 감쇠
Unity의 기본 거리 기반 감소는 로그 rolloff를 사용 하 여 최소 거리가 1 미터이 고 최대 거리가 500 미터입니다. 이러한 설정은 시나리오에 대해 적용 될 수 있으며, 원본이 너무 빨리 또는 너무 느리게 경우 수 있습니다. 자세한 내용은 다음 항목을 참조하세요.
* 권장 설정에 대해 [혼합 현실에서 설계](spatial-sound-design.md) 합니다.
* 이러한 곡선을 설정 하는 방법에 대 한 지침은 [Unity의 오디오 소스 설명서](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) 를 참조 하세요.

## <a name="reverb"></a>잔
_Microsoft Spatializer_ 는 기본적으로 사후 Spatializer 효과를 사용 하지 않도록 설정 합니다. Spatialized 원본에 대해 반향 및 기타 효과를 사용 하도록 설정 하려면 다음을 수행 합니다.
* 각 원본에 **대화방 효과 보내기 수준** 구성 요소 연결
* 각 원본에 대 한 전송 수준 곡선을 조정 하 여 효과 처리를 위해 그래프로 다시 보낸 오디오의 이득을 제어 합니다.

자세한 내용은 [spatializer 자습서의 5 장](unity-spatial-audio-ch5.md) 을 참조 하세요.

## <a name="unity-spatial-sound-examples"></a>Unity 공간 음향 예
Unity의 공간 음향 예는 다음을 참조 하세요.
* [MRTK 데모](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* [Microsoft Spatializer 샘플 프로젝트](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)

## <a name="next-steps"></a>다음 단계
* [혼합 현실에서의 소리 디자인](spatial-sound-design.md)
* [Microsoft의 spatializer 자습서](unity-spatial-audio-ch1.md)

