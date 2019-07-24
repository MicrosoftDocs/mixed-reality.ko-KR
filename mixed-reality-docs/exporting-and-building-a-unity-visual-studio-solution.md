---
title: Unity Visual Studio 솔루션 내보내기 및 빌드
description: 이 문서에서는 Visual Studio에서 빌드 및 배포할 수 있도록 Unity에서 혼합 현실 프로젝트를 내보내는 방법을 간략하게 설명 합니다.
author: ''
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: unity, visual studio, 내보내기, 빌드, 배포
ms.openlocfilehash: 68c86fdfe0e589536dafe2bf53c7d4e5dffcc514
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63525843"
---
# <a name="exporting-and-building-a-unity-visual-studio-solution"></a><span data-ttu-id="94510-104">Unity Visual Studio 솔루션 내보내기 및 빌드</span><span class="sxs-lookup"><span data-stu-id="94510-104">Exporting and building a Unity Visual Studio solution</span></span>

<span data-ttu-id="94510-105">응용 프로그램에서 시스템 키보드를 사용 하지 않으려는 경우 응용 프로그램에서 메모리를 약간 줄이고 시작 시간을 약간 단축 하므로 *D3D* 를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="94510-105">If you don't intend on using the system keyboard in your application, our recommendation is to use *D3D* as your application will use slightly less memory and have a slightly faster launch time.</span></span> <span data-ttu-id="94510-106">프로젝트에서 TouchScreenKeyboard API를 사용 하 여 시스템 키보드를 사용 하는 경우 *XAML*로 내보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="94510-106">If you are using the TouchScreenKeyboard API in your project to use the system keyboard, you need to export as *XAML*.</span></span>

## <a name="how-to-export-from-unity"></a><span data-ttu-id="94510-107">Unity에서 내보내는 방법</span><span class="sxs-lookup"><span data-stu-id="94510-107">How to export from Unity</span></span>

<span data-ttu-id="94510-108">![Unity 빌드 설정](images/unitybuildsettings-300px.png)</span><span class="sxs-lookup"><span data-stu-id="94510-108">![Unity build settings](images/unitybuildsettings-300px.png)</span></span><br>
<span data-ttu-id="94510-109">*Unity 빌드 설정*</span><span class="sxs-lookup"><span data-stu-id="94510-109">*Unity build settings*</span></span>

1. <span data-ttu-id="94510-110">Unity에서 프로젝트를 내보낼 준비가 되 면 **파일** 메뉴를 열고 **빌드 설정** ...을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="94510-110">When you are ready to export your project from Unity, open the **File** menu and select **Build Settings...**</span></span>
2. <span data-ttu-id="94510-111">열려 있는 장면 **추가** 를 클릭 하 여 빌드에 장면을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="94510-111">Click **Add Open Scenes** to add your scene to the build.</span></span>
3. <span data-ttu-id="94510-112">**빌드 설정** 대화 상자에서 다음 옵션을 선택 하 여 HoloLens를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="94510-112">In the **Build Settings** dialog, choose the following options to export for HoloLens:</span></span>
   * <span data-ttu-id="94510-113">**Platform.string** *유니버설 Windows 플랫폼* 하 고 선택 항목을 적용 하려면 **스위치 플랫폼** 을 선택 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="94510-113">**Platform:** *Universal Windows Platform* and be sure to select **Switch Platform** for your selection to take effect.</span></span>
   * <span data-ttu-id="94510-114">**SDK** *유니버설 10*.</span><span class="sxs-lookup"><span data-stu-id="94510-114">**SDK:** *Universal 10*.</span></span>
   * <span data-ttu-id="94510-115">**UWP 빌드 형식:** *D3D*.</span><span class="sxs-lookup"><span data-stu-id="94510-115">**UWP Build Type:** *D3D*.</span></span>
4. <span data-ttu-id="94510-116">**선택 사항**: **Unity C# 프로젝트:** 검사할.</span><span class="sxs-lookup"><span data-stu-id="94510-116">**Optional**: **Unity C# Projects:** Checked.</span></span>

