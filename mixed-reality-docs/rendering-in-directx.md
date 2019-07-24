---
title: DirectX에서 렌더링
description: Windows Mixed Reality의 holographic 렌더링에 대해 설명 합니다.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, holograms, 렌더링, 3D 그래픽, HolographicFrame, 렌더링 루프, 업데이트 루프, 연습, 샘플 코드
ms.openlocfilehash: 6edcaf808f2d7d48f480169e5579adb8984678a0
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629031"
---
# <a name="rendering-in-directx"></a><span data-ttu-id="25b64-104">DirectX에서 렌더링</span><span class="sxs-lookup"><span data-stu-id="25b64-104">Rendering in DirectX</span></span>

<span data-ttu-id="25b64-105">Windows Mixed Reality는 DirectX를 기반으로 하 여 사용자를 위한 풍부한 3D 그래픽 환경을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-105">Windows Mixed Reality is built on DirectX to produce rich, 3D graphical experiences for users.</span></span> <span data-ttu-id="25b64-106">렌더링 추상화는 DirectX 바로 위에 있으며 시스템에서 예측 하는 것 처럼 holographic 장면에서 하나 이상의 관찰자의 위치와 방향에 대 한 앱 이유를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-106">The rendering abstraction sits just above DirectX and lets an app reason about the position and orientation of one or more observers of a holographic scene, as predicted by the system.</span></span> <span data-ttu-id="25b64-107">그러면 개발자는 각 카메라를 기준으로 holograms을 찾을 수 있습니다. 그러면 사용자가 이동할 때 다양 한 공간 좌표계에서 앱이 이러한 holograms를 렌더링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-107">The developer can then locate their holograms relative to each camera, letting the app render these holograms in various spatial coordinate systems as the user moves around.</span></span>

## <a name="update-for-the-current-frame"></a><span data-ttu-id="25b64-108">현재 프레임에 대 한 업데이트</span><span class="sxs-lookup"><span data-stu-id="25b64-108">Update for the current frame</span></span>

<span data-ttu-id="25b64-109">Holograms에 대 한 응용 프로그램 상태를 업데이트 하려면 앱에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-109">To update the application state for holograms, once per frame the app will:</span></span>
* <span data-ttu-id="25b64-110">디스플레이 관리 시스템에서 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> 를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-110">Get a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> from the display management system.</span></span>
* <span data-ttu-id="25b64-111">렌더링이 완료 되 면 카메라 보기가 표시 되는 현재 예측으로 장면을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-111">Update the scene with the current prediction of where the camera view will be when render is completed.</span></span> <span data-ttu-id="25b64-112">Holographic 장면에는 카메라를 두 개 이상 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-112">Note, there can be more than one camera for the holographic scene.</span></span>

<span data-ttu-id="25b64-113">Holographic 카메라 보기로 렌더링 하려면 프레임당 한 번, 앱에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-113">To render to holographic camera views, once per frame the app will:</span></span>
* <span data-ttu-id="25b64-114">각 카메라에 대해 시스템의 카메라 보기 및 프로젝션 매트릭스를 사용 하 여 현재 프레임에 대 한 장면을 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-114">For each camera, render the scene for the current frame, using the camera view and projection matrices from the system.</span></span>

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a><span data-ttu-id="25b64-115">새 holographic 프레임을 만들고 해당 예측을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-115">Create a new holographic frame and get its prediction</span></span>

<span data-ttu-id="25b64-116"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> 에는 현재 프레임을 업데이트 하 고 렌더링 하기 위해 앱에 필요한 정보가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-116">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> has information that the app needs in order to update and render the current frame.</span></span> <span data-ttu-id="25b64-117">앱은 **Createnextframe** 메서드를 호출 하 여 각 새 프레임을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-117">The app begins each new frame by calling the **CreateNextFrame** method.</span></span> <span data-ttu-id="25b64-118">이 메서드가 호출 되 면 사용 가능한 최신 센서 데이터를 사용 하 여 예측을 수행 하 고 **currentprediction** 개체에 캡슐화 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-118">When this method is called, predictions are made using the latest sensor data available, and encapsulated in **CurrentPrediction** object.</span></span>

<span data-ttu-id="25b64-119">새 프레임 개체는 특정 시간 동안만 유효 하므로 렌더링 된 각 프레임에 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-119">A new frame object must be used for each rendered frame as it is only valid for an instant in time.</span></span> <span data-ttu-id="25b64-120">**Currentprediction** 속성은 카메라 위치와 같은 정보를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-120">The **CurrentPrediction** property contains information such as the camera position.</span></span> <span data-ttu-id="25b64-121">이 정보는 프레임이 사용자에 게 표시 될 것으로 예상 되는 정확한 시점에 추정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-121">The information is extrapolated to the exact moment in time when the frame is expected to be visible to the user.</span></span>

<span data-ttu-id="25b64-122">다음 코드는 **Appmain:: Update**에서 발췌 한 것 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-122">The following code is excerpted from **AppMain::Update**:</span></span>

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a><span data-ttu-id="25b64-123">카메라 업데이트 처리</span><span class="sxs-lookup"><span data-stu-id="25b64-123">Process camera updates</span></span>

<span data-ttu-id="25b64-124">백 버퍼는 프레임에서 프레임으로 변경 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-124">Back buffers can change from frame to frame.</span></span> <span data-ttu-id="25b64-125">앱은 각 카메라에 대해 백 버퍼의 유효성을 검사 하 고 필요에 따라 리소스 뷰 및 깊이 버퍼를 해제 하 고 다시 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-125">Your app needs to validate the back buffer for each camera, and release and recreate resource views and depth buffers as needed.</span></span> <span data-ttu-id="25b64-126">예측의 포즈 집합은 현재 프레임에서 사용 되는 카메라의 신뢰할 수 있는 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-126">Notice that the set of poses in the prediction is the authoritative list of cameras being used in the current frame.</span></span> <span data-ttu-id="25b64-127">일반적으로이 목록을 사용 하 여 카메라 집합을 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-127">Usually, you use this list to iterate on the set of cameras.</span></span>

<span data-ttu-id="25b64-128">**Appmain:: Update**에서:</span><span class="sxs-lookup"><span data-stu-id="25b64-128">From **AppMain::Update**:</span></span>

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

