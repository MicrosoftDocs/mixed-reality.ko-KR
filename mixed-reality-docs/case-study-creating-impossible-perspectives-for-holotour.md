---
title: 사례 연구-HoloTour 불가능 한 큐브 뷰 만들기
description: Forgettable 되지 Microsoft HoloLens 대 한 HoloTour에서 경험 싶었습니다. 기존의 여행자 중지 하는 것 외에도 일부 "불가능 한 관점" out 예정입니다.
author: DannyAskew
ms.author: daaske
ms.date: 03/21/2018
ms.topic: article
keywords: 혼합 현실을 HoloTour, HoloLens, Windows
ms.openlocfilehash: be00df73543aa295e1e0dbe1462a888d6bb24954
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600115"
---
# <a name="case-study---creating-impossible-perspectives-for-holotour"></a>사례 연구-HoloTour 불가능 한 큐브 뷰 만들기

Forgettable 되지 Microsoft HoloLens 대 한 HoloTour에서 경험 싶었습니다. 기존의 여행자 중지 하는 것 외에도 하려고 계획할 지 일부 "불가능 한 큐브 뷰" – 아웃 분 환경에서 모든 둘러보기 불가능할 것입니다 하지만 HoloLens의 기술을 통해 거실에 직접 가져올 수 없습니다 것입니다. 이러한 환경에 대 한 콘텐츠를 만드는 표준 캡처 과정 보다 몇 가지 다른 기술이 필요 합니다.

## <a name="the-content-challenge"></a>콘텐츠 문제

HoloTour 환경에 특정 백그라운드에서-뜨거운 공기 풍선 현대의 로마 및에서 유래 되었음 로마에서 Colosseum gladiatorial 퇴치 재정의 같은-제공 하는 고유한 뷰를 다른 곳에 표시 되지 않습니다. 이러한 분은 자극 만지고 HoloTour 교육 환경의 이상을 통해 출장을 내릴 수를 위한 것입니다. 이들은 하고자 기억 하 고에 대 한 다른 사용자에 게 알려주는 흥분 분입니다. 하늘에는 카메라 rig을 차지 없습니다 것 이므로 시간 이동 마스터 아직 하지 않은 것 "불가능 한 관점" 각 특수 콘텐츠를 만드는 방법에 대 한 호출 합니다.

## <a name="behind-the-scenes"></a>백그라운드 작업

이러한 고유 분 및 필요한 것 이상의 filming 및 편집 하는 큐브 뷰를 만드는 중입니다. 엄청난 시간, 장애인 많은 다른 기술과 Hollywood 마법 약간 걸렸습니다.

### <a name="viewing-rome-from-a-hot-air-balloon"></a>뜨거운 공기 풍선에서 보기 로마

이 초기 계획 일에서 HoloTour에서 항공 뷰 할까요 알고 있었습니다. 하늘에서 로마를 사용 하면 표시 되는 대부분의 사람들이 보려는 받은 적 관점 그리고 얼마나 많이 사용 랜드마크 공간적으로 배치 됩니다. 이 직접 캡처를 시도 하는 기존 카메라 및 마이크 사용 하 여 rig 되었을 매우 어려운 하지만 다행히 필요가 없었습니다.

먼저에 이동 있는 모든 HoloTour에서 방문할 위치를 설명 하는 것이 반드시 합니다. 목표로 해야 "느낌 사실상 것"을이 가상 대상 앰비언트 이동도 전달 하는 데 필요한 실생활의 어디 든 이동 하 여 묶은, 때문입니다. 예를 들어 여행 중에 Pantheon을 방문할 때 사용자를 가장 전체 wandering 및 집합적인 단계에 표시 됩니다. 위치에서 아닌 정적 스테이징된 환경에서를 실제로 준비 하는 것 처럼 느껴질 수 있도록 백그라운드 동작 수 있습니다.

풍선 승객에 대 한 항공 보기를 만들려면 함께 작업 하였습니다 다른 팀의 로마 파노라마 항공 이미지에 액세스 하는 microsoft입니다. 이러한 이미지의 품질은 뛰어난 및 보기 뛰어난, 되었지만 해당 수정 하지 않고 백그라운드에서에서 사용 했을 때 개입 살지 않는 둘러보기의 다른 부분에 비해 동작 부족이 산만 였습니다. 


![뜨거운 공기 풍선 시장 바구니 로마도 고정 해제할 수 있습니다.](images/hotairballoon1-300px.png)<br>
*뜨거운 공기 풍선 시장 바구니 로마도 고정 해제할 수*

