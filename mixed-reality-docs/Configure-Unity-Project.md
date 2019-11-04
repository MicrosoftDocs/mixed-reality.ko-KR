---
title: Windows Mixed Reality에 대 한 새 Unity 프로젝트 구성
description: MRTK 없이 Unity 프로젝트 구성
author: thetuvix
ms.author: alexturn
ms.date: 04/15/2018
ms.topic: article
keywords: Unity, 혼합 현실, 개발, 시작, 새 프로젝트
ms.openlocfilehash: af30cf91eda1b654bea6048c34f63c61238626c7
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437118"
---
# <a name="configure-a-new-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="1ec1b-104">Windows Mixed Reality에 대 한 새 Unity 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="1ec1b-104">Configure a New Unity Project for Windows Mixed Reality</span></span> 

<span data-ttu-id="1ec1b-105">(MRTK v 2를 Unity 프로젝트로 이미 가져온 경우에는 건너뜀)</span><span class="sxs-lookup"><span data-stu-id="1ec1b-105">(skip if you have already imported MRTK v2 into your Unity Project)</span></span>

<span data-ttu-id="1ec1b-106">Mixed Reality 도구 키트를 가져오지 않고 새 Unity 프로젝트를 만들려는 경우에는 Windows Mixed Reality에 대해 수동으로 변경 해야 하는 몇 가지 Unity 설정, 즉 프로젝트별 및 장면의 두 가지 범주로 분류 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ec1b-106">If you'd like to created a new Unity project without importing Mixed Reality Toolkit, there are a small set of Unity settings you'll need to manually change for Windows Mixed Reality, broken down into two categories: per-project and per-scene.</span></span>

## <a name="per-project-settings"></a><span data-ttu-id="1ec1b-107">프로젝트별 설정</span><span class="sxs-lookup"><span data-stu-id="1ec1b-107">Per-project settings</span></span>

<span data-ttu-id="1ec1b-108">Windows Mixed Reality를 대상으로 하려면 먼저 유니버설 Windows 플랫폼 앱으로 내보내도록 Unity 프로젝트를 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ec1b-108">To target Windows Mixed Reality, you first need to set your Unity project to export as a Universal Windows Platform app:</span></span> 
1. <span data-ttu-id="1ec1b-109">**파일 > 빌드 설정** ...을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ec1b-109">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="1ec1b-110">플랫폼 목록에서 **유니버설 Windows 플랫폼** 을 선택 하 고 **플랫폼 전환** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ec1b-110">Select **Universal Windows Platform** in the Platform list and click **Switch Platform**</span></span>
3. <span data-ttu-id="1ec1b-111">**SDK** 를 **유니버설 10** 으로 설정</span><span class="sxs-lookup"><span data-stu-id="1ec1b-111">Set **SDK** to **Universal 10**</span></span>
4. <span data-ttu-id="1ec1b-112">몰입 형 헤드셋을 지원 하거나 **HoloLens** 로 전환 하기 위해 **대상 장치** 를 **모든 장치로** 설정</span><span class="sxs-lookup"><span data-stu-id="1ec1b-112">Set **Target device** to **Any Device** to support immersive headsets or switch to **HoloLens**</span></span>
5. <span data-ttu-id="1ec1b-113">**빌드 유형을** **D3D** 로 설정</span><span class="sxs-lookup"><span data-stu-id="1ec1b-113">Set **Build Type** to **D3D**</span></span>
6. <span data-ttu-id="1ec1b-114">**UWP SDK** 를 **최신 설치** 로 설정</span><span class="sxs-lookup"><span data-stu-id="1ec1b-114">Set **UWP SDK** to **Latest installed**</span></span>

