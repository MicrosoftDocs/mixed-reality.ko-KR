---
title: 3. 혼합 현실용 프로젝트 설정
description: Unreal Engine 4와 Mixed Reality Toolkit UX Tools 플러그 인을 사용하여 간단한 체스 앱을 만드는 자습서 시리즈 3/6부
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, 자습서, 시작, mrtk, uxt, UX Tools, 설명서
ms.openlocfilehash: 105e817e54f7de12afdcab9fde1dfce0c38ff4a7
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376385"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a>3. 혼합 현실용 프로젝트 설정

## <a name="overview"></a>개요

이전 자습서에서는 체스 앱 프로젝트를 설정했습니다. 이 섹션에서는 혼합 현실 개발을 위한 앱을 설정하는 과정을 안내합니다. 즉, AR 세션을 추가합니다. 이 작업에 대해 ARSessionConfig 데이터 자산을 사용하게 되며 여기에는 공간 매핑 및 폐색과 같은 유용한 AR 설정이 많이 있습니다. 더 자세한 내용이 필요한 경우 Unreal Engine 설명서에서 [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) 자산과 [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html) 클래스에 대해 상세 정보를 제공합니다.

## <a name="objectives"></a>목표
* Unreal Engine의 AR 설정 작업 
* ARSessionConfig 데이터 자산 사용
* 폰 및 게임 모드 설정

## <a name="adding-the-session-asset"></a>세션 자산 추가
Unreal의 AR 세션은 스스로 발생하지 않습니다. 세션을 사용하려면 다음 작업을 위한 ARSessionConfig 데이터 자산이 필요합니다.

1. **콘텐츠 브라우저**에서 **새로 추가 > 기타 > 데이터 자산**을 클릭합니다. 루트 **Content** 폴더 수준에 있는지 확인합니다. 
    * **ARSessionConfig**를 선택하고 **선택**을 클릭한 다음, 자산의 이름을 **ARSessionConfig**로 지정합니다.

![데이터 자산 만들기](images/unreal-uxt/3-createasset.PNG)

3. **ARSessionConfig**를 두 번 클릭하여 열고 모든 기본 설정을 그대로 둔 다음, **저장**을 누릅니다. 주 창으로 돌아갑니다. 

![AR 세션 구성](images/unreal-uxt/3-arsessionconfig.PNG)

작업이 완료되면 다음 단계는 수준이 로드될 때 AR 세션이 시작되고 수준이 종료될 때 중지되도록 하는 것입니다. 다행이 Unreal에는 수준 전체 글로벌 이벤트 그래프 역할을 하는 **수준 청사진**이라는 특수 청사진 종류가 있습니다. **수준 청사진**에서 ARSessionConfig 자산을 연결하면 게임 재생이 시작될 때 AR 세션이 즉시 실행됩니다.

1. 편집기 도구 모음에서 **청사진 > 수준 청사진 열기**를 클릭합니다. 

![수준 청사진 열기](images/unreal-uxt/3-level-blueprint.PNG)

5. 실행 노드(화살표 아이콘)를 **Event BeginPlay**에 끌어다 놓습니다. **AR 세션 시작** 노드를 검색하고 Enter 키를 누릅니다.  
    * **세션 구성**에서 **자산 선택**을 클릭하고 **ARSessionConfig** 자산을 선택합니다. 

![AR 세션 시작](images/unreal-uxt/3-start-ar-session.PNG)

6. 마우스 오른쪽 단추로 EventGraph의 아무 곳을 클릭하고, 새 **Event EndPlay** 노드를 만듭니다. 실행 핀을 끌어서 놓습니다. **AR 세션 중지** 노드를 검색하고 Enter 키를 누릅니다. 수준이 종료될 때 AR 세션이 중지되지 않으면 헤드셋으로 스트림하는 동안 앱을 다시 시작할 때 특정 기능이 작동하지 않을 수 있습니다. 
    * **컴파일**을 누른 다음, **저장**하고 주 창으로 돌아갑니다.

