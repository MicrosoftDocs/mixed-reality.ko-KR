---
title: HoloLens 알려진 문제
description: HoloLens 개발자 영향을 줄 수 있는 알려진 문제 목록입니다.
author: mattzmsft
ms.author: mazeller
ms.date: 07/10/2019
ms.topic: article
keywords: 문제 해결, 알려진 문제, 도움말
ms.openlocfilehash: 1ef9e9f411e16d2f604930f3146ede1d03d7c0f6
ms.sourcegitcommit: c36b8c8573f51afa79504c4a17084e4f55d2f664
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67789485"
---
# <a name="hololens-known-issues"></a><span data-ttu-id="178ce-104">HoloLens 알려진 문제</span><span class="sxs-lookup"><span data-stu-id="178ce-104">HoloLens known issues</span></span>

<span data-ttu-id="178ce-105">이것이 현재 HoloLens에 영향을 주는 개발자를 위한 알려진된 문제 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-105">This is the current list of known issues for HoloLens affecting developers.</span></span> <span data-ttu-id="178ce-106">보려면 여기를 확인 한 부적절 한 동작 표시 되는 경우.</span><span class="sxs-lookup"><span data-stu-id="178ce-106">Check here first if you are seeing an odd behavior.</span></span> <span data-ttu-id="178ce-107">이 목록은 새로운 문제는 발견 되거나 보고 또는 이후 HoloLens 소프트웨어 업데이트 문제를 해결 하는 대로 업데이트 된 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-107">This list will be kept updated as new issues are discovered or reported, or as issues are addressed in future HoloLens software updates.</span></span>

## <a name="unable-to-connect-and-deploy-to-hololens-through-visual-studio"></a><span data-ttu-id="178ce-108">연결을 Visual Studio를 통해 HoloLens에 배포할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-108">Unable to connect and deploy to HoloLens through Visual Studio</span></span>

>[!NOTE]
><span data-ttu-id="178ce-109">마지막 업데이트 날짜: 7/8 오후 7시 25분-@ 팀에서 근본 원인을 식별 하 고 작업을 수정 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-109">Last Update: 7/8 @ 7:25PM - The team has identified the root cause and is currently working on fix.</span></span> <span data-ttu-id="178ce-110">해결 방법은 아래 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-110">Workaround available below.</span></span> 

<span data-ttu-id="178ce-111">이 문제의 근본 원인을 식별할 수 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-111">We were able to identify the root cause of this issue.</span></span> <span data-ttu-id="178ce-112">배포 및 해당 HoloLens에서 응용 프로그램을 디버그 하려면 Visual Studio 2015 또는 Visual Studio 2017의 초기 릴리스를 사용 하 고 다음 이후에 사용 되는 최신 버전의 Visual Studio 2017 또는 Visual Studio 2019 동일한 HoloLens를 사용 하 여 사용자에 게 영향을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-112">Users who used Visual Studio 2015 or early releases of Visual Studio 2017 to deploy and debug applications on their HoloLens and then subsequently used the latest versions of Visual Studio 2017 or Visual Studio 2019 with the same HoloLens will be affected.</span></span> 

<span data-ttu-id="178ce-113">Visual Studio의 최신 버전의 구성 요소를 새 버전을 배포 하지만 이전 버전의 파일이 최신 버전 실패를 일으키는 장치의 남은 됩니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-113">The newer releases of Visual Studio deploy a new version of a component, but files from the older version are left over on the device, causing the newer version to fail.</span></span>  <span data-ttu-id="178ce-114">이렇게 하면 다음 오류 메시지: DEP0100: 대상 장치에 개발자 모드가 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-114">This causes the following error message: DEP0100: Please ensure that target device has developer mode enabled.</span></span> <span data-ttu-id="178ce-115">개발자 라이선스를 얻지 못했습니다 <ip> 80004005 오류로 인해 합니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-115">Could not obtain a developer license on <ip> due to error 80004005.</span></span>
 
<span data-ttu-id="178ce-116">**해결 방법**:</span><span class="sxs-lookup"><span data-stu-id="178ce-116">**Workaround**:</span></span> 

