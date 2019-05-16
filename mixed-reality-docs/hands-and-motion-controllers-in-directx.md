---
title: 실습 및 DirectX에서 컨트롤러 동작
description: 네이티브 DirectX 앱에서 직접 추적 및 동작 컨트롤러를 사용 하기 위한 개발자 가이드입니다.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/30/2019
ms.topic: article
keywords: 실습, 동작 컨트롤러, directx, 입력, 홀로그램
ms.openlocfilehash: 08666c8c26cd4851c0c003a96a9e96d7a90228ac
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629646"
---
# <a name="hands-and-motion-controllers-in-directx"></a>실습 및 DirectX에서 컨트롤러 동작

Windows Mixed Reality에 모두 전달 및 [동작 컨트롤러](motion-controllers.md) 입력에서 찾을 공간 입력 Api 통해 처리 됩니다 합니다 [Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial) 네임 스페이스입니다. 쉽게 등의 일반적인 작업을 처리할 수 있습니다 **선택** 실습 및 동작 컨트롤러 모두에서 동일한 방식으로 있습니다.

## <a name="getting-started"></a>시작

액세스에 공간에서 Windows Mixed Reality 입력 SpatialInteractionManager 인터페이스를 사용 하 여 시작 합니다.  이 인터페이스를 호출 하 여 액세스할 수 있습니다 [SpatialInteractionManager::GetForCurrentView](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getforcurrentview), 일반적으로 앱 시작 시 따라 합니다.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

SpatialInteractionManager interactionManager = SpatialInteractionManager::GetForCurrentView();
```

SpatialInteractionManager의 작업에 대 한 액세스를 제공 하는 것 [SpatialInteractionSources](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource), 입력 소스를 나타내는입니다.  세 가지 종류의 SpatialInteractionSources 시스템에서 사용할 수 있습니다.
* **직접** 사용자의 검색 된 직접 나타냅니다. 직접 원본 HoloLens에 기본 제스처에서 완전히 표시 된 직접 HoloLens 2에서 추적에 이르기까지, 장치에 따라 다양 한 기능을 제공 합니다. 
* **컨트롤러** 쌍을 이루는 동작 컨트롤러를 나타냅니다. 동작 컨트롤러는 다양 한 기능을 제공할 수 있습니다.  예를 들어 다음과 같은 가치를 제공해야 합니다. 트리거, 메뉴 단추, 감각을 단추, 터치 패드 및 스틱을 선택 합니다.
* **음성** 사용자의 음성 말하기 시스템 검색 키워드를 나타냅니다. 예를 들어,이 소스를 삽입 된 선택 키를 눌러 사용자가 "Select" 때마다 릴리스 합니다.

프레임당 데이터 원본으로 표시 됩니다에 대 한 합니다 [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) 인터페이스입니다. 응용 프로그램에서 이벤트 구동 또는 폴링 기반 모델을 사용할 것인지에 따라이 데이터에 액세스 하려면 두 가지가 있습니다.

### <a name="event-driven-input"></a>이벤트 기반 입력
SpatialInteractionManager 수의 앱에 대 한 수신 대기할 수 있는 이벤트를 제공 합니다.  몇 가지 예로 [SourcePressed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed)하십시오 [SourceReleased](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) 하 고 [SourceUpdated](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated)합니다.

예를 들어, 다음 코드를 MyApp::OnSourcePressed SourcePressed 이벤트를 호출 하는 이벤트 처리기를 연결 합니다.  이 앱을을 누르면 모든 종류의 상호 작용 원본에서 검색할 수 있습니다.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
interactionManager.SourcePressed({ this, &MyApp::OnSourcePressed });

```

누름된이 이벤트는 눌러 발생 시 해당 SpatialInteractionSourceState 함께 비동기적으로 앱에 전송 됩니다. 앱 또는 게임 엔진은 일부 처리를 즉시 수행 해야 할 수 또는 처리 루틴 입력에서 이벤트 데이터를 큐에 대기 하는 것이 좋습니다. 선택 단추를 눌렀는지 여부를 확인 하는 방법을 보여 주는 SourcePressed 이벤트에 대 한 이벤트 처리기 함수는 다음과 같습니다.

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

