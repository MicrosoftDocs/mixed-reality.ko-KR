---
title: OpenXR
description: Mixed Reality OpenXR Developer Preview를 사용 하 여 provisional OpenXR 0.90 API를 사용해 보세요.
author: thetuvix
ms.author: alexturn
ms.date: 3/18/2019
ms.topic: article
keywords: Mixed Reality OpenXR Developer Preview
ms.openlocfilehash: 723b0b85785d4b6dd735430aa76a24b9ce05b5c7
ms.sourcegitcommit: 8d6e5723283c03f984f1fafef81afa5aab5d04bc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66039178"
---
# <a name="openxr"></a>OpenXR

OpenXR는 [혼합 현실 스펙트럼](mixed-reality.md)에 걸쳐 있는 여러 공급 업체의 다양 한 장치에 대 한 기본 액세스를 제공 하는 [Khronos](https://www.khronos.org/) 에서 열리는 오픈 로열티 없는 표준입니다.

OpenXR를 사용 하는 경우 실제 세계에 디지털 콘텐츠를 저장 하는 holographic 장치 (예: HoloLens 2)를 모두 대상으로 하는 응용 프로그램을 빌드할 수 있습니다. 실제 세계에서 디지털 환경으로 대체 합니다.  OpenXR를 사용 하면 다양 한 하드웨어 플랫폼에서 이식할 수 있는 코드를 작성할 수 있습니다.

OpenXR 표준은 현재 provisional 단계에 있으며, 피드백을 위해 초기 OpenXR 0.90 사양을 릴리스 했습니다.  [Provisional 0.90 사양](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html) 및 [헤더](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)에 대 한 액세스를 포함 하 여 OpenXR에 대 한 자세한 내용은 [Khronos OpenXR 페이지](https://www.khronos.org/openxr/)를 참조 하세요. 

Mixed Reality OpenXR Developer Preview를 사용 하 여 HoloLens 2 또는 데스크톱 PC에서 provisional OpenXR 0.90 API를 사용해 볼 수 있습니다.  이 초기 런타임을 통해 OpenXR 0.90 API를 대상으로 하는 응용 프로그램에서 HoloLens 2 또는 Windows Mixed Reality 모던 헤드셋을 대상으로 지정할 수 있습니다.

헤드셋에 액세스할 수 없는 경우 HoloLens 2 에뮬레이터 또는 Windows Mixed Reality 시뮬레이터를 대신 사용할 수 있습니다.

## <a name="setting-up-the-mixed-reality-openxr-developer-preview-for-hololens-2"></a>HoloLens 2 용 Mixed Reality OpenXR Developer 미리 보기 설정

HoloLens 2의 Mixed Reality OpenXR Developer Preview를 시작 하려면 다음을 수행 하세요.

1. HoloLens 2를 설정 하거나 지침에 따라 [hololens 2 에뮬레이터를 설치](using-the-hololens-emulator.md)합니다.
1. 장치 또는 에뮬레이터 내에서 스토어 앱을 시작 하 고 모든 앱이 업데이트 되었는지 확인 합니다.  그러면 해당 장치에서 앱과 함께 사용할 Mixed Reality OpenXR Developer Preview가 설치 됩니다.  에뮬레이터를 사용 하는 경우 에뮬레이터에서 스토어 앱을 사용 하는 데 도움이 되도록 [에뮬레이터 입력 지침](using-the-hololens-emulator.md#basic-emulator-input) 을 참조 합니다.

## <a name="setting-up-the-mixed-reality-openxr-developer-preview-for-immersive-desktop-headsets"></a>몰입 형 데스크톱 헤드셋의 Mixed Reality OpenXR Developer Preview 설정

데스크톱 PC에서 Mixed Reality OpenXR Developer Preview를 시작 하려면 다음을 수행 하세요.

1. Windows 10 10 월 2018 업데이트 (1809) 또는 Windows 10 2019 업데이트 (1903)를 실행 해야 합니다.  이전 버전의 Windows 10을 사용 하는 경우 [windows 10 업데이트 길잡이](https://www.microsoft.com/en-us/software-download/windows10)를 사용 하 여 2019 년 5 월 업데이트로 업그레이드할 수 있습니다.
1. Windows Mixed Reality 헤드셋을 설정 하거나 지침에 따라 [Windows Mixed reality 시뮬레이터를 사용 하도록](using-the-windows-mixed-reality-simulator.md)설정 합니다.
1. [Mixed Reality OpenXR Developer Preview 앱](https://www.microsoft.com/store/productId/9n5cvvl23qbt)을 설치 합니다.  이 앱은 Windows 10 10 월 2018 업데이트 (1809) 이상에서 preview OpenXR runtime을 사용 하 여 설정할 수 있습니다.  이 앱을 설치 하면 Windows 스토어에서 런타임을 최신 상태로 유지 합니다.
1. 시작 메뉴에서 Mixed Reality OpenXR Developer Preview 앱을 실행 하 고 지침에 따라 런타임을 활성으로 설정 합니다.  곧이 앱을 통해 다른 OpenXR 디버그 정보를 탐색할 수 있습니다.

![Mixed Reality OpenXR Developer Preview 앱](images/mixed-reality-openxr-developer-preview.png)

### <a name="support-for-windows-10-october-2018-update"></a>Windows 10 10 월 2018 업데이트에 대 한 지원

Windows 10에서 2019 업데이트 (1903)를 실행 하 고 위의 단계를 수행한 경우 Mixed Reality OpenXR Developer Preview를 사용할 준비가 된 것입니다.

[데스크톱 PC를 2019](https://www.microsoft.com/en-us/software-download/windows10)년 5 월 업데이트로 업그레이드할 준비가 되지 않은 경우 다음 단계를 수행 하 여 Windows 10 10 월 2018 업데이트 (1809)를 살펴볼 수 있습니다.

1. 위의 단계에 따라 Mixed Reality OpenXR Developer Preview를 설치 합니다.
1. Mixed Reality OpenXR Developer Preview를 시스템의 활성 OpenXR 런타임으로 설정 하려면 [Mixed Reality OpenXR Developer Preview Compatibility Pack](https://aka.ms/openxr-compat)을 설치 합니다.

## <a name="building-a-sample-openxr-app"></a>샘플 OpenXR 앱 빌드

[BasicXrApp](https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp) 프로젝트는 두 개의 Visual Studio 프로젝트 파일을 포함 하는 간단한 OpenXR 샘플을 보여 줍니다 .이 샘플은 Win32 데스크톱 앱과 UWP HoloLens 2 앱 모두를 위한 것입니다.  솔루션에 HoloLens UWP 프로젝트가 포함 되어 있으므로 Visual Studio에 설치 된 [유니버설 Windows 플랫폼 개발 워크 로드](install-the-tools.md#installation-checklist) 를 통해 완전히 열어야 합니다.

패키지 및 배포의 차이로 인해 Win32 및 UWP 프로젝트 파일은 별개 이지만 각 프로젝트 내의 앱 코드는 100%가 동일 합니다.

## <a name="feedback"></a>사용자 의견

[OpenXR Provisional 0.90 사양](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)에 대 한 피드백을 제공 하려면 [Khronos OpenXR 포럼](https://community.khronos.org/c/openxr), [여유 시간 #openxr 채널](https://khr.io/slack) 및 [사양 문제 추적기](https://github.com/KhronosGroup/OpenXR-Docs/issues)를 방문해 보세요.

## <a name="troubleshooting"></a>문제 해결

다음은 Mixed Reality OpenXR Developer Preview에 대 한 몇 가지 문제 해결 팁입니다.  다른 문제가 발생 하는 경우 [Khronos OpenXR 포럼](https://community.khronos.org/c/openxr) 또는 [여유 시간 #openxr 채널](https://khr.io/slack)을 방문 하세요.

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>Windows Mixed Reality를 시작 하지 않는 OpenXR 앱

OpenXR 앱을 실행할 때 Windows Mixed Reality를 시작 하지 않는 경우 Mixed Reality OpenXR 개발자 미리 보기가 활성 런타임으로 설정 되지 않을 수 있습니다.  Mixed Reality OpenXR Developer Preview 앱을 실행 하 고 지침에 따라 런타임을 활성으로 설정 해야 합니다.

### <a name="mixed-reality-openxr-developer-preview-app-cannot-be-installed"></a>Mixed Reality OpenXR Developer Preview 앱을 설치할 수 없습니다. 

Windows 10 10 월 2018 업데이트 (1809) 이상을 실행 하 고 있어야 합니다.  이전 버전의 Windows 10을 사용 하는 경우 [windows 10 업데이트 도우미](https://www.microsoft.com/en-us/software-download/windows10)를 사용 하 여 1903 (5 월 2019 업데이트)로 업그레이드할 수 있습니다.

Mixed Reality OpenXR Developer Preview 앱의 설치 단추가 Windows 10 10 월 2018 업데이트에서 아무 작업도 수행 하지 않는 경우 시스템에서 앱에 대 한 부실 시스템 요구 사항을 캐시 했을 수 있습니다.  명령 프롬프트에서 명령을 `wsreset.exe` 실행 하 여 캐시를 지울 수 있습니다.

## <a name="see-also"></a>참조

* [OpenXR에 대 한 자세한 정보](https://www.khronos.org/openxr/)
* [OpenXR Provisional 0.90 사양](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)
* [OpenXR Provisional 0.90 API 참조](https://www.khronos.org/registry/OpenXR/specs/0.90/man/html/)
* [OpenXR Provisional 0.90 헤더](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)
* [OpenXR Provisional 0.90 빠른 참조 가이드](https://www.khronos.org/registry/OpenXR/specs/0.90/refguide/OpenXR-0.90-web.pdf)