<span data-ttu-id="25b64-129">From **DeviceResources:: EnsureCameraResources**:</span><span class="sxs-lookup"><span data-stu-id="25b64-129">From **DeviceResources::EnsureCameraResources**:</span></span>

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a><span data-ttu-id="25b64-130">렌더링을 위한 기반으로 사용할 좌표계를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-130">Get the coordinate system to use as a basis for rendering</span></span>

<span data-ttu-id="25b64-131">Windows Mixed Reality를 사용 하면 앱에서 실제 세계의 위치를 추적 하는 연결 된 참조 프레임, 고정 참조 프레임 등 필요에 따라 다양 한 [좌표계](coordinate-systems-in-directx.md) 를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-131">Windows Mixed Reality lets your app create various [coordinate systems](coordinate-systems-in-directx.md) as needed, such as the attached reference frame and the stationary reference frame, that track locations in the physical world.</span></span> <span data-ttu-id="25b64-132">그러면 앱이 이러한 좌표계를 사용 하 여 각 프레임 holograms를 렌더링 하는 위치를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-132">Your app can then use these coordinate systems to reason about where to render holograms each frame.</span></span> <span data-ttu-id="25b64-133">API에서 좌표를 요청 하는 경우 항상 해당 좌표를 표시 하려는 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> 를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-133">When requesting coordinates from an API, you will always pass in the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> within which you want those coordinates to be expressed.</span></span>

<span data-ttu-id="25b64-134">**Appmain:: Update**에서:</span><span class="sxs-lookup"><span data-stu-id="25b64-134">From **AppMain::Update**:</span></span>

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

<span data-ttu-id="25b64-135">그런 다음 이러한 좌표계를 사용 하 여 장면에서 콘텐츠를 렌더링할 때 스테레오 뷰 매트릭스를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-135">These coordinate systems can then be used to generate stereo view matrices when rendering the content in your scene.</span></span>

<span data-ttu-id="25b64-136">From **CameraResources:: UpdateViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="25b64-136">From **CameraResources::UpdateViewProjectionBuffer**:</span></span>

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a><span data-ttu-id="25b64-137">응시 및 제스처 입력 처리</span><span class="sxs-lookup"><span data-stu-id="25b64-137">Process gaze and gesture input</span></span>

<span data-ttu-id="25b64-138">[응시](gaze-in-directx.md) 및 [직접](hands-and-motion-controllers-in-directx.md) 입력은 시간 기반이 아니므로 **sttimer** 함수에서 업데이트할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-138">[Gaze](gaze-in-directx.md) and [hand](hands-and-motion-controllers-in-directx.md) input are not time-based and thus do not have to update in the **StepTimer** function.</span></span> <span data-ttu-id="25b64-139">그러나이 입력은 앱이 각 프레임을 확인 해야 하는 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-139">However this input is something that the app needs to look at each frame.</span></span>

### <a name="process-time-based-updates"></a><span data-ttu-id="25b64-140">프로세스 시간 기반 업데이트</span><span class="sxs-lookup"><span data-stu-id="25b64-140">Process time-based updates</span></span>

<span data-ttu-id="25b64-141">실시간 렌더링 앱에는 시간 기반 업데이트를 처리 하는 방법이 필요 합니다. Windows Holographic 앱 템플릿에서 **Sttimer** 구현을 통해이 작업을 수행 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-141">Any real-time rendering app will need some way to process time-based updates; we provide a way to do this in the Windows Holographic app template via a **StepTimer** implementation.</span></span> <span data-ttu-id="25b64-142">이는 DirectX 11 UWP 앱 템플릿에서 제공 하는 Sttimer와 유사 하므로, 해당 템플릿을 이미 살펴본 경우에는 친숙 한 부분에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-142">This is similar to the StepTimer provided in the DirectX 11 UWP app template, so if you already have looked at that template you should be on familiar ground.</span></span> <span data-ttu-id="25b64-143">이 Sttimer 샘플 도우미 클래스는 고정 된 시간 단계 업데이트 및 가변 시간 단계 업데이트를 제공할 수 있으며 기본 모드는 가변 시간 단계입니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-143">This StepTimer sample helper class is able to provide fixed time-step updates, as well as variable time-step updates, and the default mode is variable time steps.</span></span>

<span data-ttu-id="25b64-144">Holographic 렌더링의 경우 타이머 함수에 너무 많이 배치 하지 않도록 특별히 선택 했습니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-144">In the case of holographic rendering, we've specifically chosen not to put too much into the timer function.</span></span> <span data-ttu-id="25b64-145">이는 고정 된 시간 단계가 되도록 구성할 수 있습니다 .이 경우 일부 프레임에 대해 프레임당 두 번 이상 호출 될 수 있으며, holographic 데이터 업데이트는 프레임당 한 번만 수행 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-145">This is because you can configure it to be a fixed time step, in which case it might get called more than once per frame – or not at all, for some frames – and our holographic data updates should happen once per frame.</span></span>


<span data-ttu-id="25b64-146">**Appmain:: Update**에서:</span><span class="sxs-lookup"><span data-stu-id="25b64-146">From **AppMain::Update**:</span></span>

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a><span data-ttu-id="25b64-147">좌표계에서 holograms 위치 및 회전</span><span class="sxs-lookup"><span data-stu-id="25b64-147">Position and rotate holograms in your coordinate system</span></span>

<span data-ttu-id="25b64-148">단일 좌표계에서 작업 하는 경우 템플릿이 **SpatialStationaryReferenceFrame**를 사용 하 여 작업 하는 경우이 프로세스는 3d 그래픽에서 다른 방법으로 사용 되는 것과는 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-148">If you are operating in a single coordinate system, as the template does with the **SpatialStationaryReferenceFrame**, this process isn't different from what you're otherwise used to in 3D graphics.</span></span> <span data-ttu-id="25b64-149">여기서는 큐브를 회전 하 고 고정 좌표계의 위치를 기준으로 모델 매트릭스를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-149">Here, we rotate the cube and set the model matrix relative to the position in the stationary coordinate system.</span></span>

