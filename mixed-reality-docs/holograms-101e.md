---
title: MR 기본 사항 101E-에뮬레이터를 사용 하 여 프로젝트 완료
description: Unity, Visual Studio 및 HoloLens 에뮬레이터를 사용 하 여이 코딩 연습을 수행 하 여 holographic 응용 프로그램의 기본 사항을 알아보세요.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: 혼합 현실, Windows Mixed Reality, HoloLens, 홀로그램, 아카데미, 자습서, 에뮬레이터
ms.openlocfilehash: 77f7d497396937bf471a69fa514cef84ab0b699d
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522325"
---
>[!NOTE]
><span data-ttu-id="ed907-104">혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="ed907-105">따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="ed907-106">이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="ed907-107">지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="ed907-108">향후에는 HoloLens 2를 개발 하는 방법을 보여 주는 새 자습서 시리즈를 게시할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="ed907-109">이 알림은 게시 될 때 해당 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-basics-101e-complete-project-with-emulator"></a><span data-ttu-id="ed907-110">MR 기본 사항 101E: 에뮬레이터를 사용 하 여 프로젝트 완료</span><span class="sxs-lookup"><span data-stu-id="ed907-110">MR Basics 101E: Complete project with emulator</span></span>

 >[!VIDEO https://www.youtube.com/embed/Xzm8_s05mm8]

<span data-ttu-id="ed907-111">이 자습서에서는 [응시](gaze.md), [제스처](gestures.md), [음성 입력](voice-input.md), [공간 음향](spatial-sound.md) 및 [공간 매핑을](spatial-mapping.md) 비롯 한 HoloLens의 핵심 Windows Mixed Reality 기능을 보여 주는 Unity에서 빌드된 전체 프로젝트를 안내 합니다. .</span><span class="sxs-lookup"><span data-stu-id="ed907-111">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](gaze.md), [gestures](gestures.md), [voice input](voice-input.md), [spatial sound](spatial-sound.md) and [spatial mapping](spatial-mapping.md).</span></span> <span data-ttu-id="ed907-112">자습서를 완료 하는 데 약 1 시간이 소요 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-112">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="ed907-113">장치 지원</span><span class="sxs-lookup"><span data-stu-id="ed907-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="ed907-114">과정</span><span class="sxs-lookup"><span data-stu-id="ed907-114">Course</span></span></th><th style="width:150px"> <span data-ttu-id="ed907-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="ed907-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="ed907-116"><a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="ed907-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="ed907-117">MR 기본 사항 101E: 에뮬레이터를 사용 하 여 프로젝트 완료</span><span class="sxs-lookup"><span data-stu-id="ed907-117">MR Basics 101E: Complete project with emulator</span></span></td><td style="text-align: center;"> <span data-ttu-id="ed907-118">✔️</span><span class="sxs-lookup"><span data-stu-id="ed907-118">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="ed907-119">시작하기 전 주의 사항</span><span class="sxs-lookup"><span data-stu-id="ed907-119">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="ed907-120">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="ed907-120">Prerequisites</span></span>

* <span data-ttu-id="ed907-121">올바른 [도구로](install-the-tools.md)구성 된 WINDOWS 10 PC입니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-121">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>

### <a name="project-files"></a><span data-ttu-id="ed907-122">프로젝트 파일</span><span class="sxs-lookup"><span data-stu-id="ed907-122">Project files</span></span>

* <span data-ttu-id="ed907-123">프로젝트에 필요한 [파일](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) 을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-123">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="ed907-124"> Unity 2017.2 이상이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-124"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="ed907-125">Unity 5.6 지원이 계속 필요한 경우 [이 릴리스](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip)를 사용 하세요.</span><span class="sxs-lookup"><span data-stu-id="ed907-125">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="ed907-126">Unity 5.5 지원이 계속 필요한 경우 [이 릴리스](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip)를 사용 하세요.</span><span class="sxs-lookup"><span data-stu-id="ed907-126">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="ed907-127">Unity 5.4 지원이 계속 필요한 경우 [이 릴리스](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip)를 사용 하세요.</span><span class="sxs-lookup"><span data-stu-id="ed907-127">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="ed907-128">바탕 화면 또는 기타 쉬운 위치에 파일을 보관 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-128">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="ed907-129">폴더 이름을 **종이 접기**로 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-129">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="ed907-130">다운로드 하기 전에 소스 코드를 확인 하려는 경우 [GitHub에서 사용할 수](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101)있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-130">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="ed907-131">1 장-"Holo" 세계</span><span class="sxs-lookup"><span data-stu-id="ed907-131">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/qotpUpIQxVU]

