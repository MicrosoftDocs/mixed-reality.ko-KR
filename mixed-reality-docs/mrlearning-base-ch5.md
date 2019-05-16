---
title: MR 학습 자료 모듈-고급 입력
description: 혼합된 현실 응용 프로그램에서 Azure Face recognition 얼굴 인식을 구현 하는 방법을 알아보려면이 과정을 완료 합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: unity, 자습서, hololens, 혼합된 현실
ms.openlocfilehash: 32141aafd43c5d729919673509c93bb2014edd37
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730927"
---
# <a name="mr-learning-base-module---advanced-input"></a>MR 학습 자료 모듈-고급 입력

이 단원에서는 음성 명령, 터치식 이동 제스처 및 시선 추적의 사용을 포함 하는 HoloLens 2에 대 한 몇 가지 고급 입력된 옵션을 살펴봅니다. 

## <a name="objectives"></a>목표

- 음성 명령 및 키워드를 사용 하 여 이벤트를 트리거하는 방법에 알아봅니다.
- 추적 된 실습을 사용 하 여 텍스처와 3D 개체 이동
- HoloLens 2의 눈 모양 추적 개체를 선택 하는 기능을 활용 합니다.

## <a name="instructions"></a>지침

### <a name="enabling-voice-commands"></a>음성 명령 사용

이 섹션에서는 구현 두 음성 명령입니다. 첫 번째 "토글 진단 합니다." 라는 가정에서 프레임 속도 진단 패널을 전환 하는 기능 둘째, 음성 명령 사용 하 여 소리를 재생 하는 기능. 먼저 살펴봅니다 MRTK 프로필 및 설정 음성 명령을 구성 하는 일을 담당 합니다. 

1. 기본 장면 계층에서 "MixedRealityToolkit."를 선택 합니다. 검사기 창에서 입력된 시스템 설정 될 때까지 스크롤하십시오. 두 번 입력된 시스템 프로필을 열려면 클릭 합니다. 입력된 시스템 프로필을 편집할 수 있도록에서 배운 것 처럼 복제 [1 단원](mrlearning-base-ch1.md) 

입력된 시스템 프로필에 다양 한 설정이 표시 됩니다. 음성 명령에 대 한으로 이동 라고 표시 된 부분을 "음성 명령을 설정 합니다." 

![Lesson5 Chapter1 Step2im](images/Lesson5_Chapter1_step2im.PNG)

2. 복제에서 배운 것 처럼, 편집할 수 있도록 음성 명령을 프로필 [1과](mrlearning-base-ch1.md)합니다. 설정의 범위를 보면 음성 명령 프로필을 두 번 클릭 합니다. 이러한 설정에 대 한 전체 설명은 참조 합니다 [MRTK speech 설명서](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>)합니다. 

>참고: 기본적으로 일반 동작은 자동으로 시작 합니다. 수동 시작 원하는 경우 변경할 수 있습니다 않았지만이 예제 예정에 자동으로 시작 되도록 합니다. MRTK 몇 가지 기본 음성 명령 (예: 메뉴, 진단 설정/해제 및 설정/해제 프로파일러)를 사용 하 여 제공 됩니다. "진단 켜기/끄기" 키워드를 사용 설정 및 진단 프레임 속도 카운터 해제 하기 위해. 또한 아래 단계에서는 새 음성 명령을 추가 합니다.
>
> ![Lesson5 Chapter1 Noteim](images/Lesson5_chapter1_noteim.PNG)

3. 새 음성 명령을 추가 합니다. 새 음성 명령에 추가 하려면 "+ 새 음성 명령을 추가" 단추를 클릭 하 고 아래로 기존 음성 명령 목록 아래에 표시 되는 새 줄이 표시 됩니다. 사용 하려는 음성 명령을 입력 합니다. Musicample 예이 하겠습니다 "음악을 재생 합니다." 명령을 사용 하 여

>팁:  또한 음성 명령에 대 한 키를 코드를 설정할 수 있습니다. 이렇게 하면 음성 명령을 키보드 키를 누를 때 트리거할 수 있습니다.   

4. 음성 명령에 응답 하는 기능을 추가 합니다. (예를 들어 없습니다 조작 처리기입니다.)에 연결 된 모든 다른 입력된 스크립트 없는 기본 장면 계층의 모든 개체를 선택 합니다. 검사기 창에서 "구성 요소를 추가 합니다."를 클릭 입력 "입력된 음성 처리기입니다." 선택 합니다.
   ![Lesson5 Chapter1 Step4im](images/Lesson5_chapter1_step4im.PNG)

   

