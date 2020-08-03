---
title: Unity의 텍스트
description: Unity에 텍스트를 표시 하기 위해 사용할 수 있는 텍스트 구성 요소에는 UI 텍스트와 3D 텍스트 메시의 두 가지 유형이 있습니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality, 디자인, 컨트롤, 글꼴, 입력 체계, ui, ux
ms.openlocfilehash: 63f0992a4623cf91c1b9c62c4ebf30de12529515
ms.sourcegitcommit: ef0bf03833eda826ed0b884859b4573775112aba
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2020
ms.locfileid: "87476945"
---
# <a name="text-in-unity"></a>Unity의 텍스트

텍스트는 holographic apps에서 가장 중요 한 구성 요소 중 하나입니다. Unity에 텍스트를 표시 하기 위해 사용할 수 있는 텍스트 구성 요소에는 UI 텍스트, 3D 텍스트 메시 및 텍스트 메시 Pro의 세 가지 유형이 있습니다. 기본적으로 UI 텍스트 및 3D 텍스트 메시는 흐리게 표시 되 고 너무 큽니다. HoloLens에서 크기를 관리할 수 있는 선명한 고품질 텍스트를 얻으려면 몇 가지 변수를 조정 해야 합니다. UI 텍스트 및 3D 텍스트 메시 구성 요소를 사용할 때 크기 조정 요소를 적용 하 여 적절 한 차원을 얻으려면 렌더링 품질을 향상 시킬 수 있습니다.

![선명 하 고 멋진 텍스트를 얻는 방법](images/hug-text-02-640px.png)<br>
*Unity의 흐린 기본 텍스트*

## <a name="working-with-unitys-3d-text-text-mesh-and-ui-text"></a>Unity의 3D 텍스트 (텍스트 메시) 및 UI 텍스트 작업

Unity는 장면에 추가 된 모든 새 요소가 1 개의 Unity 단위 또는 100% transform 배율 (HoloLens의 약 1 미터) 이라고 가정 합니다. 글꼴의 경우 3D TextMesh의 경계 상자는 기본적으로 높이의 약 1 미터에 제공 됩니다.

![Unity에서 글꼴 작업](images/640px-hug-text-03.png)<br>
*기본 Unity 3D 텍스트 (텍스트 메시)는 1 측정기 인 1 개의 Unity 단위를 차지 합니다.*

<br>
대부분의 비주얼 디자이너는 요소를 사용 하 여 실제 세계의 글꼴 크기를 정의 합니다. 1 미터에 약 2835 (2, 834.645666399962) 점이 있습니다. 1 미터에 대 한 시점 시스템 변환과 Unity의 기본 텍스트 메시 글꼴 크기 13을 기반으로 하는 간단한 수학 13은 0.0046 2835 (정확 하 게 0.004586111116)로 시작 하는 데 적합 한 표준 배율을 제공 합니다 (일부는 0.005로 반올림). 텍스트 개체 또는 컨테이너를 이러한 값으로 크기를 조정 하면 디자인 프로그램에서 글꼴 크기를 1:1으로 변환할 수 있을 뿐만 아니라 사용자 환경 전체에서 일관성을 유지할 수 있도록 표준도 제공 됩니다.

![다른 글꼴 크기를 사용 하는 Unity 3D 텍스트 메시](images/Text_In_Unity_Measurements1.png)<br>
*Unity 3D 텍스트 및 UI 텍스트에 대 한 값 크기 조정*

<br>

![다른 글꼴 크기를 사용 하는 Unity 3D 텍스트 메시](images/hug-text-05-1000px.png)<br>
*최적화 된 값이 있는 Unity 3D 텍스트 메시*

<br>
장면에 UI 또는 canvas 기반 텍스트 요소를 추가 하는 경우 차이가 크기는 더 커집니다. 두 크기의 차이점은 약 1000% 이며,이는 UI 기반 텍스트 구성 요소에 대 한 배율 인수를 0.00046 (정확 하 게 0.0004586111116) 또는 0.0005 (반올림 된 값)로 가져오는 것입니다.

![단위 값 마다 다른 동적 픽셀이 있는 Unity UI 텍스트](images/hug-text-04-1000px.png)<br>
*최적화 된 값이 있는 Unity UI 텍스트*

<br>

>[!NOTE]
>글꼴의 기본값은 해당 글꼴의 질감 크기 또는 해당 글꼴을 Unity로 가져온 방법의 영향을 받을 수 있습니다. 이러한 테스트는 Unity의 기본 Arial 글꼴 및 가져온 다른 글꼴을 기반으로 수행 되었습니다.

## <a name="working-with-text-mesh-pro"></a>텍스트 메시 Pro 작업

Unity의 텍스트 메시 Pro를 사용 하 여 텍스트 렌더링 품질을 보호할 수 있습니다. 이는 [사인 된 거리 필드 (.sdf)](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf) 기법을 사용 하는 거리에 관계 없이 선명한 텍스트 윤곽선을 지원 합니다. 3D 텍스트 메시 및 UI 텍스트에 대해 위에서 사용한 것과 동일한 계산 방법을 사용 하 여 기존 입력 점에 사용할 적절 한 크기 조정 값을 찾을 수 있습니다. 크기가 36 인 기본 3D 텍스트 메시 Pro 글꼴의 경계 크기는 2.5 Unity 단위 (2.5 m) 이므로 크기 조정 0.005 값을 사용 하 여 포인트 크기를 가져올 수 있습니다. UI 메뉴 아래의 텍스트 메시 Pro는 기본 경계 크기인 25 개 Unity 단위 (25m)를 갖습니다. 크기 조정 값에 대해 0.0005을 제공 합니다.

