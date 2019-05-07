---
title: Windows Mixed Reality 용 새 Unity 프로젝트 구성
description: MRTK 없이 Unity 프로젝트를 구성 합니다.
author: yoyoz
ms.author: Yoyoz
ms.date: 04/15/2018
ms.topic: article
keywords: Unity, 혼합 현실, 개발, 시작, 새 프로젝트
ms.openlocfilehash: 4ee81eca25109da428d7b3addf59e102ddc5c5cf
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993535"
---
# <a name="configure-a-new-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="270ce-104">Windows Mixed Reality 용 새 Unity 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="270ce-104">Configure a New Unity Project for Windows Mixed Reality</span></span> 

<span data-ttu-id="270ce-105">(MRTK v2 Unity 프로젝트에 이미 가져온 경우 건너뜀)</span><span class="sxs-lookup"><span data-stu-id="270ce-105">(skip if you have already imported MRTK v2 into your Unity Project)</span></span>

<span data-ttu-id="270ce-106">혼합 현실 도구 키트를 가져오지 않고 새 Unity 프로젝트를 생성 하려는 경우 소규모의 두 범주로 구분 하는 Windows Mixed Reality를 수동으로 변경 해야 하는 Unity 설정 가지: 프로젝트별와 장면 당 합니다.</span><span class="sxs-lookup"><span data-stu-id="270ce-106">If you'd like to created a new Unity project without importing Mixed Reality Toolkit, there are a small set of Unity settings you'll need to manually change for Windows Mixed Reality, broken down into two categories: per-project and per-scene.</span></span>

## <a name="per-project-settings"></a><span data-ttu-id="270ce-107">프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="270ce-107">Per-project settings</span></span>

<span data-ttu-id="270ce-108">Windows Mixed Reality를 대상으로 먼저 유니버설 Windows 플랫폼 앱으로 내보내려면 Unity 프로젝트를 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="270ce-108">To target Windows Mixed Reality, you first need to set your Unity project to export as a Universal Windows Platform app:</span></span>
1. <span data-ttu-id="270ce-109">선택 **파일 > 빌드 설정...**</span><span class="sxs-lookup"><span data-stu-id="270ce-109">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="270ce-110">선택 **유니버설 Windows 플랫폼** 플랫폼에서 나열 하 고 클릭 **플랫폼 전환**</span><span class="sxs-lookup"><span data-stu-id="270ce-110">Select **Universal Windows Platform** in the Platform list and click **Switch Platform**</span></span>
3. <span data-ttu-id="270ce-111">설정할 **SDK** 에 **유니버설 10**</span><span class="sxs-lookup"><span data-stu-id="270ce-111">Set **SDK** to **Universal 10**</span></span>
4. <span data-ttu-id="270ce-112">설정할 **대상 장치** 하 **모든 장치** 전환할 또는 몰입 형 헤드셋을 지원 하도록 **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="270ce-112">Set **Target device** to **Any Device** to support immersive headsets or switch to **HoloLens**</span></span>
5. <span data-ttu-id="270ce-113">설정할 **빌드 형식** 에 **D3D**</span><span class="sxs-lookup"><span data-stu-id="270ce-113">Set **Build Type** to **D3D**</span></span>
6. <span data-ttu-id="270ce-114">설정할 **UWP SDK** 에 **가장 최근에 설치 된**</span><span class="sxs-lookup"><span data-stu-id="270ce-114">Set **UWP SDK** to **Latest installed**</span></span>

