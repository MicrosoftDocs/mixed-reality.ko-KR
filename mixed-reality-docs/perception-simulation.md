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
# <a name="perception-simulation"></a><span data-ttu-id="f796f-104">Perception 시뮬레이션</span><span class="sxs-lookup"><span data-stu-id="f796f-104">Perception simulation</span></span>

<span data-ttu-id="f796f-105">앱에 대 한 자동화 된 테스트를 작성 하 시겠습니까?</span><span class="sxs-lookup"><span data-stu-id="f796f-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="f796f-106">구성 요소 수준 단위 테스트 뿐만 아니라 실제로 사용자 앱에 종단 간 연습을 테스트 하 시겠습니까?</span><span class="sxs-lookup"><span data-stu-id="f796f-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="f796f-107">Perception 시뮬레이션은 원하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="f796f-108">Perception 시뮬레이션 라이브러리 휴먼 보내고 world 테스트를 자동화할 수 있도록 앱에 데이터를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-108">The Perception Simulation library sends human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="f796f-109">예를 들어 휴먼 구체적이 고 반복 가능한 위치로 확인 및 제스처를 수행 하는 다음 또는 동작 컨트롤러를 사용 하 여 입력을 시뮬레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-109">For example, you can simulate the input of a human looking to a specific, repeatable position and then performing a gesture or using a motion controller.</span></span>

<span data-ttu-id="f796f-110">Perception 시뮬레이션 실제 HoloLens, HoloLens 에뮬레이터에 이와 같은 시뮬레이션 된 입력을 보낼 수 있습니다 (첫 번째 gen) HoloLens 혼합 현실 포털을 사용 하 여 PC를 2 에뮬레이터를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator (1st gen), the HoloLens 2 Emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="f796f-111">Perception 혼합 현실 장치에서 실시간 센서를 무시 하 고 전송 하는 시뮬레이션 장치에서 실행 중인 응용 프로그램에 대 한 입력을 시뮬레이션 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="f796f-112">응용 프로그램은 항상 사용 하 고 실제 센서와 Perception 시뮬레이션을 사용 하 여 실행을 사용 하 여 실행 차이 구별할 수 없습니다. 동일한 Api 통해 이러한 입력된 이벤트를 수신 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-112">Applications receive these input events through the same APIs they always use and can't tell the difference between running with real sensors versus running with Perception Simulation.</span></span> <span data-ttu-id="f796f-113">Perception 시뮬레이션은 시뮬레이션 된 입력 HoloLens 가상 컴퓨터에 보낼 HoloLens 에뮬레이터에서 사용 하는 동일한 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-113">Perception Simulation is the same technology used by the HoloLens emulators to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="f796f-114">코드에서 시뮬레이션을 사용 하려면 IPerceptionSimulationManager 개체를 만들어 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-114">To begin using simulation in your code, start by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="f796f-115">이 개체에서 속성을 시뮬레이션 된 "사용자"를 헤드 위치, 손 모양 위치 및 제스처를 포함 하 여 제어 하는 명령을 실행할 수 있습니다 및 사용 하도록 설정 하 고 동작 컨트롤러를 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures, and you can enable and manipulate motion controllers.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="f796f-116">Perception 시뮬레이션에 대 한 Visual Studio 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="f796f-116">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="f796f-117">[HoloLens 에뮬레이터를 설치할](install-the-tools.md) 개발 PC의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-117">[Install the HoloLens emulator](install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="f796f-118">에뮬레이터는 Perception 시뮬레이션 하는 데 사용할 라이브러리를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-118">The emulator includes the libraries you will use for Perception Simulation.</span></span>
2. <span data-ttu-id="f796f-119">새 Visual Studio를 만들려면 C# 데스크톱 프로젝트 (콘솔 프로젝트를 시작 하려면 잘 작동).</span><span class="sxs-lookup"><span data-stu-id="f796f-119">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="f796f-120">다음 이진 파일을 프로젝트에 참조로 추가 (프로젝트-> 추가-> 참조...). %ProgramFiles (x86) %\Microsoft XDE에서에서 찾을 수 있습니다\\(버전)와 같은 **%ProgramFiles (x86) %\Microsoft XDE\\10.0.18362.0** HoloLens 2 에뮬레이터에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-120">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in %ProgramFiles(x86)%\Microsoft XDE\\(version), such as **%ProgramFiles(x86)%\Microsoft XDE\\10.0.18362.0** for the HoloLens 2 Emulator.</span></span>  <span data-ttu-id="f796f-121">(참고: 이진 파일에는 HoloLens 2 에뮬레이터 포함 되어 있지만 작동 하기도 Windows Mixed Reality에 대 한 바탕 화면입니다.) 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-121">(Note: although the binaries are part of the HoloLens 2 Emulator, they also work for Windows Mixed Reality on the desktop.) a.</span></span> <span data-ttu-id="f796f-122">PerceptionSimulationManager.Interop.dll-관리 되는 C# Perception 시뮬레이션에 대 한 래퍼입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-122">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="f796f-123">b.</span><span class="sxs-lookup"><span data-stu-id="f796f-123">b.</span></span> <span data-ttu-id="f796f-124">PerceptionSimulationRest.dll-HoloLens 또는 에뮬레이터에 웹 소켓 통신 채널을 설정 하기 위한 라이브러리입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-124">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="f796f-125">c.</span><span class="sxs-lookup"><span data-stu-id="f796f-125">c.</span></span> <span data-ttu-id="f796f-126">SimulationStream.Interop.dll-시뮬레이션에 대 한 공유 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-126">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="f796f-127">구현을 추가 프로젝트에 이진 PerceptionSimulationManager.dll를 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-127">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="f796f-128">먼저 프로젝트에는 이진 형식으로 추가 (프로젝트-> 추가-> 기존 항목...). 프로젝트 소스 폴더에 복사 하지 않습니다 고 링크로 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-128">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="f796f-129">![프로젝트에 링크로 PerceptionSimulationManager.dll 추가할](images/saveaslink.png) b.</span><span class="sxs-lookup"><span data-stu-id="f796f-129">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="f796f-130">있는지를 확인 한 다음 빌드 출력 폴더로 복사의 가져올 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-130">Then make sure that it get's copied to your output folder on build.</span></span> <span data-ttu-id="f796f-131">이진 파일에 대 한 속성 시트입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-131">This is in the property sheet for the binary .</span></span> <span data-ttu-id="f796f-132">![출력 디렉터리로 복사할 PerceptionSimulationManager.dll 표시](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="f796f-132">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>
5. <span data-ttu-id="f796f-133">활성 솔루션 플랫폼을 x64로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-133">Set your active solution platform to x64.</span></span>  <span data-ttu-id="f796f-134">() 사용 하 여 항목을 만드는 플랫폼 x64에 대 한 경우 Configuration Manager 이미 존재 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-134">(Use the Configuration Manager to create a Platform entry for x64 if one does not already exist.)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="f796f-135">IPerceptionSimulation Manager 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="f796f-135">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="f796f-136">시뮬레이션을 제어 하려면 IPerceptionSimulationManager 개체에서 검색 된 개체에 업데이트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-136">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="f796f-137">첫 번째 단계는 해당 개체를 가져오고 대상 장치 또는 에뮬레이터에 연결 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-137">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="f796f-138">장치 포털 단추를 클릭 하 여 에뮬레이터의 IP 주소를 가져올 수 있습니다는 [도구 모음](using-the-hololens-emulator.md)</span><span class="sxs-lookup"><span data-stu-id="f796f-138">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md)</span></span>

<span data-ttu-id="f796f-139">![열기 장치 포털 아이콘](images/emulator-deviceportal.png) **장치 포털 열기**: 에뮬레이터에서 HoloLens OS용 Windows 디바이스 포털을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-139">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>  <span data-ttu-id="f796f-140">Windows Mixed Reality를 검색할 수 있습니다 "업데이트 및 보안" 다음 "개발자"에 대 한 설정 앱에서에 "를 사용 하 여 연결:" "사용 장치 포털" 섹션</span><span class="sxs-lookup"><span data-stu-id="f796f-140">For Windows Mixed Reality, this can be retrieved in the Settings app under "Update & Security", then "For developers" in the "Connect using:" section under "Enable Device Portal."</span></span>  <span data-ttu-id="f796f-141">IP 주소와 포트를 모두 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-141">Be sure to note both the IP address and port.</span></span>