<span data-ttu-id="25b64-150">**SpinningCubeRenderer:: Update**에서:</span><span class="sxs-lookup"><span data-stu-id="25b64-150">From **SpinningCubeRenderer::Update**:</span></span>

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

<span data-ttu-id="25b64-151">**고급 시나리오에 대 한 참고 사항:** 회전 하는 큐브는 단일 참조 프레임 안에 홀로그램을 배치 하는 방법에 대 한 매우 간단한 예입니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-151">**Note about advanced scenarios:** The spinning cube is a very simple example of how to position a hologram within a single reference frame.</span></span> <span data-ttu-id="25b64-152">동일한 렌더링 된 프레임에서 동시에 [여러 SpatialCoordinateSystems를 사용할](coordinate-systems-in-directx.md) 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-152">It's also possible to [use multiple SpatialCoordinateSystems](coordinate-systems-in-directx.md) in the same rendered frame, at the same time.</span></span>

### <a name="update-constant-buffer-data"></a><span data-ttu-id="25b64-153">상수 버퍼 데이터 업데이트</span><span class="sxs-lookup"><span data-stu-id="25b64-153">Update constant buffer data</span></span>

<span data-ttu-id="25b64-154">콘텐츠에 대 한 모델 변환은 평소와 같이 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-154">Model transforms for content are updated as usual.</span></span> <span data-ttu-id="25b64-155">이제 렌더링할 좌표계에 대해 유효한 변환을 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-155">By now, you will have computed valid transforms for the coordinate system you'll be rendering in.</span></span>

<span data-ttu-id="25b64-156">**SpinningCubeRenderer:: Update**에서:</span><span class="sxs-lookup"><span data-stu-id="25b64-156">From **SpinningCubeRenderer::Update**:</span></span>

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

<span data-ttu-id="25b64-157">보기 및 프로젝션 변환에 대 한 자세한 정보</span><span class="sxs-lookup"><span data-stu-id="25b64-157">What about view and projection transforms?</span></span> <span data-ttu-id="25b64-158">최상의 결과를 얻으려면 그리기 호출에 대해 거의 준비가 될 때까지 대기 하 고 싶습니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-158">For best results, we want to wait until we're almost ready for our draw calls before we get these.</span></span>

## <a name="render-the-current-frame"></a><span data-ttu-id="25b64-159">현재 프레임을 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-159">Render the current frame</span></span>

<span data-ttu-id="25b64-160">Windows Mixed Reality에서 렌더링 하는 것은 2D 모노 디스플레이에서 렌더링 하는 것과 크게 다르지 않지만 몇 가지 차이점을 고려해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-160">Rendering on Windows Mixed Reality is not much different from rendering on a 2D mono display, but there are some differences you need to be aware of:</span></span>
* <span data-ttu-id="25b64-161">Holographic 프레임 예측은 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-161">Holographic frame predictions are important.</span></span> <span data-ttu-id="25b64-162">프레임이 표시 될 때 예측에 더 가깝습니다. holograms이 더 좋아집니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-162">The closer the prediction is to when your frame is presented, the better your holograms will look.</span></span>
* <span data-ttu-id="25b64-163">Windows Mixed Reality는 카메라 보기를 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-163">Windows Mixed Reality controls the camera views.</span></span> <span data-ttu-id="25b64-164">Holographic 프레임이 나중에 표시 되기 때문에 각 항목에 렌더링 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-164">You need to render to each one because the holographic frame will be presenting them for you later.</span></span>
* <span data-ttu-id="25b64-165">인스턴스 그리기를 렌더링 대상 배열에 사용 하 여 스테레오 렌더링을 수행 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-165">Stereo rendering is recommended to be accomplished using instanced drawing to a render target array.</span></span> <span data-ttu-id="25b64-166">Holographic 앱 템플릿은 렌더링 대상 뷰를 **Texture2DArray**에 사용 하는 렌더링 대상 배열에 대해 인스턴스화된 그리기의 권장 되는 방법을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-166">The holographic app template uses the recommended approach of instanced drawing to a render target array, which uses a render target view onto a **Texture2DArray**.</span></span>
* <span data-ttu-id="25b64-167">스테레오 인스턴스를 사용 하지 않고 렌더링 하려면 각각 시스템에서 앱에 제공 되는 **Texture2DArray** 의 두 조각 중 하나를 참조 하는 배열 없는 RenderTargetViews (각 눈 마다 하나씩)를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-167">If you want to render without using stereo instancing, you will need to create two non-array RenderTargetViews (one for each eye) that each reference one of the two slices in the **Texture2DArray** provided to the app from the system.</span></span> <span data-ttu-id="25b64-168">이 방법은 일반적으로 인스턴스를 사용 하는 것 보다 훨씬 느리므로 권장 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-168">This is not recommended, as it is typically significantly slower than using instancing.</span></span>

### <a name="get-an-updated-holographicframe-prediction"></a><span data-ttu-id="25b64-169">업데이트 된 HolographicFrame 예측 가져오기</span><span class="sxs-lookup"><span data-stu-id="25b64-169">Get an updated HolographicFrame prediction</span></span>

<span data-ttu-id="25b64-170">프레임 예측을 업데이트 하면 이미지 안정화의 효율성을 향상 시키고 예측 사이의 시간 및 프레임을 사용자에 게 표시 하는 시간 때문에 holograms를 보다 정확 하 게 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-170">Updating the frame prediction enhances the effectiveness of image stabilization and allows for more accurate positioning of holograms due to the shorter time between the prediction and when the frame is visible to the user.</span></span> <span data-ttu-id="25b64-171">프레임 예측은 렌더링 직전에 업데이트 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-171">Ideally update your frame prediction just before rendering.</span></span>

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a><span data-ttu-id="25b64-172">각 카메라에 렌더링</span><span class="sxs-lookup"><span data-stu-id="25b64-172">Render to each camera</span></span>

<span data-ttu-id="25b64-173">예측에서 카메라의 집합에 대 한 루프를 실행 하 고이 집합의 각 카메라에 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-173">Loop on the set of camera poses in the prediction, and render to each camera in this set.</span></span>

<span data-ttu-id="25b64-174">**렌더링 패스 설정**</span><span class="sxs-lookup"><span data-stu-id="25b64-174">**Set up your rendering pass**</span></span>

