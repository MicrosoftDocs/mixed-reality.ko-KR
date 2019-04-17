---
title: 응시, 제스처 및 DirectX에서 동작 컨트롤러
description: 입력된 게이즈, 제스처 및 동작 컨트롤러에서 제공 하는 것을 결합 하는 홀로그램 앱에 적용할 사용자를 사용할 수 있습니다.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 응시, 제스처, 동작 컨트롤러, directx, 입력, 홀로그램
ms.openlocfilehash: 7cee3d3d7fbcd903eae0376e205034b9cc4ead3b
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605092"
---
# <a name="gaze-gestures-and-motion-controllers-in-directx"></a>응시, 제스처 및 DirectX에서 동작 컨트롤러

플랫폼을 기반으로 직접 작성 하려는 경우 입력된을 통해 사용자가 보는 위치와 같은 사용자에서 제공 하는 것을 처리 해야 합니다 [헤드 게이즈](gaze.md) 및 사용자가 사용 하 여 선택한 [제스처](gestures.md) 또는 [컨트롤러 동작](motion-controllers.md)합니다. 이러한 형태의 입력을 결합 적용할 사용자를 설정할 수 있습니다.는 [홀로그램](hologram.md) 앱에서. 합니다 [holographic 앱 템플릿](creating-a-holographic-directx-project.md) 사용 하기 쉬운 예제가 포함 되어 있습니다.

>[!NOTE]
>이 문서의 코드 조각 사용에 현재 방법을 보여 줍니다 C++/CX 대신 C + + 17 규격 C++/WinRT에 사용 되는 [ C++ holographic 프로젝트 템플릿을](creating-a-holographic-directx-project.md).  개념에 대 한 동일는 C++코드를 변환 해야 하지만 /WinRT 프로젝트입니다.

## <a name="gaze-input"></a>응시 입력

사용자의 액세스 [헤드 게이즈](gaze.md)를 사용 합니다 [SpatialPointerPose](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialpointerpose.aspx) 형식입니다. Holographic 앱 템플릿 이해 응시에 대 한 기본 코드를 포함합니다. 이 코드에서는 사용자의 눈에 장치 위치와 방향에 고려 사이 있는 앞으로 가리키는 벡터는 주어진 [좌표계](coordinate-systems-in-directx.md)합니다.




```cpp
void SpinningCubeRenderer::PositionHologram(SpatialPointerPose^ pointerPose)
{
    if (pointerPose != nullptr)
    {
        // Get the gaze direction relative to the given coordinate system.
        const float3 headPosition    = pointerPose->Head->Position;
        const float3 headDirection   = pointerPose->Head->ForwardDirection;
    
        // The hologram is positioned two meters along the user's gaze direction.
        static const float distanceFromUser = 2.0f; // meters
        const float3 gazeAtTwoMeters        = headPosition + (distanceFromUser * headDirection);
    
        // This will be used as the translation component of the hologram's
        // model transform.
        SetPosition(gazeAtTwoMeters);
    }
}
```

요청을 사용할 수 있습니다. "하지만 어디 좌표계에서 가져옵니까"?

해당 질문에 대답 해 보겠습니다. 우리의 AppMain **업데이트** 함수 처리 공간 입력된 이벤트를 우리의 StationaryFrameOfReference에 대 한 좌표 시스템을 기준으로 확보 하 여 합니다. 설정 하는 경우는 StationaryFrameOfReference 만들어졌는지 회수 합니다 [HolographicSpace](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx), 좌표 시스템의 시작 부분에 획득 하 고 [업데이트](rendering-in-directx.md)합니다.




```cpp
// Check for new input state since the last frame.
SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
if (pointerState != nullptr)
{
    // When a Pressed gesture is detected, the sample hologram will be repositioned
    // two meters in front of the user.
    m_spinningCubeRenderer->PositionHologram(
        pointerState->TryGetPointerPose(currentCoordinateSystem)
        );
}
```

데이터는 일종의 포인터 상태 관련이 참고 합니다. 에서는 공간 입력된 이벤트에서 가져옵니다. 이벤트 데이터 개체는 좌표계 포함 되므로 항상 이벤트 시 게이즈 방향을 해야 모든 공간 좌표계에 연결할 수 있습니다. 실제로 포인터 자세를 가져오기 위해 수행 해야 합니다.