<span data-ttu-id="f796f-142">먼저 RestSimulationStreamSink 개체를 가져오는 RestSimulationStreamSink.Create 부르겠습니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-142">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="f796f-143">이 대상 장치 또는 에뮬레이터는 http 연결을 통해 제어 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-143">This is the target device or emulator that you will control over an http connection.</span></span> <span data-ttu-id="f796f-144">명령을 전달 되며에서 처리 합니다 [Windows Device Portal](using-the-windows-device-portal.md) 장치 또는 에뮬레이터에서 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-144">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="f796f-145">개체를 만들려고 해야 4 개의 매개 변수는:</span><span class="sxs-lookup"><span data-stu-id="f796f-145">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="f796f-146">대상 장치의 IP 주소 Uri uri (예: "http://123.123.123.123"또는"http://123.123.123.123:50080")</span><span class="sxs-lookup"><span data-stu-id="f796f-146">Uri uri - IP address of the target device (e.g., "http://123.123.123.123" or "http://123.123.123.123:50080")</span></span>
* <span data-ttu-id="f796f-147">System.Net.NetworkCredential 자격 증명-사용자 이름/암호에 연결 합니다 [Windows Device Portal](using-the-windows-device-portal.md) 대상 장치 또는 에뮬레이터에서 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-147">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="f796f-148">해당 로컬 주소를 통해 에뮬레이터에 연결 하는 경우 (예를 들어 168.*합니다.* . \*)를 같은 PC에서 자격 증명을 모두 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-148">If you are connecting to the emulator via its local address (e.g., 168.*.*.\*) on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="f796f-149">bool 기본-보통 우선 순위에서 낮은 우선 순위에 대해 false 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-149">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="f796f-150">일반적으로이 값을 설정 하려는 *true* 테스트를 제어할 수 있는 테스트 시나리오에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-150">You generally want to set this to *true* for test scenarios, which allows your test to take control.</span></span>  <span data-ttu-id="f796f-151">에뮬레이터와 Windows Mixed Reality 시뮬레이션 우선 순위가 낮은 연결을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-151">The emulator and Windows Mixed Reality simulation use low priority connections.</span></span>  <span data-ttu-id="f796f-152">테스트 연결을 낮은 우선 순위를 사용 하면 가장 최근에 설정 된 컨트롤에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-152">If your test also uses a low priority connection, the most recently established connection will be in control.</span></span>
* <span data-ttu-id="f796f-153">System.Threading.CancellationToken 토큰-비동기 작업을 취소할 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-153">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="f796f-154">두 번째는 IPerceptionSimulationManager 만들게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-154">Second you will create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="f796f-155">시뮬레이션을 제어 하는 데 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-155">This is the object you use to control simulation.</span></span> <span data-ttu-id="f796f-156">이 비동기 메서드에서 수행도 해야 함을 note 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-156">Note that this must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="f796f-157">시뮬레이션 된 사람을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-157">Control the simulated Human</span></span>

<span data-ttu-id="f796f-158">IPerceptionSimulationManager ISimulatedHuman 개체를 반환 하는 사람이 속성을 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-158">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="f796f-159">시뮬레이션 된 사람을 제어 하려면이 개체에 대 한 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-159">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="f796f-160">예를 들어 다음과 같은 가치를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-160">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="f796f-161">기본 샘플 C# 콘솔 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="f796f-161">Basic Sample C# console application</span></span>

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

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="f796f-162">샘플 확장 C# 콘솔 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="f796f-162">Extended Sample C# console application</span></span>

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

## <a name="note-on-6-dof-controllers"></a><span data-ttu-id="f796f-163">6-DOF 컨트롤러에서 note</span><span class="sxs-lookup"><span data-stu-id="f796f-163">Note on 6-DOF controllers</span></span>

<span data-ttu-id="f796f-164">모든 속성 시뮬레이션된 6 DOF 컨트롤러에서 메서드를 호출 하기 전에 컨트롤러를 활성화 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-164">Before calling any properties on methods on a simulated 6-DOF controller, you must activate the controller.</span></span>  <span data-ttu-id="f796f-165">이렇게 하지 않으면 예외가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-165">Not doing so will result in an exception.</span></span>  <span data-ttu-id="f796f-166">Windows 10부터 2019을 업데이트할 수 있습니다, 그리고 시뮬레이션 된 6 DOF 컨트롤러를 설치 하 고 SimulatedSixDofControllerStatus.Active ISimulatedSixDofController 개체의 Status 속성을 설정 하 여 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-166">Starting with the Windows 10 May 2019 Update, simulated 6-DOF controllers can be installed and activated by setting the Status property on the ISimulatedSixDofController object to SimulatedSixDofControllerStatus.Active.</span></span>
<span data-ttu-id="f796f-167">Windows 10 년 10 월 2018에서에서 업데이트 하 고 이전에 개별적으로 먼저 설치 해야 시뮬레이션된 6 DOF 컨트롤러 \Windows\System32 폴더에 있는 PerceptionSimulationDevice 도구를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-167">In the Windows 10 October 2018 Update and earlier, you must separately install a simulated 6-DOF controller first by calling the PerceptionSimulationDevice tool located in the \Windows\System32 folder.</span></span>  <span data-ttu-id="f796f-168">이 도구의 사용은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-168">The usage of this tool is as follows:</span></span>


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

<span data-ttu-id="f796f-169">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-169">For example</span></span>

```
    PerceptionSimulationDevice.exe i 6dof 1
```

<span data-ttu-id="f796f-170">지원 되는 동작은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-170">Supported actions are:</span></span>
* <span data-ttu-id="f796f-171">i = install</span><span class="sxs-lookup"><span data-stu-id="f796f-171">i = install</span></span>
* <span data-ttu-id="f796f-172">q = query</span><span class="sxs-lookup"><span data-stu-id="f796f-172">q = query</span></span>
* <span data-ttu-id="f796f-173">r = remove</span><span class="sxs-lookup"><span data-stu-id="f796f-173">r = remove</span></span>

<span data-ttu-id="f796f-174">지원 되는 인스턴스는 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-174">Supported instances are:</span></span>
* <span data-ttu-id="f796f-175">1 = 왼쪽된 6 DOF 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="f796f-175">1 = the left 6-DOF controller</span></span>
* <span data-ttu-id="f796f-176">2 = 오른쪽 6 DOF 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="f796f-176">2 = the right 6-DOF controller</span></span>

<span data-ttu-id="f796f-177">프로세스의 종료 코드는 (0 값을 반환 하는 데 사용) 하는 성공 또는 실패 (0이 아닌 반환 값) 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-177">The exit code of the process will indicate success (a zero return value) or failure (a non-zero return value).</span></span>  <span data-ttu-id="f796f-178">'Q' 작업을 사용 하 여 쿼리는 컨트롤러를 설치 하는 여부를 반환 값 영 (0) 컨트롤러를 아직 설치 하지 않은 경우 또는 됩니다 하나 (1)는 컨트롤러를 설치 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="f796f-178">When using the 'q' action to query whether or not a controller is installed, the return value will be zero (0) if the controller is not already installed or one (1) if the controller is installed.</span></span>

<span data-ttu-id="f796f-179">Windows 컨트롤러를 제거 하는 경우 10 년 10 월 2018 업데이트 또는 이전에 해제 API를 통해 먼저 다음 도구를 호출 하 PerceptionSimulationDevice 해당 상태를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-179">When removing a controller on the Windows 10 October 2018 Update or earlier, set its status to Off via the API first, then call the PerceptionSimulationDevice tool.</span></span>

<span data-ttu-id="f796f-180">이 도구는 관리자 권한으로 실행 해야 하는 참고 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-180">Note that this tool must be run as Administrator.</span></span>




