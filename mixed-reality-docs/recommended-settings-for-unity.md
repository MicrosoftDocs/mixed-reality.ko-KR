---
title: Unity 권장 설정
description: Unity는 프로젝트 설정을 통해 전환할 수 있는 혼합 현실에 특정 한 몇 가지 동작을 제공 합니다.
author: troy-ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: unity, 설정, 혼합 현실
ms.openlocfilehash: e7628a8653fffbab9c792161ac8ff1666b47fa62
ms.sourcegitcommit: f523b74a549721b6bec69cb5d2eca5b7673a793c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85570329"
---
# <a name="recommended-settings-for-unity"></a>Unity 권장 설정

Unity는 일반적으로 모든 플랫폼의 평균 사례에 해당 하는 기본 옵션 집합을 제공 합니다. 그러나 Unity는 프로젝트 설정을 통해 전환할 수 있는 혼합 현실에 특정 한 몇 가지 동작을 제공 합니다.

## <a name="performant-environment-set-up"></a>고성능 환경 설정

### <a name="low-quality-settings"></a>저품질 설정

사용자 환경에 대 한 **Unity 품질 설정을** **매우 낮게**수정 하는 것이 중요 합니다. 그러면 응용 프로그램에서 적절 한 프레임 속도로 performantly을 실행 하는 데 도움이 됩니다. 이는 HoloLens 개발에 매우 중요 합니다. 모던 헤드셋에서 개발 하는 경우 VR 경험을 켜는 데스크톱의 사양에 따라 가장 낮은 품질의 매개 변수 없이도 프레임 속도를 달성할 수 있습니다.

Unity 2018 LTS +에서는 프로젝트의 품질 수준을 다음과 같이 설정할 수 있습니다.

**Edit**  >  **프로젝트 설정**  >  **품질** 편집 > 아래에서 **낮은** 품질 수준까지 아래쪽 화살표를 클릭 하 여 **기본값** 을 설정 합니다.

### <a name="lighting-settings"></a>조명 설정

품질 장면 설정과 마찬가지로 혼합 현실 응용 프로그램에 대해 최적의 조명 설정을 설정 하는 것이 중요 합니다. Unity에서 일반적으로 장면에 가장 큰 영향을 주는 조명 설정은 **실시간 세계 조명**입니다. **창**  >  **렌더링**  >  **조명 설정**  >  **실시간 전역 조명**으로 이동 하 여이를 끌 수 있습니다.

다른 조명 설정인 **구운 Global 조명이**있습니다. 이 설정은 몰입 형 헤드셋에서 성능과 시각적으로 눈에 띄는 결과를 제공할 수 있지만 일반적으로 HoloLens 개발에는 적용 되지 않습니다. **구운 Global Illumniation** 은 알 수 없고 변화 하는 환경의 특성 때문에 일반적으로 HoloLens 장면에서 찾을 수 없는 정적 gameobject에 대해서만 계산 됩니다.

자세한 내용은 [Unity에서 글로벌 조명을](https://docs.unity3d.com/Manual/GIIntro.html) 읽어 보세요. 

>[!NOTE]
> **실시간 전역 조명이** **장면 별로** 설정 되므로 개발자는 프로젝트의 모든 Unity 장면에 대해이 속성을 저장 해야 합니다.

### <a name="single-pass-instancing-rendering-path"></a>단일 패스 인스턴스 렌더링 경로

혼합 현실 응용 프로그램에서 장면은 사용자의 각 눈 마다 한 번씩 두 번 렌더링 됩니다. 기존의 3D 개발과 비교 하 여 계산 해야 하는 작업량을 늘리는 것이 효과적입니다. 따라서 Unity에서 가장 효율적인 렌더링 경로를 선택 하 여 CPU와 GPU 시간을 모두 저장 하는 것이 중요 합니다. 단일 패스 인스턴스 렌더링은 혼합 현실 앱에 대 한 Unity 렌더링 파이프라인을 최적화 하므로 모든 프로젝트에 대해 기본적으로이 설정을 사용 하도록 설정 하는 것이 좋습니다.

Unity 프로젝트에서이 기능을 사용 하도록 설정 하려면

1)  **플레이어 XR 설정** 열기 ( **Edit**  >  **프로젝트 설정**편집  >  **플레이어**  >  **XR 설정**으로 이동)
2) **스테레오 렌더링 방법** 드롭다운 메뉴에서 **단일 패스 인스턴스** 를 선택 합니다 (**가상 현실 지원 됨** 확인란을 선택 해야 함).

