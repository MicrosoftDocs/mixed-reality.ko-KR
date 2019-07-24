---
title: Unity 용 입력 포팅 가이드
description: Unity에서 Windows Mixed Reality의 입력을 처리 하는 방법에 대해 알아봅니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 입력, unity, 포팅
ms.openlocfilehash: 20e8efa09d20b0a9eaa246015d9c185884f9c216
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63515491"
---
# <a name="input-porting-guide-for-unity"></a><span data-ttu-id="76bf7-104">Unity 용 입력 포팅 가이드</span><span class="sxs-lookup"><span data-stu-id="76bf7-104">Input porting guide for Unity</span></span>

<span data-ttu-id="76bf7-105">Unity의 일반 입력의 두 방법 중 하나를 사용 하 여 입력 논리를 Windows Mixed Reality로 이식할 수 있습니다. 여러 플랫폼에 걸쳐 있는 GetButton/Getbutton Api 또는 Windows 별 XR. WSA. 동작 컨트롤러 및 HoloLens 바늘에 대해 구체적으로 다양 한 데이터를 제공 하는 입력 Api</span><span class="sxs-lookup"><span data-stu-id="76bf7-105">You can port your input logic to Windows Mixed Reality using one of two approaches, Unity's general Input.GetButton/GetAxis APIs that span across multiple platforms, or the Windows-specific XR.WSA.Input APIs that offer richer data specifically for motion controllers and HoloLens hands.</span></span>

## <a name="general-inputgetbuttongetaxis-apis"></a><span data-ttu-id="76bf7-106">일반 입력. GetButton/Getbutton Api</span><span class="sxs-lookup"><span data-stu-id="76bf7-106">General Input.GetButton/GetAxis APIs</span></span>

