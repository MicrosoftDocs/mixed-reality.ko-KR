---
title: Unreal의 QR 코드
description: Unreal에서 QR 코드 사용 가이드
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, 개발, 기능, 설명서, 가이드, 홀로그램, qr 코드
ms.openlocfilehash: 67a3a8092ab908cba6768e92ed6a0e7bd2737275
ms.sourcegitcommit: 5b802078090700e06630c8fc665fedeaa0a16eb7
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83342661"
---
# <a name="qr-codes-in-unreal"></a>Unreal의 QR 코드

HoloLens는 현실 세계의 알려진 위치에서 홀로그램을 렌더링하기 위해 월드 공간에서 QR 코드를 찾을 수 있습니다.  이는 또한 공유 경험을 만들기 위해 동일한 위치에 있는 여러 디바이스에서 홀로그램을 렌더링하는 데 사용할 수 있습니다. 

HoloLens에서 QR 감지를 사용하려면 프로젝트 설정> 플랫폼> HoloLens> 기능의 Unreal 에디터에서 "웹캠" 기능이 선택되어 있는지 확인합니다.  

StartARSession 함수로 ARSession을 시작하여 Unreal에서 QR 코드 추적을 사용하도록 옵트인합니다. 

QR 코드는 Unreal의 AR 추적 지오메트리 시스템을 통해 추적 이미지로 표시됩니다.  이것을 사용하려면 AR 추적 가능 알림 구성 요소를 Blueprint 행위자에 추가합니다. 

![QR AR 추적 가능 알림](images/unreal-spatialmapping-artrackablenotify.PNG)

그런 다음 구성 요소의 세부 정보로 이동하여 모니터링할 이벤트의 녹색 “+” 버튼을 클릭합니다.  

![QR 이벤트](images/unreal-spatialmapping-events.PNG)

여기서는 OnUpdateTrackedImage를 구독하여 QR 코드 중앙에 점을 렌더링하고 QR 코드의 인코딩 데이터를 인쇄했습니다. 

![QR 렌더링 예제](images/unreal-qr-render.PNG)

먼저 추적된 이미지를 ARTrackedQRCode에 캐스팅하여 현재 업데이트된 이미지가 QR 코드인지 확인합니다.  그런 다음 QRCode 변수를 사용하여 인코딩된 데이터를 검색할 수 있습니다.  GetLocalToWorldTransform 위치에서 QR 코드의 왼쪽 위를 검색할 수 있습니다.  GetEstimateSize를 사용하여 차원을 검색할 수 있습니다. 

모든 QR 코드에는 고유한 guid ID도 있습니다. 

![QR Guid](images/unreal-qr-guid.PNG)

## <a name="see-also"></a>참고 항목
* [QR 코드 추적](qr-code-tracking.md)
