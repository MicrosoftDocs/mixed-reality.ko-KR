---
title: Unity에서 응시
description: 응시는 사용자가 혼합 현실에서 앱이 만드는 holograms를 대상으로 하는 기본 방법입니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 눈에 응시, 헤드-응시, unity, 홀로그램, 혼합 현실
ms.openlocfilehash: 8222a5199cc1ea35429f21e7490e1eff49fcd1bc
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435298"
---
# <a name="head-gaze-in-unity"></a><span data-ttu-id="00be4-104">헤드-Unity에서의 응시</span><span class="sxs-lookup"><span data-stu-id="00be4-104">Head-gaze in Unity</span></span>

<span data-ttu-id="00be4-105">[응시](gaze-and-commit.md) 는 사용자가 [혼합 현실](mixed-reality.md)에서 앱이 만드는 [holograms](hologram.md) 를 대상으로 하는 기본 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="00be4-105">[Gaze](gaze-and-commit.md) is a primary way for users to target the [holograms](hologram.md) your app creates in [Mixed Reality](mixed-reality.md).</span></span>


## <a name="implementing-head-gaze"></a><span data-ttu-id="00be4-106">헤드-응시 구현</span><span class="sxs-lookup"><span data-stu-id="00be4-106">Implementing head-gaze</span></span>

<span data-ttu-id="00be4-107">개념적으로 [head-응시](gaze-and-commit.md) 는 헤드셋이 있는 사용자 헤드의 광선을 전달 하 고, 정방향 방향으로, 광선이 충돌 하는 항목을 확인 하 여 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="00be4-107">Conceptually, [head-gaze](gaze-and-commit.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span> <span data-ttu-id="00be4-108">Unity에서 사용자의 헤드 위치와 방향은 Unity 기본 [카메라](camera-in-unity.md) [(구체적으로](https://docs.unity3d.com/ScriptReference/Camera-main.html)는 없음)를 통해 노출 됩니다. [transform. forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) 및 [Unityengine. Camera. main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [transform. position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="00be4-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="00be4-109">[물리학](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) 를 호출 하면 충돌이 발생 한 3d 지점과 다른 GameObject (헤드-응시 광선 충돌)를 포함 한 충돌에 대 한 정보가 포함 된 [Raycasthit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) 구조가 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="00be4-109">Calling [Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the head-gaze ray collided with.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="00be4-110">예: 헤드-응시 구현</span><span class="sxs-lookup"><span data-stu-id="00be4-110">Example: Implement head-gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="00be4-111">모범 사례</span><span class="sxs-lookup"><span data-stu-id="00be4-111">Best practices</span></span>

<span data-ttu-id="00be4-112">위의 예제에서는 업데이트 루프에서 단일 raycast를 수행 하 여 사용자의 헤드가 가리키는 대상을 찾는 방법을 보여 주지만, 개체에서이 작업을 수행 하는 대신 단일 개체에서이 작업을 수행 하는 것이 좋습니다. gazed입니다.</span><span class="sxs-lookup"><span data-stu-id="00be4-112">While the example above demonstrates how to do a single raycast in an update loop to find the target the user's head points at, it is recommended to do this in a single object managing head-gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="00be4-113">이를 통해 앱은 각 프레임을 하나의 헤드 (각 프레임)만 수행 하 여 처리를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00be4-113">This lets your app save processing by doing just one head-gaze raycast each frame.</span></span>

## <a name="visualizing-head-gaze"></a><span data-ttu-id="00be4-114">헤드 시각화-응시</span><span class="sxs-lookup"><span data-stu-id="00be4-114">Visualizing head-gaze</span></span>

<span data-ttu-id="00be4-115">마우스 포인터를 사용 하 여 콘텐츠를 대상으로 지정 하 고 상호 작용 하는 데스크톱과 마찬가지로 사용자의 헤드를 나타내는 [커서](cursors.md) 를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="00be4-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](cursors.md) that represents the user's head-gaze.</span></span> <span data-ttu-id="00be4-116">이렇게 하면 사용자가 상호 작용 하는 것에 대 한 확신을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00be4-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="head-gaze-in-the-mixed-reality-toolkit-v2"></a><span data-ttu-id="00be4-117">Mixed Reality Toolkit v 2의 Head-응시</span><span class="sxs-lookup"><span data-stu-id="00be4-117">Head-gaze in the Mixed Reality Toolkit v2</span></span>
<span data-ttu-id="00be4-118">MRTK v 2의 [입력 관리자](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) 에서 헤드-응시에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00be4-118">You can access head-gaze from the [Input Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK v2.</span></span>

## <a name="see-also"></a><span data-ttu-id="00be4-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="00be4-119">See also</span></span>
* [<span data-ttu-id="00be4-120">카메라</span><span class="sxs-lookup"><span data-stu-id="00be4-120">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="00be4-121">커서</span><span class="sxs-lookup"><span data-stu-id="00be4-121">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="00be4-122">헤드 게이즈 및 커밋</span><span class="sxs-lookup"><span data-stu-id="00be4-122">Head-gaze and commit</span></span>](gaze-and-commit.md)
