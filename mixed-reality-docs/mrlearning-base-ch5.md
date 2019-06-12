---
title: MR 학습 기본 모듈 - 고급 입력
description: 혼합 현실 애플리케이션에서 Azure 얼굴 인식을 구현하는 방법을 알아보려면 이 과정을 완료합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 32141aafd43c5d729919673509c93bb2014edd37
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66719890"
---
# <a name="mr-learning-base-module---advanced-input"></a>MR 학습 기본 모듈 - 고급 입력

이 단원에서는 음성 명령, 이동 제스처 및 시선 추적을 비롯한 HoloLens 2의 몇 가지 고급 입력 옵션을 살펴봅니다. 

## <a name="objectives"></a>목표

- 음성 명령 및 키워드를 사용하여 이벤트를 트리거하는 방법 알아보기
- 추적 손을 사용하여 텍스처 및 3D 개체 이동
- HoloLens 2의 시선 추적 기능을 활용하여 개체 선택

## <a name="instructions"></a>지침

### <a name="enabling-voice-commands"></a>음성 명령 사용

이 섹션에서는 두 가지 음성 명령을 구현합니다. 첫째는 "진단 전환"이라고 말하여 프레임 속도 진단 패널을 전환하는 기능입니다. 둘째는 음성 명령을 사용하여 소리를 재생하는 기능입니다. 먼저, 음성 명령을 구성하기 위한 MRTK 프로필 및 설정을 알아봅니다. 

1. 기본 장면 계층에서 "MixedRealityToolkit"을 선택합니다. inspector 패널에서 아래로 스크롤하여 입력 시스템 설정으로 이동합니다. 두 번 클릭하여 입력 시스템 프로필을 엽니다. [1단원](mrlearning-base-ch1.md)에서 배운 것처럼 입력 시스템 프로필을 편집 가능하도록 복제합니다. 

입력 시스템 프로필에는 다양한 설정이 표시됩니다. 음성 명령을 사용하려면 아래쪽의 "Speech Command Settings" 위치로 이동합니다. 

![Lesson5 Chapter1 Step2im](images/Lesson5_Chapter1_step2im.PNG)

2. [1단원](mrlearning-base-ch1.md)에서 배운 것처럼 음성 명령 프로필을 편집 가능하도록 복제합니다. 음성 명령 프로필을 두 번 클릭하여 전체 설정 범위를 표시합니다. 이러한 설정에 대한 전체 설명은 [MRTK 음성 설명서](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>)를 참조하세요. 

>참고: 기본적으로 일반 동작은 자동 시작입니다. 원할 경우 수동 시작으로 변경할 수 있지만 이 예제에서는 자동 시작을 유지합니다. MRTK에는 몇 가지 기본 음성 명령(예: 메뉴, 진단 전환, 프로파일러 전환)이 제공됩니다. 진단 프레임 속도 카운터를 켜거나 끄기 위해 키워드 "진단 전환"을 사용합니다. 또한 아래 단계에서는 새 음성 명령을 추가합니다.
>
> ![Lesson5 Chapter1 Noteim](images/Lesson5_chapter1_noteim.PNG)

3. 새 음성 명령을 추가합니다. 새 음성 명령에 추가하려면 "+ add a new speech command" 단추를 클릭합니다. 그러면 기존 음성 명령 목록 아래에 새 줄이 표시됩니다. 사용하려는 음성 명령을 입력합니다. 이 음악 예제에서는 명령 "play music”을 사용합니다.

>팁: 또한 음성 명령의 키코드도 설정할 수 있습니다. 키코드를 설정하면 키보드 키를 누를 때 음성 명령이 트리거될 수 있습니다.   

4. 음성 명령에 응답하는 기능을 추가합니다. 다른 입력 스크립트가 연결되지 않은 개체(예: 조작 처리기 없음)를 기본 장면 계층에서 선택합니다. inspector 패널에서 "add component"를 클릭합니다. "speech input handler"를 입력합니다. 해당 항목을 선택합니다.
   ![Lesson5 Chapter1 Step4im](images/Lesson5_chapter1_step4im.PNG)

   

기본적으로 2개의 확인란이 표시됩니다. 하나는 "is focus required" 확인란입니다. 이 확인란은 응시 레이(시선 응시, 머리 응시, 컨트롤러 응시 또는 손 응시)로 개체를 가리키는 경우 음성 명령이 트리거됨을 의미합니다. 이 확인란을 선택 취소하여 사용자가 음성 명령을 사용하기 위해 개체를 볼 필요가 없도록 합니다.

