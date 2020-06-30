---
title: Unreal의 Spatial Anchors
description: Unreal의 공간 앵커 사용 가이드
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, 개발, 기능, 설명서, 가이드, 홀로그램, 공간 앵커
ms.openlocfilehash: 58394f4e27aff5070d55ed5f0d62cd81ff579d1f
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720319"
---
# <a name="spatial-anchors-in-unreal"></a>Unreal의 Spatial Anchors

## <a name="overview"></a>개요

공간 앵커는 애플리케이션 세션 사이의 실제 공간에서 홀로그램을 저장하는 데 사용됩니다.  이는 Unreal을 통해 **ARPin**으로 표시되며 향후 세션에 로드될 HoloLens의 앵커 저장소에 저장됩니다. 

## <a name="checking-the-anchor-store"></a>앵커 저장소 확인

앵커를 저장하거나 로드하기 전에 먼저 앵커 저장소가 준비되었는지 확인해야 합니다.  앵커 저장소가 준비되기 전에는 HoloLens 앵커 함수의 호출에 성공하지 못합니다.  

![Spatial Anchors 저장소 준비](images/unreal-spatialanchors-store-ready.PNG)

## <a name="saving-anchors"></a>앵커 저장

세계에 고정해야 하는 구성 요소가 애플리케이션에 있으면 다음 순서에 따라 앵커 저장소에 저장할 수 있습니다. 

![Spatial Anchors 저장](images/unreal-spatialanchors-save.PNG)

상세 구분:
1. 알려진 위치에 행위자를 생성합니다.
2. 행위자의 클래스를 기준으로 해당 위치와 이름을 사용하여 **ARPin**을 만듭니다. 
3. **ARPin**에 행위자를 추가하고 HoloLens 앵커 저장소에 핀을 저장합니다.  
    * 선택한 앵커 이름은 고유해야 하며 이 예제에서는 현재 타임스탬프를 추가합니다. 

4. 앵커가 앵커 저장소에 성공적으로 저장된 경우, **시스템 > 맵 관리자 > 디바이스에 저장된 앵커 파일**에서 해당 항목을 HoloLens 장치 포털에서 검사할 수 있습니다. 

## <a name="loading-anchors"></a>앵커 로드

애플리케이션이 시작되면 다음 청사진을 사용하여 구성 요소를 앵커 위치에 복원할 수 있습니다.

![Spatial Anchors 로드](images/unreal-spatialanchors-load.PNG)

상세 구분:
1. 앵커 저장소의 모든 앵커에 대해 반복합니다. 
2. ID에서 행위자를 생성합니다.
3. 해당 행위자를 앵커 저장소에서 **ARPin**에 고정합니다.  

    * 앵커는 홀로그램이 저장된 위치를 기준으로 홀로그램 위치를 다시 설정하는 것을 담당하므로 행위자를 ID에 생성하는 것이 중요합니다. 여기에 추가된 변환은 앵커에 오프셋을 추가합니다. 

앵커 ID는 앵커의 저장된 이름에 따라 다른 행위자가 생성될 수 있도록 쿼리되기도 합니다. 

## <a name="removing-anchors"></a>앵커 제거 

앵커 작업을 마치면 **WMRAnchor 저장소에서 ARPin 제거** 및 **WMRAnchor 저장소 모든 ARPin 제거** 구성 요소를 통해 개별 앵커 또는 전체 앵커 저장소를 지울 수 있습니다.

![Spatial Anchors 제거](images/unreal-spatialanchors-remove.PNG)

> [!NOTE]
> 공간 앵커가 아직 베타 버전이므로 업데이트된 정보 및 기능을 다시 확인해야 합니다.

## <a name="see-also"></a>참고 항목
* [공간 앵커](spatial-anchors.md)
* [좌표계](coordinate-systems.md)
