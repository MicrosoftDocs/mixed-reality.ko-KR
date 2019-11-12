---
title: DirectX의 헤드 및 눈 응시
description: 기본 DirectX 앱에서 헤드 응시 및 눈 추적 사용을 위한 개발자 가이드입니다.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 05/09/2019
ms.topic: article
keywords: 눈에 응시, 헤드-응시, 헤드 추적, 눈 추적, directx, 입력, holograms
ms.openlocfilehash: 664657b9ab01530a608e31091823e828cc99d0cd
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926555"
---
# <a name="head-gaze-and-eye-gaze-input-in-directx"></a>헤드-DirectX에서 응시 및 눈에 응시 입력

Windows Mixed Reality에서 눈 및 헤드 응시 입력은 사용자가 원하는 항목을 확인 하는 데 사용 됩니다. 이를 사용 하 여 [헤드-응시, 커밋](gaze-and-commit.md)등의 기본 입력 모델을 구동 하 고 상호 작용 형식에 대 한 컨텍스트를 제공할 수 있습니다. API를 통해 사용할 수 있는 두 가지 유형의 응시 벡터 인 head-응시 및 눈에 주목 합니다.  둘 다 원점 및 방향을 사용 하 여 3 차원 광선으로 제공 됩니다. 그런 다음 응용 프로그램은 자신의 장면이 나 실제 세계에이를 다시 캐스팅 하 고 사용자가 대상으로 지정 하는 내용을 확인할 수 있습니다.

**헤드-응시** 는 사용자의 헤드가 가리키는 방향을 나타냅니다. 이를 장치 자체의 위치 및 정방향 방향으로 간주 하 고 두 표시 사이의 중심점을 나타내는 위치를 사용 합니다. 헤드-응시는 모든 혼합 현실 장치에서 사용할 수 있습니다.

**눈** 에 보기는 사용자의 눈이 향하는 방향을 나타냅니다. 원점은 사용자의 눈 사이에 있습니다.  아이 추적 시스템을 포함 하는 혼합 현실 장치에서 사용할 수 있습니다.

[SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API를 통해 헤드 및 눈에 광선 모두에 액세스할 수 있습니다. [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) 를 호출 하면 지정 된 타임 스탬프 및 [좌표계](coordinate-systems-in-directx.md)에서 새 SpatialPointerPose 개체를 받을 수 있습니다. 이 SpatialPointerPose는 헤드-응시 원점 및 방향을 포함 합니다. 눈동자 추적을 사용할 수 있는 경우에도 눈에 잘 응시 된 원본 및 방향을 포함 합니다.

### <a name="device-support"></a>장치 지원
<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>기능과</strong></td>
     <td><a href="hololens-hardware-details.md"><strong>HoloLens(1세대)</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
</tr>
<tr>
     <td>헤드 게이즈(head-gaze)</td>
     <td>✔️</td>
     <td>✔️</td>
     <td>✔️</td>
</tr>
<tr>
     <td>눈-응시</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>

## <a name="using-head-gaze"></a>헤드-응시 사용

헤드-응시에 액세스 하려면 [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) 를 호출 하 여 새 SpatialPointerPose 개체를 수신 합니다. 다음 매개 변수를 전달 해야 합니다.
 - 헤드-응시에 대해 원하는 좌표계를 나타내는 [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) 입니다. 이는 다음 코드의 *coordinateSystem* 변수로 표시 됩니다. 자세한 내용은 [좌표계](coordinate-systems-in-directx.md) 개발자 가이드를 참조 하세요.
 - 요청 된 head의 정확한 시간을 나타내는 [타임 스탬프](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) 입니다.  일반적으로 현재 프레임이 표시 되는 시간에 해당 하는 타임 스탬프를 사용 합니다. 현재 [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe)를 통해 액세스할 수 있는 [HolographicFramePrediction](https://docs.microsoft.com//uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) 개체에서이 예측 표시 타임 스탬프를 가져올 수 있습니다.  이 HolographicFramePrediction 개체는 다음 코드의 *예측* 변수로 표시 됩니다.

 유효한 SpatialPointerPose 면 head position 및 정방향 방향은 속성으로 액세스할 수 있습니다.  다음 코드에서는 이러한 항목에 액세스 하는 방법을 보여 줍니다.

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

## <a name="using-eye-gaze"></a>눈동자 사용-응시

사용자가 눈에 잘 맞는 입력을 사용 하려면 장치를 처음 사용할 때 각 사용자가 [눈 추적 사용자 보정](calibration.md) 을 진행 해야 합니다. 눈에 잘 드는 API는 헤드-응시와 매우 비슷합니다.
이 API는 동일한 [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API를 사용 합니다 .이 API는 장면에 대해 raycast 수 있는 광선 및 방향을 제공 합니다.  유일한 차이점은 사용 하기 전에 명시적으로 눈동자 추적을 사용 하도록 설정 해야 한다는 것입니다. 이렇게 하려면 다음 두 단계를 수행 해야 합니다.
1. 앱에서 눈 추적을 사용할 수 있는 사용자 권한을 요청 합니다.
2. 패키지 매니페스트에서 "응시 입력" 기능을 사용 하도록 설정 합니다.

### <a name="requesting-access-to-eye-gaze-input"></a>눈동자-응시 입력에 대 한 액세스 요청
앱이 시작 되 면 [EyesPose:: RequestAccessAsync](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) 를 호출 하 여 눈동자 추적에 대 한 액세스를 요청 합니다. 필요한 경우 시스템에서 사용자에 게 묻는 메시지를 표시 하 고 액세스가 부여 된 후에 [GazeInputAccessStatus:: Allowed](https://docs.microsoft.com//uwp/api/windows.ui.input.gazeinputaccessstatus) 를 반환 합니다. 비동기 호출 이므로 약간의 추가 관리가 필요 합니다. 다음 예제에서는 분리 된 std:: thread를 회전 하 여 *m_isEyeTrackingEnabled*이라는 멤버 변수에 저장 하는 결과를 기다립니다.

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
분리 된 스레드를 시작 하는 것은 비동기 호출을 처리 하는 한 가지 옵션입니다. 또는/Winrt. C++지 원하는 새로운 [co_await](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) 기능을 사용할 수 있습니다.
사용자에 게 권한을 요청 하는 또 다른 예는 다음과 같습니다.
-   EyesPose:: IsSupported ()를 사용 하면 응용 프로그램에서 아이 트래커가 있는 경우에만 사용 권한 대화 상자를 트리거할 수 있습니다.
-   GazeInputAccessStatus m_gazeInputAccessStatus; 이는 사용 권한 프롬프트를 다시 표시 하지 않도록 하기 위한 것입니다.

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

### <a name="declaring-the-gaze-input-capability"></a>*응시 입력* 기능 선언

*솔루션 탐색기*에서 appxmanifest.xml 파일을 두 번 클릭 합니다.  그런 다음 *기능* 섹션으로 이동 하 여 *응시 입력* 기능을 선택 합니다. 

![입력 기능 응시](images/gaze-input-capability.png)

그러면 appxmanifest.xml 파일의 *Package* 섹션에 다음 줄이 추가 됩니다.
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a>눈에 보기-응시 광선
ET에 대 한 액세스를 받은 후에는 모든 프레임에서 눈에 볼 수 있습니다.
Head-응시와 마찬가지로 원하는 타임 스탬프 및 좌표계를 사용 하 여 [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) 를 호출 하 여 [SpatialPointerPose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) 를 가져옵니다. SpatialPointerPose는 [눈동자](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) 속성을 통해 [EyesPose](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose) 개체를 포함 합니다. 이는 눈동자 추적을 사용 하는 경우에만 null이 아닙니다. 여기에서 [EyesPose:: IsCalibrationValid](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)를 호출 하 여 장치의 사용자에 게 눈 추적 보정이 있는지 확인할 수 있습니다.  그런 다음, [응시](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) 속성을 사용 하 여 눈에 [SpatialRay](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialray) 위치와 방향을 포함 하는을 가져옵니다. 응시 속성은 null 일 수 있으므로이를 확인 해야 합니다. 이는 보정 된 사용자가 일시적으로 눈동자를 닫는 경우에 발생할 수 있습니다.

다음 코드에서는 눈에 잘 응시 하는 빛에 액세스 하는 방법을 보여 줍니다.

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

## <a name="fallback-when-eye-tracking-is-not-available"></a>눈 추적을 사용할 수 없는 경우 대체 (Fallback)
[아이 추적 디자인 문서](eye-tracking.md#fallback-solutions-when-eye-tracking-is-not-available)에 설명 된 것 처럼 개발자와 개발자는 모두 응용 프로그램에 대 한 아이 추적 데이터를 사용할 수 없는 인스턴스가 있을 수 있음을 알고 있어야 합니다.
이는 사용자가 보정 하지 않는 것과 같은 다양 한 이유가 있습니다. 사용자는 자신의 눈 추적 데이터 또는 단순한 interferences (예: HoloLens 센터 또는 머리카락의 얼룩 occluding 사용자의 눈동자)에 대 한 앱 액세스를 거부 했습니다. 이 문서에서 일부 Api를 이미 언급 했지만, 다음에는이에 대 한 빠른 참조로 사용할 수 있는 눈 추적을 감지 하는 방법에 대 한 요약을 제공 합니다. 

* 시스템이 아이 추적을 지원 하는지 확인 합니다. 다음 *메서드*를 호출 합니다. [EyesPose ()](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)

* 사용자가 보정 되었는지 확인 합니다. 다음 *속성*을 호출 합니다. [EyesPose. IsCalibrationValid](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid) 

* 사용자에 게 눈 추적 데이터를 사용할 수 있는 권한을 부여 했는지 확인 합니다. 현재 _' GazeInputAccessStatus '_ 를 검색 합니다. 이 작업을 수행 하는 방법에 대 한 예제는 [응시 입력에 대 한 액세스 요청](https://docs.microsoft.com/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input)에 설명 되어 있습니다.   

또한 수신 된 눈동자 추적 데이터 업데이트 사이에 시간 제한을 추가 하 고, 아래 설명 된 대로 head-응시로 대체 하 여 눈 추적 데이터가 부실 하지 않았는지 확인할 수 있습니다.  
자세한 내용은 [대체 디자인 고려 사항](eye-tracking.md#fallback-solutions-when-eye-tracking-is-not-available) 을 참조 하세요.

<br>

## <a name="correlating-gaze-with-other-inputs"></a>다른 입력과의 응시 상관 관계
경우에 따라 과거의 이벤트에 해당 하는 [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) 이 필요 하다는 것을 알 수 있습니다. 예를 들어 사용자가 공중 탭을 수행 하는 경우 앱에서 원하는 내용을 알고 싶을 수 있습니다. 이러한 목적을 위해 시스템 입력 처리와 표시 시간 사이의 대기 시간 때문에 예측 된 프레임 시간에 [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) 를 사용 하는 것은 정확 하지 않습니다. 또한 대상 지정을 위해 눈동자-응시를 사용 하는 경우 커밋 작업을 완료 하기 전에도 눈에 잘 이동 하는 경향이 있습니다. 이는 간단한 공기 탭에 대 한 문제는 적지만 긴 음성 명령을 빠른 시각 이동과 결합할 때 더 중요 합니다. 이 시나리오를 처리 하는 한 가지 방법은 입력 이벤트에 해당 하는 기록 타임 스탬프를 사용 하 여 [SpatialPointerPose:: TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)에 대 한 추가 호출을 수행 하는 것입니다.  

그러나 SpatialInteractionManager을 통해 라우팅하는 입력의 경우 더 쉬운 방법이 있습니다. [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) 에는 고유한 [TryGetAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) 함수가 있습니다. 이를 호출 하면 추측 하지 않고 완벽 하 게 상호 관련 된 [SpatialPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) 제공 됩니다. SpatialInteractionSourceStates로 작업 하는 방법에 대 한 자세한 내용은 DirectX 설명서 [에서 직접 및 동작 컨트롤러](hands-and-motion-controllers-in-directx.md) 를 참조 하세요.

<br>

## <a name="calibration"></a>보정
눈 추적을 정확 하 게 수행 하려면 각 사용자가 [눈 추적 사용자 보정](calibration.md)을 진행 해야 합니다. 이를 통해 장치는 사용자에 게 더 편안 하 고 높은 품질의 시청 환경을 제공 하 고 동시에 정확한 시각 추적을 보장 합니다. 개발자는 사용자 보정을 관리 하기 위해 최종 작업을 수행할 필요가 없습니다. 시스템은 다음과 같은 상황에서 사용자에 게 장치를 보정할 것인지 묻는 메시지를 표시 합니다.
* 사용자가 처음으로 장치를 사용 하 고 있습니다.
* 사용자가 이전에 보정 프로세스를 옵트아웃 했음
* 사용자가 장치를 마지막으로 사용한 후 보정 프로세스가 성공 하지 못했습니다.

개발자는 아이 추적 데이터를 사용 하지 못할 수 있는 사용자를 적절 하 게 지원 해야 합니다. [Hololens 2의 시각 추적](eye-tracking.md)에서 대체 솔루션에 대 한 고려 사항에 대해 자세히 알아보세요.

<br>

## <a name="see-also"></a>참고 항목
* [조정](calibration.md)
* [DirectX의 좌표계](coordinate-systems-in-directx.md)
* [눈동자-HoloLens에서 응시 2](eye-tracking.md)
* [입력 모델 응시 및 커밋](gaze-and-commit.md)
* [DirectX의 헤드 및 모션 컨트롤러](hands-and-motion-controllers-in-directx.md)
* [DirectX의 음성 입력](voice-input-in-directx.md)
