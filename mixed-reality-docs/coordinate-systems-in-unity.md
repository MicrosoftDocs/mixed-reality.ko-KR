---
title: Unity에서 시스템 좌표계
description: Unity에서 실제, 장소, 실내 확장 및 전 세계 혼합 현실 환경을 빌드하는 방법에 대해 알아보세요.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 좌표계, 공간 좌표계, 방향 전용, 고정 크기 조정, 대규모, 실내 규모, 전 세계 규모, 360 학위, 고가, 실내, 실내, 세계, 크기 조정, 위치, 방향, Unity, 앵커, 공간 앵커, 전 세계 고정, 전 세계 고정 세계 잠금, 본문 잠김, 본문 잠금, 추적 손실, locatability, 경계, recenter
ms.openlocfilehash: 36d74488b23587e5c89b40faf97921a10be7473b
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63525966"
---
# <a name="coordinate-systems-in-unity"></a><span data-ttu-id="c0251-104">Unity에서 시스템 좌표계</span><span class="sxs-lookup"><span data-stu-id="c0251-104">Coordinate systems in Unity</span></span>

<span data-ttu-id="c0251-105">Windows Mixed Reality는 규모에 상관 없이 공간 규모 앱을 통해 응용 프로그램을 수평으로 확장 하 여 규모에 상관 없이 광범위 한 [환경](coordinate-systems.md)에서 앱을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-105">Windows Mixed Reality supports apps across a wide range of [experience scales](coordinate-systems.md), from orientation-only and seated-scale apps up through room-scale apps.</span></span> <span data-ttu-id="c0251-106">HoloLens에서 더 나아가 사용자가 5 미터 이상 이동할 수 있도록 하는 세계적인 규모의 앱을 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-106">On HoloLens, you can go further and build world-scale apps that let users walk beyond 5 meters, exploring an entire floor of a building and beyond.</span></span>

<span data-ttu-id="c0251-107">Unity에서 혼합 현실 환경을 빌드하는 첫 번째 단계는 앱이 대상으로 하는 [환경 규모](coordinate-systems.md) 를 결정 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-107">Your first step in building a mixed reality experience in Unity is to determine which [experience scale](coordinate-systems.md) your app will target.</span></span>

## <a name="building-an-orientation-only-or-seated-scale-experience"></a><span data-ttu-id="c0251-108">방향 전용 또는 확장 된 환경 구축</span><span class="sxs-lookup"><span data-stu-id="c0251-108">Building an orientation-only or seated-scale experience</span></span>

<span data-ttu-id="c0251-109">**공간** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="c0251-109">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="c0251-110">**입력할** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="c0251-110">**Type:** *XRDevice*</span></span>

<span data-ttu-id="c0251-111">**방향 전용** 또는 통합 된 **환경을**구축 하려면 Unity를 고정 된 추적 공간 형식으로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-111">To build an **orientation-only** or **seated-scale experience**, you must set Unity to the Stationary tracking space type.</span></span> <span data-ttu-id="c0251-112">이를 통해 Unity의 세계 좌표계를 설정 하 여 [고정 된 참조 프레임](coordinate-systems.md#spatial-coordinate-systems)을 추적할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-112">This sets Unity's world coordinate system to track the [stationary frame of reference](coordinate-systems.md#spatial-coordinate-systems).</span></span> <span data-ttu-id="c0251-113">고정 추적 모드에서 카메라의 기본 위치 바로 앞에 있는 편집기에 배치 된 콘텐츠 (앞으로-Z)는 앱이 시작 될 때 사용자 앞에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-113">In the Stationary tracking mode, content placed in the editor just in front of the camera's default location (forward is -Z) will appear in front of the user when the app launches.</span></span>

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

<span data-ttu-id="c0251-114">**공간** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="c0251-114">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="c0251-115">**입력할** *InputTracking*</span><span class="sxs-lookup"><span data-stu-id="c0251-115">**Type:** *InputTracking*</span></span>

<span data-ttu-id="c0251-116">360도 비디오 뷰어 (위치 헤드 업데이트에서 환상 효과를 ruin)와 같은 순수한 **방향 전용 환경** 에서는 XR를 설정할 수 있습니다 [. InputTracking. disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) 을 true로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-116">For a pure **orientation-only experience** such as a 360-degree video viewer (where positional head updates would ruin the illusion), you can then set [XR.InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) to true:</span></span>

```cs
InputTracking.disablePositionalTracking = true;
```

