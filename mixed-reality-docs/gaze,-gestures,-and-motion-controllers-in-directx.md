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
# <a name="gaze-gestures-and-motion-controllers-in-directx"></a><span data-ttu-id="5a308-104">응시, 제스처 및 DirectX에서 동작 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="5a308-104">Gaze, gestures, and motion controllers in DirectX</span></span>

<span data-ttu-id="5a308-105">플랫폼을 기반으로 직접 작성 하려는 경우 입력된을 통해 사용자가 보는 위치와 같은 사용자에서 제공 하는 것을 처리 해야 합니다 [헤드 게이즈](gaze.md) 및 사용자가 사용 하 여 선택한 [제스처](gestures.md) 또는 [컨트롤러 동작](motion-controllers.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-105">If you're going to build directly on top of the platform, you will have to handle input coming from the user - such as where the user is looking via [head gaze](gaze.md) and what the user has selected with [gestures](gestures.md) or [motion controllers](motion-controllers.md).</span></span> <span data-ttu-id="5a308-106">이러한 형태의 입력을 결합 적용할 사용자를 설정할 수 있습니다.는 [홀로그램](hologram.md) 앱에서.</span><span class="sxs-lookup"><span data-stu-id="5a308-106">Combining these forms of input, you can enable a user to place a [hologram](hologram.md) in your app.</span></span> <span data-ttu-id="5a308-107">합니다 [holographic 앱 템플릿](creating-a-holographic-directx-project.md) 사용 하기 쉬운 예제가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-107">The [holographic app template](creating-a-holographic-directx-project.md) has an easy to use example.</span></span>

>[!NOTE]
><span data-ttu-id="5a308-108">이 문서의 코드 조각 사용에 현재 방법을 보여 줍니다 C++/CX 대신 C + + 17 규격 C++/WinRT에 사용 되는 [ C++ holographic 프로젝트 템플릿을](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="5a308-108">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="5a308-109">개념에 대 한 동일는 C++코드를 변환 해야 하지만 /WinRT 프로젝트입니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-109">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="gaze-input"></a><span data-ttu-id="5a308-110">응시 입력</span><span class="sxs-lookup"><span data-stu-id="5a308-110">Gaze input</span></span>

<span data-ttu-id="5a308-111">사용자의 액세스 [헤드 게이즈](gaze.md)를 사용 합니다 [SpatialPointerPose](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialpointerpose.aspx) 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-111">To access the user's [head gaze](gaze.md), you use the [SpatialPointerPose](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialpointerpose.aspx) type.</span></span> <span data-ttu-id="5a308-112">Holographic 앱 템플릿 이해 응시에 대 한 기본 코드를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-112">The holographic app template includes basic code for understanding gaze.</span></span> <span data-ttu-id="5a308-113">이 코드에서는 사용자의 눈에 장치 위치와 방향에 고려 사이 있는 앞으로 가리키는 벡터는 주어진 [좌표계](coordinate-systems-in-directx.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-113">This code provides a vector pointing forward from between the user's eyes, taking into account the device's position and orientation in a given [coordinate system](coordinate-systems-in-directx.md).</span></span>




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

<span data-ttu-id="5a308-114">요청을 사용할 수 있습니다. "하지만 어디 좌표계에서 가져옵니까"?</span><span class="sxs-lookup"><span data-stu-id="5a308-114">You may find yourself asking: "But where does the coordinate system come from?"</span></span>

<span data-ttu-id="5a308-115">해당 질문에 대답 해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-115">Let's answer that question.</span></span> <span data-ttu-id="5a308-116">우리의 AppMain **업데이트** 함수 처리 공간 입력된 이벤트를 우리의 StationaryFrameOfReference에 대 한 좌표 시스템을 기준으로 확보 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-116">In our AppMain's **Update** function, we processed a spatial input event by acquiring it relative to the coordinate system for our StationaryFrameOfReference.</span></span> <span data-ttu-id="5a308-117">설정 하는 경우는 StationaryFrameOfReference 만들어졌는지 회수 합니다 [HolographicSpace](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx), 좌표 시스템의 시작 부분에 획득 하 고 [업데이트](rendering-in-directx.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-117">Recall that the StationaryFrameOfReference was created when we set up the [HolographicSpace](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx), and the coordinate system was acquired at the start of [Update](rendering-in-directx.md).</span></span>




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

<span data-ttu-id="5a308-118">데이터는 일종의 포인터 상태 관련이 참고 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-118">Note that the data is tied to a pointer state of some kind.</span></span> <span data-ttu-id="5a308-119">에서는 공간 입력된 이벤트에서 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-119">We get this from a spatial input event.</span></span> <span data-ttu-id="5a308-120">이벤트 데이터 개체는 좌표계 포함 되므로 항상 이벤트 시 게이즈 방향을 해야 모든 공간 좌표계에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-120">The event data object includes a coordinate system, so that you can always relate the gaze direction at the time of the event to whatever spatial coordinate system you need.</span></span> <span data-ttu-id="5a308-121">실제로 포인터 자세를 가져오기 위해 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-121">In fact, you must do so in order to get the pointer pose.</span></span>

> [!NOTE]
> <span data-ttu-id="5a308-122">HoloLens 2 관련 된 자세한 지침 [예정](index.md#news-and-notes)합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-122">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

## <a name="gesture-and-motion-controller-input"></a><span data-ttu-id="5a308-123">입력 제스처 및 중인 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="5a308-123">Gesture and motion controller input</span></span>

<span data-ttu-id="5a308-124">Windows Mixed Reality에 모두 전달 [제스처](gestures.md) 하 고 [컨트롤러 동작](motion-controllers.md) 있는 동일한 공간 입력 Api 통해 처리 됩니다는 [Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial) 네임 스페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-124">In Windows Mixed Reality, both hand [gestures](gestures.md) and [motion controllers](motion-controllers.md) are handled through the same spatial input APIs, found in the [Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial) namespace.</span></span> <span data-ttu-id="5a308-125">쉽게 등의 일반적인 작업을 처리할 수 있습니다 **선택** 실습 및 동작 컨트롤러 모두에서 동일한 방식으로 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-125">This enables you to easily handle common actions like **Select** presses the same way across both hands and motion controllers.</span></span>

<span data-ttu-id="5a308-126">혼합된 현실에서 제스처 또는 컨트롤러 동작을 처리할 때 대상 API의 두 가지 수준이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-126">There are two levels of API you can target when handling gestures or motion controllers in mixed reality:</span></span>
* <span data-ttu-id="5a308-127">[상호 작용](gestures.md#the-two-core-gestures-of-hololens) ([SourcePressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed.aspx)를 [SourceReleased](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased.aspx) 하 고 [SourceUpdated](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated.aspx))를 사용 하 여 액세스를 [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx)</span><span class="sxs-lookup"><span data-stu-id="5a308-127">[Interactions](gestures.md#the-two-core-gestures-of-hololens) ([SourcePressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed.aspx), [SourceReleased](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased.aspx) and [SourceUpdated](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated.aspx)), accessed using a [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx)</span></span>
* <span data-ttu-id="5a308-128">[복합 제스처](gestures.md#composite-gestures) ([Tapped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.tapped.aspx), 저장, 조작, 탐색)를 사용 하 여 액세스를 [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx)</span><span class="sxs-lookup"><span data-stu-id="5a308-128">[Composite gestures](gestures.md#composite-gestures) ([Tapped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.tapped.aspx), Hold, Manipulation, Navigation), accessed using a [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx)</span></span>

### <a name="selectmenugrasptouchpadthumbstick-interactions-spatialinteractionmanager"></a><span data-ttu-id="5a308-129">선택/메뉴/한결/터치 패드/엄지 스틱 상호 작용 합니다. SpatialInteractionManager</span><span class="sxs-lookup"><span data-stu-id="5a308-129">Select/Menu/Grasp/Touchpad/Thumbstick interactions: SpatialInteractionManager</span></span>

<span data-ttu-id="5a308-130">실습 및 Windows Mixed Reality의 입력된 장치에서 하위 수준 누름, 릴리스 및 업데이트를 검색 하려면에서 시작 된 [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx)합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-130">To detect low-level presses, releases and updates across hands and input devices in Windows Mixed Reality, you start from a [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx).</span></span> <span data-ttu-id="5a308-131">SpatialInteractionManager에 손 모양 때 응용 프로그램을 알리는 이벤트 또는 동작 컨트롤러 입력 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-131">The SpatialInteractionManager has an event that informs the app when a hand or motion controller has detected input.</span></span>

<span data-ttu-id="5a308-132">세 가지 주요 종류 SpatialInteractionSource의, 각각 다른 SpatialInteractionSourceKind 값으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-132">There are three key kinds of SpatialInteractionSource, each represented by a different SpatialInteractionSourceKind value:</span></span>
* <span data-ttu-id="5a308-133">**직접** 사용자의 검색 된 직접 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-133">**Hand** represents a user's detected hand.</span></span> <span data-ttu-id="5a308-134">직접 원본 HoloLens에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-134">Hand sources are available only on HoloLens.</span></span>
* <span data-ttu-id="5a308-135">**컨트롤러** 쌍을 이루는 동작 컨트롤러를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-135">**Controller** represents a paired motion controller.</span></span> <span data-ttu-id="5a308-136">동작 컨트롤러는 예를 들어 다양 한 기능을 제공할 수 있습니다. 트리거, 메뉴 단추, 감각을 단추, 터치 패드 및 스틱을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-136">Motion controllers can offer a variety of capabilities, for example: Select triggers, Menu buttons, Grasp buttons, touchpads and thumbsticks.</span></span>
* <span data-ttu-id="5a308-137">**음성** 사용자의 음성 말하기 시스템 검색 키워드를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-137">**Voice** represents the user's voice speaking system-detected keywords.</span></span> <span data-ttu-id="5a308-138">선택 키를 눌러 삽입 되 고 사용자가 "Select" 때마다 해제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-138">This will inject a Select press and release whenever the user says "Select".</span></span>

<span data-ttu-id="5a308-139">누름 이러한 상호 작용 원본에서 검색할 SpatialInputHandler.cpp에서 SpatialInteractionManager의 SourcePressed 이벤트를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-139">To detect presses across any of these interaction sources, you can handle the SourcePressed event on SpatialInteractionManager in SpatialInputHandler.cpp:</span></span>


```cpp
m_interactionManager = SpatialInteractionManager::GetForCurrentView();
    
// Bind a handler to the SourcePressed event.
m_sourcePressedEventToken =
    m_interactionManager->SourcePressed +=
        ref new TypedEventHandler<SpatialInteractionManager^, SpatialInteractionSourceEventArgs^>(
            bind(&SpatialInputHandler::OnSourcePressed, this, _1, _2)
            );
```

<span data-ttu-id="5a308-140">이 누름된 이벤트 앱에 비동기적으로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-140">This pressed event is sent to your app asynchronously.</span></span> <span data-ttu-id="5a308-141">앱 또는 게임 엔진은 일부 처리를 즉시 수행 해야 할 수 또는 처리 루틴 입력에서 이벤트 데이터를 큐에 대기 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-141">Your app or game engine may want to perform some processing right away or you may want to queue up the event data in your input processing routine.</span></span>

<span data-ttu-id="5a308-142">템플릿은 시작 하는 도우미 클래스를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-142">The template includes a helper class to get you started.</span></span> <span data-ttu-id="5a308-143">이 템플릿은 forgoes 디자인의 단순성에 대 한 모든 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-143">This template forgoes any processing for simplicity of design.</span></span> <span data-ttu-id="5a308-144">도우미 클래스는 추적 하나의 이상의 **누름** 마지막 이후에 발생 한 이벤트 **업데이트** 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-144">The helper class keeps track of whether one or more **Pressed** events occurred since the last **Update** call.</span></span> <span data-ttu-id="5a308-145">SpatialInputHandler.cpp:</span><span class="sxs-lookup"><span data-stu-id="5a308-145">From SpatialInputHandler.cpp:</span></span>




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

<span data-ttu-id="5a308-146">따라서 반환 하는 경우는 [SpatialInteractionSourceState](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) 다음 업데이트 하는 동안 가장 최근 입력된 이벤트에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-146">If so, it returns the [SpatialInteractionSourceState](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) for the most recent input event during the next Update.</span></span> <span data-ttu-id="5a308-147">SpatialInputHandler.cpp:</span><span class="sxs-lookup"><span data-stu-id="5a308-147">From SpatialInputHandler.cpp:</span></span>




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

<span data-ttu-id="5a308-148">참고는 위의 코드에서 처리 모든 사용자가 기본 수행 여부를 동일 하 게 누를 **선택** 누르거나 보조 **메뉴** 또는 **이해** 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-148">Note that the code above will treat all presses the same way, whether the user is performing a primary **Select** press or a secondary **Menu** or **Grasp** press.</span></span> <span data-ttu-id="5a308-149">합니다 **선택** 누름을 바늘, 모션 동작 컨트롤러 기본 트리거/단추 누름을 어 탭 수행 손 모양으로 컨트롤러 및 음성, 트리거 또는 사용자의 지원 되는 상호 작용의 기본 폼 "Select"를 말하는 음성.</span><span class="sxs-lookup"><span data-stu-id="5a308-149">The **Select** press is a primary form of interaction supported across hands, motion controllers and voice, triggered either by a hand performing an air-tap, a motion controller with its primary trigger/button pressed, or the user's voice saying "Select".</span></span> <span data-ttu-id="5a308-150">선택 키를 누를 대상으로 하는 홀로그램을 활성화 하려면 사용자의 의도를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-150">Select presses represent the user's intention to activate the hologram they are targeting.</span></span>

<span data-ttu-id="5a308-151">키를 눌러의 종류에 대 한 이유를 발생 하는, SpatialInteractionManager::SourceUpdated 이벤트 처리기를 수정 하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-151">To reason about which kind of press is occurring, we will modify the SpatialInteractionManager::SourceUpdated event handler.</span></span> <span data-ttu-id="5a308-152">코드 (사용 가능한 경우) 감각을 누르면을 감지 하 고 큐브의 위치를 변경 하려면 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-152">Our code will detect Grasp presses (where available) and use them to reposition the cube.</span></span> <span data-ttu-id="5a308-153">이해도 사용할 수 없는 경우 대신 선택 누름 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-153">If Grasp is not available, we will use Select presses instead.</span></span>

<span data-ttu-id="5a308-154">다음과 같은 private 멤버 선언을 SpatialInputHandler.h 추가:</span><span class="sxs-lookup"><span data-stu-id="5a308-154">Add the following private member declarations to SpatialInputHandler.h:</span></span> 


```cpp
void OnSourceUpdated(
       Windows::UI::Input::Spatial::SpatialInteractionManager^ sender,
       Windows::UI::Input::Spatial::SpatialInteractionSourceEventArgs^ args);
   Windows::Foundation::EventRegistrationToken m_sourceUpdatedEventToken;
```

<span data-ttu-id="5a308-155">SpatialInputHandler.cpp를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-155">Open SpatialInputHandler.cpp.</span></span> <span data-ttu-id="5a308-156">생성자에 다음 이벤트 등록을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-156">Add the following event registration to the constructor:</span></span> 


```cpp
m_sourceUpdatedEventToken =
       m_interactionManager->SourceUpdated +=
       ref new TypedEventHandler<SpatialInteractionManager^, SpatialInteractionSourceEventArgs^>(
           bind(&SpatialInputHandler::OnSourceUpdated, this, _1, _2)
           );
```

<span data-ttu-id="5a308-157">이벤트 처리기 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-157">This is the event handler code.</span></span> <span data-ttu-id="5a308-158">입력된 소스를 파악, 발생 한 경우 다음 업데이트 루프에 대 한 포인터 포즈 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-158">If the input source is experiencing a Grasp, the pointer pose will be stored for the next update loop.</span></span> <span data-ttu-id="5a308-159">그렇지 않으면 확인 선택 입력 대신 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-159">Otherwise, it will check for a Select press instead.</span></span> <span data-ttu-id="5a308-160">SpatialInputHandler.cpp:</span><span class="sxs-lookup"><span data-stu-id="5a308-160">From SpatialInputHandler.cpp:</span></span>




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

<span data-ttu-id="5a308-161">소멸자의 이벤트 처리기의 등록을 취소 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-161">Make sure to unregister the event handler in the destructor.</span></span> <span data-ttu-id="5a308-162">SpatialInputHandler.cpp:</span><span class="sxs-lookup"><span data-stu-id="5a308-162">From SpatialInputHandler.cpp:</span></span>


```cpp
m_interactionManager->SourceUpdated -= m_sourcePressedEventToken;
```

<span data-ttu-id="5a308-163">를 컴파일하고 다시 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-163">Recompile, and then redeploy.</span></span> <span data-ttu-id="5a308-164">이제 템플릿 프로젝트 위치 회전 큐브를 변경 하려면 감각을 상호 작용을 인식할 수. 있습니다</span><span class="sxs-lookup"><span data-stu-id="5a308-164">Your template project should now be able to recognize Grasp interactions to reposition the spinning cube.</span></span>

<span data-ttu-id="5a308-165">SpatialInteractionSource API는 다양 한 기능을 사용 하 여 컨트롤러를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-165">The SpatialInteractionSource API supports controllers with a wide range of capabilities.</span></span> <span data-ttu-id="5a308-166">위의 예에서 사용 하 려 하기 전에 한 이해도 지원 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-166">In the example shown above, we check to see if Grasp is supported before trying to use it.</span></span> <span data-ttu-id="5a308-167">SpatialInteractionSource 일반적인 외 다음과 같은 선택적 기능이 지원 **선택** 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-167">The SpatialInteractionSource supports the following optional features beyond the common **Select** press:</span></span>
* <span data-ttu-id="5a308-168">**메뉴 단추:** 지원 IsMenuSupported 속성을 검사 하 여 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-168">**Menu button:** Check support by inspecting the IsMenuSupported property.</span></span> <span data-ttu-id="5a308-169">지원 되는 경우 확인 합니다 [SpatialInteractionSourceState::IsMenuPressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) 속성 확인 메뉴 단추를 누를 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-169">When supported, check the [SpatialInteractionSourceState::IsMenuPressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) property to find out if the menu button is pressed.</span></span>
* <span data-ttu-id="5a308-170">**단추를 이해 합니다.** 지원 IsGraspSupported 속성을 검사 하 여 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-170">**Grasp button:** Check support by inspecting the IsGraspSupported property.</span></span> <span data-ttu-id="5a308-171">지원는 때를 확인 합니다 [SpatialInteractionSourceState::IsGrasped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) 감각을 활성화 되어 있는지 확인 하려면 속성.</span><span class="sxs-lookup"><span data-stu-id="5a308-171">When supported, check the [SpatialInteractionSourceState::IsGrasped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) property to find out if grasp is activated.</span></span>

<span data-ttu-id="5a308-172">컨트롤러에 대 한는 SpatialInteractionSource 추가 기능을 사용 하 여 컨트롤러 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-172">For controllers, the SpatialInteractionSource has a Controller property with additional capabilities.</span></span>
* <span data-ttu-id="5a308-173">**HasThumbstick:** True 이면 컨트롤러에는 엄지 스틱 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-173">**HasThumbstick:** If true, the controller has a thumbstick.</span></span> <span data-ttu-id="5a308-174">검사는 [ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) 스틱을 가져오려고 SpatialInteractionSourceState 속성 x 및 y 값 (ThumbstickX 및 ThumbstickY) 뿐만 아니라 누름된 상태로 (IsThumbstickPressed).</span><span class="sxs-lookup"><span data-stu-id="5a308-174">Inspect the [ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) property of the SpatialInteractionSourceState to acquire the thumbstick x and y values (ThumbstickX and ThumbstickY), as well as its pressed state (IsThumbstickPressed).</span></span>
* <span data-ttu-id="5a308-175">**HasTouchpad:** True 이면 컨트롤러에는 터치 패드를 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-175">**HasTouchpad:** If true, the controller has a touchpad.</span></span> <span data-ttu-id="5a308-176">터치 패드를 가져오려고 SpatialInteractionSourceState의 ControllerProperties 속성을 검사할 x 및 y 값 (TouchpadX 및 TouchpadY) 및 사용자 (IsTouchpadTouched) 패드 접촉 되어 및 터치 패드 (축소 키를 눌러는 경우 IsTouchpadPressed)입니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-176">Inspect the ControllerProperties property of the SpatialInteractionSourceState to acquire the touchpad x and y values (TouchpadX and TouchpadY), and to know if the user is touching the pad (IsTouchpadTouched) and if they are pressing the touchpad down (IsTouchpadPressed).</span></span>
* <span data-ttu-id="5a308-177">**SimpleHapticsController:** SimpleHapticsController API 컨트롤러를 사용 하면 컨트롤러의 haptics 기능을 검사할 수 있습니다 하 고 햅 틱 피드백을 제어할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-177">**SimpleHapticsController:** The SimpleHapticsController API for the controller allows you to inspect the haptics capabilities of the controller, and it also allows you to control haptic feedback.</span></span>

<span data-ttu-id="5a308-178">터치 패드 및-1에서 엄지 스틱 (위쪽, 아래쪽에서 및 왼쪽에서 오른쪽) 양 축에 대 한 1의 범위입니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-178">Note that the range for touchpad and thumbstick from -1 to 1 for both axes (from bottom to top, and from left to right).</span></span> <span data-ttu-id="5a308-179">SpatialInteractionSourceState::SelectPressedValue 속성을 사용 하 여 액세스할을 수 있는 아날로그 트리거에 대 한 범위는 0 ~ 1 범위를 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-179">The range for the analog trigger, which is accessed using the SpatialInteractionSourceState::SelectPressedValue property, has a range of 0 to 1.</span></span> <span data-ttu-id="5a308-180">값이 true로 같다고 IsSelectPressed와 1 상관 관계가 지정 다른 값 IsSelectPressed false 같지 않은지를 사용 하 여 상관 관계를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-180">A value of 1 correlates with IsSelectPressed being equal to true; any other value correlates with IsSelectPressed being equal to false.</span></span>

<span data-ttu-id="5a308-181">컨트롤러의 포인팅 광선을 나타내는 초래 하는 참고는 손 모양 및 컨트롤러가 모두 SpatialInteractionSourceState::Properties::TryGetLocation를 사용 하 여 사용자의 직접 위치를 제공 합니다-이것은 포인터가과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-181">Note that for both a hand and a controller, using SpatialInteractionSourceState::Properties::TryGetLocation will provide the user's hand position - this is distinct from the pointer pose representing the controller's pointing ray.</span></span> <span data-ttu-id="5a308-182">손 모양 위치에 항목을 그릴 TryGetLocation을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-182">If you want to draw something at the hand location, use TryGetLocation.</span></span> <span data-ttu-id="5a308-183">컨트롤러의 팁에서 raycast 하려는 경우에 SpatialPointerPose TryGetInteractionSourcePose에서 가리키는 광선을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-183">If you want to raycast from the tip of the controller, get the pointing ray from TryGetInteractionSourcePose on the SpatialPointerPose.</span></span>

<span data-ttu-id="5a308-184">장치 보기 또는 준비 위치 (인덱스 palm 앞으로 사용 하 여 발생 손가락) 안팎에서 이동할 때 출입 바늘 때 반응 하거나 때 동작 SourceDetected 등 SourceLost, SpatialInteractionManager에서 다른 이벤트를 사용할 수도 있습니다. 컨트롤러 켜기/끄기 설정 또는 쌍을 이루는 짝이 없는 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-184">You can also use the other events on SpatialInteractionManager, such as SourceDetected and SourceLost, to react when hands enter or leave the device's view or when they move in or out of the ready position (index finger raised with palm forward), or when motion controllers are turned on/off or are paired/unpaired.</span></span>

### <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="5a308-185">그립 포즈 포인팅 포즈 비교</span><span class="sxs-lookup"><span data-stu-id="5a308-185">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="5a308-186">Windows Mixed Reality 다양 한 폼 팩터 동작 컨트롤러에서는, 각 컨트롤러의 디자인을 사용 하 여 렌더링할 때 가리키는 사용 해야 다른 사용자의 직접 위치 사이의 "전달" 방향 해당 앱의 자연 관계를 컨트롤러입니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-186">Windows Mixed Reality supports motion controllers in a variety of form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="5a308-187">잘 표현 하기 위해 이러한 컨트롤러, 두 가지 종류의 포즈 각 상호 작용 원본에 대해 조사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-187">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source:</span></span>
* <span data-ttu-id="5a308-188">합니다 **그립 포즈**, HoloLens, 감지한 손 모양 손바닥 또는 동작 컨트롤러를 보유 하는 손 안에서 가능 위치를 나타내는입니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-188">The **grip pose**, representing the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>
    * <span data-ttu-id="5a308-189">몰입 형 헤드셋이이 포즈 가장 사용 렌더링 **사용자의 직접** 또는 **사용자의 직접에 보관 된 개체**검 또는 총 등입니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-189">On immersive headsets, this pose is best used to render **the user's hand** or **an object held in the user's hand**, such as a sword or gun.</span></span>
    * <span data-ttu-id="5a308-190">합니다 **위치를 잡고**: 물론 컨트롤러를 보유 하는 경우 팜 중심 왼쪽 또는 오른쪽 가운데 그립 내의 위치를 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-190">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span>
    * <span data-ttu-id="5a308-191">합니다 **방향을 올바른 축 잡고**: 완전히 플랫 5 손가락 자세를 직접 열면 광선과 표준 프로그램 palm에서 (왼쪽된 palm, palm 오른쪽에서 이전 버전과에서 앞으로)</span><span class="sxs-lookup"><span data-stu-id="5a308-191">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
    * <span data-ttu-id="5a308-192">합니다 **방향을 정방향 축 잡고**: 부분적으로 (처럼 컨트롤러 보유) 직접을 닫을 때, 광선을 가리키는 "forward" 튜브를 통해 비 엄지 손가락으로 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-192">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
    * <span data-ttu-id="5a308-193">합니다 **축 위쪽 방향 잡고**: 오른쪽 정방향 정의 사용 권한에 포함 된 최대 축.</span><span class="sxs-lookup"><span data-stu-id="5a308-193">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>
    * <span data-ttu-id="5a308-194">그립 자세를 통해 액세스할 수 있습니다 [SpatialInteractionSourceState.Properties.TryGetLocation(...) ](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).</span><span class="sxs-lookup"><span data-stu-id="5a308-194">You can access the grip pose through [SpatialInteractionSourceState.Properties.TryGetLocation(...)](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).</span></span>
* <span data-ttu-id="5a308-195">합니다 **포인터 포즈**, 앞으로 가리키는 컨트롤러의 끝을 나타내는입니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-195">The **pointer pose**, representing the tip of the controller pointing forward.</span></span>
    * <span data-ttu-id="5a308-196">이 포즈 raycast에 가장 적합 하면 **UI를 가리키는** 컨트롤러 모델 자체를 렌더링 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="5a308-196">This pose is best used to raycast when **pointing at UI** when you are rendering the controller model itself.</span></span>
    * <span data-ttu-id="5a308-197">포인터 자세를 통해 액세스할 수 있습니다 [SpatialInteractionSourceState.Properties.TryGetLocation(...) 합니다. SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose) 또는 [SpatialInteractionSourceState.TryGetPointerPose(...) 합니다. TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_)합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-197">You can access the pointer pose through [SpatialInteractionSourceState.Properties.TryGetLocation(...).SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose) or [SpatialInteractionSourceState.TryGetPointerPose(...).TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_).</span></span>

### <a name="composite-gestures-spatialgesturerecognizer"></a><span data-ttu-id="5a308-198">복합 제스처의 경우: SpatialGestureRecognizer</span><span class="sxs-lookup"><span data-stu-id="5a308-198">Composite gestures: SpatialGestureRecognizer</span></span>

<span data-ttu-id="5a308-199">A [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx) 해당 헤드 게이즈를 사용 하 여 어떤 사용자가 대상 화면 공간 제스처 이벤트에 실습, 동작 컨트롤러 및 "Select" 음성 명령에서 사용자 상호 작용을 해석 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-199">A [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx) interprets user interactions from hands, motion controllers, and the "Select" voice command to surface spatial gesture events, which users target using their head gaze.</span></span>

<span data-ttu-id="5a308-200">공간 제스처는 Windows Mixed Reality 앱에 대 한 입력의 키 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-200">Spatial gestures are a key form of input for Windows Mixed Reality apps.</span></span> <span data-ttu-id="5a308-201">라우팅 상호 작용을 SpatialInteractionManager에서 홀로그램의 SpatialGestureRecognizer 하 여 앱 수 탭, 보류, 조작 및 탐색 이벤트 감지 균일 하 게 바늘, 음성 및 공간 입력된 장치에서 누름을 처리 하지 않고도 수동으로 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-201">By routing interactions from the SpatialInteractionManager to a hologram's SpatialGestureRecognizer, apps can detect Tap, Hold, Manipulation, and Navigation events uniformly across hands, voice, and spatial input devices, without having to handle presses and releases manually.</span></span>

<span data-ttu-id="5a308-202">SpatialGestureRecognizer 요청 하는 제스처 집합 간의 최소 명확성에만 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-202">SpatialGestureRecognizer performs only the minimal disambiguation between the set of gestures that you request.</span></span> <span data-ttu-id="5a308-203">예를 들어,만 Tap를 요청 하는 경우 사용자 수 누른 해당 손가락 있기만 원하는 탭 계속 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-203">For example, if you request just Tap, the user may hold their finger down as long as they like and a Tap will still occur.</span></span> <span data-ttu-id="5a308-204">요청 하는 경우 모두 페이지를 누르고, 보류 승격 제스처는 해당 손가락 누르고의 보조에 대 한 후 탭을 더 이상 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-204">If you request both Tap and Hold, after about a second of holding down their finger, the gesture will promote to a Hold and a Tap will no longer occur.</span></span>

<span data-ttu-id="5a308-205">SpatialGestureRecognizer를 사용 하려면 SpatialInteractionManager의 처리할 [InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected) 이벤트 및 잡기를 SpatialPointerPose 노출 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-205">To use SpatialGestureRecognizer, handle the SpatialInteractionManager's [InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected) event and grab the SpatialPointerPose exposed there.</span></span> <span data-ttu-id="5a308-206">상호 작용 하려는 의도 하는 사용자가 확인 하기 위해 사용자의 환경 등에서 화면 메시 및 교차 하 여 홀로그램이이 포즈에서 사용자의 헤드 게이즈 광선을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-206">Use the user's head gaze ray from this pose to intersect with the holograms and surface meshes in the user's surroundings, in order to determine what the user is intending to interact with.</span></span> <span data-ttu-id="5a308-207">그런 다음 대상 홀로그램의 SpatialGestureRecognizer 위해 이벤트 인수에는 SpatialInteraction 경로 사용 하 여 해당 [CaptureInteraction](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction) 메서드.</span><span class="sxs-lookup"><span data-stu-id="5a308-207">Then, route the SpatialInteraction in the event arguments to the target hologram's SpatialGestureRecognizer, using its [CaptureInteraction](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction) method.</span></span> <span data-ttu-id="5a308-208">해석에 따라 해당 상호 작용이 시작 됩니다 합니다 [SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings) 생성 시-통하거나 해당 인식기 설정 [TrySetGestureSettings](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings)합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-208">This starts interpreting that interaction according to the [SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings) set on that recognizer at creation time - or by [TrySetGestureSettings](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings).</span></span>

<span data-ttu-id="5a308-209">HoloLens에서 상호 작용 및 제스처를 일반적으로 파생 되어야 해당 사용자의 헤드 게이즈를에서 대상으로 지정 하기 보다는 동안 렌더링 또는 손 모양 아이콘이 위치에 직접 상호 작용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-209">On HoloLens, interactions and gestures should generally derive their targeting from the user's head gaze, rather than trying to render or interact at the hand's location directly.</span></span> <span data-ttu-id="5a308-210">상호 작용 시작 된 후 조작 또는 탐색 제스처와 마찬가지로 제스처를 제어 하려면 손 모양 아이콘이의 상대적 동작을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a308-210">Once an interaction has started, relative motions of the hand may be used to control the gesture, as with the Manipulation or Navigation gesture.</span></span>

## <a name="see-also"></a><span data-ttu-id="5a308-211">참조</span><span class="sxs-lookup"><span data-stu-id="5a308-211">See also</span></span>
* [<span data-ttu-id="5a308-212">응시</span><span class="sxs-lookup"><span data-stu-id="5a308-212">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="5a308-213">제스처</span><span class="sxs-lookup"><span data-stu-id="5a308-213">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="5a308-214">컨트롤러 동작</span><span class="sxs-lookup"><span data-stu-id="5a308-214">Motion controllers</span></span>](motion-controllers.md)
