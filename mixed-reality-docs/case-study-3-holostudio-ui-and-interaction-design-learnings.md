---
title: 사례 연구-3 HoloStudio UI 및 상호 작용 디자인 학습
description: HoloStudio UI 및 상호 작용 디자인 학습
author: rwinj
ms.author: marcghal
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, HoloStudio, Windows Mixed 현실
ms.openlocfilehash: e01e2ea888398e9982b56fd95f90ef0731ec6bc2
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974824"
---
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a>사례 연구-3 HoloStudio UI 및 상호 작용 디자인 학습

[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) 는 HoloLens 용 최초의 Microsoft 앱 중 하나입니다. 따라서 3D UI 및 상호 작용 디자인에 대 한 새로운 모범 사례를 만들어야 했습니다. 이를 위해 많은 사용자 테스트, 프로토타입, 평가판 및 오류가 발생 했습니다.

이러한 종류의 조사를 수행 하기 위해 모든 사람이 리소스를가지고 있는 것은 아닙니다. Holographic 디자이너 인 Cus Ghaly는 HoloStudio 개발 중에 학습 한 세 가지 사항을 공유 하 여 HoloLens 앱에 대 한 UI 및 상호 작용 디자인을 개발 했습니다.

## <a name="watch-the-video"></a>비디오 시청

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a>문제 #1: 사용자가 만들기를 진행 하지 않으려고 합니다.

원래 HoloStudio에서 실제 워크 벤치를 사각형으로 설계 했습니다. 문제는 사용자가 책상에 앉아 있거나 컴퓨터 앞에서 작업 하는 경우에도 계속 유지 되도록 하는 환경 수명 이라는 것입니다. 따라서 워크 벤치를 전환 하 고 모든 측면에서 3D 만들기를 탐색 하지 않습니다.

![HoloStudio에서 워크 벤치의 사각형 디자인은 사용자가 이동 하 여 모든 측면에서의 생성을 확인 하는 것을 dissuaded.](images/rectangular-workbench-500px.jpg)

워크 벤치 라운드를 만들기 위한 통찰력을 제공 하 여 사용자가 반드시 사용할 수 있는 "front" 또는 명확한 장소가 없었습니다. 이를 테스트할 때 갑자기 사용자가 자신의 만들기를 직접 탐색 하 고 탐색을 시작 했습니다.

![순환 워크 벤치 디자인은 사용자가 자신의 생성을 중심으로 모든 방법을 안내할 것을 권장 합니다.](images/circular-workbench-500px.jpg)

**배운 내용**

사용자에 게 익숙한 기능에 대해 항상 생각해 야 합니다. 실제 공간을 활용 하는 것은 HoloLens의 쿨 기능이 며 다른 장치에서 수행할 수 없는 것입니다.

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a>문제 #2: 모달 대화 상자는 때때로 holographic 프레임 외부에 있습니다.

경우에 따라 사용자가 앱에서 주의가 필요한 다른 방향을 찾을 수 있습니다. PC에서는 대화 상자를 팝업 할 수 있지만, 3D 환경에서 다른 사용자에 게이 작업을 수행 하는 경우 대화 상자에서 대화 상자를 가져오는 것 처럼 보일 수 있습니다. 메시지를 읽는 데 필요한 메시지는 이러한 해당 메시지를 가져오는 것이 좋습니다. 게임을 재생 하는 경우에는 유용 하지만, 작업을 위해 설계 된 도구에서는 이상적이 지 않습니다.

몇 가지 다른 작업을 시도한 후에는 대화에 대 한 "생각 거품형" 시스템을 사용 하 여 사용자가 응용 프로그램에서 주의가 필요한 곳에 합의 수 있는 tendrils를 추가 했습니다. 또한 사용자가 이동할 위치를 알 수 있도록 방향성이 있음을 암시 하는 tendrils 펄스를 만들었습니다.

!["생각 거품형" 시스템에는 응용 프로그램에서 주의가 필요한 곳에 대 한 사용자의 지침을 제공 하는 펄스 된 tendrils 포함 되어 있습니다.](images/thought-bubble-500px.jpg)

**배운 내용**

3D에서 사용자에 게 주의 해야 하는 항목을 알려 주는 것이 훨씬 더 어렵습니다. [공간 음향](spatial-sound.md), 빛 광선 또는 생각 거품과 같은 주목 이사회를 사용 하면 사용자가 필요한 위치로 이어질 수 있습니다.

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a>문제 #3: 경우에 따라 UI는 다른 holograms 차단 될 수 있습니다.

사용자가 홀로그램 및 연결 된 UI 컨트롤과 상호 작용 하려고 하지만 다른 홀로그램 앞에 있기 때문에 뷰에서 차단 되는 경우가 있습니다. HoloStudio를 개발 하는 동안이에 대 한 솔루션에 대 한 평가판 및 오류를 사용 했습니다.

![홀로그램 사이에 다른 홀로그램가 있는 경우 HoloLens에 연결 된 UI 컨트롤이 차단 될 수 있습니다.](images/ui-blocked-500px.jpg)

사용자가 차단 될 수 없도록 UI 컨트롤을 사용자에 게 더 가깝게 이동 하려고 했지만 사용자가 멀리 떨어져 있었던 홀로그램을 동시에 확인 하는 동안 사용자가 가까이 있는 컨트롤을 확인 하는 것이 좋습니다. 그러나 사용자에 게 가장 가까운 홀로그램 앞에서 컨트롤을 이동한 경우에는 영향을 주는 홀로그램에서 분리 된 것 처럼 보입니다.

마지막으로 UI 컨트롤의 고스팅을 종료 하 고 사용자와 연결 된 홀로그램와 동일한 거리에 배치 하므로 둘 다 연결 됩니다. 이렇게 하면 사용자가 컨트롤과 상호 작용할 수 있습니다.

![솔루션: UI 컨트롤을 고스트 했습니다 .이 컨트롤은 컨트롤과 상호 작용 하 여 영향을 받은 홀로그램에 연결 된 것으로 느껴질 수 있습니다.](images/ghosting-ui-500px.jpg)

**배운 내용**

사용자는 UI 컨트롤이 차단 된 경우에도 쉽게 액세스할 수 있어야 합니다. 따라서 사용자가 실제 세계 어디에 있든 관계 없이 작업을 완료할 수 있도록 하는 방법을 holograms.

## <a name="about-the-author"></a>작성자 정보

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><b>Ghaly cus</b><br>Holographic 디자이너@Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>참조
* [Instinctual 상호 작용](interaction-fundamentals.md)

 
