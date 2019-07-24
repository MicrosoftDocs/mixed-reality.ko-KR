---
title: Holographic DirectX 프로젝트 만들기
description: Windows Mixed Reality 앱 템플릿을 기반으로 새 holographic 앱을 만드는 방법을 설명 합니다.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, holographic 앱, 새 앱, UWP 앱, 템플릿 앱, holograms, 새 프로젝트, 연습, 다운로드, 샘플 코드
ms.openlocfilehash: 24f217021cd448f19a744696de42f580f139f76f
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387622"
---
# <a name="creating-a-holographic-directx-project"></a>Holographic DirectX 프로젝트 만들기

HoloLens 용으로 만드는 holographic 앱은 <a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">UWP (유니버설 Windows 플랫폼) 앱</a>입니다.  데스크톱 Windows Mixed Reality 헤드셋을 대상으로 하는 경우 UWP 앱 또는 Win32 앱을 만들 수 있습니다.

DirectX 11 holographic UWP 앱 템플릿은 DirectX 11 UWP 앱 템플릿과 매우 유사 합니다. 여기에는 프로그램 루프 (또는 "게임 루프"), Direct3D 장치 및 컨텍스트를 관리 하는 **DeviceResources** 클래스, 간소화 된 콘텐츠 렌더러 클래스가 포함 됩니다. 다른 UWP 앱과 마찬가지로 <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>도 있습니다.

그러나 혼합 현실 앱에는 일반적인 Direct3D 11 UWP 앱에 없는 몇 가지 추가 기능이 있습니다. Windows Holographic 앱 템플릿은 다음을 수행할 수 있습니다.
* Holographic 카메라와 연결 된 Direct3D 장치 리소스를 처리 합니다.
* 시스템에서 카메라 백 버퍼를 검색 합니다.
* [응시](gaze.md) 하는 입력을 처리 하 고 간단한 [제스처](gestures.md)를 인식 합니다.
* 전체 화면 스테레오 렌더링 모드로 전환 합니다.

## <a name="how-do-i-get-started"></a>시작 어떻게 할까요?

먼저 Visual Studio 2019 및 Microsoft HoloLens 에뮬레이터 다운로드 지침에 따라 [도구를 설치](install-the-tools.md)합니다. Holographic 앱 템플릿은 Microsoft HoloLens 에뮬레이터와 동일한 설치 관리자에 포함 되어 있습니다. 또한를 설치 하기 전에 템플릿을 설치 하는 옵션을 선택 해야 합니다.

이제 DirectX 11 Windows Mixed Reality 앱을 만들 준비가 되었습니다. 샘플 콘텐츠를 제거 하려면 **DRAW_SAMPLE_CONTENT** *의 전처리기*지시문을 주석으로 처리 합니다.

## <a name="creating-a-uwp-project"></a>UWP 프로젝트 만들기

도구를 [설치한](install-the-tools.md) 후에는 HOLOGRAPHIC DirectX UWP 프로젝트를 만들 수 있습니다.

새 프로젝트를 만들려면 다음을 수행 합니다.
1. **Visual Studio**를 시작 합니다.
2. **파일** 메뉴에서 **새로 만들기** 를 가리킨 다음 상황에 맞는 메뉴에서 **프로젝트** 를 선택 합니다. **새 프로젝트** 대화 상자가 열립니다.
3. 왼쪽에서 **설치** 를 확장 하 고 **비주얼 C++**  언어 노드를 확장 합니다.
4. **Windows universal > Holographic** 노드로 이동 하 고 **Holographic DirectX 11 앱 (유니버설 Windows) (C++/winrt)** 을 선택 합니다.
   ![Visual Studio에서 Holographic DirectX 11 C++/WINRT UWP 앱 프로젝트 템플릿의 스크린샷](images/holographic-directx-app-cpp-new-project.png)<br>
   *Visual Studio의 C++Holographic DirectX 11/WINRT UWP 앱 프로젝트 템플릿*
   >[!IMPORTANT]
   >프로젝트 템플릿의 이름에 "(C++/winrt)"가 포함 되어 있어야 합니다.  그렇지 않으면 이전 버전의 holographic 프로젝트 템플릿이 설치 되어 있는 것입니다.  최신 프로젝트 템플릿을 가져오려면 [최신 HoloLens 에뮬레이터를 설치](using-the-hololens-emulator.md)합니다.
