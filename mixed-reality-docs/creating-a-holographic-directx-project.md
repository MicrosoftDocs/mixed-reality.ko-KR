---
title: Holographic DirectX 프로젝트 만들기
description: Windows Mixed Reality 앱 템플릿을 기반으로 새 holographic 앱을 만드는 방법을 설명 합니다.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, holographic 앱, 새 앱을 UWP 앱, 템플릿 앱, 홀로그램, 새 프로젝트, 연습, 다운로드, 샘플 코드
ms.openlocfilehash: 7d1ea0246cf823f74e68b4e67fbcfc275d081688
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605097"
---
# <a name="creating-a-holographic-directx-project"></a>Holographic DirectX 프로젝트 만들기

HoloLens에 대해 만들 holographic 앱을 <a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">유니버설 Windows 플랫폼 (UWP) 앱</a>합니다.  데스크톱 Windows Mixed Reality 헤드셋을 대상으로 하는 경우에 UWP 앱 또는 Win32 앱을 만들 수 있습니다.

DirectX 11 holographic UWP 앱 템플릿을 DirectX 11 UWP 앱 템플릿을;를 매우 비슷합니다. 프로그램 루프 (또는 "게임 루프")를 포함 한 **DeviceResources** Direct3D 장치 및 컨텍스트를 관리 하는 클래스와 간소화 된 콘텐츠 렌더러 클래스입니다. 또한에 <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>마찬가지로 다른 UWP 앱.

그러나 혼합된 현실 앱에는 일반적인 Direct3D 11 UWP 앱에서 존재 하지 않는 몇 가지 추가 기능에 있습니다. Windows Holographic 앱 템플릿에 수 있습니다.
* Holographic 카메라를 사용 하 여 연결 된 Direct3D 장치 리소스를 처리 합니다.
* 시스템에서 카메라 백 버퍼를 검색 합니다.
* 처리할 [gaze](gaze.md) 입력 하 고 간단한 인식 [제스처](gestures.md)합니다.
* 스테레오 렌더링 전체 화면 모드로 이동 합니다.

## <a name="how-do-i-get-started"></a>어떻게 시작 합니까?

첫 번째 [도구를 설치](install-the-tools.md), 다음 Visual Studio 2017 다운로드에 대 한 지침 및 Microsoft HoloLens 에뮬레이터. Holographic 앱 템플릿은 Microsoft HoloLens 에뮬레이터와 동일한 설치 관리자에 포함 됩니다. 또한 서식 파일을 설치 하는 옵션을 설치 하기 전에 선택 되어 있는지 확인 합니다.

이제 DirectX 11 Windows Mixed Reality 앱을 만들 준비가 되었습니다! 샘플 콘텐츠를 제거 하 여 주석 처리를 확인 합니다 **DRAW_SAMPLE_CONTENT** 전처리기 지시문 *pch.h*.

## <a name="creating-a-uwp-project"></a>UWP 프로젝트 만들기

도구 설치 되 면 다음 holographic DirectX UWP 프로젝트를 만들 수 있습니다. 새 프로젝트를 만들려면:
1. 시작 **Visual Studio**합니다.
2. **파일** 메뉴에서 **새로 만들기** 선택한 **프로젝트** 상황에 맞는 메뉴에서. 합니다 **새 프로젝트** 대화 상자가 열립니다.
3. 확장 **설치 됨** 왼쪽 확장를 **시각적 C++**  언어 노드.
4. 로 이동 합니다 **Windows 유니버설 > Holographic** 노드와 선택 **Holographic DirectX 11 앱 (유니버설 Windows) (C++/WinRT)** 합니다.
   >[!IMPORTANT]
   >프로젝트 템플릿의 이름을 포함 해야 "(C++/WinRT)".  그렇지 않은 경우 설치 된 holographic 프로젝트 템플릿의 이전 버전이 있습니다.  최신 프로젝트 템플릿을 가져오려는 [최신 HoloLens 에뮬레이터를 설치할](using-the-hololens-emulator.md)합니다.
