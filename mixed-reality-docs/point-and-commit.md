---
title: 지점 및 커밋
description: 지점 및 커밋 입력된 모델 개요
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
keywords: 혼합 현실을, 상호 작용 디자인
ms.openlocfilehash: e0e9c97053734ac0125fce40be7ffe9afbd2dd68
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/27/2019
ms.locfileid: "64581313"
---
# <a name="point-and-commit"></a>지점 및 커밋
지점 및 커밋에는 대상, 선택, 2D 내용과 거리에서 3D 개체를 조작 하는 입력된 모델 수 있도록 사용자입니다. 이 "극동" 상호 작용 방법은 않은 사람이 되 고 실제로 일일 실제 상호 작용 하는 동안 navel 대화형 환경입니다. 예를 들어, 슈퍼 hero 영화, 마그네틱 연락 하 고는 거리의 실습을 통해 끝 개체를 조작할 수 있는 이지만 사람이 실제로 수행할 수 없습니다. Microsoft HoloLens (AR) 및 Microsoft 혼합 현실 VR ()에서에서는 언제 든 지 사용자가이 마법의 power holographic 콘텐츠로 즐거운 경험이 있지만 상호 작용을 보다 적용 하기 위해 뿐만 아니라 실제 세계의 물리적 제한을 주요 및 효율적입니다.

## <a name="device-support"></a>장치 지원
<table>
    <colgroup>
    <col width="40%" />
    <col width="20%" />
    <col width="20%" />
    <col width="20%" />
    </colgroup>
    <tr>
        <td><strong>입력된 모델</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (첫 번째 범용)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>몰입 형 헤드셋</strong></a></td>
    </tr>
     <tr>
        <td>지점 및 커밋 (맨 위 상호 작용)</td>
        <td>지원 되지 않습니다 ❌</td>
        <td>권장 ✔️</td>
        <td>권장 ✔️</td>
    </tr>
</table>
<br>
지점 및 커밋에 HoloLens 2에서 새 명확 하 고 손 모양 아이콘이 추적 시스템을 활용 하 여 기본 입력된 모델 중 하나가 되었습니다 합니다. 이 입력된 모델 동작 컨트롤러를 사용 하 여 몰입 형 헤드셋에서 기본 입력된 모델 이기도합니다. 지점 및 커밋은 헤드 Gaze 바꾸려면 것이 좋습니다는 입력된 모델 및 HoloLens에 커밋 (첫 번째 gen). 

## <a name="hand-rays"></a>직접 표면이
HoloLens 2에는 팜의 가운데에서 해결 직접 광선을 만듭니다. 광선이 손 모양 아이콘이의 확장으로 취급 됩니다. 도넛 모양 커서 hitted 개체를 사용 하 여 광선과 교차 하는 위치 의미 광선의 끝에 연결 됩니다. 커서 도착 하는 개체에는 손 모양 아이콘이에서 gestural 명령을 받습니다. 

엄지와 집게 손가락을 사용 하 여에 어 탭 제스처를 수행 하 여 매우 기본적인 gestural 명령이 트리거됩니다. 직접 광선 가리키고 어 탭을 커밋를 사용 하 여 사용자가 단추 또는 하이퍼링크는 웹 콘텐츠를 활성화할 수 있습니다. 자세한 복합 제스처를 사용 하 여 사용자가 웹 콘텐츠를 이동한 거리에서 3D 개체를 조작할 수 있습니다. 직접 광선의 시각적 디자인 지점 및 상태를 커밋합니다도 대응 해야 합니다. <br>
* 포인팅 상태의 광선과 인라인, dash 이며 커서 도넛 모양입니다.
* 커밋 중인 상태의 광선과 실선으로 바뀝니다 및 커서 점으로 축소 합니다.<br><br>
![](images/Hand-Rays-720px.jpg)<br>

## <a name="transition-between-near-and-far"></a>거의 및 끝 사이 전환
광선을 보내기 위해 집게 손가락으로 가리키는 같은 특정 제스처를 사용 하는 대신 설계할 손바닥 등의 가운데에서 들어오는 것 광선을 해제 하 고 자세한 gestural 조작에 대 한 5 개의 손가락을 예약 합니다. 따라서 HoloLens 2 근거리 및 원거리 상호 작용에 대 한 손 제스처의 정확히 동일한 집합을 지원합니다. 추가 학습 없습니다 먼 상호 작용에 가까이 있는 그 반대로 사용자에서 전송 하는 경우 필요 합니다. 사용자는 거리가 각기 다른 개체를 조작 동일한 잡기 제스처를 사용할 수 있습니다. 방사선 호출에는 자동 및 근접 기반입니다. <br>
* 개체 내의 거리 (약 50 cm)에 도달 하는 arm 경우 방사선 거의 상호 작용에 대 한 장려 자동으로 해제 되어 있습니다. 
* 개체가 50 cm 보다 더 강력 하 고 방사선 켜 집니다.

