---
title: 3D 앱 시작 관리자 디자인 지침
description: 3D 앱 시작 관리자는 응용 프로그램을 시작 하도록 선택할 수 있는 사용자의 혼합 현실 집에 있는 "물리적" 개체입니다.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 디자인, 3D 앱 시작 관리자, 모던 헤드셋, 라이브 큐브
ms.openlocfilehash: ce9d242e26d67c8fe5af7ac32f4e910a15715d25
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437226"
---
# <a name="3d-app-launcher-design-guidance"></a>3D 앱 시작 관리자 디자인 지침

Windows Mixed Reality 몰입 (VR) 헤드셋에 배치 하는 경우에는 산 및 물로 둘러싸인 절벽에 집으로 시각화 된 Windows Mixed Reality 홈을 입력 합니다 ( [다른 환경을 선택 하 고 직접 만들](add-custom-home-environments.md)수도 있음). 이 홈의 공간 내에서 사용자가 원하는 방식으로 관심 있는 3D 개체와 앱을 자유롭게 정렬 하 고 구성할 수 있습니다. **3d 앱 시작 관리자** 는 응용 프로그램을 시작 하도록 선택할 수 있는 사용자의 혼합 현실 집에 있는 "물리적" 개체입니다.

![예: Floaty Bird 3D 앱 시작 관리자](images/20171016-151526-mixedreality1-1200px-1000px.jpg)<br>
*Floaty Bird 3D 앱 시작 관리자 예제 (가상 앱)*

## <a name="3d-app-launcher-creation-process"></a>3D 앱 시작 관리자 만들기 프로세스

