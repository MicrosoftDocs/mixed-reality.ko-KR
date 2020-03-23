---
title: 다중 사용자 기능 자습서 - 3. 여러 사용자 연결
description: 이 과정을 완료하여 HoloLens 2 애플리케이션 내에서 다중 사용자 공유 환경을 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: cbe0d8d2db6c34ba262fe9c946b68366ed3dbb93
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031225"
---
# <a name="3-connecting-multiple-users"></a>3. 여러 사용자 연결

이 단원에서는 라이브 공유 환경의 일부로 여러 사용자를 연결하는 방법에 대해 알아봅니다. 이 단원이 완료되면 여러 디바이스에서 애플리케이션을 열고, 조인하는 각 사람에 대한 구로 표현된 아바타를 볼 수 있습니다.

## <a name="objectives"></a>목표

* 애플리케이션 내에서 PUN 구성
* 플레이어 구성
* 공유 환경에서 여러 사용자를 연결하는 방법 알아보기

## <a name="instructions"></a>지침

1. [프로젝트] 패널의 Assets->Resources->Prefabs 폴더에서 아래 이미지와 같이 NetworkLobby 프리팹을 계층 구조로 끌어서 놓습니다.

    ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. NetworkLobby를 펼치면 NetworkRoom이라는 자식 개체가 표시됩니다. NetworkRoom을 선택한 상태에서 [검사기] 패널로 이동하여 [구성 요소 추가]를 클릭합니다. PhotonView를 검색하고 구성 요소를 추가합니다.

    ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. 새 빈 게임 개체를 계층 구조에 만듭니다. 마우스 오른쪽 단추로 계층 구조를 클릭하고, 컨텍스트 메뉴에서 [빈 개체]를 선택합니다. 위치 지정이 x =0, y=0, z=0으로 설정되어 있는지 확인하고 개체 이름을 PhotonUser로 지정합니다.

    ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. [구성 요소 추가]를 클릭하고, [일반 네트워크 동기화]를 입력합니다. [일반 네트워크 동기화] 클래스를 선택합니다. 클래스가 표시되면 [사용자] 확인란을 클릭하여 설정합니다.

    ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. [구성 요소 추가]를 다시 클릭하고, [Photon 보기]를 입력합니다. 드롭다운 목록에 표시되는 [Photon 보기] 클래스를 선택합니다.

    ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. [일반 네트워크 동기화] 클래스에 대한 [파일] 아이콘을 클릭합니다. [Photon 보기]의 [관찰된 구성 요소] 필드에 끌어서 놓습니다.

    ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png)

7. 다음으로, 공유 환경에 조인하는 각 사람을 나타내는 구를 만듭니다. 마우스 오른쪽 단추로 방금 만든 PhotonUser 개체를 클릭하고, "3D 개체"까지 아래로 스크롤한 다음, [구]를 클릭합니다. 그러면 구 게임 개체가 PhotonUser 개체의 자식 항목으로 만들어집니다.

    ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. 구의 크기를 x=0.06, y=0.06 및 z=0.06으로 축소합니다.

    ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. PhotonUser 게임 개체를 [프로젝트] 패널의 Prefabs 폴더로 끌어서 놓은 다음, 장면에서 이 개체를 삭제합니다. 이제 공유 환경에서 새 플레이어를 생성하거나 인스턴스화할 때 사용할 수 있는 프리팹이 만들어졌습니다.

    ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

    >[!NOTE]
    >먼저 게임 개체가 Prefabs 폴더에 성공적으로 복사되었는지 확인한 후에 계층 구조에서 해당 개체를 삭제하세요.

10. 3단계의 지침에 따라 계층 구조에서 새 개체를 만들고, SharedPlayground라는 이름을 지정합니다. 그런 다음, [구성 요소 추가]를 클릭하고, 일반 네트워크 관리자를 검색합니다.  이 항목을 다시 클릭하여 [일반 네트워크 관리자] 구성 요소를 추가합니다. 개체의 위치를 x=0, y=0 및 z=0으로 변경합니다.

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)

## <a name="congratulations"></a>축하합니다.

위의 모든 단계와 빌드 프로세스가 완료되면 [재생] 단추를 누르고 HoloLens 2를 연결합니다. 머리를 이동함에 따라 움직이는 구를 볼 수 있습니다. 이는 Unity 프로젝트에 조인하는 모든 사용자에게 표시됩니다!

[다음 단원: 4. 여러 사용자와 개체 이동 공유](mrlearning-sharing(photon)-ch4.md)
