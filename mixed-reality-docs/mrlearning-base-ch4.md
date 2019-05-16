---
title: MR 학습 자료 모듈-3D 개체 상호 작용
description: 혼합된 현실 응용 프로그램에서 Azure Face recognition 얼굴 인식을 구현 하는 방법을 알아보려면이 과정을 완료 합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: unity, 자습서, hololens, 혼합된 현실
ms.openlocfilehash: 45e772de0825fe2161f880a165d6c75c755b849e
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730903"
---
# <a name="mr-learning-base-module---3d-object-interaction"></a>MR 학습 자료 모듈-3D 개체 상호 작용

이 단원에서는 기본 3D 콘텐츠 및 사용자 환경을 거치게 됩니다. 에서는 됩니다 하는 방법을 알아봅니다 3D 개체를 컬렉션의 일부로 구성, 경계 상자의 기본 조작에 대 한 자세한, 근거리 및 원거리 상호 작용에 알아봅니다 및 터치에 대 한 자세한 추적 손으로 제스처를 가져옵니다. 

## <a name="objectives"></a>목표

* MRTK의 그리드 개체 컬렉션을 사용 하 여 3D 콘텐츠를 구성 하는 방법 알아보기
* 경계 상자를 구현 합니다.
* 기본 조작 (회전, 이동 및 크기 조정)에 대 한 3D 개체를 구성 합니다.
* 근거리 및 원거리 상호 작용을 탐색
* 추가 손 모양 잡기 등 터치 제스처를 추적에 대해 알아봅니다

## <a name="instructions"></a>지침

### <a name="organizing-3d-objects-in-a-collection"></a>컬렉션에서 3D 개체를 구성합니다.

1. 계층을 마우스 오른쪽 단추로 클릭 하 고 선택 "빈 항목 만들기." 이 빈 게임 개체를 만듭니다. 이름을 "3DObjectCollection."로 변경 여기서는 3D 개체의 모든 배치할는 것입니다. X에 컬렉션의 위치를 설정 해야 = 0, y = 0 및 z = 0.

![Lesson4 Chapter1 Step1im](images/Lesson4_Chapter1_step1im.PNG)

2. BaseModule 자산 사용에 설명 된 사용자 지정 패키지를 가져오는 것과 같은 지침을 가져올 [1 단원](mrlearning-base-ch1.md)합니다. BaseModule 자산 3D 모듈 및이 자습서 전체에서 사용 되는 다른 유용한 스크립트를 포함 합니다. 여기 BaseModule unity 패키지를 찾을 수 있습니다. <https://github.com/Microsoft/MixedRealityLearning/releases/tag/V1.1>

3. Prefab 커피 cup 옆에 있는 파란색 큐브에서 인식할 수 있습니다. 커피 cup (나타내는 원래 3D 모델 및 prefab 되지 않습니다.) 작은 백서와 파란색 큐브를 선택 하지 마십시오 

![Lesson4 Chapter1 Noteaim](images/Lesson4_chapter1_noteaim.PNG)

4. 1 단계에서 선택한 커피 cup prefab을 "3DObjectCollection" 게임 개체 끕니다. 커피 cup 컬렉션의 자식이 됩니다.

![Lesson4 Chapter1 Step4ima](images/Lesson4_chapter1_step4ima.PNG)

