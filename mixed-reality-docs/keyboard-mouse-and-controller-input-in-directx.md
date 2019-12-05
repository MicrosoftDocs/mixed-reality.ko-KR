---
title: DirectX의 키보드, 마우스 및 컨트롤러 입력
description: 키보드, 마우스 및 게임 컨트롤러를 사용 하는 Windows Mixed Reality 용 응용 프로그램을 만드는 방법을 설명 합니다.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 키보드, 마우스, 게임 컨트롤러, xbox 컨트롤러, HoloLens, 데스크톱, 연습, 샘플 코드
ms.openlocfilehash: 1e61cb50a561492fdc6849b5b231e97fab1bb6cf
ms.sourcegitcommit: 05fa75193059a2dac4b580a9eef7b6c4bb64d8d7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74835099"
---
# <a name="keyboard-mouse-and-controller-input-in-directx"></a>DirectX의 키보드, 마우스 및 컨트롤러 입력

키보드, 마우스 및 게임 컨트롤러는 Windows Mixed Reality 장치에 대 한 유용한 형태의 입력으로 사용할 수 있습니다. Bluetooth 키보드와 마우스는 모두 HoloLens에서 지원 되며, 앱을 디버깅 하는 데 사용 하거나 다른 형식의 입력으로 사용할 수 있습니다. Windows Mixed Reality는 Pc에 연결 된 몰입 형 헤드셋도 지원 합니다. 즉, 마우스, 키보드 및 게임 컨트롤러가 일반적으로 일반적입니다.

HoloLens에서 키보드 입력을 사용 하려면 Bluetooth 키보드를 장치에 페어링 하거나 Windows 장치 포털을 통해 가상 입력을 사용 합니다. Windows Mixed Reality 몰입 형 헤드셋을 사용 하 여 키보드 입력을 사용 하려면 장치에 배치 하거나 Windows 키 + Y 키보드 조합을 사용 하 여 혼합 현실에 입력 포커스를 할당 합니다. HoloLens 용 앱은 이러한 장치를 연결 하지 않고도 기능을 제공 해야 합니다.

>[!NOTE]
>이 문서의 코드 조각은 현재 [ C++ holographic 프로젝트 템플릿에](creating-a-holographic-directx-project.md)사용 되 C++는 것 처럼 C + 17-so-far working 규격 C++/winrt 대신/cx 사용을 보여 줍니다.  개념은 C++/winrt 프로젝트와 동일 하지만 코드를 변환 해야 합니다.

## <a name="subscribe-for-corewindow-input-events"></a>CoreWindow 입력 이벤트 구독

### <a name="keyboard-input"></a>키보드 입력

Windows Holographic 앱 템플릿에서는 다른 UWP 앱과 마찬가지로 키보드 입력에 대 한 이벤트 처리기를 포함 합니다. 앱은 Windows Mixed Reality에서 키보드 입력 데이터를 동일한 방식으로 사용 합니다.

AppView .cpp에서:

```
// Register for keypress notifications.
   window->KeyDown +=
       ref new TypedEventHandler<CoreWindow^, KeyEventArgs^>(this, &AppView::OnKeyPressed);

    …

   // Input event handlers

   void AppView::OnKeyPressed(CoreWindow^ sender, KeyEventArgs^ args)
   {
       //
       // TODO: Respond to keyboard input here.
       //
   }
```

### <a name="virtual-keyboard-input"></a>가상 키보드 입력
몰입 형 데스크톱 헤드셋의 경우 몰입 형 보기를 통해 Windows에서 렌더링 한 가상 키보드를 지원할 수도 있습니다. 이를 지원 하기 위해 앱은 **Coretexteditcontext**를 구현할 수 있습니다. 이렇게 하면 Windows에서 사용자 고유의 앱 렌더링 텍스트 상자의 상태를 이해할 수 있으므로 가상 키보드에서 해당 텍스트 상자의 상태를 올바르게 적용할 수 있습니다.

CoreTextEditContext 지원 구현에 대 한 자세한 내용은 [coretexteditcontext 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl)을 참조 하세요.

### <a name="mouse-input"></a>마우스 입력

UWP CoreWindow 입력 이벤트 처리기를 통해 마우스 입력을 다시 사용할 수도 있습니다. 누름 제스처와 동일한 방식으로 마우스 클릭을 지원 하도록 Windows Holographic 앱 템플릿을 수정 하는 방법은 다음과 같습니다. 이렇게 수정한 후에는 몰입 형 헤드셋 장치를 작성 하는 동안 마우스를 클릭 하면 큐브의 위치가 변경 됩니다.

