---
title: 자습서 시작-6. 고급 입력 옵션 탐색
description: 혼합 현실 애플리케이션에서 Azure 얼굴 인식을 구현하는 방법을 알아보려면 이 과정을 완료합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, Hololens
ms.openlocfilehash: 75a14697953026474d8ca00e6473145d7b12a482
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334357"
---
# <a name="6-exploring-advanced-input-options"></a>6. 고급 입력 옵션 탐색

이 자습서에서는 음성 명령, 패닝 제스처 및 눈 추적 사용을 포함 하 여 HoloLens 2에 대 한 몇 가지 고급 입력 옵션을 살펴봅니다. 

## <a name="objectives"></a>목표

- 음성 명령 및 키워드를 사용 하 여 이벤트 트리거
- 추적 된 손을 사용 하 여 추적 된 손으로 텍스처 및 3D 개체를 이동 합니다.
- HoloLens 2 눈동자 추적 기능을 활용 하 여 개체 선택

## <a name="enabling-voice-commands"></a>음성 명령 사용

이 섹션에는 두 개의 음성 명령이 구현 되어 있습니다. 먼저 "진단 설정/해제"를 말하여 프레임 주기 진단 패널을 전환 하는 기능이 도입 되었습니다. 둘째, 음성 명령으로 소리를 재생 하는 기능을 탐색 합니다. 음성 명령 구성을 담당 하는 MRTK 프로필 및 설정이 먼저 검토 됩니다.

1. BaseScene 계층 구조에서 MixedRealityToolkit을 선택 합니다. 그런 다음 검사기 패널에서 입력을 선택 하 고 DefaultMixedRealityInputSystemProfile 왼쪽의 작은 복제 단추를 클릭 하 여 프로필 복제 팝업을 엽니다. 팝업에서 복제를 클릭 하 여 새 프로필 MixedRealityInputSystemProfile를 만듭니다.

    ![mrlearning-base-ch5-1-step1a](images/mrlearning-base-ch5-1-step1a.png)

    그러면 새로 만든 MixedRealityInputSystemProfile로 MixedRealityToolkitConfigurationProfile 자동으로 채워집니다.

    ![mrlearning-base-ch5-1-step1b](images/mrlearning-base-ch5-1-step1b.png)

2. 입력 시스템 프로필에는 다양 한 설정이 있습니다. 음성 명령의 경우 음성 섹션을 확장 하 고 이전 단계와 동일한 프로세스를 수행 하 여 DefaultMixedRealitySpeechCommandsProfile를 복제 하 고 편집 가능한 고유한 복사본으로 대체 합니다.

    ![mrlearning-base-ch5-1-step2](images/mrlearning-base-ch5-1-step2.png)

    음성 명령 프로필에서 설정 범위를 확인할 수 있습니다. 이러한 설정에 대 한 자세한 내용은 [Mrtk speech 설명서](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>)를 참조 하세요.

    기본적으로 일반 동작은 자동 시작입니다. 원하는 경우 수동 시작으로 변경할 수 있습니다. 그러나이 예에서는이를 자동 시작으로 유지 합니다. MRTK는 메뉴, 진단 설정/해제, 프로파일러 전환 등의 몇 가지 기본 음성 명령과 함께 제공 됩니다. 진단 프레임 속도 카운터를 설정 및 해제 하기 위해 "진단 설정/해제" 키워드를 사용 합니다. 또한 아래 단계에서는 새 음성 명령을 추가합니다.

3. 새 음성 명령을 추가합니다. 이렇게 하려면 + 새 음성 추가 명령 단추를 클릭 합니다. 기존 음성 명령 목록 아래에 새 줄이 표시 됩니다. 사용할 음성 명령을 입력 합니다. 이 예제에서는 "음악 재생" 명령을 사용 합니다.

    ![mrlearning-base-ch5-1-step3](images/mrlearning-base-ch5-1-step3.png)

    >[!NOTE]
    >또한 음성 명령의 키코드도 설정할 수 있습니다. 그러면 음성 명령이 키보드 키를 누를 때 이벤트를 트리거할 수 있습니다.

