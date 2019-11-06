---
title: DirectX의 손 및 동작 컨트롤러
description: 기본 DirectX 앱에서 직접 추적 및 동작 컨트롤러를 사용 하기 위한 개발자 가이드입니다.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/30/2019
ms.topic: article
keywords: 손, 모션 컨트롤러, directx, 입력, holograms
ms.openlocfilehash: 7b8222e5e539eb95b07cc24d6b49106bd174b490
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435201"
---
# <a name="hands-and-motion-controllers-in-directx"></a>DirectX의 손 및 동작 컨트롤러

Windows Mixed Reality에서 직접 및 [동작 컨트롤러](motion-controllers.md) 입력은 모두 [windows.](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial) ui&gt; 네임 스페이스에 있는 공간 입력 api를 통해 처리 됩니다. 이를 통해 바늘 및 모션 컨트롤러에서 같은 방식으로 **Select** 와 같은 일반적인 동작을 쉽게 처리할 수 있습니다.

## <a name="getting-started"></a>시작

Windows Mixed Reality의 공간 입력에 액세스 하려면 SpatialInteractionManager 인터페이스부터 시작 합니다.  일반적으로 앱을 시작 하는 동안 [SpatialInteractionManager:: GetForCurrentView](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getforcurrentview)를 호출 하 여이 인터페이스에 액세스할 수 있습니다.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

SpatialInteractionManager interactionManager = SpatialInteractionManager::GetForCurrentView();
```

SpatialInteractionManager의 작업은 입력의 원본을 나타내는 [SpatialInteractionSources](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource)에 대 한 액세스를 제공 하는 것입니다.  시스템에서 사용할 수 있는 SpatialInteractionSources에는 세 가지 종류가 있습니다.
* 사용자의 검색 된 **손을 나타냅니다.** 손으로는 HoloLens의 기본 제스처에서 HoloLens 2의 전체에 대 한 직접 추적에 이르는 장치에 따라 다양 한 기능을 제공 합니다. 
* **컨트롤러** 는 페어링된 동작 컨트롤러를 나타냅니다. 동작 컨트롤러는 다양 한 기능을 제공할 수 있습니다.  예: 트리거, 메뉴 단추, 클릭 단추, 터치 패드 및 thumbsticks를 선택 합니다.
* **음성** 은 사용자의 음성 인식 시스템 검색 키워드를 나타냅니다. 예를 들어이 소스는 사용자가 "선택" 이라고 표시 될 때마다 Select 누르기 및 릴리스를 삽입 합니다.

원본에 대 한 프레임당 데이터는 [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) 인터페이스로 표시 됩니다. 응용 프로그램에서 이벤트 기반 또는 폴링 기반 모델을 사용 하는지 여부에 따라이 데이터에 액세스 하는 두 가지 방법이 있습니다.

### <a name="event-driven-input"></a>이벤트 기반 입력
SpatialInteractionManager는 앱이 수신할 수 있는 많은 이벤트를 제공 합니다.  [Sourcepressed](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed), [SourceReleased](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) 및 [sourcepressed](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated)를 예로 들 수가 있습니다.

예를 들어 다음 코드는 MyApp:: OnSourcePressed 이벤트 처리기를 Source눌린 이벤트로 후크합니다.  이를 통해 앱은 모든 유형의 상호 작용 소스에서 누름을 검색할 수 있습니다.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
interactionManager.SourcePressed({ this, &MyApp::OnSourcePressed });

```

이 누름 이벤트는 키가 발생 했을 때 해당 SpatialInteractionSourceState 함께 비동기적으로 앱에 전송 됩니다. 앱 또는 게임 엔진에서 일부 처리를 즉시 수행 하거나 입력 처리 루틴에서 이벤트 데이터를 큐에 대기 시킬 수 있습니다. 다음은 선택 단추가 눌러져 있는지 여부를 확인 하는 방법을 보여 주는 SourcePressed 이벤트에 대 한 이벤트 처리기 함수입니다.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

