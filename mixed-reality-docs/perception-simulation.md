---
title: Perception 시뮬레이션
description: 몰입 형 응용 프로그램에 대 한 시뮬레이션 된 입력을 자동화 하는 Perception 시뮬레이션 라이브러리를 사용 하는 데
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, 시뮬레이션 테스트
ms.openlocfilehash: 693750eb753bd11cbe7d7cfb47e04f1a3506ca9a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602205"
---
# <a name="perception-simulation"></a><span data-ttu-id="060f3-104">Perception 시뮬레이션</span><span class="sxs-lookup"><span data-stu-id="060f3-104">Perception simulation</span></span>

<span data-ttu-id="060f3-105">앱에 대 한 자동화 된 테스트를 작성 하 시겠습니까?</span><span class="sxs-lookup"><span data-stu-id="060f3-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="060f3-106">구성 요소 수준 단위 테스트 뿐만 아니라 실제로 사용자 앱에 종단 간 연습을 테스트 하 시겠습니까?</span><span class="sxs-lookup"><span data-stu-id="060f3-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="060f3-107">Perception 시뮬레이션은 원하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="060f3-108">Perception 시뮬레이션 라이브러리 테스트를 자동화할 수 있도록 앱에 가짜 사람이 및 world 입력된 데이터를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-108">The Perception Simulation library sends fake human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="060f3-109">예를 들어, 왼쪽 및 오른쪽 사람이 원하는 및 제스처를 수행 하는 다음의 입력을 시뮬레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-109">For example, you can simulate the input of a human looking left and right and then performing a gesture.</span></span>

