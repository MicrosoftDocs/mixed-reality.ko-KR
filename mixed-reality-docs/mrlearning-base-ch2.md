---
title: MR 학습 자료 모듈-사용자 인터페이스를 직접 추적 하 고 혼합 현실 도구 키트 구성
description: 혼합된 현실 응용 프로그램에서 Azure Face recognition 얼굴 인식을 구현 하는 방법을 알아보려면이 과정을 완료 합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: unity, 자습서, hololens, 혼합된 현실
ms.openlocfilehash: 1530fd1a1ee06d01e8ab0cc009dfba03873c3427
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993638"
---
# <a name="mr-learning-base-module---user-interface-hand-tracking-and-mixed-reality-toolkit-configuration"></a>MR 학습 자료 모듈-사용자 인터페이스를 직접 추적 하 고 혼합 현실 도구 키트 구성

이전 단원을 MRTK HoloLens 2에 대 한 첫 번째 응용 프로그램을 시작 하 여 제공 하는 기능 중 일부를 배웠습니다. 다음 단원에서 만들고 단추 UI 텍스트 패널 함께 구성 및 기본 상호 작용 (touch)를 사용 하 여 각 단추와 상호 작용 하는 방법을 배웁니다. 간단한 작업 및 사운드 크기를 변경 하는 등의 효과 추가 하 고 개체의 색도 살펴봅니다. 이 모듈에서는 공간 메시의 시각화를 해제부터 MRTK 프로필을 수정 하는 방법에 대 한 기본 개념을 소개 합니다. 

## <a name="objectives"></a>목표

* 사용자 지정 및 혼합 현실 Toolkit 프로필 구성
* UI 요소 및 단추를 사용 하 여 홀로그램 상호 작용
* 기본 추적 직접 입력 및 상호 작용

## <a name="instructions"></a>지침

### <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>혼합 현실 Toolkit 프로필 (공간 인식 표시 옵션 변경)를 구성 하는 방법
사용자 지정 하 고 공간 인식의 표시 옵션을 조정 하 여 기본 혼합 현실 Toolkit 프로필을 구성 하는 방법을 배우게 됩니다이 단원의 메시입니다. 모든 설정이 나 MRTK 프로필의 값을 조정 하기 위해 이러한 동일한 원칙이 수행할 수 있습니다.

1. "BaseScene" 계층 구조에서 혼합 현실 도구 키트 (MRTK)를 선택 합니다. 검사기 창에서 스크립트에 대해"혼합 현실 도구 키트"를 확인 하 고 아래 그림에 나와 있는 것 처럼 "현재 프로필"를 선택 합니다. 두 번 클릭 하 여 엽니다.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step1im.PNG)

>참고: 기본적으로 MRTK 프로필은 편집할 수 없습니다. 기본 프로필 템플릿 복사 하 고 사용자 지정할 수 있는 이들은입니다. 표준 사례를 복사 하 여 하나 이상의 설정을 구성 하는 경우 여러 프로필을 사용자 지정 되므로 여러 계층의 사용자 지정 및 프로필에 있습니다.
>
>MRTK 프로필 및 해당 아키텍처에 대 한 자세한 정보를 검색 하려면 알아보려면 합니다 [MRTK 설명서](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/SpatialAwareness/SpatialAwarenessSystemArchitecture.html>)합니다.

2. 사용자 지정 하는 기본 프로필의 복사본을 만듭니다. 기본 프로필을 복사 하려면 클릭을 "복사 및 사용자 지정" 단추 (이미지 참조). MRTK 프로필의 복사본을 만듭니다. MRTK 프로필의 고유한 복사본을 사용 하 여 이제이 프로필에서 설정을 사용자 지정할 수가 있습니다. 이후 단계에 설명 된 대로이 프로필에서 중첩 된 추가 프로필에 대 한 복사/사용자 지정 단계를 반복 해야 합니다.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step2im.PNG)

