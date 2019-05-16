---
title: DirectX의 헤드 및 눈 응시
description: 헤드 게이즈 및 시선 추적 네이티브 DirectX 앱에서 사용 하기 위한 개발자 가이드입니다.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 05/09/2019
ms.topic: article
keywords: 응시, 헤드 게이즈, 추적 하는 head, 시선 추적, directx, 입력, 홀로그램
ms.openlocfilehash: f9764132df0ca4ae2f02d8f9a5740530676eb4f5
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629616"
---
# <a name="head-and-eye-gaze-in-directx"></a>DirectX의 헤드 및 눈 응시

Windows Mixed Reality 응시 입력에서 확인 하는 사용자가 결정 하기 위해 사용 됩니다. 드라이브와 같은 기본 입력된 모델을 사용할 수 있습니다 [gaze 및 커밋](gaze-and-commit.md), 상호 작용의 형식에 대 한 컨텍스트를 제공할 수 있습니다. 두 가지가 게이즈의 API를 통해 사용할 수 있는 벡터: 게이즈 및 응시 이동 합니다.  3으로 나와 모두 원본 및 방향을 사용 하 여 차원 레이 합니다. 응용 프로그램 수 다음 raycast가 백그라운드에서 또는 실제 대상인 사용자를 확인 합니다.

**헤드 gaze** 사용자의 헤드에서 가리킨 방향을 나타냅니다. 위치 및 장치 자체의 정방향으로 생각할 중심을 나타내는 위치를 사용 하 여 두 표시 간에 지점입니다.  헤드 게이즈 모든 혼합 현실 장치에서 제공 됩니다.

**응시** 사용자의 눈으로 원하는 방향을 나타냅니다. 원점은 사용자의 눈 사이 있습니다.  추적 시스템 눈을 포함 하는 혼합 현실 장치에서 제공 됩니다.

