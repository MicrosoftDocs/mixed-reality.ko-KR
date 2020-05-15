---
title: 2. 프로젝트 및 첫 번째 애플리케이션 초기화
description: Unreal Engine 4와 Mixed Reality Toolkit UX Tools 플러그인을 사용하여 간단한 체스 앱을 만드는 자습서의 2부
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, 자습서, 시작, mrtk, uxt, UX Tools, 설명서
ms.openlocfilehash: fc85f011ff3b186f3b4b5449b4f8ec49f0b6418f
ms.sourcegitcommit: 189a47b8712dd5b620e19815f5cf6d1ac0f29880
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82851577"
---
# <a name="2-initializing-your-project-and-first-application"></a>2. 프로젝트 및 첫 번째 애플리케이션 초기화

이 섹션에서는 HoloLens 2용 Unreal 애플리케이션을 새로 만드는 작업을 시작합니다. 

## <a name="objectives"></a>목표

* HoloLens 개발용으로 Unreal 구성
* 자산 가져오기 및 장면 설정

## <a name="create-a-new-unreal-project"></a>새 Unreal 프로젝트 만들기

1. Unreal Engine 실행

2. **새 프로젝트 범주**에서 **게임**을 선택하고 [다음]을 클릭합니다. **빈** 템플릿을 선택하고 [다음]을 클릭합니다. 

![빈 템플릿 선택](images/unreal-uxt/2-template.PNG)

3. [프로젝트 설정]에서 **C++, 확장 가능한 3D 또는 2D, 모바일/태블릿**을 선택하고, **시작 콘텐츠 없음**을 선택합니다. 프로젝트를 저장할 위치를 선택하고 **프로젝트 만들기**를 클릭합니다. 그러면 Visual Studio 프로젝트 및 Unreal 편집기에서 C++ 파일이 열립니다. 

![초기 프로젝트 설정](images/unreal-uxt/2-project-settings.PNG)

4. 왼쪽 위 모서리에서 **편집 > 플러그 인**으로 이동합니다. [증강 현실]에서 확인란을 선택하여 **HoloLens** 플러그 인을 사용하도록 설정합니다. [가상 현실] 섹션까지 아래로 스크롤하고 확인란을 선택하여 **Microsoft Windows Mixed Reality** 플러그 인을 사용하도록 설정합니다. 두 플러그 인은 HoloLens 2 개발에 필요합니다. 편집기를 다시 시작합니다. 

![플러그 인](images/unreal-uxt/2-plugins.PNG)

5. 왼쪽 위 모서리에서 **파일 > 새 레벨**로 이동합니다. **빈 레벨**을 선택합니다. 이제 뷰포트의 기본 장면이 비어 있습니다.

6. [기본] 탭의 왼쪽에 있는 [모드] 패널에서 PlayerStart를 끌어다 놓습니다. 앱이 시작될 때 사용자가 원점에서 시작하도록, 오른쪽의 [세부 정보] 패널에서 위치를 X = 0, Y = 0, Z = 0으로 설정합니다.

![PlayerStart를 사용하는 뷰포트](images/unreal-uxt/2-playerstart.PNG)

7. [모드] 패널의 [기본] 탭에서 **큐브**를 뷰포트로 끌어다 놓습니다. 시작할 때 큐브가 플레이어와 50cm 떨어지도록, [세부 정보] 패널에서 위치를 X = 50, Y = 0, Z = 0으로 설정합니다. 기본 큐브가 매우 크기 때문에 큐브 배율을 (0.2, 0.2, 0.2)로 변경합니다. 

8. 장면에 조명을 추가하기 전에는 큐브를 볼 수 없습니다. [모드] 패널에서 **조명** 탭으로 전환하고, **방향성 광원**을 PlayerStart 위의 장면으로 끌어다 놓습니다.

![조명이 추가된 뷰포트](images/unreal-uxt/2-light.PNG)

9.  도구 모음에서 **재생** 단추를 누르면 뷰포트에 큐브가 표시됩니다. **Esc** 키를 눌러 레벨을 중지합니다. 

![뷰포트의 큐브](images/unreal-uxt/2-cube.PNG)

