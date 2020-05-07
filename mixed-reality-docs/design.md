---
layout: LandingPage
title: 디자인 및 프로토타입 생성 시작
description: 만들 준비가 되면, 디자인 및 프로토타입 생성을 시작하는 데 필요한 기본 개념을 알아봅니다.
author: grbury
ms.author: grbury
ms.date: 08/24/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, 검색, 배포, 인덱스, 방문 페이지, 디자인, 개발, 자습서, 샘플 앱, 기본 사항, 사례 연구, 리소스, HoloLens 방법, 오픈 소스 프로젝트, 핵심 개념, 상호 작용
ms.openlocfilehash: 9ef408e1551e9f6c52a6c5fcf7df3123cc099c8c
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/29/2020
ms.locfileid: "75334113"
---
# <a name="start-designing-and-prototyping"></a>디자인 및 프로토타입 생성 시작


![혼합 현실 디자인 요약](images/03_Design.png)

## <a name="expand-your-design-process"></a>[디자인 프로세스 확장](case-study-expanding-the-design-process-for-mixed-reality.md)

2016년 Microsoft에서 열정적인 개발자를 대상으로 하는 HoloLens를 시작함에 따라 팀에서 이미 Microsoft 내외부의 스튜디오와 제휴하여 디바이스의 시작 환경을 구축했습니다. 이러한 팀은 혼합 현실 디자인의 새로운 분야에서 기회와 과제를 모두 수행하고 찾아냄으로써 학습했습니다. [자세한 정보](case-study-expanding-the-design-process-for-mixed-reality.md)

<br>

---

## <a name="what-are-the-core-concepts-of-an-experience"></a>환경의 핵심 개념은 무엇인가요?

### <a name="keep-the-user-comfortable---comfort"></a>[사용자를 편안하게 유지 - (편안함)](comfort.md)
헤드 마운트 디스플레이에서 최대한 편안하도록 하려면 디자이너와 개발자가 이러한 신호가 자연계에서 작동하는 방식을 모방하는 방식으로 콘텐츠를 만들고 표시해야 합니다.

<br>

### <a name="consider-how-the-user-sees-the-world---holographic-frame"></a>[사용자에게 세계를 표시하는 방법 고려 - (홀로그램 프레임)](holographic-frame.md)
사용자는 헤드셋에서 구동하는 사각형 뷰포트를 통해 혼합 현실의 세계를 볼 수 있습니다. HoloLens에서 이 사각형 영역은 홀로그램 프레임이라고 하며, 사용자는 이를 통해 주변의 실제 세계에 겹쳐진 디지털 콘텐츠를 볼 수 있습니다.

<br>

### <a name="types-of-mixed-reality-apps"></a>[혼합 현실 앱의 종류](types-of-mixed-reality-apps.md)
혼합 현실용 앱 개발의 장점 중 하나는 플랫폼에서 지원할 수 있는 다양한 환경이 있다는 것입니다. 혼합 현실은 완전 몰입형 가상 환경에서 사용자의 현재 환경에 대한 경량 정보 계층화까지 모든 환경에 생동감을 주는 강력한 도구 세트를 제공합니다.

<br>

### <a name="keeping-holograms-in-place---coordinate-systems"></a>[홀로그램 위치 유지 - (좌표계)](coordinate-systems.md)
혼합 현실 앱의 핵심은 현실 세계에 홀로그램을 배치하여 실물처럼 모양과 소리를 내는 것입니다. 여기에는 사용자에게 의미 있는 위치에 홀로그램을 정확하게 배치하는 작업이 포함됩니다. 이러한 위치는 물리적 공간이든 내가 만든 가상 영역이든 상관없습니다.

<br>

### <a name="making-holographic-objects-feel-real---spatial-mapping"></a>[홀로그램 개체를 실제적으로 느끼도록 만들기 - (공간 매핑)](spatial-mapping.md)
공간 매핑을 사용하면 개체를 실제 표면에 배치할 수 있습니다. 이렇게 하면 사용자의 세계에서 개체를 고정하고 실제 세계 깊이 신호를 활용할 수 있습니다.

<br>


---

<br>

![상호 작용 디자인 요소](images/MRTK_BoundingBox_Main.png)

## <a name="interaction-design-factors-to-consider"></a>고려할 상호 작용 디자인 요소


### <a name="choose-an-interaction-model-for-your-customer"></a>[고객을 위한 상호 작용 모델 선택](interaction-fundamentals.md)
간단하고 직관적인 상호 작용이라는 철학은 혼합 현실 플랫폼 전반에 얽혀 있습니다. 애플리케이션 디자이너와 개발자가 고객에게 쉽고 직관적인 상호 작용을 제공할 수 있도록 하는 3단계를 살펴보았습니다.

<br>

### <a name="hands-and-motion-controllers"></a>[실습 및 모션 컨트롤러](hands-and-tools.md)
사용자는 실제 개체를 다루듯이 한 손 또는 두 손으로 홀로그램을 직접 터치하고 조작할 수 있습니다. 또는 모션 컨트롤러를 사용하면 상당히 다양한 거리에서 정확한 상호 작용을 제공하여 사용자의 물리적 역량을 확장할 수 있습니다.

<br>