5. 다음으로, 더 많은 3D 개체는 장면에 추가 하겠습니다. 다음은이 예제에서 추가 하려는 개체의 목록입니다. 개체를 추가 하면 다양 한 크기의 장면에 포함 된 나타나는지를 알 수 있습니다. 변환 설정 [관리자] 패널에에서 각 3D 모델의 배율을 조정 합니다. 이 예제에 대 한 권장 되는 조정 아래 개체를 사용 하 여 나열 됩니다. 검색 상자에 프로젝트 패널에 이러한 단어를 검색 하 고 이전 단계와 마찬가지로 "3DObjectCollection" 개체로 3D 개체 prefab을 끕니다. 자산에서 prefabs의 이러한 컬렉션을 확인할 수 있습니다 > BaseModuleAssets > 기본 모듈 Prefabs
- "TheModule_BaseModuleIncomplete." 검색 장면으로 끌어다 놓습니다. 배율을 x로 설정 0.03, = y = 0.03, z = 0.03입니다. 
- "Octa_BaseModuleIncomplete." 검색 장면으로 끌어다 놓습니다. 소수 자릿수를 x로 0.13 =. y = 0.13, z =0.13.
- "EarthCore_BaseModuleIncomplete." 검색 장면으로 끌어다 놓습니다. 소수 자릿수를 x로 50.0 = y = 50.0, z 50.0 =.
- "Cheese_BaseModuleIncomplete." 검색 장면으로 끌어다 놓습니다. X에 소수 자릿수를 설정 0.05 = y = 0.05, z = 0.05입니다.
- "Model_Platonic_BaseModuleIncomplete." 검색 장면으로 끌어다 놓습니다. X에 소수 자릿수를 설정, 0.13 = y 0.13, = z 0.13 =.
- "CoffeeCup_BaseModuleIncomplete." 검색 장면으로 끌어다 놓습니다.

![Lesson4 Chapter1 Step5im](images/Lesson4_Chapter1_step5im.PNG)

6. 장면에 3 개의 큐브를 추가 합니다. "3DObjectCollection" 개체를 마우스 오른쪽 단추로 클릭, "3D 개체"를 선택한 다음 선택 "큐브"입니다. X에 소수 자릿수를 설정, 0.14 = y 0.14, 및 z = 0.14 =. 총 3 개의 큐브를 만들려면 추가 2 번이이 단계를 반복 합니다. 또는 큐브는 총 3 개의 큐브를 두 번 복제할 수 있습니다. 자산에서 세 개의 준비 된 큐브 prefabs 사용할 수도 있습니다 > BaseModuleAssets > 기본 모듈 Prefabs 선택 GreenCube_BaseModuleIncomplete, BlueCube_BaseModuleIncomplete 및 OrangeCube_BaseModuleIncomplete 합니다.

![Lesson4 Chapter1 Step6im](images/Lesson4_Chapter1_step6im.PNG)

7. 에 설명 된 절차를 사용 하 여 표를 형성 하는 개체의 컬렉션을 구성할 [단원 2](mrlearning-base-ch2.md) MRTK의 그리드 개체 컬렉션을 사용 하 여 합니다. 3x3 표로 개체를 구성 하는 예제를 보려면 아래 이미지를 참조 하세요.

![Lesson4 Chapter1 Notebim](images/Lesson4_chapter1_notebim.PNG)

>참고: 중앙을 개체 위의 이미지에서와 같은 개체 중 일부는 확인할 수 있습니다. 즉, prefabs 또는 개체에는 정렬 되지 않은 자식 개체가 있을 수 있습니다. 자유롭게 개체 위치를 잘 정렬 된 표를 달성 하기 위해 자식 개체 위치에 필요한 부분을 수정할 수 있습니다.


### <a name="manipulating-3d-objects"></a>3D 개체를 조작합니다.
1. 큐브를 조작 하는 기능을 추가 합니다. 3D 개체를 조작 하는 기능을 추가 하려면 다음을 수행 해야 합니다.
-   (이 예제의 큐브 중 하나) 계층 구조에서 조작 하려는 3D 개체를 선택 합니다.
-   "구성 요소를 추가 합니다."를 클릭 합니다. 
-   "조작" 검색
-   "조작 처리기입니다."를 선택 합니다.
-   "3DObjectCollection" 개체는 하지만 하지는 "3DObjectCollection" 아래의 모든 3D 개체에 대 한 반복 자체입니다.
-   모든 3D 개체는 collider 또는 확인 상자 collider (구성 요소 추가 > collider 상자).

![Lesson4 Chapter2 Step1im](images/Lesson4_chapter2_step1im.PNG)

