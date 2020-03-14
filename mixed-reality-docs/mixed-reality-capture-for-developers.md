---
title: 개발자를 위한 혼합 현실 캡처
description: 개발자를 위한 혼합 현실 캡처에 대 한 모범 사례입니다.
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: mrc, 사진, 비디오, 캡처, 카메라
ms.openlocfilehash: 72600f889997c96a629faebc35aba4b4841d4d8b
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375970"
---
# <a name="mixed-reality-capture-for-developers"></a><span data-ttu-id="67937-104">개발자를 위한 혼합 현실 캡처</span><span class="sxs-lookup"><span data-stu-id="67937-104">Mixed reality capture for developers</span></span>

> [!NOTE]
> <span data-ttu-id="67937-105">HoloLens 2에 대 한 새로운 MRC 기능에 대 한 지침은 아래의 [PV 카메라에서 렌더링](#render-from-the-pv-camera-opt-in) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="67937-105">See [Render from the PV camera](#render-from-the-pv-camera-opt-in) below for guidance on a new MRC capability for HoloLens 2.</span></span>

<span data-ttu-id="67937-106">사용자는 언제 든 지 [혼합 현실 캡처](mixed-reality-capture.md) (mrc) 사진 또는 비디오를 만들 수 있으므로 응용 프로그램을 개발할 때 고려해 야 할 몇 가지 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67937-106">Since a user could take a [mixed reality capture](mixed-reality-capture.md) (MRC) photo or video at any time, there are a few things that you should keep in mind when developing your application.</span></span> <span data-ttu-id="67937-107">여기에는 MRC 시각적 품질에 대 한 모범 사례와 Mrc가 캡처될 때 시스템 변경 내용에 대 한 응답성이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="67937-107">This includes best practices for MRC visual quality and being responsive to system changes while MRCs are being captured.</span></span>

<span data-ttu-id="67937-108">또한 개발자는 혼합 현실 캡처 및 삽입을 앱에 원활 하 게 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67937-108">Developers can also seamlessly integrate mixed reality capture and insertion into their apps.</span></span>

<span data-ttu-id="67937-109">HoloLens의 MRC (처음 생성)는 720p까지 비디오와 사진을 지원 하 고, HoloLens 2의 MRC는 최대 1080p까지 비디오를 지원 하 고 최대 4K 해상도로 사진 비디오를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="67937-109">MRC on HoloLens (first-generation) supports videos and photos up to 720p, while MRC on HoloLens 2 supports videos up to 1080p and photos up to 4K resolution.</span></span>

## <a name="the-importance-of-quality-mrc"></a><span data-ttu-id="67937-110">품질 MRC의 중요도</span><span class="sxs-lookup"><span data-stu-id="67937-110">The importance of quality MRC</span></span>

<span data-ttu-id="67937-111">혼합 현실에서 캡처한 사진과 비디오는 사용자가 앱을 가질 수 있는 첫 번째 노출이 될 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="67937-111">Mixed reality captured photos and videos are likely the first exposure a user will have of your app.</span></span> <span data-ttu-id="67937-112">Microsoft Store 페이지의 혼합 현실 스크린샷 또는 소셜 네트워크에서 MRCs를 공유 하는 다른 사용자의 스크린샷</span><span class="sxs-lookup"><span data-stu-id="67937-112">Whether as mixed reality screenshots on your Microsoft Store page or from other users sharing MRCs on social networks.</span></span> <span data-ttu-id="67937-113">MRC를 사용 하 여 앱을 시연 하 고, 사용자를 교육 하 고, 혼합 세계 상호 작용을 공유 하 고, 사용자 연구 및 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67937-113">You can use MRC to demo your app, educate users, encourage users to share their mixed world interactions, and for user research and problem solving.</span></span>

## <a name="how-mrc-impacts-your-app"></a><span data-ttu-id="67937-114">MRC가 앱에 미치는 영향</span><span class="sxs-lookup"><span data-stu-id="67937-114">How MRC impacts your app</span></span>

### <a name="enabling-mrc-in-your-app"></a><span data-ttu-id="67937-115">앱에서 MRC 사용</span><span class="sxs-lookup"><span data-stu-id="67937-115">Enabling MRC in your app</span></span>

<span data-ttu-id="67937-116">기본적으로 앱은 사용자가 혼합 된 현실 캡처를 수행할 수 있도록 하기 위해 아무것도 수행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="67937-116">By default, an app does not have to do anything to enable users to take mixed reality captures.</span></span>

### <a name="enabling-improved-alignment-for-mrc-in-your-app"></a><span data-ttu-id="67937-117">앱에서 MRC에 대 한 향상 된 맞춤 사용</span><span class="sxs-lookup"><span data-stu-id="67937-117">Enabling improved alignment for MRC in your app</span></span>

<span data-ttu-id="67937-118">기본적으로 혼합 현실 캡처는 올바른 눈동자의 holographic 출력을 photo/video (PV) 카메라와 결합 합니다.</span><span class="sxs-lookup"><span data-stu-id="67937-118">By default, mixed reality capture combines the right eye's holographic output with the photo/video (PV) camera.</span></span> <span data-ttu-id="67937-119">이러한 두 소스는 현재 실행 중인 몰입 형 앱에 의해 설정 된 포커스 지점을 사용 하 여 결합 됩니다.</span><span class="sxs-lookup"><span data-stu-id="67937-119">These two sources are combined using the focus point set by the currently running immersive app.</span></span>

<span data-ttu-id="67937-120">즉, PV 카메라와 오른쪽 디스플레이 사이의 물리적인 거리가 holograms 포커스 평면 외부에 있는도 정렬 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="67937-120">This means that holograms outside the focus plane won't align as well (due to the physical distance between the PV camera and the right display).</span></span>

#### <a name="set-the-focus-point"></a><span data-ttu-id="67937-121">포커스 지점 설정</span><span class="sxs-lookup"><span data-stu-id="67937-121">Set the focus point</span></span>

<span data-ttu-id="67937-122">모던 앱 (HoloLens)은 안정화 평면을 원하는 곳의 [포커스 지점을](focus-point-in-unity.md) 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67937-122">Immersive apps (on HoloLens) should set the [focus point](focus-point-in-unity.md) of where they want their stabilization plane to be.</span></span> <span data-ttu-id="67937-123">이렇게 하면 헤드셋과 혼합 현실 캡처 모두에서 최상의 맞춤을 보장 합니다.</span><span class="sxs-lookup"><span data-stu-id="67937-123">This ensures the best alignment in both the headset and in mixed reality capture.</span></span>

<span data-ttu-id="67937-124">포커스 지점이 설정 되지 않은 경우 안정화 평면의 기본값은 2 미터입니다.</span><span class="sxs-lookup"><span data-stu-id="67937-124">If a focus point is not set, the stabilization plane will default to two meters.</span></span>

#### <a name="render-from-the-pv-camera-opt-in"></a><span data-ttu-id="67937-125">PV 카메라에서 렌더링 (옵트인)</span><span class="sxs-lookup"><span data-stu-id="67937-125">Render from the PV camera (opt-in)</span></span>

<span data-ttu-id="67937-126">HoloLens 2는 혼합 현실 캡처를 실행 하는 동안에는 몰입 형 앱이 **PV 카메라에서 렌더링** 하는 기능을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="67937-126">HoloLens 2 adds the ability for an immersive app to **render from the PV camera** while mixed reality capture is running.</span></span> <span data-ttu-id="67937-127">앱이 추가 렌더링을 올바르게 지원 하도록 하려면 앱에서이 기능을 옵트인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67937-127">To ensure the app supports the additional render correctly, the app has to opt-in to this functionality.</span></span>

<span data-ttu-id="67937-128">PV 카메라의 렌더링은 기본 MRC 환경에 비해 다음과 같은 향상 된 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="67937-128">Render from the PV camera offers the following improvements over the default MRC experience:</span></span>
* <span data-ttu-id="67937-129">기본 MRC에서 볼 수 있는 것과 같은 거리에는 오프셋을 포함 하는 대신 실제 환경 및 손 (근거리 상호 작용의 경우)에 대 한 홀로그램 맞춤을 모든 거리에서 정확 하 게 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67937-129">Hologram alignment to both your physical environment and hands (for near interactions) should be accurate at all distances, instead of having an offset at distances other than the focus point as you might see in the default MRC.</span></span>
* <span data-ttu-id="67937-130">V RC 출력에 대 한 holograms를 렌더링 하는 데 사용 되지 않으므로 헤드셋의 올바른 눈이 손상 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="67937-130">The right eye in the headset won't be compromised, as it won't be used to render the holograms for the MRC output.</span></span>

<span data-ttu-id="67937-131">PV 카메라에서 렌더링을 사용 하도록 설정 하는 세 가지 단계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67937-131">There are three steps to enable rendering from the PV camera:</span></span>
1. <span data-ttu-id="67937-132">PhotoVideoCamera HolographicViewConfiguration 사용</span><span class="sxs-lookup"><span data-stu-id="67937-132">Enable the PhotoVideoCamera HolographicViewConfiguration</span></span>
2. <span data-ttu-id="67937-133">추가 HolographicCamera render를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="67937-133">Handle the additional HolographicCamera render</span></span>
3. <span data-ttu-id="67937-134">이 추가 HolographicCamera에서 셰이더 및 코드가 올바르게 렌더링 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="67937-134">Verify your shaders and code render correctly from this additional HolographicCamera</span></span>

##### <a name="enable-the-photovideocamera-holographicviewconfiguration"></a><span data-ttu-id="67937-135">PhotoVideoCamera HolographicViewConfiguration 사용</span><span class="sxs-lookup"><span data-stu-id="67937-135">Enable the PhotoVideoCamera HolographicViewConfiguration</span></span>

<span data-ttu-id="67937-136">옵트인 (opt in) 하려면 앱에서 PhotoVideoCamera의 [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration)을 사용 하도록 설정 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="67937-136">To opt-in, an app simply enables the PhotoVideoCamera's [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration):</span></span>
```csharp
var display = Windows.Graphics.Holographic.HolographicDisplay.GetDefault();
var view = display.TryGetViewConfiguration(Windows.Graphics.Holographic.HolographicViewConfiguration.PhotoVideoCamera);
if (view != null)
{
   view.IsEnabled = true;
}
```

##### <a name="handle-the-additional-holographiccamera-render-in-directx"></a><span data-ttu-id="67937-137">DirectX에서 추가 HolographicCamera render를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="67937-137">Handle the additional HolographicCamera render in DirectX</span></span>

<span data-ttu-id="67937-138">앱이 PV 카메라에서 렌더링 하도록 옵트인 (opt in) 하 고 혼합 현실 캡처를 시작 하면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="67937-138">When the app has opt-in to render from the PV camera and mixed reality capture starts:</span></span>
1. <span data-ttu-id="67937-139">HolographicSpace의 CameraAdded 이벤트가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="67937-139">HolographicSpace's CameraAdded event will fire.</span></span> <span data-ttu-id="67937-140">지금은 앱에서 카메라를 처리할 수 없는 경우이 이벤트가 지연 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67937-140">This event can be deferred if the app cannot handle the camera at this time.</span></span>
2. <span data-ttu-id="67937-141">이벤트가 완료 되 면 (그리고 처리 되지 않은 지연과 없음) HolographicCamera는 다음 HolographicFrame의 Ad 카메라 목록에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="67937-141">Once the event has completed (and there are no outstanding deferrals) the HolographicCamera will appear in the next HolographicFrame's AddedCameras list.</span></span>

<span data-ttu-id="67937-142">혼합 현실 캡처가 중지 될 때 (또는 혼합 현실 캡처를 실행 하는 동안 앱에서 뷰 구성을 사용 하지 않도록 설정 하는 경우) HolographicCamera는 다음 HolographicFrame의 RemovedCameras 목록에 표시 되 고 HolographicSpace의 CameraRemoved 이벤트가 발생 합니다. 시키고.</span><span class="sxs-lookup"><span data-stu-id="67937-142">When mixed reality capture stops (or if the app disables the view configuration while mixed reality capture is running): the HolographicCamera will appear in the next HolographicFrame's RemovedCameras list and the HolographicSpace's CameraRemoved event will fire.</span></span>

<span data-ttu-id="67937-143">HolographicCamera에는 카메라가 속한 구성을 식별 하는 데 도움이 되는 [Viewconfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) 속성이 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="67937-143">A [ViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) property has been added to HolographicCamera to help identify the configuration a camera belongs to.</span></span>

##### <a name="handle-the-additional-holographiccamera-render-in-unity"></a><span data-ttu-id="67937-144">Unity에서 추가 HolographicCamera render를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="67937-144">Handle the additional HolographicCamera render in Unity</span></span>

>[!NOTE]
> <span data-ttu-id="67937-145">PV 카메라에서 렌더링 하는 Unity 지원은 개발 중 이며 아직 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="67937-145">Unity support to render from the PV camera is under development and can't be used, yet.</span></span> <span data-ttu-id="67937-146">이 설명서는 PV 카메라의 렌더링을 지 원하는 Unity 빌드를 사용할 수 있을 때 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="67937-146">This documentation will be updated when a build of Unity with support for rendering from the PV camera is available.</span></span>

##### <a name="verify-shaders-and-code-support-additional-cameras"></a><span data-ttu-id="67937-147">셰이더 및 코드에서 추가 카메라 지원 확인</span><span class="sxs-lookup"><span data-stu-id="67937-147">Verify shaders and code support additional cameras</span></span>

<span data-ttu-id="67937-148">혼합 현실 캡처를 실행 하 고 비정상적인 맞춤, 누락 된 콘텐츠 또는 성능 문제를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="67937-148">Run a mixed reality capture and check for unusual alignment, missing content, or performance issues.</span></span> <span data-ttu-id="67937-149">셰이더 및 코드를 적절 하 게 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="67937-149">Update shaders and code as appropriate.</span></span>

<span data-ttu-id="67937-150">추가 카메라에 대 한 렌더링을 지원 하지 않는 특정 장면이 있는 경우 PhotoVideoCamera의 HolographicViewConfiguration을 사용 하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67937-150">If there are certain scenes that cannot support rendering to an additional camera, you can disable the PhotoVideoCamera's HolographicViewConfiguration during them.</span></span>

### <a name="disabling-mrc-in-your-app"></a><span data-ttu-id="67937-151">앱에서 MRC를 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="67937-151">Disabling MRC in your app</span></span>

#### <a name="2d-app"></a><span data-ttu-id="67937-152">2D 앱</span><span class="sxs-lookup"><span data-stu-id="67937-152">2D app</span></span>

<span data-ttu-id="67937-153">혼합 현실 캡처가를 실행 하는 경우 2D 앱은 시각적 콘텐츠를 가립니다 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67937-153">2D apps can choose to have their visual content obscured when mixed reality capture is running by:</span></span>
* <span data-ttu-id="67937-154">[DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-present) 플래그로 제공</span><span class="sxs-lookup"><span data-stu-id="67937-154">Present with the [DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-present) flag</span></span>
* <span data-ttu-id="67937-155">[DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://docs.microsoft.com/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag) 플래그를 사용 하 여 앱의 스왑 체인 만들기</span><span class="sxs-lookup"><span data-stu-id="67937-155">Create the app's swap chain with the [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://docs.microsoft.com/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag) flag</span></span>
* <span data-ttu-id="67937-156">Windows 10 5 월 2019 업데이트를 사용 하 여 ApplicationView의 [IsScreenCaptureEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled) 을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="67937-156">With the Windows 10 May 2019 Update, setting ApplicationView's [IsScreenCaptureEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled)</span></span>

#### <a name="immersive-app"></a><span data-ttu-id="67937-157">몰입 형 앱</span><span class="sxs-lookup"><span data-stu-id="67937-157">Immersive app</span></span>

<span data-ttu-id="67937-158">몰입 형 앱은 다음과 같은 방법으로 혼합 현실 캡처에서 해당 시각적 콘텐츠를 제외 하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67937-158">Immersive apps can choose to have their visual content excluded from mixed reality capture by:</span></span>
* <span data-ttu-id="67937-159">HolographicCameraRenderingParameter의 [IsContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled) 을 설정 하 여 연결 된 프레임에 대 한 혼합 현실 캡처 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="67937-159">Setting HolographicCameraRenderingParameter's [IsContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled) to disable mixed reality capture for its associated frame</span></span>
* <span data-ttu-id="67937-160">연결 된 holographic 카메라에 대해 혼합 현실 캡처를 사용 하지 않도록 HolographicCamera의 [IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled) 설정</span><span class="sxs-lookup"><span data-stu-id="67937-160">Setting HolographicCamera's [IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled) to disable mixed reality capture for its associated holographic camera</span></span>

#### <a name="password-keyboard"></a><span data-ttu-id="67937-161">암호 키보드</span><span class="sxs-lookup"><span data-stu-id="67937-161">Password Keyboard</span></span>

<span data-ttu-id="67937-162">Windows 10 5 월 2019 업데이트를 사용 하면 암호나 pin 키보드를 볼 때 시각적 콘텐츠가 혼합 현실 캡처에서 자동으로 제외 됩니다.</span><span class="sxs-lookup"><span data-stu-id="67937-162">With the Windows 10 May 2019 Update, visual content is automatically excluded from mixed reality capture when a password or pin keyboard is visible.</span></span>

### <a name="knowing-when-mrc-is-active"></a><span data-ttu-id="67937-163">MRC가 활성 상태인 경우 파악</span><span class="sxs-lookup"><span data-stu-id="67937-163">Knowing when MRC is active</span></span>

<span data-ttu-id="67937-164">앱에서 [appcapture](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.AppCapture) 클래스를 사용 하 여 시스템 혼합 현실 캡처가 실행 되는 시기 (오디오 또는 비디오)를 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67937-164">The [AppCapture](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.AppCapture) class can be used by an app to know when system mixed reality capture is running (for either audio or video).</span></span>

>[!NOTE]
><span data-ttu-id="67937-165">AppCapture의 [GetForCurrentView](https://docs.microsoft.com/uwp/api/windows.media.capture.appcapture.getforcurrentview) API는 장치에서 혼합 현실 캡처를 사용할 수 없는 경우 null을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67937-165">AppCapture's [GetForCurrentView](https://docs.microsoft.com/uwp/api/windows.media.capture.appcapture.getforcurrentview) API can return null if mixed reality capture isn't available on the device.</span></span> <span data-ttu-id="67937-166">앱이 일시 중단 될 때 CapturingChanged 이벤트의 등록을 취소 하는 것도 중요 합니다. 그렇지 않으면 MRC가 차단 된 상태가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67937-166">It's also important to de-register the CapturingChanged event when your app is suspended, otherwise MRC can get into a blocked state.</span></span>

### <a name="best-practices-hololens-specific"></a><span data-ttu-id="67937-167">모범 사례 (HoloLens 관련)</span><span class="sxs-lookup"><span data-stu-id="67937-167">Best practices (HoloLens-specific)</span></span>

<span data-ttu-id="67937-168">MRC는 개발자의 추가 작업 없이도 작동 하지만 앱의 최상의 혼합 현실 캡처 환경을 제공 하기 위해 알아두어야 할 몇 가지 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67937-168">MRC is expected to work without additional work from developers, but there are a few things to be aware of to provide the best mixed reality capture experience of your app.</span></span>

<span data-ttu-id="67937-169">**MRC는 홀로그램의 알파 채널을 사용 하 여 [카메라](locatable-camera.md) 이미지와 혼합 합니다.**</span><span class="sxs-lookup"><span data-stu-id="67937-169">**MRC uses the hologram’s alpha channel to blend with the [camera](locatable-camera.md) imagery**</span></span>

<span data-ttu-id="67937-170">가장 중요 한 단계는 불투명 검정을 지우지 않고 앱이 투명 검정을 선택 취소 하 고 있는지 확인 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="67937-170">The most important step is to make sure your app is clearing to transparent black instead of clearing to opaque black.</span></span> <span data-ttu-id="67937-171">Unity에서는 기본적으로 MixedRealityToolkit를 사용 하 여이 작업을 수행 하지만 비 Unity에서 개발 하는 경우 한 줄로 변경 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67937-171">In Unity, this is done by default with the MixedRealityToolkit but if you are developing in non-Unity, you may need to make a one line change.</span></span>

<span data-ttu-id="67937-172">앱이 투명 검정을 지우지 않는 경우 MRC에 표시 될 수 있는 아티팩트는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="67937-172">Here are some of the artifacts you might see in MRC if your app is not clearing to transparent black:</span></span>

<span data-ttu-id="67937-173">**예제 실패**: 콘텐츠 주위의 검은색 가장자리 (투명 검정으로 지우지 못함)</span><span class="sxs-lookup"><span data-stu-id="67937-173">**Example Failures**: Black edges around the content (failing to clear to transparent black)</span></span>

<table>
<tr>
<td>
<img src="images/chessboardblackedges-300px.jpg" alt="Failing to clear to transparent black: black edge artifacts around holograms"/>
</td>
<td>
<img src="images/fieldblackedges-300px.jpg" alt="Failing to clear to transparent black: black edge artifacts around holograms"/>
</td>
</tr>
</table>

<span data-ttu-id="67937-174">**예제 실패**: 홀로그램의 전체 배경 장면이 검은색으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="67937-174">**Example Failures**: The entire background scene of the hologram appears black.</span></span> <span data-ttu-id="67937-175">배경 알파 값을 1로 설정 하면 검은색 배경이 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="67937-175">Setting a background alpha value of 1 results in a black background</span></span>

![배경 알파 값을 1로 설정 하면 검은색 배경이 발생 합니다.](images/clearopaqueblack-300px.png)

<span data-ttu-id="67937-177">**예상 결과**: Holograms는 실제와 제대로 혼합 되어 표시 됩니다 (투명 검정으로 지우는 경우 예상 결과).</span><span class="sxs-lookup"><span data-stu-id="67937-177">**Expected Result**: Holograms appear properly blended with the real-world (expected result if clearing to transparent black)</span></span>

![투명 검정으로 지우는 경우 예상 결과](images/cleartransparentblack-300px.png)

<span data-ttu-id="67937-179">**해결 방법**:</span><span class="sxs-lookup"><span data-stu-id="67937-179">**Solution**:</span></span>
* <span data-ttu-id="67937-180">알파 값이 0 인 불투명 검정으로 표시 되는 모든 콘텐츠를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="67937-180">Change any content that is showing up as opaque black to have an alpha value of 0.</span></span>
* <span data-ttu-id="67937-181">앱이 투명 검정으로 선택 취소 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="67937-181">Ensure that the app is clearing to transparent black.</span></span>
* <span data-ttu-id="67937-182">Unity는 기본적으로 MixedRealityToolkit를 사용 하 여 자동으로 지우도록 선택을 취소 하지만 Unity가 아닌 앱 인 경우에는 ID3D11DeiceContext:: ClearRenderTargetView ()와 함께 사용 되는 색을 수정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67937-182">Unity defaults to clear to clear automatically with the MixedRealityToolkit, but if it’s a non-Unity app you should modify the color used with ID3D11DeiceContext::ClearRenderTargetView().</span></span> <span data-ttu-id="67937-183">불투명 검정 (0, 0, 0, 1)이 아닌 투명 한 검정 (0, 0, 0, 0)을 지울 수 있도록 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="67937-183">You want to ensure you clear to transparent black (0,0,0,0) instead of opaque black (0,0,0,1).</span></span>

<span data-ttu-id="67937-184">원하는 경우 이제 자산의 알파 값을 조정할 수 있지만 일반적으로 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="67937-184">You can now tune the alpha values of your assets if you’d like, but typically don’t need to.</span></span> <span data-ttu-id="67937-185">대부분의 경우에는 MRCs가 적절 하 게 보입니다.</span><span class="sxs-lookup"><span data-stu-id="67937-185">Most of the time, MRCs will look good out of the box.</span></span> <span data-ttu-id="67937-186">MRC는 미리 곱한 알파를 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="67937-186">MRC assumes pre-multiplied alpha.</span></span> <span data-ttu-id="67937-187">알파 값은 MRC 캡처에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="67937-187">The alpha values will only affect the MRC capture.</span></span>

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a><span data-ttu-id="67937-188">HoloLens에서 MRC를 사용 하도록 설정할 때 발생할 수 있는 사항</span><span class="sxs-lookup"><span data-stu-id="67937-188">What to expect when MRC is enabled on HoloLens</span></span>

<span data-ttu-id="67937-189">다음은 다른 설명이 없는 한 HoloLens (첫 번째 생성) 및 HoloLens 2에 모두 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="67937-189">The following apply to both HoloLens (first-generation) and HoloLens 2, unless otherwise noted:</span></span>

* <span data-ttu-id="67937-190">시스템이 30Hz 렌더링으로 응용 프로그램을 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="67937-190">The system will throttle the application to 30Hz rendering.</span></span> <span data-ttu-id="67937-191">그러면 앱이 일정 한 예산 예약을 유지 하지 않아도 되 고 30fps의 MRC 비디오 레코드 프레임 속도와 일치 하는 것을 위해 MRC를 실행 하기 위한 몇 가지 여유가 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="67937-191">This creates some headroom for MRC to run so the app doesn’t need to keep a constant budget reserve and also matches the MRC video record framerate of 30fps</span></span>
* <span data-ttu-id="67937-192">장치 오른쪽에 있는 홀로그램 콘텐츠가 "반짝"로 표시 될 수 있습니다. MRC를 기록/스트리밍할 때 텍스트를 읽는 데 더 어려울 수 있으며, 홀로그램 가장자리가 더 jaggy 표시 될 수 있습니다 ( **HoloLens 2** 에서 세 번째 카메라 렌더링에 대 한 옵트인에서이 손상을 방지 함).</span><span class="sxs-lookup"><span data-stu-id="67937-192">Hologram content in the right eye of the device may appear to “sparkle” when recording/streaming MRC: text may become more difficult to read and hologram edges may appear more jaggy (opting-in to 3rd camera render on **HoloLens 2** avoids this compromise)</span></span>
* <span data-ttu-id="67937-193">MRC 사진과 비디오는 응용 프로그램에서 응용 프로그램을 사용 하도록 설정 하는 경우 응용 프로그램의 [포커스 지점을](focus-point-in-unity.md) 고려 하며,이는 holograms 정확 하 게 배치 되도록 도와줍니다.</span><span class="sxs-lookup"><span data-stu-id="67937-193">MRC photos and videos will respect the application’s [focus point](focus-point-in-unity.md) if the application has enabled it, which will help ensure holograms are accurately positioned.</span></span> <span data-ttu-id="67937-194">비디오의 경우 포커스 지점 깊이가 현저 하 게 변경 되는 경우 holograms는 곡선으로 약간 부드럽게 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67937-194">For videos, the Focus Point is smoothed so holograms may appear to slowly drift into place if the Focus Point depth changes significantly.</span></span> <span data-ttu-id="67937-195">포커스 지점과 다른 깊이에 있는 Holograms는 실제 세계에서 오프셋 된 것 처럼 보일 수 있습니다 (포커스 점이 2 미터로 설정 되었지만 홀로그램은 1 미터에 위치 하는 경우 아래 예제 참조).</span><span class="sxs-lookup"><span data-stu-id="67937-195">Holograms that are at different depths from the focus point may appear offset from the real world (see example below where Focus Point is set at 2 meters but hologram is positioned at 1 meter).</span></span>

![2 미터의 Holograms은 전 세계에 완벽 하 게 등록 된 것으로 보입니다.](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a><span data-ttu-id="67937-198">앱 내에서 MRC 기능 통합</span><span class="sxs-lookup"><span data-stu-id="67937-198">Integrating MRC functionality from within your app</span></span>

<span data-ttu-id="67937-199">혼합 현실 앱은 앱 내에서 MRC 사진 또는 비디오 캡처를 시작할 수 있으며, 캡처된 콘텐츠는 장치의 "카메라 롤"에 저장 하지 않고도 앱에서 사용할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="67937-199">Your mixed reality app can initiate MRC photo or video capture from within the app, and the content captured is made available to your app without being stored to the device's "Camera roll."</span></span> <span data-ttu-id="67937-200">사용자 지정 MRC 레코더를 만들거나 기본 제공 카메라 캡처 UI를 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67937-200">You can create a custom MRC recorder or take advantage of built-in camera capture UI.</span></span> 

### <a name="mrc-with-built-in-camera-ui"></a><span data-ttu-id="67937-201">기본 제공 카메라 UI를 사용 하는 MRC</span><span class="sxs-lookup"><span data-stu-id="67937-201">MRC with built-in camera UI</span></span>

<span data-ttu-id="67937-202">개발자는 *[카메라 캡처 UI API](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* 를 사용 하 여 몇 줄의 코드만으로 사용자가 캡처한 혼합 현실 사진 또는 비디오를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67937-202">Developers can use the *[Camera Capture UI API](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* to get a user-captured mixed reality photo or video with just a few lines of code.</span></span>

<span data-ttu-id="67937-203">이 API는 기본 제공 MRC 카메라 UI를 시작 하 여 사용자가 사진 또는 비디오를 촬영 하 고 결과 캡처를 앱에 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="67937-203">This API launches the built-in MRC camera UI, from which the user can take a photo or video, and returns the resulting capture to your app.</span></span>  <span data-ttu-id="67937-204">카메라 UI를 직접 만들거나 캡처 스트림에 대 한 하위 수준 액세스를 필요로 하는 경우 사용자 지정 혼합 현실 캡처 레코더를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67937-204">If you want to create your own camera UI, or need lower-level access to the capture stream, you can create a custom Mixed Reality Capture recorder.</span></span>

### <a name="creating-a-custom-mrc-recorder"></a><span data-ttu-id="67937-205">사용자 지정 MRC 레코더 만들기</span><span class="sxs-lookup"><span data-stu-id="67937-205">Creating a custom MRC recorder</span></span>

<span data-ttu-id="67937-206">사용자는 항상 시스템 MRC 캡처 서비스를 사용 하 여 사진이 나 비디오를 트리거할 수 있지만 응용 프로그램은 사용자 지정 카메라 앱을 빌드할 수 있지만 MRC와 마찬가지로 카메라 스트림에 holograms를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="67937-206">While the user can always trigger a photo or video using the system MRC capture service, an application may want to build a custom camera app but include holograms in the camera stream just like MRC.</span></span> <span data-ttu-id="67937-207">이를 통해 응용 프로그램은 사용자를 대신 하 여 캡처를 시작 하거나 사용자 지정 기록 UI를 빌드하거나 MRC 설정을 사용자 지정 하 여 몇 가지 예의 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67937-207">This allows the application to kick off captures on behalf of the user, build custom recording UI, or customize MRC settings to name a few examples.</span></span>

<span data-ttu-id="67937-208">**HoloStudio는 MRC 효과를 사용 하 여 사용자 지정 MRC 카메라를 추가 합니다.**</span><span class="sxs-lookup"><span data-stu-id="67937-208">**HoloStudio adds a custom MRC camera using MRC effects**</span></span>

![HoloStudio는 MRC 효과를 사용 하 여 사용자 지정 MRC 카메라를 추가 합니다.](images/cameraiconholostudio-300px.jpg)

<span data-ttu-id="67937-210">Unity 응용 프로그램은 holograms를 사용 하도록 설정 하는 속성에 대 한 [Locatable_camera_in_Unity](locatable-camera-in-unity.md) 를 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67937-210">Unity Applications should see [Locatable_camera_in_Unity](locatable-camera-in-unity.md) for the property to enable holograms.</span></span>

<span data-ttu-id="67937-211">다른 응용 프로그램은 [Windows 미디어 캡처 api](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaCapture) 를 사용 하 여 카메라를 제어 하 고, 스틸 및 비디오에 가상 holograms 및 응용 프로그램 오디오를 포함 하는 Mrc 비디오 및 오디오 효과를 추가 하 여이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67937-211">Other applications can do this by using the [Windows Media Capture APIs](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaCapture) to control the Camera and add an MRC Video and Audio effect to include virtual holograms and application audio in stills and videos.</span></span>

<span data-ttu-id="67937-212">응용 프로그램에는 효과를 추가 하는 두 가지 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67937-212">Applications have two options to add the effect:</span></span>
* <span data-ttu-id="67937-213">이전 API: [MediaCapture. AddEffectAsync ()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addeffectasync)</span><span class="sxs-lookup"><span data-stu-id="67937-213">The older API: [Windows.Media.Capture.MediaCapture.AddEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addeffectasync)</span></span>
* <span data-ttu-id="67937-214">새 Microsoft 권장 API (개체를 반환 하 여 동적 속성을 조작할 수 있음): [MediaCapture () / AddVideoEffectAsync (](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync) ): [MediaCapture ()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) : 응용 프로그램이 [IVideoEffectDefinition](https://docs.microsoft.com/uwp/api/Windows.Media.Effects.IVideoEffectDefinition) 및 [IAudioEffectDefinition](https://docs.microsoft.com/uwp/api/windows.media.effects.iaudioeffectdefinition)의 고유한 구현을 만들도록 요구 합니다.</span><span class="sxs-lookup"><span data-stu-id="67937-214">The new Microsoft recommended API (returns an object, making it possible to manipulate dynamic properties): [Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) which require the app create its own implementation of [IVideoEffectDefinition](https://docs.microsoft.com/uwp/api/Windows.Media.Effects.IVideoEffectDefinition) and [IAudioEffectDefinition](https://docs.microsoft.com/uwp/api/windows.media.effects.iaudioeffectdefinition).</span></span> <span data-ttu-id="67937-215">샘플 사용에 대해서는 MRC 효과 샘플을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="67937-215">Please see the MRC effect sample for sample usage.</span></span>

>[!NOTE]
> <span data-ttu-id="67937-216">MixedRealityCapture 네임 스페이스는 Visual Studio에서 인식 되지 않지만 문자열은 여전히 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="67937-216">The Windows.Media.MixedRealityCapture namespace will not be recognized by Visual Studio, but the strings are still valid.</span></span>

<span data-ttu-id="67937-217">MRC 비디오 효과 (**MixedRealityCapture. MixedRealityCaptureVideoEffect**)</span><span class="sxs-lookup"><span data-stu-id="67937-217">MRC Video Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)</span></span>

|  <span data-ttu-id="67937-218">속성 이름</span><span class="sxs-lookup"><span data-stu-id="67937-218">Property Name</span></span>  |  <span data-ttu-id="67937-219">형식</span><span class="sxs-lookup"><span data-stu-id="67937-219">Type</span></span>  |  <span data-ttu-id="67937-220">기본값</span><span class="sxs-lookup"><span data-stu-id="67937-220">Default Value</span></span>  |  <span data-ttu-id="67937-221">설명</span><span class="sxs-lookup"><span data-stu-id="67937-221">Description</span></span> | 
|----------|----------|----------|----------|
|  <span data-ttu-id="67937-222">StreamType</span><span class="sxs-lookup"><span data-stu-id="67937-222">StreamType</span></span>  |  <span data-ttu-id="67937-223">UINT32 ([Mediastreamtype](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaStreamType))</span><span class="sxs-lookup"><span data-stu-id="67937-223">UINT32 ([MediaStreamType](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaStreamType))</span></span>  |  <span data-ttu-id="67937-224">1 (VideoRecord)</span><span class="sxs-lookup"><span data-stu-id="67937-224">1 (VideoRecord)</span></span>  |  <span data-ttu-id="67937-225">이 효과가 사용 되는 캡처 스트림을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="67937-225">Describe which capture stream this effect is used for.</span></span> <span data-ttu-id="67937-226">오디오를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="67937-226">Audio is not available.</span></span> | 
|  <span data-ttu-id="67937-227">HologramCompositionEnabled</span><span class="sxs-lookup"><span data-stu-id="67937-227">HologramCompositionEnabled</span></span>  |  <span data-ttu-id="67937-228">boolean</span><span class="sxs-lookup"><span data-stu-id="67937-228">boolean</span></span>  |  <span data-ttu-id="67937-229">TRUE</span><span class="sxs-lookup"><span data-stu-id="67937-229">TRUE</span></span>  |  <span data-ttu-id="67937-230">비디오 캡처에서 holograms을 사용 하거나 사용 하지 않도록 설정 하는 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="67937-230">Flag to enable or disable holograms in video capture.</span></span> | 
|  <span data-ttu-id="67937-231">RecordingIndicatorEnabled</span><span class="sxs-lookup"><span data-stu-id="67937-231">RecordingIndicatorEnabled</span></span>  |  <span data-ttu-id="67937-232">boolean</span><span class="sxs-lookup"><span data-stu-id="67937-232">boolean</span></span>  |  <span data-ttu-id="67937-233">TRUE</span><span class="sxs-lookup"><span data-stu-id="67937-233">TRUE</span></span>  |  <span data-ttu-id="67937-234">홀로그램 캡처 중에 화면에서 기록 표시기를 사용 하거나 사용 하지 않도록 설정 하는 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="67937-234">Flag to enable or disable recording indicator on screen during hologram capturing.</span></span> | 
|  <span data-ttu-id="67937-235">VideoStabilizationEnabled</span><span class="sxs-lookup"><span data-stu-id="67937-235">VideoStabilizationEnabled</span></span>  |  <span data-ttu-id="67937-236">boolean</span><span class="sxs-lookup"><span data-stu-id="67937-236">boolean</span></span>  |  <span data-ttu-id="67937-237">FALSE</span><span class="sxs-lookup"><span data-stu-id="67937-237">FALSE</span></span>  |  <span data-ttu-id="67937-238">HoloLens 트래커에서 구동 하는 비디오 안정화를 사용 하거나 사용 하지 않도록 설정 하는 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="67937-238">Flag to enable or disable video stabilization powered by the HoloLens tracker.</span></span> | 
|  <span data-ttu-id="67937-239">VideoStabilizationBufferLength</span><span class="sxs-lookup"><span data-stu-id="67937-239">VideoStabilizationBufferLength</span></span>  |  <span data-ttu-id="67937-240">UINT32</span><span class="sxs-lookup"><span data-stu-id="67937-240">UINT32</span></span>  |  <span data-ttu-id="67937-241">0</span><span class="sxs-lookup"><span data-stu-id="67937-241">0</span></span>  |  <span data-ttu-id="67937-242">비디오 안정화에 사용 되는 기록 프레임의 수를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="67937-242">Set how many historical frames are used for video stabilization.</span></span> <span data-ttu-id="67937-243">0은 전력 및 성능 측면에서 0-대기 시간 및 거의 "무료"입니다.</span><span class="sxs-lookup"><span data-stu-id="67937-243">0 is 0-latency and nearly "free" from a power and performance perspective.</span></span> <span data-ttu-id="67937-244">15는 대기 시간 및 메모리의 15 프레임에 대 한 비용으로 최고 품질을 위해 권장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="67937-244">15 is recommended for highest quality (at the cost of 15 frames of latency and memory).</span></span> | 
|  <span data-ttu-id="67937-245">GlobalOpacityCoefficient</span><span class="sxs-lookup"><span data-stu-id="67937-245">GlobalOpacityCoefficient</span></span>  |  <span data-ttu-id="67937-246">float</span><span class="sxs-lookup"><span data-stu-id="67937-246">float</span></span>  |  <span data-ttu-id="67937-247">0.9 (HoloLens) 1.0 (모던 헤드셋)</span><span class="sxs-lookup"><span data-stu-id="67937-247">0.9 (HoloLens) 1.0 (Immersive headset)</span></span>  |  <span data-ttu-id="67937-248">홀로그램의 전역 불투명도 계수를 0.0 (완전히 투명)에서 1.0 (완전히 불투명)로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="67937-248">Set global opacity coefficient of hologram in range from 0.0 (fully transparent) to 1.0 (fully opaque).</span></span> | 
|  <span data-ttu-id="67937-249">BlankOnProtectedContent</span><span class="sxs-lookup"><span data-stu-id="67937-249">BlankOnProtectedContent</span></span>  |  <span data-ttu-id="67937-250">boolean</span><span class="sxs-lookup"><span data-stu-id="67937-250">boolean</span></span>  |  <span data-ttu-id="67937-251">FALSE</span><span class="sxs-lookup"><span data-stu-id="67937-251">FALSE</span></span>  |  <span data-ttu-id="67937-252">보호 된 콘텐츠를 표시 하는 2d UWP 앱이 있는 경우 빈 프레임을 반환 하거나 사용 하지 않도록 설정 하는 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="67937-252">Flag to enable or disable returning an empty frame if there is a 2d UWP app showing protected content.</span></span> <span data-ttu-id="67937-253">이 플래그가 false이 고 2d UWP 앱이 보호 된 콘텐츠를 표시 하는 경우 2d UWP 앱은 헤드셋과 혼합 현실 캡처 모두에서 보호 된 콘텐츠 질감으로 교체 됩니다.</span><span class="sxs-lookup"><span data-stu-id="67937-253">If this flag is false and a 2d UWP app is showing protected content, the 2d UWP app will be replaced by a protected content texture in both the headset and in the mixed reality capture.</span></span> |
|  <span data-ttu-id="67937-254">ShowHiddenMesh</span><span class="sxs-lookup"><span data-stu-id="67937-254">ShowHiddenMesh</span></span>  |  <span data-ttu-id="67937-255">boolean</span><span class="sxs-lookup"><span data-stu-id="67937-255">boolean</span></span>  |  <span data-ttu-id="67937-256">FALSE</span><span class="sxs-lookup"><span data-stu-id="67937-256">FALSE</span></span>  |  <span data-ttu-id="67937-257">Holographic 카메라의 숨겨진 영역 메시 및 인접 콘텐츠를 표시 하거나 사용 하지 않도록 설정 하는 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="67937-257">Flag to enable or disable showing the holographic camera's hidden area mesh and neighboring content.</span></span> |
| <span data-ttu-id="67937-258">OutputSize</span><span class="sxs-lookup"><span data-stu-id="67937-258">OutputSize</span></span> | <span data-ttu-id="67937-259">크기</span><span class="sxs-lookup"><span data-stu-id="67937-259">Size</span></span> | <span data-ttu-id="67937-260">0, 0</span><span class="sxs-lookup"><span data-stu-id="67937-260">0, 0</span></span> | <span data-ttu-id="67937-261">비디오 안정화를 위해 자른 후 원하는 출력 크기를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="67937-261">Set the desired output size after cropping for video stabilization.</span></span> <span data-ttu-id="67937-262">0 또는 잘못 된 출력 크기가 지정 된 경우 기본 자르기 크기가 선택 됩니다.</span><span class="sxs-lookup"><span data-stu-id="67937-262">A default crop size is chosen if 0 or an invalid output size is specified.</span></span> |
| <span data-ttu-id="67937-263">PreferredHologramPerspective</span><span class="sxs-lookup"><span data-stu-id="67937-263">PreferredHologramPerspective</span></span> | <span data-ttu-id="67937-264">UINT32</span><span class="sxs-lookup"><span data-stu-id="67937-264">UINT32</span></span> | <span data-ttu-id="67937-265">1 (PhotoVideoCamera)</span><span class="sxs-lookup"><span data-stu-id="67937-265">1 (PhotoVideoCamera)</span></span> | <span data-ttu-id="67937-266">캡처할 holographic 카메라 보기 구성을 나타내는 데 사용 되는 열거형입니다.</span><span class="sxs-lookup"><span data-stu-id="67937-266">Enum used to indicate which holographic camera view configuration should be captured.</span></span> <span data-ttu-id="67937-267">0 (표시)을 설정 하면 앱에 사진/비디오 카메라에서 렌더링 하 라는 메시지가 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="67937-267">Setting 0 (Display) means that the app won't be asked to render from the photo/video camera</span></span> |

<span data-ttu-id="67937-268">MRC 오디오 효과 (**MixedRealityCapture. MixedRealityCaptureAudioEffect**)</span><span class="sxs-lookup"><span data-stu-id="67937-268">MRC Audio Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)</span></span>

<table>
<tr>
<th><span data-ttu-id="67937-269">속성 이름</span><span class="sxs-lookup"><span data-stu-id="67937-269">Property Name</span></span></th>
<th><span data-ttu-id="67937-270">형식</span><span class="sxs-lookup"><span data-stu-id="67937-270">Type</span></span></th>
<th><span data-ttu-id="67937-271">기본값</span><span class="sxs-lookup"><span data-stu-id="67937-271">Default Value</span></span></th>
<th><span data-ttu-id="67937-272">설명</span><span class="sxs-lookup"><span data-stu-id="67937-272">Description</span></span></th>
</tr>
<tr>
<td><span data-ttu-id="67937-273">MixerMode</span><span class="sxs-lookup"><span data-stu-id="67937-273">MixerMode</span></span></td>
<td><span data-ttu-id="67937-274">UINT32</span><span class="sxs-lookup"><span data-stu-id="67937-274">UINT32</span></span></td>
<td><span data-ttu-id="67937-275">2</span><span class="sxs-lookup"><span data-stu-id="67937-275">2</span></span></td>
<td>
<ul>
<li><span data-ttu-id="67937-276">0: Mic 오디오만</span><span class="sxs-lookup"><span data-stu-id="67937-276">0 : Mic audio only</span></span></li>
<li><span data-ttu-id="67937-277">1: 시스템 오디오만</span><span class="sxs-lookup"><span data-stu-id="67937-277">1 : System audio only</span></span></li>
<li><span data-ttu-id="67937-278">2: Mic 및 시스템 오디오</span><span class="sxs-lookup"><span data-stu-id="67937-278">2 : Mic and System audio</span></span></li>
</ul>
</td>
</tr>
</table>

### <a name="simultaneous-mrc-limitations"></a><span data-ttu-id="67937-279">동시 MRC 제한 사항</span><span class="sxs-lookup"><span data-stu-id="67937-279">Simultaneous MRC limitations</span></span>

<span data-ttu-id="67937-280">MRC에 동시에 액세스 하는 여러 앱에 대 한 특정 제한 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67937-280">There are certain limitations around multiple apps accessing MRC at the same time.</span></span>

#### <a name="photovideo-camera-access"></a><span data-ttu-id="67937-281">사진/비디오 카메라 액세스</span><span class="sxs-lookup"><span data-stu-id="67937-281">Photo/video camera access</span></span>

<span data-ttu-id="67937-282">Photo/video 카메라는 동시에 액세스할 수 있는 프로세스의 수로 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="67937-282">The photo/video camera is limited to the number of processes that can access it at the same time.</span></span> <span data-ttu-id="67937-283">프로세스가 비디오를 기록 하거나 사진을 촬영 하는 동안 다른 프로세스에서 사진/비디오 카메라를 획득 하는 데 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="67937-283">While a process is recording video or taking a photo any other process will fail to acquire the photo/video camera.</span></span> <span data-ttu-id="67937-284">(혼합 현실 캡처와 표준 사진/비디오 캡처 모두에 적용 됨)</span><span class="sxs-lookup"><span data-stu-id="67937-284">(this applies to both Mixed Reality Capture and standard photo/video capture)</span></span>

<span data-ttu-id="67937-285">HoloLens 2를 사용 하는 경우 앱은 MediaCaptureInitializationSettings ' [SharingMode](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode) 속성을 사용 하 여 photo/video 카메라를 독점적으로 제어할 필요가 없는 경우 sharedreadonly를 실행 하도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67937-285">With HoloLens 2, an app can use MediaCaptureInitializationSettings' [SharingMode](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode) property to indicate that they want to run SharedReadOnly if they don't need exclusive control over the photo/video camera.</span></span> <span data-ttu-id="67937-286">이렇게 하면 캡처의 해상도와 프레임 속도가 카메라에서 제공 하도록 구성 된 다른 앱으로 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="67937-286">Doing so means the resolution and framerate of the capture will be limited to what other apps have configured the camera to provide.</span></span>

##### <a name="built-in-mrc-photovideo-camera-access"></a><span data-ttu-id="67937-287">기본 제공 MRC 사진/비디오 카메라 액세스</span><span class="sxs-lookup"><span data-stu-id="67937-287">Built-in MRC photo/video camera access</span></span>

<span data-ttu-id="67937-288">Windows 10에 기본 제공 되는 MRC 기능 (Cortana, 시작 메뉴, 하드웨어 바로 가기, Miracast, Windows 장치 포털을 통해):</span><span class="sxs-lookup"><span data-stu-id="67937-288">MRC functionality built into Windows 10 (via Cortana, Start Menu, hardware shortcuts, Miracast, Windows Device Portal):</span></span>
* <span data-ttu-id="67937-289">기본적으로 ExclusiveControl를 사용 하 여 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="67937-289">Will run with ExclusiveControl by default</span></span>

<span data-ttu-id="67937-290">그러나 공유 모드에서 작동 하도록 각 하위 시스템에 대 한 지원이 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="67937-290">However, support has been added to each subsystem to operate in a shared mode:</span></span>
* <span data-ttu-id="67937-291">앱이 photo/video 카메라에 대 한 ExclusiveControl 액세스를 요청 하는 경우 기본 제공 MRC는 앱의 요청이 성공 하도록 photo/video 카메라를 사용 하 여 자동으로 중지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="67937-291">If an app requests ExclusiveControl access to the photo/video camera, built-in MRC will automatically stop using the photo/video camera so the app's request will succeed</span></span>
* <span data-ttu-id="67937-292">앱이 ExclusiveControl 때 기본 제공 MRC가 시작 되 면 기본 제공 MRC가 SharedReadOnly 모드에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="67937-292">If built-in MRC is started while an app has ExclusiveControl, built-in MRC will run in SharedReadOnly mode</span></span>

<span data-ttu-id="67937-293">이 공유 모드 기능에는 다음과 같은 제한 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67937-293">This shared mode functionality has certain restrictions:</span></span>
* <span data-ttu-id="67937-294">Cortana, 하드웨어 바로 가기 또는 시작 메뉴를 통한 사진: Windows 10 4 월 2018 업데이트 (이상)가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="67937-294">Photo via Cortana, hardware shortcuts, or Start Menu: Requires the Windows 10 April 2018 Update (or later)</span></span>
* <span data-ttu-id="67937-295">Cortana, 하드웨어 바로 가기 또는 시작 메뉴를 통한 비디오: Windows 10 4 월 2018 업데이트 (이상) 필요</span><span class="sxs-lookup"><span data-stu-id="67937-295">Video via Cortana, hardware shortcuts, or Start Menu: Requires the Windows 10 April 2018 Update (or later)</span></span>
* <span data-ttu-id="67937-296">Miracast를 통한 MRC 스트리밍: Windows 10 10 월 2018 업데이트 (이상)가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="67937-296">Streaming MRC over Miracast: Requires the Windows 10 October 2018 Update (or later)</span></span>
* <span data-ttu-id="67937-297">Windows 장치 포털을 통해 또는 HoloLens 도우미 앱을 통해 MRC 스트리밍: HoloLens 2 필요</span><span class="sxs-lookup"><span data-stu-id="67937-297">Streaming MRC over Windows Device Portal or via the HoloLens companion app: Requires HoloLens 2</span></span>

>[!NOTE]
> <span data-ttu-id="67937-298">다른 앱에서 photo/video 카메라를 사용 하는 경우 기본 제공 MRC 카메라 UI의 해상도와 프레임 속도가 일반 값에서 감소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67937-298">The resolution and framerate of the built-in MRC camera UI might be reduced from its normal values when another app is using the photo/video camera.</span></span>

#### <a name="mrc-access"></a><span data-ttu-id="67937-299">MRC 액세스</span><span class="sxs-lookup"><span data-stu-id="67937-299">MRC access</span></span>

<span data-ttu-id="67937-300">Windows 10 4 월 2018 업데이트를 사용 하면 MRC 스트림에 액세스 하는 여러 앱에 대해 더 이상 제한이 없습니다 (그러나 사진/비디오 카메라에 대 한 액세스에는 여전히 제한이 있음).</span><span class="sxs-lookup"><span data-stu-id="67937-300">With the Windows 10 April 2018 Update, there is no longer a limitation around multiple apps accessing the MRC stream (however, the access to the photo/video camera still has limitations).</span></span>

<span data-ttu-id="67937-301">Windows 10 4 월 2018 업데이트 이전에는 앱의 사용자 지정 MRC 레코더를 시스템 MRC와 함께 사용할 수 없습니다 (사진 캡처, 비디오 캡처 또는 Windows 장치 포털에서 스트리밍).</span><span class="sxs-lookup"><span data-stu-id="67937-301">Previous to the Windows 10 April 2018 Update, an app's custom MRC recorder was mutually exclusive with system MRC (capturing photos, capturing videos, or streaming from the Windows Device Portal).</span></span>

## <a name="see-also"></a><span data-ttu-id="67937-302">참고 항목</span><span class="sxs-lookup"><span data-stu-id="67937-302">See also</span></span>
* [<span data-ttu-id="67937-303">혼합 현실 캡처</span><span class="sxs-lookup"><span data-stu-id="67937-303">Mixed reality capture</span></span>](mixed-reality-capture.md)
* [<span data-ttu-id="67937-304">Spectator View</span><span class="sxs-lookup"><span data-stu-id="67937-304">Spectator view</span></span>](spectator-view.md)
