---
title: 손 coach
description: 3D 바늘은 시스템에서 사용자가 도움을 받을 수 있도록 사용자의 손을 감지 하지 못하는 경우에 트리거됩니다.
author: grayclee
ms.author: glee
ms.date: 09/25/2019
ms.topic: article
keywords: Windows Mixed Reality, 디자인, 손 coach, 몰입 형 헤드셋, MRTK, 실습, 실습 지원
ms.openlocfilehash: 38da046256dce3242b464a0741f2afa7fb19ff3c
ms.sourcegitcommit: 7ca383ef1c5dc895ca2a289435f2e9d4c1ee6e65
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85345670"
---
# <a name="hand-coach"></a><span data-ttu-id="0a1ad-104">손 coach</span><span class="sxs-lookup"><span data-stu-id="0a1ad-104">Hand coach</span></span>
![예: 손 coach](images/HandCoach/MRTK_handCoach.jpg)<br>

<span data-ttu-id="0a1ad-106">핸드 coach는 시스템에서 사용자의 손을 감지 하지 못하는 경우 트리거되는 3D 모델링 된 손을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-106">Hand coach is 3D modeled hands that are triggered when the system does not detect the user’s hands.</span></span> <span data-ttu-id="0a1ad-107">이 구성 요소는 제스처를 학습 하지 않았을 때 사용자에 게 안내 하는 데 도움이 되는 "교육" 구성 요소로 구현 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-107">This is implemented as a “teaching” component that helps guide the user when the gesture has not been taught.</span></span> <span data-ttu-id="0a1ad-108">사용자가 지정 된 기간 동안 지정 된 제스처를 수행 하지 않은 경우에는 손으로 지연 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-108">If users have not done the specified gesture for a period, the hands will loop with a delay.</span></span> <span data-ttu-id="0a1ad-109">손 coach는 단추를 누르거나 홀로그램을 선택 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-109">The Hand coach could be used to represent pressing a button or picking up a hologram.</span></span>  

## <a name="hand-coach-provided"></a><span data-ttu-id="0a1ad-110">핸드 coach 제공 됨</span><span class="sxs-lookup"><span data-stu-id="0a1ad-110">Hand coach provided</span></span>

