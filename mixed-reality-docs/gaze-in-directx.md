---
title: DirectX의 헤드 및 눈 응시
description: 기본 DirectX 앱에서 헤드 응시 및 눈 추적 사용을 위한 개발자 가이드입니다.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 05/09/2019
ms.topic: article
keywords: 눈에 응시, 헤드-응시, 헤드 추적, 눈 추적, directx, 입력, holograms
ms.openlocfilehash: 2197f0ba3ecb77188d532d77ba29595c380a039d
ms.sourcegitcommit: ff330a7e36e5ff7ae0e9a08c0e99eb7f3f81361f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70122054"
---
# <a name="head-gaze-and-eye-gaze-input-in-directx"></a><span data-ttu-id="39ae8-104">헤드-DirectX에서 응시 및 눈에 응시 입력</span><span class="sxs-lookup"><span data-stu-id="39ae8-104">Head-gaze and eye-gaze input in DirectX</span></span>

<span data-ttu-id="39ae8-105">Windows Mixed Reality에서 눈 및 헤드 응시 입력은 사용자가 원하는 항목을 확인 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-105">In Windows Mixed Reality, eye and head gaze input is used to determine what the user is looking at.</span></span> <span data-ttu-id="39ae8-106">이를 사용 하 여 [헤드-응시, 커밋](gaze-and-commit.md)등의 기본 입력 모델을 구동 하 고 상호 작용 형식에 대 한 컨텍스트를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-106">This can be used to drive primary input models such as [head-gaze and commit](gaze-and-commit.md), and also to provide context for types of interactions.</span></span> <span data-ttu-id="39ae8-107">API를 통해 사용할 수 있는 두 가지 유형의 응시 벡터 인 head-응시 및 눈에 주목 합니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-107">There are two types of gaze vectors available through the API: head-gaze and eye-gaze.</span></span>  <span data-ttu-id="39ae8-108">둘 다 원점 및 방향을 사용 하 여 3 차원 광선으로 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-108">Both are provided as a three dimensional ray with an origin and direction.</span></span> <span data-ttu-id="39ae8-109">그런 다음 응용 프로그램은 자신의 장면이 나 실제 세계에이를 다시 캐스팅 하 고 사용자가 대상으로 지정 하는 내용을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-109">Applications can then raycast into their scenes, or the real world, and determine what the user is targeting.</span></span>

<span data-ttu-id="39ae8-110">**헤드-응시** 는 사용자의 헤드가 가리키는 방향을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-110">**Head-gaze** represents the direction that the user's head is pointed in.</span></span> <span data-ttu-id="39ae8-111">이를 장치 자체의 위치 및 정방향 방향으로 간주 하 고 두 표시 사이의 중심점을 나타내는 위치를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-111">Think of this as the position and forward direction of the device itself, with the position representing the center point between the two displays.</span></span> <span data-ttu-id="39ae8-112">헤드-응시는 모든 혼합 현실 장치에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-112">Head-gaze is available on all Mixed Reality devices.</span></span>

<span data-ttu-id="39ae8-113">**눈** 에 보기는 사용자의 눈이 향하는 방향을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-113">**Eye-gaze** represents the direction that the user's eyes are looking towards.</span></span> <span data-ttu-id="39ae8-114">원점은 사용자의 눈 사이에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-114">The origin is located between the user's eyes.</span></span>  <span data-ttu-id="39ae8-115">아이 추적 시스템을 포함 하는 혼합 현실 장치에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-115">It is available on Mixed Reality devices that include an eye tracking system.</span></span>

