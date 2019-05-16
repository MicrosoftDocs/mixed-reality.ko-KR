---
title: 지점 및 실습을 사용 하 여 커밋
description: 지점 및 커밋 입력된 모델 개요
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: 지금까지 가리키고 커밋 혼합 현실을, 상호 작용, 디자인, hololens, 실습,
ms.openlocfilehash: e69c8ff2091beff7d8fbbde4e6f24d909302290a
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730810"
---
# <a name="point-and-commit-with-hands"></a>지점 및 실습을 사용 하 여 커밋
지점 및 실습을 사용 하 여 커밋은 사용자가 대상으로 선택 하 고 거리의 2D 콘텐츠 및 3D 개체를 조작할 수 있는 입력된 모델. 이 "훨씬" 상호 작용 방법이 혼합된 현실에 고유한 및 방식으로 사용자를 자연스럽 게은 실제 세계와 intereact 합니다. 슈퍼 hero 동영상에 예를 들어 *X Men*, 문자 [마그네틱](https://en.wikipedia.org/wiki/Magneto_(comics)) 연락 박수를 사용 하 여 거리가 먼 개체를 조작할 수 있습니다. 이 사람이 실제로 수행할 수 있습니다. HoloLens (AR) 및 혼합 현실 VR ()에서 주요 holographic 콘텐츠로 매력적인 환경을 뿐만 아니라 더 효과적이 고 효율적인 상호 작용 하도록 실제 세계의 물리적 제한을이 마법의 power 사용 하 여 사용자를 장착할 했습니다.

## <a name="device-support"></a>장치 지원

입력된 모델 | [HoloLens (첫 번째 범용)](https://docs.microsoft.com/en-us/windows/mixed-reality/hololens-hardware-details) | HoloLens 2 | [몰입 형 헤드셋](https://docs.microsoft.com/en-us/windows/mixed-reality/immersive-headset-hardware-details) |
| ---------| -----| ----- | ---------|
지점 및 커밋 (맨 위 상호 작용) | 지원 되지 않습니다 ❌ | 권장 ✔️ | 권장 ✔️

지점 및 커밋 라고도 바늘까지 중 하나인 새 명확 하 고 직접 추적 시스템을 활용 하는 새로운 기능입니다. 이 입력된 모델 동작 컨트롤러를 사용 하 여 몰입 형 헤드셋에서 기본 입력된 모델 이기도합니다.

## <a name="hand-rays"></a>직접 표면이

HoloLens 2에는 팜의 가운데에서 발사 직접 광선을 만들었습니다. 이 광선 손 모양 아이콘이의 확장으로 취급 됩니다. 도넛 모양 커서는 대상 개체를 사용 하 여 광선과 교차 하는 위치를 나타내는 광선의 끝에 연결 됩니다. 그런 다음 커서에서 도착 하는 개체에서 손 모양 아이콘이 gestural 명령의 받을 수 있습니다.

엄지와 집게 손가락 어 탭 작업을 수행 하 여이 기본 gestural 명령은 트리거됩니다. 직접 광선 가리키고 어 탭을 커밋를 사용 하 여 사용자가 단추 또는 하이퍼링크는 웹 콘텐츠를 활성화할 수 있습니다. 자세한 복합 제스처를 사용 하 여 사용자가 웹 콘텐츠를 탐색 하 고 거리에서 3D 개체를 조작할 수 있습니다. 이러한 지점 및 커밋 상태를 설명 하 고 아래 표시 된 것으로 직접 광선의 시각적 디자인도 대응 해야: 

* 에 *가리키는* 상태 이면 광선이 파선 이며 커서 도넛 모양입니다.
* 에 *커밋* 상태 이면 광선이 실선으로 바뀌고 커서 점으로 축소 합니다.

![](images/Hand-Rays-720px.jpg)

## <a name="transition-between-near-and-far"></a>거의 및 끝 사이 전환

"집게 손가락으로 가리키는"와 같은 특정 제스처를 사용 하는 대신 아웃 손바닥을 해제 하 고 자세한 조작 제스처에 대 한 5 개의 손가락 예약의 가운데에서와 같은 축소 이동해 서 오는 광선 설계 했습니다 광선과 보내도록 합니다. 이 디자인을 만들겠습니다. 멘 탈 모델 하나만 근거리 및 원거리 상호 작용에 대 한 손 제스처의 동일한 집합에 정확 하 게 지원 합니다. 다른 거리에 있는 개체를 조작 하는 동일한 잡기 제스처를 사용할 수 있습니다. 방사선 호출에는 자동 및 근접 기반입니다.

*  개체 내의 거리 (약 50 cm)에 도달 하는 arm 경우 방사선 거의 상호 작용에 대 한 장려 자동으로 해제 되어 있습니다.
*  개체가 50 cm 보다 더 강력 하 고 방사선 켜 집니다. 원활 하 게 전환 해야 합니다.

![](images/Transition-Between-Near-And-Far-720px.jpg)

## <a name="2d-slate-interaction"></a>2D 슬레이트 상호 작용

2D 슬레이트는 holographic 컨테이너 2D 앱 콘텐츠를 웹 브라우저와 같은 호스팅. 훨씬 2D 슬레이트를 상호 작용 하기 위한 디자인 개념 직접 광선 대상 및 air tap를 사용 하 여 선택 하는 것입니다. 을 대상으로 하는 직접 빛을 사용 하 여 후 사용자에 어 탭을 하이퍼링크 또는 단추를 트리거할 수 있습니다. 한편 "누르기 및 끌기 어" 하는 데 사용할 수 슬레이트 콘텐츠를 아래로 스크롤합니다. 두 손을 사용 하 여 탭 하 고 끌어서 어 상대적 동작에 슬레이트 콘텐츠 확대할 수 있습니다.

모서리와 가장자리에 직접 광선을 대상으로 하는 가장 가까운 조작 유도성을 표시 됩니다. "잡기, 끌기" 조작 affordances, 사용자가 수행할 수 있습니다 uniform 모퉁이 affordances 통해 크기 조정 및 edge affordances 통해 슬레이트 원래 대로 되돌릴 수 있습니다. 2D 슬레이트의 맨 위에 있는 holobar 위치와 방향을 잃기 사용자가 이동할 수 전체 슬레이트입니다.

![](images/2D-Slate-Interaction-Far-720px.jpg)

2D 조작 하기 위한 자체를 슬레이트:<br>

* 사용자가 직접 광선 모퉁이 또는 가장자리를 가장 가까운 조작 유도성 표시를 가리킵니다. 
* 유도성에서 조작 제스처를 적용 하 여 사용자 모퉁이 유도성 통해 균일 한 크기 조정을 수행할 수 있습니다 및 edge 유도성 통해 슬레이트 원래 대로 되돌릴 수 있습니다. 
* 2D 슬레이트의 맨 위에 있는 holobar에서 조작 제스처를 적용 하 여 사용자가 전체 슬레이트를 이동할 수 있습니다.<br>

<br>

## <a name="3d-object-manipulation"></a>3D 개체 조작

직접 조작에서 3D 개체를 조작 유도성 기반 및 비 유도성 기반된 조작을 조작 하는 사용자는 두 가지 방법이 있습니다. 지점 및 커밋 모델에서 사용자 정확 하 게 직접 광선을 통해 동일한 작업을 달성할 수 있습니다. 필요 없는 추가 학습 합니다.<br>

### <a name="affordance-based-manipulation"></a>유도성 기반 조작
사용자는 가리키고 조작 affordances 고 경계 상자를 표시 합니다. 직접 광선을 사용 합니다. 사용자는 전체 개체를 이동 하는 경계 상자에, 회전 하려면 edge affordances 및 조작 제스처를 적용할 수 있습니다는 coner affordances 균일 하 게 확장 합니다. <br>

![](images/3D-Object-Manipulation-Far-720px.jpg) <br>


### <a name="non-affordance-based-manipulation"></a>비-유도성 기반된 조작
사용자가 직접 광선 경계 상자를 표시 하 고 직접 조작 제스처에서 적용을 사용 하 여 가리킵니다. 한 손으로 번역 및 회전 개체의 동작 및 손 모양 아이콘이의 방향에 연결 됩니다. 두 손을 사용 하 여 사용자가 변환, 확장할 수 있으며 두 손의 상대적 동작에 따라 회전 합니다.<br>

<br>

## <a name="instinctual-gesturers"></a>Instinctual gesturers
지점 및 커밋에 대 한 instinctual 제스처 개념이 비슷합니다를 직접 조작 합니다. 사용자는 3D 개체에 대해 수행할 가정 제스처 UI affordances의 디자인 지침을 제공 합니다. 예를 들어 작은 제어 지점 사용자가 사용자가 모든 5 개의 손가락을 사용 하 여 더 큰 개체를 얻을 수도 있지만 해당 엄지와 집게 손가락 손가락 모으기 동기를 부여 될 수 있습니다.

![](images/Instinctual-Gestures-Far-720px.jpg)<br>

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a>실습 6 DoF 컨트롤러 사이의 대칭 디자인 
처음에 지점 및 끝 상호 작용에 대 한 커밋 개념이 생성 되어에 대 한는 혼합 현실 포털 (MRP), 사용자는 몰입 형 헤드셋 마모 되 고 상호 작용 하는 컨트롤러 동작을 통해 3D 개체를 사용 하 여 위치를 정의 합니다. 동작 컨트롤러 가리키고 먼 개체 조작에 대 한 광선 아웃 문제를 해결 합니다. 더 다양 한 작업을 커밋에 대 한 컨트롤러에는 단추가 있습니다. 광선의 상호 작용 모델을 활용 하 고 양쪽 손으로에 연결 합니다. 이 대칭 디자인 MRP에 익숙한 사용자 HoloLen 2를 사용할 때 훨씬 가리키는 및 조작에 대 한 다른 상호 작용 모델에 알아보려면 필요가 그 반대로 가능 합니다.    

![](images/Symmetric-Design-For-Rays-720px.jpg)<br>

## <a name="instinctual-gestures"></a>Instinctual 제스처

![](images/Instinctual-Gestures-Far-720px.jpg)

## <a name="see-also"></a>참조
* [헤드 게이즈 및 커밋](gaze-and-commit.md)
* [실습을 사용 하 여 직접 조작](direct-manipulation.md)
* [Instinctual 상호 작용](interaction-fundamentals.md)