이 렌더링 방법에 대 한 자세한 내용은 Unity에서 다음 문서를 참조 하세요.

- [고급 스테레오 렌더링을 사용 하 여 AR 및 VR 성능을 최대화 하는 방법](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [단일 패스 인스턴스](https://docs.unity3d.com/Manual/SinglePassInstancing.html)

>[!NOTE]
> 단일 패스 인스턴스화된 렌더링의 일반적인 문제 중 하나는 개발자에 게 인스턴스에 대해 작성 되지 않은 기존 사용자 지정 셰이더가 이미 있는 경우 발생 합니다. 이 기능을 사용 하도록 설정한 후 개발자는 일부 Gameobject 한 눈에만 렌더링 되는 것을 알 수 있습니다. 이는 연결 된 사용자 지정 셰이더가 인스턴스에 적합 한 속성을 포함 하지 않기 때문입니다.
>
> 이 문제를 해결 하는 방법에 대해서는 Unity의 [HoloLens에 대 한 단일 패스 스테레오 렌더링](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) 을 참조 하세요.

### <a name="enable-depth-buffer-sharing"></a>깊이 버퍼 공유 사용

사용자의 인식에서 가장 나은 홀로그램 안정성을 얻으려면 Unity에서 **깊이 버퍼 공유** 속성을 사용 하도록 설정 하는 것이 좋습니다. 이 기능을 켜면 Unity는 응용 프로그램에서 생성 된 깊이 맵을 Windows Mixed Reality 플랫폼과 공유 합니다. 그러면 플랫폼은 응용 프로그램에 의해 렌더링 되는 지정 된 프레임의 장면에 대해 특별히 홀로그램 안정성을 최적화 하는 데 도움이 됩니다.

Unity 프로젝트에서이 기능을 사용 하도록 설정 하려면

1) **플레이어 XR 설정** 열기 ( **Edit**  >  **프로젝트 설정**편집  >  **플레이어**  >  **XR 설정**으로 이동)
2) **가상 현실 sdk**Windows **Enable Depth Buffer Sharing**  >  **Mixed reality** 확장 (**가상 현실 지원** 확인란을 선택 해야 함)에서 깊이 버퍼 공유 사용 확인란을 선택 합니다.

또한이 패널의 **깊이 서식** 설정에서 **16 비트 깊이** 를 선택 하는 것이 좋습니다 (특히 HoloLens 개발의 경우). 24 비트와 비교 하 여 16 비트를 선택 하면 데이터를 이동/처리 하지 않아도 되므로 대역폭 요구 사항이 크게 줄어듭니다.

Windows Mixed Reality 플랫폼에서 홀로그램 안정성을 최적화 하기 위해 깊이 버퍼를 사용 하 여 정확 하 고 렌더링 된 모든 holograms 화면에 일치 시킵니다. 따라서에서 깊이 버퍼를 공유 하는 경우 색을 렌더링할 때 깊이를 렌더링 하는 것도 중요 합니다. Unity에서 대부분의 불투명 또는 TransparentCutout 재질은 기본적으로 깊이를 렌더링 하지만 투명 하 고 텍스트 개체는 일반적으로 셰이더가 종속 되어 있지만 일반적으로 깊이를 렌더링 하지 않습니다.

[Mixed Reality Toolkit 표준 셰이더](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md)를 사용 하 여 투명 개체의 깊이를 렌더링 하는 경우:

1) MRTK 표준 셰이더를 사용 하는 투명 재질을 선택 하 고 검사기 편집기 창을 엽니다.
2) 깊이 버퍼 공유 경고 내에서 **지금 수정** 단추를 선택 합니다. **렌더링 모드** 를 **사용자 지정**으로 설정 하 여 수동으로 수행할 수도 있습니다. 그런 다음 **모드** 를 **Transparent** 로 설정 하 고 마지막으로 **Depth Write** 를 **On** 으로 설정 합니다.

> [!IMPORTANT]
> 개발자는 카메라의 근거리/원거리 평면 설정과 함께 이러한 값을 변경할 때 Z를 사용 하는 것에 주의 해야 합니다. 두 gameobject가 동일한 픽셀로 렌더링 하려고 하 고 깊이 버퍼의 충실도 (즉, z 깊이) Unity는 다른 개체가 앞에 있는 개체를 알 수 없습니다. 개발자는 두 게임 개체가 동일한 z 깊이 값에 대해 *싸* 차는 것을 확인 합니다. 이는 카메라에서 z 깊이에 대해 계산 하는 각 개체에 대해 더 큰 범위의 값이 있으므로 24 비트 깊이 형식으로 전환 하 여 해결할 수 있습니다.
>
> 그러나 특히 HoloLens 개발의 경우 카메라의 근거리 및 far 비행기를 보다 작은 범위로 수정 하 고 16 비트 깊이 형식을 유지 하는 것이 좋습니다. Z 깊이는 근거리 및 원거리 카메라 평면을 따라 값의 범위에 대해 비선형으로 매핑됩니다. 이는 장면에서 *주 카메라* 를 선택 하 여 수정할 수 있으며, **검사기**에서 **근처 & 근처의 클리핑 평면** 값을 변경 하 여 범위를 줄입니다 (즉, 100m 또는 기타 x 값 등)

>[!IMPORTANT]
> Unity는 16 비트 깊이 형식을 사용할 때 [스텐실 버퍼를 만들지](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) 않습니다. 따라서 [8 비트 스텐실 버퍼](https://docs.unity3d.com/Manual/SL-Stencil.html)를 만들 24 비트 깊이 형식을 선택 하지 않으면 일부 Unity UI 효과 및 기타 스텐실 필수 효과가 작동 하지 않습니다.

### <a name="building-for-il2cpp"></a>IL2CPP 용 빌드

Unity는 .NET 스크립팅 백 엔드에 대해 더 이상 지원 되지 않으므로, 개발자가 UWP visual studio 빌드에 대해 **IL2CPP** 를 활용 하는 것이 좋습니다. 이는 다양 한 이점을 제공 하지만 **IL2CPP** 용 Unity에서 visual studio 솔루션을 빌드하는 것은 이전 .net 메서드보다 훨씬 느릴 수 있습니다. 따라서 개발 반복 시간을 절약 하기 위해 **IL2CPP** 빌드에 대 한 모범 사례를 따르는 것이 좋습니다.

1) 매번 미리 작성 된 파일을 다시 사용 하 여 프로젝트를 동일한 디렉터리에 빌드하여 증분 빌드를 활용 합니다.
2) 프로젝트에 대 한 맬웨어 방지 소프트웨어 검색 사용 안 함 & 빌드 폴더
   - Windows 10 설정 앱에서 **바이러스 & 위협 방지** 를 엽니다.
   - **바이러스 & 위협 방지 설정** 에서 **설정 관리** 를 선택 합니다.
   - **제외** 섹션에서 **제외 추가 또는 제거** 를 선택 합니다.
   - **제외 추가** 를 클릭 하 고 Unity 프로젝트 코드 및 빌드 출력을 포함 하는 폴더를 선택 합니다.
3) 빌드에 SSD 활용

자세한 정보는 [IL2CPP에 대 한 빌드 시간 최적화](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) 를 참조 하세요.

