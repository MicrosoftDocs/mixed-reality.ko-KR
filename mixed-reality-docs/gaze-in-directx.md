---
title: DirectX의 헤드 및 눈 응시
description: 헤드 게이즈 및 시선 추적 네이티브 DirectX 앱에서 사용 하기 위한 개발자 가이드입니다.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 05/09/2019
ms.topic: article
keywords: 응시, 헤드 게이즈, 추적 하는 head, 시선 추적, directx, 입력, 홀로그램
ms.openlocfilehash: edf20a621178d76bfc97477f9f9b2eca200f1318
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414416"
---
# <a name="head-and-eye-gaze-input-in-directx"></a><span data-ttu-id="95fb8-104">헤드 및 눈 gaze DirectX의 입력</span><span class="sxs-lookup"><span data-stu-id="95fb8-104">Head and eye gaze input in DirectX</span></span>

<span data-ttu-id="95fb8-105">Windows Mixed Reality, 눈에 헤드 응시 입력에서 검색 하는 사용자가 결정할 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-105">In Windows Mixed Reality, eye and head gaze input is used to determine what the user is looking at.</span></span> <span data-ttu-id="95fb8-106">드라이브와 같은 기본 입력된 모델을 사용할 수 있습니다 [응시 및 커밋 헤드](gaze-and-commit.md), 상호 작용의 형식에 대 한 컨텍스트를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-106">This can be used to drive primary input models such as [head gaze and commit](gaze-and-commit.md), and also to provide context for types of interactions.</span></span> <span data-ttu-id="95fb8-107">두 가지가 게이즈의 API를 통해 사용할 수 있는 벡터: 게이즈 및 응시 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-107">There are two types of gaze vectors available through the API: head gaze and eye gaze.</span></span>  <span data-ttu-id="95fb8-108">3으로 나와 모두 원본 및 방향을 사용 하 여 차원 레이 합니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-108">Both are provided as a three dimensional ray with an origin and direction.</span></span> <span data-ttu-id="95fb8-109">응용 프로그램 수 다음 raycast가 백그라운드에서 또는 실제 대상인 사용자를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-109">Applications can then raycast into their scenes, or the real world, and determine what the user is targeting.</span></span>

<span data-ttu-id="95fb8-110">**헤드 gaze** 사용자의 헤드에서 가리킨 방향을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-110">**Head gaze** represents the direction that the user's head is pointed in.</span></span> <span data-ttu-id="95fb8-111">위치 및 장치 자체의 정방향으로 생각할 중심을 나타내는 위치를 사용 하 여 두 표시 간에 지점입니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-111">Think of this as the position and forward direction of the device itself, with the position representing the center point between the two displays.</span></span>  <span data-ttu-id="95fb8-112">헤드 게이즈 모든 혼합 현실 장치에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-112">Head gaze is available on all Mixed Reality devices.</span></span>

<span data-ttu-id="95fb8-113">**응시** 사용자의 눈으로 원하는 방향을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-113">**Eye gaze** represents the direction that the user's eyes are looking towards.</span></span> <span data-ttu-id="95fb8-114">원점은 사용자의 눈 사이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-114">The origin is located between the user's eyes.</span></span>  <span data-ttu-id="95fb8-115">추적 시스템 눈을 포함 하는 혼합 현실 장치에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-115">It is available on Mixed Reality devices that include an eye tracking system.</span></span>

