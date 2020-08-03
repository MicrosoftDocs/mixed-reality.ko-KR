---
title: Windows Mixed Reality 및 새 Microsoft Edge
description: Windows Mixed Reality에서 새로운 Microsoft Edge를 준비 하세요. 에는 필요한 변경 사항, 검색할 업데이트 및 알려진 문제가 포함 됩니다.
author: mattzmsft
ms.author: mazeller
ms.date: 07/31/2020
ms.topic: article
keywords: edge, new, 몰입 형 웹, microsoft edge, browser, vr
ms.openlocfilehash: 107b825496cc318042da0e0cd9acdbe482994a69
ms.sourcegitcommit: ef0bf03833eda826ed0b884859b4573775112aba
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2020
ms.locfileid: "87476985"
---
# <a name="windows-mixed-reality-and-the-new-microsoft-edge"></a>Windows Mixed Reality 및 새 Microsoft Edge

[이제 새로운 Microsoft Edge를 다운로드할 수](https://blogs.windows.com/windowsexperience/?p=173496)있지만, 고객은 향후 몇 개월 동안 측정 된 롤아웃 방법에 따라 [Windows 10에 대 한 향후 업데이트에 설치 될 때까지 기다릴](https://blogs.windows.com/msedgedev/2020/01/15/upgrading-new-microsoft-edge-79-chromium/)수도 있습니다. 

이 뉴스를 사용 **하 여 Windows Mixed REALITY VR 헤드셋 고객이 새 Microsoft Edge에서 예측할 항목을 인식 하 고 Windows Mixed reality에서 웹 검색 환경을 개선 하는 보류 중인 업데이트를 알려 드리겠습니다**.

## <a name="introducing-the-new-microsoft-edge"></a>새 Microsoft Edge 소개

새 Microsoft Edge는 [Chromium 오픈 소스 프로젝트](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/) 를 데스크톱에 도입 하 여 고객에 게 더 나은 웹 호환성을 만들며 모든 웹 개발자가 웹의 조각화를 줄일 수 있습니다. 또한 WebVR 대신 VR 헤드셋에 대 한 몰입 형 웹 환경을 만드는 새로운 표준인 출시 시 WebXR 지원 합니다.

>[!IMPORTANT]
>최신 Windows 10 장치에 Microsoft Edge를 설치 하면 PC의 이전 (레거시) 버전이 교체 됩니다.

## <a name="getting-ready-for-the-new-microsoft-edge"></a>새 Microsoft Edge 준비

Mixed reality 홈에서 새로운 Microsoft Edge를 사용 하려는 windows Mixed Reality VR 헤드셋 고객은 mixed reality 홈의 **Win32 응용 프로그램 (예: 새 Microsoft edge)에 대 한 기본 지원을 위해 Windows 10 버전 1903 이상으로 업그레이드** 해야 합니다. Windows 업데이트를 확인 하거나 [최신 버전의 Windows 10을 수동으로 설치](https://www.microsoft.com/en-us/software-download/windows10)합니다.

Mixed reality 홈에서 가장 가능한 Microsoft Edge 환경을 사용 하는 경우, 1 월 말까지 Windows 업데이트에서 제공 되어야 하는 **2020-01 windows 10 버전 1903 용 누적 업데이트 (이상)를 사용 하 여 도착 하는 새 Microsoft edge에 대 한 일부 주요 Windows 혼합 현실 최적화**를 기다리는 것이 좋습니다.

>[!IMPORTANT]
>이러한 업데이트를 수행 하기 전에 새 Microsoft Edge를 다운로드 하도록 선택 하는 경우 Windows Mixed Reality에서 발생 하는 몇 가지 알려진 문제가 있습니다 (아래에 대해 읽어 볼 수 있음).

## <a name="known-issues"></a>알려진 문제

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a>2020-01 누적 업데이트에서 해결 된 Windows 10 버전 1903 이상 버전에서 해결 된 알려진 문제

- 새 Microsoft Edge를 포함 하 여 모든 Win32 앱을 시작 하면 헤드셋 디스플레이가 잠깐 중지 됩니다.
- Windows Mixed Reality 시작 메뉴에서 Microsoft Edge 타일이 사라집니다. "클래식 앱" 폴더에서 찾을 수 있습니다.
- 이전 Microsoft Edge의 Windows는 여전히 혼합 현실 홈을 중심으로 하지만 사용할 수 없습니다. 이러한 창을 활성화 하려고 하면 데스크톱 앱 내에서 가장자리가 시작 됩니다.
- Mixed reality 홈에서 하이퍼링크를 선택 하면 혼합 현실 홈 대신 바탕 화면에서 웹 브라우저가 시작 됩니다.
- WebVR 전시 앱은 WebVR 더 이상 지원 되지 않더라도 혼합 현실 홈에 있습니다.
- 키보드 시작 및 시각적 개체에 대 한 일반적인 개선 사항

### <a name="monitor-and-input-handling-issues"></a>모니터 및 입력 처리 문제

Windows 10 버전 1903 이상에 대 한 2020-01 누적 업데이트를 수행한 후 Windows 혼합 현실 세션 중에 **> 시스템 > 표시** 되는 설정에서 가상 모니터가 일반 물리적 모니터로 표시 됩니다. 일부 고객, 특히 실제 모니터가 둘 이상인 경우 데스크톱 레이아웃 및 입력 처리와 관련 된 문제가 발생할 수 있습니다.

**이러한 상황이 발생 하는 이유**

Windows Mixed Reality의 클래식 Win32 응용 프로그램에 대 한 지원은 [windows 10 2019 업데이트](#release-notes-may-2019.md)에서 도입 되었습니다. 이 지원을 사용 하려면 Win32 응용 프로그램을 호스트 하는 가상 모니터를 만들어야 합니다. 새 Win32 응용 프로그램이 시작 될 때마다 다른 가상 모니터를 만들어야 합니다. 불행 하 게도 가상 모니터를 만드는 작업은 헤드셋 표시를 잠깐 중지 하는 데 많이 사용 되는 작업입니다. 고객은이에 대 한 피드백을 사용자에 게 제공 하 여 불편을 경험 하 고 있습니다. 이러한 피드백 때문에 Win32 응용 프로그램의 사용이 증가 함에 따라 Windows Mixed Reality를 시작 하는 동안 3 개의 가상 모니터를 미리 할당 하 여이 중단을 방지 하 고 고객이 헤드셋 표시 중지를 발생 시 키 지 않고 최대 3 개의 동시 Win32 응용 프로그램을 시작할 수 있도록 했습니다.

**해결 방법**

일부 고객, 특히 여러 물리적 모니터를 사용 하는 고객에 게는이 가상 모니터 사전 할당을 사용 하지 않도록 설정 하는 것이 좋습니다. 고객 제어 및 선택을 제공 하기 위해 레지스트리 키 값을 변경 하는 해결 방법을 사용 하도록 설정 했습니다 (Windows 10 버전 2004에 대 한 2020-07 누적 업데이트에서 사용 가능).

>[!NOTE]
>레지스트리 키 값을 수정 하는 것은 고급 사용자를 위한 것입니다.

>[!WARNING]
>가상 모니터 미리 할당을 사용 하지 않도록 설정 하면 Windows Mixed Reality에서 Win32 응용 프로그램 (예: 스트림, 새 Microsoft Edge 또는 Google Chrome)을 시작할 때 헤드셋이 잠시 중단 될 수 있습니다.

가상 모니터 사전 할당을 사용 하지 않도록 설정 하려면:
1. Windows 10 버전 2004 2020-07 누적 업데이트에 대 한 **Windows 업데이트** 를 확인 하 고 사용 가능한 경우 업데이트를 설치 합니다.
2. **레지스트리 편집기**를 시작 합니다.
3. HKEY_CURRENT_USER \SOFTWARE\Microsoft\Windows\CurrentVersion\Holographic\PreallocateVirtualMonitors로 이동 합니다.
4. DWORD 값을 1 (기본값)에서 0 (영)으로 변경 합니다.
    * TRUE-1
    * FALSE-0

이제 가상 모니터는 미리 할당 하지 않고 Windows Mixed Reality에서 Win32 응용 프로그램을 시작 하려고 할 때 할당 됩니다. 이를 재설정 하 고 가상 모니터 사전 할당을 다시 사용 하도록 설정 하려면 DWORD 값을 1로 반환 합니다.

### <a name="additional-known-issues"></a>추가 알려진 문제

-   Windows Mixed Reality에서 열린 웹 사이트는 혼합 현실 포털이 닫히면 Microsoft Edge windows가 혼합 현실 홈에 배치 된 위치에 그대로 유지 되는 경우 손실 됩니다.
- 하이브리드 GPU 설정이 있는 Pc에서는 360 뷰어 확장을 포함 하 여 WebXR 환경을 제대로 시작 하지 못할 수 있습니다. 그래픽 카드 소프트웨어에서 기본 GPU로 전용 GPU를 선택 하면이 문제를 해결할 수 있습니다.
-   Microsoft Edge 창의 오디오는 spatialized 되지 않습니다.
-   **360 Viewer 확장 버전 2.3.8에서 수정**됨: Windows Mixed Reality에서 YouTube의 360 비디오를 열면 비디오가 헤드셋에서 왜곡 될 수 있습니다. Edge를 다시 시작 하면이 문제를 해결 하기 위해 360 뷰어 확장이 업데이트 되지 않습니다. `edge://system/`주소 표시줄에를 입력 하 고 "확장" 옆의 **확장** 단추를 선택 하 여 어떤 확장 버전이 있는지 확인할 수 있습니다.




