---
title: Holographic 원격 문제 해결 및 제한 사항
description: HoloLens 2의 Holographic Remoting에 대 한 문제 해결 단계입니다.
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 10/28/2019
ms.topic: article
keywords: Windows Mixed Reality, holograms, holographic remoting, 원격 렌더링, 네트워크 렌더링, HoloLens, 원격 holograms, 문제 해결, 도움말
ms.openlocfilehash: 7b438d9169c9306e0056655e561c04b62b1662cf
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434240"
---
# <a name="holographic-remoting-troubleshooting"></a><span data-ttu-id="4007c-104">Holographic 원격 문제 해결</span><span class="sxs-lookup"><span data-stu-id="4007c-104">Holographic Remoting troubleshooting</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4007c-105">이 지침은 HoloLens 2의 Holographic Remoting에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4007c-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="spectre-mitigated-libraries-not-found"></a><span data-ttu-id="4007c-106">스펙터 완화 라이브러리를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4007c-106">Spectre mitigated libraries not found.</span></span>

<span data-ttu-id="4007c-107">Holographic Remoting 샘플 앱은 릴리스 구성에서/Qspectre (스펙터 완화)를 사용 하도록 설정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="4007c-107">Holographic Remoting sample apps have Spectre mitigation (/Qspectre) enabled in Release configuration.</span></span>

<span data-ttu-id="4007c-108">' Vccorlib. n a l e '을 열 수 없다는 심각한 링커 오류가 발생 하는 경우 Visual Studio 워크 로드에 스펙터 완화 된 라이브러리가 포함 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="4007c-108">If you get a fatal linker error which states that 'vccorlib.lib' cannot be opened, make sure that your Visual Studio Workload includes the Spectre mitigated libraries.</span></span> <span data-ttu-id="4007c-109">자세한 내용은 https://aka.ms/Ofhn4c 을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="4007c-109">See https://aka.ms/Ofhn4c for more information.</span></span>

## <a name="limitations"></a><span data-ttu-id="4007c-110">제한 사항</span><span class="sxs-lookup"><span data-stu-id="4007c-110">Limitations</span></span>

<span data-ttu-id="4007c-111">Holographic 원격을 사용 하 여 HoloLens 2를 사용 하는 경우 다음 Api는 현재 지원 **되지** 않습니다. 달리 지정 되지 않은 경우에는 ```ERROR_NOT_SUPPORTED``` 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="4007c-111">The following APIs are currently **not** supported when using Holographic Remoting for HoloLens 2 and will raises an ```ERROR_NOT_SUPPORTED``` error unless otherwise stated:</span></span>