<span data-ttu-id="270ce-115">Unity 내보내기 하려는 앱을 만들어야 알 수 있도록 해야 합니다는 [몰입 형 뷰](app-views.md) 2D 보기 대신 합니다.</span><span class="sxs-lookup"><span data-stu-id="270ce-115">We then need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="270ce-116">"가상 현실 지원"을 사용 하도록 설정 하면 여는 작업을 수행:</span><span class="sxs-lookup"><span data-stu-id="270ce-116">We do that by enabling "Virtual Reality Supported":</span></span>
1. <span data-ttu-id="270ce-117">**빌드 설정...**  창을 열려면 **플레이어 설정...**</span><span class="sxs-lookup"><span data-stu-id="270ce-117">From the **Build Settings...** window, open **Player Settings...**</span></span>
2. <span data-ttu-id="270ce-118">선택 된 **유니버설 Windows 플랫폼에 대 한 설정을** 탭</span><span class="sxs-lookup"><span data-stu-id="270ce-118">Select the **Settings for Universal Windows Platform** tab</span></span>
3. <span data-ttu-id="270ce-119">확장 된 **xr 하이 설정을** 그룹</span><span class="sxs-lookup"><span data-stu-id="270ce-119">Expand the **XR Settings** group</span></span>
4. <span data-ttu-id="270ce-120">에 **xr 하이 설정** 섹션을 **가상 현실 지원** 추가 확인란을를 **가상 현실 장치용** 목록.</span><span class="sxs-lookup"><span data-stu-id="270ce-120">In the **XR Settings** section, check the **Virtual Reality Supported** checkbox to add the **Virtual Reality Devices** list.</span></span>
5. <span data-ttu-id="270ce-121">에 **xr 하이 설정을** 그룹에서 확인 **"Windows Mixed Reality"** 지원 되는 장치로 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="270ce-121">In the **XR Settings** group, confirm that **"Windows Mixed Reality"** is listed as a supported device.</span></span> <span data-ttu-id="270ce-122">(이 나타날 수 있습니다 "Windows Holographic"으로 Unity의 이전 버전)</span><span class="sxs-lookup"><span data-stu-id="270ce-122">(this may appear as "Windows Holographic" in older versions of Unity)</span></span>

<span data-ttu-id="270ce-123">기본 holographic 렌더링 및 공간 입력에 이제 앱이 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="270ce-123">Your app can now do basic holographic rendering and spatial input.</span></span> <span data-ttu-id="270ce-124">진행 하 고 특정 기능을 활용 하려면 앱 매니페스트에서 적절 한 기능을 선언 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="270ce-124">To go further and take advantage of certain functionality, your app must declare the appropriate capabilities in its manifest.</span></span> <span data-ttu-id="270ce-125">매니페스트 선언 되므로 모든 후속 프로젝트 내보내기에 포함 된 Unity에서 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="270ce-125">The manifest declarations can be made in Unity so they are included in every subsequent project export.</span></span> <span data-ttu-id="270ce-126">설정에 포함 됩니다 **플레이어 설정 > 유니버설 Windows 플랫폼에 대 한 설정 > 게시 설정 > 기능**합니다.</span><span class="sxs-lookup"><span data-stu-id="270ce-126">The setting are found in **Player Settings > Settings for Universal Windows Platform > Publishing Settings > Capabilities**.</span></span> <span data-ttu-id="270ce-127">혼합 현실에 대 한 일반적으로 사용 되는 Unity Api를 사용 하도록 설정 하는 것에 대 한 해당 기능은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="270ce-127">The applicable capabilities for enabling commonly-used Unity APIs for Mixed Reality are:</span></span>

