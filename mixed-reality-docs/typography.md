---
title: 입력 체계
description: 텍스트에는 앱 환경에서 정보를 제공 하기 위한 중요 한 요소입니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality를 디자인, 스타일, 글꼴, 입력 체계, ui, ux
ms.openlocfilehash: b4bac35cbc412ec7102748350c2f5c1e236c2f7d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603249"
---
# <a name="typography"></a>입력 체계

텍스트에는 앱 환경에서 정보를 제공 하기 위한 중요 한 요소입니다. 2D 화면에서 입력 체계에서와 마찬가지로 목표를 명확 하 고 읽을 수 있는입니다. 혼합된 현실의 3 차원 모양 텍스트와 전체 사용자에 영향을 줄 수 있는 기회는 더 높은 방식으로 경험 합니다.

![HoloLens의 입력 체계 예제](images/640px-typography-hero2.jpg)<br>
*HoloLens의 입력 체계 예제*

3d에서 형식에 대 한 이야기 하는 경우 대규모 입체 3D 텍스트를 생각 하는 경향이 있습니다. 일부 로고 형식 디자인 및 제한 된 응용 프로그램을 제외 하 고 돌출 된 텍스트는 텍스트의 가독성을 저하 경향이 있습니다. 3D에 대 한 환경을 설계를 하는 경우에 사용 2D 유형에 대 한 더 읽을 수이 고 쉽게 읽을 수 있기 때문에 합니다.