3. 공간 인식 메시의 표시 유형을 사용 하지 않도록 설정 합니다. 이렇게 하려면 이미지에 표시 된 대로 "공간 인식 시스템 설정"을 찾습니다. 오른쪽의 "복제" 단추를 클릭 합니다 "공간 인식 시스템 프로필"을 사용자 지정할 수 있는 복사본으로 기본 프로필을 대체 합니다. 팝업 창이 표시 되 면 두 번째 이미지 아래에 표시 된 대로 "복제" 단추를 누릅니다.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3im.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step3bim.jpg)

4. 기본 혼합 현실 공간 메시 관찰자의 사용자 지정 복사본을 만듭니다. "Windows 혼합 현실 공간 메시 관찰자" 추가 옵션을 보려면 옆의 아래쪽 화살표를 클릭 합니다. 이러한 옵션에 표시 됩니다 (편집할 수 없음) "기본 혼합 현실 공간 메시 관찰자" 표시 되는 회색으로 표시 합니다. 편집할 수 있도록 사용자 지정 가능한 복사본을 사용 하 여이 기본 프로필을 바꿔야 합니다. 복사본을 복제 하려면 오른쪽 (녹색 화살표로 표시) 단추를 클릭 합니다.

![MR213_BuildSettings](images/mrlearning-base-ch2-1step4im.PNG)

5. 다음으로, "폐색."를 표시 옵션의 설정을 조정 합니다. 따라서 공간 메시 보이지 않는, 하지만 여전히 공간 메시 (이 이라고 폐색.) 뒤 게임 개체를 숨기기

![MR213_BuildSettings](images/mrlearning-base-ch2-1step5im.PNG)

>참고: 공간 매핑 메시를 표시 하는 동안에 여전히 있는 및 상호 작용할 수 있습니다. 공간 매핑 메시 (예: 뒤에 표시 되 면 홀로그램) 뒤 모든 홀로그램 폐색 설정 때문에 표시 되지 않습니다.

축하합니다. MRTK 프로필의 설정을 수정 하는 방법을 배웠습니다. 알 수 있듯이 MRTK 설정을 수정 하기 위해 해야의 복사본을 만드는 기본 프로필을 편집할 수 있도록 합니다. (하지 않은 편집 가능한)의 기본 프로필은 항상 새 설정을 사용 하 여 프로필을 만들거나 기본 프로필을 다시 참조 하려는 경우에 다시 이동 합니다. 조정할 수 있는 다양 한 설정이 있습니다. MRTK 프로필 설정에 대 한 전체 참조를 여기 MRTK 설명서를 참조 하세요. https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html

### <a name="hand-tracking-gestures-and-interactable-buttons"></a>직접 추적 제스처와 상호 작용할 수 없는 단추
이 섹션에서는 직접 상호 작용할 수 없는 단추를 눌러 추적을 사용 하는 방법을 배웁니다.

1. 프로젝트 폴더에서 "자산"을 선택 합니다.

2. 검색 표시줄을 "pressablebutton." 입력

![MR213_BuildSettings](images/mrlearning-base-ch2-2step1im.PNG)

3. (파란색 상자로 표시 됨) 하는 prefab "PressableButton" 라는 계층 구조를 끌어다 놓습니다. 

   > 참고: 에 대 한 메시지를 표시 하는 경우 지금은 가져오세요 "TMP Essentials 가져오기"입니다. TMP Essentials가 프로젝트의 일부로 이미 경우 단추 텍스트 나타나지 않을 수 있습니다이 고, 그렇지 TMP Essentials를 가져온 후이 단계를 반복 해야 합니다.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step3im.PNG)

4. 두 번 클릭 "PressableButton" 게임 개체 (BaseScene 계층에 이제 있어야) 장면에 보려는 (단추 그래픽 아래 이미지와 다르게 나타날 수 있습니다) 아래 이미지에 표시 된 대로 합니다. 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step4im.PNG)

5. 검사기 창에서 단추 이벤트를 푸시할 때 응답할 수 있도록 "이벤트 추가"를 클릭 합니다. 표시 되는 옵션에서 드롭다운 메뉴를 선택 합니다. "InteractableOnPressReciever."를 선택 합니다. 이 단추를 누름된 이벤트를 추적된 손 모양 단추를 누를 때 응답할 수 있습니다.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step5im.PNG)

