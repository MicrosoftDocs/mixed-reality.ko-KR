---
title: HoloLens 2에 대 한 모듈을 공유 학습 MR
description: HoloLens 2 응용 프로그램에서 다중 사용자 공유 환경을 구현 하는 방법을 알아보려면이 과정을 완료 합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: 2a16d318c6d749bcbf6ed9db0d6cd2228a6ea06e
ms.sourcegitcommit: 78e21e887bf4357c96c9ab2164559d610e8c041e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67465208"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a>Azure 공간 앵커 및 공유 환경이

이 단원에서는 공유 경험에 공간 앵커 ASA (Azure)를 통합 하는 방법에 알아봅니다. ASA에는 여러 배치 장치를 공통 참조 인 경우 모든 참가자가 동일한 물리적 위치에서 개체를 볼 수 있도록 해당 실제 환경 앵커 가상 환경을 할 수 있습니다.

이 단원에서는 진행 하기 전에 ASA 기본 사항, Azure 계정 및 리소스 만들기 및 공유 경험에 ASA 통합 수 전에 필요 없는 다른 기본 빌딩 블록 다룰 ASA 학습 모듈을 완료 해야 합니다.

목표:

- ASA multi-device 맞춤에 대 한 공유 환경으로 통합
- ASA 로컬 공유 환경의 컨텍스트에서 작동 하는 방법의 기본 사항 배우기

### <a name="instructions"></a>지침

1. 이전 단원 (control + S)에서 프로젝트를 저장 하 고 쉽게 필요할 때 다시 찾을 수 있도록 "HLSharedProjectMainPart5.unity" 이름을 합니다.

2. MixedRealityPlayspace 부모 개체 아래에 있는 TableAnchor prefab을 선택 하 여 삭제 합니다.

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)



3.  자산 이동 리소스-> 프로젝트 뷰에서 자식 있도록 SharedPlayground 개체 위에 TableAnchor prefab을 끌어서 Prefabs,-> 합니다.
4.  MixedRealityPlayspace 부모 개체, TableAnchor 개체를 확장 하 고도 단추 개체를 확장 합니다. 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. 이제 계층의 ShareAzureAnchorButton를 선택 하 고 주의가 Inaspector 패널로 이동 합니다. 아래 이미지에 표시 된 드롭다운 메뉴를 스크롤하십시오 AnchorModuleScript를 선택 하 고 ShareAnchorNetework()를 클릭 합니다.

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. GetAzureAnchorButton 선택 (4 단계 참조) 하 고 [관리자] 패널에 다시 이동 합니다. 아래 이미지에 표시 된 드롭다운 메뉴를 스크롤합니다 선택 AnchorModuleScript, 및 GetSharedAnchorNetwork()를 클릭 하 고 저장 합니다.

![Module3hapter5step7im](images/module3chapter5step7im.PNG)




## <a name="congratulations"></a>축하합니다.

이 단원에서는 Azure의 강력한 새 공간 앵커 공유 환경에서 공동 배치 장치에 맞게 통합 하는 방법을 배웠습니다. 이 단원에는 공유 모듈으로 마칩니다. 아바타 및 공유 개체를 구성 하 고 마지막 ASA를 사용 하 여 여러 참가자를 맞추는 새 Photon 계정 설정, Photon 및 예제를 새 Unity 응용 프로그램을 통합 하는 방법을 알게 되었습니다. 

