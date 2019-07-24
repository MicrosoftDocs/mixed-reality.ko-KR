---
title: Unity의 공간 소리
description: Unity 장면 내의 특정 3D 점에서 가져온 공간 소리를 재생 합니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, 공간 음향, HRTF, 방 크기
ms.openlocfilehash: e2b321d7086314a14a940d57aa17e67636c758b8
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63549074"
---
# <a name="spatial-sound-in-unity"></a>Unity의 공간 소리

이 항목에서는 Unity 프로젝트에서 공간 소리를 사용 하는 방법에 대해 설명 합니다. 이 파일은 필수 플러그 인 파일 뿐만 아니라 공간 사운드를 사용 하는 Unity 구성 요소 및 속성을 다룹니다.

## <a name="enabling-spatial-sound-in-unity"></a>Unity에서 공간 소리 사용

Unity의 공간 사운드는 audio spatializer 플러그 인을 사용 하 여 설정 됩니다. 플러그 인 파일은 Unity에 직접 번들로 제공 되므로 공간 소리를 사용 하도록 설정 하는 것은 **> 프로젝트 설정 > 오디오를 편집** 하 고 검사기의 **Spatializer 플러그 인** 을 **MS hrtf Spatializer**로 변경 하는 것 만큼 쉽습니다. Microsoft spatializer는 현재 48000Hz만 지원 하기 때문에 시스템 출력 장치를 48000로 설정 하지 않은 경우에만 HRTF 오류가 발생 하지 않도록 시스템 샘플 주기를 48000으로 설정 해야 합니다.

![오디오 관리자 검사기](images/audio-250px.png)<br>
*오디오 관리자 검사기*

이제 Unity 프로젝트가 공간 소리를 사용 하도록 구성 되었습니다.

>[!NOTE]
>개발에 Windows 10 PC를 사용 하지 않는 경우 편집기 또는 장치 (Windows 10 SDK를 사용 하는 경우에도)에서 공간 소리를 얻지 못합니다.

## <a name="using-spatial-sound-in-unity"></a>Unity에서 공간 소리 사용

공간 사운드는 오디오 원본 구성 요소에 대 한 세 가지 설정을 조정 하 여 Unity 프로젝트에서 사용 됩니다. 다음 단계는 오디오 원본 구성 요소에 대 한 공간 소리를 구성 합니다.
* **계층** 패널에서 **오디오 소스가**연결 된 게임 개체를 선택 합니다.
* **검사기** 패널의 **오디오 원본** 구성 요소 아래에서
    * **Spatialize** 옵션을 선택 합니다.
    * **공간 Blend** 를 **3d** (숫자 값 1)로 설정 합니다.
    * 최상의 결과를 위해서는 **3D 소리 설정** 을 확장 하 고 **볼륨 Rolloff** 을 **사용자 지정 Rolloff**로 설정 합니다.

![오디오 원본을 보여 주는 Unity의 검사기 패널](images/audiosource.png)<br>
*오디오 원본을 보여 주는 Unity의 검사기 패널*

이제 프로젝트가 프로젝트 환경 내에 실제로 존재 합니다.

[공간 음향 디자인 지침](spatial-sound-design.md)에 대해 잘 알고 있는 것이 좋습니다. 이러한 지침은 오디오를 프로젝트에 원활 하 게 통합 하 고 사용자가 만든 환경에 사용자를 컨퍼런스 하는 데 도움이 됩니다.

## <a name="setting-spatial-sound-settings"></a>공간 음향 설정 설정

Microsoft 공간 사운드 플러그 인은 오디오 시뮬레이션에 대 한 추가 제어를 허용 하기 위해 오디오 소스 별로 설정할 수 있는 추가 매개 변수를 제공 합니다. 이 매개 변수는 시뮬레이트된 대화방의 크기입니다.

### <a name="room-size"></a>방 크기

공간 사운드로 시뮬레이션 되는 공간의 크기입니다. 회의실의 대략적인 크기는입니다. 작음 (사무실에서 작은 회의실), 중형 (대량 회의실) 및 큼 (auditorium). 또한 실내 크기를 none으로 지정 하 여 실외 환경을 시뮬레이션할 수 있습니다. 기본 방 크기는 작음입니다.

### <a name="example"></a>예제

MixedRealityToolkit for Unity는 공간 음향 설정을 쉽게 설정 하는 정적 클래스를 제공 합니다. 이 클래스는 [MixedRealityToolkit\SpatialSound 폴더](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) 에서 찾을 수 있으며 프로젝트의 모든 스크립트에서 호출할 수 있습니다. 프로젝트의 각 오디오 원본 구성 요소에서 이러한 매개 변수를 설정 하는 것이 좋습니다. 다음 예에서는 연결 된 오디오 소스에 대 한 중간 방 크기를 선택 하는 방법을 보여 줍니다.

```cs
AudioSource audioSource = gameObject.GetComponent<AudioSource>()

if (audioSource != null) {
    SpatialSoundSettings.SetRoomSize(audioSource, SpatialMappingRoomSizes.Medium);
}
```

### <a name="directly-accessing-parameters-from-unity"></a>Unity에서 매개 변수 직접 액세스

MixedRealityToolkit에서 뛰어난 오디오 도구를 사용 하지 않으려는 경우 HRTF 매개 변수를 변경 하는 방법은 다음과 같습니다. 모든 HRTF 오디오 원본에 연결 하려는 *SetHRTF.cs* 이라는 스크립트에이를 복사 하 여 붙여 넣을 수 있습니다. 이를 통해 HRTF에 중요 한 매개 변수를 변경할 수 있습니다.

```cs
using UnityEngine;
   using System.Collections;
   public class SetHRTF : MonoBehaviour    {
       public enum ROOMSIZE { Small, Medium, Large, None };
       public ROOMSIZE room = ROOMSIZE.Small;  // Small is regarded as the "most average"
       // defaults and docs from MSDN
       // https://msdn.microsoft.com/library/windows/desktop/mt186602(v=vs.85).aspx
       AudioSource audiosource;
       void Awake()
       {
           audiosource = this.gameObject.GetComponent<AudioSource>();
           if (audiosource == null)
           {
               print("SetHRTFParams needs an audio source to do anything.");
               return;
           }
           audiosource.spatialize = 1; // we DO want spatialized audio
           audiosource.spread = 0; // we dont want to reduce our angle of hearing
           audiosource.spatialBlend = 1;   // we do want to hear spatialized audio
           audiosource.SetSpatializerFloat(1, (float)room);    // 1 is the roomsize param
       }
   }
```
### <a name="spatial-sound-in-mixed-reality-toolkit"></a>혼합 현실 도구 키트의 공간 소리
- [HoloToolkit-Examples/SpatialSound/장면/U오디오 관리자 테스트. unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity)

Mixed Reality Toolkit의 다음 예는 소리를 사용 하 여 환경을 더 몰입로 만드는 방법을 보여 주는 일반적인 오디오 효과 예제입니다.
- [HoloToolkit-Examples/SpatialSound/장면/기타 Lofitest unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity)
- [HoloToolkit-Examples/SpatialSound/장면/AudioOcclusionTest](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity)

## <a name="see-also"></a>참조
* [공간 음향](spatial-sound.md)
* [공간 음향 디자인](spatial-sound-design.md)
