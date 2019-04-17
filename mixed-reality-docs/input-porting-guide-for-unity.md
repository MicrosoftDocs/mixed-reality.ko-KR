---
title: 포팅 가이드 Unity에 대 한 입력
description: Windows Mixed Reality Unity에 대 한 입력을 처리 하는 방법에 알아봅니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 입력, unity, 이식
ms.openlocfilehash: 20e8efa09d20b0a9eaa246015d9c185884f9c216
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602790"
---
# <a name="input-porting-guide-for-unity"></a><span data-ttu-id="c3154-104">포팅 가이드 Unity에 대 한 입력</span><span class="sxs-lookup"><span data-stu-id="c3154-104">Input porting guide for Unity</span></span>

<span data-ttu-id="c3154-105">Windows Mixed Reality 여러 플랫폼에 걸쳐 있는 Unity의 일반 Input.GetButton/GetAxis Api 또는 Windows 관련 XR 두 가지 방법 중 하나를 사용 하기 위한 입력된 논리를 이식할 수 있습니다. WSA입니다. 입력된 Api에 맞게 다양 한 데이터를 제공 하는 컨트롤러 동작 및 HoloLens 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3154-105">You can port your input logic to Windows Mixed Reality using one of two approaches, Unity's general Input.GetButton/GetAxis APIs that span across multiple platforms, or the Windows-specific XR.WSA.Input APIs that offer richer data specifically for motion controllers and HoloLens hands.</span></span>

## <a name="general-inputgetbuttongetaxis-apis"></a><span data-ttu-id="c3154-106">일반 Input.GetButton/GetAxis Api</span><span class="sxs-lookup"><span data-stu-id="c3154-106">General Input.GetButton/GetAxis APIs</span></span>

<span data-ttu-id="c3154-107">Unity에 대 한 입력을 노출 하는 일반 Input.GetButton/Input.GetAxis Api를 현재 사용 [Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html) 하 고 [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html)합니다.</span><span class="sxs-lookup"><span data-stu-id="c3154-107">Unity currently uses its general Input.GetButton/Input.GetAxis APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html) and [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html).</span></span> <span data-ttu-id="c3154-108">앱을 이미 사용 중인 이러한 Api 입력에 대 한 경우 Windows Mixed Reality에서 동작 컨트롤러를 지원 하기 위한 가장 쉬운 경로입니다: 단추 및 축 입력 관리자를 다시 매핑할 하기만 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3154-108">If your apps are already using these APIs for input, this is the easiest path for supporting motion controllers in Windows Mixed Reality: you should just need to remap buttons and axes in the Input Manager.</span></span>

<span data-ttu-id="c3154-109">자세한 내용은 참조 하세요. 합니다 [Unity 단추/축 매핑 테이블](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) 하며 [일반적인 Unity Api 개요](gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis)합니다.</span><span class="sxs-lookup"><span data-stu-id="c3154-109">For more information, see the [Unity button/axis mapping table](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) and the [overview of the common Unity APIs](gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis).</span></span>

## <a name="windows-specific-xrwsainput-apis"></a><span data-ttu-id="c3154-110">Windows-specific XR.WSA.Input APIs</span><span class="sxs-lookup"><span data-stu-id="c3154-110">Windows-specific XR.WSA.Input APIs</span></span>

<span data-ttu-id="c3154-111">앱에는 이미 각 플랫폼에 대 한 사용자 지정 입력된 논리 빌드를 하는 경우 아래에서 Windows 특정 공간 입력된 Api를 사용 하도록 선택할 수 있습니다 합니다 **UnityEngine.XR.WSA.Input** 네임 스페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="c3154-111">If your app already builds custom input logic for each platform, you can choose to use the Windows-specific spatial input APIs under the **UnityEngine.XR.WSA.Input** namespace.</span></span> <span data-ttu-id="c3154-112">이 기능을 사용 하면 위치 정확도 같은 추가 정보 또는 실습 및 컨트롤러 떨어져 HoloLens에 알릴 수 있도록 원본 유형, 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3154-112">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart on HoloLens.</span></span>

<span data-ttu-id="c3154-113">자세한 내용은 참조는 [UnityEngine.XR.WSA.Input Api 개요](gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput)합니다.</span><span class="sxs-lookup"><span data-stu-id="c3154-113">For more information, see the [overview of the UnityEngine.XR.WSA.Input APIs](gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput).</span></span>

## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="c3154-114">그립 포즈 포인팅 포즈 비교</span><span class="sxs-lookup"><span data-stu-id="c3154-114">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="c3154-115">Windows Mixed Reality 다양 한 폼 팩터 동작 컨트롤러에서는, 각 컨트롤러의 디자인을 사용 하 여 렌더링할 때 가리키는 사용 해야 다른 사용자의 직접 위치 사이의 "전달" 방향 해당 앱의 자연 관계를 컨트롤러입니다.</span><span class="sxs-lookup"><span data-stu-id="c3154-115">Windows Mixed Reality supports motion controllers in a variety of form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="c3154-116">잘 표현 하기 위해 이러한 컨트롤러, 두 가지 종류의 포즈 각 상호 작용 원본에 대해 조사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c3154-116">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source:</span></span>

