---
title: Unreal의 WinRT
description: Unreal 엔진용 공간 오디오 플러그 인에 대한 개요입니다.
author: fieldsJacksonG
ms.author: jacksonf
ms.date: 07/08/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 스트리밍, 원격, 혼합 현실, 개발, 시작, 기능, 새 프로젝트, 에뮬레이터, 설명서, 가이드, 특징, 홀로그램, 게임 개발
ms.openlocfilehash: 7a64002a5fa48bb589ab113f0a8dc1bfcb92d535
ms.sourcegitcommit: 2813f5b3027d47f7c6e9772338935eeccfa2aaec
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/16/2020
ms.locfileid: "86408221"
---
# <a name="winrt-in-unreal"></a><span data-ttu-id="4e47e-104">Unreal의 WinRT</span><span class="sxs-lookup"><span data-stu-id="4e47e-104">WinRT in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="4e47e-105">개요</span><span class="sxs-lookup"><span data-stu-id="4e47e-105">Overview</span></span>

<span data-ttu-id="4e47e-106">HoloLens 개발 과정에서 WinRT를 사용 하 여 기능을 작성 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-106">Over the course of your HoloLens development you may need to write a feature using WinRT.</span></span> <span data-ttu-id="4e47e-107">예를 들어 HoloLens 응용 프로그램에서 파일 대화 상자를 열려면 winrt/FileSavePicker 헤더 파일에 해당 파일이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-107">For example, opening a file dialogue in a HoloLens application would need the FileSavePicker in winrt/Windows.Storage.Pickers.h header file.</span></span>  <span data-ttu-id="4e47e-108">Unreal은 기본적으로 WinRT 코드를 컴파일하지 않으므로 별도의 이진 파일을 작성 하 고, Unreal의 빌드 시스템에서 사용할 수 있는 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-108">Since Unreal doesn't natively compile WinRT code, it's your job to build a separate binary and that can be consumed by Unreal’s build system.</span></span> <span data-ttu-id="4e47e-109">이 자습서에서는 이러한 시나리오를 안내 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-109">This tutorial will walk you through just such a scenario.</span></span>

## <a name="objectives"></a><span data-ttu-id="4e47e-110">목표</span><span class="sxs-lookup"><span data-stu-id="4e47e-110">Objectives</span></span>
- <span data-ttu-id="4e47e-111">FileSaveDialogue를 여는 유니버설 Windows DLL 만들기</span><span class="sxs-lookup"><span data-stu-id="4e47e-111">Create a Universal Windows DLL that opens a FileSaveDialogue</span></span>
- <span data-ttu-id="4e47e-112">해당 DLL을 Unreal 게임 프로젝트에 연결</span><span class="sxs-lookup"><span data-stu-id="4e47e-112">Link that DLL to an Unreal game project</span></span>
- <span data-ttu-id="4e47e-113">새 DLL을 사용 하 여 실제 청사진에서 HoloLens에 파일 저장</span><span class="sxs-lookup"><span data-stu-id="4e47e-113">Save a file on the HoloLens from an Unreal blueprint using the new DLL</span></span>