![AR 세션 중지](images/unreal-uxt/3-stoparsession.PNG)

## <a name="create-a-pawn"></a>폰 만들기
이 시점에서 프로젝트에는 여전히 플레이어 개체가 필요합니다. Unreal에서 **폰**은 게임의 사용자를 나타내지만 여기서는 HoloLens 2 환경이 됩니다.

1. **Content** 폴더에서 **새로 추가 > 청사진 클래스**를 클릭하고 아래에서 **모든 클래스**섹션을 확장합니다. 
    * **DefaultPawn**을 검색하고 **선택**을 클릭한 다음, **MRPawn**이라고 이름을 지정하고 자산을 두 번 클릭하여 엽니다. 

![DefaultPawn에서 상속하는 새 폰 만들기](images/unreal-uxt/3-defaultpawn.PNG)

> [!NOTE]
> 기본적으로 폰에는 메시 및 충돌 구성 요소가 있습니다. 대부분의 Unreal 프로젝트에서 폰은 다른 구성 요소와 충돌할 수 있는 고정 개체입니다. 혼합 현실에서 폰과 사용자는 같기 때문에 충돌 없이 홀로그램을 통과하고자 합니다. 

2. **구성 요소** 패널에서 **CollisionComponent**를 선택하고 **세부 정보** 패널의 **충돌** 섹션까지 아래로 스크롤합니다. 
    * **충돌 기본 설정** 드롭다운을 클릭하고 값을 **NoCollision**으로 변경합니다. 
    * **MeshComponent**에 대해서도 동일한 작업을 수행합니다.

![폰의 충돌 사전 설정 조정](images/unreal-uxt/3-nocollision.PNG)

3. **구성 요소** 패널에서 **구성 요소 추가 > 카메라**를 클릭하고 이름을 **카메라**로 지정합니다. 이렇게 하면 플레이어 카메라가 HoloLens 2 디바이스와 함께 움직일 수 있습니다.

4. 청사진을 **컴파일**하고 **저장**합니다.

여기에서 작업을 완료하면 주 창으로 돌아갑니다.

## <a name="create-a-game-mode"></a>게임 모드 만들기
혼합 현실 설정의 마지막 부분은 게임 모드입니다. 게임 모드는 사용할 기본 폰을 포함하여 게임 또는 환경에 대한 여러 설정을 결정합니다.

1.  **Content** 폴더에서 **새로 추가 > 청사진 클래스**를 클릭하고 아래에서 **모든 클래스**섹션을 확장합니다. 
    * **게임 보드 기본**을 검색하고 이름을 **MRGameMode**로 지정한 다음, 두 번 클릭하여 엽니다. 

![콘텐츠 브라우저의 MRGameMode](images/unreal-uxt/3-gamemode.PNG)

2.  **세부 정보** 패널의 **클래스** 섹션으로 이동하고 **기본 폰 클래스**를 **MRPawn**으로 변경합니다. 
    * **컴파일**을 누른 다음, **저장**하고 주 창으로 돌아갑니다. 

![기본 폰 클래스 설정](images/unreal-uxt/3-setpawn.PNG)

3.  **편집 > 프로젝트 설정**을 선택하고 왼쪽의 목록에서 **지도 및 모드**를 클릭합니다. 
    * **기본 모드**를 확장하고 **기본 게임 모드**를 **MRGameMode**로 변경합니다. 
    * **기본 지도**를 확장하고 **EditorStartupMap** 및 **GameDefaultMap**을 **주**로 변경합니다. 이렇게 하면 편집기를 닫았다가 다시 열 때나 게임을 플레이할 때 주 맵이 기본적으로 선택됩니다.

![프로젝트 설정 - 맵 및 모드](images/unreal-uxt/3-mapsandmodes.PNG)

프로젝트의 혼합 현실 설정이 완료되었으므로 이제 다음 자습서로 이동하여 사용자 입력을 장면에 추가할 수 있습니다. 

[다음 섹션: 4. 대화형 장면 만들기](unreal-uxt-ch4.md)