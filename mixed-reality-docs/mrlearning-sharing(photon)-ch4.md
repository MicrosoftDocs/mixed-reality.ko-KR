---
title: HoloLens 2에 대 한 모듈을 공유 학습 MR
description: HoloLens 2 응용 프로그램에서 다중 사용자 공유 환경을 구현 하는 방법을 알아보려면이 과정을 완료 합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: 2a4ea599fd4887f30589c2d839be305d3dc8d1bd
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523198"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a>4. 여러 사용자와 공유 개체 이동

이 자습서에서는 공유 세션의 모든 참가자가 공동 작업 하 고 다른 사용자 상호 작용을 볼 수 있도록 개체의 움직임을 공유 하는 방법에 알아봅니다. 단원은의 일부로 만든 음력 시작 관리자에이 [자료 모듈 자습서](mrlearning-base.md)합니다.

목표:

- 상태로 음력 시작 관리자에서 3D 모델을 공유할 수
- 3D 모델의 움직임을 공유 하기 위해 프로젝트를 구성 합니다.
- 기본적인 다중 사용자 공동 작업 응용 프로그램을 빌드하는 방법을 알아봅니다

### <a name="instructions"></a>지침


1. 이전 단원 (Control + S)에서 장면을 저장 합니다. 이름을 지정할 수 있습니다, HLSharedProjectMainPart4.unity, 쉽게 필요할 때 찾을 수 있도록 합니다.

2. 프로젝트 창에서 자산-> Scripts 폴더에서 Visual Studio 또는 이전 코드에 사용 하는 편집기에서 엽니다 GenericNetSync를 두 번 클릭 합니다.  ![](images/module3chapter4updatestep2.png)

3. 줄 34 및 38에서 제거는 / /이 단원에서 사용 하는 테이블에 대 한 코드를 활성화 합니다. 그런 다음 파일을 저장 합니다. ![](images/module3chapter4updatestep3.png)

4. 프로젝트 창에서 자산에서 PhotonRoom.cs 파일을 두 번 클릭-> Visual Studio에서 열려는 스크립트 폴더입니다. ![](images/module3chapter4updatestep4.png)

5. 3 단계에서에서 제거 해야 하는 것 처럼는 / / 26, 25, 106 줄에서 코드를 활성화 합니다.![](images/module3chapter4updatestep5a.png) ![](images/module3chapter4updatestep5b.png)

6. 계층 뷰에서 NetworkRoom 개체를 선택 합니다.![](images/module3chapter4updatestep6.png)

7. 이동할 프로젝트 보기에서 자산에는 리소스-> Prefabs-> 합니다. 먼저 끌어서 테이블 prefab Tableprefab 슬롯 PhotonRoom 클래스에 있습니다. 그런 다음 끌어서 놓기 LunarModule prefab 모듈 Prefab 슬롯 PhotonRoom 클래스에 있습니다. ![](images/module3chapter4updatestep7.png)

   참고: Prefab 개체 및 릴리스 중 하나를 클릭 하면 검사기는 해당 개체에 전환 됩니다. 클릭, 끌어서, drop 및 해당 슬롯에 있는 각 개체를 해제 합니다.



8. MixedRealityPlayspace, 왼쪽에 있는 화살표를 클릭 하 고 SharedPlayground prefab으로 MainCamera 자식 게임 개체를 아래로 이동 합니다. 삭제를 prefab을 선택 하 고 키보드에서 "삭제"를 탭 MixedRealityPlayspace prefab을 삭제할 어).
![Module3hapter4step5im](images/module3chapter4step5im.PNG)

참고:  주 카메라와 SharedPlayground 위치 0,0,0에 설정 되어 있는지 확인 합니다.

9. 새 개체를 만들려면 SharedPlayground 부모 개체에 자식 개체로 설정 하는 새 게임 개체를 만듭니다. 부모 개체를 마우스 오른쪽 단추로 클릭 하 고 빈 항목 만들기를 선택 합니다. 

10. 계층에서 선택한 새 개체를 사용 하 여 TableAnchor 개체의 이름을 [관리자] 패널에서 변경 합니다. 또한 구성 요소 추가 클릭 하 고 TableAnchor 구성 요소를 검색 합니다. 선택한 개체에 추가 합니다. 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> 참고: X 위치 설정 = 1, y = 0.55 및 z = 2입니다. 또한 회전 y로 = 90입니다. 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

11. 이제 Prefabs 폴더에 [프로젝트] 패널에서 방금 만든 "TableAnchor" 자식 개체로 테이블 prefab을 끕니다.

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)



12. 마지막으로, DebugWindow 개체에서 80 및 높이를 10으로 너비를 변경 합니다.

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a>축하합니다.


완료 되 면 Unity 프로젝트를 조인 하는 모든 사용자 음력 시작 관리자를 이동할 수 있습니다. 각 사용자는 다른 사용자 상호 작용을 볼 수 있도록 모든 움직임 동기화 됩니다. 이러한 개념 갖춘 공유 공동 작업 환경 위한 기본적인 빌딩 블록으로 사용 됩니다. 

응용 프로그램은 정확 하 게 아바타 및 개체를 정렬 하 여 실제 내에서 같은 위치에 개체 및 서로 참조 하는 로컬 사용자 수를 공유 과정의 일부로 서 연결 된 모든 사용자에 개체의 상대적인 움직임을 볼 수 있지만 전 세계입니다. 로컬 공유 경험을 고정 하려면 모든 장치에 물리적 환경에 대 한 일반적인 이해에 필요 합니다. 이 모듈에서는에서는에서는 이렇게 사용 하 여 [Azure 공간 앵커](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA)는 다음 단원에서 구현 됩니다.

다음 단원 전에 다루는 ASA 기본 사항, Azure 계정 및 리소스 생성 및 다른 기본 빌딩 블록 필요한이 공유 경험에 통합 수 전에 ASA 학습 모듈을 완료 해야 합니다.

[다음 단원: Sharing(Photon) 단원 5](mrlearning-sharing(photon)-ch5.md)

