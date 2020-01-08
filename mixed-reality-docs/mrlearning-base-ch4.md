---
title: 자습서 시작-5. 3D 개체와 상호 작용
description: ''
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, Hololens
ms.openlocfilehash: fe068d0cfcea369f10e6fa636eb73fecb3002fa7
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334381"
---
# <a name="5-interacting-with-3d-objects"></a>5.3D 개체와 상호 작용

이 자습서에서는 다음과 같은 기본 3D 콘텐츠 및 사용자 환경에 대해 설명 합니다.

* 3D 개체를 컬렉션의 일부로 구성
* 기본 조작을 위한 경계 상자
* 근거리 및 원거리 상호 작용
* 손으로 직접 추적 하는 터치 및 잡기 제스처

## <a name="objectives"></a>목표

* MRTK의 grid 개체 컬렉션을 사용 하 여 3D 콘텐츠를 구성 하는 방법을 알아봅니다.
* 경계 상자 구현
* 기본 조작을 위한 3D 개체 구성-이동, 회전 및 크기 조정
* 근거리 및 원거리 조작 살펴보기
* 잡기, 터치 등의 추가 수동 추적 제스처에 대해 알아보기

## <a name="organizing-3d-objects-in-a-collection"></a>컬렉션에서 3D 개체 구성

1. 계층 구조를 마우스 오른쪽 단추로 클릭 하 고 비어 있음 만들기를 선택 하 여 빈 게임 개체를 만들고 3DObjectCollection로 이름을 바꾼 다음 x = 0, y = 0 및 z = 0에 배치 되어 있는지 확인 합니다.

    ![mrlearning-base-ch4-1-step1](images/mrlearning-base-ch4-1-step1.png)

2. Unity 패키지 [HoloLens2](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage) 를 다운로드 하 고 동일한 지침을 사용 하 여 [1 단원](mrlearning-base-ch1.md)에 설명 된 사용자 지정 패키지를 가져옵니다. 이 패키지는이 자습서 전체에서 사용 되는 3D 모델 및 기타 유용한 자산을 포함 합니다.

3. 프로젝트 패널에서 asset > BasemodulPrefabs Sets > 기본 모듈 Prefabs로 이동 하 고 "불완전"을 검색 하 여 이러한 중 일부를 사용 합니다.

    ![mrlearning-base-ch4-1-step3](images/mrlearning-base-ch4-1-step3.png)

4. 커피 컵을 1 단계의 3DObjectCollection game 개체로 끕니다. 이제 커피 컵이 컬렉션의 자식이 됩니다.

    ![mrlearning-base-ch4-1-step4](images/mrlearning-base-ch4-1-step4.png)

5. 다음으로 이전 단계와 동일한 프로세스를 수행 하 여 더 많은 3D 개체를 장면에 추가 합니다. 다음은이 예제에서 추가할 개체의 목록입니다. 개체를 추가 하면 여러 크기의 장면에 표시 되는 것을 알 수 있습니다. 검사기 패널의 변환 설정에서 각 3D 모델의 배율을 조정 합니다. 이 예제에서 권장되는 조정은 아래 개체를 사용하여 나열됩니다.

    * Cheese_BaseModuleIncomplete. 크기 조정: x = 0.05, y = 0.05, z = 0.05.
    * CoffeeCup_BaseModuleIncomplete. 크기 조정: x = 0.1, y = 0.1, z = 0.1.
    * EarthCore_BaseModuleIncomplete. 크기 조정: x = 50.0 y = 50.0, z = 50.0.
    * Model_Platonic_BaseModuleIncomplete. 크기 조정: x = 0.13, y = 0.13, z = 0.13.
    * Octa_BaseModuleIncomplete. 크기 조정: x = 0.13. y = 0.13, z =0.13으로 설정합니다.
    * TheModule_BaseModuleIncomplete. 크기 조정: x = 0.03, y = 0.03, z = 0.03.

    ![mrlearning-base-ch4-1-step5](images/mrlearning-base-ch4-1-step5.png)

