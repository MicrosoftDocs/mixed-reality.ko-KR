---
title: Windows Mixed Reality에 대 한 새 Unity 프로젝트 구성
description: MRTK 없이 Unity 프로젝트 구성
author: thetuvix
ms.author: alexturn
ms.date: 04/15/2018
ms.topic: article
keywords: Unity, 혼합 현실, 개발, 시작, 새 프로젝트
ms.openlocfilehash: af30cf91eda1b654bea6048c34f63c61238626c7
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437118"
---
# <a name="configure-a-new-unity-project-for-windows-mixed-reality"></a>Windows Mixed Reality에 대 한 새 Unity 프로젝트 구성 

(MRTK v 2를 Unity 프로젝트로 이미 가져온 경우에는 건너뜀)

Mixed Reality 도구 키트를 가져오지 않고 새 Unity 프로젝트를 만들려는 경우에는 Windows Mixed Reality에 대해 수동으로 변경 해야 하는 몇 가지 Unity 설정, 즉 프로젝트별 및 장면의 두 가지 범주로 분류 됩니다.

## <a name="per-project-settings"></a>프로젝트별 설정

Windows Mixed Reality를 대상으로 하려면 먼저 유니버설 Windows 플랫폼 앱으로 내보내도록 Unity 프로젝트를 설정 해야 합니다. 
1. **파일 > 빌드 설정** ...을 선택 합니다.
2. 플랫폼 목록에서 **유니버설 Windows 플랫폼** 을 선택 하 고 **플랫폼 전환** 을 클릭 합니다.
3. **SDK** 를 **유니버설 10** 으로 설정
4. 몰입 형 헤드셋을 지원 하거나 **HoloLens** 로 전환 하기 위해 **대상 장치** 를 **모든 장치로** 설정
5. **빌드 유형을** **D3D** 로 설정
6. **UWP SDK** 를 **최신 설치** 로 설정

그런 다음 내보내려는 앱이 2D 보기 대신 [몰입 형 보기](app-views.md) 를 만들어야 한다고 Unity에 알려야 합니다. "가상 현실 지원"을 사용 하도록 설정 하 여이 작업을 수행 합니다.
1. **빌드 설정 ...** 창에서 **플레이어 설정 ...** 을 엽니다.
2. 유니버설 Windows 플랫폼 탭 **에 대 한 설정** 선택
3. **XR 설정** 그룹을 확장 합니다.
4. **XR 설정** 섹션에서 가상 **현실 지원 됨** 확인란을 선택 하 여 **가상 현실 장치** 목록을 추가 합니다.
5. **XR 설정** 그룹에서 **"Windows Mixed Reality"** 가 지원 되는 장치로 나열 되는지 확인 합니다. (이전 버전의 Unity에서 "Windows Holographic"로 표시 될 수 있음)

Unity 품질 설정 ![](images/getting-started-unity-quality-settings.jpg)<br>
*Unity xr 설정*

이제 앱에서 기본 holographic 렌더링 및 공간 입력을 수행할 수 있습니다. 특정 기능을 사용 하려면 앱이 해당 매니페스트에 적절 한 기능을 선언 해야 합니다. 매니페스트 선언은 Unity에서 수행할 수 있으므로 이후의 모든 프로젝트 내보내기에 포함 됩니다. 설정은 **플레이어 설정 > 유니버설 Windows 플랫폼 > 게시 설정 > 기능에 대 한 설정**에서 찾을 수 있습니다. 혼합 현실에 일반적으로 사용 되는 Unity Api를 사용 하도록 설정 하는 데 적용 되는 기능은 다음과 같습니다.

|  접근 권한 값  |  기능을 필요로 하는 Api | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver (HoloLens의 [공간 매핑](spatial-mapping.md) 메시에 대 한 액세스)&mdash;*헤드셋의 일반 공간 추적에 필요한 기능이 없습니다* . | 
|  웹캠  |  사진 캡처 및 VideoCapture | 
|  PicturesLibrary/VideosLibrary  |  각각 사진 캡처 또는 VideoCapture (캡처된 콘텐츠를 저장 하는 경우) | 
|  Microphone  |  VideoCapture (오디오 캡처 시), DictationRecognizer, GrammarRecognizer 및 KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer (및 Unity 프로파일러를 사용 하려면) | 

**Unity 품질 설정**

Unity 품질 설정 ![](images/getting-started-unity-quality-settings.jpg)<br>
*Unity 품질 설정*

HoloLens에는 모바일 클래스 GPU가 있습니다. 앱이 HoloLens를 대상으로 하는 경우 최고 성능을 위해 품질 설정을 조정 하 여 전체 프레임 속도를 유지 해야 합니다.
1. **편집 > 프로젝트 설정 > 품질** 을 선택 합니다.
2. **Windows 스토어** 로고 아래의 **드롭다운** 을 선택 하 고 **매우 낮음**을 선택 합니다. Windows 스토어 열의 상자와 **매우 낮은** 행이 녹색 인 경우 설정이 올바르게 적용 됨을 알 수 있습니다.

## <a name="per-scene-settings"></a>장면 별 설정

**Unity 카메라 설정**

![Unity 카메라 설정](images/Unitycamerasettings.png)<br>
*Unity 카메라 설정*

"가상 현실 지원" 확인란을 사용 하도록 설정 하면 [Unity 카메라](camera-in-unity.md) 구성 요소가 [헤드 추적 및 stereoscopic 렌더링](rendering.md)을 처리 합니다. 이 작업을 수행 하기 위해 사용자 지정 카메라로 바꿀 필요는 없습니다.

앱이 특별히 HoloLens를 대상으로 하는 경우 장치의 투명 디스플레이를 최적화 하기 위해 변경 해야 하는 몇 가지 설정이 있습니다. 따라서 앱은 실제 세계에 표시 됩니다.
1. **계층**에서 **기본 카메라** 를 선택 합니다.
2. **검사기** 패널에서 transform **위치** 를 **0, 0, 0** 으로 설정 하 여 사용자 헤드의 위치가 Unity 세계 원점에서 시작 되도록 합니다.
3. **Clear 플래그** 를 **Solid 색**으로 변경 합니다.
4. **배경색** 을 **RGBA 0, 0**, 0, 0으로 변경 합니다. 검은색은 HoloLens에서 투명 하 게 렌더링 됩니다.
5. **클립 평면** 을 [HoloLens 권장](camera-in-unity.md#clip-planes) 0.85 (미터) 근처로 변경 합니다.

새 카메라를 삭제 하 고 만드는 경우 카메라에 **maincamera**로 **태그가 지정** 되어 있는지 확인 합니다.


## <a name="see-also"></a>참고 항목
* [Mixed Reality Toolkit v2](mrtk-getting-started.md)
* [Unity 개발 개요](unity-development-overview.md)
