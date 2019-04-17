---
title: 색, 광원 및 재질
description: 혼합된 현실에 대 한 콘텐츠를 디자인 하려면 색, 조명, 및 각 환경에서 사용 되는 시각적 자산에 대 한 자료의 신중한 검토가 필요.
author: mavitazk
ms.author: pinkb
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 디자인 "," 색 "," light "," 자료
ms.openlocfilehash: 3f8ee8edfe4cbbaf8a55b3c4a9125f752823be9c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59601380"
---
# <a name="color-light-and-materials"></a>색, 광원 및 재질

혼합된 현실에 대 한 콘텐츠를 디자인 하려면 색, 조명, 및 각 환경에서 사용 되는 시각적 자산에 대 한 자료의 신중한 검토가 필요. 광원 및 재질을 사용 하 여 몰입 형 environment의 목소리를 설정 하는 등의 미적 목적 및 기능에서는 알림을 사용자에 게 임박한 동작의 놀라운 색 사용과 같은 이러한 결정 될 수 있습니다. 이러한 각 의사이 결정 기회와 환경의 대상 장치의 제약 조건에 대해 가중치가 적용 되어야 합니다.

다음은 렌더링 자산 holographic 및 몰입 형 헤드셋에서 관련 지침입니다. 이들 중 대부분은 밀접 하 게 다른 기술 영역 및 관련된 주제 목록이 수에 [참고](color,-light-and-materials.md#see-also) 이 문서의 끝에 있는 섹션.

## <a name="rendering-on-immersive-vs-holographic-devices"></a>렌더링 holographic 장치 및 몰입 형

몰입 형 헤드셋에서 렌더링 된 콘텐츠는 holographic 헤드셋에서 렌더링 된 콘텐츠를 비교할 때 다양 한 시각적으로 표시 됩니다. 몰입 형 헤드셋은 2D 화면의 원하는 만큼 일반적으로 콘텐츠를 렌더링할, RGB 색 일련의 투명 한 HoloLens 사용 하 여 같은 holographic 헤드셋 렌더링 홀로그램을 표시 합니다.

항상 야 holographic 헤드셋에서 holographic 경험을 테스트 합니다. 콘텐츠의 모양을 holographic 장치를 위해 특별히 개발 되었기 하는 경우에 보조 모니터, 스냅숏 및 spectator 보기에서와 같이 다릅니다. 홀로그램의 조명을 테스트 하 고 모든 면에서 (뿐만 아니라에서 위쪽 및 아래쪽) 관찰 장치를 사용 하 여 환경을 경비원 해야 콘텐츠 렌더링 되는 방법입니다. 테스트 해야 장치의 밝기 설정의 범위에서 이므로 모든 사용자가 기본값을 맡은 뿐만 아니라 조명 조건의 다양 한 집합을 공유할 수 있습니다.

## <a name="fundamentals-of-rendering-on-holographic-devices"></a>렌더링 holographic 장치에서의 기본 사항
* **Holographic 장치는 가산적 표시** – 실제 – 흰색에서 밝은 수준인 검정 하는 동안 밝은, 나타납니다를 추가 하 여 홀로그램 만들어집니다 투명 하 게 표시 됩니다.
* **색 영향 사용자의 환경에 따라 달라 집니다** – 사용자의 대화방에 다양 한 조명 조건이 다양 합니다. 적절 한 수준의 명확성에 도움이 되는 대비를 사용 하 여 콘텐츠를 만듭니다.
* **동적 조명 방지** – 홀로그램 holographic 환경에서 균일 하 게 켜지 지는 가장 효과적입니다. 고급, 동적 조명을 사용 하 여 모바일 셰이더 기능의 초과할 수 있습니다.

## <a name="designing-with-color"></a>색으로 디자인

가산적 표시의 특성상 특정 색 holographic 디스플레이에서 다르게 보일 수 있습니다. 일부 색은 다른 작은 취합니다도 표시 됩니다 하는 동안 조명 환경의 나타날 것입니다. 쿨 색 오목 하 게 표시를 배경으로 웜 색상 전경으로 이동 하는 동안에 경향이 있습니다. 경험에 색에 알아볼 때 이러한 요소를 고려 합니다.
* **장벽은** -는 "멋지고" 개념적으로 유사한 Adobe RGB 색의에서 HoloLens 혜택. 결과적으로, 일부 색 다른 품질 및 장치에서 표현을 나타낼 수 있습니다.
* **감마** -밝기 및 대비 렌더링 되는 이미지의 몰입 형 및 holographic 장치 간에 달라 집니다. 이러한 장치 차이 보다 밝은 색 및 그림자의 어두운 영역 수 있도록 나타나는 경우가 많습니다.
* **색 구분** -"색 나누어" 또는 "색 번짐과" 라고도 함, 색 구분 가장 자주 발생 하면 커서 등 홀로그램 이동 사용자의 시각을 사용 하 여 개체를 추적 하는 경우.
* **색 일관성** -일반적으로 홀로그램 렌더링 되는 충분히 밝은 색 일관성, 백그라운드에 관계 없이 유지 되도록 합니다. 큰 얼룩이 될 수 있습니다. 밝은, 단색의 큰 영역을 방지 합니다.
* **밝은 색을 렌더링** -흰색 매우 밝은 나타나고 꼭 필요할 때만 사용 해야 합니다. 대부분의 경우 R 235 G 235 B 235 주위 흰색을 것이 좋습니다. 큰 밝은 영역 사용자 뜨거움을 발생할 수 있습니다.

**렌더링 어두운 색**

가산적 표시의 특성상 어두운 색 투명 하 게 표시 됩니다. Solid black 개체를 실제로 다르지 표시 됩니다. 아래 참조 알파 채널입니다. 있도록 "black" 모양의 16,16,16 같은 매우 진한 회색 RGB 값을 시도 합니다.

![광범위 한 색 영역 및 일반](images/640px-widegamut.png)<br>
*광범위 한 색 영역 및 일반*

## <a name="technical-considerations"></a>기술적 고려 사항
* **별칭 지정** -앨리어스를 가변 또는 홀로그램의 기 하 도형 가장자리 실제 만나는 "계단 단계"을 고려 합니다. 높은 정밀도 사용 하 여 질감을 사용 하 여이 효과 계획 수 있습니다. 질감 매핑되고 필터링을 사용 하도록 설정 해야 합니다. 페이딩 홀로그램의 가장자리 또는 black edge 테두리 개체를 만든 질감을 추가 하는 것이 좋습니다. 가능한 경우 씬 geometry를 방지 합니다.
* **알파 채널** -여기서는 홀로그램 하지 렌더링 하는 모든 부분에 대 한 완전히 투명 알파 채널의 선택을 취소 해야 합니다. 장치에서 또는 Spectator 보기를 사용 하 여 이미지/비디오를 만들 때 visual 아티팩트에 알파 정의 되지 않은 잠재 고객을 종료 합니다.
* **부드럽게 질감** light 이므로-holographic 표시에서 가산 것이 좋습니다 종종 의도 한 시각 효과 생성 되지 않는으로 밝은, 단색의 큰 영역을 방지 합니다.

## <a name="storytelling-with-light-and-color"></a>밝은 색과 스토리텔링

Light와 색에 홀로그램 사용자의 환경 뿐만 아니라 제품 설명서에 보다 자연스럽 게 표시 되며 사용자에 대 한 도움말을 확인 수 있습니다. 홀로그램 환경에 대 한 조명 및 색에 알아볼 때 이러한 요소를 고려 합니다.
* **비네팅** -자료 어두워집니다 '비네팅' 효과 보기의 필드의 가운데에 사용자의 주의 집중 토론할 페르소나 수 있습니다. 이 효과 사용자의 게이즈 벡터에서 일부 radius에서 홀로그램의 자료를 어두워집니다. 이 역시 유효 사용자의 홀로그램 오블리크 또는 glancing 각도에서 볼 때 note 합니다.
* **강조** -색 밝기, 대비 및 조명 개체 또는 상호 작용의 지점에 주목 합니다. 더 자세히 살펴보려면 스토리텔링에 조명 메서드를 참조 하세요 [픽셀 Cinematography-컴퓨터 그래픽에 대 한 A 조명 Approach](http://media.siggraph.org/education/cgsource/Archive/ConfereceCourses/S96/course30.pdf)합니다.

![조각에서 장면에서 같습니다 스토리텔링 요소를 강조 표시할 색을 사용 합니다.](images/640px-fragments.jpg)<br>
*장면에서 여기에 표시 된 스토리텔링 요소를 강조 표시할 색 사용 [조각](https://www.microsoft.com/p/fragments/9nblggh5ggm8)합니다.*

## <a name="see-also"></a>참조
* [색 구분](hologram-stability.md#color-separation)
* [홀로그램](hologram.md)
* [Microsoft 디자인 언어-색](https://www.microsoft.com/design/color)
* [유니버설 Windows 플랫폼을 지 원하는 색](https://docs.microsoft.com/windows/uwp/style/color)