<span data-ttu-id="178ce-117">우리 팀은 현재 수정 프로그램을 개발 합니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-117">Our team is currently working on a fix.</span></span> <span data-ttu-id="178ce-118">그동안 문제를 해결 하 여 배포 및 디버깅을 차단 해제 하는 데 도움이 되는 다음 단계를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-118">In the meantime, you can use the following steps to work around the issue and help unblock deployment and debugging:</span></span>  
1. <span data-ttu-id="178ce-119">Visual Studio를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-119">Open Visual Studio</span></span>
2. <span data-ttu-id="178ce-120">파일-> 새로 만들기-> 프로젝트</span><span class="sxs-lookup"><span data-stu-id="178ce-120">File -> New -> Project</span></span>
3. <span data-ttu-id="178ce-121">Visual C# Windows-> 데스크톱 콘솔 앱 (.NET Framework)-></span><span class="sxs-lookup"><span data-stu-id="178ce-121">Visual C# -> Windows Desktop -> Console App (.NET Framework)</span></span>
4. <span data-ttu-id="178ce-122">프로젝트 이름 (예: HoloLensDeploymentFix)를 지정 하 고 프레임 워크 이상으로 설정 되어 있는지 확인.NET Framework 4.5 확인을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-122">Give the project a name (e.g. HoloLensDeploymentFix) and make sure the Framework is set to at least .NET Framework 4.5 then click OK.</span></span>
5. <span data-ttu-id="178ce-123">솔루션 탐색기에서 참조 노드를 마우스 오른쪽 단추로 클릭 한 다음 참조를 추가 ('찾아보기' 섹션을 클릭 하 고 '찾아보기...'를 클릭 합니다. button):</span><span class="sxs-lookup"><span data-stu-id="178ce-123">Right-click on the References node in Solution Explorer and add the following references (click to the 'Browse' section and click the 'Browse...' button):</span></span>
    ```
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\Microsoft.Tools.Deploy.dll
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\Microsoft.Tools.Connectivity.dll
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\SirepInterop.dll
    ```
    >[!NOTE]
    ><span data-ttu-id="178ce-124">설치 10.0.18362.0 없다면 해야 하는 최신 버전을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-124">If you don't have 10.0.18362.0 installed, use the most recent version that you have.</span></span>
 
6. <span data-ttu-id="178ce-125">솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 추가 선택-> 기존 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-125">Right-click on the project in Solution Explorer and choose Add -> Existing Item.</span></span>
 
7. <span data-ttu-id="178ce-126">C:\Program Files (x86) \Windows Kits\10\bin\10.0.18362.0\x86 찾아 필터를 변경 합니다. "모든 파일 (\*.\*)"</span><span class="sxs-lookup"><span data-stu-id="178ce-126">Browse to C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86 and change the filter to "All Files (\*.\*)"</span></span>
 
8. <span data-ttu-id="178ce-127">SirepClient.dll와 SshClient.dll를 선택 하 고 [추가]를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-127">Select both SirepClient.dll and SshClient.dll and click "Add".</span></span>
 
9. <span data-ttu-id="178ce-128">찾아 (되어야 파일 목록의 아래쪽) 솔루션 탐색기에서 파일을 모두 선택 하 고 "항상 복사"를 "출력 디렉터리로 복사" 속성 창에서 변경</span><span class="sxs-lookup"><span data-stu-id="178ce-128">Locate and select both files in Solution Explorer (they should be at the bottom of the list of files) and change "Copy to Output Directory" in the Properties window to "Copy always"</span></span>
 
10. <span data-ttu-id="178ce-129">파일의 맨 위에 있는 'using' 문을 기존 목록에 다음을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-129">At the top of the file, add the following to the existing list of 'using' statements:</span></span> 
    ```
    using Microsoft.Tools.Deploy;
    using System.Net;
    ```
 
11. <span data-ttu-id="178ce-130">"Static void Main(...)"를 내에서 다음 코드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-130">Inside of “static void Main(...)”, add the following code:</span></span>
    ```
    RemoteDeployClient client = RemoteDeployClient.CreateRemoteDeployClient();
    client.Connect(new ConnectionOptions()
    {
        Credentials = new NetworkCredential("DevToolsUser", string.Empty),
        IPAddress = IPAddress.Parse(args[0])
    });
    client.RemoteDevice.DeleteFile(@"C:\Data\Users\DefaultAccount\AppData\Local\DevelopmentFiles\VSRemoteTools\x86\CoreCLR\mscorlib.ni.dll");
    ```
