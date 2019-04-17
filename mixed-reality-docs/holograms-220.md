---
title: MR 공간 220-공간 소리
description: Unity에서 Visual Studio 및 HoloLens를 사용 하 여 공간 사운드 개념의 세부 정보를 알아보려면이 코딩 연습을 수행 합니다.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit mixedrealitytoolkit, mixedrealitytoolkit unity, academy, 자습서, 공간 소리
ms.openlocfilehash: 50d17fe8c9a6e3f18b1309a59c9c41af982a7505
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599015"
---
>[!NOTE]
><span data-ttu-id="a5793-104">혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="a5793-105">따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="a5793-106">이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="a5793-107">지원 되는 장치에서 작업을 계속 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="a5793-108">새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="a5793-109">게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-spatial-220-spatial-sound"></a><span data-ttu-id="a5793-110">MR 공간 220: 공간 음향</span><span class="sxs-lookup"><span data-stu-id="a5793-110">MR Spatial 220: Spatial sound</span></span>

<span data-ttu-id="a5793-111">[공간 소리](spatial-sound.md) 홀로그램으로 수명 살아 있 소 및 세계의 현재 상태를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-111">[Spatial sound](spatial-sound.md) breathes life into holograms and gives them presence in our world.</span></span> <span data-ttu-id="a5793-112">Light와 소리를 홀로그램으로 구성 됩니다 하 고 여 홀로그램 놓치 있다면 공간 소리를 찾을 수 있도록 하 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-112">Holograms are composed of both light and sound, and if you happen to lose sight of your holograms, spatial sound can help you find them.</span></span> <span data-ttu-id="a5793-113">소리 공간 유사 하지 않음에 라디오 듣기는 일반적인 소리를 3D 공간에 배치 되는 소리를 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-113">Spatial sound is not like the typical sound that you would hear on the radio, it is sound that is positioned in 3D space.</span></span> <span data-ttu-id="a5793-114">공간 소리를 사용 하 여 할 수 있습니다 홀로그램, 옆 또는 머리에도 백그라운드에서 만든 것 처럼 사운드!</span><span class="sxs-lookup"><span data-stu-id="a5793-114">With spatial sound, you can make holograms sound like they're behind you, next to you, or even on your head!</span></span> <span data-ttu-id="a5793-115">이 과정에서는 다음을 수행 해야합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-115">In this course, you will:</span></span>

* <span data-ttu-id="a5793-116">Microsoft 공간 소리를 사용 하도록 개발 환경을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-116">Configure your development environment to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="a5793-117">상호 작용을 향상 시키기 위해 공간 소리를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-117">Use Spatial Sound to enhance interactions.</span></span>
* <span data-ttu-id="a5793-118">공간 매핑 함께에서 공간 소리를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-118">Use Spatial Sound in conjunction with Spatial Mapping.</span></span>
* <span data-ttu-id="a5793-119">적절 하 게 디자인 하 고 혼합 모범 사례를 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-119">Understand sound design and mixing best practices.</span></span>
* <span data-ttu-id="a5793-120">소리를 사용 하 여 혼합 현실 세계에 사용자를 특수 효과 향상 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-120">Use sound to enhance special effects and bring the user into the Mixed Reality world.</span></span>

## <a name="device-support"></a><span data-ttu-id="a5793-121">장치 지원</span><span class="sxs-lookup"><span data-stu-id="a5793-121">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="a5793-122">과정</span><span class="sxs-lookup"><span data-stu-id="a5793-122">Course</span></span></th><th style="width:150px"> <span data-ttu-id="a5793-123"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="a5793-123"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="a5793-124"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="a5793-124"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="a5793-125">MR 공간 220: 공간 음향</span><span class="sxs-lookup"><span data-stu-id="a5793-125">MR Spatial 220: Spatial sound</span></span></td><td style="text-align: center;"> <span data-ttu-id="a5793-126">✔️</span><span class="sxs-lookup"><span data-stu-id="a5793-126">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="a5793-127">✔️</span><span class="sxs-lookup"><span data-stu-id="a5793-127">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="a5793-128">시작하기 전 주의 사항</span><span class="sxs-lookup"><span data-stu-id="a5793-128">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="a5793-129">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="a5793-129">Prerequisites</span></span>

