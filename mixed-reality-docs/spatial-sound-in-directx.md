---
title: DirectX의 공간 소리
description: 공간 소리 XAudio2 및 xAPO 오디오 라이브러리를 사용 하 여 DirectX 기반 Windows Mixed Reality 앱에 추가 합니다.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows 혼합 현실, 공간 소리, 앱, 낮은 수준의 XAudio2 xAPO, 오디오 라이브러리, DirectX, 연습
ms.openlocfilehash: 04d8c43ab400eed4cec5cbd848af5b888cb66e4b
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605142"
---
# <a name="spatial-sound-in-directx"></a><span data-ttu-id="0d41b-104">DirectX의 공간 소리</span><span class="sxs-lookup"><span data-stu-id="0d41b-104">Spatial sound in DirectX</span></span>

<span data-ttu-id="0d41b-105">공간 소리를 사용 하 여 DirectX 기반 Windows Mixed Reality 앱에 추가 합니다 [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx) 하 고 [xAPO](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx) 오디오 라이브러리입니다.</span><span class="sxs-lookup"><span data-stu-id="0d41b-105">Add spatial sound to your Windows Mixed Reality apps based on DirectX by using the [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx) and [xAPO](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx) audio libraries.</span></span>

<span data-ttu-id="0d41b-106">이 항목의 HolographicHRTFAudioSample에서 샘플 코드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0d41b-106">This topic uses sample code from the HolographicHRTFAudioSample.</span></span>

>[!NOTE]
><span data-ttu-id="0d41b-107">이 문서의 코드 조각 사용에 현재 방법을 보여 줍니다 C++/CX 대신 C + + 17 규격 C++/WinRT에 사용 되는 [ C++ holographic 프로젝트 템플릿을](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="0d41b-107">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="0d41b-108">개념에 대 한 동일는 C++코드를 변환 해야 하지만 /WinRT 프로젝트입니다.</span><span class="sxs-lookup"><span data-stu-id="0d41b-108">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="overview-of-head-relative-spatial-sound"></a><span data-ttu-id="0d41b-109">헤드 상대 공간 소리를 개요</span><span class="sxs-lookup"><span data-stu-id="0d41b-109">Overview of Head Relative Spatial Sound</span></span>

<span data-ttu-id="0d41b-110">소리 공간으로 구현 됩니다는 **오디오 처리 개체 (APO)** 를 사용 하는 **헤드 전송 함수 (HRTF)와 관련 된** 필터 *spatialize* 일반 오디오 스트림.</span><span class="sxs-lookup"><span data-stu-id="0d41b-110">Spatial sound is implemented as an **audio processing object (APO)** that uses a **head related transfer function (HRTF)** filter to *spatialize* an ordinary audio stream.</span></span>

<span data-ttu-id="0d41b-111">오디오 Api에 액세스 하는 pch.h에 이들 헤더 파일 포함:</span><span class="sxs-lookup"><span data-stu-id="0d41b-111">Include these header files in pch.h to access the audio APIs:</span></span>
* <span data-ttu-id="0d41b-112">XAudio2.h</span><span class="sxs-lookup"><span data-stu-id="0d41b-112">XAudio2.h</span></span>
* <span data-ttu-id="0d41b-113">xapo.h</span><span class="sxs-lookup"><span data-stu-id="0d41b-113">xapo.h</span></span>
* <span data-ttu-id="0d41b-114">hrtfapoapi.h</span><span class="sxs-lookup"><span data-stu-id="0d41b-114">hrtfapoapi.h</span></span>

<span data-ttu-id="0d41b-115">공간 소리를 설정 하려면:</span><span class="sxs-lookup"><span data-stu-id="0d41b-115">To set up spatial sound:</span></span>
1. <span data-ttu-id="0d41b-116">호출 [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) HRTF 오디오에 대 한 새 APO를 초기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d41b-116">Call [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) to initialize a new APO for HRTF audio.</span></span>
2. <span data-ttu-id="0d41b-117">할당 합니다 [HRTF 매개 변수](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx) 및 [HRTF 환경](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx) 공간 사운드 APO의 음향 특성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d41b-117">Assign the [HRTF parameters](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx) and [HRTF environment](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx) to define the acoustic characteristics of the spatial sound APO.</span></span>
3. <span data-ttu-id="0d41b-118">HRTF 처리를 위해 XAudio2 엔진을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d41b-118">Set up the XAudio2 engine for HRTF processing.</span></span>
4. <span data-ttu-id="0d41b-119">만들기는 [IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx) 개체와 호출 [시작](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx)합니다.</span><span class="sxs-lookup"><span data-stu-id="0d41b-119">Create an [IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx) object and call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx).</span></span>

