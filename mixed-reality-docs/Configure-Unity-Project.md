---
title: Windows Mixed Reality에 대 한 새 Unity 프로젝트 구성
description: Windows Mixed Reality 용 Unity 프로젝트를 구성 하는 방법에 대 한 지침
author: thetuvix
ms.author: alexturn
ms.date: 04/15/2018
ms.topic: article
keywords: Unity, 혼합 현실, 개발, 시작, 새 프로젝트
ms.openlocfilehash: 64f7006bf212f49ab1c478d5dbb1fc1f5ab15497
ms.sourcegitcommit: 161f3c5a80f6988a9c4af26e29481fee06840e0f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87390107"
---
# <a name="configure-a-new-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="f7457-104">Windows Mixed Reality에 대 한 새 Unity 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="f7457-104">Configure a New Unity project for Windows Mixed Reality</span></span> 

## <a name="overview"></a><span data-ttu-id="f7457-105">개요</span><span class="sxs-lookup"><span data-stu-id="f7457-105">Overview</span></span>

<span data-ttu-id="f7457-106">Windows Mixed Reality (WMR)는 Windows 10 운영 체제의 일부로 도입 된 Microsoft 플랫폼입니다.</span><span class="sxs-lookup"><span data-stu-id="f7457-106">Windows Mixed Reality (WMR) is a Microsoft platform introduced as part of the Windows 10 operating system.</span></span> <span data-ttu-id="f7457-107">WMR 플랫폼을 사용 하면 holographic 및 VR 디스플레이 장치에서 디지털 콘텐츠를 렌더링 하는 응용 프로그램을 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7457-107">The WMR platform lets you build applications that render digital content on holographic and VR display devices.</span></span>

<span data-ttu-id="f7457-108">WMR에 대해 설정할 때 두 가지 경로를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7457-108">When setting up for WMR, there are two paths you can take.</span></span> <span data-ttu-id="f7457-109">첫 번째 옵션은 WMR 환경을 자동으로 설정 하는 mrtk ( [Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) ) v2를 설치 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f7457-109">Your first option is to install the [Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) (MRTK) v2, which will automatically set up the WMR environment.</span></span> <span data-ttu-id="f7457-110">두 번째 옵션은 WMR를 사용 하기 위해 몇 가지 Unity 설정을 수동으로 변경 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f7457-110">The second option is to manually change a few Unity settings to get rolling with WMR.</span></span> 

> [!NOTE]
> <span data-ttu-id="f7457-111">나중에 언제 든 지 MRTK를 가져올 수 있으므로 수동 경로를 먼저 이동 하는 데는 아무런 영향이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f7457-111">You can always import MRTK later on, so there's no penalty for going the manual route first.</span></span>

<span data-ttu-id="f7457-112">WMR 수동 설치를 선택 하는 경우 변경 해야 하는 설정은 프로젝트별 및 장면의 두 가지 범주로 구분 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7457-112">If you choose the WMR manual setup, the settings you need to change are broken-down into two categories: per-project and per-scene.</span></span>

## <a name="per-project-settings"></a><span data-ttu-id="f7457-113">프로젝트별 설정</span><span class="sxs-lookup"><span data-stu-id="f7457-113">Per-project settings</span></span>

<span data-ttu-id="f7457-114">WMR에 대해 변경 해야 하는 첫 번째 설정은 프로젝트 플랫폼입니다.</span><span class="sxs-lookup"><span data-stu-id="f7457-114">The first setting you need to change for WMR is the project platform:</span></span> 
1. <span data-ttu-id="f7457-115">**파일 > 빌드 설정** ...을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7457-115">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="f7457-116">플랫폼 목록에서 **유니버설 Windows 플랫폼** 을 선택 하 고 **플랫폼 전환** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7457-116">Select **Universal Windows Platform** in the Platform list and click **Switch Platform**</span></span>
3. <span data-ttu-id="f7457-117">**SDK** 를 **유니버설 10** 으로 설정</span><span class="sxs-lookup"><span data-stu-id="f7457-117">Set **SDK** to **Universal 10**</span></span>
4. <span data-ttu-id="f7457-118">몰입 형 헤드셋을 지원 하거나 **HoloLens** 로 전환 하기 위해 **대상 장치** 를 **모든 장치로** 설정</span><span class="sxs-lookup"><span data-stu-id="f7457-118">Set **Target device** to **Any Device** to support immersive headsets or switch to **HoloLens**</span></span>
5. <span data-ttu-id="f7457-119">**빌드 유형을** **D3D** 로 설정</span><span class="sxs-lookup"><span data-stu-id="f7457-119">Set **Build Type** to **D3D**</span></span>
6. <span data-ttu-id="f7457-120">**UWP SDK** 를 **최신 설치** 로 설정</span><span class="sxs-lookup"><span data-stu-id="f7457-120">Set **UWP SDK** to **Latest installed**</span></span>

