---
title: Unity에서 텍스트
description: Unity에서 텍스트를 표시 하는 두 가지 유형의 텍스트 구성 요소를 사용할 수 있습니다-UI 텍스트 및 텍스트를 3D 메시입니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality를 디자인, 컨트롤, ux, ui, 입력 체계, 글꼴
ms.openlocfilehash: f57b04c7d57219b7426793879004ef010d2b1ea8
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415442"
---
# <a name="text-in-unity"></a>Unity에서 텍스트

텍스트 holographic 앱의 가장 중요 한 구성 요소 중 하나입니다. Unity에서 텍스트를 표시 하는 세 가지 유형의 텍스트 구성 요소를 사용할 수 있습니다-UI 텍스트, 텍스트 3D 메시 및 텍스트 메시 Pro입니다. 기본적으로 UI 텍스트 및 텍스트를 3D 메시 흐리게 표시 되며 너무 큽니다. 선명 하 고 고품질 텍스트 HoloLens에 크기를 관리할 수 있는 몇 가지 변수를 조정 해야 합니다. UI 텍스트 및 3D 메시 텍스트 구성 요소를 사용 하는 경우 적절 한 크기를 가져오려면 배율 인수를 적용 하 여 더 나은 렌더링 품질을 얻을 수 있습니다.

![선명 하 게 하 고 뛰어난 텍스트를 가져오는 방법](images/hug-text-02-640px.png)<br>
*Unity에서 흐리게 표시 기본 텍스트*

## <a name="working-with-unitys-3d-texttext-mesh-and-ui-text"></a>Unity의 3D 텍스트 (텍스트 메시) 및 UI 텍스트 작업

Unity 장면에 추가 된 모든 새 요소 1 Unity 단위로 크기 또는 1m HoloLens에 100% 변환 확장으로 간주 합니다. 글꼴의 경우 3D TextMesh 경계 상자 높이 대 한 1 미터에는 기본적으로 제공 합니다.

![Unity의 글꼴 사용](images/640px-hug-text-03.png)<br>
*기본 Unity 3D 텍스트 (텍스트 메시) 차지 1 미터는 Unity 단위 1 개*

<br>
대부분의 비주얼 디자이너 점을 사용 하 여 실제 환경에서 글꼴 크기를 정의 합니다. 약 2835 (2,834.645666399962)는 1 미터에는 지점입니다. 13 2835 equals 0.0046 (정확 하 게 0.004586111116)로 나눈 값의 간단한 수학 지점 시스템 변환할 1m 및 13 Unity의 기본 텍스트 메시 글꼴 크기에 따라 적절 한 표준 확장을 시작 하려면 제공 (일부 할 0.005로 반올림)입니다. 텍스트 개체 또는 이러한 값에는 컨테이너를 크기 조정을 허용 하지 않습니다만 글꼴 1:1 변환 디자인 프로그램에서 크기를 지정 하지만 사용자 환경 전체에서 일관성을 유지할 수 있도록 표준 제공.

![Unity 3D 텍스트 메시 다른 글꼴 크기를 사용 하 여](images/Text_In_Unity_Measurements1.png)<br>
*Unity 3D 텍스트 및 UI 텍스트에 대 한 크기 조정 값*

![Unity 3D 텍스트 메시 다른 글꼴 크기를 사용 하 여](images/hug-text-05-1000px.png)<br>
*Unity 3D 텍스트 메시 최적화 된 값을 사용 하 여*

<br>
장면에 UI 또는 캔버스 기반된 텍스트 요소를 추가할 때 크기과 차이로 인해가 여전히 큽니다. 두 가지 크기의 차이 약 1000 %0.00046 (정확 하 게 0.0004586111116)에 기반 하는 UI 텍스트 구성 요소에 대 한 배율 인수를 전달 해 또는 0.0005 반올림된 한 값에 대 한 합니다.

![다른 동적 픽셀 단위 값 수를 사용 하 여 unity UI 텍스트](images/hug-text-04-1000px.png)<br>
*최적화 된 값을 사용 하 여 unity UI 텍스트*

<br>

>[!NOTE]
>글꼴의 기본 값을 해당 글꼴 또는 글꼴 Unity로 가져온 방법의 질감 크기에 따라 달라질 수 있습니다. 이러한 테스트는 가져온된 다른 글꼴을 하나 뿐 아니라 Unity에서 기본 Arial 글꼴에 따라 수행 되었습니다.

## <a name="working-with-text-mesh-pro"></a>텍스트를 사용 하 여 작업에는 Pro 메시

