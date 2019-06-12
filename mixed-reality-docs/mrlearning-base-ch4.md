---
title: MR 학습 기본 모듈 - 3D 개체 조작
description: 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 알아보려면 이 과정을 완료합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 45e772de0825fe2161f880a165d6c75c755b849e
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2019
ms.locfileid: "65730903"
---
# <a name="mr-learning-base-module---3d-object-interaction"></a>MR 학습 기본 모듈 - 3D 개체 조작

이 단원에서는 기본 3D 콘텐츠 및 사용자 환경을 살펴봅니다. 3D 개체를 컬렉션의 일부로 구성하고, 기본 조작을 위한 경계 상자에 대해 알아보고, 근거리 및 원거리 조작에 대해 배우고, 손 추적을 사용한 터치 및 잡기 제스처에 대해 알아봅니다. 

## <a name="objectives"></a>목표

* MRTK의 그리드 개체 컬렉션을 사용하여 3D 콘텐츠를 구성하는 방법 알아보기
* 경계 상자 구현
* 기본 조작(이동, 회전 및 크기 조정)을 위한 3D 개체 구성
* 근거리 및 원거리 조작 살펴보기
* 잡기 및 터치와 같은 추가 손 추적 제스처 알아보기

## <a name="instructions"></a>지침

### <a name="organizing-3d-objects-in-a-collection"></a>컬렉션에서 3D 개체 구성

1. 계층을 마우스 오른쪽 단추로 클릭하고 “빈 항목 만들기”를 선택합니다. 그러면 빈 게임 개체가 만들어집니다. 이름을 “3DObjectCollection”으로 변경합니다. 여기에 모든 3D 개체를 배치합니다. 컬렉션의 위치를 x = 0, y = 0 및 z = 0에 설정해야 합니다.

![Lesson4 Chapter1 Step1im](images/Lesson4_Chapter1_step1im.PNG)

2. [Lesson1](mrlearning-base-ch1.md)에 간략히 나온 사용자 지정 패키지를 가져오기 위한 동일한 지침을 사용하여 BaseModule 자산을 가져옵니다. BaseModule 자산에는 이 자습서에 사용될 3D 모듈과 기타 유용한 스크립트가 포함됩니다. BaseModule 통합 패키지는 <https://github.com/Microsoft/MixedRealityLearning/releases/tag/V1.1>에서 찾을 수 있습니다.

3. 커피 컵 프리팹은 옆에 파란색 큐브로 구성할 수 있습니다. 파란색 큐브와 흰색 작은 컵이 있는 커피 컵(프리팹이 아닌 원래 3D 모델을 의미함)은 선택하지 마세요. 

![Lesson4 Chapter1 Noteaim](images/Lesson4_chapter1_noteaim.PNG)

4. 선택한 커피 컵 프리팹을 1단계의 “3DObjectCollection” 게임 개체로 끕니다. 이제 커피 컵이 컬렉션의 자식이 됩니다.

![Lesson4 Chapter1 Step4ima](images/Lesson4_chapter1_step4ima.PNG)

5. 다음으로, 더 많은 3D 개체를 장면에 추가합니다. 아래는 이 예제에서 추가할 개체들의 목록입니다. 개체를 추가하면 다양한 크기로 장면에 나타나는 것을 확인할 수 있습니다. 관리자 패널의 변환 설정 아래에서 각 3D 모델의 배율을 조정합니다. 이 예제에서 권장되는 조정은 아래 개체를 사용하여 나열됩니다. 프로젝트 패널의 검색 상자에서 이러한 단어를 검색하고 이전 단계와 마찬가지로 3D 개체 프리팹을 “3DObjectCollection” 개체로 끕니다. 자산>BaseModuleAssets>기본 모듈 프리팹에서 이러한 프리팹 컬렉션을 찾을 수 있습니다.
- “TheModule_BaseModuleIncomplete”를 검색합니다. 장면으로 끕니다. 배율을 x = 0.03, y = 0.03, z = 0.03으로 설정합니다. 
- “Octa_BaseModuleIncomplete”를 검색합니다. 장면으로 끕니다. 배율을 x = 0.13, y = 0.13, z =0.13으로 설정합니다.
- “EarthCore_BaseModuleIncomplete”를 검색합니다. 장면으로 끕니다. 배율을 x = 50.0 y = 50.0, z = 50.0으로 설정합니다.
- “Cheese_BaseModuleIncomplete”를 검색합니다. 장면으로 끕니다. 배율을 x = 0.05, y = 0.05, z = 0.05로 설정합니다.
- “Model_Platonic_BaseModuleIncomplete”를 검색합니다. 장면으로 끕니다. 배율을 x = 0.13, y = 0.13, z = 0.13으로 설정합니다.
- “CoffeeCup_BaseModuleIncomplete”를 검색합니다. 장면으로 끕니다.

