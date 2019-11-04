---
title: MR 공유 240-여러 HoloLens 장치
description: Holograms를 공유 하는 방법에 대 한 자세한 내용은 Unity, Visual Studio 및 HoloLens를 사용 하 여이 코딩 연습을 따르세요.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, 공유, 네트워킹, 아카데미, 자습서
ms.openlocfilehash: 0d8e8f4484546d82caadf162623a6f4059eb2f00
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434571"
---
>[!NOTE]
><span data-ttu-id="8446e-104">혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="8446e-105">따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="8446e-106">이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="8446e-107">지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="8446e-108">HoloLens 2에 대 한 [새로운 일련의 자습서](mrlearning-base.md) 가 게시 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-sharing-240-multiple-hololens-devices"></a><span data-ttu-id="8446e-109">MR 공유 240: 여러 HoloLens 장치</span><span class="sxs-lookup"><span data-stu-id="8446e-109">MR Sharing 240: Multiple HoloLens devices</span></span>

<span data-ttu-id="8446e-110">Holograms는 공간에서 이동 하면서 전 세계에 남아 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-110">Holograms are given presence in our world by remaining in place as we move about in space.</span></span> <span data-ttu-id="8446e-111">HoloLens는 다양 한 [좌표계](coordinate-systems.md) 를 사용 하 여 개체의 위치와 방향을 추적 하는 방식으로 holograms을 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-111">HoloLens keeps holograms in place by using various [coordinate systems](coordinate-systems.md) to keep track of the location and orientation of objects.</span></span> <span data-ttu-id="8446e-112">이러한 좌표계를 장치 간에 공유할 때 공유 holographic 세계에 참여 하는 데 사용할 수 있는 공유 환경을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-112">When we share these coordinate systems between devices, we can create a shared experience that allows us to take part in a shared holographic world.</span></span>

<span data-ttu-id="8446e-113">이 자습서에서는 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-113">In this tutorial, we will:</span></span>

* <span data-ttu-id="8446e-114">공유 환경의 네트워크를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-114">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="8446e-115">HoloLens 장치 간에 holograms을 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-115">Share holograms across HoloLens devices.</span></span>
* <span data-ttu-id="8446e-116">공유 holographic 세계에서 다른 사람을 검색 하세요.</span><span class="sxs-lookup"><span data-stu-id="8446e-116">Discover other people in our shared holographic world.</span></span>
* <span data-ttu-id="8446e-117">다른 플레이어를 대상으로 하 고 projectiles를 시작할 수 있는 공유 대화형 환경을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-117">Create a shared interactive experience where you can target other players - and launch projectiles at them!</span></span>

## <a name="device-support"></a><span data-ttu-id="8446e-118">장치 지원</span><span class="sxs-lookup"><span data-stu-id="8446e-118">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="8446e-119">과정</span><span class="sxs-lookup"><span data-stu-id="8446e-119">Course</span></span></th><th style="width:150px"> <span data-ttu-id="8446e-120"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="8446e-120"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="8446e-121"><a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="8446e-121"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="8446e-122">MR 공유 240: 여러 HoloLens 장치</span><span class="sxs-lookup"><span data-stu-id="8446e-122">MR Sharing 240: Multiple HoloLens devices</span></span></td><td style="text-align: center;"> <span data-ttu-id="8446e-123">✔️</span><span class="sxs-lookup"><span data-stu-id="8446e-123">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="8446e-124">시작하기 전 확인 사항</span><span class="sxs-lookup"><span data-stu-id="8446e-124">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="8446e-125">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="8446e-125">Prerequisites</span></span>

* <span data-ttu-id="8446e-126">인터넷 액세스로 설치 된 올바른 [도구로](install-the-tools.md) 구성 된 WINDOWS 10 PC</span><span class="sxs-lookup"><span data-stu-id="8446e-126">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md) with Internet access.</span></span>
* <span data-ttu-id="8446e-127">개발용으로 두 개 이상의 HoloLens 장치를 [구성](using-visual-studio.md#enabling-developer-mode)했습니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-127">At least two HoloLens devices [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="8446e-128">프로젝트 파일</span><span class="sxs-lookup"><span data-stu-id="8446e-128">Project files</span></span>

* <span data-ttu-id="8446e-129">프로젝트에 필요한 [파일](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) 을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-129">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) required by the project.</span></span> <span data-ttu-id="8446e-130">Unity 2017.2 이상이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-130">Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="8446e-131">Unity 5.6 지원이 계속 필요한 경우 [이 릴리스](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip)를 사용 하세요.</span><span class="sxs-lookup"><span data-stu-id="8446e-131">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).</span></span>
  * <span data-ttu-id="8446e-132">Unity 5.5 지원이 계속 필요한 경우 [이 릴리스](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip)를 사용 하세요.</span><span class="sxs-lookup"><span data-stu-id="8446e-132">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).</span></span>
  * <span data-ttu-id="8446e-133">Unity 5.4 지원이 계속 필요한 경우 [이 릴리스](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip)를 사용 하세요.</span><span class="sxs-lookup"><span data-stu-id="8446e-133">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).</span></span>
* <span data-ttu-id="8446e-134">바탕 화면 또는 기타 쉬운 위치에 파일을 보관 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-134">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="8446e-135">폴더 이름을 **SharedHolograms**로 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-135">Keep the folder name as **SharedHolograms**.</span></span>

