---
title: 사례 연구-3 HoloStudio UI와 상호 작용 디자인 학습
description: HoloStudio UI와 상호 작용 디자인 학습
author: rwinj
ms.author: marcghal
ms.date: 03/21/2018
ms.topic: article
keywords: 혼합 현실을 HoloStudio, HoloLens, Windows
ms.openlocfilehash: 217c489fed3c0588dae1c2753db6ba15da3522c8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603209"
---
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a><span data-ttu-id="d29ff-104">사례 연구-3 HoloStudio UI와 상호 작용 디자인 학습</span><span class="sxs-lookup"><span data-stu-id="d29ff-104">Case study - 3 HoloStudio UI and interaction design learnings</span></span>

<span data-ttu-id="d29ff-105">[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) HoloLens에 대 한 첫 번째 Microsoft 앱 중 하나 였습니다.</span><span class="sxs-lookup"><span data-stu-id="d29ff-105">[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) was one of the first Microsoft apps for HoloLens.</span></span> <span data-ttu-id="d29ff-106">이 인해 UI 3D에 대 한 새 모범 사례를 만들고 상호 작용 디자인 해야 했습니다.</span><span class="sxs-lookup"><span data-stu-id="d29ff-106">Because of this, we had to create new best practices for 3D UI and interaction design.</span></span> <span data-ttu-id="d29ff-107">많은 사용자 테스트, 프로토타입 생성 및 시행 착오를 통해이 했습니다.</span><span class="sxs-lookup"><span data-stu-id="d29ff-107">We did this through a lot of user testing, prototyping, and trial and error.</span></span>

<span data-ttu-id="d29ff-108">리소스를이이 유형의 연구를 위해 마음에 HoloStudio HoloLens 앱에 대 한 UI와 상호 작용 디자인에 대 한 개발 중 알게 우리의 수석 Holographic 디자이너 Marcus Ghaly 다음 세 가지를 공유 했습니다 하는 모든 사람이 알고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d29ff-108">We know that not everyone has the resources at their disposal to do this type of research, so we had our Sr. Holographic Designer, Marcus Ghaly, share three things we learned during the development of HoloStudio about UI and interaction design for HoloLens apps.</span></span>

## <a name="watch-the-video"></a><span data-ttu-id="d29ff-109">비디오를 시청 하세요.</span><span class="sxs-lookup"><span data-stu-id="d29ff-109">Watch the video</span></span>

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a><span data-ttu-id="d29ff-110">문제 #1: 사용자가 생성 될 때까지 이동 하 고 싶지</span><span class="sxs-lookup"><span data-stu-id="d29ff-110">Problem #1: People didn't want to move around their creations</span></span>

<span data-ttu-id="d29ff-111">원래 설계 했습니다 HoloStudio에서 workbench를 사각형으로 훨씬 유사 하 게 실제 환경에서.</span><span class="sxs-lookup"><span data-stu-id="d29ff-111">We originally designed the workbench in HoloStudio as a rectangle, much like you'd find in the real world.</span></span> <span data-ttu-id="d29ff-112">문제는 사람들이 책상에 앉아 또는 workbench로 이동 하지 않은 컴퓨터 앞에 작업 및 모든 면에서 3D 생성을 탐색 하는 경우에 계속 유지 하도록 알려주는 환경의 수명입니다.</span><span class="sxs-lookup"><span data-stu-id="d29ff-112">The problem is that people have a lifetime of experience that tells them to stay still when they're sitting at a desk or working in front of a computer, so they weren't moving around the workbench and exploring their 3D creation from all sides.</span></span>

![HoloStudio에서 워크 벤치의 사각형 디자인 dissuaded 사용자가 이동 하 고 모든 면에서 해당 만들기를 표시 합니다.](images/rectangular-workbench-500px.jpg)

<span data-ttu-id="d29ff-114">확인 했습니다. "앞면" 있도록 반올림 또는 독립 었어야 하는 위치를 지우기 workbench에 대 한 정보는 했습니다.</span><span class="sxs-lookup"><span data-stu-id="d29ff-114">We had the insight to make the workbench round, so that there was no "front" or clear place that you were supposed to stand.</span></span> <span data-ttu-id="d29ff-115">이 테스트를 갑자기 사용자 시작 이동 하 고 해당 만들기 자체적으로 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="d29ff-115">When we tested this, suddenly people started moving around and exploring their creations on their own.</span></span>

