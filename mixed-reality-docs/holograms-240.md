---
title: MR 240-여러 HoloLens 장치를 공유 합니다.
description: Unity에서 Visual Studio 및 HoloLens를 사용 하 여 홀로그램을 공유 하는 자세한 연습을 코딩이 수행 합니다.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit mixedrealitytoolkit, mixedrealitytoolkit unity, 공유, 네트워킹, academy, 자습서
ms.openlocfilehash: 70a39a739d360a5032bc8df76b6f0bd57521d9ec
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59601390"
---
>[!NOTE]
><span data-ttu-id="d93e1-104">혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="d93e1-105">따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="d93e1-106">이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="d93e1-107">지원 되는 장치에서 작업을 계속 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="d93e1-108">새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="d93e1-109">게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-sharing-240-multiple-hololens-devices"></a><span data-ttu-id="d93e1-110">MR 240을 공유 합니다. 여러 HoloLens 장치</span><span class="sxs-lookup"><span data-stu-id="d93e1-110">MR Sharing 240: Multiple HoloLens devices</span></span>

<span data-ttu-id="d93e1-111">홀로그램 위치에 남아 있는 공간에 대 한 이동 하 여 세계에 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-111">Holograms are given presence in our world by remaining in place as we move about in space.</span></span> <span data-ttu-id="d93e1-112">HoloLens 곳에서 다양 한를 사용 하 여 홀로그램을 유지 [좌표계](coordinate-systems.md) 를 추적할 위치와 개체의 방향입니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-112">HoloLens keeps holograms in place by using various [coordinate systems](coordinate-systems.md) to keep track of the location and orientation of objects.</span></span> <span data-ttu-id="d93e1-113">장치 간에 이러한 좌표계를 공유 하는 경우 공유 holographic 환경에 참여할 수 있게 하는 공유 환경을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-113">When we share these coordinate systems between devices, we can create a shared experience that allows us to take part in a shared holographic world.</span></span>

<span data-ttu-id="d93e1-114">이 자습서를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-114">In this tutorial, we will:</span></span>

* <span data-ttu-id="d93e1-115">공유 경험에 대 한 네트워크를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-115">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="d93e1-116">홀로그램 HoloLens 장치 간에 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-116">Share holograms across HoloLens devices.</span></span>
* <span data-ttu-id="d93e1-117">공유 holographic 세계의 다른 사용자를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-117">Discover other people in our shared holographic world.</span></span>
* <span data-ttu-id="d93e1-118">다른 플레이어-대상으로 하 고 있습니다 무기를 시작할 수 있는 공유 대화형 환경 만들기</span><span class="sxs-lookup"><span data-stu-id="d93e1-118">Create a shared interactive experience where you can target other players - and launch projectiles at them!</span></span>

## <a name="device-support"></a><span data-ttu-id="d93e1-119">장치 지원</span><span class="sxs-lookup"><span data-stu-id="d93e1-119">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="d93e1-120">과정</span><span class="sxs-lookup"><span data-stu-id="d93e1-120">Course</span></span></th><th style="width:150px"> <span data-ttu-id="d93e1-121"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="d93e1-121"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="d93e1-122"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="d93e1-122"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="d93e1-123">MR 240을 공유 합니다. 여러 HoloLens 장치</span><span class="sxs-lookup"><span data-stu-id="d93e1-123">MR Sharing 240: Multiple HoloLens devices</span></span></td><td style="text-align: center;"> <span data-ttu-id="d93e1-124">✔️</span><span class="sxs-lookup"><span data-stu-id="d93e1-124">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="d93e1-125">시작하기 전 주의 사항</span><span class="sxs-lookup"><span data-stu-id="d93e1-125">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="d93e1-126">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="d93e1-126">Prerequisites</span></span>

