---
title: Windows Mixed Reality에 대 한 새 Unity 프로젝트 구성
description: Windows Mixed Reality 용 Unity 프로젝트를 구성 하는 방법에 대 한 지침
author: thetuvix
ms.author: alexturn
ms.date: 04/15/2018
ms.topic: article
keywords: Unity, 혼합 현실, 개발, 시작, 새 프로젝트
ms.openlocfilehash: 64f7006bf212f49ab1c478d5dbb1fc1f5ab15497
ms.sourcegitcommit: 161f3c5a80f6988a9c4af26e29481fee06840e0f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87390107"
---
# <a name="configure-a-new-unity-project-for-windows-mixed-reality"></a>Windows Mixed Reality에 대 한 새 Unity 프로젝트 구성 

## <a name="overview"></a>개요

Windows Mixed Reality (WMR)는 Windows 10 운영 체제의 일부로 도입 된 Microsoft 플랫폼입니다. WMR 플랫폼을 사용 하면 holographic 및 VR 디스플레이 장치에서 디지털 콘텐츠를 렌더링 하는 응용 프로그램을 빌드할 수 있습니다.

WMR에 대해 설정할 때 두 가지 경로를 사용할 수 있습니다. 첫 번째 옵션은 WMR 환경을 자동으로 설정 하는 mrtk ( [Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) ) v2를 설치 하는 것입니다. 두 번째 옵션은 WMR를 사용 하기 위해 몇 가지 Unity 설정을 수동으로 변경 하는 것입니다. 

> [!NOTE]
> 나중에 언제 든 지 MRTK를 가져올 수 있으므로 수동 경로를 먼저 이동 하는 데는 아무런 영향이 없습니다.

WMR 수동 설치를 선택 하는 경우 변경 해야 하는 설정은 프로젝트별 및 장면의 두 가지 범주로 구분 됩니다.

## <a name="per-project-settings"></a>프로젝트별 설정

WMR에 대해 변경 해야 하는 첫 번째 설정은 프로젝트 플랫폼입니다. 
1. **파일 > 빌드 설정** ...을 선택 합니다.
2. 플랫폼 목록에서 **유니버설 Windows 플랫폼** 을 선택 하 고 **플랫폼 전환** 을 클릭 합니다.
3. **SDK** 를 **유니버설 10** 으로 설정
4. 몰입 형 헤드셋을 지원 하거나 **HoloLens** 로 전환 하기 위해 **대상 장치** 를 **모든 장치로** 설정
5. **빌드 유형을** **D3D** 로 설정
6. **UWP SDK** 를 **최신 설치** 로 설정

![Unity XR 설정](images/unity-uwp-settings.png)<br>
*Unity XR 설정*

플랫폼이 올바르게 구성 된 후에는 앱이 내보낼 때 2D 보기 대신 [몰입 형 보기](app-views.md) 를 만들어야 한다는 것을 Unity에 알려야 합니다.
1. **빌드 설정 ...** 창에서 **플레이어 설정 ...** 을 엽니다.
2. 유니버설 Windows 플랫폼 탭 **에 대 한 설정** 을 선택 하 고 **XR 설정** 그룹을 확장 합니다.
3. **XR 설정** 섹션에서 가상 **현실 지원 됨** 확인란을 선택 하 여 **가상 현실 장치** 목록을 추가 합니다.
4. **XR 설정** 그룹에서 **"Windows Mixed Reality"** 가 지원 되는 장치로 나열 되는지 확인 합니다. 이 옵션은 이전 버전의 Unity에서 **Windows Holographic** 표시 될 수 있습니다.

![Unity UWP 설정](images/xrsettings.png)<br>
*Unity XR 설정*

### <a name="updating-the-manifest"></a>매니페스트를 업데이트 하는 중

