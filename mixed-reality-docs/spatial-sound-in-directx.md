---
title: DirectX의 공간 소리
description: XAudio2 및 xAPO 오디오 라이브러리를 사용 하 여 DirectX를 기반으로 Windows Mixed Reality 앱에 공간 소리를 추가 합니다.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows mixed reality, 공간 사운드, 앱, XAudio2, 낮은 수준, xAPO, 오디오 라이브러리, 연습, DirectX
ms.openlocfilehash: 04d8c43ab400eed4cec5cbd848af5b888cb66e4b
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63550437"
---
# <a name="spatial-sound-in-directx"></a>DirectX의 공간 소리

[XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx) 및 [xapo](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx) 오디오 라이브러리를 사용 하 여 DirectX를 기반으로 Windows Mixed Reality 앱에 공간 소리를 추가 합니다.

이 항목에서는 HolographicHRTFAudioSample의 샘플 코드를 사용 합니다.

>[!NOTE]
>이 문서의 코드 조각은 현재 [ C++ holographic 프로젝트 템플릿에](creating-a-holographic-directx-project.md)사용 되 C++는 것 처럼 C + 17-so-far working 규격 C++/winrt 대신/cx 사용을 보여 줍니다.  개념은 C++/winrt 프로젝트와 동일 하지만 코드를 변환 해야 합니다.

## <a name="overview-of-head-relative-spatial-sound"></a>헤드 상대 공간 소리 개요

공간 사운드는 **HRTF (head 관련 전송 함수** ) 필터를 사용 하 여 일반적인 오디오 스트림을 *SPATIALIZE* 하는 **APO (오디오 처리 개체** )로 구현 됩니다.

다음 헤더 파일을 pch에 포함 하 여 오디오 Api에 액세스 합니다.
* XAudio2
* xapo. h
* hrtfapoapi

공간 소리를 설정 하려면:
1. [Createhrtfapo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) 를 호출 하 여 hrtf 오디오의 새 APO를 초기화 합니다.
2. [Hrtf 매개 변수](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx) 및 [hrtf 환경을](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx) 할당 하 여 공간 사운드 APO의 음향 특성을 정의 합니다.
3. HRTF 처리를 위한 XAudio2 엔진을 설정 합니다.
4. [IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx) 개체를 만들고 [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx)를 호출 합니다.

## <a name="implementing-hrtf-and-spatial-sound-in-your-directx-app"></a>DirectX 앱에서 HRTF 및 공간 소리 구현

다양 한 매개 변수 및 환경에서 HRTF APO를 구성 하 여 다양 한 효과를 달성할 수 있습니다. 다음 코드를 사용 하 여 가능성을 탐색 합니다. 여기에서 유니버설 Windows 플랫폼 코드 샘플을 다운로드 합니다. [공간 음향 샘플](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)

도우미 형식은 다음 파일에서 사용할 수 있습니다.
* [AudioFileReader](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp): 미디어 파운데이션 및 [IMFSourceReader 인터페이스](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx)를 사용 하 여 오디오 파일을 로드 합니다.
* [XAudio2Helpers](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h): **SetupXAudio2** 함수를 구현 하 여 hrtf 처리를 위한 XAudio2를 초기화 합니다.

### <a name="add-spatial-sound-for-an-omnidirectional-source"></a>전방향 원본에 대 한 공간 소리 추가

사용자 환경에서 일부 holograms은 모든 방향에서 동일 하 게 소리를 내보냅니다. 다음 코드에서는 전방향 사운드를 내보내는 APO를 초기화 하는 방법을 보여 줍니다. 이 예에서는 Windows Holographic 앱 템플릿에서 회전 하는 큐브에이 개념을 적용 합니다. 전체 코드 목록은 [OmnidirectionalSound](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp)를 참조 하세요.

**Window의 공간 사운드 엔진은 재생에 대해 48k samplerate 지원 합니다. Unity와 같은 대부분의 미들웨어 프로그램은 사운드 파일을 원하는 형식으로 자동으로 변환 하지만, 오디오 시스템의 하위 수준에서 tinkering를 시작 하거나 고유한 작업을 수행 하는 경우에는 다음과 같이 충돌 또는 원치 않는 동작을 방지 하는 것이 매우 중요 합니다. HRTF 시스템 오류입니다.**