위의 코드는 장치에서 기본 작업에 해당 하는 'Select' press만 확인 합니다. HoloLens에는 AirTap 수행 또는 동작 컨트롤러에서 트리거를 끌어오기을 예로 들 수 있습니다.  'Select' 누름 대상으로 하는 홀로그램을 활성화 하려면 사용자의 의도를 나타냅니다.  다양 한 다른 단추와 제스처에 대 한이 SourcePressed 이벤트가 발생 합니다 하 고 테스트 사례만 SpatialInteractionSource의 다른 속성을 검사할 수 있습니다.

### <a name="polling-based-input"></a>폴링 기반 입력
입력의 현재 상태에 대 한 모든 프레임을 폴링할 SpatialInteractionManager 이용할 수 있습니다.  이렇게 하려면 단순히 호출 [GetDetectedSourcesAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) 프레임 마다.  이 함수 하나를 포함 하는 배열을 반환 [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) 모든 활성 [SpatialInteractionSource](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource)합니다. 즉, 각 활성 동작 컨트롤러, 각 추적 된 포인터에 대 한 음성에 대 한 'select' 명령을 최근에 마냥 마음이 들 뜹니다. 그런 다음 응용 프로그램에 각 SpatialInteractionSourceState 드라이브 입력에 대 한 속성을 검사할 수 있습니다. 

폴링 메서드를 사용 하는 'select' 작업에 대 한 확인 하는 방법의 예는 다음과 같습니다. *예측* 변수를 나타냅니다는 [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) 에서 가져올 수 있는 개체를 [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)합니다.

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

각 SpatialInteractionSource에 새 소스를 식별 하 고 기존 원본 프레임 간에 상관 관계를 지정 하는 데 사용할 수 있는 ID가 있습니다.  실습은 컨트롤러 Id는 세션의 기간 동안 정적 상태로 유지 되지만 유지 하며, FOV 입력 때마다 새 ID는 할당 됩니다.  SpatialInteractionManager에서와 같은 이벤트를 사용할 수 [SourceDetected](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcedetected) 하 고 [SourceLost](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcelost), 실습을 입력 하거나 장치를 유지 하는 경우 반응의 보기 또는 동작 컨트롤러 켜고 설정 또는 경우 쌍을 이루는/짝이 없는 합니다.

### <a name="predicted-vs-historical-poses"></a>기록 포즈 및 예측
GetDetectedSourcesAtTimestamp 타임 스탬프 매개 변수는 참고 합니다. 이렇게 하면 상태를 요청 하 고 예측 하거나 데이터를 내포할 수 있습니다 또는 다른 입력 소스를 사용 하 여 공간 상호 작용을 상호 연결 기록, 하도록 합니다. 예를 들어, 현재 프레임에 손 모양 아이콘이 위치를 렌더링할 때 전달할 수 있습니다 제공한 예측된 타임 스탬프를 [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)합니다. 따라서 시스템 정방향 예측 체감된 대기 시간을 최소화 렌더링 된 프레임 출력을 사용 하 여 맞추려는 직접 위치에 있습니다.

그러나 예측된 포즈 이러한를 상호 작용 원본을 사용 하 여 대상으로 하는 이상적인 포인팅 광선을 생성 하지 않습니다. 예를 들어 컨트롤러 동작 단추를 누를 때 운영 체제에 Bluetooth를 통해 버블 업 이벤트에 대 한 최대 20ms 걸릴 수 있습니다. 마찬가지로, 손 제스처를 수행 하면, 어느 정도의 시간 시스템 제스처를 감지 하는 앱 다음에 대 한 폴링합니다 전에 전달할 수 있습니다. 상태 변경에 대 한 앱 폴링합니다 시간, 헤드 및 직접 발생 대상 과거에 실제로 발생 한 상호 작용 하는 데 사용 합니다. GetDetectedSourcesAtTimestamp를 현재 프로그램 HolographicFrame의 타임 스탬프를 전달 하 여 대상 포즈 됩니다 대신 앞으로 예측할 수 타기 팅 광선을 프레임을 표시할 때 나중에 20ms 둘 수 있습니다. 이 향후 포즈 적합 *렌더링* 상호 작용 원본에 대 한 시간 문제를 하지만 않았을 *대상으로* 과거에 발생 사용자의 대상으로 하는 대로 상호 작용을 합니다.

