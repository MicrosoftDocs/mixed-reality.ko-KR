---
title: MR 입력 211-제스처
description: Unity, Visual Studio 및 HoloLens를 사용 하 여이 코딩 연습을 수행 하 여 제스처 개념에 대 한 세부 정보를 알아보세요.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit, 아카데미, 자습서, 제스처
ms.openlocfilehash: 76d2b4c0ac3d0a3783b091f7dc8c39548a18b548
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522462"
---
>[!NOTE]
><span data-ttu-id="a97e0-104">혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="a97e0-105">따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="a97e0-106">이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="a97e0-107">지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="a97e0-108">향후에는 HoloLens 2를 개발 하는 방법을 보여 주는 새 자습서 시리즈를 게시할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="a97e0-109">이 알림은 게시 될 때 해당 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-input-211-gesture"></a><span data-ttu-id="a97e0-110">MR 입력 211: 제스처</span><span class="sxs-lookup"><span data-stu-id="a97e0-110">MR Input 211: Gesture</span></span>

<span data-ttu-id="a97e0-111">[제스처](gestures.md) 사용자 의도를 작업으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-111">[Gestures](gestures.md) turn user intention into action.</span></span> <span data-ttu-id="a97e0-112">제스처를 사용 하면 사용자가 holograms와 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-112">With gestures, users can interact with holograms.</span></span> <span data-ttu-id="a97e0-113">이 과정에서는 사용자의 손을 추적 하 고, 사용자 입력에 응답 하 고, 직접 상태 및 위치에 따라 사용자에 게 피드백을 제공 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-113">In this course, we'll learn how to track the user's hands, respond to user input, and give feedback to the user based on hand state and location.</span></span>

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

<span data-ttu-id="a97e0-114">[MR 기본 101](holograms-101.md)에서는 간단한 공기 탭 제스처를 사용 하 여 holograms와 상호 작용 했습니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-114">In [MR Basics 101](holograms-101.md), we used a simple air-tap gesture to interact with our holograms.</span></span> <span data-ttu-id="a97e0-115">이제는 공중 탭 제스처를 벗어나 이동 하 여 다음에 대 한 새로운 개념을 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-115">Now, we'll move beyond the air-tap gesture and explore new concepts to:</span></span>

* <span data-ttu-id="a97e0-116">사용자의 손을 추적 하 고 사용자에 게 피드백을 제공 하는 경우를 감지 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-116">Detect when the user's hand is being tracked and provide feedback to the user.</span></span>
* <span data-ttu-id="a97e0-117">탐색 제스처를 사용 하 여 holograms를 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-117">Use a navigation gesture to rotate our holograms.</span></span>
* <span data-ttu-id="a97e0-118">사용자의 손을 볼 때 사용자 의견을 제공 하세요.</span><span class="sxs-lookup"><span data-stu-id="a97e0-118">Provide feedback when the user's hand is about to go out of view.</span></span>
* <span data-ttu-id="a97e0-119">조작 이벤트를 사용 하 여 사용자가 손을 holograms 이동할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-119">Use manipulation events to allow users to move holograms with their hands.</span></span>

<span data-ttu-id="a97e0-120">이 과정에서는 [MR 입력 210](holograms-210.md)에서 빌드된 Unity 프로젝트 **모델 탐색기**를 다시 방문 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-120">In this course, we'll revisit the Unity project **Model Explorer**, which we built in [MR Input 210](holograms-210.md).</span></span> <span data-ttu-id="a97e0-121">Astronaut 친구는 이러한 새 제스처 개념을 탐색 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-121">Our astronaut friend is back to assist us in our exploration of these new gesture concepts.</span></span>

>[!IMPORTANT]
><span data-ttu-id="a97e0-122">아래 각 장에 포함 된 비디오는 이전 버전의 Unity 및 혼합 현실 도구 키트를 사용 하 여 기록 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-122">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="a97e0-123">단계별 지침은 정확 하 고 최신 상태 이지만 최신의 비디오에서 스크립트 및 시각적 개체를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-123">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="a97e0-124">Posterity에 대 한 비디오는 포함 되어 있지만 적용 되는 개념은 그대로 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-124">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="a97e0-125">장치 지원</span><span class="sxs-lookup"><span data-stu-id="a97e0-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="a97e0-126">과정</span><span class="sxs-lookup"><span data-stu-id="a97e0-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="a97e0-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="a97e0-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="a97e0-128"><a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="a97e0-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="a97e0-129">MR 입력 211: 제스처</span><span class="sxs-lookup"><span data-stu-id="a97e0-129">MR Input 211: Gesture</span></span></td><td style="text-align: center;"> <span data-ttu-id="a97e0-130">✔️</span><span class="sxs-lookup"><span data-stu-id="a97e0-130">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="a97e0-131">✔️</span><span class="sxs-lookup"><span data-stu-id="a97e0-131">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="a97e0-132">시작하기 전 주의 사항</span><span class="sxs-lookup"><span data-stu-id="a97e0-132">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="a97e0-133">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="a97e0-133">Prerequisites</span></span>

