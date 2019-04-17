---
title: 다시 설정 하거나 여 HoloLens 복구
description: 다시 부팅 또는 프로그램 HoloLens 재설정에 대 한 기본 및 고급 지침입니다.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 방법, 다시 부팅 다시 설정, 하드 다시 설정, 소프트 다시 설정, 전원 주기가, HoloLens, 종료 복구
ms.openlocfilehash: abf71a5f122b1c6f800bf970f51da11a34be956b
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599880"
---
# <a name="reset-or-recover-your-hololens"></a>다시 설정 하거나 여 HoloLens 복구

다시 시작을 시도 하는 것이 좋습니다에 HoloLens에 문제가 발생 하면, 다시 설정 또는 장치 복구를 사용 하 여 다시 플래시 합니다. 이 문서는 연속적으로 권장 되는 단계를 안내 합니다.

## <a name="perform-a-device-reboot"></a>장치 재부팅을 수행 합니다.

HoloLens에 문제가 발생 했습니다. 또는 응답 하지 않는 경우 먼저 중 하나를 통해 재부팅을 다음 방법입니다.

### <a name="perform-a-safe-reboot-via-cortana"></a>Cortana 통해 안전 하 게 다시 부팅을 수행 합니다.

Cortana를 통해는 HoloLens 다시 부팅 하는 가장 안전한 방법은 됩니다. 이것이 일반적으로 첫 번째 단계는 훌륭한 HoloLens 문제가 발생 하는 경우:
1. 장치에 배치
2. 전원이 켜진 사용자가 로그인 하 고 장치 잠금을 해제 하려면 암호를 기다리지 않고 있는지 확인 합니다.
3. 예를 들어 "Hey Cortana, 다시 부팅" 또는 "Hey Cortana, 다시 시작 합니다."
4. 그녀는 승인 하는 경우 자신이 요청 확인 합니다. 자신의 질문 완료 된 그녀는 그녀가를 수신 대기 후 재생할 소리에 대해 잠시 기다린 후 "예"를 말한 다음
5. 장치는 이제 재부팅/다시 시작 합니다.

### <a name="perform-a-safe-reboot-via-windows-device-portal"></a>Windows Device Portal 통해 안전 하 게 다시 부팅을 수행 합니다.

위의 작동 하지 않을 수 하려는 경우를 통해 장치를 다시 부팅 [Windows Device Portal](using-the-windows-device-portal.md)합니다. 오른쪽 위 모서리에 장치가 다시 시작/종료 하는 옵션이 합니다.

### <a name="perform-a-safe-reboot-via-the-power-button"></a>전원 단추를 통해 안전 하 게 다시 부팅을 수행 합니다.

장치를 재부팅할 수 없는 경우에 전원 단추를 통해 다시 부팅이 실행을 시도할 수 있습니다.
1. 5 초 동안 전원 단추를 누르고
   1. 모든 5 명의 led가 켜 집니다, 느린 끈 다음 오른쪽에서 왼쪽으로 표시 됩니다 1 초 후
   2. 5 초 후, 모든 led가 꺼집니다, 종료 명령이 성공적으로 발급 된 나타내는
   3. Note 바로 뒤에 있는 Led를 사용 하지 않도록 설정한 모든 단추를 누르면 중지 해야
2. 완전히 성공 하려면 종료에 대 일 분을 기다립니다. 종료를 표시 되는 경우에 여전히 진행 중일에서 수 있습니다
3. 1 초 동안 전원 단추를 누르고에서 다시 장치 전원 켜기

### <a name="perform-an-unsafe-forced-reboot"></a>안전 하지 않은 강제 다시 부팅을 수행 합니다.

성공적으로 장치를 다시 부팅 하는 일을 할 경우 위에서 설명한 방법 중 다시 부팅 해야를 할 수 있습니다. 이 메서드는 해당 하는 HoloLens에서 배터리를 끌어오는 이며 이와 같이 장치의 손상 된 상태로 유지 될 수 있습니다는 위험한 작업을 참고 합니다. 

