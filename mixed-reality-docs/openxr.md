---
title: OpenXR
description: 이식 가능한 OpenXR API 표준을 사용 하 여 엔진을 빌드하고 Windows Mixed Reality 및 HoloLens 2 헤드셋에 배포 합니다.
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, 네이티브, 네이티브 앱, 사용자 지정 엔진, 미들웨어
ms.openlocfilehash: 8263e530336d53020ebe35091426f0596f257805
ms.sourcegitcommit: 6d9d01d53137435c787f247f095d5255581695fc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83228038"
---
# <a name="openxr"></a>OpenXR

OpenXR는 [혼합 현실 스펙트럼](mixed-reality.md)에 걸쳐 있는 많은 공급 업체의 다양 한 장치에 대 한 기본 액세스를 엔진에 제공 하는 <a href="https://www.khronos.org/" target="_blank">Khronos</a> 의 오픈 로열티 없는 무료 API 표준입니다.

OpenXR를 사용 하 여 개발할 수 있습니다는 HoloLens 2 또는 Windows Mixed Reality 모던 헤드셋 바탕 화면입니다.  헤드셋에 액세스할 수 없는 경우 HoloLens 2 에뮬레이터 또는 Windows Mixed Reality 시뮬레이터를 대신 사용할 수 있습니다.

## <a name="why-openxr"></a>왜 OpenXR?

OpenXR를 사용 하면 실제 세계를 숨기고 디지털 환경으로 대체 하는 몰입 형 장치 (예: 데스크톱 Pc 용 Windows Mixed Reality 헤드셋) 뿐만 아니라 실제 세계에 디지털 콘텐츠를 저장 하는 holographic 장치 (예: HoloLens 2)를 모두 대상으로 하는 엔진을 빌드할 수 있습니다.  OpenXR를 사용 하면 다양 한 하드웨어 플랫폼에서 이식할 수 있는 코드를 작성할 수 있습니다.

OpenXR API는 응용 프로그램을 헤드셋의 기본 플랫폼 지원에 직접 연결 하는 로더를 사용 합니다.  이는 Windows Mixed Reality 헤드셋 또는 다른 헤드셋을 사용 하는지 여부에 관계 없이 최종 사용자에 게 최대 성능 및 최소 대기 시간을 제공 합니다.

## <a name="what-is-openxr"></a>OpenXR 란?

OpenXR API는 HoloLens 2와 같은 holographic 장치와 Windows Mixed Reality 헤드셋 같은 몰입 형 장치를 모두 대상으로 지정할 수 있는 엔진을 빌드하는 데 필요한 핵심 포즈 예측, 프레임 타이밍 및 공간 입력 기능을 제공 합니다.

OpenXR API에 대 한 자세한 내용은 OpenXR 1.0 <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">사양</a>, <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">API 참조</a> 및 <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">빠른 참조 가이드</a>를 확인 하세요.  자세한 내용은 <a href="https://www.khronos.org/openxr/" target="_blank">Khronos OpenXR 페이지</a>를 참조 하세요.

