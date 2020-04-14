---
title: 혼합 현실이란?
description: 이 문서에서는 혼합 현실을 정의하고, 간단한 AR 및 VR 디바이스뿐만 아니라 Microsoft HoloLens 및 Windows Mixed Reality 몰입형 헤드셋과 같은 Windows Mixed Reality 디바이스와 혼합 현실 스펙트럼을 함께 보여줍니다.
author: brandonbray
ms.author: branbray
ms.date: 03/21/2018
ms.topic: article
keywords: 혼합 현실, 홀로그램, ar, vr, mr, xr, 증강 현실, 가상 현실, 설명
ms.localizationpriority: high
ms.openlocfilehash: 7b0dcbdb88f880d4c1632fae874ba6a610f023fb
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278051"
---
# <a name="what-is-mixed-reality"></a>혼합 현실이란?

![HoloLens 2를 착용하고 손으로 가리키고 커밋](images/02_MixedRealitySlashMixedReality.png)

혼합 현실은 실제 세계와 디지털 세계를 혼합한 결과입니다. 혼합 현실은 사용자, 컴퓨터 및 환경 상호 작용의 차세대 진화이며, 지금까지의 상상력으로 제한되었던 가능성을 열어줍니다. 컴퓨터 비전, 그래픽 처리 성능, 디스플레이 기술 및 입력 시스템의 발전 덕분에 가능해진 것입니다. *혼합 현실*이라는 용어는 Paul Milgram 및 Fumio Kishino의 1994년 논문 "[A Taxonomy of Mixed Reality Visual Displays](https://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)"에 처음 등장했습니다. 이 논문에서는 *가상 연속성*의 개념을 소개하고 분류학의 분류법을 디스플레이에 응용하는 방법을 중점적으로 설명했습니다. 그 이후로 혼합 현실은 디스플레이 외에 다른 영역에도 응용되었습니다. 여기에는 환경 입력, 입체 음향 및 위치가 포함됩니다.

![혼합 현실 스펙트럼](images/mixedrealityspectrum-worlds.png)<br>
*이미지: 혼합 현실은 실제 세계와 디지털 세계를 혼합한 결과입니다.*

<br>

---

## <a name="environmental-input-and-perception"></a>환경 입력 및 인식

지난 몇 년간 인간과 컴퓨터 입력의 관계에 대한 심층 탐구가 이루어졌습니다. 또한 *인간-컴퓨터 상호 작용* 또는 HCI라고 하는 원칙도 폭넓게 연구되고 있습니다. 사용자 입력은 키보드, 마우스, 터치, 잉크, 음성은 물론 Kinect 골격 추적까지 다양한 방법을 통해 수행됩니다.

