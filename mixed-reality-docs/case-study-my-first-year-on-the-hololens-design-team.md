---
title: 사례 연구-내 첫 번째 해에는 HoloLens 디자인 팀
description: HoloLens 디자인 팀의 2016 년 1 월에 가입 된 경우 시작 3D 세계를 2D flatland에서 내 경험 합니다.
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
# <a name="case-study---my-first-year-on-the-hololens-design-team"></a>사례 연구-내 첫 번째 해에는 HoloLens 디자인 팀

HoloLens 디자인 팀의 2016 년 1 월에 가입 된 경우 시작 3D 세계를 2D flatland에서 내 경험 합니다. 팀에 합류 하기 전에 3D 디자인에서 매우 적은 경험을 했습니다. 천 마일 여기서에서 첫 번째 단계는 도약 된 점을 제외 하 고 한 번으로 시작 하는 과정에 대 한 중국어 속담 같았습니다.

![2D에서 3D Leap 이동](images/2D_to_3D-800px.gif)<br>
*2D에서 3D leap 이동*

> *"느꼈습니다 자동차를 제어 하는 방법을 알 필요 없이 차원에 다른 페이지로 이동해 처럼 합니다. 많이 사용 되 었 고 장단점이, 아직 매우 집중 합니다. "*<br>
> -Hae Jin lee 공저

지난 수 년 동안 기술과 지식을 빨리 수 있습니다, 있지만 아직 배울 부분이 많지만를 선택 합니다. 여기에 필자가 작성 한 4 관찰 하는 2D에서 3D 인터랙션 디자이너로 내 전환 문서화 비디오 자습서를 사용 하 여 합니다. 필자의 경험 leap 3D 하는 데 다른 디자이너 inspire 됩니다 하는 것이 좋겠습니다.

## <a name="good-bye-frame-hello-spatial--diegetic-ui"></a>Good-bye 프레임입니다. Hello 공간 / diegetic UI

포스터, 잡지, 웹 사이트 또는 앱 화면 디자인, 때마다 (일반적으로 사각형) 정의 된 프레임 모든 문제에 대 한 상수를 했습니다. 이 게시물에는 HoloLens 또는 기타 VR 장치를 읽는 경우가 아니면 *외부에서이 살펴보면* 프레임 내에서 안전 하 게 보호 된 2D 화면을 통해. 콘텐츠는 외부에 있습니다. 단, 혼합 현실 헤드셋 *프레임을 제거*이므로 찾고 내부 스케일 아웃에서 콘텐츠를 살펴보면서 콘텐츠 공간 내 됩니다.

