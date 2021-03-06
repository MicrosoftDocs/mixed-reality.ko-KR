---
title: 사례 연구-HoloTour에 대해 불가능 한 큐브 뷰 만들기
description: Microsoft HoloLens HoloTour의 경험을 unforgettable 하는 데 필요 합니다. 기존 tourist 중지 외에도 "불가능 한 큐브 뷰"를 계획 했습니다.
author: dannyaskew
ms.author: daaske
ms.date: 03/21/2018
ms.topic: article
keywords: HoloTour, HoloLens, Windows Mixed 현실
ms.openlocfilehash: f3ca07dfab1e4477039481c268e418aac9034bc5
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278171"
---
# <a name="case-study---creating-impossible-perspectives-for-holotour"></a>사례 연구-HoloTour에 대해 불가능 한 큐브 뷰 만들기

Microsoft HoloLens HoloTour의 경험을 unforgettable 하는 데 필요 합니다. 기존 tourist 중지 외에도 둘러보기에서 사용할 수 없는 "불가능 한 큐브 뷰"를 계획 했지만 HoloLens의 기술을 통해 관심 있는 방에 직접 가져갈 수 있습니다. 이러한 환경에 대 한 콘텐츠를 만들려면 표준 캡처 프로세스와는 약간 다른 기술이 필요 했습니다.

## <a name="the-content-challenge"></a>내용 챌린지

HoloTour 환경에는 다른 곳에 표시 되지 않는 고유한 보기를 제공 하는 현대적인 날 로마를 통과 하는 핫 공기 풍선이 나 고대의 로마의 Colosseum에서 gladiatorial 싸우는 등의 특정 장면이 있습니다. 이러한 순간은 흥미 하 고 amaze 하 여 교육 환경 이상의 HoloTour를 통해 여행 하는 것입니다. 사용자가 기억할 수 있는 분 이며 다른 사람들에 게 알려 드리겠습니다. 카메라를 공중으로 이동 하지 않았으므로 아직 마스터 된 시간 이동이 하지 않았습니다. 이러한 각 "불가능 한 큐브 뷰"는 콘텐츠를 만드는 특별 한 접근 방식으로 호출 됩니다.

## <a name="behind-the-scenes"></a>백그라운드 작업

이러한 고유한 시간과 큐브 뷰를 만드는 데는 단순히 filming 및 편집이 필요 합니다. 상당한 시간, 다양 한 기술이 있는 사용자, 약간의 Hollywood 마법을 사용 했습니다.

### <a name="viewing-rome-from-a-hot-air-balloon"></a>핫 공기 풍선에서 로마 보기

초기 계획을 세울 때 HoloTour에서 항공 보기를 수행 하려고 했습니다. 하늘에서 로마를 보면 대부분의 사람들이 볼 수 없고 인기 있는 랜드마크의 공간적 위치를 파악할 수 있는 큐브 뷰를 얻을 수 있습니다. 기존 카메라와 마이크 rig를 사용 하 여이를 캡처하는 것은 크게 어렵습니다. 단, 다행히 그렇게 하지 않아도 됩니다.

먼저 HoloTour에서 방문 하는 모든 위치에서 이동 하는 것을 설명 하는 것이 중요 합니다. 우리의 목표는 "정말 마음에 드 거 실 것입니다." 라는 목표를 달성 하는 것이 우리의 목표입니다. 예를 들어 여행에 대 한 정보를 방문 하면 plaza 및 congregating 전체에서 wandering 수 있습니다. 백그라운드 동작은 준비 된 정적 환경이 아닌 위치에 있는 것 처럼 느낌을 주는 데 도움이 됩니다.

항공 뷰를 만들기 위해 Microsoft에서 다른 팀과 협력 하 여 항공 파노라마 이미지에 대 한 액세스 권한을 얻을 수 있습니다. 이러한 이미지의 품질은 매우 우수 했지만, 보기를 수정 하지 않고 내부적으로 사용 하는 경우 둘러보기의 다른 부분과 비교 하 여 동작 부족을 lifeless 느낄 것입니다. 


로마를 떠 놓았을 때 핫 공기 풍선 바구니를 ![합니다.](images/hotairballoon1-300px.png)<br>
*로마를 넘는 핫 공기 풍선 바구니입니다.*

