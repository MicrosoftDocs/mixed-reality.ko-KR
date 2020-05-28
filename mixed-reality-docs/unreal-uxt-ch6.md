---
title: 6. 패키징 후 디바이스 또는 에뮬레이터에 배포
description: Unreal Engine 4와 Mixed Reality Toolkit UX Tools 플러그인을 사용하여 간단한 체스 앱을 만드는 튜토리얼의 6부
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, 자습서, 시작, mrtk, uxt, UX Tools, 설명서
ms.openlocfilehash: b3f0b5f9ca5347c337091539b1cc0e214515c989
ms.sourcegitcommit: 09d9fa153cd9072f60e33a5f83ced8167496fcd7
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/18/2020
ms.locfileid: "83519972"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a><span data-ttu-id="16ab7-104">6. 패키징 후 디바이스 또는 에뮬레이터에 배포</span><span class="sxs-lookup"><span data-stu-id="16ab7-104">6. Packaging & deploying to device or emulator</span></span>

<span data-ttu-id="16ab7-105">이 섹션에서는 HoloLens 2 디바이스 또는 에뮬레이터에서 실행되도록 앱을 준비하는 단계를 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="16ab7-105">This section walks you through the steps of preparing your app to run on a HoloLens 2 device or Emulator.</span></span> <span data-ttu-id="16ab7-106">디바이스가 있는 경우 컴퓨터에서 디바이스로 스트리밍하거나 앱을 패키징하여 디바이스에서 직접 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16ab7-106">If you have a device, you can either stream from your computer to the device or package the app to run directly on the device.</span></span> <span data-ttu-id="16ab7-107">디바이스가 없는 경우 에뮬레이터에서 실행되도록 앱을 패키징해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="16ab7-107">If you do not have a device, you will need to package the app for it to run on the Emulator.</span></span> 

## <a name="objectives"></a><span data-ttu-id="16ab7-108">목표</span><span class="sxs-lookup"><span data-stu-id="16ab7-108">Objectives</span></span>

* <span data-ttu-id="16ab7-109">[디바이스 전용] 홀로그램 앱 원격 기능을 통해 HoloLens 2에 앱 스트리밍</span><span class="sxs-lookup"><span data-stu-id="16ab7-109">[Device only] Stream your app to HoloLens 2 via holographic app remoting</span></span>
* <span data-ttu-id="16ab7-110">HoloLens 2 디바이스 또는 에뮬레이터에 앱 패키지 및 배포</span><span class="sxs-lookup"><span data-stu-id="16ab7-110">Package and deploy your app to a HoloLens 2 device or emulator</span></span>

## <a name="device-only-stream"></a><span data-ttu-id="16ab7-111">[디바이스 전용] 스트림</span><span class="sxs-lookup"><span data-stu-id="16ab7-111">[Device Only] Stream</span></span>

1.  <span data-ttu-id="16ab7-112">HoloLens 2의 Microsoft Store에서 **홀로그램 원격 플레이어**를 설치하고 앱 실행</span><span class="sxs-lookup"><span data-stu-id="16ab7-112">Install the **Holographic Remoting Player** from the Microsoft Store on your HoloLens 2 and run the app</span></span>

2.  <span data-ttu-id="16ab7-113">**편집 > 프로젝트 설정**으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="16ab7-113">Go to **Edit > Project Settings**.</span></span> <span data-ttu-id="16ab7-114">홀로그램 원격 섹션에서 원격 기능을 사용하는 확인란을 선택하고 편집기를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="16ab7-114">In the Holographic Remoting section, check the box to enable remoting and restart the editor.</span></span>

3.  <span data-ttu-id="16ab7-115">디바이스의 IP 주소를 입력하고 연결을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="16ab7-115">Input the IP address of your device and click Connect.</span></span>

4.  <span data-ttu-id="16ab7-116">연결되면 UE4 편집기에서 재생 단추 오른쪽에 있는 드롭다운 화살표를 클릭하고 VR 미리 보기를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="16ab7-116">Once you’re connected, in your UE4 Editor, click the drop-down arrow to the right of the Play button and select VR Preview.</span></span>

## <a name="package-and-deploy-your-app"></a><span data-ttu-id="16ab7-117">앱 패키징 및 배포</span><span class="sxs-lookup"><span data-stu-id="16ab7-117">Package and deploy your app</span></span> 

