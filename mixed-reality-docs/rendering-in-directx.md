---
title: DirectX에서 렌더링
description: Windows Mixed Reality의 holographic 렌더링에 대해 설명 합니다.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, holograms, 렌더링, 3D 그래픽, HolographicFrame, 렌더링 루프, 업데이트 루프, 연습, 샘플 코드, Direct3D
ms.openlocfilehash: 6b2e2dca9115d7093e94019d5ed91201f6ee3424
ms.sourcegitcommit: f4812e1312c4751a22a2de56771c475b22a4ba24
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/09/2019
ms.locfileid: "74940871"
---
# <a name="rendering-in-directx"></a>DirectX에서 렌더링

Windows Mixed Reality는 DirectX를 기반으로 하 여 사용자를 위한 풍부한 3D 그래픽 환경을 생성 합니다. 렌더링 추상화는 DirectX 바로 위에 있으며 시스템에서 예측 하는 것 처럼 holographic 장면에서 하나 이상의 관찰자의 위치와 방향에 대 한 앱 이유를 허용 합니다. 그러면 개발자는 각 카메라를 기준으로 holograms을 찾을 수 있습니다. 그러면 사용자가 이동할 때 다양 한 공간 좌표계에서 앱이 이러한 holograms를 렌더링할 수 있습니다.

참고:이 연습에서는 Direct3D 11의 holographic 렌더링에 대해 설명 합니다. Direct3D 12 Windows Mixed Reality 앱 템플릿은 혼합 현실 앱 템플릿 확장과 함께 제공 됩니다.

## <a name="update-for-the-current-frame"></a>현재 프레임에 대 한 업데이트

Holograms에 대 한 응용 프로그램 상태를 업데이트 하려면 앱에서 다음을 수행 합니다.
* 디스플레이 관리 시스템에서 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> 를 가져옵니다.
* 렌더링이 완료 되 면 카메라 보기가 표시 되는 현재 예측으로 장면을 업데이트 합니다. Holographic 장면에는 카메라를 두 개 이상 사용할 수 있습니다.

Holographic 카메라 보기로 렌더링 하려면 프레임당 한 번, 앱에서 다음을 수행 합니다.
* 각 카메라에 대해 시스템의 카메라 보기 및 프로젝션 매트릭스를 사용 하 여 현재 프레임에 대 한 장면을 렌더링 합니다.

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a>새 holographic 프레임을 만들고 해당 예측을 가져옵니다.

<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> 에는 현재 프레임을 업데이트 하 고 렌더링 하기 위해 앱에 필요한 정보가 있습니다. 앱은 **Createnextframe** 메서드를 호출 하 여 각 새 프레임을 시작 합니다. 이 메서드가 호출 되 면 사용 가능한 최신 센서 데이터를 사용 하 여 예측을 수행 하 고 **currentprediction** 개체에 캡슐화 합니다.

새 프레임 개체는 특정 시간 동안만 유효 하므로 렌더링 된 각 프레임에 사용 해야 합니다. **Currentprediction** 속성은 카메라 위치와 같은 정보를 포함 합니다. 이 정보는 프레임이 사용자에 게 표시 될 것으로 예상 되는 정확한 시점에 추정 됩니다.

다음 코드는 **Appmain:: Update**에서 발췌 한 것 됩니다.

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a>카메라 업데이트 처리

백 버퍼는 프레임에서 프레임으로 변경 될 수 있습니다. 앱은 각 카메라에 대해 백 버퍼의 유효성을 검사 하 고 필요에 따라 리소스 뷰 및 깊이 버퍼를 해제 하 고 다시 만들어야 합니다. 예측의 포즈 집합은 현재 프레임에서 사용 되는 카메라의 신뢰할 수 있는 목록입니다. 일반적으로이 목록을 사용 하 여 카메라 집합을 반복 합니다.

**Appmain:: Update**에서:

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

From **DeviceResources:: EnsureCameraResources**:

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a>렌더링을 위한 기반으로 사용할 좌표계를 가져옵니다.

Windows Mixed Reality를 사용 하면 앱에서 실제 세계의 위치를 추적 하는 연결 된 참조 프레임, 고정 참조 프레임 등 필요에 따라 다양 한 [좌표계](coordinate-systems-in-directx.md) 를 만들 수 있습니다. 그러면 앱이 이러한 좌표계를 사용 하 여 각 프레임 holograms를 렌더링 하는 위치를 지정할 수 있습니다. API에서 좌표를 요청 하는 경우 항상 해당 좌표를 표시 하려는 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> 를 전달 합니다.

**Appmain:: Update**에서:

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

그런 다음 이러한 좌표계를 사용 하 여 장면에서 콘텐츠를 렌더링할 때 스테레오 뷰 매트릭스를 생성할 수 있습니다.

From **CameraResources:: UpdateViewProjectionBuffer**:

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a>응시 및 제스처 입력 처리

[응시](gaze-in-directx.md) 및 [직접](hands-and-motion-controllers-in-directx.md) 입력은 시간 기반이 아니므로 **sttimer** 함수에서 업데이트할 필요가 없습니다. 그러나이 입력은 앱이 각 프레임을 확인 해야 하는 항목입니다.

