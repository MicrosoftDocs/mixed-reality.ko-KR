---
title: Spectator 뷰
description: 외부 디스플레이 또는 혼합 현실 환경의 비디오 녹화에서 혼합 현실 환경을 보여 주는 수단으로 외부 장치에서 holograms을 시각화 합니다.
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
keywords: Spectator View, iPhone, iOS, iPad, OpenCV, 카메라, ARKit, HoloLens, Mixed Reality, MixedRealityToolkit, 데모, 레코드
ms.openlocfilehash: 708ed694af3769f16d5dce0595e026f9a348d754
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047170"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a>HoloLens 및 HoloLens Spectator 보기 2

![표식](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a>개요

HoloLens를 제공 하는 경우에는 자주 제공 하지 않는 사용자가 불가사의를 경험 하지 못할 수 있습니다. Spectator 보기를 사용 하면 다른 사용자가 해당 지역에서 HoloLens 사용자에 게 표시 되는 2D 화면을 볼 수 있습니다.
Spectator View는 모바일 장치를 사용 하 여 HD에 holograms을 기록 하는 빠르고 경제적인 접근 방법을 제공 합니다. 또한 비디오 카메라를 사용 하 여 holograms에 대 한 전문적인 품질 기록을 제공 합니다.

## <a name="key-resources"></a>주요 리소스

* [**GitHub의 Spectator 보기**](https://github.com/microsoft/MixedReality-SpectatorView)
* [**Spectator View 설명서**](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [**Spectator 뷰 샘플**](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a>사용 사례
* IPhone 또는 Android 장치를 사용 하 여 혼합 현실 환경을 기록할 수 있습니다. 전체 HD를 기록 하 고 holograms 및 그림자에 앤티앨리어싱을 적용 합니다. Holograms 비디오를 빠르게 캡처하는 비용 효율적이 고 빠른 방법입니다.
* IPhone 또는 iPad에서 바로 Apple TV로 라이브 혼합 현실 경험을 스트리밍할 수 있습니다.
* 게스트와 경험을 공유 합니다. HoloLens가 아닌 사용자가 휴대폰 또는 태블릿에서 직접 holograms 경험 하도록 합니다.

## <a name="current-features"></a>현재 기능

* Holograms의 공간 동기화는 모든 사용자가 정확히 동일한 장소에서 Holograms을 볼 것입니다.
* iOS (ARKit 사용 장치) 및 Android (Arkit 사용 장치) 지원.
여러 iOS 게스트.
비디오 + holograms + 주변 소리 + 홀로그램 소리의 기록입니다.
다른 지원 앱과 함께 비디오를 저장 하거나, 전자 메일을 보내거나, 공유할 수 있도록 시트를 공유 합니다.

![표식](images/SpecViewPhoneDemo.jpg)
표식표식![](images/hololensspectatorview-500px.jpg) ![](images/spectatorview-300px.png)

다음 표에서는 다양 한 Spectator 뷰 기능 및 해당 기능을 보여 줍니다. 비디오 녹음 요구에 가장 적합 한 옵션을 선택 합니다.

|                                      | 휴대폰                  |                    비디오 카메라              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| HD 품질                           |         전체 HD         |        전문 품질 filming (비디오 카메라에 의해 결정 됨)      |
| 간편한 카메라 이동                 |            ✔            |                      ✔                      |
| 세 번째 사용자 뷰                    |            ✔            |                      ✔                      |
| 화면에 스트리밍할 수 있습니다.           |            ✔            |                      ✔                      |
| 이식 가능                             |            ✔            |                                             |
| 무선                             |            ✔            |                                             |
| 추가 필수 하드웨어         |     Android 휴대폰, iPhone    | HoloLens + Rig + Tripod + 비디오 카메라 + PC + Unity |
| 하드웨어 투자                  |           낮음            |                     높음                    |
| 플랫폼 간                       |           Android, iOS   |                                             |
| 동기화 된 콘텐츠                 |            ✔            |                      ✔                      |
| 런타임 설치 기간               |         대화          |                     느림                    |
## <a name="see-also"></a>참조

* [혼합 현실 캡처](mixed-reality-capture.md) 
* [개발자를 위한 혼합 현실 캡처](mixed-reality-capture-for-developers.md)
* [혼합 현실의 공유 환경](shared-experiences-in-mixed-reality.md)