5. **이름** 및 **위치** 텍스트 상자를 입력 하 고 **확인**을 클릭 하거나 탭 합니다. Holographic app 프로젝트가 생성 됩니다.
6. HoloLens를 대상으로 하는 개발의 경우 **대상 버전** 및 **최소 버전이** **Windows 10, 버전 1903**으로 설정 되어 있는지 확인 합니다.  HoloLens (첫 번째 gen) 또는 데스크톱 Windows Mixed Reality 헤드셋도 대상으로 지정 하는 경우 **Windows 10, 버전 1809** 의 **최소 버전** 을 대신 지정할 수 있습니다. 단, 새로 사용 하는 경우 코드에서 일부 <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">버전 적응 검사가</a> 필요 합니다. HoloLens 2의 기능.
   ![Windows 10 버전 1903을 대상으로 설정 하 고 최소 버전으로 설정 하는 스크린샷](images/new-uwp-project.png)<br>
   ***Windows 10, 버전 1903을** 대상 및 최소 버전으로 설정*
   >[!IMPORTANT]
   >**Windows 10, 버전 1903** 이 옵션으로 표시 되지 않는 경우 최신 WINDOWS 10 SDK가 설치 되어 있지 않습니다.  이 옵션을 표시 하려면 <a href="https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk" target="_blank">Windows 10 SDK 버전 10.0.18362.0 이상을 설치</a>합니다.

