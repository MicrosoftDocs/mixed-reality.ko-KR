---
title: 5. 단추 추가 및 체스 말 위치 초기화
description: Unreal Engine 4와 Mixed Reality Toolkit UX Tools 플러그 인을 사용하여 간단한 체스 앱을 만드는 자습서 시리즈 5/6부
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, 자습서, 시작, mrtk, uxt, UX Tools, 설명서
ms.openlocfilehash: 49cab5c5a8c6736b800b5ba05de2c88edf008008
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330270"
---
# <a name="5-adding-a-button--resetting-piece-locations"></a>5. 단추 추가 및 체스 말 위치 초기화


## <a name="overview"></a>개요

이전 자습서에서는 손 조작 행위자를 폰에, 조작자 구성 요소를 체스 보드에 추가하여 서로 상호 작용하게 했습니다. 이 섹션에서는 체스 앱의 기능을 빌드하여 계속해서 Mixed Reality Toolkit UX Tools 플러그 인을 작업합니다. 여기에는 새 함수 만들기와, 청사진의 행위자에 대한 참조를 가져오는 방법에 대한 학습이 포함됩니다. 이 섹션을 마치면 디바이스 또는 에뮬레이터에서 혼합 현실 앱을 패키징 및 배포할 준비가 됩니다.

## <a name="objectives"></a>목표

* 대화형 단추 추가
* 조각의 위치를 초기화하는 함수 만들기
* 누르면 함수를 트리거하도록 단추 연결

## <a name="creating-a-reset-function"></a>초기화 함수 만들기
먼저 장면에서 체스 위치를 원위치로 초기화하는 함수 청사진을 만듭니다. 

1.  **WhiteKing**을 열고 **내 청사진**의 **함수** 섹션 옆에 있는 **+** 아이콘을 클릭한 다음, 이름을 **Reset Location**으로 지정합니다. 

2.  청사진 표의 **Reset Location**에서 실행을 끌어서 놓고 **SetActorRelativeTransform** 노드를 만듭니다. 
    * 이 함수는 부모를 기준으로 행위자의 변환(위치, 회전 및 배율)을 설정합니다. 이 함수를 사용하여 보드에서 킹의 위치를 초기화할 것이며, 보드가 원래 위치에서 이동되었더라도 상관없습니다. 
    
3. 이벤트 그래프 안을 마우스 오른쪽 단추로 클릭하고 **변환**을 선택한 다음, **위치**를 **X = -26**, **Y = 4**, **Z = 0**으로 변경합니다.
    * **반환 값**을 **SetActorRelativeTransform**의 **새 상대 변환** 핀에 연결합니다. 

![위치 초기화 함수](images/unreal-uxt/5-function.PNG)

**컴파일**하고 주 창으로 돌아가기 전에 프로젝트를**저장**합니다. 


## <a name="adding-a-button"></a>단추 추가
이제 함수가 올바르게 설정되었으므로 다음 작업은 터치하면 작업을 실행하는 단추를 만드는 것입니다. 

1.  **새로 추가 > 청사진 클래스**를 클릭하고 **모든 클래스** 섹션을 확장한 다음, **SimpleButton**을 검색합니다. 
    * 이름을 **ResetButton**으로 지정하고 두 번 클릭하여 청사진을 엽니다.

> [!NOTE]
> **SimpleButton**은 UX Tools 플러그 인의 일부인 3D 단추 청사진 행위자입니다. . 

![SimpleButton의 새 청사진을 서브클래스로 분류](images/unreal-uxt/5-subclass.PNG)

2. **구성 요소** 패널에서 **PressableButton(상속)** 을 클릭하고 **세부 정보** 패널에서 **이벤트** 섹션까지 아래로 스크롤합니다. 
    * **단추를 누를 때** 옆에 있는 녹색 **+** 단추를 클릭하여 이벤트 그래프에 이벤트를 추가합니다. 단추를 누르면 이벤트가 호출됩니다. 
    
여기에서 **WhiteKing**의 **Reset Location** 함수를 호출하게 되는데, 수준에서 **WhiteKing** 행위자에 대한 참조가 필요합니다. 

1.  **세부 정보** 패널에서 **변수** 섹션으로 스크롤하고 **+** 단추를 클릭한 다음, 변수 이름을 **WhiteKing**으로 지정합니다. 
    * **변수 유형** 옆에 있는 드롭다운을 선택하고 **WhiteKing**을 검색한 다음, **개체 참조**를 선택합니다. 
    * **편집 가능한 인스턴스** 옆의 확인란을 선택합니다. 이렇게 하면 기본 레벨에서 변수를 설정할 수 있습니다. 

![변수 만들기](images/unreal-uxt/5-var.PNG)

2.  **내 청사진 > 변수**에 있는 WhiteKing 변수를 초기화 단추 이벤트 그래프로 끌어간 다음, **WhiteKing 가져오기**를 선택합니다. 

## <a name="firing-the-function"></a>함수 실행
이제 남은 것은 단추를 누를 때 초기화 함수를 실제로 실행하는 것입니다.

1.  WhiteKing 출력 핀을 새 노드로 끌어다 놓습니다. **위치 초기화** 함수를 선택합니다. 마지막으로 **단추를 누를 때**의 나가는 실행 핀을 **위치 초기화**의 들어오는 실행 핀으로 끌어다 놓습니다. ResetButton 청사진을 **컴파일**하고 **저장**한 다음, 주 창으로 돌아갑니다. 

![단추를 누를 때 위치 초기화 함수 호출](images/unreal-uxt/5-callresetloc.PNG)

2.  **ResetButton**을 뷰포트로 끌어오고 위치를**X = 50**, **Y = -25**, **Z = 10**으로 설정합니다. **기본값**에서 **WhiteKing** 변수의 값을 **WhiteKing**으로 설정합니다.

![변수 설정](images/unreal-uxt/5-buttonlevel.PNG)

앱을 실행하고 체스 말을 새 위치로 이동한 다음, 큰 분홍색 단추를 눌러 초기화 논리가 작동하는지 확인합니다.

이제 조작할 수 있는 체스 말과 보드뿐 아니라 체스 말의 위치를 초기화하는 완전한 기능을 갖춘 단추를 사용하는 혼합 현실 앱이 생겼습니다. [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp) 리포지토리에서 이 시점까지 완료된 앱을 찾을 수 있습니다. 단추를 눌렀을 때 보드 전체를 초기화하도록, 이 자습서의 범위를 넘어서 나머지 체스 말을 자유롭게 설정해 보세요.

![뷰포트에서 장면 종료](images/unreal-uxt/5-endscene.PNG)

앱을 올바르게 패키징하여 디바이스나 에뮬레이터에 배포하는 방법을 학습하는 이 자습서의 마지막 섹션을 진행할 준비가 되었습니다.

[다음 섹션: 6. 패키징 후 디바이스 또는 에뮬레이터에 배포](unreal-uxt-ch6.md)
