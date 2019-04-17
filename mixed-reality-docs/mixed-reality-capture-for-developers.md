---
title: 개발자를 위한 실제로 캡처 혼합
description: 개발자를 위한 혼합된 현실에 대 한 모범 사례를 캡처합니다.
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: mrc, 사진, 비디오, 캡처, 카메라
ms.openlocfilehash: c2d98baf16b2ea724247224aabadc1e2ca533ec1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599455"
---
# <a name="mixed-reality-capture-for-developers"></a><span data-ttu-id="f7632-104">개발자를 위한 실제로 캡처 혼합</span><span class="sxs-lookup"><span data-stu-id="f7632-104">Mixed reality capture for developers</span></span>

> [!NOTE]
> <span data-ttu-id="f7632-105">HoloLens 2 관련 된 자세한 지침 [예정](index.md#news-and-notes)합니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-105">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span> 

<span data-ttu-id="f7632-106">참조 [앱에서 사용 하도록 설정 하면 MRC](#enabling-mrc-in-your-app) 아래 HoloLens 2에 대 한 새로운 MRC 기능에 대 한 지침에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-106">See [Enabling MRC in your app](#enabling-mrc-in-your-app) below for guidance on a new MRC capability for HoloLens 2.</span></span>

<span data-ttu-id="f7632-107">사용자가 수행할 수 있으므로 [혼합 현실 캡처](mixed-reality-capture.md) (MRC) 사진 또는 언제 든 지 비디오를 응용 프로그램을 개발할 때는 염두 해야 할 몇 가지 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-107">Since a user could take a [mixed reality capture](mixed-reality-capture.md) (MRC) photo or video at any time, there are a few things that you should keep in mind when developing your application.</span></span> <span data-ttu-id="f7632-108">여기에 MRC 시각적 품질 및 MRCs 캡처되는 동안 시스템 변경 내용에 응답 속도 대 한 모범 사례입니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-108">This includes best practices for MRC visual quality and being responsive to system changes while MRCs are being captured.</span></span>

<span data-ttu-id="f7632-109">개발자 혼합된 현실 캡처 및 삽입 하 여 앱에도 원활 하 게 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-109">Developers can also seamlessly integrate mixed reality capture and insertion into their apps.</span></span>

<span data-ttu-id="f7632-110">HoloLens (항목인 1 세대)에 MRC에는 HoloLens 2는 MRC 4k 해상도로 등록 최대 1080p 및 사진과 비디오를 지원 하지만 최대 720p, 사진 및 비디오를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-110">MRC on HoloLens (first-generation) supports videos and photos up to 720p, while MRC on HoloLens 2 supports videos up to 1080p and photos up to 4K resolution.</span></span>

## <a name="the-importance-of-quality-mrc"></a><span data-ttu-id="f7632-111">MRC 품질의 중요성</span><span class="sxs-lookup"><span data-stu-id="f7632-111">The importance of quality MRC</span></span>

<span data-ttu-id="f7632-112">혼합된 현실 사진 캡처되고 비디오는 앱의 사용자에 게는 처음 접하는 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-112">Mixed reality captured photos and videos are likely the first exposure a user will have of your app.</span></span> <span data-ttu-id="f7632-113">혼합된 현실 스크린 샷을 Microsoft Store 페이지 또는 MRCs 소셜 네트워크에서 공유 하는 다른 사용자로 여부입니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-113">Whether as mixed reality screenshots on your Microsoft Store page or from other users sharing MRCs on social networks.</span></span> <span data-ttu-id="f7632-114">MRC 데모 앱, 사용자 교육, 사용자가 해당 혼합된 환경 상호 작용을 공유 하도록 권장 하는 데 사용할 수 및 사용자 설문 조사 및 문제 해결에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-114">You can use MRC to demo your app, educate users, encourage users to share their mixed world interactions, and for user research and problem solving.</span></span>

## <a name="how-mrc-impacts-your-app"></a><span data-ttu-id="f7632-115">MRC 앱에 미치는 영향을</span><span class="sxs-lookup"><span data-stu-id="f7632-115">How MRC impacts your app</span></span>

### <a name="enabling-mrc-in-your-app"></a><span data-ttu-id="f7632-116">앱에서 사용 하도록 설정 하면 MRC</span><span class="sxs-lookup"><span data-stu-id="f7632-116">Enabling MRC in your app</span></span>

<span data-ttu-id="f7632-117">기본적으로 앱 사용자가 혼합된 현실 캡처를 수행할 수 있도록 모든 작업을 수행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-117">By default, an app does not have to do anything to enable users to take mixed reality captures.</span></span> <span data-ttu-id="f7632-118">그러나 사진/비디오 (PV) 카메라와 표시 사이의 간격 증가 하는 HoloLens 2의 디자인을 하기 때문에 우리 도입할의 PV 카메라에 정렬 하는 타사 카메라 렌더링을 생성 하는 새로운 옵션이 **HoloLens 2**합니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-118">However, because the design of HoloLens 2 increases the distance between the photo/video (PV) camera and the display, we'll be introducing a new option to produce a 3rd camera render aligned to the PV camera of **HoloLens 2**.</span></span> 

<span data-ttu-id="f7632-119">타사 카메라에 옵트인 렌더링 HoloLens 2 제품에서 다음과 같이 향상 된 기본 MRC 환경을 통해:</span><span class="sxs-lookup"><span data-stu-id="f7632-119">Opting-in to 3rd camera render on HoloLens 2 offers the following improvements over the default MRC experience:</span></span>
* <span data-ttu-id="f7632-120">물리적 환경 및이 손 (거의 상호 작용) 모두에 맞춤 홀로그램 해야 정확한 전혀 거리를 거리에서 오프셋을 이외의 대신 합니다 [지점 집중](focus-point-in-unity.md) MRC 기본값에서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-120">Hologram alignment to both your physical environment and hands (for near interactions) should be accurate at all distances, instead of having an offset at distances other than the [focus point](focus-point-in-unity.md) as you might see in the default MRC.</span></span>
* <span data-ttu-id="f7632-121">헤드셋에서 오른쪽 눈 손상 되지, MRC 출력 홀로그램 렌더링에 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-121">The right eye in the headset won't be compromised, as it won't be used to render the holograms for the MRC output.</span></span>

### <a name="disabling-mrc-in-your-app"></a><span data-ttu-id="f7632-122">앱에서 사용 하지 않도록 설정 MRC</span><span class="sxs-lookup"><span data-stu-id="f7632-122">Disabling MRC in your app</span></span>

<span data-ttu-id="f7632-123">2D 앱을 사용 하는 경우 [DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://msdn.microsoft.com/library/windows/desktop/bb509554(v=vs.85).aspx) 하거나 [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://msdn.microsoft.com/library/windows/desktop/bb173076(v=vs.85).aspx) 됩니다 앱의 시각적 콘텐츠를 올바르게 구성 된 스왑 체인을 사용 하 여 보호 된 콘텐츠를 표시 하려면 혼합된 현실 캡처 실행 되는 동안에 자동으로 가려집니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-123">When a 2D app uses [DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://msdn.microsoft.com/library/windows/desktop/bb509554(v=vs.85).aspx) or [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://msdn.microsoft.com/library/windows/desktop/bb173076(v=vs.85).aspx) to show protected content with a properly-configured swap chain, the app's visual content will be automatically obscured while mixed reality capture is running.</span></span>

### <a name="knowing-when-mrc-is-active"></a><span data-ttu-id="f7632-124">MRC이 활성화 되 면 파악</span><span class="sxs-lookup"><span data-stu-id="f7632-124">Knowing when MRC is active</span></span>

<span data-ttu-id="f7632-125">합니다 [AppCapture](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.appcapture.aspx) 혼합 현실 캡처 시스템 (오디오 또는 비디오)에 실행 될 때 알아야 하는 앱 클래스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-125">The [AppCapture](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.appcapture.aspx) class can be used by an app to know when system mixed reality capture is running (for either audio or video).</span></span>

>[!NOTE]
><span data-ttu-id="f7632-126">AppCapture [GetForCurrentView](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.appcapture.getforcurrentview.aspx) null 실제로 캡처를 혼합 하는 경우 장치에서 사용할 수 없는 API를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-126">AppCapture's [GetForCurrentView](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.appcapture.getforcurrentview.aspx) API can return null if mixed reality capture isn't available on the device.</span></span> <span data-ttu-id="f7632-127">앱 일시 중단 되 면 CapturingChanged 이벤트 등록을 취소 해야 이기도, MRC 차단 된 상태로 가져올 수는 그렇지 않은 경우.</span><span class="sxs-lookup"><span data-stu-id="f7632-127">It's also important to de-register the CapturingChanged event when your app is suspended, otherwise MRC can get into a blocked state.</span></span>

### <a name="best-practices-hololens-specific"></a><span data-ttu-id="f7632-128">모범 사례 (HoloLens에 한정)</span><span class="sxs-lookup"><span data-stu-id="f7632-128">Best practices (HoloLens-specific)</span></span>

<span data-ttu-id="f7632-129">MRC는 개발자가 추가 작업 없이도 작동 해야 하지만 앱의 혼합된 현실 가장 캡처 환경을 제공 하기 위해 알아야 할 몇 가지 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-129">MRC is expected to work without additional work from developers, but there are a few things to be aware of to provide the best mixed reality capture experience of your app.</span></span>

<span data-ttu-id="f7632-130">**MRC 홀로그램의 알파 채널을 사용 하 여와 혼합 하 여 [카메라](locatable-camera.md) 이미지**</span><span class="sxs-lookup"><span data-stu-id="f7632-130">**MRC uses the hologram’s alpha channel to blend with the [camera](locatable-camera.md) imagery**</span></span>

<span data-ttu-id="f7632-131">불투명 한 검정색으로 선택을 취소 하는 대신 투명 검정으로 앱 지우기가 있는지 확인 하는 가장 중요 한 단계가입니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-131">The most important step is to make sure your app is clearing to transparent black instead of clearing to opaque black.</span></span> <span data-ttu-id="f7632-132">Unity에서 기본적으로 MixedRealityToolkit 이렇게 있지만 변경 하는 한 줄을 확인 해야 아닌 Unity에서 개발 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="f7632-132">In Unity, this is done by default with the MixedRealityToolkit but if you are developing in non-Unity, you may need to make a one line change.</span></span>

<span data-ttu-id="f7632-133">다음은 일부 아티팩트가 응용 프로그램을 투명 검정으로 선택을 취소 하지는 MRC에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-133">Here are some of the artifacts you might see in MRC if your app is not clearing to transparent black:</span></span>

<span data-ttu-id="f7632-134">**예제 오류**: 검정 (투명 한 검정으로 지우려면 장애) 콘텐츠에 대 한 가장자리</span><span class="sxs-lookup"><span data-stu-id="f7632-134">**Example Failures**: Black edges around the content (failing to clear to transparent black)</span></span>

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

<span data-ttu-id="f7632-135">**예제 오류**: 전체 배경 장면을 홀로그램의 검정색으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-135">**Example Failures**: The entire background scene of the hologram appears black.</span></span> <span data-ttu-id="f7632-136">검은색 배경에서 1의 결과 백그라운드 알파 값 설정</span><span class="sxs-lookup"><span data-stu-id="f7632-136">Setting a background alpha value of 1 results in a black background</span></span>

![검은색 배경에서 1의 결과 백그라운드 알파 값 설정](images/clearopaqueblack-300px.png)

<span data-ttu-id="f7632-138">**예상 결과**: 홀로그램 실제 (투명 한 검정으로 선택을 취소 하는 경우 예상된 결과)를 사용 하 여 제대로 혼합 표시</span><span class="sxs-lookup"><span data-stu-id="f7632-138">**Expected Result**: Holograms appear properly blended with the real-world (expected result if clearing to transparent black)</span></span>

![투명 한 검정으로 선택을 취소 하는 경우 예상된 결과](images/cleartransparentblack-300px.png)

<span data-ttu-id="f7632-140">**해결 방법**:</span><span class="sxs-lookup"><span data-stu-id="f7632-140">**Solution**:</span></span>
* <span data-ttu-id="f7632-141">된 알파 값 0 불투명 검은색으로 표시 되는 모든 콘텐츠를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-141">Change any content that is showing up as opaque black to have an alpha value of 0.</span></span>
* <span data-ttu-id="f7632-142">투명 검정으로 앱 지우기는 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-142">Ensure that the app is clearing to transparent black.</span></span>
* <span data-ttu-id="f7632-143">Unity 기본값 ID3D11DeiceContext::ClearRenderTargetView()를 사용 하 여 사용 된 색을 수정 해야 하는 비 Unity 앱 인지 하지만 MixedRealityToolkit를 사용 하 여 자동으로 취소 하려면 선택을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-143">Unity defaults to clear to clear automatically with the MixedRealityToolkit, but if it’s a non-Unity app you should modify the color used with ID3D11DeiceContext::ClearRenderTargetView().</span></span> <span data-ttu-id="f7632-144">불투명 한 검은색 (0,0,0,1) 대신 투명 한 검은색 (0,0,0,0)의 선택을 취소 하면 확인 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-144">You want to ensure you clear to transparent black (0,0,0,0) instead of opaque black (0,0,0,1).</span></span>

<span data-ttu-id="f7632-145">이제 원하는 경우 일반적으로 필요가 없습니다 자산의 알파 값을 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-145">You can now tune the alpha values of your assets if you’d like, but typically don’t need to.</span></span> <span data-ttu-id="f7632-146">대부분의 경우 MRCs 즉시 좋은 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-146">Most of the time, MRCs will look good out of the box.</span></span> <span data-ttu-id="f7632-147">MRC 미리 곱한 알파를 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-147">MRC assumes pre-multiplied alpha.</span></span> <span data-ttu-id="f7632-148">알파 값에는 MRC 캡처만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-148">The alpha values will only affect the MRC capture.</span></span>

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a><span data-ttu-id="f7632-149">MRC HoloLens에 설정 된 경우 예상 되는 상황</span><span class="sxs-lookup"><span data-stu-id="f7632-149">What to expect when MRC is enabled on HoloLens</span></span>

<span data-ttu-id="f7632-150">다음에 적용 (항목인 1 세대) HoloLens 및 HoloLens 2 언급이 없는 경우:</span><span class="sxs-lookup"><span data-stu-id="f7632-150">The following apply to both HoloLens (first-generation) and HoloLens 2, unless otherwise noted:</span></span>

* <span data-ttu-id="f7632-151">시스템에는 30 Hz 렌더링 응용 프로그램을 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-151">The system will throttle the application to 30Hz rendering.</span></span> <span data-ttu-id="f7632-152">이 앱 상수 예산 예약 유지 필요가 없도록 하려면 MRC 한 일부 여유가 만들고 30fps MRC 비디오 녹화 framerate 일치</span><span class="sxs-lookup"><span data-stu-id="f7632-152">This creates some headroom for MRC to run so the app doesn’t need to keep a constant budget reserve and also matches the MRC video record framerate of 30fps</span></span>
* <span data-ttu-id="f7632-153">홀로그램 장치의 오른쪽 눈에 보일 수도 있습니다 "번쩍이기" 기록/스트리밍할 때 MRC: 텍스트를 더 읽기 어렵다고 될 수 있습니다 및 홀로그램 가장자리 더 깨진 나타날 수 있습니다 (타사 카메라에 옵트인에 렌더링할 **HoloLens 2** 방지 이 손상)</span><span class="sxs-lookup"><span data-stu-id="f7632-153">Hologram content in the right eye of the device may appear to “sparkle” when recording/streaming MRC: text may become more difficult to read and hologram edges may appear more jaggy (opting-in to 3rd camera render on **HoloLens 2** avoids this compromise)</span></span>
* <span data-ttu-id="f7632-154">MRC 사진 및 동영상 응용 프로그램의 존중 [지점 집중](focus-point-in-unity.md) 응용 프로그램이 설정한 경우 됩니다 수 있게 도와주는 홀로그램 정확 하 게 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-154">MRC photos and videos will respect the application’s [focus point](focus-point-in-unity.md) if the application has enabled it, which will help ensure holograms are accurately positioned.</span></span> <span data-ttu-id="f7632-155">비디오에 대 한의 포커스 지점은 위해 다듬어집니다는 홀로그램 포커스 요소 깊이 크게 변경 되 면 제자리에 드리프트 느리게 보일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-155">For videos, the Focus Point is smoothed so holograms may appear to slowly drift into place if the Focus Point depth changes significantly.</span></span> <span data-ttu-id="f7632-156">홀로그램 포커스 지점에서 다른 깊이 실제 (아래 예제 참조는 포커스 지점을 2m에서 설정 되지만 홀로그램 1m의 위치가)에서 오프셋 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-156">Holograms that are at different depths from the focus point may appear offset from the real world (see example below where Focus Point is set at 2 meters but hologram is positioned at 1 meter).</span></span>

![홀로그램 2m에서 전 세계에 완벽 하 게 등록 표시 됩니다.](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a><span data-ttu-id="f7632-159">앱 내에서 MRC 기능 통합</span><span class="sxs-lookup"><span data-stu-id="f7632-159">Integrating MRC functionality from within your app</span></span>

<span data-ttu-id="f7632-160">혼합된 현실 앱 MRC 사진 또는 앱 내에서 비디오 캡처를 시작할 수 있습니다 및 저장 되지 않고 캡처된 콘텐츠 앱에 사용할 수는 장치의 "카메라 앨범."를</span><span class="sxs-lookup"><span data-stu-id="f7632-160">Your mixed reality app can initiate MRC photo or video capture from within the app, and the content captured is made available to your app without being stored to the device's "Camera roll."</span></span> <span data-ttu-id="f7632-161">사용자 지정 MRC 레코더를 만들거나 기본 제공 카메라 캡처 UI 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-161">You can create a custom MRC recorder or take advantage of built-in camera capture UI.</span></span> 

### <a name="mrc-with-built-in-camera-ui"></a><span data-ttu-id="f7632-162">기본 제공 카메라 UI 사용 하 여 MRC</span><span class="sxs-lookup"><span data-stu-id="f7632-162">MRC with built-in camera UI</span></span>

<span data-ttu-id="f7632-163">개발자가 사용할 수는 *[카메라 캡처 UI API](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* 혼합된 현실 사용자 캡처된 사진 또는 비디오 몇 줄의 코드만으로 가져오려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-163">Developers can use the *[Camera Capture UI API](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* to get a user-captured mixed reality photo or video with just a few lines of code.</span></span>

<span data-ttu-id="f7632-164">이 API는 기본 제공 MRC 카메라 UI를 올 사용자 사진 또는 비디오를 걸릴 수 있으며 결과 캡처를 앱에 반환를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-164">This API launches the built-in MRC camera UI, from which the user can take a photo or video, and returns the resulting capture to your app.</span></span>  <span data-ttu-id="f7632-165">사용자 고유의 카메라 UI를 만들려면 않거나 필요한 하위 수준 캡처 스트림에 대 한 액세스, 사용자 지정 혼합 현실 캡처 레코더를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-165">If you want to create your own camera UI, or need lower-level access to the capture stream, you can create a custom Mixed Reality Capture recorder.</span></span>

### <a name="creating-a-custom-mrc-recorder"></a><span data-ttu-id="f7632-166">사용자 지정 MRC 레코더 만들기</span><span class="sxs-lookup"><span data-stu-id="f7632-166">Creating a custom MRC recorder</span></span>

<span data-ttu-id="f7632-167">사용자 사진을 늘 실행 수 또는 시스템을 사용 하 여 비디오 MRC 캡처 서비스, 응용 프로그램 사용자 지정 카메라 앱을 빌드 하지만 홀로그램 MRC 마찬가지로 카메라 스트림에 포함 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-167">While the user can always trigger a photo or video using the system MRC capture service, an application may want to build a custom camera app but include holograms in the camera stream just like MRC.</span></span> <span data-ttu-id="f7632-168">이 응용 프로그램을 사용자를 대신 하 여 캡처를 시작, 빌드 사용자 지정 UI를 녹음/녹화 또는 MRC 설정을 몇 가지 예제 이름을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-168">This allows the application to kick off captures on behalf of the user, build custom recording UI, or customize MRC settings to name a few examples.</span></span>

<span data-ttu-id="f7632-169">**HoloStudio는 MRC 효과 사용 하 여 사용자 지정 MRC 카메라 추가**</span><span class="sxs-lookup"><span data-stu-id="f7632-169">**HoloStudio adds a custom MRC camera using MRC effects**</span></span>

![HoloStudio는 MRC 효과 사용 하 여 사용자 지정 MRC 카메라 추가](images/cameraiconholostudio-300px.jpg)

<span data-ttu-id="f7632-171">Unity 응용 프로그램 나타납니다 [Locatable_camera_in_Unity](locatable-camera-in-unity.md) 홀로그램을 사용 하도록 설정 하려면 속성에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-171">Unity Applications should see [Locatable_camera_in_Unity](locatable-camera-in-unity.md) for the property to enable holograms.</span></span>

<span data-ttu-id="f7632-172">다른 응용 프로그램이이 사용 하 여 수행할 수는 [Windows 미디어 캡처 Api](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx) 카메라를 제어 및 가상 홀로그램 및 응용 프로그램 오디오 스틸 및 비디오에 포함 하도록 MRC 비디오 및 오디오 효과 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-172">Other applications can do this by using the [Windows Media Capture APIs](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx) to control the Camera and add an MRC Video and Audio effect to include virtual holograms and application audio in stills and videos.</span></span>

<span data-ttu-id="f7632-173">응용 프로그램의 효과 추가 하려면 두 가지 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-173">Applications have two options to add the effect:</span></span>
* <span data-ttu-id="f7632-174">이전 API: [Windows.Media.Capture.MediaCapture.AddEffectAsync()](https://msdn.microsoft.com/library/windows/apps/br211961.aspx)</span><span class="sxs-lookup"><span data-stu-id="f7632-174">The older API: [Windows.Media.Capture.MediaCapture.AddEffectAsync()](https://msdn.microsoft.com/library/windows/apps/br211961.aspx)</span></span>
* <span data-ttu-id="f7632-175">새 Microsoft 권장 API (동적 속성을 조작할 수 있도록 하는 개체를 반환한): [Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.addvideoeffectasync.aspx) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.addaudioeffectasync.aspx) 앱 의자체구현을만들필요는[IVideoEffectDefinition](https://msdn.microsoft.com/library/windows/apps/windows.media.effects.ivideoeffectdefinition.aspx) 하 고 [IAudioEffectDefinition](https://msdn.microsoft.com/library/windows/apps/windows.media.effects.iaudioeffectdefinition.aspx)합니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-175">The new Microsoft recommended API (returns an object, making it possible to manipulate dynamic properties): [Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.addvideoeffectasync.aspx) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.addaudioeffectasync.aspx) which require the app create its own implementation of [IVideoEffectDefinition](https://msdn.microsoft.com/library/windows/apps/windows.media.effects.ivideoeffectdefinition.aspx) and [IAudioEffectDefinition](https://msdn.microsoft.com/library/windows/apps/windows.media.effects.iaudioeffectdefinition.aspx).</span></span> <span data-ttu-id="f7632-176">샘플 사용에 대 한 MRC 효과 샘플을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f7632-176">Please see the MRC effect sample for sample usage.</span></span>

<span data-ttu-id="f7632-177">(Visual Studio에서 이러한 네임 스페이스를 인식 되지 것입니다 하지만 문자열을 여전히 유효한 지는 note)</span><span class="sxs-lookup"><span data-stu-id="f7632-177">(Note that these namespaces will not be recognized by Visual Studio, but the strings are still valid)</span></span>

<span data-ttu-id="f7632-178">MRC 비디오 효과 (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)</span><span class="sxs-lookup"><span data-stu-id="f7632-178">MRC Video Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)</span></span>

|  <span data-ttu-id="f7632-179">속성 이름</span><span class="sxs-lookup"><span data-stu-id="f7632-179">Property Name</span></span>  |  <span data-ttu-id="f7632-180">형식</span><span class="sxs-lookup"><span data-stu-id="f7632-180">Type</span></span>  |  <span data-ttu-id="f7632-181">기본값</span><span class="sxs-lookup"><span data-stu-id="f7632-181">Default Value</span></span>  |  <span data-ttu-id="f7632-182">설명</span><span class="sxs-lookup"><span data-stu-id="f7632-182">Description</span></span> | 
|----------|----------|----------|----------|
|  <span data-ttu-id="f7632-183">StreamType</span><span class="sxs-lookup"><span data-stu-id="f7632-183">StreamType</span></span>  |  <span data-ttu-id="f7632-184">UINT32 ([MediaStreamType](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediastreamtype.aspx))</span><span class="sxs-lookup"><span data-stu-id="f7632-184">UINT32 ([MediaStreamType](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediastreamtype.aspx))</span></span>  |  <span data-ttu-id="f7632-185">1 (VideoRecord)</span><span class="sxs-lookup"><span data-stu-id="f7632-185">1 (VideoRecord)</span></span>  |  <span data-ttu-id="f7632-186">이 효과에 사용 되는 캡처 스트림을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-186">Describe which capture stream this effect is used for.</span></span> <span data-ttu-id="f7632-187">오디오를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-187">Audio is not available.</span></span> | 
|  <span data-ttu-id="f7632-188">HologramCompositionEnabled</span><span class="sxs-lookup"><span data-stu-id="f7632-188">HologramCompositionEnabled</span></span>  |  <span data-ttu-id="f7632-189">boolean</span><span class="sxs-lookup"><span data-stu-id="f7632-189">boolean</span></span>  |  <span data-ttu-id="f7632-190">TRUE</span><span class="sxs-lookup"><span data-stu-id="f7632-190">TRUE</span></span>  |  <span data-ttu-id="f7632-191">홀로그램 비디오 캡처에서를 사용 하지 않도록 설정 하거나 사용 하는 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-191">Flag to enable or disable holograms in video capture.</span></span> | 
|  <span data-ttu-id="f7632-192">RecordingIndicatorEnabled</span><span class="sxs-lookup"><span data-stu-id="f7632-192">RecordingIndicatorEnabled</span></span>  |  <span data-ttu-id="f7632-193">boolean</span><span class="sxs-lookup"><span data-stu-id="f7632-193">boolean</span></span>  |  <span data-ttu-id="f7632-194">TRUE</span><span class="sxs-lookup"><span data-stu-id="f7632-194">TRUE</span></span>  |  <span data-ttu-id="f7632-195">홀로그램 캡처 시 화면에서 기록 표시기를 사용할지를 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-195">Flag to enable or disable recording indicator on screen during hologram capturing.</span></span> | 
|  <span data-ttu-id="f7632-196">VideoStabilizationEnabled</span><span class="sxs-lookup"><span data-stu-id="f7632-196">VideoStabilizationEnabled</span></span>  |  <span data-ttu-id="f7632-197">boolean</span><span class="sxs-lookup"><span data-stu-id="f7632-197">boolean</span></span>  |  <span data-ttu-id="f7632-198">FALSE</span><span class="sxs-lookup"><span data-stu-id="f7632-198">FALSE</span></span>  |  <span data-ttu-id="f7632-199">HoloLens 추적기에서 제공 하는 비디오 안정화를 사용할지를 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-199">Flag to enable or disable video stabilization powered by the HoloLens tracker.</span></span> | 
|  <span data-ttu-id="f7632-200">VideoStabilizationBufferLength</span><span class="sxs-lookup"><span data-stu-id="f7632-200">VideoStabilizationBufferLength</span></span>  |  <span data-ttu-id="f7632-201">UINT32</span><span class="sxs-lookup"><span data-stu-id="f7632-201">UINT32</span></span>  |  <span data-ttu-id="f7632-202">0</span><span class="sxs-lookup"><span data-stu-id="f7632-202">0</span></span>  |  <span data-ttu-id="f7632-203">설정 비디오 안정화에 대 한 기록 프레임 수가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-203">Set how many historical frames are used for video stabilization.</span></span> <span data-ttu-id="f7632-204">0 0-대기 시간 및 기능과 성능 측면에서 거의 "무료"입니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-204">0 is 0-latency and nearly "free" from a power and performance perspective.</span></span> <span data-ttu-id="f7632-205">(대기 시간 및 메모리의 15 프레임) 하는 대신 가장 높은 품질에 대 한 15는 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-205">15 is recommended for highest quality (at the cost of 15 frames of latency and memory).</span></span> | 
|  <span data-ttu-id="f7632-206">GlobalOpacityCoefficient</span><span class="sxs-lookup"><span data-stu-id="f7632-206">GlobalOpacityCoefficient</span></span>  |  <span data-ttu-id="f7632-207">FLOAT</span><span class="sxs-lookup"><span data-stu-id="f7632-207">float</span></span>  |  <span data-ttu-id="f7632-208">0.9 (HoloLens) 1.0 (몰입 형 헤드셋)</span><span class="sxs-lookup"><span data-stu-id="f7632-208">0.9 (HoloLens) 1.0 (Immersive headset)</span></span>  |  <span data-ttu-id="f7632-209">홀로그램 전역 불투명도 계수 범위의 (완전히 투명) 0.0에서 1.0으로 설정 (완전 불투명).</span><span class="sxs-lookup"><span data-stu-id="f7632-209">Set global opacity coefficient of hologram in range from 0.0 (fully transparent) to 1.0 (fully opaque).</span></span> | 
|  <span data-ttu-id="f7632-210">BlankOnProtectedContent</span><span class="sxs-lookup"><span data-stu-id="f7632-210">BlankOnProtectedContent</span></span>  |  <span data-ttu-id="f7632-211">boolean</span><span class="sxs-lookup"><span data-stu-id="f7632-211">boolean</span></span>  |  <span data-ttu-id="f7632-212">FALSE</span><span class="sxs-lookup"><span data-stu-id="f7632-212">FALSE</span></span>  |  <span data-ttu-id="f7632-213">활성화 하거나 비활성화는 2d UWP 앱 보여 주는 보호 된 콘텐츠가 있는 경우 빈 프레임을 반환 하는 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-213">Flag to enable or disable returning an empty frame if there is a 2d UWP app showing protected content.</span></span> <span data-ttu-id="f7632-214">이 플래그는 false 및 2d UWP 앱 인지 보여 주는 보호 된 콘텐츠, 혼합된 현실 캡처 모두 헤드셋에 보호 된 콘텐츠 질감 2d UWP 앱 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-214">If this flag is false and a 2d UWP app is showing protected content, the 2d UWP app will be replaced by a protected content texture in both the headset and in the mixed reality capture.</span></span> |
|  <span data-ttu-id="f7632-215">ShowHiddenMesh</span><span class="sxs-lookup"><span data-stu-id="f7632-215">ShowHiddenMesh</span></span>  |  <span data-ttu-id="f7632-216">boolean</span><span class="sxs-lookup"><span data-stu-id="f7632-216">boolean</span></span>  |  <span data-ttu-id="f7632-217">FALSE</span><span class="sxs-lookup"><span data-stu-id="f7632-217">FALSE</span></span>  |  <span data-ttu-id="f7632-218">사용 하도록 설정 하거나 holographic 카메라의 숨겨진된 영역 메시를 표시 하 고 콘텐츠를 인접 하지 않도록 설정 하는 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-218">Flag to enable or disable showing the holographic camera's hidden area mesh and neighboring content.</span></span> |

<span data-ttu-id="f7632-219">MRC 오디오 효과 (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)</span><span class="sxs-lookup"><span data-stu-id="f7632-219">MRC Audio Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)</span></span>

<table>
<tr>
<th><span data-ttu-id="f7632-220">속성 이름</span><span class="sxs-lookup"><span data-stu-id="f7632-220">Property Name</span></span></th>
<th><span data-ttu-id="f7632-221">형식</span><span class="sxs-lookup"><span data-stu-id="f7632-221">Type</span></span></th>
<th><span data-ttu-id="f7632-222">기본값</span><span class="sxs-lookup"><span data-stu-id="f7632-222">Default Value</span></span></th>
<th><span data-ttu-id="f7632-223">설명</span><span class="sxs-lookup"><span data-stu-id="f7632-223">Description</span></span></th>
</tr>
<tr>
<td><span data-ttu-id="f7632-224">MixerMode</span><span class="sxs-lookup"><span data-stu-id="f7632-224">MixerMode</span></span></td>
<td><span data-ttu-id="f7632-225">UINT32</span><span class="sxs-lookup"><span data-stu-id="f7632-225">UINT32</span></span></td>
<td><span data-ttu-id="f7632-226">2</span><span class="sxs-lookup"><span data-stu-id="f7632-226">2</span></span></td>
<td>
<ul>
<li><span data-ttu-id="f7632-227">0 : Mic 오디오 전용</span><span class="sxs-lookup"><span data-stu-id="f7632-227">0 : Mic audio only</span></span></li>
<li><span data-ttu-id="f7632-228">1 : 시스템 오디오 전용</span><span class="sxs-lookup"><span data-stu-id="f7632-228">1 : System audio only</span></span></li>
<li><span data-ttu-id="f7632-229">2 : Mic 및 시스템 오디오</span><span class="sxs-lookup"><span data-stu-id="f7632-229">2 : Mic and System audio</span></span></li>
</ul>
</td>
</tr>
</table>

### <a name="simultaneous-mrc-limitations"></a><span data-ttu-id="f7632-230">동시 MRC 제한 사항</span><span class="sxs-lookup"><span data-stu-id="f7632-230">Simultaneous MRC limitations</span></span>

<span data-ttu-id="f7632-231">MRC 동시에 액세스 하는 여러 앱 주위에 특정 제한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-231">There are certain limitations around multiple apps accessing MRC at the same time.</span></span>

#### <a name="photovideo-camera-access"></a><span data-ttu-id="f7632-232">사진/비디오 카메라 액세스</span><span class="sxs-lookup"><span data-stu-id="f7632-232">Photo/video camera access</span></span>

<span data-ttu-id="f7632-233">사진/비디오 카메라는 동시에 액세스할 수 있는 프로세스 수가 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-233">The photo/video camera is limited to the number of processes that can access it at the same time.</span></span> <span data-ttu-id="f7632-234">프로세스를 기록 하는 동안 사진을 다른 프로세스를 실행 하거나 비디오 사진/비디오 카메라를 획득 하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-234">While a process is recording video or taking a photo any other process will fail to acquire the photo/video camera.</span></span> <span data-ttu-id="f7632-235">(혼합 현실 캡처 및 표준 사진/비디오 캡처를 모두에 적용)</span><span class="sxs-lookup"><span data-stu-id="f7632-235">(this applies to both Mixed Reality Capture and standard photo/video capture)</span></span>

<span data-ttu-id="f7632-236">Windows 10 2018 년 4 월 업데이트를이 제한이 적용 되지 않습니다 경우 기본 제공 MRC 카메라 UI 사진/비디오 카메라를 사용 하 여 앱을 시작한 후 사진 또는 비디오를 만드는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-236">With the Windows 10 April 2018 Update, this restriction does not apply if the built-in MRC camera UI is used to take a photo or a video after an app has started using the photo/video camera.</span></span> <span data-ttu-id="f7632-237">이 경우 기본 값에서 확인 및 기본 제공 MRC 카메라 UI의 프레임 속도 줄어들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-237">When this happens, the resolution and framerate of the built-in MRC camera UI might be reduced from its normal values.</span></span>

<span data-ttu-id="f7632-238">Windows 10 년 10 월 2018 Update이이 제한이 적용 되지 않습니다 MRC Miracast 통한 스트리밍.</span><span class="sxs-lookup"><span data-stu-id="f7632-238">With the Windows 10 October 2018 Update, this restriction does not apply to streaming MRC over Miracast.</span></span>

#### <a name="mrc-access"></a><span data-ttu-id="f7632-239">MRC 액세스</span><span class="sxs-lookup"><span data-stu-id="f7632-239">MRC access</span></span>

<span data-ttu-id="f7632-240">그러나 Windows 10 2018 년 4 월 업데이트를 더 이상 없습니다 (사진/비디오 카메라에 대 한 액세스는 아직 제한) MRC 스트림에 액세스 하는 여러 앱 관련 제한 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-240">With the Windows 10 April 2018 Update, there is no longer a limitation around multiple apps accessing the MRC stream (however, the access to the photo/video camera still has limitations).</span></span>

<span data-ttu-id="f7632-241">Windows 10 2018 년 4 월 이전 MRC 레코더를 사용자 지정 하는 앱의 업데이트 된 시스템 MRC (캡처 사진, 비디오, 캡처링 또는 Windows Device Portal 스트리밍)를 사용 하 여 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f7632-241">Previous to the Windows 10 April 2018 Update, an app's custom MRC recorder was mutually exclusive with system MRC (capturing photos, capturing videos, or streaming from the Windows Device Portal).</span></span>

## <a name="see-also"></a><span data-ttu-id="f7632-242">참조</span><span class="sxs-lookup"><span data-stu-id="f7632-242">See also</span></span>
* [<span data-ttu-id="f7632-243">혼합된 현실 캡처</span><span class="sxs-lookup"><span data-stu-id="f7632-243">Mixed reality capture</span></span>](mixed-reality-capture.md)
* [<span data-ttu-id="f7632-244">Spectator 보기</span><span class="sxs-lookup"><span data-stu-id="f7632-244">Spectator view</span></span>](spectator-view.md)
