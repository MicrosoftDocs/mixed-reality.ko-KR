---
title: 혼합 현실 캡처
description: 혼합 현실 캡처 사용에 대 한 정보입니다.
author: wguyman
ms.author: wguyman
ms.date: 10/02/2018
ms.topic: article
keywords: mrc, 혼합 현실 캡처, 사진, 비디오, 카메라, 캡처, 사용, 스트림, 라이브 스트림, 데모
ms.openlocfilehash: 7af60682f78f624e6b41ded88c8a77e70d40194c
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694507"
---
# <a name="mixed-reality-capture"></a>혼합 현실 캡처

HoloLens는 사용자에 게 실제 세계와 세계를 혼합 하는 환경을 제공 합니다. 혼합 현실 캡처 (MRC)를 사용 하면 해당 환경을 사진 또는 비디오로 캡처할 수 있습니다. 이렇게 하면 holograms를 볼 수 있도록 허용 하 여 다른 사람들과 환경을 공유할 수 있습니다. 이러한 비디오 및 사진은 첫 번째 사용자 관점에서 가져온 것입니다. 세 번째 사용자 관점은 [spectator view](spectator-view.md)를 사용 합니다.

혼합 현실 캡처에 대 한 사용 사례는 소셜 원 간에 비디오를 공유 하는 것 이상으로 이동 합니다. 비디오는 앱 사용 방법에 대해 다른 사용자에 게 지시 하는 데 사용할 수 있습니다. 개발자는 비디오 또는 스틸을 사용 하 여 재현 단계를 개선 하 고 앱 환경을 디버그할 수 있습니다.

## <a name="live-streaming-from-hololens"></a>HoloLens에서 라이브 스트리밍

[Windows 10 10 월 2018 업데이트](release-notes-october-2018.md) 는 HoloLens에 Miracast 지원을 추가 합니다. 시작 메뉴의 아래쪽에 있는 **연결** 단추를 선택 하 여 Miracast 사용 장치 및 어댑터에 대 한 선택기를 표시 합니다. 스트리밍을 시작 하려는 장치를 선택 합니다. 완료 되 면 시작 메뉴의 아래쪽에 있는 **연결 끊기** 단추를 선택 합니다.  **연결** 및 **연결 끊기** 는 빠른 작업 메뉴 에서도 사용할 수 있습니다.