### <a name="process-time-based-updates"></a>프로세스 시간 기반 업데이트

실시간 렌더링 앱에는 시간 기반 업데이트를 처리 하는 방법이 필요 합니다. Windows Holographic 앱 템플릿에서 **Sttimer** 구현을 통해이 작업을 수행 하는 방법을 제공 합니다. 이는 DirectX 11 UWP 앱 템플릿에서 제공 하는 Sttimer와 유사 하므로, 해당 템플릿을 이미 살펴본 경우에는 친숙 한 부분에 있어야 합니다. 이 Sttimer 샘플 도우미 클래스는 고정 된 시간 단계 업데이트 및 가변 시간 단계 업데이트를 제공할 수 있으며 기본 모드는 가변 시간 단계입니다.

Holographic 렌더링의 경우 타이머 함수에 너무 많이 배치 하지 않도록 특별히 선택 했습니다. 이는 고정 된 시간 단계가 되도록 구성할 수 있습니다 .이 경우 일부 프레임에 대해 프레임당 두 번 이상 호출 될 수 있으며, holographic 데이터 업데이트는 프레임당 한 번만 수행 하면 됩니다.


**Appmain:: Update**에서:

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a>좌표계에서 holograms 위치 및 회전

단일 좌표계에서 작업 하는 경우 템플릿이 **SpatialStationaryReferenceFrame**를 사용 하 여 작업 하는 경우이 프로세스는 3d 그래픽에서 다른 방법으로 사용 되는 것과는 다릅니다. 여기서는 큐브를 회전 하 고 고정 좌표계의 위치를 기준으로 모델 매트릭스를 설정 합니다.

**SpinningCubeRenderer:: Update**에서:

```cpp
// Rotate the cube.
// Convert degrees to radians, then convert seconds to rotation angle.
const float    radiansPerSecond = XMConvertToRadians(m_degreesPerSecond);
const double   totalRotation = timer.GetTotalSeconds() * radiansPerSecond;
const float    radians = static_cast<float>(fmod(totalRotation, XM_2PI));
const XMMATRIX modelRotation = XMMatrixRotationY(-radians);

// Position the cube.
const XMMATRIX modelTranslation = XMMatrixTranslationFromVector(XMLoadFloat3(&m_position));

// Multiply to get the transform matrix.
// Note that this transform does not enforce a particular coordinate system. The calling
// class is responsible for rendering this content in a consistent manner.
const XMMATRIX modelTransform = XMMatrixMultiply(modelRotation, modelTranslation);

// The view and projection matrices are provided by the system; they are associated
// with holographic cameras, and updated on a per-camera basis.
// Here, we provide the model transform for the sample hologram. The model transform
// matrix is transposed to prepare it for the shader.
XMStoreFloat4x4(&m_modelConstantBufferData.model, XMMatrixTranspose(modelTransform));
```

**고급 시나리오에 대 한 참고 사항:** 회전 하는 큐브는 단일 참조 프레임 안에 홀로그램을 배치 하는 방법에 대 한 매우 간단한 예입니다. 동일한 렌더링 된 프레임에서 동시에 [여러 SpatialCoordinateSystems를 사용할](coordinate-systems-in-directx.md) 수도 있습니다.

### <a name="update-constant-buffer-data"></a>상수 버퍼 데이터 업데이트

콘텐츠에 대 한 모델 변환은 평소와 같이 업데이트 됩니다. 이제 렌더링할 좌표계에 대해 유효한 변환을 계산 합니다.

**SpinningCubeRenderer:: Update**에서:

```cpp
// Update the model transform buffer for the hologram.
context->UpdateSubresource(
    m_modelConstantBuffer.Get(),
    0,
    nullptr,
    &m_modelConstantBufferData,
    0,
    0
);
```

보기 및 프로젝션 변환에 대 한 자세한 정보 최상의 결과를 얻으려면 그리기 호출에 대해 거의 준비가 될 때까지 대기 하 고 싶습니다.

## <a name="render-the-current-frame"></a>현재 프레임을 렌더링 합니다.

Windows Mixed Reality에서 렌더링 하는 것은 2D 모노 디스플레이에서 렌더링 하는 것과 크게 다르지 않지만 몇 가지 차이점을 고려해 야 합니다.
* Holographic 프레임 예측은 중요 합니다. 프레임이 표시 될 때 예측에 더 가깝습니다. holograms이 더 좋아집니다.
* Windows Mixed Reality는 카메라 보기를 제어 합니다. Holographic 프레임이 나중에 표시 되기 때문에 각 항목에 렌더링 해야 합니다.
* 인스턴스 그리기를 렌더링 대상 배열에 사용 하 여 스테레오 렌더링을 수행 하는 것이 좋습니다. Holographic 앱 템플릿은 렌더링 대상 뷰를 **Texture2DArray**에 사용 하는 렌더링 대상 배열에 대해 인스턴스화된 그리기의 권장 되는 방법을 사용 합니다.
* 스테레오 인스턴스를 사용 하지 않고 렌더링 하려면 각각 시스템에서 앱에 제공 되는 **Texture2DArray** 의 두 조각 중 하나를 참조 하는 배열 없는 RenderTargetViews (각 눈 마다 하나씩)를 만들어야 합니다. 이 방법은 일반적으로 인스턴스를 사용 하는 것 보다 훨씬 느리므로 권장 되지 않습니다.

