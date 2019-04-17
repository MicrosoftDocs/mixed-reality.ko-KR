---
title: MR 입력 211-제스처
description: Unity에서 Visual Studio 및 HoloLens를 사용 하 여 제스처 개념의 세부 정보를 알아보려면이 코딩 연습을 수행 합니다.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit mixedrealitytoolkit, mixedrealitytoolkit unity, academy, 자습서, 제스처
ms.openlocfilehash: 76d2b4c0ac3d0a3783b091f7dc8c39548a18b548
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603385"
---
>[!NOTE]
><span data-ttu-id="890b8-104">혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="890b8-105">따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="890b8-106">이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="890b8-107">지원 되는 장치에서 작업을 계속 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="890b8-108">새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="890b8-109">게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-input-211-gesture"></a><span data-ttu-id="890b8-110">MR 입력 211: 제스처</span><span class="sxs-lookup"><span data-stu-id="890b8-110">MR Input 211: Gesture</span></span>

<span data-ttu-id="890b8-111">[제스처](gestures.md) 사용자 의도 작업으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-111">[Gestures](gestures.md) turn user intention into action.</span></span> <span data-ttu-id="890b8-112">제스처를 사용 하 여 사용자 홀로그램 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-112">With gestures, users can interact with holograms.</span></span> <span data-ttu-id="890b8-113">이 과정에서는 사용자의 손에 추적, 사용자 입력에 응답 하는 방법을 알아보겠습니다 및 사용자에 게 피드백 상태 및 위치 가까이 기반 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-113">In this course, we'll learn how to track the user's hands, respond to user input, and give feedback to the user based on hand state and location.</span></span>

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

<span data-ttu-id="890b8-114">[MR 기본 사항 101](holograms-101.md), 우리의 홀로그램와 상호 작용 하는 간단한 어 탭 제스처를 사용 했습니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-114">In [MR Basics 101](holograms-101.md), we used a simple air-tap gesture to interact with our holograms.</span></span> <span data-ttu-id="890b8-115">이제 어 탭 제스처를 넘어 이동 하 고 새로운 개념을 탐색 드리겠습니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-115">Now, we'll move beyond the air-tap gesture and explore new concepts to:</span></span>

* <span data-ttu-id="890b8-116">사용자의 직접 추적 중인 경우를 감지 및 사용자에 게 피드백을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-116">Detect when the user's hand is being tracked and provide feedback to the user.</span></span>
* <span data-ttu-id="890b8-117">우리의 홀로그램을 회전 하려면 탐색 제스처를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-117">Use a navigation gesture to rotate our holograms.</span></span>
* <span data-ttu-id="890b8-118">사용자의 직접 보기에서 이동 하려고 할 때 피드백을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-118">Provide feedback when the user's hand is about to go out of view.</span></span>
* <span data-ttu-id="890b8-119">조작 이벤트를 사용 하 여 홀로그램 알아내기란을 사용 하 여 이동할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-119">Use manipulation events to allow users to move holograms with their hands.</span></span>

