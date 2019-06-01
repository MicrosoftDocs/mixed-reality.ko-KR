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
# <a name="head-gaze-in-unity"></a><span data-ttu-id="7b979-104">Unity에서 Head 응시</span><span class="sxs-lookup"><span data-stu-id="7b979-104">Head gaze in Unity</span></span>

<span data-ttu-id="7b979-105">[Gaze](gaze.md) 대상 사용자에 대 한 기본 방법이 합니다 [홀로그램](hologram.md) 에서 앱을 만듭니다 [혼합 현실](mixed-reality.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="7b979-105">[Gaze](gaze.md) is a primary way for users to target the [holograms](hologram.md) your app creates in [Mixed Reality](mixed-reality.md).</span></span>


## <a name="implementing-head-gaze"></a><span data-ttu-id="7b979-106">헤드 게이즈 구현</span><span class="sxs-lookup"><span data-stu-id="7b979-106">Implementing head gaze</span></span>

<span data-ttu-id="7b979-107">개념상 [gaze](gaze.md) 앞쪽으로 연결 되 고 확인 된 헤드셋 인 사용자의 헤드 광선을 그린 프로젝션에 의해 구현 됩니다 광선와 충돌 하는 어떤 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b979-107">Conceptually, [gaze](gaze.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span> <span data-ttu-id="7b979-108">Unity 주를 통해 사용자의 헤드 위치 및 방향 unity에서 노출 [카메라](camera-in-unity.md), 특히 [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) 하 고 [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html)합니다.</span><span class="sxs-lookup"><span data-stu-id="7b979-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="7b979-109">호출 [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) 결과 [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) 충돌이 발생 한 3D 지점을 포함 하 여 충돌 및 기타 GameObject 게이즈 광선에 대 한 정보를 포함 하는 구조체 와 충돌 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b979-109">Calling [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the gaze ray collided with.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="7b979-110">예: 헤드 게이즈 구현</span><span class="sxs-lookup"><span data-stu-id="7b979-110">Example: Implement head gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="7b979-111">최선의 구현 방법</span><span class="sxs-lookup"><span data-stu-id="7b979-111">Best Practices</span></span>

<span data-ttu-id="7b979-112">위의 예제는 단일 raycast 게이즈 대상을 찾으려면 업데이트 루프에서를 수행 하는 방법, 하는 동안 잠재적으로 관심 있는 개체에 gazed 되는 모든 개체에서이 작업을 수행 하는 대신 게이즈를 관리 하는 단일 개체에서이 작업을 수행 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7b979-112">While the example above demonstrates how to do a single raycast in an update loop to find the Gaze target, it is recommended to do this in a single object managing gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="7b979-113">이렇게 하면 하나만 게이즈 raycast 각 프레임을 수행 하 여 처리를 저장 하는 앱 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b979-113">This lets your app save processing by doing just one gaze raycast each frame.</span></span>

## <a name="visualizing-gaze"></a><span data-ttu-id="7b979-114">게이즈를 시각화합니다.</span><span class="sxs-lookup"><span data-stu-id="7b979-114">Visualizing Gaze</span></span>

<span data-ttu-id="7b979-115">콘텐츠를 사용 하 여 대상 및 상호 작용을 마우스 포인터로 사용 하는 위치는 바탕 화면에서 구현 해야 하는 것 처럼를 [커서](cursors.md) 사용자 게이즈를 나타내는입니다.</span><span class="sxs-lookup"><span data-stu-id="7b979-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](cursors.md) that represents the user's gaze.</span></span> <span data-ttu-id="7b979-116">에 사용자의 신뢰를 이렇게 거 든 상호 작용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b979-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="gaze-in-mixed-reality-toolkit-v2"></a><span data-ttu-id="7b979-117">혼합된 현실에서 gaze Toolkit v2</span><span class="sxs-lookup"><span data-stu-id="7b979-117">Gaze in Mixed Reality Toolkit v2</span></span>
<span data-ttu-id="7b979-118">게이즈를 액세스할 수 있습니다 합니다 [Manager 입력](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) MRTK v2의 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b979-118">You can access gaze from the [input Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK v2.</span></span>

## <a name="see-also"></a><span data-ttu-id="7b979-119">참조</span><span class="sxs-lookup"><span data-stu-id="7b979-119">See also</span></span>
* [<span data-ttu-id="7b979-120">카메라</span><span class="sxs-lookup"><span data-stu-id="7b979-120">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="7b979-121">응시 입력</span><span class="sxs-lookup"><span data-stu-id="7b979-121">Gaze input</span></span>](gaze.md)
* [<span data-ttu-id="7b979-122">커서</span><span class="sxs-lookup"><span data-stu-id="7b979-122">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="7b979-123">응시 대상 지정</span><span class="sxs-lookup"><span data-stu-id="7b979-123">Gaze targeting</span></span>](gaze-targeting.md)
