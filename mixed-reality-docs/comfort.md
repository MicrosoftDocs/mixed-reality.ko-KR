---
title: 편안함
description: 자연스럽게 보는 동안 인간의 시각적 시스템은 여러 정보 소스 또는 "큐"를 사용하여 3D 모양과 개체의 상대 위치를 해석합니다.
author: erickjpaul
ms.author: erpau
ms.date: 06/25/2020
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, 디자인, 편안함, HoloLens 2, HoloLens(1세대)
ms.openlocfilehash: 12dc632e4cba925abb1c4ac9e17364f94a6804c9
ms.sourcegitcommit: 5612e8bfb9c548eac42182702cec87b160efbbfe
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85441820"
---
# <a name="comfort"></a>편안함

## <a name="overview"></a>개요

자연스럽게 보는 동안 인간의 시각적 시스템은 여러 정보 소스 또는 "큐"를 사용하여 3D 모양과 개체의 상대 위치를 해석합니다. 일부 큐는 [직선 원근법](https://en.wikipedia.org/wiki/Perspective_(graphical)), [친숙한 크기](https://en.wikipedia.org/wiki/Size#Perception_of_size), 폐색, [심도 흐림 효과](https://en.wikipedia.org/wiki/Depth_of_field) 및 [조절](https://en.wikipedia.org/wiki/Accommodation_(eye))을 포함하여 단안(단안 큐)만 사용합니다. 다른 큐는 쌍안(쌍안 큐)을 사용하며, [수렴](https://en.wikipedia.org/wiki/Vergence)(vergence, 기본적으로 개체를 보는 데 필요한 눈동자의 상대적 회전) 및 [쌍안 시차](https://en.wikipedia.org/wiki/Stereopsis)(binocular disparity, 두 눈동자 뒤쪽의 장면 투영 간의 차이 패턴)를 포함합니다. 헤드 마운트 디스플레이에서 최대한 편안하도록 하려면 디자이너와 개발자가 이러한 신호가 자연계에서 작동하는 방식을 모방하는 방식으로 콘텐츠를 만들고 표시해야 합니다. 신체적 관점에서 목 또는 팔을 피로하게 하는 모션을 요구하지 않는 콘텐츠를 설계하는 것도 중요합니다. 이 문서에서는 이러한 목표를 달성하기 위해 명심해야 할 주요 고려 사항을 살펴보겠습니다.

## <a name="vergence-accommodation-conflict"></a>수렴-조절 불일치(vergence-accommodation conflict)

개체를 깨끗하게 보려면 눈의 초점을 개체의 거리에 맞게 [조절](https://en.wikipedia.org/wiki/Accommodation_%28eye%29) 또는 조정해야 합니다. 동시에 두 눈의 회전은 이중 이미지를 볼 수 없도록 개체의 거리에 맞게 [수렴](https://en.wikipedia.org/wiki/Convergence_(eye))해야 합니다. 자연스럽게 볼 때 수렴과 조절은 연결되어 있습니다. 가까이 있는 개체(예: 코 근처에 있는 집파리)를 볼 때 눈이 교차하여 가까운 지점에 맞게 조절합니다. 반대로, 광학 무한 물점(일반 시력의 경우 6m 이상에서 시작)에서 개체를 보는 경우 시선은 평행이 되고 수정체는 무한 물점에 맞게 조절됩니다. 

대부분의 헤드 마운트 디스플레이에서 사용자는 항상 디스플레이의 초점 거리(선명한 이미지를 얻기 위해)에 맞게 조절하지만, 관심 있는 개체의 거리(단일 이미지를 얻기 위해)로 수렴합니다. 사용자가 서로 다른 거리를 조절하고 수렴하는 경우 두 큐 간의 자연스러운 연결을 끊어야 하며, 이로 인해 시각적 불편함 또는 피로가 발생할 수 있습니다.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/-606oZKLa_s" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### <a name="guidance-for-holographic-devices"></a>홀로그램 디바이스에 대한 지침

HoloLens 디스플레이는 사용자로부터 약 2.0m 떨어진 광학 거리에 고정되어 있습니다. 따라서 사용자는 디바이스에서 깨끗한 이미지를 유지하기 위해 항상 2.0m 가까이로 조절해야 합니다. 앱 개발자는 콘텐츠와 홀로그램을 다양한 깊이에 배치하여 사용자의 눈이 수렴하는 위치를 안내할 수 있습니다. 사용자가 수렴하는 콘텐츠를 가능한 한 2.0m 가까이 유지함으로써(즉, 깊이가 많은 장면에서 가능한 경우 관심 영역을 사용자로부터 2.0m 가까이 배치함) 수렴-조절 불일치로 인한 불편함을 방지하거나 최소화할 수 있습니다. 콘텐츠를 2.0m 가까이에 배치할 수 없는 경우 사용자의 시선이 다른 거리 간에 앞뒤로 전환할 때 수렴-조절 불일치로 인한 불편함이 가장 큽니다. 다시 말해, 자신을 향해 50cm 떨어져 있고 시간이 지남에 따라 자신과 멀어지는 홀로그램을 보는 것보다 50cm 떨어져 있는 고정 홀로그램을 보는 것이 훨씬 더 편안합니다.

![사용자로부터 홀로그램을 배치하는 데 가장 적합한 거리입니다.](images/distanceguiderendering-950px.png)<br>
*사용자로부터 홀로그램을 배치하는 데 가장 적합한 거리*

### <a name="best-practices-for-hololens-1st-gen-and-hololens-2"></a>HoloLens(1세대) 및 HoloLens 2에 대한 모범 사례

최대한 편안하도록 **홀로그램을 배치하는 데 가장 적합한 영역은 1.25m에서 5m 사이입니다**. 모든 경우에서 설계자는 사용자가 콘텐츠에서 1m 이상 떨어져서 상호 작용하도록 콘텐츠 장면을 구성해야 합니다(예: [콘텐츠 크기 및 기본 배치 매개 변수 조정](gaze-and-commit.md)). 

경우에 따라 콘텐츠를 1m 이내에 표시해야 할 수도 있지만, 홀로그램은 40cm보다 더 가까이 표시하지 않는 것이 좋습니다. 따라서 더 가까운 개체를 방지하려면 **콘텐츠를 40cm에서 페이드 아웃하고 렌더링 클리핑 평면을 30cm로 배치**하는 것이 좋습니다.

깊이 움직이는 개체는 고정된 개체보다 수렴-조절 불일치로 인한 불편함이 발생할 수 있는 가능성이 더 높습니다. 마찬가지로 사용자가 근거리 초점과 원거리 초점 사이를 빠르게 전환해야 하는 경우 시각적 불편함과 피로가 발생할 수 있습니다. 따라서 **사용자가 깊이 움직이는 콘텐츠를 보거나 근거리 및 원거리 홀로그램 간에 초점을 빠르게 전환하는 빈도를 최소화하기 위해 특별히 주의해야 합니다**. 

### <a name="additional-considerations-for-hololens-2-and-near-interaction-distances"></a>HoloLens 2 및 근거리 상호 작용 거리에 대한 추가 고려 사항

직접(근거리) 상호 작용에 대한 콘텐츠를 HoloLens 2에서 설계하거나 **1m보다 가까이 배치해야 하는 모든 애플리케이션에서 설계하는 경우 사용자의 편안함을 보장하도록 특별히 주의해야 합니다**. 가시 거리가 감소함에 따라 수렴-조절 불일치로 인한 불편함이 발생할 확률은 기하 급수적으로 증가합니다. 또한 사용자는 가까운 상호 작용 거리에서 콘텐츠를 볼 때 흐릿함이 증가할 수 있으므로 깨끗하고 편안하게 볼 수 있도록 최적의 홀로그램 배치 영역 내에서 그리고 클리핑 평면 아래로 1.0m 미만까지 렌더링된 콘텐츠를 테스트하는 것이 좋습니다. 

**사용자가 1.0m 미만으로 가깝고 깊이 움직이는 콘텐츠를 볼 것으로 예상되는 시간을 기준으로 앱에 대한 "깊이 예산"을 만드는 것이 좋습니다**. 예를 들어 사용자를 시간의 25%를 초과하는 상황에 배치되지 않도록 방지합니다. 깊이 예산이 초과되면 편안한 환경을 유지할 수 있도록 사용자를 신중하게 테스트하는 것이 좋습니다. 

일반적으로 가까운 상호 작용 거리의 모든 상호 작용 요구 사항(예: 이동 속도, 도달 가능성 등)을 통해 사용자가 편안한 상태로 유지되는지 신중하게 테스트하는 것이 좋습니다. 


### <a name="guidance-for-immersive-devices"></a>몰입형 디바이스에 대한 지침

몰입형 디바이스의 경우 HoloLens에 대한 지침 및 모범 사례가 여전히 적용되지만, 편안함 영역의 특정 값이 디스플레이까지의 초점 거리에 따라 변합니다. 일반적으로 이러한 디스플레이까지의 초점 거리는 1.25m-2.5m입니다. 확실하지 않은 경우 관심 있는 개체를 사용자에게 너무 가까이 렌더링하지 말고 대부분의 콘텐츠를 1m 이상 멀리 유지하도록 합니다.

## <a name="interpupillary-distance-and-vertical-offset"></a>눈동자 간 거리 및 세로 오프셋

HMD(헤드 마운트 디스플레이)에서 디지털 콘텐츠를 볼 때 디지털 콘텐츠의 표시 위치를 기준으로 보는 사람의 눈 위치가 매우 중요합니다. 특히 HMD에서 디지털 콘텐츠를 편안하게 보려면 [IPD](https://en.wikipedia.org/wiki/Pupillary_distance)(눈동자 간 거리)와 VO(세로 오프셋)가 모두 중요합니다. 

IPD는 개인의 눈동자 또는 눈 중심 사이의 거리를 나타냅니다. VO는 보는 사람의 눈의 가로 축을 기준으로 각 눈에 보이는 디지털 콘텐츠의 잠재적인 세로 오프셋을 나타냅니다(특히, 이는 가로 오프셋 또는 쌍안 시차와 동일하지 않음). 개별 사용자에게 이러한 요소 중 하나 또는 둘 모두를 잘못 일치시키면 V-A(수렴-조절) 불일치로 인한 불편함의 영향이 악화될 수 있지만, 이러한 불일치가 최소화되는 경우(예: HoloLens의 2.0m 초점 거리에 표시되는 콘텐츠의 경우) 불편함이 발생할 수도 있습니다. 

### <a name="guidance-for-holographic-devices"></a>홀로그램 디바이스에 대한 지침

#### <a name="hololens-1st-gen"></a>HoloLens(1세대)

HoloLens(1세대)의 경우 디바이스 [보정](calibration.md) 중에 IPD가 추정되고 설정됩니다. 이미 설정된 디바이스에 대한 새 사용자의 경우 보정을 실행하거나 IPD를 수동으로 설정해야 합니다. VO는 전적으로 디바이스에 맞게 결정됩니다. 특히, VO를 최소화하려면 디바이스가 눈의 축과 수평이 되도록 디스플레이가 사용자의 머리 위에 있을 필요가 있습니다. 

#### <a name="hololens-2"></a>HoloLens 2

HoloLens 2의 경우 눈/디바이스 [보정](calibration.md) 중에 IPD가 추정되고 설정됩니다. 이미 설정된 디바이스에 대한 새 사용자의 경우 IPD가 올바르게 설정되도록 보정을 실행해야 합니다. VO는 HoloLens 2에서 자동으로 처리됩니다. 

### <a name="guidance-for-immersive-devices"></a>몰입형 디바이스에 대한 지침

Windows Mixed Reality 몰입형 HMD에는 IPD 또는 VO에 대한 자동 보정이 없습니다. IPD는 소프트웨어에서 수동으로 설정할 수 있습니다(Mixed Reality 포털 설정 아래의 [보정](calibration.md) 참조). 또는 일부 HMD에는 사용자가 렌즈 간격을 편안한 위치(즉, IPD와 거의 일치)로 조정할 수 있는 기계적 슬라이더가 있습니다. 

## <a name="rendering-rates"></a>렌더링 속도

사용자가 현실 세계에서 자유롭게 이동하고 실제 개체인 것처럼 가상 콘텐츠와 상호 작용할 수 있으므로 혼합 현실 앱은 고유합니다. 이 인상을 유지하려면 홀로그램을 렌더링하여 현실 세계에서 안정적으로 표시하고 애니메이션 효과를 부드럽게 적용해야 합니다. [60FPS(초당 프레임 수) 이상](understanding-performance-for-mixed-reality.md)으로 렌더링하면 이 목표를 달성할 수 있습니다. 60FPS를 초과하는 프레임 속도에서 렌더링을 지원하는 몇 가지 Mixed Reality 디바이스가 있으며, 이러한 디바이스의 경우 최적의 사용자 환경을 제공하기 위해 더 높은 프레임 속도로 렌더링하는 것이 좋습니다.

**자세히 알아보기**

[현실 세계 또는 가상 세계에서 안정적인 것](hologram-stability.md)처럼 보이도록 홀로그램을 그리려면 앱이 사용자의 위치에서 이미지를 렌더링해야 합니다. 이미지 렌더링에는 시간이 걸리므로 이미지가 디스플레이에 표시될 때 HoloLens 및 기타 Windows Mixed Reality 디바이스는 사용자의 머리가 있는 위치를 예측합니다. 이 예측 알고리즘은 근사값입니다. Windows Mixed Reality 알고리즘과 하드웨어는 렌더링된 이미지를 조정하여 예측된 머리 위치와 실제 머리 위치 간의 불일치를 처리합니다. 이 프로세스를 통해 사용자가 보는 이미지를 올바른 위치에서 렌더링한 것처럼 표시하고 홀로그램을 안정적으로 느끼게 합니다. 업데이트는 머리 위치를 약간만 변경하는 경우에 가장 적합하며, 모션-시차로 인해 발생한 것과 같이 일부 렌더링된 이미지 차이를 완전히 처리할 수는 없습니다.

**60FPS 이상의 프레임 속도로 렌더링하면 안정적인 홀로그램을 만드는 데 도움이 되는 다음 두 가지 작업을 수행합니다.**
1. 고르지 않은 모션과 이중 이미지를 특징으로 하는 심한 진동(judder)의 모양을 줄입니다. 더 빠른 홀로그램 모션과 낮은 렌더링 속도는 더 뚜렷한 심한 진동과 관련이 있습니다. 따라서 홀로그램 이동 시 흔들림을 방지하려면 속도를 가급적 60FPS(또는 디바이스의 최대 렌더링 속도)로 유지하는 것이 좋습니다.
2. 전체 대기 시간을 최소화합니다. 게임 스레드와 렌더링 스레드가 잠금 단계에서 실행되는 엔진에서 30FPS로 실행하면 33.3밀리초의 대기 시간이 추가될 수 있습니다. 대기 시간을 줄이면 예측 오류가 줄어들고 홀로그램 안정성이 향상됩니다.

**성능 분석**

애플리케이션 프레임 속도를 벤치마크하는 데 사용할 수 있는 다양한 도구는 다음과 같습니다.
* GPUView
* Visual Studio 그래픽 디버거
* Unity의 프레임 디버거와 같은 3D 엔진에 기본 제공되는 프로파일러

## <a name="self-motion-and-user-locomotion"></a>자체 모션 및 사용자 보행

물리적 공간의 크기만 유일하게 제한됩니다. 사용자가 실제 실내에서보다 가상 환경에서 더 멀리 이동할 수 있도록 허용하려면 순수한 가상 모션의 형태를 구현해야 합니다. 그러나 사용자의 실제 신체적 모션과 일치하지 않는 지속적인 가상 모션은 종종 멀미를 발생시킬 수 있습니다. 이 결과는 *현실 세계*에서 들어오는 자체 모션에 대한 [전정 큐](https://en.wikipedia.org/wiki/Vestibular_system)와 충돌하는 *가상 세계*의 자체 모션에 대한 *시각적 큐* 때문입니다.

다행히도, 다음과 같이 문제를 방지하는 데 도움이 되는 사용자 보행을 구현하기 위한 팁이 있습니다.
* 사용자는 항상 자신의 움직임을 제어해야 합니다. 예기치 않은 자체 모션이 특히 문제가 될 수 있습니다.
* 인간은 중력의 방향에 매우 민감합니다. 따라서 사용자가 시작하지 않은 세로 모션은 특히 피해야 합니다.

### <a name="guidance-for-holographic-devices"></a>홀로그램 디바이스에 대한 지침

사용자가 대규모 가상 환경에서 다른 위치로 이동할 수 있도록 하는 한 가지 방법은 장면에서 작은 개체를 이동하는 느낌을 주는 것입니다. 이 효과를 달성할 수 있는 방법은 다음과 같습니다.
   1. 사용자가 가상 환경에서 이동하려는 지점을 선택할 수 있는 인터페이스를 제공합니다.
   2. 선택하면 장면 렌더링을 원하는 지점 주위의 디스크로 축소합니다.
   3. 선택한 지점을 유지하면서 사용자가 작은 개체인 것처럼 이동할 수 있도록 합니다. 그런 다음, 사용자가 선택한 지점을 자신의 발 가까이로 이동할 수 있습니다.
   4. 선택한 지점을 해제하면 전체 장면 렌더링을 다시 시작합니다.

### <a name="guidance-for-immersive-devices"></a>몰입형 디바이스에 대한 지침

이전의 홀로그램 디바이스 접근 방식은 "디스크"를 이동하는 동안 앱에서 큰 검은색 공간 또는 다른 기본 환경을 렌더링해야 하므로 몰입형 디바이스에서도 효율적으로 작동하지 않습니다. 이 처리는 사람의 몰입감을 방해합니다. 몰입형 헤드셋의 사용자 보행에 대한 한 가지 트릭은 "깜박임" 방식입니다. 사용자에게 자신의 모션에 대한 제어와 움직임에 대한 간략한 인상을 제공하지만, 사용자가 순전히 가상 자체 모션으로 인해 혼란스러워 할 가능성이 낮은 구현은 다음과 같습니다.
   1. 사용자가 가상 환경에서 이동하려는 지점을 선택할 수 있는 인터페이스를 제공합니다.
   2. 선택하면 렌더링을 매우 빠르게 페이드 아웃하면서 해당 위치로 매우 빠르게 시뮬레이션된 모션(100m/s)을 시작합니다.
   3. 변환이 완료되면 렌더링을 다시 페이드 인합니다.

## <a name="heads-up-displays"></a>천정형 디스플레이

1인칭 슈팅 비디오 게임에서 HUD(천정형 디스플레이)는 플레이어 상태, 미니 맵 및 인벤토리와 같은 정보를 장면에 직접 지속적으로 제공합니다. HUD는 게임 플레이 환경을 방해하지 않으면서 플레이어에 정보를 제공하는 데 효과적입니다. 혼합 현실 환경에서 HUD는 상당한 불편함을 발생시킬 수 있으며 더 몰입적인 컨텍스트에 맞게 적응해야 합니다. 특히 사용자의 머리 방향에 단단히 고정된 HUD는 불편함을 야기할 수 있습니다. 앱에 HUD가 필요한 경우 머리 잠금 대신 *신체* 잠금을 사용하는 것이 좋습니다. 이 처리는 사용자를 통해 즉시 변환되지만 회전 임계값에 도달할 때까지 사용자의 머리로 회전하지 않는 디스플레이 세트로 구현할 수 있습니다. 이러한 회전이 수행되면 HUD에서 정보를 사용자의 시야 내에 표시하도록 방향을 설정할 수 있습니다. 사용자의 머리 모션을 기준으로 1:1 HUD 회전 및 변환을 구현하지 않도록 항상 방지해야 합니다.

## <a name="text-legibility"></a>텍스트 가독성

최적의 텍스트 가독성은 특히 HMD를 사용하는 동안 사용자가 읽어야 하는 애플리케이션 또는 시나리오에서 눈의 피로를 줄이고 사용자의 편안함을 유지하는 데 도움이 됩니다. 텍스트 가독성은 다음을 포함한 다양한 요소에 따라 달라집니다.
* 픽셀 밀도, 밝기 및 대비와 같은 디스플레이 속성 
* 색수차(chromatic aberration)와 같은 렌즈 속성
* 두께, 간격, 세리프 및 글꼴/배경색과 같은 텍스트/글꼴 속성  

일반적으로 특정 애플리케이션을 가독성에 대해 테스트하고, 편안한 환경을 위해 글꼴 크기를 가능한 한 크게 만드는 것이 좋습니다. 홀로그램 및 몰입형 디바이스에 대한 자세한 지침은 [입력 체계](typography.md) 및 [Unity의 텍스트](text-in-unity.md) 페이지에서 확인할 수 있습니다.

## <a name="holographic-frame-considerations"></a>홀로그램 프레임 고려 사항

큰 개체 또는 많은 개체가 포함된 혼합 현실 환경의 경우 콘텐츠와 상호 작용하는 데 필요한 머리와 목의 움직임에 대한 양을 고려해야 합니다. 환경에서는 머리 움직임의 측면에서 다음 세 가지 범주로 나눌 수 있습니다. 
* **가로**(옆으로)
* **세로**(위아래로)
* **몰입형**(가로 및 세로 모두)
 
가능하면 대부분의 상호 작용을 가로 또는 세로 범주로 제한합니다. 사용자의 머리가 중립 위치에 있는 동안 대부분의 환경이 홀로그램 프레임의 가운데에서 수행되는 것이 가장 좋습니다. 사용자가 보기를 자연스럽지 않은 머리 위치로 계속 이동하게 하는 상호 작용을 방지합니다(예: 항상 주요 메뉴 상호 작용에 액세스하려고 조회하는 경우).

![수평선 아래 0~35도의 최적 콘텐츠 영역](images/optimal-field-of-view-2.png)<br>
*수평선 아래 0~35도의 최적 콘텐츠 영역*

머리의 가로 움직임은 빈번하게 상호 작용하는 반면, 머리의 세로 움직임은 일반적이지 않은 이벤트에 대해 예약되어야 합니다. 예를 들어 긴 가로 타임라인이 포함되는 환경에서는 메뉴를 아래로 보는 것처럼 상호 작용에 대한 머리의 세로 움직임을 제한해야 합니다.

사용자의 공간을 중심으로 개체를 배치하여 머리만이 아니라 몸 전체를 움직이도록 하는 것이 좋습니다. 움직이는 개체 또는 큰 개체가 있는 환경은 특히 가로 축과 세로 축을 따라 자주 이동해야 하는 머리의 움직임에 특히 주의해야 합니다.

## <a name="gaze-direction"></a>시선 방향

눈과 목의 부담을 방지하려면 눈과 목의 과도한 움직임을 방지하도록 콘텐츠를 설계해야 합니다.
* **방지** 수평선 위 10도가 넘는 시선 각도(수직 이동)
* **방지** 수평선 아래 60가 넘는 시선 각도(수직 이동)
* **방지** 중심에서 45도가 넘는 목 회전(수평 이동)

특히 활동 중에 머리가 아래쪽으로 약간 기울어지는 경향이 있으므로 최적(휴식) 시선 각도를 수평선 아래 10-20도 사이로 고려합니다.

## <a name="arm-positions"></a>팔 위치

사용자가 경험하는 동안 줄곧 손을 들어야 하는 경우 근육 피로가 누적될 수 있습니다. 또한 사용자가 에어 탭 제스처를 오랫동안 반복적으로 수행하도록 요구하는 것도 지치게 할 수 있습니다. 따라서 환경에서 지속적이고 반복적인 제스처 입력을 요구하지 않도록 방지하는 것이 좋습니다. 이 목표는 짧은 휴식 시간을 마련하거나 제스처, 음성 입력을 통해 앱과의 상호 작용을 도모하여 달성 가능합니다.

## <a name="see-also"></a>참고 항목
* [응시](gaze-and-commit.md)
* [홀로그램 안정성](hologram-stability.md)
* [Instinctual 상호 작용](interaction-fundamentals.md)
* [홀로그램 프레임](holographic-frame.md)
* [조정](calibration.md)