기본적으로 2 확인란 표시 됩니다, 그리고 하나는 "is 포커스 필요" 확인란을 선택 합니다. 즉 음성 명령으로 게이즈 광선, (응시로, 헤드 게이즈, 컨트롤러 게이즈, 또는 직접 게이즈) 개체를 가리키는 트리거됩니다. 사용자 음성 명령을 사용 하 여 개체를 볼 필요가 없습니다 있도록 있도록 하려면이 확인란의 선택을 취소 합니다.

5. 음성 명령에 응답 하는 기능을 추가 합니다. 이 위해 음성 입력된 처리기에 있는 "+" 단추를 클릭 하 고 응답할 하려는 키워드를 선택 합니다.

   > 참고: 이러한 키워드는 이전 단계에서 편집한 프로필을 기반으로 채워집니다.

![Lesson5 Chapter1 Step5im](images/Lesson5_chapter1_step5im.PNG)

6. "키워드" 옆에 있는 드롭다운 메뉴가 표시 됩니다. "진단 전환 합니다." 선택 이렇게 하면 작업을 트리거할 때마다 사용자가 "진단 설정/해제" 구의 되도록 합니다. 옆에 있는 화살표를 눌러 "요소 0"을 확장 해야 note 합니다.

![Lesson5 Chapter1 Step6im](images/Lesson5_chapter1_step6im.PNG)

7. "진단 데모 컨트롤 스크립트"를 추가 프레임 속도 카운터 진단을 설정 / 해제 합니다. 이렇게 하려면 "구성 요소 추가" 단추 및 "진단 데모 제어 스크립트" 검색 키를 눌러 다음 메뉴에서 추가 합니다. 이 스크립트는 모든 개체에 추가할 수 있습니다 하지만 편의상,이를 추가 음성 입력된 처리기와 같은 개체입니다. 

   > 참고:이 스크립트는만 이러한 모듈을 사용 하 여 포함 하 고 원래 MRTK를 사용 하 여 포함 되지 않습니다.

![Lesson5 Chapter1 Step7im](images/Lesson5_chapter1_step7im.PNG)

8. 새 응답이 음성 입력 처리기에 추가 합니다. 작업을 수행 하이 (위의 그림에서 녹색 화살표로 표시) 있는 "응답 ()" 라는 부분이 아래에 있는 "+" 단추를 클릭 했습니다.

![Lesson5 Chapter1 Step7im](images/Lesson5_chapter1_step8.PNG)

9. 8 단계에서 방금 만든 새 응답에 진단 데모 컨트롤 스크립트를 포함 하는 개체를 끕니다.
    ![Lesson5 Chapter1 Step9im](images/Lesson5_chapter1_step9im.PNG)

10. 이제 "함수가" 드롭다운 목록을 선택 하 고, 진단 데모 컨트롤을 선택한 다음, "에 설정/해제 (진단)." 이 함수에서 진단 설정 및 해제 합니다.  ![Lesson5 Chapter1 Step10im](images/Lesson5_chapter1_step10im.PNG)
    
> 장치를 빌드하기 전에 mic 설정을 사용 하도록 설정 해야 있습니다 note 합니다. 파일을 클릭을 위해 빌드 설정, 거기서 플레이어 설정으로 이동 하 고 마이크 기능이 설정 되어 있는지 확인 합니다.

다음으로, "옥 타" 개체를 사용 하 여 음성 명령에서 오디오 파일을 재생 하는 기능이 추가 되었습니다. 설명한 대로 [4 단원](mrlearning-base-ch4.md)에 옥 타 개체 않도록 오디오 클립을 재생 하는 기능을 추가 했습니다. 우리의 음악 음성 명령에 대 한이 동일한 오디오 소스를 활용 합니다.

11. 기본 장면 계층에 옥 타 개체를 선택 합니다.

12. 다른 음성 입력된 처리기 (반복 4, 5 단계)를 추가 하지만 옥 타 개체입니다. 

13. 6 단계에서 "진단 켜기/끄기" 음성 명령에 추가 하는 대신 아래 그림과에서 같이 "음악을 재생" 음성 명령으로 추가 합니다.
    
     ![Lesson5 Chapter1 Step13im](images/Lesson5_chapter1_step13im.PNG)
    
    
    
14. 8 및 9 단계와 마찬가지로 새 응답을 추가 하 고 빈 슬롯을 옥 타 응답에 끌어 놓습니다.

15. "없는 함수를" select "오디오 원본"을 선택 "(AudioClip) PlayOneShot." 라는 드롭다운 메뉴를 선택 합니다.

![Lesson5 Chapter1 Step15im](images/Lesson5_chapter1_step15im.PNG)

