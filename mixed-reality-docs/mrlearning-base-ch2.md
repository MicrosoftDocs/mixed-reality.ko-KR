---
title: MR 학습 기본 모듈 - 사용자 인터페이스, 손 추적 및 Mixed Reality Toolkit 구성
description: 이 과정을 완료하면 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 이해할 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: 1800d36b7292b9cb53b09fdd4b9c4fb763d49e79
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2019
ms.locfileid: "65730948"
---
# <a name="mr-learning-base-module---user-interface-hand-tracking-and-mixed-reality-toolkit-configuration"></a>MR 학습 기본 모듈 - 사용자 인터페이스, 손 추적 및 Mixed Reality Toolkit 구성

이전 단원에서는 HoloLens 2의 첫 번째 애플리케이션을 시작으로 MRTK에 제공되는 몇 가지 기능을 알아보았습니다. 다음 단원인 이 문서에서는 UI 텍스트 패널에서 단추를 만들고 구성하는 방법과 기본 상호 작용(터치)을 사용하여 각 단추와 상호 작용하는 방법을 알아봅니다. 개체의 크기, 사운드 및 색상 변경과 같은 간단한 작업과 효과도 추가로 살펴봅니다. 이 모듈에서는 공간 메시의 시각화를 해제하는 것으로 시작하여 MRTK 프로필을 수정하는 방법에 대한 기본 개념을 소개합니다. 

## <a name="objectives"></a>목표

* Mixed Reality Toolkit 프로필 사용자 지정 및 구성
* UI 요소 및 단추를 사용하여 홀로그램과 상호 작용
* 기본적인 손 추적 입력 및 상호 작용

## <a name="instructions"></a>지침

### <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>Mixed-Reality Toolkit 프로필을 구성하는 방법(공간 인식 변경 표시 옵션)
이 섹션에서는 공간 인식 메시의 표시 옵션을 조정하여 기본 Mixed Reality Toolkit 프로필을 사용자 지정하고 구성하는 방법을 알아봅니다. MRTK 프로필의 설정이나 값을 조정할 때도 이와 동일한 원칙을 따를 수 있습니다.

1. “BaseScene” 계층 구조에서 MRTK(Mixed-Reality Toolkit)를 선택합니다. 아래 그림과 같이 inspector(검사기) 패널에서 “Mixed Reality Toolkit Script”를 찾아서 “active profile”(활성 프로필)을 선택합니다. 두 번 클릭하여 엽니다.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step1im.PNG)

>참고: 기본적으로 MRTK 프로필은 편집할 수 없습니다. 복사하여 사용자 지정할 수 있는 기본 프로필 템플릿입니다. 사용자 지정과 프로필에는 여러 계층이기 때문에 하나 이상의 설정을 구성할 때는 여러 프로필을 복사하고 사용자 지정하는 것이 일반적입니다.
>
>MRTK 프로필과 아키텍처에 대해 자세히 알아보려면 [MRTK 설명서](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/SpatialAwareness/SpatialAwarenessSystemArchitecture.html>)를 참조하세요.

2. 기본 프로필의 복사본을 만들어서 사용자 지정합니다. 기본 프로필을 복사하려면“Copy & Customize”(복사 및 사용자 지정) 단추를 클릭합니다(이미지 참조). 그러면 MRTK 프로필의 복사본이 만들어집니다. MRTK 프로필의 복사본이 준비되었으면, 이제 프로필에서 원하는 설정을 사용자 지정할 수 있습니다. 또한 이 프로필 하위에 중첩된 추가 프로필에 대해 복사/사용자 지정 단계를 반복해야 하며, 이 내용은 이후 단계에 설명되어 있습니다.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step2im.PNG)

3. 공간 인식 메시의 표시 유형을 사용하지 않도록 설정합니다. 이렇게 하려면 이미지와 같이 “Spatial Awareness System Settings”(공간 인식 시스템 설정)를 찾습니다. “Spatial Awareness System Profile”(공간 인식 시스템 프로필)의 오른쪽에 있는 "clone"(복제) 단추를 클릭하고 기본 프로필을 사용자 지정 가능한 복사본으로 대체합니다. 팝업 창이 표시되면 아래 두 번째 이미지와 같이, "Clone"(복제) 단추를 누릅니다.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3im.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3bim.jpg)

4. Default Mixed Reality Spatial Mesh Observer의 사용자 지정 복사본을 만듭니다. “Windows Mixed Reality Spatial Mesh Observer” 옆에 있는 아래쪽 화살표를 클릭하면 추가 옵션을 볼 수 있습니다. 이 옵션에는 "Default Mixed Reality Spatial Mesh Observer"가 회색(편집 불가능)으로 표시됩니다. 이 기본 프로필을 편집할 수 있도록 사용자 지정 가능한 복사본으로 대체해야 합니다. 오른쪽에 있는 단추(녹색 화살표로 표시)를 클릭하여 복사본을 복제합니다.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step4im.PNG)