<span data-ttu-id="0a1ad-111">현재 상호 작용 모델은 스크롤, 먼 선택 및 가까운 탭과 같은 다양 한 제스처 컨트롤을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-111">The current interaction model represents a wide variety of gesture controls such as scrolling, far select, and near tap.</span></span> <span data-ttu-id="0a1ad-112">다음은<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> Mrtk</a>에서 제공 되는 기존 손 제스처의 전체 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-112">Below is a full list of existing hand gestures provided in<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> MRTK</a>:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="0a1ad-113">![Near Select의 예](images/HandCoach/NearSelect.gif)</span><span class="sxs-lookup"><span data-stu-id="0a1ad-113">![Example of Near Select](images/HandCoach/NearSelect.gif)</span></span><br>
       <span data-ttu-id="0a1ad-114">**거의 선택 된 사용 예 단추를 선택 하거나 interactable 개체를 닫는 방법을 보여 줍니다.**</span><span class="sxs-lookup"><span data-stu-id="0a1ad-114">**Example of Near Select - Used show how to select buttons or close interactable objects**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0a1ad-115">![대공 탭의 예](images/HandCoach/AirTap.gif)</span><span class="sxs-lookup"><span data-stu-id="0a1ad-115">![Example of Air Tap](images/HandCoach/AirTap.gif)</span></span><br>
        <span data-ttu-id="0a1ad-116">**멀리 떨어져 있는 개체를 선택 하는 방법을 보여 주는 데 사용 되는 공기 탭의 예**</span><span class="sxs-lookup"><span data-stu-id="0a1ad-116">**Example of Air Tap - Used to show how to select objects that are far away**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0a1ad-117">![이동 예](images/HandCoach/Move.gif)</span><span class="sxs-lookup"><span data-stu-id="0a1ad-117">![Example of Move](images/HandCoach/Move.gif)</span></span><br>
       <span data-ttu-id="0a1ad-118">**공간에서 홀로그램을 이동 하는 방법을 보여 주는 데 사용 되는 개체를 공간으로 이동 하는 예제**</span><span class="sxs-lookup"><span data-stu-id="0a1ad-118">**Example of Moving an object in space-Used to show how to move a hologram in space**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0a1ad-119">![회전 예](images/HandCoach/Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="0a1ad-119">![Example of Rotate](images/HandCoach/Rotate.gif)</span></span><br>
       <span data-ttu-id="0a1ad-120">**회전-holograms 또는 개체를 회전 하는 방법을 보여 주는 데 사용 되는 예**</span><span class="sxs-lookup"><span data-stu-id="0a1ad-120">**Example of Rotate-Used to show how to rotate holograms or objects**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="0a1ad-121">![크기 조정 예제](images/HandCoach/Scale.gif)</span><span class="sxs-lookup"><span data-stu-id="0a1ad-121">![Example of Scale](images/HandCoach/Scale.gif)</span></span><br>
       <span data-ttu-id="0a1ad-122">**Holograms를 더 크거나 작게 조작 하는 방법을 보여 주기 위해 사용 하는 규모의 예**</span><span class="sxs-lookup"><span data-stu-id="0a1ad-122">**Example of Scale- Used to show how to manipulate holograms to be bigger or smaller**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0a1ad-123">![팜 위로의 예](images/HandCoach/PalmUp.gif)</span><span class="sxs-lookup"><span data-stu-id="0a1ad-123">![Example of Palm Up](images/HandCoach/PalmUp.gif)</span></span><br>
        <span data-ttu-id="0a1ad-124">**팜 up – 제안 된 사용의 예**</span><span class="sxs-lookup"><span data-stu-id="0a1ad-124">**Example of Palm up – Suggested use, to bring up hand menus**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0a1ad-125">![수동 대칭 이동의 예](images/HandCoach/HandFlip.gif)</span><span class="sxs-lookup"><span data-stu-id="0a1ad-125">![Example of HandFlip](images/HandCoach/HandFlip.gif)</span></span><br>
       <span data-ttu-id="0a1ad-126">**직접 대칭 이동-메뉴를 표시 하는 다른 방법**</span><span class="sxs-lookup"><span data-stu-id="0a1ad-126">**Exmaple of Hand Flip – Another way to bring up Hand Menus**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0a1ad-127">![스크롤 예](images/HandCoach/Scoll.gif)</span><span class="sxs-lookup"><span data-stu-id="0a1ad-127">![Example of Scroll](images/HandCoach/Scoll.gif)</span></span><br>
       <span data-ttu-id="0a1ad-128">**스크롤 예제-목록 또는 긴 문서 스크롤에 사용**</span><span class="sxs-lookup"><span data-stu-id="0a1ad-128">**Example of Scroll – Used for scrolling a list or a long document**</span></span><br>
    :::column-end:::
:::row-end:::

## <a name="design-concepts"></a><span data-ttu-id="0a1ad-129">설계 개념</span><span class="sxs-lookup"><span data-stu-id="0a1ad-129">Design concepts</span></span>

<span data-ttu-id="0a1ad-130">Hololens2의 경우 instinctual 및 자연 핸드 제스처를 기반으로 하는 손으로의 상호 작용을 설계 했습니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-130">For Hololens2, we designed out hand interactions based on instinctual and natural hand gestures.</span></span> <span data-ttu-id="0a1ad-131">이러한 경우가 대부분의 사용자에 게 직관적 이라고 생각 하므로 전용 제스처 학습 순간을 만들지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-131">We believe these to be intuitive to most users and thus did not create dedicated gesture learning moments.</span></span> <span data-ttu-id="0a1ad-132">대신, holograms와 상호 작용 하는 데 익숙하지 않은 사용자에 게 이러한 제스처에 대해 알아보기 위해 손을 coach를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-132">Instead, we created the hand coach to help users who might get stuck or are unfamiliar with interacting with holograms learn about these gestures.</span></span> <span data-ttu-id="0a1ad-133">학습 시점이 없으면 사용자에 게 작업을 수행 하는 방법을 보여 주는 것이 가장 좋은 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-133">Without a learning moment, we felt that showing users how to perform an action by demonstrating it would be the best option.</span></span> <span data-ttu-id="0a1ad-134">이 연구에서는 사용자가 제스처를 파악할 수 있었지만 약간의 지침을 필요로 했습니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-134">In our studies, we found that users were able to figure out the gesture but needed a little guidance.</span></span> <span data-ttu-id="0a1ad-135">사용자가 특정 기간 동안 개체와 상호 작용 하지 않는 것을 감지 하면 올바른 손 모양 및 손가락 배치를 시연 하는 손 모양 coach 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-135">If we detect that a user does not interact with an object for a period, a Hand coach would be triggered demonstrating the correct hand and finger placement.</span></span> 

