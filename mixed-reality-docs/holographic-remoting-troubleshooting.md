---
title: Holographic 원격 문제 해결 및 제한 사항
description: HoloLens 2의 Holographic Remoting에 대 한 문제 해결 단계입니다.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: Windows Mixed Reality, holograms, holographic remoting, 원격 렌더링, 네트워크 렌더링, HoloLens, 원격 holograms, 문제 해결, 도움말
ms.openlocfilehash: 79650ceab5d0125a8a06c776a59a45a78d0aa20c
ms.sourcegitcommit: fef42e2908e49822f2d13b05d2f9260bf0d72158
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86061116"
---
# <a name="holographic-remoting-troubleshooting"></a><span data-ttu-id="5e5f8-104">Holographic 원격 문제 해결</span><span class="sxs-lookup"><span data-stu-id="5e5f8-104">Holographic Remoting troubleshooting</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5e5f8-105">이 지침은 HoloLens 2의 Holographic Remoting에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f8-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="spectre-mitigated-libraries-not-found"></a><span data-ttu-id="5e5f8-106">스펙터 완화 라이브러리를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f8-106">Spectre mitigated libraries not found.</span></span>

<span data-ttu-id="5e5f8-107">Holographic Remoting 샘플 앱은 릴리스 구성에서/Qspectre (스펙터 완화)를 사용 하도록 설정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f8-107">Holographic Remoting sample apps have Spectre mitigation (/Qspectre) enabled in Release configuration.</span></span>

<span data-ttu-id="5e5f8-108">' Vccorlib. n a l e '을 열 수 없다는 심각한 링커 오류가 발생 하는 경우 Visual Studio 워크 로드에 스펙터 완화 된 라이브러리가 포함 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f8-108">If you get a fatal linker error which states that 'vccorlib.lib' cannot be opened, make sure that your Visual Studio Workload includes the Spectre mitigated libraries.</span></span> <span data-ttu-id="5e5f8-109">자세한 내용은 https://aka.ms/Ofhn4c 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5e5f8-109">See https://aka.ms/Ofhn4c for more information.</span></span>

## <a name="speech"></a><span data-ttu-id="5e5f8-110">음성</span><span class="sxs-lookup"><span data-stu-id="5e5f8-110">Speech</span></span>

<span data-ttu-id="5e5f8-111">Holographic Remoting Player는에 대해 말하고 사용 하지 않도록 설정할 수 있는 진단 오버레이를 지원 합니다 ```Enable Diagnostics``` ```Disable Diagnostics``` .</span><span class="sxs-lookup"><span data-stu-id="5e5f8-111">The Holographic Remoting Player supports a diagnostics overlay which can be enabled by saying ```Enable Diagnostics``` and disabled by saying ```Disable Diagnostics```.</span></span> <span data-ttu-id="5e5f8-112">이러한 음성 명령에 문제가 있는 경우를 URL로 사용 하 여 웹 브라우저를 통해 Holographic 원격 플레이어를 시작할 수도 있습니다 ```ms-holographic-remoting:?stats``` .</span><span class="sxs-lookup"><span data-stu-id="5e5f8-112">If you have trouble with these voice commands you can also launch the Holographic Remoting player via a web browser using ```ms-holographic-remoting:?stats``` as an URL.</span></span>

## <a name="limitations"></a><span data-ttu-id="5e5f8-113">제한 사항</span><span class="sxs-lookup"><span data-stu-id="5e5f8-113">Limitations</span></span>

<span data-ttu-id="5e5f8-114">다음 Api는 현재 HoloLens 2에 대 한 Holographic 원격을 사용 하는 경우 지원 **되지** 않으며 별도로 ```ERROR_NOT_SUPPORTED``` 명시 하지 않는 한 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f8-114">The following APIs are currently **not** supported when using Holographic Remoting for HoloLens 2 and will raises an ```ERROR_NOT_SUPPORTED``` error unless otherwise stated:</span></span>