이 메커니즘 원활 하 게 전환을 만듭니다.<br>
![](images/Transition-Between-Near-And-Far-720px.jpg)<br>

## <a name="2d-slate-interaction"></a>2D 슬레이트 상호 작용
2D 슬레이트는 holographic 컨테이너 2D 앱 콘텐츠를 웹 브라우저와 같은 호스팅. 훨씬 2D 슬레이트를 상호 작용 하기 위한 디자인 개념 가리키고 어 탭을 커밋 직접 광선을 사용 하는 것입니다.<br>

슬레이트 상수와 상호 작용 합니다.<br>

* 사용자는 하이퍼링크 또는 활성화에 어 탭 한 다음 단추를 가리킬 수 있습니다. 
* 한편 탐색 제스처를 슬레이트 콘텐츠를 위아래로 스크롤 하는 데 사용할 수 있습니다. 
* 사용자 탐색 제스처에 슬레이트 콘텐츠 확대/축소를 수행 하려면 두 손을 사용할 수 있습니다.<br><br>

![](images/2D-Slate-Interaction-Far-720px.jpg)<br>

2D 조작 하기 위한 자체를 슬레이트:<br>

* 사용자가 직접 광선 모퉁이 또는 가장자리를 가장 가까운 조작 유도성 표시를 가리킵니다. 
* 유도성에서 조작 제스처를 적용 하 여 사용자 모퉁이 유도성 통해 균일 한 크기 조정을 수행할 수 있습니다 및 edge 유도성 통해 슬레이트 원래 대로 되돌릴 수 있습니다. 
* 2D 슬레이트의 맨 위에 있는 holobar에서 조작 제스처를 적용 하 여 사용자가 전체 슬레이트를 이동할 수 있습니다.<br>

<br>

## <a name="3d-object-manipulation"></a>3D 개체 조작
직접 조작의 두 가지 사용자에 대 한 3D 개체를 조작 하 유도성 기반 조작 비 affordnace 기반 조작 합니다. 모델에서 지점 및 커밋 사용자 직접 광선을 통해 동일한 작업에 정확 하 게 달성할 수 있습니다. 필요 없는 추가 학습 합니다.<br>

### <a name="affordance-based-manipulation"></a>유도성 기반 조작
사용자는 가리키고 조작 affordances 고 경계 상자를 표시 합니다. 직접 광선을 사용 합니다. 사용자는 전체 개체를 이동 하는 경계 상자에, 회전 하려면 edge affordances 및 조작 제스처를 적용할 수 있습니다는 coner affordances 균일 하 게 확장 합니다. <br>

![](images/3D-Object-Manipulation-Far-720px.jpg) <br>


### <a name="non-affordance-based-manipulation"></a>비-유도성 기반된 조작
사용자가 직접 광선 경계 상자를 표시 하 고 직접 조작 제스처에서 적용을 사용 하 여 가리킵니다. 한 손으로 번역 및 회전 개체의 동작 및 손 모양 아이콘이의 방향에 연결 됩니다. 두 손을 사용 하 여 사용자가 변환, 확장할 수 있으며 두 손의 상대적 동작에 따라 회전 합니다.<br>

<br>

## <a name="instinctual-gesturers"></a>Instinctual gesturers
지점 및 커밋에 대 한 instinctual 제스처의 개념은 동기화를 직접 조작 합니다. 3D 개체에 대해 수행할 제스처 사용자 가정 하는 새로운 UI affordances의 디자인에 따라 진행 됩니다. 작은 제어점 큰 개체 5 손가락으로 가져올 사용자를 사용 하면 엄지와 집게 손가락을 사용 하 여 축소 하는 사용자는 동기를 부여 합니다.

![](images/Instinctual-Gestures-Far-720px.jpg)<br>

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a>실습 6 DoF 컨트롤러 사이의 대칭 디자인 
먼저 먼 상호 작용에 대 한 지점 및 커밋 모델의 개념 생성 되어에 대 한는 혼합 현실 포털 (MRP), 사용자는 몰입 형 헤드셋 wear 하 고 컨트롤러 동작을 통해 3d 개체 상호 작용 하는 위치를 정의 합니다. 동작 컨트롤러 가리키고 먼 개체 조작에 대 한 광선 아웃 문제를 해결 합니다. 더 다양 한 기능을 커밋에 대 한 컨트롤러에는 단추가 있습니다. 광선의 상호 작용 모델을 활용 하 고 양쪽 손으로에 연결 합니다. 대칭이 디자인에서는 지금까지 가리키고 HoloLen 2를 사용 하 여 처음으로 하는 동안 조작에 대 한 다른 상호 작용 모델에 알아보려면 MRP에 익숙한 사용자 필요가 그 반대로 가능 합니다.    

![](images/Symmetric-Design-For-Rays-720px.jpg)<br>


## <a name="see-also"></a>참조
* [응시 및 커밋](gaze-and-commit.md)
* [직접 조작](direct-manipulation.md)
* [상호 작용 기본 사항](interaction-fundamentals.md)
