---
title: MR 210-응시 입력
description: Unity에서 Visual Studio 및 HoloLens를 사용 하 여 게이즈 개념의 자세한 연습을 코딩이 수행 합니다.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit mixedrealitytoolkit-unity academy, 자습서, 응시
ms.openlocfilehash: 076314389ec5ed70347c26d50c6a993f55da0758
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993553"
---
>[!NOTE]
><span data-ttu-id="634dc-104">혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="634dc-105">따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="634dc-106">이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="634dc-107">지원 되는 장치에서 작업을 계속 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="634dc-108">새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="634dc-109">게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-input-210-gaze"></a><span data-ttu-id="634dc-110">MR 입력 210: 응시</span><span class="sxs-lookup"><span data-stu-id="634dc-110">MR Input 210: Gaze</span></span>

<span data-ttu-id="634dc-111">[Gaze](gaze.md) 입력의 첫 번째 형태 이며 사용자의 의도 및 인식 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-111">[Gaze](gaze.md) is the first form of input and reveals the user's intent and awareness.</span></span> <span data-ttu-id="634dc-112">MR 입력 210 (즉, 프로젝트 탐색기)는 Windows Mixed Reality 게이즈 관련 개념에 자세히입니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-112">MR Input 210 (aka Project Explorer) is a deep dive into gaze-related concepts for Windows Mixed Reality.</span></span> <span data-ttu-id="634dc-113">추가할 컨텍스트 인식 커서 및 홀로그램, 사용자의 게이즈 알고 앱 활용 하 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-113">We will be adding contextual awareness to our cursor and holograms, taking full advantage of what your app knows about the user's gaze.</span></span>

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

<span data-ttu-id="634dc-114">필요가 친숙 한 고상한 여기 게이즈 개념을 배울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-114">We have a friendly astronaut here to help you learn gaze concepts.</span></span> <span data-ttu-id="634dc-115">[MR 기본 사항 101](holograms-101.md), 방금 사용자 게이즈를 준수 하는 단순 커서를 했습니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-115">In [MR Basics 101](holograms-101.md), we had a simple cursor that just followed your gaze.</span></span> <span data-ttu-id="634dc-116">지금 단순 커서 능가 하는 단계로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-116">Today we're moving a step beyond the simple cursor:</span></span>

* <span data-ttu-id="634dc-117">만들어진다는 것 커서 및 우리의 홀로그램 게이즈 인식: 둘 다 있는 사용자가 보는-사용자가에 따라 변경 됩니다 *되지* 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-117">We're making the cursor and our holograms gaze-aware: both will change based on where the user is looking - or where the user is *not* looking.</span></span> <span data-ttu-id="634dc-118">따라서 해당 컨텍스트를 인식 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-118">This makes them context-aware.</span></span>
* <span data-ttu-id="634dc-119">커서 및 홀로그램 대상으로 지정 되는 것에 더 많은 컨텍스트를 사용자에 게 피드백을 추가 하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-119">We will add feedback to our cursor and holograms to give the user more context on what is being targeted.</span></span> <span data-ttu-id="634dc-120">이 피드백은 오디오 visual 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-120">This feedback can be audio and visual.</span></span>
* <span data-ttu-id="634dc-121">보여드리겠습니다 타기 팅 방법 보다 작은 대상에 도달 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-121">We'll show you targeting techniques to help users hit smaller targets.</span></span>
* <span data-ttu-id="634dc-122">프로그램 홀로그램 방향 표시기를 사용 하 여 사용자의 주의 그리는 방법을 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-122">We'll show you how to draw the user's attention to your holograms with a directional indicator.</span></span>
* <span data-ttu-id="634dc-123">사용자 환경에서 이동 그녀에 따라 사용자를 사용 하 여 프로그램 홀로그램 수행할 방법 설명 하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-123">We'll teach you techniques to take your holograms with the user as she moves around in your world.</span></span>

>[!IMPORTANT]
><span data-ttu-id="634dc-124">각 아래 단원에 포함 된 비디오는 이전 버전의 Unity 및 혼합 현실 도구 키트를 사용 하 여 기록 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-124">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="634dc-125">단계별 지침을 정확 하 고 현재는, 스크립트 및 만료 된 해당 동영상의 시각적 개체를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-125">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="634dc-126">비디오는 두세요 포함 상태를 유지 및 개념 설명 하기 때문에 계속 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-126">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="634dc-127">장치 지원</span><span class="sxs-lookup"><span data-stu-id="634dc-127">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="634dc-128">과정</span><span class="sxs-lookup"><span data-stu-id="634dc-128">Course</span></span></th><th style="width:150px"> <span data-ttu-id="634dc-129"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="634dc-129"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="634dc-130"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="634dc-130"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="634dc-131">MR 입력 210: 응시</span><span class="sxs-lookup"><span data-stu-id="634dc-131">MR Input 210: Gaze</span></span></td><td style="text-align: center;"> <span data-ttu-id="634dc-132">✔️</span><span class="sxs-lookup"><span data-stu-id="634dc-132">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="634dc-133">✔️</span><span class="sxs-lookup"><span data-stu-id="634dc-133">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="634dc-134">시작하기 전 주의 사항</span><span class="sxs-lookup"><span data-stu-id="634dc-134">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="634dc-135">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="634dc-135">Prerequisites</span></span>

