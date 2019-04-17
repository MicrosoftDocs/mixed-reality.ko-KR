---
title: DirectX의 렌더링
description: Windows Mixed Reality holographic 렌더링에 설명합니다.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality를 홀로그램, 렌더링, 3D 그래픽, HolographicFrame, 렌더링 루프 업데이트 루프, 연습, 샘플 코드
ms.openlocfilehash: fd35f971af4c3c9dfd7f21ee396c92216b3246e9
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605162"
---
# <a name="rendering-in-directx"></a>DirectX의 렌더링

Windows Mixed Reality은 풍부한을 생성 하기 위해 DirectX 기반, 3D 그래픽 환경을 사용자에 대 한 합니다. 렌더링 추상화는 DirectX 바로 위에 위치 하 고 위치 및 시스템에 의해 예측 된 holographic 장면에 하나 이상의 관찰자의 방향에 대 한 앱 이유를 있습니다. 개발자 찾을 수 있습니다 다음 각 카메라를 기준으로 해당 홀로그램 앱 사용자가 이동 하는 대로 다양 한 공간 좌표계에서 이러한 홀로그램 렌더링 수 있도록 합니다.

## <a name="update-for-the-current-frame"></a>현재 프레임에 대 한 업데이트

홀로그램에 대 한 응용 프로그램 상태를 업데이트 하려면 한 번 앱 프레임 마다 수행 됩니다.
* 가져오기는 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> 표시 관리 시스템에서.
* 현재 예측값의 카메라 보기 렌더링이 완료 된 경우 될 위치를 사용 하 여 장면을 업데이트 합니다. Note holographic 장면의 카메라를 둘 이상 있을 수 있습니다.

Holographic 카메라 뷰를 렌더링 하려면 한 번 앱 프레임 마다 수행 됩니다.
* 각 카메라에 대 한 시스템에서 카메라의 뷰 및 투영 행렬을 사용 하 여 현재 프레임에 대 한 장면을 렌더링 합니다.

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a>새 holographic 프레임을 만들고 해당 예측을 가져오기

합니다 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> 앱을 업데이트 하 고 현재 프레임을 렌더링 하기 위해 필요한 정보가 있습니다. 앱을 호출 하 여 각각의 새로운 프레임을 시작 합니다 **CreateNextFrame** 메서드. 사용 가능 하 고에서 캡슐화 된 최신 센서 데이터를 사용 하 여 예측을 수행 하면이 메서드를 호출 **CurrentPrediction** 개체입니다.

이므로 유효한 인스턴트에 대 한 시간에 각 렌더링 된 프레임에 대 한 새 프레임 개체를 따라야 합니다. 합니다 **CurrentPrediction** 카메라 위치와 같은 정보를 포함 하는 속성입니다. 정보는 프레임 사용자에 게 표시 되도록 예상 되는 경우는 정확한 시점 추정 됩니다.

다음 코드에서 발췌 한 것은 **AppMain::Update**:

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a>프로세스 카메라 업데이트

백 버퍼 프레임 간에 변경할 수 있습니다. 뒷면의 유효성을 검사 하 여 앱 요구 사항을 각 카메라에 대 한 버퍼 릴리스 및 필요에 따라 리소스 뷰와 깊이 버퍼를 다시 만듭니다. 예측에 대 한 동작 집합이 현재 프레임에 사용 되는 카메라의 신뢰할 수 있는 목록 인지 확인 합니다. 일반적으로 카메라의 집합을 반복 하려면이 목록을 사용 합니다.

**AppMain::Update**:

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

**DeviceResources::EnsureCameraResources**:

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a>렌더링에 대 한 기초로 사용 하는 좌표계를 가져옵니다

Windows Mixed Reality 있습니다 만드는 다양 한 앱 [좌표계](coordinate-systems-in-directx.md) 실제에서 위치를 추적 하는 연결 된 참조 프레임 고정 참조 프레임 등 필요에 따라 합니다. 앱은 홀로그램 각 프레임을 렌더링 하는 위치에 대 한 이유를 이러한 좌표계를 사용할 수 있습니다. 전달 API에서 좌표를 요청할 때는 항상을 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> 하려는 좌표를 표현할 수 내에서.

