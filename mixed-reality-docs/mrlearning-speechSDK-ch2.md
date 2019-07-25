---
title: MR Learning SpeechSDK 모듈-음성 인식 및 기록
description: 이 과정을 완료 하 여 혼합 현실 응용 프로그램 내에서 Azure Speech SDK를 구현 하는 방법을 알아보세요.
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: e8dc5da5a089079ba38a26969df6070af8bc6200
ms.sourcegitcommit: c7c7e3c836373b65e319609b4e8389dea6b081de
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460300"
---
# <a name="2----adding-an-offline-mode-for-local-speech-to-text-translation"></a>2.    로컬 음성-텍스트 번역을 위한 오프 라인 모드 추가

이 자습서에서는 Azure 서비스에 연결할 수 없는 경우 로컬 음성-텍스트 변환을 수행할 수 있도록 하는 오프 라인 모드를 추가 합니다. 또한 연결 되지 않은 상태를 *시뮬레이션* 합니다.

1. 계층에서 Lunarcom_Base 개체를 선택 하 고 검사기 패널에서 구성 요소 추가를 클릭 합니다. Lunarcom 오프 라인 인식을 검색 하 고 선택 합니다.

![Module4Chapter2step1im](images/module4chapter2step1im.PNG)

2. LunarcomOfflineRecognizer의 드롭다운을 클릭 하 고 사용을 선택 합니다. 이 프로그램은 사용자가 연결 되지 않은 것 처럼 작동 하는 프로젝트를 프로그램 합니다. 

![Module4Chapter2step1im](images/module4chapter2step2im.PNG)

3. 이제 Unity 편집기에서 play를 눌러 테스트 합니다. 장면에서 왼쪽 아래 모서리에 있는 마이크를 누르고 말하기를 시작 합니다. 

> [!NOTE]
> 오프 라인 상태 이기 때문에 절전 모드 해제 단어 기능이 사용 하지 않도록 설정 되었습니다. 오프 라인에서 음성이 인식 될 때마다 마이크를 물리적으로 클릭 해야 합니다. 

다음은 장면이 표시 되는 모양의 예입니다.

![Module4Chapter2exampleim](images/module4chapter2exampleim.PNG)

## <a name="congratulations"></a>축하합니다.

오프 라인 모드를 사용 하도록 설정 했습니다. 이제 오프 라인 상태인 경우에도 음성 SDK를 사용 하 여 프로젝트에 대 한 작업을 수행할 수 있습니다. 


[다음 자습서: 3.  Azure Cognitive Services speech translation 구성 요소 추가](mrlearning-speechSDK-ch3.md)