[<span data-ttu-id="4007c-112">Windows.Graphics.Holographic</span><span class="sxs-lookup"><span data-stu-id="4007c-112">Windows.Graphics.Holographic</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [<span data-ttu-id="4007c-113">HolographicCamera 구성</span><span class="sxs-lookup"><span data-stu-id="4007c-113">HolographicCamera.ViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
* [<span data-ttu-id="4007c-114">HolographicCameraPose.OverrideProjectionTransform</span><span class="sxs-lookup"><span data-stu-id="4007c-114">HolographicCameraPose.OverrideProjectionTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [<span data-ttu-id="4007c-115">HolographicCameraPose</span><span class="sxs-lookup"><span data-stu-id="4007c-115">HolographicCameraPose.OverrideViewport</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [<span data-ttu-id="4007c-116">HolographicCameraPose. OverrideViewTransform</span><span class="sxs-lookup"><span data-stu-id="4007c-116">HolographicCameraPose.OverrideViewTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
* [<span data-ttu-id="4007c-117">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span><span class="sxs-lookup"><span data-stu-id="4007c-117">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - <span data-ttu-id="4007c-118">는 실패 하지 않지만 심층 버퍼는 원격이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="4007c-118">Does not fail but depth buffer will not be remoted.</span></span>
* [<span data-ttu-id="4007c-119">HolographicDisplay.TryGetViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="4007c-119">HolographicDisplay.TryGetViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
* [<span data-ttu-id="4007c-120">HolographicSpace.CreateFramePresentationMonitor</span><span class="sxs-lookup"><span data-stu-id="4007c-120">HolographicSpace.CreateFramePresentationMonitor</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)

[<span data-ttu-id="4007c-121">Windows.Perception.Spatial</span><span class="sxs-lookup"><span data-stu-id="4007c-121">Windows.Perception.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [<span data-ttu-id="4007c-122">Spatiallocation이. AbsoluteAngularAcceleration</span><span class="sxs-lookup"><span data-stu-id="4007c-122">SpatialLocation.AbsoluteAngularAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [<span data-ttu-id="4007c-123">Spatiallocation이. AbsoluteAngularAccelerationAxisAngle</span><span class="sxs-lookup"><span data-stu-id="4007c-123">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [<span data-ttu-id="4007c-124">Spatiallocation이. AbsoluteAngularVelocity</span><span class="sxs-lookup"><span data-stu-id="4007c-124">SpatialLocation.AbsoluteAngularVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [<span data-ttu-id="4007c-125">Spatiallocation이. AbsoluteAngularVelocityAxisAngle</span><span class="sxs-lookup"><span data-stu-id="4007c-125">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [<span data-ttu-id="4007c-126">Spatiallocation이. AbsoluteLinearAcceleration</span><span class="sxs-lookup"><span data-stu-id="4007c-126">SpatialLocation.AbsoluteLinearAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [<span data-ttu-id="4007c-127">Spatiallocation이. AbsoluteLinearVelocity</span><span class="sxs-lookup"><span data-stu-id="4007c-127">SpatialLocation.AbsoluteLinearVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [<span data-ttu-id="4007c-128">SpatialStageFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="4007c-128">SpatialStageFrameOfReference.Current</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - <span data-ttu-id="4007c-129">```nullptr```항상를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="4007c-129">Always returns ```nullptr```.</span></span>
* [<span data-ttu-id="4007c-130">SpatialStageFrameOfReference.RequestNewStageAsync</span><span class="sxs-lookup"><span data-stu-id="4007c-130">SpatialStageFrameOfReference.RequestNewStageAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
* [<span data-ttu-id="4007c-131">SpatialAnchor.RemovedByUser</span><span class="sxs-lookup"><span data-stu-id="4007c-131">SpatialAnchor.RemovedByUser</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [<span data-ttu-id="4007c-132">SpatialAnchorExporter. GetDefault</span><span class="sxs-lookup"><span data-stu-id="4007c-132">SpatialAnchorExporter.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - <span data-ttu-id="4007c-133">[2.0.9](holographic-remoting-version-history.md#v2.0.9)버전부터 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4007c-133">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="4007c-134">이전 버전에서는 ```nullptr```항상를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="4007c-134">On previous versions always returns ```nullptr```.</span></span> 
* [<span data-ttu-id="4007c-135">SpatialAnchorExporter</span><span class="sxs-lookup"><span data-stu-id="4007c-135">SpatialAnchorExporter.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - <span data-ttu-id="4007c-136">[2.0.9](holographic-remoting-version-history.md#v2.0.9)버전부터 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4007c-136">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="4007c-137">이전 버전에서 비동기 작업은 항상 ```SpatialPerceptionAccessStatus.DeniedBySystem```를 사용 하 여 완료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4007c-137">On previous versions the async operation always completed with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="4007c-138">SpatialAnchorTransferManager</span><span class="sxs-lookup"><span data-stu-id="4007c-138">SpatialAnchorTransferManager.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - <span data-ttu-id="4007c-139">비동기 작업은 항상 ```SpatialPerceptionAccessStatus.DeniedBySystem```를 사용 하 여 완료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4007c-139">Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="4007c-140">SpatialAnchorTransferManager.TryExportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="4007c-140">SpatialAnchorTransferManager.TryExportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - <span data-ttu-id="4007c-141">비동기 작업은 항상 ```false```를 사용 하 여 완료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4007c-141">Async operation always completes with ```false```.</span></span>
* [<span data-ttu-id="4007c-142">SpatialAnchorTransferManager.TryImportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="4007c-142">SpatialAnchorTransferManager.TryImportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - <span data-ttu-id="4007c-143">비동기 작업은 항상 ```nullptr```를 사용 하 여 완료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4007c-143">Async operation always completes with ```nullptr```.</span></span>

[<span data-ttu-id="4007c-144">Windows.UI.Input.Spatial</span><span class="sxs-lookup"><span data-stu-id="4007c-144">Windows.UI.Input.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [<span data-ttu-id="4007c-145">SpatialInteractionSource.TryCreateHandMeshObserver</span><span class="sxs-lookup"><span data-stu-id="4007c-145">SpatialInteractionSource.TryCreateHandMeshObserver</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [<span data-ttu-id="4007c-146">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span><span class="sxs-lookup"><span data-stu-id="4007c-146">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)

[<span data-ttu-id="4007c-147">Windows.Perception.Spatial.Preview</span><span class="sxs-lookup"><span data-stu-id="4007c-147">Windows.Perception.Spatial.Preview</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [<span data-ttu-id="4007c-148">SpatialGraphInteropPreview 노드</span><span class="sxs-lookup"><span data-stu-id="4007c-148">SpatialGraphInteropPreview.CreateLocatorForNode</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [<span data-ttu-id="4007c-149">SpatialGraphInteropPreview.TryCreateFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="4007c-149">SpatialGraphInteropPreview.TryCreateFrameOfReference</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)
* [<span data-ttu-id="4007c-150">SpatialInteractionSource</span><span class="sxs-lookup"><span data-stu-id="4007c-150">SpatialInteractionSource.Controller</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)

## <a name="see-also"></a><span data-ttu-id="4007c-151">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4007c-151">See Also</span></span>
* [<span data-ttu-id="4007c-152">Holographic 원격 버전 기록</span><span class="sxs-lookup"><span data-stu-id="4007c-152">Holographic Remoting Version History</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="4007c-153">Holographic 원격 호스트 앱 작성</span><span class="sxs-lookup"><span data-stu-id="4007c-153">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="4007c-154">사용자 지정 Holographic Remoting 플레이어 앱 작성</span><span class="sxs-lookup"><span data-stu-id="4007c-154">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="4007c-155">홀로그램 원격 소프트웨어 사용 조건</span><span class="sxs-lookup"><span data-stu-id="4007c-155">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="4007c-156">Microsoft 개인 정보 취급 방침</span><span class="sxs-lookup"><span data-stu-id="4007c-156">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
