---
title: Unreal의 공간 오디오
description: Unreal 엔진용 공간 오디오 플러그 인에 대한 개요입니다.
author: hferrone
ms.author: v-haferr
ms.date: 06/15/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, 스트리밍, 원격, 혼합 현실, 개발, 시작, 기능, 새 프로젝트, 에뮬레이터, 설명서, 가이드, 특징, 홀로그램, 게임 개발
ms.openlocfilehash: 404aaec7b618e951ad69c02e7aaef80e42d31dbd
ms.sourcegitcommit: 5612e8bfb9c548eac42182702cec87b160efbbfe
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85446814"
---
# <a name="spatial-audio-in-unreal"></a>Unreal의 공간 오디오

## <a name="overview"></a>개요

시각과 달리 인간은 360도 서라운드 사운드로 들을 수 있습니다. 공간 음향은 인간의 청력이 작동하는 방식을 에뮬레이트하여 세계 좌표 공간에서의 소리 위치를 식별하는 데 필요한 신호를 제공합니다. 공간 음향을 혼합 현실 애플리케이션에 추가하면 사용자가 경험하는 몰입도가 높아집니다.  

고품질 공간 음향 처리는 복잡하므로 HoloLens 2에는 이러한 소리 개체를 처리하기 위한 전용 하드웨어가 제공됩니다.  이 하드웨어 처리 지원에 액세스하려면 먼저 **MicrosoftSpatialSound** 플러그 인을 Unreal 프로젝트에 설치해야 합니다. 이 문서에서는 해당 플러그 인을 설치하고 구성하는 과정을 안내하고, Unreal 엔진에서 공간 음향을 사용하는 데 필요한 더 자세한 리소스를 소개합니다. 

## <a name="installing-the-microsoft-spatial-sound-plugin"></a>MicrosoftSpatialSound 플러그 인 설치 

공간 음향을 프로젝트에 추가하는 첫 번째 단계는 MicrosoftSpatialSound 플러그 인을 설치하는 것이며, 이 플러그 인은 다음을 수행하여 찾을 수 있습니다. 

1. **편집 > 플러그 인**을 차례로 클릭하고, 검색 상자에서 **MicrosoftSpatialSound**를 검색합니다. 
2. **MicrosoftSpatialSound** 플러그 인에서 **사용** 확인란을 선택합니다. 
3. 플러그 인 페이지에서 **지금 다시 시작**을 선택하여 Unreal 편집기를 다시 시작합니다. 

> [!NOTE]
> 아직 설치하지 않은 경우 Unreal 자습서 시리즈의 **[프로젝트 초기화](unreal-uxt-ch2.md)** 섹션에 있는 지침에 따라 **Microsoft Windows Mixed Reality** 및 **HoloLens** 플러그 인을 설치해야 합니다.

![Unreal 공간 오디오 플러그 인](images/unreal-spatial-audio-img-01.png)

편집기가 다시 시작되면 프로젝트가 모두 설정됩니다.


## <a name="setting-the-spatialization-plugin-for-hololens-2-platform"></a>HoloLens 2 플랫폼용 공간화 플러그 인 설정
공간화 플러그 인은 플랫폼별로 구성됩니다.  다음을 수행하여 HoloLens 2용 MicrosoftSpatialSound 플러그 인을 사용하도록 설정할 수 있습니다.
1. **편집 > 프로젝트 설정**을 차례로 선택하고, **플랫폼**으로 스크롤하여 **HoloLens**를 클릭합니다.
2. **오디오** 속성을 펼치고, **공간화 플러그 인** 필드를 **MicrosoftSpatialSound**로 설정합니다.

![HoloLens 플랫폼용 공간화 플러그 인](images/unreal-spatial-audio-img-02.png)

데스크톱 PC의 Unreal 편집기에서 애플리케이션을 미리 보려면 **Windows** 플랫폼에 대해 위의 단계를 반복해야 합니다.

![Windows 플랫폼용 공간화 플러그 인](images/unreal-spatial-audio-img-05.png)

## <a name="enabling-spatial-audio-on-your-workstation"></a>워크스테이션에서 공간 오디오 사용
데스크톱 버전의 Windows에서는 기본적으로 공간 오디오를 사용하지 않도록 설정되어 있습니다. 다음을 수행하여 이를 사용하도록 설정할 수 있습니다.
* 작업 표시줄에서 마우스 오른쪽 단추로 **볼륨** 아이콘을 클릭합니다. 
    + HoloLens 2에서 듣는 콘텐츠를 가장 잘 표현하려면 **공간 음향 -> 헤드폰용 Windows Sonic**을 차례로 선택합니다.

