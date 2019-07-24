---
title: Unity의 키보드 입력
description: Unity는 사용할 수 있는 실제 키보드가 없을 때 키보드 입력을 허용 하기 위한 TouchScreenKeyboard 클래스를 제공 합니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 키보드, 입력, unity, touchscreenkeyboard
ms.openlocfilehash: 35f6f0df993931eea35db7b167110b341ea0c0f2
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63515736"
---
# <a name="keyboard-input-in-unity"></a>Unity의 키보드 입력

**공간** *UnityEngine*<br>
 **형식**: *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*

HoloLens는 Bluetooth 키보드를 비롯 한 다양 한 형태의 입력을 지원 하지만 대부분의 응용 프로그램에서는 모든 사용자가 실제 키보드를 사용할 수 있다고 간주할 수 없습니다. 응용 프로그램에 텍스트 입력이 필요한 경우 화면 키보드의 일부 형식을 제공 해야 합니다.

Unity는 사용할 수 있는 실제 키보드가 없을 때 키보드 입력을 허용 하기 위한 *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* 클래스를 제공 합니다.

## <a name="hololens-system-keyboard-behavior-in-unity"></a>Unity의 HoloLens 시스템 키보드 동작

HoloLens에서 *TouchScreenKeyboard* 는 시스템의 화면 키보드를 활용 합니다. 시스템의 화면 키보드는 대규모 보기 위에 오버레이 할 수 없기 때문에 Unity에서 키보드를 표시 하는 보조 2D XAML 뷰를 만든 다음 입력이 제출 되 면 대규모 보기로 돌아갑니다. 사용자 흐름은 다음과 같습니다.
1. 사용자가 응용 프로그램 코드에서 *TouchScreenKeyboard* 를 호출 하는 작업을 수행 합니다.
    * 앱은 *TouchScreenKeyboard* 를 호출 하기 전에 앱 상태를 일시 중지 해야 합니다.
    * 앱이 대규모 보기로 다시 전환 하기 전에 종료 될 수 있습니다.
2. Unity는 전 세계에 자동 배치 되는 2D XAML 뷰로 전환 합니다.
3. 사용자가 시스템 키보드를 사용 하 여 텍스트를 입력 하 고 제출 하거나 취소 합니다.
4. Unity에서 다시 대규모 보기로 전환
    * 앱은 *TouchScreenKeyboard* 완료 될 때 앱 상태를 다시 시작 해야 합니다.
5. 제출 된 텍스트는 *TouchScreenKeyboard* 에서 사용할 수 있습니다.

### <a name="available-keyboard-views"></a>사용 가능한 키보드 보기

사용할 수 있는 6 가지 키보드 보기는 다음과 같습니다.
* 한 줄 텍스트 상자
* 제목이 있는 한 줄 텍스트 상자
* 여러 줄 텍스트 상자
* 제목이 있는 여러 줄 텍스트 상자
* 한 줄 암호 상자
* 제목이 있는 한 줄 암호 상자

## <a name="how-to-enable-the-system-keyboard-in-unity"></a>Unity에서 시스템 키보드를 사용 하도록 설정 하는 방법

HoloLens 시스템 키보드는 "UWP 빌드 형식"을 "XAML"로 설정 하 여 내보낸 Unity 응용 프로그램 에서만 사용할 수 있습니다. "D3D"를 통해 "XAML"을 "UWP 빌드 형식"으로 선택 하는 경우에는 장단점이 있습니다. 이러한 절충에 익숙하지 않은 경우 시스템 키보드에 대 한 [대체 입력 솔루션](#alternative-keyboard-options) 을 탐색 하는 것이 좋습니다.
1. **파일** 메뉴를 열고 **빌드 설정** ...을 선택 합니다.
2. **플랫폼이** **Windows 스토어**로 설정 되 고 **SDK** 가 **유니버설 10**으로 설정 되었는지 확인 하 고 **UWP 빌드 형식을** **XAML**로 설정 합니다.
3. **빌드 설정** 대화 상자에서 **플레이어 설정 ...** 단추를 클릭 합니다.
4. **Windows 스토어에 대 한 설정 탭을** 선택 합니다.
5. **기타 설정** 그룹 확장
6. **렌더링** 섹션에서 **가상 현실 지원** 확인란을 선택 하 여 새 **가상 현실 장치** 목록을 추가 합니다.
7. 가상 현실 Sdk 목록에 **Windows Holographic** 가 표시 되는지 확인 합니다.

>[!NOTE]
>빌드를 HoloLens 장치에서 지원 되는 가상 현실로 표시 하지 않으면 프로젝트는 2D XAML 앱으로 내보냅니다.

## <a name="using-the-system-keyboard-in-your-unity-app"></a>Unity 앱에서 시스템 키보드 사용

### <a name="declare-the-keyboard"></a>키보드를 선언 합니다.

클래스에서 *TouchScreenKeyboard* 를 저장 하는 변수와 키보드에서 반환 하는 문자열을 보유할 변수를 선언 합니다.

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a>키보드 호출

키보드 입력을 요청 하는 이벤트가 발생 하는 경우 원하는 입력 형식에 따라 이러한 함수 중 하나를 호출 합니다. 제목은 textPlaceholder 매개 변수에 지정 됩니다.

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

### <a name="retrieve-typed-contents"></a>형식화 된 콘텐츠 검색

업데이트 루프에서 키보드에서 새 입력을 받았는지 확인 하 고 다른 곳에서 사용할 수 있도록 저장 합니다.

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

## <a name="alternative-keyboard-options"></a>대체 키보드 옵션

대규모 보기에서 2D 뷰로 전환 하는 것은 사용자 로부터 텍스트 입력을 가져오는 이상적인 방법이 아님을 이해 하 고 있습니다.

Unity를 통한 시스템 키보드 활용에 대 한 현재 대안은 다음과 같습니다.
* 입력에 음성 받아쓰기 사용 (<b>참고:</b> 사전에 없는 단어에는 오류가 발생 하기 쉬우며 암호 입력에 적합 하지 않음)
* 응용 프로그램 전용 보기에서 작동 하는 키보드 만들기
