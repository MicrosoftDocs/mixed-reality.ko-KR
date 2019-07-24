---
title: MR 공간 220-공간 사운드
description: Unity, Visual Studio 및 HoloLens를 사용 하 여이 코딩 연습을 수행 하 여 공간 소리 개념에 대 한 세부 정보를 알아보세요.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit, 아카데미, 자습서, 공간 음향
ms.openlocfilehash: 50d17fe8c9a6e3f18b1309a59c9c41af982a7505
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63526893"
---
>[!NOTE]
><span data-ttu-id="9c5ef-104">혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="9c5ef-105">따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="9c5ef-106">이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="9c5ef-107">지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="9c5ef-108">향후에는 HoloLens 2를 개발 하는 방법을 보여 주는 새 자습서 시리즈를 게시할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="9c5ef-109">이 알림은 게시 될 때 해당 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-spatial-220-spatial-sound"></a><span data-ttu-id="9c5ef-110">MR 공간 220: 공간 음향</span><span class="sxs-lookup"><span data-stu-id="9c5ef-110">MR Spatial 220: Spatial sound</span></span>

<span data-ttu-id="9c5ef-111">[공간 사운드](spatial-sound.md) 를 holograms로 breathes 세계에 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-111">[Spatial sound](spatial-sound.md) breathes life into holograms and gives them presence in our world.</span></span> <span data-ttu-id="9c5ef-112">Holograms은 가볍고 소리로 구성 되며 Holograms의 시야가 손실 되는 경우 공간 소리를 통해 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-112">Holograms are composed of both light and sound, and if you happen to lose sight of your holograms, spatial sound can help you find them.</span></span> <span data-ttu-id="9c5ef-113">공간 사운드는 라디오 공간에 배치 되는 일반적인 사운드와는 달리, 라디오 공간에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-113">Spatial sound is not like the typical sound that you would hear on the radio, it is sound that is positioned in 3D space.</span></span> <span data-ttu-id="9c5ef-114">공간 사운드를 사용 하면 사용자, 사용자 옆 또는 머리에 있는 것 처럼 holograms 소리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-114">With spatial sound, you can make holograms sound like they're behind you, next to you, or even on your head!</span></span> <span data-ttu-id="9c5ef-115">이 과정에서는 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-115">In this course, you will:</span></span>

* <span data-ttu-id="9c5ef-116">Microsoft 공간 소리를 사용 하도록 개발 환경을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-116">Configure your development environment to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="9c5ef-117">공간 소리를 사용 하 여 상호 작용을 향상 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-117">Use Spatial Sound to enhance interactions.</span></span>
* <span data-ttu-id="9c5ef-118">공간을 공간 매핑과 함께 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-118">Use Spatial Sound in conjunction with Spatial Mapping.</span></span>
* <span data-ttu-id="9c5ef-119">사운드 디자인을 이해 하 고 모범 사례를 혼합 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-119">Understand sound design and mixing best practices.</span></span>
* <span data-ttu-id="9c5ef-120">소리를 사용 하 여 특수 효과를 향상 시키고 사용자를 혼합 현실 세계에 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-120">Use sound to enhance special effects and bring the user into the Mixed Reality world.</span></span>

## <a name="device-support"></a><span data-ttu-id="9c5ef-121">장치 지원</span><span class="sxs-lookup"><span data-stu-id="9c5ef-121">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="9c5ef-122">과정</span><span class="sxs-lookup"><span data-stu-id="9c5ef-122">Course</span></span></th><th style="width:150px"> <span data-ttu-id="9c5ef-123"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="9c5ef-123"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="9c5ef-124"><a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="9c5ef-124"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="9c5ef-125">MR 공간 220: 공간 음향</span><span class="sxs-lookup"><span data-stu-id="9c5ef-125">MR Spatial 220: Spatial sound</span></span></td><td style="text-align: center;"> <span data-ttu-id="9c5ef-126">✔️</span><span class="sxs-lookup"><span data-stu-id="9c5ef-126">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="9c5ef-127">✔️</span><span class="sxs-lookup"><span data-stu-id="9c5ef-127">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="9c5ef-128">시작하기 전 주의 사항</span><span class="sxs-lookup"><span data-stu-id="9c5ef-128">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="9c5ef-129">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="9c5ef-129">Prerequisites</span></span>

* <span data-ttu-id="9c5ef-130">올바른 [도구로](install-the-tools.md)구성 된 WINDOWS 10 PC입니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-130">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="9c5ef-131">몇 가지 C# 기본적인 프로그래밍 기능.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-131">Some basic C# programming ability.</span></span>
* <span data-ttu-id="9c5ef-132">[MR 기본 101](holograms-101.md)를 완료 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-132">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="9c5ef-133">[개발용으로 구성 된](using-visual-studio.md#enabling-developer-mode)HoloLens 장치입니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-133">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="9c5ef-134">프로젝트 파일</span><span class="sxs-lookup"><span data-stu-id="9c5ef-134">Project files</span></span>

* <span data-ttu-id="9c5ef-135">프로젝트에 필요한 [파일](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) 을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-135">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) required by the project.</span></span><span data-ttu-id="9c5ef-136"> Unity 2017.2 이상이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-136"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="9c5ef-137">Unity 5.6 지원이 계속 필요한 경우 [이 릴리스](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip)를 사용 하세요.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-137">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span></span> <span data-ttu-id="9c5ef-138">이 릴리스는 더 이상 최신 버전이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-138">This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="9c5ef-139">Unity 5.5 지원이 계속 필요한 경우 [이 릴리스](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip)를 사용 하세요.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-139">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span></span><span data-ttu-id="9c5ef-140"> 이 릴리스는 더 이상 최신 버전이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-140"> This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="9c5ef-141">Unity 5.4 지원이 계속 필요한 경우 [이 릴리스](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip)를 사용 하세요.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-141">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span></span><span data-ttu-id="9c5ef-142"> 이 릴리스는 더 이상 최신 버전이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-142"> This release may no longer be up-to-date.</span></span>
* <span data-ttu-id="9c5ef-143">바탕 화면 또는 기타 쉬운 위치에 파일을 보관 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-143">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="9c5ef-144">다운로드 하기 전에 소스 코드를 확인 하려는 경우 [GitHub에서 사용할 수](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound)있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-144">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="9c5ef-145">정오표 및 참고 사항</span><span class="sxs-lookup"><span data-stu-id="9c5ef-145">Errata and Notes</span></span>

* <span data-ttu-id="9c5ef-146">코드에서 중단점을 적중 하려면 Visual Studio의 도구-> 옵션-> 디버깅에서 "내 코드만 사용"을 사용 하지 않도록 설정 (*선택 취소*) 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-146">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="9c5ef-147">1 장-Unity 설치</span><span class="sxs-lookup"><span data-stu-id="9c5ef-147">Chapter 1 - Unity Setup</span></span>

### <a name="objectives"></a><span data-ttu-id="9c5ef-148">목표</span><span class="sxs-lookup"><span data-stu-id="9c5ef-148">Objectives</span></span>

* <span data-ttu-id="9c5ef-149">Microsoft 공간 소리를 사용 하도록 Unity의 소리 구성을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-149">Change Unity's sound configuration to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="9c5ef-150">Unity에서 개체에 3D 소리를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-150">Add 3D sound to an object in Unity.</span></span>

### <a name="instructions"></a><span data-ttu-id="9c5ef-151">지침</span><span class="sxs-lookup"><span data-stu-id="9c5ef-151">Instructions</span></span>

* <span data-ttu-id="9c5ef-152">Unity를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-152">Start Unity.</span></span>
* <span data-ttu-id="9c5ef-153">**열기**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-153">Select **Open**.</span></span>
* <span data-ttu-id="9c5ef-154">바탕 화면으로 이동 하 여 이전에 보관 하지 않은 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-154">Navigate to your Desktop and find the folder you previously un-archived.</span></span>
* <span data-ttu-id="9c5ef-155">**Starting\Decibel** 폴더를 클릭 한 다음 **폴더 선택** 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-155">Click on the **Starting\Decibel** folder and then press the **Select Folder** button.</span></span>
* <span data-ttu-id="9c5ef-156">Unity에서 프로젝트가 로드 될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-156">Wait for the project to load in Unity.</span></span>
* <span data-ttu-id="9c5ef-157"> **프로젝트** 패널에서 **Scenes\Decibel.unity**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-157">In the **Project** panel, open **Scenes\Decibel.unity**.</span></span>
* <span data-ttu-id="9c5ef-158">**계층** 패널에서 **HologramCollection** 를 확장 하 고 **P0LY**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-158">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="9c5ef-159">검사기에서 **오디오 소스** 를 확장 하 고 **Spatialize** 확인란이 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-159">In the Inspector, expand **AudioSource** and notice that there is no **Spatialize** check box.</span></span>