5. 다음으로 표시 옵션의 설정을 “occlusion”(폐색)으로 조정합니다. 이렇게 하면 공간 메시가 보이지 않지만 공간 메시 뒤에 게임 개체를 숨길 수 있습니다. 이것을 폐색이라고 합니다.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step5im.PNG)

>참고: 공간 매핑 메시가 보이지 않더라도 여전히 존재하며 상호 작용이 가능합니다. 공간 매핑 메시 뒤에 있는 홀로그램(예: 보이는 벽 뒤에 있는 홀로그램)은 폐색 설정 때문에 보이지 않습니다.

축하합니다. MRTK 프로필에서 설정을 수정하는 방법을 알아보았습니다. 여기서 알 수 있듯이, MRTK 설정을 조정하려면 기본 프로필의 복사본을 만들어야 편집할 수 있습니다. 새 설정으로 프로필을 만들거나 기본 프로필을 다시 참조하려는 경우 다시 돌아갈 수 있는 기본 프로필(편집 불가능)은 항상 유지됩니다. 조정할 수 있는 설정은 다양합니다. MRTK 프로필 설정에 대한 전체 참조는 https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html에서 MRTK 설명서를 참조하세요.

### <a name="hand-tracking-gestures-and-interactable-buttons"></a>손 추적 제스처 및 상호 작용 가능 단추
이 섹션에서는 손 추적을 사용하여 상호 작용 가능 단추를 누르는 방법을 알아봅니다.

1. 프로젝트 폴더에서 “Assets”(자산)을 선택합니다.

2. 검색 창에 “pressablebutton”을 입력합니다.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step1im.PNG)

3. "PressableButton"이라는 프리팹(파란색 상자로 표시)을 계층 구조로 끌어다 놓습니다. 

   > 참고: “TMP Essentials 가져오기”에 대한 메시지가 표시되면 가져옵니다. TMP Essentials가 아직 프로젝트에 속하지 않은 경우, TMP Essentials를 가져온 후 이 단계를 반복해야 합니다. 그렇지 않으면 단추 텍스트가 표시되지 않을 수 있습니다.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step3im.PNG)

4. 아래 이미지와 같이 “PressableButton” 게임 개체(BaseScene 계층 구조에 있음)를 두 번 클릭하면 장면에서 볼 수 있습니다. (단추 그래픽은 아래 이미지와 다를 수 있습니다.) 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step4im.PNG)

5. inspector(검사기) 패널에서 “Add Event”(이벤트 추가)를 클릭하여 누르면 응답하는 이벤트를 단추에 부여합니다. 옵션이 표시되면 드롭다운 메뉴를 선택합니다. “InteractableOnPressReciever”를 선택합니다. 이렇게 하면 추적되는 손이 단추를 누르면 누른 이벤트에 대해 단추가 응답할 수 있습니다.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step5im.PNG)

6. 장면에 큐브를 추가합니다. 계층 구조 영역을 마우스 오른쪽 단추로 클릭하고 3D 개체를 선택한 후 “cube”(큐브)를 클릭합니다. 이제 디스플레이에 큐브가 표시됩니다. 매우 크게 보이기 때문에 좌표를 조정하여(계층 구조 영역에서 "큐브"가 선택된 상태로) 크기를 줄입니다. 배율 값을 x = 0.1, y = 0.1 및 z = 0.1로 설정합니다. 큐브를 장면에 배치하고 누를 수 있는 단추 근처에 놓지만 단추와 겹치지는 않아야 합니다. 아래 이미지에서 큐브의 위치는 x = 0, y = 0.2, z = 1입니다. 

   > 참고: 일반적으로 Unity의 1단위는 실제 세계의 1미터와 같습니다. 여기에는 예외가 있습니다. 예를 들어, 개체가 크기 조정된 객체의 자식인 경우입니다.
   
   ![MR213_BuildSettings](images/mrlearning-base-ch2-1step6ima.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-2step6imb.PNG)

7. 이 단계에서는 단추를 누르면 색이 변하는 큐브를 설정합니다. “BaseScene” 메뉴에서 PressableButton을 선택합니다. inspector(검사기) 패널의 “Select Event Type”(이벤트 유형 선택) 상자 아래에 있는 “+” 단추를 클릭합니다. 아래 그림과 같이 "BaseScene" 메뉴의 "cube"(큐브)를 "Runtime Only"(런타임 전용) 상자로 끌어서 놓습니다.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7ima.PNG)

“No Function”(함수 없음) 드롭다운 목록을 클릭합니다. “MeshRenderer”를 선택한 후 “Material material”을 선택합니다. 이제 단추가 눌리면 재질을 변경할 수 있습니다. 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imb.PNG)