|  <span data-ttu-id="270ce-128">기능</span><span class="sxs-lookup"><span data-stu-id="270ce-128">Capability</span></span>  |  <span data-ttu-id="270ce-129">기능을 요구 하는 Api</span><span class="sxs-lookup"><span data-stu-id="270ce-129">APIs requiring capability</span></span> | 
|----------|----------|
|  <span data-ttu-id="270ce-130">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="270ce-130">SpatialPerception</span></span>  |  <span data-ttu-id="270ce-131">SurfaceObserver (에 대 한 액세스 [공간 매핑](spatial-mapping.md) HoloLens에 메시)&mdash;*헤드셋의 일반 공간 추적에 필요한 기능이 없습니다*</span><span class="sxs-lookup"><span data-stu-id="270ce-131">SurfaceObserver (access to [spatial mapping](spatial-mapping.md) meshes on HoloLens)&mdash;*No capability needed for general spatial tracking of the headset*</span></span> | 
|  <span data-ttu-id="270ce-132">웹캠</span><span class="sxs-lookup"><span data-stu-id="270ce-132">WebCam</span></span>  |  <span data-ttu-id="270ce-133">PhotoCapture 및 VideoCapture</span><span class="sxs-lookup"><span data-stu-id="270ce-133">PhotoCapture and VideoCapture</span></span> | 
|  <span data-ttu-id="270ce-134">PicturesLibrary / VideosLibrary</span><span class="sxs-lookup"><span data-stu-id="270ce-134">PicturesLibrary / VideosLibrary</span></span>  |  <span data-ttu-id="270ce-135">PhotoCapture 또는 VideoCapture, 각각 (저장할 때 캡처된 콘텐츠)</span><span class="sxs-lookup"><span data-stu-id="270ce-135">PhotoCapture or VideoCapture, respectively (when storing the captured content)</span></span> | 
|  <span data-ttu-id="270ce-136">Microphone</span><span class="sxs-lookup"><span data-stu-id="270ce-136">Microphone</span></span>  |  <span data-ttu-id="270ce-137">VideoCapture (오디오 캡처) 하는 경우, DictationRecognizer, GrammarRecognizer, 및 KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="270ce-137">VideoCapture (when capturing audio), DictationRecognizer, GrammarRecognizer, and KeywordRecognizer</span></span> | 
|  <span data-ttu-id="270ce-138">InternetClient</span><span class="sxs-lookup"><span data-stu-id="270ce-138">InternetClient</span></span>  |  <span data-ttu-id="270ce-139">DictationRecognizer (및 Unity Profiler 사용)</span><span class="sxs-lookup"><span data-stu-id="270ce-139">DictationRecognizer (and to use the Unity Profiler)</span></span> | 

<span data-ttu-id="270ce-140">**Unity 품질 설정**</span><span class="sxs-lookup"><span data-stu-id="270ce-140">**Unity quality settings**</span></span>

<span data-ttu-id="270ce-141">![Unity 품질 설정](images/unityqualitysettings-350px.png)</span><span class="sxs-lookup"><span data-stu-id="270ce-141">![Unity quality settings](images/unityqualitysettings-350px.png)</span></span><br>
<span data-ttu-id="270ce-142">*Unity 품질 설정*</span><span class="sxs-lookup"><span data-stu-id="270ce-142">*Unity quality settings*</span></span>

<span data-ttu-id="270ce-143">HoloLens는 mobile 클래스 GPU에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="270ce-143">HoloLens has a mobile-class GPU.</span></span> <span data-ttu-id="270ce-144">앱은 HoloLens를 대상으로 하는 경우 전체 프레임 속도 유지 하 고 확인 하려면 품질 설정을 가장 빠른 성능을 위해 조정 해야:</span><span class="sxs-lookup"><span data-stu-id="270ce-144">If your app is targeting HoloLens, you'll want the quality settings tuned for fastest performance to ensure we maintain full framerate:</span></span>
1. <span data-ttu-id="270ce-145">선택 **편집 > 프로젝트 설정 > 품질**</span><span class="sxs-lookup"><span data-stu-id="270ce-145">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="270ce-146">선택 합니다 **드롭다운** 아래를 **Windows 스토어** 로고 및 선택 **매우 낮음**합니다.</span><span class="sxs-lookup"><span data-stu-id="270ce-146">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="270ce-147">설정을 때 적용 되 올바르게 알 수 있습니다 Windows Store 열에 있는 상자 및 **매우 낮음** 행은 녹색입니다.</span><span class="sxs-lookup"><span data-stu-id="270ce-147">You'll know the setting is applied correctly when the box in the Windows Store column and **Very Low** row is green.</span></span>

## <a name="per-scene-settings"></a><span data-ttu-id="270ce-148">장면 당 설정</span><span class="sxs-lookup"><span data-stu-id="270ce-148">Per-scene settings</span></span>

<span data-ttu-id="270ce-149">**Unity 카메라 설정**</span><span class="sxs-lookup"><span data-stu-id="270ce-149">**Unity camera settings**</span></span>