![Lesson4 Chapter1 Step5im](images/Lesson4_Chapter1_step5im.PNG)

6. 장면에 3개의 큐브를 추가합니다. “3DObjectCollection” 개체를 마우스 오른쪽 단추로 클릭하고 “3D 개체”를 선택한 다음, “큐브”를 선택합니다. 배율을 x = 0.14, y = 0.14 및 z = 0.14로 설정합니다. 이 단계를 2번 더 반복하여 총 3개의 큐브를 만듭니다. 또는 큐브를 두 번 복제하여 총 3개의 큐브를 만들 수 있습니다. 또한 자산>BaseModuleAssets>기본 모듈 프리팹에서 세 개의 준비된 큐브 프리팹을 선택하고, GreenCube_BaseModuleIncomplete, BlueCube_BaseModuleIncomplete 및 OrangeCube_BaseModuleIncomplete를 선택할 수 있습니다.

![Lesson4 Chapter1 Step6im](images/Lesson4_Chapter1_step6im.PNG)

7. 개체의 컬렉션을 구성하여 MRTK의 그리드 개체 컬렉션을 사용하는 [2단원](mrlearning-base-ch2.md)에 설명된 절차를 통해 그리드를 구성합니다. 3x3 그리드에서 개체를 구성하는 예제를 보려면 아래 이미지를 참조하세요.

![Lesson4 Chapter1 Notebim](images/Lesson4_chapter1_notebim.PNG)

>참고: 위 이미지의 개체와 같이 일부 개체가 중앙에 있지 않을 수 있습니다. 이는 프리팹 또는 개체에 정렬되지 않은 자식 개체가 있기 때문입니다. 자유롭게 개체 위치 또는 자식 개체 위치를 조정하여 잘 정렬된 그리드를 만들 수 있습니다.


### <a name="manipulating-3d-objects"></a>3D 개체 조작
1. 큐브를 조작하는 기능을 추가합니다. 3D 개체를 조작하는 기능을 추가하려면 다음을 수행해야 합니다.
-   계층에서 조작하려는 3D 개체를 선택합니다(이 예제에서 큐브 중 하나).
-   “구성 요소 추가”를 클릭합니다. 
-   “조작”을 검색합니다.
-   “조작 처리기”를 선택합니다.
-   “3DObjectCollection” 자체가 아닌 “3DObjectCollection” 개체 아래에 있는 모든 3D 개체에 대해 반복합니다.
-   모든 3D 개체에 충돌체(collider) 또는 상자 충돌체가 있는지 확인합니다(구성 요소 추가 > 상자 충돌체).

![Lesson4 Chapter2 Step1im](images/Lesson4_chapter2_step1im.PNG)

>조작 처리기는 조작 시 개체의 동작에 대한 설정을 사용자가 조정할 수 있도록 하는 구성 요소입니다. 여기에는 특정 축에 대한 회전, 크기 조정, 이동 및 이동 제한이 포함됩니다. 

2. 확장만 가능하도록 큐브 하나를 제한합니다. “3DObjectCollection” 개체에서 큐브를 하나 선택합니다. 검사기 패널에서 “두 개의 조작 유형” 옆에 있는 드롭다운 메뉴를 클릭하고 “배율”을 선택합니다. 이렇게 하면 사용자가 큐브의 크기만 변경할 수 있습니다.

![Lesson4 Chapter2 Step2im](images/Lesson4_Chapter2_step2im.PNG)

3. 서로 구별할 수 있도록 각 큐브의 색을 변경합니다. 
-   프로젝트 패널로 이동하고 “MixedRealityToolkit.SDK”가 표시될 때까지 아래로 스크롤한 다음, 선택합니다.
-   “표준 자산” 폴더를 선택합니다.
-   “재료” 폴더를 클릭합니다.
-   각 큐브에 다른 재료를 끕니다. 

>참고: 큐브에 대한 색을 선택할 수 있습니다. 예를 들어 “glowingcyan”, “glowingorange” 및 “green”을 사용하겠습니다. 자유롭게 다른 색을 시도해 보세요. 색을 큐브에 추가하려면 색을 변경할 큐브를 클릭한 다음, 재료를 큐브의 검사기 패널에 있는 메시 렌더러의 재료 필드로 끕니다. 

![Lesson4 Chapter2 Step3im](images/Lesson4_Chapter2_step3im.PNG)

