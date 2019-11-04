---
title: Unity의 포커스 지점
description: 포커스 지점을 설정 하 여 Unity에서 홀로그램 안정성 수동 조정
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, 포커스 지점, 포커스 평면, 안정화 평면, 안정화 지점, reprojection, LSR, 깊이 버퍼
ms.openlocfilehash: d48f6f1878a68a17be263f10b809229dc2705c58
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435419"
---
# <a name="focus-point-in-unity"></a><span data-ttu-id="5fa56-104">Unity의 포커스 지점</span><span class="sxs-lookup"><span data-stu-id="5fa56-104">Focus point in Unity</span></span>

<span data-ttu-id="5fa56-105">**네임 스페이스:** *unityengine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="5fa56-105">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="5fa56-106">**유형**: *HolographicSettings*</span><span class="sxs-lookup"><span data-stu-id="5fa56-106">**Type**: *HolographicSettings*</span></span>

<span data-ttu-id="5fa56-107">현재 표시 되는 holograms에서 안정화를 가장 잘 수행 하는 방법에 대 한 힌트를 HoloLens에 제공 하도록 [포커스 지점을](hologram-stability.md#reprojection) 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fa56-107">The [focus point](hologram-stability.md#reprojection) can be set to provide HoloLens a hint about how to best perform stabilization on the holograms currently being displayed.</span></span>

<span data-ttu-id="5fa56-108">Unity에서 포커스 지점을 설정 하려면 *HolographicSettings. SetFocusPointForFrame ()* 를 사용 하 여 모든 프레임을 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5fa56-108">If you want to set the Focus Point in Unity, it needs to be set every frame using *HolographicSettings.SetFocusPointForFrame()*.</span></span> <span data-ttu-id="5fa56-109">프레임에 대 한 포커스 지점이 설정 되지 않은 경우 기본 안정화 평면이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5fa56-109">If the Focus Point is not set for a frame, the default stabilization plane will be used.</span></span>

> [!NOTE]
> <span data-ttu-id="5fa56-110">기본적으로 새 Unity 프로젝트에는 "깊이 버퍼 공유 사용" 옵션이 설정 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fa56-110">By default, new Unity projects have the "Enable Depth Buffer Sharing" option set.</span></span>  <span data-ttu-id="5fa56-111">이 옵션을 사용 하는 경우 Windows 10 4 월 2018 업데이트 (RS4) 이상을 실행 하는 몰입 형 데스크톱 헤드셋 또는 HoloLens에서 실행 되는 Unity 앱은 앱이 자동으로 포커스 지점:</span><span class="sxs-lookup"><span data-stu-id="5fa56-111">With this option, a Unity app running on either an immersive desktop headset or a HoloLens running the Windows 10 April 2018 Update (RS4) or later will submit your depth buffer to Windows to optimize hologram stability automatically, without your app specifying a focus point:</span></span>
> * <span data-ttu-id="5fa56-112">모던 데스크톱 헤드셋에서 픽셀 단위 깊이 기반 재 프로젝션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5fa56-112">On an immersive desktop headset, this will enable per-pixel depth-based reprojection.</span></span>
> * <span data-ttu-id="5fa56-113">Windows 10 4 월 2018 업데이트 이상을 실행 하는 HoloLens에서이는 깊이 버퍼를 분석 하 여 최적의 안정화 평면을 자동으로 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5fa56-113">On a HoloLens running the Windows 10 April 2018 Update or later, this will analyze the depth buffer to pick an optimal stabilization plane automatically.</span></span>
>
> <span data-ttu-id="5fa56-114">이러한 방법 중 하나는 각 프레임의 포커스 지점을 선택 하기 위해 앱에서 명시적으로 작업 하지 않고도 이미지 품질을 더욱 개선 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5fa56-114">Either approach should provide even better image quality without explicit work by your app to select a focus point each frame.</span></span>  <span data-ttu-id="5fa56-115">포커스 지점을 수동으로 제공 하는 경우 위에서 설명한 자동 동작이 재정의 되 고 일반적으로 홀로그램 안정성이 감소 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5fa56-115">Note that if you do provide a focus point manually, that will override the automatic behavior described above, and will usually reduce hologram stability.</span></span>  <span data-ttu-id="5fa56-116">일반적으로 Windows 10 4 월 2018 업데이트로 아직 업데이트 되지 않은 HoloLens에서 앱이 실행 되는 경우에만 수동 포커스 지점을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5fa56-116">Generally, you should only specify a manual focus point when your app is running on a HoloLens that has not yet been updated to the Windows 10 April 2018 Update.</span></span>

### <a name="example"></a><span data-ttu-id="5fa56-117">예</span><span class="sxs-lookup"><span data-stu-id="5fa56-117">Example</span></span>

<span data-ttu-id="5fa56-118">*SetFocusPointForFrame* 정적 함수에서 사용할 수 있는 오버 로드에 의해 제안 된 대로 포커스 지점을 설정 하는 방법에는 여러 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fa56-118">There are many ways to set the Focus Point, as suggested by the overloads available on the *SetFocusPointForFrame* static function.</span></span> <span data-ttu-id="5fa56-119">아래에는 제공 된 개체의 각 프레임에 포커스 평면을 설정 하는 간단한 예제가 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fa56-119">Presented below is a simple example to set the focus plane to the provided object each frame:</span></span>

```cs
public GameObject focusedObject;
void Update()
{
    // Normally the normal is best set to be the opposite of the main camera's 
    // forward vector.
    // If the content is actually all on a plane (like text), set the normal to 
    // the normal of the plane and ensure the user does not pass through the 
    // plane.
    var normal = -Camera.main.transform.forward;     
    var position = focusedObject.transform.position;
    UnityEngine.XR.WSA.HolographicSettings.SetFocusPointForFrame(position, normal);
}
```

<span data-ttu-id="5fa56-120">위의 간단한 코드는 포커스가 있는 개체가 사용자 뒤에서 종료 되는 경우 홀로그램의 안정성을 낮출 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fa56-120">Note that the simple code above may end up reducing hologram stability if the focused object ends up behind the user.</span></span>  <span data-ttu-id="5fa56-121">따라서 일반적으로 포커스 지점을 수동으로 지정 하는 대신 "깊이 버퍼 공유 사용"을 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5fa56-121">This is why you should generally set "Enable Depth Buffer Sharing" instead of manually specifying a focus point.</span></span>

### <a name="see-also"></a><span data-ttu-id="5fa56-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5fa56-122">See also</span></span>
* [<span data-ttu-id="5fa56-123">안정화 평면</span><span class="sxs-lookup"><span data-stu-id="5fa56-123">Stabilization plane</span></span>](hologram-stability.md#reprojection)