* <span data-ttu-id="a5793-130">올바른를 사용 하 여 구성 하는 Windows 10 PC [도구가 설치 되어](install-the-tools.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-130">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="a5793-131">기본적인 C# 기능을 프로그래밍 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-131">Some basic C# programming ability.</span></span>
* <span data-ttu-id="a5793-132">완료 해야 [MR 기본 사항 101](holograms-101.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-132">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="a5793-133">HoloLens 장치 [개발에 대해 구성 된](using-visual-studio.md#enabling-developer-mode)합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-133">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="a5793-134">프로젝트 파일</span><span class="sxs-lookup"><span data-stu-id="a5793-134">Project files</span></span>

* <span data-ttu-id="a5793-135">다운로드 합니다 [파일](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) 프로젝트에서 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-135">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) required by the project.</span></span><span data-ttu-id="a5793-136"> Unity 2017.2 이상이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-136"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="a5793-137">Unity 5.6 지원이 계속 필요한 경우 사용 하세요 [이 릴리스에서](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip)합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-137">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span></span> <span data-ttu-id="a5793-138">이 릴리스에서 더 이상 최신 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-138">This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="a5793-139">Unity 5.5 지원 해야 하는 경우 사용 하세요 [이 릴리스에서](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip)합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-139">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span></span><span data-ttu-id="a5793-140"> 이 릴리스에서 더 이상 최신 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-140"> This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="a5793-141">Unity 5.4 지원이 계속 필요한 경우 사용 하세요 [이 릴리스에서](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip)합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-141">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span></span><span data-ttu-id="a5793-142"> 이 릴리스에서 더 이상 최신 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-142"> This release may no longer be up-to-date.</span></span>
* <span data-ttu-id="a5793-143">취소 보관 파일을 데스크톱 또는 기타 쉽게 달성할 수 있습니다 위치 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-143">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="a5793-144">을 다운로드 하기 전에 소스 코드를 확인 하려는 경우 있기 [GitHub에서 사용할 수 있는](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound)합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-144">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="a5793-145">오류 및 정보</span><span class="sxs-lookup"><span data-stu-id="a5793-145">Errata and Notes</span></span>

* <span data-ttu-id="a5793-146">사용 하지 않도록 설정할 필요 "내 코드만 사용" (*unchecked*)-> 도구 아래에서 Visual Studio에서 코드에서 중단점을 적중 하려면-> 디버깅 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-146">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="a5793-147">1 장-Unity 설치</span><span class="sxs-lookup"><span data-stu-id="a5793-147">Chapter 1 - Unity Setup</span></span>

### <a name="objectives"></a><span data-ttu-id="a5793-148">목표</span><span class="sxs-lookup"><span data-stu-id="a5793-148">Objectives</span></span>

* <span data-ttu-id="a5793-149">Unity의 사운드 Microsoft 공간 소리를 사용 하 여 구성을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-149">Change Unity's sound configuration to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="a5793-150">개체에 Unity 3D 소리를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-150">Add 3D sound to an object in Unity.</span></span>

### <a name="instructions"></a><span data-ttu-id="a5793-151">지침</span><span class="sxs-lookup"><span data-stu-id="a5793-151">Instructions</span></span>

* <span data-ttu-id="a5793-152">Unity를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-152">Start Unity.</span></span>
* <span data-ttu-id="a5793-153">선택 **열려**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-153">Select **Open**.</span></span>
* <span data-ttu-id="a5793-154">이동할 바탕 화면과 폴더 찾기 되지 않은 보관 된 이전에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-154">Navigate to your Desktop and find the folder you previously un-archived.</span></span>
* <span data-ttu-id="a5793-155">클릭 합니다 **Starting\Decibel** 폴더 및 다음 키를 **폴더 선택** 단추.</span><span class="sxs-lookup"><span data-stu-id="a5793-155">Click on the **Starting\Decibel** folder and then press the **Select Folder** button.</span></span>
* <span data-ttu-id="a5793-156">프로젝트가 Unity에서 로드 될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-156">Wait for the project to load in Unity.</span></span>
* <span data-ttu-id="a5793-157">에 **프로젝트** 패널 열기 **Scenes\Decibel.unity**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-157">In the **Project** panel, open **Scenes\Decibel.unity**.</span></span>
* <span data-ttu-id="a5793-158">에 **계층 구조** 패널에서 확장 **HologramCollection** 선택한 **P0LY**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-158">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="a5793-159">[관리자]에서 확장 **AudioSource** 있다는 것을 확인 하지 **Spatialize** 확인란 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-159">In the Inspector, expand **AudioSource** and notice that there is no **Spatialize** check box.</span></span>

<span data-ttu-id="a5793-160">기본적으로 Unity 입체 음향 플러그 인을 로드 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-160">By default, Unity does not load a spatializer plugin.</span></span> <span data-ttu-id="a5793-161">다음 단계를 프로젝트에서 공간 소리를 사용 하도록 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-161">The following steps will enable Spatial Sound in the project.</span></span>

* <span data-ttu-id="a5793-162">Unity의 위쪽 메뉴에서로 이동 **편집 > 프로젝트 설정 > 오디오**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-162">In Unity's top menu, go to **Edit > Project Settings > Audio**.</span></span>
* <span data-ttu-id="a5793-163">찾을 합니다 **입체 음향 플러그 인** 드롭다운에서 선택한 **MS HRTF 입체 음향**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-163">Find the **Spatializer Plugin** dropdown, and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="a5793-164">에 **계층 구조** 패널에서 **HologramCollection > P0LY**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-164">In the **Hierarchy** panel, select **HologramCollection > P0LY**.</span></span>
* <span data-ttu-id="a5793-165">에 **검사기** 패널에서 찾을 합니다 **오디오 원본** 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-165">In the **Inspector** panel, find the **Audio Source** component.</span></span>
* <span data-ttu-id="a5793-166">확인 합니다 **Spatialize** 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-166">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="a5793-167">끌어서를 **공간 Blend** 슬라이더에 이르는 **3D**, 또는 입력 **1** 편집 상자에서.</span><span class="sxs-lookup"><span data-stu-id="a5793-167">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>

<span data-ttu-id="a5793-168">이제 Unity에서 프로젝트 빌드를 Visual Studio에서 솔루션을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-168">We will now build the project in Unity and configure the solution in Visual Studio.</span></span>

1. <span data-ttu-id="a5793-169">Unity에서 선택 **파일 > 빌드 설정**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-169">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="a5793-170">클릭 **열기 장면 추가** 장면에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-170">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="a5793-171">선택 **유니버설 Windows 플랫폼** 에 **플랫폼** 클릭 **플랫폼 전환**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-171">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="a5793-172">HoloLens에 대 한 구체적으로 개발 하는 경우 설정 **대상 장치** 하 **HoloLens**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-172">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="a5793-173">그렇지 않으면 켜져 **모든 장치**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-173">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="a5793-174">확인 **빌드 형식** 로 설정 된 **D3D** 하 고 **SDK** 로 설정 되어 **가장 최근에 설치 된** (16299 또는 최신 SDK는 이어야 함).</span><span class="sxs-lookup"><span data-stu-id="a5793-174">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="a5793-175">**빌드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-175">Click **Build**.</span></span>
7. <span data-ttu-id="a5793-176">만들기는 **새 폴더** 이름을 "App"입니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-176">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="a5793-177">한 번 클릭 합니다 **앱** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-177">Single click the **App** folder.</span></span>
9. <span data-ttu-id="a5793-178">키를 눌러 **폴더 선택**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-178">Press **Select Folder**.</span></span>

<span data-ttu-id="a5793-179">Unity 완료 되 면 파일 탐색기 창이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-179">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="a5793-180">엽니다는 **앱** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-180">Open the **App** folder.</span></span>
2. <span data-ttu-id="a5793-181">엽니다는 **데시벨 Visual Studio 솔루션**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-181">Open the **Decibel Visual Studio Solution**.</span></span>

<span data-ttu-id="a5793-182">HoloLens 배포 하는 경우:</span><span class="sxs-lookup"><span data-stu-id="a5793-182">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="a5793-183">에 디버그 대상 변경 맨 위의 도구 모음을 사용 하 여 Visual Studio에서 **릴리스** 들어오고를 ARM **x86**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-183">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="a5793-184">드롭다운 로컬 컴퓨터 단추 옆의 화살표를 클릭 하 고 선택 **원격 컴퓨터**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-184">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="a5793-185">입력 **HoloLens 장치 IP 주소** 인증 모드를 설정 하 고 **유니버설 (암호화 되지 않은 프로토콜)** 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-185">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="a5793-186">클릭 **선택**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-186">Click **Select**.</span></span> <span data-ttu-id="a5793-187">장치 IP 주소를 모르는 경우 찾는 위치 **설정 > 네트워크 및 인터넷 > 고급 옵션**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-187">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="a5793-188">맨 위 메뉴 모음에서 클릭 **디버그-> 디버깅 없이 시작** 누르거나 **ctrl+f5**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-188">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="a5793-189">처음으로 장치에 배포할 경우 해야 [Visual Studio를 사용 하 여 쌍](using-visual-studio.md#pairing-your-device---hololens-1st-gen)합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-189">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device---hololens-1st-gen).</span></span>

<span data-ttu-id="a5793-190">경우는 몰입 형 헤드셋에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-190">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="a5793-191">에 디버그 대상 변경 맨 위의 도구 모음을 사용 하 여 Visual Studio에서 **릴리스** 들어오고를 ARM **x64**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-191">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="a5793-192">배포 대상 설정 되어 있는지 확인 **로컬 컴퓨터**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-192">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="a5793-193">맨 위 메뉴 모음에서 클릭 **디버그-> 디버깅 없이 시작** 누르거나 **ctrl+f5**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-193">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>

## <a name="chapter-2---spatial-sound-and-interaction"></a><span data-ttu-id="a5793-194">2 장-공간 소리 및 상호 작용</span><span class="sxs-lookup"><span data-stu-id="a5793-194">Chapter 2 - Spatial Sound and Interaction</span></span>

### <a name="objectives"></a><span data-ttu-id="a5793-195">목표</span><span class="sxs-lookup"><span data-stu-id="a5793-195">Objectives</span></span>

* <span data-ttu-id="a5793-196">소리를 사용 하 여 홀로그램 현실성을 향상 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-196">Enhance hologram realism using sound.</span></span>
* <span data-ttu-id="a5793-197">소리를 사용 하 여 사용자의 게이즈를 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-197">Direct the user's gaze using sound.</span></span>
* <span data-ttu-id="a5793-198">소리를 사용 하 여 제스처 피드백을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-198">Provide gesture feedback using sound.</span></span>

### <a name="part-1---enhancing-realism"></a><span data-ttu-id="a5793-199">1 부-현실성 향상</span><span class="sxs-lookup"><span data-stu-id="a5793-199">Part 1 - Enhancing Realism</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="a5793-200">주요 개념</span><span class="sxs-lookup"><span data-stu-id="a5793-200">Key Concepts</span></span>

* <span data-ttu-id="a5793-201">홀로그램 소리 spatialize 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-201">Spatialize hologram sounds.</span></span>
* <span data-ttu-id="a5793-202">사운드 소스를 홀로그램의 적절 한 위치에 배치 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-202">Sound sources should be placed at an appropriate location on the hologram.</span></span>

<span data-ttu-id="a5793-203">소리에 대 한 적절 한 위치를 홀로그램 종속 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-203">The appropriate location for the sound is going to depend on the hologram.</span></span> <span data-ttu-id="a5793-204">예를 들어를 홀로그램 사람이 인 경우 사운드 원본 입 및 feet 없습니다 근처에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-204">For example, if the hologram is of a human, the sound source should be located near the mouth and not the feet.</span></span>

#### <a name="instructions"></a><span data-ttu-id="a5793-205">지침</span><span class="sxs-lookup"><span data-stu-id="a5793-205">Instructions</span></span>

<span data-ttu-id="a5793-206">다음 지침을 홀로그램 spatialized 소리를 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-206">The following instructions will attach a spatialized sound to a hologram.</span></span>

* <span data-ttu-id="a5793-207">에 **계층 구조** 패널에서 확장 **HologramCollection** 선택한 **P0LY**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-207">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="a5793-208">에 **검사기** 패널의 **AudioSource**, 옆에 원을 클릭 **AudioClip** 선택한 **PolyHover** 팝업에서.</span><span class="sxs-lookup"><span data-stu-id="a5793-208">In the **Inspector** panel, in the **AudioSource**, click the circle next to **AudioClip** and select **PolyHover** from the pop-up.</span></span>
* <span data-ttu-id="a5793-209">옆에 원을 클릭 **출력** 선택한 **SoundEffects** 팝업에서.</span><span class="sxs-lookup"><span data-stu-id="a5793-209">Click the circle next to **Output** and select **SoundEffects** from the pop-up.</span></span>

<span data-ttu-id="a5793-210">Unity를 사용 하는 프로젝트 데시벨 **AudioMixer** 소리의 그룹에 대 한 사운드 수준을 조정 하는 사용 하도록 설정 하려면 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-210">Project Decibel uses a Unity **AudioMixer** component to enable adjusting sound levels for groups of sounds.</span></span> <span data-ttu-id="a5793-211">소리가 그룹화 이러한 방식으로 각 사운드의 상대 볼륨 유지 관리 하는 동안 전체 볼륨을 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-211">By grouping sounds this way, the overall volume can be adjusted while maintaining the relative volume of each sound.</span></span>

* <span data-ttu-id="a5793-212">에 **AudioSource**를 확장 하 고 **3D 소리 설정**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-212">In the **AudioSource**, expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="a5793-213">설정할 **doppler가 수준** 하 **0**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-213">Set **Doppler Level** to **0**.</span></span>

<span data-ttu-id="a5793-214">0 개 사용 하지 않도록 설정 변경 (사용자나를 홀로그램 중 하나) 동작을 야기 하는 피치에 doppler가 수준을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-214">Setting Doppler level to zero disables changes in pitch caused by motion (either of the hologram or the user).</span></span> <span data-ttu-id="a5793-215">Doppler가 전형적인 예로 빠르게 움직이는 차량 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-215">A classic example of Doppler is a fast-moving car.</span></span> <span data-ttu-id="a5793-216">자동차 고정 수신기 다가오면 엔진의 피치 증가 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-216">As the car approaches a stationary listener, the pitch of the engine rises.</span></span> <span data-ttu-id="a5793-217">수신기를 전달할 때 피치 거리를 사용 하 여 낮춰 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-217">When it passes the listener, the pitch lowers with distance.</span></span>

### <a name="part-2---directing-the-users-gaze"></a><span data-ttu-id="a5793-218">2 부-사용자의 게이즈를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-218">Part 2 - Directing the User's Gaze</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="a5793-219">주요 개념</span><span class="sxs-lookup"><span data-stu-id="a5793-219">Key Concepts</span></span>

* <span data-ttu-id="a5793-220">중요 한 홀로그램을 강조할 소리를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-220">Use sound to call attention to important holograms.</span></span>
* <span data-ttu-id="a5793-221">돌릴 눈 같아야 여기서 직접 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-221">The ears help direct where the eyes should look.</span></span>
* <span data-ttu-id="a5793-222">뇌에 몇 가지 학습된 기대 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-222">The brain has some learned expectations.</span></span>

<span data-ttu-id="a5793-223">학습된 예상의 예로 새 일반적으로 사용자의 머리 위의.</span><span class="sxs-lookup"><span data-stu-id="a5793-223">One example of learned expectations is that birds are generally above the heads of humans.</span></span> <span data-ttu-id="a5793-224">사용자에서 bird 소리를 수신 하는 경우 해당 초기 반응은 조회 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-224">If a user hears a bird sound, their initial reaction is to look up.</span></span> <span data-ttu-id="a5793-225">사용자 아래 bird 배치의 소리를 조회할 필요가 기대에 따라 홀로그램을 찾을 수 없거나 올바른 방향을 향하고에 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-225">Placing a bird below the user can lead to them facing the correct direction of the sound, but being unable to find the hologram based on the expectation of needing to look up.</span></span>

#### <a name="instructions"></a><span data-ttu-id="a5793-226">지침</span><span class="sxs-lookup"><span data-stu-id="a5793-226">Instructions</span></span>

<span data-ttu-id="a5793-227">다음 지침을를 홀로그램 찾으려고 소리를 사용할 수 있도록 백그라운드에서 숨기려면 P0LY를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-227">The following instructions enable P0LY to hide behind you, so that you can use sound to locate the hologram.</span></span>

* <span data-ttu-id="a5793-228">에 **계층 구조** 패널에서 **관리자**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-228">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="a5793-229">에 **검사기** 패널에서 찾기 **음성 입력 처리기**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-229">In the **Inspector** panel, find **Speech Input Handler**.</span></span>
* <span data-ttu-id="a5793-230">**음성 입력 처리기**를 확장 하 고 **숨기기 이동**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-230">In **Speech Input Handler**, expand **Go Hide**.</span></span>
* <span data-ttu-id="a5793-231">변경 **함수가** 하 **PolyActions.GoHide**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-231">Change **No Function** to **PolyActions.GoHide**.</span></span>

![키워드: 이동 숨기기](images/gohide.png)

### <a name="part-3---gesture-feedback"></a><span data-ttu-id="a5793-233">3 부-제스처 피드백</span><span class="sxs-lookup"><span data-stu-id="a5793-233">Part 3 - Gesture Feedback</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="a5793-234">주요 개념</span><span class="sxs-lookup"><span data-stu-id="a5793-234">Key Concepts</span></span>

* <span data-ttu-id="a5793-235">소리를 사용 하 여 양수 제스처 확인을 사용 하 여 사용자를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-235">Provide the user with positive gesture confirmation using sound</span></span>
* <span data-ttu-id="a5793-236">과도 하 게 큰 사운드 가져오기 방법으로 사용자가 채워지지 않습니다</span><span class="sxs-lookup"><span data-stu-id="a5793-236">Do not overwhelm the user - overly loud sounds get in the way</span></span>
* <span data-ttu-id="a5793-237">최상의-미묘한 소리 작업 환경을 흐릿하게 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-237">Subtle sounds work best - do not overshadow the experience</span></span>

#### <a name="instructions"></a><span data-ttu-id="a5793-238">지침</span><span class="sxs-lookup"><span data-stu-id="a5793-238">Instructions</span></span>

* <span data-ttu-id="a5793-239">에 **계층 구조** 패널에서 확장 **HologramCollection**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-239">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="a5793-240">확장 **EnergyHub** 선택한 **자료**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-240">Expand **EnergyHub** and select **Base**.</span></span>
* <span data-ttu-id="a5793-241">에 **검사기** 패널에서 **구성 요소 추가** 추가한 **제스처 소리 처리기**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-241">In the **Inspector** panel, click **Add Component** and add **Gesture Sound Handler**.</span></span>
* <span data-ttu-id="a5793-242">**제스처 소리 처리기**, 옆에 원을 클릭 **탐색 시작 클립** 하 고 **탐색 업데이트 클립** 선택한 **RotateClick**둘 다에 대 한 팝업에서.</span><span class="sxs-lookup"><span data-stu-id="a5793-242">In **Gesture Sound Handler**, click the circle next to **Navigation Started Clip** and **Navigation Updated Clip** and select **RotateClick** from the pop-up for both.</span></span>
* <span data-ttu-id="a5793-243">Visual Studio에서 로드 하려면 "GestureSoundHandler"을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-243">Double click on "GestureSoundHandler" to load in Visual Studio.</span></span>

<span data-ttu-id="a5793-244">제스처 소리 처리기는 다음 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-244">Gesture Sound Handler performs the following tasks:</span></span>

* <span data-ttu-id="a5793-245">만들기 및 구성 된 **AudioSource**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-245">Create and configure an **AudioSource**.</span></span>
* <span data-ttu-id="a5793-246">위치는 **AudioSource** 적절 한 위치의 **GameObject**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-246">Place the **AudioSource** at the location of the appropriate **GameObject**.</span></span>
* <span data-ttu-id="a5793-247">재생 합니다 **AudioClip** 제스처와 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-247">Plays the **AudioClip** associated with the gesture.</span></span>

#### <a name="build-and-deploy"></a><span data-ttu-id="a5793-248">빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="a5793-248">Build and Deploy</span></span>

1. <span data-ttu-id="a5793-249">Unity에서 선택 **파일 > 빌드 설정**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-249">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="a5793-250">**빌드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-250">Click **Build**.</span></span>
3. <span data-ttu-id="a5793-251">한 번 클릭 합니다 **앱** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-251">Single click the **App** folder.</span></span>
4. <span data-ttu-id="a5793-252">키를 눌러 **폴더 선택**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-252">Press **Select Folder**.</span></span>

<span data-ttu-id="a5793-253">도구 모음에서 "릴리스", "x86" 또는 "x64" 및 "원격 장치" 라는 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-253">Check that the Toolbar says "Release", "x86" or "x64", and "Remote Device".</span></span> <span data-ttu-id="a5793-254">그렇지 않은 경우이 Visual Studio의 코딩 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-254">If not, this is the coding instance of Visual Studio.</span></span> <span data-ttu-id="a5793-255">앱 폴더에서 솔루션을 다시 엽니다 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-255">You may need to re-open the solution from the App folder.</span></span>

* <span data-ttu-id="a5793-256">메시지가 표시 되 면 프로젝트 파일을 다시 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-256">If prompted, reload the project files.</span></span>
* <span data-ttu-id="a5793-257">이전 처럼 Visual Studio에서 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-257">As before, deploy from Visual Studio.</span></span>

<span data-ttu-id="a5793-258">응용 프로그램 후 배포 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-258">After the application is deployed:</span></span>

* <span data-ttu-id="a5793-259">P0LY 내에서 이동할 때에 따라 소리가 어떻게 변경 되는지 관찰 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-259">Observe how the sound changes as you move around P0LY.</span></span>
* <span data-ttu-id="a5793-260">예를 들어 *"이동 숨기기"* P0LY 백그라운드 위치로 이동할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-260">Say *"Go Hide"* to make P0LY move to a location behind you.</span></span> <span data-ttu-id="a5793-261">소리를 찾으려면 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-261">Find it by the sound.</span></span>
* <span data-ttu-id="a5793-262">에너지 허브의 자료를 응시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-262">Gaze at the base of the Energy Hub.</span></span> <span data-ttu-id="a5793-263">탭 끌어서 왼쪽 또는 오른쪽으로 회전를 홀로그램 및 클릭 소리 제스처를 확인 하는 방법을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-263">Tap and drag left or right to rotate the hologram and notice how the clicking sound confirms the gesture.</span></span>

<span data-ttu-id="a5793-264">참고: 사용자와 tag-along는 텍스트 패널이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-264">Note: There is a text panel that will tag-along with you.</span></span> <span data-ttu-id="a5793-265">이 과정을 통해 사용할 수 있는 사용 가능한 음성 명령을 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-265">This will contain the available voice commands that you can use throughout this course.</span></span>

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a><span data-ttu-id="a5793-266">3 장-공간 사운드 및 공간 매핑</span><span class="sxs-lookup"><span data-stu-id="a5793-266">Chapter 3 - Spatial Sound and Spatial Mapping</span></span>

### <a name="objectives"></a><span data-ttu-id="a5793-267">목표</span><span class="sxs-lookup"><span data-stu-id="a5793-267">Objectives</span></span>

* <span data-ttu-id="a5793-268">홀로그램와 소리를 사용 하 여 실제 환경 간의 상호 작용을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-268">Confirm interaction between holograms and the real world using sound.</span></span>
* <span data-ttu-id="a5793-269">실제 세계를 사용 하 여 소리를 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-269">Occlude sound using the physical world.</span></span>

### <a name="part-1---physical-world-interaction"></a><span data-ttu-id="a5793-270">1 부-실제 환경 상호 작용</span><span class="sxs-lookup"><span data-stu-id="a5793-270">Part 1 - Physical World Interaction</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="a5793-271">주요 개념</span><span class="sxs-lookup"><span data-stu-id="a5793-271">Key Concepts</span></span>

* <span data-ttu-id="a5793-272">화면 또는 다른 발생 하는 경우 일반적으로 실제 개체 때 소리가 재생 되도록 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-272">Physical objects generally make a sound when encountering a surface or another object.</span></span>
* <span data-ttu-id="a5793-273">소리 환경에서 적절 한 컨텍스트에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-273">Sounds should be context appropriate within the experience.</span></span>

<span data-ttu-id="a5793-274">예를 들어 테이블에 대 한 설정 금속 부분에서 볼더의 삭제 보다 작게 소리를 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-274">For example, setting a cup on a table should make a quieter sound than dropping a boulder on a piece of metal.</span></span>

#### <a name="instructions"></a><span data-ttu-id="a5793-275">지침</span><span class="sxs-lookup"><span data-stu-id="a5793-275">Instructions</span></span>

* <span data-ttu-id="a5793-276">에 **계층 구조** 패널에서 확장 **HologramCollection**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-276">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="a5793-277">확장 **EnergyHub**를 선택 **자료**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-277">Expand **EnergyHub**, select **Base**.</span></span>
* <span data-ttu-id="a5793-278">에 **검사기** 패널에서 **구성 요소 추가** 추가한 **탭을 현재 위치와 소리 및 작업**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-278">In the **Inspector** panel, click **Add Component** and add **Tap To Place With Sound and Action**.</span></span>
* <span data-ttu-id="a5793-279">**소리 및 작업을 사용 하 여 위치로 누릅니다**:</span><span class="sxs-lookup"><span data-stu-id="a5793-279">In **Tap To Place With Sound and Action**:</span></span>
  * <span data-ttu-id="a5793-280">확인할 **탭에 부모 놓기**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-280">Check **Place Parent On Tap**.</span></span>
  * <span data-ttu-id="a5793-281">설정할 **배치 소리** 하 **위치**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-281">Set **Placement Sound** to **Place**.</span></span>
  * <span data-ttu-id="a5793-282">설정 **Pickup 소리** 하 **Pickup**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-282">Set **Pickup Sound** to **Pickup**.</span></span>
  * <span data-ttu-id="a5793-283">+ 둘 다에서 오른쪽 아래에 있는 키를 누릅니다 **픽업 작업에서** 하 고 **배치 작업에서**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-283">Press the + in the bottom right under both **On Pickup Action** and **On Placement Action**.</span></span> <span data-ttu-id="a5793-284">EnergyHub에 장면에서 끌어 합니다 **없음 (개체)** 필드입니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-284">Drag EnergyHub from the scene into the **None (Object)** fields.</span></span>
    * <span data-ttu-id="a5793-285">아래 **픽업 작업에서**, 클릭 **No 함수** -> **EnergyHubBase** -> **ResetAnimation**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-285">Under **On Pickup Action**, click on **No Function** -> **EnergyHubBase** -> **ResetAnimation**.</span></span>
    * <span data-ttu-id="a5793-286">아래 **배치 작업에서**, 클릭 **No 함수** -> **EnergyHubBase** -> **OnSelect**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-286">Under **On Placement Action**, click on **No Function** -> **EnergyHubBase** -> **OnSelect**.</span></span>

![소리 및 작업을 사용 하 여 위치로 탭](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a><span data-ttu-id="a5793-288">2 부-사운드 폐색</span><span class="sxs-lookup"><span data-stu-id="a5793-288">Part 2 - Sound Occlusion</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="a5793-289">주요 개념</span><span class="sxs-lookup"><span data-stu-id="a5793-289">Key Concepts</span></span>

* <span data-ttu-id="a5793-290">소리, 빛을 같은 폐색 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-290">Sound, like light, can be occluded.</span></span>

<span data-ttu-id="a5793-291">전형적인 예는 콘서트 홀입니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-291">A classic example is a concert hall.</span></span> <span data-ttu-id="a5793-292">hall과 문 외부에서 수신기는 준비 하는 경우 닫혀 muffled 음악 소리 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-292">When a listener is standing outside of the hall and the door is closed, the music sounds muffled.</span></span> <span data-ttu-id="a5793-293">이기도 일반적으로 볼륨 감소 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-293">There is also typically a reduction in volume.</span></span> <span data-ttu-id="a5793-294">도어를 열 때 실제 볼륨에서 폭넓은 소리가 들립니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-294">When the door is opened, the full spectrum of the sound is heard at the actual volume.</span></span> <span data-ttu-id="a5793-295">높은 빈도 소리 더 낮은 빈도 보다 흡수 일반적으로 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-295">High frequency sounds are generally absorbed more than low frequencies.</span></span>

#### <a name="instructions"></a><span data-ttu-id="a5793-296">지침</span><span class="sxs-lookup"><span data-stu-id="a5793-296">Instructions</span></span>

* <span data-ttu-id="a5793-297">에 **계층 구조** 패널에서 확장 **HologramCollection** 선택한 **P0LY**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-297">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="a5793-298">에 **검사기** 패널에서 **구성 요소 추가** 추가한 **오디오 내보내기**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-298">In the **Inspector** panel, click **Add Component** and add **Audio Emitter**.</span></span>

<span data-ttu-id="a5793-299">오디오 내보내기 클래스는 다음과 같은 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-299">The Audio Emitter class provides the following features:</span></span>

* <span data-ttu-id="a5793-300">볼륨에 변경 내용을 복원 합니다 **AudioSource**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-300">Restores any changes to the volume of the **AudioSource**.</span></span>
* <span data-ttu-id="a5793-301">수행를 **Physics.RaycastNonAlloc** 방향으로 사용자의 위치에서는 **GameObject** 는 **AudioEmitter** 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-301">Performs a **Physics.RaycastNonAlloc** from the user's position in the direction of the **GameObject** to which the **AudioEmitter** is attached.</span></span>

<span data-ttu-id="a5793-302">RaycastNonAlloc 메서드는 반환 된 결과의 수 뿐만 아니라 할당 제한 성능 최적화로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-302">The RaycastNonAlloc method is used as a performance optimization to limit allocations as well as the number of results returned.</span></span>

* <span data-ttu-id="a5793-303">각 **IAudioInfluencer** 발생 하면 호출 된 **ApplyEffect** 메서드.</span><span class="sxs-lookup"><span data-stu-id="a5793-303">For each **IAudioInfluencer** encountered, calls the **ApplyEffect** method.</span></span>
* <span data-ttu-id="a5793-304">각각에 대 한 이전 **IAudioInfluencer** 는 더 이상 발생 한 호출을 **RemoveEffect** 메서드.</span><span class="sxs-lookup"><span data-stu-id="a5793-304">For each previous **IAudioInfluencer** that is no longer encountered, call the **RemoveEffect** method.</span></span>

<span data-ttu-id="a5793-305">AudioEmitter 업데이트 인간의 시간 규모와는 반대로 프레임당에 유의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-305">Note that AudioEmitter updates on human time scales, as opposed to on a per frame basis.</span></span> <span data-ttu-id="a5793-306">사람은 일반적으로 모든 분기 또는 0.5 초가 보다 더 자주 업데이트 해야 하는 효과 대 한 충분히 빠르게 이동 하지 마십시오 때문에 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-306">This is done because humans generally do not move fast enough for the effect to need to be updated more frequently than every quarter or half of a second.</span></span> <span data-ttu-id="a5793-307">홀로그램 다른 곳에서 신속 하 게 해당 텔레포트 효과 중단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-307">Holograms that teleport rapidly from one location to another can break the illusion.</span></span>

* <span data-ttu-id="a5793-308">에 **계층 구조** 패널에서 확장 **HologramCollection**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-308">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="a5793-309">확장 **EnergyHub** 선택한 **BlobOutside**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-309">Expand **EnergyHub** and select **BlobOutside**.</span></span>
* <span data-ttu-id="a5793-310">에 **검사기** 패널에서 **구성 요소 추가** 추가한 **오디오 Occluder**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-310">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="a5793-311">**오디오 Occluder**설정 **구분 주파수** 하 **1500**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-311">In **Audio Occluder**, set **Cutoff Frequency** to **1500**.</span></span>

<span data-ttu-id="a5793-312">이 설정은 1500 Hz이 하 버전에 AudioSource 빈도 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-312">This setting limits the AudioSource frequencies to 1500 Hz and below.</span></span>

* <span data-ttu-id="a5793-313">설정할 **볼륨 통과** 하 **0.9**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-313">Set **Volume Pass Through** to **0.9**.</span></span>

<span data-ttu-id="a5793-314">이 설정은 현재 수준의 90%를 AudioSource의 볼륨은 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-314">This setting reduces the volume of the AudioSource to 90% of it's current level.</span></span>

<span data-ttu-id="a5793-315">오디오 Occluder IAudioInfluencer를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-315">Audio Occluder implements IAudioInfluencer to:</span></span>

* <span data-ttu-id="a5793-316">사용 하 여 폐색 효과 적용는 **AudioLowPassFilter** 에 연결 하는 합니다 **AudioSource** 관리 되는 구입 합니다 **AudioEmitter**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-316">Apply an occlusion effect using an **AudioLowPassFilter** which gets attached to the **AudioSource** managed buy the **AudioEmitter**.</span></span>
* <span data-ttu-id="a5793-317">볼륨 감쇠를 AudioSource 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-317">Applies volume attenuation to the AudioSource.</span></span>
* <span data-ttu-id="a5793-318">중립 차단 주파수를 설정 하 고 필터를 사용 하지 않도록 설정 하 여 효과 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-318">Disables the effect by setting a neutral cutoff frequency and disabling the filter.</span></span>

<span data-ttu-id="a5793-319">중립으로 사용 되는 빈도 22 kHz (22000 Hz)입니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-319">The frequency used as neutral is 22 kHz (22000 Hz).</span></span> <span data-ttu-id="a5793-320">이 빈도이 게 눈에 띄는 영향을 미치지 소리를 사람의 귀 여 낼 수는 명목 최대 빈도 위에 기 때문에 선택 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-320">This frequency was chosen due to it being above the nominal maximum frequency that can be heard by the human ear, this making no discernable impact to the sound.</span></span>

* <span data-ttu-id="a5793-321">에 **계층 구조** 패널에서 **SpatialMapping**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-321">In the **Hierarchy** panel, select **SpatialMapping**.</span></span>
* <span data-ttu-id="a5793-322">에 **검사기** 패널에서 **구성 요소 추가** 추가한 **오디오 Occluder**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-322">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="a5793-323">**오디오 Occluder**설정 **구분 주파수** 하 **750**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-323">In **Audio Occluder**, set **Cutoff Frequency** to **750**.</span></span>

<span data-ttu-id="a5793-324">사용자 간의 경로에 여러 occluders 표시 되는 경우와 **AudioEmitter**, 가장 낮은 빈도 필터에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-324">When multiple occluders are in the path between the user and the **AudioEmitter**, the lowest frequency is applied to the filter.</span></span>

* <span data-ttu-id="a5793-325">설정할 **볼륨 통과** 하 **0.75**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-325">Set **Volume Pass Through** to **0.75**.</span></span>

<span data-ttu-id="a5793-326">사용자 간의 경로에 여러 occluders 표시 되는 경우와 **AudioEmitter**, 볼륨 통과 입자 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-326">When multiple occluders are in the path between the user and the **AudioEmitter**, the volume pass through is applied additively.</span></span>

* <span data-ttu-id="a5793-327">에 **계층 구조** 패널에서 **관리자**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-327">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="a5793-328">에 **검사기** 패널에서 확장 **음성 입력 처리기**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-328">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="a5793-329">**음성 입력 처리기**를 확장 하 고 **이동 요금이**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-329">In **Speech Input Handler**, expand **Go Charge**.</span></span>
* <span data-ttu-id="a5793-330">변경 **함수가** 하 **PolyActions.GoCharge**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-330">Change **No Function** to **PolyActions.GoCharge**.</span></span>

![키워드: 이동 비용](images/gocharge.png)

* <span data-ttu-id="a5793-332">확장 **여기**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-332">Expand **Come Here**.</span></span>
* <span data-ttu-id="a5793-333">변경 **함수가** 하 **PolyActions.ComeBack**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-333">Change **No Function** to **PolyActions.ComeBack**.</span></span>

![키워드: 여기로 오세요](images/comehere.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="a5793-335">빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="a5793-335">Build and Deploy</span></span>

* <span data-ttu-id="a5793-336">이전과 마찬가지로 Unity에서 프로젝트를 빌드하고 Visual Studio에서 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-336">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="a5793-337">응용 프로그램 후 배포 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-337">After the application is deployed:</span></span>

* <span data-ttu-id="a5793-338">예를 들어 *"이동 요금"* P0LY 에너지 허브를 입력 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-338">Say *"Go Charge"* to have P0LY enter the Energy Hub.</span></span>

<span data-ttu-id="a5793-339">소리 변경을 note 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-339">Note the change in the sound.</span></span> <span data-ttu-id="a5793-340">해당 muffled 및 좀 더 조용 사운드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-340">It should sound muffled and a little quieter.</span></span> <span data-ttu-id="a5793-341">벽에 다른 개체와 에너지 허브 간에 직접 위치로 수 있다면 실제로 폐색으로 인해 소리 추가 muffling 유의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-341">If you are able to position yourself with a wall or other object between you and the Energy Hub, you should notice a further muffling of the sound due to the occlusion by the real world.</span></span>

* <span data-ttu-id="a5793-342">예를 들어 *"여기에 제공"* P0LY 에너지 허브를 그대로 두고 자체는 사용자 앞에 배치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-342">Say *"Come Here"* to have P0LY leave the Energy Hub and position itself in front of you.</span></span>

<span data-ttu-id="a5793-343">Note는 사운드 폐색 P0LY 에너지 허브 종료 되 면 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-343">Note that the sound occlusion is removed once P0LY exits the Energy Hub.</span></span> <span data-ttu-id="a5793-344">인 경우 여전히 청각 폐색 P0LY 실제 세계에서 폐색 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-344">If you are still hearing occlusion, P0LY may be occluded by the real world.</span></span> <span data-ttu-id="a5793-345">명확한 시야를 P0LY 했는지를 옮겨 보십시오.</span><span class="sxs-lookup"><span data-stu-id="a5793-345">Try moving to ensure you have a clear line of sight to P0LY.</span></span>

### <a name="part-3---room-models"></a><span data-ttu-id="a5793-346">3 부-방 모델</span><span class="sxs-lookup"><span data-stu-id="a5793-346">Part 3 - Room Models</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="a5793-347">주요 개념</span><span class="sxs-lookup"><span data-stu-id="a5793-347">Key Concepts</span></span>

* <span data-ttu-id="a5793-348">사운드 지역화에 영향을 주는 subliminal 큐를 제공 하는 공간의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-348">The size of the space provides subliminal queues that contribute to sound localization.</span></span>
* <span data-ttu-id="a5793-349">대화방 모델 별로 설정 되-**AudioSource**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-349">Room models are set per-**AudioSource**.</span></span>
* <span data-ttu-id="a5793-350">[Unity에 대 한 MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity) 회의실 모델 설정에 대 한 코드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-350">The [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides code for setting the room model.</span></span>
* <span data-ttu-id="a5793-351">혼합 현실 환경에 대 한 실제 세계 좌표 공간에 가장 잘 맞는 공간이 모델을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-351">For Mixed Reality experiences, select the room model that best fits the real world space.</span></span>

<span data-ttu-id="a5793-352">가상 현실 시나리오를 만드는 경우 가상 환경에 가장 잘 맞는 공간이 모델을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-352">If you are creating a Virtual Reality scenario, select the room model that best fits the virtual environment.</span></span>

## <a name="chapter-4---sound-design"></a><span data-ttu-id="a5793-353">4 장-적절 하 게 디자인</span><span class="sxs-lookup"><span data-stu-id="a5793-353">Chapter 4 - Sound Design</span></span>

### <a name="objectives"></a><span data-ttu-id="a5793-354">목표</span><span class="sxs-lookup"><span data-stu-id="a5793-354">Objectives</span></span>

* <span data-ttu-id="a5793-355">효율적인 사운드 디자인에 대 한 고려 사항을 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-355">Understand considerations for effective sound design.</span></span>
* <span data-ttu-id="a5793-356">혼합 기술 및 지침에 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-356">Learn mixing techniques and guidelines.</span></span>

### <a name="part-1---sound-and-experience-design"></a><span data-ttu-id="a5793-357">1 부-소리 및 환경 디자인</span><span class="sxs-lookup"><span data-stu-id="a5793-357">Part 1 - Sound and Experience Design</span></span>

<span data-ttu-id="a5793-358">이 섹션에서는 키 소리 및 환경 디자인 고려 사항 및 지침을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-358">This section discusses key sound and experience design considerations and guidelines.</span></span>

#### <a name="normalize-all-sounds"></a><span data-ttu-id="a5793-359">모든 소리를 정규화 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-359">Normalize all sounds</span></span>

<span data-ttu-id="a5793-360">이 시간이 오래 걸릴 수 있는 소리 당 볼륨 수준에 맞게 특수 사례 코드에 대 한 필요가 없습니다를 쉽게 사운드 파일을 업데이트 하는 기능을 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-360">This avoids the need for special case code to adjust volume levels per sound, which can be time consuming and limits the ability to easily update sound files.</span></span>

#### <a name="design-for-an-untethered-experience"></a><span data-ttu-id="a5793-361">제한 되지 않는 환경 디자인</span><span class="sxs-lookup"><span data-stu-id="a5793-361">Design for an untethered experience</span></span>

<span data-ttu-id="a5793-362">HoloLens에 완전히 포함 된, 클라우드가 holographic 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-362">HoloLens is a fully contained, untethered holographic computer.</span></span> <span data-ttu-id="a5793-363">사용자를 이동 하는 동안 경험을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-363">Your users can and will use your experiences while moving.</span></span> <span data-ttu-id="a5793-364">에 오디오 믹스를 따라 이동 하 여 테스트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-364">Be sure to test your audio mix by walking around.</span></span>

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a><span data-ttu-id="a5793-365">소리에 홀로그램의 논리적 위치에서 내보내기</span><span class="sxs-lookup"><span data-stu-id="a5793-365">Emit sound from logical locations on your holograms</span></span>

<span data-ttu-id="a5793-366">실제 상황에서 dog 꼬리에서 짖는 하지 않습니다 및 사람이 음성 자신의 피트에서 제공 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-366">In the real world, a dog does not bark from its tail and a human's voice does not come from his/her feet.</span></span> <span data-ttu-id="a5793-367">소리 내보낼에서 예기치 않은 부분에 제공 하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-367">Avoid having your sounds emit from unexpected portions of your holograms.</span></span>

<span data-ttu-id="a5793-368">작은 홀로그램 기 하 도형 중심에서 내보낼 소리 할 적절 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-368">For small holograms, it is reasonable to have sound emit from the center of the geometry.</span></span>

#### <a name="familiar-sounds-are-most-localizable"></a><span data-ttu-id="a5793-369">친숙 한 소리는 지역화할 수 있는 가장</span><span class="sxs-lookup"><span data-stu-id="a5793-369">Familiar sounds are most localizable</span></span>

<span data-ttu-id="a5793-370">인간의 음성 및 음악은 매우 쉽게 지역화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-370">The human voice and music are very easy to localize.</span></span> <span data-ttu-id="a5793-371">사용자 이름, 호출 하는 경우에 매우 정확 하 게 결정할 방법에서 제공 하는 음성 방향을 멀리 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-371">If someone calls your name, you are able to very accurately determine from what direction the voice came and from how far away.</span></span> <span data-ttu-id="a5793-372">짧은, 알 수 없는 소리 지역화 하기는 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-372">Short, unfamiliar sounds are harder to localize.</span></span>

#### <a name="be-cognizant-of-user-expectations"></a><span data-ttu-id="a5793-373">사용자 기대 한다는 점을 인식</span><span class="sxs-lookup"><span data-stu-id="a5793-373">Be cognizant of user expectations</span></span>

<span data-ttu-id="a5793-374">소리의 위치를 식별 하는 데에서 일부를 담당 하는 경험 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-374">Life experience plays a part in our ability to identify the location of a sound.</span></span> <span data-ttu-id="a5793-375">사람의 음성 특히 쉽게 지역화할 수 없는 이유는 하나의 이유입니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-375">This is one reason why the human voice is particularly easy to localize.</span></span> <span data-ttu-id="a5793-376">소리를 배치 하는 경우 사용자의 학습 기대 알아야 할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-376">It is important to be aware of your user's learned expectations when placing your sounds.</span></span>

<span data-ttu-id="a5793-377">예를 들어 누군가가 시도해볼 bird 노래 하는 경우 일반적으로 조회 하는, 시야 (공중 또는 트리에서) 위에 새 경향이으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-377">For example, when someone hears a bird song they generally look up, as birds tend to be above the line of sight (flying or in a tree).</span></span> <span data-ttu-id="a5793-378">소리의 올바른 방향으로 설정 되지만 잘못 된 세로 방향에서 모양과 홀로그램을 찾을 수 없는 경우 혼동 되거나 불편 될 사용자에 대 한 일반적이 지 않은 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-378">It is not uncommon for a user to turn in the correct direction of a sound, but look in the wrong vertical direction and become confused or frustrated when they are unable to find the hologram.</span></span>

#### <a name="avoid-hidden-emitters"></a><span data-ttu-id="a5793-379">숨겨진된 송신기 방지</span><span class="sxs-lookup"><span data-stu-id="a5793-379">Avoid hidden emitters</span></span>

<span data-ttu-id="a5793-380">실제 상황에서 소리를 구하면에서는 일반적으로 식별할 수 소리를 표시 하는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-380">In the real world, if we hear a sound, we can generally identify the object that is emitting the sound.</span></span> <span data-ttu-id="a5793-381">이 경험에 변수에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-381">This should also hold true in your experiences.</span></span> <span data-ttu-id="a5793-382">소리를 듣고, 소리의 원본 위치에서 알고 있어야 하는 사용자에 대 한 매우 혼란을 줄 수 하 고 개체를 참조 하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-382">It can be very disconcerting for users to hear a sound, know from where the sound originates and be unable to see an object.</span></span>

<span data-ttu-id="a5793-383">이 지침을 몇 가지 예외가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-383">There are some exceptions to this guideline.</span></span> <span data-ttu-id="a5793-384">예를 들어 crickets 필드에 같은 앰비언트 소리 표시 되지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-384">For example, ambient sounds such as crickets in a field need not be visible.</span></span> <span data-ttu-id="a5793-385">수명 환경을 볼 필요 없이 이러한 소리의 소스와 경험을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-385">Life experience gives us familiarity with the source of these sounds without the need to see it.</span></span>

### <a name="part-2---sound-mixing"></a><span data-ttu-id="a5793-386">2 부-사운드 혼합</span><span class="sxs-lookup"><span data-stu-id="a5793-386">Part 2 - Sound Mixing</span></span>

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a><span data-ttu-id="a5793-387">프로그램 조합에는 HoloLens 70% 볼륨에 대 한 대상</span><span class="sxs-lookup"><span data-stu-id="a5793-387">Target your mix for 70% volume on the HoloLens</span></span>

<span data-ttu-id="a5793-388">혼합된 현실 환경 홀로그램 실제 환경에서 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-388">Mixed Reality experiences allow holograms to be seen in the real world.</span></span> <span data-ttu-id="a5793-389">또한 실제 소리가 들을 수 해야 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-389">They should also allow real world sounds to be heard.</span></span> <span data-ttu-id="a5793-390">70% 볼륨 대상을 이들을 사용자 경험의 소리와 함께 전 세계를 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-390">A 70% volume target enables the user to hear the world around them along with the sound of your experience.</span></span>

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a><span data-ttu-id="a5793-391">100% 볼륨에는 HoloLens 외부 소리 압도 될 해야</span><span class="sxs-lookup"><span data-stu-id="a5793-391">HoloLens at 100% volume should drown out external sounds</span></span>

<span data-ttu-id="a5793-392">100%의 볼륨 수준은 가상 현실 환경 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-392">A volume level of 100% is akin to a Virtual Reality experience.</span></span> <span data-ttu-id="a5793-393">시각적으로 사용자는 다른 환경에 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-393">Visually, the user is transported to a different world.</span></span> <span data-ttu-id="a5793-394">동일한 true로 유지 되어야 음성으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-394">The same should hold true audibly.</span></span>

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a><span data-ttu-id="a5793-395">Unity AudioMixer를 사용 하 여 소리의 범주를 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-395">Use the Unity AudioMixer to adjust categories of sounds</span></span>

<span data-ttu-id="a5793-396">프로그램 조합을 디자인할 때이 것이 좋습니다 사운드 범주를 만들고 하나의 단위로 해당 볼륨을 늘리거나 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-396">When designing your mix, it is often helpful to create sound categories and have the ability to increase or decrease their volume as a unit.</span></span> <span data-ttu-id="a5793-397">이 쉽고 빠르게 변경 전반적 혼합을 사용 하도록 설정 하는 동안 각 사운드의 상대적 수준을 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-397">This retains the relative levels of each sound while enabling quick and easy changes to the overall mix.</span></span> <span data-ttu-id="a5793-398">공통 범주는 다음과 같습니다. 음향 효과, 앰 비 언스, 음성 조치 및 배경 음악</span><span class="sxs-lookup"><span data-stu-id="a5793-398">Common categories include; sound effects, ambience, voice overs and background music.</span></span>

#### <a name="mix-sounds-based-on-the-users-gaze"></a><span data-ttu-id="a5793-399">사용자의 게이즈를 기준으로 소리를 혼합</span><span class="sxs-lookup"><span data-stu-id="a5793-399">Mix sounds based on the user's gaze</span></span>

<span data-ttu-id="a5793-400">사운드 목록을 변경 하려면 종종 유용 위치 기반 환경에서 사용자가 (없거나) 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-400">It can often be useful to change the sound mix in your experience based on where a user is (or is not) looking.</span></span> <span data-ttu-id="a5793-401">이 기술의 한 가지 일반적인 용도 앞에 정보를 중점적으로 사용자에 대해 쉽게 Holographic 프레임 외부에 있는 홀로그램의 볼륨 수준을 줄일 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-401">One common use for this technique are to reduce the volume level for holograms that are outside of the Holographic Frame to make it easier for the user to focus on the information in front of them.</span></span> <span data-ttu-id="a5793-402">중요 한 이벤트가 사용자의 주의를 끌기 소리의 볼륨은 다른 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-402">Another use is to increase the volume of a sound to draw the user's attention to an important event.</span></span>

#### <a name="building-your-mix"></a><span data-ttu-id="a5793-403">빌드에 조합</span><span class="sxs-lookup"><span data-stu-id="a5793-403">Building your mix</span></span>

<span data-ttu-id="a5793-404">프로그램 조합을 빌드하는 경우에 환경의 배경 오디오를 사용 하 여 시작 하 고 중요도에 따라 계층을 추가 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-404">When building your mix, it is recommended to start with your experience's background audio and add layers based on importance.</span></span> <span data-ttu-id="a5793-405">종종이 이전 보다 더 크게 중인 각 계층의 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-405">Often, this results in each layer being louder than the previous.</span></span>

<span data-ttu-id="a5793-406">여는 반전 된 중요도 사용 하 여 깔때기를 상상 일 뿐 (및 일반적으로 조용한 소리)의 맨 아래에 있는 것이 좋습니다는 다음 다이어그램과 유사 하 여 조합을 구조체입니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-406">Imagining your mix as an inverted funnel, with the least important (and generally quietest sounds) at the bottom, it is recommended to structure your mix similar to the following diagram.</span></span>

![사운드 혼합 구조](images/soundlevels.png)

<span data-ttu-id="a5793-408">음성 조치는 흥미로운 시나리오입니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-408">Voice overs are an interesting scenario.</span></span> <span data-ttu-id="a5793-409">기반 만드는 환경에 스테레오 (지역화 되지 않습니다) 소리가 또는 사용자 음성 조치 spatialize 할 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-409">Based on the experience you are creating you may wish to have a stereo (not localized) sound or to spatialize your voice overs.</span></span> <span data-ttu-id="a5793-410">두 개의 Microsoft 게시 환경을 각 시나리오의 훌륭한 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-410">Two Microsoft published experiences illustrate excellent examples of each scenario.</span></span>

<span data-ttu-id="a5793-411">[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87) 통해 스테레오 음성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-411">[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87) uses a stereo voice over.</span></span> <span data-ttu-id="a5793-412">내레이터가 표시 되는 위치를 설명 하는 소리 일치 하 고 사용자의 위치에 따라 달라 지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-412">When the narrator is describing the location being viewed, the sound is consistent and does not vary based on the user's position.</span></span> <span data-ttu-id="a5793-413">이 통해 환경의 spatialized 소리에서 수행 하지 않고 장면을 설명 하는 내레이터 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-413">This enables the narrator to describe the scene without taking away from the spatialized sounds of the environment.</span></span>

<span data-ttu-id="a5793-414">[조각](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) 는 검색의 형태로 spatialized 음성을 통해 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-414">[Fragments](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utilizes a spatialized voice over in the form of a detective.</span></span> <span data-ttu-id="a5793-415">셜록 홈즈 음성 사용자에 주의할는 중요 한 단서를 실제 사람이 방에 것 처럼 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-415">The detective's voice is used to help bring the user's attention to an important clue as if an actual human was in the room.</span></span> <span data-ttu-id="a5793-416">이 통해 비밀을 해결 하는 환경에 집중 교육을 훨씬 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-416">This enables an even greater sense of immersion into the experience of solving the mystery.</span></span>

### <a name="part-3--performance"></a><span data-ttu-id="a5793-417">파트 3-성능</span><span class="sxs-lookup"><span data-stu-id="a5793-417">Part 3 -Performance</span></span>

#### <a name="cpu-usage"></a><span data-ttu-id="a5793-418">CPU 사용량</span><span class="sxs-lookup"><span data-stu-id="a5793-418">CPU usage</span></span>

<span data-ttu-id="a5793-419">공간 소리를 사용할 때는 10-12 송신기 약 12 %CPU 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-419">When using Spatial Sound, 10 - 12 emitters will consume approximately 12% of the CPU.</span></span>

#### <a name="stream-long-audio-files"></a><span data-ttu-id="a5793-420">Stream 긴 오디오 파일</span><span class="sxs-lookup"><span data-stu-id="a5793-420">Stream long audio files</span></span>

<span data-ttu-id="a5793-421">오디오 데이터는 일반적인 샘플 속도 (44.1 및 48 kHz)에서 특히 큰 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-421">Audio data can be large, especially at common sample rates (44.1 and 48 kHz).</span></span> <span data-ttu-id="a5793-422">일반 규칙은 응용 프로그램 메모리 사용량을 줄이기 위해 5 ~ 10 초 이상 오디오 파일을 스트리밍할 수 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-422">A general rule is that audio files longer than 5 - 10 seconds should be streamed to reduce application memory usage.</span></span>

<span data-ttu-id="a5793-423">Unity에서 파일의 가져오기 설정에서 스트리밍에 대 한 오디오 파일을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-423">In Unity, you can mark an audio file for streaming in the file's import settings.</span></span>

![오디오 가져오기 설정](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a><span data-ttu-id="a5793-425">5 장-특수 효과</span><span class="sxs-lookup"><span data-stu-id="a5793-425">Chapter 5 - Special Effects</span></span>

### <a name="objectives"></a><span data-ttu-id="a5793-426">목표</span><span class="sxs-lookup"><span data-stu-id="a5793-426">Objectives</span></span>

* <span data-ttu-id="a5793-427">깊이 "매직 Windows"를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-427">Add depth to "Magic Windows".</span></span>
* <span data-ttu-id="a5793-428">가상 세계에 사용자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-428">Bring the user into the virtual world.</span></span>

### <a name="magic-windows"></a><span data-ttu-id="a5793-429">매직 Windows</span><span class="sxs-lookup"><span data-stu-id="a5793-429">Magic Windows</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="a5793-430">주요 개념</span><span class="sxs-lookup"><span data-stu-id="a5793-430">Key Concepts</span></span>

* <span data-ttu-id="a5793-431">숨겨진된를 환경에 뷰를 만들기, 멋진 시각입니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-431">Creating views into a hidden world, is visually compelling.</span></span>
* <span data-ttu-id="a5793-432">숨겨진된 전 세계 근처를 홀로그램 또는 사용자가 오디오 효과 추가 하 여 현실성을 향상 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-432">Enhance realism by adding audio effects when a hologram or the user is near the hidden world.</span></span>

#### <a name="instructions"></a><span data-ttu-id="a5793-433">지침</span><span class="sxs-lookup"><span data-stu-id="a5793-433">Instructions</span></span>

* <span data-ttu-id="a5793-434">에 **계층 구조** 패널에서 확장 **HologramCollection** 선택한 **지 하**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-434">In the **Hierarchy** panel, expand **HologramCollection** and select **Underworld**.</span></span>
* <span data-ttu-id="a5793-435">확장 **지 하** 선택한 **VoiceSource**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-435">Expand **Underworld** and select **VoiceSource**.</span></span>
* <span data-ttu-id="a5793-436">에 **검사기** 패널에서 **구성 요소 추가** 추가한 **사용자 음성 효과**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-436">In the **Inspector** panel, click **Add Component** and add **User Voice Effect**.</span></span>

<span data-ttu-id="a5793-437">**AudioSource** 구성 요소에 추가할 **VoiceSource**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-437">An **AudioSource** component will be added to **VoiceSource**.</span></span>

* <span data-ttu-id="a5793-438">**AudioSource**설정 **출력** 하 **UserVoice (Mixer)** 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-438">In **AudioSource**, set **Output** to **UserVoice (Mixer)**.</span></span>
* <span data-ttu-id="a5793-439">확인 합니다 **Spatialize** 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-439">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="a5793-440">끌어서를 **공간 Blend** 슬라이더에 이르는 **3D**, 또는 입력 **1** 편집 상자에서.</span><span class="sxs-lookup"><span data-stu-id="a5793-440">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>
* <span data-ttu-id="a5793-441">확장 **3D 소리 설정**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-441">Expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="a5793-442">설정할 **doppler가 수준** 하 **0**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-442">Set **Doppler Level** to **0**.</span></span>
* <span data-ttu-id="a5793-443">**사용자 음성 효과**설정 **부모 개체** 하는 **지 하** 장면에서.</span><span class="sxs-lookup"><span data-stu-id="a5793-443">In **User Voice Effect**, set **Parent Object** to the **Underworld** from the scene.</span></span>
* <span data-ttu-id="a5793-444">설정할 **최대 거리** 하 **1**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-444">Set **Max Distance** to **1**.</span></span>

<span data-ttu-id="a5793-445">설정 **최대 거리** 지시 **사용자 음성 효과** 얼마나 근접 사용자 해야 부모 개체에 효과 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-445">Setting **Max Distance** tells **User Voice Effect** how close the user must be to the parent object before the effect is enabled.</span></span>

* <span data-ttu-id="a5793-446">**사용자 음성 효과**를 확장 하 고 **코러스 매개 변수**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-446">In **User Voice Effect**, expand **Chorus Parameters**.</span></span>
* <span data-ttu-id="a5793-447">설정할 **깊이** 하 **0.1**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-447">Set **Depth** to **0.1**.</span></span>
* <span data-ttu-id="a5793-448">설정 **볼륨 1 탭**, **2 볼륨 탭** 및 **3 볼륨 탭** 하 **0.8**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-448">Set **Tap 1 Volume**, **Tap 2 Volume** and **Tap 3 Volume** to **0.8**.</span></span>
* <span data-ttu-id="a5793-449">설정할 **원래 소리 볼륨** 하 **0.5**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-449">Set **Original Sound Volume** to **0.5**.</span></span>

<span data-ttu-id="a5793-450">Unity의 매개 변수를 구성 하는 이전 설정이 **AudioChorusFilter** 사용자의 음성에 다양 한 기능을 추가 하는 데 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-450">The previous settings configure the parameters of the Unity **AudioChorusFilter** used to add richness to the user's voice.</span></span>

* <span data-ttu-id="a5793-451">**사용자 음성 효과**를 확장 하 고 **Echo 매개 변수**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-451">In **User Voice Effect**, expand **Echo Parameters**.</span></span>
* <span data-ttu-id="a5793-452">설정할 **지연** 에 **300**</span><span class="sxs-lookup"><span data-stu-id="a5793-452">Set **Delay** to **300**</span></span>
* <span data-ttu-id="a5793-453">설정할 **비율 Decay** 하 **0.2**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-453">Set **Decay Ratio** to **0.2**.</span></span>
* <span data-ttu-id="a5793-454">설정할 **원래 소리 볼륨** 하 **0**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-454">Set **Original Sound Volume** to **0**.</span></span>

<span data-ttu-id="a5793-455">Unity의 매개 변수를 구성 하는 이전 설정이 **AudioEchoFilter** 에코 하려면 사용자의 음성 발생 하는 데 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-455">The previous settings configure the parameters of the Unity **AudioEchoFilter** used to cause the user's voice to echo.</span></span>

<span data-ttu-id="a5793-456">사용자 음성 효과 스크립트는 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-456">The User Voice Effect script is responsible for:</span></span>

* <span data-ttu-id="a5793-457">사용자 사이의 간격을 측정 하며 **GameObject** 연결 된 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-457">Measuring the distance between the user and the **GameObject** to which the script is attached.</span></span>
* <span data-ttu-id="a5793-458">사용자가 연결 되어 있는지 여부를 확인 합니다 **GameObject**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-458">Determining whether or not the user is facing the **GameObject**.</span></span>

<span data-ttu-id="a5793-459">GameObject를 하도록 효과 대 한 거리에 관계 없이 사용자 경험 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-459">The user must be facing the GameObject, regardless of distance, for the effect to be enabled.</span></span>

* <span data-ttu-id="a5793-460">적용 하 고 구성를 **AudioChorusFilter** 와 **AudioEchoFilter** 에 **AudioSource**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-460">Applying and configuring an **AudioChorusFilter** and an **AudioEchoFilter** to the **AudioSource**.</span></span>
* <span data-ttu-id="a5793-461">필터를 사용 하지 않도록 설정 하 여 효과 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-461">Disabling the effect by disabling the filters.</span></span>

<span data-ttu-id="a5793-462">사용자 음성 효과에서 Mic Stream 선택기 구성 요소를 사용 하는 [MixedRealityToolkit Unity에 대 한](https://github.com/Microsoft/MixedRealityToolkit-Unity)하 고품질 음성 스트림을 선택 하 고 Unity의 오디오 시스템으로 라우팅합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-462">User Voice Effect uses the Mic Stream Selector component, from the [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), to select the high quality voice stream and route it into Unity's audio system.</span></span>

* <span data-ttu-id="a5793-463">에 **계층 구조** 패널에서 **관리자**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-463">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="a5793-464">에 **검사기** 패널에서 확장 **음성 입력 처리기**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-464">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="a5793-465">**음성 입력 처리기**를 확장 하 고 **표시 지 하**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-465">In **Speech Input Handler**, expand **Show Underworld**.</span></span>
* <span data-ttu-id="a5793-466">변경 **함수가** 하 **UnderworldBase.OnEnable**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-466">Change **No Function** to **UnderworldBase.OnEnable**.</span></span>

![키워드: 지 하 표시](images/showunderworld.png)

* <span data-ttu-id="a5793-468">확장 **지 하 숨기기**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-468">Expand **Hide Underworld**.</span></span>
* <span data-ttu-id="a5793-469">변경 **함수가** 하 **UnderworldBase.OnDisable**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-469">Change **No Function** to **UnderworldBase.OnDisable**.</span></span>

![키워드: 지 하 숨기기](images/hideunderworld.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="a5793-471">빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="a5793-471">Build and Deploy</span></span>

* <span data-ttu-id="a5793-472">이전과 마찬가지로 Unity에서 프로젝트를 빌드하고 Visual Studio에서 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-472">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="a5793-473">응용 프로그램 후 배포 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-473">After the application is deployed:</span></span>

* <span data-ttu-id="a5793-474">얼굴 화면 (wall, floor, 테이블) 및 say *"표시 지 하"* 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-474">Face a surface (wall, floor, table) and say *"Show Underworld"*.</span></span>

<span data-ttu-id="a5793-475">표시할 지 하 세계 및 다른 모든 홀로그램 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-475">The underworld will be shown and all other holograms will be hidden.</span></span> <span data-ttu-id="a5793-476">지 하 세계에 표시 되지 않는다면 하는 경우에 실제 화면 접하는 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-476">If you do not see the underworld, ensure that you are facing a real-world surface.</span></span>

* <span data-ttu-id="a5793-477">지 하 홀로그램 1 미터 내 있으며 이야기를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-477">Approach within 1 meter of the underworld hologram and start talking.</span></span>

<span data-ttu-id="a5793-478">오디오 효과 음성에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-478">There are now audio effects applied to your voice!</span></span>

* <span data-ttu-id="a5793-479">지 하에서 설정 하 고 효과 더 이상 적용 되는 방식을 확인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-479">Turn away from the underworld and notice how the effect is no longer applied.</span></span>
* <span data-ttu-id="a5793-480">예를 들어 *"지 하 숨기기"* 지 하 세계를 숨기려면 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-480">Say *"Hide Underworld"* to hide the underworld.</span></span>

<span data-ttu-id="a5793-481">지 하 세계 숨겨집니다 및 이전이 숨긴된 홀로그램 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-481">The underworld will be hidden and the previously hidden holograms will reappear.</span></span>

## <a name="the-end"></a><span data-ttu-id="a5793-482">끝</span><span class="sxs-lookup"><span data-stu-id="a5793-482">The End</span></span>

<span data-ttu-id="a5793-483">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-483">Congratulations!</span></span> <span data-ttu-id="a5793-484">이제 완료 **MR 공간 220: 공간 소리**합니다.</span><span class="sxs-lookup"><span data-stu-id="a5793-484">You have now completed **MR Spatial 220: Spatial sound**.</span></span>

<span data-ttu-id="a5793-485">전 세계에 수신 대기 하 고 경험에 활기를 소리로!</span><span class="sxs-lookup"><span data-stu-id="a5793-485">Listen to the world and bring your experiences to life with sound!</span></span>