5. 음성 명령에 응답하는 기능을 추가합니다. 이를 수 행하려면 음성 입력 처리기에 있는 "+" 단추를 클릭하고 응답하려는 키워드를 선택합니다.

   > 참고: 이러한 키워드는 이전 단계에서 편집한 프로필을 기준으로 채워집니다.

![Lesson5 Chapter1 Step5im](images/Lesson5_chapter1_step5im.PNG)

6. "키워드" 옆에는 드롭다운 메뉴가 표시됩니다. "Toggle Diagnostics"를 선택합니다. 이렇게 하면 사용자가 "진단 전환"이라고 말할 때마다 이 작업이 트리거됩니다. 옆에 있는 화살표를 눌러 "element 0"을 확장해야 할 수도 있습니다.

![Lesson5 Chapter1 Step6im](images/Lesson5_chapter1_step6im.PNG)

7. 프레임 속도 카운터 진단을 설정/해제하는 "diagnostics demo control script"를 추가합니다. 이렇게 하려면 "add component" 단추를 누르고 "diagnostics demo control script" 검색한 후 메뉴에서 추가합니다. 이 스크립트를 어떤 개체에도 추가할 수 있지만 편의상, 음성 입력 처리기와 동일한 개체에 추가합니다. 

   > 참고: 이 스크립트는 이러한 모듈에만 포함되며 원래 MRTK에는 포함되어 있지 않습니다.

![Lesson5 Chapter1 Step7im](images/Lesson5_chapter1_step7im.PNG)

8. 음성 입력 처리기에 새 응답을 추가합니다. 이 작업을 수행하려면 “response ()” 아래의 "+" 단추(위 그림에서 녹색 화살표로 표시)를 클릭합니다.

![Lesson5 Chapter1 Step7im](images/Lesson5_chapter1_step8.PNG)

9. Diagnostics Demo Controls 스크립트를 포함하는 개체를 8단계에서 방금 만든 새 응답으로 끌어옵니다.
    ![Lesson5 Chapter1 Step9im](images/Lesson5_chapter1_step9im.PNG)

10. 이제 "no function" 드롭다운 목록을 선택하고, 진단 데모 컨트롤을 선택한 다음, “on toggle diagnostics ()”를 선택합니다. 이 함수는 진단 설정 및 해제를 전환합니다.  ![Lesson5 Chapter1 Step10im](images/Lesson5_chapter1_step10im.PNG)
    
> 디바이스를 빌드하기 전에 마이크 설정을 사용하도록 설정해야 합니다. 이를 위해 파일을 클릭하고, 빌드 설정, 플레이어 설정으로 이동한 후 마이크 기능이 설정되어 있는지 확인합니다.

다음으로, "octa" 개체를 사용하여 음성 명령에서 오디오 파일을 재생하는 기능을 추가합니다. 앞서 [4단원](mrlearning-base-ch4.md)에서는 옥타 개체를 터치하여 오디오 클립을 재생하는 기능을 추가했습니다. 음악 음성 명령에 대해서도 이 동일한 오디오 원본을 활용합니다.

11. 기본 장면 계층 구조에서 옥타 개체를 선택합니다.

12. 다른 음성 입력 처리기(4, 5단계 반복)를 추가하지만 이번에는 옥타 개체를 사용합니다. 

13. 6단계의 "Toggle Diagnostics" 음성 명령에 추가하는 대신, 아래 그림과 같이 "play music" 음성 명령을 추가합니다.
    
     ![Lesson5 Chapter1 Step13im](images/Lesson5_chapter1_step13im.PNG)
    
    
    
14. 8 및 9단계와 마찬가지로 새 응답을 추가하고, 응답의 빈 슬롯으로 옥타를 끌어옵니다.

15. "no function"이라는 드롭다운 메뉴를 선택하고 "Audio Source"를 선택한 후 “PlayOneShot (AudioClip)”을 선택합니다.

![Lesson5 Chapter1 Step15im](images/Lesson5_chapter1_step15im.PNG)