10. 레벨을 저장하겠습니다. 왼쪽 위 모서리에서 **파일 > 현재 레벨 저장**을 클릭합니다. 레벨 이름을 "기본"으로 지정하고 **저장**을 클릭합니다. 

## <a name="set-up-a-chess-scene"></a>체스 장면 설정

1. 콘텐츠 브라우저에서 [새 항목 추가] 아래에 있는 아이콘을 클릭하여 소스 패널을 표시합니다. 그런 다음, **새 항목 추가 > 새 폴더**를 클릭하고 폴더 이름을 "ChessAssets"로 지정합니다. 이 폴더를 두 번 클릭하여 내부로 이동합니다. 여기서는 체스 세트의 3D 자산을 가져오겠습니다.

![소스 패널 표시 또는 숨기기](images/unreal-uxt/2-showhidesources.PNG)

2. [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z)에서 자산의 zip 파일을 다운로드합니다. 이 파일에는 체스 보드와 체스 세트의 3D 모델이 포함되어 있습니다. 이 파일의 압축을 풉니다.

3. 콘텐츠 브라우저의 맨 위에서 **가져오기**를 클릭합니다. 방금 압축을 푼 폴더로 이동하여 폴더 안에 있는 모든 항목을 선택합니다. 이 폴더에는 체스 보드와 체스 말의 3D 개체 메시인 FBX 파일, 그리고 체스 보드와 체스 말의 재질을 만드는 데 사용할 재질 맵인 TGA 파일이 포함되어 있습니다. **열기**를 클릭합니다. 

4. FBX 가져오기 옵션 창이 나타납니다. **재질** 섹션에서 **재질 가져오기 방법**을 **재질을 만들지 않음**으로 변경합니다. 그런 다음, **모두 가져오기**를 클릭합니다.

![FBX 옵션 가져오기](images/unreal-uxt/2-nocreatemat.PNG)

5. 콘텐츠 폴더로 돌아가서 **Blueprints**라는 새 폴더를 만듭니다. 새로운 유형의 행위자 및 스크립트 수준 이벤트를 만들 수 있는 노드 기반 인터페이스를 제공하는 특수 자산인 청사진을 전부 이 폴더에 저장할 것입니다. 

6. **Blueprints** 폴더를 두 번 클릭하여 내부로 이동한 다음, 콘텐츠 브라우저를 마우스 오른쪽 단추로 클릭하고, **청사진 클래스**를 선택합니다. **행위자**를 클릭하고 새 청사진의 이름을 "Board"로 지정합니다. Board를 두 번 클릭하여 엽니다. 

![청사진의 부모 클래스를 선택합니다.](images/unreal-uxt/2-bpparent.PNG)

![새 보드 청사진](images/unreal-uxt/2-bpboard.PNG)

7. 청사진 편집기에서 [구성 요소] 패널로 이동하여 **구성 요소 추가 > 장면**을 클릭합니다. 새로 만든 장면의 이름을 "Root"로 지정한 다음, DefaultSceneRoot 위로 Root를 끌어다 놓습니다. 그러면 기본 장면 루트가 바뀌고 뷰포트의 구가 제거됩니다. 

![루트 바꾸기](images/unreal-uxt/2-root.PNG)

8. **구성 요소 추가**를 다시 클릭하고, 이번에는 **정적 메시**를 선택합니다. 새 정적 메시의 이름을 "SM_Board"로 지정합니다. 

![정적 메시 추가](images/unreal-uxt/2-sm-board.PNG)

9. **세부 정보** 패널에서 **정적 메시** 섹션을 찾아 드롭다운을 클릭합니다. **ChessBoard**를 선택합니다. 

![뷰포트의 보드 메시](images/unreal-uxt/2-sm-board-view.PNG)

10. 계속해서 **세부 정보** 패널에서 **재질** 섹션을 찾아 드롭다운을 클릭합니다, **새 자산 만들기**에서 **재질**을 선택합니다. 이 자산의 이름을 **M_ChessBoard**로 지정하고 **ChessAssets** 폴더에 저장합니다. 

![새 장면 만들기](images/unreal-uxt/2-newmat.PNG)

