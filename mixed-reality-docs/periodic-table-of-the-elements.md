---
title: 요소의 정기적 테이블
description: 요소의 정기적 테이블에는 Microsoft의 혼합 현실 디자인 실습 개체 컬렉션을 사용 하 여 다양 한 화면 형식을 사용 하 여 3D 공간에서 개체의 배열에 배치 하는 방법을 알아보십시오 오픈 소스 샘플 앱입니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality를 디자인, 샘플 앱, 컨트롤
ms.openlocfilehash: ad95d2bcfd1b70d805adcceb36be0c6c29b838f0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604113"
---
# <a name="periodic-table-of-the-elements"></a>요소의 정기적 테이블

>[!NOTE]
>이 문서에서 설명 하는 예비 샘플에 설명 합니다 [혼합 현실 디자인 Labs](https://github.com/Microsoft/MRDesignLabs_Unity)에 대 한 학습 공유 하는 위치 및 제안에 대 한 혼합 현실 앱 개발. 이 디자인 관련 문서 및 코드에는 새 검색 우리가 발전할 합니다.

[요소의 정기적 테이블](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) 은 Microsoft의 혼합 현실 디자인 실습에서 오픈 소스 샘플 앱입니다. 이 프로젝트와 함께 3D 공간에서 개체의 배열을 사용 하 여 다양 한 화면 형식에 배치 하는 방법을 알아볼 수 있습니다는  **[개체 컬렉션](object-collection.md)** 합니다. 또한 HoloLens에서 표준 입력에 응답 하는 상호 작용할 수 없는 개체를 만드는 방법을 알아봅니다. 혼합 현실 앱 환경을 직접 만들어야이 프로젝트의 구성이 요소를 사용할 수 있습니다.

![요소 앱의 기간 테이블](images/640px-periodictable-hero.jpg)

## <a name="about-the-app"></a>앱에 대 한

요소의 정기적 테이블 화학 물 요소 및 각 3D 공간에서 해당 속성을 시각화합니다. 응시 및 air 탭 같은 HoloLens의 기본 상호 작용을 통합 합니다. 애니메이션이 적용 된 3D 모델을 사용 하 여 요소에 대 한 사용자 수에 대해 알아봅니다. 요소의 전자 셸 및 양성자 및 neutrons로 구성 된 해당 이기-시각적으로 이해할 수 있습니다.

## <a name="background"></a>배경

HoloLens, 먼저 양상이 주기적 table 앱 혼합된 현실에서 실험 하려고 하는 것이 필자의 아이디어가 했습니다. 각 요소에 텍스트를 사용 하 여 표시 되는 많은 데이터 요소, 3D 공간에서 인쇄 컴퍼지션을 탐색 하는 데 유용한 주제 것 생각 했습니다. 이 프로젝트의 다른 흥미로운 부분은 된 시각화 요소의 전자 모델 수입니다.

## <a name="design"></a>디자인

주기적 테이블의 기본 보기의 경우 내를 포함 하는 각 요소의 전자 모델 3 차원 상자 생각 합니다. 사용자 요소의 볼륨의 대략적인 아이디어를 얻을 수 있도록 각 상자의 화면 반투명 것입니다. 응시 및 air 탭을 사용 하 여 사용자의 각 요소에 대해 자세히 예기치 발생할 수 있습니다. 테이블 뷰 및 세부 정보 보기 간 전환을 원활 하 고 자연 스러운가 하도록 만들었습니다 실생활에서 열기 상자 물리적 상호 작용 비슷합니다.

![디자인 스케치](images/640px-sketch20170406.jpg)<br>
*디자인 스케치*

자세히 보기 상태의 3D 공간에서 멋지게 렌더링 된 텍스트를 사용 하 여 각 요소의 정보를 시각화 하고자 했습니다. 애니메이션이 적용 된 3D 전자 모델 가운데 영역에서 표시 되 고 다른 관점에서 볼 수 있습니다.

![조작](images/640px-periodictable-interaction.jpg)

![프로토타입](images/640px-periodictable-prototypes.jpg)<br>
*상호 작용 프로토타입*

사용자 테이블의 아래쪽에 있는 단추 탭으로 화면 형식을 변경할 수-평면, 원통형, 구 및 분산형 간에 전환할 수 있습니다.

## <a name="common-controls-and-patterns-used-in-this-app"></a>공용 컨트롤 및이 앱에서 사용 되는 패턴

### <a name="interactable-object-button"></a>상호 작용할 수 없는 개체 (단추)

[상호 작용할 수 없는 개체](interactable-object.md) 는 기본 HoloLens 입력에 응답할 수 있는 개체입니다. 모든 개체에 쉽게 적용할 수 있는 prefab 스크립트로 제공 됩니다. 예를 들어, 커피 cup 장면에서 상호 작용할 수 없는 응시, 어 탭 제스처를 탐색 및 조작 등의 입력에 응답 합니다. [자세히 알아보기](interactable-object.md)

![nteractable 개체](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a>개체 컬렉션

[개체 컬렉션](object-collection.md) 개체인 다양 한 모양의 여러 개체를 레이아웃 하는 데 도움이 됩니다. 평면, 원통형, 구 및 분산형 지원합니다. Radius, 행 및 간격 수가 같은 추가 속성을 구성할 수 있습니다. [자세히 알아보기](object-collection.md)

![개체 컬렉션](images/640px-periodictable-collections.jpg)

### <a name="fitbox"></a>Fitbox

사용자는 gazing 있는 위치에 배치 됩니다 홀로그램 기본적으로 현재 응용 프로그램이 시작 됩니다. 이 경우에 따라 홀로그램 벽 뒤 또는 테이블을 가운데에 배치 되 고 같은 원치 않는 결과로 이어집니다. fitbox 게이즈를 홀로그램을 배치할 위치를 결정 하는 데 있습니다. 사용자 고유의 이미지 또는 3D 개체를 사용 하 여 손쉽게 사용자 지정할 수 있는 간단한 PNG 이미지 질감으로 구성 됩니다.

![Fitbox](images/450px-periodictable-fitbox.jpg)

## <a name="technical-details"></a>기술 세부 정보

스크립트 및 있습니다 prefabs 요소 앱의 정기적 테이블에 [혼합 현실 디자인 Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)합니다.

## <a name="application-examples"></a>응용 프로그램 예제

이 프로젝트의 구성 요소를 활용 하 여 만들 수에 대 한 몇 가지 아이디어는 다음과 같습니다.

### <a name="stock-data-visualization-app"></a>주식 데이터 시각화 앱

동일한 컨트롤과 상호 작용 모델을 사용 하 여 요소 샘플 주기적 테이블로, 주식 시장 데이터를 시각화 하는 앱을 빌드할 수 있습니다. 이 예제에서는 구면 셰이프에서 주식 데이터를 레이아웃할 수 개체 컬렉션 컨트롤을 사용 합니다. 흥미로운 방식으로 각 주식에 대 한 추가 정보를 표시할 수 있는 세부 정보 보기를 상상할 수 있습니다.

![응용 프로그램 예제: 재무 (1 / 3)](images/640px-periodictable-applicationexamples-finance1.jpg)

![응용 프로그램 예제: 재무 (2 / 3)](images/640px-periodictable-applicationexamples-finance2.jpg)

![응용 프로그램 예제: 재무 (3 / 3)](images/640px-periodictable-applicationexamples-finance3.jpg)<br>
*요소 샘플 앱의 정기적 테이블에 사용 되는 개체 컬렉션 재무 응용 프로그램에서 어떻게 사용할 수 있습니다의 예*

### <a name="sports-app"></a>스포츠 앱

이것이 스포츠 데이터 개체 컬렉션 및 기타 구성 요소 샘플 앱의 정기적 테이블에서 요소를 사용 하 여 시각화의 예입니다.

![응용 프로그램 예제: 스포츠 (1 / 3)](images/640px-periodictable-applicationexamples-sports0.jpg)

![응용 프로그램 예제: 스포츠 (2 / 3)](images/640px-periodictable-applicationexamples-sports1.jpg)

![응용 프로그램 예제: 스포츠 (3 / 3)](images/640px-periodictable-applicationexamples-sports3.jpg)<br>
*요소 샘플 appcould의 주기적 테이블에 있는 개체 컬렉션을 사용 하는 방법의 예로 스포츠 앱에서 사용할 수*

## <a name="about-the-author"></a>저자 소개

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>했어요 Yoon Park</b><br>UX 디자이너 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>참조

* [상호 작용할 수 없는 개체](interactable-object.md)
* [개체 컬렉션](object-collection.md)
