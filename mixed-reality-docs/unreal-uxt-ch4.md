---
title: 4. 대화형 장면 만들기
description: Unreal Engine 4와 Mixed Reality Toolkit UX Tools 플러그 인을 사용하여 간단한 체스 앱을 만드는 자습서의 4부
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, 자습서, 시작, mrtk, uxt, UX Tools, 설명서
ms.openlocfilehash: 2e4d26ed4e0b8199bfc629016aea688bd1c41ef8
ms.sourcegitcommit: 09d9fa153cd9072f60e33a5f83ced8167496fcd7
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/18/2020
ms.locfileid: "83520028"
---
# <a name="4-making-your-scene-interactive"></a>4. 대화형 장면 만들기

이 섹션에서는 대화형 장면을 쉽게 만들 수 있는 도구 세트를 제공하는 Mixed Reality Toolkit UX Tools 플러그 인을 소개합니다. 이 섹션을 마치면 체스 말이 사용자 입력에 응답합니다. 

## <a name="objectives"></a>목표

* 프로젝트에 Mixed Reality Toolkit UX Tools 플러그 인 포함
* 손가락 끝에 손 조작 행위자 추가
* 조작자를 만들어 체스 보드 및 체스 말에 연결 
* 입력 시뮬레이션을 사용하여 프로젝트의 유효성 검사

## <a name="download-the-mixed-reality-toolkit-ux-tools-plugin"></a>Mixed Reality Toolkit UX Tools 플러그 인 다운로드

1.  [UX 도구 GitHub 리포지토리](https://github.com/microsoft/MixedReality-UXTools-Unreal/releases)에서 MRTK UX Tools 플러그 인의 최신 릴리스를 복제하거나 다운로드하고 압축을 풉니다.

2.  체스 프로젝트 루트 폴더에 "Plugins"라는 새 폴더를 만듭니다. 압축을 푼 UXTools 플러그 인을 이 폴더에 복사합니다. Unreal 편집기를 다시 시작합니다. 

![프로젝트 플러그 인 폴더 만들기](images/unreal-uxt/4-plugins.PNG)

3.  다시 시작한 후 UXTools 플러그 인 콘텐츠가 소스 패널에 보이지 않으면 **옵션 보기 > 플러그 인 콘텐츠 표시**를 클릭해야 할 수도 있습니다. UXTools 플러그 인은 Pointers, Input Simulation 및 Simple Button이 포함된 Content 폴더와 함수로 구분된 하위 폴더가 포함된 C++ Classes 폴더를 제공합니다.  

![플러그 인 콘텐츠 표시](images/unreal-uxt/4-showplugincontent.PNG)

## <a name="spawn-hand-interaction-actors"></a>손 조작 행위자 생성

1.  1\) 폰의 검지손가락 끝에 있는 커서를 사용하여 MRPawn을 시각화하고, 2) 폰을 통해 연결된 손 입력 이벤트를 제공하고(따라서 행위자를 직접 조작하고), 3) 손바닥에서 나가는 선을 통해 원거리 조작 입력 이벤트를 제공할 수 있도록, MRPawn에서 손 조작 행위자를 생성하는 작업부터 시작하겠습니다. **MRPawn** 청사진을 열고 **이벤트 그래프**로 이동합니다. 

2.  Event BeginPlay에서 실행 핀을 새 노드로 끌어다 놓습니다. **클래스에서 행위자 생성** 노드를 선택합니다. **클래스** 핀 옆에 있는 드롭다운을 클릭하고 **Uxt 손 조작 행위자**를 검색합니다. SpawnActor Uxt 손 조작 노드에서 실행 핀을 끌어다 놓고, Uxt 손 조작 노드 클래스에 포함된 **손 설정** 함수를 검색합니다. SpawnActor 노드의 반환 값을 손 설정 노드의 대상 핀에 연결하여 손 조작 행위자의 손을 **왼쪽**으로 설정합니다. 두 번째 **Uxt 손 조작 행위자**를 생성합니다. 이번에는 이벤트가 시작할 때 각 손에서 Uxt 손 조작 행위자가 생성되도록 손을 **오른쪽**으로 설정합니다. 

![UXT 손 조작 행위자 생성](images/unreal-uxt/4-spawnactor.PNG)

