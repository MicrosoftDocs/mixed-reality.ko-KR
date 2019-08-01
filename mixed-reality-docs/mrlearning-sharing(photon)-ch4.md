---
title: 다중 사용자 기능 자습서-4. 여러 사용자와 개체 이동 공유
description: 이 과정을 완료 하 여 HoloLens 2 응용 프로그램 내에서 다중 사용자 공유 환경을 구현 하는 방법을 알아보세요.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: 2e676d319ba7221cf9549b200b3d748f26025aa7
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701896"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a>4. 여러 사용자와 개체 이동 공유

이 자습서에서는 공유 세션의 모든 참가자가 함께 공동 작업 하 고 다른 사람의 상호 작용을 볼 수 있도록 개체의 움직임을 공유 하는 방법에 대해 알아봅니다. 이 단원에서는 [기본 모듈 자습서](mrlearning-base.md)의 일부로 작성 된 음력 시작 관리자를 기반으로 합니다.

목표로

- 공유할 3D 모델로 음력 시작 관리자 가져오기
- 3D 모델의 움직임을 공유 하도록 프로젝트를 구성 합니다.
- 기본 다중 사용자 공동 작업 응용 프로그램을 빌드하는 방법 알아보기

## <a name="instructions"></a>지침


1. 이전 단원 (컨트롤 + S)의 장면을 저장 합니다. 필요할 때 더 쉽게 찾을 수 있도록 이름을 HLSharedProjectMainPart4으로 지정할 수 있습니다.

2. 프로젝트 창의 자산-> Scripts 폴더에서 GenericNetSync를 두 번 클릭 하 여 Visual Studio에서 열거나 사용 중인 코드 편집기를 엽니다.  

![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. 34 줄과 38 줄에서이 단원에서 사용할 테이블의 코드를 활성화 하려면//를 제거 합니다. 다음으로 파일을 저장 합니다. 

![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. 프로젝트 창의 자산-> Scripts 폴더에서 PhotonRoom.cs 파일을 두 번 클릭 하 여 Visual Studio에서 엽니다. 

![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. 3 단계와 마찬가지로 25, 26, 106 줄에서 코드를 활성화 하려면//를 제거 해야 합니다.

![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png) 

![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. 계층 구조 보기에서 NetworkRoom 개체를 선택 합니다.

![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. 프로젝트 뷰에서 자산-> 리소스-> Prefabs로 이동 합니다. 먼저 prefab 테이블을 PhotonRoom 클래스의 Tableprefab 슬롯으로 끌어 놓습니다. 그런 다음, RocketLauncherCompleteVariantprefab를 PhotonRoom 클래스의 모듈 Prefab 슬롯에 끌어서 놓습니다.

![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

   참고: Prefab 개체와 릴리스 중 하나를 클릭 하면 검사기가 해당 개체로 전환 됩니다. 각 개체를 적절 한 슬롯으로 클릭 하 고 끌어서 놓고 놓습니다.

8. MixedRealityPlayspace 왼쪽에 있는 화살표를 클릭 하 고 자식 게임 개체인 MainCamera를 SharedPlayground로 이동 합니다. 그런 다음 prefab, MixedRealityPlayspace를 삭제 하 고, prefab를 선택 하 고, 키보드에서 "삭제"를 누릅니다.
![Module3hapter4step5im](images/module3chapter4step5im.PNG)

>참고:  주 카메라와 SharedPlayground 위치가 모두 0, 0, 0으로 설정 되어 있는지 확인 합니다.
>

9. 새 개체를 만들기 위해 SharedPlayground 부모 개체에 대 한 자식 개체로 설정 된 새 게임 개체를 만듭니다. 부모 개체를 마우스 오른쪽 단추로 클릭 하 고 빈 만들기를 선택 합니다. 

10. 계층에서 새 개체를 선택한 상태에서 개체의 이름을 Inspector 패널의 TableAnchor로 변경 합니다. 또한 구성 요소 추가를 클릭 하 고 TableAnchor 구성 요소를 검색 합니다. 이를 선택 하 고 개체에 추가 합니다. 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

11. 이제 Prefabs 폴더의 프로젝트 패널에서 prefab 테이블을 방금 만든 "TableAnchor" 자식 개체로 끌어 옵니다.

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

12. 마지막으로 DebugWindow 개체에서 너비를 50으로 변경 하 고 높이를 20으로 변경 합니다.

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)

## <a name="congratulations"></a>축하합니다.


이 작업이 완료 되 면 Unity 프로젝트에 참여 하는 모든 사용자가 음력 시작 관리자를 이동할 수 있습니다. 각 사용자가 다른 사람의 상호 작용을 볼 수 있도록 모든 이동이 동기화 됩니다. 이러한 개념은 모든 기능을 갖춘 공유 공동 작업 환경을 위한 기본 구성 요소로 제공 됩니다. 

모든 사용자가 공유 환경의 일부로 연결 되어 있고 개체의 상대 움직임을 볼 수 있지만, 로컬 사용자가 물리적 위치에서 같은 위치에 있는 개체와 개체를 볼 수 있도록 응용 프로그램은 아바타 및 개체를 정확 하 게 맞출 수 없습니다. world. 로컬 공유 환경을 고정 하기 위해 모든 장치에는 물리적 환경을 일반적으로 이해 해야 합니다. 이 모듈에서는 다음 단원에서 구현 될 [Azure 공간 앵커](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (global.asa)를 사용 하 여이를 구현 합니다.

다음 단원을 진행 하기 전에이를 공유 환경에 통합 하기 위해 필요한 기본 사항, Azure 계정 및 리소스 생성 및 기타 기본 빌딩 블록을 다루는 GLOBAL.ASA 학습 모듈을 완료 해야 합니다.

[다음 단원: 5. 공유 환경에 Azure Spatial Anchors 통합](mrlearning-sharing(photon)-ch5.md)

