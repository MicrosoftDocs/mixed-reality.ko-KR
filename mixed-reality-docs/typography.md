---
title: 입력 체계
description: 텍스트에는 앱 환경에서 정보를 제공 하기 위한 중요 한 요소입니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality를 디자인, 스타일, 글꼴, 입력 체계, ui, ux
ms.openlocfilehash: cc8e25e9cd7ba41bed179328fe7198e935e65d76
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66830009"
---
# <a name="typography"></a>입력 체계

텍스트에는 앱 환경에서 정보를 제공 하기 위한 중요 한 요소입니다. 2D 화면에서 입력 체계에서와 마찬가지로 목표를 명확 하 고 읽을 수 있는입니다. 혼합된 현실의 3 차원 모양 텍스트와 전체 사용자에 영향을 줄 수 있는 기회는 더 높은 방식으로 경험 합니다.

![HoloLens의 입력 체계 예제](images/typography-cover.png)<br>
*HoloLens의 입력 체계 예제*

3d에서 형식에 대 한 이야기 하는 경우 대규모 입체 3D 텍스트를 생각 하는 경향이 있습니다. 일부 로고 형식 디자인 및 제한 된 응용 프로그램을 제외 하 고 돌출 된 텍스트는 텍스트의 가독성을 저하 경향이 있습니다. 3D에 대 한 환경을 설계를 하는 경우에 사용 2D 유형에 대 한 더 읽을 수이 고 쉽게 읽을 수 있기 때문에 합니다.