<span data-ttu-id="25b64-175">Windows Mixed Reality에서는 stereoscopic 렌더링을 사용 하 여 깊이의 효과를 높이고 stereoscopically를 렌더링 하므로 왼쪽 및 오른쪽 디스플레이가 모두 활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-175">Windows Mixed Reality uses stereoscopic rendering to enhance the illusion of depth and to render stereoscopically, so both the left and the right display are active.</span></span> <span data-ttu-id="25b64-176">Stereoscopic 렌더링을 사용 하는 경우 두 표시 간의 오프셋이 있습니다. 즉, 두뇌는 실제 깊이로 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-176">With stereoscopic rendering there is an offset between the two displays, which the brain can reconcile as actual depth.</span></span> <span data-ttu-id="25b64-177">이 섹션에서는 Windows Holographic 앱 템플릿의 코드를 사용 하 여 인스턴스를 사용 하는 stereoscopic 렌더링에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-177">This section covers stereoscopic rendering using instancing, using code from the Windows Holographic app template.</span></span>

<span data-ttu-id="25b64-178">각 카메라에는 자체 렌더링 대상 (백 버퍼) 및 뷰 및 프로젝션 매트릭스가 holographic 공간으로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-178">Each camera has its own render target (back buffer), and view and projection matrices, into the holographic space.</span></span> <span data-ttu-id="25b64-179">앱은 카메라 단위로 깊이 버퍼와 같은 다른 카메라 기반 리소스를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-179">Your app will need to create any other camera-based resources - such as the depth buffer - on a per-camera basis.</span></span> <span data-ttu-id="25b64-180">Windows Holographic 앱 템플릿에서 이러한 리소스를 DX:: CameraResources에 함께 묶는 도우미 클래스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-180">In the Windows Holographic app template, we provide a helper class to bundle these resources together in DX::CameraResources.</span></span> <span data-ttu-id="25b64-181">렌더링 대상 뷰를 설정 하 여 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-181">Start by setting up the render target views:</span></span>

<span data-ttu-id="25b64-182">**Appmain:: Render**에서:</span><span class="sxs-lookup"><span data-stu-id="25b64-182">From **AppMain::Render**:</span></span>

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

<span data-ttu-id="25b64-183">**예측을 사용 하 여 카메라에 대 한 보기 및 프로젝션 매트릭스 가져오기**</span><span class="sxs-lookup"><span data-stu-id="25b64-183">**Use the prediction to get the view and projection matrices for the camera**</span></span>

<span data-ttu-id="25b64-184">각 holographic 카메라에 대 한 보기 및 프로젝션 매트릭스가 모든 프레임에서 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-184">The view and projection matrices for each holographic camera will change with every frame.</span></span> <span data-ttu-id="25b64-185">각 holographic 카메라에 대해 상수 버퍼의 데이터를 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-185">Refresh the data in the constant buffer for each holographic camera.</span></span> <span data-ttu-id="25b64-186">예측을 업데이트 한 후와 해당 카메라에 대 한 그리기 호출을 수행 하기 전에이 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-186">Do this after you updated the prediction, and before you make any draw calls for that camera.</span></span>

<span data-ttu-id="25b64-187">**Appmain:: Render**에서:</span><span class="sxs-lookup"><span data-stu-id="25b64-187">From **AppMain::Render**:</span></span>

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

<span data-ttu-id="25b64-188">여기서는 카메라 포즈에서 매트릭스를 가져오는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-188">Here, we show how the matrices are acquired from the camera pose.</span></span> <span data-ttu-id="25b64-189">이 프로세스를 진행 하는 동안 카메라의 현재 뷰포트도 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-189">During this process we also obtain the current viewport for the camera.</span></span> <span data-ttu-id="25b64-190">좌표계를 제공 하는 방법에 유의 하세요 .이 좌표계는 응시를 이해 하는 데 사용한 것과 동일한 좌표계 이며 회전 하는 큐브를 배치 하는 데 사용 하는 것과 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-190">Note how we provide a coordinate system: this is the same coordinate system we used to understand gaze, and it's the same one we used to position the spinning cube.</span></span>


<span data-ttu-id="25b64-191">From **CameraResources:: UpdateViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="25b64-191">From **CameraResources::UpdateViewProjectionBuffer**:</span></span>

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

<span data-ttu-id="25b64-192">각 프레임은 뷰포트를 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-192">The viewport should be set each frame.</span></span> <span data-ttu-id="25b64-193">꼭 짓 점 셰이더 (최소)는 일반적으로 뷰/프로젝션 데이터에 액세스할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-193">Your vertex shader (at least) will generally need access to the view/projection data.</span></span>


<span data-ttu-id="25b64-194">From **CameraResources:: AttachViewProjectionBuffer**:</span><span class="sxs-lookup"><span data-stu-id="25b64-194">From **CameraResources::AttachViewProjectionBuffer**:</span></span>

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

<span data-ttu-id="25b64-195">**카메라 백 버퍼에 렌더링 하 고 깊이 버퍼를 커밋합니다**.</span><span class="sxs-lookup"><span data-stu-id="25b64-195">**Render to the camera back buffer and commit the depth buffer**:</span></span>

<span data-ttu-id="25b64-196">좌표계가 과정이 되지 않는 경우 (예: 추적이 중단 된 경우) 앱에서 해당 프레임에 대해 렌더링할 수 없기 때문에 뷰/프로젝션 데이터를 사용 하기 전에 **TryGetViewTransform** 이 성공 했는지 확인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-196">It's a good idea to check that **TryGetViewTransform** succeeded before trying to use the view/projection data, because if the coordinate system is not locatable (e.g., tracking was interrupted) your app cannot render with it for that frame.</span></span> <span data-ttu-id="25b64-197">**CameraResources** 클래스가 성공적인 업데이트를 나타내는 경우에만이 템플릿은 회전 하는 큐브에서 **렌더링** 을 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-197">The template only calls **Render** on the spinning cube if the **CameraResources** class indicates a successful update.</span></span>