## <a name="api-reference"></a><span data-ttu-id="f796f-181">API 참조</span><span class="sxs-lookup"><span data-stu-id="f796f-181">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="f796f-182">Microsoft.PerceptionSimulation.SimulatedDeviceType</span><span class="sxs-lookup"><span data-stu-id="f796f-182">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="f796f-183">시뮬레이션 된 장치 종류를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-183">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="f796f-184">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span><span class="sxs-lookup"><span data-stu-id="f796f-184">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="f796f-185">PerceptionSimulationManager에 대 한 기본 장치를 가상의 참조</span><span class="sxs-lookup"><span data-stu-id="f796f-185">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="f796f-186">Microsoft.PerceptionSimulation.HeadTrackerMode</span><span class="sxs-lookup"><span data-stu-id="f796f-186">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="f796f-187">헤드 추적기 모드를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-187">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="f796f-188">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span><span class="sxs-lookup"><span data-stu-id="f796f-188">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="f796f-189">기본 헤드를 추적 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-189">Default Head Tracking.</span></span> <span data-ttu-id="f796f-190">즉, 시스템 관리 모드 런타임 조건에 따라 최상의 헤드를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-190">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="f796f-191">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span><span class="sxs-lookup"><span data-stu-id="f796f-191">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="f796f-192">추적만 헤드 방향입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-192">Orientation Only Head Tracking.</span></span> <span data-ttu-id="f796f-193">즉, 추적된 위치를 신뢰할 수 있는 아닐 헤드 위치에 종속 된 일부 기능을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-193">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="f796f-194">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span><span class="sxs-lookup"><span data-stu-id="f796f-194">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="f796f-195">위치 헤드 추적 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-195">Positional Head Tracking.</span></span> <span data-ttu-id="f796f-196">즉, 추적 된 헤드 위치와 방향을 둘 다 신뢰할 수 있는</span><span class="sxs-lookup"><span data-stu-id="f796f-196">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="f796f-197">Microsoft.PerceptionSimulation.SimulatedGesture</span><span class="sxs-lookup"><span data-stu-id="f796f-197">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="f796f-198">시뮬레이션 된 제스처를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-198">Describes a simulated gesture</span></span>

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

<span data-ttu-id="f796f-199">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span><span class="sxs-lookup"><span data-stu-id="f796f-199">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="f796f-200">없는 제스처를 나타내는 데 센티널 값입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-200">A sentinel value used to indicate no gestures.</span></span>

<span data-ttu-id="f796f-201">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span><span class="sxs-lookup"><span data-stu-id="f796f-201">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="f796f-202">손가락 제스처를 눌렀습니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-202">A finger pressed gesture.</span></span>

<span data-ttu-id="f796f-203">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span><span class="sxs-lookup"><span data-stu-id="f796f-203">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="f796f-204">손가락 제스처를 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-204">A finger released gesture.</span></span>

<span data-ttu-id="f796f-205">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span><span class="sxs-lookup"><span data-stu-id="f796f-205">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="f796f-206">홈/시스템 제스처입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-206">The home/system gesture.</span></span>

<span data-ttu-id="f796f-207">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span><span class="sxs-lookup"><span data-stu-id="f796f-207">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="f796f-208">최대 유효 제스처입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-208">The maximum valid gesture.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a><span data-ttu-id="f796f-209">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span><span class="sxs-lookup"><span data-stu-id="f796f-209">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span></span>

<span data-ttu-id="f796f-210">시뮬레이션 된 6 DOF 컨트롤러의 가능한 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-210">The possible states of a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

<span data-ttu-id="f796f-211">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span><span class="sxs-lookup"><span data-stu-id="f796f-211">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span></span>

<span data-ttu-id="f796f-212">6-DOF 컨트롤러 꺼져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-212">The 6-DOF controller is turned off.</span></span>

<span data-ttu-id="f796f-213">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span><span class="sxs-lookup"><span data-stu-id="f796f-213">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span></span>

<span data-ttu-id="f796f-214">6-DOF 컨트롤러 켜져 있고 추적 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-214">The 6-DOF controller is turned on and tracked.</span></span>

<span data-ttu-id="f796f-215">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span><span class="sxs-lookup"><span data-stu-id="f796f-215">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span></span>

<span data-ttu-id="f796f-216">6-DOF 컨트롤러 켜져 있지만 추적할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-216">The 6-DOF controller is turned on but cannot be tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a><span data-ttu-id="f796f-217">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span><span class="sxs-lookup"><span data-stu-id="f796f-217">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span></span>

<span data-ttu-id="f796f-218">시뮬레이션 된 6 DOF 컨트롤러에서 지원 되는 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-218">The supported buttons on a simulated 6-DOF controller.</span></span>

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

<span data-ttu-id="f796f-219">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span><span class="sxs-lookup"><span data-stu-id="f796f-219">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span></span>

<span data-ttu-id="f796f-220">아니요 단추를 나타내는 데 센티널 값입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-220">A sentinel value used to indicate no buttons.</span></span>

<span data-ttu-id="f796f-221">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span><span class="sxs-lookup"><span data-stu-id="f796f-221">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span></span>

<span data-ttu-id="f796f-222">홈 단추를 눌렀습니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-222">The Home button is pressed.</span></span>

<span data-ttu-id="f796f-223">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span><span class="sxs-lookup"><span data-stu-id="f796f-223">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span></span>

<span data-ttu-id="f796f-224">메뉴 단추가 눌러져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-224">The Menu button is pressed.</span></span>

<span data-ttu-id="f796f-225">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span><span class="sxs-lookup"><span data-stu-id="f796f-225">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span></span>

<span data-ttu-id="f796f-226">그립 단추가 눌러져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-226">The Grip button is pressed.</span></span>

<span data-ttu-id="f796f-227">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span><span class="sxs-lookup"><span data-stu-id="f796f-227">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span></span>

<span data-ttu-id="f796f-228">터치 패드 눌러져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-228">The TouchPad is pressed.</span></span>

<span data-ttu-id="f796f-229">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span><span class="sxs-lookup"><span data-stu-id="f796f-229">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span></span>

<span data-ttu-id="f796f-230">선택 단추가 눌러져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-230">The Select button is pressed.</span></span>

<span data-ttu-id="f796f-231">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span><span class="sxs-lookup"><span data-stu-id="f796f-231">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span></span>

<span data-ttu-id="f796f-232">터치 패드 검사가 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-232">The TouchPad is touched.</span></span>

<span data-ttu-id="f796f-233">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span><span class="sxs-lookup"><span data-stu-id="f796f-233">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span></span>

<span data-ttu-id="f796f-234">스틱은 눌러져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-234">The Thumbstick is pressed.</span></span>

<span data-ttu-id="f796f-235">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span><span class="sxs-lookup"><span data-stu-id="f796f-235">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span></span>

<span data-ttu-id="f796f-236">최대 유효 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-236">The maximum valid button.</span></span>


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a><span data-ttu-id="f796f-237">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span><span class="sxs-lookup"><span data-stu-id="f796f-237">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span></span>

<span data-ttu-id="f796f-238">시뮬레이션 된 명사 보정 상태</span><span class="sxs-lookup"><span data-stu-id="f796f-238">The calibration state of the simulated eyes</span></span>

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

<span data-ttu-id="f796f-239">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span><span class="sxs-lookup"><span data-stu-id="f796f-239">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span></span>

<span data-ttu-id="f796f-240">눈 보정을 사용할 수 없는 경우</span><span class="sxs-lookup"><span data-stu-id="f796f-240">The eyes calibration is unavailable.</span></span>

<span data-ttu-id="f796f-241">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span><span class="sxs-lookup"><span data-stu-id="f796f-241">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span></span>

<span data-ttu-id="f796f-242">눈 보정 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-242">The eyes have been calibrated.</span></span>  <span data-ttu-id="f796f-243">이것은 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-243">This is the default value.</span></span>

<span data-ttu-id="f796f-244">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span><span class="sxs-lookup"><span data-stu-id="f796f-244">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span></span>

<span data-ttu-id="f796f-245">눈을 보정 되는 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-245">The eyes are being calibrated.</span></span>

<span data-ttu-id="f796f-246">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span><span class="sxs-lookup"><span data-stu-id="f796f-246">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span></span>

<span data-ttu-id="f796f-247">눈 위치를 조정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-247">The eyes need to be calibrated.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a><span data-ttu-id="f796f-248">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span><span class="sxs-lookup"><span data-stu-id="f796f-248">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span></span>

<span data-ttu-id="f796f-249">추적의 정확도 손 모양 아이콘이의 연결입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-249">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

<span data-ttu-id="f796f-250">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span><span class="sxs-lookup"><span data-stu-id="f796f-250">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span></span>

<span data-ttu-id="f796f-251">연결점 추적 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-251">The joint is not tracked.</span></span>

<span data-ttu-id="f796f-252">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span><span class="sxs-lookup"><span data-stu-id="f796f-252">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span></span>

<span data-ttu-id="f796f-253">공동 위치 유추 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-253">The joint position is inferred.</span></span>

<span data-ttu-id="f796f-254">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span><span class="sxs-lookup"><span data-stu-id="f796f-254">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span></span>