먼저 APO를 초기화 해야 합니다. Holographic 샘플 앱에서는 **HolographicSpace**가 있는 경우이 작업을 수행 하도록 선택 했습니다.

From *HolographicHrtfAudioSampleMain:: SetHolographicSpace ()* :

```
// Spatial sound
auto hr = m_omnidirectionalSound.Initialize(L"assets//MonoSound.wav");
```

*OmnidirectionalSound*에서 Initialize의 구현입니다.

```
// Initializes an APO that emits sound equally in all directions.
HRESULT OmnidirectionalSound::Initialize( LPCWSTR filename )
{
    // _audioFile is of type AudioFileReader, which is defined in AudioFileReader.cpp.
    auto hr = _audioFile.Initialize( filename );

    ComPtr<IXAPO> xapo;
    if ( SUCCEEDED( hr ) )
    {
        // Passing in nullptr as the first arg for HrtfApoInit initializes the APO with defaults of
        // omnidirectional sound with natural distance decay behavior.
        // CreateHrtfApo fails with E_NOTIMPL on unsupported platforms.
        hr = CreateHrtfApo( nullptr, &xapo );
    }

    if ( SUCCEEDED( hr ) )
    {
        // _hrtfParams is of type ComPtr<IXAPOHrtfParameters>.
        hr = xapo.As( &_hrtfParams );
    }

    // Set the default environment.
    if ( SUCCEEDED( hr ) )
    {
        hr = _hrtfParams->SetEnvironment( HrtfEnvironment::Outdoors );
    }

    // Initialize an XAudio2 graph that hosts the HRTF xAPO.
    // The source voice is used to submit audio data and control playback.
    if ( SUCCEEDED( hr ) )
    {
        hr = SetupXAudio2( _audioFile.GetFormat(), xapo.Get(), &_xaudio2, &_sourceVoice );
    }

    // Submit audio data to the source voice.
    if ( SUCCEEDED( hr ) )
    {
        XAUDIO2_BUFFER buffer{ };
        buffer.AudioBytes = static_cast<UINT32>( _audioFile.GetSize() );
        buffer.pAudioData = _audioFile.GetData();
        buffer.LoopCount = XAUDIO2_LOOP_INFINITE;

        // _sourceVoice is of type IXAudio2SourceVoice*.
        hr = _sourceVoice->SubmitSourceBuffer( &buffer );
    }

    return hr;
}
```

HRTF에 대해 APO를 구성한 후에는 원본 음성에서 [시작](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) 을 호출 하 여 오디오를 재생 합니다. 이 샘플 앱에서는 큐브에서 발생 하는 소리를 계속 사용할 수 있도록 루프에 배치 하도록 선택 했습니다.

From *HolographicHrtfAudioSampleMain:: SetHolographicSpace ()* :

```
if (SUCCEEDED(hr))
{
    m_omnidirectionalSound.SetEnvironment(HrtfEnvironment::Small);
    m_omnidirectionalSound.OnUpdate(m_spinningCubeRenderer->GetPosition());
    m_omnidirectionalSound.Start();
}
```

*OmnidirectionalSound*에서:

```
HRESULT OmnidirectionalSound::Start()
{
    _lastTick = GetTickCount64();
    return _sourceVoice->Start();
}
```

이제 프레임을 업데이트할 때마다 장치 자체를 기준으로 홀로그램의 위치를 업데이트 해야 합니다. 이는 HRTF 위치가 항상 헤드 위치 및 방향을 포함 하 여 사용자의 헤드를 기준으로 표현 되기 때문입니다.

HolographicSpace에서이 작업을 수행 하려면 SpatialStationaryFrameOfReference 좌표계에서 장치 자체에 고정 된 좌표계로 변환 매트릭스를 구성 해야 합니다.

From *HolographicHrtfAudioSampleMain:: Update ()* :

