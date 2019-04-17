---
title: Microsoft Edge에서 Windows Mixed Reality WebVR 사용
description: 사용 하 여 및에서 Windows Mixed Reality WebVR 개발 개요
author: YashMaster
ms.author: yabahman
ms.date: 03/21/2018
ms.topic: article
keywords: WebVR, WebXR, WinMR WebAR, vr 웹, xr 하이 웹, mr 웹, ar, 360 웹 360 비디오, 360 비디오, 360 사진, 360 사진, 360 콘텐츠, 몰입 형 웹, immersiveweb, IW
ms.openlocfilehash: fab17f4dcecc34d8f1ca4836dce6de90522899cd
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604637"
---
# <a name="using-webvr-in-microsoft-edge-with-windows-mixed-reality"></a><span data-ttu-id="1d484-104">Microsoft Edge에서 Windows Mixed Reality WebVR 사용</span><span class="sxs-lookup"><span data-stu-id="1d484-104">Using WebVR in Microsoft Edge with Windows Mixed Reality</span></span>

## <a name="creating-webvr-content-for-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="1d484-105">몰입 형 헤드셋 Windows 혼합 현실 용 WebVR 콘텐츠 만들기</span><span class="sxs-lookup"><span data-stu-id="1d484-105">Creating WebVR content for Windows Mixed reality immersive headsets</span></span>

<span data-ttu-id="1d484-106">WebVR 1.1은 Windows 10 Fall Creators Update 시작 하는 Microsoft Edge에서에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d484-106">WebVR 1.1 is available in Microsoft Edge beginning with the Windows 10 Fall Creators Update.</span></span> <span data-ttu-id="1d484-107">개발자는이 API는 웹에서 몰입 형 VR 환경을 만들 수 사용 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d484-107">Developers can now use this API to create immersive VR experiences on the web.</span></span>

<span data-ttu-id="1d484-108">WebVR API는 HMD 돌아가기 스테레오 WebGL 장면 렌더링을 사용할 수 있는 페이지로 HMD 포즈 데이터를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d484-108">The WebVR API provides HMD pose data to the page which can be used to render a stereo WebGL scene back to the HMD.</span></span> <span data-ttu-id="1d484-109">API 지원에 대 한 세부 정보에서 사용할 수는 [Microsoft Edge 플랫폼 상태 페이지](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/)합니다.</span><span class="sxs-lookup"><span data-stu-id="1d484-109">Details on API support is available on the [Microsoft Edge Platform Status page](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/).</span></span> <span data-ttu-id="1d484-110">WebVR API 노출 영역이 항상 Microsoft Edge 내에 없는 경우</span><span class="sxs-lookup"><span data-stu-id="1d484-110">The WebVR API surface area is present at all times within Microsoft Edge.</span></span> <span data-ttu-id="1d484-111">그러나 getVRDisplays() 호출 반환 됩니다 헤드셋 헤드셋 전원을 이거나 시뮬레이터 켜 졌습니다.</span><span class="sxs-lookup"><span data-stu-id="1d484-111">However, a call to getVRDisplays() will only return a headset if either a headset is plugged in or the simulator has been turned on.</span></span>

## <a name="viewing-webvr-content-in-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="1d484-112">Windows Mixed Reality 몰입 형 헤드셋에서 WebVR 콘텐츠 보기</span><span class="sxs-lookup"><span data-stu-id="1d484-112">Viewing WebVR content in Windows Mixed Reality immersive headsets</span></span>

<span data-ttu-id="1d484-113">몰입 형 헤드셋 WebVR 콘텐츠에 액세스 하기 위한 지침을 찾을 수 있습니다 합니다 [열성적인의 가이드](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr)합니다.</span><span class="sxs-lookup"><span data-stu-id="1d484-113">Instructions for accessing WebVR content in your immersive headset can be found in the [Enthusiast's Guide](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).</span></span>

## <a name="see-also"></a><span data-ttu-id="1d484-114">관련 항목</span><span class="sxs-lookup"><span data-stu-id="1d484-114">See Also</span></span>
* [<span data-ttu-id="1d484-115">WebVR 정보</span><span class="sxs-lookup"><span data-stu-id="1d484-115">WebVR information</span></span>](http://webvr.info)
* [<span data-ttu-id="1d484-116">WebVR 사양</span><span class="sxs-lookup"><span data-stu-id="1d484-116">WebVR specification</span></span>](https://w3c.github.io/webvr/)
* <span data-ttu-id="1d484-117">[WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="1d484-117">[WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span></span>
* <span data-ttu-id="1d484-118">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="1d484-118">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span></span>
* <span data-ttu-id="1d484-119">[API Gamepad](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) 고 [확장 Gamepad](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="1d484-119">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="1d484-120">WebGL 컨텍스트에서 손실 처리</span><span class="sxs-lookup"><span data-stu-id="1d484-120">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="1d484-121">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="1d484-121">Pointerlock</span></span>](http://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="1d484-122">glTF</span><span class="sxs-lookup"><span data-stu-id="1d484-122">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="1d484-123">Babylon.js를 지 원하는 WebVR를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="1d484-123">Using Babylon.js to enable WebVR</span></span>](https://docs.microsoft.com/windows/uwp/get-started/adding-webvr-to-a-babylonjs-game)

