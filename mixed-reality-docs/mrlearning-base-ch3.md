---
title: 동적 콘텐츠 배치 하 고 적절 하 게 MR 학습 자료 모듈
description: 혼합된 현실 응용 프로그램에서 Azure Face recognition 얼굴 인식을 구현 하는 방법을 알아보려면이 과정을 완료 합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: unity, 자습서, hololens, 혼합된 현실
ms.openlocfilehash: 6f05b2cecd388b1b2f13e7e5228bc90091eee3bd
ms.sourcegitcommit: aba33a8ad1416f7598048ac35ae9ab1734bd5c37
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66270407"
---
# <a name="mr-learning-base-module---dynamic-content-placement-and-solvers"></a>동적 콘텐츠 배치 하 고 적절 하 게 MR 학습 자료 모듈

홀로그램은 직관적으로 사용자를 따라 하며 원활 하 고 세련 된 상호 작용 하는 방식으로 실제 환경에 배치 됩니다 때 HoloLens 2에서 제공 됩니다. 3 단원에서는 살펴봅니다 "해결사." 라고 MRTK의 가능한 배치 도구를 사용 하 여 홀로그램을 동적으로 배치 하는 방법을 복잡 한 공간 배치 알고리즘을 해결 하기 위해 방식에 대 한 "적절 하 게"으로 알려져 있습니다 이러한. MRTK를 적절 하 게에는 스크립트 및 동작을 따르도록, 사용자 또는 다른 게임 개체는 장면에서 UI 요소를 허용 하려면 사용 하는 시스템입니다. 데도 사용할 수 있습니다 특정 위치로 신속 하 게 맞춤에 응용 프로그램을 보다 직관적인 만드는 합니다. 

## <a name="objectives"></a>목표

* MRTK의 적절 하 게 소개
* 단추의 컬렉션을 사용 하 여 적절 하 게 사용자를 따릅니다.
* 게임 개체를 사용 하 여 적절 하 게 사용자의 추적된 실습을 수행 합니다.

## <a name="instructions"></a>지침

### <a name="location-of-solvers-in-the-mrtk"></a>MRTK에 적절 하 게의 위치
 프로젝트에서 사용할 수 해결사, utilities 폴더 아래의 다음 MRTK SDK 폴더 (MixedRealityToolkit.SDK 폴더)에 표시를 표시 됩니다 적절 하 게 폴더 아래 이미지에 표시 된 대로 합니다.

![해 찾기](images/lesson3_chapter1_step1im.PNG)

>참고: 이 단원의 살펴보겠습니다 "궤도" solver "RadialView" solver을 구현 합니다. 적절 하 게 된 MRTK에서 사용할 수 있는 전체 범위에 대 한 자세한 내용은 다음을 참조 하세요. https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html

### <a name="use-a-solver-to-follow-the-user"></a>사용자를 따라 해를 찾기 사용
이 장의 목표는 사용자의 게이즈 방향을 따릅니다 이전에 만든 단추 컬렉션을 향상 시키기 위해입니다. HoloToolkit 고 MRTK의 이전 버전에서는이 라고 했습니다 "taglong" 기능을 합니다.

1. 이전 단원에서 단추 컬렉션의 부모 개체를 선택 합니다.

![Lesson3 Chapter2 Step1im](images/Lesson3_chapter2_step1im.PNG)

2. 검사기 창에서 검색 "궤도." 고 "구성 요소 추가" 단추를 클릭 궤도 구성 요소가 표시 됩니다. 단추 컬렉션 게임 개체 궤도 구성 요소를 추가 하려면 선택 합니다.

![Lesson3 Chapter2 Step2im](images/Lesson3_Chapter2_step2im.PNG)

>참고: 구성 요소를 추가 하면 시스템 궤도 스크립트 및 solver 처리기 스크립트는 필수 구성 요소 검사기 탭에서 추가 함을 확인할 수 있습니다. 

