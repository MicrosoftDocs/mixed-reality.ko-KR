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
# <a name="creating-a-holographic-directx-project"></a><span data-ttu-id="1b908-104">Holographic DirectX 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="1b908-104">Creating a holographic DirectX project</span></span>

<span data-ttu-id="1b908-105">HoloLens 용으로 만드는 holographic 앱은 <a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">UWP (유니버설 Windows 플랫폼) 앱</a>입니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-105">A holographic app you create for a HoloLens will be a <a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">Universal Windows Platform (UWP) app</a>.</span></span>  <span data-ttu-id="1b908-106">데스크톱 Windows Mixed Reality 헤드셋을 대상으로 하는 경우 UWP 앱 또는 Win32 앱을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-106">If targeting desktop Windows Mixed Reality headsets, you can create a UWP app or a Win32 app.</span></span>

<span data-ttu-id="1b908-107">DirectX 11 holographic UWP 앱 템플릿은 DirectX 11 UWP 앱 템플릿과 매우 유사 합니다. 여기에는 프로그램 루프 (또는 "게임 루프"), Direct3D 장치 및 컨텍스트를 관리 하는 **DeviceResources** 클래스, 간소화 된 콘텐츠 렌더러 클래스가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-107">The DirectX 11 holographic UWP app template is much like the DirectX 11 UWP app template; it includes a program loop (or "game loop"), a **DeviceResources** class to manage the Direct3D device and context, and a simplified content renderer class.</span></span> <span data-ttu-id="1b908-108">다른 UWP 앱과 마찬가지로 <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-108">It also has an <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>, just like any other UWP app.</span></span>

<span data-ttu-id="1b908-109">그러나 혼합 현실 앱에는 일반적인 Direct3D 11 UWP 앱에 없는 몇 가지 추가 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-109">The mixed reality app, however, has some additional capabilities that aren't present in a typical Direct3D 11 UWP app.</span></span> <span data-ttu-id="1b908-110">Windows Holographic 앱 템플릿은 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-110">The Windows Holographic app template is able to:</span></span>
* <span data-ttu-id="1b908-111">Holographic 카메라와 연결 된 Direct3D 장치 리소스를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-111">Handle Direct3D device resources associated with holographic cameras.</span></span>
* <span data-ttu-id="1b908-112">시스템에서 카메라 백 버퍼를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-112">Retrieve camera back buffers from the system.</span></span>
* <span data-ttu-id="1b908-113">[응시](gaze.md) 하는 입력을 처리 하 고 간단한 [제스처](gestures.md)를 인식 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-113">Handle [gaze](gaze.md) input, and recognize a simple [gesture](gestures.md).</span></span>
* <span data-ttu-id="1b908-114">전체 화면 스테레오 렌더링 모드로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-114">Go into full-screen stereo rendering mode.</span></span>

## <a name="how-do-i-get-started"></a><span data-ttu-id="1b908-115">시작 어떻게 할까요?</span><span class="sxs-lookup"><span data-stu-id="1b908-115">How do I get started?</span></span>

