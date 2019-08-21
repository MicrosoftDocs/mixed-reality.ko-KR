---
title: 자습서를 시작 합니다. 3. 사용자 인터페이스 만들기 및 Mixed Reality Toolkit 구성
description: 이 과정을 완료하면 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 이해할 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: 45833ba22305acedb45bfdc9752c0b278a693190
ms.sourcegitcommit: 9636573eabdc78db6875e831a9c894a2ff173a99
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/20/2019
ms.locfileid: "69629176"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a>3. 사용자 인터페이스 만들기 및 Mixed Reality Toolkit 구성 

이전 단원에서는 HoloLens 2에 대 한 첫 번째 응용 프로그램을 시작 하 여 MRTK (Mixed Reality Toolkit)에서 제공 해야 하는 기능 중 일부에 대해 알아보았습니다. 다음 단원에서는 UI 텍스트 패널과 함께 단추를 만들고 구성 하는 방법과 기본 상호 작용 (touch)을 사용 하 여 각 단추와 상호 작용 하는 방법을 배웁니다. 개체의 크기, 사운드 및 색상 변경과 같은 간단한 작업과 효과도 추가로 살펴봅니다. 이 모듈에서는 공간 메시 시각화를 해제 하는 것부터 MRTK 프로필 수정에 대 한 기본 개념을 소개 합니다. 

## <a name="objectives"></a>목표

* Mixed Reality Toolkit 프로필 사용자 지정 및 구성
* UI 요소 및 단추를 사용 하 여 holograms와 상호 작용
* 기본적인 손 추적 입력 및 상호 작용

## <a name="instructions"></a>지침

### <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>Mixed-Reality Toolkit 프로필을 구성하는 방법(공간 인식 변경 표시 옵션)
이 섹션에서는 공간 인식 메시의 표시 옵션을 조정 하 여 기본 MRTK 프로필을 사용자 지정 하 고 구성 하는 방법을 알아봅니다. MRTK 프로필의 설정이나 값을 조정할 때도 이와 동일한 원칙을 따를 수 있습니다.

1. BaseScene 계층 구조에서 MRTK (Mixed Reality Toolkit)를 선택 합니다. 검사기 패널에서 Mixed Reality Toolkit 스크립트를 찾고 아래 그림에 표시 된 것 처럼 활성 프로필을 선택 합니다. 두 번 클릭하여 엽니다.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step1im.PNG)

>참고: 기본적으로 MRTK 프로필은 편집할 수 없습니다. 이러한 프로필은 복사 및 사용자 지정할 수 있는 기본 프로필 템플릿입니다. 사용자 지정 및 프로필 계층에는 여러 가지가 있습니다. 따라서 하나 이상의 설정을 구성할 때 여러 프로필을 복사 하 고 사용자 지정 하는 것이 표준 습관입니다.
>
>MRTK 프로필 및 해당 아키텍처에 대해 자세히 알아보려면 [mrtk 설명서](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html>)를 참조 하세요.

2. 기본 프로필의 복사본을 만들어서 사용자 지정합니다. 기본 프로필을 복사 하려면 복사 & 사용자 지정을 클릭 합니다 (이미지 참조). 그러면 MRTK 프로필의 복사본이 만들어집니다. MRTK 프로필의 복사본이 준비되었으면, 이제 프로필에서 원하는 설정을 사용자 지정할 수 있습니다. 이후 단계에서 설명한 대로이 프로필 아래에 중첩 된 추가 프로필에 대 한 복사 및 사용자 지정 단계를 반복 해야 합니다.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step2im.PNG)

3. 공간 인식 메시의 표시 유형을 사용하지 않도록 설정합니다. 이렇게 하려면 이미지에 표시 된 것 처럼 공간 인식 시스템 설정을 찾습니다. 공간 인식 시스템 프로필의 오른쪽에 있는 복제 단추를 클릭 하 여 기본 프로필을 사용자 지정 가능한 복사본으로 바꿉니다. 팝업 창이 표시 되 면 아래 두 번째 이미지에 표시 된 것 처럼 복제 단추를 누릅니다.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3im.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3bim.jpg)

4. Default Mixed Reality Spatial Mesh Observer의 사용자 지정 복사본을 만듭니다. Windows Mixed Reality 공간 메시 관찰자 옆에 있는 아래쪽 화살표를 클릭 하 여 추가 옵션을 표시 합니다. 이러한 옵션에는 회색으로 표시 된 기본 혼합 현실 공간 메시 관찰자 (편집할 수 없음)가 표시 됩니다. 이 기본 프로필을 편집할 수 있도록 사용자 지정 가능한 복사본으로 대체해야 합니다. 오른쪽 (녹색 화살표로 표시) 단추를 클릭 하 여 복사본을 복제 합니다.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step4im.PNG)