이 개념적으로 인식 있습니까 했지만 처음에 필자는 실수를 3D 공간으로 2D 사고를 전송 하기만 하면 됩니다. 분명 하지 않은 작동 하는 3D 공간 뷰 변경 (헤드 이동 사용자의 기준)와 같은 고유한 속성이 있으므로 잘 및 [편안 하 게 사용자에 대 한 다른 요구 사항](https://www.youtube.com/watch?v=-606oZKLa_s/) (장치와 사용 하 여 사용자의 속성에 기반 합니다. 해당). 예를 들어, 2D UI 디자인 공간에서 UI 요소는 화면 상단에 잠금 매우 일반적인 패턴 이지만이 HUD (헤드를 디스플레이) 스타일 UI MR/VR 환경을;에서 natural 있다고 생각 하지 않습니다. 사용자의 집중 교육 공간으로 인해 저하 하 고 사용자 뜨거움 발생 합니다. 제거 하려면 콜백하려는 프로그램 안경을에서 성가신 먼지 입자는 것과 같습니다. 시간이 지남에 따라 자연스럽 게 3D 공간에서 콘텐츠를 배치 하 고 고정된 된 상대 거리의 사용자가 콘텐츠 수행 하는 본문 잠긴 동작 추가 하다는 것이 배운 합니다.

![Body-locked](images/bodylockedtagalong.gif)<br>
*Body-locked*

<br>

![World-locked](images/worldlocked.gif)<br>
*World-locked*

### <a name="fragments-an-example-of-great-diegetic-ui"></a>조각: 우수한 Diegetic UI의 예

[조각을](https://www.microsoft.com/p/fragments/9nblggh5ggm8), 인칭 crime 운영 개발한 [Asobo Studio](http://www.asobostudio.com/) HoloLens 훌륭한 Diegetic UI를 보여 줍니다.에 대 한 합니다. 이 게임에서는 사용자 기본 문자를 신비 해결 하려고 하는 검색 됩니다. 이 해결 하기 위해 pivotal 단서가 사용자의 실제 방에 수행해 가져오기는 종종 가상 개체 내에서 포함 하지 않고 자체적으로 기존에 UI는 Asobo 팀 가상 문자 게이즈 방향, 소리, 빛 및 지침 (예:는 단서의 위치를 가리키는 화살표)을 포함 하 여 여러 큐를 영리 하 게 사용 되므로 본문 잠긴 UI 보다 검색 성능이 떨어지는 경향이이 diegetic 가져올 사용자의 주의 합니다.

![조각-Diegetic UI 예제](images/fragments-game-example-1.jpg)<br>
*조각-Diegetic UI 예제*

### <a name="observations-about-diegetic-ui"></a>Diegetic UI에 대 한 관찰

공간 (둘 다 본문 잠긴 및 world 잠긴) UI 및 diegetic UI에는 자체의 강점 및 약점에 있습니다. 디자이너를 위치 지정 메서드는 다양 한 UI에 대 한 자신의 이해 및 sensibility을 개발 하 고 최대한 많은 MR/VR 앱 사용해 보시기 바랍니다.

## <a name="the-return-of-skeuomorphism-and-magical-interaction"></a>Skeuomorphism 마법 상호 작용을 반환

Skeuomorphism, 실제 개체의 모양을 모방 하는 디지털 인터페이스가 되었습니다 "쿨" 디자인 업계의 최근 5 – 7 년 동안. Apple iOS 7에서에서 플랫 디자인 방법을 마지막으로 지정한, Skeuomorphism는 인터페이스 디자인 방법론으로 마지막 없어졌기 처럼 보였습니다. 하지만 그런 다음 새 미디어, MR/VR 헤드셋 시장에 도착 하 고 Skeuomorphism 다시 반환 되는 것 같습니다. : )

### <a name="job-simulator-an-example-of-skeuomorphic-vr-design"></a>작업 시뮬레이터의 경우: Skeuomorphic VR 디자인의 예

[작업 시뮬레이터](http://jobsimulatorgame.com/), 특이 게임을 개발한 [Owlchemy Labs](https://owlchemylabs.com/) skeuomorphic VR 디자인에 대 한 가장 인기 있는 예제 중 하나입니다. 이 게임 내 플레이어 여기서 로봇 사람 바꾸고 사람 방문이 찾기란 네 개의 다른 작업 중 하나에서 일상적인 작업을 수행 하려면 환경에 박물관 미래 전송 됩니다. 자동 정비공, 고급 Chef, 저장소 클럭의 또는 사무실 작업 합니다.

Skeuomorphism의 장점은 선택을 취소 합니다. 친숙 한 환경 및이 게임 내 개체 수 있도록 새 VR 더 편안 하 고 가상 공간에 있는 것으로 생각 될 합니다. 또한 개체와 해당 물리적 반응을 친숙 한 기술 및 동작을 연결 하 여 컨트롤에는 생각 하 고 있습니다. 예를 들어, 커피를 과거, 사용자 하기만 커피 머신을를 탐색, 단추를 누르거나, cup 핸들을 잡고 및 실제에서 것과 해당 입으로 기울어집니다.

![작업 시뮬레이터](images/job-simulator.gif)<br>
*작업 시뮬레이터*

MR/VR 개발 중간 여전히 이기 때문에 어느 정도의 skeuomorphism 사용 하 여 반드시 MR/VR 기술 상세 설명 하는 데 더 많은 대상 사용자는 전 세계에 도입 합니다. 또한 skeuomorphism 또는 현실적인 표현을 사용 하 여 특정 유형의 수술 또는 비행 시뮬레이션 등의 응용 프로그램에 유용할 수 있습니다. 이러한 앱의 목표를 개발 하 여 실제 환경에서 직접 적용할 수 있는 특정 기술을 구체화 이므로 가까울수록 시뮬레이션은 현실 세계에 더 양도할 수를 기술 합니다.

해당 skeuomorphism 방법이 하나만 기억 합니다. MR/VR 전 세계의 잠재력 이보다 훨씬 큽니다 및 디자이너 마법 하이퍼 자연 상호 작용 하도록 해야-MR/VR 전 세계에 고유 하 게 사용할 수 있는 새 affordances 합니다. 시작, 것이 좋습니다 마법 전원을 기본 제한적인 수행할 수 있도록 하려면 일반 개체에 추가-텔레포트 등 (전 능).

![Doraemon의 마법 도어 (왼쪽) 및 Ruby slippers(right)](images/doraemons-magical-door-and-ruby-slippers.jpg)<br>
*Doraemon의 마법 도어 (왼쪽) 및 ruby slippers(right)*

### <a name="observations-about-skeuomorphism-in-vr"></a>VR에 skeuomorphism에 대 한 관찰

"원격 도어" Doraemon, The 해리포터의 "Maurader의 맵에" Oz의 마법사에서 "Ruby Slippers"에서 마법 power 사용 하 여 일반 개체의 예로 인기 있는 공상에 많습니다. 이러한 마법 개체를 통해 실제 이란 무엇 이며 무엇이 간의 놀라운 기능 사이의 연결을 시각화할 수 있도록 합니다. 마법 또는 surreal 디자인할 때 하나의 개체 해야 한다고 기능 및 엔터테인먼트 간의 균형을 유지할 것을 염두에 두십시오. 새로 움의 이해에 대 한 순수 하 게 놀라운 일을 만들려는 유혹에 주의 하십시오.

## <a name="understanding-different-input-methods"></a>다른 입력된 방법 이해

2D 미디어에 대 한 디자인을 하는 경우 터치, 마우스 및 키보드 상호 작용에 대 한 입력에 집중 했습니다. MR/VR 디자인 영역에는 본문 인터페이스 되며 사용자는 입력된 방법의 더 광범위 한 선택 영역을 사용할 수 있습니다: 음성, 게이즈 제스처를 포함 [6 dof 컨트롤러](https://en.wikipedia.org/wiki/Six_degrees_of_freedom), gloves 더 직관적이 고 직접 연결을 허용 하 고 가상 개체입니다.

![HoloLens에서 사용 가능한 입력](images/inputs.jpg)<br>
*HoloLens에서 사용 가능한 입력*

> *"무엇 인가 최고 및 최악의 어차피 다른 용도로 모든 것이 있습니다."*<br>
> - [Bill Buxton](https://www.billbuxton.com/)

예를 들어 HMD 장치의 완전 직접 및 카메라 센서를 사용 하 여 입력 제스처에는 컨트롤러를 보유 하 고 있거나 sweaty 장갑을 착용에서 사용자가 직접 해제 하지만 자주 사용 하 여 실제 피로 (또는 gorilla arm) 발생할 수 있습니다. 사용자가 해당 바늘 시야; 내에서 유지 해야 하는 또한 카메라 바늘을 볼 수 없는 경우에 바늘을 사용할 수 없습니다.

음성 입력은 사용자가 하나의 명령 사용 하 여 중첩 된 메뉴가 통과 허용 하므로 복잡 한 작업을 트래버스 (예를 들어 "표시 수행한 Laika studio. 영화") 하 고 다른 형식을 함께 사용 하면 또한 매우 경제적인 (예를 들어, 적응 명령을 "얼굴 me"를 홀로그램 사용자를 보고 사용자 쪽으로). 그러나 음성 입력 시끄러운 환경에서 잘 작동 하지 않거나 매우 자동 공간에 적합 하지 않을 수 있습니다.

제스처 및 음성 외에도 핸드헬드 추적 컨트롤러 (예를 들어 Oculus 터치, 라고 외치 등)은 매우 인기 있는 입력된 메서드를 사용 하기 쉬운, 정확한 정보를 활용 하 여 사람들의 이므로 [proprioception](https://en.wikipedia.org/wiki/Proprioception), 수동 햅 틱 신호를 제공 합니다. 그러나 완전 제공 되어 전체 손가락 추적을 사용 하지 못하게 하는 대신 이러한 혜택이 제공 됩니다.

![Senso (왼쪽) 및 Manus VR(Right)](images/senso-and-manus-vr.jpg)<br>
*Senso (왼쪽) 및 Manus VR (오른쪽)*

컨트롤러로 인기 하지 하는 동안 gloves 점점 주목을 MR/VR wave 다시 덕분입니다. 뇌/고려 입력 EEG 또는 EMG 센서 헤드셋을 통합 하 여 가상 환경에 대 한 인터페이스로 힘듭니다 최근에 시작한 (예를 들어 [MindMaze VR](http://www.mindmaze.com/)).

### <a name="observations-about-input-methods"></a>입력된 방법에 대 한 관찰

이들은 just 샘플 MR/VR에 대 한 시장에서 사용 가능한 입력된 장치입니다. 업계 성숙 모범 사례에 동의할 때까지 증가 하 고 계속 합니다. 그때 까지는 디자이너 새 입력된 장치 파악 하 고 해당 특정 프로젝트에 대 한 특정 입력된 방법에 대해 잘 수 해야 합니다. 디자이너를 해결할 참신 한 솔루션이 장치의 장점에도 재생 하는 동안 제한 내에 대 한 확인 해야 합니다.

## <a name="sketch-the-scene-and-test-in-the-headset"></a>장면 스케치 및 헤드셋에서 테스트

2D에 사용한 I 대부분 내용만을 스케치 합니다. 단, 혼합된 현실 공간에서 아닙니다 충분 합니다. 사용자 및 가상 개체 간의 관계를 더 잘 imagine 전체 장면 아웃 스케치 했습니다. 장면 스케치 내 공간 고려를 위해 필자 [4d 시네마](https://www.maxon.net/en/products/cinema-4d/overview/) 경우에 따라 프로토타입 제작에서 간단한 자산을 만듭니다 [Maya](http://www.autodesk.com/products/maya/overview/)합니다. HoloLens 팀에 합류 하기 전에 프로그램 중 하나 사용 되지 않습니다 및 필자는 아직는 퇴근 하지만 3D 이러한 프로그램을 사용 하 여 작업 확실히 있었습니다 금방와 같은 새 용어에 익숙해 [셰이더](https://en.wikipedia.org/wiki/Shader) 고 [IK (역 운동학)](https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2016/ENU/Maya/files/GUID-07C3BA47-32BB-477B-B6C5-1090E5C9B81C-htm.html/)합니다.

**"얼마나 밀접 하 게 합니까 살펴본 3d에서 장면에 관계 없이 헤드셋에서 실제 환경에서 거의 발생 하지 않는다는 스케치 동일. 이유는 것이 중요 장면에 대상 헤드셋을 테스트 하려면 "-Hae Jin lee 공저**

제공 되는 모든 자습서 아웃 보았습니다 HoloLens 프로토타입 제작 [혼합 현실 자습서](tutorials.md) 를 시작 합니다. 사용 하 여 재생 하기 시작 하면서 [HoloToolkit.Unity](https://github.com/Microsoft/HoloToolkit-Unity/) Microsoft holographic 응용 프로그램의 개발을 가속화 하는 개발자에 게 제공 하는 합니다. 항목이 있습니까 잘 모 르 겠, 경우 질문을 게시 [HoloLens 질문 및 답변 포럼](https://forums.hololens.com/categories/questions-and-answers/)합니다.

HoloLens 프로토타입 제작의 기본적인 이해를 가져오면 다른 협조할 일 자체적으로 프로토타입에 역량을 강화 하고자 했습니다. 따라서 필자는 HoloLens를 사용 하는 간단한 발사 무기를 개발 하는 방법을 설명 하는 비디오 자습서입니다. 간단히 설명 하겠습니다 기본 개념을도 과정을 따르려면 수 있어야 HoloLens 개발 환경을 0에 있는 경우.

<br>

>[!VIDEO https://www.youtube.com/embed/58612RT2CT8]
*필자는 스스로 같은 비-프로그래머를 위한이 간단한 자습서입니다.*

VR 프로토타입 생성에 대 한 강좌를 사용해보겠습니다 [VR 개발 학교](http://learn.vrdev.school/) 했으며 [가상 현실에 대 한 3D 콘텐츠 생성](https://www.lynda.com/Unreal-Engine-tutorials/3D-Content-Creation-Virtual-Reality/482055-2.html?srchtrk=index%3a1%0alinktypeid%3a2%0aq%3aVirtual+Reality+%0apage%3a1%0as%3arelevance%0asa%3atrue%0aproducttypeid%3a2/) Lynda.com에 있습니다. VR 개발 학교 자세한 깊이 정보의 코딩 및 Lynda 과정으로 제공 me VR에 대 한 자산을 만들기에 대 한 유용한 간단한 소개를 제공 합니다.

## <a name="take-the-leap"></a>Leap 수행

1 년 전에 기분이이 모든 약간 명확해졌습니다. 이제 말할 수 있는 가치가 100%를 만들었습니다. MR/VR 매우 어린 보통은 여전히 있으며 많은 흥미로운 가능성을 현실화 될 때까지 대기할 수 있습니다. 영감 및 혜택을 누 생각 미래를 디자인 한 작은 부분을 재생할 수 없습니다. 3D 공간에 여행을 me 가입할를 바랍니다!

## <a name="about-the-author"></a>저자 소개

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Hae Jin Lee" width="60" height="60" src="images/haejinlee.jpg"></td>
<td style="border-style: none"><b>Hae Jin lee 공저</b><br>UX 디자이너 @Microsoft</td>
</tr>
</table>

 