>조작 처리기 구성 요소인 개체 조작 되는 경우 작동 하는 방법에 대 한 설정을 조정할 수 있도록 합니다. 여기에 회전, 크기 조정, 이동 및 특정 축의 제약 이동 합니다. 

2. 확장 될 수 있도록 큐브가 두 개를 제한 합니다. "3DObjectCollection" 개체에서 하나의 큐브를 선택 합니다. "두 전달된 조작 유형" 옆에 있는 [관리자] 패널의 드롭다운 메뉴를 클릭 하 고 "확장" 선택 이렇게 하면 사용자가 큐브의 크기만 변경할 수 있도록 합니다.

![Lesson4 Chapter2 Step2im](images/Lesson4_Chapter2_step2im.PNG)

3. 에서는 서로 구별할 수 있도록 각 큐브의 색을 변경 합니다. 
-   프로젝트 패널을 이동 하 고 "MixedRealityToolkit.SDK"를 참조 하세요. 다음 선택 될 때까지 아래로 스크롤하십시오.
-   "표준 자산" 폴더를 선택 합니다.
-   "자료" 폴더를 클릭 합니다.
-   각 큐브를 다른 자료를 끕니다. 

>참고: 큐브에 대 한 색을 선택할 수 있습니다. 예를 들어 하겠습니다 "glowingcyan", "glowingorange"를 사용 하 고 "친환경"입니다. 자유롭게 다른 색을 실험할 수 있습니다. 색에 큐브를 추가 하려면의 색을 변경 하려면 큐브를 클릭 한 다음 자료 메시 렌더러의 material 필드 큐브의 검사기 패널에 끌어다 놓습니다. 

![Lesson4 Chapter2 Step3im](images/Lesson4_Chapter2_step3im.PNG)

4. "3DObjectCollection" 개체의 다른 큐브를 선택 하 고 되도록 이동을 헤드에서 수정 거리에 제한 됩니다. 이렇게 하려면, "제약 조건에서 이동"의 오른쪽에 드롭다운 메뉴에서 클릭 하 고 "헤드에서의 거리를 수정 합니다." 선택 따라서 사용자는 해당 필드의 비전 내의 큐브만 이동할 수 있도록 합니다. 

![Lesson4 Chapter2 Step4im](images/Lesson4_chapter2_step4im.PNG)

다음 몇 단계의 목표: 잡기 및 3D 개체가 상호 작용 사용 하도록 설정 됩니다. 다양 한 조작 설정 적용 

5. 치즈 개체를 선택 하 고 검사기 창에서 "구성 요소를 추가 합니다."를 클릭 

6. 검색 상자에 "근처 상호 작용 Grabbable" 검색 하 고 스크립트를 선택 합니다. 이 구성 요소에는 사용자가 연락 하 여 추적된 실습을 사용 하 여 개체를 잡고 있습니다. 개체도 수 거리를 조작할 수 않으면 "허용 훨씬 조작" 확인란을 선택 하지 않으면 (아래 이미지에서 녹색 원으로 표시 됩니다.)

![Lesson4 Chapter2 Step6im](images/Lesson4_Chapter2_step6im.PNG)

7. 해당 개체에 5와 6 단계를 반복 하 여 "근처 상호 작용 Grabbable" 옥 타 개체, 플라톤의 다면체 개체, 지구 코어, 음력 모듈 및 coffee cup를 추가 합니다.

8. 옥 타 개체에서 맨 조작의 기능을 제거 합니다. 이렇게 하려면 계층의는 옥 타를 선택 하 고 (녹색 원으로 표시) "먼 조작을 허용" 확인란의 선택을 취소 합니다. 이렇게 하면 사용자 추적된 실습을 사용 하 여 직접 옥 타 상호 작용할 수 있도록 합니다.

>참고: 전체 설명은 조작 처리기 구성 요소 및 해당 설정에 연결 된에 대 한 하세요 합니다 [MRTK 설명서](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)합니다.