<span data-ttu-id="060f3-110">Perception 시뮬레이션 실제 HoloLens, HoloLens 에뮬레이터 또는 혼합 현실 포털 설치를 사용 하 여 PC에 이와 같은 시뮬레이션 된 입력을 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="060f3-111">Perception 혼합 현실 장치에서 실시간 센서를 무시 하 고 전송 하는 시뮬레이션 장치에서 실행 중인 응용 프로그램에 대 한 입력을 시뮬레이션 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="060f3-112">항상를 사용 하며와 Perception 시뮬레이션을 사용 하 여 실행 하는 실제 센서를 사용 하 여 실행 차이 구별할 수 없습니다. 동일한 Api 통해 이러한 모조 입력된 이벤트를 수신 하는 응용 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-112">Applications receive these fake input events through the same APIs they always use, and can't tell the difference between running with real sensors versus running with Perception Simulation.</span></span> <span data-ttu-id="060f3-113">Perception 시뮬레이션은 시뮬레이션 된 입력 HoloLens Virtual Machine에 보내는 데 HoloLens 에뮬레이터에서 동일한 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-113">Perception Simulation is the same technology used by the HoloLens emulator to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="060f3-114">시뮬레이션은 IPerceptionSimulationManager 개체를 만들어 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-114">Simulation starts by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="060f3-115">이 개체에서의 시뮬레이션 된 "사용자"를 헤드 위치, 손 모양 위치 및 제스처를 포함 하 여 속성을 제어 하는 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="060f3-116">Perception 시뮬레이션에 대 한 Visual Studio 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="060f3-116">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="060f3-117">[HoloLens 에뮬레이터를 설치할](install-the-tools.md) 개발 PC의 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-117">[Install the HoloLens emulator](install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="060f3-118">에뮬레이터는 Perception 시뮬레이션 하는 데 사용할 라이브러리를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-118">The emulator includes the libraries you will use for Perception Simulation.</span></span>
2. <span data-ttu-id="060f3-119">새 Visual Studio를 만들려면 C# 데스크톱 프로젝트 (콘솔 프로젝트를 시작 하려면 잘 작동).</span><span class="sxs-lookup"><span data-stu-id="060f3-119">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="060f3-120">다음 이진 파일을 프로젝트에 참조로 추가 (프로젝트-> 추가-> 참조...). 찾을 수 있습니다 **%ProgramFiles (x86) %\Microsoft XDE\10.0.11082.0** 를 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-120">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in **%ProgramFiles(x86)%\Microsoft XDE\10.0.11082.0** a.</span></span> <span data-ttu-id="060f3-121">PerceptionSimulationManager.Interop.dll-관리 되는 C# Perception 시뮬레이션에 대 한 래퍼입니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-121">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="060f3-122">b.</span><span class="sxs-lookup"><span data-stu-id="060f3-122">b.</span></span> <span data-ttu-id="060f3-123">PerceptionSimulationRest.dll-HoloLens 또는 에뮬레이터에 웹 소켓 통신 채널을 설정 하기 위한 라이브러리입니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-123">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="060f3-124">다.</span><span class="sxs-lookup"><span data-stu-id="060f3-124">c.</span></span> <span data-ttu-id="060f3-125">SimulationStream.Interop.dll-시뮬레이션에 대 한 공유 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-125">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="060f3-126">구현을 추가 프로젝트에 이진 PerceptionSimulationManager.dll를 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-126">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="060f3-127">먼저 프로젝트에는 이진 형식으로 추가 (프로젝트-> 추가-> 기존 항목...). 프로젝트 소스 폴더에 복사 하지 않습니다 고 링크로 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-127">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="060f3-128">![프로젝트에 링크로 PerceptionSimulationManager.dll 추가할](images/saveaslink.png) b.</span><span class="sxs-lookup"><span data-stu-id="060f3-128">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="060f3-129">있는지를 확인 한 다음 빌드 출력 폴더로 복사의 가져올 것입니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-129">Then make sure that it get's copied to your output folder on build.</span></span> <span data-ttu-id="060f3-130">이진 파일에 대 한 속성 시트입니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-130">This is in the property sheet for the binary .</span></span> <span data-ttu-id="060f3-131">![출력 디렉터리로 복사할 PerceptionSimulationManager.dll 표시](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="060f3-131">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="060f3-132">IPerceptionSimulation Manager 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="060f3-132">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="060f3-133">시뮬레이션을 제어 하려면 IPerceptionSimulationManager 개체에서 검색 된 개체에 업데이트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-133">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="060f3-134">첫 번째 단계는 해당 개체를 가져오고 대상 장치 또는 에뮬레이터에 연결 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-134">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="060f3-135">장치 포털 단추를 클릭 하 여 에뮬레이터의 IP 주소를 가져올 수 있습니다는 [도구 모음](using-the-hololens-emulator.md#anatomy-of-the-hololens-emulator)</span><span class="sxs-lookup"><span data-stu-id="060f3-135">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md#anatomy-of-the-hololens-emulator)</span></span>

<span data-ttu-id="060f3-136">![열기 장치 포털 아이콘](images/emulator-deviceportal.png) **장치 포털 열기**: 에뮬레이터에서 HoloLens OS에 대 한 Windows Device Portal 엽니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-136">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>

<span data-ttu-id="060f3-137">먼저 RestSimulationStreamSink 개체를 가져오는 RestSimulationStreamSink.Create 부르겠습니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-137">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="060f3-138">이 대상 장치 또는 에뮬레이터는 http 연결을 통해 제어 됩니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-138">This is the target device or emulator that you will control over an http connection.</span></span> <span data-ttu-id="060f3-139">명령을 전달 되며에서 처리 합니다 [Windows Device Portal](using-the-windows-device-portal.md) 장치 또는 에뮬레이터에서 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-139">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="060f3-140">개체를 만들려고 해야 4 개의 매개 변수는:</span><span class="sxs-lookup"><span data-stu-id="060f3-140">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="060f3-141">대상 장치의 IP 주소 Uri uri (예를 들어 "http://123.123.123.123")</span><span class="sxs-lookup"><span data-stu-id="060f3-141">Uri uri - IP address of the target device (e.g., "http://123.123.123.123")</span></span>
* <span data-ttu-id="060f3-142">System.Net.NetworkCredential 자격 증명-사용자 이름/암호에 연결 합니다 [Windows Device Portal](using-the-windows-device-portal.md) 대상 장치 또는 에뮬레이터에서 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-142">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="060f3-143">경우 해당 로컬 168 통해 에뮬레이터에 연결 합니다. *.* . \* 주소를 같은 PC에서 자격 증명을 모두 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-143">If you are connecting to the emulator via its local 168.*.*.\* address on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="060f3-144">bool 기본-보통 우선 순위에서 낮은 우선 순위에 대해 false 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-144">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="060f3-145">일반적으로이 값을 설정 하려는 *true* 테스트 시나리오에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-145">You generally want to set this to *true* for test scenarios.</span></span>
* <span data-ttu-id="060f3-146">System.Threading.CancellationToken 토큰-비동기 작업을 취소할 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-146">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="060f3-147">두 번째는 IPerceptionSimulationManager 만들게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-147">Second you will create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="060f3-148">시뮬레이션을 제어 하는 데 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-148">This is the object you use to control simulation.</span></span> <span data-ttu-id="060f3-149">이 비동기 메서드에서 수행도 해야 함을 note 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-149">Note that this must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="060f3-150">시뮬레이션 된 사람을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-150">Control the simulated Human</span></span>

<span data-ttu-id="060f3-151">IPerceptionSimulationManager ISimulatedHuman 개체를 반환 하는 사람이 속성을 있습니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-151">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="060f3-152">시뮬레이션 된 사람을 제어 하려면이 개체에 대 한 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-152">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="060f3-153">예를 들어 다음과 같은 가치를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-153">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="060f3-154">기본 샘플 C# 콘솔 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="060f3-154">Basic Sample C# console application</span></span>

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
                try
                {
                    RestSimulationStreamSink sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("http://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        new System.Threading.CancellationToken());

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();
        }
    }
}
```

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="060f3-155">샘플 확장 C# 콘솔 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="060f3-155">Extended Sample C# console application</span></span>

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
                try
                {
                    RestSimulationStreamSink sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("http://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        new System.Threading.CancellationToken());

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);

                    // Now, we'll simulate a sequence of actions.
                    // Sleeps in-between each action give time to the system
                    // to be able to properly react.
                    // This is just an example. A proper automated test should verify
                    // that the app has behaved correctly
                    // before proceeding to the next step, instead of using Sleeps.

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
        }
    }
}
```

## <a name="api-reference"></a><span data-ttu-id="060f3-156">API 참조</span><span class="sxs-lookup"><span data-stu-id="060f3-156">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="060f3-157">Microsoft.PerceptionSimulation.SimulatedDeviceType</span><span class="sxs-lookup"><span data-stu-id="060f3-157">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="060f3-158">시뮬레이션 된 장치 종류를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-158">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="060f3-159">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span><span class="sxs-lookup"><span data-stu-id="060f3-159">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="060f3-160">PerceptionSimulationManager에 대 한 기본 장치를 가상의 참조</span><span class="sxs-lookup"><span data-stu-id="060f3-160">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="060f3-161">Microsoft.PerceptionSimulation.HeadTrackerMode</span><span class="sxs-lookup"><span data-stu-id="060f3-161">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="060f3-162">헤드 추적기 모드를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-162">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="060f3-163">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span><span class="sxs-lookup"><span data-stu-id="060f3-163">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="060f3-164">기본 헤드를 추적 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-164">Default Head Tracking.</span></span> <span data-ttu-id="060f3-165">즉, 시스템 관리 모드 런타임 조건에 따라 최상의 헤드를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-165">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="060f3-166">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span><span class="sxs-lookup"><span data-stu-id="060f3-166">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="060f3-167">추적만 헤드 방향입니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-167">Orientation Only Head Tracking.</span></span> <span data-ttu-id="060f3-168">즉, 추적된 위치를 신뢰할 수 있는 아닐 헤드 위치에 종속 된 일부 기능을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-168">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="060f3-169">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span><span class="sxs-lookup"><span data-stu-id="060f3-169">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="060f3-170">위치 헤드 추적 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-170">Positional Head Tracking.</span></span> <span data-ttu-id="060f3-171">즉, 추적 된 헤드 위치와 방향을 둘 다 신뢰할 수 있는</span><span class="sxs-lookup"><span data-stu-id="060f3-171">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="060f3-172">Microsoft.PerceptionSimulation.SimulatedGesture</span><span class="sxs-lookup"><span data-stu-id="060f3-172">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="060f3-173">시뮬레이션 된 제스처를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-173">Describes a simulated gesture</span></span>

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

