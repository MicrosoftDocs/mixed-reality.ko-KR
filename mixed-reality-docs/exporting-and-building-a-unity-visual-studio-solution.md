---
title: 내보내기 및 Unity Visual Studio 솔루션 빌드
description: 이 문서 작성 하 고 Visual Studio에서 배포할 수 있도록 Unity에서 혼합된 현실 프로젝트 내보내기 설명 합니다.
author: ''
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: visual studio unity 내보내기, 빌드, 배포
ms.openlocfilehash: 68c86fdfe0e589536dafe2bf53c7d4e5dffcc514
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603697"
---
# <a name="exporting-and-building-a-unity-visual-studio-solution"></a><span data-ttu-id="e1211-104">내보내기 및 Unity Visual Studio 솔루션 빌드</span><span class="sxs-lookup"><span data-stu-id="e1211-104">Exporting and building a Unity Visual Studio solution</span></span>

<span data-ttu-id="e1211-105">권장 사항은 사용 하는 것에 시스템 키보드를 사용 하 여 응용 프로그램에서 하지, *D3D* 응용 프로그램은 약간 적은 메모리를 사용 하 고 시작 시간이 약간 더 빠릅니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-105">If you don't intend on using the system keyboard in your application, our recommendation is to use *D3D* as your application will use slightly less memory and have a slightly faster launch time.</span></span> <span data-ttu-id="e1211-106">프로젝트에서 TouchScreenKeyboard API를 사용 하 여 시스템 키보드를 사용 하는, 경우로 내보내려면 *XAML*합니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-106">If you are using the TouchScreenKeyboard API in your project to use the system keyboard, you need to export as *XAML*.</span></span>

## <a name="how-to-export-from-unity"></a><span data-ttu-id="e1211-107">Unity에서 내보내는 방법</span><span class="sxs-lookup"><span data-stu-id="e1211-107">How to export from Unity</span></span>

<span data-ttu-id="e1211-108">![Unity 빌드 설정](images/unitybuildsettings-300px.png)</span><span class="sxs-lookup"><span data-stu-id="e1211-108">![Unity build settings](images/unitybuildsettings-300px.png)</span></span><br>
<span data-ttu-id="e1211-109">*Unity 빌드 설정*</span><span class="sxs-lookup"><span data-stu-id="e1211-109">*Unity build settings*</span></span>

1. <span data-ttu-id="e1211-110">Unity에서 프로젝트를 내보낼 준비가 되었을 때 엽니다는 **파일** 선택한 메뉴 **빌드 설정...**</span><span class="sxs-lookup"><span data-stu-id="e1211-110">When you are ready to export your project from Unity, open the **File** menu and select **Build Settings...**</span></span>
2. <span data-ttu-id="e1211-111">클릭 **열기 장면 추가** 빌드에 장면 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-111">Click **Add Open Scenes** to add your scene to the build.</span></span>
3. <span data-ttu-id="e1211-112">에 **빌드 설정** 대화 상자에서 HoloLens에 대 한 내보내려면 다음 옵션을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-112">In the **Build Settings** dialog, choose the following options to export for HoloLens:</span></span>
   * <span data-ttu-id="e1211-113">**플랫폼:** *유니버설 Windows 플랫폼* 를 선택 해야 **플랫폼 전환** 적용 하려면 선택 항목에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-113">**Platform:** *Universal Windows Platform* and be sure to select **Switch Platform** for your selection to take effect.</span></span>
   * <span data-ttu-id="e1211-114">**SDK:** *유니버설 10*합니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-114">**SDK:** *Universal 10*.</span></span>
   * <span data-ttu-id="e1211-115">**UWP 빌드 유형:** *D3D*.</span><span class="sxs-lookup"><span data-stu-id="e1211-115">**UWP Build Type:** *D3D*.</span></span>
4. <span data-ttu-id="e1211-116">**선택적**: **Unity C# 프로젝트:** 이 옵션을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-116">**Optional**: **Unity C# Projects:** Checked.</span></span>