항공 위치를 다른 대상으로 동일한 품질 기준을 충족 확인 하기 위해 하기로 생활을 정적 사진을 변환 자동으로 이동 합니다. 첫 번째 단계에 이미지 및 합성 동작을 편집 하는 것 이었습니다. 에서는 계약을 시각 효과 artist이 도움이 됩니다. 편집 느린 유동 클라우드에서 비행 하는 새와 가끔 평면 또는 트래버스하는 skyline 헬리콥터 표시할 수행 되었습니다. 처음부터에서 다양 한 자동차 거리가 드라이브 향상 되었습니다. HoloTour의 로마 둘러보기에 수행한 경우 그럴 가능성은 사용자가이 이동 된 명시적으로 인식 합니다. 실제로 잘됐군요. 미묘한 동작 눈을 catch 하도록 설계 되지 않았습니다 하 하지만 이러한 작은 터치 하지 않고도 사용자 발견 즉시 장면에서 정적 이미지를 만들었습니다.

두 번째로 했던 장면을 볼 수 있는 유리한 지점을 제공 했습니다. 여기에 있는 실제로 경우 것 같습니다. 하므로 풍선의 3D 모델을 생성 하 고 내부에 배치 하면 단순히 midair에 부동 하는 것 처럼 느껴질 없습니다. 이 통해 더 나은 관점을 가져오려는 가장자리를 포인터로 찾아 풍선 경비원 수 있습니다. 항공 이미지를 경험 하기 자연스럽 고 재미 있는 방법으로이 사실을 알게 되었습니다.

뜨거운 공기 풍선 환경을 물류 때문 하지 못했습니다. feet 수천 로마 마우스로 가리키면 마이크에서 오디오 저희 팀에 대 한 고유한 과제 제공. 다행 스럽게도 후 프로덕션 중에 사용할 수 있는 도시 곳곳 많은 양의에서 앰비언트 오디오 캡처 했습니다. 여기서부터 캡처된에서 상대 위치에 오디오 미터를 배치 했습니다. 오디오 있습니다 된 환영 하 뜨거운 공기 풍선에 있는 다른 사용자의 관점에서 장면에 대 한 인증, 방향 soundscape를 제공 하는 경우에 먼 소리를 필터링 한 다음 않았습니다.

### <a name="time-traveling-to-ancient-rome"></a>시간 여행 하 고 대 로마

기념물 및 로마 전체 건물의 나머지는 인상적 이지만 두 천 년 해당 생성 후에 있지만 소개 될 것 같은 시간에 돌아가도록 나름의 로마에 나타난 것 처럼 이러한 구조를 참조 하는 특별 한 기회를 했습니다 알고 있었습니다.

물론 모든 비디오 영상을 또는 정적 이미지 없음)는 Colosseum의 작성 된 경우 표시 되는 상태로 따라서 해야 했던 만드는 합니다. 수; 구조에 대 한 최대 크기에 대해 알아보려면 연구를 많이 수행 해야 했습니다. 자료를 이해 하도록 작성 되었습니다.에서 아키텍처 다이어그램을 검토 하 고 기록 설명을 읽을 수 있으려면 가상를 다시 만들 수 있도록 충분 한 정보. 

![고 대 로마에서 살펴본 것 처럼 arena 바닥을 보여 주는 오버레이 사용 하 여 Colosseum의 최신 일 버려진 합니다.](images/rome-colosseum-overlay-500px.png)<br>
*고 대 로마에서 살펴본 것 처럼 arena 바닥을 보여 주는 오버레이 사용 하 여 Colosseum의 최신 일 버려진*

가장 먼저 할까요 교육 오버레이 사용 하 여 기존 투어를 개선 했습니다. HoloTour 현재 현 상태의 Colosseum 중 버려진을 방문할 때 어떻게 정교한 underground 스테이징 영역을 포함 하 여 사용 하는 동안 살펴본는 보여드리겠습니다 arena floor 변환 됩니다. 일반 소개 하는 방법을 설명 하는이 정보를 해야 할 수 있습니다 및 상상해 보세요 하려고 할 수 있습니다 하지만 HoloTour에서 볼 수 있습니다 실제로 합니다.

다음과 같은 오버레이 대 한 우리의 캡처 카메라의 관점을 일치 시키고 오버레이 이미지를 직접 만들는 아티스트 했습니다. 큐브 뷰는 모두 올바르게 정렬는 이미지를 사용 하 여 비디오를 대체 했습니다 일치 해야 합니다.

### <a name="staging-the-gladiator-fight"></a>디에 터 퇴치 준비

오버레이 하는 유용한 방법을 기록 하는 방법에 대 한 사람을 가르치는 것 이지만 가장 기대 있었습니다 무엇 된 전송 하면 다시에서 합니다. 오버레이 특정 관점에서 여전히 이미지 방금를 하지만 모델링에 전체 Colosseum 시간 이동 해야 되었으며 활성 느껴지도록 하 장면 동작에 해야 했던 위에서 설명 했 듯이 있습니다. 상당한 노력이 소요 되었습니다.

