---
title: Holographic 원격 버전 기록
description: HoloLens 2의 Holographic Remoting에 대 한 버전 기록입니다.
author: NPohl-MSFT
ms.author: nopohl
ms.date: 10/21/2019
ms.topic: article
keywords: HoloLens, 원격 서비스, Holographic 원격 작업
ms.openlocfilehash: 9ff6a5f7594eb67dd4c1c8690812ab724cac9012
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926646"
---
# <a name="holographic-remoting-version-history"></a><span data-ttu-id="6176f-104">Holographic 원격 버전 기록</span><span class="sxs-lookup"><span data-stu-id="6176f-104">Holographic Remoting Version History</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6176f-105">이 지침은 HoloLens 2의 Holographic Remoting에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6176f-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <span data-ttu-id="6176f-106">버전 2.0.14 (2019 년 10 월 26 일)<a name="v2.0.14"></a></span><span class="sxs-lookup"><span data-stu-id="6176f-106">Version 2.0.14 (October 26, 2019) <a name="v2.0.14"></a></span></span>
* <span data-ttu-id="6176f-107">새 PerceptionDevice Api에 대 한 지원 (Windows 10 11 월 2019 업데이트).</span><span class="sxs-lookup"><span data-stu-id="6176f-107">Support for new PerceptionDevice APIs (Windows 10 November 2019 Update).</span></span>
* <span data-ttu-id="6176f-108">SpatialGestureRecognizer에 의해 트리거되는 고정 제스처 이벤트를 방지 하는 문제를 해결 했습니다.</span><span class="sxs-lookup"><span data-stu-id="6176f-108">Fixed issue which prevent hold gesture events being triggered by SpatialGestureRecognizer.</span></span>
* <span data-ttu-id="6176f-109">SpatialSurfaceObserver. SetBoundingVolume를 사용 하는 경우 스레딩 문제가 수정 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6176f-109">Fixed threading issue when using SpatialSurfaceObserver.SetBoundingVolume.</span></span>

## <span data-ttu-id="6176f-110">버전 2.0.12 이상을 (2019 년 10 월 18 일)<a name="v2.0.12"></a></span><span class="sxs-lookup"><span data-stu-id="6176f-110">Version 2.0.12 (October 18, 2019) <a name="v2.0.12"></a></span></span>
* <span data-ttu-id="6176f-111">NavigationRail (X/Y/Z)을 사용 하는 경우 SpatialGestureRecognizer의 충돌이 수정 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6176f-111">Fixed crash in SpatialGestureRecognizer when using NavigationRail(X/Y/Z).</span></span>

## <span data-ttu-id="6176f-112">버전 v2.0.10 (2019 년 10 월 10 일)<a name="v2.0.10"></a></span><span class="sxs-lookup"><span data-stu-id="6176f-112">Version 2.0.10 (October 10, 2019) <a name="v2.0.10"></a></span></span>
* <span data-ttu-id="6176f-113">VR 컨트롤러의 트리거 단추를 사용할 때 충돌이 해결 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6176f-113">Fixed crash when using trigger button of VR controllers.</span></span> <span data-ttu-id="6176f-114">Holographic Remoting은 컨트롤러를 완전히 지원 하지 않습니다. HoloLens 2와 연결 된 경우에는 트리거 단추와 Windows 단추만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="6176f-114">Holographic Remoting does not fully support controllers, only the trigger button and the Windows button are working if paired with HoloLens 2.</span></span>

## <span data-ttu-id="6176f-115">버전 2.0.9 (2019 년 9 월 19 일)<a name="v2.0.9"></a></span><span class="sxs-lookup"><span data-stu-id="6176f-115">Version 2.0.9 (September 19, 2019) <a name="v2.0.9"></a></span></span>
* <span data-ttu-id="6176f-116">[SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter) 에 대 한 지원이 추가 됨</span><span class="sxs-lookup"><span data-stu-id="6176f-116">Added support for [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)</span></span>
* <span data-ttu-id="6176f-117">다음 멤버를 제공 하는 새 인터페이스 ```IPlayerContext2``` (```PlayerContext```에서 구현 됨)를 추가 했습니다.</span><span class="sxs-lookup"><span data-stu-id="6176f-117">Added new interface ```IPlayerContext2``` (implemented by ```PlayerContext```) providing the following members:</span></span>
  - <span data-ttu-id="6176f-118">[BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout) 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="6176f-118">[BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)  property.</span></span>
* <span data-ttu-id="6176f-119">```Failed_RemoteFrameTooOld``` 값이에 추가 되었습니다 ```BlitResult```</span><span class="sxs-lookup"><span data-stu-id="6176f-119">Added ```Failed_RemoteFrameTooOld``` value to ```BlitResult```</span></span>
* <span data-ttu-id="6176f-120">안정성 및 안정성 향상</span><span class="sxs-lookup"><span data-stu-id="6176f-120">Stability and reliability improvements</span></span>

## <span data-ttu-id="6176f-121">버전 2.0.8 이상이 필요 (2019 년 8 월 20 일)<a name="v2.0.8"></a></span><span class="sxs-lookup"><span data-stu-id="6176f-121">Version 2.0.8 (August 20, 2019) <a name="v2.0.8"></a></span></span>

* <span data-ttu-id="6176f-122">[IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) 를 매개 변수로 사용 하 여 [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) 를 호출할 때 충돌이 해결 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6176f-122">Fixed crash when calling [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) with a [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) as parameter.</span></span>
* <span data-ttu-id="6176f-123">안정성 및 안정성 향상</span><span class="sxs-lookup"><span data-stu-id="6176f-123">Stability and reliability improvements</span></span>

## <span data-ttu-id="6176f-124">버전 2.0.7 (2019 년 7 월 26 일)<a name="v2.0.7"></a></span><span class="sxs-lookup"><span data-stu-id="6176f-124">Version 2.0.7 (July 26, 2019) <a name="v2.0.7"></a></span></span>

* <span data-ttu-id="6176f-125">HoloLens 2에 대 한 Holographic 원격 작업의 첫 번째 공개 릴리스입니다.</span><span class="sxs-lookup"><span data-stu-id="6176f-125">First public release of Holographic Remoting for HoloLens 2.</span></span>

## <a name="see-also"></a><span data-ttu-id="6176f-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6176f-126">See Also</span></span>
* [<span data-ttu-id="6176f-127">사용자 지정 Holographic Remoting 플레이어 앱 작성</span><span class="sxs-lookup"><span data-stu-id="6176f-127">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="6176f-128">Holographic 원격 호스트 앱 작성</span><span class="sxs-lookup"><span data-stu-id="6176f-128">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="6176f-129">Holographic 원격 문제 해결 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="6176f-129">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="6176f-130">홀로그램 원격 소프트웨어 사용 조건</span><span class="sxs-lookup"><span data-stu-id="6176f-130">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="6176f-131">Microsoft 개인 정보 취급 방침</span><span class="sxs-lookup"><span data-stu-id="6176f-131">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
