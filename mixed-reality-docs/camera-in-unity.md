---
title: Unity에서 카메라
description: Unity의 주 카메라에 대 한 Windows Mixed Reality 개발 holographic 렌더링을 위해 사용 하는 방법
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit mixedrealitytoolkit, mixedrealitytoolkit unity, holographic 렌더링, holographic, 몰입도 포커스 지점을, 깊이 버퍼, 클립 방향 으로만 이동 가능한 위치, 불투명, 투명 하 고,
ms.openlocfilehash: 8ea5a1f53351faab1b2863a0afac74e958b4b1a0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597780"
---
# <a name="camera-in-unity"></a>Unity에서 카메라

혼합된 현실 헤드셋을 wear holographic 전 세계의 중심 됩니다. Unity [카메라](http://docs.unity3d.com/Manual/class-Camera.html) 구성 요소는 stereoscopic 렌더링을 자동으로 처리 및 따라온다는 헤드 이동 및 회전에 "가상 현실" 지원 "Windows Mixed Reality"를 사용 하 여 선택한 프로젝트가 있으면 (장치로 Windows 스토어 플레이어 설정의 다른 설정 구역). 이 Unity의 이전 버전에서 "Windows Holographic"으로 나타날 수 있습니다.

그러나 시각적 품질을 최적화 하기 위해 하 고 [홀로그램 안정성](hologram-stability.md), 아래에 설명 된 카메라 설정을 설정 해야 합니다.

>[!NOTE]
>이러한 설정은 앱의 각 장면에서 카메라에 적용 해야 합니다.
>
>기본적으로 unity에서 새 장면을 만들 때 포함 됩니다 아래의 제대로 적용 된 설정을 없는 카메라 구성 요소를 포함 하는 계층 구조에서 주 카메라 GameObject입니다.

## <a name="holographic-vs-immersive-headsets"></a>몰입 형 헤드셋 및 holographic

Unity 카메라 구성 요소에 대해 기본 설정은 현실 세계 없기 때문에 skybox 모양 배경 필요한 기존 3D 응용 프로그램입니다.
* 실행 하는 경우는  **[몰입 형 헤드셋](immersive-headset-hardware-details.md)**, 사용자에 게 모든 렌더링 및 따라서 skybox를 유지 하려는 경우가 많습니다.
* 그러나 실행 하는 경우는 **holographic 헤드셋** 와 같은 [HoloLens](hololens-hardware-details.md), 실제 렌더링 모든 카메라 뒤에 표시 됩니다. 이렇게 하려면 카메라 배경이 투명 하 게 (HoloLens, 투명으로 검은색 렌더링)을 설정 하는 대신 Skybox 질감:
    1. 주 카메라 계층 패널에서 선택
    2. 검사기 창에서 카메라 구성 요소를 찾 및 단색을 나타내는 플래그 지우기 드롭다운 Skybox에서 변경
    3. 배경 색 선택기를 선택 하 고 RGBA 값 (0, 0, 0, 0)으로 변경

스크립트 코드를 사용 하 여 런타임 시 인지 여부를 확인 헤드셋 몰입 형 또는 holographic 인하여 [HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html)합니다.


## <a name="positioning-the-camera"></a>카메라 위치

(X:로 사용자의 시작 위치를 가정 하는 경우 앱의 레이아웃을 쉽게 됩니다. 0, Y: 0, Z: 0). 주 카메라 사용자의 헤드의 움직임 추적, 이후 주 카메라의 시작 위치를 설정 하 여 사용자의 시작 위치를 설정할 수 있습니다.
1. 주 카메라 계층 패널에서 선택
2. 검사기 창에서 변환 구성 요소를 찾 및 (x:에서의 위치를 변경 합니다. 0, Y: 1, z:-10) (x:에 0, Y: 0, Z: 0)

   ![Unity의 검사기 창에는 카메라](images/maincamera-350px.png)<br>
   *Unity의 검사기 창에는 카메라*

## <a name="clip-planes"></a>클립 평면

에 너무 가까이 콘텐츠를 렌더링할 사용자 수 혼합된 현실에서 편리 하 게 합니다. 조정할 수 있습니다는 [근처 및 훨씬 클립 평면](hologram-stability.md#hologram-render-distances) 카메라 구성 요소입니다.
1. 주 카메라 계층 패널에서 선택
2. 검사기 창에서 카메라 구성 요소 클리핑 평면 찾을.85 0.3에서 거의 텍스트 변경 하십시오. 훨씬 더 가까이 렌더링 되는 내용은 사용자 뜨거움 발생할 수 있습니다 당 피해 야 합니다 [거리 지침 렌더링](hologram-stability.md#hologram-render-distances)합니다.

## <a name="multiple-cameras"></a>여러 카메라

장면에서 카메라의 여러 구성 요소가 있을 때 Unity stereoscopic 렌더링에 사용 하는 카메라를 알고 있고 어떤 GameObject를 확인 하 여 헤드 추적 MainCamera 태그입니다.

## <a name="recentering-a-seated-experience"></a>Recentering 탐구 환경

작성 하는 경우는 [장착 규모 환경](coordinate-systems.md)를 호출 하 여 사용자의 현재 헤드 위치 둘러싸기의 Unity의 세계 원본 수는 **[xr 하이 합니다. InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** 메서드.

## <a name="reprojection-modes"></a>Reprojection 모드

HoloLens 및 몰입 형 헤드셋 photons은 내보낼 때 사용자의 실제 헤드 위치의 모든 오측에 맞게 앱을 렌더링 하는 각 프레임을 reproject 됩니다.

기본적으로:

* **몰입 형 헤드셋** 여 홀로그램 오측 위치와 방향에 대 한 앱은 지정된 된 프레임에 대 한 깊이 버퍼를 제공 하는 경우 조정 하는 위치 reprojection 수행 됩니다.  깊이 버퍼를 제공 하지 않으면 시스템 방향에서 예측만 수정 됩니다.
* **Holographic 헤드셋** 같은 HoloLens 위치 reprojection 여부 앱은 해당 깊이 버퍼를 제공 하는지 여부를 수행 합니다.  위치 reprojection HoloLens의 깊이 버퍼 없이 불가능은 렌더링은 실제 세계에서 제공 하는 안정적인 배경의 스파스 경우가 많습니다.

작성할 수 있도록 하는 것이 알고 있는 경우는 [방향 으로만 이동 가능한 환경을](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience) 엄격 하 게 본문 잠긴 콘텐츠 (예: 360도 비디오 콘텐츠)를 사용 하 여 설정할 수 있습니다 명시적으로 방향을 설정 의해서만 되도록 reprojection 모드 [ HolographicSettings.ReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) 하 [HolographicReprojectionMode.OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html)합니다.

## <a name="sharing-your-depth-buffers-with-windows"></a>Windows를 사용 하 여 깊이 버퍼에 공유

각 프레임에에서 제공 됩니다 앱 두 상승이 중 홀로그램 안정성, 헤드셋의 형식을 기반으로 하는 Windows 앱의 깊이 버퍼를 공유에 대 한 렌더링 하는 있습니다.
* **몰입 형 헤드셋** 오측 위치와 방향에 대 한 사용자 제공 조정 깊이 버퍼를 제공 하는 경우 위치 reprojection를 수행할 수 있습니다.
* **Holographic 헤드셋** HoloLens가 자동으로 선택 하는 등을 [지점 집중](focus-point-in-unity.md) 깊이 버퍼를 제공 하는 경우 가장 콘텐츠를 교차 하는 평면을 따라 홀로그램 안정성을 최적화 합니다.

Unity 앱 Windows를 깊이 버퍼를 제공할 수 있는지 여부를 설정 합니다.
1. 로 이동 **편집할** > **프로젝트 설정** > **플레이어** > **유니버설 Windows 플랫폼 탭**  >  **Xr 하이 설정을**합니다.
2. 확장 된 **Windows Mixed Reality SDK** 항목입니다.
3. 선택 또는 선택 취소 합니다 **깊이 버퍼 공유 사용** 확인란 합니다.  이 업그레이드 된 이전 프로젝트에 대해 기본적으로이 Unity에 추가 된 기능과 선택 되지 것입니다 후에 만든 새 프로젝트에서 기본으로 선택 됩니다.

Windows 깊이 버퍼를 제공으로 Windows 매핑할 수 있습니다 정확 하 게 정규화 된 픽셀 깊이 값 깊이 버퍼에 다시 미터 거리 주 카메라에서 Unity에서 설정한 근거리 및 원거리 평면을 사용 하 여 시각적 품질을 개선할 수 있습니다.  에 렌더링 핸들 깊이 전달 하는 경우 일반적인 방법으로 값을 일반적으로 해야 여기서 반투명 렌더링 깊이 버퍼 기존를 통해 표시 하는 동안에 쓰기를 전달 하지만 색 픽셀을 혼동할 수 있습니다는 reprojection 세밀 하 게 합니다.  렌더링 패스 남습니다 대부분에 최종 깊이 픽셀의 깊이 부정확 한 값을 사용 하 여를 알고 있으면 선택 취소 하면 "사용 깊이 버퍼를 공유 하 여" 더 뛰어난 시각적 품질을 가져오려는 가능성이 있습니다.

## <a name="mixed-reality-toolkits-automatic-scenesetup"></a>혼합된 현실 도구 키트의 자동 장면 설치
가져올 때 [MRTK Unity 패키지를 릴리스](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) 에서 프로젝트를 복제 또는 합니다 [GitHub 리포지토리](https://github.com/Microsoft/MixedRealityToolkit-Unity), Unity에서 새 메뉴 ' 혼합 현실 Toolkit'를 찾을 것입니다. '구성' 메뉴 아래에서 적용 혼합 현실 장면 [설정] 메뉴를 표시 됩니다. 기본 카메라를 제거 하 고 기본 구성 요소 추가 클릭 하면 [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab)하십시오 [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), 및 [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab)합니다.

![장면 설치용 MRTK 메뉴](images/MRTK_Input_Menu.png)<br>
*장면 설치용 MRTK 메뉴*

![MRTK 자동 장면 설치](images/MRTK_HowTo_Input1.png)<br>
*MRTK 자동 장면 설치*

## <a name="mixedrealitycamera-prefab"></a>MixedRealityCamera prefab
프로젝트 패널에서 수동으로 추가할 수 있습니다. Prefabs로 이러한 구성 요소를 찾을 수 있습니다. 검색 하는 경우 **MixedRealityCamera**, 두 개의 다른 카메라 prefabs 참조 할 수 있습니다. 차이점은 **MixedRealityCamera** 전용인 카메라 prefab 반면 **MixedRealityCameraParent** 텔레포트, 동작 등 몰입 형 헤드셋에 대 한 추가 구성 요소를 포함 합니다. 컨트롤러를 경계입니다.

![MRTK에서 카메라 prefabs](images/MRTK_HowTo_Input2.png)<br>
*MRTK에서 카메라 prefabs*

**MixedRealtyCamera** HoloLens 및 몰입 형 헤드셋을 모두 지원 합니다. 장치 유형을 검색 하 고 플래그 지우기 등 Skybox 속성 최적화 합니다. 다음 사용자 지정 커서 동작 컨트롤러 모델 같은 사용자 지정 하는 Floor 유용한 속성 중 일부를 찾을 수 있습니다.

![커서 및 Floor 동작 컨트롤러에 대 한 속성](images/MRTK_HowTo_Input3.png)<br>
*커서 및 Floor 동작 컨트롤러에 대 한 속성*

## <a name="see-also"></a>참조
* [홀로그램 안정성](hologram-stability.md)
* [MixedRealityToolkit Main Camera.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs)
