---
title: 인식 시뮬레이션
description: 인식 시뮬레이션 라이브러리를 사용 하 여 몰입 형 응용 프로그램의 시뮬레이션 된 입력을 자동화 하는 방법에 대 한 지침
author: pbarnettms
ms.author: pbarnett
ms.date: 04/26/2019
ms.topic: article
keywords: HoloLens, 시뮬레이션, 테스트
ms.openlocfilehash: 8152181bdbe8c83d2b706b34f1f2fb5d51f4c880
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414527"
---
# <a name="perception-simulation"></a>인식 시뮬레이션

앱에 대 한 자동화 된 테스트를 빌드 하시 겠어요? 테스트를 구성 요소 수준 단위 테스트 이상으로 전환 하 고 응용 프로그램을 종단 간에 실행 하 시겠습니까? 인식 시뮬레이션은 원하는 것입니다. 인식 시뮬레이션 라이브러리는 테스트를 자동화할 수 있도록 사용자 및 세계 입력 데이터를 앱에 보냅니다. 예를 들어, 반복 가능한 특정 위치를 찾고 제스처를 수행 하거나 동작 컨트롤러를 사용 하 여 사용자의 입력을 시뮬레이션할 수 있습니다.

인식 시뮬레이션에서는 이와 같은 시뮬레이션 된 입력을 물리적 HoloLens, HoloLens 에뮬레이터 (첫 번째 gen), HoloLens 2 에뮬레이터 또는 혼합 현실 포털이 설치 된 PC에 보낼 수 있습니다. 인식 시뮬레이션은 혼합 현실 장치에서 라이브 센서를 우회 하 고 장치에서 실행 되는 응용 프로그램에 시뮬레이트된 입력을 보냅니다. 응용 프로그램은 항상 사용 하는 것과 동일한 Api를 통해 이러한 입력 이벤트를 수신 하 고, 실제 센서를 사용 하 여 실행 하는 것과 인식 시뮬레이션으로 실행 되는 것 인식 시뮬레이션은 hololens 에뮬레이터에서 HoloLens 가상 컴퓨터에 시뮬레이트된 입력을 보내기 위해 사용 하는 것과 동일한 기술입니다.

코드에서 시뮬레이션 사용을 시작 하려면 먼저 IPerceptionSimulationManager 개체를 만듭니다. 이 개체에서 위치, 손 모양 및 제스처를 포함 하 여 시뮬레이션 된 "인간"의 속성을 제어 하는 명령을 실행 하 고, 동작 컨트롤러를 사용 하도록 설정 하 고 조작할 수 있습니다.

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a>인식 시뮬레이션에 대 한 Visual Studio 프로젝트 설정
1. 개발 PC에 [HoloLens 에뮬레이터를 설치](install-the-tools.md) 합니다. 이 에뮬레이터는 인식 시뮬레이션에 사용할 라이브러리를 포함 합니다.
2. 새 Visual Studio C# 데스크톱 프로젝트를 만듭니다. 콘솔 프로젝트는 시작 하는 데 유용 합니다.
3. 프로젝트에 다음 이진 파일을 참조 (프로젝트 > 추가 > 참조 ...)로 추가 합니다. % ProgramFiles (x86)% \ microsoft xde\\(버전) (예: HoloLens 2 에뮬레이터의 경우 **% ProgramFiles (x86)% \ microsoft xde\\10.0.18362.0** )에서 찾을 수 있습니다.  (참고: 이진 파일은 HoloLens 2 에뮬레이터의 일부 이지만 바탕 화면에서 Windows Mixed Reality에도 작동 합니다.) 은. 인식 시뮬레이션에 대 한 PerceptionSimulationManager 관리 C# 래퍼입니다.
    b. PerceptionSimulationRest-HoloLens 또는 에뮬레이터에 웹 소켓 통신 채널을 설정 하기 위한 라이브러리입니다.
    c. SimulationStream-시뮬레이션에 대 한 공유 형식입니다.
4. 프로젝트 a에 이진 PerceptionSimulationManager 구현을 추가 합니다. 먼저 프로젝트에 이진으로 추가 합니다 (기존 항목 > 추가 >). 프로젝트 원본 폴더에 복사 하지 않도록 링크를 링크로 저장 합니다. ![PerceptionSimulationManager을 프로젝트에 링크](images/saveaslink.png) b로 추가 합니다. 그런 다음 빌드 시 출력 폴더에 복사 되었는지 확인 합니다. 이는 이진의 속성 시트에 있습니다. ![PerceptionSimulationManager를 출력 디렉터리에 복사 하도록 표시 합니다.](images/copyalways.png)
5. 활성 솔루션 플랫폼을 x 64로 설정 합니다.  (아직 없는 경우 Configuration Manager를 사용 하 여 x 64에 대 한 플랫폼 항목을 만듭니다.)

## <a name="creating-an-iperceptionsimulation-manager-object"></a>IPerceptionSimulation Manager 개체 만들기