3. 사용자를 따라 단추 컬렉션을 구성 하려면 다음과 같이 조정 구현 해야 (자신을 아래 이미지).
- 궤도 스크립트에서 "요에만 해당 합니다." "방향 유형" 드롭 다운 목록 설정 이렇게 하면 사용자 같이 개체의 해당 하나의 축 회전 하도록 합니다.
- 모든 축에서의 로컬 오프셋을 0으로 설정 합니다. X로 세계 오프셋 = 0, y-0.1 및 z = 0.6 =. 사용자 환경에 대 한 이동함에 따라 사용자를 수행 하도록 허용 하면서 개체 실제 환경에서 높이가 고정된에 남아 사용자 높이 변경 하는 경우는 개체의 이동이 잠깁니다. 다양 한 범위의 동작을 달성 하기 위해 이러한 값을 조정할 수 있습니다.
- 가능해 집니다 단추에만 수행 사용자 관점에서 사용자가 자신의 헤드를 충분히 멀리 설정 후에 다음 동작에 대해 "world 오프셋에 대 한 단계별 실행 사용 하 여 각도" 확인란을 선택할 수 있습니다 (참고: 이 제목은 잘릴 수 있습니다 일부 화면에서 아래 이미지에서는.) 예를 들어 사용자 90도 간격에 따라 개체를 집합 단계의 수 (왼쪽 예제에서 녹색 화살표로 표시 됨) 4와 같습니다. 

![Lesson3 Chapter2 Step3im](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a>추적 된 실습을 수행 하려면 개체를 사용 하도록 설정

이 섹션에서는 RadialView 해결 기를 사용 하 여 사용자의 추적된 실습을 수행 하려면 이전에 만든 큐브 게임 개체를 구성 됩니다.

1. BaseScene 계층의 큐브 개체를 선택 합니다. [관리자] 패널에서 "구성 요소 추가"를 클릭 합니다. 

![Lesson3 Chapter3 Step1im](images/Lesson3_Chapter3_step1im.PNG)

2. 검색 상자에 "RadialView"에 입력 하 고 큐브에 추가할 RadialView 구성 요소를 선택 합니다. Solver 처리기 구성 요소도 자동으로 추가 됩니다 큐브에 합니다.

3. 헤드 따르지 있지만 왼쪽을 따라 방사형 뷰를 변경 합니다. "개체 참조를 추적" 옵션 옆의 드롭다운 메뉴를 선택 합니다. 그런 다음 메뉴에서 "공동 왼쪽 전달"을 선택 합니다.

![Lesson3 Chapter3 Step3im](images/Lesson3_chapter3_step3im.PNG)

4. 직접 연결을 선택 하면 손 모양 아이콘이 부분 원하는 수행 하려면 큐브를 선택할 수 있습니다. 예를 들어 다음 손목 사용 하려고 합니다. 옵션 옆의 "추적된 직접 공동" 드롭다운 메뉴를 선택 하 고 손목을 선택 합니다. 

![Lesson3 Chapter3 Step4im](images/Lesson3_chapter3_step4im.PNG)

5. 큐브는 사용자의 손목 사이 거리 필요가 없도록 0으로 최대 및 최소 거리를 설정 합니다. 설정 되 면 큐브 완벽 하 게 맞춰집니다 손목 합니다. 또한 어떻게 큐브의 경우 방향 (예를 들어 사용자의 손목을 사용 하 여 회전, "방향으로 추적 한 개체" 참조 방향을 설정 개체를 허용 하려는)의 동작을 조정 하려면 "참조 방향" 필드를 조정할 수 있습니다.

![Lesson3 Chapter3 Step5im](images/Lesson3_chapter3_step5im.PNG)

### <a name="congratulations"></a>축 하.
축하합니다. 이 단원에서는 MRTK의 적절 하 게 직관적으로 사용자에 따라 ui를 사용 하는 방법을 알아보았습니다. 또한 사용자의 추적된 실습을 수행 하는 게임 개체 (예: 큐브)를 찾기가 연결 하는 방법을 배웠습니다. 이러한 및는 MRTK 포함 된 다른 해 찾기에 대 한 자세한 내용은 자유롭게 방문 하는 [MRTK 적절 하 게 설명서 페이지](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)합니다.

[다음 단원: 3D 개체 상호 작용](mrlearning-base-ch4.md)

