---
title: 제스처와 Unity의 동작 컨트롤러
description: 두 가지 키에 응시 Unity, 손 제스처 및 동작 컨트롤러에 대해 작업을 수행 합니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 제스처 동작 컨트롤러, unity, 게이즈를 입력
ms.openlocfilehash: d98590f9a6c40336a13cb75e8050e13edfaa2a6c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597655"
---
# <a name="gestures-and-motion-controllers-in-unity"></a><span data-ttu-id="875eb-104">제스처와 Unity의 동작 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="875eb-104">Gestures and motion controllers in Unity</span></span>

<span data-ttu-id="875eb-105">두 가지 주요 작업을 수행할 사용자 [Unity에서 gaze](gaze-in-unity.md), [제스처를 전달](gestures.md) 하 고 [컨트롤러 동작](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="875eb-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](gestures.md) and [motion controllers](motion-controllers.md).</span></span> <span data-ttu-id="875eb-106">Unity에서 동일한 Api를 통해 공간 입력의 두 원본에 대 한 데이터를 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="875eb-107">Windows Mixed Reality를 일반적인에 대 한 공간 입력된 데이터에 액세스 하는 두 가지를 제공 하는 unity *Input.GetButton/Input.GetAxis* 여러 Unity xr 하이 Sdk에서 사용할 수 있는 Api 및 *InteractionManager / GestureRecognizer* 공간을 사용할 수 있는 입력된 데이터의 전체 집합을 노출 하는 Windows Mixed Reality로 특정 API.</span><span class="sxs-lookup"><span data-stu-id="875eb-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality, the common *Input.GetButton/Input.GetAxis* APIs that work across multiple Unity XR SDKs, and an *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality that exposes the full set of spatial input data available.</span></span>

## <a name="unity-buttonaxis-mapping-table"></a><span data-ttu-id="875eb-108">Unity 단추/축 매핑 테이블</span><span class="sxs-lookup"><span data-stu-id="875eb-108">Unity button/axis mapping table</span></span>

<span data-ttu-id="875eb-109">아래 표에 단추 및 축 Id를 통해 Windows Mixed Reality 동작 컨트롤러에 대 한 Unity의 입력 관리자에서 지원 됩니다 합니다 *Input.GetButton/GetAxis* Api에는 "Windows MR 별" 열 속성을 참조 하는 동안 으로 사용할 수는 *InteractionSourceState* 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-109">The button and axis IDs in the table below are supported in Unity's Input Manager for Windows Mixed Reality motion controllers through the *Input.GetButton/GetAxis* APIs, while the "Windows MR-specific" column refers to properties available off of the *InteractionSourceState* type.</span></span> <span data-ttu-id="875eb-110">이러한 각 Api는 아래 섹션에서 자세히 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-110">Each of these APIs are described in detail in the sections below.</span></span>

<span data-ttu-id="875eb-111">Windows Mixed Reality에 대 한 단추/축 ID 매핑을는 일반적으로 Oculus 단추/축 Id와 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-111">The button/axis ID mappings for Windows Mixed Reality generally match the Oculus button/axis IDs.</span></span>

<span data-ttu-id="875eb-112">Windows Mixed Reality에 대 한 단추/축 ID 매핑이 OpenVR의 매핑을 두 가지 방식에서에서 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-112">The button/axis ID mappings for Windows Mixed Reality differ from OpenVR's mappings in two ways:</span></span>
1. <span data-ttu-id="875eb-113">매핑을 스틱 및 터치 패드를 사용 하 여 컨트롤러를 지원 하기 위해 스틱 구별 된 터치 패드 Id를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-113">The mapping uses touchpad IDs that are distinct from thumbstick, to support controllers with both thumbsticks and touchpads.</span></span>
2. <span data-ttu-id="875eb-114">매핑을 A, X 단추를 해당 물리적 ABXY 단추에 사용할 수 있는 메뉴 단추에 대 한 Id를 오버 로드 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-114">The mapping avoids overloading the A and X button IDs for the Menu buttons, to leave those available for physical ABXY buttons.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="875eb-115">입력</span><span class="sxs-lookup"><span data-stu-id="875eb-115">Input</span></span> </th><th colspan="2"><span data-ttu-id="875eb-116"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">일반적인 Unity Api</a></span><span class="sxs-lookup"><span data-stu-id="875eb-116"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Common Unity APIs</a></span></span><br /><span data-ttu-id="875eb-117">(Input.GetButton/GetAxis)</span><span class="sxs-lookup"><span data-stu-id="875eb-117">(Input.GetButton/GetAxis)</span></span> </th><th rowspan="2"><span data-ttu-id="875eb-118"><a href="gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xr.wsa.input">Windows MR-specific Input API</a></span><span class="sxs-lookup"><span data-stu-id="875eb-118"><a href="gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xr.wsa.input">Windows MR-specific Input API</a></span></span><br /><span data-ttu-id="875eb-119">(XR.WSA.Input)</span><span class="sxs-lookup"><span data-stu-id="875eb-119">(XR.WSA.Input)</span></span></th>
</tr><tr>
<th> <span data-ttu-id="875eb-120">왼쪽 위</span><span class="sxs-lookup"><span data-stu-id="875eb-120">Left hand</span></span> </th><th> <span data-ttu-id="875eb-121">오른쪽 위</span><span class="sxs-lookup"><span data-stu-id="875eb-121">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="875eb-122">누른 선택 트리거</span><span class="sxs-lookup"><span data-stu-id="875eb-122">Select trigger pressed</span></span> </td><td> <span data-ttu-id="875eb-123">Axis 9 = 1.0</span><span class="sxs-lookup"><span data-stu-id="875eb-123">Axis 9 = 1.0</span></span> </td><td> <span data-ttu-id="875eb-124">Axis 10 = 1.0</span><span class="sxs-lookup"><span data-stu-id="875eb-124">Axis 10 = 1.0</span></span> </td><td> <span data-ttu-id="875eb-125">selectPressed</span><span class="sxs-lookup"><span data-stu-id="875eb-125">selectPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="875eb-126">트리거 아날로그 값 선택</span><span class="sxs-lookup"><span data-stu-id="875eb-126">Select trigger analog value</span></span> </td><td> <span data-ttu-id="875eb-127">축 9</span><span class="sxs-lookup"><span data-stu-id="875eb-127">Axis 9</span></span> </td><td> <span data-ttu-id="875eb-128">Axis 10</span><span class="sxs-lookup"><span data-stu-id="875eb-128">Axis 10</span></span> </td><td> <span data-ttu-id="875eb-129">selectPressedAmount</span><span class="sxs-lookup"><span data-stu-id="875eb-129">selectPressedAmount</span></span></td>
</tr><tr>
<td> <span data-ttu-id="875eb-130">누른 부분적으로 트리거를 선택</span><span class="sxs-lookup"><span data-stu-id="875eb-130">Select trigger partially pressed</span></span> </td><td> <span data-ttu-id="875eb-131">단추 14 <i>(gamepad 호환성)</i> </span><span class="sxs-lookup"><span data-stu-id="875eb-131">Button 14 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="875eb-132">단추 15 <i>(gamepad 호환성)</i> </span><span class="sxs-lookup"><span data-stu-id="875eb-132">Button 15 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="875eb-133">selectPressedAmount &gt; 0.0</span><span class="sxs-lookup"><span data-stu-id="875eb-133">selectPressedAmount &gt; 0.0</span></span></td>
</tr><tr>
<td> <span data-ttu-id="875eb-134">메뉴 단추 누름</span><span class="sxs-lookup"><span data-stu-id="875eb-134">Menu button pressed</span></span> </td><td> <span data-ttu-id="875eb-135">단추 6 \*</span><span class="sxs-lookup"><span data-stu-id="875eb-135">Button 6\*</span></span> </td><td> <span data-ttu-id="875eb-136">단추 7 \*</span><span class="sxs-lookup"><span data-stu-id="875eb-136">Button 7\*</span></span> </td><td> <span data-ttu-id="875eb-137">menuPressed</span><span class="sxs-lookup"><span data-stu-id="875eb-137">menuPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="875eb-138">그립 단추 누름</span><span class="sxs-lookup"><span data-stu-id="875eb-138">Grip button pressed</span></span> </td><td> <span data-ttu-id="875eb-139">축 11 = 1.0 (아날로그 값 없음)</span><span class="sxs-lookup"><span data-stu-id="875eb-139">Axis 11 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="875eb-140">단추 4 <i>(gamepad 호환성)</i> </span><span class="sxs-lookup"><span data-stu-id="875eb-140">Button 4 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="875eb-141">축 12 = 1.0 (아날로그 값 없음)</span><span class="sxs-lookup"><span data-stu-id="875eb-141">Axis 12 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="875eb-142">단추 5 <i>(gamepad 호환성)</i> </span><span class="sxs-lookup"><span data-stu-id="875eb-142">Button 5 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="875eb-143">잡았습니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-143">grasped</span></span></td>
</tr><tr>
<td> <span data-ttu-id="875eb-144">엄지 스틱 X <i>(왼쪽:-1.0, 오른쪽: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="875eb-144">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="875eb-145">축 1</span><span class="sxs-lookup"><span data-stu-id="875eb-145">Axis 1</span></span> </td><td> <span data-ttu-id="875eb-146">축 4</span><span class="sxs-lookup"><span data-stu-id="875eb-146">Axis 4</span></span> </td><td> <span data-ttu-id="875eb-147">thumbstickPosition.x</span><span class="sxs-lookup"><span data-stu-id="875eb-147">thumbstickPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="875eb-148">엄지 스틱 Y <i>(위쪽:-1.0, 아래: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="875eb-148">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="875eb-149">축 2</span><span class="sxs-lookup"><span data-stu-id="875eb-149">Axis 2</span></span> </td><td> <span data-ttu-id="875eb-150">축 5</span><span class="sxs-lookup"><span data-stu-id="875eb-150">Axis 5</span></span> </td><td> <span data-ttu-id="875eb-151">thumbstickPosition.y</span><span class="sxs-lookup"><span data-stu-id="875eb-151">thumbstickPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="875eb-152">엄지 스틱 누름</span><span class="sxs-lookup"><span data-stu-id="875eb-152">Thumbstick pressed</span></span> </td><td> <span data-ttu-id="875eb-153">단추 8</span><span class="sxs-lookup"><span data-stu-id="875eb-153">Button 8</span></span> </td><td> <span data-ttu-id="875eb-154">단추 9</span><span class="sxs-lookup"><span data-stu-id="875eb-154">Button 9</span></span> </td><td> <span data-ttu-id="875eb-155">thumbstickPressed</span><span class="sxs-lookup"><span data-stu-id="875eb-155">thumbstickPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="875eb-156">터치 패드 X <i>(왼쪽:-1.0, 오른쪽: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="875eb-156">Touchpad X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="875eb-157">축 17 \*</span><span class="sxs-lookup"><span data-stu-id="875eb-157">Axis 17\*</span></span> </td><td> <span data-ttu-id="875eb-158">Axis 19\*</span><span class="sxs-lookup"><span data-stu-id="875eb-158">Axis 19\*</span></span> </td><td> <span data-ttu-id="875eb-159">touchpadPosition.x</span><span class="sxs-lookup"><span data-stu-id="875eb-159">touchpadPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="875eb-160">터치 패드 Y <i>(위쪽:-1.0, 아래: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="875eb-160">Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="875eb-161">축 18 \*</span><span class="sxs-lookup"><span data-stu-id="875eb-161">Axis 18\*</span></span> </td><td> <span data-ttu-id="875eb-162">축 20 \*</span><span class="sxs-lookup"><span data-stu-id="875eb-162">Axis 20\*</span></span> </td><td> <span data-ttu-id="875eb-163">touchpadPosition.y</span><span class="sxs-lookup"><span data-stu-id="875eb-163">touchpadPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="875eb-164">작업 패드</span><span class="sxs-lookup"><span data-stu-id="875eb-164">Touchpad touched</span></span> </td><td> <span data-ttu-id="875eb-165">단추 18 \*</span><span class="sxs-lookup"><span data-stu-id="875eb-165">Button 18\*</span></span> </td><td> <span data-ttu-id="875eb-166">단추 19 \*</span><span class="sxs-lookup"><span data-stu-id="875eb-166">Button 19\*</span></span> </td><td> <span data-ttu-id="875eb-167">touchpadTouched</span><span class="sxs-lookup"><span data-stu-id="875eb-167">touchpadTouched</span></span></td>
</tr><tr>
<td> <span data-ttu-id="875eb-168">터치 패드 누름</span><span class="sxs-lookup"><span data-stu-id="875eb-168">Touchpad pressed</span></span> </td><td> <span data-ttu-id="875eb-169">단추 16 \*</span><span class="sxs-lookup"><span data-stu-id="875eb-169">Button 16\*</span></span> </td><td> <span data-ttu-id="875eb-170">단추 17 \*</span><span class="sxs-lookup"><span data-stu-id="875eb-170">Button 17\*</span></span> </td><td> <span data-ttu-id="875eb-171">touchpadPressed</span><span class="sxs-lookup"><span data-stu-id="875eb-171">touchpadPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="875eb-172">6DoF 그립 포즈 또는 포인터 자세</span><span class="sxs-lookup"><span data-stu-id="875eb-172">6DoF grip pose or pointer pose</span></span> </td><td colspan="2"> <span data-ttu-id="875eb-173"><i>그립</i> 만 초래 합니다. <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span><span class="sxs-lookup"><span data-stu-id="875eb-173"><i>Grip</i> pose only: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span></span><br /><span data-ttu-id="875eb-174"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span><span class="sxs-lookup"><span data-stu-id="875eb-174"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span></span></td><td> <span data-ttu-id="875eb-175">전달 <i>그립</i> 하거나 <i>포인터</i> 인수로: sourceState.sourcePose.TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="875eb-175">Pass <i>Grip</i> or <i>Pointer</i> as an argument: sourceState.sourcePose.TryGetPosition</span></span><br /><span data-ttu-id="875eb-176">sourceState.sourcePose.TryGetRotation</span><span class="sxs-lookup"><span data-stu-id="875eb-176">sourceState.sourcePose.TryGetRotation</span></span><br /></td>
</tr><tr>
<td> <span data-ttu-id="875eb-177">상태를 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-177">Tracking state</span></span> </td><td colspan="2"> <span data-ttu-id="875eb-178"><i>위치 정확성과 소스 손실 위험 MR 관련 API를 통해 에서만 사용할 수 있습니다</i> </span><span class="sxs-lookup"><span data-stu-id="875eb-178"><i>Position accuracy and source loss risk only available through MR-specific API</i> </span></span></td><td> <span data-ttu-id="875eb-179"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span><span class="sxs-lookup"><span data-stu-id="875eb-179"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span></span><br /><span data-ttu-id="875eb-180"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span><span class="sxs-lookup"><span data-stu-id="875eb-180"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="875eb-181">이러한 단추/축 Id 매핑에 Oculus 터치 및 OpenVR 게임 패드에서 사용 하는 충돌로 인해 OpenVR에 대 한 Unity를 사용 하는 Id에서 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-181">These button/axis IDs differ from the IDs that Unity uses for OpenVR due to collisions in the mappings used by gamepads, Oculus Touch and OpenVR.</span></span>

## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="875eb-182">그립 포즈 포인팅 포즈 비교</span><span class="sxs-lookup"><span data-stu-id="875eb-182">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="875eb-183">Windows Mixed Reality 다양 한 폼 팩터 동작 컨트롤러에서는, 각 컨트롤러의 디자인을 사용 하 여 렌더링할 때 가리키는 사용 해야 다른 사용자의 직접 위치 사이의 "전달" 방향 해당 앱의 자연 관계를 컨트롤러입니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-183">Windows Mixed Reality supports motion controllers in a variety of form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="875eb-184">이러한 컨트롤러를 더 잘 나타내기 위해 두 가지 종류의 포즈 각 상호 작용 원본에 대해 조사할 수 있습니다는 **그립 자세** 하며 **포인터 자세**합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-184">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source, the **grip pose** and the **pointer pose**.</span></span> <span data-ttu-id="875eb-185">그립 자세 및 포인터 포즈 좌표 두 전역 Unity 영역 좌표에서 모든 Unity Api가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-185">Both the grip pose and pointer pose coordinates are expressed by all Unity APIs in global Unity world coordinates.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="875eb-186">그립 자세</span><span class="sxs-lookup"><span data-stu-id="875eb-186">Grip pose</span></span>

<span data-ttu-id="875eb-187">합니다 **그립 포즈** 는 HoloLens 감지한 손 모양 손바닥 또는 동작 컨트롤러 보유 palm의 위치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-187">The **grip pose** represents the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>

<span data-ttu-id="875eb-188">몰입 형 헤드셋 그립 포즈 가장 사용 렌더링 **사용자의 직접** 또는 **사용자의 직접에 보관 된 개체**검 또는 총 등입니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-188">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand**, such as a sword or gun.</span></span> <span data-ttu-id="875eb-189">그립 자세는으로 동작 컨트롤러를 시각화 하는 경우에 사용 됩니다 합니다 **렌더링 가능한 모델** 제공 동작에 대 한 Windows에서 컨트롤러는 원본 및 회전 중심으로 그립 포즈를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-189">The grip pose is also used when visualizing a motion controller, as the **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="875eb-190">그립 자세는 특히 다음과 같이 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-190">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="875eb-191">합니다 **위치를 잡고**: 물론 컨트롤러를 보유 하는 경우 팜 중심 왼쪽 또는 오른쪽 가운데 그립 내의 위치를 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-191">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="875eb-192">Windows Mixed Reality 동작 컨트롤러에서이 위치는 일반적으로 감각을 단추를 사용 하 여 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-192">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="875eb-193">합니다 **방향을 올바른 축 잡고**: 완전히 플랫 5 손가락 자세를 직접 열면 광선과 표준 프로그램 palm에서 (왼쪽된 palm, palm 오른쪽에서 이전 버전과에서 앞으로)</span><span class="sxs-lookup"><span data-stu-id="875eb-193">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="875eb-194">합니다 **방향을 정방향 축 잡고**: 부분적으로 (처럼 컨트롤러 보유) 직접을 닫을 때, 광선을 가리키는 "forward" 튜브를 통해 비 엄지 손가락으로 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-194">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="875eb-195">합니다 **축 위쪽 방향 잡고**: 오른쪽 정방향 정의 사용 권한에 포함 된 최대 축.</span><span class="sxs-lookup"><span data-stu-id="875eb-195">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>

<span data-ttu-id="875eb-196">그립 자세 하거나 Unity의 공급 업체 간 입력 API 통해 액세스할 수 있습니다 (*[xr 하이 있습니다. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)합니다. GetLocalPosition/Rotation*) 또는 Windows MR 관련 API를 통해 (*sourceState.sourcePose.TryGetPosition/Rotation*, 요청에 대 한 데이터를 초래 합니다 **그립** 노드).</span><span class="sxs-lookup"><span data-stu-id="875eb-196">You can access the grip pose through either Unity's cross-vendor input API (*[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation*) or through the Windows MR-specific API (*sourceState.sourcePose.TryGetPosition/Rotation*, requesting pose data for the **Grip** node).</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="875eb-197">포인터 자세</span><span class="sxs-lookup"><span data-stu-id="875eb-197">Pointer pose</span></span>

<span data-ttu-id="875eb-198">합니다 **포인터 포즈** 앞으로 가리키는 컨트롤러의 끝을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-198">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="875eb-199">시스템 제공 포인터 자세는 raycast 했으면 **컨트롤러 모델 자체 렌더링**합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-199">The system-provided pointer pose is best used to raycast when you are **rendering the controller model itself**.</span></span> <span data-ttu-id="875eb-200">일부 가상 건, 같은 컨트롤러 대신 다른 가상 개체를 렌더링 하는 경우 총 앱 정의 모델의 barrel 함께 전송 되는 ray 같은 가상 개체에 대 한 가장 자연 스러운 광선을 사용 하 여 가리켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-200">If you are rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that is most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="875eb-201">사용자가 가상 개체와 실제 컨트롤러 하지에서 볼 수 있으므로 가상 개체를 사용 하 여 가리키는 가능성이 됩니다 앱을 사용 하는 더 자연 스러운.</span><span class="sxs-lookup"><span data-stu-id="875eb-201">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

<span data-ttu-id="875eb-202">현재 포인터 자세는 Unity는 Windows MR 관련 API 통해서만 사용할 수 있습니다 *sourceState.sourcePose.TryGetPosition/Rotation*전달 *InteractionSourceNode.Pointer* 으로 인수입니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-202">Currently, the pointer pose is available in Unity only through the Windows MR-specific API, *sourceState.sourcePose.TryGetPosition/Rotation*, passing in *InteractionSourceNode.Pointer* as the argument.</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="875eb-203">컨트롤러 상태를 추적</span><span class="sxs-lookup"><span data-stu-id="875eb-203">Controller tracking state</span></span>

<span data-ttu-id="875eb-204">헤드셋와 같은 Windows Mixed Reality 동작 컨트롤러 설정이 필요 하지 않습니다 외부 추적 센서입니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-204">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="875eb-205">대신, 컨트롤러 자체 헤드셋의 센서에서 추적 됩니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-205">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="875eb-206">사용자가 헤드셋의 필드의 보기 컨트롤러를 이동 하면 대부분의 경우에서 Windows 계속 컨트롤러 위치를 유추 하 고 앱을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-206">If the user moves the controllers out of the headset's field of view, in most cases Windows will continue to infer controller positions and provide them to the app.</span></span> <span data-ttu-id="875eb-207">경우 컨트롤러 근사치 정확도 위치로 컨트롤러의 위치는 삭제 하는 충분 한 시간에 대 한 추적 visual 끊어졌습니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-207">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="875eb-208">이 시점에서 시스템 얼굴이 움직일, 여전히 해당 내부 방향 센서를 사용 하 여 컨트롤러의 true 방향을 노출 하는 동안 사용자의 위치를 추적 하는 사용자에 게 컨트롤러 본문 잠금을 됩니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-208">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="875eb-209">컨트롤러를 사용 하 고 UI 요소를 활성화 하는 많은 앱은 사용자 알아채지 않으면 서의 대략적인 정확도 정상적으로 작동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-209">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<span data-ttu-id="875eb-210">이 대해 가장 좋은 방법은 직접 시도해 볼 경우</span><span class="sxs-lookup"><span data-stu-id="875eb-210">The best way to get a feel for this is to try it yourself.</span></span> <span data-ttu-id="875eb-211">컨트롤러 동작을 사용 하 여 추적의 다양 한 상태에서 작동 하는 몰입 감이 뛰어난 콘텐츠 예제를 사용 하 여이 비디오를 확인해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="875eb-211">Check out this video with examples of immersive content that works with motion controllers across various tracking states:</span></span>

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="875eb-212">상태를 명시적으로 추적 하는 방법에 대 한 추론</span><span class="sxs-lookup"><span data-stu-id="875eb-212">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="875eb-213">위치 추적 상태에 따라 다르게 처리 하려는 앱 수 더 나아가 같은 컨트롤러의 상태에 대 한 속성을 검사할 *SourceLossRisk* 하 고 *PositionAccuracy*:</span><span class="sxs-lookup"><span data-stu-id="875eb-213">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as *SourceLossRisk* and *PositionAccuracy*:</span></span>

<table>
<tr>
<th> <span data-ttu-id="875eb-214">상태를 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-214">Tracking state</span></span> </th><th> <span data-ttu-id="875eb-215">SourceLossRisk</span><span class="sxs-lookup"><span data-stu-id="875eb-215">SourceLossRisk</span></span> </th><th> <span data-ttu-id="875eb-216">PositionAccuracy</span><span class="sxs-lookup"><span data-stu-id="875eb-216">PositionAccuracy</span></span> </th><th> <span data-ttu-id="875eb-217">TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="875eb-217">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="875eb-218"><b>높은 정확도</b> </span><span class="sxs-lookup"><span data-stu-id="875eb-218"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="875eb-219">&lt; 1.0</span><span class="sxs-lookup"><span data-stu-id="875eb-219">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="875eb-220">높음</span><span class="sxs-lookup"><span data-stu-id="875eb-220">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="875eb-221">true</span><span class="sxs-lookup"><span data-stu-id="875eb-221">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="875eb-222"><b>높은 정확도 (손실의 위험이)</b> </span><span class="sxs-lookup"><span data-stu-id="875eb-222"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="875eb-223">== 1.0</span><span class="sxs-lookup"><span data-stu-id="875eb-223">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="875eb-224">높음</span><span class="sxs-lookup"><span data-stu-id="875eb-224">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="875eb-225">true</span><span class="sxs-lookup"><span data-stu-id="875eb-225">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="875eb-226"><b>대략적인 정확도</b> </span><span class="sxs-lookup"><span data-stu-id="875eb-226"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="875eb-227">== 1.0</span><span class="sxs-lookup"><span data-stu-id="875eb-227">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="875eb-228">대략 일치</span><span class="sxs-lookup"><span data-stu-id="875eb-228">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="875eb-229">true</span><span class="sxs-lookup"><span data-stu-id="875eb-229">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="875eb-230"><b>위치가 없습니다</b> </span><span class="sxs-lookup"><span data-stu-id="875eb-230"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="875eb-231">== 1.0</span><span class="sxs-lookup"><span data-stu-id="875eb-231">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="875eb-232">대략 일치</span><span class="sxs-lookup"><span data-stu-id="875eb-232">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="875eb-233">false</span><span class="sxs-lookup"><span data-stu-id="875eb-233">false</span></span></td>
</tr>
</table>

<span data-ttu-id="875eb-234">이러한 동작 컨트롤러 추적 상태는 다음과 같이 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-234">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="875eb-235">**높은 정확도 경우:** 동작 컨트롤러 헤드셋의 뷰 필드 내에 있는 동안 정확도 높은 위치, visual 추적에 따라 일반적으로 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-235">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="875eb-236">참고는 컨트롤러를 이동 하는 일시적으로 보기의 필드를 벗어나거나 헤드셋 센서에서 일시적으로 가려지는지 (예: 사용자의 반면) 기반 컨트롤러의 관성 추적으로 짧은 시간에 대 한 정확도 높은 포즈 반환할 계속 자체입니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-236">Note that a moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (e.g. by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="875eb-237">**높은 정확도 (손실의 위험이):** 사용자 헤드셋의 뷰 필드의 가장자리를 넘어 동작 컨트롤러를 움직이면 헤드셋 곧 없게 됩니다 컨트롤러의 위치를 시각적으로 추적할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-237">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="875eb-238">앱 경우 컨트롤러에 도달이 FOV 경계 확인 하 여 알고 합니다 **SourceLossRisk** 1.0에 도달 합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-238">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="875eb-239">이 시점에서 앱 꾸준하게 매우 고품질 발생 해야 하는 컨트롤러 제스처를 일시 중지 하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-239">At that point, the app may choose to pause controller gestures that require a steady stream of very high-quality poses.</span></span>
* <span data-ttu-id="875eb-240">**대략적인 정확도:** 경우 컨트롤러 근사치 정확도 위치로 컨트롤러의 위치는 삭제 하는 충분 한 시간에 대 한 추적 visual 끊어졌습니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-240">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="875eb-241">이 시점에서 시스템 얼굴이 움직일, 여전히 해당 내부 방향 센서를 사용 하 여 컨트롤러의 true 방향을 노출 하는 동안 사용자의 위치를 추적 하는 사용자에 게 컨트롤러 본문 잠금을 됩니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-241">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="875eb-242">컨트롤러를 사용 하 고 UI 요소를 활성화 하는 많은 앱 사용자 알아채지 않으면 서 일반 while로 대략적인 정확도 작동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-242">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="875eb-243">라우터로도 충분 입력된 요구 사항이 있는 앱에서이 삭제 감지 하도록 선택할 수 있습니다 **높은** 정확도 **근사치** 검사 하 여 정확도 **PositionAccuracy** 속성에 대 한 사용자에 게 더 넓은 hitbox 오프 스크린 대상에서이 시간 동안 예입니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-243">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="875eb-244">**위치가 없습니다.** 컨트롤러는 오랜 시간 동안 대략적인 정확도에서 작동할 수 있습니다, 있지만 때로는 시스템 임을 알고 있습니다 본문 잠긴 위치도 하지 의미 있는 지금은.</span><span class="sxs-lookup"><span data-stu-id="875eb-244">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position is not meaningful at the moment.</span></span> <span data-ttu-id="875eb-245">예를 들어 방금 설정 하는 컨트롤러 수 하지 관찰 한 시각적으로 또는 사용자가 다음 다른 사용자가 선택 하는 컨트롤러 작성 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-245">For example, a controller that was just turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="875eb-246">시스템에서 해당 시간에 앱에 그 위치를 제공 하지 것입니다 하 고 *TryGetPosition* false를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-246">At those times, the system will not provide any position to the app, and *TryGetPosition* will return false.</span></span>

## <a name="common-unity-apis-inputgetbuttongetaxis"></a><span data-ttu-id="875eb-247">일반적인 Unity Api (Input.GetButton/GetAxis)</span><span class="sxs-lookup"><span data-stu-id="875eb-247">Common Unity APIs (Input.GetButton/GetAxis)</span></span>

<span data-ttu-id="875eb-248">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="875eb-248">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span></span><br>
<span data-ttu-id="875eb-249">**형식**: *Input*, *XR.InputTracking*</span><span class="sxs-lookup"><span data-stu-id="875eb-249">**Types**: *Input*, *XR.InputTracking*</span></span>

<span data-ttu-id="875eb-250">현재 사용 하 여 일반적인 unity *Input.GetButton/Input.GetAxis* 에 대 한 입력을 노출 하는 Api [Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html)를 [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) 및 Windows Mixed Reality 포함 실습 및 동작 컨트롤러입니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-250">Unity currently uses its general *Input.GetButton/Input.GetAxis* APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) and Windows Mixed Reality, including hands and motion controllers.</span></span> <span data-ttu-id="875eb-251">입력에 대 한 이러한 Api를 사용 하는 앱을 하는 경우 Windows Mixed Reality를 비롯 한 여러 xr 하이 Sdk에서 동작 컨트롤러 쉽게 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-251">If your app uses these APIs for input, it can easily support motion controllers across multiple XR SDKs, including Windows Mixed Reality.</span></span>

### <a name="getting-a-logical-buttons-pressed-state"></a><span data-ttu-id="875eb-252">논리 단추의 누름된 상태 가져오기</span><span class="sxs-lookup"><span data-stu-id="875eb-252">Getting a logical button's pressed state</span></span>

<span data-ttu-id="875eb-253">일반 Unity 입력 Api를 사용 하려면 일반적으로 먼저 단추 및 축의 논리적 이름으로 마무리 합니다 [Unity 입력 관리자](https://docs.unity3d.com/Manual/ConventionalGameInput.html), 각 이름에는 단추 또는 축 Id 바인딩.</span><span class="sxs-lookup"><span data-stu-id="875eb-253">To use the general Unity input APIs, you'll typically start by wiring up buttons and axes to logical names in the [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), binding a button or axis IDs to each name.</span></span> <span data-ttu-id="875eb-254">그런 다음 해당 논리 단추/축 이름을 참조 하는 코드를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-254">You can then write code that refers to that logical button/axis name.</span></span>

<span data-ttu-id="875eb-255">예를 들어 왼쪽된 동작 컨트롤러의 트리거 단추 전송 작업에 매핑할로 이동 **편집 > 프로젝트 설정 > 입력** Unity 내에서 축 제출 섹션의 속성을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-255">For example, to map the left motion controller's trigger button to the Submit action, go to **Edit > Project Settings > Input** within Unity, and expand the properties of the Submit section under Axes.</span></span> <span data-ttu-id="875eb-256">변경 된 **양의 단추** 또는 **Alt 양의 단추** 읽을 속성 **조이스틱 단추 14**, 다음과 같은:</span><span class="sxs-lookup"><span data-stu-id="875eb-256">Change the **Postive Button** or **Alt Positive Button** property to read **joystick button 14**, like this:</span></span>

<span data-ttu-id="875eb-257">![Unity's InputManager](images/unity-input-manager.png)</span><span class="sxs-lookup"><span data-stu-id="875eb-257">![Unity's InputManager](images/unity-input-manager.png)</span></span><br>
<span data-ttu-id="875eb-258">*Unity InputManager*</span><span class="sxs-lookup"><span data-stu-id="875eb-258">*Unity InputManager*</span></span>

<span data-ttu-id="875eb-259">스크립트에 다음 사용 하 여 전송 작업에 대 한 확인해 *Input.GetButton*:</span><span class="sxs-lookup"><span data-stu-id="875eb-259">Your script can then check for the Submit action using *Input.GetButton*:</span></span>

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
<span data-ttu-id="875eb-260">변경 하 여 더 많은 논리 단추를 추가할 수 있습니다 합니다 **크기** 아래에서 속성 **축**합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-260">You can add more logical buttons by changing the **Size** property under **Axes**.</span></span>

### <a name="getting-a-physical-buttons-pressed-state-directly"></a><span data-ttu-id="875eb-261">직접 물리적 단추 누름된 상태 가져오기</span><span class="sxs-lookup"><span data-stu-id="875eb-261">Getting a physical button's pressed state directly</span></span>

<span data-ttu-id="875eb-262">해당 정규화 하 여 단추를 수동으로 액세스할 수도 있습니다 사용 하 여 이름을 *Input.GetKey*:</span><span class="sxs-lookup"><span data-stu-id="875eb-262">You can also access buttons manually by their fully-qualified name, using *Input.GetKey*:</span></span>

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a><span data-ttu-id="875eb-263">손 모양 받거나 동작 컨트롤러 자세</span><span class="sxs-lookup"><span data-stu-id="875eb-263">Getting a hand or motion controller's pose</span></span>

<span data-ttu-id="875eb-264">위치 및 컨트롤러의 회전을 액세스할 수 있습니다 사용 하 여 *xr 하이 있습니다. InputTracking*:</span><span class="sxs-lookup"><span data-stu-id="875eb-264">You can access the position and rotation of the controller, using *XR.InputTracking*:</span></span>

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

<span data-ttu-id="875eb-265">참고가 컨트롤러의 그립 포즈 (사용자 보유 컨트롤러)에 검 또는 총 사용자의 직접 또는 컨트롤러 자체의 모델을 렌더링 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-265">Note that this represents the controller's grip pose (where the user holds the controller), which is useful for rendering a sword or gun in the user's hand, or a model of the controller itself.</span></span>

<span data-ttu-id="875eb-266">컨트롤러에서이 그립 포즈 포인터 포즈 (컨트롤러의 팁을 가리키는 위치)와 관계 다는 참고 합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-266">Note that the relationship between this grip pose and the pointer pose (where the tip of the controller is pointing) may differ across controllers.</span></span> <span data-ttu-id="875eb-267">이 시점에서 컨트롤러의 포인터 포즈 액세스 가능성이 MR 관련 입력 아래 섹션에 설명 된 API 통해 있습니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-267">At this moment, accessing the controller's pointer pose is only possible through the MR-specific input API, described in the sections below.</span></span>

## <a name="windows-specific-apis-xrwsainput"></a><span data-ttu-id="875eb-268">Windows 관련 Api (xr 하이 있습니다. WSA입니다. 입력)</span><span class="sxs-lookup"><span data-stu-id="875eb-268">Windows-specific APIs (XR.WSA.Input)</span></span>

<span data-ttu-id="875eb-269">**Namespace:** *UnityEngine.XR.WSA.Input*</span><span class="sxs-lookup"><span data-stu-id="875eb-269">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="875eb-270">**형식**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span><span class="sxs-lookup"><span data-stu-id="875eb-270">**Types**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span></span>

<span data-ttu-id="875eb-271">(HoloLens)에 대 한 Windows Mixed Reality 직접 입력 하 고 동작 컨트롤러에 대 한 자세한 정보를 가져오려면 아래 Windows 관련 공간 입력된 Api를 사용 하도록 선택할 수 있습니다 합니다 *UnityEngine.XR.WSA.Input* 네임 스페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-271">To get at more detailed information about Windows Mixed Reality hand input (for HoloLens) and motion controllers, you can choose to use the Windows-specific spatial input APIs under the *UnityEngine.XR.WSA.Input* namespace.</span></span> <span data-ttu-id="875eb-272">이 기능을 사용 하면 위치 정확도 같은 추가 정보 또는 실습 및 컨트롤러 간격을 알 수 있도록 원본 유형, 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-272">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart.</span></span>

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a><span data-ttu-id="875eb-273">실습 및 동작 컨트롤러의 상태에 대 한 폴링</span><span class="sxs-lookup"><span data-stu-id="875eb-273">Polling for the state of hands and motion controllers</span></span>

<span data-ttu-id="875eb-274">이 프레임 상태 사용 하 여 각 상호 작용 (직접 또는 동영상 컨트롤러) 원본에 대해 폴링하면 합니다 *GetCurrentReading* 메서드.</span><span class="sxs-lookup"><span data-stu-id="875eb-274">You can poll for this frame's state for each interaction source (hand or motion controller) using the *GetCurrentReading* method.</span></span>

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

<span data-ttu-id="875eb-275">각 *InteractionSourceState* 얻게 백 현재 시점에서 상호 작용 원본을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-275">Each *InteractionSourceState* you get back represents an interaction source at the current moment in time.</span></span> <span data-ttu-id="875eb-276">합니다 *InteractionSourceState* 와 같은 정보를 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-276">The *InteractionSourceState* exposes info such as:</span></span>
* <span data-ttu-id="875eb-277">[누름 유형의](motion-controllers.md) (선택/메뉴/한결/터치 패드/엄지 스틱) 발생 하는</span><span class="sxs-lookup"><span data-stu-id="875eb-277">Which [kinds of presses](motion-controllers.md) are occurring (Select/Menu/Grasp/Touchpad/Thumbstick)</span></span>

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* <span data-ttu-id="875eb-278">다른 데이터 컨트롤러 동작, 이러한는 터치 패드 및/또는 엄지 스틱의 XY 좌표 및 관련 작업된 상태</span><span class="sxs-lookup"><span data-stu-id="875eb-278">Other data specific to motion controllers, such the touchpad and/or thumbstick's XY coordinates and touched state</span></span>

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```
   
* <span data-ttu-id="875eb-279">원본 손 모양 또는 동작 컨트롤러 인지 알아야 InteractionSourceKind</span><span class="sxs-lookup"><span data-stu-id="875eb-279">The InteractionSourceKind to know if the source is a hand or a motion controller</span></span>

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a><span data-ttu-id="875eb-280">정방향 예측 렌더링 동작에 대 한 폴링</span><span class="sxs-lookup"><span data-stu-id="875eb-280">Polling for forward-predicted rendering poses</span></span>

* <span data-ttu-id="875eb-281">실습 및 컨트롤러의 상호 작용 원본 데이터에 대 한 폴링 얻게 발생 시점은이 프레임 photons 사용자의 눈에 도달 하면에 대 한 정방향 예측 발생 됩니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-281">When polling for interaction source data from hands and controllers, the poses you get are forward-predicted poses for the moment in time when this frame's photons will reach the user's eyes.</span></span>  <span data-ttu-id="875eb-282">이러한 정방향 예측 발생에 가장 적합 **렌더링** 컨트롤러 또는 보유 한 각 프레임 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-282">These forward-predicted poses are best used for **rendering** the controller or a held object each frame.</span></span>  <span data-ttu-id="875eb-283">지정 된 키를 눌러 대상으로 하거나 컨트롤러를 사용 하 여 릴리스 하는 경우 기록 이벤트 아래에서 설명 하는 Api를 사용 하는 경우 가장 정확 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-283">If you are targeting a given press or release with the controller, that will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* <span data-ttu-id="875eb-284">또한 현재이 프레임에 대 한 정방향 예측 머리 포즈를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-284">You can also get the forward-predicted head pose for this current frame.</span></span>  <span data-ttu-id="875eb-285">그대로 원본 자세를 사용 하 여이 대 한 유용한 **렌더링** 커서에 지정 된 키를 눌러 또는 릴리스 기록 이벤트 아래에서 설명 하는 Api를 사용 하는 경우 가장 정확 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-285">As with the source pose, this is useful for **rendering** a cursor, although targeting a given press or release will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a><span data-ttu-id="875eb-286">원본 이벤트를 상호 작용 하는 처리</span><span class="sxs-lookup"><span data-stu-id="875eb-286">Handling interaction source events</span></span>

<span data-ttu-id="875eb-287">입력된 이벤트를 정확 하 게 기록 포즈 데이터를 사용 하 여 즉시 처리를 폴링하는 대신 소스 이벤트를 상호 작용을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-287">To handle input events as they happen with their accurate historical pose data, you can handle interaction source events instead of polling.</span></span>

<span data-ttu-id="875eb-288">이벤트를 처리 하려면 상호 작용 원본:</span><span class="sxs-lookup"><span data-stu-id="875eb-288">To handle interaction source events:</span></span>
* <span data-ttu-id="875eb-289">등록 된 *InteractionManager* 입력된 이벤트입니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-289">Register for a *InteractionManager* input event.</span></span> <span data-ttu-id="875eb-290">관심 있는 상호 작용 이벤트의 각 형식에 대해 구독 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-290">For each type of interaction event that you are interested in, you need to subscribe to it.</span></span>

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```
   
* <span data-ttu-id="875eb-291">이벤트를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-291">Handle the event.</span></span> <span data-ttu-id="875eb-292">상호 작용 이벤트에 가입한 후에 해당 하는 경우 콜백을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-292">Once you have subscribed to an interaction event, you will get the callback when appropriate.</span></span> <span data-ttu-id="875eb-293">에 *SourcePressed* 예제에서는 이러한 될 수 있으며 원본 감지 된 후 해제 되거나 손실 되기 전에 합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-293">In the *SourcePressed* example, this will be after the source was detected and before it is released or lost.</span></span>

   ```cs
   void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
       var interactionSourceState = args.state;
       
       // args.state has information about:
          // targeting head ray at the time when the event was triggered
          // whether the source is pressed or not
          // properties like position, velocity, source loss risk
          // source id (which hand id for example) and source kind like hand, voice, controller or other
   }
   ```

### <a name="how-to-stop-handling-an-event"></a><span data-ttu-id="875eb-294">이벤트 처리를 중지 하는 방법</span><span class="sxs-lookup"><span data-stu-id="875eb-294">How to stop handling an event</span></span>

<span data-ttu-id="875eb-295">더 이상에 관심이 이벤트 또는 이벤트에 등록 된 개체를 제거 하는 경우의 이벤트 처리를 중지 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-295">You need to stop handling an event when you are no longer interested in the event or you are destroying the object that has subscribed to the event.</span></span> <span data-ttu-id="875eb-296">이벤트 처리를 중지 하려면 이벤트에서 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-296">To stop handling the event, you unsubscribe from the event.</span></span>

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a><span data-ttu-id="875eb-297">원본 이벤트를 상호 작용의 목록</span><span class="sxs-lookup"><span data-stu-id="875eb-297">List of interaction source events</span></span>

<span data-ttu-id="875eb-298">사용 가능한 상호 작용 원본 이벤트 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-298">The available interaction source events are:</span></span>
* <span data-ttu-id="875eb-299">*InteractionSourceDetected* (원본 활성화)</span><span class="sxs-lookup"><span data-stu-id="875eb-299">*InteractionSourceDetected* (source becomes active)</span></span>
* <span data-ttu-id="875eb-300">*InteractionSourceLost* (비활성 됨)</span><span class="sxs-lookup"><span data-stu-id="875eb-300">*InteractionSourceLost* (becomes inactive)</span></span>
* <span data-ttu-id="875eb-301">*InteractionSourcePressed* (탭, 단추 누름 또는 "Select" 마냥 마음이 들 뜹니다)</span><span class="sxs-lookup"><span data-stu-id="875eb-301">*InteractionSourcePressed* (tap, button press, or "Select" uttered)</span></span>
* <span data-ttu-id="875eb-302">*InteractionSourceReleased* (탭, 단추를 놓았음을, 또는 "Select" 마냥 마음이 들 뜹니다 끝의 끝)</span><span class="sxs-lookup"><span data-stu-id="875eb-302">*InteractionSourceReleased* (end of a tap, button released, or end of "Select" uttered)</span></span>
* <span data-ttu-id="875eb-303">*InteractionSourceUpdated* (이동 또는 그렇지 않은 경우 일부 상태 변경)</span><span class="sxs-lookup"><span data-stu-id="875eb-303">*InteractionSourceUpdated* (moves or otherwise changes some state)</span></span>

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a><span data-ttu-id="875eb-304">키를 눌러 또는 릴리스 가장 정확 하 게 일치 하는 기록 대상 발생에 대 한 이벤트</span><span class="sxs-lookup"><span data-stu-id="875eb-304">Events for historical targeting poses that most accurately match a press or release</span></span>

<span data-ttu-id="875eb-305">앞에서 설명한 폴링 Api 앱 포즈 정방향 예측을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-305">The polling APIs described earlier give your app forward-predicted poses.</span></span>  <span data-ttu-id="875eb-306">이러한 예측된 포즈 컨트롤러나 가상 핸드헬드 개체 렌더링에 가장 적합 한 중일에 향후 발생은 두 가지 주요 이유를 대상으로 적합 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-306">While those predicted poses are best for rendering the controller or a virtual handheld object, future poses are not optimal for targeting, for two key reasons:</span></span>
* <span data-ttu-id="875eb-307">컨트롤러에서 단추를 누를 때 있을 수 있습니다 무선 대기 시간이 약 20ms Bluetooth를 통한 시스템 눌러를 받기 전에 합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-307">When the user presses a button on a controller, there can be about 20ms of wireless latency over Bluetooth before the system receives the press.</span></span>
* <span data-ttu-id="875eb-308">다음 사용 중인 경우 정방향 예측 포즈를 가지는 정방향 예측의 다른 10 20ms 적용할 현재 프레임의 photons 사용자의 눈에 도달 하면 시간을 대상으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-308">Then, if you are using a forward-predicted pose, there would be another 10-20ms of forward prediction applied to target the time when the current frame's photons will reach the user's eyes.</span></span>

<span data-ttu-id="875eb-309">즉, 폴링 하면 원본 자세 하거나 헤드 즉 30 40ms 정방향 여기서 사용자의 헤드 및 실습 실제로 된 키를 눌러 또는 릴리스 발생 했을 때 다시에서 발생할 합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-309">This means that polling gives you a source pose or head pose that is 30-40ms forward from where the user's head and hands actually were back when the press or release happened.</span></span>  <span data-ttu-id="875eb-310">HoloLens 직접 입력에 대 한 지연 시간 없이 무선 전송 중일 있습니다 눌러 검색할 유사한 처리 지연이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-310">For HoloLens hand input, while there's no wireless transmission delay, there is a similar processing delay to detect the press.</span></span>

<span data-ttu-id="875eb-311">직접 또는 컨트롤러 press에서 사용자의 원래 의도에 따라 대상을 정확 하 게 사용 해야는 머리 포즈를 기록 원본 포즈 *InteractionSourcePressed* 또는 *InteractionSourceReleased* 입력된 이벤트입니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-311">To accurately target based on the user's original intent for a hand or controller press, you should use the historical source pose or head pose from that *InteractionSourcePressed* or *InteractionSourceReleased* input event.</span></span>

<span data-ttu-id="875eb-312">눌러 대상 또는 사용자의 헤드 또는 해당 컨트롤러의 기록 포즈 데이터로 릴리스 수 있습니다.:</span><span class="sxs-lookup"><span data-stu-id="875eb-312">You can target a press or release with historical pose data from the user's head or their controller:</span></span>
* <span data-ttu-id="875eb-313">에 사용할 수 있는 시점에 제스처 또는 컨트롤러 누르면 머리 포즈 발생 **대상** 사용자가 무엇을 확인 하려면 [gazing](gaze.md) 에서:</span><span class="sxs-lookup"><span data-stu-id="875eb-313">The head pose at the moment in time when a gesture or controller press occurred, which can be used for **targeting** to determine what the user was [gazing](gaze.md) at:</span></span>

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args) {
       var interactionSourceState = args.state;
       var headPose = interactionSourceState.headPose;
       RaycastHit raycastHit;
       if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
           var targetObject = raycastHit.collider.gameObject;
           // ...
       }
   }
   ```

* <span data-ttu-id="875eb-314">에 사용할 수 있는 시점에 동작 컨트롤러를 누르면 원본 포즈 발생 **대상** 어떤 사용자가 가리키는에서 컨트롤러를 확인 하려면.</span><span class="sxs-lookup"><span data-stu-id="875eb-314">The source pose at the moment in time when a motion controller press occurred, which can be used for **targeting** to determine what the user was pointing the controller at.</span></span>  <span data-ttu-id="875eb-315">눌러 발생 하는 컨트롤러의 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-315">This will be the state of the controller that experienced the press.</span></span>  <span data-ttu-id="875eb-316">컨트롤러 자체를 렌더링 하는 경우에 어떤 사용자가는 것이 좋습니다 컨트롤러를 렌더링 하는 자연 스러운 끝에서 대상 광선의 문제를 해결 하는 그립 자세 하지 않고 포인터 자세를 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-316">If you are rendering the controller itself, you can request the pointer pose rather than the grip pose, to shoot the targeting ray from what the user will consider the natural tip of that rendered controller:</span></span>

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args)
   {
       var interactionSourceState = args.state;
       var sourcePose = interactionSourceState.sourcePose;
       Vector3 sourceGripPosition;
       Quaternion sourceGripRotation;
       if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Pointer)) &&
           (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Pointer))) {
           RaycastHit raycastHit;
           if (Physics.Raycast(sourceGripPosition, sourceGripRotation * Vector3.forward, out raycastHit, 10)) {
               var targetObject = raycastHit.collider.gameObject;
               // ...
           }
       }
   }
   ```

### <a name="event-handlers-example"></a><span data-ttu-id="875eb-317">이벤트 처리기 예제</span><span class="sxs-lookup"><span data-stu-id="875eb-317">Event handlers example</span></span>

```cs
using UnityEngine.XR.WSA.Input;

void Start()
{
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased += InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
}

void OnDestroy()
{
    InteractionManager.InteractionSourceDetected -= InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost -= InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased -= InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;
}

void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
{
    // Source was detected
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceLost(InteractionSourceLostEventArgs state)
{
    // Source was lost. This will be after a SourceDetected event and no other events for this
    // source id will occur until it is Detected again
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs state)
{
    // Source was pressed. This will be after the source was detected and before it is 
    // released or lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceReleased(InteractionSourceReleasedEventArgs state)
{
    // Source was released. The source would have been detected and pressed before this point. 
    // This event will not fire if the source is lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs state)
{
    // Source was updated. The source would have been detected before this point
    // args.state has the current state of the source including id, position, kind, etc.
}
```

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a><span data-ttu-id="875eb-318">높은 수준의 복합 제스처 (GestureRecognizer) Api</span><span class="sxs-lookup"><span data-stu-id="875eb-318">High-level composite gesture APIs (GestureRecognizer)</span></span>

<span data-ttu-id="875eb-319">**Namespace:** *UnityEngine.XR.WSA.Input*</span><span class="sxs-lookup"><span data-stu-id="875eb-319">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="875eb-320">**형식**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*</span><span class="sxs-lookup"><span data-stu-id="875eb-320">**Types**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*</span></span>

<span data-ttu-id="875eb-321">앱 공간 입력된 소스를 누르기, 보류, 조작 및 탐색 제스처에 대 한 높은 수준의 복합 제스처를 인식할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-321">Your app can also recognize higher-level composite gestures for spatial input sources, Tap, Hold, Manipulation and Navigation gestures.</span></span> <span data-ttu-id="875eb-322">둘 사이에서 이러한 복합 제스처를 인식할 수 있습니다 [바늘](gestures.md) 하 고 [컨트롤러 동작](motion-controllers.md) 는 GestureRecognizer를 사용 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-322">You can recognize these composite gestures across both [hands](gestures.md) and [motion controllers](motion-controllers.md) using the GestureRecognizer.</span></span>

<span data-ttu-id="875eb-323">각 제스처 이벤트에는 GestureRecognizer 타기 팅 헤드 광선 뿐만 아니라 입력에 대 한 이벤트 시는 SourceKind를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-323">Each Gesture event on the GestureRecognizer provides the SourceKind for the input as well as the targeting head ray at the time of the event.</span></span> <span data-ttu-id="875eb-324">일부 이벤트는 특정 추가 컨텍스트 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-324">Some events provide additional context specific information.</span></span>

<span data-ttu-id="875eb-325">제스처 인식기를 사용 하 여 제스처를 캡처하는 데 필요한 몇 가지 단계만 가지</span><span class="sxs-lookup"><span data-stu-id="875eb-325">There are only a few steps required to capture gestures using a Gesture Recognizer:</span></span>
1. <span data-ttu-id="875eb-326">새 제스처 인식기를 만들려면</span><span class="sxs-lookup"><span data-stu-id="875eb-326">Create a new Gesture Recognizer</span></span>
2. <span data-ttu-id="875eb-327">조사 하는 제스처를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-327">Specify which gestures to watch for</span></span>
3. <span data-ttu-id="875eb-328">이러한 제스처에 대 한 이벤트 구독</span><span class="sxs-lookup"><span data-stu-id="875eb-328">Subscribe to events for those gestures</span></span>
4. <span data-ttu-id="875eb-329">제스처를 캡처하기 시작</span><span class="sxs-lookup"><span data-stu-id="875eb-329">Start capturing gestures</span></span>

### <a name="create-a-new-gesture-recognizer"></a><span data-ttu-id="875eb-330">새 제스처 인식기를 만들려면</span><span class="sxs-lookup"><span data-stu-id="875eb-330">Create a new Gesture Recognizer</span></span>

<span data-ttu-id="875eb-331">사용 하는 *GestureRecognizer*을 만들어야 합니다를 *GestureRecognizer*:</span><span class="sxs-lookup"><span data-stu-id="875eb-331">To use the *GestureRecognizer*, you must have created a *GestureRecognizer*:</span></span>

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a><span data-ttu-id="875eb-332">조사 하는 제스처를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-332">Specify which gestures to watch for</span></span>

<span data-ttu-id="875eb-333">제스처는 관심을 통해 지정 *SetRecognizableGestures()*:</span><span class="sxs-lookup"><span data-stu-id="875eb-333">Specify which gestures you are interested in via *SetRecognizableGestures()*:</span></span>

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a><span data-ttu-id="875eb-334">이러한 제스처에 대 한 이벤트 구독</span><span class="sxs-lookup"><span data-stu-id="875eb-334">Subscribe to events for those gestures</span></span>

<span data-ttu-id="875eb-335">관심이 있다면 제스처에 대 한 이벤트를 구독 합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-335">Subscribe to events for the gestures you are interested in.</span></span>

```cs
void Start()
{
    recognizer.Tapped += GestureRecognizer_Tapped;
    recognizer.HoldStarted += GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted += GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled += GestureRecognizer_HoldCanceled;
}
```

>[!NOTE]
><span data-ttu-id="875eb-336">탐색 및 조작 제스처 인스턴스에서 상호 배타적인를 *GestureRecognizer*합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-336">Navigation and Manipulation gestures are mutually exclusive on an instance of a *GestureRecognizer*.</span></span>

### <a name="start-capturing-gestures"></a><span data-ttu-id="875eb-337">제스처를 캡처하기 시작</span><span class="sxs-lookup"><span data-stu-id="875eb-337">Start capturing gestures</span></span>

<span data-ttu-id="875eb-338">기본적으로 *GestureRecognizer* 까지 입력을 모니터링 하지 않습니다 *StartCapturingGestures()* 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-338">By default, a *GestureRecognizer* does not monitor input until *StartCapturingGestures()* is called.</span></span> <span data-ttu-id="875eb-339">후 제스처 이벤트를 발생할 수 있기 *StopCapturingGestures()* 입력 프레임 하기 전에 수행 된 경우 호출 됩니다. 여기서 *StopCapturingGestures()* 처리 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-339">It is possible that a gesture event may be generated after *StopCapturingGestures()* is called if input was performed before the frame where *StopCapturingGestures()* was processed.</span></span> <span data-ttu-id="875eb-340">합니다 *GestureRecognizer* 여부를 때 또는 해제 하는 제스처 실제로 발생 한 previou 프레임 따라서 시작 하려면 신뢰할 수 있는 것 및 대상 지정이 프레임 응시에 따라 중지 제스처 모니터링에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-340">The *GestureRecognizer* will remember whether it was on or off during the previou frame in which the gesture actually occurred, and so it is reliable to start and stop gesture monitoring based on this frame's gaze targeting.</span></span>

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a><span data-ttu-id="875eb-341">제스처를 캡처를 중지합니다</span><span class="sxs-lookup"><span data-stu-id="875eb-341">Stop capturing gestures</span></span>

<span data-ttu-id="875eb-342">제스처 인식을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-342">To stop gesture recognition:</span></span>

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a><span data-ttu-id="875eb-343">제스처 인식기를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-343">Removing a gesture recognizer</span></span>

<span data-ttu-id="875eb-344">제거 하기 전에 이벤트 구독된에서 구독을 취소 하는 *GestureRecognizer* 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-344">Remember to unsubscribe from subscribed events before destroying a *GestureRecognizer* object.</span></span>

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a><span data-ttu-id="875eb-345">Unity의 동작 컨트롤러 모델 렌더링</span><span class="sxs-lookup"><span data-stu-id="875eb-345">Rendering the motion controller model in Unity</span></span>

<span data-ttu-id="875eb-346">![동작 컨트롤러 모델 및 텔레포트](images/motioncontrollertest-teleport-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="875eb-346">![Motion Controller model and teleportation](images/motioncontrollertest-teleport-1000px.png)</span></span><br>
<span data-ttu-id="875eb-347">*동작 컨트롤러 모델 및 텔레포트*</span><span class="sxs-lookup"><span data-stu-id="875eb-347">*Motion controller model and teleportation*</span></span>

<span data-ttu-id="875eb-348">렌더링 되는 실제 컨트롤러 보유 하 고 다양 한 단추를 누를 때 표현 하는 사용자가 일치 하는 앱에서 동작 컨트롤러를 사용할 수 있습니다 합니다 **MotionController prefab** 에 [혼합 현실 도구 키트 ](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span><span class="sxs-lookup"><span data-stu-id="875eb-348">To render motion controllers in your app that match the physical controllers your users are holding and articulate as various buttons are pressed, you can use the **MotionController prefab** in the [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span></span>  <span data-ttu-id="875eb-349">이 prefab 시스템의 설치 동작 컨트롤러 드라이버에서 런타임 시 올바른 glTF 모델을 동적으로 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-349">This prefab dynamically loads the correct glTF model at runtime from the system's installed motion controller driver.</span></span>  <span data-ttu-id="875eb-350">이러한 모델을 동적으로 로드 해야 것이 아니라 가져와 수동으로 편집기에서 앱 표시 되도록 모든 현재 및 미래의 컨트롤러에 대 한 3D 모델을 물리적으로 정확 하 게 사용자가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-350">It's important to load these models dynamically rather than importing them manually in the editor, so that your app will show physically accurate 3D models for any current and future controllers your users may have.</span></span>

1. <span data-ttu-id="875eb-351">수행 합니다 [Getting Started](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) 혼합 현실 도구 키트를 다운로드 하 여 Unity 프로젝트에 추가 하는 지침입니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-351">Follow the [Getting Started](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) instructions to download the Mixed Reality Toolkit and add it to your Unity project.</span></span>
2. <span data-ttu-id="875eb-352">사용 하 여 카메라를 대체 하는 경우는 *MixedRealityCameraParent* prefab 준비가 시작 단계 중 일부로!</span><span class="sxs-lookup"><span data-stu-id="875eb-352">If you replaced your camera with the *MixedRealityCameraParent* prefab as part of the Getting Started steps, you're good to go!</span></span>  <span data-ttu-id="875eb-353">해당 prefab 컨트롤러 렌더링 동작을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-353">That prefab includes motion controller rendering.</span></span>  <span data-ttu-id="875eb-354">추가 고, 그렇지 *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* 프로젝트 창에서 장면에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-354">Otherwise, add *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* into your scene from the Project pane.</span></span>  <span data-ttu-id="875eb-355">부모 개체의 자식으로 prefab 사용 하는 경우 카메라를 이동 하려면 추가 하는 것이 좋습니다 장면 내 사용자 텔레포트 시킵니다 컨트롤러 사용자와 함께 제공 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-355">You'll want to add that prefab as a child of whatever parent object you use to move the camera around when the user teleports within your scene, so that the controllers come along with the user.</span></span>  <span data-ttu-id="875eb-356">앱에 텔레포트과 관련이 없는 prefab 장면의 루트에 추가 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-356">If your app does not involve teleporting, just add the prefab at the root of your scene.</span></span>

## <a name="throwing-objects"></a><span data-ttu-id="875eb-357">개체를 throw합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-357">Throwing objects</span></span>

<span data-ttu-id="875eb-358">어려운 문제는 가상 현실에서 개체를 throw 되 고 처음 보입니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-358">Throwing objects in virtual reality is a harder problem then it may at first seem.</span></span> <span data-ttu-id="875eb-359">실제로 가장 기반된 조작, 예기치 않은 방식으로 게임 역할에서 throw 할 때와 마찬가지로 갈피 이며 집중 교육을 중단 합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-359">As with most physically based interactions, when throwing in game acts in an unexpected way, it is immediately obvious and breaks immersion.</span></span> <span data-ttu-id="875eb-360">고려할 어느 정도의 시간이 필요 throwing 실제로 올바른 동작을 나타내며를 공유 하고자 하는 우리의 플랫폼에 대 한 업데이트를 통해 사용 하도록 설정 하는 몇 가지 지침, 개발 하는 방법에 대 한 긴밀 하 게 투자 있어야 했습니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-360">We have spent some time thinking deeply about how to represent a physically correct throwing behavior, and have come up with a few guidelines, enabled through updates to our platform, that we would like to share with you.</span></span>

<span data-ttu-id="875eb-361">throw를 구현 하려면 권장 방법의 예제를 찾을 수 있습니다 [여기](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage)합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-361">You can find an example of how we recommend to implement throwing [here](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span></span> <span data-ttu-id="875eb-362">이 샘플이 네 가지 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-362">This sample follows these four guidelines:</span></span>
* <span data-ttu-id="875eb-363">**컨트롤러를 사용할 *속도* 위치 대신**합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-363">**Use the controller’s *velocity* instead of position**.</span></span> <span data-ttu-id="875eb-364">Windows 11 월 업데이트에서 변경 된 동작을 도입 했습니다 때 합니다 [위치 추적 상태를 ' 근사치'](motion-controllers.md#controller-tracking-state)합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-364">In the November update to Windows, we introduced a change in behavior when in the [''Approximate'' positional tracking state](motion-controllers.md#controller-tracking-state).</span></span> <span data-ttu-id="875eb-365">이 상태에서는 컨트롤러에 대 한 속도 정보는 종종 위치 높은 정확도 유지 하는 보다 더 높은 정확도 것으로 보고 됩니다 계속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-365">When in this state, velocity information about the controller will continue to be reported for as long as we believe it is high accuracy, which is often longer than position remains high accuracy.</span></span>
* <span data-ttu-id="875eb-366">**통합 된 *각도 속도* 컨트롤러의**합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-366">**Incorporate the *angular velocity* of the controller**.</span></span> <span data-ttu-id="875eb-367">이 논리에 포함 된 모든 합니다 `throwing.cs` 파일을 `GetThrownObjectVelAngVel` 위에 링크 된 패키지 내에서 정적 메서드:</span><span class="sxs-lookup"><span data-stu-id="875eb-367">This logic is all contained in the `throwing.cs` file in the `GetThrownObjectVelAngVel` static method, within the package linked above:</span></span>
   1. <span data-ttu-id="875eb-368">각도 속도 절약 됩니다으로 throw 된 개체를 throw 하는 시점에 있었던 것과 동일한 angular 개발 속도 유지 해야 합니다. `objectAngularVelocity = throwingControllerAngularVelocity;`</span><span class="sxs-lookup"><span data-stu-id="875eb-368">As angular velocity is conserved, the thrown object must maintain the same angular velocity as it had at the moment of the throw: `objectAngularVelocity = throwingControllerAngularVelocity;`</span></span>
   2. <span data-ttu-id="875eb-369">으로 throw 된 개체의 대용량의 중심 그립 포즈의 원점에 가능성이 된 다양 한 속도 컨트롤러의 사용자의 참조 프레임에서에서 가능성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-369">As the center of mass of the thrown object is likely not at the origin of the grip pose, it likely has a different velocity then that of the controller in the frame of reference of the user.</span></span> <span data-ttu-id="875eb-370">이러한 방식으로 제공 하는 개체의 개발 속도의 부분은 컨트롤러 원점에서 throw 된 개체의 대용량의 중심의 즉각적인 탄젠트 속도입니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-370">The portion of the object’s velocity contributed in this way is the instantaneous tangential velocity of the center of mass of the thrown object around the controller origin.</span></span> <span data-ttu-id="875eb-371">탄젠트 속도가이 컨트롤러 원점에서 throw 된 개체의 대용량의 중심 사이의 거리를 나타내는 벡터를 사용 하 여 컨트롤러의 angular 개발 속도의 교차곱을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-371">This tangential velocity is the cross product of the angular velocity of the controller with the vector representing the distance between the controller origin and the center of mass of the thrown object.</span></span>
    
      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```
   
   3. <span data-ttu-id="875eb-372">Throw 된 개체의 총 속도 따라서 컨트롤러의 개발 속도 및이 탄젠트 속도의 합입니다. `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span><span class="sxs-lookup"><span data-stu-id="875eb-372">The total velocity of the thrown object is thus the sum of velocity of the controller and this tangential velocity: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span></span>

* <span data-ttu-id="875eb-373">**주의를 기울여야 합니다 *시간* 속도는 적용**합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-373">**Pay close attention to the *time* at which we apply the velocity**.</span></span> <span data-ttu-id="875eb-374">단추를 누를 때 운영 체제에 Bluetooth를 통해 버블 업 이벤트에 대 한 최대 20ms 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-374">When a button is pressed, it can take up to 20ms for that event to bubble up through Bluetooth to the operating system.</span></span> <span data-ttu-id="875eb-375">즉,에서 컨트롤러 상태 변경에 대 한 폴링 누르지 하기 위해 누르는 경우 그 반대의 경우이 사용 하 여 얻을 수 있는 컨트롤러 포즈 정보 되는 사전 상태에서이 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-375">This means that if you poll for a controller state change from pressed to not pressed or vice versa, the controller pose information you get with it will actually be ahead of this change in state.</span></span> <span data-ttu-id="875eb-376">또한이 폴링 API에서 제공 되는 컨트롤러 포즈 자세한 다음 20ms를 나중에 될 수 있는 프레임을 표시할 때 가능성이 포즈를 반영 하기 위해 앞으로 예측 됩니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-376">Further, the controller pose presented by our polling API is forward predicted to reflect a likely pose at the time the frame will be displayed which could be more then 20ms in the future.</span></span> <span data-ttu-id="875eb-377">좋은 점 *렌더링* 개체를 보유 하지만 시간 문제에 대 한 않았을 *대상으로 하* 개체 잠시 궤적 계산 사용자 출시가 throw 합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-377">This is good for *rendering* held objects, but compounds our time problem for *targeting* the object as we calculate the trajectory for the moment the user released their throw.</span></span> <span data-ttu-id="875eb-378">다행 스럽게도 때 Unity 이벤트 11 월 업데이트를 사용 하 여 *InteractionSourcePressed* 또는 *InteractionSourceReleased* , 전송 상태 기록 포즈 데이터가 포함 됩니다 때 백 단추 실제로 누름 이거나 출시 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-378">Fortunately, with the November update, when a Unity event like *InteractionSourcePressed* or *InteractionSourceReleased* is sent, the state includes the historical pose data from back when the button was actually pressed or released.</span></span>  <span data-ttu-id="875eb-379">가장 정확한 컨트롤러 렌더링 및 throw 하는 동안 대상으로 컨트롤러를 얻으려면 올바르게 사용 해야 폴링 및 이벤트를 적절 하 게 합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-379">To get the most accurate controller rendering and controller targeting during throws, you must correctly use polling and eventing, as appropriate:</span></span>
   * <span data-ttu-id="875eb-380">에 대 한 **컨트롤러 렌더링** 각 프레임을 앱에 컨트롤러의 배치 해야 *GameObject* 정방향 예측 컨트롤러에서 현재 프레임의 photon 시간 위한 포즈 합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-380">For **controller rendering** each frame, your app should position the controller's *GameObject* at the forward-predicted controller pose for the current frame’s photon time.</span></span>  <span data-ttu-id="875eb-381">Unity와 같은 폴링 Api에서에서이 데이터를 가져올 *[xr 하이 있습니다. InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* 하거나  *[xr 하이 있습니다. WSA입니다. Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)* 합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-381">You get this data from Unity polling APIs like *[XR.InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* or *[XR.WSA.Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.</span></span>
   * <span data-ttu-id="875eb-382">에 대 한 **컨트롤러를 대상으로 하** 누르거나 릴리스 시 앱 raycast 해야 하 고 해당 키를 눌러 또는 릴리스 이벤트에 대 한 기록 컨트롤러 포즈 기반 궤적을 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-382">For **controller targeting** upon a press or release, your app should raycast and calculate trajectories based on the historical controller pose for that press or release event.</span></span>  <span data-ttu-id="875eb-383">같은 Unity 이벤트 Api에서에서이 데이터를 가져올  *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)* 합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-383">You get this data from Unity eventing APIs, like *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.</span></span>
* <span data-ttu-id="875eb-384">**그립 자세를 사용 하 여**입니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-384">**Use the grip pose**.</span></span> <span data-ttu-id="875eb-385">각도 속도 및 개발 속도 포인터 자세 하지 그립 자세를 기준으로 보고 됩니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-385">Angular velocity and velocity are reported relative to the grip pose, not pointer pose.</span></span>

<span data-ttu-id="875eb-386">향후 Windows 업데이트로 향상 계속를 throw 하 고 여기에서 자세한 내용을 보려면 예상할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-386">Throwing will continue to improve with future Windows updates, and you can expect to find more information on it here.</span></span>

## <a name="accelerate-development-with-mixed-reality-toolkit"></a><span data-ttu-id="875eb-387">혼합 현실 도구 키트를 사용 하 여 개발 가속화</span><span class="sxs-lookup"><span data-stu-id="875eb-387">Accelerate development with Mixed Reality Toolkit</span></span>

<span data-ttu-id="875eb-388">두 예제에서는 장면 InputManager 및 Unity에서 MotionController에 대 한 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-388">There are two example scenes about InputManager and MotionController in Unity.</span></span> <span data-ttu-id="875eb-389">이러한 작업을 통해 MRTK의 InputManager를 사용 하 여 동작 컨트롤러 단추에서 이벤트를 처리 하는 데이터에 액세스 하는 방법을 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-389">Through these scenes, you can learn how to use MRTK's InputManager and access data handle events from the motion controller buttons.</span></span>

- [<span data-ttu-id="875eb-390">HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity</span><span class="sxs-lookup"><span data-stu-id="875eb-390">HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity)
- [<span data-ttu-id="875eb-391">HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity</span><span class="sxs-lookup"><span data-stu-id="875eb-391">HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity)
- [<span data-ttu-id="875eb-392">기술 세부 정보 추가 정보 파일</span><span class="sxs-lookup"><span data-stu-id="875eb-392">Technical details README File</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input)

<span data-ttu-id="875eb-393">![MRTK의 예에서는 내부에서를 입력 합니다.](images/MRTK_ExampleScene_Input.png)</span><span class="sxs-lookup"><span data-stu-id="875eb-393">![Input example scenes in MRTK](images/MRTK_ExampleScene_Input.png)</span></span><br>
<span data-ttu-id="875eb-394">*MRTK의 예에서는 내부에서를 입력 합니다.*</span><span class="sxs-lookup"><span data-stu-id="875eb-394">*Input example scenes in MRTK*</span></span>

### <a name="automatic-scene-setup"></a><span data-ttu-id="875eb-395">장면 자동 설치</span><span class="sxs-lookup"><span data-stu-id="875eb-395">Automatic scene setup</span></span>

<span data-ttu-id="875eb-396">가져올 때 [MRTK Unity 패키지를 릴리스](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) 에서 프로젝트를 복제 또는 합니다 [GitHub 리포지토리](https://github.com/Microsoft/MixedRealityToolkit-Unity), Unity에서 새 메뉴 ' 혼합 현실 Toolkit'를 찾을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-396">When you import [MRTK release Unity packages](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) or clone the project from the [GitHub repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), you are going to find a new menu 'Mixed Reality Toolkit' in Unity.</span></span> <span data-ttu-id="875eb-397">'구성' 메뉴 아래에서 적용 혼합 현실 장면 [설정] 메뉴를 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-397">Under 'Configure' menu, you will see the menu 'Apply Mixed Reality Scene Settings'.</span></span> <span data-ttu-id="875eb-398">기본 카메라를 제거 하 고 기본 구성 요소 추가 클릭 하면 [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab)하십시오 [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), 및 [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab)합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-398">When you click it, it removes the default camera and adds foundational components - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), and [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).</span></span>

<span data-ttu-id="875eb-399">![장면 설치용 MRTK 메뉴](images/MRTK_Input_Menu.png)</span><span class="sxs-lookup"><span data-stu-id="875eb-399">![MRTK Menu for scene setup](images/MRTK_Input_Menu.png)</span></span><br>
<span data-ttu-id="875eb-400">*장면 설치용 MRTK 메뉴*</span><span class="sxs-lookup"><span data-stu-id="875eb-400">*MRTK Menu for scene setup*</span></span>

<span data-ttu-id="875eb-401">![MRTK 자동 장면 설치](images/MRTK_HowTo_Input1.png)</span><span class="sxs-lookup"><span data-stu-id="875eb-401">![Automatic scene setup in MRTK](images/MRTK_HowTo_Input1.png)</span></span><br>
<span data-ttu-id="875eb-402">*MRTK 자동 장면 설치*</span><span class="sxs-lookup"><span data-stu-id="875eb-402">*Automatic scene setup in MRTK*</span></span>

### <a name="mixedrealitycamera-prefab"></a><span data-ttu-id="875eb-403">MixedRealityCamera prefab</span><span class="sxs-lookup"><span data-stu-id="875eb-403">MixedRealityCamera prefab</span></span>

<span data-ttu-id="875eb-404">프로젝트 패널에서 수동으로 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-404">You can also manually add these from the project panel.</span></span> <span data-ttu-id="875eb-405">Prefabs로 이러한 구성 요소를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-405">You can find these components as prefabs.</span></span> <span data-ttu-id="875eb-406">검색 하는 경우 **MixedRealityCamera**, 두 개의 다른 카메라 prefabs 참조 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-406">When you search **MixedRealityCamera**, you will be able to see two different camera prefabs.</span></span> <span data-ttu-id="875eb-407">차이점은 **MixedRealityCamera** 전용인 카메라 prefab 반면 **MixedRealityCameraParent** 텔레포트, 동작 등 몰입 형 헤드셋에 대 한 추가 구성 요소를 포함 합니다. 컨트롤러를 경계입니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-407">The difference is, **MixedRealityCamera** is the camera only prefab whereas, **MixedRealityCameraParent** includes additional components for the immersive headsets such as Teleportation, Motion Controller and, Boundary.</span></span>

<span data-ttu-id="875eb-408">![MRTK에서 카메라 prefabs](images/MRTK_HowTo_Input2.png)</span><span class="sxs-lookup"><span data-stu-id="875eb-408">![Camera prefabs in MRTK](images/MRTK_HowTo_Input2.png)</span></span><br>
<span data-ttu-id="875eb-409">*MRTK에서 카메라 prefabs*</span><span class="sxs-lookup"><span data-stu-id="875eb-409">*Camera prefabs in MRTK*</span></span>

<span data-ttu-id="875eb-410">**MixedRealtyCamera** HoloLens 및 몰입 형 헤드셋을 모두 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-410">**MixedRealtyCamera** supports both HoloLens and immersive headset.</span></span> <span data-ttu-id="875eb-411">장치 유형을 검색 하 고 플래그 지우기 등 Skybox 속성 최적화 합니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-411">It detects the device type and optimizes the properties such as clear flags and Skybox.</span></span> <span data-ttu-id="875eb-412">다음 사용자 지정 커서 동작 컨트롤러 모델 같은 사용자 지정 하는 Floor 유용한 속성 중 일부를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-412">Below you can find some of the useful properties you can customize such as custom Cursor, Motion Controller models, and Floor.</span></span>

<span data-ttu-id="875eb-413">![커서 및 Floor 동작 컨트롤러에 대 한 속성](images/MRTK_HowTo_Input3.png)</span><span class="sxs-lookup"><span data-stu-id="875eb-413">![Properties for the Motion controller, Cursor and Floor](images/MRTK_HowTo_Input3.png)</span></span><br>
<span data-ttu-id="875eb-414">*커서 및 Floor 동작 컨트롤러에 대 한 속성*</span><span class="sxs-lookup"><span data-stu-id="875eb-414">*Properties for the Motion controller, Cursor and Floor*</span></span>

## <a name="follow-along-with-tutorials"></a><span data-ttu-id="875eb-415">자습서를 따라</span><span class="sxs-lookup"><span data-stu-id="875eb-415">Follow along with tutorials</span></span>

<span data-ttu-id="875eb-416">혼합 현실 아카데미에서 사용할 수 있는 자세한 사용자 지정 예제를 사용한 단계별 자습서 같습니다.</span><span class="sxs-lookup"><span data-stu-id="875eb-416">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="875eb-417">MR 입력 211: 제스처</span><span class="sxs-lookup"><span data-stu-id="875eb-417">MR Input 211: Gesture</span></span>](holograms-211.md)
- [<span data-ttu-id="875eb-418">MR 입력 213: 컨트롤러 동작</span><span class="sxs-lookup"><span data-stu-id="875eb-418">MR Input 213: Motion controllers</span></span>](mixed-reality-213.md)

<span data-ttu-id="875eb-419">[![MR 입력 213-컨트롤러 동작](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="875eb-419">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="875eb-420">*MR 입력 213-컨트롤러 동작*</span><span class="sxs-lookup"><span data-stu-id="875eb-420">*MR Input 213 - Motion controller*</span></span>

## <a name="see-also"></a><span data-ttu-id="875eb-421">참조</span><span class="sxs-lookup"><span data-stu-id="875eb-421">See also</span></span>

* [<span data-ttu-id="875eb-422">제스처</span><span class="sxs-lookup"><span data-stu-id="875eb-422">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="875eb-423">컨트롤러 동작</span><span class="sxs-lookup"><span data-stu-id="875eb-423">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="875eb-424">UnityEngine.XR.WSA.Input</span><span class="sxs-lookup"><span data-stu-id="875eb-424">UnityEngine.XR.WSA.Input</span></span>](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [<span data-ttu-id="875eb-425">UnityEngine.XR.InputTracking</span><span class="sxs-lookup"><span data-stu-id="875eb-425">UnityEngine.XR.InputTracking</span></span>](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [<span data-ttu-id="875eb-426">InteractionInputSource.cs MixedRealityToolkit Unity에서</span><span class="sxs-lookup"><span data-stu-id="875eb-426">InteractionInputSource.cs in MixedRealityToolkit-Unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/InputSources/InteractionInputSource.cs)
