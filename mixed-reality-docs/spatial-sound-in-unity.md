---
title: Unity에서 공간 소리
description: 공간 소리를 재생 하는 작업은 Unity 장면 내 특정 3D 지점에서 제공 됩니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity를 공간 소리 HRTF, 공간 크기
ms.openlocfilehash: e2b321d7086314a14a940d57aa17e67636c758b8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597515"
---
# <a name="spatial-sound-in-unity"></a>Unity에서 공간 소리

이 항목에는 Unity 프로젝트에서 공간 소리를 사용 하는 방법을 설명 합니다. 필요한 플러그 인 파일 뿐만 아니라 Unity 구성 요소 및 공간 소리를 사용할 수 있는 속성을 설명 합니다.

## <a name="enabling-spatial-sound-in-unity"></a>Unity에서 공간 소리를 사용 하도록 설정

Unity에서 공간 소리는 오디오 입체 음향 플러그 인을 사용 하 여 활성화 됩니다. 공간 소리를 사용 하도록 설정 하려고 하는 것 만큼 쉽습니다 이므로 플러그 인 파일을 Unity에 직접 묶이는 **편집 > 프로젝트 설정 > 오디오** 변경과 합니다 **입체 음향 플러그 인** 는관리자의 **MS HRTF 입체 음향**합니다. Microsoft 입체 음향만를 지원 하므로 48000 Hz 현재 드문 경우 이지만 시스템 출력 장치 설정 되지 않았음을 48000를 이미 HRTF 오류를 방지 하기 위해 48000를 시스템 샘플 요금은도 설정 해야 합니다.

![AudioManager 검사기](images/audio-250px.png)<br>
*AudioManager 검사기*

Unity 프로젝트는 이제 공간 소리를 사용 하도록 구성 됩니다.

>[!NOTE]
>개발을 위한 Windows 10 PC를 사용 하지 않는 경우 얻을 수 없습니다 공간 소리 편집기에서 나 장치의 (경우에 Windows 10 SDK를 사용 하는).

## <a name="using-spatial-sound-in-unity"></a>Unity에서 공간 소리를 사용 하 여

공간 사운드 오디오 원본 구성 요소에 세 가지 설정을 조정 하 여 Unity 프로젝트에서 사용 됩니다. 다음 단계를 공간 사운드 오디오 원본 구성 요소를 구성 합니다.
* 에 **계층 구조** 패널에 연결 하는 게임 개체를 선택 합니다 **오디오 원본**합니다.
* 에 **검사기** 패널의 합니다 **오디오 원본** 구성 요소
    * 확인 합니다 **Spatialize** 옵션입니다.
    * 설정할 **공간 Blend** 하 **3D** (숫자 값 1).
    * 최상의 결과 확장 하 고 **3D 소리 설정** 설정 **볼륨 롤오프** 하 **사용자 지정 롤오프**합니다.

![오디오 소스를 표시 하는 Unity inspector 패널](images/audiosource.png)<br>
*오디오 소스를 표시 하는 Unity inspector 패널*

소리 이제 실제로 프로젝트의 환경 내에서 존재!

잘 알고는 것이 좋습니다 합니다 [공간 소리 디자인 지침](spatial-sound-design.md)합니다. 이러한 지침을 통해 프로젝트에 오디오를 원활 하 게 통합 하는 데 사용자가 만든 환경에 사용자를 추가로 세계 체험해 합니다.

## <a name="setting-spatial-sound-settings"></a>소리 공간 설정

에 설정할 수 있습니다 하는 추가 매개 변수를 제공 하는 Microsoft 공간 소리 플러그 인을 오디오 소스 별로 오디오 시뮬레이션을 추가로 제어할 수 있도록 합니다. 이 매개 변수는 시뮬레이션 된 공간의 크기입니다.

### <a name="room-size"></a>공간 크기

크기를 공간 소리 기준으로 시뮬레이션 되는 공간입니다. 대화방의 대략적인 크기는 다음과 같습니다. (작은 회의실에 office) 소, 중 (큰 회의실) 및 대규모 (강당). 또한 none 실외 환경을 시뮬레이션 하는 공간 크기를 지정할 수 있습니다. 기본 공간 크기가 작습니다.

### <a name="example"></a>예제

Unity에 대 한 MixedRealityToolkit 공간 소리 설정을 쉽게 설정 하는 정적 클래스를 제공 합니다. 이 클래스에서 찾을 수 있습니다 합니다 [MixedRealityToolkit\SpatialSound 폴더](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) 프로젝트에서 모든 스크립트에서 호출 될 수 있습니다. 프로젝트의 각 오디오 원본 구성 요소에 이러한 매개 변수를 설정 하는 것이 좋습니다. 다음 예제에서는 연결된 된 오디오 원본에 대 한 중간 공간 크기를 선택 하면 보여 줍니다.

```cs
AudioSource audioSource = gameObject.GetComponent<AudioSource>()

if (audioSource != null) {
    SpatialSoundSettings.SetRoomSize(audioSource, SpatialMappingRoomSizes.Medium);
}
```

### <a name="directly-accessing-parameters-from-unity"></a>Unity에서 매개 변수를 직접 액세스

MixedRealityToolkit의 뛰어난 오디오 도구를 사용 하지 않으려는 경우 HRTF 매개 변수 변경 하는 방법을 다음과 같습니다. 복사/붙여 넣을 수 있습니다이 호출 스크립트로 *SetHRTF.cs* 모든 HRTF AudioSource에 연결 하려고 하는 합니다. HRTF에 중요 한 매개 변수를 변경할 수 있습니다.

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
### <a name="spatial-sound-in-mixed-reality-toolkit"></a>혼합된 현실 도구 키트의 공간 소리
- [HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity)

혼합 현실 도구 키트에서 다음 예제는 소리를 사용 하 여 사용자 환경을 더 몰입 형을 확인 하는 방법을 보여 주는 예제는 일반 오디오 효과입니다.
- [HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity)
- [HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity)

## <a name="see-also"></a>참조
* [소리 공간](spatial-sound.md)
* [공간 적절 하 게 디자인](spatial-sound-design.md)