4. 음성 명령에 응답하는 기능을 추가합니다. BaseScene 계층에서 다른 입력 스크립트가 연결 되지 않은 개체 (예: MixedRealityPlayspace game 개체)를 선택 합니다. 검사기 패널에서 구성 요소 추가를 클릭 하 고, "speech"를 검색 하 고, 음성 입력 처리기 스크립트를 선택 합니다.

    ![mrlearning-base-ch5-1-step4](images/mrlearning-base-ch5-1-step4.png)

    기본적으로 두 개의 확인란이 표시 됩니다. 하나는 포커스 필요 확인란입니다. 따라서 광선-응시, 헤드-응시, 컨트롤러-응시 또는 핸드 응시를 사용 하 여 개체를 가리키면 음성 명령이 트리거됩니다. 사용자가 개체를 확인 하 여 음성 명령을 사용할 필요가 없도록 하려면이 확인란의 선택을 취소 합니다.

5. 음성 명령에 응답하는 기능을 추가합니다. 이렇게 하려면 음성 입력 처리기에 있는 + 단추를 클릭 합니다.

    ![mrlearning-base-ch5-1-step5](images/mrlearning-base-ch5-1-step5.png)

6. 키워드 옆에 드롭다운 메뉴가 표시 됩니다. 사용자에 게 "진단 설정/해제" 라는 구가 표시 될 때마다 작업을 트리거하면 진단 설정/해제를 선택 합니다. 옆의 화살표를 눌러 요소 0을 확장 해야 할 수도 있습니다.

    ![mrlearning-base-ch5-1-step6](images/mrlearning-base-ch5-1-step6.png)

    >[!NOTE]
    >이러한 키워드는 3 단계에서 편집한 프로필을 기반으로 채워집니다.

7. 진단 시스템 음성 컨트롤 스크립트를 추가 하 여 프레임 속도 카운터 진단을 설정/해제 합니다. 이렇게 하려면 구성 요소 추가를 누르고 진단 시스템 음성 컨트롤 스크립트를 검색 한 다음 메뉴에서 추가 합니다. 이 스크립트를 어떤 개체에도 추가할 수 있지만 편의상, 음성 입력 처리기와 동일한 개체에 추가합니다.

    ![mrlearning-base-ch5-1-step7](images/mrlearning-base-ch5-1-step7.png)

8. 음성 입력 처리기에 새 응답을 추가 합니다. 이렇게 하려면 "+" 아이콘을 클릭 하 여 응답 목록에 새 응답을 추가 합니다.

    ![mrlearning-base-ch5-1-step8](images/mrlearning-base-ch5-1-step8.png)

9. 진단 시스템 음성 컨트롤 스크립트를 포함 하는 개체를 이전 단계에서 방금 만든 새 응답으로 끕니다.

    ![mrlearning-base-ch5-1-step9](images/mrlearning-base-ch5-1-step9.png)

10. 함수 드롭다운 (함수 없음), 진단 시스템 음성 컨트롤을 차례로 클릭 하 고 진단을 설정/해제 하는 ToggleDiagnostics () 함수를 선택 합니다.

    ![mrlearning-base-ch5-1-step10](images/mrlearning-base-ch5-1-step10.png)

    >[!IMPORTANT]
    > 장치를 빌드하기 전에 mic 설정을 사용 하도록 설정 해야 합니다. 이렇게 하려면 파일을 클릭 하 고 빌드 설정, 플레이어 설정으로 이동 하 여 마이크 기능이 설정 되어 있는지 확인 합니다.

    다음으로, Octa 개체를 사용 하 여 음성 명령에서 오디오 파일을 재생 하는 기능을 추가 합니다. [4 단원](mrlearning-base-ch4.md) 에서 Octa 개체를 터치 하 여 오디오 클립을 재생 하는 기능이 추가 되었습니다. 음악 음성 명령에 대해서도 이 동일한 오디오 원본을 활용합니다.

