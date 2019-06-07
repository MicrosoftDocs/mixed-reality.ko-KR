---
title: Unity를 사용 하 여 Vuforia를 사용 하 여
description: Windows Mixed Reality Unity 응용 프로그램을 빌드하는 Vuforia를 활용 합니다.
author: ailyadis
ms.author: ''
ms.date: 01/28/2019
ms.topic: article
keywords: Vuforia, 표식, 좌표, 프레임의 참조 추적
ms.openlocfilehash: c0d2f6d0707e1ddd3ee00d3eb80af9fb459f252b
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750344"
---
# <a name="using-vuforia-engine-with-unity"></a>Unity를 사용 하 여 Vuforia 엔진을 사용 하 여

Vuforia 엔진 HoloLens에 중요 한 기능을 제공 – AR 연결을 특정 이미지 및 환경에서 개체를 경험 합니다. 산업 엔터프라이즈를 위한 메커니즘을 기반으로 단계별 지침 안내 오버레이 실제 제품이 나 게임 디지털 기능 및 환경을 추가 하거나이 기능을 사용할 수 있습니다. 

AR 개발 환경을 Vuforia 엔진은 유연성에 대 한 광범위 한 기능 및 목표를 제공 합니다. 최신 기능, Vuforia 모델 대상 중 하나 사용 하 여 상용 및 산업에 대 한 주요 기능입니다. 모델 대상 응용 프로그램 컴퓨터, 자동차 또는 toys와 같은 실제 개체를 인식 하는 CAD 또는 디지털 3D 모델을 기준으로 추적을 허용 합니다. 산업 용도로이 기능은 어셈블리 작업자를 제공할 수 있으며 서비스 기술자 AR 사용 하 여 작업 지침 및 공장에서 절차 지침 또는 필드에서. 

휴대폰 및 태블릿 용으로 작성 된 기존 Vuforia 엔진 앱 HoloLens에서 실행 하는 Unity에서 쉽게 구성할 수 있습니다. Vuforia 엔진 HoloLens 앱 새 Surface Pro 4 및 Surface Book 같은 Windows 10 태블릿 하는 데 사용할 수도 있습니다.

## <a name="get-the-tools"></a>도구 다운로드

[권장 되는 버전을 설치](install-the-tools.md) Visual Studio와 Unity의 다음 Visual Studio 및 기본 IDE 및 컴파일러를 사용 하는 Unity를 구성 합니다. 

Unity를 설치 하는 경우에 "Windows 스토어.NET 스크립팅 백 엔드" 또는 "Windows 스토어 IL2CPP 스크립팅 백 엔드"를 설치 해야 합니다. 또한 Unity 내에서 Vuforia 엔진을 사용 하도록 설정 하려면 "Vuforia로 보강 된 현실 지원"을 선택 해야 합니다.


## <a name="getting-started-with-vuforia-engine"></a>Vuforia 엔진 시작

Vuforia 엔진은 Unity에 통합, 이후 개발자 다운로드 하거나 추가 도구 설치에 필요 하지 않습니다. Unity의 권장된 버전은 현재 2017.3 Vuforia 엔진 7.0.57 포함 하며 LTS 스트림의 경우 가장에 HoloLens Vuforia 엔진을 사용 하는 방법에 대 한 학습 된에 대 한 시작점을 [Vuforia 엔진 HoloLens 샘플](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) (Unity 자산 스토어 사용 가능). 샘플에는 HoloLens에 배포할 수 있는 미리 구성 된 장면을 포함 하 여 전체 HoloLens 프로젝트를 제공 합니다.

자동 Vuforia 이미지 대상 이미지 인식 및 HoloLens 환경의 디지털 콘텐츠를 사용 하 여 추가 하는 것을 사용 하는 방법을 보여 줍니다. Unity 및 Vuforia의 최신 버전을 사용 하는 개발자가 HoloLens에 모델 대상의 사용법을 보여 주는 화면 포함 하는 업데이트 된 예제에 대 한 액세스. 자동 Vuforia 엔진을 사용 하는 HoloLens 앱 만들기를 사용 하 여 실험으로 직접 콘텐츠를 쉽게 대체할 수 있습니다.


## <a name="configuring-a-vuforia-app-for-hololens"></a>HoloLens 용 Vuforia 앱을 구성합니다.

HoloLens 용 Vuforia 엔진 앱을 개발는 근본적으로 다른 장치에 대 한 Vuforia 엔진 앱 개발와 동일 합니다. 빌드 설정 및 아래 섹션에 설명 된 구성을 적용할 수 있습니다. 이것이 Vuforia 엔진이를 HoloLens 공간 매핑을 사용 하 여 작업 추적 시스템 위치를 사용 하도록 설정 하는 데 필요한 모든입니다.

## <a name="build-and-run-the-vuforia-engine-sample-for-hololens"></a>빌드 및 HoloLens Vuforia 엔진 샘플 실행
1.  다운로드 합니다 [HoloLens 용 Vuforia 엔진 샘플](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) Unity 자산 스토어에서
2.  적용 된 [권장 기능과 성능에 대 한 Unity 엔진 옵션](performance-recommendations-for-unity.md)
3.  빌드 장면에 수행 하는 샘플 작업을 추가 합니다.
4.  파일에서 플랫폼 빌드 대상에 "유니버설 Windows 플랫폼"에 대 한 설정 > 빌드 설정 합니다.
5.  다음 플랫폼 빌드 구성 설정을 선택 합니다. 
   * 대상 장치 HoloLens =
   * 빌드 형식 D3D =
   * SDK 최신 = 설치
   * Visual Studio 버전 = 최신 설치
   * 빌드 및 실행에 로컬 컴퓨터를 =