**AppMain::Update**:

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

이러한 좌표 시스템 장면에 콘텐츠를 렌더링 하는 경우 스테레오 보기 행렬을 생성 한 다음 사용할 수 있습니다.

From **CameraResources::UpdateViewProjectionBuffer**:

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a>프로세스 게이즈 및 입력 제스처

[Gaze](gaze.md) 하 고 [제스처](gestures.md) 입력 시간 기반 되지 않으며 따라서 업데이트 하지 않아도 합니다 **StepTimer** 함수입니다. 그러나 [이 입력](gaze,-gestures,-and-motion-controllers-in-directx.md) 앱에서 각 프레임에서 표시 해야 하는 것입니다.

### <a name="process-time-based-updates"></a>처리 시간을 기준으로 업데이트

실시간 렌더링 앱 시간 기반 업데이트를 처리 하는 방법이 해야 합니다. 통해 Windows Holographic 앱 템플릿에서이 작업을 수행 하는 방법을 제공 하 고는 **StepTimer** 구현 합니다. 이 DirectX 11 UWP 앱 템플릿에서 하므로 이미 살펴본 해당 템플릿을 경우 표시 됩니다 친숙 한 처음부터 제공에 StepTimer 비슷합니다. 이 StepTimer 샘플 도우미 클래스는 고정된 시간 단계 업데이트 뿐만 아니라 시간 단계 변수 업데이트를 제공할 수 있습니다 및 기본 모드 변수 시간 단계는 합니다.

Holographic 렌더링의 경우 특히 타이머 함수에 너무 많은 넣지 선택 했습니다. 고정된 시간 단계 수를 구성할 수 있습니다,이 경우 또는 전혀 일부 프레임이 프레임당 – 두 번 이상 호출 가져올 수 있습니다 및 holographic 데이터 업데이트 프레임당 한 번만 수행 해야 때문입니다.


**AppMain::Update**:

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a>위치 및 좌표 시스템의 회전 홀로그램

템플릿을 사용 하 여 마찬가지로 단일 좌표 시스템에서 작동 하는 경우는 **SpatialStationaryReferenceFrame**,이 프로세스 다르지 무엇을 하 고 그렇지 않으면 3D 그래픽에서 하는 데 사용 합니다. 큐브를 회전 우리는 여기에서 고정 좌표 시스템의 위치를 기준으로 된 모델 매트릭스를 설정 합니다.

From **SpinningCubeRenderer::Update**:

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

**고급 시나리오에 대 한 note:** 회전 큐브는 단일 참조 프레임 내에서 홀로그램을 배치 하는 방법의 간단한 예입니다. 수 이기도 [여러 SpatialCoordinateSystems를 사용 하 여](coordinate-systems-in-directx.md) 동시에 같은 렌더링 된 프레임을 합니다.

### <a name="update-constant-buffer-data"></a>상수 버퍼 데이터를 업데이트 합니다.

모델 변환 콘텐츠에 대 한 일반적인 방식으로 업데이트 됩니다. 이제에서 렌더링 될 수 있습니다 좌표계에 대해 유효한 변환만 계산 됩니다.

From **SpinningCubeRenderer::Update**:

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

뷰 및 프로젝션 변환의 경우는 어떨까요? 최상의 결과 기다립니다 준비가 거의 그리기 호출에 대 한 이러한 시작 하기 전에 하고자 합니다.

## <a name="render-the-current-frame"></a>현재 프레임을 렌더링

Windows Mixed Reality를 렌더링 2D mono 디스플레이에 렌더링 크게 다르지 이지만 일부의 차이점이 주의 해야 합니다.
* Holographic 프레임 예측은 중요 합니다. 예측에 가까울수록 더 나은 프로그램 홀로그램 보입니다 프레임 표시 되 면 방법은입니다.
* Windows Mixed Reality 카메라 보기를 제어합니다. Holographic 프레임은 표시 하를 나중에 이기 때문에 각각을 렌더링 해야 합니다.
* 스테레오 렌더링 렌더링 대상 배열에 인스턴스화된 그리기를 사용 하 여 수행 하려는 것이 좋습니다. Holographic 앱 템플릿의 인스턴스화된 그리기에 렌더링 대상 뷰를 사용 하는 렌더링 대상 배열에 대 한 권장된 접근 방식을 사용 하는 **Texture2DArray**합니다.
* 두 배열이 아닌 RenderTargetViews (눈 마다 하나씩) 조각 중 하나가 각 참조는 만드는 해야 스테레오 인스턴스를 사용 하지 않고 렌더링 하려는 경우는 **Texture2DArray** 시스템에서 앱에 제공 합니다. 이 권장 되지 않습니다, 인스턴스를 사용 하 여 보다 성능이 크게 저하 경우가 일반적입니다.