<span data-ttu-id="25b64-198">개발자 또는 사용자가 전 세계에 holograms을 유지 하기 위해 Windows Mixed Reality에는 [이미지 안정화](hologram-stability.md)기능이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-198">To keep holograms where a developer or a user puts them in the world, Windows Mixed Reality includes features for [image stabilization](hologram-stability.md).</span></span> <span data-ttu-id="25b64-199">이미지 안정화를 사용 하면 렌더링 파이프라인에서 내재 된 대기 시간을 숨겨 사용자에 게 가장 적합 한 holographic 환경을 보장할 수 있습니다. 포커스 지점을 지정 하 여 이미지 안정화를 향상 시킬 수도 있고, 실시간으로 최적화 된 이미지를 계산 하기 위한 깊이 버퍼가 제공 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-199">Image stabilization helps hide the latency inherent in a rendering pipeline to ensure the best holographic experiences for users; a focus point may be specified to enhance image stabilization even further, or a depth buffer may be provided to compute optimized image stabilization in real time.</span></span>

<span data-ttu-id="25b64-200">최상의 결과를 위해 앱은 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API를 사용 하 여 깊이 버퍼를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-200">For best results, your app should provide a depth buffer using the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API.</span></span> <span data-ttu-id="25b64-201">Windows Mixed Reality는 깊이 버퍼의 기 하 도형 정보를 사용 하 여 이미지 안정화를 실시간으로 최적화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-201">Windows Mixed Reality can then use geometry information from the depth buffer to optimize image stabilization in real time.</span></span> <span data-ttu-id="25b64-202">Windows Holographic 앱 템플릿은 기본적으로 응용 프로그램의 깊이 버퍼를 커밋 하 여 홀로그램 안정성을 최적화 하도록 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-202">The Windows Holographic app template commits the app's depth buffer by default, helping optimize hologram stability.</span></span>

<span data-ttu-id="25b64-203">**Appmain:: Render**에서:</span><span class="sxs-lookup"><span data-stu-id="25b64-203">From **AppMain::Render**:</span></span>

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
><span data-ttu-id="25b64-204">Windows는 GPU에서 깊이 질감을 처리 하므로 깊이 버퍼를 셰이더 리소스로 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-204">Windows will process your depth texture on the GPU, so it must be possible to use your depth buffer as a shader resource.</span></span> <span data-ttu-id="25b64-205">사용자가 만든 ID3D11Texture2D는 형식이 아닌 형식 이어야 하며 셰이더 리소스 뷰로 바인딩되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-205">The ID3D11Texture2D that you create should be in a typeless format and it should be bound as a shader resource view.</span></span> <span data-ttu-id="25b64-206">이미지 안정화를 위해 커밋될 수 있는 깊이 질감을 만드는 방법에 대 한 예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-206">Here is an example of how to create a depth texture that can be committed for image stabilization.</span></span>

<span data-ttu-id="25b64-207">**CommitDirect3D11DepthBuffer에 대 한 깊이 버퍼 리소스 생성**코드:</span><span class="sxs-lookup"><span data-stu-id="25b64-207">Code for **Depth buffer resource creation for CommitDirect3D11DepthBuffer**:</span></span>

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

<span data-ttu-id="25b64-208">**Holographic 내용 그리기**</span><span class="sxs-lookup"><span data-stu-id="25b64-208">**Draw holographic content**</span></span>

<span data-ttu-id="25b64-209">Windows Holographic 앱 템플릿은 인스턴스 기 하 도형을 크기 2의 Texture2DArray로 그리는 권장 기법을 사용 하 여 스테레오에서 콘텐츠를 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-209">The Windows Holographic app template renders content in stereo by using the recommended technique of drawing instanced geometry to a Texture2DArray of size 2.</span></span> <span data-ttu-id="25b64-210">이에 대 한 인스턴스 및 Windows Mixed Reality에서 작동 하는 방식을 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-210">Let's look at the instancing part of this, and how it works on Windows Mixed Reality.</span></span>

<span data-ttu-id="25b64-211">From **SpinningCubeRenderer:: Render**:</span><span class="sxs-lookup"><span data-stu-id="25b64-211">From **SpinningCubeRenderer::Render**:</span></span>

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

<span data-ttu-id="25b64-212">각 인스턴스는 상수 버퍼에서 다른 뷰/프로젝션 행렬에 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-212">Each instance accesses a different view/projection matrix from the constant buffer.</span></span> <span data-ttu-id="25b64-213">다음은 두 행렬의 배열인 상수 버퍼 구조입니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-213">Here's the constant buffer structure, which is just an array of 2 matrices.</span></span>

<span data-ttu-id="25b64-214">Hlsl에서 **VPRTVertexShader hlsl**에 포함 된 **VertexShaderShared**.</span><span class="sxs-lookup"><span data-stu-id="25b64-214">From **VertexShaderShared.hlsl**, included by **VPRTVertexShader.hlsl**:</span></span>

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

<span data-ttu-id="25b64-215">각 픽셀에 대해 렌더링 대상 배열 인덱스를 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-215">The render target array index must be set for each pixel.</span></span> <span data-ttu-id="25b64-216">다음 코드 조각에서 viewId는 **SV_RenderTargetArrayIndex** 의미 체계에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-216">In the following snippet, output.viewId is mapped to the **SV_RenderTargetArrayIndex** semantic.</span></span> <span data-ttu-id="25b64-217">이를 위해서는 선택적 Direct3D 11.3 기능을 지원 해야 합니다 .이 기능을 사용 하면 모든 셰이더 단계에서 렌더링 대상 배열 인덱스 의미 체계를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-217">Note that this requires support for an optional Direct3D 11.3 feature, which allows the render target array index semantic to be set from any shader stage.</span></span>

<span data-ttu-id="25b64-218">From **VPRTVertexShader. hlsl**:</span><span class="sxs-lookup"><span data-stu-id="25b64-218">From **VPRTVertexShader.hlsl**:</span></span>

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

<span data-ttu-id="25b64-219">Hlsl에서 **VPRTVertexShader hlsl**에 포함 된 **VertexShaderShared**.</span><span class="sxs-lookup"><span data-stu-id="25b64-219">From **VertexShaderShared.hlsl**, included by **VPRTVertexShader.hlsl**:</span></span>

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

