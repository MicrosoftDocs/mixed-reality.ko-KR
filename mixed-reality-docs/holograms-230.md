---
title: MR 공간 230-공간 매핑
description: Unity에서 Visual Studio 및 HoloLens를 사용 하 여 공간 매핑 개념의 자세한 연습을 코딩이 수행 합니다.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit mixedrealitytoolkit, mixedrealitytoolkit unity, academy, 자습서, 공간 매핑, 화면 재구성, 메시
ms.openlocfilehash: 8d5715337ddd20e9868b18fdf0c63c704f584972
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600925"
---
>[!NOTE]
><span data-ttu-id="7d80c-104">혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="7d80c-105">따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="7d80c-106">이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="7d80c-107">지원 되는 장치에서 작업을 계속 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="7d80c-108">새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="7d80c-109">게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-spatial-230-spatial-mapping"></a><span data-ttu-id="7d80c-110">MR 공간 230: 공간 매핑</span><span class="sxs-lookup"><span data-stu-id="7d80c-110">MR Spatial 230: Spatial mapping</span></span>

<span data-ttu-id="7d80c-111">[공간 매핑](spatial-mapping.md) 홀로그램 환경에 대 한 강의 하 여 실제 및 가상 세계를 함께 결합 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-111">[Spatial mapping](spatial-mapping.md) combines the real world and virtual world together by teaching holograms about the environment.</span></span> <span data-ttu-id="7d80c-112">MR 공간 230 (프로젝트 Planetarium)에서는 것에 대해 설명 하는 방법.</span><span class="sxs-lookup"><span data-stu-id="7d80c-112">In MR Spatial 230 (Project Planetarium) we'll learn how to:</span></span>

* <span data-ttu-id="7d80c-113">개발 컴퓨터에는 HoloLens에서 환경 및 전송 데이터를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-113">Scan the environment and transfer data from the HoloLens to your development machine.</span></span>
* <span data-ttu-id="7d80c-114">셰이더를 탐색 하 고, 공간 시각화에 사용 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-114">Explore shaders and learn how to use them for visualizing your space.</span></span>
* <span data-ttu-id="7d80c-115">대화방 메시 메시 처리를 사용 하 여 간단한 평면으로 분해 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-115">Break down the room mesh into simple planes using mesh processing.</span></span>
* <span data-ttu-id="7d80c-116">학습 한 배치 기술 만으로는 [MR 기본 사항 101](holograms-101.md)를 홀로그램 환경에 배치할 수 있는지에 대 한 피드백을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-116">Go beyond the placement techniques we learned in [MR Basics 101](holograms-101.md), and provide feedback about where a hologram can be placed in the environment.</span></span>
* <span data-ttu-id="7d80c-117">폐색 효과 탐색 실제 개체 뒤에 홀로그램 때 볼 수 있도록 계속이 레이 투시 능력이 사용 하 여!</span><span class="sxs-lookup"><span data-stu-id="7d80c-117">Explore occlusion effects, so when your hologram is behind a real-world object, you can still see it with x-ray vision!</span></span>

