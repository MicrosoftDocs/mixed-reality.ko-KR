---
title: OpenXR
description: 혼합 현실 OpenXR Developer Preview를 사용 하 여 임시 OpenXR 0.90 API를 사용해 보세요.
author: thetuvix
ms.author: alexturn
ms.date: 3/18/2019
ms.topic: article
keywords: 혼합된 현실 OpenXR 개발자 미리 보기
ms.openlocfilehash: 723b0b85785d4b6dd735430aa76a24b9ce05b5c7
ms.sourcegitcommit: 8d6e5723283c03f984f1fafef81afa5aab5d04bc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66039178"
---
# <a name="openxr"></a>OpenXR

열려 있는 비독점적 무료 표준 OpenXR [Khronos](https://www.khronos.org/) 걸쳐 있는 많은 공급 업체에서 광범위 한 장치에 대 한 기본 액세스를 제공 하는 [혼합된 현실 스펙트럼](mixed-reality.md).

OpenXR, 여기 실제로 있는 것 처럼 실제 환경에서 디지털 콘텐츠를 배치 하는 holographic 장치 (예: HoloLens 2) 뿐만 아니라 숨기는 몰입 형 장치 (예: 데스크톱 Pc에 대 한 Windows Mixed Reality 헤드셋)를 대상으로 하는 응용 프로그램을 구축할 수 있습니다는 실제 디지털 경험을으로 바꿉니다.  OpenXR으로 수행 되 면 다음 이식 가능한 다양 한 범위의 하드웨어 플랫폼 간에 코드를 작성할 수 있습니다.

OpenXR 표준 된 임시 단계에서 현재 사용자 의견에 대 한 릴리스는 초기 OpenXR 0.90 사양입니다.  OpenXR에 대 한 액세스에 대 한 자세한 내용은 합니다 [provisional 0.90 사양](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html) 및 [헤더](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)를 참조 합니다 [Khronos OpenXR 페이지](https://www.khronos.org/openxr/). 

HoloLens 2 또는 혼합 현실 OpenXR Developer Preview를 사용 하 여 데스크톱 PC에서 provisional OpenXR 0.90 API를 시도해 볼 수 있습니다.  이 초기 런타임 대상 응용 프로그램을 OpenXR 0.90 API HoloLens 2 또는 Windows Mixed Reality 몰입 형 헤드셋 바탕 화면에서 적용할 수 있습니다.

헤드셋에는 액세스할 수 없는 경우 대신 사용할 수 있습니다 HoloLens 2 에뮬레이터 또는 Windows Mixed Reality 시뮬레이터입니다.

## <a name="setting-up-the-mixed-reality-openxr-developer-preview-for-hololens-2"></a>HoloLens 2에 대 한 혼합 현실 OpenXR 개발자 미리 보기 설정

HoloLens 2에서 혼합 현실 OpenXR Developer Preview를 사용 하 여 시작 하기:

1. HoloLens 2를 설정 하거나 지침에 따라 [HoloLens 2 에뮬레이터를 설치할](using-the-hololens-emulator.md)합니다.
1. 장치 또는 에뮬레이터 내에서 스토어 앱을 시작 하 고 모든 앱이 업데이트 되었는지 확인 합니다.  혼합 현실 OpenXR 개발자 미리 보기 사용에 대 한 장치에서 앱을 사용 하 여 설치 합니다.  참조 하려는 경우 에뮬레이터를 사용 합니다 [에뮬레이터에 지침이 입력](using-the-hololens-emulator.md#basic-emulator-input) 에뮬레이터 내에서 스토어 앱을 사용할 수 있습니다.

## <a name="setting-up-the-mixed-reality-openxr-developer-preview-for-immersive-desktop-headsets"></a>혼합 현실 OpenXR Developer Preview 데스크톱 몰입 형 헤드셋에 대 한 설정

데스크톱 PC에서 혼합 현실 OpenXR Developer Preview를 사용 하 여 시작 하기:

1. Windows를 실행 하는 해야 10 년 10 월 2018 Update (1809) 또는 Windows 10 2019 업데이트할 수 (1903).  Windows 10의 이전 버전의 경우 월 2019로 업그레이드할 수 있습니다 사용 하 여 업데이트 합니다 [Windows 10 업데이트 도우미](https://www.microsoft.com/en-us/software-download/windows10)합니다.
1. Windows Mixed Reality 헤드셋을 설정 하거나 지침에 따라 [Windows Mixed Reality 시뮬레이터를 사용 하도록 설정](using-the-windows-mixed-reality-simulator.md)합니다.
1. 설치 합니다 [OpenXR 개발자 혼합된 현실 앱 미리 보기](https://www.microsoft.com/store/productId/9n5cvvl23qbt)합니다.  이 앱에서는 설정 OpenXR 런타임 미리 보기를 사용 하 여 windows 10 년 10 월 2018 Update (1809) 이상.  이 앱을 설치한 후 Windows 스토어는 런타임이 최신 상태로 유지 합니다.
1. 시작 메뉴에서 혼합 현실 OpenXR 개발자 미리 보기 앱을 실행 하 고 런타임 활성화 하려면 지침을 따릅니다.  곧이 앱 뿐만 아니라 다른 OpenXR 디버그 정보를 확인할 수 됩니다.

![혼합된 현실 OpenXR 개발자 앱 미리 보기](images/mixed-reality-openxr-developer-preview.png)

### <a name="support-for-windows-10-october-2018-update"></a>Windows 10 년 10 월 2018 Update에 대 한 지원

Windows를 실행 하는 경우 (1903) 업데이트 하 고 위의 단계를 수행 하는 10 월 2019, 혼합 현실 OpenXR Developer Preview를 사용할 준비가 됩니다!

라면 준비가 [월 2019를 데스크톱 PC를 업그레이드 업데이트](https://www.microsoft.com/en-us/software-download/windows10), windows 작업할 수 있습니다 10 년 10 월 2018 하나 더 많은 단계를 수행 하 여 (1809) 업데이트:

1. 혼합 현실 OpenXR Developer Preview를 설치 하려면 위의 단계를 수행 합니다.
1. 혼합 현실 OpenXR Developer Preview 시스템의 현재 OpenXR runtime을 설정 하려면 다음을 설치 합니다 [혼합 현실 OpenXR 개발자 미리 보기 호환성 팩](https://aka.ms/openxr-compat)합니다.

## <a name="building-a-sample-openxr-app"></a>샘플 OpenXR 앱 빌드

합니다 [BasicXrApp](https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp) 프로젝트 두 Visual Studio 프로젝트 파일을 모두 Win32 데스크톱 앱 및 UWP HoloLens 2 앱에 대 한 하나를 사용 하 여 간단한 OpenXR 샘플을 보여 줍니다.  솔루션 HoloLens UWP 프로젝트에 포함 되어 있으므로 필요 합니다 [유니버설 Windows 플랫폼 개발 워크 로드](install-the-tools.md#installation-checklist) 열려는 완벽 하 게 Visual Studio에 설치 합니다.

Win32와 UWP 프로젝트 파일은 별도 패키징 및 배포, 각 프로젝트 내에서 응용 프로그램 코드의 차이로 인해는 100% 동일 note!

## <a name="feedback"></a>사용자 의견

피드백을 제공 하는 [OpenXR 임시 0.90 사양](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)를 방문 하십시오 합니다 [Khronos OpenXR 포럼](https://community.khronos.org/c/openxr), [#openxr Slack 채널](https://khr.io/slack) 및 [사양 문제 추적기](https://github.com/KhronosGroup/OpenXR-Docs/issues)합니다.

## <a name="troubleshooting"></a>문제 해결

다음은 혼합 현실 OpenXR Developer Preview에 대 한 몇 가지 문제 해결 팁입니다.  다른 문제가 발생 하면, 방문 하십시오 합니다 [Khronos OpenXR 포럼](https://community.khronos.org/c/openxr) 또는 [#openxr Slack 채널](https://khr.io/slack)합니다.

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>Windows Mixed Reality를 시작 하지 않는 OpenXR 앱

OpenXR 앱이 실행 시 Windows Mixed Reality 시작 되지 않음, 경우 혼합 현실 OpenXR 개발자 미리 보기에 활성 런타임에으로 설정할 수 있습니다.  혼합 현실 OpenXR 개발자 미리 보기 앱을 실행 하 고 지침에 따라 런타임에 활성화를 해야 합니다.

### <a name="mixed-reality-openxr-developer-preview-app-cannot-be-installed"></a>혼합된 현실 OpenXR 개발자 미리 보기 앱을 설치할 수 없습니다. 

실행 하는 최소 Windows 해야 10 년 10 월 2018 (1809)을 업데이트 합니다.  Windows 10의 이전 버전의 경우 월 2019로 업그레이드할 수 있습니다 (1903) 사용 하 여 업데이트 합니다 [Windows 10 업데이트 도우미](https://www.microsoft.com/en-us/software-download/windows10)합니다.

혼합 현실 OpenXR 개발자 미리 보기 앱에서 단추를 설치 하는 경우는 Windows에서 아무 작업도 수행 10 년 10 월 2018 업데이트, 시스템 앱에 대 한 오래 된 시스템 요구 사항 캐싱되어 있습니다.  명령을 실행할 수 있습니다 `wsreset.exe` 캐시를 지우려면 명령 프롬프트에서.

## <a name="see-also"></a>참조

* [OpenXR 대 한 자세한 정보](https://www.khronos.org/openxr/)
* [OpenXR 임시 0.90 사양](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)
* [OpenXR 임시 0.90 API 참조](https://www.khronos.org/registry/OpenXR/specs/0.90/man/html/)
* [OpenXR 임시 0.90 헤더](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)
* [OpenXR 임시 0.90 빠른 참조 가이드](https://www.khronos.org/registry/OpenXR/specs/0.90/refguide/OpenXR-0.90-web.pdf)