11. BaseScene 계층 구조에서 Octa 개체를 선택 합니다.

12. Octa 개체를 사용 하 여 다른 음성 입력 처리기를 추가 합니다 (4 단계와 5 단계 반복).

13. 6 단계에서 진단 음성 전환 명령을 추가 하는 대신 아래 이미지에 표시 된 것 처럼 음악 재생 음성 명령을 추가 합니다.

    ![mrlearning-base-ch5-1-step13](images/mrlearning-base-ch5-1-step13.png)

14. 8 단계와 9 단계에서와 같이 새 응답을 추가 하 고 Octa 개체, 진단 시스템의 Voice Controls 스크립트를 포함 하는 개체를 빈 응답 슬롯으로 끕니다.

15. 함수 없음 이라는 드롭다운 메뉴를 선택 합니다. 그런 다음 오디오 원본과 PlayOneShot (오디오 클립)를 차례로 선택 합니다.

    ![Lesson5 Chapter1 Step15im](images/Lesson5_chapter1_step15im.PNG)

16. 이 예에서는 [4 단원](mrlearning-base-ch4.md)에서와 동일한 오디오 클립을 사용 합니다. 프로젝트 패널로 이동 하 여 "MRTK_Gem" 오디오 클립을 검색 하 고 아래 이미지에 표시 된 것 처럼 오디오 원본 슬롯으로 끕니다. 이제 응용 프로그램은 "진단 설정/해제" 음성 명령에 응답 하 여 프레임 전송률 카운터 패널을 전환 하 고 음악을 재생 하 여 MRTK_Gem 노래를 재생 합니다.

    ![Lesson5 Chapter1.txt Step16im](images/Lesson5_chapter1_step16im.PNG)

## <a name="the-pan-gesture"></a>이동 제스처

이 섹션에서는 이동 제스처를 사용 하는 방법을 배웁니다. 이 기능은 손가락 또는 손 모양으로 스크롤 하 여 콘텐츠를 스크롤 하는 데 유용 합니다. 이동 제스처를 사용 하 여 개체를 회전 하거나, 3D 개체의 컬렉션을 순환 하거나, 2D UI를 스크롤할 수도 있습니다.

1. 쿼드를 만듭니다. BaseScene 계층 구조에서를 마우스 오른쪽 단추로 클릭 하 고 "3D 개체"를 선택한 다음 4를 선택 합니다.

    ![Lesson5 Chapter2 Step2im](images/Lesson5_chapter2_step2im.PNG)

2. 필요에 따라 쿼드의 위치를 변경 합니다. 이 예에서는 HoloLens 2에서 편안 하 게 배치 하기 위해 카메라에서 x = 0, y = 0 및 z = 1.5을 설정 합니다.

    >[!NOTE]
    >이전 단원에서 4 개의 블록이 나 이전 단원에서 가져온 내용 앞에 있는 경우 다른 개체를 차단 하지 않도록 이동 해야 합니다.

3. 쿼드에 재질을 적용합니다. 이 자료는 이동 제스처로 스크롤할 것입니다.

    ![Lesson5 Chapter2 Step3im](images/Lesson5_chapter2_step3im.PNG)

4. 프로젝트 패널에서 검색 상자에 "이동 콘텐츠"를 입력 합니다. 해당 자료를 장면에서 쿼드로 끌어 놓습니다.

    >[!NOTE]
    >이 판 콘텐츠 자료는 MRTK의 일부가 아니지만 이전 단원에서 가져온 BaseModuleAssets 자산에 포함 되어 있습니다.

    이동 제스처를 사용하려면 개체에 충돌체(collider)가 필요합니다. 쿼드에 이미 메시 충돌체(collider)가 있는 것을 확인할 수 있습니다. 그러나 메시 충돌체(collider)는 너무 얇아서 선택하기 어려우므로 적합하지 않습니다. 메시 충돌체(collider)를 상자 충돌체(collider)와 바꾸는 것이 좋습니다.

