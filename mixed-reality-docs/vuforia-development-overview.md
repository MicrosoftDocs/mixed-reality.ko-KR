---
title: Unity에서 Vuforia 사용
description: Vuforia를 활용 하 여 Unity에서 Windows Mixed Reality 응용 프로그램을 빌드합니다.
author: thetuvix
ms.author: alexturn
ms.date: 01/28/2019
ms.topic: article
keywords: Vuforia, 표식, 좌표, 참조 프레임, 추적
ms.openlocfilehash: 0ab87a6262cbe74fd116fdc0a7045961bf8695d9
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437133"
---
# <a name="using-vuforia-engine-with-unity"></a>Unity에서 Vuforia 엔진 사용

Vuforia 엔진은 환경에서 특정 이미지 및 개체에 AR 환경을 연결 하는 기능을 제공 하는 중요 한 기능을 제공 합니다. 이 기능을 사용 하 여 산업 기업의 기계에 대 한 단계별 단계별 지침을 오버레이 하거나 실제 제품 또는 게임에 디지털 기능 및 환경을 추가할 수 있습니다. 

AR 환경을 개발할 때 유연성을 높이기 위해 Vuforia 엔진은 광범위 한 기능 및 대상을 제공 합니다. Vuforia 모델 대상의 최신 기능 중 하나는 상용 및 산업용에서 사용 하는 주요 기능입니다. 모델 대상을 사용 하면 응용 프로그램에서 컴퓨터, 자동차 또는 장난감과 같은 물리적 개체를 인식 하 고 CAD 또는 디지털 3D 모델에 따라 추적할 수 있습니다. 산업에서 사용 하는 경우이 기능을 통해 어셈블리 작업자 및 서비스 기술자에 게 공장 또는 현장에서 제공 되는 동안 AR 작업 지침과 절차 지침을 제공할 수 있습니다. 

휴대폰 및 태블릿 용으로 빌드된 기존 Vuforia 엔진 앱은 HoloLens에서 실행 되도록 Unity에서 쉽게 구성할 수 있습니다. Vuforia 엔진을 사용 하 여 Surface Pro 4 및 Surface Book과 같은 새 HoloLens 앱을 Windows 10 태블릿으로 가져올 수도 있습니다.

## <a name="get-the-tools"></a>도구 다운로드

[권장 되는 버전](install-the-tools.md) 의 visual Studio 및 Unity를 설치한 다음 visual studio 및 선호 하는 IDE 및 컴파일러를 사용 하도록 unity를 구성 합니다. 

Unity를 설치 하는 경우 "Windows 스토어 .NET Scripting 백 엔드" 또는 "Windows Store IL2CPP Scripting 백 엔드"를 설치 해야 합니다. 또한 Unity 내에서 Vuforia 엔진을 사용 하도록 설정 하려면 "Vuforia 확대 현실 지원"을 선택 해야 합니다.


## <a name="getting-started-with-vuforia-engine"></a>Vuforia 엔진 시작

Vuforia 엔진이 Unity에 통합 되었기 때문에 개발자는 추가 도구를 다운로드 하거나 설치할 필요가 없습니다. Unity의 권장 버전은 현재 2017.3에 포함 된 LTS 스트림 이며 Vuforia 엔진 7.0.57을 포함 합니다. HoloLens에서 Vuforia 엔진 사용에 대해 배우는 가장 좋은 출발점은 [Vuforia 엔진 HoloLens 샘플](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) (Unity Asset Store에서 사용 가능)과 함께 사용 하는 것입니다. 이 샘플에서는 HoloLens에 배포할 수 있는 미리 구성 된 장면을 비롯 한 전체 HoloLens 프로젝트를 제공 합니다.

이 장면에서는 Vuforia 이미지 대상을 사용 하 여 이미지를 인식 하 고 HoloLens 환경에서 디지털 콘텐츠로 확장 하는 방법을 보여 줍니다. 최신 버전의 Unity 및 Vuforia를 사용 하는 개발자는 HoloLens의 모델 목표 사용을 보여 주는 장면을 포함 하는 업데이트 된 샘플에 액세스할 수 있습니다. 사용자 고유의 콘텐츠를 백그라운드에서 쉽게 대체 하 여 Vuforia 엔진을 사용 하는 HoloLens 앱을 만들 수 있습니다.


## <a name="configuring-a-vuforia-app-for-hololens"></a>HoloLens 용 Vuforia 앱 구성

HoloLens 용 Vuforia 엔진 앱을 개발 하는 것은 기본적으로 다른 장치용 Vuforia 엔진 앱을 개발 하는 것과 같습니다. 그런 다음 아래 섹션에서 설명 하는 빌드 설정 및 구성을 적용할 수 있습니다. 이러한 모든 작업은 Vuforia 엔진이 HoloLens 공간 매핑 및 위치 추적 시스템을 사용 하도록 설정 하는 데 필요 합니다.

## <a name="build-and-run-the-vuforia-engine-sample-for-hololens"></a>HoloLens 용 Vuforia 엔진 샘플 빌드 및 실행
1.  Unity Asset Store에서 [HoloLens 용 Vuforia 엔진 샘플](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) 다운로드
2.  [전원 및 성능을 위해 권장 Unity 엔진 옵션](performance-recommendations-for-unity.md) 을 적용 합니다.
3.  빌드에서 장면에 샘플 장면을 추가 합니다.
4.  파일 > 빌드 설정에서 "유니버설 Windows 플랫폼"에 대 한 플랫폼 빌드 대상을 설정 합니다.
5.  다음 플랫폼 빌드 구성 설정을 선택 합니다. 
   * 대상 장치 = HoloLens
   * 빌드 형식 = D3D
   * SDK = 최근 설치 됨
   * Visual Studio 버전 = 최신 설치 됨
   * = 로컬 컴퓨터에서 빌드 및 실행
