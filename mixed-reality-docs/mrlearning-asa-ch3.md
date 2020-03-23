---
title: Azure Spatial Anchors 자습서 - 3. Azure Spatial Anchor 피드백 표시
description: 이 과정을 완료하면 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 이해할 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 11342bada65e963db6393d35c99e2c2fbffe8ff1
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031262"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a>3. Azure Spatial Anchor 피드백 표시

이 자습서에서는 ASA(Azure Spatial Anchors)를 사용할 때 사용자에게 앵커 검색, 이벤트 및 상태에 대한 피드백을 제공하는 방법에 대해 알아봅니다.

## <a name="objectives"></a>목표

* 현재 ASA 세션에 대한 중요한 정보를 표시하는 UI 패널을 설정하는 방법 알아보기
* 사용자가 ASA SDK를 사용할 수 있도록 하는 피드백 요소 이해 및 살펴보기

## <a name="set-up-asa-feedback-ui-panel"></a>ASA 피드백 UI 패널 설정

[계층 구조] 창에서 마우스 오른쪽 단추로 **Instructions** > **TextContent** 개체를 클릭하고, **3D 개체** > **텍스트 - TextMeshPro**를 선택하여 TextMeshPro 텍스트 개체를 Instructions > TextContent 개체의 자식 항목으로 만들고, 적절한 이름(예: **Feedback**)을 지정합니다.

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-1.png)

> [!TIP]
> 장면 작업을 더 쉽게 수행할 수 있도록 개체 왼쪽의 눈 아이콘을 클릭하여 ParentAnchor 개체에 대한 <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">장면 표시 유형</a>을 끄기로 설정합니다. 이렇게 하면 게임 내 표시 유형을 변경하지 않고 [장면] 창에서 개체를 숨깁니다.

명령 텍스트 아래에 깔끔하게 배치되도록 **Feedback** 개체를 선택한 채로 [검사기] 창에서 위치와 크기를 변경합니다. 예를 들어 다음과 같습니다.

* 사각형 변환 **세로 위치**를 -0.24로 변경
* 사각형 변환 **너비**를 0.555로 변경
* 사각형 변환 **높이**를 0.1로 변경

그런 다음, 텍스트가 텍스트 영역 내에 깔끔하게 맞추도록 글꼴 속성을 선택합니다.

* Text Mesh Pro(스크립트) **글꼴 스타일**을 [굵게]로 변경
* Text Mesh Pro(스크립트) **글꼴 크기**를 0.17로 변경
* Text Mesh Pro(스크립트) **맞춤**을 [가운데] 및 [중간]으로 변경

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-2.png)

**Feedback** 개체를 선택한 채로 [검사기] 창에서 **구성 요소 추가** 단추를 사용하여 **앵커 피드백 스크립트(스크립트)** 구성 요소를 Feedback 개체에 추가합니다.

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-3.png)

**Feedback** 개체 자체를 **앵커 피드백 스크립트(스크립트)** 구성 요소의 **피드백 텍스트** 필드에 할당합니다.

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-4.png)

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 사용자에게 실시간 피드백을 제공하기 위해 Azure Spatial Anchor 환경의 현재 상태를 표시하는 UI 패널을 만드는 방법을 알아보았습니다.
