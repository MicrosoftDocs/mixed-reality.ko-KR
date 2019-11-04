---
title: 자습서-4를 시작 합니다. 동적 콘텐츠 배치 및 solvers 사용
description: 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 알아보려면 이 과정을 완료합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, Hololens
ms.openlocfilehash: 93fcdcdfb7941f377b2f3f7786368783415b1ef2
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438410"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a>4. 동적 콘텐츠 배치 및 solvers 사용

Holograms은 사용자가 직관적이 고 원활 하 게 상호 작용 하는 방식으로 실제 환경에 배치 되는 경우 HoloLens 2를 사용 합니다. 이 자습서에서는 MRTK의 사용 가능한 배치 도구 (solvers)를 사용 하 여 동적으로 holograms을 배치 하 여 복잡 한 공간 배치 시나리오를 해결 하는 방법을 알아봅니다. MRTK에서 solvers는 UI 요소에서 사용자, 사용자 또는 장면의 기타 게임 개체를 팔 로우 하는 데 사용 되는 스크립트 및 동작의 시스템입니다. 특정 위치로 빠르게 스냅하여 애플리케이션을 보다 직관적인 만드는 데 사용할 수도 있습니다. 

## <a name="objectives"></a>목표

* MRTK 해결기 소개
* 해결기를 사용하여 단추 컬렉션이 사용자를 따르도록 하기
* 해결기를 사용하여 게임 개체가 사용자의 추적된 손을 따르도록 하기

## <a name="instructions"></a>지침

### <a name="location-of-solvers-in-the-mrtk"></a>MRTK에서 해결기의 위치
 프로젝트에서 사용 가능한 solvers를 찾으려면 MRTK SDK 폴더 (MixedRealityToolkit 폴더)를 확인 합니다. 유틸리티 폴더 아래 이미지에 표시 된 것 처럼 solvers 폴더가 표시 됩니다.

![해결기](images/lesson3_chapter1_step1im.PNG)

>참고:이 단원에서는 궤도 나 RadialView 시도의 구현만 검토 합니다. MRTK에서 사용할 수 있는 solvers의 전체 범위에 대해 자세히 알아보려면 다음을 방문 하세요. https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html

### <a name="use-a-solver-to-follow-the-user"></a>해결기를 사용하여 사용자 따르기
이 장의 목표는 사용자의 응시 방향을 따라가는 이전에 만든 단추 컬렉션을 개선 하는 것입니다. 이전 버전의 MRTK 및 HoloToolkit에서는이를 tagalong 기능 이라고 했습니다.

1. 이전 단원의 Button Collection 부모 개체를 선택합니다.

![Lesson3 Chapter2 Step1im](images/Lesson3_chapter2_step1im.PNG)

2. 검사기 패널에서 구성 요소 추가 단추를 클릭 하 고 궤도를 검색 합니다. 궤도 구성 요소가 표시 됩니다. 이를 선택 하 여 궤도 구성 요소를 단추 컬렉션 게임 개체에 추가 합니다.

![Lesson3 Chapter2 Step2im](images/Lesson3_Chapter2_step2im.PNG)

>참고: 궤도 구성 요소를 추가 하면 시스템에서 필수 구성 요소인 SolverHandler 구성 요소도 추가 됩니다. 

3. 사용자를 따르도록 단추 컬렉션을 구성 하려면 다음 조정을 구현 해야 합니다 (아래 이미지 참조).
- 궤도 스크립트에서 방향 유형 드롭다운 목록을 요 Only로 설정 합니다. 이렇게 하면 사용자를 따를 때 개체의 축 하나만 회전합니다.
- 모든 축에서 Local Offset을 0으로 설정합니다. 전역 오프셋을 x = 0, y =-0.1 및 z = 0.6로 설정 합니다. 이렇게 하면 개체의 이동이 잠기므로 사용자가 높이를 변경 하는 경우 개체는 실제 환경에서 고정 높이로 유지 되 고 사용자가 환경에 대해 이동할 때 계속 사용자를 따르도록 허용 합니다. 다양한 범위의 동작을 달성하기 위해 이러한 값을 조정할 수 있습니다.
- 사용자가 자신의 머리를 충분히 멀리 전환 하 고 나 서 단추를 클릭 한 후에도 사용자의 보기를 따라 이동 하는 동작을 위해 전 세계 오프셋에 각도 스테핑 사용 확인란을 선택할 수 있습니다 (참고: 아래 이미지에 나와 있는 것 처럼 일부 화면에서는이 제목이 잘릴 수 있음). 예를 들어 개체가 90도 마다 사용자를 따르도록 하려면 단계 수를 4로 설정 합니다 (아래 예제에서는 녹색 화살표로 표시 됨). 

![Lesson3 Chapter2 Step3im](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a>추적 된 손을 따르도록 개체 활성화

이 섹션에서는 RadialView 해를 사용 하 여 사용자의 추적 된 손을 따르도록 이전에 만든 Cube game 개체를 구성 합니다.

1. BaseScene 계층 구조에서 큐브 개체를 선택 합니다. 검사기 패널에서 구성 요소 추가를 클릭 합니다. 

![Lesson3 Chapter3 Step1im](images/Lesson3_Chapter3_step1im.PNG)

2. 검색 상자에 RadialView를 입력 하 고 RadialView 구성 요소를 선택 하 여 큐브에 추가 합니다. SolverHandler 구성 요소도 큐브에 자동으로 추가 됩니다.

3. RadialView를 헤드 대신 왼쪽 뒤에 있도록 변경 하려면 참조할 추적 된 개체 옵션 옆에 있는 드롭다운 메뉴를 선택 하 고 메뉴에서 왼쪽 연결점을 선택 합니다.

![Lesson3 Chapter3 Step3im](images/Lesson3_chapter3_step3im.PNG)

4. 손 관절을 선택하고 나면, 큐브가 따르도록 하려는 손 부분을 선택할 수 있습니다. 이 예제에서는 손목을 사용하려고 합니다. 추적 된 조인트 옵션 옆에 있는 드롭다운 메뉴를 선택 하 고 손목를 선택 합니다. 

![Lesson3 Chapter3 Step4im](images/Lesson3_chapter3_step4im.PNG)

5. 큐브와 사용자의 손목 사이에 거리가 없도록 최대 및 최소 거리를 0으로 설정합니다. 일단 설정하면 큐브는 손목에 완벽하게 맞춰집니다. 참조 방향을 추적 된 개체의 방향으로 설정 하 여 개체를 사용자의 손목로 회전할 수 있도록 하려는 경우와 같이 큐브 지향 방법의 동작을 조정 하는 참조 방향 필드를 조정할 수도 있습니다.

![Lesson3 Chapter3 Step5im](images/Lesson3_chapter3_step5im.PNG)

## <a name="congratulations"></a>축하합니다.
이 자습서에서는 MRTK의 solvers를 사용 하 여 UI가 사용자를 직관적으로 따르도록 하는 방법을 배웠습니다. 또한 해결기를 게임 개체(예: 큐브)에 연결하여 사용자의 추적된 손을 따르도록 하는 방법도 알아보았습니다. 이러한 해결기 및 MRTK에 포함된 다른 해결기에 대한 자세한 내용은 [MRTK 해결기 설명서 페이지](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)를 참조하세요.

[다음 단원: 5.3D 개체와 상호 작용](mrlearning-base-ch4.md)

