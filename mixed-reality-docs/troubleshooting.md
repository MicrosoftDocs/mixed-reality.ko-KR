---
title: HoloLens 문제 해결
description: Microsoft HoloLens의 문제 해결 단계입니다.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 문제, 버그, 문제 해결, 수정, 도움말, 지원, HoloLens
ms.openlocfilehash: 855bb0cafb0d3fba0d8d97c93d9415b51bcc2fb3
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438276"
---
# <a name="hololens-troubleshooting"></a>HoloLens 문제 해결

## <a name="my-hololens-is-unresponsive-or-wont-boot"></a>HoloLens가 응답 하지 않거나 부팅할 수 없습니다.

HoloLens가 부팅 되지 않는 경우:
* 전원 단추의 Led가 켜지 지 않거나 LED가 잠시 깜박일 경우 HoloLens를 청구 해야 할 수 있습니다.
* 전원 단추를 누를 때 Led가 켜져 있지만 디스플레이에 아무 것도 표시 되지 않으면 전원 단추를 눌러 Led의 5 가지를 모두 끌 때까지 전원 단추를 누릅니다.

HoloLens가 고정 되거나 응답 하지 않는 경우:
* 전원 단추를 누르면 Led의 5 개가 모두 꺼집니다. 또는 Led가 응답 하지 않는 경우 10 초 동안 전원 단추를 눌러 HoloLens를 끕니다. 부팅 하려면 전원 단추를 다시 누릅니다.

이러한 단계가 작동 하지 않는 경우:
* [장치를 복구](reset-or-recover-your-hololens.md)해 볼 수 있습니다.

## <a name="holograms-dont-look-good-or-are-moving-around"></a>Holograms는 좋지 않거나 이동 하지 않습니다.

Holograms 안정적이 지 않거나, jumpy, 적절 하지 않은 경우 다음 해결 방법 중 하나를 시도해 보세요.
* 장치 센터를 정리 하 고 어떤 것도 센서가 방해 하지 않는지 되는지 확인 합니다.
* 대화방에 충분 한 조명이 있는지 확인 합니다.
* HoloLens를 살펴보고 HoloLens를 확인 하 여 HoloLens를 보다 완벽 하 게 검색할 수 있도록 해 보세요.
* 보정 앱을 실행 해 보세요. 보정는 HoloLens에 가장 적합 한 작업을 수행 합니다. **설정** > **시스템** > **유틸리티**로 이동 합니다. 보정 아래에서 **보정 열기**를 선택 합니다.
* 보정 앱을 실행 한 후에도 여전히 문제가 발생 하는 경우 센서 튜닝 앱을 사용 하 여 장치 센서를 조정 합니다. **설정** > **시스템** > **유틸리티**로 이동 합니다. 센서 조정에서 **열기 센서 튜닝**을 선택 합니다.

## <a name="hololens-doesnt-respond-to-my-gestures"></a>HoloLens는 내 제스처에 응답 하지 않습니다.