```
m_spinningCubeRenderer->Update(m_timer);

SpatialPointerPose^ currentPose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
if (currentPose != nullptr)
{
    // Use a coordinate system built from a pointer pose.
    SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
    if (pose != nullptr)
    {
        float3 headPosition = pose->Head->Position;
        float3 headUp = pose->Head->UpDirection;
        float3 headDirection = pose->Head->ForwardDirection;

        // To construct a rotation matrix, we need three vectors that are mutually orthogonal.
        // The first vector is the gaze vector.
        float3 negativeZAxis = normalize(headDirection);

        // The second vector should end up pointing away from the horizontal plane of the device.
        // We first guess by using the head "up" direction.
        float3 positiveYAxisGuess = normalize(headUp);

        // The third vector completes the set by being orthogonal to the other two.
        float3 positiveXAxis = normalize(cross(negativeZAxis, positiveYAxisGuess));

        // Now, we can correct our "up" vector guess by redetermining orthogonality.
        float3 positiveYAxis = normalize(cross(negativeZAxis, positiveXAxis));

        // The rotation matrix is formed as a standard basis rotation.
        float4x4 rotationTransform =
            {
            positiveXAxis.x, positiveYAxis.x, negativeZAxis.x, 0.f,
            positiveXAxis.y, positiveYAxis.y, negativeZAxis.y, 0.f,
            positiveXAxis.z, positiveYAxis.z, negativeZAxis.z, 0.f,
            0.f, 0.f, 0.f, 1.f,
            };

        // The translate transform can be constructed using the Windows::Foundation::Numerics API.
        float4x4 translationTransform = make_float4x4_translation(-headPosition);

        // Now, we have a basis transform from our spatial coordinate system to a device-relative
        // coordinate system.
        float4x4 coordinateSystemTransform = translationTransform * rotationTransform;

        // Reinterpret the cube position in the device's coordinate system.
        float3 cubeRelativeToHead = transform(m_spinningCubeRenderer->GetPosition(), coordinateSystemTransform);

        // Note that at (0, 0, 0) exactly, the HRTF audio will simply pass through audio. We can use a minimal offset
        // to simulate a zero distance when the hologram position vector is exactly at the device origin in order to
        // allow HRTF to continue functioning in this edge case.
        float distanceFromHologramToHead = length(cubeRelativeToHead);
        static const float distanceMin = 0.00001f;
        if (distanceFromHologramToHead < distanceMin)
        {
            cubeRelativeToHead = float3(0.f, distanceMin, 0.f);
        }

        // Position the spatial sound source on the hologram.
        m_omnidirectionalSound.OnUpdate(cubeRelativeToHead);

        // For debugging, it can be interesting to observe the distance in the debugger.
        /*
        std::wstring distanceString = L"Distance from hologram to head: ";
        distanceString += std::to_wstring(distanceFromHologramToHead);
        distanceString += L"\n";
        OutputDebugStringW(distanceString.c_str());
        */
    }
}
```

HRTF 위치는 OmnidirectionalSound helper 클래스에 의해 소리 APO에 직접 적용 됩니다.

From *OmnidirectionalSound:: OnUpdate*:

```
HRESULT OmnidirectionalSound::OnUpdate(_In_ Numerics::float3 position)
{
    auto hrtfPosition = HrtfPosition{ position.x, position.y, position.z };
    return _hrtfParams->SetSourcePosition(&hrtfPosition);
}
```

정말 간단하죠. HRTF 오디오 및 Windows Holographic으로 수행할 수 있는 작업에 대해 자세히 알아보려면 계속 읽습니다.

### <a name="initialize-spatial-sound-for-a-directional-source"></a>방향성 소스에 대 한 공간 음향 초기화

사용자 환경에서의 일부 holograms는 대부분 한 방향으로 소리를 내보냅니다. 이 사운드 패턴은 만화 하트 처럼 보이지만 *cardioid* 라고 합니다. 다음 코드에서는 경우에는 APO를 초기화 하 여 방향성 소리를 내보내는 방법을 보여 줍니다. 전체 코드 목록은 [CardioidSound](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp) 를 참조 하세요.

HRTF에 대해 APO를 구성한 후에는 원본 음성에서 [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) 를 호출 하 여 오디오를 재생 합니다.

