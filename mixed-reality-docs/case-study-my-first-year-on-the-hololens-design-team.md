---
title: 사례 연구-HoloLens 디자인 팀의 첫 해
description: 2016 년 1 월에 HoloLens 디자인 팀에 참여 한 경우 2D flatland에서 3D 세계로의 경험을 시작 합니다.
author: designnomad
ms.author: haejinl
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, 디자인, 편집, 개인
ms.openlocfilehash: 050645e6096559a4f37b033e5ddfdc5444039c08
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873951"
---
# <a name="case-study---my-first-year-on-the-hololens-design-team"></a>사례 연구-HoloLens 디자인 팀의 첫 해

2016 년 1 월에 HoloLens 디자인 팀에 참여 한 경우 2D flatland에서 3D 세계로의 경험을 시작 합니다. 팀에 합류 하기 전에 3D 디자인의 경험을 거의 없었습니다. 첫 번째 단계가 윤 인 경우를 제외 하 고는 단일 단계로 시작 하는 천 마일의 여행에 대 한 중국어 삶과 같습니다.

![2D에서 3D로 가져오기](images/2D_to_3D-800px.gif)<br>
*2D에서 3D로 가져오기*

> *"자동차를 구동 하는 방법을 몰라도 드라이버의 사용자로 바로 이동할 수 있습니다. 과도 하 게 집중 하 고 있습니다. "*<br>
> -Hae Jin Lee

지난 해에는 언제 든 지 기술 및 지식을 획득 했지만 계속 배워야 합니다. 여기서는 2D에서 3D 상호 작용 디자이너로의 전환을 문서화 하는 비디오 자습서를 사용 하 여 4 개의 관찰을 작성 했습니다. 경험을 바탕으로 다른 디자이너가 영감를 3D로 전환할 것을 바랍니다.

## <a name="good-bye-frame-hello-spatial--diegetic-ui"></a>안녕하세요. Hello 공간/diegetic UI

포스터, 잡지, websites 또는 앱 화면을 디자인할 때마다 정의 된 프레임 (일반적으로 사각형)은 모든 문제에 대 한 상수 였습니다. HoloLens 또는 다른 VR 장치에서이 게시물을 읽지 않는 한, 프레임 내에 안전 하 게 보호 되는 프레임 외부부터 2D 화면 *에서이* 를 확인 하 게 됩니다. 콘텐츠는 외부에 있습니다. 그러나 혼합 현실 헤드셋은 *프레임을 제거*하므로 콘텐츠 공간 내에 있으므로 내부에서 콘텐츠를 찾고 탐색 합니다.