<span data-ttu-id="060f3-174">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span><span class="sxs-lookup"><span data-stu-id="060f3-174">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="060f3-175">없는 제스처를 나타내는 데 센티널 값</span><span class="sxs-lookup"><span data-stu-id="060f3-175">A sentinel value used to indicate no gestures</span></span>

<span data-ttu-id="060f3-176">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span><span class="sxs-lookup"><span data-stu-id="060f3-176">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="060f3-177">손가락 제스처를 누름</span><span class="sxs-lookup"><span data-stu-id="060f3-177">A finger pressed gesture</span></span>

<span data-ttu-id="060f3-178">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span><span class="sxs-lookup"><span data-stu-id="060f3-178">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="060f3-179">출시 손가락 제스처</span><span class="sxs-lookup"><span data-stu-id="060f3-179">A finger released gesture</span></span>

<span data-ttu-id="060f3-180">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span><span class="sxs-lookup"><span data-stu-id="060f3-180">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="060f3-181">홈 제스처</span><span class="sxs-lookup"><span data-stu-id="060f3-181">The home gesture</span></span>

<span data-ttu-id="060f3-182">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span><span class="sxs-lookup"><span data-stu-id="060f3-182">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="060f3-183">최대 유효 제스처</span><span class="sxs-lookup"><span data-stu-id="060f3-183">The maximum valid gesture</span></span>

### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="060f3-184">Microsoft.PerceptionSimulation.PlaybackState</span><span class="sxs-lookup"><span data-stu-id="060f3-184">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="060f3-185">재생 하는 상태를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-185">Describes the state of a playback</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="060f3-186">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span><span class="sxs-lookup"><span data-stu-id="060f3-186">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="060f3-187">녹음/녹화는 현재 중지 되 고 재생을 위한 준비</span><span class="sxs-lookup"><span data-stu-id="060f3-187">The recording is currently stopped and ready for playback</span></span>

<span data-ttu-id="060f3-188">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span><span class="sxs-lookup"><span data-stu-id="060f3-188">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="060f3-189">현재 녹음/녹화 재생</span><span class="sxs-lookup"><span data-stu-id="060f3-189">The recording is currently playing</span></span>

<span data-ttu-id="060f3-190">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span><span class="sxs-lookup"><span data-stu-id="060f3-190">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="060f3-191">녹음/녹화는 현재 일시 중지</span><span class="sxs-lookup"><span data-stu-id="060f3-191">The recording is currently paused</span></span>

<span data-ttu-id="060f3-192">**Microsoft.PerceptionSimulation.PlaybackState.End**</span><span class="sxs-lookup"><span data-stu-id="060f3-192">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="060f3-193">녹음/녹화 끝에 도달 했습니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-193">The recording has reached the end</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="060f3-194">Microsoft.PerceptionSimulation.Vector3</span><span class="sxs-lookup"><span data-stu-id="060f3-194">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="060f3-195">점 또는 3D 공간에서 벡터를 설명 하는 3 개 구성 요소가 벡터를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-195">Describes a 3 components vector, which might describe a point or a vector in 3D space</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="060f3-196">**Microsoft.PerceptionSimulation.Vector3.X**</span><span class="sxs-lookup"><span data-stu-id="060f3-196">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="060f3-197">벡터의 X 구성 요소</span><span class="sxs-lookup"><span data-stu-id="060f3-197">The X component of the vector</span></span>

<span data-ttu-id="060f3-198">**Microsoft.PerceptionSimulation.Vector3.Y**</span><span class="sxs-lookup"><span data-stu-id="060f3-198">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="060f3-199">벡터의 Y 구성 요소</span><span class="sxs-lookup"><span data-stu-id="060f3-199">The Y component of the vector</span></span>

<span data-ttu-id="060f3-200">**Microsoft.PerceptionSimulation.Vector3.Z**</span><span class="sxs-lookup"><span data-stu-id="060f3-200">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="060f3-201">벡터의 Z 구성 요소</span><span class="sxs-lookup"><span data-stu-id="060f3-201">The Z component of the vector</span></span>

<span data-ttu-id="060f3-202">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span><span class="sxs-lookup"><span data-stu-id="060f3-202">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="060f3-203">새 Vector3를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-203">Construct a new Vector3</span></span>

<span data-ttu-id="060f3-204">매개 변수</span><span class="sxs-lookup"><span data-stu-id="060f3-204">Parameters</span></span>
* <span data-ttu-id="060f3-205">x 벡터의-x 구성 요소</span><span class="sxs-lookup"><span data-stu-id="060f3-205">x - The x component of the vector</span></span>
* <span data-ttu-id="060f3-206">y 벡터의-y 구성 요소</span><span class="sxs-lookup"><span data-stu-id="060f3-206">y - The y component of the vector</span></span>
* <span data-ttu-id="060f3-207">z 벡터의-z 구성 요소</span><span class="sxs-lookup"><span data-stu-id="060f3-207">z - The z component of the vector</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="060f3-208">Microsoft.PerceptionSimulation.Rotation3</span><span class="sxs-lookup"><span data-stu-id="060f3-208">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="060f3-209">3 개 구성 요소가 회전을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-209">Describes a 3 components rotation</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="060f3-210">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span><span class="sxs-lookup"><span data-stu-id="060f3-210">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="060f3-211">회전의 피치 구성 요소 X 축을 중심으로 축소</span><span class="sxs-lookup"><span data-stu-id="060f3-211">The Pitch component of the Rotation, down around the X axis</span></span>