3.  다음으로, Uxt 손 조작 행위자에 초기 변환(생성할 위치) 및 소유자를 제공해야 합니다. **변환 생성** 핀 중 하나를 새 노드로 끌어다 놓습니다. **변환 만들기** 노드를 검색합니다. 손 조작 행위자는 표시되는 즉시 손으로 점프하고(UX Tools 플러그 인에 이미 작성되어 있는 코드) 그렇지 않으면 사라지기 때문에 초기 변환은 하나도 중요하지 않습니다. 그러나 SpawnActor 함수는 컴파일러 오류를 피하기 위해 입력으로 변환이 필요하므로 [변환 만들기]의 기본값을 그대로 유지하겠습니다. [변환 만들기]의 **반환 값**을 다른 손의 조작 행위자 변환 생성으로 끌어다 놓습니다. 

4.  두 SpawnActor 노드의 하단에서 **아래쪽 화살표**를 클릭하여 **소유자** 핀을 표시합니다. **소유자** 핀 중 하나를 새 노드로 끌어다 놓습니다. "자체"를 검색하고 **자체 참조 가져오기** 변수를 선택합니다. 자체 개체 참조 노드와 다른 손 조작 행위자의 소유자 핀 사이에 링크를 만듭니다. 노드 주위를 자유롭게 드래그하면서 청사진을 보다 읽기 쉽게 만듭니다. **컴파일**하고, **저장**하고, 주 창으로 돌아갑니다. 

![UXT 손 조작 행위자 설정 완료](images/unreal-uxt/4-fingerptrs.PNG)

MRTK UX Tools 플러그 인에서 제공하는 손 조작 행위자에 대한 자세한 내용은 공식 [설명서](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/HandInteraction.html)를 확인하세요.

## <a name="attach-manipulators"></a>조작자 연결

1.  다음으로, 체스 보드 및 킹 행위자에 조작자를 연결합니다. 조작자는 연결된 손 입력에 응답하는 구성 요소이며, 행위자의 변환에 조작자의 변환을 적용하여 조작자를 잡고, 회전하고, 변환할 수 있습니다. 행위자는 직접 조작할 수 있습니다. 

2.  보드 청사진을 엽니다. **구성 요소** 패널에서 **구성 요소 추가**를 클릭하고 **Uxt 일반 조작자**를 검색합니다. [세부 정보] 패널에는 한 손 조작 또는 양손 조작, 회전 모드 및 다듬기를 사용하도록 설정할 수 있는 **일반 조작자**라는 섹션이 있습니다. 원하는 모두를 자유롭게 선택한 다음, 보드를 **컴파일**하고 **저장**합니다. 

![일반 조작자 추가](images/unreal-uxt/4-addmanip.PNG)

![모드 설정](images/unreal-uxt/4-setrotmode.PNG)

3.  WhiteKing 행위자에 대해 위의 단계를 반복합니다.

MRTK UX Tools 플러그 인에서 제공하는 조작자 구성 요소에 대한 자세한 내용은 공식 [설명서](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/Manipulator.html)를 확인하세요.

## <a name="test-out-your-scene-with-simulated-hands"></a>시뮬레이션된 손으로 장면 테스트

1.  주 창에서 **재생**을 누릅니다. MRTK UX Tools 플러그 인에서 제공하는 두 개의 메시 손이 나타나고, 각 손바닥에서 선이 나갑니다. 

![뷰포트의 시뮬레이션된 손](images/unreal-uxt/4-handsim.PNG)

2.  **오른손**을 제어하려면 **왼쪽 Alt** 단추를 누릅니다. 마우스를 이동하면 손이 움직입니다. **마우스 휠**을 스크롤하면 손이 **앞으로** 또는 **뒤로** 이동합니다. 마우스 왼쪽 단추를 클릭하면 **손가락 모으기** 동작이 수행되고, 마우스 가운데 단추를 클릭하면 **찌르기** 동작이 수행됩니다.

3.  **왼손**을 제어하려면 **왼쪽 Shift** 단추를 누릅니다. 왼손을 움직이는 컨트롤은 오른손을 움직이는 컨트롤과 동일합니다. 

4.  이제 시뮬레이션된 손을 사용하여 백의 킹을 집어서 움직여 본 후 다시 내려놓으세요. 체스 보드를 조작할 수도 있습니다. 근거리 및 원거리 조작을 시험해 보세요. 체스 보드와 킹을 직접 잡을 수 있을 만큼 손이 가까워지면 손에서 나가는 선이 사라지고 검지손가락 끝에 있는 손가락 모양 커서로 바뀝니다. 

MRTK UX Tools 플러그 인에서 제공하는 시뮬레이션된 손 기능에 대한 자세한 내용은 공식 [설명서](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/InputSimulation.html)를 확인하세요.

[다음 섹션: 5. 단추 추가 및 조각 위치 재설정](unreal-uxt-ch5.md)
