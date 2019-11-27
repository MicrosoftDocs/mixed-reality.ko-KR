---
title: 혼합 현실이란?
description: 이 문서에서는 혼합 현실를 정의 하 고, 간단한 AR 및 VR 장치 뿐만 아니라 Microsoft HoloLens 및 Windows mixed reality 몰입 형 헤드셋과 같은 Windows Mixed Reality 장치와 혼합 현실 스펙트럼을 함께 보여 줍니다.
author: BrandonBray
ms.author: branbray
ms.date: 03/21/2018
ms.topic: article
keywords: mixed reality, holographic, ar, vr, mr, xr, 확대 현실, 가상 현실, 설명
ms.openlocfilehash: 65588902565ee0c5a1710f823311ccdecc23230e
ms.sourcegitcommit: 83698638b93c5ba77b3ffc399f1706482539f27b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74539549"
---
# <a name="what-is-mixed-reality"></a>혼합 현실이란?

![HoloLens로 가리키기 및 커밋 2](images/02_MixedRealitySlashMixedReality.png)

혼합 현실은 실제 세계와 디지털 세계를 혼합한 결과입니다. 혼합 현실은 사용자, 컴퓨터 및 환경 상호 작용의 차세대 진화이며, 지금까지의 상상력으로 제한되었던 가능성을 열어줍니다. 컴퓨터 비전, 그래픽 처리 기능, 표시 기술 및 입력 시스템의 고급 기능을 통해 가능 합니다. *혼합 현실* 이라는 용어는 원래 Paul Milgram 및 Fumio Kishino "[혼합 현실 시각적 표시의 분류](https://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)"에 의해 1994 용지에 도입 되었습니다. 이 문서에서는 *virtuality continuum*의 개념을 소개 하 고에 적용 되는 분류의 분류가 표시 되는 방식에 중점을 두었습니다. 그 이후에는 혼합 현실의 응용 프로그램이 표시를 초과 합니다. 또한 환경 입력, 공간 음향 및 위치도 포함 됩니다.

혼합 현실 스펙트럼을 ![](images/MixedRealitySpectrum-worlds.jpg)<br>
*혼합 현실은 실제 세계를 디지털 세계와 혼합 한 결과입니다.*

<br>

---

## <a name="environmental-input-and-perception"></a>환경 입력 및 인식

지난 몇 년간의 사용자와 컴퓨터 입력 간의 관계를 잘 탐색 했습니다. *사용자 컴퓨터 상호 작용* 또는 HCI 라고도 하는 널리 연구 된 분야도 있습니다. 사용자 입력은 키보드, 마우스, 터치, 잉크, 음성 및 심지어 Kinect 골격 추적을 비롯 한 다양 한 방법을 통해 수행 됩니다.