16. 오디오 클립의 경우 이 예제에서는 [4단원](mrlearning-base-ch4.md)의 동일한 오디오 클립을 사용합니다. 프로젝트 패널을 이동한 후 "MRTK_Gem" 오디오 클립을 검색하고 아래 이미지와 같이 오디오 원본 슬롯으로 끌어옵니다. 이제 애플리케이션은 "toggle diagnostics" 음성 명령에 반응하여 프레임 속도 카운터 패널을 설정/해제하고 "play music" 명령에 따라 MRTK_Gem 곡을 재생할 수 있습니다.
     ![Lesson5 Chapter1 Step16im](images/Lesson5_chapter1_step16im.PNG)


### <a name="the-pan-gesture"></a>이동 제스처 

이 장에서는 이동 제스처를 사용하는 방법을 배웁니다. 이 기능은 스크롤하는 데 유용합니다(손가락이나 손을 사용해서 콘텐츠를 따라 스크롤). 또한 이동 제스처로 3D 개체 컬렉션 전체를 순환하거나 2D UI를 스크롤할 수도 있습니다. 이동 제스처를 사용하여 질감을 이동하는 방법을 알아보겠습니다. 3D 개체의 컬렉션을 이동하는 방법도 살펴봅니다.

1. 쿼드를 만듭니다. 기본 장면 계층 구조에서 마우스 오른쪽 단추를 클릭하고 "3D Object"를 선택한 수 "Quad"를 선택합니다.

![Lesson5 Chapter2 Step2im](images/Lesson5_chapter2_step2im.PNG)

2. 쿼드를 적절히 재배치합니다. 예를 들어, HoloLens 2에서 편리한 위치가 되도록 카메라에서 x = 0, y = 0, z = 1.5 위치를 설정합니다.

   > 참고: 쿼드가 이전 단원의 콘텐츠를 막는 경우(그 앞에 위치) 다른 개체를 차단하지 않도록 이동해야 합니다.

3. 쿼드에 재질을 적용합니다. 이 재질은 이동 제스처를 사용하여 스크롤하게 되는 재질입니다. 

![Lesson5 Chapter2 Step3im](images/Lesson5_chapter2_step3im.PNG)

4. 프로젝트 패널에서 검색 상자에 “pan content”를 입력합니다. 장면의 쿼드 위로 해당 재질을 끌어옵니다. 

> 참고: "Pan content" 재질은 MRTK에 포함되지 않으며 이전 단원에서 가져온 이 모듈의 자산 패키지에 있는 자산입니다. 

> 참고: 이동 콘텐츠를 추가하는 경우 늘어난 것처럼 보일 수 있습니다. 만족스러운 모양이 될 때까지 쿼드 크기의 x, y 및 z 값을 조정하여 이 문제를 해결할 수 있습니다.

이동 제스처를 사용하려면 개체에 충돌체(collider)가 필요합니다. 쿼드에 이미 메시 충돌체(collider)가 있는 것을 확인할 수 있습니다. 그러나 메시 충돌체(collider)는 너무 얇아서 선택하기 어려우므로 적합하지 않습니다. 메시 충돌체(collider)를 상자 충돌체(collider)와 바꾸는 것이 좋습니다.

5. 쿼드에 있는 메시 충돌체(collider)를 마우스 오른쪽 단추로 클릭하고(inspector 패널) "remove component"를 클릭하여 제거합니다. 
   ![Lesson5 Chapter2 Step5im](images/Lesson5_chapter2_step5im.PNG)

6. 이제 “add component”를 클릭하고 “box collider”를 검색하여 상자 충돌체(collider)를 추가합니다. 기본적으로 추가되는 상자 충돌체(collider)는 여전히 얇으므로 “edit collider” 단추를 클릭하여 편집합니다. 이 단추를 눌러 장면 편집기에서 x, y 및 z 값이나 요소를 사용하여 크기를 조정할 수 있습니다. 이 예제에서는 쿼드 약간 뒤로 상자 충돌체(collider)를 확장하려고 합니다. 장면 편집기에서 뒤쪽의 상자 충돌체(collider)를 바깥쪽으로 끕니다(아래 이미지 참조). 이렇게 하면 사용자는 손가락 뿐만 아니라 전체 손을 사용해서 스크롤할 수 있습니다. 
    ![Lesson5 Chapter2 Step6im](images/Lesson5_chapter2_step6im.PNG)
7. 대화형으로 만듭니다. 쿼드와 직접 상호 작용하려고 하므로 “near interaction touchable” 구성 요소를 사용하겠습니다(옥타에서 음악을 재생하기 위해 4단원에서도 이 작업을 수행함). 아래 이미지와 같이 "add component"를 클릭하고 "near interaction touchable"을 검색하여 선택합니다. 

