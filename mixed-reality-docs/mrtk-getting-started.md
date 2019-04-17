---
title: MRTK 버전 2 사용 하 여 시작
description: 새 MRTK 활용 하려는 개발자를 위한
author: grbury
ms.author: grbury
ms.date: 02/22/19
ms.topic: article
keywords: Windows Mixed Reality, 테스트, MRTK 버전 2, MRTK, 도구, SDK, HoloLens, HoloLens 2
ms.openlocfilehash: 44e5fe0fd4384af68922eda4bcb0594d39a1c1b7
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600030"
---
# <a name="getting-started-with-mrtk-version-2"></a>MRTK 버전 2 사용 하 여 시작

MRTK가 처음 출시 되는 HoloLens 이므로 없습니다 경우 현재 해당 하는 개발자 커뮤니티의 어려운 작업 없이 관련 된 멋진 오픈 소스 도구 키트입니다. 지난 3 년 동안 개발자 커뮤니티의 피드백을 수신 하 고 작성 MRTK 버전 2는 가장 큰 문제를 고려해 야 합니다.  

Unity 사용 하 여 버전 2 MRTK 혼합된 현실 응용 프로그램에는 오픈 소스 플랫폼 간 개발 키트입니다.  Microsoft HoloLens, (VR) 헤드셋을 몰입 형 Windows Mixed Reality 및 OpenVR 플랫폼을 대상으로 하는 응용 프로그램의 개발을 가속화 MRTK 버전 2 것입니다. 프로젝트는 장벽이 혼합된 현실 응용 프로그램을 만들고 우리가 증가 함에 따라 커뮤니티에 다시 기여에 항목을 줄이는 목표로 합니다. 


참조 된 <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/wiki/Getting-Started-with-MRTK-v2" target="_blank">MRTK 버전 2 wiki</a> 를 시작 하 고 자세한 정보.

## <a name="new-with-mrtk-version-2"></a>MRTK 버전 2 사용 하 여 새
노력의 일환으로 이러한 플랫폼 도구 스트레스 하고자 합니다.  사실, 받은 편지함 경험 설치 환경 (OOBE) 등이 혼합 현실 학습 응용 프로그램을 개발 하려면 MRTK 버전 2 활용 했습니다.  플랫폼에서 개발 하는 가장 좋은 방법은 것 때문에 먼저 MRTK를 통해서도 새 HoloLens 2 기능을 확인 하려면 예상할 수 있습니다. 

### <a name="modular"></a>모듈식
빌드 했습니다이 모듈식 방식으로 프로젝트에 도구 키트의 모든 비트를 수행할 필요가 없습니다.  이 실제로 몇 가지 이점이 있습니다.  또한 프로젝트 크기를 작게 유지 뿐만 관리 하기가 쉬워집니다.  위쪽에, 있기 때문에 스크립트 가능한 개체를 사용 하 여 빌드되어 인터페이스 제어 되 고도 포함 되어 있는 다른 서비스, 시스템 및 플랫폼을 지원 하기 위해 고유한 구성 요소를 대체할 수 있습니다.


### <a name="cross-platform"></a>플랫폼 간
다른 플랫폼의 설명 하자면이 플랫폼 간 지원 합니다.  및 다른 플랫폼 빌드 대상 전환할 때 중단 toolkit 코드 없음 확인 했 동안 모든 단일 플랫폼은 기본적으로 지원 되는 뜻입니다.  견고성 및 모듈식 디자인을 사용 하 여 확장성을 설정 합니다 ARCore, ARKit 및 OpenVR 같은 여러 플랫폼을 지원할 수에 대 한 적절 한 경로에 있습니다.


### <a name="performant"></a>고성능
모바일 플랫폼을 사용 했습니다 생성 성능을 염두에서를 사용 하 여 합니다.  이 매우 중요 하 고 도구는 수에 대해 작동 하도록 하지 확인 하려고 했습니다.


## <a name="see-also"></a>참조
* [도구 설치](install-the-tools.md)
* [HTK/MRTK에서 MRTK 버전 2로 이식](mrtk-porting-guide.md)
