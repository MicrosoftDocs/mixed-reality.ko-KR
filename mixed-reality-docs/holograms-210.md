---
title: MR 입력 210-응시
description: Unity, Visual Studio 및 HoloLens를 사용 하 여이 코딩 연습을 수행 하 여 응시 개념에 대 한 자세한 내용을 알아보세요.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit, 아카데미, 자습서, 응시
ms.openlocfilehash: 8608701a1dd0a9a20aede1737d16d5af2e715f6b
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434686"
---
>[!NOTE]
><span data-ttu-id="9ebb7-104">혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="9ebb7-105">따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="9ebb7-106">이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="9ebb7-107">지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="9ebb7-108">HoloLens 2에 대 한 [새로운 일련의 자습서](mrlearning-base.md) 가 게시 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

# <a name="mr-input-210-gaze"></a><span data-ttu-id="9ebb7-109">MR 입력 210: 응시</span><span class="sxs-lookup"><span data-stu-id="9ebb7-109">MR Input 210: Gaze</span></span>

<span data-ttu-id="9ebb7-110">[응시](gaze-and-commit.md) 는 첫 번째 입력 형태 이며 사용자의 의도 및 인식을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-110">[Gaze](gaze-and-commit.md) is the first form of input and reveals the user's intent and awareness.</span></span> <span data-ttu-id="9ebb7-111">MR 입력 210 (즉, 프로젝트 탐색기)은 Windows Mixed Reality의 응시 관련 개념을 자세히 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-111">MR Input 210 (aka Project Explorer) is a deep dive into gaze-related concepts for Windows Mixed Reality.</span></span> <span data-ttu-id="9ebb7-112">앱이 사용자의 응시에 대해 알고 있는 기능을 최대한 활용 하 여 커서 및 holograms에 상황별 인식을 추가할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-112">We will be adding contextual awareness to our cursor and holograms, taking full advantage of what your app knows about the user's gaze.</span></span>

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

<span data-ttu-id="9ebb7-113">여기에는 응시 개념을 배우는 데 도움이 되는 친숙 한 astronaut 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-113">We have a friendly astronaut here to help you learn gaze concepts.</span></span> <span data-ttu-id="9ebb7-114">[MR 기본 101](holograms-101.md)에는 방금 응시 한 간단한 커서가 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-114">In [MR Basics 101](holograms-101.md), we had a simple cursor that just followed your gaze.</span></span> <span data-ttu-id="9ebb7-115">지금은 간단한 커서를 넘어 단계를 이동 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-115">Today we're moving a step beyond the simple cursor:</span></span>

* <span data-ttu-id="9ebb7-116">커서와 holograms를 설정 하는 중입니다. 사용자가 찾고 있는 위치에 따라 또는 사용자가 찾고 *있지 않은* 위치에 따라 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-116">We're making the cursor and our holograms gaze-aware: both will change based on where the user is looking - or where the user is *not* looking.</span></span> <span data-ttu-id="9ebb7-117">이렇게 하면 컨텍스트를 인식 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-117">This makes them context-aware.</span></span>
* <span data-ttu-id="9ebb7-118">사용자에 게 대상에 대 한 추가 컨텍스트를 제공 하는 커서 및 holograms에 피드백을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-118">We will add feedback to our cursor and holograms to give the user more context on what is being targeted.</span></span> <span data-ttu-id="9ebb7-119">이 피드백은 오디오 및 시각적 개체 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-119">This feedback can be audio and visual.</span></span>
* <span data-ttu-id="9ebb7-120">사용자가 더 작은 대상에 도달 하는 데 도움이 되는 기술 대상을 보여 드리겠습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-120">We'll show you targeting techniques to help users hit smaller targets.</span></span>
* <span data-ttu-id="9ebb7-121">방향 표시기를 사용 하 여 holograms에 사용자의 주의를 그리는 방법을 보여 드리겠습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-121">We'll show you how to draw the user's attention to your holograms with a directional indicator.</span></span>
* <span data-ttu-id="9ebb7-122">전 세계에서 이동할 때 사용자와 holograms 하는 기술을 가르쳐 드리겠습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-122">We'll teach you techniques to take your holograms with the user as she moves around in your world.</span></span>

>[!IMPORTANT]
><span data-ttu-id="9ebb7-123">아래 각 장에 포함 된 비디오는 이전 버전의 Unity 및 혼합 현실 도구 키트를 사용 하 여 기록 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-123">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="9ebb7-124">단계별 지침은 정확 하 고 최신 상태 이지만 최신의 비디오에서 스크립트 및 시각적 개체를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-124">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="9ebb7-125">Posterity에 대 한 비디오는 포함 되어 있지만 적용 되는 개념은 그대로 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-125">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="9ebb7-126">장치 지원</span><span class="sxs-lookup"><span data-stu-id="9ebb7-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="9ebb7-127">과정</span><span class="sxs-lookup"><span data-stu-id="9ebb7-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="9ebb7-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="9ebb7-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="9ebb7-129"><a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="9ebb7-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="9ebb7-130">MR 입력 210: 응시</span><span class="sxs-lookup"><span data-stu-id="9ebb7-130">MR Input 210: Gaze</span></span></td><td style="text-align: center;"> <span data-ttu-id="9ebb7-131">✔️</span><span class="sxs-lookup"><span data-stu-id="9ebb7-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="9ebb7-132">✔️</span><span class="sxs-lookup"><span data-stu-id="9ebb7-132">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="9ebb7-133">시작하기 전 확인 사항</span><span class="sxs-lookup"><span data-stu-id="9ebb7-133">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="9ebb7-134">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="9ebb7-134">Prerequisites</span></span>

