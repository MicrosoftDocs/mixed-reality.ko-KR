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
# <a name="mixed-reality-development-with-javascript-overview"></a>JavaScript를 사용한 혼합 현실 개발 개요

## <a name="mixed-reality-applications-on-the-web"></a>웹의 혼합 현실 응용 프로그램

혼합 현실 기능은 [WebXR 장치 api](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API) 를 사용 하 고 [더 이상 사용 되지 않는 WebVR api](webxr-overview.md)를 사용 하 여 웹에서 사용할 수 있습니다. 전체 WebXR 기능을 지원 하지 않는 브라우저의 경우 [WebXR Polyfills](https://github.com/immersive-web/webxr-polyfill) 를 웹 사이트에 추가할 수 있습니다.

## <a name="what-is-webxr-polyfill"></a>WebXR Safehtml 이란?

WebXR 게임 패드 모듈 뿐만 아니라 WebXR 장치 API의 JavaScript 구현입니다. 이 safehtml를 통해 개발자는 WebVR 1.1 사양을 구현 하는 브라우저에서 또는 WebVR/WebXR를 지원 하지 않는 모바일 장치에서 실행할 때 지원을 제공 하 여 최신 사양에 대해 작성할 수 있습니다.

## <a name="javascript-libraries-to-build-mixed-reality-applications-on-the-web"></a>웹에서 혼합 현실 응용 프로그램을 빌드하기 위한 JavaScript 라이브러리

## <a name="babylonjs"></a>Babylon

Babylon는 3D 콘텐츠 및 몰입 형 응용 프로그램을 쉽게 개발할 수 있도록 하는 JavaScript 3D 엔진입니다. 몰입 형 응용 프로그램을 시작 하기 전에 Babylon 개발의 기본 사항에 대해 알아보는 것이 좋습니다.

[시작 섹션](https://doc.babylonjs.com/)에서 Babylon를 사용 하 여 혼합 현실 응용 프로그램을 빌드하는 방법에 대해 알아봅니다. [Babylon 필드](https://doc.babylonjs.com/examples/)를 사용 하 여 3d 예제와 해당 소스 코드를 재생 합니다. 설명서의 [WebXR 섹션](https://doc.babylonjs.com/how_to/introduction_to_webxr) 에서 혼합 현실 개발에 대해 자세히 알아봅니다. 

## <a name="a-frame"></a>A-프레임

A-프레임은 웹에서 가상 현실를 시작 하기 위한 선언적 JavaScript 프레임 워크입니다. 자세한 내용은 [프레임 설명서](https://aframe.io/) 를 확인 하세요.

## <a name="threejs"></a>3 개 .js

세 .js는 몰입 형 환경을 만들기 위한 인기 있는 3D 라이브러리입니다. 설명서 페이지 및 [예제](https://threejs.org/examples/#webgl_animation_cloth)를 참조 하 여 [세 개의 .js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) 에 대해 자세히 알아보세요.

## <a name="webgl"></a>WebGL

WebGL Api를 사용 하 여 WebXR 장치 Api에 직접 액세스할 수 있습니다. WebGL (웹 그래픽 라이브러리)는 플러그 인을 사용 하지 않고 호환 되는 웹 브라우저 내에서 고성능 대화형 3D 및 2D 그래픽을 렌더링 하기 위한 JavaScript API입니다. [WebGL api](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)에 대해 자세히 알아보세요.

## <a name="mixed-reality-native-mobile-applications-using-javascript"></a>JavaScript를 사용 하는 혼합 현실 네이티브 모바일 응용 프로그램

몇 가지 JavaScript 라이브러리를 사용 하 여 혼합 현실 환경을 한 번 작성 하 고이를 웹 및 Windows Mixed Reality 헤드셋, Android 및 iOS 장치와 같은 네이티브 플랫폼에 배포할 수 있습니다.

## <a name="babylon-native"></a>Babylon 네이티브

[Babylon native](https://www.babylonjs.com/native/) platform을 사용 하면 누구나 Babylon 코드를 사용 하 여 네이티브 응용 프로그램을 빌드하고 네이티브 기술의 기능을 해제할 수 있습니다. [Github에서 Babylon native](https://github.com/BabylonJS/BabylonNative) 를 다운로드 하 고 [Babylon 블로그에서](https://medium.com/@babylonjs/babylon-native-821f1694fffc)자세히 읽을 수 있습니다.

## <a name="react-native"></a>React Native

[네이티브에 반응](https://reactnative.dev/) 하는 것은 개발자가 JavaScript를 사용 하 여 빌드하고 여러 플랫폼에 배포할 수 있도록 하는 또 다른 오픈 소스 라이브러리입니다. [Github의 기본에](https://github.com/facebook/react-native) 대 한 응답을 다운로드 하 고 [네이티브 블로그 반응](https://reactnative.dev/blog/)에서 자세히 알아볼 수 있습니다.

## <a name="see-also"></a>참고 항목

* [WebXR 개요](webxr-overview.md)
* [WebXR 장치 API 사양](https://immersive-web.github.io/webxr/)
* [WebXR 장치 API 설명서](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [Immersiveweb](https://immersiveweb.dev/)
* [WebXR 샘플](https://immersive-web.github.io/webxr-samples/)
* [Babylon를 사용 하 여 WebXR 환경 만들기](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [Windows Mixed Reality 및 새 Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [몰입 형 Web W3C Github](https://github.com/immersive-web)
* [WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)
* [게임 패드 API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) 및 [게임 패드 확장](https://w3c.github.io/gamepad/extensions.html)
* [WebVR 개요](webvr-overview.md)