>[!NOTE]
><span data-ttu-id="8446e-136">다운로드 하기 전에 소스 코드를 확인 하려는 경우 [GitHub에서 사용할 수](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms)있습니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-136">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="8446e-137">1 장-Holo 세계</span><span class="sxs-lookup"><span data-stu-id="8446e-137">Chapter 1 - Holo World</span></span>

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

<span data-ttu-id="8446e-138">이 장에서는 첫 번째 Unity 프로젝트를 설정 하 고 빌드 및 배포 프로세스를 단계별로 진행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-138">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="8446e-139">목표</span><span class="sxs-lookup"><span data-stu-id="8446e-139">Objectives</span></span>

* <span data-ttu-id="8446e-140">Holographic apps를 개발 하는 Unity를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-140">Setup Unity to develop holographic apps.</span></span>
* <span data-ttu-id="8446e-141">홀로그램을 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="8446e-141">See your hologram!</span></span>

### <a name="instructions"></a><span data-ttu-id="8446e-142">지침</span><span class="sxs-lookup"><span data-stu-id="8446e-142">Instructions</span></span>

* <span data-ttu-id="8446e-143">Unity를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-143">Start Unity.</span></span>
* <span data-ttu-id="8446e-144">**열기**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-144">Select **Open**.</span></span>
* <span data-ttu-id="8446e-145">이전에 unarchived **SharedHolograms** 폴더로 위치를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-145">Enter location as the **SharedHolograms** folder you previously unarchived.</span></span>
* <span data-ttu-id="8446e-146">**프로젝트 이름** 을 선택 하 고 **폴더 선택**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-146">Select **Project Name** and click **Select Folder**.</span></span>
* <span data-ttu-id="8446e-147">**계층**에서 **주 카메라** 를 마우스 오른쪽 단추로 클릭 하 고 **삭제**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-147">In the **Hierarchy**, right-click the **Main Camera** and select **Delete**.</span></span>
* <span data-ttu-id="8446e-148">HoloToolkit- **240/Prefabs/카메라** 폴더에서 **기본 카메라** prefab를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-148">In the **HoloToolkit-Sharing-240/Prefabs/Camera** folder, find the **Main Camera** prefab.</span></span>
* <span data-ttu-id="8446e-149">**주 카메라** 를 **계층**으로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-149">Drag and drop the **Main Camera** into the **Hierarchy**.</span></span>
* <span data-ttu-id="8446e-150">**계층**에서 **만들기** 를 클릭 하 고 **빈 상태로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-150">In the **Hierarchy**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="8446e-151">새 **GameObject** 를 마우스 오른쪽 단추로 클릭 하 고 **이름 바꾸기**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-151">Right-click the new **GameObject** and select **Rename**.</span></span>
* <span data-ttu-id="8446e-152">GameObject의 이름을 **HologramCollection**로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-152">Rename the GameObject to **HologramCollection**.</span></span>
* <span data-ttu-id="8446e-153">**계층**에서 **HologramCollection** 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-153">Select the **HologramCollection** object in the **Hierarchy**.</span></span>
* <span data-ttu-id="8446e-154">**Inspector** 에서 **변환 위치** 를 **X: 0, Y:-0.25, Z: 2**로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-154">In the **Inspector** set the **transform position** to: **X: 0, Y: -0.25, Z: 2**.</span></span>
* <span data-ttu-id="8446e-155">**프로젝트 패널**의 **Holograms** 폴더에서 **EnergyHub** 자산을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-155">In the **Holograms** folder in the **Project panel**, find the **EnergyHub** asset.</span></span>
* <span data-ttu-id="8446e-156">**EnergyHub** 개체를 **프로젝트 패널** 에서 **계층** 으로 **HologramCollection의 자식**으로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-156">Drag and drop the **EnergyHub** object from the **Project panel** to the **Hierarchy** as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="8446e-157">**파일 > 다른 이름으로 장면 저장** ...을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-157">Select **File > Save Scene As...**</span></span>
* <span data-ttu-id="8446e-158">장면 이름을 **SharedHolograms** 로 하 고 **저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-158">Name the scene **SharedHolograms** and click **Save**.</span></span>
* <span data-ttu-id="8446e-159">Holograms를 미리 보려면 Unity의 **재생** 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-159">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="8446e-160">**재생** 을 두 번 눌러 미리 보기 모드를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-160">Press **Play** a second time to stop preview mode.</span></span>

<span data-ttu-id="8446e-161">**Unity에서 Visual Studio로 프로젝트 내보내기**</span><span class="sxs-lookup"><span data-stu-id="8446e-161">**Export the project from Unity to Visual Studio**</span></span>