6.  고유한 정의 **제품 이름**의 **플레이어 설정**는 HoloLens에 설치 된 경우 앱의 이름으로 역할을 합니다.
7.  확인 **Vuforia 실제로 확대** 하 고 **지원 되는 가상 현실** 에서 **플레이어 설정 > xr 하이 설정**
8.  또한 아래 **xr 하이 설정을**, "Windows Mixed Reality"에 추가 되었는지 확인 합니다 **가상 현실 Sdk** 목록
9.  플레이어 설정에서 다음 기능을 확인 > 게시 설정 
   * InternetClient
   * 웹캠
   * SpatialPerception-화면 관찰자 API를 사용 하려는 경우
10. Visual Studio 프로젝트를 생성 하는 빌드를 선택 합니다.
11. Visual Studio에서 실행 파일을 빌드하고 HoloLens에 설치

참고: 모델 대상의 사용 예제를 포함 하 여 샘플 장면 포함 버전 7.2, HoloLens Vuforia 엔진 예제를 사용 하 여 시작

## <a name="the-vuforia-developer-portal"></a>Vuforia 개발자 포털

Vuforia 엔진을 사용 하 여 자신의 AR을 구축 하려는 개발자 환경 및 HoloLens에 Vuforia 개발자 포털에 등록 해야 [developer.vuforia.com](https://developer.vuforia.com/)합니다. 포털 개발자에 액세스할 수 합니다 [Vuforia 엔진 포럼](https://developer.vuforia.com/forum) 커뮤니티 토론에 참가 하는 경우를 [라이브러리](https://library.vuforia.com/) 의 모든 Vuforia 엔진 기능에는 심층적인설명서를사용하여[ Vuforia 대상 관리자](https://developer.vuforia.com/target-manager) 여기서 사용자 자신의 사용자 지정 대상을 만들 수 있습니다. 개발자가 사용 하 여 무료 개발자 라이선스를 등록할 수도 합니다 [Vuforia 라이선스 관리자](https://developer.vuforia.com/license-manager)합니다.

## <a name="extended-tracking-with-vuforia"></a>Vuforia 사용 하 여 확장 된 추적

[확장 된 추적](https://library.vuforia.com/articles/Training/Extended-Tracking) 는 대상이 더 이상 표시 하는 경우에 추적을 유지 하기 위해 환경의 맵을 만듭니다. HoloLens 수행한 공간 매핑에 Vuforia 엔진 ' 수량자입니다. 대상에서 확장 된 추적을 사용 하도록 설정 하면 공간 매핑 시스템에 전달할 대상인 포즈 사용 하도록 설정 합니다. 따라서에서 대상 Vuforia 엔진 및 HoloLens 공간 좌표계, 하지만 동시에 존재할 수 있습니다.

![Unity 설정 창](images/vuforia-extendedtracking.png)<br>
*Unity 설정 창*

**대상에서 확장 된 추적을 사용 하도록 설정**

Vuforia 엔진에서는 HoloLens 공간 좌표계에 확장 된 추적을 사용 하는 대상의 자세를 자동으로 변환 합니다. 이렇게 하면 HoloLens 추적을 가로채려 고 대상의 운전자의 공간 맵에 추가 내용을 통합할 수 있습니다. 이 프로세스는 Vuforia 엔진과 혼합된 현실에서 Unity Api 간에 발생 하 고 개발자가 프로그래밍이 필요 하지 않습니다-자동으로 처리 됩니다.

**어떤 일이 발생 하는 중... 같습니다.**
1. Vuforia의 target Tracker 인식 대상
2. 추적 대상 초기화 됩니다.
3. 위치 및 대상의 회전을 사용 하는 HoloLens에 대 한 강력한 포즈 예상을 제공 하도록 분석 됩니다.
4. Vuforia 대상의 자세를 HoloLens 공간 매핑 좌표 공간으로 변환
5. HoloLens가 추적 하 고 Vuforia 추적기 비활성화 됩니다.

개발자에 제어를 반환할 Vuforia는 TargetBehaviour에서 확장 된 추적을 사용 하지 않도록 설정 하 여이 프로세스를 제어할 수 있습니다.

**참고:** Vuforia 7.2부터 확장 추적이 더 이상 설정 된 대상 당 기준입니다. 대신 개발자는 장면에서 모든 대상에서 유사한 기능을 사용 하도록 설정 하려면 장치 추적 켤 수 있습니다.


## <a name="see-also"></a>참조
* [도구 설치](install-the-tools.md)
* [좌표계](coordinate-systems.md)
* [공간 매핑](spatial-mapping.md)
* [Unity의 카메라](camera-in-unity.md)
* [Unity Visual Studio 솔루션 내보내기 및 빌드](exporting-and-building-a-unity-visual-studio-solution.md)
* [Vuforia 설명서: Unity에서 Windows 10 용 개발](https://library.vuforia.com/articles/Solution/Developing-for-Windows-10-in-Unity)
* [Vuforia 설명서: Vuforia Unity 확장을 설치 하는 방법](https://library.vuforia.com/articles/Solution/Installing-the-Unity-Extension)
* [Vuforia 설명서: Unity에서 HoloLens 샘플 사용](https://library.vuforia.com/articles/Solution/Working-with-the-HoloLens-sample-in-Unity)
* [Vuforia 설명서: Vuforia에서 확장 된 추적](https://library.vuforia.com/articles/Training/Extended-Tracking)