12. <span data-ttu-id="178ce-131">빌드-> 솔루션 빌드</span><span class="sxs-lookup"><span data-stu-id="178ce-131">Build -> Build Solution</span></span>
 
13. <span data-ttu-id="178ce-132">컴파일된.exe (예: C:\MyProjects\HoloLensDeploymentFix\bin\Debug)를 포함 하는 폴더에 명령 프롬프트를 열으십시오</span><span class="sxs-lookup"><span data-stu-id="178ce-132">Open a command prompt to the folder that contains the compiled .exe (e.g. C:\MyProjects\HoloLensDeploymentFix\bin\Debug)</span></span>
 
14. <span data-ttu-id="178ce-133">실행 파일을 실행 하 고 장치의 IP 주소를 명령줄 인수를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-133">Run the executable and provide the device's IP address as a command-line argument.</span></span>  <span data-ttu-id="178ce-134">(USB를 통해 연결 하는 경우 있습니다 수 127.0.0.1을 사용 하 여, 그렇지 않은 경우 장치의 WiFi IP 주소를 사용 합니다.)  예를 들어 "HoloLensDeploymentFix 127.0.0.1"</span><span class="sxs-lookup"><span data-stu-id="178ce-134">(If connected via USB, you can use 127.0.0.1, otherwise use the device’s WiFi IP address.)  For example, "HoloLensDeploymentFix 127.0.0.1"</span></span>
 
15. <span data-ttu-id="178ce-135">도구 (밖에 안 걸립니다 몇 초) 아무런 메시지 없이 종료 될 때, 배포 및 Visual Studio 2017에서 디버깅 하는 일을 할 이상 이제 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-135">Once the tool has exited without any messages (this should only take a few seconds), you will now be able to deploy and debug from Visual Studio 2017 or newer.</span></span>  <span data-ttu-id="178ce-136">도구를 계속된 사용할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-136">Continued use of the tool is not necessary.</span></span>

<span data-ttu-id="178ce-137">업데이트 사용 가능 해지면 추가로 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-137">We will provide further updates as they become available.</span></span>

## <a name="issues-launching-the-microsoft-store-and-apps-on-hololens"></a><span data-ttu-id="178ce-138">Microsoft Store 및 HoloLens에 앱을 시작 하는 문제</span><span class="sxs-lookup"><span data-stu-id="178ce-138">Issues launching the Microsoft Store and apps on HoloLens</span></span>

>[!NOTE]
><span data-ttu-id="178ce-139">마지막 업데이트 날짜: 4 월 2 @ 오전 10 시-문제를 해결 합니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-139">Last Update: 4/2 @ 10 AM - Issue resolved.</span></span> 

<span data-ttu-id="178ce-140">Microsoft Store 및 HoloLens에 앱을 시작 하려고 할 때 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-140">You may experience issues when trying to launch the Microsoft Store and apps on HoloLens.</span></span> <span data-ttu-id="178ce-141">백그라운드 앱 업데이트 중 하나는 특정 시퀀스에서 프레임 워크 패키지의 최신 버전을 배포 또는 해당 종속 된 앱 중 계속 실행 하는 경우 문제가 발생 하 확인 했습니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-141">We've determined that the issue occurs when background app updates deploy a newer version of framework packages in specific sequences while one or more of their dependent apps are still running.</span></span> <span data-ttu-id="178ce-142">이 경우 새 버전 (버전 10.0.25531를 10.0.27413)는.NET 네이티브 프레임 워크의 배달 자동 앱 업데이트 잘못 프레임 워크의 이전 버전을 사용 하는 모든 실행 중인 앱에 대 한 업데이트를 실행 하는 앱을 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-142">In this case,  an automatic app update delivered a new version of the .NET Native Framework (version 10.0.25531 to 10.0.27413) caused the apps that are running to not correctly update for all running apps consuming the prior version of the framework.</span></span>  <span data-ttu-id="178ce-143">프레임 워크 업데이트에 대 한 흐름은 다음과 같습니다.-</span><span class="sxs-lookup"><span data-stu-id="178ce-143">The flow for framework update is as follows: -</span></span>

