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
# <a name="hand-tracking"></a>수동 추적

손으로 추적 시스템은 사용자의 palms를 사용 하 여 실수에 대 한 입력으로 손가락을 사용 합니다. 개발자는 모든 손가락의 위치와 회전, 전체 palm 및 자체 코드에서 사용할 제스처를 가져올 수 있습니다. 

## <a name="hand-pose"></a>직접 포즈

개발자는 직접 포즈를 사용 하 여 활성 사용자의 손으로와 손가락을 입력으로 추적할 수 있습니다. 이 시스템은 청사진과 c + +를 통해 노출 됩니다. 기술 세부 정보는 해당 하는 WinRT 클래스 [창](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) 에 있습니다 .이 UNREAL API는 unreal의 좌표계 형식으로 데이터를 제공 하 고 틱은 Unreal 엔진과 전환은 합니다.

### <a name="enum"></a>열거형

EWMRHandKeypoint는 손 모양의 뼈 계층 구조를 설명 합니다. 

청사진

![핸드 Keypoint BP](images/unreal/hand-keypoint-bp.png)
 
C++:
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

숫자 값은 [HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) 테이블에서 찾을 수 있습니다.
 
### <a name="functions"></a>Functions

청사진에서 직접 추적 함수를 사용 하려면 "핸드 추적/Windows Mixed Reality"를 엽니다.

![수동 추적 BP](images/unreal/hand-tracking-bp.png)

C + + 함수에는 "WindowsMixedRealityHandTrackingFunctionLibrary"를 포함 합니다.

BP

![수동 추적 BP 지원](images/unreal/supports-hand-tracking-bp.png)
 
C++:
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

장치에서 직접 추적이 지원 되 면 true를 반환 하 고, 수동 추적을 사용할 수 없으면 false를 반환 합니다.

BP

![핸드 조인트 변환 가져오기](images/unreal/get-hand-joint-transform.png)
 
C++:
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

이 함수는 손 모양의 공간 데이터를 반환 합니다. 데이터는 프레임 내에서 반환 된 값이 캐시 되는 모든 프레임을 업데이트 합니다. 성능상의 이유로이 함수에는 높은 논리를 포함 하지 않는 것이 좋습니다. 

* 사용자를 **위해 왼쪽 또는** 오른쪽 일 수 있습니다.
* **Keypoint** – 바늘의 뼈입니다. 
* **변환** – 뼈의 기본 좌표와 방향입니다. 뼈의 끝에 대 한 변환 데이터를 가져오려면 다음 뼈의 밑수를 요청 해야 합니다. 특수 팁 뼈는 distal의 끝을 제공 합니다. 
* **Radius** -뼈 밑의 반경입니다.
* **반환 값** -뼈가이 프레임을 추적 하면 true이 고, 뼈가 추적 되지 않으면 false입니다.

