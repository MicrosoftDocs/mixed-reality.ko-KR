---
title: MR 입력 213
description: Unity에서 Visual Studio 및 몰입 형 헤드셋을 사용 하 여 컨트롤러 동작의 세부 정보를 알아보려면이 코딩 자습서를 수행 합니다.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, 컨트롤러, academy 자습서 mixedrealitytoolkit-unity 몰입 형, 동작
ms.openlocfilehash: 85449795a4fb3d182101cb5b4c4ce3fe85b009c0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604702"
---
>[!NOTE]
><span data-ttu-id="3766b-104">혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="3766b-105">따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="3766b-106">이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="3766b-107">지원 되는 장치에서 작업을 계속 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="3766b-108">새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="3766b-109">게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-input-213-motion-controllers"></a><span data-ttu-id="3766b-110">MR 입력 213: 컨트롤러 동작</span><span class="sxs-lookup"><span data-stu-id="3766b-110">MR Input 213: Motion controllers</span></span>

<span data-ttu-id="3766b-111">혼합된 현실 세계에서 동작 컨트롤러 다른 수준의 상호 작용을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-111">Motion controllers in the mixed reality world add another level of interactivity.</span></span> <span data-ttu-id="3766b-112">사용 하 여 [컨트롤러 동작](motion-controllers.md), 직접 집중 교육을 늘리면 더 자연 스러운 방식으로 실제 상황에서는 실제 조작 비슷합니다 개체 상호 작용 하 고 앱 환경을 근원 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-112">With [motion controllers](motion-controllers.md), we can directly interact with objects in a more natural way, similar to our physical interactions in real life, increasing immersion and delight in your app experience.</span></span>

<span data-ttu-id="3766b-113">MR 입력 213에서 동작 컨트롤러의 입력된 이벤트를 단순 공간 그리기 환경을 만들어 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-113">In MR Input 213, we will explore the motion controller's input events by creating a simple spatial painting experience.</span></span> <span data-ttu-id="3766b-114">이 앱을 사용 하 여 사용자는 다양 한 유형의 브러시 및 색을 사용 하 여 3 차원 공간에서 그릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-114">With this app, users can paint in three-dimensional space with various types of brushes and colors.</span></span>

## <a name="topics-covered-in-this-tutorial"></a><span data-ttu-id="3766b-115">이 자습서에서 다루는 항목</span><span class="sxs-lookup"><span data-stu-id="3766b-115">Topics covered in this tutorial</span></span>

