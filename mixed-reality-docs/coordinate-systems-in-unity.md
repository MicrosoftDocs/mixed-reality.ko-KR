---
title: Unity의 좌표계
description: 준비 탐구 빌드하는 방법을 알아봅니다, 그리고 규모 방 및 전 세계 규모 혼합 현실 환경 Unity에서.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 좌표계, 공간 좌표계, 방향 으로만 이동 가능한 장착 규모, 고정 규모 방-크기 조정, 전 세계 규모의 360도 장착, 고정, 공간, 환경, 확장, 위치, 방향 앵커, Unity, 공간 앵커, 전 세계 잠긴 world 앵커 전 세계 잠금, 본문 잠긴 본문 잠금, 손실, locatability, 범위, 둘러싸기의 추적
ms.openlocfilehash: 36d74488b23587e5c89b40faf97921a10be7473b
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605052"
---
# <a name="coordinate-systems-in-unity"></a>Unity의 좌표계

Windows Mixed Reality 광범위 한 앱을 지원 [눈금 환경을](coordinate-systems.md), 공간 규모 앱을 통해 등록 방향 으로만 이동 가능한 및 장착 규모 앱에서. HoloLens에서 더 나아가 수 있으며 건물의 이상 층 전체 탐색 5 미터 외 워크 수 있도록 하는 전 세계 규모 앱을 빌드할 수 있습니다.

Unity에서 혼합된 현실 경험을 빌드하는 첫 번째 단계는를 결정 하는 것 [규모 경험](coordinate-systems.md) 앱 대상입니다.

## <a name="building-an-orientation-only-or-seated-scale-experience"></a>한 방향 으로만 이동 가능한 또는 장착 규모 환경 구축

**Namespace:** *UnityEngine.XR*<br>
**형식:** *XRDevice*

