---
title: Unity의 키보드 입력
description: Unity는 사용 가능한 실제 키보드가 없을 경우 키보드 입력을 수락 하기 위해 TouchScreenKeyboard 클래스를 제공 합니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 키보드 입력된 unity touchscreenkeyboard
ms.openlocfilehash: 35f6f0df993931eea35db7b167110b341ea0c0f2
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604887"
---
# <a name="keyboard-input-in-unity"></a><span data-ttu-id="0e864-104">Unity의 키보드 입력</span><span class="sxs-lookup"><span data-stu-id="0e864-104">Keyboard input in Unity</span></span>

<span data-ttu-id="0e864-105">**Namespace:** *UnityEngine*</span><span class="sxs-lookup"><span data-stu-id="0e864-105">**Namespace:** *UnityEngine*</span></span><br>
 <span data-ttu-id="0e864-106">**형식**: *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span><span class="sxs-lookup"><span data-stu-id="0e864-106">**Type**: *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span></span>

<span data-ttu-id="0e864-107">HoloLens Bluetooth 키보드를 포함 하 여 입력의 다양 한 형태를 지원 하지만 대부분의 응용 프로그램을 실제 키보드를 사용할 수 있는 모든 사용자에 게는 가정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0e864-107">While HoloLens supports many forms of input including Bluetooth keyboards, most applications cannot assume that all users will have a physical keyboard available.</span></span> <span data-ttu-id="0e864-108">응용 프로그램 텍스트 입력이 필요한 경우 화면 키보드에서 일종의 제공 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e864-108">If your application requires text input, some form of on screen keyboard should be provided.</span></span>

<span data-ttu-id="0e864-109">Unity를 제공 합니다 *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* 사용 가능한 실제 키보드가 없을 경우 키보드 입력을 수락 하는 것에 대 한 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="0e864-109">Unity provides the *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* class for accepting keyboard input when there is no physical keyboard available.</span></span>

## <a name="hololens-system-keyboard-behavior-in-unity"></a><span data-ttu-id="0e864-110">Unity에서 HoloLens 시스템 키보드 동작</span><span class="sxs-lookup"><span data-stu-id="0e864-110">HoloLens system keyboard behavior in Unity</span></span>

<span data-ttu-id="0e864-111">HoloLens에 *TouchScreenKeyboard* 시스템의 화면 키보드를 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e864-111">On HoloLens, the *TouchScreenKeyboard* leverages the system's on screen keyboard.</span></span> <span data-ttu-id="0e864-112">시스템의 화면 키보드에서 되지 않아 키보드를 표시 한 다음 입력을 제출한 후 대규모 보기로 다시 돌아와서 보조 2D XAML 보기를 만드는 Unity가 대규모 보기 위에 오버레이를 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0e864-112">The system's on screen keyboard is unable to overlay on top of a volumetric view so Unity has to create a secondary 2D XAML view to show the keyboard then return back to the volumetric view once input has been submitted.</span></span> <span data-ttu-id="0e864-113">사용자 흐름은 다음과 같이 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="0e864-113">The user flow goes like this:</span></span>
1. <span data-ttu-id="0e864-114">인해 앱 코드에서 호출할 작업을 수행 하는 사용자 *TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="0e864-114">The user performs an action causing app code to call *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="0e864-115">앱을 호출 하기 전에 응용 프로그램 상태를 일시 중지 담당 *TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="0e864-115">The app is responsible for pausing app state before calling *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="0e864-116">앱을 그 어느 때 대규모 보기로 다시 전환 하기 전에 종료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e864-116">The app may terminate before ever switching back to the volumetric view</span></span>
2. <span data-ttu-id="0e864-117">Unity는 전 세계에서 자동 배치는 2D XAML 보기로 전환</span><span class="sxs-lookup"><span data-stu-id="0e864-117">Unity switches to a 2D XAML view which is auto-placed in the world</span></span>
3. <span data-ttu-id="0e864-118">사용자가 시스템 키보드를 사용 하 여 텍스트를 입력 하 고 제출 또는 취소</span><span class="sxs-lookup"><span data-stu-id="0e864-118">The user enters text using the system keyboard and submits or cancels</span></span>
4. <span data-ttu-id="0e864-119">Unity를 대규모 보기로 다시 전환</span><span class="sxs-lookup"><span data-stu-id="0e864-119">Unity switches back to the volumetric view</span></span>
    * <span data-ttu-id="0e864-120">앱이 앱을 다시 시작 하는 일을 담당 될 때 상태를 *TouchScreenKeyboard* 이루어집니다</span><span class="sxs-lookup"><span data-stu-id="0e864-120">The app is responsible for resuming app state when the *TouchScreenKeyboard* is done</span></span>