* <span data-ttu-id="8446e-162">Unity에서 **파일 > 빌드 설정**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-162">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="8446e-163">열려 있는 장면 **추가** 를 클릭 하 여 장면을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-163">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="8446e-164">**플랫폼** 목록에서 **유니버설 Windows 플랫폼** 을 선택 하 고 **플랫폼 전환**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-164">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="8446e-165">**SDK** 를 **Universal 10**으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-165">Set **SDK** to **Universal 10**.</span></span>
* <span data-ttu-id="8446e-166">**대상 장치** 를 **HoloLens** 로 설정 하 고 **UWP 빌드 유형을** **D3D**로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-166">Set **Target device** to **HoloLens** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="8446e-167">**Unity C# 프로젝트**를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-167">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="8446e-168">**빌드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-168">Click **Build**.</span></span>
* <span data-ttu-id="8446e-169">표시 되는 파일 탐색기 창에서 "App" 이라는 **새 폴더** 를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-169">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="8446e-170">단일 **앱** 폴더를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-170">Single click the **App** folder.</span></span>
* <span data-ttu-id="8446e-171">**폴더 선택**을 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-171">Press **Select Folder**.</span></span>
* <span data-ttu-id="8446e-172">Unity가 완료 되 면 파일 탐색기 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-172">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="8446e-173">**앱** 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-173">Open the **App** folder.</span></span>
* <span data-ttu-id="8446e-174">**SharedHolograms** 를 열어 Visual Studio를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-174">Open **SharedHolograms.sln** to launch Visual Studio.</span></span>
* <span data-ttu-id="8446e-175">Visual Studio의 맨 위 도구 모음을 사용 하 여 대상을 디버그에서 **릴리스** 로, ARM에서 **x 86**으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-175">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="8446e-176">로컬 컴퓨터 옆의 드롭다운 화살표를 클릭 하 고 **원격 장치**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-176">Click on the drop-down arrow next to Local Machine, and select **Remote Device**.</span></span>
    * <span data-ttu-id="8446e-177">**주소** 를 HoloLens의 이름 또는 IP 주소로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-177">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="8446e-178">장치 IP 주소를 알 수 없는 경우 **설정 > 네트워크 & 인터넷 > 고급 옵션** 을 확인 하거나 Cortana **"안녕하세요. 내 IP 주소는 무엇입니까?"** 를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-178">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
    * <span data-ttu-id="8446e-179">**인증 모드** 를 **유니버설**으로 설정 된 상태로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-179">Leave the **Authentication Mode** set to **Universal**.</span></span>
    * <span data-ttu-id="8446e-180">**선택** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-180">Click **Select**</span></span>
* <span data-ttu-id="8446e-181">**디버그 > 디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-181">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="8446e-182">처음으로 장치에 배포 하는 경우에는 [Visual Studio와 쌍](using-visual-studio.md#pairing-your-device)으로 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-182">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device).</span></span>
* <span data-ttu-id="8446e-183">HoloLens에 배치 하 고 EnergyHub 홀로그램을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-183">Put on your HoloLens and find the EnergyHub hologram.</span></span>

## <a name="chapter-2---interaction"></a><span data-ttu-id="8446e-184">2 장-상호 작용</span><span class="sxs-lookup"><span data-stu-id="8446e-184">Chapter 2 - Interaction</span></span>

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