6. 장면에 세 개의 큐브를 추가 합니다. 3DObjectCollection 개체를 마우스 오른쪽 단추로 클릭 하 고 3D 개체를 선택한 다음 큐브를 선택 합니다. 배율을 x = 0.14, y = 0.14 및 z = 0.14로 설정합니다. 이 단계를 두 번 더 반복 하 여 총 세 개의 큐브를 만듭니다. 또는 큐브를 두 번 복제 하 여 총 3 개 큐브를 만들 수 있습니다. 또한 자산>BaseModuleAssets>기본 모듈 프리팹에서 세 개의 준비된 큐브 프리팹을 선택하고, GreenCube_BaseModuleIncomplete, BlueCube_BaseModuleIncomplete 및 OrangeCube_BaseModuleIncomplete를 선택할 수 있습니다.

    ![mrlearning-base-ch4-1-step6](images/mrlearning-base-ch4-1-step6.png)

7. [2 단원](mrlearning-base-ch2.md)에 설명 된 절차를 통해 MRTK의 Grid 개체 컬렉션을 사용 하 여 표 형태를 구성 하는 개체의 컬렉션을 구성 합니다. 3x3 모눈에서 개체를 구성 하는 예는 아래 이미지를 참조 하세요.

    ![mrlearning-base-ch4-1-step7](images/mrlearning-base-ch4-1-step7.png)

    >[!NOTE]
    >위의 이미지에 있는 개체와 같이 일부 개체는 외부에서 분리 된 것을 알 수 있습니다. 이는 프리팹 또는 개체에 정렬되지 않은 자식 개체가 있기 때문입니다. 자유롭게 개체 위치 또는 자식 개체 위치를 조정하여 잘 정렬된 그리드를 만들 수 있습니다.

## <a name="manipulating-3d-objects"></a>3D 개체 조작

1. 큐브를 조작하는 기능을 추가합니다. 3D 개체를 조작 하는 기능을 추가 하려면 다음을 수행 합니다.
    * 계층 구조에서 조작할 3D 개체 (즉, 큐브 중 하나)를 선택 합니다.
    * 구성 요소 추가를 클릭 합니다.
    * "조작" 검색
    * 조작 처리기 선택
    * 3DObjectCollection 개체 아래의 모든 3D 개체에 대해 반복 하지만 3DObjectCollection 자체는 반복 하지 않습니다.
    * 모든 3D 개체에 collider 또는 box collider (구성 요소 추가 > 상자 Collider)가 있는지 확인 합니다.

    ![Lesson4 Chapter2 Step1im](images/Lesson4_chapter2_step1im.PNG)

    >[!NOTE]
    >조작 처리기는 조작할 때 개체가 동작 하는 방법에 대 한 설정을 조정할 수 있도록 하는 구성 요소입니다. 여기에는 특정 축의 회전, 크기 조정, 이동 및 제한 이동이 포함 됩니다.

2. 확장만 가능하도록 큐브 하나를 제한합니다. 3DObjectCollection 개체에서 큐브 하나를 선택 합니다. 검사기 패널에서 두 개의 왼손 조작 유형 옆에 있는 드롭다운 메뉴를 클릭 하 고 Scale을 선택 합니다. 이렇게 하면 사용자가 큐브의 크기만 변경할 수 있습니다.

    ![Lesson4 Chapter2 Step2im](images/Lesson4_Chapter2_step2im.PNG)

3. 서로 구별할 수 있도록 각 큐브의 색을 변경합니다.
    * 프로젝트 패널로 이동 하 고 MixedRealityToolkit가 표시 될 때까지 아래로 스크롤한 다음 선택 합니다.
    * 표준 자산 폴더를 선택 합니다.
    * 재질 폴더를 클릭 합니다.
    * 각 큐브에 다른 재료를 끕니다.

    >[!NOTE]
    >큐브에 대한 색을 선택할 수 있습니다. 이 예에서는 glowingcyan, glowingcyan 및 green이 사용 됩니다. 자유롭게 다른 색을 시도해 보세요. 큐브에 색을 추가 하려면 변경할 큐브를 클릭 한 다음 큐브의 검사기 패널에서 재질을 메시 렌더러의 재질 필드로 끕니다.

    ![Lesson4 Chapter2 Step3im](images/Lesson4_Chapter2_step3im.PNG)

4. 3DObjectCollection 개체에서 다른 큐브를 선택 하 고 이동 하 여 head에서 고정 거리 만큼 이동 하도록 합니다. 이렇게 하려면 이동 레이블의 제약 조건 오른쪽에 있는 드롭다운 메뉴를 클릭 하 고 Head에서 거리 수정을 선택 합니다. 이는 큐브를 비전의 해당 필드 내에 포함 하도록 조정 합니다.

    ![Lesson4 Chapter2 Step4im](images/Lesson4_chapter2_step4im.PNG)

    다음 몇 단계의 목표는 3D 개체를 가져오고 상호 작용 하 고 다른 조작 설정을 적용 하는 것입니다.

