---
title: Azure 공간 앵커 자습서-3. Azure 공간 고정 피드백 표시
description: 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 알아보려면 이 과정을 완료합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, Hololens
ms.openlocfilehash: 77d639a88d8b4c71dc5fbe1c78565c4c3f91d36c
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438419"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a>3. Azure 공간 고정 피드백 표시

이 단원에서는 Azure 공간 앵커를 사용할 때 앵커 검색, 이벤트 및 상태에 대 한 피드백을 사용자에 게 제공 하는 방법을 알아봅니다.

## <a name="objectives"></a>목표

* 현재 GLOBAL.ASA 세션에 대 한 중요 한 정보를 표시 하는 UI 패널을 설정 하는 방법을 알아봅니다.

* 사용자가 사용자에 게 사용할 수 있도록 하는 사용자 의견 요소 이해 및 탐색

## <a name="instructions"></a>지침

### <a name="set-up-asa-feedback-ui-panel"></a>사용자 의견 피드백 설정 UI 패널

1. 이 단원에서는 "SaveAnchorToDisk" 및 "ShareAnchor" 단추를 사용 하지 않으므로 두 단추를 모두 선택 하 고 아래와 같이 검사기 패널에서 확인란의 선택을 취소 하 여 이러한 단추를 숨깁니다.
   

![module2chapter3step1im](images/module2chapter3step1im.PNG)

2. 명령 패널을 만듭니다. "명령" 단추를 마우스 오른쪽 단추로 클릭 하 고 "3D 개체"를 마우스로 가리킨 다음 "textmeshpro"를 선택 합니다.

![module2chapter3step2im](images/module2chapter3step2im.PNG)

3. 장면의 지침과 일치 하도록 텍스트의 크기와 위치를 조정 합니다. 또한 모든 텍스트의 맞춤이 가운데 맞춤 인지 확인 합니다. 그런 다음 아래 이미지에 나와 있는 것 처럼 텍스트 편집기에서 샘플 텍스트를 삭제 합니다.

![module2chapter3step3im](images/module2chapter3step3im.PNG)

4. TextMeshPro 개체의 이름을 "FeedbackPanel"로 변경 합니다.
   

![module2chapter3step4im](images/module2chapter3step4im.PNG)

5. 프로젝트 패널에서 "자산"을 선택 하 고 마우스 오른쪽 단추를 클릭 한 다음 "탐색기에서 표시"를 선택 합니다.
   

![module2chapter3step4im](images/module2chapter3step5im.PNG)

다음 몇 단계에서 필요한 파일을 다운로드 하려면 [여기](https://onedrive.live.com/?authkey=%21ABXEC8PvyQu8Qd8&id=5B7335C4342BCB0E%21395636&cid=5B7335C4342BCB0E) 를 클릭 하세요.

6. 탐색기가 열리면 자산 폴더와 "ASAmodulesAssets" 폴더를 차례로 선택한 다음 앵커 피드백 스크립트와 anchor 모듈 스크립트 파일을 폴더에 복사 합니다. 

![module2chapter3step5im](images/module2chapter3step6im.PNG)

> 참고: 이전을 덮어쓸지 아니면 이전을 유지할지를 묻는 팝업 메시지가 표시 되 면 덮어쓰기를 선택 합니다.

7. 자산 폴더로 돌아갑니다. 그런 다음 "AzureSpatialAnchorsPlugin" 폴더로 이동 하 고 예제 폴더와 마지막으로 Scripts 폴더를 차례로 이동 합니다. 그런 다음 Azure 공간 앵커 데모 래퍼를 해당 폴더에 복사 합니다. 

![module2chapter3step8im](images/module2chapter3step7im.PNG)

8. 파일이 업로드 되 면 ASA_feedback 계층 구조에서 "feedbackpanel" 텍스트를 선택 하 고 "구성 요소 추가"를 클릭 한 다음, 표시 되 면이를 검색 하 고 선택 하 여 앵커 피드백 스크립트를 추가 합니다. 

![module2chapter3step8im](images/module2chapter3step8im.PNG)

9. 아래 그림에 표시 된 것 처럼 "feedbackPanel" 텍스트 개체를 ASA_Feedback 계층에서 스크립트 아래의 빈 슬롯으로 끌어 옵니다. 

![module2chapter3step9im](images/module2chapter3step9im.PNG)

## <a name="congratulations"></a>축하합니다.

이 단원에서는 사용자에 게 실시간 피드백을 제공 하기 위해 Azure 공간 고정 환경의 현재 상태를 표시 하는 UI 패널을 만드는 방법을 배웠습니다.