<span data-ttu-id="ed907-132">이 장에서는 첫 번째 Unity 프로젝트를 설정 하 고 빌드 및 배포 프로세스를 단계별로 진행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-132">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="ed907-133">목표</span><span class="sxs-lookup"><span data-stu-id="ed907-133">Objectives</span></span>

* <span data-ttu-id="ed907-134">Holographic 개발용 Unity를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-134">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="ed907-135">홀로그램을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-135">Make a hologram.</span></span>
* <span data-ttu-id="ed907-136">만든 홀로그램을 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="ed907-136">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="ed907-137">지침</span><span class="sxs-lookup"><span data-stu-id="ed907-137">Instructions</span></span>

* <span data-ttu-id="ed907-138">Unity를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-138">Start Unity.</span></span>
* <span data-ttu-id="ed907-139">**열기**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-139">Select **Open**.</span></span>
* <span data-ttu-id="ed907-140">이전에 보관 하지 않은 **종이 접기** 폴더로 위치를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-140">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="ed907-141">**종이** 를 선택 하 고 **폴더 선택**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-141">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="ed907-142">새 장면 저장:파일 / **을 다른 이름으로 저장**합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-142">Save the new scene: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="ed907-143">장면 **종이** 의 이름을로 하 고 **저장** 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-143">Name the scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-camera"></a><span data-ttu-id="ed907-144">기본 카메라 설정</span><span class="sxs-lookup"><span data-stu-id="ed907-144">Setup the main camera</span></span>

* <span data-ttu-id="ed907-145">**계층 패널**에서 **주 카메라**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-145">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="ed907-146">**Inspector** 의 변환 위치를 **0, 0, 0**으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-146">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="ed907-147">**Clear Flags** 속성을 찾고 Dropdown을 **Skybox** 에서 **Solid color**로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-147">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="ed907-148">배경색 선택을 열려면 **배경** 필드를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-148">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="ed907-149">**R, G, B 및 A** 를 **0**으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-149">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="ed907-150">장면 설정</span><span class="sxs-lookup"><span data-stu-id="ed907-150">Setup the scene</span></span>

* <span data-ttu-id="ed907-151">**계층 패널**에서 **만들기** 를 클릭 하 고 **빈 상태로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-151">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="ed907-152">새 **GameObject** 를 마우스 오른쪽 단추로 클릭 하 고 이름 바꾸기를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-152">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="ed907-153">GameObject의 이름을 **OrigamiCollection**로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-153">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="ed907-154">**프로젝트 패널**의 **Holograms** 폴더에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-154">From the **Holograms** folder in the **Project Panel**:</span></span>
  * <span data-ttu-id="ed907-155">**스테이지** 를 계층 구조로 끌어 **OrigamiCollection**의 자식으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-155">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="ed907-156">**Sphere1** 를 계층 구조로 끌어 **OrigamiCollection**의 자식으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-156">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="ed907-157">**Sphere2** 를 계층 구조로 끌어 **OrigamiCollection**의 자식으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-157">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="ed907-158">**계층 패널** 에서 **방향 광원** 개체를 마우스 오른쪽 단추로 클릭 하 고 **삭제**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-158">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="ed907-159">**Holograms** 폴더에서 **조명을** **계층 패널**의 루트로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-159">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="ed907-160">**계층**에서 **OrigamiCollection**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-160">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="ed907-161">**검사기**에서 변환 위치를 **0,-0.5, 2.0**로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-161">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="ed907-162">Holograms를 미리 보려면 Unity의 **재생** 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-162">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="ed907-163">미리 보기 창에 종이 개체를 표시 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-163">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="ed907-164">**재생** 을 두 번 눌러 미리 보기 모드를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-164">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="ed907-165">Unity에서 Visual Studio로 프로젝트 내보내기</span><span class="sxs-lookup"><span data-stu-id="ed907-165">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="ed907-166">Unity에서 **파일 > 빌드 설정**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-166">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="ed907-167">**플랫폼** 목록에서 **Windows 스토어** 를 선택 하 고 **플랫폼 전환**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-167">Select **Windows Store** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="ed907-168">**SDK** 를 **Universal 10** 으로 설정 하 고 **빌드 형식을** **D3D**로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-168">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="ed907-169">**Unity C# 프로젝트**를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-169">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="ed907-170">열려 있는 장면 **추가** 를 클릭 하 여 장면을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-170">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="ed907-171">**플레이어 설정**...을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-171">Click **Player Settings...**.</span></span>
