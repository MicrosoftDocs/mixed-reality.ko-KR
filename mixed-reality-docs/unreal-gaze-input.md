---
title: Unreal에서 입력 응시
description: HoloLens 및 Unreal Engine에 대 한 응시 입력 설정 자습서
author: hferrone
ms.author: v-haferr
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality, holograms, HoloLens 2, 눈 추적, 응시 입력, 헤드 탑재 된 디스플레이, Unreal engine
ms.openlocfilehash: 0bc8b83a2e840b066eb5e30665584e1c68f7b021
ms.sourcegitcommit: 7f50210b71a65631fd1bc3fdb215064e0db34333
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84551809"
---
# <a name="gaze-input"></a>응시 입력

## <a name="overview"></a>개요

[Windows Mixed Reality 플러그인](https://docs.unrealengine.com/Platforms/VR/WMR/index.html) 은 응시 입력을 위한 기본 제공 함수를 제공 하지 않지만 HoloLens 2는 눈 추적을 지원 합니다. 실제 추적 기능은 Unreal의 **탑재 된 표시** 및 **눈 추적** api에서 제공 하며 다음을 포함 합니다.

- 장치 정보
- 추적 센서
- 방향 및 위치
- 창 클리핑
- 데이터 및 추적 정보를 응시 합니다.

모든 기능의 전체 목록은 실제 [헤드 탑재 된 표시](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) 및 [눈 추적](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) 설명서에서 확인할 수 있습니다.

Unreal Api 외에도 HoloLens 2에 대 한 눈에 잘 맞는 [상호 작용](eye-gaze-interaction.md) 에 대 한 설명서를 확인 하 고 [hololens 2의 눈 추적](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) 작동 방식을 확인 하세요.

> [!IMPORTANT]
> 아이 추적은 HoloLens 2 에서만 지원 됩니다.

## <a name="enabling-eye-tracking"></a>눈 추적 사용
Unreal의 Api를 사용 하려면 먼저 HoloLens 프로젝트 설정에서 응시 입력을 사용 하도록 설정 해야 합니다. 응용 프로그램이 시작 되 면 아래 스크린샷에 표시 된 동의 프롬프트가 표시 됩니다.

- **예** 를 선택 하 여 사용 권한을 설정 하 고 입력에 대 한 액세스 권한을 얻습니다. 언제 든 지이 설정을 변경 해야 하는 경우 **설정** 앱에서 찾을 수 있습니다.

![눈 입력 권한](images/unreal/eye-input-permissions.png)

> [!NOTE] 
> Unreal의 HoloLens 눈동자 추적에는 stereoscopic 추적에 필요한 두 광선 (지원 되지 않음)이 아닌 단일 응시 광선이 있습니다.

이를 통해 모든 설정에서 HoloLens 2 앱에 응시 입력을 Unreal에 추가 하기 시작 해야 합니다. 입력 응시에 대 한 자세한 내용 및 혼합 현실의 사용자에 게 영향을 주는 방법에 대 한 자세한 내용은 아래 링크를 참조 하세요. 대화형 환경을 구축할 때이에 대해 생각해 야 합니다.

## <a name="see-also"></a>참고 항목
* [보정](calibration.md)
* [편안함](comfort.md)
* [응시 및 커밋](gaze-and-commit.md)
* [음성 입력 ](voice-design.md)