<span data-ttu-id="1ec1b-115">그런 다음 내보내려는 앱이 2D 보기 대신 [몰입 형 보기](app-views.md) 를 만들어야 한다고 Unity에 알려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ec1b-115">We then need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="1ec1b-116">"가상 현실 지원"을 사용 하도록 설정 하 여이 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ec1b-116">We do that by enabling "Virtual Reality Supported":</span></span>
1. <span data-ttu-id="1ec1b-117">**빌드 설정 ...** 창에서 **플레이어 설정 ...** 을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1ec1b-117">From the **Build Settings...** window, open **Player Settings...**</span></span>
2. <span data-ttu-id="1ec1b-118">유니버설 Windows 플랫폼 탭 **에 대 한 설정** 선택</span><span class="sxs-lookup"><span data-stu-id="1ec1b-118">Select the **Settings for Universal Windows Platform** tab</span></span>
3. <span data-ttu-id="1ec1b-119">**XR 설정** 그룹을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ec1b-119">Expand the **XR Settings** group</span></span>
4. <span data-ttu-id="1ec1b-120">**XR 설정** 섹션에서 가상 **현실 지원 됨** 확인란을 선택 하 여 **가상 현실 장치** 목록을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ec1b-120">In the **XR Settings** section, check the **Virtual Reality Supported** checkbox to add the **Virtual Reality Devices** list.</span></span>
5. <span data-ttu-id="1ec1b-121">**XR 설정** 그룹에서 **"Windows Mixed Reality"** 가 지원 되는 장치로 나열 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ec1b-121">In the **XR Settings** group, confirm that **"Windows Mixed Reality"** is listed as a supported device.</span></span> <span data-ttu-id="1ec1b-122">(이전 버전의 Unity에서 "Windows Holographic"로 표시 될 수 있음)</span><span class="sxs-lookup"><span data-stu-id="1ec1b-122">(this may appear as "Windows Holographic" in older versions of Unity)</span></span>

<span data-ttu-id="1ec1b-123">Unity 품질 설정 ![](images/getting-started-unity-quality-settings.jpg)</span><span class="sxs-lookup"><span data-stu-id="1ec1b-123">![Unity quality settings](images/getting-started-unity-quality-settings.jpg)</span></span><br>
<span data-ttu-id="1ec1b-124">*Unity xr 설정*</span><span class="sxs-lookup"><span data-stu-id="1ec1b-124">*Unity xr settings*</span></span>

<span data-ttu-id="1ec1b-125">이제 앱에서 기본 holographic 렌더링 및 공간 입력을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ec1b-125">Your app can now do basic holographic rendering and spatial input.</span></span> <span data-ttu-id="1ec1b-126">특정 기능을 사용 하려면 앱이 해당 매니페스트에 적절 한 기능을 선언 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ec1b-126">To go further and take advantage of certain functionality, your app must declare the appropriate capabilities in its manifest.</span></span> <span data-ttu-id="1ec1b-127">매니페스트 선언은 Unity에서 수행할 수 있으므로 이후의 모든 프로젝트 내보내기에 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ec1b-127">The manifest declarations can be made in Unity so they are included in every subsequent project export.</span></span> <span data-ttu-id="1ec1b-128">설정은 **플레이어 설정 > 유니버설 Windows 플랫폼 > 게시 설정 > 기능에 대 한 설정**에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ec1b-128">The setting are found in **Player Settings > Settings for Universal Windows Platform > Publishing Settings > Capabilities**.</span></span> <span data-ttu-id="1ec1b-129">혼합 현실에 일반적으로 사용 되는 Unity Api를 사용 하도록 설정 하는 데 적용 되는 기능은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1ec1b-129">The applicable capabilities for enabling commonly-used Unity APIs for Mixed Reality are:</span></span>

