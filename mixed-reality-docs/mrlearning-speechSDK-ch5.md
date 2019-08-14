---
title: MR Learning SpeechSDK 모듈-음성 인식 및 기록
description: 이 과정을 완료 하 여 혼합 현실 응용 프로그램 내에서 Azure Speech SDK를 구현 하는 방법을 알아보세요.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: 43a6f02eaf09fcf43775374fae4fbe2d0bc8c346
ms.sourcegitcommit: 599bbdd861ce6ff11b6cfb345a0a995f8b7bf85b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68977985"
---
# <a name="speech-sdk-learning-module---rocket-launcher-control-using-speech-commands"></a>Speech SDK 학습 모듈-음성 명령을 사용 하 여 로켓 시작 관리자 제어

이 단원에서는 Azure Speech Service의 의도 기능을 사용 하 여 음성의 의도를 이해 합니다. 검색 된 음성을 음성 명령으로 사용 하 여 로켓 시작 관리자를 제어 합니다. 이 단원에서는 로켓 시작 기 자산을 가져오고 검색 된 의도 음성 명령을 미리 정의 된 제어 단추에 인터페이스 하 여 로켓을 제어 합니다. 

## <a name="objectives"></a>목표

- 음성 의도를 음성 명령으로 연결 하는 방법을 알아봅니다.
- 음성 의도 음성 명령을 로켓 컨트롤 입력 명령으로 사용 하는 방법에 대해 알아봅니다.

## <a name="instructions"></a>지침
1. 이 자습서에서는 "BaseModule" 자산을 사용 하 여 로켓 시작 관리자를 음성 명령과 통합 합니다. 이를 위해 프로젝트에 자산을 가져와야 합니다. 이 [링크](https://github.com/microsoft/MixedRealityLearning/releases/tag/1.2)를 사용 하 여 "로켓 시작 관리자" 자산을 다운로드할 수 있습니다. 

2. 자산을 가져오려면 자산-> 가져오기 패키지-> 사용자 지정 패키지-> 다운로드 한 파일로 이동 하 여 가져오기를 클릭 합니다.

![module4chapter5step1](images/module4chapter5step1.PNG)

3. "기본 모듈 자산" 자산을 가져온 후 "기본 모듈 자산" 폴더 > Prefabs-> "로켓 Launcher_Complete"를 선택 하 고 기존 장면 계층 구조에 끌어다 놓습니다.

![module4chapter5step2](images/module4chapter5step2.PNG)

4. 이제 "로켓 시작 관리자"를 이전 단원 [단원](mrlearning-speechSDK-ch4.md)에서 작업 한 LUIS 프로젝트와 통합 해야 합니다. 이렇게 하려면 계층에서 "로켓 Launcher_Complete" prefab를 확장 하 고 "LaunchRoundButton", "ResetRoundButton" 및 "배치 힌트" 단추를 찾습니다.

![module4chapter5step3](images/module4chapter5step3.PNG)

5. "LaunchRoundButton"를 선택 하 고 검사기 패널에서 "Interactable"로 이동 하 고 이벤트 "OnClick ()" 아래에서 "LunarModule" prefab를 끌어서 놓습니다. 그런 다음 함수 드롭다운을 선택 하 고 "LunarModule"를 선택한 다음 "StartThruster ()" 함수로 이동 하 여 선택 합니다.

![module4chapter5step 3.0](images/module4chapter5step3.0.PNG)

![module4chapter5step3a](images/module4chapter5step3a.PNG)

6. "ResetRoundButton"를 선택 하 고 검사기 패널에서 "Interactable"로 이동 하 고 이벤트 "OnClick ()" 아래에서 "LunarModule" prefab를 끌어서 놓습니다. 그런 다음 함수 드롭다운을 선택 하 고 "LunarModule"를 선택한 다음 "resetModule ()" 함수로 이동 하 여 선택 합니다.

![module4chapter5step3b](images/module4chapter5step3b.PNG)

7. "배치 힌트"를 선택 하 고, 검사기 패널에서 "Interactable"로 이동 하 고 이벤트 "OnClick ()" 아래에서 "LunarModule" prefab를 끌어 놓습니다. 그런 다음 함수 드롭다운을 선택 하 고 "LunarModule"를 선택한 다음 "TogglePlacementHints" 함수로 이동 하 여 ToggleGameOBjects ()를 선택 합니다.

![module4chapter5step3c](images/module4chapter5step3c.PNG)

8.  그런 다음, 계층에서 Lunarcom_Completed prefab를 선택 하 고 검사기에서 "Lunarcom 의도 인식기" 스크립트로 이동한 다음 "LaunchRoundButton", "ResetRoundButton" 및 "배치 힌트" 단추를 해당 위치에 끌어서 놓습니다.

![module4chapter5step4](images/module4chapter5step4.PNG)

9. Unity 편집기에서 재생 단추를 누르고 "로켓" 단추를 클릭 하 고 "로켓" 단추를 클릭 하 고, "utter" 단추를 클릭 하 고, "rest 단추를 누릅니다.", "rest 단추를 누릅니다." 또는 다른 구를 클릭 하 여 로켓 시작 관리자에 대 한 시작, 다시 설정 또는 힌트 요청을 수행 합니다.

![module4chapter5step5a](images/module4chapter5step5a.PNG)

![module4chapter5step5b](images/module4chapter5step5b.PNG)

![module4chapter5step5c](images/module4chapter5step5c.PNG)

## <a name="congratulations"></a>축하합니다.

이 단원에서는 AI 지원 음성 명령을 음성 명령에 연결 하 여 입력 방법으로 사용 하는 방법을 배웠습니다. 이제 프로그램에서 음성 명령으로 스피커 의도를 사용 하 여 로켓 시작 관리자에 대 한 입력을 제공할 수 있습니다.