void MyApp::OnSourcePressed(SpatialInteractionManager const& sender, SpatialInteractionSourceEventArgs const& args)
{
    if (args.PressKind() == SpatialInteractionPressKind::Select)
    {
        // Select button was pressed, update app state
    }
}
```

위의 코드는 장치의 기본 작업에 해당 하는 ' Select ' 누르기만 확인 합니다. 예를 들어 HoloLens를 이동 하거나 동작 컨트롤러에서 트리거를 당겨 이동 합니다.  ' Select ' 누름은 대상으로 하는 홀로그램을 활성화 하는 사용자의 의도를 나타냅니다.  SourcePressed 이벤트는 다양 한 단추 및 제스처에 대해 발생 하며, SpatialInteractionSource의 다른 속성을 검사 하 여 해당 사례를 테스트할 수 있습니다.

### <a name="polling-based-input"></a>폴링 기반 입력
또한 SpatialInteractionManager를 사용 하 여 모든 프레임의 현재 상태를 폴링할 수 있습니다.  이렇게 하려면 [GetDetectedSourcesAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) 모든 프레임을 호출 하면 됩니다.  이 함수는 모든 활성 [SpatialInteractionSource](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource)에 대해 하나의 [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) 를 포함 하는 배열을 반환 합니다. 즉, 각 활성 동작 컨트롤러에 대해 하나씩, 추적 된 각 항목에 대해 하나씩, ' select ' 명령이 최근에 재생 된 경우 음성을 위한 하나를 의미 합니다. 그런 다음 각 SpatialInteractionSourceState의 속성을 검사 하 여 입력을 응용 프로그램에 추가할 수 있습니다. 

다음은 폴링 방법을 사용 하 여 ' select ' 작업을 확인 하는 방법의 예입니다. *예측* 변수는 [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe)에서 가져올 수 있는 [HolographicFramePrediction](https://docs.microsoft.com//uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) 개체를 나타냅니다.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
auto sourceStates = m_spatialInteractionManager.GetDetectedSourcesAtTimestamp(prediction.Timestamp());

for (auto& sourceState : sourceStates)
{
    if (sourceState.IsSelectPressed())
    {
        // Select button is down, update app state
    }
}
```

각 SpatialInteractionSource에는 새 원본을 식별 하 고 기존 소스와 프레임 간에 상관 관계를 지정 하는 데 사용할 수 있는 ID가 있습니다.  시계를 떠날 때마다 새 ID가 할당 되 고, 컨트롤러 Id는 세션 기간 동안 정적 상태로 유지 됩니다.  [Sourcedetected](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcedetected)와 [SourceLost](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcelost)같은 SpatialInteractionManager의 이벤트를 사용 하 여 장치 보기를 시작 하거나 떠날 때 또는 동작 컨트롤러를 설정/해제 하거나 페어링된 경우에 반응할 수 있습니다.

### <a name="predicted-vs-historical-poses"></a>예측 및 기록 포즈
GetDetectedSourcesAtTimestamp에 timestamp 매개 변수가 있습니다. 이를 통해 예측 또는 기록 되는 상태 및 포즈 데이터를 요청 하 여 다른 입력 소스와 공간 상호 작용의 상관 관계를 지정할 수 있습니다. 예를 들어 현재 프레임에서 손으로의 위치를 렌더링할 때 [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe)에서 제공 하는 예측 타임 스탬프를 전달할 수 있습니다. 이를 통해 시스템은 렌더링 된 프레임 출력과 긴밀 하 게 일치 하는 손 위치를 전달 하 여 인식 대기 시간을 최소화 합니다.

그러나 이러한 예측 된 포즈는 상호 작용 소스를 대상으로 지정 하기 위한 이상적인 포인팅 광선을 생성 하지 않습니다. 예를 들어 동작 컨트롤러 단추를 누르면 해당 이벤트가 Bluetooth를 통해 운영 체제에 20ms 최대의 시간이 걸릴 수 있습니다. 마찬가지로 사용자가 손 제스처를 수행한 후에는 시스템이 제스처를 검색 한 후 앱에서 해당 제스처를 폴링하기 전에 몇 시간이 경과할 수 있습니다. 앱이 상태 변경에 대해 폴링하는 시간에 따라 이전에 실제로 발생 한 상호 작용을 대상으로 하는 데 사용 되는 헤드와 손을 사용 합니다. 현재 HolographicFrame의 타임 스탬프를 GetDetectedSourcesAtTimestamp에 전달 하 여 대상으로 지정 하는 경우에는 프레임이 표시 될 때이를 대상 광선으로 예측 하 게 됩니다 .이는 나중에 20ms 이상일 수 있습니다. 이 향후 포즈는 상호 작용 원본을 *렌더링* 하는 데 유용 하지만 과거에 사용자의 대상 지정이 복합어 상호 작용을 *대상으로 지정* 하는 데 시간 문제가 발생 합니다.