> [!NOTE]
> 또한 대용량 자산(스크립트 파일 제외) 또는 지속적으로 변화하는 장면/자산을 포함하는 Unity 프로젝트에 맞게 [캐시 서버](https://docs.unity3d.com/Manual/CacheServer.html)를 설정하는 것도 유용할 수 있습니다. 프로젝트를 열 때 Unity는 정식 자산을 개발자 컴퓨터에 내부 캐시 형식으로 저장합니다. 따라서 항목이 수정되면 다시 가져온 후 다시 처리해야 합니다. 모든 개발자가 새 변경 내용을 로컬로 다시 가져오지 않고, 이 프로세스를 한 번 수행한 후 캐시 서버에 저장하고, 이후에 다른 개발자와 공유할 수 있으므로 시간을 절약할 수 있습니다.

## <a name="publishing-properties"></a>게시 속성

### <a name="holographic-splash-screen"></a>Holographic 시작 화면

HoloLens에는 모바일 클래스 CPU와 GPU가 있습니다. 즉, 앱을 로드 하는 데 약간의 시간이 걸릴 수 있습니다. 앱을 로드 하는 동안 사용자에 게는 검은색만 표시 되므로 진행 상황을 궁금해 할 수 있습니다. Reassure를 로드 하는 동안 holographic 시작 화면을 추가할 수 있습니다.

Holographic 시작 화면을 전환 하려면:

1) **Edit**  >  **프로젝트 설정**편집  >  **플레이어** 페이지로 이동
2) **Windows 스토어** 탭을 클릭 하 고 **시작 이미지** 섹션을 엽니다.
3) **Windows Holographic > Holographic 시작 이미지** 속성 아래에 원하는 이미지를 적용 합니다.
    - **Unity 시작 화면 표시** 옵션을 설정/해제 하면 unity 브랜드 시작 화면을 설정 하거나 해제할 수 있습니다. Unity Pro 라이선스가 없는 경우 Unity 브랜드 시작 화면이 항상 표시 됩니다.
    - **Holographic 시작 이미지가** 적용 되는 경우 Unity 시작 화면 표시 확인란의 설정 여부에 관계 없이 항상 표시 됩니다. 사용자 지정 holographic 시작 이미지를 지정 하는 것은 Unity Pro 라이선스가 있는 개발자만 사용할 수 있습니다.

|  Unity 시작 화면 표시  |  Holographic 시작 이미지  |  동작 |
|----------|----------|----------|
|  켜기  |  없음  |  5 초 동안 또는 앱이 로드 될 때까지 기본 Unity 시작 화면을 표시 합니다. |
|  켜기  |  사용자 지정  |  5 초 동안 또는 앱이 로드 될 때까지 사용자 지정 시작 화면을 표시 합니다. |
|  끄기  |  없음  |  앱이 로드 될 때까지 투명 한 검정색 (없음)을 표시 합니다. |
|  끄기  |  사용자 지정  |  5 초 동안 또는 앱이 로드 될 때까지 사용자 지정 시작 화면을 표시 합니다. |

자세한 내용은 [Unity의 시작 화면 설명서](https://docs.unity3d.com/Manual/class-PlayerSettingsSplashScreen.html) 를 참조 하세요.

### <a name="tracking-loss"></a>추적 손실

혼합 현실 헤드셋은 [전 세계에서 잠긴 좌표계](coordinate-systems-in-unity.md)를 구성 하는 환경에 따라 holograms 위치를 유지할 수 있습니다. 헤드셋이 세계에서 자신을 찾을 수 없는 경우 헤드셋은 *추적을 잃어버린*것으로 간주 됩니다. 이러한 경우 공간 단계, 공간 앵커 및 공간 매핑과 같은 세계에서 잠긴 좌표계에 의존 하는 기능은 작동 하지 않습니다.

추적 손실이 발생 하는 경우 Unity의 기본 동작은 holograms 렌더링을 중지 하 고, [게임 루프](https://docs.unity3d.com/Manual/ExecutionOrder.html)를 일시 중지 하 고, 사용자가 응시 하는 추적 손실 알림을 표시 하는 것입니다. 사용자 지정 알림은 추적 손실 이미지 형식으로 제공 될 수도 있습니다. 전체 환경에 대 한 추적에 의존 하는 앱의 경우에는 추적이 다시 확보 될 때까지 Unity에서이를 완전히 처리할 수 있습니다. 개발자는 추적 손실을 추적 하는 동안 표시할 사용자 지정 이미지를 제공할 수 있습니다.

손실 된 추적 이미지를 사용자 지정 하려면:

1) **Edit**  >  **프로젝트 설정**편집  >  **플레이어** 페이지로 이동
2) **Windows 스토어** 탭을 클릭 하 고 **시작 이미지** 섹션을 엽니다.
3) **Windows Holographic > 추적 손실 이미지** 속성 아래에 원하는 이미지를 적용 합니다.

