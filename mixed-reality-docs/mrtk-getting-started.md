---
title: MRTK 버전 2 시작
description: MRTK를 활용하는 데 관심이 있는 새 개발자를 대상으로 합니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, 테스트, Mixed Reality Toolkit, MRTK 버전 2, MRTK, 도구, SDK, HoloLens, HoloLens 2
ms.openlocfilehash: fc9638f405604bed7c7531ace0977a88509e91b5
ms.sourcegitcommit: 4d43a8f40e3132605cee9ece9229e67d985db645
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491093"
---
# <a name="getting-started-with-mrtk-v2"></a>MRTK v2 시작

## <a name="mrtk-getting-started-guide"></a>MRTK 시작 가이드
MRTK V2를 시작하는 방법에 대한 자세한 내용은 [MRTK 시작 가이드](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)를 참조하세요.

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>MRTK(Mixed Reality Toolkit)란?
HoloLens가 처음 출시된 이후로 활성화된 MRTK는 놀라운 오픈 소스 도구 키트이며, 이에 기여한 개발자 커뮤니티의 노력이 없었으면 지금의 위치에 있지 못했을 것입니다. 가장 중요한 문제를 고려하기 위해 지난 3년간 개발자 커뮤니티의 피드백을 주의 깊게 살피면서 MRTK v2를 구축했습니다.  

Unity가 포함된 MRTK v2는 혼합 현실 애플리케이션용 오픈 소스 플랫폼 간 개발 키트입니다.  MRTK 버전 2는 Microsoft HoloLens, Windows Mixed Reality 몰입형(VR) 헤드셋 및 OpenVR 플랫폼을 대상으로 하는 애플리케이션의 개발을 가속화하기 위한 것입니다. 이 프로젝트는 진입 장벽을 낮추고, 혼합 현실 애플리케이션을 만들고, 성장함에 따라 커뮤니티에 다시 기여하는 것을 목표로 합니다. 

자세한 내용은 [MRTK 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)을 참조하세요.

## <a name="new-with-mrtk-v2"></a>MRTK v2의 새로운 기능
여기서는 이러한 플랫폼 도구에 대한 약속을 강조하려고 합니다.  실제로 MRTK 버전 2를 활용하여 설정 환경(OOBE) 및 Mixed Reality 학습 애플리케이션과 같은 받은 편지함 환경을 개발했습니다.  또한 플랫폼에서 개발하는 것이 가장 좋은 방법이라고 생각하므로 새로운 HoloLens 2 기능이 MRTK를 통해 처음 공개될 것으로 예상할 수 있습니다. 

### <a name="modular"></a>모듈식
모듈식으로 빌드했으므로 도구 키트의 모든 비트를 프로젝트에 적용할 필요가 없습니다.  실제로 몇 가지 이점이 있습니다.  이를 통해 프로젝트 크기를 더 작게 유지하고 관리하기가 더 쉽습니다.  또한 스크립트 가능한 개체를 사용하여 빌드되고 인터페이스를 기반으로 하므로 포함된 구성 요소를 사용자 고유의 구성 요소로 바꿔 다른 서비스, 시스템 및 플랫폼을 지원할 수도 있습니다.

### <a name="cross-platform"></a>플랫폼 간
다른 플랫폼과 관련하여 플랫폼 간 지원이 제공됩니다.  이는 모든 단일 플랫폼이 기본적으로 지원된다는 것을 의미하지는 않지만, 빌드 대상을 다른 플랫폼으로 전환할 때 도구 키트 코드가 중단되지 않도록 했습니다.  모듈식 설계를 통한 견고성과 확장성은 ARCore, ARKit 및 OpenVR과 같은 여러 플랫폼을 지원할 수 있는 좋은 경로를 제공합니다.

### <a name="performant"></a>성능 기준에 적합
모바일 플랫폼을 사용하는 경우 성능을 고려하여 구축했습니다.  이는 매우 중요하며, 도구가 사용자에게 불리하게 작동하지 않도록 보장하려고 했습니다.

## <a name="see-also"></a>참고 항목
* [MRTK 시작 가이드](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [MRTK 설명서 홈](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [도구 설치](install-the-tools.md)
* [HTK/MRTK에서 MRTK 버전 2로 포팅](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