* <span data-ttu-id="ed907-172">검사기 패널에서 **Windows 스토어 로고**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-172">In the Inspector Panel select the **Windows Store logo**.</span></span> <span data-ttu-id="ed907-173">그런 다음 **게시 설정**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-173">Then select **Publishing Settings**.</span></span>
* <span data-ttu-id="ed907-174">**기능** 섹션에서 **마이크** 및 **SpatialPerception** 기능을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-174">In the **Capabilities** section, select the **Microphone** and **SpatialPerception** capabilities.</span></span>
* <span data-ttu-id="ed907-175">빌드 설정 창으로 돌아가서 **빌드**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-175">Back in the Build Settings window, click **Build**.</span></span>
* <span data-ttu-id="ed907-176">"App" 이라는 **새 폴더** 를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-176">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="ed907-177">단일 **앱 폴더**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-177">Single click the **App Folder**.</span></span>
* <span data-ttu-id="ed907-178">**폴더 선택**을 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-178">Press **Select Folder**.</span></span>
* <span data-ttu-id="ed907-179">Unity가 완료 되 면 파일 탐색기 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-179">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="ed907-180">**앱** 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-180">Open the **App** folder.</span></span>
* <span data-ttu-id="ed907-181">종이에 **표시 되는 Visual Studio 솔루션**을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-181">Open the **Origami Visual Studio Solution**.</span></span>
* <span data-ttu-id="ed907-182">Visual Studio의 맨 위 도구 모음을 사용 하 여 대상을 디버그에서 **릴리스** 로, ARM에서 **x 86**으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-182">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
  * <span data-ttu-id="ed907-183">장치 단추 옆의 화살표를 클릭 하 고 **HoloLens 에뮬레이터**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-183">Click on the arrow next to the Device button, and select **HoloLens Emulator**.</span></span>
  * <span data-ttu-id="ed907-184">**디버그를 클릭 하 > 디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-184">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
  * <span data-ttu-id="ed907-185">잠시 후에 에뮬레이터가 종이 접기 프로젝트로 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-185">After some time the emulator will start with the Origami project.</span></span> <span data-ttu-id="ed907-186">[에뮬레이터](using-the-hololens-emulator.md)를 처음 시작할 때 에뮬레이터가 시작 될 때까지 15 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-186">When first launching the [emulator](using-the-hololens-emulator.md), it can take as long as 15 minutes for the emulator to start up.</span></span> <span data-ttu-id="ed907-187">시작 되 면 닫지 마세요.</span><span class="sxs-lookup"><span data-stu-id="ed907-187">Once it starts, do not close it.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="ed907-188">2 장-응시</span><span class="sxs-lookup"><span data-stu-id="ed907-188">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/BPWTbAC210k]

<span data-ttu-id="ed907-189">이 장에서는 holograms와 상호 작용 하는 세 가지 방법, 즉 [응시](gaze.md)를 소개 하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-189">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](gaze.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="ed907-190">목표</span><span class="sxs-lookup"><span data-stu-id="ed907-190">Objectives</span></span>

* <span data-ttu-id="ed907-191">전 세계 잠긴 커서를 사용 하 여 응시를 시각화 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-191">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="ed907-192">지침</span><span class="sxs-lookup"><span data-stu-id="ed907-192">Instructions</span></span>

* <span data-ttu-id="ed907-193">Unity 프로젝트로 돌아가서 빌드 설정 창이 열려 있으면 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-193">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="ed907-194">**프로젝트 패널**에서 **Holograms** 폴더를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-194">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="ed907-195">**커서** 개체를 루트 수준에서 **계층 패널로** 끕니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-195">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="ed907-196">**커서** 개체를 두 번 클릭 하면 자세히 살펴볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-196">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="ed907-197">프로젝트 패널에서 **Scripts** 폴더를 마우스 오른쪽 단추로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-197">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="ed907-198">**만들기** 하위 메뉴를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-198">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="ed907-199">**C# 스크립트**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-199">Select **C# Script**.</span></span>
* <span data-ttu-id="ed907-200">스크립트 이름을 **WorldCursor**로 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-200">Name the script **WorldCursor**.</span></span> <span data-ttu-id="ed907-201">참고: 이름은 대/소문자 구분입니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-201">Note: The name is case-sensitive.</span></span> <span data-ttu-id="ed907-202">.Cs 확장명을 추가할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-202">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="ed907-203">**계층 패널**에서 **Cursor** 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-203">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="ed907-204">**WorldCursor** 스크립트를 **검사기 패널로**끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-204">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="ed907-205">**WorldCursor** 스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-205">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="ed907-206">이 코드를 복사 하 여 **WorldCursor.cs** 에 붙여넣고 **모두 저장**합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-206">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