[<span data-ttu-id="5e5f8-115">Windows.Graphics.Holographic</span><span class="sxs-lookup"><span data-stu-id="5e5f8-115">Windows.Graphics.Holographic</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [<span data-ttu-id="5e5f8-116">HolographicCamera.ViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="5e5f8-116">HolographicCamera.ViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - <span data-ttu-id="5e5f8-117">[2.0.18 이상을](holographic-remoting-version-history.md#v2.0.18) 버전부터 지원 됨</span><span class="sxs-lookup"><span data-stu-id="5e5f8-117">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="5e5f8-118">이전 버전에서는 항상 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f8-118">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="5e5f8-119">HolographicCamera.IsHardwareContentProtectionEnabled</span><span class="sxs-lookup"><span data-stu-id="5e5f8-119">HolographicCamera.IsHardwareContentProtectionEnabled</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled#Windows_Graphics_Holographic_HolographicCamera_IsHardwareContentProtectionEnabled)
* [<span data-ttu-id="5e5f8-120">HolographicViewConfiguration.RequestRenderTargetSize</span><span class="sxs-lookup"><span data-stu-id="5e5f8-120">HolographicViewConfiguration.RequestRenderTargetSize</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - <span data-ttu-id="5e5f8-121">는 실패 하지 않지만 렌더링 대상 크기는 변경 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f8-121">Does not fail, but the render target size will not be changed.</span></span>
* [<span data-ttu-id="5e5f8-122">HolographicCameraPose.OverrideProjectionTransform</span><span class="sxs-lookup"><span data-stu-id="5e5f8-122">HolographicCameraPose.OverrideProjectionTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [<span data-ttu-id="5e5f8-123">HolographicCameraPose</span><span class="sxs-lookup"><span data-stu-id="5e5f8-123">HolographicCameraPose.OverrideViewport</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [<span data-ttu-id="5e5f8-124">HolographicCameraPose. OverrideViewTransform</span><span class="sxs-lookup"><span data-stu-id="5e5f8-124">HolographicCameraPose.OverrideViewTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
* [<span data-ttu-id="5e5f8-125">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span><span class="sxs-lookup"><span data-stu-id="5e5f8-125">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - <span data-ttu-id="5e5f8-126">는 실패 하지 않지만 심층 버퍼는 원격이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f8-126">Does not fail but depth buffer will not be remoted.</span></span>
  - <span data-ttu-id="5e5f8-127">[2.1.0](holographic-remoting-version-history.md#v2.1.0) 버전부터 지원 됨</span><span class="sxs-lookup"><span data-stu-id="5e5f8-127">Supported starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0)</span></span>
* [<span data-ttu-id="5e5f8-128">HolographicDisplay.TryGetViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="5e5f8-128">HolographicDisplay.TryGetViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - <span data-ttu-id="5e5f8-129">HolographicViewConfigurationKind. PhotoVideoCamera를 쿼리하면 항상이 반환 됩니다 ```nullptr``` .</span><span class="sxs-lookup"><span data-stu-id="5e5f8-129">Querying HolographicViewConfigurationKind.PhotoVideoCamera will always return a ```nullptr```.</span></span>
  - <span data-ttu-id="5e5f8-130">[2.0.18 이상을](holographic-remoting-version-history.md#v2.0.18) 버전부터 지원 됨</span><span class="sxs-lookup"><span data-stu-id="5e5f8-130">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="5e5f8-131">이전 버전에서는 항상 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f8-131">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="5e5f8-132">HolographicSpace.CreateFramePresentationMonitor</span><span class="sxs-lookup"><span data-stu-id="5e5f8-132">HolographicSpace.CreateFramePresentationMonitor</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [<span data-ttu-id="5e5f8-133">HolographicDisplay. GetDefault</span><span class="sxs-lookup"><span data-stu-id="5e5f8-133">HolographicDisplay.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - <span data-ttu-id="5e5f8-134">는 연결을 설정 하기 전에 호출 되는 경우 오류를 보고 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f8-134">Will report an error if called before a connection was established.</span></span>


[<span data-ttu-id="5e5f8-135">Windows.Perception.Spatial</span><span class="sxs-lookup"><span data-stu-id="5e5f8-135">Windows.Perception.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [<span data-ttu-id="5e5f8-136">Spatiallocation이. AbsoluteAngularAcceleration</span><span class="sxs-lookup"><span data-stu-id="5e5f8-136">SpatialLocation.AbsoluteAngularAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [<span data-ttu-id="5e5f8-137">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span><span class="sxs-lookup"><span data-stu-id="5e5f8-137">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [<span data-ttu-id="5e5f8-138">Spatiallocation이. AbsoluteAngularVelocity</span><span class="sxs-lookup"><span data-stu-id="5e5f8-138">SpatialLocation.AbsoluteAngularVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [<span data-ttu-id="5e5f8-139">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span><span class="sxs-lookup"><span data-stu-id="5e5f8-139">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [<span data-ttu-id="5e5f8-140">Spatiallocation이. AbsoluteLinearAcceleration</span><span class="sxs-lookup"><span data-stu-id="5e5f8-140">SpatialLocation.AbsoluteLinearAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [<span data-ttu-id="5e5f8-141">Spatiallocation이. AbsoluteLinearVelocity</span><span class="sxs-lookup"><span data-stu-id="5e5f8-141">SpatialLocation.AbsoluteLinearVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [<span data-ttu-id="5e5f8-142">SpatialStageFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="5e5f8-142">SpatialStageFrameOfReference.Current</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - <span data-ttu-id="5e5f8-143">[2.2.0](holographic-remoting-version-history.md#v2.2.0) 버전부터 지원 됨</span><span class="sxs-lookup"><span data-stu-id="5e5f8-143">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>
  - <span data-ttu-id="5e5f8-144">이전 버전에서는 항상을 반환 ```nullptr``` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f8-144">On previous versions always returns ```nullptr```.</span></span>
* [<span data-ttu-id="5e5f8-145">SpatialStageFrameOfReference.RequestNewStageAsync</span><span class="sxs-lookup"><span data-stu-id="5e5f8-145">SpatialStageFrameOfReference.RequestNewStageAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
  - <span data-ttu-id="5e5f8-146">[2.2.0](holographic-remoting-version-history.md#v2.2.0) 버전부터 지원 됨</span><span class="sxs-lookup"><span data-stu-id="5e5f8-146">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>
* [<span data-ttu-id="5e5f8-147">SpatialAnchor.RemovedByUser</span><span class="sxs-lookup"><span data-stu-id="5e5f8-147">SpatialAnchor.RemovedByUser</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [<span data-ttu-id="5e5f8-148">SpatialAnchorExporter.GetDefault</span><span class="sxs-lookup"><span data-stu-id="5e5f8-148">SpatialAnchorExporter.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - <span data-ttu-id="5e5f8-149">[2.0.9](holographic-remoting-version-history.md#v2.0.9)버전부터 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f8-149">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="5e5f8-150">이전 버전에서는 항상을 반환 ```nullptr``` 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f8-150">On previous versions always returns ```nullptr```.</span></span> 
* [<span data-ttu-id="5e5f8-151">SpatialAnchorExporter.RequestAccessAsync</span><span class="sxs-lookup"><span data-stu-id="5e5f8-151">SpatialAnchorExporter.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - <span data-ttu-id="5e5f8-152">[2.0.9](holographic-remoting-version-history.md#v2.0.9)버전부터 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f8-152">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="5e5f8-153">이전 버전에서 비동기 작업은 항상를 사용 하 여 완료 ```SpatialPerceptionAccessStatus.DeniedBySystem``` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f8-153">On previous versions the async operation always completed with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="5e5f8-154">SpatialAnchorTransferManager</span><span class="sxs-lookup"><span data-stu-id="5e5f8-154">SpatialAnchorTransferManager.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - <span data-ttu-id="5e5f8-155">비동기 작업은 항상를 사용 하 여 완료 ```SpatialPerceptionAccessStatus.DeniedBySystem``` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f8-155">Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="5e5f8-156">SpatialAnchorTransferManager.TryExportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="5e5f8-156">SpatialAnchorTransferManager.TryExportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - <span data-ttu-id="5e5f8-157">비동기 작업은 항상를 사용 하 여 완료 ```false``` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f8-157">Async operation always completes with ```false```.</span></span>
* [<span data-ttu-id="5e5f8-158">SpatialAnchorTransferManager.TryImportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="5e5f8-158">SpatialAnchorTransferManager.TryImportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - <span data-ttu-id="5e5f8-159">비동기 작업은 항상를 사용 하 여 완료 ```nullptr``` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e5f8-159">Async operation always completes with ```nullptr```.</span></span>

[<span data-ttu-id="5e5f8-160">Windows.UI.Input.Spatial</span><span class="sxs-lookup"><span data-stu-id="5e5f8-160">Windows.UI.Input.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [<span data-ttu-id="5e5f8-161">SpatialInteractionSource.TryCreateHandMeshObserver</span><span class="sxs-lookup"><span data-stu-id="5e5f8-161">SpatialInteractionSource.TryCreateHandMeshObserver</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [<span data-ttu-id="5e5f8-162">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span><span class="sxs-lookup"><span data-stu-id="5e5f8-162">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)
* [<span data-ttu-id="5e5f8-163">SpatialInteractionSource</span><span class="sxs-lookup"><span data-stu-id="5e5f8-163">SpatialInteractionSource.Controller</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)
  - <span data-ttu-id="5e5f8-164">[2.2.0](holographic-remoting-version-history.md#v2.2.0) 버전부터 지원 됨</span><span class="sxs-lookup"><span data-stu-id="5e5f8-164">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>

[<span data-ttu-id="5e5f8-165">Windows.Perception.Spatial.Preview</span><span class="sxs-lookup"><span data-stu-id="5e5f8-165">Windows.Perception.Spatial.Preview</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [<span data-ttu-id="5e5f8-166">SpatialGraphInteropPreview.CreateLocatorForNode</span><span class="sxs-lookup"><span data-stu-id="5e5f8-166">SpatialGraphInteropPreview.CreateLocatorForNode</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [<span data-ttu-id="5e5f8-167">SpatialGraphInteropPreview.TryCreateFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="5e5f8-167">SpatialGraphInteropPreview.TryCreateFrameOfReference</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)

## <a name="see-also"></a><span data-ttu-id="5e5f8-168">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5e5f8-168">See Also</span></span>
* [<span data-ttu-id="5e5f8-169">Holographic 원격 버전 기록</span><span class="sxs-lookup"><span data-stu-id="5e5f8-169">Holographic Remoting Version History</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="5e5f8-170">홀로그램 원격 원격 앱 작성</span><span class="sxs-lookup"><span data-stu-id="5e5f8-170">Writing a Holographic Remoting remote app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="5e5f8-171">사용자 지정 홀로그램 원격 플레이어 앱 작성</span><span class="sxs-lookup"><span data-stu-id="5e5f8-171">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="5e5f8-172">홀로그램 원격 소프트웨어 사용 조건</span><span class="sxs-lookup"><span data-stu-id="5e5f8-172">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="5e5f8-173">Microsoft 개인정보처리방침</span><span class="sxs-lookup"><span data-stu-id="5e5f8-173">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