<span data-ttu-id="1b908-116">먼저 Visual Studio 2019 및 Microsoft HoloLens 에뮬레이터 다운로드 지침에 따라 [도구를 설치](install-the-tools.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-116">First [install the tools](install-the-tools.md), following the instructions on downloading Visual Studio 2019 and the Microsoft HoloLens emulator.</span></span> <span data-ttu-id="1b908-117">Holographic 앱 템플릿은 Microsoft HoloLens 에뮬레이터와 동일한 설치 관리자에 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-117">The holographic app templates are included in the same installer as the Microsoft HoloLens emulator.</span></span> <span data-ttu-id="1b908-118">또한를 설치 하기 전에 템플릿을 설치 하는 옵션을 선택 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-118">Also ensure that the option to install the templates is selected before installing.</span></span>

<span data-ttu-id="1b908-119">이제 DirectX 11 Windows Mixed Reality 앱을 만들 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-119">Now you're ready to create your DirectX 11 Windows Mixed Reality app!</span></span> <span data-ttu-id="1b908-120">샘플 콘텐츠를 제거 하려면 **DRAW_SAMPLE_CONTENT** *의 전처리기*지시문을 주석으로 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-120">Note, to remove the sample content, comment out the **DRAW_SAMPLE_CONTENT** preprocessor directive in *pch.h*.</span></span>

## <a name="creating-a-uwp-project"></a><span data-ttu-id="1b908-121">UWP 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="1b908-121">Creating a UWP project</span></span>

<span data-ttu-id="1b908-122">도구를 [설치한](install-the-tools.md) 후에는 HOLOGRAPHIC DirectX UWP 프로젝트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-122">Once the [tools are installed](install-the-tools.md) you can then create a holographic DirectX UWP project.</span></span>

<span data-ttu-id="1b908-123">새 프로젝트를 만들려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-123">To create a new project:</span></span>
1. <span data-ttu-id="1b908-124">**Visual Studio**를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-124">Start **Visual Studio**.</span></span>
2. <span data-ttu-id="1b908-125">**파일** 메뉴에서 **새로 만들기** 를 가리킨 다음 상황에 맞는 메뉴에서 **프로젝트** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-125">From the **File** menu, point to **New** and select **Project** from the context menu.</span></span> <span data-ttu-id="1b908-126">**새 프로젝트** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-126">The **New Project** dialog opens.</span></span>
3. <span data-ttu-id="1b908-127">왼쪽에서 **설치** 를 확장 하 고 **비주얼 C++**  언어 노드를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-127">Expand **Installed** on the left and expand the **Visual C++** language node.</span></span>
4. <span data-ttu-id="1b908-128">**Windows universal > Holographic** 노드로 이동 하 고 **Holographic DirectX 11 앱 (유니버설 Windows) (C++/winrt)** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-128">Navigate to the **Windows Universal > Holographic** node and select **Holographic DirectX 11 App (Universal Windows) (C++/WinRT)**.</span></span>
   <span data-ttu-id="1b908-129">![Visual Studio에서 Holographic DirectX 11 C++/WINRT UWP 앱 프로젝트 템플릿의 스크린샷](images/holographic-directx-app-cpp-new-project.png)</span><span class="sxs-lookup"><span data-stu-id="1b908-129">![Screenshot of the Holographic DirectX 11 C++/WinRT UWP app project template in Visual Studio](images/holographic-directx-app-cpp-new-project.png)</span></span><br>
   <span data-ttu-id="1b908-130">*Visual Studio의 C++Holographic DirectX 11/WINRT UWP 앱 프로젝트 템플릿*</span><span class="sxs-lookup"><span data-stu-id="1b908-130">*Holographic DirectX 11 C++/WinRT UWP app project template in Visual Studio*</span></span>
   >[!IMPORTANT]
   ><span data-ttu-id="1b908-131">프로젝트 템플릿의 이름에 "(C++/winrt)"가 포함 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-131">Be sure that the project template's name includes "(C++/WinRT)".</span></span>  <span data-ttu-id="1b908-132">그렇지 않으면 이전 버전의 holographic 프로젝트 템플릿이 설치 되어 있는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-132">If not, you have an older version of the holographic project templates installed.</span></span>  <span data-ttu-id="1b908-133">최신 프로젝트 템플릿을 가져오려면 [최신 HoloLens 에뮬레이터를 설치](using-the-hololens-emulator.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-133">To get the latest project templates, [install the latest HoloLens Emulator](using-the-hololens-emulator.md).</span></span>
5. <span data-ttu-id="1b908-134">**이름** 및 **위치** 텍스트 상자를 입력 하 고 **확인**을 클릭 하거나 탭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-134">Fill in the **Name** and **Location** text boxes, and click or tap **OK**.</span></span> <span data-ttu-id="1b908-135">Holographic app 프로젝트가 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-135">The holographic app project is created.</span></span>
6. <span data-ttu-id="1b908-136">HoloLens를 대상으로 하는 개발의 경우 **대상 버전** 및 **최소 버전이** **Windows 10, 버전 1903**으로 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-136">For development targeting only HoloLens 2, ensure that the **Target version** and **Minimum version** are set to **Windows 10, version 1903**.</span></span>  <span data-ttu-id="1b908-137">HoloLens (첫 번째 gen) 또는 데스크톱 Windows Mixed Reality 헤드셋도 대상으로 지정 하는 경우 **Windows 10, 버전 1809** 의 **최소 버전** 을 대신 지정할 수 있습니다. 단, 새로 사용 하는 경우 코드에서 일부 <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">버전 적응 검사가</a> 필요 합니다. HoloLens 2의 기능.</span><span class="sxs-lookup"><span data-stu-id="1b908-137">If you are also targeting HoloLens (1st gen) or desktop Windows Mixed Reality headsets, you can set **Minimum version** to **Windows 10, version 1809** instead, although this will require some <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">version adaptive checks</a> in your code when using new features of HoloLens 2.</span></span>
   <span data-ttu-id="1b908-138">![Windows 10 버전 1903을 대상으로 설정 하 고 최소 버전으로 설정 하는 스크린샷](images/new-uwp-project.png)</span><span class="sxs-lookup"><span data-stu-id="1b908-138">![Screenshot of setting Windows 10, version 1903 as the target and minimum versions](images/new-uwp-project.png)</span></span><br>
   <span data-ttu-id="1b908-139">***Windows 10, 버전 1903을** 대상 및 최소 버전으로 설정*</span><span class="sxs-lookup"><span data-stu-id="1b908-139">*Setting **Windows 10, version 1903** as the target and minimum versions*</span></span>
   >[!IMPORTANT]
   ><span data-ttu-id="1b908-140">**Windows 10, 버전 1903** 이 옵션으로 표시 되지 않는 경우 최신 WINDOWS 10 SDK가 설치 되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-140">If you do not see **Windows 10, version 1903** as an option, you do not have the latest Windows 10 SDK installed.</span></span>  <span data-ttu-id="1b908-141">이 옵션을 표시 하려면 <a href="https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk" target="_blank">Windows 10 SDK 버전 10.0.18362.0 이상을 설치</a>합니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-141">To get this option to appear, <a href="https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk" target="_blank">install version 10.0.18362.0 or later of the Windows 10 SDK</a>.</span></span>

<span data-ttu-id="1b908-142">템플릿은 표준 규격 c + + 17 컴파일러를 지 원하는 Windows 런타임 api의 c + + 17 언어 프로젝션 인 <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/winrt</a>를 사용 하 여 프로젝트를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-142">The template generates a project using <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank">C++/WinRT</a>, a C++17 language projection of the Windows Runtime APIs that supports any standards-compliant C++17 compiler.</span></span>  <span data-ttu-id="1b908-143">이 프로젝트에서는 사용자 로부터 2 미터 배치 된 전 세계 잠긴 큐브를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-143">The project shows how to create a world-locked cube that's placed two meters from the user.</span></span> <span data-ttu-id="1b908-144">사용자는 컨트롤러의 단추를 [클릭 하거나 눌러](gestures.md#air-tap) 사용자의 [응시](gaze.md)에 지정 된 다른 위치에 큐브를 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-144">The user can [air-tap](gestures.md#air-tap) or press a button on the controller to place the cube in a different position that's specified by the user's [gaze](gaze.md).</span></span> <span data-ttu-id="1b908-145">이 프로젝트를 수정 하 여 혼합 현실 앱을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-145">You can modify this project to create any mixed reality app.</span></span>

<span data-ttu-id="1b908-146">또는 SharpDX를 기반으로 하는 **Visual C#**  holographic 프로젝트 템플릿을 사용 하 여 새 프로젝트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-146">Alternatively, you can create a new project using the **Visual C#** holographic project template, which is based on SharpDX.</span></span>  <span data-ttu-id="1b908-147">Windows Holographic 앱 C# 템플릿에서 holographic 프로젝트를 시작 하지 않은 경우에는 Windows Mixed Reality C# 템플릿 프로젝트에서 fxcompile 파일을 복사 하 여 해당 .CSPROJ 파일에서 가져와야 HLSL를 컴파일합니다. 프로젝트에 추가 하는 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-147">If your holographic C# project did not start from the Windows Holographic app template, you will need to copy the ms.fxcompile.targets file from a Windows Mixed Reality C# template project and import it in your .csproj file in order to compile HLSL files that you add to your project.</span></span>

<span data-ttu-id="1b908-148">샘플을 빌드 및 배포 하는 방법에 대 한 자세한 내용은 [Visual Studio를 사용 하 여 배포 하 고 디버깅](using-visual-studio.md) 하는 방법에 대 한 정보를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1b908-148">Review [Using Visual Studio to deploy and debug](using-visual-studio.md) for information on how to build and deploy the sample to your HoloLens, PC with immersive device attached, or an emulator.</span></span>

<span data-ttu-id="1b908-149">아래 지침의 나머지 부분에서는를 사용 C++ 하 여 앱을 빌드하는 것으로 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-149">The rest of the instructions below will assume that you are using C++ to build your app.</span></span>

### <a name="uwp-app-entry-point"></a><span data-ttu-id="1b908-150">UWP 앱 진입점</span><span class="sxs-lookup"><span data-stu-id="1b908-150">UWP app entry point</span></span>

<span data-ttu-id="1b908-151">Holographic UWP 앱은 AppView .cpp의 **Wwinmain** 함수에서 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-151">Your holographic UWP app starts in the **wWinMain** function in AppView.cpp.</span></span> <span data-ttu-id="1b908-152">**Wwinmain** 함수는 앱의 <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> 를 만들고이를 사용 하 여 <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> 를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-152">The **wWinMain** function creates the app's <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> and starts the <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> with it.</span></span>

<span data-ttu-id="1b908-153">**Appview .cpp**에서:</span><span class="sxs-lookup"><span data-stu-id="1b908-153">From **AppView.cpp**:</span></span>

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

<span data-ttu-id="1b908-154">이 시점부터 AppView 클래스는 Windows 기본 입력 이벤트, CoreWindow 이벤트 및 메시징과의 상호 작용을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-154">From that point on, the AppView class handles interaction with Windows basic input events, CoreWindow events and messaging, and so on.</span></span> <span data-ttu-id="1b908-155">또한 앱에서 사용 하는 HolographicSpace를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-155">It will also create the HolographicSpace used by your app.</span></span>

## <a name="creating-a-win32-project"></a><span data-ttu-id="1b908-156">Win32 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="1b908-156">Creating a Win32 project</span></span>

<span data-ttu-id="1b908-157">Win32 holographic 프로젝트 빌드를 시작 하는 가장 쉬운 방법은 <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank"> *basichologram* win32 샘플</a>을 조정 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-157">The easiest way to get started building a Win32 holographic project is to adapt the <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank">*BasicHologram* Win32 sample</a>.</span></span>

<span data-ttu-id="1b908-158">이 Win32 샘플은 표준 규격 c + + 17 컴파일러를 지 원하는 Windows 런타임 api에 대 한 c + + 17 언어 투영 인 <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/winrt</a>를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-158">This Win32 sample uses <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank">C++/WinRT</a>, a C++17 language projection of the Windows Runtime APIs that supports any standards-compliant C++17 compiler.</span></span>  <span data-ttu-id="1b908-159">이 프로젝트에서는 사용자 로부터 2 미터 배치 된 전 세계 잠긴 큐브를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-159">The project shows how to create a world-locked cube that's placed two meters from the user.</span></span> <span data-ttu-id="1b908-160">사용자는 컨트롤러의 단추를 눌러 사용자의 [응시](gaze.md)에 지정 된 다른 위치에 큐브를 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-160">The user can press a button on the controller to place the cube in a different position that's specified by the user's [gaze](gaze.md).</span></span> <span data-ttu-id="1b908-161">이 프로젝트를 수정 하 여 혼합 현실 앱을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-161">You can modify this project to create any mixed reality app.</span></span>

### <a name="win32-app-entry-point"></a><span data-ttu-id="1b908-162">Win32 앱 진입점</span><span class="sxs-lookup"><span data-stu-id="1b908-162">Win32 app entry point</span></span>

<span data-ttu-id="1b908-163">Holographic Win32 앱은 AppMain .cpp의 **Wwinmain** 함수에서 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-163">Your holographic Win32 app starts in the **wWinMain** function in AppMain.cpp.</span></span> <span data-ttu-id="1b908-164">**Wwinmain** 함수는 응용 프로그램의 HWND를 만들고 메시지 루프를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-164">The **wWinMain** function creates the app's HWND and starts its message loop.</span></span>

<span data-ttu-id="1b908-165">**Appmain .cpp**에서:</span><span class="sxs-lookup"><span data-stu-id="1b908-165">From **AppMain.cpp**:</span></span>

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

<span data-ttu-id="1b908-166">이 시점부터 AppMain 클래스는 기본 창 메시지와의 상호 작용을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-166">From that point on, the AppMain class handles interaction with basic window messages, and so on.</span></span> <span data-ttu-id="1b908-167">또한 앱에서 사용 하는 HolographicSpace를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-167">It will also create the HolographicSpace used by your app.</span></span>

## <a name="render-holographic-content"></a><span data-ttu-id="1b908-168">Holographic 내용 렌더링</span><span class="sxs-lookup"><span data-stu-id="1b908-168">Render holographic content</span></span>

<span data-ttu-id="1b908-169">프로젝트의 **Content** 폴더에는 [holographic 공간](getting-a-holographicspace.md)에 holograms를 렌더링 하기 위한 클래스가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-169">The project's **Content** folder contains classes for rendering holograms in the [holographic space](getting-a-holographicspace.md).</span></span> <span data-ttu-id="1b908-170">템플릿의 기본 홀로그램은 사용자 로부터 두 미터 떨어진 회전 하는 큐브입니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-170">The default hologram in the template is a spinning cube that's placed two meters away from the user.</span></span> <span data-ttu-id="1b908-171">이 큐브 그리기는 다음과 같은 주요 메서드를 포함 하는 **SpinningCubeRenderer**에서 구현 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-171">Drawing this cube is implemented in **SpinningCubeRenderer.cpp**, which has these key methods:</span></span>

|  <span data-ttu-id="1b908-172">메서드</span><span class="sxs-lookup"><span data-stu-id="1b908-172">Method</span></span>  |  <span data-ttu-id="1b908-173">설명</span><span class="sxs-lookup"><span data-stu-id="1b908-173">Explanation</span></span> | 
|----------|----------|
|  `CreateDeviceDependentResources` |  <span data-ttu-id="1b908-174">셰이더를 로드 하 고 큐브 메시를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-174">Loads shaders and creates the cube mesh.</span></span> | 
|  `PositionHologram` |  <span data-ttu-id="1b908-175">제공 된 <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>에 지정 된 위치에 홀로그램을 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-175">Places the hologram at the location specified by the provided <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>.</span></span> | 
|  `Update` |  <span data-ttu-id="1b908-176">큐브를 회전 하 고 모델 매트릭스를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-176">Rotates the cube, and sets the model matrix.</span></span> | 
|  `Render` |  <span data-ttu-id="1b908-177">꼭 짓 점 및 픽셀 셰이더를 사용 하 여 프레임을 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-177">Renders a frame using the vertex and pixel shaders.</span></span> | 

<span data-ttu-id="1b908-178">**셰이더** 하위 폴더에는 네 가지 기본 셰이더 구현이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-178">The **Shaders** subfolder contains four default shader implementations:</span></span>

|  <span data-ttu-id="1b908-179">셰이더가</span><span class="sxs-lookup"><span data-stu-id="1b908-179">Shader</span></span>  |  <span data-ttu-id="1b908-180">설명</span><span class="sxs-lookup"><span data-stu-id="1b908-180">Explanation</span></span> | 
|----------|----------|
|  `GeometryShader.hlsl` |  <span data-ttu-id="1b908-181">기 하 도형을 수정 되지 않은 상태로 유지 하는 통과입니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-181">A pass-through that leaves the geometry unmodified.</span></span> | 
|  `PixelShader.hlsl` |  <span data-ttu-id="1b908-182">색 데이터를 통과 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-182">Passes through the color data.</span></span> <span data-ttu-id="1b908-183">색 데이터는 래스터화 단계에서 보간된 후 픽셀에 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-183">The color data is interpolated and assigned to a pixel at the rasterization step.</span></span> | 
|  `VertexShader.hlsl` |  <span data-ttu-id="1b908-184">GPU에서 꼭 짓 점 처리를 수행 하기 위한 간단한 셰이더입니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-184">Simple shader to do vertex processing on the GPU.</span></span> | 
|  `VPRTVertexShader.hlsl` |  <span data-ttu-id="1b908-185">GPU에서 꼭 짓 점 처리를 수행 하는 간단한 셰이더가 Windows Mixed Reality 스테레오 렌더링에 최적화 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-185">Simple shader to do vertex processing on the GPU, that is optimized for Windows Mixed Reality stereo rendering.</span></span> | 

<span data-ttu-id="1b908-186">`VertexShaderShared.hlsl`와 사이 `VertexShader.hlsl` 에 공유 되는 `VPRTVertexShader.hlsl`공통 코드를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-186">`VertexShaderShared.hlsl` contains common code shared between `VertexShader.hlsl` and `VPRTVertexShader.hlsl`.</span></span>

<span data-ttu-id="1b908-187">셰이더는 프로젝트가 빌드될 때 컴파일되고 **SpinningCubeRenderer:: CreateDeviceDependentResources** 메서드에 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-187">The shaders are compiled when the project is built, and they're loaded in the **SpinningCubeRenderer::CreateDeviceDependentResources** method.</span></span>

## <a name="interact-with-your-holograms"></a><span data-ttu-id="1b908-188">Holograms와 상호 작용</span><span class="sxs-lookup"><span data-stu-id="1b908-188">Interact with your holograms</span></span>

<span data-ttu-id="1b908-189">사용자 입력은 <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a> 인스턴스를 가져오고 <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">sourcepressed</a> 이벤트를 구독 하는 **SpatialInputHandler** 클래스에서 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-189">User input is processed in the **SpatialInputHandler** class, which gets a <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a> instance and subscribes to the <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a> event.</span></span> <span data-ttu-id="1b908-190">그러면 공기 탭 제스처와 기타 공간 입력 이벤트를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-190">This enables detecting the air-tap gesture and other spatial input events.</span></span>

## <a name="update-holographic-content"></a><span data-ttu-id="1b908-191">Holographic 콘텐츠 업데이트</span><span class="sxs-lookup"><span data-stu-id="1b908-191">Update holographic content</span></span>

<span data-ttu-id="1b908-192">혼합 현실 앱은 기본적으로의 `AppMain.cpp` **업데이트** 메서드에서 구현 되는 게임 루프에서 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-192">Your mixed reality app updates in a game loop, which by default is implemented in the **Update** method in `AppMain.cpp`.</span></span> <span data-ttu-id="1b908-193">**Update** 메서드는 회전 큐브와 같은 장면 개체를 업데이트 하 고 최신 뷰 및 프로젝션 매트릭스를 가져오고 스왑 체인을 표시 하는 데 사용 되는 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-193">The **Update** method updates scene objects, like the spinning cube, and returns a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> object that is used to get up-to-date view and projection matrices and to present the swap chain.</span></span>

<span data-ttu-id="1b908-194">의  `AppMain.cpp` Render 메서드는 현재 앱 및 공간 위치 지정 상태에 따라 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> 을 사용 하 여 각 holographic 카메라에 현재 프레임을 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b908-194">The **Render** method in `AppMain.cpp` takes the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> and renders the current frame to each holographic camera, according to the current app and spatial positioning state.</span></span>

## <a name="see-also"></a><span data-ttu-id="1b908-195">참조</span><span class="sxs-lookup"><span data-stu-id="1b908-195">See also</span></span>
* [<span data-ttu-id="1b908-196">HolographicSpace 받기</span><span class="sxs-lookup"><span data-stu-id="1b908-196">Getting a HolographicSpace</span></span>](getting-a-holographicspace.md)
* <span data-ttu-id="1b908-197"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a></span><span class="sxs-lookup"><span data-stu-id="1b908-197"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a></span></span>
* [<span data-ttu-id="1b908-198">DirectX의 렌더링</span><span class="sxs-lookup"><span data-stu-id="1b908-198">Rendering in DirectX</span></span>](rendering-in-directx.md)
* [<span data-ttu-id="1b908-199">Visual Studio를 사용하여 앱 배포 및 디버깅</span><span class="sxs-lookup"><span data-stu-id="1b908-199">Using Visual Studio to deploy and debug</span></span>](using-visual-studio.md)
* [<span data-ttu-id="1b908-200">Using the HoloLens emulator(HoloLens 에뮬레이터 사용)</span><span class="sxs-lookup"><span data-stu-id="1b908-200">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="1b908-201">홀로그램 DirectX 앱에서 XAML 사용</span><span class="sxs-lookup"><span data-stu-id="1b908-201">Using XAML with holographic DirectX apps</span></span>](using-xaml-with-holographic-directx-apps.md)