16. 오디오 클립은이 예제에 대 한 것에서 동일한 오디오 클립을 사용 하도록 [4 단원](mrlearning-base-ch4.md)합니다. 프로젝트 패널을 이동한 "MRTK_Gem" 오디오 클립을 검색할 아래 이미지에 표시 된 대로 오디오 원본 슬롯에 놓습니다. 응용 프로그램 "전환 진단" 음성 명령에 응답할 수 있어야 합니다. 이제 프레임 속도 카운터 패널을 전환 하 고 "음악 재생" MRTK_Gem song을 재생 합니다.
     ![Lesson5 Chapter1 Step16im](images/Lesson5_chapter1_step16im.PNG)


### <a name="the-pan-gesture"></a>팬 제스처 

이 챕터에서는 이동 제스처를 사용 하는 방법을 배웁니다. (사용에 손가락이 나 직접 콘텐츠를 스크롤할 수 있습니다.)를 스크롤 하는 데 유용 또한도 스크롤 2D UI 3D 개체의 컬렉션을 순환 시킬 개체를 회전 하려면 팬 제스처를 사용할 수 있습니다. 팬 제스처 질감 warp를 사용 하는 방법을 학습 했습니다. 3D 개체의 컬렉션을 이동 하는 방법을 또한 살펴봅니다.

1. 사각형을 만듭니다. 기본 장면 계층을 마우스 오른쪽 단추로 클릭, "3D 개체에" 선택한 "쿼드."를 선택 합니다.

![Lesson5 Chapter2 Step2im](images/Lesson5_chapter2_step2im.PNG)

2. 적절 하 게 쿼드 위치를 변경 합니다. 예를 들어 x 설정 = 0, y = 0, z = HoloLens 2에서 편리한 위치에 대 한 카메라에서 1.5 합니다.

   > 참고: 경우 쿼드 블록 (아닙니다 앞) 이전 단원에서 모든 콘텐츠를 다른 개체의 모든 차단 하지는 이동 해야 합니다.

3. 쿼드에 재질을 적용 합니다. 이 자료는 팬 제스처를 사용 하 여을 통해 스크롤 됩니다 것 자료가 됩니다. 

![Lesson5 Chapter2 Step3im](images/Lesson5_chapter2_step3im.PNG)

4. "이동 콘텐츠입니다." 검색 상자에 입력에 프로젝트 패널 장면에서 쿼드에 해당 자료를 끕니다. 

> 참고: "콘텐츠 이동" 자료는 MRTK에 포함 되지 않습니다 이지만이 모듈의 자산 패키지에 자산 이전 단원에서 가져온 대로 합니다. 

> 참고: 팬 콘텐츠를 추가 하는 경우 늘어난 보일 수 있습니다. 그 모양이 만족할 때까지 x, y 및 z 값은 쿼드 크기의 값을 조정 하 여이 해결할 수 있습니다.

팬 제스처를 사용 하려면 개체는 collider를 해야 합니다. 쿼드 메시 collider에 이미 표시 될 수 있습니다. 그러나 매우 어렵고 씬 선택 이므로 메시 collider에 적합 하지 않습니다. 상자 collider를 사용 하 여 메시 collider를 대체 하는 것이 좋습니다.

5. (검사기 패널)에서 쿼드에 있는 메시 collider를 마우스 오른쪽 단추로 클릭 한 다음 "구성 요소를 제거 합니다."를 클릭 하 여 제거 
   ![Lesson5 Chapter2 Step5im](images/Lesson5_chapter2_step5im.PNG)

6. 이제 상자 collider "구성 요소를 추가" 클릭 "collider box."를 검색 하 여 추가 상자 collider는 씬 여전히 기본값 추가, 편집 "collider 편집" 단추를 클릭 합니다. 이 누를 때 장면 편집기에서 x, y 및 z 값 또는 요소를 사용 하 여 크기를 조정할 수 있습니다. 예를 들어 쿼드를 뒤 상자 collider를 약간 확장 하려고 합니다. 장면 편집기의 뒷면에 그라데이션이 (아래 이미지 참조)에서 상자 collider를 끕니다. 뿐만 아니라 사용 하 여 해당 손가락 하지만 전체 속속들이 스크롤해야 할 수는이 수행 됩니다. 
    ![Lesson5 Chapter2 Step6im](images/Lesson5_chapter2_step6im.PNG)
7. 대화형 확인 합니다. 쿼드와 직접 상호 작용 하려고 하므로 (것도 사용이 4 단원에서에서는 옥 타에서 음악을 재생)는 "근처 touchable 상호 작용" 구성 요소를 사용 하려고 합니다. "구성 요소 추가"를 클릭 합니다 "상호 작용 touchable 근처" 검색 하 고 아래 이미지에 표시 된 대로 선택 합니다. 