<span data-ttu-id="060f3-212">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span><span class="sxs-lookup"><span data-stu-id="060f3-212">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="060f3-213">Y 축 중심 오른쪽 회전 요 구성 요소</span><span class="sxs-lookup"><span data-stu-id="060f3-213">The Yaw component of the Rotation, right around the Y axis</span></span>

<span data-ttu-id="060f3-214">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span><span class="sxs-lookup"><span data-stu-id="060f3-214">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="060f3-215">Z 축 중심 오른쪽 회전의 롤포워드 구성 요소</span><span class="sxs-lookup"><span data-stu-id="060f3-215">The Roll component of the Rotation, right around the Z axis</span></span>

<span data-ttu-id="060f3-216">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span><span class="sxs-lookup"><span data-stu-id="060f3-216">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="060f3-217">새 Rotation3 생성</span><span class="sxs-lookup"><span data-stu-id="060f3-217">Construct a new Rotation3</span></span>

<span data-ttu-id="060f3-218">매개 변수</span><span class="sxs-lookup"><span data-stu-id="060f3-218">Parameters</span></span>
* <span data-ttu-id="060f3-219">피치-회전 피치 구성 요소</span><span class="sxs-lookup"><span data-stu-id="060f3-219">pitch - The pitch component of the Rotation</span></span>
* <span data-ttu-id="060f3-220">요-회전 요 구성 요소</span><span class="sxs-lookup"><span data-stu-id="060f3-220">yaw - The yaw component of the Rotation</span></span>
* <span data-ttu-id="060f3-221">배포-배포 구성 요소 회전</span><span class="sxs-lookup"><span data-stu-id="060f3-221">roll - The roll component of the Rotation</span></span>

### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="060f3-222">Microsoft.PerceptionSimulation.Frustum</span><span class="sxs-lookup"><span data-stu-id="060f3-222">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="060f3-223">보기 꼭지점이 절 두 체를, 카메라에서 일반적으로 사용에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-223">Describes a view frustum, as typically used by a camera</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="060f3-224">**Microsoft.PerceptionSimulation.Frustum.Near**</span><span class="sxs-lookup"><span data-stu-id="060f3-224">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="060f3-225">하면 프러스텀에 포함 된 최소 거리</span><span class="sxs-lookup"><span data-stu-id="060f3-225">The minimum distance that is contained in the frustum</span></span>

<span data-ttu-id="060f3-226">**Microsoft.PerceptionSimulation.Frustum.Far**</span><span class="sxs-lookup"><span data-stu-id="060f3-226">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="060f3-227">하면 프러스텀에 포함 된 최대 거리</span><span class="sxs-lookup"><span data-stu-id="060f3-227">The maximum distance that is contained in the frustum</span></span>

<span data-ttu-id="060f3-228">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span><span class="sxs-lookup"><span data-stu-id="060f3-228">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="060f3-229">가로 보기의 필드 (PI 보다 작음) 라디안에서 하면 프러스텀의</span><span class="sxs-lookup"><span data-stu-id="060f3-229">The horizontal field of view of the frustum, in radians (less than PI)</span></span>

<span data-ttu-id="060f3-230">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="060f3-230">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="060f3-231">가로 뷰 필드를 세로 보기 필드의 비율</span><span class="sxs-lookup"><span data-stu-id="060f3-231">The ratio of horizontal field of view to vertical field of view</span></span>

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="060f3-232">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="060f3-232">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="060f3-233">장치를 제어 하는 데 패킷을 생성 하는 것에 대 한 루트</span><span class="sxs-lookup"><span data-stu-id="060f3-233">Root for generating the packets used to control a device</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="060f3-234">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span><span class="sxs-lookup"><span data-stu-id="060f3-234">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="060f3-235">시뮬레이션 된 사람 및 시뮬레이션된 세계를 해석 하는 시뮬레이션 된 장치 개체를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-235">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="060f3-236">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span><span class="sxs-lookup"><span data-stu-id="060f3-236">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="060f3-237">시뮬레이션 된 사람을 제어 하는 개체를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-237">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="060f3-238">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span><span class="sxs-lookup"><span data-stu-id="060f3-238">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="060f3-239">시뮬레이션을 기본 상태로 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-239">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="060f3-240">Microsoft.PerceptionSimulation.ISimulatedDevice</span><span class="sxs-lookup"><span data-stu-id="060f3-240">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="060f3-241">시뮬레이션 된 전 세계 및 시뮬레이션 된 사람을 해석 하는 장치를 설명 하는 인터페이스</span><span class="sxs-lookup"><span data-stu-id="060f3-241">Interface describing the device which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="060f3-242">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span><span class="sxs-lookup"><span data-stu-id="060f3-242">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="060f3-243">시뮬레이션된 된 장치에서 Head Tracker를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-243">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="060f3-244">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span><span class="sxs-lookup"><span data-stu-id="060f3-244">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="060f3-245">시뮬레이션된 된 장치에서 직접 Tracker를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-245">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="060f3-246">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span><span class="sxs-lookup"><span data-stu-id="060f3-246">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="060f3-247">제공 된 장치 유형과 일치 하도록 시뮬레이션 된 장치의 속성을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-247">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="060f3-248">매개 변수</span><span class="sxs-lookup"><span data-stu-id="060f3-248">Parameters</span></span>
* <span data-ttu-id="060f3-249">입력-시뮬레이션 된 장치의 새 유형</span><span class="sxs-lookup"><span data-stu-id="060f3-249">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="060f3-250">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span><span class="sxs-lookup"><span data-stu-id="060f3-250">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="060f3-251">시뮬레이션 된 장치를 시뮬레이션 된 사람이의 머리를 추적 하는 부분을 설명 하는 인터페이스</span><span class="sxs-lookup"><span data-stu-id="060f3-251">Interface describing the portion of the simulated device that tracks the head of the simulated human</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="060f3-252">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="060f3-252">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="060f3-253">검색 하 고 현재 헤드 추적기 모드를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-253">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="060f3-254">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span><span class="sxs-lookup"><span data-stu-id="060f3-254">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="060f3-255">시뮬레이션 된 장치를 시뮬레이션 된 사람을 추적 하는 부분을 설명 하는 인터페이스</span><span class="sxs-lookup"><span data-stu-id="060f3-255">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

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

