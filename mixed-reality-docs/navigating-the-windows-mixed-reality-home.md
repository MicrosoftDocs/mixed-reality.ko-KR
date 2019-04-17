---
title: Windows Mixed Reality 홈 탐색
description: HoloLens 및 Windows Mixed Reality 헤드셋 시작에 배치 하 고 (실제 또는 디지털) 여부 앱 및 사용자 환경에서 3D 모델을 조작 하는 패러다임을 공유 합니다. Windows Mixed Reality 장치 유형에 모두에서 홈을 탐색 하는 방법에 알아봅니다.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 셸, os, 플랫폼, cliff 집, 집, home, 환경, 시작, 시작 메뉴, 홈 메뉴, pin, 앱, 시작 앱을 앱 텔레포트 배치, 이동, 이동
ms.openlocfilehash: 1ca6dd66506a64ad2e1c21870fee2725ddf20bd8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604897"
---
# <a name="navigating-the-windows-mixed-reality-home"></a>Windows Mixed Reality 홈 탐색

Windows PC 환경을 바탕 화면에서 시작 하는 것 처럼 Windows Mixed Reality 홈으로 시작 합니다. Windows Mixed Reality 홈 타고 이해 하 고 3D 위치를 탐색 하는 능력을 활용 합니다. HoloLens를 사용 하 여 집에 실제 공간이 없습니다. 몰입 형 헤드셋을 사용 하 여 집 가상 위치입니다.

집 여기서 사용할지 시작 메뉴를 열고 앱 및 콘텐츠를 배치할 이기도 합니다. 혼합된 현실 콘텐츠로 홈을 입력 하 고 동시에 여러 앱을 사용 하 여 멀티 태스크 수 있습니다. 장치를 다시 시작 하는 경우에 집에 배치 작업을 유지 합니다.

## <a name="start-menu"></a>시작 메뉴

![Microsoft HoloLens 시작 메뉴](images/start-500px.png)

시작 메뉴 이루어져 있습니다.
* 시스템 정보 (예: 네트워크 상태, 배터리 백분율, 현재 시간 및 볼륨)
* Cortana (몰입 형 헤드셋, 시작 타일에서;에 시작의 맨 위에 있는 HoloLens)
* 고정 된 앱
* 모든 앱 (더하기) 단추
* 사진 및 비디오 단추 [혼합 현실 캡처](mixed-reality-capture.md)

보기 간에 전환 고정 된 앱 및 모든 앱 더하기를 선택 하 여 또는 빼기 단추입니다. HoloLens의 시작 메뉴를 열려면 bloom 제스처를 사용 합니다. 몰입 형 헤드셋에서 컨트롤러에서 Windows 단추를 누릅니다.

## <a name="launching-apps"></a>앱 시작

앱을 시작 하려면 시작 시 선택 합니다. 시작 메뉴 사라지고 2D 창으로 배치 모드에서 앱을 열기 또는 [3D 모델](implementing-3d-app-launchers.md)합니다.

앱을 실행 하려면 다음 집에 배치 해야 합니다.
1. 사용 하 여 사용자 [gaze](gaze.md) 또는 컨트롤러 만들려는 앱의 위치입니다. 어디에 배치 하는 공간에 맞게 자동으로 (크기 %에 위치) 조정 됩니다.
2. 어-탭 (HoloLens) 또는 선택 단추 (몰입 형 헤드셋)를 사용 하 여 앱을 배치 합니다. 취소 하 고 다시 시작 메뉴 가져오기, 블 룸 제스처 또는 Windows 단추를 사용 합니다.

[2D 앱](building-2d-apps.md), 데스크톱, 모바일, 생성 또는 Xbox를 사용 하 여 혼합된 현실 몰입 형 앱으로 실행 되도록 수정할 수는 [HolographicSpace API](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx)합니다. 몰입 형 앱 및 몰입 형 환경을 홈에서 사용자를 안내 합니다. 사용자는 블 룸 제스처 (HoloLens) 또는 (몰입 형 헤드셋) 해당 컨트롤러에서 Windows 단추를 눌러 홈 반환할 수 있습니다.

앱-API 또는 Cortana를 통해 앱을 시작할 수도 있습니다.

![Windows Mixed Reality 홈에서 앱](images/mixed-reality-home-500px.png)

## <a name="moving-and-adjusting-apps"></a>이동 하 고 앱을 조정 합니다.

선택 **조정** 표시줄 표시 하기 위해 앱에서 해당 이동, 크기 조정를 제어 하 고 회전 혼합 현실 콘텐츠입니다. 이 과정을 완료 하는 경우 선택 **수행**합니다.

![조정 모드 (파란색 프레임)에서 저장소 슬레이트를 지정 합니다. 앱 바 확인 (최상위) '완료'와 '제거'를 포함 하도록 변경 된 단추입니다.](images/adjust-500px.png)

