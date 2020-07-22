---
title: OpenXR 시작
description: Windows Mixed Reality 및 HoloLens 2 헤드셋에서 이식 가능한 OpenXR API standard를 사용 하 여 시작 하세요.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, Windows Mixed Reality OpenXR 개발자 도구, DirectX, 네이티브, 네이티브 앱, 사용자 지정 엔진, 미들웨어, 시작, 101, preview 확장, OpenXR runtime 버전, 시스템 상태
ms.openlocfilehash: e09ff2748921789d74bafdb321f19882336ea500
ms.sourcegitcommit: 3c32f45fd941767d408cccc5a76f1ff1cec763da
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86879239"
---
# <a name="getting-started-with-openxr"></a>OpenXR 시작

OpenXR를 사용 하 여 개발할 수 있습니다는 HoloLens 2 또는 Windows Mixed Reality 모던 헤드셋 바탕 화면입니다.  헤드셋에 액세스할 수 없는 경우 HoloLens 2 에뮬레이터 또는 Windows Mixed Reality 시뮬레이터를 대신 사용할 수 있습니다.

## <a name="getting-started-with-openxr-for-hololens-2"></a>HoloLens 용 OpenXR 시작 2

HoloLens 2 용 OpenXR 응용 프로그램 개발을 시작 하려면:

