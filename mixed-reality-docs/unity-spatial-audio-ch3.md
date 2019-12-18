---
title: 공간 오디오 자습서-3. 비디오에서 Spatializing 오디오
description: 비디오 자산을 Unity 프로젝트로 가져오고 비디오에서 오디오를 spatialize.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens2, 공간 오디오
ms.openlocfilehash: 1e5c84fd7d14cc5edc78839bbdf91590cc7fd8e7
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182750"
---
# <a name="spatializing-audio-from-a-video"></a>비디오에서 Spatializing 오디오
HoloLens 2 Unity 자습서의 공간 오디오 모듈의이 세 번째 챕터에서는 다음을 수행 합니다.
* 비디오 가져오기 및 비디오 플레이어 추가
* Quadrangle 비디오 재생
* 비디오에서 quadrangle로 오디오 라우팅 및 오디오 spatialize

## <a name="import-a-video-and-add-a-video-player"></a>비디오 가져오기 및 비디오 플레이어 추가

비디오 파일을 Unity 프로젝트의 **프로젝트** 창으로 끌어 놓습니다. 공간 오디오 샘플 프로젝트에서 [이 비디오](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) 를 사용할 수 있습니다.

![비디오를 사용 하는 자산 폴더](images/spatial-audio/assets-folder-with-video.png)

비디오 클립의 품질 설정을 조정 하면 HoloLens 2에서 부드러운 재생을 보장할 수 있습니다. **프로젝트** 창에서 비디오 파일을 클릭 합니다. 그런 다음, 비디오 파일의 **검사기** 창에서 Windows 스토어 앱에 대 한 설정을 재정의 하 고 다음을 수행 합니다.
* **트랜스 코딩** 사용
* **코덱을** H264로 설정
* **비트 전송률 모드** 를 낮음으로 설정
* **공간 품질** 을 보통 공간 품질로 설정

이러한 조정 후 비디오 파일의 **검사기** 창은 다음과 같이 표시 됩니다.

![비디오 속성 창](images/spatial-audio/video-property-pane.png)

그런 다음 **계층** 창을 마우스 오른쪽 단추로 클릭 하 고 비디오 **-> 비디오 플레이어**를 선택 하 여 **계층** 에 **비디오 플레이어** 개체를 추가 합니다.

![계층의 비디오 플레이어](images/spatial-audio/video-player-in-hierarchy.png)

## <a name="play-video-onto-a-quadrangle"></a>Quadrangle 비디오 재생
**비디오 플레이어** 개체에는 비디오를 렌더링할 질감 게임 개체가 필요 합니다. 먼저 **계층** 창을 마우스 오른쪽 단추로 클릭 하 고 **3d 개체-> 쿼드**를 선택 하 여 **계층 구조** 에 **쿼드** 를 추가 합니다.

![계층에 쿼드 추가](images/spatial-audio/add-quad-to-hierarchy.png)

응용 프로그램이 시작 될 때 사용자 앞에 **쿼드** 가 표시 되도록 하려면 **쿼드** 의 **Position** 속성을 (0, 0, 2)로 설정 하 고 **Scale** 속성을 (1.28, 0.72, 1)로 설정 합니다. 이러한 변경을 수행한 후에는 해당 **쿼드** 의 **검사기** 창에 있는 **변형** 구성 요소가 다음과 같이 표시 됩니다.

![쿼드 변형](images/spatial-audio/quad-transform.png)

비디오를 사용 하 여 **쿼드** 을 텍스처 하려면 새 **렌더링 질감**을 만듭니다. **프로젝트** 창에서 마우스 오른쪽 단추를 클릭 하 고 **만들기-> 텍스처 렌더링**을 선택 합니다.

![렌더링 질감 만들기](images/spatial-audio/create-render-texture.png)

**렌더링 질감**의 **검사기** 창에서 **Size** 속성을 비디오의 1280x720에 대 한 기본 해상도와 일치 하도록 설정 합니다. 그러면 HoloLens 2에서 최적의 렌더링 성능을 보장 하기 위해 **깊이 버퍼** 속성을 **16 비트**수준 이상으로 설정 합니다. 이러한 설정 후에는 **렌더링 질감** 에 대 한 **검사기** 창이 다음과 같이 표시 됩니다.

![질감 속성 렌더링](images/spatial-audio/render-texture-properties.png)

다음으로, 새 **렌더링 질감** 을 **쿼드**의 질감으로 사용 합니다.
1. **프로젝트** 창에서 **렌더링 텍스처** 를 **계층 구조의** **쿼드** 로 끌어 옵니다.
2. HoloLens 2에 대 한 좋은 성능을 보장 하려면 **쿼드**의 **검사기** 창에서 **Mixed Reality Toolkit Standard 셰이더**를 선택 합니다.

이러한 설정을 사용 하는 경우 **쿼드** 의 **검사기** 창에 있는 **텍스처** 구성 요소는 다음과 같습니다.

![쿼드 질감 속성](images/spatial-audio/quad-texture-properties.png)

비디오 클립을 재생 하기 위해 새 **비디오 플레이어** 를 설정 하 고 **질감을 렌더링** 하려면 **비디오 플레이어** 의 **검사기** 창을 열고 다음을 수행 합니다.
* 비디오 **클립** 속성을 비디오 파일로 설정 합니다.
* **루프** 확인란을 선택 합니다.
* **대상 질감** 을 새 렌더링 질감으로 설정

이제 **비디오 플레이어** 에 대 한 **검사기** 창이 다음과 같이 표시 됩니다.

![비디오 플레이어 속성](images/spatial-audio/video-player-properties.png)

## <a name="spatialize-the-audio-from-the-video"></a>비디오에서 오디오 Spatialize
**4**의 **검사기** 창에서 비디오에서 오디오를 라우팅할 **오디오 소스** 를 만듭니다.
* 창 맨 아래에 있는 **구성 요소 추가** 를 클릭 합니다.
* **오디오 소스** 추가

그런 다음 **오디오 원본**에서 다음을 수행 합니다.
* **출력** 을 믹서로 설정
* **Spatialize** 상자를 선택 합니다.
* **공간 Blend** 슬라이더를 1 (3d)로 이동

이러한 변경 후에는 **4 개의** **검사기** 창에 있는 **오디오 원본** 구성 요소가 다음과 같이 표시 됩니다.

![쿼드 오디오 원본 검사기](images/spatial-audio/quad-audio-source-inspector.png)

**쿼드**에서 오디오 **소스로** 오디오를 라우팅하도록 **비디오 플레이어** 를 설정 하려면 **비디오 플레이어** 의 **검사기** 창을 열고 다음을 수행 합니다.
* **오디오 출력 모드** 를 ' 오디오 원본 '으로 설정 합니다.
* **오디오 원본** 속성을 쿼드로 설정 합니다.

이러한 변경 후에는 **비디오 플레이어** 에 대 한 **검사기** 창이 다음과 같이 표시 됩니다.

![비디오 플레이어에서 오디오 원본 설정](images/spatial-audio/video-player-set-audio-source.png)

## <a name="next-steps"></a>다음 단계
HoloLens 2 또는 Unity 편집기에서 앱을 사용해 보세요. 비디오를 보고 듣고 비디오에서 오디오가 spatialized 됩니다.

단추를 사용 하 여 런타임에 spatialization를 사용 하거나 사용 하지 않도록 설정 하려면 [4 챕터](unity-spatial-audio-ch4.md) 로 계속 진행 합니다.

