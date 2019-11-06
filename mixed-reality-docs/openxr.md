---
title: OpenXR
description: 이식 가능한 OpenXR API 표준을 사용 하 여 엔진을 빌드하고 Windows Mixed Reality 및 HoloLens 2 헤드셋에 배포 합니다.
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, Mixed Reality OpenXR Developer Portal, DirectX, 네이티브, 네이티브 앱 사용자 지정 엔진, 미들웨어
ms.openlocfilehash: d29b59d7dec19e5423c83ea6e61bb5625c8981dd
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641128"
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
