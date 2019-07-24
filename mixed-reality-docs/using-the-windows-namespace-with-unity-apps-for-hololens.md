---
title: HoloLens 용 Unity 앱과 함께 Windows 네임 스페이스 사용
description: HoloLens 용 Unity 프로젝트에서 WinRT Api를 활용 하는 방법을 설명 합니다.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, WinRT, windows mixed reality, API, 연습
ms.openlocfilehash: fd25548de8eeb3c8157a3f9de283dc5004ed1180
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548721"
---
# <a name="using-the-windows-namespace-with-unity-apps-for-hololens"></a>HoloLens 용 Unity 앱과 함께 Windows 네임 스페이스 사용

이 페이지에서는 HoloLens 용 Unity 프로젝트에서 WinRT Api를 활용 하는 방법을 설명 합니다.

## <a name="conditionally-include-winrt-api-calls"></a>조건부로 WinRT API 호출 포함

WinRT Api는 유니버설 Windows 플랫폼 및 Xbox One 플랫폼에 대해 빌드된 Unity 프로젝트에 활용할 수 있습니다. WinRT Api를 대상으로 하는 Unity 스크립트에서 작성 하는 모든 코드는 해당 빌드에 대해서만 조건부로 포함 되어야 합니다. 

Unity의 두 단계를 통해이 작업을 수행할 수 있습니다.
1) 플레이어 설정에서 API 호환성 수준을 **.net 4.6** 또는 **.NET Standard 2.0** 으로 설정 해야 합니다.
    -  > **프로젝트 설정**    플레이어 구성 Api 호환성 수준을 .net 4.6 또는 .NET Standard 2.0로 편집 >  >  > 
2) 전처리기 지시문 **ENABLE_WINMD_SUPPORT** 은 WinRT 활용 코드를 통해 래핑해야 합니다.

다음 코드 조각은 유니버설 Windows 플랫폼에 대 한 [Unity 수동 페이지에서 가져온 것입니다. C# 스크립트](http://docs.unity3d.com/Manual/windowsstore-scripts.html)의 WinRT API. 이 예에서 광고 ID는 반환 되지만 UWP 및 Xbox One 빌드에만 해당 됩니다.

```
using UnityEngine;
public class WinRTAPI : MonoBehaviour {
    void Update() {
        auto adId = GetAdvertisingId();
        // ...
    }

    string GetAdvertisingId() {
        #if ENABLE_WINMD_SUPPORT
            return Windows.System.UserProfile.AdvertisingManager.AdvertisingId;
        #else
            return "";
        #endif
    }
}
```

## <a name="edit-your-scripts-in-a-unity-c-project"></a>Unity C# 프로젝트에서 스크립트 편집

Unity 편집기에서 스크립트를 두 번 클릭 하면 기본적으로 편집기 프로젝트에서 스크립트가 시작 됩니다. Visual Studio 프로젝트가 Windows 런타임를 참조 하지 않으므로 WinRT Api를 알 수 없는 것으로 표시 됩니다. 또한 **ENALBE_WINMD_SUPPORT** 지시문은 정의 되지 않으며, UWP Visual Studio 솔루션에 프로젝트를 빌드할 때까지 *#if* 래핑된 코드는 무시 됩니다.

## <a name="see-also"></a>참조
* [Unity Visual Studio 솔루션 내보내기 및 빌드](exporting-and-building-a-unity-visual-studio-solution.md)
* [Windows 런타임 지원 Unity](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)