<span data-ttu-id="f7457-121">![Unity XR 설정](images/unity-uwp-settings.png)</span><span class="sxs-lookup"><span data-stu-id="f7457-121">![Unity XR settings](images/unity-uwp-settings.png)</span></span><br>
<span data-ttu-id="f7457-122">*Unity XR 설정*</span><span class="sxs-lookup"><span data-stu-id="f7457-122">*Unity XR settings*</span></span>

<span data-ttu-id="f7457-123">플랫폼이 올바르게 구성 된 후에는 앱이 내보낼 때 2D 보기 대신 [몰입 형 보기](app-views.md) 를 만들어야 한다는 것을 Unity에 알려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7457-123">After the platform is configured correctly, you need to let Unity know that your app should create an [immersive view](app-views.md) instead of a 2D view when exported:</span></span>
1. <span data-ttu-id="f7457-124">**빌드 설정 ...** 창에서 **플레이어 설정 ...** 을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f7457-124">From the **Build Settings...** window, open **Player Settings...**</span></span>
2. <span data-ttu-id="f7457-125">유니버설 Windows 플랫폼 탭 **에 대 한 설정** 을 선택 하 고 **XR 설정** 그룹을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7457-125">Select the **Settings for Universal Windows Platform** tab and expand the **XR Settings** group</span></span>
3. <span data-ttu-id="f7457-126">**XR 설정** 섹션에서 가상 **현실 지원 됨** 확인란을 선택 하 여 **가상 현실 장치** 목록을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7457-126">In the **XR Settings** section, check the **Virtual Reality Supported** checkbox to add the **Virtual Reality Devices** list.</span></span>
4. <span data-ttu-id="f7457-127">**XR 설정** 그룹에서 **"Windows Mixed Reality"** 가 지원 되는 장치로 나열 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7457-127">In the **XR Settings** group, confirm that **"Windows Mixed Reality"** is listed as a supported device.</span></span> <span data-ttu-id="f7457-128">이 옵션은 이전 버전의 Unity에서 **Windows Holographic** 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7457-128">(this option may appear as **Windows Holographic** in older versions of Unity)</span></span>

<span data-ttu-id="f7457-129">![Unity UWP 설정](images/xrsettings.png)</span><span class="sxs-lookup"><span data-stu-id="f7457-129">![Unity UWP settings](images/xrsettings.png)</span></span><br>
<span data-ttu-id="f7457-130">*Unity XR 설정*</span><span class="sxs-lookup"><span data-stu-id="f7457-130">*Unity XR settings*</span></span>

### <a name="updating-the-manifest"></a><span data-ttu-id="f7457-131">매니페스트를 업데이트 하는 중</span><span class="sxs-lookup"><span data-stu-id="f7457-131">Updating the manifest</span></span>

<span data-ttu-id="f7457-132">이제 앱이 holographic 렌더링 및 공간 입력을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7457-132">Your app can now handle holographic rendering and spatial input.</span></span> <span data-ttu-id="f7457-133">그러나 특정 기능을 활용 하려면 앱이 해당 매니페스트에 적절 한 기능을 선언 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7457-133">However, your app needs to declare the appropriate capabilities in its manifest to take advantage of certain functionality.</span></span> <span data-ttu-id="f7457-134">**플레이어 설정 > 설정 유니버설 Windows 플랫폼 > 게시 설정 > 기능**으로 이동 하 여 프로젝트 기능을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7457-134">You can find your projects capabilities by going to **Player Settings > Settings for Universal Windows Platform > Publishing Settings > Capabilities**.</span></span> 

<span data-ttu-id="f7457-135">내보낸 이후 모든 프로젝트에 포함 하기 위해 Unity에서 매니페스트 선언을 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f7457-135">It's recommended that you make the manifest declarations in Unity to include them in all future projects that you export.</span></span> <span data-ttu-id="f7457-136">혼합 현실에 일반적으로 사용 되는 Unity Api를 사용 하는 데 적용 되는 기능은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f7457-136">The applicable capabilities for enabling commonly used Unity APIs for Mixed Reality are:</span></span>

