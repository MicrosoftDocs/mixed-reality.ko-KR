---
title: MR 기본 사항-101E 에뮬레이터를 사용 하 여 전체 프로젝트
description: 연습 holographic 응용 프로그램의 기본 사항을 알아보려는 Unity, Visual Studio 및 HoloLens 에뮬레이터를 사용 하 여 코딩이 수행 합니다.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: 혼합된 현실 등 Windows Mixed Reality, HoloLens, 홀로그램, academy, 자습서, 에뮬레이터
ms.openlocfilehash: 77f7d497396937bf471a69fa514cef84ab0b699d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599405"
---
>[!NOTE]
><span data-ttu-id="cc85e-104">혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="cc85e-105">따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="cc85e-106">이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="cc85e-107">지원 되는 장치에서 작업을 계속 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="cc85e-108">새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="cc85e-109">게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-basics-101e-complete-project-with-emulator"></a><span data-ttu-id="cc85e-110">MR Basics 101E: 에뮬레이터를 사용 하 여 전체 프로젝트</span><span class="sxs-lookup"><span data-stu-id="cc85e-110">MR Basics 101E: Complete project with emulator</span></span>

 >[!VIDEO https://www.youtube.com/embed/Xzm8_s05mm8]

<span data-ttu-id="cc85e-111">이 자습서에서는 안내 완벽 한 프로젝트를 Unity HoloLens 포함 하 여 핵심 Windows Mixed Reality 기능을 보여 주는 기본 제공 [gaze](gaze.md)하십시오 [제스처](gestures.md), [입력음성](voice-input.md), [공간 소리](spatial-sound.md) 하 고 [공간 매핑](spatial-mapping.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-111">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](gaze.md), [gestures](gestures.md), [voice input](voice-input.md), [spatial sound](spatial-sound.md) and [spatial mapping](spatial-mapping.md).</span></span> <span data-ttu-id="cc85e-112">이 자습서를 완료 하려면 약 1 시간이 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-112">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="cc85e-113">장치 지원</span><span class="sxs-lookup"><span data-stu-id="cc85e-113">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="cc85e-114">과정</span><span class="sxs-lookup"><span data-stu-id="cc85e-114">Course</span></span></th><th style="width:150px"> <span data-ttu-id="cc85e-115"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="cc85e-115"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="cc85e-116"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="cc85e-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="cc85e-117">MR Basics 101E: 에뮬레이터를 사용 하 여 전체 프로젝트</span><span class="sxs-lookup"><span data-stu-id="cc85e-117">MR Basics 101E: Complete project with emulator</span></span></td><td style="text-align: center;"> <span data-ttu-id="cc85e-118">✔️</span><span class="sxs-lookup"><span data-stu-id="cc85e-118">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="cc85e-119">시작하기 전 주의 사항</span><span class="sxs-lookup"><span data-stu-id="cc85e-119">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="cc85e-120">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="cc85e-120">Prerequisites</span></span>

* <span data-ttu-id="cc85e-121">올바른를 사용 하 여 구성 하는 Windows 10 PC [도구가 설치 되어](install-the-tools.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-121">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>

### <a name="project-files"></a><span data-ttu-id="cc85e-122">프로젝트 파일</span><span class="sxs-lookup"><span data-stu-id="cc85e-122">Project files</span></span>

* <span data-ttu-id="cc85e-123">다운로드 합니다 [파일](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) 프로젝트에서 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-123">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="cc85e-124"> Unity 2017.2 이상이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-124"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="cc85e-125">Unity 5.6 지원이 계속 필요한 경우 사용 하세요 [이 릴리스에서](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip)합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-125">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="cc85e-126">Unity 5.5 지원 해야 하는 경우 사용 하세요 [이 릴리스에서](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip)합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-126">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="cc85e-127">Unity 5.4 지원이 계속 필요한 경우 사용 하세요 [이 릴리스에서](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip)합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-127">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="cc85e-128">취소 보관 파일을 데스크톱 또는 기타 쉽게 달성할 수 있습니다 위치 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-128">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="cc85e-129">폴더 이름을 변수로 유지 **Origami**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-129">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="cc85e-130">을 다운로드 하기 전에 소스 코드를 확인 하려는 경우 있기 [GitHub에서 사용할 수 있는](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101)합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-130">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="cc85e-131">1 장-"Holo" world</span><span class="sxs-lookup"><span data-stu-id="cc85e-131">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/qotpUpIQxVU]

<span data-ttu-id="cc85e-132">이 챕터에 첫 번째 Unity 프로젝트 및 빌드를 단계별로 설치 및 배포 프로세스에서는 했습니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-132">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="cc85e-133">목표</span><span class="sxs-lookup"><span data-stu-id="cc85e-133">Objectives</span></span>

* <span data-ttu-id="cc85e-134">Holographic 개발에 대 한 Unity를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-134">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="cc85e-135">홀로그램을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-135">Make a hologram.</span></span>
* <span data-ttu-id="cc85e-136">만든 홀로그램을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="cc85e-136">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="cc85e-137">지침</span><span class="sxs-lookup"><span data-stu-id="cc85e-137">Instructions</span></span>

* <span data-ttu-id="cc85e-138">Unity를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-138">Start Unity.</span></span>
* <span data-ttu-id="cc85e-139">선택 **열려**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-139">Select **Open**.</span></span>
* <span data-ttu-id="cc85e-140">위치를 입력 합니다 **Origami** 폴더 되지 않은 보관 된 이전에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-140">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="cc85e-141">선택 **Origami** 누릅니다 **폴더 선택**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-141">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="cc85e-142">새 장면을 저장 합니다. **파일** / **으로 장면 저장**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-142">Save the new scene: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="cc85e-143">장면 이름을 **Origami** 누릅니다 합니다 **저장** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-143">Name the scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-camera"></a><span data-ttu-id="cc85e-144">주 카메라 설정</span><span class="sxs-lookup"><span data-stu-id="cc85e-144">Setup the main camera</span></span>

* <span data-ttu-id="cc85e-145">에 **계층 패널**를 선택 **주 카메라**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-145">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="cc85e-146">에 **검사기** 변환 위치로 설정 **0,0,0**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-146">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="cc85e-147">찾을 합니다 **플래그 지우기** 속성에서 드롭다운을 변경 하 고 **Skybox** 에 **단색**.</span><span class="sxs-lookup"><span data-stu-id="cc85e-147">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="cc85e-148">클릭 합니다 **백그라운드** 필드를 색 선택기를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-148">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="cc85e-149">설정할 **R, G, B 및 A** 하 **0**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-149">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="cc85e-150">장면 설치</span><span class="sxs-lookup"><span data-stu-id="cc85e-150">Setup the scene</span></span>

* <span data-ttu-id="cc85e-151">에 **계층 패널**, 클릭 **만들기** 하 고 **빈 항목 만들기**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-151">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="cc85e-152">새을 마우스 오른쪽 단추로 클릭 **GameObject** 고 이름 바꾸기를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-152">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="cc85e-153">GameObject 이름 바꾸기 **OrigamiCollection**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-153">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="cc85e-154">**홀로그램** 폴더에는 **프로젝트 패널**:</span><span class="sxs-lookup"><span data-stu-id="cc85e-154">From the **Holograms** folder in the **Project Panel**:</span></span>
  * <span data-ttu-id="cc85e-155">끌기 **스테이지** 의 자식 계층 구조로 **OrigamiCollection**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-155">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="cc85e-156">끌기 **Sphere1** 의 자식 계층 구조로 **OrigamiCollection**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-156">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="cc85e-157">끌기 **Sphere2** 의 자식 계층 구조로 **OrigamiCollection**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-157">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="cc85e-158">마우스 오른쪽 단추로 클릭 합니다 **Directional Light** 개체를 **계층 패널** 선택한 **삭제**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-158">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="cc85e-159">**홀로그램** 폴더를 끌어서 **광원** 의 루트에는 **계층 패널**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-159">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="cc85e-160">에 **계층**를 선택 합니다 **OrigamiCollection**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-160">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="cc85e-161">에 **검사기**, 변환 위치를 설정 **0,-0.5, 2.0**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-161">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="cc85e-162">키를 눌러 합니다 **재생** 여 홀로그램 미리 보기에 Unity에서 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-162">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="cc85e-163">Origami 개체 미리 보기 창에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-163">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="cc85e-164">키를 눌러 **재생** 미리 보기 모드를 중지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-164">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="cc85e-165">Visual studio에서 Unity 프로젝트 내보내기</span><span class="sxs-lookup"><span data-stu-id="cc85e-165">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="cc85e-166">Unity select에서 **파일 > 빌드 설정**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-166">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="cc85e-167">선택 **Windows 스토어** 에 **플랫폼** 클릭 **플랫폼 전환**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-167">Select **Windows Store** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="cc85e-168">설정 **SDK** 하 **유니버설 10** 하 고 **빌드 형식** 를 **D3D**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-168">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="cc85e-169">확인할 **Unity C# 프로젝트**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-169">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="cc85e-170">클릭 **열기 장면 추가** 장면에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-170">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="cc85e-171">클릭 **플레이어 설정...** .</span><span class="sxs-lookup"><span data-stu-id="cc85e-171">Click **Player Settings...**.</span></span>
* <span data-ttu-id="cc85e-172">검사기 창 선택에서 합니다 **Windows 스토어 로고**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-172">In the Inspector Panel select the **Windows Store logo**.</span></span> <span data-ttu-id="cc85e-173">선택한 **게시 설정**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-173">Then select **Publishing Settings**.</span></span>
* <span data-ttu-id="cc85e-174">에 **기능** 섹션을 선택 합니다 **마이크** 및 **SpatialPerception** 기능.</span><span class="sxs-lookup"><span data-stu-id="cc85e-174">In the **Capabilities** section, select the **Microphone** and **SpatialPerception** capabilities.</span></span>
* <span data-ttu-id="cc85e-175">다시 빌드 설정 창에서에서 클릭 **빌드**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-175">Back in the Build Settings window, click **Build**.</span></span>
* <span data-ttu-id="cc85e-176">만들기는 **새 폴더** 이름을 "App"입니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-176">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="cc85e-177">한 번 클릭 합니다 **앱 폴더**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-177">Single click the **App Folder**.</span></span>
* <span data-ttu-id="cc85e-178">키를 눌러 **폴더 선택**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-178">Press **Select Folder**.</span></span>
* <span data-ttu-id="cc85e-179">Unity 완료 되 면 파일 탐색기 창이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-179">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="cc85e-180">엽니다는 **앱** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-180">Open the **App** folder.</span></span>
* <span data-ttu-id="cc85e-181">엽니다는 **Origami Visual Studio 솔루션**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-181">Open the **Origami Visual Studio Solution**.</span></span>
* <span data-ttu-id="cc85e-182">에 디버그 대상 변경 맨 위의 도구 모음을 사용 하 여 Visual Studio에서 **릴리스** 들어오고를 ARM **X86**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-182">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
  * <span data-ttu-id="cc85e-183">선택한 장치 단추 옆의 화살표를 클릭 **HoloLens 에뮬레이터**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-183">Click on the arrow next to the Device button, and select **HoloLens Emulator**.</span></span>
  * <span data-ttu-id="cc85e-184">클릭 **디버그-> 디버깅 없이 시작** 누르거나 **ctrl+f5**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-184">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
  * <span data-ttu-id="cc85e-185">일정 시간이 지난 후 에뮬레이터 Origami 프로젝트를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-185">After some time the emulator will start with the Origami project.</span></span> <span data-ttu-id="cc85e-186">처음 시작할 때 합니다 [에뮬레이터](using-the-hololens-emulator.md), 에뮬레이터가 시작에 대 일 분 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-186">When first launching the [emulator](using-the-hololens-emulator.md), it can take as long as 15 minutes for the emulator to start up.</span></span> <span data-ttu-id="cc85e-187">이 시작 되 면 닫지는 마세요.</span><span class="sxs-lookup"><span data-stu-id="cc85e-187">Once it starts, do not close it.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="cc85e-188">2 장-응시</span><span class="sxs-lookup"><span data-stu-id="cc85e-188">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/BPWTbAC210k]

<span data-ttu-id="cc85e-189">이 챕터에 하겠습니다 상호 작용 하는 세 가지 중 첫 번째를 도입 하 여 홀로그램-를 사용 하 여 [gaze](gaze.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-189">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](gaze.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="cc85e-190">목표</span><span class="sxs-lookup"><span data-stu-id="cc85e-190">Objectives</span></span>

* <span data-ttu-id="cc85e-191">전 세계 잠긴 커서를 사용 하 여 게이즈를 시각화 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-191">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="cc85e-192">지침</span><span class="sxs-lookup"><span data-stu-id="cc85e-192">Instructions</span></span>

* <span data-ttu-id="cc85e-193">Unity 프로젝트에 돌아가서 계속 열려 있는 경우 빌드 설정 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-193">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="cc85e-194">선택 된 **홀로그램** 폴더에는 **프로젝트 패널**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-194">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="cc85e-195">끌어서 합니다 **커서** 개체를 **계층 패널** 루트 수준에서.</span><span class="sxs-lookup"><span data-stu-id="cc85e-195">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="cc85e-196">두 번 클릭 합니다 **커서** 개체에 자세히 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-196">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="cc85e-197">마우스 오른쪽 단추로 클릭 합니다 **스크립트** 프로젝트 패널의 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-197">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="cc85e-198">클릭 합니다 **만들기** 하위 메뉴.</span><span class="sxs-lookup"><span data-stu-id="cc85e-198">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="cc85e-199">선택  **C# 스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-199">Select **C# Script**.</span></span>
* <span data-ttu-id="cc85e-200">스크립트 이름을 **WorldCursor**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-200">Name the script **WorldCursor**.</span></span> <span data-ttu-id="cc85e-201">참고: 이름은 대/소문자 구분입니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-201">Note: The name is case-sensitive.</span></span> <span data-ttu-id="cc85e-202">.Cs 확장명을 추가할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-202">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="cc85e-203">선택 된 **커서** 개체를 **계층 패널**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-203">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="cc85e-204">끌어서 놓기 합니다 **WorldCursor** 으로 스크립팅 하는 **검사기 패널**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-204">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="cc85e-205">두 번 클릭 합니다 **WorldCursor** 스크립트 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-205">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="cc85e-206">이 코드를 붙여넣습니다 **WorldCursor.cs** 하 고 **모두 저장**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-206">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

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

* <span data-ttu-id="cc85e-207">앱을 다시 빌드해야 **파일 > 빌드 설정**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-207">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="cc85e-208">이전에 배포 하는 데 에뮬레이터를 Visual Studio 솔루션에 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-208">Return to the Visual Studio solution previously used to deploy to the emulator.</span></span>
* <span data-ttu-id="cc85e-209">' 모두 다시 로드 ' 메시지가 표시 되 면 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-209">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="cc85e-210">클릭 **디버그-> 디버깅 없이 시작** 누르거나 **ctrl+f5**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-210">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="cc85e-211">장면 주위에 Xbox 컨트롤러를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-211">Use the Xbox controller to look around the scene.</span></span> <span data-ttu-id="cc85e-212">커서 개체의 모양을 상호 작용 하는 방법을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-212">Notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="cc85e-213">3 장-제스처</span><span class="sxs-lookup"><span data-stu-id="cc85e-213">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/6d-0RHeKHq4]

<span data-ttu-id="cc85e-214">이 챕터에서는 대 한 지원을 추가 했습니다 [제스처](gestures.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-214">In this chapter, we'll add support for [gestures](gestures.md).</span></span> <span data-ttu-id="cc85e-215">사용자가 문서 구체를 선택 하면 중력 Unity의 물리 엔진을 사용 하 여 설정 하 여 대체 구체를 만들 수 것입니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-215">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="cc85e-216">목표</span><span class="sxs-lookup"><span data-stu-id="cc85e-216">Objectives</span></span>

* <span data-ttu-id="cc85e-217">선택 제스처를 사용 하 여 홀로그램 사용자를 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-217">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="cc85e-218">지침</span><span class="sxs-lookup"><span data-stu-id="cc85e-218">Instructions</span></span>

<span data-ttu-id="cc85e-219">선택 제스처를 검색할 수 있습니다 보다 스크립트를 만들어서 시작 하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-219">We'll start by creating a script than can detect the Select gesture.</span></span>

* <span data-ttu-id="cc85e-220">에 **스크립트** 폴더를 라는 스크립트를 만듭니다 **GazeGestureManager**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-220">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="cc85e-221">끌기 합니다 **GazeGestureManager** 에 스크립트를 **OrigamiCollection** 개체 계층 구조에서.</span><span class="sxs-lookup"><span data-stu-id="cc85e-221">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="cc85e-222">엽니다는 **GazeGestureManager** Visual Studio에서 스크립트 및 다음 코드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-222">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

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

* <span data-ttu-id="cc85e-223">명명 된이 이번 Scripts 폴더에서 다른 스크립트를 만들 **SphereCommands**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-223">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="cc85e-224">확장을 **OrigamiCollection** 계층 뷰에서 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-224">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="cc85e-225">끌기 합니다 **SphereCommands** 에 스크립트를 **Sphere1** 계층 패널에서 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-225">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="cc85e-226">끌기 합니다 **SphereCommands** 에 스크립트를 **Sphere2** 계층 패널에서 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-226">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="cc85e-227">편집을 위해 Visual Studio에서 스크립트를 열거나 및이 사용 하 여 기본 코드를 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-227">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

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

* <span data-ttu-id="cc85e-228">내보내기, 빌드 및 HoloLens 에뮬레이터에 앱을 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-228">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="cc85e-229">장면 살펴보겠습니다는 구 중 하나에 중점을</span><span class="sxs-lookup"><span data-stu-id="cc85e-229">Look around the scene, and center on one of the spheres.</span></span>
* <span data-ttu-id="cc85e-230">키를 눌러 합니다 **는** Xbox 컨트롤러 단추 또는 스페이스바를 누르면 선택 제스처를 시뮬레이션 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-230">Press the **A** button on the Xbox controller or press the Spacebar to simulate the Select gesture.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="cc85e-231">4 장-음성</span><span class="sxs-lookup"><span data-stu-id="cc85e-231">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/LxbOhnd2_GM]

<span data-ttu-id="cc85e-232">이 챕터에서는 두 가지에 대 한 지원을 추가한 [음성 명령](voice-input.md): 원래 위치에 끌어 놓은 구 및 "놓기 sphere" "재설정된 world"를 반환 대체 구체를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-232">In this chapter, we'll add support for two [voice commands](voice-input.md): "Reset world" to returns the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="cc85e-233">목표</span><span class="sxs-lookup"><span data-stu-id="cc85e-233">Objectives</span></span>

* <span data-ttu-id="cc85e-234">백그라운드에서 항상 수신 대기 하는 음성 명령을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-234">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="cc85e-235">음성 명령에 반응 하는 홀로그램을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-235">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="cc85e-236">지침</span><span class="sxs-lookup"><span data-stu-id="cc85e-236">Instructions</span></span>

* <span data-ttu-id="cc85e-237">에 **스크립트** 폴더를 라는 스크립트를 만듭니다 **SpeechManager**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-237">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="cc85e-238">끌기 합니다 **SpeechManager** 에 스크립트를 **OrigamiCollection** 계층 구조의 개체</span><span class="sxs-lookup"><span data-stu-id="cc85e-238">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="cc85e-239">엽니다는 **SpeechManager** Visual Studio의 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-239">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="cc85e-240">이 코드를 붙여넣습니다 **SpeechManager.cs** 하 고 **모두 저장**:</span><span class="sxs-lookup"><span data-stu-id="cc85e-240">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

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

* <span data-ttu-id="cc85e-241">엽니다는 **SphereCommands** Visual Studio의 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-241">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="cc85e-242">스크립트를 다음과 같이 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-242">Update the script to read as follows:</span></span>

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

* <span data-ttu-id="cc85e-243">내보내기, 빌드 및 HoloLens 에뮬레이터에 앱을 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-243">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="cc85e-244">에뮬레이터는 PC의 마이크 지원 및 음성 응답: 커서, 구 중 하나 이므로 뷰를 조정 하 고 "Drop Sphere"입니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-244">The emulator will support your PC's microphone and respond to your voice: adjust the view so the cursor is on one of the spheres, and say "Drop Sphere".</span></span>
* <span data-ttu-id="cc85e-245">예를 들어 "**다시 설정 전 세계**"를 초기 위치로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-245">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="cc85e-246">5 장-공간 소리</span><span class="sxs-lookup"><span data-stu-id="cc85e-246">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Xc3C4VA10w4]

<span data-ttu-id="cc85e-247">이 챕터에서는에서는 음악 앱을 추가 하 고 특정 작업에 음향 효과 트리거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-247">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="cc85e-248">사용할 예정 [공간 소리](spatial-sound.md) 소리 3D 공간에서 특정 위치를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-248">We'll be using [spatial sound](spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="cc85e-249">목표</span><span class="sxs-lookup"><span data-stu-id="cc85e-249">Objectives</span></span>

* <span data-ttu-id="cc85e-250">사용자 환경에서 홀로그램 들어보세요.</span><span class="sxs-lookup"><span data-stu-id="cc85e-250">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="cc85e-251">지침</span><span class="sxs-lookup"><span data-stu-id="cc85e-251">Instructions</span></span>

* <span data-ttu-id="cc85e-252">위쪽 메뉴에서 Unity에서에서 **편집 > 프로젝트 설정 > 오디오**</span><span class="sxs-lookup"><span data-stu-id="cc85e-252">In the Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="cc85e-253">찾을 합니다 **입체 음향 플러그 인** 설정 하 고 선택 **MS HRTF 입체 음향**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-253">Find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="cc85e-254">**홀로그램** 폴더를 끌어서 합니다 **앰 비 언스** 개체를 **OrigamiCollection** 계층 패널에서 개체.</span><span class="sxs-lookup"><span data-stu-id="cc85e-254">From the **Holograms** folder, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="cc85e-255">선택 **OrigamiCollection** 찾고 합니다 **오디오 원본** 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-255">Select **OrigamiCollection** and find the **Audio Source** component.</span></span> <span data-ttu-id="cc85e-256">이러한 속성을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-256">Change these properties:</span></span>
  * <span data-ttu-id="cc85e-257">확인 합니다 **Spatialize** 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-257">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="cc85e-258">확인 합니다 **절전 모드 해제에서 재생**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-258">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="cc85e-259">변경 **공간 Blend** 하 **3D** 슬라이더 오른쪽으로 끌어서 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-259">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span>
  * <span data-ttu-id="cc85e-260">확인 합니다 **루프** 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-260">Check the **Loop** property.</span></span>
  * <span data-ttu-id="cc85e-261">확장 **3D 소리 설정**를 입력 하 고 **0.1** 에 대 한 **Doppler 수준**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-261">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="cc85e-262">설정할 **볼륨 롤오프** 하 **로그 롤오프**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-262">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="cc85e-263">설정할 **최대 거리** 하 **20**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-263">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="cc85e-264">에 **스크립트** 폴더를 라는 스크립트를 만듭니다 **SphereSounds**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-264">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="cc85e-265">끌기 **SphereSounds** 에 **Sphere1** 및 **Sphere2** 계층의 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-265">Drag **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="cc85e-266">오픈 **SphereSounds** Visual Studio에서 다음 코드를 업데이트 하 고 **모두 저장**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-266">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

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

* <span data-ttu-id="cc85e-267">스크립트를 저장 하 고 Unity로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-267">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="cc85e-268">내보내기, 빌드 및 HoloLens 에뮬레이터에 앱을 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-268">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="cc85e-269">Wear 헤드폰 전체 효과 가져오고 좀 더 자세히 및 변경 소리가 단계 멀리 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-269">Wear headphones to get the full effect, and move closer and further from the Stage to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="cc85e-270">6 장-공간 매핑</span><span class="sxs-lookup"><span data-stu-id="cc85e-270">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/S-517Y63Cnk]

<span data-ttu-id="cc85e-271">이제 사용 하려는 [공간 매핑](spatial-mapping.md) 게임판 실제 환경에서 실제 개체에 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-271">Now we are going to use [spatial mapping](spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="cc85e-272">목표</span><span class="sxs-lookup"><span data-stu-id="cc85e-272">Objectives</span></span>

* <span data-ttu-id="cc85e-273">가상 세계에 실제를 사용자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-273">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="cc85e-274">여기서는 가장 중요 한 문제를 홀로그램에 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-274">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="cc85e-275">지침</span><span class="sxs-lookup"><span data-stu-id="cc85e-275">Instructions</span></span>

* <span data-ttu-id="cc85e-276">클릭 합니다 **홀로그램** 프로젝트 패널의 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-276">Click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="cc85e-277">끌어서 합니다 **공간 매핑** 의 루트에 자산을 **계층**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-277">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="cc85e-278">클릭 합니다 **공간 매핑** 계층 구조의 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-278">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="cc85e-279">에 **검사기 패널**, 다음 속성을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-279">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="cc85e-280">확인 합니다 **Visual 메시 그리기** 상자입니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-280">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="cc85e-281">찾습니다 **그리기 자료** 오른쪽에 원을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-281">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="cc85e-282">형식 "**와이어 프레임**" 맨 위에 있는 검색 필드에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-282">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="cc85e-283">결과 클릭 하 고 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-283">Click on the result and then close the window.</span></span>
* <span data-ttu-id="cc85e-284">내보내기, 빌드 및 HoloLens 에뮬레이터에 앱을 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-284">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="cc85e-285">앱을 실행할 때 이전에 스캔 한 실제 거실 메시가 와이어 프레임에서 렌더링 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-285">When the app runs, a mesh of a previously scanned real-world living room will be rendered in wireframe.</span></span>
* <span data-ttu-id="cc85e-286">단계를 해제 하 고 바닥에 롤링 구 대체 됩니다 하는 방법을 보세요!</span><span class="sxs-lookup"><span data-stu-id="cc85e-286">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="cc85e-287">이제는 OrigamiCollection 새 위치로 이동 하는 방법을 보여드리겠습니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-287">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="cc85e-288">에 **스크립트** 폴더를 라는 스크립트를 만듭니다 **TapToPlaceParent**합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-288">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="cc85e-289">에 **계층**, 확장를 **OrigamiCollection** 선택 하 고는 **단계** 개체.</span><span class="sxs-lookup"><span data-stu-id="cc85e-289">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="cc85e-290">끌기 합니다 **TapToPlaceParent** 단계 개체에는 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-290">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="cc85e-291">엽니다는 **TapToPlaceParent** Visual Studio에서 스크립트 및 다음 업데이트:</span><span class="sxs-lookup"><span data-stu-id="cc85e-291">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="cc85e-292">내보내기, 앱 빌드 및 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-292">Export, build and deploy the app.</span></span>
* <span data-ttu-id="cc85e-293">선택 제스처를 사용 하 여 이제 이제 특정 위치에 해당 gazing 게임을 넣을 수를 (**는** 또는 스페이스바) 다음을 새 위치로 이동 하 고 선택 제스처를 다시 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-293">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture (**A** or Spacebar) and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="the-end"></a><span data-ttu-id="cc85e-294">끝</span><span class="sxs-lookup"><span data-stu-id="cc85e-294">The end</span></span>

<span data-ttu-id="cc85e-295">및이 자습서의 끝입니다!</span><span class="sxs-lookup"><span data-stu-id="cc85e-295">And that's the end of this tutorial!</span></span>

<span data-ttu-id="cc85e-296">알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-296">You learned:</span></span>

* <span data-ttu-id="cc85e-297">Unity에서 holographic 앱을 만드는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-297">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="cc85e-298">확인 방법 게이즈, 제스처, 음성, 소리 및 공간 매핑을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc85e-298">How to make use of gaze, gesture, voice, sounds, and spatial mapping.</span></span>
* <span data-ttu-id="cc85e-299">Visual Studio를 사용 하는 앱 빌드 및 배포 하는 방법.</span><span class="sxs-lookup"><span data-stu-id="cc85e-299">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="cc85e-300">이제 holographic 앱을 만들기 시작할 준비가 되었습니다!</span><span class="sxs-lookup"><span data-stu-id="cc85e-300">You are now ready to start creating your own holographic apps!</span></span>

## <a name="see-also"></a><span data-ttu-id="cc85e-301">참조</span><span class="sxs-lookup"><span data-stu-id="cc85e-301">See also</span></span>

* [<span data-ttu-id="cc85e-302">MR Basics 101: 장치를 사용 하 여 전체 프로젝트</span><span class="sxs-lookup"><span data-stu-id="cc85e-302">MR Basics 101: Complete project with device</span></span>](holograms-101.md)
* [<span data-ttu-id="cc85e-303">응시</span><span class="sxs-lookup"><span data-stu-id="cc85e-303">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="cc85e-304">제스처</span><span class="sxs-lookup"><span data-stu-id="cc85e-304">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="cc85e-305">음성 입력</span><span class="sxs-lookup"><span data-stu-id="cc85e-305">Voice input</span></span>](voice-input.md)
* [<span data-ttu-id="cc85e-306">소리 공간</span><span class="sxs-lookup"><span data-stu-id="cc85e-306">Spatial sound</span></span>](spatial-sound.md)
* [<span data-ttu-id="cc85e-307">공간 매핑</span><span class="sxs-lookup"><span data-stu-id="cc85e-307">Spatial mapping</span></span>](spatial-mapping.md)
