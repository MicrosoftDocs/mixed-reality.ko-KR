---
title: MR 공간 230-공간 매핑
description: Unity, Visual Studio 및 HoloLens를 사용 하 여이 코딩 연습을 수행 하 여 공간 매핑 개념에 대 한 자세한 내용을 알아보세요.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit, 아카데미, 자습서, 공간 매핑, 표면 재구성, 메시
ms.openlocfilehash: ed58676a0fda660cc6b4c197239aeb53166baa4d
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993557"
---
>[!NOTE]
><span data-ttu-id="372cc-104">혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="372cc-105">따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="372cc-106">이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="372cc-107">지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="372cc-108">향후에는 HoloLens 2를 개발 하는 방법을 보여 주는 새 자습서 시리즈를 게시할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="372cc-109">이 알림은 게시 될 때 해당 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-spatial-230-spatial-mapping"></a><span data-ttu-id="372cc-110">MR 공간 230: 공간 매핑</span><span class="sxs-lookup"><span data-stu-id="372cc-110">MR Spatial 230: Spatial mapping</span></span>

<span data-ttu-id="372cc-111">[공간 매핑은](spatial-mapping.md) 환경에 대 한 holograms을 교육 하 여 실제 세계와 가상 세계를 함께 결합 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-111">[Spatial mapping](spatial-mapping.md) combines the real world and virtual world together by teaching holograms about the environment.</span></span> <span data-ttu-id="372cc-112">MR 공간 230 (Project Planetarium)에서 다음을 수행 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-112">In MR Spatial 230 (Project Planetarium) we'll learn how to:</span></span>

* <span data-ttu-id="372cc-113">환경을 검색 하 고 HoloLens에서 개발 컴퓨터로 데이터를 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-113">Scan the environment and transfer data from the HoloLens to your development machine.</span></span>
* <span data-ttu-id="372cc-114">셰이더를 탐색 하 고 공간을 시각화 하는 데 사용 하는 방법을 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="372cc-114">Explore shaders and learn how to use them for visualizing your space.</span></span>
* <span data-ttu-id="372cc-115">메시 처리를 사용 하 여 대화방 메시를 간단한 평면으로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-115">Break down the room mesh into simple planes using mesh processing.</span></span>
* <span data-ttu-id="372cc-116">[MR 기본 사항 101](holograms-101.md)에서 배운 배치 기술 외에도, 환경에서 홀로그램을 배치할 수 있는 위치에 대 한 피드백을 제공 하세요.</span><span class="sxs-lookup"><span data-stu-id="372cc-116">Go beyond the placement techniques we learned in [MR Basics 101](holograms-101.md), and provide feedback about where a hologram can be placed in the environment.</span></span>
* <span data-ttu-id="372cc-117">폐색 효과를 탐색 하 여 홀로그램이 실제 개체 뒤에 있을 때 x-레이 비전을 사용 하 여 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-117">Explore occlusion effects, so when your hologram is behind a real-world object, you can still see it with x-ray vision!</span></span>

>[!VIDEO https://www.youtube.com/embed/NSNYRkUX6Mw]

## <a name="device-support"></a><span data-ttu-id="372cc-118">장치 지원</span><span class="sxs-lookup"><span data-stu-id="372cc-118">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="372cc-119">과정</span><span class="sxs-lookup"><span data-stu-id="372cc-119">Course</span></span></th><th style="width:150px"> <span data-ttu-id="372cc-120"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="372cc-120"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="372cc-121"><a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="372cc-121"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="372cc-122">MR 공간 230: 공간 매핑</span><span class="sxs-lookup"><span data-stu-id="372cc-122">MR Spatial 230: Spatial mapping</span></span></td><td style="text-align: center;"> <span data-ttu-id="372cc-123">✔️</span><span class="sxs-lookup"><span data-stu-id="372cc-123">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="372cc-124">시작하기 전 주의 사항</span><span class="sxs-lookup"><span data-stu-id="372cc-124">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="372cc-125">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="372cc-125">Prerequisites</span></span>

* <span data-ttu-id="372cc-126">올바른 [도구로](install-the-tools.md)구성 된 WINDOWS 10 PC입니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-126">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="372cc-127">몇 가지 C# 기본적인 프로그래밍 기능.</span><span class="sxs-lookup"><span data-stu-id="372cc-127">Some basic C# programming ability.</span></span>
* <span data-ttu-id="372cc-128">[MR 기본 101](holograms-101.md)를 완료 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-128">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="372cc-129">[개발용으로 구성 된](using-visual-studio.md#enabling-developer-mode)HoloLens 장치입니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-129">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="372cc-130">프로젝트 파일</span><span class="sxs-lookup"><span data-stu-id="372cc-130">Project files</span></span>

* <span data-ttu-id="372cc-131">프로젝트에 필요한 [파일](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) 을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-131">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) required by the project.</span></span><span data-ttu-id="372cc-132"> Unity 2017.2 이상이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-132"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="372cc-133">Unity 5.6 지원이 계속 필요한 경우 [이 릴리스](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip)를 사용 하세요.</span><span class="sxs-lookup"><span data-stu-id="372cc-133">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip).</span></span>
  * <span data-ttu-id="372cc-134">Unity 5.5 지원이 계속 필요한 경우 [이 릴리스](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip)를 사용 하세요.</span><span class="sxs-lookup"><span data-stu-id="372cc-134">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip).</span></span>
  * <span data-ttu-id="372cc-135">Unity 5.4 지원이 계속 필요한 경우 [이 릴리스](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip)를 사용 하세요.</span><span class="sxs-lookup"><span data-stu-id="372cc-135">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip).</span></span>
* <span data-ttu-id="372cc-136">바탕 화면 또는 기타 쉬운 위치에 파일을 보관 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-136">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="372cc-137">다운로드 하기 전에 소스 코드를 확인 하려는 경우 [GitHub에서 사용할 수](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping)있습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping).</span></span>

### <a name="notes"></a><span data-ttu-id="372cc-138">참고</span><span class="sxs-lookup"><span data-stu-id="372cc-138">Notes</span></span>

* <span data-ttu-id="372cc-139">Visual Studio의 "내 코드만 사용"은 코드에서 중단점을 적중 하기 위해 디버깅 > 도구 > 옵션에서 비활성화 (*선택 취소*) 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-139">"Enable Just My Code" in Visual Studio needs to be disabled (*unchecked*) under Tools > Options > Debugging in order to hit breakpoints in your code.</span></span>

## <a name="unity-setup"></a><span data-ttu-id="372cc-140">Unity 설치</span><span class="sxs-lookup"><span data-stu-id="372cc-140">Unity setup</span></span>

