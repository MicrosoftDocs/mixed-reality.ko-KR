---
title: MRTK 패키지
description: 이 문서에서는 Microsoft 혼합 현실 Toollkit를 구성 하는 패키지를 설명 합니다.
author: davidkline-ms
ms.author: davidkl
ms.date: 02/12/19
ms.topic: article
keywords: Windows Mixed Reality를 MRTK, 패키지, 구성 요소
ms.openlocfilehash: 7e44d75e1c267cff0ba67dd86dabfaa51bce659d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604642"
---
# <a name="mrtk-packages"></a>MRTK 패키지

혼합 현실 도구 키트 (MRTK)은 구성 요소화 된 방식으로 혼합 현실 하드웨어 및 플랫폼에 대 한 지원을 제공 하 여 플랫폼 간 혼합 현실 응용 프로그램 개발을 사용 하도록 설정 하는 패키지의 컬렉션.

범주 MRTK 패키지에는 세 가지가 있습니다. 

* [Foundation](#foundation-packages)
* [확장명](#extension-packages)
* [실험적](#experimental-packages)

## <a name="foundation-packages"></a>Foundation 패키지

혼합 현실 Toolkit Foundation에는 혼합 현실 플랫폼 간에 공통 기능을 활용 하 여 응용 프로그램을 사용 하는 패키지의 집합입니다. 이러한 패키지 해제 되며 소스 코드에서 Microsoft에서 지원 합니다 [mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) github 분기 합니다.

![MRTK Foundation 패키지](images/mrtk-foundation.jpg)

*혼합된 현실 Toolkit Foundation 패키지*

MRTK Foundation의 구성 됩니다.

* [Core 패키지](#core-package)
* [플랫폼 공급자](#platform-providers)
* [시스템 서비스](#system-services)
* [기능 자산](#feature-assets)

다음 섹션에서는 각 범주에는 패키지의 형식을 설명합니다.

### <a name="core-package"></a>Core 패키지

Core 패키지는 _필요한_ 구성 요소 모든 MRTK foundation 패키지에서 종속성으로 수행 됩니다.

MRTK Core 패키지에는 다음이 포함 됩니다.

* [공용 인터페이스, 클래스 및 데이터 형식](#common-interfaces-clases-and-data-types)
* [MixedRealityToolkit 장면 구성 요소](#mixedrealitytoolkit-scene-component)
* [MRTK 표준 셰이더](#mrtk-standard-shader)
* [Unity 입력된 공급자](#unity-input-provider)
* [패키지 관리](#package-management)

#### <a name="common-interfaces-classes-and-data-types"></a>공용 인터페이스, 클래스 및 데이터 형식

혼합 현실 Toolkit 코어 패키지는 모든 공용 인터페이스, 클래스 및 다른 모든 구성 요소에서 사용 되는 데이터 형식에 대 한 정의 포함 합니다. 응용 프로그램 플랫폼에서 가장 높은 호환성 수준을 사용 하도록 정의 된 인터페이스를 통해서만 MRTK 구성 요소를 액세스 하는 것이 좋습니다.

#### <a name="mixedrealitytoolkit-scene-component"></a>MixedRealityToolkit 장면 구성 요소

MixedRealityToolkit 장면 구성 요소는 혼합 현실 도구 키트에 대 한 단일, 중앙 집중식 리소스 관리자입니다. 이 구성 요소를 로드 하 고 및 플랫폼 및 서비스 모듈의 수명 관리, 해당 구성 설정에 액세스 하려면 시스템에 대 한 리소스를 제공 합니다. 

#### <a name="mrtk-standard-shader"></a>MRTK 표준 셰이더

MRTK 표준 셰이더는 MRTK에서 제공 되는 자료의 거의 모든 기초를 제공 합니다. 이 셰이더는 매우 유연 하 고 다양 한 MRTK는 지원 되는 플랫폼에 대 한 최적화. 것 _항상_ MRTK 표준 셰이더를 사용 하 여 최적의 성능을 위해 응용 프로그램의 자료는 것이 좋습니다.

#### <a name="unity-input-provider"></a>Unity 입력된 공급자

Unity 입력 공급자 3D 공간 마우스 게임 컨트롤러, 터치 스크린 등 일반적인 입력된 장치에 대 한 액세스를 제공합니다.

#### <a name="package-management"></a>패키지 관리

_서비스 예정_

혼합 현실 Toolkit Core 패키지를 검색 하 고 선택적 foundation, 확장 및 실험적 MRTK 패키지 관리에 대 한 지원을 제공 합니다.

### <a name="platform-providers"></a>플랫폼 공급자

MRTK 플랫폼 공급자 패키지는 대상 혼합 현실 하드웨어 혼합 현실 Toolkit 및 플랫폼 기능을 사용 하도록 설정 하는 구성 요소입니다.

지원 되는 플랫폼은 다음과 같습니다.

* [Windows Mixed Reality](#windows-mixed-reality)
* [OpenVR](#openvr)
* [Windows 음성](#windows-voice)

#### <a name="windows-mixed-reality"></a>Windows Mixed Reality

Windows Mixed Reality 패키지는 Microsoft HoloLens 및 혼합 현실 몰입 Windows 장치에 대 한 지원을 제공합니다. 패키지에는 전체 플랫폼 지원이 포함 되어 있습니다. 포함 하 여:

* 대상으로 응시
* 제스처
* Windows Mixed Reality 동작 컨트롤러
* 공간 매핑

#### <a name="openvr"></a>OpenVR

OpenVR 패키지 OpenVR 플랫폼을 사용 하 여 장치에 대 한 지원 하드웨어 및 플랫폼을 제공 합니다.

#### <a name="windows-voice"></a>Windows 음성

Windows 음성 패키지는 Microsoft Windows 10 장치에서 키워드 인식과 받아쓰기 기능에 대 한 지원을 제공합니다.

### <a name="system-services"></a>시스템 서비스

핵심 플랫폼 서비스는 시스템 서비스 패키지에 제공 됩니다. 이러한 패키지에 정의 된 시스템 서비스 인터페이스, 혼합 현실 도구 키트의 기본 구현을 포함 합니다 [core](#core-package) 패키지 있습니다.

MRTK foundation에는 다음 시스템 서비스가 포함 됩니다.

* [경계 시스템](#boundary-system)
* [진단 시스템](#diagnostic-system)
* [입력된 시스템](#input-system)
* [공간 인식 시스템](#spatial-awareness-system)
* [텔레포트 시스템](#teleport-system)

#### <a name="boundary-system"></a>경계 시스템

가상 현실에 대 한 데이터를 제공 하는 MRTK 경계 시스템 playspace입니다. 사용자가 경계를 구성 하는 시스템에서는 시스템 floor 평면, 사각형 playspace, 추적된 영역 등을 제공할 수 있습니다.

#### <a name="diagnostic-system"></a>진단 시스템

MRTK 진단 시스템에 응용 프로그램 환경에서 실시간 성능 데이터를 제공합니다. Glace에서 응용 프로그램을 사용 하 여 프레임 속도, 프로세서 시간 및 기타 주요 성능 메트릭을 볼 수 있게 됩니다.

#### <a name="input-system"></a>입력된 시스템

MRTK 입력 시스템 응용 프로그램이 사용자 동작을 지정 하 고 가장 적합 한 단추 및 대상 컨트롤러의 축에 이러한 작업을 할당 하 여 플랫폼 간 방식으로 입력을 액세스할 수 있습니다.

#### <a name="spatial-awareness-system"></a>공간 인식 시스템

MRTK 공간 인식 시스템 Microsoft HoloLens 같은 장치에서 실제 환경 데이터에 액세스할 수 있습니다.

#### <a name="teleport-system"></a>텔레포트 시스템

MRTK 텔레포트 시스템에 가상 현실 locomotion 지원을 제공합니다.

### <a name="feature-assets"></a>기능 자산

기능 자산은 스크립트 및 Unity 자산으로 제공 되는 관련 기능의 컬렉션입니다. 이러한 기능 중 일부는 다음과 같습니다.

* 사용자 인터페이스 컨트롤
* 표준 자산
* more

## <a name="extension-packages"></a>확장 패키지

MRTK 확장 패키지는 확장 하 고 혼합 현실 도구 키트의 기능을 향상 시키는 Microsoft 및 커뮤니티에서 작성 하는 패키지의 컬렉션입니다. 확장 작성자가 필요한 종속성을 상태, 혼합 현실 도구 키트와 호환 패키지로 표시 및 라이선스 제공 되며 문을 지원 합니다.

확장 패키지에는 새로운 기능과 새로운 플랫폼 지원을 제공할 수 있습니다. 시간이 지남에 따라 확장, 지원 및 작성자의 승인을 사용 하 여 마이그레이션될 수 있으므로 MRTK 기반 이때는 해제 되며 Microsoft 지원에 합니다.

![MRTK 확장 패키지](images/mrtk-extensions.jpg)

*혼합된 현실 Toolkit 확장 패키지*

## <a name="experimental-packages"></a>실험적 패키지

실험적 패키지에는 흥미로운 새로운 아이디어, 비행 프로토타입 기능 및 시험판 버전을 제공합니다. 가장 실험적 패키지의 목표는 새로운 고 고객의 관심 계기입니다. 많은 있지만 모든 실험적 패키지 수 확장으로 다시 출시 된 프로토타입 및 테스트 단계를 완료 합니다.

![MRTK 실험적 패키지](images/mrtk-experimental.jpg)

*혼합된 현실 Toolkit 실험적 패키지*

## <a name="conclusion"></a>결론

혼합 현실 Toolkit 패키지 및 패키지 관리 시스템은 입자 불필요 한 구성 요소 프로젝트에 포함 되도록 요구 하지 않고 환경에 기능을 작성 하기 위한 명확 하 고 간단한 방법을 사용 하도록 설계 되었습니다.

시간이 지남에 따라 패키지 관리 지원은 추가 하 고 혼합 현실 도구 키트 내에서 강화 합니다. 피드백 했거나 참여 하려는 경우를 방문 하십시오 합니다 [혼합 현실 Toolkit 프로젝트](https://github.com/Microsoft/MixedRealityToolkit-Unity) github입니다. 

## <a name="see-also"></a>참조

* [MixedRealityToolkit-Unity (GitHub)](https://github.com/Microsoft/MixedRealityToolkit-Unity)