![다른 글꼴 크기를 사용 하는 Unity 3D 텍스트 메시](images/Text_In_Unity_Measurements2.png)<br>
*Unity 3D 텍스트 및 UI 텍스트에 대 한 값 크기 조정*

## <a name="recommended-text-size"></a>권장 텍스트 크기
짐작할 수 있듯이, PC 또는 태블릿 장치에서 사용 하는 형식 크기 (일반적으로 12 – 32pt 사이)는 2 미터 거리에서 매우 작게 보입니다. 각 글꼴의 특성에 따라 달라 지지만 일반적으로 권장 되는 최소 보기 각도와 가독성을 위한 글꼴 높이는 사용자 연구 연구를 기반으로 하는 0.35 °-0.4 °/12.21-13.97mm을 중심으로 합니다. 위에서 소개한 배율 인수를 사용 하는 약 35-40pt입니다. 

0.45 m (45cm)에서 거의 상호 작용 하는 경우 읽을 수 있는 최소 글꼴의 보기 각도와 높이는 0.4 °-0.5 °/3.14 – 3.9 mm입니다. 위에서 소개한 크기 조정 인수를 사용 하 여 약 9-12pt입니다.

![](images/typography-distance-1000px.jpg)
*근거리 및 원거리 상호 작용 범위 콘텐츠 (근거리 및 원거리* 상호 작용 범위)

### <a name="the-minimum-legible-font-size"></a>읽을 때 최소 글꼴 크기
| 거리 | 시야각 | 텍스트 높이 | 글꼴 크기 |
|---------|---------|---------|---------|
| 45cm (직접 조작 거리) | 0.4 °-0.5 ° | 3.14 – 3.9 mm | 8.9 – 11.13 pt |
| 2m | 0.35 °-0.4 ° | 12.21 – 13.97 mm | 34.63-39.58 pt |


### <a name="the-comfortably-legible-font-size"></a>편안 하 게 읽을 때의 글꼴 크기
| 거리 | 시야각 | 텍스트 높이 | 글꼴 크기 |
|---------|---------|---------|---------|
| 45cm (직접 조작 거리) | 0.65 °-0.8 ° | 5.1-6.3 mm | 14.47-17.8 pt |
| 2m | 0.6 °-0.75 ° | 20.9-26.2 mm | 59.4-74.2 pt |

맑은 고딕 (Windows의 기본 글꼴)은 대부분의 경우 잘 작동 합니다. 그러나 밝은 수직선을 진동 하 고 가독성을 저하 시킬 수 있으므로 작은 크기로 밝은 색 또는 반투명 글꼴 패밀리를 사용 하지 마십시오. 스트로크 두께가 충분 한 최신 글꼴이 제대로 작동 합니다. 예를 들어 Helvetica 및 Arial은 멋진 하 고 일반 또는 굵게 가중치를 사용 하 여 HoloLens에서 매우 읽을 수 있습니다.


![각도 보기 ](images/Text_In_Unity_ViewingAngle.jpg)
 *거리, 각도 및 텍스트 높이* 보기

## <a name="text-with-mixed-reality-toolkit-v2"></a>Mixed Reality Toolkit v 2를 사용 하는 텍스트

### <a name="sharp-text-rendering-quality-with-proper-dimension"></a>적절 한 차원의 선명한 텍스트 렌더링 품질

이러한 크기 조정 요소에 따라 [UI 텍스트 및 3D 텍스트 메시를 사용 하 여 텍스트 prefabs](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Prefabs/Text)를 만들었습니다. 개발자는 이러한 prefabs를 사용 하 여 선명한 텍스트와 일관 된 글꼴 크기를 가져올 수 있습니다.

![적절 한 차원의 선명한 텍스트 렌더링 품질](images/hug-text-06-1000px.png)<br>
*적절 한 차원의 선명한 텍스트 렌더링 품질*

### <a name="shader-with-occlusion-support"></a>폐색가 지원 되는 셰이더

Unity의 기본 글꼴 재질은 폐색를 지원 하지 않습니다. 이로 인해 기본적으로 개체 뒤에 텍스트가 표시 됩니다. [폐색를 지 원하는 간단한 셰이더](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MRTK/Core/StandardAssets/Shaders/Text3DShader.shader)를 포함 했습니다. 아래 이미지는 기본 글꼴 재질 (왼쪽) 및 적절 한 폐색 (오른쪽) 텍스트가 포함 된 텍스트를 보여 줍니다.

![폐색가 지원 되는 셰이더](images/hug-text-07-1000px.png)<br>
*폐색가 지원 되는 셰이더*


## <a name="see-also"></a>참고 항목
* [MRTK의 텍스트 Prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Prefabs/Text)
* [입력 체계](typography.md)

 