HoloLens 2의 전체 기능 집합을 대상으로 지정 하려면 트레일러 추적, 눈 추적, 공간 매핑 및 공간 앵커와 같이 OpenXR 1.0 코어 이외의 추가 기능을 사용할 수 있도록 하는 공급 업체 및 공급 업체별 OpenXR 확장을 사용 합니다.  올해 후반에 제공 되는 확장에 대 한 자세한 내용은 아래의 [로드맵 섹션](#roadmap) 을 참조 하세요.

OpenXR는 자체는 혼합 현실 엔진이 아닙니다.  대신, OpenXR를 사용 하 여 Unity와 같은 엔진에서 이식 가능한 코드를 작성 한 후에는 해당 플랫폼을 구축한 공급 업체에 관계 없이 사용자의 holographic 또는 몰입 형 장치의 기본 플랫폼 기능에 액세스할 수 있습니다.

## <a name="roadmap"></a>로드맵

OpenXR 사양은 런타임 구현자가 <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">기본 OpenXR 1.0 사양</a>에 정의 된 [핵심 기능](#what-is-openxr) 외에 추가 기능을 노출할 수 있도록 하는 확장 메커니즘을 정의 합니다.

OpenXR 확장에는 세 가지 종류가 있습니다.
* **공급 업체 확장 (예: `MSFT` ):** 하드웨어 또는 소프트웨어 기능에서 공급 업체별 혁신을 사용 하도록 설정 합니다.  모든 런타임 공급 업체는 언제 든 지 공급 업체 확장을 소개 하 고 제공할 수 있습니다.
  * **실험적 공급 업체 확장 (예: `MSFT_preview` ):** 피드백을 수집 하기 위해 미리 보는 실험적 공급 업체 확장입니다.  `MSFT_preview`확장은 개발자 장치에만 해당 되며, 실제 확장이 제공 될 때 제거 됩니다.  실험을 위해 [개발자 장치에서 미리 보기 확장을 사용 하도록 설정할](openxr-getting-started.md#using-preview-extensions)수 있습니다.
* **교차 공급 업체 `EXT` 확장:** 여러 회사에서 정의 하 고 구현 하는 공급 업체 확장 프로그램입니다.  관심이 있는 회사 그룹은 언제 든 지 내선 내선 번호를 도입할 수 있습니다.
* **공식 `KHR` 확장:** 공식 Khronos 확장 비준 핵심 사양 릴리스의 일부로 구성 됩니다.  KHR 확장은 코어 사양 자체와 동일한 라이선스로 적용 됩니다.

2020 년 7 월까지 Windows Mixed Reality OpenXR 런타임은 `MSFT` `EXT` HoloLens 2 기능의 전체 집합을 OpenXR 응용 프로그램으로 가져오는 및 확장 집합을 지원 합니다.

| 기능 영역 | 확장 가용성 |
|--------------|------------------------|
| 시스템 + 세션 | **OpenXR 1.0 코어 사양:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#instance" target="_blank">XrInstance</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#system" target="_blank">XrSystemId</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#session" target="_blank">XrSession</a></code> |
| [참조 공간 (보기, 로컬, 단계)](coordinate-systems.md) | **OpenXR 1.0 코어 사양:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#spaces" target="_blank">XrSpace</a></code> |
| 구성 보기 (mono, 스테레오) | **OpenXR 1.0 코어 사양:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#view_configurations" target="_blank">XrView...</a></code> |
| [Swapchains](rendering.md)  +  [프레임 타이밍](understanding-performance-for-mixed-reality.md) | **OpenXR 1.0 코어 사양:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#rendering" target="_blank">XrSwapchain...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-synchronization" target="_blank">xrWaitFrame</a></code> |
| 컴포지션 계층<br />(프로젝션, 쿼드) | **OpenXR 1.0 코어 사양:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#compositing" target="_blank">XrCompositionLayer...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-submission" target="_blank">xrEndFrame</a></code> |
| [Input 및 haptics](interaction-fundamentals.md) | **OpenXR 1.0 코어 사양:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#input" target="_blank">XrAction...</a></code> |
| Direct3D 11 통합 | **정식 `KHR` 확장 릴리스:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D11_enable" target="_blank">XR_KHR_D3D11_enable</a></code> |
| Direct3D 12 통합 | **`KHR` [Preview 런타임 2003](openxr-getting-started.md#using-preview-extensions)의 공식 확장:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D12_enable" target="_blank">XR_KHR_D3D12_enable</a></code><br /><p>**안정적인 런타임에 지원**: 2020 년 5 월 *(계획 됨)*</p> |
| [바인딩되지 않은 참조 공간 <br /> (세계 규모가 뛰어난 환경)](coordinate-systems.md#building-a-world-scale-experience) | **`MSFT`확장 릴리스:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_unbounded_reference_space" target="_blank">XR_MSFT_unbounded_reference_space</a></code> |
| [공간 앵커](spatial-anchors.md) | **`MSFT`확장 릴리스:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_anchor">XR_MSFT_spatial_anchor</a></code> |
| [손으로 조작 <br /> (그립/aim 포즈, 공중 탭, 방법)](hands-and-tools.md)<p>*HoloLens 2만*</p> | **`MSFT`확장 릴리스:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_interaction">XR_MSFT_hand_interaction</a></code> |
| [손 모양 articulation + 손 모양](hands-and-tools.md)<p>*HoloLens 2만*</p> | **`MSFT_preview`[preview 런타임 2001](openxr-getting-started.md#using-preview-extensions)의 확장:**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_hand_tracking_preview">XR_MSFT_hand_tracking_preview</a></code><br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_hand_tracking_mesh_preview">XR_MSFT_hand_tracking_mesh_preview</a></code><p>** `MSFT` 또는 `EXT` preview 런타임의 확장**: 2020 년 5 월 *(계획 됨)*</p> |
| [응시](eye-tracking.md)<p>*HoloLens 2만*</p> | ** `EXT` [preview 런타임 2003](openxr-getting-started.md#using-preview-extensions)의 확장**:<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_eye_gaze_interaction" target="_blank">XR_EXT_eye_gaze_interaction</a></code><p>**안정적인 런타임에 지원**: 2020 년 5 월 *(계획 됨)*</p> |
| 다른 HoloLens Sdk (예: [QR](qr-code-tracking.md))와의 상호 운용성<p>*HoloLens 2만*</p> | **`MSFT_preview`[preview 런타임 2001](openxr-getting-started.md#using-preview-extensions)의 확장:**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_spatial_graph_bridge_preview">XR_MSFT_spatial_graph_bridge_preview</a></code><p>** `MSFT` preview 런타임의 확장**: 2020 년 5 월 *(계획 됨)*</p> |
| [혼합 현실 캡처 <br /> (PV 카메라의 세 번째 렌더링)](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)<p>*HoloLens 2만*</p> | **`MSFT_preview`[preview 런타임 2003](openxr-getting-started.md#using-preview-extensions)의 확장:**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_secondary_view_configuration_preview">XR_MSFT_secondary_view_configuration_preview</a></code><br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_first_person_observer_preview">XR_MSFT_first_person_observer_preview</a></code><p>** `MSFT` preview 런타임의 확장**: 6 월 2020 *(계획 됨)*</p> |
| [동작 컨트롤러 렌더링 모델](motion-controllers.md#rendering-the-motion-controller-model) | **`MSFT_preview`[preview 런타임 2003](openxr-getting-started.md#using-preview-extensions)의 확장:**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_controller_model_preview">XR_MSFT_controller_model_preview</a></code><p>** `MSFT` preview 런타임의 확장**: 7 월 2020 *(계획 됨)*</p> |
| [장면 이해 (평면, 메시)](scene-understanding.md)<p>*HoloLens 2만*</p> | <p>** `MSFT_preview` preview 런타임의 확장**: 6 월 2020 *(계획 됨)*</p><p>** `MSFT` preview 런타임의 확장**: 7 월 2020 *(계획 됨)*</p> |
| 기타 교차 공급 업체 확장 | <p>**정식 `KHR` 확장 릴리스:**</p><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_composition_layer_depth" target="_blank">XR_KHR_composition_layer_depth</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_visibility_mask" target="_blank">XR_KHR_visibility_mask</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_win32_convert_performance_counter_time" target="_blank">XR_KHR_win32_convert_performance_counter_time</a></code><p>**`EXT`릴리스된 확장:**</p><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_win32_appcontainer_compatible" target="_blank">XR_EXT_win32_appcontainer_compatible</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_debug_utils" target="_blank">XR_EXT_debug_utils</a></code> |

이러한 확장 중 일부는 공급 업체별 확장으로 시작 될 수 있지만 `MSFT` , Microsoft 및 기타 OpenXR runtime 공급 업체는 `EXT` `KHR` 이러한 기능 영역에 대 한 교차 공급 업체 또는 확장을 설계 하기 위해 함께 작업 하 고 있습니다.  이렇게 하면 핵심 사양과 마찬가지로 해당 기능에 대해 작성 하는 코드를 런타임 공급 업체 간에 이식할 수 있습니다.

## <a name="get-started-with-openxr"></a>OpenXR 시작

OpenXR를 사용 하 여 개발할 수 있습니다는 HoloLens 2 또는 Windows Mixed Reality 모던 헤드셋 바탕 화면입니다.  헤드셋에 액세스할 수 없는 경우 HoloLens 2 에뮬레이터 또는 Windows Mixed Reality 시뮬레이터를 대신 사용할 수 있습니다.

HoloLens 2 또는 몰입 형 Windows Mixed Reality 헤드셋 용 OpenXR 응용 프로그램 개발을 시작 하려면 [OpenXR 개발을 시작 하는 방법](openxr-getting-started.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

* <a href="https://www.khronos.org/openxr/" target="_blank">OpenXR에 대 한 자세한 정보</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 사양</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">OpenXR 1.0 API 참조</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">OpenXR 1.0 빠른 참조 가이드</a>