<span data-ttu-id="39ae8-116">[SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API를 통해 헤드 및 눈에 광선 모두에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-116">Both head and eye-gaze rays are accessible through the  [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API.</span></span> <span data-ttu-id="39ae8-117">[SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) 를 호출 하면 지정 된 타임 스탬프 및 [좌표계](coordinate-systems-in-directx.md)에서 새 SpatialPointerPose 개체를 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-117">Simply call [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object at the specified timestamp and [coordinate system](coordinate-systems-in-directx.md).</span></span> <span data-ttu-id="39ae8-118">이 SpatialPointerPose는 헤드-응시 원점 및 방향을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-118">This SpatialPointerPose contains a head-gaze origin and direction.</span></span> <span data-ttu-id="39ae8-119">눈동자 추적을 사용할 수 있는 경우에도 눈에 잘 응시 된 원본 및 방향을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-119">It also contains an eye-gaze origin and direction if eye tracking is available.</span></span>

## <a name="using-head-gaze"></a><span data-ttu-id="39ae8-120">헤드-응시 사용</span><span class="sxs-lookup"><span data-stu-id="39ae8-120">Using head-gaze</span></span>

<span data-ttu-id="39ae8-121">헤드-응시에 액세스 하려면 [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) 를 호출 하 여 새 SpatialPointerPose 개체를 수신 합니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-121">To access the head-gaze, start by calling  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) to receive a new SpatialPointerPose object.</span></span> <span data-ttu-id="39ae8-122">다음 매개 변수를 전달 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-122">You need to pass the following parameters.</span></span>
 - <span data-ttu-id="39ae8-123">헤드-응시에 대해 원하는 좌표계를 나타내는 [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) 입니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-123">A [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) that represents the desired coordinate system for the head-gaze.</span></span> <span data-ttu-id="39ae8-124">이는 다음 코드의 *coordinateSystem* 변수로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-124">This is represented by the *coordinateSystem* variable in the following code.</span></span> <span data-ttu-id="39ae8-125">자세한 내용은 [좌표계](coordinate-systems-in-directx.md) 개발자 가이드를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="39ae8-125">For more information, visit our [coordinate systems](coordinate-systems-in-directx.md) developer guide.</span></span>
 - <span data-ttu-id="39ae8-126">요청 된 head의 정확한 시간을 나타내는 [타임 스탬프](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) 입니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-126">A [Timestamp](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) that represents the exact time of the head pose requested.</span></span>  <span data-ttu-id="39ae8-127">일반적으로 현재 프레임이 표시 되는 시간에 해당 하는 타임 스탬프를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-127">Typically you will use a timestamp that corresponds to the time when the current frame will be displayed.</span></span> <span data-ttu-id="39ae8-128">현재 [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)를 통해 액세스할 수 있는 [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) 개체에서이 예측 표시 타임 스탬프를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-128">You can get this predicted display timestamp from a  [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) object, which is accessible through the current [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).</span></span>  <span data-ttu-id="39ae8-129">이 HolographicFramePrediction 개체는 다음 코드의 *예측* 변수로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-129">This HolographicFramePrediction object is represented by the *prediction* variable in the following code.</span></span>

 <span data-ttu-id="39ae8-130">유효한 SpatialPointerPose 면 head position 및 정방향 방향은 속성으로 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-130">Once you have a valid SpatialPointerPose, the head position and forward direction are accessible as properties.</span></span>  <span data-ttu-id="39ae8-131">다음 코드에서는 이러한 항목에 액세스 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-131">The following code  shows how to access them.</span></span>

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head-gaze
}
```

## <a name="using-eye-gaze"></a><span data-ttu-id="39ae8-132">눈동자 사용-응시</span><span class="sxs-lookup"><span data-stu-id="39ae8-132">Using eye-gaze</span></span>

<span data-ttu-id="39ae8-133">눈에 잘 드는 API는 헤드-응시와 매우 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-133">The eye-gaze API is very similar to head-gaze.</span></span>  <span data-ttu-id="39ae8-134">이 API는 동일한 [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API를 사용 합니다 .이 API는 장면에 대해 raycast 수 있는 광선 및 방향을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-134">It uses the same  [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API, which provides a ray origin and direction that you can raycast against your scene.</span></span>  <span data-ttu-id="39ae8-135">유일한 차이점은 사용 하기 전에 명시적으로 눈동자 추적을 사용 하도록 설정 해야 한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-135">The only difference is that you need to explicitly enable eye tracking before using it.</span></span> <span data-ttu-id="39ae8-136">이렇게 하려면 다음 두 단계를 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-136">For this, you need to do two steps:</span></span>
1. <span data-ttu-id="39ae8-137">앱에서 눈 추적을 사용할 수 있는 사용자 권한을 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-137">Request user permission to use eye tracking in your app.</span></span>
2. <span data-ttu-id="39ae8-138">패키지 매니페스트에서 "응시 입력" 기능을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-138">Enable the "Gaze Input" capability in your package manifest.</span></span>

### <a name="requesting-access-to-eye-gaze-input"></a><span data-ttu-id="39ae8-139">눈동자-응시 입력에 대 한 액세스 요청</span><span class="sxs-lookup"><span data-stu-id="39ae8-139">Requesting access to eye-gaze input</span></span>
<span data-ttu-id="39ae8-140">앱이 시작 되 면 [EyesPose:: RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) 를 호출 하 여 눈동자 추적에 대 한 액세스를 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-140">When your app is starting up, call [EyesPose::RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) to request access to eye tracking.</span></span> <span data-ttu-id="39ae8-141">필요한 경우 시스템에서 사용자에 게 묻는 메시지를 표시 하 고 액세스가 부여 된 후에 [GazeInputAccessStatus:: Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus) 를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-141">The system will prompt the user if needed, and return [GazeInputAccessStatus::Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus) once access has been granted.</span></span> <span data-ttu-id="39ae8-142">비동기 호출 이므로 약간의 추가 관리가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-142">This is an asynchronous call, so it requires a bit of extra management.</span></span> <span data-ttu-id="39ae8-143">다음 예제에서는 *m_isEyeTrackingEnabled*라는 멤버 변수에 저장 하는 결과를 대기 하도록 분리 된 std:: thread를 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-143">The following example spins up a detached std::thread to wait for the result, which it stores to a member variable called *m_isEyeTrackingEnabled*.</span></span>

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
<span data-ttu-id="39ae8-144">분리 된 스레드를 시작 하는 것은 비동기 호출을 처리 하는 한 가지 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-144">Starting a detached thread is just one option for handling async calls.</span></span>  <span data-ttu-id="39ae8-145">또는/Winrt. C++지 원하는 새로운 [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-145">Alternatively, you could use the new [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) functionality supported by C++/WinRT.</span></span>
<span data-ttu-id="39ae8-146">사용자에 게 권한을 요청 하는 또 다른 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-146">Here is another example for asking for user permission:</span></span>
-   <span data-ttu-id="39ae8-147">EyesPose:: IsSupported ()를 사용 하면 응용 프로그램에서 아이 트래커가 있는 경우에만 사용 권한 대화 상자를 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-147">EyesPose::IsSupported() allows the application to trigger the permission dialog only if there is an eye tracker.</span></span>
-   <span data-ttu-id="39ae8-148">GazeInputAccessStatus m_gazeInputAccessStatus; 이는 사용 권한 프롬프트를 다시 표시 하지 않도록 하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-148">GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.</span></span>

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


### <a name="declaring-the-gaze-input-capability"></a><span data-ttu-id="39ae8-149">*응시 입력* 기능 선언</span><span class="sxs-lookup"><span data-stu-id="39ae8-149">Declaring the *Gaze Input* capability</span></span>

<span data-ttu-id="39ae8-150">*솔루션 탐색기*에서 appxmanifest.xml 파일을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-150">Double click the appxmanifest file in *Solution Explorer*.</span></span>  <span data-ttu-id="39ae8-151">그런 다음 *기능* 섹션으로 이동 하 여 *응시 입력* 기능을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-151">Then navigate to the *Capabilities* section and check the *Gaze Input* capability.</span></span> 

![입력 기능 응시](images/gaze-input-capability.png)

<span data-ttu-id="39ae8-153">그러면 appxmanifest.xml 파일의 *Package* 섹션에 다음 줄이 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-153">This adds the following lines to the *Package* section in the appxmanifest file:</span></span>
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a><span data-ttu-id="39ae8-154">눈에 보기-응시 광선</span><span class="sxs-lookup"><span data-stu-id="39ae8-154">Getting the eye-gaze ray</span></span>
<span data-ttu-id="39ae8-155">ET에 대 한 액세스를 받은 후에는 모든 프레임에서 눈에 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-155">Once you have received access to ET, you are free to grab the eye-gaze ray every frame.</span></span>
<span data-ttu-id="39ae8-156">Head-응시와 마찬가지로 원하는 타임 스탬프 및 좌표계를 사용 하 여 [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) 를 호출 하 여 [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) 를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-156">Just as with head-gaze, get the [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) by calling [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with a desired timestamp and coordinate system.</span></span> <span data-ttu-id="39ae8-157">SpatialPointerPose는 [눈동자](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) 속성을 통해 [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) 개체를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-157">The SpatialPointerPose contains an [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) object through the [Eyes](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) property.</span></span> <span data-ttu-id="39ae8-158">이는 눈동자 추적을 사용 하는 경우에만 null이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-158">This is non-null only if eye tracking is enabled.</span></span> <span data-ttu-id="39ae8-159">여기에서 [EyesPose:: IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)를 호출 하 여 장치의 사용자에 게 눈 추적 보정이 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-159">From there you can check if the user in the device has an eye tracking calibration by calling [EyesPose::IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).</span></span>  <span data-ttu-id="39ae8-160">그런 다음, [응시](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) 속성을 사용 하 여 [SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) contianing를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-160">Next, use the [Gaze](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) property to get the a [SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) contianing the eye-gaze position and direction.</span></span> <span data-ttu-id="39ae8-161">응시 속성은 null 일 수 있으므로이를 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-161">The Gaze property can sometimes be null, so be sure to check for this.</span></span> <span data-ttu-id="39ae8-162">이는 보정 된 사용자가 일시적으로 눈동자를 닫는 경우에 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-162">This can happen is if a calibrated user temporarily closes their eyes.</span></span>

<span data-ttu-id="39ae8-163">다음 코드에서는 눈에 잘 응시 하는 빛에 액세스 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-163">The following code shows how to access the eye-gaze ray.</span></span>

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
            
            // Do something with the eye-gaze
        }
    }
}

```

## <a name="correlating-gaze-with-other-inputs"></a><span data-ttu-id="39ae8-164">다른 입력과의 응시 상관 관계</span><span class="sxs-lookup"><span data-stu-id="39ae8-164">Correlating gaze with other inputs</span></span>

<span data-ttu-id="39ae8-165">경우에 따라 과거의 이벤트에 해당 하는 [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) 이 필요 하다는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-165">Sometimes you may find that you need a [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) that corresponds with an event in the past.</span></span> <span data-ttu-id="39ae8-166">예를 들어 사용자가 공중 탭을 수행 하는 경우 앱에서 원하는 내용을 알고 싶을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-166">For example, if the user performs an Air Tap, your app might want to know what they were looking at.</span></span> <span data-ttu-id="39ae8-167">이러한 목적을 위해 시스템 입력 처리와 표시 시간 사이의 대기 시간 때문에 예측 된 프레임 시간에 [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) 를 사용 하는 것은 정확 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-167">For this purpose, simply using [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) with the predicted frame time would be inaccurate because of the latency between system input processing and display time.</span></span> <span data-ttu-id="39ae8-168">또한 대상 지정을 위해 눈동자-응시를 사용 하는 경우 커밋 작업을 완료 하기 전에도 눈에 잘 이동 하는 경향이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-168">In addition, if using eye-gaze for targeting, our eyes tend to move on even before finishing a commit action.</span></span> <span data-ttu-id="39ae8-169">이는 간단한 공기 탭에 대 한 문제는 적지만 긴 음성 명령을 빠른 시각 이동과 결합할 때 더 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-169">This is less of an issue for a simple Air Tap, but becomes more critical when combining long voice commands with fast eye movements.</span></span> <span data-ttu-id="39ae8-170">이 시나리오를 처리 하는 한 가지 방법은 입력 이벤트에 해당 하는 기록 타임 스탬프를 사용 하 여 [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)에 대 한 추가 호출을 수행 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-170">One way to handle this scenario is to make an additional call to  [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), using a historical timestamp that corresponds to the input event.</span></span>  

<span data-ttu-id="39ae8-171">그러나 SpatialInteractionManager을 통해 라우팅하는 입력의 경우 더 쉬운 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-171">However, for input that routes through the SpatialInteractionManager, there's an easier method.</span></span> <span data-ttu-id="39ae8-172">[SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) 에는 고유한 [TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) 함수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-172">The [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) has its very own [TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) function.</span></span> <span data-ttu-id="39ae8-173">이를 호출 하면 추측 하지 않고 완벽 하 게 상호 관련 된 [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39ae8-173">Calling that will provide a perfectly correlated [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) without the guesswork.</span></span> <span data-ttu-id="39ae8-174">SpatialInteractionSourceStates로 작업 하는 방법에 대 한 자세한 내용은 DirectX 설명서 [에서 직접 및 동작 컨트롤러](hands-and-motion-controllers-in-directx.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="39ae8-174">For more information on working with SpatialInteractionSourceStates, take a look at the [Hands and Motion Controllers in DirectX](hands-and-motion-controllers-in-directx.md) documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="39ae8-175">참조</span><span class="sxs-lookup"><span data-stu-id="39ae8-175">See also</span></span>
* [<span data-ttu-id="39ae8-176">헤드-응시 및 커밋 입력 모델</span><span class="sxs-lookup"><span data-stu-id="39ae8-176">Head-gaze and commit input model</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="39ae8-177">눈동자-HoloLens에서 응시 2</span><span class="sxs-lookup"><span data-stu-id="39ae8-177">Eye-gaze on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="39ae8-178">조정</span><span class="sxs-lookup"><span data-stu-id="39ae8-178">Calibration</span></span>](calibration.md)
* [<span data-ttu-id="39ae8-179">DirectX의 좌표계</span><span class="sxs-lookup"><span data-stu-id="39ae8-179">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="39ae8-180">DirectX의 음성 입력</span><span class="sxs-lookup"><span data-stu-id="39ae8-180">Voice Input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="39ae8-181">DirectX의 헤드 및 모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="39ae8-181">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