8. 이동 제스처를 인식하는 기능을 추가합니다. "add component"를 클릭하고 "hand interaction pan"을 입력합니다. 손 레이(멀리에서 이동할 수 있음)과 집게 손가락 중에서 선택할 수 있습니다. 이 예제에서는 집게 손가락을 유지합니다. 
    ![Lesson5 Chapter2 Step7 8Im](images/Lesson5_chapter2_step7-8im.PNG)

![Lesson5 Chapter2 Step8im](images/Lesson5_chapter2_step8im.PNG)

9. hand interaction pan 스크립트에서 "lock horizontal" 및 "lock vertical" 확인란은 각각 해당 이동을 잠급니다. 질감 이동 설정을 사용하여 질감(질감 매핑)이 사용자의 이동 움직임을 따르게 합니다. 이 예제에서는 해당 확인란을 선택합니다. "velocity active" 옵션도 있습니다. 이 옵션을 선택 취소하면 이동 제스처가 작동하지 않습니다. 이 확인란도 선택합니다. 이제 이동 지원 쿼드가 생성됩니다.

   

   다음으로, 3D 개체를 이동하는 방법을 알아보겠습니다. 

10. 쿼드 개체를 마우스 오른쪽 단추로 클릭하고 3D 개체를 선택한 후 "cube"를 클릭합니다. 대략적으로 x = 0.1, y = 0.1 및 z = 0.1이 되도록 큐브 크기를 조정합니다. 해당 큐브를 3번 복사합니다(큐브를 마우스 오른쪽 단추로 클릭하고 duplicate를 누르거나 control/command D를 누름). 간격을 균일하게 유지합니다. 장면은 아래 그림과 유사해야 합니다.

![Lesson5 Chapter2 Step10im](images/Lesson5_chapter2_step10im.PNG)







11. 쿼드를 다시 선택하고 hand interaction pan 스크립트 아래에서 각 큐브에 대한 이동 작업을 설정하려고 합니다. "pan event receivers" 아래에서 이벤트를 수신할 개체의 수를 지정하려고 합니다. 큐브가 4개 있으므로 "4"를 입력하고 Enter 키를 누릅니다. 4개의 빈 필드가 표시됩니다.


![Lesson5 Chapter2 Step11im](images/Lesson5_chapter2_step11im.PNG)



12. 각 큐브를 비어 있는 각 슬롯으로 끕니다.
     ![Lesson5 Chapter2 Step12im](images/Lesson5_chapter2_step12im.PNG)
    
13. 모든 큐브에 "move with pan" 스크립트를 추가합니다. 이를 위해 control/command를 길게 누른 후 각 개체를 선택합니다. 그런 다음, inspector 패널에서 "add component"를 클릭하고 "move with pan"을 검색합니다. 해당 스크립트를 클릭하면 각 큐브에 추가됩니다. 이제 3D 개체가 이동 제스처를 사용하여 이동됩니다. 쿼드에서 메시 렌더를 제거하는 경우 3D 개체 목록을 따라 이동할 수 있는 위치에 보이지 않는 쿼드가 있습니다.

### <a name="eye-tracking"></a>시선 추적

이 장에서는 데모에서 시선 추적을 사용하도록 설정하는 방법을 알아봅니다. 시선 응시를 사용하여 응시할 경우 3D 메뉴 항목을 천천히 회전하게 됩니다. 또한 응시된 항목을 선택하면 재미있는 효과가 트리거됩니다.

1. Mixed Reality Toolkit 프로필이 제대로 구성되어 있는지 확인합니다. 이 문서를 작성할 때는 Mixed Reality Toolkit 프로필 구성에 기본적으로 시선 추적 기능이 포함되지 않았습니다. 시선 추적 기능을 추가하려면 [Mixed Reality Toolkit 설명서](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-the-mrtk-profiles-required-for-eye-tracking  )에 설명된 대로 “시선 추적에 필요한 MRTK 프로필 설정" 섹션의 지침을 따르세요. 위 설명서 링크의 나머지 단계에 따라 GazeProvider(카메라에 연결된 구성 요소)에서 시선 추적을 사용하도록 설정하고 Unity 편집기에서 시선 추적의 시뮬레이션을 사용하도록 설정하는 것을 포함하여 위의 설명서 링크의 나머지 단계를 수행하여 시선 추적이 적절히 구성되도록 합니다. 후속 버전의 MRTK에는 기본적으로 시선 추적이 포함될 수 있습니다.

    위의 링크에서는 다음에 대한 간단한 지침을 제공합니다.

    - MRTK 프로필에서 사용할 시선 응시 데이터 공급자 만들기
    - Gaze Provider에서 시선 추적을 사용하도록 설정
    - 편집기에서 시선 추적을 시뮬레이트하기 위한 설정
    - 빌드한 애플리케이션에서 시선 추적을 허용하도록 Visual Studio 솔루션 기능 편집