다행 스럽게도 합니다 [SourcePressed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed)를 [SourceReleased](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) 및 [SourceUpdated](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated) 이벤트를 기록 제공 [상태](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) 연관 각 입력된 이벤트입니다.  직접 포함 되어이 통해 사용할 수 있는 기록 헤드 및 직접 발생 [TryGetPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose), 기록를 함께 [타임 스탬프](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.timestamp) 이 이벤트와 연결할 다른 Api에 전달할 수 있습니다.

렌더링 하 고 각 프레임의 실습 및 컨트롤러를 사용 하 여 대상으로 하는 경우 다음 모범 사례에 연결 합니다.
* 에 대 한 **손/컨트롤러 렌더링** 앱 해야 하는 각 프레임 **폴링** 에 대 한 합니다 **정방향 예측** 현재 프레임의 photon 시 각 상호 작용 원본의 발생할 합니다.  호출 하 여 모든 상호 작용 원본에 대해 폴링하면 [GetDetectedSourcesAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) 제공한 예측된 타임 스탬프를 전달 하는 각 프레임을 [HolographicFrame::CurrentPrediction](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.currentprediction)합니다.
* 에 대 한 **손/컨트롤러를 대상으로 하** 누르거나 릴리스 시 앱 눌렀다 해제 처리 해야 **이벤트**, 플레이어가 기반으로 합니다 **기록** 에 대 한 헤드 또는 직접 자세 해당 이벤트입니다. 처리 하 여이 대상 광선을 얻게 합니다 [SourcePressed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed) 또는 [SourceReleased](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) 이벤트를 시작 합니다 [상태](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) 속성에서 이벤트 인수를 호출한 다음 해당 [ TryGetPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) 메서드.

## <a name="cross-device-input-properties"></a>장치 간 입력된 속성
SpatialInteractionSource API 컨트롤러와 직접 추적 기능의 광범위 한를 사용 하 여 시스템을 지원 합니다. 이러한 기능을 수는 장치 유형 간에 공통적입니다. 예를 들어, 직접 추적 및 동작 컨트롤러 모두에 'select' 작업을 및 3D 위치를 제공합니다. 가능 하면 API는 SpatialInteractionSource에서 동일한 속성에 이러한 일반적인 기능을 매핑합니다.  이 통해 응용 프로그램을 보다 쉽게 다양 한 입력된 형식 지원 합니다. 다음 표에서 지원 되는 속성을 설명 하 고 입력된 형식 간에 어떻게 다른 지 합니다.

