---
title: MRTK 버전 2 시작
description: MRTK를 활용 하려는 새로운 개발자
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
keywords: Windows Mixed Reality, 테스트, 혼합 현실 도구 키트, MRTK 버전 2, MRTK, 도구, SDK, HoloLens, HoloLens 2
ms.openlocfilehash: bb958543aa68586dd689a2048665b233d6be7064
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913131"
---
# <a name="getting-started-with-mrtk-v2"></a>MRTK v2 시작

## <a name="mrtk-getting-started-guide"></a>MRTK 시작 가이드
MRTK v 2를 시작 하는 방법에 대 한 자세한 내용은 [mrtk 시작 가이드](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) 를 참조 하세요.

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>혼합 현실 도구 키트 (MRTK) 란?
MRTK는 HoloLens가 처음 출시 된 후에 발생 하는 놀라운 오픈 소스 도구 키트 이며, 오늘날 개발자 커뮤니티의 하드 작업 없이는 오늘날 어디에서 나 사용할 수 없습니다. 지난 3 년간 개발자 커뮤니티의 피드백을 수신 하 고 MRTK v 2를 구축 하 여 가장 중요 한 문제를 고려 했습니다.  

Unity가 포함된 MRTK v2는 혼합 현실 애플리케이션용 오픈 소스 플랫폼 간 개발 키트입니다.  MRTK 버전 2는 Microsoft HoloLens, Windows Mixed Reality 몰입형(VR) 헤드셋 및 OpenVR 플랫폼을 대상으로 하는 애플리케이션의 개발을 가속화하기 위한 것입니다. 이 프로젝트는 항목에 대 한 장벽을 줄이고, 혼합 현실 응용 프로그램을 만들고, 모든 성장에 따라 커뮤니티에 다시 기여 하기 위한 것입니다. 

자세히 알아보려면 [Mrtk 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) 을 참조 하세요.

## <a name="new-with-mrtk-v2"></a>MRTK v2에서 새로 만들기
이러한 플랫폼 도구에 대 한 약속을 스트레스 하고자 합니다.  실제로는 MRTK 버전 2를 활용 하 여 설치 환경 (OOBE) 및 혼합 현실 학습 응용 프로그램 등의 수신함 환경을 개발 했습니다.  플랫폼에서 개발 하는 것이 가장 좋은 방법 이라고 생각 하기 때문에 MRTK를 통해 처음에 제공 되는 새로운 HoloLens 2 기능이 표시 될 수도 있습니다. 

### <a name="modular"></a>방식
모듈식 방식으로 빌드 되었으므로 도구 키트의 모든 비트를 프로젝트에 적용할 필요가 없습니다.  실제로 몇 가지 이점이 있습니다.  이를 통해 프로젝트 크기를 더 작게 유지 하 고 쉽게 관리할 수 있습니다.  또한 스크립트 가능한 개체를 사용 하 여 빌드 되었으며 인터페이스를 기반으로 하기 때문에 사용자 고유의 구성 요소를 대체 하 여 다른 서비스, 시스템 및 플랫폼을 지원할 수도 있습니다.

### <a name="cross-platform"></a>플랫폼 간
다른 플랫폼의 경우 플랫폼 간 지원이 제공 됩니다.  이는 모든 단일 플랫폼이 기본적으로 지원 되는 것을 의미 하지는 않지만 빌드 대상을 다른 플랫폼으로 전환 하면 도구 키트 코드가 중단 되지 않도록 합니다.  모듈식 디자인을 사용한 견고성과 확장성은 ARCore, Arcore 및 OpenVR와 같은 여러 플랫폼을 지원할 수 있는 좋은 경로를 설정 합니다.

### <a name="performant"></a>성능과
모바일 플랫폼을 사용 하 여 작업 하는 경우 성능을 염두에 두어야 합니다.  이는 매우 중요 하며, 도구가 사용자에 대해 작동 하지 않도록 하는 데 필요 합니다.

## <a name="see-also"></a>참고 항목
* [MRTK 시작 가이드](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [MRTK 설명서 홈](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [도구 설치](install-the-tools.md)
* [HTK/MRTK에서 MRTK 버전 2로 포팅](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