<span data-ttu-id="25b64-220">이 방법으로 스테레오 렌더링 대상 배열에 그리기를 수행 하는 기존 인스턴스 그리기 기술을 사용 하려는 경우에는 일반적으로 사용 하는 인스턴스 수를 두 배로 그려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-220">If you want to use your existing instanced drawing techniques with this method of drawing to a stereo render target array, all you have to do is draw twice the number of instances you normally have.</span></span> <span data-ttu-id="25b64-221">셰이더에는 **입력. s i d id** 를 2로 나누고, 개체 당 데이터의 버퍼에 인덱싱할 수 있는 원본 인스턴스 id (예:)를 가져옵니다.`int actualIdx = input.instId / 2;`</span><span class="sxs-lookup"><span data-stu-id="25b64-221">In the shader, divide **input.instId** by 2 to get the original instance ID, which can be indexed into (for example) a buffer of per-object data: `int actualIdx = input.instId / 2;`</span></span>

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a><span data-ttu-id="25b64-222">HoloLens에서 스테레오 콘텐츠를 렌더링 하는 방법에 대 한 중요 정보</span><span class="sxs-lookup"><span data-stu-id="25b64-222">Important note about rendering stereo content on HoloLens</span></span>

<span data-ttu-id="25b64-223">Windows Mixed Reality는 모든 셰이더 단계에서 렌더링 대상 배열 인덱스를 설정 하는 기능을 지원 합니다. 일반적으로이 작업은 Direct3D 11에 대 한 의미 체계를 정의 하는 방식 때문에 기 하 도형 셰이더 단계 에서만 수행할 수 있는 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-223">Windows Mixed Reality supports the ability to set the render target array index from any shader stage; normally, this is a task that could only be done in the geometry shader stage due to the way the semantic is defined for Direct3D 11.</span></span> <span data-ttu-id="25b64-224">여기서는 꼭 짓 점 및 픽셀 셰이더 단계 집합만 사용 하 여 렌더링 파이프라인을 설정 하는 방법의 전체 예제를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-224">Here, we show a complete example of how to set up a rendering pipeline with just the vertex and pixel shader stages set.</span></span> <span data-ttu-id="25b64-225">셰이더 코드는 위에서 설명한 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-225">The shader code is as described above.</span></span>

<span data-ttu-id="25b64-226">From **SpinningCubeRenderer:: Render**:</span><span class="sxs-lookup"><span data-stu-id="25b64-226">From **SpinningCubeRenderer::Render**:</span></span>

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

### <a name="important-note-about-rendering-on-non-hololens-devices"></a><span data-ttu-id="25b64-227">HoloLens가 아닌 장치에서 렌더링 하는 방법에 대 한 중요 정보</span><span class="sxs-lookup"><span data-stu-id="25b64-227">Important note about rendering on non-HoloLens devices</span></span>

<span data-ttu-id="25b64-228">꼭 짓 점 셰이더의 렌더링 대상 배열 인덱스를 설정 하려면 그래픽 드라이버가 선택적 Direct3D 11.3 기능을 지원 해야 합니다 .이 기능은 HoloLens에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-228">Setting the render target array index in the vertex shader requires that the graphics driver supports an optional Direct3D 11.3 feature, which HoloLens does support.</span></span> <span data-ttu-id="25b64-229">앱은 렌더링을 위한 해당 기법도 안전 하 게 구현할 수 있으며 모든 요구 사항은 Microsoft HoloLens에서 실행 하기 위해 충족 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-229">Your app may be able to safely implement just that technique for rendering, and all requirements will be met for running on the Microsoft HoloLens.</span></span>

<span data-ttu-id="25b64-230">Holographic 앱에 대 한 강력한 개발 도구인 HoloLens 에뮬레이터를 사용 하 고 Windows 10 Pc에 연결 된 Windows Mixed Reality 모던 헤드셋 장치를 지 원하는 경우를 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-230">It may be the case that you want to use the HoloLens emulator as well, which can be a powerful development tool for your holographic app - and support Windows Mixed Reality immersive headset devices that are attached to Windows 10 PCs.</span></span> <span data-ttu-id="25b64-231">비 HoloLens 렌더링 경로에 대 한 지원. 따라서 모든 Windows Mixed Reality의 경우 Windows Holographic 앱 템플릿에도 빌드됩니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-231">Support for the non-HoloLens rendering path - and therefore, for all of Windows Mixed Reality - is also built into the Windows Holographic app template.</span></span> <span data-ttu-id="25b64-232">템플릿 코드에서 개발 PC의 GPU에서 holographic 앱을 실행할 수 있도록 하는 코드를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-232">In the template code, you will find code to enable your holographic app to run on the GPU in your development PC.</span></span> <span data-ttu-id="25b64-233">**DeviceResources** 클래스가이 선택적 기능 지원을 확인 하는 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-233">Here is how the **DeviceResources** class checks for this optional feature support.</span></span>

<span data-ttu-id="25b64-234">From **DeviceResources:: CreateDeviceResources**:</span><span class="sxs-lookup"><span data-stu-id="25b64-234">From **DeviceResources::CreateDeviceResources**:</span></span>

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

<span data-ttu-id="25b64-235">이 선택적 기능 없이 렌더링을 지원 하려면 앱에서 geometry 셰이더를 사용 하 여 렌더링 대상 배열 인덱스를 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-235">To support rendering without this optional feature, your app must use a geometry shader to set the render target array index.</span></span> <span data-ttu-id="25b64-236">이 코드 조각은 **VSSetConstantBuffers** *뒤* 에 추가 *되 고,* 이전 섹션에 표시 된 코드 예제의 **pssetshader** 이전에는 HoloLens에서 스테레오를 렌더링 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-236">This snippet would be added *after* **VSSetConstantBuffers**, and *before* **PSSetShader** in the code example shown in the previous section that explains how to render stereo on HoloLens.</span></span>

<span data-ttu-id="25b64-237">From **SpinningCubeRenderer:: Render**:</span><span class="sxs-lookup"><span data-stu-id="25b64-237">From **SpinningCubeRenderer::Render**:</span></span>

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