| 속성 | 설명 | HoloLens 제스처 | 컨트롤러 동작 | 명확 하 고 실습|
|--- |--- |--- |--- |--- |
| [SpatialInteractionSource::**선호도**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.handedness) | 오른쪽 또는 왼쪽 / 컨트롤러입니다. | 지원되지 않음 | 지원됨 | 지원됨 |
| [SpatialInteractionSourceState::**IsSelectPressed**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isselectpressed) | 기본 단추의 현재 상태입니다. | 어 탭 | 트리거 | 완화 된 어 탭 (수직 축소) |
| [SpatialInteractionSourceState::**IsGrasped**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isgrasped) | 잡기 단추의 현재 상태입니다. | 지원되지 않음 | 단추를 선택 합니다. | 축소 또는 닫힌 직접 |
| [SpatialInteractionSourceState::**IsMenuPressed**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.ismenupressed) | 메뉴 단추의 현재 상태입니다.    | 지원되지 않음 | 메뉴 단추 | 지원되지 않음 |
| [SpatialInteractionSourceLocation::**Position**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.position) | 컨트롤러에서 직접 또는 그립 위치의 XYZ 위치입니다. | 팜 위치 | 그립 포즈 위치 | 팜 위치 |
| [SpatialInteractionSourceLocation::**Orientation**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.orientation) | 컨트롤러에서 직접 또는 그립 포즈의 방향을 나타내는 쿼터 니 언입니다. | 지원되지 않음 | 그립 포즈 방향 | Palm 방향 |
| [SpatialPointerInteractionSourcePose::**Position**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.position#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_Position) | 포인팅 광선의 원점입니다. | 지원되지 않음 | 지원됨 | 지원됨 |
| [SpatialPointerInteractionSourcePose::**ForwardDirection**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.forwarddirection#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_ForwardDirection) | 포인팅 광선의 방향입니다. | 지원되지 않음 | 지원됨 | 지원됨 |

위의 속성 중 일부를 모든 장치에서 사용할 수 없는 및 API를 통해이 테스트할 수 있습니다. 예를 들어, 검사할 수 있습니다 합니다 [SpatialInteractionSource::IsGraspSupported](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.isgraspsupported) 원본 감각을 동작을 제공 하는지 여부를 결정 하는 속성입니다.

### <a name="grip-pose-vs-pointing-pose"></a>그립 포즈 포인팅 포즈 비교

Windows Mixed Reality 다양 한 폼 팩터 동작 컨트롤러를 지원합니다.  또한 명확 하 고 직접 추적 시스템을 지원 합니다.  이러한 모든 시스템 손 모양 위치 및 앱에서 사용자의 직접 가리키는 또는 rendreing 개체에 대해 사용 해야 하는 "정방향" 방향 간의 여러 관계를 가집니다.  이 지원 하려면 두 가지 유형의 직접 추적 및 동작 컨트롤러 모두에 대해 제공 하는 3D 포즈 있습니다.  첫 번째는 사용자의 직접 위치를 나타내는 그립 자세 합니다.  두 번째는 사용자의 직접 또는 컨트롤러에서 시작 되는 포인팅 빛을 나타내는 자세를 가리킵니다. 따라서 렌더링 하려는 경우 **사용자의 직접** 또는 **사용자의 직접에 보관 된 개체**등 sword 또는 총, 그립 자세를 사용 합니다. 예를 들어 사용자가 직접 또는 컨트롤러의 raycast 하려는 경우 **UI를 가리키는** 를 가리키는 자세를 사용 합니다.

액세스할 수 있습니다 합니다 **그립 포즈** 를 통해 [SpatialInteractionSourceState::Properties::TryGetLocation(...) ](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties.trygetlocation#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).  다음과 같이 정의 됩니다.
* 합니다 **위치를 잡고**: 물론 컨트롤러를 보유 하는 경우 팜 중심 왼쪽 또는 오른쪽 가운데 그립 내의 위치를 조정 합니다.
* 합니다 **방향을 올바른 축 잡고**: 완전히 플랫 5 손가락 자세를 직접 열면 광선과 표준 프로그램 palm에서 (왼쪽된 palm, palm 오른쪽에서 이전 버전과에서 앞으로)
* 합니다 **방향을 정방향 축 잡고**: 부분적으로 (처럼 컨트롤러 보유) 직접을 닫을 때, 광선을 가리키는 "forward" 튜브를 통해 비 엄지 손가락으로 구성 합니다.
* 합니다 **축 위쪽 방향 잡고**: 오른쪽 정방향 정의 사용 권한에 포함 된 최대 축.

액세스할 수 있습니다 합니다 **포인터 포즈** 를 통해 [SpatialInteractionSourceState::Properties::TryGetLocation (...):: SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose) 또는 [SpatialInteractionSourceState:: TryGetPointerPose (...):: TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_)합니다.

## <a name="controller-specific-input-properties"></a>컨트롤러 관련 입력된 속성
컨트롤러에 대 한는 SpatialInteractionSource 추가 기능을 사용 하 여 컨트롤러 속성이 있습니다.
* **HasThumbstick:** True 이면 컨트롤러에는 엄지 스틱 합니다. 검사는 [ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) 스틱을 가져오려고 SpatialInteractionSourceState 속성 x 및 y 값 (ThumbstickX 및 ThumbstickY) 뿐만 아니라 누름된 상태로 (IsThumbstickPressed).
* **HasTouchpad:** True 이면 컨트롤러에는 터치 패드를 있습니다. 터치 패드를 가져오려고 SpatialInteractionSourceState의 ControllerProperties 속성을 검사할 x 및 y 값 (TouchpadX 및 TouchpadY) 및 사용자 (IsTouchpadTouched) 패드 접촉 되어 및 터치 패드 (축소 키를 눌러는 경우 IsTouchpadPressed)입니다.
* **SimpleHapticsController:** SimpleHapticsController API 컨트롤러를 사용 하면 컨트롤러의 haptics 기능을 검사할 수 있습니다 하 고 햅 틱 피드백을 제어할 수도 있습니다.

터치 패드 및 엄지 스틱의 범위는-1과 1 양 축에 대 한 (위쪽, 아래쪽에서 및 왼쪽에서 오른쪽) note 합니다. SpatialInteractionSourceState::SelectPressedValue 속성을 사용 하 여 액세스할을 수 있는 아날로그 트리거에 대 한 범위는 0 ~ 1 범위를 있습니다. 값이 true로 같다고 IsSelectPressed와 1 상관 관계가 지정 다른 값 IsSelectPressed false 같지 않은지를 사용 하 여 상관 관계를 지정 합니다.

## <a name="articulated-hand-tracking"></a>명확 하 고 직접 추적
Windows Mixed Reality API 추적, 예를 들어 HoloLens 2에서 명확 하 고 직접 전체 지원을 제공 합니다. 응용 프로그램에서 직접 조작 및 지점 커밋 입력된 모델을 구현 하 추적 명확 하 고 직접 사용할 수 있습니다. 완전히 사용자 지정 상호 작용을 작성 하려면 데도 수 있습니다.

### <a name="hand-skeleton"></a>직접 스 켈 레 톤
추적 명확 하 고 직접 다양 한 유형의 상호 작용을 사용 하도록 설정 하는 25 공동 구조를 제공 합니다.  인덱스/중간/링/거의 손가락에 대 한 5이 음, thumb에서 4이 음 및 1 손목 공동 구조를 제공합니다.  손목 연결점 계층의 기반으로 사용 됩니다. 다음 그림에서는 골격의 레이아웃을 보여 줍니다.

![직접 스 켈 레 톤](images/hand-skeleton.png)

대부분의 경우에서 각이 음 나타내는 뼈에 따라 명명 됩니다.  모든 연결에서 두 뼈 되므로 해당 위치에서 자식 뼈에 따라 각 공동 명명 규칙을 사용 합니다.  자식 본 다음 손목 멀리 뼈도 정의 됩니다.  예를 들어는 "인덱스 Proximal" 공동 포함 인덱스 proximal 뼈의 시작 위치 및 해당 뼈의 방향입니다.  뼈의 끝 위치를 포함 하지 않습니다.  하는 경우 얻게이 다음에서 계층의 "인덱스 중간" 공동의 공동 합니다.

25 계층적이 음 외에도 시스템 palm 연결점을 제공합니다.  손바닥 골격 구조의 일부 일반적으로 간주 되지 않습니다.  편리 하 게 손 모양 아이콘이 전체 위치 및 방향 으로만 제공 됩니다.

각 연결에 대 한 다음과 같은 정보가 제공 됩니다.

| 이름 | 설명 |
|--- |--- |
|위치 | 사용할 수는 이음새의 3D 위치 좌표 시스템을 요청 합니다. |
|방향 | 사용할 수는 뼈의 3D 방향을 좌표계를 요청 합니다. |
|반경 | 공동 위치에 있는 스킨의 화면 까지의 거리입니다. 직접 상호 작용 또는 손가락 너비를 사용 하는 시각화를 튜닝 하는 데 유용 합니다. |
|정확도 | 이 연결 정보에 대 한 시스템 느낌 얼마나 자신에 힌트를 제공 합니다. |

함수를 통해 직접 스 켈 레 톤 데이터에 액세스할 수 있습니다 합니다 [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)합니다.  함수를 호출 [TryGetHandPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygethandpose#Windows_UI_Input_Spatial_SpatialInteractionSourceState_TryGetHandPose)를 호출 하는 개체를 반환할 [HandPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handpose)합니다.  원본 명확 하 고 실습을 지원 하지 않는 경우이 함수는 null을 반환 됩니다.  HandPose를 만든 후 호출 하 여 현재 공동 데이터를 가져올 수 있습니다 [TryGetJoint](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handpose.trygetjoint#Windows_Perception_People_HandPose_TryGetJoint_Windows_Perception_Spatial_SpatialCoordinateSystem_Windows_Perception_People_HandJointKind_Windows_Perception_People_JointPose__), 연결점의 이름에 관심이 있습니다.  데이터가로 반환 되는 [JointPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.jointpose) 구조입니다.  다음 코드는 집게 손가락 팁의 위치를 가져옵니다. 변수의 *currentState* 의 인스턴스를 나타내며 [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)합니다.

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

### <a name="hand-mesh"></a>직접 메시

완벽 하 게 deformable 삼각형 직접 메시에 대 한 API 추적 명확 하 고 손 모양 아이콘이 있습니다.  이 메시와 직접 스 켈 레 톤 함께 실시간에서 변형 수 하며 고급 물리학 기술 뿐만 아니라 시각화에 대 한 유용 합니다.  직접 메시에 액세스 하려면 먼저 생성 해야는 [HandMeshObserver](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshobserver) 개체를 호출 하 여 [TryCreateHandMeshObserverAsync](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync) 에 [SpatialInteractionSource](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource)합니다.  이 한 번 원본별, 일반적으로 처음 표시 해야 합니다.  즉, 손 모양 FOV 들어갈 때마다 HandMeshObserver 개체를 만들려면이 함수를 호출 합니다.  이 비동기 함수를 동시성 여기의 비트를 사용 하 여 처리 해야 하므로 note 합니다.  를 사용할 수 있는 요청 HandMeshObserver 개체 삼각형 인덱스 버퍼를 호출 하 여 [GetTriangleIndices](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshobserver.gettriangleindices#Windows_Perception_People_HandMeshObserver_GetTriangleIndices_System_UInt16___)합니다.  해당 항목을 한 번 가져올 하 고 해당 원본의 수명에 대 한 캐시 수 있도록 인덱스 프레임을 통해 프레임을 변경 하지 마세요.  인덱스 감기 시계 방향 순서로 제공 됩니다.

다음 코드는 메시 관찰자를 만들려면 분리 std::thread 스핀업 하 고 메시 관찰자를 사용할 수 있으면 인덱스 버퍼를 추출 합니다.  라는 변수에서 시작 *currentState*의 인스턴스인 [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) 나타내는 추적 된 손 모양입니다.

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
분리 된 스레드를 시작 하는 것은 비동기 호출을 처리 하기 위한 하나의 옵션입니다.  또는 사용할 수 있습니다 새 [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) 기능에서 지원 되는 C++/WinRT 합니다.

HandMeshObserver 개체를 만든 후 해당 해당 SpatialInteractionSource 활성 상태인 동안 점유 해야 있습니다.  다음 각 프레임을 요청할 수 있습니다를 호출 하 여 손 모양 아이콘이 나타내는 최신 버텍스 버퍼에 대 한 [GetVertexStateForPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshobserver.getvertexstateforpose) 전달 된 [HandPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handpose) 꼭 짓 점 하려는 자세를 나타내는 인스턴스 에 대 한  버퍼의 각 꼭 짓 점 위치와 일반에 있습니다.  직접 메시에 대 한 현재 꼭 짓 점 집합을 가져오는 방법의 예는 다음과 같습니다.  이전과 마찬가지로 합니다 *currentState* 변수 인스턴스를 나타냅니다 [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)합니다.

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

스 켈 레 톤이 음 달리 직접 메시 API 수 없도록 꼭 짓 점에 대 한 좌표 시스템을 지정할 수 있습니다.  대신 합니다 [HandMeshVertexState](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshvertexstate) 꼭 짓 점을에서 제공 되는 좌표계를 지정 합니다.  메시 변환 호출 하 여 얻을 수 있습니다 [TryGetTransformTo](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem.trygettransformto#Windows_Perception_Spatial_SpatialCoordinateSystem_TryGetTransformTo_Windows_Perception_Spatial_SpatialCoordinateSystem_) 원하는 좌표 시스템을 지정 합니다.  꼭 짓 점을 사용 하 여 작업할 때마다이 메시 변환을 사용 해야 합니다.  이 방법은 메시 렌더링을 위해 사용 하는 경우에 특히 CPU 오버 헤드를 줄입니다.

## <a name="gaze-and-commit-composite-gestures"></a>Gaze 및 복합 제스처 커밋
HoloLens에서 특히 게이즈 커밋 입력된 모델을 사용 하 여 응용 프로그램에 대 한 (첫 번째 gen) 공간 입력 API가 제공 선택적인 [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx) 사용할 수 있는 기반으로 구축 하는 복합 제스처를 사용 하도록 설정 합니다 ' select' 이벤트입니다.  라우팅 상호 작용을 SpatialInteractionManager에서 홀로그램의 SpatialGestureRecognizer 하 여 앱 수 탭, 보류, 조작 및 탐색 이벤트 감지 균일 하 게 바늘, 음성 및 공간 입력된 장치에서 누름을 처리 하지 않고도 수동으로 해제 합니다.

SpatialGestureRecognizer 요청 하는 제스처 집합 간의 최소 명확성에만 수행 합니다. 예를 들어,만 Tap를 요청 하는 경우 사용자 수 누른 해당 손가락 있기만 원하는 탭 계속 발생 합니다. 요청 하는 경우 모두 페이지를 누르고, 보류 승격 제스처는 해당 손가락 누르고의 보조에 대 한 후 탭을 더 이상 발생 합니다.

SpatialGestureRecognizer를 사용 하려면 SpatialInteractionManager의 처리할 [InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected) 이벤트 및 잡기를 SpatialPointerPose 노출 있습니다. 상호 작용 하려는 의도 하는 사용자가 확인 하기 위해 사용자의 환경 등에서 화면 메시 및 교차 하 여 홀로그램이이 포즈에서 사용자의 헤드 게이즈 광선을 사용 합니다. 그런 다음 대상 홀로그램의 SpatialGestureRecognizer 위해 이벤트 인수에는 SpatialInteraction 경로 사용 하 여 해당 [CaptureInteraction](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction) 메서드. 해석에 따라 해당 상호 작용이 시작 됩니다 합니다 [SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings) 생성 시-통하거나 해당 인식기 설정 [TrySetGestureSettings](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings)합니다.

HoloLens에 (gen 먼저) 해당 사용자의 헤드 게이즈를에서 타기 팅 하기 보다는 동안 렌더링 또는 손 모양 아이콘이 위치에 직접 작용 상호 작용 및 제스처를 일반적으로 파생 되어야 합니다. 상호 작용 시작 된 후 조작 또는 탐색 제스처와 마찬가지로 제스처를 제어 하려면 손 모양 아이콘이의 상대적 동작을 사용할 수 있습니다.

## <a name="see-also"></a>참조
* [DirectX의 헤드 및 눈 응시](gaze-in-directx.md)
* [입력된 모델을 직접 조작](direct-manipulation.md)
* [지점 및 커밋 입력된 모델](point-and-commit.md)
* [입력된 모델을 응시 및 커밋](gaze-and-commit.md)
* [모션 컨트롤러](motion-controllers.md)