이를 개념적으로 이해 했지만 처음부터 2D 생각을 3D 공간으로 전송 하는 실수를 했습니다. 3D 공간에는 보기 변경 (사용자의 헤드 이동 기반) 및 사용자가 편안 하 게 사용 하기 위한 요구 사항 (사용자의 속성을 기반으로 함), [사용자 편안에 대 한 요구 사항](https://www.youtube.com/watch?v=-606oZKLa_s/) (사용자의 속성을 기반으로 함) 등의 고유한 속성이 있으므로 잘 작동 하지 않습니다. 예를 들어 2D UI 디자인 공간에서 화면 모퉁이에 대 한 UI 요소 잠금은 매우 일반적인 패턴 이지만이 HUD (헤드 표시) 스타일 UI는 MR/VR 환경에서 자연스럽 게 보이지 않습니다. 사용자의 집중 교육 공간에 방해가 되며 사용자 discomfort이 발생 합니다. 제거 하는 데 방해가 되는 고 지에 대 한 성가신 먼지 파티클이 있는 것과 같습니다. 시간이 지남에 따라 3D 공간에 콘텐츠를 배치 하는 것이 보다 자연스럽 게 생각 되 고 콘텐츠가 사용자를 상대적으로 고정 된 거리 만큼 따르도록 하는 본문 잠금 동작을 추가 하는 것을 알게 되었습니다.

![본문-잠김](images/bodylockedtagalong.gif)<br>
*본문-잠김*

<br>

![세계에서 잠김](images/worldlocked.gif)<br>
*세계에서 잠김*

### <a name="fragments-an-example-of-great-diegetic-ui"></a>부분 유용한 Diegetic UI의 예

[조각](https://www.microsoft.com/p/fragments/9nblggh5ggm8), HoloLens에 대해 [Asobo Studio](http://www.asobostudio.com/) 에서 개발한 최초의 사용자 범죄 THRILLER는 멋진 Diegetic UI를 보여 줍니다. 이 게임에서 사용자는 불가사의를 해결 하려고 하는 감지 주 문자가 됩니다. 이러한 pivotal를 해결 하는 방법에 대 한 단서는 사용자의 실제 방에 블로그에도 올라와를 제공 하는 것 이며, 대부분의 경우에는 해당 개체가 아닌 가상 개체 내에 포함 되는 경우가 많습니다. 이 diegetic UI는 본문 잠금 UI 보다 검색 하기 덜 편 하므로 Asobo 팀은 가상 문자 ' 응시 방향, 소리, 조명 및 가이드 (예: 단서의 위치를 가리키는 화살표)를 비롯 한 여러 가지를 사용 하 여 사용자의 주의를 잡아 영리 합니다.

![조각-Diegetic UI 예제](images/fragments-game-example-1.jpg)<br>
*조각-Diegetic UI 예제*

### <a name="observations-about-diegetic-ui"></a>Diegetic UI에 대 한 관찰

공간 UI (본문 잠김 및 전 세계 잠김) 및 diegetic UI에는 고유한 장점과 단점이 있습니다. 디자이너가 최대한 많은 MR/VR 앱을 사용해 볼 수 있도록 하 고 다양 한 UI 위치 지정 방법에 대 한 자체 이해 및 sensibility을 개발 하는 것이 좋습니다.

## <a name="the-return-of-skeuomorphism-and-magical-interaction"></a>Skeuomorphism 및 마법 상호 작용의 반환

Skeuomorphism는 실제 개체의 모양을 모방 하는 디지털 인터페이스가 설계 업계의 지난 5 ~ 7 년 동안 "쿨" 적이 있었습니다. Apple이 iOS 7에서 플랫 설계를 제공 하는 경우 Skeuomorphism가 인터페이스 디자인 방법으로 마지막으로 중단 된 것 처럼 보입니다. 하지만 새 미디어 MR/VR 헤드셋이 시장에 도착 하 고 Skeuomorphism가 다시 반환 된 것 처럼 보입니다. : )

### <a name="job-simulator-an-example-of-skeuomorphic-vr-design"></a>작업 시뮬레이터: Skeuomorphic VR 디자인의 예

[Owlchemy Labs](https://owlchemylabs.com/) 에서 개발한 whimsical 게임 인 [작업 시뮬레이터](http://jobsimulatorgame.com/)는 skeuomorphic VR 디자인에 가장 많이 사용 되는 예제 중 하나입니다. 이 게임 내에서 로봇이 사람을 대체 하 고 다른 사람이 박물관를 방문 하 여 다음과 같은 네 가지 작업 중 하나에서 일상적인 작업을 수행 하는 것을 경험 하는 미래에 플레이어를 전송 합니다. 자동 정비공, Gourmet Chef, 매장 담당자 또는 Office 작업자입니다.

Skeuomorphism의 혜택은 명확 합니다. 이 게임 내에서 친숙 한 환경 및 개체는 새 VR 사용자에 게 더 편안 하 고 가상 공간에 표시 되는 데 도움이 됩니다. 또한 친숙 한 지식 및 동작을 개체 및 해당 하는 실제 반응 연결 하 여 제어 하는 것과 같은 느낌을 줍니다. 예를 들어 커피의 컵을 위해 사람들은 커피 컴퓨터를 탐색 하 고, 단추를 누르고, 컵 핸들을 잡고, 실제 세계에서와 같이 입로 기울입니다.

![작업 시뮬레이터](images/job-simulator.gif)<br>
*작업 시뮬레이터*

MR/VR는 여전히 미디어를 개발 하는 중 이므로 MR/VR 기술을 상세 설명 하 고 전 세계에 있는 대규모의 고객에 게 도입할 수 있도록 특정 수준의 skeuomorphism를 사용 해야 합니다. 또한 skeuomorphism 또는 현실적인 표현을 사용 하면 수술 또는 비행 시뮬레이션 같은 특정 유형의 응용 프로그램에 유용할 수 있습니다. 이러한 앱은 실제 세계에 직접 적용할 수 있는 특정 기술을 개발 하 고 구체화 하는 것이 목표 이기 때문에 시뮬레이션에 대 한 자세한 내용은 실제 세계에 가까울수록 더 많은 지식을 보유 하 고 있습니다.

Skeuomorphism는 한 가지 방법입니다. MR/VR 전 세계의 잠재력은 그 보다 훨씬 더 클 수 있으며, 개발자는 MR/VR 세계에서 고유 하 게 사용할 수 있는 새로운 affordances 인 마법 하이퍼 자연 스러운 상호 작용을 만들기 위해 노력 해야 합니다. 처음에는 사용자가 teleportation 및 omniscience를 포함 하 여 기본적인 기능을 수행할 수 있도록 일반 개체에 대 한 마법 능력을 추가 하는 것이 좋습니다.

![Doraemon의 마법의 도어 (왼쪽) 및 Ruby slippers (오른쪽)](images/doraemons-magical-door-and-ruby-slippers.jpg)<br>
*Doraemon의 마법의 도어 (왼쪽) 및 ruby slippers (오른쪽)*

### <a name="observations-about-skeuomorphism-in-vr"></a>VR의 skeuomorphism에 대 한 관찰

Doraemon의 "어디서 나 도어", Harry Potter의 Oz "Maurader의 map"에 있는 "Ruby Slippers"에서 "의 map"으로, 인기 있는 abound에서 마법 전원 fiction이 있는 일반 개체의 예 이러한 마법 개체는 실제와 환상적인 간의 연결을 시각화 하는 데 도움이 됩니다. 마법 또는 surreal 개체를 설계할 때는 기능과 엔터테인먼트 간에 균형을 맞추어야 합니다. 하려는 유혹는 새로 움의 편의를 위해 순수 하 게 놀라운 작업을 만들기 위한 것입니다.

## <a name="understanding-different-input-methods"></a>다른 입력 방법 이해

2D 미디어 용으로 설계 된 경우 입력을 위한 터치, 마우스 및 키보드 상호 작용에 집중 해야 했습니다. MR/VR 디자인 공간의 본문은 인터페이스가 되 고 사용자는 더 광범위 한 입력 방법 (음성, 응시, 제스처, [6 dof 컨트롤러](https://en.wikipedia.org/wiki/Six_degrees_of_freedom)및 가상 개체와의 직접 연결을 지 원하는 글러브 포함)을 사용할 수 있습니다.

![HoloLens에서 사용 가능한 입력](images/inputs.jpg)<br>
*HoloLens에서 사용 가능한 입력*

> *"모든 항목에 가장 적합 하 고 다른 항목에 대 한 최악의 것입니다."*<br>
> \- [요금 청구](https://www.billbuxton.com/)

예를 들어, HMD 장치에서 운영 체제 및 카메라 센서를 사용 하는 제스처 입력은 컨트롤러를 보유 하거나 sweaty 글러브를 사용 하는 사용자를 확보 하지만 자주 사용 하면 물리적 피로 (gorilla client arm)를 유발할 수 있습니다. 또한 사용자가 시야에 손을 두어야 합니다. 카메라에서 손을 볼 수 없으면 손을 사용할 수 없습니다.

음성 입력은 사용자가 명령 하나 (예: "Laika 스튜디오에서 만든 동영상 표시")를 사용 하 여 중첩 된 메뉴를 잘라낼 수 있도록 하 고, 다른 모달 (예: "Face" 명령 홀로그램 사용자가 사용자에 게이를 보고 있습니다. 그러나 음성 입력은 잡음이 있는 환경에서 제대로 작동 하지 않거나 매우 조용한 공간에서 적절 하지 않을 수 있습니다.

바로 사용할 수 있고, 정확 하 고, 사용자의 [proprioception](https://en.wikipedia.org/wiki/Proprioception)활용 하 고, 수동 햅 큐를 제공 하기 때문에, 제스처 및 음성 외에도 추적 된 컨트롤러 (예: Oculus Touch, vive 등)는 매우 인기 있는 입력 방법입니다. 그러나 이러한 이점은 완전 한 기능을 제공 하 고 전체 손가락 추적을 사용 하지 않는 것이 더 나을 수 있습니다.

![초 (왼쪽) 및 수동 (미국) (오른쪽)](images/senso-and-manus-vr.jpg)<br>
*초 (왼쪽) 및 수동 (미국) (오른쪽)*

컨트롤러 만큼 널리 사용 되는 것은 아니지만, 렉스는 MR/VR 웨이브 덕분에 다시 모멘텀을 얻을 수 있습니다. 가장 최근 인 두뇌/마인드 입력은 eeg 또는 emg 센서를 헤드셋 (예: [MindMaze VR](http://www.mindmaze.com/))에 통합 하 여 가상 환경에 대 한 인터페이스로 트랙 션을 획득 하기 시작 했습니다.

### <a name="observations-about-input-methods"></a>입력 방법에 대 한 관찰

MR/VR 시장에서 사용할 수 있는 입력 장치의 샘플입니다. 업계가 성숙 하 고 모범 사례에 동의할 때까지 계속 수가 증가 됩니다. 그때까지 디자이너는 새 입력 장치를 계속 인식 하 고 특정 프로젝트에 대 한 특정 입력 방법에서 잘 익숙한 합니다. 디자이너는 장치 강도로 재생 하는 동시에 제한 내에서 독창적인 솔루션을 검색 해야 합니다.

## <a name="sketch-the-scene-and-test-in-the-headset"></a>헤드셋에서 장면 및 테스트를 스케치 합니다.

2D에서 작업 하는 경우 주로 내용만 스케치 했습니다. 그러나 혼합 된 현실 공간에는 충분 하지 않습니다. 사용자와 가상 개체 간의 관계를 더 잘 이해 하려면 전체 장면을 스케치 해야 했습니다. 공간을 인식 하는 데 도움이 되도록 [영화 4d](https://www.maxon.net/en/products/cinema-4d/overview/) 에서 장면을 스케치 하 고 가끔 [Maya](http://www.autodesk.com/products/maya/overview/)에서 프로토타입 제작을 위한 간단한 자산을 만드는 작업을 시작 했습니다. HoloLens 팀에 참여 하기 전에 프로그램을 사용해 본 적이 없고 아직 고 했지만, 이러한 3D 프로그램을 사용 하는 것은 [셰이더](https://en.wikipedia.org/wiki/Shader) 및 [IK (역 기구학)](https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2016/ENU/Maya/files/GUID-07C3BA47-32BB-477B-B6C5-1090E5C9B81C-htm.html/)와 같은 새로운 용어에 익숙해질 수 있습니다.

**"3D의 장면을 면밀 하 게 스케치 하는 방법에 관계 없이 헤드셋의 실제 환경은 스케치와 거의 동일 하지 않습니다. 따라서 대상 헤드셋에서 장면을 테스트 하는 것이 중요 합니다. "— Hae Jin Lee**

HoloLens 프로토타입화의 경우 [혼합 현실 자습서](tutorials.md) 의 모든 자습서를 시작 하 려 합니다. 그런 다음 Microsoft에서 개발자에 게 제공 하는 [HoloToolkit](https://github.com/Microsoft/HoloToolkit-Unity/) 을 사용 하 여 holographic 응용 프로그램의 개발을 가속화 하기 시작 했습니다. 문제가 발생 하는 경우에는 [HoloLens 질문 & 답변 포럼](https://forums.hololens.com/categories/questions-and-answers/)에 질문을 게시 했습니다.

HoloLens 프로토타입에 대 한 기본적인 이해를 얻은 후에는 다른 비 coders에 대 한 다른 사용자의 프로토타입을 활용 하고자 했습니다. HoloLens를 사용 하 여 간단한 작업을 개발 하는 방법을 설명 하는 비디오 자습서를 만들었습니다. 기본 개념에 대해 간략하게 설명 하 고 HoloLens 개발에 경험이 없는 경우에도 수행할 수 있습니다.

<br>

>[!VIDEO https://www.youtube.com/embed/58612RT2CT8]
*이와 같은 프로그래머가 아닌 프로그래머를 위한 간단한 자습서를 만들었습니다.*

VR 프로토타입화의 경우 [Vr 개발자 학교](http://learn.vrdev.school/) 에서 과정을 수행 하 고 Lynda.com에서 [가상 현실에 3D 콘텐츠를 만들었습니다](https://www.lynda.com/Unreal-Engine-tutorials/3D-Content-Creation-Virtual-Reality/482055-2.html?srchtrk=index%3a1%0alinktypeid%3a2%0aq%3aVirtual+Reality+%0apage%3a1%0as%3arelevance%0asa%3atrue%0aproducttypeid%3a2/) . VR 개발자 school은 코딩에 대 한 깊이 있는 정보를 제공 하 고 L; Lynda 강좌는 VR 자산을 만드는 데 유용한 간단한 소개를 제공 했습니다.

## <a name="take-the-leap"></a>Leap 가져오기

1 년 전 까지는이 모든 것을 약간 과도 하 게 생각 합니다. 이제 100%가 될 것입니다. MR/VR는 여전히 매우 medium 이며, 실현 되기를 기다리는 많은 흥미로운 가능성이 있습니다. 아이디어를 뒤집는 것 미래를 설계 하는 데 한 가지 작은 부분을 재생할 수 있습니다. 3D 공간에 참여 하는 것이 좋습니다!

## <a name="about-the-author"></a>작성자 정보

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Hae Jin Lee" width="60" height="60" src="images/haejinlee.jpg"></td>
<td style="border-style: none"><b>Hae Jin Lee</b><br>UX 디자이너@Microsoft</td>
</tr>
</table>

 