![순환 workbench 디자인 사용자를 만들기까지 경비원 하는 것이 좋습니다.](images/circular-workbench-500px.jpg)

<span data-ttu-id="d29ff-117">**학습 한 내용을**</span><span class="sxs-lookup"><span data-stu-id="d29ff-117">**What we learned**</span></span>

<span data-ttu-id="d29ff-118">항상 란 사용자 편리 하 게 생각이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d29ff-118">Always be thinking about what's comfortable for the user.</span></span> <span data-ttu-id="d29ff-119">해당 물리적 공간 활용 기능은 쿨의 HoloLens 및 기타 장치를 사용 하 여 수행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d29ff-119">Taking advantage of their physical space is a cool feature of HoloLens and something you can't do with other devices.</span></span>

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a><span data-ttu-id="d29ff-120">문제 #2: 모달 대화 상자는 holographic 프레임</span><span class="sxs-lookup"><span data-stu-id="d29ff-120">Problem #2: Modal dialogs are sometimes out of the holographic frame</span></span>

<span data-ttu-id="d29ff-121">경우에 따라 앱에서 주의가 필요한 항목에서 다른 방향 사용자를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d29ff-121">Sometimes, your user may be looking in a different direction from something that needs their attention in your app.</span></span> <span data-ttu-id="d29ff-122">PC에는 대화 상자에서 최대만 팝업 수 있지만 대화 상자는 고유한 방식으로 시작 되는 듯한 느낌 3D 환경에서 사람의 얼굴에서이 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="d29ff-122">On a PC, you can just pop up a dialog, but if you do this in someone's face in a 3D environment, it can feel like the dialog is getting in their way.</span></span> <span data-ttu-id="d29ff-123">메시지를 확인 해야 할 이지만 해당 속성을 벗어나면 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d29ff-123">You need them to read the message, but their instinct is to try to get away from it.</span></span> <span data-ttu-id="d29ff-124">이 반응 게임을 재생 중인 이지만 작업을 위한 도구 내에서 이상적인 하는 경우에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d29ff-124">This reaction is great if you're playing a game, but in a tool designed for work, it's less than ideal.</span></span>

<span data-ttu-id="d29ff-125">잠시 다른 작업을 시도한 후 마지막으로 "거품형 생각 했습니다." 시스템을 사용 하 여이 대화 상자에서 확인 하 고 tendrils 사용자 응용 프로그램에서 주의가 필요한 하기 위해 수행할 수 있는 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d29ff-125">After trying a few different things, we finally settled on using a "thought bubble" system for our dialogs and added tendrils that users can follow to where their attention is needed in our application.</span></span> <span data-ttu-id="d29ff-126">사용자 실마리가 이동 될 수 있도록 방향의 의미를 암시 하는 tendrils pulse를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="d29ff-126">We also made the tendrils pulse, which implied a sense of directionality so that users knew where to go.</span></span>

!["생각 거품" 시스템 방향으로 사용자가 앱에 주의가 필요한 위치를 앞의 의미를 제공 하는 깜박이 tendrils 포함 되어 있습니다.](images/thought-bubble-500px.jpg)

<span data-ttu-id="d29ff-128">**학습 한 내용을**</span><span class="sxs-lookup"><span data-stu-id="d29ff-128">**What we learned**</span></span>

<span data-ttu-id="d29ff-129">것에 주의 해야 하는 항목에 사용자에 게 경고를 3d에서 훨씬 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="d29ff-129">It's much harder in 3D to alert users to things they need to pay attention to.</span></span> <span data-ttu-id="d29ff-130">같은 주의 이사를 사용 하 여 [공간 소리](spatial-sound.md)광선을 밝은, 사고 버블링 사용자 수 필요한 곳 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d29ff-130">Using attention directors such as [spatial sound](spatial-sound.md), light rays, or thought bubbles, can lead users to where they need to be.</span></span>

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a><span data-ttu-id="d29ff-131">문제 #3: 경우에 따라 다른 제공 하 여 UI 차단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d29ff-131">Problem #3: Sometimes UI can get blocked by other holograms</span></span>