```cs
using UnityEngine;

public class WorldCursor : MonoBehaviour
{
    private MeshRenderer meshRenderer;

    // Use this for initialization
    void Start()
    {
        // Grab the mesh renderer that's on the same object as this script.
        meshRenderer = this.gameObject.GetComponentInChildren<MeshRenderer>();
    }

    // Update is called once per frame
    void Update()
    {
        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;

        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram...
            // Display the cursor mesh.
            meshRenderer.enabled = true;

            // Move thecursor to the point where the raycast hit.
            this.transform.position = hitInfo.point;

            // Rotate the cursor to hug the surface of the hologram.
            this.transform.rotation = Quaternion.FromToRotation(Vector3.up, hitInfo.normal);
        }
        else
        {
            // If the raycast did not hit a hologram, hide the cursor mesh.
            meshRenderer.enabled = false;
        }
    }
}
```

* <span data-ttu-id="ed907-207">**빌드 설정 > 파일**에서 응용 프로그램을 다시 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-207">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="ed907-208">이전에 에뮬레이터에 배포 하는 데 사용한 Visual Studio 솔루션으로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-208">Return to the Visual Studio solution previously used to deploy to the emulator.</span></span>
* <span data-ttu-id="ed907-209">메시지가 표시 되 면 ' 모두 다시 로드 '를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-209">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="ed907-210">**디버그를 클릭 하 > 디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-210">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="ed907-211">Xbox 컨트롤러를 사용 하 여 장면을 살펴볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-211">Use the Xbox controller to look around the scene.</span></span> <span data-ttu-id="ed907-212">커서가 개체 모양과 상호 작용 하는 방식을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-212">Notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="ed907-213">3 장-제스처</span><span class="sxs-lookup"><span data-stu-id="ed907-213">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/6d-0RHeKHq4]

<span data-ttu-id="ed907-214">이 장에서는 [제스처](gestures.md)에 대 한 지원을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-214">In this chapter, we'll add support for [gestures](gestures.md).</span></span> <span data-ttu-id="ed907-215">사용자가 용지 구를 선택 하면 Unity의 물리학 엔진을 사용 하 여 무게를 설정 하 여 구를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-215">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="ed907-216">목표</span><span class="sxs-lookup"><span data-stu-id="ed907-216">Objectives</span></span>

* <span data-ttu-id="ed907-217">선택 제스처를 사용 하 여 holograms를 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-217">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="ed907-218">지침</span><span class="sxs-lookup"><span data-stu-id="ed907-218">Instructions</span></span>

<span data-ttu-id="ed907-219">먼저 선택 제스처를 검색할 수 있는 것 보다 스크립트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-219">We'll start by creating a script than can detect the Select gesture.</span></span>

* <span data-ttu-id="ed907-220">**Scripts** 폴더에서 **GazeGestureManager**라는 스크립트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-220">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="ed907-221">**GazeGestureManager** 스크립트를 계층의 **OrigamiCollection** 개체로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-221">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="ed907-222">Visual Studio에서 **GazeGestureManager** 스크립트를 열고 다음 코드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-222">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

```cs
using UnityEngine;
using UnityEngine.XR.WSA.Input;

public class GazeGestureManager : MonoBehaviour
{
    public static GazeGestureManager Instance { get; private set; }

    // Represents the hologram that is currently being gazed at.
    public GameObject FocusedObject { get; private set; }

    GestureRecognizer recognizer;

    // Use this for initialization
    void Start()
    {
        Instance = this;

        // Set up a GestureRecognizer to detect Select gestures.
        recognizer = new GestureRecognizer();
        recognizer.Tapped += (args) =>
        {
            // Send an OnSelect message to the focused object and its ancestors.
            if (FocusedObject != null)
            {
                FocusedObject.SendMessageUpwards("OnSelect", SendMessageOptions.DontRequireReceiver);
            }
        };
        recognizer.StartCapturingGestures();
    }

    // Update is called once per frame
    void Update()
    {
        // Figure out which hologram is focused this frame.
        GameObject oldFocusObject = FocusedObject;

        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;
        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram, use that as the focused object.
            FocusedObject = hitInfo.collider.gameObject;
        }
        else
        {
            // If the raycast did not hit a hologram, clear the focused object.
            FocusedObject = null;
        }

        // If the focused object changed this frame,
        // start detecting fresh gestures again.
        if (FocusedObject != oldFocusObject)
        {
            recognizer.CancelGestures();
            recognizer.StartCapturingGestures();
        }
    }
}
```