항공 위치가 다른 대상과 동일한 품질 막대를 충족 하는지 확인 하기 위해 정적 사진을 살아 있는 장면으로 변환 하기로 결정 했습니다. 첫 번째 단계는 이미지 및 복합 동작을 편집 하는 것입니다. 이를 지원 하기 위해 시각적 효과 음악가를 계약 했습니다. 편집은 클라우드 천천히 유동을 표시 하기 위해 수행 되었으며, skyline를 트래버스하는 간헐적으로 비행기 또는 헬리콥터를 표시 하기 위해 수행 되었습니다. 처음에는 거리를 구동 하기 위해 많은 자동차를 만들었습니다. HoloTour에서 로마를 둘러 보 었으 면이 움직임을 명시적으로 인식 하지 못할 가능성이 있습니다. 정말 유용 합니다. 미묘한 동작은 눈을 파악 하기 위한 것이 아니며, 이러한 작은 접촉 없이, 사람들은 장면에서 정적 이미지 였던 것을 즉시 알 수 있습니다.

두 번째는 장면을 볼 수 있는 유리한 점을 제공 했습니다. 단순히 midair에서 부동으로 표시 되는 것 처럼 보일 수 있으므로 풍선의 3D 모델을 만들고 그 안에 배치 했습니다. 이를 통해 풍선을 탐색 하 고 가장자리를 확인 하 여 더 나은 관점을 얻을 수 있습니다. 항공 이미지를 경험 하는 자연 스러운 재미 있는 방법입니다.

핫 공기 풍선 환경에는 오디오 팀에 대 한 고유한 과제가 표시 되어 있습니다. 다행히 사후 프로덕션 중에 사용할 수 있었던 모든 도시에서 많은 양의 주변 오디오 캡처가 있었습니다. 오디오 송신기가 땅에서 캡처된 위치에서 상대 위치에 배치 되었습니다. 그런 다음, 핫 air 풍선에서 사람의 riding 관점에서 발생 하는 것 처럼 오디오를 먼 소리로 필터링 하 여 장면의 인증 된 방향성 soundscape을 제공 합니다.

### <a name="time-traveling-to-ancient-rome"></a>고대의 로마로 이동 하는 시간

남아 기념물와 빌딩의 빌딩은 생성 후에는 매우 2000 년 이내에 발생 하지만, 이전에는 이전 시간으로 이동 하 여이 구조를 확인 하는 데 도움이 될 것입니다.

물론, Colosseum의 비디오 푸티지 또는 정적 이미지는 빌드 시 표시 된 것 처럼 보이지 않으므로 직접 만들어야 합니다. 최대한 많은 연구를 수행 하 여 구조에 대해 자세히 알아보세요. 에서 만든 자료를 이해 하 고, 아키텍처 다이어그램을 검토 하 고, 기록 설명을 읽고 가상 재작성을 수행할 수 있는 충분 한 정보를 얻을 수 있습니다. 

고대의 로마를 사용 하 여 아레나의 Colosseum을 보여 주는 오버레이를 사용 하 여 현대적인 일일 유적를 ![합니다.](images/rome-colosseum-overlay-500px.png)<br>
*고대의 로마를 보여 주는 오버레이가 포함 된 Colosseum의 현대 유적입니다.*

가장 먼저 할 일은 교육 오버레이의 기존 투어를 개선 하는 것 이었습니다. HoloTour는 현재 처럼 Colosseum의 유적를 방문할 때, 아레나는 정교한 지역 준비 영역을 포함 하 여 사용 중에 표시 되는 방법을 보여 주기 위해 변형 되었습니다. 이 정보에 대해서는 일반적인 둘러보기로 설명 했지만이 정보를 상상 하려고 할 수 있지만 HoloTour에서 실제로 볼 수 있습니다.

이와 같은 오버레이의 경우 아티스트는 캡처 푸티지의 관점과 일치 하 고 오버레이 이미지를 직접 만듭니다. 비디오를 이미지와 바꿀 때 모두 제대로 정렬 되도록 큐브 뷰가 일치 해야 합니다.

### <a name="staging-the-gladiator-fight"></a>글 글 전투 준비

오버레이는 사용자에 게 기록에 대해 학습 하는 데 유용 하 게 사용할 수 있는 방법 이지만 이전에는 이전에 시간을 전송 했습니다. 오버레이는 특정 관점에서 이미지 일 뿐 이지만 이동 하는 시간을 모델링 하는 데는 전체 Colosseum을 모델링 해야 하며, 위에서 설명한 대로, 장면에서 작동 하 여 활성 상태로 만들어야 합니다. 상당한 노력을 취했습니다.