1.  <span data-ttu-id="178ce-144">새 프레임 워크 패키지를 스토어에서 다운로드 및 설치</span><span class="sxs-lookup"><span data-stu-id="178ce-144">The new framework package is downloaded from the store and installed</span></span>
2.  <span data-ttu-id="178ce-145">이전 프레임 워크를 사용 하 여 모든 앱은 ' 업데이트 ' 최신 버전을 사용 하려면</span><span class="sxs-lookup"><span data-stu-id="178ce-145">All apps using the older framework are ‘updated’ to use the newer version</span></span>

<span data-ttu-id="178ce-146">2 단계 완료 되기 전에 중단 되는 경우 시작 메뉴에서 시작할 수 없는 최신 프레임 워크에 등록 되지 않은 모든 앱 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-146">If step 2 is interrupted before completion then any apps for which the newer framework wasn’t registered will fail to launch from the start menu.</span></span>  <span data-ttu-id="178ce-147">HoloLens에 앱이이 문제로 인해 저하 될 수 있습니다 하는 것이 믿습니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-147">We believe any app on HoloLens could be affected by this issue.</span></span>

<span data-ttu-id="178ce-148">그러나 일부 사용자에 게는 응답이 없는 앱을 닫기 피드백 허브 같은 다른 앱을 시작 하 고 3D 뷰어 또는 사진 확인 있으며 문제를 보고 합니다.이 작동 하지 않습니다 100%의 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-148">Some users have reported that closing hung apps and launching other apps such as Feedback Hub, 3D Viewer or Photos resolves the issue for them - however, this does not work 100% of the time.</span></span>

<span data-ttu-id="178ce-149">했습니다 근본 원인인이 문제를 발생 시 키 지 버그 하지만 업데이트 자체를 올바르게 처리 되 고.NET 네이티브 프레임 워크 업데이트 발생 하는 OS에서.</span><span class="sxs-lookup"><span data-stu-id="178ce-149">We have root caused that this issue was not caused the update itself, but a bug in the OS that resulted in the .NET Native framework update being handled incorrectly.</span></span> <span data-ttu-id="178ce-150">수정 프로그램을 확인 하 고 업데이트 (OS 버전 17763.380) 릴리스를 발표할 기쁩니다 수정 사항을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-150">We are pleased to announce that we have identified a fix and have released an update (OS version 17763.380) containing the fix.</span></span> 

<span data-ttu-id="178ce-151">장치를 업데이트 하세요 걸릴 수 있습니다를 보려면:</span><span class="sxs-lookup"><span data-stu-id="178ce-151">To see if your device can take the update please:</span></span>

1.  <span data-ttu-id="178ce-152">"설정" 앱으로 이동 하 고 "업데이트 및 보안"을 엽니다</span><span class="sxs-lookup"><span data-stu-id="178ce-152">Go to the “Settings” app and open “Update & Security”</span></span>
2.  <span data-ttu-id="178ce-153">"업데이트 확인"을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-153">Click “Check for Updates”</span></span>
3.  <span data-ttu-id="178ce-154">17763.380 업데이트를 사용할 수 있는 경우 업데이트 하세요 앱 중단 버그 픽스를 받으려면이 빌드에</span><span class="sxs-lookup"><span data-stu-id="178ce-154">If update to 17763.380 is available, please update to this build to receive the fix for the App Hang bug</span></span>
4.  <span data-ttu-id="178ce-155">운영 체제의이 버전으로 업데이트 되 면 앱은 예상 대로 작동 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-155">Upon updating to this version of the OS, the Apps should work as expected.</span></span>

<span data-ttu-id="178ce-156">또한 모든 HoloLens OS 릴리스를 사용 하 여 마찬가지로에서는 게시 된 FFU 이미지는 Microsoft 다운로드 센터 https://aka.ms/hololensdownload/10.0.17763.380 합니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-156">Additionally, as we do with every HoloLens OS release, we have posted the FFU image to the Microsoft Download Center at https://aka.ms/hololensdownload/10.0.17763.380.</span></span> 

