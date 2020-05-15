---
title: Unreal의 공간 매핑
description: Unreal의 공간 매핑 사용 가이드
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, 개발, 기능, 설명서, 가이드, 홀로그램, 공간 매핑
ms.openlocfilehash: 32f8247010745b23bf73c5161c378bc1284169ef
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840082"
---
# <a name="spatial-mapping-in-unreal"></a>Unreal의 공간 매핑

HoloLens에서 공간 매핑을 사용하려면 Unreal 편집기의 프로젝트 설정> 플랫폼> HoloLens> 기능에서 "공간 인식" 기능을 선택해야 합니다.  

HoloLens 게임에서 공간 매핑을 사용하도록 옵트인하려면 ARSessionConfig에서 "Generate Mesh Data from Tracked Geometry(추적 지오메트리에서 메시 데이터 생성)"을 사용하도록 설정합니다.  그러면 HoloLens 플러그 인은 공간 매핑 데이터를 비동기적으로 가져와서 MRMesh를 통해 Unreal에 표시합니다. 

![Spatial Anchors 저장소 준비](images/unreal-spatialmapping-arsettings.PNG)

공간 매핑 메시의 디버그 시각화를 보려면 ARSessionConfig에서 "Render Mesh Data in Wireframe(와이어프레임에서 메시 데이터 렌더링)" 확인란을 선택하여 MRMesh에 있는 모든 삼각형의 흰색 와이어프레임 윤곽선을 표시합니다. 

프로젝트 설정 > Platform > HoloLens > 공간 매핑에서 다음 매개 변수를 수정하여 공간 매핑의 런타임 동작을 업데이트할 수 있습니다. 

![Spatial Anchors 프로젝트 설정](images/unreal-spatialmapping-projectsettings.PNG)

입방미터당 최대 삼각형 수는 공간 매핑 메시의 삼각형 밀도를 업데이트합니다.  공간 메싱 볼륨 크기는 공간 매핑 데이터를 렌더링하고 업데이트할 플레이어 주변의 큐브 크기를 나타냅니다.  애플리케이션 런타임 환경이 클 것으로 예상된다면 이 필드는 실제 공간과 일치하도록 커야 합니다.  반대로 애플리케이션이 사용자 바로 주변의 표면에만 홀로그램을 비추면 되는 경우에는 이 필드가 작아도 됩니다.  사용자가 월드를 걸어 다닐 때 공간 매핑 볼륨이 함께 이동합니다. 

런타임에 MRMesh에 대한 액세스 권한을 얻으려면 먼저 다음과 같이 AR 추적 가능 알림 구성 요소를 청사진 행위자에 추가합니다. 

![Spatial Anchors AR 추적 가능 알림](images/unreal-spatialmapping-artrackablenotify.PNG)

그런 다음, 구성 요소의 세부 정보로 이동하여 모니터링할 이벤트의 녹색 “+” 단추를 클릭합니다. 

![Spatial Anchors 이벤트](images/unreal-spatialmapping-events.PNG)

여기서는 다음과 같이 On Add Tracked Geometry 이벤트를 모니터링하면서 공간 매핑 데이터에 해당하는 유효한 월드 메시를 찾고, 메시의 재질을 변경합니다. 

![Spatial Anchors 예제](images/unreal-spatialmapping-example.PNG)

C++에서는 OnTrackableAdded 대리자를 구독하여 ARTrackedGeometry가 사용 가능하 게 되는 즉시 받을 수 있습니다.  업데이트 및 제거 이벤트에 대한 비슷한 대리자로 AddOnTrackableUpdatedDelegate_Handle 및 AddOnTrackableRemovedDelegate_Handle이 있습니다. 

![Spatial Anchors 예제 C++ 코드](images/unreal-spatialmapping-examplecode.PNG)

프로젝트의 build.cs에는 “ARBlueprintLibrary.h”를 포함할 PublicDependencyModuleNames의 “AugmentedReality”와 UARTrackedGeometry의 MRMesh 구성 요소를 검사할 “MRMesh”기 있어야 합니다. 

공간 매핑은 ARTrackedGeometries를 통해 표시되는 유일한 데이터 형식이 아니므로, 먼저 EARObjectClassification이 공간 매핑 지오메트리를 나타내는 월드인지 확인합니다. 

## <a name="see-also"></a>참고 항목
* [공간 매핑](spatial-mapping.md)
