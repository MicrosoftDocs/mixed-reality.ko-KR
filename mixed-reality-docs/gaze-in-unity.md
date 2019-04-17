---
title: Unity에서 gaze
description: 게이즈는 사용자 앱에서 혼합된 현실에서 만드는 홀로그램 대상 사용자는 기본 방법입니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 응시, unity, 홀로그램, 혼합된 현실
ms.openlocfilehash: 09915479a9eef95c5ce4533371e113ab6191a331
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604802"
---
# <a name="gaze-in-unity"></a>Unity에서 gaze

[Gaze](gaze.md) 대상 사용자에 대 한 기본 방법이 합니다 [홀로그램](hologram.md) 에서 앱을 만듭니다 [혼합 현실을](mixed-reality.md)합니다.

## <a name="implementing-gaze"></a>게이즈를 구현합니다.

개념상 [gaze](gaze.md) 앞쪽으로 연결 되 고 확인 된 헤드셋 인 사용자의 헤드 광선을 그린 프로젝션에 의해 구현 됩니다 광선와 충돌 하는 어떤 합니다. Unity 주를 통해 사용자의 헤드 위치 및 방향 unity에서 노출 [카메라](camera-in-unity.md), 특히 [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) 하 고 [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html)합니다.

호출 [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) 결과 [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) 충돌이 발생 한 3D 지점을 포함 하 여 충돌 및 기타 GameObject 게이즈 광선에 대 한 정보를 포함 하는 구조체 와 충돌 합니다.

### <a name="example-implement-gaze"></a>예: 구현 응시

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

## <a name="gaze-in-mixed-reality-toolkit"></a>혼합된 현실 도구 키트의 gaze
가져올 때 [MRTK Unity 패키지를 릴리스](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) 에서 프로젝트를 복제 또는 합니다 [GitHub 리포지토리](https://github.com/Microsoft/MixedRealityToolkit-Unity), Unity에서 새 메뉴 ' 혼합 현실 Toolkit'를 찾을 것입니다. '구성' 메뉴 아래에서 적용 혼합 현실 장면 [설정] 메뉴를 표시 됩니다. 기본 카메라를 제거 하 고 기본 구성 요소 추가 클릭 하면 [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab)하십시오 [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), 및 [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab)합니다.

![장면 설치용 MRTK 메뉴](images/MRTK_Input_Menu.png)<br>
*장면 설치용 MRTK 메뉴*

![MRTK 자동 장면 설치](images/MRTK_HowTo_Input1.png)<br>
*MRTK 자동 장면 설치*

### <a name="gaze-related-scripts-in-mixed-reality-toolkit"></a>혼합 현실 도구 키트의 관련된 스크립트 gaze
혼합 현실 도구 키트의 prefab InputManager 포함 [GazeManager.cs](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeManager.cs) 하 고 [Gaze 안정기](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeStabilizer.cs)합니다. 아래 [SimpleSinglePointerSelector](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Focus/SimpleSinglePointerSelector.cs), 사용자 지정 커서를 할당할 수 있습니다. 기본, 애니메이션 [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab) 할당 됩니다.

[Cursor.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) 하 고 [CursorWithFeedback.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) 커서를 사용 하 여 게이즈를 시각화 하는 방법을 보여 줍니다.

## <a name="see-also"></a>참조
* [카메라](camera-in-unity.md)
* [응시](gaze.md)
* [커서](cursors.md)
* [대상으로 응시](gaze-targeting.md)
