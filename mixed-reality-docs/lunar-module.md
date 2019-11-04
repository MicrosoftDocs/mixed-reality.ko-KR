---
title: 달착륙선
description: LunarModule은 Microsoft의 혼합 현실 디자인 랩에서 오픈 소스 샘플 앱입니다. 이 프로젝트를 사용 하 여 두 개의 지향 추적 및 Xbox 컨트롤러 입력으로 HoloLens의 기본 제스처를 확장 하 고, 표면 매핑 및 평면 찾기에 반응 하는 개체를 만들고, 간단한 메뉴 시스템을 구현 하는 방법을 배울 수 있습니다.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 샘플 앱, 디자인, HoloLens
ms.openlocfilehash: 1df2b7e9aaf92a7045aa3c378d3029cf09e085a6
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438538"
---
# <a name="lunar-module"></a>달착륙선

>[!NOTE]
>이 문서에서는 혼합 현실 앱 개발에 대 한 학습 정보 및 제안을 공유 하는 위치를 [혼합 현실 디자인 랩에서](https://github.com/Microsoft/MRDesignLabs_Unity)만든 예비 샘플에 대해 설명 합니다. 디자인 관련 문서와 코드는 새로운 검색을 수행할 때 개선 됩니다.

[음력 모듈](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule) 은 Microsoft의 혼합 현실 디자인 랩에서 오픈 소스 샘플 앱입니다. 이 프로젝트를 사용 하 여 두 개의 지향 추적 및 Xbox 컨트롤러 입력으로 HoloLens의 기본 제스처를 확장 하 고, 표면 매핑 및 평면 찾기에 반응 하는 개체를 만들고, 간단한 메뉴 시스템을 구현 하는 방법을 배울 수 있습니다. 모든 프로젝트의 구성 요소는 혼합 현실 앱 환경에서 사용할 수 있습니다.

## <a name="rethinking-classic-experiences-for-windows-mixed-reality"></a>Windows Mixed Reality의 클래식 환경 재고

높은 대기 중에는 아래에서 연상 된 아폴로 모듈의 작은 배송을 위한 작은 배송이 있습니다. Fearless 파일럿은 적절 한 방문 영역을 말합니다. 이는 단절 하지만 다행히 이전에는 여러 번 수행 되었습니다.

Atari 1979 음력 Lander](images/640px-atari-lunar-lander.png)에서 원본 인터페이스를 ![합니다.<br>
*Atari의 1979 음력 Lander 원본 인터페이스*

[음력 Lander](https://en.wikipedia.org/wiki/Lunar_Lander_(1979_video_game)) 는 플레이어가 초승달 Lander을 평평한 지형을 위한 조종사를 시도 하는 아케이드 클래식입니다. 1970 년대에 태어난 모든 사용자는 plummeting에서이 벡터 선박에 붙은 눈 들과 함께 아케이드에서 많은 시간에 소요 될 가능성이 높습니다. 플레이어는 원하는 방문 영역에 대 한 배송을 탐색 하 여 점점 더 자세한 정보를 표시 하도록 조정 합니다. 성공은 가로 및 세로 속도의 안전 임계값 내에서 시작 됨을 의미 합니다. 지점은 방문 영역 크기에 따라 승수를 사용 하 여 착륙 하는 데 걸린 시간 및 남아 있는 연료에 대해 획득 됩니다.

게임 플레이와는 별도로 게임의 아케이드 연대는 컨트롤 체계의 지속적인 혁신을 가져왔습니다. 가장 간단한 4 방향 조이스틱 및 단추 구성 (아이콘 [Pac](https://en.wikipedia.org/wiki/Pac-Man)에서 볼 수 있음)부터 후기 90 년대 및 분 00 초 (예: golf 시뮬레이터 and 레일 shooters)에서 볼 수 있는 매우 구체적이 고 복잡 한 스키마를 확인 합니다. 음력 Lander 컴퓨터에 사용 되는 입력 체계는 특히 intriguing, 즉 연석이 고 집중 교육의 두 가지 이유 때문입니다.

Atari의 음력 Lander의 아케이드 콘솔을 ![](images/atariconsole.png)<br>
*Atari의 음력 Lander 아케이드 콘솔*

Atari와 기타 많은 게임 회사에서 입력을 계속 하는 이유는 무엇 인가요?

아케이드를 통한 어린이는 자연스럽 게 최신의 flasintrigued est 컴퓨터를 통해 자연스럽 게 발생 합니다. 하지만 음력 Lander는 novel 입력 정비공를 제공 합니다.

음력 Lander는 운송지 왼쪽과 오른쪽 및 **위한 것 레버** 를 회전 하는 두 가지 단추를 사용 하 여 배송이 생성 하는 위한 것의 양을 제어 합니다. 이 레버는 일반 조이스틱이 제공할 수 없는 특정 수준의 finesse를 사용자에 게 제공 합니다. 또한 현대 aviation routine cockpits에 공통적인 구성 요소 이기도 합니다. Atari를 사용 하는 것은 음력 Lander에서 사용자를 컨퍼런스 하는 것이 사실입니다. 이 개념을 **tactile 집중 교육**이라고 합니다.

Tactile 집중 교육는 반복적인 작업을 수행할 수 있는 토대로 피드백의 경험입니다. 이 경우 눈에 표시 되는 제한 레버 및 회전을 조정 하는 반복적인 작업을 통해 플레이어를 초승달의 표면에 연결 하는 작업에 연결할 수 있습니다. 이 개념은 "flow"의 심리학 개념에 연결 될 수 있습니다. 사용자가 과제와 보상의 적절 한 조합이 있는 작업에 완전히 흡수 되거나 보다 간단 하 게 배치 되는 경우 "영역에" 있습니다.

혼합 현실에서 가장 두드러진 형식의 집중 교육는 공간 집중 교육입니다. 혼합 현실의 전체 지점은 이러한 디지털 개체가 실제 세계에 믿는 것 하는 것입니다. Microsoft는 환경에서 synthesizing holograms, 전체 환경 및 환경에서 공간적으로 사용 하 고 있습니다. 이는 Atari가 음력 Lander의 tactile 집중 교육를 사용 하는 것 처럼 microsoft 환경에서 다른 유형의 집중 교육을 계속 사용할 수 있다는 의미는 아닙니다.

## <a name="designing-with-immersion"></a>집중 교육를 사용 하 여 디자인

Tactile 집중 교육를 Atari 클래식에 업데이트 된 대규모 sequel에 적용 하려면 어떻게 해야 하나요? 입력 체계를 주요 당면 하기 전에 3 차원 공간에 대 한 게임 생성을 처리 해야 합니다.

HoloLens에서 화면 매핑을 시각화 하는 ![](images/surfacemapping.png)<br>
*HoloLens의 공간 매핑 시각화*

사용자의 환경을 활용 하 여 음력 모듈을 사용 하기 위한 무한 지형 옵션을 효과적으로 사용할 수 있습니다. 게임을 원래 제목과 비슷하게 만들려면 사용자가 잠재적으로 환경에서 다양 한 문제에 대 한 랜딩 패드를 조작 하 고 저장할 수 있습니다.

음력 모듈 ![비행](images/640px-lm-hero.jpg)<br>
*음력 모듈 비행*

사용자가 입력 체계를 학습 하 고, 배송을 제어 하 고, 소규모 대상이 배치 될 것을 요구 하는 경우가 많습니다. 성공적인 게임 환경에는 과제와 보상의 올바른 조합이 있습니다. 사용자는 HoloLens에서 검색 된 표면의 사용자 정의 영역에 성공적으로 배치 하도록 요구 하는 가장 쉬운 모드를 사용 하 여 난이도 수준을 선택할 수 있어야 합니다. 사용자가 게임 중단을 크랭크 면 적절 하다는 것을 알 수 있습니다.

### <a name="adding-input-for-hand-gestures"></a>핸드 제스처에 대 한 입력 추가

HoloLens 기본 입력은 두 개의 제스처 인 [공기 탭과 블 룸](gaze-and-commit.md#composite-gestures)있습니다. 사용자는 상황별 미묘한 차이을 기억할 필요가 없으며 플랫폼의 인터페이스를 다양 하 고 쉽게 배울 수 있도록 하는 특정 제스처의 laundry 목록이 필요 하지 않습니다. 시스템은 두 개의 제스처를 노출할 수 있지만, 장치는 한 번에 두 손을 추적할 수 있습니다. 음력 Lander는 [몰입 형 앱](app-model.md) 이며, 두 손을 활용 하 고 음력 모듈 탐색을 위한 고유한 즐거운 tactile 수단을 추가 하는 제스처의 기본 집합을 확장할 수 있습니다.

원래 컨트롤 구성표를 다시 살펴보면 **위한 것 및 회전을 해결 해야 했습니다**. 주의할 점은 새 컨텍스트에서 회전이 추가 축을 추가 하는 것입니다 (기술적으로는 2 이지만 Y 축은 계단에는 더 중요 하지 않음). 두 가지 고유한 배송 이동은 자신에 게 직접 매핑됩니다.

lander를 눌러 세 축 모두에서 회전 하는 제스처를 ![](images/module-handdrag.gif)<br>
*제스처를 탭 하 고 끌어서 세 축 모두에서 lander 회전*

**위한 것**

원래 아케이드 컴퓨터의 레버가 값의 눈금에 매핑되고, 레버가 더 높은 위한 것 배송에 적용 되었습니다. 여기서 nuance 중요 한 점은 사용자가 컨트롤의 손을 벗어나 원하는 값을 유지 하는 것입니다. 탭 및 끌기 동작을 효과적으로 사용 하 여 같은 결과를 얻을 수 있습니다. 위한 것 값은 0부터 시작 합니다. 사용자가 값을 늘리기 위해 탭 하 고 끕니다. 그러면 유지 관리로 전환할 수 있습니다. 모든 탭 및 끌기 제스처 값 변경은 원래 값에서 델타입니다.

**회전**

좀 더 복잡 합니다. Holographic "회전" 단추를 누르면 더욱 끔찍한 환경을 사용할 수 있습니다. 실제 컨트롤은 활용할 수 없으므로 lander를 나타내는 개체를 조작 하거나 lander 자체를 사용 하 여 동작을 가져와야 합니다. 사용자가 얼굴을 원하는 방향으로 "푸시 및 풀" 할 수 있도록 하는 탭 및 끌기를 사용 하는 메서드를 제공 합니다. 사용자가 탭 하 여 보유할 때마다 제스처가 시작 된 지점이 회전의 원본이 됩니다. 원점에서 끌어서 오면 (X, Y, Z) 손 모양 변환의 델타 (X, Y, Z)가 변환 되어 lander의 회전 값의 델타에 적용 됩니다. 간단히 말해서 *왼쪽 <-> 오른쪽 아래로 끌어서 < > 아래로 이동 < 공백으로 다시 이동 하면 배송이 적절 하 게 회전*합니다.

HoloLens는 두 손을 추적할 수 있으므로 위한 것가 왼쪽에 의해 제어 되는 동안 회전을 오른쪽에 할당할 수 있습니다. Finesse는이 게임의 성공을 위한 주행 요소입니다. 이러한 상호 작용의 *느낌* 은 절대 우선 순위가 가장 높습니다. 특히 tactile 집중 교육의 컨텍스트입니다. 너무 신속 하 게 반응 하는 배송일은 너무 빨리 반응 하는 것은 쉽지 않지만, 속도가 너무 느리면 사용자가 배송에서 awkwardly 긴 시간 동안 "푸시 및 끌어오기"를 수행 해야 합니다.

### <a name="adding-input-for-game-controllers"></a>게임 컨트롤러에 대 한 입력 추가

HoloLens의 제스처는 미세 제어의 novel 메서드를 제공 하지만, 아날로그 컨트롤에서 얻을 수 있는 ' true ' tactile 피드백은 아직 없습니다. Xbox 게임 컨트롤러를 연결 하면 컨트롤을 활용 하 여 미세 제어를 유지 하면서 이러한 physicality를 다시 가져올 수 있습니다.

Xbox 컨트롤러에 비교적 간단 하 게 전달 되는 컨트롤 구성표를 적용 하는 방법에는 여러 가지가 있습니다. 가능한 한 원래 아케이드 설정에 가깝게 유지 하려고 하기 때문에 **위한 것** 는 트리거 단추에 가장 잘 매핑됩니다. 이러한 단추는 아날로그 컨트롤이 며,이는 간단한 *설정 및 해제* 상태를 포함 하는 것입니다. 즉, 실제로 배치 수준에 응답 합니다. 이렇게 하면 **위한 것 레버**와 비슷한 구문을 제공 합니다. 원래 게임 및 손 제스처와는 달리이 컨트롤은 사용자가 트리거에 대 한 압력 배치를 중지 한 후 배송일의 위한 것을 자릅니다. 원래 아케이드 게임과 동일한 수준의 finesse을 계속 제공 합니다.

![왼쪽 엄지 스틱이 요 및 Roll에 매핑되고 오른쪽 엄지 스틱이 피치 및 롤에 매핑됩니다](images/thumbsticksidebyside.gif)<br>
*왼쪽 엄지 스틱은 요 및 roll에 매핑됩니다. 오른쪽 엄지 스틱을 피치 및 롤에 매핑됨*

이중 thumbsticks는 자연스럽 게 배송 회전을 제어 하는 것입니다. 불행 하 게는 축 하 나와 두 개의 축이 둘 다를 지 원하는 두 개의 thumbsticks를 제공 합니다. 이러한 불일치는 하나의 엄지 스틱 컨트롤 하나를 의미 합니다. 또는 thumbsticks에 대 한 축이 겹칩니다. Thumbsticks는 기본적으로 로컬 X 및 Y 값을 혼합 하므로 이전 솔루션이 "중단" 된 느낌을 종료 했습니다. 후자 솔루션은 어떤 중복 축을 가장 자연스럽 게 파악 하는 테스트를 필요로 했습니다. 최종 샘플에서는 왼쪽 엄지 스틱에 *요* 및 *roll* (Y 및 x 축)를 사용 하 고 오른쪽 엄지 스틱에 *피치* 및 *롤* (Z 및 x 축)을 사용 합니다. 이는 *요* 및 *피치*와 독립적으로 쌍으로 연결 되는 것 처럼 보이지만 가장 자연스럽 *게 생각 합니다* . 참고로, thumbsticks에 대 한 두 가지 *모두를 사용* 하 여 회전 값을 두 배로 만듭니다. lander do 루프를 사용할 때 매우 재미 있습니다.

이 샘플 앱은 공간 인식 및 tactile 집중 교육 Windows Mixed Reality의 확장 가능 입력 소프트웨어나 덕분에 환경을 크게 변경 하는 방법을 보여 줍니다. 음력은 Lander에 40 년 동안 사용할 수 있지만 작은 팔각형를 사용 하 여 노출 되는 개념은 영원히 지속 됩니다. 미래를 발견 때 과거를 확인 하지 않는 이유는 무엇 인가요?

## <a name="technical-details"></a>기술 세부 정보

[Mixed Reality 디자인 실험 GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule)에서 음력 모듈 샘플 앱에 대 한 스크립트 및 prefabs를 찾을 수 있습니다.

## <a name="about-the-author"></a>작성자 정보

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Addison Linville" width="60" height="60" src="images/addisonlinville-tile-60px.jpg"></td>
<td style="border-style: none"><b>Addison Linville</b><br>UX 디자이너 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>참고 항목
* [모션 컨트롤러](motion-controllers.md)
* [헤드 게이즈 및 커밋](gaze-and-commit.md)
* [혼합 현실 앱의 종류](types-of-mixed-reality-apps.md)
