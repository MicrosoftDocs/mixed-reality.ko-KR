---
title: JavaScript Mixed Reality 개발 개요
description: 웹, 모바일 및 windows 모던 헤드셋을 위한 JavaScript를 사용한 혼합 현실 개발 개요입니다.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR, WinMR, WebAR, WebVR, WindowsMixedReality, HoloLens, windows mixed reality, 웹 vr, 웹 xr, 웹 mr, 웹 ar, 360, 360 비디오, 360 비디오, 360 photo, 360 사진, 360 콘텐츠, 몰입 형 웹, 몰입 형 웹, IW, immersiveweb
ms.openlocfilehash: a1288e8f477f42b0937e797623fb83fe8f63685c
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835612"
---
# <a name="mixed-reality-development-with-javascript-overview"></a><span data-ttu-id="f0974-104">JavaScript를 사용한 혼합 현실 개발 개요</span><span class="sxs-lookup"><span data-stu-id="f0974-104">Mixed Reality Development with JavaScript Overview</span></span>

## <a name="mixed-reality-applications-on-the-web"></a><span data-ttu-id="f0974-105">웹의 혼합 현실 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="f0974-105">Mixed Reality applications on the web</span></span>

<span data-ttu-id="f0974-106">혼합 현실 기능은 [WebXR 장치 api](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API) 를 사용 하 고 [더 이상 사용 되지 않는 WebVR api](webxr-overview.md)를 사용 하 여 웹에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0974-106">Mixed Reality features are available on the web by the use of [WebXR Device APIs](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API) and [deprecated WebVR APIs](webxr-overview.md).</span></span> <span data-ttu-id="f0974-107">전체 WebXR 기능을 지원 하지 않는 브라우저의 경우 [WebXR Polyfills](https://github.com/immersive-web/webxr-polyfill) 를 웹 사이트에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0974-107">For browsers that do not support full WebXR features, you can add [WebXR Polyfills](https://github.com/immersive-web/webxr-polyfill) to your website.</span></span>

## <a name="what-is-webxr-polyfill"></a><span data-ttu-id="f0974-108">WebXR Safehtml 이란?</span><span class="sxs-lookup"><span data-stu-id="f0974-108">What is WebXR Polyfill</span></span>

<span data-ttu-id="f0974-109">WebXR 게임 패드 모듈 뿐만 아니라 WebXR 장치 API의 JavaScript 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="f0974-109">A JavaScript implementation of the WebXR Device API, as well as the WebXR Gamepad Module.</span></span> <span data-ttu-id="f0974-110">이 safehtml를 통해 개발자는 WebVR 1.1 사양을 구현 하는 브라우저에서 또는 WebVR/WebXR를 지원 하지 않는 모바일 장치에서 실행할 때 지원을 제공 하 여 최신 사양에 대해 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0974-110">This polyfill allows developers to write against the latest specification, providing support when run on browsers that implement the WebVR 1.1 spec, or on mobile devices with no WebVR/WebXR support at all.</span></span>

## <a name="javascript-libraries-to-build-mixed-reality-applications-on-the-web"></a><span data-ttu-id="f0974-111">웹에서 혼합 현실 응용 프로그램을 빌드하기 위한 JavaScript 라이브러리</span><span class="sxs-lookup"><span data-stu-id="f0974-111">JavaScript libraries to build Mixed Reality applications on the web</span></span>

## <a name="babylonjs"></a><span data-ttu-id="f0974-112">Babylon</span><span class="sxs-lookup"><span data-stu-id="f0974-112">Babylon.js</span></span>

<span data-ttu-id="f0974-113">Babylon는 3D 콘텐츠 및 몰입 형 응용 프로그램을 쉽게 개발할 수 있도록 하는 JavaScript 3D 엔진입니다.</span><span class="sxs-lookup"><span data-stu-id="f0974-113">Babylon is a JavaScript 3D engine that makes developing 3D content and immersive applications easy.</span></span> <span data-ttu-id="f0974-114">몰입 형 응용 프로그램을 시작 하기 전에 Babylon 개발의 기본 사항에 대해 알아보는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f0974-114">Before getting started with immersive applications, we recommend to learn the basics of Babylon.js development.</span></span>

<span data-ttu-id="f0974-115">[시작 섹션](https://doc.babylonjs.com/)에서 Babylon를 사용 하 여 혼합 현실 응용 프로그램을 빌드하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="f0974-115">Learn how to build a mixed reality application with Babylon in the [getting started section](https://doc.babylonjs.com/).</span></span> <span data-ttu-id="f0974-116">[Babylon 필드](https://doc.babylonjs.com/examples/)를 사용 하 여 3d 예제와 해당 소스 코드를 재생 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0974-116">Play with 3D examples and their source code using [Babylon Playground](https://doc.babylonjs.com/examples/).</span></span> <span data-ttu-id="f0974-117">설명서의 [WebXR 섹션](https://doc.babylonjs.com/how_to/introduction_to_webxr) 에서 혼합 현실 개발에 대해 자세히 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="f0974-117">Dive into mixed reality development on the [WebXR section](https://doc.babylonjs.com/how_to/introduction_to_webxr) of the documentation.</span></span> 

## <a name="a-frame"></a><span data-ttu-id="f0974-118">A-프레임</span><span class="sxs-lookup"><span data-stu-id="f0974-118">A-Frame</span></span>

<span data-ttu-id="f0974-119">A-프레임은 웹에서 가상 현실를 시작 하기 위한 선언적 JavaScript 프레임 워크입니다.</span><span class="sxs-lookup"><span data-stu-id="f0974-119">A-frame is a declarative JavaScript framework to get started with Virtual Reality in the web.</span></span> <span data-ttu-id="f0974-120">자세한 내용은 [프레임 설명서](https://aframe.io/) 를 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="f0974-120">Check out the [A-Frame documentation](https://aframe.io/) to learn more.</span></span>

## <a name="threejs"></a><span data-ttu-id="f0974-121">3 개 .js</span><span class="sxs-lookup"><span data-stu-id="f0974-121">Three.js</span></span>

<span data-ttu-id="f0974-122">세 .js는 몰입 형 환경을 만들기 위한 인기 있는 3D 라이브러리입니다.</span><span class="sxs-lookup"><span data-stu-id="f0974-122">Three.js is a popular 3D library for creating immersive experiences.</span></span> <span data-ttu-id="f0974-123">설명서 페이지 및 [예제](https://threejs.org/examples/#webgl_animation_cloth)를 참조 하 여 [세 개의 .js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) 에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="f0974-123">Learn more about [three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) in documentation page and by exploring [examples](https://threejs.org/examples/#webgl_animation_cloth).</span></span>

## <a name="webgl"></a><span data-ttu-id="f0974-124">WebGL</span><span class="sxs-lookup"><span data-stu-id="f0974-124">WebGL</span></span>

<span data-ttu-id="f0974-125">WebGL Api를 사용 하 여 WebXR 장치 Api에 직접 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0974-125">You can access the WebXR Device APIs directly by using WebGL APIs.</span></span> <span data-ttu-id="f0974-126">WebGL (웹 그래픽 라이브러리)는 플러그 인을 사용 하지 않고 호환 되는 웹 브라우저 내에서 고성능 대화형 3D 및 2D 그래픽을 렌더링 하기 위한 JavaScript API입니다. [WebGL api](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="f0974-126">WebGL (Web Graphics Library) is a JavaScript API for rendering high-performance interactive 3D and 2D graphics within any compatible web browser without the use of plug-ins. Learn more about the [WebGL APIs](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API).</span></span>

## <a name="mixed-reality-native-mobile-applications-using-javascript"></a><span data-ttu-id="f0974-127">JavaScript를 사용 하는 혼합 현실 네이티브 모바일 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="f0974-127">Mixed Reality native mobile applications using JavaScript</span></span>

<span data-ttu-id="f0974-128">몇 가지 JavaScript 라이브러리를 사용 하 여 혼합 현실 환경을 한 번 작성 하 고이를 웹 및 Windows Mixed Reality 헤드셋, Android 및 iOS 장치와 같은 네이티브 플랫폼에 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0974-128">With the help of few JavaScript libraries you can write your mixed reality experiences once and deploy it to web and to native platforms like Windows Mixed Reality headsets, Android and iOS devices.</span></span>

## <a name="babylon-native"></a><span data-ttu-id="f0974-129">Babylon 네이티브</span><span class="sxs-lookup"><span data-stu-id="f0974-129">Babylon Native</span></span>

<span data-ttu-id="f0974-130">[Babylon native](https://www.babylonjs.com/native/) platform을 사용 하면 누구나 Babylon 코드를 사용 하 여 네이티브 응용 프로그램을 빌드하고 네이티브 기술의 기능을 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0974-130">[Babylon Native](https://www.babylonjs.com/native/) platform allows anyone to take their Babylon.js code and build a native application with it, unlocking the power of native technologies.</span></span> <span data-ttu-id="f0974-131">[Github에서 Babylon native](https://github.com/BabylonJS/BabylonNative) 를 다운로드 하 고 [Babylon 블로그에서](https://medium.com/@babylonjs/babylon-native-821f1694fffc)자세히 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0974-131">You can download [Babylon native on github](https://github.com/BabylonJS/BabylonNative) and read more about it on [Babylon.js blog](https://medium.com/@babylonjs/babylon-native-821f1694fffc).</span></span>

## <a name="react-native"></a><span data-ttu-id="f0974-132">React Native</span><span class="sxs-lookup"><span data-stu-id="f0974-132">React Native</span></span>

<span data-ttu-id="f0974-133">[네이티브에 반응](https://reactnative.dev/) 하는 것은 개발자가 JavaScript를 사용 하 여 빌드하고 여러 플랫폼에 배포할 수 있도록 하는 또 다른 오픈 소스 라이브러리입니다.</span><span class="sxs-lookup"><span data-stu-id="f0974-133">[React Native](https://reactnative.dev/) is another open source library that allows developers to build using JavaScript and deploy to multiple platforms.</span></span> <span data-ttu-id="f0974-134">[Github의 기본에](https://github.com/facebook/react-native) 대 한 응답을 다운로드 하 고 [네이티브 블로그 반응](https://reactnative.dev/blog/)에서 자세히 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0974-134">You can download [React Native on Github](https://github.com/facebook/react-native) and learn more about it in [React Native Blog](https://reactnative.dev/blog/).</span></span>

## <a name="see-also"></a><span data-ttu-id="f0974-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f0974-135">See Also</span></span>

* [<span data-ttu-id="f0974-136">WebXR 개요</span><span class="sxs-lookup"><span data-stu-id="f0974-136">WebXR Overview</span></span>](webxr-overview.md)
* [<span data-ttu-id="f0974-137">WebXR 장치 API 사양</span><span class="sxs-lookup"><span data-stu-id="f0974-137">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="f0974-138">WebXR 장치 API 설명서</span><span class="sxs-lookup"><span data-stu-id="f0974-138">WebXR Device API documentation</span></span>](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [<span data-ttu-id="f0974-139">Immersiveweb</span><span class="sxs-lookup"><span data-stu-id="f0974-139">Immersiveweb.dev</span></span>](https://immersiveweb.dev/)
* [<span data-ttu-id="f0974-140">WebXR 샘플</span><span class="sxs-lookup"><span data-stu-id="f0974-140">WebXR Samples</span></span>](https://immersive-web.github.io/webxr-samples/)
* [<span data-ttu-id="f0974-141">Babylon를 사용 하 여 WebXR 환경 만들기</span><span class="sxs-lookup"><span data-stu-id="f0974-141">Using Babylon.js to create WebXR experiences</span></span>](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [<span data-ttu-id="f0974-142">Windows Mixed Reality 및 새 Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="f0974-142">Windows Mixed Reality and the new Microsoft Edge</span></span>](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [<span data-ttu-id="f0974-143">몰입 형 Web W3C Github</span><span class="sxs-lookup"><span data-stu-id="f0974-143">Immersive Web W3C Github</span></span>](https://github.com/immersive-web)
* <span data-ttu-id="f0974-144">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="f0974-144">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span></span>
* <span data-ttu-id="f0974-145">[게임 패드 API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) 및 [게임 패드 확장](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="f0974-145">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="f0974-146">WebVR 개요</span><span class="sxs-lookup"><span data-stu-id="f0974-146">WebVR Overview</span></span>](webvr-overview.md)
