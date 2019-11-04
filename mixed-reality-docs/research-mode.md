---
title: HoloLens 연구 모드
description: 응용 프로그램은 HoloLens의 연구 모드를 사용 하 여 키 장치 센서 스트림 (깊이, 환경 추적 및 IR 반사)에 액세스할 수 있습니다.
author: davidgedye
ms.author: dgedye
ms.date: 05/03/2018
ms.topic: article
keywords: 연구 모드, cv, rs4, 컴퓨터 비전, 연구, HoloLens
ms.openlocfilehash: 307df0c226221422f13af09d8f4944c22ead3865
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438307"
---
# <a name="hololens-research-mode"></a>HoloLens 연구 모드

> [!NOTE]
> 이 기능은 HoloLens 용 [Windows 10 4 월 2018 업데이트](release-notes-april-2018.md) 의 일부로 추가 되었으며 이전 릴리스에서는 사용할 수 없습니다.

연구 모드는 장치의 키 센서에 대 한 응용 프로그램 액세스를 제공 하는 HoloLens의 새로운 기능입니다. 다음이 포함됩니다.
- 지도 작성 및 헤드 추적을 위해 시스템에서 사용 하는 네 가지 환경 추적 카메라입니다.
- 깊이 카메라 데이터의 두 가지 버전으로, 자주 사용 하는 빈도 (30FPS) 근거리 검출에 사용 되 고, 자주 사용 되는 (1-5 FPS), 더 낮은 주파수 (FPS)의 경우 현재 공간 매핑에서 사용 됩니다.
- HoloLens에서 깊이를 계산 하는 데 사용 되는 IR 반사 스트림의 두 가지 버전이 며, 이러한 이미지는 HoloLens에서 발생 하며 주변 광원의 영향을 받지 않습니다.

![연구 모드 앱 스크린샷](images/sensor-stream-viewer.jpg)<br>
*연구 모드에서 사용할 수 있는 8 개의 센서 스트림을 표시 하는 테스트 응용 프로그램의 혼합 현실 캡처*

## <a name="device-support"></a>장치 지원

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>기능과</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
    </tr>
     <tr>
        <td>연구 모드</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="before-using-research-mode"></a>연구 모드를 사용 하기 전에

연구 모드의 이름은 다음과 같습니다 .이는 Computer Vision 및 로봇 공학의 필드에서 새로운 아이디어를 시도 하는 교육 및 산업 연구원을 위한 것입니다.  연구 모드는 기업 전체에 배포 되거나 Microsoft Store에서 제공 되는 응용 프로그램에는 적합 하지 않습니다. 이는 연구 모드에서 장치 보안을 낮추고 정상적인 작업 보다 훨씬 더 많은 배터리 전원을 소비 하기 때문입니다. Microsoft는 향후 장치에서이 모드를 지원 하기 위해 커밋하지 않습니다. 따라서 새 아이디어를 개발 하 고 테스트 하는 데 사용 하는 것이 좋습니다. 그러나 연구 모드를 사용 하는 응용 프로그램은 광범위 하 게 배포할 수 없으며 향후 하드웨어에서 계속 작동 한다는 보장이 없습니다.

## <a name="enabling-research-mode"></a>연구 모드 사용

연구 모드는 개발자 모드의 하위 모드입니다. 먼저 설정 앱에서 개발자 모드를 사용 하도록 설정 해야 합니다 (**개발자를 위한 & 보안 >의 설정 > 업데이트**).

1. "개발자 기능 사용"을 **On** 으로 설정
2. "장치 포털 사용"을 **켜기** 로 설정 합니다.

그런 다음 HoloLens와 동일한 Wi-fi 네트워크에 연결 된 웹 브라우저를 사용 하 여 HoloLens의 IP 주소로 이동 합니다 ( **설정 > 네트워크 & 인터넷 > wi-fi > 하드웨어 속성**). 이는 [장치 포털](using-the-windows-device-portal.md)이며 포털의 "시스템" 섹션에서 "연구 모드" 페이지를 찾을 수 있습니다.

HoloLens 장치 포털의 ![연구 모드 탭](images/ResearchModeDevPortal.png)<br>
*HoloLens 장치 포털의 연구 모드*

**센서 스트림에 대 한 액세스 허용**을 선택한 후에는 HoloLens를 다시 부팅 해야 합니다. 이 작업은 장치 포털의 페이지 맨 위에 있는 "전원" 메뉴 항목 아래에서 수행할 수 있습니다.

장치를 다시 부팅 한 후에는 장치 포털을 통해 로드 된 응용 프로그램이 연구 모드 스트림에 액세스할 수 있어야 합니다.

## <a name="using-sensor-data-in-your-apps"></a>앱에서 센서 데이터 사용

응용 프로그램은 photo/video 카메라 스트림에 액세스 하는 것과 동일한 방식으로 [미디어 파운데이션](https://msdn.microsoft.com/library/windows/desktop/ms694197) 스트림을 열어 센서 스트림 데이터에 액세스할 수 있습니다. 

연구소 개발에 대해 작동 하는 모든 Api는 연구 모드 에서도 사용할 수 있습니다. 특히 응용 프로그램은 각 센서 프레임 캡처 시간에서 6DoF 공간에 HoloLens가 있는 위치를 정확 하 게 알 수 있습니다.

다양 한 연구 모드 스트림에 액세스 하는 방법, 내장 함수 및 extrinsics를 사용 하는 방법 및 [HoloLensForCV GitHub](https://github.com/Microsoft/HoloLensForCV)리포지토리에서 스트림을 기록 하는 방법을 보여 주는 샘플 응용 프로그램입니다.

## <a name="known-issues"></a>알려진 문제

HoloLensForCV 리포지토리에서 [문제 추적기](https://github.com/Microsoft/HololensForCV/issues) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

* [Microsoft 미디어 파운데이션](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [HoloLensForCV GitHub 리포지토리](https://github.com/Microsoft/HoloLensForCV)
* [Windows 디바이스 포털 사용](using-the-windows-device-portal.md)