<span data-ttu-id="178ce-157">업데이트 하려는 경우 3/29 일부 터 Microsoft Store UWP 앱의 새 버전을 릴리스 했습니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-157">If you would not like to take the update, we have released a new version of the Microsoft Store UWP app as of 3/29.</span></span> <span data-ttu-id="178ce-158">있다면 저장소의 업데이트 된 버전.</span><span class="sxs-lookup"><span data-stu-id="178ce-158">Once you have the updated version of the Store:</span></span>

1) <span data-ttu-id="178ce-159">스토어를 열고 로드 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-159">Open the Store and confirm that it loads.</span></span>
2) <span data-ttu-id="178ce-160">Bloom 제스처를 사용 하 여 메뉴를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-160">Use the Bloom Gesture to open the menu.</span></span>
3) <span data-ttu-id="178ce-161">이전에 손상 된 앱을 열려고 시도</span><span class="sxs-lookup"><span data-stu-id="178ce-161">Attempt to open previously broken apps</span></span>
3) <span data-ttu-id="178ce-162">여전히 시작할 수 없습니다, 하는 경우 탭 및 손상 된 앱의 아이콘을 보유 하 고 제거를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-162">If it still cannot be launched, tap and hold the icon of the broken app and select uninstall.</span></span>
4) <span data-ttu-id="178ce-163">Resinstall 저장소에서 이러한 앱.</span><span class="sxs-lookup"><span data-stu-id="178ce-163">Resinstall these apps from the store.</span></span>

<span data-ttu-id="178ce-164">장치의 앱을 로드 하는 데 수 없는 경우 수행 하 여 다운로드 센터를 통해.NET 네이티브 프레임 워크 및 런타임 버전을 테스트용으로 로드를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-164">If your device is still unable to load apps, you can sideload a version of the .NET Native Framework and Runtime through the download center by doing:</span></span>

1)  <span data-ttu-id="178ce-165">다운로드 하세요 [이 zip 파일](http://download.microsoft.com/download/8/5/C/85C23745-794C-419D-B8D7-115FBCCD6DA7/netfx_1.7.zip) Microsoft 다운로드 센터에서.</span><span class="sxs-lookup"><span data-stu-id="178ce-165">Please download [this zip file](http://download.microsoft.com/download/8/5/C/85C23745-794C-419D-B8D7-115FBCCD6DA7/netfx_1.7.zip) from the Microsoft Download Center.</span></span>  <span data-ttu-id="178ce-166">압축을 푸는 두 파일이 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-166">Unzipping will produce two files.</span></span>  <span data-ttu-id="178ce-167">Microsoft.NET.Native.Runtime.1.7.appx 및 Microsoft.NET.Native.Framework.1.7.appx</span><span class="sxs-lookup"><span data-stu-id="178ce-167">Microsoft.NET.Native.Runtime.1.7.appx and Microsoft.NET.Native.Framework.1.7.appx</span></span>
2)  <span data-ttu-id="178ce-168">장치가 개발자 잠금 해제 인지를 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="178ce-168">Please verify that your device is dev unlocked.</span></span>  <span data-ttu-id="178ce-169">이렇게 하려면 지침은 전에 수행 하지 않았다면 [여기](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fwindows%2Fmixed-reality%2Fusing-the-windows-device-portal&data=02%7C01%7Cjalynch%40microsoft.com%7C3622a462ebd04870fccb08d6ae94cad6%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636888351416725140&sdata=ZB6Zdx9GV95PcU6FAVgWaP3eQNMsyIc%2FbNDEby3Sb8A%3D&reserved=0)합니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-169">If you haven’t done that before the instructions to do that are [here](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fwindows%2Fmixed-reality%2Fusing-the-windows-device-portal&data=02%7C01%7Cjalynch%40microsoft.com%7C3622a462ebd04870fccb08d6ae94cad6%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636888351416725140&sdata=ZB6Zdx9GV95PcU6FAVgWaP3eQNMsyIc%2FbNDEby3Sb8A%3D&reserved=0).</span></span>
3)  <span data-ttu-id="178ce-170">그런 다음 Windows Device Portal 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-170">You then want to get into the Windows Device Portal.</span></span>  <span data-ttu-id="178ce-171">USB를 통해이 작업을 수행 하는 것이 좋습니다 및을 수행 하면 입력 하 여 http://127.0.0.1:10080 브라우저에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-171">Our recommendation is to do this over USB and you would do that by typing http://127.0.0.1:10080 into your browser.</span></span>  
4)  <span data-ttu-id="178ce-172">Windows Device Portal에서는 등록 해야 "테스트용 로드"를 만든 후 두 다운로드 하는 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-172">Once you have the Windows Device Portal up we need you to “side load” the two files that you downloaded.</span></span>  <span data-ttu-id="178ce-173">작업을 수행 하는 "앱" 섹션을 가져와서 "앱"을 클릭할 때까지 왼쪽된 사이드 바 아래로 이동 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-173">To do that you need to go down the left side bar until you get to the “Apps” section and click on “Apps”.</span></span>
5)  <span data-ttu-id="178ce-174">다음 화면이 표시 됩니다는 비슷한는 아래.</span><span class="sxs-lookup"><span data-stu-id="178ce-174">You will then see a screen that is similar to the below.</span></span>  <span data-ttu-id="178ce-175">이러한 두 APPX 파일의 압축을 푼 찾아 "앱 설치" 라는 섹션으로 이동 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-175">You want to go to the section that says “Install App” and browse to where you unzipped those two APPX files.</span></span>  <span data-ttu-id="178ce-176">한 번에 하나씩만 수행을 하므로 첫 번째를 선택한 후 다음 "이동" 섹션에서 클릭 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-176">You can only do one at a time, so after you select the first one, then click on “Go” under the Deploy section.</span></span>  <span data-ttu-id="178ce-177">다음 두 번째 APPX 파일에 대 한이 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-177">Then do this for the second APPX file.</span></span> 
  <span data-ttu-id="178ce-178">![테스트용 로드 앱을 설치 하려면 Windows Device Portal](images/20190322-DevicePortal.png)</span><span class="sxs-lookup"><span data-stu-id="178ce-178">![Windows Device Portal to Install Side-Loaded app](images/20190322-DevicePortal.png)</span></span><br>