<span data-ttu-id="c0251-117">사용자가 나중에 연결 된 원본을 recenter 할 수 있도록 하는 **확장 된 환경의**경우 XR를 호출할 수 있습니다 [. Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) 메서드:</span><span class="sxs-lookup"><span data-stu-id="c0251-117">For a **seated-scale experience**, to let the user later recenter the seated origin, you can call the [XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) method:</span></span>

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a><span data-ttu-id="c0251-118">대규모 또는 공간 확장 환경 구축</span><span class="sxs-lookup"><span data-stu-id="c0251-118">Building a standing-scale or room-scale experience</span></span>

<span data-ttu-id="c0251-119">**공간** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="c0251-119">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="c0251-120">**입력할** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="c0251-120">**Type:** *XRDevice*</span></span>

<span data-ttu-id="c0251-121">대규모 또는  **공간 규모의 경험**을 위해 바닥을 기준으로 콘텐츠를 넣어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-121">For a **standing-scale** or **room-scale experience**, you'll need to place content relative to the floor.</span></span> <span data-ttu-id="c0251-122">사용자의 층을 사용 하는 이유는 사용자의 정의 된 최고 수준 원점 및 선택적 대화방 경계를 나타내는 **[공간 단계](coordinate-systems.md#spatial-coordinate-systems)** 를 처음 실행 하는 동안 설정 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-122">You reason about the user's floor using the **[spatial stage](coordinate-systems.md#spatial-coordinate-systems)**, which represents the user's defined floor-level origin and optional room boundary, set up during first run.</span></span>