시뮬레이션을 제어 하기 위해 IPerceptionSimulationManager 개체에서 검색 된 개체에 대 한 업데이트를 실행 합니다. 첫 번째 단계는 해당 개체를 가져와 대상 장치 또는 에뮬레이터에 연결 하는 것입니다. [도구 모음](using-the-hololens-emulator.md) 에서 장치 포털 단추를 클릭 하 여 에뮬레이터의 IP 주소를 가져올 수 있습니다.

![장치 포털 열기 아이콘](images/emulator-deviceportal.png) **장치 포털 열기**: 에뮬레이터에서 HoloLens OS용 Windows 디바이스 포털을 엽니다.  Windows Mixed Reality의 경우 "업데이트 & 보안" 아래의 설정 앱에서 "장치 포털 사용"의 "연결 사용:" 섹션에 있는 "개발자 용" 섹션에서 검색할 수 있습니다.  IP 주소와 포트를 모두 기록해 두어야 합니다.

먼저 RestSimulationStreamSink를 호출 하 여 RestSimulationStreamSink 개체를 가져옵니다. Http 연결을 제어 하는 대상 장치 또는 에뮬레이터입니다. 명령은 장치 또는 에뮬레이터에서 실행 되는 [Windows 장치 포털](using-the-windows-device-portal.md) 에 전달 되 고 처리 됩니다. 개체를 만드는 데 필요한 네 가지 매개 변수는 다음과 같습니다.
* Uri uri-대상 장치의 IP 주소 (예: "http://123.123.123.123" 또는 "http://123.123.123.123:50080")
* 시스템 .Net. NetworkCredential 자격 증명-대상 장치 또는 에뮬레이터의 [Windows 장치 포털](using-the-windows-device-portal.md) 에 연결 하기 위한 사용자 이름/암호입니다. 로컬 주소를 통해 에뮬레이터에 연결 하는 경우 (예:*168 ...* *) 같은 PC에서 모든 자격 증명이 허용 됩니다.
* bool normal-보통 우선 순위의 경우 True, 낮은 우선 순위의 경우 false 일반적으로 테스트 시나리오의 경우이를 *true* 로 설정 하 여 테스트를 제어할 수 있도록 합니다.  에뮬레이터 및 Windows Mixed Reality 시뮬레이션에서는 낮은 우선 순위의 연결을 사용 합니다.  또한 테스트에서 낮은 우선 순위의 연결을 사용 하는 경우 가장 최근에 설정 된 연결이 제어 됩니다.
* CancellationToken 토큰-비동기 작업을 취소 하는 토큰입니다.

두 번째는 IPerceptionSimulationManager를 만듭니다. 시뮬레이션을 제어 하는 데 사용 하는 개체입니다. 비동기 메서드에서도이 작업을 수행 해야 합니다.

## <a name="control-the-simulated-human"></a>시뮬레이션 된 사용자 제어

IPerceptionSimulationManager에는 ISimulatedHuman 개체를 반환 하는 인적 속성이 있습니다. 시뮬레이션 된 사용자를 제어 하려면이 개체에 대 한 작업을 수행 합니다. 이는 아래와 같이 함수의 반환값을 데이터 프레임으로 바로 변환하는 데 사용할 수 있음을 나타냅니다.

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

## <a name="extended-sample-c-console-application"></a>확장 된 C# 샘플 콘솔 응용 프로그램

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

## <a name="note-on-6-dof-controllers"></a>6-DOF 컨트롤러에 대 한 참고 사항

시뮬레이션 된 6 DOF controller의 메서드에 대 한 속성을 호출 하기 전에 컨트롤러를 활성화 해야 합니다.  이렇게 하지 않으면 예외가 발생 합니다.  Windows 10 2019 년 5 월 업데이트부터 ISimulatedSixDofController 개체의 Status 속성을 SimulatedSixDofControllerStatus로 설정 하 여 시뮬레이션 된 6 DOF 컨트롤러를 설치 하 고 활성화할 수 있습니다.
Windows 10 10 월 2018 업데이트 및 그 이전 버전에서는 \Windows\System32 폴더에 있는 PerceptionSimulationDevice 도구를 호출 하 여 시뮬레이션 된 6-DOF 컨트롤러를 별도로 설치 해야 합니다.  이 도구의 사용법은 다음과 같습니다.


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

예를 들면 다음과 같습니다.

```
    PerceptionSimulationDevice.exe i 6dof 1
```

지원 되는 작업은 다음과 같습니다.
* i = 설치
* q = 쿼리
* r = 제거

지원 되는 인스턴스는 다음과 같습니다.
* 1 = 왼쪽 6-DOF controller
* 2 = 오른쪽 6-DOF controller

프로세스의 종료 코드는 성공 (0이 아닌 반환 값) 또는 실패 (0이 아닌 반환 값)를 표시 합니다.  ' Q ' 작업을 사용 하 여 컨트롤러가 설치 되어 있는지 여부를 쿼리하려면 컨트롤러를 아직 설치 하지 않은 경우 반환 값은 0이 고, 컨트롤러가 설치 된 경우에는 (1)입니다.

