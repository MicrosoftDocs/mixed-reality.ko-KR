---
title: 사례 연구-구멍에 실제로 탐색
description: 이 사례 연구에는 HoloLens, 벽, floor, 및에 실제 환경에서 가상 있는데 뒤 보려는 사용자에 대 한 "매직 창" 효과 구현 하는 방법을 설명 합니다.
author: EricRehmeyer
ms.author: ericrehm
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, magic 창, 시차
ms.openlocfilehash: 945a09614fbc77400825b524f4e0b591bf7b1f6b
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873932"
---
# <a name="case-study---looking-through-holes-in-your-reality"></a>사례 연구-구멍에 실제로 탐색

혼합된 현실 및 Microsoft HoloLens 사용 하 여 수행할 수 있는 작업에 대 한 생각을 하는 경우는 일반적으로 맞도록 질문 "하는 개체 내 공간을 추가할 수 있습니까?"와 같은 "어떤 수 있습니까 계층 내 공간 위에?" 또는 고려할 수 있습니다 다른 영역을 강조 표시 하려는-magic 트릭을 기본적으로-동일한 기술을 사용 하 여 들어오거나와 관련해 서 실제 개체를 통해 확인 합니다.

## <a name="the-tech"></a>기술 지원 담당자

벽을 통해 중단 됩니다 대로 외계인 경우 느껴지거나 했습니다  **[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)**, 안전 벽을 잠금 해제  **[조각](case-study-creating-an-immersive-experience-in-fragments.md)**, 이루어지는 했거나 UNSC 무한대 격납고에서 참조 하는  **[2015에서 E3 Halo 5 경험](https://www.youtube.com/watch?v=QDw5QjDtFy8)** 에 대 한 말하고자 보았을 것입니다. 상상력에 따라 임시 구멍에 건식에 배치 하거나 느슨한 floorboard 아래 세계를 숨기려면이 visual 트릭을 사용할 수 있습니다.

![RoboRaid 3 차원 파이프 및 다른 구조 벽을 중단 된 침략자 만들 구멍을 통해서만 표시 뒤에 추가 합니다.](images/roboraid-640px.png)

RoboRaid 3 차원 파이프 및 다른 구조 벽을 중단 된 침략자 만들 구멍을 통해서만 표시 뒤에 추가 합니다.

이러한 고유 홀로그램 중 하나를 사용 하 여 HoloLens에, 실제로 실제 창을 통해 자체를 표시 하는 동일한 방식 앱 사용자 층을 통해 또는 벽 뒤 콘텐츠의 효과 제공할 수 있습니다. 왼쪽으로 직접 이동 하 고 오른쪽에 무엇이 든 볼 수 있습니다. 좀 더 자세히를 가져오고 모든 좀 더 자세한를 볼 수 있습니다. 주요한 차이점은는 실제 구멍 수 있으며, 사용자 층 함에도 수 없습니다 마법 holographic 콘텐츠를 통해 않았다는 것입니다. (태스크를 추가 백로그.)

## <a name="behind-the-scenes"></a>백그라운드 작업

이 트릭은 두 가지 효과가의 조합입니다. 첫째, holographic 콘텐츠 "공간 앵커"를 사용 하 여 전 세계에 고정 해당 콘텐츠를 "world 잠긴" 앵커를 사용 하 여는에서 원하는 항목 하지 시각적으로 드리프트를 거의 실제 개체에서 기본 공간 매핑 시스템에 여유 공간 해당 3D 모델을 업데이트 또는 이동할 때에 의미 합니다.

둘째,만 표시 되도록 구멍을 통과 하 여 실제로 holographic 콘텐츠 매우 구체적인 공간을 시각적으로 제한 됩니다. 해당 폐색 탐색 논리 구멍, 창 또는 이르는 길 트릭을 판매 해야 하는 데 필요한 경우 항목 보기의 대부분을 차단 하지 않고 비밀 봤다면 차원 공간에서 crack 방금 잘못 배치 공룡 처럼 보일 수 있습니다.

![이 변경은 실제 스크린 샷 아니라 HoloLens에서 MR 기본 사항 101에서 비밀 지 표시 되는 모양을 보여 줍니다. 검은색 인클로저 나타나지 않지만 가상 구멍을 통해 콘텐츠를 볼 수 있습니다. (실제 장치를 살펴보는 경우 바닥 넘어서 없는 처럼 눈 먼 거리에 집중 하기 때문에 훨씬 더 사라집니다.)](images/origamiholecomposited-640px.png)

이 변경은 실제 스크린샷에서 아니라는 방법의 예시에서 비밀의 지 하는 [MR 기본 사항 101](holograms-101.md) HoloLens에서. 검은색 인클로저 나타나지 않지만 가상 구멍을 통해 콘텐츠를 볼 수 있습니다. (실제 장치를 살펴보는 경우 바닥 넘어서 없는 처럼 눈 먼 거리에 집중 하기 때문에 훨씬 더 사라집니다.)

### <a name="world-locking-holographic-content"></a>Holographic 콘텐츠 world 잠금

Unity에서 전 세계 잠긴 상태로 유지 하려면 holographic 콘텐츠를 일으키는 다음과 같습니다. WorldAnchor 구성 요소를 추가 하는 것 만큼 쉽습니다

```
myObject.AddComponent<WorldAnchor>();
```

WorldAnchor 구성 요소는 위치 및 해당 GameObject (및 따라서 계층 구조에서 해당 개체에서 다른 작업)의 실제 개체 주변에 상대적으로 안정적인 되도록 회전에 지속적으로 조정 됩니다. 콘텐츠를 작성할 때이 가상 구멍 중심이 개체의 루트 피벗 하는 방식으로 만듭니다. (개체의 피벗 벽의 깊은 수준에 있으면 해당 약간 조정 위치 및 회전에 훨씬 더 눈에 띄는 되 고 구멍 빌드되며 같지 않을 수 있습니다.)

### <a name="occluding-everything-but-the-virtual-hole"></a>가상 구멍을 제외한 모든 occluding

선택적으로 담 벼 락에서 숨겨진 항목에 보기를 차단 하는 방법의 여러 가지가 있습니다. 가장 간단한 것 HoloLens 완전히 black 개체 보이지 않는 나타나는지 즉는 가산적 표시 되는 사실을 활용 합니다. 모든 특수 셰이더 또는 자재 트릭을 수행 하지 않고 Unity에서 이렇게 하려면-을 black 자료를 만들고 콘텐츠에서 상자 하는 개체에 할당 합니다. 3D 모델링을 수행 하는 같은 생각 하지 않습니다, 경우에 많은 기본 쿼드 개체를 사용 하 여 고 약간 서로 겹치는 하기만 됩니다. 이 방식의 단점은 많이 있지만 빠르게 작동 하는 것 이며 낮은 충실도 개념 작업 증명을 가져오는, 나중에 리팩터링 하려는 의심 되는 경우에 합니다.

위의 "블랙 박스" 접근 방식에 큰 단점 하나는 잘 촬영 하지 않습니다. 효과 HoloLens의 표시를 통해 완벽 하 게 보일 수, 있지만 수행한 모든 스크린샷 벽의 floor 남은 대신 큰 검은색 개체를 표시 됩니다. 그 이유는 실제 하드웨어와 스크린 샷을 복합 홀로그램와 진실 다르게 합니다. 일부 가짜 수학에 잠시 우회 보겠습니다...

*가짜 수학 경고! 이러한 번호 및 수식은 모든 종류의 정확한 메트릭 일 수 없습니다는 내용을 설명 하기 위한 것!*

HoloLens를 통해 참조 항목:

```
( Reality * darkening_amount ) + Holograms
```

스크린샷 및 비디오에 표시 되는 내용:

```
( Reality * ( 1 - hologram_alpha ) ) + Holograms * hologram_alpha
```

영어의 경우: HoloLens를 통해 표시 되는 간단한의 조합 어두운된 실제로 (선글라스 통해와 같이) 및 모든 홀로그램 앱 표시 하려고 합니다. 하지만 카메라의 이미지 픽셀 별 투명도 값에 따라 앱의 홀로그램 혼합 됩니다 스크린 샷을 사용 하는 경우.

이 문제를 해결 하는 한 가지 방법은 깊이 버퍼에 쓸 및 기타 불투명 자료를 사용 하 여 정렬만 "블랙 박스" 자료를 변경 하기 위해서입니다. 이 예제를 확인 하세요 합니다 [GitHub의는 MixedRealityToolkit에 WindowOcclusion.shader 파일](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader)합니다. 여기에 관련 줄을 복사 됩니다.

```
"RenderType" = "Opaque"
"Queue" = "Geometry"
ColorMask 0
```

(오프셋에 유의 하세요 "50, 100" 줄 것 이기 때문 것을 생략 하는 것이 관련 되지 않은 문제를 해결 하는 것입니다.)

보이지 않는 폐색 자료를 구현 하는 올바른 표시에서 및 혼합 현실 스크린샷에서 보이는 상자를 그리는 앱 수 있습니다. 보너스 점수에 대 한 이보다 적은 수의 보이지 않는 픽셀을 그릴 clever 수행 하 여 더욱 상자의 성능을 개선 하기 위해 시도할 수 있지만 근본 원인을 제거를 얻을 수 있습니다 하 고 일반적으로 필요 하지 않습니다.

![Unity 그립니다 외부 부분 occluding 상자 제외 하 고 해당 하는 대로 MR 기본 사항 101에서 비밀 지 하는 다음과 같습니다. Note는 지 하의 피벗 임을 구멍을 유지 하는 데 도움이 되는 상자의 가운데에 실제 floor를 기준으로 최대한 안정적으로.](images/underworld-occluded-640px.png)

비밀 지 하는 다음과 같습니다 [MR 기본 사항 101](holograms-101.md) 으로 Unity 외부 부분 occluding 상자 제외 하 고이 그립니다. Note는 지 하의 피벗 임을 구멍을 유지 하는 데 도움이 되는 상자의 가운데에 실제 floor를 기준으로 최대한 안정적으로.

## <a name="do-it-yourself"></a>사용자가 직접 수행

HoloLens 있고 직접 효과 사용 하 시겠습니까? (코딩할 필요 없이) 할 수 없는 가장 간단한 방법은 로드 한 후 무료 3D 뷰어 앱을 설치 하는 것은 [GitHub에서 제공한 the.fbx 파일 다운로드](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow) 방에 꽃 pot 모델을 볼 합니다. HoloLens, 로드 및 직장 효과 볼 수 있습니다. 모델 앞에 있는 경우 볼 수 있습니다를 작은 구멍에-기타 등등 표시 되지 않습니다. 다른 쪽에서 모델을 조회 하 고 완전히 사라집니다. 상상할 수 있는 몇 가지 아이디어를 생성 하려면 세로 화면에 대 한 가상 구멍 위치로 이동, 회전 및 크기 조정 컨트롤의 3D 뷰어 사용!

![Unity 편집기에서이 모델을 보기는 flowerpot 주위에 큰 검은색 상자 표시 됩니다. 상자가 사라집니다, HoloLens에서 매직 창 효과를 방법을 제공 합니다.](images/magicwindowflowerpotineditor.png)

Unity 편집기에서이 모델을 보기는 flowerpot 주위에 큰 검은색 상자 표시 됩니다. 상자가 사라집니다, HoloLens에서 매직 창 효과를 방법을 제공 합니다.

이 기술을 사용 하는 앱을 빌드 하려는 경우 체크 아웃 합니다 [MR 기본 사항 101 자습서](holograms-101.md) 에 [혼합 현실 자습서](tutorials.md)합니다. 7 장 (위의 그림)로 숨겨진된 지 표시 하 여 층에 끝납니다. 자습서가 지루한 라고?

다음은 몇 가지 아이디어를 작성할 수 있는이 다음의:
* 대화형 가상 구멍 내부 콘텐츠를 확인 하는 방법을 생각할 수 있습니다. 사용자가 해당 경계를 넘어 몇 가지 영향을 미칠 수 불가사의이 트릭을 제공할 수 있는의 의미 실제로 향상 시킬 수 있습니다.
* 알려진된 영역에 다시 개체를 통해 참조 하는 방법을 생각할 수 있습니다. 예를 들어 수 holographic 구멍 커피 테이블에 배치 하는 방법을 아래에 floor를 참조 하세요?

## <a name="about-the-author"></a>저자 소개

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Eric Rehmeyer" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Eric Rehmeyer</b><br>선임 소프트웨어 엔지니어 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>참조
* [MR 기본 101: 디바이스를 사용하는 완전한 프로젝트](holograms-101.md)
* [좌표계](coordinate-systems.md)
* [공간 앵커](spatial-anchors.md)
* [공간 매핑](spatial-mapping.md)