다른 앱은 앱 바에 추가 옵션이 있을 수 있습니다. Microsoft Edge에 예를 들어 *스크롤*를 *끌어서*, 및 *확대/축소* 선택 합니다. 

![HoloLens에서 실행 되는 2D 앱에 대 한 앱 모음](images/holobar-500px.png)

합니다 **다시** 단추 앱에서 이전에 본된 화면으로 되돌아갑니다. 앱에서 표시 하는 다른 앱으로 이동 하지 경험의 시작 부분에 도달 하면 중지 됩니다.

## <a name="getting-around-your-home"></a>집 살펴보기

사용 하 여 **HoloLens**, 집 이동할 물리적 공간을 통해 이동 합니다.

사용 하 여 **몰입 형 헤드셋**, 마찬가지로 시작 하 고 가상 세계의 비슷한 영역 내에서 이동 하 여 playspace에서 경비원 수 있습니다. 더 먼 간에 이동할 사용 스틱을 컨트롤러에서를 거의 "," 하거나 사용할 수 있습니다 *텔레포트* 하프를 즉시 이동 합니다.

![Windows Mixed Reality 홈에서 텔레포트](images/teleportation-500px.png)

**텔레포트:**
1. 텔레포트 십자선을 불러옵니다.
   * 사용 하 여 [컨트롤러 동작](motion-controllers.md): 스틱을 앞으로 키를 누릅니다 하 고 해당 위치에 저장 합니다.
   * Xbox 컨트롤러를 사용 하 여: 왼쪽된 엄지 스틱을 앞으로 키를 누릅니다 하 고 해당 위치에 저장 합니다.
   * 마우스를 사용 하 여: 마우스 오른쪽 단추 클릭 마우스 단추를 길게 (스크롤 휠을 사용 하 여 직면 하는 경우 하려는 방향 회전 텔레포트 있습니다).
2. 텔레포트 하려는 십자선을 배치 합니다.
   * 사용 하 여 [컨트롤러 동작](motion-controllers.md):는 십자선 이동할 (기반이 보류할 스틱을 앞으로) 컨트롤러를 기울입니다.
   * Xbox 컨트롤러를 사용 하 여: 사용 하 여 사용자 [gaze](gaze.md) 십자선을 이동할입니다.
   * 마우스를 사용 하 여: 십자선을 이동 하려면 마우스를 이동 합니다.
3. 십자선 놓여진 위치 텔레포트 단추를 놓습니다.

**가상으로 "설명:"**
* 사용 하 여 [컨트롤러 동작](motion-controllers.md): 엄지 스틱을 누른 상태에서를 클릭 한 다음 스틱을 "방법을 설명 합니다." 하려는 방향으로 이동
* Xbox 컨트롤러를 사용 하 여: 왼쪽된 엄지 스틱을 누른 상태에서 클릭 한 다음 스틱을 "방법을 설명 합니다." 하려는 방향으로 이동

## <a name="immersive-headset-input-support"></a>몰입 형 헤드셋 입력된 지원

[Windows Mixed Reality 몰입 형 헤드셋](immersive-headset-hardware-details.md) 홈 Windows Mixed Reality를 탐색 하기 위한 여러 입력된 유형을 지원 합니다. 실제로 경비원 및 환경을 참조 하기 때문에 HoloLens 탐색을 위한 액세서리 입력을 지원 하지 않습니다. 그러나는 HoloLens [입력을 지원](hardware-accessories.md) 앱 상호 작용에 대 한 합니다.

### <a name="motion-controllers"></a>컨트롤러 동작

Windows Mixed Reality를 사용 하 여 최상의 Windows Mixed Reality 됩니다 [컨트롤러 동작](motion-controllers.md) 헤드셋-표식이 필요 없거나 외부 카메라에서에서 방금 센서를 사용 하 여 해당 지원 6-의-자유도입니다. 추적!

탐색 명령 곧 제공 될 예정입니다.

### <a name="gamepad"></a>게임 패드
* **왼쪽된 엄지 스틱:**
  * 앞으로 왼쪽된 엄지 스틱을 누르고 합니다 [텔레포트](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) 십자선 합니다.
  * 왼쪽, 오른쪽, 엄지 스틱 또는 누르거나, 오른쪽, 왼쪽으로 이동할 다시 조금씩에서 다시 합니다.
  * 왼쪽된 엄지 스틱을 누른 상태에서 클릭 한 다음 스틱을 하려는 방향으로 이동 [거의 "방법을 설명 합니다."](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)
