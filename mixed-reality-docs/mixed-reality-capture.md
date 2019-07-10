---
title: 혼합 현실 캡처
description: 혼합된 현실 캡처를 사용 하 여 정보입니다.
author: wguyman
ms.author: wguyman
ms.date: 10/02/2018
ms.topic: article
keywords: mrc, 혼합 현실 캡처, 사진, 비디오, 카메라, 캡처, 사용량, 스트림, 라이브 스트림, 데모
ms.openlocfilehash: 7af60682f78f624e6b41ded88c8a77e70d40194c
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694507"
---
# <a name="mixed-reality-capture"></a>혼합 현실 캡처

HoloLens 사용자 혼합 디지털 세계와 실제의 경험을 제공 합니다. 혼합된 현실 캡처 (MRC)를 사용 하는 사진 또는 비디오로 캡처할 수 있습니다. 이렇게 하면 표시 된를 홀로그램을 볼 수 있도록 하 여 다른 사용자와 경험을 공유할 수 있습니다. 첫 번째 사용자의 관점에서 이러한 비디오 및 사진 이며 3 인칭 관점을 사용 하 여 [spectator 보기](spectator-view.md)합니다.

혼합된 현실 캡처에 대 한 사용 사례는 소셜 원 간에 비디오를 공유 하는 초과 이동 합니다. 앱을 사용 하는 방법에 다른 사용자에 게 지시할 비디오를 사용할 수 있습니다. 개발자는 재현 단계를 개선 하 고 앱 환경을 디버그 비디오 또는 과반수 조건이 충족 되므로 사용할 수 있습니다.

## <a name="live-streaming-from-hololens"></a>라이브 HoloLens에서 스트리밍

합니다 [Windows 10 년 10 월 2018 Update](release-notes-october-2018.md) Miracast 지원 HoloLens에 추가 합니다. 선택 된 **Connect** Miracast 지원 장치 및 어댑터에 대 한 선택기를 표시 하려면 시작 메뉴의 맨 위에 있는 단추입니다. 스트리밍을 시작 하려면 원하는 장치를 선택 합니다. 을 완료 한 후 선택 합니다 **연결 끊기** 시작 메뉴의 맨 위에 있는 단추입니다.  **연결** 하 고 **연결 끊기** 빠른 작업 메뉴에서 사용할 수 있습니다.

