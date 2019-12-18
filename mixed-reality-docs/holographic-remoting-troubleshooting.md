---
title: Holographic 원격 문제 해결 및 제한 사항
description: HoloLens 2의 Holographic Remoting에 대 한 문제 해결 단계입니다.
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 12/17/2019
ms.topic: article
keywords: Windows Mixed Reality, holograms, holographic remoting, 원격 렌더링, 네트워크 렌더링, HoloLens, 원격 holograms, 문제 해결, 도움말
ms.openlocfilehash: 05333c8911010945a543cf603b9925eb30c841db
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181973"
---
# <a name="holographic-remoting-troubleshooting"></a><span data-ttu-id="9fa44-104">Holographic 원격 문제 해결</span><span class="sxs-lookup"><span data-stu-id="9fa44-104">Holographic Remoting troubleshooting</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9fa44-105">이 지침은 HoloLens 2의 Holographic Remoting에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fa44-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="spectre-mitigated-libraries-not-found"></a><span data-ttu-id="9fa44-106">스펙터 완화 라이브러리를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9fa44-106">Spectre mitigated libraries not found.</span></span>

<span data-ttu-id="9fa44-107">Holographic Remoting 샘플 앱은 릴리스 구성에서/Qspectre (스펙터 완화)를 사용 하도록 설정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="9fa44-107">Holographic Remoting sample apps have Spectre mitigation (/Qspectre) enabled in Release configuration.</span></span>

<span data-ttu-id="9fa44-108">' Vccorlib. n a l e '을 열 수 없다는 심각한 링커 오류가 발생 하는 경우 Visual Studio 워크 로드에 스펙터 완화 된 라이브러리가 포함 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa44-108">If you get a fatal linker error which states that 'vccorlib.lib' cannot be opened, make sure that your Visual Studio Workload includes the Spectre mitigated libraries.</span></span> <span data-ttu-id="9fa44-109">자세한 내용은 https://aka.ms/Ofhn4c 을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9fa44-109">See https://aka.ms/Ofhn4c for more information.</span></span>

## <a name="limitations"></a><span data-ttu-id="9fa44-110">제한 사항</span><span class="sxs-lookup"><span data-stu-id="9fa44-110">Limitations</span></span>

<span data-ttu-id="9fa44-111">Holographic 원격을 사용 하 여 HoloLens 2를 사용 하는 경우 다음 Api는 현재 지원 **되지** 않습니다. 달리 지정 되지 않은 경우에는 ```ERROR_NOT_SUPPORTED``` 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa44-111">The following APIs are currently **not** supported when using Holographic Remoting for HoloLens 2 and will raises an ```ERROR_NOT_SUPPORTED``` error unless otherwise stated:</span></span>

