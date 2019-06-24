---
title: HoloLens 2에 대 한 모듈을 공유 학습 MR
description: HoloLens 2 응용 프로그램에서 다중 사용자 공유 환경을 구현 하는 방법을 알아보려면이 과정을 완료 합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: 9f4a0c0cc37ab097a60c44891d56fa65f6032418
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326453"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a>Azure 공간 앵커 및 공유 환경이

이 단원에서는 공유 경험에 공간 앵커 ASA (Azure)를 통합 하는 방법을 배웁니다. ASA에 대 한 일반적인 이해를 누른 경우 모든 참가자가 동일한 물리적 위치에서 개체를 볼 수 있도록 해당 실제 환경과 가상 고정 하려면 환경에 여러 배치 장치를 수 있습니다.

이 단원에서는 진행 하기 전에 ASA 기본 사항, Azure 계정 및 리소스 만들기 및 공유 경험에 ASA 통합 수 전에 필요 없는 다른 기본 빌딩 블록 다룰 ASA 학습 모듈을 완료 해야 합니다.

목표:

- ASA multi-device 맞춤에 대 한 공유 환경으로 통합
- ASA 로컬 공유 환경의 컨텍스트에서 작동 하는 방법의 기본 사항 배우기

### <a name="instructions"></a>지침

1. 이전 단원 (control + S)에서 프로젝트를 저장 하 고 쉽게 필요할 때 다시 찾을 수 있도록 "HLSharedProjectMainPart5.unity" 이름을 합니다.

2. "MixedRealityPlayspace" 부모 개체 아래에 있는 TableAnchor prefab을 선택 하 여 삭제 합니다.

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

3. 이전 단원 중 일부와 마찬가지로 얻을 수 있는 새 사용자 지정 패키지를 가져올 [여기 있습니다.](placeholderlink)

![Module3Chapter5step3im](images/module3chapter5step3im.PNG)

4. 을 가져온 후 프로젝트 패널에서 "prefabs" 폴더에서 새로 업데이트 된 테이블 앵커 (이전 단계에서 가져온 unity 패키지)에서 가져올 놓습니다 부모 개체 "MixedRealityPlayspace."

![Module3hapter5step4im](images/module3chapter5step4im.PNG)

5. "MixedRealityPlayspace" 부모 개체를 "TableAnchor" 개체를 확장 하 고 "단추" 개체를 확장 합니다. 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

6. 이제 계층의 "ShareAzureAnchorButton"를 선택 하 고 주의가 검사기 패널로 이동 합니다. 아래 이미지에 표시 된 드롭다운 메뉴를 스크롤하십시오 "AnchorModuleScript"를 선택 하 고 "ShareAnchorNetework()." 클릭

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

7. 6 단계와 마찬가지로 "GetAzureAnchorButton"를 선택 하 고 [관리자] 패널에 다시 이동 합니다. 아래 이미지에 표시 된 드롭다운 메뉴를 스크롤하십시오 "AnchorModuleScript"를 선택 하 고 "GetSharedAnchorNetwork()." 클릭 다음 저장 합니다.

![Module3hapter5step7im](images/module3chapter5step7im.PNG)




## <a name="congratulations"></a>축하합니다.

이 단원에서는 Azure의 강력한 새 공간 앵커 공유 환경에서 공동 배치 장치에 맞게 통합 하는 방법을 배웠습니다. 이 단원에는 공유 모듈으로 마칩니다. 아바타 및 공유 개체를 구성 하 고 마지막 ASA를 사용 하 여 여러 참가자를 맞추는 새 Photon 계정 설정, Photon 및 예제를 새 Unity 응용 프로그램을 통합 하는 방법을 알게 되었습니다. 

