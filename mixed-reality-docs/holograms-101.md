---
title: MR 기본 사항 101-장치를 사용 하 여 프로젝트 완료
description: Unity, Visual Studio 및 HoloLens를 사용 하 여이 코딩 연습을 수행 하 여 Windows Mixed Reality의 기본 사항을 알아보세요.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: 혼합 현실, Windows Mixed Reality, HoloLens, 홀로그램, 아카데미, 자습서
ms.openlocfilehash: 456aeea88b0d7f51acb52156d8139ec2df06883a
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434712"
---
>[!NOTE]
><span data-ttu-id="97a9f-104">혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="97a9f-105">따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="97a9f-106">이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="97a9f-107">지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="97a9f-108">HoloLens 2에 대 한 [새로운 일련의 자습서](mrlearning-base.md) 가 게시 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-basics-101-complete-project-with-device"></a><span data-ttu-id="97a9f-109">MR 기본 사항 101: 장치를 사용 하 여 프로젝트 완료</span><span class="sxs-lookup"><span data-stu-id="97a9f-109">MR Basics 101: Complete project with device</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

<span data-ttu-id="97a9f-110">이 자습서에서는 [응시](gaze-and-commit.md), [제스처](gaze-and-commit.md#composite-gestures), [음성 입력](voice-input.md), [공간 음향](spatial-sound.md) 및 [공간 매핑을](spatial-mapping.md) 비롯 한 HoloLens의 핵심 Windows Mixed Reality 기능을 보여 주는 Unity에서 빌드된 전체 프로젝트를 안내 합니다. .</span><span class="sxs-lookup"><span data-stu-id="97a9f-110">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](gaze-and-commit.md), [gestures](gaze-and-commit.md#composite-gestures), [voice input](voice-input.md), [spatial sound](spatial-sound.md) and [spatial mapping](spatial-mapping.md).</span></span>

<span data-ttu-id="97a9f-111">자습서를 완료 하는 데 약 1 시간이 소요 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-111">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="97a9f-112">장치 지원</span><span class="sxs-lookup"><span data-stu-id="97a9f-112">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="97a9f-113">과정</span><span class="sxs-lookup"><span data-stu-id="97a9f-113">Course</span></span></th><th style="width:150px"> <span data-ttu-id="97a9f-114"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="97a9f-114"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="97a9f-115"><a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="97a9f-115"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="97a9f-116">MR 기본 사항 101: 장치를 사용 하 여 프로젝트 완료</span><span class="sxs-lookup"><span data-stu-id="97a9f-116">MR Basics 101: Complete project with device</span></span></td><td style="text-align: center;"> <span data-ttu-id="97a9f-117">✔️</span><span class="sxs-lookup"><span data-stu-id="97a9f-117">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="97a9f-118">시작하기 전 확인 사항</span><span class="sxs-lookup"><span data-stu-id="97a9f-118">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="97a9f-119">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="97a9f-119">Prerequisites</span></span>

* <span data-ttu-id="97a9f-120">올바른 [도구로](install-the-tools.md)구성 된 WINDOWS 10 PC입니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-120">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="97a9f-121">[개발용으로 구성 된](using-visual-studio.md#enabling-developer-mode)HoloLens 장치입니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-121">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="97a9f-122">프로젝트 파일</span><span class="sxs-lookup"><span data-stu-id="97a9f-122">Project files</span></span>

* <span data-ttu-id="97a9f-123">프로젝트에 필요한 [파일](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) 을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-123">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="97a9f-124"> Unity 2017.2 이상이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-124"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="97a9f-125">Unity 5.6 지원이 계속 필요한 경우 [이 릴리스](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip)를 사용 하세요.</span><span class="sxs-lookup"><span data-stu-id="97a9f-125">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="97a9f-126">Unity 5.5 지원이 계속 필요한 경우 [이 릴리스](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip)를 사용 하세요.</span><span class="sxs-lookup"><span data-stu-id="97a9f-126">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="97a9f-127">Unity 5.4 지원이 계속 필요한 경우 [이 릴리스](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip)를 사용 하세요.</span><span class="sxs-lookup"><span data-stu-id="97a9f-127">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="97a9f-128">바탕 화면 또는 기타 쉬운 위치에 파일을 보관 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-128">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="97a9f-129">폴더 이름을 **종이 접기**로 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-129">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="97a9f-130">다운로드 하기 전에 소스 코드를 확인 하려는 경우 [GitHub에서 사용할 수](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101)있습니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-130">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="97a9f-131">1 장-"Holo" 세계</span><span class="sxs-lookup"><span data-stu-id="97a9f-131">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

<span data-ttu-id="97a9f-132">이 장에서는 첫 번째 Unity 프로젝트를 설정 하 고 빌드 및 배포 프로세스를 단계별로 진행 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-132">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="97a9f-133">목표</span><span class="sxs-lookup"><span data-stu-id="97a9f-133">Objectives</span></span>

* <span data-ttu-id="97a9f-134">Holographic 개발용 Unity를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-134">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="97a9f-135">홀로그램을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-135">Make a hologram.</span></span>
* <span data-ttu-id="97a9f-136">만든 홀로그램을 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="97a9f-136">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="97a9f-137">지침</span><span class="sxs-lookup"><span data-stu-id="97a9f-137">Instructions</span></span>

* <span data-ttu-id="97a9f-138">Unity를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-138">Start Unity.</span></span>
* <span data-ttu-id="97a9f-139">**열기**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-139">Select **Open**.</span></span>
* <span data-ttu-id="97a9f-140">이전에 보관 하지 않은 **종이 접기** 폴더로 위치를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-140">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="97a9f-141">**종이** 를 선택 하 고 **폴더 선택**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-141">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="97a9f-142">**종이** 에는 장면이 포함 되지 않으므로 빈 기본 장면을 새 파일에 저장 / **파일** 을 사용 하 여 새 파일을 **저장 합니다**.</span><span class="sxs-lookup"><span data-stu-id="97a9f-142">Since the **Origami** project does not contain a scene, save the empty default scene to a new file using: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="97a9f-143">새 장면 **종이** 의 이름을로 하 고 **저장** 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-143">Name the new scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-virtual-camera"></a><span data-ttu-id="97a9f-144">기본 가상 카메라 설정</span><span class="sxs-lookup"><span data-stu-id="97a9f-144">Setup the main virtual camera</span></span>

* <span data-ttu-id="97a9f-145">**계층 패널**에서 **주 카메라**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-145">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="97a9f-146">**Inspector** 의 변환 위치를 **0, 0, 0**으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-146">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="97a9f-147">**Clear Flags** 속성을 찾고 Dropdown을 **Skybox** 에서 **Solid color**로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-147">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="97a9f-148">배경색 선택을 열려면 **배경** 필드를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-148">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="97a9f-149">**R, G, B 및 A** 를 **0**으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-149">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="97a9f-150">장면 설정</span><span class="sxs-lookup"><span data-stu-id="97a9f-150">Setup the scene</span></span>

* <span data-ttu-id="97a9f-151">**계층 패널**에서 **만들기** 를 클릭 하 고 **빈 상태로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-151">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="97a9f-152">새 **GameObject** 를 마우스 오른쪽 단추로 클릭 하 고 이름 바꾸기를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-152">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="97a9f-153">GameObject의 이름을 **OrigamiCollection**로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-153">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="97a9f-154">프로젝트 패널의 **Holograms** 폴더에서 자산을 확장 하 고 Holograms를 선택 하거나 프로젝트 패널에서 Holograms 폴더를 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-154">From the **Holograms** folder in the Project Panel (expand Assets and select Holograms or double click the Holograms folder in the Project Panel):</span></span>
  * <span data-ttu-id="97a9f-155">**스테이지** 를 계층 구조로 끌어 **OrigamiCollection**의 자식으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-155">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="97a9f-156">**Sphere1** 를 계층 구조로 끌어 **OrigamiCollection**의 자식으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-156">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="97a9f-157">**Sphere2** 를 계층 구조로 끌어 **OrigamiCollection**의 자식으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-157">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="97a9f-158">**계층 패널** 에서 **방향 광원** 개체를 마우스 오른쪽 단추로 클릭 하 고 **삭제**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-158">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="97a9f-159">**Holograms** 폴더에서 **조명을** **계층 패널**의 루트로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-159">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="97a9f-160">**계층**에서 **OrigamiCollection**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-160">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="97a9f-161">**검사기**에서 변환 위치를 **0,-0.5, 2.0**로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-161">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="97a9f-162">Holograms를 미리 보려면 Unity의 **재생** 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-162">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="97a9f-163">미리 보기 창에 종이 개체를 표시 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-163">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="97a9f-164">**재생** 을 두 번 눌러 미리 보기 모드를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-164">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="97a9f-165">Unity에서 Visual Studio로 프로젝트 내보내기</span><span class="sxs-lookup"><span data-stu-id="97a9f-165">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="97a9f-166">Unity에서 **파일 > 빌드 설정**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-166">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="97a9f-167">**플랫폼** 목록에서 **유니버설 Windows 플랫폼** 을 선택 하 고 **플랫폼 전환**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-167">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="97a9f-168">**SDK** 를 **Universal 10** 으로 설정 하 고 **빌드 형식을** **D3D**로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-168">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="97a9f-169">**Unity C# 프로젝트**를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-169">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="97a9f-170">열려 있는 장면 **추가** 를 클릭 하 여 장면을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-170">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="97a9f-171">**빌드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-171">Click **Build**.</span></span>
* <span data-ttu-id="97a9f-172">표시 되는 파일 탐색기 창에서 "App" 이라는 **새 폴더** 를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-172">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="97a9f-173">단일 **앱 폴더**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-173">Single click the **App Folder**.</span></span>
* <span data-ttu-id="97a9f-174">**폴더 선택**을 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-174">Press **Select Folder**.</span></span>
* <span data-ttu-id="97a9f-175">Unity가 완료 되 면 파일 탐색기 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-175">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="97a9f-176">**앱** 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-176">Open the **App** folder.</span></span>
* <span data-ttu-id="97a9f-177">(두 번 클릭) **종이**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-177">Open (double click) **Origami.sln**.</span></span>
* <span data-ttu-id="97a9f-178">Visual Studio의 맨 위 도구 모음을 사용 하 여 대상을 디버그에서 **릴리스** 로, ARM에서 **x 86**으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-178">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="97a9f-179">장치 단추 옆의 화살표를 클릭 하 고 **원격 컴퓨터** 를 선택 하 여 wi-fi를 통해 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-179">Click on the arrow next to the Device button, and select **Remote Machine** to deploy over Wi-Fi.</span></span>
  * <span data-ttu-id="97a9f-180">**주소** 를 HoloLens의 이름 또는 IP 주소로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-180">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="97a9f-181">장치 IP 주소를 알 수 없는 경우 **설정 > 네트워크 & 인터넷 > 고급 옵션** 을 확인 하거나 Cortana **"안녕하세요. 내 IP 주소는 무엇입니까?"** 를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-181">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
  * <span data-ttu-id="97a9f-182">HoloLens가 USB를 통해 연결 된 경우 **장치** 를 선택 하 여 usb를 통해 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-182">If the HoloLens is attached over USB, you may instead select **Device** to deploy over USB.</span></span>
  * <span data-ttu-id="97a9f-183">**인증 모드** 를 **유니버설**으로 설정 된 상태로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-183">Leave the **Authentication Mode** set to **Universal**.</span></span>
  * <span data-ttu-id="97a9f-184">**선택** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-184">Click **Select**</span></span>

* <span data-ttu-id="97a9f-185">**디버그 > 디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-185">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="97a9f-186">처음으로 장치에 배포 하는 경우에는 [Visual Studio와 쌍](using-visual-studio.md#pairing-your-device)으로 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-186">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device).</span></span>