헤드와 눈 게이즈 광선을 통해 액세스할 수 합니다 [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API. 호출 하기만 하면 됩니다 [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) 지정된 된 타임 스탬프 새 SpatialPointerPose 개체를 수신 하 고 [좌표계](coordinate-systems-in-directx.md)합니다. 이 SpatialPointerPose 헤드 게이즈 원점과 방향을 포함합니다. 또한 포함 눈 게이즈 원점과 방향을 시선 추적에 사용할 수 있는 경우.

## <a name="using-head-gaze"></a>헤드 게이즈를 사용 하 여

헤드 응시에 액세스 하려면 호출 하 여 시작 [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) 새 SpatialPointerPose 개체를 받을 수 있습니다. 다음 매개 변수를 전달 해야 합니다.
 - A [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) 헤드 응시에 대 한 원하는 좌표계를 나타내는입니다. 표시 되는 *coordinatesystem입니다* 다음 코드에서 변수입니다. 자세한 내용은 참조 하세요. 당사의 [좌표계](coordinate-systems-in-directx.md) 개발자 가이드.
 - A [타임 스탬프](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) 요청 머리 포즈의 정확한 시간을 나타내는입니다.  일반적으로 현재 프레임을 표시할 때 시간에 해당 하는 타임 스탬프를 사용 합니다. 이 예측 된 디스플레이 타임 스탬프를 가져올 수 있습니다는 [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) 개체를 통해 현재 액세스할 수 있는 [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)합니다.  이 HolographicFramePrediction 개체는 표현 합니다 *예측* 변수 다음 코드에서입니다.

 유효한 SpatialPointerPose가 되 면 헤드 위치 및 정방향 속성으로 액세스할 수 있습니다.  다음 코드에 액세스 하는 방법을 보여 줍니다.

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

## <a name="using-eye-gaze"></a>응시를 사용 하 여

눈 게이즈 API 헤드 게이즈 매우 비슷합니다.  에서는 동일한 [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) 원점과 방향을 장면에 대 한 raycast 수 있는 광선을 제공 하는 API입니다.  유일한 차이점은 명시적으로 시선 액세스를 요청 하 여 사용 하기 전에 추적을 사용 하도록 설정 해야 합니다.

### <a name="declaring-the-gaze-input-capability"></a>선언 된 *Gaze 입력* 기능

Appxmanifest 파일에서 두 번 클릭 *솔루션 탐색기*합니다.  으로 이동 합니다 *기능* 섹션 및 확인 합니다 *Gaze 입력* 기능입니다. 

![응시 입력된 기능](images/gaze-input-capability.png)

다음 줄을 추가 합니다 *패키지* appxmanifest 파일의 섹션:
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="requesting-access-to-gaze-input"></a>Gaze 입력에 대 한 액세스를 요청 합니다.
앱 시작 시 호출 [EyesPose::RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) 눈 추적에 액세스를 요청 합니다. 시스템에서 필요한 경우 사용자에 게 하 고 반환 됩니다 [GazeInputAccessStatus::Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus) 면 액세스 권한이 부여 되었습니다. 이 비동기 호출을 이므로 약간의 추가 관리를 필요 합니다. 다음 예에서는 이라는 멤버 변수에 저장 하는 결과 기다리는 분리 std::thread 스핀업 *m_isEyeTrackingEnabled*합니다.

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

분리 된 스레드를 시작 하는 것은 비동기 호출을 처리 하기 위한 하나의 옵션입니다.  또는 사용할 수 있습니다 새 [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) 기능에서 지원 되는 C++/WinRT 합니다.

### <a name="getting-the-eye-gaze-ray"></a>눈 게이즈 광선이 시작

ET에 대 한 액세스를 받으면 프레임 마다 눈 게이즈 광선을 자유롭게 수 있습니다.  헤드 게이즈 마찬가지로 가져오기 합니다 [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) 를 호출 하 여 [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) 좌표계를 원하는 타임 스탬프를 사용 하 여 합니다. SpatialPointerPose 포함을 [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) 개체를 통해 합니다 [눈](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) 속성입니다. 이 null이 아닌 시선 추적을 사용 하는 경우에 합니다. 여기에서 확인할 수 있습니다 면 장치에서 사용자에 게 보정을 호출 하 여 추적 주시 [EyesPose::IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)합니다.  다음을 사용 하 여는 [Gaze](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) 가져올 속성을를 [SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) contianing 눈 gaze 위치 및 방향입니다. 응시 속성 경우도 null을이 확인 해야 합니다. 이 수 발생할 경우 보정된 사용자 들은 눈이 일시적으로 닫는 경우

다음 코드를 눈 게이즈 광선을 액세스 하는 방법을 보여 줍니다.

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

## <a name="correlating-gaze-with-other-inputs"></a>다른 입력을 사용 하 여 상관 관계 자동 연결 응시

해야 있습니다 하는 경우에 따라 한 [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) 이벤트를 사용 하 여 이전에 해당 하는 합니다. 예를 들어, 사용자는 어 탭을 수행 하는 경우 앱 알아야 할 새로운 것을 보는 것입니다. 이 작업을 위해 사용 하 [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) 예측 프레임 시간은 정확 하지 않습니다 시스템 입력된 처리 및 표시 시간 사이의 대기 시간 때문입니다.

이 시나리오를 처리 하는 방법은를 추가로 호출을 확인 하는 것 [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), 입력된 이벤트에 해당 하는 기록 타임 스탬프를 사용 하 여 합니다.  그러나 SpatialInteractionManager를 통해 라우팅하는 입력 방법이 쉬운 방법입니다. 합니다 [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) 에 해당 자신만 [TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) 함수입니다. 완벽 하 게 상호 연관 된 제공 하는 호출 [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) 추측 하지 않고 있습니다. 작업 SpatialInteractionSourceStates에 대 한 자세한 내용은 잠시 살펴 합니다 [실습 및 DirectX에서 동작 컨트롤러](hands-and-motion-controllers-in-directx.md) 설명서.

## <a name="see-also"></a>참조
* [실습 및 DirectX에서 컨트롤러 동작](hands-and-motion-controllers-in-directx.md)
* [DirectX의 좌표계](coordinate-systems-in-directx.md)
* [입력된 모델을 응시 및 커밋](gaze-and-commit.md)

