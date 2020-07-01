---
title: 2. 프로젝트 및 첫 번째 애플리케이션 초기화
description: Unreal Engine 4와 Mixed Reality Toolkit UX Tools 플러그 인을 사용하여 간단한 체스 앱을 만드는 자습서 시리즈 2/6부
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, 자습서, 시작, mrtk, uxt, UX Tools, 설명서
ms.openlocfilehash: 150fee721bb9cd72d287737aca4262bd87dccba8
ms.sourcegitcommit: 7ca383ef1c5dc895ca2a289435f2e9d4c1ee6e65
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85345733"
---
# <a name="2-initializing-your-project-and-first-application"></a>2. 프로젝트 및 첫 번째 애플리케이션 초기화

## <a name="overview"></a>개요

이 첫 번째 자습서에서는 HoloLens 2용 새 Unreal 애플리케이션을 시작합니다. 여기에는 HoloLens 플러그 인 추가, 수준 만들기 및 조명, 게임 게시판과 체스 말로 채우기가 포함됩니다. 3D 체스 말과 개체 재질용으로 미리 만들어진 자산을 사용하므로 처음부터 모든 것을 새롭게 모델링하는 것이 아닙니다. 이 자습서의 끝 부분에서는 혼합 현실에 사용할 수 있는 빈 캔버스를 제공합니다.

계속하기 전에 [시작](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch1) 페이지에서 모든 필수 구성 요소를 갖추었는지 확인합니다.

## <a name="objectives"></a>목표
* HoloLens 개발을 위한 Unreal 프로젝트 구성
* 자산 가져오기 및 장면 설정
* 청사진을 사용하여 행위자 및 스크립트 수준 이벤트 만들기