<span data-ttu-id="c0251-123">Unity가 바닥 수준에서 세계 좌표계를 사용 하 여 작동 하도록 하려면 Unity를 RoomScale 추적 공간 형식으로 설정 하 고 해당 집합이 성공 하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-123">To ensure that Unity is operating with its world coordinate system at floor-level, you can set Unity to the RoomScale tracking space type, and ensure that the set succeeds:</span></span>

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
* <span data-ttu-id="c0251-124">SetTrackingSpaceType가 true를 반환 하는 경우 Unity는 세계 좌표계를 정상적으로 전환 하 여 [참조의 스테이지 프레임](coordinate-systems.md#spatial-coordinate-systems)을 추적 했습니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-124">If SetTrackingSpaceType returns true, Unity has successfully switched its world coordinate system to track the [stage frame of reference](coordinate-systems.md#spatial-coordinate-systems).</span></span>
* <span data-ttu-id="c0251-125">SetTrackingSpaceType가 false를 반환 하는 경우 Unity는 사용자가 환경에서 한 층도 설정 하지 않았기 때문에 참조의 스테이지 프레임으로 전환할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-125">If SetTrackingSpaceType returns false, Unity was unable to switch to the stage frame of reference, likely because the user has not set up even a floor in their environment.</span></span> <span data-ttu-id="c0251-126">이는 일반적이 지 않지만 다른 방에 단계를 설정 하 고 사용자가 새 단계를 설정 하지 않고 장치를 현재 대화방으로 이동한 경우에 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-126">This is not common, but can happen if the stage was set up in a different room and the device was moved to the current room without the user setting up a new stage.</span></span>

<span data-ttu-id="c0251-127">앱이 RoomScale 추적 공간 유형을 성공적으로 설정 하면 y = 0 평면에 배치 된 콘텐츠가 바닥에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-127">Once your app successfully sets the RoomScale tracking space type, content placed on the y=0 plane will appear on the floor.</span></span> <span data-ttu-id="c0251-128">(0, 0, 0)의 원점은 사용자가 대화방을 설치 하는 동안 구현 하는 바닥의 특정 위치가 되며,-Z는 설치 중에 전달 된 정방향 방향을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-128">The origin at (0, 0, 0) will be the specific place on the floor where the user stood during room setup, with -Z representing the forward direction they were facing during setup.</span></span>

<span data-ttu-id="c0251-129">**공간** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="c0251-129">**Namespace:** *UnityEngine.Experimental.XR*</span></span><br>
<span data-ttu-id="c0251-130">**입력할** *상한을*</span><span class="sxs-lookup"><span data-stu-id="c0251-130">**Type:** *Boundary*</span></span>

<span data-ttu-id="c0251-131">그런 다음 스크립트 코드에서 TryGetGeometry 메서드를 호출할 수 있습니다. XR 형식으로 경계 다각형을 가져오고 TrackedArea 경계 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-131">In script code, you can then call the TryGetGeometry method on your the UnityEngine.Experimental.XR.Boundary type to get a boundary polygon, specifying a boundary type of TrackedArea.</span></span> <span data-ttu-id="c0251-132">사용자가 경계 (꼭 짓 점 목록)를 정의 하는 경우 사용자에 게 **공간 확장 환경을** 제공 하 여 사용자가 만든 장면을 살펴볼 수 있다는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-132">If the user defined a boundary (you get back a list of vertices), you know it is safe to deliver a **room-scale experience** to the user, where they can walk around the scene you create.</span></span>

<span data-ttu-id="c0251-133">사용자가 접근 하면 시스템에서 자동으로 경계를 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-133">Note that the system will automatically render the boundary when the user approaches it.</span></span> <span data-ttu-id="c0251-134">앱은 경계 자체를 렌더링 하기 위해이 다각형을 사용할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-134">Your app does not need to use this polygon to render the boundary itself.</span></span> <span data-ttu-id="c0251-135">그러나이 경계 다각형을 사용 하 여 장면 개체의 레이아웃을 선택 하 여 사용자가 teleporting 없이 해당 개체에 실제로 연결할 수 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-135">However, you may choose to lay out your scene objects using this boundary polygon, to ensure the user can physically reach those objects without teleporting:</span></span>

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="c0251-136">세계 최고 규모 환경 구축</span><span class="sxs-lookup"><span data-stu-id="c0251-136">Building a world-scale experience</span></span>

<span data-ttu-id="c0251-137">**공간** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="c0251-137">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="c0251-138">**입력할** *WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="c0251-138">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="c0251-139">사용자가 5 미터를 wander 수 있도록 하는 HoloLens의 진정한 **세계 규모 환경** 에서는 공간 규모 환경에 사용 되는 기술이 아닌 새로운 기술이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-139">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="c0251-140">사용할 수 있는 한 가지 핵심 기술은 사용자가 로밍 하는 정도에 관계 없이 실제 세계에서 holograms 클러스터를 정확 하 게 잠그는 [공간 앵커](coordinate-systems.md#spatial-anchors) 를 만든 다음 [이후 세션에서 해당 holograms를 다시 찾는](coordinate-systems.md#spatial-anchor-persistence)것입니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-140">One key technique you'll use is to create a [spatial anchor](coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, regardless of how far the user has roamed, and then [find those holograms again in later sessions](coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="c0251-141">Unity에서는 GameObject에 **WorldAnchor** Unity 구성 요소를 추가 하 여 공간 앵커를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-141">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="c0251-142">세계 앵커 추가</span><span class="sxs-lookup"><span data-stu-id="c0251-142">Adding a World Anchor</span></span>

<span data-ttu-id="c0251-143">세계 앵커를 추가 하려면 실제 지역에서 고정<WorldAnchor>하려는 변환을 사용 하 여 game 개체에서 addcomponent ()를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-143">To add a world anchor, call AddComponent<WorldAnchor>() on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="c0251-144">정말 간단하죠.</span><span class="sxs-lookup"><span data-stu-id="c0251-144">That's it!</span></span> <span data-ttu-id="c0251-145">이 게임 개체는 이제 실제 세계의 현재 위치에 고정 되어 있습니다 .이를 통해 Unity 세계 좌표가 약간 조정 되어 물리적 맞춤을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-145">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="c0251-146">[지 속성](persistence-in-unity.md) 을 사용 하 여 이후 앱 세션에서이 앵커 된 위치를 다시 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-146">Use [persistence](persistence-in-unity.md) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="c0251-147">세계 앵커 제거</span><span class="sxs-lookup"><span data-stu-id="c0251-147">Removing a World Anchor</span></span>

<span data-ttu-id="c0251-148">GameObject를 실제 세계 위치로 잠글 필요가 없으며이 프레임으로 이동 하지 않으려면 세계 앵커 구성 요소에 대해 소멸을 호출 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-148">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="c0251-149">GameObject이 프레임을 이동 하려면 DestroyImmediate를 대신 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-149">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="c0251-150">세계 고정 GameObject 이동</span><span class="sxs-lookup"><span data-stu-id="c0251-150">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="c0251-151">GameObject은 세계 앵커가 있는 동안 이동할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-151">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="c0251-152">GameObject이 프레임을 이동 해야 하는 경우 다음을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-152">If you need to move the GameObject this frame, you need to:</span></span>
1. <span data-ttu-id="c0251-153">세계 앵커 구성 요소 DestroyImmediate</span><span class="sxs-lookup"><span data-stu-id="c0251-153">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="c0251-154">GameObject 이동</span><span class="sxs-lookup"><span data-stu-id="c0251-154">Move the GameObject</span></span>
3. <span data-ttu-id="c0251-155">GameObject에 새 세계 앵커 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-155">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="c0251-156">Locatability 변경 내용 처리</span><span class="sxs-lookup"><span data-stu-id="c0251-156">Handling Locatability Changes</span></span>

<span data-ttu-id="c0251-157">WorldAnchor는 특정 시점에 물리적 세계에 과정이 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-157">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="c0251-158">이런 경우 Unity는 고정 된 개체의 변환을 업데이트 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-158">If that occurs, Unity will not be updating the transform of the anchored object.</span></span> <span data-ttu-id="c0251-159">이는 앱이 실행 되는 동안에도 변경 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-159">This also can change while an app is running.</span></span> <span data-ttu-id="c0251-160">Locatability의 변경을 처리 하지 못하면 개체가 전 세계의 올바른 물리적 위치에 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-160">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="c0251-161">Locatability 변경 내용에 대 한 알림이 표시 되는 경우:</span><span class="sxs-lookup"><span data-stu-id="c0251-161">To be notified about locatability changes:</span></span>
1. <span data-ttu-id="c0251-162">OnTrackingChanged 이벤트 구독</span><span class="sxs-lookup"><span data-stu-id="c0251-162">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="c0251-163">이벤트를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-163">Handle the event</span></span>

<span data-ttu-id="c0251-164">**Ontrackingchanged** 이벤트는 기본 공간 앵커가 과정이의 상태와 과정이 되지 않는 사이에 변경 될 때마다 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-164">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="c0251-165">그런 다음 이벤트를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-165">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="c0251-166">경우에 따라 앵커가 즉시 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-166">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="c0251-167">이 경우 addcomponent<WorldAnchor>()가 반환 되 면 앵커의이 islocated 속성은 true로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-167">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="c0251-168">따라서 OnTrackingChanged 이벤트가 트리거되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-168">As a result, the OnTrackingChanged event will not be triggered.</span></span> <span data-ttu-id="c0251-169">깨끗 한 패턴은 앵커를 연결한 후 초기 IsLocated 상태를 사용 하 여 OnTrackingChanged 처리기를 호출 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-169">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a><span data-ttu-id="c0251-170">장치에서 앵커 공유</span><span class="sxs-lookup"><span data-stu-id="c0251-170">Sharing anchors across devices</span></span>

<span data-ttu-id="c0251-171"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 공간 앵커</a> 를 사용 하 여 로컬 WorldAnchor에서 지속적인 클라우드 앵커를 만들 수 있습니다. 그러면 앱이 여러 HoloLens, IOS 및 Android 장치에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-171">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="c0251-172">여러 장치에서 공통 공간 앵커를 공유 하 여 각 사용자는 동일한 물리적 위치에서 해당 앵커에 대해 렌더링 된 콘텐츠를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-172">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="c0251-173">이렇게 실제 세계 공유 환경을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-173">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="c0251-174">Unity에서 공유 환경 빌드를 시작 하려면 5 분 <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure 공간 앵커 Unity 퀵 스타트</a>를 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="c0251-174">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="c0251-175">Azure 공간 앵커를 사용 하 여 실행 하면 <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Unity에서 앵커를 만들고 찾을</a>수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c0251-175">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="see-also"></a><span data-ttu-id="c0251-176">관련 항목</span><span class="sxs-lookup"><span data-stu-id="c0251-176">See Also</span></span>
* [<span data-ttu-id="c0251-177">환경 크기 조정</span><span class="sxs-lookup"><span data-stu-id="c0251-177">Experience scales</span></span>](coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="c0251-178">공간 스테이지</span><span class="sxs-lookup"><span data-stu-id="c0251-178">Spatial stage</span></span>](coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="c0251-179">Unity의 손실 추적</span><span class="sxs-lookup"><span data-stu-id="c0251-179">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="c0251-180">공간 앵커</span><span class="sxs-lookup"><span data-stu-id="c0251-180">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="c0251-181">Unity의 지속성</span><span class="sxs-lookup"><span data-stu-id="c0251-181">Persistence in Unity</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="c0251-182">Unity의 공유 환경</span><span class="sxs-lookup"><span data-stu-id="c0251-182">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)
* <span data-ttu-id="c0251-183"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="c0251-183"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="c0251-184"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Unity 용 Azure 공간 앵커 SDK</a></span><span class="sxs-lookup"><span data-stu-id="c0251-184"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>