### <a name="get-an-updated-holographicframe-prediction"></a>업데이트 된 HolographicFrame 예측 가져오기

프레임 예측을 업데이트 하면 이미지 안정화의 효율성을 향상 시키고 예측 사이의 시간 및 프레임을 사용자에 게 표시 하는 시간 때문에 holograms를 보다 정확 하 게 배치할 수 있습니다. 프레임 예측은 렌더링 직전에 업데이트 하는 것이 좋습니다.

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a>각 카메라에 렌더링

예측에서 카메라의 집합에 대 한 루프를 실행 하 고이 집합의 각 카메라에 렌더링 합니다.

**렌더링 패스 설정**

Windows Mixed Reality에서는 stereoscopic 렌더링을 사용 하 여 깊이의 효과를 높이고 stereoscopically를 렌더링 하므로 왼쪽 및 오른쪽 디스플레이가 모두 활성화 됩니다. Stereoscopic 렌더링을 사용 하는 경우 두 표시 간의 오프셋이 있습니다. 즉, 두뇌는 실제 깊이로 조정할 수 있습니다. 이 섹션에서는 Windows Holographic 앱 템플릿의 코드를 사용 하 여 인스턴스를 사용 하는 stereoscopic 렌더링에 대해 설명 합니다.

각 카메라에는 자체 렌더링 대상 (백 버퍼) 및 뷰 및 프로젝션 매트릭스가 holographic 공간으로 포함 됩니다. 앱은 카메라 단위로 깊이 버퍼와 같은 다른 카메라 기반 리소스를 만들어야 합니다. Windows Holographic 앱 템플릿에서 이러한 리소스를 DX:: CameraResources에 함께 묶는 도우미 클래스를 제공 합니다. 렌더링 대상 뷰를 설정 하 여 시작 합니다.

**Appmain:: Render**에서:

```cpp
// This represents the device-based resources for a HolographicCamera.
DX::CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();

// Get the device context.
const auto context = m_deviceResources->GetD3DDeviceContext();
const auto depthStencilView = pCameraResources->GetDepthStencilView();

// Set render targets to the current holographic camera.
ID3D11RenderTargetView *const targets[1] =
    { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, depthStencilView);

// Clear the back buffer and depth stencil view.
if (m_canGetHolographicDisplayForCamera &&
    cameraPose.HolographicCamera().Display().IsOpaque())
{
    context->ClearRenderTargetView(targets[0], DirectX::Colors::CornflowerBlue);
}
else
{
    context->ClearRenderTargetView(targets[0], DirectX::Colors::Transparent);
}
context->ClearDepthStencilView(
    depthStencilView, D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);
```

**예측을 사용 하 여 카메라에 대 한 보기 및 프로젝션 매트릭스 가져오기**

각 holographic 카메라에 대 한 보기 및 프로젝션 매트릭스가 모든 프레임에서 변경 됩니다. 각 holographic 카메라에 대해 상수 버퍼의 데이터를 새로 고칩니다. 예측을 업데이트 한 후와 해당 카메라에 대 한 그리기 호출을 수행 하기 전에이 작업을 수행 합니다.

**Appmain:: Render**에서:

```cpp
// The view and projection matrices for each holographic camera will change
// every frame. This function refreshes the data in the constant buffer for
// the holographic camera indicated by cameraPose.
if (m_stationaryReferenceFrame)
{
    pCameraResources->UpdateViewProjectionBuffer(
        m_deviceResources, cameraPose, m_stationaryReferenceFrame.CoordinateSystem());
}

// Attach the view/projection constant buffer for this camera to the graphics pipeline.
bool cameraActive = pCameraResources->AttachViewProjectionBuffer(m_deviceResources);
```

여기서는 카메라 포즈에서 매트릭스를 가져오는 방법을 보여 줍니다. 이 프로세스를 진행 하는 동안 카메라의 현재 뷰포트도 가져옵니다. 좌표계를 제공 하는 방법에 유의 하세요 .이 좌표계는 응시를 이해 하는 데 사용한 것과 동일한 좌표계 이며 회전 하는 큐브를 배치 하는 데 사용 하는 것과 동일 합니다.


From **CameraResources:: UpdateViewProjectionBuffer**:

```cpp
// The system changes the viewport on a per-frame basis for system optimizations.
auto viewport = cameraPose.Viewport();
m_d3dViewport = CD3D11_VIEWPORT(
    viewport.X,
    viewport.Y,
    viewport.Width,
    viewport.Height
);

// The projection transform for each frame is provided by the HolographicCameraPose.
HolographicStereoTransform cameraProjectionTransform = cameraPose.ProjectionTransform();

// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);

// If TryGetViewTransform returns a null pointer, that means the pose and coordinate
// system cannot be understood relative to one another; content cannot be rendered
// in this coordinate system for the duration of the current frame.
// This usually means that positional tracking is not active for the current frame, in
// which case it is possible to use a SpatialLocatorAttachedFrameOfReference to render
// content that is not world-locked instead.
DX::ViewProjectionConstantBuffer viewProjectionConstantBufferData;
bool viewTransformAcquired = viewTransformContainer != nullptr;
if (viewTransformAcquired)
{
    // Otherwise, the set of view transforms can be retrieved.
    HolographicStereoTransform viewCoordinateSystemTransform = viewTransformContainer.Value();

    // Update the view matrices. Holographic cameras (such as Microsoft HoloLens) are
    // constantly moving relative to the world. The view matrices need to be updated
    // every frame.
    XMStoreFloat4x4(
        &viewProjectionConstantBufferData.viewProjection[0],
        XMMatrixTranspose(XMLoadFloat4x4(&viewCoordinateSystemTransform.Left) *
            XMLoadFloat4x4(&cameraProjectionTransform.Left))
    );
    XMStoreFloat4x4(
        &viewProjectionConstantBufferData.viewProjection[1],
        XMMatrixTranspose(XMLoadFloat4x4(&viewCoordinateSystemTransform.Right) *
            XMLoadFloat4x4(&cameraProjectionTransform.Right))
    );
}
```

각 프레임은 뷰포트를 설정 해야 합니다. 꼭 짓 점 셰이더 (최소)는 일반적으로 뷰/프로젝션 데이터에 액세스할 수 있어야 합니다.


From **CameraResources:: AttachViewProjectionBuffer**:

```cpp
// Set the viewport for this camera.
context->RSSetViewports(1, &m_d3dViewport);

// Send the constant buffer to the vertex shader.
context->VSSetConstantBuffers(
    1,
    1,
    m_viewProjectionConstantBuffer.GetAddressOf()
);
```

**카메라 백 버퍼에 렌더링 하 고 깊이 버퍼를 커밋합니다**.

좌표계가 과정이 되지 않는 경우 (예: 추적이 중단 된 경우) 앱에서 해당 프레임에 대해 렌더링할 수 없기 때문에 뷰/프로젝션 데이터를 사용 하기 전에 **TryGetViewTransform** 이 성공 했는지 확인 하는 것이 좋습니다. **CameraResources** 클래스가 성공적인 업데이트를 나타내는 경우에만이 템플릿은 회전 하는 큐브에서 **렌더링** 을 호출 합니다.

개발자 또는 사용자가 전 세계에 holograms을 유지 하기 위해 Windows Mixed Reality에는 [이미지 안정화](hologram-stability.md)기능이 포함 되어 있습니다. 이미지 안정화를 사용 하면 렌더링 파이프라인에서 내재 된 대기 시간을 숨겨 사용자에 게 가장 적합 한 holographic 환경을 보장할 수 있습니다. 포커스 지점을 지정 하 여 이미지 안정화를 향상 시킬 수도 있고, 실시간으로 최적화 된 이미지를 계산 하기 위한 깊이 버퍼가 제공 될 수도 있습니다.

최상의 결과를 위해 앱은 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API를 사용 하 여 깊이 버퍼를 제공 해야 합니다. Windows Mixed Reality는 깊이 버퍼의 기 하 도형 정보를 사용 하 여 이미지 안정화를 실시간으로 최적화할 수 있습니다. Windows Holographic 앱 템플릿은 기본적으로 응용 프로그램의 깊이 버퍼를 커밋 하 여 홀로그램 안정성을 최적화 하도록 지원 합니다.

**Appmain:: Render**에서:

```cpp
// Only render world-locked content when positional tracking is active.
if (cameraActive)
{
    // Draw the sample hologram.
    m_spinningCubeRenderer->Render();
    if (m_canCommitDirect3D11DepthBuffer)
    {
        // On versions of the platform that support the CommitDirect3D11DepthBuffer API, we can 
        // provide the depth buffer to the system, and it will use depth information to stabilize 
        // the image at a per-pixel level.
        HolographicCameraRenderingParameters renderingParameters =
            holographicFrame.GetRenderingParameters(cameraPose);
        
        IDirect3DSurface interopSurface =
            DX::CreateDepthTextureInteropObject(pCameraResources->GetDepthStencilTexture2D());

        // Calling CommitDirect3D11DepthBuffer causes the system to queue Direct3D commands to 
        // read the depth buffer. It will then use that information to stabilize the image as
        // the HolographicFrame is presented.
        renderingParameters.CommitDirect3D11DepthBuffer(interopSurface);
    }
}
```

>[!NOTE]
>Windows는 GPU에서 깊이 질감을 처리 하므로 깊이 버퍼를 셰이더 리소스로 사용할 수 있어야 합니다. 사용자가 만든 ID3D11Texture2D는 형식이 아닌 형식 이어야 하며 셰이더 리소스 뷰로 바인딩되어야 합니다. 이미지 안정화를 위해 커밋될 수 있는 깊이 질감을 만드는 방법에 대 한 예제는 다음과 같습니다.

