---
title: Perception 시뮬레이션
description: 몰입 형 응용 프로그램에 대 한 시뮬레이션 된 입력을 자동화 하는 Perception 시뮬레이션 라이브러리를 사용 하는 데
author: pbarnettms
ms.author: pbarnett
ms.date: 04/26/2019
ms.topic: article
keywords: HoloLens, 시뮬레이션 테스트
ms.openlocfilehash: 8152181bdbe8c83d2b706b34f1f2fb5d51f4c880
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414527"
---
# <a name="perception-simulation"></a>Perception 시뮬레이션

앱에 대 한 자동화 된 테스트를 작성 하 시겠습니까? 구성 요소 수준 단위 테스트 뿐만 아니라 실제로 사용자 앱에 종단 간 연습을 테스트 하 시겠습니까? Perception 시뮬레이션은 원하는 것입니다. Perception 시뮬레이션 라이브러리 휴먼 보내고 world 테스트를 자동화할 수 있도록 앱에 데이터를 입력 합니다. 예를 들어 휴먼 구체적이 고 반복 가능한 위치로 확인 및 제스처를 수행 하는 다음 또는 동작 컨트롤러를 사용 하 여 입력을 시뮬레이션할 수 있습니다.

Perception 시뮬레이션 실제 HoloLens, HoloLens 에뮬레이터에 이와 같은 시뮬레이션 된 입력을 보낼 수 있습니다 (첫 번째 gen) HoloLens 혼합 현실 포털을 사용 하 여 PC를 2 에뮬레이터를 설치 합니다. Perception 혼합 현실 장치에서 실시간 센서를 무시 하 고 전송 하는 시뮬레이션 장치에서 실행 중인 응용 프로그램에 대 한 입력을 시뮬레이션 합니다. 응용 프로그램은 항상 사용 하 고 실제 센서와 Perception 시뮬레이션을 사용 하 여 실행을 사용 하 여 실행 차이 구별할 수 없습니다. 동일한 Api 통해 이러한 입력된 이벤트를 수신 합니다. Perception 시뮬레이션은 시뮬레이션 된 입력 HoloLens 가상 컴퓨터에 보낼 HoloLens 에뮬레이터에서 사용 하는 동일한 기술입니다.

코드에서 시뮬레이션을 사용 하려면 IPerceptionSimulationManager 개체를 만들어 시작 합니다. 이 개체에서 속성을 시뮬레이션 된 "사용자"를 헤드 위치, 손 모양 위치 및 제스처를 포함 하 여 제어 하는 명령을 실행할 수 있습니다 및 사용 하도록 설정 하 고 동작 컨트롤러를 조작할 수 있습니다.

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a>Perception 시뮬레이션에 대 한 Visual Studio 프로젝트 설정
1. [HoloLens 에뮬레이터를 설치할](install-the-tools.md) 개발 PC의 합니다. 에뮬레이터는 Perception 시뮬레이션 하는 데 사용할 라이브러리를 포함 합니다.
2. 새 Visual Studio를 만들려면 C# 데스크톱 프로젝트 (콘솔 프로젝트를 시작 하려면 잘 작동).
3. 다음 이진 파일을 프로젝트에 참조로 추가 (프로젝트-> 추가-> 참조...). %ProgramFiles (x86) %\Microsoft XDE에서에서 찾을 수 있습니다\\(버전)와 같은 **%ProgramFiles (x86) %\Microsoft XDE\\10.0.18362.0** HoloLens 2 에뮬레이터에 대 한 합니다.  (참고: 이진 파일에는 HoloLens 2 에뮬레이터 포함 되어 있지만 작동 하기도 Windows Mixed Reality에 대 한 바탕 화면입니다.) 합니다. PerceptionSimulationManager.Interop.dll-관리 되는 C# Perception 시뮬레이션에 대 한 래퍼입니다.
    b. PerceptionSimulationRest.dll-HoloLens 또는 에뮬레이터에 웹 소켓 통신 채널을 설정 하기 위한 라이브러리입니다.
    c. SimulationStream.Interop.dll-시뮬레이션에 대 한 공유 형식입니다.
4. 구현을 추가 프로젝트에 이진 PerceptionSimulationManager.dll를 합니다. 먼저 프로젝트에는 이진 형식으로 추가 (프로젝트-> 추가-> 기존 항목...). 프로젝트 소스 폴더에 복사 하지 않습니다 고 링크로 저장 합니다. ![프로젝트에 링크로 PerceptionSimulationManager.dll 추가할](images/saveaslink.png) b. 있는지를 확인 한 다음 빌드 출력 폴더로 복사의 가져올 것입니다. 이진 파일에 대 한 속성 시트입니다. ![출력 디렉터리로 복사할 PerceptionSimulationManager.dll 표시](images/copyalways.png)
5. 활성 솔루션 플랫폼을 x64로 설정 합니다.  () 사용 하 여 항목을 만드는 플랫폼 x64에 대 한 경우 Configuration Manager 이미 존재 하지 않습니다.

