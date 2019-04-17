---
title: 3D 앱 시작 관리자 디자인 지침
description: 3D 앱 시작 관리자는 응용 프로그램 실행을 선택할 수 있는 사용자의 혼합된 현실 집에서 "실제" 개체입니다.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality를 디자인, 3D 앱 시작 관리자, 몰입 형 헤드셋, 라이브 큐브
ms.openlocfilehash: 47db5bffa121c0cc11d246dc749c464e5f187270
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598550"
---
# <a name="3d-app-launcher-design-guidance"></a>3D 앱 시작 관리자 디자인 지침

Windows Mixed Reality 몰입 형 (VR) 헤드셋을 놓을 때 입력할 집 Windows Mixed Reality 산 및 물으로 둘러싸인 절벽에서 집으로 시각화 (수행할 수 있지만 [다른 환경을 선택 하 고 자체를 만들 수도](add-custom-home-environments.md)). 홈이 공간 내에서 사용자가 정렬 하 고 3D 개체는 원하는 방식으로 처리 되는 앱을 구성 합니다. A **3D 앱 시작 관리자** 사용자에서는 "실제" 개체의 응용 프로그램 실행을 선택할 수 있는 현실 집을 혼합 됩니다.

![예: 부동 Bird 3D 앱 시작 관리자](images/20171016-151526-mixedreality1-1200px-1000px.jpg)<br>
*부동 Bird 3D 앱 시작 관리자 예제 (가상 앱)*

## <a name="3d-app-launcher-creation-process"></a>3D 앱 시작 관리자 만들기 프로세스