합니다 [Windows Device Portal](using-the-windows-device-portal.md) 하 고 [Microsoft HoloLens 도우미 앱](https://www.microsoft.com/store/productId/9NBLGGH4QWNX) 노출 라이브 스트리밍 개발자 모드에 있는 장치에 대 한 옵션입니다.

[Dynamics 365 원격 지원](https://dynamics.microsoft.com/en-us/mixed-reality/remote-assist) 원격 위치에서 직원에 게 HoloLens에서 라이브 스트리밍을 지원 합니다.

## <a name="taking-mixed-reality-captures"></a>혼합된 현실 수행 캡처

![시작 메뉴의 맨 아래에 카메라 아이콘을 클릭](images/cameraiconinpins-300px.png)<br>
*시작 메뉴의 맨 아래에 카메라 아이콘을 클릭*

여러 가지 방법으로 혼합된 현실 캡처를 시작할 수 있습니다.
* Cortana 번 사용할 수 있는 모든 현재 실행 중인 앱에 관계 없이 합니다. 단순히 "사진을 찍은 Hey Cortana" 또는 "Hey Cortana, 녹음/녹화를 시작 합니다." 비디오를 중지 하려면 예를 들어 "Hey Cortana 기록을 중지 합니다."
* 시작 메뉴에서 선택 하거나 **카메라** 하거나 **비디오**합니다. 사용 하 여 [어 탭](gestures.md#air-tap) 를 기본 제공 MRC 카메라 UI를 엽니다.
* 빠른 작업 메뉴에서 선택 하거나 **카메라** 하거나 **비디오** 를 기본 제공 MRC 카메라 UI를 엽니다.
* 앱은 고유한 UI 사용자 지정을 사용 하 여 혼합된 현실 캡처 또는의 노출할 수 있습니다 합니다 [Windows 10 년 10 월 2018 Update](release-notes-october-2018.md), [내장 MRC 카메라 UI](mixed-reality-capture-for-developers.md)합니다.
* HoloLens에 고유 합니다. 
    * [Windows Device Portal](using-the-windows-device-portal.md) 사진, 비디오, 라이브 스트림은 데 사용할 수 있으며 캡처를 보고 하는 혼합된 현실 캡처 페이지에 있습니다.
    * 두 키를 눌러 합니다 **볼륨 크게** 및 **볼륨 작게** 단추 현재 실행 중인 앱에 관계 없이 사진을 찍은를 동시에.
    * 저장 합니다 **볼륨 크게** 및 **볼륨 작게** 비디오 기록을 시작 하려면 3 초간 단추입니다. 비디오를 중지 하려면 둘 다를 탭 **볼륨 크게** 하 고 **볼륨 작게** 동시에 단추입니다.
* 고유한 몰입 형 헤드셋: 
    * 저장할 동작 컨트롤러를 사용 하는 **Windows** 단추를 누른 다음 합니다 **트리거** 여 사진을 찍습니다. 
    * 저장할 동작 컨트롤러를 사용 하는 **Windows** 단추를 누른 다음는 **메뉴** 비디오 녹화를 시작 하는 단추입니다. 저장 합니다 **Windows** 단추를 누른 다음는 **트리거** 비디오 녹화를 중지 하려면.
    
>[!NOTE]
>합니다 [Windows 10 년 10 월 2018 Update](release-notes-october-2018.md) 블 룸 및 Windows 단추 동작 하는 방법을 변경 합니다. 업데이트 이전의 Windows 단추를 블 룸 제스처는 기록을 중지 합니다. 업데이트 후 bloom 제스처 또는 Windows 단추 열립니다 시작 메뉴 (또는 빠른 작업 메뉴는 앱의 경우). 메뉴에서 선택 **중지 비디오** 기록을 중지 합니다.

### <a name="limitations-of-mixed-reality-capture"></a>혼합된 현실 캡처의 제한 사항

HoloLens에서 시스템 30 Hz 위해의 렌더링 속도가 제한 됩니다. 앱 상수 예산 예약, 유지 필요가 없도록 하려면 MRC 한 일부 여유가 만들고 MRC 비디오 녹화 framerate 30fps (를) 일치 합니다.

비디오는 5 분의 최대 길이 합니다.

기본 제공 MRC 카메라 UI에만 한 번에 단일 MRC 작업을 지 원하는 사진 촬영 이어서 비디오 기록에서 함께 사용할 수 없습니다.

### <a name="file-formats"></a>파일 형식

Cortana 음성 명령에서 혼합된 현실 캡처하고 시작 메뉴 도구에서는 다음 형식으로 파일을 만듭니다.

|  형식  |  형식  |  확장명  |  해결 방법  |  오디오 | 
|----------|----------|----------|----------|----------|
|  사진  |  [JPEG](https://en.wikipedia.org/wiki/JPEG)  |  .jpg  |  3904x2196px (HoloLens 2)<br> 1408x792px (HoloLens)<br> 1920x1080px<br> (몰입 형 헤드셋) |  해당 사항 없음 | 
|  비디오  |  [MPEG-4](https://en.wikipedia.org/wiki/MPEG-4)  |  .mp4  |  1920x1080px<br> 30fps (HoloLens 2)<br> 1216x684px 24 fps (HoloLens)에서<br> 1632x918px 30fps (몰입 형 헤드셋) |  48kHz Stereo | 

>[!NOTE]
>시스템 리소스가 부족 하거나 사진/비디오 카메라를 라이브 스트리밍하는 동안 다른 응용 프로그램에서 사용 하 여 이미 하는 경우에 사진 및 비디오의 해상도 작을 수 있습니다.

### <a name="video-stabilization"></a>비디오 안정화

기본적으로:
* 대기 시간이 없는 비디오 안정화 Miracast를 통한 스트리밍 라이브 상태일 때 적용 됩니다.
* 대기 시간이 긴 비디오 안정화 기본 제공 MRC 카메라 UI, Cortana 음성 명령, 및 Windows Device Portal 사용 하 여 캡처된 비디오에 적용 됩니다.

## <a name="viewing-mixed-reality-captures"></a>캡처 혼합된 현실 보기

혼합된 현실 캡처 사진 및 비디오 장치의 "카메라 앨범" 폴더에 저장 됩니다. 통해 액세스할 수 있습니다 이러한 합니다 [Photos 앱](see-your-photos.md#photos-app) 또는 파일 탐색기.

HoloLens에 연결 된 PC에 사용할 수도 있습니다 [Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture) 또는 PC의 파일 탐색기 ([MTP 통해](release-notes-april-2018.md#new-features-for-hololens)).

설치 하는 경우는 [OneDrive 앱](https://www.microsoft.com/p/onedrive/9wzdncrfj1p3)를 켤 수 있습니다 **카메라 업로드** MRC 사진 및 비디오 OneDrive 및 OneDrive를 사용 하 여 다른 장치에 동기화 됩니다.

>[!NOTE]
>부터 Windows 10 2018 년 4 월 업데이트 사진 앱은 더 이상 사진 및 비디오 OneDrive에 업로드 합니다.

## <a name="see-also"></a>참조
* [Spectator View](spectator-view.md)
* [위치를 찾을 수 있는 카메라](locatable-camera.md)
* [개발자를 위한 혼합 현실 캡처](mixed-reality-capture-for-developers.md)
* [사진 보기](see-your-photos.md)
* [Windows 디바이스 포털 사용](using-the-windows-device-portal.md)
