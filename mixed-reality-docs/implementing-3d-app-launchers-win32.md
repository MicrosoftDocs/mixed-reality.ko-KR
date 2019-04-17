---
title: 3D 앱 시작 관리자 (Win32 앱)를 구현 합니다.
description: 3D 앱 시작 관리자를 만들고 Win32 VR 앱과 게임 (스트림 외에 배포)에 대 한 로고를 따라서 나타납니다 Windows Mixed Reality 시작 메뉴 및 홈 환경에서 하는 방법입니다.
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, 로고, 아이콘, 모델링, 표시 아이콘, 3D 표시 아이콘, 타일, 라이브 큐브, win32
ms.openlocfilehash: ac3d5e17614bcd1072f6843a46bf0525f441f130
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600995"
---
# <a name="implement-3d-app-launchers-win32-apps"></a>3D 앱 시작 관리자 (Win32 앱)를 구현 합니다.

> [!NOTE]
> 이 기능은 에서만 사용할 수 있습니다 최신을 실행 하는 Pc [Windows Insider](https://insider.windows.com) 항공편 (RS5), 빌드 17704 이상.

합니다 [Windows Mixed Reality 홈](navigating-the-windows-mixed-reality-home.md) 출발점 응용 프로그램을 시작 하기 전에 사용자가 이동 하는 위치입니다. 기본적으로 Win32 VR 앱과 게임을 몰입 형 헤드셋 외부에서 시작 될 있고 Windows Mixed Reality 시작 메뉴에서 "모든 앱" 목록에 나타나지 않습니다. 그러나 3D 앱 시작 관리자를 구현 하려면이 문서의 지침에 따라 몰입 형 Win32 VR 경험에서 시작할 수 Windows Mixed Reality 시작 메뉴 및 홈 환경 내에서.

몰입 형 Win32 VR 환경 distributied Steam 외부에 그렇습니다. VR 환경에 대 한 [스트림을 통해 distributed](updating-your-steamvr-application-for-windows-mixed-reality.md), 했습니다 [SteamVR 베타용 Windows Mixed Reality 업데이트](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) SteamVR 표시 하는 Windows에서 타이틀 있도록 함께 최신 Windows Insider RS5 항공편 혼합된 현실 시작 메뉴 기본 시작 관리자를 사용 하 여 자동으로 "모든 앱" 목록의입니다. 즉,이 문서에서 설명 하는 방법을 SteamVR 타이틀에 대 한 필요 하지 않으며 SteamVR 베타 기능에 대 한 Windows Mixed Reality로 재정의 됩니다.

## <a name="3d-app-launcher-creation-process"></a>3D 앱 시작 관리자 만들기 프로세스

3D 앱 시작 관리자를 작성 하는 방법은 3 단계가 있습니다.
1. [디자인 및 concepting](3d-app-launcher-design-guidance.md)
2. [모델링 및 내보내기](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. 응용 프로그램 (이 문서)에 통합

3D 자산 사용 하 여 응용 프로그램 시작 관리자를 작성 해야 하는 대로 사용 해야 합니다 [Windows Mixed Reality 작성 지침](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) 호환성을 확인 합니다. 이 제작 사양을 충족 하지 못한 자산 Windows Mixed Reality 홈에서 렌더링 되지 않습니다.

## <a name="configuring-the-3d-launcher"></a>3D 시작 관리자를 구성합니다.

Win32 응용 프로그램에는 3D 앱 시작 관리자를 만드는 경우 Windows Mixed Reality 시작 메뉴에서 "모든 앱" 목록에 표시 됩니다. 이렇게 하려면 만들기를 [시각적 요소 매니페스트](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) 다음이 단계를 수행 하 여 3D 앱 시작 관리자를 참조 하는 XML 파일:

1. 만들기는 **3D 앱 시작 관리자 자산 GLB 파일** (참조 [모델링 및 내보내기](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).
2. 만들기는 **[시각적 요소 매니페스트](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** 응용 프로그램에 대 한 합니다.
    1. 시작 합니다 [아래 샘플](#sample-visual-elements-manifest)합니다.  전체 참조 [시각적 요소 매니페스트](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) 자세한 세부 정보에 대 한 설명서입니다.
    2. 업데이트 **Square150x150Logo** 하 고 **Square70x70Logo** PNG/JPG/GIF 앱을 사용 하 여 합니다.
        * Windows Mixed Reality 모든 앱 목록에서 앱의 2D 로고 및 데스크톱에서 시작 메뉴에 대 한이 사용 됩니다.
        * 파일 경로 Visual 요소 매니페스트를 포함 하는 폴더에 상대적입니다.
        * 표준 메커니즘을 통해 앱에 대 한 시작 메뉴 아이콘 바탕 화면을 제공 해야 합니다. 이 수 있습니다 (예: 통해 IShellLink::SetIconLocation) 만든 바로 가기 또는 실행 파일에서 직접.
        * *선택 사항:* MRT 다른 해상도 비율 및 고대비 테마에 대 한 다양 한 자산 크기를 제공 하기를 원하는 경우 resources.pri 파일을 사용할 수 있습니다.
    3. 업데이트를 **MixedRealityModel 경로** 에 3D 앱 시작 관리자는 GLB를 가리키도록
    4. 실행 파일의 확장명을 가진 동일한 이름의 파일을 저장 "합니다. VisualElementsManifest.xml "을 동일한 디렉터리에 저장 합니다. 예를 들어, "contoso.exe" 실행 파일에 대 한에 해당 하는 XML 파일 이름은 "contoso.visualelementsmanifest.xml"입니다.
3. **바로 가기를 추가** 데스크톱 Windows 시작 메뉴에 응용 프로그램입니다. 참조 된 [아래 샘플](#sample-app-launcher-shortcut-creation) 예 C++ 구현 합니다. 
    * %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs (컴퓨터) 또는 %APPDATA%\Microsoft\Windows\Start Menu\Programs (사용자) 만들기
    * 시각적 요소 매니페스트 또는 참조 하는 자산 업데이트로 변경 되 면 업데이트 또는 설치 관리자를 업데이트 해야 바로 가기 매니페스트 다시 구문 분석 하 고 캐시 된 자산이 업데이트 되도록 합니다.
4. *선택 사항:* 사용자 바탕 화면 바로 가기를 경우 직접 응용 프로그램의 EXE를 가리키지 않습니다 (같은 사용자 지정 프로토콜 처리기를 호출 하는 경우에 예를 들어 "myapp: / /"), 시작 메뉴 응용 프로그램의 VisualElementsManifest.xml 파일을 찾을 자동으로 되지 않습니다. 이 해결 하려면 바로 가기의 System.AppUserModel.VisualElementsManifestHintPath ()를 사용 하 여 Visual 요소 매니페스트 파일 경로 지정 해야 합니다. 이 동일한 기술을 사용 하 여 System.AppUserModel.ID로 바로 가기에 설정할 수 있습니다. System.AppUserModel.ID 데 필요 하지 않습니다 하지만 바로 가기를 사용 하는 경우 응용 프로그램의 명시적 응용 프로그램 사용자 모델 ID와 일치 하도록 하려는 경우 수행할 수 있습니다.  참조를 [앱 시작 관리자 바로 가기 만들기 샘플](#sample-app-launcher-shortcut-creation) 에 대 한 아래 섹션을 C++ 샘플입니다.

### <a name="sample-visual-elements-manifest"></a>샘플 시각적 요소 매니페스트

```xml
<Application xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <VisualElements
    ShowNameOnSquare150x150Logo="on"
    Square150x150Logo="YOUR_APP_LOGO_150X150.png"
    Square70x70Logo=" YOUR_APP_LOGO_70X70.png"
    ForegroundText="light"
    BackgroundColor="#000000">
    <MixedRealityModel Path="YOUR_3D_APP_LAUNCHER_ASSET.glb">
        <SpatialBoundingBox Center="0,0,0" Extents="Auto" />
    </MixedRealityModel>
  </VisualElements>
</Application>
```

### <a name="sample-app-launcher-shortcut-creation"></a>샘플 앱 시작 관리자 바로 가기 만들기

아래 샘플 코드에서 바로 가기를 만드는 방법을 보여 줍니다. C++를 재정의 Visual 요소 매니페스트 XML 파일의 경로를 포함 합니다. 참고 재정의 가기 직접 매니페스트에 연결 된 (예: EXE를 가리키지 않습니다 하는 경우에만 필요 바로 가기와 같은 사용자 지정 프로토콜 처리기를 사용 하 여 "myapp: / /").

#### <a name="sample-lnk-shortcut-creation-c"></a>샘플입니다. LNK 바로 가기 만들기 (C++)

```cpp
#include <windows.h>
#include <propkey.h>
#include <shlobj_core.h>
#include <shlwapi.h>
#include <propvarutil.h>
#include <wrl.h>

#include <memory>

using namespace Microsoft::WRL;

#define RETURN_IF_FAILED(x) do { HRESULT hr = x; if (FAILED(hr)) { return hr; } } while(0)
#define RETURN_IF_WIN32_BOOL_FALSE(x) do { DWORD res = x; if (res == 0) { return HRESULT_FROM_WIN32(GetLastError()); } } while(0)

int wmain()
{
    RETURN_IF_FAILED(CoInitializeEx(nullptr, COINIT_APARTMENTTHREADED));

    ComPtr<IShellLink> shellLink;
    RETURN_IF_FAILED(CoCreateInstance(__uuidof(ShellLink), nullptr, CLSCTX_INPROC_SERVER, IID_PPV_ARGS(&shellLink)));
    RETURN_IF_FAILED(shellLink->SetPath(L"MyLauncher://launch/app-identifier"));

    // It is also possible to use an icon file in another location. For example, "C:\Program Files (x86)\MyLauncher\assets\app-identifier.ico".
    RETURN_IF_FAILED(shellLink->SetIconLocation(L"C:\\Program Files (x86)\\MyLauncher\\apps\\app-identifier\\game.exe", 0 /*iIcon*/));

    ComPtr<IPropertyStore> propStore;
    RETURN_IF_FAILED(shellLink.As(&propStore));

    {
        // Optional: If the application has an explict Application User Model ID, then you should usually specify it in the shortcut.
        PROPVARIANT propVar;
        RETURN_IF_FAILED(InitPropVariantFromString(L"ExplicitAppUserModelID", &propVar));
        RETURN_IF_FAILED(propStore->SetValue(PKEY_AppUserModel_ID, propVar));
        PropVariantClear(&propVar);
    }

    {
        // A hint path to the manifest is only necessary if the target path of the shortcut is not a file path to the executable.
        // By convention the manifest is named <executable name>.VisualElementsManifest.xml and is in the same folder as the executable
        // (and resources.pri if applicable). Assets referenced by the manifest are relative to the folder containing the manifest.

        //
        // PropKey.h
        //
        //  Name:     System.AppUserModel.VisualElementsManifestHintPath -- PKEY_AppUserModel_VisualElementsManifestHintPath
        //  Type:     String -- VT_LPWSTR  (For variants: VT_BSTR)
        //  FormatID: {9F4C2855-9F79-4B39-A8D0-E1D42DE1D5F3}, 31
        //  
        //  Suggests where to look for the VisualElementsManifest for a Win32 app
        //
        // DEFINE_PROPERTYKEY(PKEY_AppUserModel_VisualElementsManifestHintPath, 0x9F4C2855, 0x9F79, 0x4B39, 0xA8, 0xD0, 0xE1, 0xD4, 0x2D, 0xE1, 0xD5, 0xF3, 31);
        // #define INIT_PKEY_AppUserModel_VisualElementsManifestHintPath { { 0x9F4C2855, 0x9F79, 0x4B39, 0xA8, 0xD0, 0xE1, 0xD4, 0x2D, 0xE1, 0xD5, 0xF3 }, 31 }

        PROPVARIANT propVar;
        RETURN_IF_FAILED(InitPropVariantFromString(L"C:\\Program Files (x86)\\MyLauncher\\apps\\app-identifier\\game.visualelementsmanifest.xml", &propVar));
        RETURN_IF_FAILED(propStore->SetValue(PKEY_AppUserModel_VisualElementsManifestHintPath, propVar));
        PropVariantClear(&propVar);
    }

    constexpr PCWSTR shortcutPath = L"%APPDATA%\\Microsoft\\Windows\\Start Menu\\Programs\\game.lnk";
    const DWORD requiredBufferLength = ExpandEnvironmentStrings(shortcutPath, nullptr, 0);
    RETURN_IF_WIN32_BOOL_FALSE(requiredBufferLength);

    const auto expandedShortcutPath = std::make_unique<wchar_t[]>(requiredBufferLength);
    RETURN_IF_WIN32_BOOL_FALSE(ExpandEnvironmentStrings(shortcutPath, expandedShortcutPath.get(), requiredBufferLength));

    ComPtr<IPersistFile> persistFile;
    RETURN_IF_FAILED(shellLink.As(&persistFile));
    RETURN_IF_FAILED(persistFile->Save(expandedShortcutPath.get(), FALSE));

    return 0;
}
```

#### <a name="sample-url-launcher-shortcut"></a>샘플입니다. URL 시작 관리자 바로 가기 

```
[{9F4C2855-9F79-4B39-A8D0-E1D42DE1D5F3}]
Prop31=C:\Program Files (x86)\MyLauncher\apps\app-identifier\game.visualelementsmanifest.xml
Prop5=ExplicitAppUserModelID

[{000214A0-0000-0000-C000-000000000046}]
Prop3=19,0

[InternetShortcut]
IDList=
URL=MyLauncher://launch/app-identifier
IconFile=C:\Program Files (x86)\MyLauncher\apps\app-identifier\game.exe
IconIndex=0
```

## <a name="see-also"></a>참조

* [혼합된 현실 모델 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) 3D 앱 시작 관리자를 포함 합니다.
* [3D 앱 시작 관리자 디자인 지침](3d-app-launcher-design-guidance.md)
* [Windows Mixed Reality 집에서 사용할 3D 모델 만들기](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [3D 앱 시작 관리자 (UWP 앱)를 구현합니다.](implementing-3d-app-launchers.md)
* [Windows Mixed Reality 홈 탐색](navigating-the-windows-mixed-reality-home.md)