## <a name="implementing-hrtf-and-spatial-sound-in-your-directx-app"></a><span data-ttu-id="0d41b-120">DirectX 앱에서 HRTF 및 공간 소리 구현</span><span class="sxs-lookup"><span data-stu-id="0d41b-120">Implementing HRTF and spatial sound in your DirectX app</span></span>

<span data-ttu-id="0d41b-121">다른 매개 변수 및 환경 HRTF APO를 구성 하 여 다양 한 효과 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d41b-121">You can achieve a variety of effects by configuring the HRTF APO with different parameters and environments.</span></span> <span data-ttu-id="0d41b-122">다음 코드를 사용 하 여 가능성을 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d41b-122">Use the following code to explore the possibilities.</span></span> <span data-ttu-id="0d41b-123">여기에서 유니버설 Windows 플랫폼 코드 샘플을 다운로드 합니다. [소리 공간 예제](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)</span><span class="sxs-lookup"><span data-stu-id="0d41b-123">Download the Universal Windows Platform code sample from here: [Spatial sound sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)</span></span>

<span data-ttu-id="0d41b-124">도우미 형식은 이러한 파일에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d41b-124">Helper types are available in these files:</span></span>
* <span data-ttu-id="0d41b-125">[AudioFileReader.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp): Media Foundation을 사용 하 여 오디오 파일을 로드 하며 [IMFSourceReader 인터페이스](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx)합니다.</span><span class="sxs-lookup"><span data-stu-id="0d41b-125">[AudioFileReader.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp): Loads audio files by using Media Foundation and the [IMFSourceReader interface](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx).</span></span>
* <span data-ttu-id="0d41b-126">[XAudio2Helpers.h](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h): 구현 된 **SetupXAudio2** XAudio2 HRTF 처리를 위해 초기화 하는 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="0d41b-126">[XAudio2Helpers.h](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h): Implements the **SetupXAudio2** function to initialize XAudio2 for HRTF processing.</span></span>

### <a name="add-spatial-sound-for-an-omnidirectional-source"></a><span data-ttu-id="0d41b-127">전방향 원본의 공간 소리를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d41b-127">Add spatial sound for an omnidirectional source</span></span>

<span data-ttu-id="0d41b-128">사용자의 환경에서 일부 홀로그램 모든 방향에서 균등 하 게 소리를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="0d41b-128">Some holograms in the user's surroundings emit sound equally in all directions.</span></span> <span data-ttu-id="0d41b-129">다음 코드는 APO 내보낼 전방향 소리를 초기화 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0d41b-129">The following code shows how to initialize an APO to emit omnidirectional sound.</span></span> <span data-ttu-id="0d41b-130">이 예제에서는 적용이 개념 회전 큐브를 Windows Holographic 앱 템플릿에서 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d41b-130">In this example, we apply this concept to the spinning cube from the Windows Holographic app template.</span></span> <span data-ttu-id="0d41b-131">전체 코드 목록을 보려면 [OmnidirectionalSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp)합니다.</span><span class="sxs-lookup"><span data-stu-id="0d41b-131">For the complete code listing, see [OmnidirectionalSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp).</span></span>

