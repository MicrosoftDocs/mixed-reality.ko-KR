---
title: HoloLens 연구 모드
description: 응용 프로그램은 HoloLens의 연구 모드를 사용 하 여 키 장치 센서 스트림 (깊이, 환경 추적 및 IR 반사)에 액세스할 수 있습니다.
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
keywords: 연구 모드, cv, rs4, 컴퓨터 비전, 연구, HoloLens, HoloLens 2
ms.openlocfilehash: 62b82e3a36452d4b104bf04999e556ec19d2a5e3
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720399"
---
# <a name="hololens-research-mode"></a>HoloLens 연구 모드

## <a name="overview"></a>개요

연구 모드는 장치에서 키 센서에 대 한 액세스 권한을 제공 하기 위해 첫 번째 세대 HoloLens에서 도입 되었습니다. 특히 배포에 적합 하지 않은 연구 응용 프로그램에 사용 됩니다. 이제 다음 입력에서 데이터를 수집할 수 있습니다.

* **표시 되는 밝은 환경 추적 카메라** -헤드 추적 및 맵 작성을 위해 시스템에서 사용 됩니다.
* **깊이 카메라** – 다음과 같은 두 가지 모드로 작동 합니다.  
    + [손으로 추적](interaction-fundamentals.md) 하는 데 사용 되는 짧은 throw, 높은 빈도 (30fps) 근거리 감지
    + [공간 매핑에서](spatial-mapping.md) 사용 되는 긴-발생 빈도가 낮은 빈도 (1-5 FPS)
* HoloLens에서 깊이를 계산 하는 데 사용 하는 **두 가지 버전의 IR (반사 stream** ) 이러한 이미지는 적외선으로 표시 되며 주변에 표시 되는 빛의 영향을 받지 않습니다.

HoloLens 2를 사용 하는 경우 다음 입력에도 액세스할 수 있습니다.

* **가 속도계** – 시스템에서 X, Y 및 Z 축과 무게를 따라 선형 가속을 결정 하는 데 사용 됩니다.
* **Gyro** – 시스템에서 회전을 결정 하는 데 사용 됩니다.
* **지자기 센터** – 시스템에서 절대 방향을 예측 하는 데 사용 됩니다.

![연구 모드 앱 스크린샷](images/sensor-stream-viewer.jpg)<br>
*연구 모드에서 사용할 수 있는 8 개의 센서 스트림을 표시 하는 테스트 응용 프로그램의 혼합 현실 캡처*

> [!NOTE]
> [Windows 10 4 월 2018 업데이트](release-notes-april-2018.md) 의 일부로 Research 모드 기능이 추가 되었으며 이전 릴리스에서는 사용할 수 없습니다.

## <a name="usage"></a>사용

연구 모드는 Computer Vision 및 로봇 공학의 필드에서 새로운 아이디어를 탐색 하는 교육 및 산업 연구원을 위해 설계 되었습니다.  엔터프라이즈 환경에 배포 되었거나 Microsoft Store 또는 다른 배포 채널을 통해 사용할 수 있는 응용 프로그램에는 적합 하지 않습니다.

또한 Microsoft는 연구 모드 또는 동등한 기능을 향후 하드웨어 또는 OS 업데이트에서 지원 하도록 보장 하지 않습니다. 그러나이를 사용 하 여 새 아이디어를 개발 하 고 테스트 하지 않아야 합니다.

## <a name="security-and-performance"></a>보안 및 성능