4. “3DObjectCollection” 개체에서 다른 큐브를 선택하고 해당 큐브의 이동이 헤드로부터 거리 고정으로 제한되도록 합니다. 이렇게 하려면 “이동에 대한 제약 조건”의 오른쪽에서 드롭다운 메뉴를 클릭하고 “헤드로부터 거리 고정”을 선택합니다. 그러면 사용자가 큐브를 가시 범위 내에서만 움직일 수 있게 됩니다. 

![Lesson4 Chapter2 Step4im](images/Lesson4_chapter2_step4im.PNG)

다음 몇 단계의 목표: 3D 개체를 사용하여 잡기 및 조작을 사용하도록 설정합니다. 다양한 조작 설정을 적용합니다. 

5. 치즈 개체를 선택하고 검사기 창에서 “구성 요소 추가”를 클릭합니다. 

6. 검색 상자에 “근거리 잡기형 상호 작용(Near Interaction Grabbable)”을 검색하고 스크립트를 선택합니다. 이 구성 요소를 사용하면 사용자가 추적된 손을 사용하여 개체에 접근하여 잡을 수 있습니다. 또한 “원거리 조작 허용” 확인란이 선택 해제되어 있지 않는 한, 멀리서 개체를 조작할 수도 있습니다(아래 이미지에 녹색 원으로 표시).

![Lesson4 Chapter2 Step6im](images/Lesson4_Chapter2_step6im.PNG)

7. 해당 개체에서 5~6단계를 반복하여 “근거리 잡기형 상호 작용”을 Octa 개체, Platonic 개체, 지구 코어, 달 착륙선 및 커피 컵에 추가합니다.

8. Octa 개체에서 원거리 조작 기능을 제거합니다. 이렇게 하려면 계층에서 Octa를 선택하고 “원거리 조작 허용” 확인란(녹색 원으로 표시)을 선택 취소합니다. 그러면 사용자가 추적된 손을 사용하여 직접 Octa와 상호 작용할 수 있습니다.

>참고: 조작 처리기 구성 요소 및 관련된 설정에 대한 전체 설명은 [MRTK 설명서](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)를 참조하세요.

9. “근거리 잡기형 상호 작용” 구성 요소가 지구 코어, 달 착륙선 및 커피 컵에 추가되었는지 확인합니다(7단계 참조).

10. 달 착륙선의 경우 아래 이미지에 표시된 것처럼 근거리 및 원거리 상호 작용 모두에 대해 개체의 중심을 회전하도록 조작 처리기 설정을 변경합니다.

![Lesson4 Chapter2 Step10im](images/Lesson4_chapter2_step10im.PNG)

11: 지구 코어의 경우 릴리스 동작을 “없음”으로 변경합니다. 그러면 사용자가 지구 코어를 잡았다가 놓은 후에는 더이상 움직이지 않습니다. 

![Lesson4 Chapter2 Step11im](images/Lesson4_Chapter2_step11im.PNG)

> 참고: 이 설정은 던질 수 있는 공 만들기와 같은 시나리오에 유용합니다. 속도와 각속도를 유지하면 공을 놓고 난 후에 놓을 때의 속도로 계속 움직이게 되는데, 이는 물리적 공의 동작 방식과 유사합니다.

### <a name="adding-bounding-boxes"></a>경계 상자 추가
경계 상자는 직접 조작(근거리 상호 작용) 및 광선 기반 조작(원거리 상호 작용) 모두에서 한 손으로 개체를 더 쉽고 더 직관적으로 조작할 수 있도록 합니다. 경계 상자는 특정 축을 기준으로 개체를 크기 조정 및 회전하기 위해 잡을 수 있는 “핸들”을 제공합니다.
>참고: 경계 상자를 개체에 추가하려면 먼저 개체에 충돌체가 있어야 합니다(예: 상자 충돌체). 이 단원에서 이전에 수행한 것처럼 충돌체는 개체를 선택하고 개체의 검사 패널에서 구성 요소 추가>박스 충돌체를 선택하여 추가할 수 있습니다.
>

1. 아직 없는 경우 지구 코어 개체에 상자 충돌체를 추가합니다(제공된 지침마다 기본 모듈 자산 폴더에 제공된 프리팹을 사용할 경우 상자 충돌체 및 설정이 필요하지 않음). 지구 코어의 경우 아래 이미지에 표시된 대로 상자 충돌체를 지구 코어 밑에 있는 “node_id30” 개체에 추가해야 합니다. node_id30을 선택하고 개체의 검사기 탭에서 “구성 요소 추가”를 클릭하고 “상자 충돌체”를 검색합니다. 