* <span data-ttu-id="d93e1-127">올바른를 사용 하 여 구성 하는 Windows 10 PC [도구가 설치 되어](install-the-tools.md) 인터넷 액세스를 사용 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-127">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md) with Internet access.</span></span>
* <span data-ttu-id="d93e1-128">두 개 이상의 HoloLens 장치 [개발에 대해 구성 된](using-visual-studio.md#enabling-developer-mode)합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-128">At least two HoloLens devices [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="d93e1-129">프로젝트 파일</span><span class="sxs-lookup"><span data-stu-id="d93e1-129">Project files</span></span>

* <span data-ttu-id="d93e1-130">다운로드 합니다 [파일](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) 프로젝트에서 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-130">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) required by the project.</span></span> <span data-ttu-id="d93e1-131">Unity 2017.2 이상이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-131">Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="d93e1-132">Unity 5.6 지원이 계속 필요한 경우 사용 하세요 [이 릴리스에서](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip)합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-132">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).</span></span>
  * <span data-ttu-id="d93e1-133">Unity 5.5 지원 해야 하는 경우 사용 하세요 [이 릴리스에서](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip)합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-133">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).</span></span>
  * <span data-ttu-id="d93e1-134">Unity 5.4 지원이 계속 필요한 경우 사용 하세요 [이 릴리스에서](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip)합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-134">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).</span></span>
* <span data-ttu-id="d93e1-135">취소 보관 파일을 데스크톱 또는 기타 쉽게 달성할 수 있습니다 위치 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-135">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="d93e1-136">폴더 이름을 변수로 유지 **SharedHolograms**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-136">Keep the folder name as **SharedHolograms**.</span></span>

>[!NOTE]
><span data-ttu-id="d93e1-137">을 다운로드 하기 전에 소스 코드를 확인 하려는 경우 있기 [GitHub에서 사용할 수 있는](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms)합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="d93e1-138">1 장-Holo World</span><span class="sxs-lookup"><span data-stu-id="d93e1-138">Chapter 1 - Holo World</span></span>

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

<span data-ttu-id="d93e1-139">이 챕터에 첫 번째 Unity 프로젝트 및 빌드를 단계별로 설치 및 배포 프로세스에서는 했습니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-139">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="d93e1-140">목표</span><span class="sxs-lookup"><span data-stu-id="d93e1-140">Objectives</span></span>

* <span data-ttu-id="d93e1-141">Holographic 앱을 개발 하는 Unity를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-141">Setup Unity to develop holographic apps.</span></span>
* <span data-ttu-id="d93e1-142">프로그램 홀로그램을 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="d93e1-142">See your hologram!</span></span>

### <a name="instructions"></a><span data-ttu-id="d93e1-143">지침</span><span class="sxs-lookup"><span data-stu-id="d93e1-143">Instructions</span></span>

* <span data-ttu-id="d93e1-144">Unity를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-144">Start Unity.</span></span>
* <span data-ttu-id="d93e1-145">선택 **열려**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-145">Select **Open**.</span></span>
* <span data-ttu-id="d93e1-146">위치를 입력 합니다 **SharedHolograms** 하면 이전에 보관 되지 않은 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-146">Enter location as the **SharedHolograms** folder you previously unarchived.</span></span>
* <span data-ttu-id="d93e1-147">선택 **프로젝트 이름** 누릅니다 **폴더 선택**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-147">Select **Project Name** and click **Select Folder**.</span></span>
* <span data-ttu-id="d93e1-148">에 **계층**를 마우스 오른쪽 단추로 클릭 합니다 **주 카메라** 선택한 **삭제**.</span><span class="sxs-lookup"><span data-stu-id="d93e1-148">In the **Hierarchy**, right-click the **Main Camera** and select **Delete**.</span></span>
* <span data-ttu-id="d93e1-149">에 **HoloToolkit 공유-240/Prefabs/카메라** 폴더를 찾을 합니다 **주 카메라** prefab 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-149">In the **HoloToolkit-Sharing-240/Prefabs/Camera** folder, find the **Main Camera** prefab.</span></span>
* <span data-ttu-id="d93e1-150">끌어서 놓기 합니다 **주 카메라** 에 **계층**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-150">Drag and drop the **Main Camera** into the **Hierarchy**.</span></span>
* <span data-ttu-id="d93e1-151">에 **계층**, 클릭 **만들기** 하 고 **빈 항목 만들기**.</span><span class="sxs-lookup"><span data-stu-id="d93e1-151">In the **Hierarchy**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="d93e1-152">새을 마우스 오른쪽 단추로 클릭 **GameObject** 선택한 **이름 바꾸기**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-152">Right-click the new **GameObject** and select **Rename**.</span></span>
* <span data-ttu-id="d93e1-153">GameObject 이름 바꾸기 **HologramCollection**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-153">Rename the GameObject to **HologramCollection**.</span></span>
* <span data-ttu-id="d93e1-154">선택 된 **HologramCollection** 개체를 **계층**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-154">Select the **HologramCollection** object in the **Hierarchy**.</span></span>
* <span data-ttu-id="d93e1-155">에 **검사기** 설정 합니다 **위치를 변환** 에: **X: 0, Y:-0.25, Z: 2**.</span><span class="sxs-lookup"><span data-stu-id="d93e1-155">In the **Inspector** set the **transform position** to: **X: 0, Y: -0.25, Z: 2**.</span></span>
* <span data-ttu-id="d93e1-156">에 **홀로그램** 폴더에는 **프로젝트 패널**, 찾을 **EnergyHub** 자산입니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-156">In the **Holograms** folder in the **Project panel**, find the **EnergyHub** asset.</span></span>
* <span data-ttu-id="d93e1-157">끌어서 놓기는 **EnergyHub** 에서 개체를 **프로젝트 패널** 에 **계층** 으로 **HologramCollection 자식의**.</span><span class="sxs-lookup"><span data-stu-id="d93e1-157">Drag and drop the **EnergyHub** object from the **Project panel** to the **Hierarchy** as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="d93e1-158">선택 **파일 >으로 장면 저장...**</span><span class="sxs-lookup"><span data-stu-id="d93e1-158">Select **File > Save Scene As...**</span></span>
* <span data-ttu-id="d93e1-159">장면 이름을 **SharedHolograms** 누릅니다 **저장**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-159">Name the scene **SharedHolograms** and click **Save**.</span></span>
* <span data-ttu-id="d93e1-160">키를 눌러 합니다 **재생** 여 홀로그램 미리 보기에 Unity에서 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-160">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="d93e1-161">키를 눌러 **재생** 미리 보기 모드를 중지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-161">Press **Play** a second time to stop preview mode.</span></span>

<span data-ttu-id="d93e1-162">**Visual studio에서 Unity 프로젝트 내보내기**</span><span class="sxs-lookup"><span data-stu-id="d93e1-162">**Export the project from Unity to Visual Studio**</span></span>
* <span data-ttu-id="d93e1-163">Unity select에서 **파일 > 빌드 설정**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-163">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="d93e1-164">클릭 **열기 장면 추가** 장면에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-164">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="d93e1-165">선택 **유니버설 Windows 플랫폼** 에 **플랫폼** 클릭 **플랫폼 전환**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-165">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="d93e1-166">설정할 **SDK** 하 **유니버설 10**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-166">Set **SDK** to **Universal 10**.</span></span>
* <span data-ttu-id="d93e1-167">설정 **대상 장치** 하 **HoloLens** 하 고 **UWP 빌드 형식** 에 **D3D**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-167">Set **Target device** to **HoloLens** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="d93e1-168">확인할 **Unity C# 프로젝트**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-168">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="d93e1-169">**빌드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-169">Click **Build**.</span></span>
* <span data-ttu-id="d93e1-170">표시 되는 파일 탐색기 창에서 만들기를 **새 폴더** 이름을 "App"입니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-170">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="d93e1-171">한 번 클릭 합니다 **앱** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-171">Single click the **App** folder.</span></span>
* <span data-ttu-id="d93e1-172">키를 눌러 **폴더 선택**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-172">Press **Select Folder**.</span></span>
* <span data-ttu-id="d93e1-173">Unity 완료 되 면 파일 탐색기 창이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-173">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="d93e1-174">엽니다는 **앱** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-174">Open the **App** folder.</span></span>
* <span data-ttu-id="d93e1-175">오픈 **SharedHolograms.sln** Visual Studio를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-175">Open **SharedHolograms.sln** to launch Visual Studio.</span></span>
* <span data-ttu-id="d93e1-176">에 디버그 대상 변경 맨 위의 도구 모음을 사용 하 여 Visual Studio에서 **릴리스** 들어오고를 ARM **X86**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-176">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="d93e1-177">로컬 컴퓨터 옆에 있는 드롭다운 화살표를 클릭 하 고 선택 **원격 장치**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-177">Click on the drop-down arrow next to Local Machine, and select **Remote Device**.</span></span>
    * <span data-ttu-id="d93e1-178">설정 된 **주소** 이름 또는 IP 주소에 HoloLens 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-178">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="d93e1-179">장치 IP 주소를 모르는 경우 찾는 위치 **설정 > 네트워크 및 인터넷 > 고급 옵션** Cortana 요청 또는 **"Hey Cortana, 내 IP 주소는 무엇 인가요?"**</span><span class="sxs-lookup"><span data-stu-id="d93e1-179">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
    * <span data-ttu-id="d93e1-180">유지 된 **인증 모드** 로 설정 **유니버설**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-180">Leave the **Authentication Mode** set to **Universal**.</span></span>
    * <span data-ttu-id="d93e1-181">클릭 **선택**</span><span class="sxs-lookup"><span data-stu-id="d93e1-181">Click **Select**</span></span>
* <span data-ttu-id="d93e1-182">클릭 **디버그 > 디버깅 없이 시작** 누르거나 **ctrl+f5**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-182">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="d93e1-183">처음으로 장치에 배포할 경우 해야 [Visual Studio를 사용 하 여 쌍](using-visual-studio.md#pairing-your-device-hololens)합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-183">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
* <span data-ttu-id="d93e1-184">에 HoloLens에 놓고 EnergyHub 홀로그램을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-184">Put on your HoloLens and find the EnergyHub hologram.</span></span>

## <a name="chapter-2---interaction"></a><span data-ttu-id="d93e1-185">2 장-상호 작용</span><span class="sxs-lookup"><span data-stu-id="d93e1-185">Chapter 2 - Interaction</span></span>

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

<span data-ttu-id="d93e1-186">이 장에서 홀로그램 상호 작용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-186">In this chapter, we'll interact with our holograms.</span></span> <span data-ttu-id="d93e1-187">먼저 커서를 시각화에 추가한 우리의 [Gaze](gaze.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-187">First, we'll add a cursor to visualize our [Gaze](gaze.md).</span></span> <span data-ttu-id="d93e1-188">그런 다음 추가할 것 [제스처](gestures.md) 를 사용 하 여, 이제 직접 우리의 홀로그램 공간에 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-188">Then, we'll add [Gestures](gestures.md) and use our hand to place our holograms in space.</span></span>

### <a name="objectives"></a><span data-ttu-id="d93e1-189">목표</span><span class="sxs-lookup"><span data-stu-id="d93e1-189">Objectives</span></span>

* <span data-ttu-id="d93e1-190">커서를 제어 하려면 입력 게이즈를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-190">Use gaze input to control a cursor.</span></span>
* <span data-ttu-id="d93e1-191">홀로그램 상호 작용할 수 입력 제스처를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-191">Use gesture input to interact with holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="d93e1-192">지침</span><span class="sxs-lookup"><span data-stu-id="d93e1-192">Instructions</span></span>

<span data-ttu-id="d93e1-193">**응시**</span><span class="sxs-lookup"><span data-stu-id="d93e1-193">**Gaze**</span></span>
* <span data-ttu-id="d93e1-194">에 **계층 패널** 선택 합니다 **HologramCollection** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-194">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="d93e1-195">에 **검사기 패널** 클릭 합니다 **구성 요소 추가** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-195">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="d93e1-196">메뉴에서 검색 상자에 입력 **Gaze Manager**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-196">In the menu, type in the search box **Gaze Manager**.</span></span> <span data-ttu-id="d93e1-197">검색 결과 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-197">Select the search result.</span></span>
* <span data-ttu-id="d93e1-198">에 **HoloToolkit 공유 240\Prefabs\Input** 폴더를 찾기는 **커서** 자산입니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-198">In the **HoloToolkit-Sharing-240\Prefabs\Input** folder, find the **Cursor** asset.</span></span>
* <span data-ttu-id="d93e1-199">끌어서 놓기 합니다 **커서** 자산에는 **계층**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-199">Drag and drop the **Cursor** asset onto the **Hierarchy**.</span></span>

<span data-ttu-id="d93e1-200">**제스처**</span><span class="sxs-lookup"><span data-stu-id="d93e1-200">**Gesture**</span></span>
* <span data-ttu-id="d93e1-201">에 **계층 패널** 선택 합니다 **HologramCollection** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-201">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="d93e1-202">클릭 **Add Component** 유형과 **제스처 관리자** 검색 필드에 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-202">Click **Add Component** and type **Gesture Manager** in the search field.</span></span> <span data-ttu-id="d93e1-203">검색 결과 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-203">Select the search result.</span></span>
* <span data-ttu-id="d93e1-204">에 **계층 패널**를 확장 하 고 **HologramCollection**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-204">In the **Hierarchy panel**, expand **HologramCollection**.</span></span>
* <span data-ttu-id="d93e1-205">선택 된 자식 **EnergyHub** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-205">Select the child **EnergyHub** object.</span></span>
* <span data-ttu-id="d93e1-206">에 **검사기 패널** 클릭 합니다 **구성 요소 추가** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-206">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="d93e1-207">메뉴에서 검색 상자에 입력 **홀로그램 배치**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-207">In the menu, type in the search box **Hologram Placement**.</span></span> <span data-ttu-id="d93e1-208">검색 결과 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-208">Select the search result.</span></span>
* <span data-ttu-id="d93e1-209">선택 하 여 장면 저장 **파일 > 저장 장면**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-209">Save the scene by selecting **File > Save Scene**.</span></span>

<span data-ttu-id="d93e1-210">**배포 하 고 이용할 수 있습니다**</span><span class="sxs-lookup"><span data-stu-id="d93e1-210">**Deploy and enjoy**</span></span>
* <span data-ttu-id="d93e1-211">빌드 및 이전 장에서 지침을 사용 하 여 HoloLens에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-211">Build and deploy to your HoloLens, using the instructions from the previous chapter.</span></span>
* <span data-ttu-id="d93e1-212">앱이 출시 되 면 여 HoloLens, 머리를 이동 하 고는 EnergyHub 프로그램 게이즈를 따라가는 방법을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-212">Once the app launches on your HoloLens, move your head around and notice how the EnergyHub follows your gaze.</span></span>
* <span data-ttu-id="d93e1-213">커서를 홀로그램으로 gaze 때 표시 되 고를 홀로그램에서 gazing 되지 경우 점 광원으로 변경 하는 방법을 살펴보세요.</span><span class="sxs-lookup"><span data-stu-id="d93e1-213">Notice how the cursor appears when you gaze upon the hologram, and changes to a point light when not gazing at a hologram.</span></span>
* <span data-ttu-id="d93e1-214">홀로그램 배치에 어 탭을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-214">Perform an air-tap to place the hologram.</span></span> <span data-ttu-id="d93e1-215">프로젝트에서이 이번에는 홀로그램 한 번 (다시 시도에 다시 배포)만 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-215">At this time in our project, you can only place the hologram once (redeploy to try again).</span></span>

## <a name="chapter-3---shared-coordinates"></a><span data-ttu-id="d93e1-216">3 장-공유 조정</span><span class="sxs-lookup"><span data-stu-id="d93e1-216">Chapter 3 - Shared Coordinates</span></span>

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

<span data-ttu-id="d93e1-217">재미를 확인 하 여 홀로그램, 상호 작용 하지만 나아가 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-217">It's fun to see and interact with holograms, but let's go further.</span></span> <span data-ttu-id="d93e1-218">첫 번째 공유 경험-모든 사람이 함께 볼 수는 홀로그램 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-218">We'll set up our first shared experience - a hologram everyone can see together.</span></span>

### <a name="objectives"></a><span data-ttu-id="d93e1-219">목표</span><span class="sxs-lookup"><span data-stu-id="d93e1-219">Objectives</span></span>

* <span data-ttu-id="d93e1-220">공유 경험에 대 한 네트워크를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-220">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="d93e1-221">공용 참조 지점을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-221">Establish a common reference point.</span></span>
* <span data-ttu-id="d93e1-222">장치의 좌표 시스템을 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-222">Share coordinate systems across devices.</span></span>
* <span data-ttu-id="d93e1-223">모든 사용자가 동일한 홀로그램 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-223">Everyone sees the same hologram!</span></span>

>[!NOTE]
><span data-ttu-id="d93e1-224">합니다 **InternetClientServer** 하 고 **PrivateNetworkClientServer** 공유 서버에 연결 하는 앱에 대 한 기능을 선언 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-224">The **InternetClientServer** and **PrivateNetworkClientServer** capabilities must be declared for an app to connect to the sharing server.</span></span> <span data-ttu-id="d93e1-225">이루어지는를 이미 홀로그램 240 하지만이 사용자의 프로젝트에 대 한 염두에 둡니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-225">This is done for you already in Holograms 240, but keep this in mind for your own projects.</span></span>
>1. <span data-ttu-id="d93e1-226">Unity 편집기에서 "> 프로젝트 설정 > Player 편집"로 이동 하 여 플레이어 설정으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-226">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="d93e1-227">"Windows Store" 탭을 클릭</span><span class="sxs-lookup"><span data-stu-id="d93e1-227">Click on the "Windows Store" tab</span></span>
>3. <span data-ttu-id="d93e1-228">"게시 설정 > 기능" 섹션을 확인 합니다 **InternetClientServer** 기능 하며 **PrivateNetworkClientServer** 기능</span><span class="sxs-lookup"><span data-stu-id="d93e1-228">In the "Publishing Settings > Capabilities" section, check the **InternetClientServer** capability and the **PrivateNetworkClientServer** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="d93e1-229">지침</span><span class="sxs-lookup"><span data-stu-id="d93e1-229">Instructions</span></span>

* <span data-ttu-id="d93e1-230">에 **프로젝트 패널** 로 이동 합니다 **HoloToolkit 공유 240\Prefabs\Sharing** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-230">In the **Project panel** navigate to the **HoloToolkit-Sharing-240\Prefabs\Sharing** folder.</span></span>
* <span data-ttu-id="d93e1-231">끌어서 놓기 합니다 **공유** 으로 prefab 합니다 **계층 패널**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-231">Drag and drop the **Sharing** prefab into the **Hierarchy panel**.</span></span>

<span data-ttu-id="d93e1-232">다음 공유 서비스를 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-232">Next we need to launch the sharing service.</span></span> <span data-ttu-id="d93e1-233">만 **PC** 공유 환경이 단계를 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-233">Only **one PC** in the shared experience needs to do this step.</span></span>
* <span data-ttu-id="d93e1-234">Unity-는 위 메뉴에서 선택 합니다 **HoloToolkit 공유 240 메뉴**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-234">In Unity - in the top-hand menu - select the **HoloToolkit-Sharing-240 menu**.</span></span>
* <span data-ttu-id="d93e1-235">선택 된 **공유 서비스 시작** 드롭다운 목록에서 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-235">Select the **Launch Sharing Service** item in the drop-down.</span></span>
* <span data-ttu-id="d93e1-236">확인 합니다 **사설망** 옵션을 클릭 **액세스를 허용** 방화벽 프롬프트를 표시 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="d93e1-236">Check the **Private Network** option and click **Allow Access** when the firewall prompt appears.</span></span>
* <span data-ttu-id="d93e1-237">공유 서비스 콘솔 창에 표시 된 IPv4 주소를 적어 note 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-237">Note down the IPv4 address displayed in the Sharing Service console window.</span></span> <span data-ttu-id="d93e1-238">서비스에서 실행 되는 컴퓨터와 동일한 IP입니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-238">This is the same IP as the machine the service is being run on.</span></span>

<span data-ttu-id="d93e1-239">지침 따릅니다 **모든 Pc** 는 공유 환경에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-239">Follow the rest of the instructions on **all PCs** that will join the shared experience.</span></span>
* <span data-ttu-id="d93e1-240">에 **계층**를 선택 합니다 **공유** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-240">In the **Hierarchy**, select the **Sharing** object.</span></span>
* <span data-ttu-id="d93e1-241">에 **검사기**의 **공유 단계** 구성 요소를 변경 합니다 **서버 주소** 'localhost' SharingService.exe를 실행 하는 컴퓨터의 IPv4 주소에서.</span><span class="sxs-lookup"><span data-stu-id="d93e1-241">In the **Inspector**, on the **Sharing Stage** component, change the **Server Address** from 'localhost' to the IPv4 address of the machine running SharingService.exe.</span></span>
* <span data-ttu-id="d93e1-242">에 **계층 구조** 선택 합니다 **HologramCollection** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-242">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="d93e1-243">에 **검사기** 클릭 합니다 **구성 요소 추가** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-243">In the **Inspector** click the **Add Component** button.</span></span>
* <span data-ttu-id="d93e1-244">검색 상자에 입력 **가져오기 내보내기 앵커 Manager**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-244">In the search box, type **Import Export Anchor Manager**.</span></span> <span data-ttu-id="d93e1-245">검색 결과 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-245">Select the search result.</span></span>
* <span data-ttu-id="d93e1-246">에 **프로젝트 패널** 로 이동 합니다 **스크립트** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-246">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="d93e1-247">두 번 클릭 합니다 **HologramPlacement** 스크립트 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-247">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="d93e1-248">내용을 아래 코드로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-248">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the anchor model.
    /// The anchor model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    private bool animationPlayed = false;

    void Start()
    {
        // We care about getting updates for the anchor transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the anchor transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the anchor if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    void Update()
    {
        if (GotTransform)
        {
            if (ImportExportAnchorManager.Instance.AnchorEstablished &&
                animationPlayed == false)
            {
                // This triggers the animation sequence for the anchor model and 
                // puts the cool materials on the model.
                GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                animationPlayed = true;
            }
        }
        else
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the anchor 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;
        
        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the anchor to do its animation and
        // swap its materials.
        if (GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* <span data-ttu-id="d93e1-249">Unity에서 다시 선택 합니다 **HologramCollection** 에 **계층 패널**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-249">Back in Unity, select the **HologramCollection** in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="d93e1-250">에 **검사기 패널** 클릭 합니다 **구성 요소 추가** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-250">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="d93e1-251">메뉴에서 검색 상자에 입력 **앱 상태 관리자**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-251">In the menu, type in the search box **App State Manager**.</span></span> <span data-ttu-id="d93e1-252">검색 결과 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-252">Select the search result.</span></span>

<span data-ttu-id="d93e1-253">**배포 하 고 이용할 수 있습니다**</span><span class="sxs-lookup"><span data-stu-id="d93e1-253">**Deploy and enjoy**</span></span>
* <span data-ttu-id="d93e1-254">HoloLens 장치에 대 한 프로젝트를 빌드하십시오.</span><span class="sxs-lookup"><span data-stu-id="d93e1-254">Build the project for your HoloLens devices.</span></span>
* <span data-ttu-id="d93e1-255">첫 번째를 배포 하려면 하나의 HoloLens를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-255">Designate one HoloLens to deploy to first.</span></span> <span data-ttu-id="d93e1-256">앵커는 EnergyHub 저장 하기 전에 서비스에 업로드할 때까지 대기 해야 합니다 (정도 걸리며 ~ 30 ~ 60 초)입니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-256">You will need to wait for the Anchor to be uploaded to the service before you can place the EnergyHub (this can take ~30-60 seconds).</span></span> <span data-ttu-id="d93e1-257">업로드가 완료 될 때까지 탭 제스처는 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-257">Until the upload is done, your tap gestures will be ignored.</span></span>
* <span data-ttu-id="d93e1-258">EnergyHub 배치 된 후 서비스에 업로드할 해당 위치 및 다른 모든 HoloLens 장치에 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-258">After the EnergyHub has been placed, its location will be uploaded to the service and you can then deploy to all other HoloLens devices.</span></span>
* <span data-ttu-id="d93e1-259">새 HoloLens 세션에 먼저 가입는 EnergyHub 위치의 해당 장치에서 올바르지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-259">When a new HoloLens first joins the session, the location of the EnergyHub may not be correct on that device.</span></span> <span data-ttu-id="d93e1-260">그러나 앵커 및 EnergyHub 위치 서비스에서 다운로드 했거나, 즉시는 EnergyHub 새, 공유 위치로 이동 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-260">However, as soon as the anchor and EnergyHub locations have been downloaded from the service, the EnergyHub should jump to the new, shared location.</span></span> <span data-ttu-id="d93e1-261">이 ~ 30 ~ 60 내에서 발생 하지 않습니다 하는 경우 시간 (초), 자세한 환경을 위한 정보 수집에 앵커를 설정할 때 원래 HoloLens가를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-261">If this does not happen within ~30-60 seconds, walk to where the original HoloLens was when setting the anchor to gather more environment clues.</span></span> <span data-ttu-id="d93e1-262">위치 잠그지 않습니다 하는 경우에 장치에 다시 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-262">If the location still does not lock on, redeploy to the device.</span></span>
* <span data-ttu-id="d93e1-263">경우 장치는 모두 준비 하 고 앱을 실행 합니다 EnergyHub 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-263">When the devices are all ready and running the app, look for the EnergyHub.</span></span> <span data-ttu-id="d93e1-264">홀로그램의 위치에 모두 동의할 수 방향을 텍스트 연결 및?</span><span class="sxs-lookup"><span data-stu-id="d93e1-264">Can you all agree on the hologram's location and which direction the text is facing?</span></span>

## <a name="chapter-4---discovery"></a><span data-ttu-id="d93e1-265">4 장-검색</span><span class="sxs-lookup"><span data-stu-id="d93e1-265">Chapter 4 - Discovery</span></span>

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

<span data-ttu-id="d93e1-266">이제 동일한 홀로그램을 볼 수 있습니다 everyone!</span><span class="sxs-lookup"><span data-stu-id="d93e1-266">Everyone can now see the same hologram!</span></span> <span data-ttu-id="d93e1-267">이제 공유 holographic 세계에 연결 된 다른 모든 사용자를 확인해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-267">Now let's see everyone else connected to our shared holographic world.</span></span> <span data-ttu-id="d93e1-268">이 챕터에서는 헤드 위치와 같은 공유 세션에서 다른 모든 HoloLens 장치 회전을 잡고 됩니다 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-268">In this chapter, we'll grab the head location and rotation of all other HoloLens devices in the same sharing session.</span></span>

### <a name="objectives"></a><span data-ttu-id="d93e1-269">목표</span><span class="sxs-lookup"><span data-stu-id="d93e1-269">Objectives</span></span>

* <span data-ttu-id="d93e1-270">공유 경험에서 서로 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-270">Discover each other in our shared experience.</span></span>
* <span data-ttu-id="d93e1-271">선택 하 고 플레이어 아바타를 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-271">Choose and share a player avatar.</span></span>
* <span data-ttu-id="d93e1-272">모든 사용자의 헤드 옆에 있는 플레이어 아바타를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-272">Attach the player avatar next to everyone's heads.</span></span>

### <a name="instructions"></a><span data-ttu-id="d93e1-273">지침</span><span class="sxs-lookup"><span data-stu-id="d93e1-273">Instructions</span></span>

* <span data-ttu-id="d93e1-274">에 **프로젝트 패널** 로 이동 합니다 **홀로그램** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-274">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="d93e1-275">끌어서 놓기 합니다 **PlayerAvatarStore** 에 **계층**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-275">Drag and drop the **PlayerAvatarStore** into the **Hierarchy**.</span></span>
* <span data-ttu-id="d93e1-276">에 **프로젝트 패널** 로 이동 합니다 **스크립트** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-276">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="d93e1-277">두 번 클릭 합니다 **AvatarSelector** 스크립트 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-277">Double-click the **AvatarSelector** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="d93e1-278">내용을 아래 코드로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-278">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Script to handle the user selecting the avatar.
/// </summary>
public class AvatarSelector : MonoBehaviour
{
    /// <summary>
    /// This is the index set by the PlayerAvatarStore for the avatar.
    /// </summary>
    public int AvatarIndex { get; set; }

    /// <summary>
    /// Called when the user is gazing at this avatar and air-taps it.
    /// This sends the user's selection to the rest of the devices in the experience.
    /// </summary>
    void OnSelect()
    {
        PlayerAvatarStore.Instance.DismissAvatarPicker();

        LocalPlayerManager.Instance.SetUserAvatar(AvatarIndex);        
    }

    void Start()
    {
        // Add Billboard component so the avatar always faces the user.
        Billboard billboard = gameObject.GetComponent<Billboard>();
        if (billboard == null)
        {
            billboard = gameObject.AddComponent<Billboard>();
        }

        // Lock rotation along the Y axis.
        billboard.PivotAxis = PivotAxis.Y;
    }
}
```

* <span data-ttu-id="d93e1-279">에 **계층 구조** 선택 합니다 **HologramCollection** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-279">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="d93e1-280">에 **검사기** 클릭 **구성 요소 추가**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-280">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="d93e1-281">검색 상자에 입력 **로컬 플레이어 관리자**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-281">In the search box, type **Local Player Manager**.</span></span> <span data-ttu-id="d93e1-282">검색 결과 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-282">Select the search result.</span></span>
* <span data-ttu-id="d93e1-283">에 **계층 구조** 선택 합니다 **HologramCollection** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-283">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="d93e1-284">에 **검사기** 클릭 **구성 요소 추가**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-284">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="d93e1-285">검색 상자에 입력 **원격 Player Manager**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-285">In the search box, type **Remote Player Manager**.</span></span> <span data-ttu-id="d93e1-286">검색 결과 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-286">Select the search result.</span></span>
* <span data-ttu-id="d93e1-287">엽니다는 **HologramPlacement** Visual Studio의 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-287">Open the **HologramPlacement** script in Visual Studio.</span></span>
* <span data-ttu-id="d93e1-288">내용을 아래 코드로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-288">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and 
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the model 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* <span data-ttu-id="d93e1-289">엽니다는 **AppStateManager** Visual Studio의 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-289">Open the **AppStateManager** script in Visual Studio.</span></span>
* <span data-ttu-id="d93e1-290">내용을 아래 코드로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-290">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        WaitingForAnchor,
        WaitingForStageTransform,
        PickingAvatar,
        Ready
    }

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // We start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = null;
                }
                break;
        }
    }
}
```

<span data-ttu-id="d93e1-291">**배포 하 고 이용할 수 있습니다**</span><span class="sxs-lookup"><span data-stu-id="d93e1-291">**Deploy and Enjoy**</span></span>
* <span data-ttu-id="d93e1-292">빌드 및 HoloLens 장치에 프로젝트를 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-292">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="d93e1-293">대 한 ping 소리가 아바타 선택 메뉴을 어 탭 제스처를 사용 하 여 아바타를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-293">When you hear a pinging sound, find the avatar selection menu and select an avatar with the air-tap gesture.</span></span>
* <span data-ttu-id="d93e1-294">모든 홀로그램을 확인 하지 하는 경우 커서 주위 밝은 지점 바뀝니다 다른 색에 HoloLens 서비스와 통신 하는 경우: 초기화 (진한 자주색), 위치 데이터 (노란색) 가져오기/내보내기 앵커 (녹색) 다운로드 앵커 (파란색)을 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-294">If you're not looking at any holograms, the point light around your cursor will turn a different color when your HoloLens is communicating with the service: initializing (dark purple), downloading the anchor (green), importing/exporting location data (yellow), uploading the anchor (blue).</span></span> <span data-ttu-id="d93e1-295">커서 주위 밝은 지점과 기본 색 (옅은 자주) 인 경우 다음 준비가 세션에서 다른 플레이어와 상호 작용.</span><span class="sxs-lookup"><span data-stu-id="d93e1-295">If your point light around your cursor is the default color (light purple), then you are ready to interact with other players in your session!</span></span>
* <span data-ttu-id="d93e1-296">다른 사용자를 살펴보고 공간-에 연결 됩니다 해당 자격 증명 입력 위에 부동 및 해당 헤드 동작이 모방 holographic 로봇!</span><span class="sxs-lookup"><span data-stu-id="d93e1-296">Look at other people connected to your space - there will be a holographic robot floating above their shoulder and mimicking their head motions!</span></span>

## <a name="chapter-5---placement"></a><span data-ttu-id="d93e1-297">5 장-배치</span><span class="sxs-lookup"><span data-stu-id="d93e1-297">Chapter 5 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

<span data-ttu-id="d93e1-298">이 챕터에서는 실제 화면에 배치할 수 앵커를 만들 수 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-298">In this chapter, we'll make the anchor able to be placed on real-world surfaces.</span></span> <span data-ttu-id="d93e1-299">공유 좌표는 앵커 공유 환경에 연결 된 모든 사용자 사이의 중간 지점 전환 사용 하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-299">We'll use shared coordinates to place that anchor in the middle point between everyone connected to the shared experience.</span></span>

### <a name="objectives"></a><span data-ttu-id="d93e1-300">목표</span><span class="sxs-lookup"><span data-stu-id="d93e1-300">Objectives</span></span>

* <span data-ttu-id="d93e1-301">홀로그램 플레이어의 헤드 위치에 따라 공간 지도에 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-301">Place holograms on the spatial map based on players’ head position.</span></span>

### <a name="instructions"></a><span data-ttu-id="d93e1-302">지침</span><span class="sxs-lookup"><span data-stu-id="d93e1-302">Instructions</span></span>

* <span data-ttu-id="d93e1-303">에 **프로젝트 패널** 로 이동 합니다 **홀로그램** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-303">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="d93e1-304">끌어서 놓기는 **CustomSpatialMapping** 끌어다 prefab 합니다 **계층**.</span><span class="sxs-lookup"><span data-stu-id="d93e1-304">Drag and drop the **CustomSpatialMapping** prefab onto the **Hierarchy**.</span></span>
* <span data-ttu-id="d93e1-305">에 **프로젝트 패널** 로 이동 합니다 **스크립트** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-305">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="d93e1-306">두 번 클릭 합니다 **AppStateManager** 스크립트 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-306">Double-click the **AppStateManager** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="d93e1-307">내용을 아래 코드로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-307">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        PickingAvatar,
        WaitingForAnchor,
        WaitingForStageTransform,
        Ready
    }

    // The object to call to make a projectile.
    GameObject shootHandler = null;

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // The shootHandler shoots projectiles.
        if (GetComponent<ProjectileLauncher>() != null)
        {
            shootHandler = GetComponent<ProjectileLauncher>().gameObject;
        }

        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // Spatial mapping should be disabled when we start up so as not
        // to distract from the avatar picking.
        SpatialMappingManager.Instance.StopObserver();
        SpatialMappingManager.Instance.gameObject.SetActive(false);

        // On device we start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    public void ResetStage()
    {
        // If we fall back to waiting for anchor, everything needed to 
        // get us into setting the target transform state will be setup.
        if (CurrentAppState != AppState.PickingAvatar)
        {
            CurrentAppState = AppState.WaitingForAnchor;
        }

        // Reset the underworld.
        if (UnderworldBase.Instance)
        {
            UnderworldBase.Instance.ResetUnderworld();
        }
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                // Once the anchor is established we need to run spatial mapping for a 
                // little while to build up some meshes.
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;

                    SpatialMappingManager.Instance.gameObject.SetActive(true);
                    SpatialMappingManager.Instance.DrawVisualMeshes = true;
                    SpatialMappingDeformation.Instance.ResetGlobalRendering();
                    SpatialMappingManager.Instance.StartObserver();
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = shootHandler;
                }
                break;
        }
    }
}
```

* <span data-ttu-id="d93e1-308">에 **프로젝트 패널** 로 이동 합니다 **스크립트** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-308">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="d93e1-309">두 번 클릭 합니다 **HologramPlacement** 스크립트 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-309">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="d93e1-310">내용을 아래 코드로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-310">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    /// <summary>
    /// We use a voice command to enable moving the target.
    /// </summary>
    KeywordRecognizer keywordRecognizer;

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;

        // And if the users want to reset the stage transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.ResetStage] = this.OnResetStage;

        // Setup a keyword recognizer to enable resetting the target location.
        List<string> keywords = new List<string>();
        keywords.Add("Reset Target");
        keywordRecognizer = new KeywordRecognizer(keywords.ToArray());
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    /// <summary>
    /// When the keyword recognizer hears a command this will be called.  
    /// In this case we only have one keyword, which will re-enable moving the 
    /// target.
    /// </summary>
    /// <param name="args">information to help route the voice command.</param>
    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        ResetStage();
    }

    /// <summary>
    /// Resets the stage transform, so users can place the target again.
    /// </summary>
    public void ResetStage()
    {
        GotTransform = false;

        // AppStateManager needs to know about this so that
        // the right objects get input routed to them.
        AppStateManager.Instance.ResetStage();

        // Other devices in the experience need to know about this as well.
        CustomMessages.Instance.SendResetStage();

        // And we need to reset the object to its start animation state.
        GetComponent<EnergyHubBase>().ResetAnimation();
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and 
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        Vector3 retval;
        // We need to know how many users are in the experience with good transforms.
        Vector3 cumulatedPosition = Camera.main.transform.position;
        int playerCount = 1;
        foreach (RemotePlayerManager.RemoteHeadInfo remoteHead in RemotePlayerManager.Instance.remoteHeadInfos)
        {
            if (remoteHead.Anchored && remoteHead.Active)
            {
                playerCount++;
                cumulatedPosition += remoteHead.HeadObject.transform.position;
            }
        }

        // If we have more than one player ...
        if (playerCount > 1)
        {
            // Put the transform in between the players.
            retval = cumulatedPosition / playerCount;
            RaycastHit hitInfo;

            // And try to put the transform on a surface below the midpoint of the players.
            if (Physics.Raycast(retval, Vector3.down, out hitInfo, 5, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
        }
        // If we are the only player, have the model act as the 'cursor' ...
        else
        {
            // We prefer to put the model on a real world surface.
            RaycastHit hitInfo;

            if (Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, 30, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
            else
            {
                // But if we don't have a ray that intersects the real world, just put the model 2m in
                // front of the user.
                retval = Camera.main.transform.position + Camera.main.transform.forward * 2;
            }
        }
        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    void OnResetStage(NetworkInMessage msg)
    {
        GotTransform = false;

        GetComponent<EnergyHubBase>().ResetAnimation();
        AppStateManager.Instance.ResetStage();
    }
}
```