다행히 [Sourcepressed](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed), [SourceReleased](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) 및 [sourcepressed](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated) 이벤트는 각 입력 이벤트와 연결 된 기록 [상태](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) 를 제공 합니다.  여기에는이 이벤트와 상관 관계를 위해 다른 Api에 전달할 수 있는 기록 [타임 스탬프](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.timestamp) 와 함께 [TryGetPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)를 통해 사용할 수 있는 기록 헤드 및 직접 포즈가 포함 됩니다.

그러면 각 프레임 및 컨트롤러를 사용 하 여 렌더링 하 고 대상을 지정할 때 다음과 같은 모범 사례가 발생 합니다.
* 각 프레임의 **수동/컨트롤러 렌더링** 의 경우 앱은 현재 프레임의 photon 시간에 각 상호 작용 소스의 **앞으로 예측** 된 포즈를 **폴링합니다** .  [HolographicFrame:: CurrentPrediction](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.currentprediction)제공 하는 예측 타임 스탬프를 전달 하 여 각 프레임 [GetDetectedSourcesAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) 를 호출 하 여 모든 상호 작용 소스에 대해 폴링할 수 있습니다.
* 보도 나 릴리스를 대상으로 하는 **직접/컨트롤러를 대상** 으로 하는 경우 앱은 해당 이벤트에 대 한 **기록** 헤드 또는 핸드 포즈를 기반으로 하는 raycasting 나 눌린/릴리스 **이벤트**를 처리 해야 합니다. [Sourcepressed](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed) 또는 [SourceReleased](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) 이벤트를 처리 하 고, 이벤트 인수에서 [State](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) 속성을 가져온 다음, [TryGetPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) 메서드를 호출 하 여이 대상 광선을 가져옵니다.

## <a name="cross-device-input-properties"></a>장치 간 입력 속성
SpatialInteractionSource API는 다양 한 기능을 갖춘 컨트롤러 및 핸드 추적 시스템을 지원 합니다. 이러한 기능 중 몇 가지는 장치 유형 간에 공통적으로 제공 됩니다. 예를 들어 직접 추적 및 동작 컨트롤러는 모두 ' select ' 작업과 3D 위치를 제공 합니다. 가능 하면 API는 이러한 일반적인 기능을 SpatialInteractionSource의 동일한 속성에 매핑합니다.  이를 통해 응용 프로그램은 다양 한 입력 형식을 보다 쉽게 지원할 수 있습니다. 다음 표에서는 지원 되는 속성과 이러한 속성이 입력 형식에서 비교 되는 방식을 설명 합니다.