5. 다음으로 표시 옵션의 설정을 “occlusion”(폐색)으로 조정합니다. 이렇게 하면 공간 메쉬가 표시 되지 않지만 공간 메시 뒤의 게임 개체 (폐색 라고도 함)는 숨겨집니다.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step5im.PNG)

>참고: 공간 매핑 메시가 보이지 않더라도 여전히 존재하며 상호 작용이 가능합니다. 표시 되는 벽 뒤의 홀로그램 처럼 공간 매핑 메시 뒤의 holograms는 폐색 설정 때문에 표시 되지 않습니다.

축하합니다. MRTK 프로필에서 설정을 수정하는 방법을 알아보았습니다. 여기서 알 수 있듯이, MRTK 설정을 조정하려면 기본 프로필의 복사본을 만들어야 편집할 수 있습니다. 새 설정을 사용 하 여 프로필을 만들거나 기본 프로필을 다시 참조할 수 있는 경우에만 다시 편집할 수 없는 기본 프로필이 항상 포함 됩니다. 조정할 수 있는 설정은 다양합니다. MRTK 프로필 설정에 대한 전체 참조는 https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html 에서 MRTK 설명서를 참조하세요.

### <a name="hand-tracking-gestures-and-interactable-buttons"></a>손 추적 제스처 및 상호 작용 가능 단추
이 섹션에서는 수동 추적을 사용 하 여 pressable 단추를 누르는 방법을 배웁니다.

1. 프로젝트 폴더에서 자산을 선택 합니다.

2. 검색 창에 “pressablebutton”을 입력합니다.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step1im.PNG)

3. "PressableButton"이라는 프리팹(파란색 상자로 표시)을 계층 구조로 끌어다 놓습니다. 

   > 참고: "TMP Essentials 가져오기"에 대 한 메시지가 표시 되 면 지금 가져옵니다. TMP Essentials가 아직 프로젝트에 포함 되지 않은 경우 TMP Essentials를 가져온 후이 단계를 반복 해야 할 수 있습니다. 그렇지 않으면 단추 텍스트가 표시 되지 않을 수 있습니다.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step3im.PNG)

4. 아래 이미지에 표시 된 것 처럼, 이제 BaseScene 계층 구조에 있는 보도 게임 개체를 두 번 클릭 하 여 장면에서 볼 수 있습니다. 단추 그래픽이 아래 이미지와 다르게 나타날 수 있습니다. 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step4im.PNG)

5. Inspector 패널에서 이벤트 추가를 클릭 하 여 단추를 푸시할 때 응답할 이벤트를 제공 합니다. 표시 되는 옵션에서 드롭다운 메뉴를 선택 하 고 InteractableOnPressReciever를 선택 합니다. 이렇게 하면 추적되는 손이 단추를 누르면 누른 이벤트에 대해 단추가 응답할 수 있습니다.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step5im.PNG)

6. 장면에 큐브를 추가합니다. 계층 영역을 마우스 오른쪽 단추로 클릭 하 고 3D 개체를 선택한 다음 큐브를 클릭 합니다. 이제 디스플레이에 큐브가 표시됩니다. 매우 큰 것으로 표시 됩니다. 계층 영역에서 큐브를 선택 하는 동안 좌표를 조정 하 여 크기를 줄일 수 있습니다. 배율 값을 x = 0.1, y = 0.1 및 z = 0.1로 설정합니다. 큐브를 장면에 배치하고 누를 수 있는 단추 근처에 놓지만 단추와 겹치지는 않아야 합니다. 아래 이미지에서 큐브의 위치는 x = 0, y = 0.2, z = 1입니다. 

   > 참고: 일반적으로 Unity의 1단위는 실제 세계의 1미터와 같습니다. 여기에는 예외가 있습니다. 예를 들어, 개체가 크기 조정된 객체의 자식인 경우입니다.
   
   ![MR213_BuildSettings](images/mrlearning-base-ch2-1step6ima.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-2step6imb.PNG)

7. 이 단계에서는 단추를 누르면 색이 변하는 큐브를 설정합니다. BaseScene 메뉴에서 보도 단추를 선택 합니다. 검사기 패널의 이벤트 유형 선택 상자에서 + 단추를 클릭 합니다. 아래 이미지에 표시 된 것 처럼 BaseScene 메뉴에서 런타임 전용 상자로 큐브를 끌어 옵니다.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7ima.PNG)

함수 없음 이라는 드롭다운 목록을 클릭 합니다. MeshRenderer을 선택 하 고 재질 재질을 선택 합니다. 이렇게 하면 단추를 누를 때 재질을 변경할 수 있습니다. 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imb.PNG)