<span data-ttu-id="060f3-256">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="060f3-256">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="060f3-257">미터 단위의 전 세계를 통해 관련 노드의 위치 검색</span><span class="sxs-lookup"><span data-stu-id="060f3-257">Retrieve the position of the node with relation to the world, in meters</span></span>

<span data-ttu-id="060f3-258">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span><span class="sxs-lookup"><span data-stu-id="060f3-258">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="060f3-259">검색 하 고 헤드의 가운데를 기준으로 시뮬레이션 된 직접 추적기의 위치를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-259">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="060f3-260">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span><span class="sxs-lookup"><span data-stu-id="060f3-260">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="060f3-261">검색 하 고 시뮬레이션 된 직접 추적기의 아래쪽 피치를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-261">Retrieve and set the downward pitch of the simulated hand tracker</span></span>

<span data-ttu-id="060f3-262">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span><span class="sxs-lookup"><span data-stu-id="060f3-262">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="060f3-263">검색 및 시뮬레이션 된 직접 추적기의 하면 프러스텀을 무시할지 여부를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-263">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="060f3-264">무시 된 경우 두 게 항상 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-264">When ignored, both hands are always visible.</span></span> <span data-ttu-id="060f3-265">없습니다 (기본값)를 무시 하는 경우는 표시 직접 추적기의 하면 프러스텀 있는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-265">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="060f3-266">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span><span class="sxs-lookup"><span data-stu-id="060f3-266">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="060f3-267">검색 및 실습 시뮬레이션된 직접 추적기에 표시 되는지 확인 하는 데 꼭지점이 절 두 체 속성을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-267">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="060f3-268">Microsoft.PerceptionSimulation.ISimulatedHuman</span><span class="sxs-lookup"><span data-stu-id="060f3-268">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="060f3-269">시뮬레이션 된 사람을 제어 하기 위한 상위 수준 인터페이스</span><span class="sxs-lookup"><span data-stu-id="060f3-269">Top level interface for controlling the simulated human</span></span>

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

<span data-ttu-id="060f3-270">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="060f3-270">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="060f3-271">검색 하 고 전 세계를 미터 단위로 통해 관련 노드의 위치를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-271">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="060f3-272">위치는 사람이 feet 중앙 지점에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-272">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="060f3-273">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span><span class="sxs-lookup"><span data-stu-id="060f3-273">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="060f3-274">검색 및 전 세계의 방향을 시뮬레이션 된 얼굴을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-274">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="060f3-275">음의 Z 축을 0 라디안 직면 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-275">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="060f3-276">Y 축에 대 한 양의 라디안을 시계 방향으로 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-276">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="060f3-277">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span><span class="sxs-lookup"><span data-stu-id="060f3-277">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="060f3-278">검색 하 고 시뮬레이션 된 사람이의 높이 미터 단위로 설정</span><span class="sxs-lookup"><span data-stu-id="060f3-278">Retrieve and set the height of the simulated human, in meters</span></span>

<span data-ttu-id="060f3-279">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span><span class="sxs-lookup"><span data-stu-id="060f3-279">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="060f3-280">시뮬레이션 된 사람이의 왼쪽 위를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-280">Retrieve the left hand of the simulated human</span></span>

<span data-ttu-id="060f3-281">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span><span class="sxs-lookup"><span data-stu-id="060f3-281">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="060f3-282">시뮬레이션 된 사람이의 오른쪽 위 검색</span><span class="sxs-lookup"><span data-stu-id="060f3-282">Retrieve the right hand of the simulated human</span></span>

<span data-ttu-id="060f3-283">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span><span class="sxs-lookup"><span data-stu-id="060f3-283">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="060f3-284">시뮬레이션 된 사람이의 머리를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-284">Retrieve the head of the simulated human</span></span>

<span data-ttu-id="060f3-285">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="060f3-285">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="060f3-286">시뮬레이션 된 사람이 미터 단위로, 현재 위치를 기준으로 이동</span><span class="sxs-lookup"><span data-stu-id="060f3-286">Move the simulated human relative to its current position, in meters</span></span>

<span data-ttu-id="060f3-287">매개 변수</span><span class="sxs-lookup"><span data-stu-id="060f3-287">Parameters</span></span>
* <span data-ttu-id="060f3-288">현재 위치를 기준으로 이동 하려면 변환 번역</span><span class="sxs-lookup"><span data-stu-id="060f3-288">translation - The translation to move, relative to current position</span></span>

