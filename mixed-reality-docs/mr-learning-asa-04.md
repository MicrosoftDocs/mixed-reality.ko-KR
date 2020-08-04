---
title: Azure Spatial Anchors 자습서 - 4. Azure Spatial Anchor 피드백 표시
description: 이 과정을 완료하여 혼합 현실 애플리케이션 내에서 Azure Spatial Anchors를 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: afcd7753fb2296503e67a1977b183df951124560
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376525"
---
# <a name="4-displaying-feedback-from-azure-spatial-anchors"></a>4. Azure Spatial Anchor에서 피드백 표시

이 자습서에서는 ASA(Azure Spatial Anchors)를 사용하여 사용자에게 앵커 검색, 이벤트 및 상태에 대한 피드백을 제공하는 방법에 대해 알아봅니다.

## <a name="objectives"></a>목표

* 현재 ASA 세션에 대한 필수 정보를 표시하는 UI 패널을 설정하는 방법 알아보기
* 사용자가 ASA SDK를 사용할 수 있도록 하는 피드백 요소 알아보기 및 살펴보기

## <a name="setting-up-asa-feedback-panel"></a>ASA 피드백 패널 설정

Hierarchy 창에서 **명령** > **TextContent** 개체를 마우스 오른쪽 단추로 클릭합니다. **3D 개체** > **텍스트 - TextMeshPro**를 선택하여 TextMeshPro 텍스트 개체를 명령 > TextContent 개체의 자식으로 만듭니다.

![mr-learning-asa](images/mr-learning-asa/asa-04-section1-step1-1.png)

> [!TIP]
> 장면 작업을 더 쉽게 수행할 수 있도록 개체 왼쪽의 눈 아이콘을 클릭하여 ParentAnchor 개체에 대한 <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">장면 표시 유형</a>을 끄기로 설정합니다. 이렇게 하면 게임 내 표시 유형을 변경하지 않고 [장면] 창에서 개체를 숨깁니다.

새로 만든 텍스트(TMP) 개체 **Feedback**의 이름을 바꾼 다음, Inspector 창에서 명령 텍스트 아래에 깔끔하게 배치되도록 위치와 크기를 변경합니다. 예를 들어 다음과 같습니다.

* 사각형 변환 구성 요소의 **세로 위치**를 -0.24로 변경합니다.
* 사각형 변환 구성 요소의 **너비**를 0.555로 변경합니다.
* 사각형 변환 구성 요소의 **높이**를 0.1로 변경합니다.

그런 다음, 텍스트가 텍스트 영역 내에 깔끔하게 맞추도록 글꼴 속성을 선택합니다.

* TextMeshPro - 텍스트 구성 요소의 **글꼴 스타일**을 굵게로 변경합니다.
* TextMeshPro - 텍스트 구성 요소의 **글꼴 크기**를 0.17로 변경합니다.
* TextMeshPro - 텍스트 구성 요소의 **맞춤**을 가운데 및 중간으로 변경합니다.

![mr-learning-asa](images/mr-learning-asa/asa-04-section1-step1-2.png)

Hierarchy 창에서 **Feedback** 개체를 선택한 다음, Inspector 창에서 **구성 요소 추가** 단추를 사용하여 **Anchor Feedback Script(스크립트)** 구성 요소를 추가하고 다음과 같이 구성합니다.

* **Feedback** 개체 자체를 **Anchor Feedback Script(스크립트)** 구성 요소의 **피드백 텍스트** 필드에 할당합니다.

![mr-learning-asa](images/mr-learning-asa/asa-04-section1-step1-3.png)

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 UI 패널을 만드는 방법을 알아보았습니다. 사용자에게 실시간 피드백을 제공하기 위한 Azure Spatial Anchors 환경의 현재 상태를 표시합니다.

[다음 자습서: 5. Android 및 iOS용 Azure Spatial Anchors](mr-learning-asa-05.md)
