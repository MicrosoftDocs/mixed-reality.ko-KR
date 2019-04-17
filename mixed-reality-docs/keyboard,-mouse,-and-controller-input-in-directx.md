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
# <a name="keyboard-mouse-and-controller-input-in-directx"></a><span data-ttu-id="3c963-104">키보드, 마우스 및 DirectX에서 컨트롤러 입력</span><span class="sxs-lookup"><span data-stu-id="3c963-104">Keyboard, mouse, and controller input in DirectX</span></span>

<span data-ttu-id="3c963-105">키보드, 마우스 및 게임 컨트롤러 모두 유용한 형태의 Windows Mixed Reality 장치에 대 한 입력을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-105">Keyboards, mice, and game controllers can all be useful forms of input for Windows Mixed Reality devices.</span></span> <span data-ttu-id="3c963-106">Bluetooth 키보드 및 마우스는 모두에서 지원 HoloLens에 앱을 디버깅 하거나 대체 형식의 입력으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-106">Bluetooth keyboards and mice are both supported on HoloLens, for use with debugging your app or as an alternate form of input.</span></span> <span data-ttu-id="3c963-107">Windows Mixed Reality는 Pc-마우스, 키보드 및 게임 컨트롤러가 지금까지 표준 된 위치에 연결 하는 몰입 형 헤드셋도 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-107">Windows Mixed Reality also supports immersive headsets attached to PCs - where mice, keyboards, and game controllers have historically been the norm.</span></span>

<span data-ttu-id="3c963-108">HoloLens, 쌍 장치의 Bluetooth 키보드에서 키보드 입력을 사용 하려면 Windows Device Portal 통해 가상 입력을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-108">To use keyboard input on HoloLens, pair a Bluetooth keyboard to your device or use virtual input via the Windows Device Portal.</span></span> <span data-ttu-id="3c963-109">Windows Mixed Reality 몰입 형 헤드셋 착용 하는 동안 키보드 입력을 사용 하려면 입력된 포커스를 장치에 배치 하거나 Windows 키 + Y 키보드 조합을 사용 하 여 혼합 된 현실에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-109">To use keyboard input while wearing a Windows Mixed Reality immersive headset, assign input focus to mixed reality by putting on the device or using the Windows Key + Y keyboard combination.</span></span> <span data-ttu-id="3c963-110">HoloLens를 위한 앱 연결 된 이러한 장치 없이 기능을 입력 해야 한다는 것을 염두에 두십시오.</span><span class="sxs-lookup"><span data-stu-id="3c963-110">Keep in mind that apps intended for HoloLens must provide functionality without these devices attached.</span></span>