<span data-ttu-id="060f3-289">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span><span class="sxs-lookup"><span data-stu-id="060f3-289">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="060f3-290">Y 축에 대 한 시계 방향으로 현재 방향 기준으로 시뮬레이션 된 사람이 회전</span><span class="sxs-lookup"><span data-stu-id="060f3-290">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="060f3-291">매개 변수</span><span class="sxs-lookup"><span data-stu-id="060f3-291">Parameters</span></span>
* <span data-ttu-id="060f3-292">라디안으로-Y 축을 중심으로 회전할 양</span><span class="sxs-lookup"><span data-stu-id="060f3-292">radians - The amount to rotate around the Y axis</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="060f3-293">Microsoft.PerceptionSimulation.ISimulatedHand</span><span class="sxs-lookup"><span data-stu-id="060f3-293">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="060f3-294">시뮬레이션 된 사용자의 직접을 설명 하는 인터페이스</span><span class="sxs-lookup"><span data-stu-id="060f3-294">Interface describing a hand of the simulated human</span></span>

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

<span data-ttu-id="060f3-295">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="060f3-295">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="060f3-296">미터 단위의 전 세계를 통해 관련 노드의 위치 검색</span><span class="sxs-lookup"><span data-stu-id="060f3-296">Retrieve the position of the node with relation to the world, in meters</span></span>

<span data-ttu-id="060f3-297">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span><span class="sxs-lookup"><span data-stu-id="060f3-297">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="060f3-298">검색 및 미터에서 사람을 기준으로 시뮬레이션 된 손 모양 아이콘이 위치를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-298">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="060f3-299">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span><span class="sxs-lookup"><span data-stu-id="060f3-299">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="060f3-300">검색 하 고 손 모양 아이콘이 현재 활성화 되어 있는지 여부를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-300">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="060f3-301">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span><span class="sxs-lookup"><span data-stu-id="060f3-301">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="060f3-302">손 모양 아이콘이 (즉, 인지는 HandTracker에서 검색할 수는 위치) SimulatedDevice에 현재 표시 되는지 여부를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-302">Retrieve whether the hand is currently visible to the SimulatedDevice (ie, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="060f3-303">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span><span class="sxs-lookup"><span data-stu-id="060f3-303">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="060f3-304">SimulatedDevice를 볼 수 있도록 손 모양 아이콘이 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-304">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="060f3-305">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="060f3-305">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="060f3-306">미터 단위로, 현재 위치를 기준으로 시뮬레이션 된 손 모양 아이콘이 위치를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-306">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="060f3-307">매개 변수</span><span class="sxs-lookup"><span data-stu-id="060f3-307">Parameters</span></span>
* <span data-ttu-id="060f3-308">번역-시뮬레이션 된 손 모양 아이콘이 변환할 크기</span><span class="sxs-lookup"><span data-stu-id="060f3-308">translation - The amount to translate the simulated hand</span></span>

<span data-ttu-id="060f3-309">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span><span class="sxs-lookup"><span data-stu-id="060f3-309">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="060f3-310">시뮬레이션 된 손 모양 아이콘이 (만 검색 됩니다 시스템 손 모양 아이콘이 사용 되는 경우)를 사용 하 여 제스처를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-310">Perform a gesture using the simulated hand (it will only be detected by the system if the hand is enabled).</span></span>

<span data-ttu-id="060f3-311">매개 변수</span><span class="sxs-lookup"><span data-stu-id="060f3-311">Parameters</span></span>
* <span data-ttu-id="060f3-312">제스처-제스처를 수행 하려면</span><span class="sxs-lookup"><span data-stu-id="060f3-312">gesture - The gesture to perform</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="060f3-313">Microsoft.PerceptionSimulation.ISimulatedHead</span><span class="sxs-lookup"><span data-stu-id="060f3-313">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="060f3-314">시뮬레이션 된 사람이의 머리를 설명 하는 인터페이스</span><span class="sxs-lookup"><span data-stu-id="060f3-314">Interface describing the head of the simulated human</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="060f3-315">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="060f3-315">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="060f3-316">미터 단위의 전 세계를 통해 관련 노드의 위치 검색</span><span class="sxs-lookup"><span data-stu-id="060f3-316">Retrieve the position of the node with relation to the world, in meters</span></span>

<span data-ttu-id="060f3-317">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span><span class="sxs-lookup"><span data-stu-id="060f3-317">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="060f3-318">시뮬레이션 된 헤드의 회전을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-318">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="060f3-319">양수 라디안 축을 찾을 때 시계 방향으로 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-319">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="060f3-320">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span><span class="sxs-lookup"><span data-stu-id="060f3-320">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="060f3-321">시뮬레이션 된 head의 지름을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-321">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="060f3-322">이 값은 head의 center (회전 지점)를 확인 하려면 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-322">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="060f3-323">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="060f3-323">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="060f3-324">현재 회전의 기준으로 시뮬레이션 된 헤드를 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-324">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="060f3-325">양수 라디안 축을 찾을 때 시계 방향으로 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-325">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="060f3-326">매개 변수</span><span class="sxs-lookup"><span data-stu-id="060f3-326">Parameters</span></span>
* <span data-ttu-id="060f3-327">회전-회전 크기</span><span class="sxs-lookup"><span data-stu-id="060f3-327">rotation - The amount to rotate</span></span>

### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="060f3-328">Microsoft.PerceptionSimulation.ISimulationRecording</span><span class="sxs-lookup"><span data-stu-id="060f3-328">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="060f3-329">재생에 대 한 로드를 기록 하는 단일 상호 작용 하기 위한 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-329">Interface for interacting with a single recording loaded for playback.</span></span>

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

<span data-ttu-id="060f3-330">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span><span class="sxs-lookup"><span data-stu-id="060f3-330">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="060f3-331">기록에 대 한 데이터 형식의 목록을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-331">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="060f3-332">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span><span class="sxs-lookup"><span data-stu-id="060f3-332">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="060f3-333">기록의 현재 상태를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-333">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="060f3-334">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span><span class="sxs-lookup"><span data-stu-id="060f3-334">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="060f3-335">재생을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-335">Start the playback.</span></span> <span data-ttu-id="060f3-336">재생을 일시 중지 된 위치에서 다시 시작 됩니다 기록을 일시 중지 하는 경우 중지 하는 경우에 재생 시작 부분에서 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-336">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="060f3-337">이미 재생 하는 경우이 호출은 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-337">If already playing, this call is ignored.</span></span>

