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
# <a name="holographic-remoting-troubleshooting"></a>Holographic 원격 문제 해결

> [!IMPORTANT]
> 이 지침은 HoloLens 2의 Holographic Remoting에만 적용 됩니다.

## <a name="spectre-mitigated-libraries-not-found"></a>스펙터 완화 라이브러리를 찾을 수 없습니다.

Holographic Remoting 샘플 앱은 릴리스 구성에서/Qspectre (스펙터 완화)를 사용 하도록 설정 했습니다.

' Vccorlib. n a l e '을 열 수 없다는 심각한 링커 오류가 발생 하는 경우 Visual Studio 워크 로드에 스펙터 완화 된 라이브러리가 포함 되어 있는지 확인 합니다. 자세한 내용은 https://aka.ms/Ofhn4c 를 참조하세요.

# <a name="limitations"></a>제한 사항

다음 api는 현재 HoloLens 2에 대 한 Holographic 원격을 사용 하는 경우 지원 되지 ```ERROR_NOT_SUPPORTED``` 않으며 별도로 명시 하지 않는 한 오류가 발생 합니다.

[Windows.Graphics.Holographic](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic)

* [HolographicCamera 구성](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
* [HolographicCameraPose.OverrideProjectionTransform](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [HolographicCameraPose](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [HolographicCameraPose. OverrideViewTransform](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
* [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) 는 실패 하지 않지만 깊이 버퍼는 원격이 아닙니다.
* [HolographicDisplay.TryGetViewConfiguration](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
* [HolographicSpace.CreateFramePresentationMonitor](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)

[Windows.Perception.Spatial](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial)

* [Spatiallocation이. AbsoluteAngularAcceleration](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [Spatiallocation이. AbsoluteAngularAccelerationAxisAngle](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [Spatiallocation이. AbsoluteAngularVelocity](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [Spatiallocation이. AbsoluteAngularVelocityAxisAngle](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [Spatiallocation이. AbsoluteLinearAcceleration](https://docs.microsoft.com/is-is/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [Spatiallocation이. AbsoluteLinearVelocity](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [SpatialStageFrameOfReference](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialstageframeofreference.current) -항상를 반환 ```nullptr```합니다.
* [SpatialStageFrameOfReference.RequestNewStageAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
* [SpatialAnchor.RemovedByUser](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [SpatialAnchorExporter-항상를 반환 ```nullptr```합니다.](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
* [SpatialAnchorExporter 작업은 항상로 ```SpatialPerceptionAccessStatus.DeniedBySystem```완료 됩니다.](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
* [SpatialAnchorTransferManager](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync) 작업은 항상로 ```SpatialPerceptionAccessStatus.DeniedBySystem```완료 됩니다.
* [SpatialAnchorTransferManager](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_) 작업은 항상로 ```false```완료 됩니다.
* [SpatialAnchorTransferManager 작업은 항상로 ```nullptr```완료 됩니다.](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)

[Windows.UI.Input.Spatial](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial)

* [SpatialInteractionSource.TryCreateHandMeshObserver](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [SpatialInteractionSource.TryCreateHandMeshObserverAsync](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)

[Windows.Perception.Spatial.Preview](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.preview)

* [SpatialGraphInteropPreview 노드](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [SpatialGraphInteropPreview.TryCreateFrameOfReference](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)

## <a name="see-also"></a>관련 항목
* [Holographic 원격 호스트 앱 작성](holographic-remoting-create-host.md)
* [사용자 지정 Holographic Remoting 플레이어 앱 작성](holographic-remoting-create-player.md)
* [Holographic 원격 소프트웨어 사용 조건](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 개인 정보 취급 방침](https://go.microsoft.com/fwlink/?LinkId=521839)