|  <span data-ttu-id="1ec1b-130">접근 권한 값</span><span class="sxs-lookup"><span data-stu-id="1ec1b-130">Capability</span></span>  |  <span data-ttu-id="1ec1b-131">기능을 필요로 하는 Api</span><span class="sxs-lookup"><span data-stu-id="1ec1b-131">APIs requiring capability</span></span> | 
|----------|----------|
|  <span data-ttu-id="1ec1b-132">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="1ec1b-132">SpatialPerception</span></span>  |  <span data-ttu-id="1ec1b-133">SurfaceObserver (HoloLens의 [공간 매핑](spatial-mapping.md) 메시에 대 한 액세스)&mdash;*헤드셋의 일반 공간 추적에 필요한 기능이 없습니다* .</span><span class="sxs-lookup"><span data-stu-id="1ec1b-133">SurfaceObserver (access to [spatial mapping](spatial-mapping.md) meshes on HoloLens)&mdash;*No capability needed for general spatial tracking of the headset*</span></span> | 
|  <span data-ttu-id="1ec1b-134">웹캠</span><span class="sxs-lookup"><span data-stu-id="1ec1b-134">WebCam</span></span>  |  <span data-ttu-id="1ec1b-135">사진 캡처 및 VideoCapture</span><span class="sxs-lookup"><span data-stu-id="1ec1b-135">PhotoCapture and VideoCapture</span></span> | 
|  <span data-ttu-id="1ec1b-136">PicturesLibrary/VideosLibrary</span><span class="sxs-lookup"><span data-stu-id="1ec1b-136">PicturesLibrary / VideosLibrary</span></span>  |  <span data-ttu-id="1ec1b-137">각각 사진 캡처 또는 VideoCapture (캡처된 콘텐츠를 저장 하는 경우)</span><span class="sxs-lookup"><span data-stu-id="1ec1b-137">PhotoCapture or VideoCapture, respectively (when storing the captured content)</span></span> | 
|  <span data-ttu-id="1ec1b-138">Microphone</span><span class="sxs-lookup"><span data-stu-id="1ec1b-138">Microphone</span></span>  |  <span data-ttu-id="1ec1b-139">VideoCapture (오디오 캡처 시), DictationRecognizer, GrammarRecognizer 및 KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="1ec1b-139">VideoCapture (when capturing audio), DictationRecognizer, GrammarRecognizer, and KeywordRecognizer</span></span> | 
|  <span data-ttu-id="1ec1b-140">InternetClient</span><span class="sxs-lookup"><span data-stu-id="1ec1b-140">InternetClient</span></span>  |  <span data-ttu-id="1ec1b-141">DictationRecognizer (및 Unity 프로파일러를 사용 하려면)</span><span class="sxs-lookup"><span data-stu-id="1ec1b-141">DictationRecognizer (and to use the Unity Profiler)</span></span> | 

<span data-ttu-id="1ec1b-142">**Unity 품질 설정**</span><span class="sxs-lookup"><span data-stu-id="1ec1b-142">**Unity quality settings**</span></span>

<span data-ttu-id="1ec1b-143">Unity 품질 설정 ![](images/getting-started-unity-quality-settings.jpg)</span><span class="sxs-lookup"><span data-stu-id="1ec1b-143">![Unity quality settings](images/getting-started-unity-quality-settings.jpg)</span></span><br>
<span data-ttu-id="1ec1b-144">*Unity 품질 설정*</span><span class="sxs-lookup"><span data-stu-id="1ec1b-144">*Unity quality settings*</span></span>

<span data-ttu-id="1ec1b-145">HoloLens에는 모바일 클래스 GPU가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ec1b-145">HoloLens has a mobile-class GPU.</span></span> <span data-ttu-id="1ec1b-146">앱이 HoloLens를 대상으로 하는 경우 최고 성능을 위해 품질 설정을 조정 하 여 전체 프레임 속도를 유지 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ec1b-146">If your app is targeting HoloLens, you'll want the quality settings tuned for fastest performance to ensure we maintain full framerate:</span></span>
1. <span data-ttu-id="1ec1b-147">**편집 > 프로젝트 설정 > 품질** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ec1b-147">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="1ec1b-148">**Windows 스토어** 로고 아래의 **드롭다운** 을 선택 하 고 **매우 낮음**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ec1b-148">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="1ec1b-149">Windows 스토어 열의 상자와 **매우 낮은** 행이 녹색 인 경우 설정이 올바르게 적용 됨을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ec1b-149">You'll know the setting is applied correctly when the box in the Windows Store column and **Very Low** row is green.</span></span>

## <a name="per-scene-settings"></a><span data-ttu-id="1ec1b-150">장면 별 설정</span><span class="sxs-lookup"><span data-stu-id="1ec1b-150">Per-scene settings</span></span>

