---
title: Windows Mixed Reality SteamVR 응용 프로그램 업데이트
description: Windows Mixed Reality 헤드셋을 사용 하 여 호환성을 최대화 하기 위해 SteamVR 응용 프로그램을 업데이트 하는 것에 대 한 모범 사례입니다.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: SteamVR, 호환성
ms.openlocfilehash: db21651df8e586edf500f0d05def4b1ea5474284
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597855"
---
# <a name="updating-your-steamvr-application-for-windows-mixed-reality"></a>Windows Mixed Reality SteamVR 응용 프로그램 업데이트

개발자가 테스트 하 고 Windows Mixed Reality 헤드셋에서 실행 SteamVR 환경이 최적화를 사용 하는 것이 좋습니다. 이 문서에서는 일반적인 향상 된 기능 개발자 경험 Windows Mixed Reality를 유용한 실행 되도록 만들 수를 설명 합니다.

## <a name="initial-setup-instructions"></a>초기 설치 지침

첫 번째 따르세요 있는지 아웃 게임 또는 앱 Windows Mixed Reality 확인 테스트를 시작 하 여 [시작 가이드입니다.](http://aka.ms/WindowsMixedRealitySteamVR)

## <a name="controller-models"></a>컨트롤러 모델
1. 앱에 컨트롤러 모델 렌더링 합니다.
    * 사용 된 [Windows Mixed Reality 동작 컨트롤러 모델](motion-controllers.md#rendering-the-motion-controller-model)
    * 로컬 get을 사용 하 여 IVRRenderModel::GetComponentState 변환 구성 요소 부분 (예: 포인터 포즈)
2. 환경을 사용 하는 손의 개념이 포함 된 Api 컨트롤러를 구분 하기 위해 입력에서 힌트를 가져와야 [(Unity 예제)](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)

## <a name="controls"></a>컨트롤

디자인 하거나 조정 하는 경우 컨트롤 레이아웃 염두를 다음 명령 집합을 예약 합니다.
1. 클릭 하는 **왼쪽 및 오른쪽 아날로그 엄지 스틱** 용으로 예약 되어 합니다 **Steam 대시보드**합니다.
2. 합니다 **Windows 단추** 홈 Windows Mixed Reality로 사용자를 항상 반환 됩니다.

가능한 경우 기본 스틱 thumb 기반 텔레포트 일치 하는 [Windows Mixed Reality 홈](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) 텔레포트 동작

## <a name="tooltips-and-ui"></a>도구 설명 및 UI

많은 VR 게임 활용 동작 컨트롤러 도구 설명 및 사용자가 게임 또는 앱에 대 한 가장 중요 한 명령이 설명에 오버레이 합니다. Windows 혼합 현실 용 응용 프로그램을 튜닝 하는 경우에이 부분에서는 Windows 컨트롤러 모델에 매핑할 도구 설명 되었는지 확인 하려면 환경 검토 하는 것이 좋습니다.

또한 없으면 컨트롤러의 이미지를 표시 하는 있는 환경에서 모든 지점 해야 Windows Mixed Reality 동작 컨트롤러를 사용 하 여 업데이트 된 이미지를 제공 합니다.

## <a name="haptics"></a>Haptics

로 시작 합니다 [Windows 10 2018 년 4 월 업데이트](release-notes-april-2018.md), haptics SteamVR Windows Mixed Reality를 환경에 대 한 지원 됩니다. 이미 SteamVR 응용 프로그램이 나 게임이 haptics에 대 한 지원이 포함 되어, 경우 지금 없이 작동 합니다 (추가 작업 없이) 사용 하 여 [Windows Mixed Reality 동작 컨트롤러](motion-controllers.md)합니다.

Windows Mixed Reality 동작 컨트롤러에는 몇 가지 다른 SteamVR 동작 컨트롤러 약간 다른 예상 보다 사용자 경험을 이어질 수 있는 선형 작동기 달리 표준 haptics 모터를 사용 합니다. 따라서 테스트 하 고 Windows Mixed Reality 동작 컨트롤러를 사용 하 여 프로그램 haptics 디자인을 튜닝 하는 것이 좋습니다. 예를 들어, 경우에 따라 짧은 햅 틱 펄스 (5 ~ 10 밀리초)는 Windows Mixed Reality 동작 컨트롤러에서 덜 눈에 띄는 합니다. 더 눈에 띄는 pulse를 얻으려면 말합니다 전원에 다시 하기 전에 긴 "click" (40-70ms)를 스핀업 모터 더 많은 시간을 주기를 보내 실험 합니다.

## <a name="launching-steamvr-apps-from-windows-mixed-reality-start-menu"></a>Windows Mixed Reality 시작 메뉴에서 SteamVR 응용 프로그램 실행

했습니다 VR 환경의 스트림을 통해 배포에 대 한 [SteamVR 베타용 Windows Mixed Reality를 업데이트](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) 최신 함께 [Windows Insider](https://insider.windows.com) RS5 항공편 SteamVR 제목에 표시 되도록 합니다 Windows Mixed Reality 시작 메뉴 "모든 앱"에서 자동으로 나열 합니다. 이러한 소프트웨어 버전이 설치를 사용 하 여 고객에 게 해당 헤드셋을 제거 하지 않고 Windows Mixed Reality 홈 내에서 직접 SteamVR 제목 이제 시작할 수 있습니다.

## <a name="windows-mixed-reality-logo"></a>Windows Mixed Reality 로고

제목에 대 한 Windows Mixed Reality 지원, 표시할 앱 방문 페이지에서 "저장소 페이지 편집" 링크를 "기본 정보" 탭을 클릭 하 고 "가상 Reality." 아래로 스크롤하여 이동 "숨길 Windows Mixed Reality"의 선택을 취소 하 고 저장소에 게시 하십시오.

## <a name="bugs-and-feedback"></a>버그 및 피드백

Windows Mixed Reality SteamVR 환경을 개선 하는 데 있어 여러분의 의견은 의미가 없습니다. 모든 피드백을 통해 버그를 제출 하세요 합니다 [Windows 피드백 허브](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback)합니다. 다음은 몇 [SteamVR 피드백이 가능한 유용한 것으로 확인 하는 방법에 대 한 팁](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr)합니다.

질문이 나 의견을 공유할 경우을 보내면에서 우리의 [Steam 포럼](http://steamcommunity.com/app/719950/discussions/)합니다.

## <a name="faqs-and-troubleshooting"></a>Faq 및 문제 해결

설정 또는 사용 경험을 재생 하는 일반적인 문제를 실행 하는 경우 [최신 문제 해결 단계를 확인 하세요](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr)합니다.

## <a name="see-also"></a>참조
* [도구 설치](install-the-tools.md)
* [헤드셋 및 중인 컨트롤러 드라이버 기록](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)
* [Windows Mixed Reality 최소 PC 하드웨어 호환성 지침](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