>[!NOTE]
><span data-ttu-id="e1211-117">이 확인란을 선택 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-117">Checking this box allows you to:</span></span>
>* <span data-ttu-id="e1211-118">Visual Studio 원격 디버거에서 앱을 디버그 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-118">Debug your app in the Visual Studio remote debugger.</span></span>
>* <span data-ttu-id="e1211-119">Unity에서 스크립트를 편집 C# WinRT Api에 대 한 IntelliSense를 사용 하는 동안 프로젝트입니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-119">Edit scripts in the Unity C# project while using IntelliSense for WinRT APIs.</span></span>

5. <span data-ttu-id="e1211-120">**빌드 설정...**  창을 열려면 **플레이어 설정...**</span><span class="sxs-lookup"><span data-stu-id="e1211-120">From the **Build Settings...** window, open **Player Settings...**</span></span>
6. <span data-ttu-id="e1211-121">선택 된 **유니버설 Windows 플랫폼에 대 한 설정을** 탭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-121">Select the **Settings for Universal Windows Platform** tab.</span></span>
7. <span data-ttu-id="e1211-122">확장 된 **xr 하이 설정을** 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-122">Expand the **XR Settings** group.</span></span>
8. <span data-ttu-id="e1211-123">에 **xr 하이 설정** 섹션을 확인 합니다 **가상 현실 지원** 새 추가 하려면이 확인란을 **가상 현실 장치용** 나열 하 고 확인 **"Windows 혼합 Reality"** 지원 되는 장치로 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-123">In the **XR Settings** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality Devices** list and confirm **"Windows Mixed Reality"** is listed as a supported device.</span></span>
9. <span data-ttu-id="e1211-124">반환 합니다 **빌드 설정** 대화 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-124">Return to the **Build Settings** dialog.</span></span>
10. <span data-ttu-id="e1211-125">선택 **빌드**합니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-125">Select **Build**.</span></span>
11. <span data-ttu-id="e1211-126">표시 되는 Windows 탐색기 대화 상자에서 Unity의 빌드 출력을 포함할 새 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-126">In the Windows Explorer dialog that appears, create a new folder to hold Unity's build output.</span></span> <span data-ttu-id="e1211-127">일반적으로 "App" 폴더를 이름을합니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-127">Generally, we name the folder "App".</span></span>
12. <span data-ttu-id="e1211-128">새로 만든된 폴더를 선택 하 고 클릭 **폴더 선택**합니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-128">Select the newly created folder and click **Select Folder**.</span></span>
13. <span data-ttu-id="e1211-129">Unity 빌드 완료 되 면 프로젝트 루트 디렉터리는 Windows 탐색기 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-129">Once Unity has finished building, a Windows Explorer window will open to the project root directory.</span></span> <span data-ttu-id="e1211-130">새로 만든 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-130">Navigate into the newly created folder.</span></span>
14. <span data-ttu-id="e1211-131">이 폴더 안에 있는 생성 된 Visual Studio 솔루션 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-131">Open the generated Visual Studio solution file located inside this folder.</span></span>

## <a name="when-to-re-export-from-unity"></a><span data-ttu-id="e1211-132">Unity에서 다시 내보내야 하는 경우</span><span class="sxs-lookup"><span data-stu-id="e1211-132">When to re-export from Unity</span></span>

<span data-ttu-id="e1211-133">확인 된 "C# 프로젝트"에 모든 Unity 스크립트 파일을 포함 하는 Unity에서 앱을 내보내는 만들 때 Visual Studio 솔루션을 하는 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-133">Checking the "C# Projects" checkbox when exporting your app from Unity creates a Visual Studio solution that includes all your Unity script files.</span></span> <span data-ttu-id="e1211-134">이 옵션을 사용 하면 스크립트에서 Unity를 다시 내보내지 않고 반복할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-134">This allows you to iterate on your scripts without re-exporting from Unity.</span></span> <span data-ttu-id="e1211-135">그러나 스크립트의 내용을 변경 하지는 프로젝트에 변경 하려는 경우에 Unity에서 다시 내보낼 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-135">However, if you want to make changes to your project that aren't just changing the contents of scripts, you will need to re-export from Unity.</span></span> <span data-ttu-id="e1211-136">Unity에서 다시 내보내야 하는 시간의 몇 가지 예는:</span><span class="sxs-lookup"><span data-stu-id="e1211-136">Some examples of times you need to re-export from Unity are:</span></span>
* <span data-ttu-id="e1211-137">추가 하거나 프로젝트 탭에서 자산을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-137">You add or remove assets in the Project tab.</span></span>
* <span data-ttu-id="e1211-138">관리자 탭에서 모든 값을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-138">You change any value in the Inspector tab.</span></span>
* <span data-ttu-id="e1211-139">추가 하거나 계층 구조 탭에서 개체를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-139">You add or remove objects from the Hierarchy tab.</span></span>
* <span data-ttu-id="e1211-140">Unity 프로젝트 설정을 변경 하기</span><span class="sxs-lookup"><span data-stu-id="e1211-140">You change any Unity project settings</span></span>

