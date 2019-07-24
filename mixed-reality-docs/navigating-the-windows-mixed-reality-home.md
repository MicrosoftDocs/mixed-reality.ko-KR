---
title: Windows Mixed Reality 홈 탐색
description: HoloLens 및 Windows Mixed Reality 헤드셋은 사용자 환경에서 앱 및 3D 모델을 시작, 배치 및 조작 하기 위한 패러다임 (실제 또는 디지털)을 공유 합니다. 두 장치 유형에 서 Windows Mixed Reality 홈을 탐색 하는 방법을 알아봅니다.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 셸, os, 플랫폼, 절벽 집, 집, 홈, 환경, 시작, 시작 메뉴, 홈 메뉴, pin, 앱, 앱 시작, 앱 배치, 텔레포트, 이동, 탐색
ms.openlocfilehash: 1ca6dd66506a64ad2e1c21870fee2725ddf20bd8
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63525189"
---
# <a name="navigating-the-windows-mixed-reality-home"></a>Windows Mixed Reality 홈 탐색

Windows PC 환경이 바탕 화면에서 시작 하는 것 처럼 Windows Mixed Reality는 홈으로 시작 합니다. Windows Mixed Reality 홈은 3D 위치를 이해 하 고 탐색할 수 있는 innate 기능을 활용 합니다. HoloLens를 사용 하는 경우 홈은 실제 공간입니다. 모던 헤드셋을 사용 하 여 홈은 가상 장소입니다.

또한 홈에서 시작 메뉴를 사용 하 여 앱과 콘텐츠를 열고 저장할 수 있습니다. 여러 앱을 동시에 사용 하 여 혼합 현실 콘텐츠 및 멀티태스킹을로 홈을 채울 수 있습니다. 장치를 다시 시작 하는 경우에도 홈에서 발생 하는 항목은 그대로 유지 됩니다.

## <a name="start-menu"></a>시작 메뉴

![Microsoft HoloLens의 시작 메뉴](images/start-500px.png)

시작 메뉴는 다음으로 구성 됩니다.
* 시스템 정보 (네트워크 상태, 배터리 비율, 현재 시간 및 볼륨)
* Cortana (모던 헤드셋, 시작 타일, HoloLens의 맨 위에 있는 경우)
* 고정 된 앱
* 모든 앱 단추 (더하기 기호)
* [혼합 현실 캡처](mixed-reality-capture.md) 에 대 한 사진 및 비디오 단추

더하기 또는 빼기 단추를 선택 하 여 고정 된 앱과 모든 앱 보기 사이를 전환 합니다. HoloLens에서 시작 메뉴를 열려면 블 룸 제스처를 사용 합니다. 몰입 형 헤드셋에서 컨트롤러의 Windows 단추를 누릅니다.

## <a name="launching-apps"></a>앱 시작

앱을 시작 하려면 시작 시 앱을 선택 합니다. 시작 메뉴가 사라지고 앱이 배치 모드에서 2D 창이 나 [3d 모델로](implementing-3d-app-launchers.md)열립니다.

앱을 실행 하려면 홈에 저장 해야 합니다.
1. 사용자의 [응시](gaze.md) 또는 컨트롤러를 사용 하 여 앱을 원하는 위치에 배치 합니다. 크기 및 위치를 자동으로 조정 하 여 배치 하는 공간에 맞게 조정 됩니다.
2. 항공기 탭 (HoloLens) 또는 선택 단추 (몰입 형 헤드셋)를 사용 하 여 앱을 넣습니다. 시작 메뉴를 취소 하 고 다시 가져오려면 블 룸 제스처 또는 Windows 단추를 사용 합니다.

데스크톱, 모바일 또는 Xbox 용으로 만든 [2d 앱](building-2d-apps.md)은 [HolographicSpace API](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx)를 사용 하 여 혼합 된 현실 앱으로 실행 되도록 수정할 수 있습니다. 몰입 형 앱은 사용자가 집에서 나 몰입 형 환경으로 이동 합니다. 사용자는 HoloLens (블 룸 제스처)를 사용 하거나 자신의 컨트롤러 (몰입 형 헤드셋)에서 Windows 단추를 눌러 홈을 반환할 수 있습니다.

앱 간 API 또는 Cortana를 통해 앱을 시작할 수도 있습니다.

![Windows Mixed Reality 홈의 앱](images/mixed-reality-home-500px.png)

## <a name="moving-and-adjusting-apps"></a>앱 이동 및 조정

앱 바에서 **조정** 을 선택 하 여 혼합 현실 콘텐츠를 이동, 크기 조정 및 회전 하는 컨트롤을 표시 합니다. 완료 되 면 **완료**를 선택 합니다.