6)  <span data-ttu-id="178ce-179">이 시점에서 응용 프로그램 작업을 다시 시작 해야 하 고 저장소로 가져올 수도 있습니다는 것이 믿습니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-179">At this point we believe your applications should start working again and that you can also get to the Store.</span></span>
7)  <span data-ttu-id="178ce-180">일부 경우에서는 필요한 영향을 받는 앱이 시작 되기 전에 3D 뷰어 앱을 시작 하는 추가 단계를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-180">In some cases, it is necessary run the additional step of launching the 3D Viewer app before affected apps will launch.</span></span> 

<span data-ttu-id="178ce-181">이 문제를 해결 하는 프로세스를 통해 발전와 귀 환경을 혼합 현실 성공적으로 만들려면 커뮤니티를 사용 하 여 작업을 계속 하려면 기다려를 드립니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-181">We appreciate your patience as we have gone through the process to get this issue resolved, and we look forward to continued working with our community to create successful Mixed Reality experiences.</span></span>

## <a name="connecting-to-wifi"></a><span data-ttu-id="178ce-182">WiFi에 연결</span><span class="sxs-lookup"><span data-stu-id="178ce-182">Connecting to WiFi</span></span>

<span data-ttu-id="178ce-183">OOBE 및 설정 하는 동안에 자격 증명 시간 제한은 2 분입니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-183">During OOBE & Settings, there is a credential timeout of 2 mins.</span></span> <span data-ttu-id="178ce-184">사용자 이름/암호를 2 분이 고 그렇지 username 필드가 자동으로 지워집니다. 내에 입력 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-184">The username/password needs to be entered within 2 mins otherwise the username field will be automatically cleared.</span></span>

<span data-ttu-id="178ce-185">Bluetooth 키보드를 사용 하 여 긴 암호를 입력 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-185">We recommend using a Bluetooth keyboard for entering long passwords.</span></span>

