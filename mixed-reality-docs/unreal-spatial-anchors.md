---
title: Unreal의 Spatial Anchors
description: Unreal의 공간 앵커 사용 가이드
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, 개발, 기능, 설명서, 가이드, 홀로그램, 공간 앵커
ms.openlocfilehash: c35d8efc9998aac5b40de833e5acbf7f80353e6b
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840142"
---
# <a name="spatial-anchors-in-unreal"></a>Unreal의 Spatial Anchors

공간 앵커는 애플리케이션 세션 사이의 실제 공간에서 홀로그램을 유지하는 데 사용됩니다.  이는 Unreal을 통해 ARPins로 표시되며 향후 세션에서 로드될 HoloLens의 앵커 저장소에 저장됩니다. 

앵커를 저장하거나 로드하기 전에 먼저 앵커 저장소가 준비되었는지 확인합니다.  앵커 저장소가 준비되기 전에 HoloLens 앵커 기능을 호출하려고 시도해도 성공하지 못합니다.  

![Spatial Anchors 저장소 준비](images/unreal-spatialanchors-store-ready.PNG)

## <a name="save-anchors"></a>앵커 저장

세계에 고정해야 하는 구성 요소가 애플리케이션에 있으면 다음 순서에 따라 앵커 저장소에 저장할 수 있습니다. 

![Spatial Anchors 저장](images/unreal-spatialanchors-save.PNG)

여기에서는 행위자를 알려진 위치에 생성하고, 그 위치와 행위자의 클래스를 기반으로 한 이름을 가진 ARPin을 만들고, 행위자를 ARPin에 추가하고, 핀을 HoloLens 앵커 저장소에 저장합니다.  선택한 앵커 이름은 고유해야 하므로 이 예제에서는 현재 타임 스탬프를 추가합니다.  앵커가 앵커 저장소에 성공적으로 저장한 경우, 시스템 > 맵 관리자 > 디바이스에 저장된 앵커 파일에서 HoloLens 디바이스 포털에서 검사할 수 있습니다. 

## <a name="load-anchors"></a>앵커 로드

애플리케이션이 시작되면 다음 Blueprint를 호출하여 구성 요소를 앵커 위치에 복원할 수 있습니다.

![Spatial Anchors 로드](images/unreal-spatialanchors-load.PNG)

이 예제에서는 앵커 저장소의 모든 앵커를 반복하고, 행위자를 ID에 생성하고, 앵커 저장소의 ARPin에 행위자를 고정합니다.  앵커는 홀로그램이 저장된 위치를 기준으로 홀로그램 위치를 다시 설정하는 것을 담당하므로 행위자를 ID에 생성하는 것이 중요합니다. 따라서 여기에 추가된 변환은 앵커에 오프셋을 추가합니다. 

앵커 ID는 앵커의 저장된 이름에 따라 다른 행위자가 생성될 수 있도록 쿼리되기도 합니다. 

## <a name="remove-anchors"></a>앵커 제거 

앵커로 작업이 완료되면 향후 세션에 포함되지 않도록 전체 앵커 저장소를 지우거나 앵커 저장소에서 개별 앵커를 제거할 수 있습니다. 

![Spatial Anchors 제거](images/unreal-spatialanchors-remove.PNG)

## <a name="see-also"></a>참고 항목
* [공간 앵커](spatial-anchors.md)
* [좌표계](coordinate-systems.md)