![저장소 슬레이트는 조정 모드 (파란색 프레임)입니다. 참고 앱 바 (위쪽)가 ' 완료 ' 및 ' 제거 ' 단추를 포함 하도록 변경 되었습니다.](images/adjust-500px.png)

앱 바에 다른 앱이 추가 옵션이 있을 수 있습니다. 예를 들어 Microsoft Edge는 *스크롤*, *끌기*및 *확대/축소* 를 선택 합니다. 

![HoloLens에서 실행 되는 2D 앱에 대 한 앱 바](images/holobar-500px.png)

**뒤로** 단추는 앱에서 이전에 표시 된 화면으로 다시 이동 합니다. 앱에 표시 된 환경의 시작에 도달 하면 중지 되며 다른 앱으로 이동 하지 않습니다.

## <a name="getting-around-your-home"></a>홈 살펴보기

**HoloLens**를 사용 하면 실제 공간으로 이동 하 여 집 사이를 이동 합니다.

**모던 헤드셋**을 사용 하 여 가상 세계의 비슷한 영역 내에서 이동할 수 있도록 playspace를 비슷하게 시작 하 고 살펴볼 수 있습니다. 더 긴 거리를 이동 하려면 컨트롤러에서 엄지 스틱을 거의 "워크"로 사용 하거나 *teleportation* 를 사용 하 여 더 긴 거리를 즉시 이동할 수 있습니다.

![Windows Mixed Reality 홈의 Teleportation](images/teleportation-500px.png)

**텔레포트 하려면:**
1. Teleportation reticle를 엽니다.
   * [동작 컨트롤러](motion-controllers.md)사용: 엄지 스틱을 앞으로 누르고 해당 위치에서 유지 합니다.
   * Xbox 컨트롤러 사용: 왼쪽 엄지 스틱을 앞으로 이동 하 여 해당 위치에 저장 합니다.
   * 마우스 사용: 마우스 오른쪽 단추 클릭 단추를 누른 채 스크롤 휠을 사용 하 여 텔레포트 할 때 사용할 방향을 회전 합니다.
2. Reticle를 텔레포트로 이동 합니다.
   * [동작 컨트롤러](motion-controllers.md)사용: 엄지 스틱 앞에 있는 컨트롤러를 reticle 이동 합니다.
   * Xbox 컨트롤러 사용: reticle를 이동 하려면 [응시](gaze.md) 를 사용 합니다.
   * 마우스를 사용 하 여 마우스를 이동 하 여 reticle를 이동 합니다.
3. Reticle가 배치 된 위치를 텔레포트 하려면 단추를 놓습니다.

**거의 모든 "연습:"**
* [동작 컨트롤러](motion-controllers.md)사용: 엄지 스틱 및 대기를 클릭 한 다음 "워크" 하려는 방향으로 엄지 스틱을 이동 합니다.
* Xbox 컨트롤러 사용: 왼쪽 엄지 스틱 및 대기를 클릭 한 다음 "워크" 하려는 방향으로 엄지 스틱을 이동 합니다.

## <a name="immersive-headset-input-support"></a>모던 헤드셋 입력 지원

[Windows Mixed reality 몰입 형 헤드셋](immersive-headset-hardware-details.md) 은 Windows mixed reality 홈을 탐색 하기 위한 여러 입력 형식을 지원 합니다. HoloLens는 실제로 안내 하 고 환경을 확인 하기 때문에 탐색을 위한 액세서리 입력을 지원 하지 않습니다. 그러나 HoloLens는 앱과 상호 작용 하기 위한 [입력을 지원](hardware-accessories.md) 합니다.

### <a name="motion-controllers"></a>동작 컨트롤러

Windows mixed reality 환경에는 헤드셋의 센서만 사용 하 여 6 자유도를 지 원하는 Windows Mixed Reality [동작 컨트롤러가](motion-controllers.md) 있습니다. 여기에는 외부 카메라 또는 마커가 필요 하지 않습니다.

탐색 명령은 곧 제공 될 예정입니다.

### <a name="gamepad"></a>게임 패드
* **왼쪽 엄지 스틱:**
  * 왼쪽 엄지 스틱을 앞으로 길게 [teleportation](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) reticle를 가져옵니다.
  * 왼쪽, 오른쪽 또는 뒤로 엄지 스틱을 탭 하 여 왼쪽, 오른쪽 또는 뒤로 이동 합니다.
  * 왼쪽 엄지 스틱 및 대기를 클릭 한 다음, 원하는 방향으로 엄지 스틱을 이동 [합니다.](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)