<span data-ttu-id="d93e1-311">**배포 하 고 이용할 수 있습니다**</span><span class="sxs-lookup"><span data-stu-id="d93e1-311">**Deploy and enjoy**</span></span>
* <span data-ttu-id="d93e1-312">빌드 및 HoloLens 장치에 프로젝트를 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-312">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="d93e1-313">앱 준비 되 면 원에 구축 하 고는 EnergyHub everyone의 가운데에 표시 되는 방식을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-313">When the app is ready, stand in a circle and notice how the EnergyHub appears in the center of everyone.</span></span>
* <span data-ttu-id="d93e1-314">EnergyHub 배치 하려면 탭 하세요.</span><span class="sxs-lookup"><span data-stu-id="d93e1-314">Tap to place the EnergyHub.</span></span>
* <span data-ttu-id="d93e1-315">홀로그램을 새 위치로 이동할 대상 재설정 '는 EnergyHub 다시 선택 하 고 그룹으로 함께 작동을 음성 명령을 실행 하십시오.</span><span class="sxs-lookup"><span data-stu-id="d93e1-315">Try the voice command 'Reset Target' to pick the EnergyHub back up and work together as a group to move the hologram to a new location.</span></span>

## <a name="chapter-6---real-world-physics"></a><span data-ttu-id="d93e1-316">6 장-실제 물리학</span><span class="sxs-lookup"><span data-stu-id="d93e1-316">Chapter 6 - Real-World Physics</span></span>

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