```
// Initializes an APO that emits directional sound.
HRESULT CardioidSound::Initialize( LPCWSTR filename )
{
    // _audioFile is of type AudioFileReader, which is defined in AudioFileReader.cpp.
    auto hr = _audioFile.Initialize( filename );
    if ( SUCCEEDED( hr ) )
    {
        // Initialize with "Scaling" fully directional and "Order" with broad radiation pattern.
        // As the order goes higher, the cardioid directivity region becomes narrower.
        // Any direct path signal outside of the directivity region will be attenuated based on the scaling factor.
        // For example, if scaling is set to 1 (fully directional) the direct path signal outside of the directivity
        // region will be fully attenuated and only the reflections from the environment will be audible.
        hr = ConfigureApo( 1.0f, 4.0f );
    }
    return hr;
}

HRESULT CardioidSound::ConfigureApo( float scaling, float order )
{
    // Cardioid directivity configuration:
    // Directivity is specified at xAPO instance initialization and can't be changed per frame.
    // To change directivity, stop audio processing and reinitialize another APO instance with the new directivity.
    HrtfDirectivityCardioid cardioid;
    cardioid.directivity.type = HrtfDirectivityType::Cardioid;
    cardioid.directivity.scaling = scaling;
    cardioid.order = order;

    // APO intialization
    HrtfApoInit apoInit;
    apoInit.directivity = &cardioid.directivity;
    apoInit.distanceDecay = nullptr; // nullptr specifies natural distance decay behavior (simulates real world)

    // CreateHrtfApo fails with E_NOTIMPL on unsupported platforms.
    ComPtr<IXAPO> xapo;
    auto hr = CreateHrtfApo( &apoInit, &xapo );

    if ( SUCCEEDED( hr ) )
    {
        hr = xapo.As( &_hrtfParams );
    }

    // Set the initial environment.
    // Environment settings configure the "distance cues" used to compute the early and late reverberations.
    if ( SUCCEEDED( hr ) )
    {
        hr = _hrtfParams->SetEnvironment( _HrtfEnvironment::Outdoors );
    }

    // Initialize an XAudio2 graph that hosts the HRTF xAPO.
    // The source voice is used to submit audio data and control playback.
    if ( SUCCEEDED( hr ) )
    {
        hr = SetupXAudio2( _audioFile.GetFormat(), xapo.Get(), &_xaudio2, &_sourceVoice );
    }

    // Submit audio data to the source voice
    if ( SUCCEEDED( hr ) )
    {
        XAUDIO2_BUFFER buffer{ };
        buffer.AudioBytes = static_cast<UINT32>( _audioFile.GetSize() );
        buffer.pAudioData = _audioFile.GetData();
        buffer.LoopCount = XAUDIO2_LOOP_INFINITE;
        hr = _sourceVoice->SubmitSourceBuffer( &buffer );
    }

    return hr;
}
```

### <a name="implement-custom-decay"></a>사용자 지정 감소 구현

거리 및/또는 완전히 잘라내는 거리에 따라 공간 사운드가 꺼진 비율을 재정의할 수 있습니다. 공간 소리에서 사용자 지정 감소 동작을 구현 하려면 [HrtfDistanceDecay 구조체](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx) 를 채운 후 [Createhrtfapo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) 함수에 전달 하기 전에 [HrtfApoInit 구조체](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx) 의 **distanceDecay** 필드에 할당 합니다.

이전에 표시 된 **Initialize** 메서드에 다음 코드를 추가 하 여 사용자 지정 감소 동작을 지정 합니다. 전체 코드 목록은 [customdecay .cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp)를 참조 하세요.

```
HRESULT CustomDecaySound::Initialize( LPCWSTR filename )
{
    auto hr = _audioFile.Initialize( filename );

    ComPtr<IXAPO> xapo;
    if ( SUCCEEDED( hr ) )
    {
        HrtfDistanceDecay customDecay;
        customDecay.type = HrtfDistanceDecayType::CustomDecay;               // Custom decay behavior, we'll pass in the gain value on every frame.
        customDecay.maxGain = 0;                                             // 0dB max gain
        customDecay.minGain = -96.0f;                                        // -96dB min gain
        customDecay.unityGainDistance = HRTF_DEFAULT_UNITY_GAIN_DISTANCE;    // Default unity gain distance
        customDecay.cutoffDistance = HRTF_DEFAULT_CUTOFF_DISTANCE;           // Default cutoff distance

        // Setting the directivity to nullptr specifies omnidirectional sound.
        HrtfApoInit init;
        init.directivity = nullptr;
        init.distanceDecay = &customDecay;

        // CreateHrtfApo will fail with E_NOTIMPL on unsupported platforms.
        hr = CreateHrtfApo( &init, &xapo );
    }
...
}
```