* <span data-ttu-id="ed907-223">Scripts 폴더에 **SphereCommands**이라는 다른 스크립트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-223">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="ed907-224">계층 구조 뷰에서 **OrigamiCollection** 개체를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-224">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="ed907-225">**SphereCommands** 스크립트를 계층 패널의 **Sphere1** 개체로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-225">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="ed907-226">**SphereCommands** 스크립트를 계층 패널의 **Sphere2** 개체로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-226">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="ed907-227">편집을 위해 Visual Studio에서 스크립트를 열고 기본 코드를 다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-227">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }
}
```

* <span data-ttu-id="ed907-228">앱을 내보내고, 빌드하고, 배포 하 여 HoloLens 에뮬레이터에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-228">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="ed907-229">장면을 중심으로 살펴보고 구 중 하나를 중심으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-229">Look around the scene, and center on one of the spheres.</span></span>
* <span data-ttu-id="ed907-230">Xbox 컨트롤러에서 **A** 단추를 누르거나 스페이스바를 눌러 선택 제스처를 시뮬레이션 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-230">Press the **A** button on the Xbox controller or press the Spacebar to simulate the Select gesture.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="ed907-231">4 장-음성</span><span class="sxs-lookup"><span data-stu-id="ed907-231">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/LxbOhnd2_GM]

<span data-ttu-id="ed907-232">이 장에서는 다음과 같은 두 가지 [음성 명령](voice-input.md)에 대 한 지원을 추가 합니다. "다시 설정"을 사용 하 여 삭제 된 구를 원래 위치로 반환 하 고 "놓기"를 사용 하 여 구를 나눌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-232">In this chapter, we'll add support for two [voice commands](voice-input.md): "Reset world" to returns the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="ed907-233">목표</span><span class="sxs-lookup"><span data-stu-id="ed907-233">Objectives</span></span>

* <span data-ttu-id="ed907-234">백그라운드에서 항상 수신 대기 하는 음성 명령을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-234">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="ed907-235">음성 명령에 반응 하는 홀로그램을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-235">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="ed907-236">지침</span><span class="sxs-lookup"><span data-stu-id="ed907-236">Instructions</span></span>

* <span data-ttu-id="ed907-237">**Scripts** 폴더에서 **SpeechManager**라는 스크립트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-237">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="ed907-238">**SpeechManager** 스크립트를 계층의 **OrigamiCollection** 개체로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-238">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="ed907-239">Visual Studio에서 **SpeechManager** 스크립트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-239">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="ed907-240">이 코드를 복사 하 여 **SpeechManager.cs** 에 붙여넣고 **모두 저장**합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-240">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

```cs
using System.Collections.Generic;
using System.Linq;
using UnityEngine;
using UnityEngine.Windows.Speech;

public class SpeechManager : MonoBehaviour
{
    KeywordRecognizer keywordRecognizer = null;
    Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();

    // Use this for initialization
    void Start()
    {
        keywords.Add("Reset world", () =>
        {
            // Call the OnReset method on every descendant object.
            this.BroadcastMessage("OnReset");
        });

        keywords.Add("Drop Sphere", () =>
        {
            var focusObject = GazeGestureManager.Instance.FocusedObject;
            if (focusObject != null)
            {
                // Call the OnDrop method on just the focused object.
                focusObject.SendMessage("OnDrop", SendMessageOptions.DontRequireReceiver);
            }
        });

        // Tell the KeywordRecognizer about our keywords.
        keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());

