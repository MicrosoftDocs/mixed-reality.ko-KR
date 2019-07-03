---
title: HoloLens 2에 대 한 모듈을 공유 학습 MR
description: HoloLens 2 응용 프로그램에서 다중 사용자 공유 환경을 구현 하는 방법을 알아보려면이 과정을 완료 합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: 44cc41b10ed79d3085ec601ec9cf21af47b0fea5
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523309"
---
# <a name="connecting-multiple-users"></a>여러 사용자를 연결합니다.

이 단원에서는 라이브를 공유 과정의 일부로 서 여러 사용자를 연결 하는 방법에 알아봅니다. 이 단원에서는 말 구, 조인 하는 각 사람의 표현 나타내는 아바타를 여러 장치에서 응용 프로그램을 열어 수 있습니다. 

목표:

- 예제 응용 프로그램 내에서 구성
- 플레이어를 구성 합니다.
- 공유 환경에서 여러 사용자를 연결 하는 방법 알아보기

### <a name="instructions"></a>지침

1. 자산-> 리소스-> [프로젝트] 패널에 Prefabs 폴더, 끌어서 놓기 계층 구조에서 NetworkLobby prefab 아래 이미지에 표시 된 대로 합니다.


   ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. NetworkLobby를 확장 하면 NetworkRoom 라는 자식 개체를 표시 됩니다. 선택한 NetworkRoom를 사용 하 여 검사기 패널로 이동 하 고 구성 요소 추가 클릭 합니다. PhotonView 검색 하 고 구성 요소를 추가 합니다.

   ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. 계층 구조에서 새 빈 게임 개체를 만듭니다. 계층을 마우스 오른쪽 단추로 클릭 하 고 상황에 맞는 메뉴에서 빈을 선택 합니다. 위치를 x로 설정 해야 = 0, y = 0, z = 0 및 PhotonUser 개체 이름을 지정 합니다.

   ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. 구성 요소 추가 클릭 하 고 제네릭 Net 동기화를 입력 합니다. Net 동기화 제네릭 클래스를 선택 합니다. 클래스에는 다음이 표시 되 면 설정 하려면 사용자 확인란을 클릭 합니다. 

   ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. 추가 구성 요소를 다시 클릭 하 고 Photon 보기를 입력 합니다. 드롭다운 목록에 표시 되는 Photon 뷰 클래스를 선택 합니다.

   ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. Net 동기화 제네릭 클래스에 대 한 파일 아이콘을 클릭 합니다. 끌어서 Photon 보기의 관찰 된 구성 요소 필드에 끌어 놓습니다. ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png) 

7. 그런 다음 공유 경험을 조인 하는 각 사용자를 나타내는 구 만듭니다. 방금 만든 PhotonUser 개체 및 scrolldown를 마우스 오른쪽 단추로 클릭 "하 고 3D 개체 타원 무늬입니다. 이렇게 하면 구체 게임 개체를 PhotonUser 개체의 자식으로 만들어집니다.

   ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. X 아래로 구체 확장 0.06, = y 0.06, ad z = 0.06 =.

   ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. 프로젝트 패널에서 Prefabs 폴더에 PhotonUser 게임 개체를 끌어서 장면에서 삭제 합니다. 생성 또는 공유 환경에서 새 플레이어를 인스턴스화할 때 사용할 수 있는 prefab 이제 만들었습니다.

   ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> 참고: 계층 구조에서 삭제 되기 전까지 게임 개체 Prefabs 폴더에 복사 성공적으로를 확인 합니다.

10. 3 단계의 지침에 따라 새 개체를 계층 구조에서 만들고 SharedPlayground 라는 이름을 지정 합니다. 그런 다음 구성 요소 추가 클릭 일반 네트워크 관리자를 검색 하 고 클릭 하 여 일반 네트워크 관리자 구성 요소를 추가 합니다. 위치를 변경 합니다 개체의 x = 0, y = 0 및 z = 0.

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a>축하합니다.

위의 모든 단계를 완료 하 고 빌드 프로세스를 완료 이기도 play 단추를 누르고 HoloLens 2에 연결 합니다. 머리를 이동 하면 이동 구가 표시 됩니다. Unity 프로젝트를 조인 하는 모든 사용자에 대 한 내용이 표시 됩니다.

[다음 단원: Sharing(Photon) 단원 4](mrlearning-sharing(photon)-ch4.md)