Unity의 텍스트 메시 Pro를 사용 하 여 텍스트 렌더링 품질을 보호할 수 있습니다. 사용 하 여 거리에 관계 없이 선명한 텍스트 윤곽선을 지원 합니다 [SDF (서명 거리 필드)](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf) 기법입니다. 에 사용 되는 위에 텍스트를 3D 메시 및 UI 텍스트 동일한 계산 방법을 사용 기존 인쇄 지점을 사용 하려면 적절 한 크기 조정 값을 찾을 수 있습니다. 36 크기를 사용 하 여 기본 3D 텍스트 메시 Pro 글꼴 2.5 Unity Unit(2.5m)의 경계를 보여주고, 있으므로 포인트 크기를 사용 하려면 크기 조정 값 0.005를 사용할 수 있습니다. 기본 크기의 25 Unity Unit(25m) 경계는 텍스트 메시 Pro UI 메뉴 아래에 제공이 0.0005 크기 조정 값에 대 한 합니다.

![Unity 3D 텍스트 메시 다른 글꼴 크기를 사용 하 여](images/Text_In_Unity_Measurements2.png)<br>
*Unity 3D 텍스트 및 UI 텍스트에 대 한 크기 조정 값*

## <a name="recommended-text-size"></a>권장 되는 텍스트 크기
예상할 수 있듯이 PC 또는 태블릿 장치 (일반적으로 12 – 32pt) 사이 사용 하는 형식 크기 2 미터 거리 만큼 떨어진 좁습니다 찾습니다. 각 글꼴의 특성에 다르지만 0.35°-0.4°/12.21-13.97mm 사용자 연구 조사의에 따라 권장 되는 보기 각도 및 읽기 쉽도록 코멘트가 글꼴 높이 최소는 일반적입니다. 위에 소개 된 배율 인수를 사용 하 여 35 40pt는. 

거의 상호 작용 0.45m(45cm)에 최소 읽을 수 글꼴 각도 높이 0.4 °-0.5 ° / 3.14 – 3.9 mm 합니다. 위에 소개 된 배율 인수를 사용 하 여 9 12pt는.

![가까운과 먼 상호 작용 범위](images/typography-distance-1000px.jpg)
*근처에서 콘텐츠와 먼 상호 작용 범위*

### <a name="the-minimum-legible-font-size"></a>읽을 수 있는 최소 글꼴 크기
| 거리 | 각도 | 텍스트 높이 | 글꼴 크기 |
|---------|---------|---------|---------|
| 45 cm (직접 조작 거리) | 0.4°-0.5° | 3.14–3.9mm | 8.9–11.13pt |
| 2m | 0.35°-0.4° | 12.21 – 13.97 mm | 34.63-39.58pt |


### <a name="the-comfortably-legible-font-size"></a>편안 하 게 읽을 수 글꼴 크기
| 거리 | 각도 | 텍스트 높이 | 글꼴 크기 |
|---------|---------|---------|---------|
| 45 cm (직접 조작 거리) | 0.65°-0.8° | 5.1-6.3mm | 14.47-17.8pt |
| 2m | 0.6°-0.75° | 20.9-26.2mm | 59.4-74.2pt |

Segoe UI (Windows에 대 한 기본 글꼴) 대부분의 경우 잘 작동합니다. 그러나 씬 세로 스트로크는 진동 이므로 가독성을 저하 시킵니다 작은 크기로 light 또는 semi 밝은 글꼴 패밀리를 사용 하지 마십시오. 충분 한 스트로크 두께 사용 하 여 최신 글꼴 잘 작동 합니다. 예를 들어, Helvetica Arial 멋진 확인 및 일반 또는 굵게 표시 된 가중치를 사용 하 여 HoloLens에 매우 읽을 수 있습니다.


![시야각](images/Text_In_Unity_ViewingAngle.jpg)
*거리, 각도 및 텍스트 높이 보기*

## <a name="sharp-text-rendering-quality-with-proper-dimension"></a>적절 한 치수를 사용 하 여 텍스트 렌더링 품질을 정확한

이 배율은 따라 만들었습니다 [UI 텍스트 및 텍스트를 3D 메시를 사용 하 여 텍스트 prefabs](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text)합니다. 개발자는 정확한 텍스트와 일관 된 글꼴 크기를 가져오려면 이러한 prefabs를 사용할 수 있습니다.

![적절 한 치수를 사용 하 여 텍스트 렌더링 품질을 정확한](images/hug-text-06-1000px.png)<br>
*적절 한 치수를 사용 하 여 텍스트 렌더링 품질을 정확한*

## <a name="shader-with-occlusion-support"></a>폐색 지원과 셰이더

Unity의 기본 글꼴 재질 폐색을 지원 하지 않습니다. 이 때문에 기본적으로 텍스트 개체 뒤에 표시 됩니다. 간단한 포함 되어 있습니다 [셰이더를 폐색 지](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/StandardAssets/Shaders/Text3DShader.shader)합니다. 아래 이미지는 기본 글꼴 재질 (왼쪽)를 사용 하 여 텍스트 및 적절 한 폐색 (오른쪽)를 사용 하 여 텍스트를 보여 줍니다.

![폐색 지원과 셰이더](images/hug-text-07-1000px.png)<br>
*폐색 지원과 셰이더*


## <a name="see-also"></a>참조
* [텍스트 Prefab은 MRTK에서](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text)
* [입력 체계](typography.md)

 