* <span data-ttu-id="c3154-117">합니다 **그립 포즈**, HoloLens, 감지한 손 모양 손바닥 또는 동작 컨트롤러를 보유 하는 손 안에서 가능 위치를 나타내는입니다.</span><span class="sxs-lookup"><span data-stu-id="c3154-117">The **grip pose**, representing the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>
    * <span data-ttu-id="c3154-118">몰입 형 헤드셋이이 포즈 가장 사용 렌더링 **사용자의 직접** 또는 **사용자의 직접에 보관 된 개체**검 또는 총 등입니다.</span><span class="sxs-lookup"><span data-stu-id="c3154-118">On immersive headsets, this pose is best used to render **the user's hand** or **an object held in the user's hand**, such as a sword or gun.</span></span>
    * <span data-ttu-id="c3154-119">합니다 **위치를 잡고**: 물론 컨트롤러를 보유 하는 경우 팜 중심 왼쪽 또는 오른쪽 가운데 그립 내의 위치를 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3154-119">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span>
    * <span data-ttu-id="c3154-120">합니다 **방향을 올바른 축 잡고**: 완전히 플랫 5 손가락 자세를 직접 열면 광선과 표준 프로그램 palm에서 (왼쪽된 palm, palm 오른쪽에서 이전 버전과에서 앞으로)</span><span class="sxs-lookup"><span data-stu-id="c3154-120">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
    * <span data-ttu-id="c3154-121">합니다 **방향을 정방향 축 잡고**: 부분적으로 (처럼 컨트롤러 보유) 직접을 닫을 때, 광선을 가리키는 "forward" 튜브를 통해 비 엄지 손가락으로 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="c3154-121">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
    * <span data-ttu-id="c3154-122">합니다 **축 위쪽 방향 잡고**: 오른쪽 정방향 정의 사용 권한에 포함 된 최대 축.</span><span class="sxs-lookup"><span data-stu-id="c3154-122">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>
    * <span data-ttu-id="c3154-123">그립 자세 하거나 Unity의 공급 업체 간 입력 API 통해 액세스할 수 있습니다 (**[xr 하이 있습니다. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)합니다. GetLocalPosition/Rotation**) 또는 Windows 관련 API를 통해 (**sourceState.sourcePose.TryGetPosition/Rotation**, 그립 포즈를 요청).</span><span class="sxs-lookup"><span data-stu-id="c3154-123">You can access the grip pose through either Unity's cross-vendor input API (**[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation**) or through the Windows-specific API (**sourceState.sourcePose.TryGetPosition/Rotation**, requesting the Grip pose).</span></span>
* <span data-ttu-id="c3154-124">합니다 **포인터 포즈**, 앞으로 가리키는 컨트롤러의 끝을 나타내는입니다.</span><span class="sxs-lookup"><span data-stu-id="c3154-124">The **pointer pose**, representing the tip of the controller pointing forward.</span></span>
    * <span data-ttu-id="c3154-125">이 포즈 raycast에 가장 적합 하면 **UI를 가리키는** 컨트롤러 모델 자체를 렌더링 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="c3154-125">This pose is best used to raycast when **pointing at UI** when you are rendering the controller model itself.</span></span>
    * <span data-ttu-id="c3154-126">현재 포인터 자세는 Windows 전용 API를 통해서만 사용할 수 있습니다 (**sourceState.sourcePose.TryGetPosition/Rotation**, 포인터 포즈를 요청).</span><span class="sxs-lookup"><span data-stu-id="c3154-126">Currently, the pointer pose is available only through the Windows-specific API (**sourceState.sourcePose.TryGetPosition/Rotation**, requesting the Pointer pose).</span></span>

<span data-ttu-id="c3154-127">이러한 자세 좌표 모든 Unity 영역 좌표에서 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c3154-127">These pose coordinates are all expressed in Unity world coordinates.</span></span>

## <a name="see-also"></a><span data-ttu-id="c3154-128">참조</span><span class="sxs-lookup"><span data-stu-id="c3154-128">See also</span></span>
* [<span data-ttu-id="c3154-129">컨트롤러 동작</span><span class="sxs-lookup"><span data-stu-id="c3154-129">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="c3154-130">제스처와 Unity의 동작 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="c3154-130">Gestures and motion controllers in Unity</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="c3154-131">UnityEngine.XR.WSA.Input</span><span class="sxs-lookup"><span data-stu-id="c3154-131">UnityEngine.XR.WSA.Input</span></span>](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [<span data-ttu-id="c3154-132">UnityEngine.XR.InputTracking</span><span class="sxs-lookup"><span data-stu-id="c3154-132">UnityEngine.XR.InputTracking</span></span>](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [<span data-ttu-id="c3154-133">포팅 가이드</span><span class="sxs-lookup"><span data-stu-id="c3154-133">Porting guides</span></span>](porting-guides.md)