        // Register a callback for the KeywordRecognizer and start recognizing!
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        System.Action keywordAction;
        if (keywords.TryGetValue(args.text, out keywordAction))
        {
            keywordAction.Invoke();
        }
    }
}
```

* <span data-ttu-id="ed907-241">Visual Studio에서 **SphereCommands** 스크립트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-241">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="ed907-242">다음과 같이 스크립트를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-242">Update the script to read as follows:</span></span>

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    Vector3 originalPosition;

    // Use this for initialization
    void Start()
    {
        // Grab the original local position of the sphere when the app starts.
        originalPosition = this.transform.localPosition;
    }

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }

    // Called by SpeechManager when the user says the "Reset world" command
    void OnReset()
    {
        // If the sphere has a Rigidbody component, remove it to disable physics.
        var rigidbody = this.GetComponent<Rigidbody>();
        if (rigidbody != null)
        {
            rigidbody.isKinematic = true;
            Destroy(rigidbody);
        }

        // Put the sphere back into its original local position.
        this.transform.localPosition = originalPosition;
    }

    // Called by SpeechManager when the user says the "Drop sphere" command
    void OnDrop()
    {
        // Just do the same logic as a Select gesture.
        OnSelect();
    }
}
```

* <span data-ttu-id="ed907-243">앱을 내보내고, 빌드하고, 배포 하 여 HoloLens 에뮬레이터에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-243">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="ed907-244">에뮬레이터가 PC의 마이크를 지원 하 고 음성에 응답 합니다. 커서가 구 중 하나에 있도록 보기를 조정 하 고 "삭제 구" 라고 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-244">The emulator will support your PC's microphone and respond to your voice: adjust the view so the cursor is on one of the spheres, and say "Drop Sphere".</span></span>
* <span data-ttu-id="ed907-245">초기 위치로 다시 전환 하기 위해 "**세계 재설정**" 이라고 말할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-245">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="ed907-246">5 장-공간 소리</span><span class="sxs-lookup"><span data-stu-id="ed907-246">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Xc3C4VA10w4]

<span data-ttu-id="ed907-247">이 장에서는 앱에 음악을 추가한 다음 특정 작업에 대 한 음향 효과를 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-247">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="ed907-248">3D 공간에서 소리를 특정 위치에 제공 하기 위해 [공간 소리](spatial-sound.md) 를 사용할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-248">We'll be using [spatial sound](spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="ed907-249">목표</span><span class="sxs-lookup"><span data-stu-id="ed907-249">Objectives</span></span>

* <span data-ttu-id="ed907-250">전 세계에서 holograms를 들어봅니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-250">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="ed907-251">지침</span><span class="sxs-lookup"><span data-stu-id="ed907-251">Instructions</span></span>

* <span data-ttu-id="ed907-252">Unity의 상단 메뉴에서 select **> 프로젝트 설정 > 오디오를 편집** 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-252">In the Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="ed907-253">**Spatializer 플러그 인** 설정을 찾아 **MS hrtf Spatializer**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-253">Find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="ed907-254">**Holograms** 폴더에서 **외계** 개체를 계층 패널의 **OrigamiCollection** 개체로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-254">From the **Holograms** folder, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="ed907-255">**OrigamiCollection** 를 선택 하 고 **오디오 원본** 구성 요소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-255">Select **OrigamiCollection** and find the **Audio Source** component.</span></span> <span data-ttu-id="ed907-256">다음 속성을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-256">Change these properties:</span></span>
  * <span data-ttu-id="ed907-257">**Spatialize** 속성을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-257">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="ed907-258">절전 모드 해제를 확인 **합니다.**</span><span class="sxs-lookup"><span data-stu-id="ed907-258">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="ed907-259">슬라이더를 오른쪽으로 끌어 **공간 Blend** 를 **3d** 로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-259">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span>
  * <span data-ttu-id="ed907-260">**Loop** 속성을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-260">Check the **Loop** property.</span></span>
  * <span data-ttu-id="ed907-261">**3D 소리 설정**을 확장 하 고 **Doppler 수준**에 대해 **0.1** 을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-261">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="ed907-262">**볼륨 Rolloff** 를 **로그 Rolloff**로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-262">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="ed907-263">**최대 거리** 를 **20**으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-263">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="ed907-264">**Scripts** 폴더에서 **SphereSounds**라는 스크립트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-264">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="ed907-265">**SphereSounds** 를 계층의 **Sphere1** 및 **Sphere2** 개체로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-265">Drag **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="ed907-266">Visual Studio에서 **SphereSounds** 를 열고 다음 코드를 업데이트 하 고 **모두 저장**합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-266">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