빌드에 **방향 으로만 이동 가능한** 또는 **장착 규모 환경**로 설정 해야 Unity는 고정 공간 형식을 추적 합니다. 이 Unity의 세계 좌표 시스템 추적을 설정 합니다 [고정 참조 프레임](coordinate-systems.md#spatial-coordinate-systems)합니다. 고정 추적 모드에서 콘텐츠 편집기 카메라의 기본 위치 바로 앞에 배치 (앞으로-Z) 앱이 시작 되 면 사용자 앞에 표시 됩니다.

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

**Namespace:** *UnityEngine.XR*<br>
**형식:** *InputTracking*

에 대 한 순수 **방향 으로만 이동 가능한 환경을** (여기서 헤드 위치 업데이트는 손상 효과) 하는 360도 비디오 뷰어와 같은 설정할 수 있습니다 [xr 하이 합니다. InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) true로 합니다.

```cs
InputTracking.disablePositionalTracking = true;
```

에 대 한는 **장착 규모 환경**, 사용자에 게 나중 둘러싸기의 탐구 원점으로 호출할 수 있습니다는 [xr 하이 합니다. InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) 메서드:

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a>고정 크기 조정 또는 방 규모 환경 구축

**Namespace:** *UnityEngine.XR*<br>
**형식:** *XRDevice*

에 대 한는 **고정 크기 조정** 또는 **방 규모 환경**, floor를 기준으로 콘텐츠를 배치 해야 합니다. 사용자에 대 한 이유를 사용 하 여 floor 합니다  **[공간 단계](coordinate-systems.md#spatial-coordinate-systems)** 층 원본 및 선택적인 공간이 경계 정의 된 사용자를 나타내는, 설정 하는 동안 먼저 실행 합니다.

Floor 수준에서 해당 세계 좌표계를 사용 하 여 Unity가 작동 하는지 확인 합니다 하려면 공간 형식을 추적 RoomScale Unity로 하 고 집합 성공 했는지 확인 합니다.

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
* Unity가 추적 하는 전 세계 좌표계로 전환 했습니다 SetTrackingSpaceType true를 반환 합니다 [단계에서 참조 하는 프레임을](coordinate-systems.md#spatial-coordinate-systems)입니다.
* SetTrackingSpaceType false를 반환 하는 경우 Unity 환경에서 바닥도 설정 하 고 있지 않은 사용자 때문에 스테이지의 참조 프레임, 가능성이 전환할 수 없습니다. 이 일반적인 되지 않지만 스테이지를 다른 방에 설정 하 고 장치는 사용자가 새 스테이지를 설정 하지 않고 현재 대화방에 이동 된 경우 발생할 수 있습니다.

앱 공간 유형, 콘텐츠 y 배치 추적 RoomScale를 성공적으로 설정 되 면 0 평면 바닥에 표시 됩니다. 원점 (0, 0, 0)에서 사용자 공간 설치 하는 동안-앞쪽으로 설치 하는 동안 연결 된 것을 나타내는 Z를 사용 하 여 구현 하는 위치 현장에서 구체적인 장소를 수 있습니다.

**Namespace:** *UnityEngine.Experimental.XR*<br>
**형식:** *경계*

스크립트 코드에서 수 있습니다 TryGetGeometry 메서드를 호출 하는 경계 다각형, 가져올 UnityEngine.Experimental.XR.Boundary 형식의 TrackedArea의 경계 형식을 지정 합니다. 안전 하 게 제공 하는 것을 알고 사용자 경계 (얻게 다시 꼭 짓 점 목록)을 정의 하는 경우는 **방 규모 환경** 위치 수 안내 장면 주위를 사용자에 게 만듭니다.

시스템 사용자 가까워지면 경계 렌더링 자동으로 참고 합니다. 앱이이 다각형을 사용 하 여 자체 경계를 렌더링할 필요가 없습니다. 그러나 사용자 텔레포트 하지 않고 해당 개체를 물리적으로 연결할 수 있도록이 경계 다각형을 사용 하 여 장면의 개체 레이아웃을 선택할 수도 있습니다.

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a>전 세계 규모 환경 구축

**Namespace:** *UnityEngine.XR.WSA*<br>
**형식:** *WorldAnchor*

True에 대 한 **세계 규모 환경** 5m 초과 겪고 수 있도록 하는 HoloLens에서 새 기술을 보다 더 많은 공간이 규모 환경에 대 한 필요 합니다. 하나의 키 기술을 사용 하 여 만드는 것을 [공간 앵커](coordinate-systems.md#spatial-anchors) 홀로그램을 사용자 로밍 정도 관계 없이 실제 세계의 위치에 정확 하 게 클러스터를 잠글 수 고 [다시에서 나중에 이러한 홀로그램을 찾습니다 세션](coordinate-systems.md#spatial-anchor-persistence)합니다.

Unity에서 만든 공간 앵커를 추가 하 여 합니다 **WorldAnchor** Unity 구성 요소는 GameObject 합니다.

### <a name="adding-a-world-anchor"></a>전 세계 앵커를 추가합니다.

전 세계 앵커를 추가 하려면 AddComponent 호출<WorldAnchor>실제 환경에서 고정 하려는 변환 사용 하 여 게임 개체 ().

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

정말 간단하죠. 이 게임 개체 물리적 세계의 현재 위치에 고정 될 이제-실제 정렬 되도록 시간이 지남에 따라 약간씩 조정 Unity 세계 좌표 표시 될 수 있습니다. 사용 하 여 [지 속성](persistence-in-unity.md) 이후 앱 세션에 다시 고정 된 위치에서이 찾을 수 있습니다.

### <a name="removing-a-world-anchor"></a>전 세계 앵커를 제거합니다.

경우 더 이상 실제 위치로 잠겨 GameObject 이동이 프레임에서 원하지, 다음 호출할 수 없습니다만 Destroy World 앵커 구성 요소.

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

이 프레임 GameObject를 이동 하려는 경우 대신 DestroyImmediate를 호출 해야 합니다.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a>GameObject를 고정 하는 세계를 이동 합니다.

GameObject의에 전 세계 앵커를 이동할 수 없습니다. 이 프레임 GameObject를 이동 해야 할 경우에 필요 합니다.
1. DestroyImmediate World 앵커 구성 요소
2. GameObject를 이동 합니다.
3. GameObject를 새로운 세계 앵커 구성 요소를 추가 합니다.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a>Locatability 변경 내용 처리

WorldAnchor 아닐 찾을 수 있는 시점의 실제 시간입니다. 발생 하는 경우 Unity가 되지 업데이트할 고정 된 개체의 변환입니다. 이 변경할 수도 응용 프로그램이 실행 되는 동안. Locatability에서 변경을 처리 하지 못했습니다 전 세계에서 올바른 물리적 위치에 표시 되지 않도록 개체에 발생 합니다.

Locatability 변경에 대 한 알림을 받으려면:
1. OnTrackingChanged 이벤트 구독
2. 이벤트 처리

합니다 **OnTrackingChanged** 이벤트에 내부 공간 앵커 되지 과정이 및 과정이 중인 상태의 간에 변경 될 때마다 호출 됩니다.

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

다음 이벤트를 처리 합니다.

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

경우에 따라 앵커 위치 즉시 됩니다. 이 isLocated 속성 앵커의 경우 true로 설정 됩니다 여기서 AddComponent<WorldAnchor>()를 반환 합니다. 결과적으로, OnTrackingChanged 이벤트는 트리거되지 않습니다. 정리 패턴을 앵커를 연결한 후 초기 IsLocated 상태로 OnTrackingChanged 처리기를 호출 하는 것입니다.

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a>장치에서 앵커를 공유합니다.

사용할 수 있습니다 <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 공간 앵커</a> 앱 여러 HoloLens, iOS 및 Android 장치에서 찾을 수 있는 로컬 WorldAnchor에서 견고한 클라우드 앵커를 만들려고 합니다.  일반적인 공간 앵커를 여러 장치를 공유 각 사용자는 동일한 실제 위치에 해당 앵커에 상대적인 렌더링 된 콘텐츠를 볼 수입니다.  따라서 실시간 공유 환경.

5 분을 사용해으로 시작 하려면 Unity에서 공유 환경을 구축 <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">빠른 시작 Azure 공간 앵커 Unity</a>합니다.

Azure 공간 앵커를 사용 하 여 실행을 했으면 할 수 있습니다 <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Unity에서 앵커를 찾아서 만들</a>합니다.

## <a name="see-also"></a>관련 항목
* [환경 확장](coordinate-systems.md#mixed-reality-experience-scales)
* [공간 단계](coordinate-systems.md#stage-frame-of-reference)
* [Unity에서 손실 추적](tracking-loss-in-unity.md)
* [공간 앵커](spatial-anchors.md)
* [Unity의 지 속성](persistence-in-unity.md)
* [Unity에서 공유 경험](shared-experiences-in-unity.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 공간 앵커</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure 공간 앵커 Unity 용 SDK</a>