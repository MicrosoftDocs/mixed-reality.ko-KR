---
title: HoloLens 2에 대 한 모듈을 공유 학습 MR
description: HoloLens 2 응용 프로그램에서 다중 사용자 공유 환경을 구현 하는 방법을 알아보려면이 과정을 완료 합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: a67eaef45582054b62198a563f0ee01724fd60db
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328129"
---
# <a name="synchronizing-the-movements-of-shared-objects"></a>공유 개체의 움직임을 동기화

이 단원에서는 공유 세션의 모든 참가자가 공동 작업 하 고 다른 사용자 상호 작용을 볼 수 있도록 개체의 움직임을 공유 하는 방법을 배웁니다. 단원은의 일부로 만든 음력 시작 관리자에이 [자료 모듈 자습서](mrlearning-base.md)합니다.

목표:

- 3D 모델을 공유할 수로 완료 된 음력 시작 관리자 가져오기
- 3D 모델의 움직임을 공유 하기 위해 프로젝트를 구성 합니다.
- 기본적인 다중 사용자 공동 작업 응용 프로그램을 빌드하는 방법을 알아봅니다

### <a name="instructions"></a>지침

1. 이전 단원 (control + S)에서 장면을 저장 합니다. 쉽게 다시 필요할 때 찾을 수 있도록 "HLSharedProjectMainPart4.unity" 이름을 수 있습니다.

2. (선택 하 고 delete 키를 눌러) "NetworkLobby" 개체를 삭제 합니다. 또한 2 단원에서 "prefabs" 폴더로 이동 하 고 여기에서 "NetworkLobby" prefab을 삭제 합니다.

![Module3Chapter4tep2im](images/module3chapter4step2im.PNG)

3. (예: 2 단계 단원 2에서에서) 새 사용자 지정 패키지를 가져오고 가져오기 합니다 [LunarModule.unitypackage](linkforModule1 lesson with the lunar module) 하며 [NetworkLobbyReplacement.unitypackage 합니다.](linkforNetworklobbyreplacement package here)

![Module3Chapter4step3im](images/module3chapter4step3im.PNG)

4. 이제 "prefabs" 폴더에서 새 "NetworkLobby" prefab을 계층으로 끕니다. 

![Module3hapter4step4im](images/module3chapter4step4im.PNG)

> 참고: 이전 단계에서 가져온 두 개의 패키지 "NetworkLobby" prefab을 업데이트 합니다. 줄일 수 많은 텍스트를 입력에서!

5. 이제 "MixedRealityPlayspace"의 왼쪽에 있는 화살표를 클릭 하 고 "SharedPlayground" prefab으로 자식 게임 개체를 "MainCamera" 아래로 이동 합니다. 그런 다음 (삭제, 선택 하 여 prefab 키보드의 "삭제"를 탭) prefab "MixedRealityPlayspace"를 삭제 합니다.

![Module3hapter4step5im](images/module3chapter4step5im.PNG)

6. 자식 개체를 "SharedPlayground" 부모 개체 (새 개체를 만들고 부모 개체를 마우스 오른쪽 단추로 클릭 한 다음 "빈 항목 만들기"를 선택)로 새 게임 개체를 만듭니다.
7. 계층에서 선택한 새 개체를 사용 하 여 "TableAnchor" 개체의 이름을 [관리자] 패널에서 변경 합니다. 또한 "구성 요소를 추가"를 클릭 하 고 "TableAnchor" 구성 요소에 대 한 검색 합니다. 선택한 개체에 추가 합니다.

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> 참고: x 위치 설정 = 1, y = 0.55 및 z = 2입니다. 또한 회전 y로 = 90입니다. 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

8. 이제 프로젝트 패널에서 "prefabs" 폴더에 끌어다 놓습니다 "table" prefab "TableAnchor" 자식 개체를 만들었습니다.

   ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

9. "NetworkRoom,"는 계층 구조에서 "NetworkLobby" 아래에 있는 자식 개체를 선택 하 고 "검사기 창에"PhotonView"검색" 구성 요소 추가 클릭 스크립트를 추가 하는 "*NetworkRoom*" 개체입니다.

![Module3Chapter4step9im](images/module3chapter4step9im.PNG)

11. 마지막으로 "DebugWindow" 개체의 너비를 80 및 높이를 10으로 변경 합니다.

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a>축하합니다.

완료 되 면 Unity 프로젝트를 조인 하는 모든 사용자 음력 시작 관리자를 이동할 수 있습니다. 각 사용자는 다른 사용자 상호 작용을 볼 수 있도록 모든 움직임 동기화 됩니다. 이러한 개념 갖춘 공유 공동 작업 환경 위한 기본적인 빌딩 블록으로 사용 됩니다. 

응용 프로그램은 정확 하 게 볼 수 있도록 로컬 서로 및 실제 내에서 같은 위치에 개체 아바타 및 개체를 정렬 하는 데 수 공유 환경의 일부분으로 연결 된 모든 사용자에 개체의 상대적인 움직임을 볼 수 있지만 전 세계입니다. 로컬 공유 경험을 고정 하려면 모든 장치에 물리적 환경에 대 한 일반적인 이해에 필요 합니다. 이 모듈에서는 이렇게 사용 하 여 [Azure 공간 앵커](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA)는 다음 단원에서 구현 됩니다.

다음 단원에 하기 전에 알아야 할 ASA에 필요한 Azure 계정 및 리소스 생성 및 다른 기본 빌딩 블록이 공유 경험에 통합 수 전에 ASA 학습 모듈을 완료 해야 합니다.

[다음 단원: Sharing(Photon) 단원 5](mrlearning-sharing(photon)-ch5.md)