5. 검사기 패널에서 쿼드에 있는 메시 collider를 마우스 오른쪽 단추로 클릭 합니다. 그런 다음 구성 요소 제거를 클릭 하 여 제거 합니다.

    ![Lesson5 Chapter2 Step5im](images/Lesson5_chapter2_step5im.PNG)

6. 이제 구성 요소 추가를 클릭 하 고 "box collider"를 검색 하 여 상자 collider를 추가 합니다. 기본 추가 된 상자 collider는 여전히 너무 씬 이므로 클릭 하 여 편집 하려면 Collider 단추를 클릭 합니다. 이 단추를 눌러 장면 편집기에서 x, y 및 z 값이나 요소를 사용하여 크기를 조정할 수 있습니다. 이 예제에서는 쿼드 약간 뒤로 상자 충돌체(collider)를 확장하려고 합니다. 장면 편집기에서 뒤쪽의 상자 충돌체(collider)를 바깥쪽으로 끕니다(아래 이미지 참조). 이렇게 하면 사용자가 손가락을 사용할 수 있을 뿐 아니라 스크롤 하는 데 사용할 수 있습니다.

    ![Lesson5 Chapter2 Step6im](images/Lesson5_chapter2_step6im.PNG)

7. 대화형으로 만듭니다. 쿼드와 직접 상호 작용 하려고 하므로 4 단원에서 사용 했던 거의 상호 작용 Touchable 구성 요소를 사용 하 여 Octa 개체에서 음악을 재생 하려고 합니다. 구성 요소 추가를 클릭 하 고, "near 인터랙션 touchable"를 검색 하 여 아래 이미지에 표시 된 것 처럼 선택 합니다.

    ![mrlearning-base-ch5-2-step7a](images/mrlearning-base-ch5-2-step7a.png)

    상자 Collider의 크기 및/또는 가운데와 일치 하지 않는 범위 및/또는 가운데에 대 한 노란색 경고가 표시 되 면 범위 고정 및/또는 수정 센터 단추를 클릭 하 여 중심과 범위 값을 업데이트 합니다.

    ![mrlearning-base-ch5-2-step7b](images/mrlearning-base-ch5-2-step7b.png)

8. 이동 제스처를 인식하는 기능을 추가합니다. 구성 요소 추가를 클릭 하 고 검색 필드에 "직접 상호 작용"을 입력 한 다음 직접 상호 작용 팬 확대/축소 스크립트 구성 요소를 추가 합니다.

    ![mrlearning-base-ch5-2-step8a](images/mrlearning-base-ch5-2-step8a.png)

    그리고이를 사용 하는 경우에는 팬 사용 쿼드를 사용 합니다.

    여기에서 볼 수 있듯이 수동 상호 작용 이동 확대/축소 스크립트 구성 요소에는 다양 한 설정이 포함 되어 있습니다 (선택 사항).

    ![mrlearning-base-ch5-2-step8b](images/mrlearning-base-ch5-2-step8b.png)

9. 다음으로, 3D 개체를 이동하는 방법을 알아보겠습니다.

    계층에서 4 개의 개체를 마우스 오른쪽 단추로 클릭 하 여 상황별 팝업 메뉴를 열고 **3D 개체** > **큐브** 를 선택 하 여 장면에 큐브를 추가 합니다.

    큐브의 **위치가** _0, 0, 0_ 으로 설정 되어 있는지 확인 합니다 .이는 쿼드에서 깔끔하게 배치 됩니다. 큐브를 _0.1, 0.1, 0.1_의 **배율로** 축소 합니다.

    ![mrlearning-base-ch5-2-step9](images/mrlearning-base-ch5-2-step9.png)

    큐브를 마우스 오른쪽 단추로 클릭 하 여 큐브를 세 번 복제 하 고, 상황별 팝업 메뉴를 열고, **복제**를 선택 합니다.

    큐브를 균등 하 게 분할 합니다. 장면이 아래 이미지와 유사 하 게 표시 됩니다.