|![MixedReality213 Topic1](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|<span data-ttu-id="3766b-119">**컨트롤러 시각화**</span><span class="sxs-lookup"><span data-stu-id="3766b-119">**Controller visualization**</span></span>|<span data-ttu-id="3766b-120">**컨트롤러 입력된 이벤트**</span><span class="sxs-lookup"><span data-stu-id="3766b-120">**Controller input events**</span></span>|<span data-ttu-id="3766b-121">**사용자 지정 컨트롤러 및 UI**</span><span class="sxs-lookup"><span data-stu-id="3766b-121">**Custom controller and UI**</span></span>|
|<span data-ttu-id="3766b-122">Unity 게임 모드 및 런타임의 동작 컨트롤러 모델을 렌더링 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-122">Learn how to render motion controller models in Unity's game mode and runtime.</span></span>|<span data-ttu-id="3766b-123">다양 한 유형의 단추 이벤트 및 해당 응용 프로그램을 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-123">Understand different types of button events and their applications.</span></span>|<span data-ttu-id="3766b-124">컨트롤러를 기반으로 UI 요소를 오버레이 하거나 완전히 사용자 지정 하는 방법에 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-124">Learn how to overlay UI elements on top of the controller or fully customize it.</span></span>|

## <a name="device-support"></a><span data-ttu-id="3766b-125">장치 지원</span><span class="sxs-lookup"><span data-stu-id="3766b-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="3766b-126">과정</span><span class="sxs-lookup"><span data-stu-id="3766b-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="3766b-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="3766b-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="3766b-128"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="3766b-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="3766b-129">MR 입력 213: 컨트롤러 동작</span><span class="sxs-lookup"><span data-stu-id="3766b-129">MR Input 213: Motion controllers</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="3766b-130">✔️</span><span class="sxs-lookup"><span data-stu-id="3766b-130">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="3766b-131">시작하기 전 주의 사항</span><span class="sxs-lookup"><span data-stu-id="3766b-131">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="3766b-132">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="3766b-132">Prerequisites</span></span>

<span data-ttu-id="3766b-133">몰입 형 헤드셋 설치 검사 목록에 표시 [이 페이지](install-the-tools.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-133">See the installation checklist for immersive headsets on [this page](install-the-tools.md).</span></span>

* <span data-ttu-id="3766b-134">이 자습서에서는 [Unity 2017.2.1p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)</span><span class="sxs-lookup"><span data-stu-id="3766b-134">This tutorial requires [Unity 2017.2.1p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)</span></span>

### <a name="project-files"></a><span data-ttu-id="3766b-135">프로젝트 파일</span><span class="sxs-lookup"><span data-stu-id="3766b-135">Project files</span></span>

* <span data-ttu-id="3766b-136">[파일을 다운로드할](https://github.com/Microsoft/MixedReality213/archive/master.zip) 프로젝트에 필요한 및 바탕 화면에 압축을 풉니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-136">[Download the files](https://github.com/Microsoft/MixedReality213/archive/master.zip) required by the project and extract the files to the Desktop.</span></span>

>[!NOTE]
><span data-ttu-id="3766b-137">을 다운로드 하기 전에 소스 코드를 확인 하려는 경우 있기 [GitHub에서 사용할 수 있는](https://github.com/Microsoft/MixedReality213)합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-137">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/MixedReality213).</span></span>

## <a name="unity-setup"></a><span data-ttu-id="3766b-138">Unity 설치</span><span class="sxs-lookup"><span data-stu-id="3766b-138">Unity setup</span></span>

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a><span data-ttu-id="3766b-139">목표</span><span class="sxs-lookup"><span data-stu-id="3766b-139">Objectives</span></span>

* <span data-ttu-id="3766b-140">Unity에 대 한 Windows Mixed Reality 개발 최적화</span><span class="sxs-lookup"><span data-stu-id="3766b-140">Optimize Unity for Windows Mixed Reality development</span></span>
* <span data-ttu-id="3766b-141">혼합된 현실 카메라 설정</span><span class="sxs-lookup"><span data-stu-id="3766b-141">Setup Mixed Reality Camera</span></span>
* <span data-ttu-id="3766b-142">환경 설정</span><span class="sxs-lookup"><span data-stu-id="3766b-142">Setup environment</span></span>

### <a name="instructions"></a><span data-ttu-id="3766b-143">지침</span><span class="sxs-lookup"><span data-stu-id="3766b-143">Instructions</span></span>

* <span data-ttu-id="3766b-144">Unity를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-144">Start Unity.</span></span>
* <span data-ttu-id="3766b-145">선택 **열려**합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-145">Select **Open**.</span></span>
* <span data-ttu-id="3766b-146">찾기 바탕 화면으로 이동 합니다 **MixedReality213 마스터** 하면 이전에 보관 되지 않은 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-146">Navigate to your Desktop and find the **MixedReality213-master** folder you previously unarchived.</span></span>
* <span data-ttu-id="3766b-147">**폴더 선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-147">Click **Select Folder**.</span></span>
* <span data-ttu-id="3766b-148">Unity 프로젝트 파일 로드 완료 되 면 Unity 편집기 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-148">Once Unity finishes loading project files, you will be able to see Unity editor.</span></span>
* <span data-ttu-id="3766b-149">Unity에서 선택 **파일 > 빌드 설정**합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-149">In Unity, select **File > Build Settings**.</span></span>

![MR213_BuildSettings](images/mr213-buildsettings-450px.png)
* <span data-ttu-id="3766b-151">선택 **유니버설 Windows 플랫폼** 에 **플랫폼** 나열 하 고 클릭 합니다 **플랫폼 전환** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-151">Select **Universal Windows Platform** in the **Platform** list and click the **Switch Platform** button.</span></span>
* <span data-ttu-id="3766b-152">대상 장치를 설정 **모든 장치**</span><span class="sxs-lookup"><span data-stu-id="3766b-152">Set Target Device to **Any device**</span></span>
* <span data-ttu-id="3766b-153">빌드 형식으로 **D3D**</span><span class="sxs-lookup"><span data-stu-id="3766b-153">Set Build Type to **D3D**</span></span>
* <span data-ttu-id="3766b-154">SDK로 **가장 최근에 설치 된**</span><span class="sxs-lookup"><span data-stu-id="3766b-154">Set SDK to **Latest Installed**</span></span>
* <span data-ttu-id="3766b-155">확인할 **Unity C# 프로젝트**</span><span class="sxs-lookup"><span data-stu-id="3766b-155">Check **Unity C# Projects**</span></span>
    * <span data-ttu-id="3766b-156">이렇게 하면 Unity 프로젝트를 다시 작성 하지 않고 Visual Studio 프로젝트에서 스크립트 파일을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-156">This allows you modify script files in the Visual Studio project without rebuilding Unity project.</span></span>
* <span data-ttu-id="3766b-157">클릭 **플레이어 설정**합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-157">Click **Player Settings**.</span></span>
* <span data-ttu-id="3766b-158">에 **검사기** 패널 맨 아래로 스크롤</span><span class="sxs-lookup"><span data-stu-id="3766b-158">In the **Inspector** panel, scroll down to the bottom</span></span>
* <span data-ttu-id="3766b-159">Xr 하이 설정에서 확인 **가상 현실 지원**</span><span class="sxs-lookup"><span data-stu-id="3766b-159">In XR Settings, check **Virtual Reality Supported**</span></span>
* <span data-ttu-id="3766b-160">가상 현실 Sdk 선택 **Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="3766b-160">Under Virtual Reality SDKs, select **Windows Mixed Reality**</span></span>

![MR213_XRSettings](images/mr213-xrsettings-500px.png)
* <span data-ttu-id="3766b-162">닫기 **빌드 설정** 창입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-162">Close **Build Settings** window.</span></span>

### <a name="project-structure"></a><span data-ttu-id="3766b-163">프로젝트 구조</span><span class="sxs-lookup"><span data-stu-id="3766b-163">Project structure</span></span>

<span data-ttu-id="3766b-164">이 자습서에서는  **[혼합 현실 Toolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-164">This tutorial uses **[Mixed Reality Toolkit - Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)**.</span></span> <span data-ttu-id="3766b-165">릴리스를 찾을 수 있습니다 [이 페이지](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-165">You can find the releases on [this page](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span></span>

![ProjectStructure](images/mr213-projectstructure-650px.png)

<span data-ttu-id="3766b-167">**참조에 대 한 완료 된 장면**</span><span class="sxs-lookup"><span data-stu-id="3766b-167">**Completed scenes for your reference**</span></span>
* <span data-ttu-id="3766b-168">완료 하는 두 Unity 장면에서 찾을 수 있습니다 **장면** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-168">You will find two completed Unity scenes under **Scenes** folder.</span></span>
    * <span data-ttu-id="3766b-169">**MixedReality213**: 단일 브러시를 사용 하 여 완료 된 장면</span><span class="sxs-lookup"><span data-stu-id="3766b-169">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="3766b-170">**MixedReality213Advanced**: 여러 브러시를 사용 하 여 고급 디자인에 대 한 장면 완료</span><span class="sxs-lookup"><span data-stu-id="3766b-170">**MixedReality213Advanced**: Completed scene for advanced design with multiple brushes</span></span>

<span data-ttu-id="3766b-171">**이 자습서에 대 한 새 장면 설치**</span><span class="sxs-lookup"><span data-stu-id="3766b-171">**New Scene setup for the tutorial**</span></span>
* <span data-ttu-id="3766b-172">Unity에서 클릭 **파일 > 새 장면**</span><span class="sxs-lookup"><span data-stu-id="3766b-172">In Unity, click **File > New Scene**</span></span>
* <span data-ttu-id="3766b-173">삭제할 **주 카메라** 고 **Directional Light**</span><span class="sxs-lookup"><span data-stu-id="3766b-173">Delete **Main Camera** and **Directional Light**</span></span>
* <span data-ttu-id="3766b-174">**프로젝트 패널**를 검색 하 고 끌어에 다음 prefabs 합니다 **계층** 패널:</span><span class="sxs-lookup"><span data-stu-id="3766b-174">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="3766b-175">Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**</span><span class="sxs-lookup"><span data-stu-id="3766b-175">Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**</span></span>
    * <span data-ttu-id="3766b-176">Assets/AppPrefabs/**Environment**</span><span class="sxs-lookup"><span data-stu-id="3766b-176">Assets/AppPrefabs/**Environment**</span></span>

![카메라 및 환경](images/mr213-cameraenvironment-300px.jpg)
* <span data-ttu-id="3766b-178">혼합 현실 도구 키트의 카메라 prefabs 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-178">There are two camera prefabs in Mixed Reality Toolkit:</span></span>
    * <span data-ttu-id="3766b-179">**MixedRealityCamera.prefab**: 카메라만</span><span class="sxs-lookup"><span data-stu-id="3766b-179">**MixedRealityCamera.prefab**: Camera only</span></span>
    * <span data-ttu-id="3766b-180">**MixedRealityCameraParent.prefab**: 카메라 + 텔레포트 경계</span><span class="sxs-lookup"><span data-stu-id="3766b-180">**MixedRealityCameraParent.prefab**: Camera + Teleportation + Boundary</span></span>
    * <span data-ttu-id="3766b-181">이 자습서에서는 사용할지 **MixedRealityCamera** 텔레포트 기능 없이 합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-181">In this tutorial, we will use **MixedRealityCamera** without teleportation feature.</span></span> <span data-ttu-id="3766b-182">이 인해 간단한 추가한 **환경** prefab 접지 느낌 사용자 기본 floor를 포함 하는 합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-182">Because of this, we added simple **Environment** prefab which contains a basic floor to make the user feel grounded.</span></span>
    * <span data-ttu-id="3766b-183">사용 하 여 텔레포트에 자세히 알아보려면 **MixedRealityCameraParent**를 참조 하세요 [텔레포트 및 locomotion 디자인-고급](#advanced-design---teleportation-and-locomotion)</span><span class="sxs-lookup"><span data-stu-id="3766b-183">To learn more about the teleportation with **MixedRealityCameraParent**, see [Advanced design - Teleportation and locomotion](#advanced-design---teleportation-and-locomotion)</span></span>

<span data-ttu-id="3766b-184">**Skybox 설치**</span><span class="sxs-lookup"><span data-stu-id="3766b-184">**Skybox setup**</span></span>
* <span data-ttu-id="3766b-185">클릭 **창 > 조명 > 설정**</span><span class="sxs-lookup"><span data-stu-id="3766b-185">Click **Window > Lighting > Settings**</span></span>
* <span data-ttu-id="3766b-186">오른쪽에 원을 클릭을 **Skybox 자료 필드**</span><span class="sxs-lookup"><span data-stu-id="3766b-186">Click the circle on the right side of the **Skybox Material field**</span></span>
* <span data-ttu-id="3766b-187">'회색' 입력 하 고 선택 **SkyboxGray**</span><span class="sxs-lookup"><span data-stu-id="3766b-187">Type in ‘gray’ and select **SkyboxGray**</span></span>

<span data-ttu-id="3766b-188">(Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)</span><span class="sxs-lookup"><span data-stu-id="3766b-188">(Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)</span></span>

![Skybox를 설정합니다.](images/mr123-skyboxsetting-400px.jpg)
* <span data-ttu-id="3766b-190">확인할 **Skybox** 옵션을 볼 수 회색 그라데이션 skybox 할당</span><span class="sxs-lookup"><span data-stu-id="3766b-190">Check **Skybox** option to be able to see assigned gray gradient skybox</span></span>

![설정/해제 skybox 옵션](images/mr213-skyboxcheck-400px.jpg)
* <span data-ttu-id="3766b-192">MixedRealityCamera, 환경 및 회색 skybox를 사용 하 여 장면 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-192">The scene with MixedRealityCamera, Environment and gray skybox will look like this.</span></span>

![MixedReality213 환경](images/mr213-environment-600px.jpg)
* <span data-ttu-id="3766b-194">클릭 **파일 >으로 장면 저장**</span><span class="sxs-lookup"><span data-stu-id="3766b-194">Click **File > Save Scene as**</span></span>
* <span data-ttu-id="3766b-195">**저장** 장면 폴더 이름으로 장면</span><span class="sxs-lookup"><span data-stu-id="3766b-195">**Save** your scene under Scenes folder with any name</span></span>

## <a name="chapter-1---controller-visualization"></a><span data-ttu-id="3766b-196">1 장-컨트롤러 시각화</span><span class="sxs-lookup"><span data-stu-id="3766b-196">Chapter 1 - Controller visualization</span></span>

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a><span data-ttu-id="3766b-197">목표</span><span class="sxs-lookup"><span data-stu-id="3766b-197">Objectives</span></span>

* <span data-ttu-id="3766b-198">컨트롤러 모델 Unity 게임 모드와 런타임 동작을 렌더링 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-198">Learn how to render motion controller models in Unity's game mode and at runtime.</span></span>

<span data-ttu-id="3766b-199">Windows Mixed Reality 컨트롤러 시각화에는 애니메이션된 컨트롤러 모델을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-199">Windows Mixed Reality provides an animated controller model for controller visualization.</span></span> <span data-ttu-id="3766b-200">앱에서 컨트롤러 시각화에 대해 수행할 수 있는 몇 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-200">There are several approaches you can take for controller visualization in your app:</span></span>
* <span data-ttu-id="3766b-201">기본값-수정 하지 않고 기본 컨트롤러를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="3766b-201">Default - Using default controller without modification</span></span>
* <span data-ttu-id="3766b-202">하이브리드-기본 컨트롤러를 사용 하 여 있지만 해당 요소 중 일부를 사용자 지정 또는 UI 구성 요소를 오버레이</span><span class="sxs-lookup"><span data-stu-id="3766b-202">Hybrid - Using default controller, but customizing some of its elements or overlaying UI components</span></span>
* <span data-ttu-id="3766b-203">대체-자체를 사용 하 여 컨트롤러에 대 한 3D 모델을 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="3766b-203">Replacement - Using your own customized 3D model for the controller</span></span>

<span data-ttu-id="3766b-204">이 챕터에서는 이러한 컨트롤러 사용자 지정의 예에 대 한 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-204">In this chapter, we will learn about the examples of these controller customizations.</span></span>

### <a name="instructions"></a><span data-ttu-id="3766b-205">지침</span><span class="sxs-lookup"><span data-stu-id="3766b-205">Instructions</span></span>

* <span data-ttu-id="3766b-206">에 **프로젝트** 패널에서 입력 **MotionControllers** 검색 상자에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-206">In the **Project** panel, type **MotionControllers** in the search box .</span></span> <span data-ttu-id="3766b-207">자산/HoloToolkit/입력/Prefabs 아래에서 찾을 수 있습니다/입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-207">You can also find it under Assets/HoloToolkit/Input/Prefabs/.</span></span>
* <span data-ttu-id="3766b-208">끌어서 합니다 **MotionControllers** 으로 prefab 합니다 **계층** 패널.</span><span class="sxs-lookup"><span data-stu-id="3766b-208">Drag the **MotionControllers** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="3766b-209">클릭 합니다 **MotionControllers** 의 prefab 합니다 **계층** 패널.</span><span class="sxs-lookup"><span data-stu-id="3766b-209">Click on the **MotionControllers** prefab in the **Hierarchy** panel.</span></span>

<span data-ttu-id="3766b-210">**MotionControllers prefab**</span><span class="sxs-lookup"><span data-stu-id="3766b-210">**MotionControllers prefab**</span></span>

<span data-ttu-id="3766b-211">**MotionControllers** prefab에는 **MotionControllerVisualizer** 대체 컨트롤러 모델에 대 한 슬롯을 제공 하는 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-211">**MotionControllers** prefab has a **MotionControllerVisualizer** script which provides the slots for alternate controller models.</span></span> <span data-ttu-id="3766b-212">손 모양 검 등 사용자 고유의 사용자 지정 3D 모델을 할당 하 고 ' 항상 사용 하 여 대체 왼쪽/오른쪽 모델 '을 확인 하는 경우 기본 모델 대신 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-212">If you assign your own custom 3D models such as a hand or a sword and check 'Always Use Alternate Left/Right Model', you will see them instead of the default model.</span></span> <span data-ttu-id="3766b-213">이 슬롯 4 장의 컨트롤러 모델은 브러시를 바꾸려면 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-213">We will use this slot in Chapter 4 to replace the controller model with a brush.</span></span>

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

<span data-ttu-id="3766b-215">**지침**</span><span class="sxs-lookup"><span data-stu-id="3766b-215">**Instructions**</span></span>
* <span data-ttu-id="3766b-216">에 **검사기** 패널에서 두 번 클릭 **MotionControllerVisualizer** Visual Studio의 코드를 참조 하는 스크립트</span><span class="sxs-lookup"><span data-stu-id="3766b-216">In the **Inspector** panel, double click **MotionControllerVisualizer** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="3766b-217">**MotionControllerVisualizer 스크립트**</span><span class="sxs-lookup"><span data-stu-id="3766b-217">**MotionControllerVisualizer script**</span></span>

<span data-ttu-id="3766b-218">합니다 **MotionControllerVisualizer** 하 고 **MotionControllerInfo** 클래스에 액세스 하는 기본 컨트롤러 모델을 수정할 수 있는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-218">The **MotionControllerVisualizer** and **MotionControllerInfo** classes provide the means to access & modify the default controller models.</span></span> <span data-ttu-id="3766b-219">**MotionControllerVisualizer** Unity의 구독할 **InteractionSourceDetected** 이벤트 및 파일이 있는 경우 컨트롤러 모델을 자동으로 인스턴스화합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-219">**MotionControllerVisualizer** subscribes to Unity's **InteractionSourceDetected** event and automatically instantiates controller models when they are found.</span></span>

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

<span data-ttu-id="3766b-220">컨트롤러 모델에 따라 전달할지 [glTF 사양](https://github.com/KhronosGroup/glTF)합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-220">The controller models are delivered according to [the glTF specification](https://github.com/KhronosGroup/glTF).</span></span> <span data-ttu-id="3766b-221">전송 및 3D 자산을 압축 하는 프로세스를 개선 하는 동안 일반적인 형식으로 제공 형식이으로 작성 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-221">This format has been created to provide a common format, while improving the process behind transmitting and unpacking 3D assets.</span></span> <span data-ttu-id="3766b-222">이 경우 검색 하 여 사용자의 환경을 최대한 원활 하 게 확인 하려고 하 고 동작 컨트롤러 버전 사용자를 사용할 수 있습니다는 보장 되지 않습니다는 런타임 시 컨트롤러 모델을 로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-222">In this case, we need to retrieve and load the controller models at runtime, as we want to make the user's experience as seamless as possible, and it's not guaranteed which version of the motion controllers the user might be using.</span></span> <span data-ttu-id="3766b-223">혼합 현실 도구 키트를 통해이 과정에서는 Khronos 그룹의 버전을 사용 하 여 [UnityGLTF 프로젝트](https://github.com/KhronosGroup/UnityGLTF)합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-223">This course, via the Mixed Reality Toolkit, uses a version of the Khronos Group's [UnityGLTF project](https://github.com/KhronosGroup/UnityGLTF).</span></span>

<span data-ttu-id="3766b-224">컨트롤러를 전달한 후 스크립트 사용할 수 있습니다 **MotionControllerInfo** 를 특정 컨트롤러 요소에 대 한 변환의 찾을 자체 올바르게 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-224">Once the controller has been delivered, scripts can use **MotionControllerInfo** to find the transforms for specific controller elements so they can correctly position themselves.</span></span>

<span data-ttu-id="3766b-225">뒷부분에 나오는 챕터에에서는 이러한 스크립트를 사용 하 여 컨트롤러에 UI 요소를 연결 하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-225">In a later chapter, we will learn how to use these scripts to attach UI elements to the controllers.</span></span>

<span data-ttu-id="3766b-226">*일부 스크립트를 사용 하 여 코드 블록을 찾을 수 있습니다 **#if! UNITY_EDITOR** 나 **UNITY_WSA**합니다. 이러한 코드 블록에 Windows를 배포할 때 UWP 런타임 에서만 실행 됩니다. Unity 편집기 및 UWP 앱 런타임에서 사용 되는 Api 집합은 다른 때문입니다.*</span><span class="sxs-lookup"><span data-stu-id="3766b-226">*In some scripts, you will find code blocks with **#if !UNITY_EDITOR** or **UNITY_WSA**. These code blocks run only on the UWP runtime when you deploy to Windows. This is because the set of APIs used by the Unity editor and the UWP app runtime are different.*</span></span>
* <span data-ttu-id="3766b-227">**저장할** 장면과 클릭 합니다 **재생** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-227">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="3766b-228">헤드셋에서 동작 컨트롤러를 사용 하 여 장면의 참조 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-228">You will be able to see the scene with motion controllers in your headset.</span></span> <span data-ttu-id="3766b-229">단추 클릭, 엄지 스틱 이동 및 터치 패드 터치 강조 표시에 대 한 자세한 애니메이션을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-229">You can see detailed animations for button clicks, thumbstick movement, and touchpad touch highlighting.</span></span>

![MR213_Controller 시각화 기본](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a><span data-ttu-id="3766b-231">2 장-UI 요소는 컨트롤러에 연결</span><span class="sxs-lookup"><span data-stu-id="3766b-231">Chapter 2 - Attaching UI elements to the controller</span></span>

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a><span data-ttu-id="3766b-232">목표</span><span class="sxs-lookup"><span data-stu-id="3766b-232">Objectives</span></span>

* <span data-ttu-id="3766b-233">동작 컨트롤러의 요소에 알아봅니다</span><span class="sxs-lookup"><span data-stu-id="3766b-233">Learn about the elements of the motion controllers</span></span>
* <span data-ttu-id="3766b-234">컨트롤러의 특정 부분에 개체를 연결 하는 방법에 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-234">Learn how to attach objects to specific parts of the controllers</span></span>

<span data-ttu-id="3766b-235">이 챕터에서는 사용자 수 쉽게 액세스 하 고 언제 든 지에 조작 하는 컨트롤러에 사용자 인터페이스 요소를 추가 하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-235">In this chapter, you will learn how to add user interface elements to the controller which the user can easily access and manipulate at anytime.</span></span> <span data-ttu-id="3766b-236">단순한 색 선택기 입력 터치 패드를 사용 하 여 UI를 추가 하는 방법 또한 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-236">You will also learn how to add a simple color picker UI using the touchpad input.</span></span>

### <a name="instructions"></a><span data-ttu-id="3766b-237">지침</span><span class="sxs-lookup"><span data-stu-id="3766b-237">Instructions</span></span>

* <span data-ttu-id="3766b-238">에 **프로젝트** 패널에서 검색할 **MotionControllerInfo** 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-238">In the **Project** panel, search **MotionControllerInfo** script.</span></span>
* <span data-ttu-id="3766b-239">검색 결과에서 두 번 클릭 **MotionControllerInfo** 스크립트를 Visual Studio에서 코드를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3766b-239">From the search result, double click **MotionControllerInfo** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="3766b-240">**MotionControllerInfo 스크립트**</span><span class="sxs-lookup"><span data-stu-id="3766b-240">**MotionControllerInfo script**</span></span>

<span data-ttu-id="3766b-241">첫 번째 단계 UI에 연결 하려는 컨트롤러의 요소를 선택 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-241">The first step is to choose which element of the controller you want the UI to attach to.</span></span> <span data-ttu-id="3766b-242">이러한 요소에 정의 된 **ControllerElementEnum** 에 **MotionControllerInfo.cs**합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-242">These elements are defined in **ControllerElementEnum** in **MotionControllerInfo.cs**.</span></span>

![MR213 MotionControllerElements](images/mr213-motioncontrollerelements-1000px.jpg)
* <span data-ttu-id="3766b-244">**홈**</span><span class="sxs-lookup"><span data-stu-id="3766b-244">**Home**</span></span>
* <span data-ttu-id="3766b-245">**메뉴**</span><span class="sxs-lookup"><span data-stu-id="3766b-245">**Menu**</span></span>
* <span data-ttu-id="3766b-246">**이해**</span><span class="sxs-lookup"><span data-stu-id="3766b-246">**Grasp**</span></span>
* <span data-ttu-id="3766b-247">**Thumbstick**</span><span class="sxs-lookup"><span data-stu-id="3766b-247">**Thumbstick**</span></span>
* <span data-ttu-id="3766b-248">**Select**</span><span class="sxs-lookup"><span data-stu-id="3766b-248">**Select**</span></span>
* <span data-ttu-id="3766b-249">**터치패드**</span><span class="sxs-lookup"><span data-stu-id="3766b-249">**Touchpad**</span></span>
* <span data-ttu-id="3766b-250">**포인팅 포즈** –이 요소 끝을 가리키는 정방향 컨트롤러를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-250">**Pointing pose** – this element represents the tip of the controller pointing forward direction.</span></span>

<span data-ttu-id="3766b-251">**지침**</span><span class="sxs-lookup"><span data-stu-id="3766b-251">**Instructions**</span></span>
* <span data-ttu-id="3766b-252">에 **프로젝트** 패널에서 검색할 **AttachToController** 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-252">In the **Project** panel, search **AttachToController** script.</span></span>
* <span data-ttu-id="3766b-253">검색 결과에서 두 번 클릭 **AttachToController** 스크립트를 Visual Studio에서 코드를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3766b-253">From the search result, double click **AttachToController** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="3766b-254">**AttachToController 스크립트**</span><span class="sxs-lookup"><span data-stu-id="3766b-254">**AttachToController script**</span></span>

<span data-ttu-id="3766b-255">합니다 **AttachToController** 스크립트는 모든 개체 요소를 사용 하는 손 지정 된 컨트롤러를 연결 하는 간단한 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-255">The **AttachToController** script provides a simple way to attach any objects to a specified controller handedness and element.</span></span>

<span data-ttu-id="3766b-256">In **AttachElementToController()**,</span><span class="sxs-lookup"><span data-stu-id="3766b-256">In **AttachElementToController()**,</span></span>
* <span data-ttu-id="3766b-257">선호도 사용 하 여 확인 **MotionControllerInfo.Handedness**</span><span class="sxs-lookup"><span data-stu-id="3766b-257">Check handedness using **MotionControllerInfo.Handedness**</span></span>
* <span data-ttu-id="3766b-258">사용 하 여 컨트롤러의 특정 요소를 가져옵니다 **MotionControllerInfo.TryGetElement()**</span><span class="sxs-lookup"><span data-stu-id="3766b-258">Get specific element of the controller using **MotionControllerInfo.TryGetElement()**</span></span>
* <span data-ttu-id="3766b-259">요소를 검색 한 후 컨트롤러 모델 부모 아래에 있는 해당 개체에서에서 변환 하 고 개체의 로컬 위치 및 회전을 0으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-259">After retrieving the element's transform from the controller model, parent the object under it and set object's local position & rotation to zero.</span></span>

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

<span data-ttu-id="3766b-260">사용 하는 가장 간단한 방법은 **AttachToController** 의 경우 처럼 스크립트에서 상속 하는 **ColorPickerWheel 합니다.**</span><span class="sxs-lookup"><span data-stu-id="3766b-260">The simplest way to use **AttachToController** script is to inherit from it, as we've done in the case of **ColorPickerWheel.**</span></span> <span data-ttu-id="3766b-261">재정의 하기만 합니다 **OnAttachToController** 및 **OnDetatchFromController** 설치를 수행 하기 위해 함수 / 컨트롤러 감지 되거나 연결이 끊어진 경우 분석 합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-261">Simply override the **OnAttachToController** and **OnDetatchFromController** functions to perform your setup / breakdown when the controller is detected / disconnected.</span></span>

<span data-ttu-id="3766b-262">**지침**</span><span class="sxs-lookup"><span data-stu-id="3766b-262">**Instructions**</span></span>
* <span data-ttu-id="3766b-263">에 **프로젝트** 패널에서 검색 상자에 입력 **ColorPickerWheel**합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-263">In the **Project** panel, type in the search box **ColorPickerWheel**.</span></span> <span data-ttu-id="3766b-264">자산/AppPrefabs 아래에서 찾을 수 있습니다/입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-264">You can also find it under Assets/AppPrefabs/.</span></span>
* <span data-ttu-id="3766b-265">끌기 **ColorPickerWheel** 으로 prefab 합니다 **계층** 패널입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-265">Drag **ColorPickerWheel** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="3766b-266">클릭 합니다 **ColorPickerWheel** 의 prefab 합니다 **계층** 패널.</span><span class="sxs-lookup"><span data-stu-id="3766b-266">Click the **ColorPickerWheel** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="3766b-267">에 **검사기** 패널에서 두 번 클릭 **ColorPickerWheel** 스크립트를 Visual Studio에서 코드를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3766b-267">In the **Inspector** panel, double click **ColorPickerWheel** Script to see the code in Visual Studio.</span></span>

![ColorPickerWheel prefab](images/mr213-colorpickerwheel-1000px.jpg)

<span data-ttu-id="3766b-269">**ColorPickerWheel 스크립트**</span><span class="sxs-lookup"><span data-stu-id="3766b-269">**ColorPickerWheel script**</span></span>

<span data-ttu-id="3766b-270">이후 **ColorPickerWheel** 상속 **AttachToController**를 보여 줍니다 **선호도** 및 **요소** 에  **검사기** 패널입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-270">Since **ColorPickerWheel** inherits **AttachToController**, it shows **Handedness** and **Element** in the **Inspector** panel.</span></span> <span data-ttu-id="3766b-271">왼쪽된 컨트롤러에서 터치 패드 요소에 UI 연결에서는 했습니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-271">We'll be attaching the UI to the Touchpad element on the left controller.</span></span>

![ColorPickerWheel 스크립트](images/mr213-attachtocontroller-300px.jpg)

<span data-ttu-id="3766b-273">**ColorPickerWheel** 재정의 된 **OnAttachToController** 하 고 **OnDetatchFromController** 색 선택 영역에 대 한 다음 챕터에서 사용할 입력된 이벤트를 구독할 수 터치 패드를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-273">**ColorPickerWheel** overrides the **OnAttachToController** and **OnDetatchFromController** to subscribe to the input event which will be used in next chapter for color selection with touchpad input.</span></span>

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
* <span data-ttu-id="3766b-274">**저장할** 장면과 클릭 합니다 **재생** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-274">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="3766b-275">**컨트롤러에 개체를 연결 하는 것에 대 한 대체 메서드**</span><span class="sxs-lookup"><span data-stu-id="3766b-275">**Alternative method for attaching objects to the controllers**</span></span>

<span data-ttu-id="3766b-276">스크립트에서 상속 하는 것이 좋습니다 **AttachToController** 시키고 **OnAttachToController**합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-276">We recommend that your scripts inherit from **AttachToController** and override **OnAttachToController**.</span></span> <span data-ttu-id="3766b-277">그러나이 항상 못할 합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-277">However, this may not always be possible.</span></span> <span data-ttu-id="3766b-278">대신 독립 실행형 구성 요소로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-278">An alternative is using it as a standalone component.</span></span> <span data-ttu-id="3766b-279">이 스크립트를 리팩터링 하지 않고는 기존 prefab 컨트롤러에 연결 하려는 경우 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-279">This can be useful when you want to attach an existing prefab to a controller without refactoring your scripts.</span></span> <span data-ttu-id="3766b-280">IsAttached 하도록 설정할 때까지 기다리는 클래스 하기만 설정을 수행 하기 전에 true입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-280">Simply have your class wait for IsAttached to be set to true before performing any setup.</span></span> <span data-ttu-id="3766b-281">이 작업을 수행 하는 가장 간단한 방법은 코 루틴을 사용 하 여 '시작 합니다.'가</span><span class="sxs-lookup"><span data-stu-id="3766b-281">The simplest way to do this is by using a coroutine for 'Start.'</span></span>

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a><span data-ttu-id="3766b-282">3 장-터치 입력을 사용 하 여 작업</span><span class="sxs-lookup"><span data-stu-id="3766b-282">Chapter 3 - Working with touchpad input</span></span>

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a><span data-ttu-id="3766b-283">목표</span><span class="sxs-lookup"><span data-stu-id="3766b-283">Objectives</span></span>

* <span data-ttu-id="3766b-284">터치 패드 입력된 데이터 이벤트를 받는 방법</span><span class="sxs-lookup"><span data-stu-id="3766b-284">Learn how to get touchpad input data events</span></span>
* <span data-ttu-id="3766b-285">앱 환경에 대 한 터치 패드 축 위치 정보를 사용 하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="3766b-285">Learn how to use touchpad axis position information for your app experience</span></span>

### <a name="instructions"></a><span data-ttu-id="3766b-286">지침</span><span class="sxs-lookup"><span data-stu-id="3766b-286">Instructions</span></span>

* <span data-ttu-id="3766b-287">에 **계층 구조** 패널에서 **ColorPickerWheel**</span><span class="sxs-lookup"><span data-stu-id="3766b-287">In the **Hierarchy** panel, click **ColorPickerWheel**</span></span>
* <span data-ttu-id="3766b-288">에 **검사기** 패널의 **Animatior**를 두 번 클릭 **ColorPickerWheelController**</span><span class="sxs-lookup"><span data-stu-id="3766b-288">In the **Inspector** panel, under **Animatior**, double click **ColorPickerWheelController**</span></span>
* <span data-ttu-id="3766b-289">볼 수 있습니다 **애니메이터** 열린 탭</span><span class="sxs-lookup"><span data-stu-id="3766b-289">You will be able to see **Animator** tab opened</span></span>

<span data-ttu-id="3766b-290">**Unity의 애니메이션 컨트롤러를 사용 하 여 UI 표시/숨기기**</span><span class="sxs-lookup"><span data-stu-id="3766b-290">**Showing/hiding UI with Unity's Animation controller**</span></span>

<span data-ttu-id="3766b-291">표시 하거나 숨기려면 합니다 **ColorPickerWheel** 애니메이션을 사용 하 여 UI를 사용 하 여 [Unity의 애니메이션 시스템](https://docs.unity3d.com/Manual/AnimationOverview.html)입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-291">To show and hide the **ColorPickerWheel** UI with animation, we are using [Unity's animation system](https://docs.unity3d.com/Manual/AnimationOverview.html).</span></span> <span data-ttu-id="3766b-292">설정 합니다 **ColorPickerWheel**의 **Visible** 속성을 true 또는 false 트리거 **표시** 하 고 **숨기기** 애니메이션 트리거.</span><span class="sxs-lookup"><span data-stu-id="3766b-292">Setting the **ColorPickerWheel**'s **Visible** property to true or false triggers **Show** and **Hide** animation triggers.</span></span> <span data-ttu-id="3766b-293">**표시** 하 고 **숨기기** 에 정의 된 매개 변수를 **ColorPickerWheelController** 애니메이션 컨트롤러입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-293">**Show** and **Hide** parameters are defined in the **ColorPickerWheelController** animation controller.</span></span>

![Unity 애니메이션 컨트롤러](images/mr123-animationcontroller-550px.jpg)

<span data-ttu-id="3766b-295">**지침**</span><span class="sxs-lookup"><span data-stu-id="3766b-295">**Instructions**</span></span>
* <span data-ttu-id="3766b-296">에 **계층 구조** 패널에서 **ColorPickerWheel** prefab</span><span class="sxs-lookup"><span data-stu-id="3766b-296">In the **Hierarchy** panel, select **ColorPickerWheel** prefab</span></span>
* <span data-ttu-id="3766b-297">에 **검사기** 패널에서 두 번 클릭 **ColorPickerWheel** Visual Studio의 코드를 참조 하는 스크립트</span><span class="sxs-lookup"><span data-stu-id="3766b-297">In the **Inspector** panel, double click **ColorPickerWheel** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="3766b-298">**ColorPickerWheel 스크립트**</span><span class="sxs-lookup"><span data-stu-id="3766b-298">**ColorPickerWheel script**</span></span>

<span data-ttu-id="3766b-299">**ColorPickerWheel** Unity의 구독할 **InteractionSourceUpdated** 터치 이벤트를 수신 대기 하는 이벤트입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-299">**ColorPickerWheel** subscribes to Unity's **InteractionSourceUpdated** event to listen for touchpad events.</span></span>

<span data-ttu-id="3766b-300">**InteractionSourceUpdated()**, 스크립트는 먼저 확인 하는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-300">In **InteractionSourceUpdated()**, the script first checks to ensure that it:</span></span>
* <span data-ttu-id="3766b-301">터치 패드 이벤트 실제로 (obj.state. **touchpadTouched**)</span><span class="sxs-lookup"><span data-stu-id="3766b-301">is actually a touchpad event (obj.state.**touchpadTouched**)</span></span>
* <span data-ttu-id="3766b-302">왼쪽된 컨트롤러에서 시작 (obj.state.source. **사용 하는 손**)</span><span class="sxs-lookup"><span data-stu-id="3766b-302">originates from the left controller (obj.state.source.**handedness**)</span></span>

<span data-ttu-id="3766b-303">둘 다 true 인 경우에 터치 패드 위치 (obj.state. **touchpadPosition**)에 할당 됩니다 **selectorPosition**합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-303">If both are true, the touchpad position (obj.state.**touchpadPosition**) is assigned to **selectorPosition**.</span></span>

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

<span data-ttu-id="3766b-304">**update ()** 에 따라 **표시** 속성을 트리거하는 색 선택기의 애니메이터 구성 요소에서 표시 / 숨기기 애니메이션 트리거</span><span class="sxs-lookup"><span data-stu-id="3766b-304">In **Update()**, based on **visible** property, it triggers Show and Hide animation triggers in the color picker's animator component</span></span>

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

<span data-ttu-id="3766b-305">**update ()** 하십시오 **selectorPosition** 광선을 그린 UV 위치를 반환 하는 색상표의 메시 collider에 캐스팅 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-305">In **Update()**, **selectorPosition** is used to cast a ray at the color wheel's mesh collider, which returns a UV position.</span></span> <span data-ttu-id="3766b-306">이 위치 픽셀 좌표를 찾아 색 색상표의 질감의 값을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-306">This position can then be used to find the pixel coordinate and color value of the color wheel's texture.</span></span> <span data-ttu-id="3766b-307">이 값은 다른 스크립트를 통해 액세스할 수 합니다 **SelectedColor** 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-307">This value is accessible to other scripts via the **SelectedColor** property.</span></span>

![색 선택기 휠 플레이어가](images/mr213-colorpickerwheel-raycast-700px.png)

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

## <a name="chapter-4---overriding-controller-model"></a><span data-ttu-id="3766b-309">4 장-컨트롤러 모델 재정의</span><span class="sxs-lookup"><span data-stu-id="3766b-309">Chapter 4 - Overriding controller model</span></span>

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a><span data-ttu-id="3766b-310">목표</span><span class="sxs-lookup"><span data-stu-id="3766b-310">Objectives</span></span>

* <span data-ttu-id="3766b-311">사용자 지정 3D 모델을 사용 하 여 컨트롤러 모델을 재정의 하는 방법에 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-311">Learn how to override the controller model with a custom 3D model.</span></span>

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a><span data-ttu-id="3766b-313">지침</span><span class="sxs-lookup"><span data-stu-id="3766b-313">Instructions</span></span>

* <span data-ttu-id="3766b-314">클릭 **MotionControllers** 에 **계층** 패널입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-314">Click **MotionControllers** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="3766b-315">오른쪽에 원을 클릭 합니다 **대체 오른쪽 컨트롤러** 필드입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-315">Click the circle on the right side of the **Alternate Right Controller** field.</span></span>
* <span data-ttu-id="3766b-316">입력 **' BrushController**'를 prefab 결과에서 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-316">Type in **'BrushController**' and select the prefab from the result.</span></span> <span data-ttu-id="3766b-317">자산/AppPrefabs 아래에서 찾을 수 있습니다/**BrushController**합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-317">You can find it under Assets/AppPrefabs/**BrushController**.</span></span>
* <span data-ttu-id="3766b-318">확인 **항상 대체 오른쪽 모델 사용**</span><span class="sxs-lookup"><span data-stu-id="3766b-318">Check **Always Use Alternate Right Model**</span></span>

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

<span data-ttu-id="3766b-320">합니다 **BrushController** prefab에 포함 될 필요가 없습니다 합니다 **계층** 패널입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-320">The **BrushController** prefab does not have to be included in the **Hierarchy** panel.</span></span> <span data-ttu-id="3766b-321">그러나 하위 구성 요소를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-321">However, to check out its child components:</span></span>
* <span data-ttu-id="3766b-322">에 **프로젝트** 패널에 입력 합니다 **BrushController** 끌어서 **BrushController** 으로 prefab 합니다 **계층** 패널.</span><span class="sxs-lookup"><span data-stu-id="3766b-322">In the **Project** panel, type in **BrushController** and drag **BrushController** prefab into the **Hierarchy** panel.</span></span>

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

<span data-ttu-id="3766b-324">찾을 수 있습니다 합니다 **팁** 구성 요소 **BrushController**합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-324">You will find the **Tip** component in **BrushController**.</span></span> <span data-ttu-id="3766b-325">해당 변환 그리기 줄 시작/중지에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-325">We will use its transform to start/stop drawing lines.</span></span>
* <span data-ttu-id="3766b-326">삭제 된 **BrushController** 에서 합니다 **계층** 패널입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-326">Delete the **BrushController** from the **Hierarchy** panel.</span></span>
* <span data-ttu-id="3766b-327">**저장할** 장면과 클릭 합니다 **재생** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-327">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="3766b-328">브러시 모델 오른쪽 동작 컨트롤러를 교체 했습니다. 참조 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-328">You will be able to see the brush model replaced the right-hand motion controller.</span></span>

## <a name="chapter-5---painting-with-select-input"></a><span data-ttu-id="3766b-329">5 장-선택 입력을 사용 하 여 그리기</span><span class="sxs-lookup"><span data-stu-id="3766b-329">Chapter 5 - Painting with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a><span data-ttu-id="3766b-330">목표</span><span class="sxs-lookup"><span data-stu-id="3766b-330">Objectives</span></span>

* <span data-ttu-id="3766b-331">선택 단추 이벤트를 사용 하 여 시작 하 고 선 그리기를 중지 하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="3766b-331">Learn how to use the Select button event to start and stop a line drawing</span></span>

### <a name="instructions"></a><span data-ttu-id="3766b-332">지침</span><span class="sxs-lookup"><span data-stu-id="3766b-332">Instructions</span></span>

* <span data-ttu-id="3766b-333">검색 **BrushController** 의 prefab 합니다 **프로젝트** 패널입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-333">Search **BrushController** prefab in the **Project** panel.</span></span>
* <span data-ttu-id="3766b-334">에 **검사기** 패널에서 두 번 클릭 **BrushController** Visual Studio의 코드를 참조 하는 스크립트</span><span class="sxs-lookup"><span data-stu-id="3766b-334">In the **Inspector** panel, double click **BrushController** Script to see the code in Visual Studio</span></span>

<span data-ttu-id="3766b-335">**BrushController 스크립트**</span><span class="sxs-lookup"><span data-stu-id="3766b-335">**BrushController script**</span></span>

<span data-ttu-id="3766b-336">**BrushController** InteractionManager의 구독할 **InteractionSourcePressed** 하 고 **InteractionSourceReleased** 이벤트입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-336">**BrushController** subscribes to the InteractionManager's **InteractionSourcePressed** and **InteractionSourceReleased** events.</span></span> <span data-ttu-id="3766b-337">때 **InteractionSourcePressed** 이벤트는 트리거되지 브러시의 **그리기** 속성이 true는 경우 **InteractionSourceReleased** 이벤트가 트리거될 브러시의 **그리기** 속성이 false로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-337">When **InteractionSourcePressed** event is triggered, the brush's **Draw** property is set to true; when **InteractionSourceReleased** event is triggered, the brush's **Draw** property is set to false.</span></span>

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

<span data-ttu-id="3766b-338">하는 동안 **그릴** 로 설정 된 true 브러시에에서 생성 됩니다 포인트는 인스턴스화된 Unity **LineRenderer**합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-338">While **Draw** is set to true, the brush will generate points in an instantiated Unity **LineRenderer**.</span></span> <span data-ttu-id="3766b-339">브러시의에이 prefab에 대 한 참조 유지 **스트로크 Prefab** 필드입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-339">A reference to this prefab is kept in the brush's **Stroke Prefab** field.</span></span>

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

<span data-ttu-id="3766b-340">색 선택기 휠 UI에서에서 현재 선택한 색을 사용 하도록 **BrushController** 에 대 한 참조가 있어야 합니다 **ColorPickerWheel** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-340">To use the currently selected color from the color picker wheel UI, **BrushController** needs to have a reference to the **ColorPickerWheel** object.</span></span> <span data-ttu-id="3766b-341">때문에 합니다 **BrushController** prefab 대체 컨트롤러로 런타임에 인스턴스화됩니다, 장면의 개체에 대 한 참조를 런타임에 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-341">Because the **BrushController** prefab is instantiated at runtime as a replacement controller, any references to objects in the scene will have to be set at runtime.</span></span> <span data-ttu-id="3766b-342">이 경우에 사용 하 여 **GameObject.FindObjectOfType** 찾으려고 합니다 **ColorPickerWheel**:</span><span class="sxs-lookup"><span data-stu-id="3766b-342">In this case we use **GameObject.FindObjectOfType** to locate the **ColorPickerWheel**:</span></span>

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
* <span data-ttu-id="3766b-343">**저장할** 장면과 클릭 합니다 **재생** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-343">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="3766b-344">선을 그리는 및 선택 단추를 사용 하 여 오른쪽 컨트롤러에서 페인트 하는 일을 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-344">You will be able to draw the lines and paint using the select button on the right-hand controller.</span></span>

## <a name="chapter-6---object-spawning-with-select-input"></a><span data-ttu-id="3766b-345">-6 장 입력 Select를 사용 하 여 개체 생성</span><span class="sxs-lookup"><span data-stu-id="3766b-345">Chapter 6 - Object spawning with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a><span data-ttu-id="3766b-346">목표</span><span class="sxs-lookup"><span data-stu-id="3766b-346">Objectives</span></span>

* <span data-ttu-id="3766b-347">선택 사용 방법 알아보기 단추 입력된 이벤트를 이해 하 고</span><span class="sxs-lookup"><span data-stu-id="3766b-347">Learn how to use Select and Grasp button input events</span></span>
* <span data-ttu-id="3766b-348">개체를 인스턴스화하는 방법을 알아봅니다</span><span class="sxs-lookup"><span data-stu-id="3766b-348">Learn how to instantiate objects</span></span>

### <a name="instructions"></a><span data-ttu-id="3766b-349">지침</span><span class="sxs-lookup"><span data-stu-id="3766b-349">Instructions</span></span>

* <span data-ttu-id="3766b-350">에 **프로젝트** 패널에서 입력 **ObjectSpawner** 검색 상자에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-350">In the **Project** panel, type **ObjectSpawner** in the search box.</span></span> <span data-ttu-id="3766b-351">자산/AppPrefabs 아래에서 찾을 수 있습니다 /</span><span class="sxs-lookup"><span data-stu-id="3766b-351">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="3766b-352">끌어서 합니다 **ObjectSpawner** 으로 prefab 합니다 **계층** 패널.</span><span class="sxs-lookup"><span data-stu-id="3766b-352">Drag the **ObjectSpawner** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="3766b-353">클릭 **ObjectSpawner** 에 **계층** 패널입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-353">Click **ObjectSpawner** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="3766b-354">**ObjectSpawner** 라는 필드가 **색 소스**합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-354">**ObjectSpawner** has a field named **Color Source**.</span></span>
* <span data-ttu-id="3766b-355">**계층 구조** 패널에서 끌어 합니다 **ColorPickerWheel** 이 필드에 대 한 참조입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-355">From the **Hierarchy** panel, drag the **ColorPickerWheel** reference into this field.</span></span>

![개체 Spawner 검사기](images/mr213-objectspawnercolorpickerwheel-650px.jpg)
* <span data-ttu-id="3766b-357">클릭 합니다 **ObjectSpawner** 의 prefab 합니다 **계층** 패널.</span><span class="sxs-lookup"><span data-stu-id="3766b-357">Click the **ObjectSpawner** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="3766b-358">에 **검사기** 패널에서 두 번 클릭 **ObjectSpawner** 스크립트를 Visual Studio에서 코드를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3766b-358">In the **Inspector** panel, double click **ObjectSpawner** Script to see the code in Visual Studio.</span></span>

<span data-ttu-id="3766b-359">**ObjectSpawner 스크립트**</span><span class="sxs-lookup"><span data-stu-id="3766b-359">**ObjectSpawner script**</span></span>

<span data-ttu-id="3766b-360">합니다 **ObjectSpawner** 공간으로 기본 메시 (큐브, 구, 실린더)의 복사본을 인스턴스화합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-360">The **ObjectSpawner** instantiates copies of a primitive mesh (cube, sphere, cylinder) into the space.</span></span> <span data-ttu-id="3766b-361">경우는 **InteractionSourcePressed** 선호도 확인 하는 경우 검색 되는 **InteractionSourcePressType.Grasp** 하거나 **InteractionSourcePressType.Select** 이벤트입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-361">When a **InteractionSourcePressed** is detected it checks the handedness and if it's an **InteractionSourcePressType.Grasp** or **InteractionSourcePressType.Select** event.</span></span>

<span data-ttu-id="3766b-362">에 **이해** 이벤트 현재 메시 유형 (구, 큐브의 원기둥)의 인덱스를 1만 큼</span><span class="sxs-lookup"><span data-stu-id="3766b-362">For a **Grasp** event, it increments the index of current mesh type (sphere, cube, cylinder)</span></span>

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

<span data-ttu-id="3766b-363">에 대 한는 **선택** 이벤트의 **SpawnObject()**, 새 개체는 인스턴스화된, 부모가 및 전 세계에 출시 합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-363">For a **Select** event, in **SpawnObject()**, a new object is instantiated, un-parented and released into the world.</span></span>

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

<span data-ttu-id="3766b-364">합니다 **ObjectSpawner** 사용 하는 **ColorPickerWheel** 표시 개체의 재질의 색을 설정 하려면.</span><span class="sxs-lookup"><span data-stu-id="3766b-364">The **ObjectSpawner** uses the **ColorPickerWheel** to set the color of the display object's material.</span></span> <span data-ttu-id="3766b-365">생성 된 개체는 해당 색을 유지 하므로이 자료의 인스턴스를 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-365">Spawned objects are given an instance of this material so they will retain their color.</span></span>
* <span data-ttu-id="3766b-366">**저장할** 장면과 클릭 합니다 **재생** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-366">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="3766b-367">감각을 단추를 사용 하 여 개체를 변경 하 고 선택 단추를 사용 하 여 개체를 생성 하는 일을 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-367">You will be able to change the objects with the Grasp button and spawn objects with the Select button.</span></span>

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a><span data-ttu-id="3766b-368">빌드 및 혼합 현실 포털에 앱 배포</span><span class="sxs-lookup"><span data-stu-id="3766b-368">Build and deploy app to Mixed Reality Portal</span></span>
* <span data-ttu-id="3766b-369">Unity에서 선택 **파일 > 빌드 설정**합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-369">In Unity, select **File > Build Settings**.</span></span>
* <span data-ttu-id="3766b-370">클릭 **열려 장면 추가** 현재 장면에 추가 하는 **Scenes In Build**합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-370">Click **Add Open Scenes** to add current scene to the **Scenes In Build**.</span></span>
* <span data-ttu-id="3766b-371">**빌드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-371">Click **Build**.</span></span>
* <span data-ttu-id="3766b-372">만들기는 **새 폴더** 이름을 "App"입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-372">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="3766b-373">한 번 클릭 합니다 **앱** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-373">Single click the **App** folder.</span></span>
* <span data-ttu-id="3766b-374">**폴더 선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-374">Click **Select Folder**.</span></span>
* <span data-ttu-id="3766b-375">Unity 완료 되 면 파일 탐색기 창이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-375">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="3766b-376">엽니다는 **앱** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-376">Open the **App** folder.</span></span>
* <span data-ttu-id="3766b-377">두 번 클릭 **YourSceneName.sln** Visual Studio 솔루션 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-377">Double click **YourSceneName.sln** Visual Studio Solution file.</span></span>
* <span data-ttu-id="3766b-378">에 디버그 대상 변경 맨 위의 도구 모음을 사용 하 여 Visual Studio에서 **릴리스** 들어오고를 ARM **X64**합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-378">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X64**.</span></span>
* <span data-ttu-id="3766b-379">선택한 장치 단추 옆의 드롭다운 화살표를 클릭 **로컬 컴퓨터**합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-379">Click on the drop-down arrow next to the Device button, and select **Local Machine**.</span></span>
* <span data-ttu-id="3766b-380">클릭 **디버그-> 디버깅 없이 시작** 누르거나 메뉴에서 **ctrl+f5**합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-380">Click **Debug -> Start Without debugging** in the menu or press **Ctrl + F5**.</span></span>

<span data-ttu-id="3766b-381">이제 앱 작성 및 혼합 현실 포털에 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-381">Now the app is built and installed in Mixed Reality Portal.</span></span> <span data-ttu-id="3766b-382">혼합 현실 포털에서 시작 메뉴를 통해이 작업을 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-382">You can launch it again through Start menu in Mixed Reality Portal.</span></span>

## <a name="advanced-design---brush-tools-with-radial-layout"></a><span data-ttu-id="3766b-383">고급 디자인-방사형 레이아웃을 사용 하 여 브러시 도구</span><span class="sxs-lookup"><span data-stu-id="3766b-383">Advanced design - Brush tools with radial layout</span></span>

![MixedReality213 Main](images/mr213-main-600px.jpg)

<span data-ttu-id="3766b-385">이 챕터에서는 사용자 지정 브러시 도구 컬렉션을 사용 하 여 기본 동작 컨트롤러 모델을 대체 하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-385">In this chapter, you will learn how to replace the default motion controller model with a custom brush tool collection.</span></span> <span data-ttu-id="3766b-386">참조를 위해 완성 된 장면을 찾을 수 있습니다 **MixedReality213Advanced** 아래에서 **장면** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-386">For your reference, you can find the completed scene **MixedReality213Advanced** under **Scenes** folder.</span></span>

### <a name="instructions"></a><span data-ttu-id="3766b-387">지침</span><span class="sxs-lookup"><span data-stu-id="3766b-387">Instructions</span></span>

* <span data-ttu-id="3766b-388">에 **프로젝트** 패널에서 입력 **BrushSelector** 검색 상자에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-388">In the **Project** panel, type **BrushSelector** in the search box .</span></span> <span data-ttu-id="3766b-389">자산/AppPrefabs 아래에서 찾을 수 있습니다 /</span><span class="sxs-lookup"><span data-stu-id="3766b-389">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="3766b-390">끌어서 합니다 **BrushSelector** 으로 prefab 합니다 **계층** 패널.</span><span class="sxs-lookup"><span data-stu-id="3766b-390">Drag the **BrushSelector** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="3766b-391">조직에 대 한 호출 빈 GameObject를 만듭니다 **브러시**</span><span class="sxs-lookup"><span data-stu-id="3766b-391">For organization, create an empty GameObject called **Brushes**</span></span>
* <span data-ttu-id="3766b-392">prefabs 다음 끌어 합니다 **프로젝트** 에 패널 **브러시**</span><span class="sxs-lookup"><span data-stu-id="3766b-392">Drag following prefabs from the **Project** panel into **Brushes**</span></span>
    * <span data-ttu-id="3766b-393">Assets/AppPrefabs/**BrushFat**</span><span class="sxs-lookup"><span data-stu-id="3766b-393">Assets/AppPrefabs/**BrushFat**</span></span>
    * <span data-ttu-id="3766b-394">Assets/AppPrefabs/**BrushThin**</span><span class="sxs-lookup"><span data-stu-id="3766b-394">Assets/AppPrefabs/**BrushThin**</span></span>
    * <span data-ttu-id="3766b-395">Assets/AppPrefabs/**Eraser**</span><span class="sxs-lookup"><span data-stu-id="3766b-395">Assets/AppPrefabs/**Eraser**</span></span>
    * <span data-ttu-id="3766b-396">Assets/AppPrefabs/**MarkerFat**</span><span class="sxs-lookup"><span data-stu-id="3766b-396">Assets/AppPrefabs/**MarkerFat**</span></span>
    * <span data-ttu-id="3766b-397">Assets/AppPrefabs/**MarkerThin**</span><span class="sxs-lookup"><span data-stu-id="3766b-397">Assets/AppPrefabs/**MarkerThin**</span></span>
    * <span data-ttu-id="3766b-398">Assets/AppPrefabs/**Pencil**</span><span class="sxs-lookup"><span data-stu-id="3766b-398">Assets/AppPrefabs/**Pencil**</span></span>

![브러시](images/mixedreality213-brushes-250px.png)
* <span data-ttu-id="3766b-400">클릭 **MotionControllers** 의 prefab 합니다 **계층** 패널입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-400">Click **MotionControllers** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="3766b-401">에 **검사기** 패널에서 선택 취소 **항상 사용 하 여 대체 오른쪽 모델** 에 **동작 컨트롤러 시각화 도우미**</span><span class="sxs-lookup"><span data-stu-id="3766b-401">In the **Inspector** panel, uncheck **Always Use Alternate Right Model** on the **Motion Controller Visualizer**</span></span>
* <span data-ttu-id="3766b-402">에 **계층 구조** 패널에서 **BrushSelector**</span><span class="sxs-lookup"><span data-stu-id="3766b-402">In the **Hierarchy** panel, click **BrushSelector**</span></span>
* <span data-ttu-id="3766b-403">**BrushSelector** 라는 필드가 **ColorPicker**</span><span class="sxs-lookup"><span data-stu-id="3766b-403">**BrushSelector** has a field named **ColorPicker**</span></span>
* <span data-ttu-id="3766b-404">**계층 구조** 패널에서 끌어 합니다 **ColorPickerWheel** 에 **ColorPicker** 필드에 **검사기** 패널.</span><span class="sxs-lookup"><span data-stu-id="3766b-404">From the **Hierarchy** panel, drag the **ColorPickerWheel** into **ColorPicker** field in the **Inspector** panel.</span></span>

![선택기 브러시 ColorPickerWheel 할당](images/mr213-brushselector-500px.jpg)
* <span data-ttu-id="3766b-406">에 **계층** 패널의 **BrushSelector** prefab을 선택 합니다 **메뉴** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-406">In the **Hierarchy** panel, under **BrushSelector** prefab, select the **Menu** object.</span></span>
* <span data-ttu-id="3766b-407">에 **검사기** 패널의 합니다 **LineObjectCollection** 구성 요소를 엽니다는 **개체** 배열 드롭다운 합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-407">In the **Inspector** panel, under the **LineObjectCollection** component, open the **Objects** array dropdown.</span></span> <span data-ttu-id="3766b-408">6 빈 슬롯을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-408">You will see 6 empty slots.</span></span>
* <span data-ttu-id="3766b-409">**계층** 패널에서 각 아래 부모가 prefabs 끌어 합니다 **브러시** GameObject 순서에 관계 없이 이러한 슬롯으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-409">From the **Hierarchy** panel, drag each of the prefabs parented under the **Brushes** GameObject into these slots in any order.</span></span> <span data-ttu-id="3766b-410">(프로젝트 폴더에 prefabs 없습니다 장면에서를 prefabs 끌어 온 있는지 확인 합니다.)</span><span class="sxs-lookup"><span data-stu-id="3766b-410">(Make sure you're dragging the prefabs from the scene, not the prefabs in the project folder.)</span></span>

![브러시 선택기](images/mr213-brushselectorbrushes-700px.jpg)

<span data-ttu-id="3766b-412">**BrushSelector prefab**</span><span class="sxs-lookup"><span data-stu-id="3766b-412">**BrushSelector prefab**</span></span>

<span data-ttu-id="3766b-413">이후를 **BrushSelector** 상속 **AttachToController**를 보여 줍니다 **선호도** 및 **요소** 옵션에  **검사기** 패널입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-413">Since the **BrushSelector** inherits **AttachToController**, it shows **Handedness** and **Element** options in the **Inspector** panel.</span></span> <span data-ttu-id="3766b-414">선택한 **오른쪽** 및 **내포할 가리키는** 브러시 도구 정방향으로 오른쪽 컨트롤러에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-414">We selected **Right** and **Pointing Pose** to attach brush tools to the right hand controller with forward direction.</span></span>

<span data-ttu-id="3766b-415">합니다 **BrushSelector** 두 유틸리티 사용:</span><span class="sxs-lookup"><span data-stu-id="3766b-415">The **BrushSelector** makes use of two utilities:</span></span>
* <span data-ttu-id="3766b-416">**타원**: 타원 도형 함께 공간에서 요소를 생성 하는 데 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-416">**Ellipse**: used to generate points in space along an ellipse shape.</span></span>
* <span data-ttu-id="3766b-417">**LineObjectCollection**: 모든 줄 클래스 (예: 타원)에 의해 생성 된 요소를 사용 하 여 개체를 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-417">**LineObjectCollection**: distributes objects using the points generated by any Line class (eg, Ellipse).</span></span> <span data-ttu-id="3766b-418">새로운 사용 타원 모양 따라 여 브러시에 적용할입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-418">This is what we'll be using to place our brushes along the Ellipse shape.</span></span>

<span data-ttu-id="3766b-419">를 결합 하면 이러한 유틸리티 방사형 메뉴를 만드는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-419">When combined, these utilities can be used to create a radial menu.</span></span>

<span data-ttu-id="3766b-420">**LineObjectCollection 스크립트**</span><span class="sxs-lookup"><span data-stu-id="3766b-420">**LineObjectCollection script**</span></span>

<span data-ttu-id="3766b-421">**LineObjectCollection** 크기, 위치 및 해당 선을 따라 배포 된 개체의 회전을 위한 컨트롤을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-421">**LineObjectCollection** has controls for the size, position and rotation of objects distributed along its line.</span></span> <span data-ttu-id="3766b-422">이것이 브러시 선택기와 같은 방사형 메뉴를 만드는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-422">This is useful for creating radial menus like the brush selector.</span></span> <span data-ttu-id="3766b-423">모양을 만들려면 브러시 확장 되는에서 선택한 가운데 위치에 접근 하는 대로 nothing 합니다 **ObjectScale** 가장자리 해제 테이퍼 센터에 대 한 최대치를 곡선입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-423">To create the appearance of brushes that scale up from nothing as they approach the center selected position, the **ObjectScale** curve peaks in the center and tapers off at the edges.</span></span>

<span data-ttu-id="3766b-424">**BrushSelector 스크립트**</span><span class="sxs-lookup"><span data-stu-id="3766b-424">**BrushSelector script**</span></span>

<span data-ttu-id="3766b-425">경우에 **BrushSelector**, 절차 애니메이션을 사용 하기로 결정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-425">In the case of the **BrushSelector**, we've chosen to use procedural animation.</span></span> <span data-ttu-id="3766b-426">브러시 모델에서 타원에 배포 되는 먼저 합니다 **LineObjectCollection** 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-426">First, brush models are distributed in an ellipse by the **LineObjectCollection** script.</span></span> <span data-ttu-id="3766b-427">그런 다음 각 브러시는 해당 위치에 따라 사용자의 직접 유지 관리에 대 한 해당 **DisplayMode** 선택에 따라 변경 하는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-427">Then, each brush is responsible for maintaining its position in the user's hand based on its **DisplayMode** value, which changes based on the selection.</span></span> <span data-ttu-id="3766b-428">사용자가 브러시 중단 되는 브러시 위치 전환의 높은 확률으로 인해 방법을 절차적 방법과 선택 했습니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-428">We chose a procedural approach because of the high probability of brush position transitions being interrupted as the user selects brushes.</span></span> <span data-ttu-id="3766b-429">Mecanim 애니메이션 중단을 정상적으로 처리할 수 있지만 간단한 Lerp 작업 보다 더 복잡할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-429">Mecanim animations can handle interruptions gracefully, but it tends to be more complicated than a simple Lerp operation.</span></span>

<span data-ttu-id="3766b-430">**BrushSelector** 둘의 조합을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-430">**BrushSelector** uses a combination of both.</span></span> <span data-ttu-id="3766b-431">터치 패드 입력 감지 되 면 브러시 옵션 표시 됩니다 및 방사형 메뉴 따라 강화 합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-431">When touchpad input is detected, brush options become visible and scale up along the radial menu.</span></span> <span data-ttu-id="3766b-432">(선택 된 내용이 있는지를 나타내는) 제한 시간 후 브러시 옵션 확장 아래로 마찬가지로 선택된 된 브러시를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-432">After a timeout period (which indicates that the user has made a selection) the brush options scale down again, leaving only the selected brush.</span></span>

<span data-ttu-id="3766b-433">**터치 입력을 시각화**</span><span class="sxs-lookup"><span data-stu-id="3766b-433">**Visualizing touchpad input**</span></span>

<span data-ttu-id="3766b-434">컨트롤러 모델에 완전히 대체 하는 경우에도 유용한 입력에 원래 모델 입력으로 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-434">Even in cases where the controller model has been completely replaced, it can be helpful to show input on the original model inputs.</span></span> <span data-ttu-id="3766b-435">이렇게 하면 실제로 사용자의 작업을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-435">This helps to ground the user's actions in reality.</span></span> <span data-ttu-id="3766b-436">에 대 한 합니다 **BrushSelector** 입력을 받으면 터치 패드를 간단 하 게 표시 되도록 설정 하기로 결정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-436">For the **BrushSelector** we've chosen to make the touchpad briefly visible when the input is received.</span></span> <span data-ttu-id="3766b-437">사용자 지정 자료를 사용 하 여 해당 자료를 교체 컨트롤러에서 터치 패드 요소를 검색 하 여 수행 했지만 다음 마지막 시간 터치 패드에 따라 해당 재질의 색 그라데이션을 적용 입력이 수신 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-437">This was done by retrieving the Touchpad element from the controller, replacing its material with a custom material, then applying a gradient to that material's color based on the last time touchpad input was received.</span></span>

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

<span data-ttu-id="3766b-438">**터치 입력을 사용 하 여 브러시 도구 선택**</span><span class="sxs-lookup"><span data-stu-id="3766b-438">**Brush tool selection with touchpad input**</span></span>

<span data-ttu-id="3766b-439">브러시 선택기 터치 패드의 누름된 입력을 감지 하면 왼쪽 이나 오른쪽으로 것인지 확인에 입력 될 내용의 위치를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-439">When the brush selector detects touchpad's pressed input, it checks the position of the input to determine if it was to the left or right.</span></span>

<span data-ttu-id="3766b-440">**SelectPressedAmount 사용 하 여 스트로크 두께**</span><span class="sxs-lookup"><span data-stu-id="3766b-440">**Stroke thickness with selectPressedAmount**</span></span>

<span data-ttu-id="3766b-441">대신 합니다 **InteractionSourcePressType.Select** 이벤트에는 **InteractionSourcePressed()** 를 통해 누름 양의 아날로그 가치를 얻을 수 **selectPressedAmount**.</span><span class="sxs-lookup"><span data-stu-id="3766b-441">Instead of the **InteractionSourcePressType.Select** event in the **InteractionSourcePressed()**, you can get the analog value of the pressed amount through **selectPressedAmount**.</span></span> <span data-ttu-id="3766b-442">이 값을 검색할 수 있습니다 **InteractionSourceUpdated()** 합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-442">This value can be retrieved in **InteractionSourceUpdated()**.</span></span>

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

<span data-ttu-id="3766b-443">**지우개 스크립트**</span><span class="sxs-lookup"><span data-stu-id="3766b-443">**Eraser script**</span></span>

<span data-ttu-id="3766b-444">**지우개** 는 특수 한 유형의 기본 재정의 하는 브러시 **브러시**의 **DrawOverTime()** 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-444">**Eraser** is a special type of brush that overrides the base **Brush**'s **DrawOverTime()** function.</span></span> <span data-ttu-id="3766b-445">그리기 참이 면이 지우개 모든 기존 브러시 스트로크를 사용 하 여 해당 팁과 교차 하는 경우를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-445">While Draw is true, the eraser checks to see if its tip intersects with any existing brush strokes.</span></span> <span data-ttu-id="3766b-446">이 경우 아래로 축소 됩니다 큐에 추가 되며 삭제.</span><span class="sxs-lookup"><span data-stu-id="3766b-446">If it does, they are added to a queue to be shrunk down and deleted.</span></span>

## <a name="advanced-design---teleportation-and-locomotion"></a><span data-ttu-id="3766b-447">고급 디자인-텔레포트 및 locomotion</span><span class="sxs-lookup"><span data-stu-id="3766b-447">Advanced design - Teleportation and locomotion</span></span>

<span data-ttu-id="3766b-448">장면 텔레포트 엄지 스틱을 사용 하 여를 사용 하 여 이동, 사용 하 여 사용자를 허용 하려는 경우 **MixedRealityCameraParent** of **MixedRealityCamera**합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-448">If you want to allow the user to move around the scene with teleportation using thumbstick, use **MixedRealityCameraParent** instead of **MixedRealityCamera**.</span></span> <span data-ttu-id="3766b-449">추가 해야 **InputManager** 하 고 **DefaultCusor**합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-449">You also need to add **InputManager** and **DefaultCusor**.</span></span> <span data-ttu-id="3766b-450">이후 **MixedRealityCameraParent** 이미 포함 되어 **MotionControllers** 하 고 **경계** 으로 자식 구성 요소를 제거 해야 기존  **MotionControllers** 하 고 **환경** prefab 합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-450">Since **MixedRealityCameraParent** already includes **MotionControllers** and **Boundary** as child components, you should remove existing **MotionControllers** and **Environment** prefab.</span></span>

### <a name="instructions"></a><span data-ttu-id="3766b-451">지침</span><span class="sxs-lookup"><span data-stu-id="3766b-451">Instructions</span></span>

* <span data-ttu-id="3766b-452">에 **계층 구조** 패널에서 삭제 **MixedRealityCamera**에 **환경** 및 **MotionControllers**</span><span class="sxs-lookup"><span data-stu-id="3766b-452">In the **Hierarchy** panel, delete **MixedRealityCamera**, **Environment** and **MotionControllers**</span></span>
* <span data-ttu-id="3766b-453">**프로젝트 패널**를 검색 하 고 끌어에 다음 prefabs 합니다 **계층** 패널:</span><span class="sxs-lookup"><span data-stu-id="3766b-453">From the **Project panel**, search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="3766b-454">Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**</span><span class="sxs-lookup"><span data-stu-id="3766b-454">Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**</span></span>
    * <span data-ttu-id="3766b-455">Assets/AppPrefabs/Input/Prefabs/**InputManager**</span><span class="sxs-lookup"><span data-stu-id="3766b-455">Assets/AppPrefabs/Input/Prefabs/**InputManager**</span></span>
    * <span data-ttu-id="3766b-456">Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**</span><span class="sxs-lookup"><span data-stu-id="3766b-456">Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**</span></span>

![혼합된 현실 카메라 부모](images/mr213-cameraparent-300px.png)
* <span data-ttu-id="3766b-458">에 **계층 구조** 패널에서 **입력 관리자**</span><span class="sxs-lookup"><span data-stu-id="3766b-458">In the **Hierarchy** panel, click **Input Manager**</span></span>
* <span data-ttu-id="3766b-459">에 **검사기** 패널에서 아래로 스크롤하여 합니다 **간단한 단일 포인터 선택기** 섹션</span><span class="sxs-lookup"><span data-stu-id="3766b-459">In the **Inspector** panel, scroll down to the **Simple Single Pointer Selector** section</span></span>
* <span data-ttu-id="3766b-460">**계층 구조** 패널에서 끌어 **DefaultCursor** 에 **커서** 필드</span><span class="sxs-lookup"><span data-stu-id="3766b-460">From the **Hierarchy** panel, drag **DefaultCursor** into **Cursor** field</span></span>

![기본 커서를 할당합니다.](images/mr213-defaultcursor-500px.png)
* <span data-ttu-id="3766b-462">**저장할** 장면과 클릭 합니다 **재생** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-462">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="3766b-463">왼쪽/오른쪽 또는 텔레포트 회전 하려면 스틱을 사용할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-463">You will be able to use the thumbstick to rotate left/right or teleport.</span></span>

## <a name="the-end"></a><span data-ttu-id="3766b-464">끝</span><span class="sxs-lookup"><span data-stu-id="3766b-464">The end</span></span>

<span data-ttu-id="3766b-465">및이 자습서의 끝입니다!</span><span class="sxs-lookup"><span data-stu-id="3766b-465">And that's the end of this tutorial!</span></span> <span data-ttu-id="3766b-466">알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-466">You learned:</span></span>
* <span data-ttu-id="3766b-467">Unity의 게임 모드와 런타임 동작 컨트롤러 모델을 사용 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-467">How to work with motion controller models in Unity's game mode and runtime.</span></span>
* <span data-ttu-id="3766b-468">다양 한 유형의 단추 이벤트 및 해당 응용 프로그램을 사용 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-468">How to use different types of button events and their applications.</span></span>
* <span data-ttu-id="3766b-469">컨트롤러를 기반으로 UI 요소를 오버레이 또는 완전히 사용자 지정 하는 방법.</span><span class="sxs-lookup"><span data-stu-id="3766b-469">How to overlay UI elements on top of the controller or fully customize it.</span></span>

<span data-ttu-id="3766b-470">이제 동작 컨트롤러를 사용 하 여 몰입 형 환경을 만들기 시작할 준비가 되었습니다!</span><span class="sxs-lookup"><span data-stu-id="3766b-470">You are now ready to start creating your own immersive experience with motion controllers!</span></span>

## <a name="completed-scenes"></a><span data-ttu-id="3766b-471">완료 된 장면</span><span class="sxs-lookup"><span data-stu-id="3766b-471">Completed scenes</span></span>

* <span data-ttu-id="3766b-472">Unity의 **프로젝트** 패널을 클릭 합니다 **장면** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-472">In Unity's **Project** panel click on the **Scenes** folder.</span></span>
* <span data-ttu-id="3766b-473">두 가지 Unity sceens 보면 **MixedReality213** 하 고 **MixedReality213Advanced**합니다.</span><span class="sxs-lookup"><span data-stu-id="3766b-473">You will find two Unity sceens **MixedReality213** and **MixedReality213Advanced**.</span></span>
    * <span data-ttu-id="3766b-474">**MixedReality213**: 단일 브러시를 사용 하 여 완료 된 장면</span><span class="sxs-lookup"><span data-stu-id="3766b-474">**MixedReality213**: Completed scene with single brush</span></span>
    * <span data-ttu-id="3766b-475">**MixedReality213Advanced**: 선택 단추를 누릅니다 시간 예제를 사용 하 여 여러 브러시를 사용 하 여 완료 된 장면</span><span class="sxs-lookup"><span data-stu-id="3766b-475">**MixedReality213Advanced**: Completed scene with multiple brush with select button's press amount example</span></span>

## <a name="see-also"></a><span data-ttu-id="3766b-476">참조</span><span class="sxs-lookup"><span data-stu-id="3766b-476">See also</span></span>

* [<span data-ttu-id="3766b-477">MR 입력 213 프로젝트 파일</span><span class="sxs-lookup"><span data-stu-id="3766b-477">MR Input 213 project files</span></span>](https://github.com/Microsoft/MixedReality213)
* [<span data-ttu-id="3766b-478">혼합된 현실 Toolkit-장면 동작 컨트롤러 테스트</span><span class="sxs-lookup"><span data-stu-id="3766b-478">Mixed Reality Toolkit - Motion Controller Test scene</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [<span data-ttu-id="3766b-479">혼합된 현실 도구 키트-잡기 메커니즘</span><span class="sxs-lookup"><span data-stu-id="3766b-479">Mixed Reality Toolkit - Grab Mechanics</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [<span data-ttu-id="3766b-480">동작 컨트롤러 개발 지침</span><span class="sxs-lookup"><span data-stu-id="3766b-480">Motion controller development guidelines</span></span>](motion-controllers.md)