|  <span data-ttu-id="f7457-137">기능</span><span class="sxs-lookup"><span data-stu-id="f7457-137">Capability</span></span>  |  <span data-ttu-id="f7457-138">기능을 필요로 하는 Api</span><span class="sxs-lookup"><span data-stu-id="f7457-138">APIs requiring capability</span></span> | 
|----------|----------|
|  <span data-ttu-id="f7457-139">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="f7457-139">SpatialPerception</span></span>  |  <span data-ttu-id="f7457-140">SurfaceObserver (HoloLens의 [공간 매핑](spatial-mapping.md) 메시에 대 한 액세스) &mdash; *헤드셋의 일반 공간 추적에 필요한 기능이 없습니다* .</span><span class="sxs-lookup"><span data-stu-id="f7457-140">SurfaceObserver (access to [spatial mapping](spatial-mapping.md) meshes on HoloLens)&mdash;*No capability needed for general spatial tracking of the headset*</span></span> | 
|  <span data-ttu-id="f7457-141">웹캠</span><span class="sxs-lookup"><span data-stu-id="f7457-141">WebCam</span></span>  |  <span data-ttu-id="f7457-142">사진 캡처 및 VideoCapture</span><span class="sxs-lookup"><span data-stu-id="f7457-142">PhotoCapture and VideoCapture</span></span> | 
|  <span data-ttu-id="f7457-143">PicturesLibrary/VideosLibrary</span><span class="sxs-lookup"><span data-stu-id="f7457-143">PicturesLibrary / VideosLibrary</span></span>  |  <span data-ttu-id="f7457-144">각각 사진 캡처 또는 VideoCapture (캡처된 콘텐츠를 저장 하는 경우)</span><span class="sxs-lookup"><span data-stu-id="f7457-144">PhotoCapture or VideoCapture, respectively (when storing the captured content)</span></span> | 
|  <span data-ttu-id="f7457-145">마이크</span><span class="sxs-lookup"><span data-stu-id="f7457-145">Microphone</span></span>  |  <span data-ttu-id="f7457-146">VideoCapture (오디오 캡처 시), DictationRecognizer, GrammarRecognizer 및 KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="f7457-146">VideoCapture (when capturing audio), DictationRecognizer, GrammarRecognizer, and KeywordRecognizer</span></span> | 
|  <span data-ttu-id="f7457-147">InternetClient</span><span class="sxs-lookup"><span data-stu-id="f7457-147">InternetClient</span></span>  |  <span data-ttu-id="f7457-148">DictationRecognizer (및 Unity 프로파일러를 사용 하려면)</span><span class="sxs-lookup"><span data-stu-id="f7457-148">DictationRecognizer (and to use the Unity Profiler)</span></span> | 

### <a name="quality-settings"></a><span data-ttu-id="f7457-149">품질 설정</span><span class="sxs-lookup"><span data-stu-id="f7457-149">Quality settings</span></span>

<span data-ttu-id="f7457-150">HoloLens에는 모바일 클래스 GPU가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7457-150">HoloLens has a mobile-class GPU.</span></span> <span data-ttu-id="f7457-151">앱이 HoloLens를 대상으로 하는 경우 앱의 품질 설정이 전체 프레임 속도를 유지 하기 위해 가장 빠른 성능을 위해 조정 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7457-151">If your app is targeting HoloLens, you'll want the quality settings in your app tuned for fastest performance to ensure it maintains full frame-rate:</span></span>
1. <span data-ttu-id="f7457-152">**편집 > 프로젝트 설정 > 품질** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7457-152">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="f7457-153">**Windows 스토어** 로고 아래의 **드롭다운** 을 선택 하 고 **매우 낮음**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7457-153">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="f7457-154">Windows 스토어 열 및 **매우 낮음** 행의 상자가 녹색이면 설정이 올바르게 적용된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f7457-154">You'll know the setting is applied correctly when the box in the Windows Store column and **Very Low** row is green.</span></span>

