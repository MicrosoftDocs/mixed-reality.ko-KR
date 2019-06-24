---
title: HoloLens 2에 대 한 모듈을 공유 학습 MR
description: HoloLens 2 응용 프로그램에서 다중 사용자 공유 환경을 구현 하는 방법을 알아보려면이 과정을 완료 합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: f2e8cef618ea2fbee398ce19f1ba60b712b5fe3e
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327473"
---
# <a name="connecting-multiple-users"></a>**여러 사용자를 연결합니다.** 

이 단원에서는 라이브 공유 환경의 일부분으로 여러 사용자를 연결 하는 방법을 배웁니다. 이 단원을 마치면 수를 여러 장치에서 응용 프로그램을 열고 "아바타" 표현 (아바타 구로 표시 합니다.)를 조인 하는 각 사용자의를 참조 하세요. 

목표:

- 예제 응용 프로그램 내에서 구성
- 플레이어를 구성 합니다.
- 공유 환경에서 여러 사용자를 연결 하는 방법 알아보기

### <a name="instructions"></a>지침

1. 자산에서 > 리소스 > Prefabs 폴더의 프로젝트 패널, 끌어서 놓기는 "NetworkLobby" 계층에 prefab에서 아래 이미지에 표시 된 대로 합니다.


![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. "NetworkRoom." 라는 자식 개체를 prefab "NetworkLobby"를 확장 하면 표시 검사기 패널로 이동 하 고 "구성 요소를 추가 합니다."를 클릭 후 선택 "PhotonView"를 검색 하 고 구성 요소를 추가 합니다.

![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. 계층 구조에서 새 빈 게임 개체를 만듭니다 (계층 구조에서 마우스 오른쪽 단추로 클릭 하 고 상황에 맞는 메뉴에서 "비어 있음"을 선택). 위치를 x로 설정 해야 = 0, y = 0, z = 0 및 "PhotonUser." 개체 이름

![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. 그런 다음 공유 경험을 조인 하는 각 사용자를 나타내는 구 만들기 하고자 합니다. 방금 만든 "PhotonUser" 개체를 마우스 오른쪽 단추로 클릭, 이동 "3D 개체" 및 "타원 무늬."를 클릭 합니다. 이렇게 하면 구체 게임 개체를 PhotonUser 개체의 자식으로 만들어집니다.

![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

5. X 아래로 구체 확장 0.06, = y 0.06, ad z = 0.06 =.

![Module3hapter3step5im](images/module3chapter3step5im.PNG)

6. 프로젝트 패널에서 "prefabs" 폴더로 "PhotonUser" 게임 개체를 끕니다. 그런 다음 장면에서 삭제 합니다. 생성 또는 공유 환경에서 새 플레이어를 인스턴스화할 때 사용할 prefab 이제 만들었습니다.

![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> 참고: 계층 구조에서 삭제 되기 전까지 게임 개체에 "prefabs" 폴더에 성공적으로 복사 되도록 합니다.

7. (3 단계는 유사한 지침 사용), 계층 구조에 새 개체를 만들고 이름을 "SharedPlayground." 그런 다음 "구성 요소 추가" 및 "일반 네트워크 관리자"에 대 한 검색을 클릭 하 고 클릭 하 여 일반 네트워크 관리자 구성 요소를 추가 합니다. 위치를 변경 합니다 개체의 x = 0, y = 0 및 z = 0.

![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a>축하합니다.

위의 모든 단계를 완료 하 고 재생 단추를 누르고 HoloLens 2에 연결 하는 경우 빌드 프로세스는 완료 머리를 이동 하면 이동 구가 표시 됩니다! Unity 프로젝트를 조인 하는 모든 사용자에 대 한 내용이 표시 됩니다.

[다음 단원: Sharing(Photon) 단원 4](mrlearning-sharing(photon)-ch4.md)