>[!VIDEO https://www.youtube.com/embed/y2Y4LhK6TEM]

* <span data-ttu-id="372cc-141">**Unity**를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-141">Start **Unity**.</span></span>
* <span data-ttu-id="372cc-142">새로 만들기 **를 선택 하** 여 새 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-142">Select **New** to create a new project.</span></span>
* <span data-ttu-id="372cc-143">프로젝트 이름을 **Planetarium**로 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-143">Name the project **Planetarium**.</span></span>
* <span data-ttu-id="372cc-144">**3d** 설정이 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-144">Verify that the **3D** setting is selected.</span></span>
* <span data-ttu-id="372cc-145">**Create Project**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-145">Click **Create Project**.</span></span>
* <span data-ttu-id="372cc-146">Unity가 시작 되 면 **편집 > 프로젝트 설정 > 플레이어**로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-146">Once Unity launches, go to **Edit > Project Settings > Player**.</span></span>
* <span data-ttu-id="372cc-147">**검사기** 패널에서 녹색 **Windows 스토어** 아이콘을 찾아 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-147">In the **Inspector** panel, find and select the green **Windows Store** icon.</span></span>
* <span data-ttu-id="372cc-148">**기타 설정**을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-148">Expand **Other Settings**.</span></span>
* <span data-ttu-id="372cc-149">**렌더링** 섹션에서 **가상 현실 지원** 옵션을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-149">In the **Rendering** section, check the **Virtual Reality Supported** option.</span></span>
* <span data-ttu-id="372cc-150">**Windows Holographic** 가 **가상 현실 sdk**목록에 나타나는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-150">Verify that **Windows Holographic** appears in the list of **Virtual Reality SDKs**.</span></span> <span data-ttu-id="372cc-151">그렇지 않은 경우 목록 아래쪽 **+** 의 단추를 선택 하 고 **Windows Holographic**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-151">If not, select the **+** button at the bottom of the list and choose **Windows Holographic**.</span></span>
* <span data-ttu-id="372cc-152">**게시 설정**을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-152">Expand **Publishing Settings**.</span></span>
* <span data-ttu-id="372cc-153">**기능** 섹션에서 다음 설정을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-153">In the **Capabilities** section, check the following settings:</span></span>
    * <span data-ttu-id="372cc-154">InternetClientServer</span><span class="sxs-lookup"><span data-stu-id="372cc-154">InternetClientServer</span></span>
    * <span data-ttu-id="372cc-155">PrivateNetworkClientServer</span><span class="sxs-lookup"><span data-stu-id="372cc-155">PrivateNetworkClientServer</span></span>
    * <span data-ttu-id="372cc-156">마이크</span><span class="sxs-lookup"><span data-stu-id="372cc-156">Microphone</span></span>
    * <span data-ttu-id="372cc-157">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="372cc-157">SpatialPerception</span></span>
* <span data-ttu-id="372cc-158">**편집 > 프로젝트 설정 > 품질** 로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-158">Go to **Edit > Project Settings > Quality**</span></span>
* <span data-ttu-id="372cc-159">**검사기** 패널의 Windows 스토어 아이콘에서 ' default ' 행 아래의 검은색 드롭다운 화살표를 선택 하 고 기본 설정을 **매우 낮음**으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-159">In the **Inspector** panel, under the Windows Store icon, select the black drop-down arrow under the 'Default' row and change the default setting to **Very Low**.</span></span>
* <span data-ttu-id="372cc-160">**자산 > 가져오기 패키지 > 사용자 지정 패키지**로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-160">Go to **Assets > Import Package > Custom Package**.</span></span>
* <span data-ttu-id="372cc-161">**. ..\Holographicacademy-holograms-230-SpatialMapping\Starting** 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-161">Navigate to the **...\HolographicAcademy-Holograms-230-SpatialMapping\Starting** folder.</span></span>
* <span data-ttu-id="372cc-162">**Planetarium. unitypackage**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-162">Click on **Planetarium.unitypackage**.</span></span>
* <span data-ttu-id="372cc-163">**열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-163">Click **Open**.</span></span>
* <span data-ttu-id="372cc-164">**Unity 패키지 가져오기** 창이 표시 되 면 **가져오기** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-164">An **Import Unity Package** window should appear, click on the **Import** button.</span></span>
* <span data-ttu-id="372cc-165">Unity가이 프로젝트를 완료 하는 데 필요한 모든 자산을 가져올 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-165">Wait for Unity to import all of the assets that we will need to complete this project.</span></span>
* <span data-ttu-id="372cc-166">**계층** 패널에서 **주 카메라**를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-166">In the **Hierarchy** panel, delete the **Main Camera**.</span></span>
* <span data-ttu-id="372cc-167">**프로젝트** 패널의 **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** 폴더에서 **주 카메라** 개체를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-167">In the **Project** panel, **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** folder, find the **Main Camera** object.</span></span>
* <span data-ttu-id="372cc-168">**주 카메라** Prefab을 **계층** 패널로 끌어다 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-168">Drag and drop the **Main Camera** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="372cc-169">**계층** 패널에서 **방향 광원** 개체를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-169">In the **Hierarchy** panel, delete the **Directional Light** object.</span></span>
* <span data-ttu-id="372cc-170">**프로젝트** 패널의 **Holograms** 폴더에서 **Cursor** 개체를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-170">In the **Project** panel, **Holograms** folder, locate the **Cursor** object.</span></span>
* <span data-ttu-id="372cc-171">**커서** Prefab을 **계층**으로 끌어 & 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-171">Drag & drop the **Cursor** prefab into the **Hierarchy**.</span></span>
* <span data-ttu-id="372cc-172">**계층** 패널에서 **Cursor** 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-172">In the **Hierarchy** panel, select the **Cursor** object.</span></span>
* <span data-ttu-id="372cc-173">**검사기** 패널에서 **계층** 드롭다운을 클릭 하 고 **계층 편집 ...** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-173">In the **Inspector** panel, click the **Layer** drop-down and select **Edit Layers...**.</span></span>
* <span data-ttu-id="372cc-174">**사용자 계층 31** 의 이름을 "**SpatialMapping**"로 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-174">Name **User Layer 31** as "**SpatialMapping**".</span></span>
* <span data-ttu-id="372cc-175">새 장면 저장: **파일 > 다른 이름으로 장면 저장 ...**</span><span class="sxs-lookup"><span data-stu-id="372cc-175">Save the new scene: **File > Save Scene As...**</span></span>
* <span data-ttu-id="372cc-176">**새 폴더** 를 클릭 하 고 폴더 이름을 **장면**으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-176">Click **New Folder** and name the folder **Scenes**.</span></span>
* <span data-ttu-id="372cc-177">파일 이름을 "**Planetarium**"로 하 고 해당 파일을 **백그라운드** 폴더에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-177">Name the file "**Planetarium**" and save it in the **Scenes** folder.</span></span>

## <a name="chapter-1---scanning"></a><span data-ttu-id="372cc-178">1 장-검색</span><span class="sxs-lookup"><span data-stu-id="372cc-178">Chapter 1 - Scanning</span></span>

>[!VIDEO https://www.youtube.com/embed/888oW51z_cE]

<span data-ttu-id="372cc-179">**목표로**</span><span class="sxs-lookup"><span data-stu-id="372cc-179">**Objectives**</span></span>
* <span data-ttu-id="372cc-180">SurfaceObserver 및 해당 설정이 경험 및 성능에 미치는 영향에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-180">Learn about the SurfaceObserver and how its settings impact experience and performance.</span></span>
* <span data-ttu-id="372cc-181">회의실의 메시를 수집 하는 방 스캔 환경을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-181">Create a room scanning experience to collect the meshes of your room.</span></span>

<span data-ttu-id="372cc-182">**지침**</span><span class="sxs-lookup"><span data-stu-id="372cc-182">**Instructions**</span></span>
* <span data-ttu-id="372cc-183">**프로젝트** 패널 **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** 폴더에서 **SpatialMapping** prefab를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-183">In the **Project** panel **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** folder, find the **SpatialMapping** prefab.</span></span>
* <span data-ttu-id="372cc-184">**SpatialMapping** Prefab를 **계층** 패널로 끌어 & 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-184">Drag & drop the **SpatialMapping** prefab into the **Hierarchy** panel.</span></span>

<span data-ttu-id="372cc-185">**빌드 및 배포 (1 부)**</span><span class="sxs-lookup"><span data-stu-id="372cc-185">**Build and Deploy (part 1)**</span></span>
* <span data-ttu-id="372cc-186">Unity에서 **파일 > 빌드 설정**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-186">In Unity, select **File > Build Settings**.</span></span>
* <span data-ttu-id="372cc-187">열려 있는 장면 **추가** 를 클릭 하 여 **Planetarium** 장면을 빌드에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-187">Click **Add Open Scenes** to add the **Planetarium** scene to the build.</span></span>
* <span data-ttu-id="372cc-188">**플랫폼** 목록에서 **유니버설 Windows 플랫폼** 을 선택 하 고 **플랫폼 전환**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-188">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="372cc-189">**SDK** 를 **Universal 10** 및 **UWP 빌드 형식** 으로 **D3D**로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-189">Set **SDK** to **Universal 10** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="372cc-190">**Unity C# 프로젝트**를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-190">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="372cc-191">**빌드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-191">Click **Build**.</span></span>
* <span data-ttu-id="372cc-192">"App" 이라는 **새 폴더** 를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-192">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="372cc-193">단일 **앱** 폴더를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-193">Single click the **App** folder.</span></span>
* <span data-ttu-id="372cc-194">**폴더 선택** 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-194">Press the **Select Folder** button.</span></span>
* <span data-ttu-id="372cc-195">Unity 작성이 완료 되 면 파일 탐색기 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-195">When Unity is done building, a File Explorer window will appear.</span></span>
* <span data-ttu-id="372cc-196">**앱** 폴더를 두 번 클릭 하 여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-196">Double-click on the **App** folder to open it.</span></span>
* <span data-ttu-id="372cc-197">**Planetarium** 을 두 번 클릭 하 여 Visual Studio에서 프로젝트를 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-197">Double-click on **Planetarium.sln** to load the project in Visual Studio.</span></span>
* <span data-ttu-id="372cc-198">Visual Studio에서 맨 위 도구 모음을 사용 하 여 구성을 **릴리스**로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-198">In Visual Studio, use the top toolbar to change the Configuration to **Release**.</span></span>
* <span data-ttu-id="372cc-199">플랫폼을 **x 86**으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-199">Change the Platform to **x86**.</span></span>
* <span data-ttu-id="372cc-200">' 로컬 컴퓨터 ' 오른쪽에 있는 드롭다운 화살표를 클릭 하 고 **원격 컴퓨터**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-200">Click on the drop-down arrow to the right of 'Local Machine', and select **Remote Machine**.</span></span>
* <span data-ttu-id="372cc-201">주소 필드에 [장치의 IP 주소](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) 를 입력 하 고 인증 모드를 **유니버설 (암호화 되지 않은 프로토콜)** 로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-201">Enter [your device's IP address](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) in the Address field and change Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span>
* <span data-ttu-id="372cc-202">**디버그를 클릭 하 > 디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-202">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="372cc-203">Visual Studio에서 빌드 및 배포 상태에 대 한 **출력** 패널을 시청 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-203">Watch the **Output** panel in Visual Studio for build and deploy status.</span></span>
* <span data-ttu-id="372cc-204">앱이 배포 된 후에는 공간을 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-204">Once your app has deployed, walk around the room.</span></span> <span data-ttu-id="372cc-205">검은색 및 흰색 와이어 프레임 메시를 포함 하는 주변 서피스가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-205">You will see the surrounding surfaces covered by black and white wireframe meshes.</span></span>
* <span data-ttu-id="372cc-206">주변을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-206">Scan your surroundings.</span></span> <span data-ttu-id="372cc-207">벽, 최대값이 및 층을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-207">Be sure to look at walls, ceilings, and floors.</span></span>

<span data-ttu-id="372cc-208">**빌드 및 배포 (2 부)**</span><span class="sxs-lookup"><span data-stu-id="372cc-208">**Build and Deploy (part 2)**</span></span>

<span data-ttu-id="372cc-209">이제 공간 매핑이 성능에 영향을 줄 수 있는 방법을 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-209">Now let's explore how Spatial Mapping can affect performance.</span></span>
* <span data-ttu-id="372cc-210">Unity에서 **Window > Profiler**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-210">In Unity, select **Window > Profiler**.</span></span>
* <span data-ttu-id="372cc-211">**> GPU 추가 Profiler**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-211">Click **Add Profiler > GPU**.</span></span>
* <span data-ttu-id="372cc-212">**활성 프로파일러 > <Enter IP>** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-212">Click **Active Profiler > <Enter IP>**.</span></span>
* <span data-ttu-id="372cc-213">HoloLens의 **IP 주소** 를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-213">Enter the **IP address** of your HoloLens.</span></span>
* <span data-ttu-id="372cc-214">**연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-214">Click **Connect**.</span></span>
* <span data-ttu-id="372cc-215">GPU에서 프레임을 렌더링 하는 데 걸리는 시간 (밀리초)을 관찰 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-215">Observe the number of milliseconds it takes for the GPU to render a frame.</span></span>
* <span data-ttu-id="372cc-216">장치에서 응용 프로그램이 실행 되는 것을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-216">Stop the application from running on the device.</span></span>
* <span data-ttu-id="372cc-217">Visual Studio로 돌아가서 **SpatialMappingObserver.cs**을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-217">Return to Visual Studio and open **SpatialMappingObserver.cs**.</span></span> <span data-ttu-id="372cc-218">이 파일은 어셈블리-CSharp (유니버설 Windows) 프로젝트의 HoloToolkit\SpatialMapping 폴더에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-218">You will find it in the HoloToolkit\SpatialMapping folder of the Assembly-CSharp (Universal Windows) project.</span></span>
* <span data-ttu-id="372cc-219">**활성 ()** 함수를 찾고 다음 코드 줄을 추가 합니다. **TrianglesPerCubicMeter = 1200;**</span><span class="sxs-lookup"><span data-stu-id="372cc-219">Find the **Awake()** function, and add the following line of code: **TrianglesPerCubicMeter = 1200;**</span></span>
* <span data-ttu-id="372cc-220">장치에 프로젝트를 다시 배포 하 고 **프로파일러를 다시 연결**합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-220">Re-deploy the project to your device, and then **reconnect the profiler**.</span></span> <span data-ttu-id="372cc-221">프레임을 렌더링 하는 시간 (밀리초)의 변경 내용을 관찰 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-221">Observe the change in the number of milliseconds to render a frame.</span></span>
* <span data-ttu-id="372cc-222">장치에서 응용 프로그램이 실행 되는 것을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-222">Stop the application from running on the device.</span></span>

<span data-ttu-id="372cc-223">**Unity에서 저장 및 로드**</span><span class="sxs-lookup"><span data-stu-id="372cc-223">**Save and load in Unity**</span></span>

<span data-ttu-id="372cc-224">마지막으로 대화방 메시를 저장 하 고 Unity에 로드 하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-224">Finally, let's save our room mesh and load it into Unity.</span></span>
* <span data-ttu-id="372cc-225">Visual Studio로 돌아가서 이전 섹션에서 **TrianglesPerCubicMeter** **()** 함수에 추가한 줄을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-225">Return to Visual Studio and remove the **TrianglesPerCubicMeter** line that you added in the **Awake()** function during the previous section.</span></span>
* <span data-ttu-id="372cc-226">장치에 프로젝트를 다시 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-226">Redeploy the project to your device.</span></span> <span data-ttu-id="372cc-227">이제 입방 미터 당 **500** 삼각형으로 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-227">We should now be running with **500** triangles per cubic meter.</span></span>
* <span data-ttu-id="372cc-228">브라우저를 열고 HoloLens IPAddress를 입력 하 여 **Windows 장치 포털로**이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-228">Open a browser and enter in your HoloLens IPAddress to navigate to the **Windows Device Portal**.</span></span>
* <span data-ttu-id="372cc-229">왼쪽 패널에서 **3D 보기** 옵션을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-229">Select the **3D View** option in the left panel.</span></span>
* <span data-ttu-id="372cc-230">**표면 재구성** 아래에서 **업데이트** 단추를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-230">Under **Surface reconstruction** select the **Update** button.</span></span>
* <span data-ttu-id="372cc-231">HoloLens에서 스캔 한 영역이 표시 창에 표시 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-231">Watch as the areas that you have scanned on your HoloLens appear in the display window.</span></span>
* <span data-ttu-id="372cc-232">회의실 검색을 저장 하려면 **저장** 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-232">To save your room scan, press the **Save** button.</span></span>
* <span data-ttu-id="372cc-233">**다운로드** 폴더를 열어서 저장 된 **대화방 모델을**찾습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-233">Open your **Downloads** folder to find the saved room model **SRMesh.obj**.</span></span>
* <span data-ttu-id="372cc-234">**Srmesh. .obj** 를 Unity 프로젝트의 **자산** 폴더에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-234">Copy **SRMesh.obj** to the **Assets** folder of your Unity project.</span></span>
* <span data-ttu-id="372cc-235">Unity의 **계층** 패널에서 **SpatialMapping** 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-235">In Unity, select the **SpatialMapping** object in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="372cc-236">**개체 표면 관찰자 (스크립트)** 구성 요소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-236">Locate the **Object Surface Observer (Script)** component.</span></span>
* <span data-ttu-id="372cc-237">**방 모델** 속성의 오른쪽에 있는 원을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-237">Click the circle to the right of the **Room Model** property.</span></span>
* <span data-ttu-id="372cc-238">**Srmesh** 개체를 찾아 선택한 다음 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-238">Find and select the **SRMesh** object and then close the window.</span></span>
* <span data-ttu-id="372cc-239">이제 **검사기** 패널의 **Room 모델** 속성이 **srmesh**로 설정 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-239">Verify that the **Room Model** property in the **Inspector** panel is now set to **SRMesh**.</span></span>
* <span data-ttu-id="372cc-240">**재생** 단추를 눌러 Unity의 미리 보기 모드를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-240">Press the **Play** button to enter Unity's preview mode.</span></span>
* <span data-ttu-id="372cc-241">SpatialMapping 구성 요소는 저장 된 대화방 모델에서 메시를 로드 하므로 Unity에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-241">The SpatialMapping component will load the meshes from the saved room model so you can use them in Unity.</span></span>
* <span data-ttu-id="372cc-242">**장면** 보기로 전환 하 여 와이어 프레임 셰이더에 표시 되는 모든 대화방 모델을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-242">Switch to **Scene** view to see all of your room model displayed with the wireframe shader.</span></span>
* <span data-ttu-id="372cc-243">**재생** 단추를 다시 클릭 하 여 미리 보기 모드를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-243">Press the **Play** button again to exit preview mode.</span></span>

<span data-ttu-id="372cc-244">**참고:** 다음 번에 Unity에서 미리 보기 모드를 입력 하면 기본적으로 저장 된 대화방 메쉬가 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-244">**NOTE:** The next time that you enter preview mode in Unity, it will load the saved room mesh by default.</span></span>

## <a name="chapter-2---visualization"></a><span data-ttu-id="372cc-245">2 장-시각화</span><span class="sxs-lookup"><span data-stu-id="372cc-245">Chapter 2 - Visualization</span></span>

>[!VIDEO https://www.youtube.com/embed/RnkvXl-aXD4]

<span data-ttu-id="372cc-246">**목표로**</span><span class="sxs-lookup"><span data-stu-id="372cc-246">**Objectives**</span></span>
* <span data-ttu-id="372cc-247">셰이더의 기본 사항에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-247">Learn the basics of shaders.</span></span>
* <span data-ttu-id="372cc-248">주변을 시각화 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-248">Visualize your surroundings.</span></span>

<span data-ttu-id="372cc-249">**지침**</span><span class="sxs-lookup"><span data-stu-id="372cc-249">**Instructions**</span></span>
* <span data-ttu-id="372cc-250">Unity의 **계층 구조** 패널에서 **SpatialMapping** 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-250">In Unity's **Hierarchy** panel, select the **SpatialMapping** object.</span></span>
* <span data-ttu-id="372cc-251">**검사기** 패널에서 **공간 매핑 관리자 (스크립트)** 구성 요소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-251">In the **Inspector** panel, find the **Spatial Mapping Manager (Script)** component.</span></span>
* <span data-ttu-id="372cc-252">**표면 재질** 속성의 오른쪽에 있는 원을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-252">Click the circle to the right of the **Surface Material** property.</span></span>
* <span data-ttu-id="372cc-253">**BlueLinesOnWalls** 재질을 찾아 선택 하 고 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-253">Find and select the **BlueLinesOnWalls** material and close the window.</span></span>
* <span data-ttu-id="372cc-254">**프로젝트** 패널 **셰이더** 폴더에서 **BlueLinesOnWalls** 를 두 번 클릭 하 여 Visual Studio에서 셰이더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-254">In the **Project** panel **Shaders** folder, double-click on **BlueLinesOnWalls** to open the shader in Visual Studio.</span></span>
* <span data-ttu-id="372cc-255">다음 작업을 수행 하는 간단한 픽셀 (꼭 짓 점-조각) 셰이더입니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-255">This is a simple pixel (vertex to fragment) shader, which accomplishes the following tasks:</span></span>
    1. <span data-ttu-id="372cc-256">꼭 짓 점 위치를 세계 공간으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-256">Converts a vertex's location to world space.</span></span>
    2. <span data-ttu-id="372cc-257">꼭 짓 점의 법선을 확인 하 여 픽셀이 세로 인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-257">Checks the vertex's normal to determine if a pixel is vertical.</span></span>
    3. <span data-ttu-id="372cc-258">렌더링할 픽셀의 색을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-258">Sets the color of the pixel for rendering.</span></span>

<span data-ttu-id="372cc-259">**빌드 및 배포**</span><span class="sxs-lookup"><span data-stu-id="372cc-259">**Build and Deploy**</span></span>
* <span data-ttu-id="372cc-260">Unity로 돌아가서 **재생** 을 눌러 미리 보기 모드를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-260">Return to Unity and press **Play** to enter preview mode.</span></span>
* <span data-ttu-id="372cc-261">저장 된 검색 데이터에서 자동으로 로드 되는 실내 메시의 모든 세로 화면에서 파란색 선이 렌더링 됩니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-261">Blue lines will be rendered on all vertical surfaces of the room mesh (which automatically loaded from our saved scanning data).</span></span>
* <span data-ttu-id="372cc-262">**장면** 탭으로 전환 하 여 대화방 보기를 조정 하 고 전체 대화방 메쉬가 Unity에 표시 되는 방식을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-262">Switch to the **Scene** tab to adjust your view of the room and see how the entire room mesh appears in Unity.</span></span>
* <span data-ttu-id="372cc-263">**프로젝트** 패널에서 **재질** 폴더를 찾고 **BlueLinesOnWalls** 재질을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-263">In the **Project** panel, find the **Materials** folder and select the **BlueLinesOnWalls** material.</span></span>
* <span data-ttu-id="372cc-264">일부 속성을 수정 하 고 Unity 편집기에서 변경 내용이 표시 되는 방식을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-264">Modify some properties and see how the changes appear in the Unity editor.</span></span>
    * <span data-ttu-id="372cc-265">**검사기** 패널에서 **LineScale** 값을 조정 하 여 선이 더 두껍게 표시 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-265">In the **Inspector** panel, adjust the **LineScale** value to make the lines appear thicker or thinner.</span></span>
    * <span data-ttu-id="372cc-266">**검사기** 패널에서 선 **per측정기** 값을 조정 하 여 각 벽에 표시 되는 줄 수를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-266">In the **Inspector** panel, adjust the **LinesPerMeter** value to change how many lines appear on each wall.</span></span>
* <span data-ttu-id="372cc-267">**재생** 을 다시 클릭 하 여 미리 보기 모드를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-267">Click **Play** again to exit preview mode.</span></span>
* <span data-ttu-id="372cc-268">HoloLens에 빌드 및 배포 하 고 실제 표면에 셰이더 렌더링이 어떻게 나타나는지 관찰 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-268">Build and deploy to the HoloLens and observe how the shader rendering appears on real surfaces.</span></span>

<span data-ttu-id="372cc-269">Unity는 자료를 미리 보는 많은 작업을 수행 하지만 항상 장치에서 렌더링을 체크 아웃 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-269">Unity does a great job of previewing materials, but it's always a good idea to check-out rendering in the device.</span></span>

## <a name="chapter-3---processing"></a><span data-ttu-id="372cc-270">3 장-처리</span><span class="sxs-lookup"><span data-stu-id="372cc-270">Chapter 3 - Processing</span></span>

>[!VIDEO https://www.youtube.com/embed/kaUKiNiDxwY]

<span data-ttu-id="372cc-271">**목표로**</span><span class="sxs-lookup"><span data-stu-id="372cc-271">**Objectives**</span></span>
* <span data-ttu-id="372cc-272">응용 프로그램에서 사용할 공간 매핑 데이터를 처리 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-272">Learn techniques to process spatial mapping data for use in your application.</span></span>
* <span data-ttu-id="372cc-273">공간 매핑 데이터를 분석 하 여 평면을 찾고 삼각형을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-273">Analyze spatial mapping data to find planes and remove triangles.</span></span>
* <span data-ttu-id="372cc-274">홀로그램 배치에 평면을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-274">Use planes for hologram placement.</span></span>

<span data-ttu-id="372cc-275">**지침**</span><span class="sxs-lookup"><span data-stu-id="372cc-275">**Instructions**</span></span>
* <span data-ttu-id="372cc-276">Unity의 **Project** panel **Holograms** 폴더에서 **SpatialProcessing** 개체를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-276">In Unity's **Project** panel, **Holograms** folder, find the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="372cc-277">**SpatialProcessing** 개체를 **계층** 패널로 끌어 & 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-277">Drag & drop the **SpatialProcessing** object into the **Hierarchy** panel.</span></span>

<span data-ttu-id="372cc-278">SpatialProcessing prefab에는 공간 매핑 데이터를 처리 하기 위한 구성 요소가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-278">The SpatialProcessing prefab includes components for processing the spatial mapping data.</span></span> <span data-ttu-id="372cc-279">**SurfaceMeshesToPlanes.cs** 는 공간 매핑 데이터를 기반으로 평면을 찾아서 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-279">**SurfaceMeshesToPlanes.cs** will find and generate planes based on the spatial mapping data.</span></span> <span data-ttu-id="372cc-280">우리는 응용 프로그램에서 비행기를 사용 하 여 벽, 층 및 최대값이을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-280">We will use planes in our application to represent walls, floors and ceilings.</span></span> <span data-ttu-id="372cc-281">이 prefab에는 공간 매핑 메시에서 꼭 짓 점을 제거할 수 있는 **RemoveSurfaceVertices.cs** 도 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-281">This prefab also includes **RemoveSurfaceVertices.cs** which can remove vertices from the spatial mapping mesh.</span></span> <span data-ttu-id="372cc-282">이를 사용 하 여 메시에 구멍을 만들거나 더 이상 필요 하지 않은 불필요 한 삼각형 (평면을 대신 사용할 수 있음)을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-282">This can be used to create holes in the mesh, or to remove excess triangles that are no longer needed (because planes can be used instead).</span></span>
* <span data-ttu-id="372cc-283">Unity의 **Project** panel **Holograms** 폴더에서 **SpaceCollection** 개체를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-283">In Unity's **Project** panel, **Holograms** folder, find the **SpaceCollection** object.</span></span>
* <span data-ttu-id="372cc-284">**SpaceCollection** 개체를 **계층** 패널로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-284">Drag and drop the **SpaceCollection** object into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="372cc-285">**계층** 패널에서 **SpatialProcessing** 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-285">In the **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="372cc-286">**검사기** 패널에서 **재생 공간 관리자 (스크립트)** 구성 요소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-286">In the **Inspector** panel, find the **Play Space Manager (Script)** component.</span></span>
* <span data-ttu-id="372cc-287">**PlaySpaceManager.cs** 를 두 번 클릭 하 여 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-287">Double-click on **PlaySpaceManager.cs** to open it in Visual Studio.</span></span>

<span data-ttu-id="372cc-288">PlaySpaceManager.cs는 응용 프로그램 관련 코드를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-288">PlaySpaceManager.cs contains application-specific code.</span></span> <span data-ttu-id="372cc-289">이 스크립트에 기능을 추가 하 여 다음 동작을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-289">We will add functionality to this script to enable the following behavior:</span></span>
1. <span data-ttu-id="372cc-290">검색 시간 제한 (10 초)을 초과 하 고 나면 공간 매핑 데이터 수집을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-290">Stop collecting spatial mapping data after we exceed the scanning time limit (10 seconds).</span></span>
2. <span data-ttu-id="372cc-291">공간 매핑 데이터를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-291">Process the spatial mapping data:</span></span>
    1. <span data-ttu-id="372cc-292">SurfaceMeshesToPlanes를 사용 하 여 평면 (벽, 층, 최대값이 등)을 보다 간단 하 게 표현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-292">Use SurfaceMeshesToPlanes to create a simpler representation of the world as planes (walls, floors, ceilings, etc).</span></span>
    2. <span data-ttu-id="372cc-293">평면 경계 내에 있는 표면 삼각형을 제거 하려면 RemoveSurfaceVertices를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-293">Use RemoveSurfaceVertices to remove surface triangles that fall within plane boundaries.</span></span>
3. <span data-ttu-id="372cc-294">전 세계에서 holograms의 컬렉션을 생성 하 고 사용자 가까이에 벽 및 바닥 평면을 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-294">Generate a collection of holograms in the world and place them on wall and floor planes near the user.</span></span>

<span data-ttu-id="372cc-295">PlaySpaceManager.cs에 표시 된 코딩 연습을 완료 하거나 아래에서 완성 된 솔루션으로 스크립트를 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-295">Complete the coding exercises marked in PlaySpaceManager.cs, or replace the script with the finished solution from below:</span></span>

```cs
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;

/// <summary>
/// The SurfaceManager class allows applications to scan the environment for a specified amount of time 
/// and then process the Spatial Mapping Mesh (find planes, remove vertices) after that time has expired.
/// </summary>
public class PlaySpaceManager : Singleton<PlaySpaceManager>
{
    [Tooltip("When checked, the SurfaceObserver will stop running after a specified amount of time.")]
    public bool limitScanningByTime = true;

    [Tooltip("How much time (in seconds) that the SurfaceObserver will run after being started; used when 'Limit Scanning By Time' is checked.")]
    public float scanTime = 30.0f;

    [Tooltip("Material to use when rendering Spatial Mapping meshes while the observer is running.")]
    public Material defaultMaterial;

    [Tooltip("Optional Material to use when rendering Spatial Mapping meshes after the observer has been stopped.")]
    public Material secondaryMaterial;

    [Tooltip("Minimum number of floor planes required in order to exit scanning/processing mode.")]
    public uint minimumFloors = 1;

    [Tooltip("Minimum number of wall planes required in order to exit scanning/processing mode.")]
    public uint minimumWalls = 1;

    /// <summary>
    /// Indicates if processing of the surface meshes is complete.
    /// </summary>
    private bool meshesProcessed = false;

    /// <summary>
    /// GameObject initialization.
    /// </summary>
    private void Start()
    {
        // Update surfaceObserver and storedMeshes to use the same material during scanning.
        SpatialMappingManager.Instance.SetSurfaceMaterial(defaultMaterial);

        // Register for the MakePlanesComplete event.
        SurfaceMeshesToPlanes.Instance.MakePlanesComplete += SurfaceMeshesToPlanes_MakePlanesComplete;
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        // Check to see if the spatial mapping data has been processed
        // and if we are limiting how much time the user can spend scanning.
        if (!meshesProcessed && limitScanningByTime)
        {
            // If we have not processed the spatial mapping data
            // and scanning time is limited...

            // Check to see if enough scanning time has passed
            // since starting the observer.
            if (limitScanningByTime && ((Time.time - SpatialMappingManager.Instance.StartTime) < scanTime))
            {
                // If we have a limited scanning time, then we should wait until
                // enough time has passed before processing the mesh.
            }
            else
            {
                // The user should be done scanning their environment,
                // so start processing the spatial mapping data...

                /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

                // 3.a: Check if IsObserverRunning() is true on the
                // SpatialMappingManager.Instance.
                if(SpatialMappingManager.Instance.IsObserverRunning())
                {
                    // 3.a: If running, Stop the observer by calling
                    // StopObserver() on the SpatialMappingManager.Instance.
                    SpatialMappingManager.Instance.StopObserver();
                }

                // 3.a: Call CreatePlanes() to generate planes.
                CreatePlanes();

                // 3.a: Set meshesProcessed to true.
                meshesProcessed = true;
            }
        }
    }

    /// <summary>
    /// Handler for the SurfaceMeshesToPlanes MakePlanesComplete event.
    /// </summary>
    /// <param name="source">Source of the event.</param>
    /// <param name="args">Args for the event.</param>
    private void SurfaceMeshesToPlanes_MakePlanesComplete(object source, System.EventArgs args)
    {
        /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

        // Collection of floor and table planes that we can use to set horizontal items on.
        List<GameObject> horizontal = new List<GameObject>();

        // Collection of wall planes that we can use to set vertical items on.
        List<GameObject> vertical = new List<GameObject>();

        // 3.a: Get all floor and table planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'horizontal' list.
        horizontal = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Table | PlaneTypes.Floor);

        // 3.a: Get all wall planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'vertical' list.
        vertical = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Wall);

        // Check to see if we have enough horizontal planes (minimumFloors)
        // and vertical planes (minimumWalls), to set holograms on in the world.
        if (horizontal.Count >= minimumFloors && vertical.Count >= minimumWalls)
        {
            // We have enough floors and walls to place our holograms on...

            // 3.a: Let's reduce our triangle count by removing triangles
            // from SpatialMapping meshes that intersect with our active planes.
            // Call RemoveVertices().
            // Pass in all activePlanes found by SurfaceMeshesToPlanes.Instance.
            RemoveVertices(SurfaceMeshesToPlanes.Instance.ActivePlanes);

            // 3.a: We can indicate to the user that scanning is over by
            // changing the material applied to the Spatial Mapping meshes.
            // Call SpatialMappingManager.Instance.SetSurfaceMaterial().
            // Pass in the secondaryMaterial.
            SpatialMappingManager.Instance.SetSurfaceMaterial(secondaryMaterial);

            // 3.a: We are all done processing the mesh, so we can now
            // initialize a collection of Placeable holograms in the world
            // and use horizontal/vertical planes to set their starting positions.
            // Call SpaceCollectionManager.Instance.GenerateItemsInWorld().
            // Pass in the lists of horizontal and vertical planes that we found earlier.
            SpaceCollectionManager.Instance.GenerateItemsInWorld(horizontal, vertical);
        }
        else
        {
            // We do not have enough floors/walls to place our holograms on...

            // 3.a: Re-enter scanning mode so the user can find more surfaces by 
            // calling StartObserver() on the SpatialMappingManager.Instance.
            SpatialMappingManager.Instance.StartObserver();

            // 3.a: Re-process spatial data after scanning completes by
            // re-setting meshesProcessed to false.
            meshesProcessed = false;
        }
    }

    /// <summary>
    /// Creates planes from the spatial mapping surfaces.
    /// </summary>
    private void CreatePlanes()
    {
        // Generate planes based on the spatial map.
        SurfaceMeshesToPlanes surfaceToPlanes = SurfaceMeshesToPlanes.Instance;
        if (surfaceToPlanes != null && surfaceToPlanes.enabled)
        {
            surfaceToPlanes.MakePlanes();
        }
    }

    /// <summary>
    /// Removes triangles from the spatial mapping surfaces.
    /// </summary>
    /// <param name="boundingObjects"></param>
    private void RemoveVertices(IEnumerable<GameObject> boundingObjects)
    {
        RemoveSurfaceVertices removeVerts = RemoveSurfaceVertices.Instance;
        if (removeVerts != null && removeVerts.enabled)
        {
            removeVerts.RemoveSurfaceVerticesWithinBounds(boundingObjects);
        }
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        if (SurfaceMeshesToPlanes.Instance != null)
        {
            SurfaceMeshesToPlanes.Instance.MakePlanesComplete -= SurfaceMeshesToPlanes_MakePlanesComplete;
        }
    }
}
```

<span data-ttu-id="372cc-296">**빌드 및 배포**</span><span class="sxs-lookup"><span data-stu-id="372cc-296">**Build and Deploy**</span></span>
* <span data-ttu-id="372cc-297">HoloLens에 배포 하기 전에 Unity의 **재생** 단추를 눌러 재생 모드로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-297">Before deploying to the HoloLens, press the **Play** button in Unity to enter play mode.</span></span>
* <span data-ttu-id="372cc-298">파일에서 대화방 메시를 로드 한 후에는 공간 매핑 메시에서 처리가 시작 될 때까지 10 초 정도 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-298">After the room mesh is loaded from file, wait for 10 seconds before processing starts on the spatial mapping mesh.</span></span>
* <span data-ttu-id="372cc-299">처리가 완료 되 면 비행기가 바닥, 벽, 천장 등을 나타내는 것 처럼 보입니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-299">When processing is complete, planes will appear to represent the floor, walls, ceiling, etc.</span></span>
* <span data-ttu-id="372cc-300">모든 비행기를 찾은 후에는 카메라 근처의 바닥에 표를 표시 하는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-300">After all of the planes have been found, you should see a solar system appear on a table of floor near the camera.</span></span>
* <span data-ttu-id="372cc-301">두 포스터는 카메라 근처의 벽에도 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-301">Two posters should appear on walls near the camera too.</span></span> <span data-ttu-id="372cc-302">**게임** 모드에서 볼 수 없는 경우 **장면** 탭으로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-302">Switch to the **Scene** tab if you cannot see them in **Game** mode.</span></span>
* <span data-ttu-id="372cc-303">재생 모드를 종료 하려면 **재생** 단추를 다시 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-303">Press the **Play** button again to exit play mode.</span></span>
* <span data-ttu-id="372cc-304">평소 처럼를 빌드하고 HoloLens에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-304">Build and deploy to the HoloLens, as usual.</span></span>
* <span data-ttu-id="372cc-305">공간 매핑 데이터의 검색 및 처리가 완료 될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-305">Wait for scanning and processing of the spatial mapping data to complete.</span></span>
* <span data-ttu-id="372cc-306">비행기가 표시 되 면 세계에서 태양계와 포스터를 찾으려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-306">Once you see planes, try to find the solar system and posters in your world.</span></span>

## <a name="chapter-4---placement"></a><span data-ttu-id="372cc-307">4 장-배치</span><span class="sxs-lookup"><span data-stu-id="372cc-307">Chapter 4 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/Srhtpid1uZc]

<span data-ttu-id="372cc-308">**목표로**</span><span class="sxs-lookup"><span data-stu-id="372cc-308">**Objectives**</span></span>
* <span data-ttu-id="372cc-309">홀로그램이 표면에 맞는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-309">Determine if a hologram will fit on a surface.</span></span>
* <span data-ttu-id="372cc-310">홀로그램을 화면에 맞출 수 없는 경우 사용자에 게 피드백을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-310">Provide feedback to the user when a hologram can/cannot fit on a surface.</span></span>

<span data-ttu-id="372cc-311">**지침**</span><span class="sxs-lookup"><span data-stu-id="372cc-311">**Instructions**</span></span>
* <span data-ttu-id="372cc-312">Unity의 **계층 구조** 패널에서 **SpatialProcessing** 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-312">In Unity's **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="372cc-313">**검사기** 패널에서 **평면 (스크립트) 구성 요소에 대 한 표면 메시** 를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-313">In the **Inspector** panel, find the **Surface Meshes To Planes (Script)** component.</span></span>
* <span data-ttu-id="372cc-314">**그리기 평면** 속성을 **없음** 으로 변경 하 여 선택을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-314">Change the **Draw Planes** property to **Nothing** to clear the selection.</span></span>
* <span data-ttu-id="372cc-315">벽 평면만 렌더링 되도록 **평면 그리기** 속성을 **벽**으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-315">Change the **Draw Planes** property to **Wall**, so that only wall planes will be rendered.</span></span>
* <span data-ttu-id="372cc-316">**프로젝트** 패널의 **Scripts** 폴더에서 **Placeable.cs** 를 두 번 클릭 하 여 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-316">In the **Project** panel, **Scripts** folder, double-click on **Placeable.cs** to open it in Visual Studio.</span></span>

<span data-ttu-id="372cc-317">**동적 배치** 가능 스크립트는 평면 찾기가 완료 된 후 생성 된 포스터 및 프로젝션 상자에 이미 연결 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-317">The **Placeable** script is already attached to the posters and projection box that are created after plane finding completes.</span></span> <span data-ttu-id="372cc-318">코드의 주석 처리를 제거 하기만 하면 됩니다 .이 스크립트는 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-318">All we need to do is uncomment some code, and this script will achieve the following:</span></span>
1. <span data-ttu-id="372cc-319">홀로그램의 중심에서 raycasting로 화면에 맞출 수 있는지 여부와 경계 큐브의 4 개 모퉁이를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-319">Determine if a hologram will fit on a surface by raycasting from the center and four corners of the bounding cube.</span></span>
2. <span data-ttu-id="372cc-320">표면 법선을 확인 하 여 홀로그램을 가만히 놓을 수 있을 만큼 부드러운 지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-320">Check the surface normal to determine if it is smooth enough for the hologram to sit flush on.</span></span>
3. <span data-ttu-id="372cc-321">홀로그램 주위에 경계 큐브를 렌더링 하 여 배치 하는 동안 실제 크기를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-321">Render a bounding cube around the hologram to show its actual size while being placed.</span></span>
4. <span data-ttu-id="372cc-322">홀로그램 아래/뒤에 그림자를 캐스팅 하 여 바닥/벽에 배치 될 위치를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-322">Cast a shadow under/behind the hologram to show where it will be placed on the floor/wall.</span></span>
5. <span data-ttu-id="372cc-323">홀로그램을 표면에 배치할 수 없는 경우 그림자를 빨간색으로 렌더링 하 고 가능 하면 녹색으로 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-323">Render the shadow as red, if the hologram cannot be placed on the surface, or green, if it can.</span></span>
6. <span data-ttu-id="372cc-324">선호도가 있는 표면 유형 (수직 또는 수평)에 맞춰 홀로그램의 방향을 다시 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-324">Re-orient the hologram to align with the surface type (vertical or horizontal) that it has affinity to.</span></span>
7. <span data-ttu-id="372cc-325">이동 또는 맞춤 동작을 방지 하기 위해 홀로그램을 선택한 화면에 원활 하 게 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-325">Smoothly place the hologram on the selected surface to avoid jumping or snapping behavior.</span></span>

<span data-ttu-id="372cc-326">아래 코딩 연습에서 모든 코드의 주석 처리를 제거 하거나 **Placeable.cs**에서이 완성 된 솔루션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-326">Uncomment all code in the coding exercise below, or use this completed solution in **Placeable.cs**:</span></span>

```cs
using System.Collections.Generic;
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Enumeration containing the surfaces on which a GameObject
/// can be placed.  For simplicity of this sample, only one
/// surface type is allowed to be selected.
/// </summary>
public enum PlacementSurfaces
{
    // Horizontal surface with an upward pointing normal.    
    Horizontal = 1,

    // Vertical surface with a normal facing the user.
    Vertical = 2,
}

/// <summary>
/// The Placeable class implements the logic used to determine if a GameObject
/// can be placed on a target surface. Constraints for placement include:
/// * No part of the GameObject's box collider impacts with another object in the scene
/// * The object lays flat (within specified tolerances) against the surface
/// * The object would not fall off of the surface if gravity were enabled.
/// This class also provides the following visualizations.
/// * A transparent cube representing the object's box collider.
/// * Shadow on the target surface indicating whether or not placement is valid.
/// </summary>
public class Placeable : MonoBehaviour
{
    [Tooltip("The base material used to render the bounds asset when placement is allowed.")]
    public Material PlaceableBoundsMaterial = null;

    [Tooltip("The base material used to render the bounds asset when placement is not allowed.")]
    public Material NotPlaceableBoundsMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it allowed.")]
    public Material PlaceableShadowMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it not allowed.")]
    public Material NotPlaceableShadowMaterial = null;

    [Tooltip("The type of surface on which the object can be placed.")]
    public PlacementSurfaces PlacementSurface = PlacementSurfaces.Horizontal;

    [Tooltip("The child object(s) to hide during placement.")]
    public List<GameObject> ChildrenToHide = new List<GameObject>();

    /// <summary>
    /// Indicates if the object is in the process of being placed.
    /// </summary>
    public bool IsPlacing { get; private set; }

    // The most recent distance to the surface.  This is used to 
    // locate the object when the user's gaze does not intersect
    // with the Spatial Mapping mesh.
    private float lastDistance = 2.0f;

    // The distance away from the target surface that the object should hover prior while being placed.
    private float hoverDistance = 0.15f;

    // Threshold (the closer to 0, the stricter the standard) used to determine if a surface is flat.
    private float distanceThreshold = 0.02f;

    // Threshold (the closer to 1, the stricter the standard) used to determine if a surface is vertical.
    private float upNormalThreshold = 0.9f;

    // Maximum distance, from the object, that placement is allowed.
    // This is used when raycasting to see if the object is near a placeable surface.
    private float maximumPlacementDistance = 5.0f;

    // Speed (1.0 being fastest) at which the object settles to the surface upon placement.
    private float placementVelocity = 0.06f;

    // Indicates whether or not this script manages the object's box collider.
    private bool managingBoxCollider = false;

    // The box collider used to determine of the object will fit in the desired location.
    // It is also used to size the bounding cube.
    private BoxCollider boxCollider = null;

    // Visible asset used to show the dimensions of the object. This asset is sized
    // using the box collider's bounds.
    private GameObject boundsAsset = null;

    // Visible asset used to show the where the object is attempting to be placed.
    // This asset is sized using the box collider's bounds.
    private GameObject shadowAsset = null;

    // The location at which the object will be placed.
    private Vector3 targetPosition;

    /// <summary>
    /// Called when the GameObject is created.
    /// </summary>
    private void Awake()
    {
        targetPosition = gameObject.transform.position;

        // Get the object's collider.
        boxCollider = gameObject.GetComponent<BoxCollider>();
        if (boxCollider == null)
        {
            // The object does not have a collider, create one and remember that
            // we are managing it.
            managingBoxCollider = true;
            boxCollider = gameObject.AddComponent<BoxCollider>();
            boxCollider.enabled = false;
        }

        // Create the object that will be used to indicate the bounds of the GameObject.
        boundsAsset = GameObject.CreatePrimitive(PrimitiveType.Cube);
        boundsAsset.transform.parent = gameObject.transform;
        boundsAsset.SetActive(false);

        // Create a object that will be used as a shadow.
        shadowAsset = GameObject.CreatePrimitive(PrimitiveType.Quad);
        shadowAsset.transform.parent = gameObject.transform;
        shadowAsset.SetActive(false);
    }

    /// <summary>
    /// Called when our object is selected.  Generally called by
    /// a gesture management component.
    /// </summary>
    public void OnSelect()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (!IsPlacing)
        {
            OnPlacementStart();
        }
        else
        {
            OnPlacementStop();
        }
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (IsPlacing)
        {
            // Move the object.
            Move();

            // Set the visual elements.
            Vector3 targetPosition;
            Vector3 surfaceNormal;
            bool canBePlaced = ValidatePlacement(out targetPosition, out surfaceNormal);
            DisplayBounds(canBePlaced);
            DisplayShadow(targetPosition, surfaceNormal, canBePlaced);
        }
        else
        {
            // Disable the visual elements.
            boundsAsset.SetActive(false);
            shadowAsset.SetActive(false);

            // Gracefully place the object on the target surface.
            float dist = (gameObject.transform.position - targetPosition).magnitude;
            if (dist > 0)
            {
                gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, targetPosition, placementVelocity / dist);
            }
            else
            {
                // Unhide the child object(s) to make placement easier.
                for (int i = 0; i < ChildrenToHide.Count; i++)
                {
                    ChildrenToHide[i].SetActive(true);
                }
            }
        }
    }

    /// <summary>
    /// Verify whether or not the object can be placed.
    /// </summary>
    /// <param name="position">
    /// The target position on the surface.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the object is to be placed.
    /// </param>
    /// <returns>
    /// True if the target position is valid for placing the object, otherwise false.
    /// </returns>
    private bool ValidatePlacement(out Vector3 position, out Vector3 surfaceNormal)
    {
        Vector3 raycastDirection = gameObject.transform.forward;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            // Raycast from the bottom face of the box collider.
            raycastDirection = -(Vector3.up);
        }

        // Initialize out parameters.
        position = Vector3.zero;
        surfaceNormal = Vector3.zero;

        Vector3[] facePoints = GetColliderFacePoints();

        // The origin points we receive are in local space and we 
        // need to raycast in world space.
        for (int i = 0; i < facePoints.Length; i++)
        {
            facePoints[i] = gameObject.transform.TransformVector(facePoints[i]) + gameObject.transform.position;
        }

        // Cast a ray from the center of the box collider face to the surface.
        RaycastHit centerHit;
        if (!Physics.Raycast(facePoints[0],
                        raycastDirection,
                        out centerHit,
                        maximumPlacementDistance,
                        SpatialMappingManager.Instance.LayerMask))
        {
            // If the ray failed to hit the surface, we are done.
            return false;
        }

        // We have found a surface.  Set position and surfaceNormal.
        position = centerHit.point;
        surfaceNormal = centerHit.normal;

        // Cast a ray from the corners of the box collider face to the surface.
        for (int i = 1; i < facePoints.Length; i++)
        {
            RaycastHit hitInfo;
            if (Physics.Raycast(facePoints[i],
                                raycastDirection,
                                out hitInfo,
                                maximumPlacementDistance,
                                SpatialMappingManager.Instance.LayerMask))
            {
                // To be a valid placement location, each of the corners must have a similar
                // enough distance to the surface as the center point
                if (!IsEquivalentDistance(centerHit.distance, hitInfo.distance))
                {
                    return false;
                }
            }
            else
            {
                // The raycast failed to intersect with the target layer.
                return false;
            }
        }

        return true;
    }

    /// <summary>
    /// Determine the coordinates, in local space, of the box collider face that 
    /// will be placed against the target surface.
    /// </summary>
    /// <returns>
    /// Vector3 array with the center point of the face at index 0.
    /// </returns>
    private Vector3[] GetColliderFacePoints()
    {
        // Get the collider extents.  
        // The size values are twice the extents.
        Vector3 extents = boxCollider.size / 2;

        // Calculate the min and max values for each coordinate.
        float minX = boxCollider.center.x - extents.x;
        float maxX = boxCollider.center.x + extents.x;
        float minY = boxCollider.center.y - extents.y;
        float maxY = boxCollider.center.y + extents.y;
        float minZ = boxCollider.center.z - extents.z;
        float maxZ = boxCollider.center.z + extents.z;

        Vector3 center;
        Vector3 corner0;
        Vector3 corner1;
        Vector3 corner2;
        Vector3 corner3;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            center = new Vector3(boxCollider.center.x, minY, boxCollider.center.z);
            corner0 = new Vector3(minX, minY, minZ);
            corner1 = new Vector3(minX, minY, maxZ);
            corner2 = new Vector3(maxX, minY, minZ);
            corner3 = new Vector3(maxX, minY, maxZ);
        }
        else
        {
            // Placing on vertical surfaces.
            center = new Vector3(boxCollider.center.x, boxCollider.center.y, maxZ);
            corner0 = new Vector3(minX, minY, maxZ);
            corner1 = new Vector3(minX, maxY, maxZ);
            corner2 = new Vector3(maxX, minY, maxZ);
            corner3 = new Vector3(maxX, maxY, maxZ);
        }

        return new Vector3[] { center, corner0, corner1, corner2, corner3 };
    }

    /// <summary>
    /// Put the object into placement mode.
    /// </summary>
    public void OnPlacementStart()
    {
        // If we are managing the collider, enable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = true;
        }

        // Hide the child object(s) to make placement easier.
        for (int i = 0; i < ChildrenToHide.Count; i++)
        {
            ChildrenToHide[i].SetActive(false);
        }

        // Tell the gesture manager that it is to assume
        // all input is to be given to this object.
        GestureManager.Instance.OverrideFocusedObject = gameObject;

        // Enter placement mode.
        IsPlacing = true;
    }

    /// <summary>
    /// Take the object out of placement mode.
    /// </summary>
    /// <remarks>
    /// This method will leave the object in placement mode if called while
    /// the object is in an invalid location.  To determine whether or not
    /// the object has been placed, check the value of the IsPlacing property.
    /// </remarks>
    public void OnPlacementStop()
    {
        // ValidatePlacement requires a normal as an out parameter.
        Vector3 position;
        Vector3 surfaceNormal;

        // Check to see if we can exit placement mode.
        if (!ValidatePlacement(out position, out surfaceNormal))
        {
            return;
        }

        // The object is allowed to be placed.
        // We are placing at a small buffer away from the surface.
        targetPosition = position + (0.01f * surfaceNormal);

        OrientObject(true, surfaceNormal);

        // If we are managing the collider, disable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = false;
        }

        // Tell the gesture manager that it is to resume
        // its normal behavior.
        GestureManager.Instance.OverrideFocusedObject = null;

        // Exit placement mode.
        IsPlacing = false;
    }

    /// <summary>
    /// Positions the object along the surface toward which the user is gazing.
    /// </summary>
    /// <remarks>
    /// If the user's gaze does not intersect with a surface, the object
    /// will remain at the most recently calculated distance.
    /// </remarks>
    private void Move()
    {
        Vector3 moveTo = gameObject.transform.position;
        Vector3 surfaceNormal = Vector3.zero;
        RaycastHit hitInfo;

        bool hit = Physics.Raycast(Camera.main.transform.position,
                                Camera.main.transform.forward,
                                out hitInfo,
                                20f,
                                SpatialMappingManager.Instance.LayerMask);

        if (hit)
        {
            float offsetDistance = hoverDistance;

            // Place the object a small distance away from the surface while keeping 
            // the object from going behind the user.
            if (hitInfo.distance <= hoverDistance)
            {
                offsetDistance = 0f;
            }

            moveTo = hitInfo.point + (offsetDistance * hitInfo.normal);

            lastDistance = hitInfo.distance;
            surfaceNormal = hitInfo.normal;
        }
        else
        {
            // The raycast failed to hit a surface.  In this case, keep the object at the distance of the last
            // intersected surface.
            moveTo = Camera.main.transform.position + (Camera.main.transform.forward * lastDistance);
        }

        // Follow the user's gaze.
        float dist = Mathf.Abs((gameObject.transform.position - moveTo).magnitude);
        gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, moveTo, placementVelocity / dist);

        // Orient the object.
        // We are using the return value from Physics.Raycast to instruct
        // the OrientObject function to align to the vertical surface if appropriate.
        OrientObject(hit, surfaceNormal);
    }

    /// <summary>
    /// Orients the object so that it faces the user.
    /// </summary>
    /// <param name="alignToVerticalSurface">
    /// If true and the object is to be placed on a vertical surface, 
    /// orient parallel to the target surface.  If false, orient the object 
    /// to face the user.
    /// </param>
    /// <param name="surfaceNormal">
    /// The target surface's normal vector.
    /// </param>
    /// <remarks>
    /// The aligntoVerticalSurface parameter is ignored if the object
    /// is to be placed on a horizontalSurface
    /// </remarks>
    private void OrientObject(bool alignToVerticalSurface, Vector3 surfaceNormal)
    {
        Quaternion rotation = Camera.main.transform.localRotation;

        // If the user's gaze does not intersect with the Spatial Mapping mesh,
        // orient the object towards the user.
        if (alignToVerticalSurface && (PlacementSurface == PlacementSurfaces.Vertical))
        {
            // We are placing on a vertical surface.
            // If the normal of the Spatial Mapping mesh indicates that the
            // surface is vertical, orient parallel to the surface.
            if (Mathf.Abs(surfaceNormal.y) <= (1 - upNormalThreshold))
            {
                rotation = Quaternion.LookRotation(-surfaceNormal, Vector3.up);
            }
        }
        else
        {
            rotation.x = 0f;
            rotation.z = 0f;
        }

        gameObject.transform.rotation = rotation;
    }

    /// <summary>
    /// Displays the bounds asset.
    /// </summary>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayBounds(bool canBePlaced)
    {
        // Ensure the bounds asset is sized and positioned correctly.
        boundsAsset.transform.localPosition = boxCollider.center;
        boundsAsset.transform.localScale = boxCollider.size;
        boundsAsset.transform.rotation = gameObject.transform.rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = PlaceableBoundsMaterial;
        }
        else
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableBoundsMaterial;
        }

        // Show the bounds asset.
        boundsAsset.SetActive(true);
    }

    /// <summary>
    /// Displays the placement shadow asset.
    /// </summary>
    /// <param name="position">
    /// The position at which to place the shadow asset.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the asset will be placed
    /// </param>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayShadow(Vector3 position,
                            Vector3 surfaceNormal,
                            bool canBePlaced)
    {
        // Rotate and scale the shadow so that it is displayed on the correct surface and matches the object.
        float rotationX = 0.0f;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            rotationX = 90.0f;
            shadowAsset.transform.localScale = new Vector3(boxCollider.size.x, boxCollider.size.z, 1);
        }
        else
        {
            shadowAsset.transform.localScale = boxCollider.size;
        }

        Quaternion rotation = Quaternion.Euler(rotationX, gameObject.transform.rotation.eulerAngles.y, 0);
        shadowAsset.transform.rotation = rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = PlaceableShadowMaterial;
        }
        else
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableShadowMaterial;
        }

        // Show the shadow asset as appropriate.        
        if (position != Vector3.zero)
        {
            // Position the shadow a small distance from the target surface, along the normal.
            shadowAsset.transform.position = position + (0.01f * surfaceNormal);
            shadowAsset.SetActive(true);
        }
        else
        {
            shadowAsset.SetActive(false);
        }
    }

    /// <summary>
    /// Determines if two distance values should be considered equivalent. 
    /// </summary>
    /// <param name="d1">
    /// Distance to compare.
    /// </param>
    /// <param name="d2">
    /// Distance to compare.
    /// </param>
    /// <returns>
    /// True if the distances are within the desired tolerance, otherwise false.
    /// </returns>
    private bool IsEquivalentDistance(float d1, float d2)
    {
        float dist = Mathf.Abs(d1 - d2);
        return (dist <= distanceThreshold);
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        // Unload objects we have created.
        Destroy(boundsAsset);
        boundsAsset = null;
        Destroy(shadowAsset);
        shadowAsset = null;
    }
}
```

<span data-ttu-id="372cc-327">**빌드 및 배포**</span><span class="sxs-lookup"><span data-stu-id="372cc-327">**Build and Deploy**</span></span>
* <span data-ttu-id="372cc-328">이전과 마찬가지로 프로젝트를 빌드하고 HoloLens에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-328">As before, build the project and deploy to the HoloLens.</span></span>
* <span data-ttu-id="372cc-329">공간 매핑 데이터의 검색 및 처리가 완료 될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-329">Wait for scanning and processing of the spatial mapping data to complete.</span></span>
* <span data-ttu-id="372cc-330">태양계가 표시 되 면 아래 투영 상자를 응시 하 고 선택 제스처를 수행 하 여 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-330">When you see the solar system, gaze at the projection box below and perform a select gesture to move it around.</span></span> <span data-ttu-id="372cc-331">투영 상자를 선택 하는 동안에는 경계 큐브가 투영 상자 주위에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-331">While the projection box is selected, a bounding cube will be visible around the projection box.</span></span>
* <span data-ttu-id="372cc-332">머리를 이동 하 여 대화방의 다른 위치를 응시 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-332">Move you head to gaze at a different location in the room.</span></span> <span data-ttu-id="372cc-333">투영 상자는 응시 다음에와 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-333">The projection box should follow your gaze.</span></span> <span data-ttu-id="372cc-334">투영 상자 아래 그림자가 빨간색으로 바뀌고 해당 화면에 홀로그램을 놓을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-334">When the shadow below the projection box turns red, you cannot place the hologram on that surface.</span></span> <span data-ttu-id="372cc-335">투영 상자 아래의 그림자가 녹색으로 바뀌고 다른 선택 제스처를 수행 하 여 홀로그램을 놓을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-335">When the shadow below the projection box turns green, you can place the hologram by performing another select gesture.</span></span>
* <span data-ttu-id="372cc-336">벽에서 holographic 포스터 중 하나를 찾아 선택 하 여 새 위치로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-336">Find and select one of the holographic posters on a wall to move it to a new location.</span></span> <span data-ttu-id="372cc-337">바닥 또는 천장에 포스터를 배치할 수 없으며, 이동할 때 각 벽에 대해 올바르게 방향이 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-337">Notice that you cannot place the poster on the floor or ceiling, and that it stays correctly oriented to each wall as you move around.</span></span>

## <a name="chapter-5---occlusion"></a><span data-ttu-id="372cc-338">5 장-폐색</span><span class="sxs-lookup"><span data-stu-id="372cc-338">Chapter 5 - Occlusion</span></span>

>[!VIDEO https://www.youtube.com/embed/6Xrzh_w-7SE]

<span data-ttu-id="372cc-339">**목표로**</span><span class="sxs-lookup"><span data-stu-id="372cc-339">**Objectives**</span></span>
* <span data-ttu-id="372cc-340">홀로그램을 공간 매핑 메시로 폐색 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-340">Determine if a hologram is occluded by the spatial mapping mesh.</span></span>
* <span data-ttu-id="372cc-341">흥미로운 효과를 얻기 위해 다른 폐색 기술을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-341">Apply different occlusion techniques to achieve a fun effect.</span></span>

<span data-ttu-id="372cc-342">**지침**</span><span class="sxs-lookup"><span data-stu-id="372cc-342">**Instructions**</span></span>

<span data-ttu-id="372cc-343">먼저 공간 매핑 메시가 실제 세계를 occluding 하지 않고 다른 holograms을 려 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-343">First, we are going to allow the spatial mapping mesh to occlude other holograms without occluding the real world:</span></span>
* <span data-ttu-id="372cc-344">**계층** 패널에서 **SpatialProcessing** 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-344">In the **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="372cc-345">**검사기** 패널에서 **재생 공간 관리자 (스크립트)** 구성 요소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-345">In the **Inspector** panel, find the **Play Space Manager (Script)** component.</span></span>
* <span data-ttu-id="372cc-346">**보조 재질** 속성의 오른쪽에 있는 원을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-346">Click the circle to the right of the **Secondary Material** property.</span></span>
* <span data-ttu-id="372cc-347">**폐색** 재질을 찾아 선택 하 고 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-347">Find and select the **Occlusion** material and close the window.</span></span>

<span data-ttu-id="372cc-348">다음으로 지구에 특별 한 동작을 추가 하 여 다른 홀로그램 (예: sun)에 의해 폐색 될 때마다 파란색 강조 표시를 하거나 공간 매핑 메시로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-348">Next, we are going to add a special behavior to Earth, so that it has a blue highlight whenever it becomes occluded by another hologram (like the sun), or by the spatial mapping mesh:</span></span>
* <span data-ttu-id="372cc-349">**프로젝트** 패널의 **Holograms** 폴더에서 **SolarSystem** 개체를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-349">In the **Project** panel, in the **Holograms** folder, expand the **SolarSystem** object.</span></span>
* <span data-ttu-id="372cc-350">**지구**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-350">Click on **Earth**.</span></span>
* <span data-ttu-id="372cc-351">**검사기** 패널에서 지구 재질 (최하위 구성 요소)을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-351">In the **Inspector** panel, find the Earth's material (bottom component).</span></span>
* <span data-ttu-id="372cc-352">**셰이더 드롭다운에서**셰이더를 **사용자 지정 > OcclusionRim**로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-352">In the **Shader drop-down**, change the shader to **Custom > OcclusionRim**.</span></span> <span data-ttu-id="372cc-353">그러면 다른 개체에 의해 폐색 될 때마다 지구 주위에 파란색 강조 표시가 렌더링 됩니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-353">This will render a blue highlight around Earth whenever it is occluded by another object.</span></span>

<span data-ttu-id="372cc-354">마지막으로, 태양계에서 행성에 대해 x-레이 비전 효과를 사용 하도록 설정 하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-354">Finally, we are going to enable an x-ray vision effect for planets in our solar system.</span></span> <span data-ttu-id="372cc-355">다음을 수행 하려면 **PlanetOcclusion.cs** (Scripts\SolarSystem 폴더에 있음)를 편집 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-355">We will need to edit **PlanetOcclusion.cs** (found in the Scripts\SolarSystem folder) in order to achieve the following:</span></span>
1. <span data-ttu-id="372cc-356">SpatialMapping 계층 (방 메시 및 평면)에서 행성을 폐색 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-356">Determine if a planet is occluded by the SpatialMapping layer (room meshes and planes).</span></span>
2. <span data-ttu-id="372cc-357">SpatialMapping 계층에 의해 폐색 될 때마다 전 세계의 와이어 프레임 표현을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-357">Show the wireframe representation of a planet whenever it is occluded by the SpatialMapping layer.</span></span>
3. <span data-ttu-id="372cc-358">SpatialMapping 계층에 의해 차단 되지 않는 행성의 와이어 프레임 표현을 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-358">Hide the wireframe representation of a planet when it is not blocked by the SpatialMapping layer.</span></span>

<span data-ttu-id="372cc-359">PlanetOcclusion.cs의 코딩 연습을 수행 하거나 다음 솔루션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-359">Follow the coding exercise in PlanetOcclusion.cs, or use the following solution:</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Determines when the occluded version of the planet should be visible.
/// This script allows us to do selective occlusion, so the occlusionObject
/// will only be rendered when a Spatial Mapping surface is occluding the planet,
/// not when another hologram is responsible for the occlusion.
/// </summary>
public class PlanetOcclusion : MonoBehaviour
{
    [Tooltip("Object to display when the planet is occluded.")]
    public GameObject occlusionObject;

    /// <summary>
    /// Points to raycast to when checking for occlusion.
    /// </summary>
    private Vector3[] checkPoints;

    // Use this for initialization
    void Start()
    {
        occlusionObject.SetActive(false);

        // Set the check points to use when testing for occlusion.
        MeshFilter filter = gameObject.GetComponent<MeshFilter>();
        Vector3 extents = filter.mesh.bounds.extents;
        Vector3 center = filter.mesh.bounds.center;
        Vector3 top = new Vector3(center.x, center.y + extents.y, center.z);
        Vector3 left = new Vector3(center.x - extents.x, center.y, center.z);
        Vector3 right = new Vector3(center.x + extents.x, center.y, center.z);
        Vector3 bottom = new Vector3(center.x, center.y - extents.y, center.z);

        checkPoints = new Vector3[] { center, top, left, right, bottom };
    }

    // Update is called once per frame
    void Update()
    {
        /* TODO: 5.a DEVELOPER CODING EXERCISE 5.a */

        // Check to see if any of the planet's boundary points are occluded.
        for (int i = 0; i < checkPoints.Length; i++)
        {
            // 5.a: Convert the current checkPoint to world coordinates.
            // Call gameObject.transform.TransformPoint(checkPoints[i]).
            // Assign the result to a new Vector3 variable called 'checkPt'.
            Vector3 checkPt = gameObject.transform.TransformPoint(checkPoints[i]);

            // 5.a: Call Vector3.Distance() to calculate the distance
            // between the Main Camera's position and 'checkPt'.
            // Assign the result to a new float variable called 'distance'.
            float distance = Vector3.Distance(Camera.main.transform.position, checkPt);

            // 5.a: Take 'checkPt' and subtract the Main Camera's position from it.
            // Assign the result to a new Vector3 variable called 'direction'.
            Vector3 direction = checkPt - Camera.main.transform.position;

            // Used to indicate if the call to Physics.Raycast() was successful.
            bool raycastHit = false;

            // 5.a: Check if the planet is occluded by a spatial mapping surface.
            // Call Physics.Raycast() with the following arguments:
            // - Pass in the Main Camera's position as the origin.
            // - Pass in 'direction' for the direction.
            // - Pass in 'distance' for the maxDistance.
            // - Pass in SpatialMappingManager.Instance.LayerMask as layerMask.
            // Assign the result to 'raycastHit'.
            raycastHit = Physics.Raycast(Camera.main.transform.position, direction, distance, SpatialMappingManager.Instance.LayerMask);

            if (raycastHit)
            {
                // 5.a: Our raycast hit a surface, so the planet is occluded.
                // Set the occlusionObject to active.
                occlusionObject.SetActive(true);

                // At least one point is occluded, so break from the loop.
                break;
            }
            else
            {
                // 5.a: The Raycast did not hit, so the planet is not occluded.
                // Deactivate the occlusionObject.
                occlusionObject.SetActive(false);
            }
        }
    }
}
```

<span data-ttu-id="372cc-360">**빌드 및 배포**</span><span class="sxs-lookup"><span data-stu-id="372cc-360">**Build and Deploy**</span></span>
* <span data-ttu-id="372cc-361">평소 처럼 응용 프로그램을 빌드하고 HoloLens에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-361">Build and deploy the application to HoloLens, as usual.</span></span>
* <span data-ttu-id="372cc-362">공간 매핑 데이터의 스캔 및 처리가 완료 될 때까지 기다립니다 (벽에 파란색 선이 표시 되어야 함).</span><span class="sxs-lookup"><span data-stu-id="372cc-362">Wait for scanning and processing of the spatial mapping data to be complete (you should see blue lines appear on walls).</span></span>
* <span data-ttu-id="372cc-363">태양계의 투영 상자를 찾아 선택한 다음 벽 옆 또는 카운터 뒤에 있는 상자를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-363">Find and select the solar system's projection box and then set the box next to a wall or behind a counter.</span></span>
* <span data-ttu-id="372cc-364">포스터 또는 프로젝션 상자에서 피어에 화면을 숨겨서 기본 폐색를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-364">You can view basic occlusion by hiding behind surfaces to peer at the poster or projection box.</span></span>
* <span data-ttu-id="372cc-365">지구를 찾아 다른 홀로그램 또는 표면 뒤에 있을 때마다 파란색 강조 표시 효과가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-365">Look for the Earth, there should be a blue highlight effect whenever it goes behind another hologram or surface.</span></span>
* <span data-ttu-id="372cc-366">벽 또는 방의 다른 표면 뒤에서 행성 이동을 시청 합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-366">Watch as the planets move behind the wall or other surfaces in the room.</span></span> <span data-ttu-id="372cc-367">이제 x 광선의 비전을 통해 와이어 프레임 구조를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-367">You now have x-ray vision and can see their wireframe skeletons!</span></span>

## <a name="the-end"></a><span data-ttu-id="372cc-368">끝</span><span class="sxs-lookup"><span data-stu-id="372cc-368">The End</span></span>

<span data-ttu-id="372cc-369">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-369">Congratulations!</span></span> <span data-ttu-id="372cc-370">이제 MR 공간 230 **을 완료 했습니다. 공간 매핑입니다**.</span><span class="sxs-lookup"><span data-stu-id="372cc-370">You have now completed **MR Spatial 230: Spatial mapping**.</span></span>
* <span data-ttu-id="372cc-371">환경을 검색 하 고 공간 매핑 데이터를 Unity로 로드 하는 방법을 알고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-371">You know how to scan your environment and load spatial mapping data to Unity.</span></span>
* <span data-ttu-id="372cc-372">셰이더의 기본 사항과 자료를 사용 하 여 전 세계를 다시 시각화 하는 방법을 이해 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-372">You understand the basics of shaders and how materials can be used to re-visualize the world.</span></span>
* <span data-ttu-id="372cc-373">평면을 찾고 메시에서 삼각형을 제거 하는 새로운 처리 기법을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-373">You learned of new processing techniques for finding planes and removing triangles from a mesh.</span></span>
* <span data-ttu-id="372cc-374">Holograms를 이동 하 고 적합 한 표면에 놓을 수 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="372cc-374">You were able to move and place holograms on surfaces that made sense.</span></span>
* <span data-ttu-id="372cc-375">다양 한 폐색 기술이 경험 했으며 x 광선의 기능을 asha.</span><span class="sxs-lookup"><span data-stu-id="372cc-375">You experienced different occlusion techniques and harnessed the power of x-ray vision!</span></span>
