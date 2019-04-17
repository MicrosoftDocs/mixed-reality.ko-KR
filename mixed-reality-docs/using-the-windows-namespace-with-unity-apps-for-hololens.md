---
title: HoloLens 용 Unity 앱을 사용 하 여 Windows 네임 스페이스를 사용 하 여
description: WinRT api HoloLens에 대 한 Unity 프로젝트에서 사용 하는 방법에 설명 합니다.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: WinRT, unity, windows 혼합된 현실 등 API 연습
ms.openlocfilehash: ed65b5995d74c54057a49b878c1206d0f06394ca
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599870"
---
# <a name="using-the-windows-namespace-with-unity-apps-for-hololens"></a>HoloLens 용 Unity 앱을 사용 하 여 Windows 네임 스페이스를 사용 하 여

이 페이지에는 HoloLens에 대 한 WinRT Api Unity 프로젝트에서 사용 하는 방법을 설명 합니다.

## <a name="conditionally-include-winrt-api-calls"></a>WinRT API 호출을 조건부로 포함

WinRT Api는 Windows 8, Windows 8.1 또는 유니버설 Windows 플랫폼을 대상으로 하는 Unity 프로젝트 빌드에만 사용 됩니다. WinRT Api를 대상으로 하는 Unity 스크립트 작성 하는 모든 코드는 이러한 빌드만 조건부로 포함 되어야 합니다. 이렇게 NETFX_CORE 또는 WINDOWS_UWP 전처리기 정의 사용 합니다. 다른 코드 뿐만 아니라 문을 사용 하 여이 규칙이 적용 됩니다.

에 대 한 Unity 설명서 페이지에서 다음 코드 조각은 [유니버설 Windows 플랫폼: WinRT API에서 C# 스크립트](http://docs.unity3d.com/Manual/windowsstore-scripts.html)합니다. 이 예제에서는 광고 ID가 반환 Windows 8.0 또는 더 높은 대상에만 빌드:

```
using UnityEngine;
public class WinRTAPI : MonoBehaviour {
    void Update() {
        auto adId = GetAdvertisingId();
        // ...
    }

    string GetAdvertisingId() {
        #if NETFX_CORE
            return Windows.System.UserProfile.AdvertisingManager.AdvertisingId;
        #else
            return "";
        #endif
    }
}
```

## <a name="edit-your-scripts-in-a-unity-c-project"></a>Unity에서 스크립트 편집 C# 프로젝트

Unity 편집기에서 스크립트를 두 번 클릭 하면 기본적으로 시작 됩니다 편집기 프로젝트의 스크립트. WinRT Api는 알 수 없는 두 가지 이유로 표시 됩니다. NETFX_CORE이이 환경에서 정의 되지 않으며 프로젝트는 Windows 런타임 참조 하지 않습니다. 사용 하는 경우는 [내보내기 좋으며 설정을 작성](exporting-and-building-a-unity-visual-studio-solution.md), 및 대신 해당 프로젝트의 스크립트를 편집, NETFX_CORE를 정의 하 고 현재 위치에이 구성을 사용 하 여 Windows Runtime에 대 한 참조를 포함할 수도, WinRT Api 됩니다. IntelliSense에 사용할 수 있습니다.

Unity C# 프로젝트 원격 디버깅 Visual Studio에서 F5를 사용 하 여 스크립트를 통해 디버깅을 사용할 수도 있습니다. Unity를 열면 처음으로 작업 하는 IntelliSense를 보이지 않는 경우 C# 프로젝트, 프로젝트를 닫고 다시 엽니다. IntelliSense는 작업을 시작 해야 합니다.

## <a name="see-also"></a>참조
* [내보내기 및 Unity Visual Studio 솔루션 빌드](exporting-and-building-a-unity-visual-studio-solution.md)