5. 치즈 개체를 선택한 다음, 검사기 패널에서 구성 요소 추가를 클릭 합니다.

6. 근접 한 상호 작용 Grabbable 검색 상자에서 검색 하 고 스크립트를 선택 합니다. 이 구성 요소를 통해 사용자는 추적 된 손으로 개체를 연결 하 고 가져올 수 있습니다. 아래 이미지에서 녹색 원으로 표시 되는 경우에도 개체를 거리에서 조작할 수 있습니다.

    ![Lesson4 Chapter2 Step6im](images/Lesson4_Chapter2_step6im.PNG)

7. 해당 개체에 대해 5 단계와 6 단계를 반복 하 여 근거리 상호 작용 Grabbable을 Octa 개체, Platonic 개체, 지구 코어, 음력 모듈 및 커피 컵에 추가 합니다.

8. Octa 개체에서 원거리 조작 기능을 제거합니다. 이렇게 하려면 계층에서 Octa를 선택 하 고 far 조작 허용 확인란의 선택을 취소 합니다 (녹색 원으로 표시 됨). 이렇게 하면 사용자가 추적 된 손을 사용 하 여 직접 octa와 상호 작용할 수 있습니다.

    >[!NOTE]
    >조작 처리기 구성 요소 및 연결 된 설정에 대 한 전체 설명서는 [Mrtk 설명서](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)를 참조 하세요.

9. 근접 한 상호 작용 Grabbable 구성 요소가 지구 코어, 음력 모듈 및 커피 컵에 추가 되었는지 확인 합니다 (7 단계 참조).

10. 음력 모듈의 경우 아래 이미지에 나와 있는 것 처럼 거의 상호 작용에 대 한 개체의 중심을 중심으로 회전 하도록 조작 처리기 설정을 변경 합니다.

    ![Lesson4 Chapter2 Step10im](images/Lesson4_chapter2_step10im.PNG)

11. 지구 코어의 경우 릴리스 동작을 nothing으로 변경 합니다. 이렇게 하면 사용자의 이해를 통해 지구 코어가 릴리스되는 경우 계속 해 서 이동 하지 않습니다.

    ![Lesson4 Chapter2 Step11im](images/Lesson4_Chapter2_step11im.PNG)

    >[!NOTE]
    >이 설정은 throw 할 수 있는 공을 만드는 등의 시나리오에 유용 합니다. 적절 한 속도 및 각도의 속도를 유지 하 여 해골을 릴리스한 후에는 릴리스되는 속도로 계속 이동 합니다. 물리적 공이 동작 하는 방식과 유사 합니다.

## <a name="adding-bounding-boxes"></a>경계 상자 추가

경계 상자를 사용 하면 직접 조작 (근거리 상호 작용)과 광선 기반 조작 (먼 상호 작용)에 대해 한 손으로 개체를 보다 쉽고 직관적으로 조작할 수 있습니다. 경계 상자는 특정 축을 따라 개체의 크기를 조정 하 고 회전 하는 데 grabbed 수 있는 핸들을 제공 합니다.

>[!NOTE]
>개체에 경계 상자를 추가 하려면 먼저이 단원의 앞에서 설명한 것 처럼 개체 (예: 상자 collider)에 collider가 있어야 합니다. Colliders 개체를 선택 하 고 개체의 검사자 패널에서 구성 요소 추가 > 상자 Collider를 선택 하 여 추가할 수 있습니다.

