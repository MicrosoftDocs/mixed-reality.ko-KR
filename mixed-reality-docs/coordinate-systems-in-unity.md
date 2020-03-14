---
title: Unity에서 시스템 좌표계
description: Unity에서 실제, 장소, 실내 확장 및 전 세계 혼합 현실 환경을 빌드하는 방법에 대해 알아보세요.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 좌표계, 공간 좌표계, 방향 전용, 고정 크기 조정, 대규모, 실내 규모, 전 세계 규모, 360 학위, 고가, 실내, 실내, 세계, 크기 조정, 위치, 방향, Unity, 앵커, 공간 앵커, 전 세계 고정, 전 세계 고정 세계 잠금, 본문 잠김, 본문 잠금, 추적 손실, locatability, 경계, recenter
ms.openlocfilehash: 36d74488b23587e5c89b40faf97921a10be7473b
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375770"
---
# <a name="coordinate-systems-in-unity"></a>Unity에서 시스템 좌표계

Windows Mixed Reality는 규모에 상관 없이 공간 규모 앱을 통해 응용 프로그램을 수평으로 확장 하 여 규모에 상관 없이 광범위 한 [환경](coordinate-systems.md)에서 앱을 지원 합니다. HoloLens에서 더 나아가 사용자가 5 미터 이상 이동할 수 있도록 하는 세계적인 규모의 앱을 빌드할 수 있습니다.

Unity에서 혼합 현실 환경을 빌드하는 첫 번째 단계는 앱이 대상으로 하는 [환경 규모](coordinate-systems.md) 를 결정 하는 것입니다.

## <a name="building-an-orientation-only-or-seated-scale-experience"></a>방향 전용 또는 확장 된 환경 구축

**네임 스페이스:** *UNITYENGINE. XR*<br>
**유형:** *xrdevice*

