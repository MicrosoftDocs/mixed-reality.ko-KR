---
title: 혼합 현실은 무엇입니까?
description: 이 문서는 혼합된 현실을 정의 하 고 Microsoft HoloLens 및 Windows Mixed Reality 몰입 형 헤드셋와 같은 Windows Mixed Reality 장치 뿐만 아니라 간단한 AR 및 VR 장치, 혼합된 현실 스펙트럼을 따라 배치 하는 방법을 보여 줍니다.
author: BrandonBray
ms.author: branbray
ms.date: 03/21/2018
ms.topic: article
keywords: 혼합된 현실 등 holographic, ar, vr, mr, xr 하이, 증강된 현실, 가상 현실, 설명
ms.openlocfilehash: fbac8176b36cf28673dd9633cc059e5856a50296
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326309"
---
# <a name="what-is-mixed-reality"></a>혼합 현실은 무엇입니까?

혼합된 현실에 디지털 세계와 실제 혼합의 결과입니다. 혼합된 현실 사용자, 컴퓨터 및 환경 상호 작용의 차기 혁신 대상 이며 이전 까지는 우리의 imaginations 있었습니다 하는 가능성의 잠금을 해제 합니다. 가능한 computer vision, 그래픽 처리 능력, 디스플레이 기술 및 입력된 시스템에서 향상 된 기능으로 구성 됩니다. 용어 *혼합 현실을* Paul Milgram 및 Fumio Kishino 1994 문서의 원래 도입 "[혼합의 분류를 실제로 시각적 표시](http://etclab.mie.utoronto.ca/people/paul_dir/IEICE94/ieice.html)." 해당 문서에는 개념이 도입 되었습니다.는 *virtuality 연속선*, 분류에 적용 하는 분류에 표시 하는 방법에 집중 하 고. 그 이후로 혼합된 현실의 응용 프로그램 표시를 넘어섭니다. 환경 입력, 소리 공간 및 위치에도 포함 됩니다.

## <a name="environmental-input-and-perception"></a>환경 입력 및 인식

![컴퓨터, 사용자 환경 간의 상호 작용을 표시 하는 벤 다이어그램](images/mixed-reality-venn-diagram-300px.png)<br> 

지난 수십 통해 사람과 입력 하는 컴퓨터 간의 관계에도 탐색 합니다. 라고 하는 광범위 하 게 연구 분야에 있어도 *휴먼 컴퓨터 간 상호 작용* 또는 HCI 합니다. 다양 한 키보드, 마우스, 터치, 잉크, 음성 및 Kinect 골격 추적도 포함 하는 수단을 통해 사용자 입력이 발생 합니다.

