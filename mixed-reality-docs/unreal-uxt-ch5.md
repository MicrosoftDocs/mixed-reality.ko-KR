---
title: 5. 단추 추가 및 체스 말 위치 초기화
description: Unreal Engine 4와 Mixed Reality Toolkit UX Tools 플러그인을 사용하여 간단한 체스 앱을 만드는 자습서의 5부
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, 자습서, 시작, mrtk, uxt, UX Tools, 설명서
ms.openlocfilehash: df5ea22e7097fdd3b788ec298bc1cd78c315b585
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840402"
---
# <a name="5-adding-a-button--resetting-piece-locations"></a>5. 단추 추가 및 체스 말 위치 초기화

이 섹션에서는 계속해서 Mixed Reality Toolkit UX Tools 플러그 인의 기능을 시연하고 체스 앱의 기능을 구현합니다. 새 기능을 만들고 현재 레벨에서 청사진으로 행위자의 참조를 가져오는 방법을 알아봅니다.

## <a name="objectives"></a>목표

* 프로젝트에 단추 추가
* 체스 말을 원래 위치로 보내는 새 "위치 초기화" 함수 만들기
* 단추를 누르면 새로 만든 함수를 트리거하도록 단추 연결

## <a name="create-a-function-to-reset-location"></a>위치를 초기화하는 함수 만들기

1.  **WhiteKing**을 엽니다. **내 청사진** 패널에서 **함수** 섹션 옆에 있는 "+" 단추를 클릭하여 새 함수를 만듭니다. 이 함수 이름을 "위치 초기화"로 지정합니다. 

2.  새로 만든 **위치 초기화** 청사진에서 실행 핀을 청사진 그리드의 아무 위치로 끌어다 놓고 **SetActorRelativeTransform** 노드를 호출합니다. 이 함수는 부모를 기준으로 행위자의 변환(위치, 회전 및 배율)을 설정합니다. 이 함수를 사용하여 보드에서 킹의 위치를 초기화할 것이며, 보드가 원래 위치에서 이동되었더라도 상관 없습니다. 위치가 X =-26, Y = 4, Z = 0인 **변환 만들기** 노드를 만들고, 새 상대 변환 입력에 연결합니다. 

![위치 초기화 함수](images/unreal-uxt/5-function.PNG)

3.  **WhiteKing**을 컴파일하고 저장합니다. 주 창으로 돌아갑니다. 

## <a name="add-a-button"></a>단추 추가

1.  **Blueprints** 폴더에서 SimpleButton을 서브클래스로 분류하는 새 청사진을 만듭니다. SimpleButton은 UX Tools 플러그 인의 일부로 제공되는 3D 단추 청사진 행위자입니다. 이 단추의 이름을 "ResetButton"으로 지정하고 두 번 클릭하여 청사진을 엽니다. 

![SimpleButton의 새 청사진을 서브클래스로 분류](images/unreal-uxt/5-subclass.PNG)

2.  **구성 요소** 패널에서 **PressableButton(상속됨)** 을 클릭합니다. [세부 정보] 패널에서 **이벤트** 섹션이 보일 때까지 스크롤합니다. **단추를 누를 때** 옆에 있는 녹색 더하기 단추를 클릭합니다. 그러면 **단추를 누를 때** 이벤트가 이벤트 그래프에 추가되고, 단추를 누르면 이 이벤트가 호출됩니다. 여기서 WhiteKing의 위치 초기화 함수를 호출합니다. 호출하려면 먼저 레벨에서 WhiteKing 행위자에 대한 참조를 가져와야 합니다. 

3.  **내 청사진** 패널에서 **변수** 섹션을 찾은 다음, **+** 단추를 클릭하여 새 변수를 추가합니다. 이 변수의 이름을 "WhiteKing"으로 지정합니다. [세부 정보] 패널에서 **변수 유형** 옆에 있는 드롭다운을 선택하고, "WhiteKing"을 검색하고, **개체 참조**를 선택합니다. 마지막으로 **편집 가능한 인스턴스** 옆의 확인란을 선택합니다. 이렇게 하면 기본 레벨에서 변수를 설정할 수 있습니다. 

![변수 만들기](images/unreal-uxt/5-var.PNG)

4.  **내 청사진 > 변수**에 있는 WhiteKing 변수를 단순 단추 이벤트 그래프로 끌어다 놓습니다. **WhiteKing 가져오기**를 선택합니다. 

5.  WhiteKing 출력 핀을 새 노드로 끌어다 놓습니다. **위치 초기화** 함수를 선택합니다. 마지막으로 **단추를 누를 때**의 나가는 실행 핀을 **위치 초기화**의 들어오는 실행 핀으로 끌어다 놓습니다. ResetButton 청사진을 **컴파일**하고 **저장**한 다음, 주 창으로 돌아갑니다. 

![단추를 누를 때 위치 초기화 함수 호출](images/unreal-uxt/5-callresetloc.PNG)

6.  **SimpleButton**을 뷰포트로 끌어다 놓고 위치를 X = 50, Y =-25, Z = 10으로 설정합니다. **기본값**에서 WhiteKing 변수의 값을 **WhiteKing**으로 설정합니다.

![변수 설정](images/unreal-uxt/5-buttonlevel.PNG)

이제 잡을 수 있는 체스 말과 보드뿐 아니라 누르면 체스 말의 위치를 초기화하는 완전한 기능을 갖춘 단추를 사용하는 혼합 현실 앱이 생겼습니다. 이 시점까지 완료된 앱은 [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp)에서 찾을 수 있습니다. 사용자가 단추를 누를 때 보드 전체를 초기화하도록, 이 자습서의 범위를 넘어서 나머지 체스 말을 자유롭게 설정해 보세요.

![뷰포트에서 장면 종료](images/unreal-uxt/5-endscene.PNG)

[다음 섹션: 6. 패키징 후 디바이스 또는 에뮬레이터에 배포](unreal-uxt-ch6.md)