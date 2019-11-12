---
title: 개발자를 위한 혼합 현실 캡처
description: 개발자를 위한 혼합 현실 캡처에 대 한 모범 사례입니다.
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: mrc, 사진, 비디오, 캡처, 카메라
ms.openlocfilehash: 72600f889997c96a629faebc35aba4b4841d4d8b
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926795"
---
# <a name="mixed-reality-capture-for-developers"></a>개발자를 위한 혼합 현실 캡처

> [!NOTE]
> HoloLens 2에 대 한 새로운 MRC 기능에 대 한 지침은 아래의 [PV 카메라에서 렌더링](#render-from-the-pv-camera-opt-in) 을 참조 하세요.

사용자는 언제 든 지 [혼합 현실 캡처](mixed-reality-capture.md) (mrc) 사진 또는 비디오를 만들 수 있으므로 응용 프로그램을 개발할 때 고려해 야 할 몇 가지 사항이 있습니다. 여기에는 MRC 시각적 품질에 대 한 모범 사례와 Mrc가 캡처될 때 시스템 변경 내용에 대 한 응답성이 포함 됩니다.

또한 개발자는 혼합 현실 캡처 및 삽입을 앱에 원활 하 게 통합할 수 있습니다.

HoloLens의 MRC (처음 생성)는 720p까지 비디오와 사진을 지원 하 고, HoloLens 2의 MRC는 최대 1080p까지 비디오를 지원 하 고 최대 4K 해상도로 사진 비디오를 지원 합니다.

## <a name="the-importance-of-quality-mrc"></a>품질 MRC의 중요도

혼합 현실에서 캡처한 사진과 비디오는 사용자가 앱을 가질 수 있는 첫 번째 노출이 될 가능성이 높습니다. Microsoft Store 페이지의 혼합 현실 스크린샷 또는 소셜 네트워크에서 MRCs를 공유 하는 다른 사용자의 스크린샷 MRC를 사용 하 여 앱을 시연 하 고, 사용자를 교육 하 고, 혼합 세계 상호 작용을 공유 하 고, 사용자 연구 및 문제를 해결할 수 있습니다.

## <a name="how-mrc-impacts-your-app"></a>MRC가 앱에 미치는 영향

### <a name="enabling-mrc-in-your-app"></a>앱에서 MRC 사용

기본적으로 앱은 사용자가 혼합 된 현실 캡처를 수행할 수 있도록 하기 위해 아무것도 수행할 필요가 없습니다.

### <a name="enabling-improved-alignment-for-mrc-in-your-app"></a>앱에서 MRC에 대 한 향상 된 맞춤 사용

기본적으로 혼합 현실 캡처는 올바른 눈동자의 holographic 출력을 photo/video (PV) 카메라와 결합 합니다. 이러한 두 소스는 현재 실행 중인 몰입 형 앱에 의해 설정 된 포커스 지점을 사용 하 여 결합 됩니다.

즉, PV 카메라와 오른쪽 디스플레이 사이의 물리적인 거리가 holograms 포커스 평면 외부에 있는도 정렬 되지 않습니다.

#### <a name="set-the-focus-point"></a>포커스 지점 설정

모던 앱 (HoloLens)은 안정화 평면을 원하는 곳의 [포커스 지점을](focus-point-in-unity.md) 설정 해야 합니다. 이렇게 하면 헤드셋과 혼합 현실 캡처 모두에서 최상의 맞춤을 보장 합니다.

포커스 지점이 설정 되지 않은 경우 안정화 평면의 기본값은 2 미터입니다.

#### <a name="render-from-the-pv-camera-opt-in"></a>PV 카메라에서 렌더링 (옵트인)

HoloLens 2는 혼합 현실 캡처를 실행 하는 동안에는 몰입 형 앱이 **PV 카메라에서 렌더링** 하는 기능을 추가 합니다. 앱이 추가 렌더링을 올바르게 지원 하도록 하려면 앱에서이 기능을 옵트인 해야 합니다.

PV 카메라의 렌더링은 기본 MRC 환경에 비해 다음과 같은 향상 된 기능을 제공 합니다.
* 기본 MRC에서 볼 수 있는 것과 같은 거리에는 오프셋을 포함 하는 대신 실제 환경 및 손 (근거리 상호 작용의 경우)에 대 한 홀로그램 맞춤을 모든 거리에서 정확 하 게 지정 해야 합니다.
* V RC 출력에 대 한 holograms를 렌더링 하는 데 사용 되지 않으므로 헤드셋의 올바른 눈이 손상 되지 않습니다.

PV 카메라에서 렌더링을 사용 하도록 설정 하는 세 가지 단계가 있습니다.
1. PhotoVideoCamera HolographicViewConfiguration 사용
2. 추가 HolographicCamera render를 처리 합니다.
3. 이 추가 HolographicCamera에서 셰이더 및 코드가 올바르게 렌더링 되는지 확인 합니다.

##### <a name="enable-the-photovideocamera-holographicviewconfiguration"></a>PhotoVideoCamera HolographicViewConfiguration 사용

옵트인 (opt in) 하려면 앱에서 PhotoVideoCamera의 [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration)을 사용 하도록 설정 하기만 하면 됩니다.
```csharp
var display = Windows.Graphics.Holographic.HolographicDisplay.GetDefault();
var view = display.TryGetViewConfiguration(Windows.Graphics.Holographic.HolographicViewConfiguration.PhotoVideoCamera);
if (view != null)
{
   view.IsEnabled = true;
}
```

##### <a name="handle-the-additional-holographiccamera-render-in-directx"></a>DirectX에서 추가 HolographicCamera render를 처리 합니다.

앱이 PV 카메라에서 렌더링 하도록 옵트인 (opt in) 하 고 혼합 현실 캡처를 시작 하면 다음을 수행 합니다.
1. HolographicSpace의 CameraAdded 이벤트가 발생 합니다. 지금은 앱에서 카메라를 처리할 수 없는 경우이 이벤트가 지연 될 수 있습니다.
2. 이벤트가 완료 되 면 (그리고 처리 되지 않은 지연과 없음) HolographicCamera는 다음 HolographicFrame의 Ad 카메라 목록에 표시 됩니다.

혼합 현실 캡처가 중지 될 때 (또는 혼합 현실 캡처를 실행 하는 동안 앱에서 뷰 구성을 사용 하지 않도록 설정 하는 경우) HolographicCamera는 다음 HolographicFrame의 RemovedCameras 목록에 표시 되 고 HolographicSpace의 CameraRemoved 이벤트가 발생 합니다. 시키고.

HolographicCamera에는 카메라가 속한 구성을 식별 하는 데 도움이 되는 [Viewconfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) 속성이 추가 되었습니다.

##### <a name="handle-the-additional-holographiccamera-render-in-unity"></a>Unity에서 추가 HolographicCamera render를 처리 합니다.

>[!NOTE]
> PV 카메라에서 렌더링 하는 Unity 지원은 개발 중 이며 아직 사용할 수 없습니다. 이 설명서는 PV 카메라의 렌더링을 지 원하는 Unity 빌드를 사용할 수 있을 때 업데이트 됩니다.

##### <a name="verify-shaders-and-code-support-additional-cameras"></a>셰이더 및 코드에서 추가 카메라 지원 확인

혼합 현실 캡처를 실행 하 고 비정상적인 맞춤, 누락 된 콘텐츠 또는 성능 문제를 확인 합니다. 셰이더 및 코드를 적절 하 게 업데이트 합니다.

추가 카메라에 대 한 렌더링을 지원 하지 않는 특정 장면이 있는 경우 PhotoVideoCamera의 HolographicViewConfiguration을 사용 하지 않도록 설정할 수 있습니다.

### <a name="disabling-mrc-in-your-app"></a>앱에서 MRC를 사용 하지 않도록 설정

#### <a name="2d-app"></a>2D 앱

혼합 현실 캡처가를 실행 하는 경우 2D 앱은 시각적 콘텐츠를 가립니다 선택할 수 있습니다.
* [DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-present) 플래그로 제공
* [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://docs.microsoft.com/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag) 플래그를 사용 하 여 앱의 스왑 체인 만들기
* Windows 10 5 월 2019 업데이트를 사용 하 여 ApplicationView의 [IsScreenCaptureEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled) 을 설정 합니다.

#### <a name="immersive-app"></a>몰입 형 앱

몰입 형 앱은 다음과 같은 방법으로 혼합 현실 캡처에서 해당 시각적 콘텐츠를 제외 하도록 선택할 수 있습니다.
* HolographicCameraRenderingParameter의 [IsContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled) 을 설정 하 여 연결 된 프레임에 대 한 혼합 현실 캡처 사용 안 함
* 연결 된 holographic 카메라에 대해 혼합 현실 캡처를 사용 하지 않도록 HolographicCamera의 [IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled) 설정

#### <a name="password-keyboard"></a>암호 키보드

Windows 10 5 월 2019 업데이트를 사용 하면 암호나 pin 키보드를 볼 때 시각적 콘텐츠가 혼합 현실 캡처에서 자동으로 제외 됩니다.

### <a name="knowing-when-mrc-is-active"></a>MRC가 활성 상태인 경우 파악

앱에서 [appcapture](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.AppCapture) 클래스를 사용 하 여 시스템 혼합 현실 캡처가 실행 되는 시기 (오디오 또는 비디오)를 알 수 있습니다.

>[!NOTE]
>AppCapture의 [GetForCurrentView](https://docs.microsoft.com/uwp/api/windows.media.capture.appcapture.getforcurrentview) API는 장치에서 혼합 현실 캡처를 사용할 수 없는 경우 null을 반환할 수 있습니다. 앱이 일시 중단 될 때 CapturingChanged 이벤트의 등록을 취소 하는 것도 중요 합니다. 그렇지 않으면 MRC가 차단 된 상태가 될 수 있습니다.

### <a name="best-practices-hololens-specific"></a>모범 사례 (HoloLens 관련)

MRC는 개발자의 추가 작업 없이도 작동 하지만 앱의 최상의 혼합 현실 캡처 환경을 제공 하기 위해 알아두어야 할 몇 가지 사항이 있습니다.

**MRC는 홀로그램의 알파 채널을 사용 하 여 [카메라](locatable-camera.md) 이미지와 혼합 합니다.**

가장 중요 한 단계는 불투명 검정을 지우지 않고 앱이 투명 검정을 선택 취소 하 고 있는지 확인 하는 것입니다. Unity에서는 기본적으로 MixedRealityToolkit를 사용 하 여이 작업을 수행 하지만 비 Unity에서 개발 하는 경우 한 줄로 변경 해야 할 수 있습니다.

앱이 투명 검정을 지우지 않는 경우 MRC에 표시 될 수 있는 아티팩트는 다음과 같습니다.

**예제 실패**: 콘텐츠 주위의 검은색 가장자리 (투명 검정으로 지우지 못함)

<table>
<tr>
<td>
<img src="images/chessboardblackedges-300px.jpg" alt="Failing to clear to transparent black: black edge artifacts around holograms"/>
</td>
<td>
<img src="images/fieldblackedges-300px.jpg" alt="Failing to clear to transparent black: black edge artifacts around holograms"/>
</td>
</tr>
</table>

**예제 실패**: 홀로그램의 전체 배경 장면이 검은색으로 표시 됩니다. 배경 알파 값을 1로 설정 하면 검은색 배경이 발생 합니다.

![배경 알파 값을 1로 설정 하면 검은색 배경이 발생 합니다.](images/clearopaqueblack-300px.png)

**예상 결과**: Holograms는 실제와 제대로 혼합 되어 표시 됩니다 (투명 검정으로 지우는 경우 예상 결과).

![투명 검정으로 지우는 경우 예상 결과](images/cleartransparentblack-300px.png)

**해결 방법**:
* 알파 값이 0 인 불투명 검정으로 표시 되는 모든 콘텐츠를 변경 합니다.
* 앱이 투명 검정으로 선택 취소 되어 있는지 확인 합니다.
* Unity는 기본적으로 MixedRealityToolkit를 사용 하 여 자동으로 지우도록 선택을 취소 하지만 Unity가 아닌 앱 인 경우에는 ID3D11DeiceContext:: ClearRenderTargetView ()와 함께 사용 되는 색을 수정 해야 합니다. 불투명 검정 (0, 0, 0, 1)이 아닌 투명 한 검정 (0, 0, 0, 0)을 지울 수 있도록 하려고 합니다.

원하는 경우 이제 자산의 알파 값을 조정할 수 있지만 일반적으로 필요 하지 않습니다. 대부분의 경우에는 MRCs가 적절 하 게 보입니다. MRC는 미리 곱한 알파를 가정 합니다. 알파 값은 MRC 캡처에만 영향을 줍니다.

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a>HoloLens에서 MRC를 사용 하도록 설정할 때 발생할 수 있는 사항

다음은 다른 설명이 없는 한 HoloLens (첫 번째 생성) 및 HoloLens 2에 모두 적용 됩니다.

* 시스템이 30Hz 렌더링으로 응용 프로그램을 제한 합니다. 그러면 앱이 일정 한 예산 예약을 유지 하지 않아도 되 고 30fps의 MRC 비디오 레코드 프레임 속도와 일치 하는 것을 위해 MRC를 실행 하기 위한 몇 가지 여유가 생성 됩니다.
* 장치 오른쪽에 있는 홀로그램 콘텐츠가 "반짝"로 표시 될 수 있습니다. MRC를 기록/스트리밍할 때 텍스트를 읽는 데 더 어려울 수 있으며, 홀로그램 가장자리가 더 jaggy 표시 될 수 있습니다 ( **HoloLens 2** 에서 세 번째 카메라 렌더링에 대 한 옵트인에서이 손상을 방지 함).
* MRC 사진과 비디오는 응용 프로그램에서 응용 프로그램을 사용 하도록 설정 하는 경우 응용 프로그램의 [포커스 지점을](focus-point-in-unity.md) 고려 하며,이는 holograms 정확 하 게 배치 되도록 도와줍니다. 비디오의 경우 포커스 지점 깊이가 현저 하 게 변경 되는 경우 holograms는 곡선으로 약간 부드럽게 표시 될 수 있습니다. 포커스 지점과 다른 깊이에 있는 Holograms는 실제 세계에서 오프셋 된 것 처럼 보일 수 있습니다 (포커스 점이 2 미터로 설정 되었지만 홀로그램은 1 미터에 위치 하는 경우 아래 예제 참조).

![2 미터의 Holograms은 전 세계에 완벽 하 게 등록 된 것으로 보입니다. 종가 또는 먼 거리가 Holograms는 약간 오프셋할 수 있습니다.](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a>앱 내에서 MRC 기능 통합

혼합 현실 앱은 앱 내에서 MRC 사진 또는 비디오 캡처를 시작할 수 있으며, 캡처된 콘텐츠는 장치의 "카메라 롤"에 저장 하지 않고도 앱에서 사용할 수 있게 됩니다. 사용자 지정 MRC 레코더를 만들거나 기본 제공 카메라 캡처 UI를 활용할 수 있습니다. 

### <a name="mrc-with-built-in-camera-ui"></a>기본 제공 카메라 UI를 사용 하는 MRC

개발자는 *[카메라 캡처 UI API](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* 를 사용 하 여 몇 줄의 코드만으로 사용자가 캡처한 혼합 현실 사진 또는 비디오를 가져올 수 있습니다.

이 API는 기본 제공 MRC 카메라 UI를 시작 하 여 사용자가 사진 또는 비디오를 촬영 하 고 결과 캡처를 앱에 반환 합니다.  카메라 UI를 직접 만들거나 캡처 스트림에 대 한 하위 수준 액세스를 필요로 하는 경우 사용자 지정 혼합 현실 캡처 레코더를 만들 수 있습니다.

### <a name="creating-a-custom-mrc-recorder"></a>사용자 지정 MRC 레코더 만들기

사용자는 항상 시스템 MRC 캡처 서비스를 사용 하 여 사진이 나 비디오를 트리거할 수 있지만 응용 프로그램은 사용자 지정 카메라 앱을 빌드할 수 있지만 MRC와 마찬가지로 카메라 스트림에 holograms를 포함 합니다. 이를 통해 응용 프로그램은 사용자를 대신 하 여 캡처를 시작 하거나 사용자 지정 기록 UI를 빌드하거나 MRC 설정을 사용자 지정 하 여 몇 가지 예의 이름을 지정할 수 있습니다.

**HoloStudio는 MRC 효과를 사용 하 여 사용자 지정 MRC 카메라를 추가 합니다.**

![HoloStudio는 MRC 효과를 사용 하 여 사용자 지정 MRC 카메라를 추가 합니다.](images/cameraiconholostudio-300px.jpg)

Unity 응용 프로그램은 holograms를 사용 하도록 설정 하는 속성에 대 한 [Locatable_camera_in_Unity](locatable-camera-in-unity.md) 를 확인 해야 합니다.

다른 응용 프로그램은 [Windows 미디어 캡처 api](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaCapture) 를 사용 하 여 카메라를 제어 하 고, 스틸 및 비디오에 가상 holograms 및 응용 프로그램 오디오를 포함 하는 Mrc 비디오 및 오디오 효과를 추가 하 여이 작업을 수행할 수 있습니다.

응용 프로그램에는 효과를 추가 하는 두 가지 옵션이 있습니다.
* 이전 API: [MediaCapture. AddEffectAsync ()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addeffectasync)
* 새 Microsoft 권장 API (개체를 반환 하 여 동적 속성을 조작할 수 있음): [MediaCapture () / AddVideoEffectAsync (](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync) ): [MediaCapture ()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) : 응용 프로그램이 [IVideoEffectDefinition](https://docs.microsoft.com/uwp/api/Windows.Media.Effects.IVideoEffectDefinition) 및 [IAudioEffectDefinition](https://docs.microsoft.com/uwp/api/windows.media.effects.iaudioeffectdefinition)의 고유한 구현을 만들도록 요구 합니다. 샘플 사용에 대해서는 MRC 효과 샘플을 참조 하세요.

>[!NOTE]
> MixedRealityCapture 네임 스페이스는 Visual Studio에서 인식 되지 않지만 문자열은 여전히 유효 합니다.

MRC 비디오 효과 (**MixedRealityCapture. MixedRealityCaptureVideoEffect**)

|  속성 이름  |  작업 표시줄의 검색 상자에  |  기본값  |  설명 | 
|----------|----------|----------|----------|
|  StreamType  |  UINT32 ([Mediastreamtype](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaStreamType))  |  1 (VideoRecord)  |  이 효과가 사용 되는 캡처 스트림을 설명 합니다. 오디오를 사용할 수 없습니다. | 
|  HologramCompositionEnabled  |  부울  |  TRUE  |  비디오 캡처에서 holograms을 사용 하거나 사용 하지 않도록 설정 하는 플래그입니다. | 
|  RecordingIndicatorEnabled  |  부울  |  TRUE  |  홀로그램 캡처 중에 화면에서 기록 표시기를 사용 하거나 사용 하지 않도록 설정 하는 플래그입니다. | 
|  VideoStabilizationEnabled  |  부울  |  FALSE  |  HoloLens 트래커에서 구동 하는 비디오 안정화를 사용 하거나 사용 하지 않도록 설정 하는 플래그입니다. | 
|  VideoStabilizationBufferLength  |  UINT32  |  0  |  비디오 안정화에 사용 되는 기록 프레임의 수를 설정 합니다. 0은 전력 및 성능 측면에서 0-대기 시간 및 거의 "무료"입니다. 15는 대기 시간 및 메모리의 15 프레임에 대 한 비용으로 최고 품질을 위해 권장 됩니다. | 
|  GlobalOpacityCoefficient  |  float  |  0.9 (HoloLens) 1.0 (모던 헤드셋)  |  홀로그램의 전역 불투명도 계수를 0.0 (완전히 투명)에서 1.0 (완전히 불투명)로 설정 합니다. | 
|  BlankOnProtectedContent  |  부울  |  FALSE  |  보호 된 콘텐츠를 표시 하는 2d UWP 앱이 있는 경우 빈 프레임을 반환 하거나 사용 하지 않도록 설정 하는 플래그입니다. 이 플래그가 false이 고 2d UWP 앱이 보호 된 콘텐츠를 표시 하는 경우 2d UWP 앱은 헤드셋과 혼합 현실 캡처 모두에서 보호 된 콘텐츠 질감으로 교체 됩니다. |
|  ShowHiddenMesh  |  부울  |  FALSE  |  Holographic 카메라의 숨겨진 영역 메시 및 인접 콘텐츠를 표시 하거나 사용 하지 않도록 설정 하는 플래그입니다. |
| OutputSize | 사이즈 | 0, 0 | 비디오 안정화를 위해 자른 후 원하는 출력 크기를 설정 합니다. 0 또는 잘못 된 출력 크기가 지정 된 경우 기본 자르기 크기가 선택 됩니다. |
| PreferredHologramPerspective | UINT32 | 1 (PhotoVideoCamera) | 캡처할 holographic 카메라 보기 구성을 나타내는 데 사용 되는 열거형입니다. 0 (표시)을 설정 하면 앱에 사진/비디오 카메라에서 렌더링 하 라는 메시지가 표시 되지 않습니다. |

MRC 오디오 효과 (**MixedRealityCapture. MixedRealityCaptureAudioEffect**)

<table>
<tr>
<th>속성 이름</th>
<th>작업 표시줄의 검색 상자에</th>
<th>기본값</th>
<th>설명</th>
</tr>
<tr>
<td>MixerMode</td>
<td>UINT32</td>
<td>2</td>
<td>
<ul>
<li>0: Mic 오디오만</li>
<li>1: 시스템 오디오만</li>
<li>2: Mic 및 시스템 오디오</li>
</ul>
</td>
</tr>
</table>

### <a name="simultaneous-mrc-limitations"></a>동시 MRC 제한 사항

MRC에 동시에 액세스 하는 여러 앱에 대 한 특정 제한 사항이 있습니다.

#### <a name="photovideo-camera-access"></a>사진/비디오 카메라 액세스

Photo/video 카메라는 동시에 액세스할 수 있는 프로세스의 수로 제한 됩니다. 프로세스가 비디오를 기록 하거나 사진을 촬영 하는 동안 다른 프로세스에서 사진/비디오 카메라를 획득 하는 데 실패 합니다. (혼합 현실 캡처와 표준 사진/비디오 캡처 모두에 적용 됨)

HoloLens 2를 사용 하는 경우 앱은 MediaCaptureInitializationSettings ' [SharingMode](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode) 속성을 사용 하 여 photo/video 카메라를 독점적으로 제어할 필요가 없는 경우 sharedreadonly를 실행 하도록 지정할 수 있습니다. 이렇게 하면 캡처의 해상도와 프레임 속도가 카메라에서 제공 하도록 구성 된 다른 앱으로 제한 됩니다.

##### <a name="built-in-mrc-photovideo-camera-access"></a>기본 제공 MRC 사진/비디오 카메라 액세스

Windows 10에 기본 제공 되는 MRC 기능 (Cortana, 시작 메뉴, 하드웨어 바로 가기, Miracast, Windows 장치 포털을 통해):
* 기본적으로 ExclusiveControl를 사용 하 여 실행 됩니다.

그러나 공유 모드에서 작동 하도록 각 하위 시스템에 대 한 지원이 추가 되었습니다.
* 앱이 photo/video 카메라에 대 한 ExclusiveControl 액세스를 요청 하는 경우 기본 제공 MRC는 앱의 요청이 성공 하도록 photo/video 카메라를 사용 하 여 자동으로 중지 됩니다.
* 앱이 ExclusiveControl 때 기본 제공 MRC가 시작 되 면 기본 제공 MRC가 SharedReadOnly 모드에서 실행 됩니다.

이 공유 모드 기능에는 다음과 같은 제한 사항이 있습니다.
* Cortana, 하드웨어 바로 가기 또는 시작 메뉴를 통한 사진: Windows 10 4 월 2018 업데이트 (이상)가 필요 합니다.
* Cortana, 하드웨어 바로 가기 또는 시작 메뉴를 통한 비디오: Windows 10 4 월 2018 업데이트 (이상) 필요
* Miracast를 통한 MRC 스트리밍: Windows 10 10 월 2018 업데이트 (이상)가 필요 합니다.
* Windows 장치 포털을 통해 또는 HoloLens 도우미 앱을 통해 MRC 스트리밍: HoloLens 2 필요

>[!NOTE]
> 다른 앱에서 photo/video 카메라를 사용 하는 경우 기본 제공 MRC 카메라 UI의 해상도와 프레임 속도가 일반 값에서 감소할 수 있습니다.

#### <a name="mrc-access"></a>MRC 액세스

Windows 10 4 월 2018 업데이트를 사용 하면 MRC 스트림에 액세스 하는 여러 앱에 대해 더 이상 제한이 없습니다 (그러나 사진/비디오 카메라에 대 한 액세스에는 여전히 제한이 있음).

Windows 10 4 월 2018 업데이트 이전에는 앱의 사용자 지정 MRC 레코더를 시스템 MRC와 함께 사용할 수 없습니다 (사진 캡처, 비디오 캡처 또는 Windows 장치 포털에서 스트리밍).

## <a name="see-also"></a>참고 항목
* [혼합 현실 캡처](mixed-reality-capture.md)
* [Spectator View](spectator-view.md)