8. 팬 제스처를 인식 하는 기능을 추가 합니다. "구성 요소를 추가"를 클릭 하 고 "상호 작용 pan을 전달 합니다." 입력 직접 광선 (거리에서 이동할 수 있도록) 및 집게 손가락 중에서 선택을 해야 합니다. 예를 들어 집게 손가락으로 유지 합니다. 
    ![Lesson5 Chapter2 Step7 8Im](images/Lesson5_chapter2_step7-8im.PNG)

![Lesson5 Chapter2 Step8im](images/Lesson5_chapter2_step8im.PNG)

9. 직접 상호 작용 팬 스크립트에서 "잠금 가로" 및 "lock 세로" 확인란 잠깁니다 움직임, 각각. 자동 줄 바꿈 질감 설정 텍스처 (텍스처 매핑) 하 게 사용자의 팬 이동을 수행 합니다. 예를 들어 해당 확인란을 선택 하려고 합니다. "Velocity active" 옵션을 선택 취소 하는 경우 이동 제스처가 작동 하지 것입니다는 이기도 합니다. 이 상자도 선택 합니다. 이제 이동 지원 쿼드가 있어야 합니다.

   

   다음으로, 3D 개체를 이동 하는 방법을 배웁니다. 

10. 4 개의 개체를 마우스 오른쪽 단추로 클릭, 3D 개체 선택 클릭 "큐브"입니다. 되도록 대략 x 큐브 확장 0.1 = y = 0.1 및 z = 0.1입니다. (큐브를 마우스 오른쪽 단추로 클릭 하 고 중복 키를 눌러 또는 명령에 의해 키를 눌러 컨트롤/D) 해당 큐브에 3 회를 복사 합니다. 공간을 넉넉히 확보 균등 하 게 합니다. 장면 아래 그림과 유사 해야 합니다.

![Lesson5 Chapter2 Step10im](images/Lesson5_chapter2_step10im.PNG)







11. 쿼드를 다시 선택 하 고 직접 상호 작용 팬 스크립트 아래에 있는 각 큐브 이동 작업을 설정 하려고 합니다. "이동 이벤트 수신기"에서 이벤트를 수신 하는 개체의 수를 지정 하려고 합니다. 4 큐브 되므로 유형 "4" enter 키를 누릅니다. 4 개의 빈 필드 표시 됩니다.


![Lesson5 Chapter2 Step11im](images/Lesson5_chapter2_step11im.PNG)



12. 각 요소를 빈 슬롯에 각각에서 큐브를 끕니다.
     ![Lesson5 Chapter2 Step12im](images/Lesson5_chapter2_step12im.PNG)
    
13. 큐브의 모든 "pan 이동" 스크립트를 추가 합니다. 이 위해 제어/명령 길게 누른 각 개체를 선택 합니다. 그런 다음 검사기 창에서 "구성 요소 추가"를 클릭 하 고 "팬을 사용 하 여 이동 합니다." 검색 스크립트를 클릭 하 고 각 큐브에 추가 됩니다. 이제 3D 개체 이동 제스처를 사용 하 여 이동 합니다. 제거 하는 경우에 쿼드에서 메시 렌더링, 이제는 보이지 않는 쿼드 3D 개체의 목록을 통해 이동할 수 있습니다.

### <a name="eye-tracking"></a>시선 추적

이 챕터에서는 데모에서 눈 추적을 사용 하도록 설정 하는 방법을 살펴봅니다. 느린 응시를 사용 하 여 시 gazed 되는 경우는 3D 메뉴 항목을 회전 합니다 했습니다. 재미 있게도 트리거할에서는 gazed 시 항목을 선택할 때 적용 됩니다.

1. 혼합 현실 Toolkit 프로필이 제대로 구성 되어 있는지 확인 합니다. 이 문서의 작성 시점 현재 혼합된 현실 toolkit 프로필 구성에는 눈 추적 기능을 기본적으로 포함 되지 않습니다. 에 설명 된 대로 시선 추적 기능을 추가 하려면 "눈 추적에 필요한 MRTK 프로필 설정" 섹션의 지침에 따라 합니다 [혼합 현실 도구 키트 설명서](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-the-mrtk-profiles-required-for-eye-tracking  )합니다. 시선 추적 GazeProvider (카메라에 연결 된 구성 요소)의 눈 모양 추적 및 시선 Unity 편집기에서 추적의 시뮬레이션을 사용 하도록 설정 하면 사용을 포함 한 위의 설명서 링크의 나머지 단계를 수행 하 여 올바르게 구성 되어 있는지 확인 합니다. 참고는 나중 버전의 MRTK의 눈 모양 추적 기본적으로 포함 될 수 있습니다.

    위의 링크에 대 한 간략 한 지침을 제공합니다.

    - MRTK 프로필의 사용에 대 한 눈 모양 Gaze 데이터 공급자 만들기
    - Gaze 공급자의 눈 모양 추적을 사용 하도록 설정
    - 편집기에서 추적 눈을 시뮬레이션 하기 위한 설정
    - 작성된 된 응용 프로그램에 눈 추적할 수 있도록 Visual Studio 솔루션의 기능 편집