### <a name="intuitive"></a><span data-ttu-id="0a1ad-136">간단</span><span class="sxs-lookup"><span data-stu-id="0a1ad-136">Intuitive</span></span>

<span data-ttu-id="0a1ad-137">실습에 애니메이션을 적용 하는 경우 분명 하 게 shoudn't 혼동을 발생 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-137">When animating hands, it should be obvious and shoudn't cause any confusion.</span></span> <span data-ttu-id="0a1ad-138">바늘의 애니메이션은 사용자에 게 하기 호출할 사용자를 이해 하려는 제스처를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-138">The animation of the hands is a representation of the gesture your trying to evoke to the user to understand it's purpose.</span></span> 

<span data-ttu-id="0a1ad-139">예를 들어 사용자가 단추를 누르기를 원하는 경우 단추를 누르는 손을 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-139">For example, if you wish a user to press a button, a hand pressing a button would be triggered.</span></span>

<span data-ttu-id="0a1ad-140">![예: 손 모양 coach 가까이 누르기](images/HandCoach/NearSelect_unity.gif)</span><span class="sxs-lookup"><span data-stu-id="0a1ad-140">![Example: Hand coach Near Tap](images/HandCoach/NearSelect_unity.gif)</span></span><br>
<span data-ttu-id="0a1ad-141">*보석 가까이 누르기를 보여 주는 손 Coach*</span><span class="sxs-lookup"><span data-stu-id="0a1ad-141">*Hand Coach demonstrating Near Tapping a Gem*</span></span>  

### <a name="hand-scale"></a><span data-ttu-id="0a1ad-142">수동 크기 조정</span><span class="sxs-lookup"><span data-stu-id="0a1ad-142">Hand scale</span></span>

<span data-ttu-id="0a1ad-143">UI 메뉴를 사용 하 여 다양 한 손 크기를 테스트 하 고 실제로는 크기에 따라 menacing 느낌이 있지만 너무 작은 경우에는 제스처를 보고 이해 하기 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-143">We tested various hand sizes with the UI menus and felt that if the hands were true to size, it gave a menacing feeling but if they were too small then it was hard to see and understand the gesture.</span></span> 

<span data-ttu-id="0a1ad-144">**음성 전달 및 손**</span><span class="sxs-lookup"><span data-stu-id="0a1ad-144">**Voice over and hands**</span></span>

<span data-ttu-id="0a1ad-145">사용자가 음성을 통해 일련의 지침을 수신 하 고 직접 coach를 통해 다양 한 지침을 볼 수 있다고 생각 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-145">Don’t expect users can listen to one set of instructions via voice over and watch different instructions via Hand coach.</span></span> <span data-ttu-id="0a1ad-146">토대로 오버 로드를 줄이기 위해 사용자에 게 집중 하 고 경합에 집중 하는 데 도움이 되는 지침을 시퀀싱 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-146">Sequence your instructions to help users focus versus compete for their attention to reduce sensory overload.</span></span>


## <a name="can-i-create-my-own"></a><span data-ttu-id="0a1ad-147">직접 만들 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="0a1ad-147">Can I create my own?</span></span>

<span data-ttu-id="0a1ad-148">예.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-148">Yes!</span></span> <span data-ttu-id="0a1ad-149">게임에 고유한 제스처를 만들어 커뮤니티에 다시 참가 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-149">We encourage you to create your own unique gesture for your game and contribute back to the community!</span></span>
<span data-ttu-id="0a1ad-150">다운로드 가능한 앱에 사용할 수 있는 Rigged 손의 Maya 파일을 제공 합니다. <a href="files/HandCoach_MRTK.zip">다운로드 HandCoach_MRTK.zip</a></span><span class="sxs-lookup"><span data-stu-id="0a1ad-150">We have provided a Maya file of a Rigged hand that can be used for your app which can be downloaded here: <a href="files/HandCoach_MRTK.zip"> Download HandCoach_MRTK.zip</a></span></span>

