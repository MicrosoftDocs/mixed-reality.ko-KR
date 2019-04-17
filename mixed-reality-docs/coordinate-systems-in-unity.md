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
# <a name="coordinate-systems-in-unity"></a><span data-ttu-id="c9713-104">Unity의 좌표계</span><span class="sxs-lookup"><span data-stu-id="c9713-104">Coordinate systems in Unity</span></span>

<span data-ttu-id="c9713-105">Windows Mixed Reality 광범위 한 앱을 지원 [눈금 환경을](coordinate-systems.md), 공간 규모 앱을 통해 등록 방향 으로만 이동 가능한 및 장착 규모 앱에서.</span><span class="sxs-lookup"><span data-stu-id="c9713-105">Windows Mixed Reality supports apps across a wide range of [experience scales](coordinate-systems.md), from orientation-only and seated-scale apps up through room-scale apps.</span></span> <span data-ttu-id="c9713-106">HoloLens에서 더 나아가 수 있으며 건물의 이상 층 전체 탐색 5 미터 외 워크 수 있도록 하는 전 세계 규모 앱을 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-106">On HoloLens, you can go further and build world-scale apps that let users walk beyond 5 meters, exploring an entire floor of a building and beyond.</span></span>

<span data-ttu-id="c9713-107">Unity에서 혼합된 현실 경험을 빌드하는 첫 번째 단계는를 결정 하는 것 [규모 경험](coordinate-systems.md) 앱 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-107">Your first step in building a mixed reality experience in Unity is to determine which [experience scale](coordinate-systems.md) your app will target.</span></span>

## <a name="building-an-orientation-only-or-seated-scale-experience"></a><span data-ttu-id="c9713-108">한 방향 으로만 이동 가능한 또는 장착 규모 환경 구축</span><span class="sxs-lookup"><span data-stu-id="c9713-108">Building an orientation-only or seated-scale experience</span></span>

<span data-ttu-id="c9713-109">**Namespace:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="c9713-109">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="c9713-110">**형식:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="c9713-110">**Type:** *XRDevice*</span></span>

<span data-ttu-id="c9713-111">빌드에 **방향 으로만 이동 가능한** 또는 **장착 규모 환경**로 설정 해야 Unity는 고정 공간 형식을 추적 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-111">To build an **orientation-only** or **seated-scale experience**, you must set Unity to the Stationary tracking space type.</span></span> <span data-ttu-id="c9713-112">이 Unity의 세계 좌표 시스템 추적을 설정 합니다 [고정 참조 프레임](coordinate-systems.md#spatial-coordinate-systems)합니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-112">This sets Unity's world coordinate system to track the [stationary frame of reference](coordinate-systems.md#spatial-coordinate-systems).</span></span> <span data-ttu-id="c9713-113">고정 추적 모드에서 콘텐츠 편집기 카메라의 기본 위치 바로 앞에 배치 (앞으로-Z) 앱이 시작 되 면 사용자 앞에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-113">In the Stationary tracking mode, content placed in the editor just in front of the camera's default location (forward is -Z) will appear in front of the user when the app launches.</span></span>

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

<span data-ttu-id="c9713-114">**Namespace:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="c9713-114">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="c9713-115">**형식:** *InputTracking*</span><span class="sxs-lookup"><span data-stu-id="c9713-115">**Type:** *InputTracking*</span></span>

<span data-ttu-id="c9713-116">에 대 한 순수 **방향 으로만 이동 가능한 환경을** (여기서 헤드 위치 업데이트는 손상 효과) 하는 360도 비디오 뷰어와 같은 설정할 수 있습니다 [xr 하이 합니다. InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) true로 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-116">For a pure **orientation-only experience** such as a 360-degree video viewer (where positional head updates would ruin the illusion), you can then set [XR.InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) to true:</span></span>

```cs
InputTracking.disablePositionalTracking = true;
```

<span data-ttu-id="c9713-117">에 대 한는 **장착 규모 환경**, 사용자에 게 나중 둘러싸기의 탐구 원점으로 호출할 수 있습니다는 [xr 하이 합니다. InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) 메서드:</span><span class="sxs-lookup"><span data-stu-id="c9713-117">For a **seated-scale experience**, to let the user later recenter the seated origin, you can call the [XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) method:</span></span>

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a><span data-ttu-id="c9713-118">고정 크기 조정 또는 방 규모 환경 구축</span><span class="sxs-lookup"><span data-stu-id="c9713-118">Building a standing-scale or room-scale experience</span></span>