```cs
using UnityEngine;

public class SphereSounds : MonoBehaviour
{
    AudioSource impactAudioSource = null;
    AudioSource rollingAudioSource = null;

    bool rolling = false;

    void Start()
    {
        // Add an AudioSource component and set up some defaults
        impactAudioSource = gameObject.AddComponent<AudioSource>();
        impactAudioSource.playOnAwake = false;
        impactAudioSource.spatialize = true;
        impactAudioSource.spatialBlend = 1.0f;
        impactAudioSource.dopplerLevel = 0.0f;
        impactAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        impactAudioSource.maxDistance = 20f;

        rollingAudioSource = gameObject.AddComponent<AudioSource>();
        rollingAudioSource.playOnAwake = false;
        rollingAudioSource.spatialize = true;
        rollingAudioSource.spatialBlend = 1.0f;
        rollingAudioSource.dopplerLevel = 0.0f;
        rollingAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        rollingAudioSource.maxDistance = 20f;
        rollingAudioSource.loop = true;

        // Load the Sphere sounds from the Resources folder
        impactAudioSource.clip = Resources.Load<AudioClip>("Impact");
        rollingAudioSource.clip = Resources.Load<AudioClip>("Rolling");
    }

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Play an impact sound if the sphere impacts strongly enough.
        if (collision.relativeVelocity.magnitude >= 0.1f)
        {
            impactAudioSource.Play();
        }
    }

    // Occurs each frame that this object continues to collide with another object
    void OnCollisionStay(Collision collision)
    {
        Rigidbody rigid = gameObject.GetComponent<Rigidbody>();

        // Play a rolling sound if the sphere is rolling fast enough.
        if (!rolling && rigid.velocity.magnitude >= 0.01f)
        {
            rolling = true;
            rollingAudioSource.Play();
        }
        // Stop the rolling sound if rolling slows down.
        else if (rolling && rigid.velocity.magnitude < 0.01f)
        {
            rolling = false;
            rollingAudioSource.Stop();
        }
    }

    // Occurs when this object stops colliding with another object
    void OnCollisionExit(Collision collision)
    {
        // Stop the rolling sound if the object falls off and stops colliding.
        if (rolling)
        {
            rolling = false;
            impactAudioSource.Stop();
            rollingAudioSource.Stop();
        }
    }
}
```

* <span data-ttu-id="ed907-267">스크립트를 저장 하 고 Unity로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-267">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="ed907-268">앱을 내보내고, 빌드하고, 배포 하 여 HoloLens 에뮬레이터에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-268">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="ed907-269">전체 효과를 얻으려면 헤드폰을 착용 하 고, 소리 변화를 들으려면 스테이지에서 더 가깝게 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-269">Wear headphones to get the full effect, and move closer and further from the Stage to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="ed907-270">6 장-공간 매핑</span><span class="sxs-lookup"><span data-stu-id="ed907-270">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/S-517Y63Cnk]

<span data-ttu-id="ed907-271">이제 [공간 매핑을](spatial-mapping.md) 사용 하 여 실제 개체에 게임 보드를 추가 하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-271">Now we are going to use [spatial mapping](spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="ed907-272">목표</span><span class="sxs-lookup"><span data-stu-id="ed907-272">Objectives</span></span>

* <span data-ttu-id="ed907-273">실제 세계를 가상 세계에 가져오세요.</span><span class="sxs-lookup"><span data-stu-id="ed907-273">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="ed907-274">가장 중요 한 위치에 holograms을 두십시오.</span><span class="sxs-lookup"><span data-stu-id="ed907-274">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="ed907-275">지침</span><span class="sxs-lookup"><span data-stu-id="ed907-275">Instructions</span></span>

* <span data-ttu-id="ed907-276">프로젝트 패널에서 **Holograms** 폴더를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-276">Click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="ed907-277">**공간 매핑** 자산을 **계층**의 루트로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-277">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="ed907-278">계층에서 **공간 매핑** 개체를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-278">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="ed907-279">**검사기 패널**에서 다음 속성을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-279">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="ed907-280">**시각적 개체 메시 그리기** 상자를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-280">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="ed907-281">**그리기 자료** 를 찾고 오른쪽에 있는 원을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-281">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="ed907-282">위쪽의 검색 필드에 "**골격형**"을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-282">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="ed907-283">결과를 클릭 한 다음 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-283">Click on the result and then close the window.</span></span>
* <span data-ttu-id="ed907-284">앱을 내보내고, 빌드하고, 배포 하 여 HoloLens 에뮬레이터에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-284">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="ed907-285">앱이 실행 되 면 이전에 스캔 한 실제 실내의 메쉬가 와이어 프레임으로 렌더링 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-285">When the app runs, a mesh of a previously scanned real-world living room will be rendered in wireframe.</span></span>
* <span data-ttu-id="ed907-286">롤링 구가 단계를 어떻게 진행 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-286">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="ed907-287">이제 OrigamiCollection를 새 위치로 이동 하는 방법을 보여 드리겠습니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-287">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="ed907-288">**Scripts** 폴더에서 **TapToPlaceParent**라는 스크립트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-288">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="ed907-289">**계층**에서 **OrigamiCollection** 를 확장 하 고 **단계** 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-289">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="ed907-290">**TapToPlaceParent** 스크립트를 Stage 개체로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-290">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="ed907-291">Visual Studio에서 **TapToPlaceParent** 스크립트를 열고 다음으로 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-291">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

