---
title: 사례 연구-3 HoloStudio UI 및 상호 작용 디자인 학습
description: HoloStudio UI 및 상호 작용 디자인 학습
author: rwinj
ms.author: marcghal
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, HoloStudio, Windows Mixed 현실
ms.openlocfilehash: e01e2ea888398e9982b56fd95f90ef0731ec6bc2
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974824"
---
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a><span data-ttu-id="a8295-104">사례 연구-3 HoloStudio UI 및 상호 작용 디자인 학습</span><span class="sxs-lookup"><span data-stu-id="a8295-104">Case study - 3 HoloStudio UI and interaction design learnings</span></span>

<span data-ttu-id="a8295-105">[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) 는 HoloLens 용 최초의 Microsoft 앱 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="a8295-105">[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) was one of the first Microsoft apps for HoloLens.</span></span> <span data-ttu-id="a8295-106">따라서 3D UI 및 상호 작용 디자인에 대 한 새로운 모범 사례를 만들어야 했습니다.</span><span class="sxs-lookup"><span data-stu-id="a8295-106">Because of this, we had to create new best practices for 3D UI and interaction design.</span></span> <span data-ttu-id="a8295-107">이를 위해 많은 사용자 테스트, 프로토타입, 평가판 및 오류가 발생 했습니다.</span><span class="sxs-lookup"><span data-stu-id="a8295-107">We did this through a lot of user testing, prototyping, and trial and error.</span></span>

<span data-ttu-id="a8295-108">이러한 종류의 조사를 수행 하기 위해 모든 사람이 리소스를가지고 있는 것은 아닙니다. Holographic 디자이너 인 Cus Ghaly는 HoloStudio 개발 중에 학습 한 세 가지 사항을 공유 하 여 HoloLens 앱에 대 한 UI 및 상호 작용 디자인을 개발 했습니다.</span><span class="sxs-lookup"><span data-stu-id="a8295-108">We know that not everyone has the resources at their disposal to do this type of research, so we had our Sr. Holographic Designer, Marcus Ghaly, share three things we learned during the development of HoloStudio about UI and interaction design for HoloLens apps.</span></span>

## <a name="watch-the-video"></a><span data-ttu-id="a8295-109">비디오 시청</span><span class="sxs-lookup"><span data-stu-id="a8295-109">Watch the video</span></span>

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a><span data-ttu-id="a8295-110">문제 #1: 사용자가 만들기를 진행 하지 않으려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8295-110">Problem #1: People didn't want to move around their creations</span></span>

<span data-ttu-id="a8295-111">원래 HoloStudio에서 실제 워크 벤치를 사각형으로 설계 했습니다.</span><span class="sxs-lookup"><span data-stu-id="a8295-111">We originally designed the workbench in HoloStudio as a rectangle, much like you'd find in the real world.</span></span> <span data-ttu-id="a8295-112">문제는 사용자가 책상에 앉아 있거나 컴퓨터 앞에서 작업 하는 경우에도 계속 유지 되도록 하는 환경 수명 이라는 것입니다. 따라서 워크 벤치를 전환 하 고 모든 측면에서 3D 만들기를 탐색 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8295-112">The problem is that people have a lifetime of experience that tells them to stay still when they're sitting at a desk or working in front of a computer, so they weren't moving around the workbench and exploring their 3D creation from all sides.</span></span>

![HoloStudio에서 워크 벤치의 사각형 디자인은 사용자가 이동 하 여 모든 측면에서의 생성을 확인 하는 것을 dissuaded.](images/rectangular-workbench-500px.jpg)

<span data-ttu-id="a8295-114">워크 벤치 라운드를 만들기 위한 통찰력을 제공 하 여 사용자가 반드시 사용할 수 있는 "front" 또는 명확한 장소가 없었습니다.</span><span class="sxs-lookup"><span data-stu-id="a8295-114">We had the insight to make the workbench round, so that there was no "front" or clear place that you were supposed to stand.</span></span> <span data-ttu-id="a8295-115">이를 테스트할 때 갑자기 사용자가 자신의 만들기를 직접 탐색 하 고 탐색을 시작 했습니다.</span><span class="sxs-lookup"><span data-stu-id="a8295-115">When we tested this, suddenly people started moving around and exploring their creations on their own.</span></span>

