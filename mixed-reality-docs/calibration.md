---
title: 보정
description: IPD (interpupillary distance)를 보정 하면 시각적 개체의 품질을 향상 시킬 수 있습니다. HoloLens와 Windows Mixed Reality 모던 헤드셋은 IPD를 사용자 지정 하는 방법을 제공 합니다.
author: xerxesb85
ms.author: xerxesb
ms.date: 02/24/2019
ms.topic: article
keywords: 보정, 편안 함, 시각적 개체, 품질, ipd
ms.openlocfilehash: 5f8e6aef1df0efe4c64c807e627f69c7949363f2
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974810"
---
# <a name="improve-visual-quality-and-comfort"></a>시각적 품질 및 편안 함 개선
HoloLens, HoloLens 2 및 Windows Mixed Reality 몰입 형 헤드셋은 시각적 효과의 품질을 향상 시키는 다양 한 방법을 제공 합니다. 

## <a name="hololens"></a>HoloLens

IPD (interpupillary distance)를 보정 하면 시각적 개체의 품질을 향상 시킬 수 있습니다.

### <a name="during-setup"></a>설치 하는 동안

![두 번째 단계의 IPD 손가락 맞춤 화면](images/ipd-finger-alignment-300px.jpg)<br>

*두 번째 단계의 IPD 손가락 맞춤 화면*

HoloLens에는 설치 중에 시각적 개체를 보정 하 라는 메시지가 표시 됩니다. 이를 통해 장치는 사용자의 [interpupillary 거리](https://en.wikipedia.org/wiki/Interpupillary_distance) (IPD)에 따라 홀로그램 표시를 조정할 수 있습니다. 잘못 된 IPD를 사용 하는 경우 holograms는 불안정 하거나 잘못 된 거리에 표시 될 수 있습니다.

Cortana가 자신을 도입 하면 첫 번째 설정 단계는 보정입니다. 이 설정 단계에서 보정 단계를 완료 하는 것이 좋지만 Cortana가 "건너뛰기"로 이동 하 라는 메시지가 표시 될 때까지 대기 하 여이 단계를 건너뛸 수 있습니다.

사용자는 자신의 손가락을 눈에 관계 없이 6 개의 대상과 맞추고 있습니다. 이 프로세스를 통해 HoloLens는 사용자에 대 한 올바른 IPD를 설정 합니다. 새 사용자에 대해 보정을 업데이트 하거나 조정 해야 하는 경우 보정 앱을 사용 하 여 설치 프로그램 외부에서 해당 보정을 실행할 수 있습니다.

### <a name="calibration-app"></a>보정 앱

보정 앱을 통해 언제 든 지 보정을 수행할 수 있습니다. 보정 앱은 기본적으로 설치 되며, 시작 메뉴 또는 설정 앱을 통해 액세스할 수 있습니다. 시각적 개체의 품질을 개선 하거나 새 사용자에 대 한 시각적 개체를 보정 하려면 보정을 사용 하는 것이 좋습니다.

**시작에서 앱 시작**
1. [블 룸](gestures.md#bloom) 를 사용 하 여 [시작 메뉴](navigating-the-windows-mixed-reality-home.md#start-menu)를 가져옵니다.
2. 모든 **+** 앱을 보려면 선택 합니다.
3. **보정**을 시작 합니다.

![셸에서 보정 앱에 액세스](images/calibration-shell.png)

![시작 된 후에 라이브 큐브로 표시 되는 보정 앱](images/calibration-livecube-200px.png)

**설정에서 앱 시작**
1. [블 룸](gestures.md#bloom) 를 사용 하 여 [시작 메뉴](navigating-the-windows-mixed-reality-home.md#start-menu)를 가져옵니다.
2. 설정이 **+** 시작에 고정 되지 않은  경우 모든 앱을 보려면 선택 합니다.
3. 시작 **설정**입니다.
4. **시스템** > **유틸리티** 로 이동 하 여 **보정 열기**를 선택 합니다.

![설정 앱에서 보정 앱 시작](images/calibration-settings-500px.jpg)

## <a name="hololens-2"></a>HoloLens 2

### <a name="calibration"></a>보정 

HoloLens 2에서는 장치를 설치 하는 동안 시각적 개체를 보정 하 라는 메시지가 표시 됩니다. 사용자에 게는 고정 대상 집합을 확인 하 라는 메시지가 표시 됩니다. 이를 통해 장치는 holograms를 정확 하 게 배치 하 고 더 편안한 3D 보기 환경을 개선 하 고 디스플레이 품질을 개선 하도록 사용자에 게 홀로그램 렌더링을 조정할 수 있습니다. 모든 조정은 수동 조정을 수행할 필요 없이 즉시 수행 됩니다. 

### <a name="calibration-when-sharing-a-device"></a>장치를 공유 하는 경우의 보정 

Hololens 2 장치를 사용할 필요 없이 사용자 간에 장치를 공유할 수 있습니다. 사용자가 장치를 처음 사용 하는 경우 Hololens 2는 사용자에 게 장치를 배치할 때 시각적 개체를 보정할 지 묻는 메시지를 표시 합니다. 사용자가 이미 장치에서 시각적 개체를 보정 한 경우 사용자가 헤드에 장치를 배치할 때 품질 및 편안한 보기 환경을 위해 디스플레이가 원활 하 게 조정 됩니다.  

### <a name="launching-the-calibration-app-from-settings"></a>설정에서 보정 앱 시작
1. 시작 제스처를 사용 하 여 시작 메뉴를 가져옵니다.
2. 설정이 **+** 시작에 고정 되지 않은  경우 모든 앱을 보려면 선택 합니다.
3. 시작 **설정**입니다.
4. **시스템** > **유틸리티** 로 이동 하 여 **보정 열기**를 선택 합니다.

## <a name="immersive-headsets"></a>몰입형 헤드셋

헤드셋 내에서 IPD를 변경 하려면 설정 앱을 열고 **Mixed reality** > **헤드셋 표시** 로 이동 하 여 슬라이더 컨트롤을 이동 합니다. 헤드셋에서 실시간으로 변경 내용을 볼 수 있습니다. IPD을 알고 있는 경우 optometrist에 대 한 방문에서 직접 입력할 수 있습니다.

PC에 **설정** > **혼합 현실** > **헤드셋 표시** 로 이동 하 여이 설정을 조정할 수도 있습니다.

헤드셋에서 IPD 사용자 지정을 지원 하지 않는 경우이 설정이 사용 되지 않습니다.

## <a name="see-also"></a>참조
* [HoloLens의 환경 고려 사항](environment-considerations-for-hololens.md)