1. 상자 collider가 아직 없는 경우 지구 코어 개체에 상자 collider를 추가 합니다. 지정 된 지침에 따라 기본 모듈 자산 폴더에 제공 된 prefab를 사용 하는 경우에는 box collider 및 setup이 필요 하지 않습니다. 지구 코어의 경우 아래 이미지에 나와 있는 것 처럼 지구 코어 아래의 node_id30 개체에 collider 상자를 추가 했습니다. 개체의 검사자 탭에서 node_id30를 선택 하 고 구성 요소 추가를 클릭 한 다음 box collider를 검색 합니다.

    ![Lesson4 Chapter3 Step1im](images/Lesson4_Chapter3_step1im.PNG)

    ![Lesson4 Chapter3 Step2im](images/Lesson4_chapter3_step2im.PNG)

    >[!NOTE]
    >상자를 크기가 너무 크거나 너무 작게 지정 해야 합니다. 둘러싸고 있는 개체(이 예제에서는 지구 코어)와 대략 동일한 크기여야 합니다. Collider 상자에서 Collider 편집 옵션을 선택 하 여 필요에 따라 상자를 조정 합니다. X, y 및 z 값을 변경 하거나 편집기 장면 창에서 경계 상자 처리기를 끌 수 있습니다.

    ![Lesson4 Chapter3 Noteim](images/Lesson4_Chapter3_noteim.PNG)

2. 지구 코어의 node_id30 개체에 경계 상자를 추가 합니다. 이렇게 하려면 3DObjectCollection에서 node_id30 개체를 선택 합니다. 검사기 탭에서 구성 요소 추가를 클릭 하 고 경계 상자를 검색 합니다. 경계 상자, 상자 충돌체 및 조작 스크립트(조작 처리기, 근거리 잡기형 상호 작용)가 모두 동일한 게임 개체에 있는지 확인합니다.

3. 경계 상자의 동작 섹션에 있는 활성화 드롭다운 목록에서 시작 시 활성화를 선택 합니다. 다양 한 활성화 옵션 및 기타 경계 상자 옵션에 대 한 추가 정보를 검토 하려면 [Mrtk의 경계 상자 설명서](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html>) 를 참조 하세요.

    *다음 몇 단계에서는 기본 상자 자료를 조정 하 고, grabbed 하는 동안 재질을 조정 하 고, 모퉁이 및 측 핸들의 시각화를 조정 하 여 경계 상자를 어떻게 표시 하는 방법도 변경 합니다. MRTK에는 경계 상자를 사용자 지정 하기 위한 몇 가지 옵션이 포함 되어 있습니다.*

4. 프로젝트 패널에서 "boundingbox"를 검색 하면 아래 이미지와 같이 검색 결과에서 파란색 구로 표시 된 자료 목록이 표시 됩니다.

5. 경계 상자 구성 요소에서 boundingbox 재질을 box 재질 슬롯으로 끕니다. 또한 boundingboxgrabbed 재질을 잡고 경계 상자 구성 요소의 box grabbed 재질 슬롯에 놓습니다.

    ![mrlearning-base-ch4-3-step5](images/mrlearning-base-ch4-3-step5.png)

6. MRTK_BoundingBox_ScaleHandle prefab를 크기 조정 핸들 prefab 슬롯으로 끌고 MRTK_BoundingBox_RotateHandle를 결합 상자 구성 요소의 회전 핸들 슬롯으로 끕니다.

    ![mrlearning-base-ch4-3-step6](images/mrlearning-base-ch4-3-step6.png)

7. 경계 상자가 오른쪽 개체를 대상으로 하는지 확인합니다. 경계 상자 구성 요소에는 대상 개체 및 경계 재정의 스크립트가 있습니다. 경계 상자를 포함 하는 개체를 두 슬롯 모두로 끕니다. 이 예제에서는 아래 이미지에 나와 있는 것 처럼 node_id30 개체를 두 슬롯으로 끌어 옵니다.

    ![mrlearning-base-ch4-3-step7](images/mrlearning-base-ch4-3-step7.png)

    >[!NOTE]
    >응용 프로그램을 시작 하거나 재생할 때 개체는 파란색 프레임으로 둘러싸여 있습니다. 개체의 크기를 조정하려면 해당 프레임의 모서리를 끌면 됩니다. 크기 조정 핸들 및 회전 핸들이 더 크고 더 표시 되도록 하려면 기본 경계 상자 설정 (4 ~ 6 단계를 방지)을 사용 하는 것이 좋습니다.

8. 기본 경계 상자 시각화로 돌아가려면 경계 상자의 개체에 대 한 검사기 패널에서 회전 핸들 prefab을 선택 하 고 delete 키를 눌러 제거 합니다. 재생 모드로 전환 하면 wou에 아래 이미지와 비슷한 경계 상자 시각화가 표시 됩니다.

    ![mrlearning-base-ch4-3-step8](images/mrlearning-base-ch4-3-step8.png)

    >[!NOTE]
    >경계 상자 시각화는 재생 모드에 있을 때만 나타납니다.

