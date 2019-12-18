---
title: 공간 오디오 자습서-1. 프로젝트에 공간 오디오 추가
description: Microsoft Spatializer 플러그 인을 Unity 프로젝트에 추가 하 여 HoloLens 2 HRTF 하드웨어 오프 로드에 액세스 합니다.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens2, 공간 오디오
ms.openlocfilehash: 8978017b3ce6c49a81b3eee2fe21e9234f4e71f0
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182800"
---
# <a name="adding-spatial-audio-to-your-unity-project"></a><span data-ttu-id="2fecf-105">Unity 프로젝트에 공간 오디오 추가</span><span class="sxs-lookup"><span data-stu-id="2fecf-105">Adding spatial audio to your Unity project</span></span>

<span data-ttu-id="2fecf-106">HoloLens2에 대 한 tutioral for Unity의 공간 오디오를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fecf-106">Welcome to the spatial audio tutioral for Unity on HoloLens2.</span></span> <span data-ttu-id="2fecf-107">이 자습서 시퀀스는 다음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2fecf-107">This tutorial sequence shows:</span></span>
* <span data-ttu-id="2fecf-108">Unity의 HoloLens 2에서 HRTF 오프 로드를 사용 하는 방법</span><span class="sxs-lookup"><span data-stu-id="2fecf-108">How to use HRTF offload on HoloLens 2 in Unity</span></span>
* <span data-ttu-id="2fecf-109">HRTF 오프 로드를 사용할 때 반향 기능을 사용 하도록 설정 하는 방법</span><span class="sxs-lookup"><span data-stu-id="2fecf-109">How to enable reverb when using HRTF offload</span></span>

