---
title: Windows Mixed Reality 시뮬레이터를 사용 하 여
description: Windows Mixed Reality 시뮬레이터를 사용 하면 Windows Mixed Reality 몰입 형 헤드셋 없이 PC에서 혼합된 현실 앱을 테스트할 수 있습니다.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Windows는 시뮬레이터를 실제로 테스트 혼합
ms.openlocfilehash: 782cab85f163edd2afc4251210b7596c73dcc8b8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603638"
---
# <a name="using-the-windows-mixed-reality-simulator"></a>Windows Mixed Reality 시뮬레이터를 사용 하 여

Windows Mixed Reality 시뮬레이터를 사용 하면 Windows Mixed Reality 몰입 형 헤드셋 없이 PC에서 혼합된 현실 앱을 테스트할 수 있습니다. Windows 10 크리에이터 스 업데이트부터 사용할 수는 것입니다. 시뮬레이터는 비슷합니다는 [HoloLens 에뮬레이터](using-the-hololens-emulator.md)되지만 시뮬레이터 가상 컴퓨터를 사용 하지 않습니다. 시뮬레이터에서 실행 되는 앱을 몰입 형 헤드셋을 사용한 경우와 마찬가지로 Windows 10 데스크톱 사용자 세션에서 실행 합니다. 일반적으로 몰입 형 헤드셋에 센서에서 읽을 수 있는 사람과 환경 입력 키보드, 마우스, 또는 Xbox 컨트롤러를 사용 하 여 시뮬레이션 대신 됩니다. 앱은 시뮬레이터에서 실행을 수정할 필요가 없습니다 및 알지 들는 몰입 형 헤드셋에서 실행 되지 않습니다.

## <a name="enabling-the-windows-mixed-reality-simulator"></a>Windows Mixed Reality 시뮬레이터를 사용 하도록 설정

1. **개발자 모드를 사용 하도록 설정** 설정에서-> 업데이트 및 개발자를 위한 보안->
2. 시작 합니다 **혼합 현실 포털** 바탕 화면에서
3. 설치 환경을 통해 이동 해야 처음 포털 시작 인 경우
   1. 클릭 **시작**
   2. 클릭 **동의 함** 계약에 동의
   3. 클릭 **(개발자 용) 시뮬레이션에 대 한 설정** 물리적 장치 없이 설치 프로그램을 통해 계속 하려면
   4. 클릭 **설정** 선택을 확인 하려면
4. 클릭 합니다 **개발자를 위한** 혼합 현실 포털의 왼쪽에 단추
5. 시뮬레이션 토글 스위치를 전환 하 고 **에서**
   * 이렇게 하려면 관리자 권한 및 사용자 계정 컨트롤 대화 상자가 나타나면 받아들여야 합니다.

이제 시뮬레이션을 사용 하 여 실행 해야!

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a>혼합 현실 시뮬레이터에 앱 배포

시뮬레이터를 가상 컴퓨터 없이 로컬 PC에서 실행 되므로 유니버설 Windows 앱을 간단히 배포할 수 있습니다 합니다 **로컬 컴퓨터** 디버깅 하는 경우.

## <a name="basic-simulator-input"></a>기본 시뮬레이터 입력

시뮬레이터를 제어 하는 것은 매우 많은 일반적인 3D 비디오 게임 비슷합니다는 [HoloLens 에뮬레이터](using-the-hololens-emulator.md)합니다. 키보드, 마우스 또는 Xbox 컨트롤러를 사용 하 여 사용할 수는 입력된 옵션이 있습니다.

착용 하는 몰입 형 헤드셋 시뮬레이션된 된 사용자의 동작을 지시 하 여 시뮬레이터를 제어 합니다. 작업은 시뮬레이션 된 사용자를 이동 하 고 응답 하는 몰입 형 헤드셋에서 일관 되 게는 앱과 상호 작용을 발생 합니다.
* **앞으로, 다시을 유지 하 고 마우스 오른쪽 단추로** -W, 사용 하 여 키보드 또는 Xbox 컨트롤러에 왼쪽된 메모리에서 A, S, D 키입니다.
* **조회할 아래, 왼쪽 및 오른쪽** -클릭 하 고 마우스를 끌어 키보드 또는 Xbox 컨트롤러에 올바른 메모리에서 화살표 키를 사용 합니다.
* **컨트롤러에서 작업 단추 누름** -마우스, 키보드에서 Enter 키를 눌러 또는 Xbox 컨트롤러에는 단추를 사용 합니다.
* **홈 컨트롤러 단추 누름** -키보드에서 Windows 키나 F2 키를 눌러 또는 Xbox 컨트롤러 B 단추를 누릅니다.
* **스크롤 하는 것에 대 한 컨트롤러 이동을** -Alt 키를 누른 채로 마우스 오른쪽 단추 및 위쪽 / 아래쪽에 마우스를 끌어 또는 Xbox 컨트롤러를에서 오른쪽 트리거와 단추 누른 오른쪽 스틱을 위아래로 이동 합니다.

## <a name="tracked-controllers"></a>추적된 컨트롤러

혼합 현실 시뮬레이터는 최대 2 명의 핸드헬드 추적된 동작 컨트롤러를 시뮬레이션할 수 있습니다. 혼합 현실 포털의 설정/해제 스위치를 사용 하 여 사용 하도록 설정 합니다. 시뮬레이션 된 각 컨트롤러에 있습니다.
* 공간 내의 위치
* 홈 버튼
* 메뉴 버튼
* 그립 단추
* 터치 패드

## <a name="see-also"></a>참조
* [Using the HoloLens emulator(HoloLens 에뮬레이터 사용)](using-the-hololens-emulator.md)
* [혼합된 현실 시뮬레이터 입력 고급](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [Unity에서 공간 매핑](spatial-mapping-in-unity.md)
* [DirectX의 공간 매핑](spatial-mapping-in-directx.md)
