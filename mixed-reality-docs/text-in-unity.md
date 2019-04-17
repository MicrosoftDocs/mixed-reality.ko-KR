---
title: Unity에서 텍스트
description: Unity에서 텍스트를 표시 하는 두 가지 유형의 텍스트 구성 요소를 사용할 수 있습니다-UI 텍스트 및 텍스트를 3D 메시입니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality를 디자인, 컨트롤, ux, ui, 입력 체계, 글꼴
ms.openlocfilehash: 02f282ab80a44190d21d2dadefeb7a624c862d04
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603673"
---
# <a name="text-in-unity"></a>Unity에서 텍스트

텍스트 holographic 앱의 가장 중요 한 구성 요소 중 하나입니다. Unity에서 텍스트를 표시 하는 두 가지 유형의 텍스트 구성 요소를 사용할 수 있습니다-UI 텍스트 및 텍스트를 3D 메시입니다. 기본적으로 이러한 희미하게 보일 않으며 너무 큽니다. 선명 하 고 고품질 텍스트 HoloLens에 크기를 관리할 수 있는 몇 가지 변수를 조정 해야 합니다. UI 텍스트 및 3D 메시 텍스트 구성 요소를 사용 하는 경우 적절 한 크기를 가져오려면 배율 인수를 적용 하 여 더 나은 렌더링 품질을 얻을 수 있습니다.

![선명 하 게 하 고 뛰어난 텍스트를 가져오는 방법](images/hug-text-02-640px.png)<br>
*Unity에서 흐리게 표시 기본 텍스트*

## <a name="working-with-fonts-in-unity"></a>Unity의 글꼴 사용

Unity 장면에 추가 된 모든 새 요소 1 Unity 단위로 크기 또는 1m HoloLens에 100% 변환 확장으로 간주 합니다. 글꼴의 경우 3D TextMesh 경계 상자 높이 대 한 1 미터에는 기본적으로 제공 합니다.

![Unity의 글꼴 사용](images/640px-hug-text-03.png)<br>
*기본 Unity 텍스트 1 미터는 1 Unity 단위를 차지 합니다.*

<br>
대부분의 비주얼 디자이너 점을 사용 하 여 실제 환경에서 글꼴 크기를 정의 합니다. 약 2835 (2,834.645666399962)는 1 미터에는 지점입니다. 13 2835 equals 0.0046 (정확 하 게 0.004586111116)로 나눈 값의 간단한 수학 지점 시스템 변환할 1m 및 13 Unity의 기본 텍스트 메시 글꼴 크기에 따라 적절 한 표준 확장을 시작 하려면 제공 (일부 할 0.005로 반올림)입니다. 텍스트 개체 또는 이러한 값에는 컨테이너를 크기 조정을 허용 하지 않습니다만 글꼴 1:1 변환 디자인 프로그램에서 크기를 조정 하지만 응용 프로그램 또는 게임 전체에서 일관성을 유지할 수 있도록 표준 제공.

![Unity 3D 텍스트 메시 다른 글꼴 크기를 사용 하 여](images/hug-text-05-1000px.png)<br>
*Unity 3D 텍스트 메시 최적화 된 값을 사용 하 여*

<br>
장면에 UI 또는 캔버스 기반된 텍스트 요소를 추가할 때 크기과 차이로 인해가 여전히 큽니다. 두 가지 크기의 차이 약 1000 %0.00046 (정확 하 게 0.0004586111116)에 기반 하는 UI 텍스트 구성 요소에 대 한 배율 인수를 전달 해 또는 0.0005 반올림된 한 값에 대 한 합니다.

![다른 동적 픽셀 단위 값 수를 사용 하 여 unity UI 텍스트](images/hug-text-04-1000px.png)<br>
*최적화 된 값을 사용 하 여 unity UI 텍스트*

<br>

>[!NOTE]
>글꼴의 기본 값을 해당 글꼴 또는 글꼴 Unity로 가져온 방법의 질감 크기에 따라 달라질 수 있습니다. 이러한 테스트는 가져온된 다른 글꼴을 하나 뿐 아니라 Unity에서 기본 Arial 글꼴에 따라 수행 되었습니다.

## <a name="sharp-text-rendering-quality-with-proper-dimension"></a>적절 한 치수를 사용 하 여 텍스트 렌더링 품질을 정확한

이 배율은 따라 만들었습니다 [두 prefabs-UI 텍스트 및 텍스트를 3D 메시](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/UX/Prefabs)합니다. 개발자는 정확한 텍스트와 일관 된 글꼴 크기를 가져오려면 이러한 prefabs를 사용할 수 있습니다.

![적절 한 치수를 사용 하 여 텍스트 렌더링 품질을 정확한](images/hug-text-06-1000px.png)<br>
*적절 한 치수를 사용 하 여 텍스트 렌더링 품질을 정확한*

## <a name="shader-with-occlusion-support"></a>폐색 지원과 셰이더

Unity의 기본 글꼴 재질 폐색을 지원 하지 않습니다. 이 때문에 기본적으로 텍스트 개체 뒤에 표시 됩니다. 간단한 포함 되어 있습니다 [셰이더를 폐색 지](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/UX/Shaders)합니다. 아래 이미지는 기본 글꼴 재질 (왼쪽)를 사용 하 여 텍스트 및 적절 한 폐색 (오른쪽)를 사용 하 여 텍스트를 보여 줍니다.

![폐색 지원과 셰이더](images/hug-text-07-1000px.png)<br>
*폐색 지원과 셰이더*

## <a name="recommended-type-size"></a>권장 되는 형식 크기

예상할 수 있듯이 PC 또는 태블릿 장치 (일반적으로 12 – 32pt) 사이 사용 하는 형식 크기 2 미터 거리 만큼 떨어진 좁습니다 찾습니다. 각 글꼴의 특징에 따라 다르겠지요 이지만 일반적 스트로크 진동 없이 쉽게 읽을 수 있도록 권장 되는 최소 문자 크기 30pt, 위에 소개 된 배율에 따라 해결 합니다. 가까운 거리에 사용할 할 앱을 더 작은 형식 크기 사용할 수 있습니다. 글꼴 선택, Segoe UI (Windows에 대 한 기본 글꼴) 대부분의 경우 잘 작동합니다. 그러나 씬 세로 스트로크는 진동 이므로 가독성을 저하 됩니다 42pt 아래 형식 크기에 대 한 조명 또는 semi 밝은 글꼴을 사용 하지 마십시오. 충분 한 스트로크 두께 사용 하 여 최신 글꼴 잘 작동 합니다. 예를 들어, Helvetica Arial 멋진 확인 및 일반 또는 굵게 표시 된 가중치를 사용 하 여 HoloLens에 매우 읽을 수 있습니다.

![권장 되는 형식 크기](images/hug-text-08-1000px.png)<br>
*Type 진입 예제*

## <a name="see-also"></a>참조
* [텍스트 Prefab은 MixedRealityToolkit에서](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/UX/Prefabs)
* [샘플 텍스트 레이아웃 prefab 및 장면](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX/Scenes)
* [Typography](typography.md)

 