<span data-ttu-id="060f3-338">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span><span class="sxs-lookup"><span data-stu-id="060f3-338">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="060f3-339">현재 위치에 있는 재생 일시 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-339">Pauses the playback at its current location.</span></span> <span data-ttu-id="060f3-340">녹음/녹화 중지 되 면 호출 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-340">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="060f3-341">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span><span class="sxs-lookup"><span data-stu-id="060f3-341">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="060f3-342">검색 기록에 지정된 된 시간 (초부터 100 나노초 간격) 및 해당 위치에서 일시 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-342">Seeks the recording to the specified time (in 100 nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="060f3-343">시간 기록의 끝 이면 마지막 프레임에서 일시 중지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-343">If the time is beyond the end of the recording, it is paused at the last frame.</span></span>

<span data-ttu-id="060f3-344">매개 변수</span><span class="sxs-lookup"><span data-stu-id="060f3-344">Parameters</span></span>
* <span data-ttu-id="060f3-345">틱-검색 하려는 경우</span><span class="sxs-lookup"><span data-stu-id="060f3-345">ticks - The time to which to seek</span></span>

<span data-ttu-id="060f3-346">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span><span class="sxs-lookup"><span data-stu-id="060f3-346">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="060f3-347">재생을 중지 하 고 시작 부분에 위치를 다시 설정</span><span class="sxs-lookup"><span data-stu-id="060f3-347">Stops the playback and resets the position to the beginning</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="060f3-348">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span><span class="sxs-lookup"><span data-stu-id="060f3-348">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="060f3-349">재생 중 상태 변경을 수신 하기 위한 인터페이스</span><span class="sxs-lookup"><span data-stu-id="060f3-349">Interface for receiving state changes during playback</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="060f3-350">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span><span class="sxs-lookup"><span data-stu-id="060f3-350">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="060f3-351">ISimulationRecording 재생 상태가 변경 되 면 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-351">Called when an ISimulationRecording's playback state has changed</span></span>

<span data-ttu-id="060f3-352">매개 변수</span><span class="sxs-lookup"><span data-stu-id="060f3-352">Parameters</span></span>
* <span data-ttu-id="060f3-353">newState-기록의 새 상태</span><span class="sxs-lookup"><span data-stu-id="060f3-353">newState - The new state of the recording</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="060f3-354">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="060f3-354">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="060f3-355">Perception 시뮬레이션 개체를 만들기 위한 루트 개체</span><span class="sxs-lookup"><span data-stu-id="060f3-355">Root object for creating Perception Simulation objects</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="060f3-356">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span><span class="sxs-lookup"><span data-stu-id="060f3-356">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="060f3-357">시뮬레이션 된 패킷을 생성 하 고 제공 된 싱크에서에 게 배달에 대 한 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-357">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="060f3-358">매개 변수</span><span class="sxs-lookup"><span data-stu-id="060f3-358">Parameters</span></span>
* <span data-ttu-id="060f3-359">싱크-생성 된 모든 패킷의 받을 싱크</span><span class="sxs-lookup"><span data-stu-id="060f3-359">sink - The sink that will receive all generated packets</span></span>

<span data-ttu-id="060f3-360">반환 값</span><span class="sxs-lookup"><span data-stu-id="060f3-360">Return value</span></span>

<span data-ttu-id="060f3-361">만든된 관리자</span><span class="sxs-lookup"><span data-stu-id="060f3-361">The created Manager</span></span>

<span data-ttu-id="060f3-362">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span><span class="sxs-lookup"><span data-stu-id="060f3-362">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="060f3-363">모든 받은 패킷에 지정된 된 경로에 있는 파일에 저장 하는 싱크를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-363">Create a sink which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="060f3-364">매개 변수</span><span class="sxs-lookup"><span data-stu-id="060f3-364">Parameters</span></span>
* <span data-ttu-id="060f3-365">경로-만들려는 파일의 경로</span><span class="sxs-lookup"><span data-stu-id="060f3-365">path - The path of the file to create</span></span>

<span data-ttu-id="060f3-366">반환 값</span><span class="sxs-lookup"><span data-stu-id="060f3-366">Return value</span></span>

<span data-ttu-id="060f3-367">만든된 싱크</span><span class="sxs-lookup"><span data-stu-id="060f3-367">The created sink</span></span>

<span data-ttu-id="060f3-368">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span><span class="sxs-lookup"><span data-stu-id="060f3-368">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="060f3-369">지정된 된 파일에서 기록 로드</span><span class="sxs-lookup"><span data-stu-id="060f3-369">Load a recording from the specified file</span></span>

<span data-ttu-id="060f3-370">매개 변수</span><span class="sxs-lookup"><span data-stu-id="060f3-370">Parameters</span></span>
* <span data-ttu-id="060f3-371">경로-로드할 파일의 경로</span><span class="sxs-lookup"><span data-stu-id="060f3-371">path - The path of the file to load</span></span>
* <span data-ttu-id="060f3-372">팩터리-필요한 경우에 ISimulationStreamSink 작성용 녹음/녹화를 사용한 팩터리</span><span class="sxs-lookup"><span data-stu-id="060f3-372">factory - A factory used by the recording for creating an ISimulationStreamSink when required</span></span>

<span data-ttu-id="060f3-373">반환 값</span><span class="sxs-lookup"><span data-stu-id="060f3-373">Return value</span></span>

<span data-ttu-id="060f3-374">로드 된 기록</span><span class="sxs-lookup"><span data-stu-id="060f3-374">The loaded recording</span></span>