<span data-ttu-id="f796f-255">연결점 추적 완벽 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-255">The joint is fully tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a><span data-ttu-id="f796f-256">Microsoft.PerceptionSimulation.SimulatedHandPose</span><span class="sxs-lookup"><span data-stu-id="f796f-256">Microsoft.PerceptionSimulation.SimulatedHandPose</span></span>

<span data-ttu-id="f796f-257">추적의 정확도 손 모양 아이콘이의 연결입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-257">The tracking accuracy of a joint of the hand.</span></span>

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

<span data-ttu-id="f796f-258">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span><span class="sxs-lookup"><span data-stu-id="f796f-258">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span></span>

<span data-ttu-id="f796f-259">손 모양 아이콘이 손가락이 음 닫힌된 포즈를 반영 하도록 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-259">The hand's finger joints are configured to reflect a closed pose.</span></span>

<span data-ttu-id="f796f-260">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span><span class="sxs-lookup"><span data-stu-id="f796f-260">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span></span>

<span data-ttu-id="f796f-261">손 모양 아이콘이 손가락이 음을 열고 자세를 반영 하도록 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-261">The hand's finger joints are configured to reflect an open pose.</span></span>

<span data-ttu-id="f796f-262">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span><span class="sxs-lookup"><span data-stu-id="f796f-262">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span></span>

<span data-ttu-id="f796f-263">손 모양 아이콘이 손가락이 음 포인팅 포즈를 반영 하도록 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-263">The hand's finger joints are configured to reflect a pointing pose.</span></span>

<span data-ttu-id="f796f-264">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span><span class="sxs-lookup"><span data-stu-id="f796f-264">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span></span>

<span data-ttu-id="f796f-265">손 모양 아이콘이 손가락이 음 pinching 포즈를 반영 하도록 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-265">The hand's finger joints are configured to reflect a pinching pose.</span></span>

<span data-ttu-id="f796f-266">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span><span class="sxs-lookup"><span data-stu-id="f796f-266">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span></span>

<span data-ttu-id="f796f-267">SimulatedHandPose에 대 한 최대 유효 값입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-267">The maximum valid value for SimulatedHandPose.</span></span>


### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="f796f-268">Microsoft.PerceptionSimulation.PlaybackState</span><span class="sxs-lookup"><span data-stu-id="f796f-268">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="f796f-269">재생 하는 상태를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-269">Describes the state of a playback.</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="f796f-270">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span><span class="sxs-lookup"><span data-stu-id="f796f-270">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="f796f-271">녹음/녹화 중지 되 고 재생을 위해 준비 중인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-271">The recording is currently stopped and ready for playback.</span></span>

<span data-ttu-id="f796f-272">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span><span class="sxs-lookup"><span data-stu-id="f796f-272">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="f796f-273">현재 녹음/녹화 재생 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-273">The recording is currently playing.</span></span>

<span data-ttu-id="f796f-274">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span><span class="sxs-lookup"><span data-stu-id="f796f-274">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="f796f-275">녹음/녹화 현재 일시 중지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-275">The recording is currently paused.</span></span>

<span data-ttu-id="f796f-276">**Microsoft.PerceptionSimulation.PlaybackState.End**</span><span class="sxs-lookup"><span data-stu-id="f796f-276">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="f796f-277">녹음/녹화 끝에 도달 했습니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-277">The recording has reached the end.</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="f796f-278">Microsoft.PerceptionSimulation.Vector3</span><span class="sxs-lookup"><span data-stu-id="f796f-278">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="f796f-279">점 또는 3D 공간에서 벡터를 설명 하는 3 개 구성 요소가 벡터를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-279">Describes a 3 components vector, which might describe a point or a vector in 3D space.</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="f796f-280">**Microsoft.PerceptionSimulation.Vector3.X**</span><span class="sxs-lookup"><span data-stu-id="f796f-280">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="f796f-281">벡터의 X 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-281">The X component of the vector.</span></span>

<span data-ttu-id="f796f-282">**Microsoft.PerceptionSimulation.Vector3.Y**</span><span class="sxs-lookup"><span data-stu-id="f796f-282">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="f796f-283">벡터의 Y 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-283">The Y component of the vector.</span></span>

<span data-ttu-id="f796f-284">**Microsoft.PerceptionSimulation.Vector3.Z**</span><span class="sxs-lookup"><span data-stu-id="f796f-284">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="f796f-285">벡터의 Z 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-285">The Z component of the vector.</span></span>

<span data-ttu-id="f796f-286">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span><span class="sxs-lookup"><span data-stu-id="f796f-286">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="f796f-287">새 Vector3를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-287">Construct a new Vector3.</span></span>

<span data-ttu-id="f796f-288">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f796f-288">Parameters</span></span>
* <span data-ttu-id="f796f-289">x 벡터의-x 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-289">x - The x component of the vector.</span></span>
* <span data-ttu-id="f796f-290">y 벡터의-y 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-290">y - The y component of the vector.</span></span>
* <span data-ttu-id="f796f-291">z 벡터의-z 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-291">z - The z component of the vector.</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="f796f-292">Microsoft.PerceptionSimulation.Rotation3</span><span class="sxs-lookup"><span data-stu-id="f796f-292">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="f796f-293">3 개 구성 요소가 회전을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-293">Describes a 3 components rotation.</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="f796f-294">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span><span class="sxs-lookup"><span data-stu-id="f796f-294">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="f796f-295">회전의 피치 구성 요소 X 축을 중심으로 축소 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-295">The Pitch component of the Rotation, down around the X axis.</span></span>

<span data-ttu-id="f796f-296">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span><span class="sxs-lookup"><span data-stu-id="f796f-296">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="f796f-297">Y 축 중심 오른쪽 회전 요 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-297">The Yaw component of the Rotation, right around the Y axis.</span></span>

<span data-ttu-id="f796f-298">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span><span class="sxs-lookup"><span data-stu-id="f796f-298">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="f796f-299">Z 축 중심 오른쪽 회전의 롤포워드 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-299">The Roll component of the Rotation, right around the Z axis.</span></span>

<span data-ttu-id="f796f-300">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span><span class="sxs-lookup"><span data-stu-id="f796f-300">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="f796f-301">새 Rotation3를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-301">Construct a new Rotation3.</span></span>

<span data-ttu-id="f796f-302">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f796f-302">Parameters</span></span>
* <span data-ttu-id="f796f-303">피치-피치 구성 요소를 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-303">pitch - The pitch component of the Rotation.</span></span>
* <span data-ttu-id="f796f-304">요-요 구성 요소를 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-304">yaw - The yaw component of the Rotation.</span></span>
* <span data-ttu-id="f796f-305">롤포워드-롤포워드 구성 요소를 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-305">roll - The roll component of the Rotation.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a><span data-ttu-id="f796f-306">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span><span class="sxs-lookup"><span data-stu-id="f796f-306">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span></span>

<span data-ttu-id="f796f-307">시뮬레이션된 손 모양에 대 한 공동 구성을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-307">Describes the configuration of a joint on a simulated hand.</span></span>

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

<span data-ttu-id="f796f-308">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span><span class="sxs-lookup"><span data-stu-id="f796f-308">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span></span>

<span data-ttu-id="f796f-309">연결점의 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-309">The position of the joint.</span></span>

<span data-ttu-id="f796f-310">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span><span class="sxs-lookup"><span data-stu-id="f796f-310">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span></span>

<span data-ttu-id="f796f-311">연결점의 회전입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-311">The rotation of the joint.</span></span>

<span data-ttu-id="f796f-312">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span><span class="sxs-lookup"><span data-stu-id="f796f-312">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span></span>

<span data-ttu-id="f796f-313">추적의 정확도 연결점입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-313">The tracking accuracy of the joint.</span></span>


### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="f796f-314">Microsoft.PerceptionSimulation.Frustum</span><span class="sxs-lookup"><span data-stu-id="f796f-314">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="f796f-315">보기 꼭지점이 절 두 체를, 카메라에서 일반적으로 사용 하는 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-315">Describes a view frustum, as typically used by a camera.</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="f796f-316">**Microsoft.PerceptionSimulation.Frustum.Near**</span><span class="sxs-lookup"><span data-stu-id="f796f-316">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="f796f-317">하면 프러스텀에 포함 된 최소 거리입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-317">The minimum distance that is contained in the frustum.</span></span>

<span data-ttu-id="f796f-318">**Microsoft.PerceptionSimulation.Frustum.Far**</span><span class="sxs-lookup"><span data-stu-id="f796f-318">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="f796f-319">하면 프러스텀에 포함 된 최대 거리입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-319">The maximum distance that is contained in the frustum.</span></span>