* <span data-ttu-id="9ebb7-135">올바른 [도구로](install-the-tools.md)구성 된 WINDOWS 10 PC입니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-135">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="9ebb7-136">몇 가지 C# 기본적인 프로그래밍 기능.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-136">Some basic C# programming ability.</span></span>
* <span data-ttu-id="9ebb7-137">[MR 기본 101](holograms-101.md)를 완료 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-137">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="9ebb7-138">[개발용으로 구성 된](using-visual-studio.md#enabling-developer-mode)HoloLens 장치입니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-138">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="9ebb7-139">프로젝트 파일</span><span class="sxs-lookup"><span data-stu-id="9ebb7-139">Project files</span></span>

* <span data-ttu-id="9ebb7-140">프로젝트에 필요한 [파일](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) 을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-140">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) required by the project.</span></span><span data-ttu-id="9ebb7-141"> Unity 2017.2 이상이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-141"> Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="9ebb7-142">바탕 화면 또는 기타 쉬운 위치에 파일을 보관 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-142">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="9ebb7-143">다운로드 하기 전에 소스 코드를 확인 하려는 경우 [GitHub에서 사용할 수](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze)있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-143">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="9ebb7-144">정오표 및 참고 사항</span><span class="sxs-lookup"><span data-stu-id="9ebb7-144">Errata and Notes</span></span>

* <span data-ttu-id="9ebb7-145">Visual Studio에서 코드의 중단점을 적중 하려면 도구-> 옵션-> 디버깅에서 "내 코드만"을 사용 하지 않도록 설정 (선택 취소) 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-145">In Visual Studio, "Just My Code" needs to be disabled (unchecked) under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="9ebb7-146">1 장-Unity 설치</span><span class="sxs-lookup"><span data-stu-id="9ebb7-146">Chapter 1 - Unity Setup</span></span>

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a><span data-ttu-id="9ebb7-147">목표</span><span class="sxs-lookup"><span data-stu-id="9ebb7-147">Objectives</span></span>

* <span data-ttu-id="9ebb7-148">HoloLens 개발을 위해 Unity를 최적화합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-148">Optimize Unity for HoloLens development.</span></span>
* <span data-ttu-id="9ebb7-149">자산을 가져오고 장면을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-149">Import assets and setup the scene.</span></span>
* <span data-ttu-id="9ebb7-150">HoloLens에서 astronaut를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-150">View the astronaut in the HoloLens.</span></span>

### <a name="instructions"></a><span data-ttu-id="9ebb7-151">지침</span><span class="sxs-lookup"><span data-stu-id="9ebb7-151">Instructions</span></span>

1. <span data-ttu-id="9ebb7-152">Unity를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-152">Start Unity.</span></span>
2. <span data-ttu-id="9ebb7-153">**새 프로젝트**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-153">Select **New Project**.</span></span>
3. <span data-ttu-id="9ebb7-154">프로젝트 이름을 **Modelexplorer**로 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-154">Name the project **ModelExplorer**.</span></span>
4. <span data-ttu-id="9ebb7-155">이전에 보관 하지 않은 **응시** 폴더로 위치를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-155">Enter location as the **Gaze** folder you previously un-archived.</span></span>
5. <span data-ttu-id="9ebb7-156">프로젝트가 **3D**로 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-156">Make sure the project is set to **3D**.</span></span>
6. <span data-ttu-id="9ebb7-157">**Create Project**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-157">Click **Create Project**.</span></span>

### <a name="unity-settings-for-hololens"></a><span data-ttu-id="9ebb7-158">HoloLens 용 Unity 설정</span><span class="sxs-lookup"><span data-stu-id="9ebb7-158">Unity settings for HoloLens</span></span>

<span data-ttu-id="9ebb7-159">내보내려는 앱이 2D 보기 대신 [몰입 형 보기](app-views.md) 를 만들어야 한다고 Unity에 알려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-159">We need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="9ebb7-160">HoloLens를 가상 현실 장치로 추가 하 여이 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-160">We do that by adding HoloLens as a virtual reality device.</span></span>

1. <span data-ttu-id="9ebb7-161">**편집 > 프로젝트 설정 > 플레이어**로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-161">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="9ebb7-162">플레이어 설정에 대 한 **검사기 패널** 에서 **Windows 스토어** 아이콘을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-162">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="9ebb7-163">**XR 설정** 그룹을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-163">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="9ebb7-164">**렌더링** 섹션에서 **가상 현실 지원 됨** 확인란을 선택 하 여 새 **가상 현실 sdk** 목록을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-164">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="9ebb7-165">**Windows Mixed Reality** 가 목록에 나타나는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-165">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="9ebb7-166">그렇지 않은 경우 목록 맨 아래에 있는 **+** 단추를 선택 하 고 **Windows Holographic**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-166">If not, select the **+** button at the bottom of the list and choose **Windows Holographic**.</span></span>

<span data-ttu-id="9ebb7-167">다음으로, scripting 백 엔드를 .NET으로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-167">Next, we need to set our scripting backend to .NET.</span></span>

