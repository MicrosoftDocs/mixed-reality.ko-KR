---
title: HoloLens 용 Unity를 사용 하는 WinRT Api
description: HoloLens 용 Unity 프로젝트에서 WinRT Api (Windows 네임 스페이스)를 활용 하는 방법을 설명 합니다.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, WinRT, windows mixed reality, API, 연습
ms.openlocfilehash: 80f950d7571a936e93eb08490ad83dbb34a50b3a
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277991"
---
# <a name="winrt-apis-with-unity-for-hololens"></a><span data-ttu-id="8f4bd-104">HoloLens 용 Unity를 사용 하는 WinRT Api</span><span class="sxs-lookup"><span data-stu-id="8f4bd-104">WinRT APIs with Unity for HoloLens</span></span>

<span data-ttu-id="8f4bd-105">이 페이지에서는 HoloLens 용 Unity 프로젝트에서 WinRT Api를 활용 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f4bd-105">This page describes how to make use of WinRT APIs in your Unity project for HoloLens.</span></span>

## <a name="mixed-reality-apis"></a><span data-ttu-id="8f4bd-106">혼합 현실 Api</span><span class="sxs-lookup"><span data-stu-id="8f4bd-106">Mixed Reality APIs</span></span>

<span data-ttu-id="8f4bd-107">Windows SDK의 혼합 현실 하위 집합은 전처리기 지시문이 없는 프로젝트에서 사용할 수 있는 .NET Standard 2.0 호환 프로젝션에서 사용할 수 있게 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8f4bd-107">A Mixed Reality focused subset of the Windows SDK has been made available in a .NET Standard 2.0 compatible projection, which you can use in your project without preprocessor directives.</span></span> <span data-ttu-id="8f4bd-108">여기에는 대부분의 Api가 포함 되며,이 네임 스페이스에는 나중에 추가 Api를 포함 하도록 확장 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f4bd-108">This includes most APIs in the Windows.Perception and Windows.UI.Input.Spatial namespaces, and may expand to include additional APIs in the future.</span></span> <span data-ttu-id="8f4bd-109">투영 된 Api는 편집기에서 실행 되는 동안 사용할 수 있으며이를 통해 [재생 모드](https://docs.microsoft.com//windows/mixed-reality/unity-play-mode)를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f4bd-109">The projected APIs can be used while running in the Editor, which enables the use of [Play Mode](https://docs.microsoft.com//windows/mixed-reality/unity-play-mode).</span></span> <span data-ttu-id="8f4bd-110">이 프로젝션을 사용 하려면 프로젝트를 다음과 같이 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f4bd-110">To use this projection, make the following modifications to your project:</span></span>

1) <span data-ttu-id="8f4bd-111">[Unity 용 nuget](https://github.com/GlitchEnzo/NuGetForUnity)을 사용 하 여 [MixedReality DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) nuget 패키지에 대 한 참조를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f4bd-111">Add a reference to the [Microsoft.Windows.MixedReality.DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) NuGet package using [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span></span>
2) <span data-ttu-id="8f4bd-112">`Microsoft.`를 사용 하 여 `Windows` 네임 스페이스에 대 한 접두사 참조입니다.</span><span class="sxs-lookup"><span data-stu-id="8f4bd-112">Prefix references to the `Windows` namespace with `Microsoft.`:</span></span>
```cs
using namespace Microsoft.Windows.Perception.Spatial;
```
3) <span data-ttu-id="8f4bd-113">Native pointer 캐스트를 `FromNativePtr`으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="8f4bd-113">Replace native pointer casts with `FromNativePtr`:</span></span>
```cs
var worldOrigin = SpatialCoordinateSystem.FromNativePtr(unityWorldOriginPtr);
```

## <a name="conditionally-include-winrt-api-calls"></a><span data-ttu-id="8f4bd-114">조건부로 WinRT API 호출 포함</span><span class="sxs-lookup"><span data-stu-id="8f4bd-114">Conditionally include WinRT API calls</span></span>

