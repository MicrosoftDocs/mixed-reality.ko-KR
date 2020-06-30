---
title: Unreal의 공간 매핑
description: Unreal의 공간 매핑 사용 가이드
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, 개발, 기능, 설명서, 가이드, 홀로그램, 공간 매핑
ms.openlocfilehash: ffa57749cd96e240ac4812f950f4e13a6dbc68bd
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720409"
---
# <a name="spatial-mapping-in-unreal"></a>Unreal의 공간 매핑

## <a name="overview"></a>개요
공간 매핑을 사용하면 HoloLens 주위의 세계를 표시하여 실제 세계의 표면에 개체를 배치함으로써 홀로그램이 사용자에게 더 현실감 있게 보이도록 할 수 있습니다. 또한 공간 매핑은 실제 세계의 심도 큐를 사용하여 사용자의 세계에 개체를 고정합니다. 이렇게 하면 사용자가 이러한 홀로그램이 사실은 홀로그램의 공간에 있음을 알게 됩니다. 즉, 공간에 떠 있거나 사용자를 따라 이동하는 홀로그램이 실제처럼 느껴지지 않습니다. 가능한 모든 상황에서 편안하게 항목을 배치하려 합니다.

공간 매핑 품질, 배치, 폐색, 렌더링 등에 대한 자세한 내용은 [공간 매핑](spatial-mapping.md) 문서에서 확인할 수 있습니다.

## <a name="enabling-spatial-mapping"></a>공간 매핑 사용

HoloLens에서 공간 매핑을 사용하려면 다음을 수행합니다.
- **편집 > 프로젝트 설정**을 열고 **플랫폼** 섹션까지 아래로 스크롤합니다.    
    + **HoloLens**를 선택하고 **공간 인식**을 선택합니다.

공간 매핑을 옵트인하고 HoloLens 게임에서 **MRMesh**를 디버깅하려면 다음을 수행합니다.
1. **ARSessionConfig**를 열고 **ARSettings > 세계 매핑** 섹션을 확장합니다. 

2. **추적된 기하 도형에서 메시 데이터 생성**을 선택합니다. 즉, HoloLens 플러그 인이 비동기로 공간 매핑 데이터를 가져오고 **MRMesh**를 통해 Unreal에 보냅니다. 
3. **MRMesh**에 있는 모든 삼각형의 흰색 와이어 프레임 윤곽선을 표시하려면 **와이어 프레임에서 메시 데이터 렌더링**을 선택합니다. 

![Spatial Anchors 저장소 준비](images/unreal-spatialmapping-arsettings.PNG)


## <a name="spatial-mapping-at-runtime"></a>런타임에 공간 매핑
다음 매개 변수를 수정하여 공간 매핑 런타임 동작을 업데이트할 수 있습니다.

- **편집 > 프로젝트 설정**을 열고 **플랫폼** 섹션까지 아래로 스크롤한 다음, **HoloLens > 공간 매핑**을 선택합니다. 

![Spatial Anchors 프로젝트 설정](images/unreal-spatialmapping-projectsettings.PNG)

- **입방미터당 최대 삼각형 수**는 공간 매핑 메시의 삼각형 밀도를 업데이트합니다.  
- **공간 메싱 볼륨 크기**는 공간 매핑 데이터를 렌더링하고 업데이트할 플레이어 주변의 큐브 크기입니다.  
    + 애플리케이션 런타임 환경이 클 것으로 예상된다면 이 값이 실제 공간과 일치하게 커야 합니다.  반대로 애플리케이션이 사용자 바로 주변의 표면에만 홀로그램을 배치하면 되는 경우에는 이 값이 더 작아도 됩니다. 사용자가 월드를 걸어 다닐 때 공간 매핑 볼륨이 함께 이동합니다. 

## <a name="working-with-mrmesh"></a>MRMesh 작업
런타임에 **MRMesh**에 액세스하려면 다음을 수행합니다.
1. **ARTrackableNotify** 구성 요소를 청사진 행위자에 추가합니다. 

![Spatial Anchors AR 추적 가능 알림](images/unreal-spatialmapping-artrackablenotify.PNG)

2. **ARTrackableNotify** 구성 요소를 선택하고 **세부 정보** 패널에서 **이벤트** 섹션을 확장합니다. 
    - 모니터링할 이벤트에서 **+** 단추를 클릭합니다. 

![Spatial Anchors 이벤트](images/unreal-spatialmapping-events.PNG)

이 경우 **추적된 기하 도형 추가** 이벤트가 모니터링되며 공간 매핑 데이터에 일치하는 유효한 세계 메시를 찾습니다. [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) 구성 요소 API에서 이벤트의 전체 목록을 확인할 수 있습니다. 

청사진 이벤트 그래프 또는 C++에서 메시의 재질을 변경할 수 있습니다. 아래의 스크린샷은 청사진 경로를 보여 줍니다. 

![Spatial Anchors 예제](images/unreal-spatialmapping-example.PNG)

아래 코드에 표시된 것처럼 C++에서 `OnTrackableAdded` 대리자를 구독하여 가능한 즉시 `ARTrackedGeometry`를 가져올 수 있습니다. 

> [!IMPORTANT]
> 프로젝트 build.cs 파일의 **PublicDependencyModuleNames** 목록에 **AugmentedReality**가 **반드시** 있어야 합니다.
> - 여기에는 **UARTrackedGeometry**의 **MRMesh** 구성 요소를 검사할 수 있는 **ARBlueprintLibrary** 및 **MRMeshComponent**가 포함됩니다. 

![Spatial Anchors 예제 C++ 코드](images/unreal-spatialmapping-examplecode.PNG)

공간 매핑이 **ARTrackedGeometries**를 통해 표시되는 유일한 데이터 형식은 아닙니다. 공간 매핑 기하 도형인 `EARObjectClassification` 및 `World`도 확인할 수 있습니다. 

업데이트 및 제거 이벤트에 대한 비슷한 대리자로 
- `AddOnTrackableUpdatedDelegate_Handle` 
- `AddOnTrackableRemovedDelegate_Handle`을 차례로 클릭합니다. 

[UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html) API에서 이벤트의 전체 목록을 확인할 수 있습니다.

## <a name="see-also"></a>참고 항목
* [공간 매핑](spatial-mapping.md)