<span data-ttu-id="0d41b-132">**창의 공간 사운드 엔진 48 k samplerate 재생만 지원합니다. 오디오 시스템 또는 사용자 고유의 만드는 더 낮은 수준에서 이리저리를 시작 하는 경우이 충돌 또는 같은 원치 않는 동작을 방지 하기 위해 매우 중요 하지만 Unity와 같은 대부분의 미들웨어 프로그램을 원하는 형식으로 사운드 파일을 자동으로 변환 HRTF 시스템 오류가 발생 했습니다.**</span><span class="sxs-lookup"><span data-stu-id="0d41b-132">**Window's spatial sound engine only supports 48k samplerate for playback. Most middleware programs, like Unity, will automatically convert sound files into the desired format, but if you start tinkering at lower levels in the audio system or making your own, this is very important to remember to prevent crashes or undesired behaviour like HRTF system failure.**</span></span>

<span data-ttu-id="0d41b-133">먼저는 APO 초기화 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d41b-133">First, we need to initialize the APO.</span></span> <span data-ttu-id="0d41b-134">Holographic 샘플 앱에서 되 면이 작업을 수행 하기로 합니다 **HolographicSpace**합니다.</span><span class="sxs-lookup"><span data-stu-id="0d41b-134">In our holographic sample app, we choose to do this once we have the **HolographicSpace**.</span></span>

<span data-ttu-id="0d41b-135">From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span><span class="sxs-lookup"><span data-stu-id="0d41b-135">From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span></span>

```
// Spatial sound
auto hr = m_omnidirectionalSound.Initialize(L"assets//MonoSound.wav");
```

<span data-ttu-id="0d41b-136">초기화의 구현에서 *OmnidirectionalSound.cpp*:</span><span class="sxs-lookup"><span data-stu-id="0d41b-136">The implementation of Initialize, from *OmnidirectionalSound.cpp*:</span></span>

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

<span data-ttu-id="0d41b-137">호출 하는 APO HRTF에 대 한 구성 되 면 [시작](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) 원본 음성 오디오를 재생 하는 데에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d41b-137">After the APO is configured for HRTF, you call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) on the source voice to play the audio.</span></span> <span data-ttu-id="0d41b-138">샘플 앱에서 큐브에서 제공 사운드를 계속할 수 있도록 루프에서 배치를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d41b-138">In our sample app, we choose to put it on a loop so that you can continue to hear the sound coming from the cube.</span></span>

<span data-ttu-id="0d41b-139">From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span><span class="sxs-lookup"><span data-stu-id="0d41b-139">From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span></span>

```
if (SUCCEEDED(hr))
{
    m_omnidirectionalSound.SetEnvironment(HrtfEnvironment::Small);
    m_omnidirectionalSound.OnUpdate(m_spinningCubeRenderer->GetPosition());
    m_omnidirectionalSound.Start();
}
```

<span data-ttu-id="0d41b-140">From *OmnidirectionalSound.cpp*:</span><span class="sxs-lookup"><span data-stu-id="0d41b-140">From *OmnidirectionalSound.cpp*:</span></span>

```
HRESULT OmnidirectionalSound::Start()
{
    _lastTick = GetTickCount64();
    return _sourceVoice->Start();
}
```

<span data-ttu-id="0d41b-141">이제, 프레임, 업데이트 될 때마다 장치 자체를 기준으로 홀로그램의 위치를 업데이트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d41b-141">Now, whenever we update the frame, we need to update the hologram's position relative to the device itself.</span></span> <span data-ttu-id="0d41b-142">즉, HRTF 위치는 항상 헤드 위치와 방향을 포함 하 여 사용자의 head 기준으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d41b-142">This is because HRTF positions are always expressed relative to the user's head, including the head position and orientation.</span></span>

<span data-ttu-id="0d41b-143">HolographicSpace에서 이렇게 하려면 장치 자체를 수정 하는 좌표계에 SpatialStationaryFrameOfReference 좌표 시스템에서 변환 행렬을 생성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d41b-143">To do this in a HolographicSpace, we need to construct a transform matrix from our SpatialStationaryFrameOfReference coordinate system to a coordinate system that is fixed to the device itself.</span></span>

<span data-ttu-id="0d41b-144">From *HolographicHrtfAudioSampleMain::Update()*:</span><span class="sxs-lookup"><span data-stu-id="0d41b-144">From *HolographicHrtfAudioSampleMain::Update()*:</span></span>

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