<span data-ttu-id="f796f-320">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span><span class="sxs-lookup"><span data-stu-id="f796f-320">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="f796f-321">가로 보기의 필드 (PI 보다 작음) 라디안에서 하면 프러스텀입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-321">The horizontal field of view of the frustum, in radians (less than PI).</span></span>

<span data-ttu-id="f796f-322">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="f796f-322">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="f796f-323">가로 뷰 필드를 세로 보기 필드의 비율입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-323">The ratio of horizontal field of view to vertical field of view.</span></span>

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="f796f-324">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="f796f-324">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="f796f-325">장치를 제어 하는 데 패킷을 생성 하는 것에 대 한 루트입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-325">Root for generating the packets used to control a device.</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="f796f-326">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span><span class="sxs-lookup"><span data-stu-id="f796f-326">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="f796f-327">시뮬레이션 된 사람 및 시뮬레이션된 세계를 해석 하는 시뮬레이션 된 장치 개체를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-327">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="f796f-328">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span><span class="sxs-lookup"><span data-stu-id="f796f-328">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="f796f-329">시뮬레이션 된 사람을 제어 하는 개체를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-329">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="f796f-330">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span><span class="sxs-lookup"><span data-stu-id="f796f-330">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="f796f-331">시뮬레이션을 기본 상태로 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-331">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="f796f-332">Microsoft.PerceptionSimulation.ISimulatedDevice</span><span class="sxs-lookup"><span data-stu-id="f796f-332">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="f796f-333">시뮬레이션 된 전 세계 및 시뮬레이션 된 사람을 해석 하는 장치를 설명 하는 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f796f-333">Interface describing the device which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="f796f-334">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span><span class="sxs-lookup"><span data-stu-id="f796f-334">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="f796f-335">시뮬레이션된 된 장치에서 Head Tracker를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-335">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="f796f-336">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span><span class="sxs-lookup"><span data-stu-id="f796f-336">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="f796f-337">시뮬레이션된 된 장치에서 직접 Tracker를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-337">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="f796f-338">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span><span class="sxs-lookup"><span data-stu-id="f796f-338">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="f796f-339">제공 된 장치 유형과 일치 하도록 시뮬레이션 된 장치의 속성을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-339">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="f796f-340">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f796f-340">Parameters</span></span>
* <span data-ttu-id="f796f-341">입력-시뮬레이션 된 장치의 새 유형</span><span class="sxs-lookup"><span data-stu-id="f796f-341">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="f796f-342">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span><span class="sxs-lookup"><span data-stu-id="f796f-342">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="f796f-343">시뮬레이션 된 장치를 시뮬레이션 된 사람이의 머리를 추적 하는 부분을 설명 하는 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-343">Interface describing the portion of the simulated device that tracks the head of the simulated human.</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="f796f-344">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="f796f-344">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="f796f-345">검색 하 고 현재 헤드 추적기 모드를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-345">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="f796f-346">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span><span class="sxs-lookup"><span data-stu-id="f796f-346">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="f796f-347">시뮬레이션 된 장치를 시뮬레이션 된 사람을 추적 하는 부분을 설명 하는 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f796f-347">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

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

<span data-ttu-id="f796f-348">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="f796f-348">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="f796f-349">미터 단위의 전 세계를 통해 관련 노드의 위치를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-349">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="f796f-350">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span><span class="sxs-lookup"><span data-stu-id="f796f-350">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="f796f-351">검색 하 고 헤드의 가운데를 기준으로 시뮬레이션 된 직접 추적기의 위치를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-351">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="f796f-352">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span><span class="sxs-lookup"><span data-stu-id="f796f-352">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="f796f-353">검색 하 고 시뮬레이션 된 직접 추적기의 아래쪽 피치를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-353">Retrieve and set the downward pitch of the simulated hand tracker.</span></span>

<span data-ttu-id="f796f-354">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span><span class="sxs-lookup"><span data-stu-id="f796f-354">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="f796f-355">검색 및 시뮬레이션 된 직접 추적기의 하면 프러스텀을 무시할지 여부를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-355">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="f796f-356">무시 된 경우 두 게 항상 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-356">When ignored, both hands are always visible.</span></span> <span data-ttu-id="f796f-357">없습니다 (기본값)를 무시 하는 경우는 표시 직접 추적기의 하면 프러스텀 있는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-357">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="f796f-358">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span><span class="sxs-lookup"><span data-stu-id="f796f-358">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="f796f-359">검색 및 실습 시뮬레이션된 직접 추적기에 표시 되는지 확인 하는 데 꼭지점이 절 두 체 속성을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-359">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="f796f-360">Microsoft.PerceptionSimulation.ISimulatedHuman</span><span class="sxs-lookup"><span data-stu-id="f796f-360">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="f796f-361">시뮬레이션 된 사람을 제어 하기 위한 상위 수준 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-361">Top level interface for controlling the simulated human.</span></span>

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

<span data-ttu-id="f796f-362">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="f796f-362">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="f796f-363">검색 하 고 전 세계를 미터 단위로 통해 관련 노드의 위치를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-363">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="f796f-364">위치는 사람이 feet 중앙 지점에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-364">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="f796f-365">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span><span class="sxs-lookup"><span data-stu-id="f796f-365">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="f796f-366">검색 및 전 세계의 방향을 시뮬레이션 된 얼굴을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-366">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="f796f-367">음의 Z 축을 0 라디안 직면 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-367">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="f796f-368">Y 축에 대 한 양의 라디안을 시계 방향으로 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-368">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="f796f-369">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span><span class="sxs-lookup"><span data-stu-id="f796f-369">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="f796f-370">검색 하 고 미터에서 시뮬레이션 된 사람이의 높이 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-370">Retrieve and set the height of the simulated human, in meters.</span></span>

<span data-ttu-id="f796f-371">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span><span class="sxs-lookup"><span data-stu-id="f796f-371">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="f796f-372">시뮬레이션 된 사람이의 왼쪽을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-372">Retrieve the left hand of the simulated human.</span></span>

<span data-ttu-id="f796f-373">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span><span class="sxs-lookup"><span data-stu-id="f796f-373">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="f796f-374">시뮬레이션 된 사람이의 오른쪽 위를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-374">Retrieve the right hand of the simulated human.</span></span>

<span data-ttu-id="f796f-375">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span><span class="sxs-lookup"><span data-stu-id="f796f-375">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="f796f-376">시뮬레이션 된 사람이의 머리를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-376">Retrieve the head of the simulated human.</span></span>

<span data-ttu-id="f796f-377">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="f796f-377">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="f796f-378">시뮬레이션 된 사람이 미터 단위로, 현재 위치를 기준으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-378">Move the simulated human relative to its current position, in meters.</span></span>

<span data-ttu-id="f796f-379">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f796f-379">Parameters</span></span>
* <span data-ttu-id="f796f-380">번역 번역에 현재 위치를 기준으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-380">translation - The translation to move, relative to current position.</span></span>

<span data-ttu-id="f796f-381">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span><span class="sxs-lookup"><span data-stu-id="f796f-381">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="f796f-382">Y 축에 대 한 시계 방향으로 현재 방향 기준으로 시뮬레이션 된 사람이 회전</span><span class="sxs-lookup"><span data-stu-id="f796f-382">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="f796f-383">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f796f-383">Parameters</span></span>
* <span data-ttu-id="f796f-384">라디안으로-Y 축을 중심으로 회전할 양입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-384">radians - The amount to rotate around the Y axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a><span data-ttu-id="f796f-385">Microsoft.PerceptionSimulation.ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="f796f-385">Microsoft.PerceptionSimulation.ISimulatedHuman2</span></span>

<span data-ttu-id="f796f-386">ISimulatedHuman2 ISimulatedHuman 캐스팅 하 여 추가 속성을 사용할 수</span><span class="sxs-lookup"><span data-stu-id="f796f-386">Additional properties are available by casting the ISimulatedHuman to ISimulatedHuman2</span></span>

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

<span data-ttu-id="f796f-387">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span><span class="sxs-lookup"><span data-stu-id="f796f-387">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span></span>

<span data-ttu-id="f796f-388">왼쪽된 6 DOF 컨트롤러를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-388">Retrieve the left 6-DOF controller.</span></span>

<span data-ttu-id="f796f-389">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span><span class="sxs-lookup"><span data-stu-id="f796f-389">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span></span>

