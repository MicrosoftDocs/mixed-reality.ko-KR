---
title: 개발자를 위한 실제로 캡처 혼합
description: 개발자를 위한 혼합된 현실에 대 한 모범 사례를 캡처합니다.
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: mrc, 사진, 비디오, 캡처, 카메라
ms.openlocfilehash: d1675d2d6c74c6d15ca245a66719e00f2a7c2111
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694369"
---
# <a name="mixed-reality-capture-for-developers"></a>개발자를 위한 실제로 캡처 혼합

> [참고!] 참조 [PV 카메라에서 렌더링](#render-from-the-pv-camera-opt-in) 아래 HoloLens 2에 대 한 새로운 MRC 기능에 대 한 지침에 대 한 합니다.

사용자가 수행할 수 있으므로 [혼합 현실 캡처](mixed-reality-capture.md) (MRC) 사진 또는 언제 든 지 비디오를 응용 프로그램을 개발할 때는 염두 해야 할 몇 가지 사항입니다. 여기에 MRC 시각적 품질 및 MRCs 캡처되는 동안 시스템 변경 내용에 응답 속도 대 한 모범 사례입니다.

개발자 혼합된 현실 캡처 및 삽입 하 여 앱에도 원활 하 게 통합할 수 있습니다.

HoloLens (항목인 1 세대)에 MRC에는 HoloLens 2는 MRC 4k 해상도로 등록 최대 1080p 및 사진과 비디오를 지원 하지만 최대 720p, 사진 및 비디오를 지원 합니다.

## <a name="the-importance-of-quality-mrc"></a>MRC 품질의 중요성

혼합된 현실 사진 캡처되고 비디오는 앱의 사용자에 게는 처음 접하는 가능성이 높습니다. 혼합된 현실 스크린 샷을 Microsoft Store 페이지 또는 MRCs 소셜 네트워크에서 공유 하는 다른 사용자로 여부입니다. MRC 데모 앱, 사용자 교육, 사용자가 해당 혼합된 환경 상호 작용을 공유 하도록 권장 하는 데 사용할 수 및 사용자 설문 조사 및 문제 해결에 대 한 합니다.

## <a name="how-mrc-impacts-your-app"></a>MRC 앱에 미치는 영향을

### <a name="enabling-mrc-in-your-app"></a>앱에서 사용 하도록 설정 하면 MRC

기본적으로 앱 사용자가 혼합된 현실 캡처를 수행할 수 있도록 모든 작업을 수행할 필요가 없습니다.

### <a name="enabling-improved-alignment-for-mrc-in-your-app"></a>앱에서 향상 된 MRC 맞춤을 사용 하도록 설정

기본적으로 혼합된 현실 캡처 (PV) 사진/비디오 카메라를 사용 하 여 오른쪽 눈 holographic 출력을 결합합니다. 이러한 두 개의 소스에서 현재 실행 중인 몰입 형 앱 설정의 포커스 지점을 사용 하 여 결합 됩니다.

이 포커스 문자표 홀로그램 (인해 PV 카메라 및 오른쪽 표시 간의 실제 거리) 어울리지 않습니다는 것을 의미 합니다.

#### <a name="set-the-focus-point"></a>포커스 지점을 설정 합니다.

몰입 형 앱 (HoloLens) 설정 해야 합니다 [지점 집중](focus-point-in-unity.md) 되도록 해당 안정화 평면 원할 때마다 원하는 위치입니다. 이렇게 하면 캡처 혼합된 현실 헤드셋 모두에 가장 좋은 맞춤 합니다.

포커스 지점을 설정 되지 않은 경우 두 가지 단위가 안정화 평면 기본값은입니다.

#### <a name="render-from-the-pv-camera-opt-in"></a>옵트인 (opt in) PV 카메라에서 렌더링

몰입 형 앱에 대 한 기능을 추가 하는 HoloLens 2 **PV 카메라에서 렌더링** 혼합된 현실 캡처 실행 되는 동안. 앱 추가 렌더링을 올바르게 지원 하도록 앱은이 기능에 옵트인 합니다.

기본 MRC 환경을 통해 다음과 같은 개선 사항이 PV 카메라 제품에서 렌더링 합니다.
* 물리적 환경 및이 손 (거의 상호 작용) 모두에 맞춤 홀로그램 해야 정확 하 게 전혀 거리를 하는 대신 오프셋 거리의 포커스 지점 외에 기본 MRC 볼 수 있습니다.
* 헤드셋에서 오른쪽 눈 손상 되지, MRC 출력 홀로그램 렌더링에 사용 되지 않습니다.

PV 카메라에서 렌더링을 사용 하도록 설정 하려면 세 가지 단계가 있습니다.
1. PhotoVideoCamera HolographicViewConfiguration를 사용 하도록 설정
2. 추가 HolographicCamera 렌더링 처리
3. 확인할 셰이더와 코드에이 추가 HolographicCamera에서 올바르게 렌더링

##### <a name="enable-the-photovideocamera-holographicviewconfiguration"></a>PhotoVideoCamera HolographicViewConfiguration를 사용 하도록 설정

에 옵트인, 앱에서는 단지는 PhotoVideoCamera [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration):
```csharp
var display = Windows.Graphics.Holographic.HolographicDisplay.GetDefault();
var view = display.TryGetViewConfiguration(Windows.Graphics.Holographic.HolographicViewConfiguration.PhotoVideoCamera);
if (view != null)
{
   view.IsEnabled = true;
}
```

##### <a name="handle-the-additional-holographiccamera-render-in-directx"></a>DirectX의 추가 HolographicCamera 렌더링 처리

앱이 PV 카메라에서 렌더링을 옵트인 하 고 혼합된 현실 캡처 시작 경우:
1. HolographicSpace의 CameraAdded 이벤트가 발생 합니다. 앱이이 시간에 카메라를 처리할 수 없는 경우이 이벤트를 지연 시킬 수 있습니다.
2. 이벤트 완료 (고 면 미해결 지연이 없을)는 HolographicCamera 다음 HolographicFrame의 AddedCameras 목록에 표시 됩니다.

혼합된 현실 캡처가 중지 됩니다 (또는 앱 혼합된 현실 캡처 실행 되는 동안 보기 구성을 사용 하지 않도록 설정 하는 경우): 다음 HolographicFrame의 RemovedCameras 목록에는 HolographicCamera 나타나고 HolographicSpace의 CameraRemoved 이벤트는 발생 합니다.

A [ViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) 카메라 속한 구성을 식별 하는 데 HolographicCamera 속성이 추가 되었습니다.

##### <a name="handle-the-additional-holographiccamera-render-in-unity"></a>Unity에서 추가 HolographicCamera 렌더링 처리

>[!NOTE]
> Unity PV 카메라에서 렌더링 하는 개발 중 지원과 아직 사용할 수 없습니다. 이 설명서는 PV 카메라에서 렌더링에 대 한 지원 사용 하 여 Unity의 빌드를 사용할 때 업데이트 됩니다.

##### <a name="verify-shaders-and-code-support-additional-cameras"></a>셰이더를 확인 하 고 추가 카메라 지원 코드

혼합된 현실 캡처 및 비정상적인 맞춤, 누락 된 콘텐츠 또는 성능 문제에 대 한 검사를 실행 합니다. 셰이더와 적절 하 게 코드를 업데이트 합니다.

특정 장면을 렌더링 추가 카메라를 지원 하지 않는 경우에 해당 과정 중 PhotoVideoCamera의 HolographicViewConfiguration를 비활성화할 수 있습니다.

### <a name="disabling-mrc-in-your-app"></a>앱에서 사용 하지 않도록 설정 MRC

#### <a name="2d-app"></a>2D 앱

2D 앱에서 혼합된 현실 캡처 중인지 가려질 해당 시각적 콘텐츠를 선택할 수 있습니다.:
* 사용 하 여 표시 합니다 [DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://docs.microsoft.com/windows/desktop/direct3ddxgi/dxgi-present) 플래그
* 사용 하 여 앱의 스왑 체인을 만들 합니다 [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://docs.microsoft.com/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag) 플래그
* Windows 10을 사용 하 여 업데이트할 수 있습니다 2019, ApplicationView의 설정 [IsScreenCaptureEnabled](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled)

#### <a name="immersive-app"></a>몰입 형 앱

몰입 형 앱을 해당 시각적 콘텐츠에서 혼합된 현실 캡처에서 제외 하도록 선택할 수 있습니다.:
* HolographicCameraRenderingParameter의 설정 [IsContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled) 관련된 프레임에 대 한 혼합된 현실 캡처를 사용 하지 않도록 설정
* HolographicCamera의 설정 [IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled) 해당 연결된 holographic 카메라에 대 한 혼합된 현실 캡처를 사용 하지 않도록 설정

#### <a name="password-keyboard"></a>암호 키보드

Windows 10 년 5 월 업데이트 2019, 암호 또는 pin 키보드 표시 되는 경우 혼합된 현실 캡처에서 시각적 콘텐츠가 자동으로 제외 됩니다.

### <a name="knowing-when-mrc-is-active"></a>MRC이 활성화 되 면 파악

합니다 [AppCapture](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.AppCapture) 혼합 현실 캡처 시스템 (오디오 또는 비디오)에 실행 될 때 알아야 하는 앱 클래스를 사용할 수 있습니다.

>[!NOTE]
>AppCapture [GetForCurrentView](https://docs.microsoft.com/uwp/api/windows.media.capture.appcapture.getforcurrentview) null 실제로 캡처를 혼합 하는 경우 장치에서 사용할 수 없는 API를 반환할 수 있습니다. 앱 일시 중단 되 면 CapturingChanged 이벤트 등록을 취소 해야 이기도, MRC 차단 된 상태로 가져올 수는 그렇지 않은 경우.

### <a name="best-practices-hololens-specific"></a>모범 사례 (HoloLens에 한정)

MRC는 개발자가 추가 작업 없이도 작동 해야 하지만 앱의 혼합된 현실 가장 캡처 환경을 제공 하기 위해 알아야 할 몇 가지 있습니다.

**MRC 홀로그램의 알파 채널을 사용 하 여와 혼합 하 여 [카메라](locatable-camera.md) 이미지**

불투명 한 검정색으로 선택을 취소 하는 대신 투명 검정으로 앱 지우기가 있는지 확인 하는 가장 중요 한 단계가입니다. Unity에서 기본적으로 MixedRealityToolkit 이렇게 있지만 변경 하는 한 줄을 확인 해야 아닌 Unity에서 개발 하는 경우.

다음은 일부 아티팩트가 응용 프로그램을 투명 검정으로 선택을 취소 하지는 MRC에서 확인할 수 있습니다.

**예제 오류**: 검정 (투명 한 검정으로 지우려면 장애) 콘텐츠에 대 한 가장자리

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

**예제 오류**: 전체 배경 장면을 홀로그램의 검정색으로 표시 됩니다. 검은색 배경에서 1의 결과 백그라운드 알파 값 설정

![검은색 배경에서 1의 결과 백그라운드 알파 값 설정](images/clearopaqueblack-300px.png)

**예상 결과**: 홀로그램 실제 (투명 한 검정으로 선택을 취소 하는 경우 예상된 결과)를 사용 하 여 제대로 혼합 표시

![투명 한 검정으로 선택을 취소 하는 경우 예상된 결과](images/cleartransparentblack-300px.png)

**해결 방법**:
* 된 알파 값 0 불투명 검은색으로 표시 되는 모든 콘텐츠를 변경 합니다.
* 투명 검정으로 앱 지우기는 있는지 확인 합니다.
* Unity 기본값 ID3D11DeiceContext::ClearRenderTargetView()를 사용 하 여 사용 된 색을 수정 해야 하는 비 Unity 앱 인지 하지만 MixedRealityToolkit를 사용 하 여 자동으로 취소 하려면 선택을 취소 합니다. 불투명 한 검은색 (0,0,0,1) 대신 투명 한 검은색 (0,0,0,0)의 선택을 취소 하면 확인 하려고 합니다.

이제 원하는 경우 일반적으로 필요가 없습니다 자산의 알파 값을 조정할 수 있습니다. 대부분의 경우 MRCs 즉시 좋은 살펴보겠습니다. MRC 미리 곱한 알파를 가정합니다. 알파 값에는 MRC 캡처만 적용 됩니다.

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a>MRC HoloLens에 설정 된 경우 예상 되는 상황

다음에 적용 (항목인 1 세대) HoloLens 및 HoloLens 2 언급이 없는 경우:

* 시스템에는 30 Hz 렌더링 응용 프로그램을 제한 됩니다. 이 앱 상수 예산 예약 유지 필요가 없도록 하려면 MRC 한 일부 여유가 만들고 30fps MRC 비디오 녹화 framerate 일치
* 홀로그램 장치의 오른쪽 눈에 보일 수도 있습니다 "번쩍이기" 기록/스트리밍할 때 MRC: 텍스트를 더 읽기 어렵다고 될 수 있습니다 및 홀로그램 가장자리 더 깨진 나타날 수 있습니다 (타사 카메라에 옵트인에 렌더링할 **HoloLens 2** 방지 이 손상)
* MRC 사진 및 동영상 응용 프로그램의 존중 [지점 집중](focus-point-in-unity.md) 응용 프로그램이 설정한 경우 됩니다 수 있게 도와주는 홀로그램 정확 하 게 배치 됩니다. 비디오에 대 한의 포커스 지점은 위해 다듬어집니다는 홀로그램 포커스 요소 깊이 크게 변경 되 면 제자리에 드리프트 느리게 보일 수 있습니다. 홀로그램 포커스 지점에서 다른 깊이 실제 (아래 예제 참조는 포커스 지점을 2m에서 설정 되지만 홀로그램 1m의 위치가)에서 오프셋 나타날 수 있습니다.

![홀로그램 2m에서 전 세계에 완벽 하 게 등록 표시 됩니다. 홀로그램 닫기 또는 먼 거리에 약간 오프셋 될 수 있습니다.](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a>앱 내에서 MRC 기능 통합

혼합된 현실 앱 MRC 사진 또는 앱 내에서 비디오 캡처를 시작할 수 있습니다 및 저장 되지 않고 캡처된 콘텐츠 앱에 사용할 수는 장치의 "카메라 앨범."를 사용자 지정 MRC 레코더를 만들거나 기본 제공 카메라 캡처 UI 활용할 수 있습니다. 

### <a name="mrc-with-built-in-camera-ui"></a>기본 제공 카메라 UI 사용 하 여 MRC

개발자가 사용할 수는 *[카메라 캡처 UI API](https://docs.microsoft.com/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* 혼합된 현실 사용자 캡처된 사진 또는 비디오 몇 줄의 코드만으로 가져오려고 합니다.

이 API는 기본 제공 MRC 카메라 UI를 올 사용자 사진 또는 비디오를 걸릴 수 있으며 결과 캡처를 앱에 반환를 시작 합니다.  사용자 고유의 카메라 UI를 만들려면 않거나 필요한 하위 수준 캡처 스트림에 대 한 액세스, 사용자 지정 혼합 현실 캡처 레코더를 만들 수 있습니다.

### <a name="creating-a-custom-mrc-recorder"></a>사용자 지정 MRC 레코더 만들기

사용자 사진을 늘 실행 수 또는 시스템을 사용 하 여 비디오 MRC 캡처 서비스, 응용 프로그램 사용자 지정 카메라 앱을 빌드 하지만 홀로그램 MRC 마찬가지로 카메라 스트림에 포함 해야 할 수 있습니다. 이 응용 프로그램을 사용자를 대신 하 여 캡처를 시작, 빌드 사용자 지정 UI를 녹음/녹화 또는 MRC 설정을 몇 가지 예제 이름을 사용자 지정할 수 있습니다.

**HoloStudio는 MRC 효과 사용 하 여 사용자 지정 MRC 카메라 추가**

![HoloStudio는 MRC 효과 사용 하 여 사용자 지정 MRC 카메라 추가](images/cameraiconholostudio-300px.jpg)

Unity 응용 프로그램 나타납니다 [Locatable_camera_in_Unity](locatable-camera-in-unity.md) 홀로그램을 사용 하도록 설정 하려면 속성에 대 한 합니다.

다른 응용 프로그램이이 사용 하 여 수행할 수는 [Windows 미디어 캡처 Api](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaCapture) 카메라를 제어 및 가상 홀로그램 및 응용 프로그램 오디오 스틸 및 비디오에 포함 하도록 MRC 비디오 및 오디오 효과 추가 합니다.

응용 프로그램의 효과 추가 하려면 두 가지 옵션이 있습니다.
* 이전 API: [Windows.Media.Capture.MediaCapture.AddEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addeffectasync)
* 새 Microsoft 권장 API (동적 속성을 조작할 수 있도록 하는 개체를 반환한): [Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) 앱 의자체구현을만들필요는[IVideoEffectDefinition](https://docs.microsoft.com/uwp/api/Windows.Media.Effects.IVideoEffectDefinition) 하 고 [IAudioEffectDefinition](https://docs.microsoft.com/uwp/api/windows.media.effects.iaudioeffectdefinition)합니다. 샘플 사용에 대 한 MRC 효과 샘플을 참조 하세요.

>[!NOTE]
> Windows.Media.MixedRealityCapture 네임 스페이스는 Visual Studio에서 인식 되지 않습니다 하지만 문자열은 여전히 유효 합니다.

MRC 비디오 효과 (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)

|  속성 이름  |  형식  |  Default Value  |  설명 | 
|----------|----------|----------|----------|
|  StreamType  |  UINT32 ([MediaStreamType](https://docs.microsoft.com/uwp/api/Windows.Media.Capture.MediaStreamType))  |  1 (VideoRecord)  |  이 효과에 사용 되는 캡처 스트림을 설명 합니다. 오디오를 사용할 수 없습니다. | 
|  HologramCompositionEnabled  |  boolean  |  TRUE  |  홀로그램 비디오 캡처에서를 사용 하지 않도록 설정 하거나 사용 하는 플래그입니다. | 
|  RecordingIndicatorEnabled  |  boolean  |  TRUE  |  홀로그램 캡처 시 화면에서 기록 표시기를 사용할지를 플래그입니다. | 
|  VideoStabilizationEnabled  |  boolean  |  FALSE  |  HoloLens 추적기에서 제공 하는 비디오 안정화를 사용할지를 플래그입니다. | 
|  VideoStabilizationBufferLength  |  UINT32  |  0  |  설정 비디오 안정화에 대 한 기록 프레임 수가 사용 됩니다. 0 0-대기 시간 및 기능과 성능 측면에서 거의 "무료"입니다. (대기 시간 및 메모리의 15 프레임) 하는 대신 가장 높은 품질에 대 한 15는 사용 하는 것이 좋습니다. | 
|  GlobalOpacityCoefficient  |  FLOAT  |  0.9 (HoloLens) 1.0 (몰입 형 헤드셋)  |  홀로그램 전역 불투명도 계수 범위의 (완전히 투명) 0.0에서 1.0으로 설정 (완전 불투명). | 
|  BlankOnProtectedContent  |  boolean  |  FALSE  |  활성화 하거나 비활성화는 2d UWP 앱 보여 주는 보호 된 콘텐츠가 있는 경우 빈 프레임을 반환 하는 플래그입니다. 이 플래그는 false 및 2d UWP 앱 인지 보여 주는 보호 된 콘텐츠, 혼합된 현실 캡처 모두 헤드셋에 보호 된 콘텐츠 질감 2d UWP 앱 바뀝니다. |
|  ShowHiddenMesh  |  boolean  |  FALSE  |  사용 하도록 설정 하거나 holographic 카메라의 숨겨진된 영역 메시를 표시 하 고 콘텐츠를 인접 하지 않도록 설정 하는 플래그입니다. |
| OutputSize | Size | 0, 0 | 비디오 안정화에 그림이 잘린 후 원하는 출력 크기를 설정 합니다. 0 또는 잘못 된 출력 크기를 지정 하는 경우 기본 자르기 크기가 선택 됩니다. |
| PreferredHologramPerspective | UINT32 | 1 (PhotoVideoCamera) | 구성 하는 holographic 카메라 보기 캡처해야 나타내는 데 사용 하는 열거형입니다. 앱에서 사진/비디오를 렌더링 하 라는 메시지가 표시 되지 않습니다 0 (표시)으로 설정 합니다. |

MRC 오디오 효과 (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)

<table>
<tr>
<th>속성 이름</th>
<th>형식</th>
<th>Default Value</th>
<th>설명</th>
</tr>
<tr>
<td>MixerMode</td>
<td>UINT32</td>
<td>2</td>
<td>
<ul>
<li>0 : Mic 오디오 전용</li>
<li>1 : 시스템 오디오 전용</li>
<li>2 : Mic 및 시스템 오디오</li>
</ul>
</td>
</tr>
</table>

### <a name="simultaneous-mrc-limitations"></a>동시 MRC 제한 사항

MRC 동시에 액세스 하는 여러 앱 주위에 특정 제한이 있습니다.

#### <a name="photovideo-camera-access"></a>사진/비디오 카메라 액세스

사진/비디오 카메라는 동시에 액세스할 수 있는 프로세스 수가 제한 됩니다. 프로세스를 기록 하는 동안 사진을 다른 프로세스를 실행 하거나 비디오 사진/비디오 카메라를 획득 하지 못합니다. (혼합 현실 캡처 및 표준 사진/비디오 캡처를 모두에 적용)

HoloLens 2를 사용 하 여 앱 MediaCaptureInitializationSettings의 따르면 [SharingMode](https://docs.microsoft.com/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode) 사진/비디오 카메라에 대 한 독점적인 제어권 필요할 경우 SharedReadOnly 실행할 것인지를 나타내는 속성을 합니다. 이렇게 확인 및 캡처의 프레임 속도 어떤 다른 앱 구성 있도록 카메라 제한 됩니다.

##### <a name="built-in-mrc-photovideo-camera-access"></a>기본 제공 MRC 사진/비디오 카메라 액세스

Cortana, 시작 메뉴, 하드웨어 바로 가기, Miracast, Windows Device Portal) (통해 Windows 10에 기본 제공 되는 MRC 기능:
* 기본적으로 ExclusiveControl를 사용 하 여 실행 됩니다.

그러나 공유 모드에서 작동 하도록 각 하위 시스템에 지원이 추가 되었습니다.
* 앱 ExclusiveControl 사진/비디오 카메라에 대 한 액세스를 요청 하는 경우 기본 제공 MRC 자동으로 중지 됩니다 사진/비디오 카메라를 사용 하 여 앱의 요청은 성공 하므로
* 기본 제공 MRC SharedReadOnly 모드에서 실행 됩니다 MRC 기본 제공 앱에 ExclusiveControl 동안 시작 된 경우

이 공유 모드 기능에는 특정 제한이 있습니다.
* Cortana, 하드웨어 바로 가기 또는 시작 메뉴를 통해 사진: 필요한 Windows 10 2018 년 4 월 업데이트 (또는 이상)
* Cortana, 하드웨어 바로 가기 또는 시작 메뉴를 통해 비디오: 필요한 Windows 10 2018 년 4 월 업데이트 (또는 이상)
* Miracast 통해 스트리밍 MRC: 필요한 Windows 10 년 10 월 2018 업데이트 (또는 이상)
* Windows Device Portal 통해 또는 HoloLens 도우미 앱을 통해 MRC 스트리밍: HoloLens 2 필요

>[!NOTE]
> 다른 앱에서 사진/비디오 카메라를 사용 하는 경우 기본 값에서 확인 및 기본 제공 MRC 카메라 UI의 프레임 속도 줄어들 수 있습니다.

#### <a name="mrc-access"></a>MRC 액세스

그러나 Windows 10 2018 년 4 월 업데이트를 더 이상 없습니다 (사진/비디오 카메라에 대 한 액세스는 아직 제한) MRC 스트림에 액세스 하는 여러 앱 관련 제한 사항입니다.

Windows 10 2018 년 4 월 이전 MRC 레코더를 사용자 지정 하는 앱의 업데이트 된 시스템 MRC (캡처 사진, 비디오, 캡처링 또는 Windows Device Portal 스트리밍)를 사용 하 여 함께 사용할 수 없습니다.

## <a name="see-also"></a>참조
* [혼합 현실 캡처](mixed-reality-capture.md)
* [Spectator View](spectator-view.md)
