---
title: 공간 오디오 자습서-2. Spatializing button 상호 작용 소리
description: 프로젝트에 단추를 추가 하 고 단추 상호 작용 소리를 spatialize.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens2, 공간 오디오
ms.openlocfilehash: bd70e3bc88ee39b2c6257089ac3a2b93dfae0ad1
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182780"
---
# <a name="spatializing-button-interaction-sounds"></a>Spatializing button 상호 작용 소리

## <a name="objectives"></a>목표
HoloLens 2 자습서의 공간 오디오 모듈의이 두 번째 장에서는 다음을 수행 합니다.
* 단추 추가
* 단추 클릭 소리 Spatialize

## <a name="add-a-button"></a>단추 추가
**프로젝트** 창에서 **자산** 을 선택 하 고 검색 표시줄에 "PressableButtonHoloLens2"를 입력 합니다.

![자산에서 prefab 단추](images/spatial-audio/button-prefab-in-assets.png)

Prefab 단추는 흰색 아이콘이 아니라 파란색 아이콘으로 표시 되는 항목입니다. **PressableButtonHoloLens2** 라는 Prefab을 **계층** 창으로 끌어옵니다. 새 단추의 **검사기** 창에서 **위치** 속성을 (0,-0.4, 2)로 설정 하 여 응용 프로그램이 시작 될 때 사용자 앞에 표시 되도록 합니다. 단추의 **변환** 구성 요소는 다음과 같습니다.

![단추 변형](images/spatial-audio/button-transform.png)

## <a name="spatialize-button-feedback"></a>Spatialize 단추 피드백
이 단계에서는 단추에 대 한 오디오 피드백을 spatialize 합니다. 관련 디자인 제안 사항은 [공간 음향 디자인](spatial-sound-design.md)을 참조 하세요. 

오디오 **믹서** 창에서는 오디오 **원본** 구성 요소에서 오디오 재생을 위해 **믹서 그룹**이라는 대상을 정의할 수 있습니다. 
* **창 > 오디오-> 오디오 믹서** 를 사용 하 여 메뉴 모음에서 **오디오 믹서** 창을 엽니다.
* **Mixers**옆의 ' + '를 클릭 하 여 **믹서** 를 만듭니다. 새 믹서에는 **Master**라는 기본 **그룹이** 포함 됩니다.

이제 **믹서** 창이 다음과 같이 표시 됩니다.

![첫 번째 믹서가 있는 믹서 패널](images/spatial-audio/mixer-panel-with-first-mixer.png)

> [!NOTE]
> [5 장](unity-spatial-audio-ch5.md)에서 반향를 사용 하도록 설정할 때까지 믹서의 볼륨 미터는 Microsoft Spatializer을 통해 재생 된 소리에 대 한 활동을 표시 하지 않습니다.

**계층** 창에서 **PressableButtonHoloLens2** 를 클릭 합니다. **검사기** 창에서 다음을 수행 합니다.
1. **오디오 원본** 구성 요소 찾기
2. **출력** 속성의 경우 선택기를 클릭 하 고 믹서를 선택 합니다.
3. **Spatialize** 확인란을 선택 합니다.
4. **공간 Blend** 슬라이더를 3d (1)로 이동 합니다.

> [!NOTE]
> 2019 이전의 Unity 버전에서 ' Spatialize ' 확인란은 **오디오 소스**에 대 한 **검사기** 창의 아래쪽에 있습니다.

이러한 변경 후 **PressableButtonHoloLens2** 의 **오디오 원본** 구성 요소는 다음과 같습니다.

![오디오 원본 단추](images/spatial-audio/button-audio-source.png)

> [!NOTE]
> **Spatialize** 확인란을 선택 하지 않고 **공간 Blend** 를 1 (3d)로 이동 하는 경우 Unity는 **Microsoft spatializer** with hrtfs 대신 패닝 spatializer를 사용 합니다.

## <a name="adjust-the-volume-curve"></a>볼륨 곡선 조정
기본적으로 Unity는 수신기에서 더 멀리 경우 spatialized 소리를 표시 합니다. 이 감쇠가 상호 작용 피드백 소리에 적용 되 면 인터페이스를 사용 하기가 더 어려울 수 있습니다.

이 감쇠를 사용 하지 않도록 설정 하려면 **볼륨** 곡선을 조정 합니다. **PressableButtonHoloLens2**에 대 한 **검사기** 창의 **오디오 원본** 구성 요소에는 **3d 소리 설정**이라는 섹션이 있습니다. 해당 섹션에서 다음을 수행 합니다.
1. **Volume Rolloff** 속성을 Linear로 설정 합니다.
2. Y 축의 ' 0 '에서 ' 1 '까지 **볼륨** 곡선 (빨간색 곡선)의 끝점을 끕니다.
3. **볼륨** 곡선의 모양을 평면으로 조정 하려면 흰색 곡선 셰이프 컨트롤을 X 축에 평행으로 끌어 놓습니다.

이러한 변경 후에는 **PressableButtonHoloLens2** **오디오 원본** 속성의 **3d 사운드 설정** 섹션이 다음과 같이 표시 됩니다.

![3D 소리 설정 단추](images/spatial-audio/button-3d-sound-settings.png)

## <a name="next-steps"></a>다음 단계

HoloLens 2 또는 Unity 편집기에서 앱을 사용해 보세요. 앱에서 단추를 터치 하 고 spatialized 단추 상호 작용 소리를 들 수 있습니다.

Unity 편집기에서 테스트 하는 경우 스페이스바를 눌러 스크롤 휠을 눌러 직접 시뮬레이션을 활성화 합니다. 자세한 내용은 [Mrtk 설명서](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)를 참조 하세요.

[3 장으로](unity-spatial-audio-ch3.md) 이동 하 여 앱에 비디오를 추가 하 고 비디오에서 오디오를 spatialize.