> [!NOTE]
> HoloLens 2 관련 된 자세한 지침 [예정](index.md#news-and-notes)합니다.

## <a name="gesture-and-motion-controller-input"></a>입력 제스처 및 중인 컨트롤러

Windows Mixed Reality에 모두 전달 [제스처](gestures.md) 하 고 [컨트롤러 동작](motion-controllers.md) 있는 동일한 공간 입력 Api 통해 처리 됩니다는 [Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial) 네임 스페이스입니다. 쉽게 등의 일반적인 작업을 처리할 수 있습니다 **선택** 실습 및 동작 컨트롤러 모두에서 동일한 방식으로 있습니다.

혼합된 현실에서 제스처 또는 컨트롤러 동작을 처리할 때 대상 API의 두 가지 수준이 있습니다.
* [상호 작용](gestures.md#the-two-core-gestures-of-hololens) ([SourcePressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed.aspx)를 [SourceReleased](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased.aspx) 하 고 [SourceUpdated](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated.aspx))를 사용 하 여 액세스를 [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx)
* [복합 제스처](gestures.md#composite-gestures) ([Tapped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.tapped.aspx), 저장, 조작, 탐색)를 사용 하 여 액세스를 [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx)

### <a name="selectmenugrasptouchpadthumbstick-interactions-spatialinteractionmanager"></a>선택/메뉴/한결/터치 패드/엄지 스틱 상호 작용 합니다. SpatialInteractionManager

실습 및 Windows Mixed Reality의 입력된 장치에서 하위 수준 누름, 릴리스 및 업데이트를 검색 하려면에서 시작 된 [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx)합니다. SpatialInteractionManager에 손 모양 때 응용 프로그램을 알리는 이벤트 또는 동작 컨트롤러 입력 되었습니다.

세 가지 주요 종류 SpatialInteractionSource의, 각각 다른 SpatialInteractionSourceKind 값으로 표시 합니다.
* **직접** 사용자의 검색 된 직접 나타냅니다. 직접 원본 HoloLens에만 사용할 수 있습니다.
* **컨트롤러** 쌍을 이루는 동작 컨트롤러를 나타냅니다. 동작 컨트롤러는 예를 들어 다양 한 기능을 제공할 수 있습니다. 트리거, 메뉴 단추, 감각을 단추, 터치 패드 및 스틱을 선택 합니다.
* **음성** 사용자의 음성 말하기 시스템 검색 키워드를 나타냅니다. 선택 키를 눌러 삽입 되 고 사용자가 "Select" 때마다 해제 됩니다.

누름 이러한 상호 작용 원본에서 검색할 SpatialInputHandler.cpp에서 SpatialInteractionManager의 SourcePressed 이벤트를 처리할 수 있습니다.


```cpp
m_interactionManager = SpatialInteractionManager::GetForCurrentView();
    
// Bind a handler to the SourcePressed event.
m_sourcePressedEventToken =
    m_interactionManager->SourcePressed +=
        ref new TypedEventHandler<SpatialInteractionManager^, SpatialInteractionSourceEventArgs^>(
            bind(&SpatialInputHandler::OnSourcePressed, this, _1, _2)
            );
```

이 누름된 이벤트 앱에 비동기적으로 전송 됩니다. 앱 또는 게임 엔진은 일부 처리를 즉시 수행 해야 할 수 또는 처리 루틴 입력에서 이벤트 데이터를 큐에 대기 하는 것이 좋습니다.

템플릿은 시작 하는 도우미 클래스를 포함 합니다. 이 템플릿은 forgoes 디자인의 단순성에 대 한 모든 처리 합니다. 도우미 클래스는 추적 하나의 이상의 **누름** 마지막 이후에 발생 한 이벤트 **업데이트** 호출 합니다. SpatialInputHandler.cpp:




```cpp
void SpatialInputHandler::OnSourcePressed(SpatialInteractionManager^ sender, SpatialInteractionSourceEventArgs^ args)
{
    m_sourceState = args->State;
    
    //
    // TODO: In your app or game engine, rewrite this method to queue
    //       input events in your input class or event handler.
    //
}
```

따라서 반환 하는 경우는 [SpatialInteractionSourceState](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) 다음 업데이트 하는 동안 가장 최근 입력된 이벤트에 대 한 합니다. SpatialInputHandler.cpp:




```cpp
// Checks if the user performed an input gesture since the last call to this method.
// Allows the main update loop to check for asynchronous changes to the user
// input state.
SpatialInteractionSourceState^ SpatialInputHandler::CheckForInput()
{
    SpatialInteractionSourceState^ sourceState = m_sourceState;
    m_sourceState = nullptr;
    return sourceState;
}
```

참고는 위의 코드에서 처리 모든 사용자가 기본 수행 여부를 동일 하 게 누를 **선택** 누르거나 보조 **메뉴** 또는 **이해** 키를 누릅니다. 합니다 **선택** 누름을 바늘, 모션 동작 컨트롤러 기본 트리거/단추 누름을 어 탭 수행 손 모양으로 컨트롤러 및 음성, 트리거 또는 사용자의 지원 되는 상호 작용의 기본 폼 "Select"를 말하는 음성. 선택 키를 누를 대상으로 하는 홀로그램을 활성화 하려면 사용자의 의도를 나타냅니다.

키를 눌러의 종류에 대 한 이유를 발생 하는, SpatialInteractionManager::SourceUpdated 이벤트 처리기를 수정 하겠습니다. 코드 (사용 가능한 경우) 감각을 누르면을 감지 하 고 큐브의 위치를 변경 하려면 사용 합니다. 이해도 사용할 수 없는 경우 대신 선택 누름 사용 합니다.

다음과 같은 private 멤버 선언을 SpatialInputHandler.h 추가: 


```cpp
void OnSourceUpdated(
       Windows::UI::Input::Spatial::SpatialInteractionManager^ sender,
       Windows::UI::Input::Spatial::SpatialInteractionSourceEventArgs^ args);
   Windows::Foundation::EventRegistrationToken m_sourceUpdatedEventToken;
```

SpatialInputHandler.cpp를 엽니다. 생성자에 다음 이벤트 등록을 추가 합니다. 


```cpp
m_sourceUpdatedEventToken =
       m_interactionManager->SourceUpdated +=
       ref new TypedEventHandler<SpatialInteractionManager^, SpatialInteractionSourceEventArgs^>(
           bind(&SpatialInputHandler::OnSourceUpdated, this, _1, _2)
           );
```

이벤트 처리기 코드입니다. 입력된 소스를 파악, 발생 한 경우 다음 업데이트 루프에 대 한 포인터 포즈 저장 됩니다. 그렇지 않으면 확인 선택 입력 대신 합니다. SpatialInputHandler.cpp:




```cpp
void SpatialInputHandler::OnSourceUpdated(SpatialInteractionManager^ sender, SpatialInteractionSourceEventArgs^ args)
{
    if (args->State->Source->IsGraspSupported)
    {
        if (args->State->IsGrasped)
        {
            m_sourceState = args->State;
        }
    }
    else
    {
        if (args->State->IsSelectPressed)
        {
            m_sourceState = args->State;
        }
    }
}
```

소멸자의 이벤트 처리기의 등록을 취소 해야 합니다. SpatialInputHandler.cpp:


```cpp
m_interactionManager->SourceUpdated -= m_sourcePressedEventToken;
```

를 컴파일하고 다시 배포 합니다. 이제 템플릿 프로젝트 위치 회전 큐브를 변경 하려면 감각을 상호 작용을 인식할 수. 있습니다

SpatialInteractionSource API는 다양 한 기능을 사용 하 여 컨트롤러를 지원합니다. 위의 예에서 사용 하 려 하기 전에 한 이해도 지원 하는지 확인 합니다. SpatialInteractionSource 일반적인 외 다음과 같은 선택적 기능이 지원 **선택** 키를 누릅니다.
* **메뉴 단추:** 지원 IsMenuSupported 속성을 검사 하 여 확인 합니다. 지원 되는 경우 확인 합니다 [SpatialInteractionSourceState::IsMenuPressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) 속성 확인 메뉴 단추를 누를 합니다.
* **단추를 이해 합니다.** 지원 IsGraspSupported 속성을 검사 하 여 확인 합니다. 지원는 때를 확인 합니다 [SpatialInteractionSourceState::IsGrasped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) 감각을 활성화 되어 있는지 확인 하려면 속성.

컨트롤러에 대 한는 SpatialInteractionSource 추가 기능을 사용 하 여 컨트롤러 속성이 있습니다.
* **HasThumbstick:** True 이면 컨트롤러에는 엄지 스틱 합니다. 검사는 [ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) 스틱을 가져오려고 SpatialInteractionSourceState 속성 x 및 y 값 (ThumbstickX 및 ThumbstickY) 뿐만 아니라 누름된 상태로 (IsThumbstickPressed).
* **HasTouchpad:** True 이면 컨트롤러에는 터치 패드를 있습니다. 터치 패드를 가져오려고 SpatialInteractionSourceState의 ControllerProperties 속성을 검사할 x 및 y 값 (TouchpadX 및 TouchpadY) 및 사용자 (IsTouchpadTouched) 패드 접촉 되어 및 터치 패드 (축소 키를 눌러는 경우 IsTouchpadPressed)입니다.
* **SimpleHapticsController:** SimpleHapticsController API 컨트롤러를 사용 하면 컨트롤러의 haptics 기능을 검사할 수 있습니다 하 고 햅 틱 피드백을 제어할 수도 있습니다.

터치 패드 및-1에서 엄지 스틱 (위쪽, 아래쪽에서 및 왼쪽에서 오른쪽) 양 축에 대 한 1의 범위입니다. SpatialInteractionSourceState::SelectPressedValue 속성을 사용 하 여 액세스할을 수 있는 아날로그 트리거에 대 한 범위는 0 ~ 1 범위를 있습니다. 값이 true로 같다고 IsSelectPressed와 1 상관 관계가 지정 다른 값 IsSelectPressed false 같지 않은지를 사용 하 여 상관 관계를 지정 합니다.

컨트롤러의 포인팅 광선을 나타내는 초래 하는 참고는 손 모양 및 컨트롤러가 모두 SpatialInteractionSourceState::Properties::TryGetLocation를 사용 하 여 사용자의 직접 위치를 제공 합니다-이것은 포인터가과 다릅니다. 손 모양 위치에 항목을 그릴 TryGetLocation을 사용 합니다. 컨트롤러의 팁에서 raycast 하려는 경우에 SpatialPointerPose TryGetInteractionSourcePose에서 가리키는 광선을 가져옵니다.

장치 보기 또는 준비 위치 (인덱스 palm 앞으로 사용 하 여 발생 손가락) 안팎에서 이동할 때 출입 바늘 때 반응 하거나 때 동작 SourceDetected 등 SourceLost, SpatialInteractionManager에서 다른 이벤트를 사용할 수도 있습니다. 컨트롤러 켜기/끄기 설정 또는 쌍을 이루는 짝이 없는 됩니다.

### <a name="grip-pose-vs-pointing-pose"></a>그립 포즈 포인팅 포즈 비교

Windows Mixed Reality 다양 한 폼 팩터 동작 컨트롤러에서는, 각 컨트롤러의 디자인을 사용 하 여 렌더링할 때 가리키는 사용 해야 다른 사용자의 직접 위치 사이의 "전달" 방향 해당 앱의 자연 관계를 컨트롤러입니다.

잘 표현 하기 위해 이러한 컨트롤러, 두 가지 종류의 포즈 각 상호 작용 원본에 대해 조사할 수 있습니다.
* 합니다 **그립 포즈**, HoloLens, 감지한 손 모양 손바닥 또는 동작 컨트롤러를 보유 하는 손 안에서 가능 위치를 나타내는입니다.
    * 몰입 형 헤드셋이이 포즈 가장 사용 렌더링 **사용자의 직접** 또는 **사용자의 직접에 보관 된 개체**검 또는 총 등입니다.
    * 합니다 **위치를 잡고**: 물론 컨트롤러를 보유 하는 경우 팜 중심 왼쪽 또는 오른쪽 가운데 그립 내의 위치를 조정 합니다.
    * 합니다 **방향을 올바른 축 잡고**: 완전히 플랫 5 손가락 자세를 직접 열면 광선과 표준 프로그램 palm에서 (왼쪽된 palm, palm 오른쪽에서 이전 버전과에서 앞으로)
    * 합니다 **방향을 정방향 축 잡고**: 부분적으로 (처럼 컨트롤러 보유) 직접을 닫을 때, 광선을 가리키는 "forward" 튜브를 통해 비 엄지 손가락으로 구성 합니다.
    * 합니다 **축 위쪽 방향 잡고**: 오른쪽 정방향 정의 사용 권한에 포함 된 최대 축.
    * 그립 자세를 통해 액세스할 수 있습니다 [SpatialInteractionSourceState.Properties.TryGetLocation(...) ](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).
* 합니다 **포인터 포즈**, 앞으로 가리키는 컨트롤러의 끝을 나타내는입니다.
    * 이 포즈 raycast에 가장 적합 하면 **UI를 가리키는** 컨트롤러 모델 자체를 렌더링 하는 경우.
    * 포인터 자세를 통해 액세스할 수 있습니다 [SpatialInteractionSourceState.Properties.TryGetLocation(...) 합니다. SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose) 또는 [SpatialInteractionSourceState.TryGetPointerPose(...) 합니다. TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_)합니다.

### <a name="composite-gestures-spatialgesturerecognizer"></a>복합 제스처의 경우: SpatialGestureRecognizer

A [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx) 해당 헤드 게이즈를 사용 하 여 어떤 사용자가 대상 화면 공간 제스처 이벤트에 실습, 동작 컨트롤러 및 "Select" 음성 명령에서 사용자 상호 작용을 해석 합니다.

공간 제스처는 Windows Mixed Reality 앱에 대 한 입력의 키 형식입니다. 라우팅 상호 작용을 SpatialInteractionManager에서 홀로그램의 SpatialGestureRecognizer 하 여 앱 수 탭, 보류, 조작 및 탐색 이벤트 감지 균일 하 게 바늘, 음성 및 공간 입력된 장치에서 누름을 처리 하지 않고도 수동으로 해제 합니다.

SpatialGestureRecognizer 요청 하는 제스처 집합 간의 최소 명확성에만 수행 합니다. 예를 들어,만 Tap를 요청 하는 경우 사용자 수 누른 해당 손가락 있기만 원하는 탭 계속 발생 합니다. 요청 하는 경우 모두 페이지를 누르고, 보류 승격 제스처는 해당 손가락 누르고의 보조에 대 한 후 탭을 더 이상 발생 합니다.

SpatialGestureRecognizer를 사용 하려면 SpatialInteractionManager의 처리할 [InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected) 이벤트 및 잡기를 SpatialPointerPose 노출 있습니다. 상호 작용 하려는 의도 하는 사용자가 확인 하기 위해 사용자의 환경 등에서 화면 메시 및 교차 하 여 홀로그램이이 포즈에서 사용자의 헤드 게이즈 광선을 사용 합니다. 그런 다음 대상 홀로그램의 SpatialGestureRecognizer 위해 이벤트 인수에는 SpatialInteraction 경로 사용 하 여 해당 [CaptureInteraction](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction) 메서드. 해석에 따라 해당 상호 작용이 시작 됩니다 합니다 [SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings) 생성 시-통하거나 해당 인식기 설정 [TrySetGestureSettings](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings)합니다.

HoloLens에서 상호 작용 및 제스처를 일반적으로 파생 되어야 해당 사용자의 헤드 게이즈를에서 대상으로 지정 하기 보다는 동안 렌더링 또는 손 모양 아이콘이 위치에 직접 상호 작용 합니다. 상호 작용 시작 된 후 조작 또는 탐색 제스처와 마찬가지로 제스처를 제어 하려면 손 모양 아이콘이의 상대적 동작을 사용할 수 있습니다.

## <a name="see-also"></a>참조
* [응시](gaze.md)
* [제스처](gestures.md)
* [컨트롤러 동작](motion-controllers.md)