<span data-ttu-id="d29ff-132">사용자를 홀로그램 및 연결 된 해당 UI 컨트롤을 사용 하 여 상호 작용 하려고 하지만 앞에 다른 홀로그램 이므로 보기에서 차단 된 경우에 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d29ff-132">There are times when a user wants to interact with a hologram and its associated UI controls, but they are blocked from view because another hologram is in front of them.</span></span> <span data-ttu-id="d29ff-133">HoloStudio를 개발 하는 동안이 대 한 솔루션을 시행 착오를 사용 했습니다.</span><span class="sxs-lookup"><span data-stu-id="d29ff-133">While we were developing HoloStudio, we used trial and error to come to a solution for this.</span></span>

![UI 컨트롤을 홀로그램와 연결 된 HoloLens 착용 사용자 간의 다른 홀로그램 있으면 차단 될 수 있습니다.](images/ui-blocked-500px.jpg)

<span data-ttu-id="d29ff-135">차단 하지만 멀리 떨어져 있는 홀로그램 동시에 확인 하는 동안 근접 하는 컨트롤에서 사용자에 대 한 편리한 없다는 찾을 가져올 수 없습니다 사용자에 게 더 가깝게 UI 컨트롤을 이동 하려고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="d29ff-135">We tried moving the UI control closer to the user so it couldn't get blocked, but found that it wasn't comfortable for the user to look at a control that was near to you while simultaneously looking at a hologram that was far away.</span></span> <span data-ttu-id="d29ff-136">그러나 사용자에 게 가장 가까운 홀로그램 앞에 컨트롤을 이동, 하는 경우 영향을 줄 수 해야 홀로그램에서 분리 된 것 처럼 개입 합니다.</span><span class="sxs-lookup"><span data-stu-id="d29ff-136">If, however, we moved the control in front of the closest hologram to the user, they felt like it was detached from the hologram it should be affecting.</span></span>

<span data-ttu-id="d29ff-137">에서는 마지막 UI 컨트롤, 영상 끝난을 넣습니다 같은 거리에 사용자의 연결 된 홀로그램으로 모두 느낌 연결 하므로.</span><span class="sxs-lookup"><span data-stu-id="d29ff-137">We finally ended up ghosting the UI control, and put it at the same distance from the user as the hologram it's associated with, so they both feel connected.</span></span> <span data-ttu-id="d29ff-138">이 려 지 된 경우에 컨트롤과 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d29ff-138">This allows the user to interact with the control even though it's been obscured.</span></span>

![솔루션: 컨트롤과 상호 작용을 허용 및에 영향을 주는 되었습니다 홀로그램에 연결 되어 있다고 생각 했는데 모두 UI 컨트롤을 고스팅 했습니다.](images/ghosting-ui-500px.jpg)

<span data-ttu-id="d29ff-140">**학습 한 내용을**</span><span class="sxs-lookup"><span data-stu-id="d29ff-140">**What we learned**</span></span>

<span data-ttu-id="d29ff-141">사용자는이 차단 된 경우에 UI 컨트롤에 쉽게 액세스할 수 있으므로 사용자가 실제로 해당 홀로그램 있는 관계 없이 해당 작업을 완료할 수 있도록 하는 방법 파악 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d29ff-141">Users need to be able to easily access UI controls even if they've been blocked, so figure out methods to ensure that users can complete their tasks no matter where their holograms are in the real world.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="d29ff-142">저자 소개</span><span class="sxs-lookup"><span data-stu-id="d29ff-142">About the author</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><span data-ttu-id="d29ff-143"><b>Marcus Ghaly</b></span><span class="sxs-lookup"><span data-stu-id="d29ff-143"><b>Marcus Ghaly</b></span></span><br><span data-ttu-id="d29ff-144">선임 Holographic 디자이너 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="d29ff-144">Sr. Holographic Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="d29ff-145">참조</span><span class="sxs-lookup"><span data-stu-id="d29ff-145">See also</span></span>
* [<span data-ttu-id="d29ff-146">상호 작용 기본 사항</span><span class="sxs-lookup"><span data-stu-id="d29ff-146">Interaction fundamentals</span></span>](interaction-fundamentals.md)

 
