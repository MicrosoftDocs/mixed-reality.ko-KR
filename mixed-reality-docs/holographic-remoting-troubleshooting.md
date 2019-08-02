---
title: Holographic 원격 문제 해결 및 제한 사항
description: HoloLens 2의 Holographic Remoting에 대 한 문제 해결 단계입니다.
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 08/01/2019
ms.topic: article
keywords: Windows Mixed Reality, holograms, holographic remoting, 원격 렌더링, 네트워크 렌더링, HoloLens, 원격 holograms, 문제 해결, 도움말
ms.openlocfilehash: 86b6979dbfc9b514b3af13ebdcc3d3ece17e6335
ms.sourcegitcommit: ca949efe0279995a376750d89e23d7123eb44846
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68718147"
---
# <a name="holographic-remoting-troubleshooting"></a><span data-ttu-id="d12c6-104">Holographic 원격 문제 해결</span><span class="sxs-lookup"><span data-stu-id="d12c6-104">Holographic Remoting troubleshooting</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d12c6-105">이 지침은 HoloLens 2의 Holographic Remoting에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d12c6-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="spectre-mitigated-libraries-not-found"></a><span data-ttu-id="d12c6-106">스펙터 완화 라이브러리를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d12c6-106">Spectre mitigated libraries not found.</span></span>

<span data-ttu-id="d12c6-107">Holographic Remoting 샘플 앱은 릴리스 구성에서/Qspectre (스펙터 완화)를 사용 하도록 설정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="d12c6-107">Holographic Remoting sample apps have Spectre mitigation (/Qspectre) enabled in Release configuration.</span></span>

<span data-ttu-id="d12c6-108">' Vccorlib. n a l e '을 열 수 없다는 심각한 링커 오류가 발생 하는 경우 Visual Studio 워크 로드에 스펙터 완화 된 라이브러리가 포함 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d12c6-108">If you get a fatal linker error which states that 'vccorlib.lib' cannot be opened, make sure that your Visual Studio Workload includes the Spectre mitigated libraries.</span></span> <span data-ttu-id="d12c6-109">자세한 내용은 https://aka.ms/Ofhn4c 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d12c6-109">See https://aka.ms/Ofhn4c for more information.</span></span>

# <a name="limitations"></a><span data-ttu-id="d12c6-110">제한 사항</span><span class="sxs-lookup"><span data-stu-id="d12c6-110">Limitations</span></span>

<span data-ttu-id="d12c6-111">다음 api는 현재 HoloLens 2에 대 한 Holographic 원격을 사용 하는 경우 지원 되지 ```ERROR_NOT_SUPPORTED``` 않으며 별도로 명시 하지 않는 한 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="d12c6-111">The following APIs are currently **not** supported when using Holographic Remoting for HoloLens 2 and will raises an ```ERROR_NOT_SUPPORTED``` error unless otherwise stated:</span></span>

[<span data-ttu-id="d12c6-112">Windows.Graphics.Holographic</span><span class="sxs-lookup"><span data-stu-id="d12c6-112">Windows.Graphics.Holographic</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic)