![Lesson4 Chapter3 Step1im](images/Lesson4_Chapter3_step1im.PNG)

![Lesson4 Chapter3 Step2im](images/Lesson4_chapter3_step2im.PNG)

> 참고: 상자 충돌체를 시각화하여 너무 크거나 너무 작지 않도록 해야 합니다. 둘러싸고 있는 개체(이 예제에서는 지구 코어)와 대략 동일한 크기여야 합니다. 필요에 따라 상자 충돌체에서 충돌체 편집 옵션을 선택하여 상자 충돌체를 조정합니다. x, y 및 z 값을 변경하거나 편집기 장면 창에서 경계 상자 처리기를 끌 수 있습니다. 

![Lesson4 Chapter3 Noteim](images/Lesson4_Chapter3_noteim.PNG)

2. 경계 상자를 지구 코어의 “node_id30” 개체에 추가합니다. 이렇게 하려면 “3DObjectCollection”에서 “node_id30” 개체를 선택합니다. 검사기 탭에서 “구성 요소 추가”를 클릭하고 “경계 상자”를 검색합니다. 경계 상자, 상자 충돌체 및 조작 스크립트(조작 처리기, 근거리 잡기형 상호 작용)가 모두 동일한 게임 개체에 있는지 확인합니다.

3.  경계 상자의 “동작” 섹션의 정품 인증 드롭다운 목록에서 “시작 시 정품 인증”을 선택합니다. 다양한 정품 인증 옵션 및 다른 경계 상자 옵션에 대한 추가 세부 정보를 검토하려면 [MRTK의 경계 상자 설명서](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html>)를 참조하세요.

   

   *다음 몇 단계에서는 핸들(코너 및 사이드 핸들)의 시각화와 함께 기본 상자 재료, 잡는 동안의 재료를 조정하여 경계 상자의 모양을 변경할 수 있습니다. MRTK에는 경계 상자를 사용자 지정할 수 있는 몇 가지 옵션이 포함되어 있습니다.*

4. 프로젝트 패널에서 “boundingbox”를 검색하면 아래 이미지에 표시된 대로 검색 결과에 파란색 구로 표시된 재료의 목록을 확인할 수 있습니다. 

5. “boundingbox” 재료를 경계 상자 구성 요소의 상자 재료 슬롯으로 끕니다. 또한 “boundingboxgrabbed” 재료를 잡아 경계 상자 구성 요소의 잡은 상자 재료 슬롯에 배치합니다.

6. “MRTK_BoundingBox_ScaleWidget” 재료를 경계 상자 구성 요소의 크기 조정 핸들 프리팹 슬롯으로 끕니다. 

7. “MRTK_BoundingBox_RotateWidget” 재료를 경계 상자 구성 요소의 회전 핸들 슬롯으로 끕니다.

![Lesson4 Chapter3 Step4 7Im](images/Lesson4_chapter3_step4-7im.PNG)

8. 경계 상자가 오른쪽 개체를 대상으로 하는지 확인합니다. 경계 상자 구성 요소에는 “대상 개체” 및 “경계 재정의” 스크립트가 있습니다. 경계 상자가 있는 개체를 이 두 슬롯으로 끌어야 합니다. 이 예제에서는 아래 이미지에 나온 것처럼 “node_id30” 개체를 이러한 슬롯 모두로 끕니다.

> 애플리케이션을 시작하거나 재생하는 경우 개체는 이제 파란색 프레임으로 묶이게 됩니다. 개체의 크기를 조정하려면 해당 프레임의 모서리를 끌면 됩니다. 크기 조정 핸들 및 회전 핸들을 더 크고 잘 표시되도록 하려면 기본 경계 상자 설정(4~7단계 사용 안 함)을 사용하는 것이 좋습니다. 

![Lesson4 Chapter3 Step8im](images/Lesson4_Chapter3_step8im.PNG)

9. 기본 경계 상자 시각화로 돌아가려면 경계 상자 개체의 검사기 패널에서 회전 핸들 프리팹을 선택하고 삭제 키를 누릅니다. 그러면 아래 이미지와 유사한 경계 상자 시각화가 표시됩니다. 참고: 경계 상자 시각화는 재생 모드에 있을 때만 나타납니다.

![Lesson4 Chapter3 Step9im](images/Lesson4_chapter3_step9im.PNG)

### <a name="adding-touch-effects"></a>터치 효과 추가
이 예제에서는 손으로 개체를 터치할 때 사운드 효과를 재생합니다.