>[!NOTE]
><span data-ttu-id="94510-117">이 확인란을 선택 하면 다음 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94510-117">Checking this box allows you to:</span></span>
>* <span data-ttu-id="94510-118">Visual Studio 원격 디버거에서 앱을 디버그 합니다.</span><span class="sxs-lookup"><span data-stu-id="94510-118">Debug your app in the Visual Studio remote debugger.</span></span>
>* <span data-ttu-id="94510-119">WinRT Api 용 IntelliSense를 C# 사용 하는 동안 Unity 프로젝트의 스크립트를 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="94510-119">Edit scripts in the Unity C# project while using IntelliSense for WinRT APIs.</span></span>

5. <span data-ttu-id="94510-120">**빌드 설정 ...** 창에서 **플레이어 설정 ...** 을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="94510-120">From the **Build Settings...** window, open **Player Settings...**</span></span>
6. <span data-ttu-id="94510-121">유니버설 Windows 플랫폼 탭 **에 대 한 설정을** 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="94510-121">Select the **Settings for Universal Windows Platform** tab.</span></span>
7. <span data-ttu-id="94510-122">**XR 설정** 그룹을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="94510-122">Expand the **XR Settings** group.</span></span>
8. <span data-ttu-id="94510-123">**XR 설정** 섹션에서 **가상 현실 지원** 확인란을 선택 하 여 새 **가상 현실 장치** 목록을 추가 하 고 **"Windows Mixed Reality"** 가 지원 되는 장치로 나열 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="94510-123">In the **XR Settings** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality Devices** list and confirm **"Windows Mixed Reality"** is listed as a supported device.</span></span>
9. <span data-ttu-id="94510-124">**빌드 설정** 대화 상자로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="94510-124">Return to the **Build Settings** dialog.</span></span>
10. <span data-ttu-id="94510-125">**빌드**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="94510-125">Select **Build**.</span></span>
11. <span data-ttu-id="94510-126">표시 되는 Windows 탐색기 대화 상자에서 Unity의 빌드 출력을 보관할 새 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="94510-126">In the Windows Explorer dialog that appears, create a new folder to hold Unity's build output.</span></span> <span data-ttu-id="94510-127">일반적으로 "App" 폴더의 이름을로 합니다.</span><span class="sxs-lookup"><span data-stu-id="94510-127">Generally, we name the folder "App".</span></span>
12. <span data-ttu-id="94510-128">새로 만든 폴더를 선택 하 고 **폴더 선택**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="94510-128">Select the newly created folder and click **Select Folder**.</span></span>
13. <span data-ttu-id="94510-129">Unity가 빌드를 완료 하면 Windows 탐색기 창이 프로젝트 루트 디렉터리에 열립니다.</span><span class="sxs-lookup"><span data-stu-id="94510-129">Once Unity has finished building, a Windows Explorer window will open to the project root directory.</span></span> <span data-ttu-id="94510-130">새로 만든 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="94510-130">Navigate into the newly created folder.</span></span>
14. <span data-ttu-id="94510-131">이 폴더 내에 있는 생성 된 Visual Studio 솔루션 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="94510-131">Open the generated Visual Studio solution file located inside this folder.</span></span>

## <a name="when-to-re-export-from-unity"></a><span data-ttu-id="94510-132">Unity에서 다시 내보내는 경우</span><span class="sxs-lookup"><span data-stu-id="94510-132">When to re-export from Unity</span></span>

<span data-ttu-id="94510-133">Unity에서 앱C# 을 내보낼 때 "프로젝트" 확인란을 선택 하면 모든 Unity 스크립트 파일이 포함 된 Visual Studio 솔루션이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="94510-133">Checking the "C# Projects" checkbox when exporting your app from Unity creates a Visual Studio solution that includes all your Unity script files.</span></span> <span data-ttu-id="94510-134">이를 통해 Unity에서 다시 내보내지 않고 스크립트를 반복할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94510-134">This allows you to iterate on your scripts without re-exporting from Unity.</span></span> <span data-ttu-id="94510-135">그러나 스크립트의 내용만 변경 하지 않는 프로젝트를 변경 하려는 경우에는 Unity에서 다시 내보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="94510-135">However, if you want to make changes to your project that aren't just changing the contents of scripts, you will need to re-export from Unity.</span></span> <span data-ttu-id="94510-136">Unity에서 다시 내보내는 데 필요한 몇 가지 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="94510-136">Some examples of times you need to re-export from Unity are:</span></span>
* <span data-ttu-id="94510-137">프로젝트 탭에서 자산을 추가 하거나 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="94510-137">You add or remove assets in the Project tab.</span></span>
* <span data-ttu-id="94510-138">Inspector 탭에서 값을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="94510-138">You change any value in the Inspector tab.</span></span>
* <span data-ttu-id="94510-139">계층 탭에서 개체를 추가 하거나 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="94510-139">You add or remove objects from the Hierarchy tab.</span></span>
* <span data-ttu-id="94510-140">Unity 프로젝트 설정을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="94510-140">You change any Unity project settings</span></span>

