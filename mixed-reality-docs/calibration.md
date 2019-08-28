---
title: 보정
description: IPD (interpupillary distance)를 보정 하면 시각적 개체의 품질을 향상 시킬 수 있습니다. HoloLens와 Windows Mixed Reality 모던 헤드셋은 IPD를 사용자 지정 하는 방법을 제공 합니다.
author: xerxesb85
ms.author: xerxesb
ms.date: 02/24/2019
ms.topic: article
keywords: 보정, 편안 함, 시각적 개체, 품질, ipd
ms.openlocfilehash: 1fc3904f4b3e441a967616f20e4287dbc7f08835
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047049"
---
# <a name="improve-visual-quality-and-comfort"></a>시각적 품질 및 편안 함 개선
HoloLens, HoloLens 2 및 Windows Mixed Reality 몰입 형 헤드셋은 시각적 효과의 품질을 향상 시키는 다양 한 방법을 제공 합니다. 

## <a name="hololens-2"></a>Hololens 2

### <a name="calibration"></a>보정

Hololens 2는 최고 품질의 시각적 이미지를 제공 하 고 고객에 게 편안 하 게 사용할 수 있도록 설계 되었습니다. 아이 추적 기술은 가상 환경을 보고 상호 작용 하는 사용자 환경을 개선 하는 데 사용 됩니다.  
HoloLens 2에서는 장치를 설치 하는 동안 시각적 개체를 보정 하 라는 메시지가 표시 됩니다. 사용자에 게는 고정 대상 집합을 확인 하 라는 메시지가 표시 됩니다. 이렇게 하면 장치에서 사용자에 대 한 홀로그램 렌더링을 조정 하 여 holograms, 편안한 3D 시청 환경 및 향상 된 디스플레이 품질을 정확 하 게 배치할 수 있습니다. 모든 조정은 수동 조정을 수행할 필요 없이 즉시 수행 됩니다. 랜드마크로 눈동자를 사용 하 여 모든 사용자에 대 한 장치를 조정 하 고, 헤드셋이 약간의 사용을 통해 약간 이동 됨에 따라 시각적 개체를 조정 합니다. 눈 위치 추적은 시스템에서 내부적으로 사용 되며 개발자는이 기능을 활용 하기 위해 아무것도 수행할 필요가 없습니다. 개발자는이 정보를 사용할 수 없습니다. Hololens 2에서는 보정을 수행 하는 경우 모든 사용자에 대 한 정확한 눈동자를 추적할 수 있습니다. 시선 추적을 사용하여 애플리케이션에서는 사용자가 실시간으로 보는 곳을 추적할 수 있습니다. 이는 개발자가 Holographic 환경 내에서 새로운 수준의 컨텍스트, 인간 이해 및 상호 작용을 최대한 활용할 수 있도록 하는 기본 기능입니다.  
보정은 장치에 로컬로 저장 되며 어떤 계정 정보에도 연결 되지 않습니다. 보정 없이 장치를 사용한 사용자의 레코드는 없습니다. 이는 새 사용자가 처음으로 장치를 사용 하는 경우 시각적 개체를 보정 하는 메시지를 표시 하 고 이전에는 보정을 옵트아웃 하거나 보정에 실패 한 경우에는 시각적 개체를 보정 하는 메시지를 받게 됩니다 보정은 항상 **설정** > **개인 정보 취급 방침** > **추적**장치에서 삭제할 수 있습니다. 

### <a name="calibration-failures"></a>보정 오류