프로젝트 패널로 이동하여 변경할 재질을 검색합니다. 이 예제의 경우 “MRTK_Standard_Cyan” 재질을 사용하며, 프로젝트 탭의 검색 창에 "cyan"을 입력하여 찾을 수 있습니다. (MRTK에는 선택할 수 있는 재질과 색상이 많이 포함되어 있습니다.) 재질을 “MeshRenderer.material” 아래 상자로 끌어옵니다. MRTK 재질은 Assets>MixedRealityToolkit.SDK>StandardAssets>Materials에서 찾을 수 있습니다.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imbb.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step7imc.PNG)

이제 단추를 누르면 지정한 재질에 따라 큐브 색이 변하도록 이벤트가 설정되었습니다. 이 예제에서는 큐브가 녹청색으로 변합니다.

8. 다음으로, 단추에서 손을 떼면 단추가 기본 색으로 돌아가도록 릴리스 동작을 설정합니다. 7단계(이전 단계)를 반복하지만 이번에는 아래 이미지와 같이 “OnPress” 이벤트 대신 “OnRelease” 이벤트를 선택합니다.

9.  단추에서 손을 떼면 기본값으로 설정될 큐브의 재질을 프로젝트 패널에서 검색합니다. (여기에서는 MRTK_Standard_LightGray가 선택됩니다.) “MeshRenderer.material” 필드 아래 상자로 재질을 끌어옵니다.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step8im.PNG)

이제 단추를 누르면 새로운 색(예: 녹청)으로 변하고 단추에서 손을 떼면 지정한 기본 색(예: 연한 회색)으로 돌아가야 합니다. 화면 상단의 “play”(재생) 단추를 눌러서 편집기에서 테스트해보거나 HoloLens 2에 배포하여 테스트해봅니다! 손 시뮬레이션을 포함하여 편집기 내 시뮬레이션에 대해 자세히 알아보려면 [MRTK의 시뮬레이션 설명서 페이지](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>)를 참조하세요. 

### <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>MRTK의 Grid Object Collection을 사용하여 버튼 패널 만들기

이 섹션에서는 MRTK의 GridObjectCollection 도구를 사용하여 여러 단추를 깔끔한 사용자 인터페이스로 자동 정렬하는 방법을 알아봅니다.

1. 단추가 5개가 될 때까지 이전 섹션의 단추를 복제합니다. 이 작업을 수행하는 방법은 여러 가지입니다.
- 단추를 마우스 오른쪽 단추로 클릭하고 “copy”(복사)를 클릭한 후 단추 아래로 이동하여 마우스 오른쪽 단추를 다시 클릭하고 “paste”(붙여넣기)를 클릭합니다. 
- 단추를 마우스 오른쪽 단추로 클릭하고 “duplicate”(복제)를 클릭합니다. 
- 큐브를 클릭하고 키보드의 "Ctrl D"키를 눌러서 키보드 명령을 사용합니다.

단추가 총 5개가 될 때까지 이 단계를 반복합니다. (아래 이미지의 빨간색 화살표 5개를 참조하세요.)

![Mrlearning Base Ch2 3Step1im](images/mrlearning-base-ch2-3step1im.PNG)

2. 빈 부모 게임 개체 아래 단추를 그룹화합니다. 그리드 컬렉션에 단추를 포함하려면 단추를 공통 부모 개체 아래에 그룹화해야 합니다. 계층 구조에서 마우스 오른쪽 단추를 클릭하고 "create empty"(빈 항목 만들기)를 클릭합니다. 모든 단추를 넣을 수 있는 빈 게임 개체가 새로 만들어집니다. “gameObject”라고 표시됩니다. 마우스 오른쪽 단추로 클릭하고 이름을 “ButtonCollection”으로 바꿉니다.

![Mrlearning Base Ch2 3Step2im](images/mrlearning-base-ch2-3step2im.PNG)

3. 모든 단추를 새 컬렉션으로 옮깁니다. 아래 이미지와 같이 계층 구조에 있는 단추 개체 5개를 모두 선택하고 “ButtonCollection” 게임 개체 아래로 끌어오면 됩니다. 팁: Ctrl 키를 누른 상태로 항목을 선택하면 여러 항목을 선택할 수 있습니다.

![Mrlearning Base Ch2 3Step3imb](images/mrlearning-base-ch2-3step3imb.PNG)

4. MRTK의 “Grid Object Collection” 구성 요소를 단추 컬렉션에 추가합니다.  이렇게 하려면 “ButtonCollection” 부모 개체를 선택하고 inspector(검사기) 패널에서 “Add Component”(구성 요소 추가) 단추를 클릭합니다. 그런 다음, 검색 창에서 “Grid Object Collection”을 검색하여 목록에 표시되면 선택합니다.