Windows 10 10 월 2018 업데이트 또는 그 이전 버전에서 컨트롤러를 제거 하는 경우 먼저 API를 통해 상태를 Off로 설정한 다음 PerceptionSimulationDevice 도구를 호출 합니다.

이 도구는 관리자 권한으로 실행 해야 합니다.




## <a name="api-reference"></a>API 참조

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a>PerceptionSimulation. SimulatedDeviceType

시뮬레이션 된 장치 유형을 설명 합니다.

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

**PerceptionSimulation. SimulatedDeviceType**

PerceptionSimulationManager에 대 한 기본값 인 가상의 참조 장치

### <a name="microsoftperceptionsimulationheadtrackermode"></a>PerceptionSimulation Ermode

헤드 추적 장치 모드를 설명 합니다.

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

**PerceptionSimulation Ermode. 기본값**

기본 헤드 추적입니다. 즉, 시스템에서 런타임 조건에 따라 가장 적합 한 헤드 추적 모드를 선택할 수 있습니다.

**PerceptionSimulation입니다. 방향**

방향 전용 헤드 추적입니다. 즉, 추적 된 위치는 신뢰할 수 없으며 헤드 위치에 종속 된 일부 기능을 사용 하지 못할 수 있습니다.

**PerceptionSimulation입니다. 위치**

위치 헤드 추적. 즉, 추적 된 헤드 위치와 방향이 모두 안정적 임을 의미 합니다.

### <a name="microsoftperceptionsimulationsimulatedgesture"></a>PerceptionSimulation. SimulatedGesture

시뮬레이션 된 제스처를 설명 합니다.

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

**PerceptionSimulation. SimulatedGesture**

제스처를 표시 하는 데 사용 되는 센티널 값입니다.

**PerceptionSimulation. SimulatedGesture. FingerPressed**

손가락 누름 제스처입니다.

**PerceptionSimulation. SimulatedGesture. FingerReleased**

손가락이 해제 된 제스처입니다.

**PerceptionSimulation. SimulatedGesture**

홈/시스템 제스처입니다.

**PerceptionSimulation. SimulatedGesture**

최대 유효 제스처입니다.

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a>PerceptionSimulation. SimulatedSixDofControllerStatus

시뮬레이션 된 6 DOF controller의 가능한 상태입니다.

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

**PerceptionSimulation. SimulatedSixDofControllerStatus**

6-DOF 컨트롤러가 꺼져 있습니다.

**PerceptionSimulation. SimulatedSixDofControllerStatus**

6-DOF 컨트롤러를 켜고 추적 합니다.

**PerceptionSimulation. SimulatedSixDofControllerStatus**

6-DOF 컨트롤러가 켜져 있지만 추적할 수 없습니다.

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a>PerceptionSimulation. SimulatedSixDofControllerButton

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

**PerceptionSimulation. SimulatedSixDofControllerButton**

단추를 표시 하지 않는 데 사용 되는 센티널 값입니다.

**PerceptionSimulation. SimulatedSixDofControllerButton**

홈 단추를 눌렀습니다.

**PerceptionSimulation. SimulatedSixDofControllerButton**

메뉴 단추가 눌러져 있습니다.

**PerceptionSimulation. SimulatedSixDofControllerButton**

그립 단추가 눌러져 있습니다.

**PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadPress**

터치 패드가 눌러져 있습니다.

**PerceptionSimulation. SimulatedSixDofControllerButton**

선택 단추가 눌러져 있습니다.

**PerceptionSimulation. SimulatedSixDofControllerButton. TouchpadTouch**

터치 패드가 수행 됩니다.

**PerceptionSimulation. SimulatedSixDofControllerButton**

엄지 스틱이 눌러져 있습니다.

**PerceptionSimulation. SimulatedSixDofControllerButton**

최대 유효 단추입니다.


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a>PerceptionSimulation. SimulatedEyesCalibrationState

시뮬레이션 된 눈동자의 보정 상태

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

**PerceptionSimulation. SimulatedEyesCalibrationState**

눈동자 보정을 사용할 수 없습니다.

**PerceptionSimulation. SimulatedEyesCalibrationState**

눈이 보정 되었습니다.  이것은 기본값입니다.

**PerceptionSimulation. SimulatedEyesCalibrationState**

눈이 보정 되 고 있습니다.

**PerceptionSimulation. SimulatedEyesCalibrationState. UserCalibrationNeeded**

눈동자를 보정 해야 합니다.

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a>PerceptionSimulation. SimulatedHandJointTrackingAccuracy

바늘의 조인트 추적 정확도입니다.

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

**PerceptionSimulation. SimulatedHandJointTrackingAccuracy**

조인트는 추적 되지 않습니다.

**PerceptionSimulation. SimulatedHandJointTrackingAccuracy**

조인트 위치가 유추 됩니다.