```cs
using UnityEngine;

public class TapToPlaceParent : MonoBehaviour
{
    bool placing = false;

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // On each Select gesture, toggle whether the user is in placing mode.
        placing = !placing;

        // If the user is in placing mode, display the spatial mapping mesh.
        if (placing)
        {
            SpatialMapping.Instance.DrawVisualMeshes = true;
        }
        // If the user is not in placing mode, hide the spatial mapping mesh.
        else
        {
            SpatialMapping.Instance.DrawVisualMeshes = false;
        }
    }

    // Update is called once per frame
    void Update()
    {
        // If the user is in placing mode,
        // update the placement to match the user's gaze.

        if (placing)
        {
            // Do a raycast into the world that will only hit the Spatial Mapping mesh.
            var headPosition = Camera.main.transform.position;
            var gazeDirection = Camera.main.transform.forward;

            RaycastHit hitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out hitInfo,
                30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // Move this object's parent object to
                // where the raycast hit the Spatial Mapping mesh.
                this.transform.parent.position = hitInfo.point;

                // Rotate this object's parent object to face the user.
                Quaternion toQuat = Camera.main.transform.localRotation;
                toQuat.x = 0;
                toQuat.z = 0;
                this.transform.parent.rotation = toQuat;
            }
        }
    }
}
```

* <span data-ttu-id="ed907-292">앱을 내보내고 빌드하고 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-292">Export, build and deploy the app.</span></span>
* <span data-ttu-id="ed907-293">이제 선택 제스처 (**a** 또는 스페이스바)를 사용 하 고, 새 위치로 이동 하 고, 선택 제스처를 다시 사용 하 여 특정 위치에 게임을 gazing 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-293">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture (**A** or Spacebar) and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="the-end"></a><span data-ttu-id="ed907-294">끝</span><span class="sxs-lookup"><span data-stu-id="ed907-294">The end</span></span>

<span data-ttu-id="ed907-295">이 자습서의 끝입니다!</span><span class="sxs-lookup"><span data-stu-id="ed907-295">And that's the end of this tutorial!</span></span>

<span data-ttu-id="ed907-296">배운 내용:</span><span class="sxs-lookup"><span data-stu-id="ed907-296">You learned:</span></span>

* <span data-ttu-id="ed907-297">Unity에서 holographic 앱을 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="ed907-297">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="ed907-298">응시, 제스처, 음성, 소리 및 공간 매핑을 활용 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-298">How to make use of gaze, gesture, voice, sounds, and spatial mapping.</span></span>
* <span data-ttu-id="ed907-299">Visual Studio를 사용 하 여 앱을 빌드하고 배포 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-299">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="ed907-300">이제 사용자 고유의 holographic apps를 만들 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ed907-300">You are now ready to start creating your own holographic apps!</span></span>

## <a name="see-also"></a><span data-ttu-id="ed907-301">참조</span><span class="sxs-lookup"><span data-stu-id="ed907-301">See also</span></span>

* [<span data-ttu-id="ed907-302">MR 기본 101: 디바이스를 사용하는 완전한 프로젝트</span><span class="sxs-lookup"><span data-stu-id="ed907-302">MR Basics 101: Complete project with device</span></span>](holograms-101.md)
* [<span data-ttu-id="ed907-303">응시</span><span class="sxs-lookup"><span data-stu-id="ed907-303">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="ed907-304">제스처</span><span class="sxs-lookup"><span data-stu-id="ed907-304">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="ed907-305">음성 입력 </span><span class="sxs-lookup"><span data-stu-id="ed907-305">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="ed907-306">공간 음향</span><span class="sxs-lookup"><span data-stu-id="ed907-306">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="ed907-307">공간 매핑</span><span class="sxs-lookup"><span data-stu-id="ed907-307">Spatial mapping</span></span>](spatial-mapping.md)
