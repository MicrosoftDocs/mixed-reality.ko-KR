---
title: OpenXR 시작 하기
description: Windows Mixed Reality 및 HoloLens 2 헤드셋에서 이식 가능한 OpenXR API standard를 사용 하 여 시작 하세요.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, windows Mixed Reality OpenXR Developer Portal, DirectX, 네이티브, 네이티브 앱, 사용자 지정 엔진, 미들웨어, 시작, 101, preview 확장
ms.openlocfilehash: 7a210ce25d1e7c22710f1029aca2ca7f55a8b71c
ms.sourcegitcommit: 9de2cb11321e6517db69e8c93459a205900a2174
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163337"
---
# <a name="getting-started-with-openxr"></a>OpenXR 시작 하기

OpenXR를 사용 하 여 개발할 수 있습니다는 HoloLens 2 또는 Windows Mixed Reality 모던 헤드셋 바탕 화면입니다.  헤드셋에 액세스할 수 없는 경우 HoloLens 2 에뮬레이터 또는 Windows Mixed Reality 시뮬레이터를 대신 사용할 수 있습니다.

## <a name="getting-started-with-openxr-for-hololens-2"></a>HoloLens 용 OpenXR 시작 2

HoloLens 2 용 OpenXR 응용 프로그램 개발을 시작 하려면:

