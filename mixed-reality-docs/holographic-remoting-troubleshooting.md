---
title: Holographic 원격 문제 해결 및 제한 사항
description: HoloLens 2의 Holographic Remoting에 대 한 문제 해결 단계입니다.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: Windows Mixed Reality, holograms, holographic remoting, 원격 렌더링, 네트워크 렌더링, HoloLens, 원격 holograms, 문제 해결, 도움말
ms.openlocfilehash: fc379eb4ad849fb5b236b82719711b37fead8a68
ms.sourcegitcommit: 48456c607a2d0dcf035a77e8ba67615396b0a211
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81484313"
---
# <a name="holographic-remoting-troubleshooting"></a><span data-ttu-id="5b844-104">Holographic 원격 문제 해결</span><span class="sxs-lookup"><span data-stu-id="5b844-104">Holographic Remoting troubleshooting</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5b844-105">이 지침은 HoloLens 2의 Holographic Remoting에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b844-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="spectre-mitigated-libraries-not-found"></a><span data-ttu-id="5b844-106">스펙터 완화 라이브러리를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5b844-106">Spectre mitigated libraries not found.</span></span>

<span data-ttu-id="5b844-107">Holographic Remoting 샘플 앱은 릴리스 구성에서/Qspectre (스펙터 완화)를 사용 하도록 설정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="5b844-107">Holographic Remoting sample apps have Spectre mitigation (/Qspectre) enabled in Release configuration.</span></span>

<span data-ttu-id="5b844-108">' Vccorlib. n a l e '을 열 수 없다는 심각한 링커 오류가 발생 하는 경우 Visual Studio 워크 로드에 스펙터 완화 된 라이브러리가 포함 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b844-108">If you get a fatal linker error which states that 'vccorlib.lib' cannot be opened, make sure that your Visual Studio Workload includes the Spectre mitigated libraries.</span></span> <span data-ttu-id="5b844-109">자세한 내용은 https://aka.ms/Ofhn4c을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5b844-109">See https://aka.ms/Ofhn4c for more information.</span></span>

## <a name="limitations"></a><span data-ttu-id="5b844-110">제한 사항</span><span class="sxs-lookup"><span data-stu-id="5b844-110">Limitations</span></span>

<span data-ttu-id="5b844-111">Holographic 원격을 사용 하 여 HoloLens 2를 사용 하는 경우 다음 Api는 현재 지원 **되지** 않습니다. 달리 지정 되지 않은 경우에는 ```ERROR_NOT_SUPPORTED``` 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b844-111">The following APIs are currently **not** supported when using Holographic Remoting for HoloLens 2 and will raises an ```ERROR_NOT_SUPPORTED``` error unless otherwise stated:</span></span>

