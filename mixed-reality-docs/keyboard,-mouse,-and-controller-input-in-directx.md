---
title: 키보드, 마우스 및 DirectX에서 컨트롤러 입력
description: Windows Mixed Reality 키보드, 마우스 및 게임 컨트롤러를 사용 하는 대 한 앱을 만드는 방법에 설명 합니다.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 키보드, 마우스, 게임 컨트롤러, 컨트롤러 xbox, HoloLens, 데스크톱, 연습, 샘플 코드
ms.openlocfilehash: 1e61cb50a561492fdc6849b5b231e97fab1bb6cf
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605087"
---
# <a name="keyboard-mouse-and-controller-input-in-directx"></a>키보드, 마우스 및 DirectX에서 컨트롤러 입력

키보드, 마우스 및 게임 컨트롤러 모두 유용한 형태의 Windows Mixed Reality 장치에 대 한 입력을 수 있습니다. Bluetooth 키보드 및 마우스는 모두에서 지원 HoloLens에 앱을 디버깅 하거나 대체 형식의 입력으로 사용 합니다. Windows Mixed Reality는 Pc-마우스, 키보드 및 게임 컨트롤러가 지금까지 표준 된 위치에 연결 하는 몰입 형 헤드셋도 지원 합니다.

HoloLens, 쌍 장치의 Bluetooth 키보드에서 키보드 입력을 사용 하려면 Windows Device Portal 통해 가상 입력을 사용 합니다. Windows Mixed Reality 몰입 형 헤드셋 착용 하는 동안 키보드 입력을 사용 하려면 입력된 포커스를 장치에 배치 하거나 Windows 키 + Y 키보드 조합을 사용 하 여 혼합 된 현실에 할당 합니다. HoloLens를 위한 앱 연결 된 이러한 장치 없이 기능을 입력 해야 한다는 것을 염두에 두십시오.

>[!NOTE]
>이 문서의 코드 조각 사용에 현재 방법을 보여 줍니다 C++/CX 대신 C + + 17 규격 C++/WinRT에 사용 되는 [ C++ holographic 프로젝트 템플릿을](creating-a-holographic-directx-project.md).  개념에 대 한 동일는 C++코드를 변환 해야 하지만 /WinRT 프로젝트입니다.

## <a name="subscribe-for-corewindow-input-events"></a>CoreWindow 입력된 이벤트에 대 한 구독

### <a name="keyboard-input"></a>키보드 입력

Windows Holographic 앱 템플릿에 다른 UWP 앱에서와 마찬가지로 키보드 입력에 대 한 이벤트 처리기를 포함 합니다. 앱에서 Windows Mixed Reality에서 동일한 방식으로 키보드 입력된 데이터를 사용 합니다.

AppView.cpp:

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
몰입 형 데스크톱 헤드셋에 대 한 몰입 형 보기를 통해 Windows에서 렌더링 하는 가상 키보드도 지원할 수 있습니다. 이 지원 하려면 앱 구현할 수 있습니다 **CoreTextEditContext**합니다. 따라서 Windows를 가상 키보드에 텍스트를 올바르게 기여할 수 있도록 사용자 고유의 앱 렌더링 된 입력란의 상태를 파악할 수 있습니다.

CoreTextEditContext 지원 구현에 대 한 자세한 내용은 참조는 [CoreTextEditContext 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl)합니다.

### <a name="mouse-input"></a>마우스 입력

또한 UWP CoreWindow 입력된 이벤트 처리기를 통해 다시 마우스 입력을 사용할 수 있습니다. 동일한 방식으로 누름된 제스처에서 마우스 클릭을 지원 하려면 Windows Holographic 앱 템플릿을 수정 하는 방법은 다음과 같습니다. 작업을 수행 하면 위치 몰입 형 헤드셋 장치를 착용 하는 동안 마우스 클릭이이 수정 큐브를 변경 합니다.

