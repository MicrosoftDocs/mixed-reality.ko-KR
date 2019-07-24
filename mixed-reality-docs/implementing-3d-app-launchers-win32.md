---
title: 3D 앱 응용 프로그램 구현 (Win32 앱)
description: Win32 VR 앱 및 게임 (스트림 외부에 배포)에 3D 앱 시작 및 로고를 만드는 방법으로, Windows Mixed Reality 시작 메뉴 및 홈 환경에 표시 됩니다.
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, 로고, 아이콘, 모델링, 시작 관리자, 3D 시작 관리자, 타일, 라이브 큐브, win32
ms.openlocfilehash: ac3d5e17614bcd1072f6843a46bf0525f441f130
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63515609"
---
# <a name="implement-3d-app-launchers-win32-apps"></a>3D 앱 응용 프로그램 구현 (Win32 앱)

> [!NOTE]
> 이 기능은 최신 [Windows 참가자](https://insider.windows.com) 항공편 (RS5), 빌드 17704 이상 버전을 실행 하는 pc 에서만 사용할 수 있습니다.

[Windows Mixed Reality 홈](navigating-the-windows-mixed-reality-home.md) 은 사용자가 응용 프로그램을 시작 하기 전에 수행 하는 시작 지점입니다. 기본적으로 모던 Win32 VR 앱 및 게임은 헤드셋 외부에서 시작 해야 하며 Windows Mixed Reality 시작 메뉴의 "모든 앱" 목록에 나타나지 않습니다. 그러나이 문서의 지침에 따라 3D 앱 시작 관리자를 구현 하면 Windows Mixed Reality 시작 메뉴 및 홈 환경에서 몰입 형 Win32 VR 환경을 시작할 수 있습니다.

이는 스트림 외부에서 distributied 하는 모던 Win32 VR 환경에만 적용 됩니다. [스트림를 통해 배포](updating-your-steamvr-application-for-windows-mixed-reality.md)되는 VR 환경의 경우 [SteamVR Beta에 대 한 windows mixed Reality](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) 를 최신 windows 참가자 RS5 항공편과 함께 업데이트 하 여 "모든 앱" 목록의 windows mixed Reality 시작 메뉴에 SteamVR 제목이 표시 되도록 합니다. 기본 시작 관리자를 자동으로 사용 합니다. 즉,이 문서에서 설명 하는 메서드는 SteamVR 제목에는 필요 하지 않으며 SteamVR Beta 기능을 위해 Windows Mixed Reality에 의해 재정의 됩니다.

## <a name="3d-app-launcher-creation-process"></a>3D 앱 시작 관리자 만들기 프로세스

3D 앱 시작 관리자를 만드는 단계는 세 가지입니다.
1. [디자인 및 concepting](3d-app-launcher-design-guidance.md)
2. [모델링 및 내보내기](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. 응용 프로그램에 통합 (이 문서)

응용 프로그램에 대 한 관리자로 사용할 3D 자산은 호환성을 보장 하기 위해 [Windows Mixed Reality 제작 지침](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) 을 사용 하 여 작성 해야 합니다. 이 제작 사양을 충족 하지 못하는 자산은 Windows Mixed Reality 홈에서 렌더링 되지 않습니다.

## <a name="configuring-the-3d-launcher"></a>3D 시작 관리자 구성

Win32 응용 프로그램은 3D 앱 시작 관리자를 만드는 경우 Windows Mixed Reality 시작 메뉴의 "모든 앱" 목록에 표시 됩니다. 이렇게 하려면 다음 단계를 수행 하 여 3D 앱 시작 관리자를 참조 하는 [시각적 요소 매니페스트](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) XML 파일을 만듭니다.

1. **3D 앱 시작 관리자 자산 및 파일** 만들기 ( [모델링 및 내보내기](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)참조)
2. 응용 프로그램에 대 한 **[시각적 요소 매니페스트](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** 를 만듭니다.
    1. [아래 샘플](#sample-visual-elements-manifest)에서 시작할 수 있습니다.  자세한 내용은 전체 [시각적 요소 매니페스트](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) 설명서를 참조 하세요.
    2. **Square150x150Logo** 및 **Square70x70Logo** 를 앱에 대 한 PNG/JPG/GIF로 업데이트 합니다.
        * 이러한 응용 프로그램은 Windows Mixed Reality의 모든 앱 목록과 데스크톱의 시작 메뉴에서 앱의 2D 로고에 사용 됩니다.
        * 파일 경로는 시각적 요소 매니페스트를 포함 하는 폴더에 대 한 상대 경로입니다.
        * 표준 메커니즘을 통해 앱에 대 한 바탕 화면 시작 메뉴 아이콘을 계속 제공 해야 합니다. 이는 실행 파일에 직접 또는 직접 만든 바로 가기 (예: IShellLink:: SetIconLocation을 통해)에 있을 수 있습니다.
        * *필드* MRT.LOG에서 다양 한 해상도 크기 조정 및 고대비 테마에 대 한 여러 자산 크기를 제공 하려는 경우에는 리소스 .pri 파일을 사용할 수 있습니다.
    3. 3D 앱 시작 관리자에 대 한 지 수 b를 가리키도록 **MixedRealityModel 경로** 를 업데이트 합니다.
    4. 실행 파일과 동일한 이름으로 파일을 저장 합니다 .이 파일의 확장명은 "입니다. VisualElementsManifest "를 찾아 동일한 디렉터리에 저장 합니다. 예를 들어 "contoso .exe" 실행 파일의 경우 해당 XML 파일의 이름은 "visualelementsmanifest"입니다.
3. 응용 프로그램의 **바로 가기를** 바탕 화면 Windows 시작 메뉴에 추가 합니다. 예제 C++ 구현은 [아래 샘플](#sample-app-launcher-shortcut-creation) 을 참조 하세요. 
    * %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs (machine) 또는%APPDATA%\Microsoft\Windows\Start Menu\Programs (사용자)에 만듭니다.
    * 업데이트에서 시각적 요소 매니페스트 또는이를 참조 하는 자산을 변경 하는 경우 매니페스트가 다시 구문 분석 캐시 된 자산이 업데이트 되도록 업데이트 프로그램 또는 설치 관리자에서 바로 가기를 업데이트 해야 합니다.
4. *필드* 바탕 화면 바로 가기가 응용 프로그램의 EXE를 직접 가리키지 않는 경우 (예: "myapp://"와 같은 사용자 지정 프로토콜 처리기를 호출 하는 경우) 시작 메뉴에서 앱의 VisualElementsManifest 파일을 자동으로 찾을 수 없습니다. 이 문제를 해결 하려면 바로 가기에서 VisualElementsManifestHintPath ()를 사용 하 여 시각적 요소 매니페스트의 파일 경로를 지정 해야 합니다. System.AppUserModel.ID와 동일한 기법을 사용 하 여 바로 가기에서 설정할 수 있습니다. System.AppUserModel.ID를 사용할 필요는 없지만 응용 프로그램의 명시적인 응용 프로그램 사용자 모델 ID (사용 되는 경우)와 일치 하는 바로 가기를 만들려는 경우이 작업을 수행할 수 있습니다.  샘플은 C++ 아래의 [샘플 앱 시작 관리자 바로 가기 생성](#sample-app-launcher-shortcut-creation) 섹션을 참조 하세요.

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

아래 샘플 코드에서는 시각적 요소 매니페스트 XML 파일에 대 한 C++경로 재정의를 비롯 하 여에서 바로 가기를 만들 수 있는 방법을 보여 줍니다. 이 재정의는 바로 가기가 매니페스트와 연결 된 EXE를 직접 가리키지 않는 경우에만 필요 합니다 (예: 바로 가기는 "myapp://"와 같은 사용자 지정 프로토콜 처리기를 사용 합니다.

#### <a name="sample-lnk-shortcut-creation-c"></a>샘플이. L n k 바로C++가기 만들기 ()

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

#### <a name="sample-url-launcher-shortcut"></a>샘플이. URL 시작 관리자 바로 가기 

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

* 3D 앱 시작 관리자를 포함 하는 [혼합 현실 모델 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) 입니다.
* [3D 앱 시작 관리자 디자인 지침](3d-app-launcher-design-guidance.md)
* [Windows Mixed Reality 홈에서 사용할 3D 모델 만들기](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [3D 앱 응용 프로그램 구현 (UWP 앱)](implementing-3d-app-launchers.md)
* [Windows Mixed Reality 홈 탐색](navigating-the-windows-mixed-reality-home.md)
