---
title: 앱 보기
description: Windows Mixed Reality 앱에서 볼 수 있는 두 가지 종류의 보기는 몰입 형 뷰와 2D 뷰입니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 몰입 형 보기, 2D 보기, 슬레이트, 앱
ms.openlocfilehash: a5b50df5be31d66a866e691d9e059bcf38672064
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437013"
---
# <a name="app-views"></a>앱 보기

Windows 앱에는 **몰입 형** 보기와 **2d 보기**의 두 가지 보기가 포함 될 수 있습니다. 앱은 다양 한 몰입 형 보기와 2D 보기 간에 전환할 수 있습니다 .이 보기는 모니터에서 창으로, 또는 슬레이트로 헤드셋에서 2D 뷰를 표시 합니다. 하나 이상의 몰입 형 보기가 있는 앱은 **혼합 현실 앱**으로 분류 됩니다. 몰입 형 보기가 없는 앱은 **2d 앱**입니다.

## <a name="immersive-views"></a>몰입 형 보기

몰입 형 보기를 사용 하면 앱이 사용자의 세계에서 holograms을 만들거나 가상 환경에서 사용자를 컨퍼런스 수 있습니다. 앱이 몰입 형 보기에서 holograms 때 다른 앱은 동시&mdash;에 그리지 않습니다. 여러 앱에서는 함께 합성 되지 않습니다. 앱이 사용자의 헤드 이동과 일치 하도록 장면을 [렌더링](rendering.md) 하는 큐브 뷰를 지속적으로 조정 하 여, 응용 프로그램에서 [세계에 잠긴](coordinate-systems.md) holograms를 렌더링 하 여 실제 세계에 고정 된 지점에 유지 하거나, 보유 하 고 있는 가상 환경을 사용자가 내에서 이동 하는 위치입니다.

몰입 형 보기에서 ![holograms를 전 세계에 배치할 수 있습니다.](images/designoverview-940px.jpg)<br>
*몰입 형 보기에서 holograms를 전 세계에 배치할 수 있습니다.*

[HoloLens](hololens-hardware-details.md)에서 앱은 사용자의 실제 환경 위에 holograms을 렌더링 합니다. [Windows Mixed Reality 몰입 형 헤드셋](immersive-headset-hardware-details.md)에서 사용자는 실제 세계를 볼 수 없으므로 앱에서 사용자에 게 표시 되는 모든 항목을 렌더링 해야 합니다.

[Windows Mixed Reality 홈](navigating-the-windows-mixed-reality-home.md) (환경 주위에 배치한 시작 메뉴 및 holograms 포함)은 몰입 형 보기에서 렌더링 되지 않습니다. HoloLens에서 몰입 형 보기가 표시 되는 동안 발생 하는 시스템 알림은 Cortana에 의해 통화 릴레이 되며 사용자는 음성 입력으로 응답할 수 있습니다.

몰입 형 보기에서 앱은 모든 입력을 처리 해야 합니다. Windows Mixed Reality의 입력은 [응시](gaze-and-commit.md), [제스처](gaze-and-commit.md#composite-gestures) (HoloLens 전용), [음성](voice-input.md) 및 [동작 컨트롤러](motion-controllers.md) (몰입 형 헤드셋 전용)로 구성 됩니다.

## <a name="2d-views"></a>2D 뷰

Windows Mixed Reality 홈에 대 한 여러 개의 2D 보기가 ![](images/teleportation-940px.png)<br>
*Windows Mixed Reality 홈 주위에 2D 보기가 배치 된 여러 앱*

2D 보기가 포함 된 앱이 [Windows Mixed Reality 홈](navigating-the-windows-mixed-reality-home.md) ("셸"이 라고도 함)에는 앱 시작 관리자 및 사용자가 전 세계에 배치한 다른 holograms 함께 렌더링 되는 가상 슬레이트로 표시 됩니다. 사용자는 크기에 관계 없이 고정 된 해상도로 유지 되지만이 슬레이트를 이동 하 고 크기를 조정할 수 있습니다. 앱의 첫 번째 뷰가 2D 보기 이면 2D 콘텐츠는 앱을 시작 하는 데 사용 되는 것과 동일한 슬레이트를 채웁니다.

데스크톱 헤드셋에서 현재 데스크톱 모니터에서 실행 되는 모든 UWP (유니버설 Windows 플랫폼) 앱을 실행할 수 있습니다. 이러한 앱은 현재 2D 뷰를 이미 렌더링 하 고 있으며 해당 콘텐츠는 시작 시 사용자 세계의 슬레이트에 자동으로 표시 됩니다. 2D UWP 앱은 슬레이트으로 데스크톱 헤드셋 및 HoloLens에서 실행 되도록 **Windows 유니버설** 장치 제품군을 대상으로 지정할 수 있습니다.

2D 보기의 한 가지 주요 용도는 시스템 키보드를 사용할 수 있는 텍스트 입력 양식을 표시 하는 것입니다. 셸이 몰입 형 보기 위에 렌더링 될 수 없으므로 앱은 시스템 키보드를 표시 하기 위해 2D 보기로 전환 해야 합니다. 텍스트 입력을 허용 하려는 앱은 텍스트 상자를 사용 하 여 2D 보기로 전환할 수 있습니다. 해당 텍스트 상자에 포커스가 있는 동안 시스템은 시스템 키보드를 표시 하므로 사용자가 텍스트를 입력할 수 있습니다.

데스크톱 PC에서 앱은 데스크톱 모니터와 연결 된 헤드셋 모두에 2D 보기를 포함할 수 있습니다. 예를 들어 주 2D 보기를 사용 하 여 데스크톱 모니터에서 Edge를 탐색 하 여 360 수준 비디오를 찾을 수 있습니다. 비디오를 재생할 때 Edge는 헤드셋 내에서 보조 몰입 형 보기를 시작 하 여 몰입 형 비디오 콘텐츠를 표시 합니다.

## <a name="see-also"></a>참고 항목

* [앱 모델](app-model.md)
* [혼합 현실에 사용되는 2D UWP 앱 업데이트](building-2d-apps.md)
* [HolographicSpace 받기](getting-a-holographicspace.md)
* [Windows Mixed Reality 홈 탐색](navigating-the-windows-mixed-reality-home.md)
* [혼합 현실 앱의 종류](types-of-mixed-reality-apps.md)
