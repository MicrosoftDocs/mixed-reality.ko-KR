---
title: OpenXR
description: 이식 가능한 OpenXR API 표준을 사용 하 여 엔진을 빌드하고 Windows Mixed Reality 및 HoloLens 2 헤드셋에 배포 합니다.
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, Mixed Reality OpenXR Developer Portal, DirectX, 네이티브, 네이티브 앱 사용자 지정 엔진, 미들웨어
ms.openlocfilehash: 67d2ab42a40aa04eb9dcd6881a4392a81c0f3b8f
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/11/2019
ms.locfileid: "73914388"
---
# <a name="openxr"></a>OpenXR

OpenXR는 [혼합 현실 스펙트럼](mixed-reality.md)에 걸쳐 있는 많은 공급 업체의 다양 한 장치에 대 한 기본 액세스를 엔진에 제공 하는 <a href="https://www.khronos.org/" target="_blank">Khronos</a> 의 오픈 로열티 없는 무료 API 표준입니다.

OpenXR를 사용 하 여 개발할 수 있습니다는 HoloLens 2 또는 Windows Mixed Reality 모던 헤드셋 바탕 화면입니다.  헤드셋에 액세스할 수 없는 경우 HoloLens 2 에뮬레이터 또는 Windows Mixed Reality 시뮬레이터를 대신 사용할 수 있습니다.

## <a name="why-openxr"></a>왜 OpenXR?

OpenXR를 사용 하면 실제 환경에서 디지털 콘텐츠를 포함 하는 두 holographic 장치 (예: HoloLens 2)를 대상으로 하는 엔진을 빌드할 수 있습니다. 이러한 장치는 물리적 콘텐츠를 숨기는 몰입 형 장치 (예: 데스크톱 Pc의 경우 Windows Mixed Reality 헤드셋) 뿐 아니라 전 세계에서 디지털 환경으로 대체 합니다.  OpenXR를 사용 하면 다양 한 하드웨어 플랫폼에서 이식할 수 있는 코드를 작성할 수 있습니다.

OpenXR API는 응용 프로그램을 헤드셋의 기본 플랫폼 지원에 직접 연결 하는 로더를 사용 합니다.  이는 Windows Mixed Reality 헤드셋 또는 다른 헤드셋을 사용 하는지 여부에 관계 없이 최종 사용자에 게 최대 성능 및 최소 대기 시간을 제공 합니다.

## <a name="what-is-openxr"></a>OpenXR 란?

핵심 OpenXR 1.0 API는 HoloLens 2와 같은 holographic 장치 및 Windows Mixed Reality 헤드셋 같은 몰입 형 장치를 모두 대상으로 지정할 수 있는 엔진을 빌드하는 데 필요한 기본 기능을 제공 합니다.
* 시스템 + 세션
* 참조 공간 (보기, 로컬, 단계)
* 구성 보기 (mono, 스테레오)
* Swapchains + 프레임 타이밍
* 컴포지션 계층
* Input 및 haptics
* 그래픽 API + 플랫폼 통합

OpenXR API에 대 한 자세한 내용은 OpenXR 1.0 <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">사양</a>, <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">API 참조</a> 및 <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">빠른 참조 가이드</a>를 확인 하세요.  자세한 내용은 <a href="https://www.khronos.org/openxr/" target="_blank">Khronos OpenXR 페이지</a>를 참조 하세요.