6. 장면에 큐브를 추가 합니다. 계층 영역을 마우스 오른쪽 단추로 클릭, 3D 개체 선택 클릭 "큐브"입니다. 이제 큐브에 디스플레이에 있어야 합니다. 매우 큰 표시, 따라서 좌표를 조정 "큐브"는 여전히 선택 된 상태 계층 영역의 크기를 줄이려면 됩니다 것입니다. 소수 자릿수 값 x로 0.1 = y 0.1 및 z = 0.1 =. Pressable 단추 옆에 배치 장면에 큐브를 배치 해야 하지만 단추를 사용 하 여 겹쳐서는 안 됩니다. 아래 이미지에서 큐브의 위치는 x = 0, y, 0.2 및 z = = 1입니다. 

   > 참고: 일반적으로 Unity에 1 단위는 실제에서 1 미터와 거의 같습니다. 예를 들어 개체 크기 조정 된 개체의 자식인 경우이 예외가 있습니다.
   
   ![MR213_BuildSettings](images/mrlearning-base-ch2-1step6ima.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-2step6imb.PNG)

7. 이 단계에서는 사용자가 단추를 누를 때 색을 변경 하려면 큐브를 설정 합니다. PressableButton "BaseScene" 메뉴에서 선택 합니다. [관리자] 패널에서 "이벤트 형식 선택" 상자에서 "+" 단추를 클릭 합니다. 아래 이미지와 같이 "런타임만" 상자에 "큐브" "BaseScene" 메뉴에서 끌기

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7ima.PNG)

"Function 없습니다." 라는 드롭다운 목록을 클릭합니다 "MeshRenderer"를 선택한 다음 "자재 자료입니다."를 선택 합니다. 이렇게 하면 단추를 누를 때 재질을 변경할 수 있습니다. 

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imb.PNG)

프로젝트 패널 및 자료로 변경 하려는 검색으로 이동 합니다. 이 예제에 대 한 "MRTK_Standard_Cyan" 자료를 사용 하 여, "녹청" (The MRTK 많은 자료 및 색을 선택할 포함 합니다.) 프로젝트 탭의 검색 표시줄에 입력 하 여 찾을 하려는합니다 "MeshRenderer.material." 아래에 있는 상자에 재질을 끌어 옵니다. 자산에서 MRTK 자료를 찾을 수 있습니다 > MixedRealityToolkit.SDK > StandardAssets > 자료입니다.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step7imbb.PNG)

![MR213_BuildSettings](images/mrlearning-base-ch2-1step7imc.PNG)

이벤트 단추를 누르면 큐브 지정한 자료에 따라 색 변경 되도록 설정 되었습니다. 이 예제에서는 큐브 녹청 색으로 변경 됩니다.

8. 다음 릴리스 시 단추 돌아갑니다 기본 색 릴리스 작업을 설정 하는 것입니다. 아래 이미지에 표시 된 대로 "OnPress" 이벤트 대신 "OnRelease" 이벤트를 사용 하 여 이번 7 단계 (이전 단계)를 반복 합니다.

9.  프로젝트 패널에서 해제 단추 시 기본값으로 큐브에 대 한 자료에 대 한 검색 (경우에 당사가 MRTK_Standard_LightGray.) 재질 "MeshRenderer.material" 필드 아래에 있는 상자 끌어다 놓습니다.

![MR213_BuildSettings](images/mrlearning-base-ch2-2step8im.PNG)

이제 새로운 색으로 변경 해야 단추를 누를 때 (예를 들어, 녹청) 단추를 놓을 때 지정한 기본 색으로 다시 변경 해야 하 고 (예를 들어, 연한 회색입니다.) 편집기에서 사용해 테스트할 HoloLens 2에 배포 하거나 화면 맨 위에 있는 "실행" 단추를 눌러! 읽을 직접 시뮬레이션을 포함 하 여 편집기에서 시뮬레이션에 자세히 알아보려면 합니다 [MRTK의 시뮬레이션 설명서 페이지](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html>)합니다. 

