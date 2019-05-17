---
title: Holographic DirectX 프로젝트 만들기
description: Windows Mixed Reality 앱 템플릿을 기반으로 새 holographic 앱을 만드는 방법을 설명 합니다.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, holographic 앱, 새 앱을 UWP 앱, 템플릿 앱, 홀로그램, 새 프로젝트, 연습, 다운로드, 샘플 코드
ms.openlocfilehash: a7eac9d8056fe5f7bcc442d6441f71331fa96cf6
ms.sourcegitcommit: 19c9bff21061d485821b61c9f3498daef8fa8235
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65828121"
---
# <a name="creating-a-holographic-directx-project"></a><span data-ttu-id="8b086-104">Holographic DirectX 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="8b086-104">Creating a holographic DirectX project</span></span>

<span data-ttu-id="8b086-105">HoloLens에 대해 만들 holographic 앱을 <a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">유니버설 Windows 플랫폼 (UWP) 앱</a>합니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-105">A holographic app you create for a HoloLens will be a <a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">Universal Windows Platform (UWP) app</a>.</span></span>  <span data-ttu-id="8b086-106">데스크톱 Windows Mixed Reality 헤드셋을 대상으로 하는 경우에 UWP 앱 또는 Win32 앱을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-106">If targeting desktop Windows Mixed Reality headsets, you can create a UWP app or a Win32 app.</span></span>

<span data-ttu-id="8b086-107">DirectX 11 holographic UWP 앱 템플릿을 DirectX 11 UWP 앱 템플릿을;를 매우 비슷합니다. 프로그램 루프 (또는 "게임 루프")를 포함 한 **DeviceResources** Direct3D 장치 및 컨텍스트를 관리 하는 클래스와 간소화 된 콘텐츠 렌더러 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-107">The DirectX 11 holographic UWP app template is much like the DirectX 11 UWP app template; it includes a program loop (or "game loop"), a **DeviceResources** class to manage the Direct3D device and context, and a simplified content renderer class.</span></span> <span data-ttu-id="8b086-108">또한에 <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>마찬가지로 다른 UWP 앱.</span><span class="sxs-lookup"><span data-stu-id="8b086-108">It also has an <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>, just like any other UWP app.</span></span>

