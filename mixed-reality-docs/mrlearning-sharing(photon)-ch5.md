---
title: 다중 사용자 기능 자습서-5. 공유 환경에 Azure 공간 앵커 통합
description: 이 과정을 완료 하 여 HoloLens 2 응용 프로그램 내에서 다중 사용자 공유 환경을 구현 하는 방법을 알아보세요.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, Hololens
ms.openlocfilehash: 9d76d5323705c001dbafe4411a9334dd3403d0ca
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926235"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a>5. Azure 공간 앵커를 공유 환경에 통합

이 단원에서는 Azure 공간 앵커 (GLOBAL.ASA)를 공유 환경에 통합 하는 방법에 대해 알아봅니다. 모든 참가자가 동일한 물리적 위치에 있는 개체를 볼 수 있도록 실제 환경에서 가상 환경을 고정 하는 경우에는 여러 개의 공동 배치 된 장치에서 일반적인 참조를 사용할 수 있습니다.

이 단원을 계속 진행 하기 전에 먼저 Azure 계정 및 리소스를 만들고, Azure 계정 및 리소스를 만들고, Azure를 공유 환경에 통합 하기 전에 필요한 다른 기본 구성 요소를 포함 하는 GLOBAL.ASA 학습 모듈을 완료 해야 합니다.

목표로

- 다기능를 다중 장치 맞춤을 위한 공유 환경에 통합 하세요.
- 로컬 공유 환경의 컨텍스트에서가 작동 하는 방식에 대 한 기본 사항을 알아봅니다.

### <a name="instructions"></a>지침

1. 이전 단원 (컨트롤 + S)의 프로젝트를 저장 하 고 다시 필요할 때 더 쉽게 찾을 수 있도록 이름을 "HLSharedProjectMainPart5"로 표시 합니다.

2. MixedRealityPlayspace 부모 개체 아래에서 TableAnchor prefab를 선택 하 고 삭제 합니다.

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

3.  프로젝트 뷰에서 자산-> 리소스-> Prefabs로 이동 하 고 SharedPlayground 개체의 맨 위에 TableAnchor를 끌어 자식으로 만듭니다.
4.  MixedRealityPlayspace 부모 개체인 TableAnchor 개체를 확장 하 고 Buttons 개체도 확장 합니다. 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. 이제 계층 구조에서 ShareAzureAnchorButton을 선택 하 고 주목를 검사기 패널로 이동 합니다. 아래 이미지에 표시 된 드롭다운 메뉴로 스크롤하고 AnchorModuleScript를 선택 하 고 ShareAnchorNetwork ()를 클릭 합니다.

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. GetAzureAnchorButton (4 단계 참조)를 선택 하 고 주목를 검사기 패널로 다시 이동 합니다. 아래 이미지에 표시 된 드롭다운 메뉴로 스크롤하고 AnchorModuleScript를 선택 하 고 GetSharedAnchorNetwork ()를 클릭 한 다음 저장을 클릭 합니다.

![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. 공유 모듈을 테스트 하려면 azure 공간 앵커 세션을 시작 하는 "Azure 만들기 세션 시작" 단추를 클릭 한 다음 "Azure 앵커 만들기" 단추를 클릭 하 여 azure 앵커를 만듭니다. Azure 앵커가 생성 될 때까지 기다립니다. Azure 앵커를 만든 후 "Azure 앵커 공유" 단추를 클릭 하 여 HoloLens에서 만든 azure 앵커를 공유 합니다.

7. 다른 HoloLens에서 공유 azure 앵커를 수신 하려면 "Azure GLOBAL.ASA 세션 시작"을 클릭 하 여 현재 GLOBAL.ASA 세션을 시작 하 고 가져옵니다.

8. "Azure 앵커 가져오기" 단추를 클릭 하 여 다른 HoloLens에서 공유 azure 앵커를 가져옵니다.

   > 참고: 개별 단추의 해당 작업에 대 한 모든 세부 정보가 디버그 창에 표시 됩니다.

## <a name="congratulations"></a>축하합니다.

이 단원에서는 Azure의 강력한 새 공간 앵커를 통합 하 여 공유 환경에서 공동 배치 된 장치를 맞추는 방법에 대해 알아보았습니다. 이렇게 하면 공유 모듈도 종료 됩니다. 새 Photon 계정을 설정 하 고, Photon 및 THIS를 새 Unity 응용 프로그램에 통합 하 고, 아바타 및 공유 개체를 구성 하 고, 마지막으로,를 사용 하 여 여러 참가자를 정렬 하는 방법을 배웠습니다. 

