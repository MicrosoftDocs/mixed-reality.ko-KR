---
title: 관람자 보기
description: 외부 디스플레이에서 혼합 현실 환경을 보여 주거나 혼합 현실 환경의 비디오를 녹화하는 수단으로 외부 디바이스에서 홀로그램을 시각화합니다.
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: 관람자 보기, iPhone, iOS, iPad, OpenCV, 카메라, ARKit, HoloLens, Mixed Reality, Mixed Reality Toolkit, 데모, 레코드
ms.openlocfilehash: 9bc1c2809c7d780d439d9efb58f464b41de3dccd
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/29/2020
ms.locfileid: "74491166"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a>HoloLens 및 HoloLens 2의 관람자 보기

![표식](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a>개요

HoloLens를 착용할 때 이를 착용하지 않은 사람이 놀라운 것을 경험하지 못할 수 있다는 것을 잊는 경우가 많습니다. 관람자 보기를 사용하면 다른 사용자가 2D 화면에서 HoloLens 사용자가 자신의 세계에서 보는 것을 볼 수 있습니다.
관람자 보기는 모바일 디바이스를 사용하여 홀로그램을 HD로 녹화하는 빠르고 경제적인 방법을 제공합니다. 또한 비디오 카메라를 사용하여 홀로그램을 전문적인 품질로 녹화하는 기능을 제공합니다.

## <a name="key-resources"></a>주요 리소스

* [**GitHub의 관람자 보기**](https://github.com/microsoft/MixedReality-SpectatorView)
* [**관람자 보기 설명서**](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [**관람자 보기 샘플**](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a>사용 사례
* iPhone 또는 Android 디바이스를 사용하여 혼합 현실 환경을 녹화할 수 있습니다. Full HD로 녹화하고, 안티앨리어싱을 홀로그램과 그림자에 적용합니다. 이는 홀로그램의 비디오를 캡처하는 비용 효율적이고 빠른 방법입니다.
* 라이브 혼합 현실 환경을 지연 없이 iPhone 또는 iPad에서 Apple TV로 직접 스트림합니다!
* 게스트와 경험을 공유합니다. 비 HoloLens 사용자가 휴대폰 또는 태블릿에서 홀로그램을 직접 경험할 수 있도록 합니다.

## <a name="current-features"></a>현재 기능

* 홀로그램의 공간 동기화를 통해 모든 사용자가 똑같은 장소에서 홀로그램을 볼 수 있습니다.
* iOS(ARKit 사용 디바이스) 및 Android(ARCore 사용 디바이스)를 지원합니다.
여러 iOS 게스트가 사용할 수 있습니다.
비디오 + 홀로그램 + 주변 소리 + 홀로그램 소리를 녹화합니다.
비디오를 저장하거나, 이메일로 보내거나, 다른 지원 앱과 공유할 수 있도록 시트를 공유합니다.

![표식](images/SpecViewPhoneDemo.jpg)
![표식](images/hololensspectatorview-500px.jpg) ![표식](images/spectatorview-300px.png)

다음 표에는 다양한 관람자 보기 기능 및 해당 특성이 나와 있습니다. 비디오 녹화 요구 사항에 가장 적합한 옵션을 선택하세요.

|                                      | 모바일                  |                    비디오 카메라              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| HD 품질                           |         Full HD         |        전문 품질 촬영(비디오 카메라)      |
| 간편한 카메라 이동                 |            ✔            |                      ✔                      |
| 3인칭 보기                    |            ✔            |                      ✔                      |
| 화면으로 스트리밍 가능           |            ✔            |                      ✔                      |
| 이식 가능                             |            ✔            |                                             |
| 무선                             |            ✔            |                                             |
| 추가 필수 하드웨어         |     Android 휴대폰, iPhone    | HoloLens + 의장품 + 삼각대 + 비디오 카메라 + PC + Unity |
| 하드웨어 투자                  |           낮음            |                     높음                    |
| 플랫폼 간                       |           Android, iOS   |                                             |
| 동기화된 콘텐츠                 |            ✔            |                      ✔                      |
| 런타임 설치 기간               |         즉시          |                     느림                    |
## <a name="see-also"></a>참고 항목

* [혼합 현실 캡처](mixed-reality-capture.md) 
* [개발자를 위한 혼합 현실 캡처](mixed-reality-capture-for-developers.md)
* [혼합 현실의 공유 환경](shared-experiences-in-mixed-reality.md)
