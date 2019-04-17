---
title: 상호 작용 기본 사항
description: HoloLens에서 환경을 구축한 대로 (첫 번째 gen) HoloLens 2 및 몰입 형 헤드셋을 공유 하는 데 유용 알게 몇 가지 작업을 기록 시작 했습니다.
author: rwinj
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: 혼합 현실을, 상호 작용 디자인
ms.openlocfilehash: d594126529b6314a4706f8b6b6af856058c3280a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597550"
---
# <a name="interaction-fundamentals"></a>상호 작용 기본 사항

HoloLens 및 몰입 형 헤드셋 환경을 구축한으로 공유 하는 데 유용 알게 몇 가지 작업을 기록 시작 했습니다. 이러한 혼합된 현실 상호 작용 디자인을 위한 기본적인 빌딩 블록으로 간주 합니다.

## <a name="device-support"></a>장치 지원

에 적용 되는 상호 작용 디자인 문서를 사용할 수 있는 장치 유형 또는 형식의 개요는 다음과 같습니다.
<br>

<table>

<th>
<tr>

<td style="width:150px;"><strong>입력</strong></td>
<td style="width:150px; text-align: center;"><a href="hololens-hardware-details.md"><strong>HoloLens (첫 번째 범용)</strong></a></td>
<td style="width:150px; text-align: center;"><strong>HoloLens 2</strong></td>
<td style="width:150px; text-align: center;"><a href="immersive-headset-hardware-details.md"><strong>몰입 형 헤드셋</strong></a></td>
</tr>
</th>
 
<tr>
<td> <a href="gestures.md">명확 하 고 실습</a></td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td><td></td>

</tr><tr>
<td> <a href="gaze-targeting.md">모니터링 대상</a></td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td><td style="text-align: center;"></td>
</tr><tr>
<td> <a href="gaze-targeting.md">대상으로 응시</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="gestures.md">제스처</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> <a href="voice-design.md">음성 디자인</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> 게임 패드</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr>
<tr>
<td> <a href="motion-controllers.md">컨트롤러 동작</a></td><td></td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>

</tr>
<th>
<tr>
<td style="width:150px;"><strong>인식 및 공간 기능</strong></td>
<td style="width:150px; text-align: center;"><a href="hololens-hardware-details.md"><strong>HoloLens (첫 번째 범용)</strong></a></td>
<td style="width:150px; text-align: center;"><strong>HoloLens 2</strong></td>
<td style="width:150px; text-align: center;"><a href="immersive-headset-hardware-details.md"><strong>몰입 형 헤드셋</strong></a></td>
</tr>
</th>
<tr>

<td> <a href="spatial-sound-design.md">공간 적절 하 게 디자인</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-mapping-design.md">공간 매핑 디자인</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> <a href="hologram.md">홀로그램</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr>

</table>

## <a name="the-user-is-the-camera"></a>사용자가 카메라

![사용자가 카메라](images/useriscamera-640px.jpg)

항상 해당 실제 및 가상 환경에 대 한 이동 사용자 관점에 대 한 디자인에 대 한 생각 합니다.

**몇 가지 질문**
* 이 사용자 앉아 안락, 준비, 이거나 환경을 사용 하는 동안 walking?
* 다른 위치로 콘텐츠 조정 하는 방법
* 사용자 조정할 수 있습니까?
* 사용자 앱을 사용 하 여 편리 하 게 되나요?

**모범 사례**
* 사용자가 카메라와 움직임을 제어 합니다. 이러한 드라이브 수 있습니다.
* 사실상 사용자를 전송 해야 할 경우 vestibular 뜨거움 관련 된 문제에 중요할 수 있습니다.
* 사용 하 여 더 짧은 애니메이션
* 왼쪽/오른쪽 아래로에서 애니메이션을 적용 하거나 Z 대신 페이드
* 타이밍 속도가 저하
* 사용자가 백그라운드에서 전 세계를 참조 하도록 허용

**피해 야 할 사항**
* 카메라 흔들기 하지 않거나 3DOF에 의도적으로 잠글 (만 방향, 변환이 수행 되지 않음) 불편 한 사용자가 수행할 수 있습니다.
* 갑작스러운 이동 되지 있습니다. 사용자의 콘텐츠를 표시 해야 할 경우 느린와 원활 하 게 쪽으로 이동 하 최대 편안 함에 대 한 합니다. 사용자가 반응 하에서 제공 하는 큰 메뉴 하 게 됩니다.
* 가속화 또는 사용자의 카메라를 설정 하지 마세요. 사용자는 가속 (angular 및 변환)에 민감합니다.

## <a name="leverage-the-users-perspective"></a>사용자의 관점을 활용 합니다.