이 작업은 팀에서 단독으로 작업 하기에는 너무 크기 때문에, 미술 팀은 일반적으로 Hollywood 영화에 대 한 시각적 효과에서 작동 하는 외부 효과 회사인 Whiskytree로 작업 했습니다. Whiskytree를 통해 Colosseum를 원래 대로 다시 만들어 아레나에서 발생 하는 동안 구조에 대해 가르쳐 줄 고 황제의 상자에서의 글 히 싸 보기를 만들 수 있었습니다. 응원 crowds 및 대기가 없어 배너는 이미지 뿐만 아니라 실제 위치에 따라 결정 하는 데 필요한 미묘한 동작을 추가 합니다.

아레나에서 볼 때 다시 만든 Colosseum을 ![합니다. HoloTour에서 볼 때 배너는 간단히 flutter 동작을 제공 합니다.](images/recreated-colosseum-holotour-500px.png)<br>
*아레나에서 볼 때 생성 된 Colosseum입니다. HoloTour에서 볼 때 배너는 간단히 flutter 동작을 제공 합니다.*

로마 둘러보기는 글 글 해를 위한 전투로 끝납니다. Whiskytree는 비디오로 렌더링 된 아레나 및 3D로 잘 된 시뮬레이션을 제공 했지만, 아레나의 글 글에 추가 해야 했습니다. 이 프로세스의 부분은 인큐베이션 game studio의 프로젝트 보다 Hollywood 비디오 프로덕션 처럼 보입니다. 팀의 구성원은 거친 전투 시퀀스를 매핑한 다음 choreographer으로 구체화 했습니다. Microsoft는이를 대상으로 하는 모의 전투 및 구매한 갑옷을 준비 하는 행위자를 고용 했습니다. 마지막으로 전체 장면을 녹색 화면에 filmed.

을 사용 하 여에 대 한 지침을 가져오는 것을 ![.](images/green-screen-gladiators-holotour-500px.jpg)<br>
*Gladiatiors에 대 한 지침을 가져오는 데*

이 장면에서는 모든 푸티지가 해당 관점에서 수행 되어야 하는 황제의 상자에 배치 됩니다. 아레나에서 인 글을 filmed 하는 경우, 나중에는 이동 시퀀스를 올바르게 합성할 수 없기 때문에 카메라 연산자를 매우 긴 복식 리프트에 배치 하 여 filming에 대 한 이동 순서를 살펴봅니다.

오른쪽의 원근감을 가져오는 ![: 복식 리프트에서 filming.](images/scissor-lift-holotour-500px.jpg)<br>
*오른쪽의 원근감 가져오기: 복식 리프트에서 filming*

사후 프로덕션 환경에서 글 바꿈될은 아레나의 층에는 잘 만들어졌지만 큐브 뷰는 올바르지만 한 가지 문제가 있습니다. 녹색 화면에 있는 글 글의 그림자가 합성 프로세스의 일부로 제거 되었습니다. 그림자를 사용 하지 않으면 글이 항공에서 떠 있었던 것 처럼 보입니다. 다행히 Whiskytree는 이러한 종류의 문제를 해결 하는 데 유용 하며 약간의 기술 wizardry 사용 하 여 화면에 그림자를 다시 추가 합니다. 결과는 오늘 투어에서 볼 수 있습니다.

## <a name="about-the-authors"></a>작성자 정보

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="David Haley" width="60" height="60" src="images/haley.png" /></td>
<td style="border:0" width="408"> <b>David Haley</b> 는 HoloTour에서 작업 하는 것을 고려 하 여 카메라 rig 및 비디오 재생에 대해 자세히 살펴본 선임 개발자입니다.</td>

<td style="border:0" width="60px"> <img alt="Jason Syltebo" width="60" height="60" src="images/syltebo.png" /></td>
<td style="border:0" width="408"> <b>Jason Syltebo</b> 는 나중에 다시 방문 하는 경우에도 방문 하는 모든 대상의 soundscape를 경험할 수 있도록 하는 오디오 디자이너입니다.</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Danny Askew" width="60" height="60" src="images/askew.png" /></td>
<td style="border:0" width="408"> <b>Danny Askew</b> 는 로마를 통한 이동이 가능한 한 이상 인지 한 비디오 음악가입니다.</td>

<td style="border:0" width="60px"></td>
<td style="border:0" width="408"></td>
</tr>
</table>


## <a name="see-also"></a>참고 항목
* [비디오: Microsoft HoloLens: HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)