### <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>패널 MRTK의 그리드 개체 컬렉션을 사용 하 여 단추 만들기

이 섹션에서는 여러 단추 MRTK의 GridObjectCollection 도구를 사용 하 여 깔끔한 사용자 인터페이스에 맞게 자동으로 조정 하는 방법을 배웁니다.

1. 5 개의 단추 표시 될 때까지 이전 섹션에서 단추를 복제 합니다. 이 작업을 수행 하는 방법은 여러 가지가 있습니다.
- 단추를 마우스 오른쪽 단추로 클릭 및 "복사"를 클릭 한 다음 단추 아래의 아래로 이동 및 마우스 오른쪽 단추로 다시 클릭 "붙여 넣습니다."를 클릭 
- 단추를 마우스 오른쪽 단추로 클릭 하 고 "중복 되었습니다."를 클릭 합니다. 
- 큐브 및 키를 눌러 "ctrl D" 키보드에서를 클릭 하 여 키보드 명령을 사용 합니다.

총 5 개의 단추 표시 (아래 이미지에서 빨간색 화살표 5 참조) 될 때까지이 단계를 반복 합니다.

![C h 2 3Step1im Mrlearning 자료](images/mrlearning-base-ch2-3step1im.PNG)

2. 빈 부모 게임 개체 아래에 있는 단추를 그룹화 합니다. 표 컬렉션의 단추를 위해서는 공통 부모 개체 아래에 있는 단추를 그룹화 해야 합니다. hiearachy 마우스 오른쪽 단추로 클릭 하 고 "빈 항목 만들기."를 클릭 합니다. 에 있는 모든 단추를 삽입할 수에 대 한 새 빈 게임 개체를 만듭니다. "GameObject."으로 표시 됩니다. 마우스 오른쪽 단추로 클릭 하 고 이름을 "ButtonCollection."로

![C h 2 3Step2im Mrlearning 자료](images/mrlearning-base-ch2-3step2im.PNG)

3. 새 컬렉션에 있는 모든 단추를 이동 합니다. 아래 이미지에 표시 된 대로 "ButtonCollection" 게임 개체에서 모든 끌어와 프로그램 heirarch에서 5 개 모두 단추 개체를 선택 하 여이 작업을 수행 합니다. 팁: ctrl 키를 누른 채 항목을 선택 하 여 여러 항목을 선택 합니다.

![C h 2 3Step3imb Mrlearning 자료](images/mrlearning-base-ch2-3step3imb.PNG)

4. 단추 컬렉션 MRTK의 "표 개체 컬렉션" 구성 요소를 추가 합니다.  이렇게 하려면 "ButtonCollection" 부모 개체를 선택 하 고 [관리자] 패널에서 "구성 요소 추가" 단추를 클릭 합니다. 검색 표시줄에서 "그리드 개체 컬렉션"에 대 한 검색 한 다음 목록에 나타나면 선택 합니다.

![C h 2 3Step4im Mrlearning 자료](images/mrlearning-base-ch2-3step4im.PNG)

표 개체 컬렉션 구성 요소를 사용 하면 단추 또는 구성할 수 있습니다 깔끔하게 행, 열 또는 그리드 개체. 이 방법으로 멋진 사용자 인터페이스를 만드는 빠르고 간단한 방법을 제공 하는 MRTK 제공한 구성 요소 중 하나입니다.

5. 표 개체 컬렉션을 구성 합니다. 을 보장 하기 위해 모든 단추 모양을 사용자 "형식 방향을 설정"을 선택 하 고 (표시 된 대로 이미지에서입니다.) "전달 부모 직면"를 선택 합니다 다음에서 단추 사이의 간격을 설정 하는 셀 크기를 변경 합니다. 아래 이미지 에서처럼 0.12 단위로 0.12 단위를 사용 하 여 셀 너비 및 셀 높이 시작 합니다. 개체/단추 자산 선택에 따라 이러한 값을 조정 해야 합니다. "행"은 1로 설정 되어 있는지 확인 합니다. 그런 다음 "컬렉션 업데이트"를 클릭 하 고 장면 아래 그림과 같이 표시 됩니다. 


