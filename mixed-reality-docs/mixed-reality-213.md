---
title: MR 입력 213
description: Unity, Visual Studio 및 몰입 형 헤드셋을 사용 하 여이 코딩 자습서를 수행 하 여 동작 컨트롤러의 세부 정보를 알아보세요.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, 동작 컨트롤러, 아카데미, 자습서
ms.openlocfilehash: 85449795a4fb3d182101cb5b4c4ce3fe85b009c0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516352"
---
>[!NOTE]
><span data-ttu-id="19289-104">혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="19289-105">따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="19289-106">이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="19289-107">지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19289-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="19289-108">향후에는 HoloLens 2를 개발 하는 방법을 보여 주는 새 자습서 시리즈를 게시할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="19289-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="19289-109">이 알림은 게시 될 때 해당 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19289-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-input-213-motion-controllers"></a><span data-ttu-id="19289-110">MR 입력 213: 동작 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="19289-110">MR Input 213: Motion controllers</span></span>

<span data-ttu-id="19289-111">혼합 현실 세계의 동작 컨트롤러는 다른 수준의 대화형 작업을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-111">Motion controllers in the mixed reality world add another level of interactivity.</span></span> <span data-ttu-id="19289-112">[동작 컨트롤러](motion-controllers.md)를 사용 하 여 집중 교육 및 즐거움를 응용 프로그램 환경에서 확장 하는 실제 상호 작용과 비슷하게 보다 자연스럽 게 개체와 직접 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-112">With [motion controllers](motion-controllers.md), we can directly interact with objects in a more natural way, similar to our physical interactions in real life, increasing immersion and delight in your app experience.</span></span>

<span data-ttu-id="19289-113">MR 입력 213에서는 간단한 공간 그리기 환경을 만들어 동작 컨트롤러의 입력 이벤트를 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-113">In MR Input 213, we will explore the motion controller's input events by creating a simple spatial painting experience.</span></span> <span data-ttu-id="19289-114">이 앱을 사용 하면 다양 한 유형의 브러시 및 색을 사용 하 여 3 차원 공간으로 그릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-114">With this app, users can paint in three-dimensional space with various types of brushes and colors.</span></span>

## <a name="topics-covered-in-this-tutorial"></a><span data-ttu-id="19289-115">이 자습서에서 다루는 항목</span><span class="sxs-lookup"><span data-stu-id="19289-115">Topics covered in this tutorial</span></span>