<span data-ttu-id="270ce-150">![Unity 카메라 설정](images/Unitycamerasettings.png)</span><span class="sxs-lookup"><span data-stu-id="270ce-150">![Unity camera settings](images/Unitycamerasettings.png)</span></span><br>
<span data-ttu-id="270ce-151">*Unity 카메라 설정*</span><span class="sxs-lookup"><span data-stu-id="270ce-151">*Unity camera settings*</span></span>

<span data-ttu-id="270ce-152">"가상 현실 지원" 확인란을 사용 하도록 설정 하면 합니다 [Unity 카메라](camera-in-unity.md) 구성 요소 핸들 [추적과 stereoscopic 렌더링 헤드](rendering.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="270ce-152">Once you enable the "Virtual Reality Supported" checkbox, the [Unity Camera](camera-in-unity.md) component handles [head tracking and stereoscopic rendering](rendering.md).</span></span> <span data-ttu-id="270ce-153">이렇게 하려면 사용자 지정 카메라를 사용 하 여 바꾸려면 않아도가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="270ce-153">There is no need to replace it with a custom camera to do this.</span></span>

<span data-ttu-id="270ce-154">앱 HoloLens 특히 대상이 되는 경우 가지 실제 세계를 통해 앱에 표시 됩니다 있도록 투명 한 디스플레이 장치에 대 한 최적화 하도록 변경 해야 하는 몇 가지 설정이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="270ce-154">If your app is targeting HoloLens specifically, there are a few settings that need to be changed to optimize for the device's transparent displays, so your app will show through to the physical world:</span></span>
1. <span data-ttu-id="270ce-155">에 **계층 구조**를 선택 합니다 **주 카메라**</span><span class="sxs-lookup"><span data-stu-id="270ce-155">In the **Hierarchy**, select the **Main Camera**</span></span>
2. <span data-ttu-id="270ce-156">에 **검사기** 패널에서 변환을 설정 **위치** 하 **0, 0, 0** Unity world 원점에서 시작 되는 사용자가 헤드의 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="270ce-156">In the **Inspector** panel, set the transform **position** to **0, 0, 0** so the location of the users head starts at the Unity world origin.</span></span>
3. <span data-ttu-id="270ce-157">변경 **플래그 지우기** 하 **단색**합니다.</span><span class="sxs-lookup"><span data-stu-id="270ce-157">Change **Clear Flags** to **Solid Color**.</span></span>
4. <span data-ttu-id="270ce-158">변경 된 **백그라운드** 색 **RGBA 0,0,0,0**합니다.</span><span class="sxs-lookup"><span data-stu-id="270ce-158">Change the **Background** color to **RGBA 0,0,0,0**.</span></span> <span data-ttu-id="270ce-159">검정은 HoloLens에 투명 하 게 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="270ce-159">Black renders as transparent in HoloLens.</span></span>
5. <span data-ttu-id="270ce-160">변경 **가까운 평면-클리핑** 에 [HoloLens 권장](camera-in-unity.md#clip-planes) 0.85 (미터)입니다.</span><span class="sxs-lookup"><span data-stu-id="270ce-160">Change **Clipping Planes - Near** to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 (meters).</span></span>

<span data-ttu-id="270ce-161">새 카메라를 만들고 삭제 하는 경우 반드시 카메라 **태그가 지정 된** 으로 **MainCamera**합니다.</span><span class="sxs-lookup"><span data-stu-id="270ce-161">If you delete and create a new camera, make sure your camera is **Tagged** as **MainCamera**.</span></span>


## <a name="see-also"></a><span data-ttu-id="270ce-162">참조</span><span class="sxs-lookup"><span data-stu-id="270ce-162">See also</span></span>
* [<span data-ttu-id="270ce-163">혼합 현실을 Toolkit v2</span><span class="sxs-lookup"><span data-stu-id="270ce-163">Mixed Reality Toolkit v2</span></span>](mrtk-getting-started.md)
* [<span data-ttu-id="270ce-164">Unity 개발 개요</span><span class="sxs-lookup"><span data-stu-id="270ce-164">Unity Development Overview</span></span>](unity-development-overview.md)