2. 대상 개체에 시선 추적 대상 구성 요소를 추가합니다. 개체가 시선 응시 이벤트에 대응하도록 하려면 각 개체에 시선 응시를 통해 상호 작용할 EyeTrackingTarget 구성 요소를 추가해야 합니다. 그리드 컬렉션에 속하는 9개의 3D 개체 각각에 이 구성 요소를 추가합니다. 팁: EyeTrackingTarget 구성 요소를 일괄로 추가하려면 계층 구조에서 여러 항목을 선택합니다.
    ![Lesson5 Chapter3 Step2](images/Lesson5Chapter3Step2.JPG)

3. 다음으로, 몇 가지 흥미로운 상호 작용을 위해 EyeTrackingTutorialDemo 스크립트를 추가합니다. EyeTrackingTutorialDemo 스크립트는 이 자습서 시리즈의 리포지토리 일부로 포함되며 기본적으로 Mixed Reality Toolkit에는 포함되지 않습니다. 그리드 컬렉션의 각 3D 개체에 대해 "Add Component" 메뉴에서 구성 요소를 검색하여 EyeTrackingTutorialDemo 스크립트를 추가합니다.
   ![Lesson5 Chapter3 Step3](images/Lesson5Chapter3Step3.JPG)

   4. 대상를 보고 있는 동안 개체가 회전합니다. 보고 있는 동안 3D 개체가 회전하도록 구성하려고 합니다. 이렇게 하려면 아래 이미지와 같이 EyeTrackingTarget 구성 요소의 "While Looking At Target" 섹션에 새 필드를 삽입합니다. 

![Lesson5 Chapter3 Step4a](images/Lesson5Chapter3Step4a.JPG)
![Lesson5 Chapter3 Step4b](images/Lesson5Chapter3Step4b.JPG)



새로 만든 필드에 현재 Game Object를 추가하고 아래 이미지와 같이 EyeTrackingTutorialDemo > RotateTarget()을 선택합니다. 이제 3D 개체는 시선 추적 시 응시될 때 회전하도록 구성되었습니다. 

5. 선택 시 응시되는 “대상 블립” 기능을 추가합니다(에어 탭 또는 "select"라고 말하기). 4단계와 마찬가지로, 아래 그림과 같이 EyeTrackingTarget 구성 요소의 Game Object "Select()" 필드에 할당하여 EyeTrackingTutorialDemo > BlipTarget()을 트리거하려고 합니다. 이제 이와 같이 구성되었으므로, 에어 탭 또는 음성 명령 “select”와 같은 선택 작업을 트리거할 때마다 게임 개체가 약간 블립됩니다. 
    ![Lesson5 Chapter3 Step5](images/Lesson5Chapter3Step5.JPG)
6. HoloLens 2로 빌드하기 전에 시선 추적 기능이 제대로 구성되었는지 확인합니다. 이 문서를 작성할 당시, Unity에서는 응시 입력(시선 추적) 기능을 설정할 수 없었습니다. HoloLens 2에서 시선 추적이 제대로 작동하려면 이 기능을 설정해야 합니다. 응시 입력 기능을 사용하도록 설정하려면 Mixed Reality Toolkit 설명서에서 다음 지침을 따르세요. https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2 


### <a name="congratulations"></a>축하합니다. 
애플리케이션에 기본적인 시선 추적 기능을 추가했습니다. 이러한 작업은 시선 추적 기능 활용의 시작에 불과합니다. 이 장의 마지막 단원인 5단원에서는 음성 명령, 이동 제스처 및 시선 추적과 같은 고급 입력 기능에 대해 알아보았습니다. 

[다음 단원: 달착륙선 어셈블리 샘플 환경](mrlearning-base-ch6.md)

