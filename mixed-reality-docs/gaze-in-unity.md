---
title: Unity에서 gaze
description: 게이즈는 사용자 앱에서 혼합된 현실에서 만드는 홀로그램 대상 사용자는 기본 방법입니다.
author: thetuvix
ms.author: yoyoz
ms.date: 03/21/2018
ms.topic: article
keywords: 응시, unity, 홀로그램, 혼합된 현실
ms.openlocfilehash: b2cc86db156a1e97b013e4cd6debe3abe5ffb6dd
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453723"
---
# <a name="head-gaze-in-unity"></a>Unity에서 Head 응시

[Gaze](gaze.md) 대상 사용자에 대 한 기본 방법이 합니다 [홀로그램](hologram.md) 에서 앱을 만듭니다 [혼합 현실](mixed-reality.md)합니다.


## <a name="implementing-head-gaze"></a>헤드 게이즈 구현

개념상 [gaze](gaze.md) 앞쪽으로 연결 되 고 확인 된 헤드셋 인 사용자의 헤드 광선을 그린 프로젝션에 의해 구현 됩니다 광선와 충돌 하는 어떤 합니다. Unity 주를 통해 사용자의 헤드 위치 및 방향 unity에서 노출 [카메라](camera-in-unity.md), 특히 [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) 하 고 [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html)합니다.

호출 [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) 결과 [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) 충돌이 발생 한 3D 지점을 포함 하 여 충돌 및 기타 GameObject 게이즈 광선에 대 한 정보를 포함 하는 구조체 와 충돌 합니다.

### <a name="example-implement-head-gaze"></a>예: 헤드 게이즈 구현

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

### <a name="best-practices"></a>최선의 구현 방법

위의 예제는 단일 raycast 게이즈 대상을 찾으려면 업데이트 루프에서를 수행 하는 방법, 하는 동안 잠재적으로 관심 있는 개체에 gazed 되는 모든 개체에서이 작업을 수행 하는 대신 게이즈를 관리 하는 단일 개체에서이 작업을 수행 하는 것이 좋습니다. 이렇게 하면 하나만 게이즈 raycast 각 프레임을 수행 하 여 처리를 저장 하는 앱 수 있습니다.

## <a name="visualizing-gaze"></a>게이즈를 시각화합니다.

콘텐츠를 사용 하 여 대상 및 상호 작용을 마우스 포인터로 사용 하는 위치는 바탕 화면에서 구현 해야 하는 것 처럼를 [커서](cursors.md) 사용자 게이즈를 나타내는입니다. 에 사용자의 신뢰를 이렇게 거 든 상호 작용 합니다.

## <a name="gaze-in-mixed-reality-toolkit-v2"></a>혼합된 현실에서 gaze Toolkit v2
게이즈를 액세스할 수 있습니다 합니다 [Manager 입력](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) MRTK v2의 합니다.

## <a name="see-also"></a>참조
* [카메라](camera-in-unity.md)
* [응시 입력](gaze.md)
* [커서](cursors.md)
* [응시 대상 지정](gaze-targeting.md)