1. <span data-ttu-id="9ebb7-168">**편집 > 프로젝트 설정 > 플레이어** 로 이동 합니다 (이전 단계에서이 작업을 계속 진행할 수 있음).</span><span class="sxs-lookup"><span data-stu-id="9ebb7-168">Go to **Edit > Project Settings > Player** (you may still have this up from the previous step).</span></span>
2. <span data-ttu-id="9ebb7-169">플레이어 설정에 대 한 **검사기 패널** 에서 **Windows 스토어** 아이콘을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-169">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="9ebb7-170">**기타 설정** 구성 섹션에서 **Scripting 백 엔드가** **.net** 으로 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-170">In the **Other Settings** Configuration section, make sure that **Scripting Backend** is set to **.NET**</span></span>

<span data-ttu-id="9ebb7-171">마지막으로, HoloLens에서 빠른 성능을 얻기 위해 품질 설정을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-171">Finally, we'll update our quality settings to achieve a fast performance on HoloLens.</span></span>

1. <span data-ttu-id="9ebb7-172">**편집 > 프로젝트 설정 > 품질**로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-172">Go to **Edit > Project Settings > Quality**.</span></span>
2. <span data-ttu-id="9ebb7-173">Windows 스토어 아이콘 아래의 **기본** 행에 있는 아래쪽 화살표를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-173">Click on downward pointing arrow in the **Default** row under the Windows Store icon.</span></span>
3. <span data-ttu-id="9ebb7-174">**Windows 스토어 앱**에 대해 **매우 낮음** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-174">Select **Very Low** for **Windows Store Apps**.</span></span>

### <a name="import-project-assets"></a><span data-ttu-id="9ebb7-175">프로젝트 자산 가져오기</span><span class="sxs-lookup"><span data-stu-id="9ebb7-175">Import project assets</span></span>

1. <span data-ttu-id="9ebb7-176">**프로젝트** 패널에서 **자산** 폴더를 마우스 오른쪽 단추로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-176">Right click the **Assets** folder in the **Project** panel.</span></span>
2. <span data-ttu-id="9ebb7-177">**패키지 가져오기 > 사용자 지정 패키지**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-177">Click on **Import Package > Custom Package**.</span></span>
3. <span data-ttu-id="9ebb7-178">다운로드 한 프로젝트 파일로 이동 하 고 **unitypackage**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-178">Navigate to the project files you downloaded and click on **ModelExplorer.unitypackage**.</span></span>
4. <span data-ttu-id="9ebb7-179">**열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-179">Click **Open**.</span></span>
5. <span data-ttu-id="9ebb7-180">패키지가 로드 되 면 **가져오기** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-180">After the package loads, click on the **Import** button.</span></span>

### <a name="setup-the-scene"></a><span data-ttu-id="9ebb7-181">장면 설정</span><span class="sxs-lookup"><span data-stu-id="9ebb7-181">Setup the scene</span></span>

1. <span data-ttu-id="9ebb7-182">계층에서 **주 카메라**를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-182">In the Hierarchy, delete the **Main Camera**.</span></span>
2. <span data-ttu-id="9ebb7-183">**HoloToolkit** 폴더에서 **입력** 폴더를 열고 **Prefabs** 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-183">In the **HoloToolkit** folder, open the **Input** folder, then open the **Prefabs** folder.</span></span>
3. <span data-ttu-id="9ebb7-184">**MixedRealityCameraParent** Prefab를 **Prefabs** 폴더에서 **계층**으로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-184">Drag and drop the **MixedRealityCameraParent** prefab from the **Prefabs** folder into the **Hierarchy**.</span></span>
4. <span data-ttu-id="9ebb7-185">계층에서 **방향 광원** 을 마우스 오른쪽 단추로 클릭 하 고 **삭제**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-185">Right-click the **Directional Light** in the Hierarchy and select **Delete**.</span></span>
5. <span data-ttu-id="9ebb7-186">**Holograms** 폴더에서 다음 자산을 **계층**의 루트에 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-186">In the **Holograms** folder, drag and drop the following assets into the root of the **Hierarchy**:</span></span>
    * <span data-ttu-id="9ebb7-187">**AstroMan**</span><span class="sxs-lookup"><span data-stu-id="9ebb7-187">**AstroMan**</span></span>
    * <span data-ttu-id="9ebb7-188">**조명을**</span><span class="sxs-lookup"><span data-stu-id="9ebb7-188">**Lights**</span></span>
    * <span data-ttu-id="9ebb7-189">**SpaceAudioSource**</span><span class="sxs-lookup"><span data-stu-id="9ebb7-189">**SpaceAudioSource**</span></span>
    * <span data-ttu-id="9ebb7-190">**SpaceBackground**</span><span class="sxs-lookup"><span data-stu-id="9ebb7-190">**SpaceBackground**</span></span>
6. <span data-ttu-id="9ebb7-191">**재생 모드** 를 시작 하 ▶ astronaut를 봅니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-191">Start **Play Mode** ▶ to view the astronaut.</span></span>
7. <span data-ttu-id="9ebb7-192">**재생 모드** ▶ 다시 클릭 하 여 **중지**합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-192">Click **Play Mode** ▶ again to **Stop**.</span></span>
8. <span data-ttu-id="9ebb7-193">**Holograms** 폴더에서 **fitbox** 자산을 찾아 **계층**의 루트로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-193">In the **Holograms** folder, find the **Fitbox** asset and drag it to the root of the **Hierarchy**.</span></span>
9. <span data-ttu-id="9ebb7-194">**계층** 패널에서 **fitbox** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-194">Select the **Fitbox** in the **Hierarchy** panel.</span></span>
10. <span data-ttu-id="9ebb7-195">**계층** 에서 **AstroMan** 컬렉션을 **검사기** 패널의 fitbox에 있는 **홀로그램 컬렉션** 속성으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-195">Drag the **AstroMan** collection from the **Hierarchy** to the **Hologram Collection** property of the Fitbox in the **Inspector** panel.</span></span>