<span data-ttu-id="25b64-238">**HLSL 참고 사항**: 이 경우 TEXCOORD0와 같이 항상 허용 되는 셰이더 의미 체계를 사용 하 여 렌더링 대상 배열 인덱스를 기 하 도형 셰이더에 전달 하는 약간 수정 된 꼭 짓 점 셰이더도 로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-238">**HLSL NOTE**: In this case, you must also load a slightly modified vertex shader that passes the render target array index to the geometry shader using an always-allowed shader semantic, such as TEXCOORD0.</span></span> <span data-ttu-id="25b64-239">기 하 도형 셰이더는 작업을 수행할 필요가 없습니다. 템플릿 기 하 도형 셰이더는 SV_RenderTargetArrayIndex 의미 체계를 설정 하는 데 사용 되는 렌더링 대상 배열 인덱스를 제외 하 고 모든 데이터를 통과 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-239">The geometry shader does not have to do any work; the template geometry shader passes through all data, with the exception of the render target array index, which is used to set the SV_RenderTargetArrayIndex semantic.</span></span>

<span data-ttu-id="25b64-240">Hlsl에 대 한 앱 템플릿 코드 **GeometryShader**:</span><span class="sxs-lookup"><span data-stu-id="25b64-240">App template code for **GeometryShader.hlsl**:</span></span>

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

## <a name="present"></a><span data-ttu-id="25b64-241">있음</span><span class="sxs-lookup"><span data-stu-id="25b64-241">Present</span></span>

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a><span data-ttu-id="25b64-242">Holographic 프레임을 사용 하 여 스왑 체인을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-242">Enable the holographic frame to present the swap chain</span></span>

<span data-ttu-id="25b64-243">Windows Mixed Reality를 사용 하는 경우 시스템은 스왑 체인을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-243">With Windows Mixed Reality, the system controls the swap chain.</span></span> <span data-ttu-id="25b64-244">그러면 시스템에서 각 holographic 카메라에 대 한 프레임을 관리 하 여 고품질 사용자 환경을 보장 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-244">The system then manages presenting frames to each holographic camera to ensure a high quality user experience.</span></span> <span data-ttu-id="25b64-245">또한 각 카메라에 대해 이미지 안정화 또는 혼합 현실 캡처와 같은 시스템 측면을 최적화 하기 위해 각 프레임을 업데이트 하는 뷰포트를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-245">It also provides a viewport update each frame, for each camera, to optimize aspects of the system such as image stabilization or Mixed Reality Capture.</span></span> <span data-ttu-id="25b64-246">따라서 DirectX를 사용 하는 holographic 앱은 DXGI 스왑 체인에 **존재** 하는을 호출 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-246">So, a holographic app using DirectX doesn't call **Present** on a DXGI swap chain.</span></span> <span data-ttu-id="25b64-247">대신 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> 클래스를 사용 하 여 그리기를 완료 한 후 프레임에 대 한 모든 swapchain을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-247">Instead, you use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class to present all swapchains for a frame once you're done drawing it.</span></span>

<span data-ttu-id="25b64-248">**DeviceResources::P 다시 보낸**위치:</span><span class="sxs-lookup"><span data-stu-id="25b64-248">From **DeviceResources::Present**:</span></span>

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

<span data-ttu-id="25b64-249">기본적으로이 API는 프레임이 반환 될 때까지 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-249">By default, this API waits for the frame to finish before it returns.</span></span> <span data-ttu-id="25b64-250">Holographic apps는 새 프레임에서 작업을 시작 하기 전에 이전 프레임이 완료 될 때까지 기다려야 합니다 .이는 대기 시간을 줄이고 프레임 예측에서 더 나은 결과를 허용 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-250">Holographic apps should wait for the previous frame to finish before starting work on a new frame, because this reduces latency and allows for better results from holographic frame predictions.</span></span> <span data-ttu-id="25b64-251">이것은 하드 규칙이 아니며, 렌더링을 위해 한 화면 새로 고침 보다 오랜 시간이 걸리는 프레임을 사용 하는 경우 HolographicFramePresentWaitBehavior 매개 변수를 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>에 전달 하 여이 대기를 비활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-251">This isn't a hard rule, and if you have frames that take longer than one screen refresh to render you can disable this wait by passing the HolographicFramePresentWaitBehavior parameter to <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>.</span></span> <span data-ttu-id="25b64-252">이 경우에는 GPU에서 연속 로드를 유지 하기 위해 비동기 렌더링 스레드를 사용할 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-252">In this case, you would likely use an asynchronous rendering thread in order to maintain a continuous load on the GPU.</span></span> <span data-ttu-id="25b64-253">HoloLens 장치의 새로 고침 빈도는 60hz입니다. 단, 한 프레임의 기간은 약 16 밀리초입니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-253">Note that the refresh rate of the HoloLens device is 60hz, where one frame has a duration of approximately 16 ms.</span></span> <span data-ttu-id="25b64-254">모던 헤드셋 장치의 범위는 60hz에서 90hz;입니다. 90 hz에서 디스플레이를 새로 고치면 각 프레임의 기간이 약 11 밀리초가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-254">Immersive headset devices can range from 60hz to 90hz; when refreshing the display at 90 hz, each frame will have a duration of approximately 11 ms.</span></span>

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a><span data-ttu-id="25b64-255">HolographicFrame와 협력 하 여 DeviceLost 시나리오를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-255">Handle DeviceLost scenarios in cooperation with the HolographicFrame</span></span>

<span data-ttu-id="25b64-256">DirectX 11 앱은 일반적으로 **DeviceLost** 오류가 있는지 확인 하기 위해 DXGI 스왑 체인의 **present** 함수에서 반환 된 HRESULT를 확인 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-256">DirectX 11 apps would typically want to check the HRESULT returned by the DXGI swap chain's **Present** function to find out if there was a **DeviceLost** error.</span></span> <span data-ttu-id="25b64-257"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> 클래스는이를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-257">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class handles this for you.</span></span> <span data-ttu-id="25b64-258">반환 되는 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> 를 검사 하 여 Direct3D 장치 및 장치 기반 리소스를 해제 하 고 다시 만들어야 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-258">Inspect the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> it returns to find out if you need to release and recreate the Direct3D device and device-based resources.</span></span>

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