<span data-ttu-id="76bf7-107">Unity는 현재 일반 입력을 사용 합니다. GetButton/Input. Getbutton Api를 사용 하 여 [Oculus sdk](https://docs.unity3d.com/Manual/OculusControllers.html) 및 [openvr sdk](https://docs.unity3d.com/Manual/OpenVRControllers.html)의 입력을 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="76bf7-107">Unity currently uses its general Input.GetButton/Input.GetAxis APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html) and [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html).</span></span> <span data-ttu-id="76bf7-108">앱이 입력에 이러한 Api를 이미 사용 하 고 있는 경우 Windows Mixed Reality에서 동작 컨트롤러를 지원 하기에 가장 쉬운 경로입니다. 입력 관리자에서 단추와 축을 다시 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76bf7-108">If your apps are already using these APIs for input, this is the easiest path for supporting motion controllers in Windows Mixed Reality: you should just need to remap buttons and axes in the Input Manager.</span></span>

<span data-ttu-id="76bf7-109">자세한 내용은 [unity 단추/축 매핑 표](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) 및 [일반적인 unity api 개요](gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="76bf7-109">For more information, see the [Unity button/axis mapping table](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) and the [overview of the common Unity APIs](gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis).</span></span>

## <a name="windows-specific-xrwsainput-apis"></a><span data-ttu-id="76bf7-110">Windows 관련 XR. WSA. 입력 Api</span><span class="sxs-lookup"><span data-stu-id="76bf7-110">Windows-specific XR.WSA.Input APIs</span></span>

<span data-ttu-id="76bf7-111">앱에서 각 플랫폼에 대 한 사용자 지정 입력 논리를 이미 빌드하는 경우 **XR** 네임 스페이스에서 Windows 관련 공간 입력 api를 사용 하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76bf7-111">If your app already builds custom input logic for each platform, you can choose to use the Windows-specific spatial input APIs under the **UnityEngine.XR.WSA.Input** namespace.</span></span> <span data-ttu-id="76bf7-112">이렇게 하면 위치 정확도 나 원본 종류와 같은 추가 정보에 액세스할 수 있으므로 HoloLens와 컨트롤러를 따로 지시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76bf7-112">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart on HoloLens.</span></span>

<span data-ttu-id="76bf7-113">자세한 내용은 [UnityEngine. XR api 개요](gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="76bf7-113">For more information, see the [overview of the UnityEngine.XR.WSA.Input APIs](gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput).</span></span>

## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="76bf7-114">그립 포즈 및 포인팅 포즈</span><span class="sxs-lookup"><span data-stu-id="76bf7-114">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="76bf7-115">Windows Mixed Reality는 다양 한 폼 팩터에서 동작 컨트롤러를 지원 하며, 각 컨트롤러의 디자인이 사용자의 손 위치와 앱에서 사용 해야 하는 자연 스러운 "전달" 방향 간의 관계에 차이가 있습니다. controller.</span><span class="sxs-lookup"><span data-stu-id="76bf7-115">Windows Mixed Reality supports motion controllers in a variety of form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="76bf7-116">이러한 컨트롤러를 더 잘 나타내기 위해 각 상호 작용 소스에 대해 조사할 수 있는 두 가지 종류의 포즈가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76bf7-116">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source:</span></span>

* <span data-ttu-id="76bf7-117">HoloLens에서 감지 된 손바닥의 위치 또는 이동 컨트롤러를 보유 하는 야자수의 위치를 나타내는 **그립 포즈**입니다.</span><span class="sxs-lookup"><span data-stu-id="76bf7-117">The **grip pose**, representing the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>
    * <span data-ttu-id="76bf7-118">모던 헤드셋에서는이 포즈를 사용 하 여 사용자 **의 손을** 나 **사용자의 손으로 보유 한 개체**(예: 소드 또는 포)를 렌더링 하는 데 가장 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="76bf7-118">On immersive headsets, this pose is best used to render **the user's hand** or **an object held in the user's hand**, such as a sword or gun.</span></span>
    * <span data-ttu-id="76bf7-119">**그립 위치**: 중심 컨트롤러를 자연스럽 게 사용할 때 왼쪽 또는 오른쪽으로 조정 하 여 그립 내에서 위치를 가운데에 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="76bf7-119">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span>
    * <span data-ttu-id="76bf7-120">**그립 방향의 오른쪽 축입니다**. 손을 완전히 열어 평평한 5 손가락 포즈를 형성 하는 경우 야자나무 (왼쪽 야자나무에서 전방, 오른쪽 팜)에 있는 광선</span><span class="sxs-lookup"><span data-stu-id="76bf7-120">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
    * <span data-ttu-id="76bf7-121">**그립 방향의 앞 축**: 컨트롤러를 보유 하 고 있는 것 처럼 부분적으로 닫는 경우 엄지 단추가 아닌 손가락으로 형성 된 튜브를 통해 "전달" 하는 광선이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="76bf7-121">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
    * <span data-ttu-id="76bf7-122">**그립 방향의 위쪽 축입니다**. 오른쪽 및 전방 정의에 의해 암시 된 위쪽 축입니다.</span><span class="sxs-lookup"><span data-stu-id="76bf7-122">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>
    * <span data-ttu-id="76bf7-123">Unity의 교차 공급 업체 입력 API (XR)를 통해 그립 포즈에 액세스할 수 있습니다 **[. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation**) 또는 Windows 특정 API (**sourcestate/Rotation**, 그립 포즈 요청)를 통해</span><span class="sxs-lookup"><span data-stu-id="76bf7-123">You can access the grip pose through either Unity's cross-vendor input API (**[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation**) or through the Windows-specific API (**sourceState.sourcePose.TryGetPosition/Rotation**, requesting the Grip pose).</span></span>
* <span data-ttu-id="76bf7-124">앞에 있는 컨트롤러의 팁을 나타내는 **포인터가 포즈**입니다.</span><span class="sxs-lookup"><span data-stu-id="76bf7-124">The **pointer pose**, representing the tip of the controller pointing forward.</span></span>
    * <span data-ttu-id="76bf7-125">이 포즈는 컨트롤러 모델 자체를 렌더링할 때 **UI를 가리킬** 때 raycast에 가장 잘 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="76bf7-125">This pose is best used to raycast when **pointing at UI** when you are rendering the controller model itself.</span></span>
    * <span data-ttu-id="76bf7-126">현재 포인터 포즈는 Windows 관련 API (**Sourcestate/Rotation**, 포인터 포즈 요청)를 통해서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76bf7-126">Currently, the pointer pose is available only through the Windows-specific API (**sourceState.sourcePose.TryGetPosition/Rotation**, requesting the Pointer pose).</span></span>

<span data-ttu-id="76bf7-127">이러한 포즈 좌표는 모두 Unity 세계 좌표로 표현 됩니다.</span><span class="sxs-lookup"><span data-stu-id="76bf7-127">These pose coordinates are all expressed in Unity world coordinates.</span></span>

## <a name="see-also"></a><span data-ttu-id="76bf7-128">참조</span><span class="sxs-lookup"><span data-stu-id="76bf7-128">See also</span></span>
* [<span data-ttu-id="76bf7-129">모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="76bf7-129">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="76bf7-130">Unity의 제스처 및 모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="76bf7-130">Gestures and motion controllers in Unity</span></span>](gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="76bf7-131">UnityEngine. XR</span><span class="sxs-lookup"><span data-stu-id="76bf7-131">UnityEngine.XR.WSA.Input</span></span>](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [<span data-ttu-id="76bf7-132">UnityEngine. XR 추적</span><span class="sxs-lookup"><span data-stu-id="76bf7-132">UnityEngine.XR.InputTracking</span></span>](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [<span data-ttu-id="76bf7-133">포팅 가이드</span><span class="sxs-lookup"><span data-stu-id="76bf7-133">Porting guides</span></span>](porting-guides.md)