<span data-ttu-id="f796f-390">오른쪽 6 DOF 컨트롤러를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-390">Retrieve the right 6-DOF controller.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="f796f-391">Microsoft.PerceptionSimulation.ISimulatedHand</span><span class="sxs-lookup"><span data-stu-id="f796f-391">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="f796f-392">시뮬레이션 된 사용자의 직접을 설명 하는 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f796f-392">Interface describing a hand of the simulated human</span></span>

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

<span data-ttu-id="f796f-393">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="f796f-393">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="f796f-394">미터 단위의 전 세계를 통해 관련 노드의 위치를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-394">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="f796f-395">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span><span class="sxs-lookup"><span data-stu-id="f796f-395">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="f796f-396">검색 및 미터에서 사람을 기준으로 시뮬레이션 된 손 모양 아이콘이 위치를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-396">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="f796f-397">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span><span class="sxs-lookup"><span data-stu-id="f796f-397">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="f796f-398">검색 하 고 손 모양 아이콘이 현재 활성화 되어 있는지 여부를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-398">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="f796f-399">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span><span class="sxs-lookup"><span data-stu-id="f796f-399">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="f796f-400">손 모양 아이콘이 (즉, 인지는 HandTracker에서 검색할 수는 위치) SimulatedDevice에 현재 표시 되는지 여부를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-400">Retrieve whether the hand is currently visible to the SimulatedDevice (ie, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="f796f-401">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span><span class="sxs-lookup"><span data-stu-id="f796f-401">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="f796f-402">SimulatedDevice를 볼 수 있도록 손 모양 아이콘이 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-402">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="f796f-403">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="f796f-403">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="f796f-404">미터 단위로, 현재 위치를 기준으로 시뮬레이션 된 손 모양 아이콘이 위치를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-404">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="f796f-405">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f796f-405">Parameters</span></span>
* <span data-ttu-id="f796f-406">변환-시뮬레이션 된 손 모양 아이콘이 변환할 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-406">translation - The amount to translate the simulated hand.</span></span>

<span data-ttu-id="f796f-407">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span><span class="sxs-lookup"><span data-stu-id="f796f-407">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="f796f-408">시뮬레이션 된 손 모양 아이콘이 사용 하 여 제스처를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-408">Perform a gesture using the simulated hand.</span></span>  <span data-ttu-id="f796f-409">만 검색 됩니다 시스템 손 모양 아이콘이 사용 되는 경우.</span><span class="sxs-lookup"><span data-stu-id="f796f-409">It will only be detected by the system if the hand is enabled.</span></span>

<span data-ttu-id="f796f-410">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f796f-410">Parameters</span></span>
* <span data-ttu-id="f796f-411">제스처-제스처를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-411">gesture - The gesture to perform.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand2"></a><span data-ttu-id="f796f-412">Microsoft.PerceptionSimulation.ISimulatedHand2</span><span class="sxs-lookup"><span data-stu-id="f796f-412">Microsoft.PerceptionSimulation.ISimulatedHand2</span></span>

<span data-ttu-id="f796f-413">ISimulatedHand ISimulatedHand2 캐스팅 하 여 추가 속성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-413">Additional properties are available by casting an ISimulatedHand to ISimulatedHand2.</span></span>
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

<span data-ttu-id="f796f-414">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span><span class="sxs-lookup"><span data-stu-id="f796f-414">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span></span>

<span data-ttu-id="f796f-415">검색 또는 시뮬레이션 된 손 모양 아이콘이의 회전 각도 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-415">Retrieve or set the rotation of the simulated hand.</span></span>  <span data-ttu-id="f796f-416">양수 라디안 축을 찾을 때 시계 방향으로 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-416">Positive radians rotate clockwise when looking along the axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand3"></a><span data-ttu-id="f796f-417">Microsoft.PerceptionSimulation.ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="f796f-417">Microsoft.PerceptionSimulation.ISimulatedHand3</span></span>

<span data-ttu-id="f796f-418">ISimulatedHand ISimulatedHand3 캐스팅 하 여 추가 속성을 사용할 수</span><span class="sxs-lookup"><span data-stu-id="f796f-418">Additional properties are available by casting an ISimulatedHand to ISimulatedHand3</span></span>
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

<span data-ttu-id="f796f-419">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="f796f-419">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span></span>

<span data-ttu-id="f796f-420">지정 된 연결점에 대 한 공동 구성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-420">Get the joint configuration for the specified joint.</span></span>

<span data-ttu-id="f796f-421">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="f796f-421">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span></span>

<span data-ttu-id="f796f-422">지정 된 연결점에 대 한 공동 구성을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-422">Set the joint configuration for the specified joint.</span></span>

<span data-ttu-id="f796f-423">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span><span class="sxs-lookup"><span data-stu-id="f796f-423">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span></span>

<span data-ttu-id="f796f-424">손 모양 아이콘이 애니메이션 효과를 주는 선택적 플래그를 사용 하 여 알려진된 포즈를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-424">Set the hand to a known pose with an optional flag to animate.</span></span>  <span data-ttu-id="f796f-425">참고: 즉시 해당 최종 joint 구성을 반영 하는 음 바뀌지는지 않습니다 애니메이션 효과 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-425">Note: animating won't result in joints immediately reflecting their final joint configurations.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="f796f-426">Microsoft.PerceptionSimulation.ISimulatedHead</span><span class="sxs-lookup"><span data-stu-id="f796f-426">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="f796f-427">시뮬레이션 된 사람이의 머리를 설명 하는 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-427">Interface describing the head of the simulated human.</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="f796f-428">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="f796f-428">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="f796f-429">미터 단위의 전 세계를 통해 관련 노드의 위치를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-429">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="f796f-430">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span><span class="sxs-lookup"><span data-stu-id="f796f-430">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="f796f-431">시뮬레이션 된 헤드의 회전을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-431">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="f796f-432">양수 라디안 축을 찾을 때 시계 방향으로 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-432">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="f796f-433">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span><span class="sxs-lookup"><span data-stu-id="f796f-433">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="f796f-434">시뮬레이션 된 head의 지름을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-434">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="f796f-435">이 값은 head의 center (회전 지점)를 확인 하려면 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-435">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="f796f-436">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="f796f-436">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="f796f-437">현재 회전의 기준으로 시뮬레이션 된 헤드를 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-437">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="f796f-438">양수 라디안 축을 찾을 때 시계 방향으로 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-438">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="f796f-439">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f796f-439">Parameters</span></span>
* <span data-ttu-id="f796f-440">회전-으로 회전할 양입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-440">rotation - The amount to rotate.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead2"></a><span data-ttu-id="f796f-441">Microsoft.PerceptionSimulation.ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="f796f-441">Microsoft.PerceptionSimulation.ISimulatedHead2</span></span>

<span data-ttu-id="f796f-442">ISimulatedHead ISimulatedHead2 캐스팅 하 여 추가 속성을 사용할 수</span><span class="sxs-lookup"><span data-stu-id="f796f-442">Additional properties are available by casting an ISimulatedHead to ISimulatedHead2</span></span>

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

<span data-ttu-id="f796f-443">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span><span class="sxs-lookup"><span data-stu-id="f796f-443">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span></span>

<span data-ttu-id="f796f-444">시뮬레이션 된 사람이의 시점을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-444">Retrieve the eyes of the simulated human.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a><span data-ttu-id="f796f-445">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span><span class="sxs-lookup"><span data-stu-id="f796f-445">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span></span>

<span data-ttu-id="f796f-446">시뮬레이션 된 사용자와 연결 된 6 DOF 컨트롤러를 설명 하는 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-446">Interface describing a 6-DOF controller associated with the simulated human.</span></span>

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

<span data-ttu-id="f796f-447">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="f796f-447">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span></span>

<span data-ttu-id="f796f-448">미터 단위의 전 세계를 통해 관련 노드의 위치를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-448">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="f796f-449">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span><span class="sxs-lookup"><span data-stu-id="f796f-449">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span></span>

<span data-ttu-id="f796f-450">검색 또는 컨트롤러의 현재 상태를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-450">Retrieve or set the current state of the controller.</span></span>  <span data-ttu-id="f796f-451">컨트롤러의 상태를 Off 이동, 회전 또는 키를 눌러 호출 전에 단추 성공할 이외의 값으로 설정 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-451">The controller status must be set to a value other than Off before any calls to move, rotate or press buttons will succeed.</span></span>

<span data-ttu-id="f796f-452">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span><span class="sxs-lookup"><span data-stu-id="f796f-452">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span></span>

<span data-ttu-id="f796f-453">검색 또는 미터에서 사람을 기준으로 시뮬레이션 된 컨트롤러의 위치를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-453">Retrieve or set the position of the simulated controller relative to the human, in meters.</span></span>

<span data-ttu-id="f796f-454">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span><span class="sxs-lookup"><span data-stu-id="f796f-454">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span></span>

<span data-ttu-id="f796f-455">검색 또는 시뮬레이션 된 컨트롤러의 방향을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-455">Retrieve or set the orientation of the simulated controller.</span></span>

<span data-ttu-id="f796f-456">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="f796f-456">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="f796f-457">시뮬레이션 된 컨트롤러의 현재 위치, 미터 단위에서를 기준으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-457">Move the position of the simulated controller relative to its current position, in meters.</span></span>

<span data-ttu-id="f796f-458">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f796f-458">Parameters</span></span>
* <span data-ttu-id="f796f-459">변환-시뮬레이션 된 컨트롤러를 변환할 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-459">translation - The amount to translate the simulated controller.</span></span>

<span data-ttu-id="f796f-460">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="f796f-460">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="f796f-461">시뮬레이션 된 컨트롤러에서 단추를 누르십시오.</span><span class="sxs-lookup"><span data-stu-id="f796f-461">Press a button on the simulated controller.</span></span>  <span data-ttu-id="f796f-462">만 검색 됩니다 시스템에서 컨트롤러를 사용 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="f796f-462">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="f796f-463">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f796f-463">Parameters</span></span>
* <span data-ttu-id="f796f-464">단추-단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-464">button - The button to press.</span></span>

<span data-ttu-id="f796f-465">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="f796f-465">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="f796f-466">시뮬레이션 된 컨트롤러에서 단추를 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-466">Release a button on the simulated controller.</span></span>  <span data-ttu-id="f796f-467">만 검색 됩니다 시스템에서 컨트롤러를 사용 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="f796f-467">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="f796f-468">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f796f-468">Parameters</span></span>
* <span data-ttu-id="f796f-469">단추-해제 하려면 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-469">button - The button to release.</span></span>

<span data-ttu-id="f796f-470">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="f796f-470">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**</span></span>

<span data-ttu-id="f796f-471">시뮬레이션 된 컨트롤러의 터치 패드에 시뮬레이션 된 손가락의 위치를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-471">Get the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="f796f-472">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f796f-472">Parameters</span></span>
* <span data-ttu-id="f796f-473">x 손가락의-가로 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-473">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="f796f-474">y 손가락의-세로 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-474">y - The vertical position of the finger.</span></span>

<span data-ttu-id="f796f-475">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span><span class="sxs-lookup"><span data-stu-id="f796f-475">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span></span>

<span data-ttu-id="f796f-476">시뮬레이션 된 컨트롤러의 터치 패드에 시뮬레이트된 손가락의 위치를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-476">Set the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="f796f-477">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f796f-477">Parameters</span></span>
* <span data-ttu-id="f796f-478">x 손가락의-가로 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-478">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="f796f-479">y 손가락의-세로 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-479">y - The vertical position of the finger.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a><span data-ttu-id="f796f-480">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="f796f-480">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span></span>

<span data-ttu-id="f796f-481">추가 속성 및 메서드를 사용할 수 있습니다는 ISimulatedSixDofController ISimulatedSixDofController2 캐스팅 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-481">Additional properties and methods are available by casting an ISimulatedSixDofController to ISimulatedSixDofController2</span></span>

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

<span data-ttu-id="f796f-482">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="f796f-482">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**</span></span>

<span data-ttu-id="f796f-483">시뮬레이션 된 컨트롤러에서 시뮬레이션 된 스틱의 위치를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-483">Get the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="f796f-484">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f796f-484">Parameters</span></span>
* <span data-ttu-id="f796f-485">x 스틱의-가로 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-485">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="f796f-486">y 스틱의-세로 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-486">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="f796f-487">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span><span class="sxs-lookup"><span data-stu-id="f796f-487">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span></span>

<span data-ttu-id="f796f-488">시뮬레이션 된 컨트롤러에서 시뮬레이션 된 엄지 스틱의 위치를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-488">Set the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="f796f-489">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f796f-489">Parameters</span></span>
* <span data-ttu-id="f796f-490">x 스틱의-가로 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-490">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="f796f-491">y 스틱의-세로 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-491">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="f796f-492">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span><span class="sxs-lookup"><span data-stu-id="f796f-492">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span></span>

<span data-ttu-id="f796f-493">검색 또는 시뮬레이션 된 컨트롤러의 배터리 수준을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-493">Retrieve or set the battery level of the simulated controller.</span></span>  <span data-ttu-id="f796f-494">값은 0.0 보다 커야 100.0 보다 작거나 같음.</span><span class="sxs-lookup"><span data-stu-id="f796f-494">The value must be greater than 0.0 and less than or equal to 100.0.</span></span>


### <a name="microsoftperceptionsimulationisimulatedeyes"></a><span data-ttu-id="f796f-495">Microsoft.PerceptionSimulation.ISimulatedEyes</span><span class="sxs-lookup"><span data-stu-id="f796f-495">Microsoft.PerceptionSimulation.ISimulatedEyes</span></span>

<span data-ttu-id="f796f-496">시뮬레이션 된 사람이의 시점을 설명 하는 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-496">Interface describing the eyes of the simulated human.</span></span>

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

<span data-ttu-id="f796f-497">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span><span class="sxs-lookup"><span data-stu-id="f796f-497">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span></span>

<span data-ttu-id="f796f-498">시뮬레이션 된 명사 회전을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-498">Retrieve the rotation of the simulated eyes.</span></span> <span data-ttu-id="f796f-499">양수 라디안 축을 찾을 때 시계 방향으로 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-499">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="f796f-500">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="f796f-500">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="f796f-501">현재 회전의 기준으로 시뮬레이션 된 눈을 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-501">Rotate the simulated eyes relative to its current rotation.</span></span> <span data-ttu-id="f796f-502">양수 라디안 축을 찾을 때 시계 방향으로 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-502">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="f796f-503">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f796f-503">Parameters</span></span>
* <span data-ttu-id="f796f-504">회전-으로 회전할 양입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-504">rotation - The amount to rotate.</span></span>

<span data-ttu-id="f796f-505">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span><span class="sxs-lookup"><span data-stu-id="f796f-505">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span></span>

<span data-ttu-id="f796f-506">시뮬레이션 된 명사 보정 상태를 가져오거나 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-506">Retrieves or sets the calibration state of the simulated eyes.</span></span>

<span data-ttu-id="f796f-507">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="f796f-507">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span></span>

<span data-ttu-id="f796f-508">미터 단위의 전 세계를 통해 관련 노드의 위치를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-508">Retrieve the position of the node with relation to the world, in meters.</span></span>


### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="f796f-509">Microsoft.PerceptionSimulation.ISimulationRecording</span><span class="sxs-lookup"><span data-stu-id="f796f-509">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="f796f-510">재생에 대 한 로드를 기록 하는 단일 상호 작용 하기 위한 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-510">Interface for interacting with a single recording loaded for playback.</span></span>

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

<span data-ttu-id="f796f-511">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span><span class="sxs-lookup"><span data-stu-id="f796f-511">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="f796f-512">기록에 대 한 데이터 형식의 목록을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-512">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="f796f-513">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span><span class="sxs-lookup"><span data-stu-id="f796f-513">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="f796f-514">기록의 현재 상태를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-514">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="f796f-515">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span><span class="sxs-lookup"><span data-stu-id="f796f-515">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="f796f-516">재생을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-516">Start the playback.</span></span> <span data-ttu-id="f796f-517">재생을 일시 중지 된 위치에서 다시 시작 됩니다 기록을 일시 중지 하는 경우 중지 하는 경우에 재생 시작 부분에서 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-517">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="f796f-518">이미 재생 하는 경우이 호출은 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-518">If already playing, this call is ignored.</span></span>

<span data-ttu-id="f796f-519">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span><span class="sxs-lookup"><span data-stu-id="f796f-519">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="f796f-520">현재 위치에 있는 재생 일시 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-520">Pauses the playback at its current location.</span></span> <span data-ttu-id="f796f-521">녹음/녹화 중지 되 면 호출 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-521">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="f796f-522">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span><span class="sxs-lookup"><span data-stu-id="f796f-522">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="f796f-523">검색 기록에 지정된 된 시간 (초부터 100 나노초 간격) 및 해당 위치에서 일시 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-523">Seeks the recording to the specified time (in 100 nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="f796f-524">시간 기록의 끝 이면 마지막 프레임에서 일시 중지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-524">If the time is beyond the end of the recording, it is paused at the last frame.</span></span>

<span data-ttu-id="f796f-525">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f796f-525">Parameters</span></span>
* <span data-ttu-id="f796f-526">틱-검색 하려는 경우.</span><span class="sxs-lookup"><span data-stu-id="f796f-526">ticks - The time to which to seek.</span></span>

<span data-ttu-id="f796f-527">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span><span class="sxs-lookup"><span data-stu-id="f796f-527">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="f796f-528">재생을 중지 하 고 시작 부분에 위치를 다시 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-528">Stops the playback and resets the position to the beginning.</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="f796f-529">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span><span class="sxs-lookup"><span data-stu-id="f796f-529">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="f796f-530">재생 중 상태 변경 내용을 수신 하는 것에 대 한 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-530">Interface for receiving state changes during playback.</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="f796f-531">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span><span class="sxs-lookup"><span data-stu-id="f796f-531">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="f796f-532">ISimulationRecording 재생 상태가 변경 되 면 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-532">Called when an ISimulationRecording's playback state has changed.</span></span>

<span data-ttu-id="f796f-533">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f796f-533">Parameters</span></span>
* <span data-ttu-id="f796f-534">newState-기록의 새 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-534">newState - The new state of the recording.</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="f796f-535">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="f796f-535">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="f796f-536">Perception 시뮬레이션 개체를 만들기 위한 루트 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-536">Root object for creating Perception Simulation objects.</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="f796f-537">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span><span class="sxs-lookup"><span data-stu-id="f796f-537">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="f796f-538">시뮬레이션 된 패킷을 생성 하 고 제공 된 싱크에서에 게 배달에 대 한 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-538">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="f796f-539">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f796f-539">Parameters</span></span>
* <span data-ttu-id="f796f-540">싱크-생성 된 모든 패킷의 받을 싱크입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-540">sink - The sink that will receive all generated packets.</span></span>

<span data-ttu-id="f796f-541">반환 값</span><span class="sxs-lookup"><span data-stu-id="f796f-541">Return value</span></span>

<span data-ttu-id="f796f-542">만든된 관리자입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-542">The created Manager.</span></span>

<span data-ttu-id="f796f-543">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span><span class="sxs-lookup"><span data-stu-id="f796f-543">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="f796f-544">모든 받은 패킷에 지정된 된 경로에 있는 파일에 저장 하는 싱크를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-544">Create a sink which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="f796f-545">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f796f-545">Parameters</span></span>
* <span data-ttu-id="f796f-546">경로-만들려는 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-546">path - The path of the file to create.</span></span>

<span data-ttu-id="f796f-547">반환 값</span><span class="sxs-lookup"><span data-stu-id="f796f-547">Return value</span></span>

<span data-ttu-id="f796f-548">만든된 싱크입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-548">The created sink.</span></span>

<span data-ttu-id="f796f-549">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span><span class="sxs-lookup"><span data-stu-id="f796f-549">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="f796f-550">지정된 된 파일에서 녹음/녹화를 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-550">Load a recording from the specified file.</span></span>

<span data-ttu-id="f796f-551">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f796f-551">Parameters</span></span>
* <span data-ttu-id="f796f-552">경로-로드할 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-552">path - The path of the file to load.</span></span>
* <span data-ttu-id="f796f-553">팩터리-필요한 경우에 ISimulationStreamSink 만들기에 대 한 기록에서 사용 하는 팩터리입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-553">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>

<span data-ttu-id="f796f-554">반환 값</span><span class="sxs-lookup"><span data-stu-id="f796f-554">Return value</span></span>

<span data-ttu-id="f796f-555">로드 된 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-555">The loaded recording.</span></span>

<span data-ttu-id="f796f-556">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording (System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory, Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span><span class="sxs-lookup"><span data-stu-id="f796f-556">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="f796f-557">지정된 된 파일에서 녹음/녹화를 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-557">Load a recording from the specified file.</span></span>

<span data-ttu-id="f796f-558">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f796f-558">Parameters</span></span>
* <span data-ttu-id="f796f-559">경로-로드할 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-559">path - The path of the file to load.</span></span>
* <span data-ttu-id="f796f-560">팩터리-필요한 경우에 ISimulationStreamSink 만들기에 대 한 기록에서 사용 하는 팩터리입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-560">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>
* <span data-ttu-id="f796f-561">콜백-수신 하는 콜백을 regrading 기록의 상태 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-561">callback - A callback which receives updates regrading the recording's status.</span></span>

<span data-ttu-id="f796f-562">반환 값</span><span class="sxs-lookup"><span data-stu-id="f796f-562">Return value</span></span>

<span data-ttu-id="f796f-563">로드 된 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-563">The loaded recording.</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="f796f-564">Microsoft.PerceptionSimulation.StreamDataTypes</span><span class="sxs-lookup"><span data-stu-id="f796f-564">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="f796f-565">다양 한 유형의 스트림 데이터를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-565">Describes the different types of stream data.</span></span>

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

<span data-ttu-id="f796f-566">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span><span class="sxs-lookup"><span data-stu-id="f796f-566">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="f796f-567">스트림 데이터 형식이 없습니다를 나타내는 데 센티널 값입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-567">A sentinel value used to indicate no stream data types.</span></span>

<span data-ttu-id="f796f-568">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span><span class="sxs-lookup"><span data-stu-id="f796f-568">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="f796f-569">위치 및 헤드의 방향에 대 한 데이터의 Stream입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-569">Stream of data regarding the position and orientation of the head.</span></span>

<span data-ttu-id="f796f-570">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span><span class="sxs-lookup"><span data-stu-id="f796f-570">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="f796f-571">손으로 제스처와 위치에 대 한 데이터의 Stream입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-571">Stream of data regarding the position and gestures of hands.</span></span>

<span data-ttu-id="f796f-572">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span><span class="sxs-lookup"><span data-stu-id="f796f-572">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="f796f-573">공간 매핑의 환경에 대 한 데이터의 Stream입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-573">Stream of data regarding spatial mapping of the environment.</span></span>

<span data-ttu-id="f796f-574">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span><span class="sxs-lookup"><span data-stu-id="f796f-574">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="f796f-575">장치의 보정에 대 한 데이터의 Stream입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-575">Stream of data regarding calibration of the device.</span></span> <span data-ttu-id="f796f-576">보정 패킷 시스템 원격 모드에만 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-576">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="f796f-577">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span><span class="sxs-lookup"><span data-stu-id="f796f-577">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="f796f-578">장치 환경에 대 한 데이터의 Stream입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-578">Stream of data regarding the environment of the device.</span></span>

<span data-ttu-id="f796f-579">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span><span class="sxs-lookup"><span data-stu-id="f796f-579">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="f796f-580">모든 기록 된 데이터 형식을 나타내는 데 센티널 값입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-580">A sentinel value used to indicate all recorded data types.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="f796f-581">Microsoft.PerceptionSimulation.ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="f796f-581">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="f796f-582">시뮬레이션 스트림에서 데이터 패킷을 수신 하는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-582">An object that receives data packets from a simulation stream.</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="f796f-583">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span><span class="sxs-lookup"><span data-stu-id="f796f-583">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="f796f-584">내부적으로 형식화 된 및 버전 관리 된 단일 패킷을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-584">Receives a single packet, which is internally typed and versioned.</span></span>

<span data-ttu-id="f796f-585">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f796f-585">Parameters</span></span>
* <span data-ttu-id="f796f-586">length-패킷 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-586">length - The length of the packet.</span></span>
* <span data-ttu-id="f796f-587">패킷 패킷의 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-587">packet - The data of the packet.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="f796f-588">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span><span class="sxs-lookup"><span data-stu-id="f796f-588">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="f796f-589">ISimulationStreamSink 만들어지는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-589">An object that creates ISimulationStreamSink.</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="f796f-590">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span><span class="sxs-lookup"><span data-stu-id="f796f-590">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="f796f-591">ISimulationStreamSink의 단일 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-591">Creates a single instance of ISimulationStreamSink.</span></span>

<span data-ttu-id="f796f-592">반환 값</span><span class="sxs-lookup"><span data-stu-id="f796f-592">Return value</span></span>

<span data-ttu-id="f796f-593">만든된 싱크입니다.</span><span class="sxs-lookup"><span data-stu-id="f796f-593">The created sink.</span></span>
