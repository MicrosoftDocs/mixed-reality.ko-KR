---
title: Unreal에서 직접 추적
description: Unreal에서 수동 추적을 사용 하는 방법을 설명 합니다.
author: AndreyChistyakov
ms.author: anchisty
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, 핸드 추적
ms.openlocfilehash: 3f7f4dd1eb62cb707eaaf8632a2ba3c280a4ac31
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835446"
---
# <a name="hand-tracking"></a><span data-ttu-id="9119a-104">수동 추적</span><span class="sxs-lookup"><span data-stu-id="9119a-104">Hand Tracking</span></span>

<span data-ttu-id="9119a-105">손으로 추적 시스템은 사용자의 palms를 사용 하 여 실수에 대 한 입력으로 손가락을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-105">The hand tracking system uses a person’s palms and fingers as input to Unreal.</span></span> <span data-ttu-id="9119a-106">개발자는 모든 손가락의 위치와 회전, 전체 palm 및 자체 코드에서 사용할 제스처를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-106">A developer can get every finger’s position and rotation, the entire palm, and even hand gestures to use in their own code.</span></span> 

## <a name="hand-pose"></a><span data-ttu-id="9119a-107">직접 포즈</span><span class="sxs-lookup"><span data-stu-id="9119a-107">Hand Pose</span></span>

<span data-ttu-id="9119a-108">개발자는 직접 포즈를 사용 하 여 활성 사용자의 손으로와 손가락을 입력으로 추적할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-108">Using the hand pose, developers can track the hands and fingers of the active user as input.</span></span> <span data-ttu-id="9119a-109">이 시스템은 청사진과 c + +를 통해 노출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-109">This system is exposed through both Blueprints and C++.</span></span> <span data-ttu-id="9119a-110">기술 세부 정보는 해당 하는 WinRT 클래스 [창](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) 에 있습니다 .이 UNREAL API는 unreal의 좌표계 형식으로 데이터를 제공 하 고 틱은 Unreal 엔진과 전환은 합니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-110">Technical details are in the corresponding WinRT class [Windows.Perception.People.HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) This Unreal API provides the data in the format of Unreal’s coordinate system and ticks are synchronised with the Unreal Engine.</span></span>

### <a name="enum"></a><span data-ttu-id="9119a-111">열거형</span><span class="sxs-lookup"><span data-stu-id="9119a-111">Enum</span></span>

<span data-ttu-id="9119a-112">EWMRHandKeypoint는 손 모양의 뼈 계층 구조를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-112">EWMRHandKeypoint describes the Hand’s bone hierarchy.</span></span> 

<span data-ttu-id="9119a-113">청사진</span><span class="sxs-lookup"><span data-stu-id="9119a-113">Blueprint:</span></span>

![핸드 Keypoint BP](images/unreal/hand-keypoint-bp.png)
 
<span data-ttu-id="9119a-115">C++:</span><span class="sxs-lookup"><span data-stu-id="9119a-115">C++:</span></span>
```cpp
enum class EWMRHandKeypoint : uint8
{
    Palm,
    Wrist,
    ThumbMetacarpal,
    ThumbProximal,
    ThumbDistal,
    ThumbTip,
    IndexMetacarpal,
    IndexProximal,
    IndexIntermediate,
    IndexDistal,
    IndexTip,
    MiddleMetacarpal,
    MiddleProximal,
    MiddleIntermediate,
    MiddleDistal,
    MiddleTip,
    RingMetacarpal,
    RingProximal,
    RingIntermediate,
    RingDistal,
    RingTip,
    LittleMetacarpal,
    LittleProximal,
    LittleIntermediate,
    LittleDistal,
    LittleTip
};
```

![직접 기초](images/hand-skeleton.png)

<span data-ttu-id="9119a-117">숫자 값은 [HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) 테이블에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-117">The numerical values can be found in the table [Windows.Perception.People.HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind)</span></span>
 