<span data-ttu-id="9c5ef-160">기본적으로 Unity는 spatializer 플러그 인을 로드 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-160">By default, Unity does not load a spatializer plugin.</span></span> <span data-ttu-id="9c5ef-161">다음 단계에서는 프로젝트에서 공간 소리를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-161">The following steps will enable Spatial Sound in the project.</span></span>

* <span data-ttu-id="9c5ef-162">Unity의 최상위 메뉴에서 **편집 > 프로젝트 설정 > 오디오**로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-162">In Unity's top menu, go to **Edit > Project Settings > Audio**.</span></span>
* <span data-ttu-id="9c5ef-163">**Spatializer 플러그 인** 드롭다운을 찾고 **MS hrtf Spatializer**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-163">Find the **Spatializer Plugin** dropdown, and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="9c5ef-164">**계층** 패널에서 **HologramCollection > P0LY**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-164">In the **Hierarchy** panel, select **HologramCollection > P0LY**.</span></span>
* <span data-ttu-id="9c5ef-165">**검사기** 패널에서 **오디오 원본** 구성 요소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-165">In the **Inspector** panel, find the **Audio Source** component.</span></span>
* <span data-ttu-id="9c5ef-166">**Spatialize** 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-166">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="9c5ef-167">**공간 Blend** 슬라이더를 **3d**로 끌어 놓거나 편집 상자에 **1** 을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-167">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>

<span data-ttu-id="9c5ef-168">이제 Unity에서 프로젝트를 빌드하고 Visual Studio에서 솔루션을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-168">We will now build the project in Unity and configure the solution in Visual Studio.</span></span>

1. <span data-ttu-id="9c5ef-169">Unity에서 **파일 > 빌드 설정**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-169">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="9c5ef-170">열려 있는 장면 **추가** 를 클릭 하 여 장면을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-170">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="9c5ef-171">**플랫폼** 목록에서 **유니버설 Windows 플랫폼** 을 선택 하 고 **플랫폼 전환**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-171">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="9c5ef-172">특별히 HoloLens를 개발 하는 경우 **대상 장치** 를 **hololens**로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-172">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="9c5ef-173">그렇지 않으면 **모든 장치**에 그대로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-173">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="9c5ef-174">**빌드 형식이** **D3D** 로 설정 되 고 **sdk** 가 **최신 버전** 으로 설정 되어 있는지 확인 합니다 (sdk 16299 이상 이어야 함).</span><span class="sxs-lookup"><span data-stu-id="9c5ef-174">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="9c5ef-175">**빌드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-175">Click **Build**.</span></span>
7. <span data-ttu-id="9c5ef-176">"App" 이라는 **새 폴더** 를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-176">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="9c5ef-177">단일 **앱** 폴더를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-177">Single click the **App** folder.</span></span>
9. <span data-ttu-id="9c5ef-178">**폴더 선택**을 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-178">Press **Select Folder**.</span></span>

<span data-ttu-id="9c5ef-179">Unity가 완료 되 면 파일 탐색기 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-179">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="9c5ef-180">**앱** 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-180">Open the **App** folder.</span></span>
2. <span data-ttu-id="9c5ef-181">**데시벨 Visual Studio 솔루션**을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-181">Open the **Decibel Visual Studio Solution**.</span></span>

