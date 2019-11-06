---
title: Unity의 공간 소리
description: Unity 장면 내의 특정 3D 점에서 가져온 공간 소리를 재생 합니다.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, 공간 음향, HRTF, 방 크기
ms.openlocfilehash: c96717d9df9b89fbb09f0b4466ee3a9bf5c8a149
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641070"
---
# <a name="spatial-sound-in-unity"></a>Unity의 공간 소리

이 페이지는 Unity mixed reality 프로젝트에서 Microsoft HRTF spatializer를 사용 하 고 디자인 하는 데 도움이 되는 리소스에 대 한 링크를 제공 합니다.

## <a name="enable-spatialization"></a>Spatialization 사용

프로젝트의 오디오 설정에서 **MS HRTF Spatializer** 를 사용 하도록 설정 합니다. 자세한 내용은 [Unity의 spatializer 설명서](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)를 참조 하세요. 

**오디오 원본을** 계층의 개체에 연결 하 고, **spatialization 사용** 확인란을 선택 하 고 **공간 Blend** 슬라이더를 ' 1 '로 이동 하 여 spatialization를 사용 하도록 설정 합니다. 자세한 내용은 [Unity의 오디오 원본 설명서](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)를 참조 하세요. 

## <a name="design-with-spatialization"></a>Spatialization를 사용 하 여 디자인

### <a name="distance-based-attenuation"></a>거리 기반 감쇠
Unity의 기본 거리 기반 감소는 로그 rolloff를 사용 하 여 최소 거리가 1 미터이 고 최대 거리가 500 미터입니다. 이는 시나리오에 적합 하거나, 소스를 너무 빨리 경우 수 있습니다. 거리 감소 곡선에 대 한 권장 설정은 [혼합 현실의 소리 디자인](spatial-sound-design.md) 을 참조 하세요. unity에서 이러한 곡선을 설정 하는 방법에 대 한 자세한 내용은 [unity의 오디오 소스 설명서](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) 를 참조 하세요.

### <a name="environment"></a>환경
**MS HRTF Spatializer** 에는 [네 개의 반향 설정이](https://docs.microsoft.com/windows/win32/api/hrtfapoapi/ne-hrtfapoapi-hrtfenvironment) 있고 기본값은 ' small ' 인 대화방 반향 구성 요소가 포함 됩니다. Spatialized 오디오 소스가 있는 Unity의 각 개체에 다음 C# 스크립트를 연결 하 여 각 오디오 원본에 대해 대화방 설정을 프로그래밍 방식으로 변경할 수 있습니다.

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

## <a name="unity-spatial-sound-examples"></a>Unity 공간 음향 예
Mixed Reality Toolkit (MRTK)에는 혼합 현실에서 오디오 효과를 적용 하는 방법에 대 한 예제가 포함 되어 있습니다. [mrtk 데모](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio).