### <a name="functions"></a><span data-ttu-id="9119a-118">Functions</span><span class="sxs-lookup"><span data-stu-id="9119a-118">Functions</span></span>

<span data-ttu-id="9119a-119">청사진에서 직접 추적 함수를 사용 하려면 "핸드 추적/Windows Mixed Reality"를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-119">To use hand tracking functions in Blueprints, open "Hand Tracking/Windows Mixed Reality"</span></span>

![수동 추적 BP](images/unreal/hand-tracking-bp.png)

<span data-ttu-id="9119a-121">C + + 함수에는 "WindowsMixedRealityHandTrackingFunctionLibrary"를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-121">For C++ functions, include "WindowsMixedRealityHandTrackingFunctionLibrary.h"</span></span>

<span data-ttu-id="9119a-122">BP</span><span class="sxs-lookup"><span data-stu-id="9119a-122">BP:</span></span>

![수동 추적 BP 지원](images/unreal/supports-hand-tracking-bp.png)
 
<span data-ttu-id="9119a-124">C++:</span><span class="sxs-lookup"><span data-stu-id="9119a-124">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

<span data-ttu-id="9119a-125">장치에서 직접 추적이 지원 되 면 true를 반환 하 고, 수동 추적을 사용할 수 없으면 false를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-125">Returns true if hand tracking is supported on the device, false if hand tracking is not available.</span></span>

<span data-ttu-id="9119a-126">BP</span><span class="sxs-lookup"><span data-stu-id="9119a-126">BP:</span></span>

![핸드 조인트 변환 가져오기](images/unreal/get-hand-joint-transform.png)
 
<span data-ttu-id="9119a-128">C++:</span><span class="sxs-lookup"><span data-stu-id="9119a-128">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

<span data-ttu-id="9119a-129">이 함수는 손 모양의 공간 데이터를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-129">This function returns spatial data of the hand.</span></span> <span data-ttu-id="9119a-130">데이터는 프레임 내에서 반환 된 값이 캐시 되는 모든 프레임을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-130">The data updates every frame, inside a frame the returned values are cached.</span></span> <span data-ttu-id="9119a-131">성능상의 이유로이 함수에는 높은 논리를 포함 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-131">It is not recommended to have heavy logic on this function for performance reasons.</span></span> 

* <span data-ttu-id="9119a-132">사용자를 **위해 왼쪽 또는** 오른쪽 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-132">**Hand** – hand of the user, may be left or right</span></span>
* <span data-ttu-id="9119a-133">**Keypoint** – 바늘의 뼈입니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-133">**Keypoint** – the bone of the hand.</span></span> 
* <span data-ttu-id="9119a-134">**변환** – 뼈의 기본 좌표와 방향입니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-134">**Transform** – coordinates and orientation of bone’s base.</span></span> <span data-ttu-id="9119a-135">뼈의 끝에 대 한 변환 데이터를 가져오려면 다음 뼈의 밑수를 요청 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-135">To get the transform data for the end of a bone, the base of the next bone should be requested.</span></span> <span data-ttu-id="9119a-136">특수 팁 뼈는 distal의 끝을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-136">A special Tip bone gives end of distal.</span></span> 
* <span data-ttu-id="9119a-137">**Radius** -뼈 밑의 반경입니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-137">**Radius** — radius of the base of the bone.</span></span>
* <span data-ttu-id="9119a-138">**반환 값** -뼈가이 프레임을 추적 하면 true이 고, 뼈가 추적 되지 않으면 false입니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-138">**Return Value** — true if the bone is tracked this frame, false if the bone is not tracked.</span></span>