### <a name="directly-commanding-objects-with-voice-input"></a>[음성 입력으로 개체에 직접 명령](voice-input.md)
음성은 HoloLens의 주요 입력 형태 중 하나입니다. 음성을 사용하면 제스처를 사용하지 않고 홀로그램에 직접 명령할 수 있습니다. 음성 입력은 의도를 전달하는 자연스러운 방법일 수 있습니다.

<br>

### <a name="leveraging-the-users-eye-gaze"></a>[사용자의 눈길 활용 - 응시](eye-tracking.md)
HoloLens 2는 사용자가 보고 있는 대상에 대한 정보를 사용할 수 있는 기능을 개발자에게 제공하여 홀로그램 환경 내에서 이해할 수 있는 새로운 수준의 컨텍스트 및 사용자를 허용합니다.

<br>

### <a name="color-light-and-materials"></a>[색, 광원 및 재질](color,-light-and-materials.md)
혼합 현실용 콘텐츠를 디자인하려면 환경에서 사용되는 시각적 자산 각각에 대한 색, 조명 및 재질을 신중하게 고려해야 합니다.

<br>

### <a name="suggesting-the-scale-of-an-object"></a>[개체 크기 조정 제안](scale.md)
홀로그램 형태로 사실적으로 보이는 콘텐츠를 표시하는 핵심 요소는 실제 세계의 시각적 특징을 최대한 긴밀하게 모방하는 것입니다. 즉, 실제 세계에서 개체의 위치, 크기 및 구성 요소를 이해하는 데 도움이 될 수 있는 만큼 시각적 신호를 최대한 많이 통합해야 합니다.

<br>

### <a name="clear-and-readable-typography"></a>[명확하고 읽기 가능한 입력 체계](typography.md)
2D 화면의 입력 체계처럼 목표는 명확하고 읽기 쉬운 것입니다. 혼합 현실의 3차원 측면에서는 텍스트와 사용자 환경 전체에 훨씬 더 큰 영향을 줄 수 있는 기회가 있습니다.

<br>

### <a name="ux-elements-for-the-mixed-reality"></a>[혼합 현실용 UX 요소](app-patterns-landingpage.md)
혼합 현실에서 공간 상호 작용 및 UI의 기본 구성 요소에 대해 알아봅니다.
<br>


---

## <a name="choose-a-prototyping-option"></a>프로토타입 생성 옵션 선택  

:::row:::   
    :::column:::    
       [![Unity 배우기](images/Final_unity_logo.png)](https://learn.unity.com/)<br>
        **[Unity 배우기](https://learn.unity.com/)**<br>
        Unity를 사용하여 대화형 환경을 만드는 방법을 알아봅니다. 처음부터 끝까지 수행하여 알아봅니다.
    :::column-end:::    
    :::column:::    
        [![Mixed Reality Toolkit(MRTK)](images/Final_mrtk-small_logo.png)](https://github.com/Microsoft/MixedRealityToolkit-Unity)<br>
        **[Mixed Reality Toolkit(MRTK)](https://github.com/Microsoft/MixedRealityToolkit-Unity)**<br>  
        공간 상호 작용 및 UI의 기본 구성 요소와 함께 Unity를 사용하여 혼합 현실 디자인 및 개발을 바로 시작합니다.   
    :::column-end:::
    :::column:::    
        [![혼합 현실 디자인 랩](images/Final_mrdl_logo.png)](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)<br>
        **[혼합 현실 디자인 랩](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)**<br>  
        MRTK의 기본 구성 요소를 사용하여 아름다운 혼합 현실 환경을 만드는 방법을 보여주는 샘플 앱을 다운로드하세요.
    :::column-end:::        
    :::column:::    
        [![Microsoft Maquette](images/Final_maquette_logo.png)](https://www.maquette.ms/)<br>
        **[Microsoft Maquette](https://www.maquette.ms/)**<br>  
        VR을 위한 디자인. Microsoft Maquette를 사용하면 공간 프로토타입을 쉽고 빠르며 몰입감 있게 제작할 수 있습니다. 
    :::column-end:::    
:::row-end:::

<br>

---



## <a name="what-would-you-like-to-do-next"></a>다음에 수행할 작업은 무엇인가요?

:::row:::
    :::column:::
       [![기본 사항 이해](images/icon-lightbulb.png)](index.md#understand-the-basics)<br>
        **[기본 사항 이해](index.md#understand-the-basics)**<br>
        혼합 현실을 정의하는 것이 무엇이며, 혼합 현실이 어떻게 사용되는지에 대해 더 잘 이해합니다.
    :::column-end:::
    :::column:::
        [![이벤트 참가](images/icon-calendar.jpg)](sf-academy-events.md)<br>
         **[이벤트 참가](sf-academy-events.md)**<br>
        하드웨어를 살펴보고 첫 번째 HoloLens 2 애플리케이션을 만들기 위한 실습 자습서를 받으세요.
    :::column-end:::
    :::column:::
        [![도구 설치](images/icon-design.jpg)](install-the-tools.md)<br>
         **[도구 설치](install-the-tools.md)**<br>
        설치 체크리스트를 사용하여 HoloLens와 혼합 현실용 앱을 빌드하는 데 필요한 도구를 구합니다.
    :::column-end:::
    :::column:::
        [![개발 시작](images/icon-developer.jpg)](development.md)<br>
        **[개발 시작](development.md)**<br>
        자신의 기술 수준, 작업 스타일 또는 플랫폼 관심 분야에 따라 개발 경로를 선택합니다.
    :::column-end:::
:::row-end:::


<br>

<br>


