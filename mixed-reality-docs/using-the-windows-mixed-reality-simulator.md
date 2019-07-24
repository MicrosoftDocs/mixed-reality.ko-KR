---
title: Windows Mixed Reality 시뮬레이터 사용
description: Windows Mixed reality 시뮬레이터를 사용 하면 Windows Mixed Reality 몰입 형 헤드셋 없이 PC에서 혼합 현실 앱을 테스트할 수 있습니다.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
keywords: Windows Mixed Reality, 시뮬레이터, 테스트
ms.openlocfilehash: a7cbd5b5ca1c0ed0e4f81715d337d5eec68117f0
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64580698"
---
# <a name="using-the-windows-mixed-reality-simulator"></a>Windows Mixed Reality 시뮬레이터 사용

Windows Mixed reality 시뮬레이터를 사용 하면 Windows Mixed Reality 몰입 형 헤드셋 없이 PC에서 혼합 현실 앱을 테스트할 수 있습니다. Windows 10 크리에이터 스 업데이트부터 사용할 수 있습니다. 시뮬레이터는 가상 컴퓨터를 사용 하지 않지만 [HoloLens 에뮬레이터](using-the-hololens-emulator.md)와 비슷합니다. 시뮬레이터에서 실행 되는 앱은 몰입 형 헤드셋을 사용 하는 경우와 마찬가지로 Windows 10 desktop 사용자 세션에서 실행 됩니다. 일반적으로 몰입 형 헤드셋에서 센서에 의해 읽혀집니다 사용자 및 환경 입력이 키보드, 마우스 또는 Xbox 컨트롤러를 사용 하 여 시뮬레이션 됩니다. 앱은 시뮬레이터에서 실행 되도록 수정할 필요가 없으며 몰입 형 헤드셋에서 실행 되지 않는 것을 알 수 없습니다.

## <a name="enabling-the-windows-mixed-reality-simulator"></a>Windows Mixed Reality 시뮬레이터 사용

1. 개발자 모드를 설정에서 **사용 하도록** 설정-> 업데이트 및 보안-개발자를 위한 >
2. 바탕 화면에서 **혼합 현실 포털** 시작
3. 포털을 처음 시작 하는 경우 설정 환경을 진행 해야 합니다.
   1. **시작** 을 클릭 합니다.
   2. 동의 함 **을 클릭 하** 여 동의 합니다.
   3. **시뮬레이션에 대 한 설정 (개발자의 경우)** 을 클릭 하 여 물리적 장치 없이 설치를 진행 합니다.
   4. **설정** 을 클릭 하 여 선택을 확인 합니다.
4. Mixed Reality 포털의 왼쪽에 있는 **개발자 용** 단추를 클릭 합니다.
5. 시뮬레이션 전환 전환 **켜기로 전환**
   * 시뮬레이션을 사용 하도록 설정 하면 기본적으로 왼쪽 시뮬레이션 된 6-DOF controller가 설치 되 고 활성화 됩니다.  Windows 10에서 2019 업데이트를 설치 하기 전에 시뮬레이션 된 6 DOF 컨트롤러를 설치 하려면 관리자 권한이 필요 합니다.  사용자 계정 컨트롤 대화 상자가 나타나면 동의 해야 합니다.

이제 시뮬레이션을 사용 하 여 실행 해야 합니다.

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a>혼합 현실 시뮬레이터에 앱 배포

시뮬레이터는 가상 머신을 사용 하지 않고 로컬 PC에서 실행 되므로 디버그할 때 유니버설 Windows 앱을 **로컬 컴퓨터** 에 배포 하기만 하면 됩니다.

## <a name="basic-simulator-input"></a>기본 시뮬레이터 입력

시뮬레이터 제어는 일반적인 3D 비디오 게임과 [HoloLens 에뮬레이터](using-the-hololens-emulator.md)와 매우 비슷합니다. 키보드, 마우스 또는 Xbox 컨트롤러를 사용하여 사용할 수 있는 입력 옵션이 있습니다.

몰입 형 헤드셋을 입고 하는 시뮬레이션 된 사용자의 작업을 전달 하 여 시뮬레이터를 제어 합니다. 작업은 시뮬레이트된 사용자를 이동 하 고 몰입 형 헤드셋에서와 같이 응답 하는 앱과 상호 작용 합니다.
* **앞으로, 뒤로, 왼쪽 및 오른쪽으로 걷기** - 키보드의 W, A, S 및 D 키 또는 Xbox 컨트롤러의 왼쪽 스틱을 사용합니다.
* **위, 아래, 왼쪽 및 오른쪽 보기** - 마우스를 클릭하여 끌거나, 키보드의 화살표 키 또는 Xbox 컨트롤러의 오른쪽 스틱을 사용합니다.
* **작업 단추 컨트롤러에서 키를 누릅니다** . 마우스 오른쪽 단추로 마우스를 클릭 하거나 키보드에서 enter 키를 누르거나 Xbox 컨트롤러에서 A 단추를 사용 합니다.
* **홈 단추 컨트롤러에서 키를 누릅니다** . 키보드에서 Windows 키나 F2 키를 누르거나 Xbox 컨트롤러에서 B 단추를 누릅니다.
* **스크롤을 위한 컨트롤러 이동** -Alt 키를 누른 상태에서 마우스 오른쪽 단추를 누른 상태에서 마우스를 위아래로 끌거나 Xbox 컨트롤러에서 오른쪽 트리거와 단추를 누르고 오른쪽 스틱을 위아래로 이동 합니다.

## <a name="tracked-controllers"></a>추적 된 컨트롤러

혼합 현실 시뮬레이터는 최대 2 개의 직접 보관 된 동작 컨트롤러를 시뮬레이션할 수 있습니다. 혼합 현실 포털에서 토글 스위치를 사용 하 여 사용 하도록 설정 합니다. 시뮬레이트된 각 컨트롤러에는 다음이 포함 됩니다.
* 공간에서의 위치 및 방향
* 홈 버튼
* 메뉴 버튼
* 그립 단추
* 터치 패드
* 사용해
* 배터리 수준

## <a name="see-also"></a>참조
* [Using the HoloLens emulator(HoloLens 에뮬레이터 사용)](using-the-hololens-emulator.md)
* [고급 혼합 현실 시뮬레이터 입력](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [Unity의 공간 매핑](spatial-mapping-in-unity.md)
* [DirectX의 공간 매핑](spatial-mapping-in-directx.md)