3D 앱 시작 관리자를 만드는 단계는 세 가지입니다.
1. 디자인 및 concepting (이 문서)
2. [모델링 및 내보내기](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. 응용 프로그램에 통합:
    * [UWP 앱](implementing-3d-app-launchers.md)
    * [Win32 앱](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a>디자인 개념

### <a name="fantastic-yet-familiar"></a>잘 알고 있습니다.

앱 시작 관리자가 거주 하는 Windows Mixed Reality 환경은 fantastical/좋아하는 파트에 대해 잘 알고 있습니다. 최상의 실행 기가이 세계의 규칙을 따릅니다. 앱에서 친숙 한 대표 개체를 사용할 수 있는 방법을 생각해 볼 수 있지만 실제 현실에 대 한 일부 규칙은 벤드 합니다. 마법이 발생 합니다.

### <a name="intuitive"></a>간단

앱 시작 관리자를 살펴보면 앱을 시작 하는 용도는 명확 하 고 혼동이 발생 해서는 안 됩니다. 예를 들어, 관리자가 절벽 집에서 décor 부분에 대해 혼란 스 럽 지 않을 수 있는 명확 하 고 충분 한 앱 대표 인지 확인할 수 있습니다. 앱 시작 관리자는 사용자에 게 연락 하 여 사용자를 초대 해야 합니다.

![예제: 최신 메모 3D 앱 시작 관리자](images/20171016-152145-mixedreality1-1200px-1000px.jpg)<br>
*최신 참고 3D 앱 시작 관리자 예제 (가상 앱)*

### <a name="home-scale"></a>홈 크기 조정

3D 앱 시작은 절벽 집에서 라이브 되며 기본 크기는 공간의 다른 "물리적" 개체에 적합 해야 합니다. 집 식물 또는 일부 가구 옆에 시작 관리자를 배치 하면 집, 크기를 중심으로 느낌을 해야 합니다. 시작 하는 것은 30 평방 센티미터를 확인 하는 것 이지만 사용자가 원하는 경우 규모를 확장 하거나 축소할 수 있다는 점을 명심 해야 합니다.

### <a name="own-able"></a>소유 가능

앱 시작 관리자는 사람들의 공간에 있을 것으로 기대 하는 개체와 같은 느낌을 합니다. 이러한 작업은 실질적으로 이러한 작업을 수행 하기 때문에 사용자가 자유롭게 검색 하 고 가까이 유지할 수 있었던 것 처럼 보입니다.

![예: Astro 구부리기 3D 앱 시작 관리자](images/20171016-132936-mixedreality-1200px-1000px.jpg)<br>
*Astro 구부리기 3D 앱 시작 관리자 예제 (가상 앱)*

### <a name="recognizable"></a>읽을

3D 앱 시작 관리자는 "자신의 앱의 브랜드"를 표시 하는 사용자에 게 즉시 표현 해야 합니다. 앱에 별표 (*) 또는 특별히 식별 가능한 개체가 있는 경우 디자인의 큰 부분으로 사용 하는 것이 좋습니다. 혼합 현실 세계에서 개체는 단지 로고만이 아닌 사용자에 게 더 많은 관심을 그리도록 합니다. 인식 가능한 개체는 신속 하 고 명확 하 게 브랜드를 전달 합니다.

### <a name="volumetric"></a>대규모

앱은 기본 평면에 로고를 배치 하 고 하루에 호출 하는 것 보다 더 많은 것이 있습니다. 시작 관리자는 사용자의 공간에서 흥미로운 3D의 실제 개체와 같은 느낌을 합니다. 좋은 방법은 앱이 Macy의 추수 퍼레이드에서 풍선을 사용 한다고 가정 하는 것입니다. 사용자에 게 질문을 하 고 나 서 몇 분 동안에는 어떻게 해야 하나요? 모든 보기 각도에서 크게 보이는 것은 무엇 인가요?


:::row:::
    :::column:::
        *로고 전용](images/20171016-140436-mixedreality-640px.jpg) ![* 로고
    :::column-end:::
    :::column:::
        문자를 사용 하 여 더 쉽게 인식할 ![문자](images/20171016-140557-mixedreality-640px.jpg) *인식*
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
        ![플랫 접근 방법, 즉, 느낌이 좋은 플랫](images/20171016-155101-mixedreality-640px.jpg) *플랫 접근 방식이* 아닙니다.
    :::column-end:::
    :::column:::
        ![대규모 접근 방식을 사용 하면 앱을 보다 잘 파악할](images/20171016-161407-mixedreality-640px.jpg) *대규모 접근 방법을* 더 잘 보여 줍니다.
    :::column-end:::
:::row-end:::


## <a name="tips-for-good-3d-models"></a>좋은 3D 모델에 대 한 팁

### <a name="best-practices"></a>모범 사례
* 앱 시작 관리자에 대 한 차원을 계획할 때 약 30cm 큐브를 촬영 합니다. 따라서 1:1:1 크기 비율입니다.
* 모델은 1만 polygon 미만 이어야 합니다. [삼각형 개수 및 세부 정보 수준에 대 한 자세한 정보 (LODs)](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* 가능 하면 몰입 형 헤드셋에서 테스트 합니다.
* 가능 하면 모델의 기 하 도형에 세부 정보를 빌드 하세요. 자세한 내용은 질감을 사용 하지 마세요.
* "물 근접" 폐쇄형 기 하 도형을 빌드합니다. 에서 모델링 되지 않은 구멍이 없습니다.
* 개체의 기본 자료를 사용 합니다. 실제 세계에서 크 래 프 트를 만들어 보겠습니다.
* 모델이 다른 거리와 크기에서 잘 읽도록 합니다.
* 모델을 이동할 준비가 되 면 [자산 내보내기 지침](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview)을 참조 하세요.

질감에서 미묘한 세부 정보를 포함 하는 ![모델](images/20171013-143334-mixedreality-640px.jpg)<br>
*질감에서 미묘한 세부 정보를 포함 하는 모델*

### <a name="what-to-avoid"></a>피해 야 할 사항
* 고대비 세부 정보 또는 작은 사용 중 패턴과 텍스처를 사용 하지 마세요.
* 씬 geometry를 사용 하지 마세요. 거리가 적절 하 게 작동 하지 않고 별칭이 잘못 됩니다.
* 모델의 일부가 1:1:1 크기 비율을 초과 하 여 너무 많이 확장 되는 것을 허용 하지 않습니다. 크기 조정 문제를 만듭니다.

고대비, 사용량이 적은 패턴을 방지 ![](images/20171013-143603-mixedreality-640px.jpg)<br>
*고대비, 작은 사용 중 패턴 방지*

## <a name="how-to-handle-type"></a>형식을 처리 하는 방법

### <a name="best-practices"></a>모범 사례
* 앱 시작 관리자 (또는 그 이상)의 1/3에 대 한 형식을 구성 하는 것이 좋습니다. 사용자는 시작 관리자가 실제로 시작 관리자 임을 알 수 있도록 하는 주요 사항은 유형입니다.
* Super wide를 사용 하지 마십시오. 앱 시작 전 코어 차원의 범위 내에 유지 하려고 합니다.
* 플랫 형식이 작동할 수 있지만 특정 환경 및 특정 환경에서 보는 것은 어려울 수 있습니다. 이를 지원 하기 위해이를 solid 개체 또는 배경으로 배치 하는 것을 고려할 수 있습니다.
* 3D에서 형식에 차원을 추가 하는 것이 좋습니다. 형식의 면을 다른 색으로 음영을 사용 하면 가독성을 높일 수 있습니다.


:::row:::
    :::column:::
        배경 없이 ![플랫 유형을 사용 하면 특정 각도에서 볼 수 있을 수 있으며 특정 환경에서 *배경이 없는 플랫 유형을](images/flattype-640px.png) 특정 각도 및 특정 환경에서 표시 하기가 어려울 수 있습니다* .
    :::column-end:::
    :::column:::
        기본 제공 배경이 있는 ![형식은 *기본 제공 되는 배경이 있는 형식*](images/flattypeandbkg-640px.png) 제대로 작동할 수 있습니다.
    :::column-end:::
    :::column:::
        ![돌출 형식은 가장자리를 음영 처리 하는 경우에도 *입체 형식*](images/20171016-160221-mixedreality-640px.jpg) 회색으로 표시 될 수 있습니다.
    :::column-end:::
:::row-end:::


**작동 하는 색을 입력 합니다.**
* 하얀
* 명암
* 밝은 반 채도 색

![형식 색입니다.](images/20171016-112111-mixedreality-640px.jpg)<br>
*작동 하는 색을 입력 합니다.*

### <a name="what-to-avoid"></a>피해 야 할 사항

**문제를 일으키는 색을 입력 합니다.**
* 중간 색조
* 으로
* 채도가 높은 색 또는 낮춘 색

문제가 발생 하는 색 ![형식입니다.](images/20171016-112246-mixedreality-640px.jpg)<br>
*문제를 일으키는 색을 입력 합니다.*

## <a name="lighting"></a>조명

앱 시작 관리자의 조명은 절벽 집 환경에서 제공 됩니다. 이 경우에는 집 전체의 여러 위치에서 시작 관리자를 테스트 하 여 밝은 및 그림자 모두에 적합 합니다. 좋은 소식은이 문서에 있는 다른 디자인 지침을 수행한 경우에는 관리자가 절벽 집에서 대부분의 조명에 매우 좋은 셰이프 여야 합니다.

시작 관리자가 환경에서 다양 한 조명의 화면에 표시 되는 모습을 테스트 하는 좋은 위치는 스튜디오, 미디어 객실 (Patio의 구체적인 영역)입니다. 또 다른 좋은 테스트는 반쪽 및 1/2 그림자에 배치 하 고 모양을 확인 하는 것입니다.

사용 중인 시작 관리자가 밝은 및 그림자 모두에 적합 한지 확인 ![합니다.](images/20171013-145523-mixedreality-1200px-1000px.jpg)<br>
*시작 관리자가 밝은 및 그림자 둘 다에서 제대로 보이는지 확인 합니다.*

## <a name="texturing"></a>질감

### <a name="authoring-your-textures"></a>질감 제작

3D 앱 시작 관리자의 끝 형식은 .PBR (물리적으로 기반 렌더링) 파이프라인을 사용 하 여 만든. 이는 복잡 한 프로세스 일 수 있습니다. 현재는 기술 음악가를 사용 하는 것이 좋습니다. 용감한 DIY 인 경우, 시작 하기 전에 내부적으로 수행 해야 하는 작업을 [연구 하 고 배우](https://wiki.polycount.com/wiki/PBR) 는 데 걸리는 시간은 일반적인 실수를 피하는 데 도움이 됩니다. 

![예제: 최신 메모 앱](images/pbr-freshnote1-640px-500px.png)<br>
*최신 참고 3D 앱 시작 관리자 예제 (가상 앱)*

**권장 authoring tool**

Allegorithmic [를 사용 하 여 최종](https://www.allegorithmic.com/products/substance-painter) 파일을 작성 하는 것이 좋습니다. 학습 기능 복사에서 .PBR 셰이더를 작성 하는 방법을 잘 모르는 경우 다음 [자습서](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials)를 참조 하세요.

이러한 기능 중 하나를 잘 알고 있는 경우에는 (교대로 [3D 옷걸이](https://3dcoat.com/home/), [Quixel Suite 2 또는](https://quixel.se/suite2/) [moset 도구 모음이](https://www.marmoset.co/toolbag/) 작동 합니다.)

### <a name="best-practices"></a>모범 사례

* 앱 시작 관리자 개체가 .PBR 용으로 작성 된 경우에는 절벽 집 환경으로 변환 하는 것이 매우 간단 합니다.
* 셰이더에는 금속/황삭 작업 흐름이 필요 합니다. Unreal .PBR 셰이더는 닫는 팩스입니다.
* 질감을 내보내는 경우 [권장 되는 질감 크기](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) 를 염두에 두십시오.
* 실시간 조명에 대 한 개체를 빌드해야 합니다. 즉, 다음을 의미 합니다.
    * 그림자를 구운 안 함
    * 질감에서 조명 구운 방지
    * .PBR 재질 제작 패키지 중 하나를 사용 하 여 셰이더에 대해 생성 된 올바른 맵 가져오기

## <a name="see-also"></a>참고 항목

* [혼합 현실 홈에서 사용할 3D 모델 만들기](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [3D 앱 시작 관리자(UWP 앱) 구현](implementing-3d-app-launchers.md)
* [3D 앱 시작 관리자(Win32 앱) 구현](implementing-3d-app-launchers-win32.md)
