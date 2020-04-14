---
title: WebVR 개요
description: Windows Mixed Reality에서 WebVR 사용 및 개발 개요
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebVR, WebXR, WinMR, WebAR, web vr, web xr, 웹 mr, 웹 ar, 360, 360 비디오, 360 비디오, 360 photo, 360 사진, 360 콘텐츠, 몰입 형 웹, immersiveweb, IW
ms.openlocfilehash: fdff2acf7816f36129d867650b16d9760a92e375
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278454"
---
# <a name="webvr-overview"></a><span data-ttu-id="a05fe-104">WebVR 개요</span><span class="sxs-lookup"><span data-stu-id="a05fe-104">WebVR Overview</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a05fe-105">**WebVR 1.1 api**는 더 이상 사용 되지 않으며 **WebXR Device api**s로 대체 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a05fe-105">**WebVR 1.1 API**s are deprecated and replaced by **WebXR Device API**s.</span></span>

<span data-ttu-id="a05fe-106">WebVR 1.1 Api는 Chrome 및 새 Microsoft Edge에서 더 이상 사용 되지 않고 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a05fe-106">WebVR 1.1 APIs are deprecated and removed from Chrome and the new Microsoft Edge.</span></span> <span data-ttu-id="a05fe-107">WebVR Api는 WebXR 장치 Api로 대체 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a05fe-107">WebVR APIs are superseded by WebXR Device APIs.</span></span> <span data-ttu-id="a05fe-108">[Caniuse.com](https://caniuse.com/#search=webvr)에서 현재 WebVR api를 지 원하는 브라우저 목록을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a05fe-108">You can check the list of browsers currently supporting WebVR APIs on [caniuse.com](https://caniuse.com/#search=webvr).</span></span>

## <a name="viewing-webvr-content-in-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="a05fe-109">Windows Mixed Reality 모던 헤드셋에서 WebVR 콘텐츠 보기</span><span class="sxs-lookup"><span data-stu-id="a05fe-109">Viewing WebVR content in Windows Mixed Reality immersive headsets</span></span>

<span data-ttu-id="a05fe-110">**이전 버전의 Microsoft Edge (15-18)** 를 사용 하 여 몰입 형 헤드셋의 WebVR 콘텐츠에 액세스 하기 위한 지침은 [열성적인 가이드](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a05fe-110">Instructions for accessing WebVR content in your immersive headsets with **older versions of Microsoft Edge(15-18)** can be found in the [Enthusiast's Guide](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).</span></span> <span data-ttu-id="a05fe-111">Edge 브라우저 검색 창에서 "edge://version/"를 입력 하 여 edge 버전을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a05fe-111">You can check your edge version by typing "edge://version/" in your Edge browsers search bar.</span></span>

## <a name="see-also"></a><span data-ttu-id="a05fe-112">관련 항목</span><span class="sxs-lookup"><span data-stu-id="a05fe-112">See Also</span></span>

* [<span data-ttu-id="a05fe-113">WebXR 개요</span><span class="sxs-lookup"><span data-stu-id="a05fe-113">WebXR Overview</span></span>](webxr-overview.md)
* [<span data-ttu-id="a05fe-114">WebXR 장치 API 사양</span><span class="sxs-lookup"><span data-stu-id="a05fe-114">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="a05fe-115">Windows Mixed Reality 및 새 Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="a05fe-115">Windows Mixed Reality and the new Microsoft Edge</span></span>](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge)
* [<span data-ttu-id="a05fe-116">WebVR 정보</span><span class="sxs-lookup"><span data-stu-id="a05fe-116">WebVR information</span></span>](https://webvr.info)
* [<span data-ttu-id="a05fe-117">WebVR 사양</span><span class="sxs-lookup"><span data-stu-id="a05fe-117">WebVR specification</span></span>](https://w3c.github.io/webvr/)
* <span data-ttu-id="a05fe-118">[WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="a05fe-118">[WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span></span>
* <span data-ttu-id="a05fe-119">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="a05fe-119">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span></span>
* <span data-ttu-id="a05fe-120">[게임 패드 API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) 및 [게임 패드 확장](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="a05fe-120">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="a05fe-121">WebGL에서 손실 된 컨텍스트 처리</span><span class="sxs-lookup"><span data-stu-id="a05fe-121">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="a05fe-122">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="a05fe-122">Pointerlock</span></span>](https://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="a05fe-123">글 Tf</span><span class="sxs-lookup"><span data-stu-id="a05fe-123">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="a05fe-124">Babylon를 사용 하 여 WebVR 사용</span><span class="sxs-lookup"><span data-stu-id="a05fe-124">Using Babylon.js to enable WebVR</span></span>](https://docs.microsoft.com/windows/uwp/get-started/adding-webvr-to-a-babylonjs-game)