**CommitDirect3D11DepthBuffer에 대 한 깊이 버퍼 리소스 생성**코드:

```cpp
// Create a depth stencil view for use with 3D rendering if needed.
CD3D11_TEXTURE2D_DESC depthStencilDesc(
    DXGI_FORMAT_R16_TYPELESS,
    static_cast<UINT>(m_d3dRenderTargetSize.Width),
    static_cast<UINT>(m_d3dRenderTargetSize.Height),
    m_isStereo ? 2 : 1, // Create two textures when rendering in stereo.
    1, // Use a single mipmap level.
    D3D11_BIND_DEPTH_STENCIL | D3D11_BIND_SHADER_RESOURCE
);

winrt::check_hresult(
    device->CreateTexture2D(
        &depthStencilDesc,
        nullptr,
        &m_d3dDepthStencil
    ));

CD3D11_DEPTH_STENCIL_VIEW_DESC depthStencilViewDesc(
    m_isStereo ? D3D11_DSV_DIMENSION_TEXTURE2DARRAY : D3D11_DSV_DIMENSION_TEXTURE2D,
    DXGI_FORMAT_D16_UNORM
);
winrt::check_hresult(
    device->CreateDepthStencilView(
        m_d3dDepthStencil.Get(),
        &depthStencilViewDesc,
        &m_d3dDepthStencilView
    ));
```

**Holographic 내용 그리기**

Windows Holographic 앱 템플릿은 인스턴스 기 하 도형을 크기 2의 Texture2DArray로 그리는 권장 기법을 사용 하 여 스테레오에서 콘텐츠를 렌더링 합니다. 이에 대 한 인스턴스 및 Windows Mixed Reality에서 작동 하는 방식을 살펴보겠습니다.

From **SpinningCubeRenderer:: Render**:

```cpp
// Draw the objects.
context->DrawIndexedInstanced(
    m_indexCount,   // Index count per instance.
    2,              // Instance count.
    0,              // Start index location.
    0,              // Base vertex location.
    0               // Start instance location.
);
```

각 인스턴스는 상수 버퍼에서 다른 뷰/프로젝션 행렬에 액세스 합니다. 다음은 두 행렬의 배열인 상수 버퍼 구조입니다.

Hlsl에서 **VPRTVertexShader hlsl**에 포함 된 **VertexShaderShared**.

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

각 픽셀에 대해 렌더링 대상 배열 인덱스를 설정 해야 합니다. 다음 코드 조각에서 viewId는 **SV_RenderTargetArrayIndex** 의미 체계에 매핑됩니다. 이를 위해서는 선택적 Direct3D 11.3 기능을 지원 해야 합니다 .이 기능을 사용 하면 모든 셰이더 단계에서 렌더링 대상 배열 인덱스 의미 체계를 설정할 수 있습니다.

From **VPRTVertexShader. hlsl**:

```HLSL    
// Per-vertex data passed to the geometry shader.
struct VertexShaderOutput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;

    // The render target array index is set here in the vertex shader.
    uint        viewId  : SV_RenderTargetArrayIndex;
};
```

Hlsl에서 **VPRTVertexShader hlsl**에 포함 된 **VertexShaderShared**.

```HLSL
// Per-vertex data used as input to the vertex shader.
struct VertexShaderInput
{
    min16float3 pos     : POSITION;
    min16float3 color   : COLOR0;
    uint        instId  : SV_InstanceID;
};

// Simple shader to do vertex processing on the GPU.
VertexShaderOutput main(VertexShaderInput input)
{
    VertexShaderOutput output;
    float4 pos = float4(input.pos, 1.0f);

    // Note which view this vertex has been sent to. Used for matrix lookup.
    // Taking the modulo of the instance ID allows geometry instancing to be used
    // along with stereo instanced drawing; in that case, two copies of each 
    // instance would be drawn, one for left and one for right.
    int idx = input.instId % 2;

    // Transform the vertex position into world space.
    pos = mul(pos, model);

    // Correct for perspective and project the vertex position onto the screen.
    pos = mul(pos, viewProjection[idx]);
    output.pos = (min16float4)pos;

    // Pass the color through without modification.
    output.color = input.color;

    // Set the render target array index.
    output.viewId = idx;

    return output;
}
```