* 탭의 **오른쪽 엄지 스틱** 왼쪽 또는 오른쪽으로 45도 각도로 직면 한 방향으로 회전 합니다.
* 키를 눌러 합니다 **는** 단추 수행을 선택 하 고 처럼 동작 합니다 [어 탭](gestures.md#air-tap) 제스처입니다.
* 키를 눌러를 **가이드** 나타납니다는 [시작 메뉴](navigating-the-windows-mixed-reality-home.md#start-menu) 처럼 동작 하 고는 [블 룸](gestures.md#bloom) 제스처입니다.
* 키를 눌러 합니다 **왼쪽 및 오른쪽 트리거** 집에서 상호 작용 하는 2D 데스크톱 앱을 확대 하는 수 있습니다.

### <a name="keyboard-and-mouse"></a>키보드 및 마우스

**참고:** 사용 하 여 **Windows 키 + Y** 마우스 PC의 데스크톱 및 Windows Mixed Reality 홈 제어 사이 전환 합니다.

내 홈는 Windows의 혼합 현실:
* 키를 눌러 합니다 **마우스 왼쪽 단추로 클릭** 마우스 단추 수행을 선택 하 고 처럼 동작 합니다 [어 탭](gestures.md#air-tap) 제스처입니다.
* 보유 하는 **마우스 오른쪽 단추로 클릭** 마우스 단추를 표시 합니다 [텔레포트](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) 십자선 합니다.
* 키를 눌러를 **Windows** 키보드의 키를 표시 합니다 [시작 메뉴](navigating-the-windows-mixed-reality-home.md#start-menu) 처럼 동작 하 고는 [블 룸](gestures.md#bloom) 제스처입니다.
* 때 [gazing](gaze.md) 수 있습니다 2D 데스크톱 앱에서는 **마우스 왼쪽 단추 클릭** 를 선택 하려면 **마우스 오른쪽 단추로 클릭** 상황에 맞는 메뉴를 표시 하 고 사용 하는 **스크롤 휠이** 에 스크롤 (마찬가지로 PC의 바탕 화면에 표시)입니다.

## <a name="cortana"></a>Cortana

[Cortana](voice-input.md#hey-cortana) PC 및 phone에서 Windows Mixed Reality에서 사용자 개인 비서를와 비슷합니다. HoloLens 내장 마이크를 갖지만 몰입 형 헤드셋에는 추가 하드웨어가 필요할 수 있습니다. Cortana가 앱을 열고, 장치 다시 시작, 온라인 항목 조회 및 기타 정보를 사용 합니다. 개발자를 선택할 수도 있습니다 [Cortana 통합](https://dev.windows.com/cortana) 해당 환경에 있습니다.

또한 집 해결 하기 위해 음성 명령을 사용할 수 있습니다. 예를 들어, 단추를 가리킬 (사용 하 여 [gaze](gaze.md) 또는 장치에 따라 컨트롤러) "을 선택 합니다." 라고 말합니다. 다른 음성 명령에 "Go home", "큰", "작은" 포함 "닫기" 및 "에 직면 me."

## <a name="store-settings-and-system-apps"></a>저장소, 설정 및 시스템 앱

Windows Mixed Reality는와 같은 다양 한 기본 제공 앱에 있습니다.
* **Microsoft Store** 앱과 게임을 가져오려면
* **피드백 허브** 시스템 및 시스템 응용 프로그램에 대 한 피드백을 제출 하려면
* **설정을** 시스템 설정을 구성할 수 ([네트워킹을 포함 하 여](connecting-to-wi-fi-on-hololens.md) 및 시스템 업데이트)
* **Microsoft Edge** 웹 사이트를 탐색 하려면
* **사진** 사진 및 비디오 보기 및 공유 하려면
* **보정** (HoloLens에만 해당) 현재 사용자에 게 HoloLens 환경을 조정 합니다.
* **제스처에 알아봅니다** (HoloLens) 또는 **혼합 현실에 알아봅니다** (몰입 형 헤드셋) 장치를 사용 하 여 알아보려면
* **3D 뷰어** 혼합된 현실 콘텐츠를 사용 하 여 전 세계를 데코 레이트 하려면
* **혼합 현실 포털** (데스크톱)을 설정 및 몰입 형 헤드셋을 관리 하 고, 다른 사람이 볼 헤드셋에서 보기의 실시간 미리 보기를 스트리밍에 대 한 합니다.
* **영화 및 TV** 360 비디오 및 최신 동영상, tv를 보기 위한 보여 줍니다.
* **Cortana** 가상 상대방의 모든 필요한
* **데스크톱** (몰입 형 헤드셋)는 몰입 형 헤드셋에서 데스크톱 모니터 보기
* **파일 탐색기** 장치에 있는 파일 및 폴더 액세스

## <a name="see-also"></a>참조
* [앱 보기](app-views.md)
* [컨트롤러 동작](motion-controllers.md)
* [하드웨어 accessories](hardware-accessories.md)
* [HoloLens에 대 한 환경 고려 사항](environment-considerations-for-hololens.md)
* [3D 앱 시작 관리자를 구현합니다.](implementing-3d-app-launchers.md)
* [Windows Mixed Reality 집에서 사용할 3D 모델 만들기](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