| 속성 | 설명 | HoloLens 제스처 | 동작 컨트롤러 | 트레일러 식|
|--- |--- |--- |--- |--- |
| [SpatialInteractionSource::**손**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource.handedness) | 오른쪽 또는 왼쪽/컨트롤러입니다. | 지원되지 않음 | 지원함 | 지원함 |
| [SpatialInteractionSourceState::**Isselectpressed**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isselectpressed) | 기본 단추의 현재 상태입니다. | 공기 탭 | 트리거 | 완화 공기 탭 (수직으로) |
| [SpatialInteractionSourceState::**IsGrasped**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isgrasped) | 잡기 단추의 현재 상태입니다. | 지원되지 않음 | 잡기 단추 | 손가락으로 나 폐쇄 |
| [SpatialInteractionSourceState::**IsMenuPressed**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.ismenupressed) | 메뉴 단추의 현재 상태입니다.    | 지원되지 않음 | 메뉴 단추 | 지원되지 않음 |
| [SpatialInteractionSourceLocation::**Position**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.position) | 컨트롤러에서 손 모양 또는 그립 위치의 XYZ 위치입니다. | 팜 위치 | 그립 포즈 위치 | 팜 위치 |
| [SpatialInteractionSourceLocation::**Orientation**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.orientation) | 컨트롤러에서 손 방향 또는 그립 포즈를 나타내는 4 원수입니다. | 지원되지 않음 | 그립 포즈 방향 | 팜 방향 |
| [SpatialPointerInteractionSourcePose::**Position**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.position#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_Position) | 포인팅 광선의 원점입니다. | 지원되지 않음 | 지원함 | 지원함 |
| [SpatialPointerInteractionSourcePose::**Forwarddirection**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.forwarddirection#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_ForwardDirection) | 포인팅 광선의 방향입니다. | 지원되지 않음 | 지원함 | 지원함 |

일부 속성은 일부 장치에서 사용할 수 없으며 API는이에 대 한 테스트 수단을 제공 합니다. 예를 들어 [SpatialInteractionSource:: Isgrsupported](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource.isgraspsupported) 속성을 검사 하 여 원본에서 판단 동작을 제공 하는지 여부를 확인할 수 있습니다.

### <a name="grip-pose-vs-pointing-pose"></a>그립 포즈 및 포인팅 포즈

Windows Mixed Reality는 다양 한 폼 팩터에서 동작 컨트롤러를 지원 합니다.  또한 트레일러 식 추적 시스템도 지원 합니다.  이러한 모든 시스템에는 앱이 사용자 손으로 개체를 가리키거나 렌더링 하는 데 사용 해야 하는 손 위치와 자연 스러운 "전달" 방향 간에 서로 다른 관계가 있습니다.  이를 모두 지원 하기 위해 직접 추적 및 동작 컨트롤러 모두에 두 가지 유형의 3D 포즈를 제공 합니다.  첫 번째는 그립 포즈 이며 사용자의 손 위치를 나타냅니다.  두 번째는 사용자의 손 또는 컨트롤러에서 시작 하는 광선을 나타내는 포즈를 가리킵니다. 따라서 사용자의 손을 또는 소드와 같은 **사용자의 손으로 저장 된 개체** **를 렌더링 하려면** 그립 포즈를 사용 합니다. 예를 들어 사용자가 **UI를 가리키고** 있는 경우와 같이 컨트롤러에서 raycast를 사용 하려는 경우 포인팅 포즈를 사용 합니다.

[SpatialInteractionSourceState::P roperties:: TryGetLocation (...)](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties.trygetlocation#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_)을 통해 **그립 포즈** 에 액세스할 수 있습니다.  다음과 같이 정의 됩니다.
* **그립 위치**: 컨트롤러를 자연스럽 게 유지 하는 경우 왼쪽 또는 오른쪽으로 조정 하 여 그립 내 위치를 가운데에 맞춥니다.
* **그립 방향 오른쪽 축**: 손 모양 5 손가락 포즈를 형성 하는 손을 완전히 열 때 palm (왼쪽 야자나무에서 오른쪽으로 뒤로)의 광선을 만듭니다.
* **그립 방향 전방 축: 핸들**을 부분적으로 (컨트롤러를 보유 하는 것 처럼) 닫는 경우 비 엄지 손가락으로 형성 된 튜브를 통해 "전달" 하는 광선이 표시 됩니다.
* **그립 방향 up 축**: 오른쪽 및 전방 정의에 의해 암시 된 위쪽 축입니다.

[SpatialInteractionSourceState::P roperties:: TryGetLocation (...):: SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose) 또는 [SpatialInteractionSourceState:: TryGetPointerPose (...):: TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_) 를 통해 **포인터 포즈** 에 액세스할 수 있습니다. .

## <a name="controller-specific-input-properties"></a>컨트롤러 특정 입력 속성
컨트롤러의 경우 SpatialInteractionSource에는 추가 기능이 있는 컨트롤러 속성이 있습니다.
* **Hasthumbstick 스틱:** True 이면 컨트롤러에 엄지 스틱이 있습니다. SpatialInteractionSourceState의 [Controllerproperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) 속성을 검사 하 여 엄지 스틱 x 및 y 값 (ThumbstickX 및 ThumbstickY) 뿐만 아니라 눌린 상태 (IsThumbstickPressed)를 가져옵니다.
* **HasTouchpad:** True 이면 컨트롤러에 터치 패드가 있습니다. SpatialInteractionSourceState의 ControllerProperties 속성을 검사 하 여 터치 패드 x 및 y 값 (TouchpadX 및 TouchpadY)을 획득 하 고 사용자가 pad (IsTouchpadTouched)와 터치 하 고 있는지 여부를 확인 합니다 ( IsTouchpadPressed).
* **SimpleHapticsController:** 컨트롤러에 대 한 SimpleHapticsController API를 사용 하면 컨트롤러의 haptics 기능을 검사 하 고 햅 피드백을 제어할 수도 있습니다.

터치 패드 및 엄지 스틱의 범위는 양쪽 축 (아래쪽에서 위쪽, 왼쪽에서 오른쪽)에 대해-1에서 1 사이입니다. SpatialInteractionSourceState:: Select보도 Sedvalue 속성을 사용 하 여 액세스 되는 아날로그 트리거의 범위는 0에서 1 사이입니다. 값 1은 IsSelectPressed이 true가 되는 것과 관련이 있습니다. 다른 모든 값은 false와 동일 합니다.

## <a name="articulated-hand-tracking"></a>트레일러 식 추적
Windows Mixed Reality API는 HoloLens 2와 같이 트레일러 식 추적을 완벽 하 게 지원 합니다. 트레일러 식 추적을 사용 하 여 응용 프로그램에서 직접 조작 및 지점 및 커밋 입력 모델을 구현할 수 있습니다. 이 클래스를 사용 하 여 완전 한 사용자 지정 상호 작용을 작성할 수도 있습니다.

### <a name="hand-skeleton"></a>직접 기초
트레일러 식 추적은 다양 한 유형의 상호 작용을 가능 하 게 하는 25 개의 공동 구조를 제공 합니다.  뼈대는 인덱스/중간/링/작은 손가락에 대해 5 개의 조인트, 엄지 단추에 대 한 4 개의 조인트 및 1 개의 손목 조인트를 제공 합니다.  손목 조인트는 계층의 기반으로 사용 됩니다. 다음 그림은 해골의 레이아웃을 보여 줍니다.

![직접 기초](images/hand-skeleton.png)

대부분의 경우 각 조인트는 나타내는 뼈에 따라 이름이 지정 됩니다.  모든 조인트에는 두 개의 뼈가 있기 때문에 해당 위치에서 자식 뼈를 기준으로 각 조인트의 이름을 지정 하는 규칙을 사용 합니다.  자식 뼈는 손목의 뼈로 정의 됩니다.  예를 들어 "Index Proximal" 조인트에는 인덱스 Proximal 뼈의 시작 위치와 해당 뼈의 방향이 포함 됩니다.  뼈의 끝 위치를 포함 하지 않습니다.  이를 필요로 하는 경우 계층의 다음 조인트 인 "인덱스 중간" 조인트에서 가져옵니다.

25 개의 계층 구조 조인트 외에도 시스템은 palm 조인트를 제공 합니다.  팜은 일반적으로 골격 구조의 일부로 간주 되지 않습니다.  이는 직접 전체 위치와 방향을 가져오는 편리한 방법 으로만 제공 됩니다.

각 조인트에 대해 다음과 같은 정보가 제공 됩니다.

| 이름 | 설명 |
|--- |--- |
|위치 | 모든 요청 된 좌표계에서 사용할 수 있는 조인트의 3D 위치입니다. |
|방향 | 요청 된 좌표계에서 사용할 수 있는 뼈의 3D 방향입니다. |
|반경 | 조인트 위치에서 스킨 표면의 표면 까지의 거리입니다. 손가락 너비를 사용 하는 직접 상호 작용 또는 시각화를 조정 하는 데 유용 합니다. |
|정확도 | 시스템에서이 공동 정보를 확실 하 게 판단 하는 방법에 대 한 힌트를 제공 합니다. |

[SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)에서 함수를 통해 손 레 톤 데이터에 액세스할 수 있습니다.  함수는 [TryGetHandPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygethandpose#Windows_UI_Input_Spatial_SpatialInteractionSourceState_TryGetHandPose)라고 하며,이 함수는 [핸드 포즈](https://docs.microsoft.com//uwp/api/windows.perception.people.handpose)라는 개체를 반환 합니다.  원본에서 트레일러를 지원 하지 않는 경우이 함수는 null을 반환 합니다.  수동 포즈를 사용 하는 경우 관심 있는 조인트의 이름으로 [TryGetJoint](https://docs.microsoft.com//uwp/api/windows.perception.people.handpose.trygetjoint#Windows_Perception_People_HandPose_TryGetJoint_Windows_Perception_Spatial_SpatialCoordinateSystem_Windows_Perception_People_HandJointKind_Windows_Perception_People_JointPose__)를 호출 하 여 현재 공동 데이터를 가져올 수 있습니다.  데이터는 [JointPose](https://docs.microsoft.com//uwp/api/windows.perception.people.jointpose) 구조체로 반환 됩니다.  다음 코드는 인덱스 손가락 팁의 위치를 가져옵니다. *CurrentState* 변수는 [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)의 인스턴스를 나타냅니다.

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::Foundation::Numerics;

auto handPose = currentState.TryGetHandPose();
if (handPose)
{
    JointPose joint;
    if (handPose.TryGetJoint(desiredCoordinateSystem, HandJointKind::IndexTip, joint))
    {
        float3 indexTipPosition = joint.Position;

        // Do something with the index tip position
    }
}
```

### <a name="hand-mesh"></a>손 모양 메시

트레일러 식 추적 API는 완전히 deformable 삼각형 손 모양 메시를 허용 합니다.  이 메시는 수동 구조와 함께 실시간으로 변형 될 수 있으며, 고급 물리학 기술 뿐만 아니라 시각화에도 유용 합니다.  손 메시에 액세스 하려면 먼저 [SpatialInteractionSource](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource)에서 [TryCreateHandMeshObserverAsync](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync) 를 호출 하 여 [HandMeshObserver](https://docs.microsoft.com//uwp/api/windows.perception.people.handmeshobserver) 개체를 만들어야 합니다.  일반적으로이 작업은 소스 마다 한 번만 수행 하면 됩니다. 일반적으로이 작업은 처음에 표시 됩니다.  즉,이 함수를 호출 하 여 HandMeshObserver 개체를 만듭니다.  비동기 함수 이므로 여기서는 약간의 동시성을 처리 해야 합니다.  사용 가능한 경우 [GetTriangleIndices](https://docs.microsoft.com//uwp/api/windows.perception.people.handmeshobserver.gettriangleindices#Windows_Perception_People_HandMeshObserver_GetTriangleIndices_System_UInt16___)를 호출 하 여 HandMeshObserver 개체에 삼각형 인덱스 버퍼를 요청할 수 있습니다.  인덱스는 프레임 위로 프레임을 변경 하지 않으므로 해당 항목을 한 번 가져와 소스의 수명 동안 캐시할 수 있습니다.  인덱스는 시계 방향 권선 순서로 제공 됩니다.

다음 코드는 분리 된 std:: thread를 회전 하 여 메시 관찰자를 만들고 메시 관찰자를 사용할 수 있게 되 면 인덱스 버퍼를 추출 합니다.  추적 된 손을 나타내는 [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) 인스턴스인 *currentState*라는 변수에서 시작 합니다.

```cpp
using namespace Windows::Perception::People;

std::thread createObserverThread([this, currentState]()
{
    HandMeshObserver newHandMeshObserver = currentState.Source().TryCreateHandMeshObserverAsync().get();
    if (newHandMeshObserver)
    {
        unsigned indexCount = newHandMeshObserver.TriangleIndexCount();
        vector<unsigned short> indices(indexCount);
        newHandMeshObserver.GetTriangleIndices(indices);

        // Save the indices and handMeshObserver for later use - and use a mutex to synchronize access if needed!
     }
});
createObserverThread.detach();
```
분리 된 스레드를 시작 하는 것은 비동기 호출을 처리 하는 한 가지 옵션입니다.  또는/Winrt. C++지 원하는 새로운 [co_await](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) 기능을 사용할 수 있습니다.

HandMeshObserver 개체를 만든 후에는 해당 SpatialInteractionSource 활성화 된 기간 동안 해당 개체를 유지 해야 합니다.  그런 다음, 각 프레임에서 [GetVertexStateForPose](https://docs.microsoft.com//uwp/api/windows.perception.people.handmeshobserver.getvertexstateforpose) 를 호출 하 고 꼭 짓 점을 나타내는 [핸드](https://docs.microsoft.com//uwp/api/windows.perception.people.handpose) 포즈 인스턴스를 전달 하 여 손을 나타내는 최신 꼭 짓 점 버퍼에 대해 요청할 수 있습니다.  버퍼의 각 꼭 짓 점은 위치 및 법선입니다.  다음은 손 메시의 현재 꼭 짓 점 집합을 가져오는 방법의 예입니다.  이전과 마찬가지로 *currentState* 변수는 [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)의 인스턴스를 나타냅니다.

```cpp
using namespace winrt::Windows::Perception::People;

auto handPose = currentState.TryGetHandPose();
if (handPose)
{
    std::vector<HandMeshVertex> vertices(handMeshObserver.VertexCount());
    auto vertexState = handMeshObserver.GetVertexStateForPose(handPose);
    vertexState.GetVertices(vertices);

    auto meshTransform = vertexState.CoordinateSystem().TryGetTransformTo(desiredCoordinateSystem);
    if (meshTransform != nullptr)
    {
        // Do something with the vertices and mesh transform, along with the indices that you saved earlier
    }
}
```

기본 조인트와는 달리, 손 모양 메시 API를 사용 하 여 꼭 짓 점의 좌표계를 지정할 수 없습니다.  대신 [HandMeshVertexState](https://docs.microsoft.com//uwp/api/windows.perception.people.handmeshvertexstate) 는 꼭 짓 점이 제공 되는 좌표계를 지정 합니다.  그런 다음 [TryGetTransformTo](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem.trygettransformto#Windows_Perception_Spatial_SpatialCoordinateSystem_TryGetTransformTo_Windows_Perception_Spatial_SpatialCoordinateSystem_) 를 호출 하 고 원하는 좌표계를 지정 하 여 메시 변환을 가져올 수 있습니다.  꼭 짓 점을 사용할 때마다이 메시 변환을 사용 해야 합니다.  이 방법은 특히 렌더링 목적 으로만 메시를 사용 하는 경우 CPU 오버 헤드를 줄입니다.

## <a name="gaze-and-commit-composite-gestures"></a>복합 제스처 응시 및 커밋
응시 및 커밋 입력 모델을 사용 하는 응용 프로그램의 경우, 특히 HoloLens (첫 번째 gen)에서 공간 입력 API는 ' select ' 이벤트 위에 빌드되는 복합 제스처를 사용 하도록 설정 하는 데 사용할 수 있는 선택적 [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx) 를 제공 합니다.  SpatialInteractionManager에서 홀로그램의 SpatialGestureRecognizer에 대 한 상호 작용을 라우팅하는 방식으로 앱은 누름, 음성 및 공간 입력 장치에서 누르기, 보유, 조작 및 탐색 이벤트를 처리할 필요 없이 직접 검색할 수 있습니다. 및는 수동으로 릴리스 합니다.

SpatialGestureRecognizer은 요청 하는 제스처 집합 간에 최소한의 명확성만 수행 합니다. 예를 들어, 탭을 요청 하는 경우 사용자는 손가락을 누르고 있는 동안 손가락을 길게 누르고 탭이 계속 발생 합니다. 두 번 누르기와 유지를 모두 요청 하는 경우 손가락을 누른 채 잠시 후에 제스처는 보류 중으로 승격 되 고 탭이 더 이상 발생 하지 않습니다.

SpatialGestureRecognizer를 사용 하려면 SpatialInteractionManager의 [InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected) 이벤트를 처리 하 고 여기에 노출 된 SpatialPointerPose를 가져옵니다. 이 포즈의 사용자 헤드 응시 레이를 사용 하 여 사용자가 사용자의 holograms 및 surface 메시를 사용 하 여 사용자가 원하는 작업을 결정 합니다. 그런 다음 [CaptureInteraction](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction) 메서드를 사용 하 여 이벤트 인수의 SpatialInteraction을 대상 홀로그램의 SpatialGestureRecognizer로 라우팅합니다. 이렇게 하면 생성 시 또는 [TrySetGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings)에서 해당 인식기의 [SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings) 설정에 따라 해당 상호 작용을 해석 하기 시작 합니다.

HoloLens (첫 번째 gen)에서 상호 작용 및 제스처는 일반적으로 직접 위치에서 직접 렌더링 하거나 상호 작용 하는 대신 사용자의 헤드 응시에서 대상으로 지정 해야 합니다. 상호 작용이 시작 된 후 조작 또는 탐색 제스처와 같이 손의 상대 동작을 사용 하 여 제스처를 제어할 수 있습니다.

## <a name="see-also"></a>참고 항목
* [DirectX의 헤드 및 눈 응시](gaze-in-directx.md)
* [직접 조작 입력 모델](direct-manipulation.md)
* [지점 및 커밋 입력 모델](point-and-commit.md)
* [입력 모델 응시 및 커밋](gaze-and-commit.md)
* [모션 컨트롤러](motion-controllers.md)