센서 및 처리 기술의 발전 덕분에 환경에서 새로운 컴퓨터 입력 영역이 탄생하고 있습니다. 컴퓨터와 환경 간의 상호 작용은 실질적으로 환경 이해 또는 *인식*입니다. 따라서 환경 정보를 표시하는 Windows의 API 이름을 [인식 API](https://docs.microsoft.com/uwp/api/Windows.Perception)라고 합니다. 환경 입력은 사람의 위치(예: [머리 추적](coordinate-systems.md)), 표면 및 경계(예: [공간 매핑](spatial-mapping.md) 및 [장면 이해](scene-understanding.md)), 주변 조명, 환경 소리, 개체 인식 및 위치 등을 캡처합니다.

<br>

![컴퓨터, 인간 및 환경 간의 상호 작용을 보여주는 벤 다이어그램](images/mixed-reality-venn-diagram-300px.png)<br> 
*이미지: 컴퓨터, 인간 및 환경 간의 상호 작용*

<br>

현재 **컴퓨터 처리, 사용자 입력 및 환경 입력**이라는 세 가지 조합은 진정한 혼합 현실 환경을 만들 수 있는 기회를 제공합니다. 실제 세계에서의 움직임은 디지털 세계에서의 움직임으로 변환될 수 있습니다. 실제 세계의 경계는 디지털 세계의 게임 플레이와 같은 애플리케이션 환경에 영향을 줄 수 있습니다. 환경 입력이 없으면 실제 현실과 디지털 현실이 혼합될 수 없습니다.<br>

<br>

---


## <a name="the-mixed-reality-spectrum"></a>혼합 현실 스펙트럼

혼합 현실은 실제 세계와 디지털 세계를 혼합하므로 이러한 두 가지 현실은 가상 연속성이라는 스펙트럼의 양극단을 정의합니다. 간단히 말해, 이를 *혼합 현실 스펙트럼*이라고 합니다. 왼쪽에는 사람이 존재하는 실제 현실이 있고 오른쪽에는 해당하는 디지털 현실이 있습니다.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/_xpI0JosYUk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### <a name="augmented-vs-virtual-reality"></a>증강 현실과 가상 현실 비교

현재 시중에 나와 있는 대부분의 휴대폰에는 환경 이해 기능이 거의 없거나 아예 없습니다. 따라서 이러한 휴대폰이 제공하는 환경은 실제 현실과 디지털 현실을 혼합할 수 없습니다. 실제 세계의 비디오 스트림에 그래픽을 오버레이하는 환경은 *증강 현실*입니다. 사용자의 시야를 가리고 디지털 환경을 제공하는 환경은 *가상 현실*입니다. 아시다시피 이러한 두 극단 사이에 구현되는 환경은 *혼합 현실*입니다.
* 실제 세계로 시작하고 홀로그램 등의 디지털 개체를 실제로 있는 것처럼 배치
* 실제 세계로 시작하고 다른 사람(아바타)을 디지털로 표현하여 메모를 남길 때 서 있던 위치를 보여줍니다. 즉, 서로 다른 시점의 비동기 협업을 나타내는 환경입니다.
* 디지털 세계로 시작하고 사용자가 실제 개체를 피할 수 있도록 벽, 가구 등 실제 세계의 물리적 경계가 환경에 디지털 방식으로 표시됩니다.


<br>

![혼합 현실 스펙트럼](images/mixedrealityspectrum.png)<br>
*이미지: 혼합 현실 스펙트럼*

<br>

현재 사용 가능한 대부분의 증강 현실 및 가상 현실 제품은 이 스펙트럼의 극히 일부분을 나타냅니다. 그러나 이는 더 큰 혼합 현실 스펙트럼의 일부입니다. Windows 10은 전체 스펙트럼을 염두에 두고 제작되었으며 실제 세계의 사람, 장소 및 사물의 디지털 표현을 혼합할 수 있습니다.




## <a name="devices-and-experiences"></a>디바이스 및 환경


Windows Mixed Reality 환경을 제공하는 두 가지 주요 디바이스가 있습니다.
1. **홀로그램 디바이스.** 디지털 콘텐츠를 실제 환경에 정말로 있는 것처럼 배치하는 기능이 있는 디바이스입니다.
2. **몰입형 디바이스.** 실제 세계를 숨기고 디지털 환경으로 바꾸어서 "현재 상태"를 만드는 기능이 있는 디바이스입니다.

<table>
<tr>
<th width="30%"> 특징</th><th width="35%"> 홀로그램 디바이스</th><th width="35%"> 몰입형 디바이스</th>
</tr><tr>
<td><strong>디바이스 예</strong></td><td> Microsoft HoloLens<br><br> <img alt="Microsoft HoloLens 2 image" width="300" height="169" src="images/HoloLens2.jpg" /></td><td> Samsung HMD Odyssey+<br><br> <img alt="Samsung HMD Odyssey+ image" width="300" height="169" src="images/Samsung-HMD-Odyssey.jpg" /></td>
</tr><tr>
<td><strong>디스플레이</strong></td><td> 시스루 디스플레이. 사용자가 헤드셋을 착용하고 있는 동안 실제 환경을 볼 수 있습니다.</td><td> 불투명 디스플레이. 사용자가 헤드셋을 착용하고 있는 동안 실제 환경을 가립니다.</td>
</tr><tr>
<td><strong>운동</strong></td><td> 회전 및 변환 모두 완전한 6 자유도 운동.</td><td> 회전 및 변환 모두 완전한 6 자유도 운동.</td>
</tr>
</table>



디바이스가 USB 케이블 또는 Wi-Fi를 통해 별도의 PC에 연결 또는 테더링되어 있는지, 아니면 테더링되지 않고 독립적으로 작동하는지에 따라 홀로그램 디바이스와 몰입형 디바이스가 결정되는 것은 아닙니다. 물론 이동성을 개선하는 기능은 더 나은 환경을 가져다 주며, 홀로그램 디바이스와 몰입형 디바이스는 모두 테더링 또는 테더링 해제가 가능합니다.


기술의 발전 덕분에 혼합 현실 환경이 탄생했습니다. 현재 전체 스펙트럼의 환경을 실행할 수 있는 디바이스는 없습니다. 그러나 Windows 10은 디바이스 제조업체와 개발자 모두에게 공통적인 혼합 현실 플랫폼을 제공합니다. 현재 디바이스는 혼합 현실 스펙트럼 내 특정 범위를 지원할 수 있습니다. 앞으로 새 디바이스가 해당 범위를 확장할 것입니다. 향후 홀로그램 디바이스는 더 많은 몰입감을, 몰입형 디바이스는 더 많은 홀로그램을 제공할 것입니다.

<br>

![혼합 현실 스펙트럼의 디바이스 유형](images/Final_WhatIsMixedReality07.png)<br>
*이미지: 디바이스의 혼합 현실 스펙트럼 내 위치*

애플리케이션 또는 게임 개발자는 어떤 종류의 환경을 만들지 생각하는 것이 가장 좋습니다. 이 환경은 일반적으로 이 스펙트럼의 특정 지점이나 부분을 대상으로 합니다. 그런 다음, 개발자는 대상 디바이스의 기능을 고려해야 합니다. 예를 들어 실제 세계에 의존하는 환경은 HoloLens에서 가장 잘 실행됩니다.
* **왼쪽 방향(실제 현실에 가까움).** 사용자가 실제 환경에 그대로 있으며 해당 환경을 떠났다는 생각이 들게 하지 않습니다.
* **중간(완전한 혼합 현실).** 실제 세계와 디지털 세계를 혼합한 환경입니다. [쥬만지](https://en.wikipedia.org/wiki/Jumanji)라는 영화를 본 시청자는 이야기가 시작된 집의 실제 구조가 정글 환경과 어떻게 조화를 이뤘는지 납득할 수 있습니다.
* **오른쪽 방향(디지털 현실에 가까움).** 사용자는 완전한 디지털 환경을 경험하며 그 주변의 실제 환경에서 어떤 일이 발생하는지는 인식하지 못합니다.


## <a name="see-also"></a>참고 항목

* [홀로그램이란?](hologram.md)
* [혼합 현실의 기본 사항 이해](index.md#understand-the-basics)
* [생성 및 프로토타입 제작 시작](design.md)
* [도구 및 아키텍처 알아보기](development.md)

