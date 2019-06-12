---
title: HoloLens 연구 모드
description: HoloLens에서 연구 모드를 사용 하 여 응용 프로그램 주요 장치 센서 스트림 (깊이, 추적, 환경 및 IR 반사) 액세스할 수 있습니다.
author: davidgedye
ms.author: dgedye
ms.date: 05/03/2018
ms.topic: article
keywords: 모드, cv, rs4, 컴퓨터 비전, HoloLens 연구 조사
ms.openlocfilehash: e9a7683f8d582b459185066e74655e8f2b236db4
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829928"
---
# <a name="hololens-research-mode"></a>HoloLens 연구 모드

> [!NOTE]
> 일부로이 기능이 추가 되었습니다 합니다 [Windows 10 2018 년 4 월 업데이트](release-notes-april-2018.md) HoloLens에 대 한는 이전 버전에서 사용할 수 없습니다.

Research 모드는 HoloLens 장치에서 키 센서에 대 한 응용 프로그램 액세스를 제공 하는의 새로운 기능입니다. 이러한 개체는 다음과 같습니다.
- 네 가지 환경 맵 빌드 및 헤드 추적에 대 한 시스템에서 사용 하는 카메라를 추적 합니다.
- 두 버전에 대 한 높은 빈도 (30 FPS) 깊이 거의 감지 일반적으로 사용 되는 추적에 직접 및 낮은 빈도 (1 FPS) 먼 깊이 감지에 대 한 다른의 깊이 카메라 데이터의 현재 공간 매핑 사용
- 이러한 이미지는 HoloLens에서 표시등이 되며 합리적으로 영향을 받지 한 앰비언트 조명으로 깊이 있지만 그 자체로 유용을 계산 하는 HoloLens에서 사용 하는 IR 반사 스트림의 두 가지 버전입니다.

![Research 모드 앱 스크린 샷](images/sensor-stream-viewer.jpg)<br>
*연구 모드에서 사용할 수 있는 8 개 센서 스트림을 표시 하는 테스트 응용 프로그램의 혼합된 현실 캡처*

## <a name="device-support"></a>장치 지원

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>기능</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>몰입 형 헤드셋</strong></a></td>
    </tr>
     <tr>
        <td>연구 모드</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="before-using-research-mode"></a>연구 모드를 사용 하기 전에

연구 모드 라는 잘: Computer Vision 및 로봇 공학의 필드에 새로운 아이디어를 사용해 교육 및 산업 연구원이 위한 것입니다.  엔터프라이즈 배포 하거나 Microsoft Store 사용할 수 있는 응용 프로그램에 대 한 연구 모드를 사용 하는 것이 없습니다. 이 대 한 이유는 연구 모드 장치의 보안을 줄이고 하 고 일반적인 작업 보다 훨씬 더 많은 배터리 전원 소모입니다. 이후 모든 장치에서이 모드를 지원 하기 위해 Microsoft 커밋하지 않는 합니다. 따라서 좋습니다 개발 하 고 새로운 아이디어; 테스트 사용 그러나 광범위 하 게 연구 모드를 사용 하거나 계속 이후 하드웨어에서 작동 하는 모든 보증 하는 응용 프로그램을 배포할 수 없습니다.

## <a name="enabling-research-mode"></a>연구 모드를 사용 하도록 설정

Research 모드는 개발자 모드의 하위 모드입니다. 설정 앱의 개발자 모드를 사용 하도록 설정 하려면 먼저 (**설정 > 업데이트 및 보안 > 개발자를 위한**):

1. "개발자 기능을 사용 합니다."로 **에서**
2. "장치 포털을 사용 합니다."로 **에서**

에 HoloLens의 IP 주소로 이동 후에 HoloLens와 같은 Wi-fi 네트워크에 연결 된 웹 브라우저를 사용 하 여 (수집한 **설정 > 네트워크 및 인터넷 > Wi-fi > 하드웨어 속성**). 이 [장치 포털](using-the-windows-device-portal.md), 포털의 "System" 섹션에서 "연구 모드" 페이지를 찾을 수 있습니다.

![HoloLens 장치 포털의 연구 Mode 탭](images/ResearchModeDevPortal.png)<br>
*HoloLens 장치 포털에서 연구 모드*

선택한 후 **센서 스트림에 대 한 액세스 허용**, HoloLens 다시 부팅 해야 합니다. 장치 포털 페이지의 맨 위에 있는 "Power" 메뉴 항목에서에서이 수행할 수 있습니다.

장치 다시 부팅 된 후 장치 포털을 통해 로드 된 응용 프로그램 연구 모드 스트림에 액세스할 수 있어야 합니다.

## <a name="using-sensor-data-in-your-apps"></a>앱에서 센서 데이터를 사용 하 여

응용 프로그램 열어 센서 스트림 데이터를 액세스할 수 있습니다 [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) 사진/비디오 카메라 스트림에 액세스 하는 동일한 방식으로 스트림 합니다. 

HoloLens 개발을 위한 작동 하는 모든 Api 연구 모드에 있을 때 사용할 수 있습니다. 특히 응용 프로그램은 정확 하 게 HoloLens 인 6DoF 공간에서 각 센서 프레임 캡처 시간의 파악할 수 있습니다.

다양 한 연구 모드 스트림에 액세스 하는 방법, extrinsics, 고 내장 함수를 사용 하는 방법 및 스트림을 기록 하는 방법을 보여 주는 샘플 응용 프로그램에서 사용할 수는 [HoloLensForCV GitHub 리포지토리](https://github.com/Microsoft/HoloLensForCV)합니다.

## <a name="known-issues"></a>알려진 문제

참조를 [문제 추적기](https://github.com/Microsoft/HololensForCV/issues) HoloLensForCV 리포지토리에 있습니다.

## <a name="see-also"></a>참조

* [Microsoft Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [HoloLensForCV GitHub 리포지토리](https://github.com/Microsoft/HoloLensForCV)
* [Windows 디바이스 포털 사용](using-the-windows-device-portal.md)