10. CTRL 키를 누른 채 계층 패널에서 각 **큐브** 개체를 선택 하 여 모든 큐브에 MoveWithPan 스크립트를 추가 합니다. 검사기 패널에서 구성 요소 추가를 클릭 하 고, 이동 하 여 **이동** 스크립트를 검색 하 고 선택 하 여 모든 큐브에 추가 합니다.

    ![mrlearning-base-ch5-2-step10a](images/mrlearning-base-ch5-2-step10a.png)

    >[!NOTE]
    >MoveWithPan 스크립트는 MRTK의 일부가 아니지만 이전 단원에서 가져온 BaseModuleAssets 자산에 포함 되어 있습니다.

    큐브를 선택한 상태에서 계층 패널의 **네** 번째 개체를 이동 **하 여 이동** 스크립트 구성 요소의 이동 **입력 원본** 필드로 끕니다.

    ![mrlearning-base-ch5-2-step10b](images/mrlearning-base-ch5-2-step10b.png)

    이제 큐브는 이동 제스처로 이동 합니다.

    >[!TIP]
    >각 큐브의 MoveWithPan 인스턴스는 각 큐브의 이동 입력 원본 필드에 추가 되 고 해당 큐브 개체의 위치를 적절 하 게 업데이트 하는 쿼드 개체의 HandInteractionPanZoom 인스턴스에서 보낸가 중 업데이트 된 이벤트를 수신 합니다.

    큐브를 선택한 상태에서 z 축을 따라 앞으로 이동 하면 **z** 값을 _0.7_로 변경 하 여 각 큐브의 메쉬가 **4** **상자 Collider** 안에 있습니다.

    ![mrlearning-base-ch5-2-step10c](images/mrlearning-base-ch5-2-step10c.png)

    이제 검사기 패널에서 검사를 취소 하 여 **쿼드**의 **메시 렌더러** 구성 요소를 사용 하지 않도록 설정 하면 3d 개체 목록을 통해 이동할 수 있는 보이지 않는 쿼드이 표시 됩니다.

    ![mrlearning-base-ch5-2-step10d](images/mrlearning-base-ch5-2-step10d.png)

## <a name="eye-tracking"></a>시선 추적

이 섹션에서는 데모에서 눈 추적을 사용 하도록 설정 하는 방법에 대해 설명 합니다. 눈에 gazed 때 3D 메뉴 항목을 천천히 회전 하 게 됩니다. 또한 응시된 항목을 선택하면 재미있는 효과가 트리거됩니다.