센서 및 처리의 발전은 환경에서 컴퓨터 입력의 새로운 영역으로 증가 하는 것입니다. 컴퓨터와 환경 간의 상호 작용은 효과적으로 환경적을 이해 하거나 *인식*합니다. 따라서 환경 정보를 표시 하는 Windows의 API 이름을 [인식 api](https://docs.microsoft.com/uwp/api/Windows.Perception)라고 합니다. 환경 입력은 세계의 개인 위치 (예: [헤드 추적](coordinate-systems.md)), 표면 및 경계 (예: [공간 매핑](spatial-mapping.md) 및 [장면 이해](scene-understanding.md)), 주변 조명, 환경 소리, 개체 인식 등의 작업을 캡처합니다. 및 위치.

<br>



:::row:::
    :::column:::
        이제 세 가지 모든**컴퓨터 처리, 인간 입력 및 환경 입력**을 조합 하 여 진정한 혼합 현실 환경을 만들 수 있는 기회를 설정 합니다. 실제 세계의 이동은 디지털 세계의 움직임으로 변환 될 수 있습니다. 실제 세계의 경계는 디지털 세계의 게임 플레이와 같은 응용 프로그램 환경에 영향을 줄 수 있습니다. 환경 입력을 사용 하지 않으면 실제 및 디지털 현실 사이에서 환경을 혼합할 수 없습니다.<br>
        <br>
        *이미지: 컴퓨터, 사람 및 환경 간의 상호 작용입니다.*
    :::column-end:::
        :::column:::
       ![컴퓨터, 사람 및 환경 간의 상호 작용을 보여 주는 벤 다이어그램](images/mixed-reality-venn-diagram-300px.png)<br> 
    :::column-end:::
:::row-end:::

<br>

---


## <a name="the-mixed-reality-spectrum"></a>혼합 현실 스펙트럼

혼합 현실는 물리적 및 디지털 세계를 혼합 하므로 이러한 두 가지 현실은 virtuality continuum 이라는 스펙트럼의 극좌표 형 끝을 정의 합니다. 간단히 하기 위해이를 *혼합 현실 스펙트럼*이라고 합니다. 왼쪽에는 사람이 존재 하는 실제 현실이 있습니다. 오른쪽에는 해당 디지털 현실이 있습니다.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/_xpI0JosYUk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### <a name="augmented-vs-virtual-reality"></a>확대 및 가상 현실

현재 출시 된 대부분의 휴대폰에는 환경에 대 한 이해가 거의 없습니다. 따라서 제공 되는 환경은 물리적인 현실와 디지털 현실를 혼합할 수 없습니다. 실제 세계의 비디오 스트림에 대해 그래픽이 확장 되는 환경이 확대 된 *현실*입니다. 디지털 환경을 제공 하기 위해 보기를 려 하는 환경은 *가상 현실*입니다. 여기에서 볼 수 있듯이 이러한 두 극단 사이에 사용 되는 환경은 *혼합 현실*입니다.
* 실제 세계부터 홀로그램 등의 디지털 개체를 실제로 배치 하는 것 처럼 배치 합니다.
* 실제 세계부터 다른 사람 (아바타)의 디지털 표현은 메모를 나갈 때가 있는 위치를 보여 줍니다. 즉, 서로 다른 시점에 비동기 공동 작업을 나타내는 환경이 있습니다.
* 디지털 세계부터 벽, 가구 등 실제 세계의 물리적 경계는 사용자가 물리적 개체를 피하는 데 도움이 되는 환경 내에서 디지털로 표시 됩니다.


<br>

혼합 현실 스펙트럼을 ![](images/MixedRealitySpectrum.jpg)<br>
*혼합 현실 스펙트럼*

<br>

현재 제공 되는 대부분의 확대 현실 및 가상 현실 제품은이 스펙트럼의 매우 작은 부분을 나타냅니다. 그러나이는 더 큰 혼합 현실 스펙트럼의 하위 집합입니다. Windows 10은 전체 스펙트럼을 염두에 두고 작성 되었으며 실제 세계의 사람들, 장소 및 사물에 대 한 디지털 표현을 혼합할 수 있습니다.




## <a name="devices-and-experiences"></a>장치 및 환경


Windows Mixed Reality 환경을 제공 하는 두 가지 주요 유형의 장치가 있습니다.
1. **Holographic 장치.** 이러한 특징은 실제 환경에서 디지털 콘텐츠를 실제 환경으로 저장 하는 장치 기능에 따라 구분 됩니다.
2. **모던 장치.** 이러한 특징은 실제 세계를 숨기고 디지털 환경으로 대체 하는 것을 의미 하는 "현재 상태"를 만드는 장치의 기능을 의미 합니다.

<table>
<tr>
<th width="20%"> 특징</th><th width="40%"> Holographic 장치</th><th width="40%"> 몰입 형 장치</th>
</tr><tr>
<td> 장치 예</td><td> Microsoft HoloLens<br /> <img alt="Microsoft HoloLens image" width="300" height="169" src="images/mshololens-hero1-whitbg-rgb-300px.png" /></td><td> Acer Windows Mixed Reality Development Edition<br /> <img alt="Acer Windows Mixed Reality Development Edition image" width="300" height="169" src="images/acer-windows-mixed-reality-development-edition-headset-300px.jpg" /></td>
</tr><tr>
<td> Display</td><td> <i>참조-표시</i> 사용자가 헤드셋을 입고 있는 동안 물리적 환경을 볼 수 있습니다.</td><td> <i>불투명 표시.</i> 헤드셋을 입고 있는 동안 물리적 환경을 차단 합니다.</td>
</tr><tr>
<td> 방식</td><td> 회전 및 변환과 같이 완전 한 6 도씩 자유롭게 이동 합니다.</td><td> 회전 및 변환과 같이 완전 한 6 도씩 자유롭게 이동 합니다.</td>
</tr>
</table>

장치가 별도의 PC (USB 케이블 또는 Wi-fi를 통해)에 연결 되어 있든, 아니면 테더 링 된 (작업할)에 연결 되어 있는지에 관계 없이 장치를 holographic 또는 몰입 형으로 표시할지 여부는 반영 되지 않습니다. 즉, 이동성을 개선 하는 기능이 더 나은 환경을 holographic 하 고, 및 몰입 형 장치는 테더 링 된 또는 작업할 일 수 있습니다.


기술적으로는 혼합 현실 환경을 사용할 수 있습니다. 오늘날 전체 스펙트럼에서 환경을 실행할 수 있는 장치가 없습니다. 그러나 Windows 10은 장치 제조업체와 개발자 모두에 게 공통적인 혼합 현실 플랫폼을 제공 합니다. 현재 장치는 혼합 현실 스펙트럼 내에서 특정 범위를 지원할 수 있습니다. 시간이 지남에 따라 새 장치는 해당 범위를 확장 합니다. 나중에 holographic 장치는 더 몰입이 되 고 몰입 형 장치는 더 holographic 됩니다.

<br>

혼합 현실 스펙트럼에서 장치 유형을 ![](images/MixedRealitySpectrum-devices.jpg)<br>
*혼합 현실 스펙트럼에 장치가 있는 경우*

응용 프로그램 또는 게임 개발자가 만들려는 환경 유형을 생각 하는 것이 가장 좋습니다. 이 환경은 일반적으로 스펙트럼에서 특정 지점이 나 파트를 대상으로 합니다. 그런 다음 개발자는 대상으로 지정할 장치의 기능을 고려해 야 합니다. 예를 들어 실제 세계를 사용 하는 환경은 HoloLens에서 가장 잘 실행 됩니다.
* **왼쪽 (거의 실제 현실)을 향해** 사용자는 실제 환경에 그대로 유지 되며 해당 환경을 떠난 것으로 생각 하지 않습니다.
* **중간 (완전히 혼합 된 현실).** 이러한 환경은 진정한 세계와 디지털 세계를 혼합 합니다. 영화 [Jumanji](https://en.wikipedia.org/wiki/Jumanji) 을 본 적이 있는 시청자는 스토리가 있는 집의 물리적 구조가 정글 환경과 혼합 된 방식을 조정할 수 있습니다.
* **오른쪽 (근거리 디지털 현실)** 사용자는 완전 한 디지털 환경을 경험 하 고 그 주변의 물리적 환경에서 어떤 일이 발생 하는지는 인식 하지 못합니다.


## <a name="see-also"></a>참고 항목

* [홀로그램이란?](hologram.md)
* [혼합 현실의 기본 사항 이해](index.md#understand-the-basics)
* [만들기 및 프로토타입 만들기 시작](design.md)
* [도구 및 아키텍처 알아보기](development.md)