### <a name="get-an-updated-holographicframe-prediction"></a>업데이트 된 HolographicFrame 예측을 가져오기

프레임 예측 업데이트 이미지 안정화의 효율성을 개선 하 고 홀로그램 사이의 예측 프레임 사용자에 게 표시 된 경우 더 짧은 시간으로 인해 보다 정확 하 게 배치 허용 합니다. 이상적으로 렌더링 직전 프레임 예측을 업데이트 합니다.

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a>각 카메라에 렌더링 합니다.

예측에서는 카메라 포즈 집합에서 loop 하 고이 집합의 각 카메라에 렌더링 합니다.

**렌더링 패스에 설정**

Windows Mixed Reality 사용 하 여 stereoscopic 렌더링 깊이 효과 향상 시키기 위해 렌더링 쓰고, 왼쪽 및 오른쪽 표시 활성화 되므로 합니다. 입체 렌더링 뇌 실제 크기를 조정할 수 있습니다 하는 두 디스플레이 간에 오프셋이 생깁니다. 이 섹션에서는 stereoscopic 렌더링 Windows Holographic 앱 템플릿에서 코드를 사용 하 여 인스턴스를 사용 하 여 합니다.

각 카메라 holographic 공간으로 자체 렌더링 대상 (백 버퍼) 및 뷰 및 프로젝션 매트릭스에 있습니다. 앱은 리소스를 만드는 모든 다른 카메라 기반-깊이 버퍼와 같은 카메라 당 기준 해야 합니다. Windows Holographic 앱 템플릿에서 DX::CameraResources에서 이러한 리소스를 함께 번들로 묶는 도우미 클래스를 제공 했습니다. 렌더링 대상 뷰를 설정 하 여 시작 합니다.

**AppMain::Render**:

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

**예측을 사용 하 여 카메라에 대 한 뷰 및 투영 행렬을 가져오려면**

각 holographic 카메라에 대 한 뷰 및 투영 행렬은 프레임 마다를 사용 하 여 변경 됩니다. 각 holographic 카메라에 대 한 상수 버퍼의 데이터를 새로 고칩니다. 예측을 업데이트 하는 카메라에 대 한 모든 그리기 호출을 수행 하기 전에 후이 작업을 수행 합니다.

**AppMain::Render**:

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

여기에 행렬 카메라 포즈에서 획득 하는 방법을 보여 줍니다. 이 과정에서 카메라에 대 한 현재 뷰포트를 가져옵니다. 좌표 시스템을 제공 하는 방법: 게이즈를 이해 하는 데에서는 동일한 좌표 시스템 이며 동일한 회전 큐브를 위치로 사용 하는 것입니다.


From **CameraResources::UpdateViewProjectionBuffer**:

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

뷰포트의 각 프레임을 설정 되어야 합니다. 꼭 짓 점 셰이더 (최소) 일반적으로 할 보기/프로젝션 데이터에 액세스할 수 있습니다.


**CameraResources::AttachViewProjectionBuffer**:

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

**카메라 백 버퍼에 렌더링 하 고 깊이 버퍼 커밋**:

있는지 여부를 확인 하는 것이 좋습니다 **TryGetViewTransform** 되므로 보기/프로젝션 데이터를 사용 하기 전에 성공 좌표계를 찾을 수 없는 경우 (예를 들어 추적이 중단 되었습니다) 앱에 대 한 것으로 렌더링할 수 없습니다 프레임입니다. 템플릿을 호출 **렌더링** 회전 큐브의 경우 합니다 **CameraResources** 클래스 성공적인 업데이트를 나타냅니다.