1. 오디오 원본 구성 요소를 게임 개체에 추가합니다. 장면 계층에서 “Octa” 개체를 선택합니다. 검사기 패널에서 “구성 요소 추가” 단추를 클릭하고 “오디오 원본”을 검색한 후 선택합니다. 이 오디오 원본을 사용하여 이후 단계에서 사운드 효과를 재생합니다. 

>참고: “Octa” 개체에 상자 충돌체가 있는지 확인합니다.

2. “근거리 터치형 상호 작용(near interaction touchable)” 구성 요소를 추가합니다. 검사기 패널에서 “구성 요소 추가” 단추를 클릭하고 “근거리 터치형 상호 작용”을 검색합니다. 선택하여 구성 요소를 추가합니다. 참고: 상자 충돌체를 강조 표시하지 않고 추가하려는 구성 요소를 강조 표시하도록 스크린샷을 수정합니다.

>참고: 이전에는 “근거리 잡기형 상호 작용”을 추가했습니다. 이것과 “근거리 터치형 상호 작용” 간의 차이점은 “잡기형” 상호 작용은 잡고 상호 작용할 개체를 위한 것이고, “터치형” 구성 요소는 터치할 개체를 위한 것이란 점입니다. 두 구성 요소 모두 상호 작용의 조합을 위해 함께 사용할 수 있습니다.

![Lesson4 Chapter4 Step1 2Im](images/Lesson4_chapter4_step1-2im.PNG)

3. “손 상호 작용 터치” 스크립트에 추가합니다. 이 스크립트는 이 데모 패키지의 일부로 가져온 통합 장면에 포함되고 원래 MRTK에는 포함되지 않습니다. 이전 단계와 동일하게, “구성 요소 추가”를 클릭하고 “손 상호 작용 터치”를 검색하여 추가합니다. 
   스크립트와 함께 사용할 수 있는 3가지 옵션이 있습니다. 

   - “터치 시 완료(On touch completed)” 개체를 터치하고 릴리스할 때 트리거됩니다. 
   - “터치 시 시작(On touch started)” 개체를 터치하면 트리거됩니다. 
   - “터치 시 업데이트(On touch updated)” 손으로 개체를 터치하는 동안 주기적으로 트리거됩니다. 

   이 예제에서는 “터치 시 시작” 설정을 사용하여 작업해보겠습니다.

4. 아래 이미지에 표시된 대로 “터치 시 시작”에서 “+” 단추를 클릭합니다. Octa 개체를 빈 필드로 끕니다. 

5. “함수 없음”(아래 이미지에서 녹색 사각형 위)이라는 드롭다운에서 AudioSource > PlayOneShot을 선택합니다. 아래 개념을 사용하여 오디오 클립을 이 필드에 추가하겠습니다.

   - MRTK는 오디오 클립의 작은 목록을 제공합니다. 프로젝트 패널에서 자유롭게 살펴보세요. “MixedRealityToolkit.SDK” 폴더의 “표준 자산” 폴더에서 찾을 수 있습니다. 모든 오디오 클립이 있는 “audio” 폴더가 표시됩니다.
   - 이 예제에서는 “MRTK_Gem” 오디오 클립을 사용하려고 합니다. 
   - 오디오 클립을 추가하려면 원하는 클립을 프로젝트 패널에서 검사기 패널의 AudioSource.PlayOneShot(위 예제에서 녹색 상자로 표시됨)으로 끌기만 하면 됩니다.

   이제 사용자가 Octa 개체에 접근하여 터치하면 오디오 트랙 “MRTK_Gem”이 재생됩니다. 또한 “손 상호 작용 터치” 스크립트는 터치 시 개체의 색을 조정합니다. 

![Lesson4 Chapter4 Step3 5 Noteim](images/Lesson4_chapter4_step3-5-noteim.PNG)

### <a name="congratulations"></a>축하합니다. 
이 단원에서는 그리드 컬렉션에서 3D 개체를 구성하는 방법과 근거리 상호 작용(추적된 손으로 직접 잡기)과 원거리 상호 작용(응시 레이 또는 손 레이 사용)을 사용하여 3D 개체를 조작(크기 조정, 회전 및 이동)하는 방법을 알아보았습니다. 또한 3D 개체 주위에 경계 상자를 배치하는 방법을 학습하고 경계 상자에서 gizmo를 사용하고 사용자 지정하는 방법을 배웠습니다. 마지막으로 개체를 터치할 때 이벤트를 트리거하는 방법을 알아보았습니다.

[다음 단원: 고급 입력](mrlearning-base-ch5.md)