![순환 워크 벤치 디자인은 사용자가 자신의 생성을 중심으로 모든 방법을 안내할 것을 권장 합니다.](images/circular-workbench-500px.jpg)

<span data-ttu-id="a8295-117">**배운 내용**</span><span class="sxs-lookup"><span data-stu-id="a8295-117">**What we learned**</span></span>

<span data-ttu-id="a8295-118">사용자에 게 익숙한 기능에 대해 항상 생각해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8295-118">Always be thinking about what's comfortable for the user.</span></span> <span data-ttu-id="a8295-119">실제 공간을 활용 하는 것은 HoloLens의 쿨 기능이 며 다른 장치에서 수행할 수 없는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a8295-119">Taking advantage of their physical space is a cool feature of HoloLens and something you can't do with other devices.</span></span>

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a><span data-ttu-id="a8295-120">문제 #2: 모달 대화 상자는 때때로 holographic 프레임 외부에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8295-120">Problem #2: Modal dialogs are sometimes out of the holographic frame</span></span>

<span data-ttu-id="a8295-121">경우에 따라 사용자가 앱에서 주의가 필요한 다른 방향을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8295-121">Sometimes, your user may be looking in a different direction from something that needs their attention in your app.</span></span> <span data-ttu-id="a8295-122">PC에서는 대화 상자를 팝업 할 수 있지만, 3D 환경에서 다른 사용자에 게이 작업을 수행 하는 경우 대화 상자에서 대화 상자를 가져오는 것 처럼 보일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8295-122">On a PC, you can just pop up a dialog, but if you do this in someone's face in a 3D environment, it can feel like the dialog is getting in their way.</span></span> <span data-ttu-id="a8295-123">메시지를 읽는 데 필요한 메시지는 이러한 해당 메시지를 가져오는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a8295-123">You need them to read the message, but their instinct is to try to get away from it.</span></span> <span data-ttu-id="a8295-124">게임을 재생 하는 경우에는 유용 하지만, 작업을 위해 설계 된 도구에서는 이상적이 지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a8295-124">This reaction is great if you're playing a game, but in a tool designed for work, it's less than ideal.</span></span>

<span data-ttu-id="a8295-125">몇 가지 다른 작업을 시도한 후에는 대화에 대 한 "생각 거품형" 시스템을 사용 하 여 사용자가 응용 프로그램에서 주의가 필요한 곳에 합의 수 있는 tendrils를 추가 했습니다.</span><span class="sxs-lookup"><span data-stu-id="a8295-125">After trying a few different things, we finally settled on using a "thought bubble" system for our dialogs and added tendrils that users can follow to where their attention is needed in our application.</span></span> <span data-ttu-id="a8295-126">또한 사용자가 이동할 위치를 알 수 있도록 방향성이 있음을 암시 하는 tendrils 펄스를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="a8295-126">We also made the tendrils pulse, which implied a sense of directionality so that users knew where to go.</span></span>

!["생각 거품형" 시스템에는 응용 프로그램에서 주의가 필요한 곳에 대 한 사용자의 지침을 제공 하는 펄스 된 tendrils 포함 되어 있습니다.](images/thought-bubble-500px.jpg)

<span data-ttu-id="a8295-128">**배운 내용**</span><span class="sxs-lookup"><span data-stu-id="a8295-128">**What we learned**</span></span>

<span data-ttu-id="a8295-129">3D에서 사용자에 게 주의 해야 하는 항목을 알려 주는 것이 훨씬 더 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="a8295-129">It's much harder in 3D to alert users to things they need to pay attention to.</span></span> <span data-ttu-id="a8295-130">[공간 음향](spatial-sound.md), 빛 광선 또는 생각 거품과 같은 주목 이사회를 사용 하면 사용자가 필요한 위치로 이어질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8295-130">Using attention directors such as [spatial sound](spatial-sound.md), light rays, or thought bubbles, can lead users to where they need to be.</span></span>

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a><span data-ttu-id="a8295-131">문제 #3: 경우에 따라 UI는 다른 holograms 차단 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8295-131">Problem #3: Sometimes UI can get blocked by other holograms</span></span>