11. M_ChessBoard 드롭다운의 옆에 있는 사각형을 두 번 클릭하여 새로 만든 M_ChessBoard 재질을 엽니다. 재질 편집기를 마우스 오른쪽 단추로 클릭하고 **텍스처 샘플** 노드를 검색합니다. **세부 정보** 패널의 **재질 식 텍스처 기본** 섹션에서 드롭다운을 클릭하고 **ChessBoard_Albedo**를 선택합니다. 마지막으로 **RGB** 출력 핀을 **M_ChessBoard**의 기본 색 핀으로 끌어다 놓습니다. 

![기본 색 설정](images/unreal-uxt/2-boardalbedomat.PNG)

12. 같은 과정을 네 번 더 반복하여 **ChessBoard_AO** 텍스처 샘플을 **주변 폐색** 핀에 연결하고, **ChessBoard_Metal** 텍스처 샘플을 **금속** 핀에 연결하고, **ChessBoard_Normal** 텍스처 샘플을 **일반** 핀에 연결하고, **ChessBoard_Rough** 텍스처 샘플을 **거칠기** 핀에 연결합니다. **Save**을 클릭합니다. 

![나머지 텍스처 연결](images/unreal-uxt/2-boardmat.PNG)

13. **Board** 청사진으로 돌아갑니다. 방금 만든 재질이 청사진에 적용된 것을 볼 수 있습니다. 보드를 화면에 배치할 때 보드의 크기와 위치가 적절하도록 보드의 **배율**을 (0.05, 0.05, 0.05)로 변경하고 **회전**을 Z = 90으로 변경합니다. 위쪽의 도구 모음에서 **컴파일**을 클릭한 다음, **저장**을 클릭합니다. 주 창으로 돌아갑니다. 

![재질이 적용된 체스 보드](images/unreal-uxt/2-chessboard.PNG)

14. 이제 큐브를 삭제하고 새로 만든 Board 행위자로 바꾸겠습니다. **월드 아웃라이너**에서 마우스 오른쪽 단추로 **큐브 > 편집 > 삭제**를 클릭합니다. 콘텐츠 브라우저에서 Board를 뷰포트로 끌어다 놓습니다. 보드의 위치를 X = 80, Y = 0, Z =-20으로 설정합니다. 

15. **재생** 단추를 클릭하여 새 보드를 레벨에서 확인합니다. **Esc** 키를 눌러 편집기로 돌아갑니다. 

16. 보드와 똑같은 단계를 따라 체스 말을 만들겠습니다. 이번에는 다음과 같이 체스 말의 메시와 재질을 선택합니다.

    a) 콘텐츠 브라우저에서 Blueprints 폴더로 이동하여 행위자 형식의 새 청사진 클래스를 만듭니다. 이 행위자의 이름을 "WhiteKing"으로 지정합니다.

    b) WhiteKing을 두 번 클릭하여 엽니다. "Root"라는 새 장면 구성 요소를 추가하여 DefaultSceneRoot 대신 사용합니다. 

    c) "SM_King"이라는 새 정적 메시 구성 요소를 추가합니다. [세부 정보] 패널에서 **정적 메시**를 **Chess_King**으로 설정하고, **재질**을 **M_ChessWhite**라는 새 재질로 설정합니다. 

    d) 새 **M_ChessWhite** 재질을 열고 관련 텍스처를 해당하는 재질 입력에 연결합니다. 

    ![체스 킹 재질 만들기](images/unreal-uxt/2-chesskingmat.PNG)

    e) **WhiteKing** 청사진으로 돌아가서 **배율**을 (0.05, 0.05, 0.05)로 변경하고 **회전**을 Z = 90으로 변경합니다.

    f) 청사진을 컴파일하고 저장한 다음, 주 창으로 돌아갑니다. 

17. WhiteKing을 뷰포트로 끌어다 놓습니다. WhiteKing이 Board의 자식이 되도록, **월드 아웃라이너**에서 WhiteKing을 Board로 끌어다 놓습니다. 

![월드 아웃라이너](images/unreal-uxt/2-child.PNG)

18. **세부 정보** 패널의 **변환**에서 WhiteKing의 **위치**를 X =-26, Y = 4, Z = 0으로 설정합니다.

19. **재생**을 클릭하여 레벨을 확인합니다. **Esc** 키를 눌러 종료합니다. 

[다음 섹션: 3. 혼합 현실용 프로젝트 설정](unreal-uxt-ch3.md)