발달 센서 및 처리에 환경에서 컴퓨터 입력의 새 영역에 증가 제공 됩니다. 컴퓨터 및 환경 간의 상호 작용은 효과적으로 환경 이해 하거나 *perception*합니다. 따라서 환경 정보를 표시 하는 Windows API 이름을 호출 되는 [perception Api](https://docs.microsoft.com/uwp/api/Windows.Perception)합니다. 환경 입력 캡처 등에서 전 세계 사용자의 위치 (예: [헤드 추적](coordinate-systems.md)), 화면 및 경계 (예: [공간 매핑](spatial-mapping.md) 및 [공간이해](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)), 주변 조명, 소리 환경, 개체 인식 및 위치입니다.

이제 처리 하는 모든 세-컴퓨터의 조합, 사용자 입력 및 입력 환경-설정 true 혼합된 현실 환경을 만들 수 있습니다. 실제 세계를 통해 이동 디지털 세계에서 이동에 변환할 수 있습니다. 실제에서 경계 디지털 세계에서 게임 플레이 같은 응용 프로그램 환경을 변경할 수 있습니다. 환경 입력 없이 환경을 물리적 환경과 디지털 현실 사이의 blend 수 없습니다.

## <a name="the-mixed-reality-spectrum"></a>혼합된 현실 스펙트럼

물리적 환경과 디지털 환경을 혼합 하는 혼합된 현실에 있으므로 이러한 두 현실을 virtuality 연속성 이라고 가깝습니다 극좌표 형 end를 정의 합니다. 편의상,이 참조 합니다 *혼합된 현실 스펙트럼*합니다. 왼쪽에 있는 다음과 같은 방법으로는 존재 we, 사람과; 실제 실제로 했습니다. 오른쪽에 있는 해당 디지털 실제로 했습니다.

<br>

>[!VIDEO https://www.youtube.com/embed/_xpI0JosYUk]

시장에서 대부분의 휴대폰 현재 기능이 거의 없는 환경 이해. 따라서 제공 하는 환경 간에 물리적 환경과 디지털 현실을 혼합할 수 없습니다. 비디오 스트림의 실제 그래픽을 오버레이 하는 환경이 됩니다 *현실 보강*합니다. 디지털 환경을 제공 하기 위해 뷰 채워집니다 경험 *가상 현실*합니다. 이러한 두 가지 극단적인 간에 사용 되는 환경은 알 수 있듯이 *혼합 현실을*:
* 실제로 있는 것 처럼를 홀로그램 등 디지털 개체를 배치할 실제 세계를 사용 하 여 시작 합니다.
* 실제 세계 다른 사람의-디지털 표현과 아바타-정보를 유지 하는 경우 준비 된 해당 위치를 보여 줍니다. 즉, 환경을 시간상에서 다른 지점에서 비동기 공동 작업을 나타냅니다.
* 실제 개체를 방지 하는 사용자가 환경 내에서 벽 및 가구와 같은 실제 세계에서 물리적 경계 디지털 표시 디지털 세계를 시작 합니다.

![혼합된 현실 스펙트럼](images/mixed-reality-spectrum-550px.png)

증강된 현실 가장 및 사용할 수 있는 가상 현실 제품 지금이 스펙트럼의 매우 작은 부분을 나타냅니다. 그러나 이러한는 더 큰 혼합된 현실 스펙트럼의 하위 집합입니다. Windows 10을 염두에 전체 스펙트럼을 사용 하 여 작성 되 고 사람, 장소 및 실제 작업의 디지털 표현을 혼합 수 있습니다.

![혼합된 현실 스펙트럼에 장치 유형](images/mixed-reality-spectrum-device-types-550px.png)

Windows Mixed Reality 환경을 제공 하는 장치의 두 가지 주요 유형 가지
1. **Holographic 장치입니다.** 이러한 장치의 실제로 있는 것 처럼 실제 환경에서 디지털 콘텐츠를 배치할 수에 따라 구분 됩니다.
2. **몰입 형 장치입니다.** 이러한 "상태"-실제 세계를 숨기고 디지털 환경으로 바꿔의 의미를 만들려면 장치의 기능으로 구분 됩니다.

<table>
<tr>
<th width="20%"> 특징</th><th width="40%"> Holographic 장치</th><th width="40%"> 몰입 형 장치</th>
</tr><tr>
<td> 예제 장치</td><td> Microsoft HoloLens<br /> <img alt="Microsoft HoloLens image" width="300" height="169" src="images/mshololens-hero1-whitbg-rgb-300px.png" /></td><td> Acer Windows 혼합 현실 Development Edition<br /> <img alt="Acer Windows Mixed Reality Development Edition image" width="300" height="169" src="images/acer-windows-mixed-reality-development-edition-headset-300px.jpg" /></td>
</tr><tr>
<td> 표시</td><td> <i>투명 한 표시 합니다.</i> 사용자를 헤드셋 착용 하는 동안 물리적 환경 참조 수 있습니다.</td><td> <i>불투명 하 게 표시 합니다.</i> 헤드셋 착용 하는 동안 물리적 환경을 차단 합니다.</td>
</tr><tr>
<td> 이동</td><td> 전체 6도 자유롭게 이동, 회전 및 변환 합니다.</td><td> 전체 6도 자유롭게 이동, 회전 및 변환 합니다.</td>
</tr>
</table>

참고, 여부 장치에 연결 되었거나 (USB 케이블 또는 Wi-fi)를 통해 별도 PC 또는 자체 포함 된 (제한 되지 않는) 않습니다 테더 링 된 장치 holographic 또는 몰입 형 인지를 반영 하지 않습니다. 물론 mobility를 개선 하는 기능이 더 나은 환경을 발생할 및 holographic 및 몰입 형 없습니다 수 테더 링 된 장치나 클라우드가.

## <a name="devices-and-experiences"></a>장치 및 환경

기술적 향상과 새로운 혼합된 현실 환경 사용 하도록 설정한 경우 장치가 없는 현재 전체 스펙트럼에서 환경을 실행할 수 있는 합니다. 그러나 Windows 10 장치 제조업체와 개발자 모두에 대 한 일반적인 혼합된 현실 플랫폼을 제공합니다. 현재 장치는 혼합된 현실 스펙트럼 내의 특정 범위를 지원할 수 있습니다. 시간이 지남에 따라 새 장치는 해당 범위를 확장 합니다. 나중에 holographic 장치 보다 몰입 형 되 고 몰입도 높은 장치 보다 holographic 됩니다.

![혼합된 현실 스펙트럼에서 장치 배치 되는 위치](images/mixed-reality-spectrum-device-placement-550px.png)

어떤 유형의 환경을 응용 프로그램을 생각 하는 것이 좋습니다 또는 게임 개발자가 만들려는 경우가 많습니다. 스펙트럼의 일부나 특정 지점 환경을 대상으로 일반적으로 합니다. 그런 다음 개발자 대상으로 하려는 장치의 기능을 고려해 야 합니다. 예를 들어, 실제 사용 하는 환경을 HoloLens에서 최상의 실행 됩니다.
* **(근처 실제 실제로) 왼쪽입니다.** 사용자가 실제 환경에서 그대로 및 해당 환경 남았음 생각 하려고 하지 않습니다.
* **중간 (완벽 하 게 혼합된 현실).** 이러한 경험을이 통해 실제 세계와 디지털 세계 혼합 됩니다. 보는 사람에 게 동영상 살펴본 [Jumanji](https://en.wikipedia.org/wiki/Jumanji) 정글 환경을 사용 하 여 스토리 발생 하 여 집의 물리적 구조를 혼합 하는 방법을 조정할 수 있습니다.
* **포함 (near 디지털 실제로) 권한입니다.** 사용자는 완전히 디지털 환경 환경과 이들을 실제 환경에서 발생 하는 상황 인식 하지 않습니다.


## <a name="see-also"></a>참조
* [API 참조: Windows.Perception](https://docs.microsoft.com/uwp/api/Windows.Perception)
* [API 참조: Windows.Perception.Spatial](https://docs.microsoft.com/uwp/api/Windows.Perception.Spatial)
* [API 참조: Windows.Perception.Spatial.Surfaces](https://docs.microsoft.com/uwp/api/Windows.Perception.Spatial.Surfaces)