**방향 전용** 또는 통합 된 **환경을**구축 하려면 Unity를 고정 된 추적 공간 형식으로 설정 해야 합니다. 이를 통해 Unity의 세계 좌표계를 설정 하 여 [고정 된 참조 프레임](coordinate-systems.md#spatial-coordinate-systems)을 추적할 수 있습니다. 고정 추적 모드에서 카메라의 기본 위치 바로 앞에 있는 편집기에 배치 된 콘텐츠 (앞으로-Z)는 앱이 시작 될 때 사용자 앞에 표시 됩니다.

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

**네임 스페이스:** *UNITYENGINE. XR*<br>
**형식:** *inputtracking*

360도 비디오 뷰어 (위치 헤드 업데이트에서 환상 효과를 ruin)와 같은 순수한 **방향 전용 환경** 에서는 XR를 설정할 수 있습니다 [. InputTracking. disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) 을 true로 설정 합니다.

```cs
InputTracking.disablePositionalTracking = true;
```

사용자가 나중에 연결 된 원본을 recenter 할 수 있도록 하는 **확장 된 환경의**경우 XR를 호출할 수 있습니다 [. Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) 메서드:

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a>대규모 또는 공간 확장 환경 구축

**네임 스페이스:** *UNITYENGINE. XR*<br>
**유형:** *xrdevice*

**대규모 또는** **공간 규모의 경험**을 위해 바닥을 기준으로 콘텐츠를 넣어야 합니다. 사용자의 층을 사용 하는 이유는 사용자의 정의 된 최고 수준 원점 및 선택적 대화방 경계를 나타내는 **[공간 단계](coordinate-systems.md#spatial-coordinate-systems)** 를 처음 실행 하는 동안 설정 하는 것입니다.

Unity가 바닥 수준에서 세계 좌표계를 사용 하 여 작동 하도록 하려면 Unity를 RoomScale 추적 공간 형식으로 설정 하 고 해당 집합이 성공 하도록 할 수 있습니다.

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```
* SetTrackingSpaceType가 true를 반환 하는 경우 Unity는 세계 좌표계를 정상적으로 전환 하 여 [참조의 스테이지 프레임](coordinate-systems.md#spatial-coordinate-systems)을 추적 했습니다.
* SetTrackingSpaceType가 false를 반환 하는 경우 Unity는 사용자가 환경에서 한 층도 설정 하지 않았기 때문에 참조의 스테이지 프레임으로 전환할 수 없습니다. 이는 일반적이 지 않지만 다른 방에 단계를 설정 하 고 사용자가 새 단계를 설정 하지 않고 장치를 현재 대화방으로 이동한 경우에 발생할 수 있습니다.

앱이 RoomScale 추적 공간 유형을 성공적으로 설정 하면 y = 0 평면에 배치 된 콘텐츠가 바닥에 표시 됩니다. (0, 0, 0)의 원점은 사용자가 대화방을 설치 하는 동안 구현 하는 바닥의 특정 위치가 되며,-Z는 설치 중에 전달 된 정방향 방향을 나타냅니다.

**네임 스페이스:** *UNITYENGINE. XR*<br>
**형식:** *경계*

그런 다음 스크립트 코드에서 TryGetGeometry 메서드를 호출할 수 있습니다. XR 형식으로 경계 다각형을 가져오고 TrackedArea 경계 형식을 지정 합니다. 사용자가 경계 (꼭 짓 점 목록)를 정의 하는 경우 사용자에 게 **공간 확장 환경을** 제공 하 여 사용자가 만든 장면을 살펴볼 수 있다는 것을 알 수 있습니다.

사용자가 접근 하면 시스템에서 자동으로 경계를 렌더링 합니다. 앱은 경계 자체를 렌더링 하기 위해이 다각형을 사용할 필요가 없습니다. 그러나이 경계 다각형을 사용 하 여 장면 개체의 레이아웃을 선택 하 여 사용자가 teleporting 없이 해당 개체에 실제로 연결할 수 있는지 확인할 수 있습니다.

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a>세계 최고 규모 환경 구축

**네임 스페이스:** *unityengine. XR. WSA*<br>
**유형:** *WorldAnchor*

사용자가 5 미터를 wander 수 있도록 하는 HoloLens의 진정한 **세계 규모 환경** 에서는 공간 규모 환경에 사용 되는 기술이 아닌 새로운 기술이 필요 합니다. 사용할 수 있는 한 가지 핵심 기술은 사용자가 로밍 하는 정도에 관계 없이 실제 세계에서 holograms 클러스터를 정확 하 게 잠그는 [공간 앵커](coordinate-systems.md#spatial-anchors) 를 만든 다음 [이후 세션에서 해당 holograms를 다시 찾는](coordinate-systems.md#spatial-anchor-persistence)것입니다.

Unity에서는 GameObject에 **WorldAnchor** Unity 구성 요소를 추가 하 여 공간 앵커를 만듭니다.

### <a name="adding-a-world-anchor"></a>세계 앵커 추가

세계 앵커를 추가 하려면 실제 지역에서 고정 하려는 변환으로 game 개체에서 AddComponent<WorldAnchor>()를 호출 합니다.

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

간단하죠. 이 게임 개체는 이제 실제 세계의 현재 위치에 고정 되어 있습니다 .이를 통해 Unity 세계 좌표가 약간 조정 되어 물리적 맞춤을 확인할 수 있습니다. [지 속성](persistence-in-unity.md) 을 사용 하 여 이후 앱 세션에서이 앵커 된 위치를 다시 찾습니다.

### <a name="removing-a-world-anchor"></a>세계 앵커 제거

GameObject를 실제 세계 위치로 잠글 필요가 없으며이 프레임으로 이동 하지 않으려면 세계 앵커 구성 요소에 대해 소멸을 호출 하면 됩니다.

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

GameObject이 프레임을 이동 하려면 DestroyImmediate를 대신 호출 해야 합니다.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a>세계 고정 GameObject 이동

GameObject은 세계 앵커가 있는 동안 이동할 수 없습니다. GameObject이 프레임을 이동 해야 하는 경우 다음을 수행 해야 합니다.
1. 세계 앵커 구성 요소 DestroyImmediate
2. GameObject 이동
3. GameObject에 새 세계 앵커 구성 요소를 추가 합니다.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a>Locatability 변경 내용 처리

WorldAnchor는 특정 시점에 물리적 세계에 과정이 수 없습니다. 이런 경우 Unity는 고정 된 개체의 변환을 업데이트 하지 않습니다. 이는 앱이 실행 되는 동안에도 변경 될 수 있습니다. Locatability의 변경을 처리 하지 못하면 개체가 전 세계의 올바른 물리적 위치에 표시 되지 않습니다.

Locatability 변경 내용에 대 한 알림이 표시 되는 경우:
1. OnTrackingChanged 이벤트 구독
2. 이벤트를 처리 합니다.

**Ontrackingchanged** 이벤트는 기본 공간 앵커가 과정이의 상태와 과정이 되지 않는 사이에 변경 될 때마다 호출 됩니다.

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

그런 다음 이벤트를 처리 합니다.

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

경우에 따라 앵커가 즉시 배치 됩니다. 이 경우 AddComponent<WorldAnchor>()가 반환 되 면 앵커의이 isLocated 속성은 true로 설정 됩니다. 따라서 OnTrackingChanged 이벤트가 트리거되지 않습니다. 깨끗 한 패턴은 앵커를 연결한 후 초기 IsLocated 상태를 사용 하 여 OnTrackingChanged 처리기를 호출 하는 것입니다.

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a>장치에서 앵커 공유

<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 공간 앵커</a> 를 사용 하 여 로컬 WorldAnchor에서 지속적인 클라우드 앵커를 만들 수 있습니다. 그러면 앱이 여러 HoloLens, IOS 및 Android 장치에서 찾을 수 있습니다.  여러 장치에서 공통 공간 앵커를 공유 하 여 각 사용자는 동일한 물리적 위치에서 해당 앵커에 대해 렌더링 된 콘텐츠를 볼 수 있습니다.  이렇게 실제 세계 공유 환경을 제공합니다.

Unity에서 공유 환경 빌드를 시작 하려면 5 분 <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure 공간 앵커 Unity 퀵 스타트</a>를 사용해 보세요.

Azure 공간 앵커를 사용 하 여 실행 하면 <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Unity에서 앵커를 만들고 찾을</a>수 있습니다.

## <a name="see-also"></a>참고 항목
* [환경 크기 조정](coordinate-systems.md#mixed-reality-experience-scales)
* [공간 스테이지](coordinate-systems.md#stage-frame-of-reference)
* [Unity의 손실 추적](tracking-loss-in-unity.md)
* [공간 앵커](spatial-anchors.md)
* [Unity의 지속성](persistence-in-unity.md)
* [Unity의 공유 환경](shared-experiences-in-unity.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Unity 용 Azure 공간 앵커 SDK</a>