* [<span data-ttu-id="d12c6-113">HolographicCamera 구성</span><span class="sxs-lookup"><span data-stu-id="d12c6-113">HolographicCamera.ViewConfiguration</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
* [<span data-ttu-id="d12c6-114">HolographicCameraPose.OverrideProjectionTransform</span><span class="sxs-lookup"><span data-stu-id="d12c6-114">HolographicCameraPose.OverrideProjectionTransform</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [<span data-ttu-id="d12c6-115">HolographicCameraPose</span><span class="sxs-lookup"><span data-stu-id="d12c6-115">HolographicCameraPose.OverrideViewport</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [<span data-ttu-id="d12c6-116">HolographicCameraPose. OverrideViewTransform</span><span class="sxs-lookup"><span data-stu-id="d12c6-116">HolographicCameraPose.OverrideViewTransform</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
* <span data-ttu-id="d12c6-117">[HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) 는 실패 하지 않지만 깊이 버퍼는 원격이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="d12c6-117">[HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) - Does not fail but depth buffer will not be remoted.</span></span>
* [<span data-ttu-id="d12c6-118">HolographicDisplay.TryGetViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="d12c6-118">HolographicDisplay.TryGetViewConfiguration</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
* [<span data-ttu-id="d12c6-119">HolographicSpace.CreateFramePresentationMonitor</span><span class="sxs-lookup"><span data-stu-id="d12c6-119">HolographicSpace.CreateFramePresentationMonitor</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)

[<span data-ttu-id="d12c6-120">Windows.Perception.Spatial</span><span class="sxs-lookup"><span data-stu-id="d12c6-120">Windows.Perception.Spatial</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial)

* [<span data-ttu-id="d12c6-121">Spatiallocation이. AbsoluteAngularAcceleration</span><span class="sxs-lookup"><span data-stu-id="d12c6-121">SpatialLocation.AbsoluteAngularAcceleration</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [<span data-ttu-id="d12c6-122">Spatiallocation이. AbsoluteAngularAccelerationAxisAngle</span><span class="sxs-lookup"><span data-stu-id="d12c6-122">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [<span data-ttu-id="d12c6-123">Spatiallocation이. AbsoluteAngularVelocity</span><span class="sxs-lookup"><span data-stu-id="d12c6-123">SpatialLocation.AbsoluteAngularVelocity</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [<span data-ttu-id="d12c6-124">Spatiallocation이. AbsoluteAngularVelocityAxisAngle</span><span class="sxs-lookup"><span data-stu-id="d12c6-124">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [<span data-ttu-id="d12c6-125">Spatiallocation이. AbsoluteLinearAcceleration</span><span class="sxs-lookup"><span data-stu-id="d12c6-125">SpatialLocation.AbsoluteLinearAcceleration</span></span>](https://docs.microsoft.com/is-is/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [<span data-ttu-id="d12c6-126">Spatiallocation이. AbsoluteLinearVelocity</span><span class="sxs-lookup"><span data-stu-id="d12c6-126">SpatialLocation.AbsoluteLinearVelocity</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* <span data-ttu-id="d12c6-127">[SpatialStageFrameOfReference](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialstageframeofreference.current) -항상를 반환 ```nullptr```합니다.</span><span class="sxs-lookup"><span data-stu-id="d12c6-127">[SpatialStageFrameOfReference.Current](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialstageframeofreference.current) - Always returns ```nullptr```.</span></span>
* [<span data-ttu-id="d12c6-128">SpatialStageFrameOfReference.RequestNewStageAsync</span><span class="sxs-lookup"><span data-stu-id="d12c6-128">SpatialStageFrameOfReference.RequestNewStageAsync</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
* [<span data-ttu-id="d12c6-129">SpatialAnchor.RemovedByUser</span><span class="sxs-lookup"><span data-stu-id="d12c6-129">SpatialAnchor.RemovedByUser</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* <span data-ttu-id="d12c6-130">[SpatialAnchorExporter-항상를 반환 ```nullptr```합니다.](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)</span><span class="sxs-lookup"><span data-stu-id="d12c6-130">[SpatialAnchorExporter.GetDefault](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
) - Always returns ```nullptr```.</span></span>
* <span data-ttu-id="d12c6-131">[SpatialAnchorExporter 작업은 항상로 ```SpatialPerceptionAccessStatus.DeniedBySystem```완료 됩니다.](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)</span><span class="sxs-lookup"><span data-stu-id="d12c6-131">[SpatialAnchorExporter.RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
) - Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* <span data-ttu-id="d12c6-132">[SpatialAnchorTransferManager](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync) 작업은 항상로 ```SpatialPerceptionAccessStatus.DeniedBySystem```완료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d12c6-132">[SpatialAnchorTransferManager.RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync) - Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* <span data-ttu-id="d12c6-133">[SpatialAnchorTransferManager](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_) 작업은 항상로 ```false```완료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d12c6-133">[SpatialAnchorTransferManager.TryExportAnchorsAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_) - Async operation always completes with ```false```.</span></span>
* <span data-ttu-id="d12c6-134">[SpatialAnchorTransferManager 작업은 항상로 ```nullptr```완료 됩니다.](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)</span><span class="sxs-lookup"><span data-stu-id="d12c6-134">[SpatialAnchorTransferManager.TryImportAnchorsAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
) - Async operation always completes with ```nullptr```.</span></span>

[<span data-ttu-id="d12c6-135">Windows.UI.Input.Spatial</span><span class="sxs-lookup"><span data-stu-id="d12c6-135">Windows.UI.Input.Spatial</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial)

* [<span data-ttu-id="d12c6-136">SpatialInteractionSource.TryCreateHandMeshObserver</span><span class="sxs-lookup"><span data-stu-id="d12c6-136">SpatialInteractionSource.TryCreateHandMeshObserver</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [<span data-ttu-id="d12c6-137">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span><span class="sxs-lookup"><span data-stu-id="d12c6-137">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)

[<span data-ttu-id="d12c6-138">Windows.Perception.Spatial.Preview</span><span class="sxs-lookup"><span data-stu-id="d12c6-138">Windows.Perception.Spatial.Preview</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.preview)

* [<span data-ttu-id="d12c6-139">SpatialGraphInteropPreview 노드</span><span class="sxs-lookup"><span data-stu-id="d12c6-139">SpatialGraphInteropPreview.CreateLocatorForNode</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [<span data-ttu-id="d12c6-140">SpatialGraphInteropPreview.TryCreateFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="d12c6-140">SpatialGraphInteropPreview.TryCreateFrameOfReference</span></span>](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)

## <a name="see-also"></a><span data-ttu-id="d12c6-141">관련 항목</span><span class="sxs-lookup"><span data-stu-id="d12c6-141">See Also</span></span>
* [<span data-ttu-id="d12c6-142">Holographic 원격 호스트 앱 작성</span><span class="sxs-lookup"><span data-stu-id="d12c6-142">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="d12c6-143">사용자 지정 Holographic Remoting 플레이어 앱 작성</span><span class="sxs-lookup"><span data-stu-id="d12c6-143">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="d12c6-144">Holographic 원격 소프트웨어 사용 조건</span><span class="sxs-lookup"><span data-stu-id="d12c6-144">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="d12c6-145">Microsoft 개인 정보 취급 방침</span><span class="sxs-lookup"><span data-stu-id="d12c6-145">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)