**PerceptionSimulation. SimulatedHandJointTrackingAccuracy**

조인트는 완전히 추적 됩니다.

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a>PerceptionSimulation. SimulatedHandPose

바늘의 조인트 추적 정확도입니다.

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

**PerceptionSimulation. SimulatedHandPose**

손 모양 손가락 조인트는 닫힌 포즈를 반영 하도록 구성 됩니다.

**PerceptionSimulation. SimulatedHandPose**

손 모양 손가락 조인트는 열린 포즈를 반영 하도록 구성 됩니다.

**PerceptionSimulation. SimulatedHandPose**

손 모양 손가락 조인트는 포인팅 포즈를 반영 하도록 구성 됩니다.

**PerceptionSimulation. SimulatedHandPose**

손 모양 손가락 조인트는 집기 포즈를 반영 하도록 구성 됩니다.

**PerceptionSimulation. SimulatedHandPose**

SimulatedHandPose에 대 한 최대 유효 값입니다.


### <a name="microsoftperceptionsimulationplaybackstate"></a>PerceptionSimulation.

재생 상태를 설명 합니다.

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

**PerceptionSimulation. 중지 됨**

기록이 현재 중지 되었고 재생할 준비가 되었습니다.

**PerceptionSimulation. 재생 중**

기록이 현재 재생 중입니다.

**PerceptionSimulation. 일시 중지 됨**

기록이 현재 일시 중지 되었습니다.

**PerceptionSimulation. 종료**

기록이 끝에 도달 했습니다.

### <a name="microsoftperceptionsimulationvector3"></a>PerceptionSimulation. Vector3

3D 공간에서 점이 나 벡터를 설명할 수 있는 3 개의 구성 요소 벡터에 대해 설명 합니다.

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

**PerceptionSimulation. Vector3**

벡터의 X 구성 요소입니다.

**PerceptionSimulation. Vector3**

벡터의 Y 구성 요소입니다.

**PerceptionSimulation. Vector3**

벡터의 Z 구성 요소입니다.