![공간화 플러그 인](images/unreal-spatial-audio-img-04.png)

> [!NOTE]
>이 설정은 Unreal 편집기에서 프로젝트를 테스트하려는 경우에만 필요합니다.

## <a name="creating-attenuation-objects"></a>감쇠 개체 만들기
필요한 플러그 인이 설치되고 구성되면 다음을 수행합니다.
1. **행위자 배치** 창에서 **주변 소리** 행위자를 검색하여 **장면** 창으로 끕니다.

![주변 소리 행위자 추가](images/unreal-spatial-audio-img-07.png)

2. **주변 소리** 행위자를 장면에서 시각적 요소의 자식으로 만듭니다. 
    * 주변 소리 행위자는 기본적으로 시각적 표현을 제공하지 않으므로 장면의 위치에서 소리만 들을 수 있습니다. 시각적 요소에 연결하면 다른 자산처럼 행위자를 보고 이동할 수 있습니다.

3.  마우스 오른쪽 단추로 **콘텐츠 브라우저**를 클릭하고, **고급 자산 만들기 -> 소리 -> 소리 감쇠**를 차례로 선택합니다.

![소리 감쇠 자산 만들기](images/unreal-spatial-audio-img-06.png)

4. **콘텐츠 브라우저** 창에서 마우스 오른쪽 단추로 **소리 감쇠** 자산을 클릭하고, **편집** 옵션을 선택하여 속성 창을 표시합니다.
    * **공간화 메서드**를 **Binaural(입체 음향)** 로 전환합니다.

![공간화 메서드 설정](images/unreal-spatial-audio-img-03.png)

5. **주변 소리** 행위자를 선택하고, **세부 정보** 패널에서 **감쇠** 섹션까지 아래로 스크롤합니다. 
    * **감쇠 설정** 속성을 만든 **소리 감쇠** 자산으로 설정합니다.

![감쇠 설정](images/unreal-spatial-audio-img-08.png)

6. 사용할 SoundAsset 파일을 지정하도록 주변 소리 행위자의 **소리** 속성을 업데이트하여 주변 소리 행위자에 연결하려는 **소리 자산**을 설정합니다.

![소리 자산 설정](images/unreal-spatial-audio-img-09.png)

> [!NOTE] 
> MicrosoftSpatialSound 플러그 인을 사용하여 공간화하려면 SoundAsset 파일이 모노여야 합니다. 아래 스크린샷과 같이 콘텐츠 브라우저 창에서 마우스로 자산 위를 가리키면 소리 파일의 속성을 확인할 수 있습니다.

![새 소리 감쇠 자산](images/unreal-spatial-audio-img-10.png)

이러한 모든 설정이 구성되면 HoloLens 2의 전용 하드웨어 오프로드 지원을 사용하여 주변 소리를 공간화할 수 있습니다.

## <a name="configuring-objects-for-spatialization"></a>공간화 개체 구성
공간 오디오를 사용한다는 것은 가상 환경에서 소리가 작동하는 방식을 관리해야 한다는 것을 의미합니다. 주요 초점은 사용자가 가까이 있을 때는 더 크게 표시되고, 멀리 있을 때는 더 조용하게 표시되는 소리 개체를 만드는 것입니다. 이를 소리 감쇠라고 하며, 소리가 고정된 지점에 있는 것처럼 표시되도록 합니다.

모든 감쇠 개체에는 다음에 대한 수정 가능한 설정이 제공됩니다.
* 거리
* 공간화
* 공기 흡수
* 수신기 포커스
* 반향 보내기
* 폐색

[Unreal의 소리 감쇠](https://docs.unrealengine.com/Engine/Audio/DistanceModelAttenuation/index.html)에는 이러한 각 항목에 대한 세부 정보와 구현이 있습니다.


## <a name="see-also"></a>참고 항목
* [공간 음향](https://docs.microsoft.com/windows/mixed-reality/spatial-sound)
* [공간 음향 디자인](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design)
* [MR 공간 220: 공간 음향](https://docs.microsoft.com/windows/mixed-reality/holograms-220)