## <a name="creating-an-iperceptionsimulation-manager-object"></a>IPerceptionSimulation Manager 개체 만들기

시뮬레이션을 제어 하려면 IPerceptionSimulationManager 개체에서 검색 된 개체에 업데이트를 실행할 수 있습니다. 첫 번째 단계는 해당 개체를 가져오고 대상 장치 또는 에뮬레이터에 연결 하는 것입니다. 장치 포털 단추를 클릭 하 여 에뮬레이터의 IP 주소를 가져올 수 있습니다는 [도구 모음](using-the-hololens-emulator.md)

![열기 장치 포털 아이콘](images/emulator-deviceportal.png) **장치 포털 열기**: 에뮬레이터에서 HoloLens OS용 Windows 디바이스 포털을 엽니다.  Windows Mixed Reality를 검색할 수 있습니다 "업데이트 및 보안" 다음 "개발자"에 대 한 설정 앱에서에 "를 사용 하 여 연결:" "사용 장치 포털" 섹션  IP 주소와 포트를 모두 확인 해야 합니다.

먼저 RestSimulationStreamSink 개체를 가져오는 RestSimulationStreamSink.Create 부르겠습니다. 이 대상 장치 또는 에뮬레이터는 http 연결을 통해 제어 됩니다. 명령을 전달 되며에서 처리 합니다 [Windows Device Portal](using-the-windows-device-portal.md) 장치 또는 에뮬레이터에서 실행 합니다. 개체를 만들려고 해야 4 개의 매개 변수는:
* 대상 장치의 IP 주소 Uri uri (예: "http://123.123.123.123"또는"http://123.123.123.123:50080")
* System.Net.NetworkCredential 자격 증명-사용자 이름/암호에 연결 합니다 [Windows Device Portal](using-the-windows-device-portal.md) 대상 장치 또는 에뮬레이터에서 합니다. 해당 로컬 주소를 통해 에뮬레이터에 연결 하는 경우 (예를 들어 168.*합니다.* . *)를 같은 PC에서 자격 증명을 모두 허용 됩니다.
* bool 기본-보통 우선 순위에서 낮은 우선 순위에 대해 false 마찬가지입니다. 일반적으로이 값을 설정 하려는 *true* 테스트를 제어할 수 있는 테스트 시나리오에 대 한 합니다.  에뮬레이터와 Windows Mixed Reality 시뮬레이션 우선 순위가 낮은 연결을 사용합니다.  테스트 연결을 낮은 우선 순위를 사용 하면 가장 최근에 설정 된 컨트롤에 연결 됩니다.
* System.Threading.CancellationToken 토큰-비동기 작업을 취소할 토큰입니다.

두 번째는 IPerceptionSimulationManager 만들게 됩니다. 시뮬레이션을 제어 하는 데 개체입니다. 이 비동기 메서드에서 수행도 해야 함을 note 합니다.

## <a name="control-the-simulated-human"></a>시뮬레이션 된 사람을 제어 합니다.