>[!NOTE]
><span data-ttu-id="3c963-111">이 문서의 코드 조각 사용에 현재 방법을 보여 줍니다 C++/CX 대신 C + + 17 규격 C++/WinRT에 사용 되는 [ C++ holographic 프로젝트 템플릿을](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="3c963-111">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="3c963-112">개념에 대 한 동일는 C++코드를 변환 해야 하지만 /WinRT 프로젝트입니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-112">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="subscribe-for-corewindow-input-events"></a><span data-ttu-id="3c963-113">CoreWindow 입력된 이벤트에 대 한 구독</span><span class="sxs-lookup"><span data-stu-id="3c963-113">Subscribe for CoreWindow input events</span></span>

### <a name="keyboard-input"></a><span data-ttu-id="3c963-114">키보드 입력</span><span class="sxs-lookup"><span data-stu-id="3c963-114">Keyboard input</span></span>

<span data-ttu-id="3c963-115">Windows Holographic 앱 템플릿에 다른 UWP 앱에서와 마찬가지로 키보드 입력에 대 한 이벤트 처리기를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-115">In the Windows Holographic app template, we include an event handler for keyboard input just like any other UWP app.</span></span> <span data-ttu-id="3c963-116">앱에서 Windows Mixed Reality에서 동일한 방식으로 키보드 입력된 데이터를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-116">Your app consumes keyboard input data the same way in Windows Mixed Reality.</span></span>

<span data-ttu-id="3c963-117">AppView.cpp:</span><span class="sxs-lookup"><span data-stu-id="3c963-117">From AppView.cpp:</span></span>

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

### <a name="virtual-keyboard-input"></a><span data-ttu-id="3c963-118">가상 키보드 입력</span><span class="sxs-lookup"><span data-stu-id="3c963-118">Virtual keyboard input</span></span>
<span data-ttu-id="3c963-119">몰입 형 데스크톱 헤드셋에 대 한 몰입 형 보기를 통해 Windows에서 렌더링 하는 가상 키보드도 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-119">For immersive desktop headsets, you can also support virtual keyboards rendered by Windows over your immersive view.</span></span> <span data-ttu-id="3c963-120">이 지원 하려면 앱 구현할 수 있습니다 **CoreTextEditContext**합니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-120">To support this, your app can implement **CoreTextEditContext**.</span></span> <span data-ttu-id="3c963-121">따라서 Windows를 가상 키보드에 텍스트를 올바르게 기여할 수 있도록 사용자 고유의 앱 렌더링 된 입력란의 상태를 파악할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-121">This lets Windows understand the state of your own app-rendered text boxes, so the virtual keyboard can correctly contribute to the text there.</span></span>

<span data-ttu-id="3c963-122">CoreTextEditContext 지원 구현에 대 한 자세한 내용은 참조는 [CoreTextEditContext 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl)합니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-122">For more information on implementing CoreTextEditContext support, see the [CoreTextEditContext sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span></span>

### <a name="mouse-input"></a><span data-ttu-id="3c963-123">마우스 입력</span><span class="sxs-lookup"><span data-stu-id="3c963-123">Mouse Input</span></span>

<span data-ttu-id="3c963-124">또한 UWP CoreWindow 입력된 이벤트 처리기를 통해 다시 마우스 입력을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-124">You can also use mouse input, again via the UWP CoreWindow input event handlers.</span></span> <span data-ttu-id="3c963-125">동일한 방식으로 누름된 제스처에서 마우스 클릭을 지원 하려면 Windows Holographic 앱 템플릿을 수정 하는 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-125">Here's how to modify the Windows Holographic app template to support mouse clicks in the same way as pressed gestures.</span></span> <span data-ttu-id="3c963-126">작업을 수행 하면 위치 몰입 형 헤드셋 장치를 착용 하는 동안 마우스 클릭이이 수정 큐브를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-126">After making this modification, a mouse click while wearing an immersive headset device will reposition the cube.</span></span>

<span data-ttu-id="3c963-127">UWP 앱 데이터를 가져올 수도 원시 XY 마우스를 사용 하 여 확인 합니다 [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API.</span><span class="sxs-lookup"><span data-stu-id="3c963-127">Note that UWP apps can also get raw XY data for the mouse by using the [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API.</span></span>

<span data-ttu-id="3c963-128">AppView.h 새 OnPointerPressed 처리기를 선언 하 여 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-128">Start by declaring a new OnPointerPressed handler in AppView.h:</span></span>

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

<span data-ttu-id="3c963-129">AppView.cpp에서 SetWindow에이 코드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-129">In AppView.cpp, add this code to SetWindow:</span></span>

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

<span data-ttu-id="3c963-130">파일의 맨 아래에 OnPointerPressed에 대 한이 정의 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-130">Then put this definition for OnPointerPressed at the bottom of the file:</span></span>

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

<span data-ttu-id="3c963-131">방금 추가한 이벤트 처리기가 템플릿 기본 클래스를 통과 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-131">The event handler we just added is a pass-through to the template main class.</span></span> <span data-ttu-id="3c963-132">이 통과 지원 하기 위해 기본 클래스를 수정 해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-132">Let's modify the main class to support this pass-through.</span></span> <span data-ttu-id="3c963-133">헤더 파일에이 공용 메서드 선언을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-133">Add this public method declaration to the header file:</span></span>

```
// Handle mouse input.
       void OnPointerPressed();
```

<span data-ttu-id="3c963-134">이 전용 멤버 변수를 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-134">You'll need this private member variable, as well:</span></span>

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

<span data-ttu-id="3c963-135">마지막으로, 기본 클래스의 마우스 클릭을 지원 하기 위해 새 논리를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-135">Finally, we will update the main class with new logic to support mouse clicks.</span></span> <span data-ttu-id="3c963-136">이 이벤트 처리기를 추가 하 여 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-136">Start by adding this event handler.</span></span> <span data-ttu-id="3c963-137">클래스 이름을 업데이트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-137">Make sure to update the class name:</span></span>

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

<span data-ttu-id="3c963-138">이제 Update 메서드가 있고,이 사용 하 여 포인터 포즈를 가져오기 위한 기존 논리를 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-138">Now, in the Update method, replace the existing logic for getting a pointer pose with this:</span></span>

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

<span data-ttu-id="3c963-139">다시 컴파일하고 다시 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-139">Recompile and redeploy.</span></span> <span data-ttu-id="3c963-140">마우스 클릭 연결 bluetooth 마우스를 사용 하 여 몰입 형 헤드셋-또는 HoloLens에서 큐브를 위치는 이제 유의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-140">You should notice that the mouse click will now reposition the cube in your immersive headset - or HoloLens with bluetooth mouse attached.</span></span>

### <a name="game-controller-support"></a><span data-ttu-id="3c963-141">게임 컨트롤러 지원</span><span class="sxs-lookup"><span data-stu-id="3c963-141">Game controller support</span></span>

<span data-ttu-id="3c963-142">게임 컨트롤러는 재미 있고 편리한 방법은 사용자 수는 몰입 형 Windows Mixed Reality 환경을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-142">Game controllers can be a fun and convenient way of allowing the user to control an immersive Windows Mixed Reality experience.</span></span>

<span data-ttu-id="3c963-143">Windows Holographic 앱 템플릿에 게임 컨트롤러에 대 한 지원을 추가 하는 첫 번째 단계는 다음과 같습니다. 주 파일에 대 한 헤더 클래스에 다음 private 멤버 선언을 추가합니다</span><span class="sxs-lookup"><span data-stu-id="3c963-143">The first step in adding support for game controllers to the Windows Holographic app template, is to add the following private member declarations to the header class for your main file:</span></span>

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

<span data-ttu-id="3c963-144">Gamepad 이벤트 및 기본 클래스의 생성자에서 현재 연결 된 모든 게임 패드를 초기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-144">Initialize gamepad events, and any gamepads that are currently attached, in the constructor for your main class:</span></span>

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

<span data-ttu-id="3c963-145">기본 클래스에 이러한 이벤트 처리기를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-145">Add these event handlers to your main class.</span></span> <span data-ttu-id="3c963-146">클래스 이름을 업데이트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-146">Make sure to update the class name:</span></span>

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

<span data-ttu-id="3c963-147">컨트롤러 상태에서 변경 내용을 인식 하려면 입력된 논리를 마지막으로 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-147">Finally, update the input logic to recognize changes in controller state.</span></span> <span data-ttu-id="3c963-148">여기에서 마우스 이벤트를 추가 하는 것에 대 한 위 섹션에 설명 된 같은 m_pointerPressed 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-148">Here, we use the same m_pointerPressed variable discussed in the section above for adding mouse events.</span></span> <span data-ttu-id="3c963-149">Update 메서드를 SpatialPointerPose에 대 한 확인 하는 바로 앞에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-149">Add this to the Update method, just before where it checks for the SpatialPointerPose:</span></span>

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

<span data-ttu-id="3c963-150">기본 클래스를 정리할 때 이벤트 등록을 취소 하려면 두는 것을 잊지 마세요.</span><span class="sxs-lookup"><span data-stu-id="3c963-150">Don't forget to unregister the events when cleaning up the main class:</span></span>

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

<span data-ttu-id="3c963-151">를 컴파일하고 다시 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-151">Recompile, and redeploy.</span></span> <span data-ttu-id="3c963-152">이제 연결 또는 쌍, 게임 컨트롤러를 회전 큐브 위치를 변경 하려면 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-152">You can now attach, or pair, a game controller and use it to reposition the spinning cube.</span></span>

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a><span data-ttu-id="3c963-153">키보드 및 마우스 입력에 대 한 중요 한 지침</span><span class="sxs-lookup"><span data-stu-id="3c963-153">Important guidelines for keyboard and mouse input</span></span>

<span data-ttu-id="3c963-154">Windows Mixed Reality 지원 PC에서 사용할 수 있는 것과 자연 스러운 사용자 입력 – 주로 의존 하는 장치는 Microsoft HoloLens –에이 코드를 사용할 수 있는 방법을의 몇 가지 주요 차이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-154">There are some key differences in how this code can be used on Microsoft HoloLens – which is a device that relies primarily on natural user input – versus what is available on a Windows Mixed Reality-enabled PC.</span></span>
* <span data-ttu-id="3c963-155">키보드 또는 마우스 입력이 있어야 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-155">You can’t rely on keyboard or mouse input to be present.</span></span> <span data-ttu-id="3c963-156">앱의 기능을 모두 게이즈, 제스처 및 음성 입력을 사용 하 여 작동 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-156">All of your app's functionality must work with gaze, gesture, and speech input.</span></span>
* <span data-ttu-id="3c963-157">Bluetooth 키보드 연결 된 경우에 앱에 대 한 요청 받을 수 있는 모든 텍스트에 대 한 키보드 입력을 사용 하도록 설정 하려면 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-157">When a Bluetooth keyboard is attached, it can be helpful to enable keyboard input for any text that your app might ask for.</span></span> <span data-ttu-id="3c963-158">예를 들어 받아쓰기 기능에 대 한 훌륭한 보완 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-158">This can be a great supplement for dictation, for example.</span></span>
* <span data-ttu-id="3c963-159">앱 디자인에 있어 WASD (예)에 의존 하지 않습니다 및 마우스 게임에 대 한 컨트롤을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-159">When it comes to designing your app, don’t rely on (for example) WASD and mouse look controls for your game.</span></span> <span data-ttu-id="3c963-160">HoloLens는 대화방 경비원 사용자를 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-160">HoloLens is designed for the user to walk around the room.</span></span> <span data-ttu-id="3c963-161">이 경우 사용자는 직접 카메라를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-161">In this case, the user controls the camera directly.</span></span> <span data-ttu-id="3c963-162">카메라 이동/모양 컨트롤을 사용 하 여 전시실 촉진에 대 한 인터페이스는 동일한 환경을 제공 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-162">An interface for driving the camera around the room with move/look controls won't provide the same experience.</span></span>
* <span data-ttu-id="3c963-163">키보드 입력 훌륭한 방법은 키보드를 사용 하는 사용자는 필요 하지는 특히 앱 또는 게임 엔진의 디버깅 측면을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-163">Keyboard input can be an excellent way to control the debugging aspects of your app or game engine, especially since the user will not be required to use the keyboard.</span></span> <span data-ttu-id="3c963-164">이 연결 동일 CoreWindow 이벤트 Api 사용 하 여를 사용 하는 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-164">Wiring it up is the same as you're used to, with CoreWindow event APIs.</span></span> <span data-ttu-id="3c963-165">이 시나리오에서는 디버그 세션 중 이벤트를 라우팅하도록 키보드 "만 입력 debug" 모드로 앱을 구성 하는 방법을 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-165">In this scenario, you might choose to implement a way to configure your app to route keyboard events to a "debug input only" mode during your debug sessions.</span></span>
* <span data-ttu-id="3c963-166">Bluetooth 컨트롤러도 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="3c963-166">Bluetooth controllers work as well.</span></span>

## <a name="see-also"></a><span data-ttu-id="3c963-167">참조</span><span class="sxs-lookup"><span data-stu-id="3c963-167">See also</span></span>
* [<span data-ttu-id="3c963-168">하드웨어 accessories</span><span class="sxs-lookup"><span data-stu-id="3c963-168">Hardware accessories</span></span>](hardware-accessories.md)