프로젝트 패널로 이동 하 여 변경할 자료를 검색 합니다. 이 예에서는 프로젝트 탭의 검색 표시줄에 "녹청"을 입력 하 여 찾은 MRTK_Standard_Cyan 재질을 사용 합니다. (MRTK에는 선택할 수 있는 다양 한 재질 및 색이 포함 되어 있습니다.) 재질을 MeshRenderer 아래의 상자로 끕니다. MRTK 재질은 Assets>MixedRealityToolkit.SDK>StandardAssets>Materials에서 찾을 수 있습니다.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step7imc.PNG)

이제 단추를 누르면 지정한 재질에 따라 큐브 색이 변하도록 이벤트가 설정되었습니다. 이 예제에서는 큐브가 녹청색으로 변합니다.

8. 다음으로, 단추에서 손을 떼면 단추가 기본 색으로 돌아가도록 릴리스 동작을 설정합니다. 위의 7 단계를 반복 합니다. 그러나 이번에는 아래 이미지와 같이 Onrelease 이벤트 대신 OnRelease 이벤트를 사용 합니다.

9.  프로젝트 패널에서 해당 큐브에 대 한 자료를 검색 하 여 단추 릴리스가 될 때를 기본값으로 합니다. 이 경우 MRTK_Standard_LightGray를 선택 합니다. 재질을 MeshRenderer 필드 아래의 상자로 끌어 놓습니다.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step8im.PNG)

이제 단추를 누르면 새 색 사이안으로 변경 됩니다. 단추를 놓으면 지정 된 기본 색 (예: 밝은 회색)으로 다시 변경 됩니다. 화면 위쪽의 재생 단추를 눌러 편집기에서 사용해 보거나 HoloLens 2에 배포 하 여 테스트 합니다. 수동 시뮬레이션을 포함 하 여 편집기 내 시뮬레이션에 대 한 자세한 내용은 [Mrtk의 시뮬레이션 설명서 페이지](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>)를 참조 하세요. 

### <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>MRTK의 Grid Object Collection을 사용하여 버튼 패널 만들기

이 섹션에서는 MRTK의 GridObjectCollection 도구를 사용 하 여 자동으로 여러 단추를 깔끔한 사용자 인터페이스로 정렬 하는 방법을 설명 합니다.

1. 단추가 5 개 있을 때까지 이전 섹션에서 단추를 복제 합니다. 이 작업을 수행하는 방법은 여러 가지입니다.
- 단추를 마우스 오른쪽 단추로 클릭 하 고 복사를 클릭 합니다. 그런 다음 단추 아래로 이동 하 고 마우스 오른쪽 단추를 다시 클릭 한 다음 붙여넣기를 클릭 합니다. 
- 단추를 마우스 오른쪽 단추로 클릭 하 고 복제를 클릭 합니다. 
- 해당 큐브를 클릭 하 고 키보드에서 Ctrl D를 눌러 키보드 명령을 사용 합니다.

단추가 5 개 있을 때까지이를 반복 합니다. 아래 이미지에서 5 개의 빨간색 화살표를 확인 합니다.

![Mrlearning Base Ch2 3Step1im](images/mrlearning-base-ch2-3step1im.PNG)

2. 빈 부모 게임 개체 아래 단추를 그룹화합니다. Grid 컬렉션의 단추를 포함 하려면 단추를 공통 부모 개체 아래에 그룹화 해야 합니다. 마우스 오른쪽 단추를 클릭 하 고 빈 만들기를 클릭 합니다. 모든 단추를 넣을 수 있는 빈 게임 개체가 새로 만들어집니다. GameObject로 표시 됩니다. 마우스 오른쪽 단추를 클릭 하 고 이름을 ButtonCollection으로 바꿉니다.

![Mrlearning Base Ch2 3Step2im](images/mrlearning-base-ch2-3step2im.PNG)

3. 모든 단추를 새 컬렉션으로 옮깁니다. 이 작업을 수행 하려면 계층 구조에서 5 개의 단추 개체를 모두 선택 하 고 아래 이미지에 나와 있는 것 처럼 ButtonCollection game 개체 아래에 모두 끌어 놓습니다. 팁: 항목을 선택 하는 동안 Ctrl 키를 눌러 여러 항목을 선택 합니다.

![Mrlearning Base Ch2 3Step3imb](images/mrlearning-base-ch2-3step3imb.PNG)

4. 단추 컬렉션에 MRTK의 Grid 개체 컬렉션 구성 요소를 추가 합니다. 이렇게 하려면 ButtonCollection 부모 개체를 선택 합니다. 검사기 패널에서 구성 요소 추가 단추를 클릭 합니다. 검색 창에서 표 개체 컬렉션을 검색 하 고 목록에 표시 되 면 선택 합니다.

![Mrlearning Base Ch2 3Step4im](images/mrlearning-base-ch2-3step4im.PNG)

