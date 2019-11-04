---
title: Unity의 카메라
description: Windows Mixed Reality 개발용 Unity의 기본 카메라를 사용 하 여 holographic 렌더링을 수행 하는 방법
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit, holographic 렌더링, holographic, 몰입 형, 포커스 지점, 깊이 버퍼, 방향 전용, 위치, 불투명, 투명, 클립
ms.openlocfilehash: 1a2e66d5c028109a58ea8682668521f50158add9
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436953"
---
# <a name="camera-in-unity"></a><span data-ttu-id="ac62f-104">Unity의 카메라</span><span class="sxs-lookup"><span data-stu-id="ac62f-104">Camera in Unity</span></span>

<span data-ttu-id="ac62f-105">혼합 현실 헤드셋을 착용 하면 holographic 세계의 중심이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-105">When you wear a mixed reality headset, it becomes the center of your holographic world.</span></span> <span data-ttu-id="ac62f-106">Unity [카메라](https://docs.unity3d.com/Manual/class-Camera.html) 구성 요소는 stereoscopic 렌더링을 자동으로 처리 하며, 프로젝트에 "Windows Mixed reality"가 "Windows Mixed reality"로 선택 된 "가상 현실 지원"이 있는 경우에는 다른 설정 Windows 스토어 플레이어 설정의 섹션</span><span class="sxs-lookup"><span data-stu-id="ac62f-106">The Unity [Camera](https://docs.unity3d.com/Manual/class-Camera.html) component will automatically handle stereoscopic rendering and will follow your head movement and rotation when your project has "Virtual Reality Supported" selected with "Windows Mixed Reality" as the device (in the Other Settings section of the Windows Store Player Settings).</span></span> <span data-ttu-id="ac62f-107">이전 버전의 Unity에서 "Windows Holographic"로 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-107">This may be listed as "Windows Holographic" in older versions of Unity.</span></span>

<span data-ttu-id="ac62f-108">그러나 시각적 품질 및 [홀로그램 안정성](hologram-stability.md)을 완벽 하 게 최적화 하려면 아래에서 설명 하는 카메라 설정을 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-108">However, to fully optimize visual quality and [hologram stability](hologram-stability.md), you should set the camera settings described below.</span></span>

>[!NOTE]
><span data-ttu-id="ac62f-109">이러한 설정은 앱의 각 장면에서 카메라에 적용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-109">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="ac62f-110">기본적으로 Unity에서 새 장면을 만들 때 카메라 구성 요소를 포함 하는 계층의 기본 카메라 GameObject가 포함 되지만, 아래에는 설정이 제대로 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-110">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but does not have the settings below properly applied.</span></span>

## <a name="automatic-scene-and-camera-setup-with-mixed-reality-toolkit-v2"></a><span data-ttu-id="ac62f-111">혼합 현실 도구 키트 v2를 사용 하 여 자동 장면 및 카메라 설정</span><span class="sxs-lookup"><span data-stu-id="ac62f-111">Automatic Scene and Camera Setup with Mixed Reality Toolkit v2</span></span>

<span data-ttu-id="ac62f-112">[단계별 가이드에](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) 따라 Unity 프로젝트에 Mixed Reality Toolkit v 2를 추가 하면 프로젝트가 자동으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-112">Follow the [step-by-step](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) guide to add Mixed Reality Toolkit v2 to your Unity project and it will configure your project automatically.</span></span>

<span data-ttu-id="ac62f-113">아래 섹션의 가이드를 사용 하 여 MRTK 없이 프로젝트를 수동으로 구성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-113">You can also manually configure the project without MRTK with the guide in the section below.</span></span>

## <a name="holographic-vs-immersive-headsets"></a><span data-ttu-id="ac62f-114">Holographic 및 몰입 형 헤드셋</span><span class="sxs-lookup"><span data-stu-id="ac62f-114">Holographic vs. immersive headsets</span></span>