<span data-ttu-id="d93e1-317">이 장에서 실제 화면 히 면 튀어 홀로그램 추가 하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-317">In this chapter we'll add holograms that bounce off real-world surfaces.</span></span> <span data-ttu-id="d93e1-318">가득 차와 친구에서 시작 하는 프로젝트에 공간을 시청 하세요.</span><span class="sxs-lookup"><span data-stu-id="d93e1-318">Watch your space fill up with projects launched by both you and your friends!</span></span>

### <a name="objectives"></a><span data-ttu-id="d93e1-319">목표</span><span class="sxs-lookup"><span data-stu-id="d93e1-319">Objectives</span></span>

* <span data-ttu-id="d93e1-320">실제 화면 히 면 튀어 무기를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-320">Launch projectiles that bounce off real-world surfaces.</span></span>
* <span data-ttu-id="d93e1-321">다른 플레이어 볼 수 있도록 합니다 무기를 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-321">Share the projectiles so other players can see them.</span></span>

### <a name="instructions"></a><span data-ttu-id="d93e1-322">지침</span><span class="sxs-lookup"><span data-stu-id="d93e1-322">Instructions</span></span>

* <span data-ttu-id="d93e1-323">에 **계층 구조** 선택 합니다 **HologramCollection** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-323">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="d93e1-324">에 **검사기** 클릭 **구성 요소 추가**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-324">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="d93e1-325">검색 상자에 입력 **멀리 Launcher**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-325">In the search box, type **Projectile Launcher**.</span></span> <span data-ttu-id="d93e1-326">검색 결과 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-326">Select the search result.</span></span>