<span data-ttu-id="890b8-120">이 과정에서 Unity 프로젝트를 다시 방문할 예정 **모델 탐색기**, 구축한입니다 [MR 입력 210](holograms-210.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-120">In this course, we'll revisit the Unity project **Model Explorer**, which we built in [MR Input 210](holograms-210.md).</span></span> <span data-ttu-id="890b8-121">우리의 고상한 friend가 이러한 새 제스처 개념의 탐색 지원 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-121">Our astronaut friend is back to assist us in our exploration of these new gesture concepts.</span></span>

>[!IMPORTANT]
><span data-ttu-id="890b8-122">각 아래 단원에 포함 된 비디오는 이전 버전의 Unity 및 혼합 현실 도구 키트를 사용 하 여 기록 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-122">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="890b8-123">단계별 지침을 정확 하 고 현재는, 스크립트 및 만료 된 해당 동영상의 시각적 개체를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-123">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="890b8-124">비디오는 두세요 포함 상태를 유지 및 개념 설명 하기 때문에 계속 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-124">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="890b8-125">장치 지원</span><span class="sxs-lookup"><span data-stu-id="890b8-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="890b8-126">과정</span><span class="sxs-lookup"><span data-stu-id="890b8-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="890b8-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="890b8-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="890b8-128"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="890b8-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="890b8-129">MR 입력 211: 제스처</span><span class="sxs-lookup"><span data-stu-id="890b8-129">MR Input 211: Gesture</span></span></td><td style="text-align: center;"> <span data-ttu-id="890b8-130">✔️</span><span class="sxs-lookup"><span data-stu-id="890b8-130">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="890b8-131">✔️</span><span class="sxs-lookup"><span data-stu-id="890b8-131">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="890b8-132">시작하기 전 주의 사항</span><span class="sxs-lookup"><span data-stu-id="890b8-132">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="890b8-133">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="890b8-133">Prerequisites</span></span>

* <span data-ttu-id="890b8-134">올바른를 사용 하 여 구성 하는 Windows 10 PC [도구가 설치 되어](install-the-tools.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-134">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>
* <span data-ttu-id="890b8-135">기본적인 C# 기능을 프로그래밍 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-135">Some basic C# programming ability.</span></span>
* <span data-ttu-id="890b8-136">완료 해야 [MR 기본 사항 101](holograms-101.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-136">You should have completed [MR Basics 101](holograms-101.md).</span></span>
* <span data-ttu-id="890b8-137">완료 해야 [MR 입력 210](holograms-210.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-137">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="890b8-138">HoloLens 장치 [개발에 대해 구성 된](using-visual-studio.md#enabling-developer-mode)합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-138">A HoloLens device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="890b8-139">프로젝트 파일</span><span class="sxs-lookup"><span data-stu-id="890b8-139">Project files</span></span>

* <span data-ttu-id="890b8-140">다운로드 합니다 [파일](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) 프로젝트에서 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-140">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) required by the project.</span></span><span data-ttu-id="890b8-141"> Unity 2017.2 이상이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-141"> Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="890b8-142">취소 보관 파일을 데스크톱 또는 기타 쉽게 달성할 수 있습니다 위치 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-142">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="890b8-143">을 다운로드 하기 전에 소스 코드를 확인 하려는 경우 있기 [GitHub에서 사용할 수 있는](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture)합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-143">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="890b8-144">오류 및 정보</span><span class="sxs-lookup"><span data-stu-id="890b8-144">Errata and Notes</span></span>

* <span data-ttu-id="890b8-145">사용 하지 않도록 설정할 필요 "내 코드만 사용" (*unchecked*)-> 도구 아래에서 Visual Studio에서 코드에서 중단점을 적중 하려면-> 디버깅 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-145">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-0---unity-setup"></a><span data-ttu-id="890b8-146">장 0-Unity 설치</span><span class="sxs-lookup"><span data-stu-id="890b8-146">Chapter 0 - Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="890b8-147">지침</span><span class="sxs-lookup"><span data-stu-id="890b8-147">Instructions</span></span>

1. <span data-ttu-id="890b8-148">Unity를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-148">Start Unity.</span></span>
2. <span data-ttu-id="890b8-149">선택 **열려**합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-149">Select **Open**.</span></span>
3. <span data-ttu-id="890b8-150">로 이동 합니다 **제스처** 폴더 되지 않은 보관 된 이전에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-150">Navigate to the **Gesture** folder you previously un-archived.</span></span>
4. <span data-ttu-id="890b8-151">찾기 및 선택 합니다 **터**/**모델 탐색기** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-151">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="890b8-152">클릭 합니다 **폴더 선택** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-152">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="890b8-153">에 **프로젝트** 패널을 확장 합니다 **장면** 폴더.</span><span class="sxs-lookup"><span data-stu-id="890b8-153">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="890b8-154">두 번 클릭 **ModelExplorer** 장면 Unity에 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-154">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="890b8-155">빌드</span><span class="sxs-lookup"><span data-stu-id="890b8-155">Building</span></span>

1. <span data-ttu-id="890b8-156">Unity에서 선택 **파일 > 빌드 설정**합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-156">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="890b8-157">하는 경우 **장면/ModelExplorer** 에 나열 되지 **Scenes In Build**, 클릭 **열기 장면 추가** 장면에 추가할 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-157">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="890b8-158">HoloLens에 대 한 구체적으로 개발 하는 경우 설정 **대상 장치** 하 **HoloLens**합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-158">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="890b8-159">그렇지 않으면 켜져 **모든 장치**합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-159">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="890b8-160">확인 **빌드 형식** 로 설정 된 **D3D** 하 고 **SDK** 로 설정 되어 **가장 최근에 설치 된** (16299 또는 최신 SDK는 이어야 함).</span><span class="sxs-lookup"><span data-stu-id="890b8-160">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="890b8-161">**빌드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-161">Click **Build**.</span></span>
6. <span data-ttu-id="890b8-162">만들기는 **새 폴더** 이름을 "App"입니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-162">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="890b8-163">한 번 클릭 합니다 **앱** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-163">Single click the **App** folder.</span></span>
8. <span data-ttu-id="890b8-164">키를 눌러 **폴더 선택** Unity for Visual Studio 프로젝트를 빌드하기 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-164">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="890b8-165">Unity 완료 되 면 파일 탐색기 창이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-165">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="890b8-166">엽니다는 **앱** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-166">Open the **App** folder.</span></span>
2. <span data-ttu-id="890b8-167">엽니다는 **ModelExplorer Visual Studio 솔루션**합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-167">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="890b8-168">HoloLens 배포 하는 경우:</span><span class="sxs-lookup"><span data-stu-id="890b8-168">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="890b8-169">에 디버그 대상 변경 맨 위의 도구 모음을 사용 하 여 Visual Studio에서 **릴리스** 들어오고를 ARM **x86**합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-169">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="890b8-170">드롭다운 로컬 컴퓨터 단추 옆의 화살표를 클릭 하 고 선택 **원격 컴퓨터**합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-170">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="890b8-171">입력 **HoloLens 장치 IP 주소** 인증 모드를 설정 하 고 **유니버설 (암호화 되지 않은 프로토콜)** 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-171">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="890b8-172">클릭 **선택**합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-172">Click **Select**.</span></span> <span data-ttu-id="890b8-173">장치 IP 주소를 모르는 경우 찾는 위치 **설정 > 네트워크 및 인터넷 > 고급 옵션**합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-173">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="890b8-174">맨 위 메뉴 모음에서 클릭 **디버그-> 디버깅 없이 시작** 누르거나 **ctrl+f5**합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-174">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="890b8-175">처음으로 장치에 배포할 경우 해야 [Visual Studio를 사용 하 여 쌍](using-visual-studio.md#pairing-your-device-hololens)합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-175">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](using-visual-studio.md#pairing-your-device-hololens).</span></span>
5. <span data-ttu-id="890b8-176">앱에 배포 하는 경우 해제 합니다 **Fitbox** 사용 하 여를 **제스처 선택**.</span><span class="sxs-lookup"><span data-stu-id="890b8-176">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="890b8-177">경우는 몰입 형 헤드셋에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-177">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="890b8-178">에 디버그 대상 변경 맨 위의 도구 모음을 사용 하 여 Visual Studio에서 **릴리스** 들어오고를 ARM **x64**합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-178">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="890b8-179">배포 대상 설정 되어 있는지 확인 **로컬 컴퓨터**합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-179">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="890b8-180">맨 위 메뉴 모음에서 클릭 **디버그-> 디버깅 없이 시작** 누르거나 **ctrl+f5**합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-180">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="890b8-181">앱에 배포 하는 경우 해제 합니다 **Fitbox** 동작 컨트롤러에서 트리거를 풀링 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-181">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="890b8-182">Visual Studio 오류 패널에서 빨간색 일부 오류를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-182">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="890b8-183">무시 해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-183">It is safe to ignore them.</span></span> <span data-ttu-id="890b8-184">스위치를 실제 보려면 출력 패널에 빌드 진행률입니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-184">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="890b8-185">출력 패널에는 오류 (가장 일반적으로 스크립트를이 잘못 되어 발생)을 수정 해야 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-185">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---hand-detected-feedback"></a><span data-ttu-id="890b8-186">1 장-직접 사용자 의견 검색</span><span class="sxs-lookup"><span data-stu-id="890b8-186">Chapter 1 - Hand detected feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a><span data-ttu-id="890b8-187">목표</span><span class="sxs-lookup"><span data-stu-id="890b8-187">Objectives</span></span>

* <span data-ttu-id="890b8-188">추적 이벤트를 전달 하는 데 구독 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-188">Subscribe to hand tracking events.</span></span>
* <span data-ttu-id="890b8-189">손 모양 추적 되는 경우 사용자가 표시할 커서 피드백을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-189">Use cursor feedback to show users when a hand is being tracked.</span></span>

### <a name="instructions"></a><span data-ttu-id="890b8-190">지침</span><span class="sxs-lookup"><span data-stu-id="890b8-190">Instructions</span></span>

* <span data-ttu-id="890b8-191">에 **계층** 패널을 확장 합니다 **InputManager** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-191">In the **Hierarchy** panel, expand the **InputManager** object.</span></span>
* <span data-ttu-id="890b8-192">찾아 선택 합니다 **GesturesInput** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-192">Look for and select the **GesturesInput** object.</span></span>

<span data-ttu-id="890b8-193">합니다 **InteractionInputSource.cs** 스크립트는 두이 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-193">The **InteractionInputSource.cs** script performs these steps:</span></span>

1. <span data-ttu-id="890b8-194">InteractionSourceDetected 및 InteractionSourceLost 이벤트를 구독합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-194">Subscribes to the InteractionSourceDetected and InteractionSourceLost events.</span></span>
2. <span data-ttu-id="890b8-195">HandDetected 상태를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-195">Sets the HandDetected state.</span></span>
3. <span data-ttu-id="890b8-196">InteractionSourceDetected 및 InteractionSourceLost 이벤트에서이 구독을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-196">Unsubscribes from the InteractionSourceDetected and InteractionSourceLost events.</span></span>

<span data-ttu-id="890b8-197">에서는 커서에서 업그레이드에서는 어 [MR 입력 210](holograms-210.md) 사용자 작업에 따라 피드백을 보여 주는 하나로 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-197">Next, we'll upgrade our cursor from [MR Input 210](holograms-210.md) into one that shows feedback depending on the user's actions.</span></span>

1. <span data-ttu-id="890b8-198">에 **계층 구조** 패널에서 합니다 **커서** 개체를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-198">In the **Hierarchy** panel, select the **Cursor** object and delete it.</span></span>
2. <span data-ttu-id="890b8-199">에 **프로젝트** 패널에서 검색할 **CursorWithFeedback** 으로 끌어 놓습니다 합니다 **계층** 패널입니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-199">In the **Project** panel, search for **CursorWithFeedback** and drag it into the **Hierarchy** panel.</span></span>
3. <span data-ttu-id="890b8-200">클릭할 **InputManager** 에 **계층** 패널 다음 끌어를 **CursorWithFeedback** 에서 개체를 **계층** 에 InputManager의 **SimpleSinglePointerSelector**의 **커서** 맨 아래에 필드를 **검사기**합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-200">Click on **InputManager** in the **Hierarchy** panel, then drag the **CursorWithFeedback** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>
4. <span data-ttu-id="890b8-201">클릭 합니다 **CursorWithFeedback** 에 **계층**합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-201">Click on the **CursorWithFeedback** in the **Hierarchy**.</span></span>
5. <span data-ttu-id="890b8-202">에 **검사기** 패널에서 확장 **커서 상태 데이터** 에 **개체 커서** 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-202">In the **Inspector** panel, expand **Cursor State Data** on the **Object Cursor** script.</span></span>

<span data-ttu-id="890b8-203">합니다 **커서 상태 데이터** 이 처럼 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-203">The **Cursor State Data** works like this:</span></span>

* <span data-ttu-id="890b8-204">모든 **관찰** 상태 없습니다 직접 검색 하 고 사용자는 단순히 확인 하는 것을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-204">Any **Observe** state means that no hand is detected and the user is simply looking around.</span></span>
* <span data-ttu-id="890b8-205">모든 **상호 작용** 상태는 직접 또는 컨트롤러 검색 되는 것을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-205">Any **Interact** state means that a hand or controller is detected.</span></span>
* <span data-ttu-id="890b8-206">모든 **호버** 상태를 홀로그램에서 사용자가 보는 것을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-206">Any **Hover** state means the user is looking at a hologram.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="890b8-207">빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="890b8-207">Build and Deploy</span></span>

* <span data-ttu-id="890b8-208">Unity를 사용 하 여 **파일 > 빌드 설정** 응용 프로그램을 다시 작성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-208">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="890b8-209">엽니다는 **앱** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-209">Open the **App** folder.</span></span>
* <span data-ttu-id="890b8-210">열려 있지 않으면 엽니다는 **ModelExplorer Visual Studio 솔루션**합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-210">If it's not already open, open the **ModelExplorer Visual Studio Solution**.</span></span>
  * <span data-ttu-id="890b8-211">(이미 빌드된/을 배포한 경우 Visual Studio에서이 프로젝트를 설정 하는 동안 다음 수 VS의 해당 인스턴스를 열고 ' 모두 다시 로드 ' 메시지가 표시 되 면 클릭).</span><span class="sxs-lookup"><span data-stu-id="890b8-211">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>
* <span data-ttu-id="890b8-212">Visual Studio에서 클릭 **디버그-> 디버깅 없이 시작** 누르거나 **ctrl+f5**합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-212">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="890b8-213">응용 프로그램을 HoloLens를 배포한 후에 어 탭 제스처를 사용 하 여 fitbox를 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-213">After the application deploys to the HoloLens, dismiss the fitbox using the air-tap gesture.</span></span>
* <span data-ttu-id="890b8-214">보기로 직접 이동 하 고 직접 추적을 시작 하려면 하늘을 집게 손가락을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-214">Move your hand into view and point your index finger to the sky to start hand tracking.</span></span>
* <span data-ttu-id="890b8-215">왼쪽으로 직접 이동, 오른쪽, 위쪽 및 아래쪽 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-215">Move your hand left, right, up and down.</span></span>
* <span data-ttu-id="890b8-216">직접 검색 되어 다음 보기에서 손실 된 경우 커서가 어떻게 변경 하는지 시청 하세요.</span><span class="sxs-lookup"><span data-stu-id="890b8-216">Watch how the cursor changes when your hand is detected and then lost from view.</span></span>
* <span data-ttu-id="890b8-217">몰입 형 헤드셋을 사용 하는 경우에 연결 및 컨트롤러를 분리 하는 것이 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-217">If you're on an immersive headset, you'll have to connect and disconnect your controller.</span></span> <span data-ttu-id="890b8-218">연결 된 컨트롤러를 "제공 가능한"은 항상이 피드백 몰입 형 장치에서 덜 관심 있는 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-218">This feedback becomes less interesting on an immersive device, as a connected controller will always be "available".</span></span>

## <a name="chapter-2---navigation"></a><span data-ttu-id="890b8-219">2 장-탐색</span><span class="sxs-lookup"><span data-stu-id="890b8-219">Chapter 2 - Navigation</span></span>

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a><span data-ttu-id="890b8-220">목표</span><span class="sxs-lookup"><span data-stu-id="890b8-220">Objectives</span></span>

* <span data-ttu-id="890b8-221">고상한을 회전 하려면 탐색 제스처 이벤트를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-221">Use Navigation gesture events to rotate the astronaut.</span></span>

### <a name="instructions"></a><span data-ttu-id="890b8-222">지침</span><span class="sxs-lookup"><span data-stu-id="890b8-222">Instructions</span></span>

<span data-ttu-id="890b8-223">앱에서 탐색 제스처를 사용 하려면 하겠습니다 편집 **GestureAction.cs** 탐색 제스처 발생 하는 경우 개체를 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-223">To use Navigation gestures in our app, we are going to edit **GestureAction.cs** to rotate objects when the Navigation gesture occurs.</span></span> <span data-ttu-id="890b8-224">또한 피드백 탐색 사용할 때 표시할 커서를 추가 하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-224">Additionally, we'll add feedback to the cursor to display when Navigation is available.</span></span>

1. <span data-ttu-id="890b8-225">에 **계층 구조** 패널에서 확장 **CursorWithFeedback**합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-225">In the **Hierarchy** panel, expand **CursorWithFeedback**.</span></span>
2. <span data-ttu-id="890b8-226">에 **홀로그램** 폴더를 찾기는 **ScrollFeedback** 자산입니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-226">In the **Holograms** folder, find the **ScrollFeedback** asset.</span></span>
3. <span data-ttu-id="890b8-227">끌어서 놓기는 **ScrollFeedback** 으로 prefab 합니다 **CursorWithFeedback** GameObject를 **계층**.</span><span class="sxs-lookup"><span data-stu-id="890b8-227">Drag and drop the **ScrollFeedback** prefab onto the **CursorWithFeedback** GameObject in the **Hierarchy**.</span></span>
4. <span data-ttu-id="890b8-228">클릭할 **CursorWithFeedback**합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-228">Click on **CursorWithFeedback**.</span></span>
5. <span data-ttu-id="890b8-229">에 **검사기** 패널에서 합니다 **구성 요소 추가** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-229">In the **Inspector** panel, click the **Add Component** button.</span></span>
6. <span data-ttu-id="890b8-230">메뉴에서 검색 상자에 입력 **CursorFeedback**합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-230">In the menu, type in the search box **CursorFeedback**.</span></span> <span data-ttu-id="890b8-231">검색 결과 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-231">Select the search result.</span></span>
7. <span data-ttu-id="890b8-232">끌어서 놓기 합니다 **ScrollFeedback** 에서 개체를 **계층** 에 **게임 개체를 검색 하는 스크롤** 속성에는 **커서 피드백**구성 요소를 **검사기**합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-232">Drag and drop the **ScrollFeedback** object from the **Hierarchy** onto the **Scroll Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>
8. <span data-ttu-id="890b8-233">에 **계층** 패널을 선택 합니다 **AstroMan** 개체.</span><span class="sxs-lookup"><span data-stu-id="890b8-233">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
9. <span data-ttu-id="890b8-234">에 **검사기** 패널에서 합니다 **구성 요소 추가** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-234">In the **Inspector** panel, click the **Add Component** button.</span></span>
10. <span data-ttu-id="890b8-235">메뉴에서 검색 상자에 입력 **제스처 작업**합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-235">In the menu, type in the search box **Gesture Action**.</span></span> <span data-ttu-id="890b8-236">검색 결과 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-236">Select the search result.</span></span>

<span data-ttu-id="890b8-237">다음으로 열기 **GestureAction.cs** Visual Studio에서.</span><span class="sxs-lookup"><span data-stu-id="890b8-237">Next, open **GestureAction.cs** in Visual Studio.</span></span> <span data-ttu-id="890b8-238">코딩 2.c 실행, 다음을 수행 하는 스크립트를 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-238">In coding exercise 2.c, edit the script to do the following:</span></span>

1. <span data-ttu-id="890b8-239">**회전 된 AstroMan** 탐색 제스처가 수행 될 때마다 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-239">**Rotate the AstroMan** object whenever a Navigation gesture is performed.</span></span>
2. <span data-ttu-id="890b8-240">계산 합니다 **rotationFactor** 개체에 적용 되는 회전의 양을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-240">Calculate the **rotationFactor** to control the amount of rotation applied to the object.</span></span>
3. <span data-ttu-id="890b8-241">**개체를 회전** y 축 왼쪽 또는 오른쪽 속속들이 이동할 때.</span><span class="sxs-lookup"><span data-stu-id="890b8-241">**Rotate the object** around the y-axis when the user moves their hand left or right.</span></span>

<span data-ttu-id="890b8-242">전체 코딩 연습 2.c 스크립트 또는 코드 완료 된 솔루션 아래 코드로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-242">Complete coding exercises 2.c in the script, or replace the code with the completed solution below:</span></span>

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

<span data-ttu-id="890b8-243">다른 탐색 이벤트를 몇 가지 정보를 사용 하 여 이미 입력 된 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-243">You'll notice that the other navigation events are already filled in with some info.</span></span> <span data-ttu-id="890b8-244">도구 키트의 끌어다 GameObject를 푸시 했습니다 InputSystem의 모달 스택, 회전 시작 되 면는 고상한에 초점을 유지 하기 위해 사용자 포함 되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-244">We push the GameObject onto the Toolkit's InputSystem's modal stack, so the user doesn't have to maintain focus on the Astronaut once rotation has begun.</span></span> <span data-ttu-id="890b8-245">마찬가지로, 제스처 완료 되 면 스택에서 GameObject를 팝 했습니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-245">Correspondingly, we pop the GameObject off the stack once the gesture is completed.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="890b8-246">빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="890b8-246">Build and Deploy</span></span>

1. <span data-ttu-id="890b8-247">Unity에서 응용 프로그램을 다시 빌드 및는 HoloLens에서 실행 하려면 Visual Studio에서 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-247">Rebuild the application in Unity and then build and deploy from Visual Studio to run it in the HoloLens.</span></span>
2. <span data-ttu-id="890b8-248">커서의 어느 쪽에 두 개의 화살표가 나타납니다 고상한을 응시 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-248">Gaze at the astronaut, two arrows should appear on either side of the cursor.</span></span> <span data-ttu-id="890b8-249">이 새로운 시각적 개체는 고상한 회전할 수 있는지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-249">This new visual indicates that the astronaut can be rotated.</span></span>
3. <span data-ttu-id="890b8-250">준비 위치 (집게 손가락 하늘 향함)에 직접 배치는 HoloLens 직접 추적 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-250">Place your hand in the ready position (index finger pointed towards the sky) so the HoloLens will start tracking your hand.</span></span>
4. <span data-ttu-id="890b8-251">고상한을 회전 하려면 집게 손가락의 축소 위치로 줄이고 왼쪽 또는 오른쪽 NavigationX 제스처를 트리거할으로 직접 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-251">To rotate the astronaut, lower your index finger to a pinch position, and then move your hand left or right to trigger the NavigationX gesture.</span></span>

## <a name="chapter-3---hand-guidance"></a><span data-ttu-id="890b8-252">3 장-직접 지침</span><span class="sxs-lookup"><span data-stu-id="890b8-252">Chapter 3 - Hand Guidance</span></span>

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a><span data-ttu-id="890b8-253">목표</span><span class="sxs-lookup"><span data-stu-id="890b8-253">Objectives</span></span>

* <span data-ttu-id="890b8-254">사용 하 여 **지침 점수를 전달** 직접 추적 손실 됩니다 예측할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-254">Use **hand guidance score** to help predict when hand tracking will be lost.</span></span>
* <span data-ttu-id="890b8-255">제공 **커서에 대 한 피드백** 사용자의 직접 보기의 카메라의 가장자리를가 하는 경우를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-255">Provide **feedback on the cursor** to show when the user's hand nears the camera's edge of view.</span></span>

### <a name="instructions"></a><span data-ttu-id="890b8-256">지침</span><span class="sxs-lookup"><span data-stu-id="890b8-256">Instructions</span></span>

1. <span data-ttu-id="890b8-257">에 **계층** 패널을 선택 합니다 **CursorWithFeedback** 개체.</span><span class="sxs-lookup"><span data-stu-id="890b8-257">In the **Hierarchy** panel, select the **CursorWithFeedback** object.</span></span>
2. <span data-ttu-id="890b8-258">에 **검사기** 패널에서 합니다 **구성 요소 추가** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-258">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="890b8-259">메뉴에서 검색 상자에 입력 **손 지침**합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-259">In the menu, type in the search box **Hand Guidance**.</span></span> <span data-ttu-id="890b8-260">검색 결과 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-260">Select the search result.</span></span>
4. <span data-ttu-id="890b8-261">에 **프로젝트** 패널 **홀로그램** 폴더를 찾기는 **HandGuidanceFeedback** 자산입니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-261">In the **Project** panel **Holograms** folder, find the **HandGuidanceFeedback** asset.</span></span>
5. <span data-ttu-id="890b8-262">끌어서 놓기는 **HandGuidanceFeedback** 자산에는 **손 지침 표시기** 속성에는 **검사기** 패널입니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-262">Drag and drop the **HandGuidanceFeedback** asset onto the **Hand Guidance Indicator** property in the **Inspector** panel.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="890b8-263">빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="890b8-263">Build and Deploy</span></span>

* <span data-ttu-id="890b8-264">Unity에서 응용 프로그램을 다시 빌드 및 HoloLens에 앱을 Visual Studio에서 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-264">Rebuild the application in Unity and then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="890b8-265">직접 뷰로 가져올 하 고 추적 하려면 집게 손가락을 발생 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-265">Bring your hand into view and raise your index finger to get tracked.</span></span>
* <span data-ttu-id="890b8-266">탐색 제스처와 고상한 회전을 시작 (집게 손가락 및 함께 엄지 단추).</span><span class="sxs-lookup"><span data-stu-id="890b8-266">Start rotating the astronaut with the Navigation gesture (pinch your index finger and thumb together).</span></span>
* <span data-ttu-id="890b8-267">맨 왼쪽, 오른쪽, 위쪽 및 아래쪽 직접을 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-267">Move your hand far left, right, up, and down.</span></span>
* <span data-ttu-id="890b8-268">손 제스처 프레임의 가장자리 만료일이 화살표 옆에 표시 되어야 하는 대로 해당 직접 추적 경고 메시지를 커서 손실 됩니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-268">As your hand nears the edge of the gesture frame, an arrow should appear next to the cursor to warn you that hand tracking will be lost.</span></span> <span data-ttu-id="890b8-269">화살표는 직접 추적 손실 되지 않도록 하기 위해 이동할 방향을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-269">The arrow indicates which direction to move your hand in order to prevent tracking from being lost.</span></span>

## <a name="chapter-4---manipulation"></a><span data-ttu-id="890b8-270">4 장-조작</span><span class="sxs-lookup"><span data-stu-id="890b8-270">Chapter 4 - Manipulation</span></span>

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a><span data-ttu-id="890b8-271">목표</span><span class="sxs-lookup"><span data-stu-id="890b8-271">Objectives</span></span>

* <span data-ttu-id="890b8-272">손으로 고상한 이동할 조작 이벤트를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-272">Use Manipulation events to move the astronaut with your hands.</span></span>
* <span data-ttu-id="890b8-273">사용자 조작에 사용할 수 있습니다 시기를 알 수 있도록 커서에서 피드백을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-273">Provide feedback on the cursor to let the user know when Manipulation can be used.</span></span>

### <a name="instructions"></a><span data-ttu-id="890b8-274">지침</span><span class="sxs-lookup"><span data-stu-id="890b8-274">Instructions</span></span>

<span data-ttu-id="890b8-275">GestureManager.cs 및 AstronautManager.cs 수 있도록 다음 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-275">GestureManager.cs and AstronautManager.cs will allow us to do the following:</span></span>

1. <span data-ttu-id="890b8-276">음성 키워드를 사용 하 여 "**이동 고상한**" 사용할 수 있도록 **조작** 제스처 및 "**회전 고상한**" 비활성화 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-276">Use the speech keyword "**Move Astronaut**" to enable **Manipulation** gestures and "**Rotate Astronaut**" to disable them.</span></span>
2. <span data-ttu-id="890b8-277">응답으로 전환 합니다 **조작 제스처 인식기**합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-277">Switch to responding to the **Manipulation Gesture Recognizer**.</span></span>

<span data-ttu-id="890b8-278">그럼 시작해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-278">Let's get started.</span></span>

1. <span data-ttu-id="890b8-279">에 **계층** 패널에서 새로운 빈 GameObject를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-279">In the **Hierarchy** panel, create a new empty GameObject.</span></span> <span data-ttu-id="890b8-280">Name it "**AstronautManager**".</span><span class="sxs-lookup"><span data-stu-id="890b8-280">Name it "**AstronautManager**".</span></span>
2. <span data-ttu-id="890b8-281">에 **검사기** 패널에서 합니다 **구성 요소 추가** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-281">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="890b8-282">메뉴에서 검색 상자에 입력 **고상한 Manager**합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-282">In the menu, type in the search box **Astronaut Manager**.</span></span> <span data-ttu-id="890b8-283">검색 결과 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-283">Select the search result.</span></span>
4. <span data-ttu-id="890b8-284">에 **검사기** 패널에서 합니다 **구성 요소 추가** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-284">In the **Inspector** panel, click the **Add Component** button.</span></span>
5. <span data-ttu-id="890b8-285">메뉴에서 검색 상자에 입력 **음성 입력 원본**합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-285">In the menu, type in the search box **Speech Input Source**.</span></span> <span data-ttu-id="890b8-286">검색 결과 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-286">Select the search result.</span></span>

<span data-ttu-id="890b8-287">이제는 고상한의 상호 작용 상태를 제어 하는 데 필요한 음성 명령을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-287">We'll now add the speech commands required to control the interaction state of the astronaut.</span></span>

1. <span data-ttu-id="890b8-288">확장 된 **키워드** 섹션을 **검사기**합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-288">Expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="890b8-289">클릭 합니다 **+** 새로운 키워드를 추가 하려면 오른쪽에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-289">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="890b8-290">As 키워드를 입력 **고상한 이동**합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-290">Type the Keyword as **Move Astronaut**.</span></span> <span data-ttu-id="890b8-291">원하는 경우 키 바로 가기를 추가 해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-291">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="890b8-292">클릭 합니다 **+** 새로운 키워드를 추가 하려면 오른쪽에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-292">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="890b8-293">As 키워드를 입력 **고상한 회전**합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-293">Type the Keyword as **Rotate Astronaut**.</span></span> <span data-ttu-id="890b8-294">원하는 경우 키 바로 가기를 추가 해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-294">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="890b8-295">해당 처리기 코드를 찾을 수 있습니다 **GestureAction.cs**를 **ISpeechHandler.OnSpeechKeywordRecognized** 처리기입니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-295">The corresponding handler code can be found in **GestureAction.cs**, in the **ISpeechHandler.OnSpeechKeywordRecognized** handler.</span></span>

![4 장 음성 입력 원본을 설정 하는 방법](images/holograms211-speech.png)

<span data-ttu-id="890b8-297">다음으로 조작 피드백 커서에서 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-297">Next, we'll setup the manipulation feedback on the cursor.</span></span>

1. <span data-ttu-id="890b8-298">에 **프로젝트** 패널 **홀로그램** 폴더를 찾기는 **PathingFeedback** 자산입니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-298">In the **Project** panel **Holograms** folder, find the **PathingFeedback** asset.</span></span>
2. <span data-ttu-id="890b8-299">끌어서 놓기는 **PathingFeedback** 으로 prefab 합니다 **CursorWithFeedback** 개체를 **계층**합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-299">Drag and drop the **PathingFeedback** prefab onto the **CursorWithFeedback** object in the **Hierarchy**.</span></span>
3. <span data-ttu-id="890b8-300">에 **계층 구조** 패널에서 클릭 **CursorWithFeedback**합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-300">In the **Hierarchy** panel, click on **CursorWithFeedback**.</span></span>
4. <span data-ttu-id="890b8-301">끌어서 놓기 합니다 **PathingFeedback** 에서 개체를 **계층** 에 **게임 개체를 검색 하는 경로 지정** 속성에는 **커서 피드백**구성 요소를 **검사기**합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-301">Drag and drop the **PathingFeedback** object from the **Hierarchy** onto the **Pathing Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>

<span data-ttu-id="890b8-302">이제 코드를 추가 해야 **GestureAction.cs** 다음을 사용 하도록 설정 하려면:</span><span class="sxs-lookup"><span data-stu-id="890b8-302">Now we need to add code to **GestureAction.cs** to enable the following:</span></span>

1. <span data-ttu-id="890b8-303">코드를 추가 합니다 **IManipulationHandler.OnManipulationUpdated** 고상한을 이동 하는 함수를 때를 **조작** 제스처가 감지 되 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-303">Add code to the **IManipulationHandler.OnManipulationUpdated** function, which will move the astronaut when a **Manipulation** gesture is detected.</span></span>
2. <span data-ttu-id="890b8-304">계산 된 **이동 벡터** 위치는 고상한 설정할지 결정할 기반 가까이 위치 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-304">Calculate the **movement vector** to determine where the astronaut should be moved to based on hand position.</span></span>
3. <span data-ttu-id="890b8-305">**이동** 의 새 위치로 고상한 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-305">**Move** the astronaut to the new position.</span></span>

<span data-ttu-id="890b8-306">4.a 연습 완료 코딩 **GestureAction.cs**, 하거나 아래 완료 된 솔루션을 사용 하 여:</span><span class="sxs-lookup"><span data-stu-id="890b8-306">Complete coding exercise 4.a in **GestureAction.cs**, or use our completed solution below:</span></span>

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

### <a name="build-and-deploy"></a><span data-ttu-id="890b8-307">빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="890b8-307">Build and Deploy</span></span>

* <span data-ttu-id="890b8-308">Unity에서를 다시 빌드하십시오 빌드 및 HoloLens에 앱을 실행 하려면 Visual Studio에서 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-308">Rebuild in Unity and then build and deploy from Visual Studio to run the app in HoloLens.</span></span>
* <span data-ttu-id="890b8-309">HoloLens 앞에 손을 이동 하 고 추적할 수 있도록 집게 손가락을 발생 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-309">Move your hand in front of the HoloLens and raise your index finger so that it can be tracked.</span></span>
* <span data-ttu-id="890b8-310">고상한 위에 커서를 집중 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-310">Focus the cursor over the astronaut.</span></span>
* <span data-ttu-id="890b8-311">조작 제스처를 사용 하 여 고상한 이동할 ' 고상한 이동 '을 가정해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-311">Say 'Move Astronaut' to move the astronaut with a Manipulation gesture.</span></span>
* <span data-ttu-id="890b8-312">4 방향 화살표는 프로그램이 지금 응답할 조작 이벤트를 나타내기 위해 커서 주위에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-312">Four arrows should appear around the cursor to indicate that the program will now respond to Manipulation events.</span></span>
* <span data-ttu-id="890b8-313">엄지 손가락 아래로 집게 손가락을 절감 하 고 함께 키거나 유지 하세요.</span><span class="sxs-lookup"><span data-stu-id="890b8-313">Lower your index finger down to your thumb, and keep them pinched together.</span></span>
* <span data-ttu-id="890b8-314">직접 주위를 이동 하면는 고상한도 이동 됩니다 (이것이 조작) 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-314">As you move your hand around, the astronaut will move too (this is Manipulation).</span></span>
* <span data-ttu-id="890b8-315">집게 손가락을 고상한 조작 중지를 발생 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-315">Raise your index finger to stop manipulating the astronaut.</span></span>
* <span data-ttu-id="890b8-316">참고: 고상한 이동 ' 직접 이동 하기 전에 라고 하면, 한 탐색 제스처를 대신 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-316">Note: If you do not say 'Move Astronaut' before moving your hand, then the Navigation gesture will be used instead.</span></span>
* <span data-ttu-id="890b8-317">회전식 상태로 돌아갈 ' 고상한 회전 ' 가정해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-317">Say 'Rotate Astronaut' to return to the rotatable state.</span></span>

## <a name="chapter-5---model-expansion"></a><span data-ttu-id="890b8-318">5 장-모델 확장</span><span class="sxs-lookup"><span data-stu-id="890b8-318">Chapter 5 - Model expansion</span></span>

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a><span data-ttu-id="890b8-319">목표</span><span class="sxs-lookup"><span data-stu-id="890b8-319">Objectives</span></span>

* <span data-ttu-id="890b8-320">여러 고상한 모델을 확장 하 고, 더 작은 부분을 사용자가 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-320">Expand the Astronaut model into multiple, smaller pieces that the user can interact with.</span></span>
* <span data-ttu-id="890b8-321">개별적으로 탐색 및 조작 제스처를 사용 하 여 각 부분을 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-321">Move each piece individually using Navigation and Manipulation gestures.</span></span>

### <a name="instructions"></a><span data-ttu-id="890b8-322">지침</span><span class="sxs-lookup"><span data-stu-id="890b8-322">Instructions</span></span>

<span data-ttu-id="890b8-323">이 섹션에서는에서는 다음 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-323">In this section, we will accomplish the following tasks:</span></span>

1. <span data-ttu-id="890b8-324">새 키워드를 추가 합니다. "**확장 모델**" 고상한 모델을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-324">Add a new keyword "**Expand Model**" to expand the astronaut model.</span></span>
2. <span data-ttu-id="890b8-325">새 키워드를 추가 합니다. "**재설정 모델**" 원래 형태로 모델을 반환 하 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-325">Add a new Keyword "**Reset Model**" to return the model to its original form.</span></span>

<span data-ttu-id="890b8-326">이전 장에서 음성 입력 원본에 자세한 두 키워드를 추가 하 여이 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-326">We'll do this by adding two more keywords to the Speech Input Source from the previous chapter.</span></span> <span data-ttu-id="890b8-327">또한 인식 이벤트를 처리 하는 또 다른 방법은 보여 드립니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-327">We'll also demonstrate another way to handle recognition events.</span></span>

1. <span data-ttu-id="890b8-328">다시 클릭할 **AstronautManager** 에 **검사기** 확장를 **키워드** 섹션를 **검사기**.</span><span class="sxs-lookup"><span data-stu-id="890b8-328">Click back on **AstronautManager** in the **Inspector** and expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="890b8-329">클릭 합니다 **+** 새로운 키워드를 추가 하려면 오른쪽에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-329">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="890b8-330">As 키워드를 입력 **모델을 확장**합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-330">Type the Keyword as **Expand Model**.</span></span> <span data-ttu-id="890b8-331">원하는 경우 키 바로 가기를 추가 해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-331">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="890b8-332">클릭 합니다 **+** 새로운 키워드를 추가 하려면 오른쪽에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-332">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="890b8-333">As 키워드를 입력 **모델을 다시 설정**합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-333">Type the Keyword as **Reset Model**.</span></span> <span data-ttu-id="890b8-334">원하는 경우 키 바로 가기를 추가 해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-334">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="890b8-335">에 **검사기** 패널에서 합니다 **구성 요소 추가** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-335">In the **Inspector** panel, click the **Add Component** button.</span></span>
7. <span data-ttu-id="890b8-336">메뉴에서 검색 상자에 입력 **음성 입력 처리기**합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-336">In the menu, type in the search box **Speech Input Handler**.</span></span> <span data-ttu-id="890b8-337">검색 결과 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-337">Select the search result.</span></span>
8. <span data-ttu-id="890b8-338">확인할 **전역 수신기는**초점을 맞춰 보겠습니다에서는 GameObject 관계 없이 작동 하도록 이러한 명령을 것 이므로, 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-338">Check **Is Global Listener**, since we want these commands to work regardless of the GameObject we're focusing.</span></span>
9. <span data-ttu-id="890b8-339">클릭 합니다 **+** 단추를 선택 **확장 모델** 키워드 드롭다운 목록에서.</span><span class="sxs-lookup"><span data-stu-id="890b8-339">Click the **+** button and select **Expand Model** from the Keyword dropdown.</span></span>
10. <span data-ttu-id="890b8-340">클릭 합니다 **+** 응답으로 끌어서를 **AstronautManager** 에서 **계층** 에 **없음 (개체)** 필드입니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-340">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
11. <span data-ttu-id="890b8-341">이제 클릭 합니다 **No 함수** 드롭다운 **AstronautManager**, 다음 **ExpandModelCommand**합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-341">Now, click the **No Function** dropdown, select **AstronautManager**, then **ExpandModelCommand**.</span></span>
12. <span data-ttu-id="890b8-342">음성 입력 처리기를 클릭 **+** 단추를 선택 **재설정 모델** 키워드 드롭다운 목록에서.</span><span class="sxs-lookup"><span data-stu-id="890b8-342">Click the Speech Input Handler's **+** button and select **Reset Model** from the Keyword dropdown.</span></span>
13. <span data-ttu-id="890b8-343">클릭 합니다 **+** 응답으로 끌어서를 **AstronautManager** 에서 **계층** 에 **없음 (개체)** 필드입니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-343">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
14. <span data-ttu-id="890b8-344">이제 클릭 합니다 **No 함수** 드롭다운 **AstronautManager**, 다음 **ResetModelCommand**합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-344">Now, click the **No Function** dropdown, select **AstronautManager**, then **ResetModelCommand**.</span></span>

![5 장에 대 한 음성 입력 소스를 설정 하 고 처리기 방법](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a><span data-ttu-id="890b8-346">빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="890b8-346">Build and Deploy</span></span>

* <span data-ttu-id="890b8-347">시도해 보세요.</span><span class="sxs-lookup"><span data-stu-id="890b8-347">Try it!</span></span> <span data-ttu-id="890b8-348">빌드하고 HoloLens에 앱을 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-348">Build and deploy the app to the HoloLens.</span></span>
* <span data-ttu-id="890b8-349">예를 들어 **확장 모델** 확장된 고상한 모델을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-349">Say **Expand Model** to see the expanded astronaut model.</span></span>
* <span data-ttu-id="890b8-350">사용 하 여 **탐색** 개별 고상한 세트를 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-350">Use **Navigation** to rotate individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="890b8-351">예를 들어 **이동 고상한** 사용 하 여 **조작** 고상한 세트의 개별 항목을 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-351">Say **Move Astronaut** and then use **Manipulation** to move individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="890b8-352">예를 들어 **회전 고상한** 조각을 다시 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-352">Say **Rotate Astronaut** to rotate the pieces again.</span></span>
* <span data-ttu-id="890b8-353">예를 들어 **재설정 모델** 는 고상한 원래 형태로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-353">Say **Reset Model** to return the astronaut to its original form.</span></span>

## <a name="the-end"></a><span data-ttu-id="890b8-354">끝</span><span class="sxs-lookup"><span data-stu-id="890b8-354">The End</span></span>

<span data-ttu-id="890b8-355">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-355">Congratulations!</span></span> <span data-ttu-id="890b8-356">이제 완료 **MR 입력 211: 제스처**합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-356">You have now completed **MR Input 211: Gesture**.</span></span>

* <span data-ttu-id="890b8-357">검색 및 추적, 탐색 및 조작 이벤트를 전달 하는 데 응답 하는 방법을 알고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-357">You know how to detect and respond to hand tracking, navigation and manipulation events.</span></span>
* <span data-ttu-id="890b8-358">탐색 및 조작 제스처 간의 차이점을 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-358">You understand the difference between Navigation and Manipulation gestures.</span></span>
* <span data-ttu-id="890b8-359">손 모양 손실 되려고 할 때, 손 모양 검색 되 고 개체가 다른 상호 작용 (탐색 및 조작)를 지원 하는 경우에 대 한 시각적 피드백을 제공 하는 커서를 변경 하는 방법을 알고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="890b8-359">You know how to change the cursor to provide visual feedback for when a hand is detected, when a hand is about to be lost, and for when an object supports different interactions (Navigation vs Manipulation).</span></span>