## <a name="device-update"></a><span data-ttu-id="178ce-186">장치 업데이트</span><span class="sxs-lookup"><span data-stu-id="178ce-186">Device Update</span></span>
* <span data-ttu-id="178ce-187">새 업데이트 후 30 초 셸은 한 번 사라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-187">30 seconds after a new update, the shell may disappear one time.</span></span> <span data-ttu-id="178ce-188">수행 하십시오 합니다 **블 룸** 제스처에 세션을 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-188">Please perform the **bloom** gesture to resume your session.</span></span>

## <a name="visual-studio"></a><span data-ttu-id="178ce-189">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="178ce-189">Visual Studio</span></span>
* <span data-ttu-id="178ce-190">참조 [도구를 설치](install-the-tools.md) HoloLens 개발에 권장 되는 Visual Studio의 최신 버전에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-190">See [Install the tools](install-the-tools.md) for the most up-to-date version of Visual Studio recommended for HoloLens development.</span></span>
* <span data-ttu-id="178ce-191">에 HoloLens에 Visual Studio에서 앱을 배포할 때 오류가 표시 될 수 있습니다. **사용자 매핑 섹션 열려 있는 파일에서 요청된 된 작업을 수행할 수 없습니다. (예외가 발생한 HRESULT: 0x800704C8)** .</span><span class="sxs-lookup"><span data-stu-id="178ce-191">When deploying an app from Visual Studio to your HoloLens, you may see the error: **The requested operation cannot be performed on a file with a user-mapped section open. (Exception from HRESULT: 0x800704C8)**.</span></span> <span data-ttu-id="178ce-192">이 경우 다시 시도 및 배포는 일반적으로 성공 합니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-192">If this happens, try again and your deployment will generally succeed.</span></span>

## <a name="emulator"></a><span data-ttu-id="178ce-193">에뮬레이터</span><span class="sxs-lookup"><span data-stu-id="178ce-193">Emulator</span></span>
* <span data-ttu-id="178ce-194">Microsoft Store 모든 앱을 에뮬레이터와 호환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-194">Not all apps in the Microsoft Store are compatible with the emulator.</span></span> <span data-ttu-id="178ce-195">예를 들어 Young Conker 및 조각이 없는 에뮬레이터에서 재생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-195">For example, Young Conker and Fragments are not playable on the emulator.</span></span>
* <span data-ttu-id="178ce-196">에뮬레이터에서 PC 웹캠을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-196">You cannot use the PC webcam in the Emulator.</span></span>
* <span data-ttu-id="178ce-197">에뮬레이터를 사용 하 여 Windows Device Portal 실시간 미리 보기 기능을 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-197">The Live Preview feature of the Windows Device Portal does not work with the emulator.</span></span> <span data-ttu-id="178ce-198">여전히 혼합 현실 비디오 및 이미지를 캡처할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-198">You can still capture Mixed Reality videos and images.</span></span>