![C h 2 3Step5im Mrlearning 자료](images/mrlearning-base-ch2-3step5im.PNG)

>참고: 부모 개체 또는 자식 개체의 방향에 따라 향후 프로젝트에 다르게 설정 방향을 조정 해야 가능성이 높습니다. 셀 너비 및 셀 높이 필드 컬렉션에 있는 개체의 크기에 따라 다르게 정의 해야 합니다.

### <a name="adding-text-into-your-scene"></a>장면에 텍스트 추가

이 섹션에서는 추가 혼합된 현실 경험 하는 텍스트를 편집 하는 방법을 배우게 됩니다. 이미 않았다면의 TextMeshPro 지침에 따라 Unity에서 사용 하도록 설정 했는지 확인 하십시오 [여기](https://docs.unity3d.com/Packages/com.unity.textmeshpro@2.0/manual/index.html#installation)합니다.

1. "ButtonCollection" 부모 개체를 선택 하 고 컬렉션을 마우스 오른쪽 단추로 클릭 합니다. 드롭다운 메뉴에서 "3D 개체"를 확장 한 후 "TextMeshPro-Text"를 선택 합니다. 아래 이미지에 표시 된 대로 단추 컬렉션에서 TextMeshPro 개체를 표시 됩니다.

![단원 2 종단간 Chapter4 Step1a](images/Lesson2_Chapter4_Step1a.JPG)
![단원 2 종단간 Chapter4 Step1b](images/Lesson2_Chapter4_Step1b.JPG)

2. TextMeshPro 요소의 텍스트 필드 (아래와 같이 [관리자] 패널에 있음) "단추 컬렉션 Text." 입력 텍스트는 장면에 나타나지만 단추 및/또는 크기가 잘못 뒤 숨겨집니다.

![단원 2 종단간 Chapter4 2 단계](images/Lesson2_Chapter4_Step2.JPG)

3. 텍스트 크기와 배치를 가독성 향상을 위해 글꼴의 크기를 변경 하려면 TextMeshPro 구성 요소에서 "글꼴 크기" 필드를 조정 합니다. 아래 이미지에 표시 된 대로 확장와 "Rect 변환" 위치 조정 해야 합니다. 이 텍스트 구성에 사용 되는 값에 대 한 아래 이미지 참조 및 자유롭게 크기 및 텍스트 필드의 배치를 강화 하는 시작 지점으로 이러한 값을 사용 합니다.

![단원 2 종단간 Chapter4 3 단계의](images/Lesson2_Chapter4_Step3.JPG)
![단원 2 종단간 Chapter4 4 단계](images/Lesson2_Chapter4_Step4.JPG)

5. 단추 개체의 텍스트 값을 수정 하려면 여 확장 하 고 "SeeItSayItLabel" 개체 이동 단추 옆의 화살표를 클릭 한 다음 위의 단계에 설명 된 대로 단추에 텍스트를 편집할 수 있는 "TextMeshPro,"로 이동 합니다.

![단원 2 종단간 Chapter4 5 단계](images/Lesson2_Chapter4_Step5.JPG)

### <a name="congratulations"></a>축 하.
이 단원에서는 복사 사용자 지정 하 고 (즉, 공간 인식 메시 표시 유형입니다.) MRTK 프로필 설정을 구성 하는 방법을 배웠습니다. 이벤트를 트리거하기 위해 HoloLens 2에서 추적된 실습을 사용 하 여 단추와 상호 작용 하는 방법을 알아보았습니다. 마지막으로, Unity의 텍스트 메시 Pro를 사용 하 여 간단한 UI 인터페이스 MRTK의 표 개체 컬렉션 구성 요소를 만드는 방법을 알아보았습니다.

[다음 단원: 동적 콘텐츠 배치 및 해 찾기](mrlearning-base-ch3.md)