## <a name="hand-live-link-animation"></a>손 모양 링크 애니메이션
손 포즈는 라이브 링크 플러그 인을 사용 하 여 애니메이션에 노출 됩니다. 플러그 인 설명서는 [여기](https://docs.unrealengine.com/en-US/Engine/Animation/LiveLinkPlugin/index.html) 에 있습니다.

Windows Mixed Reality 및 라이브 링크 플러그 인을 사용 하는 경우 **창 > 라이브 링크로** 이동 하 여 라이브 링크 편집기 창을 엽니다. **+ 소스 단추** 를 클릭 하 고 Windows Mixed Reality 추적 소스를 사용 하도록 설정 합니다.

![라이브 링크 소스](images/unreal/live-link-source.png)
 
소스를 사용 하도록 설정 하 고 애니메이션 자산을 연 후 애니메이션의 장면 미리 보기 탭에는 다음과 같은 추가 옵션이 포함 됩니다. (플러그 인이 베타에 있으므로 해당 프로세스는 나중에 변경 될 수 있습니다.)

![라이브 링크 애니메이션](images/unreal/live-link-animation.png)
 
손 모양 애니메이션 계층은 EWMRHandKeypoint에서와 동일 합니다. WindowsMixedRealityHandTrackingLiveLinkRemapAsset를 사용 하 여 애니메이션의 대상을 지정할 수 있습니다. 

![라이브 링크 애니메이션 2](images/unreal/live-link-animation2.png)
 
편집기에서 서브클래싱 할 수 있습니다.

![라이브 링크 다시 매핑](images/unreal/live-link-remap.png)
 
## <a name="hand-mesh"></a>손 모양 메시
사용자 손을 나타내는 메시입니다. 

![손 모양 메시](images/unreal/hand-mesh.png)
 
### <a name="how-to-enable-and-configure"></a>설정 및 구성 방법

개발자는 직접 메시에 직접 액세스 하 여 자신만의 용도를 얻을 수 있습니다. 이 액세스는 ARSessionConfig: AR 설정-> 세계 매핑-> 추적 된 기 하 도형에서 메시 데이터를 생성 하는 것으로 설정 해야 합니다. 

메시의 기본 매개 변수는 다음과 같습니다.

1.  폐색에 대 한 메시 데이터 사용
2.  메시 데이터의 충돌 생성
3.  메시 데이터의 Nav 메시 생성
4.  와이어 프레임으로 메시 데이터 렌더링 – 생성 된 메시를 표시 하는 디버그 매개 변수

혼합 현실 프로젝트의 경우 이러한 매개 변수 값은 공간 매핑 메시 및 손 모양 메시 기본값으로 사용 됩니다. 개발자는 특정 메시에 대해 BP 또는 코드에서이를 변경할 수 있습니다.

### <a name="c-api-reference"></a>C + + API 참조 
```cpp
enum class EARObjectClassification : uint8
{
// other types 
    HandMesh,
};
```

이 값은 모든 추적 가능 개체 간의 손 메시입니다.

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

이러한 대리자는 시스템에서 손 메시를 포함 하 여 추적 가능 개체를 검색할 때 호출 됩니다. 
```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```
대리자에 대 한 처리기의 시그니처는 다음과 같아야 합니다.
```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

메시 데이터는 다음을 통해 액세스할 수 있습니다.`UARTrackedGeometry::GetUnderlyingMesh`

### <a name="blueprint-api-reference"></a>청사진 API 참조

개발자는 청사진 행위자에 AR 추적 가능 Notify 구성 요소를 추가 해야 합니다.

![ARTrackable 알림](images/unreal/ar-trackable-notify.png)
 
그런 다음 구성 요소의 세부 정보로 이동 합니다. 

![ARTrackable 알림 2](images/unreal/ar-trackable-notify2.png)
 
그리고 다음과 같은 코드를 사용 하 여 추적 된 기 하 도형 추가/업데이트/제거에서를 덮어씁니다.

![ARTrackable 알림](images/unreal/on-artrackable-notify.png)
 
## <a name="hand-rays"></a>손 광선

개발자는 손 모양을 포인팅 장치로 사용할 수 있습니다. 시스템은 c + + 및 청사진에서 사용할 수 있습니다. 기술적으로는 [SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose) 을 노출 합니다.

모든 함수의 결과가 모든 프레임을 변경 하기 때문에 모든 함수를 호출할 수 있다는 것을 언급 하는 것이 중요 합니다. Pure vs 비 순수형 또는 호출 가능 함수에 대 한 자세한 내용은 [다음을 참조 하세요.](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)

청사진의 경우 "Windows Mixed Reality HMD"를 엽니다.

![핸드 광선 BP](images/unreal/hand-rays-bp.png)
 
C + +의 경우 "WindowsMixedRealityFunctionLibrary"를 포함 합니다.

### <a name="enum"></a>열거형

![입력 컨트롤러 단추](images/unreal/input-controller-buttons.png)
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```
* 사용자가 트리거된 Select 이벤트를 **선택** 합니다 .이 이벤트는 HoloLens 2를 사용 하 여 HoloLens 2 또는 응시 및 커밋을 통해 트리거될 수 있습니다. 이 이벤트를 트리거하는 또 다른 방법은 "Select"를 말하는 것입니다. 
* **– 사용자** 가 트리거한 사용자 트리거 이벤트는 홀로그램에서 사용자의 손가락을 닫아 HoloLens 2에서 트리거됩니다. 
```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```
* **Nottracked** – 손 모양이 표시 되지 않습니다.
* **추적** –이 손을 완전히 추적 합니다.

### <a name="struct"></a>구조체

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
* **원점** – 손 모양
* **방향** – 손 방향
* **Up** – 손 모양 벡터
* **방향** – 4 원수 
* **상태 추적** -현재 추적 상태

### <a name="functions"></a>Functions

연속 모니터링을 위해 모든 프레임에서 모든 함수를 호출할 수 있어야 합니다. 

![포인터 포즈 정보 가져오기](images/unreal/get-pointer-pose-info.png)
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```
함수는이 프레임에 있는 손 모양에 대 한 전체 정보를 반환 합니다. 

![Grasped BP](images/unreal/is-grasped-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```
이 프레임에서 손을 grasped 면 true를 반환 합니다. 

![선택 프레스 BP](images/unreal/is-select-pressed-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```
사용자가이 프레임에서 Select를 트리거한 경우 true를 반환 합니다.

![단추 클릭을 클릭 합니다.](images/unreal/is-button-clicked-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```
이 프레임에서 이벤트/단추가 트리거되는 경우 true를 반환 합니다.

![컨트롤러 추적 상태 BP 가져오기](images/unreal/get-controller-tracking-status-bp.png)
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```
이 프레임에서 추적 상태를 반환 합니다.

## <a name="gestures"></a>제스처

Hololens 2는 공간 제스처를 추적할 수 있습니다. 이러한 제스처에 대 한 자세한 내용은 [개발자가 혼합](https://docs.microsoft.com/hololens/hololens2-basic-usage) 현실 응용 프로그램에 대 한 입력으로 캡처할 수 있습니다. 

C + + 함수는 "WindowsMixedRealitySpatialInputFunctionLibrary"입니다.

청사진 함수는 Windows Mixed Reality 공간 입력에 있습니다.

![캡처 제스처](images/unreal/capture-gestures.png)

### <a name="enum"></a>열거형

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
이 열거형은 공간 축 제스처를 설명 합니다. [여기](holograms-211.md) 에서 자세한 내용을 확인할 수 있습니다.

### <a name="function"></a>기능

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
함수는 제스처의 캡처를 사용 하거나 사용 하지 않도록 설정 합니다. 사용 되는 제스처는 입력 이벤트를 발생 시킵니다. 제스처 캡처를 사용 하도록 설정 하면 true를 반환 하 고 오류가 발생 하면 false를 반환 합니다.
주요 이벤트

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
제스처를 사용 하는 경우 이벤트가 발생 하기 시작 합니다. 