사용자는 몰입 형 및 holographic 장치에 표시를 통해 혼합된 현실 세계를 참조 하십시오. HoloLens,이 표시 라고 합니다 [holographic 프레임](holographic-frame.md)합니다.

2D 개발에 자주 콘텐츠 및 설정을 쉽게 액세스할 수 있도록 화면 모서리에 배치할 수 있습니다. 그러나 holographic 앱에서 사용자 보기의 모서리에 있는 콘텐츠 않을 편리 하 게 액세스 합니다. 이 경우 holographic 프레임의 가운데에는 콘텐츠에 대 한 프라임 위치입니다.

사용자가 즉시 보기 이외의 개체나 중요 한 이벤트를 찾으려면의 안내를 해야 합니다. 화살표, 연한 내역, 문자 헤드 이동, 사고 거품, 포인터, 공간 소리 및 음성 안내 앱의 중요 한 내용을 안내 하는 데 사용할 수 있습니다.

사용자의 편안 하 게 화면 잠금 콘텐츠 하지 하는 것이 좋습니다. 보기 콘텐츠를 유지 하는 경우 전 세계에 놓고 "tag-along" 시작 메뉴와 같은 콘텐츠를 확인 합니다. 사용자 관점 함께 끌어오는 콘텐츠 환경에서 자연스럽 게 느낄 됩니다.

![프레임의 가장자리에 도달 하면 시작 메뉴가 따릅니다 사용자 보기](images/tagalong-1000px.jpg)<br>
*프레임의 가장자리에 도달 하면 시작 메뉴가 따릅니다 사용자 보기*

HoloLens에서 홀로그램 잘려 가져오려면 하지 되므로 holographic 프레임 내에 맞을 때 실제 생각 합니다. 사용자는 프레임 내에서 홀로그램의 범위를 확인 하기 위해 이동 합니다. HoloLens, 사용자의 뷰 내에 주 작업에 집중을 유지 하 여 UI를 간소화 하기 위해 중요 한 것입니다. 몰입 형 헤드셋 장치 보기 필드 내에서 영구적 가상 세계의 효과 유지 하기 위해 중요 한 것입니다.

## <a name="user-comfort"></a>사용자 편안 함

최대 되도록 [쾌적](comfort.md) 표시 머리에 만들고 사람은 3D 도형 및 자연에서 개체의 상대 위치를 해석 하는 방법을 비슷한 방식으로 콘텐츠를 제공 하는 디자이너 및 개발자를 위한 중요 한 것 전 세계입니다. 실제 관점에서 arm의 목 fatiguing 동작이 필요 하지 않은 콘텐츠를 설계 해야 이기도 합니다.

HoloLens 또는 몰입 형 헤드셋 개발 인지 모두 눈에 대 한 시각적 개체를 렌더링 하는 것이 중요 합니다. 한 눈에 헤 즈 업 디스플레이 렌더링만 어려울 수 있습니다 인터페이스 이해 사용자의 눈을 뇌 uneasiness 발생 하기.

## <a name="share-your-experience"></a>사용자 경험 공유

사용 하 여 [혼합 현실 캡처](mixed-reality-capture.md), 사진 또는 비디오 언제 든 지 해당 환경의 사용자 캡처할 수 있습니다. 스냅숏 또는 비디오를 권장 하려는 앱의 환경을 고려해 야 합니다.

## <a name="leverage-basic-ui-elements-of-the-windows-mixed-reality-home"></a>Windows Mixed Reality 홈의 기본 UI 요소를 활용 합니다.

Windows PC 환경을 바탕 화면에서 시작 하는 것 처럼 Windows Mixed Reality 홈으로 시작 합니다. 합니다 [Windows Mixed Reality 홈](navigating-the-windows-mixed-reality-home.md) 타고 이해 하 고 3D 위치를 탐색 하는 능력을 활용 합니다. HoloLens를 사용 하 여 집에 실제 공간이 없습니다. 몰입 형 헤드셋을 사용 하 여 집 가상 위치입니다.

집 여기서 사용할지 시작 메뉴를 열고 앱 및 콘텐츠를 배치할 이기도 합니다. 혼합된 현실 콘텐츠로 홈을 입력 하 고 동시에 여러 앱을 사용 하 여 멀티 태스크 수 있습니다. 장치를 다시 시작 하는 경우에 집에 배치 작업을 유지 합니다.

## <a name="see-also"></a>참조
* [대상으로 응시](gaze-targeting.md)
* [제스처](gestures.md)
* [음성 디자인](voice-design.md)
* [컨트롤러 동작](motion-controllers.md)
* [공간 적절 하 게 디자인](spatial-sound-design.md)
* [공간 매핑 디자인](spatial-mapping-design.md)
* [Comfort](comfort.md)
* [Windows Mixed Reality 홈 탐색](navigating-the-windows-mixed-reality-home.md)