Windows Mixed Reality를을 유지 하기 위해 홀로그램은 사용자나 개발자에에서 넣습니다 전 세계에 대 한 기능을 포함 [안정화 이미지](hologram-stability.md)합니다. 이미지 안정화 사용자에 대 한 가장 holographic 환경 보장 하는 렌더링 파이프라인에 내재 된 대기 시간을 숨기는 데 도움이 됩니다. 이미지 안정화를 한층 더 강화 하기 위해 포커스 지점을 지정할 수 있습니다 또는 깊이 버퍼를 계산 액세스에 최적화 된 이미지 안정화 실시간으로 제공 될 수 있습니다.

최상의 결과 앱에 사용 하 여 깊이 버퍼를 제공 해야 합니다 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API. Windows Mixed Reality 실시간에서 이미지 안정화를 최적화 하려면 깊이 버퍼에서 기 하 도형 정보를 사용할 수 있습니다. Windows Holographic 앱 템플릿 홀로그램 안정성을 최적화 하는 데 도움이 기본적으로 앱의 깊이 버퍼를 커밋합니다.

**AppMain::Render**:

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
>Windows에서 셰이더 리소스로 깊이 버퍼를 사용할 수 있어야 하므로 GPU에서 깊이 질감을 처리 합니다. 만든 ID3D11Texture2D 관대 한 형식의 형식 이어야 하며, 셰이더 리소스 뷰 바인딩해야 합니다. 이미지 안정화에 커밋할 수 있는 깊이 질감을 만드는 방법의 예는 다음과 같습니다.

에 대 한 코드 **CommitDirect3D11DepthBuffer에 대 한 깊이 버퍼 리소스를 만들**:

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

**그리기 holographic 콘텐츠**

Windows Holographic 앱 템플릿 크기는 2 Texture2DArray에 인스턴스화된 기 하 도형 그리기의 권장 되는 기술을 사용 하 여 스테레오의 콘텐츠를 렌더링 합니다. Windows Mixed Reality를 작동 하는 방법 및이 인스턴스 부분을 살펴보겠습니다.

From **SpinningCubeRenderer::Render**:

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

상수 버퍼에서 다른 보기/투영 행렬을 액세스 하는 각 인스턴스에입니다. 가 2 행렬의 배열이 있는 상수 버퍼 구조체에는 다음과 같습니다.

**VertexShaderShared.hlsl**에서 포함 된 **VPRTVertexShader.hlsl**:

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

각 픽셀에 대 한 렌더링 대상 배열 인덱스를 설정 해야 합니다. 다음 코드 조각에서 output.viewId에 매핑되는 **SV_RenderTargetArrayIndex** 의미 체계. 렌더링 대상 배열 인덱스를 의미 체계는 셰이더 단계에서 설정할 수 있는 선택적 Direct3D 11.3 기능에 대 한 지원이 필요 note 합니다.

**VPRTVertexShader.hlsl**:

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

**VertexShaderShared.hlsl**에서 포함 된 **VPRTVertexShader.hlsl**:

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

기존 인스턴스를 사용 하려는 경우 그리기 기술을 스테레오에 그리기의이 메서드를 사용 하 여 렌더링 대상 배열을 수행 해야 하는 모든 두 배 일반적으로 인스턴스 수를 그립니다. 셰이더에서 나누는 **input.instId** 원래 인스턴스 ID를 가져오는 2에서 인덱싱할 수 있는 버퍼로 개체별 데이터의 예를 들어: `int actualIdx = input.instId / 2;`

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a>HoloLens에서 스테레오 콘텐츠를 렌더링 하는 방법에 대 한 중요 정보

Windows Mixed Reality 모든 셰이더 단계의 렌더링 대상 배열 인덱스를 설정 하는 기능을 지원 일반적으로 의미 체계 Direct3D 11에 대해 정의 된 방식으로 인해 기 하 도형 셰이더 단계에만 수행할 수 있는 작업입니다. 여기에서 집합에만 꼭 짓 점 및 픽셀 셰이더 단계를 사용 하 여 렌더링 파이프라인을 설정 하는 방법의 전체 예제를 보여 줍니다. 셰이더 코드는 위에서 설명한 것 처럼 됩니다.