<span data-ttu-id="25b64-259">Direct3D 장치를 분실 한 경우 다시 만든 경우 새 장치를 사용 하 여 시작 하도록 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> 에 지시 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-259">Note that if the Direct3D device was lost, and you did recreate it, you have to tell the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> to start using the new device.</span></span> <span data-ttu-id="25b64-260">이 장치에 대해 스왑 체인이 다시 작성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-260">The swap chain will be recreated for this device.</span></span>

<span data-ttu-id="25b64-261">From **DeviceResources:: InitializeUsingHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="25b64-261">From **DeviceResources::InitializeUsingHolographicSpace**:</span></span>

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

<span data-ttu-id="25b64-262">프레임이 표시 되 면 주 프로그램 루프로 돌아가서 다음 프레임으로 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-262">Once your frame is presented, you can return back to the main program loop and allow it to continue to the next frame.</span></span>

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a><span data-ttu-id="25b64-263">하이브리드 그래픽 Pc 및 혼합 현실 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="25b64-263">Hybrid graphics PCs and mixed reality applications</span></span>

<span data-ttu-id="25b64-264">Windows 10 크리에이터 업데이트 Pc는 개별 및 통합 Gpu를 **모두** 사용 하 여 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-264">Windows 10 Creators Update PCs may be configured with **both** discrete and integrated GPUs.</span></span> <span data-ttu-id="25b64-265">이러한 유형의 컴퓨터를 사용 하 여 Windows는 헤드셋이 연결 된 어댑터를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-265">With these types of computers, Windows will choose the adapter the headset is connected to.</span></span> <span data-ttu-id="25b64-266">응용 프로그램에서 생성 하는 DirectX 장치가 동일한 어댑터를 사용 하는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-266">Applications must ensure the DirectX device it creates uses the same adapter.</span></span>

<span data-ttu-id="25b64-267">가장 일반적인 Direct3D 샘플 코드는 하이브리드 시스템이 헤드셋에 사용 되는 것과 다를 수 있는 기본 하드웨어 어댑터를 사용 하 여 DirectX 장치를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-267">Most general Direct3D sample code demonstrates creating a DirectX device using the default hardware adapter, which on a hybrid system may not be the same as the one used for the headset.</span></span>

<span data-ttu-id="25b64-268">이로 인해 발생할 수 있는 문제를 해결 하려면 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>의 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> 를 사용 합니다. PrimaryAdapterId () 또는 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>. AdapterId ().</span><span class="sxs-lookup"><span data-stu-id="25b64-268">To work around any issues this may cause, use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterId</a> from either <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>.PrimaryAdapterId() or <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>.AdapterId().</span></span> <span data-ttu-id="25b64-269">그런 다음이 adapterId를 사용 하 여 IDXGIFactory4 Adapterbyluid를 사용 하는 올바른 DXGIAdapter를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-269">This adapterId can then be used to select the right DXGIAdapter using IDXGIFactory4.EnumAdapterByLuid.</span></span>

<span data-ttu-id="25b64-270">From **DeviceResources:: InitializeUsingHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="25b64-270">From **DeviceResources::InitializeUsingHolographicSpace**:</span></span>

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

<span data-ttu-id="25b64-271">**Idxgid 어댑터를 사용 하 여 DeviceResources:: CreateDeviceResources를 업데이트** 하는 코드</span><span class="sxs-lookup"><span data-stu-id="25b64-271">Code to **update DeviceResources::CreateDeviceResources to use IDXGIAdapter**</span></span>

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

<span data-ttu-id="25b64-272">**하이브리드 그래픽 및 미디어 파운데이션**</span><span class="sxs-lookup"><span data-stu-id="25b64-272">**Hybrid graphics and Media Foundation**</span></span>

<span data-ttu-id="25b64-273">하이브리드 시스템에서 미디어 파운데이션를 사용 하면 비디오가 렌더링 되지 않거나 비디오 질감이 손상 되는 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-273">Using Media Foundation on hybrid systems may cause issues where video will not render or video texture is corrupt.</span></span> <span data-ttu-id="25b64-274">이는 미디어 파운데이션가 위에서 설명한 대로 시스템 동작을 기본값으로 수행 하기 때문에 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-274">This can occur because Media Foundation is defaulting to a system behavior as mentioned above.</span></span> <span data-ttu-id="25b64-275">일부 시나리오에서는 다중 스레딩을 지원 하기 위해 별도의 ID3D11Device를 만들어야 하며, 올바른 생성 플래그가 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-275">In some scenarios, creating a separate ID3D11Device is required to support multi-threading and the correct creation flags are set.</span></span>

<span data-ttu-id="25b64-276">ID3D11Device를 초기화할 때는 D3D11_CREATE_DEVICE_VIDEO_SUPPORT 플래그를 D3D11_CREATE_DEVICE_FLAG의 일부로 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-276">When initializing the ID3D11Device, D3D11_CREATE_DEVICE_VIDEO_SUPPORT flag must be defined as part of the D3D11_CREATE_DEVICE_FLAG.</span></span> <span data-ttu-id="25b64-277">장치 및 컨텍스트를 만든 후에는 <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">Setmultithreadprotected</a> 를 호출 하 여 다중 스레딩을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-277">Once the device and context is created, call <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> to enable multithreading.</span></span> <span data-ttu-id="25b64-278">장치를 <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>에 연결 하려면 <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager:: resetdevice</a> 함수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="25b64-278">To associate the device with the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, use the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice</a> function.</span></span>

<span data-ttu-id="25b64-279">**ID3D11Device와 IMFDXGIDeviceManager를 연결 하는**코드:</span><span class="sxs-lookup"><span data-stu-id="25b64-279">Code to **associate a ID3D11Device with IMFDXGIDeviceManager**:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="25b64-280">참조</span><span class="sxs-lookup"><span data-stu-id="25b64-280">See also</span></span>
* [<span data-ttu-id="25b64-281">DirectX의 좌표계</span><span class="sxs-lookup"><span data-stu-id="25b64-281">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="25b64-282">Using the HoloLens emulator(HoloLens 에뮬레이터 사용)</span><span class="sxs-lookup"><span data-stu-id="25b64-282">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