### <a name="save-the-project"></a><span data-ttu-id="9ebb7-196">프로젝트를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-196">Save the project</span></span>

1. <span data-ttu-id="9ebb7-197">새 장면: 파일을 저장 하 **> 장면을 저장**합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-197">Save the new scene: **File > Save Scene As**.</span></span>
2. <span data-ttu-id="9ebb7-198">**새 폴더** 를 클릭 하 고 폴더 이름을 **장면**으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-198">Click **New Folder** and name the folder **Scenes**.</span></span>
3. <span data-ttu-id="9ebb7-199">파일 이름을 "**Modelexplorer**"로 하 고 해당 파일을 **백그라운드** 폴더에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-199">Name the file “**ModelExplorer**” and save it in the **Scenes** folder.</span></span>

### <a name="build-the-project"></a><span data-ttu-id="9ebb7-200">프로젝트 빌드</span><span class="sxs-lookup"><span data-stu-id="9ebb7-200">Build the project</span></span>

1. <span data-ttu-id="9ebb7-201">Unity에서 **파일 > 빌드 설정**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-201">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="9ebb7-202">열려 있는 장면 **추가** 를 클릭 하 여 장면을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-202">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="9ebb7-203">**플랫폼** 목록에서 **유니버설 Windows 플랫폼** 을 선택 하 고 **플랫폼 전환**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-203">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="9ebb7-204">특별히 HoloLens를 개발 하는 경우 **대상 장치** 를 **hololens**로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-204">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="9ebb7-205">그렇지 않으면 **모든 장치**에 그대로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-205">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="9ebb7-206">**빌드 형식이** **D3D** 로 설정 되 고 **sdk** 가 **최신 버전** 으로 설정 되어 있는지 확인 합니다 (sdk 16299 이상 이어야 함).</span><span class="sxs-lookup"><span data-stu-id="9ebb7-206">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="9ebb7-207">**빌드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-207">Click **Build**.</span></span>
7. <span data-ttu-id="9ebb7-208">"App" 이라는 **새 폴더** 를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-208">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="9ebb7-209">단일 **앱** 폴더를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-209">Single click the **App** folder.</span></span>
9. <span data-ttu-id="9ebb7-210">**폴더 선택**을 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-210">Press **Select Folder**.</span></span>

<span data-ttu-id="9ebb7-211">Unity가 완료 되 면 파일 탐색기 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-211">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="9ebb7-212">**앱** 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-212">Open the **App** folder.</span></span>
2. <span data-ttu-id="9ebb7-213">**모델 탐색기 Visual Studio 솔루션**을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-213">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="9ebb7-214">HoloLens에 배포 하는 경우:</span><span class="sxs-lookup"><span data-stu-id="9ebb7-214">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="9ebb7-215">Visual Studio의 맨 위 도구 모음을 사용 하 여 대상을 디버그에서 **릴리스** 로, ARM에서 **x 86**으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-215">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="9ebb7-216">로컬 컴퓨터 단추 옆에 있는 드롭다운 화살표를 클릭 하 고 **원격 컴퓨터**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-216">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="9ebb7-217">**HoloLens 장치 IP 주소** 를 입력 하 고 인증 모드를 **유니버설 (암호화 되지 않은 프로토콜)** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-217">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="9ebb7-218">**선택**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-218">Click **Select**.</span></span> <span data-ttu-id="9ebb7-219">장치 IP 주소를 모르는 경우 **네트워크 & 인터넷 > 고급 옵션 > 설정**을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-219">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="9ebb7-220">상단 메뉴 모음에서 **디버그-> 디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-220">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="9ebb7-221">처음으로 장치에 배포 하는 경우에는 [Visual Studio와 쌍](using-visual-studio.md#pairing-your-device)으로 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-221">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device).</span></span>
5. <span data-ttu-id="9ebb7-222">앱이 배포 되 면 **선택 제스처로** **fitbox** 를 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-222">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="9ebb7-223">모던 헤드셋에 배포 하는 경우:</span><span class="sxs-lookup"><span data-stu-id="9ebb7-223">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="9ebb7-224">Visual Studio의 맨 위 도구 모음을 사용 하 여 대상을 디버그에서 **릴리스** 로, ARM에서 x **64**로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-224">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="9ebb7-225">배포 대상이 **로컬 컴퓨터**로 설정 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-225">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="9ebb7-226">상단 메뉴 모음에서 **디버그-> 디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-226">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="9ebb7-227">앱이 배포 되 면 동작 컨트롤러에서 트리거를 당겨 **Fitbox** 를 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-227">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

## <a name="chapter-2---cursor-and-target-feedback"></a><span data-ttu-id="9ebb7-228">2 장-커서 및 대상 피드백</span><span class="sxs-lookup"><span data-stu-id="9ebb7-228">Chapter 2 - Cursor and target feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a><span data-ttu-id="9ebb7-229">목표</span><span class="sxs-lookup"><span data-stu-id="9ebb7-229">Objectives</span></span>

* <span data-ttu-id="9ebb7-230">커서 비주얼 디자인 및 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-230">Cursor visual design and behavior.</span></span>
* <span data-ttu-id="9ebb7-231">응시 기반 커서 피드백입니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-231">Gaze-based cursor feedback.</span></span>
* <span data-ttu-id="9ebb7-232">응시 기반 홀로그램 피드백입니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-232">Gaze-based hologram feedback.</span></span>