## <a name="getting-started"></a><span data-ttu-id="4e47e-114">시작</span><span class="sxs-lookup"><span data-stu-id="4e47e-114">Getting started</span></span>
1. <span data-ttu-id="4e47e-115">[필요한 모든 도구가](unreal-uxt-ch1.md) 설치 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-115">Check that you have all [required tools](unreal-uxt-ch1.md) installed</span></span>
2. <span data-ttu-id="4e47e-116">[새 Unreal 프로젝트를 만들고](unreal-uxt-ch2.md#creating-a-new-unreal-project) 이름을 **Consumewinrt** 로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-116">[Create a new Unreal project](unreal-uxt-ch2.md#creating-a-new-unreal-project) and name it **Consumewinrt**</span></span>
3. <span data-ttu-id="4e47e-117">HoloLens 개발에 [필요한 플러그 인](unreal-uxt-ch2.md#enabling-required-plugins) 사용</span><span class="sxs-lookup"><span data-stu-id="4e47e-117">Enable the [required plugins](unreal-uxt-ch2.md#enabling-required-plugins) for HoloLens development</span></span>
4. <span data-ttu-id="4e47e-118">장치 또는 에뮬레이터에 [배포 설정](unreal-uxt-ch6.md)</span><span class="sxs-lookup"><span data-stu-id="4e47e-118">[Setup for deployment](unreal-uxt-ch6.md) to a device or emulator</span></span>

## <a name="creating-a-winrt-dll"></a><span data-ttu-id="4e47e-119">WinRT DLL 만들기</span><span class="sxs-lookup"><span data-stu-id="4e47e-119">Creating a WinRT DLL</span></span> 
1. <span data-ttu-id="4e47e-120">새 Visual Studio 프로젝트를 열고, Unreal 게임의 **uproject** 파일과 동일한 디렉터리에 **DLL (유니버설 Windows)** 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-120">Open a new Visual Studio project and create a **DLL (Universal Windows)** project in the same directory to the Unreal game’s **uproject** file.</span></span> 

![DLL 만들기](images/unreal-winrt-img-01.png)

2. <span data-ttu-id="4e47e-122">프로젝트 이름을 **HoloLensWinrtDLL** 로 설정 하 고 위치를 **thirdparty (** 하위 디렉터리로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-122">Name the project **HoloLensWinrtDLL** and set the location as a **ThirdParty** subdirectory to the Unreal game’s uproject file.</span></span> 
    * <span data-ttu-id="4e47e-123">나중에 경로를 찾기 쉽도록 **동일한 디렉터리에 솔루션 및 프로젝트 두기** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-123">Select **Place solution and project in the same directory** to simplify looking for paths later.</span></span> 

![DLL 구성](images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> <span data-ttu-id="4e47e-125">새 프로젝트를 컴파일한 후에는 각각 **HoloLensWinrtDLL** 및 **HoloLensWinrtDLL** 라는 빈 cpp 및 헤더 파일에 특별히 주의를 기울여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-125">After the new project compiles, you want to pay special attention to the blank cpp and header files, named **HoloLensWinrtDLL.cpp** and **HoloLensWinrtDLL.h** respectively.</span></span> <span data-ttu-id="4e47e-126">헤더는 Unreal에서 DLL을 사용 하는 포함 파일이 고, cpp는 내보내기 함수의 본문을 포함 하 고 그렇지 않으면 컴파일할 수 없는 모든 WinRT 코드를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-126">The header is the include file that uses the DLL in Unreal, while the cpp holds the body of any functions you export and includes any WinRT code that Unreal wouldn't otherwise be able to compile.</span></span> 

3. <span data-ttu-id="4e47e-127">코드를 추가 하기 전에 필요한 WinRT 코드를 컴파일할 수 있도록 프로젝트 속성을 업데이트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-127">Before you add any code, you need to update the project properties to ensure the WinRT code you need can compile:</span></span> 
    * <span data-ttu-id="4e47e-128">HoloLensWinrtDLL 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **속성** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-128">Right click on the HoloLensWinrtDLL project and select **properties**</span></span>  
    * <span data-ttu-id="4e47e-129">모든 구성 및 **플랫폼** 드롭다운으로 **구성** **드롭다운을** **모든 플랫폼** 으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-129">Change the **Configuration** dropdown to **All Configurations** and the **Platform** dropdown to **All Platforms**</span></span>  
    * <span data-ttu-id="4e47e-130">**구성 속성에서 C/c + +> 모든 옵션>** 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-130">Under **Configuration Properties> C/C++> All Options**:</span></span>
        * <span data-ttu-id="4e47e-131">비동기 작업을 기다릴 수 있도록 **추가 옵션** 에 **wait** 추가</span><span class="sxs-lookup"><span data-stu-id="4e47e-131">Add **await** to **Additional Options** to ensure we can wait on async tasks</span></span>  
        * <span data-ttu-id="4e47e-132">**C + + 언어 표준** 을 **ISO c + + 17 Standard (/std: c + + 17)** 로 변경 하 여 WinRT 코드를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-132">Change **C++ Language Standard** to **ISO C++17 Standard (/std:c++17)** to include any WinRT code</span></span>

![DLL 구성](images/unreal-winrt-img-03.png)

<span data-ttu-id="4e47e-134">프로젝트에서 파일 대화 상자를 열고 HoloLens 디스크에 파일을 저장 하는 WinRT 코드를 사용 하 여 DLL의 소스를 업데이트할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-134">Your project is ready to update the DLL’s source with WinRT code that opens a file dialogue and saves a file to the HoloLens disk.</span></span>  

## <a name="adding-the-dll-code"></a><span data-ttu-id="4e47e-135">DLL 코드 추가</span><span class="sxs-lookup"><span data-stu-id="4e47e-135">Adding the DLL code</span></span>
1. <span data-ttu-id="4e47e-136">HoloLensWinrtDLL를 열고, Unreal에 사용할 dll 내보내기 함수를 추가 **합니다** .</span><span class="sxs-lookup"><span data-stu-id="4e47e-136">Open **HoloLensWinrtDLL.h** and add a dll exported function for Unreal to consume:</span></span> 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. <span data-ttu-id="4e47e-137">HoloLensWinrtDLL를 열고 클래스에서 사용할 모든 헤더를 추가 **합니다** .</span><span class="sxs-lookup"><span data-stu-id="4e47e-137">Open **HoloLensWinrtDLL.cpp** and add all headers the class will use:</span></span>  

```cpp
#include "pch.h"
#include "HoloLensWinrtDLL.h"

#include <winrt/Windows.Storage.h>
#include <winrt/Windows.Storage.Streams.h>
#include <winrt/Windows.Storage.Pickers.h>
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Foundation.Collections.h>

#include <string>
#include <vector>
#include <thread>
```

> [!NOTE]
> <span data-ttu-id="4e47e-138">모든 WinRT 코드는 **HoloLensWinrtDLL** 에 저장 되므로 실제는 헤더를 참조할 때 winrt 코드를 포함 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-138">All WinRT code is stored in **HoloLensWinrtDLL.cpp** so Unreal doesn't try to include any WinRT code when referencing the header.</span></span> 

3. <span data-ttu-id="4e47e-139">여전히 HoloLensWinrtDLL에서 OpenFileDialogue () 및 지원 되는 모든 코드에 대 한 함수 본문을 추가 **합니다**.</span><span class="sxs-lookup"><span data-stu-id="4e47e-139">Still in **HoloLensWinrtDLL.cpp**, add a function body for OpenFileDialogue() and all supported code:</span></span> 

```cpp
// sgm is declared outside of OpenFileDialogue so it doesn't
// get destroyed when OpenFileDialogue goes out of scope.
SaveGameManager sgm;

void HoloLensWinrtDLL::OpenFileDialogue()
{
    sgm.SaveGame();
}
```

4. <span data-ttu-id="4e47e-140">**HoloLensWinrtDLL** 에 SaveGameManager 클래스를 추가 하 여 파일 대화 상자를 처리 하 고 파일을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-140">Add a SaveGameManager class to **HoloLensWinrtDLL.cpp** to handle the file dialogue and saving the file:</span></span> 

```cpp
class SaveGameManager
{
public:
    SaveGameManager()
    {
    }

    ~SaveGameManager()
    {
        // Wait for currently running thread to complete before terminating.
        if(m_thread.joinable())
        {
            m_thread.join();
        }
    }

    void SaveGame()
    {
        OpenFileDialogueAction();
    }

private:
    winrt::Windows::Storage::StorageFile m_file = winrt::Windows::Storage::StorageFile(nullprt);
    std::thread m_thread;

    winrt::Windows::Foundation::IAsyncAction OpenFileDialogueAction()
    {
        std::vector<winrt::hstring> extensions;
        extensions.push_back(L".txt");

        auto picker = winrt::Windows::Storage::Pickers::FileSavePicker();

        // FileSavePicker needs a file type to open without errors.
        picker.FileTypeChoices().Insert(L"Plain Text",
                                        winrt::single_threaded_vector<winrt::hstring>(
                                        std::move(extensions)));

        // Opening the FilePicker must be done on the Game UI thread.
        // Any other IAsyncOperations should be done on a background thread.
        m_file = co_await picker.PickSaveFileAsync();

        if(m_file)
        {
            // Unreal's game thread is an STA, async tasks need to run on
            // a background MTA thread, or waiting on them will deadlock.    
            std::thread thread([this]() { RunThread(); });
            m_thread = std::move(thread);
        }
    }

    void RunThread()
    {
        // Ensure this thread is an MTA
        winrt::init_apartment();
        Run().get();
    }

    winrt::Windows::Foundation::IAsyncAction Run()
    {
        co_await winrt::Windows::Storage::FileIO::WriteTextAsync(
                m_file, L"Hello WinRT");
    }
};
```

5. <span data-ttu-id="4e47e-141">Dll 솔루션에서 자식 디렉터리 ARM64/Release/HoloLensWinrtDLL에 대 한 DLL을 빌드하기 위해 **Release > ARM64** 솔루션을 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-141">Build the solution for **Release > ARM64** to build the DLL to the child directory ARM64/Release/HoloLensWinrtDLL from the DLL solution.</span></span> 

## <a name="adding-the-winrt-binary-to-unreal"></a><span data-ttu-id="4e47e-142">Unreal에 WinRT 이진 추가</span><span class="sxs-lookup"><span data-stu-id="4e47e-142">Adding the WinRT binary to Unreal</span></span> 
<span data-ttu-id="4e47e-143">Unreal에서 DLL을 연결 하 고 사용 하려면 c + + 프로젝트가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-143">Linking and using a DLL in Unreal requires a C++ project.</span></span> <span data-ttu-id="4e47e-144">청사진 프로젝트를 사용 하는 경우 c + + 클래스를 추가 하 여 c + + 프로젝트로 쉽게 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-144">If you're using a Blueprint project, it can be easily converted to a C++ project by adding a C++ class:</span></span>  

1. <span data-ttu-id="4e47e-145">Unreal 편집기에서 **파일 > 새 c + + 클래스** ...를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-145">In the Unreal editor, open **File > New C++ Class…**</span></span> <span data-ttu-id="4e47e-146">그리고 DLL에서 코드를 실행 하기 위해 **Winrtactor** 라는 새 **행위자** 를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-146">and create a new **Actor** named **WinrtActor** to run the code in the DLL:</span></span> 

![DLL 구성](images/unreal-winrt-img-04.png)

> [!NOTE]
> <span data-ttu-id="4e47e-148">이제 uproject 파일과 동일한 디렉터리에 Source/ConsumeWinRT/ConsumerWinRT 라는 새 빌드 스크립트와 함께 솔루션이 생성 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-148">A solution has now been created in the same directory as the uproject file along with a new build script named Source/ConsumeWinRT/ConsumerWinRT.Build.cs.</span></span>

2. <span data-ttu-id="4e47e-149">솔루션을 열고, **게임/ConsumeWinRT/Source/ConsumeWinRT** 폴더를 찾아보고, **ConsumeWinRT.build.cs**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-149">Open the solution, browse for the **Games/ConsumeWinRT/Source/ConsumeWinRT** folder, and open **ConsumeWinRT.build.cs**:</span></span>

![DLL 구성](images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a><span data-ttu-id="4e47e-151">DLL 연결</span><span class="sxs-lookup"><span data-stu-id="4e47e-151">Linking the DLL</span></span>
1. <span data-ttu-id="4e47e-152">**ConsumeWinRT.build.cs**에서 속성을 추가 하 여 DLL (HoloLensWinrtDLL이 포함 된 디렉터리)에 대 한 포함 경로를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-152">In **ConsumeWinRT.build.cs**, add a property to find the include path for the DLL (the directory containing HoloLensWinrtDLL.h).</span></span> <span data-ttu-id="4e47e-153">DLL이 포함 경로에 대 한 자식 디렉터리에 있으므로이 속성은 이진 루트 디렉터리로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-153">The DLL is in a child directory to the include path, so this property will be used as the binary root dir:</span></span>

```cs
public class ConsumeWinRT : ModuleRules
{
    private string WinrtIncPath
    {
        get 
        {
            string ModulePath = Path.GetDirectoryName(
                   RulesCompiler.GetFileNameFromType(this.GetType()));

            // Third party directory is at the project root,
            // which is two directories up from the game .exe (Binaries/HoloLens)
            return Path.GetFullPath(
                   Path.Combine(ModulePath,
                   "../../ThirddParty/HoloLensWinrtDLL"));
        }
    }
}
```

2. <span data-ttu-id="4e47e-154">클래스 생성자에서 다음 코드를 추가 하 여 포함 경로를 업데이트 하 고, 새 lib를 연결 하 고, DLL을 지연 로드 하 고 패키지 된 appx 위치에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-154">In the class constructor, add the following code to update the include path, link the new lib, and delay-load and copy the DLL to the packaged appx location:</span></span>

```cs
public ConsumeWinRT(ReadOnlyTargetRules target) : base(Target)
{
    // This is the directory the DLL's include header is in.
    PublicIncludePaths.Add(WinrtIncPath);

    // The code in HoloLensWinrtDLL will only work in a Windows Store app.
    // Only link these binaries for HoloLens.
    // Similar code can be written for desktop and similarly linked 
    // to use the same features when using Holographic Remoting.
    if(Target.Platform == UnrealTargetPlatform.HoloLens)
    {
        // Link the lib
        PublicAdditionalLibraries.Add(Path.Combine(
              WinrtIncPath, "ARM64", "Release",
              "HoloLensWinrtDLL","HoloLensWinrtDLL.lib"));

        string winrtDLL = "HoloLensWinrtDLL.dll";
        // Mark the dll to be DelayLoaded
        PublicDelayLoadDLLs.Add(winrtDLL);
        // RuntimeDependencies are included in packaged builds.
        RuntimeDependencies.Add(Path.Combine(WinrtIncPath,
                "ARM64", "Release", "HoloLensWinrtDLL", winrtDLL));
    }

    // Preserve the original code in build.cs below:
}
```

3. <span data-ttu-id="4e47e-155">**Winrtactor .h** 를 열고 청사진에서 사용할 수 있는 두 개의 함수 정의와 DLL 코드를 사용 하는 다른 함수 정의를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-155">Open **WinrtActor.h** and add two function definitions, one that a blueprint can use and another that uses the DLL code:</span></span> 
```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue;
```

4. <span data-ttu-id="4e47e-156">**Winrtactor .cpp** 를 열고 beginplay에서 DLL을 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-156">Open **WinrtActor.cpp** and load the DLL in BeginPlay:</span></span> 

```cpp
void AWinfrtActor::BeginPlay()
{
#if PLATFORM_HOLOLENS
    HoloLensWinrtDLL::OpenFileDialogue();
#endif
}
``` 

>[!CAUTION]
> <span data-ttu-id="4e47e-157">DLL은 해당 함수를 호출 하기 전에 로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-157">The DLL must be loaded before calling any of its functions.</span></span>

### <a name="building-the-game"></a><span data-ttu-id="4e47e-158">게임 빌드</span><span class="sxs-lookup"><span data-stu-id="4e47e-158">Building the game</span></span>
1. <span data-ttu-id="4e47e-159">게임 솔루션을 빌드하여 게임 프로젝트에 열려 있는 실제이 아닌 편집기를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-159">Build the game solution to launch the Unreal editor opened to the game project:</span></span> 
    * <span data-ttu-id="4e47e-160">**행위자 입력** 탭에서 새 **winrtactor** 를 검색 하 여 장면으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-160">In the **Place Actors** tab, search for the new **WinrtActor** and drag it into the scene</span></span> 
    * <span data-ttu-id="4e47e-161">수준 청사진을 열고 **Winrtactor** 에서 청사진 호출 가능 함수를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-161">Open the level blueprint to execute the blueprint callable function in the **WinrtActor**</span></span> 

![DLL 구성](images/unreal-winrt-img-06.png)

2. <span data-ttu-id="4e47e-163">**세계 Outliner**에서 이전에 장면에 놓인 **Windrtactor** 를 찾아 수준 청사진으로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-163">In the **World Outliner**, find the **WindrtActor** previously dropped into the scene and drag it into the level blueprint:</span></span> 

![DLL 구성](images/unreal-winrt-img-07.png)

3. <span data-ttu-id="4e47e-165">수준 청사진에서 WinrtActor의 출력 노드를 끌어서 **파일 열기 대화 상자**를 검색 한 다음 사용자 입력에서 노드를 라우팅합니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-165">In the level blueprint, drag the output node from WinrtActor, search for **Open File Dialogue**, then route the node from any user input.</span></span>  <span data-ttu-id="4e47e-166">이 경우 음성 이벤트에서 파일 열기 대화 상자가 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-166">In this case, Open File Dialogue is being called from a speech event:</span></span> 

![DLL 구성](images/unreal-winrt-img-08.png)

4. <span data-ttu-id="4e47e-168">[HoloLens에 대해이 게임을 패키지](unreal-uxt-ch6.md)하 고 배포 하 고 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-168">[Package this game for HoloLens](unreal-uxt-ch6.md), deploy it, and run.</span></span>  

<span data-ttu-id="4e47e-169">Unreal에서 OpenFileDialogue을 호출 하면 .txt 파일 이름에 대 한 HoloLens 프롬프트에서 파일 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-169">When Unreal calls OpenFileDialogue, a File Dialogue opens on the HoloLens prompting for a .txt file name.</span></span>  <span data-ttu-id="4e47e-170">파일이 저장 되 면 장치 포털의 **파일 탐색기** 탭으로 이동 하 여 "Hello WinRT" 내용을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-170">After the file is saved, go to the **File explorer** tab in the device portal to see the contents “Hello WinRT”.</span></span> 

## <a name="summary"></a><span data-ttu-id="4e47e-171">요약</span><span class="sxs-lookup"><span data-stu-id="4e47e-171">Summary</span></span> 

<span data-ttu-id="4e47e-172">이 자습서의 코드는 Unreal에서 WinRT 코드를 사용 하기 위한 시작 점으로 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-172">We encourage you to use the code in this tutorial as a starting point for consuming WinRT code in Unreal.</span></span>  <span data-ttu-id="4e47e-173">이를 통해 사용자는 Windows와 동일한 파일 대화 상자를 사용 하 여 HoloLens 디스크에 파일을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-173">It allows users to save files to the HoloLens disk using the same file dialogue as Windows.</span></span>  <span data-ttu-id="4e47e-174">동일한 프로세스를 따라 HoloLensWinrtDLL 헤더에서 추가 함수를 내보내고 Unreal에서 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-174">Follow the same process to export any additional functions from the HoloLensWinrtDLL header and used in Unreal.</span></span>  <span data-ttu-id="4e47e-175">백그라운드 MTA 스레드에서 비동기 WinRT 코드를 대기 하는 DLL 코드를 확인 합니다 .이는 Unreal 게임 스레드의 교착 상태를 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e47e-175">Note the DLL code that waits on any async WinRT code in a background MTA thread, which avoids deadlocking the Unreal game thread.</span></span> 

## <a name="see-also"></a><span data-ttu-id="4e47e-176">참조</span><span class="sxs-lookup"><span data-stu-id="4e47e-176">See also</span></span>
* [<span data-ttu-id="4e47e-177">C + +/WinRT Api</span><span class="sxs-lookup"><span data-stu-id="4e47e-177">C++/WinRT APIs</span></span>](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)
* [<span data-ttu-id="4e47e-178">FileSavePicker 클래스</span><span class="sxs-lookup"><span data-stu-id="4e47e-178">FileSavePicker class</span></span>](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [<span data-ttu-id="4e47e-179">실제 타사 라이브러리</span><span class="sxs-lookup"><span data-stu-id="4e47e-179">Unreal Third-Party Libraries</span></span>](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html) 
