---
title: Unreal의 QR 코드
description: Unreal에서 QR 코드 사용 가이드
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, 개발, 기능, 설명서, 가이드, 홀로그램, qr 코드
ms.openlocfilehash: a53fad14ab76136f1da419379dd39eca3a29701a
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376105"
---
# <a name="qr-codes-in-unreal"></a>Unreal의 QR 코드

## <a name="overview"></a>개요

HoloLens 2는 웹캠을 사용하여 세계 공간에서 QR 코드를 볼 수 있습니다. 즉, 각 코드의 실세계 위치에서 좌표계를 사용하여 스스로를 홀로그램으로 렌더링합니다.  HoloLens 2는 단일 QR 코드 외에도, 공유 경험을 만들기 위해 여러 디바이스에서 동일한 위치에 홀로그램을 렌더링할 수 있습니다. 애플리케이션에 QR 코드를 추가하기 위한 모범 사례를 따라야 합니다.

- 자동 영역
- 조명 및 배경
- 크기, 거리 및 각도 위치

QR 코드가 앱에 배치될 때 [환경 고려 사항](environment-considerations-for-hololens.md)에 특히 주의해야 합니다. 이러한 각각의 토픽에 대한 자세한 정보와 필요한 NuGet 패키지를 다운로드하는 방법에 대한 지침은 주 [QR 코드 추적](qr-code-tracking.md) 설명서에서 확인할 수 있습니다. 

## <a name="enabling-qr-detection"></a>QR 검색 사용
HoloLens 2는 웹캠을 사용하여 QR 코드를 확인해야 하므로 프로젝트 설정에서 사용하도록 설정해야 합니다.
- **편집 > 프로젝트 설정**을 열고 **플랫폼** 섹션까지 아래로 스크롤한 다음, **HoloLens**를 클릭합니다.
    + **기능** 섹션을 확장하고 **웹캠**을 선택합니다.  

또한 [ARSessionConfig 자산](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset)을 추가하여 QR 코드 추적을 옵트인해야 합니다.

사용 직전에 `UHoloLensARFunctionLibrary::StartQRCodeCapture()`를 호출하여 추적을 수동으로 사용하도록 설정해야 합니다. QR 코드 추적을 종료한 후에는 `UHoloLensARFunctionLibrary::StopCameraCapture()`를 통해 QR 코드 추적을 사용하지 않도록 설정하고 디바이스 리소스를 저장해야 합니다. 

## <a name="setting-up-a-tracked-image"></a>추적 이미지 설정

QR 코드는 Unreal의 AR 추적 기하 도형 시스템을 통해 추적 이미지로 표시됩니다. 이 작업을 수행하려면 다음을 수행해야 합니다.
1. 청사진을 만들고 **ARTrackableNotify** 구성 요소를 추가합니다.

![QR AR 추적 가능 알림](images/unreal-spatialmapping-artrackablenotify.PNG)

2. **ARTrackableNotify**를 선택하고 **세부 정보** 패널에서 **이벤트** 섹션을 확장합니다. 

![QR 이벤트](images/unreal-spatialmapping-events.PNG)

3. **추적 기하 도형 추가** 옆의 **+** 를 클릭하여 이벤트 그래프에 추가합니다.
    - [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) 구성 요소 API에서 이벤트의 전체 목록을 확인할 수 있습니다. 

![QR 렌더링 예제](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-image"></a>추적 이미지 사용
다음 이미지의 이벤트 그래프는 QR 코드의 가운데에 점을 렌더링하고 그 데이터를 출력하는 데 사용되는 **OnUpdateTrackedImage** 이벤트를 보여 줍니다. 

![QR 렌더링 예제](images/unreal-qr-render.PNG)

진행 상황은 다음과 같습니다.
1. 먼저 추적 이미지를 **ARTrackedQRCode**에 캐스트하여 현재 업데이트된 이미지가 QR 코드인지 확인합니다.  
2. 인코딩된 데이터는 **QRCode** 변수에서 검색합니다. **GetLocalToWorldTransform** 위치에서 QR 코드의 왼쪽 위를, **GetEstimateSize**로 크기를 가져올 수 있습니다. 

코드에서 [QR 코드 좌표계를 가져올 수](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code)도 있습니다.

## <a name="finding-the-unique-id"></a>고유 ID 찾기
모든 QR 코드에는 다음을 통해 찾을 수 있는 고유한 guid ID가 있습니다.
- **As ARTracked QRCode** 핀을 끌어서 놓고 검색하여 **고유 ID 가져오기**

![QR Guid](images/unreal-qr-guid.PNG)

QR 코드를 사용하기 위해서는 뒤에서 많은 작업이 필요하므로 이것이 전부는 아닙니다. 내부 작업을 더 상세히 설명하는 다음 링크를 확인해 보세요.

## <a name="see-also"></a>참고 항목
* [공간 매핑](spatial-mapping.md)
* [홀로그램](hologram.md)
* [좌표계](coordinate-systems.md)