IPerceptionSimulationManager ISimulatedHuman 개체를 반환 하는 사람이 속성을 있습니다. 시뮬레이션 된 사람을 제어 하려면이 개체에 대 한 작업을 수행 합니다. 예를 들어 다음과 같은 가치를 제공해야 합니다.

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a>기본 샘플 C# 콘솔 응용 프로그램

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            Task.Run(async () =>
            {
                RestSimulationStreamSink sink = null;
                CancellationToken token = new System.Threading.CancellationToken();

                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("http://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }

                // Always close the sink to return control to the previous application.
                if (sink != null)
                {
                    await sink.Close(token);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();
        }
    }
}
```

## <a name="extended-sample-c-console-application"></a>샘플 확장 C# 콘솔 응용 프로그램

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            RestSimulationStreamSink sink = null;
            CancellationToken token = new System.Threading.CancellationToken();

            Task.Run(async () =>
            {
                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("http://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);

                    // Now, we'll simulate a sequence of actions.
                    // Sleeps in-between each action give time to the system
                    // to be able to properly react.
                    // This is just an example. A proper automated test should verify
                    // that the app has behaved correctly
                    // before proceeding to the next step, instead of using Sleeps.

                    // Activate the right hand
                    manager.Human.RightHand.Activated = true;

                    // Simulate Bloom gesture, which should cause Shell to disappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... this time, Shell should reappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate a Head rotation down around the X axis
                    // This should cause gaze to aim about the center of the screen
                    manager.Human.Head.Rotate(new Rotation3(0.04f, 0.0f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a finger press & release
                    // Should cause a tap on the center tile, thus launching it
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate a second finger press & release
                    // Should activate the app that was launched when the center tile was clicked
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(5000);

                    // Simulate a Head rotation towards the upper right corner
                    manager.Human.Head.Rotate(new Rotation3(-0.14f, 0.17f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a third finger press & release
                    // Should press the Remove button on the app
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... bringing the Shell back once more
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();

            // Always close the sink to return control to the previous application.
            if (sink != null)
            {
                sink.Close(token);
            }
        }
    }
}
```

## <a name="note-on-6-dof-controllers"></a>6-DOF 컨트롤러에서 note

모든 속성 시뮬레이션된 6 DOF 컨트롤러에서 메서드를 호출 하기 전에 컨트롤러를 활성화 해야 합니다.  이렇게 하지 않으면 예외가 발생 합니다.  Windows 10부터 2019을 업데이트할 수 있습니다, 그리고 시뮬레이션 된 6 DOF 컨트롤러를 설치 하 고 SimulatedSixDofControllerStatus.Active ISimulatedSixDofController 개체의 Status 속성을 설정 하 여 활성화할 수 있습니다.
Windows 10 년 10 월 2018에서에서 업데이트 하 고 이전에 개별적으로 먼저 설치 해야 시뮬레이션된 6 DOF 컨트롤러 \Windows\System32 폴더에 있는 PerceptionSimulationDevice 도구를 호출 합니다.  이 도구의 사용은 다음과 같습니다.


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

예를 들면 다음과 같습니다.

```
    PerceptionSimulationDevice.exe i 6dof 1
```

지원 되는 동작은 다음과 같습니다.
* i = install
* q = query
* r = remove

지원 되는 인스턴스는 됩니다.
* 1 = 왼쪽된 6 DOF 컨트롤러
* 2 = 오른쪽 6 DOF 컨트롤러

프로세스의 종료 코드는 (0 값을 반환 하는 데 사용) 하는 성공 또는 실패 (0이 아닌 반환 값) 나타냅니다.  'Q' 작업을 사용 하 여 쿼리는 컨트롤러를 설치 하는 여부를 반환 값 영 (0) 컨트롤러를 아직 설치 하지 않은 경우 또는 됩니다 하나 (1)는 컨트롤러를 설치 하는 경우.

Windows 컨트롤러를 제거 하는 경우 10 년 10 월 2018 업데이트 또는 이전에 해제 API를 통해 먼저 다음 도구를 호출 하 PerceptionSimulationDevice 해당 상태를 설정 합니다.

이 도구는 관리자 권한으로 실행 해야 하는 참고 합니다.




## <a name="api-reference"></a>API 참조

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a>Microsoft.PerceptionSimulation.SimulatedDeviceType

시뮬레이션 된 장치 종류를 설명합니다.

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**

PerceptionSimulationManager에 대 한 기본 장치를 가상의 참조

### <a name="microsoftperceptionsimulationheadtrackermode"></a>Microsoft.PerceptionSimulation.HeadTrackerMode

헤드 추적기 모드를 설명합니다.

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**

기본 헤드를 추적 합니다. 즉, 시스템 관리 모드 런타임 조건에 따라 최상의 헤드를 선택할 수 있습니다.

**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**

추적만 헤드 방향입니다. 즉, 추적된 위치를 신뢰할 수 있는 아닐 헤드 위치에 종속 된 일부 기능을 사용할 수 없습니다.

**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**

위치 헤드 추적 합니다. 즉, 추적 된 헤드 위치와 방향을 둘 다 신뢰할 수 있는

### <a name="microsoftperceptionsimulationsimulatedgesture"></a>Microsoft.PerceptionSimulation.SimulatedGesture

시뮬레이션 된 제스처를 설명합니다.

```
public enum SimulatedGesture
{
    None = 0,
    FingerPressed = 1,
    FingerReleased = 2,
    Home = 4,
    Max = Home
}
```

**Microsoft.PerceptionSimulation.SimulatedGesture.None**

없는 제스처를 나타내는 데 센티널 값입니다.

**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**

손가락 제스처를 눌렀습니다.

**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**

손가락 제스처를 해제 합니다.

**Microsoft.PerceptionSimulation.SimulatedGesture.Home**

홈/시스템 제스처입니다.

**Microsoft.PerceptionSimulation.SimulatedGesture.Max**

최대 유효 제스처입니다.

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a>Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus

시뮬레이션 된 6 DOF 컨트롤러의 가능한 상태입니다.

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**

6-DOF 컨트롤러 꺼져 있습니다.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**

6-DOF 컨트롤러 켜져 있고 추적 합니다.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**

6-DOF 컨트롤러 켜져 있지만 추적할 수 없습니다.

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a>Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton

시뮬레이션 된 6 DOF 컨트롤러에서 지원 되는 단추입니다.

```
public enum SimulatedSixDofControllerButton
{
    None = 0,
    Home = 1,
    Menu = 2,
    Grip = 4,
    TouchpadPress = 8,
    Select = 16,
    TouchpadTouch = 32,
    Thumbstick = 64,
    Max = Thumbstick
}
```

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**

아니요 단추를 나타내는 데 센티널 값입니다.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**

홈 단추를 눌렀습니다.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**

메뉴 단추가 눌러져 있습니다.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**

그립 단추가 눌러져 있습니다.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**

터치 패드 눌러져 있습니다.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**

선택 단추가 눌러져 있습니다.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**

터치 패드 검사가 수행 됩니다.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**

스틱은 눌러져 있습니다.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**

최대 유효 단추입니다.


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a>Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState

시뮬레이션 된 명사 보정 상태

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**

눈 보정을 사용할 수 없는 경우

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**

눈 보정 되었습니다.  이것은 기본값입니다.

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**

눈을 보정 되는 합니다.

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**

눈 위치를 조정 해야 합니다.

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a>Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy

추적의 정확도 손 모양 아이콘이의 연결입니다.

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**

연결점 추적 되지 않습니다.

**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**

공동 위치 유추 됩니다.

**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**

연결점 추적 완벽 하 게 됩니다.

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a>Microsoft.PerceptionSimulation.SimulatedHandPose

추적의 정확도 손 모양 아이콘이의 연결입니다.

```
public enum SimulatedHandPose
{
    Closed = 0,
    Open = 1,
    Point = 2,
    Pinch = 3,
    Max = Pinch
}
```

**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**

손 모양 아이콘이 손가락이 음 닫힌된 포즈를 반영 하도록 구성 됩니다.

**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**

손 모양 아이콘이 손가락이 음을 열고 자세를 반영 하도록 구성 됩니다.

**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**

손 모양 아이콘이 손가락이 음 포인팅 포즈를 반영 하도록 구성 됩니다.

**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**

손 모양 아이콘이 손가락이 음 pinching 포즈를 반영 하도록 구성 됩니다.

**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**

SimulatedHandPose에 대 한 최대 유효 값입니다.


### <a name="microsoftperceptionsimulationplaybackstate"></a>Microsoft.PerceptionSimulation.PlaybackState

재생 하는 상태를 설명합니다.

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

**Microsoft.PerceptionSimulation.PlaybackState.Stopped**

녹음/녹화 중지 되 고 재생을 위해 준비 중인 합니다.

**Microsoft.PerceptionSimulation.PlaybackState.Playing**

현재 녹음/녹화 재생 합니다.

**Microsoft.PerceptionSimulation.PlaybackState.Paused**

녹음/녹화 현재 일시 중지 됩니다.

**Microsoft.PerceptionSimulation.PlaybackState.End**

녹음/녹화 끝에 도달 했습니다.

### <a name="microsoftperceptionsimulationvector3"></a>Microsoft.PerceptionSimulation.Vector3

점 또는 3D 공간에서 벡터를 설명 하는 3 개 구성 요소가 벡터를 설명 합니다.

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

**Microsoft.PerceptionSimulation.Vector3.X**

벡터의 X 구성 요소입니다.

**Microsoft.PerceptionSimulation.Vector3.Y**

벡터의 Y 구성 요소입니다.

**Microsoft.PerceptionSimulation.Vector3.Z**

벡터의 Z 구성 요소입니다.

**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**

새 Vector3를 생성 합니다.

매개 변수
* x 벡터의-x 구성 요소입니다.
* y 벡터의-y 구성 요소입니다.
* z 벡터의-z 구성 요소입니다.

### <a name="microsoftperceptionsimulationrotation3"></a>Microsoft.PerceptionSimulation.Rotation3

3 개 구성 요소가 회전을 설명합니다.

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

**Microsoft.PerceptionSimulation.Rotation3.Pitch**

회전의 피치 구성 요소 X 축을 중심으로 축소 합니다.

**Microsoft.PerceptionSimulation.Rotation3.Yaw**

Y 축 중심 오른쪽 회전 요 구성 요소입니다.

**Microsoft.PerceptionSimulation.Rotation3.Roll**

Z 축 중심 오른쪽 회전의 롤포워드 구성 요소입니다.

**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**

새 Rotation3를 생성 합니다.

매개 변수
* 피치-피치 구성 요소를 회전 합니다.
* 요-요 구성 요소를 회전 합니다.
* 롤포워드-롤포워드 구성 요소를 회전 합니다.

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a>Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration

시뮬레이션된 손 모양에 대 한 공동 구성을 설명합니다.

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**

연결점의 위치입니다.

**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**

연결점의 회전입니다.

**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**

추적의 정확도 연결점입니다.


### <a name="microsoftperceptionsimulationfrustum"></a>Microsoft.PerceptionSimulation.Frustum

보기 꼭지점이 절 두 체를, 카메라에서 일반적으로 사용 하는 설명 합니다.

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

**Microsoft.PerceptionSimulation.Frustum.Near**

하면 프러스텀에 포함 된 최소 거리입니다.

**Microsoft.PerceptionSimulation.Frustum.Far**

하면 프러스텀에 포함 된 최대 거리입니다.

**Microsoft.PerceptionSimulation.Frustum.FieldOfView**

가로 보기의 필드 (PI 보다 작음) 라디안에서 하면 프러스텀입니다.

**Microsoft.PerceptionSimulation.Frustum.AspectRatio**

가로 뷰 필드를 세로 보기 필드의 비율입니다.

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a>Microsoft.PerceptionSimulation.IPerceptionSimulationManager

장치를 제어 하는 데 패킷을 생성 하는 것에 대 한 루트입니다.

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**

시뮬레이션 된 사람 및 시뮬레이션된 세계를 해석 하는 시뮬레이션 된 장치 개체를 검색 합니다.

**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**

시뮬레이션 된 사람을 제어 하는 개체를 검색 합니다.

**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**

시뮬레이션을 기본 상태로 다시 설정합니다.

### <a name="microsoftperceptionsimulationisimulateddevice"></a>Microsoft.PerceptionSimulation.ISimulatedDevice

시뮬레이션 된 전 세계 및 시뮬레이션 된 사람을 해석 하는 장치를 설명 하는 인터페이스

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**

시뮬레이션된 된 장치에서 Head Tracker를 검색 합니다.

**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**

시뮬레이션된 된 장치에서 직접 Tracker를 검색 합니다.

**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**

제공 된 장치 유형과 일치 하도록 시뮬레이션 된 장치의 속성을 설정 합니다.

매개 변수
* 입력-시뮬레이션 된 장치의 새 유형

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a>Microsoft.PerceptionSimulation.ISimulatedHeadTracker

시뮬레이션 된 장치를 시뮬레이션 된 사람이의 머리를 추적 하는 부분을 설명 하는 인터페이스입니다.

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**

검색 하 고 현재 헤드 추적기 모드를 설정 합니다.

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a>Microsoft.PerceptionSimulation.ISimulatedHandTracker

시뮬레이션 된 장치를 시뮬레이션 된 사람을 추적 하는 부분을 설명 하는 인터페이스

```
public interface ISimulatedHandTracker
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    float Pitch { get; set; }
    bool FrustumIgnored { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    Frustum Frustum { get; set; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**

미터 단위의 전 세계를 통해 관련 노드의 위치를 검색 합니다.

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**

검색 하 고 헤드의 가운데를 기준으로 시뮬레이션 된 직접 추적기의 위치를 설정 합니다.

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**

검색 하 고 시뮬레이션 된 직접 추적기의 아래쪽 피치를 설정 합니다.

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**

검색 및 시뮬레이션 된 직접 추적기의 하면 프러스텀을 무시할지 여부를 설정 합니다. 무시 된 경우 두 게 항상 표시 됩니다. 없습니다 (기본값)를 무시 하는 경우는 표시 직접 추적기의 하면 프러스텀 있는 경우입니다.

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**

검색 및 실습 시뮬레이션된 직접 추적기에 표시 되는지 확인 하는 데 꼭지점이 절 두 체 속성을 설정 합니다.

### <a name="microsoftperceptionsimulationisimulatedhuman"></a>Microsoft.PerceptionSimulation.ISimulatedHuman

시뮬레이션 된 사람을 제어 하기 위한 상위 수준 인터페이스입니다.

```
public interface ISimulatedHuman 
{
    Vector3 WorldPosition { get; set; }
    float Direction { get; set; }
    float Height { get; set; }
    ISimulatedHand LeftHand { get; }
    ISimulatedHand RightHand { get; }
    ISimulatedHead Head { get; }
    void Move(Vector3 translation);
    void Rotate(float radians);
}
```

**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**

검색 하 고 전 세계를 미터 단위로 통해 관련 노드의 위치를 설정 합니다. 위치는 사람이 feet 중앙 지점에 해당합니다.

**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**

검색 및 전 세계의 방향을 시뮬레이션 된 얼굴을 설정 합니다. 음의 Z 축을 0 라디안 직면 합니다. Y 축에 대 한 양의 라디안을 시계 방향으로 회전 합니다.

**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**

검색 하 고 미터에서 시뮬레이션 된 사람이의 높이 설정 합니다.

**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**

시뮬레이션 된 사람이의 왼쪽을 검색 합니다.

**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**

시뮬레이션 된 사람이의 오른쪽 위를 검색 합니다.

**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**

시뮬레이션 된 사람이의 머리를 검색 합니다.

**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**

시뮬레이션 된 사람이 미터 단위로, 현재 위치를 기준으로 이동 합니다.

매개 변수
* 번역 번역에 현재 위치를 기준으로 이동 합니다.

**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**

Y 축에 대 한 시계 방향으로 현재 방향 기준으로 시뮬레이션 된 사람이 회전

매개 변수
* 라디안으로-Y 축을 중심으로 회전할 양입니다.

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a>Microsoft.PerceptionSimulation.ISimulatedHuman2

ISimulatedHuman2 ISimulatedHuman 캐스팅 하 여 추가 속성을 사용할 수

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**

왼쪽된 6 DOF 컨트롤러를 검색 합니다.

**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**

오른쪽 6 DOF 컨트롤러를 검색 합니다.


### <a name="microsoftperceptionsimulationisimulatedhand"></a>Microsoft.PerceptionSimulation.ISimulatedHand

시뮬레이션 된 사용자의 직접을 설명 하는 인터페이스

```
public interface ISimulatedHand
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    bool Activated { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    bool Visible { [return: MarshalAs(UnmanagedType.Bool)] get; }
    void EnsureVisible();
    void Move(Vector3 translation);
    void PerformGesture(SimulatedGesture gesture);
}
```

**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**

미터 단위의 전 세계를 통해 관련 노드의 위치를 검색 합니다.

**Microsoft.PerceptionSimulation.ISimulatedHand.Position**

검색 및 미터에서 사람을 기준으로 시뮬레이션 된 손 모양 아이콘이 위치를 설정 합니다.

**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**

검색 하 고 손 모양 아이콘이 현재 활성화 되어 있는지 여부를 설정 합니다.

**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**

손 모양 아이콘이 (즉, 인지는 HandTracker에서 검색할 수는 위치) SimulatedDevice에 현재 표시 되는지 여부를 검색 합니다.

**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**

SimulatedDevice를 볼 수 있도록 손 모양 아이콘이 이동 합니다.

**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**

미터 단위로, 현재 위치를 기준으로 시뮬레이션 된 손 모양 아이콘이 위치를 이동 합니다.

매개 변수
* 변환-시뮬레이션 된 손 모양 아이콘이 변환할 크기입니다.

**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**

시뮬레이션 된 손 모양 아이콘이 사용 하 여 제스처를 수행 합니다.  만 검색 됩니다 시스템 손 모양 아이콘이 사용 되는 경우.

매개 변수
* 제스처-제스처를 수행 합니다.

### <a name="microsoftperceptionsimulationisimulatedhand2"></a>Microsoft.PerceptionSimulation.ISimulatedHand2

ISimulatedHand ISimulatedHand2 캐스팅 하 여 추가 속성을 사용할 수 있습니다.
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**

검색 또는 시뮬레이션 된 손 모양 아이콘이의 회전 각도 설정 합니다.  양수 라디안 축을 찾을 때 시계 방향으로 회전 합니다.

### <a name="microsoftperceptionsimulationisimulatedhand3"></a>Microsoft.PerceptionSimulation.ISimulatedHand3

ISimulatedHand ISimulatedHand3 캐스팅 하 여 추가 속성을 사용할 수
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**

지정 된 연결점에 대 한 공동 구성을 가져옵니다.

**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**

지정 된 연결점에 대 한 공동 구성을 설정 합니다.

**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**

손 모양 아이콘이 애니메이션 효과를 주는 선택적 플래그를 사용 하 여 알려진된 포즈를 설정 합니다.  참고: 즉시 해당 최종 joint 구성을 반영 하는 음 바뀌지는지 않습니다 애니메이션 효과 적용 합니다.


### <a name="microsoftperceptionsimulationisimulatedhead"></a>Microsoft.PerceptionSimulation.ISimulatedHead

시뮬레이션 된 사람이의 머리를 설명 하는 인터페이스입니다.

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**

미터 단위의 전 세계를 통해 관련 노드의 위치를 검색 합니다.

**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**

시뮬레이션 된 헤드의 회전을 검색 합니다. 양수 라디안 축을 찾을 때 시계 방향으로 회전 합니다.

**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**

시뮬레이션 된 head의 지름을 검색 합니다. 이 값은 head의 center (회전 지점)를 확인 하려면 사용 합니다.

**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**

현재 회전의 기준으로 시뮬레이션 된 헤드를 회전 합니다. 양수 라디안 축을 찾을 때 시계 방향으로 회전 합니다.

매개 변수
* 회전-으로 회전할 양입니다.

### <a name="microsoftperceptionsimulationisimulatedhead2"></a>Microsoft.PerceptionSimulation.ISimulatedHead2

ISimulatedHead ISimulatedHead2 캐스팅 하 여 추가 속성을 사용할 수

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**

시뮬레이션 된 사람이의 시점을 검색 합니다.

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a>Microsoft.PerceptionSimulation.ISimulatedSixDofController

시뮬레이션 된 사용자와 연결 된 6 DOF 컨트롤러를 설명 하는 인터페이스입니다.

```
public interface ISimulatedSixDofController
{
    Vector3 WorldPosition { get; }
    SimulatedSixDofControllerStatus Status { get; set; }
    Vector3 Position { get; }
    Rotation3 Orientation { get; set; }
    void Move(Vector3 translation);
    void PressButton(SimulatedSixDofControllerButton button);
    void ReleaseButton(SimulatedSixDofControllerButton button);
    void GetTouchpadPosition(out float x, out float y);
    void SetTouchpadPosition(float x, float y);
}
```

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**

미터 단위의 전 세계를 통해 관련 노드의 위치를 검색 합니다.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**

검색 또는 컨트롤러의 현재 상태를 설정 합니다.  컨트롤러의 상태를 Off 이동, 회전 또는 키를 눌러 호출 전에 단추 성공할 이외의 값으로 설정 되어야 합니다.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**

검색 또는 미터에서 사람을 기준으로 시뮬레이션 된 컨트롤러의 위치를 설정 합니다.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**

검색 또는 시뮬레이션 된 컨트롤러의 방향을 설정 합니다.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**

시뮬레이션 된 컨트롤러의 현재 위치, 미터 단위에서를 기준으로 이동 합니다.

매개 변수
* 변환-시뮬레이션 된 컨트롤러를 변환할 크기입니다.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**

시뮬레이션 된 컨트롤러에서 단추를 누르십시오.  만 검색 됩니다 시스템에서 컨트롤러를 사용 하는 경우.

매개 변수
* 단추-단추를 누릅니다.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**

시뮬레이션 된 컨트롤러에서 단추를 놓습니다.  만 검색 됩니다 시스템에서 컨트롤러를 사용 하는 경우.

매개 변수
* 단추-해제 하려면 단추입니다.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**

시뮬레이션 된 컨트롤러의 터치 패드에 시뮬레이션 된 손가락의 위치를 가져옵니다.

매개 변수
* x 손가락의-가로 위치입니다.
* y 손가락의-세로 위치입니다.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**

시뮬레이션 된 컨트롤러의 터치 패드에 시뮬레이트된 손가락의 위치를 설정 합니다.

매개 변수
* x 손가락의-가로 위치입니다.
* y 손가락의-세로 위치입니다.

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a>Microsoft.PerceptionSimulation.ISimulatedSixDofController2

추가 속성 및 메서드를 사용할 수 있습니다는 ISimulatedSixDofController ISimulatedSixDofController2 캐스팅 합니다.

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**

시뮬레이션 된 컨트롤러에서 시뮬레이션 된 스틱의 위치를 가져옵니다.

매개 변수
* x 스틱의-가로 위치입니다.
* y 스틱의-세로 위치입니다.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**

시뮬레이션 된 컨트롤러에서 시뮬레이션 된 엄지 스틱의 위치를 설정 합니다.

매개 변수
* x 스틱의-가로 위치입니다.
* y 스틱의-세로 위치입니다.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**

검색 또는 시뮬레이션 된 컨트롤러의 배터리 수준을 설정 합니다.  값은 0.0 보다 커야 100.0 보다 작거나 같음.


### <a name="microsoftperceptionsimulationisimulatedeyes"></a>Microsoft.PerceptionSimulation.ISimulatedEyes

시뮬레이션 된 사람이의 시점을 설명 하는 인터페이스입니다.

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**

시뮬레이션 된 명사 회전을 검색 합니다. 양수 라디안 축을 찾을 때 시계 방향으로 회전 합니다.

**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**

현재 회전의 기준으로 시뮬레이션 된 눈을 회전 합니다. 양수 라디안 축을 찾을 때 시계 방향으로 회전 합니다.

매개 변수
* 회전-으로 회전할 양입니다.

**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**

시뮬레이션 된 명사 보정 상태를 가져오거나 검색 합니다.

**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**

미터 단위의 전 세계를 통해 관련 노드의 위치를 검색 합니다.


### <a name="microsoftperceptionsimulationisimulationrecording"></a>Microsoft.PerceptionSimulation.ISimulationRecording

재생에 대 한 로드를 기록 하는 단일 상호 작용 하기 위한 인터페이스입니다.

```
public interface ISimulationRecording
{
    StreamDataTypes DataTypes { get; }
    PlaybackState State { get; }
    void Play();
    void Pause();
    void Seek(UInt64 ticks);
    void Stop();
};
```

**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**

기록에 대 한 데이터 형식의 목록을 검색합니다.

**Microsoft.PerceptionSimulation.ISimulationRecording.State**

기록의 현재 상태를 검색합니다.

**Microsoft.PerceptionSimulation.ISimulationRecording.Play**

재생을 시작 합니다. 재생을 일시 중지 된 위치에서 다시 시작 됩니다 기록을 일시 중지 하는 경우 중지 하는 경우에 재생 시작 부분에서 시작 됩니다. 이미 재생 하는 경우이 호출은 무시 됩니다.

**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**

현재 위치에 있는 재생 일시 중지합니다. 녹음/녹화 중지 되 면 호출 무시 됩니다.

**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**

검색 기록에 지정된 된 시간 (초부터 100 나노초 간격) 및 해당 위치에서 일시 중지 합니다. 시간 기록의 끝 이면 마지막 프레임에서 일시 중지 됩니다.

매개 변수
* 틱-검색 하려는 경우.

**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**

재생을 중지 하 고 시작 부분에 위치를 다시 설정 합니다.

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a>Microsoft.PerceptionSimulation.ISimulationRecordingCallback

재생 중 상태 변경 내용을 수신 하는 것에 대 한 인터페이스입니다.

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**

ISimulationRecording 재생 상태가 변경 되 면 호출 됩니다.

매개 변수
* newState-기록의 새 상태입니다.

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a>Microsoft.PerceptionSimulation.PerceptionSimulationManager

Perception 시뮬레이션 개체를 만들기 위한 루트 개체입니다.

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**

시뮬레이션 된 패킷을 생성 하 고 제공 된 싱크에서에 게 배달에 대 한 개체를 만듭니다.

매개 변수
* 싱크-생성 된 모든 패킷의 받을 싱크입니다.

반환 값

만든된 관리자입니다.

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**

모든 받은 패킷에 지정된 된 경로에 있는 파일에 저장 하는 싱크를 만듭니다.

매개 변수
* 경로-만들려는 파일의 경로입니다.

반환 값

만든된 싱크입니다.

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**

지정된 된 파일에서 녹음/녹화를 로드 합니다.

매개 변수
* 경로-로드할 파일의 경로입니다.
* 팩터리-필요한 경우에 ISimulationStreamSink 만들기에 대 한 기록에서 사용 하는 팩터리입니다.

반환 값

로드 된 기록 합니다.

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording (System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory, Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**

지정된 된 파일에서 녹음/녹화를 로드 합니다.

매개 변수
* 경로-로드할 파일의 경로입니다.
* 팩터리-필요한 경우에 ISimulationStreamSink 만들기에 대 한 기록에서 사용 하는 팩터리입니다.
* 콜백-수신 하는 콜백을 regrading 기록의 상태 업데이트 합니다.

반환 값

로드 된 기록 합니다.

### <a name="microsoftperceptionsimulationstreamdatatypes"></a>Microsoft.PerceptionSimulation.StreamDataTypes

다양 한 유형의 스트림 데이터를 설명합니다.

```
public enum StreamDataTypes
{
    None = 0x00,
    Head = 0x01,
    Hands = 0x02,
    SpatialMapping = 0x08,
    Calibration = 0x10,
    Environment = 0x20,
    All = None | Head | Hands | SpatialMapping | Calibration | Environment
}
```

**Microsoft.PerceptionSimulation.StreamDataTypes.None**

스트림 데이터 형식이 없습니다를 나타내는 데 센티널 값입니다.

**Microsoft.PerceptionSimulation.StreamDataTypes.Head**

위치 및 헤드의 방향에 대 한 데이터의 Stream입니다.

**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**

손으로 제스처와 위치에 대 한 데이터의 Stream입니다.

**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**

공간 매핑의 환경에 대 한 데이터의 Stream입니다.

**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**

장치의 보정에 대 한 데이터의 Stream입니다. 보정 패킷 시스템 원격 모드에만 허용 됩니다.

**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**

장치 환경에 대 한 데이터의 Stream입니다.

**Microsoft.PerceptionSimulation.StreamDataTypes.All**

모든 기록 된 데이터 형식을 나타내는 데 센티널 값입니다.

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a>Microsoft.PerceptionSimulation.ISimulationStreamSink

시뮬레이션 스트림에서 데이터 패킷을 수신 하는 개체입니다.

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**

내부적으로 형식화 된 및 버전 관리 된 단일 패킷을 받습니다.

매개 변수
* length-패킷 길이입니다.
* 패킷 패킷의 데이터입니다.

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a>Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory

ISimulationStreamSink 만들어지는 개체입니다.

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**

ISimulationStreamSink의 단일 인스턴스를 만듭니다.

반환 값

만든된 싱크입니다.
