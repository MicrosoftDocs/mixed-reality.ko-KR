---
title: 개발자를 위한 실제로 캡처 혼합
description: 개발자를 위한 혼합된 현실에 대 한 모범 사례를 캡처합니다.
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: mrc, 사진, 비디오, 캡처, 카메라
ms.openlocfilehash: d1675d2d6c74c6d15ca245a66719e00f2a7c2111
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694369"
---
# <a name="mixed-reality-capture-for-developers"></a><span data-ttu-id="ab3e1-104">개발자를 위한 실제로 캡처 혼합</span><span class="sxs-lookup"><span data-stu-id="ab3e1-104">Mixed reality capture for developers</span></span>

> <span data-ttu-id="ab3e1-105">[참고!] 참조 [PV 카메라에서 렌더링](#render-from-the-pv-camera-opt-in) 아래 HoloLens 2에 대 한 새로운 MRC 기능에 대 한 지침에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-105">[NOTE!] See [Render from the PV camera](#render-from-the-pv-camera-opt-in) below for guidance on a new MRC capability for HoloLens 2.</span></span>

<span data-ttu-id="ab3e1-106">사용자가 수행할 수 있으므로 [혼합 현실 캡처](mixed-reality-capture.md) (MRC) 사진 또는 언제 든 지 비디오를 응용 프로그램을 개발할 때는 염두 해야 할 몇 가지 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-106">Since a user could take a [mixed reality capture](mixed-reality-capture.md) (MRC) photo or video at any time, there are a few things that you should keep in mind when developing your application.</span></span> <span data-ttu-id="ab3e1-107">여기에 MRC 시각적 품질 및 MRCs 캡처되는 동안 시스템 변경 내용에 응답 속도 대 한 모범 사례입니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-107">This includes best practices for MRC visual quality and being responsive to system changes while MRCs are being captured.</span></span>

<span data-ttu-id="ab3e1-108">개발자 혼합된 현실 캡처 및 삽입 하 여 앱에도 원활 하 게 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-108">Developers can also seamlessly integrate mixed reality capture and insertion into their apps.</span></span>

<span data-ttu-id="ab3e1-109">HoloLens (항목인 1 세대)에 MRC에는 HoloLens 2는 MRC 4k 해상도로 등록 최대 1080p 및 사진과 비디오를 지원 하지만 최대 720p, 사진 및 비디오를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-109">MRC on HoloLens (first-generation) supports videos and photos up to 720p, while MRC on HoloLens 2 supports videos up to 1080p and photos up to 4K resolution.</span></span>

## <a name="the-importance-of-quality-mrc"></a><span data-ttu-id="ab3e1-110">MRC 품질의 중요성</span><span class="sxs-lookup"><span data-stu-id="ab3e1-110">The importance of quality MRC</span></span>

<span data-ttu-id="ab3e1-111">혼합된 현실 사진 캡처되고 비디오는 앱의 사용자에 게는 처음 접하는 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-111">Mixed reality captured photos and videos are likely the first exposure a user will have of your app.</span></span> <span data-ttu-id="ab3e1-112">혼합된 현실 스크린 샷을 Microsoft Store 페이지 또는 MRCs 소셜 네트워크에서 공유 하는 다른 사용자로 여부입니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-112">Whether as mixed reality screenshots on your Microsoft Store page or from other users sharing MRCs on social networks.</span></span> <span data-ttu-id="ab3e1-113">MRC 데모 앱, 사용자 교육, 사용자가 해당 혼합된 환경 상호 작용을 공유 하도록 권장 하는 데 사용할 수 및 사용자 설문 조사 및 문제 해결에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-113">You can use MRC to demo your app, educate users, encourage users to share their mixed world interactions, and for user research and problem solving.</span></span>

## <a name="how-mrc-impacts-your-app"></a><span data-ttu-id="ab3e1-114">MRC 앱에 미치는 영향을</span><span class="sxs-lookup"><span data-stu-id="ab3e1-114">How MRC impacts your app</span></span>

### <a name="enabling-mrc-in-your-app"></a><span data-ttu-id="ab3e1-115">앱에서 사용 하도록 설정 하면 MRC</span><span class="sxs-lookup"><span data-stu-id="ab3e1-115">Enabling MRC in your app</span></span>

<span data-ttu-id="ab3e1-116">기본적으로 앱 사용자가 혼합된 현실 캡처를 수행할 수 있도록 모든 작업을 수행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-116">By default, an app does not have to do anything to enable users to take mixed reality captures.</span></span>

### <a name="enabling-improved-alignment-for-mrc-in-your-app"></a><span data-ttu-id="ab3e1-117">앱에서 향상 된 MRC 맞춤을 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="ab3e1-117">Enabling improved alignment for MRC in your app</span></span>

<span data-ttu-id="ab3e1-118">기본적으로 혼합된 현실 캡처 (PV) 사진/비디오 카메라를 사용 하 여 오른쪽 눈 holographic 출력을 결합합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-118">By default, mixed reality capture combines the right eye's holographic output with the photo/video (PV) camera.</span></span> <span data-ttu-id="ab3e1-119">이러한 두 개의 소스에서 현재 실행 중인 몰입 형 앱 설정의 포커스 지점을 사용 하 여 결합 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-119">These two sources are combined using the focus point set by the currently running immersive app.</span></span>

<span data-ttu-id="ab3e1-120">이 포커스 문자표 홀로그램 (인해 PV 카메라 및 오른쪽 표시 간의 실제 거리) 어울리지 않습니다는 것을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-120">This means that holograms outside the focus plane won't align as well (due to the physical distance between the PV camera and the right display).</span></span>

#### <a name="set-the-focus-point"></a><span data-ttu-id="ab3e1-121">포커스 지점을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-121">Set the focus point</span></span>

<span data-ttu-id="ab3e1-122">몰입 형 앱 (HoloLens) 설정 해야 합니다 [지점 집중](focus-point-in-unity.md) 되도록 해당 안정화 평면 원할 때마다 원하는 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-122">Immersive apps (on HoloLens) should set the [focus point](focus-point-in-unity.md) of where they want their stabilization plane to be.</span></span> <span data-ttu-id="ab3e1-123">이렇게 하면 캡처 혼합된 현실 헤드셋 모두에 가장 좋은 맞춤 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-123">This ensures the best alignment in both the headset and in mixed reality capture.</span></span>

<span data-ttu-id="ab3e1-124">포커스 지점을 설정 되지 않은 경우 두 가지 단위가 안정화 평면 기본값은입니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-124">If a focus point is not set, the stabilization plane will default to two meters.</span></span>

#### <a name="render-from-the-pv-camera-opt-in"></a><span data-ttu-id="ab3e1-125">옵트인 (opt in) PV 카메라에서 렌더링</span><span class="sxs-lookup"><span data-stu-id="ab3e1-125">Render from the PV camera (opt-in)</span></span>

<span data-ttu-id="ab3e1-126">몰입 형 앱에 대 한 기능을 추가 하는 HoloLens 2 **PV 카메라에서 렌더링** 혼합된 현실 캡처 실행 되는 동안.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-126">HoloLens 2 adds the ability for an immersive app to **render from the PV camera** while mixed reality capture is running.</span></span> <span data-ttu-id="ab3e1-127">앱 추가 렌더링을 올바르게 지원 하도록 앱은이 기능에 옵트인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-127">To ensure the app supports the additional render correctly, the app has to opt-in to this functionality.</span></span>

<span data-ttu-id="ab3e1-128">기본 MRC 환경을 통해 다음과 같은 개선 사항이 PV 카메라 제품에서 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-128">Render from the PV camera offers the following improvements over the default MRC experience:</span></span>
* <span data-ttu-id="ab3e1-129">물리적 환경 및이 손 (거의 상호 작용) 모두에 맞춤 홀로그램 해야 정확 하 게 전혀 거리를 하는 대신 오프셋 거리의 포커스 지점 외에 기본 MRC 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-129">Hologram alignment to both your physical environment and hands (for near interactions) should be accurate at all distances, instead of having an offset at distances other than the focus point as you might see in the default MRC.</span></span>
* <span data-ttu-id="ab3e1-130">헤드셋에서 오른쪽 눈 손상 되지, MRC 출력 홀로그램 렌더링에 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-130">The right eye in the headset won't be compromised, as it won't be used to render the holograms for the MRC output.</span></span>

<span data-ttu-id="ab3e1-131">PV 카메라에서 렌더링을 사용 하도록 설정 하려면 세 가지 단계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-131">There are three steps to enable rendering from the PV camera:</span></span>
1. <span data-ttu-id="ab3e1-132">PhotoVideoCamera HolographicViewConfiguration를 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="ab3e1-132">Enable the PhotoVideoCamera HolographicViewConfiguration</span></span>
2. <span data-ttu-id="ab3e1-133">추가 HolographicCamera 렌더링 처리</span><span class="sxs-lookup"><span data-stu-id="ab3e1-133">Handle the additional HolographicCamera render</span></span>
3. <span data-ttu-id="ab3e1-134">확인할 셰이더와 코드에이 추가 HolographicCamera에서 올바르게 렌더링</span><span class="sxs-lookup"><span data-stu-id="ab3e1-134">Verify your shaders and code render correctly from this additional HolographicCamera</span></span>

##### <a name="enable-the-photovideocamera-holographicviewconfiguration"></a><span data-ttu-id="ab3e1-135">PhotoVideoCamera HolographicViewConfiguration를 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="ab3e1-135">Enable the PhotoVideoCamera HolographicViewConfiguration</span></span>

<span data-ttu-id="ab3e1-136">에 옵트인, 앱에서는 단지는 PhotoVideoCamera [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration):</span><span class="sxs-lookup"><span data-stu-id="ab3e1-136">To opt-in, an app simply enables the PhotoVideoCamera's [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration):</span></span>
```csharp
var display = Windows.Graphics.Holographic.HolographicDisplay.GetDefault();
var view = display.TryGetViewConfiguration(Windows.Graphics.Holographic.HolographicViewConfiguration.PhotoVideoCamera);
if (view != null)
{
   view.IsEnabled = true;
}
```

##### <a name="handle-the-additional-holographiccamera-render-in-directx"></a><span data-ttu-id="ab3e1-137">DirectX의 추가 HolographicCamera 렌더링 처리</span><span class="sxs-lookup"><span data-stu-id="ab3e1-137">Handle the additional HolographicCamera render in DirectX</span></span>

<span data-ttu-id="ab3e1-138">앱이 PV 카메라에서 렌더링을 옵트인 하 고 혼합된 현실 캡처 시작 경우:</span><span class="sxs-lookup"><span data-stu-id="ab3e1-138">When the app has opt-in to render from the PV camera and mixed reality capture starts:</span></span>
1. <span data-ttu-id="ab3e1-139">HolographicSpace의 CameraAdded 이벤트가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-139">HolographicSpace's CameraAdded event will fire.</span></span> <span data-ttu-id="ab3e1-140">앱이이 시간에 카메라를 처리할 수 없는 경우이 이벤트를 지연 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-140">This event can be deferred if the app cannot handle the camera at this time.</span></span>
2. <span data-ttu-id="ab3e1-141">이벤트 완료 (고 면 미해결 지연이 없을)는 HolographicCamera 다음 HolographicFrame의 AddedCameras 목록에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-141">Once the event has completed (and there are no outstanding deferrals) the HolographicCamera will appear in the next HolographicFrame's AddedCameras list.</span></span>

<span data-ttu-id="ab3e1-142">혼합된 현실 캡처가 중지 됩니다 (또는 앱 혼합된 현실 캡처 실행 되는 동안 보기 구성을 사용 하지 않도록 설정 하는 경우): 다음 HolographicFrame의 RemovedCameras 목록에는 HolographicCamera 나타나고 HolographicSpace의 CameraRemoved 이벤트는 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-142">When mixed reality capture stops (or if the app disables the view configuration while mixed reality capture is running): the HolographicCamera will appear in the next HolographicFrame's RemovedCameras list and the HolographicSpace's CameraRemoved event will fire.</span></span>

<span data-ttu-id="ab3e1-143">A [ViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) 카메라 속한 구성을 식별 하는 데 HolographicCamera 속성이 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-143">A [ViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) property has been added to HolographicCamera to help identify the configuration a camera belongs to.</span></span>

##### <a name="handle-the-additional-holographiccamera-render-in-unity"></a><span data-ttu-id="ab3e1-144">Unity에서 추가 HolographicCamera 렌더링 처리</span><span class="sxs-lookup"><span data-stu-id="ab3e1-144">Handle the additional HolographicCamera render in Unity</span></span>

>[!NOTE]
> <span data-ttu-id="ab3e1-145">Unity PV 카메라에서 렌더링 하는 개발 중 지원과 아직 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-145">Unity support to render from the PV camera is under development and can't be used, yet.</span></span> <span data-ttu-id="ab3e1-146">이 설명서는 PV 카메라에서 렌더링에 대 한 지원 사용 하 여 Unity의 빌드를 사용할 때 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-146">This documentation will be updated when a build of Unity with support for rendering from the PV camera is available.</span></span>

##### <a name="verify-shaders-and-code-support-additional-cameras"></a><span data-ttu-id="ab3e1-147">셰이더를 확인 하 고 추가 카메라 지원 코드</span><span class="sxs-lookup"><span data-stu-id="ab3e1-147">Verify shaders and code support additional cameras</span></span>

<span data-ttu-id="ab3e1-148">혼합된 현실 캡처 및 비정상적인 맞춤, 누락 된 콘텐츠 또는 성능 문제에 대 한 검사를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-148">Run a mixed reality capture and check for unusual alignment, missing content, or performance issues.</span></span> <span data-ttu-id="ab3e1-149">셰이더와 적절 하 게 코드를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-149">Update shaders and code as appropriate.</span></span>

<span data-ttu-id="ab3e1-150">특정 장면을 렌더링 추가 카메라를 지원 하지 않는 경우에 해당 과정 중 PhotoVideoCamera의 HolographicViewConfiguration를 비활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-150">If there are certain scenes that cannot support rendering to an additional camera, you can disable the PhotoVideoCamera's HolographicViewConfiguration during them.</span></span>

### <a name="disabling-mrc-in-your-app"></a><span data-ttu-id="ab3e1-151">앱에서 사용 하지 않도록 설정 MRC</span><span class="sxs-lookup"><span data-stu-id="ab3e1-151">Disabling MRC in your app</span></span>

#### <a name="2d-app"></a><span data-ttu-id="ab3e1-152">2D 앱</span><span class="sxs-lookup"><span data-stu-id="ab3e1-152">2D app</span></span>

<span data-ttu-id="ab3e1-153">2D 앱에서 혼합된 현실 캡처 중인지 가려질 해당 시각적 콘텐츠를 선택할 수 있습니다.:</span><span class="sxs-lookup"><span data-stu-id="ab3e1-153">2D apps can choose to have their visual content obscured when mixed reality capture is running by:</span></span>
* <span data-ttu-id="ab3e1-154">사용 하 여 표시 합니다 [DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-present) 플래그</span><span class="sxs-lookup"><span data-stu-id="ab3e1-154">Present with the [DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-present) flag</span></span>
* <span data-ttu-id="ab3e1-155">사용 하 여 앱의 스왑 체인을 만들 합니다 [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://docs.microsoft.com/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag) 플래그</span><span class="sxs-lookup"><span data-stu-id="ab3e1-155">Create the app's swap chain with the [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://docs.microsoft.com/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag) flag</span></span>
* <span data-ttu-id="ab3e1-156">Windows 10을 사용 하 여 업데이트할 수 있습니다 2019, ApplicationView의 설정 [IsScreenCaptureEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled)</span><span class="sxs-lookup"><span data-stu-id="ab3e1-156">With the Windows 10 May 2019 Update, setting ApplicationView's [IsScreenCaptureEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled)</span></span>

#### <a name="immersive-app"></a><span data-ttu-id="ab3e1-157">몰입 형 앱</span><span class="sxs-lookup"><span data-stu-id="ab3e1-157">Immersive app</span></span>

<span data-ttu-id="ab3e1-158">몰입 형 앱을 해당 시각적 콘텐츠에서 혼합된 현실 캡처에서 제외 하도록 선택할 수 있습니다.:</span><span class="sxs-lookup"><span data-stu-id="ab3e1-158">Immersive apps can choose to have their visual content excluded from mixed reality capture by:</span></span>
* <span data-ttu-id="ab3e1-159">HolographicCameraRenderingParameter의 설정 [IsContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled) 관련된 프레임에 대 한 혼합된 현실 캡처를 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="ab3e1-159">Setting HolographicCameraRenderingParameter's [IsContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled) to disable mixed reality capture for its associated frame</span></span>
* <span data-ttu-id="ab3e1-160">HolographicCamera의 설정 [IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled) 해당 연결된 holographic 카메라에 대 한 혼합된 현실 캡처를 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="ab3e1-160">Setting HolographicCamera's [IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled) to disable mixed reality capture for its associated holographic camera</span></span>

#### <a name="password-keyboard"></a><span data-ttu-id="ab3e1-161">암호 키보드</span><span class="sxs-lookup"><span data-stu-id="ab3e1-161">Password Keyboard</span></span>

<span data-ttu-id="ab3e1-162">Windows 10 년 5 월 업데이트 2019, 암호 또는 pin 키보드 표시 되는 경우 혼합된 현실 캡처에서 시각적 콘텐츠가 자동으로 제외 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-162">With the Windows 10 May 2019 Update, visual content is automatically excluded from mixed reality capture when a password or pin keyboard is visible.</span></span>

### <a name="knowing-when-mrc-is-active"></a><span data-ttu-id="ab3e1-163">MRC이 활성화 되 면 파악</span><span class="sxs-lookup"><span data-stu-id="ab3e1-163">Knowing when MRC is active</span></span>

<span data-ttu-id="ab3e1-164">합니다 [AppCapture](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.AppCapture) 혼합 현실 캡처 시스템 (오디오 또는 비디오)에 실행 될 때 알아야 하는 앱 클래스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-164">The [AppCapture](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.AppCapture) class can be used by an app to know when system mixed reality capture is running (for either audio or video).</span></span>

>[!NOTE]
><span data-ttu-id="ab3e1-165">AppCapture [GetForCurrentView](https://docs.microsoft.com/uwp/api/windows.media.capture.appcapture.getforcurrentview) null 실제로 캡처를 혼합 하는 경우 장치에서 사용할 수 없는 API를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-165">AppCapture's [GetForCurrentView](https://docs.microsoft.com/uwp/api/windows.media.capture.appcapture.getforcurrentview) API can return null if mixed reality capture isn't available on the device.</span></span> <span data-ttu-id="ab3e1-166">앱 일시 중단 되 면 CapturingChanged 이벤트 등록을 취소 해야 이기도, MRC 차단 된 상태로 가져올 수는 그렇지 않은 경우.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-166">It's also important to de-register the CapturingChanged event when your app is suspended, otherwise MRC can get into a blocked state.</span></span>

### <a name="best-practices-hololens-specific"></a><span data-ttu-id="ab3e1-167">모범 사례 (HoloLens에 한정)</span><span class="sxs-lookup"><span data-stu-id="ab3e1-167">Best practices (HoloLens-specific)</span></span>

<span data-ttu-id="ab3e1-168">MRC는 개발자가 추가 작업 없이도 작동 해야 하지만 앱의 혼합된 현실 가장 캡처 환경을 제공 하기 위해 알아야 할 몇 가지 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-168">MRC is expected to work without additional work from developers, but there are a few things to be aware of to provide the best mixed reality capture experience of your app.</span></span>

<span data-ttu-id="ab3e1-169">**MRC 홀로그램의 알파 채널을 사용 하 여와 혼합 하 여 [카메라](locatable-camera.md) 이미지**</span><span class="sxs-lookup"><span data-stu-id="ab3e1-169">**MRC uses the hologram’s alpha channel to blend with the [camera](locatable-camera.md) imagery**</span></span>

<span data-ttu-id="ab3e1-170">불투명 한 검정색으로 선택을 취소 하는 대신 투명 검정으로 앱 지우기가 있는지 확인 하는 가장 중요 한 단계가입니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-170">The most important step is to make sure your app is clearing to transparent black instead of clearing to opaque black.</span></span> <span data-ttu-id="ab3e1-171">Unity에서 기본적으로 MixedRealityToolkit 이렇게 있지만 변경 하는 한 줄을 확인 해야 아닌 Unity에서 개발 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-171">In Unity, this is done by default with the MixedRealityToolkit but if you are developing in non-Unity, you may need to make a one line change.</span></span>

<span data-ttu-id="ab3e1-172">다음은 일부 아티팩트가 응용 프로그램을 투명 검정으로 선택을 취소 하지는 MRC에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-172">Here are some of the artifacts you might see in MRC if your app is not clearing to transparent black:</span></span>

<span data-ttu-id="ab3e1-173">**예제 오류**: 검정 (투명 한 검정으로 지우려면 장애) 콘텐츠에 대 한 가장자리</span><span class="sxs-lookup"><span data-stu-id="ab3e1-173">**Example Failures**: Black edges around the content (failing to clear to transparent black)</span></span>

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

<span data-ttu-id="ab3e1-174">**예제 오류**: 전체 배경 장면을 홀로그램의 검정색으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-174">**Example Failures**: The entire background scene of the hologram appears black.</span></span> <span data-ttu-id="ab3e1-175">검은색 배경에서 1의 결과 백그라운드 알파 값 설정</span><span class="sxs-lookup"><span data-stu-id="ab3e1-175">Setting a background alpha value of 1 results in a black background</span></span>

![검은색 배경에서 1의 결과 백그라운드 알파 값 설정](images/clearopaqueblack-300px.png)

<span data-ttu-id="ab3e1-177">**예상 결과**: 홀로그램 실제 (투명 한 검정으로 선택을 취소 하는 경우 예상된 결과)를 사용 하 여 제대로 혼합 표시</span><span class="sxs-lookup"><span data-stu-id="ab3e1-177">**Expected Result**: Holograms appear properly blended with the real-world (expected result if clearing to transparent black)</span></span>

![투명 한 검정으로 선택을 취소 하는 경우 예상된 결과](images/cleartransparentblack-300px.png)

<span data-ttu-id="ab3e1-179">**해결 방법**:</span><span class="sxs-lookup"><span data-stu-id="ab3e1-179">**Solution**:</span></span>
* <span data-ttu-id="ab3e1-180">된 알파 값 0 불투명 검은색으로 표시 되는 모든 콘텐츠를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-180">Change any content that is showing up as opaque black to have an alpha value of 0.</span></span>
* <span data-ttu-id="ab3e1-181">투명 검정으로 앱 지우기는 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-181">Ensure that the app is clearing to transparent black.</span></span>
* <span data-ttu-id="ab3e1-182">Unity 기본값 ID3D11DeiceContext::ClearRenderTargetView()를 사용 하 여 사용 된 색을 수정 해야 하는 비 Unity 앱 인지 하지만 MixedRealityToolkit를 사용 하 여 자동으로 취소 하려면 선택을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-182">Unity defaults to clear to clear automatically with the MixedRealityToolkit, but if it’s a non-Unity app you should modify the color used with ID3D11DeiceContext::ClearRenderTargetView().</span></span> <span data-ttu-id="ab3e1-183">불투명 한 검은색 (0,0,0,1) 대신 투명 한 검은색 (0,0,0,0)의 선택을 취소 하면 확인 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-183">You want to ensure you clear to transparent black (0,0,0,0) instead of opaque black (0,0,0,1).</span></span>

<span data-ttu-id="ab3e1-184">이제 원하는 경우 일반적으로 필요가 없습니다 자산의 알파 값을 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-184">You can now tune the alpha values of your assets if you’d like, but typically don’t need to.</span></span> <span data-ttu-id="ab3e1-185">대부분의 경우 MRCs 즉시 좋은 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-185">Most of the time, MRCs will look good out of the box.</span></span> <span data-ttu-id="ab3e1-186">MRC 미리 곱한 알파를 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-186">MRC assumes pre-multiplied alpha.</span></span> <span data-ttu-id="ab3e1-187">알파 값에는 MRC 캡처만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-187">The alpha values will only affect the MRC capture.</span></span>

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a><span data-ttu-id="ab3e1-188">MRC HoloLens에 설정 된 경우 예상 되는 상황</span><span class="sxs-lookup"><span data-stu-id="ab3e1-188">What to expect when MRC is enabled on HoloLens</span></span>

<span data-ttu-id="ab3e1-189">다음에 적용 (항목인 1 세대) HoloLens 및 HoloLens 2 언급이 없는 경우:</span><span class="sxs-lookup"><span data-stu-id="ab3e1-189">The following apply to both HoloLens (first-generation) and HoloLens 2, unless otherwise noted:</span></span>

* <span data-ttu-id="ab3e1-190">시스템에는 30 Hz 렌더링 응용 프로그램을 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-190">The system will throttle the application to 30Hz rendering.</span></span> <span data-ttu-id="ab3e1-191">이 앱 상수 예산 예약 유지 필요가 없도록 하려면 MRC 한 일부 여유가 만들고 30fps MRC 비디오 녹화 framerate 일치</span><span class="sxs-lookup"><span data-stu-id="ab3e1-191">This creates some headroom for MRC to run so the app doesn’t need to keep a constant budget reserve and also matches the MRC video record framerate of 30fps</span></span>
* <span data-ttu-id="ab3e1-192">홀로그램 장치의 오른쪽 눈에 보일 수도 있습니다 "번쩍이기" 기록/스트리밍할 때 MRC: 텍스트를 더 읽기 어렵다고 될 수 있습니다 및 홀로그램 가장자리 더 깨진 나타날 수 있습니다 (타사 카메라에 옵트인에 렌더링할 **HoloLens 2** 방지 이 손상)</span><span class="sxs-lookup"><span data-stu-id="ab3e1-192">Hologram content in the right eye of the device may appear to “sparkle” when recording/streaming MRC: text may become more difficult to read and hologram edges may appear more jaggy (opting-in to 3rd camera render on **HoloLens 2** avoids this compromise)</span></span>
* <span data-ttu-id="ab3e1-193">MRC 사진 및 동영상 응용 프로그램의 존중 [지점 집중](focus-point-in-unity.md) 응용 프로그램이 설정한 경우 됩니다 수 있게 도와주는 홀로그램 정확 하 게 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-193">MRC photos and videos will respect the application’s [focus point](focus-point-in-unity.md) if the application has enabled it, which will help ensure holograms are accurately positioned.</span></span> <span data-ttu-id="ab3e1-194">비디오에 대 한의 포커스 지점은 위해 다듬어집니다는 홀로그램 포커스 요소 깊이 크게 변경 되 면 제자리에 드리프트 느리게 보일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-194">For videos, the Focus Point is smoothed so holograms may appear to slowly drift into place if the Focus Point depth changes significantly.</span></span> <span data-ttu-id="ab3e1-195">홀로그램 포커스 지점에서 다른 깊이 실제 (아래 예제 참조는 포커스 지점을 2m에서 설정 되지만 홀로그램 1m의 위치가)에서 오프셋 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-195">Holograms that are at different depths from the focus point may appear offset from the real world (see example below where Focus Point is set at 2 meters but hologram is positioned at 1 meter).</span></span>

![홀로그램 2m에서 전 세계에 완벽 하 게 등록 표시 됩니다.](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a><span data-ttu-id="ab3e1-198">앱 내에서 MRC 기능 통합</span><span class="sxs-lookup"><span data-stu-id="ab3e1-198">Integrating MRC functionality from within your app</span></span>

<span data-ttu-id="ab3e1-199">혼합된 현실 앱 MRC 사진 또는 앱 내에서 비디오 캡처를 시작할 수 있습니다 및 저장 되지 않고 캡처된 콘텐츠 앱에 사용할 수는 장치의 "카메라 앨범."를</span><span class="sxs-lookup"><span data-stu-id="ab3e1-199">Your mixed reality app can initiate MRC photo or video capture from within the app, and the content captured is made available to your app without being stored to the device's "Camera roll."</span></span> <span data-ttu-id="ab3e1-200">사용자 지정 MRC 레코더를 만들거나 기본 제공 카메라 캡처 UI 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-200">You can create a custom MRC recorder or take advantage of built-in camera capture UI.</span></span> 

### <a name="mrc-with-built-in-camera-ui"></a><span data-ttu-id="ab3e1-201">기본 제공 카메라 UI 사용 하 여 MRC</span><span class="sxs-lookup"><span data-stu-id="ab3e1-201">MRC with built-in camera UI</span></span>

<span data-ttu-id="ab3e1-202">개발자가 사용할 수는 *[카메라 캡처 UI API](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* 혼합된 현실 사용자 캡처된 사진 또는 비디오 몇 줄의 코드만으로 가져오려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-202">Developers can use the *[Camera Capture UI API](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* to get a user-captured mixed reality photo or video with just a few lines of code.</span></span>

<span data-ttu-id="ab3e1-203">이 API는 기본 제공 MRC 카메라 UI를 올 사용자 사진 또는 비디오를 걸릴 수 있으며 결과 캡처를 앱에 반환를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-203">This API launches the built-in MRC camera UI, from which the user can take a photo or video, and returns the resulting capture to your app.</span></span>  <span data-ttu-id="ab3e1-204">사용자 고유의 카메라 UI를 만들려면 않거나 필요한 하위 수준 캡처 스트림에 대 한 액세스, 사용자 지정 혼합 현실 캡처 레코더를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-204">If you want to create your own camera UI, or need lower-level access to the capture stream, you can create a custom Mixed Reality Capture recorder.</span></span>

### <a name="creating-a-custom-mrc-recorder"></a><span data-ttu-id="ab3e1-205">사용자 지정 MRC 레코더 만들기</span><span class="sxs-lookup"><span data-stu-id="ab3e1-205">Creating a custom MRC recorder</span></span>

<span data-ttu-id="ab3e1-206">사용자 사진을 늘 실행 수 또는 시스템을 사용 하 여 비디오 MRC 캡처 서비스, 응용 프로그램 사용자 지정 카메라 앱을 빌드 하지만 홀로그램 MRC 마찬가지로 카메라 스트림에 포함 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-206">While the user can always trigger a photo or video using the system MRC capture service, an application may want to build a custom camera app but include holograms in the camera stream just like MRC.</span></span> <span data-ttu-id="ab3e1-207">이 응용 프로그램을 사용자를 대신 하 여 캡처를 시작, 빌드 사용자 지정 UI를 녹음/녹화 또는 MRC 설정을 몇 가지 예제 이름을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-207">This allows the application to kick off captures on behalf of the user, build custom recording UI, or customize MRC settings to name a few examples.</span></span>

<span data-ttu-id="ab3e1-208">**HoloStudio는 MRC 효과 사용 하 여 사용자 지정 MRC 카메라 추가**</span><span class="sxs-lookup"><span data-stu-id="ab3e1-208">**HoloStudio adds a custom MRC camera using MRC effects**</span></span>

![HoloStudio는 MRC 효과 사용 하 여 사용자 지정 MRC 카메라 추가](images/cameraiconholostudio-300px.jpg)

<span data-ttu-id="ab3e1-210">Unity 응용 프로그램 나타납니다 [Locatable_camera_in_Unity](locatable-camera-in-unity.md) 홀로그램을 사용 하도록 설정 하려면 속성에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-210">Unity Applications should see [Locatable_camera_in_Unity](locatable-camera-in-unity.md) for the property to enable holograms.</span></span>

<span data-ttu-id="ab3e1-211">다른 응용 프로그램이이 사용 하 여 수행할 수는 [Windows 미디어 캡처 Api](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaCapture) 카메라를 제어 및 가상 홀로그램 및 응용 프로그램 오디오 스틸 및 비디오에 포함 하도록 MRC 비디오 및 오디오 효과 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-211">Other applications can do this by using the [Windows Media Capture APIs](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaCapture) to control the Camera and add an MRC Video and Audio effect to include virtual holograms and application audio in stills and videos.</span></span>

<span data-ttu-id="ab3e1-212">응용 프로그램의 효과 추가 하려면 두 가지 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-212">Applications have two options to add the effect:</span></span>
* <span data-ttu-id="ab3e1-213">이전 API: [Windows.Media.Capture.MediaCapture.AddEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addeffectasync)</span><span class="sxs-lookup"><span data-stu-id="ab3e1-213">The older API: [Windows.Media.Capture.MediaCapture.AddEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addeffectasync)</span></span>
* <span data-ttu-id="ab3e1-214">새 Microsoft 권장 API (동적 속성을 조작할 수 있도록 하는 개체를 반환한): [Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) 앱 의자체구현을만들필요는[IVideoEffectDefinition](https://docs.microsoft.com/uwp/api/Windows.Media.Effects.IVideoEffectDefinition) 하 고 [IAudioEffectDefinition](https://docs.microsoft.com/uwp/api/windows.media.effects.iaudioeffectdefinition)합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-214">The new Microsoft recommended API (returns an object, making it possible to manipulate dynamic properties): [Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) which require the app create its own implementation of [IVideoEffectDefinition](https://docs.microsoft.com/uwp/api/Windows.Media.Effects.IVideoEffectDefinition) and [IAudioEffectDefinition](https://docs.microsoft.com/uwp/api/windows.media.effects.iaudioeffectdefinition).</span></span> <span data-ttu-id="ab3e1-215">샘플 사용에 대 한 MRC 효과 샘플을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-215">Please see the MRC effect sample for sample usage.</span></span>

>[!NOTE]
> <span data-ttu-id="ab3e1-216">Windows.Media.MixedRealityCapture 네임 스페이스는 Visual Studio에서 인식 되지 않습니다 하지만 문자열은 여전히 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-216">The Windows.Media.MixedRealityCapture namespace will not be recognized by Visual Studio, but the strings are still valid.</span></span>

<span data-ttu-id="ab3e1-217">MRC 비디오 효과 (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)</span><span class="sxs-lookup"><span data-stu-id="ab3e1-217">MRC Video Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)</span></span>

|  <span data-ttu-id="ab3e1-218">속성 이름</span><span class="sxs-lookup"><span data-stu-id="ab3e1-218">Property Name</span></span>  |  <span data-ttu-id="ab3e1-219">형식</span><span class="sxs-lookup"><span data-stu-id="ab3e1-219">Type</span></span>  |  <span data-ttu-id="ab3e1-220">Default Value</span><span class="sxs-lookup"><span data-stu-id="ab3e1-220">Default Value</span></span>  |  <span data-ttu-id="ab3e1-221">설명</span><span class="sxs-lookup"><span data-stu-id="ab3e1-221">Description</span></span> | 
|----------|----------|----------|----------|
|  <span data-ttu-id="ab3e1-222">StreamType</span><span class="sxs-lookup"><span data-stu-id="ab3e1-222">StreamType</span></span>  |  <span data-ttu-id="ab3e1-223">UINT32 ([MediaStreamType](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaStreamType))</span><span class="sxs-lookup"><span data-stu-id="ab3e1-223">UINT32 ([MediaStreamType](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaStreamType))</span></span>  |  <span data-ttu-id="ab3e1-224">1 (VideoRecord)</span><span class="sxs-lookup"><span data-stu-id="ab3e1-224">1 (VideoRecord)</span></span>  |  <span data-ttu-id="ab3e1-225">이 효과에 사용 되는 캡처 스트림을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-225">Describe which capture stream this effect is used for.</span></span> <span data-ttu-id="ab3e1-226">오디오를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-226">Audio is not available.</span></span> | 
|  <span data-ttu-id="ab3e1-227">HologramCompositionEnabled</span><span class="sxs-lookup"><span data-stu-id="ab3e1-227">HologramCompositionEnabled</span></span>  |  <span data-ttu-id="ab3e1-228">boolean</span><span class="sxs-lookup"><span data-stu-id="ab3e1-228">boolean</span></span>  |  <span data-ttu-id="ab3e1-229">TRUE</span><span class="sxs-lookup"><span data-stu-id="ab3e1-229">TRUE</span></span>  |  <span data-ttu-id="ab3e1-230">홀로그램 비디오 캡처에서를 사용 하지 않도록 설정 하거나 사용 하는 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-230">Flag to enable or disable holograms in video capture.</span></span> | 
|  <span data-ttu-id="ab3e1-231">RecordingIndicatorEnabled</span><span class="sxs-lookup"><span data-stu-id="ab3e1-231">RecordingIndicatorEnabled</span></span>  |  <span data-ttu-id="ab3e1-232">boolean</span><span class="sxs-lookup"><span data-stu-id="ab3e1-232">boolean</span></span>  |  <span data-ttu-id="ab3e1-233">TRUE</span><span class="sxs-lookup"><span data-stu-id="ab3e1-233">TRUE</span></span>  |  <span data-ttu-id="ab3e1-234">홀로그램 캡처 시 화면에서 기록 표시기를 사용할지를 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-234">Flag to enable or disable recording indicator on screen during hologram capturing.</span></span> | 
|  <span data-ttu-id="ab3e1-235">VideoStabilizationEnabled</span><span class="sxs-lookup"><span data-stu-id="ab3e1-235">VideoStabilizationEnabled</span></span>  |  <span data-ttu-id="ab3e1-236">boolean</span><span class="sxs-lookup"><span data-stu-id="ab3e1-236">boolean</span></span>  |  <span data-ttu-id="ab3e1-237">FALSE</span><span class="sxs-lookup"><span data-stu-id="ab3e1-237">FALSE</span></span>  |  <span data-ttu-id="ab3e1-238">HoloLens 추적기에서 제공 하는 비디오 안정화를 사용할지를 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-238">Flag to enable or disable video stabilization powered by the HoloLens tracker.</span></span> | 
|  <span data-ttu-id="ab3e1-239">VideoStabilizationBufferLength</span><span class="sxs-lookup"><span data-stu-id="ab3e1-239">VideoStabilizationBufferLength</span></span>  |  <span data-ttu-id="ab3e1-240">UINT32</span><span class="sxs-lookup"><span data-stu-id="ab3e1-240">UINT32</span></span>  |  <span data-ttu-id="ab3e1-241">0</span><span class="sxs-lookup"><span data-stu-id="ab3e1-241">0</span></span>  |  <span data-ttu-id="ab3e1-242">설정 비디오 안정화에 대 한 기록 프레임 수가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-242">Set how many historical frames are used for video stabilization.</span></span> <span data-ttu-id="ab3e1-243">0 0-대기 시간 및 기능과 성능 측면에서 거의 "무료"입니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-243">0 is 0-latency and nearly "free" from a power and performance perspective.</span></span> <span data-ttu-id="ab3e1-244">(대기 시간 및 메모리의 15 프레임) 하는 대신 가장 높은 품질에 대 한 15는 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-244">15 is recommended for highest quality (at the cost of 15 frames of latency and memory).</span></span> | 
|  <span data-ttu-id="ab3e1-245">GlobalOpacityCoefficient</span><span class="sxs-lookup"><span data-stu-id="ab3e1-245">GlobalOpacityCoefficient</span></span>  |  <span data-ttu-id="ab3e1-246">FLOAT</span><span class="sxs-lookup"><span data-stu-id="ab3e1-246">float</span></span>  |  <span data-ttu-id="ab3e1-247">0.9 (HoloLens) 1.0 (몰입 형 헤드셋)</span><span class="sxs-lookup"><span data-stu-id="ab3e1-247">0.9 (HoloLens) 1.0 (Immersive headset)</span></span>  |  <span data-ttu-id="ab3e1-248">홀로그램 전역 불투명도 계수 범위의 (완전히 투명) 0.0에서 1.0으로 설정 (완전 불투명).</span><span class="sxs-lookup"><span data-stu-id="ab3e1-248">Set global opacity coefficient of hologram in range from 0.0 (fully transparent) to 1.0 (fully opaque).</span></span> | 
|  <span data-ttu-id="ab3e1-249">BlankOnProtectedContent</span><span class="sxs-lookup"><span data-stu-id="ab3e1-249">BlankOnProtectedContent</span></span>  |  <span data-ttu-id="ab3e1-250">boolean</span><span class="sxs-lookup"><span data-stu-id="ab3e1-250">boolean</span></span>  |  <span data-ttu-id="ab3e1-251">FALSE</span><span class="sxs-lookup"><span data-stu-id="ab3e1-251">FALSE</span></span>  |  <span data-ttu-id="ab3e1-252">활성화 하거나 비활성화는 2d UWP 앱 보여 주는 보호 된 콘텐츠가 있는 경우 빈 프레임을 반환 하는 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-252">Flag to enable or disable returning an empty frame if there is a 2d UWP app showing protected content.</span></span> <span data-ttu-id="ab3e1-253">이 플래그는 false 및 2d UWP 앱 인지 보여 주는 보호 된 콘텐츠, 혼합된 현실 캡처 모두 헤드셋에 보호 된 콘텐츠 질감 2d UWP 앱 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-253">If this flag is false and a 2d UWP app is showing protected content, the 2d UWP app will be replaced by a protected content texture in both the headset and in the mixed reality capture.</span></span> |
|  <span data-ttu-id="ab3e1-254">ShowHiddenMesh</span><span class="sxs-lookup"><span data-stu-id="ab3e1-254">ShowHiddenMesh</span></span>  |  <span data-ttu-id="ab3e1-255">boolean</span><span class="sxs-lookup"><span data-stu-id="ab3e1-255">boolean</span></span>  |  <span data-ttu-id="ab3e1-256">FALSE</span><span class="sxs-lookup"><span data-stu-id="ab3e1-256">FALSE</span></span>  |  <span data-ttu-id="ab3e1-257">사용 하도록 설정 하거나 holographic 카메라의 숨겨진된 영역 메시를 표시 하 고 콘텐츠를 인접 하지 않도록 설정 하는 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-257">Flag to enable or disable showing the holographic camera's hidden area mesh and neighboring content.</span></span> |
| <span data-ttu-id="ab3e1-258">OutputSize</span><span class="sxs-lookup"><span data-stu-id="ab3e1-258">OutputSize</span></span> | <span data-ttu-id="ab3e1-259">Size</span><span class="sxs-lookup"><span data-stu-id="ab3e1-259">Size</span></span> | <span data-ttu-id="ab3e1-260">0, 0</span><span class="sxs-lookup"><span data-stu-id="ab3e1-260">0, 0</span></span> | <span data-ttu-id="ab3e1-261">비디오 안정화에 그림이 잘린 후 원하는 출력 크기를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-261">Set the desired output size after cropping for video stabilization.</span></span> <span data-ttu-id="ab3e1-262">0 또는 잘못 된 출력 크기를 지정 하는 경우 기본 자르기 크기가 선택 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-262">A default crop size is chosen if 0 or an invalid output size is specified.</span></span> |
| <span data-ttu-id="ab3e1-263">PreferredHologramPerspective</span><span class="sxs-lookup"><span data-stu-id="ab3e1-263">PreferredHologramPerspective</span></span> | <span data-ttu-id="ab3e1-264">UINT32</span><span class="sxs-lookup"><span data-stu-id="ab3e1-264">UINT32</span></span> | <span data-ttu-id="ab3e1-265">1 (PhotoVideoCamera)</span><span class="sxs-lookup"><span data-stu-id="ab3e1-265">1 (PhotoVideoCamera)</span></span> | <span data-ttu-id="ab3e1-266">구성 하는 holographic 카메라 보기 캡처해야 나타내는 데 사용 하는 열거형입니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-266">Enum used to indicate which holographic camera view configuration should be captured.</span></span> <span data-ttu-id="ab3e1-267">앱에서 사진/비디오를 렌더링 하 라는 메시지가 표시 되지 않습니다 0 (표시)으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-267">Setting 0 (Display) means that the app won't be asked to render from the photo/video camera</span></span> |

<span data-ttu-id="ab3e1-268">MRC 오디오 효과 (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)</span><span class="sxs-lookup"><span data-stu-id="ab3e1-268">MRC Audio Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)</span></span>

<table>
<tr>
<th><span data-ttu-id="ab3e1-269">속성 이름</span><span class="sxs-lookup"><span data-stu-id="ab3e1-269">Property Name</span></span></th>
<th><span data-ttu-id="ab3e1-270">형식</span><span class="sxs-lookup"><span data-stu-id="ab3e1-270">Type</span></span></th>
<th><span data-ttu-id="ab3e1-271">Default Value</span><span class="sxs-lookup"><span data-stu-id="ab3e1-271">Default Value</span></span></th>
<th><span data-ttu-id="ab3e1-272">설명</span><span class="sxs-lookup"><span data-stu-id="ab3e1-272">Description</span></span></th>
</tr>
<tr>
<td><span data-ttu-id="ab3e1-273">MixerMode</span><span class="sxs-lookup"><span data-stu-id="ab3e1-273">MixerMode</span></span></td>
<td><span data-ttu-id="ab3e1-274">UINT32</span><span class="sxs-lookup"><span data-stu-id="ab3e1-274">UINT32</span></span></td>
<td><span data-ttu-id="ab3e1-275">2</span><span class="sxs-lookup"><span data-stu-id="ab3e1-275">2</span></span></td>
<td>
<ul>
<li><span data-ttu-id="ab3e1-276">0 : Mic 오디오 전용</span><span class="sxs-lookup"><span data-stu-id="ab3e1-276">0 : Mic audio only</span></span></li>
<li><span data-ttu-id="ab3e1-277">1 : 시스템 오디오 전용</span><span class="sxs-lookup"><span data-stu-id="ab3e1-277">1 : System audio only</span></span></li>
<li><span data-ttu-id="ab3e1-278">2 : Mic 및 시스템 오디오</span><span class="sxs-lookup"><span data-stu-id="ab3e1-278">2 : Mic and System audio</span></span></li>
</ul>
</td>
</tr>
</table>

### <a name="simultaneous-mrc-limitations"></a><span data-ttu-id="ab3e1-279">동시 MRC 제한 사항</span><span class="sxs-lookup"><span data-stu-id="ab3e1-279">Simultaneous MRC limitations</span></span>

<span data-ttu-id="ab3e1-280">MRC 동시에 액세스 하는 여러 앱 주위에 특정 제한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-280">There are certain limitations around multiple apps accessing MRC at the same time.</span></span>

#### <a name="photovideo-camera-access"></a><span data-ttu-id="ab3e1-281">사진/비디오 카메라 액세스</span><span class="sxs-lookup"><span data-stu-id="ab3e1-281">Photo/video camera access</span></span>

<span data-ttu-id="ab3e1-282">사진/비디오 카메라는 동시에 액세스할 수 있는 프로세스 수가 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-282">The photo/video camera is limited to the number of processes that can access it at the same time.</span></span> <span data-ttu-id="ab3e1-283">프로세스를 기록 하는 동안 사진을 다른 프로세스를 실행 하거나 비디오 사진/비디오 카메라를 획득 하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-283">While a process is recording video or taking a photo any other process will fail to acquire the photo/video camera.</span></span> <span data-ttu-id="ab3e1-284">(혼합 현실 캡처 및 표준 사진/비디오 캡처를 모두에 적용)</span><span class="sxs-lookup"><span data-stu-id="ab3e1-284">(this applies to both Mixed Reality Capture and standard photo/video capture)</span></span>

<span data-ttu-id="ab3e1-285">HoloLens 2를 사용 하 여 앱 MediaCaptureInitializationSettings의 따르면 [SharingMode](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode) 사진/비디오 카메라에 대 한 독점적인 제어권 필요할 경우 SharedReadOnly 실행할 것인지를 나타내는 속성을 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-285">With HoloLens 2, an app can use MediaCaptureInitializationSettings's [SharingMode](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode) property to indicate that they want to run SharedReadOnly if they don't need exclusive control over the photo/video camera.</span></span> <span data-ttu-id="ab3e1-286">이렇게 확인 및 캡처의 프레임 속도 어떤 다른 앱 구성 있도록 카메라 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-286">Doing so means the resolution and framerate of the capture will be limited to what other apps have configured the camera to provide.</span></span>

##### <a name="built-in-mrc-photovideo-camera-access"></a><span data-ttu-id="ab3e1-287">기본 제공 MRC 사진/비디오 카메라 액세스</span><span class="sxs-lookup"><span data-stu-id="ab3e1-287">Built-in MRC photo/video camera access</span></span>

<span data-ttu-id="ab3e1-288">Cortana, 시작 메뉴, 하드웨어 바로 가기, Miracast, Windows Device Portal) (통해 Windows 10에 기본 제공 되는 MRC 기능:</span><span class="sxs-lookup"><span data-stu-id="ab3e1-288">MRC functionality built into Windows 10 (via Cortana, Start Menu, hardware shortcuts, Miracast, Windows Device Portal):</span></span>
* <span data-ttu-id="ab3e1-289">기본적으로 ExclusiveControl를 사용 하 여 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-289">Will run with ExclusiveControl by default</span></span>

<span data-ttu-id="ab3e1-290">그러나 공유 모드에서 작동 하도록 각 하위 시스템에 지원이 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-290">However, support has been added to each subsystem to operate in a shared mode:</span></span>
* <span data-ttu-id="ab3e1-291">앱 ExclusiveControl 사진/비디오 카메라에 대 한 액세스를 요청 하는 경우 기본 제공 MRC 자동으로 중지 됩니다 사진/비디오 카메라를 사용 하 여 앱의 요청은 성공 하므로</span><span class="sxs-lookup"><span data-stu-id="ab3e1-291">If an app requests ExclusiveControl access to the photo/video camera, built-in MRC will automatically stop using the photo/video camera so the app's request will succeed</span></span>
* <span data-ttu-id="ab3e1-292">기본 제공 MRC SharedReadOnly 모드에서 실행 됩니다 MRC 기본 제공 앱에 ExclusiveControl 동안 시작 된 경우</span><span class="sxs-lookup"><span data-stu-id="ab3e1-292">If built-in MRC is started while an app has ExclusiveControl, built-in MRC will run in SharedReadOnly mode</span></span>

<span data-ttu-id="ab3e1-293">이 공유 모드 기능에는 특정 제한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-293">This shared mode functionality has certain restrictions:</span></span>
* <span data-ttu-id="ab3e1-294">Cortana, 하드웨어 바로 가기 또는 시작 메뉴를 통해 사진: 필요한 Windows 10 2018 년 4 월 업데이트 (또는 이상)</span><span class="sxs-lookup"><span data-stu-id="ab3e1-294">Photo via Cortana, hardware shortcuts, or Start Menu: Requires the Windows 10 April 2018 Update (or later)</span></span>
* <span data-ttu-id="ab3e1-295">Cortana, 하드웨어 바로 가기 또는 시작 메뉴를 통해 비디오: 필요한 Windows 10 2018 년 4 월 업데이트 (또는 이상)</span><span class="sxs-lookup"><span data-stu-id="ab3e1-295">Video via Cortana, hardware shortcuts, or Start Menu: Requires the Windows 10 April 2018 Update (or later)</span></span>
* <span data-ttu-id="ab3e1-296">Miracast 통해 스트리밍 MRC: 필요한 Windows 10 년 10 월 2018 업데이트 (또는 이상)</span><span class="sxs-lookup"><span data-stu-id="ab3e1-296">Streaming MRC over Miracast: Requires the Windows 10 October 2018 Update (or later)</span></span>
* <span data-ttu-id="ab3e1-297">Windows Device Portal 통해 또는 HoloLens 도우미 앱을 통해 MRC 스트리밍: HoloLens 2 필요</span><span class="sxs-lookup"><span data-stu-id="ab3e1-297">Streaming MRC over Windows Device Portal or via the HoloLens companion app: Requires HoloLens 2</span></span>

>[!NOTE]
> <span data-ttu-id="ab3e1-298">다른 앱에서 사진/비디오 카메라를 사용 하는 경우 기본 값에서 확인 및 기본 제공 MRC 카메라 UI의 프레임 속도 줄어들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-298">The resolution and framerate of the built-in MRC camera UI might be reduced from its normal values when another app is using the photo/video camera.</span></span>

#### <a name="mrc-access"></a><span data-ttu-id="ab3e1-299">MRC 액세스</span><span class="sxs-lookup"><span data-stu-id="ab3e1-299">MRC access</span></span>

<span data-ttu-id="ab3e1-300">그러나 Windows 10 2018 년 4 월 업데이트를 더 이상 없습니다 (사진/비디오 카메라에 대 한 액세스는 아직 제한) MRC 스트림에 액세스 하는 여러 앱 관련 제한 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-300">With the Windows 10 April 2018 Update, there is no longer a limitation around multiple apps accessing the MRC stream (however, the access to the photo/video camera still has limitations).</span></span>

<span data-ttu-id="ab3e1-301">Windows 10 2018 년 4 월 이전 MRC 레코더를 사용자 지정 하는 앱의 업데이트 된 시스템 MRC (캡처 사진, 비디오, 캡처링 또는 Windows Device Portal 스트리밍)를 사용 하 여 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ab3e1-301">Previous to the Windows 10 April 2018 Update, an app's custom MRC recorder was mutually exclusive with system MRC (capturing photos, capturing videos, or streaming from the Windows Device Portal).</span></span>

## <a name="see-also"></a><span data-ttu-id="ab3e1-302">참조</span><span class="sxs-lookup"><span data-stu-id="ab3e1-302">See also</span></span>
* [<span data-ttu-id="ab3e1-303">혼합 현실 캡처</span><span class="sxs-lookup"><span data-stu-id="ab3e1-303">Mixed reality capture</span></span>](mixed-reality-capture.md)
* [<span data-ttu-id="ab3e1-304">Spectator View</span><span class="sxs-lookup"><span data-stu-id="ab3e1-304">Spectator view</span></span>](spectator-view.md)
