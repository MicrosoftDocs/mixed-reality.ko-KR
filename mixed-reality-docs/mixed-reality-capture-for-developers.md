---
title: 개발자를 위한 실제로 캡처 혼합
description: 개발자를 위한 혼합된 현실에 대 한 모범 사례를 캡처합니다.
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: mrc, 사진, 비디오, 캡처, 카메라
ms.openlocfilehash: c2d98baf16b2ea724247224aabadc1e2ca533ec1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599455"
---
# <a name="mixed-reality-capture-for-developers"></a>개발자를 위한 실제로 캡처 혼합

> [!NOTE]
> HoloLens 2 관련 된 자세한 지침 [예정](index.md#news-and-notes)합니다. 

참조 [앱에서 사용 하도록 설정 하면 MRC](#enabling-mrc-in-your-app) 아래 HoloLens 2에 대 한 새로운 MRC 기능에 대 한 지침에 대 한 합니다.

사용자가 수행할 수 있으므로 [혼합 현실 캡처](mixed-reality-capture.md) (MRC) 사진 또는 언제 든 지 비디오를 응용 프로그램을 개발할 때는 염두 해야 할 몇 가지 사항입니다. 여기에 MRC 시각적 품질 및 MRCs 캡처되는 동안 시스템 변경 내용에 응답 속도 대 한 모범 사례입니다.

개발자 혼합된 현실 캡처 및 삽입 하 여 앱에도 원활 하 게 통합할 수 있습니다.

HoloLens (항목인 1 세대)에 MRC에는 HoloLens 2는 MRC 4k 해상도로 등록 최대 1080p 및 사진과 비디오를 지원 하지만 최대 720p, 사진 및 비디오를 지원 합니다.

## <a name="the-importance-of-quality-mrc"></a>MRC 품질의 중요성

혼합된 현실 사진 캡처되고 비디오는 앱의 사용자에 게는 처음 접하는 가능성이 높습니다. 혼합된 현실 스크린 샷을 Microsoft Store 페이지 또는 MRCs 소셜 네트워크에서 공유 하는 다른 사용자로 여부입니다. MRC 데모 앱, 사용자 교육, 사용자가 해당 혼합된 환경 상호 작용을 공유 하도록 권장 하는 데 사용할 수 및 사용자 설문 조사 및 문제 해결에 대 한 합니다.

## <a name="how-mrc-impacts-your-app"></a>MRC 앱에 미치는 영향을

### <a name="enabling-mrc-in-your-app"></a>앱에서 사용 하도록 설정 하면 MRC

기본적으로 앱 사용자가 혼합된 현실 캡처를 수행할 수 있도록 모든 작업을 수행할 필요가 없습니다. 그러나 사진/비디오 (PV) 카메라와 표시 사이의 간격 증가 하는 HoloLens 2의 디자인을 하기 때문에 우리 도입할의 PV 카메라에 정렬 하는 타사 카메라 렌더링을 생성 하는 새로운 옵션이 **HoloLens 2**합니다. 

타사 카메라에 옵트인 렌더링 HoloLens 2 제품에서 다음과 같이 향상 된 기본 MRC 환경을 통해:
* 물리적 환경 및이 손 (거의 상호 작용) 모두에 맞춤 홀로그램 해야 정확한 전혀 거리를 거리에서 오프셋을 이외의 대신 합니다 [지점 집중](focus-point-in-unity.md) MRC 기본값에서 볼 수 있습니다.
* 헤드셋에서 오른쪽 눈 손상 되지, MRC 출력 홀로그램 렌더링에 사용 되지 않습니다.

### <a name="disabling-mrc-in-your-app"></a>앱에서 사용 하지 않도록 설정 MRC

2D 앱을 사용 하는 경우 [DXGI_PRESENT_RESTRICT_TO_OUTPUT](https://msdn.microsoft.com/library/windows/desktop/bb509554(v=vs.85).aspx) 하거나 [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](https://msdn.microsoft.com/library/windows/desktop/bb173076(v=vs.85).aspx) 됩니다 앱의 시각적 콘텐츠를 올바르게 구성 된 스왑 체인을 사용 하 여 보호 된 콘텐츠를 표시 하려면 혼합된 현실 캡처 실행 되는 동안에 자동으로 가려집니다.

### <a name="knowing-when-mrc-is-active"></a>MRC이 활성화 되 면 파악

합니다 [AppCapture](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.appcapture.aspx) 혼합 현실 캡처 시스템 (오디오 또는 비디오)에 실행 될 때 알아야 하는 앱 클래스를 사용할 수 있습니다.

>[!NOTE]
>AppCapture [GetForCurrentView](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.appcapture.getforcurrentview.aspx) null 실제로 캡처를 혼합 하는 경우 장치에서 사용할 수 없는 API를 반환할 수 있습니다. 앱 일시 중단 되 면 CapturingChanged 이벤트 등록을 취소 해야 이기도, MRC 차단 된 상태로 가져올 수는 그렇지 않은 경우.

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

다른 응용 프로그램이이 사용 하 여 수행할 수는 [Windows 미디어 캡처 Api](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.aspx) 카메라를 제어 및 가상 홀로그램 및 응용 프로그램 오디오 스틸 및 비디오에 포함 하도록 MRC 비디오 및 오디오 효과 추가 합니다.

응용 프로그램의 효과 추가 하려면 두 가지 옵션이 있습니다.
* 이전 API: [Windows.Media.Capture.MediaCapture.AddEffectAsync()](https://msdn.microsoft.com/library/windows/apps/br211961.aspx)
* 새 Microsoft 권장 API (동적 속성을 조작할 수 있도록 하는 개체를 반환한): [Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.addvideoeffectasync.aspx) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediacapture.addaudioeffectasync.aspx) 앱 의자체구현을만들필요는[IVideoEffectDefinition](https://msdn.microsoft.com/library/windows/apps/windows.media.effects.ivideoeffectdefinition.aspx) 하 고 [IAudioEffectDefinition](https://msdn.microsoft.com/library/windows/apps/windows.media.effects.iaudioeffectdefinition.aspx)합니다. 샘플 사용에 대 한 MRC 효과 샘플을 참조 하세요.

(Visual Studio에서 이러한 네임 스페이스를 인식 되지 것입니다 하지만 문자열을 여전히 유효한 지는 note)

MRC 비디오 효과 (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)

|  속성 이름  |  형식  |  기본값  |  설명 | 
|----------|----------|----------|----------|
|  StreamType  |  UINT32 ([MediaStreamType](https://msdn.microsoft.com/library/windows/apps/windows.media.capture.mediastreamtype.aspx))  |  1 (VideoRecord)  |  이 효과에 사용 되는 캡처 스트림을 설명 합니다. 오디오를 사용할 수 없습니다. | 
|  HologramCompositionEnabled  |  boolean  |  TRUE  |  홀로그램 비디오 캡처에서를 사용 하지 않도록 설정 하거나 사용 하는 플래그입니다. | 
|  RecordingIndicatorEnabled  |  boolean  |  TRUE  |  홀로그램 캡처 시 화면에서 기록 표시기를 사용할지를 플래그입니다. | 
|  VideoStabilizationEnabled  |  boolean  |  FALSE  |  HoloLens 추적기에서 제공 하는 비디오 안정화를 사용할지를 플래그입니다. | 
|  VideoStabilizationBufferLength  |  UINT32  |  0  |  설정 비디오 안정화에 대 한 기록 프레임 수가 사용 됩니다. 0 0-대기 시간 및 기능과 성능 측면에서 거의 "무료"입니다. (대기 시간 및 메모리의 15 프레임) 하는 대신 가장 높은 품질에 대 한 15는 사용 하는 것이 좋습니다. | 
|  GlobalOpacityCoefficient  |  FLOAT  |  0.9 (HoloLens) 1.0 (몰입 형 헤드셋)  |  홀로그램 전역 불투명도 계수 범위의 (완전히 투명) 0.0에서 1.0으로 설정 (완전 불투명). | 
|  BlankOnProtectedContent  |  boolean  |  FALSE  |  활성화 하거나 비활성화는 2d UWP 앱 보여 주는 보호 된 콘텐츠가 있는 경우 빈 프레임을 반환 하는 플래그입니다. 이 플래그는 false 및 2d UWP 앱 인지 보여 주는 보호 된 콘텐츠, 혼합된 현실 캡처 모두 헤드셋에 보호 된 콘텐츠 질감 2d UWP 앱 바뀝니다. |
|  ShowHiddenMesh  |  boolean  |  FALSE  |  사용 하도록 설정 하거나 holographic 카메라의 숨겨진된 영역 메시를 표시 하 고 콘텐츠를 인접 하지 않도록 설정 하는 플래그입니다. |

MRC 오디오 효과 (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)

<table>
<tr>
<th>속성 이름</th>
<th>형식</th>
<th>기본값</th>
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

Windows 10 2018 년 4 월 업데이트를이 제한이 적용 되지 않습니다 경우 기본 제공 MRC 카메라 UI 사진/비디오 카메라를 사용 하 여 앱을 시작한 후 사진 또는 비디오를 만드는 데 사용 됩니다. 이 경우 기본 값에서 확인 및 기본 제공 MRC 카메라 UI의 프레임 속도 줄어들 수 있습니다.

Windows 10 년 10 월 2018 Update이이 제한이 적용 되지 않습니다 MRC Miracast 통한 스트리밍.

#### <a name="mrc-access"></a>MRC 액세스

그러나 Windows 10 2018 년 4 월 업데이트를 더 이상 없습니다 (사진/비디오 카메라에 대 한 액세스는 아직 제한) MRC 스트림에 액세스 하는 여러 앱 관련 제한 사항입니다.

Windows 10 2018 년 4 월 이전 MRC 레코더를 사용자 지정 하는 앱의 업데이트 된 시스템 MRC (캡처 사진, 비디오, 캡처링 또는 Windows Device Portal 스트리밍)를 사용 하 여 함께 사용할 수 없습니다.

## <a name="see-also"></a>참조
* [혼합된 현실 캡처](mixed-reality-capture.md)
* [Spectator 보기](spectator-view.md)
