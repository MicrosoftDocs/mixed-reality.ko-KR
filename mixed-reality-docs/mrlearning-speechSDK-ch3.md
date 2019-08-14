---
title: Azure Speech Services 자습서-3. Azure Cognitive Services speech translation 구성 요소 추가
description: 이 과정을 완료 하 여 혼합 현실 응용 프로그램 내에서 Azure Speech SDK를 구현 하는 방법을 알아보세요.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: c7cbdca3c22253042a9be44a194fca8925f0f446
ms.sourcegitcommit: 599bbdd861ce6ff11b6cfb345a0a995f8b7bf85b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68977960"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a>3. Azure Cognitive Services speech translation 구성 요소 추가

이 자습서에서는 프로젝트의 Azure Cognitive Services Speech Translation 구성 요소에 대해 알아보고 세 가지 언어로 번역 합니다. 

## <a name="instructions"></a>지침

1. 계층에서 Lunarcom_Base 개체를 선택 하 고 검사기 패널에서 구성 요소 추가를 클릭 합니다. LunarcomTranslationRecognizer를 검색 하 고 선택 합니다.

![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

> 참고: 음성 SDK 변환기를 테스트 하기 전에 오프 라인 모드 시뮬레이터를 사용 하지 않도록 설정 했는지 확인 합니다. 변환 하려면 인터넷에 연결 되어 있어야 합니다. 이 설정을 찾을 수 있는 위치 아래 이미지를 참조 하세요. 
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

2. LunarcomTranslationRecognizer의 드롭다운을 클릭 하 고 번역 하려는 언어를 선택 합니다.

![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. 이제 응용 프로그램을 실행 하 고 위성 단추를 클릭 하 여 변환기를 테스트 하 고 말하기를 시작 합니다. 인식을 중지 하려면 위성 단추를 다시 누릅니다. 다음은 장면이 표시 되는 모양의 예입니다. "대상 언어" 드롭다운 (위의 이미지 참조)에서 언어를 자유롭게 변경 하 여 다른 언어로 번역을 탐색할 수 있습니다.

> 참고: 테스트 하기 전에 아래 이미지에 나와 있는 것 처럼 오프 라인 시뮬레이터를 사용 하지 않도록 설정 해야 합니다.
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

다음은 장면이 표시 되는 모양의 예입니다.

![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a>축하합니다.

이제 프로젝트는 말하는 단어를 여러 언어로 번역할 수 있습니다. 자유롭게 언어를 사용 하 고 번역의 정확도를 테스트할 수 있습니다. 

[다음 자습서: 4. 의도 및 자연어 이해 설정](mrlearning-speechSDK-ch4.md)

