---
title: 색, 조명 및 재질
description: 혼합 현실용 콘텐츠를 디자인하려면 환경에서 사용되는 시각적 자산 각각에 대한 색, 조명 및 재질을 신중하게 고려해야 합니다.
author: mavitazk
ms.author: pinkb
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 디자인, 색, 조명, 재질
ms.openlocfilehash: c49d88c2bb53c07adcb77e8dbb0e3cd77e1e78ae
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436411"
---
# <a name="color-light-and-materials"></a>색, 조명 및 재질

혼합 현실용 콘텐츠를 디자인하려면 환경에서 사용되는 시각적 자산 각각에 대한 색, 조명 및 재질을 신중하게 고려해야 합니다. 이러한 결정은 가볍고 자료를 사용 하 여 몰입 형 환경의 톤을 설정 하는 것과 같이 미적 목적을 위한 것 이며, 인상적인 색을 사용 하 여 사용자에 게 임박한 작업을 경고할 수 있습니다. 이러한 각 결정은 사용자 환경의 대상 장치에 대 한 기회 및 제약 조건과 비교 하 여 평가 해야 합니다.

다음은 몰입 형 및 holographic 헤드셋에서 자산을 렌더링 하는 방법에 대 한 지침입니다. 이 중 상당수는 다른 기술 영역에 밀접 하 게 연결 되어 있으며 관련 된 주제 목록은이 문서의 끝에 있는 [참고](color,-light-and-materials.md#see-also) 항목 섹션에서 찾을 수 있습니다.

## <a name="rendering-on-immersive-vs-holographic-devices"></a>몰입 형 및 holographic 장치에서 렌더링

모던 헤드셋에서 렌더링 된 콘텐츠는 holographic 헤드셋에서 렌더링 된 콘텐츠와 비교 하 여 시각적으로 다르게 표시 됩니다. 모던 헤드셋은 일반적으로 2D 화면에서 기대한 대로 콘텐츠를 렌더링 하는 반면, holographic 헤드셋과 같은 헤드셋은 색 순차를 사용 하 고, 참조는 RGB 디스플레이를 사용 하 여 holograms를 렌더링 합니다.

항상 holographic 헤드셋에서 holographic 환경을 테스트 하는 데 시간이 걸립니다. Holographic 장치용으로 특별히 빌드된 경우에도 콘텐츠의 모양은 보조 모니터, 스냅숏 및 spectator 보기에 표시 됩니다. 장치를 사용 하 여 경험을 holograms 하 고, 모든 측면 (위 및 아래)에서 콘텐츠를 렌더링 하는 방법을 테스트 합니다. 모든 사용자가 가정 하는 기본값을 공유 하 고 다양 한 조명 조건 집합을 공유 하는 것은 아니므로 장치에서 밝기 설정의 범위를 테스트 해야 합니다.

## <a name="fundamentals-of-rendering-on-holographic-devices"></a>Holographic 장치에서 렌더링의 기본 사항
* **Holographic 장치에는 추가 디스플레이** – Holograms는 실제 세계의 빛에 조명을 추가 하 여 생성 됩니다. 흰색은 밝은 색으로 표시 되 고 검정은 투명 하 게 표시 됩니다.
* **색 영향은 사용자의 환경에 따라 달라 집니다** . 사용자 방에는 다양 한 조명 조건이 있습니다. 명확 하 게 이해 하려면 적절 한 대비 수준으로 콘텐츠를 만듭니다.
* **동적 조명 방지** – holographic 환경에서 균일 하 게 lit Holograms 가장 효율적입니다. 고급 동적 조명을 사용 하면 모바일 장치의 기능을 초과할 가능성이 높습니다. 동적 조명이 필요한 경우 [Mixed Reality Toolkit 표준 셰이더](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md)를 사용 하는 것이 좋습니다. 

## <a name="designing-with-color"></a>색으로 디자인

가산 표시의 특성으로 인해 특정 색은 holographic 디스플레이에서 다르게 나타날 수 있습니다. 일부 색은 조명 환경에서 팝 되는 반면 다른 색은 약간의 수준으로 표시 됩니다. 쿨 색은 배경으로 recede, 웜 색은 전경으로 이동 하는 경향이 있습니다. 사용자 환경에서 색을 탐색할 때 다음 요소를 고려 합니다.
* **영역** -HoloLens는 Adobe RGB와 개념적으로 유사한 색의 "넓은 색 영역"을 활용 합니다. 따라서 일부 색은 장치에서 다양 한 품질 및 표현을 나타낼 수 있습니다.
* **감마** -렌더링 된 이미지의 밝기와 대비는 몰입 형 장치와 holographic 장치 간에 차이가 있습니다. 이러한 장치 차이점은 종종 색 및 그림자의 어두운 영역을 더 밝게 하거나 밝게 하는 것 처럼 보입니다.
* "Color 분할" 또는 "color fringing" 라고도 하는 **색** 구분은 사용자가 눈에 관계 없이 개체를 추적할 때 커서를 포함 하 여 holograms (커서 포함)를 이동 하는 경우 가장 일반적으로 발생 합니다.
* **색 균일성** -일반적으로 holograms는 배경에 관계 없이 색 균일성을 유지할 수 있도록 밝은 색으로 렌더링 됩니다. 많은 영역이 blotchy 될 수 있습니다. 밝은 단색의 넓은 영역을 사용 하지 마십시오.
* **렌더링 밝은 색** -흰색은 매우 밝은 색으로 나타나며 거의 사용 되지 않습니다. 대부분의 경우 R 235 G 235 B 235를 중심으로 하는 흰색 값을 고려 합니다. 밝은 영역이 크면 사용자 discomfort 발생할 수 있습니다.

**어두운 색 렌더링**

가산적 표시의 특성으로 인해 진한 색이 투명 하 게 표시 됩니다. 순수한 검은색 개체는 실제 환경과는 다른 것 처럼 보입니다. 아래 알파 채널을 참조 하세요. "검은색"의 모양을 지정 하려면 16, 16, 16과 같은 매우 진한 회색 RGB 값을 사용해 보세요.

![일반 색 영역 및 넓은 색 영역](images/640px-widegamut.png)<br>
*표준 색 및 와이드 색 영역 비교*

## <a name="technical-considerations"></a>기술 고려 사항
* **앨리어싱** -홀로그램의 기 하 도형 가장자리가 실제 세계를 충족 하는 앨리어싱, 가변 또는 "계단 단계"로 간에. 높은 디테일으로 질감을 사용 하면 이러한 효과를 악화 수 있습니다. 질감이 매핑되고 필터링이 설정 되어 있어야 합니다. Holograms의 가장자리를 페이드 인 하거나 개체 주위에 검정색 가장자리 테두리를 만드는 질감을 추가 하는 것이 좋습니다. 가능 하면 씬 기 하 도형을 피합니다.
* **알파 채널** -홀로그램을 렌더링 하지 않는 모든 파트에 대해 완전히 투명 하 게 하려면 알파 채널을 지워야 합니다. 장치 또는 Spectator 보기에서 이미지/비디오를 가져오는 경우 알파를 정의 되지 않은 상태로 두면 시각적 아티팩트가 표시 되지 않습니다.
* **질감 부드럽게** -조명이 holographic 디스플레이에 추가 되기 때문에 일반적으로 의도 한 시각적 효과를 생성 하지 않으므로 밝은 단색의 넓은 영역을 방지 하는 것이 가장 좋습니다.

## <a name="storytelling-with-light-and-color"></a>밝은 색과 색이 있는 스토리텔링

가볍고 색을 사용 하면 사용자의 환경에서 holograms를 보다 자연스럽 게 표시 하 고 사용자에 대 한 지침과 도움을 제공할 수 있습니다. Holographic 환경을 위해 조명 및 색을 탐색할 때 다음 요소를 고려 합니다.

:::row:::
    :::column:::
* **Vignetting** -자료를 어둡게 하는 ' vignette ' 효과를 사용 하면 보기 필드의 중심에 사용자의 주의를 집중할 수 있습니다. 이 효과는 사용자의 응시 벡터의 일부 반경에서 홀로그램의 재질을 어둡게 합니다. 이는 사용자의 뷰가 오블리크 또는 glancing 각도에서 holograms 때에도 적용 됩니다.<br>
* 색, 밝기 및 조명을 대비 하 여 개체 또는 상호 작용 지점의 **강조** 그리기 스토리텔링의 조명 방법에 대 한 자세한 내용은 [픽셀 Cinematography-컴퓨터 그래픽의 조명 방법](https://media.siggraph.org/education/cgsource/Archive/ConfereceCourses/S96/course30.pdf)을 참조 하세요.<br>
        <br>
        *이미지: 스토리텔링 요소에 대해 강조 표시 하기 위해 색을 사용 합니다. [조각](https://www.microsoft.com/p/fragments/9nblggh5ggm8)에서 장면에 표시 됩니다.*
    :::column-end:::
        :::column:::
        ![조각의 장면에서 여기에 표시 된 스토리텔링 요소에 대 한 강조를 표시 하는 색을 사용 합니다.](images/640px-fragments.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

## <a name="see-also"></a>참고 항목
* [색 구분](hologram-stability.md#color-separation)
* [Holograms](hologram.md)
* [Microsoft 디자인 언어 색](https://www.microsoft.com/design/color)
* [유니버설 Windows 플랫폼 색](https://docs.microsoft.com/windows/uwp/style/color)