<span data-ttu-id="d93e1-327">**배포 하 고 이용할 수 있습니다**</span><span class="sxs-lookup"><span data-stu-id="d93e1-327">**Deploy and enjoy**</span></span>
* <span data-ttu-id="d93e1-328">빌드 및 HoloLens 장치에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-328">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="d93e1-329">모든 장치에서 앱 실행 중일 때 실제 화면에서 멀리 시작에 어 탭을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-329">When the app is running on all devices, perform an air-tap to launch projectile at real world surfaces.</span></span>
* <span data-ttu-id="d93e1-330">프로그램 멀리 다른 플레이어의 아바타와 충돌 하는 경우를 확인 하세요!</span><span class="sxs-lookup"><span data-stu-id="d93e1-330">See what happens when your projectile collides with another player's avatar!</span></span>

## <a name="chapter-7---grand-finale"></a><span data-ttu-id="d93e1-331">7 장-실현할</span><span class="sxs-lookup"><span data-stu-id="d93e1-331">Chapter 7 - Grand Finale</span></span>

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

<span data-ttu-id="d93e1-332">이 챕터에서는 공동 작업을 사용 하 여 검색할 수 있는 포털을 찾아 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-332">In this chapter, we'll uncover a portal that can only be discovered with collaboration.</span></span>

