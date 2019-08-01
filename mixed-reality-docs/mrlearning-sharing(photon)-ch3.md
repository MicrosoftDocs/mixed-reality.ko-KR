---
title: 다중 사용자 기능 자습서-3. 여러 사용자 연결
description: 이 과정을 완료 하 여 HoloLens 2 응용 프로그램 내에서 다중 사용자 공유 환경을 구현 하는 방법을 알아보세요.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: d3068a1ebbbc2b6db8b563be8bf8c6e488e9491a
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701936"
---
# <a name="3-connecting-multiple-users"></a>3. 여러 사용자 연결

이 단원에서는 라이브 공유 환경의 일부로 여러 사용자를 연결 하는 방법에 대해 알아봅니다. 이 단원의 끝에는 여러 장치에서 응용 프로그램을 열고, 연결 된 각 사용자의 표현으로 표현 된 아바타를 볼 수 있습니다. 

목표로

- 응용 프로그램 내에서 THIS 구성
- 플레이어 구성
- 공유 환경에서 여러 사용자를 연결 하는 방법 알아보기

## <a name="instructions"></a>지침

1. 프로젝트 패널의 자산-> 리소스-> Prefabs 폴더에서 아래 이미지에 표시 된 것 처럼 NetworkLobby prefab을 계층으로 끌어 놓습니다.

![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. NetworkLobby를 확장 하면 Networklobby 이라는 자식 개체가 표시 됩니다. NetworkRoom을 선택 하 고 검사기 패널로 이동 하 여 구성 요소 추가를 클릭 합니다. PhotonView를 검색 하 고 구성 요소를 추가 합니다.

![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. 계층에 빈 게임 개체를 새로 만듭니다. 계층 구조를 마우스 오른쪽 단추로 클릭 하 고 상황에 맞는 메뉴에서 비어 있음을 선택 합니다. 위치 지정이 x = 0, y = 0, z = 0으로 설정 되어 있는지 확인 하 고 개체 이름을 PhotonUser로 지정 합니다.

![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. 구성 요소 추가를 클릭 하 고 일반 네트워크 동기화를 입력 합니다. 일반 Net Sync 클래스를 선택 합니다. 클래스가 표시 되 면 사용자 확인란을 클릭 하 여 설정 합니다. 

![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. 구성 요소 추가를 다시 클릭 하 고 Photon View를 입력 합니다. 드롭다운 목록에 표시 되는 Photon View 클래스를 선택 합니다.

![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. 일반 네트워크 동기화 클래스에 대 한 파일 아이콘을 클릭 합니다. Photon 뷰의 관찰 된 구성 요소 필드에 끌어서 놓습니다. 

![module3chapter3updateStep6im](images/module3chapter3updateStep6im.png) 

7. 다음으로 공유 환경에 가입 하는 각 사람을 나타내는 구를 만듭니다. 방금 만든 PhotonUser 개체를 마우스 오른쪽 단추로 클릭 하 고 scrolldown "3D 개체를 클릭 한 후 구를 클릭 합니다. 그러면 구 게임 개체가 PhotonUser 개체의 자식으로 생성 됩니다.

![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. X = 0.06, y = 0.06, ad z = 0.06로 구를 축소 합니다.

![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. PhotonUser game 개체를 프로젝트 패널의 Prefabs 폴더로 끌어 장면에서 삭제 합니다. 이제 공유 환경에서 새 플레이어를 생성 하거나 인스턴스화할 때 사용할 수 있는 prefab를 만들었습니다.

![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> 참고: 게임 개체가 계층 구조에서 삭제 되기 전에 Prefabs 폴더에 성공적으로 복사 되었는지 확인 합니다.

10. 3 단계의 지침에 따라 계층 구조에 새 개체를 만들고 이름을 SharedPlayground로 합니다. 그런 다음 구성 요소 추가를 클릭 하 고 일반 네트워크 관리자를 검색 한 후이를 클릭 하 여 일반 네트워크 관리자 구성 요소를 추가 합니다. 개체의 위치를 x = 0, y = 0 및 z = 0으로 변경 합니다.

![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a>축하합니다.

위의 모든 단계를 완료 하 고 빌드 프로세스도 완료 되 면 재생 단추를 누르고 HoloLens 2를 연결 합니다. 헤드를 이동 하면 구가 이동 하는 것을 볼 수 있습니다. Unity 프로젝트를 조인 하는 모든 사용자에 대해 표시 됩니다.

[다음 단원: 4. 여러 사용자와 개체 이동 공유](mrlearning-sharing(photon)-ch4.md)