1. HoloLens 2를 설정 하거나 지침에 따라 [hololens 2 에뮬레이터의 최신 버전을 설치](using-the-hololens-emulator.md)합니다.  장치에서 최근에 OS를 업데이트 했거나 최근 에뮬레이터 이미지를 사용 하는 경우 OpenXR 1.0 준비 완료가 이미 있어야 합니다.
1. 모든 [확장이](openxr.md#roadmap) 있는 최신 OpenXR 런타임이 있는지 확인 하 고, 장치 또는 에뮬레이터 내에서 **스토어** 앱을 시작 하 고, 오른쪽 위에 있는 메뉴를 열고, **다운로드 및 업데이트** 를 클릭 하 고, **업데이트 가져오기**를 클릭 합니다.  이렇게 하면 HoloLens의 OpenXR 런타임이 최신 상태가 됩니다.  에뮬레이터를 사용 하는 경우 에뮬레이터 이미지를 시작할 때마다 다시 설정 되므로 [최신 버전의 HoloLens 2 에뮬레이터 이미지가](using-the-hololens-emulator.md)있는지 확인 하는 것이 가장 좋습니다.

## <a name="getting-started-with-openxr-for-windows-mixed-reality-headsets"></a>Windows Mixed Reality 용 OpenXR 시작 헤드셋

몰입 형 Windows Mixed Reality 헤드셋 용 OpenXR 응용 프로그램 개발을 시작 하려면 다음을 수행 합니다.

1. Windows Mixed Reality 최종 사용자가 OpenXR 응용 프로그램을 실행 하는 데 필요한 최소한 Windows 10 2019 업데이트 (1903)를 실행 해야 합니다.  이전 버전의 Windows 10을 사용 하는 경우 <a href="https://www.microsoft.com/software-download/windows10" target="_blank">windows 10 업데이트 길잡이</a>를 사용 하 여 업그레이드할 수 있습니다.
2. Windows Mixed Reality 헤드셋을 설정 하거나 지침에 따라 [Windows Mixed reality 시뮬레이터를 사용 하도록](using-the-windows-mixed-reality-simulator.md)설정 합니다.

이것으로 끝입니다.  Windows Mixed Reality OpenXR 런타임은 모든 Windows Mixed Reality 사용자에 대해 자동으로 설치 되 고 활성화 됩니다.  그런 다음 Microsoft Store는 런타임을 최신 상태로 유지 합니다.

Windows Mixed Reality OpenXR 런타임을 다시 활성화 해야 하는 경우 시작 메뉴에서 혼합 현실 포털을 시작 하 고 ... 메뉴 왼쪽 아래에서 "OpenXR 설정"을 선택 합니다.  해당 메뉴 항목이 없으면 OpenXR 런타임이 이미 활성 상태입니다.<br>
![Mixed Reality 포털에서 OpenXR 설정](images/mixed-reality-portal-set-up-openxr.png)

## <a name="getting-the-windows-mixed-reality-openxr-developer-tools"></a>Windows Mixed Reality OpenXR 개발자 도구 가져오기

Windows Mixed Reality OpenXR 런타임을 사용해 보려면 <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">Mixed Reality OpenXR 개발자 도구 앱</a>을 설치 하면 됩니다.  이 앱은 활성 런타임과 현재 헤드셋에 대 한 주요 정보를 제공 하는 시스템 상태 페이지와 함께 OpenXR의 다양 한 기능을 실행 하는 데모 장면을 제공 합니다.

HoloLens 2 에뮬레이터를 사용 하는 경우 혼합 현실 OpenXR 개발자 도구를 설치 하는 가장 쉬운 방법은 "OpenXR" 페이지로 이동한 다음 "개발자 기능"에서 "설치" 단추를 클릭 하 여 [Windows 장치 포털](using-the-windows-device-portal.md)을 사용 하는 것입니다. (이는 실제 HoloLens 2 장치 에서도 작동 함)

![혼합 현실 OpenXR 개발자 도구 앱](images/mixed-reality-openxr-developer-tools.png)

## <a name="building-a-sample-openxr-app"></a>샘플 OpenXR 앱 빌드

OpenXR 개발에 필요한 도구를 아직 설치 하지 않은 경우 [설치](install-the-tools.md) 해야 합니다.

<a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> 프로젝트는 두 개의 Visual Studio 프로젝트 파일이 포함된 간단한 OpenXR 샘플을 보여주며, 두 파일 중 하나는 Win32 데스크톱 앱용이고 다른 하나는 UWP HoloLens 2 앱용입니다.  솔루션에 HoloLens UWP 프로젝트가 포함 되어 있으므로 Visual Studio에 설치 된 [유니버설 Windows 플랫폼 개발 워크 로드](install-the-tools.md#installation-checklist) 를 통해 완전히 열어야 합니다.

패키지 및 배포의 차이로 인해 Win32 및 UWP 프로젝트 파일은 별개 이지만 각 프로젝트 내의 앱 코드는 거의 동일 합니다.

OpenXR Win32 desktop을 빌드한 후 EXE를 사용 하면 Windows Mixed Reality 헤드셋 또는 다른 헤드셋이 든 상관 없이 OpenXR를 지 원하는 모든 데스크톱 VR 플랫폼에서 VR 헤드셋과 함께 사용할 수 있습니다.

OpenXR UWP 앱 패키지를 빌드한 후에는 HoloLens 2 장치 또는 HoloLens 2 에뮬레이터에 [해당 패키지를 배포할](using-visual-studio.md) 수 있습니다.

## <a name="integrate-the-openxr-loader-into-a-project"></a>OpenXR 로더를 프로젝트에 통합

기존 프로젝트에서 OpenXR를 시작 하려면 OpenXR loader를 포함 합니다.  로더는 장치에서 활성 OpenXR 런타임을 검색 하 고 구현 하는 핵심 함수 및 확장 기능에 대 한 액세스를 제공 합니다.

Visual Studio 프로젝트에서 [공식 OpenXR NuGet 패키지를 참조](#reference-official-openxr-nuget-package) 하거나 Khronos GitHub 리포지토리의 [공식 OpenXR loader 원본을 포함할](#include-official-openxr-loader-source) 수 있습니다.  어느 방법을 사용 하 든 OpenXR 1.0 핵심 기능과 게시 된 확장 및 확장에 대 한 액세스를 제공 `KHR` `EXT` `MSFT` 합니다.

확장도 시험해 보려는 경우 `MSFT_preview` 혼합 현실 GitHub 리포지토리에서 [preview OpenXR 헤더를 복사할](#using-preview-extensions) 수 있습니다.

### <a name="reference-official-openxr-nuget-package"></a>공식 OpenXR NuGet 패키지 참조

<a href="https://www.nuget.org/packages/OpenXR.Loader/" target="_blank"> **OpenXR** NuGet 패키지</a> 는 미리 빌드된 OpenXR Loader를 참조 하는 가장 쉬운 방법입니다. Visual Studio c + + 솔루션의 DLL입니다.  그러면 OpenXR 1.0 핵심 기능과 게시 된 `KHR` `EXT` 확장 및 확장에 액세스할 수 있습니다 `MSFT` .

Visual Studio c + + 솔루션에 OpenXR NuGet 패키지 참조를 추가 하려면 다음을 수행 합니다.
1. **솔루션 탐색기**에서 OpenXR을 사용 하는 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **NuGet 패키지 관리 ...** 를 선택 합니다.
1. **찾아보기** 탭으로 전환 하 고 **OpenXR**를 검색 합니다.
1. **OpenXR** 패키지를 선택 하 고 오른쪽의 세부 정보 창에서 설치를 클릭 합니다.
1. 확인을 클릭 하 여 프로젝트에 대 한 변경 내용을 적용 합니다.
1. `#include <openxr/openxr.h>`OPENXR API를 사용 하 여 시작 하려면 소스 파일에를 추가 합니다.

실행 중인 OpenXR API의 예제를 보려면 <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> 샘플 앱을 확인 하세요.

### <a name="include-official-openxr-loader-source"></a>공식 OpenXR 로더 원본 포함

예를 들어 추가 로더를 방지 하기 위해 직접 로더를 빌드 하려는 경우. DLL에서 공식 Khronos OpenXR loader 소스를 프로젝트로 끌어올 수 있습니다.  그러면 OpenXR 1.0 핵심 기능과 게시 된 `KHR` `EXT` 확장 및 확장에 액세스할 수 있습니다 `MSFT` .

여기에서 시작 하려면 <a href="https://github.com/KhronosGroup/OpenXR-SDK" target="_blank">GitHub의 Khronos OpenXR-SDK 리포지토리</a>에 있는 지침을 따르세요.  프로젝트는 CMake를 사용 하 여 빌드됩니다. MSBuild를 사용 하는 경우 사용자 고유의 프로젝트에 코드를 복사 해야 합니다.

## <a name="using-preview-extensions"></a>Preview 확장 사용

`MSFT_preview` [확장 로드맵](openxr.md#roadmap) 에 나열 된 확장은 피드백을 수집 하기 위해 미리 보는 실험적 공급 업체 확장입니다.  이러한 확장은 개발자 장치에만 해당 되며, 실제 확장이 제공 될 때 제거 됩니다.

사용 가능한 확장을 사용해 보려는 경우 다음 단계를 수행 하 여 `MSFT_preview` 프로젝트를 업데이트 합니다.
1. 위의 방법 중 하나를 수행 하 여 OpenXR 로더를 프로젝트에 통합 합니다.
1. 프로젝트의 standard OpenXR 헤더를 <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/openxr_preview/include/openxr" target="_blank">GitHub의 Mixed Reality OpenXR 리포지토리의 미리 보기 헤더로</a>바꿉니다.

그런 다음 대상 HoloLens 2 또는 데스크톱 PC에서 preview 확장 지원을 활성화 합니다.
  1. 모든 [확장이](openxr.md#roadmap) 있는 최신 OpenXR 런타임이 있는지 확인 하 고, 대상 장치 또는 에뮬레이터 내에서 **스토어** 앱을 시작 하 고, 오른쪽 위의 메뉴를 열고, **다운로드 및 업데이트** 를 클릭 하 고, **업데이트 가져오기**를 클릭 합니다.
  1. 대상 장치에서 Windows 장치 포털을 사용 하도록 설정 합니다.
     * 대상 장치가 HoloLens 2 장치인 경우 대상 장치에서 [다음 지침을 따릅니다](using-the-windows-device-portal.md) .  이 경우 HoloLens 2 에뮬레이터에서 알려진 문제로 인해 다음 단계의 UI가 에뮬레이터에 표시 되지 않도록 하는 실제 헤드셋이 필요 합니다.
     * 대상 장치가 몰입 형 헤드셋 주변 기기가 첨부 된 데스크톱 PC 인 경우 대상 데스크톱 PC에서 <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-desktop#set-up-device-portal-on-windows-desktop" target="_blank">다음 지침을 따릅니다</a> .
  1. 왼쪽 창에서 **OpenXR** 탭으로 이동 하 고 **최신 Preview OpenXR runtime 사용**을 설정 합니다.  이렇게 하면 미리 보기 확장이 활성화 된 장치에서 미리 보기 런타임을 사용할 수 있습니다.
     ![Device Portal OpenXR preview runtime 확인란](images/device-portal-openxr-preview-runtime.png)
  1. [Windows Mixed Reality OpenXR 개발자 도구](openxr-getting-started.md#getting-the-windows-mixed-reality-openxr-developer-tools) 의 **시스템 상태** 탭에 표시 된 **런타임 버전이** 현재 시도 하려는 preview 확장의 필수 버전과 일치 하는지 확인 합니다.  그렇다면 **확장 목록에 확장 프로그램이 표시** 됩니다.  안정적인 확장을 사용할 수 있게 되 면 미리 보기 확장이 제거 됩니다.<br />
     ![Mixed Reality OpenXR 개발자 도구 앱 시스템 상태 탭](images/mixed-reality-openxr-developer-tools-status.png)

이러한 preview 확장의 설명서 및 사용 방법에 대 한 샘플은 <a href="https://github.com/microsoft/OpenXR-MixedReality#openxr-preview-extensions" target="_blank">Mixed Reality OpenXR 리포지토리</a> 를 참조 하세요.

## <a name="troubleshooting"></a>문제 해결

OpenXR 개발을 시작 하 고 실행 하는 데 문제가 있는 경우 [문제 해결 팁](openxr-troubleshooting.md)을 확인 하세요.