* <span data-ttu-id="97a9f-187">이제 종이 접기 프로젝트가 빌드하여 HoloLens에 배포 되 고 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-187">The Origami project will now build, deploy to your HoloLens, and then run.</span></span>
* <span data-ttu-id="97a9f-188">HoloLens에 배치 하 고 새 holograms를 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="97a9f-188">Put on your HoloLens and look around to see your new holograms.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="97a9f-189">2 장-응시</span><span class="sxs-lookup"><span data-stu-id="97a9f-189">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

<span data-ttu-id="97a9f-190">이 장에서는 holograms와 상호 작용 하는 세 가지 방법, 즉 [응시](gaze-and-commit.md)를 소개 하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-190">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](gaze-and-commit.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="97a9f-191">목표</span><span class="sxs-lookup"><span data-stu-id="97a9f-191">Objectives</span></span>

* <span data-ttu-id="97a9f-192">전 세계 잠긴 커서를 사용 하 여 응시를 시각화 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-192">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="97a9f-193">지침</span><span class="sxs-lookup"><span data-stu-id="97a9f-193">Instructions</span></span>

* <span data-ttu-id="97a9f-194">Unity 프로젝트로 돌아가서 빌드 설정 창이 열려 있으면 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-194">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="97a9f-195">**프로젝트 패널**에서 **Holograms** 폴더를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-195">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="97a9f-196">**커서** 개체를 루트 수준에서 **계층 패널로** 끕니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-196">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="97a9f-197">**커서** 개체를 두 번 클릭 하면 자세히 살펴볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-197">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="97a9f-198">프로젝트 패널에서 **Scripts** 폴더를 마우스 오른쪽 단추로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-198">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="97a9f-199">**만들기** 하위 메뉴를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-199">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="97a9f-200">**C# 스크립트**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-200">Select **C# Script**.</span></span>
* <span data-ttu-id="97a9f-201">스크립트 이름을 **WorldCursor**로 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-201">Name the script **WorldCursor**.</span></span> <span data-ttu-id="97a9f-202">참고: 이름은 대/소문자를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-202">Note: The name is case-sensitive.</span></span> <span data-ttu-id="97a9f-203">.Cs 확장명을 추가할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-203">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="97a9f-204">**계층 패널**에서 **Cursor** 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-204">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="97a9f-205">**WorldCursor** 스크립트를 **검사기 패널로**끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-205">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="97a9f-206">**WorldCursor** 스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-206">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="97a9f-207">이 코드를 복사 하 여 **WorldCursor.cs** 에 붙여넣고 **모두 저장**합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-207">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

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

            // Move the cursor to the point where the raycast hit.
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