UWP 앱 데이터를 가져올 수도 원시 XY 마우스를 사용 하 여 확인 합니다 [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API.

AppView.h 새 OnPointerPressed 처리기를 선언 하 여 시작 합니다.

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

AppView.cpp에서 SetWindow에이 코드를 추가 합니다.

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

파일의 맨 아래에 OnPointerPressed에 대 한이 정의 넣습니다.

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

방금 추가한 이벤트 처리기가 템플릿 기본 클래스를 통과 합니다. 이 통과 지원 하기 위해 기본 클래스를 수정 해 보겠습니다. 헤더 파일에이 공용 메서드 선언을 추가 합니다.

```
// Handle mouse input.
       void OnPointerPressed();
```

이 전용 멤버 변수를 해야 합니다.

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

마지막으로, 기본 클래스의 마우스 클릭을 지원 하기 위해 새 논리를 사용 하 여 업데이트 됩니다. 이 이벤트 처리기를 추가 하 여 시작 합니다. 클래스 이름을 업데이트 해야 합니다.

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

이제 Update 메서드가 있고,이 사용 하 여 포인터 포즈를 가져오기 위한 기존 논리를 바꿉니다.

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

다시 컴파일하고 다시 배포 합니다. 마우스 클릭 연결 bluetooth 마우스를 사용 하 여 몰입 형 헤드셋-또는 HoloLens에서 큐브를 위치는 이제 유의 해야 합니다.

### <a name="game-controller-support"></a>게임 컨트롤러 지원

게임 컨트롤러는 재미 있고 편리한 방법은 사용자 수는 몰입 형 Windows Mixed Reality 환경을 제어할 수 있습니다.

Windows Holographic 앱 템플릿에 게임 컨트롤러에 대 한 지원을 추가 하는 첫 번째 단계는 다음과 같습니다. 주 파일에 대 한 헤더 클래스에 다음 private 멤버 선언을 추가합니다

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

Gamepad 이벤트 및 기본 클래스의 생성자에서 현재 연결 된 모든 게임 패드를 초기화 합니다.

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

기본 클래스에 이러한 이벤트 처리기를 추가 합니다. 클래스 이름을 업데이트 해야 합니다.

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

컨트롤러 상태에서 변경 내용을 인식 하려면 입력된 논리를 마지막으로 업데이트 합니다. 여기에서 마우스 이벤트를 추가 하는 것에 대 한 위 섹션에 설명 된 같은 m_pointerPressed 변수를 사용 합니다. Update 메서드를 SpatialPointerPose에 대 한 확인 하는 바로 앞에 추가 합니다.

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

기본 클래스를 정리할 때 이벤트 등록을 취소 하려면 두는 것을 잊지 마세요.

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

를 컴파일하고 다시 배포 합니다. 이제 연결 또는 쌍, 게임 컨트롤러를 회전 큐브 위치를 변경 하려면 사용 합니다.

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a>키보드 및 마우스 입력에 대 한 중요 한 지침

Windows Mixed Reality 지원 PC에서 사용할 수 있는 것과 자연 스러운 사용자 입력 – 주로 의존 하는 장치는 Microsoft HoloLens –에이 코드를 사용할 수 있는 방법을의 몇 가지 주요 차이점이 있습니다.
* 키보드 또는 마우스 입력이 있어야 사용할 수 없습니다. 앱의 기능을 모두 게이즈, 제스처 및 음성 입력을 사용 하 여 작동 해야 합니다.
* Bluetooth 키보드 연결 된 경우에 앱에 대 한 요청 받을 수 있는 모든 텍스트에 대 한 키보드 입력을 사용 하도록 설정 하려면 유용할 수 있습니다. 예를 들어 받아쓰기 기능에 대 한 훌륭한 보완 수 있습니다.
* 앱 디자인에 있어 WASD (예)에 의존 하지 않습니다 및 마우스 게임에 대 한 컨트롤을 찾습니다. HoloLens는 대화방 경비원 사용자를 위한 것입니다. 이 경우 사용자는 직접 카메라를 제어합니다. 카메라 이동/모양 컨트롤을 사용 하 여 전시실 촉진에 대 한 인터페이스는 동일한 환경을 제공 하지 않습니다.
* 키보드 입력 훌륭한 방법은 키보드를 사용 하는 사용자는 필요 하지는 특히 앱 또는 게임 엔진의 디버깅 측면을 제어할 수 있습니다. 이 연결 동일 CoreWindow 이벤트 Api 사용 하 여를 사용 하는 합니다. 이 시나리오에서는 디버그 세션 중 이벤트를 라우팅하도록 키보드 "만 입력 debug" 모드로 앱을 구성 하는 방법을 구현할 수 있습니다.
* Bluetooth 컨트롤러도 작동합니다.

## <a name="see-also"></a>참조
* [하드웨어 accessories](hardware-accessories.md)