* <span data-ttu-id="634dc-136">올바른를 사용 하 여 구성 하는 Windows 10 PC [도구가 설치 되어](install-the-tools.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-136">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="634dc-137">기본적인 C# 기능을 프로그래밍 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-137">Some basic C# programming ability.</span></span>
* <span data-ttu-id="634dc-138">완료 해야 [MR 기본 사항 101](holograms-101.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-138">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="634dc-139">HoloLens 장치 [개발에 대해 구성 된](using-visual-studio.md#enabling-developer-mode)합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-139">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="634dc-140">프로젝트 파일</span><span class="sxs-lookup"><span data-stu-id="634dc-140">Project files</span></span>

* <span data-ttu-id="634dc-141">다운로드 합니다 [파일](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) 프로젝트에서 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-141">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) required by the project.</span></span><span data-ttu-id="634dc-142"> Unity 2017.2 이상이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-142"> Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="634dc-143">취소 보관 파일을 데스크톱 또는 기타 쉽게 달성할 수 있습니다 위치 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-143">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="634dc-144">을 다운로드 하기 전에 소스 코드를 확인 하려는 경우 있기 [GitHub에서 사용할 수 있는](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze)합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-144">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="634dc-145">오류 및 정보</span><span class="sxs-lookup"><span data-stu-id="634dc-145">Errata and Notes</span></span>

* <span data-ttu-id="634dc-146">Visual Studio에서 "내 코드만" 해야 사용 안 함 (선택 안 함된) 도구-> 옵션-> 디버깅 코드에서 중단점을 적중 하려면.</span><span class="sxs-lookup"><span data-stu-id="634dc-146">In Visual Studio, "Just My Code" needs to be disabled (unchecked) under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="634dc-147">1 장-Unity 설치</span><span class="sxs-lookup"><span data-stu-id="634dc-147">Chapter 1 - Unity Setup</span></span>

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a><span data-ttu-id="634dc-148">목표</span><span class="sxs-lookup"><span data-stu-id="634dc-148">Objectives</span></span>

* <span data-ttu-id="634dc-149">HoloLens 개발에 대 한 Unity를 최적화 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-149">Optimize Unity for HoloLens development.</span></span>
* <span data-ttu-id="634dc-150">자산을 가져오고 장면 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-150">Import assets and setup the scene.</span></span>
* <span data-ttu-id="634dc-151">에 HoloLens를 고상한을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-151">View the astronaut in the HoloLens.</span></span>

### <a name="instructions"></a><span data-ttu-id="634dc-152">지침</span><span class="sxs-lookup"><span data-stu-id="634dc-152">Instructions</span></span>

1. <span data-ttu-id="634dc-153">Unity를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-153">Start Unity.</span></span>
2. <span data-ttu-id="634dc-154">선택 **새 프로젝트**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-154">Select **New Project**.</span></span>
3. <span data-ttu-id="634dc-155">프로젝트 이름을 **ModelExplorer**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-155">Name the project **ModelExplorer**.</span></span>
4. <span data-ttu-id="634dc-156">위치를 입력 합니다 **Gaze** 폴더 되지 않은 보관 된 이전에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-156">Enter location as the **Gaze** folder you previously un-archived.</span></span>
5. <span data-ttu-id="634dc-157">프로젝트 설정 되어 있는지 확인 **3D**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-157">Make sure the project is set to **3D**.</span></span>
6. <span data-ttu-id="634dc-158">클릭 **프로젝트를 만들**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-158">Click **Create Project**.</span></span>

### <a name="unity-settings-for-hololens"></a><span data-ttu-id="634dc-159">HoloLens에 대 한 unity 설정</span><span class="sxs-lookup"><span data-stu-id="634dc-159">Unity settings for HoloLens</span></span>

<span data-ttu-id="634dc-160">Unity 내보내기 하려는 앱을 만들어야 알 수 있도록 해야는 [몰입 형 뷰](app-views.md) 2D 보기 대신 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-160">We need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="634dc-161">가상 현실 장치로 HoloLens 추가 여는 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-161">We do that by adding HoloLens as a virtual reality device.</span></span>

1. <span data-ttu-id="634dc-162">로 이동 **편집 > 프로젝트 설정 > 플레이어**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-162">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="634dc-163">에 **검사기 패널** 플레이어 설정에 대 한 선택 합니다 **Windows 스토어** 아이콘입니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-163">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="634dc-164">확장 된 **xr 하이 설정을** 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-164">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="634dc-165">에 **렌더링** 섹션을 **가상 현실 지원** 새 추가 하려면이 확인란을 **가상 현실 Sdk** 목록.</span><span class="sxs-lookup"><span data-stu-id="634dc-165">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="634dc-166">확인 **Windows Mixed Reality** 목록에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-166">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="634dc-167">그렇지 않은 경우 선택 합니다 **+** 목록의 맨 아래에 있는 단추를 선택 **Windows Holographic**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-167">If not, select the **+** button at the bottom of the list and choose **Windows Holographic**.</span></span>

<span data-ttu-id="634dc-168">다음으로.net 스크립팅 백 엔드를 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-168">Next, we need to set our scripting backend to .NET.</span></span>

1. <span data-ttu-id="634dc-169">로 이동 **편집 > 프로젝트 설정 > 플레이어** (될 수 있습니다이 이전 단계에서).</span><span class="sxs-lookup"><span data-stu-id="634dc-169">Go to **Edit > Project Settings > Player** (you may still have this up from the previous step).</span></span>
2. <span data-ttu-id="634dc-170">에 **검사기 패널** 플레이어 설정에 대 한 선택 합니다 **Windows 스토어** 아이콘입니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-170">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="634dc-171">에 **기타 설정** 구성 섹션, 했는지 **스크립팅 백 엔드** 로 설정 된 **.NET**</span><span class="sxs-lookup"><span data-stu-id="634dc-171">In the **Other Settings** Configuration section, make sure that **Scripting Backend** is set to **.NET**</span></span>

<span data-ttu-id="634dc-172">마지막으로, HoloLens에 빠른 성능을 달성 하기 위해 우리의 품질 설정을 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-172">Finally, we'll update our quality settings to achieve a fast performance on HoloLens.</span></span>

1. <span data-ttu-id="634dc-173">로 이동 **편집 > 프로젝트 설정 > 품질**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-173">Go to **Edit > Project Settings > Quality**.</span></span>
2. <span data-ttu-id="634dc-174">아래쪽 화살표를 클릭 합니다 **기본** Windows 스토어 아이콘 아래에 있는 행입니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-174">Click on downward pointing arrow in the **Default** row under the Windows Store icon.</span></span>
3. <span data-ttu-id="634dc-175">선택 **매우 낮은** 에 대 한 **Windows 스토어 앱**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-175">Select **Very Low** for **Windows Store Apps**.</span></span>

### <a name="import-project-assets"></a><span data-ttu-id="634dc-176">프로젝트 자산 가져오기</span><span class="sxs-lookup"><span data-stu-id="634dc-176">Import project assets</span></span>

1. <span data-ttu-id="634dc-177">마우스 오른쪽 단추로 클릭 합니다 **자산** 폴더에는 **프로젝트** 패널입니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-177">Right click the **Assets** folder in the **Project** panel.</span></span>
2. <span data-ttu-id="634dc-178">클릭할 **패키지를 가져올 > 사용자 지정 패키지**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-178">Click on **Import Package > Custom Package**.</span></span>
3. <span data-ttu-id="634dc-179">다운로드 한 프로젝트 파일을 이동 하 고 클릭 **ModelExplorer.unitypackage**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-179">Navigate to the project files you downloaded and click on **ModelExplorer.unitypackage**.</span></span>
4. <span data-ttu-id="634dc-180">**열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-180">Click **Open**.</span></span>
5. <span data-ttu-id="634dc-181">패키지를 로드 한 후 클릭 합니다 **가져오기** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-181">After the package loads, click on the **Import** button.</span></span>

### <a name="setup-the-scene"></a><span data-ttu-id="634dc-182">장면 설치</span><span class="sxs-lookup"><span data-stu-id="634dc-182">Setup the scene</span></span>

1. <span data-ttu-id="634dc-183">계층 구조에서 삭제 합니다 **주 카메라**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-183">In the Hierarchy, delete the **Main Camera**.</span></span>
2. <span data-ttu-id="634dc-184">에 **HoloToolkit** 폴더를 열고 합니다 **입력** 폴더를 엽니다를 **Prefabs** 폴더.</span><span class="sxs-lookup"><span data-stu-id="634dc-184">In the **HoloToolkit** folder, open the **Input** folder, then open the **Prefabs** folder.</span></span>
3. <span data-ttu-id="634dc-185">끌어서 놓기 합니다 **MixedRealityCameraParent** 에서 prefab 합니다 **Prefabs** 폴더를 **계층**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-185">Drag and drop the **MixedRealityCameraParent** prefab from the **Prefabs** folder into the **Hierarchy**.</span></span>
4. <span data-ttu-id="634dc-186">마우스 오른쪽 단추로 클릭 합니다 **Directional Light** 계층 및 선택 **삭제**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-186">Right-click the **Directional Light** in the Hierarchy and select **Delete**.</span></span>
5. <span data-ttu-id="634dc-187">에 **홀로그램** 폴더를 끌어서의 루트에 다음 자산을 삭제 합니다 **계층**:</span><span class="sxs-lookup"><span data-stu-id="634dc-187">In the **Holograms** folder, drag and drop the following assets into the root of the **Hierarchy**:</span></span>
    * <span data-ttu-id="634dc-188">**AstroMan**</span><span class="sxs-lookup"><span data-stu-id="634dc-188">**AstroMan**</span></span>
    * <span data-ttu-id="634dc-189">**광원**</span><span class="sxs-lookup"><span data-stu-id="634dc-189">**Lights**</span></span>
    * <span data-ttu-id="634dc-190">**SpaceAudioSource**</span><span class="sxs-lookup"><span data-stu-id="634dc-190">**SpaceAudioSource**</span></span>
    * <span data-ttu-id="634dc-191">**SpaceBackground**</span><span class="sxs-lookup"><span data-stu-id="634dc-191">**SpaceBackground**</span></span>
6. <span data-ttu-id="634dc-192">시작 **재생 모드** ▶ 고상한을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-192">Start **Play Mode** ▶ to view the astronaut.</span></span>
7. <span data-ttu-id="634dc-193">클릭 **재생 모드** 를 다시 ▶ **중지**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-193">Click **Play Mode** ▶ again to **Stop**.</span></span>
8. <span data-ttu-id="634dc-194">에 **홀로그램** 폴더를 찾을 **Fitbox** 자산의 루트에 놓습니다 합니다 **계층**.</span><span class="sxs-lookup"><span data-stu-id="634dc-194">In the **Holograms** folder, find the **Fitbox** asset and drag it to the root of the **Hierarchy**.</span></span>
9. <span data-ttu-id="634dc-195">선택 된 **Fitbox** 에 **계층** 패널.</span><span class="sxs-lookup"><span data-stu-id="634dc-195">Select the **Fitbox** in the **Hierarchy** panel.</span></span>
10. <span data-ttu-id="634dc-196">끌어서를 **AstroMan** 컬렉션에서는 **계층** 에 **홀로그램 컬렉션** 에서 Fitbox 속성을 **검사기** 패널.</span><span class="sxs-lookup"><span data-stu-id="634dc-196">Drag the **AstroMan** collection from the **Hierarchy** to the **Hologram Collection** property of the Fitbox in the **Inspector** panel.</span></span>

### <a name="save-the-project"></a><span data-ttu-id="634dc-197">프로젝트를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-197">Save the project</span></span>

1. <span data-ttu-id="634dc-198">새 장면을 저장 합니다. **파일 >으로 장면 저장**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-198">Save the new scene: **File > Save Scene As**.</span></span>
2. <span data-ttu-id="634dc-199">클릭 **새 폴더** 는 폴더의 이름을 **장면**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-199">Click **New Folder** and name the folder **Scenes**.</span></span>
3. <span data-ttu-id="634dc-200">파일 이름을 "**ModelExplorer**"에 저장 된 **장면** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-200">Name the file “**ModelExplorer**” and save it in the **Scenes** folder.</span></span>

### <a name="build-the-project"></a><span data-ttu-id="634dc-201">프로젝트 빌드</span><span class="sxs-lookup"><span data-stu-id="634dc-201">Build the project</span></span>

1. <span data-ttu-id="634dc-202">Unity에서 선택 **파일 > 빌드 설정**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-202">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="634dc-203">클릭 **열기 장면 추가** 장면에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-203">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="634dc-204">선택 **유니버설 Windows 플랫폼** 에 **플랫폼** 클릭 **플랫폼 전환**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-204">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="634dc-205">HoloLens에 대 한 구체적으로 개발 하는 경우 설정 **대상 장치** 하 **HoloLens**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-205">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="634dc-206">그렇지 않으면 켜져 **모든 장치**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-206">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="634dc-207">확인 **빌드 형식** 로 설정 된 **D3D** 하 고 **SDK** 로 설정 되어 **가장 최근에 설치 된** (16299 또는 최신 SDK는 이어야 함).</span><span class="sxs-lookup"><span data-stu-id="634dc-207">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="634dc-208">**빌드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-208">Click **Build**.</span></span>
7. <span data-ttu-id="634dc-209">만들기는 **새 폴더** 이름을 "App"입니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-209">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="634dc-210">한 번 클릭 합니다 **앱** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-210">Single click the **App** folder.</span></span>
9. <span data-ttu-id="634dc-211">키를 눌러 **폴더 선택**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-211">Press **Select Folder**.</span></span>

<span data-ttu-id="634dc-212">Unity 완료 되 면 파일 탐색기 창이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-212">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="634dc-213">엽니다는 **앱** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-213">Open the **App** folder.</span></span>
2. <span data-ttu-id="634dc-214">엽니다는 **ModelExplorer Visual Studio 솔루션**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-214">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="634dc-215">HoloLens 배포 하는 경우:</span><span class="sxs-lookup"><span data-stu-id="634dc-215">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="634dc-216">에 디버그 대상 변경 맨 위의 도구 모음을 사용 하 여 Visual Studio에서 **릴리스** 들어오고를 ARM **x86**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-216">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="634dc-217">드롭다운 로컬 컴퓨터 단추 옆의 화살표를 클릭 하 고 선택 **원격 컴퓨터**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-217">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="634dc-218">입력 **HoloLens 장치 IP 주소** 인증 모드를 설정 하 고 **유니버설 (암호화 되지 않은 프로토콜)** 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-218">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="634dc-219">클릭 **선택**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-219">Click **Select**.</span></span> <span data-ttu-id="634dc-220">장치 IP 주소를 모르는 경우 찾는 위치 **설정 > 네트워크 및 인터넷 > 고급 옵션**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-220">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="634dc-221">맨 위 메뉴 모음에서 클릭 **디버그-> 디버깅 없이 시작** 누르거나 **ctrl+f5**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-221">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="634dc-222">처음으로 장치에 배포할 경우 해야 [Visual Studio를 사용 하 여 쌍](using-visual-studio.md#pairing-your-device-hololens)합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-222">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="634dc-223">앱에 배포 하는 경우 해제 합니다 **Fitbox** 사용 하 여를 **제스처 선택**.</span><span class="sxs-lookup"><span data-stu-id="634dc-223">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="634dc-224">경우는 몰입 형 헤드셋에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-224">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="634dc-225">에 디버그 대상 변경 맨 위의 도구 모음을 사용 하 여 Visual Studio에서 **릴리스** 들어오고를 ARM **x64**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-225">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="634dc-226">배포 대상 설정 되어 있는지 확인 **로컬 컴퓨터**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-226">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="634dc-227">맨 위 메뉴 모음에서 클릭 **디버그-> 디버깅 없이 시작** 누르거나 **ctrl+f5**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-227">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="634dc-228">앱에 배포 하는 경우 해제 합니다 **Fitbox** 동작 컨트롤러에서 트리거를 풀링 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-228">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

## <a name="chapter-2---cursor-and-target-feedback"></a><span data-ttu-id="634dc-229">2 장-커서 및 대상 피드백</span><span class="sxs-lookup"><span data-stu-id="634dc-229">Chapter 2 - Cursor and target feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a><span data-ttu-id="634dc-230">목표</span><span class="sxs-lookup"><span data-stu-id="634dc-230">Objectives</span></span>

* <span data-ttu-id="634dc-231">커서 시각적 디자인 및 동작 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-231">Cursor visual design and behavior.</span></span>
* <span data-ttu-id="634dc-232">피드백 커서 게이즈 기반입니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-232">Gaze-based cursor feedback.</span></span>
* <span data-ttu-id="634dc-233">홀로그램 게이즈 기반 피드백입니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-233">Gaze-based hologram feedback.</span></span>

<span data-ttu-id="634dc-234">기준 작업 몇 가지 커서 디자인 원칙 즉 하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-234">We're going to base our work on some cursor design principles, namely:</span></span>

* <span data-ttu-id="634dc-235">커서가 항상 존재 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-235">The cursor is always present.</span></span>
* <span data-ttu-id="634dc-236">너무 작은 또는 큰 커서를 허용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="634dc-236">Don't let the cursor get too small or big.</span></span>
* <span data-ttu-id="634dc-237">콘텐츠를 방해 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-237">Avoid obstructing content.</span></span>

### <a name="instructions"></a><span data-ttu-id="634dc-238">지침</span><span class="sxs-lookup"><span data-stu-id="634dc-238">Instructions</span></span>

1. <span data-ttu-id="634dc-239">에 **HoloToolkit\Input\Prefabs** 폴더를 찾기는 **InputManager** 자산입니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-239">In the **HoloToolkit\Input\Prefabs** folder, find the **InputManager** asset.</span></span>
2. <span data-ttu-id="634dc-240">끌어서 놓기 합니다 **InputManager** 에 **계층**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-240">Drag and drop the **InputManager** onto the **Hierarchy**.</span></span>
3. <span data-ttu-id="634dc-241">에 **HoloToolkit\Input\Prefabs** 폴더를 찾기는 **커서** 자산입니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-241">In the **HoloToolkit\Input\Prefabs** folder, find the **Cursor** asset.</span></span>
4. <span data-ttu-id="634dc-242">끌어서 놓기 합니다 **커서** 에 **계층**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-242">Drag and drop the **Cursor** onto the **Hierarchy**.</span></span>
5. <span data-ttu-id="634dc-243">선택 된 **InputManager** 개체를 **계층**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-243">Select the **InputManager** object in the **Hierarchy**.</span></span>
6. <span data-ttu-id="634dc-244">끌어서 합니다 **커서** 에서 개체를 **계층** InputManager의에 **SimpleSinglePointerSelector**의 **커서** 필드에 아래쪽의 **검사기**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-244">Drag the **Cursor** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>

![간단한 단일 포인터 선택기 설정](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a><span data-ttu-id="634dc-246">빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="634dc-246">Build and Deploy</span></span>

1. <span data-ttu-id="634dc-247">앱을 다시 빌드해야 **파일 > 빌드 설정**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-247">Rebuild the app from **File > Build Settings**.</span></span>
2. <span data-ttu-id="634dc-248">엽니다는 **앱 폴더**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-248">Open the **App folder**.</span></span>
3. <span data-ttu-id="634dc-249">엽니다는 **ModelExplorer Visual Studio 솔루션**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-249">Open the **ModelExplorer Visual Studio Solution**.</span></span>
4. <span data-ttu-id="634dc-250">클릭 **디버그-> 디버깅 없이 시작** 누르거나 **ctrl+f5**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-250">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
5. <span data-ttu-id="634dc-251">커서를 그리는 방법 및를 홀로그램 접촉 되어 해당 하는 경우 모양을 변경 하는 방법을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-251">Observe how the cursor is drawn, and how it changes appearance if it is touching a hologram.</span></span>

### <a name="instructions"></a><span data-ttu-id="634dc-252">지침</span><span class="sxs-lookup"><span data-stu-id="634dc-252">Instructions</span></span>

1. <span data-ttu-id="634dc-253">에 **계층** 패널을 확장 합니다 **AstroMan**->**GEO_G**->**Back_Center** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-253">In the **Hierarchy** panel, expand the **AstroMan**->**GEO_G**->**Back_Center** object.</span></span>
2. <span data-ttu-id="634dc-254">두 번 클릭 **Interactible.cs** Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-254">Double click on **Interactible.cs** to open it in Visual Studio.</span></span>
3. <span data-ttu-id="634dc-255">줄의 주석도 제거 합니다 **IFocusable.OnFocusEnter()** 하 고 **IFocusable.OnFocusExit()** 콜백을 **Interactible.cs**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-255">Uncomment the lines in the **IFocusable.OnFocusEnter()** and **IFocusable.OnFocusExit()** callbacks in **Interactible.cs**.</span></span> <span data-ttu-id="634dc-256">이러한 값은 포커스 (하거나 게이즈 컨트롤러 가리켜) 하 고 특정 GameObject collider를 끝낼 때 혼합 현실 도구 키트의 InputManager에 의해 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-256">These are called by the Mixed Reality Toolkit's InputManager when focus (either by gaze or by controller pointing) enters and exits the specific GameObject's collider.</span></span>

```cs
/* TODO: DEVELOPER CODING EXERCISE 2.d */

void IFocusable.OnFocusEnter()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to highlight the material when gaze enters.
        defaultMaterials[i].EnableKeyword("_ENVIRONMENT_COLORING");
    }
}

void IFocusable.OnFocusExit()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to remove highlight on material when gaze exits.
        defaultMaterials[i].DisableKeyword("_ENVIRONMENT_COLORING");
    }
}
```

>[!NOTE]
><span data-ttu-id="634dc-257">사용 하 여 `EnableKeyword` 고 `DisableKeyword` 위에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-257">We use `EnableKeyword` and `DisableKeyword` above.</span></span> <span data-ttu-id="634dc-258">확인 하기 위해 도구 키트의 표준 셰이더를 사용 하 여 사용자 고유의 앱에서 이러한 사용, 수행 해야 합니다 [스크립트를 통해 자료에 액세스 하기 위해 Unity 지침](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html)합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-258">In order to make use of these in your own app with the Toolkit's Standard shader, you'll need to follow the [Unity guidelines for accessing materials via script](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html).</span></span> <span data-ttu-id="634dc-259">이미 포함 되어이 예에서 합니다 [강조 표시 된 자료의 세 가지 변형 된](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) 리소스 폴더 (이름에 강조 표시를 사용 하 여 세 가지 자료 검색)에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-259">In this case, we've already included the [three variants of highlighted material](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) needed in the Resources folder (look for the three materials with highlight in the name).</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="634dc-260">빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="634dc-260">Build and Deploy</span></span>

1. <span data-ttu-id="634dc-261">이전과 마찬가지로 프로젝트를 빌드하고 HoloLens에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-261">As before, build the project and deploy to the HoloLens.</span></span>
2. <span data-ttu-id="634dc-262">개체는 게이즈는 대상으로 하는 경우 어떻게 되는지 관찰 하 고 있지 않은 경우.</span><span class="sxs-lookup"><span data-stu-id="634dc-262">Observe what happens when the gaze is aimed at an object and when it's not.</span></span>

## <a name="chapter-3---targeting-techniques"></a><span data-ttu-id="634dc-263">3 장-기술을 대상으로</span><span class="sxs-lookup"><span data-stu-id="634dc-263">Chapter 3 - Targeting Techniques</span></span>

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a><span data-ttu-id="634dc-264">목표</span><span class="sxs-lookup"><span data-stu-id="634dc-264">Objectives</span></span>

* <span data-ttu-id="634dc-265">대상 홀로그램 쉽게 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-265">Make it easier to target holograms.</span></span>
* <span data-ttu-id="634dc-266">자연 스러운 헤드 이동 안정화 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-266">Stabilize natural head movements.</span></span>

### <a name="instructions"></a><span data-ttu-id="634dc-267">지침</span><span class="sxs-lookup"><span data-stu-id="634dc-267">Instructions</span></span>

1. <span data-ttu-id="634dc-268">에 **계층** 패널을 선택 합니다 **InputManager** 개체.</span><span class="sxs-lookup"><span data-stu-id="634dc-268">In the **Hierarchy** panel, select the **InputManager** object.</span></span>
2. <span data-ttu-id="634dc-269">에 **검사기** 패널에서 찾을 합니다 **Gaze 안정기** 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-269">In the **Inspector** panel, find the **Gaze Stabilizer** script.</span></span> <span data-ttu-id="634dc-270">확인 하려는 경우 클릭 하 여 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-270">Click it to open in Visual Studio, if you want to take a look.</span></span>
    * <span data-ttu-id="634dc-271">이 스크립트는 Raycast 데이터 샘플을 반복 하 고 전체 자릿수를 대상으로 하는 사용자의 게이즈를 안정화 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-271">This script iterates over samples of Raycast data and helps stabilize the user's gaze for precision targeting.</span></span>
3. <span data-ttu-id="634dc-272">에 **검사기**, 편집할 수 있습니다 합니다 **안정성 샘플 저장** 값입니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-272">In the **Inspector**, you can edit the **Stored Stability Samples** value.</span></span> <span data-ttu-id="634dc-273">이 값은 안정기에 반복이 안정화 되 값을 계산 하는 샘플 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-273">This value represents the number of samples that the stabilizer iterates on to calculate the stabilized value.</span></span>

## <a name="chapter-4---directional-indicator"></a><span data-ttu-id="634dc-274">4 장-방향 표시기</span><span class="sxs-lookup"><span data-stu-id="634dc-274">Chapter 4 - Directional indicator</span></span>

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a><span data-ttu-id="634dc-275">목표</span><span class="sxs-lookup"><span data-stu-id="634dc-275">Objectives</span></span>

* <span data-ttu-id="634dc-276">홀로그램을 찾기 위해 커서에서 방향 표시기를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-276">Add a directional indicator on the cursor to help find holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="634dc-277">지침</span><span class="sxs-lookup"><span data-stu-id="634dc-277">Instructions</span></span>

<span data-ttu-id="634dc-278">사용 하려고 합니다 **DirectionIndicator.cs** 될 파일:</span><span class="sxs-lookup"><span data-stu-id="634dc-278">We're going to use the **DirectionIndicator.cs** file which will:</span></span>

1. <span data-ttu-id="634dc-279">사용자가를 홀로그램에서 gazing 되지 경우 방향 표시기를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-279">Show the directional indicator if the user is not gazing at the holograms.</span></span>
2. <span data-ttu-id="634dc-280">사용자가를 홀로그램에서 gazing 경우 방향 표시기를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-280">Hide the directional indicator if the user is gazing at the holograms.</span></span>
3. <span data-ttu-id="634dc-281">방향 표시기를 홀로그램을 가리키도록 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-281">Update the directional indicator to point to the holograms.</span></span>

<span data-ttu-id="634dc-282">그럼 시작해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-282">Let's get started.</span></span>

1. <span data-ttu-id="634dc-283">클릭 합니다 **AstroMan** 개체를 **계층** 패널 및 **화살표를 클릭** 하 여 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-283">Click on the **AstroMan** object in the **Hierarchy** panel and **click the arrow** to expand it.</span></span>
2. <span data-ttu-id="634dc-284">에 **계층** 패널을 선택 합니다 **DirectionalIndicator** 개체 아래 **AstroMan**.</span><span class="sxs-lookup"><span data-stu-id="634dc-284">In the **Hierarchy** panel, select the **DirectionalIndicator** object under **AstroMan**.</span></span>
3. <span data-ttu-id="634dc-285">에 **검사기** 패널에서 합니다 **구성 요소 추가** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-285">In the **Inspector** panel, click the **Add Component** button.</span></span>
4. <span data-ttu-id="634dc-286">메뉴에서 검색 상자에 입력 **방향 표시기**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-286">In the menu, type in the search box **Direction Indicator**.</span></span> <span data-ttu-id="634dc-287">검색 결과 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-287">Select the search result.</span></span>
5. <span data-ttu-id="634dc-288">에 **계층** 패널을 끌어서 놓아를 **커서** 개체를 **커서** 속성에는 **검사기**.</span><span class="sxs-lookup"><span data-stu-id="634dc-288">In the **Hierarchy** panel, drag and drop the **Cursor** object onto the **Cursor** property in the **Inspector**.</span></span>
6. <span data-ttu-id="634dc-289">에 **프로젝트** 패널의 **홀로그램** 폴더, 끌어서 놓기를 **DirectionalIndicator** 자산에는 **방향 표시기**의 속성을 **검사기**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-289">In the **Project** panel, in the **Holograms** folder, drag and drop the **DirectionalIndicator** asset onto the **Directional Indicator** property in the **Inspector**.</span></span>
7. <span data-ttu-id="634dc-290">앱 빌드 및 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-290">Build and deploy the app.</span></span>
8. <span data-ttu-id="634dc-291">방향 표시기 개체는 고상한을 찾을 수 있습니다 어떻게 시청 하세요.</span><span class="sxs-lookup"><span data-stu-id="634dc-291">Watch how the directional indicator object helps you find the astronaut.</span></span>

## <a name="chapter-5---billboarding"></a><span data-ttu-id="634dc-292">5 장-빌보드</span><span class="sxs-lookup"><span data-stu-id="634dc-292">Chapter 5 - Billboarding</span></span>

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a><span data-ttu-id="634dc-293">목표</span><span class="sxs-lookup"><span data-stu-id="634dc-293">Objectives</span></span>

* <span data-ttu-id="634dc-294">빌보드를 사용 하 여 홀로그램 항상 사용자 쪽에 직면 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-294">Use billboarding to have holograms always face towards you.</span></span>

<span data-ttu-id="634dc-295">사용 합니다 **Billboard.cs** 를 항상 사용자 향하도록 같은 지향 GameObject를 유지 하는 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-295">We will be using the **Billboard.cs** file to keep a GameObject oriented such that it is facing the user at all times.</span></span>

1. <span data-ttu-id="634dc-296">에 **계층** 패널을 선택 합니다 **AstroMan** 개체.</span><span class="sxs-lookup"><span data-stu-id="634dc-296">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
2. <span data-ttu-id="634dc-297">에 **검사기** 패널에서 합니다 **구성 요소 추가** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-297">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="634dc-298">메뉴에서 검색 상자에 입력 **빌보드**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-298">In the menu, type in the search box **Billboard**.</span></span> <span data-ttu-id="634dc-299">검색 결과 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-299">Select the search result.</span></span>
4. <span data-ttu-id="634dc-300">에 **검사기** 설정 합니다 **피벗 축** 에 **Y**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-300">In the **Inspector** set the **Pivot Axis** to **Y**.</span></span>
5. <span data-ttu-id="634dc-301">시도해 보세요.</span><span class="sxs-lookup"><span data-stu-id="634dc-301">Try it!</span></span> <span data-ttu-id="634dc-302">빌드 및 배포 하기 전에 해당 응용 프로그램.</span><span class="sxs-lookup"><span data-stu-id="634dc-302">Build and deploy the app as before.</span></span>
6. <span data-ttu-id="634dc-303">어떻게 빌보드 개체 얼굴 관점을 변경 하는 방법에 관계 없이 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="634dc-303">See how the Billboard object faces you no matter how you change the viewpoint.</span></span>
7. <span data-ttu-id="634dc-304">스크립트를 삭제 합니다 **AstroMan** 지금은 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-304">Delete the script from the **AstroMan** for now.</span></span>

## <a name="chapter-6---tag-along"></a><span data-ttu-id="634dc-305">6 장-Tag-Along</span><span class="sxs-lookup"><span data-stu-id="634dc-305">Chapter 6 - Tag-Along</span></span>

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a><span data-ttu-id="634dc-306">목표</span><span class="sxs-lookup"><span data-stu-id="634dc-306">Objectives</span></span>

* <span data-ttu-id="634dc-307">Tag-Along 전시실 팔 로우 하 여 홀로그램을 사용 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-307">Use Tag-Along to have our holograms follow us around the room.</span></span>

<span data-ttu-id="634dc-308">이 문제에 작업을에서는 다음 디자인 제약 조건으로 안내 됩니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-308">As we work on this issue, we'll be guided by the following design constraints:</span></span>

* <span data-ttu-id="634dc-309">콘텐츠 항상 있어야 한눈에 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-309">Content should always be a glance away.</span></span>
* <span data-ttu-id="634dc-310">콘텐츠 방식에서 아니어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-310">Content should not be in the way.</span></span>
* <span data-ttu-id="634dc-311">콘텐츠 헤드 잠금 편리 하 게 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-311">Head-locking content is uncomfortable.</span></span>

<span data-ttu-id="634dc-312">여기에 솔루션 "tag-along" 접근 방식을 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-312">The solution used here is to use a "tag-along" approach.</span></span>

<span data-ttu-id="634dc-313">Tag-along 개체를 완전히 사용자 보기를 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-313">A tag-along object never fully leaves the user's view.</span></span> <span data-ttu-id="634dc-314">생각할 수 있습니다는 개체와 tag-along 고무 밴드에서 사용자의 머리글에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-314">You can think of the a tag-along as being an object attached to the user's head by rubber bands.</span></span> <span data-ttu-id="634dc-315">사용자가이 완전히 종료 하지 않고 보기의 모서리 쪽으로 이동 하 여 콘텐츠를 쉽게 보기 내에서 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-315">As the user moves, the content will stay within an easy glance by sliding towards the edge of the view without completely leaving.</span></span> <span data-ttu-id="634dc-316">사용자 gazes 향해 tag-along 개체, 경우 있어 자세히 보기로 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-316">When the user gazes towards the tag-along object, it comes more fully into view.</span></span>

<span data-ttu-id="634dc-317">사용 하려고 합니다 **SimpleTagalong.cs** 될 파일:</span><span class="sxs-lookup"><span data-stu-id="634dc-317">We're going to use the **SimpleTagalong.cs** file which will:</span></span>

1. <span data-ttu-id="634dc-318">카메라 범위 내에서 Tag-Along 개체 인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-318">Determine if the Tag-Along object is within the camera bounds.</span></span>
2. <span data-ttu-id="634dc-319">그렇지 않은 경우 하면 보기 프러스텀 내 하면 보기 프러스텀 부분적으로 내에 Tag-Along를 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-319">If not within the view frustum, position the Tag-Along to partially within the view frustum.</span></span>
3. <span data-ttu-id="634dc-320">이 고, 그렇지 사용자 로부터 Tag-Along 기본 거리를 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-320">Otherwise, position the Tag-Along to a default distance from the user.</span></span>

<span data-ttu-id="634dc-321">이렇게 하려면 먼저 변경 해야 합니다 **Interactible.cs** 스크립트를 호출 하는 **TagalongAction**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-321">To do this, we first must change the **Interactible.cs** script to call the **TagalongAction**.</span></span>

1. <span data-ttu-id="634dc-322">편집할 **Interactible.cs** 코딩을 완료 하 여 6.a (주석 처리 제거 줄 84를 87)를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-322">Edit **Interactible.cs** by completing coding exercise 6.a (uncommenting lines 84 to 87).</span></span>

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

<span data-ttu-id="634dc-323">합니다 **InteractibleAction.cs** 스크립트를 사용 하 여 쌍을 이루는 **Interactible.cs** 홀로그램에서 탭 사용자 지정 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-323">The **InteractibleAction.cs** script, paired with **Interactible.cs** performs custom actions when you tap on holograms.</span></span> <span data-ttu-id="634dc-324">이 경우 tag-along 맞게 하나를 사용 하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-324">In this case, we'll use one specifically for tag-along.</span></span>

* <span data-ttu-id="634dc-325">에 **스크립트** 폴더를 클릭 **TagalongAction.cs** 자산을 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-325">In the **Scripts** folder click on **TagalongAction.cs** asset to open in Visual Studio.</span></span>
* <span data-ttu-id="634dc-326">코딩 연습을 완료 하거나이 변경:</span><span class="sxs-lookup"><span data-stu-id="634dc-326">Complete the coding exercise or change it to this:</span></span>
  * <span data-ttu-id="634dc-327">맨 위에 있는 합니다 **계층**, 검색 표시줄 유형에 **ChestButton_Center** 결과 선택 하 고 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-327">At the top of the **Hierarchy**, in the search bar type **ChestButton_Center** and select the result.</span></span>
  * <span data-ttu-id="634dc-328">에 **검사기** 패널에서 합니다 **구성 요소 추가** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-328">In the **Inspector** panel, click the **Add Component** button.</span></span>
  * <span data-ttu-id="634dc-329">메뉴에서 검색 상자에 입력 **태그가 있는 작업**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-329">In the menu, type in the search box **Tagalong Action**.</span></span> <span data-ttu-id="634dc-330">검색 결과 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-330">Select the search result.</span></span>
  * <span data-ttu-id="634dc-331">**홀로그램** 폴더 찾기 합니다 **태그가 있는** 자산입니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-331">In **Holograms** folder find the **Tagalong** asset.</span></span>
  * <span data-ttu-id="634dc-332">선택 된 **ChestButton_Center** 개체를 **계층**합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-332">Select the **ChestButton_Center** object in the **Hierarchy**.</span></span> <span data-ttu-id="634dc-333">끌어서 놓기는 **태그가 있는** 에서 개체를 **프로젝트** 패널에 **검사기** 에 **개체에 태그가 있는** 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-333">Drag and drop the **TagAlong** object from the **Project** panel onto the **Inspector** into the **Object To Tagalong** property.</span></span>
  * <span data-ttu-id="634dc-334">끌어서 합니다 **태그가 있는 작업** 에서 개체를 **검사기** 에 **Interactible 작업** 필드에 **Interactible** 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-334">Drag the **Tagalong Action** object from the **Inspector** into the **Interactible Action** field on the **Interactible** script.</span></span>
* <span data-ttu-id="634dc-335">두 번 클릭 합니다 **TagalongAction** 스크립트 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-335">Double click the **TagalongAction** script to open it in Visual Studio.</span></span>

![Interactible 설정](images/holograms210-interactible.png)

<span data-ttu-id="634dc-337">다음을 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-337">We need to add the following:</span></span>

* <span data-ttu-id="634dc-338">PerformAction 함수 TagalongAction 스크립트 (InteractibleAction에서 상속)에 기능을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-338">Add functionality to the PerformAction function in the TagalongAction script (inherited from InteractibleAction).</span></span>
* <span data-ttu-id="634dc-339">빌보드 gazed 시 개체에 추가한 피벗 축의 XY로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-339">Add billboarding to the gazed-upon object, and set the pivot axis to XY.</span></span>
* <span data-ttu-id="634dc-340">개체에 간단한 Tag-Along를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-340">Then add simple Tag-Along to the object.</span></span>

<span data-ttu-id="634dc-341">솔루션을 다음과 같습니다 **TagalongAction.cs**:</span><span class="sxs-lookup"><span data-stu-id="634dc-341">Here's our solution, from **TagalongAction.cs**:</span></span>

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using HoloToolkit.Unity;
using UnityEngine;

public class TagalongAction : InteractibleAction
{
    [SerializeField]
    [Tooltip("Drag the Tagalong prefab asset you want to display.")]
    private GameObject objectToTagalong;

    private void Awake()
    {
        if (objectToTagalong != null)
        {
            objectToTagalong = Instantiate(objectToTagalong);
            objectToTagalong.SetActive(false);

            /* TODO: DEVELOPER CODING EXERCISE 6.b */

            // 6.b: AddComponent Billboard to objectToTagAlong,
            // so it's always facing the user as they move.
            Billboard billboard = objectToTagalong.AddComponent<Billboard>();

            // 6.b: AddComponent SimpleTagalong to objectToTagAlong,
            // so it's always following the user as they move.
            objectToTagalong.AddComponent<SimpleTagalong>();

            // 6.b: Set any public properties you wish to experiment with.
            billboard.PivotAxis = PivotAxis.XY; // Already the default, but provided in case you want to edit
        }
    }

    public override void PerformAction()
    {
        // Recommend having only one tagalong.
        if (objectToTagalong == null || objectToTagalong.activeSelf)
        {
            return;
        }

        objectToTagalong.SetActive(true);
    }
}
```

* <span data-ttu-id="634dc-342">시도해 보세요.</span><span class="sxs-lookup"><span data-stu-id="634dc-342">Try it!</span></span> <span data-ttu-id="634dc-343">앱 빌드 및 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-343">Build and deploy the app.</span></span>
* <span data-ttu-id="634dc-344">콘텐츠 게이즈 지점의 중앙을 따라가는 방법을 시청 하지만 지속적으로 하지 않고 차단 합니다.</span><span class="sxs-lookup"><span data-stu-id="634dc-344">Watch how the content follows the center of the gaze point, but not continuously and without blocking it.</span></span>