5. <span data-ttu-id="0e864-121">제출 된 텍스트에서 사용할 수는 *TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="0e864-121">Submitted text is available in the *TouchScreenKeyboard*</span></span>

### <a name="available-keyboard-views"></a><span data-ttu-id="0e864-122">사용 가능한 바로 뷰</span><span class="sxs-lookup"><span data-stu-id="0e864-122">Available keyboard views</span></span>

<span data-ttu-id="0e864-123">가지 6 개의 다른 키보드 뷰가 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0e864-123">There are six different keyboard views available:</span></span>
* <span data-ttu-id="0e864-124">한 줄 텍스트</span><span class="sxs-lookup"><span data-stu-id="0e864-124">Single-line textbox</span></span>
* <span data-ttu-id="0e864-125">제목 줄 텍스트 상자</span><span class="sxs-lookup"><span data-stu-id="0e864-125">Single-line textbox with title</span></span>
* <span data-ttu-id="0e864-126">여러 줄 텍스트 상자</span><span class="sxs-lookup"><span data-stu-id="0e864-126">Multi-line textbox</span></span>
* <span data-ttu-id="0e864-127">여러 줄 텍스트 상자 제목</span><span class="sxs-lookup"><span data-stu-id="0e864-127">Multi-line textbox with title</span></span>
* <span data-ttu-id="0e864-128">한 줄 암호 상자</span><span class="sxs-lookup"><span data-stu-id="0e864-128">Single-line password box</span></span>
* <span data-ttu-id="0e864-129">제목 줄 암호 상자</span><span class="sxs-lookup"><span data-stu-id="0e864-129">Single-line password box with title</span></span>

## <a name="how-to-enable-the-system-keyboard-in-unity"></a><span data-ttu-id="0e864-130">Unity에서 시스템 키보드를 사용 하는 방법</span><span class="sxs-lookup"><span data-stu-id="0e864-130">How to enable the system keyboard in Unity</span></span>

<span data-ttu-id="0e864-131">HoloLens 시스템 키보드만 "UWP 빌드"로 설정 된 형식 "XAML"를 사용 하 여 내보낸 Unity 응용 프로그램에 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0e864-131">The HoloLens system keyboard is only available to Unity applications that are exported with the "UWP Build Type" set to "XAML".</span></span> <span data-ttu-id="0e864-132">"D3D"를 통해 UWP 빌드 유형""XAML "를 선택 하면 할 장단점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e864-132">There are tradeoffs you make when you choose "XAML" as the "UWP Build Type" over "D3D".</span></span> <span data-ttu-id="0e864-133">탐색 하려는 경우 이러한 절충에 익숙하지를 [솔루션의 대체 입력](#alternative-keyboard-options) 시스템 키보드를 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e864-133">If you aren't comfortable with those tradeoffs, you may wish to explore an [alternative input solution](#alternative-keyboard-options) to the system keyboard.</span></span>
1. <span data-ttu-id="0e864-134">엽니다는 **파일** 선택한 메뉴 **빌드 설정...**</span><span class="sxs-lookup"><span data-stu-id="0e864-134">Open the **File** menu and select **Build Settings...**</span></span>
2. <span data-ttu-id="0e864-135">확인 합니다 **플랫폼** 로 설정 되어 **Windows 스토어**의 **SDK** 로 설정 되어 **유니버설 10**, 설정 및를 **UWP 빌드 형식**  하 **XAML**합니다.</span><span class="sxs-lookup"><span data-stu-id="0e864-135">Ensure the **Platform** is set to **Windows Store**, the **SDK** is set to **Universal 10**, and set the **UWP Build Type** to **XAML**.</span></span>
3. <span data-ttu-id="0e864-136">에 **빌드 설정** 대화 상자에서 클릭 된 **플레이어 설정...**  단추</span><span class="sxs-lookup"><span data-stu-id="0e864-136">In the **Build Settings** dialog, click the **Player Settings...** button</span></span>
4. <span data-ttu-id="0e864-137">선택 된 **설정에 대 한 Windows 저장소** 탭</span><span class="sxs-lookup"><span data-stu-id="0e864-137">Select the **Settings for Windows Store** tab</span></span>
5. <span data-ttu-id="0e864-138">확장 된 **기타 설정** 그룹</span><span class="sxs-lookup"><span data-stu-id="0e864-138">Expand the **Other Settings** group</span></span>
6. <span data-ttu-id="0e864-139">에 **렌더링** 섹션을 확인 합니다 **가상 현실 지원** 새 추가 하려면이 확인란을 **가상 현실 장치용** 목록</span><span class="sxs-lookup"><span data-stu-id="0e864-139">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality Devices** list</span></span>
7. <span data-ttu-id="0e864-140">확인 **Windows Holographic** 가상 현실 Sdk의 목록에 표시</span><span class="sxs-lookup"><span data-stu-id="0e864-140">Ensure **Windows Holographic** appears in the list of Virtual Reality SDKs</span></span>