<span data-ttu-id="8f4bd-115">또는 전처리기 지시문을 사용 하 여 유니버설 Windows 플랫폼 및 Xbox One 플랫폼에 대해 빌드된 Unity 프로젝트에 WinRT Api를 활용할 수 있습니다. WinRT Api를 대상으로 하는 Unity 스크립트에서 작성 하는 모든 코드는 해당 빌드에 대해서만 조건부로 포함 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f4bd-115">Alternatively, WinRT APIs can be leveraged for Unity projects built for the Universal Windows Platform and Xbox One platform by using preprocessor directives; any code that you write in Unity scripts that target WinRT APIs must be conditionally included for only those builds.</span></span> 

<span data-ttu-id="8f4bd-116">Unity의 두 단계를 통해이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8f4bd-116">This can be done via two steps in Unity:</span></span>
1) <span data-ttu-id="8f4bd-117">플레이어 설정에서 API 호환성 수준을 **.net 4.6** 또는 **.NET Standard 2.0** 으로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f4bd-117">API compatibility level must be set to **.NET 4.6** or **.NET Standard 2.0** in the player settings</span></span>
    - <span data-ttu-id="8f4bd-118"> > **프로젝트 설정** > **플레이어** > **구성** > **Api 호환성 수준을** **.net 4.6** 또는 **.NET Standard 2.0** 로 **편집** 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f4bd-118">**Edit** > **Project Settings** > **Player** > **Configuration** > **Api Compatibility Level** to **.NET 4.6** or **.NET Standard 2.0**</span></span>
2) <span data-ttu-id="8f4bd-119">전처리기 지시문 **ENABLE_WINMD_SUPPORT** 은 WinRT 활용 코드를 통해 래핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8f4bd-119">The preprocessor directive **ENABLE_WINMD_SUPPORT** must be wrapped around any WinRT-leveraged code</span></span>

<span data-ttu-id="8f4bd-120">다음 코드 조각은 [스크립트의 C# WinRT API 유니버설 Windows 플랫폼](https://docs.unity3d.com/Manual/windowsstore-scripts.html)에 대 한 Unity 수동 페이지에서 가져온 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8f4bd-120">The following code snippet is from the Unity manual page for [Universal Windows Platform: WinRT API in C# scripts](https://docs.unity3d.com/Manual/windowsstore-scripts.html).</span></span> <span data-ttu-id="8f4bd-121">이 예에서 광고 ID는 반환 되지만 UWP 및 Xbox One 빌드에만 해당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f4bd-121">In this example, an advertising ID is returned, but only on UWP and Xbox One builds:</span></span>

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

## <a name="edit-your-scripts-in-a-unity-c-project"></a><span data-ttu-id="8f4bd-122">Unity C# 프로젝트에서 스크립트 편집</span><span class="sxs-lookup"><span data-stu-id="8f4bd-122">Edit your scripts in a Unity C# project</span></span>

<span data-ttu-id="8f4bd-123">Unity 편집기에서 스크립트를 두 번 클릭 하면 기본적으로 편집기 프로젝트에서 스크립트가 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f4bd-123">When you double-click a script in the Unity editor, it will by default launch your script in an editor project.</span></span> <span data-ttu-id="8f4bd-124">Visual Studio 프로젝트가 Windows 런타임를 참조 하지 않으므로 WinRT Api를 알 수 없는 것으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f4bd-124">The WinRT APIs will appear to be unknown because the Visual Studio project does not reference the Windows Runtime.</span></span> <span data-ttu-id="8f4bd-125">또한 **ENABLE_WINMD_SUPPORT** 지시문은 정의 되지 않으며, UWP Visual Studio 솔루션에 프로젝트를 빌드할 때까지 *#if* 래핑된 코드는 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8f4bd-125">Further, the **ENABLE_WINMD_SUPPORT** directive will be undefined and any *#if* wrapped code will be ignored until you build your project into a UWP Visual Studio solution.</span></span>

## <a name="see-also"></a><span data-ttu-id="8f4bd-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8f4bd-126">See also</span></span>
* [<span data-ttu-id="8f4bd-127">Unity Visual Studio 솔루션 내보내기 및 빌드</span><span class="sxs-lookup"><span data-stu-id="8f4bd-127">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="8f4bd-128">Windows 런타임 지원 Unity</span><span class="sxs-lookup"><span data-stu-id="8f4bd-128">Windows Runtime Support Unity</span></span>](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)