<span data-ttu-id="95fb8-116">헤드와 눈 게이즈 광선을 통해 액세스할 수 합니다 [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API.</span><span class="sxs-lookup"><span data-stu-id="95fb8-116">Both head and eye gaze rays are accessible through the  [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API.</span></span> <span data-ttu-id="95fb8-117">호출 하기만 하면 됩니다 [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) 지정된 된 타임 스탬프 새 SpatialPointerPose 개체를 수신 하 고 [좌표계](coordinate-systems-in-directx.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-117">Simply call [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object at the specified timestamp and [coordinate system](coordinate-systems-in-directx.md).</span></span> <span data-ttu-id="95fb8-118">이 SpatialPointerPose 헤드 게이즈 원점과 방향을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-118">This SpatialPointerPose contains a head gaze origin and direction.</span></span> <span data-ttu-id="95fb8-119">또한 포함 눈 게이즈 원점과 방향을 시선 추적에 사용할 수 있는 경우.</span><span class="sxs-lookup"><span data-stu-id="95fb8-119">It also contains an eye gaze origin and direction if eye tracking is available.</span></span>

## <a name="using-head-gaze"></a><span data-ttu-id="95fb8-120">헤드 게이즈를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="95fb8-120">Using head gaze</span></span>

<span data-ttu-id="95fb8-121">헤드 응시에 액세스 하려면 호출 하 여 시작 [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) 새 SpatialPointerPose 개체를 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-121">To access the head gaze, start by calling  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object.</span></span> <span data-ttu-id="95fb8-122">다음 매개 변수를 전달 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-122">You need to pass the following parameters.</span></span>
 - <span data-ttu-id="95fb8-123">A [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) 헤드 응시에 대 한 원하는 좌표계를 나타내는입니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-123">A [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) that represents the desired coordinate system for the head gaze.</span></span> <span data-ttu-id="95fb8-124">표시 되는 *coordinatesystem입니다* 다음 코드에서 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-124">This is represented by the *coordinateSystem* variable in the following code.</span></span> <span data-ttu-id="95fb8-125">자세한 내용은 참조 하세요. 당사의 [좌표계](coordinate-systems-in-directx.md) 개발자 가이드.</span><span class="sxs-lookup"><span data-stu-id="95fb8-125">For more information, visit our [coordinate systems](coordinate-systems-in-directx.md) developer guide.</span></span>
 - <span data-ttu-id="95fb8-126">A [타임 스탬프](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) 요청 머리 포즈의 정확한 시간을 나타내는입니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-126">A [Timestamp](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) that represents the exact time of the head pose requested.</span></span>  <span data-ttu-id="95fb8-127">일반적으로 현재 프레임을 표시할 때 시간에 해당 하는 타임 스탬프를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-127">Typically you will use a timestamp that corresponds to the time when the current frame will be displayed.</span></span> <span data-ttu-id="95fb8-128">이 예측 된 디스플레이 타임 스탬프를 가져올 수 있습니다는 [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) 개체를 통해 현재 액세스할 수 있는 [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)합니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-128">You can get this predicted display timestamp from a  [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) object, which is accessible through the current [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).</span></span>  <span data-ttu-id="95fb8-129">이 HolographicFramePrediction 개체는 표현 합니다 *예측* 변수 다음 코드에서입니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-129">This HolographicFramePrediction object is represented by the *prediction* variable in the following code.</span></span>

 <span data-ttu-id="95fb8-130">유효한 SpatialPointerPose가 되 면 헤드 위치 및 정방향 속성으로 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-130">Once you have a valid SpatialPointerPose, the head position and forward direction are accessible as properties.</span></span>  <span data-ttu-id="95fb8-131">다음 코드에 액세스 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-131">The following code  shows how to access them.</span></span>

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head gaze
}
```

## <a name="using-eye-gaze"></a><span data-ttu-id="95fb8-132">응시를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="95fb8-132">Using eye gaze</span></span>

<span data-ttu-id="95fb8-133">눈 게이즈 API 헤드 게이즈 매우 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-133">The eye gaze API is very similar to head gaze.</span></span>  <span data-ttu-id="95fb8-134">에서는 동일한 [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) 원점과 방향을 장면에 대 한 raycast 수 있는 광선을 제공 하는 API입니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-134">It uses the same  [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, which provides a ray origin and direction that you can raycast against your scene.</span></span>  <span data-ttu-id="95fb8-135">유일한 차이점은 명시적으로 사용 하기 전에 눈 추적을 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-135">The only difference is that you need to explicitly enable eye tracking before using it.</span></span> <span data-ttu-id="95fb8-136">이 위해 두 단계를 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-136">For this, you need to do two steps:</span></span>
1. <span data-ttu-id="95fb8-137">시선 추적 앱에서 사용 하 여 사용자 권한을 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-137">Request user permission to use eye tracking in your app.</span></span>
2. <span data-ttu-id="95fb8-138">패키지 매니페스트에 "Gaze Input" 기능을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-138">Enable the "Gaze Input" capability in your package manifest.</span></span>

### <a name="requesting-access-to-gaze-input"></a><span data-ttu-id="95fb8-139">Gaze 입력에 대 한 액세스를 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-139">Requesting access to gaze input</span></span>
<span data-ttu-id="95fb8-140">앱 시작 시 호출 [EyesPose::RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) 눈 추적에 액세스를 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-140">When your app is starting up, call [EyesPose::RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) to request access to eye tracking.</span></span> <span data-ttu-id="95fb8-141">시스템에서 필요한 경우 사용자에 게 하 고 반환 됩니다 [GazeInputAccessStatus::Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus) 면 액세스 권한이 부여 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-141">The system will prompt the user if needed, and return [GazeInputAccessStatus::Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus) once access has been granted.</span></span> <span data-ttu-id="95fb8-142">이 비동기 호출을 이므로 약간의 추가 관리를 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-142">This is an asynchronous call, so it requires a bit of extra management.</span></span> <span data-ttu-id="95fb8-143">다음 예에서는 이라는 멤버 변수에 저장 하는 결과 기다리는 분리 std::thread 스핀업 *m_isEyeTrackingEnabled*합니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-143">The following example spins up a detached std::thread to wait for the result, which it stores to a member variable called *m_isEyeTrackingEnabled*.</span></span>

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::UI::Input;

std::thread requestAccessThread([this]()
{
    auto status = EyesPose::RequestAccessAsync().get();

    if (status == GazeInputAccessStatus::Allowed)
        m_isEyeTrackingEnabled = true;
    else
        m_isEyeTrackingEnabled = false;
});

requestAccessThread.detach();

```
<span data-ttu-id="95fb8-144">분리 된 스레드를 시작 하는 것은 비동기 호출을 처리 하기 위한 하나의 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-144">Starting a detached thread is just one option for handling async calls.</span></span>  <span data-ttu-id="95fb8-145">또는 사용할 수 있습니다 새 [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) 기능에서 지원 되는 C++/WinRT 합니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-145">Alternatively, you could use the new [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) functionality supported by C++/WinRT.</span></span>
<span data-ttu-id="95fb8-146">사용자 권한을 요구 하는 다른 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-146">Here is another example for asking for user permission:</span></span>
-   <span data-ttu-id="95fb8-147">EyesPose::IsSupported() 응용 프로그램을을 눈 추적기는 필요한 경우에 권한 대화 상자를 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-147">EyesPose::IsSupported() allows the application to trigger the permission dialog only if there is an eye tracker.</span></span>
-   <span data-ttu-id="95fb8-148">GazeInputAccessStatus m_gazeInputAccessStatus; 권한 프롬프트를 반복 해 서 팝업을 방지 하기 위해입니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-148">GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.</span></span>

```cpp
GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.

// This will trigger to show the permission prompt to the user.
// Ask for access if there is a corresponding device and registry flag did not disable it.
if (Windows::Perception::People::EyesPose::IsSupported() &&
   (m_gazeInputAccessStatus == GazeInputAccessStatus::Unspecified))
{ 
    Concurrency::create_task(Windows::Perception::People::EyesPose::RequestAccessAsync()).then(
    [this](GazeInputAccessStatus status)
    {
        // GazeInputAccessStatus::{Allowed, DeniedBySystem, DeniedByUser, Unspecified}
            m_gazeInputAccessStatus = status;
        
        // Let's be sure to not ask again.
        if(status == GazeInputAccessStatus::Unspecified)
        {
                m_gazeInputAccessStatus = GazeInputAccessStatus::DeniedBySystem;    
        }
    });
}

```


### <a name="declaring-the-gaze-input-capability"></a><span data-ttu-id="95fb8-149">선언 된 *Gaze 입력* 기능</span><span class="sxs-lookup"><span data-stu-id="95fb8-149">Declaring the *Gaze Input* capability</span></span>

<span data-ttu-id="95fb8-150">Appxmanifest 파일에서 두 번 클릭 *솔루션 탐색기*합니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-150">Double click the appxmanifest file in *Solution Explorer*.</span></span>  <span data-ttu-id="95fb8-151">으로 이동 합니다 *기능* 섹션 및 확인 합니다 *Gaze 입력* 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-151">Then navigate to the *Capabilities* section and check the *Gaze Input* capability.</span></span> 

![응시 입력된 기능](images/gaze-input-capability.png)

<span data-ttu-id="95fb8-153">다음 줄을 추가 합니다 *패키지* appxmanifest 파일의 섹션:</span><span class="sxs-lookup"><span data-stu-id="95fb8-153">This adds the following lines to the *Package* section in the appxmanifest file:</span></span>
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a><span data-ttu-id="95fb8-154">눈 게이즈 광선이 시작</span><span class="sxs-lookup"><span data-stu-id="95fb8-154">Getting the eye gaze ray</span></span>
<span data-ttu-id="95fb8-155">ET에 대 한 액세스를 받으면 프레임 마다 눈 게이즈 광선을 자유롭게 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-155">Once you have received access to ET, you are free to grab the eye gaze ray every frame.</span></span>  <span data-ttu-id="95fb8-156">헤드 게이즈 마찬가지로 가져오기 합니다 [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) 를 호출 하 여 [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) 좌표계를 원하는 타임 스탬프를 사용 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-156">Just as with head gaze, get the [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) by calling [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with a desired timestamp and coordinate system.</span></span> <span data-ttu-id="95fb8-157">SpatialPointerPose 포함을 [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) 개체를 통해 합니다 [눈](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-157">The SpatialPointerPose contains an [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) object through the [Eyes](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) property.</span></span> <span data-ttu-id="95fb8-158">이 null이 아닌 시선 추적을 사용 하는 경우에 합니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-158">This is non-null only if eye tracking is enabled.</span></span> <span data-ttu-id="95fb8-159">여기에서 확인할 수 있습니다 면 장치에서 사용자에 게 보정을 호출 하 여 추적 주시 [EyesPose::IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)합니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-159">From there you can check if the user in the device has an eye tracking calibration by calling [EyesPose::IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span></span>  <span data-ttu-id="95fb8-160">다음을 사용 하 여는 [Gaze](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) 가져올 속성을를 [SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) contianing 눈 gaze 위치 및 방향입니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-160">Next, use the [Gaze](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) property to get the a [SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) contianing the eye gaze position and direction.</span></span> <span data-ttu-id="95fb8-161">응시 속성 경우도 null을이 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-161">The Gaze property can sometimes be null, so be sure to check for this.</span></span> <span data-ttu-id="95fb8-162">이 수 발생할 경우 보정된 사용자 들은 눈이 일시적으로 닫는 경우</span><span class="sxs-lookup"><span data-stu-id="95fb8-162">This can happen is if a calibrated user temporarily closes their eyes.</span></span>

<span data-ttu-id="95fb8-163">다음 코드를 눈 게이즈 광선을 액세스 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-163">The following code shows how to access the eye gaze ray.</span></span>

```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    if (pointerPose.Eyes() && pointerPose.Eyes().IsCalibrationValid())
    {
        if (pointerPose.Eyes().Gaze())
        {
            auto spatialRay = pointerPose.Eyes().Gaze().Value();
            float3 eyeGazeOrigin = spatialRay.Origin;
            float3 eyeGazeDirection = spatialRay.Direction;
            
            // Do something with the eye gaze
        }
    }
}

```

## <a name="correlating-gaze-with-other-inputs"></a><span data-ttu-id="95fb8-164">다른 입력을 사용 하 여 상관 관계 자동 연결 응시</span><span class="sxs-lookup"><span data-stu-id="95fb8-164">Correlating gaze with other inputs</span></span>

<span data-ttu-id="95fb8-165">해야 있습니다 하는 경우에 따라 한 [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) 이벤트를 사용 하 여 이전에 해당 하는 합니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-165">Sometimes you may find that you need a [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) that corresponds with an event in the past.</span></span> <span data-ttu-id="95fb8-166">예를 들어, 사용자는 어 탭을 수행 하는 경우 앱 알아야 할 새로운 것을 보는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-166">For example, if the user performs an Air Tap, your app might want to know what they were looking at.</span></span> <span data-ttu-id="95fb8-167">이 작업을 위해 사용 하 [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) 예측 프레임 시간은 정확 하지 않습니다 시스템 입력된 처리 및 표시 시간 사이의 대기 시간 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-167">For this purpose, simply using [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with the predicted frame time would be inaccurate because of the latency between system input processing and display time.</span></span> <span data-ttu-id="95fb8-168">또한 응시 타기 팅을 사용 하는 경우 눈 커밋 작업을 완료 하기 전에 이동 경향이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-168">In addition, if using eye gaze for targeting, our eyes tend to move on even before finishing a commit action.</span></span> <span data-ttu-id="95fb8-169">이 간단한 어 탭에 대 한 문제가 되지 않습니다 이지만 빠른 눈 이동을 장기 음성 명령을 결합 하는 경우 더욱 중요 해지 합니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-169">This is less of an issue for a simple Air Tap, but becomes more critical when combining long voice commands with fast eye movements.</span></span> <span data-ttu-id="95fb8-170">이 시나리오를 처리 하는 방법은를 추가로 호출을 확인 하는 것 [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), 입력된 이벤트에 해당 하는 기록 타임 스탬프를 사용 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-170">One way to handle this scenario is to make an additional call to  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), using a historical timestamp that corresponds to the input event.</span></span>  

<span data-ttu-id="95fb8-171">그러나 SpatialInteractionManager를 통해 라우팅하는 입력 방법이 쉬운 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-171">However, for input that routes through the SpatialInteractionManager, there's an easier method.</span></span> <span data-ttu-id="95fb8-172">합니다 [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) 에 해당 자신만 [TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-172">The [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) has its very own [TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) function.</span></span> <span data-ttu-id="95fb8-173">완벽 하 게 상호 연관 된 제공 하는 호출 [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) 추측 하지 않고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95fb8-173">Calling that will provide a perfectly correlated [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) without the guesswork.</span></span> <span data-ttu-id="95fb8-174">작업 SpatialInteractionSourceStates에 대 한 자세한 내용은 잠시 살펴 합니다 [실습 및 DirectX에서 동작 컨트롤러](hands-and-motion-controllers-in-directx.md) 설명서.</span><span class="sxs-lookup"><span data-stu-id="95fb8-174">For more information on working with SpatialInteractionSourceStates, take a look at the [Hands and Motion Controllers in DirectX](hands-and-motion-controllers-in-directx.md) documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="95fb8-175">참조</span><span class="sxs-lookup"><span data-stu-id="95fb8-175">See also</span></span>
* [<span data-ttu-id="95fb8-176">헤드 게이즈 및 커밋 입력된 모델</span><span class="sxs-lookup"><span data-stu-id="95fb8-176">Head gaze and commit input model</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="95fb8-177">HoloLens 2에 응시</span><span class="sxs-lookup"><span data-stu-id="95fb8-177">Eye-gaze on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="95fb8-178">DirectX의 좌표계</span><span class="sxs-lookup"><span data-stu-id="95fb8-178">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="95fb8-179">DirectX의 음성 입력</span><span class="sxs-lookup"><span data-stu-id="95fb8-179">Voice Input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="95fb8-180">DirectX의 헤드 및 모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="95fb8-180">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