6.  **플레이어 설정**에서 HoloLens에 설치 될 때 앱 이름으로 사용할 고유한 **제품 이름을**정의 합니다.
7.  플레이어 설정에서 지원 되는 **Vuforia 확대 현실** 및 **가상 현실** **XR 설정 >** 확인
8.  또한 **XR 설정**에서 "Windows Mixed Reality"가 **가상 현실 sdk** 목록에 추가 되었는지 확인 합니다.
9.  플레이어 설정에서 다음 기능을 확인 > 게시 설정 
   * InternetClient
   * 웹캠
   * SpatialPerception-Surface 관찰자 API를 사용 하려는 경우
10. 빌드를 선택 하 여 Visual Studio 프로젝트 생성
11. Visual Studio에서 실행 파일을 빌드하고 HoloLens에 설치

참고: 버전 7.2부터 HoloLens 용 Vuforia 엔진 샘플에는 모델 대상의 예제 사용법을 비롯 한 샘플 장면이 포함 되어 있습니다.

## <a name="the-vuforia-developer-portal"></a>Vuforia 개발자 포털

Vuforia 엔진 및 HoloLens를 사용 하 여 자체 AR 환경을 만들려는 개발자는 [developer.vuforia.com](https://developer.vuforia.com/)에서 Vuforia 개발자 포털에 등록 해야 합니다. 포털에서 개발자는 커뮤니티 토론, 모든 Vuforia 엔진 기능에 대 한 심층 설명서를 포함 하는 [라이브러리](https://library.vuforia.com/) 및 사용자가 사용할 수 있는 [Vuforia 대상 관리자](https://developer.vuforia.com/target-manager) 에 참여할 수 있는 [Vuforia 엔진 포럼](https://developer.vuforia.com/forum) 에 액세스할 수 있습니다. 고유한 사용자 지정 대상을 만듭니다. 또한 개발자는 [Vuforia 라이선스 관리자](https://developer.vuforia.com/license-manager)를 사용 하 여 무료 개발자 라이선스에 등록할 수 있습니다.

## <a name="extended-tracking-with-vuforia"></a>Vuforia를 사용 하 여 확장 추적

[확장 추적은](https://library.vuforia.com/articles/Training/Extended-Tracking) 대상이 더 이상 표시 되지 않는 경우에도 추적을 유지 하는 환경 지도를 만듭니다. HoloLens에서 수행 하는 공간 매핑에 해당 하는 Vuforia 엔진입니다. 대상에 대해 확장 된 추적을 사용 하도록 설정 하면 해당 대상의 포즈를 공간 매핑 시스템에 전달할 수 있습니다. 이러한 방식으로 대상은 Vuforia 엔진과 HoloLens 공간 좌표계 모두에 있을 수 있지만 동시에 존재할 수는 없습니다.

Unity 설정 창 ![](images/vuforia-extendedtracking.png)<br>
*Unity 설정 창*

**대상에 대 한 확장 추적 설정**

Vuforia 엔진은 확장 된 추적을 사용 하는 대상의 포즈를 HoloLens 공간 좌표계로 자동으로 변환 합니다. 이를 통해 HoloLens는 추적을 사용 하 여 모든 콘텐츠 확대를 대상의 주변 공간 매핑에 통합할 수 있습니다. 이 프로세스는 Unity에서 Vuforia 엔진과 혼합 현실 Api 사이에서 발생 하며 개발자의 프로그래밍이 필요 하지 않습니다 .이는 자동으로 처리 됩니다.

**수행 되는 작업은 다음과 같습니다.**
1. Vuforia의 대상 추적기는 대상을 인식 합니다.
2. 그러면 대상 추적이 초기화 됩니다.
3. 대상의 위치 및 회전이 분석 되어 HoloLens에서 사용할 강력한 포즈 예상치를 제공 합니다.
4. Vuforia는 대상의 포즈를 HoloLens 공간 매핑 좌표 공간으로 변환 합니다.
5. HoloLens는 추적을 사용 하 고 Vuforia 추적기는 비활성화 됩니다.

개발자는 TargetBehaviour에서 확장 된 추적을 사용 하지 않도록 설정 하 여이 프로세스를 제어 하 고 Vuforia에 제어를 반환할 수 있습니다.

**참고:** Vuforia 7.2부터 확장 된 추적은 더 이상 대상 별로 사용 하도록 설정 되지 않습니다. 대신 개발자는 장면의 모든 대상에서 유사한 기능을 사용 하도록 장치 추적을 켤 수 있습니다.


## <a name="see-also"></a>참고 항목
* [도구 설치](install-the-tools.md)
* [좌표계](coordinate-systems.md)
* [공간 매핑](spatial-mapping.md)
* [Unity의 카메라](camera-in-unity.md)
* [Unity Visual Studio 솔루션 내보내기 및 빌드](exporting-and-building-a-unity-visual-studio-solution.md)
* [Vuforia 설명서: Unity에서 Windows 10 개발](https://library.vuforia.com/articles/Solution/Developing-for-Windows-10-in-Unity)
* [Vuforia 설명서: Vuforia Unity 확장을 설치 하는 방법](https://library.vuforia.com/articles/Solution/Installing-the-Unity-Extension)
* [Vuforia 설명서: Unity에서 HoloLens 샘플 사용](https://library.vuforia.com/articles/Solution/Working-with-the-HoloLens-sample-in-Unity)
* [Vuforia 설명서: Vuforia에서 확장 추적](https://library.vuforia.com/articles/Training/Extended-Tracking)