From **SpinningCubeRenderer::Render**:

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

### <a name="important-note-about-rendering-on-non-hololens-devices"></a>비 HoloLens 장치에서 렌더링 하는 방법에 대 한 중요 정보

그래픽 드라이버 HoloLens을 지 원하는 선택적 Direct3D 11.3 기능을 지원 하는지 필요 꼭 짓 점 셰이더에서 렌더링 대상 배열 인덱스를 설정 합니다. 앱 안전 하 게 렌더링에 대 한 해당 기법만을 구현 하는 일을 할 수 있습니다 및 Microsoft HoloLens 실행 하기 위한 모든 요구 사항을 충족 됩니다.

-Holographic 앱에 대 한 강력한 개발 도구 및 Windows 10 Pc에 연결 되어 있는 Windows Mixed Reality 몰입 형 헤드셋 장치를 지원할 수 있는 HoloLens 에뮬레이터도 사용 하려는 경우 수도 있습니다. 따라서 모든 Windows Mixed Reality-에 대 한도 기능이 Windows Holographic 앱 템플릿 및 HoloLens가 아닌 렌더링 경로 지원 합니다. 템플릿 코드에서 holographic 앱 개발 PC에에서는 GPU에서 실행을 사용 하도록 코드를 찾을 수 있습니다. 다음은 하는 방법을 **DeviceResources** 확인이 선택적 기능 지원에 대 한 클래스입니다.

**DeviceResources::CreateDeviceResources**:

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

이 선택적 기능 없이 렌더링을 지원 하려면 앱의 렌더링 대상 배열 인덱스를 설정 하려면 기 하 도형 셰이더를 사용 해야 합니다. 이 코드 조각을 추가 될 *한 후* **VSSetConstantBuffers**, 및 *하기 전에* **PSSetShader** 이전에 표시 된 코드 예제 스테레오 HoloLens에 렌더링 하는 방법을 설명 하는 섹션입니다.

From **SpinningCubeRenderer::Render**:

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

**HLSL 참고**: 이 경우 렌더링 대상 배열 인덱스는 항상 허용 셰이더 TEXCOORD0 같은 의미 체계를 사용 하 여 기 하 도형 셰이더를 전달 하는 약간 수정 된 꼭 짓 점 셰이더도 로드 해야 합니다. 기 하 도형 셰이더; 작업을 수행할 필요가 없습니다. 템플릿 기 하 도형 셰이더는 SV_RenderTargetArrayIndex 의미 체계 설정 하는 데 사용 되는 렌더링 대상 배열 인덱스를 제외 하 고 모든 데이터를 통해 전달 됩니다.

앱 템플릿 코드에 대 한 **GeometryShader.hlsl**:

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

## <a name="present"></a>있음

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a>스왑 체인을 주도록 holographic 프레임을 사용 하도록 설정

Windows Mixed Reality를 사용 하 여 시스템 스왑 체인을 제어합니다. 그런 다음 시스템 고품질 사용자 환경을 보장 하려면 각 holographic 카메라 발표할 프레임을 관리 합니다. 뷰포트 업데이트 이미지 안정화 또는 혼합 현실 캡처 등 시스템의 측면을 최적화 하기 위해 각 카메라에 대 한 각 프레임도 제공 합니다. 따라서 DirectX를 사용 하 여 holographic 앱을 호출 하지 않습니다 **있는** 는 DXGI에 스왑 체인입니다. 대신 사용 합니다 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> 완료 되 면 프레임에 대 한 모든 swapchain를 제공 하는 클래스 것 그리기 합니다.

**DeviceResources::Present**:

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