<span data-ttu-id="9ebb7-233">다음은 몇 가지 커서 디자인 원칙에 대 한 작업의 기반입니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-233">We're going to base our work on some cursor design principles, namely:</span></span>

* <span data-ttu-id="9ebb7-234">커서는 항상 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-234">The cursor is always present.</span></span>
* <span data-ttu-id="9ebb7-235">커서를 너무 작거나 크게 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-235">Don't let the cursor get too small or big.</span></span>
* <span data-ttu-id="9ebb7-236">방해 하지 않는지 콘텐츠를 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-236">Avoid obstructing content.</span></span>

### <a name="instructions"></a><span data-ttu-id="9ebb7-237">지침</span><span class="sxs-lookup"><span data-stu-id="9ebb7-237">Instructions</span></span>

1. <span data-ttu-id="9ebb7-238">**HoloToolkit\Input\Prefabs** 폴더에서 **inputmanager** 자산을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-238">In the **HoloToolkit\Input\Prefabs** folder, find the **InputManager** asset.</span></span>
2. <span data-ttu-id="9ebb7-239">**Inputmanager** 를 **계층 구조**에 끌어다 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-239">Drag and drop the **InputManager** onto the **Hierarchy**.</span></span>
3. <span data-ttu-id="9ebb7-240">**HoloToolkit\Input\Prefabs** 폴더에서 **커서** 자산을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-240">In the **HoloToolkit\Input\Prefabs** folder, find the **Cursor** asset.</span></span>
4. <span data-ttu-id="9ebb7-241">**커서** 를 **계층**으로 끌어다 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-241">Drag and drop the **Cursor** onto the **Hierarchy**.</span></span>
5. <span data-ttu-id="9ebb7-242">**계층**에서 **inputmanager** 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-242">Select the **InputManager** object in the **Hierarchy**.</span></span>
6. <span data-ttu-id="9ebb7-243">**계층** 의 **커서** 개체를 **검사기**의 맨 아래에 있는 Inputmanager의 **simplesinglepointerselector**필드로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-243">Drag the **Cursor** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>