>[!WARNING]
>잠재적으로 위험한 메서드 이며 위에서 설명한 방법 해결 이벤트에 사용 해야 합니다.

1. 10 초 이상에 대 한 전원 단추를 누르고
   * 10 초 이상에 대 한 단추를
   * 모든 LED 활동을 무시 해도 안전
2. 단추를 놓은 2 ~ 3 초 동안 대기
3. 1 초 동안 전원 단추를 누르고에서 다시 장치 전원 켜기

## <a name="reset-the-device-to-a-factory-clean-state"></a>장치 공장 깨끗 한 상태로 다시 설정

HoloLens에 여전히 문제가 발생 한 다시 부팅 한 후에 정리 공장 기본 상태로 재설정을 시도할 수 있습니다. 장치를 재설정 하면 모든 개인 데이터, 앱 및 설정이 삭제 됩니다. 최신 버전의 Windows Holographic를 설치할지 다시 설정 및 초기화 단계를 다시 실행 해야 합니다 (보정, WiFi에 연결, 사용자 계정 만들기, 앱 등을 다운로드 합니다...).
1. 시작 합니다 **설정을** 앱-> **업데이트** -> **다시 설정**
2. 선택 된 **재설정 한 장치** 확인 대화 상자를 읽고 옵션
3. 장치 다시 부팅 되며 진행률 표시줄을 사용 하 여 gears 회전의 집합을 표시, 동의 장치를 초기화 하는 경우
4. 이 프로세스를 완료 하려면 약 30 분 정도 대기 합니다.
5. 다시 설정 완료 되 고 첫 실행 경험 중에 장치가 다시 부팅 됨

## <a name="perform-a-full-device-recovery"></a>전체 장치 복구를 수행 합니다.

위의 옵션을 수행한 후 장치는 경우 **여전히** 고정, 업데이트 또는 소프트웨어, 응답 하지 않거나 발생 한 문제와 Windows Device Recovery Tool 사용 하 여 복구할 수 있습니다. 장치를 복구 하는 것 앱, 게임, 사진, 사용자 계정 등을 포함 하 여 장치의 모든 사용자 콘텐츠를 제거 한다는 내용의 점에서 다시 설정 하는 것과 비슷합니다. 가능 하면 유지 하려는 모든 정보를 백업 합니다.

완벽 하 게 복구 하려면에 HoloLens:
1. PC에서 모든 휴대폰 및 Windows 장치를 연결 끊기
2. 설치 하 고 시작 합니다 [Windows Device Recovery Tool](https://support.microsoft.com/help/12379/windows-10-mobile-device-recovery-tool-faq) (WDRT) PC에서
3. HoloLens에 제공 하는 마이크로 USB 케이블을 사용 하 여 사용자 PC에 연결
   * 일부 USB 케이블 같은 만들어졌는지 note 합니다. 사용 중인 다른 케이블 성공적으로, 경우에이 흐름은 케이블 잘 작동 하지 않을 수 있습니다 새 상태를 노출 합니다. 에 HoloLens와 함께 제공 되 최상의 및 가장 거친 옵션
4. 장치가 자동으로 검색 하는 경우에 HoloLens 타일을 표시 됩니다. 클릭 하 고 프로세스를 완료 하려면 지침에 따라

>[!NOTE]
>WDRT 이전 버전의 Windows Holographic; 하기 위해 장치를 복구할 수 있습니다. 깜박임 후 업데이트를 설치 해야 합니다.

도구에 장치를 자동으로 검색할 수 없는 경우 다음과 같이 하세요.
1. PC와 다시 시도 하세요 (이 대부분의 문제를 수정 함)를 다시 부팅
2. 클릭 합니다 **내 장치가 없습니다 단추**, 선택 **Microsoft HoloLens**, 화면의 지시를 따릅니다 및
