---
title: Azure Speech Services 자습서 - 2. 로컬 음성-텍스트 변환을 위한 오프라인 모드 추가
description: 이 과정을 완료하여 혼합 현실 애플리케이션 내에서 Azure Speech SDK를 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 75ddce9063bb9d33f5fe2343fe30178222a5f8ac
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031616"
---
# <a name="2-using-speech-recognition-to-execute-commands"></a>2. 음성 인식을 사용하여 명령 실행

이 자습서에서는 Azure 음성 인식을 통해 사용자가 정의하는 단어 또는 구에 따라 작업을 수행할 수 있는 명령을 실행하는 기능을 추가합니다.

## <a name="objectives"></a>목표

* Azure 음성 인식을 사용하여 명령을 실행하는 방법 알아보기

## <a name="instructions"></a>지침

[계층 구조] 창에서 **Lunarcom** 개체를 선택한 다음, [검사기] 창에서 **구성 요소 추가** 단추를 사용하여 **Lunarcom 실행 단어 인식기(스크립트)** 구성 요소를 Lunarcom 개체에 추가하고 다음과 같이 구성합니다.

* **실행 단어** 필드에서 적절한 구를 입력합니다(예: _터미널 활성화_).
* **해제 단어** 필드에서 적절한 구(예: _터미널 해제_)를 입력합니다.

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-1.png)

> [!NOTE]
> Lunarcom 실행 단어 인식기(스크립트) 구성 요소는 MRTK의 일부가 아닙니다. 이 자습서의 자산과 함께 제공되었습니다.

이전 자습서에서와 같이 이제 게임 모드로 들어가면 터미널 패널을 기본적으로 사용하도록 설정되어 있지만, **터미널 해제**라는 해제 단어를 말하여 터미널 패널을 사용하지 않도록 설정할 수 있습니다.

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-2.png)

그리고 **터미널 활성화**라는 실행 단어를 말하여 터미널 패널을 다시 사용하도록 설정합니다.

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-3.png)

> [!CAUTION]
> 애플리케이션에서 Azure에 연결해야 하므로 컴퓨터/디바이스가 인터넷에 연결되어 있는지 확인합니다.

> [!TIP]
> Azure에 자주 연결할 수 없는 것으로 예상되는 경우 [음성 명령 사용](mrlearning-base-ch5.md#enabling-voice-commands) 지침에 따라 MRTK를 사용하여 음성 명령을 구현할 수도 있습니다.

## <a name="congratulations"></a>축하합니다.

Azure에서 구동하는 음성 명령을 구현했습니다. 디바이스에서 애플리케이션을 실행하여 기능이 제대로 작동하는지 확인합니다.

다음 자습서에서는 Azure 음성 번역을 사용하여 음성을 번역하는 방법에 대해 알아봅니다.

[다음 자습서: 3. Azure Cognitive Services 음성 번역 구성 요소 추가](mrlearning-speechSDK-ch3.md)