## <a name="unity"></a><span data-ttu-id="178ce-199">Unity</span><span class="sxs-lookup"><span data-stu-id="178ce-199">Unity</span></span>
* <span data-ttu-id="178ce-200">참조 [도구를 설치](install-the-tools.md) HoloLens 개발에 권장 되는 Unity의 최신 버전에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-200">See [Install the tools](install-the-tools.md) for the most up-to-date version of Unity recommended for HoloLens development.</span></span>
* <span data-ttu-id="178ce-201">Unity HoloLens Technical Preview의 알려진된 문제에 설명 되어는 [HoloLens Unity 포럼](http://forum.unity3d.com/threads/known-issues.394627/)합니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-201">Known issues with the Unity HoloLens Technical Preview are documented in the [HoloLens Unity forums](http://forum.unity3d.com/threads/known-issues.394627/).</span></span>

## <a name="windows-device-portal"></a><span data-ttu-id="178ce-202">Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="178ce-202">Windows Device Portal</span></span>
* <span data-ttu-id="178ce-203">혼합 현실 캡처의 실시간 미리 보기 기능에는 몇 초 정도 대기 시간이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-203">The Live Preview feature in Mixed Reality capture may exhibit several seconds of latency.</span></span>
* <span data-ttu-id="178ce-204">가상 입력 페이지에서 가상 제스처 섹션 제스처 및 스크롤 컨트롤 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-204">On the Virtual Input page, the Gesture and Scroll controls under the Virtual Gestures section are not functional.</span></span> <span data-ttu-id="178ce-205">사용 하는 효과가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-205">Using them will have no effect.</span></span> <span data-ttu-id="178ce-206">동일한 페이지의 가상 키보드 제대로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-206">The virtual keyboard on the same page works correctly.</span></span>
* <span data-ttu-id="178ce-207">설정에서 개발자 모드를 사용 하도록 설정한 후 장치 포털에는 스위치를 사용 하기 전에 몇 초 정도 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-207">After enabling Developer Mode in Settings, it may take a few seconds before the switch to turn on the Device Portal is enabled.</span></span>

## <a name="api"></a><span data-ttu-id="178ce-208">API</span><span class="sxs-lookup"><span data-stu-id="178ce-208">API</span></span>
* <span data-ttu-id="178ce-209">응용 프로그램을 설정 하는 경우는 [지점 집중](focus-point-in-unity.md) 사용자 또는 수직 camera.forward에 뒤 홀로그램 혼합 현실 캡처 사진 또는 비디오에 표시 되지 것입니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-209">If the application sets the [focus point](focus-point-in-unity.md) behind the user or the normal to camera.forward, holograms will not appear in Mixed Reality Capture photos or videos.</span></span> <span data-ttu-id="178ce-210">이 버그는 응용 프로그램에서 적극적으로 설정 하는 경우, Windows에서 해결 될 때까지 합니다 [지점 집중](focus-point-in-unity.md) 평면 보통 반대 카메라 정방향 설정 되도록 해야 (예: 일반 =-camera.forward).</span><span class="sxs-lookup"><span data-stu-id="178ce-210">Until this bug is fixed in Windows, if applications actively set the [focus point](focus-point-in-unity.md) they should ensure the plane normal is set opposite camera-forward (e.g. normal = -camera.forward).</span></span>

## <a name="xbox-wireless-controller"></a><span data-ttu-id="178ce-211">Xbox 무선 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="178ce-211">Xbox Wireless Controller</span></span>
* <span data-ttu-id="178ce-212">HoloLens를 사용 하 여 사용할 수 있습니다 Xbox 무선 컨트롤러 S는 업데이트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-212">Xbox Wireless Controller S must be updated before it can be used with HoloLens.</span></span> <span data-ttu-id="178ce-213">준수할 수 있도록 [최신](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) 는 HoloLens 사용 하 여 컨트롤러를 연결 하기 전에 합니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-213">Ensure you are [up to date](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) before attempting to pair your controller with a HoloLens.</span></span>
* <span data-ttu-id="178ce-214">Xbox 무선 컨트롤러 연결 되어 있는 동안에 HoloLens를 다시 부팅 하면 컨트롤러는 자동으로 다시 연결 되지 HoloLens에.</span><span class="sxs-lookup"><span data-stu-id="178ce-214">If you reboot your HoloLens while the Xbox Wireless Controller is connected, the controller will not automatically reconnect to HoloLens.</span></span> <span data-ttu-id="178ce-215">가이드 단추는 표시등이 느린 컨트롤러 꺼질 때까지 해제 3 분 후입니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-215">The Guide button light will flash slowly until the controller powers off after 3 minutes.</span></span> <span data-ttu-id="178ce-216">컨트롤러 즉시 끄지 광원 해제 될 때까지 가이드 단추를 눌러 컨트롤러를 다시 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-216">To reconnect your controller immediately, power off the controller by holding the Guide button until the light turns off.</span></span> <span data-ttu-id="178ce-217">켜면 컨트롤러 다시, HoloLens에 다시 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-217">When you power your controller on again, it will reconnect to HoloLens.</span></span>
* <span data-ttu-id="178ce-218">Xbox 무선 컨트롤러 연결 되어 있는 동안 대기 모드로 전환에 HoloLens, 하는 경우 컨트롤러에 대 한 의견은 HoloLens 절전 모드 해제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-218">If your HoloLens enters standby while the Xbox Wireless Controller is connected, any input on the controller will wake the HoloLens.</span></span> <span data-ttu-id="178ce-219">완료 되 면 컨트롤러 해제 강화 하 여이 방지할 수 있습니다 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="178ce-219">You can prevent this by powering off your controller when you are done using it.</span></span>
