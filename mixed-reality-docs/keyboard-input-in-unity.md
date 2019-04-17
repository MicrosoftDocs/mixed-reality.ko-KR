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
# <a name="keyboard-input-in-unity"></a>Unity의 키보드 입력

**Namespace:** *UnityEngine*<br>
 **형식**: *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*

HoloLens Bluetooth 키보드를 포함 하 여 입력의 다양 한 형태를 지원 하지만 대부분의 응용 프로그램을 실제 키보드를 사용할 수 있는 모든 사용자에 게는 가정할 수 없습니다. 응용 프로그램 텍스트 입력이 필요한 경우 화면 키보드에서 일종의 제공 되어야 합니다.

Unity를 제공 합니다 *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* 사용 가능한 실제 키보드가 없을 경우 키보드 입력을 수락 하는 것에 대 한 클래스입니다.

## <a name="hololens-system-keyboard-behavior-in-unity"></a>Unity에서 HoloLens 시스템 키보드 동작

HoloLens에 *TouchScreenKeyboard* 시스템의 화면 키보드를 활용 합니다. 시스템의 화면 키보드에서 되지 않아 키보드를 표시 한 다음 입력을 제출한 후 대규모 보기로 다시 돌아와서 보조 2D XAML 보기를 만드는 Unity가 대규모 보기 위에 오버레이를 수 없습니다. 사용자 흐름은 다음과 같이 이루어집니다.
1. 인해 앱 코드에서 호출할 작업을 수행 하는 사용자 *TouchScreenKeyboard*
    * 앱을 호출 하기 전에 응용 프로그램 상태를 일시 중지 담당 *TouchScreenKeyboard*
    * 앱을 그 어느 때 대규모 보기로 다시 전환 하기 전에 종료할 수 있습니다.
2. Unity는 전 세계에서 자동 배치는 2D XAML 보기로 전환
3. 사용자가 시스템 키보드를 사용 하 여 텍스트를 입력 하 고 제출 또는 취소
4. Unity를 대규모 보기로 다시 전환
    * 앱이 앱을 다시 시작 하는 일을 담당 될 때 상태를 *TouchScreenKeyboard* 이루어집니다
5. 제출 된 텍스트에서 사용할 수는 *TouchScreenKeyboard*

### <a name="available-keyboard-views"></a>사용 가능한 바로 뷰

가지 6 개의 다른 키보드 뷰가 제공 됩니다.
* 한 줄 텍스트
* 제목 줄 텍스트 상자
* 여러 줄 텍스트 상자
* 여러 줄 텍스트 상자 제목
* 한 줄 암호 상자
* 제목 줄 암호 상자

## <a name="how-to-enable-the-system-keyboard-in-unity"></a>Unity에서 시스템 키보드를 사용 하는 방법

HoloLens 시스템 키보드만 "UWP 빌드"로 설정 된 형식 "XAML"를 사용 하 여 내보낸 Unity 응용 프로그램에 제공 됩니다. "D3D"를 통해 UWP 빌드 유형""XAML "를 선택 하면 할 장단점이 있습니다. 탐색 하려는 경우 이러한 절충에 익숙하지를 [솔루션의 대체 입력](#alternative-keyboard-options) 시스템 키보드를 합니다.
1. 엽니다는 **파일** 선택한 메뉴 **빌드 설정...**
2. 확인 합니다 **플랫폼** 로 설정 되어 **Windows 스토어**의 **SDK** 로 설정 되어 **유니버설 10**, 설정 및를 **UWP 빌드 형식**  하 **XAML**합니다.
3. 에 **빌드 설정** 대화 상자에서 클릭 된 **플레이어 설정...**  단추
4. 선택 된 **설정에 대 한 Windows 저장소** 탭
5. 확장 된 **기타 설정** 그룹
6. 에 **렌더링** 섹션을 확인 합니다 **가상 현실 지원** 새 추가 하려면이 확인란을 **가상 현실 장치용** 목록
7. 확인 **Windows Holographic** 가상 현실 Sdk의 목록에 표시

>[!NOTE]
>HoloLens 장치를 사용 하 여 가상 현실 지원으로 빌드를 표시 하지 않습니다, 프로젝트를 2D XAML 앱으로 내보냅니다.

## <a name="using-the-system-keyboard-in-your-unity-app"></a>Unity 앱에서 시스템 키보드 사용

### <a name="declare-the-keyboard"></a>키보드를 선언 합니다.

클래스에 저장 하는 변수를 선언 합니다 *TouchScreenKeyboard* 문자열 키보드를 보유할 변수를 반환 합니다.

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a>키보드를 호출 합니다.

이벤트가 발생 키보드 입력을 요청 하는 경우 원하는 입력 형식에 따라 이러한 함수 중 하나를 호출 합니다. 제목 textPlaceholder 매개 변수에 지정 되어 있는지를 참고 합니다.

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

업데이트 루프에서 키보드 새 입력을 수신 하는 경우를 확인 하 고 다른 곳에서 사용할 수 있도록 저장 합니다.

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

사용자의 텍스트 입력을 얻을 수 있는 이상적인 방법은 없습니다 2D 보기에 대 한 대규모 보기에서 외부 전환할 이해 합니다.

Unity 통해 시스템 키보드를 활용 하 여 현재 대안은 다음과 같습니다.
* 입력에 대 한 음성 받아쓰기를 사용 하 여 (<b>참고:</b> 종종 오류가 사전에 없는 단어 이며 암호 항목에 적합 하지 않은)
* 응용 프로그램 전용 보기에서 작동 하는 키보드 만들기