<span data-ttu-id="ac62f-115">Unity 카메라 구성 요소의 기본 설정은 실제 세계에 있지 않기 때문에 skybox 같은 배경을 필요로 하는 기존의 3D 응용 프로그램을 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-115">The default settings on the Unity Camera component are for traditional 3D applications which need a skybox-like background as they don't have a real world.</span></span>

* <span data-ttu-id="ac62f-116">**[몰입 형 헤드셋](immersive-headset-hardware-details.md)** 에서 실행 하는 경우 사용자에 게 표시 되는 모든 항목을 렌더링 하므로 skybox을 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-116">When running on an **[immersive headset](immersive-headset-hardware-details.md)**, you are rendering everything the user sees, and so you'll likely want to keep the skybox.</span></span>
* <span data-ttu-id="ac62f-117">그러나 [HoloLens](hololens-hardware-details.md)와 같은 **holographic 헤드셋** 에서 실행 하는 경우 실제 세계는 카메라에서 렌더링 하는 모든 항목 뒤에 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-117">However, when running on a **holographic headset** like [HoloLens](hololens-hardware-details.md), the real world should appear behind everything the camera renders.</span></span> <span data-ttu-id="ac62f-118">이렇게 하려면 카메라 배경을 투명 하 게 설정 합니다 (HoloLens에서 black 렌더링은 Skybox 질감이 아닌 투명 하 게 렌더링 됨).</span><span class="sxs-lookup"><span data-stu-id="ac62f-118">To do this, set the camera background to be transparent (in HoloLens, black renders as transparent) instead of a Skybox texture:</span></span>
    1. <span data-ttu-id="ac62f-119">계층 패널에서 주 카메라를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-119">Select the Main Camera in the Hierarchy panel</span></span>
    2. <span data-ttu-id="ac62f-120">검사기 패널에서 카메라 구성 요소를 찾아 Clear Flags dropdown을 Skybox에서 Solid Color로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-120">In the Inspector panel, find the Camera component and change the Clear Flags dropdown from Skybox to Solid Color</span></span>
    3. <span data-ttu-id="ac62f-121">배경색 선택을 선택 하 고 RGBA 값을 (0, 0, 0, 0)으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-121">Select the Background color picker and change the RGBA values to (0, 0, 0, 0)</span></span>

<span data-ttu-id="ac62f-122">스크립트 코드를 사용 하 여 [HolographicSettings](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html)를 확인 하 여 헤드셋이 몰입 또는 holographic 인지 여부를 런타임에 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-122">You can use script code to determine at runtime whether the headset is immersive or holographic by checking [HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).</span></span>

## <a name="positioning-the-camera"></a><span data-ttu-id="ac62f-123">카메라 위치 지정</span><span class="sxs-lookup"><span data-stu-id="ac62f-123">Positioning the Camera</span></span>

<span data-ttu-id="ac62f-124">사용자의 시작 위치 (X: 0, Y: 0, Z: 0)를 사용 하는 경우 앱을 레이아웃 하는 것이 더 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-124">It will be easier to lay out your app if you imagine the starting position of the user as (X: 0, Y: 0, Z: 0).</span></span> <span data-ttu-id="ac62f-125">주 카메라가 사용자 헤드의 이동을 추적 하므로 기본 카메라의 시작 위치를 설정 하 여 사용자의 시작 위치를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-125">Since the Main Camera is tracking movement of the user's head, the starting position of the user can be set by setting the starting position of the Main Camera.</span></span>

1. <span data-ttu-id="ac62f-126">계층 패널에서 주 카메라를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-126">Select Main Camera in the Hierarchy panel</span></span>
2. <span data-ttu-id="ac62f-127">검사기 패널에서 변형 구성 요소를 찾아 위치를 (X: 0, Y: 1, Z:-10)에서 (X: 0, Y: 0, Z: 0)로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-127">In the Inspector panel, find the Transform component and change the Position from (X: 0, Y: 1, Z: -10) to (X: 0, Y: 0, Z: 0)</span></span>

   <span data-ttu-id="ac62f-128">Unity의 검사기 창에서 카메라를 ![](images/maincamera-350px.png)</span><span class="sxs-lookup"><span data-stu-id="ac62f-128">![Camera in the Inspector pane in Unity](images/maincamera-350px.png)</span></span>  
   <span data-ttu-id="ac62f-129">*Unity의 검사기 창에 있는 카메라*</span><span class="sxs-lookup"><span data-stu-id="ac62f-129">*Camera in the Inspector pane in Unity*</span></span>

