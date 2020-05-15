---
title: 3. 혼합 현실용 프로젝트 설정
description: Unreal Engine 4와 Mixed Reality Toolkit UX Tools 플러그인을 사용하여 간단한 체스 앱을 만드는 자습서의 3부
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, 자습서, 시작, mrtk, uxt, UX Tools, 설명서
ms.openlocfilehash: b5b5e2de787279602341e60f2bfa29aa05ea9b31
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840622"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a>3. 혼합 현실용 프로젝트 설정

이 섹션에서는 혼합 현실 개발용으로 앱을 구성하는 과정을 안내합니다. 

## <a name="objectives"></a>목표

* ARSessionConfig, 폰 및 GameMode를 사용하여 혼합 현실 프로젝트를 설정하는 방법 알아보기

## <a name="configure-the-session"></a>세션 구성

1. 콘텐츠 브라우저에서 **Content** 폴더로 돌아갑니다. **새로 추가 > 기타 > 데이터 자산**을 클릭합니다. 

2. **ARSessionConfig**를 클래스로 선택하고, **선택**을 클릭합니다. 자산 이름을 "ARSessionConfig"로 지정합니다.

![데이터 자산 만들기](images/unreal-uxt/3-createasset.PNG)

3. ARSessionConfig를 두 번 클릭하여 엽니다. ARSessionConfig 데이터 자산에는 공간 매핑과 폐색을 포함하여 여러 가지 유용한 AR 설정이 포함되어 있습니다. ARSessionConfig에 대한 자세한 내용은 [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html)에서 Unreal Engine 설명서를 참조하세요. 우리가 하고 있는 체스 앱은 설정을 수정할 필요가 없으므로 **저장**을 누르고 주 창으로 돌아갑니다. 

![AR 세션 구성](images/unreal-uxt/3-arsessionconfig.PNG)

4. 뷰포트 위에 있는 도구 모음에서 **청사진 > 레벨 청사진 열기**를 클릭합니다. 레벨 청사진은 레벨 수준에서 글로벌 이벤트 그래프 역할을 하는 특수한 청사진입니다. 레벨의 처음부터 AR 세션 구성이 적용되도록 여기서 AR 세션을 시작하겠습니다.  

5. **Event BeginPlay**에서 실행 노드를 끌어다 놓습니다. **AR 세션 시작** 노드를 검색합니다. **세션 구성**을 클릭하고, 새로 만든 **ARSessionConfig** 자산을 선택합니다. **컴파일**을 누른 다음, **저장**합니다. 주 창으로 돌아갑니다.

![AR 세션 시작](images/unreal-uxt/3-startarsession.PNG)

## <a name="create-a-pawn"></a>폰 만들기

1.  Content 폴더에 **DefaultPawn**에서 상속하는 새 청사진을 만듭니다. Unreal에서 폰은 게임의 사용자(여기서는 HoloLens 2 환경)를 나타냅니다. 새 폰의 이름을 "MRPawn"으로 바꾸고 MRPawn을 두 번 클릭하여 엽니다. 

![DefaultPawn에서 상속하는 새 폰 만들기](images/unreal-uxt/3-defaultpawn.PNG)

2.  대부분의 Unreal 프로젝트에서 사용자가 제어하는 폰은 다른 구성 요소와 충돌하는 솔리드 개체이므로, 기본적으로 폰에는 메시 구성 요소와 충돌 구성 요소가 있습니다. 여기서는 사용자가 폰이므로 충돌을 생성하지 않고 홀로그램을 통과할 수 있어야 합니다. [구성 요소] 패널에서 **CollisionComponent**를 선택합니다. [세부 정보] 패널에서 [충돌] 섹션까지 아래로 스크롤한 다음, [충돌 사전 설정] 옆에 있는 드롭다운을 클릭합니다. 이 설정을 [폰]에서 **NoCollision**으로 변경합니다. **MeshComponent**도 똑같이 합니다. 청사진을 **컴파일**한 다음, **저장**합니다. 주 창으로 돌아갑니다. 

![폰의 충돌 사전 설정 조정](images/unreal-uxt/3-nocollision.PNG)

## <a name="create-a-game-mode"></a>게임 모드 만들기

1.  콘텐츠 브라우저의 Content 폴더에서 부모가 **게임 모드 기본**인 새 청사진을 만듭니다. 이름을 MRGameMode로 지정하고 두 번 클릭하여 엽니다. Unreal에서 게임 모드는 사용할 기본 폰을 포함하여 게임 또는 환경에 대한 여러 설정을 결정합니다. 

![콘텐츠 브라우저의 MRGameMode](images/unreal-uxt/3-gamemode.PNG)

2.  [세부 정보] 패널에서 [클래스] 섹션을 찾습니다. [기본 폰 클래스]를 DefaultPawn에서 방금 만든 **MRPawn**으로 변경합니다. **컴파일**을 누른 다음, **저장**합니다. 주 창으로 돌아갑니다. 

![기본 폰 클래스 설정](images/unreal-uxt/3-setpawn.PNG)

3.  프로젝트 설정의 마지막 단계는 MRGameMode를 기본값으로 사용하라고 Unreal에 알리는 것입니다. [프로젝트]에서 **편집 > 프로젝트 설정 > 맵 및 모드** 섹션으로 이동합니다. [기본 모드] 섹션에서 드롭다운을 클릭하고 **MRGameMode**를 선택합니다. 바로 아래에 있는 [기본 맵] 섹션에서 **EditorStartupMap** 및 **GameDefaultMap**을 **기본**으로 변경합니다. 이렇게 하면 편집기를 닫았다가 다시 열 때 기본 맵이 기본적으로 선택됩니다. 마찬가지로, 게임을 플레이할 때 기본 맵이 시작 레벨입니다. 

![프로젝트 설정 - 맵 및 모드](images/unreal-uxt/3-mapsandmodes.PNG)

[다음 섹션: 4. 대화형 장면 만들기](unreal-uxt-ch4.md)