UWP 앱은 [Mousedevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API를 사용 하 여 마우스용 원시 XY 데이터를 가져올 수도 있습니다.

AppView. h에서 새 OnPointerPressed 처리기를 선언 하 여 시작 합니다.

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

AppView .cpp에서이 코드를 SetWindow에 추가 합니다.

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

그런 다음 파일의 아래쪽에 OnPointerPressed이 정의를 추가 합니다.

```
void AppView::OnPointerPressed(CoreWindow^ sender, PointerEventArgs^ args)
   {
       // Allow the user to interact with the holographic world using the mouse.
       if (m_main != nullptr)
       {
           m_main->OnPointerPressed();
       }
   }
```

방금 추가한 이벤트 처리기는 템플릿 주 클래스에 대 한 통과입니다. 이 통과를 지원 하도록 주 클래스를 수정 하겠습니다. 헤더 파일에이 공용 메서드 선언을 추가 합니다.

```
// Handle mouse input.
       void OnPointerPressed();
```

이 private 멤버 변수도 필요 합니다.

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

마지막으로 마우스 클릭을 지원 하기 위해 새 논리를 사용 하 여 주 클래스를 업데이트 합니다. 이 이벤트 처리기를 추가 하 여 시작 합니다. 클래스 이름을 업데이트 해야 합니다.

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

이제 Update 메서드에서 포인터가 포즈를 가져오기 위해 기존 논리를 다음과 같이 바꿉니다.

```
SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   SpatialPointerPose^ pose = nullptr;
   if (pointerState != nullptr)
   {
       pose = pointerState->TryGetPointerPose(currentCoordinateSystem);
   }
   else if (m_pointerPressed)
   {
       pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
   }
   m_pointerPressed = false;
```

다시 컴파일하고 다시 배포 합니다. 이제 마우스 클릭이 몰입 형 헤드셋에서 큐브 위치를 변경 하는 것을 확인할 수 있으며, bluetooth 마우스가 연결 되어 있습니다.

### <a name="game-controller-support"></a>게임 컨트롤러 지원

게임 컨트롤러는 사용자가 몰입 형 Windows Mixed Reality 환경을 제어할 수 있게 하는 재미 있고 편리한 방법일 수 있습니다.

Windows Holographic 앱 템플릿에 게임 컨트롤러에 대 한 지원을 추가 하는 첫 번째 단계는 기본 파일에 대 한 헤더 클래스에 다음 전용 멤버 선언을 추가 하는 것입니다.

```
// Recognize gamepads that are plugged in after the app starts.
       void OnGamepadAdded(Platform::Object^, Windows::Gaming::Input::Gamepad^ args);
```

```
// Stop looking for gamepads that are unplugged.
       void OnGamepadRemoved(Platform::Object^, Windows::Gaming::Input::Gamepad^ args);
```

```
Windows::Foundation::EventRegistrationToken                     m_gamepadAddedEventToken;
       Windows::Foundation::EventRegistrationToken                     m_gamepadRemovedEventToken;
```

```
// Keeps track of a gamepad and the state of its A button.
       struct GamepadWithButtonState
       {
           Windows::Gaming::Input::Gamepad^ gamepad;
           bool buttonAWasPressedLastFrame = false;
       };
       std::vector<GamepadWithButtonState>                             m_gamepads;
```

주 클래스의 생성자에서 게임 패드 이벤트와 현재 연결 되어 있는 모든 gamepads를 초기화 합니다.

```
// If connected, a game controller can also be used for input.
   m_gamepadAddedEventToken = Gamepad::GamepadAdded +=
       ref new EventHandler<Gamepad^>(
           bind(&$safeprojectname$Main::OnGamepadAdded, this, _1, _2)
           );
```

```
m_gamepadRemovedEventToken = Gamepad::GamepadRemoved +=
       ref new EventHandler<Gamepad^>(
           bind(&$safeprojectname$Main::OnGamepadRemoved, this, _1, _2)
           );
```

```
for (auto const& gamepad : Gamepad::Gamepads)
   {
       OnGamepadAdded(nullptr, gamepad);
   }
```

이러한 이벤트 처리기를 기본 클래스에 추가 합니다. 클래스 이름을 업데이트 해야 합니다.

```
void MyHolographicAppMain::OnGamepadAdded(Object^, Gamepad^ args)
   {
       for (auto const& gamepadWithButtonState : m_gamepads)
       {
           if (args == gamepadWithButtonState.gamepad)
           {
               // This gamepad is already in the list.
               return;
           }
       }
       m_gamepads.push_back({ args, false });
   }
```

```
void MyHolographicAppMain::OnGamepadRemoved(Object^, Gamepad^ args)
   {
       m_gamepads.erase(
           std::remove_if(m_gamepads.begin(), m_gamepads.end(), [&](GamepadWithButtonState& gamepadWithState)
               {
                   return gamepadWithState.gamepad == args;
               }),
           m_gamepads.end());
   }
```

마지막으로, 컨트롤러 상태의 변경 내용을 인식 하도록 입력 논리를 업데이트 합니다. 여기서는 마우스 이벤트를 추가 하기 위해 위의 섹션에서 설명한 것과 동일한 m_pointerPressed 변수를 사용 합니다. 이를 업데이트 메서드에 SpatialPointerPose를 확인 하는 위치 바로 앞에 추가 합니다.

```
// Check for new input state since the last frame.
   for (auto& gamepadWithButtonState : m_gamepads)
   {
       bool buttonDownThisUpdate = ((gamepadWithButtonState.gamepad->GetCurrentReading().Buttons & GamepadButtons::A) == GamepadButtons::A);
       if (buttonDownThisUpdate && !gamepadWithButtonState.buttonAWasPressedLastFrame)
       {
           m_pointerPressed = true;
       }
       gamepadWithButtonState.buttonAWasPressedLastFrame = buttonDownThisUpdate;
   }
```

```
// For context.
   SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   SpatialPointerPose^ pose = nullptr;
   if (pointerState != nullptr)
   {
       pose = pointerState->TryGetPointerPose(currentCoordinateSystem);
   }
   else if (m_pointerPressed)
   {
       pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
   }
   m_pointerPressed = false;
```

주 클래스를 정리할 때 이벤트의 등록을 취소 해야 합니다.

```
if (m_gamepadAddedEventToken.Value != 0)
   {
       Gamepad::GamepadAdded -= m_gamepadAddedEventToken;
   }
   if (m_gamepadRemovedEventToken.Value != 0)
   {
       Gamepad::GamepadRemoved -= m_gamepadRemovedEventToken;
   }
```

다시 컴파일하고 다시 배포 합니다. 이제 게임 컨트롤러를 연결 하거나 페어링 하 고이를 사용 하 여 회전 하는 큐브를 재배치할 수 있습니다.

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a>키보드 및 마우스 입력에 대 한 중요 한 지침

Microsoft HoloLens에서이 코드를 사용 하는 방법에는 몇 가지 중요 한 차이점이 있습니다 .이는 주로 자연 사용자 입력을 사용 하는 장치 이며 Windows Mixed Reality 사용 PC에서 사용할 수 있는 장치입니다.
* 키보드 또는 마우스 입력을 사용 하 여 표시할 수 없습니다. 모든 앱 기능은 응시, 제스처 및 음성 입력을 사용 해야 합니다.
* Bluetooth 키보드가 연결 되 면 앱에서 요청할 수 있는 텍스트에 대해 키보드 입력을 사용 하도록 설정 하는 것이 유용할 수 있습니다. 예를 들어이는 받아쓰기에 유용한 보조가 될 수 있습니다.
* 앱을 디자인 하는 경우에는 게임에 대 한 WASD 및 마우스 모양 컨트롤을 사용 하지 마세요. HoloLens는 사용자가 대화방을 탐색할 수 있도록 설계 되었습니다. 이 경우 사용자는 카메라를 직접 제어 합니다. 이동/보기 컨트롤을 사용 하 여 실내를 중심으로 카메라를 구동 하는 인터페이스는 동일한 환경을 제공 하지 않습니다.
* 키보드 입력은 특히 사용자가 키보드를 사용할 필요가 없기 때문에 앱 또는 게임 엔진의 디버깅 측면을 제어 하는 뛰어난 방법일 수 있습니다. CoreWindow 이벤트 Api를 사용 하 여 연결 하는 것과 동일 합니다. 이 시나리오에서는 디버그 세션 중에 키보드 이벤트를 "디버그 입력 전용" 모드로 라우팅하도록 앱을 구성 하는 방법을 구현 하도록 선택할 수 있습니다.
* Bluetooth 컨트롤러도 작동 합니다.

## <a name="see-also"></a>참고 항목
* [하드웨어 액세서리](hardware-accessories.md)