이 작업 너무 큽니다 단독으로 작업을 수행 하는 팀에 대 한 아트 팀 Whiskytree, 외부 효과 회사는 일반적으로 경험이 Hollywood 영화에 대 한 시각 효과에 작동 합니다. Whiskytree 있었습니다는 Colosseum 해당 heyday에서 다시 arena 바닥에 고정 하는 동안 구조에 설명 하 고 황제의 상자에서 디에 터 싸의 보기를 만들 수 있습니다. 관중 cheering 및 배너 손 흔드는 미묘한 실제 위치 및 이미지 뿐 아니라 다음과 같은 것으로 생각 될 수 있도록 하는 데 필요한 동작을 추가 합니다.

![Arena 바닥에서 보듯이 다시 만들어진된 Colosseum 합니다. HoloTour에서 보면 동작의 느낌을 제공 하는 breeze에서 배너 flutter 합니다.](images/recreated-colosseum-holotour-500px.png)<br>
*Arena 바닥에서 보듯이 다시 만들어진된 Colosseum 합니다. HoloTour에서 보면 동작의 느낌을 제공 하는 breeze에서 배너 flutter 합니다.*

로마 둘러보기 디에 터 퇴치를 사용 하 여 완료 됩니다. Whiskytree arena 및 비디오를 렌더링 하는 3D 크 라우드 시뮬레이션을 사용 하 여 제공 되지만 arena 현장에서의 레디에 추가 해야 합니다. 프로세스의이 부분 처럼 보이기 Hollywood 비디오 제작 프로젝트 보다는 인큐베이션 게임 개발에서. 팀의 멤버 대략적인 퇴치 시퀀스 아웃 매핑되고를 choreographer를 사용 하 여 만들고 다 듬 합니다. 우리의 모의 전투를 준비 하는 행위자를 고용 하 고 일부 표시 됩니다 있도록 방어를 구매 합니다. 마지막으로 녹색 화면에 대 한 전체 장면을 촬영 했습니다.

![우리의 레디 간에 지침입니다.](images/green-screen-gladiators-holotour-500px.jpg)<br>
*우리의 gladiatiors, 간에 사용 지침*

이 장면 중심이 황제의 상자에서 해당 관점에서 하는 데 필요한 모든 카메라 있음을 의미 합니다. 레디 arena 현장에서 대체 된 위치에서 촬영 했습니다 하는 경우 없습니다 있었습니다를 올바르게 복합 퇴치 시퀀스에서 나중에 설명 하겠습니다이 카메라 연산자 매우 긴 위 리프트 filming 퇴치 시퀀스에서 확인 하도록 합니다.

![올바른 큐브 뷰를 가져오는: 위 리프트에서 filming 합니다.](images/scissor-lift-holotour-500px.jpg)<br>
*오른쪽 관점을 시작 합니다: 위 리프트에서 filming*

제작 후에 레디 arena floor 합성 하 고 관점 올바르지 되었지만 문제가 하나 남아: 녹색 화면의 레디의 그림자에 합성 프로세스의 일부로 제거 되었습니다. 그림자 없이를 확인할 수는 레디 공중에서 부동 된 같은 합니다. 다행 스럽게도 Whiskytree가 바로 이러한 종류의 문제를 해결 하는 데 유용 되며 다시이 장면에 그림자를 추가 하려면 약간의 기술 없 사용. 결과에 표시 되는 투어 지금입니다.

## <a name="about-the-authors"></a>저자 소개

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="David Haley" width="60" height="60" src="images/haley.png" /></td>
<td style="border:0" width="408"> <b>David Haley</b> HoloTour 작업에서 가능한 죽이기 보다 카메라 rig 및 비디오 재생에 대 한 자세한 학습 하는 선임 개발자가 있습니다.</td>

<td style="border:0" width="60px"> <img alt="Jason Syltebo" width="60" height="60" src="images/syltebo.png" /></td>
<td style="border:0" width="408"> <b>Jason Syltebo</b> 를 방문 하면 시간에 돌아가도록 하는 경우에 모든 대상의 soundscape 경험할 수 있는지 수행한는 오디오 디자이너입니다.</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Danny Askew" width="60" height="60" src="images/askew.png" /></td>
<td style="border:0" width="408"> <b>Danny Askew</b> 로마 과정이 되었습니다 최대한으로 완벽 한 비디오 음악가 됩니다.</td>

<td style="border:0" width="60px"></td>
<td style="border:0" width="408"></td>
</tr>
</table>


## <a name="see-also"></a>참조
* [동영상: Microsoft HoloLens: HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)
