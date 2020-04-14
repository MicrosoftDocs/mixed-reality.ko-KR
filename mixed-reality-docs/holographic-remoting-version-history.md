---
title: Holographic 원격 버전 기록
description: HoloLens 2의 Holographic Remoting에 대 한 버전 기록입니다.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens, 원격 서비스, Holographic 원격 작업
ms.openlocfilehash: 5ba3aaa8874dea4418114b331d3d99fc977e982c
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278201"
---
# <a name="holographic-remoting-version-history"></a><span data-ttu-id="685b1-104">Holographic 원격 버전 기록</span><span class="sxs-lookup"><span data-stu-id="685b1-104">Holographic Remoting Version History</span></span>

> [!IMPORTANT]
> <span data-ttu-id="685b1-105">이 지침은 HoloLens 2의 Holographic Remoting에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="685b1-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="version-210-march-11-2020"></a><span data-ttu-id="685b1-106">버전 2.1.0 (2020 년 3 월 11 일)<a name="v2.1.0"></a></span><span class="sxs-lookup"><span data-stu-id="685b1-106">Version 2.1.0 (March 11, 2020) <a name="v2.1.0"></a></span></span>
* <span data-ttu-id="685b1-107">UDP를 통해 [RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) 를 사용 하도록 네트워크 전송을 전환 했습니다.</span><span class="sxs-lookup"><span data-stu-id="685b1-107">Switched network transport to use [RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) via UDP.</span></span> <span data-ttu-id="685b1-108">보안 연결에는 [SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) 가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="685b1-108">Secure connections use [SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) now.</span></span> <span data-ttu-id="685b1-109">[Holographic Remoting Player](holographic-remoting-player.md) 는 이전의 모든 Release Holographic 원격 버전과 여전히 호환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="685b1-109">Note, the [Holographic Remoting Player](holographic-remoting-player.md) is still compatible with all previously release Holographic Remoting versions.</span></span> <span data-ttu-id="685b1-110">새 네트워크 전송을 활용 하려면 Holographic Remoting 플레이어와 해당 원격 앱이 버전 2.1.0을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="685b1-110">To benefit from the new network transport both, the Holographic Remoting Player and the remote app in question, have to use version 2.1.0.</span></span>
* <span data-ttu-id="685b1-111">CommitDirect3D11DepthBuffer에 대 한 지원이 추가 되었습니다. [HolographicCameraRenderingParameters.](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)</span><span class="sxs-lookup"><span data-stu-id="685b1-111">Added support for [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span></span> 

## <a name="version-2020-february-2-2020"></a><span data-ttu-id="685b1-112">버전 2.0.20 이상을 (2 월 2 일, 2020)<a name="v2.0.20"></a></span><span class="sxs-lookup"><span data-stu-id="685b1-112">Version 2.0.20 (February 2, 2020) <a name="v2.0.20"></a></span></span>
* <span data-ttu-id="685b1-113">충돌이 발생할 수 있는 다양 한 버그를 수정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="685b1-113">Fixed various bugs that lead to crashes.</span></span>

## <a name="version-2018-december-17-2019"></a><span data-ttu-id="685b1-114">버전 2.0.18 이상을 (2019 년 12 월 17 일)<a name="v2.0.18"></a></span><span class="sxs-lookup"><span data-stu-id="685b1-114">Version 2.0.18 (December 17, 2019) <a name="v2.0.18"></a></span></span>
* <span data-ttu-id="685b1-115">[HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration) 에 대 한 지원이 추가 됨</span><span class="sxs-lookup"><span data-stu-id="685b1-115">Added support for [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration)</span></span>
* <span data-ttu-id="685b1-116">충돌이 발생할 수 있는 다양 한 버그를 수정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="685b1-116">Fixed various bugs that lead to crashes.</span></span>
* <span data-ttu-id="685b1-117">HolographicCamera를 수락 하 고 HoloraphicFrame에 추가 된 카메라로 표시 하는 데 HolographicSpace. CameraAdded 콜백이 필요한 버그를 수정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="685b1-117">Fixed bug where a HolographicSpace.CameraAdded callback was required for a HolographicCamera to get accepted and show up as added camera in the HoloraphicFrame.</span></span>

## <a name="version-2016-november-11-2019"></a><span data-ttu-id="685b1-118">버전 2.0.16 (2019 년 11 월 11 일)<a name="2.0.16"></a></span><span class="sxs-lookup"><span data-stu-id="685b1-118">Version 2.0.16 (November 11, 2019) <a name="2.0.16"></a></span></span>
* <span data-ttu-id="685b1-119">QR 코드 추적의 교착 상태를 수정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="685b1-119">Fixed deadlock in QR code tracking.</span></span>
* <span data-ttu-id="685b1-120">주 스레드에서 차단 대기로 인해 unhandeled 예외가 수정 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="685b1-120">Fixed unhandeled exception due to blocking wait in main thread.</span></span>

## <a name="version-2014-october-26-2019"></a><span data-ttu-id="685b1-121">버전 2.0.14 (2019 년 10 월 26 일)<a name="v2.0.14"></a></span><span class="sxs-lookup"><span data-stu-id="685b1-121">Version 2.0.14 (October 26, 2019) <a name="v2.0.14"></a></span></span>
* <span data-ttu-id="685b1-122">새 PerceptionDevice Api에 대 한 지원 (Windows 10 11 월 2019 업데이트).</span><span class="sxs-lookup"><span data-stu-id="685b1-122">Support for new PerceptionDevice APIs (Windows 10 November 2019 Update).</span></span>
* <span data-ttu-id="685b1-123">SpatialGestureRecognizer에 의해 트리거되는 고정 제스처 이벤트를 방지 하는 문제를 해결 했습니다.</span><span class="sxs-lookup"><span data-stu-id="685b1-123">Fixed issue which prevent hold gesture events being triggered by SpatialGestureRecognizer.</span></span>
* <span data-ttu-id="685b1-124">SpatialSurfaceObserver. SetBoundingVolume를 사용 하는 경우 스레딩 문제가 수정 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="685b1-124">Fixed threading issue when using SpatialSurfaceObserver.SetBoundingVolume.</span></span>

## <a name="version-2012-october-18-2019"></a><span data-ttu-id="685b1-125">버전 2.0.12 이상을 (2019 년 10 월 18 일)<a name="v2.0.12"></a></span><span class="sxs-lookup"><span data-stu-id="685b1-125">Version 2.0.12 (October 18, 2019) <a name="v2.0.12"></a></span></span>
* <span data-ttu-id="685b1-126">NavigationRail (X/Y/Z)을 사용 하는 경우 SpatialGestureRecognizer의 충돌이 수정 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="685b1-126">Fixed crash in SpatialGestureRecognizer when using NavigationRail(X/Y/Z).</span></span>

## <a name="version-2010-october-10-2019"></a><span data-ttu-id="685b1-127">버전 v2.0.10 (2019 년 10 월 10 일)<a name="v2.0.10"></a></span><span class="sxs-lookup"><span data-stu-id="685b1-127">Version 2.0.10 (October 10, 2019) <a name="v2.0.10"></a></span></span>
* <span data-ttu-id="685b1-128">VR 컨트롤러의 트리거 단추를 사용할 때 충돌이 해결 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="685b1-128">Fixed crash when using trigger button of VR controllers.</span></span> <span data-ttu-id="685b1-129">Holographic Remoting은 컨트롤러를 완전히 지원 하지 않습니다. HoloLens 2와 연결 된 경우에는 트리거 단추와 Windows 단추만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="685b1-129">Holographic Remoting does not fully support controllers, only the trigger button and the Windows button are working if paired with HoloLens 2.</span></span>

## <a name="version-209-september-19-2019"></a><span data-ttu-id="685b1-130">버전 2.0.9 (2019 년 9 월 19 일)<a name="v2.0.9"></a></span><span class="sxs-lookup"><span data-stu-id="685b1-130">Version 2.0.9 (September 19, 2019) <a name="v2.0.9"></a></span></span>
* <span data-ttu-id="685b1-131">[SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter) 에 대 한 지원이 추가 됨</span><span class="sxs-lookup"><span data-stu-id="685b1-131">Added support for [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)</span></span>
* <span data-ttu-id="685b1-132">다음 멤버를 제공 하는 새 인터페이스 ```IPlayerContext2``` (```PlayerContext```에서 구현 됨)를 추가 했습니다.</span><span class="sxs-lookup"><span data-stu-id="685b1-132">Added new interface ```IPlayerContext2``` (implemented by ```PlayerContext```) providing the following members:</span></span>
  - <span data-ttu-id="685b1-133">[BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout) 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="685b1-133">[BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)  property.</span></span>
* <span data-ttu-id="685b1-134">```Failed_RemoteFrameTooOld``` 값이에 추가 되었습니다 ```BlitResult```</span><span class="sxs-lookup"><span data-stu-id="685b1-134">Added ```Failed_RemoteFrameTooOld``` value to ```BlitResult```</span></span>
* <span data-ttu-id="685b1-135">안정성 및 안정성 향상</span><span class="sxs-lookup"><span data-stu-id="685b1-135">Stability and reliability improvements</span></span>

## <a name="version-208-august-20-2019"></a><span data-ttu-id="685b1-136">버전 2.0.8 이상이 필요 (2019 년 8 월 20 일)<a name="v2.0.8"></a></span><span class="sxs-lookup"><span data-stu-id="685b1-136">Version 2.0.8 (August 20, 2019) <a name="v2.0.8"></a></span></span>

* <span data-ttu-id="685b1-137">[IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) 를 매개 변수로 사용 하 여 [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) 를 호출할 때 충돌이 해결 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="685b1-137">Fixed crash when calling [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) with a [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) as parameter.</span></span>
* <span data-ttu-id="685b1-138">안정성 및 안정성 향상</span><span class="sxs-lookup"><span data-stu-id="685b1-138">Stability and reliability improvements</span></span>

## <a name="version-207-july-26-2019"></a><span data-ttu-id="685b1-139">버전 2.0.7 (2019 년 7 월 26 일)<a name="v2.0.7"></a></span><span class="sxs-lookup"><span data-stu-id="685b1-139">Version 2.0.7 (July 26, 2019) <a name="v2.0.7"></a></span></span>

* <span data-ttu-id="685b1-140">HoloLens 2에 대 한 Holographic 원격 작업의 첫 번째 공개 릴리스입니다.</span><span class="sxs-lookup"><span data-stu-id="685b1-140">First public release of Holographic Remoting for HoloLens 2.</span></span>

## <a name="see-also"></a><span data-ttu-id="685b1-141">관련 항목</span><span class="sxs-lookup"><span data-stu-id="685b1-141">See Also</span></span>
* [<span data-ttu-id="685b1-142">사용자 지정 Holographic Remoting 플레이어 앱 작성</span><span class="sxs-lookup"><span data-stu-id="685b1-142">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="685b1-143">Holographic 원격 호스트 앱 작성</span><span class="sxs-lookup"><span data-stu-id="685b1-143">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="685b1-144">Holographic 원격 문제 해결 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="685b1-144">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="685b1-145">홀로그램 원격 소프트웨어 사용 조건</span><span class="sxs-lookup"><span data-stu-id="685b1-145">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="685b1-146">Microsoft 개인 정보 취급 방침</span><span class="sxs-lookup"><span data-stu-id="685b1-146">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