<span data-ttu-id="1ec1b-151">**Unity 카메라 설정**</span><span class="sxs-lookup"><span data-stu-id="1ec1b-151">**Unity camera settings**</span></span>

<span data-ttu-id="1ec1b-152">![Unity 카메라 설정](images/Unitycamerasettings.png)</span><span class="sxs-lookup"><span data-stu-id="1ec1b-152">![Unity camera settings](images/Unitycamerasettings.png)</span></span><br>
<span data-ttu-id="1ec1b-153">*Unity 카메라 설정*</span><span class="sxs-lookup"><span data-stu-id="1ec1b-153">*Unity camera settings*</span></span>

<span data-ttu-id="1ec1b-154">"가상 현실 지원" 확인란을 사용 하도록 설정 하면 [Unity 카메라](camera-in-unity.md) 구성 요소가 [헤드 추적 및 stereoscopic 렌더링](rendering.md)을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ec1b-154">Once you enable the "Virtual Reality Supported" checkbox, the [Unity Camera](camera-in-unity.md) component handles [head tracking and stereoscopic rendering](rendering.md).</span></span> <span data-ttu-id="1ec1b-155">이 작업을 수행 하기 위해 사용자 지정 카메라로 바꿀 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1ec1b-155">There is no need to replace it with a custom camera to do this.</span></span>

<span data-ttu-id="1ec1b-156">앱이 특별히 HoloLens를 대상으로 하는 경우 장치의 투명 디스플레이를 최적화 하기 위해 변경 해야 하는 몇 가지 설정이 있습니다. 따라서 앱은 실제 세계에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ec1b-156">If your app is targeting HoloLens specifically, there are a few settings that need to be changed to optimize for the device's transparent displays, so your app will show through to the physical world:</span></span>
1. <span data-ttu-id="1ec1b-157">**계층**에서 **기본 카메라** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ec1b-157">In the **Hierarchy**, select the **Main Camera**</span></span>
2. <span data-ttu-id="1ec1b-158">**검사기** 패널에서 transform **위치** 를 **0, 0, 0** 으로 설정 하 여 사용자 헤드의 위치가 Unity 세계 원점에서 시작 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ec1b-158">In the **Inspector** panel, set the transform **position** to **0, 0, 0** so the location of the users head starts at the Unity world origin.</span></span>
3. <span data-ttu-id="1ec1b-159">**Clear 플래그** 를 **Solid 색**으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ec1b-159">Change **Clear Flags** to **Solid Color**.</span></span>
4. <span data-ttu-id="1ec1b-160">**배경색** 을 **RGBA 0, 0**, 0, 0으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ec1b-160">Change the **Background** color to **RGBA 0,0,0,0**.</span></span> <span data-ttu-id="1ec1b-161">검은색은 HoloLens에서 투명 하 게 렌더링 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ec1b-161">Black renders as transparent in HoloLens.</span></span>
5. <span data-ttu-id="1ec1b-162">**클립 평면** 을 [HoloLens 권장](camera-in-unity.md#clip-planes) 0.85 (미터) 근처로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ec1b-162">Change **Clipping Planes - Near** to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 (meters).</span></span>

<span data-ttu-id="1ec1b-163">새 카메라를 삭제 하 고 만드는 경우 카메라에 **maincamera**로 **태그가 지정** 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ec1b-163">If you delete and create a new camera, make sure your camera is **Tagged** as **MainCamera**.</span></span>


## <a name="see-also"></a><span data-ttu-id="1ec1b-164">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1ec1b-164">See also</span></span>
* [<span data-ttu-id="1ec1b-165">Mixed Reality Toolkit v2</span><span class="sxs-lookup"><span data-stu-id="1ec1b-165">Mixed Reality Toolkit v2</span></span>](mrtk-getting-started.md)
* [<span data-ttu-id="1ec1b-166">Unity 개발 개요</span><span class="sxs-lookup"><span data-stu-id="1ec1b-166">Unity Development Overview</span></span>](unity-development-overview.md)