템플릿은 표준 규격 c + + 17 컴파일러를 지 원하는 Windows 런타임 api의 c + + 17 언어 프로젝션 인 <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/winrt</a>를 사용 하 여 프로젝트를 생성 합니다.  이 프로젝트에서는 사용자 로부터 2 미터 배치 된 전 세계 잠긴 큐브를 만드는 방법을 보여 줍니다. 사용자는 컨트롤러의 단추를 [클릭 하거나 눌러](gestures.md#air-tap) 사용자의 [응시](gaze.md)에 지정 된 다른 위치에 큐브를 배치할 수 있습니다. 이 프로젝트를 수정 하 여 혼합 현실 앱을 만들 수 있습니다.

또는 SharpDX를 기반으로 하는 **Visual C#**  holographic 프로젝트 템플릿을 사용 하 여 새 프로젝트를 만들 수 있습니다.  Windows Holographic 앱 C# 템플릿에서 holographic 프로젝트를 시작 하지 않은 경우에는 Windows Mixed Reality C# 템플릿 프로젝트에서 fxcompile 파일을 복사 하 여 해당 .CSPROJ 파일에서 가져와야 HLSL를 컴파일합니다. 프로젝트에 추가 하는 파일입니다.

샘플을 빌드 및 배포 하는 방법에 대 한 자세한 내용은 [Visual Studio를 사용 하 여 배포 하 고 디버깅](using-visual-studio.md) 하는 방법에 대 한 정보를 참조 하세요.

아래 지침의 나머지 부분에서는를 사용 C++ 하 여 앱을 빌드하는 것으로 가정 합니다.

### <a name="uwp-app-entry-point"></a>UWP 앱 진입점

Holographic UWP 앱은 AppView .cpp의 **Wwinmain** 함수에서 시작 합니다. **Wwinmain** 함수는 앱의 <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> 를 만들고이를 사용 하 여 <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> 를 시작 합니다.

**Appview .cpp**에서:

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

이 시점부터 AppView 클래스는 Windows 기본 입력 이벤트, CoreWindow 이벤트 및 메시징과의 상호 작용을 처리 합니다. 또한 앱에서 사용 하는 HolographicSpace를 만듭니다.

## <a name="creating-a-win32-project"></a>Win32 프로젝트 만들기

Win32 holographic 프로젝트 빌드를 시작 하는 가장 쉬운 방법은 <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank"> *basichologram* win32 샘플</a>을 조정 하는 것입니다.

이 Win32 샘플은 표준 규격 c + + 17 컴파일러를 지 원하는 Windows 런타임 api에 대 한 c + + 17 언어 투영 인 <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/winrt</a>를 사용 합니다.  이 프로젝트에서는 사용자 로부터 2 미터 배치 된 전 세계 잠긴 큐브를 만드는 방법을 보여 줍니다. 사용자는 컨트롤러의 단추를 눌러 사용자의 [응시](gaze.md)에 지정 된 다른 위치에 큐브를 배치할 수 있습니다. 이 프로젝트를 수정 하 여 혼합 현실 앱을 만들 수 있습니다.

### <a name="win32-app-entry-point"></a>Win32 앱 진입점

Holographic Win32 앱은 AppMain .cpp의 **Wwinmain** 함수에서 시작 합니다. **Wwinmain** 함수는 응용 프로그램의 HWND를 만들고 메시지 루프를 시작 합니다.

**Appmain .cpp**에서:

```cpp
int APIENTRY wWinMain(
    _In_     HINSTANCE hInstance,
    _In_opt_ HINSTANCE hPrevInstance,
    _In_     LPWSTR    lpCmdLine,
    _In_     int       nCmdShow)
{
    UNREFERENCED_PARAMETER(hPrevInstance);
    UNREFERENCED_PARAMETER(lpCmdLine);

    winrt::init_apartment();

    App app;

    // Initialize global strings, and perform application initialization.
    app.Initialize(hInstance);

    // Create the HWND and the HolographicSpace.
    app.CreateWindowAndHolographicSpace(hInstance, nCmdShow);

    // Main message loop:
    app.Run(hInstance);

    // Perform application teardown.
    app.Uninitialize();

    return 0;
}
```

이 시점부터 AppMain 클래스는 기본 창 메시지와의 상호 작용을 처리 합니다. 또한 앱에서 사용 하는 HolographicSpace를 만듭니다.

## <a name="render-holographic-content"></a>Holographic 내용 렌더링

프로젝트의 **Content** 폴더에는 [holographic 공간](getting-a-holographicspace.md)에 holograms를 렌더링 하기 위한 클래스가 포함 되어 있습니다. 템플릿의 기본 홀로그램은 사용자 로부터 두 미터 떨어진 회전 하는 큐브입니다. 이 큐브 그리기는 다음과 같은 주요 메서드를 포함 하는 **SpinningCubeRenderer**에서 구현 됩니다.

|  메서드  |  설명 | 
|----------|----------|
|  `CreateDeviceDependentResources` |  셰이더를 로드 하 고 큐브 메시를 만듭니다. | 
|  `PositionHologram` |  제공 된 <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>에 지정 된 위치에 홀로그램을 배치 합니다. | 
|  `Update` |  큐브를 회전 하 고 모델 매트릭스를 설정 합니다. | 
|  `Render` |  꼭 짓 점 및 픽셀 셰이더를 사용 하 여 프레임을 렌더링 합니다. | 

**셰이더** 하위 폴더에는 네 가지 기본 셰이더 구현이 있습니다.

|  셰이더가  |  설명 | 
|----------|----------|
|  `GeometryShader.hlsl` |  기 하 도형을 수정 되지 않은 상태로 유지 하는 통과입니다. | 
|  `PixelShader.hlsl` |  색 데이터를 통과 합니다. 색 데이터는 래스터화 단계에서 보간된 후 픽셀에 할당 됩니다. | 
|  `VertexShader.hlsl` |  GPU에서 꼭 짓 점 처리를 수행 하기 위한 간단한 셰이더입니다. | 
|  `VPRTVertexShader.hlsl` |  GPU에서 꼭 짓 점 처리를 수행 하는 간단한 셰이더가 Windows Mixed Reality 스테레오 렌더링에 최적화 되어 있습니다. | 

`VertexShaderShared.hlsl`와 사이 `VertexShader.hlsl` 에 공유 되는 `VPRTVertexShader.hlsl`공통 코드를 포함 합니다.

셰이더는 프로젝트가 빌드될 때 컴파일되고 **SpinningCubeRenderer:: CreateDeviceDependentResources** 메서드에 로드 됩니다.

## <a name="interact-with-your-holograms"></a>Holograms와 상호 작용

사용자 입력은 <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a> 인스턴스를 가져오고 <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">sourcepressed</a> 이벤트를 구독 하는 **SpatialInputHandler** 클래스에서 처리 됩니다. 그러면 공기 탭 제스처와 기타 공간 입력 이벤트를 검색할 수 있습니다.

## <a name="update-holographic-content"></a>Holographic 콘텐츠 업데이트

혼합 현실 앱은 기본적으로의 `AppMain.cpp` **업데이트** 메서드에서 구현 되는 게임 루프에서 업데이트 됩니다. **Update** 메서드는 회전 큐브와 같은 장면 개체를 업데이트 하 고 최신 뷰 및 프로젝션 매트릭스를 가져오고 스왑 체인을 표시 하는 데 사용 되는 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> 개체를 반환 합니다.

의  `AppMain.cpp` Render 메서드는 현재 앱 및 공간 위치 지정 상태에 따라 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> 을 사용 하 여 각 holographic 카메라에 현재 프레임을 렌더링 합니다.

## <a name="see-also"></a>참조
* [HolographicSpace 받기](getting-a-holographicspace.md)
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a>
* [DirectX의 렌더링](rendering-in-directx.md)
* [Visual Studio를 사용하여 앱 배포 및 디버깅](using-visual-studio.md)
* [Using the HoloLens emulator(HoloLens 에뮬레이터 사용)](using-the-hololens-emulator.md)
* [홀로그램 DirectX 앱에서 XAML 사용](using-xaml-with-holographic-directx-apps.md)