HoloLens, 종류는 가산적 색 시스템에 따라 light를 사용 하 여 홀로그램을 사용 하 여 생성 됩니다. 다른 홀로그램 마찬가지로 형식 world 잠기고 모든 각도에서 관찰 될 수 있는 실제 환경에 배치할 수 있습니다. 합니다 [시차](https://en.wikipedia.org/wiki/Parallax) 형식과 환경 효과 또한 깊이 환경에 추가 합니다.

## <a name="typography-in-mixed-reality"></a>혼합된 현실의 입력 체계

혼합된 현실에서 인쇄 규칙은 다른 곳 다르지 않습니다. 가상 세계와 실제 텍스트를 읽을 수 하 고 읽을 수 있어야 합니다. 텍스트나 벽에 있을 수는 실제 개체 위에 나타납니다. 디지털 사용자 인터페이스와 함께 부동 수 없습니다. 컨텍스트에 관계 없이 읽고 인식에 대 한 동일한 인쇄 규칙을 적용 했습니다.

### <a name="create-clear-hierarchy"></a>일반 계층 만들기

다양 한 형식 크기와 가중치를 사용 하 여 대비 및 계층 구조를 빌드하십시오. 형식 확장을 정의 하 고 앱 환경 전체에서 그 다음에 일관 된 정보 계층을 사용 하 여 뛰어난 사용자 환경을 제공 합니다.

![형식 진입 예제](images/typography-ramp-1000px.jpg)<br>
*에 형식 확장을 정의 하 고 앱 환경 전체에서 그 뒤에*

### <a name="limit-your-fonts"></a>해당 글꼴이 제한

단일 컨텍스트에서 두 개 이상의 다양 한 글꼴 패밀리를 사용 하지 마십시오. 사용자 경험의 일관성 및 조화 중단 되 고 정보를 사용 하기가 어려워집니다. HoloLens에서 너무 많은 글꼴 스타일을 사용 하 여 실제 환경에서 기반으로 정보는 중첩 하므로 환경이 저하 됩니다. Segoe UI에는 모든 Microsoft 디지털 디자인에 대 한 글꼴입니다. Windows Mixed Reality 셸에서 일관 되 게 사용 됩니다. Segoe UI 글꼴 파일을 다운로드할 수 있습니다 합니다 [toolkit 페이지를 디자인 하는 Windows](https://docs.microsoft.com/windows/uwp/design-downloads/)합니다.

[Segoe UI 서체에 대 한 자세한 정보](https://docs.microsoft.com/windows/uwp/design/style/typography)

### <a name="avoid-thin-font-weights"></a>씬 글꼴 두께 방지 합니다.

씬 세로 획 진동 되며 읽기 쉽도록 코멘트가 저하 되므로 42pt 아래 형식 크기에 대 한 간단한 또는 semilight 글꼴 두께 사용 하지 마십시오. 충분 한 스트로크 두께 사용 하 여 최신 글꼴 잘 작동 합니다. 예를 들어, Helvetica Arial와 매우 HoloLens에서 읽을 수 일반 또는 굵게 표시 된 가중치를 사용 하 여입니다.

### <a name="color"></a>색

HoloLens에서 홀로그램 가산적 간단한 시스템을 사용 하 여 생성 된 흰색 텍스트 이므로 항상 읽을 수 있습니다. 시작 메뉴에서 앱 바에 흰색 텍스트의 예제를 찾을 수 있습니다. HoloLens에 흰색 텍스트 백 접시 없이 잘 작동 하는 경우에 복잡 한 실제 배경이 만들 수 있습니다 형식 읽기 어렵습니다. 사용자의 포커스를 개선 및 실제 백그라운드에서 혼란을 최소화, 어둡게 또는 색이 지정 된 다시 판에 흰색 텍스트를 사용 하는 것이 좋습니다.

<br>


![어두운 또는 색이 지정 된 백 판에 흰색 텍스트를 사용 하는 것이 좋습니다. ](images/typography-whiteonblack2-1000px.jpg)
 *어둡게 또는 색이 지정 된 백 판에 흰색 텍스트의 예입니다.*
<br>

어두운 텍스트를 사용 하려면 읽을 수 있도록 밝은 백 접시를 사용 해야 합니다. 가산적 색 시스템 검정 투명 하 게 표시 됩니다. 즉, 접시를 다시는 컬러 없이 검정 텍스트를 볼 수 없습니다.

![검정 텍스트 예제](images/typography-whiteonblack.png)
<br>*백에서 흰색과 검정색 흰색 텍스트의 예*


![검정 텍스트 예제](images/640px-typography-blackonwhite.jpg)
<br>*시스템 앱-저장소 및 설정의에서 검정 텍스트의 예*

## <a name="recommended-font-size"></a>권장 되는 글꼴 크기

예상할 수 있듯이 PC 또는 태블릿 장치 (일반적으로 12 – 32pt) 사이 사용 하는 형식 크기 2 미터 거리 만큼 떨어진 좁습니다 찾습니다. 각 글꼴의 특성에 다르지만 0.35°-0.4°/12.21-13.97mm 사용자 연구 조사의에 따라 권장 되는 보기 각도 및 읽기 쉽도록 코멘트가 글꼴 높이 최소는 일반적입니다. 에 도입 된 배율 인수를 사용 하 여 35 40pt 것 [Unity에서 텍스트](text-in-unity.md) 페이지입니다. 

거의 상호 작용 0.45m(45cm)에 최소 읽을 수 글꼴 각도 높이 0.4 °-0.5 ° / 3.14 – 3.9 mm 합니다. 에 도입 된 배율 인수를 사용 하 여 9 12pt 것 [Unity에서 텍스트](text-in-unity.md)합니다.

![가까운과 먼 상호 작용 범위](images/typography-distance-1000px.jpg)
*근처에서 콘텐츠와 먼 상호 작용 범위*

### <a name="the-minimum-legible-font-size"></a>읽을 수 있는 최소 글꼴 크기
| 거리 | 각도 | 텍스트 높이 | 글꼴 크기 * * |
|---------|---------|---------|---------|
| 45 cm (직접 조작 거리) | 0.4°-0.5° | 3.14–3.9mm | 8.9–11.13pt |
| 2m | 0.35°-0.4° | 12.21 – 13.97 mm | 34.63-39.58pt |


### <a name="the-comfortably-legible-font-size"></a>편안 하 게 읽을 수 글꼴 크기
| 거리 | 각도 | 텍스트 높이 | 글꼴 크기 * * |
|---------|---------|---------|---------|
| 45 cm (직접 조작 거리) | 0.65°-0.8° | 5.1-6.3mm | 14.47-17.8pt |
| 2m | 0.6°-0.75° | 20.9-26.2mm | 59.4-74.2pt |


Segoe UI (Windows에 대 한 기본 글꼴) 대부분의 경우 잘 작동합니다. 그러나 씬 세로 스트로크는 진동 이므로 가독성을 저하 시킵니다 작은 크기로 light 또는 semi 밝은 글꼴 패밀리를 사용 하지 마십시오. 충분 한 스트로크 두께 사용 하 여 최신 글꼴 잘 작동 합니다. 예를 들어, Helvetica Arial 멋진 확인 및 일반 또는 굵게 표시 된 가중치를 사용 하 여 HoloLens에 매우 읽을 수 있습니다.

* * 자세한 Unity에서 텍스트 크기 계산에 대 한 정보를 참조 하십시오 페이지로 [Unity에는 텍스트](text-in-unity.md)

![시야각](images/Text_In_Unity_ViewingAngle.jpg)
*거리, 각도 및 텍스트 높이 보기*

## <a name="resources"></a>리소스
* [Segoe 글꼴](http://download.microsoft.com/download/1/B/C/1BCF071A-78EE-4968-ACBE-15461C274B61/Segoe%20fonts%20v1705.zip)
* [HoloLens 글꼴](http://download.microsoft.com/download/3/8/D/38D659E2-4B9C-413A-B2E7-1956181DC427/Hololens%20font.zip)

![HoloLens 글꼴을 사용 하면 Windows Mixed Reality에 사용 되는 기호 문자 모양](images/300px-hololensmdl2symbols.jpg)
<br>*HoloLens 글꼴 Windows Mixed Reality에 사용 되는 기호 문자 모양을 제공 합니다.*

## <a name="see-also"></a>참조
* [Unity의 텍스트](text-in-unity.md)
* [색, 광원 및 재질](color,-light-and-materials.md)