<span data-ttu-id="8446e-185">이 장에서는 holograms와 상호 작용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-185">In this chapter, we'll interact with our holograms.</span></span> <span data-ttu-id="8446e-186">먼저, [응시](gaze-and-commit.md)를 시각화 하는 커서를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-186">First, we'll add a cursor to visualize our [Gaze](gaze-and-commit.md).</span></span> <span data-ttu-id="8446e-187">그런 다음 [제스처](gaze-and-commit.md#composite-gestures) 를 추가 하 고 손을 사용 하 여 holograms을 공간에 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-187">Then, we'll add [Gestures](gaze-and-commit.md#composite-gestures) and use our hand to place our holograms in space.</span></span>

### <a name="objectives"></a><span data-ttu-id="8446e-188">목표</span><span class="sxs-lookup"><span data-stu-id="8446e-188">Objectives</span></span>

* <span data-ttu-id="8446e-189">응시 입력을 사용 하 여 커서를 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-189">Use gaze input to control a cursor.</span></span>
* <span data-ttu-id="8446e-190">제스처 입력을 사용 하 여 holograms와 상호 작용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-190">Use gesture input to interact with holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="8446e-191">지침</span><span class="sxs-lookup"><span data-stu-id="8446e-191">Instructions</span></span>

<span data-ttu-id="8446e-192">**응시**</span><span class="sxs-lookup"><span data-stu-id="8446e-192">**Gaze**</span></span>

* <span data-ttu-id="8446e-193">**계층 패널** 에서 **HologramCollection** 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-193">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="8446e-194">**검사기 패널** 에서 **구성 요소 추가** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-194">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="8446e-195">메뉴의 검색 상자에 **응시 관리자**를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-195">In the menu, type in the search box **Gaze Manager**.</span></span> <span data-ttu-id="8446e-196">검색 결과를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-196">Select the search result.</span></span>
* <span data-ttu-id="8446e-197">**HoloToolkit-Sharing-240\Prefabs\Input** 폴더에서 **커서** 자산을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-197">In the **HoloToolkit-Sharing-240\Prefabs\Input** folder, find the **Cursor** asset.</span></span>
* <span data-ttu-id="8446e-198">**커서** 자산을 **계층 구조**에 끌어다 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-198">Drag and drop the **Cursor** asset onto the **Hierarchy**.</span></span>

<span data-ttu-id="8446e-199">**지우는**</span><span class="sxs-lookup"><span data-stu-id="8446e-199">**Gesture**</span></span>

* <span data-ttu-id="8446e-200">**계층 패널** 에서 **HologramCollection** 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-200">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="8446e-201">**구성 요소 추가** 를 클릭 하 고 검색 필드에 **제스처 관리자** 를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-201">Click **Add Component** and type **Gesture Manager** in the search field.</span></span> <span data-ttu-id="8446e-202">검색 결과를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-202">Select the search result.</span></span>
* <span data-ttu-id="8446e-203">**계층 패널**에서 **HologramCollection**를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-203">In the **Hierarchy panel**, expand **HologramCollection**.</span></span>
* <span data-ttu-id="8446e-204">자식 **EnergyHub** 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-204">Select the child **EnergyHub** object.</span></span>
* <span data-ttu-id="8446e-205">**검사기 패널** 에서 **구성 요소 추가** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-205">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="8446e-206">메뉴에서 **홀로그램 배치**를 검색 상자에 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-206">In the menu, type in the search box **Hologram Placement**.</span></span> <span data-ttu-id="8446e-207">검색 결과를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-207">Select the search result.</span></span>
* <span data-ttu-id="8446e-208">**파일 > 장면 저장**을 선택 하 여 장면을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-208">Save the scene by selecting **File > Save Scene**.</span></span>

<span data-ttu-id="8446e-209">**배포 및 이용**</span><span class="sxs-lookup"><span data-stu-id="8446e-209">**Deploy and enjoy**</span></span>

* <span data-ttu-id="8446e-210">이전 장의 지침을 사용 하 여를 빌드하고 HoloLens에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-210">Build and deploy to your HoloLens, using the instructions from the previous chapter.</span></span>
* <span data-ttu-id="8446e-211">앱이 HoloLens에서 시작 되 면 헤드를 이동 하 고 EnergyHub이 응시를 따라가는 방법을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-211">Once the app launches on your HoloLens, move your head around and notice how the EnergyHub follows your gaze.</span></span>
* <span data-ttu-id="8446e-212">홀로그램을 응시 할 때 커서가 어떻게 표시 되는지, 그리고 홀로그램에서 gazing 않을 때 점 빛의 변화를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-212">Notice how the cursor appears when you gaze upon the hologram, and changes to a point light when not gazing at a hologram.</span></span>
* <span data-ttu-id="8446e-213">비행기를 탭 하 여 홀로그램을 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-213">Perform an air-tap to place the hologram.</span></span> <span data-ttu-id="8446e-214">지금은 프로젝트에서 홀로그램을 한 번만 추가할 수 있습니다 (다시 배포 다시 시도).</span><span class="sxs-lookup"><span data-stu-id="8446e-214">At this time in our project, you can only place the hologram once (redeploy to try again).</span></span>

## <a name="chapter-3---shared-coordinates"></a><span data-ttu-id="8446e-215">3 장-공유 좌표</span><span class="sxs-lookup"><span data-stu-id="8446e-215">Chapter 3 - Shared Coordinates</span></span>

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

<span data-ttu-id="8446e-216">Holograms를 확인 하 고 상호 작용 하는 데 재미 있지만 더 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-216">It's fun to see and interact with holograms, but let's go further.</span></span> <span data-ttu-id="8446e-217">첫 번째 공유 환경을 설정 합니다. 즉, 모든 사람이 함께 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-217">We'll set up our first shared experience - a hologram everyone can see together.</span></span>

### <a name="objectives"></a><span data-ttu-id="8446e-218">목표</span><span class="sxs-lookup"><span data-stu-id="8446e-218">Objectives</span></span>

* <span data-ttu-id="8446e-219">공유 환경의 네트워크를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-219">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="8446e-220">공통 참조 지점을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-220">Establish a common reference point.</span></span>
* <span data-ttu-id="8446e-221">장치 간에 좌표계를 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-221">Share coordinate systems across devices.</span></span>
* <span data-ttu-id="8446e-222">모든 사람이 동일한 홀로그램을 보게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-222">Everyone sees the same hologram!</span></span>

>[!NOTE]
><span data-ttu-id="8446e-223">공유 서버에 연결 하려면 앱에 대해 **Internetclientserver** 및 **PrivateNetworkClientServer** 기능을 선언 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-223">The **InternetClientServer** and **PrivateNetworkClientServer** capabilities must be declared for an app to connect to the sharing server.</span></span> <span data-ttu-id="8446e-224">이 작업은 이미 Holograms 240에 있지만 사용자 고유의 프로젝트에 대해서는이를 염두에 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-224">This is done for you already in Holograms 240, but keep this in mind for your own projects.</span></span>

>1. <span data-ttu-id="8446e-225">Unity 편집기에서 "편집 > 프로젝트 설정 > 플레이어"로 이동 하 여 플레이어 설정으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-225">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="8446e-226">"Windows 스토어" 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-226">Click on the "Windows Store" tab</span></span>
>3. <span data-ttu-id="8446e-227">"게시 설정 > 기능" 섹션에서 **Internetclientserver** 기능 및 **PrivateNetworkClientServer** 기능을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-227">In the "Publishing Settings > Capabilities" section, check the **InternetClientServer** capability and the **PrivateNetworkClientServer** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="8446e-228">지침</span><span class="sxs-lookup"><span data-stu-id="8446e-228">Instructions</span></span>

* <span data-ttu-id="8446e-229">**프로젝트 패널** 에서 **HoloToolkit-Sharing-240\Prefabs\Sharing** 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-229">In the **Project panel** navigate to the **HoloToolkit-Sharing-240\Prefabs\Sharing** folder.</span></span>
* <span data-ttu-id="8446e-230">**공유** Prefab을 **계층 패널로**끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-230">Drag and drop the **Sharing** prefab into the **Hierarchy panel**.</span></span>

<span data-ttu-id="8446e-231">다음으로 공유 서비스를 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-231">Next we need to launch the sharing service.</span></span> <span data-ttu-id="8446e-232">공유 환경에서 한 대의 **PC** 만이 단계를 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-232">Only **one PC** in the shared experience needs to do this step.</span></span>

* <span data-ttu-id="8446e-233">Unity-위쪽 메뉴에서 **HoloToolkit-240 메뉴**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-233">In Unity - in the top-hand menu - select the **HoloToolkit-Sharing-240 menu**.</span></span>
* <span data-ttu-id="8446e-234">드롭다운에서 **공유 서비스 시작** 항목을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-234">Select the **Launch Sharing Service** item in the drop-down.</span></span>
* <span data-ttu-id="8446e-235">**개인 네트워크** 옵션을 선택 하 고 방화벽 프롬프트가 표시 되 면 **액세스 허용** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-235">Check the **Private Network** option and click **Allow Access** when the firewall prompt appears.</span></span>
* <span data-ttu-id="8446e-236">공유 서비스 콘솔 창에 표시 된 IPv4 주소를 적어둡니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-236">Note down the IPv4 address displayed in the Sharing Service console window.</span></span> <span data-ttu-id="8446e-237">이는 서비스가 실행 되는 컴퓨터와 동일한 IP입니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-237">This is the same IP as the machine the service is being run on.</span></span>

<span data-ttu-id="8446e-238">공유 환경에 참여 하는 **모든 pc** 의 나머지 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-238">Follow the rest of the instructions on **all PCs** that will join the shared experience.</span></span>

* <span data-ttu-id="8446e-239">**계층**에서 **공유** 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-239">In the **Hierarchy**, select the **Sharing** object.</span></span>
* <span data-ttu-id="8446e-240">**검사자**의 **공유 단계** 구성 요소에서 **서버 주소** 를 ' localhost '에서 SharingService를 실행 하는 컴퓨터의 IPv4 주소로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-240">In the **Inspector**, on the **Sharing Stage** component, change the **Server Address** from 'localhost' to the IPv4 address of the machine running SharingService.exe.</span></span>
* <span data-ttu-id="8446e-241">**계층** 에서 **HologramCollection** 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-241">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="8446e-242">**검사기** 에서 **구성 요소 추가** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-242">In the **Inspector** click the **Add Component** button.</span></span>
* <span data-ttu-id="8446e-243">검색 상자에 **가져오기 내보내기 앵커 관리자**를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-243">In the search box, type **Import Export Anchor Manager**.</span></span> <span data-ttu-id="8446e-244">검색 결과를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-244">Select the search result.</span></span>
* <span data-ttu-id="8446e-245">**프로젝트 패널** 에서 **Scripts** 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-245">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="8446e-246">**HologramPlacement** 스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-246">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="8446e-247">내용을 아래 코드로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-247">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="8446e-248">Unity로 돌아가서 **계층 패널**에서 **HologramCollection** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-248">Back in Unity, select the **HologramCollection** in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="8446e-249">**검사기 패널** 에서 **구성 요소 추가** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-249">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="8446e-250">메뉴에서 **앱 상태 관리자**검색 상자에를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-250">In the menu, type in the search box **App State Manager**.</span></span> <span data-ttu-id="8446e-251">검색 결과를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-251">Select the search result.</span></span>

<span data-ttu-id="8446e-252">**배포 및 이용**</span><span class="sxs-lookup"><span data-stu-id="8446e-252">**Deploy and enjoy**</span></span>

* <span data-ttu-id="8446e-253">HoloLens 장치에 대 한 프로젝트를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-253">Build the project for your HoloLens devices.</span></span>
* <span data-ttu-id="8446e-254">첫 번째에 배포할 HoloLens를 하나 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-254">Designate one HoloLens to deploy to first.</span></span> <span data-ttu-id="8446e-255">EnergyHub을 시작 하기 전에 Anchor가 서비스에 업로드 될 때까지 기다려야 합니다 (30-60 초 정도 걸릴 수 있음).</span><span class="sxs-lookup"><span data-stu-id="8446e-255">You will need to wait for the Anchor to be uploaded to the service before you can place the EnergyHub (this can take ~30-60 seconds).</span></span> <span data-ttu-id="8446e-256">업로드가 완료 될 때까지 탭 제스처는 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-256">Until the upload is done, your tap gestures will be ignored.</span></span>
* <span data-ttu-id="8446e-257">EnergyHub가 배치 된 후에는 해당 위치가 서비스에 업로드 되 고 다른 모든 HoloLens 장치에 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-257">After the EnergyHub has been placed, its location will be uploaded to the service and you can then deploy to all other HoloLens devices.</span></span>
* <span data-ttu-id="8446e-258">새 HoloLens가 먼저 세션에 조인 하면 해당 장치에서 EnergyHub 위치가 올바르지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-258">When a new HoloLens first joins the session, the location of the EnergyHub may not be correct on that device.</span></span> <span data-ttu-id="8446e-259">그러나 anchor 및 EnergyHub 위치가 서비스에서 다운로드 되는 즉시 EnergyHub는 새 공유 위치로 이동 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-259">However, as soon as the anchor and EnergyHub locations have been downloaded from the service, the EnergyHub should jump to the new, shared location.</span></span> <span data-ttu-id="8446e-260">이 문제가 ~ 30-60 초 이내에 발생 하지 않는 경우 더 많은 환경 단서를 수집 하도록 앵커를 설정 하는 경우 원래 HoloLens가 있었던 위치를 살펴보세요.</span><span class="sxs-lookup"><span data-stu-id="8446e-260">If this does not happen within ~30-60 seconds, walk to where the original HoloLens was when setting the anchor to gather more environment clues.</span></span> <span data-ttu-id="8446e-261">위치가 여전히 잠겨 있지 않으면 장치에 다시 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-261">If the location still does not lock on, redeploy to the device.</span></span>
* <span data-ttu-id="8446e-262">장치를 모두 준비 하 고 앱을 실행 하는 경우 EnergyHub을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-262">When the devices are all ready and running the app, look for the EnergyHub.</span></span> <span data-ttu-id="8446e-263">홀로그램의 위치와 텍스트가 접하는 방향을 모두 동의할 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="8446e-263">Can you all agree on the hologram's location and which direction the text is facing?</span></span>

## <a name="chapter-4---discovery"></a><span data-ttu-id="8446e-264">4 장-검색</span><span class="sxs-lookup"><span data-stu-id="8446e-264">Chapter 4 - Discovery</span></span>

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

<span data-ttu-id="8446e-265">이제 모든 사용자가 동일한 홀로그램을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-265">Everyone can now see the same hologram!</span></span> <span data-ttu-id="8446e-266">이제 shared holographic 세계에 연결 된 다른 모든 사용자를 확인해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-266">Now let's see everyone else connected to our shared holographic world.</span></span> <span data-ttu-id="8446e-267">이 장에서는 동일한 공유 세션에서 다른 모든 HoloLens 장치의 헤드 위치와 회전을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-267">In this chapter, we'll grab the head location and rotation of all other HoloLens devices in the same sharing session.</span></span>

### <a name="objectives"></a><span data-ttu-id="8446e-268">목표</span><span class="sxs-lookup"><span data-stu-id="8446e-268">Objectives</span></span>

* <span data-ttu-id="8446e-269">공유 환경에서 서로를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-269">Discover each other in our shared experience.</span></span>
* <span data-ttu-id="8446e-270">플레이어 아바타를 선택 하 고 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-270">Choose and share a player avatar.</span></span>
* <span data-ttu-id="8446e-271">플레이어 아바타를 모든 사용자의 헤드 옆에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-271">Attach the player avatar next to everyone's heads.</span></span>

### <a name="instructions"></a><span data-ttu-id="8446e-272">지침</span><span class="sxs-lookup"><span data-stu-id="8446e-272">Instructions</span></span>

* <span data-ttu-id="8446e-273">**프로젝트 패널** 에서 **Holograms** 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-273">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="8446e-274">**PlayerAvatarStore** 를 **계층**으로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-274">Drag and drop the **PlayerAvatarStore** into the **Hierarchy**.</span></span>
* <span data-ttu-id="8446e-275">**프로젝트 패널** 에서 **Scripts** 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-275">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="8446e-276">**AvatarSelector** 스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-276">Double-click the **AvatarSelector** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="8446e-277">내용을 아래 코드로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-277">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="8446e-278">**계층** 에서 **HologramCollection** 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-278">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="8446e-279">**검사기** 에서 **구성 요소 추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-279">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="8446e-280">검색 상자에 **로컬 플레이어 관리자**를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-280">In the search box, type **Local Player Manager**.</span></span> <span data-ttu-id="8446e-281">검색 결과를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-281">Select the search result.</span></span>
* <span data-ttu-id="8446e-282">**계층** 에서 **HologramCollection** 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-282">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="8446e-283">**검사기** 에서 **구성 요소 추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-283">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="8446e-284">검색 상자에 **원격 플레이어 관리자**를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-284">In the search box, type **Remote Player Manager**.</span></span> <span data-ttu-id="8446e-285">검색 결과를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-285">Select the search result.</span></span>
* <span data-ttu-id="8446e-286">Visual Studio에서 **HologramPlacement** 스크립트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-286">Open the **HologramPlacement** script in Visual Studio.</span></span>
* <span data-ttu-id="8446e-287">내용을 아래 코드로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-287">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="8446e-288">Visual Studio에서 **AppStateManager** 스크립트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-288">Open the **AppStateManager** script in Visual Studio.</span></span>
* <span data-ttu-id="8446e-289">내용을 아래 코드로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-289">Replace the contents with the code below.</span></span>

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

<span data-ttu-id="8446e-290">**배포 및 이용**</span><span class="sxs-lookup"><span data-stu-id="8446e-290">**Deploy and Enjoy**</span></span>

* <span data-ttu-id="8446e-291">프로젝트를 빌드하고 HoloLens 장치에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-291">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="8446e-292">Ping 소리가 들리면 아바타 선택 메뉴를 찾고 공중 탭 제스처를 사용 하 여 아바타를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-292">When you hear a pinging sound, find the avatar selection menu and select an avatar with the air-tap gesture.</span></span>
* <span data-ttu-id="8446e-293">Holograms을 확인 하지 않는 경우 HoloLens가 서비스와 통신 하는 동안 커서 주위의 점 빛이 다른 색으로 전환 됩니다. 초기화 (진한 자주), 앵커 다운로드 (녹색), 위치 데이터 가져오기/내보내기 (노랑), 앵커 (파란색)를 업로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-293">If you're not looking at any holograms, the point light around your cursor will turn a different color when your HoloLens is communicating with the service: initializing (dark purple), downloading the anchor (green), importing/exporting location data (yellow), uploading the anchor (blue).</span></span> <span data-ttu-id="8446e-294">커서 주위의 점 조명이 기본 색 (연한 자주색) 이면 세션의 다른 플레이어와 상호 작용할 준비가 된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-294">If your point light around your cursor is the default color (light purple), then you are ready to interact with other players in your session!</span></span>
* <span data-ttu-id="8446e-295">공간에 연결 된 다른 사용자를 살펴보세요. 어깨 위에 holographic 로봇이 떠 모방 해당 헤드 동작을 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-295">Look at other people connected to your space - there will be a holographic robot floating above their shoulder and mimicking their head motions!</span></span>

## <a name="chapter-5---placement"></a><span data-ttu-id="8446e-296">5 장-배치</span><span class="sxs-lookup"><span data-stu-id="8446e-296">Chapter 5 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

<span data-ttu-id="8446e-297">이 장에서는 실제 세계 표면에 앵커를 배치할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-297">In this chapter, we'll make the anchor able to be placed on real-world surfaces.</span></span> <span data-ttu-id="8446e-298">공유 좌표를 사용 하 여 공유 환경에 연결 된 모든 사람 사이에서 중간 지점에 해당 앵커를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-298">We'll use shared coordinates to place that anchor in the middle point between everyone connected to the shared experience.</span></span>

### <a name="objectives"></a><span data-ttu-id="8446e-299">목표</span><span class="sxs-lookup"><span data-stu-id="8446e-299">Objectives</span></span>

* <span data-ttu-id="8446e-300">플레이어의 헤드 위치에 따라 공간 매핑 메시에 holograms을 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-300">Place holograms on the spatial mapping mesh based on players’ head position.</span></span>

### <a name="instructions"></a><span data-ttu-id="8446e-301">지침</span><span class="sxs-lookup"><span data-stu-id="8446e-301">Instructions</span></span>

* <span data-ttu-id="8446e-302">**프로젝트 패널** 에서 **Holograms** 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-302">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="8446e-303">**CustomSpatialMapping** Prefab를 **계층 구조**에 끌어다 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-303">Drag and drop the **CustomSpatialMapping** prefab onto the **Hierarchy**.</span></span>
* <span data-ttu-id="8446e-304">**프로젝트 패널** 에서 **Scripts** 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-304">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="8446e-305">**AppStateManager** 스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-305">Double-click the **AppStateManager** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="8446e-306">내용을 아래 코드로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-306">Replace the contents with the code below.</span></span>

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

* <span data-ttu-id="8446e-307">**프로젝트 패널** 에서 **Scripts** 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-307">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="8446e-308">**HologramPlacement** 스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-308">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="8446e-309">내용을 아래 코드로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-309">Replace the contents with the code below.</span></span>

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

<span data-ttu-id="8446e-310">**배포 및 이용**</span><span class="sxs-lookup"><span data-stu-id="8446e-310">**Deploy and enjoy**</span></span>

* <span data-ttu-id="8446e-311">프로젝트를 빌드하고 HoloLens 장치에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-311">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="8446e-312">앱이 준비 되 면 원 안에 표시 되 고 EnergyHub이 모든 사람의 중앙에 표시 되는 방식을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-312">When the app is ready, stand in a circle and notice how the EnergyHub appears in the center of everyone.</span></span>
* <span data-ttu-id="8446e-313">을 탭 하 여 EnergyHub을 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-313">Tap to place the EnergyHub.</span></span>
* <span data-ttu-id="8446e-314">음성 명령 ' 다시 설정 대상 '을 사용 하 여 EnergyHub 백업을 선택 하 고 그룹으로 함께 작업 하 여 홀로그램을 새 위치로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-314">Try the voice command 'Reset Target' to pick the EnergyHub back up and work together as a group to move the hologram to a new location.</span></span>

## <a name="chapter-6---real-world-physics"></a><span data-ttu-id="8446e-315">6 장-실제 세계 물리학</span><span class="sxs-lookup"><span data-stu-id="8446e-315">Chapter 6 - Real-World Physics</span></span>

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

<span data-ttu-id="8446e-316">이 장에서는 실제 화면을 바운스 하는 holograms을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-316">In this chapter we'll add holograms that bounce off real-world surfaces.</span></span> <span data-ttu-id="8446e-317">사용자와 친구 모두에 의해 시작 되는 프로젝트를 사용 하 여 공간을 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-317">Watch your space fill up with projects launched by both you and your friends!</span></span>

### <a name="objectives"></a><span data-ttu-id="8446e-318">목표</span><span class="sxs-lookup"><span data-stu-id="8446e-318">Objectives</span></span>

* <span data-ttu-id="8446e-319">실제 표면에서 바운스 된 projectiles를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-319">Launch projectiles that bounce off real-world surfaces.</span></span>
* <span data-ttu-id="8446e-320">다른 플레이어가 볼 수 있도록 projectiles을 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-320">Share the projectiles so other players can see them.</span></span>

### <a name="instructions"></a><span data-ttu-id="8446e-321">지침</span><span class="sxs-lookup"><span data-stu-id="8446e-321">Instructions</span></span>

* <span data-ttu-id="8446e-322">**계층** 에서 **HologramCollection** 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-322">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="8446e-323">**검사기** 에서 **구성 요소 추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-323">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="8446e-324">검색 상자에 나이 **시작 관리자**를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-324">In the search box, type **Projectile Launcher**.</span></span> <span data-ttu-id="8446e-325">검색 결과를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-325">Select the search result.</span></span>

<span data-ttu-id="8446e-326">**배포 및 이용**</span><span class="sxs-lookup"><span data-stu-id="8446e-326">**Deploy and enjoy**</span></span>

* <span data-ttu-id="8446e-327">HoloLens 장치를 빌드하고 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-327">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="8446e-328">앱이 모든 장치에서 실행 되는 경우에는 공기 탭을 수행 하 여 실제 화면에서 멀리 있는 게임을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-328">When the app is running on all devices, perform an air-tap to launch projectile at real world surfaces.</span></span>
* <span data-ttu-id="8446e-329">멀리가 다른 플레이어의 아바타와 충돌 하는 경우 어떻게 되나요?를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8446e-329">See what happens when your projectile collides with another player's avatar!</span></span>

## <a name="chapter-7---grand-finale"></a><span data-ttu-id="8446e-330">7 장-그랜드 Finale</span><span class="sxs-lookup"><span data-stu-id="8446e-330">Chapter 7 - Grand Finale</span></span>

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

<span data-ttu-id="8446e-331">이 장에서는 공동 작업 에서만 검색할 수 있는 포털을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-331">In this chapter, we'll uncover a portal that can only be discovered with collaboration.</span></span>

### <a name="objectives"></a><span data-ttu-id="8446e-332">목표</span><span class="sxs-lookup"><span data-stu-id="8446e-332">Objectives</span></span>

* <span data-ttu-id="8446e-333">함께 작동 하 여 비밀 포털을 projectiles 앵커에서 충분 한를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-333">Work together to launch enough projectiles at the anchor to uncover a secret portal!</span></span>

### <a name="instructions"></a><span data-ttu-id="8446e-334">지침</span><span class="sxs-lookup"><span data-stu-id="8446e-334">Instructions</span></span>

* <span data-ttu-id="8446e-335">**프로젝트 패널** 에서 **Holograms** 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-335">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="8446e-336">지 **각 자산을** **HologramCollection의 자식**으로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-336">Drag and drop the **Underworld** asset as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="8446e-337">**HologramCollection** 가 선택 된 상태에서 **검사기**의 **구성 요소 추가** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-337">With **HologramCollection** selected, click the **Add Component** button in the **Inspector**.</span></span>
* <span data-ttu-id="8446e-338">메뉴의 검색 상자에 **ExplodeTarget**을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-338">In the menu, type in the search box **ExplodeTarget**.</span></span> <span data-ttu-id="8446e-339">검색 결과를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-339">Select the search result.</span></span>
* <span data-ttu-id="8446e-340">**HologramCollection** 를 선택 하면 **계층 구조** 에서 **EnergyHub** 개체를 **검사기**의 **대상** 필드로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-340">With **HologramCollection** selected, from the **Hierarchy** drag the **EnergyHub** object to the **Target** field in the **Inspector**.</span></span>
* <span data-ttu-id="8446e-341">**HologramCollection** 를 선택 하면 **계층 구조** 에서 지 수 **개체를** **검사기**의 **지 수 필드로** 끕니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-341">With **HologramCollection** selected, from the **Hierarchy** drag the **Underworld** object to the **Underworld** field in the **Inspector**.</span></span>

<span data-ttu-id="8446e-342">**배포 및 이용**</span><span class="sxs-lookup"><span data-stu-id="8446e-342">**Deploy and enjoy**</span></span>

* <span data-ttu-id="8446e-343">HoloLens 장치를 빌드하고 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-343">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="8446e-344">앱이 시작 되 면 함께 공동 작업 하 여 EnergyHub에서 projectiles를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="8446e-344">When the app has launched, collaborate together to launch projectiles at the EnergyHub.</span></span>
* <span data-ttu-id="8446e-345">지가 표시 되 면 projectiles를 실행 합니다 (추가 재미를 위해 로봇이 세 번 적중).</span><span class="sxs-lookup"><span data-stu-id="8446e-345">When the underworld appears, launch projectiles at underworld robots (hit a robot three times for extra fun).</span></span>