## <a name="building-and-deploying-a-unity-visual-studio-solution"></a><span data-ttu-id="e1211-141">Unity Visual Studio 솔루션을 구축 및 배포</span><span class="sxs-lookup"><span data-stu-id="e1211-141">Building and deploying a Unity Visual Studio solution</span></span>

<span data-ttu-id="e1211-142">앱 빌드 및 배포의 나머지 부분에서 발생 [Visual Studio](using-visual-studio.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-142">The remainder of building and deploying apps happens in [Visual Studio](using-visual-studio.md).</span></span> <span data-ttu-id="e1211-143">Unity 빌드 구성을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-143">You will need to specify a Unity build configuration.</span></span> <span data-ttu-id="e1211-144">Unity의 명명 규칙에서 무엇을 하 고 일반적으로 하는 데 Visual Studio에서 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-144">Unity's naming conventions may differ from what you're usually used to in Visual Studio:</span></span>

|  <span data-ttu-id="e1211-145">Configuration</span><span class="sxs-lookup"><span data-stu-id="e1211-145">Configuration</span></span>  |  <span data-ttu-id="e1211-146">설명</span><span class="sxs-lookup"><span data-stu-id="e1211-146">Explanation</span></span> | 
|----------|----------|
|  <span data-ttu-id="e1211-147">디버그</span><span class="sxs-lookup"><span data-stu-id="e1211-147">Debug</span></span>  |  <span data-ttu-id="e1211-148">모든 최적화 해제 및 프로파일러 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-148">All optimizations off and the profiler is enabled.</span></span> <span data-ttu-id="e1211-149">스크립트를 디버그 하는 데 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-149">Used to debug scripts.</span></span> | 
|  <span data-ttu-id="e1211-150">마스터</span><span class="sxs-lookup"><span data-stu-id="e1211-150">Master</span></span>  |  <span data-ttu-id="e1211-151">모든 최적화 켜져 있고 프로파일러를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-151">All optimizations are turned on and the profiler is disabled.</span></span> <span data-ttu-id="e1211-152">앱 스토어에 제출 하는 데 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-152">Used to submit apps to the Store.</span></span> | 
|  <span data-ttu-id="e1211-153">릴리스</span><span class="sxs-lookup"><span data-stu-id="e1211-153">Release</span></span>  |  <span data-ttu-id="e1211-154">모든 최적화가 설정 하 고 프로파일러 활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-154">All optimizations are turned on and the profiler is enabled.</span></span> <span data-ttu-id="e1211-155">앱 성능을 평가 하는 데 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-155">Used to evaluate app performance.</span></span> | 

<span data-ttu-id="e1211-156">Note 위의 목록은 Visual Studio 프로젝트를 생성 해야 하는 일반적인 트리거의 하위 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-156">Note, the above list is a subset of the common triggers that will cause the Visual Studio project to need to be generated.</span></span> <span data-ttu-id="e1211-157">일반적으로 Visual Studio 내에서.cs 파일을 편집 하는 프로젝트에서 Unity 내에서 다시 생성할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-157">In general, editing .cs files from within Visual Studio will not require the project to be regenerated from within Unity.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="e1211-158">문제 해결</span><span class="sxs-lookup"><span data-stu-id="e1211-158">Troubleshooting</span></span>

<span data-ttu-id="e1211-159">Visual Studio 프로젝트의.cs 파일을 편집 하지 인식 되는 경우를 확인 하는 "Unity C# 프로젝트" VS 프로젝트 Unity의 빌드 메뉴에서 생성 하는 경우 확인 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1211-159">If you find that edits to your .cs files are not being recognized in your Visual Studio project, ensure that "Unity C# Projects" is checked when you generate the VS project from Unity's Build menu.</span></span>