1. 아이 추적에 대해 MRTK 프로필이 제대로 구성 되어 있는지 확인 합니다. 이렇게 하려면 [MRTK의 눈동자 추적 시작](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) 지침으로 이동 하 여 눈동자 추적 [설정 단계별](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-eye-tracking-step-by-step) 섹션의 단계를 검토 하 여 눈동자 추적이 제대로 구성 되어 있는지 확인 합니다. 설명서의 나머지 단계를 완료 합니다.

    >[!NOTE]
    >[혼합 현실 도구 키트 구성](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1#configure-the-mixed-reality-toolkit) 단원에 설명 된 대로 DefaultHoloLens2InputSystemProfile를 사용 하 여 사용자 지정 MRTK 구성 프로필을 복제 하는 경우 unity 프로젝트에서 기본적으로 눈 추적을 사용 하도록 설정 하지만 unity 편집기에 대 한 눈 추적 시뮬레이션을 설정 하 고 빌드에 대 한 시각 추적을 허용 하도록 Visual Studio를 구성 해야 합니다.

    위의 링크에서는 다음에 대한 간단한 지침을 제공합니다.

    - MRTK 프로필에서 사용할 Windows Mixed Reality 눈동자 응시 Data Provider 만들기
    - 카메라에 연결 된 응시 공급자에서 눈 추적 사용
    - Unity 편집기에서 눈 추적 시뮬레이션 설정
    - 빌드한 애플리케이션에서 시선 추적을 허용하도록 Visual Studio 솔루션 기능 편집

2. 대상 개체에 시선 추적 대상 구성 요소를 추가합니다. 개체가 눈동자 응시 이벤트에 응답할 수 있도록 하려면 눈에 EyeTrackingTarget 구성 요소를 사용 하 여 상호 작용 하려는 각 개체에 대 한 작업을 수행 해야 합니다. 그리드 컬렉션에 속하는 9개의 3D 개체 각각에 이 구성 요소를 추가합니다.

    >[!TIP]
    >Shift 및/또는 CTRL 키를 사용 하 여 계층에서 여러 항목을 선택한 다음 EyeTrackingTarget 구성 요소를 대량 추가할 수 있습니다.

    ![Lesson5 Chapter3 2 단계](images/Lesson5Chapter3Step2.JPG)

3. 다음에는 몇 가지 흥미로운 상호 작용을 위해 EyeTrackingTutorialDemo 스크립트를 추가 합니다. 그리드 컬렉션의 각 3D 개체에 대해 구성 요소 추가 메뉴에서 구성 요소를 검색 하 여 EyeTrackingTutorialDemo 스크립트를 추가 합니다.

    ![Lesson5 Chapter3 3 단계](images/Lesson5Chapter3Step3.JPG)

    >[!NOTE]
    >EyeTrackingTutorialDemo 스크립트 자료는 MRTK의 일부가 아니지만 이전 단원에서 가져온 BaseModuleAssets 자산에 포함 되어 있습니다.

4. 대상를 보고 있는 동안 개체가 회전합니다. 3D 개체를 확인 하는 동안 회전 하도록 구성 하려고 합니다. 이렇게 하려면 아래 이미지에 표시 된 것 처럼 EyeTrackingTarget 구성 요소의 Target ()을 찾는 중 () 섹션에 새 필드를 삽입 합니다.

    ![Lesson5 Chapter3 Step4a](images/Lesson5Chapter3Step4a.JPG)

    아래 이미지에 표시 된 것 처럼 새로 만든 필드에서 빈 필드에 현재 게임 개체를 추가 하 고 EyeTrackingTutorialDemo > RotateTarget ()를 선택 합니다. 이제 3D 개체는 시선 추적 시 응시될 때 회전하도록 구성되었습니다.

    ![Lesson5 Chapter3 Step4b](images/Lesson5Chapter3Step4b.JPG)

5. Gazed 하는 기능을 "선택" 하는 기능을 추가 하 여 선택 합니다. 4 단계와 마찬가지로 아래 그림에 표시 된 것 처럼 EyeTrackingTarget 구성 요소의 game 개체의 Select () 필드에 할당 하 여 EyeTrackingTutorialDemo > BlipTarget ()를 트리거해야 합니다. 이제 구성 된 상태에서 선택 작업 (예: 공중 탭 또는 음성 명령 "선택")을 트리거할 때마다 게임 개체가 약간 나는 것을 알 수 있습니다.

    ![Lesson5 Chapter3 5 단계](images/Lesson5Chapter3Step5.JPG)

6. HoloLens 2로 빌드하기 전에 시선 추적 기능이 제대로 구성되었는지 확인합니다. 이 문서를 작성할 당시에는 Unity에 눈길 추적 기능에 대 한 응시 입력을 설정 하는 기능이 아직 없습니다. 이 기능을 설정 하는 것은 HoloLens 2에서의 아이 추적이 작동 하는 데 필요 합니다. [HoloLens 2 지침에서 Unity 앱 테스트](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) 를 수행 하 여 응시 입력 기능을 사용 하도록 설정 합니다.

## <a name="congratulations"></a>축하합니다.

응용 프로그램에 기본 눈 추적 기능을 추가 했습니다. 이러한 작업은 시선 추적 기능 활용의 시작에 불과합니다. 이 장에서는 음성 명령, 패닝 제스처 및 눈 추적 등 고급 입력 기능에 대해 배운 5 단원도 마무리 합니다.

[다음 단원: 7. 음력 모듈 샘플 응용 프로그램 만들기](mrlearning-base-ch6.md)