<span data-ttu-id="0d41b-145">HRTF 위치 OmnidirectionalSound 도우미 클래스로 사운드 APO에 직접 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d41b-145">The HRTF position is applied directly to the sound APO by the OmnidirectionalSound helper class.</span></span>

<span data-ttu-id="0d41b-146">*OmnidirectionalSound::OnUpdate*:</span><span class="sxs-lookup"><span data-stu-id="0d41b-146">From *OmnidirectionalSound::OnUpdate*:</span></span>

```
HRESULT OmnidirectionalSound::OnUpdate(_In_ Numerics::float3 position)
{
    auto hrtfPosition = HrtfPosition{ position.x, position.y, position.z };
    return _hrtfParams->SetSourcePosition(&hrtfPosition);
}
```

<span data-ttu-id="0d41b-147">정말 간단하죠.</span><span class="sxs-lookup"><span data-stu-id="0d41b-147">That's it!</span></span> <span data-ttu-id="0d41b-148">HRTF 오디오 및 Windows Holographic를 사용 하 여 수행할 수 있는 작업에 대 한 자세한 정보를 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d41b-148">Continue reading to learn more about what you can do with HRTF audio and Windows Holographic.</span></span>

### <a name="initialize-spatial-sound-for-a-directional-source"></a><span data-ttu-id="0d41b-149">방향 원본에 대 한 공간 소리를 초기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d41b-149">Initialize spatial sound for a directional source</span></span>

<span data-ttu-id="0d41b-150">사용자의 환경에서 일부 홀로그램 한 방향의 대부분 소리를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="0d41b-150">Some holograms in the user's surroundings emit sound mostly in one direction.</span></span> <span data-ttu-id="0d41b-151">이 사운드 패턴 이라고 *cardioid* 만화 핵심 비슷하기 때문에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d41b-151">This sound pattern is named *cardioid* because it looks like a cartoon heart.</span></span> <span data-ttu-id="0d41b-152">다음 코드는 사운드를 내보내는 방향은 APO를 초기화 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0d41b-152">The following code shows how to initialize an APO to emit directional sound.</span></span> <span data-ttu-id="0d41b-153">전체 코드 목록을 보려면 [CardioidSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp) 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d41b-153">For the complete code listing, see [CardioidSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp) .</span></span>

<span data-ttu-id="0d41b-154">APO HRTF로 구성 된 후 호출 [시작](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) 원본 음성 오디오를 재생 하는 데에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d41b-154">After the APO is configured for HRTF, call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) on the source voice to play the audio.</span></span>

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

### <a name="implement-custom-decay"></a><span data-ttu-id="0d41b-155">사용자 지정 decay 구현</span><span class="sxs-lookup"><span data-stu-id="0d41b-155">Implement custom decay</span></span>

<span data-ttu-id="0d41b-156">거리를 사용 하 여 공간 소리 떨어지면 및/또는 어떤 거리에서이 통해 완전히 속도 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d41b-156">You can override the rate at which a spatial sound falls off with distance and/or at what distance it cuts off completely.</span></span> <span data-ttu-id="0d41b-157">채울 공간 소리에 사용자 지정 decay 동작을 구현 하는 [HrtfDistanceDecay 구조체](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx) 에 할당 하는 **distanceDecay** 필드에 [HrtfApoInit 구조체](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx) 전달 하기 전에 합니다 [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="0d41b-157">To implement custom decay behavior on a spatial sound, populate an [HrtfDistanceDecay struct](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx) and assign it to the **distanceDecay** field in an [HrtfApoInit struct](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx) before passing it to the [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) function.</span></span>

<span data-ttu-id="0d41b-158">다음 코드를 추가 합니다 **초기화** decay 사용자 지정 동작을 지정 하려면 이전에 표시 되는 메서드.</span><span class="sxs-lookup"><span data-stu-id="0d41b-158">Add the following code to the **Initialize** method shown previously to specify custom decay behavior.</span></span> <span data-ttu-id="0d41b-159">전체 코드 목록을 보려면 [CustomDecay.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp)합니다.</span><span class="sxs-lookup"><span data-stu-id="0d41b-159">For the complete code listing, see [CustomDecay.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp).</span></span>

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