<span data-ttu-id="a8295-132">사용자가 홀로그램 및 연결 된 UI 컨트롤과 상호 작용 하려고 하지만 다른 홀로그램 앞에 있기 때문에 뷰에서 차단 되는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8295-132">There are times when a user wants to interact with a hologram and its associated UI controls, but they are blocked from view because another hologram is in front of them.</span></span> <span data-ttu-id="a8295-133">HoloStudio를 개발 하는 동안이에 대 한 솔루션에 대 한 평가판 및 오류를 사용 했습니다.</span><span class="sxs-lookup"><span data-stu-id="a8295-133">While we were developing HoloStudio, we used trial and error to come to a solution for this.</span></span>

![홀로그램 사이에 다른 홀로그램가 있는 경우 HoloLens에 연결 된 UI 컨트롤이 차단 될 수 있습니다.](images/ui-blocked-500px.jpg)

<span data-ttu-id="a8295-135">사용자가 차단 될 수 없도록 UI 컨트롤을 사용자에 게 더 가깝게 이동 하려고 했지만 사용자가 멀리 떨어져 있었던 홀로그램을 동시에 확인 하는 동안 사용자가 가까이 있는 컨트롤을 확인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a8295-135">We tried moving the UI control closer to the user so it couldn't get blocked, but found that it wasn't comfortable for the user to look at a control that was near to you while simultaneously looking at a hologram that was far away.</span></span> <span data-ttu-id="a8295-136">그러나 사용자에 게 가장 가까운 홀로그램 앞에서 컨트롤을 이동한 경우에는 영향을 주는 홀로그램에서 분리 된 것 처럼 보입니다.</span><span class="sxs-lookup"><span data-stu-id="a8295-136">If, however, we moved the control in front of the closest hologram to the user, they felt like it was detached from the hologram it should be affecting.</span></span>

<span data-ttu-id="a8295-137">마지막으로 UI 컨트롤의 고스팅을 종료 하 고 사용자와 연결 된 홀로그램와 동일한 거리에 배치 하므로 둘 다 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8295-137">We finally ended up ghosting the UI control, and put it at the same distance from the user as the hologram it's associated with, so they both feel connected.</span></span> <span data-ttu-id="a8295-138">이렇게 하면 사용자가 컨트롤과 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8295-138">This allows the user to interact with the control even though it's been obscured.</span></span>

![솔루션: UI 컨트롤을 고스트 했습니다 .이 컨트롤은 컨트롤과 상호 작용 하 여 영향을 받은 홀로그램에 연결 된 것으로 느껴질 수 있습니다.](images/ghosting-ui-500px.jpg)

<span data-ttu-id="a8295-140">**배운 내용**</span><span class="sxs-lookup"><span data-stu-id="a8295-140">**What we learned**</span></span>

<span data-ttu-id="a8295-141">사용자는 UI 컨트롤이 차단 된 경우에도 쉽게 액세스할 수 있어야 합니다. 따라서 사용자가 실제 세계 어디에 있든 관계 없이 작업을 완료할 수 있도록 하는 방법을 holograms.</span><span class="sxs-lookup"><span data-stu-id="a8295-141">Users need to be able to easily access UI controls even if they've been blocked, so figure out methods to ensure that users can complete their tasks no matter where their holograms are in the real world.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="a8295-142">작성자 정보</span><span class="sxs-lookup"><span data-stu-id="a8295-142">About the author</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><span data-ttu-id="a8295-143"><b>Ghaly cus</b></span><span class="sxs-lookup"><span data-stu-id="a8295-143"><b>Marcus Ghaly</b></span></span><br><span data-ttu-id="a8295-144">Holographic 디자이너@Microsoft</span><span class="sxs-lookup"><span data-stu-id="a8295-144">Sr. Holographic Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="a8295-145">참조</span><span class="sxs-lookup"><span data-stu-id="a8295-145">See also</span></span>
* [<span data-ttu-id="a8295-146">Instinctual 상호 작용</span><span class="sxs-lookup"><span data-stu-id="a8295-146">Instinctual interactions</span></span>](interaction-fundamentals.md)

 