>[!NOTE]
><span data-ttu-id="16ab7-118">HoloLens용 Unreal 앱을 처음으로 패키징하는 경우 Epic Launcher에서 지원 파일을 다운로드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="16ab7-118">If this is your first time packaging an Unreal app for HoloLens, you'll need to download supporting files from the Epic Launcher.</span></span> <span data-ttu-id="16ab7-119">이렇게 하려면 Epic Games Launcher에서 **라이브러리** 탭으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="16ab7-119">To do so, go to the **Library** tab in the Epic Games Launcher.</span></span> <span data-ttu-id="16ab7-120">**실행** 옆의 드롭다운 화살표를 선택하고 **옵션**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="16ab7-120">Select the dropdown arrow next to **Launch** and select **Options**.</span></span> <span data-ttu-id="16ab7-121">**대상 플랫폼**에서 **HoloLens 2**를 선택하고 **적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="16ab7-121">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span> 
><span data-ttu-id="16ab7-122">![프로젝트 설정 - 설명](images/unreal-uxt/6-installationoptions.PNG)</span><span class="sxs-lookup"><span data-stu-id="16ab7-122">![Project Settings - Description](images/unreal-uxt/6-installationoptions.PNG)</span></span>

1.  <span data-ttu-id="16ab7-123">**편집 > 프로젝트 설정**으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="16ab7-123">Go to **Edit > Project Settings**.</span></span> <span data-ttu-id="16ab7-124">**프로젝트 > 설명 > 정보 > 프로젝트 이름**에서 프로젝트 이름을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="16ab7-124">Under **Project > Description > About > Project Name**, give your project a name.</span></span> <span data-ttu-id="16ab7-125">**프로젝트 > 설명 > 게시자 > 회사 고유 이름**에서 “CN={INSERT COMPANY NAME}”을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="16ab7-125">Under **Project > Description > Publisher > Company Distinguished Name** put “CN={INSERT COMPANY NAME}”.</span></span> <span data-ttu-id="16ab7-126">이들 필드 중 하나를 비워 두면 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="16ab7-126">Leaving either of these fields blank will result in an error.</span></span> 

![프로젝트 설정 - 설명](images/unreal-uxt/6-cn.PNG)

2.  <span data-ttu-id="16ab7-128">**플랫폼 > HoloLens**에서 대상으로 지정할 에뮬레이션 및/또는 디바이스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="16ab7-128">Under **Platforms > HoloLens** choose Emulation and/or Device based on which you want to target.</span></span>

3.  <span data-ttu-id="16ab7-129">**패키징** 섹션에서 **서명 인증서** 옆에 있는 **새로 생성** 단추를 클릭하여 새 서명 인증서를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="16ab7-129">In the **Packaging** section, next to **Signing Certificate**, click the **Generate new** button to generate a new signing certificate.</span></span> <span data-ttu-id="16ab7-130">주 창으로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="16ab7-130">Return to the Main window.</span></span>

![프로젝트 설정 - 플랫폼 - HoloLens](images/unreal-uxt/6-packaging.PNG)

4.  <span data-ttu-id="16ab7-132">**파일 > 패키지 프로젝트**으로 이동하여 **HoloLens**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="16ab7-132">Go to **File > Package Project** and select **HoloLens**.</span></span> <span data-ttu-id="16ab7-133">새 폴더를 만들어 패키지를 저장하고 **폴더 선택**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="16ab7-133">Create a new folder to save your package in and click **Select Folder**.</span></span> 

5.  <span data-ttu-id="16ab7-134">앱이 성공적으로 패키지된 후 **Windows Device Portal**을 열고 **보기 > 앱**으로 이동한 다음, **앱 배포** 섹션을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="16ab7-134">Once the app has been successfully packaged, open the **Windows Device Portal**, go to **Views > Apps**, and find the **Deploy apps** section.</span></span>

6.  <span data-ttu-id="16ab7-135">**찾아보기 ...** 를 클릭하여 **ChessApp.appxbundle** 파일로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="16ab7-135">Click**Browse...** and navigate to your **ChessApp.appxbundle** file.</span></span> <span data-ttu-id="16ab7-136">**열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="16ab7-136">Click **Open**.</span></span> 

    * <span data-ttu-id="16ab7-137">디바이스에 앱을 처음 설치하는 경우**프레임워크 패키지를 선택하도록 허용** 옆의 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="16ab7-137">If this is the first time you are installing the app on your device, check the box next to **Allow me to select framework packages**.</span></span> <span data-ttu-id="16ab7-138">다음 대화 상자에서 적절한 VCLibs appx 파일(디바이스의 경우 arm64, 에뮬레이터의 경우 x64)을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="16ab7-138">In the next dialogue, include the appropriate VCLibs appx file (arm64 for device, x64 for emulator).</span></span> 

7.  <span data-ttu-id="16ab7-139">**설치**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="16ab7-139">Click **Install**</span></span>

<span data-ttu-id="16ab7-140">이 자습서를 완료한 것을 축하합니다!</span><span class="sxs-lookup"><span data-stu-id="16ab7-140">Congratulations on finishing this tutorial!</span></span>  