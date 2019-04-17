---
title: 저장 하 고 파일을 찾는
description: 찾기, 저장 및 HoloLens에 파일을 공유 하는 방법.
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: 방법, 파일 선택기, 파일, 사진, 비디오, 그림, OneDrive, 저장소, 파일 탐색기
ms.openlocfilehash: d539af29fc94fdbde0d2cf08157ae8b5ce8ad0a1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602685"
---
# <a name="saving-and-finding-your-files"></a>저장 하 고 파일을 찾는

파일 저장 및 다른 Windows 10 Desktop 및 모바일 장치에 비슷한 방식으로 관리할 수 있습니다:
* 파일 탐색기 앱을 사용 하 여 로컬 폴더에 액세스
* 앱 자체의 저장소를 내
* 특수 한 알려진 폴더 (예: 비디오 또는 음악 라이브러리)
* 앱과 파일 선택 (예: OneDrive)을 포함 하는 저장소 서비스를 사용 하 여
* MTP (미디어 전송 프로토콜) 지원을 통해 USB 통해 여 HoloLens에 연결 된 pc는 데스크톱 PC를 사용 하 여

## <a name="file-explorer"></a>파일 탐색기

이동 및 HoloLens 내에서 파일을 삭제 하려면 파일 탐색기 앱을 사용할 수 있습니다.

>[!NOTE]
>"최근" 필터를 찾을 수 없으면 파일 탐색기에서 파일을 활성화할 수 있습니다 (시계 아이콘은 왼쪽된 창에서 강조 표시). 이 해결 하려면 선택 합니다 **이 장치** (아래에 있는 시계 아이콘)을 왼쪽된 창에서 아이콘을 문서 또는 메뉴를 열고 선택 **이 장치**합니다.

## <a name="files-within-an-app"></a>앱 내에서 파일

응용 프로그램 장치에서 파일을 저장 하는 경우 해당 응용 프로그램 액세스 하는 데 사용할 수 있습니다.

### <a name="where-are-my-photosvideos"></a>내 사진/비디오 위치?

[혼합 현실 캡처](mixed-reality-capture.md) 사진 및 비디오 장치의 카메라 앨범 폴더에 저장 됩니다. 통해 액세스할 수 있습니다 이러한 합니다 [Photos 앱](see-your-photos.md#photos-app)합니다. 사진 및 비디오 OneDrive 동기화 할 사진 앱을 사용할 수 있습니다. 사진 및 동영상의 혼합 현실 캡처 페이지를 통해 액세스할 수도 있습니다는 [Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture)합니다.

### <a name="requesting-files-from-another-app"></a>다른 앱에서 요청 파일

응용 프로그램을 통해 다른 앱에서 파일을 열거나 파일을 저장 하도록 요청할 수 있습니다 [선택기 파일](app-model.md#file-pickers)합니다.

## <a name="known-folders"></a>알려진된 폴더

많은 지원 하며, HoloLens [폴더를 알려진](app-model.md#known-folders) 앱에 대 한 액세스 권한을 요청할 수 있다는입니다.

## <a name="files-in-a-service"></a>서비스에서 파일

파일을 저장 합니다 (또는 파일에 액세스) 서비스를 서비스에 연결 된 앱 설치 되어 있어야 합니다. 파일을 저장 하 고 OneDrive에서 파일에 액세스를 위해 설치 해야 합니다 [OneDrive 앱](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3)합니다.

## <a name="mtp-media-transfer-protocol"></a>MTP (미디어 전송 프로토콜)

다른 모바일 장치와 마찬가지로 HoloLens 데스크톱 PC에 연결 하 고 쉽게 전송 HoloLens 라이브러리 (사진, 비디오, 문서)에 액세스 하려면 PC에서 파일 탐색기를 엽니다.

## <a name="clarifications"></a>확인

* HoloLens 외부 하드 드라이브나 SD 카드에 연결 하는 것을 지원 하지 않습니다.
* [Windows 10 2018 년 4 월 업데이트 (RS4) HoloLens에 대 한](release-notes-april-2018.md), HoloLens 저장 및 관리 장치에서 파일에 대 한 파일 탐색기를 포함 합니다. 파일 탐색기의 추가 파일 선택기 (예를 들어 파일을 저장 하는 장치 또는 OneDrive)을 선택 하는 기능을 제공 합니다.