<span data-ttu-id="0a1ad-151">![Maya의 애니메이션 실습 예](images/HandCoach/MayaSelect_Gif.gif)</span><span class="sxs-lookup"><span data-stu-id="0a1ad-151">![Example of Animated Hands in Maya](images/HandCoach/MayaSelect_Gif.gif)</span></span><br>
<span data-ttu-id="0a1ad-152">*Maya의 상자에 애니메이션을 적용 하는 Poking 예*</span><span class="sxs-lookup"><span data-stu-id="0a1ad-152">*Example of animated Hand Poking a box in Maya*</span></span>


<span data-ttu-id="0a1ad-153">**권장 authoring tool**</span><span class="sxs-lookup"><span data-stu-id="0a1ad-153">**Recommended authoring tool**</span></span>

<span data-ttu-id="0a1ad-154">3D 아티스트 중에는 [Autodesk의 Maya](https://www.youtube.com/watch?v=q0K3n0Gf8mA) 를 사용 하도록 선택 하 고,이를 사용 하 여 자산이 생성 되는 방식을 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-154">Among 3D artists, many choose to use [Autodesk’s Maya which itself is able to use HoloLens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) to transform the way assets are created.</span></span> <span data-ttu-id="0a1ad-155">제공 되는 실습 파일은 Maya 이진 파일 이므로 Maya를 사용 하 여 애니메이션을 적용 하 고 내보내는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-155">The hands file provided is a Maya Binary File, so it is recommended to use Maya to animate and export the hands.</span></span> <span data-ttu-id="0a1ad-156">다른 3D 프로그램을 사용 하려는 경우에는 다음을 참조 <b>하세요. FBX</b>: <a href="files/HandCoachMRTK_FBX.zip">HandCoachMRTK_FBX.zip다운로드</a> 하 여 사용자 고유의 컨트롤러 설치를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-156">If you prefer to use another 3D program, here is a <b>.FBX</b>: <a href="files/HandCoachMRTK_FBX.zip">           Download HandCoachMRTK_FBX.zip</a> to create your own controller setup.</span></span> 

<span data-ttu-id="0a1ad-157">제공 된 다운로드 가능 maya 손으로 제공 된 파일을 사용 하는 경우 unity의 손을 0.6으로 축소 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-157">If using the downloadable maya Hand File provided, it is suggested to scale down the hands in unity to 0.6.</span></span>

<span data-ttu-id="0a1ad-158">![예: Maya의 핸드 coach rig](images/HandCoach/MayaExample.png)</span><span class="sxs-lookup"><span data-stu-id="0a1ad-158">![Example: Hand coach rig in Maya](images/HandCoach/MayaExample.png)</span></span><br>
<span data-ttu-id="0a1ad-159">*Rigged 손*</span><span class="sxs-lookup"><span data-stu-id="0a1ad-159">*Rigged Hands*</span></span>

### <a name="technical-specs"></a><span data-ttu-id="0a1ad-160">기술 사양</span><span class="sxs-lookup"><span data-stu-id="0a1ad-160">Technical Specs</span></span>

*   <span data-ttu-id="0a1ad-161">두 개의 전달 파일은 Maya Ascii 형식으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-161">Two handed File is available in Maya Ascii format</span></span>
*    <span data-ttu-id="0a1ad-162">오른쪽 및 왼쪽은 Maya 이진 형식으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-162">Right and Left Hand is available in Maya Binary format</span></span>
*   <span data-ttu-id="0a1ad-163">Maya 파일을 24FPS로 설정</span><span class="sxs-lookup"><span data-stu-id="0a1ad-163">Set your Maya file to 24 FPS</span></span>
*   <span data-ttu-id="0a1ad-164">파일 내에는 두 개의 핸드 또는 단일 면 제스처에 사용할 수 있는 왼쪽과 오른쪽이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-164">Within the file, there is a left and right hand which can be used for two handed or single-handed gestures.</span></span> <span data-ttu-id="0a1ad-165">오른쪽은 기본적으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-165">The right hand will only be visible by default.</span></span>
*   <span data-ttu-id="0a1ad-166">약 10 개의 프레임에 대 한 버퍼를 시작 부분에 그대로 두고 페이드를 종료 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-166">It is suggested to leave a buffer of about 10 frames at the beginning and end for fades</span></span>
*   <span data-ttu-id="0a1ad-167">지정 된 대상을 사용 하 여 개체에 애니메이션 효과를 주려면 기본 상자 또는 Null에 애니메이션 효과를 주는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-167">If animating a object with a specified target, its best practice to animate to a Default box or Null.</span></span>
*   <span data-ttu-id="0a1ad-168">상자와 같은 물리적 개체에 애니메이션 효과를 적용 하는 경우에는 Maya에서 번역에 애니메이션 효과를 주지 않지만 Unity 또는 코드에서 애니메이션 효과를 주기 위해 대기 하는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-168">If the hand is animating a physical object such as a box, its best practice to not animate the translation in Maya but wait to animate it in Unity or in Code.</span></span>
*   <span data-ttu-id="0a1ad-169">표시 되는 애니메이션은 의미 있는 정보를 전달 하는 데 1.5 초 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-169">Visible Animation should be 1.5 secs for any meaningful information to be conveyed</span></span>
*   <span data-ttu-id="0a1ad-170">애니메이션에 만족 하는 경우:</span><span class="sxs-lookup"><span data-stu-id="0a1ad-170">When you feel satisfied with your animation:</span></span>
    *   <span data-ttu-id="0a1ad-171">모든 연결점 및 굽기 키 프레임 선택</span><span class="sxs-lookup"><span data-stu-id="0a1ad-171">Select all joints and bake key frames</span></span>
    *   <span data-ttu-id="0a1ad-172">컨트롤러를 삭제 하 고, 조인트 및 메시를 선택 하 고, FBX로 내보내기를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-172">Delete the Controllers, Select the joints and mesh and export as an FBX</span></span>
    *  <span data-ttu-id="0a1ad-173">여러 애니메이션이 있는 경우 Maya의 기본 제공 게임 내보내기를 사용할 수 있습니다.https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html</span><span class="sxs-lookup"><span data-stu-id="0a1ad-173">If there are Multiple Animations, you can use Maya’s built in Game Exporter: https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html</span></span>

## <a name="exporting-from-maya"></a><span data-ttu-id="0a1ad-174">Maya에서 내보내기</span><span class="sxs-lookup"><span data-stu-id="0a1ad-174">Exporting from Maya</span></span>

<span data-ttu-id="0a1ad-175">애니메이션에 만족 하는 경우</span><span class="sxs-lookup"><span data-stu-id="0a1ad-175">After you are satisfied with your animation</span></span>
* <span data-ttu-id="0a1ad-176">모든 조인트 선택: 계층 > 선택</span><span class="sxs-lookup"><span data-stu-id="0a1ad-176">Select all joints: Select > Hierarchy</span></span>

     ![예: 메뉴 위치](images/HandCoach/Hierarchy.png)<br>
* <span data-ttu-id="0a1ad-178">애니메이션 굽기: 애니메이션 > 키 > 굽기 애니메이션으로 전환</span><span class="sxs-lookup"><span data-stu-id="0a1ad-178">Bake out your animation: Switch to Animation > Key > Bake Animation</span></span>

     ![예: 메뉴 위치](images/HandCoach/BakeAnimation.png)<br>
* <span data-ttu-id="0a1ad-180">컨트롤러 Rig: Outliner > MainR_Grp 또는 MainL_Grp를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-180">Delete the Controller Rig: Outliner > MainR_Grp or MainL_Grp</span></span>

     ![예: 메뉴 위치](images/HandCoach/ControllerRig.png)<br>

* <span data-ttu-id="0a1ad-182">FBX로 내보내기: Select JNT + 메시: File > 선택 영역 내보내기 (옵션 상자) > 선택 영역 내보내기</span><span class="sxs-lookup"><span data-stu-id="0a1ad-182">Export as FBX: Select JNT + Mesh: File > Export Selection (option box) > Export Selection</span></span>

     ![예: 메뉴 위치](images/HandCoach/OptionBox.png)<br>

     ![예: 메뉴 위치](images/HandCoach/SelectionExport.png)<br>

     ![예: 메뉴 위치](images/HandCoach/FBXSelection.png)<br>


 <span data-ttu-id="0a1ad-186">FBX로 내보내고 Unity로 이동 하는 경우에는 0.6에 맞게 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-186">When exporting as a FBX and brought into Unity, scale the hands down to 0.6.</span></span> <span data-ttu-id="0a1ad-187">이는 손을 표시 하는 데 완벽 한 균형을 갖고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-187">We found that this was perfect balance for displaying the hands.</span></span> 

<span data-ttu-id="0a1ad-188">![예: Unity 설정](images/HandCoach/HandHintScale.png)</span><span class="sxs-lookup"><span data-stu-id="0a1ad-188">![Example: Unity Settings](images/HandCoach/HandHintScale.png)</span></span><br>
<span data-ttu-id="0a1ad-189">*MRTK에서 찾은 HandCoach_R prefab에 대 한 Unity 설정*</span><span class="sxs-lookup"><span data-stu-id="0a1ad-189">*Unity Settings for HandCoach_R prefab found in MRTK*</span></span>


## <a name="implementing-hands-into-your-unity-project"></a><span data-ttu-id="0a1ad-190">Unity 프로젝트에 대 한 직접 구현</span><span class="sxs-lookup"><span data-stu-id="0a1ad-190">Implementing Hands into your Unity project</span></span>

### <a name="best-practices"></a><span data-ttu-id="0a1ad-191">모범 사례</span><span class="sxs-lookup"><span data-stu-id="0a1ad-191">Best practices</span></span>
*    <span data-ttu-id="0a1ad-192">Unity의 손을 0.6으로 축소 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-192">It is suggested to scale down the hands in unity to 0.6</span></span>
*   <span data-ttu-id="0a1ad-193">손을 두 번 재생 하 고, 완료 되지 않은 경우 제스처가 완료 될 때까지 지속적으로 반복 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-193">Hands should be played twice and if not completed then continuously looped until gesture is completed.</span></span> <span data-ttu-id="0a1ad-194">사용자가를 등록 하 고 제스처를 볼 수 있도록 하려면 두 번 반복 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-194">The hands should be looped twice to ensure the user had time to register and see the gesture.</span></span> <span data-ttu-id="0a1ad-195">바늘은 루프 간에 페이드 인 및 페이드 아웃 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-195">The hands should fade in and out between loops.</span></span> 
 *  <span data-ttu-id="0a1ad-196">사용자의 손을 HL2 카메라에서 볼 수 있지만 사용자가 필요한 상호 작용을 수행 하지 않는 경우 10 초 후에도 손을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-196">If user’s hands are visible by HL2 cameras but users are not doing the interaction needed of them the hands will appear after 10 seconds.</span></span>
*   <span data-ttu-id="0a1ad-197">사용자의 손을 HL2 카메라에 표시 되지 않으면 5 초 후에도 손을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-197">If user’s hands are NOT visible by HL2 cameras, the hands will appear after 5 seconds.</span></span>  
*   <span data-ttu-id="0a1ad-198">애니메이션 중간의 HL2 카메라에서 사용자의 손을 시각적으로 추적 하는 경우 애니메이션이 완료 되 고 페이드 아웃 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-198">If user’s hands are visibly tracked by HL2 cameras in the middle of the animation, the animation will complete and fade out.</span></span>
*   <span data-ttu-id="0a1ad-199">음성을 포함 하는 경우에는 손 제스처에 해당 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-199">If you are including voice over, we suggest that it corresponds to the gesture of the hand.</span></span>
*   <span data-ttu-id="0a1ad-200">한 번 이상 실습을 수행한 경우에는 사용자가 중지 된 것으로 검색 된 경우에만 제스처를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-200">If you have taught the hands at least once, only repeat the gesture if its detected that the user is stuck.</span></span>
*   <span data-ttu-id="0a1ad-201">특정 손가락/손 위치가 중요 한 경우 사용자가 애니메이션에서 이러한 미묘한 차이를 명확 하 게 볼 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-201">If specific finger/hand positions are critical, ensure users can clearly see these nuances in the animation.</span></span> <span data-ttu-id="0a1ad-202">가장 중요 한 부분이 명확 하 게 표시 되도록 손을 준.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-202">Try angling the hands so the most important parts are clearly visible.</span></span> 
* <span data-ttu-id="0a1ad-203">손으로 왜곡 된 경우 Unity의 품질 설정으로 이동 하 여 뼈의 크기를 늘려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-203">If you notice distortion on the hands, you need to go to Unity's Quality settings increase the amount of bones.</span></span> 
 <span data-ttu-id="0a1ad-204">Unity의 편집 > 프로젝트 설정 > 품질 > 기타 > 혼합 가중치로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-204">Go to Unity's Edit > Project Settings > Quality > Other > Blend Weights.</span></span> <span data-ttu-id="0a1ad-205">부드러운 조인트를 보려면 "4 뼈"가 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-205">Make sure "4 bones" are selected to see Smooth Joints.</span></span> 

   ![예: 메뉴 위치](images/HandCoach/ProjectSettings.png)<br>





### <a name="what-to-avoid"></a><span data-ttu-id="0a1ad-207">피해야 할 사항</span><span class="sxs-lookup"><span data-stu-id="0a1ad-207">What to avoid</span></span>
* <span data-ttu-id="0a1ad-208">너무 크게 크기 조정</span><span class="sxs-lookup"><span data-stu-id="0a1ad-208">Scaling the Hands too large</span></span>
* <span data-ttu-id="0a1ad-209">사용자에 게 너무 가까운 손을 두기</span><span class="sxs-lookup"><span data-stu-id="0a1ad-209">placing the Hands too close to the user</span></span>
* <span data-ttu-id="0a1ad-210">손을 한 번만 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-210">Hands should only be taught once.</span></span> <span data-ttu-id="0a1ad-211">교육을 통해 혼란을 야기 하 고 messiness 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-211">Over teaching can cause confusion and messiness</span></span>
*   <span data-ttu-id="0a1ad-212">Unity로 가져오면 최신 MRTK를 다운로드 하세요.https://github.com/microsoft/MixedRealityToolkit-Unity</span><span class="sxs-lookup"><span data-stu-id="0a1ad-212">Bringing it into Unity, please download the latest MRTK  here: https://github.com/microsoft/MixedRealityToolkit-Unity</span></span>
    *   <span data-ttu-id="0a1ad-213">재질: Teaching_Hand2</span><span class="sxs-lookup"><span data-stu-id="0a1ad-213">Material: Teaching_Hand2</span></span>
    *   <span data-ttu-id="0a1ad-214">스크립트: <a href= "https://github.com/MixedRealityToolkit-Unity/blob/'HandCoachUX'/Documentation/README_HandCoach.md">mrtk 손 coach</a> 에 대 한 mrtk 지침 참조</span><span class="sxs-lookup"><span data-stu-id="0a1ad-214">Scripts: Refer to MRTK guidelines for <a href= "https://github.com/MixedRealityToolkit-Unity/blob/'HandCoachUX'/Documentation/README_HandCoach.md"> MRTK hand coach </a></span></span>
    *   <span data-ttu-id="0a1ad-215">프로젝트별 설정</span><span class="sxs-lookup"><span data-stu-id="0a1ad-215">Per- project setting</span></span>
        *   <span data-ttu-id="0a1ad-216">UWP로 설정 된 장면: Windows Mixed Reality의 [Unity 구성 프로젝트](Configure-Unity-Project.md) 에서 지침을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a1ad-216">Scene set to UWP: Instruction can be found on the [Configure Unity Project](Configure-Unity-Project.md) for Windows Mixed Reality</span></span>

## <a name="see-also"></a><span data-ttu-id="0a1ad-217">참조</span><span class="sxs-lookup"><span data-stu-id="0a1ad-217">See also</span></span>
* [<span data-ttu-id="0a1ad-218">상호 작용-기본 사항</span><span class="sxs-lookup"><span data-stu-id="0a1ad-218">Interaction-fundamentals</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="0a1ad-219">자산 생성 프로세스</span><span class="sxs-lookup"><span data-stu-id="0a1ad-219">Asset Creation Process</span></span>](asset-creation-process.md)
* [<span data-ttu-id="0a1ad-220">제스처</span><span class="sxs-lookup"><span data-stu-id="0a1ad-220">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="0a1ad-221">도구 설치</span><span class="sxs-lookup"><span data-stu-id="0a1ad-221">Install the Tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="0a1ad-222">Unity 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="0a1ad-222">Configure Unity Project</span></span>](Configure-Unity-Project.md)
* [<span data-ttu-id="0a1ad-223">Unity 개발 개요</span><span class="sxs-lookup"><span data-stu-id="0a1ad-223">Unity development overview</span></span>](unity-development-overview.md)
* [<span data-ttu-id="0a1ad-224">MRTK 101</span><span class="sxs-lookup"><span data-stu-id="0a1ad-224">MRTK 101</span></span>](mrtk-101.md)