연구 모드를 사용 하도록 설정 하면 일반적인 조건에서 HoloLens 2를 사용 하는 것 보다 더 많은 배터리 전력이 사용 됩니다. 이는 연구 모드 기능을 사용 하는 응용 프로그램이 실행 되 고 있지 않은 경우에도 마찬가지입니다.  응용 프로그램에서 센서 데이터를 오용 하는 경우이 모드를 사용 하도록 설정 하면 장치의 전반적인 보안이 낮아질 수도 있습니다.  장치 보안에 대 한 자세한 내용은 [HoloLens 보안 FAQ](https://docs.microsoft.com/hololens/hololens-faq-security)에서 찾을 수 있습니다.  


## <a name="device-support"></a>디바이스 지원

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    <!-- <col width="33%" /> -->
    </colgroup>
    <tr>
        <td><strong>기능</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens 1 Gen</strong></a></td>
        <!-- <td><a href="hololens2-hardware.md"><strong>HoloLens 2</strong></a></td> -->
    </tr>
     <tr>
        <td>헤드 추적 카메라</td>
        <td>✔️</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td>& IR 카메라 깊이</td>
        <td>✔️</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td>가속도계</td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td>자이로스코프</td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td>지자기 센터</td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
</table>

> [!IMPORTANT]
> HoloLens 2에 대 한 연구 모드 지원은 7 월 2020에 공개 미리 보기로 제공 될 예정 이며 위에 나열 된 모든 기능을 포함 합니다. 자세한 내용은 다시 확인 하세요. 

## <a name="enabling-research-mode"></a>연구 모드 사용

연구 모드는 개발자 모드의 확장입니다. 시작 하기 전에 연구 모드 설정에 액세스 하려면 장치의 개발자 기능을 사용 하도록 설정 해야 합니다. 

* **시작 메뉴를 열고 설정 >** 한 다음 **업데이트**를 선택 합니다.
* **개발자를 위해** 를 선택 하 고 **개발자 모드**를 사용 하도록 설정 합니다.
* 아래로 스크롤하여 **장치 포털**을 사용 하도록 설정 합니다.

개발자 기능을 사용 하도록 설정한 후에는 [장치 포털에 연결](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) 하 여 연구 모드 기능을 사용 하도록 설정 합니다.

*HoloLens 1 Gen*:

* **장치 포털**에서 **시스템 > 연구 모드로** 이동 합니다.
* **센서 스트림에 대 한 액세스 허용을**선택 합니다.
* 페이지 맨 위에 있는 **전원** 메뉴 항목에서 장치를 다시 시작 합니다.

장치를 다시 시작한 후에는 **장치 포털** 을 통해 로드 된 응용 프로그램이 연구 모드 스트림에 액세스할 수 있습니다.

![HoloLens 장치 포털의 연구 모드 탭](images/ResearchModeDevPortal.png)<br>
*HoloLens 장치 포털의 연구 모드 창*

## <a name="using-sensor-data-in-your-apps"></a>앱에서 센서 데이터 사용

*HoloLens 1 Gen*

응용 프로그램은 [미디어 파운데이션](https://msdn.microsoft.com/library/windows/desktop/ms694197)를 통해 사진 및 비디오 카메라 스트림에 액세스 하는 것과 동일한 방식으로 센서 스트림 데이터에 액세스할 수 있습니다. 

HoloLens 개발에 대해 작동 하는 모든 Api는 연구 모드 에서도 사용할 수 있습니다. 특히 응용 프로그램은 각 센서 프레임 캡처 시간에서 6DoF 공간에 HoloLens가 있는 위치를 정확 하 게 알고 있습니다.

다양 한 연구 모드 스트림에 액세스 하는 방법, [내장 함수 및 extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)를 사용 하는 방법 및 [HoloLensForCV GitHub 리포지토리](https://github.com/Microsoft/HoloLensForCV) 리포지토리에서 스트림을 기록 하는 방법에 대 한 샘플 응용 프로그램을 찾을 수 있습니다.

 > [!NOTE]
 > 이번에는 HoloLensForCV 샘플이 HoloLens 2에서 작동 하지 않습니다.

## <a name="known-issues"></a>알려진 문제

HoloLensForCV 리포지토리에서 [문제 추적기](https://github.com/Microsoft/HololensForCV/issues) 를 사용 하 여 알려진 문제를 따를 수 있습니다.

## <a name="see-also"></a>참고 항목

* [Microsoft 미디어 파운데이션](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [HoloLensForCV GitHub 리포지토리](https://github.com/Microsoft/HoloLensForCV)
* [Windows 디바이스 포털 사용](using-the-windows-device-portal.md)