<span data-ttu-id="9c5ef-182">HoloLens에 배포 하는 경우:</span><span class="sxs-lookup"><span data-stu-id="9c5ef-182">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="9c5ef-183">Visual Studio의 맨 위 도구 모음을 사용 하 여 대상을 디버그에서 **릴리스** 로, ARM에서 **x 86**으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-183">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="9c5ef-184">로컬 컴퓨터 단추 옆에 있는 드롭다운 화살표를 클릭 하 고 **원격 컴퓨터**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-184">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="9c5ef-185">**HoloLens 장치 IP 주소** 를 입력 하 고 인증 모드를 **유니버설 (암호화 되지 않은 프로토콜)** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-185">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="9c5ef-186">**선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-186">Click **Select**.</span></span> <span data-ttu-id="9c5ef-187">장치 IP 주소를 모르는 경우 **네트워크 & 인터넷 > 고급 옵션 > 설정**을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-187">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="9c5ef-188">상단 메뉴 모음에서 **디버그-> 디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-188">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="9c5ef-189">처음으로 장치에 배포 하는 경우에는 [Visual Studio와 쌍](using-visual-studio.md#pairing-your-device---hololens-1st-gen)으로 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-189">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device---hololens-1st-gen).</span></span>

<span data-ttu-id="9c5ef-190">모던 헤드셋에 배포 하는 경우:</span><span class="sxs-lookup"><span data-stu-id="9c5ef-190">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="9c5ef-191">Visual Studio의 맨 위 도구 모음을 사용 하 여 대상을 디버그에서 **릴리스** 로, ARM에서 x **64**로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-191">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="9c5ef-192">배포 대상이 **로컬 컴퓨터**로 설정 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-192">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="9c5ef-193">상단 메뉴 모음에서 **디버그-> 디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-193">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>

## <a name="chapter-2---spatial-sound-and-interaction"></a><span data-ttu-id="9c5ef-194">2 장-공간 소리 및 상호 작용</span><span class="sxs-lookup"><span data-stu-id="9c5ef-194">Chapter 2 - Spatial Sound and Interaction</span></span>

### <a name="objectives"></a><span data-ttu-id="9c5ef-195">목표</span><span class="sxs-lookup"><span data-stu-id="9c5ef-195">Objectives</span></span>

* <span data-ttu-id="9c5ef-196">소리를 사용 하 여 홀로그램 현실감을 향상 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-196">Enhance hologram realism using sound.</span></span>
* <span data-ttu-id="9c5ef-197">소리를 사용 하 여 사용자의 응시를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-197">Direct the user's gaze using sound.</span></span>
* <span data-ttu-id="9c5ef-198">소리를 사용 하 여 제스처 피드백을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-198">Provide gesture feedback using sound.</span></span>

### <a name="part-1---enhancing-realism"></a><span data-ttu-id="9c5ef-199">1 부-현실감 향상</span><span class="sxs-lookup"><span data-stu-id="9c5ef-199">Part 1 - Enhancing Realism</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="9c5ef-200">주요 개념</span><span class="sxs-lookup"><span data-stu-id="9c5ef-200">Key Concepts</span></span>

* <span data-ttu-id="9c5ef-201">Spatialize 홀로그램 소리.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-201">Spatialize hologram sounds.</span></span>
* <span data-ttu-id="9c5ef-202">사운드 원본은 홀로그램의 적절 한 위치에 배치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-202">Sound sources should be placed at an appropriate location on the hologram.</span></span>

<span data-ttu-id="9c5ef-203">적절 한 소리 위치는 홀로그램에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-203">The appropriate location for the sound is going to depend on the hologram.</span></span> <span data-ttu-id="9c5ef-204">예를 들어, 홀로그램이 사람이 라면 음은 피트가 아니라 입 근처에 위치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-204">For example, if the hologram is of a human, the sound source should be located near the mouth and not the feet.</span></span>

#### <a name="instructions"></a><span data-ttu-id="9c5ef-205">지침</span><span class="sxs-lookup"><span data-stu-id="9c5ef-205">Instructions</span></span>

<span data-ttu-id="9c5ef-206">다음 지침에서는 spatialized 소리를 홀로그램에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-206">The following instructions will attach a spatialized sound to a hologram.</span></span>

* <span data-ttu-id="9c5ef-207">**계층** 패널에서 **HologramCollection** 를 확장 하 고 **P0LY**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-207">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="9c5ef-208">**검사기** 패널의 **오디오 원본**에서 **오디오 클립** 옆의 원을 클릭 하 고 팝업에서 **PolyHover** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-208">In the **Inspector** panel, in the **AudioSource**, click the circle next to **AudioClip** and select **PolyHover** from the pop-up.</span></span>
* <span data-ttu-id="9c5ef-209">**출력** 옆의 원을 클릭 하 고 팝업에서 **SoundEffects** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-209">Click the circle next to **Output** and select **SoundEffects** from the pop-up.</span></span>

<span data-ttu-id="9c5ef-210">프로젝트는 Unity **오디오 믹서** 구성 요소를 사용 하 여 소리 그룹의 소리 수준을 조정할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-210">Project Decibel uses a Unity **AudioMixer** component to enable adjusting sound levels for groups of sounds.</span></span> <span data-ttu-id="9c5ef-211">이러한 방식으로 소리를 그룹화 하면 각 소리의 상대적 볼륨을 유지 하면서 전체 볼륨을 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-211">By grouping sounds this way, the overall volume can be adjusted while maintaining the relative volume of each sound.</span></span>

* <span data-ttu-id="9c5ef-212">**오디오 소스**에서 **3d 사운드 설정**을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-212">In the **AudioSource**, expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="9c5ef-213">**Doppler Level** 을 **0**으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-213">Set **Doppler Level** to **0**.</span></span>

<span data-ttu-id="9c5ef-214">Doppler level을 0으로 설정 하면 이동 (홀로그램 또는 사용자 중 하나)으로 인 한 피치의 변화가 비활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-214">Setting Doppler level to zero disables changes in pitch caused by motion (either of the hologram or the user).</span></span> <span data-ttu-id="9c5ef-215">Doppler의 전형적인 예는 빠른 이동 차량입니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-215">A classic example of Doppler is a fast-moving car.</span></span> <span data-ttu-id="9c5ef-216">자동차가 고정 수신기에 가까워지면 엔진의 피치는 증가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-216">As the car approaches a stationary listener, the pitch of the engine rises.</span></span> <span data-ttu-id="9c5ef-217">수신기가 전달 되 면 피치는 거리가 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-217">When it passes the listener, the pitch lowers with distance.</span></span>

### <a name="part-2---directing-the-users-gaze"></a><span data-ttu-id="9c5ef-218">2 부-사용자의 응시 전달</span><span class="sxs-lookup"><span data-stu-id="9c5ef-218">Part 2 - Directing the User's Gaze</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="9c5ef-219">주요 개념</span><span class="sxs-lookup"><span data-stu-id="9c5ef-219">Key Concepts</span></span>

* <span data-ttu-id="9c5ef-220">소리를 사용 하 여 중요 한 holograms에 주의를 기울여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-220">Use sound to call attention to important holograms.</span></span>
* <span data-ttu-id="9c5ef-221">귀는 눈이 보이는 위치를 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-221">The ears help direct where the eyes should look.</span></span>
* <span data-ttu-id="9c5ef-222">두뇌는 몇 가지 배운 기대를 갖고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-222">The brain has some learned expectations.</span></span>

<span data-ttu-id="9c5ef-223">배운 기대에 대 한 한 가지 예는 일반 사람이 일반적으로 사람을 나타내는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-223">One example of learned expectations is that birds are generally above the heads of humans.</span></span> <span data-ttu-id="9c5ef-224">사용자가 소리를 듣게 되 면 초기 반응을 조회 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-224">If a user hears a bird sound, their initial reaction is to look up.</span></span> <span data-ttu-id="9c5ef-225">사용자를 아래에 배치 하면 올바른 소리 방향을 향하도록 할 수 있지만 조회 해야 하는 기대에 따라 홀로그램을 찾을 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-225">Placing a bird below the user can lead to them facing the correct direction of the sound, but being unable to find the hologram based on the expectation of needing to look up.</span></span>

#### <a name="instructions"></a><span data-ttu-id="9c5ef-226">지침</span><span class="sxs-lookup"><span data-stu-id="9c5ef-226">Instructions</span></span>

<span data-ttu-id="9c5ef-227">다음 지침에 따라 P0LY를 사용 하 여 홀로그램을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-227">The following instructions enable P0LY to hide behind you, so that you can use sound to locate the hologram.</span></span>

* <span data-ttu-id="9c5ef-228">**계층** 패널에서 **관리자**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-228">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="9c5ef-229">**검사기** 패널에서 **음성 입력 처리기**를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-229">In the **Inspector** panel, find **Speech Input Handler**.</span></span>
* <span data-ttu-id="9c5ef-230">**음성 입력 처리기**에서 **이동 숨기기**를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-230">In **Speech Input Handler**, expand **Go Hide**.</span></span>
* <span data-ttu-id="9c5ef-231">**No 함수** 를 **PolyActions**로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-231">Change **No Function** to **PolyActions.GoHide**.</span></span>

![키워드로 숨기기로 이동](images/gohide.png)

### <a name="part-3---gesture-feedback"></a><span data-ttu-id="9c5ef-233">3 부-제스처 피드백</span><span class="sxs-lookup"><span data-stu-id="9c5ef-233">Part 3 - Gesture Feedback</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="9c5ef-234">주요 개념</span><span class="sxs-lookup"><span data-stu-id="9c5ef-234">Key Concepts</span></span>

* <span data-ttu-id="9c5ef-235">사용자에 게 소리를 사용 하 여 긍정 제스처 확인 제공</span><span class="sxs-lookup"><span data-stu-id="9c5ef-235">Provide the user with positive gesture confirmation using sound</span></span>
* <span data-ttu-id="9c5ef-236">사용자가 과도 하 게 소리를 이동 하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-236">Do not overwhelm the user - overly loud sounds get in the way</span></span>
* <span data-ttu-id="9c5ef-237">미세한 소리는 최적으로 작동 합니다. 환경을 과도 하 게 숨기지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-237">Subtle sounds work best - do not overshadow the experience</span></span>

#### <a name="instructions"></a><span data-ttu-id="9c5ef-238">지침</span><span class="sxs-lookup"><span data-stu-id="9c5ef-238">Instructions</span></span>

* <span data-ttu-id="9c5ef-239">**계층** 패널에서 **HologramCollection**를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-239">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="9c5ef-240">**EnergyHub** 를 확장 하 고 **Base**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-240">Expand **EnergyHub** and select **Base**.</span></span>
* <span data-ttu-id="9c5ef-241">**검사기** 패널에서 **구성 요소 추가** 를 클릭 하 고 **제스처 소리 처리기**를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-241">In the **Inspector** panel, click **Add Component** and add **Gesture Sound Handler**.</span></span>
* <span data-ttu-id="9c5ef-242">**제스처 소리 처리기**에서 **탐색 시작 클립** 옆의 동그라미를 클릭 하 고 **업데이트 된 클립을 탐색** 하 고 두 가지 모두에 대 한 팝업에서 **RotateClick** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-242">In **Gesture Sound Handler**, click the circle next to **Navigation Started Clip** and **Navigation Updated Clip** and select **RotateClick** from the pop-up for both.</span></span>
* <span data-ttu-id="9c5ef-243">"GestureSoundHandler"를 두 번 클릭 하 여 Visual Studio에서 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-243">Double click on "GestureSoundHandler" to load in Visual Studio.</span></span>

<span data-ttu-id="9c5ef-244">제스처 소리 처리기는 다음 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-244">Gesture Sound Handler performs the following tasks:</span></span>

* <span data-ttu-id="9c5ef-245">**오디오 소스**를 만들고 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-245">Create and configure an **AudioSource**.</span></span>
* <span data-ttu-id="9c5ef-246">해당 **GameObject**의 위치에 **오디오 원본을** 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-246">Place the **AudioSource** at the location of the appropriate **GameObject**.</span></span>
* <span data-ttu-id="9c5ef-247">제스처와 연결 된 **오디오 클립** 을 재생 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-247">Plays the **AudioClip** associated with the gesture.</span></span>

#### <a name="build-and-deploy"></a><span data-ttu-id="9c5ef-248">빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="9c5ef-248">Build and Deploy</span></span>

1. <span data-ttu-id="9c5ef-249">Unity에서 **파일 > 빌드 설정**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-249">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="9c5ef-250">**빌드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-250">Click **Build**.</span></span>
3. <span data-ttu-id="9c5ef-251">단일 **앱** 폴더를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-251">Single click the **App** folder.</span></span>
4. <span data-ttu-id="9c5ef-252">**폴더 선택**을 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-252">Press **Select Folder**.</span></span>

<span data-ttu-id="9c5ef-253">도구 모음에 "릴리스", "x86", "x64" 및 "원격 장치"가 표시 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-253">Check that the Toolbar says "Release", "x86" or "x64", and "Remote Device".</span></span> <span data-ttu-id="9c5ef-254">그렇지 않으면 Visual Studio의 코딩 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-254">If not, this is the coding instance of Visual Studio.</span></span> <span data-ttu-id="9c5ef-255">앱 폴더에서 솔루션을 다시 열어야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-255">You may need to re-open the solution from the App folder.</span></span>

* <span data-ttu-id="9c5ef-256">메시지가 표시 되 면 프로젝트 파일을 다시 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-256">If prompted, reload the project files.</span></span>
* <span data-ttu-id="9c5ef-257">이전과 마찬가지로 Visual Studio에서 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-257">As before, deploy from Visual Studio.</span></span>

<span data-ttu-id="9c5ef-258">응용 프로그램을 배포한 후:</span><span class="sxs-lookup"><span data-stu-id="9c5ef-258">After the application is deployed:</span></span>

* <span data-ttu-id="9c5ef-259">P0LY 주위로 이동 하면서 사운드가 어떻게 변화 하는지 관찰 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-259">Observe how the sound changes as you move around P0LY.</span></span>
* <span data-ttu-id="9c5ef-260">P0LY를 사용자의 한 위치로 이동 하려면 *"감추기"* 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-260">Say *"Go Hide"* to make P0LY move to a location behind you.</span></span> <span data-ttu-id="9c5ef-261">소리를 통해 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-261">Find it by the sound.</span></span>
* <span data-ttu-id="9c5ef-262">에너지 허브의 기반을 응시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-262">Gaze at the base of the Energy Hub.</span></span> <span data-ttu-id="9c5ef-263">왼쪽 또는 오른쪽을 탭 하 고 끌어서 홀로그램을 회전 하 고 클릭 한 소리에서 제스처를 확인 하는 방법을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-263">Tap and drag left or right to rotate the hologram and notice how the clicking sound confirms the gesture.</span></span>

<span data-ttu-id="9c5ef-264">참고: 태그를 표시 하는 텍스트 패널이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-264">Note: There is a text panel that will tag-along with you.</span></span> <span data-ttu-id="9c5ef-265">여기에는이 과정 전체에서 사용할 수 있는 음성 명령이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-265">This will contain the available voice commands that you can use throughout this course.</span></span>

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a><span data-ttu-id="9c5ef-266">3 장-공간 소리 및 공간 매핑</span><span class="sxs-lookup"><span data-stu-id="9c5ef-266">Chapter 3 - Spatial Sound and Spatial Mapping</span></span>

### <a name="objectives"></a><span data-ttu-id="9c5ef-267">목표</span><span class="sxs-lookup"><span data-stu-id="9c5ef-267">Objectives</span></span>

* <span data-ttu-id="9c5ef-268">소리를 사용 하 여 holograms와 실제 세계 간의 상호 작용을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-268">Confirm interaction between holograms and the real world using sound.</span></span>
* <span data-ttu-id="9c5ef-269">실제 세계를 사용 하는 소리를 려.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-269">Occlude sound using the physical world.</span></span>

### <a name="part-1---physical-world-interaction"></a><span data-ttu-id="9c5ef-270">1 부-물리적 세계 상호 작용</span><span class="sxs-lookup"><span data-stu-id="9c5ef-270">Part 1 - Physical World Interaction</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="9c5ef-271">주요 개념</span><span class="sxs-lookup"><span data-stu-id="9c5ef-271">Key Concepts</span></span>

* <span data-ttu-id="9c5ef-272">일반적으로 실제 개체는 표면이 나 다른 개체가 발생할 때 소리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-272">Physical objects generally make a sound when encountering a surface or another object.</span></span>
* <span data-ttu-id="9c5ef-273">소리는 환경 내에서 적절 한 상황 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-273">Sounds should be context appropriate within the experience.</span></span>

<span data-ttu-id="9c5ef-274">예를 들어 테이블에서 컵을 설정 하는 것은 금속을 제거 하는 것 보다 더 조용한 소리를 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-274">For example, setting a cup on a table should make a quieter sound than dropping a boulder on a piece of metal.</span></span>

#### <a name="instructions"></a><span data-ttu-id="9c5ef-275">지침</span><span class="sxs-lookup"><span data-stu-id="9c5ef-275">Instructions</span></span>

* <span data-ttu-id="9c5ef-276">**계층** 패널에서 **HologramCollection**를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-276">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="9c5ef-277">**EnergyHub**를 확장 하 고 **기본**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-277">Expand **EnergyHub**, select **Base**.</span></span>
* <span data-ttu-id="9c5ef-278">**검사기** 패널에서 **구성 요소 추가** 를 클릭 하 고 **소리 및 동작을 사용 하 여 탭을**추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-278">In the **Inspector** panel, click **Add Component** and add **Tap To Place With Sound and Action**.</span></span>
* <span data-ttu-id="9c5ef-279">**소리 및 작업을 사용 하 여 이동 합니다**.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-279">In **Tap To Place With Sound and Action**:</span></span>
  * <span data-ttu-id="9c5ef-280">**부모를 탭**하 여 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-280">Check **Place Parent On Tap**.</span></span>
  * <span data-ttu-id="9c5ef-281">**배치 사운드** **를 설정**합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-281">Set **Placement Sound** to **Place**.</span></span>
  * <span data-ttu-id="9c5ef-282">픽업 **소리** 를 **픽업**소리로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-282">Set **Pickup Sound** to **Pickup**.</span></span>
  * <span data-ttu-id="9c5ef-283">**픽업 동작** 및 **배치 동작**양쪽의 오른쪽 아래에 있는 +를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-283">Press the + in the bottom right under both **On Pickup Action** and **On Placement Action**.</span></span> <span data-ttu-id="9c5ef-284">EnergyHub를 장면에서 **없음 (개체)** 필드로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-284">Drag EnergyHub from the scene into the **None (Object)** fields.</span></span>
    * <span data-ttu-id="9c5ef-285">**픽업 동작에서** **EnergyHubBase** ->  resetanimation함수 -> 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-285">Under **On Pickup Action**, click on **No Function** -> **EnergyHubBase** -> **ResetAnimation**.</span></span>
    * <span data-ttu-id="9c5ef-286">**배치 동작에서** **EnergyHubBase** ->  onselect함수 -> 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-286">Under **On Placement Action**, click on **No Function** -> **EnergyHubBase** -> **OnSelect**.</span></span>

![소리 및 동작으로 이동 하려면 탭 하세요.](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a><span data-ttu-id="9c5ef-288">2 부-소리 폐색</span><span class="sxs-lookup"><span data-stu-id="9c5ef-288">Part 2 - Sound Occlusion</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="9c5ef-289">주요 개념</span><span class="sxs-lookup"><span data-stu-id="9c5ef-289">Key Concepts</span></span>

* <span data-ttu-id="9c5ef-290">광원은 폐색 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-290">Sound, like light, can be occluded.</span></span>

<span data-ttu-id="9c5ef-291">일반적인 예로는 콘서트 홀이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-291">A classic example is a concert hall.</span></span> <span data-ttu-id="9c5ef-292">수신기가 홀 외부에 있을 때 도어가 닫혀 있으면 음악은 muffled.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-292">When a listener is standing outside of the hall and the door is closed, the music sounds muffled.</span></span> <span data-ttu-id="9c5ef-293">일반적으로 볼륨을 축소 하기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-293">There is also typically a reduction in volume.</span></span> <span data-ttu-id="9c5ef-294">도어가 열리면 실제 볼륨에서 소리의 전체 스펙트럼을 듣게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-294">When the door is opened, the full spectrum of the sound is heard at the actual volume.</span></span> <span data-ttu-id="9c5ef-295">일반적으로 빈도가 낮은 소리는 낮은 주파수 보다 더 많이 흡수 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-295">High frequency sounds are generally absorbed more than low frequencies.</span></span>

#### <a name="instructions"></a><span data-ttu-id="9c5ef-296">지침</span><span class="sxs-lookup"><span data-stu-id="9c5ef-296">Instructions</span></span>

* <span data-ttu-id="9c5ef-297">**계층** 패널에서 **HologramCollection** 를 확장 하 고 **P0LY**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-297">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="9c5ef-298">**검사기** 패널에서 **구성 요소 추가** 를 클릭 하 고 **오디오 송신기**를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-298">In the **Inspector** panel, click **Add Component** and add **Audio Emitter**.</span></span>

<span data-ttu-id="9c5ef-299">오디오 내보내기 클래스는 다음과 같은 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-299">The Audio Emitter class provides the following features:</span></span>

* <span data-ttu-id="9c5ef-300">**오디오 원본**볼륨의 변경 내용을 복원 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-300">Restores any changes to the volume of the **AudioSource**.</span></span>
* <span data-ttu-id="9c5ef-301">**AudioEmitter** 가 연결 된 **GameObject** 방향의 사용자 위치에서 **RaycastNonAlloc** 를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-301">Performs a **Physics.RaycastNonAlloc** from the user's position in the direction of the **GameObject** to which the **AudioEmitter** is attached.</span></span>

<span data-ttu-id="9c5ef-302">RaycastNonAlloc 메서드는 반환 되는 결과 수 뿐만 아니라 할당을 제한 하기 위한 성능 최적화로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-302">The RaycastNonAlloc method is used as a performance optimization to limit allocations as well as the number of results returned.</span></span>

* <span data-ttu-id="9c5ef-303">발견 된 각 **IAudioInfluencer** 에 대해 **applyeffect** 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-303">For each **IAudioInfluencer** encountered, calls the **ApplyEffect** method.</span></span>
* <span data-ttu-id="9c5ef-304">더 이상 발생 하지 않는 각 이전 **IAudioInfluencer** 에 대해 **removeeffect** 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-304">For each previous **IAudioInfluencer** that is no longer encountered, call the **RemoveEffect** method.</span></span>

<span data-ttu-id="9c5ef-305">인간 시간에 대 한 AudioEmitter 업데이트는 프레임 기준에 비해 확장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-305">Note that AudioEmitter updates on human time scales, as opposed to on a per frame basis.</span></span> <span data-ttu-id="9c5ef-306">이러한 작업은 일반적으로 일부 분기 또는 1/2 초 보다 더 자주 업데이트 해야 하는 결과가 충분히 빨리 이동 하지 않기 때문에 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-306">This is done because humans generally do not move fast enough for the effect to need to be updated more frequently than every quarter or half of a second.</span></span> <span data-ttu-id="9c5ef-307">한 위치에서 다른 위치로 빠르게 Holograms 환상 효과를 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-307">Holograms that teleport rapidly from one location to another can break the illusion.</span></span>

* <span data-ttu-id="9c5ef-308">**계층** 패널에서 **HologramCollection**를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-308">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="9c5ef-309">**EnergyHub** 를 확장 하 고 **bloboutside**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-309">Expand **EnergyHub** and select **BlobOutside**.</span></span>
* <span data-ttu-id="9c5ef-310">**검사기** 패널에서 **구성 요소 추가** 및 **오디오 추가 Occluder**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-310">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="9c5ef-311">**Audio Occluder**에서 **구분 빈도** 를 **1500**으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-311">In **Audio Occluder**, set **Cutoff Frequency** to **1500**.</span></span>

<span data-ttu-id="9c5ef-312">이 설정은 오디오 원본 빈도를 1500 Hz 이하로 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-312">This setting limits the AudioSource frequencies to 1500 Hz and below.</span></span>

* <span data-ttu-id="9c5ef-313">**볼륨 통과** 를 **0.9**으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-313">Set **Volume Pass Through** to **0.9**.</span></span>

<span data-ttu-id="9c5ef-314">이 설정은 오디오 원본의 볼륨을 현재 수준의 90%로 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-314">This setting reduces the volume of the AudioSource to 90% of it's current level.</span></span>

<span data-ttu-id="9c5ef-315">Audio Occluder는 IAudioInfluencer을 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-315">Audio Occluder implements IAudioInfluencer to:</span></span>

* <span data-ttu-id="9c5ef-316">**AudioEmitter**를 구매한 폐색에 연결 되는 **AudioLowPassFilter** 를 사용 하  여 효과를 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-316">Apply an occlusion effect using an **AudioLowPassFilter** which gets attached to the **AudioSource** managed buy the **AudioEmitter**.</span></span>
* <span data-ttu-id="9c5ef-317">볼륨 감쇠를 오디오 소스에 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-317">Applies volume attenuation to the AudioSource.</span></span>
* <span data-ttu-id="9c5ef-318">중립 구분 빈도를 설정 하 고 필터를 사용 하지 않도록 설정 하 여 효과를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-318">Disables the effect by setting a neutral cutoff frequency and disabling the filter.</span></span>

<span data-ttu-id="9c5ef-319">중립으로 사용 되는 빈도는 22khz (22000 Hz)입니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-319">The frequency used as neutral is 22 kHz (22000 Hz).</span></span> <span data-ttu-id="9c5ef-320">이 빈도는 인간 귀에 의해 들릴 수 있는 명목상의 최대 주파수를 초과 하기 때문에 선택 되었으며 소리에 띄는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-320">This frequency was chosen due to it being above the nominal maximum frequency that can be heard by the human ear, this making no discernable impact to the sound.</span></span>

* <span data-ttu-id="9c5ef-321">**계층** 패널에서 **SpatialMapping**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-321">In the **Hierarchy** panel, select **SpatialMapping**.</span></span>
* <span data-ttu-id="9c5ef-322">**검사기** 패널에서 **구성 요소 추가** 및 **오디오 추가 Occluder**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-322">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="9c5ef-323">**Audio Occluder**에서 **구분 빈도** 를 **750**으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-323">In **Audio Occluder**, set **Cutoff Frequency** to **750**.</span></span>

<span data-ttu-id="9c5ef-324">사용자와 **AudioEmitter**간의 경로에 여러 occluders가 있는 경우 가장 낮은 빈도가 필터에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-324">When multiple occluders are in the path between the user and the **AudioEmitter**, the lowest frequency is applied to the filter.</span></span>

* <span data-ttu-id="9c5ef-325">**볼륨 통과** 를 **0.75**으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-325">Set **Volume Pass Through** to **0.75**.</span></span>

<span data-ttu-id="9c5ef-326">사용자와 **AudioEmitter**간의 경로에 여러 개의 occluders가 있는 경우 볼륨 통과가 추가로 업데이트할지 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-326">When multiple occluders are in the path between the user and the **AudioEmitter**, the volume pass through is applied additively.</span></span>

* <span data-ttu-id="9c5ef-327">**계층** 패널에서 **관리자**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-327">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="9c5ef-328">**검사기** 패널에서 **Speech Input Handler**를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-328">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="9c5ef-329">**음성 입력 처리기**에서 **이동 요금**을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-329">In **Speech Input Handler**, expand **Go Charge**.</span></span>
* <span data-ttu-id="9c5ef-330">**No 함수** 를 **PolyActions**로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-330">Change **No Function** to **PolyActions.GoCharge**.</span></span>

![키워드로 요금 청구](images/gocharge.png)

* <span data-ttu-id="9c5ef-332">확장은 **여기에서 제공**됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-332">Expand **Come Here**.</span></span>
* <span data-ttu-id="9c5ef-333">**No 함수** 를 **PolyActions**로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-333">Change **No Function** to **PolyActions.ComeBack**.</span></span>

![키워드로 여기로 오세요](images/comehere.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="9c5ef-335">빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="9c5ef-335">Build and Deploy</span></span>

* <span data-ttu-id="9c5ef-336">이전과 마찬가지로 Unity에서 프로젝트를 빌드하고 Visual Studio에서 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-336">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="9c5ef-337">응용 프로그램을 배포한 후:</span><span class="sxs-lookup"><span data-stu-id="9c5ef-337">After the application is deployed:</span></span>

* <span data-ttu-id="9c5ef-338">P0LY을 에너지 허브로 전환 하려면 *"요금 청구"* 라고 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-338">Say *"Go Charge"* to have P0LY enter the Energy Hub.</span></span>

<span data-ttu-id="9c5ef-339">소리의 변화를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-339">Note the change in the sound.</span></span> <span data-ttu-id="9c5ef-340">Muffled 하 고 약간 더 조용한 소리를 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-340">It should sound muffled and a little quieter.</span></span> <span data-ttu-id="9c5ef-341">사용자와 에너지 허브 사이에 벽 또는 다른 개체를 배치할 수 있는 경우 실제 폐색로 인 한 소리의 추가 muffling을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-341">If you are able to position yourself with a wall or other object between you and the Energy Hub, you should notice a further muffling of the sound due to the occlusion by the real world.</span></span>

* <span data-ttu-id="9c5ef-342">에너지 허브를 P0LY 하 고 그 앞에 *배치 하는* 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-342">Say *"Come Here"* to have P0LY leave the Energy Hub and position itself in front of you.</span></span>

<span data-ttu-id="9c5ef-343">P0LY가 에너지 허브를 종료 하면 소리 폐색 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-343">Note that the sound occlusion is removed once P0LY exits the Energy Hub.</span></span> <span data-ttu-id="9c5ef-344">계속 해 서 폐색 하는 경우 P0LY는 실제 세계에서 폐색 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-344">If you are still hearing occlusion, P0LY may be occluded by the real world.</span></span> <span data-ttu-id="9c5ef-345">P0LY에 대 한 시야를 명확 하 게 볼 수 있도록 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-345">Try moving to ensure you have a clear line of sight to P0LY.</span></span>

### <a name="part-3---room-models"></a><span data-ttu-id="9c5ef-346">3 부 실 모델</span><span class="sxs-lookup"><span data-stu-id="9c5ef-346">Part 3 - Room Models</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="9c5ef-347">주요 개념</span><span class="sxs-lookup"><span data-stu-id="9c5ef-347">Key Concepts</span></span>

* <span data-ttu-id="9c5ef-348">공간 크기는 소리 지역화에 기여 하는 subliminal 큐를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-348">The size of the space provides subliminal queues that contribute to sound localization.</span></span>
* <span data-ttu-id="9c5ef-349">방 모델은 비-**오디오 원본**으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-349">Room models are set per-**AudioSource**.</span></span>
* <span data-ttu-id="9c5ef-350">[MixedRealityToolkit For Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) 는 대화방 모델을 설정 하는 코드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-350">The [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides code for setting the room model.</span></span>
* <span data-ttu-id="9c5ef-351">혼합 현실 환경에서는 실제 세계 공간에 가장 잘 맞는 방 모델을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-351">For Mixed Reality experiences, select the room model that best fits the real world space.</span></span>

<span data-ttu-id="9c5ef-352">가상 현실 시나리오를 만드는 경우 가상 환경에 가장 잘 맞는 공간 모델을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-352">If you are creating a Virtual Reality scenario, select the room model that best fits the virtual environment.</span></span>

## <a name="chapter-4---sound-design"></a><span data-ttu-id="9c5ef-353">4 장-소리 디자인</span><span class="sxs-lookup"><span data-stu-id="9c5ef-353">Chapter 4 - Sound Design</span></span>

### <a name="objectives"></a><span data-ttu-id="9c5ef-354">목표</span><span class="sxs-lookup"><span data-stu-id="9c5ef-354">Objectives</span></span>

* <span data-ttu-id="9c5ef-355">효과적인 사운드 디자인에 대 한 고려 사항을 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-355">Understand considerations for effective sound design.</span></span>
* <span data-ttu-id="9c5ef-356">기술 및 지침을 혼합 해 보세요.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-356">Learn mixing techniques and guidelines.</span></span>

### <a name="part-1---sound-and-experience-design"></a><span data-ttu-id="9c5ef-357">1 부-소리 및 환경 설계</span><span class="sxs-lookup"><span data-stu-id="9c5ef-357">Part 1 - Sound and Experience Design</span></span>

<span data-ttu-id="9c5ef-358">이 섹션에서는 주요 사운드 및 경험 설계 고려 사항 및 지침을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-358">This section discusses key sound and experience design considerations and guidelines.</span></span>

#### <a name="normalize-all-sounds"></a><span data-ttu-id="9c5ef-359">모든 소리 정규화</span><span class="sxs-lookup"><span data-stu-id="9c5ef-359">Normalize all sounds</span></span>

<span data-ttu-id="9c5ef-360">이렇게 하면 특수 한 사례 코드를 사용 하 여 사운드 당 볼륨 수준을 조정할 필요가 없습니다 .이 경우 시간이 많이 걸리고 소리 파일을 쉽게 업데이트 하는 기능이 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-360">This avoids the need for special case code to adjust volume levels per sound, which can be time consuming and limits the ability to easily update sound files.</span></span>

#### <a name="design-for-an-untethered-experience"></a><span data-ttu-id="9c5ef-361">작업할 환경을 위한 디자인</span><span class="sxs-lookup"><span data-stu-id="9c5ef-361">Design for an untethered experience</span></span>

<span data-ttu-id="9c5ef-362">HoloLens는 완전히 포함 된 작업할 holographic 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-362">HoloLens is a fully contained, untethered holographic computer.</span></span> <span data-ttu-id="9c5ef-363">사용자는 이동 하는 동안 사용자 환경을 사용 하 고 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-363">Your users can and will use your experiences while moving.</span></span> <span data-ttu-id="9c5ef-364">문제를 해결 하 여 오디오 조합을 테스트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-364">Be sure to test your audio mix by walking around.</span></span>

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a><span data-ttu-id="9c5ef-365">Holograms의 논리적 위치에서 소리를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-365">Emit sound from logical locations on your holograms</span></span>

<span data-ttu-id="9c5ef-366">실제 세계에서 강아지는 짖 하지 않으며 사람의 음성은 자신의 집에서 제공 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-366">In the real world, a dog does not bark from its tail and a human's voice does not come from his/her feet.</span></span> <span data-ttu-id="9c5ef-367">Holograms의 예기치 않은 부분 으로부터 사운드가 방출 되는 것을 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-367">Avoid having your sounds emit from unexpected portions of your holograms.</span></span>

<span data-ttu-id="9c5ef-368">작은 holograms 경우 기 하 도형의 중심에서 소리를 내보내는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-368">For small holograms, it is reasonable to have sound emit from the center of the geometry.</span></span>

#### <a name="familiar-sounds-are-most-localizable"></a><span data-ttu-id="9c5ef-369">친숙 한 소리는 가장 지역화 가능 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-369">Familiar sounds are most localizable</span></span>

<span data-ttu-id="9c5ef-370">휴먼 음성 및 음악은 쉽게 지역화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-370">The human voice and music are very easy to localize.</span></span> <span data-ttu-id="9c5ef-371">사용자의 이름을 호출 하는 경우에는 음성의 출처와 거리를 매우 정확 하 게 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-371">If someone calls your name, you are able to very accurately determine from what direction the voice came and from how far away.</span></span> <span data-ttu-id="9c5ef-372">짧고, 익숙하지 않은 소리는 지역화 하기가 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-372">Short, unfamiliar sounds are harder to localize.</span></span>

#### <a name="be-cognizant-of-user-expectations"></a><span data-ttu-id="9c5ef-373">사용자 기대치 cognizant</span><span class="sxs-lookup"><span data-stu-id="9c5ef-373">Be cognizant of user expectations</span></span>

<span data-ttu-id="9c5ef-374">수명 환경은 소리의 위치를 식별 하는 기능을 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-374">Life experience plays a part in our ability to identify the location of a sound.</span></span> <span data-ttu-id="9c5ef-375">이는 휴먼 음성을 특히 쉽게 지역화할 수 있는 한 가지 이유입니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-375">This is one reason why the human voice is particularly easy to localize.</span></span> <span data-ttu-id="9c5ef-376">소리를 넣을 때 사용자의 학습 된 기대치를 파악 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-376">It is important to be aware of your user's learned expectations when placing your sounds.</span></span>

<span data-ttu-id="9c5ef-377">예를 들어 사용자가 bird 노래를 듣게 되 면 일반적으로는 거리가 시야 (비행 또는 트리)를 초과 하는 경향이 있으므로 일반적으로 조회 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-377">For example, when someone hears a bird song they generally look up, as birds tend to be above the line of sight (flying or in a tree).</span></span> <span data-ttu-id="9c5ef-378">사용자가 소리의 올바른 방향을 설정 하는 것이 일반적이 지 않지만 잘못 된 세로 방향을 확인 하 여 홀로그램을 찾을 수 없는 경우 혼동 또는 실망 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-378">It is not uncommon for a user to turn in the correct direction of a sound, but look in the wrong vertical direction and become confused or frustrated when they are unable to find the hologram.</span></span>

#### <a name="avoid-hidden-emitters"></a><span data-ttu-id="9c5ef-379">숨겨진 송신기 방지</span><span class="sxs-lookup"><span data-stu-id="9c5ef-379">Avoid hidden emitters</span></span>

<span data-ttu-id="9c5ef-380">실제 세계에서 소리가 들리면 일반적으로 소리를 내보내는 개체를 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-380">In the real world, if we hear a sound, we can generally identify the object that is emitting the sound.</span></span> <span data-ttu-id="9c5ef-381">사용자 환경 에서도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-381">This should also hold true in your experiences.</span></span> <span data-ttu-id="9c5ef-382">사용자가 소리를 disconcerting 소리를 듣고 개체가 표시 되지 않도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-382">It can be very disconcerting for users to hear a sound, know from where the sound originates and be unable to see an object.</span></span>

<span data-ttu-id="9c5ef-383">이 지침에는 몇 가지 예외가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-383">There are some exceptions to this guideline.</span></span> <span data-ttu-id="9c5ef-384">예를 들어 필드의 crickets와 같은 앰비언트 소리는 표시 하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-384">For example, ambient sounds such as crickets in a field need not be visible.</span></span> <span data-ttu-id="9c5ef-385">수명 경험을 통해 이러한 소리의 출처를 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-385">Life experience gives us familiarity with the source of these sounds without the need to see it.</span></span>

### <a name="part-2---sound-mixing"></a><span data-ttu-id="9c5ef-386">2 부-소리 믹싱</span><span class="sxs-lookup"><span data-stu-id="9c5ef-386">Part 2 - Sound Mixing</span></span>

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a><span data-ttu-id="9c5ef-387">HoloLens의 70% 볼륨에 대 한 조합 대상</span><span class="sxs-lookup"><span data-stu-id="9c5ef-387">Target your mix for 70% volume on the HoloLens</span></span>

<span data-ttu-id="9c5ef-388">혼합 현실 환경에서는 holograms를 실제 환경에서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-388">Mixed Reality experiences allow holograms to be seen in the real world.</span></span> <span data-ttu-id="9c5ef-389">또한 실제 소리를 듣지 못하게 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-389">They should also allow real world sounds to be heard.</span></span> <span data-ttu-id="9c5ef-390">사용자는 70% 볼륨 대상을 사용 하 여 사용자 환경의 소리와 함께 전 세계를 들를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-390">A 70% volume target enables the user to hear the world around them along with the sound of your experience.</span></span>

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a><span data-ttu-id="9c5ef-391">HoloLens 100% 볼륨이 외부 소리를 drown 함</span><span class="sxs-lookup"><span data-stu-id="9c5ef-391">HoloLens at 100% volume should drown out external sounds</span></span>

<span data-ttu-id="9c5ef-392">100%의 볼륨 수준은 가상 현실 환경과 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-392">A volume level of 100% is akin to a Virtual Reality experience.</span></span> <span data-ttu-id="9c5ef-393">시각적으로 사용자를 다른 지역으로 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-393">Visually, the user is transported to a different world.</span></span> <span data-ttu-id="9c5ef-394">동일 하 게 true 통화을 유지 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-394">The same should hold true audibly.</span></span>

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a><span data-ttu-id="9c5ef-395">Unity 오디오 믹서를 사용 하 여 소리 범주 조정</span><span class="sxs-lookup"><span data-stu-id="9c5ef-395">Use the Unity AudioMixer to adjust categories of sounds</span></span>

<span data-ttu-id="9c5ef-396">혼합을 디자인할 때 소리 범주를 만들고 해당 볼륨을 하나의 단위로 늘리거나 줄일 수 있는 기능을 제공 하는 것이 도움이 되는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-396">When designing your mix, it is often helpful to create sound categories and have the ability to increase or decrease their volume as a unit.</span></span> <span data-ttu-id="9c5ef-397">이렇게 하면 전체 조합을 빠르게 변경 하는 동시에 각 소리의 상대적 수준이 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-397">This retains the relative levels of each sound while enabling quick and easy changes to the overall mix.</span></span> <span data-ttu-id="9c5ef-398">일반적인 범주는 다음과 같습니다. 음향 효과, 외계, 음성 failover)가 및 배경 음악</span><span class="sxs-lookup"><span data-stu-id="9c5ef-398">Common categories include; sound effects, ambience, voice overs and background music.</span></span>

#### <a name="mix-sounds-based-on-the-users-gaze"></a><span data-ttu-id="9c5ef-399">사용자의 응시에 따라 소리 혼합</span><span class="sxs-lookup"><span data-stu-id="9c5ef-399">Mix sounds based on the user's gaze</span></span>

<span data-ttu-id="9c5ef-400">사용자의 위치에 따라 사용자 환경에서 사운드 조합을 변경 하는 것이 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-400">It can often be useful to change the sound mix in your experience based on where a user is (or is not) looking.</span></span> <span data-ttu-id="9c5ef-401">이 기법은 일반적으로 Holographic 프레임 외부에 있는 holograms의 볼륨 수준을 줄여 사용자가 앞의 정보에 더 쉽게 집중할 수 있도록 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-401">One common use for this technique are to reduce the volume level for holograms that are outside of the Holographic Frame to make it easier for the user to focus on the information in front of them.</span></span> <span data-ttu-id="9c5ef-402">또 다른 용도는 중요 한 이벤트에 사용자의 주의가 필요한 소리의 볼륨을 늘리는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-402">Another use is to increase the volume of a sound to draw the user's attention to an important event.</span></span>

#### <a name="building-your-mix"></a><span data-ttu-id="9c5ef-403">조합 빌드</span><span class="sxs-lookup"><span data-stu-id="9c5ef-403">Building your mix</span></span>

<span data-ttu-id="9c5ef-404">조합을 빌드할 때 경험의 배경 오디오로 시작 하 고 중요도에 따라 레이어를 추가 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-404">When building your mix, it is recommended to start with your experience's background audio and add layers based on importance.</span></span> <span data-ttu-id="9c5ef-405">일반적으로 각 계층이 이전 보다 크게 크게 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-405">Often, this results in each layer being louder than the previous.</span></span>

<span data-ttu-id="9c5ef-406">가장 중요 하지 않은 (일반적으로 quietest 소리) 아래쪽에 있는 반전 된 깔때기로 혼합을 발견 다음 다이어그램과 유사한 조합을 구성 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-406">Imagining your mix as an inverted funnel, with the least important (and generally quietest sounds) at the bottom, it is recommended to structure your mix similar to the following diagram.</span></span>

![사운드 조합 구조](images/soundlevels.png)

<span data-ttu-id="9c5ef-408">음성 failover)가은 흥미로운 시나리오입니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-408">Voice overs are an interesting scenario.</span></span> <span data-ttu-id="9c5ef-409">만드는 환경에 따라 스테레오 (지역화 되지 않음) 사운드가 나 음성 failover)가을 spatialize 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-409">Based on the experience you are creating you may wish to have a stereo (not localized) sound or to spatialize your voice overs.</span></span> <span data-ttu-id="9c5ef-410">Microsoft에서 게시 한 두 가지 환경에서는 각 시나리오의 뛰어난 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-410">Two Microsoft published experiences illustrate excellent examples of each scenario.</span></span>

<span data-ttu-id="9c5ef-411">[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87) 는 스테레오 음성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-411">[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87) uses a stereo voice over.</span></span> <span data-ttu-id="9c5ef-412">내레이터가 표시 되는 위치를 설명 하는 경우 소리는 일관적 이며 사용자의 위치에 따라 달라 지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-412">When the narrator is describing the location being viewed, the sound is consistent and does not vary based on the user's position.</span></span> <span data-ttu-id="9c5ef-413">이렇게 하면 내레이터가 환경의 spatialized 소리를 벗어나지 않고 장면을 설명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-413">This enables the narrator to describe the scene without taking away from the spatialized sounds of the environment.</span></span>

<span data-ttu-id="9c5ef-414">[조각은](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) 감지 형식의 spatialized 음성을 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-414">[Fragments](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utilizes a spatialized voice over in the form of a detective.</span></span> <span data-ttu-id="9c5ef-415">감지의 음성은 실제 사람이 대화방에 있는 것 처럼 중요 한 단서를 사용자에 게 전달 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-415">The detective's voice is used to help bring the user's attention to an important clue as if an actual human was in the room.</span></span> <span data-ttu-id="9c5ef-416">이를 통해 집중 교육을 더 잘 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-416">This enables an even greater sense of immersion into the experience of solving the mystery.</span></span>

### <a name="part-3--performance"></a><span data-ttu-id="9c5ef-417">3 부-성능</span><span class="sxs-lookup"><span data-stu-id="9c5ef-417">Part 3 -Performance</span></span>

#### <a name="cpu-usage"></a><span data-ttu-id="9c5ef-418">CPU 사용량</span><span class="sxs-lookup"><span data-stu-id="9c5ef-418">CPU usage</span></span>

<span data-ttu-id="9c5ef-419">공간 사운드를 사용 하는 경우 10-12는 CPU의 약 12%를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-419">When using Spatial Sound, 10 - 12 emitters will consume approximately 12% of the CPU.</span></span>

#### <a name="stream-long-audio-files"></a><span data-ttu-id="9c5ef-420">긴 오디오 파일 스트림</span><span class="sxs-lookup"><span data-stu-id="9c5ef-420">Stream long audio files</span></span>

<span data-ttu-id="9c5ef-421">오디오 데이터는 특히 일반적인 샘플 요금 (44.1 및 48 kHz)에서 클 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-421">Audio data can be large, especially at common sample rates (44.1 and 48 kHz).</span></span> <span data-ttu-id="9c5ef-422">일반적인 규칙은 응용 프로그램 메모리 사용을 줄이기 위해 5-10 초 보다 긴 오디오 파일을 스트리밍하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-422">A general rule is that audio files longer than 5 - 10 seconds should be streamed to reduce application memory usage.</span></span>

<span data-ttu-id="9c5ef-423">Unity에서는 파일의 가져오기 설정에서 스트리밍을 위해 오디오 파일을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-423">In Unity, you can mark an audio file for streaming in the file's import settings.</span></span>

![오디오 가져오기 설정](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a><span data-ttu-id="9c5ef-425">5 장-특수 효과</span><span class="sxs-lookup"><span data-stu-id="9c5ef-425">Chapter 5 - Special Effects</span></span>

### <a name="objectives"></a><span data-ttu-id="9c5ef-426">목표</span><span class="sxs-lookup"><span data-stu-id="9c5ef-426">Objectives</span></span>

* <span data-ttu-id="9c5ef-427">"Magic Windows"에 깊이를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-427">Add depth to "Magic Windows".</span></span>
* <span data-ttu-id="9c5ef-428">사용자를 가상 세계에 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-428">Bring the user into the virtual world.</span></span>

### <a name="magic-windows"></a><span data-ttu-id="9c5ef-429">매직 창</span><span class="sxs-lookup"><span data-stu-id="9c5ef-429">Magic Windows</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="9c5ef-430">주요 개념</span><span class="sxs-lookup"><span data-stu-id="9c5ef-430">Key Concepts</span></span>

* <span data-ttu-id="9c5ef-431">숨겨진 세계에 뷰를 만들면 시각적으로 매력적인 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-431">Creating views into a hidden world, is visually compelling.</span></span>
* <span data-ttu-id="9c5ef-432">홀로그램 또는 사용자가 숨겨진 세계 가까이 있을 때 오디오 효과를 추가 하 여 현실감을 향상 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-432">Enhance realism by adding audio effects when a hologram or the user is near the hidden world.</span></span>

#### <a name="instructions"></a><span data-ttu-id="9c5ef-433">지침</span><span class="sxs-lookup"><span data-stu-id="9c5ef-433">Instructions</span></span>

* <span data-ttu-id="9c5ef-434">**계층** 패널에서 **HologramCollection** 를 확장 하 고 지 각 **를 선택 합니다**.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-434">In the **Hierarchy** panel, expand **HologramCollection** and select **Underworld**.</span></span>
* <span data-ttu-id="9c5ef-435">지 각 **를 확장 하** 고 **VoiceSource**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-435">Expand **Underworld** and select **VoiceSource**.</span></span>
* <span data-ttu-id="9c5ef-436">**검사기** 패널에서 **구성 요소 추가** 를 클릭 하 고 **사용자 음성 효과**를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-436">In the **Inspector** panel, click **Add Component** and add **User Voice Effect**.</span></span>

<span data-ttu-id="9c5ef-437">**VoiceSource**에 **오디오 원본** 구성 요소가 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-437">An **AudioSource** component will be added to **VoiceSource**.</span></span>

* <span data-ttu-id="9c5ef-438">**오디오 원본**에서 **출력** 을 **UserVoice (혼합기)** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-438">In **AudioSource**, set **Output** to **UserVoice (Mixer)**.</span></span>
* <span data-ttu-id="9c5ef-439">**Spatialize** 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-439">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="9c5ef-440">**공간 Blend** 슬라이더를 **3d**로 끌어 놓거나 편집 상자에 **1** 을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-440">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>
* <span data-ttu-id="9c5ef-441">**3D 소리 설정**을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-441">Expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="9c5ef-442">**Doppler Level** 을 **0**으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-442">Set **Doppler Level** to **0**.</span></span>
* <span data-ttu-id="9c5ef-443">**사용자 음성 효과**에서 **부모 개체** 를 장면의 지 수  로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-443">In **User Voice Effect**, set **Parent Object** to the **Underworld** from the scene.</span></span>
* <span data-ttu-id="9c5ef-444">**최대 거리** 를 **1**로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-444">Set **Max Distance** to **1**.</span></span>

<span data-ttu-id="9c5ef-445">**최대 거리** 를 설정 하면 효과를 사용 하도록 설정 하기 전에 사용자에 게 부모 개체에 대 한 사용자 **음성 효과** 를 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-445">Setting **Max Distance** tells **User Voice Effect** how close the user must be to the parent object before the effect is enabled.</span></span>

* <span data-ttu-id="9c5ef-446">**사용자 음성 효과**에서 **코러스 매개 변수**를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-446">In **User Voice Effect**, expand **Chorus Parameters**.</span></span>
* <span data-ttu-id="9c5ef-447">**깊이** 를 **0.1**으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-447">Set **Depth** to **0.1**.</span></span>
* <span data-ttu-id="9c5ef-448">**탭 1 볼륨**을 설정 하 고 **2 볼륨을 탭** 한 다음 **볼륨 3** 개를 **0.8**으로 탭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-448">Set **Tap 1 Volume**, **Tap 2 Volume** and **Tap 3 Volume** to **0.8**.</span></span>
* <span data-ttu-id="9c5ef-449">**원본 사운드 볼륨** 을 **0.5**으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-449">Set **Original Sound Volume** to **0.5**.</span></span>

<span data-ttu-id="9c5ef-450">이전 설정은 사용자의 음성에 다양 한 다양성을 추가 하는 데 사용 되는 Unity **AudioChorusFilter** 의 매개 변수를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-450">The previous settings configure the parameters of the Unity **AudioChorusFilter** used to add richness to the user's voice.</span></span>

* <span data-ttu-id="9c5ef-451">**사용자 음성 효과**에서 **Echo 매개 변수**를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-451">In **User Voice Effect**, expand **Echo Parameters**.</span></span>
* <span data-ttu-id="9c5ef-452">**지연 시간** 을 **300** 으로 설정</span><span class="sxs-lookup"><span data-stu-id="9c5ef-452">Set **Delay** to **300**</span></span>
* <span data-ttu-id="9c5ef-453">**감소 비율** 을 **0.2**로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-453">Set **Decay Ratio** to **0.2**.</span></span>
* <span data-ttu-id="9c5ef-454">**원래 사운드 볼륨** 을 **0**으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-454">Set **Original Sound Volume** to **0**.</span></span>

<span data-ttu-id="9c5ef-455">이전 설정은 사용자의 음성 에코를 발생 시키는 데 사용 되는 Unity **AudioEchoFilter** 의 매개 변수를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-455">The previous settings configure the parameters of the Unity **AudioEchoFilter** used to cause the user's voice to echo.</span></span>

<span data-ttu-id="9c5ef-456">사용자 음성 효과 스크립트는 다음을 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-456">The User Voice Effect script is responsible for:</span></span>

* <span data-ttu-id="9c5ef-457">사용자와 스크립트가 연결 된 **GameObject** 간의 거리를 측정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-457">Measuring the distance between the user and the **GameObject** to which the script is attached.</span></span>
* <span data-ttu-id="9c5ef-458">사용자가 **GameObject**를 연결 하는지 여부를 확인 하는 중입니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-458">Determining whether or not the user is facing the **GameObject**.</span></span>

<span data-ttu-id="9c5ef-459">효과를 사용 하도록 설정 하려면 거리에 관계 없이 사용자가 GameObject 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-459">The user must be facing the GameObject, regardless of distance, for the effect to be enabled.</span></span>

* <span data-ttu-id="9c5ef-460">**AudioChorusFilter** 및 **AudioEchoFilter** 를 **오디오 소스**에 적용 하 고 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-460">Applying and configuring an **AudioChorusFilter** and an **AudioEchoFilter** to the **AudioSource**.</span></span>
* <span data-ttu-id="9c5ef-461">필터를 사용 하지 않도록 설정 하 여 효과를 비활성화 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-461">Disabling the effect by disabling the filters.</span></span>

<span data-ttu-id="9c5ef-462">사용자 음성 효과는 [MixedRealityToolkit For unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)에서 Mic 스트림 선택기 구성 요소를 사용 하 여 고품질의 음성 스트림을 선택 하 고 Unity의 오디오 시스템으로 라우팅합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-462">User Voice Effect uses the Mic Stream Selector component, from the [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), to select the high quality voice stream and route it into Unity's audio system.</span></span>

* <span data-ttu-id="9c5ef-463">**계층** 패널에서 **관리자**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-463">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="9c5ef-464">**검사기** 패널에서 **Speech Input Handler**를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-464">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="9c5ef-465">**음성 입력 처리기**에서 지 이상 **표시**를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-465">In **Speech Input Handler**, expand **Show Underworld**.</span></span>
* <span data-ttu-id="9c5ef-466">**No 함수** 를 UnderworldBase로 변경 합니다 **.**</span><span class="sxs-lookup"><span data-stu-id="9c5ef-466">Change **No Function** to **UnderworldBase.OnEnable**.</span></span>

![키워드로 지 각 표시](images/showunderworld.png)

* <span data-ttu-id="9c5ef-468">지 각 **지를 확장**합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-468">Expand **Hide Underworld**.</span></span>
* <span data-ttu-id="9c5ef-469">UnderworldBase **함수** 를 변경 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-469">Change **No Function** to **UnderworldBase.OnDisable**.</span></span>

![키워드로 지 각 숨기기](images/hideunderworld.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="9c5ef-471">빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="9c5ef-471">Build and Deploy</span></span>

* <span data-ttu-id="9c5ef-472">이전과 마찬가지로 Unity에서 프로젝트를 빌드하고 Visual Studio에서 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-472">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="9c5ef-473">응용 프로그램을 배포한 후:</span><span class="sxs-lookup"><span data-stu-id="9c5ef-473">After the application is deployed:</span></span>

* <span data-ttu-id="9c5ef-474">표면 (벽, 바닥, 테이블)을 표면에 표시 하 고 "지 각"을 *표시*합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-474">Face a surface (wall, floor, table) and say *"Show Underworld"*.</span></span>

<span data-ttu-id="9c5ef-475">지 수를 표시 하 고 다른 모든 holograms를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-475">The underworld will be shown and all other holograms will be hidden.</span></span> <span data-ttu-id="9c5ef-476">지 수가 표시 되지 않으면 실제 화면을 향하고 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-476">If you do not see the underworld, ensure that you are facing a real-world surface.</span></span>

* <span data-ttu-id="9c5ef-477">1 미터 내에서의 접근 방식으로 통신을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-477">Approach within 1 meter of the underworld hologram and start talking.</span></span>

<span data-ttu-id="9c5ef-478">이제 오디오 효과가 음성에 적용 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-478">There are now audio effects applied to your voice!</span></span>

* <span data-ttu-id="9c5ef-479">지 수를 끄고 효과가 더 이상 적용 되지 않는 방식을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-479">Turn away from the underworld and notice how the effect is no longer applied.</span></span>
* <span data-ttu-id="9c5ef-480">지 수를 숨기려면 "지 수 *숨기기"* 라고 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-480">Say *"Hide Underworld"* to hide the underworld.</span></span>

<span data-ttu-id="9c5ef-481">지 수는 숨겨지고 이전에 숨겨진 holograms 다시 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-481">The underworld will be hidden and the previously hidden holograms will reappear.</span></span>

## <a name="the-end"></a><span data-ttu-id="9c5ef-482">끝</span><span class="sxs-lookup"><span data-stu-id="9c5ef-482">The End</span></span>

<span data-ttu-id="9c5ef-483">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-483">Congratulations!</span></span> <span data-ttu-id="9c5ef-484">이제 MR 공간 220 **을 완료 했습니다. 공간 사운드**.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-484">You have now completed **MR Spatial 220: Spatial sound**.</span></span>

<span data-ttu-id="9c5ef-485">세계를 듣고 경험을 바탕으로 경험을 해보세요.</span><span class="sxs-lookup"><span data-stu-id="9c5ef-485">Listen to the world and bring your experiences to life with sound!</span></span>
