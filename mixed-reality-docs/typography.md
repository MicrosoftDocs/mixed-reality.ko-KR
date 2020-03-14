---
title: 입력 체계
description: 텍스트는 앱 환경에서 정보를 전달 하는 데 중요 한 요소입니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality, 디자인, 스타일, 글꼴, 입력 체계, ui, ux
ms.openlocfilehash: 9664d355e941d800ac1ac862860fc5889b6b7686
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375800"
---
# <a name="typography"></a>입력 체계

![HoloLens의 입력 체계 예제](images/typography-cover.png)<br>


텍스트는 앱 환경에서 정보를 전달 하는 데 중요 한 요소입니다. 2D 화면의 입력 체계처럼 목표는 명확하고 읽기 쉬운 것입니다. 혼합 현실의 3차원 측면에서는 텍스트와 사용자 환경 전체에 훨씬 더 큰 영향을 줄 수 있는 기회가 있습니다.

3D의 유형에 대 한 정보를 제공 하는 경우 입체 대규모 3D 텍스트를 생각 하는 경향이 있습니다. 일부 로고 형식 디자인 및 몇 가지 다른 제한 된 응용 프로그램을 제외 하 고, 입체 텍스트는 텍스트의 가독성을 저하 하는 경향이 있습니다. 3D에 대 한 환경을 디자인 하는 경우에도 형식에 대해 2D를 사용 합니다 .이는 읽기 쉽고 읽기 쉽습니다.