1. HoloLens 2를 설정 하거나 지침에 따라 [hololens 2 에뮬레이터의 최신 버전을 설치](using-the-hololens-emulator.md)합니다.  장치에서 최근에 OS를 업데이트 했거나 최근 에뮬레이터 이미지를 사용 하는 경우 OpenXR 1.0 준비 완료가 이미 있어야 합니다.
1. 모든 [확장이](openxr.md#roadmap) 있는 최신 OpenXR 런타임이 있는지 확인 하 고, 장치 또는 에뮬레이터 내에서 스토어 앱을 시작 하 고, 오른쪽 위에 있는 메뉴를 열고, **다운로드 및 업데이트** 를 클릭 하 고, **업데이트 가져오기**를 클릭 합니다.  이렇게 하면 HoloLens의 OpenXR 런타임이 최신 상태가 됩니다.  에뮬레이터를 사용 하는 경우 에뮬레이터 이미지를 시작할 때마다 다시 설정 되므로 [최신 버전의 HoloLens 2 에뮬레이터 이미지가](using-the-hololens-emulator.md)있는지 확인 하는 것이 가장 좋습니다.

## <a name="getting-started-with-openxr-for-windows-mixed-reality-headsets"></a>Windows Mixed Reality 용 OpenXR 시작 헤드셋

몰입 형 Windows Mixed Reality 헤드셋 용 OpenXR 응용 프로그램 개발을 시작 하려면 다음을 수행 합니다.

1. Windows Mixed Reality 최종 사용자가 OpenXR 응용 프로그램을 실행 하는 데 필요한 최소한 Windows 10 2019 업데이트 (1903)를 실행 해야 합니다.  이전 버전의 Windows 10을 사용 하는 경우 <a href="https://www.microsoft.com/software-download/windows10" target="_blank">windows 10 업데이트 길잡이</a>를 사용 하 여 업그레이드할 수 있습니다.
2. Windows Mixed Reality 헤드셋을 설정 하거나 지침에 따라 [Windows Mixed reality 시뮬레이터를 사용 하도록](using-the-windows-mixed-reality-simulator.md)설정 합니다.  Windows Mixed reality를 설정 하는 경우 혼합 현실 포털은 Windows Mixed Reality OpenXR 런타임을 자동으로 설치 합니다.  그러면 Microsoft Store 런타임이 최신 상태로 유지 됩니다.
3. 시작 메뉴에서 Mixed Reality 포털을 시작 하 여 Windows Mixed Reality OpenXR 런타임을 활성 상태로 만들고 ... 메뉴를 선택 하 고 "OpenXR 설정"을 선택 합니다.<br>
혼합 현실 포털에서 OpenXR 설정 ![](images/mixed-reality-portal-set-up-openxr.png)

Windows Mixed Reality OpenXR 런타임을 다시 활성화 해야 하는 경우 3 단계를 반복 합니다.

> [!NOTE]
> Windows Mixed Reality OpenXR 런타임은 곧 모든 Windows Mixed Reality 최종 사용자에 대해 자동으로 활성화 됩니다.

## <a name="getting-the-windows-mixed-reality-openxr-developer-portal"></a>Windows Mixed Reality OpenXR 개발자 포털 가져오기

Windows Mixed Reality OpenXR 런타임을 사용해 보려면 <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">Mixed Reality OpenXR 개발자 포털 앱</a>을 설치 하면 됩니다.  이 앱은 활성 런타임과 현재 헤드셋에 대 한 주요 정보를 제공 하는 시스템 상태 페이지와 함께 OpenXR의 다양 한 기능을 실행 하는 데모 장면을 제공 합니다.

에뮬레이터를 사용 하는 경우 "OpenXR" 페이지로 이동 하 고 "개발자 기능" 아래에서 "설치" 단추를 클릭 하 여 혼합 현실 OpenXR 개발자 포털을 설치 하는 가장 쉬운 방법은 [Windows 장치 포털](using-the-windows-device-portal.md)을 사용 하는 것입니다. (이는 실제 HoloLens 2 장치 에서도 작동 함)

![Mixed Reality OpenXR 개발자 포털 앱](images/mixed-reality-openxr-developer-portal.png)

## <a name="building-a-sample-openxr-app"></a>샘플 OpenXR 앱 빌드

OpenXR 개발에 필요한 도구를 아직 설치 하지 않은 경우 [설치](install-the-tools.md) 해야 합니다.

<a href="https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> 프로젝트는 두 개의 Visual Studio 프로젝트 파일을 포함 하는 간단한 OpenXR 샘플을 보여 줍니다 .이 샘플은 Win32 데스크톱 앱과 UWP HoloLens 2 앱 모두를 위한 것입니다.  솔루션에 HoloLens UWP 프로젝트가 포함 되어 있으므로 Visual Studio에 설치 된 [유니버설 Windows 플랫폼 개발 워크 로드](install-the-tools.md#installation-checklist) 를 통해 완전히 열어야 합니다.

패키지 및 배포의 차이로 인해 Win32 및 UWP 프로젝트 파일은 별개 이지만 각 프로젝트 내의 앱 코드는 100%가 동일 합니다.

OpenXR Win32 desktop을 빌드한 후 EXE를 사용 하면 Windows Mixed Reality 헤드셋 또는 다른 헤드셋이 든 상관 없이 OpenXR를 지 원하는 모든 데스크톱 VR 플랫폼에서 VR 헤드셋과 함께 사용할 수 있습니다.

OpenXR UWP 앱 패키지를 빌드한 후에는 HoloLens 2 장치 또는 HoloLens 2 에뮬레이터에 [해당 패키지를 배포할](using-visual-studio.md) 수 있습니다.

## <a name="integrate-the-openxr-loader-into-a-project"></a>OpenXR 로더를 프로젝트에 통합

기존 프로젝트에서 OpenXR를 시작 하려면 OpenXR loader를 포함 합니다.  로더는 장치에서 활성 OpenXR 런타임을 검색 하 고 구현 하는 핵심 함수 및 확장 기능에 대 한 액세스를 제공 합니다.

Visual Studio 프로젝트에서 [공식 OpenXR NuGet 패키지를 참조](#reference-official-openxr-nuget-package) 하거나 Khronos GitHub 리포지토리의 [공식 OpenXR loader 원본을 포함할](#include-official-openxr-loader-source) 수 있습니다.  어떤 방법을 사용 하 든 OpenXR 1.0 핵심 기능과 게시 된 `KHR`, `EXT` 및 `MSFT` 확장에 대 한 액세스를 제공 합니다.

`MSFT_preview` 확장을 시험해 보려는 경우 혼합 현실 GitHub 리포지토리에서 [Preview OpenXR 헤더를 복사할](#using-preview-extensions) 수 있습니다.

### <a name="reference-official-openxr-nuget-package"></a>공식 OpenXR NuGet 패키지 참조

<a href="https://www.nuget.org/packages/OpenXR.Loader/" target="_blank"> **OpenXR** NuGet 패키지</a> 는 미리 빌드된 OpenXR Loader를 참조 하는 가장 쉬운 방법입니다. Visual Studio C++ 솔루션의 DLL입니다.  이렇게 하면 OpenXR 1.0 핵심 기능과 게시 된 `KHR`, `EXT` 및 `MSFT` 확장에 대 한 액세스를 제공 합니다.

Visual Studio C++ 솔루션에 OpenXR NuGet 패키지 참조를 추가 하려면 다음을 수행 합니다.
1. **솔루션 탐색기**에서 OpenXR을 사용 하는 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **NuGet 패키지 관리 ...** 를 선택 합니다.
1. **찾아보기** 탭으로 전환 하 고 **OpenXR**를 검색 합니다.
1. **OpenXR** 패키지를 선택 하 고 오른쪽의 세부 정보 창에서 설치를 클릭 합니다.
1. 확인을 클릭 하 여 프로젝트에 대 한 변경 내용을 적용 합니다.
1. OpenXR API 사용을 시작 하려면 소스 파일에 `#include <openxr/openxr.h>`를 추가 합니다.

실행 중인 OpenXR API의 예제를 보려면 <a href="https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> 샘플 앱을 확인 하세요.

### <a name="include-official-openxr-loader-source"></a>공식 OpenXR 로더 원본 포함

예를 들어 추가 로더를 방지 하기 위해 직접 로더를 빌드 하려는 경우. DLL에서 공식 Khronos OpenXR loader 소스를 프로젝트로 끌어올 수 있습니다.  이렇게 하면 OpenXR 1.0 핵심 기능과 게시 된 `KHR`, `EXT` 및 `MSFT` 확장에 대 한 액세스를 제공 합니다.

여기에서 시작 하려면 <a href="https://github.com/KhronosGroup/OpenXR-SDK" target="_blank">GitHub의 Khronos OpenXR-SDK 리포지토리</a>에 있는 지침을 따르세요.  프로젝트는 CMake를 사용 하 여 빌드됩니다. MSBuild를 사용 하는 경우 사용자 고유의 프로젝트에 코드를 복사 해야 합니다.

## <a name="using-preview-extensions"></a>Preview 확장 사용

[확장 로드맵](openxr.md#roadmap) 에 나열 된 `MSFT_preview` 확장은 피드백을 수집 하기 위해 미리 보는 실험적 공급 업체 확장입니다.  이러한 확장은 개발자 장치에만 해당 되며, 실제 확장이 제공 될 때 제거 됩니다.

사용 가능한 `MSFT_preview` 확장을 사용해 보려면 다음 단계를 수행 하 여 프로젝트를 업데이트 합니다.
1. 위의 방법 중 하나를 수행 하 여 OpenXR 로더를 프로젝트에 통합 합니다.
1. 프로젝트의 standard OpenXR 헤더를 <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/openxr_preview/include/openxr" target="_blank">GitHub의 Mixed Reality OpenXR 리포지토리의 미리 보기 헤더로</a>바꿉니다.

그런 다음 대상 HoloLens 2 또는 데스크톱 PC에서 preview 확장을 활성화 합니다.
  1. 대상 장치에서 Windows 장치 포털을 사용 하도록 설정 합니다.
     * 대상 장치가 HoloLens 2 장치인 경우 대상 장치에서 [다음 지침을 따릅니다](using-the-windows-device-portal.md) .  이 경우 HoloLens 2 에뮬레이터에서 알려진 문제로 인해 다음 단계의 UI가 에뮬레이터에 표시 되지 않도록 하는 실제 헤드셋이 필요 합니다.
     * 대상 장치가 몰입 형 헤드셋 주변 기기가 첨부 된 데스크톱 PC 인 경우 대상 데스크톱 PC에서 <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-desktop#set-up-device-portal-on-windows-desktop" target="_blank">다음 지침을 따릅니다</a> .
  1. 왼쪽 창에서 **OpenXR** 탭으로 이동 하 고 **최신 Preview OpenXR runtime 사용**을 설정 합니다.  이렇게 하면 미리 보기 확장이 활성화 된 장치에서 미리 보기 런타임을 사용할 수 있습니다.

이러한 preview 확장의 설명서 및 사용 방법에 대 한 샘플은 <a href="https://github.com/Microsoft/OpenXR-MixedReality#openxr-preview-extensions" target="_blank">Mixed Reality OpenXR 리포지토리</a> 를 참조 하세요.

## <a name="troubleshooting"></a>문제 해결

OpenXR 개발을 시작 하 고 실행 하는 데 문제가 있는 경우 [문제 해결 팁](openxr-troubleshooting.md)을 확인 하세요.