이제 앱이 holographic 렌더링 및 공간 입력을 처리할 수 있습니다. 그러나 특정 기능을 활용 하려면 앱이 해당 매니페스트에 적절 한 기능을 선언 해야 합니다. **플레이어 설정 > 설정 유니버설 Windows 플랫폼 > 게시 설정 > 기능**으로 이동 하 여 프로젝트 기능을 찾을 수 있습니다. 

내보낸 이후 모든 프로젝트에 포함 하기 위해 Unity에서 매니페스트 선언을 만드는 것이 좋습니다. 혼합 현실에 일반적으로 사용 되는 Unity Api를 사용 하는 데 적용 되는 기능은 다음과 같습니다.

|  기능  |  기능을 필요로 하는 Api | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver (HoloLens의 [공간 매핑](spatial-mapping.md) 메시에 대 한 액세스) &mdash; *헤드셋의 일반 공간 추적에 필요한 기능이 없습니다* . | 
|  웹캠  |  사진 캡처 및 VideoCapture | 
|  PicturesLibrary/VideosLibrary  |  각각 사진 캡처 또는 VideoCapture (캡처된 콘텐츠를 저장 하는 경우) | 
|  마이크  |  VideoCapture (오디오 캡처 시), DictationRecognizer, GrammarRecognizer 및 KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer (및 Unity 프로파일러를 사용 하려면) | 

### <a name="quality-settings"></a>품질 설정

HoloLens에는 모바일 클래스 GPU가 있습니다. 앱이 HoloLens를 대상으로 하는 경우 앱의 품질 설정이 전체 프레임 속도를 유지 하기 위해 가장 빠른 성능을 위해 조정 되도록 합니다.
1. **편집 > 프로젝트 설정 > 품질** 을 선택 합니다.
2. **Windows 스토어** 로고 아래의 **드롭다운** 을 선택 하 고 **매우 낮음**을 선택 합니다. Windows 스토어 열 및 **매우 낮음** 행의 상자가 녹색이면 설정이 올바르게 적용된 것입니다.

![Unity 품질 설정](images/getting-started-unity-quality-settings.jpg)<br>
*Unity 품질 설정*

## <a name="per-scene-settings"></a>장면 별 설정

### <a name="unity-camera-settings"></a>Unity 카메라 설정

**가상 현실을 지원 됨** 을 선택 하면 [Unity 카메라](camera-in-unity.md) 구성 요소가 [헤드 추적 및 stereoscopic 렌더링](rendering.md)을 처리 합니다. 즉, 기본 카메라 개체를 사용자 지정 카메라로 바꿀 필요가 없습니다.

앱이 특별히 HoloLens를 대상으로 하는 경우에는 장치의 투명 디스플레이를 최적화 하기 위해 몇 가지 설정을 변경 해야 합니다. 이러한 설정을 통해 holographic 콘텐츠를 실제 세계에 표시할 수 있습니다.
1. **계층**에서 **기본 카메라** 를 선택 합니다.
2. **검사기** 패널에서 변환 **위치** 를 **0, 0, 0** 으로 설정 하 여 사용자의 헤드 위치가 Unity 세계 원점에서 시작 되도록 합니다.
3. **Clear 플래그** 를 **Solid 색**으로 변경 합니다.
4. **배경색** 을 **RGBA 0, 0**, 0, 0으로 변경 합니다. 검은색은 HoloLens에서 투명 하 게 렌더링 됩니다.
5. **클립 평면** 을 [HoloLens 권장](camera-in-unity.md#clip-planes) 0.85 (미터) 근처로 변경 합니다.

![Unity 카메라 설정](images/Unitycamerasettings.png)<br>
*Unity 카메라 설정*

> [!IMPORTANT]
> 새 카메라를 삭제 하 고 만드는 경우 새 카메라에 **maincamera**로 태그가 지정 되어 있는지 확인 합니다.

## <a name="see-also"></a>참고 항목
* [Mixed Reality Toolkit v2](mrtk-getting-started.md)
* [Unity 개발 개요](unity-development-overview.md)