## <a name="creating-a-new-unreal-project"></a>새 Unreal 프로젝트 만들기
가장 먼저 필요한 것은 작업할 프로젝트입니다. HoloLens용 Unreal 앱을 처음으로 만드는 경우 Epic Launcher에서 [지원 파일을 다운로드](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch6#packaging-and-deploying-the-app)해야 합니다.

1. Unreal Engine 실행

2. **새 프로젝트 범주**에서 **게임**을 선택하고 **다음**을 클릭합니다. 

![게임 프로젝트 템플릿 선택](images/unreal-uxt/2-gamestemplate.png)

3. **빈** 템플릿을 선택하고 **다음**을 클릭합니다. 

![빈 템플릿 선택](images/unreal-uxt/2-template.PNG)

4. **C++** , **확장 가능한 3D 또는 2D, 모바일/태블릿**을 선택하고 **프로젝트 설정**으로 **시작 콘텐츠 없음**을 선택합니다. 
    * 저장 위치를 선택하고 **프로젝트 만들기**를 클릭합니다. 

> [!NOTE]
> 나중에 섹션 4에서 설정할 UX Tools 플러그 인을 빌드하려면 Blueprint 프로젝트 대신 C++ 프로젝트를 선택해야 합니다.

![초기 프로젝트 설정](images/unreal-uxt/2-project-settings.PNG)

Unreal 편집기에서 프로젝트가 자동으로 열리므로, 다음 섹션에 대한 준비가 완료되었습니다.

## <a name="enabling-required-plugins"></a>필수 플러그 인 사용
장면에 개체를 추가하려면 먼저 두 플러그 인을 사용하도록 설정해야 합니다.

1. **편집 > 플러그 인**을 열고 기본 제공 옵션 목록에서 **증강 현실**을 선택합니다. 
    * **HoloLens**까지 아래로 스크롤하고 **사용**을 선택합니다. 

![HoloLens 플러그 인 사용](images/unreal-uxt/2-plugins.PNG)

2. 기본 제공 옵션 목록에서 **가상 현실**을 선택합니다. 
    * **Microsoft Windows Mixed Reality**까지 아래로 스크롤하고, **사용**을 선택한 다음, 편집기를 다시 시작합니다. 

![Windows Mixed Reality 플러그 인 사용](images/unreal-uxt/2-virtual-reality-plugin.PNG)

> [!NOTE]
> 두 플러그 인은 HoloLens 2 개발에 필요합니다.

작업이 완료되면 회사에 대한 빈 수준이 준비됩니다.

## <a name="creating-a-level"></a>수준 만들기
다음 작업은 참조 및 규모에 대한 시작 지점과 큐브를 사용하여 간단한 플레이어 설정을 만드는 것입니다.

1. **파일 > 새 수준**을 선택하고 **빈 수준**을 선택합니다. 이제 뷰포트의 기본 장면이 비어 있습니다.

2. **모드** 탭에서 **기본**를 선택하고 장면으로 **PlayerStart**를 끌어옵니다. 
    * **세부 정보** 탭에서 **위치**를 **X = 0**, **Y = 0** 및 **Z = 0**으로 설정합니다. 그러면 앱이 시작될 때 장면의 가운데에 사용자가 설정됩니다.

![PlayerStart를 사용하는 뷰포트](images/unreal-uxt/2-playerstart.PNG)

3. **기본** 탭에서 **큐브**를 장면으로 끌어옵니다. 
    * **위치**를 **X = 50**, **Y = 0**, **Z = 0**으로 설정합니다. 그러면 시작 시점에 큐브가 플레이어와 50cm 떨어져 배치됩니다. 
    * **배율**을 **X = 0.2**, **Y = 0.2**, **Z = 0.2**로 변경하여 큐브를 축소합니다. 

장면을 테스트하기 전에 마지막으로 장면에 조명을 추가하지 않으면 큐브를 볼 수 없습니다.

4. **모드** 패널에서 **조명** 탭으로 전환하고 **방향성 광원**을 장면으로 끌어옵니다. **PlayerStart** 위에 조명을 배치하면 볼 수 있습니다.

![조명이 추가된 뷰포트](images/unreal-uxt/2-light.PNG)

5. **파일 > 현재 저장**으로 이동하고, 수준 이름을 **Main**으로 지정한 후 **저장**을 클릭합니다. 

장면 집합에서 도구 모음의 **재생**을 눌러 큐브의 작동을 확인합니다. 작업을 감상한 후 **Esc**를 눌러 애플리케이션을 중지합니다.

![뷰포트의 큐브](images/unreal-uxt/2-cube.PNG)

이제 장면을 설정했으므로 체스 보드와 말에서 추가를 시작하여 애플리케이션 환경을 다듬어갈 수 있습니다.

## <a name="importing-assets"></a>자산 가져오기
이 때는 장면이 비어 있지만 미리 준비된 자산을 프로젝트로 가져오면 이 상황을 해결할 수 있습니다.

1. [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) 자산 폴더를 다운로드하고 압축을 풉니다.

2. **콘텐츠 브라우저**에서 **새로 추가 > 새 폴더**를 클릭하고 이름을 **ChessAssets**로 지정합니다. 
    * 새 폴더를 두 번 클릭합니다. 여기가 3D 자산을 가져올 위치입니다.

![소스 패널 표시 또는 숨기기](images/unreal-uxt/2-showhidesources.PNG)

3. **콘텐츠 브라우저**에서 **가져오기**를 클릭하고 압축을 푼 자산 폴더의 모든 항목을 선택한 다음, **열기**를 클릭합니다. 
    * 이 폴더에는 FBX 형식의 체스 보드 및 말용 3D 개체 메시와, 재질에 사용할 TGA 형식의 질감 맵이 들어 있습니다.  

4. FBX 가져오기 옵션 창이 표시되면 **재질** 섹션을 확장하고 **재질 가져오기 메서드**를 **재질 생성 안 함**으로 변경합니다.
    * **모두 가져오기**를 클릭합니다.

![FBX 옵션 가져오기](images/unreal-uxt/2-nocreatemat.PNG)

이제 자산 작업은 완료되었습니다. 다음 작업 집합은 청사진을 사용하여 애플리케이션의 구성 요소를 만드는 것입니다.

## <a name="adding-blueprints"></a>청사진 추가

1. **콘텐츠 브라우저**에서 **새로 추가 > 새 폴더**를 클릭하고 이름을 **Content Browser**로 지정합니다. 

> [!NOTE]
> [청사진](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html)은 새로운 유형의 행위자 및 스크립트 수준 이벤트를 만들기 위한 노드 기반 인터페이스를 제공하는 특수 자산입니다. 

2. **Blueprints** 폴더를 두 번 클릭한 다음, 마우스 오른쪽 단추를 클릭하여 **청사진 클래스**를 선택합니다.         
    * **행위자**를 클릭하고 청사진의 이름을 **Board**로 지정합니다. 

![청사진의 부모 클래스를 선택합니다.](images/unreal-uxt/2-bpparent.PNG)

이제 새 **보드** 청사진이 다음 스크린샷에서처럼 **Blueprints** 폴더에 표시됩니다. 

![새 보드 청사진](images/unreal-uxt/2-bpboard.PNG)

만든 개체에 재질을 추가할 준비가 완료되었습니다.

## <a name="working-with-materials"></a>재질 작업
사용자가 만든 개체는 기본적으로 회색으로 밋밋하게 표시됩니다. 개체에 재질과 메시를 추가하는 작업이 이 자습서의 마지막 과제 집합입니다.

1. **보드**를 두 번 클릭하여 청사진 편집기를 엽니다. 

2. **구성 요소** 패널에서 **구성 요소 추가 > 장면**을 클릭하고 이름을 **Root**로 지정합니다. 아래 스크린샷에는 **Root**가 **DefaultSceneRoot**의 자식으로 표시되어 있습니다.

![루트 바꾸기](images/unreal-uxt/2-root-blueprint.PNG)


3. **Root**를 클릭하고 끌어서 **DefaultSceneRoot**에 놓아 바꾸고 뷰포트의 구를 제거합니다. 

![루트 바꾸기](images/unreal-uxt/2-root.PNG)


4. **구성 요소** 패널에서 **구성 요소 추가 > 정적 메시**를 클릭하고 이름을 **SM_Board**로 지정합니다. **Root**에 자식 개체로 표시됩니다.

![정적 메시 추가](images/unreal-uxt/2-sm-board.PNG)

4. **SM_Board**를 클릭하고 **세부 정보** 패널의 **정적 메시** 섹션까지 아래로 스크롤한 다음, 드롭다운에서 **ChessBoard**를 선택합니다. 

![뷰포트의 보드 메시](images/unreal-uxt/2-sm-board-view.PNG)

5.  **세부 정보** 패널에서 **재질** 섹션을 확장하고 드롭다운 목록에서 **새 자산 만들기 > 재질**을 클릭합니다. 
    * 이 재질의 이름을 **M_ChessBoard**로 지정하고 **ChessAssets** 폴더에 저장합니다. 

![새 장면 만들기](images/unreal-uxt/2-newmat.PNG)

6.  **M_ChessBoard** 재질 이미지를 두 번 클릭하여 재질 편집기를 엽니다. 

![재질 편집기 열기](images/unreal-uxt/2-material-editor.PNG)

7. 재질 편집기를 마우스 오른쪽 단추로 클릭하고 **질감 샘플**을 검색합니다. 
    * **세부 정보** 패널의 **재질 식 질감 기본** 섹션에서 **질감**을 **ChessBoard_Albedo**로 설정합니다. 
    * **RGB** 출력 핀을 **M_ChessBoard**의 기본 색 핀으로 끌어옵니다. 

![기본 색 설정](images/unreal-uxt/2-boardalbedomat.PNG)

8.  다음 설정을 통해 이전 단계를 4번 더 반복하여 4개의 **질감 샘플** 노드를 만듭니다.
    * **질감**을 **ChessBoard_AO**로 설정하고 **RGB**를 **앰비언트 어클루전** 핀에 연결합니다.
    * **질감**을 **ChessBoard_Metal**로 설정하고 **RGB**를 **메탈릭** 핀에 연결합니다. 
    * **질감**을 **ChessBoard_Normal**로 설정하고 **RGB**를 **기본** 핀에 연결합니다.
    * **질감**을 **ChessBoard_Rough**로 설정하고 **RGB**를 **조도** 핀에 연결합니다. 
    * **Save**을 클릭합니다. 

![나머지 텍스처 연결](images/unreal-uxt/2-boardmat.PNG)

계속하기 전에 재질 설정이 위 스크린샷처럼 표시되는지 확인합니다.

## <a name="populating-the-scene"></a>장면 채우기
**Board** 청사진으로 돌아가면 방금 만든 재질이 적용된 것을 볼 수 있습니다. 이제 장면을 설정하기만 하면 됩니다. 먼저 다음과 같은 속성을 변경하여 보드가 장면에 배치될 때 올바른 크기와 정확한 각도가 되게 합니다.
1.  **배율**을 **(0.05, 0.05, 0.05)** , **Z 회전**을 **90**으로 설정합니다. 
    * 상단 도구 모음에서 **컴파일**을 클릭한 다음, **저장**하고 주 창으로 돌아갑니다. 

![재질이 적용된 체스 보드](images/unreal-uxt/2-chessboard.PNG)

2.  **큐브 > 편집 > 삭제**를 마우스 오른쪽 단추로 클릭하고 **콘텐츠 브라우저**에서 **Board**를 뷰포트로 끌어옵니다. 
    * **위치**를 **X = 80**, **Y = 0**, **Z = -20**으로 설정합니다. 

3.  **재생** 단추를 클릭하여 새 보드를 레벨에서 확인합니다. **Esc** 키를 눌러 편집기로 돌아갑니다. 

이제 보드에서 했던 것과 같은 단계를 따라 체스 말을 만듭니다.

1. **Blueprints** 폴더로 이동하고 마우스 오른쪽 단추를 클릭하여 **청사진 클래스**와 **행위자**를 차례로 선택합니다. 행위자의 이름을 **WhiteKing**으로 지정합니다.

2. **WhiteKing**을 두 번 클릭하여 청사진 편집기에서 열고 **구성 요소 추가 > 장면**을 클릭한 다음, 이름을 **Root**로 지정합니다. 
    * **Root**를 끌어서 **DefaultSceneRoot**에 놓아 바꿉니다. 

3. **구성 요소 추가 > 정적 메시**를 클릭하고 이름을 **SM_King**으로 지정합니다. 
    * 세부 정보 창에서 **정적 메시**를 **Chess_King**으로, **재질**을 새 재질인 **M_ChessWhite**로 설정합니다. 

4. 재질 편집기에서 **M_ChessWhite**을 열고 다음 **질감 샘플** 노드를 다음에 연결합니다.
    * **질감**을 **ChessWhite_AO**로 설정하고 **RGB**를 **앰비언트 어클루전** 핀에 연결합니다.
    * **질감**을 **ChessWhite_Metal**로 설정하고 **RGB**를 **메탈릭** 핀에 연결합니다. 
    * **질감**을 **ChessWhite_Normal**로 설정하고 **RGB**를 **기본** 핀에 연결합니다.
    * **질감**을 **ChessWhite_Rough**로 설정하고 **RGB**를 **조도** 핀에 연결합니다. 
    * **Save**을 클릭합니다. 

계속하기 전에 **M_ChessKing** 재질이 다음 이미지와 같이 표시됩니다.

![체스 킹 재질 만들기](images/unreal-uxt/2-chesskingmat.PNG)

거의 완료되었습니다. 새 체스 말을 장면에 추가하기만 하면 됩니다. 

1. **WhiteKing** 청사진으로 돌아가서 **배율**을 **(0.05, 0.05, 0.05)** , **Z 회전**을 **90**으로 변경합니다.
    * 청사진을 컴파일하고 저장한 다음, 주 창으로 돌아갑니다. 

2.  **WhiteKing**을 뷰포트에 끌어오고 **World Outliner** 패널로 전환한 다음, **WhiteKing**을 **Board**로 끌어가 자식 개체로 만듭니다.

![월드 아웃라이너](images/unreal-uxt/2-child.PNG)

3.  **세부 정보** 패널의 **변환**에서 **WhiteKing**의 **위치**를 **X = -26**, **Y = 4**, **Z = 0**으로 설정합니다.

이제 마쳤습니다. **재생**를 클릭하여 입력된 수준의 작동을 확인하고 마무리되면 **Esc**를 누릅니다. 이 자습서에서 다룬 내용은 간단한 프로젝트의 여러 기본적인 사항이지만 이제 프로젝트로 이 시리즈의 다음 부분인 혼합 현실 설정을 진행할 수 있습니다. 

[다음 섹션: 3. 혼합 현실용 프로젝트 설정](unreal-uxt-ch3.md)