<span data-ttu-id="060f3-375">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording (System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory, Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span><span class="sxs-lookup"><span data-stu-id="060f3-375">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="060f3-376">지정된 된 파일에서 기록 로드</span><span class="sxs-lookup"><span data-stu-id="060f3-376">Load a recording from the specified file</span></span>

<span data-ttu-id="060f3-377">매개 변수</span><span class="sxs-lookup"><span data-stu-id="060f3-377">Parameters</span></span>
* <span data-ttu-id="060f3-378">경로-로드할 파일의 경로</span><span class="sxs-lookup"><span data-stu-id="060f3-378">path - The path of the file to load</span></span>
* <span data-ttu-id="060f3-379">팩터리-필요한 경우에 ISimulationStreamSink 작성용 녹음/녹화를 사용한 팩터리</span><span class="sxs-lookup"><span data-stu-id="060f3-379">factory - A factory used by the recording for creating an ISimulationStreamSink when required</span></span>
* <span data-ttu-id="060f3-380">콜백-수신 하는 콜백을 regrading 기록의 상태 업데이트</span><span class="sxs-lookup"><span data-stu-id="060f3-380">callback - A callback which receives updates regrading the recording's status</span></span>

<span data-ttu-id="060f3-381">반환 값</span><span class="sxs-lookup"><span data-stu-id="060f3-381">Return value</span></span>

<span data-ttu-id="060f3-382">로드 된 기록</span><span class="sxs-lookup"><span data-stu-id="060f3-382">The loaded recording</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="060f3-383">Microsoft.PerceptionSimulation.StreamDataTypes</span><span class="sxs-lookup"><span data-stu-id="060f3-383">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="060f3-384">다양 한 유형의 스트림 데이터에 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-384">Describes the different types of stream data</span></span>

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

<span data-ttu-id="060f3-385">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span><span class="sxs-lookup"><span data-stu-id="060f3-385">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="060f3-386">스트림 데이터 형식이 없습니다를 나타내는 데 센티널 값</span><span class="sxs-lookup"><span data-stu-id="060f3-386">A sentinel value used to indicate no stream data types</span></span>

<span data-ttu-id="060f3-387">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span><span class="sxs-lookup"><span data-stu-id="060f3-387">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="060f3-388">위치 및 헤드의 방향에 대 한 데이터의 Stream</span><span class="sxs-lookup"><span data-stu-id="060f3-388">Stream of data regarding the position and orientation of the head</span></span>

<span data-ttu-id="060f3-389">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span><span class="sxs-lookup"><span data-stu-id="060f3-389">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="060f3-390">손으로 제스처와 위치에 대 한 데이터의 Stream</span><span class="sxs-lookup"><span data-stu-id="060f3-390">Stream of data regarding the position and gestures of hands</span></span>

<span data-ttu-id="060f3-391">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span><span class="sxs-lookup"><span data-stu-id="060f3-391">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="060f3-392">공간 매핑의 환경에 대 한 데이터의 Stream</span><span class="sxs-lookup"><span data-stu-id="060f3-392">Stream of data regarding spatial mapping of the environment</span></span>

<span data-ttu-id="060f3-393">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span><span class="sxs-lookup"><span data-stu-id="060f3-393">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="060f3-394">장치의 보정에 대 한 데이터의 Stream입니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-394">Stream of data regarding calibration of the device.</span></span> <span data-ttu-id="060f3-395">보정 패킷 시스템 원격 모드에만 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-395">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="060f3-396">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span><span class="sxs-lookup"><span data-stu-id="060f3-396">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="060f3-397">장치 환경에 대 한 데이터의 Stream</span><span class="sxs-lookup"><span data-stu-id="060f3-397">Stream of data regarding the environment of the device</span></span>

<span data-ttu-id="060f3-398">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span><span class="sxs-lookup"><span data-stu-id="060f3-398">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="060f3-399">모든 기록 된 데이터 형식을 나타내는 데 센티널 값</span><span class="sxs-lookup"><span data-stu-id="060f3-399">A sentinel value used to indicate all recorded data types</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="060f3-400">Microsoft.PerceptionSimulation.ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="060f3-400">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="060f3-401">시뮬레이션 스트림에서 데이터 패킷을 수신 하는 개체</span><span class="sxs-lookup"><span data-stu-id="060f3-401">An object that receives data packets from a simulation stream</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="060f3-402">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span><span class="sxs-lookup"><span data-stu-id="060f3-402">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="060f3-403">내부적으로 형식화 된 및 버전 관리 된 단일 패킷을 수신합니다</span><span class="sxs-lookup"><span data-stu-id="060f3-403">Receives a single packet, which is internally typed and versioned</span></span>

<span data-ttu-id="060f3-404">매개 변수</span><span class="sxs-lookup"><span data-stu-id="060f3-404">Parameters</span></span>
* <span data-ttu-id="060f3-405">length-패킷 길이</span><span class="sxs-lookup"><span data-stu-id="060f3-405">length - The length of the packet</span></span>
* <span data-ttu-id="060f3-406">패킷 데이터 패킷</span><span class="sxs-lookup"><span data-stu-id="060f3-406">packet - The data of the packet</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="060f3-407">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span><span class="sxs-lookup"><span data-stu-id="060f3-407">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="060f3-408">ISimulationStreamSink 만들어지는 개체</span><span class="sxs-lookup"><span data-stu-id="060f3-408">An object that creates ISimulationStreamSink</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="060f3-409">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span><span class="sxs-lookup"><span data-stu-id="060f3-409">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="060f3-410">ISimulationStreamSink의 단일 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="060f3-410">Creates a single instance of ISimulationStreamSink</span></span>

<span data-ttu-id="060f3-411">반환 값</span><span class="sxs-lookup"><span data-stu-id="060f3-411">Return value</span></span>

<span data-ttu-id="060f3-412">만든된 싱크</span><span class="sxs-lookup"><span data-stu-id="060f3-412">The created sink</span></span>
