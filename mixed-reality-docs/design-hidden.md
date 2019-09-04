---
layout: LandingPage
title: 디자인 및 프로토타입 생성 시작
description: 무언가를 만들 준비가 되었습니다. 디자인 및 프로토타입 생성을 시작하는 데 필요한 기본 개념을 알아봅니다.
author: grbury
ms.author: grbury
ms.date: 08/24/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, 검색, 배포, 인덱스, 방문 페이지, 디자인, 개발, 자습서, 샘플 앱, 기본 사항, 사례 연구, 리소스, HoloLens 방법, 오픈 소스 프로젝트
ms.openlocfilehash: 3efb411425d18a8f50a209b69b00bfa038d594f1
ms.sourcegitcommit: 183b6248807f600fe7d83daa13a6fe0b0f0dc846
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70148009"
---
# <a name="start-designing-and-prototyping"></a>디자인 및 프로토타입 생성 시작


![구성 요소](images/text_in_unity_viewingangle.jpg)

## <a name="what-are-the-core-concepts-of-an-experience"></a>환경의 핵심 개념은 무엇인가요?

### <a name="keep-the-user-comfortable---comfortcomfortmd"></a>[사용자를 편안하게 유지 - (편안함)](comfort.md)
헤드 마운트 디스플레이에서 최대한 편안하도록 하려면 디자이너와 개발자가 이러한 신호가 자연계에서 작동하는 방식을 모방하는 방식으로 콘텐츠를 만들고 표시해야 합니다.

<br>

### <a name="consider-how-the-user-sees-the-world---holographic-frameholographic-framemd"></a>[사용자에게 세계를 표시하는 방법 고려 - (홀로그램 프레임)](holographic-frame.md)
사용자는 헤드셋에서 구동하는 사각형 뷰포트를 통해 혼합 현실의 세계를 볼 수 있습니다. HoloLens에서 이 사각형 영역은 홀로그램 프레임이라고 하며, 사용자는 이를 통해 주변의 실제 세계에 겹쳐진 디지털 콘텐츠를 볼 수 있습니다.

<br>

### <a name="making-holographic-objects-feel-real---spatial-mappingspatial-mappingmd"></a>[홀로그램 개체를 실제적으로 느끼도록 만들기 - (공간 매핑)](spatial-mapping.md)
공간 매핑을 사용하면 개체를 실제 표면에 배치할 수 있습니다. 이렇게 하면 사용자의 세계에서 개체를 고정하고 실제 세계 깊이 신호를 활용할 수 있습니다.

<br>

### <a name="suggesting-the-scale-of-an-object---scalescalemd"></a>[개체 크기 조정 제안 - (크기 조정)](scale.md)
홀로그램 형태로 사실적으로 보이는 콘텐츠를 표시하는 핵심 요소는 실제 세계의 시각적 통계를 최대한 긴밀하게 모방하는 것입니다. 즉, 실제 세계에서 개체의 위치, 크기 및 구성 요소를 이해하는 데 도움이 될 수 있는 만큼 시각적 신호를 최대한 많이 통합해야 합니다.

<br>

### <a name="clear-and-readable-typographytypographymd"></a>[명확하고 읽기 가능한 입력 체계](typography.md)
2D 화면의 입력 체계처럼 목표는 명확하고 읽기 쉬운 것입니다. 혼합 현실의 3차원 측면에서는 텍스트와 사용자 환경 전체에 훨씬 더 큰 영향을 줄 수 있는 기회가 있습니다.

<br>

### <a name="color-light-and-materialscolor-light-and-materialsmd"></a>[색, 광원 및 재질](color,-light-and-materials.md)
혼합 현실용 콘텐츠를 디자인하려면 환경에서 사용되는 시각적 자산 각각에 대한 색, 조명 및 재질을 신중하게 고려해야 합니다.


<br>

---



![상호 작용 디자인 요소](images/MRTK_BoundingBox_Main.png)

## <a name="interaction-design-factors-to-consider"></a>고려할 상호 작용 디자인 요소


### <a name="expanding-the-design-process-for-mixed-realitycase-study-expanding-the-design-process-for-mixed-realitymd"></a>[혼합 현실의 디자인 프로세스 확장](case-study-expanding-the-design-process-for-mixed-reality.md)
2016년 Microsoft에서 열정적인 개발자를 대상으로 하는 HoloLens를 시작함에 따라 팀에서 이미 Microsoft 내외부의 스튜디오와 제휴하여 디바이스의 시작 환경을 구축했습니다. 이러한 팀은 혼합 현실 디자인의 새로운 분야에서 기회와 과제를 모두 수행하고 찾아냄으로써 학습했습니다.

<br>

