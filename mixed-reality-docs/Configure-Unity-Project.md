---
title: Windows Mixed Reality 용 새 Unity 프로젝트 구성
description: MRTK 없이 Unity 프로젝트를 구성 합니다.
author: yoyoz
ms.author: Yoyoz
ms.date: 04/15/2018
ms.topic: article
keywords: Unity, 혼합 현실, 개발, 시작, 새 프로젝트
ms.openlocfilehash: 68dded9d0fc9e861bdda56c4954d72ddafafa686
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326098"
---
# <a name="configure-a-new-unity-project-for-windows-mixed-reality"></a>Windows Mixed Reality 용 새 Unity 프로젝트 구성 

(MRTK v2 Unity 프로젝트에 이미 가져온 경우 건너뜀)

혼합 현실 도구 키트를 가져오지 않고 새 Unity 프로젝트를 생성 하려는 경우 소규모의 두 범주로 구분 하는 Windows Mixed Reality를 수동으로 변경 해야 하는 Unity 설정 가지: 프로젝트별와 장면 당 합니다.

## <a name="per-project-settings"></a>프로젝트 설정

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

![Unity 품질 설정](images/getting-started-unity-quality-settings.jpg)<br>
*Unity xr 하이 설정*

기본 holographic 렌더링 및 공간 입력에 이제 앱이 수행할 수 있습니다. 진행 하 고 특정 기능을 활용 하려면 앱 매니페스트에서 적절 한 기능을 선언 해야 합니다. 매니페스트 선언 되므로 모든 후속 프로젝트 내보내기에 포함 된 Unity에서 만들 수 있습니다. 설정에 포함 됩니다 **플레이어 설정 > 유니버설 Windows 플랫폼에 대 한 설정 > 게시 설정 > 기능**합니다. 혼합 현실에 대 한 일반적으로 사용 되는 Unity Api를 사용 하도록 설정 하는 것에 대 한 해당 기능은 다음과 같습니다.

|  기능  |  기능을 요구 하는 Api | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver (에 대 한 액세스 [공간 매핑](spatial-mapping.md) HoloLens에 메시)&mdash;*헤드셋의 일반 공간 추적에 필요한 기능이 없습니다* | 
|  웹캠  |  PhotoCapture 및 VideoCapture | 
|  PicturesLibrary / VideosLibrary  |  PhotoCapture 또는 VideoCapture, 각각 (저장할 때 캡처된 콘텐츠) | 
|  마이크  |  VideoCapture (오디오 캡처) 하는 경우, DictationRecognizer, GrammarRecognizer, 및 KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer (및 Unity Profiler 사용) | 

**Unity 품질 설정**

![Unity 품질 설정](images/getting-started-unity-quality-settings.jpg)<br>
*Unity 품질 설정*

HoloLens는 mobile 클래스 GPU에 있습니다. 앱은 HoloLens를 대상으로 하는 경우 전체 프레임 속도 유지 하 고 확인 하려면 품질 설정을 가장 빠른 성능을 위해 조정 해야:
1. 선택 **편집 > 프로젝트 설정 > 품질**
2. 선택 합니다 **드롭다운** 아래를 **Windows 스토어** 로고 및 선택 **매우 낮음**합니다. 설정을 때 적용 되 올바르게 알 수 있습니다 Windows Store 열에 있는 상자 및 **매우 낮음** 행은 녹색입니다.

## <a name="per-scene-settings"></a>장면 당 설정

**Unity 카메라 설정**

![Unity 카메라 설정](images/Unitycamerasettings.png)<br>
*Unity 카메라 설정*

"가상 현실 지원" 확인란을 사용 하도록 설정 하면 합니다 [Unity 카메라](camera-in-unity.md) 구성 요소 핸들 [추적과 stereoscopic 렌더링 헤드](rendering.md)합니다. 이렇게 하려면 사용자 지정 카메라를 사용 하 여 바꾸려면 않아도가 됩니다.

앱 HoloLens 특히 대상이 되는 경우 가지 실제 세계를 통해 앱에 표시 됩니다 있도록 투명 한 디스플레이 장치에 대 한 최적화 하도록 변경 해야 하는 몇 가지 설정이 있습니다.
1. 에 **계층 구조**를 선택 합니다 **주 카메라**
2. 에 **검사기** 패널에서 변환을 설정 **위치** 하 **0, 0, 0** Unity world 원점에서 시작 되는 사용자가 헤드의 위치입니다.
3. 변경 **플래그 지우기** 하 **단색**합니다.
4. 변경 된 **백그라운드** 색 **RGBA 0,0,0,0**합니다. 검정은 HoloLens에 투명 하 게 렌더링합니다.
5. 변경 **가까운 평면-클리핑** 에 [HoloLens 권장](camera-in-unity.md#clip-planes) 0.85 (미터)입니다.

새 카메라를 만들고 삭제 하는 경우 반드시 카메라 **태그가 지정 된** 으로 **MainCamera**합니다.


## <a name="see-also"></a>참조
* [혼합 현실을 Toolkit v2](mrtk-getting-started.md)
* [Unity 개발 개요](unity-development-overview.md)