[<span data-ttu-id="5b844-112">Windows.Graphics.Holographic</span><span class="sxs-lookup"><span data-stu-id="5b844-112">Windows.Graphics.Holographic</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [<span data-ttu-id="5b844-113">HolographicCamera 구성</span><span class="sxs-lookup"><span data-stu-id="5b844-113">HolographicCamera.ViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - <span data-ttu-id="5b844-114">[2.0.18 이상을](holographic-remoting-version-history.md#v2.0.18) 버전부터 지원 됨</span><span class="sxs-lookup"><span data-stu-id="5b844-114">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="5b844-115">이전 버전에서는 항상 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b844-115">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="5b844-116">HolographicCamera.IsHardwareContentProtectionEnabled</span><span class="sxs-lookup"><span data-stu-id="5b844-116">HolographicCamera.IsHardwareContentProtectionEnabled</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled#Windows_Graphics_Holographic_HolographicCamera_IsHardwareContentProtectionEnabled)
* [<span data-ttu-id="5b844-117">HolographicViewConfiguration.RequestRenderTargetSize</span><span class="sxs-lookup"><span data-stu-id="5b844-117">HolographicViewConfiguration.RequestRenderTargetSize</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - <span data-ttu-id="5b844-118">는 실패 하지 않지만 렌더링 대상 크기는 변경 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5b844-118">Does not fail, but the render target size will not be changed.</span></span>
* [<span data-ttu-id="5b844-119">HolographicCameraPose.OverrideProjectionTransform</span><span class="sxs-lookup"><span data-stu-id="5b844-119">HolographicCameraPose.OverrideProjectionTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [<span data-ttu-id="5b844-120">HolographicCameraPose</span><span class="sxs-lookup"><span data-stu-id="5b844-120">HolographicCameraPose.OverrideViewport</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [<span data-ttu-id="5b844-121">HolographicCameraPose. OverrideViewTransform</span><span class="sxs-lookup"><span data-stu-id="5b844-121">HolographicCameraPose.OverrideViewTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
* [<span data-ttu-id="5b844-122">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span><span class="sxs-lookup"><span data-stu-id="5b844-122">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - <span data-ttu-id="5b844-123">는 실패 하지 않지만 심층 버퍼는 원격이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="5b844-123">Does not fail but depth buffer will not be remoted.</span></span>
  - <span data-ttu-id="5b844-124">[2.1.0](holographic-remoting-version-history.md#v2.1.0) 버전부터 지원 됨</span><span class="sxs-lookup"><span data-stu-id="5b844-124">Supported starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0)</span></span>
* [<span data-ttu-id="5b844-125">HolographicDisplay.TryGetViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="5b844-125">HolographicDisplay.TryGetViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - <span data-ttu-id="5b844-126">HolographicViewConfigurationKind. PhotoVideoCamera를 쿼리하면 항상 ```nullptr```반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b844-126">Querying HolographicViewConfigurationKind.PhotoVideoCamera will always return a ```nullptr```.</span></span>
  - <span data-ttu-id="5b844-127">[2.0.18 이상을](holographic-remoting-version-history.md#v2.0.18) 버전부터 지원 됨</span><span class="sxs-lookup"><span data-stu-id="5b844-127">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="5b844-128">이전 버전에서는 항상 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b844-128">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="5b844-129">HolographicSpace.CreateFramePresentationMonitor</span><span class="sxs-lookup"><span data-stu-id="5b844-129">HolographicSpace.CreateFramePresentationMonitor</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [<span data-ttu-id="5b844-130">HolographicDisplay. GetDefault</span><span class="sxs-lookup"><span data-stu-id="5b844-130">HolographicDisplay.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - <span data-ttu-id="5b844-131">는 연결을 설정 하기 전에 호출 되는 경우 오류를 보고 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b844-131">Will report an error if called before a connection was established.</span></span>


[<span data-ttu-id="5b844-132">Windows.Perception.Spatial</span><span class="sxs-lookup"><span data-stu-id="5b844-132">Windows.Perception.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [<span data-ttu-id="5b844-133">Spatiallocation이. AbsoluteAngularAcceleration</span><span class="sxs-lookup"><span data-stu-id="5b844-133">SpatialLocation.AbsoluteAngularAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [<span data-ttu-id="5b844-134">Spatiallocation이. AbsoluteAngularAccelerationAxisAngle</span><span class="sxs-lookup"><span data-stu-id="5b844-134">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [<span data-ttu-id="5b844-135">Spatiallocation이. AbsoluteAngularVelocity</span><span class="sxs-lookup"><span data-stu-id="5b844-135">SpatialLocation.AbsoluteAngularVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [<span data-ttu-id="5b844-136">Spatiallocation이. AbsoluteAngularVelocityAxisAngle</span><span class="sxs-lookup"><span data-stu-id="5b844-136">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [<span data-ttu-id="5b844-137">Spatiallocation이. AbsoluteLinearAcceleration</span><span class="sxs-lookup"><span data-stu-id="5b844-137">SpatialLocation.AbsoluteLinearAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [<span data-ttu-id="5b844-138">Spatiallocation이. AbsoluteLinearVelocity</span><span class="sxs-lookup"><span data-stu-id="5b844-138">SpatialLocation.AbsoluteLinearVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [<span data-ttu-id="5b844-139">SpatialStageFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="5b844-139">SpatialStageFrameOfReference.Current</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - <span data-ttu-id="5b844-140">```nullptr```항상를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b844-140">Always returns ```nullptr```.</span></span>
* [<span data-ttu-id="5b844-141">SpatialStageFrameOfReference.RequestNewStageAsync</span><span class="sxs-lookup"><span data-stu-id="5b844-141">SpatialStageFrameOfReference.RequestNewStageAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
* [<span data-ttu-id="5b844-142">SpatialAnchor.RemovedByUser</span><span class="sxs-lookup"><span data-stu-id="5b844-142">SpatialAnchor.RemovedByUser</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [<span data-ttu-id="5b844-143">SpatialAnchorExporter. GetDefault</span><span class="sxs-lookup"><span data-stu-id="5b844-143">SpatialAnchorExporter.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - <span data-ttu-id="5b844-144">[2.0.9](holographic-remoting-version-history.md#v2.0.9)버전부터 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b844-144">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="5b844-145">이전 버전에서는 ```nullptr```항상를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="5b844-145">On previous versions always returns ```nullptr```.</span></span> 
* [<span data-ttu-id="5b844-146">SpatialAnchorExporter</span><span class="sxs-lookup"><span data-stu-id="5b844-146">SpatialAnchorExporter.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - <span data-ttu-id="5b844-147">[2.0.9](holographic-remoting-version-history.md#v2.0.9)버전부터 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b844-147">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="5b844-148">이전 버전에서 비동기 작업은 항상 ```SpatialPerceptionAccessStatus.DeniedBySystem```를 사용 하 여 완료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b844-148">On previous versions the async operation always completed with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="5b844-149">SpatialAnchorTransferManager</span><span class="sxs-lookup"><span data-stu-id="5b844-149">SpatialAnchorTransferManager.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - <span data-ttu-id="5b844-150">비동기 작업은 항상 ```SpatialPerceptionAccessStatus.DeniedBySystem```를 사용 하 여 완료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b844-150">Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="5b844-151">SpatialAnchorTransferManager.TryExportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="5b844-151">SpatialAnchorTransferManager.TryExportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - <span data-ttu-id="5b844-152">비동기 작업은 항상 ```false```를 사용 하 여 완료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b844-152">Async operation always completes with ```false```.</span></span>
* [<span data-ttu-id="5b844-153">SpatialAnchorTransferManager.TryImportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="5b844-153">SpatialAnchorTransferManager.TryImportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - <span data-ttu-id="5b844-154">비동기 작업은 항상 ```nullptr```를 사용 하 여 완료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5b844-154">Async operation always completes with ```nullptr```.</span></span>

[<span data-ttu-id="5b844-155">Windows.UI.Input.Spatial</span><span class="sxs-lookup"><span data-stu-id="5b844-155">Windows.UI.Input.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [<span data-ttu-id="5b844-156">SpatialInteractionSource.TryCreateHandMeshObserver</span><span class="sxs-lookup"><span data-stu-id="5b844-156">SpatialInteractionSource.TryCreateHandMeshObserver</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [<span data-ttu-id="5b844-157">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span><span class="sxs-lookup"><span data-stu-id="5b844-157">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)
* [<span data-ttu-id="5b844-158">SpatialInteractionSource</span><span class="sxs-lookup"><span data-stu-id="5b844-158">SpatialInteractionSource.Controller</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)

[<span data-ttu-id="5b844-159">Windows.Perception.Spatial.Preview</span><span class="sxs-lookup"><span data-stu-id="5b844-159">Windows.Perception.Spatial.Preview</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [<span data-ttu-id="5b844-160">SpatialGraphInteropPreview 노드</span><span class="sxs-lookup"><span data-stu-id="5b844-160">SpatialGraphInteropPreview.CreateLocatorForNode</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [<span data-ttu-id="5b844-161">SpatialGraphInteropPreview.TryCreateFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="5b844-161">SpatialGraphInteropPreview.TryCreateFrameOfReference</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)

## <a name="see-also"></a><span data-ttu-id="5b844-162">관련 항목</span><span class="sxs-lookup"><span data-stu-id="5b844-162">See Also</span></span>
* [<span data-ttu-id="5b844-163">Holographic 원격 버전 기록</span><span class="sxs-lookup"><span data-stu-id="5b844-163">Holographic Remoting Version History</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="5b844-164">Holographic Remoting 원격 앱 작성</span><span class="sxs-lookup"><span data-stu-id="5b844-164">Writing a Holographic Remoting remote app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="5b844-165">사용자 지정 Holographic Remoting 플레이어 앱 작성</span><span class="sxs-lookup"><span data-stu-id="5b844-165">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="5b844-166">홀로그램 원격 소프트웨어 사용 조건</span><span class="sxs-lookup"><span data-stu-id="5b844-166">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="5b844-167">Microsoft 개인 정보 취급 방침</span><span class="sxs-lookup"><span data-stu-id="5b844-167">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
