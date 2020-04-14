---
title: 사례 연구-현실에서의 구멍 검색
description: 이 사례 연구에서는 HoloLens에 "자동 창" 효과를 구현 하 여 사용자가 실제 환경 내에서 옆면을 볼 수 있도록 하는 방법을 설명 합니다.
author: ericrehmeyer
ms.author: bestruku
ms.date: 10/18/2019
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, 마법 창, 시차
ms.openlocfilehash: c829656c98b7c87f8b969dbbd16115f6a0bbaf27
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278151"
---
# <a name="case-study---looking-through-holes-in-your-reality"></a>사례 연구-현실에서의 구멍 검색

사용자가 혼합 현실 및 Microsoft HoloLens로 수행할 수 있는 작업에 대해 생각 하는 경우 일반적으로 "대화방에 추가할 수 있는 개체는 무엇 인가요?"와 같은 질문에 해당 합니다. 또는 "공간 위에 계층화 할 수 있는 것은 무엇입니까?" 고려할 수 있는 다른 영역을 강조 하 고 싶습니다. 기본적으로 동일한 기술을 사용 하 여 사용자를 대상으로 하는 실제 개체를 조회 하는 것입니다.

## <a name="the-tech"></a>기술

**[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)** 의 벽을 fought 하 고, **[조각](case-study-creating-an-immersive-experience-in-fragments.md)** 에서 벽을 안전 하 게 잠금 해제 하거나, **[2015의 E3에 있는 HALO 5 환경](https://www.youtube.com/watch?v=QDw5QjDtFy8)** 에서 unsc Infinity hangar를 볼 만큼 충분 하다 고 생각 하는 경우, 제가 이야기 하 고 있는 것을 볼 수 있습니다. 상상력에 따라이 시각적 트릭을 사용 하 여 drywall에 임시 구멍을 배치 하거나 느슨한 floorboard에서 환경을 숨길 수 있습니다.

![RoboRaid은 3 차원 파이프와 벽 뒤에 있는 다른 구조를 추가 하 여 invaders break로 생성 된 구멍을 통해서만 표시 됩니다.](images/roboraid-640px.png)

RoboRaid은 3 차원 파이프와 벽 뒤에 있는 다른 구조를 추가 하 여 invaders break로 생성 된 구멍을 통해서만 표시 됩니다.

앱은 HoloLens의 이러한 고유 holograms 중 하나를 사용 하 여 실제 창을 통해 자신을 나타내는 것과 같은 방식으로 벽 뒤에 있는 콘텐츠의 효과를 제공할 수 있습니다. 왼쪽으로 이동 하 고 오른쪽에 있는 모든 항목을 볼 수 있습니다. 좀 더 자세히 알아보겠습니다. 모든 것을 볼 수 있습니다. 주요 차이점은 실제 구멍에서를 사용 하는 것 이지만, 바닥 stubbornly는 해당 마법 holographic 콘텐츠를 통과할 수 없습니다. (백로그에 작업을 추가 합니다.)

## <a name="behind-the-scenes"></a>백그라운드 작업

이 트릭은 두 가지 효과의 조합입니다. 첫째, holographic 콘텐츠는 "공간 앵커"를 사용 하 여 전 세계에 고정 됩니다. 앵커를 사용 하 여 "세계에서 잠김" 콘텐츠를 사용 하면 이동 하는 경우 또는 기본 공간 매핑 시스템에서 해당 공간의 3D 모델을 업데이트 하는 경우에도 원하는 내용이 근처의 물리적 개체에서 시각적으로 사라지지 않습니다.

둘째, holographic 내용이 매우 특정 공간으로 시각적으로 제한 되므로 현실에서 구멍을 통해서만 볼 수 있습니다. 이 폐색는 트릭을 판매 하는 논리 구멍, 창 또는 이르는 길을 살펴보는 데 필요 합니다. 대부분의 뷰를 차단 하지 않으면 비밀 Jurassic 차원에 대 한 공간을 해독 하는 것은 잘못 배치 된 공룡 처럼 보일 수 있습니다.

![이는 실제 스크린샷은 아니지만, MR 기본 사항 101의 비밀 지 여부에 대 한 설명은 HoloLens를 확인 하는 방법에 대 한 설명입니다. 검은색 인클로저는 표시 되지 않지만 가상 구멍을 통해 콘텐츠를 볼 수 있습니다. (실제 장치를 살펴볼 때 눈이 없는 것 처럼 더 많은 거리에 집중 하는 것 처럼 보일 수도 있습니다.)](images/origamiholecomposited-640px.png)

실제 스크린샷은 아니지만, [MR 기본 사항 101](holograms-101.md) 의 비밀 지가 HoloLens를 어떻게 볼 수 있는 지에 대 한 예시를 보여 줍니다. 검은색 인클로저는 표시 되지 않지만 가상 구멍을 통해 콘텐츠를 볼 수 있습니다. (실제 장치를 살펴볼 때 눈이 없는 것 처럼 더 많은 거리에 집중 하는 것 처럼 보일 수도 있습니다.)

### <a name="world-locking-holographic-content"></a>세계 holographic 콘텐츠 잠금

Unity에서 holographic 콘텐츠가 세계에서 잠긴 상태로 유지 되도록 하는 것은 WorldAnchor 구성 요소를 추가 하는 것 만큼 쉽습니다.

```
myObject.AddComponent<WorldAnchor>();
```

WorldAnchor 구성 요소는 해당 GameObject의 위치와 회전을 지속적으로 조정 하 여 주변 물리적 개체에 상대적으로 유지 합니다. 콘텐츠를 제작할 때 개체의 루트 피벗이이 가상 구멍 가운데에 오도록 하 여 해당 콘텐츠를 만듭니다. (개체의 피벗이 벽에 있는 경우에는 위치 및 회전이 약간 조정 되는 것이 훨씬 더 눈에 띄지 않으며 구멍이 안정적이 지 않은 것 처럼 보일 수 있습니다.)

### <a name="occluding-everything-but-the-virtual-hole"></a>가상 구멍이 아닌 모든 항목 Occluding

벽에서 숨겨진 항목에 대 한 보기를 선택적으로 차단 하는 다양 한 방법이 있습니다. 가장 간단한 방법은 HoloLens가 추가 표시를 사용 한다는 사실을 활용 하는 것입니다. 즉, 완전히 검정색 개체가 보이지 않는 것으로 나타납니다. 특별 한 셰이더 나 재질을 사용 하지 않고 Unity에서이 작업을 수행할 수 있습니다. 검정 재질을 만들어 콘텐츠의 상자를 지정 하는 개체에 할당 하기만 하면 됩니다. 3D 모델링을 수행 하는 것이 마음에 들지 않으면 몇 개의 기본 쿼드 개체를 사용 하 고 약간 겹치게 합니다. 이 접근 방식에는 몇 가지 단점이 있지만, 작업을 수행 하는 가장 빠른 방법은 나중에 리팩터링할 수 있는 것으로 의심 되는 경우에도 중요 한 개념 증명을 사용 하는 것입니다.

위의 "검은색 상자" 접근 방법의 주요 단점 중 하나는 사진이 제대로 작동 하지 않는다는 것입니다. HoloLens 표시를 통해 효과가 완벽 하 게 보일 수 있지만, 사용 하는 모든 스크린샷은 벽 또는 층이 아니라 긴 검은색 개체를 표시 합니다. 그 이유는 물리적 하드웨어와 스크린샷 복합 holograms 및 현실가 다르게 하는 것입니다. 약간의 가짜를 잠시 우회.

*가짜 수학 경고! 이러한 숫자와 수식은 정확한 메트릭이 아닌 점을 보여 주기 위해 작성 되었습니다.*

HoloLens를 통해 표시 되는 내용:

```
( Reality * darkening_amount ) + Holograms
```

스크린샷 및 비디오에 표시 되는 내용:

```
( Reality * ( 1 - hologram_alpha ) ) + Holograms * hologram_alpha
```

영어: HoloLens를 통해 표시 되는 내용은 어두운 현실 (예: 선글라스) 및 앱에서 표시 하려는 holograms의 간단한 조합입니다. 하지만 스크린샷을 만들 때 카메라 이미지는 픽셀 별 투명도 값에 따라 앱의 holograms 혼합 됩니다.

이 문제를 해결 하는 한 가지 방법은 "검은색 상자" 자료를 깊이 버퍼에만 쓰도록 변경 하 고 다른 모든 불투명 자료를 정렬 하는 것입니다. 이에 대 한 예제를 보려면 GitHub의 [MixedRealityToolkit에서 WindowOcclusion 파일](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader)을 확인 하세요. 관련 줄이 여기에 복사 됩니다.

```
"RenderType" = "Opaque"
"Queue" = "Geometry"
ColorMask 0
```

("오프셋 50, 100" 줄은 관련 되지 않은 문제를 처리 하는 것 이므로이를 그대로 유지 하는 것이 좋습니다.)

표시 되는 것과 같은 보이지 않는 폐색 재질을 구현 하 여 앱이 디스플레이 및 혼합 현실 스크린샷에서 올바른 모양의 상자를 그릴 수 있습니다. 보너스 점수를 얻기 위해 더 작은 수의 보이지 않는 픽셀을 그리기 위해 더 많은 작업을 수행 하 여 해당 상자의 성능을 향상 시킬 수 있지만,이는 일반적으로 weeds에 포함 될 수 있으며 일반적으로 필요 하지 않습니다.

![다음은 occluding 상자의 외부 파트를 제외 하 고 Unity가 그릴 때 MR 기본 101의 비밀 지 수입니다. 지 수에 대 한 피벗은 상자 중심에 있으므로 실제 바닥을 기준으로 가능한 한 안정적으로 구멍을 유지할 수 있습니다.](images/underworld-occluded-640px.png)

다음은 occluding 상자의 외부 파트를 제외 하 고 Unity가 그릴 때 [MR 기본 101](holograms-101.md) 의 비밀 지 수입니다. 지 수에 대 한 피벗은 상자 중심에 있으므로 실제 바닥을 기준으로 가능한 한 안정적으로 구멍을 유지할 수 있습니다.

## <a name="do-it-yourself"></a>직접

HoloLens가 있고 그에 대 한 효과를 시험해 보 시겠습니까? 가장 쉬운 작업 (코딩 필요 없음)은 무료 3D 뷰어 앱을 설치한 다음, [GitHub에 제공 된 fbx 파일 다운로드](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow) 를 로드 하 여 대화방에서 꽃 .pot 모델을 볼 수 있습니다. HoloLens에 로드 하 고 작업에 대 한 환상 효과를 볼 수 있습니다. 모델 앞에 있는 경우 작은 구멍만 볼 수 있으며, 다른 모든 항목은 보이지 않습니다. 다른 쪽에서 모델을 살펴보면 완전히 사라집니다. 3D 뷰어의 이동, 회전 및 크기 조정 컨트롤을 사용 하 여 몇 가지 아이디어를 생성 하는 것으로 간주할 수 있는 수직 표면의 가상 구멍을 배치 합니다.

![Unity 편집기에서이 모델을 보면 flowerpot 주위에 긴 검은색 상자가 표시 됩니다. HoloLens에서 상자가 사라지고 매직 창 효과를 제공 합니다.](images/magicwindowflowerpotineditor.png)

Unity 편집기에서이 모델을 보면 flowerpot 주위에 긴 검은색 상자가 표시 됩니다. HoloLens에서 상자가 사라지고 매직 창 효과를 제공 합니다.

이 기법을 사용 하는 앱을 빌드 하려는 경우 [Mixed Reality 자습서](tutorials.md)의 [MR 기본 사항 101 자습서](holograms-101.md) 를 확인 하세요. 7 장은 위에서 설명한 대로 숨겨진 지 각 지를 보여 주는 폭발으로 끝납니다. 자습서는 지루한 일이 있나요?

다음은이 아이디어를 수행할 수 있는 몇 가지 아이디어입니다.
* 가상 구멍 내에서 콘텐츠를 대화형으로 만드는 방법을 생각해 보겠습니다. 사용자가 자신의 벽을 넘어 약간의 영향을 줄 수 있도록 하면이 트릭에서 제공할 수 있는 불가사의의 의미를 크게 높일 수 있습니다.
* 개체를 통해 알려진 영역으로 다시 확인 하는 방법을 고려 합니다. 예를 들어 커피 테이블에 holographic를 추가 하 고 그 아래에 있는 바닥을 확인 하려면 어떻게 해야 하나요?

## <a name="about-the-author"></a>작성자 정보

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Eric Rehmeyer" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Eric Rehmeyer</b><br>수석 소프트웨어 엔지니어 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>참고 항목
* [MR 기본 사항 101: 장치를 사용 하 여 프로젝트 완료](holograms-101.md)
* [좌표계](coordinate-systems.md)
* [공간 앵커](spatial-anchors.md)
* [공간 매핑](spatial-mapping.md)