### <a name="types-of-mixed-reality-appstypes-of-mixed-reality-appsmd"></a>[혼합 현실 앱의 종류](types-of-mixed-reality-apps.md)
Windows Mixed Reality용 앱 개발의 장점 중 하나는 플랫폼에서 지원할 수 있는 다양한 환경이 있다는 것입니다. Windows Mixed Reality는 완전 몰입형 가상 환경에서 사용자의 현재 환경에 대한 경량 정보 계층화까지 모든 환경에 생동감을 주는 강력한 도구 세트를 제공합니다.

<br>

### <a name="choose-an-interaction-model-for-your-customerinteraction-fundamentalsmd"></a>[고객을 위한 상호 작용 모델 선택](interaction-fundamentals.md)
간단하고 직관적인 상호 작용이라는 철학은 혼합 현실 플랫폼 전반에 얽혀 있습니다. 애플리케이션 디자이너와 개발자가 고객에게 쉽고 직관적인 상호 작용을 제공할 수 있도록 하는 3단계를 살펴보았습니다.

<br>

### <a name="hands-and-motion-controllershands-and-toolsmd"></a>[실습 및 모션 컨트롤러](hands-and-tools.md)
2D 화면의 입력 체계처럼 목표는 명확하고 읽기 쉬운 것입니다. 혼합 현실의 3차원 측면에서는 텍스트와 사용자 환경 전체에 훨씬 더 큰 영향을 줄 수 있는 기회가 있습니다.

<br>

### <a name="voice-commandingvoice-designmd"></a>[음성 명령](voice-design.md)
음성 명령을 사용하는 경우 응시는 일반적으로 타기팅 메커니즘, 즉 포인터("선택")로서 또는 애플리케이션으로 명령을 보내기 위해("보기, 말하기") 사용됩니다.

<br>

### <a name="leveraging-the-users-eye-gazeeye-trackingmd"></a>[사용자의 눈길 활용 - 응시](eye-tracking.md)
HoloLens 2는 사용자가 보고 있는 대상에 대한 정보를 사용할 수 있는 기능을 개발자에게 제공하여 홀로그램 환경 내에서 이해할 수 있는 새로운 수준의 컨텍스트 및 사용자를 허용합니다.


<br>


---

## <a name="choose-a-prototyping-option"></a>프로토타입 생성 옵션 선택  





:::row:::
    :::column:::
        <img alt="Unity Logo" width="70" height="70" src="images/unity_logo.png">
         <a href="https://learn.unity.com/" target="">Learn Unity</a>
        Learn how to create interactive experiences with Unity
    :::column-end:::
        :::column:::
       <img alt="MRTK Logo" width="70" height="70" src="images/MRTK_Logo_Sq_Text.png">
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="">Mixed Reality Toolkit</a> - Mixed Reality Toolkit의 공간 상호 작용과 UI 구성 요소를 사용하면 Unity에서 혼합 현실 디자인 및 개발을 시작할 수 있습니다.
    :::column-end:::
    :::column:::
        <img alt="MRDL Logo" width="70" height="70" src="images/MRDL_Logo_Sq_Text.png">
         <a href="https://github.com/Microsoft/MRDL_Unity_PeriodicTable" target="">Mixed Reality Design Labs</a>
        Mixed Reality Design Lab's sample apps shows how to use MRTK's building blocks to create beautiful mixed reality experiences.
    :::column-end:::
    :::column:::
        <img alt="Maquette Logo" width="70" height="70" src="images/MicrosoftMaquette_logo_glow.png">
         <a href="https://www.maquette.ms/" target="">Microsoft Maquette</a>
        Design for VR. Microsoft Maquette makes spatial prototyping easy, quick, and immersive.
    :::column-end:::
:::row-end:::


<br>

---



## <a name="what-would-you-like-to-do-next"></a>다음에 수행할 작업은 무엇인가요?


:::row:::
    :::column:::
       ![기본 사항 이해](images/icon-lightbulb.jpg)
        ### [Understand the basics](index-hidden.md)
        Get a better understanding of what defines mixed reality and how it’s being used.
    :::column-end:::
    :::column:::
        ![Install the tools](images/icon-design.jpg)
         ### [Install the tools](install-the-tools.md)
        Use the installation checklist to get the tools you need to build applications for Microsoft HoloLens and Windows Mixed Reality.
    :::column-end:::
    :::column:::
        ![Come to an event](images/icon-calendar.jpg)
         ### [Come to an event](sf-academy-events.md)
        See the hardware and get a hands-on tutorial to make your first HoloLens 2 application.
    :::column-end:::
    :::column:::
        ![Start developing](images/icon-developer.jpg)
         ### [Start developing](development-hidden.md)
        Choose a development path based on your skill level, work style. or platform interest.
    :::column-end:::
:::row-end:::