![Mrlearning Base Ch2 3Step4im](images/mrlearning-base-ch2-3step4im.PNG)

Grid Object Collection 구성 요소를 사용하면 단추나 원하는 개체 세트를 행, 열 또는 그리드로 깔끔하게 구성할 수 있습니다. 이 기능은 MRTK에 제공되는 기본 구성 요소 중 하나이며, 멋진 사용자 인터페이스를 만들 수 있는 신속하고 간편한 수단을 제공합니다.

5. 그리드 개체 컬렉션 구성 모든 단추가 사용자를 향하도록 하려면 “orient type”을 선택한 후 “face parent forward”을 선택합니다(이미지 참조). 그런 다음, 셀 크기를 변경하여 단추 사이의 간격을 설정합니다. Cell Width(셀 너비)와 Cell Height(셀 높이)는 아래 이미지와 같이 0.12 단위 x 0.12 단위부터 시작합니다. 선택한 개체/단추 자산에 따라 이 값을 조정해야 할 수도 있습니다. "Rows"(행)은 1로 설정해야 합니다. 그런 다음, “Update Collection”(컬렉션 업데이트)을 클릭하면 아래 그림과 같이 장면이 표시됩니다. 


![Mrlearning Base Ch2 3Step5im](images/mrlearning-base-ch2-3step5im.PNG)

>참고: 자식 개체나 부모 개체의 방향에 따라, 향후 프로젝트에서는 방향 설정을 다르게 조정해야 할 수도 있습니다. 컬렉션에 있는 개체의 크기에 따라 Cell Width(셀 너비)와 Cell Height(셀 높이) 필드도 다르게 정의해야 할 수 있습니다.

### <a name="adding-text-into-your-scene"></a>장면에 텍스트 추가

이 섹션에서는 혼합 현실 환경에 텍스트를 추가하고 편집하는 방법을 알아봅니다. Unity에 TextMeshPro가 활성화되어 있지 않은 경우 [여기](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation)의 지침에 따라 사용하도록 설정합니다.

1. “ButtonCollection” 부모 개체를 선택하고 컬렉션을 마우스 오른쪽 단추로 클릭합니다. 드롭다운 메뉴에서 "3D object"(3D 개체)를 펼친 후 "TextMeshPro-Text"를 선택합니다. 아래 이미지와 같이, 단추 컬렉션 아래 TextMeshPro 개체가 보입니다.

![Lesson2 Chapter4 Step1a](images/Lesson2_Chapter4_Step1a.JPG)
![Lesson2 Chapter4 Step1b](images/Lesson2_Chapter4_Step1b.JPG)

2. TextMeshPro 구성 요소의 텍스트 필드(inspector 패널에 있음, 아래 그림 참조)에 “Button Collection Text”를 입력합니다. 텍스트가 장면이 나타나지만 단추 뒤에 숨겨져 있거나 잘못된 크기로 표시됩니다.

![Lesson2 Chapter4 Step2](images/Lesson2_Chapter4_Step2.JPG)

3. 가독성을 위해 텍스트 크기와 배치를 개선하려면, TextMeshPro 구성 요소에서 “font size”(글꼴 크기) 필드를 조정하여 글꼴의 크기를 변경합니다. 아래 이미지와 같이 “Rect Transform” 위치와 크기도 조정해야 합니다. 텍스트 구성에 사용된 값은 아래 이미지를 참조하세요. 이 값을 시작 지점으로 사용하여 텍스트 필드의 크기와 배치를 개선할 수 있습니다.

![Lesson2 Chapter4 Step3](images/Lesson2_Chapter4_Step3.JPG)
![Lesson2 Chapter4 Step4](images/Lesson2_Chapter4_Step4.JPG)

5. 단추 개체의 텍스트 값을 수정하려면 단추 옆에 있는 화살표를 클릭하고 펼쳐서 “SeeItSayItLabel” 개체로 이동한 후 “TextMeshPro”로 이동하여, 위 단계의 설명대로 단추 텍스트를 편집할 수 있습니다.

![Lesson2 Chapter4 Step5](images/Lesson2_Chapter4_Step5.JPG)

### <a name="congratulations"></a>축하합니다.
이 단원에서는 MRTK 프로필 설정(예: 공간 인식 메시 표시 유형)을 복사, 사용자 지정 및 구성하는 방법을 알아보았습니다. HoloLens 2에서 추적되는 손을 사용하여 단추와 상호 작용하고 이벤트 트리거하는 방법도 알아보았습니다. 마지막으로 Grid Object Collection 구성 요소인 Unity의 Text Mesh Pro를 사용하여 간단한 UI 인터페이스를 만드는 방법을 알아보았습니다.

[다음 단원: 동적 콘텐츠 배치 및 해결기](mrlearning-base-ch3.md)