HoloLens가 제스처를 볼 수 있도록 하려면 한 쪽에서 몇 피트를 연장 하는 제스처 프레임으로 손을 두세요. HoloLens가 손을 볼 수 있는 경우 커서가 점에서 링으로 바뀝니다. [제스처](gaze-and-commit.md#composite-gestures)사용에 대해 자세히 알아보세요.

환경이 너무 어두운 경우 HoloLens에 손을 표시 되지 않으므로 충분 한 빛이 있는지 확인 하세요.

센터에 지문 또는 얼룩이 있는 경우 HoloLens와 함께 제공 되는 마이크로 파이버 클리닝 천을 사용 하 여 센터를 천천히 정리 하세요.

## <a name="hololens-doesnt-respond-to-my-voice-commands"></a>HoloLens는 내 음성 명령에 응답 하지 않습니다.

Cortana가 음성 명령에 응답 하지 않는 경우 Cortana가 켜져 있는지 확인 합니다. 모든 앱 목록에서 Cortana > 메뉴 > 노트북 > 설정을 선택 하 여 변경 합니다. 설명 하는 내용에 대 한 자세한 내용은 음성을 사용 하 여 HoloLens 제어를 참조 하세요.

## <a name="i-cant-place-holograms-or-see-holograms-i-previously-placed"></a>Holograms를 배치 하거나 이전에 배치한 holograms을 확인할 수 없습니다.

HoloLens가 공간을 매핑하거나 로드할 수 없는 경우 제한 된 모드로 전환 되며 holograms를 배치 하거나 사용자가 배치한 holograms을 볼 수 없습니다. 다음의 몇 가지 조치를 시도해 볼 수 있습니다.
* 사용자 환경에 충분 한 조명이 있는지 확인 하 여 HoloLens가 공간을 보고 매핑할 수 있도록 합니다.
* Wi-fi 네트워크에 연결 되어 있는지 확인 합니다. Wi-fi에 연결 되지 않은 경우 HoloLens는 알려진 공간을 식별 하 고 로드할 수 없습니다.
* 새 공간을 만들어야 하는 경우 Wi-fi에 연결한 다음 HoloLens를 다시 시작 합니다.
* 올바른 공간이 활성화 되어 있는지 확인 하거나 공간을 수동으로 로드 하려면 **설정** > **시스템** > **공간**으로 이동 합니다.
* 올바른 공간이 로드 되 고 문제가 여전히 발생 하는 경우 공간이 손상 된 것일 수 있습니다. 이 문제를 해결 하려면 공간을 선택 하 고 제거를 선택 합니다. 공간이 제거 되 면 HoloLens는 환경 매핑을 시작 하 고 새 공간을 만듭니다.

## <a name="my-hololens-frequently-enters-limited-mode-or-shows-a-tracking-lost-message"></a>내 HoloLens는 제한 된 모드로 자주 들어가거나 "손실 추적" 메시지를 표시 합니다.

장치가 "제한 된 모드" 또는 "손실 추적" 메시지를 자주 표시 하는 경우 내 Holograms에서 제안 하는 [것이 좋지 않거나 이동 하지](#holograms-dont-look-good-or-are-moving-around)않습니다.

## <a name="my-hololens-cant-tell-what-space-im-in"></a>내 HoloLens에서 어떤 공간이 있는지 확인할 수 없습니다.

HoloLens에서 사용 중인 공간을 자동으로 식별 하 고 로드할 수 없는 경우 Wi-fi에 연결 되어 있는지 확인 하 고, 대화방에 많은 빛이 있으며, 주변에 대 한 주요 변경 내용이 없습니다. **설정** > **시스템** > **공간**으로 이동 하 여 공간을 수동으로 로드 하거나 공간을 관리할 수도 있습니다.

## <a name="im-getting-a-low-disk-space-error"></a>"디스크 공간 부족" 오류가 발생 합니다.

다음 중 하나 이상을 수행 하 여 저장소 공간을 확보 해야 합니다.
* 사용 하지 않는 공간을 삭제 합니다. **설정** > **시스템** > **공간**으로 이동 하 여 더 이상 필요 하지 않은 공간을 선택 하 고 **제거**를 선택 합니다.
* 배치한 holograms 중 일부를 제거 합니다.
* 사진 앱에서 일부 그림과 비디오를 삭제 합니다.
* HoloLens에서 일부 앱을 제거 합니다. 모든 앱 목록에서 제거 하려는 앱을 탭 하 고 누른 다음 **제거**를 선택 합니다.

## <a name="my-hololens-cant-create-a-new-space"></a>HoloLens에서 새 공간을 만들 수 없습니다.

가장 가능성이 높은 문제는 저장소 공간이 부족 하다는 것입니다. [위의 팁](#im-getting-a-low-disk-space-error) 중 하나를 사용 하 여 디스크 공간을 확보 하세요.
