---
title: Unity에서 응시
description: 응시는 사용자가 혼합 현실에서 앱이 만드는 holograms를 대상으로 하는 기본 방법입니다.
author: thetuvix
ms.author: yoyoz
ms.date: 03/21/2018
ms.topic: article
keywords: 눈에 응시, 헤드-응시, unity, 홀로그램, 혼합 현실
ms.openlocfilehash: 43e643bac00e3c889b14000331d2ed95014fdcc5
ms.sourcegitcommit: ff330a7e36e5ff7ae0e9a08c0e99eb7f3f81361f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70122036"
---
# <a name="head-gaze-in-unity"></a>헤드-Unity에서의 응시

[응시](gaze.md) 는 사용자가 [혼합 현실](mixed-reality.md)에서 앱이 만드는 [holograms](hologram.md) 를 대상으로 하는 기본 방법입니다.


## <a name="implementing-head-gaze"></a>헤드-응시 구현

개념적으로 [head-응시](gaze.md) 는 헤드셋이 있는 사용자 헤드의 광선을 전달 하 고, 정방향 방향으로, 광선이 충돌 하는 항목을 확인 하 여 구현 합니다. Unity에서 사용자의 헤드 위치와 방향은 Unity 기본 [카메라](camera-in-unity.md) [(구체적으로](http://docs.unity3d.com/ScriptReference/Camera-main.html)는 없음)를 통해 노출 됩니다. [transform. forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) 및 [Unityengine. Camera. main](http://docs.unity3d.com/ScriptReference/Camera-main.html). [transform. position](http://docs.unity3d.com/ScriptReference/Transform-position.html).

[물리학](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) 를 호출 하면 충돌이 발생 한 3d 지점과 다른 GameObject (헤드-응시 광선 충돌)를 포함 한 충돌에 대 한 정보가 포함 된 [Raycasthit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) 구조가 생성 됩니다.

### <a name="example-implement-head-gaze"></a>예: 헤드 구현-응시

```cs
void Update()
{
       RaycastHit hitInfo;
       if (Physics.Raycast(
               Camera.main.transform.position,
               Camera.main.transform.forward,
               out hitInfo,
               20.0f,
               Physics.DefaultRaycastLayers))
       {
           // If the Raycast has succeeded and hit a hologram
           // hitInfo's point represents the position being gazed at
           // hitInfo's collider GameObject represents the hologram being gazed at
       }
}
```

### <a name="best-practices"></a>모범 사례

위의 예제에서는 업데이트 루프에서 단일 raycast를 수행 하 여 사용자의 헤드가 가리키는 대상을 찾는 방법을 보여 주지만, 개체에서이 작업을 수행 하는 대신 단일 개체에서이 작업을 수행 하는 것이 좋습니다. gazed입니다. 이를 통해 앱은 각 프레임을 하나의 헤드 (각 프레임)만 수행 하 여 처리를 저장할 수 있습니다.

## <a name="visualizing-head-gaze"></a>헤드 시각화-응시

마우스 포인터를 사용 하 여 콘텐츠를 대상으로 지정 하 고 상호 작용 하는 데스크톱과 마찬가지로 사용자의 헤드를 나타내는 [커서](cursors.md) 를 구현 해야 합니다. 이렇게 하면 사용자가 상호 작용 하는 것에 대 한 확신을 얻을 수 있습니다.

## <a name="head-gaze-in-the-mixed-reality-toolkit-v2"></a>Mixed Reality Toolkit v 2의 Head-응시
MRTK v 2의 [입력 관리자](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) 에서 헤드-응시에 액세스할 수 있습니다.

## <a name="see-also"></a>참조
* [카메라](camera-in-unity.md)
* [커서](cursors.md)
* [응시 입력](gaze.md)
* [응시 대상 지정](gaze-targeting.md)