**PerceptionSimulation (System.web, system.web, System.web) (#ctor Vector3)**

새 Vector3를 생성 합니다.

매개 변수
* x-벡터의 x 구성 요소입니다.
* y-벡터의 y 구성 요소입니다.
* z-벡터의 z 구성 요소입니다.

### <a name="microsoftperceptionsimulationrotation3"></a>PerceptionSimulation. Rotation3

3 개의 구성 요소 회전을 설명 합니다.

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

**PerceptionSimulation. Rotation3**

X 축을 중심으로 하는 회전의 피치 구성 요소입니다.

**PerceptionSimulation. Rotation3. 요**

Y 축을 중심으로 하는 회전의 요 구성 요소입니다.

**PerceptionSimulation. Rotation3**

Z 축을 중심으로 하는 회전의 롤 구성 요소입니다.

**PerceptionSimulation (System.web, system.web, System.web) (#ctor Rotation3)**

새 Rotation3를 생성 합니다.

매개 변수
* 피치-회전의 피치 구성 요소입니다.
* 요-회전의 요 구성 요소입니다.
* roll-회전의 롤오버 구성 요소입니다.

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a>PerceptionSimulation. SimulatedHandJointConfiguration

시뮬레이션 된 손으로의 조인트 구성에 대해 설명 합니다.

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

**PerceptionSimulation. SimulatedHandJointConfiguration**

조인트의 위치입니다.

**PerceptionSimulation. SimulatedHandJointConfiguration**

조인트의 회전입니다.

**PerceptionSimulation. SimulatedHandJointConfiguration**

조인트의 추적 정확도입니다.


### <a name="microsoftperceptionsimulationfrustum"></a>PerceptionSimulation

카메라에서 일반적으로 사용 되는 것과 같은 뷰를 설명 합니다.

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

**PerceptionSimulation. Near**

가 수에 포함 된 최소 거리입니다.

**PerceptionSimulation.**

가 수에 포함 된 최대 거리입니다.

**PerceptionSimulation. FieldOfView**

두 부분을 뺀 값의 가로 필드 (PI 보다 작음)입니다.

**PerceptionSimulation. AspectRatio**

뷰의 가로 필드와 세로 필드의 비율입니다.

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a>PerceptionSimulation. IPerceptionSimulationManager

장치를 제어 하는 데 사용 되는 패킷을 생성 하는 루트입니다.

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

**PerceptionSimulation. IPerceptionSimulationManager**

시뮬레이션 된 사용자 및 시뮬레이션 된 전 세계를 해석 하는 시뮬레이션 된 장치 개체를 검색 합니다.

**PerceptionSimulation. IPerceptionSimulationManager**

시뮬레이션 된 사용자를 제어 하는 개체를 검색 합니다.

**PerceptionSimulation. IPerceptionSimulationManager**

시뮬레이션을 기본 상태로 다시 설정 합니다.

### <a name="microsoftperceptionsimulationisimulateddevice"></a>PerceptionSimulation. ISimulatedDevice

시뮬레이션 된 사람들과 시뮬레이션 된 사용자를 해석 하는 장치를 설명 하는 인터페이스

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

**PerceptionSimulation. ISimulatedDevice**

시뮬레이션 된 장치에서 헤드 추적 장치를 검색 합니다.

**PerceptionSimulation. ISimulatedDevice**

시뮬레이션 된 장치에서 손 트래커를 검색 합니다.

**PerceptionSimulation ISimulatedDevice. SetSimulatedDeviceType (PerceptionSimulation)**

제공 된 장치 유형과 일치 하도록 시뮬레이트된 장치의 속성을 설정 합니다.

매개 변수
* 유형-시뮬레이션 된 장치의 새 유형

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a>PerceptionSimulation. ISimulatedHeadTracker

시뮬레이션 된 사람의 헤드를 추적 하는 시뮬레이션 된 장치의 부분을 설명 하는 인터페이스입니다.

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

**PerceptionSimulation. ISimulatedHeadTracker.**

현재 헤드 추적 모드를 검색 하 고 설정 합니다.

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a>PerceptionSimulation. ISimulatedHandTracker

시뮬레이션 된 사람의 손을 추적 하는 시뮬레이션 된 장치의 부분을 설명 하는 인터페이스입니다.

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

**PerceptionSimulation. ISimulatedHandTracker. WorldPosition**

전 세계와 관련 하 여 노드의 위치를 미터 단위로 검색 합니다.

**PerceptionSimulation. ISimulatedHandTracker**

헤드의 중심을 기준으로 시뮬레이션 된 손 트래커의 위치를 검색 하 고 설정 합니다.

**PerceptionSimulation. ISimulatedHandTracker**

시뮬레이션 된 손 추적기의 하향 피치를 검색 하 고 설정 합니다.

**PerceptionSimulation. ISimulatedHandTracker. FrustumIgnored**

시뮬레이션 된 손 추적기의 하 한을 무시 하는지 여부를 검색 하 고 설정 합니다. 무시 하면 두 손을 항상 표시 됩니다. 무시 되지 않는 경우 (기본값) 손을 트래커의 두 부분에 있는 경우에만 표시 됩니다.

**PerceptionSimulation. ISimulatedHandTracker**

손을 시뮬레이션 된 손 추적기에 표시할지 여부를 결정 하는 데 사용 되는 대/그와 같은 속성을 검색 하 고 설정 합니다.

### <a name="microsoftperceptionsimulationisimulatedhuman"></a>PerceptionSimulation. ISimulatedHuman

시뮬레이션 된 사용자를 제어 하기 위한 최상위 인터페이스입니다.

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

**PerceptionSimulation. ISimulatedHuman. WorldPosition**

전 세계와 관련 하 여 노드의 위치를 측정 하 고 설정 합니다. 위치는 인간 피트의 중심에 있는 지점에 해당 합니다.

**PerceptionSimulation. ISimulatedHuman**

시뮬레이션 된 사람이 직면 하는 방향을 검색 하 고 설정 합니다. 0 라디안은 음의 Z 축을 아래로 내립니다. 양의 라디안은 Y 축에 대해 시계 방향으로 회전 합니다.

**PerceptionSimulation. ISimulatedHuman**

시뮬레이션 된 인간의 높이를 미터 단위로 검색 하 고 설정 합니다.

**PerceptionSimulation. ISimulatedHuman. LeftHand**

시뮬레이션 된 사람의 왼쪽을 검색 합니다.

**PerceptionSimulation. ISimulatedHuman. RightHand**

시뮬레이션 된 사람의 오른쪽을 검색 합니다.

**PerceptionSimulation. ISimulatedHuman**

시뮬레이션 된 사람의 머리를 검색 합니다.

**PerceptionSimulation (ISimulatedHuman (PerceptionSimulation. Vector3)**

현재 위치를 기준으로 시뮬레이션 된 사용자를 미터 단위로 이동 합니다.

매개 변수
* translation-현재 위치를 기준으로 이동할 변환입니다.

**PerceptionSimulation. ISimulatedHuman (System.web)**

시뮬레이션 된 사용자를 현재 방향에 상대적으로 회전 하 여 Y 축에 대해 시계 방향으로 회전 합니다.

매개 변수
* radians-Y 축을 중심으로 회전할 양입니다.

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a>PerceptionSimulation. ISimulatedHuman2

ISimulatedHuman을 ISimulatedHuman2로 캐스팅 하 여 추가 속성을 사용할 수 있습니다.

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

**PerceptionSimulation. ISimulatedHuman2**

왼쪽 6-DOF 컨트롤러를 검색 합니다.

**PerceptionSimulation. ISimulatedHuman2 컨트롤러**

오른쪽 6-DOF controller를 검색 합니다.


### <a name="microsoftperceptionsimulationisimulatedhand"></a>PerceptionSimulation. ISimulatedHand

시뮬레이션 된 사람의 손을 설명 하는 인터페이스

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

**PerceptionSimulation. ISimulatedHand. WorldPosition**

전 세계와 관련 하 여 노드의 위치를 미터 단위로 검색 합니다.

**PerceptionSimulation. ISimulatedHand**

미터 단위로 인간을 기준으로 시뮬레이션 된 손의 위치를 검색 하 고 설정 합니다.

**PerceptionSimulation. ISimulatedHand**

손이 현재 활성화 되어 있는지 여부를 검색 하 고 설정 합니다.

**PerceptionSimulation. ISimulatedHand**

손이 현재 SimulatedDevice에 표시 되는지 여부를 검색 합니다 .이는 핸드 트래커에서 검색할 위치에 있는지 여부를 검색 합니다.

**PerceptionSimulation. ISimulatedHand. Ensurevisible**

SimulatedDevice에 표시 되도록 손을 이동 합니다.

**PerceptionSimulation (ISimulatedHand (PerceptionSimulation. Vector3)**

현재 위치를 기준으로 시뮬레이션 된 손의 위치를 미터 단위로 이동 합니다.

매개 변수
* 번역-시뮬레이션 된 손을 변환할 양입니다.

**PerceptionSimulation ISimulatedHand. PerformGesture (PerceptionSimulation)**

시뮬레이션 된 손을 사용 하 여 제스처를 수행 합니다.  손을 사용 하도록 설정 된 경우에만 시스템에서 검색 됩니다.

매개 변수
* 제스처-수행할 제스처입니다.

### <a name="microsoftperceptionsimulationisimulatedhand2"></a>PerceptionSimulation. ISimulatedHand2

ISimulatedHand을 ISimulatedHand2로 캐스팅 하 여 추가 속성을 사용할 수 있습니다.
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

**PerceptionSimulation. ISimulatedHand2**

시뮬레이션 된 손 각도를 검색 하거나 설정 합니다.  양수 라디안은 축을 따라 볼 때 시계 방향으로 회전 합니다.

### <a name="microsoftperceptionsimulationisimulatedhand3"></a>PerceptionSimulation. ISimulatedHand3

ISimulatedHand을 ISimulatedHand3로 캐스팅 하 여 추가 속성을 사용할 수 있습니다.
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

**PerceptionSimulation. ISimulatedHand3. GetJointConfiguration**

지정 된 조인트의 조인트 구성을 가져옵니다.

**PerceptionSimulation. ISimulatedHand3. SetJointConfiguration**

지정 된 조인트의 조인트 구성을 설정 합니다.

**PerceptionSimulation. ISimulatedHand3. SetHandPose**

애니메이션 효과를 주는 선택적 플래그를 사용 하 여 손 모양을 알려진 포즈로 설정 합니다.  참고: 애니메이션 효과는 최종 조인트 구성을 즉시 반영 하지 않습니다.


### <a name="microsoftperceptionsimulationisimulatedhead"></a>PerceptionSimulation. ISimulatedHead

시뮬레이션 된 사람의 머리를 설명 하는 인터페이스입니다.

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

**PerceptionSimulation. ISimulatedHead. WorldPosition**

전 세계와 관련 하 여 노드의 위치를 미터 단위로 검색 합니다.

**PerceptionSimulation. ISimulatedHead**

시뮬레이션 된 헤드의 회전을 검색 합니다. 양수 라디안은 축을 따라 볼 때 시계 방향으로 회전 합니다.

**PerceptionSimulation. ISimulatedHead**

시뮬레이션 된 헤드의 지름을 검색 합니다. 이 값은 헤드의 중심 (회전 지점)을 결정 하는 데 사용 됩니다.

**PerceptionSimulation. ISimulatedHead (PerceptionSimulation. Rotation3)**

현재 회전을 기준으로 시뮬레이션 된 헤드를 회전 합니다. 양수 라디안은 축을 따라 볼 때 시계 방향으로 회전 합니다.

매개 변수
* 회전-회전할 양입니다.

### <a name="microsoftperceptionsimulationisimulatedhead2"></a>PerceptionSimulation. ISimulatedHead2

ISimulatedHead을 ISimulatedHead2로 캐스팅 하 여 추가 속성을 사용할 수 있습니다.

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

**PerceptionSimulation. ISimulatedHead2**

시뮬레이션 된 사람의 눈동자를 검색 합니다.

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a>PerceptionSimulation. ISimulatedSixDofController

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

**PerceptionSimulation. ISimulatedSixDofController. WorldPosition**

전 세계와 관련 하 여 노드의 위치를 미터 단위로 검색 합니다.

**PerceptionSimulation. ISimulatedSixDofController**

컨트롤러의 현재 상태를 검색 하거나 설정 합니다.  이동, 회전 또는 누르기 단추에 대 한 호출이 성공 하기 전에 컨트롤러 상태를 Off 이외의 값으로 설정 해야 합니다.

**PerceptionSimulation. ISimulatedSixDofController**

사용자를 기준으로 시뮬레이션 된 컨트롤러의 위치를 미터 단위로 검색 하거나 설정 합니다.

**PerceptionSimulation. ISimulatedSixDofController**

시뮬레이션 된 컨트롤러의 방향을 검색 하거나 설정 합니다.

**PerceptionSimulation (ISimulatedSixDofController (PerceptionSimulation. Vector3)**

현재 위치를 기준으로 시뮬레이트된 컨트롤러의 위치를 미터 단위로 이동 합니다.

매개 변수
* 번역-시뮬레이트된 컨트롤러를 변환할 양입니다.

**PerceptionSimulation. ISimulatedSixDofController (SimulatedSixDofControllerButton)**

시뮬레이션 된 컨트롤러의 단추를 누릅니다.  컨트롤러가 사용 하도록 설정 된 경우에만 시스템에서 검색 됩니다.

매개 변수
* button-단추를 누릅니다.

**PerceptionSimulation. ISimulatedSixDofController (SimulatedSixDofControllerButton)**

시뮬레이션 된 컨트롤러에서 단추를 놓습니다.  컨트롤러가 사용 하도록 설정 된 경우에만 시스템에서 검색 됩니다.

매개 변수
* button-해제할 단추입니다.

**PerceptionSimulation ISimulatedSixDofController. GetTouchpadPosition (out float, out float)**

시뮬레이션 된 컨트롤러의 터치 패드에서 시뮬레이션 된 손가락의 위치를 가져옵니다.

매개 변수
* x-손가락의 가로 위치입니다.
* y-손가락의 세로 위치입니다.

**PerceptionSimulation ISimulatedSixDofController. SetTouchpadPosition (float, float)**

시뮬레이션 된 컨트롤러의 터치 패드에서 시뮬레이션 된 손가락의 위치를 설정 합니다.

매개 변수
* x-손가락의 가로 위치입니다.
* y-손가락의 세로 위치입니다.

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a>PerceptionSimulation. ISimulatedSixDofController2

ISimulatedSixDofController를 ISimulatedSixDofController2로 캐스팅 하 여 추가 속성 및 메서드를 사용할 수 있습니다.

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

**PerceptionSimulation ISimulatedSixDofController2. GetThumbstickPosition (out float, out float)**

시뮬레이트된 컨트롤러에서 시뮬레이션 된 엄지 스틱의 위치를 가져옵니다.

매개 변수
* x-엄지 스틱의 가로 위치입니다.
* y-엄지 스틱의 세로 위치입니다.

**PerceptionSimulation ISimulatedSixDofController2. SetThumbstickPosition (float, float)**

시뮬레이트된 컨트롤러에서 시뮬레이션 된 엄지 스틱의 위치를 설정 합니다.

매개 변수
* x-엄지 스틱의 가로 위치입니다.
* y-엄지 스틱의 세로 위치입니다.

**PerceptionSimulation. ISimulatedSixDofController2. BatteryLevel**

시뮬레이트된 컨트롤러의 배터리 수준을 검색 하거나 설정 합니다.  값은 0.0 보다 크고 100.0 보다 작거나 같아야 합니다.


### <a name="microsoftperceptionsimulationisimulatedeyes"></a>PerceptionSimulation. ISimulatedEyes

시뮬레이션 된 사람의 눈을 설명 하는 인터페이스입니다.

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

**PerceptionSimulation. ISimulatedEyes**

시뮬레이션 된 눈동자의 회전을 검색 합니다. 양수 라디안은 축을 따라 볼 때 시계 방향으로 회전 합니다.

**PerceptionSimulation. ISimulatedEyes (PerceptionSimulation. Rotation3)**

현재 회전을 기준으로 시뮬레이션 된 눈동자를 회전 합니다. 양수 라디안은 축을 따라 볼 때 시계 방향으로 회전 합니다.

매개 변수
* 회전-회전할 양입니다.

**PerceptionSimulation. ISimulatedEyes. CalibrationState**

시뮬레이션 된 눈동자의 보정 상태를 검색 하거나 설정 합니다.

**PerceptionSimulation. ISimulatedEyes. WorldPosition**

전 세계와 관련 하 여 노드의 위치를 미터 단위로 검색 합니다.


### <a name="microsoftperceptionsimulationisimulationrecording"></a>PerceptionSimulation. ISimulationRecording

재생을 위해 로드 된 단일 기록과 상호 작용 하기 위한 인터페이스입니다.

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

**PerceptionSimulation. ISimulationRecording**

기록의 데이터 형식 목록을 검색 합니다.

**PerceptionSimulation. ISimulationRecording**

기록의 현재 상태를 검색 합니다.

**PerceptionSimulation. ISimulationRecording**

재생을 시작 합니다. 기록이 일시 중지 된 경우 일시 중지 된 위치에서 재생이 다시 시작 됩니다. 중지 된 경우 재생이 시작 부분에서 시작 됩니다. 이미를 재생 하는 경우이 호출은 무시 됩니다.

**PerceptionSimulation. ISimulationRecording**

현재 위치에서 재생을 일시 중지 합니다. 기록이 중지 되 면 호출은 무시 됩니다.

**PerceptionSimulation (ISimulationRecording).**

지정 된 시간 (시작부터 100 나노초 간격)에 대 한 기록을 검색 하 고 해당 위치에서 일시 중지 합니다. 시간이 기록의 끝을 초과 하면 마지막 프레임에서 일시 중지 됩니다.

매개 변수
* 틱-검색 하는 시간입니다.

**PerceptionSimulation. ISimulationRecording**

재생을 중지 하 고 위치를 시작 부분으로 다시 설정 합니다.

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a>PerceptionSimulation. ISimulationRecordingCallback

재생 하는 동안 상태 변경을 수신 하기 위한 인터페이스입니다.

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

**PerceptionSimulation. ISimulationRecordingCallback PlaybackStateChanged (PerceptionSimulation Backstate)**

ISimulationRecording의 재생 상태가 변경 될 때 호출 됩니다.

매개 변수
* newState-기록의 새 상태입니다.

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a>PerceptionSimulation. PerceptionSimulationManager

인식 시뮬레이션 개체를 만들기 위한 루트 개체입니다.

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

**PerceptionSimulation PerceptionSimulationManager. CreatePerceptionSimulationManager (PerceptionSimulation)**

시뮬레이션 된 패킷을 생성 하 여 제공 된 싱크에 전달 하기 위해 개체에를 만듭니다.

매개 변수
* sink-생성 된 모든 패킷을 수신 하는 싱크입니다.

반환 값

만든 관리자입니다.

**PerceptionSimulation PerceptionSimulationManager. CreatePerceptionSimulationRecording (System.string)**

받은 모든 패킷을 파일의 지정 된 경로에 저장 하는 싱크를 만듭니다.

매개 변수
* path-만들 파일의 경로입니다.

반환 값

만든 싱크입니다.

**PerceptionSimulation. PerceptionSimulationManager, LoadPerceptionSimulationRecording (System.string, PerceptionSimulation)**

지정 된 파일에서 기록을 로드 합니다.

매개 변수
* path-로드할 파일의 경로입니다.
* 팩터리-필요할 때 ISimulationStreamSink를 만들기 위해 기록에서 사용 하는 팩터리입니다.

반환 값

로드 된 기록입니다.

**PerceptionSimulation (PerceptionSimulationManager, LoadPerceptionSimulationRecording (System.string, PerceptionSimulation) PerceptionSimulation. ISimulationRecordingCallback)**

지정 된 파일에서 기록을 로드 합니다.

매개 변수
* path-로드할 파일의 경로입니다.
* 팩터리-필요할 때 ISimulationStreamSink를 만들기 위해 기록에서 사용 하는 팩터리입니다.
* 콜백-녹화 상태를 다시 보고 하는 업데이트를 수신 하는 콜백입니다.

반환 값

로드 된 기록입니다.

### <a name="microsoftperceptionsimulationstreamdatatypes"></a>PerceptionSimulation 데이터 형식

다양 한 유형의 스트림 데이터를 설명 합니다.

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

**PerceptionSimulation 데이터 형식입니다.**

스트림 데이터 형식이 없음을 나타내는 데 사용 되는 센티널 값입니다.

**PerceptionSimulation. Head**

헤드의 위치와 방향에 대 한 데이터 스트림입니다.

**PerceptionSimulation. 직접**

바늘의 위치 및 제스처와 관련 된 데이터 스트림입니다.

**PerceptionSimulation. SpatialMapping**

환경의 공간 매핑에 대 한 데이터 스트림입니다.

**PerceptionSimulation. 보정**

장치의 보정에 대 한 데이터 스트림입니다. 원격 모드의 시스템 에서만 보정 패킷을 허용 합니다.

**PerceptionSimulation. 환경**

장치 환경에 대 한 데이터 스트림입니다.

**PerceptionSimulation 데이터 형식**

기록 된 모든 데이터 형식을 나타내는 데 사용 되는 센티널 값입니다.

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a>PerceptionSimulation. ISimulationStreamSink

시뮬레이션 스트림에서 데이터 패킷을 수신 하는 개체입니다.

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

**PerceptionSimulation ISimulationStreamSink. OnPacketReceived (uint length, byte [] packet)**

는 내부적으로 형식화 되 고 버전이 지정 되는 단일 패킷을 받습니다.

매개 변수
* length-패킷의 길이입니다.
* packet-패킷의 데이터입니다.

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a>PerceptionSimulation. ISimulationStreamSinkFactory

ISimulationStreamSink을 만드는 개체입니다.

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

**PerceptionSimulation ISimulationStreamSinkFactory. CreateSimulationStreamSink ()**

ISimulationStreamSink의 단일 인스턴스를 만듭니다.

반환 값

만든 싱크입니다.