보정은 대부분의 사용자에 대해 작동 해야 하지만 사용자가 성공적으로 보정할 수 없는 경우도 있습니다.  
보정 오류의 몇 가지 예는 다음과 같습니다.
- 보정 환경에서 보정 대상을 따르지 않고 무시를 가져오는 사용자
- 더티 또는 긁힌 장치 센터 또는 장치 센터의 위치가 올바르게 지정 되지 않았습니다. 
- 더티 또는 긁힌
- 특정 유형의 연락처 lenses 및 고 사양 (컬러 연락처 lenses, 일부 toric 연락처 lenses, IR 차단, 몇 가지 높은 prescription 고, 선글라스 등)
- 구성을, eyelash 확장
- 눈 및/또는 장치 Occlusions (머리카락, 일부 굵은 eyeglass 프레임)
- 아이 physiology, 특정 눈동자 조건 및/또는 눈 수술 (좁은 눈, 긴 eyelashes, amblyopia, nystagmus, LASIK 또는 기타 아이 surgeries의 일부 사례 등)

보정에 실패 한 경우 다음 해결 방법 중 하나를 시도 합니다. 
- 장치 센터 정리
- 제거
- 장치 센터를 모든 방식으로 푸시
- 센서 또는 눈에 방해 하지 않는지 (예: 머리)이 없는지 확인 합니다. 
- 대화방에 충분 한 조명이 있고 직접 햇빛에 있지 않은지 확인 합니다.
- 보정 중에 대상을 신중 하 게 따라야 합니다.

모든 지침을 따르고 보정을 계속 실패 하는 경우 **설정** > **시스템** > **보정**에서 보정 프롬프트를 사용 하지 않도록 설정할 수 있습니다. ' 새로운 사용자가이 Hololens를 사용 하는 경우 자동으로 눈동자 보정 실행을 요청 해야 합니다. 이로 인해 홀로그램 렌더링 품질과 discomfort이 악화 될 수 있습니다.

### <a name="launching-the-calibration-app-from-settings"></a>설정에서 보정 앱 시작
1. 시작 제스처를 사용 하 여 [시작 메뉴](navigating-the-windows-mixed-reality-home.md#start-menu)를 가져옵니다.
2. **설정이** 시작에 고정 되지 않은 경우 모든 앱을 보려면 **모든 앱** 을 선택 합니다.
3. 시작 **설정**입니다.
4. **시스템** > **보정** 눈 모양 보정으로 이동 하 여 눈동자 보정 실행을 선택 합니다. > 

### <a name="calibration-when-sharing-a-devicesession"></a>장치/세션을 공유할 때의 보정

Hololens 2는 각 사용자가 장치 설치를 통과 하지 않아도 사용자 간에 공유할 수 있습니다. 사용자가 장치를 처음 사용 하는 경우 Hololens 2는 사용자에 게 장치를 배치할 때 시각적 개체를 보정할 지 묻는 메시지를 표시 합니다. 사용자가 이전에 장치에서 시각적 개체를 보정 한 경우 사용자가 헤드에 장치를 배치할 때 품질 및 편안 하 게 볼 수 있도록 디스플레이를 원활 하 게 조정 합니다. 


## <a name="hololens-v1"></a>Hololens (v1)

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
2. 설정이 **+** 시작에 고정 되지 않은 경우 모든 앱을 보려면 선택 합니다.
3. 시작 **설정**입니다.
4. **시스템** > **유틸리티** 로 이동 하 여 **보정 열기**를 선택 합니다.

![설정 앱에서 보정 앱 시작](images/calibration-settings-500px.jpg)


## <a name="immersive-headsets"></a>몰입형 헤드셋

헤드셋 내에서 IPD를 변경 하려면 설정 앱을 열고 **Mixed reality** > **헤드셋 표시** 로 이동 하 여 슬라이더 컨트롤을 이동 합니다. 헤드셋에서 실시간으로 변경 내용을 볼 수 있습니다. IPD을 알고 있는 경우 optometrist에 대 한 방문에서 직접 입력할 수 있습니다.

PC에 **설정** > **혼합 현실** > **헤드셋 표시** 로 이동 하 여이 설정을 조정할 수도 있습니다.

헤드셋에서 IPD 사용자 지정을 지원 하지 않는 경우이 설정이 사용 되지 않습니다.

## <a name="see-also"></a>참조
* [HoloLens의 환경 고려 사항](environment-considerations-for-hololens.md)