HoloLens, 종류는 가산적 색 시스템에 따라 light를 사용 하 여 홀로그램을 사용 하 여 생성 됩니다. 다른 홀로그램 마찬가지로 형식 world 잠기고 모든 각도에서 관찰 될 수 있는 실제 환경에 배치할 수 있습니다. 합니다 [시차](https://en.wikipedia.org/wiki/Parallax) 형식과 환경 효과 또한 깊이 환경에 추가 합니다.

## <a name="typography-in-mixed-reality"></a>혼합된 현실의 입력 체계

혼합된 현실에서 인쇄 규칙은 다른 곳 다르지 않습니다. 가상 세계와 실제 텍스트를 읽을 수 하 고 읽을 수 있어야 합니다. 텍스트나 벽에 있을 수는 실제 개체 위에 나타납니다. 디지털 사용자 인터페이스와 함께 부동 수 없습니다. 컨텍스트에 관계 없이 읽고 인식에 대 한 동일한 인쇄 규칙을 적용 했습니다.

### <a name="create-clear-hierarchy"></a>일반 계층 만들기

다양 한 형식 크기와 가중치를 사용 하 여 대비 및 계층 구조를 빌드하십시오. 형식 확장을 정의 하 고 앱 환경 전체에서 그 다음에 일관 된 정보 계층을 사용 하 여 뛰어난 사용자 환경을 제공 합니다.

![형식 진입 예제](images/typography-ramp-1000px.jpg)<br>
*형식 진입 예제*

### <a name="limit-your-fonts"></a>해당 글꼴이 제한

단일 컨텍스트에서 두 개 이상의 다양 한 글꼴 패밀리를 사용 하지 마십시오. 사용자 경험의 일관성 및 조화 중단 되 고 정보를 사용 하기가 어려워집니다. HoloLens에서 너무 많은 글꼴 스타일을 사용 하 여 실제 환경에서 기반으로 정보는 중첩 하므로 환경이 저하 됩니다. Segoe UI에는 모든 Microsoft 디지털 디자인에 대 한 글꼴입니다. Windows Mixed Reality 셸에서 일관 되 게 사용 됩니다. Segoe UI 글꼴 파일을 다운로드할 수 있습니다 합니다 [toolkit 페이지를 디자인 하는 Windows](https://docs.microsoft.com/windows/uwp/design-downloads/)합니다.

[Segoe UI 서체에 대 한 자세한 정보](https://docs.microsoft.com/windows/uwp/design/style/typography)

### <a name="avoid-thin-font-weights"></a>씬 글꼴 두께 방지 합니다.

씬 세로 획 진동 되며 읽기 쉽도록 코멘트가 저하 되므로 42pt 아래 형식 크기에 대 한 간단한 또는 semilight 글꼴 두께 사용 하지 마십시오. 충분 한 스트로크 두께 사용 하 여 최신 글꼴 잘 작동 합니다. 예를 들어, Helvetica Arial와 매우 HoloLens에서 읽을 수 일반 또는 굵게 표시 된 가중치를 사용 하 여입니다.

### <a name="color"></a>색

HoloLens에서 홀로그램 가산적 간단한 시스템을 사용 하 여 생성 된 흰색 텍스트 이므로 항상 읽을 수 있습니다. 시작 메뉴에서 앱 바에 흰색 텍스트의 예제를 찾을 수 있습니다. HoloLens에 흰색 텍스트 백 접시 없이 잘 작동 하는 경우에 복잡 한 실제 배경이 만들 수 있습니다 형식 읽기 어렵습니다. 사용자의 포커스를 개선 및 실제 백그라운드에서 혼란을 최소화, 어둡게 또는 색이 지정 된 다시 판에 흰색 텍스트를 사용 하는 것이 좋습니다.

<br>


![어두운 또는 색이 지정 된 백 판에 흰색 텍스트를 사용 하는 것이 좋습니다.](images/typography-whiteonblack2-1000px.jpg)

어두운 또는 색이 지정 된 백 판에 흰색 텍스트를 사용 하는 것이 좋습니다.

<br>


![검정 텍스트 예제](images/640px-typography-textcolors.jpg)

어두운 텍스트를 사용 하려면 읽을 수 있도록 밝은 백 접시를 사용 해야 합니다. 가산적 색 시스템 검정 투명 하 게 표시 됩니다. 즉, 접시를 다시는 컬러 없이 검정 텍스트를 볼 수 없습니다.

<br>


![검정 텍스트 예제](images/640px-typography-blackonwhite.jpg)

UWP 앱 스토어, 설정 등의 검정 텍스트의 예제를 찾을 수 있습니다.

## <a name="recommended-font-size"></a>권장 되는 글꼴 크기

![두 개의 미터에는 텍스트를 표시 하기 위한 최적의 거리입니다.](images/typography-distance-1000px.jpg)

두 개의 미터에는 텍스트를 표시 하기 위한 최적의 거리입니다.

혼합된 현실에서는 3 차원 수준에 있으므로 항상 글꼴의 크기를 통신 하기가 쉽 것은 아닙니다. 사용자의 쾌적 한 두 가지 단위가 홀로그램 배치에 대 한 최적의 거리입니다. 최적의 글꼴 크기를 찾으려면이 거리 기준으로 사용할 수 있습니다.

예상할 수 있듯이 PC 또는 태블릿 장치 (일반적으로 12 – 32pt) 사이 사용 하는 형식 크기 2 미터 거리 만큼 떨어진 좁습니다 찾습니다. 각 글꼴의 특성에 다르지만 일반적으로 권장 되는 최소 형식 스트로크 진동 없이 읽기 쉽도록 코멘트가 크기가 약 30 (태평양 표준시)입니다. 가까운 거리에 사용할 할 앱을 더 작은 형식 크기 사용할 수 있습니다. **지점 크기는 Unity의 3D 텍스트 메시 및 UI 텍스트를 기반으로 합니다. 자세한 메트릭과 배율 인수를 참조 하십시오 [Unity에서 텍스트](text-in-unity.md)합니다.**

## <a name="resources"></a>리소스
* [Segoe 글꼴](http://download.microsoft.com/download/1/B/C/1BCF071A-78EE-4968-ACBE-15461C274B61/Segoe%20fonts%20v1705.zip)
* [HoloLens 글꼴](http://download.microsoft.com/download/3/8/D/38D659E2-4B9C-413A-B2E7-1956181DC427/Hololens%20font.zip)

![HoloLens 글꼴을 사용 하면 Windows Mixed Reality에 사용 되는 기호 문자 모양](images/300px-hololensmdl2symbols.jpg)

HoloLens 글꼴 Windows Mixed Reality에 사용 되는 기호 문자 모양을 제공 합니다.

## <a name="see-also"></a>참조
* [Unity에서 텍스트](http://holodocsfuture/index.php?title=Text_in_Unity&action=edit&redlink=1)
* [색, 광원 및 재질](color,-light-and-materials.md)