<span data-ttu-id="8b086-109">그러나 혼합된 현실 앱에는 일반적인 Direct3D 11 UWP 앱에서 존재 하지 않는 몇 가지 추가 기능에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-109">The mixed reality app, however, has some additional capabilities that aren't present in a typical Direct3D 11 UWP app.</span></span> <span data-ttu-id="8b086-110">Windows Holographic 앱 템플릿에 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-110">The Windows Holographic app template is able to:</span></span>
* <span data-ttu-id="8b086-111">Holographic 카메라를 사용 하 여 연결 된 Direct3D 장치 리소스를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-111">Handle Direct3D device resources associated with holographic cameras.</span></span>
* <span data-ttu-id="8b086-112">시스템에서 카메라 백 버퍼를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-112">Retrieve camera back buffers from the system.</span></span>
* <span data-ttu-id="8b086-113">처리할 [gaze](gaze.md) 입력 하 고 간단한 인식 [제스처](gestures.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-113">Handle [gaze](gaze.md) input, and recognize a simple [gesture](gestures.md).</span></span>
* <span data-ttu-id="8b086-114">스테레오 렌더링 전체 화면 모드로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-114">Go into full-screen stereo rendering mode.</span></span>

## <a name="how-do-i-get-started"></a><span data-ttu-id="8b086-115">어떻게 시작 합니까?</span><span class="sxs-lookup"><span data-stu-id="8b086-115">How do I get started?</span></span>

<span data-ttu-id="8b086-116">첫 번째 [도구를 설치](install-the-tools.md), 다음 Visual Studio 2017 다운로드에 대 한 지침 및 Microsoft HoloLens 에뮬레이터.</span><span class="sxs-lookup"><span data-stu-id="8b086-116">First [install the tools](install-the-tools.md), following the instructions on downloading Visual Studio 2017 and the Microsoft HoloLens emulator.</span></span> <span data-ttu-id="8b086-117">Holographic 앱 템플릿은 Microsoft HoloLens 에뮬레이터와 동일한 설치 관리자에 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-117">The holographic app templates are included in the same installer as the Microsoft HoloLens emulator.</span></span> <span data-ttu-id="8b086-118">또한 서식 파일을 설치 하는 옵션을 설치 하기 전에 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-118">Also ensure that the option to install the templates is selected before installing.</span></span>

<span data-ttu-id="8b086-119">이제 DirectX 11 Windows Mixed Reality 앱을 만들 준비가 되었습니다!</span><span class="sxs-lookup"><span data-stu-id="8b086-119">Now you're ready to create your DirectX 11 Windows Mixed Reality app!</span></span> <span data-ttu-id="8b086-120">샘플 콘텐츠를 제거 하 여 주석 처리를 확인 합니다 **DRAW_SAMPLE_CONTENT** 전처리기 지시문 *pch.h*.</span><span class="sxs-lookup"><span data-stu-id="8b086-120">Note, to remove the sample content, comment out the **DRAW_SAMPLE_CONTENT** preprocessor directive in *pch.h*.</span></span>

## <a name="creating-a-uwp-project"></a><span data-ttu-id="8b086-121">UWP 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="8b086-121">Creating a UWP project</span></span>

<span data-ttu-id="8b086-122">한 번 합니다 [도구가 설치 되어](install-the-tools.md) holographic DirectX UWP 프로젝트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-122">Once the [tools are installed](install-the-tools.md) you can then create a holographic DirectX UWP project.</span></span>

<span data-ttu-id="8b086-123">새 프로젝트를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="8b086-123">To create a new project:</span></span>
1. <span data-ttu-id="8b086-124">시작 **Visual Studio**합니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-124">Start **Visual Studio**.</span></span>
2. <span data-ttu-id="8b086-125">**파일** 메뉴에서 **새로 만들기** 선택한 **프로젝트** 상황에 맞는 메뉴에서.</span><span class="sxs-lookup"><span data-stu-id="8b086-125">From the **File** menu, point to **New** and select **Project** from the context menu.</span></span> <span data-ttu-id="8b086-126">합니다 **새 프로젝트** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-126">The **New Project** dialog opens.</span></span>
3. <span data-ttu-id="8b086-127">확장 **설치 됨** 왼쪽 확장를 **시각적 C++**  언어 노드.</span><span class="sxs-lookup"><span data-stu-id="8b086-127">Expand **Installed** on the left and expand the **Visual C++** language node.</span></span>
4. <span data-ttu-id="8b086-128">로 이동 합니다 **Windows 유니버설 > Holographic** 노드와 선택 **Holographic DirectX 11 앱 (유니버설 Windows) (C++/WinRT)** 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-128">Navigate to the **Windows Universal > Holographic** node and select **Holographic DirectX 11 App (Universal Windows) (C++/WinRT)**.</span></span>
   <span data-ttu-id="8b086-129">![Holographic DirectX 11의 스크린샷 C++Visual Studio에서 WinRT UWP 앱 프로젝트 템플릿](images/holographic-directx-app-cpp-new-project.png)</span><span class="sxs-lookup"><span data-stu-id="8b086-129">![Screenshot of the Holographic DirectX 11 C++/WinRT UWP app project template in Visual Studio](images/holographic-directx-app-cpp-new-project.png)</span></span><br>
   <span data-ttu-id="8b086-130">*DirectX 11 holographic C++Visual Studio에서 WinRT UWP 앱 프로젝트 템플릿*</span><span class="sxs-lookup"><span data-stu-id="8b086-130">*Holographic DirectX 11 C++/WinRT UWP app project template in Visual Studio*</span></span>
   >[!IMPORTANT]
   ><span data-ttu-id="8b086-131">프로젝트 템플릿의 이름을 포함 해야 "(C++/WinRT)".</span><span class="sxs-lookup"><span data-stu-id="8b086-131">Be sure that the project template's name includes "(C++/WinRT)".</span></span>  <span data-ttu-id="8b086-132">그렇지 않은 경우 설치 된 holographic 프로젝트 템플릿의 이전 버전이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-132">If not, you have an older version of the holographic project templates installed.</span></span>  <span data-ttu-id="8b086-133">최신 프로젝트 템플릿을 가져오려는 [최신 HoloLens 에뮬레이터를 설치할](using-the-hololens-emulator.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-133">To get the latest project templates, [install the latest HoloLens Emulator](using-the-hololens-emulator.md).</span></span>
5. <span data-ttu-id="8b086-134">입력 합니다 **이름** 및 **위치** 텍스트 상자 및 클릭 하거나 탭 **확인**합니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-134">Fill in the **Name** and **Location** text boxes, and click or tap **OK**.</span></span> <span data-ttu-id="8b086-135">Holographic 앱 프로젝트가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-135">The holographic app project is created.</span></span>
6. <span data-ttu-id="8b086-136">개발을 위한 HoloLens 2만 대상 지정 되어 있는지 확인 합니다 **대상 버전** 및 **최소 버전** 으로 설정 됩니다 **Windows 10 버전 1903**합니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-136">For development targeting only HoloLens 2, ensure that the **Target version** and **Minimum version** are set to **Windows 10, version 1903**.</span></span>  <span data-ttu-id="8b086-137">HoloLens도 대상으로 하는 경우 (첫 번째 gen) 하거나 설정할 수 있습니다 데스크톱 Windows Mixed Reality 헤드셋 **최소 버전** 하 **Windows 10 버전 1809** 대신 일부 해야 하지만 <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank"> 버전 적응 검사</a> HoloLens 2의 새로운 기능을 사용 하는 경우 코드에서.</span><span class="sxs-lookup"><span data-stu-id="8b086-137">If you are also targeting HoloLens (1st gen) or desktop Windows Mixed Reality headsets, you can set **Minimum version** to **Windows 10, version 1809** instead, although this will require some <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">version adaptive checks</a> in your code when using new features of HoloLens 2.</span></span>
   <span data-ttu-id="8b086-138">![Windows 10 버전 1903 대상 및 최소 버전으로 설정 하는 스크린샷](images/new-uwp-project.png)</span><span class="sxs-lookup"><span data-stu-id="8b086-138">![Screenshot of setting Windows 10, version 1903 as the target and minimum versions](images/new-uwp-project.png)</span></span><br>
   <span data-ttu-id="8b086-139">*설정 **Windows 10 버전 1903** 대상 및 최소 버전*</span><span class="sxs-lookup"><span data-stu-id="8b086-139">*Setting **Windows 10, version 1903** as the target and minimum versions*</span></span>
   >[!IMPORTANT]
   ><span data-ttu-id="8b086-140">표시 되지 않으면 **Windows 10 버전 1903** 옵션이 없는 최신 Windows 10 SDK를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-140">If you do not see **Windows 10, version 1903** as an option, you do not have the latest Windows 10 SDK installed.</span></span>  <span data-ttu-id="8b086-141">표시 하려면이 옵션을 가져오려는 <a href="https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk" target="_blank">10.0.18362.0 버전을 설치 또는 Windows 10 SDK의 뒷부분에 나오는</a>합니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-141">To get this option to appear, <a href="https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk" target="_blank">install version 10.0.18362.0 or later of the Windows 10 SDK</a>.</span></span>

<span data-ttu-id="8b086-142">템플릿을 사용 하 여 프로젝트 생성 <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>, Windows 런타임 Api를 지 원하는 모든 표준 호환 C + + 17 컴파일러의 C + + 17 개의 언어 프로젝션 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-142">The template generates a project using <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank">C++/WinRT</a>, a C++17 language projection of the Windows Runtime APIs that supports any standards-compliant C++17 compiler.</span></span>  <span data-ttu-id="8b086-143">프로젝트에는 사용자 로부터 두 미터를 배치에 전 세계 잠긴 큐브를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-143">The project shows how to create a world-locked cube that's placed two meters from the user.</span></span> <span data-ttu-id="8b086-144">사용자 수 [어 탭](gestures.md#air-tap) 큐브에 사용자 지정 된 다른 위치에 배치 하려면 컨트롤러에서 단추를 누르거나 [gaze](gaze.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-144">The user can [air-tap](gestures.md#air-tap) or press a button on the controller to place the cube in a different position that's specified by the user's [gaze](gaze.md).</span></span> <span data-ttu-id="8b086-145">혼합된 현실 앱을 만들려면이 프로젝트를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-145">You can modify this project to create any mixed reality app.</span></span>

<span data-ttu-id="8b086-146">사용 하 여 새 프로젝트를 만들 수는 또는 **시각적 C#**  holographic 프로젝트 템플릿을 SharpDX을 기반으로 하는 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-146">Alternatively, you can create a new project using the **Visual C#** holographic project template, which is based on SharpDX.</span></span>  <span data-ttu-id="8b086-147">경우에 holographic C# Windows Holographic 앱 템플릿에서 프로젝트를 시작 되지 않았습니다, Windows Mixed Reality에서 ms.fxcompile.targets 파일을 복사 해야 합니다 C# HLSL 컴파일하기 위해 파일에.csproj에 템플릿 프로젝트 및 가져오기 프로젝트에 추가 하는 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-147">If your holographic C# project did not start from the Windows Holographic app template, you will need to copy the ms.fxcompile.targets file from a Windows Mixed Reality C# template project and import it in your .csproj file in order to compile HLSL files that you add to your project.</span></span>

<span data-ttu-id="8b086-148">검토 [배포 및 디버깅 Visual Studio를 사용 하 여](using-visual-studio.md) 여 HoloLens, 연결 하는 몰입 감이 뛰어난 장치를 사용 하 여 PC 또는 에뮬레이터를 샘플을 배포 하는 방법에 대 한 정보에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-148">Review [Using Visual Studio to deploy and debug](using-visual-studio.md) for information on how to build and deploy the sample to your HoloLens, PC with immersive device attached, or an emulator.</span></span>

<span data-ttu-id="8b086-149">사용 중인 아래 지침의 나머지 부분에서는 C++ 앱을 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-149">The rest of the instructions below will assume that you are using C++ to build your app.</span></span>

### <a name="uwp-app-entry-point"></a><span data-ttu-id="8b086-150">UWP 앱 진입점</span><span class="sxs-lookup"><span data-stu-id="8b086-150">UWP app entry point</span></span>

<span data-ttu-id="8b086-151">Holographic UWP 앱에서 시작 합니다 **wWinMain** AppView.cpp의 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-151">Your holographic UWP app starts in the **wWinMain** function in AppView.cpp.</span></span> <span data-ttu-id="8b086-152">**wWinMain** 함수 앱을 만듭니다 <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> 하 고 시작 합니다 <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> 된 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-152">The **wWinMain** function creates the app's <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> and starts the <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> with it.</span></span>

<span data-ttu-id="8b086-153">**AppView.cpp**:</span><span class="sxs-lookup"><span data-stu-id="8b086-153">From **AppView.cpp**:</span></span>

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

<span data-ttu-id="8b086-154">해당 지점에서 AppView 클래스는 Windows 기본 입력된 이벤트, CoreWindow 이벤트 및 메시징 및 등을 사용 하 여 상호 작용을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-154">From that point on, the AppView class handles interaction with Windows basic input events, CoreWindow events and messaging, and so on.</span></span> <span data-ttu-id="8b086-155">또한 앱에서 사용 하는 HolographicSpace 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-155">It will also create the HolographicSpace used by your app.</span></span>

## <a name="creating-a-win32-project"></a><span data-ttu-id="8b086-156">Win32 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="8b086-156">Creating a Win32 project</span></span>

<span data-ttu-id="8b086-157">Win32 맞게 holographic 프로젝트는 빌드를 시작 하는 가장 쉬운 방법은 합니다 <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank"> *BasicHologram* Win32 샘플</a>합니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-157">The easiest way to get started building a Win32 holographic project is to adapt the <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank">*BasicHologram* Win32 sample</a>.</span></span>

<span data-ttu-id="8b086-158">이 Win32 샘플에서는 <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>, Windows 런타임 Api를 지 원하는 모든 표준 호환 C + + 17 컴파일러의 C + + 17 개의 언어 프로젝션 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-158">This Win32 sample uses <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank">C++/WinRT</a>, a C++17 language projection of the Windows Runtime APIs that supports any standards-compliant C++17 compiler.</span></span>  <span data-ttu-id="8b086-159">프로젝트에는 사용자 로부터 두 미터를 배치에 전 세계 잠긴 큐브를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-159">The project shows how to create a world-locked cube that's placed two meters from the user.</span></span> <span data-ttu-id="8b086-160">사용자 큐브에 사용자 지정 된 다른 위치에 배치 하려면 컨트롤러에서 단추를 눌러도 [gaze](gaze.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-160">The user can press a button on the controller to place the cube in a different position that's specified by the user's [gaze](gaze.md).</span></span> <span data-ttu-id="8b086-161">혼합된 현실 앱을 만들려면이 프로젝트를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-161">You can modify this project to create any mixed reality app.</span></span>

### <a name="win32-app-entry-point"></a><span data-ttu-id="8b086-162">Win32 응용 프로그램 진입점</span><span class="sxs-lookup"><span data-stu-id="8b086-162">Win32 app entry point</span></span>

<span data-ttu-id="8b086-163">Holographic Win32 앱이 시작 되는 **wWinMain** AppMain.cpp의 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-163">Your holographic Win32 app starts in the **wWinMain** function in AppMain.cpp.</span></span> <span data-ttu-id="8b086-164">합니다 **wWinMain** 함수 앱의 HWND를 만들고 해당 메시지 루프를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-164">The **wWinMain** function creates the app's HWND and starts its message loop.</span></span>

<span data-ttu-id="8b086-165">**AppMain.cpp**:</span><span class="sxs-lookup"><span data-stu-id="8b086-165">From **AppMain.cpp**:</span></span>

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

<span data-ttu-id="8b086-166">해당 지점에서 AppMain 클래스 등 기본적인 창 메시지와 상호 작용을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-166">From that point on, the AppMain class handles interaction with basic window messages, and so on.</span></span> <span data-ttu-id="8b086-167">또한 앱에서 사용 하는 HolographicSpace 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-167">It will also create the HolographicSpace used by your app.</span></span>

## <a name="render-holographic-content"></a><span data-ttu-id="8b086-168">Holographic 콘텐츠를 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-168">Render holographic content</span></span>

<span data-ttu-id="8b086-169">프로젝트의 **콘텐츠** 폴더에서 렌더링 홀로그램 클래스를 포함 합니다 [holographic 공간](getting-a-holographicspace.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-169">The project's **Content** folder contains classes for rendering holograms in the [holographic space](getting-a-holographicspace.md).</span></span> <span data-ttu-id="8b086-170">템플릿에서 기본 홀로그램 사용자 반대쪽으로 두 가지 단위가 배치 되는 회전 큐브는입니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-170">The default hologram in the template is a spinning cube that's placed two meters away from the user.</span></span> <span data-ttu-id="8b086-171">구현 되는이 큐브에 그리기 **SpinningCubeRenderer.cpp**, 이러한 주요 메서드 있는:</span><span class="sxs-lookup"><span data-stu-id="8b086-171">Drawing this cube is implemented in **SpinningCubeRenderer.cpp**, which has these key methods:</span></span>

|  <span data-ttu-id="8b086-172">메서드</span><span class="sxs-lookup"><span data-stu-id="8b086-172">Method</span></span>  |  <span data-ttu-id="8b086-173">설명</span><span class="sxs-lookup"><span data-stu-id="8b086-173">Explanation</span></span> | 
|----------|----------|
|  `CreateDeviceDependentResources` |  <span data-ttu-id="8b086-174">셰이더를 로드 하 고 큐브 메시를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-174">Loads shaders and creates the cube mesh.</span></span> | 
|  `PositionHologram` |  <span data-ttu-id="8b086-175">인수에 의해 지정 된 위치를 홀로그램 배치 <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>합니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-175">Places the hologram at the location specified by the provided <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>.</span></span> | 
|  `Update` |  <span data-ttu-id="8b086-176">큐브를 회전 하 고 된 모델 매트릭스를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-176">Rotates the cube, and sets the model matrix.</span></span> | 
|  `Render` |  <span data-ttu-id="8b086-177">꼭 짓 점 및 픽셀 셰이더를 사용 하 여 프레임을 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-177">Renders a frame using the vertex and pixel shaders.</span></span> | 

<span data-ttu-id="8b086-178">합니다 **셰이더** 하위 폴더에 4 개의 기본 셰이더 구현이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-178">The **Shaders** subfolder contains four default shader implementations:</span></span>

|  <span data-ttu-id="8b086-179">셰이더</span><span class="sxs-lookup"><span data-stu-id="8b086-179">Shader</span></span>  |  <span data-ttu-id="8b086-180">설명</span><span class="sxs-lookup"><span data-stu-id="8b086-180">Explanation</span></span> | 
|----------|----------|
|  `GeometryShader.hlsl` |  <span data-ttu-id="8b086-181">기 하 도형 수정 되지 않은 상태로 유지 하는 통과 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-181">A pass-through that leaves the geometry unmodified.</span></span> | 
|  `PixelShader.hlsl` |  <span data-ttu-id="8b086-182">색 데이터를 통해 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-182">Passes through the color data.</span></span> <span data-ttu-id="8b086-183">색 데이터 보간 되 고 래스터화 단계에서 픽셀에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-183">The color data is interpolated and assigned to a pixel at the rasterization step.</span></span> | 
|  `VertexShader.hlsl` |  <span data-ttu-id="8b086-184">GPU에서 꼭 짓 점 처리를 수행 하기 위한 간단한 셰이더입니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-184">Simple shader to do vertex processing on the GPU.</span></span> | 
|  `VPRTVertexShader.hlsl` |  <span data-ttu-id="8b086-185">Windows Mixed Reality 스테레오 렌더링을 위해 최적화 된 GPU에서 꼭 짓 점 처리를 수행 하기 위한 간단한 셰이더입니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-185">Simple shader to do vertex processing on the GPU, that is optimized for Windows Mixed Reality stereo rendering.</span></span> | 

<span data-ttu-id="8b086-186">`VertexShaderShared.hlsl` 간에 공유 되는 일반적인 코드를 포함 `VertexShader.hlsl` 고 `VPRTVertexShader.hlsl`입니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-186">`VertexShaderShared.hlsl` contains common code shared between `VertexShader.hlsl` and `VPRTVertexShader.hlsl`.</span></span>

<span data-ttu-id="8b086-187">프로젝트를 빌드할 때 로드 하는 셰이더를 컴파일되는 **SpinningCubeRenderer::CreateDeviceDependentResources** 메서드.</span><span class="sxs-lookup"><span data-stu-id="8b086-187">The shaders are compiled when the project is built, and they're loaded in the **SpinningCubeRenderer::CreateDeviceDependentResources** method.</span></span>

## <a name="interact-with-your-holograms"></a><span data-ttu-id="8b086-188">사용자 제공 상호 작용</span><span class="sxs-lookup"><span data-stu-id="8b086-188">Interact with your holograms</span></span>

<span data-ttu-id="8b086-189">사용자 입력에서 처리 되는 **SpatialInputHandler** 클래스는 가져옵니다를 <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a> 인스턴스를 구독 하는 <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a> 이벤트.</span><span class="sxs-lookup"><span data-stu-id="8b086-189">User input is processed in the **SpatialInputHandler** class, which gets a <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a> instance and subscribes to the <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a> event.</span></span> <span data-ttu-id="8b086-190">그러면 어 탭 제스처 및 기타 공간 입력된 이벤트를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-190">This enables detecting the air-tap gesture and other spatial input events.</span></span>

## <a name="update-holographic-content"></a><span data-ttu-id="8b086-191">Holographic 콘텐츠 업데이트</span><span class="sxs-lookup"><span data-stu-id="8b086-191">Update holographic content</span></span>

<span data-ttu-id="8b086-192">기본적으로에서 구현 되는 게임 루프에서 혼합된 현실 앱 업데이트를 **업데이트** 메서드에서 `AppMain.cpp`합니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-192">Your mixed reality app updates in a game loop, which by default is implemented in the **Update** method in `AppMain.cpp`.</span></span> <span data-ttu-id="8b086-193">합니다 **업데이트** 회전 큐브를 같은 장면 개체를 업데이트 하 고 반환 하는 메서드를 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> 최신 뷰 및 투영 행렬을 가져오고 스왑 체인을 제공 하는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-193">The **Update** method updates scene objects, like the spinning cube, and returns a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> object that is used to get up-to-date view and projection matrices and to present the swap chain.</span></span>

<span data-ttu-id="8b086-194">**렌더링** 에서 메서드 `AppMain.cpp` 는 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> 하 고 각 holographic 카메라 위치 지정 공간 상태 확인 하 고 현재 앱에 따라 현재 프레임을 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b086-194">The **Render** method in `AppMain.cpp` takes the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> and renders the current frame to each holographic camera, according to the current app and spatial positioning state.</span></span>

## <a name="see-also"></a><span data-ttu-id="8b086-195">참조</span><span class="sxs-lookup"><span data-stu-id="8b086-195">See also</span></span>
* [<span data-ttu-id="8b086-196">HolographicSpace 받기</span><span class="sxs-lookup"><span data-stu-id="8b086-196">Getting a HolographicSpace</span></span>](getting-a-holographicspace.md)
* <span data-ttu-id="8b086-197"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a></span><span class="sxs-lookup"><span data-stu-id="8b086-197"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a></span></span>
* [<span data-ttu-id="8b086-198">DirectX의 렌더링</span><span class="sxs-lookup"><span data-stu-id="8b086-198">Rendering in DirectX</span></span>](rendering-in-directx.md)
* [<span data-ttu-id="8b086-199">Visual Studio를 사용하여 앱 배포 및 디버깅</span><span class="sxs-lookup"><span data-stu-id="8b086-199">Using Visual Studio to deploy and debug</span></span>](using-visual-studio.md)
* [<span data-ttu-id="8b086-200">Using the HoloLens emulator(HoloLens 에뮬레이터 사용)</span><span class="sxs-lookup"><span data-stu-id="8b086-200">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="8b086-201">홀로그램 DirectX 앱에서 XAML 사용</span><span class="sxs-lookup"><span data-stu-id="8b086-201">Using XAML with holographic DirectX apps</span></span>](using-xaml-with-holographic-directx-apps.md)