Grid 개체 컬렉션 구성 요소를 사용 하면 간단한 행, 열 또는 표에서 단추 또는 개체 집합을 구성할 수 있습니다. Enticing 사용자 인터페이스를 만드는 빠르고 쉬운 방법을 제공 하는 MRTK에서 제공 하는 빌딩 블록 중 하나입니다.

5. 그리드 개체 컬렉션 구성 모든 단추가 사용자에 게 오게 하려면 방향 유형을 선택 합니다. 그런 다음 아래 그림에 표시 된 것 처럼 정면 부모를 선택 합니다. 그런 다음, 셀 크기를 변경하여 단추 사이의 간격을 설정합니다. 아래 이미지에 표시 된 것 처럼 셀 너비와 셀 높이에 대해 0.12 단위 x 0.12 단위부터 시작 합니다. 선택한 개체 및 단추 자산에 따라 이러한 값을 조정 해야 할 수 있습니다. 행이 1로 설정 되어 있는지 확인 합니다. 컬렉션 업데이트를 클릭 합니다. 장면이 아래 그림과 같이 표시 됩니다. 


![Mrlearning Base Ch2 3Step5im](images/mrlearning-base-ch2-3step5im.PNG)

>참고: 자식 개체나 부모 개체의 방향에 따라, 향후 프로젝트에서는 방향 설정을 다르게 조정해야 할 수도 있습니다. 컬렉션에 있는 개체의 크기에 따라 Cell Width(셀 너비)와 Cell Height(셀 높이) 필드도 다르게 정의해야 할 수 있습니다.

### <a name="adding-text-into-your-scene"></a>장면에 텍스트 추가

이 섹션에서는 혼합 현실 환경에 텍스트를 추가하고 편집하는 방법을 알아봅니다. Unity에 TextMeshPro가 활성화되어 있지 않은 경우 [여기](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation)의 지침에 따라 사용하도록 설정합니다.

1. ButtonCollection 부모 개체를 선택 하 고 컬렉션을 마우스 오른쪽 단추로 클릭 합니다. 드롭다운 메뉴에서 3D 개체를 확장 합니다. 그런 다음 TextMeshPro를 선택 합니다. 아래 이미지에 표시 된 것 처럼 단추 컬렉션 아래에 TextMeshPro 개체가 표시 됩니다.

![Lesson2 Chapter4 Step1a](images/Lesson2_Chapter4_Step1a.JPG)
![Lesson2 Chapter4 Step1b](images/Lesson2_Chapter4_Step1b.JPG)

2. 텍스트 크기와 배치의 가독성을 높이기 위해 TextMeshPro 구성 요소의 글꼴 크기 필드를 조정 하 여 글꼴 크기를 변경 합니다. 아래 이미지에 표시 된 것 처럼 Rect 변환 위치 및 배율을 조정 해야 합니다. 텍스트 구성에 사용 되는 값은 아래 이미지를 참조 하세요. 이러한 값을 시작 점으로 사용 하 여 텍스트 필드의 크기와 배치를 더욱 향상 시킬 수 있습니다.

![2 단원 Chapter4 3 단계](images/Lesson2_Chapter4_Step3.JPG)

3. 아래와 같이 검사기 패널의 TextMeshPro 구성 요소 텍스트 필드에 있습니다. 단추 컬렉션 텍스트를 입력 합니다. 텍스트는 장면에 표시 되지만 단추 뒤 또는 잘못 된 크기로 숨겨집니다.

![2 단원 Chapter4 2 단계](images/Lesson2_Chapter4_Step2.JPG)
![2 단원 Chapter4 4 단계](images/Lesson2_Chapter4_Step4.JPG)

4. 단추 개체에서 텍스트 값을 수정 하려면 단추 옆의 화살표를 클릭 하 여 확장 하 고 SeeItSayItLabel 개체로 이동 합니다. 위의 단계에 설명 된 대로 단추에 텍스트를 편집할 수 있는 TextMeshPro로 이동 합니다.

![Lesson2 Chapter4 Step5](images/Lesson2_Chapter4_Step5.JPG)

## <a name="congratulations"></a>축하합니다.
이 단원에서는 MRTK 프로필 설정(예: 공간 인식 메시 표시 유형)을 복사, 사용자 지정 및 구성하는 방법을 알아보았습니다. HoloLens 2에서 추적되는 손을 사용하여 단추와 상호 작용하고 이벤트 트리거하는 방법도 알아보았습니다. 마지막으로 Grid Object Collection 구성 요소인 Unity의 Text Mesh Pro를 사용하여 간단한 UI 인터페이스를 만드는 방법을 알아보았습니다.

[다음 단원: 4. 동적 콘텐츠 배치 및 해결기 사용](mrlearning-base-ch3.md)