[<span data-ttu-id="9fa44-112">Windows.Graphics.Holographic</span><span class="sxs-lookup"><span data-stu-id="9fa44-112">Windows.Graphics.Holographic</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [<span data-ttu-id="9fa44-113">HolographicCamera 구성</span><span class="sxs-lookup"><span data-stu-id="9fa44-113">HolographicCamera.ViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - <span data-ttu-id="9fa44-114">[2.0.18 이상을](holographic-remoting-version-history.md#v2.0.18) 버전부터 지원 됨</span><span class="sxs-lookup"><span data-stu-id="9fa44-114">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="9fa44-115">이전 버전에서는 항상 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa44-115">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="9fa44-116">HolographicViewConfiguration.RequestRenderTargetSize</span><span class="sxs-lookup"><span data-stu-id="9fa44-116">HolographicViewConfiguration.RequestRenderTargetSize</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - <span data-ttu-id="9fa44-117">는 실패 하지 않지만 렌더링 대상 크기는 변경 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9fa44-117">Does not fail, but the render target size will not be changed.</span></span>
* [<span data-ttu-id="9fa44-118">HolographicCameraPose.OverrideProjectionTransform</span><span class="sxs-lookup"><span data-stu-id="9fa44-118">HolographicCameraPose.OverrideProjectionTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [<span data-ttu-id="9fa44-119">HolographicCameraPose</span><span class="sxs-lookup"><span data-stu-id="9fa44-119">HolographicCameraPose.OverrideViewport</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [<span data-ttu-id="9fa44-120">HolographicCameraPose. OverrideViewTransform</span><span class="sxs-lookup"><span data-stu-id="9fa44-120">HolographicCameraPose.OverrideViewTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
* [<span data-ttu-id="9fa44-121">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span><span class="sxs-lookup"><span data-stu-id="9fa44-121">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - <span data-ttu-id="9fa44-122">는 실패 하지 않지만 심층 버퍼는 원격이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="9fa44-122">Does not fail but depth buffer will not be remoted.</span></span>
* [<span data-ttu-id="9fa44-123">HolographicDisplay.TryGetViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="9fa44-123">HolographicDisplay.TryGetViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - <span data-ttu-id="9fa44-124">HolographicViewConfigurationKind. PhotoVideoCamera를 쿼리하면 항상 ```nullptr```반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fa44-124">Querying HolographicViewConfigurationKind.PhotoVideoCamera will always return a ```nullptr```.</span></span>
  - <span data-ttu-id="9fa44-125">[2.0.18 이상을](holographic-remoting-version-history.md#v2.0.18) 버전부터 지원 됨</span><span class="sxs-lookup"><span data-stu-id="9fa44-125">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="9fa44-126">이전 버전에서는 항상 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa44-126">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="9fa44-127">HolographicSpace.CreateFramePresentationMonitor</span><span class="sxs-lookup"><span data-stu-id="9fa44-127">HolographicSpace.CreateFramePresentationMonitor</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [<span data-ttu-id="9fa44-128">HolographicDisplay. GetDefault</span><span class="sxs-lookup"><span data-stu-id="9fa44-128">HolographicDisplay.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - <span data-ttu-id="9fa44-129">는 연결을 설정 하기 전에 호출 되는 경우 오류를 보고 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa44-129">Will report an error if called before a connection was established.</span></span>


[<span data-ttu-id="9fa44-130">Windows.Perception.Spatial</span><span class="sxs-lookup"><span data-stu-id="9fa44-130">Windows.Perception.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [<span data-ttu-id="9fa44-131">Spatiallocation이. AbsoluteAngularAcceleration</span><span class="sxs-lookup"><span data-stu-id="9fa44-131">SpatialLocation.AbsoluteAngularAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [<span data-ttu-id="9fa44-132">Spatiallocation이. AbsoluteAngularAccelerationAxisAngle</span><span class="sxs-lookup"><span data-stu-id="9fa44-132">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [<span data-ttu-id="9fa44-133">Spatiallocation이. AbsoluteAngularVelocity</span><span class="sxs-lookup"><span data-stu-id="9fa44-133">SpatialLocation.AbsoluteAngularVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [<span data-ttu-id="9fa44-134">Spatiallocation이. AbsoluteAngularVelocityAxisAngle</span><span class="sxs-lookup"><span data-stu-id="9fa44-134">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [<span data-ttu-id="9fa44-135">Spatiallocation이. AbsoluteLinearAcceleration</span><span class="sxs-lookup"><span data-stu-id="9fa44-135">SpatialLocation.AbsoluteLinearAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [<span data-ttu-id="9fa44-136">Spatiallocation이. AbsoluteLinearVelocity</span><span class="sxs-lookup"><span data-stu-id="9fa44-136">SpatialLocation.AbsoluteLinearVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [<span data-ttu-id="9fa44-137">SpatialStageFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="9fa44-137">SpatialStageFrameOfReference.Current</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - <span data-ttu-id="9fa44-138">항상 ```nullptr```를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa44-138">Always returns ```nullptr```.</span></span>
* [<span data-ttu-id="9fa44-139">SpatialStageFrameOfReference.RequestNewStageAsync</span><span class="sxs-lookup"><span data-stu-id="9fa44-139">SpatialStageFrameOfReference.RequestNewStageAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
* [<span data-ttu-id="9fa44-140">SpatialAnchor.RemovedByUser</span><span class="sxs-lookup"><span data-stu-id="9fa44-140">SpatialAnchor.RemovedByUser</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [<span data-ttu-id="9fa44-141">SpatialAnchorExporter. GetDefault</span><span class="sxs-lookup"><span data-stu-id="9fa44-141">SpatialAnchorExporter.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - <span data-ttu-id="9fa44-142">[2.0.9](holographic-remoting-version-history.md#v2.0.9)버전부터 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fa44-142">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="9fa44-143">이전 버전에서는 ```nullptr```항상를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fa44-143">On previous versions always returns ```nullptr```.</span></span> 
* [<span data-ttu-id="9fa44-144">SpatialAnchorExporter</span><span class="sxs-lookup"><span data-stu-id="9fa44-144">SpatialAnchorExporter.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - <span data-ttu-id="9fa44-145">[2.0.9](holographic-remoting-version-history.md#v2.0.9)버전부터 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fa44-145">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="9fa44-146">이전 버전에서 비동기 작업은 항상 ```SpatialPerceptionAccessStatus.DeniedBySystem```를 사용 하 여 완료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fa44-146">On previous versions the async operation always completed with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="9fa44-147">SpatialAnchorTransferManager</span><span class="sxs-lookup"><span data-stu-id="9fa44-147">SpatialAnchorTransferManager.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - <span data-ttu-id="9fa44-148">비동기 작업은 항상 ```SpatialPerceptionAccessStatus.DeniedBySystem```를 사용 하 여 완료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fa44-148">Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="9fa44-149">SpatialAnchorTransferManager.TryExportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="9fa44-149">SpatialAnchorTransferManager.TryExportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - <span data-ttu-id="9fa44-150">비동기 작업은 항상 ```false```를 사용 하 여 완료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fa44-150">Async operation always completes with ```false```.</span></span>
* [<span data-ttu-id="9fa44-151">SpatialAnchorTransferManager.TryImportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="9fa44-151">SpatialAnchorTransferManager.TryImportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - <span data-ttu-id="9fa44-152">비동기 작업은 항상 ```nullptr```를 사용 하 여 완료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fa44-152">Async operation always completes with ```nullptr```.</span></span>

[<span data-ttu-id="9fa44-153">Windows.UI.Input.Spatial</span><span class="sxs-lookup"><span data-stu-id="9fa44-153">Windows.UI.Input.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [<span data-ttu-id="9fa44-154">SpatialInteractionSource.TryCreateHandMeshObserver</span><span class="sxs-lookup"><span data-stu-id="9fa44-154">SpatialInteractionSource.TryCreateHandMeshObserver</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [<span data-ttu-id="9fa44-155">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span><span class="sxs-lookup"><span data-stu-id="9fa44-155">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)

[<span data-ttu-id="9fa44-156">Windows.Perception.Spatial.Preview</span><span class="sxs-lookup"><span data-stu-id="9fa44-156">Windows.Perception.Spatial.Preview</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [<span data-ttu-id="9fa44-157">SpatialGraphInteropPreview 노드</span><span class="sxs-lookup"><span data-stu-id="9fa44-157">SpatialGraphInteropPreview.CreateLocatorForNode</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [<span data-ttu-id="9fa44-158">SpatialGraphInteropPreview.TryCreateFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="9fa44-158">SpatialGraphInteropPreview.TryCreateFrameOfReference</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)
* [<span data-ttu-id="9fa44-159">SpatialInteractionSource</span><span class="sxs-lookup"><span data-stu-id="9fa44-159">SpatialInteractionSource.Controller</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)

## <a name="see-also"></a><span data-ttu-id="9fa44-160">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9fa44-160">See Also</span></span>
* [<span data-ttu-id="9fa44-161">Holographic 원격 버전 기록</span><span class="sxs-lookup"><span data-stu-id="9fa44-161">Holographic Remoting Version History</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="9fa44-162">Holographic 원격 호스트 앱 작성</span><span class="sxs-lookup"><span data-stu-id="9fa44-162">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="9fa44-163">사용자 지정 Holographic Remoting 플레이어 앱 작성</span><span class="sxs-lookup"><span data-stu-id="9fa44-163">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="9fa44-164">홀로그램 원격 소프트웨어 사용 조건</span><span class="sxs-lookup"><span data-stu-id="9fa44-164">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="9fa44-165">Microsoft 개인정보처리방침</span><span class="sxs-lookup"><span data-stu-id="9fa44-165">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
