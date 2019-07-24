---
title: 하드웨어 액세서리
description: HoloLens 및 Windows Mixed Reality에서 사용할 수 있는 액세서리 유형 및 설정 하는 방법을 설명 합니다.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 방법, 액세서리, bluetooth, bt, 컨트롤러, 게임 패드, clicker, xbox
ms.openlocfilehash: c25f849cbf05a78ba2fe7118dbe160d05e0f5e3f
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63526618"
---
# <a name="hardware-accessories"></a>하드웨어 액세서리

Windows Mixed Reality 장치는 액세서리를 지원 합니다. Bluetooth 또는 USB를 사용 하 여 지원 되는 액세서리를 장치를 사용 하는 HoloLens에 연결 하는 동시에 bluetooth 또는 USB를 사용 하 여 지원 되는 액세서리를 연결 된 PC를 통해 몰입 형 헤드셋에 페어링

HoloLens에서 액세서리를 사용 하는 두 가지 일반적인 시나리오는 공기 탭 제스처와 가상 키보드를 대체 하는 것입니다. 이를 위해 가장 일반적인 두 가지 액세서리는 **HoloLens Clicker** 및 **Bluetooth 키보드**입니다. Microsoft HoloLens에는 Bluetooth 4.1 라디오가 포함 되어 있으며 [BLUETOOTH HID](https://en.wikipedia.org/wiki/List_of_Bluetooth_profiles#Human_Interface_Device_Profile_.28HID.29) 및 [bluetooth GATT](https://en.wikipedia.org/wiki/List_of_Bluetooth_profiles#Generic_Attribute_Profile_.28GATT.29) 프로필을 지원 합니다.

Windows Mixed Reality 몰입 형 헤드셋은 [응시](gaze.md) 및 [음성](voice-input.md)이외의 입력을 위한 액세서리를 요구 합니다. 지원 되는 액세서리는 **키보드 및 마우스**, **게임 패드**및 **[동작 컨트롤러](motion-controllers.md)** 를 포함 합니다.

## <a name="pairing-bluetooth-accessories"></a>Bluetooth 액세서리 페어링

Microsoft HoloLens와 Bluetooth 주변 장치를 페어링 하는 것은 Windows 10 데스크톱 또는 모바일 장치와 Bluetooth 주변 장치를 페어링 하는 것과 비슷합니다.
1. 시작 메뉴에서 **설정** 앱을 엽니다.
2. **장치로** 이동
3. 슬라이더 스위치를 사용 하 여 Bluetooth 라디오가 꺼진 경우 켭니다.
4. Bluetooth 장치를 페어링 모드로 전환 합니다. 장치 마다 다릅니다. 대부분의 Bluetooth 장치에서 하나 이상의 단추를 누르고 있으므로이 작업을 수행할 수 있습니다.
5. 장치 이름이 Bluetooth 장치 목록에 표시 될 때까지 기다립니다. 장치를 선택 하는 경우 장치를 선택 하 고 **쌍** 단추를 선택 합니다. 근처에 많은 Bluetooth 장치가 있는 경우 연결 하려는 장치를 보려면 Bluetooth 장치 목록의 맨 아래로 스크롤해야 할 수도 있습니다.
6. Bluetooth 주변 장치를 입력 기능과 페어링 하는 경우 (예: Bluetooth 키보드), 6 자리 또는 8 자리 pin이 표시 될 수 있습니다. 주변 장치에 pin을 입력 하 고 enter 키를 눌러 Microsoft HoloLens와 페어링 합니다.

## <a name="motion-controllers"></a>동작 컨트롤러

Windows Mixed Reality [동작 컨트롤러](motion-controllers.md) 는 몰입 형 헤드셋에서 지원 되지만 HoloLens는 지원 되지 않습니다. 이러한 컨트롤러는 몰입 형 헤드셋의 센서를 사용 하 여 뷰 필드의 이동에 대 한 정확 하 고 응답성이 뛰어난 추적을 제공 합니다. 즉, 공간의 벽에 하드웨어를 설치할 필요가 없습니다. 각 컨트롤러에는 몇 가지 입력 방법이 있습니다.

![Windows Mixed Reality 동작 컨트롤러](images/winmr-ck-1080x1080-350px.jpg)

## <a name="hololens-clicker"></a>HoloLens Clicker

HoloLens Clicker는 hololens 용으로 특별히 구축 된 첫 번째 주변 장치 이며 HoloLens Development Edition에 포함 되어 있습니다. HoloLens Clicker를 사용 하면 사용자가 최소한의 손을 클릭 하 여 클릭 하 고 이동 하 여 이동 제스처를 바꿀 수 있습니다. 모든 [제스처](gestures.md)를 대체 하지는 않습니다. 예를 들어 [블 룸](gestures.md#bloom) 및 [크기 조정 또는 이동](gestures.md#composite-gestures) 제스처는 직접 동작을 사용 합니다. HoloLens clicker는 간단한 단추가 있는 방향 센서 장치입니다. Bluetooth 저 에너지 (BTLE)를 사용 하 여 HoloLens에 연결 합니다.

![HoloLens Clicker](images/hololens-clicker-500px.jpg)

[홀로그램](hologram.md)을 선택 하려면 응시 한 다음를 클릭 합니다. 이 작업에는 clicker의 방향이 중요 하지 않습니다. 스크롤하거나 이동 하려면 클릭 한 채 Clicker 위쪽/아래쪽 또는 왼쪽/오른쪽으로 회전 합니다. 스크롤 하는 동안 손목 회전의 +/-15 ° 만큼의 가장 빠른 속도로 도달 합니다. 더 빨리 이동 하면 더 이상 스크롤되지 않습니다.

Clicker 내에는 두 개의 Led가 있습니다.
* 흰색 LED는 장치가 페어링 (깜박임) 인지 충전 (solid) 인지를 나타냅니다.
* 주황색 LED는 장치의 배터리가 부족 하거나 (깜박임) 오류가 발생 했음을 나타냅니다 (solid).

전체 요금 (즉, 벽면 충전기에서 2-3 시간)에 대 한 2 주 이상의 정기 사용을 예측할 수 있습니다. 배터리가 부족 하면 단추를 누르거나 절전 모드에서 해제 하는 경우 주황색 LED가 5 초 동안 10 번 깜박입니다. Clicker가 매우 낮은 배터리 모드일 경우 5 초 동안 주황색 LED가 더 빨리 깜박입니다.

## <a name="bluetooth-keyboards"></a>Bluetooth 키보드

영어 Qwerty 블루투스 키보드는 holographic 키보드를 사용할 수 있는 모든 곳에서 페어링 하 고 사용할 수 있습니다. 고품질 키보드를 사용 하면 차이점이 있으므로 [Microsoft Universal 폴딩 가능 키보드](https://www.microsoft.com/accessories/products/keyboards/universal-foldable-keyboard/gu5-00001) 또는 [Microsoft Designer Bluetooth Desktop](https://www.microsoft.com/accessories/products/keyboards/designer-bluetooth-desktop/7n9-00001)을 사용 하는 것이 좋습니다.

## <a name="bluetooth-gamepads"></a>Bluetooth gamepads

특히 게임 패드 지원을 사용 하도록 설정 하는 앱 및 게임과 함께 컨트롤러를 사용할 수 있습니다. Gamepads는 HoloLens 사용자 인터페이스를 제어 하는 데 사용할 수 없습니다.

Xbox a S와 함께 제공 되는 xbox 무선 컨트롤러 또는 Xbox One의 액세서리로 판매 되는 xbox 무선 컨트롤러를 사용 하 여 HoloLens 및 몰입 형 헤드셋과 함께 사용할 수 있습니다. HoloLens를 사용 하려면 먼저 Xbox 무선 컨트롤러를 [업데이트 해야](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) 합니다.

Bluetooth gamepads의 다른 브랜드는 Windows Mixed Reality 장치에서 작동할 수 있지만 지원은 응용 프로그램에 따라 달라 집니다.

## <a name="other-bluetooth-accessories"></a>기타 Bluetooth 액세서리

주변 장치는 Bluetooth HID 또는 GATT 프로필을 지원 하기만 하면 HoloLens와 쌍으로 연결할 수 있습니다. 키보드, 마우스 및 HoloLens Clicker 외에 다른 Bluetooth HID 및 GATT 장치에는 완전 한 기능을 제공 하기 위해 Microsoft HoloLens의 도우미 응용 프로그램이 필요할 수 있습니다.

지원 되지 않는 주변 장치는 다음과 같습니다.
* Bluetooth 오디오 프로필의 주변 장치는 지원 되지 않습니다.
* 스피커 및 헤드셋과 같은 Bluetooth 오디오 장치는 설정 앱에서 사용 가능으로 표시 될 수 있지만, Microsoft HoloLens와 오디오 끝점으로 사용할 수는 없습니다.
* Bluetooth 사용 전화 및 Pc는 쌍으로 연결 되 고 파일 전송에 사용할 수 없습니다.

## <a name="unpairing-a-bluetooth-peripheral"></a>Bluetooth 주변 장치 페어링 해제
1. 시작 메뉴에서 **설정** 앱을 엽니다.
2. **장치로** 이동
3. Bluetooth 라디오가 꺼진 경우 켭니다.
4. 사용 가능한 Bluetooth 장치 목록에서 장치를 찾습니다.
5. 목록에서 장치를 선택 하 고 **제거** 단추를 선택 합니다.

## <a name="disabling-bluetooth-on-microsoft-hololens"></a>Microsoft HoloLens에서 Bluetooth를 사용 하지 않도록 설정

그러면 Bluetooth 라디오의 RF 구성 요소가 꺼지고 Microsoft HoloLens의 모든 Bluetooth 기능이 사용 하지 않도록 설정 됩니다.
1. 시작 메뉴에서 **설정** 앱을 엽니다.
2. **장치로** 이동
3. Bluetooth 용 슬라이더 스위치를 OFF 위치로 이동 합니다.
