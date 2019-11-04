---
title: Windows Mixed Reality와 함께 Microsoft Edge에서 WebVR 사용
description: Windows Mixed Reality에서 WebVR 사용 및 개발 개요
author: YashMaster
ms.author: yabahman
ms.date: 03/21/2018
ms.topic: article
keywords: WebVR, WebXR, WinMR, WebAR, web vr, web xr, 웹 mr, 웹 ar, 360, 360 비디오, 360 비디오, 360 photo, 360 사진, 360 콘텐츠, 몰입 형 웹, immersiveweb, IW
ms.openlocfilehash: 87805d2c40e9e63cdf3e432189b9deb7d575a380
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437208"
---
# <a name="using-webvr-in-microsoft-edge-with-windows-mixed-reality"></a>Windows Mixed Reality와 함께 Microsoft Edge에서 WebVR 사용

## <a name="creating-webvr-content-for-windows-mixed-reality-immersive-headsets"></a>Windows Mixed reality 모던 헤드셋에 대 한 WebVR 콘텐츠 만들기

WebVR 1.1은 Microsoft Edge에서 Windows 10이 하 버전의 작성자 업데이트부터 사용할 수 있습니다. 이제 개발자는이 API를 사용 하 여 웹에서 모던 VR 환경을 만들 수 있습니다.

WebVR API는 스테레오 WebGL 장면을 HMD로 다시 렌더링 하는 데 사용할 수 있는 페이지에 HMD 포즈 데이터를 제공 합니다. API 지원에 대 한 자세한 내용은 [Microsoft Edge Platform 상태 페이지](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/)에서 확인할 수 있습니다. WebVR API 노출 영역은 Microsoft Edge 내에서 항상 제공 됩니다. 그러나 getVRDisplays ()를 호출 하면 헤드셋이 연결 되어 있거나 시뮬레이터가 설정 된 경우에만 헤드셋을 반환 합니다.

## <a name="viewing-webvr-content-in-windows-mixed-reality-immersive-headsets"></a>Windows Mixed Reality 모던 헤드셋에서 WebVR 콘텐츠 보기

모던 헤드셋의 WebVR 콘텐츠에 액세스 하기 위한 지침은 [열성적인 'S Guide](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr)(영문)에서 찾을 수 있습니다.

## <a name="see-also"></a>참고 항목
* [WebVR 정보](https://webvr.info)
* [WebVR 사양](https://w3c.github.io/webvr/)
* [WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)
* [WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)
* [게임 패드 API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) 및 [게임 패드 확장](https://w3c.github.io/gamepad/extensions.html)
* [WebGL에서 손실 된 컨텍스트 처리](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [Pointerlock](https://www.w3.org/TR/pointerlock/)
* [글 Tf](https://www.khronos.org/gltf)
* [Babylon를 사용 하 여 WebVR 사용](https://docs.microsoft.com/windows/uwp/get-started/adding-webvr-to-a-babylonjs-game)