5. 입력 합니다 **이름** 및 **위치** 텍스트 상자 및 클릭 하거나 탭 **확인**합니다. Holographic 앱 프로젝트가 만들어집니다.
6. 개발을 위한 HoloLens 2만 대상 지정 되어 있는지 확인 합니다 **대상 버전** 및 **최소 버전** 으로 설정 됩니다 **Windows 10 버전 1903**합니다.  HoloLens도 대상으로 하는 경우 (첫 번째 gen) 하거나 설정할 수 있습니다 데스크톱 Windows Mixed Reality 헤드셋 **최소 버전** 하 **Windows 10 버전 1809** 대신 일부 해야 하지만 <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank"> 버전 adapative 검사</a> HoloLens 2의 새로운 기능을 사용 하는 경우 코드에서.

![Visual Studio에서 holographic 앱 프로젝트 템플릿의 스크린샷](images/holographic-directx-app-cpp-new-project.png)<br>
*Visual Studio에서 holographic 앱 프로젝트 템플릿*

템플릿을 사용 하 여 프로젝트 생성 <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>, Windows 런타임 Api를 지 원하는 모든 표준 호환 C + + 17 컴파일러의 C + + 17 개의 언어 프로젝션 합니다.  프로젝트에는 사용자 로부터 두 미터를 배치에 전 세계 잠긴 큐브를 만드는 방법을 보여 줍니다. 사용자 수 [어 탭](gestures.md#air-tap) 큐브에 사용자 지정 된 다른 위치에 배치 하려면 컨트롤러에서 단추를 누르거나 [gaze](gaze.md)합니다. 혼합된 현실 앱을 만들려면이 프로젝트를 수정할 수 있습니다.

사용 하 여 새 프로젝트를 만들 수는 또는 **시각적 C#**  holographic 프로젝트 템플릿을 SharpDX을 기반으로 하는 합니다.  경우에 holographic C# Windows Holographic 앱 템플릿에서 프로젝트를 시작 되지 않았습니다, Windows Mixed Reality에서 ms.fxcompile.targets 파일을 복사 해야 합니다 C# HLSL 컴파일하기 위해 파일에.csproj에 템플릿 프로젝트 및 가져오기 프로젝트에 추가 하는 파일입니다.

검토 [배포 및 디버깅 Visual Studio를 사용 하 여](using-visual-studio.md) 여 HoloLens, 연결 하는 몰입 감이 뛰어난 장치를 사용 하 여 PC 또는 에뮬레이터를 샘플을 배포 하는 방법에 대 한 정보에 대 한 합니다.

사용 중인 아래 지침의 나머지 부분에서는 C++ 앱을 빌드합니다.

### <a name="uwp-app-entry-point"></a>UWP 앱 진입점

Holographic UWP 앱에서 시작 합니다 **wWinMain** AppView.cpp의 함수입니다. **wWinMain** 함수 앱을 만듭니다 <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> 하 고 시작 합니다 <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> 된 합니다.

**AppView.cpp**:

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

해당 지점에서 AppView 클래스는 Windows 기본 입력된 이벤트, CoreWindow 이벤트 및 메시징 및 등을 사용 하 여 상호 작용을 처리 합니다. 또한 앱에서 사용 하는 HolographicSpace 만들어집니다.

## <a name="creating-a-win32-project"></a>Win32 프로젝트 만들기

Win32 맞게 holographic 프로젝트는 빌드를 시작 하는 가장 쉬운 방법은 합니다 <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank"> *BasicHologram* Win32 샘플</a>합니다.

이 Win32 샘플에서는 <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>, Windows 런타임 Api를 지 원하는 모든 표준 호환 C + + 17 컴파일러의 C + + 17 개의 언어 프로젝션 합니다.  프로젝트에는 사용자 로부터 두 미터를 배치에 전 세계 잠긴 큐브를 만드는 방법을 보여 줍니다. 사용자 큐브에 사용자 지정 된 다른 위치에 배치 하려면 컨트롤러에서 단추를 눌러도 [gaze](gaze.md)합니다. 혼합된 현실 앱을 만들려면이 프로젝트를 수정할 수 있습니다.

### <a name="win32-app-entry-point"></a>Win32 응용 프로그램 진입점

Holographic Win32 앱이 시작 되는 **wWinMain** AppMain.cpp의 함수입니다. 합니다 **wWinMain** 함수 앱의 HWND를 만들고 해당 메시지 루프를 시작 합니다.

**AppMain.cpp**:

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

해당 지점에서 AppMain 클래스 등 기본적인 창 메시지와 상호 작용을 처리합니다. 또한 앱에서 사용 하는 HolographicSpace 만들어집니다.

## <a name="render-holographic-content"></a>Holographic 콘텐츠를 렌더링 합니다.

프로젝트의 **콘텐츠** 폴더에서 렌더링 홀로그램 클래스를 포함 합니다 [holographic 공간](getting-a-holographicspace.md)입니다. 템플릿에서 기본 홀로그램 사용자 반대쪽으로 두 가지 단위가 배치 되는 회전 큐브는입니다. 구현 되는이 큐브에 그리기 **SpinningCubeRenderer.cpp**, 이러한 주요 메서드 있는:

|  메서드  |  설명 | 
|----------|----------|
|  `CreateDeviceDependentResources` |  셰이더를 로드 하 고 큐브 메시를 만듭니다. | 
|  `PositionHologram` |  인수에 의해 지정 된 위치를 홀로그램 배치 <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>합니다. | 
|  `Update` |  큐브를 회전 하 고 된 모델 매트릭스를 설정 합니다. | 
|  `Render` |  꼭 짓 점 및 픽셀 셰이더를 사용 하 여 프레임을 렌더링 합니다. | 

합니다 **셰이더** 하위 폴더에 4 개의 기본 셰이더 구현이 포함 되어 있습니다.

|  셰이더  |  설명 | 
|----------|----------|
|  `GeometryShader.hlsl` |  기 하 도형 수정 되지 않은 상태로 유지 하는 통과 합니다. | 
|  `PixelShader.hlsl` |  색 데이터를 통해 전달 합니다. 색 데이터 보간 되 고 래스터화 단계에서 픽셀에 할당 합니다. | 
|  `VertexShader.hlsl` |  GPU에서 꼭 짓 점 처리를 수행 하기 위한 간단한 셰이더입니다. | 
|  `VPRTVertexShader.hlsl` |  Windows Mixed Reality 스테레오 렌더링을 위해 최적화 된 GPU에서 꼭 짓 점 처리를 수행 하기 위한 간단한 셰이더입니다. | 

`VertexShaderShared.hlsl` 간에 공유 되는 일반적인 코드를 포함 `VertexShader.hlsl` 고 `VPRTVertexShader.hlsl`입니다.

프로젝트를 빌드할 때 로드 하는 셰이더를 컴파일되는 **SpinningCubeRenderer::CreateDeviceDependentResources** 메서드.

## <a name="interact-with-your-holograms"></a>사용자 제공 상호 작용

사용자 입력에서 처리 되는 **SpatialInputHandler** 클래스는 가져옵니다를 <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a> 인스턴스를 구독 하는 <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a> 이벤트. 그러면 어 탭 제스처 및 기타 공간 입력된 이벤트를 검색 합니다.

## <a name="update-holographic-content"></a>Holographic 콘텐츠 업데이트

기본적으로에서 구현 되는 게임 루프에서 혼합된 현실 앱 업데이트를 **업데이트** 메서드에서 `AppMain.cpp`합니다. 합니다 **업데이트** 회전 큐브를 같은 장면 개체를 업데이트 하 고 반환 하는 메서드를 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> 최신 뷰 및 투영 행렬을 가져오고 스왑 체인을 제공 하는 개체입니다.

**렌더링** 에서 메서드 `AppMain.cpp` 는 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> 하 고 각 holographic 카메라 위치 지정 공간 상태 확인 하 고 현재 앱에 따라 현재 프레임을 렌더링 합니다.

## <a name="see-also"></a>참조
* [HolographicSpace 가져오기](getting-a-holographicspace.md)
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a>
* [DirectX의 렌더링](rendering-in-directx.md)
* [Visual Studio를 사용 하 여 배포 및 디버깅](using-visual-studio.md)
* [Using the HoloLens emulator(HoloLens 에뮬레이터 사용)](using-the-hololens-emulator.md)
* [Holographic DirectX 앱에서 XAML 사용](using-xaml-with-holographic-directx-apps.md)