|![MixedReality213 Topic1](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|<span data-ttu-id="19289-119">**컨트롤러 시각화**</span><span class="sxs-lookup"><span data-stu-id="19289-119">**Controller visualization**</span></span>|<span data-ttu-id="19289-120">**컨트롤러 입력 이벤트**</span><span class="sxs-lookup"><span data-stu-id="19289-120">**Controller input events**</span></span>|<span data-ttu-id="19289-121">**사용자 지정 컨트롤러 및 UI**</span><span class="sxs-lookup"><span data-stu-id="19289-121">**Custom controller and UI**</span></span>|
|<span data-ttu-id="19289-122">Unity의 게임 모드 및 런타임에 동작 컨트롤러 모델을 렌더링 하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="19289-122">Learn how to render motion controller models in Unity's game mode and runtime.</span></span>|<span data-ttu-id="19289-123">다양 한 종류의 단추 이벤트 및 해당 응용 프로그램을 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-123">Understand different types of button events and their applications.</span></span>|<span data-ttu-id="19289-124">컨트롤러 위에 UI 요소를 오버레이 하거나 완전히 사용자 지정 하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="19289-124">Learn how to overlay UI elements on top of the controller or fully customize it.</span></span>|

## <a name="device-support"></a><span data-ttu-id="19289-125">장치 지원</span><span class="sxs-lookup"><span data-stu-id="19289-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="19289-126">과정</span><span class="sxs-lookup"><span data-stu-id="19289-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="19289-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="19289-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="19289-128"><a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="19289-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="19289-129">MR 입력 213: 동작 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="19289-129">MR Input 213: Motion controllers</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="19289-130">✔️</span><span class="sxs-lookup"><span data-stu-id="19289-130">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="19289-131">시작하기 전 주의 사항</span><span class="sxs-lookup"><span data-stu-id="19289-131">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="19289-132">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="19289-132">Prerequisites</span></span>

<span data-ttu-id="19289-133">[이 페이지](install-the-tools.md)의 모던 헤드셋에 대 한 설치 검사 목록을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="19289-133">See the installation checklist for immersive headsets on [this page](install-the-tools.md).</span></span>

* <span data-ttu-id="19289-134">이 자습서에는 [Unity 2017.2.1 p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe) 가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-134">This tutorial requires [Unity 2017.2.1p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)</span></span>

### <a name="project-files"></a><span data-ttu-id="19289-135">프로젝트 파일</span><span class="sxs-lookup"><span data-stu-id="19289-135">Project files</span></span>

* <span data-ttu-id="19289-136">프로젝트에 필요한 [파일을 다운로드](https://github.com/Microsoft/MixedReality213/archive/master.zip) 하 고 바탕 화면에 파일을 추출 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-136">[Download the files](https://github.com/Microsoft/MixedReality213/archive/master.zip) required by the project and extract the files to the Desktop.</span></span>

>[!NOTE]
><span data-ttu-id="19289-137">다운로드 하기 전에 소스 코드를 확인 하려는 경우 [GitHub에서 사용할 수](https://github.com/Microsoft/MixedReality213)있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/MixedReality213).</span></span>

## <a name="unity-setup"></a><span data-ttu-id="19289-138">Unity 설치</span><span class="sxs-lookup"><span data-stu-id="19289-138">Unity setup</span></span>

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a><span data-ttu-id="19289-139">목표</span><span class="sxs-lookup"><span data-stu-id="19289-139">Objectives</span></span>

* <span data-ttu-id="19289-140">Windows Mixed Reality 개발을 위한 Unity 최적화</span><span class="sxs-lookup"><span data-stu-id="19289-140">Optimize Unity for Windows Mixed Reality development</span></span>
* <span data-ttu-id="19289-141">혼합 현실 설치 카메라</span><span class="sxs-lookup"><span data-stu-id="19289-141">Setup Mixed Reality Camera</span></span>
* <span data-ttu-id="19289-142">설정 환경</span><span class="sxs-lookup"><span data-stu-id="19289-142">Setup environment</span></span>

### <a name="instructions"></a><span data-ttu-id="19289-143">지침</span><span class="sxs-lookup"><span data-stu-id="19289-143">Instructions</span></span>

* <span data-ttu-id="19289-144">Unity를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-144">Start Unity.</span></span>
* <span data-ttu-id="19289-145">**열기**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-145">Select **Open**.</span></span>
* <span data-ttu-id="19289-146">바탕 화면으로 이동 하 여 이전에 unarchived **MixedReality213** 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-146">Navigate to your Desktop and find the **MixedReality213-master** folder you previously unarchived.</span></span>
* <span data-ttu-id="19289-147">**폴더 선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-147">Click **Select Folder**.</span></span>
* <span data-ttu-id="19289-148">Unity에서 프로젝트 파일 로드를 마치면 Unity 편집기를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-148">Once Unity finishes loading project files, you will be able to see Unity editor.</span></span>
* <span data-ttu-id="19289-149">Unity에서 **파일 > 빌드 설정**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-149">In Unity, select **File > Build Settings**.</span></span>

![MR213_BuildSettings](images/mr213-buildsettings-450px.png)
* <span data-ttu-id="19289-151">**플랫폼** 목록에서 **유니버설 Windows 플랫폼** 을 선택 하 고 **플랫폼 전환** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-151">Select **Universal Windows Platform** in the **Platform** list and click the **Switch Platform** button.</span></span>
* <span data-ttu-id="19289-152">대상 장치를 **모든 장치로** 설정</span><span class="sxs-lookup"><span data-stu-id="19289-152">Set Target Device to **Any device**</span></span>
* <span data-ttu-id="19289-153">빌드 유형을 **D3D** 로 설정</span><span class="sxs-lookup"><span data-stu-id="19289-153">Set Build Type to **D3D**</span></span>
* <span data-ttu-id="19289-154">SDK를 **최신 설치** 로 설정</span><span class="sxs-lookup"><span data-stu-id="19289-154">Set SDK to **Latest Installed**</span></span>
* <span data-ttu-id="19289-155">**Unity C# 프로젝트** 확인</span><span class="sxs-lookup"><span data-stu-id="19289-155">Check **Unity C# Projects**</span></span>
    * <span data-ttu-id="19289-156">이를 통해 Unity 프로젝트를 다시 빌드하지 않고 Visual Studio 프로젝트에서 스크립트 파일을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-156">This allows you modify script files in the Visual Studio project without rebuilding Unity project.</span></span>
* <span data-ttu-id="19289-157">**플레이어 설정**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-157">Click **Player Settings**.</span></span>
* <span data-ttu-id="19289-158">**검사기** 패널에서 아래쪽으로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-158">In the **Inspector** panel, scroll down to the bottom</span></span>
* <span data-ttu-id="19289-159">XR 설정에서 **지원 되는 가상 현실** 확인</span><span class="sxs-lookup"><span data-stu-id="19289-159">In XR Settings, check **Virtual Reality Supported**</span></span>
* <span data-ttu-id="19289-160">가상 현실 Sdk에서 **Windows Mixed reality** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-160">Under Virtual Reality SDKs, select **Windows Mixed Reality**</span></span>

![MR213_XRSettings](images/mr213-xrsettings-500px.png)
* <span data-ttu-id="19289-162">**빌드 설정** 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-162">Close **Build Settings** window.</span></span>

### <a name="project-structure"></a><span data-ttu-id="19289-163">프로젝트 구조</span><span class="sxs-lookup"><span data-stu-id="19289-163">Project structure</span></span>

<span data-ttu-id="19289-164">이 자습서에서는 **[Mixed Reality Toolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-164">This tutorial uses **[Mixed Reality Toolkit - Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)**.</span></span> <span data-ttu-id="19289-165">[이 페이지](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)에서 릴리스를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-165">You can find the releases on [this page](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span></span>

![ProjectStructure](images/mr213-projectstructure-650px.png)

<span data-ttu-id="19289-167">**참조용으로 완료 된 장면**</span><span class="sxs-lookup"><span data-stu-id="19289-167">**Completed scenes for your reference**</span></span>
* <span data-ttu-id="19289-168">**백그라운드** 폴더 아래에 두 개의 완료 된 Unity 장면을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-168">You will find two completed Unity scenes under **Scenes** folder.</span></span>
    * <span data-ttu-id="19289-169">**MixedReality213**: 단일 브러시를 사용 하 여 완료 된 장면</span><span class="sxs-lookup"><span data-stu-id="19289-169">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="19289-170">**MixedReality213Advanced**: 여러 브러시가 있는 고급 디자인을 위한 완료 된 장면</span><span class="sxs-lookup"><span data-stu-id="19289-170">**MixedReality213Advanced**: Completed scene for advanced design with multiple brushes</span></span>

<span data-ttu-id="19289-171">**자습서에 대 한 새 장면 설정**</span><span class="sxs-lookup"><span data-stu-id="19289-171">**New Scene setup for the tutorial**</span></span>
* <span data-ttu-id="19289-172">Unity에서 **파일 > 새 장면** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-172">In Unity, click **File > New Scene**</span></span>
* <span data-ttu-id="19289-173">**기본 카메라** 및 **방향성 광원** 삭제</span><span class="sxs-lookup"><span data-stu-id="19289-173">Delete **Main Camera** and **Directional Light**</span></span>
* <span data-ttu-id="19289-174">**프로젝트 패널**에서 다음 prefabs을 검색 하 여 **계층** 패널로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="19289-174">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="19289-175">Asset/HoloToolkit/Input/Prefabs/**MixedRealityCamera**</span><span class="sxs-lookup"><span data-stu-id="19289-175">Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**</span></span>
    * <span data-ttu-id="19289-176">자산/AppPrefabs/**환경**</span><span class="sxs-lookup"><span data-stu-id="19289-176">Assets/AppPrefabs/**Environment**</span></span>

![카메라 및 환경](images/mr213-cameraenvironment-300px.jpg)
* <span data-ttu-id="19289-178">혼합 현실 도구 키트에는 두 가지 카메라 prefabs 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-178">There are two camera prefabs in Mixed Reality Toolkit:</span></span>
    * <span data-ttu-id="19289-179">**Prefab MixedRealityCamera**: 카메라 전용</span><span class="sxs-lookup"><span data-stu-id="19289-179">**MixedRealityCamera.prefab**: Camera only</span></span>
    * <span data-ttu-id="19289-180">**Prefab MixedRealityCameraParent**: 카메라 + Teleportation + 경계</span><span class="sxs-lookup"><span data-stu-id="19289-180">**MixedRealityCameraParent.prefab**: Camera + Teleportation + Boundary</span></span>
    * <span data-ttu-id="19289-181">이 자습서에서는 teleportation 기능 없이 **MixedRealityCamera** 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-181">In this tutorial, we will use **MixedRealityCamera** without teleportation feature.</span></span> <span data-ttu-id="19289-182">이로 인해 사용자가 접지 되도록 기본적인 층을 포함 하는 간단한 **환경** prefab를 추가 했습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-182">Because of this, we added simple **Environment** prefab which contains a basic floor to make the user feel grounded.</span></span>
    * <span data-ttu-id="19289-183">**MixedRealityCameraParent**를 사용 하 여 teleportation에 대 한 자세한 내용은 [고급 디자인-teleportation 및 locomotion](#advanced-design---teleportation-and-locomotion) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="19289-183">To learn more about the teleportation with **MixedRealityCameraParent**, see [Advanced design - Teleportation and locomotion](#advanced-design---teleportation-and-locomotion)</span></span>

<span data-ttu-id="19289-184">**Skybox 설정**</span><span class="sxs-lookup"><span data-stu-id="19289-184">**Skybox setup**</span></span>
* <span data-ttu-id="19289-185">**창 > 조명 > 설정** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-185">Click **Window > Lighting > Settings**</span></span>
* <span data-ttu-id="19289-186">**Skybox 재질 필드** 의 오른쪽에 있는 원을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-186">Click the circle on the right side of the **Skybox Material field**</span></span>
* <span data-ttu-id="19289-187">' 회색 '을 입력 하 고 **SkyboxGray** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-187">Type in ‘gray’ and select **SkyboxGray**</span></span>

<span data-ttu-id="19289-188">(자산/AppPrefabs/지원/재질/SkyboxGray)</span><span class="sxs-lookup"><span data-stu-id="19289-188">(Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)</span></span>

![Skybox 설정](images/mr123-skyboxsetting-400px.jpg)
* <span data-ttu-id="19289-190">할당 된 회색 그라데이션 Skybox을 볼 수 있도록 **Skybox** 옵션을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-190">Check **Skybox** option to be able to see assigned gray gradient skybox</span></span>

![Skybox 옵션 설정/해제](images/mr213-skyboxcheck-400px.jpg)
* <span data-ttu-id="19289-192">MixedRealityCamera, 환경 및 회색 skybox이 포함 된 장면을 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19289-192">The scene with MixedRealityCamera, Environment and gray skybox will look like this.</span></span>

![MixedReality213 환경](images/mr213-environment-600px.jpg)
* <span data-ttu-id="19289-194">**파일 > 장면 저장을** 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-194">Click **File > Save Scene as**</span></span>
* <span data-ttu-id="19289-195">모든 이름의 장면 폴더 아래에 장면 **저장**</span><span class="sxs-lookup"><span data-stu-id="19289-195">**Save** your scene under Scenes folder with any name</span></span>

## <a name="chapter-1---controller-visualization"></a><span data-ttu-id="19289-196">1 장-컨트롤러 시각화</span><span class="sxs-lookup"><span data-stu-id="19289-196">Chapter 1 - Controller visualization</span></span>

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a><span data-ttu-id="19289-197">목표</span><span class="sxs-lookup"><span data-stu-id="19289-197">Objectives</span></span>

* <span data-ttu-id="19289-198">Unity의 게임 모드 및 런타임에 동작 컨트롤러 모델을 렌더링 하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="19289-198">Learn how to render motion controller models in Unity's game mode and at runtime.</span></span>

<span data-ttu-id="19289-199">Windows Mixed Reality는 컨트롤러 시각화를 위한 애니메이션 컨트롤러 모델을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-199">Windows Mixed Reality provides an animated controller model for controller visualization.</span></span> <span data-ttu-id="19289-200">앱에서 컨트롤러 시각화에 대해 수행할 수 있는 몇 가지 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-200">There are several approaches you can take for controller visualization in your app:</span></span>
* <span data-ttu-id="19289-201">기본값-수정 하지 않고 기본 컨트롤러 사용</span><span class="sxs-lookup"><span data-stu-id="19289-201">Default - Using default controller without modification</span></span>
* <span data-ttu-id="19289-202">하이브리드-기본 컨트롤러를 사용 하지만 일부 요소 또는 겹쳐 있는 UI 구성 요소를 사용자 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-202">Hybrid - Using default controller, but customizing some of its elements or overlaying UI components</span></span>
* <span data-ttu-id="19289-203">대체-컨트롤러에 대해 사용자 지정 된 사용자 지정 3D 모델 사용</span><span class="sxs-lookup"><span data-stu-id="19289-203">Replacement - Using your own customized 3D model for the controller</span></span>

<span data-ttu-id="19289-204">이 장에서는 이러한 컨트롤러 사용자 지정의 예제에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="19289-204">In this chapter, we will learn about the examples of these controller customizations.</span></span>

### <a name="instructions"></a><span data-ttu-id="19289-205">지침</span><span class="sxs-lookup"><span data-stu-id="19289-205">Instructions</span></span>

* <span data-ttu-id="19289-206">**프로젝트** 패널의 검색 상자에 **motioncontrollers** 를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-206">In the **Project** panel, type **MotionControllers** in the search box .</span></span> <span data-ttu-id="19289-207">자산/HoloToolkit/입력/Prefabs/에서 찾을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-207">You can also find it under Assets/HoloToolkit/Input/Prefabs/.</span></span>
* <span data-ttu-id="19289-208">**Motioncontrollers** Prefab을 **계층** 패널로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="19289-208">Drag the **MotionControllers** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="19289-209">**계층** 패널에서 **motioncontrollers** prefab를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-209">Click on the **MotionControllers** prefab in the **Hierarchy** panel.</span></span>

<span data-ttu-id="19289-210">**MotionControllers prefab**</span><span class="sxs-lookup"><span data-stu-id="19289-210">**MotionControllers prefab**</span></span>

<span data-ttu-id="19289-211">**Motioncontrollers** prefab에는 대체 컨트롤러 모델용 슬롯을 제공 하는 **Motioncontroller시각기** 스크립트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-211">**MotionControllers** prefab has a **MotionControllerVisualizer** script which provides the slots for alternate controller models.</span></span> <span data-ttu-id="19289-212">손 또는 소드와 같은 사용자 지정 3D 모델을 할당 하 고 ' 항상 대체 왼쪽/오른쪽 모델 사용 '을 선택 하면 기본 모델 대신 해당 모델이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19289-212">If you assign your own custom 3D models such as a hand or a sword and check 'Always Use Alternate Left/Right Model', you will see them instead of the default model.</span></span> <span data-ttu-id="19289-213">4 장에서이 슬롯을 사용 하 여 컨트롤러 모델을 브러시로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="19289-213">We will use this slot in Chapter 4 to replace the controller model with a brush.</span></span>

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

<span data-ttu-id="19289-215">**지침**</span><span class="sxs-lookup"><span data-stu-id="19289-215">**Instructions**</span></span>
* <span data-ttu-id="19289-216">**검사기** 패널에서 **Motioncontrollervisualizer** 스크립트를 두 번 클릭 하 여 Visual Studio에서 코드를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-216">In the **Inspector** panel, double click **MotionControllerVisualizer** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="19289-217">**MotionControllerVisualizer 도우미 스크립트**</span><span class="sxs-lookup"><span data-stu-id="19289-217">**MotionControllerVisualizer script**</span></span>

<span data-ttu-id="19289-218">**Motioncontrollervisualizer** 및 **Motioncontrollervisualizer** 클래스는 기본 컨트롤러 모델을 액세스 & 수정 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-218">The **MotionControllerVisualizer** and **MotionControllerInfo** classes provide the means to access & modify the default controller models.</span></span> <span data-ttu-id="19289-219">**Motioncontrollervisualizer** 는 Unity의 **InteractionSourceDetected** 이벤트를 구독 하 고 발견 되 면 컨트롤러 모델을 자동으로 인스턴스화합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-219">**MotionControllerVisualizer** subscribes to Unity's **InteractionSourceDetected** event and automatically instantiates controller models when they are found.</span></span>

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

<span data-ttu-id="19289-220">컨트롤러 모델은 고 지 수 [설정](https://github.com/KhronosGroup/glTF)에 따라 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19289-220">The controller models are delivered according to [the glTF specification](https://github.com/KhronosGroup/glTF).</span></span> <span data-ttu-id="19289-221">이 형식은 공통 형식을 제공 하기 위해 만들어졌지만 3D 자산의 전송 및 압축 풀기의 프로세스를 개선 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-221">This format has been created to provide a common format, while improving the process behind transmitting and unpacking 3D assets.</span></span> <span data-ttu-id="19289-222">이 경우 가능한 한 원활 하 게 사용자 환경을 만들고 사용자가 사용 중일 수 있는 동작 컨트롤러의 버전을 보장 하지 않기 때문에 런타임에 컨트롤러 모델을 검색 하 고 로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-222">In this case, we need to retrieve and load the controller models at runtime, as we want to make the user's experience as seamless as possible, and it's not guaranteed which version of the motion controllers the user might be using.</span></span> <span data-ttu-id="19289-223">이 과정에서 혼합 현실 도구 키트를 통해 Khronos 그룹의 [Unity글 tf 프로젝트](https://github.com/KhronosGroup/UnityGLTF)버전을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-223">This course, via the Mixed Reality Toolkit, uses a version of the Khronos Group's [UnityGLTF project](https://github.com/KhronosGroup/UnityGLTF).</span></span>

<span data-ttu-id="19289-224">컨트롤러가 전달 된 후에는 스크립트에서 **Motioncontrollerinfo** 를 사용 하 여 특정 컨트롤러 요소에 대 한 변환을 찾아 스스로 위치를 올바르게 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-224">Once the controller has been delivered, scripts can use **MotionControllerInfo** to find the transforms for specific controller elements so they can correctly position themselves.</span></span>

<span data-ttu-id="19289-225">이후 장에서는 이러한 스크립트를 사용 하 여 UI 요소를 컨트롤러에 연결 하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="19289-225">In a later chapter, we will learn how to use these scripts to attach UI elements to the controllers.</span></span>

<span data-ttu-id="19289-226">*일부 스크립트에서는 #if 된 코드 블록을 찾을 수 있습니다 **. UNITY_EDITOR** 또는 **UNITY_WSA**. 이러한 코드 블록은 Windows에 배포할 때 UWP 런타임에만 실행 됩니다. Unity 편집기와 UWP 앱 런타임에서 사용 하는 Api 집합이 다르기 때문입니다.*</span><span class="sxs-lookup"><span data-stu-id="19289-226">*In some scripts, you will find code blocks with **#if !UNITY_EDITOR** or **UNITY_WSA**. These code blocks run only on the UWP runtime when you deploy to Windows. This is because the set of APIs used by the Unity editor and the UWP app runtime are different.*</span></span>
* <span data-ttu-id="19289-227">장면을 **저장** 하 고 **재생** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-227">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="19289-228">헤드셋에서 이동 컨트롤러를 사용 하는 장면을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-228">You will be able to see the scene with motion controllers in your headset.</span></span> <span data-ttu-id="19289-229">단추 클릭, 엄지 스틱 움직임 및 터치 패드 touch 강조 표시에 대 한 자세한 애니메이션을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-229">You can see detailed animations for button clicks, thumbstick movement, and touchpad touch highlighting.</span></span>

![MR213_Controller 시각화 기본값](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a><span data-ttu-id="19289-231">2 장-컨트롤러에 UI 요소 연결</span><span class="sxs-lookup"><span data-stu-id="19289-231">Chapter 2 - Attaching UI elements to the controller</span></span>

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a><span data-ttu-id="19289-232">목표</span><span class="sxs-lookup"><span data-stu-id="19289-232">Objectives</span></span>

* <span data-ttu-id="19289-233">동작 컨트롤러의 요소에 대 한 자세한 정보</span><span class="sxs-lookup"><span data-stu-id="19289-233">Learn about the elements of the motion controllers</span></span>
* <span data-ttu-id="19289-234">컨트롤러의 특정 부분에 개체를 연결 하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="19289-234">Learn how to attach objects to specific parts of the controllers</span></span>

<span data-ttu-id="19289-235">이 장에서는 사용자가 언제 든 지 쉽게 액세스 하 고 조작할 수 있는 사용자 인터페이스 요소를 컨트롤러에 추가 하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="19289-235">In this chapter, you will learn how to add user interface elements to the controller which the user can easily access and manipulate at anytime.</span></span> <span data-ttu-id="19289-236">또한 터치 패드 입력을 사용 하 여 간단한 색 선택 UI를 추가 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="19289-236">You will also learn how to add a simple color picker UI using the touchpad input.</span></span>

### <a name="instructions"></a><span data-ttu-id="19289-237">지침</span><span class="sxs-lookup"><span data-stu-id="19289-237">Instructions</span></span>

* <span data-ttu-id="19289-238">**프로젝트** 패널에서 **Motioncontrollerinfo** 스크립트를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-238">In the **Project** panel, search **MotionControllerInfo** script.</span></span>
* <span data-ttu-id="19289-239">검색 결과에서 **Motioncontrollerinfo** 스크립트를 두 번 클릭 하 여 Visual Studio의 코드를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-239">From the search result, double click **MotionControllerInfo** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="19289-240">**MotionControllerInfo 스크립트**</span><span class="sxs-lookup"><span data-stu-id="19289-240">**MotionControllerInfo script**</span></span>

<span data-ttu-id="19289-241">첫 번째 단계는 UI를 연결 하려는 컨트롤러의 요소를 선택 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="19289-241">The first step is to choose which element of the controller you want the UI to attach to.</span></span> <span data-ttu-id="19289-242">이러한 요소는 **MotionControllerInfo.cs**의 **controllerelementenum** 에 정의 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-242">These elements are defined in **ControllerElementEnum** in **MotionControllerInfo.cs**.</span></span>

![MR213 MotionControllerElements](images/mr213-motioncontrollerelements-1000px.jpg)
* <span data-ttu-id="19289-244">**Home**</span><span class="sxs-lookup"><span data-stu-id="19289-244">**Home**</span></span>
* <span data-ttu-id="19289-245">**메뉴**</span><span class="sxs-lookup"><span data-stu-id="19289-245">**Menu**</span></span>
* <span data-ttu-id="19289-246">**잡습니다**</span><span class="sxs-lookup"><span data-stu-id="19289-246">**Grasp**</span></span>
* <span data-ttu-id="19289-247">**사용해**</span><span class="sxs-lookup"><span data-stu-id="19289-247">**Thumbstick**</span></span>
* <span data-ttu-id="19289-248">**Select**</span><span class="sxs-lookup"><span data-stu-id="19289-248">**Select**</span></span>
* <span data-ttu-id="19289-249">**터치패드**</span><span class="sxs-lookup"><span data-stu-id="19289-249">**Touchpad**</span></span>
* <span data-ttu-id="19289-250">**가리키기 포즈** –이 요소는 정방향 방향을 가리키는 컨트롤러의 팁을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="19289-250">**Pointing pose** – this element represents the tip of the controller pointing forward direction.</span></span>

<span data-ttu-id="19289-251">**지침**</span><span class="sxs-lookup"><span data-stu-id="19289-251">**Instructions**</span></span>
* <span data-ttu-id="19289-252">**프로젝트** 패널에서 **AttachToController** 스크립트를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-252">In the **Project** panel, search **AttachToController** script.</span></span>
* <span data-ttu-id="19289-253">검색 결과에서 **AttachToController** 스크립트를 두 번 클릭 하 여 Visual Studio에서 코드를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-253">From the search result, double click **AttachToController** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="19289-254">**AttachToController 스크립트**</span><span class="sxs-lookup"><span data-stu-id="19289-254">**AttachToController script**</span></span>

<span data-ttu-id="19289-255">**AttachToController** 스크립트는 및 요소를 통해 지정 된 컨트롤러에 개체를 연결 하는 간단한 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-255">The **AttachToController** script provides a simple way to attach any objects to a specified controller handedness and element.</span></span>

<span data-ttu-id="19289-256">**AttachElementToController ()** 에서</span><span class="sxs-lookup"><span data-stu-id="19289-256">In **AttachElementToController()**,</span></span>
* <span data-ttu-id="19289-257">**Motioncontrollerinfo를** 사용 하 여 사용 하기</span><span class="sxs-lookup"><span data-stu-id="19289-257">Check handedness using **MotionControllerInfo.Handedness**</span></span>
* <span data-ttu-id="19289-258">**Motioncontrollerinfo. TryGetElement ()를** 사용 하 여 컨트롤러의 특정 요소를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="19289-258">Get specific element of the controller using **MotionControllerInfo.TryGetElement()**</span></span>
* <span data-ttu-id="19289-259">컨트롤러 모델에서 요소의 변환을 검색 한 후 해당 개체의 부모 개체를 부모로 설정 하 고 개체의 로컬 위치를 0으로 & 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-259">After retrieving the element's transform from the controller model, parent the object under it and set object's local position & rotation to zero.</span></span>

```cs
public MotionControllerInfo.ControllerElementEnum Element { get { return element; } }

private void AttachElementToController(MotionControllerInfo newController)
{
     if (!IsAttached && newController.Handedness == handedness)
     {
          if (!newController.TryGetElement(element, out elementTransform))
          {
               Debug.LogError("Unable to find element of type " + element + " under controller " + newController.ControllerParent.name + "; not attaching.");
               return;
          }

          controller = newController;

          SetChildrenActive(true);

          // Parent ourselves under the element and set our offsets
          transform.parent = elementTransform;
          transform.localPosition = positionOffset;
          transform.localEulerAngles = rotationOffset;
          if (setScaleOnAttach)
          {
               transform.localScale = scale;
          }

          // Announce that we're attached
          OnAttachToController();
          IsAttached = true;
     }
}
```

<span data-ttu-id="19289-260">**AttachToController** 스크립트를 사용 하는 가장 간단한 방법은 **Color kerwheel** 의 경우와 마찬가지로이 스크립트에서 상속 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="19289-260">The simplest way to use **AttachToController** script is to inherit from it, as we've done in the case of **ColorPickerWheel.**</span></span> <span data-ttu-id="19289-261">**OnAttachToController** 및 **OnDetatchFromController** 함수를 재정의 하 여 컨트롤러를 검색/연결 해제 하는 경우 설정/분석을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-261">Simply override the **OnAttachToController** and **OnDetatchFromController** functions to perform your setup / breakdown when the controller is detected / disconnected.</span></span>

<span data-ttu-id="19289-262">**지침**</span><span class="sxs-lookup"><span data-stu-id="19289-262">**Instructions**</span></span>
* <span data-ttu-id="19289-263">**프로젝트** 패널에서 검색 상자 **Colorpickerwheel**을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-263">In the **Project** panel, type in the search box **ColorPickerWheel**.</span></span> <span data-ttu-id="19289-264">자산/AppPrefabs/에서 찾을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-264">You can also find it under Assets/AppPrefabs/.</span></span>
* <span data-ttu-id="19289-265">**Colorprefab Kerwheel** 을 **계층** 패널로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="19289-265">Drag **ColorPickerWheel** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="19289-266">**계층** 패널에서 **Colorpickerwheel** prefab를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-266">Click the **ColorPickerWheel** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="19289-267">**검사기** 패널에서 **Colorpickerwheel** 스크립트를 두 번 클릭 하 여 Visual Studio의 코드를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-267">In the **Inspector** panel, double click **ColorPickerWheel** Script to see the code in Visual Studio.</span></span>

![Colorprefab Kerwheel](images/mr213-colorpickerwheel-1000px.jpg)

<span data-ttu-id="19289-269">**Color Kerwheel 스크립트**</span><span class="sxs-lookup"><span data-stu-id="19289-269">**ColorPickerWheel script**</span></span>

<span data-ttu-id="19289-270">**ColorAttachToController Kerwheel** 은 를 상속 하므로 **검사기** 패널에 **손** 및 **요소가** 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19289-270">Since **ColorPickerWheel** inherits **AttachToController**, it shows **Handedness** and **Element** in the **Inspector** panel.</span></span> <span data-ttu-id="19289-271">UI를 왼쪽 컨트롤러의 터치 패드 요소에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-271">We'll be attaching the UI to the Touchpad element on the left controller.</span></span>

![Color Kerwheel 스크립트](images/mr213-attachtocontroller-300px.jpg)

<span data-ttu-id="19289-273">**Colorpickerwheel** 은 **OnAttachToController** 및 **OnDetatchFromController** 를 재정의 하 여 입력 이벤트를 구독 합니다 .이 이벤트는 다음 챕터에서 터치 패드 입력을 사용 하 여 색을 선택 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19289-273">**ColorPickerWheel** overrides the **OnAttachToController** and **OnDetatchFromController** to subscribe to the input event which will be used in next chapter for color selection with touchpad input.</span></span>

```cs
public class ColorPickerWheel : AttachToController, IPointerTarget
{
    protected override void OnAttachToController()
    {
        // Subscribe to input now that we're parented under the controller
        InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
    }

    protected override void OnDetachFromController()
    {
        Visible = false;

        // Unsubscribe from input now that we've detached from the controller
        InteractionManager.InteractionSourceUpdated -= InteractionSourceUpdated;
    }
    ...
}
```
* <span data-ttu-id="19289-274">장면을 **저장** 하 고 **재생** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-274">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="19289-275">**개체를 컨트롤러에 연결 하는 다른 방법**</span><span class="sxs-lookup"><span data-stu-id="19289-275">**Alternative method for attaching objects to the controllers**</span></span>

<span data-ttu-id="19289-276">스크립트는 **AttachToController** 에서 상속 하 고 **OnAttachToController**를 재정의 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-276">We recommend that your scripts inherit from **AttachToController** and override **OnAttachToController**.</span></span> <span data-ttu-id="19289-277">그러나 이것이 항상 가능 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-277">However, this may not always be possible.</span></span> <span data-ttu-id="19289-278">다른 방법으로는 독립 실행형 구성 요소로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-278">An alternative is using it as a standalone component.</span></span> <span data-ttu-id="19289-279">이는 스크립트를 리팩터링 하지 않고 컨트롤러에 기존 prefab를 연결 하려는 경우에 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-279">This can be useful when you want to attach an existing prefab to a controller without refactoring your scripts.</span></span> <span data-ttu-id="19289-280">설치를 수행 하기 전에 클래스에서 IsAttached을 true로 설정할 때까지 대기 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19289-280">Simply have your class wait for IsAttached to be set to true before performing any setup.</span></span> <span data-ttu-id="19289-281">이 작업을 수행 하는 가장 간단한 방법은 ' Start '에 코 루틴를 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="19289-281">The simplest way to do this is by using a coroutine for 'Start.'</span></span>

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a><span data-ttu-id="19289-282">3 장-터치 패드 입력 작업</span><span class="sxs-lookup"><span data-stu-id="19289-282">Chapter 3 - Working with touchpad input</span></span>

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a><span data-ttu-id="19289-283">목표</span><span class="sxs-lookup"><span data-stu-id="19289-283">Objectives</span></span>

* <span data-ttu-id="19289-284">터치 패드 입력 데이터 이벤트를 가져오는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="19289-284">Learn how to get touchpad input data events</span></span>
* <span data-ttu-id="19289-285">앱 환경에 대 한 터치 패드 축 위치 정보를 사용 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="19289-285">Learn how to use touchpad axis position information for your app experience</span></span>

### <a name="instructions"></a><span data-ttu-id="19289-286">지침</span><span class="sxs-lookup"><span data-stu-id="19289-286">Instructions</span></span>

* <span data-ttu-id="19289-287">**계층** 패널에서 **Colorpickerwheel** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-287">In the **Hierarchy** panel, click **ColorPickerWheel**</span></span>
* <span data-ttu-id="19289-288">**검사기** 패널의 **Animatior**아래에서 **ColorPickerWheelController** 을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-288">In the **Inspector** panel, under **Animatior**, double click **ColorPickerWheelController**</span></span>
* <span data-ttu-id="19289-289">**애니메이터** 탭이 열려 있는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-289">You will be able to see **Animator** tab opened</span></span>

<span data-ttu-id="19289-290">**Unity 애니메이션 컨트롤러를 사용 하 여 UI 표시/숨기기**</span><span class="sxs-lookup"><span data-stu-id="19289-290">**Showing/hiding UI with Unity's Animation controller**</span></span>

<span data-ttu-id="19289-291">애니메이션을 사용 하 여 **Colorpickerwheel** UI를 표시 하거나 숨기려면 [Unity의 애니메이션 시스템](https://docs.unity3d.com/Manual/AnimationOverview.html)을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-291">To show and hide the **ColorPickerWheel** UI with animation, we are using [Unity's animation system](https://docs.unity3d.com/Manual/AnimationOverview.html).</span></span> <span data-ttu-id="19289-292">**Colorpickerwheel**의 **Visible** 속성을 true 또는 false 트리거로 설정 하면 애니메이션 트리거가 **표시** 되 고 **숨겨집니다** .</span><span class="sxs-lookup"><span data-stu-id="19289-292">Setting the **ColorPickerWheel**'s **Visible** property to true or false triggers **Show** and **Hide** animation triggers.</span></span> <span data-ttu-id="19289-293">**표시** 및 **숨기기** 매개 변수는 **ColorPickerWheelController** 애니메이션 컨트롤러에서 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19289-293">**Show** and **Hide** parameters are defined in the **ColorPickerWheelController** animation controller.</span></span>

![Unity 애니메이션 컨트롤러](images/mr123-animationcontroller-550px.jpg)

<span data-ttu-id="19289-295">**지침**</span><span class="sxs-lookup"><span data-stu-id="19289-295">**Instructions**</span></span>
* <span data-ttu-id="19289-296">**계층** 패널에서 **Colorpickerwheel** prefab를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-296">In the **Hierarchy** panel, select **ColorPickerWheel** prefab</span></span>
* <span data-ttu-id="19289-297">**검사기** 패널에서 **Colorpickerwheel** 스크립트를 두 번 클릭 하 여 Visual Studio에서 코드를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-297">In the **Inspector** panel, double click **ColorPickerWheel** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="19289-298">**Color Kerwheel 스크립트**</span><span class="sxs-lookup"><span data-stu-id="19289-298">**ColorPickerWheel script**</span></span>

<span data-ttu-id="19289-299">**Color Kerwheel** 은 Unity 이벤트를 수신 하는 Unity의 **InteractionSourceUpdated** 이벤트를 구독 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-299">**ColorPickerWheel** subscribes to Unity's **InteractionSourceUpdated** event to listen for touchpad events.</span></span>

<span data-ttu-id="19289-300">**InteractionSourceUpdated ()** 에서 스크립트는 먼저 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-300">In **InteractionSourceUpdated()**, the script first checks to ensure that it:</span></span>
* <span data-ttu-id="19289-301">는 실제로 터치 패드 이벤트 (.obj. 상태)입니다. **touchpadTouched**)</span><span class="sxs-lookup"><span data-stu-id="19289-301">is actually a touchpad event (obj.state.**touchpadTouched**)</span></span>
* <span data-ttu-id="19289-302">왼쪽 컨트롤러에서 생성 됩니다 **(obj. source. 손**)</span><span class="sxs-lookup"><span data-stu-id="19289-302">originates from the left controller (obj.state.source.**handedness**)</span></span>

<span data-ttu-id="19289-303">둘 다 true 이면 터치 패드 위치 (obj. 상태)입니다. **touchpadPosition**)가 **selectorPosition**에 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19289-303">If both are true, the touchpad position (obj.state.**touchpadPosition**) is assigned to **selectorPosition**.</span></span>

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness && obj.state.touchpadTouched)
    {
        Visible = true;
        selectorPosition = obj.state.touchpadPosition;
    }
}
```

<span data-ttu-id="19289-304">**표시 되** 는 속성을 기반으로 하는 **Update ()** 에서 색 선택의 애니메이터 구성 요소에 표시 및 숨기기 애니메이션 트리거를 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-304">In **Update()**, based on **visible** property, it triggers Show and Hide animation triggers in the color picker's animator component</span></span>

```cs
if (visible != visibleLastFrame)
{
    if (visible)
    {
        animator.SetTrigger("Show");
    }
    else
    {
        animator.SetTrigger("Hide");
    }
}
```

<span data-ttu-id="19289-305">**Update ()** 에서 **selectorPosition** 는 UV 위치를 반환 하는 색 휠의 메시 collider에서 광선을 캐스팅 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19289-305">In **Update()**, **selectorPosition** is used to cast a ray at the color wheel's mesh collider, which returns a UV position.</span></span> <span data-ttu-id="19289-306">그런 다음이 위치를 사용 하 여 색 휠의 질감의 픽셀 좌표 및 색 값을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-306">This position can then be used to find the pixel coordinate and color value of the color wheel's texture.</span></span> <span data-ttu-id="19289-307">이 값은 **Selectedcolor** 속성을 통해 다른 스크립트에서 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-307">This value is accessible to other scripts via the **SelectedColor** property.</span></span>

![색 선택 휠 Raycasting](images/mr213-colorpickerwheel-raycast-700px.png)

```cs
...
    // Clamp selector position to a radius of 1
    Vector3 localPosition = new Vector3(selectorPosition.x * inputScale, 0.15f, selectorPosition.y * inputScale);
    if (localPosition.magnitude > 1)
    {
        localPosition = localPosition.normalized;
    }
    selectorTransform.localPosition = localPosition;

    // Raycast the wheel mesh and get its UV coordinates
    Vector3 raycastStart = selectorTransform.position + selectorTransform.up * 0.15f;
    RaycastHit hit;
    Debug.DrawLine(raycastStart, raycastStart - (selectorTransform.up * 0.25f));

    if (Physics.Raycast(raycastStart, -selectorTransform.up, out hit, 0.25f, 1 << colorWheelObject.layer, QueryTriggerInteraction.Ignore))
    {
        // Get pixel from the color wheel texture using UV coordinates
        Vector2 uv = hit.textureCoord;
        int pixelX = Mathf.FloorToInt(colorWheelTexture.width * uv.x);
        int pixelY = Mathf.FloorToInt(colorWheelTexture.height * uv.y);
        selectedColor = colorWheelTexture.GetPixel(pixelX, pixelY);
        selectedColor.a = 1f;
    }
    // Set the selector's color and blend it with white to make it visible on top of the wheel
    selectorRenderer.material.color = Color.Lerp (selectedColor, Color.white, 0.5f);
}
```

## <a name="chapter-4---overriding-controller-model"></a><span data-ttu-id="19289-309">4 장-컨트롤러 모델 재정의</span><span class="sxs-lookup"><span data-stu-id="19289-309">Chapter 4 - Overriding controller model</span></span>

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a><span data-ttu-id="19289-310">목표</span><span class="sxs-lookup"><span data-stu-id="19289-310">Objectives</span></span>

* <span data-ttu-id="19289-311">사용자 지정 3D 모델을 사용 하 여 컨트롤러 모델을 재정의 하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="19289-311">Learn how to override the controller model with a custom 3D model.</span></span>

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a><span data-ttu-id="19289-313">지침</span><span class="sxs-lookup"><span data-stu-id="19289-313">Instructions</span></span>

* <span data-ttu-id="19289-314">**계층** 패널에서 **motioncontrollers** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-314">Click **MotionControllers** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="19289-315">**오른쪽의 대체 컨트롤러** 필드 오른쪽에 있는 원을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-315">Click the circle on the right side of the **Alternate Right Controller** field.</span></span>
* <span data-ttu-id="19289-316">**' BrushController**'을 입력 하 고 결과에서 prefab를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-316">Type in **'BrushController**' and select the prefab from the result.</span></span> <span data-ttu-id="19289-317">자산/AppPrefabs/**BrushController**에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-317">You can find it under Assets/AppPrefabs/**BrushController**.</span></span>
* <span data-ttu-id="19289-318">**항상 대체 권한 모델 사용** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-318">Check **Always Use Alternate Right Model**</span></span>

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

<span data-ttu-id="19289-320">**BrushController** Prefab는 **계층** 패널에 포함할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-320">The **BrushController** prefab does not have to be included in the **Hierarchy** panel.</span></span> <span data-ttu-id="19289-321">그러나 자식 구성 요소를 체크 아웃 하려면:</span><span class="sxs-lookup"><span data-stu-id="19289-321">However, to check out its child components:</span></span>
* <span data-ttu-id="19289-322">**프로젝트** 패널에서 **BrushController** 를 입력 하 고 **BrushController** prefab를 **계층** 패널로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="19289-322">In the **Project** panel, type in **BrushController** and drag **BrushController** prefab into the **Hierarchy** panel.</span></span>

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

<span data-ttu-id="19289-324">**팁** 구성 요소는 **BrushController**에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-324">You will find the **Tip** component in **BrushController**.</span></span> <span data-ttu-id="19289-325">이를 사용 하 여 줄 그리기를 시작/중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-325">We will use its transform to start/stop drawing lines.</span></span>
* <span data-ttu-id="19289-326">**계층** 패널에서 **BrushController** 를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-326">Delete the **BrushController** from the **Hierarchy** panel.</span></span>
* <span data-ttu-id="19289-327">장면을 **저장** 하 고 **재생** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-327">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="19289-328">오른쪽 동작 컨트롤러를 교체 하는 브러시 모델을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-328">You will be able to see the brush model replaced the right-hand motion controller.</span></span>

## <a name="chapter-5---painting-with-select-input"></a><span data-ttu-id="19289-329">5 장-선택 입력으로 그리기</span><span class="sxs-lookup"><span data-stu-id="19289-329">Chapter 5 - Painting with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a><span data-ttu-id="19289-330">목표</span><span class="sxs-lookup"><span data-stu-id="19289-330">Objectives</span></span>

* <span data-ttu-id="19289-331">선택 단추 이벤트를 사용 하 여 선 그리기를 시작 및 중지 하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="19289-331">Learn how to use the Select button event to start and stop a line drawing</span></span>

### <a name="instructions"></a><span data-ttu-id="19289-332">지침</span><span class="sxs-lookup"><span data-stu-id="19289-332">Instructions</span></span>

* <span data-ttu-id="19289-333">**프로젝트** 패널에서 **BrushController** prefab를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-333">Search **BrushController** prefab in the **Project** panel.</span></span>
* <span data-ttu-id="19289-334">**검사기** 패널에서 **BrushController** 스크립트를 두 번 클릭 하 여 Visual Studio에서 코드를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-334">In the **Inspector** panel, double click **BrushController** Script to see the code in Visual Studio</span></span>

<span data-ttu-id="19289-335">**BrushController 스크립트**</span><span class="sxs-lookup"><span data-stu-id="19289-335">**BrushController script**</span></span>

<span data-ttu-id="19289-336">**BrushController** 는 InteractionManager의 **InteractionSourcePressed** 및 **InteractionSourceReleased** 이벤트를 구독 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-336">**BrushController** subscribes to the InteractionManager's **InteractionSourcePressed** and **InteractionSourceReleased** events.</span></span> <span data-ttu-id="19289-337">**InteractionSourcePressed** 이벤트가 트리거되면 브러시의 **그리기** 속성이 true로 설정 됩니다. **InteractionSourceReleased** 이벤트가 트리거되면 브러시의 **그리기** 속성이 false로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19289-337">When **InteractionSourcePressed** event is triggered, the brush's **Draw** property is set to true; when **InteractionSourceReleased** event is triggered, the brush's **Draw** property is set to false.</span></span>

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = true;
    }
}

private void InteractionSourceReleased(InteractionSourceReleasedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = false;
    }
}
```

<span data-ttu-id="19289-338">**Draw** 를 true로 설정 하는 동안 브러시는 인스턴스화된 Unity **LineRenderer**의 요소를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-338">While **Draw** is set to true, the brush will generate points in an instantiated Unity **LineRenderer**.</span></span> <span data-ttu-id="19289-339">이 prefab에 대 한 참조는 브러시의 **Stroke prefab** 필드에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19289-339">A reference to this prefab is kept in the brush's **Stroke Prefab** field.</span></span>

```cs
private IEnumerator DrawOverTime()
{
    // Get the position of the tip
    Vector3 lastPointPosition = tip.position;

    ...

    // Create a new brush stroke
    GameObject newStroke = Instantiate(strokePrefab);
    LineRenderer line = newStroke.GetComponent<LineRenderer>();
    newStroke.transform.position = startPosition;
    line.SetPosition(0, tip.position);
    float initialWidth = line.widthMultiplier;

    // Generate points in an instantiated Unity LineRenderer
    while (draw)
    {
        // Move the last point to the draw point position
        line.SetPosition(line.positionCount - 1, tip.position);
        line.material.color = colorPicker.SelectedColor;
        brushRenderer.material.color = colorPicker.SelectedColor;
        lastPointAddedTime = Time.unscaledTime;
        // Adjust the width between 1x and 2x width based on strength of trigger pull
        line.widthMultiplier = Mathf.Lerp(initialWidth, initialWidth * 2, width);

        if (Vector3.Distance(lastPointPosition, tip.position) > minPositionDelta || Time.unscaledTime > lastPointAddedTime + maxTimeDelta)
        {
            // Spawn a new point
            lastPointAddedTime = Time.unscaledTime;
            lastPointPosition = tip.position;
            line.positionCount += 1;
            line.SetPosition(line.positionCount - 1, lastPointPosition);
        }
        yield return null;
    }
}
```

<span data-ttu-id="19289-340">색 선택 휠 UI에서 현재 선택 된 색을 사용 하려면 **BrushController** 에 **Colorpickerwheel** 개체에 대 한 참조가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-340">To use the currently selected color from the color picker wheel UI, **BrushController** needs to have a reference to the **ColorPickerWheel** object.</span></span> <span data-ttu-id="19289-341">**BrushController** prefab는 런타임에 대체 컨트롤러로 인스턴스화되기 때문에 장면의 개체에 대 한 모든 참조는 런타임에 설정 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-341">Because the **BrushController** prefab is instantiated at runtime as a replacement controller, any references to objects in the scene will have to be set at runtime.</span></span> <span data-ttu-id="19289-342">이 경우 **GameObject** 를 사용 하 여 colorFindObjectOfType를 찾습니다 .</span><span class="sxs-lookup"><span data-stu-id="19289-342">In this case we use **GameObject.FindObjectOfType** to locate the **ColorPickerWheel**:</span></span>

```cs
private void OnEnable()
{
    // Locate the ColorPickerWheel
    colorPicker = FindObjectOfType<ColorPickerWheel>();

    // Assign currently selected color to the brush’s material color
    brushRenderer.material.color = colorPicker.SelectedColor;
    ...
}
```
* <span data-ttu-id="19289-343">장면을 **저장** 하 고 **재생** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-343">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="19289-344">오른쪽 컨트롤러의 선택 단추를 사용 하 여 선을 그리고 그릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-344">You will be able to draw the lines and paint using the select button on the right-hand controller.</span></span>

## <a name="chapter-6---object-spawning-with-select-input"></a><span data-ttu-id="19289-345">6 장-선택 입력으로 개체 생성</span><span class="sxs-lookup"><span data-stu-id="19289-345">Chapter 6 - Object spawning with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a><span data-ttu-id="19289-346">목표</span><span class="sxs-lookup"><span data-stu-id="19289-346">Objectives</span></span>

* <span data-ttu-id="19289-347">선택 및 이해 단추 입력 이벤트를 사용 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="19289-347">Learn how to use Select and Grasp button input events</span></span>
* <span data-ttu-id="19289-348">개체를 인스턴스화하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="19289-348">Learn how to instantiate objects</span></span>

### <a name="instructions"></a><span data-ttu-id="19289-349">지침</span><span class="sxs-lookup"><span data-stu-id="19289-349">Instructions</span></span>

* <span data-ttu-id="19289-350">**프로젝트** 패널의 검색 상자에 **ObjectSpawner** 를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-350">In the **Project** panel, type **ObjectSpawner** in the search box.</span></span> <span data-ttu-id="19289-351">자산/AppPrefabs/에서 찾을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-351">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="19289-352">**ObjectSpawner** Prefab를 **계층** 패널로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="19289-352">Drag the **ObjectSpawner** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="19289-353">**계층** 패널에서 **ObjectSpawner** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-353">Click **ObjectSpawner** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="19289-354">**ObjectSpawner** 에는 **Color Source**라는 필드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-354">**ObjectSpawner** has a field named **Color Source**.</span></span>
* <span data-ttu-id="19289-355">**계층** 패널에서 **Colorpickerwheel** 참조를이 필드로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="19289-355">From the **Hierarchy** panel, drag the **ColorPickerWheel** reference into this field.</span></span>

![개체 Spawner Inspector](images/mr213-objectspawnercolorpickerwheel-650px.jpg)
* <span data-ttu-id="19289-357">**계층** 패널에서 **ObjectSpawner** prefab을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-357">Click the **ObjectSpawner** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="19289-358">**검사기** 패널에서 **ObjectSpawner** 스크립트를 두 번 클릭 하 여 Visual Studio에서 코드를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-358">In the **Inspector** panel, double click **ObjectSpawner** Script to see the code in Visual Studio.</span></span>

<span data-ttu-id="19289-359">**ObjectSpawner 스크립트**</span><span class="sxs-lookup"><span data-stu-id="19289-359">**ObjectSpawner script**</span></span>

<span data-ttu-id="19289-360">**ObjectSpawner** 는 기본 메시 (cube, 구, 실린더)의 복사본을 공간으로 인스턴스화합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-360">The **ObjectSpawner** instantiates copies of a primitive mesh (cube, sphere, cylinder) into the space.</span></span> <span data-ttu-id="19289-361">**InteractionSourcePressed** 감지 되 면이를 확인 하 고 **InteractionSourcePressType** 또는 **InteractionSourcePressType** 이벤트 인지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-361">When a **InteractionSourcePressed** is detected it checks the handedness and if it's an **InteractionSourcePressType.Grasp** or **InteractionSourcePressType.Select** event.</span></span>

<span data-ttu-id="19289-362">이 이벤트 **의** 경우 현재 메시 유형 (구, 큐브, 실린더)의 인덱스를 증가 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="19289-362">For a **Grasp** event, it increments the index of current mesh type (sphere, cube, cylinder)</span></span>

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    // Check handedness, see if it is left controller
    if (obj.state.source.handedness == handedness)
    {
        switch (obj.pressType)
        {
            // If it is Select button event, spawn object
            case InteractionSourcePressType.Select:
                if (state == StateEnum.Idle)
                {
                    // We've pressed the grasp - enter spawning state
                    state = StateEnum.Spawning;
                    SpawnObject();
                }
                break;

            // If it is Grasp button event
            case InteractionSourcePressType.Grasp:

                // Increment the index of current mesh type (sphere, cube, cylinder)
                meshIndex++;
                if (meshIndex >= NumAvailableMeshes)
                {
                    meshIndex = 0;
                }
                break;

            default:
                break;
        }
    }
}
```

<span data-ttu-id="19289-363">**Select** 이벤트의 경우 **SpawnObject ()** 에서 새 개체가 인스턴스화되어, 부모로 해제 되 고, 전 세계에 릴리스됩니다.</span><span class="sxs-lookup"><span data-stu-id="19289-363">For a **Select** event, in **SpawnObject()**, a new object is instantiated, un-parented and released into the world.</span></span>

```cs
private void SpawnObject()
{
    // Instantiate the spawned object
    GameObject newObject = Instantiate(displayObject.gameObject, spawnParent);
    // Detatch the newly spawned object
    newObject.transform.parent = null;
    // Reset the scale transform to 1
    scaleParent.localScale = Vector3.one;
    // Set its material color so its material gets instantiated
    newObject.GetComponent<Renderer>().material.color = colorSource.SelectedColor;
}
```

<span data-ttu-id="19289-364">**ObjectSpawner** 는 Color **kerwheel** 을 사용 하 여 표시 개체의 재질 색을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-364">The **ObjectSpawner** uses the **ColorPickerWheel** to set the color of the display object's material.</span></span> <span data-ttu-id="19289-365">생성 된 개체에는이 자료의 인스턴스가 제공 되므로 색을 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-365">Spawned objects are given an instance of this material so they will retain their color.</span></span>
* <span data-ttu-id="19289-366">장면을 **저장** 하 고 **재생** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-366">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="19289-367">[클릭] 단추를 사용 하 여 개체를 변경 하 고 [선택] 단추를 사용 하 여 개체를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-367">You will be able to change the objects with the Grasp button and spawn objects with the Select button.</span></span>

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a><span data-ttu-id="19289-368">혼합 현실 포털에 앱 빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="19289-368">Build and deploy app to Mixed Reality Portal</span></span>
* <span data-ttu-id="19289-369">Unity에서 **파일 > 빌드 설정**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-369">In Unity, select **File > Build Settings**.</span></span>
* <span data-ttu-id="19289-370">열려 있는 장면 **추가** 를 클릭 하 여 현재 장면을 **빌드 장면**에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-370">Click **Add Open Scenes** to add current scene to the **Scenes In Build**.</span></span>
* <span data-ttu-id="19289-371">**빌드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-371">Click **Build**.</span></span>
* <span data-ttu-id="19289-372">"App" 이라는 **새 폴더** 를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="19289-372">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="19289-373">단일 **앱** 폴더를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-373">Single click the **App** folder.</span></span>
* <span data-ttu-id="19289-374">**폴더 선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-374">Click **Select Folder**.</span></span>
* <span data-ttu-id="19289-375">Unity가 완료 되 면 파일 탐색기 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19289-375">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="19289-376">**앱** 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="19289-376">Open the **App** folder.</span></span>
* <span data-ttu-id="19289-377">**YourSceneName** Visual Studio 솔루션 파일을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-377">Double click **YourSceneName.sln** Visual Studio Solution file.</span></span>
* <span data-ttu-id="19289-378">Visual Studio의 맨 위 도구 모음을 사용 하 여 대상을 디버그에서 **릴리스** 로, ARM에서 x **64**로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-378">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X64**.</span></span>
* <span data-ttu-id="19289-379">장치 단추 옆에 있는 드롭다운 화살표를 클릭 하 고 **로컬 컴퓨터**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-379">Click on the drop-down arrow next to the Device button, and select **Local Machine**.</span></span>
* <span data-ttu-id="19289-380">메뉴에서 **디버그 >-디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="19289-380">Click **Debug -> Start Without debugging** in the menu or press **Ctrl + F5**.</span></span>

<span data-ttu-id="19289-381">이제 앱이 혼합 현실 포털에 빌드되고 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19289-381">Now the app is built and installed in Mixed Reality Portal.</span></span> <span data-ttu-id="19289-382">혼합 현실 포털의 시작 메뉴를 통해 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-382">You can launch it again through Start menu in Mixed Reality Portal.</span></span>

## <a name="advanced-design---brush-tools-with-radial-layout"></a><span data-ttu-id="19289-383">방사형 레이아웃을 사용 하는 고급 디자인-브러시 도구</span><span class="sxs-lookup"><span data-stu-id="19289-383">Advanced design - Brush tools with radial layout</span></span>

![MixedReality213 주](images/mr213-main-600px.jpg)

<span data-ttu-id="19289-385">이 장에서는 기본 동작 컨트롤러 모델을 사용자 지정 브러시 도구 컬렉션으로 바꾸는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="19289-385">In this chapter, you will learn how to replace the default motion controller model with a custom brush tool collection.</span></span> <span data-ttu-id="19289-386">참조를 위해, **장면 폴더 아래** 에서 완료 된 장면 **MixedReality213Advanced** 를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-386">For your reference, you can find the completed scene **MixedReality213Advanced** under **Scenes** folder.</span></span>

### <a name="instructions"></a><span data-ttu-id="19289-387">지침</span><span class="sxs-lookup"><span data-stu-id="19289-387">Instructions</span></span>

* <span data-ttu-id="19289-388">**프로젝트** 패널의 검색 상자에 **BrushSelector** 를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-388">In the **Project** panel, type **BrushSelector** in the search box .</span></span> <span data-ttu-id="19289-389">자산/AppPrefabs/에서 찾을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-389">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="19289-390">**BrushSelector** Prefab를 **계층** 패널로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="19289-390">Drag the **BrushSelector** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="19289-391">조직의 경우 **브러시** 라는 빈 GameObject를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="19289-391">For organization, create an empty GameObject called **Brushes**</span></span>
* <span data-ttu-id="19289-392">**프로젝트** 패널에서 다음 Prefabs을 **브러시로** 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="19289-392">Drag following prefabs from the **Project** panel into **Brushes**</span></span>
    * <span data-ttu-id="19289-393">자산/AppPrefabs/**BrushFat**</span><span class="sxs-lookup"><span data-stu-id="19289-393">Assets/AppPrefabs/**BrushFat**</span></span>
    * <span data-ttu-id="19289-394">자산/AppPrefabs/**BrushThin**</span><span class="sxs-lookup"><span data-stu-id="19289-394">Assets/AppPrefabs/**BrushThin**</span></span>
    * <span data-ttu-id="19289-395">자산/AppPrefabs/**지우개**</span><span class="sxs-lookup"><span data-stu-id="19289-395">Assets/AppPrefabs/**Eraser**</span></span>
    * <span data-ttu-id="19289-396">자산/AppPrefabs/**Markerfat**</span><span class="sxs-lookup"><span data-stu-id="19289-396">Assets/AppPrefabs/**MarkerFat**</span></span>
    * <span data-ttu-id="19289-397">자산/AppPrefabs/**Markerthin**</span><span class="sxs-lookup"><span data-stu-id="19289-397">Assets/AppPrefabs/**MarkerThin**</span></span>
    * <span data-ttu-id="19289-398">자산/AppPrefabs/**연필**</span><span class="sxs-lookup"><span data-stu-id="19289-398">Assets/AppPrefabs/**Pencil**</span></span>

![브러시](images/mixedreality213-brushes-250px.png)
* <span data-ttu-id="19289-400">**계층** 패널에서 **motioncontrollers** prefab를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-400">Click **MotionControllers** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="19289-401">**검사기** 패널에서 항상 **동작 컨트롤러 시각화 도우미** 의 **대체 오른쪽 모델 사용** 확인란을 선택 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-401">In the **Inspector** panel, uncheck **Always Use Alternate Right Model** on the **Motion Controller Visualizer**</span></span>
* <span data-ttu-id="19289-402">**계층** 패널에서 **BrushSelector** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-402">In the **Hierarchy** panel, click **BrushSelector**</span></span>
* <span data-ttu-id="19289-403">**BrushSelector** 에 **colorpicker** 라는 필드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-403">**BrushSelector** has a field named **ColorPicker**</span></span>
* <span data-ttu-id="19289-404">**계층** 패널에서 **Colorpickerwheel** 을 **Inspector** 패널의 **colorpicker** 필드로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="19289-404">From the **Hierarchy** panel, drag the **ColorPickerWheel** into **ColorPicker** field in the **Inspector** panel.</span></span>

![브러시 선택기에 ColorPickerWheel 할당](images/mr213-brushselector-500px.jpg)
* <span data-ttu-id="19289-406">**계층** 패널의 **BrushSelector** prefab에서 **메뉴** 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-406">In the **Hierarchy** panel, under **BrushSelector** prefab, select the **Menu** object.</span></span>
* <span data-ttu-id="19289-407">**검사기** 패널의 **lineobjectcollection** 구성 요소 아래에서 **개체** 배열 드롭다운을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="19289-407">In the **Inspector** panel, under the **LineObjectCollection** component, open the **Objects** array dropdown.</span></span> <span data-ttu-id="19289-408">빈 슬롯이 6 개 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19289-408">You will see 6 empty slots.</span></span>
* <span data-ttu-id="19289-409">**계층** 패널에서 **브러시** GameObject의 각 prefabs 부모를 각각 순서 대로 이러한 슬롯으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="19289-409">From the **Hierarchy** panel, drag each of the prefabs parented under the **Brushes** GameObject into these slots in any order.</span></span> <span data-ttu-id="19289-410">(프로젝트 폴더의 prefabs가 아니라 장면에서 prefabs을 끌지 확인 하세요.)</span><span class="sxs-lookup"><span data-stu-id="19289-410">(Make sure you're dragging the prefabs from the scene, not the prefabs in the project folder.)</span></span>

![브러시 선택기](images/mr213-brushselectorbrushes-700px.jpg)

<span data-ttu-id="19289-412">**BrushSelector prefab**</span><span class="sxs-lookup"><span data-stu-id="19289-412">**BrushSelector prefab**</span></span>

<span data-ttu-id="19289-413">**BrushSelector** 는 **AttachToController**를 상속 하므로 **검사기** 패널 **에서** 및 **요소** 옵션을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-413">Since the **BrushSelector** inherits **AttachToController**, it shows **Handedness** and **Element** options in the **Inspector** panel.</span></span> <span data-ttu-id="19289-414">**오른쪽** 및 **포인팅 포즈** 를 선택 하 여 정방향 컨트롤러에 브러시 도구를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-414">We selected **Right** and **Pointing Pose** to attach brush tools to the right hand controller with forward direction.</span></span>

<span data-ttu-id="19289-415">**BrushSelector** 는 다음과 같은 두 가지 유틸리티를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-415">The **BrushSelector** makes use of two utilities:</span></span>
* <span data-ttu-id="19289-416">**Ellipse**: 타원 셰이프를 따라 공간에 요소를 생성 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19289-416">**Ellipse**: used to generate points in space along an ellipse shape.</span></span>
* <span data-ttu-id="19289-417">**Lineobjectcollection**: 모든 줄 클래스 (예: 타원)에서 생성 된 요소를 사용 하 여 개체를 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-417">**LineObjectCollection**: distributes objects using the points generated by any Line class (eg, Ellipse).</span></span> <span data-ttu-id="19289-418">타원 셰이프를 따라 브러시를 배치 하는 데 사용할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="19289-418">This is what we'll be using to place our brushes along the Ellipse shape.</span></span>

<span data-ttu-id="19289-419">결합 하면 이러한 유틸리티를 사용 하 여 방사형 메뉴를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-419">When combined, these utilities can be used to create a radial menu.</span></span>

<span data-ttu-id="19289-420">**LineObjectCollection 스크립트**</span><span class="sxs-lookup"><span data-stu-id="19289-420">**LineObjectCollection script**</span></span>

<span data-ttu-id="19289-421">**Lineobjectcollection** 에는 줄을 따라 분산 된 개체의 크기, 위치 및 회전에 대 한 컨트롤이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-421">**LineObjectCollection** has controls for the size, position and rotation of objects distributed along its line.</span></span> <span data-ttu-id="19289-422">이는 브러시 선택기와 같은 방사형 메뉴를 만드는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-422">This is useful for creating radial menus like the brush selector.</span></span> <span data-ttu-id="19289-423">가운데 선택 된 위치에 따라 아무것도 확장 되지 않는 브러시의 모양을 만들려면 **objectscale** 곡선이 가운데에서 증가 하 고 가장자리에서 tapers 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-423">To create the appearance of brushes that scale up from nothing as they approach the center selected position, the **ObjectScale** curve peaks in the center and tapers off at the edges.</span></span>

<span data-ttu-id="19289-424">**BrushSelector 스크립트**</span><span class="sxs-lookup"><span data-stu-id="19289-424">**BrushSelector script**</span></span>

<span data-ttu-id="19289-425">**BrushSelector**의 경우 절차적 애니메이션을 사용 하도록 선택 했습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-425">In the case of the **BrushSelector**, we've chosen to use procedural animation.</span></span> <span data-ttu-id="19289-426">먼저, 브러시 모델은 **Lineobjectcollection** 스크립트에 의해 타원에 배포 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19289-426">First, brush models are distributed in an ellipse by the **LineObjectCollection** script.</span></span> <span data-ttu-id="19289-427">그런 다음, 각 브러시는 선택 항목에 따라 변경 되는 **DisplayMode** 값을 기반으로 사용자 손으로 위치를 유지 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-427">Then, each brush is responsible for maintaining its position in the user's hand based on its **DisplayMode** value, which changes based on the selection.</span></span> <span data-ttu-id="19289-428">사용자가 브러시를 선택할 때 브러시 위치 전환이 중단 될 확률이 높다는 것으로 인해 절차적 접근 방식을 선택 했습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-428">We chose a procedural approach because of the high probability of brush position transitions being interrupted as the user selects brushes.</span></span> <span data-ttu-id="19289-429">Mecanim 애니메이션은 중단을 정상적으로 처리할 수 있지만 간단한 Lerp 작업 보다 복잡 한 경향이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-429">Mecanim animations can handle interruptions gracefully, but it tends to be more complicated than a simple Lerp operation.</span></span>

<span data-ttu-id="19289-430">**BrushSelector** 는 두 가지 조합을 모두 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-430">**BrushSelector** uses a combination of both.</span></span> <span data-ttu-id="19289-431">터치 패드 입력이 검색 되 면 브러시 옵션이 표시 되 고 방사형 메뉴를 따라 확장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19289-431">When touchpad input is detected, brush options become visible and scale up along the radial menu.</span></span> <span data-ttu-id="19289-432">제한 시간 (사용자가 선택 했음을 나타냄) 후에 브러시 옵션이 다시 축소 되어 선택한 브러시만 남게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19289-432">After a timeout period (which indicates that the user has made a selection) the brush options scale down again, leaving only the selected brush.</span></span>

<span data-ttu-id="19289-433">**터치 패드 입력 시각화**</span><span class="sxs-lookup"><span data-stu-id="19289-433">**Visualizing touchpad input**</span></span>

<span data-ttu-id="19289-434">컨트롤러 모델이 완전히 바뀐 경우에도 원래 모델 입력에 대 한 입력을 표시 하는 것이 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-434">Even in cases where the controller model has been completely replaced, it can be helpful to show input on the original model inputs.</span></span> <span data-ttu-id="19289-435">이를 통해 실제로 사용자의 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-435">This helps to ground the user's actions in reality.</span></span> <span data-ttu-id="19289-436">**BrushSelector** 의 경우 입력을 받을 때 터치 패드가 잠깐 표시 되도록 선택 했습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-436">For the **BrushSelector** we've chosen to make the touchpad briefly visible when the input is received.</span></span> <span data-ttu-id="19289-437">이렇게 하려면 컨트롤러에서 터치 패드 요소를 검색 하 고 해당 재질을 사용자 지정 재질로 바꾼 다음, 터치 패드 입력을 마지막으로 받은 시간을 기준으로 해당 재질의 색에 그라데이션을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-437">This was done by retrieving the Touchpad element from the controller, replacing its material with a custom material, then applying a gradient to that material's color based on the last time touchpad input was received.</span></span>

```cs
protected override void OnAttachToController()
{
    // Turn off the default controller's renderers
    controller.SetRenderersVisible(false);

    // Get the touchpad and assign our custom material to it
    Transform touchpad;
    if (controller.TryGetElement(MotionControllerInfo.ControllerElementEnum.Touchpad, out touchpad))
    {
        touchpadRenderer = touchpad.GetComponentInChildren<MeshRenderer>();
        originalTouchpadMaterial = touchpadRenderer.material;
        touchpadRenderer.material = touchpadMaterial;
        touchpadRenderer.enabled = true;
    }
            
    // Subscribe to input now that we're parented under the controller
    InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
}

private void Update()
{
    ...
    // Update our touchpad material
    Color glowColor = touchpadColor.Evaluate((Time.unscaledTime - touchpadTouchTime) / touchpadGlowLossTime);
    touchpadMaterial.SetColor("_EmissionColor", glowColor);
    touchpadMaterial.SetColor("_Color", glowColor);
    ...
}
```

<span data-ttu-id="19289-438">**터치 패드가 입력 된 브러시 도구 선택**</span><span class="sxs-lookup"><span data-stu-id="19289-438">**Brush tool selection with touchpad input**</span></span>

<span data-ttu-id="19289-439">브러시 선택기에서 터치 패드의 누른 입력을 검색 하면 입력의 위치를 확인 하 여 왼쪽 또는 오른쪽에 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-439">When the brush selector detects touchpad's pressed input, it checks the position of the input to determine if it was to the left or right.</span></span>

<span data-ttu-id="19289-440">**Select보도 Sedamount를 사용 하 여 두께 스트로크**</span><span class="sxs-lookup"><span data-stu-id="19289-440">**Stroke thickness with selectPressedAmount**</span></span>

<span data-ttu-id="19289-441">**InteractionSourcePressed ()** 에서 **InteractionSourcePressType** 이벤트 대신 **select보도 sedamount**를 통해 눌린 금액의 아날로그 값을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-441">Instead of the **InteractionSourcePressType.Select** event in the **InteractionSourcePressed()**, you can get the analog value of the pressed amount through **selectPressedAmount**.</span></span> <span data-ttu-id="19289-442">이 값은 **InteractionSourceUpdated ()** 에서 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-442">This value can be retrieved in **InteractionSourceUpdated()**.</span></span>

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness)
    {
        if (obj.state.touchpadPressed)
        {
            // Check which side we clicked
            if (obj.state.touchpadPosition.x < 0)
            {
                currentAction = SwipeEnum.Left;
            }
            else
            {
                currentAction = SwipeEnum.Right;
            }

            // Ping the touchpad material so it gets bright
            touchpadTouchTime = Time.unscaledTime;
        }

        if (activeBrush != null)
        {
            // If the pressed amount is greater than our threshold, draw
            if (obj.state.selectPressedAmount >= selectPressedDrawThreshold)
            {
                activeBrush.Draw = true;
                activeBrush.Width = ProcessSelectPressedAmount(obj.state.selectPressedAmount);
            }
            else
            {
                // Otherwise, stop drawing
                activeBrush.Draw = false;
                selectPressedSmooth = 0f;
            }
        }
    }
}
```

<span data-ttu-id="19289-443">**지우개 스크립트**</span><span class="sxs-lookup"><span data-stu-id="19289-443">**Eraser script**</span></span>

<span data-ttu-id="19289-444">**지우개** 는 기본 **브러시**의 **drawovertime ()** 함수를 재정의 하는 특수 한 유형의 브러시입니다.</span><span class="sxs-lookup"><span data-stu-id="19289-444">**Eraser** is a special type of brush that overrides the base **Brush**'s **DrawOverTime()** function.</span></span> <span data-ttu-id="19289-445">그리기가 true 인 동안 지우개는 해당 팁이 기존 브러시 스트로크와 교차 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-445">While Draw is true, the eraser checks to see if its tip intersects with any existing brush strokes.</span></span> <span data-ttu-id="19289-446">이렇게 하면 축소 하 고 삭제할 큐에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="19289-446">If it does, they are added to a queue to be shrunk down and deleted.</span></span>

## <a name="advanced-design---teleportation-and-locomotion"></a><span data-ttu-id="19289-447">고급 디자인-Teleportation 및 locomotion</span><span class="sxs-lookup"><span data-stu-id="19289-447">Advanced design - Teleportation and locomotion</span></span>

<span data-ttu-id="19289-448">사용자가 엄지 스틱을 사용 하 여 teleportation를 사용 하 여 장면 주위로 이동할 수 있도록 하려면 **MixedRealityCamera**대신 **MixedRealityCameraParent** 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-448">If you want to allow the user to move around the scene with teleportation using thumbstick, use **MixedRealityCameraParent** instead of **MixedRealityCamera**.</span></span> <span data-ttu-id="19289-449">**Inputmanager** 및 **DefaultCusor**도 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-449">You also need to add **InputManager** and **DefaultCusor**.</span></span> <span data-ttu-id="19289-450">**MixedRealityCameraParent** 에는 이미 **Motioncontrollers** 와 **경계가** 자식 구성 요소로 포함 되어 있으므로 기존 **motioncontrollers** 및 **Environment** prefab을 제거 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-450">Since **MixedRealityCameraParent** already includes **MotionControllers** and **Boundary** as child components, you should remove existing **MotionControllers** and **Environment** prefab.</span></span>

### <a name="instructions"></a><span data-ttu-id="19289-451">지침</span><span class="sxs-lookup"><span data-stu-id="19289-451">Instructions</span></span>

* <span data-ttu-id="19289-452">**계층** 패널에서 **MixedRealityCamera**, **Environment** 및 **motioncontrollers** 를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-452">In the **Hierarchy** panel, delete **MixedRealityCamera**, **Environment** and **MotionControllers**</span></span>
* <span data-ttu-id="19289-453">**프로젝트 패널**에서 다음 prefabs을 검색 하 여 **계층** 패널로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="19289-453">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="19289-454">Asset/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**</span><span class="sxs-lookup"><span data-stu-id="19289-454">Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**</span></span>
    * <span data-ttu-id="19289-455">자산/AppPrefabs/입력/Prefabs/**Inputmanager**</span><span class="sxs-lookup"><span data-stu-id="19289-455">Assets/AppPrefabs/Input/Prefabs/**InputManager**</span></span>
    * <span data-ttu-id="19289-456">자산/AppPrefabs/입력/Prefabs/커서/**Defaultcursor**</span><span class="sxs-lookup"><span data-stu-id="19289-456">Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**</span></span>

![혼합 현실 카메라 부모](images/mr213-cameraparent-300px.png)
* <span data-ttu-id="19289-458">**계층** 패널에서 **입력 관리자** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-458">In the **Hierarchy** panel, click **Input Manager**</span></span>
* <span data-ttu-id="19289-459">**검사기** 패널에서 **간단한 단일 포인터 선택기** 섹션까지 아래로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-459">In the **Inspector** panel, scroll down to the **Simple Single Pointer Selector** section</span></span>
* <span data-ttu-id="19289-460">**계층** 패널에서 **defaultcursor** 를 **커서** 필드로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="19289-460">From the **Hierarchy** panel, drag **DefaultCursor** into **Cursor** field</span></span>

![DefaultCursor 할당](images/mr213-defaultcursor-500px.png)
* <span data-ttu-id="19289-462">장면을 **저장** 하 고 **재생** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-462">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="19289-463">엄지 스틱을 사용 하 여 왼쪽/오른쪽 또는 텔레포트로 회전할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-463">You will be able to use the thumbstick to rotate left/right or teleport.</span></span>

## <a name="the-end"></a><span data-ttu-id="19289-464">끝</span><span class="sxs-lookup"><span data-stu-id="19289-464">The end</span></span>

<span data-ttu-id="19289-465">이 자습서의 끝입니다!</span><span class="sxs-lookup"><span data-stu-id="19289-465">And that's the end of this tutorial!</span></span> <span data-ttu-id="19289-466">배운 내용:</span><span class="sxs-lookup"><span data-stu-id="19289-466">You learned:</span></span>
* <span data-ttu-id="19289-467">Unity의 게임 모드 및 런타임에서 동작 컨트롤러 모델을 사용 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-467">How to work with motion controller models in Unity's game mode and runtime.</span></span>
* <span data-ttu-id="19289-468">다양 한 형식의 단추 이벤트 및 해당 응용 프로그램을 사용 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="19289-468">How to use different types of button events and their applications.</span></span>
* <span data-ttu-id="19289-469">컨트롤러 위에 UI 요소를 오버레이 하거나 완전히 사용자 지정 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="19289-469">How to overlay UI elements on top of the controller or fully customize it.</span></span>

<span data-ttu-id="19289-470">이제 이동 컨트롤러를 사용 하 여 사용자 고유의 몰입 형 환경을 만들 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-470">You are now ready to start creating your own immersive experience with motion controllers!</span></span>

## <a name="completed-scenes"></a><span data-ttu-id="19289-471">완료 된 장면</span><span class="sxs-lookup"><span data-stu-id="19289-471">Completed scenes</span></span>

* <span data-ttu-id="19289-472">Unity의 **프로젝트** 패널에서 **장면** 폴더를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="19289-472">In Unity's **Project** panel click on the **Scenes** folder.</span></span>
* <span data-ttu-id="19289-473">두 Unity sceens **MixedReality213** 및 **MixedReality213Advanced**를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="19289-473">You will find two Unity sceens **MixedReality213** and **MixedReality213Advanced**.</span></span>
    * <span data-ttu-id="19289-474">**MixedReality213**: 단일 브러시를 사용 하 여 완료 된 장면</span><span class="sxs-lookup"><span data-stu-id="19289-474">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="19289-475">**MixedReality213Advanced**: 선택 단추의 보도 금액 예제를 사용 하는 여러 브러시가 있는 완료 된 장면</span><span class="sxs-lookup"><span data-stu-id="19289-475">**MixedReality213Advanced**: Completed scene with multiple brush with select button's press amount example</span></span>

## <a name="see-also"></a><span data-ttu-id="19289-476">참조</span><span class="sxs-lookup"><span data-stu-id="19289-476">See also</span></span>

* [<span data-ttu-id="19289-477">MR 입력 213 프로젝트 파일</span><span class="sxs-lookup"><span data-stu-id="19289-477">MR Input 213 project files</span></span>](https://github.com/Microsoft/MixedReality213)
* [<span data-ttu-id="19289-478">혼합 현실 도구 키트-동작 컨트롤러 테스트 장면</span><span class="sxs-lookup"><span data-stu-id="19289-478">Mixed Reality Toolkit - Motion Controller Test scene</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [<span data-ttu-id="19289-479">혼합 현실 도구 키트-잡기 메커니즘</span><span class="sxs-lookup"><span data-stu-id="19289-479">Mixed Reality Toolkit - Grab Mechanics</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [<span data-ttu-id="19289-480">동작 컨트롤러 개발 지침</span><span class="sxs-lookup"><span data-stu-id="19289-480">Motion controller development guidelines</span></span>](motion-controllers.md)