* <span data-ttu-id="a97e0-134">올바른 [도구로](install-the-tools.md)구성 된 WINDOWS 10 PC입니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-134">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="a97e0-135">몇 가지 C# 기본적인 프로그래밍 기능.</span><span class="sxs-lookup"><span data-stu-id="a97e0-135">Some basic C# programming ability.</span></span>
* <span data-ttu-id="a97e0-136">[MR 기본 101](holograms-101.md)를 완료 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-136">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="a97e0-137">[MR 입력 210](holograms-210.md)을 완료 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-137">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="a97e0-138">[개발용으로 구성 된](using-visual-studio.md#enabling-developer-mode)HoloLens 장치입니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-138">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="a97e0-139">프로젝트 파일</span><span class="sxs-lookup"><span data-stu-id="a97e0-139">Project files</span></span>

* <span data-ttu-id="a97e0-140">프로젝트에 필요한 [파일](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) 을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-140">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) required by the project.</span></span><span data-ttu-id="a97e0-141"> Unity 2017.2 이상이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-141"> Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="a97e0-142">바탕 화면 또는 기타 쉬운 위치에 파일을 보관 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-142">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="a97e0-143">다운로드 하기 전에 소스 코드를 확인 하려는 경우 [GitHub에서 사용할 수](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture)있습니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-143">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="a97e0-144">정오표 및 참고 사항</span><span class="sxs-lookup"><span data-stu-id="a97e0-144">Errata and Notes</span></span>

* <span data-ttu-id="a97e0-145">코드에서 중단점을 적중 하려면 Visual Studio의 도구-> 옵션-> 디버깅에서 "내 코드만 사용"을 사용 하지 않도록 설정 (*선택 취소*) 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-145">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-0---unity-setup"></a><span data-ttu-id="a97e0-146">0 장-Unity 설치</span><span class="sxs-lookup"><span data-stu-id="a97e0-146">Chapter 0 - Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="a97e0-147">지침</span><span class="sxs-lookup"><span data-stu-id="a97e0-147">Instructions</span></span>

1. <span data-ttu-id="a97e0-148">Unity를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-148">Start Unity.</span></span>
2. <span data-ttu-id="a97e0-149">**열기**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-149">Select **Open**.</span></span>
3. <span data-ttu-id="a97e0-150">이전에 보관 하지 않은 **제스처** 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-150">Navigate to the **Gesture** folder you previously un-archived.</span></span>
4. <span data-ttu-id="a97e0-151">**모델 탐색기** **시작**/폴더를 찾아 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-151">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="a97e0-152">**폴더 선택** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-152">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="a97e0-153">**프로젝트** 패널에서 **장면** 폴더를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-153">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="a97e0-154">**모델 탐색기** 장면을 두 번 클릭 하 여 Unity에서 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-154">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="a97e0-155">빌드</span><span class="sxs-lookup"><span data-stu-id="a97e0-155">Building</span></span>

1. <span data-ttu-id="a97e0-156">Unity에서 **파일 > 빌드 설정**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-156">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="a97e0-157">백그라운드에서 장면 **/모델 탐색기** 가 **백그라운드**에서 표시 되지 않는 경우 **열린 장면 추가** 를 클릭 하 여 장면을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-157">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="a97e0-158">특별히 HoloLens를 개발 하는 경우 **대상 장치** 를 **hololens**로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-158">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="a97e0-159">그렇지 않으면 **모든 장치**에 그대로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-159">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="a97e0-160">**빌드 형식이** **D3D** 로 설정 되 고 **sdk** 가 **최신 버전** 으로 설정 되어 있는지 확인 합니다 (sdk 16299 이상 이어야 함).</span><span class="sxs-lookup"><span data-stu-id="a97e0-160">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="a97e0-161">**빌드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-161">Click **Build**.</span></span>
6. <span data-ttu-id="a97e0-162">"App" 이라는 **새 폴더** 를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-162">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="a97e0-163">단일 **앱** 폴더를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-163">Single click the **App** folder.</span></span>
8. <span data-ttu-id="a97e0-164">**폴더 선택** 을 클릭 하면 Unity에서 Visual Studio 용 프로젝트 빌드를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-164">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="a97e0-165">Unity가 완료 되 면 파일 탐색기 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-165">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="a97e0-166">**앱** 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-166">Open the **App** folder.</span></span>
2. <span data-ttu-id="a97e0-167">**모델 탐색기 Visual Studio 솔루션**을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-167">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="a97e0-168">HoloLens에 배포 하는 경우:</span><span class="sxs-lookup"><span data-stu-id="a97e0-168">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="a97e0-169">Visual Studio의 맨 위 도구 모음을 사용 하 여 대상을 디버그에서 **릴리스** 로, ARM에서 **x 86**으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-169">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="a97e0-170">로컬 컴퓨터 단추 옆에 있는 드롭다운 화살표를 클릭 하 고 **원격 컴퓨터**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-170">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="a97e0-171">**HoloLens 장치 IP 주소** 를 입력 하 고 인증 모드를 **유니버설 (암호화 되지 않은 프로토콜)** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-171">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="a97e0-172">**선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-172">Click **Select**.</span></span> <span data-ttu-id="a97e0-173">장치 IP 주소를 모르는 경우 **네트워크 & 인터넷 > 고급 옵션 > 설정**을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a97e0-173">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="a97e0-174">상단 메뉴 모음에서 **디버그-> 디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-174">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="a97e0-175">처음으로 장치에 배포 하는 경우에는 [Visual Studio와 쌍](using-visual-studio.md#pairing-your-device-hololens)으로 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-175">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="a97e0-176">앱이 배포 되 면 **선택 제스처로** **fitbox** 를 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-176">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="a97e0-177">모던 헤드셋에 배포 하는 경우:</span><span class="sxs-lookup"><span data-stu-id="a97e0-177">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="a97e0-178">Visual Studio의 맨 위 도구 모음을 사용 하 여 대상을 디버그에서 **릴리스** 로, ARM에서 x **64**로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-178">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="a97e0-179">배포 대상이 **로컬 컴퓨터**로 설정 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-179">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="a97e0-180">상단 메뉴 모음에서 **디버그-> 디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-180">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="a97e0-181">앱이 배포 되 면 동작 컨트롤러에서 트리거를 당겨 **Fitbox** 를 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-181">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="a97e0-182">Visual Studio 오류 패널에 몇 가지 빨간색 오류가 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-182">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="a97e0-183">무시 해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-183">It is safe to ignore them.</span></span> <span data-ttu-id="a97e0-184">출력 패널로 전환 하 여 실제 빌드 진행률을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-184">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="a97e0-185">출력 패널에 오류가 발생 하면 문제를 해결 해야 합니다 (대부분 스크립트에서 실수로 인해 발생 하는 경우).</span><span class="sxs-lookup"><span data-stu-id="a97e0-185">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---hand-detected-feedback"></a><span data-ttu-id="a97e0-186">1 장 검색 된 피드백</span><span class="sxs-lookup"><span data-stu-id="a97e0-186">Chapter 1 - Hand detected feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a><span data-ttu-id="a97e0-187">목표</span><span class="sxs-lookup"><span data-stu-id="a97e0-187">Objectives</span></span>

* <span data-ttu-id="a97e0-188">직접 추적 이벤트를 구독 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-188">Subscribe to hand tracking events.</span></span>
* <span data-ttu-id="a97e0-189">커서 피드백을 사용 하 여 손을 추적할 때 사용자를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-189">Use cursor feedback to show users when a hand is being tracked.</span></span>

### <a name="instructions"></a><span data-ttu-id="a97e0-190">지침</span><span class="sxs-lookup"><span data-stu-id="a97e0-190">Instructions</span></span>

* <span data-ttu-id="a97e0-191">**계층** 패널에서 **inputmanager** 개체를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-191">In the **Hierarchy** panel, expand the **InputManager** object.</span></span>
* <span data-ttu-id="a97e0-192">**GesturesInput** 개체를 찾고 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-192">Look for and select the **GesturesInput** object.</span></span>

<span data-ttu-id="a97e0-193">**InteractionInputSource.cs** 스크립트는 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-193">The **InteractionInputSource.cs** script performs these steps:</span></span>

1. <span data-ttu-id="a97e0-194">InteractionSourceDetected 및 InteractionSourceLost 이벤트를 구독 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-194">Subscribes to the InteractionSourceDetected and InteractionSourceLost events.</span></span>
2. <span data-ttu-id="a97e0-195">수동 검색 상태를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-195">Sets the HandDetected state.</span></span>
3. <span data-ttu-id="a97e0-196">InteractionSourceDetected 및 InteractionSourceLost 이벤트의 구독을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-196">Unsubscribes from the InteractionSourceDetected and InteractionSourceLost events.</span></span>

<span data-ttu-id="a97e0-197">다음으로, 사용자의 작업에 따라 사용자 의견을 표시 하는 커서를 [MR 입력 210](holograms-210.md) 에서 하나로 업그레이드 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-197">Next, we'll upgrade our cursor from [MR Input 210](holograms-210.md) into one that shows feedback depending on the user's actions.</span></span>

1. <span data-ttu-id="a97e0-198">**계층** 패널에서 **커서** 개체를 선택 하 고 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-198">In the **Hierarchy** panel, select the **Cursor** object and delete it.</span></span>
2. <span data-ttu-id="a97e0-199">**프로젝트** 패널에서 **CursorWithFeedback** 를 검색 하 여 **계층** 패널로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-199">In the **Project** panel, search for **CursorWithFeedback** and drag it into the **Hierarchy** panel.</span></span>
3. <span data-ttu-id="a97e0-200">**계층** 패널 **에서 inputmanager** 를 클릭 한 다음 **계층 구조** 에서 **CursorWithFeedback** 개체를 다음의 맨 아래에 있는 Inputmanager의 **simplesinglepointerselector**필드로 끕니다.  **검사기**.</span><span class="sxs-lookup"><span data-stu-id="a97e0-200">Click on **InputManager** in the **Hierarchy** panel, then drag the **CursorWithFeedback** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>
4. <span data-ttu-id="a97e0-201">**계층**에서 **CursorWithFeedback** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-201">Click on the **CursorWithFeedback** in the **Hierarchy**.</span></span>
5. <span data-ttu-id="a97e0-202">**검사기** 패널에서 **개체 커서** 스크립트의 **커서 상태 데이터** 를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-202">In the **Inspector** panel, expand **Cursor State Data** on the **Object Cursor** script.</span></span>

<span data-ttu-id="a97e0-203">**커서 상태 데이터** 는 다음과 같이 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-203">The **Cursor State Data** works like this:</span></span>

* <span data-ttu-id="a97e0-204">모든 **관찰** 상태는 검색 된 손이 없고 사용자가 간단히 살펴보는 것을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-204">Any **Observe** state means that no hand is detected and the user is simply looking around.</span></span>
* <span data-ttu-id="a97e0-205">모든 **상호 작용** 상태는 손 또는 컨트롤러가 검색 됨을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-205">Any **Interact** state means that a hand or controller is detected.</span></span>
* <span data-ttu-id="a97e0-206">**가리키기** 상태는 사용자가 홀로그램을 보고 있음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-206">Any **Hover** state means the user is looking at a hologram.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="a97e0-207">빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="a97e0-207">Build and Deploy</span></span>

* <span data-ttu-id="a97e0-208">Unity에서 **파일 > 빌드 설정을** 사용 하 여 응용 프로그램을 다시 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-208">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="a97e0-209">**앱** 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-209">Open the **App** folder.</span></span>
* <span data-ttu-id="a97e0-210">아직 열려 있지 않은 경우 **Modelexplorer Visual Studio 솔루션**을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-210">If it's not already open, open the **ModelExplorer Visual Studio Solution**.</span></span>
  * <span data-ttu-id="a97e0-211">설정 하는 동안 Visual Studio에서이 프로젝트를 이미 빌드/배포한 경우 해당 인스턴스를 열고 메시지가 표시 되 면 다시 로드를 클릭할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-211">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>
* <span data-ttu-id="a97e0-212">Visual Studio에서 **디버그-> 디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-212">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="a97e0-213">응용 프로그램을 HoloLens에 배포한 후에는 공기 탭 제스처를 사용 하 여 fitbox를 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-213">After the application deploys to the HoloLens, dismiss the fitbox using the air-tap gesture.</span></span>
* <span data-ttu-id="a97e0-214">손을 보기로 이동 하 고 인덱스 손가락을 하늘으로 가리켜 손으로 추적을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-214">Move your hand into view and point your index finger to the sky to start hand tracking.</span></span>
* <span data-ttu-id="a97e0-215">왼쪽, 오른쪽, 위쪽 및 아래쪽으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-215">Move your hand left, right, up and down.</span></span>
* <span data-ttu-id="a97e0-216">손 모양 검색 후 보기가 손실 될 때 커서가 어떻게 변경 되는지 봅니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-216">Watch how the cursor changes when your hand is detected and then lost from view.</span></span>
* <span data-ttu-id="a97e0-217">모던 헤드셋을 사용할 경우 컨트롤러를 연결 하 고 연결을 끊어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-217">If you're on an immersive headset, you'll have to connect and disconnect your controller.</span></span> <span data-ttu-id="a97e0-218">연결 된 컨트롤러는 항상 "사용할 수 있음" 이므로이 피드백은 몰입 형 장치에서 그다지 흥미로운 점이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-218">This feedback becomes less interesting on an immersive device, as a connected controller will always be "available".</span></span>

## <a name="chapter-2---navigation"></a><span data-ttu-id="a97e0-219">2 장-탐색</span><span class="sxs-lookup"><span data-stu-id="a97e0-219">Chapter 2 - Navigation</span></span>

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a><span data-ttu-id="a97e0-220">목표</span><span class="sxs-lookup"><span data-stu-id="a97e0-220">Objectives</span></span>

* <span data-ttu-id="a97e0-221">탐색 제스처 이벤트를 사용 하 여 astronaut를 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-221">Use Navigation gesture events to rotate the astronaut.</span></span>

### <a name="instructions"></a><span data-ttu-id="a97e0-222">지침</span><span class="sxs-lookup"><span data-stu-id="a97e0-222">Instructions</span></span>

<span data-ttu-id="a97e0-223">앱에서 탐색 제스처를 사용 하려면 탐색 제스처가 발생할 때 **GestureAction.cs** 를 편집 하 여 개체를 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-223">To use Navigation gestures in our app, we are going to edit **GestureAction.cs** to rotate objects when the Navigation gesture occurs.</span></span> <span data-ttu-id="a97e0-224">또한 탐색을 사용할 수 있을 때 표시할 피드백을 커서에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-224">Additionally, we'll add feedback to the cursor to display when Navigation is available.</span></span>

1. <span data-ttu-id="a97e0-225">**계층** 패널에서 **CursorWithFeedback**를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-225">In the **Hierarchy** panel, expand **CursorWithFeedback**.</span></span>
2. <span data-ttu-id="a97e0-226">**Holograms** 폴더에서 **ScrollFeedback** 자산을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-226">In the **Holograms** folder, find the **ScrollFeedback** asset.</span></span>
3. <span data-ttu-id="a97e0-227">**ScrollFeedback** Prefab를 **계층**의 **CursorWithFeedback** GameObject에 끌어다 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-227">Drag and drop the **ScrollFeedback** prefab onto the **CursorWithFeedback** GameObject in the **Hierarchy**.</span></span>
4. <span data-ttu-id="a97e0-228">**CursorWithFeedback**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-228">Click on **CursorWithFeedback**.</span></span>
5. <span data-ttu-id="a97e0-229">**검사기** 패널에서 **구성 요소 추가** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-229">In the **Inspector** panel, click the **Add Component** button.</span></span>
6. <span data-ttu-id="a97e0-230">메뉴의 검색 상자에 **CursorFeedback**을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-230">In the menu, type in the search box **CursorFeedback**.</span></span> <span data-ttu-id="a97e0-231">검색 결과를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-231">Select the search result.</span></span>
7. <span data-ttu-id="a97e0-232">**ScrollFeedback** 개체를 **계층** 의 **커서 피드백** 구성 요소에 있는 **검색 된 게임 개체의 스크롤** 속성으로 끌어 **놓습니다.**</span><span class="sxs-lookup"><span data-stu-id="a97e0-232">Drag and drop the **ScrollFeedback** object from the **Hierarchy** onto the **Scroll Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>
8. <span data-ttu-id="a97e0-233">**계층** 패널에서 **AstroMan** 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-233">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
9. <span data-ttu-id="a97e0-234">**검사기** 패널에서 **구성 요소 추가** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-234">In the **Inspector** panel, click the **Add Component** button.</span></span>
10. <span data-ttu-id="a97e0-235">메뉴에서 검색 상자 **제스처 동작**을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-235">In the menu, type in the search box **Gesture Action**.</span></span> <span data-ttu-id="a97e0-236">검색 결과를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-236">Select the search result.</span></span>

<span data-ttu-id="a97e0-237">다음으로, Visual Studio에서 **GestureAction.cs** 을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-237">Next, open **GestureAction.cs** in Visual Studio.</span></span> <span data-ttu-id="a97e0-238">연습 2. c 코딩에서 스크립트를 편집 하 여 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-238">In coding exercise 2.c, edit the script to do the following:</span></span>

1. <span data-ttu-id="a97e0-239">탐색 제스처가 수행 될 때마다 **AstroMan 개체를 회전** 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-239">**Rotate the AstroMan** object whenever a Navigation gesture is performed.</span></span>
2. <span data-ttu-id="a97e0-240">**RotationFactor** 를 계산 하 여 개체에 적용 되는 회전의 양을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-240">Calculate the **rotationFactor** to control the amount of rotation applied to the object.</span></span>
3. <span data-ttu-id="a97e0-241">사용자가 왼쪽 또는 오른쪽으로 이동 하면 y 축 주위로 **개체를 회전** 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-241">**Rotate the object** around the y-axis when the user moves their hand left or right.</span></span>

<span data-ttu-id="a97e0-242">스크립트에서 예제 2(sp2)를 완료 하거나 코드를 아래의 완료 된 솔루션으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-242">Complete coding exercises 2.c in the script, or replace the code with the completed solution below:</span></span>

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

<span data-ttu-id="a97e0-243">다른 탐색 이벤트는 이미 일부 정보로 채워져 있음을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-243">You'll notice that the other navigation events are already filled in with some info.</span></span> <span data-ttu-id="a97e0-244">GameObject를 도구 키트의 InputSystem's stack에 푸시하여, 회전이 시작 된 후 사용자가 Astronaut에 포커스를 유지할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-244">We push the GameObject onto the Toolkit's InputSystem's modal stack, so the user doesn't have to maintain focus on the Astronaut once rotation has begun.</span></span> <span data-ttu-id="a97e0-245">마찬가지로 제스처가 완료 되 면 GameObject를 스택에서 팝 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-245">Correspondingly, we pop the GameObject off the stack once the gesture is completed.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="a97e0-246">빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="a97e0-246">Build and Deploy</span></span>

1. <span data-ttu-id="a97e0-247">Unity에서 응용 프로그램을 다시 빌드한 다음, Visual Studio에서 빌드 및 배포 하 여 HoloLens에서 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-247">Rebuild the application in Unity and then build and deploy from Visual Studio to run it in the HoloLens.</span></span>
2. <span data-ttu-id="a97e0-248">Astronaut을 응시 하 고 두 개의 화살표가 커서 양쪽에 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-248">Gaze at the astronaut, two arrows should appear on either side of the cursor.</span></span> <span data-ttu-id="a97e0-249">이 새 시각적 개체는 astronaut을 회전할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-249">This new visual indicates that the astronaut can be rotated.</span></span>
3. <span data-ttu-id="a97e0-250">HoloLens가 손을 추적 하기 시작 하도록 준비 된 위치 (하늘을 가리키고 있는 인덱스 손가락)에 손을 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-250">Place your hand in the ready position (index finger pointed towards the sky) so the HoloLens will start tracking your hand.</span></span>
4. <span data-ttu-id="a97e0-251">Astronaut를 회전 하려면 인덱스 손가락을 왼쪽 이나 오른쪽으로 이동 하 여 NavigationX 제스처를 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-251">To rotate the astronaut, lower your index finger to a pinch position, and then move your hand left or right to trigger the NavigationX gesture.</span></span>

## <a name="chapter-3---hand-guidance"></a><span data-ttu-id="a97e0-252">3 장 지침</span><span class="sxs-lookup"><span data-stu-id="a97e0-252">Chapter 3 - Hand Guidance</span></span>

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a><span data-ttu-id="a97e0-253">목표</span><span class="sxs-lookup"><span data-stu-id="a97e0-253">Objectives</span></span>

* <span data-ttu-id="a97e0-254">수동 **가이드 점수** 를 사용 하 여 수동 추적이 손실 되는 경우를 예측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-254">Use **hand guidance score** to help predict when hand tracking will be lost.</span></span>
* <span data-ttu-id="a97e0-255">**커서에 대 한 피드백** 을 제공 하 여 사용자가 카메라의 보기 가장자리에 가까이 있는 경우를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-255">Provide **feedback on the cursor** to show when the user's hand nears the camera's edge of view.</span></span>

### <a name="instructions"></a><span data-ttu-id="a97e0-256">지침</span><span class="sxs-lookup"><span data-stu-id="a97e0-256">Instructions</span></span>

1. <span data-ttu-id="a97e0-257">**계층** 패널에서 **CursorWithFeedback** 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-257">In the **Hierarchy** panel, select the **CursorWithFeedback** object.</span></span>
2. <span data-ttu-id="a97e0-258">**검사기** 패널에서 **구성 요소 추가** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-258">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="a97e0-259">메뉴에서 검색 상자 **손 모양 지침**을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-259">In the menu, type in the search box **Hand Guidance**.</span></span> <span data-ttu-id="a97e0-260">검색 결과를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-260">Select the search result.</span></span>
4. <span data-ttu-id="a97e0-261">**프로젝트** 패널 **Holograms** 폴더에서 **HandGuidanceFeedback** 자산을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-261">In the **Project** panel **Holograms** folder, find the **HandGuidanceFeedback** asset.</span></span>
5. <span data-ttu-id="a97e0-262">**HandGuidanceFeedback** 자산을 **검사기** 패널의 **손 지침 표시기** 속성으로 끌어다 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-262">Drag and drop the **HandGuidanceFeedback** asset onto the **Hand Guidance Indicator** property in the **Inspector** panel.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="a97e0-263">빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="a97e0-263">Build and Deploy</span></span>

* <span data-ttu-id="a97e0-264">Unity에서 응용 프로그램을 다시 빌드한 다음, Visual Studio에서 빌드 및 배포 하 여 HoloLens에서 앱을 경험해 보세요.</span><span class="sxs-lookup"><span data-stu-id="a97e0-264">Rebuild the application in Unity and then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="a97e0-265">손으로 보기를 전환 하 고 인덱스 손가락을 발생 시켜 추적 하세요.</span><span class="sxs-lookup"><span data-stu-id="a97e0-265">Bring your hand into view and raise your index finger to get tracked.</span></span>
* <span data-ttu-id="a97e0-266">탐색 제스처로 astronaut 회전을 시작 합니다 (인덱스 손가락 및 엄지 단추를 함께 사용).</span><span class="sxs-lookup"><span data-stu-id="a97e0-266">Start rotating the astronaut with the Navigation gesture (pinch your index finger and thumb together).</span></span>
* <span data-ttu-id="a97e0-267">왼쪽, 오른쪽, 위쪽 및 아래쪽으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-267">Move your hand far left, right, up, and down.</span></span>
* <span data-ttu-id="a97e0-268">제스처 프레임의 가장자리가 가까이 있으면 커서 옆에 화살표를 표시 하 여 손 추적이 손실 된다는 경고를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-268">As your hand nears the edge of the gesture frame, an arrow should appear next to the cursor to warn you that hand tracking will be lost.</span></span> <span data-ttu-id="a97e0-269">화살표는 추적 손실을 방지 하기 위해 손을 이동할 방향을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-269">The arrow indicates which direction to move your hand in order to prevent tracking from being lost.</span></span>

## <a name="chapter-4---manipulation"></a><span data-ttu-id="a97e0-270">4 장-조작</span><span class="sxs-lookup"><span data-stu-id="a97e0-270">Chapter 4 - Manipulation</span></span>

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a><span data-ttu-id="a97e0-271">목표</span><span class="sxs-lookup"><span data-stu-id="a97e0-271">Objectives</span></span>

* <span data-ttu-id="a97e0-272">조작 이벤트를 사용 하 여 astronaut를 손으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-272">Use Manipulation events to move the astronaut with your hands.</span></span>
* <span data-ttu-id="a97e0-273">조작을 사용할 수 있는 경우 사용자에 게 알릴 수 있도록 커서에 대 한 피드백을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-273">Provide feedback on the cursor to let the user know when Manipulation can be used.</span></span>

### <a name="instructions"></a><span data-ttu-id="a97e0-274">지침</span><span class="sxs-lookup"><span data-stu-id="a97e0-274">Instructions</span></span>

<span data-ttu-id="a97e0-275">GestureManager.cs 및 AstronautManager.cs를 사용 하면 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-275">GestureManager.cs and AstronautManager.cs will allow us to do the following:</span></span>

1. <span data-ttu-id="a97e0-276">음성 키워드 "**Move Astronaut**"를 사용 하 여 **조작** 제스처를 사용 하도록 설정 하 고 "**Rotate Astronaut**"를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-276">Use the speech keyword "**Move Astronaut**" to enable **Manipulation** gestures and "**Rotate Astronaut**" to disable them.</span></span>
2. <span data-ttu-id="a97e0-277">**조작 제스처 인식기**에 대 한 응답으로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-277">Switch to responding to the **Manipulation Gesture Recognizer**.</span></span>

<span data-ttu-id="a97e0-278">이제 시작하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-278">Let's get started.</span></span>

1. <span data-ttu-id="a97e0-279">**계층** 패널에서 비어 있는 새 GameObject을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-279">In the **Hierarchy** panel, create a new empty GameObject.</span></span> <span data-ttu-id="a97e0-280">이름을 "**AstronautManager**"로 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-280">Name it "**AstronautManager**".</span></span>
2. <span data-ttu-id="a97e0-281">**검사기** 패널에서 **구성 요소 추가** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-281">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="a97e0-282">메뉴의 검색 상자에 **Astronaut Manager**를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-282">In the menu, type in the search box **Astronaut Manager**.</span></span> <span data-ttu-id="a97e0-283">검색 결과를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-283">Select the search result.</span></span>
4. <span data-ttu-id="a97e0-284">**검사기** 패널에서 **구성 요소 추가** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-284">In the **Inspector** panel, click the **Add Component** button.</span></span>
5. <span data-ttu-id="a97e0-285">메뉴의 검색 상자에 **음성 입력 원본**을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-285">In the menu, type in the search box **Speech Input Source**.</span></span> <span data-ttu-id="a97e0-286">검색 결과를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-286">Select the search result.</span></span>

<span data-ttu-id="a97e0-287">이제 astronaut의 상호 작용 상태를 제어 하는 데 필요한 음성 명령을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-287">We'll now add the speech commands required to control the interaction state of the astronaut.</span></span>

1. <span data-ttu-id="a97e0-288">**검사기**에서 **키워드** 섹션을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-288">Expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="a97e0-289">오른쪽의 **+** 를 클릭 하 여 새 키워드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-289">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="a97e0-290">키워드를 **Move Astronaut**로 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-290">Type the Keyword as **Move Astronaut**.</span></span> <span data-ttu-id="a97e0-291">원한다 면 키 바로 가기를 자유롭게 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-291">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="a97e0-292">오른쪽의 **+** 를 클릭 하 여 새 키워드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-292">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="a97e0-293">**Astronaut 회전**으로 키워드를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-293">Type the Keyword as **Rotate Astronaut**.</span></span> <span data-ttu-id="a97e0-294">원한다 면 키 바로 가기를 자유롭게 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-294">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="a97e0-295">해당 처리기 코드는 **GestureAction.cs**의 **ISpeechHandler OnSpeechKeywordRecognized** 처리기에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-295">The corresponding handler code can be found in **GestureAction.cs**, in the **ISpeechHandler.OnSpeechKeywordRecognized** handler.</span></span>

![4 장의 음성 입력 소스를 설정 하는 방법](images/holograms211-speech.png)

<span data-ttu-id="a97e0-297">다음으로 커서에서 조작 피드백을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-297">Next, we'll setup the manipulation feedback on the cursor.</span></span>

1. <span data-ttu-id="a97e0-298">**프로젝트** 패널 **Holograms** 폴더에서 **pathingfeedback** 자산을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-298">In the **Project** panel **Holograms** folder, find the **PathingFeedback** asset.</span></span>
2. <span data-ttu-id="a97e0-299">**Pathingfeedback** Prefab을 **계층**의 **CursorWithFeedback** 개체로 끌어서 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-299">Drag and drop the **PathingFeedback** prefab onto the **CursorWithFeedback** object in the **Hierarchy**.</span></span>
3. <span data-ttu-id="a97e0-300">**계층** 패널에서 **CursorWithFeedback**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-300">In the **Hierarchy** panel, click on **CursorWithFeedback**.</span></span>
4. <span data-ttu-id="a97e0-301">**Inspector**의 **커서 피드백** 구성 요소에서  **Pathing 검색 된 게임 개체** 속성에 **pathingfeedback** 개체를 끌어서 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-301">Drag and drop the **PathingFeedback** object from the **Hierarchy** onto the **Pathing Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>

<span data-ttu-id="a97e0-302">이제 **GestureAction.cs** 에 코드를 추가 하 여 다음을 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-302">Now we need to add code to **GestureAction.cs** to enable the following:</span></span>

1. <span data-ttu-id="a97e0-303">**IManipulationHandler** 함수에 코드를 추가 합니다 .이 함수는 **조작** 제스처가 검색 될 때 astronaut를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-303">Add code to the **IManipulationHandler.OnManipulationUpdated** function, which will move the astronaut when a **Manipulation** gesture is detected.</span></span>
2. <span data-ttu-id="a97e0-304">**이동 벡터** 를 계산 하 여 astronaut 위치에 따라 이동 해야 하는 위치를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-304">Calculate the **movement vector** to determine where the astronaut should be moved to based on hand position.</span></span>
3. <span data-ttu-id="a97e0-305">Astronaut를 새 위치로 **이동** 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-305">**Move** the astronaut to the new position.</span></span>

<span data-ttu-id="a97e0-306">**GestureAction.cs**에서 연습 4-5를 완료 하거나 아래에서 완성 된 솔루션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-306">Complete coding exercise 4.a in **GestureAction.cs**, or use our completed solution below:</span></span>

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
            transform.position = manipulationOriginalPosition + eventData.CumulativeDelta;
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

### <a name="build-and-deploy"></a><span data-ttu-id="a97e0-307">빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="a97e0-307">Build and Deploy</span></span>

* <span data-ttu-id="a97e0-308">Unity에서 다시 빌드한 다음, Visual Studio에서 빌드 및 배포 하 여 HoloLens에서 앱을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-308">Rebuild in Unity and then build and deploy from Visual Studio to run the app in HoloLens.</span></span>
* <span data-ttu-id="a97e0-309">HoloLens 앞으로 손을 이동 하 고 추적할 수 있도록 인덱스 손가락을 올립니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-309">Move your hand in front of the HoloLens and raise your index finger so that it can be tracked.</span></span>
* <span data-ttu-id="a97e0-310">Astronaut 위에 커서를 올려 둡니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-310">Focus the cursor over the astronaut.</span></span>
* <span data-ttu-id="a97e0-311">Astronaut를 조작 제스처로 이동 하려면 ' Move Astronaut '를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-311">Say 'Move Astronaut' to move the astronaut with a Manipulation gesture.</span></span>
* <span data-ttu-id="a97e0-312">이제 프로그램에서 조작 이벤트에 응답 하는 것을 나타내기 위해 커서 주위에 네 개의 화살표가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-312">Four arrows should appear around the cursor to indicate that the program will now respond to Manipulation events.</span></span>
* <span data-ttu-id="a97e0-313">인덱스 손가락을 엄지 단추 아래로 낮추고 pinched을 함께 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-313">Lower your index finger down to your thumb, and keep them pinched together.</span></span>
* <span data-ttu-id="a97e0-314">손을 움직이면 astronaut도 이동 합니다 (이는 조작).</span><span class="sxs-lookup"><span data-stu-id="a97e0-314">As you move your hand around, the astronaut will move too (this is Manipulation).</span></span>
* <span data-ttu-id="a97e0-315">Astronaut 조작을 중지 하도록 인덱스 손가락을 올립니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-315">Raise your index finger to stop manipulating the astronaut.</span></span>
* <span data-ttu-id="a97e0-316">참고: 손을 이동 하기 전에 ' Move Astronaut '가 표시 되지 않으면 탐색 제스처가 대신 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-316">Note: If you do not say 'Move Astronaut' before moving your hand, then the Navigation gesture will be used instead.</span></span>
* <span data-ttu-id="a97e0-317">Rotatable 상태로 돌아가려면 ' Astronaut 회전 ' 이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-317">Say 'Rotate Astronaut' to return to the rotatable state.</span></span>

## <a name="chapter-5---model-expansion"></a><span data-ttu-id="a97e0-318">5 장-모델 확장</span><span class="sxs-lookup"><span data-stu-id="a97e0-318">Chapter 5 - Model expansion</span></span>

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a><span data-ttu-id="a97e0-319">목표</span><span class="sxs-lookup"><span data-stu-id="a97e0-319">Objectives</span></span>

* <span data-ttu-id="a97e0-320">Astronaut 모델을 사용자가 상호 작용할 수 있는 여러 개의 작은 조각으로 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-320">Expand the Astronaut model into multiple, smaller pieces that the user can interact with.</span></span>
* <span data-ttu-id="a97e0-321">탐색 및 조작 제스처를 사용 하 여 각 부분을 개별적으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-321">Move each piece individually using Navigation and Manipulation gestures.</span></span>

### <a name="instructions"></a><span data-ttu-id="a97e0-322">지침</span><span class="sxs-lookup"><span data-stu-id="a97e0-322">Instructions</span></span>

<span data-ttu-id="a97e0-323">이 섹션에서는 다음 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-323">In this section, we will accomplish the following tasks:</span></span>

1. <span data-ttu-id="a97e0-324">새 "**모델 확장**" 키워드를 추가 하 여 astronaut 모델을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-324">Add a new keyword "**Expand Model**" to expand the astronaut model.</span></span>
2. <span data-ttu-id="a97e0-325">새 키워드 "**모델 다시 설정**"을 추가 하 여 모델을 원래 형식으로 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-325">Add a new Keyword "**Reset Model**" to return the model to its original form.</span></span>

<span data-ttu-id="a97e0-326">이전 장의 음성 입력 소스에 두 개 이상의 키워드를 추가 하 여이 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-326">We'll do this by adding two more keywords to the Speech Input Source from the previous chapter.</span></span> <span data-ttu-id="a97e0-327">또한 인식 이벤트를 처리 하는 또 다른 방법을 보여 드리겠습니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-327">We'll also demonstrate another way to handle recognition events.</span></span>

1. <span data-ttu-id="a97e0-328">**검사기** 에서 **AstronautManager** 를 클릭 하 고 **검사기**에서 **키워드** 섹션을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-328">Click back on **AstronautManager** in the **Inspector** and expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="a97e0-329">오른쪽의 **+** 를 클릭 하 여 새 키워드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-329">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="a97e0-330">키워드를 **확장 모델**로 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-330">Type the Keyword as **Expand Model**.</span></span> <span data-ttu-id="a97e0-331">원한다 면 키 바로 가기를 자유롭게 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-331">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="a97e0-332">오른쪽의 **+** 를 클릭 하 여 새 키워드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-332">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="a97e0-333">키워드를 **모델 다시 설정**으로 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-333">Type the Keyword as **Reset Model**.</span></span> <span data-ttu-id="a97e0-334">원한다 면 키 바로 가기를 자유롭게 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-334">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="a97e0-335">**검사기** 패널에서 **구성 요소 추가** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-335">In the **Inspector** panel, click the **Add Component** button.</span></span>
7. <span data-ttu-id="a97e0-336">메뉴의 검색 상자에 **음성 입력 처리기**를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-336">In the menu, type in the search box **Speech Input Handler**.</span></span> <span data-ttu-id="a97e0-337">검색 결과를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-337">Select the search result.</span></span>
8. <span data-ttu-id="a97e0-338">이 명령은 GameObject에 관계 없이 작동 하기 때문에 **전역 수신기**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-338">Check **Is Global Listener**, since we want these commands to work regardless of the GameObject we're focusing.</span></span>
9. <span data-ttu-id="a97e0-339">단추를 **+** 클릭 하 고 키워드 드롭다운에서 **모델 확장** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-339">Click the **+** button and select **Expand Model** from the Keyword dropdown.</span></span>
10. <span data-ttu-id="a97e0-340">응답 아래를 클릭 하 고 계층의 **AstronautManager** 을 **None (Object)** 필드로 끕니다.  **+**</span><span class="sxs-lookup"><span data-stu-id="a97e0-340">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
11. <span data-ttu-id="a97e0-341">이제 **함수 없음** 드롭다운을 클릭 하 고 **AstronautManager**, **ExpandModelCommand**를 차례로 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-341">Now, click the **No Function** dropdown, select **AstronautManager**, then **ExpandModelCommand**.</span></span>
12. <span data-ttu-id="a97e0-342">음성 입력 처리기의 **+** 단추를 클릭 하 고 키워드 드롭다운에서 **모델 다시 설정** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-342">Click the Speech Input Handler's **+** button and select **Reset Model** from the Keyword dropdown.</span></span>
13. <span data-ttu-id="a97e0-343">응답 아래를 클릭 하 고 계층의 **AstronautManager** 을 **None (Object)** 필드로 끕니다.  **+**</span><span class="sxs-lookup"><span data-stu-id="a97e0-343">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
14. <span data-ttu-id="a97e0-344">이제 **함수 없음** 드롭다운을 클릭 하 고 **AstronautManager**, **resetmodelcommand**를 차례로 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-344">Now, click the **No Function** dropdown, select **AstronautManager**, then **ResetModelCommand**.</span></span>

![5 장의 음성 입력 소스 및 처리기를 설정 하는 방법](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a><span data-ttu-id="a97e0-346">빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="a97e0-346">Build and Deploy</span></span>

* <span data-ttu-id="a97e0-347">시도해 보세요.</span><span class="sxs-lookup"><span data-stu-id="a97e0-347">Try it!</span></span> <span data-ttu-id="a97e0-348">앱을 빌드하고 HoloLens에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-348">Build and deploy the app to the HoloLens.</span></span>
* <span data-ttu-id="a97e0-349">**모델을 확장** 하 여 확장 된 astronaut 모델을 표시 한다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-349">Say **Expand Model** to see the expanded astronaut model.</span></span>
* <span data-ttu-id="a97e0-350">**탐색** 을 사용 하 여 astronaut 짝패의 개별 부분을 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-350">Use **Navigation** to rotate individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="a97e0-351">**Astronaut를 이동한** 다음 **조작** 을 사용 하 여 Astronaut 짝패의 개별 부분을 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-351">Say **Move Astronaut** and then use **Manipulation** to move individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="a97e0-352">**Astronaut를 회전** 하 여 조각을 다시 회전 한다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-352">Say **Rotate Astronaut** to rotate the pieces again.</span></span>
* <span data-ttu-id="a97e0-353">**모델을 다시 설정** 하 여 원래 형식으로 astronaut를 반환 한다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-353">Say **Reset Model** to return the astronaut to its original form.</span></span>

## <a name="the-end"></a><span data-ttu-id="a97e0-354">끝</span><span class="sxs-lookup"><span data-stu-id="a97e0-354">The End</span></span>

<span data-ttu-id="a97e0-355">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-355">Congratulations!</span></span> <span data-ttu-id="a97e0-356">이제 MR 입력 211 **을 완료 했습니다. 제스처**.</span><span class="sxs-lookup"><span data-stu-id="a97e0-356">You have now completed **MR Input 211: Gesture**.</span></span>

* <span data-ttu-id="a97e0-357">직접 추적, 탐색 및 조작 이벤트를 검색 하 고 대응 하는 방법을 알고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-357">You know how to detect and respond to hand tracking, navigation and manipulation events.</span></span>
* <span data-ttu-id="a97e0-358">탐색 제스처와 조작 제스처의 차이점을 이해 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-358">You understand the difference between Navigation and Manipulation gestures.</span></span>
* <span data-ttu-id="a97e0-359">커서를 변경 하 여 손을 감지 했을 때, 손을 잃어 버릴 때, 개체가 서로 다른 상호 작용을 지 원하는 경우 (탐색 vs 조작)에 대 한 시각적 피드백을 제공 하도록 커서를 변경 하는 방법을 알고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a97e0-359">You know how to change the cursor to provide visual feedback for when a hand is detected, when a hand is about to be lost, and for when an object supports different interactions (Navigation vs Manipulation).</span></span>
