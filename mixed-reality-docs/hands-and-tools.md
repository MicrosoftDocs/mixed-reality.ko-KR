---
title: 직접 및 동작 컨트롤러
description: 직접 및 동작 컨트롤러 상호 작용 개요
author: shengkait
ms.author: shentan
ms.date: 04/26/2019
ms.topic: article
keywords: 혼합 현실, 손, 움직임 컨트롤러, 상호 작용, 디자인
ms.openlocfilehash: 27d13316bbc4b3b40a1e617d73dd5487c05cb347
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334441"
---
# <a name="hands-and-motion-controllers"></a>직접 및 동작 컨트롤러
## <a name="scenarios"></a>시나리오
[상호 작용 개요](interaction-fundamentals.md)를 읽은 후이 상호 작용 모델을 채택 하도록 선택 하는 경우 사용자가 holographic와 상호 작용 하는 데 두 개의 손을 사용 하도록 요구 하는 응용 프로그램을 개발 하 고 있음을 의미 합니다. 응용 프로그램은 가상과 물리적 간의 경계를 제거 하는 목표를 달성 하 게 됩니다.

몇 가지 특정 시나리오는 다음과 같습니다.
* UI affordances를 사용 하 여 콘텐츠를 표시 및 제어 하는 정보 근로자 2D 가상 화면 제공
* 팩터리 어셈블리 줄에 대 한 첫 번째 줄 작업자 자습서 및 가이드 제공
* 의료 전문가 지원 및 교육을 위한 전문 도구 개발  
* 3D 가상 개체를 사용 하 여 실제 세계를 장식 하거나 두 번째 세계를 만듭니다. 
* 실제 세계를 배경으로 사용 하 여 위치 기반 서비스 및 게임 만들기

<br>

---

## <a name="hands-and-motion-controllers-modalities"></a>손 및 동작 컨트롤러 소프트웨어나

:::row:::
    :::column:::
       [손으로 직접 조작 ![](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)<br>
       ### <a name="direct-manipulation-with-handsdirect-manipulationmdbr"></a>[수동으로 직접 조작](direct-manipulation.md)<br>
       이는 사용자가 직접 holograms를 터치 하 고 조작할 수 있는 손을 활용 하는 것입니다. 일상의 경험을 활용 하 고 적절 한 시각적 affordances 제공 함으로써 사용자는 실제 개체를 조작 하는 동일한 방법을 사용 하 여 가상 항목과 상호 작용할 수 있습니다.
    :::column-end:::
    :::column:::
       [손을 사용 하 여 ![지점 및 커밋](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)<br>
        ### <a name="point-and-commit-with-handspoint-and-commitmdbr"></a>[수동으로 가리키고 커밋](point-and-commit.md)<br>
        이를 통해 사용자는 거리가 holograms 상호 작용할 수 있습니다. 사용자가 주변 환경을 최대한 활용할 수 있도록 합니다. 사용자는 어디 든 지 holograms를 배치할 수 있으며 모든 거리에서 계속 액세스할 수 있습니다. 2D 및 3D holograms을 제어 하 고 조작 하기 위한 멘 탈 모델 및 제스처는 직접 조작의 경우와 매우 동기화 됩니다.
    :::column-end:::
    :::column:::
       [![동작 컨트롤러](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)<br>
       ### <a name="motion-controllersmotion-controllersmdbr"></a>[모션 컨트롤러](motion-controllers.md)<br>
       동작 컨트롤러는 하나 또는 두 손을 모두 사용 하는 동시에 다 수의 거리에서 정확한 상호 작용을 제공 하 여 사용자의 물리적 기능을 확장 하는 도구입니다. 이러한 하드웨어 액세서리는 널리 사용 되는 다양 한 상호 작용에 대 한 바로 가기를 제공 하 고 다양 한 작업에 대 한 tactile 피드백을 제공 합니다. 현재 동작 컨트롤러는 WMR (Windows Mixed Reality) 시나리오 에서만 사용할 수 있습니다. 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a>참고 항목
* [헤드 게이즈 및 커밋](gaze-and-commit.md)
* [헤드 게이즈 및 유지](gaze-and-dwell.md)
* [수동으로 직접 조작](direct-manipulation.md)
* [수동으로 가리키고 커밋](point-and-commit.md)
* [핸즈프리](hands-free.md)
