---
title: 하드웨어 accessories
description: HoloLens 및 Windows Mixed Reality를 설정 하는 방법에 사용할 수 있는 보조 프로그램의 형식을 설명 합니다.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 방법, 보조 프로그램, bluetooth, bt, 컨트롤러, 게임 패드, clicker, xbox
ms.openlocfilehash: c25f849cbf05a78ba2fe7118dbe160d05e0f5e3f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604737"
---
# <a name="hardware-accessories"></a>하드웨어 accessories

Windows Mixed Reality 장치는 보조 프로그램을 지원합니다. Bluetooth를 사용할 수 있습니다 또는 쌍에 USB를 통해 연결 되는 PC는 몰입 형 헤드셋 accessories 지원 하지만 Bluetooth를 사용 하 여 HoloLens에 지원 되는 보조 연결 됩니다.

HoloLens accessories 사용을 위한 두 가지 일반적인 시나리오 무선에 대 한 대체 제스처와 가상 키보드 탭으로 됩니다. 이 위해 두 가지 가장 일반적인 accessories은는 **HoloLens Clicker** 하 고 **Bluetooth 키보드**합니다. Microsoft HoloLens 4.1 Bluetooth 라디오를 포함 하 고 지 원하는 [Bluetooth HID](https://en.wikipedia.org/wiki/List_of_Bluetooth_profiles#Human_Interface_Device_Profile_.28HID.29) 하 고 [Bluetooth GATT](https://en.wikipedia.org/wiki/List_of_Bluetooth_profiles#Generic_Attribute_Profile_.28GATT.29) 프로필입니다.

Windows Mixed Reality 몰입 형 헤드셋 외의 입력에 대 한 보조 프로그램 필요 [gaze](gaze.md) 하 고 [음성](voice-input.md)합니다. 지원 되는 보조 프로그램 포함 **키보드 및 마우스**를 **gamepad**, 및  **[컨트롤러 동작](motion-controllers.md)** 합니다.

## <a name="pairing-bluetooth-accessories"></a>Bluetooth accessories 페어링

Microsoft HoloLens 사용 하 여 Bluetooth 주변 장치를 연결 하는 것은 Windows 10을 사용 하 여 주변 장치 Bluetooth 페어링 비슷합니다 데스크톱 또는 모바일 장치:
1. 시작 메뉴에서 엽니다는 **설정을** 앱
2. 로 **장치**
3. 슬라이더 스위치를 사용 하는 경우 Bluetooth 라디오를 켜려면
4. Bluetooth 장치 연결 모드에 배치 합니다. 이 장치 마다 달라 집니다. 대부분의 Bluetooth 장치에서 하나 이상의 단추를 누르고 하면 됩니다.
5. Bluetooth 장치 목록에 표시 하려면 장치 이름이 될 때까지 기다립니다. 경우에, 장치를 선택 합니다. 그런 다음 선택 합니다 **쌍** 단추입니다. 있는 경우 있습니다 근처에 있는 많은 Bluetooth 장치 연결 하려는 장치를 확인 하려면 Bluetooth 장치 목록 아래쪽으로 스크롤하여 해야 합니다.
6. 사용 하 여 Bluetooth 주변 장치 쌍 기능을 입력 하는 경우 (예: Bluetooth 키보드의 경우)는 6 자리 또는 8 자리 pin을 표시할 수 있습니다. 주변 장치에 해당 pin을 입력 해야 하 고 enter 키를 눌러 Microsoft HoloLens 사용 하 여 전체 연결 합니다.

## <a name="motion-controllers"></a>컨트롤러 동작

Windows Mixed Reality [컨트롤러 동작](motion-controllers.md) 몰입 형 헤드셋 이지만 HoloLens 하지에서 지원 됩니다. 이러한 컨트롤러는 몰입 형 헤드셋을 공간에 벽에 하드웨어를 설치 하지 않아도 즉에 센서를 사용 하 여 필드의 보기의 이동 정확 하 고 응답성이 뛰어난 추적을 제공 합니다. 각 컨트롤러는 입력의 몇 가지 메서드를 갖추고 있습니다.

![Windows Mixed Reality 동작 컨트롤러](images/winmr-ck-1080x1080-350px.jpg)

## <a name="hololens-clicker"></a>HoloLens Clicker

HoloLens Clicker HoloLens 위해 특별히 구축 된 첫 번째 주변 장치 이며 HoloLens Development Edition에 포함 합니다. HoloLens Clicker 사용자를를 클릭 하 고 어 탭 제스처에 대 한 대체 최소 손 동작을 사용 하 여 스크롤할 수 있습니다. 모든 대체 기능이 아닙니다 [제스처](gestures.md)합니다. 예를 들어 [블 룸](gestures.md#bloom) 하 고 [크기를 조정 하거나 이동](gestures.md#composite-gestures) 제스처 직접 동작을 사용 합니다. HoloLens clicker는 간단한 단추를 사용 하 여는 방향 센서 장치입니다. Bluetooth Low Energy (BTLE)를 사용 하 여 HoloLens 연결 합니다.

![HoloLens Clicker](images/hololens-clicker-500px.jpg)

선택 하는 [홀로그램](hologram.md)을 응시 및 클릭 합니다. 이 작업에 대 한는 clicker의 방향이 중요 하지 않습니다. 스크롤 또는 이동를 클릭 한 보관,으로 회전 합니다 Clicker 위쪽/아래쪽 또는 왼쪽/오른쪽입니다. 스크롤 하는 동안 15 ° 손목 회전 + /-정도로 빠른 속도 도달 하 게 됩니다. 더 많은 움직이지 않습니다 모든 빨라집니다.

Clicker 내에서 두 개의 Led가 있습니다.
* 흰색 LED (깜박이) 장치 쌍은 있는지 여부를 나타냅니다 (고정) 청구 또는
* 장치에 배터리 (깜박이) 또는 (고정)에 오류가 발생할 수는 LED 나타냅니다 주황색

전체 충전 (즉, 벽 충전기에 2 ~ 3 시간)에 2 주 이상 정기적으로 사용 될 수 있습니다. 배터리 부족, 주황색 단추를 누르거나 절전 모드 해제 절전 모드의 경우 10 시간 동안 5 초 LED가 깜박입니다. 경우에는 5 초 기간을 통해 보다 신속 하 게 LED가 깜박입니다 주황색 프로그램 Clicker 매우 배터리 모드입니다.

## <a name="bluetooth-keyboards"></a>Bluetooth 키보드

영어 Qwerty Bluetooth 키보드 쌍으로 연결할 수 있습니다 및 holographic 키보드를 사용 하 여 원하는 위치를 사용 합니다. 차이를 사용 하면 품질 키보드를 가져오기, 따라서 것이 좋습니다 합니다 [Microsoft 유니버설 폴딩 키보드](https://www.microsoft.com/accessories/products/keyboards/universal-foldable-keyboard/gu5-00001) 또는 [Microsoft 디자이너 Bluetooth Desktop](https://www.microsoft.com/accessories/products/keyboards/designer-bluetooth-desktop/7n9-00001)합니다.

## <a name="bluetooth-gamepads"></a>Bluetooth 게임 패드

특히 gamepad 지원을 사용 하도록 설정 하는 앱 및 게임을 사용 하 여 컨트롤러를 사용할 수 있습니다. HoloLens 사용자 인터페이스를 제어 하려면 게임 패드를 사용할 수 없습니다.

HoloLens 및 몰입 형 헤드셋와 함께 사용할 수 있도록 하는 Xbox 1 S 기능 Bluetooth 연결에 대 한 accessories로 판매 또는 Xbox 하나 S를 사용 하 여 제공 되는 Xbox 무선 컨트롤러입니다. Xbox 무선 컨트롤러 [업데이트 해야](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) HoloLens를 사용 하 여 사용할 수 있습니다.

Windows Mixed Reality 장치 Bluetooth 게임 패드의 다른 브랜드 작동할 수 있지만 지원 응용 프로그램에 따라 달라 집니다.

## <a name="other-bluetooth-accessories"></a>다른 Bluetooth accessories

주변 장치에서 Bluetooth HID 또는 GATT 프로필 지원, HoloLens 페어링할 수 됩니다. 다른 Bluetooth HID GATT 장치와 키보드, 마우스 및 HoloLens Clicker 외에도 완전 하 게 작동 하는 도우미 응용 프로그램 Microsoft HoloLens 필요할 수 있습니다.

지원 되지 않는 주변 장치는 다음과 같습니다.
* 주변 장치 Bluetooth 오디오 프로필에 지원 되지 않습니다.
* 발표자 헤드셋 등 Bluetooth 오디오 장치 설정 앱에서 사용 가능한 나타날 수 있지만 Microsoft HoloLens 오디오 끝점으로 사용할 수 없습니다.
* Bluetooth 가능 휴대폰 및 Pc를 쌍으로 연결 된 파일 전송에 사용 되는 지원 되지 않습니다.

## <a name="unpairing-a-bluetooth-peripheral"></a>Bluetooth 주변 장치를 연결 해제
1. 시작 메뉴에서 엽니다는 **설정을** 앱
2. 로 **장치**
3. 해제 되어 있으면 Bluetooth 라디오를 켜려면
4. 사용 가능한 Bluetooth 장치 목록에서 장치 찾기
5. 선택한 후 목록에서 장치를 선택 합니다 **제거** 단추

## <a name="disabling-bluetooth-on-microsoft-hololens"></a>Microsoft HoloLens Bluetooth를 사용 하지 않도록 설정

RF 구성 요소는 Bluetooth 라디오 해제 되 고 Microsoft HoloLens 모든 Bluetooth 기능을 사용 하지 않도록 설정 됩니다.
1. 시작 메뉴에서 엽니다는 **설정을** 앱
2. 로 **장치**
3. Bluetooth에 대 한 슬라이더 스위치를 OFF 위치로 이동