### <a name="objectives"></a><span data-ttu-id="d93e1-333">목표</span><span class="sxs-lookup"><span data-stu-id="d93e1-333">Objectives</span></span>

* <span data-ttu-id="d93e1-334">암호 포털을 파악 하는 앵커에 충분 한 무기를 시작 하려면 함께!</span><span class="sxs-lookup"><span data-stu-id="d93e1-334">Work together to launch enough projectiles at the anchor to uncover a secret portal!</span></span>

### <a name="instructions"></a><span data-ttu-id="d93e1-335">지침</span><span class="sxs-lookup"><span data-stu-id="d93e1-335">Instructions</span></span>

* <span data-ttu-id="d93e1-336">에 **프로젝트 패널** 로 이동 합니다 **홀로그램** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-336">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="d93e1-337">끌어서 놓기 합니다 **지 하** 자산을 **HologramCollection 자식의**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-337">Drag and drop the **Underworld** asset as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="d93e1-338">사용 하 여 **HologramCollection** 선택 합니다 **구성 요소 추가** 단추를 **검사기**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-338">With **HologramCollection** selected, click the **Add Component** button in the **Inspector**.</span></span>
* <span data-ttu-id="d93e1-339">메뉴에서 검색 상자에 입력 **ExplodeTarget**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-339">In the menu, type in the search box **ExplodeTarget**.</span></span> <span data-ttu-id="d93e1-340">검색 결과 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-340">Select the search result.</span></span>
* <span data-ttu-id="d93e1-341">사용 하 여 **HologramCollection** 에서 선택한를 **계층** 끌어 합니다 **EnergyHub** 개체를 **대상** 필드에 **검사기**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-341">With **HologramCollection** selected, from the **Hierarchy** drag the **EnergyHub** object to the **Target** field in the **Inspector**.</span></span>
* <span data-ttu-id="d93e1-342">사용 하 여 **HologramCollection** 에서 선택한 합니다 **계층** 끌어를 **지 하** 개체를 **지 하** 필드에  **검사기**합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-342">With **HologramCollection** selected, from the **Hierarchy** drag the **Underworld** object to the **Underworld** field in the **Inspector**.</span></span>

<span data-ttu-id="d93e1-343">**배포 하 고 이용할 수 있습니다**</span><span class="sxs-lookup"><span data-stu-id="d93e1-343">**Deploy and enjoy**</span></span>
* <span data-ttu-id="d93e1-344">빌드 및 HoloLens 장치에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-344">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="d93e1-345">앱이 시작 되는 EnergyHub에서 무기를 시작 하려면 공동 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-345">When the app has launched, collaborate together to launch projectiles at the EnergyHub.</span></span>
* <span data-ttu-id="d93e1-346">지 하 세계에는 다음이 표시 되 면 무기 지 하 로봇 (적중 추가 재미 있는 작업에 대해 세 번 로봇)에서 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="d93e1-346">When the underworld appears, launch projectiles at underworld robots (hit a robot three times for extra fun).</span></span>