<span data-ttu-id="f7457-155">![Unity 품질 설정](images/getting-started-unity-quality-settings.jpg)</span><span class="sxs-lookup"><span data-stu-id="f7457-155">![Unity quality settings](images/getting-started-unity-quality-settings.jpg)</span></span><br>
<span data-ttu-id="f7457-156">*Unity 품질 설정*</span><span class="sxs-lookup"><span data-stu-id="f7457-156">*Unity quality settings*</span></span>

## <a name="per-scene-settings"></a><span data-ttu-id="f7457-157">장면 별 설정</span><span class="sxs-lookup"><span data-stu-id="f7457-157">Per-scene settings</span></span>

### <a name="unity-camera-settings"></a><span data-ttu-id="f7457-158">Unity 카메라 설정</span><span class="sxs-lookup"><span data-stu-id="f7457-158">Unity camera settings</span></span>

<span data-ttu-id="f7457-159">**가상 현실을 지원 됨** 을 선택 하면 [Unity 카메라](camera-in-unity.md) 구성 요소가 [헤드 추적 및 stereoscopic 렌더링](rendering.md)을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7457-159">With **Virtual Reality Supported** checked, the [Unity Camera](camera-in-unity.md) component handles [head tracking and stereoscopic rendering](rendering.md).</span></span> <span data-ttu-id="f7457-160">즉, 기본 카메라 개체를 사용자 지정 카메라로 바꿀 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f7457-160">That means there's no need for you to replace the Main Camera object with a custom camera.</span></span>

<span data-ttu-id="f7457-161">앱이 특별히 HoloLens를 대상으로 하는 경우에는 장치의 투명 디스플레이를 최적화 하기 위해 몇 가지 설정을 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7457-161">If your app is targeting HoloLens specifically, you need to change a few settings to optimize for the device's transparent displays.</span></span> <span data-ttu-id="f7457-162">이러한 설정을 통해 holographic 콘텐츠를 실제 세계에 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7457-162">These settings allow your holographic content to show through to the physical world:</span></span>
1. <span data-ttu-id="f7457-163">**계층**에서 **기본 카메라** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7457-163">In the **Hierarchy**, select the **Main Camera**</span></span>
2. <span data-ttu-id="f7457-164">**검사기** 패널에서 변환 **위치** 를 **0, 0, 0** 으로 설정 하 여 사용자의 헤드 위치가 Unity 세계 원점에서 시작 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7457-164">In the **Inspector** panel, set the transform **position** to **0, 0, 0** so the location of the user's head starts at the Unity world origin.</span></span>
3. <span data-ttu-id="f7457-165">**Clear 플래그** 를 **Solid 색**으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7457-165">Change **Clear Flags** to **Solid Color**.</span></span>
4. <span data-ttu-id="f7457-166">**배경색** 을 **RGBA 0, 0**, 0, 0으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7457-166">Change the **Background** color to **RGBA 0,0,0,0**.</span></span> <span data-ttu-id="f7457-167">검은색은 HoloLens에서 투명 하 게 렌더링 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7457-167">Black renders as transparent in HoloLens.</span></span>
5. <span data-ttu-id="f7457-168">**클립 평면** 을 [HoloLens 권장](camera-in-unity.md#clip-planes) 0.85 (미터) 근처로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7457-168">Change **Clipping Planes - Near** to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 (meters).</span></span>

<span data-ttu-id="f7457-169">![Unity 카메라 설정](images/Unitycamerasettings.png)</span><span class="sxs-lookup"><span data-stu-id="f7457-169">![Unity camera settings](images/Unitycamerasettings.png)</span></span><br>
<span data-ttu-id="f7457-170">*Unity 카메라 설정*</span><span class="sxs-lookup"><span data-stu-id="f7457-170">*Unity camera settings*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f7457-171">새 카메라를 삭제 하 고 만드는 경우 새 카메라에 **maincamera**로 태그가 지정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7457-171">If you delete and create a new camera, make sure your new camera is tagged as **MainCamera**.</span></span>

## <a name="see-also"></a><span data-ttu-id="f7457-172">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f7457-172">See also</span></span>
* [<span data-ttu-id="f7457-173">Mixed Reality Toolkit v2</span><span class="sxs-lookup"><span data-stu-id="f7457-173">Mixed Reality Toolkit v2</span></span>](mrtk-getting-started.md)
* [<span data-ttu-id="f7457-174">Unity 개발 개요</span><span class="sxs-lookup"><span data-stu-id="f7457-174">Unity Development Overview</span></span>](unity-development-overview.md)
