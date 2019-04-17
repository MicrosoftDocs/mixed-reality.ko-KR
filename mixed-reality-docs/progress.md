---
title: 진행률 표시
description: 진행률 컨트롤은 긴 작업을 진행 중인 사용자에게 피드백을 제공합니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, ux, ui, 컨트롤, 디자인
ms.openlocfilehash: 9edddc7800f0d7334d1ceba97b9a06fd6d4580ac
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603214"
---
# <a name="displaying-progress"></a>진행률 표시

진행률 컨트롤은 긴 작업을 진행 중인 사용자에게 피드백을 제공합니다. 이는 진행률 표시기가 표시될 때 사용자가 앱을 조작할 수 없다는 의미이며 사용되는 표시기에 따라 대기 시간을 예측할 수도 있다는 의미입니다.

![HoloLens에 진행률 링 예제](images/640px-progress-hero.jpg)<br>
*HoloLens에 진행률 링 예제*

## <a name="types-of-progress"></a>진행률 유형

상황에 대 한 사용자 정보를 제공 하는 것이 반드시 합니다. 혼합된 현실에서 사용자 수 수 쉽게 사항 물리적 환경 또는 개체 앱은 하지 제공 좋은 시각적 피드백 경우. 몇 초를 사용 하는 경우에 대 한 데이터를 로드 하는 경우와 같이 또는 장면에서 업데이트 하는, 시각적 표시기를 표시 하는 것입니다. 작업 진행 중-임을 사용자에 게 표시할 두 가지는 **진행률 표시줄이** 또는 **진행률 링**합니다.

### <a name="progress-bar"></a>진행률 표시줄

![HoloLens에 진행률 표시줄 예제](images/640px-progressbar.jpg)

진행률 표시줄을 작업의 완료 백분율을 보여 줍니다. 작업 시간 (비활성화 상태) 라고 하는 동안 사용 해야 하지만 진행률의 앱을 사용 하 여 사용자의 상호 작용을 차단 하지 않아야 합니다.

### <a name="progress-ring"></a>진행률 링

![HoloLens에 진행률 링 예제](images/640px-progressring.jpg)

진행률 링만 결정 되지 않은 상태 여 서 있으며 추가 사용자 상호 작용은 작업이 완료 될 때까지 차단 되는 경우 사용 해야 합니다.

### <a name="progress-with-a-custom-object"></a>사용자 지정 개체를 사용 하 여 진행률

![HoloLens에 사용자 지정 메시 예제를 사용 하 여 진행률](images/640px-progresscustom.jpg)

사용자 고유의 사용자 지정 2D/3D 개체를 사용 하 여 진행률 컨트롤을 사용자 지정 하 여 앱의 개성과 브랜드 id에 추가할 수 있습니다.

## <a name="best-practices"></a>모범 사례
* 긴밀 하 게 결합 [빌보드 또는 tag-along](billboarding-and-tag-along.md) 쉽게 해당 헤드 빈 공간으로 이동 하 고 상황에 맞는 손실 수 사용자 이므로 진행률 표시. 앱이에서 반복적인 충돌이 발생 하면 아무 것도 볼 수 없는 경우 처럼 보일 수 있습니다. Billboarding 및 tag-along 진행률 prefab에 빌드됩니다.
* 항상 사용자에 게 상황에 대 한 상태 정보를 제공 하는 것이 적합 합니다. 진행률 prefab 상태를 제공 하는 데 Windows 표준 링 형식 진행 상황 비롯 한 다양 한 시각적 스타일을 제공 합니다. 또한 앱의 브랜드에 맞게 진행 상황의 스타일을 원하는 경우 애니메이션을 사용 하 여 메시를 사용자 지정을 사용할 수 있습니다.

## <a name="see-also"></a>참조
* [스크립트 및 혼합 현실 도구 키트에는 진행률에 대 한 prefabs](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_ProgressExample.md)
* [상호 작용할 수 없는 개체](interactable-object.md)
* [개체 컬렉션](object-collection.md)
* [빌보드 및 tag-along](billboarding-and-tag-along.md)