<span data-ttu-id="c9713-119">**Namespace:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="c9713-119">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="c9713-120">**형식:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="c9713-120">**Type:** *XRDevice*</span></span>

<span data-ttu-id="c9713-121">에 대 한는 **고정 크기 조정** 또는 **방 규모 환경**, floor를 기준으로 콘텐츠를 배치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-121">For a **standing-scale** or **room-scale experience**, you'll need to place content relative to the floor.</span></span> <span data-ttu-id="c9713-122">사용자에 대 한 이유를 사용 하 여 floor 합니다  **[공간 단계](coordinate-systems.md#spatial-coordinate-systems)** 층 원본 및 선택적인 공간이 경계 정의 된 사용자를 나타내는, 설정 하는 동안 먼저 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-122">You reason about the user's floor using the **[spatial stage](coordinate-systems.md#spatial-coordinate-systems)**, which represents the user's defined floor-level origin and optional room boundary, set up during first run.</span></span>

<span data-ttu-id="c9713-123">Floor 수준에서 해당 세계 좌표계를 사용 하 여 Unity가 작동 하는지 확인 합니다 하려면 공간 형식을 추적 RoomScale Unity로 하 고 집합 성공 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-123">To ensure that Unity is operating with its world coordinate system at floor-level, you can set Unity to the RoomScale tracking space type, and ensure that the set succeeds:</span></span>

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
* <span data-ttu-id="c9713-124">Unity가 추적 하는 전 세계 좌표계로 전환 했습니다 SetTrackingSpaceType true를 반환 합니다 [단계에서 참조 하는 프레임을](coordinate-systems.md#spatial-coordinate-systems)입니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-124">If SetTrackingSpaceType returns true, Unity has successfully switched its world coordinate system to track the [stage frame of reference](coordinate-systems.md#spatial-coordinate-systems).</span></span>
* <span data-ttu-id="c9713-125">SetTrackingSpaceType false를 반환 하는 경우 Unity 환경에서 바닥도 설정 하 고 있지 않은 사용자 때문에 스테이지의 참조 프레임, 가능성이 전환할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-125">If SetTrackingSpaceType returns false, Unity was unable to switch to the stage frame of reference, likely because the user has not set up even a floor in their environment.</span></span> <span data-ttu-id="c9713-126">이 일반적인 되지 않지만 스테이지를 다른 방에 설정 하 고 장치는 사용자가 새 스테이지를 설정 하지 않고 현재 대화방에 이동 된 경우 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-126">This is not common, but can happen if the stage was set up in a different room and the device was moved to the current room without the user setting up a new stage.</span></span>

<span data-ttu-id="c9713-127">앱 공간 유형, 콘텐츠 y 배치 추적 RoomScale를 성공적으로 설정 되 면 0 평면 바닥에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-127">Once your app successfully sets the RoomScale tracking space type, content placed on the y=0 plane will appear on the floor.</span></span> <span data-ttu-id="c9713-128">원점 (0, 0, 0)에서 사용자 공간 설치 하는 동안-앞쪽으로 설치 하는 동안 연결 된 것을 나타내는 Z를 사용 하 여 구현 하는 위치 현장에서 구체적인 장소를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-128">The origin at (0, 0, 0) will be the specific place on the floor where the user stood during room setup, with -Z representing the forward direction they were facing during setup.</span></span>

<span data-ttu-id="c9713-129">**Namespace:** *UnityEngine.Experimental.XR*</span><span class="sxs-lookup"><span data-stu-id="c9713-129">**Namespace:** *UnityEngine.Experimental.XR*</span></span><br>
<span data-ttu-id="c9713-130">**형식:** *경계*</span><span class="sxs-lookup"><span data-stu-id="c9713-130">**Type:** *Boundary*</span></span>

<span data-ttu-id="c9713-131">스크립트 코드에서 수 있습니다 TryGetGeometry 메서드를 호출 하는 경계 다각형, 가져올 UnityEngine.Experimental.XR.Boundary 형식의 TrackedArea의 경계 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-131">In script code, you can then call the TryGetGeometry method on your the UnityEngine.Experimental.XR.Boundary type to get a boundary polygon, specifying a boundary type of TrackedArea.</span></span> <span data-ttu-id="c9713-132">안전 하 게 제공 하는 것을 알고 사용자 경계 (얻게 다시 꼭 짓 점 목록)을 정의 하는 경우는 **방 규모 환경** 위치 수 안내 장면 주위를 사용자에 게 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-132">If the user defined a boundary (you get back a list of vertices), you know it is safe to deliver a **room-scale experience** to the user, where they can walk around the scene you create.</span></span>

<span data-ttu-id="c9713-133">시스템 사용자 가까워지면 경계 렌더링 자동으로 참고 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-133">Note that the system will automatically render the boundary when the user approaches it.</span></span> <span data-ttu-id="c9713-134">앱이이 다각형을 사용 하 여 자체 경계를 렌더링할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-134">Your app does not need to use this polygon to render the boundary itself.</span></span> <span data-ttu-id="c9713-135">그러나 사용자 텔레포트 하지 않고 해당 개체를 물리적으로 연결할 수 있도록이 경계 다각형을 사용 하 여 장면의 개체 레이아웃을 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-135">However, you may choose to lay out your scene objects using this boundary polygon, to ensure the user can physically reach those objects without teleporting:</span></span>

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="c9713-136">전 세계 규모 환경 구축</span><span class="sxs-lookup"><span data-stu-id="c9713-136">Building a world-scale experience</span></span>

<span data-ttu-id="c9713-137">**Namespace:** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="c9713-137">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="c9713-138">**형식:** *WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="c9713-138">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="c9713-139">True에 대 한 **세계 규모 환경** 5m 초과 겪고 수 있도록 하는 HoloLens에서 새 기술을 보다 더 많은 공간이 규모 환경에 대 한 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-139">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="c9713-140">하나의 키 기술을 사용 하 여 만드는 것을 [공간 앵커](coordinate-systems.md#spatial-anchors) 홀로그램을 사용자 로밍 정도 관계 없이 실제 세계의 위치에 정확 하 게 클러스터를 잠글 수 고 [다시에서 나중에 이러한 홀로그램을 찾습니다 세션](coordinate-systems.md#spatial-anchor-persistence)합니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-140">One key technique you'll use is to create a [spatial anchor](coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, regardless of how far the user has roamed, and then [find those holograms again in later sessions](coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="c9713-141">Unity에서 만든 공간 앵커를 추가 하 여 합니다 **WorldAnchor** Unity 구성 요소는 GameObject 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-141">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="c9713-142">전 세계 앵커를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-142">Adding a World Anchor</span></span>

<span data-ttu-id="c9713-143">전 세계 앵커를 추가 하려면 AddComponent 호출<WorldAnchor>실제 환경에서 고정 하려는 변환 사용 하 여 게임 개체 ().</span><span class="sxs-lookup"><span data-stu-id="c9713-143">To add a world anchor, call AddComponent<WorldAnchor>() on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="c9713-144">정말 간단하죠.</span><span class="sxs-lookup"><span data-stu-id="c9713-144">That's it!</span></span> <span data-ttu-id="c9713-145">이 게임 개체 물리적 세계의 현재 위치에 고정 될 이제-실제 정렬 되도록 시간이 지남에 따라 약간씩 조정 Unity 세계 좌표 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-145">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="c9713-146">사용 하 여 [지 속성](persistence-in-unity.md) 이후 앱 세션에 다시 고정 된 위치에서이 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-146">Use [persistence](persistence-in-unity.md) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="c9713-147">전 세계 앵커를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-147">Removing a World Anchor</span></span>

<span data-ttu-id="c9713-148">경우 더 이상 실제 위치로 잠겨 GameObject 이동이 프레임에서 원하지, 다음 호출할 수 없습니다만 Destroy World 앵커 구성 요소.</span><span class="sxs-lookup"><span data-stu-id="c9713-148">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="c9713-149">이 프레임 GameObject를 이동 하려는 경우 대신 DestroyImmediate를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-149">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="c9713-150">GameObject를 고정 하는 세계를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-150">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="c9713-151">GameObject의에 전 세계 앵커를 이동할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-151">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="c9713-152">이 프레임 GameObject를 이동 해야 할 경우에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-152">If you need to move the GameObject this frame, you need to:</span></span>
1. <span data-ttu-id="c9713-153">DestroyImmediate World 앵커 구성 요소</span><span class="sxs-lookup"><span data-stu-id="c9713-153">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="c9713-154">GameObject를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-154">Move the GameObject</span></span>
3. <span data-ttu-id="c9713-155">GameObject를 새로운 세계 앵커 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-155">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="c9713-156">Locatability 변경 내용 처리</span><span class="sxs-lookup"><span data-stu-id="c9713-156">Handling Locatability Changes</span></span>

<span data-ttu-id="c9713-157">WorldAnchor 아닐 찾을 수 있는 시점의 실제 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-157">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="c9713-158">발생 하는 경우 Unity가 되지 업데이트할 고정 된 개체의 변환입니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-158">If that occurs, Unity will not be updating the transform of the anchored object.</span></span> <span data-ttu-id="c9713-159">이 변경할 수도 응용 프로그램이 실행 되는 동안.</span><span class="sxs-lookup"><span data-stu-id="c9713-159">This also can change while an app is running.</span></span> <span data-ttu-id="c9713-160">Locatability에서 변경을 처리 하지 못했습니다 전 세계에서 올바른 물리적 위치에 표시 되지 않도록 개체에 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-160">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="c9713-161">Locatability 변경에 대 한 알림을 받으려면:</span><span class="sxs-lookup"><span data-stu-id="c9713-161">To be notified about locatability changes:</span></span>
1. <span data-ttu-id="c9713-162">OnTrackingChanged 이벤트 구독</span><span class="sxs-lookup"><span data-stu-id="c9713-162">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="c9713-163">이벤트 처리</span><span class="sxs-lookup"><span data-stu-id="c9713-163">Handle the event</span></span>

<span data-ttu-id="c9713-164">합니다 **OnTrackingChanged** 이벤트에 내부 공간 앵커 되지 과정이 및 과정이 중인 상태의 간에 변경 될 때마다 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-164">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="c9713-165">다음 이벤트를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-165">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="c9713-166">경우에 따라 앵커 위치 즉시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-166">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="c9713-167">이 isLocated 속성 앵커의 경우 true로 설정 됩니다 여기서 AddComponent<WorldAnchor>()를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-167">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="c9713-168">결과적으로, OnTrackingChanged 이벤트는 트리거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-168">As a result, the OnTrackingChanged event will not be triggered.</span></span> <span data-ttu-id="c9713-169">정리 패턴을 앵커를 연결한 후 초기 IsLocated 상태로 OnTrackingChanged 처리기를 호출 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-169">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a><span data-ttu-id="c9713-170">장치에서 앵커를 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-170">Sharing anchors across devices</span></span>

<span data-ttu-id="c9713-171">사용할 수 있습니다 <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 공간 앵커</a> 앱 여러 HoloLens, iOS 및 Android 장치에서 찾을 수 있는 로컬 WorldAnchor에서 견고한 클라우드 앵커를 만들려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-171">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="c9713-172">일반적인 공간 앵커를 여러 장치를 공유 각 사용자는 동일한 실제 위치에 해당 앵커에 상대적인 렌더링 된 콘텐츠를 볼 수입니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-172">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="c9713-173">따라서 실시간 공유 환경.</span><span class="sxs-lookup"><span data-stu-id="c9713-173">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="c9713-174">5 분을 사용해으로 시작 하려면 Unity에서 공유 환경을 구축 <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">빠른 시작 Azure 공간 앵커 Unity</a>합니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-174">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="c9713-175">Azure 공간 앵커를 사용 하 여 실행을 했으면 할 수 있습니다 <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Unity에서 앵커를 찾아서 만들</a>합니다.</span><span class="sxs-lookup"><span data-stu-id="c9713-175">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="see-also"></a><span data-ttu-id="c9713-176">관련 항목</span><span class="sxs-lookup"><span data-stu-id="c9713-176">See Also</span></span>
* [<span data-ttu-id="c9713-177">환경 확장</span><span class="sxs-lookup"><span data-stu-id="c9713-177">Experience scales</span></span>](coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="c9713-178">공간 단계</span><span class="sxs-lookup"><span data-stu-id="c9713-178">Spatial stage</span></span>](coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="c9713-179">Unity에서 손실 추적</span><span class="sxs-lookup"><span data-stu-id="c9713-179">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="c9713-180">공간 앵커</span><span class="sxs-lookup"><span data-stu-id="c9713-180">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="c9713-181">Unity의 지 속성</span><span class="sxs-lookup"><span data-stu-id="c9713-181">Persistence in Unity</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="c9713-182">Unity에서 공유 경험</span><span class="sxs-lookup"><span data-stu-id="c9713-182">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)
* <span data-ttu-id="c9713-183"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 공간 앵커</a></span><span class="sxs-lookup"><span data-stu-id="c9713-183"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="c9713-184"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure 공간 앵커 Unity 용 SDK</a></span><span class="sxs-lookup"><span data-stu-id="c9713-184"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>