## <a name="clip-planes"></a><span data-ttu-id="ac62f-130">클립 평면</span><span class="sxs-lookup"><span data-stu-id="ac62f-130">Clip planes</span></span>

<span data-ttu-id="ac62f-131">사용자에 게 너무 가까운 렌더링 콘텐츠는 혼합 현실에서 불편을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-131">Rendering content too close to the user can be uncomfortable in mixed reality.</span></span> <span data-ttu-id="ac62f-132">카메라 구성 요소에서 [근거리 및 원거리 클립 평면](hologram-stability.md#hologram-render-distances) 을 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-132">You can adjust the [near and far clip planes](hologram-stability.md#hologram-render-distances) on the Camera component.</span></span>

1. <span data-ttu-id="ac62f-133">계층 패널에서 주 카메라를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-133">Select the Main Camera in the Hierarchy panel</span></span>
2. <span data-ttu-id="ac62f-134">검사기 패널에서 평면 클리핑 카메라 구성 요소를 찾아 가까운 텍스트 상자를 0.3에서 85로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-134">In the Inspector panel, find the Camera component Clipping Planes and change the Near textbox from 0.3 to .85.</span></span> <span data-ttu-id="ac62f-135">더 가까이 렌더링 된 콘텐츠는 사용자 discomfort 발생할 수 있으므로 [렌더링 거리 지침](hologram-stability.md#hologram-render-distances)에 따라 피해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-135">Content rendered even closer can lead to user discomfort and should be avoided per the [render distance guidelines](hologram-stability.md#hologram-render-distances).</span></span>

## <a name="multiple-cameras"></a><span data-ttu-id="ac62f-136">여러 카메라</span><span class="sxs-lookup"><span data-stu-id="ac62f-136">Multiple Cameras</span></span>

<span data-ttu-id="ac62f-137">장면에 여러 카메라 구성 요소가 있는 경우 Unity는 MainCamera 태그가 있는 GameObject를 확인 하 여 stereoscopic 렌더링 및 헤드 추적에 사용할 카메라를 알고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-137">When there are multiple Camera components in the scene, Unity knows which camera to use for stereoscopic rendering and head tracking by checking which GameObject has the MainCamera tag.</span></span>

## <a name="recentering-a-seated-experience"></a><span data-ttu-id="ac62f-138">장착 된 환경 입력</span><span class="sxs-lookup"><span data-stu-id="ac62f-138">Recentering a seated experience</span></span>

<span data-ttu-id="ac62f-139">통합 된 [환경을](coordinate-systems.md)구축 하는 경우 XR를 호출 하 여 사용자의 현재 헤드 위치에서 Unity의 세계 원본을 recenter 수 있습니다 **[. Recenter 메서드입니다.](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)**</span><span class="sxs-lookup"><span data-stu-id="ac62f-139">If you're building a [seated-scale experience](coordinate-systems.md), you can recenter Unity's world origin at the user's current head position by calling the **[XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** method.</span></span>

## <a name="reprojection-modes"></a><span data-ttu-id="ac62f-140">재 투영 모드</span><span class="sxs-lookup"><span data-stu-id="ac62f-140">Reprojection modes</span></span>

<span data-ttu-id="ac62f-141">HoloLens 및 몰입 형 헤드셋은 모두 앱이 렌더링 하는 각 프레임을 다시 프로젝션 하 여 photons를 내보낼 때 사용자의 실제 헤드 위치 misprediction 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-141">Both HoloLens and immersive headsets will reproject each frame your app renders to adjust for any misprediction of the user's actual head position when photons are emitted.</span></span>

<span data-ttu-id="ac62f-142">기본적으로:</span><span class="sxs-lookup"><span data-stu-id="ac62f-142">By default:</span></span>

* <span data-ttu-id="ac62f-143">**모던 헤드셋** 은 위치를 다시 프로젝션 하 고, 앱에서 지정 된 프레임에 대 한 깊이 버퍼를 제공 하는 경우 위치 및 방향 모두에서 misprediction에 대 한 holograms을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-143">**Immersive headsets** will perform positional reprojection, adjusting your holograms for misprediction in both position and orientation, if the app provides a depth buffer for a given frame.</span></span>  <span data-ttu-id="ac62f-144">깊이 버퍼를 제공 하지 않으면 시스템은 방향 으로만 mispredictions을 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-144">If a depth buffer is not provided, the system will only correct mispredictions in orientation.</span></span>
* <span data-ttu-id="ac62f-145">**Holographic 헤드셋** 과 같은 헤드셋은 앱이 깊이 버퍼를 제공 하는지 여부에 관계 없이 위치를 다시 프로젝션 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-145">**Holographic headsets** like HoloLens will perform positional reprojection whether the app provides its depth buffer or not.</span></span>  <span data-ttu-id="ac62f-146">렌더링은 실제 세계에서 제공 하는 안정적인 배경을 사용 하는 스파스 인 경우가 많기 때문에 HoloLens의 깊이 버퍼 없이 위치 다시 프로젝션이 가능 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-146">Positional reprojection is possible without depth buffers on HoloLens as rendering is often sparse with a stable background provided by the real world.</span></span>

<span data-ttu-id="ac62f-147">엄격 본문 잠긴 콘텐츠 (예: 360도 비디오 콘텐츠)를 사용 하 여 [방향 전용 환경을](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience) 빌드하는 경우에는를 설정 [하 여 reprojection 모드를 방향 으로만 설정 하면 됩니다. HolographicSettings ReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) HolographicReprojectionMode. [OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).</span><span class="sxs-lookup"><span data-stu-id="ac62f-147">If you know that you are building an [orientation-only experience](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience) with rigidly body-locked content (e.g. 360-degree video content), you can explicitly set the reprojection mode to be orientation only by setting [HolographicSettings.ReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) to [HolographicReprojectionMode.OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).</span></span>

## <a name="sharing-your-depth-buffers-with-windows"></a><span data-ttu-id="ac62f-148">Windows와 깊이 버퍼 공유</span><span class="sxs-lookup"><span data-stu-id="ac62f-148">Sharing your depth buffers with Windows</span></span>

<span data-ttu-id="ac62f-149">Windows에 앱의 깊이 버퍼를 공유 하면 각 프레임에서 렌더링 하는 헤드셋의 유형에 따라 홀로그램 안정성의 두 가지 향상 된 기능 중 하나를 앱에 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-149">Sharing your app's depth buffer to Windows each frame will give your app one of two boosts in hologram stability, based on the type of headset you're rendering for:</span></span>

* <span data-ttu-id="ac62f-150">**몰입 형 헤드셋** 은 깊이 버퍼가 제공 될 때 위치를 다시 프로젝션 하 여 위치와 방향 모두에서 misprediction에 대 한 holograms를 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-150">**Immersive headsets** can perform positional reprojection when a depth buffer is provided, adjusting your holograms for misprediction in both position and orientation.</span></span>
* <span data-ttu-id="ac62f-151">**Holographic 헤드셋** 에는 몇 가지 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-151">**Holographic headsets** have a few different methods.</span></span> <span data-ttu-id="ac62f-152">HoloLens 1은 깊이 버퍼가 제공 될 때 [포커스 지점을](focus-point-in-unity.md) 자동으로 선택 하 여 대부분의 콘텐츠와 교차 하는 평면을 따라 홀로그램의 안정성을 최적화 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-152">HoloLens 1 will automatically select a [focus point](focus-point-in-unity.md) when a depth buffer is provided, optimizing hologram stability along the plane that intersects the most content.</span></span> <span data-ttu-id="ac62f-153">HoloLens 2는 [깊이 LSR (설명 참조)](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)을 사용 하 여 콘텐츠를 안정화 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-153">HoloLens 2 will stabilize content using [Depth LSR (see Remarks)](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint).</span></span>

<span data-ttu-id="ac62f-154">Unity 앱이 Windows에 깊이 버퍼를 제공할지 여부를 설정 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-154">To set whether your Unity app will provide a depth buffer to Windows:</span></span>

1. <span data-ttu-id="ac62f-155">**편집** > **프로젝트 설정** > **플레이어** > **유니버설 Windows 플랫폼 탭** > **XR 설정**으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-155">Go to **Edit** > **Project Settings** > **Player** > **Universal Windows Platform tab** > **XR Settings**.</span></span>
2. <span data-ttu-id="ac62f-156">**Windows Mixed REALITY SDK** 항목을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-156">Expand the **Windows Mixed Reality SDK** item.</span></span>
3. <span data-ttu-id="ac62f-157">**깊이 버퍼 공유 사용** 확인란을 선택 하거나 선택 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-157">Check or uncheck the **Enable Depth Buffer Sharing** check box.</span></span>  <span data-ttu-id="ac62f-158">이 기능은 Unity에 추가 되 고 업그레이드 된 이전 프로젝트에서는 기본적으로 선택 되지 않으므로 새로 만든 프로젝트에서 기본적으로 선택 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-158">This will be checked by default in new projects created since this feature was added to Unity and will be unchecked by default for older projects that were upgraded.</span></span>

<span data-ttu-id="ac62f-159">Windows에 깊이 버퍼를 제공 하면 시각적 품질을 향상 시킬 수 있습니다. 즉, Windows에서 기본 카메라의 Unity에 설정 된 근처와 far를 사용 하 여 깊이 버퍼의 정규화 된 픽셀 당 깊이 값을 미터 단위로 다시 정확히 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-159">Providing a depth buffer to Windows can improve visual quality so long as Windows can accurately map the normalized per-pixel depth values in your depth buffer back to distances in meters, using the near and far planes you've set in Unity on the main camera.</span></span>  <span data-ttu-id="ac62f-160">렌더링 과정에서 일반적인 방법으로 깊이 값이 처리 되는 경우에는 일반적으로 여기에 자세히 설명 해야 합니다 .이는 기존 색 픽셀을 통해 표시 되는 동안 깊이 버퍼에 쓰는 반투명 렌더링 패스가 다시 프로젝션을 혼동 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-160">If your render passes handle depth values in typical ways, you should generally be fine here, though translucent render passes that write to the depth buffer while showing through to existing color pixels can confuse the reprojection.</span></span>  <span data-ttu-id="ac62f-161">렌더링 패스에서 깊이 값이 정확 하지 않은 최종 깊이 픽셀을 많이 사용 하는 경우 "깊이 버퍼 공유 사용"을 선택을 취소 하면 시각적 품질이 향상 될 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="ac62f-161">If you know that your render passes will leave many of your final depth pixels with inaccurate depth values, you are likely to get better visual quality by unchecking "Enable Depth Buffer Sharing".</span></span>

## <a name="see-also"></a><span data-ttu-id="ac62f-162">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ac62f-162">See also</span></span>

* [<span data-ttu-id="ac62f-163">홀로그램 안정성</span><span class="sxs-lookup"><span data-stu-id="ac62f-163">Hologram stability</span></span>](hologram-stability.md)
* [<span data-ttu-id="ac62f-164">MixedRealityToolkit 주 카메라 prefab</span><span class="sxs-lookup"><span data-stu-id="ac62f-164">MixedRealityToolkit Main Camera.prefab</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs)
