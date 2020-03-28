---
title: OpenXR 모범 사례
description: OpenXR 응용 프로그램의 시각적 품질, 안정성 및 성능에 대 한 모범 사례를 알아봅니다.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, 네이티브, 네이티브 앱, 사용자 지정 엔진, 미들웨어, 모범 사례, 성능, 품질, 안정성
ms.openlocfilehash: c0ddbd0604760ccae34d347e93b918be4aead269
ms.sourcegitcommit: 536fd45b48a70bbeca1454cef517ae007225e533
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80362018"
---
# <a name="openxr-app-best-practices"></a>OpenXR 앱 모범 사례

아래 <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a>의 OpenXRProgram .cpp 파일에서 모범 사례에 대 한 예제를 확인할 수 있습니다. 시작 부분에 있는 Run () 함수는 일반적인 OpenXR 앱 코드 흐름을 초기화에서 이벤트 및 렌더링 루프로 캡처합니다.

## <a name="best-practices-for-visual-quality-and-stability"></a>시각적 품질 및 안정성에 대 한 모범 사례

이 섹션의 모범 사례에서는 모든 OpenXR 응용 프로그램에서 최상의 시각적 품질 및 안정성을 얻는 방법에 대해 설명 합니다.

HoloLens 2와 관련 된 추가 성능 권장 사항은 아래의 [hololens의 성능에 대 한 모범 사례 2](#best-practices-for-performance-on-hololens-2) 섹션을 참조 하세요.

### <a name="gamma-correct-rendering"></a>감마-올바른 렌더링

렌더링 파이프라인이 감마를 정확 하 게 유지 하도록 주의 해야 합니다. 이 swapchain present 렌더링할 때 렌더링 대상 뷰 형식은이 swapchain present 형식과 일치 해야 합니다 (예:이 swapchain present 형식 및 렌더링 대상 뷰의 DXGI_FORMAT_B8G8R8A8_UNORM_SRGB).
응용 프로그램의 렌더링 파이프라인이 셰이더 코드에서 수동 sRGB 변환을 수행 하는 경우는 예외입니다 .이 경우 앱은 sRGB이 swapchain present 형식을 요청 하지만 렌더링 대상 뷰에 선형 형식을 사용 해야 합니다 (예: 요청 DXGI_FORMAT_B8G8R8A8_UNORM_SRGB 이 swapchain present 형식을 사용 하 되, 렌더링 대상 뷰로 DXGI_FORMAT_B8G8R8A8_UNORM를 사용 하 여 콘텐츠를 이중 감마로 수정 하지 않도록 합니다.

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

## <a name="best-practices-for-performance-on-hololens-2"></a>HoloLens의 성능에 대 한 모범 사례 2

하드웨어 재 프로젝션 지원을 포함 하는 모바일 장치인 HoloLens 2에는 최적의 성능을 얻기 위한 보다 엄격한 요구 사항이 있습니다.  `xrEndFrame`를 통해 컴퍼지션 데이터를 제출 하는 여러 가지 방법이 있으며이로 인해 사후 처리가 발생 하 여 성능이 저하 될 수 있습니다.

### <a name="select-a-swapchain-format"></a>이 swapchain present 형식 선택

항상 `xrEnumerateSwapchainFormats`를 사용 하 여 지원 되는 픽셀 형식을 열거 하 고 앱이 지 원하는 런타임의 첫 번째 색 및 깊이 픽셀 형식을 선택 합니다 .이는 런타임이 최적의 성능을 위해 선호 하기 때문입니다. HoloLens 2에서 `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` 및 `DXGI_FORMAT_D16_UNORM`는 일반적으로 렌더링 성능을 향상 시키기 위한 첫 번째 선택입니다. 이 기본 설정은 데스크톱 PC에서 실행 되는 VR 헤드셋에서 다를 수 있습니다. 여기서 24 비트 깊이 버퍼는 성능에 영향을 미치지 않습니다.
  
**성능 경고:** 기본이 swapchain present 색 형식이 아닌 형식을 사용 하면 런타임 사후 처리가 발생 하며,이로 인해 성능이 크게 저하 됩니다.

### <a name="render-with-recommended-rendering-parameters-and-frame-timing"></a>권장 되는 렌더링 매개 변수 및 프레임 타이밍으로 렌더링

항상 권장 되는 구성 너비/높이 (`recommendedImageRectWidth` 및 `recommendedImageRectHeight` `XrViewConfigurationView`)를 사용 하 여 렌더링 하 고, 렌더링 전에 항상 `xrLocateViews` API를 사용 하 여 권장 되는 보기 포즈, fov 및 기타 렌더링 매개 변수를 쿼리 합니다.
포즈 및 뷰를 쿼리할 때 항상 최신 `xrWaitFrame` 호출의 `XrFrameEndInfo.predictedDisplayTime`를 사용 합니다.
이를 통해 HoloLens는 HoloLens를 입고 있는 사용자의 렌더링을 조정 하 고 시각적 품질을 최적화할 수 있습니다.

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

### <a name="avoid-quad-layers"></a>쿼드 계층 방지

`XrCompositionLayerQuad`를 사용 하 여 4 개의 계층을 컴포지션 계층으로 제출 하는 대신 쿼드 콘텐츠를 프로젝션이 swapchain present 직접 렌더링 합니다.

**성능 경고:** 쿼드 계층과 같이 단일 프로젝션 계층 밖의 추가 계층을 제공 하면 런타임 사후 처리가 발생 하 여 상당한 성능 저하가 발생 합니다.