<span data-ttu-id="2fecf-110">[Microsoft Spatializer GitHub 리포지토리](https://github.com/microsoft/spatialaudio-unity) 는이 자습서 시퀀스의 완료 된 Unity 프로젝트를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fecf-110">The [Microsoft Spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity) has a completed Unity project of this tutorial sequence.</span></span> 

<span data-ttu-id="2fecf-111">소리를 spatialize 하는 데 도움이 될 수 있는 경우의 권장 사항은 [공간 사운드 디자인](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2fecf-111">For our recommendations on when it can be helpful to spatialize sounds, see [spatial sound design](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).</span></span>

## <a name="objectives"></a><span data-ttu-id="2fecf-112">목표</span><span class="sxs-lookup"><span data-stu-id="2fecf-112">Objectives</span></span>
<span data-ttu-id="2fecf-113">이 첫 번째 장에서는 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fecf-113">In this first chapter, you'll:</span></span>
* <span data-ttu-id="2fecf-114">Unity 프로젝트 만들기 및 MRTK 가져오기</span><span class="sxs-lookup"><span data-stu-id="2fecf-114">Create a Unity project and import MRTK</span></span>
* <span data-ttu-id="2fecf-115">Microsoft spatializer 플러그 인 가져오기</span><span class="sxs-lookup"><span data-stu-id="2fecf-115">Import the Microsoft spatializer plugin</span></span>
* <span data-ttu-id="2fecf-116">Microsoft spatializer 플러그 인 사용</span><span class="sxs-lookup"><span data-stu-id="2fecf-116">Enable the Microsoft spatializer plugin</span></span>
* <span data-ttu-id="2fecf-117">개발자 워크스테이션에서 공간 오디오 사용</span><span class="sxs-lookup"><span data-stu-id="2fecf-117">Enable spatial audio on your developer workstation</span></span>

## <a name="create-a-project-and-add-nuget-for-unity"></a><span data-ttu-id="2fecf-118">프로젝트 만들기 및 Unity 용 NuGet 추가</span><span class="sxs-lookup"><span data-stu-id="2fecf-118">Create a project and add NuGet for Unity</span></span>
<span data-ttu-id="2fecf-119">빈 Unity 프로젝트로 시작한 다음 Unity에 대해 NuGet을 추가 하 고 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fecf-119">Start with an empty Unity project, then add and configure NuGet for Unity:</span></span>
1. <span data-ttu-id="2fecf-120">최신 NuGetForUnity를 다운로드 [합니다. unitypackage](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)</span><span class="sxs-lookup"><span data-stu-id="2fecf-120">Download the latest [NuGetForUnity .unitypackage](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)</span></span>
2. <span data-ttu-id="2fecf-121">Unity 메뉴 모음에서 **자산-> 가져오기 패키지-> 사용자 지정 패키지** ...를 클릭 하 고 NuGetForUnity 패키지를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fecf-121">In the Unity menu bar, click **Assets -> Import Package -> Custom Package...** and install the NuGetForUnity package:</span></span>

![사용자 지정 패키지 가져오기](images/spatial-audio/import-custom-package.png)

## <a name="add-the-windows-mixed-reality-package"></a><span data-ttu-id="2fecf-123">Windows Mixed Reality 패키지 추가</span><span class="sxs-lookup"><span data-stu-id="2fecf-123">Add the Windows Mixed Reality package</span></span>
<span data-ttu-id="2fecf-124">Unity 2019 이상에서 Windows Mixed Reality 지원은 선택적 패키지에 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2fecf-124">Windows Mixed Reality support in Unity 2019 and later is contained in an optional package.</span></span> <span data-ttu-id="2fecf-125">프로젝트에 추가 하려면 Unity 메뉴 모음에서 **창 > 패키지 관리자** 를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2fecf-125">To add it to your project, open **Window -> Package Manager** from the Unity menu bar:</span></span>

![패키지 관리자 메뉴](images/spatial-audio/package-manager-menu.png)

<span data-ttu-id="2fecf-127">그런 다음 **Windows Mixed Reality** 패키지를 찾아서 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fecf-127">Then find and install the **Windows Mixed Reality** package:</span></span>

![패키지 관리자 창](images/spatial-audio/package-manager-window.png)

## <a name="install-mrtk-and-microsoft-spatializer"></a><span data-ttu-id="2fecf-129">MRTK 및 Microsoft Spatializer 설치</span><span class="sxs-lookup"><span data-stu-id="2fecf-129">Install MRTK and Microsoft Spatializer</span></span>
<span data-ttu-id="2fecf-130">Unity에 NuGet을 사용 하 여 MRTK 및 Microsoft Spatializer 플러그 인을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fecf-130">Using NuGet for Unity, install the MRTK and Microsoft Spatializer plugins:</span></span>
1. <span data-ttu-id="2fecf-131">Unity 메뉴 모음에서 **nuget > Nuget 패키지 관리**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fecf-131">In the Unity menu bar, click on **NuGet -> Manage NuGet Packages**.</span></span>

![NuGet 패키지 관리](images/spatial-audio/manage-nuget-packages.png)

2. <span data-ttu-id="2fecf-133">**검색** 상자에 "MixedReality"를 입력 하 고 MRTK 핵심 패키지: **MixedReality** 를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fecf-133">In the **Search** box, enter "Microsoft.MixedReality.Toolkit" and install the MRTK core package: **Microsoft.MixedReality.Toolkit.Foundation**</span></span>

![MRTK NuGet 패키지](images/spatial-audio/mrtk-nuget-package.png)

<span data-ttu-id="2fecf-135">[Mrtk NuGet 패키지](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) 에는 추가 컨텍스트 및 세부 정보가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2fecf-135">[MRTK NuGet Package](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) has additional context and details.</span></span>

4. <span data-ttu-id="2fecf-136">**검색** 상자에 "SpatialAudio"를 입력 하 고 microsoft Spatializer Package: SpatialAudio를 설치 합니다. **Spatializer**</span><span class="sxs-lookup"><span data-stu-id="2fecf-136">In the **Search** box, enter "Microsoft.SpatialAudio" and install the Microsoft Spatializer package: **Microsoft.SpatialAudio.Spatializer.Unity**</span></span>

![Spatializer 플러그 인 NuGet](images/spatial-audio/spatializer-plugin-nuget.png)

## <a name="set-up-mrtk-in-your-project"></a><span data-ttu-id="2fecf-138">프로젝트에서 MRTK 설정</span><span class="sxs-lookup"><span data-stu-id="2fecf-138">Set up MRTK in your project</span></span>

1. <span data-ttu-id="2fecf-139">**파일 > 빌드 설정**으로 이동 하 여 빌드 설정 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2fecf-139">Open the Build Settings window by going to **File -> Build Settings**.</span></span>

2. <span data-ttu-id="2fecf-140">_유니버설 Windows 플랫폼_ 를 선택 하 고 **플랫폼 전환**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fecf-140">Select the _Universal Windows Platform_ and click **Switch Platform**.</span></span>

3. <span data-ttu-id="2fecf-141">**빌드 창** 에서 **플레이어 설정** 을 클릭 하 여 **검사기** 창에서 **플레이어 설정** 속성을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2fecf-141">Click **Player Settings** in the **Build Window** to open the **Player Settings** properties in the **Inspector** pane.</span></span>
    * <span data-ttu-id="2fecf-142">**XR 설정**에서 **가상 현실 지원** 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fecf-142">Under **XR Settings**, check the **Virtual Reality Supported** checkbox</span></span>
    * <span data-ttu-id="2fecf-143">**XR 설정**에서 **스테레오 렌더링 모드** 를 **인스턴스 하나로**변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fecf-143">Under **XR Settings**, change the **Stereo Rendering Mode** to **Single Pass Instanced**.</span></span>
    * <span data-ttu-id="2fecf-144">**게시 설정**에서 **기능** 섹션의 **공간 인식** 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fecf-144">Under **Publishing Settings**, check the **Spatial Perception** checkbox in the **Capabilities** section</span></span>

4. <span data-ttu-id="2fecf-145">메뉴 모음에서 **혼합 현실 도구 키트-장면에 추가 및 구성 >를 클릭 합니다.**</span><span class="sxs-lookup"><span data-stu-id="2fecf-145">On the menu bar, click **Mixed Reality Toolkit -> Add to Scene and Configure..**</span></span> <span data-ttu-id="2fecf-146">장면에 MRTK를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fecf-146">to add MRTK to your scene.</span></span>

<span data-ttu-id="2fecf-147">앱을 빌드하고 HoloLens 2에 배포 하는 방법을 비롯 한 추가 지침은 [MR 학습 기본 모듈의 1 장](mrlearning-base-ch1.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2fecf-147">For additional guidance, including how to build your app and deploy to a HoloLens 2, see [Chapter 1 of the MR Learning Base Module](mrlearning-base-ch1.md).</span></span>

## <a name="enable-the-microsoft-spatializer-plugin"></a><span data-ttu-id="2fecf-148">Microsoft Spatializer 플러그 인 사용</span><span class="sxs-lookup"><span data-stu-id="2fecf-148">Enable the Microsoft Spatializer plugin</span></span>
<span data-ttu-id="2fecf-149">**Microsoft Spatializer** 플러그 인을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fecf-149">Enable the **Microsoft Spatializer** plugin.</span></span> <span data-ttu-id="2fecf-150">**편집 > 프로젝트 설정-오디오 >** 열고 **Spatializer 플러그 인** 을 "Microsoft Spatializer"로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fecf-150">Open **Edit -> Project Settings -> Audio**, and change **Spatializer Plugin** to "Microsoft Spatializer".</span></span> <span data-ttu-id="2fecf-151">이제 **프로젝트 설정** 의 **Audio** 섹션이 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2fecf-151">The **Audio** section of the **Project Settings** will now look like this:</span></span>

![Spatializer 플러그 인을 보여 주는 프로젝트 설정](images/spatial-audio/project-settings.png)

## <a name="enable-spatial-audio-on-your-workstation"></a><span data-ttu-id="2fecf-153">워크스테이션에서 공간 오디오 사용</span><span class="sxs-lookup"><span data-stu-id="2fecf-153">Enable spatial audio on your workstation</span></span>
<span data-ttu-id="2fecf-154">데스크톱 버전의 Windows에서는 공간 오디오가 기본적으로 사용 하지 않도록 설정 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2fecf-154">On desktop versions of Windows, spatial audio is disabled by default.</span></span> <span data-ttu-id="2fecf-155">작업 표시줄에서 볼륨 아이콘을 마우스 오른쪽 단추로 클릭 하 여 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fecf-155">Enable it by right-clicking on the volume icon in the task bar.</span></span> <span data-ttu-id="2fecf-156">HoloLens 2에서 제공 하는 내용을 가장 잘 표시 하려면 **공간 사운드-헤드폰 용 Windows Sonic >** 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fecf-156">To get the best representation of what you'll hear on HoloLens 2, choose **Spatial sound -> Windows Sonic for Headphones**.</span></span>

![데스크톱 공간 오디오 설정](images/spatial-audio/desktop-audio-settings.png)

> [!NOTE]
> <span data-ttu-id="2fecf-158">이 설정은 Unity 편집기에서 프로젝트를 테스트 하려는 경우에만 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fecf-158">This setting is only required if you plan to test your project in the Unity editor.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2fecf-159">다음 단계</span><span class="sxs-lookup"><span data-stu-id="2fecf-159">Next steps</span></span>
<span data-ttu-id="2fecf-160">[Unity 공간 오디오 챕터 2](unity-spatial-audio-ch2.md) to spatialize button 인터랙션 소리를 계속 진행 합니다.</span><span class="sxs-lookup"><span data-stu-id="2fecf-160">Continue on to [Unity spatial audio chapter 2](unity-spatial-audio-ch2.md) to spatialize button interaction sounds.</span></span>