HoloLens 2의 전체 기능 집합을 대상으로 지정 하려면 트레일러 추적, 눈 추적, 공간 매핑 및 공간 앵커와 같이 OpenXR 1.0 코어 이외의 추가 기능을 사용할 수 있도록 하는 공급 업체 및 공급 업체별 OpenXR 확장을 사용 합니다.  올해 후반에 제공 되는 확장에 대 한 자세한 내용은 아래의 [로드맵 섹션](openxr.md#roadmap) 섹션을 참조 하세요.

OpenXR는 자체는 혼합 현실 엔진이 아닙니다.  대신, OpenXR를 사용 하 여 Unity와 같은 엔진에서 이식 가능한 코드를 작성 한 후에는 해당 플랫폼을 구축한 공급 업체에 관계 없이 사용자의 holographic 또는 몰입 형 장치의 기본 플랫폼 기능에 액세스할 수 있습니다.

## <a name="getting-started-with-openxr-for-hololens-2"></a>HoloLens 용 OpenXR 시작 2

HoloLens 2 용 OpenXR 응용 프로그램 개발을 시작 하려면:

1. HoloLens 2를 설정 하거나 지침에 따라 [hololens 2 에뮬레이터를 설치](using-the-hololens-emulator.md)합니다.
1. 장치 또는 에뮬레이터 내에서 스토어 앱을 시작 하 고 모든 앱이 업데이트 되었는지 확인 합니다.  그러면 HoloLens의 OpenXR 런타임이 OpenXR 1.0으로 업데이트 됩니다.  에뮬레이터를 사용 하는 경우 에뮬레이터에서 스토어 앱을 사용 하는 데 도움이 되도록 [에뮬레이터 입력 지침](using-the-hololens-emulator.md#basic-emulator-input) 을 참조 합니다.

## <a name="getting-started-with-openxr-for-windows-mixed-reality-headsets"></a>Windows Mixed Reality 용 OpenXR 시작 헤드셋

몰입 형 Windows Mixed Reality 헤드셋 용 OpenXR 응용 프로그램 개발을 시작 하려면 다음을 수행 합니다.

1. Windows Mixed Reality 최종 사용자가 OpenXR 응용 프로그램을 실행 하는 데 필요한 최소 요구 사항인 Windows 10 5 월 2019 업데이트 (1903)를 실행 해야 합니다.  이전 버전의 Windows 10을 사용 하는 경우 <a href="https://www.microsoft.com//software-download/windows10" target="_blank">windows 10 업데이트 길잡이</a>를 사용 하 여 2019 년 5 월 업데이트로 업그레이드할 수 있습니다.  PC를 업데이트할 수 없는 경우에는 [Windows 10 10 월 2018 업데이트 (1809)를 사용 하 여 OpenXR 앱을 개발할](openxr.md#developing-on-windows-10-october-2018-update)수도 있습니다. 그러나 성능이 저하 되거나 기타 문제가 발생할 수 있습니다.
2. Windows Mixed Reality 헤드셋을 설정 하거나 지침에 따라 [Windows Mixed reality 시뮬레이터를 사용 하도록](using-the-windows-mixed-reality-simulator.md)설정 합니다.  Windows Mixed reality를 설정한 후 혼합 현실 포털은 Windows Mixed Reality OpenXR 런타임을 자동으로 설치 합니다.  그러면 Microsoft Store 런타임이 최신 상태로 유지 됩니다.
3. 시작 메뉴에서 Mixed Reality 포털을 시작 하 여 Windows Mixed Reality OpenXR 런타임을 활성 상태로 만들고 ... 메뉴를 선택 하 고 "OpenXR 설정"을 선택 합니다.<br>
혼합 현실 포털에서 OpenXR 설정 ![](images/mixed-reality-portal-set-up-openxr.png)

Windows Mixed Reality OpenXR 런타임을 다시 활성화 해야 하는 경우 3 단계를 반복 합니다.

> [!NOTE]
> Windows Mixed Reality OpenXR 런타임은 곧 모든 Windows Mixed Reality 최종 사용자에 대해 자동으로 설정 됩니다.

## <a name="getting-the-mixed-reality-openxr-developer-portal"></a>Mixed Reality OpenXR 개발자 포털 가져오기

Windows Mixed Reality OpenXR 런타임을 사용해 보려면 <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">[Mixed Reality OpenXR 개발자 포털 앱</a>을 설치 하면 됩니다.  이 앱은 활성 런타임과 현재 헤드셋에 대 한 주요 정보를 제공 하는 시스템 상태 페이지와 함께 OpenXR의 다양 한 기능을 실행 하는 데모 장면을 제공 합니다.

![Mixed Reality OpenXR 개발자 포털 앱](images/mixed-reality-openxr-developer-portal.png)

## <a name="building-a-sample-openxr-app"></a>샘플 OpenXR 앱 빌드

<a href="https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> 프로젝트는 두 개의 Visual Studio 프로젝트 파일을 포함 하는 간단한 OpenXR 샘플을 보여 줍니다 .이 샘플은 Win32 데스크톱 앱과 UWP HoloLens 2 앱 모두를 위한 것입니다.  솔루션에 HoloLens UWP 프로젝트가 포함 되어 있으므로 Visual Studio에 설치 된 [유니버설 Windows 플랫폼 개발 워크 로드](install-the-tools.md#installation-checklist) 를 통해 완전히 열어야 합니다.

패키지 및 배포의 차이로 인해 Win32 및 UWP 프로젝트 파일은 별개 이지만 각 프로젝트 내의 앱 코드는 100%가 동일 합니다.

## <a name="openxr-app-best-practices-for-hololens-2"></a>HoloLens의 OpenXR 앱 모범 사례 2

아래 BasicXrApp의 [Openxrprogram .cpp](https://github.com/microsoft/OpenXR-SDK-VisualStudio/blob/master/samples/BasicXrApp/OpenXrProgram.cpp) 파일에서 모범 사례에 대 한 예제를 확인할 수 있습니다. 시작 부분에 있는 Run () 함수는 일반적인 OpenXR 앱 코드 흐름을 초기화에서 이벤트 및 렌더링 루프로 캡처합니다.

### <a name="select-a-pixel-format"></a>픽셀 형식 선택

항상 `xrEnumerateSwapchainFormats`를 사용 하 여 지원 되는 픽셀 형식을 열거 하 고 앱이 지 원하는 런타임의 첫 번째 색 및 깊이 픽셀 형식을 선택 합니다 .이는 런타임이 선호 합니다. HoloLens 2에서 `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` 및 `DXGI_FORMAT_D16_UNORM`는 일반적으로 렌더링 성능을 향상 시키기 위한 첫 번째 선택입니다. 이 기본 설정은 데스크톱 PC에서 실행 되는 VR 헤드셋에서 다를 수 있습니다.  
  
**성능 경고:** 기본이 swapchain present 색 형식이 아닌 형식을 사용 하면 런타임 사후 처리가 발생 하며,이로 인해 성능이 크게 저하 됩니다.

### <a name="gamma-correct-rendering"></a>감마-올바른 렌더링

모든 OpenXR 런타임에 적용 되기는 하지만 렌더링 파이프라인이 감마를 정확 하 게 유지 하도록 주의 해야 합니다. 이 swapchain present 렌더링할 때 렌더링 대상 뷰 형식은이 swapchain present 형식과 일치 해야 합니다 (예:이 swapchain present 형식 및 렌더링 대상 뷰의 DXGI_FORMAT_B8G8R8A8_UNORM_SRGB).
응용 프로그램의 렌더링 파이프라인이 셰이더 코드에서 수동 sRGB 변환을 수행 하는 경우는 예외입니다 .이 경우 앱은 sRGB이 swapchain present 형식을 요청 하지만 렌더링 대상 뷰에 선형 형식을 사용 해야 합니다 (예: 요청 DXGI_FORMAT_B8G8R8A8_UNORM_SRGB 이 swapchain present 형식을 사용 하 되, 렌더링 대상 뷰로 DXGI_FORMAT_B8G8R8A8_UNORM를 사용 하 여 콘텐츠를 이중 감마로 수정 하지 않도록 합니다.

### <a name="use-a-single-projection-layer"></a>단일 프로젝션 계층 사용

HoloLens 2는 응용 프로그램에서 콘텐츠를 렌더링할 수 있는 GPU 능력과 단일 프로젝션 계층에 최적화 된 하드웨어 compositor 있습니다.
항상 단일 프로젝션 계층을 사용 하면 응용 프로그램의 프레임 속도, 홀로그램 안정성 및 시각적 품질에 도움이 됩니다.  
  
**성능 경고:** 단일 보호 계층을 제외한 모든 항목을 제출 하면 런타임 사후 처리가 발생 하며,이로 인해 성능이 크게 저하 됩니다.

### <a name="render-with-texture-array-and-vprt"></a>질감 배열 및 VPRT를 사용 하 여 렌더링

색이 swapchain present `arraySize=2`를 사용 하 여 왼쪽과 오른쪽에 `xrSwapchain` 하 고, 깊이를 위해 하나를 만듭니다.
왼쪽 눈동자를 조각 0에 그리고 올바른 눈을 조각 1로 렌더링 합니다.
Stereoscopic 렌더링에 대해 VPRT 및 인스턴스화된 그리기 호출에 셰이더를 사용 하 여 GPU 로드를 최소화 합니다.
이를 통해 런타임의 최적화를 사용 하 여 HoloLens 2에서 최상의 성능을 구현할 수도 있습니다.
이중 전체 렌더링 또는 눈에이 swapchain present 별도의 개별 같이 질감 배열을 사용 하는 대신, 런타임 사후 처리가 발생 하 여 상당한 성능 저하가 발생 합니다.

### <a name="render-with-recommended-rendering-parameters-and-frame-timing"></a>권장 되는 렌더링 매개 변수 및 프레임 타이밍으로 렌더링

항상 권장 되는 구성 너비/높이 (`recommendedImageRectWidth` 및 `recommendedImageRectHeight` `XrViewConfigurationView`)를 사용 하 여 렌더링 하 고, 렌더링 전에 항상 `xrLocateViews` API를 사용 하 여 권장 되는 보기 포즈, fov 및 기타 렌더링 매개 변수를 쿼리 합니다.
포즈 및 뷰를 쿼리할 때 항상 최신 `xrWaitFrame` 호출의 `XrFrameEndInfo.predictedDisplayTime`를 사용 합니다.
이를 통해 HoloLens는 HoloLens를 입고 있는 사용자의 렌더링을 조정 하 고 시각적 품질을 최적화할 수 있습니다.

### <a name="submit-depth-buffer-for-projection-layers"></a>프로젝션 계층에 대 한 깊이 버퍼를 제출 합니다.

`XR_KHR_composition_layer_depth` 확장을 항상 사용 하 고 `xrEndFrame`에 프레임을 제출할 때 프로젝션 계층과 함께 깊이 버퍼를 제출 합니다.
이렇게 하면 HoloLens 2에서 하드웨어 깊이 다시 프로젝션을 사용 하 여 홀로그램의 안정성을 향상 시킬 수 있습니다.

### <a name="choose-a-reasonable-depth-range"></a>적절 한 깊이 범위 선택

더 좁은 깊이 범위를 사용 하 여 HoloLens의 홀로그램 안정성을 위해 가상 콘텐츠의 범위를 설정 합니다.
예를 들어 OpenXrProgram .cpp 샘플은 0.1 ~ 20 미터를 사용 합니다.
보다 균일 한 깊이 해상도를 위해 [역방향-Z](https://developer.nvidia.com/content/depth-precision-visualized) 를 사용 합니다.
HoloLens 2에서 선호 하는 `DXGI_FORMAT_D16_UNORM` 깊이 형식을 사용 하면 프레임 속도와 성능을 향상 시킬 수 있지만, 16 비트 깊이 버퍼는 24 비트 깊이 버퍼 보다 깊이 있는 해상도를 제공 하지 않습니다.
따라서 깊이 해상도를 가장 잘 활용 하기 위해 이러한 모범 사례를 따르는 것이 더 중요 합니다.

### <a name="prepare-for-different-environment-blend-modes"></a>다른 환경 blend 모드 준비

응용 프로그램이 전 세계에 완전히 차단 되는 몰입 형 헤드셋에서 실행 되는 경우 `xrEnumerateEnvironmentBlendModes` API를 사용 하 여 지원 되는 환경 blend 모드를 열거 하 고 렌더링 콘텐츠를 적절 하 게 준비 해야 합니다.
예를 들어 HoloLens와 같은 `XR_ENVIRONMENT_BLEND_MODE_ADDITIVE`를 사용 하는 시스템의 경우에는 앱이 투명 한 색으로 투명 한 색으로 사용 해야 하는 반면, `XR_ENVIRONMENT_BLEND_MODE_OPAQUE`를 사용 하는 시스템의 경우에는 앱이 백그라운드에서 일부 불투명 색 또는 일부 가상 공간을 렌더링 해야 합니다.

### <a name="choose-unbounded-reference-space-as-applications-root-space"></a>응용 프로그램의 루트 공간으로 바인딩되지 않은 참조 공간을 선택 합니다.

응용 프로그램은 일반적으로 뷰, 작업 및 holograms를 연결 하는 데 루트 세계 좌표 공간을 설정 합니다.
확장이 지원 되는 경우에는 `XR_REFERENCE_SPACE_TYPE_UNBOUNDED_MSFT`를 사용 하 여 [전 세계 규모의 좌표계](coordinate-systems.md#building-a-world-scale-experience)를 설정 하 고, 사용자가 앱이 시작 되는 위치에서 먼 거리 (예: 5 미터)로 이동할 때 앱에서 원치 않는 홀로그램 드리프트를 피할 수 있도록 합니다.
제한 없는 공간 확장이 존재 하지 않는 경우 `XR_REFERENCE_SPACE_TYPE_LOCAL`를 대체 (fallback)로 사용 합니다.

### <a name="associate-hologram-with-spatial-anchor"></a>홀로그램을 공간 앵커와 연결

바인딩되지 않은 참조 공간을 사용 하는 경우 사용자가 holograms 하 게 되 면 해당 참조 공간이 [달라질 수](coordinate-systems.md#building-a-world-scale-experience)있습니다.
홀로그램 사용자가 전 세계의 불연속 위치에 배치 하는 경우 `xrCreateSpatialAnchorSpaceMSFT` 확장 함수를 사용 하 여 [공간 앵커를 만들고](spatial-anchors.md#best-practices) 홀로그램을 원점에 배치 합니다.
그러면 홀로그램은 시간이 지남에 따라 독립적으로 안정적으로 유지 됩니다.

### <a name="support-mixed-reality-capture"></a>혼합 현실 캡처 지원

HoloLens 2의 기본 디스플레이는 추가 환경 혼합을 사용 하지만, 사용자가 [혼합 된 현실 캡처](mixed-reality-capture-for-developers.md)를 시작 하면 앱의 렌더링 콘텐츠가 환경 비디오 스트림과 알파 혼합 됩니다.
혼합 현실에서 최적의 시각적 품질을 얻기 위해 비디오를 캡처하는 것은 프로젝션 계층의 `layerFlags`에서 `XR_COMPOSITION_LAYER_BLEND_TEXTURE_SOURCE_ALPHA_BIT`를 설정 하는 것이 가장 좋습니다.  

**성능 경고:** 단일 프로젝션 계층에서 `XR_COMPOSITION_LAYER_BLEND_TEXTURE_SOURCE_ALPHA_BIT` 플래그를 생략 하면 런타임 사후 처리가 발생 하며,이로 인해 성능이 크게 저하 됩니다.

### <a name="avoid-quad-layers"></a>쿼드 계층 방지

`XrCompositionLayerQuad`를 사용 하 여 4 개의 계층을 컴포지션 계층으로 제출 하는 대신 쿼드 콘텐츠를 프로젝션이 swapchain present 직접 렌더링 합니다.

**성능 경고:** 쿼드 계층과 같이 단일 프로젝션 계층 밖의 추가 계층을 제공 하면 런타임 사후 처리가 발생 하 여 상당한 성능 저하가 발생 합니다.

## <a name="openxr-app-performance-on-hololens-2"></a>HoloLens의 OpenXR 앱 성능 2

HoloLens 2에는 `xrEndFrame`를 통해 컴퍼지션 데이터를 제출 하는 다양 한 방법이 있습니다. 그러면 사후 처리가 발생 하 여 성능이 저하 될 수 있습니다.
성능 penalities을 방지 하려면 다음 특징을 가진 [단일 `XrCompositionProjectionLayer`를 제출](#use-a-single-projection-layer) 합니다.
* [텍스처 배열 사용이 swapchain present](#render-with-texture-array-and-vprt)
* [기본 색이 swapchain present 형식 사용](#select-a-pixel-format)
* [질감 원본-알파 혼합 플래그 설정](#support-mixed-reality-capture)
* [권장 되는 보기 차원 사용](#render-with-recommended-rendering-parameters-and-frame-timing)
* `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` 플래그를 설정 하지 마십시오.
* `XrCompositionLayerDepthInfoKHR` `minDepth`를 0.0 f로 설정 하 고 `maxDepth`를 1.0 f로 설정 합니다.

추가 고려 사항으로 인해 성능이 향상 됩니다.
* [16 비트 깊이 형식 사용](#choose-a-reasonable-depth-range)
* [인스턴스화된 그리기 호출 만들기](#render-with-texture-array-and-vprt)

## <a name="roadmap"></a>로드맵

OpenXR 사양은 런타임 구현자가 <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">기본 OpenXR 1.0 사양</a>에 정의 된 [핵심 기능](openxr.md#what-is-openxr) 외에 추가 기능을 노출할 수 있도록 하는 확장 메커니즘을 정의 합니다.

OpenXR 확장에는 세 가지 종류가 있습니다.
* **공급 업체 확장 (예: MSFT):** 하드웨어 또는 소프트웨어 기능에서 공급 업체별 혁신을 사용 하도록 설정 합니다.  모든 런타임 공급 업체는 언제 든 지 공급 업체 확장을 소개 하 고 제공할 수 있습니다.
* **EXT 확장:** 여러 회사가 정의 하 고 구현 하는 교차 공급 업체 확장  관심이 있는 회사 그룹은 언제 든 지 내선 내선 번호를 도입할 수 있습니다.
* **Khr 확장:** 공식 Khronos 확장은 핵심 사양 릴리스의 일부로 비준.  KHR 확장은 코어 사양 자체와 동일한 라이선스로 적용 됩니다.

Windows Mixed Reality OpenXR 런타임은 올해의 마지막에는 HoloLens 2 기능의 전체 집합을 OpenXR 응용 프로그램으로 가져오는 MSFT 및 EXT 확장 집합을 지원 합니다.
* [바인딩되지 않은 참조 공간 (세계 규모가 뛰어난 환경)](coordinate-systems.md#building-a-world-scale-experience)
* [공간 앵커 + 저장소](spatial-anchors.md)
* [손 모양 articulation + 손 모양](hands-and-tools.md)
* [응시](eye-tracking.md)
* [보조 뷰 구성 (혼합 현실 캡처)](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)
* [장면 이해](scene-understanding.md)
* Windows SDK Api와의 상호 운용성

이러한 확장 중 일부는 공급 업체별 MSFT 확장으로 시작 될 수 있지만, Microsoft 및 기타 OpenXR runtime 공급 업체는 이러한 여러 기능 영역에 대 한 공급 업체 확장 또는 KHR 확장을 디자인 하기 위해 함께 작업 하 고 있습니다.  이렇게 하면 핵심 사양과 마찬가지로 해당 기능에 대해 작성 하는 코드를 런타임 공급 업체 간에 이식할 수 있습니다.

## <a name="troubleshooting"></a>문제 해결

Windows Mixed Reality OpenXR 런타임에 대 한 몇 가지 문제 해결 팁은 다음과 같습니다.  <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 사양</a>에 대 한 다른 질문이 있는 경우 <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR 포럼</a> 또는 <a href="https://khr.io/slack" target="_blank">여유 시간 #openxr 채널</a>을 방문 하세요.

### <a name="developing-on-windows-10-october-2018-update"></a>Windows 10 10 월 2018 업데이트에서 개발

개발 PC를 2019 년 5 월 [업데이트로 업그레이드할](https://www.microsoft.com//software-download/windows10)수 없는 경우 다음 단계를 수행 하 여 개발을 위해 Windows 10 10 월 2018 업데이트 (1809) PC를 설정할 수 있습니다.

1. 위의 단계에 따라 데스크톱 PC에서 OpenXR를 시작 합니다.
1. Windows Mixed Reality OpenXR 런타임을 시스템의 활성 OpenXR 런타임으로 설정 하려면 [Windows Mixed Reality OpenXR Developer Compatibility Pack](https://aka.ms/openxr-compat)을 설치 합니다.

> [!NOTE]
> OpenXR 응용 프로그램을 개발할 때 Windows 10 10 월 2018 업데이트 (1809)를 사용할 수 있지만, 최종 사용자가 Windows Mixed Reality에서 OpenXR를 사용 하려면 Windows 10에서 2019 업데이트 (1903)가 최소 요구 사항입니다.  10 월 2018 업데이트에서 OpenXR 앱을 실행할 때 성능이 저하 되거나 기타 문제가 발생할 수 있습니다.  개발 PC를 Windows 10 5 월 2019 업데이트 (1903)로 업그레이드 하는 것이 좋습니다.

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>Windows Mixed Reality를 시작 하지 않는 OpenXR 앱

OpenXR 앱을 실행할 때 Windows Mixed Reality를 시작 하지 않는 경우 Windows Mixed Reality OpenXR 런타임이 활성 런타임으로 설정 되지 않을 수 있습니다.  [OpenXR For Windows Mixed Reality 헤드셋 시작](#getting-started-with-openxr-for-windows-mixed-reality-headsets) 을 참조 하 여 런타임을 활성 상태로 만듭니다.

시스템의 Windows Mixed Reality OpenXR 런타임 상태에 대 한 추가 문제 해결 도움말을 보려면 [Mixed Reality OpenXR 개발자 포털](#getting-the-mixed-reality-openxr-developer-portal) 을 실행할 수도 있습니다.

### <a name="mixed-reality-portal-not-showing-set-up-openxr-menu-item"></a>혼합 현실 포털에서 "OpenXR 설정" 메뉴 항목을 표시 하지 않음

Windows 10 10 월 2018 업데이트 (1809) 이상을 실행 하 고 있어야 합니다.  이전 버전의 Windows 10을 사용 하는 경우 [windows 10 업데이트 도우미](https://www.microsoft.com//software-download/windows10)를 사용 하 여 1903 (5 월 2019 업데이트)로 업그레이드할 수 있습니다.

이전 버전의 Mixed Reality 포털 앱이 있는 경우 "OpenXR 설정" 메뉴 항목을 사용 하지 못할 수 있습니다.  [혼합 현실 포털 앱 업데이트](https://www.microsoft.com/p/mixed-reality-portal/9ng1h8b3zc7m) 를 확인 하 여 최신 버전이 있는지 확인 합니다.

Windows Mixed Reality OpenXR 런타임이 이미 설치 되어 있고 활성 상태인 경우에는 "OpenXR 설정" 메뉴 항목이 표시 되지 않습니다.  [Mixed Reality OpenXR 개발자 포털](#getting-the-mixed-reality-openxr-developer-portal) 을 설치 하 여 시스템에서 OpenXR 런타임의 현재 상태를 확인할 수 있습니다.

## <a name="see-also"></a>참고 항목

* <a href="https://www.khronos.org/openxr/" target="_blank">OpenXR에 대 한 자세한 정보</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 사양</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">OpenXR 1.0 API 참조</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">OpenXR 1.0 빠른 참조 가이드</a>
