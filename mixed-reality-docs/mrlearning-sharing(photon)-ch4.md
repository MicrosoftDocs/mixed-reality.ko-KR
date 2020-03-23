---
title: 다중 사용자 기능 자습서 - 4. 여러 사용자와 개체 움직임 공유
description: 이 과정을 완료하여 HoloLens 2 애플리케이션 내에서 다중 사용자 공유 환경을 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: b0ddf0799fd94c29ce8f1221c55073cd77b63703
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031244"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a>4. 여러 사용자와 개체 움직임 공유

이 자습서에서는 공유 세션의 모든 참가자가 협업하고 서로의 상호 작용을 볼 수 있도록 개체의 움직임을 공유하는 방법에 대해 알아봅니다. 이 단원에서는 [기본 모듈 자습서](mrlearning-base.md)의 일부로 작성된 Lunar 발사 시스템을 기반으로 합니다.

## <a name="objectives"></a>목표

- 공유할 3D 모델로 Lunar 발사 시스템 가져오기
- 3D 모델의 움직임을 공유하도록 프로젝트 구성
- 기본 다중 사용자 협업 애플리케이션을 빌드하는 방법 알아보기

## <a name="instructions"></a>지침

1. 이전 단원의 장면을 저장합니다(Control+S). 필요할 때 더 쉽게 찾을 수 있도록 HLSharedProjectMainPart4.unity라는 이름을 지정할 수 있습니다.

2. [프로젝트] 창의 Assets->Scripts 폴더에서 GenericNetSync를 두 번 클릭하여 Visual Studio 또는 사용 중인 코드 편집기에서 엽니다.  

    ![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. 34번 및 38번 줄에서 "//"를 제거하여 이 단원에서 사용할 테이블의 코드를 활성화합니다. 다음으로, 파일을 저장합니다.

    ![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. [프로젝트] 창의 Assets->Scripts 폴더에서 PhotonRoom.cs 파일을 두 번 클릭하여 Visual Studio에서 엽니다.

    ![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. 3단계와 마찬가지로 25, 26, 106번 줄에서 "//"를 제거하여 코드를 활성화해야 합니다.

    ![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png)

    ![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. [계층 구조] 보기에서 NetworkRoom 개체를 선택합니다.

    ![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. [프로젝트] 보기에서 Assets->Resources->Prefabs로 차례로 이동합니다. 먼저 Table 프리팹을 PhotonRoom 클래스의 Tableprefab 슬롯으로 끌어서 놓습니다. 다음으로, RocketLauncherCompleteVariantprefab을 PhotonRoom 클래스의 [모듈 프리팹] 슬롯으로 끌어서 놓습니다.

    ![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

    >[!NOTE]
    >프리팹 개체 중 하나를 클릭하고 해제하면 [검사기]에서 해당 개체로 전환합니다. 각 개체를 클릭하고, 해당 슬롯으로 끌어서 놓고, 해제합니다.

8. MixedRealityPlayspace 왼쪽에 있는 화살표를 클릭하고, MainCamera 자식 게임 개체를 SharedPlayground 프리팹으로 이동합니다. 다음으로, MixedRealityPlayspace 프리팹을 선택하고 키보드에서 "삭제"를 탭하여 이 프리팹을 삭제합니다.

    ![Module3hapter4step5im](images/module3chapter4step5im.PNG)

    >[!NOTE]
    >주 카메라와 SharedPlayground의 위치가 모두 0,0,0으로 설정되어 있는지 확인합니다.

9. "SharedPlayground" 개체를 선택하여 마우스 오른쪽 단추를 클릭하고, "빈 개체 만들기" 옵션을 선택하여 빈 게임 개체를 "SharedPlayground" 게임 개체의 자식 항목으로 만듭니다.

   ![Module3chapter4step6im](images/module3chapter4step6im.PNG)

10. [계층 구조]에서 새 개체를 선택한 채로 [검사기] 패널에서 개체 이름을 TableAnchor로 변경합니다. 또한 [구성 요소 추가]를 클릭하고, TableAnchor 구성 요소를 검색합니다. 이를 선택하여 개체에 추가합니다.

    ![Module3Chapter4step7im](images/module3chapter4step7im.PNG)

11. [프로젝트] 패널의 Prefabs 폴더에서 Table 프리팹을 방금 만든 "TableAnchor" 자식 개체로 끕니다.

    ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

## <a name="congratulations"></a>축하합니다.

이 작업이 완료되면 주위를 둘러보면서 Lunar 모듈을 찾습니다. 그러면 Unity 프로젝트에 조인하는 모든 사용자가 Lunar 발사 시스템을 움직일 수 있습니다.  모든 움직임이 동기화되어 각 사용자가 서로의 상호 작용을 볼 수 있습니다. 이러한 개념은 모든 기능을 갖춘 공유 협업 환경을 위한 기본 구성 요소로 제공됩니다.

모든 사용자가 공유 환경의 일부로 연결되어 있고 개체의 상대적인 움직임을 볼 수 있지만, 애플리케이션에서 여전히 아바타와 개체를 정확하게 맞출 수 없으므로 로컬 사용자가 실제 세계 내의 동일한 위치에서 서로와 개체를 볼 수 없습니다. 로컬 공유 환경을 고정시키려면 모든 디바이스에서 물리적 환경을 일반적으로 인식해야 합니다. 이 모듈에서는 다음 단원에서 구현될 [ASA(Azure Spatial Anchors)](<https://azure.microsoft.com//services/spatial-anchors/>)를 사용하여 이를 수행합니다.

다음 단원으로 진행하려면 먼저 ASA 기본 사항, Azure 계정 및 리소스 만들기뿐만 아니라 이를 공유 환경에 통합하기 전에 필요한 다른 기본 구성 요소도 다루는 ASA 학습 모듈을 완료해야 합니다.

[다음 단원: 5. 공유 환경에 Azure Spatial Anchors 통합](mrlearning-sharing(photon)-ch5.md)
