---
title: 앱 보기
description: Windows Mixed Reality 앱에서 보기의 두 종류는 몰입 형 뷰 및 2D 보기입니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 몰입 형 뷰, 슬레이트, 2D 보기 앱
ms.openlocfilehash: 2cf65941616ac6906d40e4b4616311317ac705d3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604732"
---
# <a name="app-views"></a>앱 보기

Windows 앱에는 두 종류의 보기를 포함할 수 있습니다 **몰입 형 뷰** 하 고 **2D 뷰**합니다. 앱은 해당 다양 한 몰입 형 뷰 및 슬레이트와 헤드셋 또는 창으로 모니터에서 2D 해당 뷰를 보여 주는 2D 뷰 간에 전환할 수 있습니다. 하나 이상의 몰입 형 보기가 있는 앱으로 분류 됩니다 **혼합 현실 앱**합니다. 절대로 몰입 형 뷰는 앱 **2D 앱**합니다.

## <a name="immersive-views"></a>몰입 형 뷰

몰입 형 뷰를 앱 홀로그램와 관련해 서 전 세계에서 만들거나 가상 환경에서 사용자를 세계 체험해 하는 기능을 제공 합니다. 동시에 다른 앱 없음 그리기는 앱을 몰입 형 뷰에서 그릴 때&mdash;여러 앱에서 홀로그램 서로 하지 합성 합니다. 큐브 뷰를 지속적으로 조정 하 여 사용자 [앱이 렌더링](rendering.md) 헤드 이동을 사용자에 맞게 장면을 앱 렌더링할 수 있습니다 [world 잠긴](coordinate-systems.md) 실제 고정된 지점에서 남아 있는 홀로그램 세계, 또는 그 사용자가 이동 하는 대로 해당 위치를 보유 하는 가상 세계를 렌더링할 수 있습니다.

![몰입 형 보기에서 홀로그램와 관련해 서 전 세계에 배치할 수 있습니다.](images/designoverview.jpg)<br>
*몰입 형 보기에서 홀로그램에에서 배치할 수와 관련해 서 전 세계*

온 [HoloLens](hololens-hardware-details.md), 앱 사용자의 실제 환경 기반으로 해당 홀로그램을 렌더링 합니다. 에 [Windows Mixed Reality 몰입 형 헤드셋](immersive-headset-hardware-details.md), 사용자는 실제 세계에서 볼 수 없습니다 및 사용자에 게 표시 앱 모두를 렌더링 해야 합니다.

합니다 [Windows Mixed Reality 홈](navigating-the-windows-mixed-reality-home.md) (시작 메뉴 및 홀로그램 환경 주위의 배치한 포함) 하는 동안에 몰입 감이 뛰어난 렌더링 하지 않습니다 중 하나를 확인 합니다. HoloLens, Cortana, 몰입 형 뷰를 표시 하는 동안 발생 하는 모든 시스템 알림의 음성으로 릴레이 켜고 사용자 음성 입력으로 응답할 수 있습니다.

뷰에서 몰입 형 앱 모든 입력 처리를 담당 이기도 합니다. Windows Mixed Reality의 입력으로 이루어져 [gaze](gaze.md)를 [제스처](gestures.md) (HoloLens에만 해당), [음성](voice-input.md) 고 [컨트롤러 동작](motion-controllers.md) (몰입 형 헤드셋만)입니다.

## <a name="2d-views"></a>2D 뷰

![Windows Mixed Reality 홈 주위 2D 뷰를 여러 개 배치](images/teleportation-640px.png)<br>
*Windows Mixed Reality 홈 주위에 2D 뷰를 사용 하 여 여러 앱*

2D 뷰를 사용 하 여 앱에 표시 합니다 [Windows Mixed Reality 홈](navigating-the-windows-mixed-reality-home.md) ("셸" 라고도 함) 슬레이트를 가상으로 앱 시작 관리자 및 사용자가 해당 환경에서 배치 다른 홀로그램와 함께 렌더링 합니다. 사용자가 해당 크기에 관계 없이 고정 된 해상도에서 그대로 유지 하지만이 슬레이트를 이동, 크기 조정 조정할 수 있습니다. 앱의 첫 번째 보기 2D 뷰일 경우 2D 콘텐츠 응용 프로그램을 실행 하는 데 동일한 슬레이트를 채워집니다.

데스크톱에서 헤드셋에서 현재 데스크톱 모니터에서 실행 되는 모든 유니버설 Windows 플랫폼 (UWP) 앱을 실행할 수 있습니다. 이러한 앱은 현재 2D 뷰 렌더링 이미와 같은 콘텐츠 시작 될 때 사용자의 환경에서 슬레이트를 자동으로 표시 됩니다. 2D UWP 앱 대상으로 지정할 수는 **Windows.Universal** 장치 제품군 및 HoloLens 슬레이트와 데스크톱 모두 헤드셋에서 실행 합니다.

2D 뷰의 키 용도 수 있도록 하는 텍스트 입력 폼을 표시 하는 것 하나 시스템 키보드를 사용 합니다. 셸에서 몰입 형 뷰를 기반으로 렌더링할 수 없습니다, 때문에 앱에 시스템 키보드를 표시 하는 2D 보기를 전환 해야 합니다. 텍스트 입력을 허용 하려는 앱은 텍스트 상자를 사용 하 여 2D 보기로 전환할 수 있습니다. 해당 텍스트 상자에 포커스가 있는 동안 사용자가 텍스트를 입력할 수 있도록 시스템 키보드를 시스템에 표시 됩니다.

데스크톱 PC에 앱 수 있다는 두 데스크톱 모니터에는 연결 된 헤드셋에서 2D 뷰 note 합니다. 예를 들어, 360도 비디오를 찾아볼 수 주 2D 뷰를 사용 하 여 데스크톱 모니터에 지를 찾아볼 수 있습니다. 해당 비디오를 재생할 때 모서리 몰입 형 비디오 콘텐츠를 표시할 헤드셋 내 보조 몰입 형 보기를 시작 됩니다.

## <a name="see-also"></a>참조

* [앱 모델](app-model.md)
* [혼합된 현실에 대 한 2D UWP 앱 업데이트](building-2d-apps.md)
* [HolographicSpace 가져오기](getting-a-holographicspace.md)
* [Windows Mixed Reality 홈 탐색](navigating-the-windows-mixed-reality-home.md)
* [혼합된 현실 앱 유형](types-of-mixed-reality-apps.md)
