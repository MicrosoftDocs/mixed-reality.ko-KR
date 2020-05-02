---
title: Azure Speech Services 자습서 - 3. Azure Cognitive Services 음성 번역 구성 요소 추가
description: 이 과정에서는 혼합 현실 애플리케이션 내에서 Azure Speech SDK를 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: d8e73e24f0522ff71b95ea1886d59893216b0597
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/29/2020
ms.locfileid: "79028333"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a>3. Azure Cognitive Services 음성 번역 구성 요소 추가

이 자습서에서는 음성 번역을 프로젝트에 추가하여 음성을 세 가지 언어로 번역하고 전사할 수 있습니다.

## <a name="objectives"></a>목표

* Azure 음성 번역을 통합하는 방법 알아보기

## <a name="instructions"></a>지침

[계층 구조] 창에서 **Lunarcom** 개체를 선택한 다음, [검사기] 창에서 **구성 요소 추가** 단추를 사용하여 **Lunarcom 번역 인식기(스크립트)** 구성 요소를 Lunarcom 개체에 추가하고 다음과 같이 구성합니다.

* **대상 언어**를 선택한 언어(예: _독일어_)로 변경합니다.

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-1.png)

> [!NOTE]
> Lunarcom 번역 인식기(스크립트) 구성 요소는 MRTK의 일부가 아닙니다. 이 자습서의 자산과 함께 제공되었습니다.

이제 게임 모드로 들어가면 먼저 위성 단추를 눌러 음성 번역을 테스트할 수 있습니다. 그런 다음, 마이크가 컴퓨터에 있다고 가정하여 사용자가 무언가를 말하면 음성이 선택한 언어로 번역되어 터미널 패널에 전사됩니다.

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-2.png)

> [!CAUTION]
> 애플리케이션에서 Azure에 연결해야 하므로 컴퓨터/디바이스가 인터넷에 연결되어 있는지 확인합니다.

## <a name="congratulations"></a>축하합니다.

이제 프로젝트에서 사용자가 말하는 단어를 여러 다른 언어로 성공적으로 번역할 수 있습니다. 디바이스에서 애플리케이션을 실행하여 기능이 제대로 작동하는지 확인합니다.

[다음 자습서: 4. 의도 및 자연어 이해 설정](mrlearning-speechSDK-ch4.md)
