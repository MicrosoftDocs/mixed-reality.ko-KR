---
title: 음성 입력
description: 음성 입력을 사용 하는 방법을 설명 합니다.
author: AndreyChistyakov
ms.author: anchisty
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality, HoloLens
ms.openlocfilehash: d61a9f9d40c76c8872ff0a1b39d65f95ae88d2b7
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835323"
---
# <a name="voice-input"></a>음성 입력

HoloLens에서 음성 인식을 사용 하도록 설정 하려면 개발자가 프로젝트 설정 > Platform > HoloLens > 기능에서 사용 하지 않는 편집기에서 "마이크"를 사용 하도록 설정 해야 합니다. 또한 장치는 설정 > 개인 정보 > 음성에서 음성 인식을 사용 하도록 설정 하 고 영어를 사용 해야 합니다.

![Windows 음성 인식 설정](images/unreal/speech-recognition-settings.png)

가능한 최상의 서비스 품질을 위해 온라인 음성 인식을 사용 하도록 설정 하는 것이 좋습니다. HoloLens의 음성 인식에 대 한 기술 세부 정보는 여기를 참조 [하세요](voice-input.md) .

그러면 응용 프로그램이 처음 시작 될 때 마이크를 사용 하도록 설정 하는 대화 상자가 표시 됩니다. 사용자가 예를 선택 하면 응용 프로그램이 음성 입력을 시작 합니다.

음성 입력에는 특별 한 Windows Mixed Reality API가 필요 하지 않으며, 대신 기존 Unreal Engine 4 입력 매핑 API를 기반으로 합니다. 입력 API를 사용 하는 방법에 대 한 자세한 내용은 [여기](https://docs.unrealengine.com/en-US/Gameplay/Input/index.html) 를 참조 하세요.

음성 매핑이 엔진 – 아래 작업 및 축 매핑의 바인딩 섹션에 추가 되었습니다. 

![UE4 엔진 입력 설정은](images/unreal/engine-input.png)
 
다음은 "점프" 전 세계 모니터링을 추가 하는 예제입니다. 모든 영어 단어 또는 짧은 문장을 사용할 수 있습니다. 

프로젝트 설정을 통해 음성 매핑을 추가한 후에는 다음 예제와 같이 개발자가 표준 Unreal 논리를 사용 하 여 입력을 처리할 수 있습니다. 
 
![음성에 대 한 간단한 작업](images/unreal/input-action-bp.png)
