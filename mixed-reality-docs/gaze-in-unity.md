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
# <a name="gaze-in-unity"></a><span data-ttu-id="46f56-104">Unity에서 gaze</span><span class="sxs-lookup"><span data-stu-id="46f56-104">Gaze in Unity</span></span>

<span data-ttu-id="46f56-105">[Gaze](gaze.md) 대상 사용자에 대 한 기본 방법이 합니다 [홀로그램](hologram.md) 에서 앱을 만듭니다 [혼합 현실을](mixed-reality.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="46f56-105">[Gaze](gaze.md) is a primary way for users to target the [holograms](hologram.md) your app creates in [mixed reality](mixed-reality.md).</span></span>

## <a name="implementing-gaze"></a><span data-ttu-id="46f56-106">게이즈를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="46f56-106">Implementing Gaze</span></span>

<span data-ttu-id="46f56-107">개념상 [gaze](gaze.md) 앞쪽으로 연결 되 고 확인 된 헤드셋 인 사용자의 헤드 광선을 그린 프로젝션에 의해 구현 됩니다 광선와 충돌 하는 어떤 합니다.</span><span class="sxs-lookup"><span data-stu-id="46f56-107">Conceptually, [gaze](gaze.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span> <span data-ttu-id="46f56-108">Unity 주를 통해 사용자의 헤드 위치 및 방향 unity에서 노출 [카메라](camera-in-unity.md), 특히 [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) 하 고 [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[ transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html)합니다.</span><span class="sxs-lookup"><span data-stu-id="46f56-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](http://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](http://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](http://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="46f56-109">호출 [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) 결과 [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) 충돌이 발생 한 3D 지점을 포함 하 여 충돌 및 기타 GameObject 게이즈 광선에 대 한 정보를 포함 하는 구조체 와 충돌 합니다.</span><span class="sxs-lookup"><span data-stu-id="46f56-109">Calling [Physics.RayCast](http://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](http://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the gaze ray collided with.</span></span>

### <a name="example-implement-gaze"></a><span data-ttu-id="46f56-110">예: 구현 응시</span><span class="sxs-lookup"><span data-stu-id="46f56-110">Example: Implement Gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="46f56-111">최선의 구현 방법</span><span class="sxs-lookup"><span data-stu-id="46f56-111">Best Practices</span></span>

<span data-ttu-id="46f56-112">위의 예제는 단일 raycast 게이즈 대상을 찾으려면 업데이트 루프에서를 수행 하는 방법, 하는 동안 잠재적으로 관심 있는 개체에 gazed 되는 모든 개체에서이 작업을 수행 하는 대신 게이즈를 관리 하는 단일 개체에서이 작업을 수행 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="46f56-112">While the example above demonstrates how to do a single raycast in an update loop to find the Gaze target, it is recommended to do this in a single object managing gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="46f56-113">이렇게 하면 하나만 게이즈 raycast 각 프레임을 수행 하 여 처리를 저장 하는 앱 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46f56-113">This lets your app save processing by doing just one gaze raycast each frame.</span></span>

## <a name="visualizing-gaze"></a><span data-ttu-id="46f56-114">게이즈를 시각화합니다.</span><span class="sxs-lookup"><span data-stu-id="46f56-114">Visualizing Gaze</span></span>

<span data-ttu-id="46f56-115">콘텐츠를 사용 하 여 대상 및 상호 작용을 마우스 포인터로 사용 하는 위치는 바탕 화면에서 구현 해야 하는 것 처럼를 [커서](cursors.md) 사용자 게이즈를 나타내는입니다.</span><span class="sxs-lookup"><span data-stu-id="46f56-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](cursors.md) that represents the user's gaze.</span></span> <span data-ttu-id="46f56-116">에 사용자의 신뢰를 이렇게 거 든 상호 작용 합니다.</span><span class="sxs-lookup"><span data-stu-id="46f56-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="gaze-in-mixed-reality-toolkit"></a><span data-ttu-id="46f56-117">혼합된 현실 도구 키트의 gaze</span><span class="sxs-lookup"><span data-stu-id="46f56-117">Gaze in Mixed Reality Toolkit</span></span>
<span data-ttu-id="46f56-118">가져올 때 [MRTK Unity 패키지를 릴리스](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) 에서 프로젝트를 복제 또는 합니다 [GitHub 리포지토리](https://github.com/Microsoft/MixedRealityToolkit-Unity), Unity에서 새 메뉴 ' 혼합 현실 Toolkit'를 찾을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="46f56-118">When you import [MRTK release Unity packages](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) or clone the project from the [GitHub repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), you are going to find a new menu 'Mixed Reality Toolkit' in Unity.</span></span> <span data-ttu-id="46f56-119">'구성' 메뉴 아래에서 적용 혼합 현실 장면 [설정] 메뉴를 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="46f56-119">Under 'Configure' menu, you will see the menu 'Apply Mixed Reality Scene Settings'.</span></span> <span data-ttu-id="46f56-120">기본 카메라를 제거 하 고 기본 구성 요소 추가 클릭 하면 [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab)하십시오 [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), 및 [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab)합니다.</span><span class="sxs-lookup"><span data-stu-id="46f56-120">When you click it, it removes the default camera and adds foundational components - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), and [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).</span></span>

<span data-ttu-id="46f56-121">![장면 설치용 MRTK 메뉴](images/MRTK_Input_Menu.png)</span><span class="sxs-lookup"><span data-stu-id="46f56-121">![MRTK Menu for scene setup](images/MRTK_Input_Menu.png)</span></span><br>
<span data-ttu-id="46f56-122">*장면 설치용 MRTK 메뉴*</span><span class="sxs-lookup"><span data-stu-id="46f56-122">*MRTK Menu for scene setup*</span></span>

<span data-ttu-id="46f56-123">![MRTK 자동 장면 설치](images/MRTK_HowTo_Input1.png)</span><span class="sxs-lookup"><span data-stu-id="46f56-123">![Automatic scene setup in MRTK](images/MRTK_HowTo_Input1.png)</span></span><br>
<span data-ttu-id="46f56-124">*MRTK 자동 장면 설치*</span><span class="sxs-lookup"><span data-stu-id="46f56-124">*Automatic scene setup in MRTK*</span></span>

### <a name="gaze-related-scripts-in-mixed-reality-toolkit"></a><span data-ttu-id="46f56-125">혼합 현실 도구 키트의 관련된 스크립트 gaze</span><span class="sxs-lookup"><span data-stu-id="46f56-125">Gaze related scripts in Mixed Reality Toolkit</span></span>
<span data-ttu-id="46f56-126">혼합 현실 도구 키트의 prefab InputManager 포함 [GazeManager.cs](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeManager.cs) 하 고 [Gaze 안정기](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeStabilizer.cs)합니다.</span><span class="sxs-lookup"><span data-stu-id="46f56-126">Mixed Reality Toolkit's InputManager prefab includes [GazeManager.cs](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeManager.cs) and [Gaze Stabilizer](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Gaze/GazeStabilizer.cs).</span></span> <span data-ttu-id="46f56-127">아래 [SimpleSinglePointerSelector](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Focus/SimpleSinglePointerSelector.cs), 사용자 지정 커서를 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46f56-127">Under [SimpleSinglePointerSelector](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Focus/SimpleSinglePointerSelector.cs), you can assign your custom Cursor.</span></span> <span data-ttu-id="46f56-128">기본, 애니메이션 [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab) 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="46f56-128">In default, animated [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab) is assigned.</span></span>

<span data-ttu-id="46f56-129">[Cursor.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) 하 고 [CursorWithFeedback.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) 커서를 사용 하 여 게이즈를 시각화 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="46f56-129">[Cursor.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) and [CursorWithFeedback.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor) shows you how to visualize your Gaze using Cursors.</span></span>

## <a name="see-also"></a><span data-ttu-id="46f56-130">참조</span><span class="sxs-lookup"><span data-stu-id="46f56-130">See also</span></span>
* [<span data-ttu-id="46f56-131">카메라</span><span class="sxs-lookup"><span data-stu-id="46f56-131">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="46f56-132">응시</span><span class="sxs-lookup"><span data-stu-id="46f56-132">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="46f56-133">커서</span><span class="sxs-lookup"><span data-stu-id="46f56-133">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="46f56-134">대상으로 응시</span><span class="sxs-lookup"><span data-stu-id="46f56-134">Gaze targeting</span></span>](gaze-targeting.md)