[Windows 장치 포털](using-the-windows-device-portal.md) 및 [Microsoft HoloLens 부록 앱](https://www.microsoft.com/store/productId/9NBLGGH4QWNX) 은 개발자 모드의 장치에 대 한 라이브 스트리밍 옵션을 노출 합니다.

[Dynamics 365 원격 지원](https://dynamics.microsoft.com/en-us/mixed-reality/remote-assist) 에서는 HoloLens에서 원격 위치의 직원으로의 라이브 스트리밍을 지원 합니다.

## <a name="taking-mixed-reality-captures"></a>혼합 현실 캡처 수행

![시작 메뉴의 아래쪽에 있는 카메라 아이콘을 클릭 합니다.](images/cameraiconinpins-300px.png)<br>
*시작 메뉴의 아래쪽에 있는 카메라 아이콘을 클릭 합니다.*

여러 가지 방법으로 혼합 현실 캡처를 시작할 수 있습니다.
* Cortana는 현재 실행 중인 앱에 관계 없이 언제 든 지 사용할 수 있습니다. "안녕하세요. Cortana, 사진 찍기" 또는 "안녕하세요. 비디오를 중지 하려면 "안녕하세요 Cortana, 녹음 중지" 라고 표시 됩니다.
* 시작 메뉴에서 **카메라** 또는 **비디오**를 선택 합니다. [무선 탭](gestures.md#air-tap) 을 사용 하 여 기본 제공 mrc 카메라 UI를 엽니다.
* 빠른 작업 메뉴에서 **카메라** 또는 **비디오** 를 선택 하 여 기본 제공 mrc 카메라 UI를 엽니다.
* 앱은 [Windows 10 10 월 2018 업데이트](release-notes-october-2018.md), [기본 제공 MRC 카메라 UI](mixed-reality-capture-for-developers.md)를 기준으로 사용자 지정 또는를 사용 하 여 혼합 현실 캡처에 대 한 자체 UI를 노출할 수 있습니다.
* HoloLens 고유: 
    * [Windows 장치 포털](using-the-windows-device-portal.md) 에는 사진, 비디오, 라이브 스트림 및 보기 캡처를 수행 하는 데 사용할 수 있는 혼합 현실 캡처 페이지가 있습니다.
    * 현재 실행 중인 앱에 상관 없이 **볼륨 위로** 및 **볼륨 아래로** 단추를 동시에 눌러 사진을 찍습니다.
    * 비디오 기록을 시작 하려면 3 초 동안 **볼륨** 을 잡고 볼륨을 **아래로 이동** 합니다. 비디오를 중지 하려면 **볼륨 위로** 및 **볼륨 아래로** 단추를 동시에 누릅니다.
* 몰입 형 헤드셋 고유: 
    * 동작 컨트롤러를 사용 하 여 **Windows** 단추를 누른 다음 **트리거** 를 눌러 사진을 찍습니다. 
    * 동작 컨트롤러를 사용 하 여 **Windows** 단추를 누른 다음 **메뉴** 단추를 탭 하 여 비디오 기록을 시작 합니다. **Windows** 단추를 누른 후 **트리거** 를 탭 하 여 비디오 녹화를 중지 합니다.
    
>[!NOTE]
>[Windows 10 10 월 2018 업데이트](release-notes-october-2018.md) 는 블 룸 및 windows 단추가 동작 하는 방식을 변경 합니다. 업데이트 하기 전에 블 룸 제스처 또는 Windows 단추는 기록을 중지 합니다. 업데이트 후에는 블 룸 제스처 또는 Windows 단추를 클릭 하 여 시작 메뉴 (또는 앱에 있는 경우 빠른 작업 메뉴)를 엽니다. 메뉴에서 **비디오 중지** 를 선택 하 여 기록을 중지 합니다.

### <a name="limitations-of-mixed-reality-capture"></a>혼합 현실 캡처의 제한 사항

HoloLens에서 시스템은 렌더링 율을 30Hz로 제한 합니다. 그러면 앱이 일정 한 예산 예약을 유지할 필요가 없고 (최대) 30fps의 MRC 비디오 레코드의 프레임 속도와 일치 하는 MRC 용 여유 공간이 생성 됩니다.

비디오의 최대 길이는 5 분입니다.

기본 제공 MRC 카메라 UI는 한 번에 하나의 MRC 작업만 지원 합니다 (그림은 비디오 기록과 함께 사용할 수 없음).

### <a name="file-formats"></a>파일 형식

혼합 현실 Cortana 음성 명령의 캡처 및 시작 메뉴 도구는 다음과 같은 형식으로 파일을 만듭니다.

|  type  |  형식  |  확장명  |  해결 방법  |  오디오 | 
|----------|----------|----------|----------|----------|
|  사진  |  [JPEG](https://en.wikipedia.org/wiki/JPEG)  |  .jpg  |  3904x2196px (HoloLens 2)<br> 1408x792px (HoloLens)<br> 1920x1080px (몰입 형 헤드셋) |  해당 사항 없음 | 
|  비디오  |  [MPEG-4](https://en.wikipedia.org/wiki/MPEG-4)  |  .mp4  |  1920x1080px 30fps (HoloLens 2)<br> 24fps (HoloLens)에서 1216x684px<br> 1632x918px (30fps) (모던 헤드셋) |  48kHz 스테레오 | 

>[!NOTE]
>사진/비디오 카메라가 다른 응용 프로그램에서 이미 사용 중이거나 라이브 스트리밍 또는 시스템 리소스가 부족 한 경우 사진과 비디오의 해상도를 줄일 수 있습니다.

### <a name="video-stabilization"></a>비디오 안정화

기본적으로:
* 대기 시간이 0 인 비디오 안정화는 Miracast를 통한 라이브 스트리밍 시 적용 됩니다.
* 대기 시간이 긴 비디오 안정화는 기본 제공 MRC 카메라 UI, Cortana 음성 명령 및 Windows Device Portal을 사용 하 여 캡처한 비디오에 적용 됩니다.

## <a name="viewing-mixed-reality-captures"></a>혼합 현실 캡처 보기

혼합 현실 캡처 사진과 비디오는 장치의 "카메라 롤" 폴더에 저장 됩니다. 이러한 파일은 [사진 앱](see-your-photos.md#photos-app) 또는 파일 탐색기를 통해 액세스할 수 있습니다.

HoloLens에 연결 된 PC에서는[MTP를 통해](release-notes-april-2018.md#new-features-for-hololens) [Windows 장치 포털](using-the-windows-device-portal.md#mixed-reality-capture) 또는 pc의 파일 탐색기를 사용할 수도 있습니다.

[Onedrive 앱](https://www.microsoft.com/p/onedrive/9wzdncrfj1p3)을 설치 하는 경우에는 **카메라 업로드를** 켤 수 있습니다. 그러면 mrc 사진과 비디오가 onedrive를 사용 하 여 onedrive 및 다른 장치와 동기화 됩니다.

>[!NOTE]
>Windows 10 4 월 2018 업데이트를 바탕으로 사진 앱은 더 이상 사진과 비디오를 OneDrive에 업로드 하지 않습니다.

## <a name="see-also"></a>참조
* [Spectator View](spectator-view.md)
* [위치를 찾을 수 있는 카메라](locatable-camera.md)
* [개발자를 위한 혼합 현실 캡처](mixed-reality-capture-for-developers.md)
* [사진 보기](see-your-photos.md)
* [Windows 디바이스 포털 사용](using-the-windows-device-portal.md)
