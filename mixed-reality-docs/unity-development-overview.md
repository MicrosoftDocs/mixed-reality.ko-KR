---
title: Unity 개발 개요
description: 시작 빌드를 시작된 혼합 현실 앱 Unity에서.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, 혼합 현실, 개발, 시작, 새 프로젝트를 이식, 기능, 카메라, 시뮬레이션, 에뮬레이션, 설명서
ms.openlocfilehash: fc40ef4eae31cf22f640be2666c5af3afb717ff3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604547"
---
# <a name="unity-development-overview"></a>Unity 개발 개요

가장 빠른 빌드 경로 [혼합된 현실 앱](app-views.md) 된 [Unity](http://aka.ms/HoloLensUnity)합니다. 탐색 하는 데 시간이 하는 것이 좋습니다 합니다 [Unity 자습서](https://unity3d.com/learn/tutorials)합니다. Unity에는 포괄적인 자산을 할 경우 [Asset Store](https://www.assetstore.unity3d.com/)합니다. Unity의 기본적인 이해를 만든 후 방문할 수 있습니다 합니다 [혼합 현실 Academy](academy.md) Unity 사용한 혼합된 현실 개발의 세부 정보를 알아보려면 합니다. 방문 해야 합니다 [Unity 혼합 현실 포럼](http://forum.unity3d.com/forums/hololens.102/) Unity에서 혼합된 현실 앱을 빌드하는 커뮤니티의 나머지와 함께 문제를 발생할 수에 합니다.

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a>Windows Mixed Reality로 기존 Unity 앱 이식

Windows Mixed Reality로 이식 하려는 기존 Unity 프로젝트에 있는 경우를 함께 수행 합니다 [Unity 포팅 가이드](porting-guides.md) 시작 하려면.

## <a name="configuring-a-new-unity-project-for-windows-mixed-reality"></a>Windows Mixed Reality에 대 한 새 Unity 프로젝트 구성

Unity 사용 하 여 혼합된 현실 앱을 처음 빌드하는 방법을 [도구를 설치](install-the-tools.md)합니다. HoloLens 하지 않고 Windows Mixed Reality 몰입 형 헤드셋 대상으로 수를 Unity의 특수 버전 지금은 해야 합니다.

새 Unity 프로젝트를 만든 경우 소규모의 두 범주로 구분 하는 Windows Mixed Reality를 변경 해야 하는 Unity 설정 가지: 프로젝트별와 장면 당 합니다.

### <a name="per-project-settings"></a>프로젝트 설정

Windows Mixed Reality를 대상으로 먼저 유니버설 Windows 플랫폼 앱으로 내보내려면 Unity 프로젝트를 설정 해야 합니다.
1. 선택 **파일 > 빌드 설정...**
2. 선택 **유니버설 Windows 플랫폼** 플랫폼에서 나열 하 고 클릭 **플랫폼 전환**
3. 설정할 **SDK** 에 **유니버설 10**
4. 설정할 **대상 장치** 하 **모든 장치** 전환할 또는 몰입 형 헤드셋을 지원 하도록 **HoloLens**
5. 설정할 **빌드 형식** 에 **D3D**
6. 설정할 **UWP SDK** 에 **가장 최근에 설치 된**

Unity 내보내기 하려는 앱을 만들어야 알 수 있도록 해야 합니다는 [몰입 형 뷰](app-views.md) 2D 보기 대신 합니다. "가상 현실 지원"을 사용 하도록 설정 하면 여는 작업을 수행:
1. **빌드 설정...**  창을 열려면 **플레이어 설정...**
2. 선택 된 **유니버설 Windows 플랫폼에 대 한 설정을** 탭
3. 확장 된 **xr 하이 설정을** 그룹
4. 에 **xr 하이 설정** 섹션을 **가상 현실 지원** 추가 확인란을를 **가상 현실 장치용** 목록.
5. 에 **xr 하이 설정을** 그룹에서 확인 **"Windows Mixed Reality"** 지원 되는 장치로 나열 됩니다. (이 나타날 수 있습니다 "Windows Holographic"으로 Unity의 이전 버전)

기본 holographic 렌더링 및 공간 입력에 이제 앱이 수행할 수 있습니다. 진행 하 고 특정 기능을 활용 하려면 앱 매니페스트에서 적절 한 기능을 선언 해야 합니다. 매니페스트 선언 되므로 모든 후속 프로젝트 내보내기에 포함 된 Unity에서 만들 수 있습니다. 설정에 포함 됩니다 **플레이어 설정 > 유니버설 Windows 플랫폼에 대 한 설정 > 게시 설정 > 기능**합니다. 혼합 현실에 대 한 일반적으로 사용 되는 Unity Api를 사용 하도록 설정 하는 것에 대 한 해당 기능은 다음과 같습니다.

|  기능  |  기능을 요구 하는 Api | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver (에 대 한 액세스 [공간 매핑](spatial-mapping.md) HoloLens에 메시)&mdash;*헤드셋의 일반 공간 추적에 필요한 기능이 없습니다* | 
|  웹캠  |  PhotoCapture 및 VideoCapture | 
|  PicturesLibrary / VideosLibrary  |  PhotoCapture 또는 VideoCapture, 각각 (저장할 때 캡처된 콘텐츠) | 
|  마이크  |  VideoCapture (오디오 캡처) 하는 경우, DictationRecognizer, GrammarRecognizer, 및 KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer (및 Unity Profiler 사용) | 

**Unity 품질 설정**

![Unity 품질 설정](images/unityqualitysettings-350px.png)<br>
*Unity 품질 설정*

HoloLens는 mobile 클래스 GPU에 있습니다. 앱은 HoloLens를 대상으로 하는 경우 전체 프레임 속도 유지 하 고 확인 하려면 품질 설정을 가장 빠른 성능을 위해 조정 해야:
1. 선택 **편집 > 프로젝트 설정 > 품질**
2. 선택 합니다 **드롭다운** 아래를 **Windows 스토어** 로고 및 선택 **가장 빠름**합니다. 설정을 때 적용 되 올바르게 알 수 있습니다 Windows Store 열에 있는 상자 및 **Fastest** 행은 녹색입니다.

### <a name="per-scene-settings"></a>장면 당 설정

**Unity 카메라 설정**

![Unity 카메라 설정](images/unitycamerasettings.png)<br>
*Unity 카메라 설정*

"가상 현실 지원" 확인란을 사용 하도록 설정 하면 합니다 [Unity 카메라](camera-in-unity.md) 구성 요소 핸들 [추적과 stereoscopic 렌더링 헤드](rendering.md)합니다. 이렇게 하려면 사용자 지정 카메라를 사용 하 여 바꾸려면 않아도가 됩니다.

앱 HoloLens 특히 대상이 되는 경우 가지 실제 세계를 통해 앱에 표시 됩니다 있도록 투명 한 디스플레이 장치에 대 한 최적화 하도록 변경 해야 하는 몇 가지 설정이 있습니다.
1. 에 **계층 구조**를 선택 합니다 **주 카메라**
2. 에 **검사기** 패널에서 변환을 설정 **위치** 하 **0, 0, 0** Unity world 원점에서 시작 되는 사용자가 헤드의 위치입니다.
3. 변경 **플래그 지우기** 하 **단색**합니다.
4. 변경 된 **백그라운드** 색 **RGBA 0,0,0,0**합니다. 검정은 HoloLens에 투명 하 게 렌더링합니다.
5. 변경 **가까운 평면-클리핑** 에 [HoloLens 권장](camera-in-unity.md#clip-planes) 0.85 (미터)입니다.

새 카메라를 만들고 삭제 하는 경우 반드시 카메라 **태그가 지정 된** 으로 **MainCamera**합니다.

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>혼합된 현실 기능 및 입력 추가

위에서 설명한 대로 프로젝트를 구성 했으면, 표준 Unity 게임 개체 (예: 카메라)가 켜 집니다 즉시에 **장착 규모 환경**, 사용자로 자동으로 업데이트 하는 카메라의 위치를 사용 하 여 이동 전 세계를 통해 해당 헤드입니다.

Windows Mixed Reality 기능에 대 한 지원 같은 추가 [공간 단계](coordinate-systems.md#spatial-coordinate-systems)를 [제스처, 동작 컨트롤러](gestures-and-motion-controllers-in-unity.md) 또는 [입력 음성](voice-input-in-unity.md) 에 직접 작성 한 Api를 사용 하 여 이루어집니다 Unity 합니다.

첫 번째 단계를 검토 해야 합니다 [눈금을 경험](coordinate-systems.md) 앱 대상으로 지정할 수 있는:
* 빌드 하려는 경우는 **방향 으로만 이동 가능한** 또는 **장착 규모 경험**를 설정 해야 합니다. Unity 공간 형식을 추적의 [고정](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)합니다.
* 빌드 하려는 경우는 **고정 크기 조정** 또는 **방 규모 환경**, Unity의 확인 해야 합니다. 공간 형식 추적을 설정 했습니다.는 [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).
* 빌드 하려는 경우는 **전 세계 규모** HoloLens에서 experience 5m 초과 로밍 하는 사용자 수를 해야 사용 하는 [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience) 구성 요소.

혼합된 현실 앱에 대 한 핵심 구성 요소를 모두 다른 Unity Api를 사용 하 여 일관 된 방식으로 노출 됩니다.
* [카메라](camera-in-unity.md)
* [좌표계](coordinate-systems-in-unity.md)
* [응시](gaze-in-unity.md)
* [제스처와 컨트롤러 동작](gestures-and-motion-controllers-in-unity.md)
* [음성 입력](voice-input-in-unity.md)
* [지속성](persistence-in-unity.md)
* [소리 공간](spatial-sound-in-unity.md)
* [공간 매핑](spatial-mapping-in-unity.md)

다 수의 혼합된 현실 앱은 원하는 사용 하려면 Unity 앱에도 표시 됩니다는 다른 주요 기능에는
* [공유 경험](shared-experiences-in-unity.md)
* [찾을 수 있는 카메라](locatable-camera-in-unity.md)
* [Focus point](focus-point-in-unity.md)
* [손실 추적](tracking-loss-in-unity.md)
* [키보드](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a>실제 또는 시뮬레이트된 장치에서 Unity 프로젝트를 실행합니다.

다음 단계를 가져온 후 holographic Unity 프로젝트를 테스트할 준비가, [Unity Visual Studio 솔루션을 빌드하고 내보내기](exporting-and-building-a-unity-visual-studio-solution.md)합니다.

준비 되었으면에서 해당 VS 솔루션을 실행할 수 있습니다 다음 앱 세 가지 방법 중 하나에서 하나를 사용 하 여 실제 또는 시뮬레이트된 장치:
* [실제 HoloLens 또는 Windows Mixed Reality 몰입 형 헤드셋에 배포](using-visual-studio.md)
* [HoloLens 에뮬레이터에 배포](using-the-hololens-emulator.md)
* [Windows Mixed Reality 몰입 형 헤드셋 시뮬레이터에 배포](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a>Unity 설명서

Windows 개발자 센터에서 사용할 수 있는이 문서에서는 외에도 Unity는 Unity 편집기와 함께 Windows Mixed Reality 기능에 대 한 설명서를 설치합니다. Unity는 설명서에는 별도 두 섹션이 포함 되어 있습니다.을 제공 합니다.
1. **Unity 스크립팅 참조**
    * 설명서의이 섹션에서는 Unity가 제공 하는 스크립팅 API의 세부 정보를 포함 합니다.
    * 통해 Unity 편집기에서 사용 하 여 액세스할 수 있는 **도움말 > 스크립팅 참조**
2. **Unity 설명서**
    * 이 설명서는 고급 기본 기술에서 Unity를 사용 하는 방법을 배울 수 있도록 설계 되었습니다.
    * 통해 Unity 편집기에서 사용 하 여 액세스할 수 있는 **도움말 > 수동**

## <a name="see-also"></a>참조
* [MR Basics 100: Unity를 사용 하 여 시작](holograms-100.md)
* [Unity에 대 한 권장된 설정](recommended-settings-for-unity.md)
* [Unity에 대 한 성능 권장 사항](performance-recommendations-for-unity.md)
* [내보내기 및 Unity Visual Studio 솔루션 빌드](exporting-and-building-a-unity-visual-studio-solution.md)
* [HoloLens 용 Unity 앱을 사용 하 여 Windows 네임 스페이스를 사용 하 여](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [Unity 및 Visual Studio를 사용 하 여 작업에 대 한 모범 사례](best-practices-for-working-with-unity-and-visual-studio.md)
* [Unity 재생 모드](unity-play-mode.md)
* [포팅 가이드](porting-guides.md)