9. 커피 cup earth 핵심, 음력 모듈을 "근처 상호 작용 Grabbable" 구성 요소에 추가 되었는지 확인 (단계 7 참조).

10. 음력 모듈에 대 한 조작 처리기 설정을 변경할 개체의 거의 모두에 대 한 중심 및 먼 상호 작용 하는 방법에 대 한 회전 되도록 아래 이미지에 표시 된 대로.

![Lesson4 Chapter2 Step10im](images/Lesson4_chapter2_step10im.PNG)

11: 지구 core에 대 한 릴리스 동작을 변경 "항목이 없습니다." 이렇게 하면 사용자 감각에서 지구 핵심 릴리스되면 여 이동할 계속 되지 않도록 합니다. 

![Lesson4 Chapter2 Step11im](images/Lesson4_Chapter2_step11im.PNG)

> 참고: 이 설정은 throw 할 수 있는 공 만들기와 같은 시나리오에 유용 합니다. 속도 및 angular 개발 속도 유지는 되므로 공을 출시 되 면에서 릴리스된 마찬가지로 실제 공 작동 하는 방법이 된 속도에 이동 하려면 계속 합니다.

### <a name="adding-bounding-boxes"></a>경계 상자 추가
경계 상자 쉽고 광선 기반 조작 (먼 상호 작용 합니다.)와 상호 작용) (near을 직접 조작에 대 한 것을 사용 하 여 개체를 조작 하는 것이 직관적 경계 상자 크기 조정 및 특정 축 따라 개체를 회전을 잡을 수 "handles"를 제공 합니다.
>참고: 경계 상자 개체에 추가 하기 전에 먼저 해야는 collider 개체 (예는 상자 collider.) 에서 수행한 것 처럼 이전에이 단원. 추가 구성 요소를 선택 하는 개체의 검사기 패널에 개체를 선택 하 여 colliders를 추가할 수 있습니다 > 상자 Collider 합니다.
>

1. 하나 아직 없는 경우 (상자 collider 및 없어도 다음 제공 된 지침에 따라 기본 모듈 Assets 폴더를에 제공 된 prefab을 사용 하는 경우 설치 합니다.) 상자 collider 지구 핵심 개체에 추가 지구 코어의 경우 해야 상자 collider 지구 core 아래의 "node_id30" 개체를 추가할 아래 이미지에 표시 된 대로 합니다. node_id30 선택 개체의 관리자 탭에서 "구성 요소 추가"를 클릭 하 고 "collider box." 검색 

![Lesson4 Chapter3 Step1im](images/Lesson4_Chapter3_step1im.PNG)

![Lesson4 Chapter3 Step2im](images/Lesson4_chapter3_step2im.PNG)

> 참고: 너무 크거나 너무 작아서 되지 않도록 상자 collider를 시각화 하는 있는지 확인 합니다. 약 (이 예제에서는 지구 코어)의 관련는 개체와 동일한 크기 여야 합니다. 필요에 따라 상자 collider 편집 collider 옵션을 선택 하 여 상자 collider를 조정 합니다. X, y 및 z 값을 변경 하거나 있습니다 편집기 장면 창의 경계 상자 처리기를 끌거나 합니다. 

![Lesson4 Chapter3 Noteim](images/Lesson4_Chapter3_noteim.PNG)

2. 지구 핵심 "node_id30" 개체 경계 상자를 추가 합니다. 이렇게 하려면 "3DObjectCollection"에서 "node_id30" 개체를 선택 합니다. 관리자 탭에서 "구성 요소를 추가"를 클릭 하 고 "경계 상자입니다."에 대 한 검색 경계 상자, 상자 collider 및 조작 스크립트 (상호 작용 grabbable 거의 조작 처리기)를 모두 동일한 게임 객체에 있는지 확인 합니다.

3.  경계 상자의 "동작" 섹션에서 정품 인증 드롭다운 목록에서 "시작 시 활성화"를 선택 합니다. 다양 한 정품 인증 옵션 및 다른 경계 상자 옵션에 대 한 추가 세부 정보를 검토 하려면 하십시오는 [MRTK의 경계 상자 설명서](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html>)

   

   *다음 몇 단계에서는 또한 경계 상자 핸들 (한 쪽 핸들)의 시각화 뿐만 아니라 기본 상자 자료,이 잡고 동안 자료를 조정 하 여 모양을 변경 합니다. MRTK 경계 상자를 사용자 지정할 수 있는 몇 가지 옵션을 포함 합니다.*

4. 프로젝트 패널에서 아래 이미지에 표시 된 대로 "boundingbox"를 검색 파랑 구 검색 결과에서 가리키는 자료 목록이 표시 됩니다. 

5. 경계 상자 구성 요소에 대해 상자 재료 슬롯으로 "boundingbox" 자료를 끕니다. "Boundingboxgrabbed" 자료를 잡고 경계 상자 구성 요소에 대해 상자 grabbed 재료 슬롯에 넣을 수도 있습니다.

6. 경계 상자 구성 요소에 크기 조정 핸들 prefab 슬롯으로 "MRTK_BoundingBox_ScaleWidget" 자료를 끕니다. 

7. 회전 핸들 슬롯으로 결합 상자 구성 요소에 "MRTK_BoundingBox_RotateWidget" 자료를 끕니다.

![Lesson4 Chapter3 4 단계 7Im](images/Lesson4_chapter3_step4-7im.PNG)

8. 경계 상자 오른쪽 개체를 대상으로 하는지 확인 합니다. 경계 상자 구성 요소에는 "대상 개체" 및 "제한 재정의" 스크립트입니다. 이러한 슬롯 중 둘 다에 묶어 경계 상자가 포함 된 개체를 끌 수 있는지 확인 합니다. 이 예제에서는 아래 그림과에서 같이 "node_id30" 개체를 모두 이러한 슬롯을 끕니다.

> 을 시작 하거나 응용 프로그램을 재생 하는 경우 개체는 이제 파란색 프레임으로 묶을 수 있습니다. 개체의 크기를 조정 하려면 해당 프레임의 모퉁이 끌어를 천만 요. 크기 조정 핸들 및 크고 더 잘 표시 되도록 회전 핸들을 원하는 경우 경계 상자 설정 (4 ~ 7 단계를 방지 합니다.) 기본값을 사용 하는 것이 좋습니다. 

![Lesson4 Chapter3 Step8im](images/Lesson4_Chapter3_step8im.PNG)

9. 경계 상자의 개체의 검사기 창에 있는 상자 시각화 경계 기본값으로 반환할 회전 핸들 prefab 선택 및 delete 키를, 경계 상자 시각화 아래 이미지와 비슷하게 나타납니다. 참고: 경계 상자 시각화 play 모드에 있을 때만 나타납니다.

![Lesson4 Chapter3 Step9im](images/Lesson4_chapter3_step9im.PNG)

### <a name="adding-touch-effects"></a>터치 효과 추가합니다.
이 예제에서는 손으로 개체를 터치 할 때 사운드 효과 재생 하려고 합니다.

1. 게임 개체에는 오디오 원본 구성 요소를 추가 합니다. 장면 계층 구조에서 "옥 타" 개체를 선택 합니다. 검사기 창에서 "구성 요소 추가" 단추를, 검색 및 "오디오 소스" 선택 합니다. 이 오디오 소스 음향 효과 나중에 재생 하는 데 사용 하겠습니다. 

>참고: "옥 타" 개체에 상자 collider에 있는지 확인 합니다.

2. 상호 작용 touchable"근처" 구성 요소를 추가 합니다. 검사기 패널과 "상호 작용 touchable 근처"에 대 한 검색에서 "구성 요소 추가" 단추를 클릭 구성 요소를 추가 하려면 선택 합니다. 참고: 스크린 샷 하는 구성 요소를 추가 하 고 뿐 아니라 상자 collider 강조 표시를 강조 표시 수정 합니다.

>참고: 이전에 "거의 상호 작용 grabbable."를 추가 했습니다. 이 사이의 상호 작용 touchable"근처" 차이점은 "grabbable" 상호 작용을 주워 상호 작용할 개체 하기 위한 것입니다. "Touchable" 구성 요소는 그대로 유지 되도록 개체에 대 한 것입니다. 두 구성 요소 상호 작용의 조합에 대해 함께 사용할 수 있습니다.

![Lesson4 Chapter4 Step1 2Im](images/Lesson4_chapter4_step1-2im.PNG)

3. "터치 상호 작용 전달" 스크립트에 추가 합니다. 이 스크립트는이 데모 패키지의 일부로 가져온 unity 장면으로 포함 하 고 원래 MRTK에 포함 되지 않습니다. 이전 단계와 같은 "구성 요소를 추가"를 클릭 하 고 "직접 상호 작용 터치"를 검색할 추가 합니다. 
   스크립트를 사용 하 여 3 개 옵션이 있는지 확인 합니다. 

   - "에서 터치를 완료 합니다." 이 터치 하는 개체를 해제 하는 경우 트리거됩니다. 
   - "에서 터치 시작 합니다." 이 개체는 연결 된 경우 트리거됩니다. 
   - "에서 터치 업데이트 합니다." 이렇게 하면 직접 개체에 접촉 되어 있는 동안 정기적으로 트리거됩니다. 

   예를 들어 "에서 시작 하는 터치" 설정을 사용 하 여 라는 노력 합니다.

4. 아래 이미지에 표시 된 대로 "에서 시작 하는 터치" 옵션에서 "+" 단추를 클릭 합니다. 빈 필드에 옥 타 개체를 끕니다. 

5. 드롭다운 목록 (아래 이미지에서 녹색 사각형) 위 "function 없습니다" 라는, AudioSource 선택 > PlayOneShot 합니다. 오디오 클립 아래 개념을 사용 하 여이 필드를 추가 합니다.

   - MRTK 오디오 클립의 작은 목록이 제공지 않습니다. 프로젝트 패널에서 이러한 살펴보시기 바랍니다. 이러한 "MixedRealityToolkit.SDK" 폴더를 선택한 다음 "표준 자산" 폴더에서 찾을 수 있습니다. 있는 모든 오디오 클립 있는 "오디오" 폴더를 표시 됩니다.
   - 예를 들어 "MRTK_Gem" 오디오 클립을 사용 하려고 합니다. 
   - 오디오 클립을 추가 하려면 단순히 끌어옵니다 원하는 클립 프로젝트 패널에서 inspector 패널에서 AudioSource.PlayOneShot (위의 예제에서 녹색 상자로 표시 됨).

   이제 사용자에 도달 하 옥 타 개체와 연결 하는 경우 "MRTK_Gem" 오디오 트랙 재생 됩니다. "직접 상호 작용 터치" 스크립트를 작업 하는 경우 개체의 색을 조정도 됩니다. 

![Lesson4 Chapter4 3 단계 5 Noteim](images/Lesson4_chapter4_step3-5-noteim.PNG)

### <a name="congratulations"></a>축 하. 
표 컬렉션에서 3D 개체를 구성 하는 방법과 (크기 조정, 회전 및 이동) 하는 3D 개체를 조작 하는 방법을 알아보았습니다이 단원에서는 거의 (직접 클릭 한 다음 추적된 실습을 사용 하 여) 상호 작용 하 고 먼 상호 작용 (게이즈 표면이 또는 직접 광선을 사용 합니다.)를 사용 하 여 또한 3D 개체 주위의 경계 상자를 배치 하는 방법을 학습 하 고 사용 하 여의 경계 상자 gizmo를 사용자 지정 하는 방법을 배웠습니다. 마지막으로 개체를 변경 하는 경우 이벤트를 트리거하는 방법을 알아보았습니다.

[다음 단원: 고급 입력](mrlearning-base-ch5.md)