* **오른쪽 엄지 스틱** 을 왼쪽 또는 오른쪽으로 눌러서 45도로 향하는 방향을 회전 합니다.
* **A** 단추를 누르면 선택이 수행 되 고 [공기 탭](gestures.md#air-tap) 제스처 처럼 작동 합니다.
* **가이드** 단추를 누르면 [시작 메뉴가](navigating-the-windows-mixed-reality-home.md#start-menu) 표시 되 고 [블 룸](gestures.md#bloom) 제스처 처럼 작동 합니다.
* **왼쪽 및 오른쪽 트리거** 를 누르면 홈에서 상호 작용 하는 2d 데스크톱 앱을 확대 및 축소할 수 있습니다.

### <a name="keyboard-and-mouse"></a>키보드 및 마우스

**참고:** **Windows 키 + Y** 를 사용 하 여 PC의 데스크톱과 Windows Mixed Reality 홈을 제어 하기 위해 마우스를 전환 합니다.

Windows Mixed Reality 홈 내에서:
* 마우스 **왼쪽 단추 클릭** 단추를 누르면 선택이 수행 되 고 [air 탭](gestures.md#air-tap) 제스처 처럼 작동 합니다.
* 마우스 오른쪽 단추를 **클릭** 하면 [teleportation](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) reticle이 표시 됩니다.
* 키보드에서 **Windows** 키를 누르면 [시작 메뉴가](navigating-the-windows-mixed-reality-home.md#start-menu) 표시 되 고 [블 룸](gestures.md#bloom) 제스처 처럼 작동 합니다.
* 2D 데스크톱 앱에서 [gazing](gaze.md) 때 마우스 왼쪽 단추를 **클릭** 하 여 선택 하 고 **마우스 오른쪽 단추를 클릭** 하 여 상황에 맞는 메뉴를 표시 한 다음 **스크롤 휠을** 사용 하 여 PC의 데스크톱과 마찬가지로 스크롤할 수 있습니다.

## <a name="cortana"></a>Cortana

[Cortana](voice-input.md#hey-cortana) 는 PC 및 휴대폰에서와 마찬가지로 Windows Mixed Reality의 개인 길잡이입니다. HoloLens에는 기본 제공 마이크가 있지만 몰입 형 헤드셋에는 추가 하드웨어가 필요할 수 있습니다. Cortana를 사용 하 여 앱을 열고, 장치를 다시 시작 하 고, 온라인으로 조회 하는 등의 작업을 수행 합니다. 개발자는 Cortana를 해당 환경에 [통합](https://dev.windows.com/cortana) 하도록 선택할 수도 있습니다.

음성 명령을 사용 하 여 집 주위를 볼 수도 있습니다. 예를 들어 장치에 따라 단추 ( [응시](gaze.md) 또는 컨트롤러 사용)를 가리키고 "선택" 이라고 합니다. 다른 음성 명령에는 "이동 홈", "크게", "더 작음", "닫기" 및 "얼굴"이 포함 됩니다.

## <a name="store-settings-and-system-apps"></a>저장소, 설정 및 시스템 앱

Windows Mixed Reality에는 다음과 같은 다양 한 기본 제공 앱이 있습니다.
* 앱 및 게임을 가져오는 **Microsoft Store**
* 시스템 및 시스템 앱에 대 한 피드백을 제출 하는 **피드백 허브**
* 시스템 설정 (네트워킹 및 시스템 업데이트[포함](connecting-to-wi-fi-on-hololens.md) )을 구성 하는 **설정**
* 웹 사이트를 찾아보는 **Microsoft Edge**
* 사진과 비디오를 보고 공유할 수 있는 **사진**
* **보정** (HoloLens에만 해당) 현재 사용자에 게 HoloLens 환경을 조정할 수 있습니다.
* **제스처 배우기** (HoloLens) 또는 **혼합 현실 배우기** (몰입 형 헤드셋)를 사용 하 여 장치를 사용 하는 방법을 알아보세요.
* 혼합 현실 콘텐츠를 사용 하 여 전 세계를 장식 하는 **3D 뷰어**
* **혼합 현실 포털** (데스크톱) 다른 사람이 볼 수 있도록 모던 헤드셋을 설정 및 관리 하 고 헤드셋에서 보기의 실시간 미리 보기를 스트리밍하는 데 사용할 수 있습니다.
* 360 비디오와 최신 영화 및 tv 쇼를 보기 위한 **영화 및 tv**
* 모든 가상 길잡이 요구 사항에 대 한 **Cortana**
* **바탕 화면** 몰입 형 헤드셋에서 데스크톱 모니터를 볼 때 사용할 모던 헤드셋
* **파일 탐색기** 장치에 있는 파일 및 폴더에 액세스

## <a name="see-also"></a>참조
* [앱 보기](app-views.md)
* [모션 컨트롤러](motion-controllers.md)
* [하드웨어 액세서리](hardware-accessories.md)
* [HoloLens의 환경 고려 사항](environment-considerations-for-hololens.md)
* [3D 앱 응용 프로그램 구현](implementing-3d-app-launchers.md)
* [Windows Mixed Reality 홈에서 사용할 3D 모델 만들기](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