## <a name="hand-live-link-animation"></a><span data-ttu-id="9119a-139">손 모양 링크 애니메이션</span><span class="sxs-lookup"><span data-stu-id="9119a-139">Hand Live Link Animation</span></span>
<span data-ttu-id="9119a-140">손 포즈는 라이브 링크 플러그 인을 사용 하 여 애니메이션에 노출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-140">Hand poses are exposed to Animation using the Live Link plugin.</span></span> <span data-ttu-id="9119a-141">플러그 인 설명서는 [여기](https://docs.unrealengine.com/en-US/Engine/Animation/LiveLinkPlugin/index.html) 에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-141">The plugin documentation is [here](https://docs.unrealengine.com/en-US/Engine/Animation/LiveLinkPlugin/index.html)</span></span>

<span data-ttu-id="9119a-142">Windows Mixed Reality 및 라이브 링크 플러그 인을 사용 하는 경우 **창 > 라이브 링크로** 이동 하 여 라이브 링크 편집기 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-142">If the Windows Mixed Reality and Live Link plugins are enabled, go to **Window > Live Link** to open the Live Link editor window.</span></span> <span data-ttu-id="9119a-143">**+ 소스 단추** 를 클릭 하 고 Windows Mixed Reality 추적 소스를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-143">Click the **+ Source button** and enable Windows Mixed Reality Hand Tracking Source</span></span>

![라이브 링크 소스](images/unreal/live-link-source.png)
 
<span data-ttu-id="9119a-145">소스를 사용 하도록 설정 하 고 애니메이션 자산을 연 후 애니메이션의 장면 미리 보기 탭에는 다음과 같은 추가 옵션이 포함 됩니다. (플러그 인이 베타에 있으므로 해당 프로세스는 나중에 변경 될 수 있습니다.)</span><span class="sxs-lookup"><span data-stu-id="9119a-145">After you enable the source and open any animation asset, the Preview Scene tab of Animation will have the following additional options (the details are in Unreal’s Live Link documentation- as the plugin is in beta, the process may change later)</span></span>

![라이브 링크 애니메이션](images/unreal/live-link-animation.png)
 
<span data-ttu-id="9119a-147">손 모양 애니메이션 계층은 EWMRHandKeypoint에서와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-147">The hand animation hierarchy is the same as in EWMRHandKeypoint.</span></span> <span data-ttu-id="9119a-148">WindowsMixedRealityHandTrackingLiveLinkRemapAsset를 사용 하 여 애니메이션의 대상을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-148">Animation can be retargeted using WindowsMixedRealityHandTrackingLiveLinkRemapAsset.</span></span> 

![라이브 링크 애니메이션 2](images/unreal/live-link-animation2.png)
 
<span data-ttu-id="9119a-150">편집기에서 서브클래싱 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-150">It can be subclassed in the editor</span></span>

![라이브 링크 다시 매핑](images/unreal/live-link-remap.png)
 
## <a name="hand-mesh"></a><span data-ttu-id="9119a-152">손 모양 메시</span><span class="sxs-lookup"><span data-stu-id="9119a-152">Hand Mesh</span></span>
<span data-ttu-id="9119a-153">사용자 손을 나타내는 메시입니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-153">Mesh representing the user hands.</span></span> 

![손 모양 메시](images/unreal/hand-mesh.png)
 
### <a name="how-to-enable-and-configure"></a><span data-ttu-id="9119a-155">설정 및 구성 방법</span><span class="sxs-lookup"><span data-stu-id="9119a-155">How to enable and configure</span></span>

<span data-ttu-id="9119a-156">개발자는 직접 메시에 직접 액세스 하 여 자신만의 용도를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-156">Developers can get direct access to hand meshes for their own purposes.</span></span> <span data-ttu-id="9119a-157">이 액세스는 ARSessionConfig: AR 설정-> 세계 매핑-> 추적 된 기 하 도형에서 메시 데이터를 생성 하는 것으로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-157">This access must be enabled in ARSessionConfig: AR Settings -> World Mapping -> Generate Mesh Data from Tracked Geometry.</span></span> 

<span data-ttu-id="9119a-158">메시의 기본 매개 변수는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-158">Here are the default parameters for meshes:</span></span>

1.  <span data-ttu-id="9119a-159">폐색에 대 한 메시 데이터 사용</span><span class="sxs-lookup"><span data-stu-id="9119a-159">Use Mesh Data for Occlusion</span></span>
2.  <span data-ttu-id="9119a-160">메시 데이터의 충돌 생성</span><span class="sxs-lookup"><span data-stu-id="9119a-160">Generate Collision for Mesh Data</span></span>
3.  <span data-ttu-id="9119a-161">메시 데이터의 Nav 메시 생성</span><span class="sxs-lookup"><span data-stu-id="9119a-161">Generate Nav Mesh for Mesh Data</span></span>
4.  <span data-ttu-id="9119a-162">와이어 프레임으로 메시 데이터 렌더링 – 생성 된 메시를 표시 하는 디버그 매개 변수</span><span class="sxs-lookup"><span data-stu-id="9119a-162">Render Mesh Data in Wireframe – debug parameter that shows generated mesh</span></span>

<span data-ttu-id="9119a-163">혼합 현실 프로젝트의 경우 이러한 매개 변수 값은 공간 매핑 메시 및 손 모양 메시 기본값으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-163">For mixed reality projects, these parameter values will be used as the spatial mapping mesh and hand mesh defaults.</span></span> <span data-ttu-id="9119a-164">개발자는 특정 메시에 대해 BP 또는 코드에서이를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-164">Developers can change them in BP or code for any particular mesh.</span></span>

### <a name="c-api-reference"></a><span data-ttu-id="9119a-165">C + + API 참조</span><span class="sxs-lookup"><span data-stu-id="9119a-165">C++ API Reference</span></span> 
```cpp
enum class EARObjectClassification : uint8
{
// other types 
    HandMesh,
};
```

<span data-ttu-id="9119a-166">이 값은 모든 추적 가능 개체 간의 손 메시입니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-166">This value is the hand mesh among all trackable objects.</span></span>

```cpp
class FARSupportInterface 
{
public:
// other params 
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableAdded)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableUpdated)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableRemoved)
};
```

<span data-ttu-id="9119a-167">이러한 대리자는 시스템에서 손 메시를 포함 하 여 추적 가능 개체를 검색할 때 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-167">These delegates are called when the system detects any trackable object, including a hand mesh.</span></span> 
```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```
<span data-ttu-id="9119a-168">대리자에 대 한 처리기의 시그니처는 다음과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-168">Handlers to the delegates should have the following signature:</span></span>
```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

<span data-ttu-id="9119a-169">메시 데이터는 다음을 통해 액세스할 수 있습니다.`UARTrackedGeometry::GetUnderlyingMesh`</span><span class="sxs-lookup"><span data-stu-id="9119a-169">Mesh data can be accessed by `UARTrackedGeometry::GetUnderlyingMesh`</span></span>

### <a name="blueprint-api-reference"></a><span data-ttu-id="9119a-170">청사진 API 참조</span><span class="sxs-lookup"><span data-stu-id="9119a-170">Blueprint API Reference</span></span>

<span data-ttu-id="9119a-171">개발자는 청사진 행위자에 AR 추적 가능 Notify 구성 요소를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-171">Developers should add an AR Trackable Notify Component to a Blueprint actor</span></span>

![ARTrackable 알림](images/unreal/ar-trackable-notify.png)
 
<span data-ttu-id="9119a-173">그런 다음 구성 요소의 세부 정보로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-173">Then go to the component’s details</span></span> 

![ARTrackable 알림 2](images/unreal/ar-trackable-notify2.png)
 
<span data-ttu-id="9119a-175">그리고 다음과 같은 코드를 사용 하 여 추적 된 기 하 도형 추가/업데이트/제거에서를 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-175">And overwrite On Add/Update/Remove Tracked Geometry with code like the below:</span></span>

![ARTrackable 알림](images/unreal/on-artrackable-notify.png)
 
## <a name="hand-rays"></a><span data-ttu-id="9119a-177">손 광선</span><span class="sxs-lookup"><span data-stu-id="9119a-177">Hand Rays</span></span>

<span data-ttu-id="9119a-178">개발자는 손 모양을 포인팅 장치로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-178">Developers can use a hand ray as a pointing device.</span></span> <span data-ttu-id="9119a-179">시스템은 c + + 및 청사진에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-179">The system is available in C++ and Blueprint.</span></span> <span data-ttu-id="9119a-180">기술적으로는 [SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose) 을 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-180">Technically it exposes [Windows.UI.Input.Spatial.SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose)</span></span>

<span data-ttu-id="9119a-181">모든 함수의 결과가 모든 프레임을 변경 하기 때문에 모든 함수를 호출할 수 있다는 것을 언급 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-181">It’s important to mention that since the results of all the functions changes every frame, they are all made callable.</span></span> <span data-ttu-id="9119a-182">Pure vs 비 순수형 또는 호출 가능 함수에 대 한 자세한 내용은 [다음을 참조 하세요.](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)</span><span class="sxs-lookup"><span data-stu-id="9119a-182">For more information about pure vs impure or callable functions, see [that](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)</span></span>

<span data-ttu-id="9119a-183">청사진의 경우 "Windows Mixed Reality HMD"를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-183">For Blueprint open “Windows Mixed Reality HMD”</span></span>

![핸드 광선 BP](images/unreal/hand-rays-bp.png)
 
<span data-ttu-id="9119a-185">C + +의 경우 "WindowsMixedRealityFunctionLibrary"를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-185">For C++ include "WindowsMixedRealityFunctionLibrary.h"</span></span>

### <a name="enum"></a><span data-ttu-id="9119a-186">열거형</span><span class="sxs-lookup"><span data-stu-id="9119a-186">Enum</span></span>

![입력 컨트롤러 단추](images/unreal/input-controller-buttons.png)
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```
* <span data-ttu-id="9119a-188">사용자가 트리거된 Select 이벤트를 **선택** 합니다 .이 이벤트는 HoloLens 2를 사용 하 여 HoloLens 2 또는 응시 및 커밋을 통해 트리거될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-188">**Select** -– User triggered Select event, which can be triggered in HoloLens 2 by airtap or gaze and commit.</span></span> <span data-ttu-id="9119a-189">이 이벤트를 트리거하는 또 다른 방법은 "Select"를 말하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-189">Another way to trigger this event is to say “Select”.</span></span> 
* <span data-ttu-id="9119a-190">**– 사용자** 가 트리거한 사용자 트리거 이벤트는 홀로그램에서 사용자의 손가락을 닫아 HoloLens 2에서 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-190">**Grasp** -– User triggered Grasp event, which is triggered in HoloLens 2 by closing the user’s fingers on a hologram.</span></span> 
```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```
* <span data-ttu-id="9119a-191">**Nottracked** – 손 모양이 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-191">**NotTracked** –- the hand isn’t visible</span></span>
* <span data-ttu-id="9119a-192">**추적** –이 손을 완전히 추적 합니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-192">**Tracked** –- the hand is fully tracked</span></span>

### <a name="struct"></a><span data-ttu-id="9119a-193">구조체</span><span class="sxs-lookup"><span data-stu-id="9119a-193">Struct</span></span>

![포인터 포즈 정보 BP](images/unreal/pointer-pose-info-bp.png)
```cpp
struct FPointerPoseInfo
{
    FVector Origin;
    FVector Direction;
    FVector Up;
    FQuat Orientation;
    EHMDTrackingStatus TrackingStatus;
};
```
* <span data-ttu-id="9119a-195">**원점** – 손 모양</span><span class="sxs-lookup"><span data-stu-id="9119a-195">**Origin** – origin of the hand</span></span>
* <span data-ttu-id="9119a-196">**방향** – 손 방향</span><span class="sxs-lookup"><span data-stu-id="9119a-196">**Direction** – direction of the hand</span></span>
* <span data-ttu-id="9119a-197">**Up** – 손 모양 벡터</span><span class="sxs-lookup"><span data-stu-id="9119a-197">**Up** – up vector of the hand</span></span>
* <span data-ttu-id="9119a-198">**방향** – 4 원수</span><span class="sxs-lookup"><span data-stu-id="9119a-198">**Orientation** – orientation quaternion</span></span> 
* <span data-ttu-id="9119a-199">**상태 추적** -현재 추적 상태</span><span class="sxs-lookup"><span data-stu-id="9119a-199">**Tracking Status** – current tracking status</span></span>

### <a name="functions"></a><span data-ttu-id="9119a-200">Functions</span><span class="sxs-lookup"><span data-stu-id="9119a-200">Functions</span></span>

<span data-ttu-id="9119a-201">연속 모니터링을 위해 모든 프레임에서 모든 함수를 호출할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-201">All the functions should be callable on every frame for continuous monitoring.</span></span> 

![포인터 포즈 정보 가져오기](images/unreal/get-pointer-pose-info.png)
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```
<span data-ttu-id="9119a-203">함수는이 프레임에 있는 손 모양에 대 한 전체 정보를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-203">The function returns the full information about the hand ray direction in this frame.</span></span> 

![Grasped BP](images/unreal/is-grasped-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```
<span data-ttu-id="9119a-205">이 프레임에서 손을 grasped 면 true를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-205">Returns true if the hand is grasped in this frame.</span></span> 

![선택 프레스 BP](images/unreal/is-select-pressed-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```
<span data-ttu-id="9119a-207">사용자가이 프레임에서 Select를 트리거한 경우 true를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-207">Returns true if the user triggered Select in this frame.</span></span>

![단추 클릭을 클릭 합니다.](images/unreal/is-button-clicked-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```
<span data-ttu-id="9119a-209">이 프레임에서 이벤트/단추가 트리거되는 경우 true를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-209">Returns true if the event/button is triggered in this frame.</span></span>

![컨트롤러 추적 상태 BP 가져오기](images/unreal/get-controller-tracking-status-bp.png)
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```
<span data-ttu-id="9119a-211">이 프레임에서 추적 상태를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-211">Returns the tracking status in this frame.</span></span>

## <a name="gestures"></a><span data-ttu-id="9119a-212">제스처</span><span class="sxs-lookup"><span data-stu-id="9119a-212">Gestures</span></span>

<span data-ttu-id="9119a-213">Hololens 2는 공간 제스처를 추적할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-213">The Hololens 2 can track spatial gestures.</span></span> <span data-ttu-id="9119a-214">이러한 제스처에 대 한 자세한 내용은 [개발자가 혼합](https://docs.microsoft.com/hololens/hololens2-basic-usage) 현실 응용 프로그램에 대 한 입력으로 캡처할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-214">Details about these gestures are [here](https://docs.microsoft.com/hololens/hololens2-basic-usage) A developer can capture them as input to their mixed reality application.</span></span> 

<span data-ttu-id="9119a-215">C + + 함수는 "WindowsMixedRealitySpatialInputFunctionLibrary"입니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-215">The C++ function is in "WindowsMixedRealitySpatialInputFunctionLibrary.h"</span></span>

<span data-ttu-id="9119a-216">청사진 함수는 Windows Mixed Reality 공간 입력에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-216">The Blueprint function is in Windows Mixed Reality Spatial Input</span></span>

![캡처 제스처](images/unreal/capture-gestures.png)

### <a name="enum"></a><span data-ttu-id="9119a-218">열거형</span><span class="sxs-lookup"><span data-stu-id="9119a-218">Enum</span></span>

![제스처 형식](images/unreal/gesture-type.png)
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```
<span data-ttu-id="9119a-220">이 열거형은 공간 축 제스처를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-220">This enum describes spatial axis gestures.</span></span> <span data-ttu-id="9119a-221">[여기](holograms-211.md) 에서 자세한 내용을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-221">You can read about them [here](holograms-211.md)</span></span>

### <a name="function"></a><span data-ttu-id="9119a-222">기능</span><span class="sxs-lookup"><span data-stu-id="9119a-222">Function</span></span>

![제스처 BP 캡처](images/unreal/capture-gestures-bp.png)
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false, 
    bool Hold = false, 
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None, 
    bool NavigationAxisX = true, 
    bool NavigationAxisY = true, 
    bool NavigationAxisZ = true);
```
<span data-ttu-id="9119a-224">함수는 제스처의 캡처를 사용 하거나 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-224">The function enables and disables capturing of gestures.</span></span> <span data-ttu-id="9119a-225">사용 되는 제스처는 입력 이벤트를 발생 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-225">The enabled gestures fire input events.</span></span> <span data-ttu-id="9119a-226">제스처 캡처를 사용 하도록 설정 하면 true를 반환 하 고 오류가 발생 하면 false를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-226">It returns true if enabling gesture capture succeeded and false if there's an error.</span></span>
<span data-ttu-id="9119a-227">주요 이벤트</span><span class="sxs-lookup"><span data-stu-id="9119a-227">Key Events</span></span>

![주요 이벤트](images/unreal/key-events.png)

![주요 이벤트 2](images/unreal/key-events2.png)
```cpp
const FKey FSpatialInputKeys::TapGesture(TapGestureName);
const FKey FSpatialInputKeys::DoubleTapGesture(DoubleTapGestureName);
const FKey FSpatialInputKeys::HoldGesture(HoldGestureName);

const FKey FSpatialInputKeys::LeftTapGesture(LeftTapGestureName);
const FKey FSpatialInputKeys::LeftDoubleTapGesture(LeftDoubleTapGestureName);
const FKey FSpatialInputKeys::LeftHoldGesture(LeftHoldGestureName);

const FKey FSpatialInputKeys::RightTapGesture(RightTapGestureName);
const FKey FSpatialInputKeys::RightDoubleTapGesture(RightDoubleTapGestureName);
const FKey FSpatialInputKeys::RightHoldGesture(RightHoldGestureName);

const FKey FSpatialInputKeys::LeftManipulationGesture(LeftManipulationGestureName);
const FKey FSpatialInputKeys::LeftManipulationXGesture(LeftManipulationXGestureName);
const FKey FSpatialInputKeys::LeftManipulationYGesture(LeftManipulationYGestureName);
const FKey FSpatialInputKeys::LeftManipulationZGesture(LeftManipulationZGestureName);

const FKey FSpatialInputKeys::LeftNavigationGesture(LeftNavigationGestureName);
const FKey FSpatialInputKeys::LeftNavigationXGesture(LeftNavigationXGestureName);
const FKey FSpatialInputKeys::LeftNavigationYGesture(LeftNavigationYGestureName);
const FKey FSpatialInputKeys::LeftNavigationZGesture(LeftNavigationZGestureName);


const FKey FSpatialInputKeys::RightManipulationGesture(RightManipulationGestureName);
const FKey FSpatialInputKeys::RightManipulationXGesture(RightManipulationXGestureName);
const FKey FSpatialInputKeys::RightManipulationYGesture(RightManipulationYGestureName);
const FKey FSpatialInputKeys::RightManipulationZGesture(RightManipulationZGestureName);

const FKey FSpatialInputKeys::RightNavigationGesture(RightNavigationGestureName);
const FKey FSpatialInputKeys::RightNavigationXGesture(RightNavigationXGestureName);
const FKey FSpatialInputKeys::RightNavigationYGesture(RightNavigationYGestureName);
const FKey FSpatialInputKeys::RightNavigationZGesture(RightNavigationZGestureName);
```
<span data-ttu-id="9119a-230">제스처를 사용 하는 경우 이벤트가 발생 하기 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="9119a-230">If the gesture is enabled, the events begin firing.</span></span> 

