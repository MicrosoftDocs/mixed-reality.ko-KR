---
title: HoloLens 문제 해결
description: Microsoft HoloLens 대 한 문제 해결 단계입니다.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 문제, 버그, 문제 해결, 수정, 도움말, 지원, HoloLens
ms.openlocfilehash: 7b7a32a9a358ff75b2675d265445d9ef1acc1b9e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597575"
---
# <a name="hololens-troubleshooting"></a>HoloLens 문제 해결

## <a name="my-hololens-is-unresponsive-or-wont-boot"></a>내 HoloLens 응답 하지 않거나 부팅 되지 않습니다.

HoloLens에 부팅할 수 없는 경우:
* 전원 단추에서 Led light 없는 경우 최신, 또는 1 개의 LED를 깜빡이는 간단 하 게, HoloLens에 요금을 청구 해야 할 수 있습니다.
* 전원 단추를 누르면 표시 하는 아무 것도 표시 되지 경우는 led가 켜 집니다, 5 개 전원 단추에서 Led 모두 해제 될 때까지 전원 단추를 누르고 있으면 됩니다.

HoloLens에 고정 되었거나 응답 하지 않는 경우:
* 전원 단추에서 Led의 모든 5 / 자체 끄기, 10 초 동안 Led 응답성이 아닌 경우까지 전원 단추를 눌러 프로그램 HoloLens를 해제 합니다. 다시 부팅 하도록 전원 단추를 누릅니다.

이러한 단계가 작동 하지 않습니다.
* 시도할 수 있습니다 [장치의 복구](reset-or-recover-your-hololens.md)합니다.

## <a name="holograms-dont-look-good-or-are-moving-around"></a>홀로그램 좋지 않아 또는 이동 됩니다.

여 홀로그램 불안정 한, 변화가 심하거, 또는 올바르지 않은 경우 이러한 수정 사항의 하나를 시도 합니다.
* 사용자 장치 하이퍼바이저를 정리 하 고 센서 데 방해가 되는 아무 작업도 수행 해야 합니다.
* 방에 light 충분 한지 확인 합니다.
* 시도 따라 이동 하 고 따라서 HoloLens 주변 환경에 찾고 검사 더욱 완전 하 게 합니다.
* 보정 앱을 실행 해 보세요. 이 눈에 대 한 가장 잘 작동 하 여 HoloLens 보정 합니다. 로 이동 **설정을** > **System** > **유틸리티**합니다. 보정에서 선택 **열고 보정**합니다.
* 여전히 문제가 있는 보정 앱을 실행 한 후, 센서 튜닝 앱 사용 하 여 장치 센서를 조정 합니다. 로 이동 **설정을** > **System** > **유틸리티**합니다. 센서 튜닝 선택 **열고 센서 튜닝**합니다.

## <a name="hololens-doesnt-respond-to-my-gestures"></a>HoloLens 내 제스처에 응답 하지 않습니다.

HoloLens에 제스처를 볼 수 있는지, 직접의 양쪽에서 몇을 확장 하는 제스처 프레임을 유지 합니다. HoloLens 직접 볼 수 커서 링에 점이에서 변경 됩니다. 사용 하 여 자세히 알아봅니다 [제스처](gestures.md)합니다.

환경의 너무 어두운 색 이면 HoloLens 직접 참조 하지 않습니다, 충분 한 light 인지를 확인 하므로 수도 있습니다.

사용자가 있고 하이퍼바이저가 지문 또는 손가락 정리 하 여 하이퍼바이저를 조심 스럽게 정리에 HoloLens와 함께 제공 된 천을 마이크로 파이버를 사용 하십시오.

## <a name="hololens-doesnt-respond-to-my-voice-commands"></a>HoloLens 내 음성 명령에 응답 하지 않습니다.

Cortana 음성 명령에 응답 하지 않는 경우에 Cortana가 켜져 있는지 확인 합니다. 모든 앱 목록에서 Cortana를 선택 > 메뉴 > 노트북 > 설정 변경 내용을 확인 합니다. 말할 수 있습니다 하는 방법에 대 한 자세한 내용은 컨트롤 HoloLens에 음성을 사용 하 여 참조 하세요.

## <a name="i-cant-place-holograms-or-see-holograms-i-previously-placed"></a>홀로그램 배치 하거나 이전에 배치 홀로그램 참조 수 없습니다.

HoloLens 없습니다 매핑하거나 공간에 로드 하는 경우 제한 모드로 됩니다 및 홀로그램 배치 하거나 배치한 홀로그램 참조 수 없습니다. 다음의 몇 가지 조치를 시도해 볼 수 있습니다.
* 있는지 충분 한 light 환경의 HoloLens 확인 하 고 공간에 매핑할 수 있도록 합니다.
* Wi-fi 네트워크에 연결 되어 있는지 확인 합니다. Wi-fi에 연결 되지 않은 경우 HoloLens 식별 하 고 알려진된 공간을 로드할 수 없습니다.
* 새 공간을 만들어야 하는 경우 Wi-fi 연결에 HoloLens를 다시 시작 하십시오.
* 로 이동 하는 경우 올바른 공간이 활성 상태인 경우를 보거나 공간을 수동으로 로드 **설정을** > **System** > **공간**입니다.
* 올바른 공간을 로드 하 고 여전히 문제가 발생 하는 경우 공간 손상 되었을 수 있습니다. 이 해결 하려면 공간을 선택한 다음 제거를 선택 합니다. 공간 제거 되 면 HoloLens 되며 환경 매핑을 시작 합니다. 새 공간을 만듭니다.

## <a name="my-hololens-frequently-enters-limited-mode-or-shows-a-tracking-lost-message"></a>내 HoloLens 자주 제한 모드로 들어가거나 "손실 추적" 메시지가 표시 됩니다.

장치는 종종 "제한 된 모드" 또는 "추적 손실" 메시지를 표시, 시도에서 제안을 [내 홀로그램 좋지 않아 또는 이동 된](#holograms-dont-look-good-or-are-moving-around)합니다.

## <a name="my-hololens-cant-tell-what-space-im-in"></a>내 HoloLens 내가 어떤 공간을 확인할 수 없습니다.

HoloLens에 자동으로 식별 하 고 있는 공간을 로드할 수 없습니다 Wi-fi에 연결 하 고 대화방에 빛의 충분 한 않은 내용이 주요는 주변 환경에 있는지 확인 합니다. 공간을 수동으로 로드 하거나 프로그램 공간으로 이동 하 여 관리할 수도 있습니다 **설정을** > **System** > **공간**입니다.

## <a name="im-getting-a-low-disk-space-error"></a>"디스크 공간 부족" 오류가 발생 했습니다.

다음 중 하나 이상을 수행 하 여 저장소 공간을 확보 해야 합니다.
* 일부 사용 되지 않는 공간 삭제 합니다. 로 이동 **설정을** > **System** > **공백이**, 더 이상 필요 하 고, 한 다음 선택 영역을 선택 합니다 **제거**.
* 배치한 홀로그램 중 일부를 제거 합니다.
* 사진 및 비디오 사진 앱의 일부를 삭제 합니다.
* 에 HoloLens에서 일부 앱을 제거 합니다. 모든 앱 목록에서 페이지를 누르고 앱을 제거 하 고 선택한 **제거**합니다.

## <a name="my-hololens-cant-create-a-new-space"></a>내 HoloLens에 새 공간을 만들 수 없습니다.

가장 가능성이 높은 문제는 부족 하면 저장소 공간입니다. 중 하나를 시도 합니다 [위의 팁](#im-getting-a-low-disk-space-error) 일부 디스크 공간을 확보 합니다.