이 방법으로 스테레오 렌더링 대상 배열에 그리기를 수행 하는 기존 인스턴스 그리기 기술을 사용 하려는 경우에는 일반적으로 사용 하는 인스턴스 수를 두 배로 그려야 합니다. 셰이더의 경우 **입력.** 로 이동 id를 2로 나눕니다 .이 id는 (예: 개체별 데이터의 버퍼)로 인덱싱되는 원본 인스턴스 id를 가져옵니다 (예: `int actualIdx = input.instId / 2;`

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a>HoloLens에서 스테레오 콘텐츠를 렌더링 하는 방법에 대 한 중요 정보

Windows Mixed Reality는 모든 셰이더 단계에서 렌더링 대상 배열 인덱스를 설정 하는 기능을 지원 합니다. 일반적으로이 작업은 Direct3D 11에 대 한 의미 체계를 정의 하는 방식 때문에 기 하 도형 셰이더 단계 에서만 수행할 수 있는 작업입니다. 여기서는 꼭 짓 점 및 픽셀 셰이더 단계 집합만 사용 하 여 렌더링 파이프라인을 설정 하는 방법의 전체 예제를 보여 줍니다. 셰이더 코드는 위에서 설명한 것과 같습니다.

From **SpinningCubeRenderer:: Render**:

```cpp
const auto context = m_deviceResources->GetD3DDeviceContext();

// Each vertex is one instance of the VertexPositionColor struct.
const UINT stride = sizeof(VertexPositionColor);
const UINT offset = 0;
context->IASetVertexBuffers(
    0,
    1,
    m_vertexBuffer.GetAddressOf(),
    &stride,
    &offset
);
context->IASetIndexBuffer(
    m_indexBuffer.Get(),
    DXGI_FORMAT_R16_UINT, // Each index is one 16-bit unsigned integer (short).
    0
);
context->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
context->IASetInputLayout(m_inputLayout.Get());

// Attach the vertex shader.
context->VSSetShader(
    m_vertexShader.Get(),
    nullptr,
    0
);
// Apply the model constant buffer to the vertex shader.
context->VSSetConstantBuffers(
    0,
    1,
    m_modelConstantBuffer.GetAddressOf()
);

// Attach the pixel shader.
context->PSSetShader(
    m_pixelShader.Get(),
    nullptr,
    0
);

// Draw the objects.
context->DrawIndexedInstanced(
    m_indexCount,   // Index count per instance.
    2,              // Instance count.
    0,              // Start index location.
    0,              // Base vertex location.
    0               // Start instance location.
);
```

### <a name="important-note-about-rendering-on-non-hololens-devices"></a>HoloLens가 아닌 장치에서 렌더링 하는 방법에 대 한 중요 정보

꼭 짓 점 셰이더의 렌더링 대상 배열 인덱스를 설정 하려면 그래픽 드라이버가 선택적 Direct3D 11.3 기능을 지원 해야 합니다 .이 기능은 HoloLens에서 지원 됩니다. 앱은 렌더링을 위한 해당 기법도 안전 하 게 구현할 수 있으며 모든 요구 사항은 Microsoft HoloLens에서 실행 하기 위해 충족 됩니다.

Holographic 앱에 대 한 강력한 개발 도구인 HoloLens 에뮬레이터를 사용 하 고 Windows 10 Pc에 연결 된 Windows Mixed Reality 모던 헤드셋 장치를 지 원하는 경우를 들 수 있습니다. 비 HoloLens 렌더링 경로에 대 한 지원. 따라서 모든 Windows Mixed Reality의 경우 Windows Holographic 앱 템플릿에도 빌드됩니다. 템플릿 코드에서 개발 PC의 GPU에서 holographic 앱을 실행할 수 있도록 하는 코드를 찾을 수 있습니다. **DeviceResources** 클래스가이 선택적 기능 지원을 확인 하는 방법은 다음과 같습니다.

From **DeviceResources:: CreateDeviceResources**:

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

이 선택적 기능 없이 렌더링을 지원 하려면 앱에서 geometry 셰이더를 사용 하 여 렌더링 대상 배열 인덱스를 설정 해야 합니다. 이 코드 조각은 **VSSetConstantBuffers** *뒤* 에 추가 되 고, 이전 섹션에 표시 된 코드 예제의 **Pssetshader** *이전에* 는 HoloLens에서 스테레오를 렌더링 하는 방법을 설명 합니다.

From **SpinningCubeRenderer:: Render**:

```cpp
if (!m_usingVprtShaders)
{
    // On devices that do not support the D3D11_FEATURE_D3D11_OPTIONS3::
    // VPAndRTArrayIndexFromAnyShaderFeedingRasterizer optional feature,
    // a pass-through geometry shader is used to set the render target 
    // array index.
    context->GSSetShader(
        m_geometryShader.Get(),
        nullptr,
        0
    );
}
```

**HLSL 참고**:이 경우 TEXCOORD0와 같은 항상 허용 되는 셰이더 의미 체계를 사용 하 여 렌더링 대상 배열 인덱스를 geometry 셰이더에 전달 하는 약간 수정 된 꼭 짓 점 셰이더도 로드 해야 합니다. 기 하 도형 셰이더는 작업을 수행할 필요가 없습니다. 템플릿 기 하 도형 셰이더는 SV_RenderTargetArrayIndex 의미 체계를 설정 하는 데 사용 되는 렌더링 대상 배열 인덱스를 제외 하 고 모든 데이터를 통과 합니다.

Hlsl에 대 한 앱 템플릿 코드 **GeometryShader**:

```HLSL
// Per-vertex data from the vertex shader.
struct GeometryShaderInput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;
    uint        instId  : TEXCOORD0;
};

// Per-vertex data passed to the rasterizer.
struct GeometryShaderOutput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;
    uint        rtvId   : SV_RenderTargetArrayIndex;
};

// This geometry shader is a pass-through that leaves the geometry unmodified 
// and sets the render target array index.
[maxvertexcount(3)]
void main(triangle GeometryShaderInput input[3], inout TriangleStream<GeometryShaderOutput> outStream)
{
    GeometryShaderOutput output;
    [unroll(3)]
    for (int i = 0; i < 3; ++i)
    {
        output.pos   = input[i].pos;
        output.color = input[i].color;
        output.rtvId = input[i].instId;
        outStream.Append(output);
    }
}
```

## <a name="present"></a>표시

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a>Holographic 프레임을 사용 하 여 스왑 체인을 표시 합니다.

Windows Mixed Reality를 사용 하는 경우 시스템은 스왑 체인을 제어 합니다. 그러면 시스템에서 각 holographic 카메라에 대 한 프레임을 관리 하 여 고품질 사용자 환경을 보장 합니다. 또한 각 카메라에 대해 이미지 안정화 또는 혼합 현실 캡처와 같은 시스템 측면을 최적화 하기 위해 각 프레임을 업데이트 하는 뷰포트를 제공 합니다. 따라서 DirectX를 사용 하는 holographic 앱은 DXGI 스왑 체인에 **존재** 하는을 호출 하지 않습니다. 대신 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> 클래스를 사용 하 여 그리기를 완료 한 후 프레임에 대 한 모든 swapchain을 표시 합니다.

**DeviceResources::P 다시 보낸**위치:

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

기본적으로이 API는 프레임이 반환 될 때까지 대기 합니다. Holographic apps는 새 프레임에서 작업을 시작 하기 전에 이전 프레임이 완료 될 때까지 기다려야 합니다 .이는 대기 시간을 줄이고 프레임 예측에서 더 나은 결과를 허용 하기 때문입니다. 이것은 하드 규칙이 아니며, 렌더링을 위해 한 화면 새로 고침 보다 오랜 시간이 걸리는 프레임을 사용 하는 경우 HolographicFramePresentWaitBehavior 매개 변수를 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>에 전달 하 여이 대기를 비활성화할 수 있습니다. 이 경우에는 GPU에서 연속 로드를 유지 하기 위해 비동기 렌더링 스레드를 사용할 가능성이 높습니다. HoloLens 장치의 새로 고침 빈도는 60hz입니다. 단, 한 프레임의 기간은 약 16 밀리초입니다. 모던 헤드셋 장치의 범위는 60hz에서 90hz;입니다. 90 hz에서 디스플레이를 새로 고치면 각 프레임의 기간이 약 11 밀리초가 됩니다.

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a>HolographicFrame와 협력 하 여 DeviceLost 시나리오를 처리 합니다.

DirectX 11 앱은 일반적으로 **DeviceLost** 오류가 있는지 확인 하기 위해 DXGI 스왑 체인의 **present** 함수에서 반환 된 HRESULT를 확인 하려고 합니다. <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> 클래스는이를 처리 합니다. 반환 되는 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> 를 검사 하 여 Direct3D 장치 및 장치 기반 리소스를 해제 하 고 다시 만들어야 하는지 확인 합니다.

```cpp
// The PresentUsingCurrentPrediction API will detect when the graphics device
// changes or becomes invalid. When this happens, it is considered a Direct3D
// device lost scenario.
if (presentResult == HolographicFramePresentResult::DeviceRemoved)
{
    // The Direct3D device, context, and resources should be recreated.
    HandleDeviceLost();
}
```

Direct3D 장치를 분실 한 경우 다시 만든 경우 새 장치를 사용 하 여 시작 하도록 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> 에 지시 해야 합니다. 이 장치에 대해 스왑 체인이 다시 작성 됩니다.

From **DeviceResources:: InitializeUsingHolographicSpace**:

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

프레임이 표시 되 면 주 프로그램 루프로 돌아가서 다음 프레임으로 계속할 수 있습니다.

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a>하이브리드 그래픽 Pc 및 혼합 현실 응용 프로그램

Windows 10 크리에이터 업데이트 Pc는 개별 및 통합 Gpu를 **모두** 사용 하 여 구성할 수 있습니다. 이러한 유형의 컴퓨터를 사용 하 여 Windows는 헤드셋이 연결 된 어댑터를 선택 합니다. 응용 프로그램에서 생성 하는 DirectX 장치가 동일한 어댑터를 사용 하는지 확인 해야 합니다.

가장 일반적인 Direct3D 샘플 코드는 하이브리드 시스템이 헤드셋에 사용 되는 것과 다를 수 있는 기본 하드웨어 어댑터를 사용 하 여 DirectX 장치를 만드는 방법을 보여 줍니다.

이로 인해 발생할 수 있는 문제를 해결 하려면 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>의 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> 를 사용 합니다. PrimaryAdapterId () 또는 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>. AdapterId (). 그런 다음이 adapterId를 사용 하 여 IDXGIFactory4 Adapterbyluid를 사용 하는 올바른 DXGIAdapter를 선택할 수 있습니다.

From **DeviceResources:: InitializeUsingHolographicSpace**:

```cpp
// The holographic space might need to determine which adapter supports
// holograms, in which case it will specify a non-zero PrimaryAdapterId.
LUID id =
{
    m_holographicSpace.PrimaryAdapterId().LowPart,
    m_holographicSpace.PrimaryAdapterId().HighPart
};

// When a primary adapter ID is given to the app, the app should find
// the corresponding DXGI adapter and use it to create Direct3D devices
// and device contexts. Otherwise, there is no restriction on the DXGI
// adapter the app can use.
if ((id.HighPart != 0) || (id.LowPart != 0))
{
    UINT createFlags = 0;

    // Create the DXGI factory.
    ComPtr<IDXGIFactory1> dxgiFactory;
    winrt::check_hresult(
        CreateDXGIFactory2(
            createFlags,
            IID_PPV_ARGS(&dxgiFactory)
        ));
    ComPtr<IDXGIFactory4> dxgiFactory4;
    winrt::check_hresult(dxgiFactory.As(&dxgiFactory4));

    // Retrieve the adapter specified by the holographic space.
    winrt::check_hresult(
        dxgiFactory4->EnumAdapterByLuid(
            id,
            IID_PPV_ARGS(&m_dxgiAdapter)
        ));
}
else
{
    m_dxgiAdapter.Reset();
}
```

**Idxgid 어댑터를 사용 하 여 DeviceResources:: CreateDeviceResources를 업데이트** 하는 코드

```cpp
// Create the Direct3D 11 API device object and a corresponding context.
ComPtr<ID3D11Device> device;
ComPtr<ID3D11DeviceContext> context;

const D3D_DRIVER_TYPE driverType = m_dxgiAdapter == nullptr ? D3D_DRIVER_TYPE_HARDWARE : D3D_DRIVER_TYPE_UNKNOWN;
const HRESULT hr = D3D11CreateDevice(
    m_dxgiAdapter.Get(),        // Either nullptr, or the primary adapter determined by Windows Holographic.
    driverType,                 // Create a device using the hardware graphics driver.
    0,                          // Should be 0 unless the driver is D3D_DRIVER_TYPE_SOFTWARE.
    creationFlags,              // Set debug and Direct2D compatibility flags.
    featureLevels,              // List of feature levels this app can support.
    ARRAYSIZE(featureLevels),   // Size of the list above.
    D3D11_SDK_VERSION,          // Always set this to D3D11_SDK_VERSION for Windows Runtime apps.
    &device,                    // Returns the Direct3D device created.
    &m_d3dFeatureLevel,         // Returns feature level of device created.
    &context                    // Returns the device immediate context.
);
```

**하이브리드 그래픽 및 미디어 파운데이션**

하이브리드 시스템에서 미디어 파운데이션를 사용 하면 비디오가 렌더링 되지 않거나 비디오 질감이 손상 되는 문제가 발생할 수 있습니다. 이는 미디어 파운데이션가 위에서 설명한 대로 시스템 동작을 기본값으로 수행 하기 때문에 발생할 수 있습니다. 일부 시나리오에서는 다중 스레딩을 지원 하기 위해 별도의 ID3D11Device를 만들어야 하며, 올바른 생성 플래그가 설정 됩니다.

ID3D11Device를 초기화할 때 D3D11_CREATE_DEVICE_VIDEO_SUPPORT 플래그는 D3D11_CREATE_DEVICE_FLAG의 일부로 정의 해야 합니다. 장치 및 컨텍스트를 만든 후에는 <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">Setmultithreadprotected</a> 를 호출 하 여 다중 스레딩을 사용 하도록 설정 합니다. 장치를 <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>에 연결 하려면 <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager:: resetdevice</a> 함수를 사용 합니다.

**ID3D11Device와 IMFDXGIDeviceManager를 연결 하는**코드:

```cpp
// create dx device for media pipeline
winrt::com_ptr<ID3D11Device> spMediaDevice;

// See above. Also make sure to enable the following flags on the D3D11 device:
//   * D3D11_CREATE_DEVICE_VIDEO_SUPPORT
//   * D3D11_CREATE_DEVICE_BGRA_SUPPORT
if (FAILED(CreateMediaDevice(spAdapter.get(), &spMediaDevice)))
    return;                                                     

// Turn multithreading on 
winrt::com_ptr<ID3D10Multithread> spMultithread;
if (spContext.try_as(spMultithread))
{
    spMultithread->SetMultithreadProtected(TRUE);
}

// lock the shared dxgi device manager
// call MFUnlockDXGIDeviceManager when no longer needed
UINT uiResetToken;
winrt::com_ptr<IMFDXGIDeviceManager> spDeviceManager;
hr = MFLockDXGIDeviceManager(&uiResetToken, spDeviceManager.put());
if (FAILED(hr))
    return hr;
    
// associate the device with the manager
hr = spDeviceManager->ResetDevice(spMediaDevice.get(), uiResetToken);
if (FAILED(hr))
    return hr;
```

## <a name="see-also"></a>참고 항목
* [DirectX의 좌표계](coordinate-systems-in-directx.md)
* [Using the HoloLens emulator(HoloLens 에뮬레이터 사용)](using-the-hololens-emulator.md)