>[!VIDEO https://www.youtube.com/embed/NSNYRkUX6Mw]

## <a name="device-support"></a><span data-ttu-id="7d80c-118">장치 지원</span><span class="sxs-lookup"><span data-stu-id="7d80c-118">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="7d80c-119">과정</span><span class="sxs-lookup"><span data-stu-id="7d80c-119">Course</span></span></th><th style="width:150px"> <span data-ttu-id="7d80c-120"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="7d80c-120"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="7d80c-121"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="7d80c-121"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="7d80c-122">MR 공간 230: 공간 매핑</span><span class="sxs-lookup"><span data-stu-id="7d80c-122">MR Spatial 230: Spatial mapping</span></span></td><td style="text-align: center;"> <span data-ttu-id="7d80c-123">✔️</span><span class="sxs-lookup"><span data-stu-id="7d80c-123">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="7d80c-124">시작하기 전 주의 사항</span><span class="sxs-lookup"><span data-stu-id="7d80c-124">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="7d80c-125">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="7d80c-125">Prerequisites</span></span>

* <span data-ttu-id="7d80c-126">올바른를 사용 하 여 구성 하는 Windows 10 PC [도구가 설치 되어](install-the-tools.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-126">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="7d80c-127">기본적인 C# 기능을 프로그래밍 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-127">Some basic C# programming ability.</span></span>
* <span data-ttu-id="7d80c-128">완료 해야 [MR 기본 사항 101](holograms-101.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-128">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="7d80c-129">HoloLens 장치 [개발에 대해 구성 된](using-visual-studio.md#enabling-developer-mode)합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-129">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="7d80c-130">프로젝트 파일</span><span class="sxs-lookup"><span data-stu-id="7d80c-130">Project files</span></span>

* <span data-ttu-id="7d80c-131">다운로드 합니다 [파일](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) 프로젝트에서 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-131">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) required by the project.</span></span><span data-ttu-id="7d80c-132"> Unity 2017.2 이상이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-132"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="7d80c-133">Unity 5.6 지원이 계속 필요한 경우 사용 하세요 [이 릴리스에서](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip)합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-133">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip).</span></span>
  * <span data-ttu-id="7d80c-134">Unity 5.5 지원 해야 하는 경우 사용 하세요 [이 릴리스에서](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip)합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-134">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip).</span></span>
  * <span data-ttu-id="7d80c-135">Unity 5.4 지원이 계속 필요한 경우 사용 하세요 [이 릴리스에서](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip)합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-135">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip).</span></span>
* <span data-ttu-id="7d80c-136">취소 보관 파일을 데스크톱 또는 기타 쉽게 달성할 수 있습니다 위치 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-136">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="7d80c-137">을 다운로드 하기 전에 소스 코드를 확인 하려는 경우 있기 [GitHub에서 사용할 수 있는](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping)합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping).</span></span>

### <a name="notes"></a><span data-ttu-id="7d80c-138">참고</span><span class="sxs-lookup"><span data-stu-id="7d80c-138">Notes</span></span>

* <span data-ttu-id="7d80c-139">"사용할 수 없게 해야 하는 Visual Studio에서에서" 내 코드만 사용 (*unchecked*) 도구 > 옵션 > 디버깅 코드에서 중단점을 적중 하려면.</span><span class="sxs-lookup"><span data-stu-id="7d80c-139">"Enable Just My Code" in Visual Studio needs to be disabled (*unchecked*) under Tools > Options > Debugging in order to hit breakpoints in your code.</span></span>

## <a name="unity-setup"></a><span data-ttu-id="7d80c-140">Unity 설치</span><span class="sxs-lookup"><span data-stu-id="7d80c-140">Unity setup</span></span>

>[!VIDEO https://www.youtube.com/embed/y2Y4LhK6TEM]

* <span data-ttu-id="7d80c-141">시작 **Unity**합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-141">Start **Unity**.</span></span>
* <span data-ttu-id="7d80c-142">선택 **새로 만들기** 새 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-142">Select **New** to create a new project.</span></span>
* <span data-ttu-id="7d80c-143">프로젝트 이름을 **Planetarium**합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-143">Name the project **Planetarium**.</span></span>
* <span data-ttu-id="7d80c-144">있는지 확인 합니다 **3D** 설정을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-144">Verify that the **3D** setting is selected.</span></span>
* <span data-ttu-id="7d80c-145">클릭 **프로젝트를 만들**합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-145">Click **Create Project**.</span></span>
* <span data-ttu-id="7d80c-146">Unity이 시작 되 면 이동할 **편집 > 프로젝트 설정 > 플레이어**합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-146">Once Unity launches, go to **Edit > Project Settings > Player**.</span></span>
* <span data-ttu-id="7d80c-147">에 **검사기** 패널을 찾고 선택 녹색 **Windows 스토어** 아이콘입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-147">In the **Inspector** panel, find and select the green **Windows Store** icon.</span></span>
* <span data-ttu-id="7d80c-148">확장 **기타 설정을**합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-148">Expand **Other Settings**.</span></span>
* <span data-ttu-id="7d80c-149">에 **렌더링** 섹션을 확인 합니다 **가상 현실 지원** 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-149">In the **Rendering** section, check the **Virtual Reality Supported** option.</span></span>
* <span data-ttu-id="7d80c-150">확인 **Windows Holographic** 목록에 표시 됩니다 **가상 현실 Sdk**합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-150">Verify that **Windows Holographic** appears in the list of **Virtual Reality SDKs**.</span></span> <span data-ttu-id="7d80c-151">그렇지 않은 경우 선택 합니다 **+** 목록의 맨 아래에 있는 단추를 선택 **Windows Holographic**합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-151">If not, select the **+** button at the bottom of the list and choose **Windows Holographic**.</span></span>
* <span data-ttu-id="7d80c-152">확장 **게시 설정**합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-152">Expand **Publishing Settings**.</span></span>
* <span data-ttu-id="7d80c-153">에 **기능** 섹션에서 다음 설정을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-153">In the **Capabilities** section, check the following settings:</span></span>
    * <span data-ttu-id="7d80c-154">InternetClientServer</span><span class="sxs-lookup"><span data-stu-id="7d80c-154">InternetClientServer</span></span>
    * <span data-ttu-id="7d80c-155">PrivateNetworkClientServer</span><span class="sxs-lookup"><span data-stu-id="7d80c-155">PrivateNetworkClientServer</span></span>
    * <span data-ttu-id="7d80c-156">마이크</span><span class="sxs-lookup"><span data-stu-id="7d80c-156">Microphone</span></span>
    * <span data-ttu-id="7d80c-157">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="7d80c-157">SpatialPerception</span></span>
* <span data-ttu-id="7d80c-158">로 **편집 > 프로젝트 설정 > 품질**</span><span class="sxs-lookup"><span data-stu-id="7d80c-158">Go to **Edit > Project Settings > Quality**</span></span>
* <span data-ttu-id="7d80c-159">에 **검사기** Windows 스토어 아이콘 선택에서 '기본' 행 아래에 있는 검은색 드롭다운 화살표를 클릭 한 기본 설정을 변경 **가장 빠름**합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-159">In the **Inspector** panel, under the Windows Store icon, select the black drop-down arrow under the 'Default' row and change the default setting to **Fastest**.</span></span>
* <span data-ttu-id="7d80c-160">로 이동 **자산 > 패키지 가져오기 > 사용자 지정 패키지**합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-160">Go to **Assets > Import Package > Custom Package**.</span></span>
* <span data-ttu-id="7d80c-161">로 이동 합니다 **...\HolographicAcademy-Holograms-230-SpatialMapping\Starting** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-161">Navigate to the **...\HolographicAcademy-Holograms-230-SpatialMapping\Starting** folder.</span></span>
* <span data-ttu-id="7d80c-162">클릭할 **Planetarium.unitypackage**합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-162">Click on **Planetarium.unitypackage**.</span></span>
* <span data-ttu-id="7d80c-163">**열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-163">Click **Open**.</span></span>
* <span data-ttu-id="7d80c-164">**Unity 패키지 가져오기** 창이 표시 됩니다를 클릭 합니다 **가져오기** 단추.</span><span class="sxs-lookup"><span data-stu-id="7d80c-164">An **Import Unity Package** window should appear, click on the **Import** button.</span></span>
* <span data-ttu-id="7d80c-165">이 프로젝트를 완료 해야 하는 자산을 모두 가져오려면 Unity 될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-165">Wait for Unity to import all of the assets that we will need to complete this project.</span></span>
* <span data-ttu-id="7d80c-166">에 **계층 구조** 패널에서 삭제 합니다 **주 카메라**합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-166">In the **Hierarchy** panel, delete the **Main Camera**.</span></span>
* <span data-ttu-id="7d80c-167">에 **프로젝트** 패널 **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** 폴더를 찾기는 **주 카메라** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-167">In the **Project** panel, **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** folder, find the **Main Camera** object.</span></span>
* <span data-ttu-id="7d80c-168">끌어서 놓기는 **주 카메라** 으로 prefab 합니다 **계층** 패널입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-168">Drag and drop the **Main Camera** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="7d80c-169">에 **계층** 패널에서 삭제 합니다 **Directional Light** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-169">In the **Hierarchy** panel, delete the **Directional Light** object.</span></span>
* <span data-ttu-id="7d80c-170">에 **프로젝트** 패널 **홀로그램** 폴더를 찾습니다는 **커서** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-170">In the **Project** panel, **Holograms** folder, locate the **Cursor** object.</span></span>
* <span data-ttu-id="7d80c-171">끌어서 놓기 합니다 **커서** 으로 prefab 합니다 **계층**합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-171">Drag & drop the **Cursor** prefab into the **Hierarchy**.</span></span>
* <span data-ttu-id="7d80c-172">에 **계층** 패널을 선택 합니다 **커서** 개체.</span><span class="sxs-lookup"><span data-stu-id="7d80c-172">In the **Hierarchy** panel, select the **Cursor** object.</span></span>
* <span data-ttu-id="7d80c-173">에 **검사기** 패널을 클릭 합니다 **계층** 드롭다운을 선택 **계층 편집...** .</span><span class="sxs-lookup"><span data-stu-id="7d80c-173">In the **Inspector** panel, click the **Layer** drop-down and select **Edit Layers...**.</span></span>
* <span data-ttu-id="7d80c-174">이름을 **사용자 계층 31** 으로 "**SpatialMapping**"입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-174">Name **User Layer 31** as "**SpatialMapping**".</span></span>
* <span data-ttu-id="7d80c-175">새 장면을 저장 합니다. **파일 >으로 장면 저장...**</span><span class="sxs-lookup"><span data-stu-id="7d80c-175">Save the new scene: **File > Save Scene As...**</span></span>
* <span data-ttu-id="7d80c-176">클릭 **새 폴더** 는 폴더의 이름을 **장면**합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-176">Click **New Folder** and name the folder **Scenes**.</span></span>
* <span data-ttu-id="7d80c-177">파일 이름을 "**Planetarium**"에 저장 된 **장면** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-177">Name the file "**Planetarium**" and save it in the **Scenes** folder.</span></span>

## <a name="chapter-1---scanning"></a><span data-ttu-id="7d80c-178">1 장-검색</span><span class="sxs-lookup"><span data-stu-id="7d80c-178">Chapter 1 - Scanning</span></span>

>[!VIDEO https://www.youtube.com/embed/888oW51z_cE]

<span data-ttu-id="7d80c-179">**Objectives**</span><span class="sxs-lookup"><span data-stu-id="7d80c-179">**Objectives**</span></span>
* <span data-ttu-id="7d80c-180">SurfaceObserver 및 설정을 미치는 경험 하는 방법 및 성능에 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-180">Learn about the SurfaceObserver and how its settings impact experience and performance.</span></span>
* <span data-ttu-id="7d80c-181">사용자 공간 메시를 수집 하는 환경을 검색 공간을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-181">Create a room scanning experience to collect the meshes of your room.</span></span>

<span data-ttu-id="7d80c-182">**지침**</span><span class="sxs-lookup"><span data-stu-id="7d80c-182">**Instructions**</span></span>
* <span data-ttu-id="7d80c-183">에 **프로젝트** 패널 **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** 폴더를 찾을 합니다 **SpatialMapping** prefab 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-183">In the **Project** panel **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** folder, find the **SpatialMapping** prefab.</span></span>
* <span data-ttu-id="7d80c-184">끌어서 놓기 합니다 **SpatialMapping** 으로 prefab 합니다 **계층** 패널입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-184">Drag & drop the **SpatialMapping** prefab into the **Hierarchy** panel.</span></span>

<span data-ttu-id="7d80c-185">**빌드 및 배포 (1 부)**</span><span class="sxs-lookup"><span data-stu-id="7d80c-185">**Build and Deploy (part 1)**</span></span>
* <span data-ttu-id="7d80c-186">Unity에서 선택 **파일 > 빌드 설정**합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-186">In Unity, select **File > Build Settings**.</span></span>
* <span data-ttu-id="7d80c-187">클릭 **열려 장면 추가** 추가할 합니다 **Planetarium** 빌드 장면입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-187">Click **Add Open Scenes** to add the **Planetarium** scene to the build.</span></span>
* <span data-ttu-id="7d80c-188">선택 **유니버설 Windows 플랫폼** 에 **플랫폼** 클릭 **플랫폼 전환**합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-188">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="7d80c-189">설정 **SDK** 하 **유니버설 10** 하 고 **UWP 빌드 형식** 에 **D3D**합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-189">Set **SDK** to **Universal 10** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="7d80c-190">확인할 **Unity C# 프로젝트**합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-190">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="7d80c-191">**빌드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-191">Click **Build**.</span></span>
* <span data-ttu-id="7d80c-192">만들기는 **새 폴더** 이름을 "App"입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-192">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="7d80c-193">한 번 클릭 합니다 **앱** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-193">Single click the **App** folder.</span></span>
* <span data-ttu-id="7d80c-194">키를 눌러 합니다 **폴더 선택** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-194">Press the **Select Folder** button.</span></span>
* <span data-ttu-id="7d80c-195">Unity 완료 되 면 빌드 파일 탐색기 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-195">When Unity is done building, a File Explorer window will appear.</span></span>
* <span data-ttu-id="7d80c-196">두 번 클릭 합니다 **앱** 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-196">Double-click on the **App** folder to open it.</span></span>
* <span data-ttu-id="7d80c-197">두 번 클릭 **Planetarium.sln** Visual Studio에서 프로젝트를 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-197">Double-click on **Planetarium.sln** to load the project in Visual Studio.</span></span>
* <span data-ttu-id="7d80c-198">Visual Studio에서 최상위 도구 모음을 사용 하도록 구성을 변경 하려면 **릴리스**합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-198">In Visual Studio, use the top toolbar to change the Configuration to **Release**.</span></span>
* <span data-ttu-id="7d80c-199">플랫폼을 변경 **x86**합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-199">Change the Platform to **x86**.</span></span>
* <span data-ttu-id="7d80c-200">' Localmachine ' 오른쪽에 드롭다운 화살표를 클릭 하 고 선택 **원격 컴퓨터**합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-200">Click on the drop-down arrow to the right of 'Local Machine', and select **Remote Machine**.</span></span>
* <span data-ttu-id="7d80c-201">입력 [장치의 IP 주소](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) 주소 필드 및 인증 모드를 변경할 **유니버설 (암호화 되지 않은 프로토콜)** 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-201">Enter [your device's IP address](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) in the Address field and change Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span>
* <span data-ttu-id="7d80c-202">클릭 **디버그-> 디버깅 없이 시작** 누르거나 **ctrl+f5**합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-202">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="7d80c-203">조사식 합니다 **출력** 빌드에 대 한 Visual Studio에서 패널 및 상태를 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-203">Watch the **Output** panel in Visual Studio for build and deploy status.</span></span>
* <span data-ttu-id="7d80c-204">앱에 배포한 전시실 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-204">Once your app has deployed, walk around the room.</span></span> <span data-ttu-id="7d80c-205">흑백 와이어 프레임 메시를 다루지 주변 화면을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-205">You will see the surrounding surfaces covered by black and white wireframe meshes.</span></span>
* <span data-ttu-id="7d80c-206">환경을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-206">Scan your surroundings.</span></span> <span data-ttu-id="7d80c-207">벽, 최대값이, 바닥 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-207">Be sure to look at walls, ceilings, and floors.</span></span>

<span data-ttu-id="7d80c-208">**빌드 및 배포 (2 부)**</span><span class="sxs-lookup"><span data-stu-id="7d80c-208">**Build and Deploy (part 2)**</span></span>

<span data-ttu-id="7d80c-209">이제 어떻게 공간 매핑 수 성능에 영향을 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-209">Now let's explore how Spatial Mapping can affect performance.</span></span>
* <span data-ttu-id="7d80c-210">Unity에서 선택 **창 > Profiler**합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-210">In Unity, select **Window > Profiler**.</span></span>
* <span data-ttu-id="7d80c-211">클릭 **Profiler 추가 > GPU**합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-211">Click **Add Profiler > GPU**.</span></span>
* <span data-ttu-id="7d80c-212">클릭 **활성 Profiler > <Enter IP>** 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-212">Click **Active Profiler > <Enter IP>**.</span></span>
* <span data-ttu-id="7d80c-213">입력 된 **IP 주소** 여 HoloLens의 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-213">Enter the **IP address** of your HoloLens.</span></span>
* <span data-ttu-id="7d80c-214">**연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-214">Click **Connect**.</span></span>
* <span data-ttu-id="7d80c-215">GPU에서 프레임을 렌더링 하는 데 걸리는 시간 (밀리초)의 수를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-215">Observe the number of milliseconds it takes for the GPU to render a frame.</span></span>
* <span data-ttu-id="7d80c-216">장치에서 실행에서 응용 프로그램을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-216">Stop the application from running on the device.</span></span>
* <span data-ttu-id="7d80c-217">Visual Studio로 돌아가서 연 **SpatialMappingObserver.cs**합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-217">Return to Visual Studio and open **SpatialMappingObserver.cs**.</span></span> <span data-ttu-id="7d80c-218">어셈블리-CSharp (유니버설 Windows) 프로젝트의 HoloToolkit\SpatialMapping 폴더에서 찾을 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-218">You will find it in the HoloToolkit\SpatialMapping folder of the Assembly-CSharp (Universal Windows) project.</span></span>
* <span data-ttu-id="7d80c-219">찾을 합니다 **Awake()** 함수 및 코드의 다음 줄을 추가 합니다. **TrianglesPerCubicMeter = 1200;**</span><span class="sxs-lookup"><span data-stu-id="7d80c-219">Find the **Awake()** function, and add the following line of code: **TrianglesPerCubicMeter = 1200;**</span></span>
* <span data-ttu-id="7d80c-220">장치 프로젝트를 다시 배포 차례로 **프로파일러를 다시 연결**합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-220">Re-deploy the project to your device, and then **reconnect the profiler**.</span></span> <span data-ttu-id="7d80c-221">프레임을 렌더링 하는 밀리초 수의 변경 내용을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-221">Observe the change in the number of milliseconds to render a frame.</span></span>
* <span data-ttu-id="7d80c-222">장치에서 실행에서 응용 프로그램을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-222">Stop the application from running on the device.</span></span>

<span data-ttu-id="7d80c-223">**저장 하 고 Unity에서 로드**</span><span class="sxs-lookup"><span data-stu-id="7d80c-223">**Save and load in Unity**</span></span>

<span data-ttu-id="7d80c-224">마지막으로, 보겠습니다 저장이 대화방 메시 하 고 Unity로 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-224">Finally, let's save our room mesh and load it into Unity.</span></span>
* <span data-ttu-id="7d80c-225">Visual Studio로 돌아가서 및 제거는 **TrianglesPerCubicMeter** 에서 추가한 줄 합니다 **Awake()** 함수에서 이전 섹션 중입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-225">Return to Visual Studio and remove the **TrianglesPerCubicMeter** line that you added in the **Awake()** function during the previous section.</span></span>
* <span data-ttu-id="7d80c-226">장치에 프로젝트를 다시 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-226">Redeploy the project to your device.</span></span> <span data-ttu-id="7d80c-227">에서는 이제 실행 해야 **500** 평방 미터당 삼각형입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-227">We should now be running with **500** triangles per cubic meter.</span></span>
* <span data-ttu-id="7d80c-228">브라우저를 열고로 이동 하 여 HoloLens IPAddress에를 입력 합니다 **Windows Device Portal**합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-228">Open a browser and enter in your HoloLens IPAddress to navigate to the **Windows Device Portal**.</span></span>
* <span data-ttu-id="7d80c-229">선택 된 **3D 뷰** 왼쪽된 패널의 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-229">Select the **3D View** option in the left panel.</span></span>
* <span data-ttu-id="7d80c-230">아래 **재구성 노출** 선택 합니다 **업데이트** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-230">Under **Surface reconstruction** select the **Update** button.</span></span>
* <span data-ttu-id="7d80c-231">표시 창에 표시 하 여 HoloLens에서 검색 한 영역을 시청 하세요.</span><span class="sxs-lookup"><span data-stu-id="7d80c-231">Watch as the areas that you have scanned on your HoloLens appear in the display window.</span></span>
* <span data-ttu-id="7d80c-232">키를 눌러에 공간 검색을 저장 하는 **저장** 단추.</span><span class="sxs-lookup"><span data-stu-id="7d80c-232">To save your room scan, press the **Save** button.</span></span>
* <span data-ttu-id="7d80c-233">오픈 프로그램 **다운로드** 저장된 공간이 모델을 찾을 폴더 **SRMesh.obj**합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-233">Open your **Downloads** folder to find the saved room model **SRMesh.obj**.</span></span>
* <span data-ttu-id="7d80c-234">복사본 **SRMesh.obj** 에 **자산** Unity 프로젝트의 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-234">Copy **SRMesh.obj** to the **Assets** folder of your Unity project.</span></span>
* <span data-ttu-id="7d80c-235">Unity에서 선택 합니다 **SpatialMapping** 개체를 **계층** 패널입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-235">In Unity, select the **SpatialMapping** object in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="7d80c-236">찾을 합니다 **개체 화면 관찰자 (스크립트)** 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-236">Locate the **Object Surface Observer (Script)** component.</span></span>
* <span data-ttu-id="7d80c-237">오른쪽에 원을 클릭 합니다 **방 모델** 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-237">Click the circle to the right of the **Room Model** property.</span></span>
* <span data-ttu-id="7d80c-238">찾기 및 선택 합니다 **SRMesh** 개체 및 다음 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-238">Find and select the **SRMesh** object and then close the window.</span></span>
* <span data-ttu-id="7d80c-239">되어 있는지 확인 합니다 **방 모델** 속성에는 **검사기** 패널으로 설정 되었습니다 **SRMesh**.</span><span class="sxs-lookup"><span data-stu-id="7d80c-239">Verify that the **Room Model** property in the **Inspector** panel is now set to **SRMesh**.</span></span>
* <span data-ttu-id="7d80c-240">키를 눌러 합니다 **재생** 단추 Unity의 미리 보기 모드로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-240">Press the **Play** button to enter Unity's preview mode.</span></span>
* <span data-ttu-id="7d80c-241">Unity에서 사용할 수 있도록 SpatialMapping 구성 요소 저장된 공간이 모델에서는 메시를 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-241">The SpatialMapping component will load the meshes from the saved room model so you can use them in Unity.</span></span>
* <span data-ttu-id="7d80c-242">전환할 **장면** 와이어 프레임 셰이더와 표시 공간 모델의 모든 표시 되도록 보기.</span><span class="sxs-lookup"><span data-stu-id="7d80c-242">Switch to **Scene** view to see all of your room model displayed with the wireframe shader.</span></span>
* <span data-ttu-id="7d80c-243">키를 눌러 합니다 **재생** 하려면 단추를 다시 미리 보기 모드를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-243">Press the **Play** button again to exit preview mode.</span></span>

<span data-ttu-id="7d80c-244">**참고:** Unity에서 미리 보기 모드를 시작 하는 다음에 저장 된 대화방 메시 기본적으로 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-244">**NOTE:** The next time that you enter preview mode in Unity, it will load the saved room mesh by default.</span></span>

## <a name="chapter-2---visualization"></a><span data-ttu-id="7d80c-245">2 장-시각화</span><span class="sxs-lookup"><span data-stu-id="7d80c-245">Chapter 2 - Visualization</span></span>

>[!VIDEO https://www.youtube.com/embed/RnkvXl-aXD4]

<span data-ttu-id="7d80c-246">**Objectives**</span><span class="sxs-lookup"><span data-stu-id="7d80c-246">**Objectives**</span></span>
* <span data-ttu-id="7d80c-247">셰이더의 기본 사항을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-247">Learn the basics of shaders.</span></span>
* <span data-ttu-id="7d80c-248">환경을 시각화 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-248">Visualize your surroundings.</span></span>

<span data-ttu-id="7d80c-249">**지침**</span><span class="sxs-lookup"><span data-stu-id="7d80c-249">**Instructions**</span></span>
* <span data-ttu-id="7d80c-250">Unity의 **계층 구조** 패널을 선택 합니다 **SpatialMapping** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-250">In Unity's **Hierarchy** panel, select the **SpatialMapping** object.</span></span>
* <span data-ttu-id="7d80c-251">에 **검사기** 패널에서 찾을 합니다 **공간 매핑 관리자 (스크립트)** 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-251">In the **Inspector** panel, find the **Spatial Mapping Manager (Script)** component.</span></span>
* <span data-ttu-id="7d80c-252">오른쪽에 원을 클릭 합니다 **표면 재질** 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-252">Click the circle to the right of the **Surface Material** property.</span></span>
* <span data-ttu-id="7d80c-253">찾기 및 선택 합니다 **BlueLinesOnWalls** material 및는 창 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-253">Find and select the **BlueLinesOnWalls** material and close the window.</span></span>
* <span data-ttu-id="7d80c-254">에 **프로젝트** 패널 **셰이더** 폴더를 두 번 클릭 **BlueLinesOnWalls** 를 Visual Studio에서 셰이더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-254">In the **Project** panel **Shaders** folder, double-click on **BlueLinesOnWalls** to open the shader in Visual Studio.</span></span>
* <span data-ttu-id="7d80c-255">이 간단한 픽셀 (조각 꼭 짓 점) 다음 작업을 수행 하는 셰이더:</span><span class="sxs-lookup"><span data-stu-id="7d80c-255">This is a simple pixel (vertex to fragment) shader, which accomplishes the following tasks:</span></span>
    1. <span data-ttu-id="7d80c-256">세계 좌표 공간을 꼭 짓 점을 위치를 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-256">Converts a vertex's location to world space.</span></span>
    2. <span data-ttu-id="7d80c-257">꼭 짓 점이 픽셀에 세로 인지 확인 하려면 normal을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-257">Checks the vertex's normal to determine if a pixel is vertical.</span></span>
    3. <span data-ttu-id="7d80c-258">렌더링 된 픽셀의 색을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-258">Sets the color of the pixel for rendering.</span></span>

<span data-ttu-id="7d80c-259">**빌드 및 배포**</span><span class="sxs-lookup"><span data-stu-id="7d80c-259">**Build and Deploy**</span></span>
* <span data-ttu-id="7d80c-260">Unity 및 키를 눌러 돌아갑니다 **재생** 미리 보기 모드로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-260">Return to Unity and press **Play** to enter preview mode.</span></span>
* <span data-ttu-id="7d80c-261">파란색 선은 (저장 된 검색 데이터에서 자동으로 로드)는 공간이 메시의 모든 세로 화면에 렌더링 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-261">Blue lines will be rendered on all vertical surfaces of the room mesh (which automatically loaded from our saved scanning data).</span></span>
* <span data-ttu-id="7d80c-262">으로 전환 합니다 **장면** 탭 대화방의 보기를 조정 하 여 전체 공간 메시 Unity에 표시 되는 방식을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7d80c-262">Switch to the **Scene** tab to adjust your view of the room and see how the entire room mesh appears in Unity.</span></span>
* <span data-ttu-id="7d80c-263">에 **프로젝트** 패널에서 찾을 **자료** 폴더를 선택 합니다 **BlueLinesOnWalls** 자료입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-263">In the **Project** panel, find the **Materials** folder and select the **BlueLinesOnWalls** material.</span></span>
* <span data-ttu-id="7d80c-264">일부 속성을 수정 하 고 Unity 편집기에서 변경 내용을 표시 하는 방법을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7d80c-264">Modify some properties and see how the changes appear in the Unity editor.</span></span>
    * <span data-ttu-id="7d80c-265">에 **검사기** 패널을 조정 합니다 **LineScale** 두꺼운 두께 표시 하는 줄을 확인 하는 값.</span><span class="sxs-lookup"><span data-stu-id="7d80c-265">In the **Inspector** panel, adjust the **LineScale** value to make the lines appear thicker or thinner.</span></span>
    * <span data-ttu-id="7d80c-266">에 **검사기** 패널을 조정 합니다 **LinesPerMeter** 각 담 벼 락에 표시 된 줄 수를 변경 하려면 값.</span><span class="sxs-lookup"><span data-stu-id="7d80c-266">In the **Inspector** panel, adjust the **LinesPerMeter** value to change how many lines appear on each wall.</span></span>
* <span data-ttu-id="7d80c-267">클릭 **재생** 미리 보기 모드를 종료 하는 다시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-267">Click **Play** again to exit preview mode.</span></span>
* <span data-ttu-id="7d80c-268">작성 하는 HoloLens에 배포 및 실제 화면에 렌더링 하는 셰이더 어떻게 표시 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-268">Build and deploy to the HoloLens and observe how the shader rendering appears on real surfaces.</span></span>

<span data-ttu-id="7d80c-269">Unity는 훌륭한 자료, 미리 보기의 이지만 항상 장치에서 체크 아웃 렌더링 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-269">Unity does a great job of previewing materials, but it's always a good idea to check-out rendering in the device.</span></span>

## <a name="chapter-3---processing"></a><span data-ttu-id="7d80c-270">3 장-처리</span><span class="sxs-lookup"><span data-stu-id="7d80c-270">Chapter 3 - Processing</span></span>

>[!VIDEO https://www.youtube.com/embed/kaUKiNiDxwY]

<span data-ttu-id="7d80c-271">**Objectives**</span><span class="sxs-lookup"><span data-stu-id="7d80c-271">**Objectives**</span></span>
* <span data-ttu-id="7d80c-272">응용 프로그램에서 사용 하기 위해 공간 매핑 데이터를 처리 하는 방법에 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-272">Learn techniques to process spatial mapping data for use in your application.</span></span>
* <span data-ttu-id="7d80c-273">평면을 검색 하 고 삼각형을 제거할 공간 매핑 데이터를 분석 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-273">Analyze spatial mapping data to find planes and remove triangles.</span></span>
* <span data-ttu-id="7d80c-274">홀로그램 배치에 대해 평면을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-274">Use planes for hologram placement.</span></span>

<span data-ttu-id="7d80c-275">**지침**</span><span class="sxs-lookup"><span data-stu-id="7d80c-275">**Instructions**</span></span>
* <span data-ttu-id="7d80c-276">Unity의 **프로젝트** 패널 **홀로그램** 폴더를 찾을 합니다 **SpatialProcessing** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-276">In Unity's **Project** panel, **Holograms** folder, find the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="7d80c-277">끌어서 놓기 합니다 **SpatialProcessing** 개체를 **계층** 패널입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-277">Drag & drop the **SpatialProcessing** object into the **Hierarchy** panel.</span></span>

<span data-ttu-id="7d80c-278">SpatialProcessing prefab 공간 매핑 데이터를 처리 하는 것에 대 한 구성 요소를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-278">The SpatialProcessing prefab includes components for processing the spatial mapping data.</span></span> <span data-ttu-id="7d80c-279">**SurfaceMeshesToPlanes.cs** 찾아 평면 공간 매핑 데이터를 기반으로 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-279">**SurfaceMeshesToPlanes.cs** will find and generate planes based on the spatial mapping data.</span></span> <span data-ttu-id="7d80c-280">바닥, 벽, 최대값이 나타내는 평면 응용 프로그램에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-280">We will use planes in our application to represent walls, floors and ceilings.</span></span> <span data-ttu-id="7d80c-281">이 prefab도 포함 되어 있습니다 **RemoveSurfaceVertices.cs** 공간 매핑 메시에 서 꼭 짓 점을 제거할 수는 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-281">This prefab also includes **RemoveSurfaceVertices.cs** which can remove vertices from the spatial mapping mesh.</span></span> <span data-ttu-id="7d80c-282">이 메시에 구멍을 생성 하거나 (평면 사용할 수 있으므로 대신) 더 이상 필요 없는 과도 한 삼각형을 제거 하도록 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-282">This can be used to create holes in the mesh, or to remove excess triangles that are no longer needed (because planes can be used instead).</span></span>
* <span data-ttu-id="7d80c-283">Unity의 **프로젝트** 패널 **홀로그램** 폴더를 찾을 합니다 **SpaceCollection** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-283">In Unity's **Project** panel, **Holograms** folder, find the **SpaceCollection** object.</span></span>
* <span data-ttu-id="7d80c-284">끌어서 놓기 합니다 **SpaceCollection** 개체를 **계층** 패널입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-284">Drag and drop the **SpaceCollection** object into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="7d80c-285">에 **계층** 패널을 선택 합니다 **SpatialProcessing** 개체.</span><span class="sxs-lookup"><span data-stu-id="7d80c-285">In the **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="7d80c-286">에 **검사기** 패널에서 찾을 합니다 **재생 공간 관리자 (스크립트)** 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-286">In the **Inspector** panel, find the **Play Space Manager (Script)** component.</span></span>
* <span data-ttu-id="7d80c-287">두 번 클릭 **PlaySpaceManager.cs** Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-287">Double-click on **PlaySpaceManager.cs** to open it in Visual Studio.</span></span>

<span data-ttu-id="7d80c-288">PlaySpaceManager.cs 응용 프로그램별 코드를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-288">PlaySpaceManager.cs contains application-specific code.</span></span> <span data-ttu-id="7d80c-289">이 스크립트는 다음 동작을 사용 하도록 설정 하려면 기능을 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-289">We will add functionality to this script to enable the following behavior:</span></span>
1. <span data-ttu-id="7d80c-290">검색 시간 제한 (10 초)를 초과 하는 후 공간 매핑을 데이터 수집을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-290">Stop collecting spatial mapping data after we exceed the scanning time limit (10 seconds).</span></span>
2. <span data-ttu-id="7d80c-291">공간 매핑 데이터를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-291">Process the spatial mapping data:</span></span>
    1. <span data-ttu-id="7d80c-292">SurfaceMeshesToPlanes 평면 (벽, 층, 최대값이 등)으로 전 세계의 간단한 표현을 만드는 데 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-292">Use SurfaceMeshesToPlanes to create a simpler representation of the world as planes (walls, floors, ceilings, etc).</span></span>
    2. <span data-ttu-id="7d80c-293">평면 경계 내에 속하는 노출 삼각형 제거할 RemoveSurfaceVertices를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-293">Use RemoveSurfaceVertices to remove surface triangles that fall within plane boundaries.</span></span>
3. <span data-ttu-id="7d80c-294">전 세계에서 홀로그램의 컬렉션을 생성 하 고 벽 및 층 평면 사용자 근처에 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-294">Generate a collection of holograms in the world and place them on wall and floor planes near the user.</span></span>

<span data-ttu-id="7d80c-295">PlaySpaceManager.cs, 표시 코딩 연습을 완료 하거나 아래에서 완성 된 솔루션을 사용 하 여 스크립트를 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-295">Complete the coding exercises marked in PlaySpaceManager.cs, or replace the script with the finished solution from below:</span></span>

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

<span data-ttu-id="7d80c-296">**빌드 및 배포**</span><span class="sxs-lookup"><span data-stu-id="7d80c-296">**Build and Deploy**</span></span>
* <span data-ttu-id="7d80c-297">키를 눌러는 HoloLens를 배포 하기 전에 합니다 **재생** 재생 모드로 전환 하는 Unity에서 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-297">Before deploying to the HoloLens, press the **Play** button in Unity to enter play mode.</span></span>
* <span data-ttu-id="7d80c-298">대화방 메시 파일에서 로드 되 면 처리 공간 매핑 메시에 서 시작 하기 전에 10 초 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-298">After the room mesh is loaded from file, wait for 10 seconds before processing starts on the spatial mapping mesh.</span></span>
* <span data-ttu-id="7d80c-299">처리가 완료 되 면 바닥, 벽, ceiling, 등을 나타내는 평면 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-299">When processing is complete, planes will appear to represent the floor, walls, ceiling, etc.</span></span>
* <span data-ttu-id="7d80c-300">결국 평면 중 발견 된 하나의 태양계 floor 카메라 근처의 테이블에 표시를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-300">After all of the planes have been found, you should see a solar system appear on a table of floor near the camera.</span></span>
* <span data-ttu-id="7d80c-301">두 가지 포스터는 너무 벽 카메라 근처에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-301">Two posters should appear on walls near the camera too.</span></span> <span data-ttu-id="7d80c-302">으로 전환 합니다 **장면** 탭에 표시 되지 않는 경우 **게임** 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-302">Switch to the **Scene** tab if you cannot see them in **Game** mode.</span></span>
* <span data-ttu-id="7d80c-303">키를 눌러 합니다 **재생** 다시 모드를 종료 하려면 play 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-303">Press the **Play** button again to exit play mode.</span></span>
* <span data-ttu-id="7d80c-304">빌드 및 HoloLens, 평소 대로 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-304">Build and deploy to the HoloLens, as usual.</span></span>
* <span data-ttu-id="7d80c-305">검색 및 완료 공간 매핑 데이터의 처리를 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-305">Wait for scanning and processing of the spatial mapping data to complete.</span></span>
* <span data-ttu-id="7d80c-306">평면에 표시 되 면 전 세계에서 태양계 및 포스터를 찾으려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-306">Once you see planes, try to find the solar system and posters in your world.</span></span>

## <a name="chapter-4---placement"></a><span data-ttu-id="7d80c-307">4 장-배치</span><span class="sxs-lookup"><span data-stu-id="7d80c-307">Chapter 4 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/Srhtpid1uZc]

<span data-ttu-id="7d80c-308">**Objectives**</span><span class="sxs-lookup"><span data-stu-id="7d80c-308">**Objectives**</span></span>
* <span data-ttu-id="7d80c-309">홀로그램 화면에 맞는 경우를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-309">Determine if a hologram will fit on a surface.</span></span>
* <span data-ttu-id="7d80c-310">화면에서를 홀로그램/없는 경우 사용자에 게 피드백을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-310">Provide feedback to the user when a hologram can/cannot fit on a surface.</span></span>

<span data-ttu-id="7d80c-311">**지침**</span><span class="sxs-lookup"><span data-stu-id="7d80c-311">**Instructions**</span></span>
* <span data-ttu-id="7d80c-312">Unity의 **계층 구조** 패널을 선택 합니다 **SpatialProcessing** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-312">In Unity's **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="7d80c-313">에 **검사기** 패널에서 찾을 합니다 **표면 메시를 평면 (스크립트)** 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-313">In the **Inspector** panel, find the **Surface Meshes To Planes (Script)** component.</span></span>
* <span data-ttu-id="7d80c-314">변경 된 **그리기 평면** 속성을 **Nothing** 선택을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-314">Change the **Draw Planes** property to **Nothing** to clear the selection.</span></span>
* <span data-ttu-id="7d80c-315">변경 합니다 **그리는 평면** 속성을 **벽**벽 평면에만 렌더링 될 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-315">Change the **Draw Planes** property to **Wall**, so that only wall planes will be rendered.</span></span>
* <span data-ttu-id="7d80c-316">에 **프로젝트** 패널 **스크립트** 폴더를 두 번 클릭 **Placeable.cs** Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-316">In the **Project** panel, **Scripts** folder, double-click on **Placeable.cs** to open it in Visual Studio.</span></span>

<span data-ttu-id="7d80c-317">합니다 **Placeable** 스크립트가 평면 찾기 완료 된 후 만들어진 포스터 및 프로젝션 상자에 이미 연결 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-317">The **Placeable** script is already attached to the posters and projection box that are created after plane finding completes.</span></span> <span data-ttu-id="7d80c-318">수행 해야 하는 것은 일부 코드를 주석 처리를 제거 하 고이 스크립트는 다음을 수행:</span><span class="sxs-lookup"><span data-stu-id="7d80c-318">All we need to do is uncomment some code, and this script will achieve the following:</span></span>
1. <span data-ttu-id="7d80c-319">홀로그램 플레이어가 중심 경계 큐브의 네 모퉁이를 여는 화면에 맞도록 경우를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-319">Determine if a hologram will fit on a surface by raycasting from the center and four corners of the bounding cube.</span></span>
2. <span data-ttu-id="7d80c-320">플러시 보관 홀로그램에 대 한 충분 한 부드러운 인지 확인 하는 일반적인 화면을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-320">Check the surface normal to determine if it is smooth enough for the hologram to sit flush on.</span></span>
3. <span data-ttu-id="7d80c-321">실제 크기로 배치 하는 동안 표시할 홀로그램 주위의 경계 큐브를 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-321">Render a bounding cube around the hologram to show its actual size while being placed.</span></span>
4. <span data-ttu-id="7d80c-322">아래/뒤 floor/벽에 배치 됩니다 여기서 표시할 홀로그램 섀도 캐스팅 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-322">Cast a shadow under/behind the hologram to show where it will be placed on the floor/wall.</span></span>
5. <span data-ttu-id="7d80c-323">그림자 빨강으로 렌더링할를 홀로그램 가능한 경우 녹색, 화면에 배치할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-323">Render the shadow as red, if the hologram cannot be placed on the surface, or green, if it can.</span></span>
6. <span data-ttu-id="7d80c-324">선호도 노출 종류 (세로 또는 가로)에 맞춰 홀로그램 방향을 다시 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-324">Re-orient the hologram to align with the surface type (vertical or horizontal) that it has affinity to.</span></span>
7. <span data-ttu-id="7d80c-325">이동 또는 동작을 맞추기 방지 하기 위해 선택한 화면에서를 홀로그램을 원활 하 게 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-325">Smoothly place the hologram on the selected surface to avoid jumping or snapping behavior.</span></span>

<span data-ttu-id="7d80c-326">아래 코딩 연습에서 모든 코드 주석 처리를 제거 하거나이 완료 된 솔루션에서 사용 하 여 **Placeable.cs**:</span><span class="sxs-lookup"><span data-stu-id="7d80c-326">Uncomment all code in the coding exercise below, or use this completed solution in **Placeable.cs**:</span></span>

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

<span data-ttu-id="7d80c-327">**빌드 및 배포**</span><span class="sxs-lookup"><span data-stu-id="7d80c-327">**Build and Deploy**</span></span>
* <span data-ttu-id="7d80c-328">이전과 마찬가지로 프로젝트를 빌드하고 HoloLens에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-328">As before, build the project and deploy to the HoloLens.</span></span>
* <span data-ttu-id="7d80c-329">검색 및 완료 공간 매핑 데이터의 처리를 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-329">Wait for scanning and processing of the spatial mapping data to complete.</span></span>
* <span data-ttu-id="7d80c-330">태양계에 표시 되 면 아래에 있는 프로젝션 상자 응시 고 해 선택 제스처를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-330">When you see the solar system, gaze at the projection box below and perform a select gesture to move it around.</span></span> <span data-ttu-id="7d80c-331">프로젝션 확인란을 선택 하는 동안 경계 큐브 프로젝션 상자 주위에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-331">While the projection box is selected, a bounding cube will be visible around the projection box.</span></span>
* <span data-ttu-id="7d80c-332">대화방의 다른 위치를 응시 이동을 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-332">Move you head to gaze at a different location in the room.</span></span> <span data-ttu-id="7d80c-333">프로젝션 상자에 응시를 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-333">The projection box should follow your gaze.</span></span> <span data-ttu-id="7d80c-334">프로젝션 상자 아래의 그림자 색이 빨강으로 홀로그램 해당 화면에 배치할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-334">When the shadow below the projection box turns red, you cannot place the hologram on that surface.</span></span> <span data-ttu-id="7d80c-335">프로젝션 상자 아래의 섀도 녹색 바뀌면 다른 선택 제스처를 수행 하 여를 홀로그램을 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-335">When the shadow below the projection box turns green, you can place the hologram by performing another select gesture.</span></span>
* <span data-ttu-id="7d80c-336">찾기 및 새 위치로 이동할 벽 holographic 포스터 중 하나를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-336">Find and select one of the holographic posters on a wall to move it to a new location.</span></span> <span data-ttu-id="7d80c-337">Floor 또는 한계 포스터를 배치할 수 없습니다 하 고 항상 각 옆면에 올바르게 방향 이동 살펴보세요.</span><span class="sxs-lookup"><span data-stu-id="7d80c-337">Notice that you cannot place the poster on the floor or ceiling, and that it stays correctly oriented to each wall as you move around.</span></span>

## <a name="chapter-5---occlusion"></a><span data-ttu-id="7d80c-338">5 장-폐색</span><span class="sxs-lookup"><span data-stu-id="7d80c-338">Chapter 5 - Occlusion</span></span>

>[!VIDEO https://www.youtube.com/embed/6Xrzh_w-7SE]

<span data-ttu-id="7d80c-339">**Objectives**</span><span class="sxs-lookup"><span data-stu-id="7d80c-339">**Objectives**</span></span>
* <span data-ttu-id="7d80c-340">공간 매핑 관계로 홀로그램 폐색는 경우를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-340">Determine if a hologram is occluded by the spatial mapping mesh.</span></span>
* <span data-ttu-id="7d80c-341">재미 있는 달성 하기 위해 다른 폐색 기술을 적용할 효과입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-341">Apply different occlusion techniques to achieve a fun effect.</span></span>

<span data-ttu-id="7d80c-342">**지침**</span><span class="sxs-lookup"><span data-stu-id="7d80c-342">**Instructions**</span></span>

<span data-ttu-id="7d80c-343">먼저 실제 occluding 없이 다른 홀로그램 채워집니다에 공간 매핑 메시를 허용 하려는:</span><span class="sxs-lookup"><span data-stu-id="7d80c-343">First, we are going to allow the spatial mapping mesh to occlude other holograms without occluding the real world:</span></span>
* <span data-ttu-id="7d80c-344">에 **계층** 패널을 선택 합니다 **SpatialProcessing** 개체.</span><span class="sxs-lookup"><span data-stu-id="7d80c-344">In the **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="7d80c-345">에 **검사기** 패널에서 찾을 합니다 **재생 공간 관리자 (스크립트)** 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-345">In the **Inspector** panel, find the **Play Space Manager (Script)** component.</span></span>
* <span data-ttu-id="7d80c-346">오른쪽에 원을 클릭 합니다 **보조 자료** 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-346">Click the circle to the right of the **Secondary Material** property.</span></span>
* <span data-ttu-id="7d80c-347">찾기 및 선택 합니다 **폐색** material 및는 창 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-347">Find and select the **Occlusion** material and close the window.</span></span>

<span data-ttu-id="7d80c-348">다음으로, 하겠습니다 지구, 특별 한 동작을 추가할 때마다 (예: 일요일), 다른 홀로그램 하거나 공간 매핑 메시 여 폐색 됩니다 파란색 강조 표시가 포함 되도록:</span><span class="sxs-lookup"><span data-stu-id="7d80c-348">Next, we are going to add a special behavior to Earth, so that it has a blue highlight whenever it becomes occluded by another hologram (like the sun), or by the spatial mapping mesh:</span></span>
* <span data-ttu-id="7d80c-349">에 **프로젝트** 패널를 **홀로그램** 폴더를 확장 합니다 **SolarSystem** 개체.</span><span class="sxs-lookup"><span data-stu-id="7d80c-349">In the **Project** panel, in the **Holograms** folder, expand the **SolarSystem** object.</span></span>
* <span data-ttu-id="7d80c-350">클릭할 **지구**합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-350">Click on **Earth**.</span></span>
* <span data-ttu-id="7d80c-351">에 **검사기** 패널에서 지구 자료 (아래 구성 요소)를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-351">In the **Inspector** panel, find the Earth's material (bottom component).</span></span>
* <span data-ttu-id="7d80c-352">에 **셰이더 드롭다운**, 셰이더를 변경할 **사용자 지정 > OcclusionRim**합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-352">In the **Shader drop-down**, change the shader to **Custom > OcclusionRim**.</span></span> <span data-ttu-id="7d80c-353">이 다른 개체에 의해 폐색는 때마다 지구 주변의 파란색 강조 표시를 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-353">This will render a blue highlight around Earth whenever it is occluded by another object.</span></span>

<span data-ttu-id="7d80c-354">마지막으로, 태양 시스템에서 행성에 대 한 x-레이 시각 효과 사용 하도록 설정 하는 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-354">Finally, we are going to enable an x-ray vision effect for planets in our solar system.</span></span> <span data-ttu-id="7d80c-355">편집 해야 합니다 **PlanetOcclusion.cs** (Scripts\SolarSystem 폴더에 있음) 다음을 구현 하려면:</span><span class="sxs-lookup"><span data-stu-id="7d80c-355">We will need to edit **PlanetOcclusion.cs** (found in the Scripts\SolarSystem folder) in order to achieve the following:</span></span>
1. <span data-ttu-id="7d80c-356">전 세계 SpatialMapping 계층 (대화방 메시 및 비행기)에서 폐색는 경우를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-356">Determine if a planet is occluded by the SpatialMapping layer (room meshes and planes).</span></span>
2. <span data-ttu-id="7d80c-357">SpatialMapping 계층에서 폐색는 때마다는 전 세계의 와이어 프레임 표현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-357">Show the wireframe representation of a planet whenever it is occluded by the SpatialMapping layer.</span></span>
3. <span data-ttu-id="7d80c-358">SpatialMapping 계층에서 차단 되지 않는 경우에 전 세계의 와이어 프레임 표현을 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-358">Hide the wireframe representation of a planet when it is not blocked by the SpatialMapping layer.</span></span>

<span data-ttu-id="7d80c-359">PlanetOcclusion.cs의 코딩 연습을 따르거나 다음 솔루션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-359">Follow the coding exercise in PlanetOcclusion.cs, or use the following solution:</span></span>

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

<span data-ttu-id="7d80c-360">**빌드 및 배포**</span><span class="sxs-lookup"><span data-stu-id="7d80c-360">**Build and Deploy**</span></span>
* <span data-ttu-id="7d80c-361">빌드 및 HoloLens, 응용 프로그램을 평소 대로 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-361">Build and deploy the application to HoloLens, as usual.</span></span>
* <span data-ttu-id="7d80c-362">검색 및 완료 되기를 공간 매핑 데이터의 처리를 위해 대기 (벽에 표시 되는 파란색 줄이 표시 됩니다).</span><span class="sxs-lookup"><span data-stu-id="7d80c-362">Wait for scanning and processing of the spatial mapping data to be complete (you should see blue lines appear on walls).</span></span>
* <span data-ttu-id="7d80c-363">찾을 태양계의 프로젝션 상자를 선택 하 고 카운터 빠르거나 벽 옆에 있는 상자를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-363">Find and select the solar system's projection box and then set the box next to a wall or behind a counter.</span></span>
* <span data-ttu-id="7d80c-364">기본 폐색 숨기기 포스터 또는 프로젝션 box에서 피어 링 하려면 화면 뒤에서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-364">You can view basic occlusion by hiding behind surfaces to peer at the poster or projection box.</span></span>
* <span data-ttu-id="7d80c-365">지구를 찾고, 다른 홀로그램 또는 화면 뒤 만약 때마다 파란색 강조 표시가 적용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-365">Look for the Earth, there should be a blue highlight effect whenever it goes behind another hologram or surface.</span></span>
* <span data-ttu-id="7d80c-366">행성 벽 또는 단체 실에 다른 화면 뒤 나가면서를 시청 하세요.</span><span class="sxs-lookup"><span data-stu-id="7d80c-366">Watch as the planets move behind the wall or other surfaces in the room.</span></span> <span data-ttu-id="7d80c-367">이제 레이 투시 능력이 있고 해당 와이어 프레임 구조를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-367">You now have x-ray vision and can see their wireframe skeletons!</span></span>

## <a name="the-end"></a><span data-ttu-id="7d80c-368">끝</span><span class="sxs-lookup"><span data-stu-id="7d80c-368">The End</span></span>

<span data-ttu-id="7d80c-369">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-369">Congratulations!</span></span> <span data-ttu-id="7d80c-370">이제 완료 **MR 공간 230: 공간 매핑**합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-370">You have now completed **MR Spatial 230: Spatial mapping**.</span></span>
* <span data-ttu-id="7d80c-371">Unity에 환경 및 부하 공간 매핑 데이터를 검색 하는 방법을 알고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-371">You know how to scan your environment and load spatial mapping data to Unity.</span></span>
* <span data-ttu-id="7d80c-372">셰이더와 다시 전 세계를 시각화 자료를 사용할 수 있는 방법을의 기초를 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-372">You understand the basics of shaders and how materials can be used to re-visualize the world.</span></span>
* <span data-ttu-id="7d80c-373">평면을 찾고 삼각형 메시에서 제거 하기 위한 새 처리 기술을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-373">You learned of new processing techniques for finding planes and removing triangles from a mesh.</span></span>
* <span data-ttu-id="7d80c-374">이동 하 고 있는 것은 타당 표면 홀로그램 배치 수 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="7d80c-374">You were able to move and place holograms on surfaces that made sense.</span></span>
* <span data-ttu-id="7d80c-375">다른 폐색 기술을 발생 하 고 레이 투시 능력이의 강력한 성능을 활용!</span><span class="sxs-lookup"><span data-stu-id="7d80c-375">You experienced different occlusion techniques and harnessed the power of x-ray vision!</span></span>
