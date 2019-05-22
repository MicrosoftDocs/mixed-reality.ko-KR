---
title: 사례 연구-3 HoloStudio UI와 상호 작용 디자인 학습
description: HoloStudio UI와 상호 작용 디자인 학습
author: rwinj
ms.author: marcghal
ms.date: 03/21/2018
ms.topic: article
keywords: 혼합 현실을 HoloStudio, HoloLens, Windows
ms.openlocfilehash: e01e2ea888398e9982b56fd95f90ef0731ec6bc2
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974824"
---
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a>사례 연구-3 HoloStudio UI와 상호 작용 디자인 학습

[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) HoloLens에 대 한 첫 번째 Microsoft 앱 중 하나 였습니다. 이 인해 UI 3D에 대 한 새 모범 사례를 만들고 상호 작용 디자인 해야 했습니다. 많은 사용자 테스트, 프로토타입 생성 및 시행 착오를 통해이 했습니다.

리소스를이이 유형의 연구를 위해 마음에 HoloStudio HoloLens 앱에 대 한 UI와 상호 작용 디자인에 대 한 개발 중 알게 우리의 수석 Holographic 디자이너 Marcus Ghaly 다음 세 가지를 공유 했습니다 하는 모든 사람이 알고 있습니다.

## <a name="watch-the-video"></a>비디오를 시청 하세요.

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a>문제 #1: 사용자가 생성 될 때까지 이동 하 고 싶지

원래 설계 했습니다 HoloStudio에서 workbench를 사각형으로 훨씬 유사 하 게 실제 환경에서. 문제는 사람들이 책상에 앉아 또는 workbench로 이동 하지 않은 컴퓨터 앞에 작업 및 모든 면에서 3D 생성을 탐색 하는 경우에 계속 유지 하도록 알려주는 환경의 수명입니다.

![HoloStudio에서 워크 벤치의 사각형 디자인 dissuaded 사용자가 이동 하 고 모든 면에서 해당 만들기를 표시 합니다.](images/rectangular-workbench-500px.jpg)

확인 했습니다. "앞면" 있도록 반올림 또는 독립 었어야 하는 위치를 지우기 workbench에 대 한 정보는 했습니다. 이 테스트를 갑자기 사용자 시작 이동 하 고 해당 만들기 자체적으로 탐색 합니다.

![순환 workbench 디자인 사용자를 만들기까지 경비원 하는 것이 좋습니다.](images/circular-workbench-500px.jpg)

**학습 한 내용을**

항상 란 사용자 편리 하 게 생각이 됩니다. 해당 물리적 공간 활용 기능은 쿨의 HoloLens 및 기타 장치를 사용 하 여 수행할 수 없습니다.

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a>문제 #2: 모달 대화 상자는 holographic 프레임

경우에 따라 앱에서 주의가 필요한 항목에서 다른 방향 사용자를 검색할 수 있습니다. PC에는 대화 상자에서 최대만 팝업 수 있지만 대화 상자는 고유한 방식으로 시작 되는 듯한 느낌 3D 환경에서 사람의 얼굴에서이 작업을 수행 합니다. 메시지를 확인 해야 할 이지만 해당 속성을 벗어나면 있습니다. 이 반응 게임을 재생 중인 이지만 작업을 위한 도구 내에서 이상적인 하는 경우에 유용 합니다.

잠시 다른 작업을 시도한 후 마지막으로 "거품형 생각 했습니다." 시스템을 사용 하 여이 대화 상자에서 확인 하 고 tendrils 사용자 응용 프로그램에서 주의가 필요한 하기 위해 수행할 수 있는 추가 합니다. 사용자 실마리가 이동 될 수 있도록 방향의 의미를 암시 하는 tendrils pulse를 만들었습니다.

!["생각 거품" 시스템 방향으로 사용자가 앱에 주의가 필요한 위치를 앞의 의미를 제공 하는 깜박이 tendrils 포함 되어 있습니다.](images/thought-bubble-500px.jpg)

**학습 한 내용을**

것에 주의 해야 하는 항목에 사용자에 게 경고를 3d에서 훨씬 어렵습니다. 같은 주의 이사를 사용 하 여 [공간 소리](spatial-sound.md)광선을 밝은, 사고 버블링 사용자 수 필요한 곳 발생할 수 있습니다.

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a>문제 #3: 경우에 따라 다른 제공 하 여 UI 차단할 수 있습니다.

사용자를 홀로그램 및 연결 된 해당 UI 컨트롤을 사용 하 여 상호 작용 하려고 하지만 앞에 다른 홀로그램 이므로 보기에서 차단 된 경우에 경우가 있습니다. HoloStudio를 개발 하는 동안이 대 한 솔루션을 시행 착오를 사용 했습니다.

![UI 컨트롤을 홀로그램와 연결 된 HoloLens 착용 사용자 간의 다른 홀로그램 있으면 차단 될 수 있습니다.](images/ui-blocked-500px.jpg)

차단 하지만 멀리 떨어져 있는 홀로그램 동시에 확인 하는 동안 근접 하는 컨트롤에서 사용자에 대 한 편리한 없다는 찾을 가져올 수 없습니다 사용자에 게 더 가깝게 UI 컨트롤을 이동 하려고 했습니다. 그러나 사용자에 게 가장 가까운 홀로그램 앞에 컨트롤을 이동, 하는 경우 영향을 줄 수 해야 홀로그램에서 분리 된 것 처럼 개입 합니다.

에서는 마지막 UI 컨트롤, 영상 끝난을 넣습니다 같은 거리에 사용자의 연결 된 홀로그램으로 모두 느낌 연결 하므로. 이 려 지 된 경우에 컨트롤과 상호 작용할 수 있습니다.

![솔루션: 컨트롤과 상호 작용을 허용 및에 영향을 주는 되었습니다 홀로그램에 연결 되어 있다고 생각 했는데 모두 UI 컨트롤을 고스팅 했습니다.](images/ghosting-ui-500px.jpg)

**학습 한 내용을**

사용자는이 차단 된 경우에 UI 컨트롤에 쉽게 액세스할 수 있으므로 사용자가 실제로 해당 홀로그램 있는 관계 없이 해당 작업을 완료할 수 있도록 하는 방법 파악 해야 합니다.

## <a name="about-the-author"></a>저자 소개

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><b>Marcus Ghaly</b><br>선임 Holographic 디자이너 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>참조
* [Instinctual 상호 작용](interaction-fundamentals.md)

 