![간단한 단일 포인터 선택기 설정](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a><span data-ttu-id="9ebb7-245">빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="9ebb7-245">Build and Deploy</span></span>

1. <span data-ttu-id="9ebb7-246">**빌드 설정 > 파일**에서 응용 프로그램을 다시 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-246">Rebuild the app from **File > Build Settings**.</span></span>
2. <span data-ttu-id="9ebb7-247">**앱 폴더**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-247">Open the **App folder**.</span></span>
3. <span data-ttu-id="9ebb7-248">**모델 탐색기 Visual Studio 솔루션**을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-248">Open the **ModelExplorer Visual Studio Solution**.</span></span>
4. <span data-ttu-id="9ebb7-249">**디버그를 클릭 하 > 디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-249">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
5. <span data-ttu-id="9ebb7-250">커서를 그리는 방법 및 홀로그램을 터치 하는 경우 모양이 어떻게 변경 되는지 관찰 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-250">Observe how the cursor is drawn, and how it changes appearance if it is touching a hologram.</span></span>

### <a name="instructions"></a><span data-ttu-id="9ebb7-251">지침</span><span class="sxs-lookup"><span data-stu-id="9ebb7-251">Instructions</span></span>

1. <span data-ttu-id="9ebb7-252">**계층** 패널에서 **AstroMan**->**GEO_G**->**Back_Center** 개체를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-252">In the **Hierarchy** panel, expand the **AstroMan**->**GEO_G**->**Back_Center** object.</span></span>
2. <span data-ttu-id="9ebb7-253">**Interactible.cs** 를 두 번 클릭 하 여 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-253">Double click on **Interactible.cs** to open it in Visual Studio.</span></span>
3. <span data-ttu-id="9ebb7-254">**Interactible.cs**의 **OnFocusEnter ()** 및 **OnFocusExit ()** 콜백에서 줄의 주석 처리를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-254">Uncomment the lines in the **IFocusable.OnFocusEnter()** and **IFocusable.OnFocusExit()** callbacks in **Interactible.cs**.</span></span> <span data-ttu-id="9ebb7-255">이는 포커스 (응시 또는 컨트롤러 포인팅)가 특정 GameObject의 collider를 입력 하 고 종료 하는 경우 Mixed Reality Toolkit의 InputManager에서 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-255">These are called by the Mixed Reality Toolkit's InputManager when focus (either by gaze or by controller pointing) enters and exits the specific GameObject's collider.</span></span>

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
><span data-ttu-id="9ebb7-256">`EnableKeyword`와 `DisableKeyword`를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-256">We use `EnableKeyword` and `DisableKeyword` above.</span></span> <span data-ttu-id="9ebb7-257">Toolkit의 표준 셰이더를 사용 하 여 자신의 앱에서 이러한 기능을 활용 하려면 [스크립트를 통해 자료에 액세스 하기 위한 Unity 지침](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html)을 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-257">In order to make use of these in your own app with the Toolkit's Standard shader, you'll need to follow the [Unity guidelines for accessing materials via script](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html).</span></span> <span data-ttu-id="9ebb7-258">이 경우 Resources 폴더에 필요한 [강조 표시 된 자료의 세 가지 변형이](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) 이미 포함 되어 있습니다 (이름에 강조 표시 된 세 가지 자료 참조).</span><span class="sxs-lookup"><span data-stu-id="9ebb7-258">In this case, we've already included the [three variants of highlighted material](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) needed in the Resources folder (look for the three materials with highlight in the name).</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="9ebb7-259">빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="9ebb7-259">Build and Deploy</span></span>

1. <span data-ttu-id="9ebb7-260">이전과 마찬가지로 프로젝트를 빌드하고 HoloLens에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-260">As before, build the project and deploy to the HoloLens.</span></span>
2. <span data-ttu-id="9ebb7-261">응시가 개체를 목표로 하 고 있지 않을 때 발생 하는 상황을 관찰 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-261">Observe what happens when the gaze is aimed at an object and when it's not.</span></span>

## <a name="chapter-3---targeting-techniques"></a><span data-ttu-id="9ebb7-262">3 장-대상 지정 기술</span><span class="sxs-lookup"><span data-stu-id="9ebb7-262">Chapter 3 - Targeting Techniques</span></span>

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a><span data-ttu-id="9ebb7-263">목표</span><span class="sxs-lookup"><span data-stu-id="9ebb7-263">Objectives</span></span>

* <span data-ttu-id="9ebb7-264">Holograms을 더 쉽게 대상으로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-264">Make it easier to target holograms.</span></span>
* <span data-ttu-id="9ebb7-265">안정화 자연 헤드 이동.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-265">Stabilize natural head movements.</span></span>

### <a name="instructions"></a><span data-ttu-id="9ebb7-266">지침</span><span class="sxs-lookup"><span data-stu-id="9ebb7-266">Instructions</span></span>

1. <span data-ttu-id="9ebb7-267">**계층** 패널에서 **inputmanager** 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-267">In the **Hierarchy** panel, select the **InputManager** object.</span></span>
2. <span data-ttu-id="9ebb7-268">**검사기** 패널에서 **응시 안정기** 스크립트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-268">In the **Inspector** panel, find the **Gaze Stabilizer** script.</span></span> <span data-ttu-id="9ebb7-269">원하는 경우 클릭 하 여 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-269">Click it to open in Visual Studio, if you want to take a look.</span></span>
    * <span data-ttu-id="9ebb7-270">이 스크립트는 Raycast 데이터의 샘플을 반복 하 고 사용자가 전체 자릿수를 대상으로 하는 응시를 안정화 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-270">This script iterates over samples of Raycast data and helps stabilize the user's gaze for precision targeting.</span></span>
3. <span data-ttu-id="9ebb7-271">**검사기**에서 **저장 된 안정성 샘플** 값을 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-271">In the **Inspector**, you can edit the **Stored Stability Samples** value.</span></span> <span data-ttu-id="9ebb7-272">이 값은 안정기가 안정화 값을 계산 하기 위해 반복 하는 샘플 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-272">This value represents the number of samples that the stabilizer iterates on to calculate the stabilized value.</span></span>

## <a name="chapter-4---directional-indicator"></a><span data-ttu-id="9ebb7-273">4 장 방향 표시기</span><span class="sxs-lookup"><span data-stu-id="9ebb7-273">Chapter 4 - Directional indicator</span></span>

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a><span data-ttu-id="9ebb7-274">목표</span><span class="sxs-lookup"><span data-stu-id="9ebb7-274">Objectives</span></span>

* <span data-ttu-id="9ebb7-275">커서에 방향 표시기를 추가 하 여 holograms를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-275">Add a directional indicator on the cursor to help find holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="9ebb7-276">지침</span><span class="sxs-lookup"><span data-stu-id="9ebb7-276">Instructions</span></span>

<span data-ttu-id="9ebb7-277">**DirectionIndicator.cs** 파일을 사용할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-277">We're going to use the **DirectionIndicator.cs** file which will:</span></span>

1. <span data-ttu-id="9ebb7-278">사용자가 holograms에 gazing 되지 않은 경우 방향 표시기를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-278">Show the directional indicator if the user is not gazing at the holograms.</span></span>
2. <span data-ttu-id="9ebb7-279">사용자가 holograms에 gazing 경우 방향 표시기를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-279">Hide the directional indicator if the user is gazing at the holograms.</span></span>
3. <span data-ttu-id="9ebb7-280">Holograms를 가리키도록 방향 표시기를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-280">Update the directional indicator to point to the holograms.</span></span>

<span data-ttu-id="9ebb7-281">그럼 시작해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-281">Let's get started.</span></span>

1. <span data-ttu-id="9ebb7-282">**계층** 패널에서 **AstroMan** 개체를 클릭 하 고 **화살표를 클릭** 하 여 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-282">Click on the **AstroMan** object in the **Hierarchy** panel and **click the arrow** to expand it.</span></span>
2. <span data-ttu-id="9ebb7-283">**계층** 패널의 **AstroMan**아래에서 **DirectionalIndicator** 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-283">In the **Hierarchy** panel, select the **DirectionalIndicator** object under **AstroMan**.</span></span>
3. <span data-ttu-id="9ebb7-284">**검사기** 패널에서 **구성 요소 추가** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-284">In the **Inspector** panel, click the **Add Component** button.</span></span>
4. <span data-ttu-id="9ebb7-285">메뉴에서 검색 상자 **방향 표시기**를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-285">In the menu, type in the search box **Direction Indicator**.</span></span> <span data-ttu-id="9ebb7-286">검색 결과를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-286">Select the search result.</span></span>
5. <span data-ttu-id="9ebb7-287">**계층** 패널에서 **커서** 개체를 **검사기**의 **cursor** 속성으로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-287">In the **Hierarchy** panel, drag and drop the **Cursor** object onto the **Cursor** property in the **Inspector**.</span></span>
6. <span data-ttu-id="9ebb7-288">**프로젝트** 패널의 **Holograms** 폴더에서 **DirectionalIndicator** 자산을 **검사기**의 **방향 표시기** 속성으로 끌어다 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-288">In the **Project** panel, in the **Holograms** folder, drag and drop the **DirectionalIndicator** asset onto the **Directional Indicator** property in the **Inspector**.</span></span>
7. <span data-ttu-id="9ebb7-289">앱을 빌드 및 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-289">Build and deploy the app.</span></span>
8. <span data-ttu-id="9ebb7-290">방향 표시기 개체를 사용 하 여 astronaut를 찾는 방법을 시청 하세요.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-290">Watch how the directional indicator object helps you find the astronaut.</span></span>

## <a name="chapter-5---billboarding"></a><span data-ttu-id="9ebb7-291">5 장-Billboarding</span><span class="sxs-lookup"><span data-stu-id="9ebb7-291">Chapter 5 - Billboarding</span></span>

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a><span data-ttu-id="9ebb7-292">목표</span><span class="sxs-lookup"><span data-stu-id="9ebb7-292">Objectives</span></span>

* <span data-ttu-id="9ebb7-293">Billboarding를 사용 하 여 holograms 항상 사용자를 중심으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-293">Use billboarding to have holograms always face towards you.</span></span>

<span data-ttu-id="9ebb7-294">**Billboard.cs** 파일을 사용 하 여 사용자가 항상 연결 되도록 GameObject 지향을 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-294">We will be using the **Billboard.cs** file to keep a GameObject oriented such that it is facing the user at all times.</span></span>

1. <span data-ttu-id="9ebb7-295">**계층** 패널에서 **AstroMan** 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-295">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
2. <span data-ttu-id="9ebb7-296">**검사기** 패널에서 **구성 요소 추가** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-296">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="9ebb7-297">메뉴에서 검색 상자 **빌보드**를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-297">In the menu, type in the search box **Billboard**.</span></span> <span data-ttu-id="9ebb7-298">검색 결과를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-298">Select the search result.</span></span>
4. <span data-ttu-id="9ebb7-299">**Inspector** 에서 **피벗 축** 을 **Y**로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-299">In the **Inspector** set the **Pivot Axis** to **Y**.</span></span>
5. <span data-ttu-id="9ebb7-300">시도해 보세요.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-300">Try it!</span></span> <span data-ttu-id="9ebb7-301">이전 처럼 앱을 빌드하고 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-301">Build and deploy the app as before.</span></span>
6. <span data-ttu-id="9ebb7-302">관점을 변경 하는 방법에 관계 없이 빌보드 개체가 어떻게 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-302">See how the Billboard object faces you no matter how you change the viewpoint.</span></span>
7. <span data-ttu-id="9ebb7-303">지금은 **AstroMan** 에서 스크립트를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-303">Delete the script from the **AstroMan** for now.</span></span>

## <a name="chapter-6---tag-along"></a><span data-ttu-id="9ebb7-304">6 장-태그 동반</span><span class="sxs-lookup"><span data-stu-id="9ebb7-304">Chapter 6 - Tag-Along</span></span>

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a><span data-ttu-id="9ebb7-305">목표</span><span class="sxs-lookup"><span data-stu-id="9ebb7-305">Objectives</span></span>

* <span data-ttu-id="9ebb7-306">태그를 사용 하 여 holograms에 대 한 의견을 보내 주시기 바랍니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-306">Use Tag-Along to have our holograms follow us around the room.</span></span>

<span data-ttu-id="9ebb7-307">이 문제를 해결 하는 동안 다음과 같은 설계 제약 조건을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-307">As we work on this issue, we'll be guided by the following design constraints:</span></span>

* <span data-ttu-id="9ebb7-308">콘텐츠는 항상 한 눈에 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-308">Content should always be a glance away.</span></span>
* <span data-ttu-id="9ebb7-309">콘텐츠는 그렇지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-309">Content should not be in the way.</span></span>
* <span data-ttu-id="9ebb7-310">헤드 잠금 콘텐츠는 불편 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-310">Head-locking content is uncomfortable.</span></span>

<span data-ttu-id="9ebb7-311">여기에 사용 된 솔루션은 "태그 동반" 방식을 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-311">The solution used here is to use a "tag-along" approach.</span></span>

<span data-ttu-id="9ebb7-312">태그 동반 개체는 사용자의 보기를 완전히 유지 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-312">A tag-along object never fully leaves the user's view.</span></span> <span data-ttu-id="9ebb7-313">태그는 고무 밴드에 의해 사용자의 헤드에 연결 된 개체로 생각할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-313">You can think of the a tag-along as being an object attached to the user's head by rubber bands.</span></span> <span data-ttu-id="9ebb7-314">사용자가 이동 하면 완전히 종료 하지 않고 뷰의 가장자리를 향해 이동 하 여 콘텐츠를 쉽게 한눈에 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-314">As the user moves, the content will stay within an easy glance by sliding towards the edge of the view without completely leaving.</span></span> <span data-ttu-id="9ebb7-315">사용자가 태그를 따라 개체를 gazes 하는 경우에는 더 자세히 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-315">When the user gazes towards the tag-along object, it comes more fully into view.</span></span>

<span data-ttu-id="9ebb7-316">**SimpleTagalong.cs** 파일을 사용할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-316">We're going to use the **SimpleTagalong.cs** file which will:</span></span>

1. <span data-ttu-id="9ebb7-317">태그 동반 개체가 카메라 범위 내에 있는지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-317">Determine if the Tag-Along object is within the camera bounds.</span></span>
2. <span data-ttu-id="9ebb7-318">뷰 내에 없는 경우 태그를 뷰에 부분적으로 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-318">If not within the view frustum, position the Tag-Along to partially within the view frustum.</span></span>
3. <span data-ttu-id="9ebb7-319">그렇지 않으면 사용자의 기본 거리를 따라 태그를 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-319">Otherwise, position the Tag-Along to a default distance from the user.</span></span>

<span data-ttu-id="9ebb7-320">이렇게 하려면 먼저 **TagalongAction**를 호출 하도록 **Interactible.cs** 스크립트를 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-320">To do this, we first must change the **Interactible.cs** script to call the **TagalongAction**.</span></span>

1. <span data-ttu-id="9ebb7-321">코딩 연습 6. a (주석 처리 줄 84 ~ 87)를 완료 하 여 **Interactible.cs** 를 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-321">Edit **Interactible.cs** by completing coding exercise 6.a (uncommenting lines 84 to 87).</span></span>

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

<span data-ttu-id="9ebb7-322">**Interactible.cs** 와 쌍을 이루는 **InteractibleAction.cs** 스크립트는 holograms을 탭 할 때 사용자 지정 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-322">The **InteractibleAction.cs** script, paired with **Interactible.cs** performs custom actions when you tap on holograms.</span></span> <span data-ttu-id="9ebb7-323">이 경우 태그에 대해 구체적으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-323">In this case, we'll use one specifically for tag-along.</span></span>

* <span data-ttu-id="9ebb7-324">**Scripts** 폴더에서 **TagalongAction.cs** 자산을 클릭 하 여 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-324">In the **Scripts** folder click on **TagalongAction.cs** asset to open in Visual Studio.</span></span>
* <span data-ttu-id="9ebb7-325">코딩 연습을 완료 하거나 다음과 같이 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-325">Complete the coding exercise or change it to this:</span></span>
  * <span data-ttu-id="9ebb7-326">**계층**의 맨 위에 있는 검색 표시줄에 **ChestButton_Center** 를 입력 하 고 결과를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-326">At the top of the **Hierarchy**, in the search bar type **ChestButton_Center** and select the result.</span></span>
  * <span data-ttu-id="9ebb7-327">**검사기** 패널에서 **구성 요소 추가** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-327">In the **Inspector** panel, click the **Add Component** button.</span></span>
  * <span data-ttu-id="9ebb7-328">메뉴에서 검색 상자 **Tagalong 작업**을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-328">In the menu, type in the search box **Tagalong Action**.</span></span> <span data-ttu-id="9ebb7-329">검색 결과를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-329">Select the search result.</span></span>
  * <span data-ttu-id="9ebb7-330">**Holograms** 폴더에서 **Tagalong** 자산을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-330">In **Holograms** folder find the **Tagalong** asset.</span></span>
  * <span data-ttu-id="9ebb7-331">**계층**에서 **ChestButton_Center** 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-331">Select the **ChestButton_Center** object in the **Hierarchy**.</span></span> <span data-ttu-id="9ebb7-332">**TagAlong** 개체를 **프로젝트** 패널에서 **Inspector** **개체의 TagAlong** 속성에 끌어서 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-332">Drag and drop the **TagAlong** object from the **Project** panel onto the **Inspector** into the **Object To Tagalong** property.</span></span>
  * <span data-ttu-id="9ebb7-333">**Inspector** 에서 **Tagalong Action** 개체를 **Interactible** 스크립트의 **Interactible action** 필드로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-333">Drag the **Tagalong Action** object from the **Inspector** into the **Interactible Action** field on the **Interactible** script.</span></span>
* <span data-ttu-id="9ebb7-334">**TagalongAction** 스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-334">Double click the **TagalongAction** script to open it in Visual Studio.</span></span>

![Interactible 설정](images/holograms210-interactible.png)

<span data-ttu-id="9ebb7-336">다음을 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-336">We need to add the following:</span></span>

* <span data-ttu-id="9ebb7-337">TagalongAction 스크립트 (InteractibleAction에서 상속 됨)의 PerformAction 함수에 기능을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-337">Add functionality to the PerformAction function in the TagalongAction script (inherited from InteractibleAction).</span></span>
* <span data-ttu-id="9ebb7-338">Billboarding을 gazed 개체에 추가 하 고 피벗 축을 XY로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-338">Add billboarding to the gazed-upon object, and set the pivot axis to XY.</span></span>
* <span data-ttu-id="9ebb7-339">그런 다음 개체에 간단한 태그를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-339">Then add simple Tag-Along to the object.</span></span>

<span data-ttu-id="9ebb7-340">**TagalongAction.cs**의 솔루션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-340">Here's our solution, from **TagalongAction.cs**:</span></span>

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

* <span data-ttu-id="9ebb7-341">시도해 보세요.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-341">Try it!</span></span> <span data-ttu-id="9ebb7-342">앱을 빌드 및 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-342">Build and deploy the app.</span></span>
* <span data-ttu-id="9ebb7-343">콘텐츠가 응시 지점의 중심을 따라가는 지를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ebb7-343">Watch how the content follows the center of the gaze point, but not continuously and without blocking it.</span></span>