## <a name="building-and-deploying-a-unity-visual-studio-solution"></a><span data-ttu-id="94510-141">Unity Visual Studio 솔루션 빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="94510-141">Building and deploying a Unity Visual Studio solution</span></span>

<span data-ttu-id="94510-142">응용 프로그램 빌드 및 배포의 나머지 부분은 [Visual Studio](using-visual-studio.md)에서 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="94510-142">The remainder of building and deploying apps happens in [Visual Studio](using-visual-studio.md).</span></span> <span data-ttu-id="94510-143">Unity 빌드 구성을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="94510-143">You will need to specify a Unity build configuration.</span></span> <span data-ttu-id="94510-144">Unity의 명명 규칙은 Visual Studio에서 일반적으로 사용 하는 것과 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94510-144">Unity's naming conventions may differ from what you're usually used to in Visual Studio:</span></span>

|  <span data-ttu-id="94510-145">Configuration</span><span class="sxs-lookup"><span data-stu-id="94510-145">Configuration</span></span>  |  <span data-ttu-id="94510-146">설명</span><span class="sxs-lookup"><span data-stu-id="94510-146">Explanation</span></span> | 
|----------|----------|
|  <span data-ttu-id="94510-147">디버그</span><span class="sxs-lookup"><span data-stu-id="94510-147">Debug</span></span>  |  <span data-ttu-id="94510-148">모든 최적화를 해제 하 고 프로파일러를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="94510-148">All optimizations off and the profiler is enabled.</span></span> <span data-ttu-id="94510-149">스크립트를 디버깅 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="94510-149">Used to debug scripts.</span></span> | 
|  <span data-ttu-id="94510-150">마스터</span><span class="sxs-lookup"><span data-stu-id="94510-150">Master</span></span>  |  <span data-ttu-id="94510-151">모든 최적화를 사용 하도록 설정 하 고 프로파일러를 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="94510-151">All optimizations are turned on and the profiler is disabled.</span></span> <span data-ttu-id="94510-152">스토어에 앱을 제출 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="94510-152">Used to submit apps to the Store.</span></span> | 
|  <span data-ttu-id="94510-153">릴리스</span><span class="sxs-lookup"><span data-stu-id="94510-153">Release</span></span>  |  <span data-ttu-id="94510-154">모든 최적화를 설정 하 고 프로파일러를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="94510-154">All optimizations are turned on and the profiler is enabled.</span></span> <span data-ttu-id="94510-155">앱 성능을 평가 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="94510-155">Used to evaluate app performance.</span></span> | 

<span data-ttu-id="94510-156">위의 목록은 Visual Studio 프로젝트를 생성 해야 하는 일반적인 트리거의 하위 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="94510-156">Note, the above list is a subset of the common triggers that will cause the Visual Studio project to need to be generated.</span></span> <span data-ttu-id="94510-157">일반적으로 Visual Studio 내에서 .cs 파일을 편집 하는 경우 Unity 내에서 프로젝트를 다시 생성할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="94510-157">In general, editing .cs files from within Visual Studio will not require the project to be regenerated from within Unity.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="94510-158">문제 해결</span><span class="sxs-lookup"><span data-stu-id="94510-158">Troubleshooting</span></span>

<span data-ttu-id="94510-159">Visual Studio 프로젝트에서 .cs 파일에 대 한 편집 내용이 인식 되지 않는 것을 발견 한 경우 Unity의 빌드 메뉴에서 C# VS 프로젝트를 생성할 때 "unity 프로젝트"가 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="94510-159">If you find that edits to your .cs files are not being recognized in your Visual Studio project, ensure that "Unity C# Projects" is checked when you generate the VS project from Unity's Build menu.</span></span>