#### <a name="opt-out-of-automatic-pause"></a>자동 일시 중지 옵트아웃

일부 앱은 추적을 요구 하지 않을 수 있습니다 (예: 360도 비디오 뷰어 등의 [방향 전용 앱](coordinate-systems-in-unity.md) ). 추적이 손실 되는 동안 중단 없이 처리를 계속 해야 할 수도 있습니다. 이러한 경우 앱은 추적 동작의 기본 손실을 옵트아웃 (opt out) 할 수 있습니다. 이를 선택 하는 개발자는 추적 손실 시나리오에서 제대로 렌더링 되지 않는 개체를 숨기 거 나 비활성화할 책임이 있습니다. 대부분의 경우이 경우에 렌더링 하는 데 권장 되는 콘텐츠는 주 카메라를 중심으로 하는 본문 잠금 콘텐츠입니다.

자동 일시 중지 동작을 옵트아웃 하려면:

1) **Edit**  >  **프로젝트 설정**편집  >  **플레이어** 페이지로 이동
2) **Windows 스토어** 탭을 클릭 하 고 **시작 이미지** 섹션을 엽니다.
3) **Holographic 일시 중지 및 이미지 표시** 확인란을 선택 하 여 Windows >를 수정 합니다.

#### <a name="tracking-loss-events"></a>손실 이벤트 추적

추적이 손실 될 때 사용자 지정 동작을 정의 하려면 전역 [추적 손실 이벤트](tracking-loss-in-unity.md)를 처리 합니다.

### <a name="capabilities"></a>기능

앱이 특정 기능을 활용 하려면 해당 매니페스트에 적절 한 기능을 선언 해야 합니다. 매니페스트 선언은 Unity에서 수행할 수 있으므로 이후의 모든 프로젝트 내보내기에 포함 됩니다.

다음을 수행 하 여 혼합 현실 응용 프로그램에 기능을 사용 하도록 설정할 수 있습니다.

1) **Edit**  >  **프로젝트 설정**편집  >  **플레이어** 페이지로 이동
2) **Windows 스토어** 탭을 클릭 하 고 **게시 설정** 섹션을 열고 **기능** 목록을 찾습니다.

Holographic apps에 일반적으로 사용 되는 Api를 사용 하도록 설정 하는 데 적용 되는 기능은 다음과 같습니다.
<br>

|  기능  |  기능을 필요로 하는 Api |
|----------|----------|
|  SpatialPerception  |  SurfaceObserver |
|  웹캠  |  사진 캡처 및 VideoCapture |
|  PicturesLibrary/VideosLibrary  |  각각 사진 캡처 또는 VideoCapture (캡처된 콘텐츠를 저장 하는 경우) |
|  마이크  |  VideoCapture (오디오 캡처 시), DictationRecognizer, GrammarRecognizer 및 KeywordRecognizer |
|  InternetClient  |  DictationRecognizer (및 Unity 프로파일러를 사용 하려면) |

## <a name="see-also"></a>참고 항목

* [Unity 개발 개요](unity-development-overview.md)
* [혼합 현실 성능 이해](understanding-performance-for-mixed-reality.md)
* [Unity의 권장 성능](performance-recommendations-for-unity.md)