## <a name="adding-touch-effects"></a>터치 효과 추가

이 예제에서는 손으로 개체를 터치할 때 사운드 효과를 재생합니다.

1. 오디오 원본 구성 요소를 게임 개체에 추가합니다. 장면 계층 구조에서 Octa 개체를 선택 합니다. 검사기 패널에서 구성 요소 추가 단추를 클릭 하 고 오디오 원본을 검색 한 다음 선택 합니다. 이 오디오 원본을 사용하여 이후 단계에서 사운드 효과를 재생합니다.

    >[!NOTE]
    >Octa 개체에 collider box가 있는지 확인 합니다.

2. Near 인터랙션 Touchable 구성 요소를 추가 합니다. 검사기 패널에서 구성 요소 추가 단추를 클릭 하 고 거의 상호 작용 touchable를 검색 합니다. 선택하여 구성 요소를 추가합니다.

    >[!NOTE]
    >이전에는 거의 상호 작용 grabbable를 추가 했습니다. 이와 거의 상호 작용 touchable의 차이점은 grabbable 상호 작용은 개체를 grabbed 하 고 상호 작용 하기 위한 것입니다. Touchable 구성 요소는 개체에 대 한 작업을 수행 하기 위한 것입니다. 두 구성 요소 모두 상호 작용의 조합을 위해 함께 사용할 수 있습니다.

    ![Lesson4 Chapter4 Step1 2Im](images/Lesson4_chapter4_step1-2im.PNG)

3. 직접 상호 작용 터치 스크립트에를 추가 합니다. 이전 단계와 마찬가지로 구성 요소 추가를 클릭 하 고 직접 상호 작용 터치를 검색 하 여 추가 합니다.

    스크립트에는 세 가지 옵션이 있습니다.
    * 터치 완료 시: 개체를 터치 하 고 해제할 때 트리거
    * 터치 시작 시: 개체가 작업 될 때 트리거
    * 터치 업데이트 시: 손을 개체와 접촉 하는 동안 주기적으로 트리거

    이 예에서는 Touch 시작 설정으로 작업 합니다.

    >[!NOTE]
    >이 스크립트는이 자습서의 시작 부분에서 가져온 BaseModuleAssets Unity 패키지에 포함 되어 있으며 원래 MRTK에는 포함 되어 있지 않습니다.

4. 터치 시작 옵션에서 + 단추를 클릭 하 고 Octa 개체를 빈 필드로 끕니다.

    ![mrlearning-base-ch4-4-step4](images/mrlearning-base-ch4-4-step4.png)

5. 함수가 없는 드롭다운에서 PlayOneShot를 > 선택 합니다. 아래 개념을 사용하여 오디오 클립을 이 필드에 추가하겠습니다.

    * MRTK는 오디오 클립의 작은 목록을 제공합니다. 프로젝트 패널에서 자유롭게 살펴볼 수 있습니다. MixedRealityToolkit > 표준 자산 > 오디오 폴더 > 자산 아래에서 찾을 수 있습니다.
    * 이 예에서는 MRTK_Gem 오디오 클립을 사용 합니다.
    * 오디오 클립을 추가 하려면 프로젝트 패널에서 원하는 클립을 PlayOneShot 필드로 끌기만 하면 됩니다.

    ![mrlearning-base-ch4-4-step5](images/mrlearning-base-ch4-4-step5.png)

   이제 사용자가 Octa 개체에 도달 하 여 접촉 하면 MRTK_Gem 오디오 트랙이 재생 됩니다. 또한 직접 상호 작용 터치 스크립트는 개체의 색을 조정 합니다.

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 그리드 컬렉션에서 3D 개체를 구성 하는 방법 및 거의 상호 작용 (추적 된 손으로 직접 이동) 및 먼 상호 작용 (응시 광선 또는 핸드 광선 사용)을 사용 하 여 이러한 개체를 조작 하는 방법 (크기 조정, 회전 및 이동)을 배웠습니다. 3D 개체 주위에 경계 상자를 배치 하는 방법 및 경계 상자에서 gizmo 그리려면를 사용 하 고 사용자 지정 하는 방법을 배웠습니다. 마지막으로 개체를 터치할 때 이벤트를 트리거하는 방법을 알아보았습니다.

[다음 단원: 6. 고급 입력 옵션 탐색](mrlearning-base-ch5.md)