2. 대상 개체에 시각 추적 대상 구성 요소를 추가 합니다. 눈 게이즈 이벤트에 응답 하는 개체를 허용 하려면 응시를 사용 하 여 상호 작용 하는 각 개체에 대해 EyeTrackingTarget 구성 요소를 추가 해야 합니다. 각 표 컬렉션의 일부인 9 3D 개체에이 구성 요소를 추가 합니다. 팁: EyeTrackingTarget 구성 요소를 일괄 추가할 계층의 여러 항목을 선택 합니다.
    ![Lesson5 Chapter3 2 단계](images/Lesson5Chapter3Step2.JPG)

3. 다음 몇 가지 흥미로운 상호 작용을 위한 EyeTrackingTutorialDemo 스크립트를 추가 합니다. 이 자습서 시리즈의 리포지토리의 일부로 포함 EyeTrackingTutorialDemo 스크립트 이며 혼합 현실 도구 키트를 사용 하 여 기본적으로 포함 되지 않습니다. 표 컬렉션의 각 3D 개체에 대 한 "구성 요소 추가" 메뉴에서 구성 요소를 검색 하 여 EyeTrackingTutorialDemo 스크립트를 추가 합니다.
   ![Lesson5 Chapter3 3 단계](images/Lesson5Chapter3Step3.JPG)

   4. 대상 확인 하는 동안 개체를 회전 합니다. 살펴보고 있는 해당 하는 동안 회전은 3D 개체를 구성 하려고 합니다. 이렇게 하려면 아래 이미지에 표시 된 대로 EyeTrackingTarget 요소의 "하는 동안 확인에서 대상" 섹션에 새 필드를 삽입 합니다. 

![Lesson5 Chapter3 Step4a](images/Lesson5Chapter3Step4a.JPG)
![Lesson5 Chapter3 Step4b](images/Lesson5Chapter3Step4b.JPG)



새로 만든된 필드에 빈 필드에 현재 게임 개체를 추가 하 고 EyeTrackingTutorialDemo 선택 > RotateTarget() 아래 이미지에 표시 된 대로 합니다. 이제 3D 개체는 눈 추적 시 gazed 되는 경우 실행 하도록 구성 됩니다. 

5. 기능에서 선택 (어-탭 또는 "select" 라는) 시에 gazed 되는 "블 립이 대상"에 추가 합니다. 4 단계와 마찬가지로, 우리가 트리거 하려는 EyeTrackingTutorialDemo > BlipTarget() 아래 그림에 나와 있는 것 처럼 EyeTrackingTarget 요소의 게임 개체의 "select" () 필드에 할당 하 여 합니다. 이제 구성이 표시 됩니다 어 탭 또는 음성 명령 등 선택 작업을 트리거하는 때마다 게임 개체에 약간의 문제가 "선택 합니다." 
    ![Lesson5 Chapter3 5 단계](images/Lesson5Chapter3Step5.JPG)
6. HoloLens 2를 빌드하기 전에 제대로 구성 눈 추적 기능을 확인 합니다. 이 문서의 작성 시점 현재 Unity 아직 없는 게이즈 (눈 추적)에 대 한 입력된 기능을 설정할 수 있습니다. 이 기능을 설정 하는 것이 눈 추적 HoloLens 2에서 작동 하려면 필요 합니다. 응시 입력된 기능을 사용 하도록 설정 하려면 혼합된 현실 도구 키트 설명서에서 이러한 지침을 따릅니다. https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2 


### <a name="congratulations"></a>축하합니다. 
응용 프로그램에 기능을 추적 하는 기본 눈을 추가 했습니다. 이러한 작업은 새로운 시선 추적을 사용 하 여 가능성을의 시작일 뿐입니다. 이 장에서도 배우게 5, 여기서 음성 명령 등 고급 입력된 기능에 대 한 이동을 제스처 및 눈 추적으로 마칩니다. 

[다음 단원: 음력 모듈 어셈블리 샘플 환경](mrlearning-base-ch6.md)