HoloLens에서 덧셈 색 시스템을 기반으로 하는 holograms를 사용 하 여 유형이 생성 됩니다. 다른 holograms와 마찬가지로, 모든 각도에서 세계를 잠그고 관찰할 수 있는 실제 환경에 형식을 배치할 수 있습니다. 형식과 환경 간의 [시차](https://en.wikipedia.org/wiki/Parallax) 효과는 또한 경험에 깊이를 추가 합니다.

## <a name="typography-in-mixed-reality"></a>혼합 현실의 입력 체계

혼합 현실의 입력 규칙은 다른 위치와는 다릅니다. 물리적 세계와 가상 환경의 텍스트는 읽고 읽을 수 있어야 합니다. 텍스트는 벽에 있거나 물리적 개체 위에 있을 수 있습니다. 디지털 사용자 인터페이스와 함께 떠 있을 수 있습니다. 컨텍스트에 관계 없이 읽기 및 인식에 동일한 입력 규칙을 적용 합니다.

### <a name="create-clear-hierarchy"></a>Clear 계층 만들기

서로 다른 형식 크기와 가중치를 사용 하 여 대비 및 계층 구조를 작성 합니다. 앱 환경 전체에서 유형 램프를 정의 하 고 그 다음에는 일관 된 정보 계층 구조를 제공 하는 뛰어난 사용자 환경을 제공 합니다.

![형식 진입 예](images/typography-ramp-1000px.jpg)<br>
*유형 램프를 정의 하 고 앱 환경 전체에서 팔 로우 합니다.*

### <a name="limit-your-fonts"></a>글꼴 제한

단일 컨텍스트에서 두 개 이상의 다른 글꼴 패밀리를 사용 하지 마십시오. 이렇게 하면 사용자 환경의 조화와 일관성이 손상 되어 정보를 사용 하기가 어려워집니다. HoloLens에서 정보는 물리적 환경 위에 중첩 되므로 글꼴 스타일을 너무 많이 사용 하면 환경이 저하 됩니다. 맑은 고딕은 모든 Microsoft 디지털 디자인의 글꼴입니다. Windows Mixed Reality 셸에서 일관 되 게 사용 됩니다. [Windows 디자인 도구 키트 페이지](https://docs.microsoft.com/windows/uwp/design-downloads/)에서 맑은 고딕 글꼴 파일을 다운로드할 수 있습니다.

[맑은 고딕 서체에 대 한 자세한 정보](https://docs.microsoft.com/windows/uwp/design/style/typography)

### <a name="avoid-thin-font-weights"></a>씬 글꼴 가중치 방지

얇은 수직선을 진동 하 고 가독성을 저하 시킬 수 있으므로 42pt에서 형식 크기에 대 한 밝거나 글꼴 가중치를 사용 하지 마십시오. 스트로크 두께가 충분 한 최신 글꼴이 제대로 작동 합니다. 예를 들어, Helvetica 및 Arial은 일반 또는 굵게 가중치를 사용 하 여 HoloLens에서 매우 쉽게 읽을 수 있습니다.

### <a name="color"></a>색

HoloLens에서 holograms은 가감 시스템을 사용 하 여 생성 되므로 흰색 텍스트는 매우 읽기 쉽게 합니다. 시작 메뉴와 앱 바에서 흰색 텍스트의 예제를 찾을 수 있습니다. HoloLens의 백 플레이트 없이 흰색 텍스트가 제대로 작동 하는 경우에도 복잡 한 물리적 배경으로 인해 형식을 읽기가 어려울 수 있습니다. 사용자의 포커스를 개선 하 고 실제 백그라운드에서 혼란 스 러를 최소화 하려면 진한 또는 컬러 뒷면에서 흰색 텍스트를 사용 하는 것이 좋습니다.

<br>


![진한 또는 컬러 뒷면에서 흰색 텍스트를 사용 하는 것이 좋습니다. *어두운 또는 컬러 후면의 흰색 텍스트 예를](images/typography-whiteonblack2-1000px.jpg)
합니다.*
<br>

어두운 텍스트를 사용 하려면 밝은 후면 판을 사용 하 여 읽을 수 있도록 해야 합니다. 가산적 색 시스템에서 검정은 투명으로 표시 됩니다. 즉, 색이 지정 된 배경 판을 표시 하지 않고 검정 텍스트를 볼 수 없습니다.

:::row:::
    :::column:::
        ![검정 텍스트 예제](images/typography-whiteonblack.png)<br>
        *검정의 흰색 및 흰색 텍스트의 검정색 예*<br>
    :::column-end:::
    :::column:::
        ![검정 텍스트 예제](images/640px-typography-blackonwhite.jpg)<br>
        *시스템 앱의 검정 텍스트 예-스토어 및 설정*<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="recommended-font-size"></a>권장 글꼴 크기

짐작할 수 있듯이, PC 또는 태블릿 장치에서 사용 하는 형식 크기 (일반적으로 12 – 32pt 사이)는 2 미터 거리에서 매우 작게 보입니다. 각 글꼴의 특성에 따라 달라 지지만 일반적으로 권장 되는 최소 보기 각도와 가독성을 위한 글꼴 높이는 사용자 연구 연구를 기반으로 하는 0.35 °-0.4 °/12.21-13.97mm을 중심으로 합니다. [Unity 페이지의 텍스트](text-in-unity.md) 에 도입 된 배율 인수를 사용 하는 약 35-40pt입니다. 

0\.45 m (45cm)에서 거의 상호 작용 하는 경우 읽을 수 있는 최소 글꼴의 보기 각도와 높이는 0.4 °-0.5 °/3.14 – 3.9 mm입니다. [Unity의 텍스트](text-in-unity.md)에서 도입 된 배율 인수를 사용 하는 12pt에 대 한 정보입니다.

근거리 및 원거리 상호 작용 범위 ![근거리 *및 원거리 상호 작용 범위에서 콘텐츠*](images/typography-distance-1000px.jpg)


### <a name="the-minimum-legible-font-size"></a>읽을 때 최소 글꼴 크기
| 거리 | 시야각 | 텍스트 높이 | 글꼴 크기 * * |
|---------|---------|---------|---------|
| 45cm (직접 조작 거리) | 0.4 °-0.5 ° | 3.14 – 3.9 mm | 8.9 – 11.13 pt |
| 2m | 0.35 °-0.4 ° | 12.21 – 13.97 mm | 34.63-39.58 pt |


### <a name="the-comfortably-legible-font-size"></a>편안 하 게 읽을 때의 글꼴 크기
| 거리 | 시야각 | 텍스트 높이 | 글꼴 크기 * * |
|---------|---------|---------|---------|
| 45cm (직접 조작 거리) | 0.65 °-0.8 ° | 5.1-6.3 mm | 14.47-17.8 pt |
| 2m | 0.6 °-0.75 ° | 20.9-26.2 mm | 59.4-74.2 pt |


맑은 고딕 (Windows의 기본 글꼴)은 대부분의 경우 잘 작동 합니다. 그러나 밝은 수직선을 진동 하 고 가독성을 저하 시킬 수 있으므로 작은 크기로 밝은 색 또는 반투명 글꼴 패밀리를 사용 하지 마십시오. 스트로크 두께가 충분 한 최신 글꼴이 제대로 작동 합니다. 예를 들어 Helvetica 및 Arial은 멋진 하 고 일반 또는 굵게 가중치를 사용 하 여 HoloLens에서 매우 읽을 수 있습니다.

**Unity의 텍스트 크기 계산에 대 한 자세한 내용은 [unity의 텍스트](text-in-unity.md) 를 참조 하세요.**

*거리, 각도 및 텍스트 높이를 볼*](images/Text_In_Unity_ViewingAngle.jpg)
각도 ![보기

<br>

---

## <a name="resources"></a>리소스

:::row:::
    :::column:::
    ### <a name="segoe-fontsbr"></a>[Segoe 글꼴](https://download.microsoft.com/download/1/B/C/1BCF071A-78EE-4968-ACBE-15461C274B61/Segoe%20fonts%20v1705.zip)<br>
    (Zip 파일)<br>
    ### <a name="hololens-fontbr"></a>[HoloLens 글꼴](https://download.microsoft.com/download/3/8/D/38D659E2-4B9C-413A-B2E7-1956181DC427/Hololens%20font.zip)<br>
    (Zip 파일)<br>
    <br>
    *이미지: HoloLens 글꼴은 Windows Mixed Reality에서 사용 되는 기호 문자 모양을 제공 합니다.*
    :::column-end:::
        :::column:::
        ![HoloLens 글꼴은 Windows Mixed Reality에서 사용 되는 기호 문자 모양을 제공 합니다.](images/hololensmdl2symbols.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="see-also"></a>참고 항목
* [Unity의 텍스트](text-in-unity.md)
* [색, 광원 및 재질](color,-light-and-materials.md)