* <span data-ttu-id="97a9f-208">**빌드 설정 > 파일**에서 응용 프로그램을 다시 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-208">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="97a9f-209">이전에 HoloLens에 배포 하는 데 사용한 Visual Studio 솔루션으로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-209">Return to the Visual Studio solution previously used to deploy to your HoloLens.</span></span>
* <span data-ttu-id="97a9f-210">메시지가 표시 되 면 ' 모두 다시 로드 '를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-210">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="97a9f-211">**디버그를 클릭 하 > 디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-211">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="97a9f-212">이제 장면을 살펴보고 커서가 개체 모양과 상호 작용 하는 방식을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-212">Now look around the scene and notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="97a9f-213">3 장-제스처</span><span class="sxs-lookup"><span data-stu-id="97a9f-213">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

<span data-ttu-id="97a9f-214">이 장에서는 [제스처](gaze-and-commit.md#composite-gestures)에 대 한 지원을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-214">In this chapter, we'll add support for [gestures](gaze-and-commit.md#composite-gestures).</span></span> <span data-ttu-id="97a9f-215">사용자가 용지 구를 선택 하면 Unity의 물리학 엔진을 사용 하 여 무게를 설정 하 여 구를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-215">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="97a9f-216">목표</span><span class="sxs-lookup"><span data-stu-id="97a9f-216">Objectives</span></span>

* <span data-ttu-id="97a9f-217">선택 제스처를 사용 하 여 holograms를 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-217">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="97a9f-218">지침</span><span class="sxs-lookup"><span data-stu-id="97a9f-218">Instructions</span></span>

<span data-ttu-id="97a9f-219">먼저 스크립트를 만든 다음 선택 제스처를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-219">We'll start by creating a script then can detect the Select gesture.</span></span>

* <span data-ttu-id="97a9f-220">**Scripts** 폴더에서 **GazeGestureManager**라는 스크립트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-220">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="97a9f-221">**GazeGestureManager** 스크립트를 계층의 **OrigamiCollection** 개체로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-221">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="97a9f-222">Visual Studio에서 **GazeGestureManager** 스크립트를 열고 다음 코드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-222">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

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
    void Awake()
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

* <span data-ttu-id="97a9f-223">Scripts 폴더에 **SphereCommands**이라는 다른 스크립트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-223">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="97a9f-224">계층 구조 뷰에서 **OrigamiCollection** 개체를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-224">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="97a9f-225">**SphereCommands** 스크립트를 계층 패널의 **Sphere1** 개체로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-225">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="97a9f-226">**SphereCommands** 스크립트를 계층 패널의 **Sphere2** 개체로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-226">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="97a9f-227">편집을 위해 Visual Studio에서 스크립트를 열고 기본 코드를 다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-227">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

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

* <span data-ttu-id="97a9f-228">앱을 내보내고, 빌드하여 HoloLens에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-228">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="97a9f-229">구 중 하나를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-229">Look at one of the spheres.</span></span>
* <span data-ttu-id="97a9f-230">선택 제스처를 수행 하 고 아래 화면에 대 한 구 드롭다운을 시청 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-230">Perform the select gesture and watch the sphere drop onto the surface below.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="97a9f-231">4 장-음성</span><span class="sxs-lookup"><span data-stu-id="97a9f-231">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

<span data-ttu-id="97a9f-232">이 장에서는 두 개의 [음성 명령](voice-input.md)에 대 한 지원을 추가 합니다. "다시 설정"은 삭제 된 구를 원래 위치로 반환 하 고, "삭제 구"는 구가 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-232">In this chapter, we'll add support for two [voice commands](voice-input.md): "Reset world" to return the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="97a9f-233">목표</span><span class="sxs-lookup"><span data-stu-id="97a9f-233">Objectives</span></span>

* <span data-ttu-id="97a9f-234">백그라운드에서 항상 수신 대기 하는 음성 명령을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-234">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="97a9f-235">음성 명령에 반응 하는 홀로그램을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-235">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="97a9f-236">지침</span><span class="sxs-lookup"><span data-stu-id="97a9f-236">Instructions</span></span>

* <span data-ttu-id="97a9f-237">**Scripts** 폴더에서 **SpeechManager**라는 스크립트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-237">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="97a9f-238">**SpeechManager** 스크립트를 계층의 **OrigamiCollection** 개체로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-238">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="97a9f-239">Visual Studio에서 **SpeechManager** 스크립트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-239">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="97a9f-240">이 코드를 복사 하 여 **SpeechManager.cs** 에 붙여넣고 **모두 저장**합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-240">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

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

* <span data-ttu-id="97a9f-241">Visual Studio에서 **SphereCommands** 스크립트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-241">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="97a9f-242">다음과 같이 스크립트를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-242">Update the script to read as follows:</span></span>

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

* <span data-ttu-id="97a9f-243">앱을 내보내고, 빌드하여 HoloLens에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-243">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="97a9f-244">구 중 하나를 확인 하 고 "**삭제 구**" 라고 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-244">Look at one of the spheres, and say "**Drop Sphere**".</span></span>
* <span data-ttu-id="97a9f-245">초기 위치로 다시 전환 하기 위해 "**세계 재설정**" 이라고 말할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-245">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="97a9f-246">5 장-공간 소리</span><span class="sxs-lookup"><span data-stu-id="97a9f-246">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

<span data-ttu-id="97a9f-247">이 장에서는 앱에 음악을 추가한 다음 특정 작업에 대 한 음향 효과를 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-247">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="97a9f-248">3D 공간에서 소리를 특정 위치에 제공 하기 위해 [공간 소리](spatial-sound.md) 를 사용할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-248">We'll be using [spatial sound](spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="97a9f-249">목표</span><span class="sxs-lookup"><span data-stu-id="97a9f-249">Objectives</span></span>

* <span data-ttu-id="97a9f-250">전 세계에서 holograms를 들어봅니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-250">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="97a9f-251">지침</span><span class="sxs-lookup"><span data-stu-id="97a9f-251">Instructions</span></span>

* <span data-ttu-id="97a9f-252">Unity의 상단 메뉴에서 선택 **> 프로젝트 설정 > 오디오를 편집** 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-252">In Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="97a9f-253">오른쪽의 검사기 패널에서 **Spatializer 플러그 인** 설정을 찾아 **MS hrtf Spatializer**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-253">In the Inspector Panel on the right side, find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="97a9f-254">프로젝트 패널의 **Holograms** 폴더에서 **외계** 개체를 계층 패널의 **OrigamiCollection** 개체로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-254">From the **Holograms** folder in the Project panel, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="97a9f-255">**OrigamiCollection** 를 선택 하 고 검사기 패널에서 **오디오 원본** 구성 요소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-255">Select **OrigamiCollection** and find the **Audio Source** component in the Inspector panel.</span></span> <span data-ttu-id="97a9f-256">다음 속성을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-256">Change these properties:</span></span>
  * <span data-ttu-id="97a9f-257">**Spatialize** 속성을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-257">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="97a9f-258">절전 모드 **해제를 확인 합니다.**</span><span class="sxs-lookup"><span data-stu-id="97a9f-258">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="97a9f-259">슬라이더를 오른쪽으로 끌어 **공간 Blend** 를 **3d** 로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-259">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span> <span data-ttu-id="97a9f-260">슬라이더를 이동 하는 경우 값은 0에서 1로 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-260">The value should change from 0 to 1 when you move the slider.</span></span>
  * <span data-ttu-id="97a9f-261">**Loop** 속성을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-261">Check the **Loop** property.</span></span>
  * <span data-ttu-id="97a9f-262">**3D 소리 설정**을 확장 하 고 **Doppler 수준**에 대해 **0.1** 을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-262">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="97a9f-263">**볼륨 Rolloff** 를 **로그 Rolloff**로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-263">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="97a9f-264">**최대 거리** 를 **20**으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-264">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="97a9f-265">**Scripts** 폴더에서 **SphereSounds**라는 스크립트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-265">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="97a9f-266">**SphereSounds** 를 계층의 **Sphere1** 및 **Sphere2** 개체로 끌어서 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-266">Drag and drop **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="97a9f-267">Visual Studio에서 **SphereSounds** 를 열고 다음 코드를 업데이트 하 고 **모두 저장**합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-267">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

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

* <span data-ttu-id="97a9f-268">스크립트를 저장 하 고 Unity로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-268">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="97a9f-269">앱을 내보내고, 빌드하여 HoloLens에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-269">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="97a9f-270">스테이지에서 가깝게 이동 하 여 다른 쪽으로 이동 하 여 소리 변경을 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-270">Move closer and further from the Stage and turn side-to-side to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="97a9f-271">6 장-공간 매핑</span><span class="sxs-lookup"><span data-stu-id="97a9f-271">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

<span data-ttu-id="97a9f-272">이제 [공간 매핑을](spatial-mapping.md) 사용 하 여 실제 개체에 게임 보드를 추가 하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-272">Now we are going to use [spatial mapping](spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="97a9f-273">목표</span><span class="sxs-lookup"><span data-stu-id="97a9f-273">Objectives</span></span>

* <span data-ttu-id="97a9f-274">실제 세계를 가상 세계에 가져오세요.</span><span class="sxs-lookup"><span data-stu-id="97a9f-274">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="97a9f-275">가장 중요 한 위치에 holograms을 두십시오.</span><span class="sxs-lookup"><span data-stu-id="97a9f-275">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="97a9f-276">지침</span><span class="sxs-lookup"><span data-stu-id="97a9f-276">Instructions</span></span>

* <span data-ttu-id="97a9f-277">Unity의 프로젝트 패널에서 **Holograms** 폴더를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-277">In Unity, click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="97a9f-278">**공간 매핑** 자산을 **계층**의 루트로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-278">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="97a9f-279">계층에서 **공간 매핑** 개체를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-279">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="97a9f-280">**검사기 패널**에서 다음 속성을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-280">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="97a9f-281">**시각적 개체 메시 그리기** 상자를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-281">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="97a9f-282">**그리기 자료** 를 찾고 오른쪽에 있는 원을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-282">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="97a9f-283">위쪽의 검색 필드에 "**골격형**"을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-283">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="97a9f-284">결과를 클릭 한 다음 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-284">Click on the result and then close the window.</span></span> <span data-ttu-id="97a9f-285">이렇게 하면 재질 그리기 값이 와이어 프레임으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-285">When you do this, the value for Draw Material should get set to Wireframe.</span></span>
* <span data-ttu-id="97a9f-286">앱을 내보내고, 빌드하여 HoloLens에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-286">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="97a9f-287">앱이 실행 되 면 와이어 프레임 메쉬가 실제 세계를 오버레이 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-287">When the app runs, a wireframe mesh will overlay your real world.</span></span>
* <span data-ttu-id="97a9f-288">롤링 구가 단계를 어떻게 진행 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-288">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="97a9f-289">이제 OrigamiCollection를 새 위치로 이동 하는 방법을 보여 드리겠습니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-289">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="97a9f-290">**Scripts** 폴더에서 **TapToPlaceParent**라는 스크립트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-290">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="97a9f-291">**계층**에서 **OrigamiCollection** 를 확장 하 고 **단계** 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-291">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="97a9f-292">**TapToPlaceParent** 스크립트를 Stage 개체로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-292">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="97a9f-293">Visual Studio에서 **TapToPlaceParent** 스크립트를 열고 다음으로 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-293">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="97a9f-294">앱을 내보내고 빌드하고 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-294">Export, build and deploy the app.</span></span>
* <span data-ttu-id="97a9f-295">이제 gazing을 사용 하 고, 선택 제스처를 사용 하 고, 새 위치로 이동 하 고, 선택 제스처를 다시 사용 하 여 특정 위치에 게임을 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-295">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="chapter-7---holographic-fun"></a><span data-ttu-id="97a9f-296">7 장-Holographic 재미</span><span class="sxs-lookup"><span data-stu-id="97a9f-296">Chapter 7 - Holographic fun</span></span>

### <a name="objectives"></a><span data-ttu-id="97a9f-297">목표</span><span class="sxs-lookup"><span data-stu-id="97a9f-297">Objectives</span></span>

* <span data-ttu-id="97a9f-298">Holographic 지 수에 대 한 입구를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-298">Reveal the entrance to a holographic underworld.</span></span>

### <a name="instructions"></a><span data-ttu-id="97a9f-299">지침</span><span class="sxs-lookup"><span data-stu-id="97a9f-299">Instructions</span></span>

<span data-ttu-id="97a9f-300">이제 holographic 지 수를 파악 하는 방법을 보여 드리겠습니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-300">Now we'll show you how to uncover the holographic underworld:</span></span>

* <span data-ttu-id="97a9f-301">프로젝트 패널의 **Holograms** 폴더에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-301">From the **Holograms** folder in the Project Panel:</span></span>
  * <span data-ttu-id="97a9f-302">지 **수를 계층으로 끌어** **OrigamiCollection**의 자식으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-302">Drag **Underworld** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="97a9f-303">**Scripts** 폴더에서 **HitTarget**라는 스크립트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-303">In the **Scripts** folder, create a script named **HitTarget**.</span></span>
* <span data-ttu-id="97a9f-304">**계층**에서 **OrigamiCollection**를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-304">In the **Hierarchy**, expand the **OrigamiCollection**.</span></span>
* <span data-ttu-id="97a9f-305">**스테이지** 개체를 확장 하 고 **대상** 개체 (파란색 팬)를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-305">Expand the **Stage** object and select the **Target** object (blue fan).</span></span>
* <span data-ttu-id="97a9f-306">**HitTarget** 스크립트를 **대상** 개체로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-306">Drag the **HitTarget** script onto the **Target** object.</span></span>
* <span data-ttu-id="97a9f-307">Visual Studio에서 **HitTarget** 스크립트를 열고 다음으로 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-307">Open the **HitTarget** script in Visual Studio, and update it to be the following:</span></span>

```cs
using UnityEngine;

public class HitTarget : MonoBehaviour
{
    // These public fields become settable properties in the Unity editor.
    public GameObject underworld;
    public GameObject objectToHide;

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Hide the stage and show the underworld.
        objectToHide.SetActive(false);
        underworld.SetActive(true);

        // Disable Spatial Mapping to let the spheres enter the underworld.
        SpatialMapping.Instance.MappingEnabled = false;
    }
}
```

* <span data-ttu-id="97a9f-308">Unity에서 **대상** 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-308">In Unity, select the **Target** object.</span></span>
* <span data-ttu-id="97a9f-309">이제 **적중 대상** 구성 요소에서 두 개의 공용 속성이 표시 되 고 장면에서 개체를 참조 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-309">Two public properties are now visible on the **Hit Target** component and need to reference objects in our scene:</span></span>
  * <span data-ttu-id="97a9f-310">계층 **패널의** 지 **속성을** **적중 대상** 구성 요소의 지 속성 속성으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-310">Drag **Underworld** from the **Hierarchy** panel to the **Underworld** property on the **Hit Target** component.</span></span>
  * <span data-ttu-id="97a9f-311">**단계** 를 **계층** 패널에서 개체로 끌어 **적중 대상** 구성 요소의 속성을 **숨깁니다** .</span><span class="sxs-lookup"><span data-stu-id="97a9f-311">Drag **Stage** from the **Hierarchy** panel to the **Object to Hide** property on the **Hit Target** component.</span></span>
* <span data-ttu-id="97a9f-312">앱을 내보내고 빌드하고 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-312">Export, build and deploy the app.</span></span>
* <span data-ttu-id="97a9f-313">바닥에 종이를 놓고 선택 제스처를 사용 하 여 구를 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-313">Place the Origami Collection on the floor, and then use the Select gesture to make a sphere drop.</span></span>
* <span data-ttu-id="97a9f-314">구가 대상 (파란색 팬)에 도달 하면 폭발이 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-314">When the sphere hits the target (blue fan), an explosion will occur.</span></span> <span data-ttu-id="97a9f-315">컬렉션이 숨겨지고 지 수에 대 한 구멍이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-315">The collection will be hidden and a hole to the underworld will appear.</span></span>

## <a name="the-end"></a><span data-ttu-id="97a9f-316">끝</span><span class="sxs-lookup"><span data-stu-id="97a9f-316">The end</span></span>

<span data-ttu-id="97a9f-317">이 자습서의 끝입니다!</span><span class="sxs-lookup"><span data-stu-id="97a9f-317">And that's the end of this tutorial!</span></span>

<span data-ttu-id="97a9f-318">배운 내용:</span><span class="sxs-lookup"><span data-stu-id="97a9f-318">You learned:</span></span>

* <span data-ttu-id="97a9f-319">Unity에서 holographic 앱을 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="97a9f-319">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="97a9f-320">응시, 제스처, 음성, 소리 및 공간 매핑을 활용 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-320">How to make use of gaze, gesture, voice, sound, and spatial mapping.</span></span>
* <span data-ttu-id="97a9f-321">Visual Studio를 사용 하 여 앱을 빌드하고 배포 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="97a9f-321">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="97a9f-322">이제 사용자 고유의 holographic 환경을 만들 준비가 되었습니다!</span><span class="sxs-lookup"><span data-stu-id="97a9f-322">You are now ready to start creating your own holographic experience!</span></span>

## <a name="see-also"></a><span data-ttu-id="97a9f-323">참고 항목</span><span class="sxs-lookup"><span data-stu-id="97a9f-323">See also</span></span>

* [<span data-ttu-id="97a9f-324">MR 기본 사항 101E: 에뮬레이터를 사용 하 여 프로젝트 완료</span><span class="sxs-lookup"><span data-stu-id="97a9f-324">MR Basics 101E: Complete project with emulator</span></span>](holograms-101e.md)
* [<span data-ttu-id="97a9f-325">응시</span><span class="sxs-lookup"><span data-stu-id="97a9f-325">Gaze</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="97a9f-326">헤드 게이즈 및 커밋</span><span class="sxs-lookup"><span data-stu-id="97a9f-326">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="97a9f-327">음성 입력 </span><span class="sxs-lookup"><span data-stu-id="97a9f-327">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="97a9f-328">공간 음향</span><span class="sxs-lookup"><span data-stu-id="97a9f-328">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="97a9f-329">공간 매핑</span><span class="sxs-lookup"><span data-stu-id="97a9f-329">Spatial mapping</span></span>](spatial-mapping.md)