기본적으로이 API는 프레임을 반환 하기 전에 완료에 대 한 대기 합니다. Holographic 앱을 이전 프레임 대기 시간이 줄어들고 holographic 프레임 예측에서 더 나은 결과 허용 하기 때문에 새 프레임에서 작업을 시작 하기 전에 완료 되기를 기다려야 합니다. 이 규칙을 하드 아니며 프레임 수를 렌더링 하 한 화면 새로 고침 보다 오래 걸리는 HolographicFramePresentWaitBehavior 매개 변수를 전달 하 여이 대기를 해제할 수 있다면 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>합니다. 이 경우에 비동기 렌더링 스레드를 GPU에 지속적인 부하를 유지 하기 위해 사용할 수 있습니다는. HoloLens 장치 새로 고침 빈도 60hz, 한 프레임에 약 16ms 기간 note 합니다. 몰입 형 헤드셋 장치에서에서 까지입니다 60hz 90 hz; 90 hz에서 표시를 새로 고칠 때 각 프레임에 약 11 밀리초 동안을 해야 합니다.

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a>HolographicFrame 협력의 DeviceLost 시나리오 처리

DirectX 11 앱을 DXGI 스왑 체인에서 반환한 HRESULT를 확인 하려면 일반적으로 **존재** 알아보려면 경우 함수는 **DeviceLost** 오류입니다. 합니다 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> 클래스 이러한 작업을 처리 합니다. 검사는 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> 를 해제 하는 Direct3D 장치 및 장치 기반 리소스를 다시 할 경우에 반환 합니다.

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

Direct3D 장치 손실 되어 다시 만들지 않은 경우 있는지를 확인 합니다 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> 새 장치를 사용 하 여 시작 합니다. 이 장치에 대 한 스왑 체인 다시 만들어집니다.

From **DeviceResources::InitializeUsingHolographicSpace**:

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

프레임에 표시 되 면 주 프로그램 루프에 다시 반환할 수 있으며 다음 프레임으로 계속할 수 있도록 수 있습니다.

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a>하이브리드 그래픽 Pc 및 혼합된 현실 응용 프로그램

Windows 10 크리에이터 스 업데이트 Pc를 사용 하 여 구성할 수 있습니다 **둘 다** Gpu 불연속 및 통합 합니다. 이러한 종류의 컴퓨터를 사용 하 여 Windows 헤드셋에 연결 된 어댑터를 선택 합니다. 응용 프로그램 동일한 어댑터를 사용 하는 만들면 DirectX 장치를 확인 해야 합니다.

가장 일반적인 Direct3D 샘플 코드 하이브리드 시스템에서 헤드셋에 사용 되는 것과 동일 하지 않을 수도 있는 기본 하드웨어 어댑터를 사용 하 여 DirectX 장치를 만드는 방법을 보여줍니다.

이 인해 발생할 수 있습니다 문제를 해결 하려면 사용 합니다 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> 에서 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>합니다. PrimaryAdapterId() 또는 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>합니다. AdapterId() 합니다. 그런 다음이 adapterId IDXGIFactory4.EnumAdapterByLuid를 사용 하 여 오른쪽 DXGIAdapter 선택에 사용할 수 있습니다.

From **DeviceResources::InitializeUsingHolographicSpace**:

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

코드를 **IDXGIAdapter 데 DeviceResources::CreateDeviceResources 업데이트**

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

Media Foundation을 사용 하 여 하이브리드 시스템에 있는 비디오 렌더링 되지 것입니다 또는 비디오 질감 손상 되었습니다. 문제를 일으킬 수 있습니다. Media Foundation은 위에서 설명한 것 처럼 시스템 동작을 기본값으로 하기 때문에 발생할 수 있습니다. 일부 시나리오에서는 별도 ID3D11Device 만들기는 다중 스레딩을 지원 및 올바른 생성 플래그를 설정 하는 일을 해야 합니다.

ID3D11Device를 초기화할 때 D3D11_CREATE_DEVICE_VIDEO_SUPPORT 플래그는 D3D11_CREATE_DEVICE_FLAG의 일부분으로 정의 되어야 합니다. 장치 및 상황에 맞는 만들어지면 호출 <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> 수 있도록 다중 스레딩 합니다. 사용 하 여 장치를 연결 하는 <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>를 사용 하 여 합니다 <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice</a> 함수.

코드를 **IMFDXGIDeviceManager는 ID3D11Device 연관**:

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

## <a name="see-also"></a>참조
* [DirectX의 좌표계](coordinate-systems-in-directx.md)
* [Using the HoloLens emulator(HoloLens 에뮬레이터 사용)](using-the-hololens-emulator.md)
