---
title: Windows Mixed Reality 및 새 Microsoft Edge
description: Windows Mixed Reality에서 새로운 Microsoft Edge를 준비 하세요. 에는 필요한 변경 사항, 검색할 업데이트 및 알려진 문제가 포함 됩니다.
author: mattzmsft
ms.author: mazeller
ms.date: 01/15/2020
ms.topic: article
keywords: edge, new, 몰입 형 웹, microsoft edge, browser, vr
ms.openlocfilehash: 2576762786c9234377308f226036c830e01d9133
ms.sourcegitcommit: d73d9012941fa1b13eb7d2f45ccc481d6365827a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76885625"
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

### <a name="additional-known-issues"></a>추가 알려진 문제

-   Windows Mixed Reality에서 열린 웹 사이트는 혼합 현실 포털이 닫히면 Microsoft Edge windows가 혼합 현실 홈에 배치 된 위치에 그대로 유지 되는 경우 손실 됩니다.
-   Microsoft Edge 창의 오디오는 spatialized 되지 않습니다.
-   **360 Viewer 확장 버전 2.3.8에서 수정**됨: Windows Mixed Reality에서 YouTube의 360 비디오를 열면 비디오가 헤드셋에서 왜곡 될 수 있습니다. Edge를 다시 시작 하면이 문제를 해결 하기 위해 360 뷰어 확장이 업데이트 되지 않습니다. 주소 표시줄에 `edge://system/`를 입력 하 고 "확장" 옆의 **확장** 단추를 선택 하 여 어떤 확장 버전이 있는지 확인할 수 있습니다.
-   Windows Mixed Reality 세션 중에는 설정 > 시스템 > 디스플레이에서 일반 물리적 모니터로 가상 모니터가 표시 됩니다.