>[!NOTE]
><span data-ttu-id="0e864-141">HoloLens 장치를 사용 하 여 가상 현실 지원으로 빌드를 표시 하지 않습니다, 프로젝트를 2D XAML 앱으로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="0e864-141">If you don't mark the build as Virtual Reality Supported with the HoloLens device, the project will export as a 2D XAML app.</span></span>

## <a name="using-the-system-keyboard-in-your-unity-app"></a><span data-ttu-id="0e864-142">Unity 앱에서 시스템 키보드 사용</span><span class="sxs-lookup"><span data-stu-id="0e864-142">Using the system keyboard in your Unity app</span></span>

### <a name="declare-the-keyboard"></a><span data-ttu-id="0e864-143">키보드를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e864-143">Declare the keyboard</span></span>

<span data-ttu-id="0e864-144">클래스에 저장 하는 변수를 선언 합니다 *TouchScreenKeyboard* 문자열 키보드를 보유할 변수를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e864-144">In the class, declare a variable to store the *TouchScreenKeyboard* and a variable to hold the string the keyboard returns.</span></span>

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a><span data-ttu-id="0e864-145">키보드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e864-145">Invoke the keyboard</span></span>

<span data-ttu-id="0e864-146">이벤트가 발생 키보드 입력을 요청 하는 경우 원하는 입력 형식에 따라 이러한 함수 중 하나를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e864-146">When an event occurs requesting keyboard input, call one of these functions depending upon the type of input desired.</span></span> <span data-ttu-id="0e864-147">제목 textPlaceholder 매개 변수에 지정 되어 있는지를 참고 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e864-147">Note that the title is specified in the textPlaceholder parameter.</span></span>

```cs
// Single-line textbox
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false);

// Single-line textbox with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false, "Single-line title");

// Multi-line textbox
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, true, false, false);

// Multi-line textbox with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, true, false, false, "Multi-line Title");

// Single-line password box
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, true, false);

// Single-line password box with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, true, false, "Secure Single-line Title");
```

### <a name="retrieve-typed-contents"></a><span data-ttu-id="0e864-148">형식화 된 콘텐츠 검색</span><span class="sxs-lookup"><span data-stu-id="0e864-148">Retrieve typed contents</span></span>

<span data-ttu-id="0e864-149">업데이트 루프에서 키보드 새 입력을 수신 하는 경우를 확인 하 고 다른 곳에서 사용할 수 있도록 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e864-149">In the update loop, check if the keyboard received new input and store it for use elsewhere.</span></span>

```cs
if (TouchScreenKeyboard.visible == false && keyboard != null)
{
       if (keyboard.done == true)
       {
           keyboardText = keyboard.text;
           keyboard = null;
       }
}
```

## <a name="alternative-keyboard-options"></a><span data-ttu-id="0e864-150">대체 키보드 옵션</span><span class="sxs-lookup"><span data-stu-id="0e864-150">Alternative keyboard options</span></span>

<span data-ttu-id="0e864-151">사용자의 텍스트 입력을 얻을 수 있는 이상적인 방법은 없습니다 2D 보기에 대 한 대규모 보기에서 외부 전환할 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e864-151">We understand that switching out of a volumetric view into a 2D view isn't the ideal way to get text input from the user.</span></span>

<span data-ttu-id="0e864-152">Unity 통해 시스템 키보드를 활용 하 여 현재 대안은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0e864-152">The current alternatives to leveraging the system keyboard through Unity include:</span></span>
* <span data-ttu-id="0e864-153">입력에 대 한 음성 받아쓰기를 사용 하 여 (<b>참고:</b> 종종 오류가 사전에 없는 단어 이며 암호 항목에 적합 하지 않은)</span><span class="sxs-lookup"><span data-stu-id="0e864-153">Using speech dictation for input (<b>Note:</b> this is often error prone for words not found in the dictionary and is not suitable for password entry)</span></span>
* <span data-ttu-id="0e864-154">응용 프로그램 전용 보기에서 작동 하는 키보드 만들기</span><span class="sxs-lookup"><span data-stu-id="0e864-154">Create a keyboard that works in your applications exclusive view</span></span>