3D 앱 시작 관리자를 작성 하는 방법은 3 단계가 있습니다.
1. 디자인 및 concepting (이 문서)
2. [모델링 및 내보내기](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. 응용 프로그램에 통합 합니다.
    * [UWP 앱](implementing-3d-app-launchers.md)
    * [Win32 앱](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a>디자인 개념

### <a name="fantastic-yet-familiar"></a>친숙 한 아직 놀라운 기능

사용자 앱 시작 관리자에 거주 하 고 Windows Mixed Reality 환경은 부분에 친숙 한 파트 정보화/sci-fi입니다. 가장 좋은 시작 관리자는이 세상 규칙을 따릅니다. 어떻게 친숙 하 고 대표적인 개체를 앱에서 수행할 수 있지만 실제 실제로의 규칙 중 일부를 변형할 생각할 수 있습니다. 매직 발생 합니다.

### <a name="intuitive"></a>직관적인

사용자 앱 시작 관리자를 보면 용도-앱을 시작 하려면 명백 하 고 모든 혼동 해서는 안 됩니다. 예를 들어 프로그램 시작 관리자는 장식 Cliff 집안의 부분에 대 한 혼동 하지는 앱의 만큼 충분히 확실 한 대표 하는 해야 합니다. 에 앱 시작 관리자에는 터치/선택할 것 피플을 초대 해야 합니다.

![예: 새 참고 3D 앱 시작 관리자](images/20171016-152145-mixedreality1-1200px-1000px.jpg)<br>
*새 참고 3D 앱 시작 관리자 예제 (가상 앱)*

### <a name="home-scale"></a>홈 확장

Cliff 집에 살고 있는 3D 앱 시작 관리자 및 기본 크기로 공간에서 다른 "실제" 개체를 사용 하 여 의미를 확인 해야 합니다. 에 배치 하면 프로그램 시작 관리자에서 옆에 있는 예를 들어 집 공장 또는 일부 가구 것 느껴질 size-wise, 집 합니다. 좋은 시작 지점이 30 입방 형 3 센티미터에 어떻게 표시 하는 사용자가 크기를 조정할 수를 위아래로 원하는 경우 기억 됩니다.

### <a name="own-able"></a>소유 수

앱 시작 관리자는 담당할 해당 공간에 기대 개체 처럼 느껴질 것입니다. 이러한 됩니다 수 거의 주변 자체이를 사용 하 여 시작 관리자 느껴질 것 같은 사용자 생각 바람직 만큼 자동으로 검색 하 고 주변 유지 하므로.

![예: 우주 Warp 3D 앱 시작 관리자](images/20171016-132936-mixedreality-1200px-1000px.jpg)<br>
*우주 Warp 3D 앱 시작 관리자 예제 (가상 앱)*

### <a name="recognizable"></a>인식할 수 있는

즉시 3D 앱 시작 관리자에 표시 하는 사람에 게 "앱의 브랜드"를 표현 해야 합니다. 앱 별 문자나 특히 식별이 가능한 개체를 해야 하는 경우에 디자인의 주요 부분으로 사용 하는 것이 좋습니다. 혼합된 현실 세계에서 개체를만 로고만 보다 사용자의 관심사를 그립니다. 인식할 수 있는 빠르고 명확 하 게 브랜드를 통신합니다.

### <a name="volumetric"></a>대규모

앱은 이상의 평면에 로고를 배치 하 고 호출 시간부터 개발 합니다. 프로그램 시작 관리자 사용자의 공간에서 흥미로운, 3D, 물리적 개체 처럼 느껴질 것입니다. 앱 Macy의 추수 감사절 일 섰고 풍선에 하려는 imagine 하는 것이 좋습니다. 질문 어떤는 감명을 사람들이 그 길가의 왔는지에 따라? 유용한 모든 보기 각도에서 표시 됩니다 무엇입니까?


:::row:::
    :::column:::
        ![Logo only](images/20171016-140436-mixedreality-640px.jpg)
        *Logo only*
    :::column-end:::
    :::column:::
        ![More recognizable with a character](images/20171016-140557-mixedreality-640px.jpg)
        *More recognizable with a character*
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
        ![Flat approach, not surprisingly, feels flat](images/20171016-155101-mixedreality-640px.jpg)
        *Flat approach, not surprisingly, feels flat*
    :::column-end:::
    :::column:::
        ![Volumetric approach better showcases your app](images/20171016-161407-mixedreality-640px.jpg)
        *Volumetric approach better showcases your app*
    :::column-end:::
:::row-end:::


## <a name="tips-for-good-3d-models"></a>적합 한 3D 모델에 대 한 팁

### <a name="best-practices"></a>모범 사례
* 사용자 앱 시작 관리자에 대 한 차원을 계획할 때 약 30 cm 큐브에 대 한 문제를 해결 합니다. 따라서 1: 1:1 크기 비율입니다.
* 모델에는 10,000 개 미만이 다각형 이어야 합니다. [삼각형 개수 및 세부 (단계 Lod) 수준에 자세히 알아보기](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* 가능한 경우에 몰입 형 헤드셋에서 테스트 합니다.
* 가능한 경우 모델의 기 하 도형에 빌드 세부 정보 – 자세한 질감을 의존 하지 마세요.
* "Water 긴밀 하 게" 닫힌 geometry를 빌드하십시오. 모델링 되지는 빈 합니다.
* 개체에 자연 스러운 자료를 사용 합니다. 실제 환경에서 작성 한다고 가정 합니다.
* 모델에 다른 거리 및 크기에서 잘 있는지 확인 합니다.
* 모델 준비가 되 면 읽기를 [자산 지침 내보내기](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview)합니다.

![질감의 미묘한 세부 정보를 사용 하 여 모델](images/20171013-143334-mixedreality-640px.jpg)<br>
*질감의 미묘한 세부 정보를 사용 하 여 모델*

### <a name="what-to-avoid"></a>피해 야 할 사항
* 고대비 세부 정보 또는 사용 중인 작은 패턴 및 질감을 사용 하지 마세요.
* 씬 geometry를 사용 하지 않는 – 거리에서 잘 작동 하지 않습니다 고 별칭 잘못 됩니다.
* 확장 모델의 파트를 허용 하지 않습니다 1 이상의 너무 많은: 1:1 크기 비율입니다. 크기 조정 문제가 생기게 됩니다.

![고대비 작은 사용 중인 패턴 방지](images/20171013-143603-mixedreality-640px.jpg)<br>
*고대비, small, 사용 중인 패턴 방지*

## <a name="how-to-handle-type"></a>형식을 처리 하는 방법

### <a name="best-practices"></a>모범 사례
* 형식에 앱 시작 관리자 (또는 그 이상)의 약 1/3을 구성 하는 것이 좋습니다. 형식은 사용자 프로그램 시작 관리자는 실제로 상당히 많은 경우 유용 하도록 시작 관리자 개념을 제공 하는 것이 중요 합니다.
* 형식이 매우 피하십시오 – 유지 앱 시작 관리자의 범위 내에서 핵심 차원 (더 많거나 적은) 하려고 합니다.
* 플랫 형식이 작동 수 있지만 특정 환경에서는 특정 각도 보려는 하드 사용할 수 있다는 주의 합니다. Solid 개체 또는이 도움이 되도록 배경 배치 하는 것이 좋습니다.
* 형식에 추가 차원 느낌 멋진 3d에서 합니다. 형식의 양쪽 음영 다른, 어두운 색 가독성을 사용 하 여 도움이 됩니다.


:::row:::
    :::column:::
        ![Flat type without a backdrop can be hard to view from certain angles and in certain environments](images/flattype-640px.png)
        *Flat type without a backdrop can be hard to view from certain angles and in certain environments*
    :::column-end:::
    :::column:::
        ![Type with a built-in backdrop can work well](images/flattypeandbkg-640px.png)
        *Type with a built-in backdrop can work well*
    :::column-end:::
    :::column:::
        ![Extruded type can work well if you shade the sides](images/20171016-160221-mixedreality-640px.jpg)
        *Extruded type can work well if you shade the sides*
    :::column-end:::
:::row-end:::


**작동 하는 형식 색**
* 하얀
* 검정
* 밝은 반 채도가 높은 색

![작동 하는 색을 입력 합니다.](images/20171016-112111-mixedreality-640px.jpg)<br>
*작동 하는 형식 색*

### <a name="what-to-avoid"></a>피해 야 할 사항

**문제를 일으키는 형식 색**
* 중간 톤
* 회색
* 과도 하 게 포화 색 또는 낮춘된 색

![문제를 일으키는 색을 입력 합니다.](images/20171016-112246-mixedreality-640px.jpg)<br>
*문제를 일으키는 형식 색*

## <a name="lighting"></a>조명

사용자 앱 시작 관리자에 대 한 조명 Cliff 집 환경에서 제공 됩니다. 프로그램 시작 관리자에서 조명 및 그림자 모두 좋아 보입니다. 집 전체의 여러 위치에서 테스트 해야 합니다. 프로그램 시작 관리자는 Cliff 집에서 대부분의 조명에 대해 잘 셰이프에서 수 있어야이 문서의 다른 디자인 지침을 수행한 경우 좋은 소식이입니다.

프로그램 시작 관리자 환경에서 다양 한 광원에서 모양을 테스트 하려면 적절 한 위치는 Studio 미디어 대화방에 다시 테라스 (구체적인 영역과 앞 마당) 및 외부 아무 곳 이나를 합니다. 또 다른 좋은 테스트 절반 조명 및 그림자 절반에 배치 하 모양을 참조입니다.

![프로그램 시작 관리자에서 조명 및 그림자를 모두 정상적으로 진행 해야 합니다.](images/20171013-145523-mixedreality-1200px-1000px.jpg)<br>
*프로그램 시작 관리자에서 조명 및 그림자를 모두 정상적으로 진행 되는지 확인*

## <a name="texturing"></a>질감

### <a name="authoring-your-textures"></a>질감 제작

프로그램 3D 앱 시작 관리자의 최종 형식을 (물리적으로 기반 렌더링) PBR 파이프라인을 사용 하 여.glb 파일을 됩니다. 까다로운 프로세스-수 이제 아직 없는 경우 기술 artist를 사용할 수 있는 좋은 기회입니다. 인 경우 한 때 DIY-er 시간을 내어 [PBR 용어를 알아보고 조사](http://wiki.polycount.com/wiki/PBR) 도와 시작 하기 전에 내부에서 일어나는 일반적인 실수를 피하도록 합니다. 

![예: 새 Note 앱](images/pbr-freshnote1-640px-500px.png)<br>
*새 참고 3D 앱 시작 관리자 예제 (가상 앱)*

**권장 되는 제작 도구**

사용 하는 것이 좋습니다 [물질 복사](https://www.allegorithmic.com/products/substance-painter) Allegorithmic 최종 파일을 작성 하 여 합니다. 친숙 하지 않은 물질 페인, 여기에서 PBR 셰이더를 작성 하는 경우는 [자습서](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials)합니다.

(또는 [3D Coat](https://3dcoat.com/home/)를 [Quixel 제품군 2](https://quixel.se/suite2/), 또는 [Marmoset Toolbag](https://www.marmoset.co/toolbag/) 다음 중 하나를 사용 하 여 더욱 친숙 하는 경우에 작동 됩니다.)

### <a name="best-practices"></a>모범 사례

* 앱 시작 관리자 개체 PBR에 대해 작성 된, 하는 경우에 Cliff 집 환경에 대 한 변환 하는 것이 간단 이어야 합니다.
* 이 셰이더는 금속/거친 작업 흐름 필요 – The Unreal PBR 셰이더가 닫기 사본을 합니다.
* 질감을 내보내는 유지 하는 경우는 [권장 되는 질감 크기](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) 유의 해야 합니다.
* 실시간 조명에 대해 개체를 작성 해야 합니다.-즉:
    * 구운된 그림자 – 또는 그려지는 그림자를 방지 합니다.
    * 질감에서 구운된 조명 방지
    * 패키지 제작 PBR 자료 중 하나를 사용 하 여이 셰이더에 대해 생성 된 올바른 지도 받기

## <a name="see-also"></a>참조

* [홈 혼합된 현실에서 사용 하 여에 대 한 3D 모델 만들기](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [3D 앱 시작 관리자 (UWP 앱)를 구현 합니다.](implementing-3d-app-launchers.md)
* [3D 앱 시작 관리자 (Win32 앱)를 구현 합니다.](implementing-3d-app-launchers-win32.md)
